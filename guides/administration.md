# Archivematica administration

* [Fixity checking and repair](#fixity)  
* [Dropping MySQL and ES data in pipelines](#flushing)  
* [Reindexing AIPs in Archival Storage indexes](#reindexing)  
* [Deleting AIPs not indexed on a pipeline](#deletingaips)  
* [Cleaning up after successful Automation Tools ingests](#autotoolssuccess)
* [Responding to failed Automation Tools ingests](#autotoolsfailure)
* [Adding and switching AIP Store locations](#locations)  
* [Clearing space when local disk is nearly full](#clearingspace)  
* [Restarting services](#restarting)  
* [Log of changes to default Archivematica FPR](#fprchanges)  
* [Archivematica configuration settings](#configsettings)  

<a name="fixity"></a>  
## Fixity checking and repair  

Fixity checks of all AIPs are conducted on a quarterly basis using the [Fixity](https://github.com/artefactual/fixity) application. Fixity's `scanall` function is run via the [cca-fixity](https://github.com/timothyryanwalsh/cca-fixity) scripts installed at `/var/archivematica/cca-fixity` on the Storage Service VM and called automatically on the second Friday of each January, April, July, and October via the crontab. Logs are saved on the Archivematica Storage Service server at `/var/log/cca-fixity`and results are emailed to the relevant administrators.

If you must run a fixity check manually, use [nohup](https://en.wikipedia.org/wiki/Nohup) to ensure that the process runs to completion in the background, even if your terminal session ends, e.g.:  

`nohup fixity scanall &`

When AIP corruption is detected, notify IT and restore the AIP from backups according to the Storage Service's [Recovery](https://www.archivematica.org/en/docs/storage-service-0.10/recovery/#recovery) procedures.  

<a name="flushing"></a>
## Dropping MySQL and ES data in pipelines  

We will periodically drop the Elasticsearch indexes and rows from the MySQL databases on each of the processing pipelines to minimize resource drain and keep performance quick. This should be done every few months and only after all ingests have been successfully QAed.  

When the ES index is dropped, backups and logs from `/srv/am-est-backups` and `/var/log/elasticsearch` may also be deleted. This will help to save space on the local disk.

To drop the ES index on a pipeline:

`curl -XDELETE http://<pipeline.ip.address>/aips`

<a name="reindexing"></a>
## Reindexing AIPs Archival Storage indexes  

To re-index an AIP in an Archival Storage index on a given pipeline, you can use the `rebuild-aip-index.py` and `reindex-aip.sh` scripts from the Archivematica folder of the [CCA scripts repo](https://github.com/timothyryanwalsh/cca-scripts/tree/master/archivematica) on the pipeline where you would like the AIPs to be re-indexed.

The bash script `reindex-aip.sh` reindexes an AIP using the [Archivematica devtools](https://github.com/artefactual/archivematica-devtools).

The Python script `rebuild-aip-index.py` allows you to specify the UUIDs of the AIPs you would like to index by adding them as strings to the list "aip_list", then calls `reindex-aip.sh` for each of the AIPs.

Before using the scripts:  
* Clone the `archivematica-devtools` repo to your home folder on the pipeline server  
* Change paths in the scripts to point to correct locations  

<a name="deletingaips"></a>  
## Deleting AIPs not indexed on a pipeline
         
To send a deletion request for an AIP that is not currently indexed on an Archivematica pipeline, ssh into the Storage Service VM and run the following curl command, replacing all values in < > with the appropriate information:

```
curl -X POST -H "Content-Type: application/json" -H "Authorization: ApiKey <SS user>:<SS user API key>" -d '{"event_reason":"<reason for deletion>","pipeline":"<UUID to pipeline to send deletion from>","user_id":<integer pipeline user primary key>,"user_email":"<email to send deletion notice to>"}' <SS URL>/api/v2/file/<AIP UUID>/delete_aip/
```

<a name="autotoolssuccess"></a>  
## Cleaning up after successful Automation Tools ingests  

After ingests started via Automation Tools finish successfully, they must be deleted from the Transfer Source (in this case, `/mnt/incoming/auto-transfers/`) manually. This must be done by a user with `sudo` permissions, e.g. `sudo rm -rf /path/to/transfer/`. **Be careful when deleting files with sudo, as it is very easy to accidentally delete files you did not intend to delete**.

Tim wrote some code for the Automation Tools repository that will automatically delete transfer source files after a successful ingest if the `transfer-script.sh` script is run with a `--delete` flag. This code is [currently being reviewed](https://github.com/artefactual/automation-tools/pull/44) - if the pull request is accepted and merged, it would remove the need for manually cleaning up after successful Automation Tools ingests. 

<a name="autotoolsfailure"></a>  
## Responding to failed Automation Tools ingests  

When an ingest started via Automation Tools fails, the first order of business is to determine why the ingest failed and either fix the transfer or submit a support ticket with Artefactual.

When you are ready to re-start the transfer/ingest after correcting the problem, you will notice that simply putting the transfer in the watched folder will not work. This is because the `transfers.db` SQLite database that the Automation Tools use to keep track of which transfers have already been started will already include the transfer (determined based on the folder name), preventing it from being started.

The solution is to delete the `transfers.db` database and to manually re-start the `transfer-script.sh` with `sudo` permissions and as user `archivematica`:  

* `sudo rm -f /var/archivematica/automation-tools/transfers.db`  
* `sudo -u archivematica /etc/archivematica/automation-tools/transfer-script.sh`  

You only need to manually call `transfer-script.sh` once - after that, the crontab will call the script every 5 minutes, per the recommended installation instructions.  

**Note that deleting `transfers.db` means that the Automation Tools will no longer have a record of which transfers in the `/mnt/incoming/auto-transfers` directory have already been started, so you will want to make sure only transfers you intend to start are present in that directory before deleting the database.**

<a name="locations"></a>  
## Adding and switching AIP Store locations  

Each storage location configured in the Storage Service is 5 TB in size (this was done in order to make backups manageable for IT). As storage locations will, new locations will need to be added to the Storage Service and assigned as the default values for pipelines. **Locations should contain only AIPs for which DIPs will be produced (e.g. processed digital archives) or AIPs for which DIPs will not be produced (e.g. digitization masters), not mixed.**

Steps to add a new location:  
1. Ensure directory to add is mounted on Storage Service VM (read/write) and pipeline VMs (read-only). Ask CCA sysadmin to configure this if not true.    
2. Configure as a storage space in the Storage Service GUI.  
3. Set as default value in appropriate pipelines.  
4. Update defaultProcessingMCP files with new Store AIP location in Automation Tools.  
5. (If new storage location will contain AIPs for which we want to generate DIPs) Modify the `--location-uuid` value in `/etc/archivematica/automation-tools/create_dips_job_script.sh` to the value for the new AIP Store location. If it is necessary to monitor and create DIPs for more than one AIP Store location, create a second script (e.g. `create_dips_job_script_1.sh`) and add this additional script to the crontab under user `archivematica` (to edit the crontab, use `sudo crontab -u archivematica -e`).  

<a name="clearingspace"></a>
## Clearing space when local disk is nearly full  

When local disk space on one of the Archivematica pipelines is almost full, IT will send an alert. To clear space, you may delete some logs and well as older MySQL and Elasticsearch backups, namely:  

* `/srv/am-db-backups`: Keep latest backup; all others can be deleted  
* `/srv/am-es-backups`: Keep latest backup (check file size to ensure it's a real backup); all others can be deleted  
* `/var/log/elasticsearch`: Delete any logs more than a month old  

<a name="restarting"></a>  
## Restarting services

To stop services:  

```
sudo stop archivematica-mcp-server
sudo stop archivematica-mcp-client
sudo stop archivematica-dashboard
sudo service nginx stop
sudo /etc/init.d/gearman-job-server stop
sudo service mysql stop
sudo /etc/init.d/elasticsearch stop
```

To start services:  

```
sudo /etc/init.d/elasticsearch start
sudo service mysql start
sudo /etc/init.d/gearman-job-server start
sudo start archivematica-dashboard
sudo service nginx start
sudo start archivematica-mcp-server
sudo start archivematica-mcp-client
```

To restart only the Archivematica server/client/dashboard:  

`sudo bash -c 'for i in dashboard mcp-client mcp-server; do service archivematica-$i restart; done'`  


<a name="fprchanges"></a>
## Log of changes to default Archivematica FPR  

* FITS command replaced with bash script to prevent non-XML outputs from raising error (fixed in AM 1.7)  
* FITS set as a characterization tool for all file formats -- note that this is crucial, as it means there is an indexed last modified date for all files ingested. See [METSFlask documentation](https://github.com/timothyryanwalsh/metsflask#detailed-identification-and-dates) for details on how to ensure FITS characterization for all files in AM 1.6  
* Extraction rules for RAW, ISO, AFF, and E01 disk images are disabled so that disk images can be stored alongside files (disk image extraction occurs in BitCurator prior to Archivematica ingest in our local workflows)  
* Ghostscript PDF->PDF/A command replaced with a bash script that prevents errors when output filepaths are longer than 255 characters  
* Normalization rules for Adobe Flash, Macromedia Flash, and Generic SWF are disabled (by default, Archivematica attempts to normalize these formats to ffv1/Matroska video, which failed nearly 100% of the time)  
* Libreoffice and commands for transcoding to docx, odt, xlsx, ods, and pptx added   

<a name="configsettings"></a>
## Archivematica configuration settings  

* Elasticsearch request_timeout value changed from 10 to 60 seconds  
* Storage Service will be set to use all available cores for bagit-python fixity checking (default is 1; should be user-configurable in SS/0.11)  
