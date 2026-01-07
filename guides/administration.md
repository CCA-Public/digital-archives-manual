# Archivematica administration

* [Logging in](#login)
* [Start an ingest](#startingest)
* [Archivematica server monitoring](#monitoring)  
* [Fixity checking and repair](#fixity)  
* [Dropping MySQL and ES data in pipelines](#flushing)  
* [Reindexing AIPs in Archival Storage indexes](#reindexing)  
* [Deleting AIPs](#deletingaips)  
* [Cleaning up after successful Automation Tools ingests](#autotoolssuccess)
* [Responding to failed Automation Tools ingests](#autotoolsfailure)  
* [Checking Automation Tools logs](#checkthelogs)  
* [Adding and switching AIP Store locations](#locations)  
* [Updating Automation Tools processing configuration](#updateconfig)
* [Clearing space when local disk is nearly full](#clearingspace)  
* [Restarting services](#restarting)  
* [Log of changes to default Archivematica FPR](#fprchanges)  
* [Archivematica custom settings](#customsettings)  
* [Archivematica updates and dependencies](#update)  

<a name="login"></a>
## Logging in

For administrators to log into the Archivematica servers, they will need to ask IT to make them an account. The command to access the server is `ssh user@172.17.50.68` where `user` is your username and the string of numbers is the URL for the pipeline or Storage Service. Enter your password when prompted.

To log out, use `Ctrl+D`. 

<a name="startingest"></a>
## Starting an ingest

Confirm that the digital processing archivists have uploaded their SIPs to the appropriate pipeline. Once you've logged into the server for that pipeline, do:

    cd /mnt/incoming/transfers/UPLOADED_SIP_FOLDER
    sudo mv * /mnt/incoming/auto-transfers/

This moves the SIPs into a watched folder. Archivematica will start ingesting these SIPs at the next five minute interval. Next confirm the folder is empty using the `ls` command. Then delete the empty folder:

    cd ..
    rm -rf  /UPLOADED_SIP_FOLDER/

<a name="monitoring"></a>  
## Archivematica server monitoring

[Server monitoring](https://vsp-prtg-01.int.cca/public/mapshow.htm?id=2636&mapid=archivematica)

<a name="fixity"></a>  
## Fixity checking and repair  

Fixity checks of all AIPs are conducted on a quarterly basis using the [Fixity](https://github.com/artefactual/fixity) application. Fixity's `scanall` function is run via the [cca-fixity](https://github.com/CCA-Public/cca-fixity) scripts installed at `/var/archivematica/cca-fixity` on the Storage Service VM and called automatically on the second Friday of each January, April, July, and October via the crontab. Logs are saved on the Archivematica Storage Service server at `/var/log/cca-fixity`and results are emailed to the relevant administrators.

To manually conduct a fixity check of a single AIP:

1. Connect to VSP-AMSS-02  
2. Load environmental variables: `source /etc/profile.d/fixity.sh`
3. Run fixity `scan` function: `fixity scan <AIP UUID>`  

If you must run a `scanall` fixity check manually, use [nohup](https://en.wikipedia.org/wiki/Nohup) to ensure that the process runs to completion in the background, even if your terminal session ends

1. Connect to VSP-AMSS-02  
2. Load environmental variables: `source /etc/profile.d/fixity.sh`
3. Run fixity `scanall` function: `nohup fixity scanall &`

When AIP corruption is detected, notify IT and restore the AIP from backups according to the Storage Service's [Recovery](https://www.archivematica.org/en/docs/storage-service-0.10/recovery/#recovery) procedures.  

<a name="flushing"></a>
## Dropping MySQL and ES data in pipelines  

We will periodically drop the Elasticsearch indexes and rows from the MySQL databases on each of the processing pipelines to minimize resource drain and keep performance quick. This should be done every few months and only after all ingests have been successfully QAed. 

Artefactual Support has been asked to create an estimate for a script to do this cleanup for pipeline MySQL databases.   

To drop the ES index on a pipeline:

`curl -XDELETE http://<pipeline.ip.address>:9200/aips`

When the ES index is dropped, backups and logs from `/srv/am-est-backups` and `/var/log/elasticsearch` may also be deleted. This will help to save space on the local disk.

<a name="reindexing"></a>
## Reindexing AIPs Archival Storage indexes  

To re-index an AIP in an Archival Storage index on a given pipeline, you can use the `rebuild-aip-index.py` and `reindex-aip.sh` scripts from the Archivematica folder of the [CCA scripts repo](https://github.com/CCA-Public/cca-scripts/tree/master/archivematica) on the pipeline where you would like the AIPs to be re-indexed.

The bash script `reindex-aip.sh` reindexes an AIP using the [Archivematica devtools](https://github.com/artefactual/archivematica-devtools).

The Python script `rebuild-aip-index.py` allows you to specify the UUIDs of the AIPs you would like to index by adding them as strings to the list "aip_list", then calls `reindex-aip.sh` for each of the AIPs.

Before using the scripts:  
* Clone the `archivematica-devtools` repo to your home folder on the pipeline server  
* Change paths in the scripts to point to correct locations  

<a name="deletingaips"></a>  
## Deleting AIPs
         
To send a deletion request for an AIP that is indexed on an Archivematica pipeline, follow [these instructions](https://www.archivematica.org/en/docs/archivematica-1.7/user-manual/archival-storage/archival-storage/#delete-aip). 

To send a deletion request for an AIP that is not currently indexed on an Archivematica pipeline, ssh into the Storage Service VM and run the following curl command, replacing all values in < > with the appropriate information:

```
curl -X POST -H "Content-Type: application/json" -H "Authorization: ApiKey <SS user>:<SS user API key>" -d '{"event_reason":"<reason for deletion>","pipeline":"<UUID to pipeline to send deletion from>","user_id":<integer pipeline user primary key>,"user_email":"<email to send deletion notice to>"}' <SS URL>/api/v2/file/<AIP UUID>/delete_aip/
```

<a name="autotoolssuccess"></a>  
## Cleaning up after successful Automation Tools ingests  

After ingests started via Automation Tools finish successfully, they must be deleted from the Transfer Source (in this case, `/mnt/incoming/auto-transfers/`) manually. This must be done by a user with `sudo` permissions, e.g. `sudo rm -rf /path/to/transfer/`. **Be careful when deleting files with sudo, as it is very easy to accidentally delete files you did not intend to delete**.

Tessa wrote some code for the Automation Tools repository that will automatically delete transfer source files after a successful ingest if the `transfer-script.sh` script is run with a `--delete` flag. This code is [currently being reviewed](https://github.com/artefactual/automation-tools/pull/44) - if the pull request is accepted and merged, it would remove the need for manually cleaning up after successful Automation Tools ingests. 

<a name="autotoolsfailure"></a>  
## Responding to failed Automation Tools ingests  

When an ingest started via Automation Tools fails, the first order of business is to determine why the ingest failed and either fix the transfer or submit a support ticket with Artefactual.

When you are ready to re-start the transfer/ingest after correcting the problem, you will notice that simply putting the transfer in the watched folder will not work. This is because the `transfers.db` SQLite database that the Automation Tools use to keep track of which transfers have already been started will already include the transfer (determined based on the folder name), preventing it from being started.

The solution is to delete the `transfers.db` database and to manually re-start the `transfer-script.sh` with `sudo` permissions and as user `archivematica`:  

* `sudo rm -f /var/archivematica/automation-tools/transfers.db`  
* `sudo -u archivematica /etc/archivematica/automation-tools/transfer-script.sh`  

You only need to manually call `transfer-script.sh` once - after that, the crontab will call the script every 5 minutes, per the recommended installation instructions.  

**Note that deleting `transfers.db` means that the Automation Tools will no longer have a record of which transfers in the `/mnt/incoming/auto-transfers` directory have already been started, so you will want to make sure only transfers you intend to start are present in that directory before deleting the database.**

<a name="checkthelogs"></a>  
## Checking Automation Tools logs  

If you run into unexpected behavior from Automation Tools (e.g. transfers not starting or not approving, DIPs not being created for new AIPs), the first place to check is the logs.  

Relevant logs:  
* Automation Tools transfers: `/var/log/archivematica/automation-tools/transfers.log`  
* Create DIP Job: `/var/log/archivematica/automation-tools/create-dip-jobs.log`  

<a name="locations"></a>  
## Adding and switching AIP Store locations  

Each storage location configured in the Storage Service is 5 TB in size (this was done in order to make backups manageable for IT). As storage locations fill, new locations will need to be added to the Storage Service and assigned as the default values for pipelines. **Locations should contain only AIPs for which DIPs will be produced (e.g. processed digital archives) or AIPs for which DIPs will not be produced (e.g. digitization masters), not mixed.**

Steps to start using a new AIP Store location:  

1. Ensure directory to add is mounted on Storage Service VM (read/write) and pipeline VMs (read-only). Ask CCA sysadmin to configure this if not true.    
2. Configure as a Space and AIP storage Location in the Storage Service GUI (or ask Artefactual support to do this for you).     
3. Set new AIP storage location as the default value in appropriate pipelines.  
4. Replace the defaultProcessingMCP.xml file used with Automation Tools transfers at `/opt/archivematica/automation-tools/transfers/pre-transfer/defaultProcessingMCP.xml` with an updated configuration.  
5. (If new storage location will contain AIPs for which we want to generate DIPs) Modify the `--location-uuid` value in `/etc/archivematica/automation-tools/create_dips_job_script.sh` to the value for the new AIP Store location. If it is necessary to monitor and create DIPs for more than one AIP Store location, create a second script (e.g. `create_dips_job_script_1.sh`) and add this additional script to the crontab under user `archivematica` (to edit the crontab, use `sudo crontab -u archivematica -e`).  

These AIP Store locations are already configured in the Archivematica Storage Service:  

| AIP Store | Currently in Use? | Configured with Automation Tools DIP creation script? | Notes |  
| :----: | :------------: | :---------: | :----: |  
| DARK_ARCHIVE_001 | Yes | Yes | Current default AIP Store location for Pipeline 2 (processed digital archives) |  
| DARK_ARCHIVE_002 | Yes | No | Current default AIP Store location for Pipeline 1 (accessions and A/V) |  
| DARK_ARCHIVE_003 | No | n/a | n/a |  
| DARK_ARCHIVE_004 | No | n/a | n/a |  
| DARK_ARCHIVE_005 | No | n/a | n/a |  

<a name="updateconfig"></a>
## Updating Automation Tools processing configuration

When updating the processing configuration, go to the "Administration" tab of the appropriate pipeline dashboard, select the "Default" configuration, and adjust settings as needed. Then click "Save" and download the updated congfiguration file from the following page. 

This must then be put into Automation Tools in Archivematica. Send the configuration file to the appropriate pipeline using the "send_to_archivematica.py" script on the BitCurator machines. Then move the file from /mnt/incoming/transfer to Automation Tools.

<a name="clearingspace"></a>
## Clearing space when local disk is nearly full  

When local disk space on one of the Archivematica pipelines is almost full, IT will send an alert. To clear space, you may delete some logs as well as older MySQL and Elasticsearch backups, namely:  

* `/srv/am-db-backups`: Keep latest backup; all others can be deleted  
* `/srv/am-es-backups`: Keep latest backup (check file size to ensure it's a real backup); all others can be deleted  
* `/var/log/elasticsearch`: Delete any logs more than a month old

You may also delete temporary files:

* `cd /tmp`
* `sudo systemctl stop archivematica-mcp-server`
* `sudo systemctl stop archivematica-dashboard`
* `sudo rm * -rf`
* `sudo systemctl start archivematica-mcp-server`
* `sudo systemctl start archivematica-dashboard`

<a name="restarting"></a>  
## Restarting services

To stop services:  

```
sudo service archivematica-mcp-server stop
sudo service archivematica-mcp-client stop
sudo service archivematica-dashboard stop
sudo service nginx stop
sudo service gearman-job-server stop
sudo service mysql stop
sudo service elasticsearch stop
```

To start services:  

```
sudo service archivematica-mcp-server start
sudo service archivematica-mcp-client start
sudo service archivematica-dashboard start
sudo service nginx start
sudo service gearman-job-server start
sudo service mysql start
sudo service elasticsearch start
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

<a name="customsettings"></a>
## Custom Archivematica settings  

* Elasticsearch request_timeout value changed from 10 to 60 seconds  
* Storage Service will be set to use all available cores for bagit-python fixity checking (default is 1; should be user-configurable in SS/0.11)  

Artefactual also documented more atypical aspects of the CCA's Archivematica set-up:

* The automation tools are installed in /usr/lib/archivematica/automation-tools/
* The script located at /etc/archivematica/automation-tools/transfer-script.sh runs each 5 minutes as system user archivematica, and uses the Archivematica user autobot.
* The configuration file at /etc/archivematica/automation-tools/transfers.confdefines logfile and database are at /var/log/archivematica/automation-tools/ , and the lock file at /var/archivematica/automation-tools/transfers-pid.lck. This file might need to be removed in the automation-tools stop working.
* Automated ingests use folder /mnt/incoming/auto-transfers as transfer source, and the AIPs are stored in DARK_ARCHIVE_002 aipstore for VSP-AMPL-04, and DARK_ARCHIVE_001 for VSP-AMPL-05

<a name="update"></a>
## Archivematica updates and dependencies   

Version updates for Archivematica should be done by Artefactual, and are covered by our service contract with them. However, because Archivematica has a number of dependencies, the Digital Archivist should assess the capacity of both local IT and Artefactual support prior to upgrading. 

Dependencies which may affect the success of upgrades include:

* **Automation tools on the BitCurator machines:** Any change that results in a change to the Archivematica Pipeline server security keys will result in the create_dip.sh script failing. The script needs to be updated to reflect the new key.
* **TMS API:** The TMS API was affected by the upgrade to the 2019 version of Archivematica. More details forthcoming. 
* **SCOPE** 
