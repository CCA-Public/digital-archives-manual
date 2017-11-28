# Administration

* [Fixity checking and repair](#fixity)  
* [Dropping MySQL and ES data in pipelines](#flushing)  
* [Reindexing AIPs in Archival Storage indexes](#reindexing)  
* [Clearing space when local disk is nearly full](#clearingspace)  
* [Restarting services](#restarting)  
* [Log of changes to default Archivematica FPR](#fprchanges)  
* [Archivematica configuration settings](#configsettings)  

<a name="fixity"></a>  
## Fixity checking and repair  

Fixity checks of all AIPs are conducted on a bi-annual (twice a year) basis using the [Fixity](https://github.com/artefactual/fixity) application. Fixity's `scanall` function is run via the `run-fixity-scanall.sh` bash script on the Storage Service VM. Logs are saved on the Archivematica Storage Service server and results are emailed to Storage Service administrators. Regular timing of these fixity checks is still to be determined with IT; for now they are run manually.

When AIP corruption is detected, the AIP is restored from backups according to the Storage Service's [Recovery](https://www.archivematica.org/en/docs/storage-service-0.10/recovery/#recovery) procedures.  

<a name="flushing"></a>
## Dropping MySQL and ES data in pipelines  

We will periodically drop the Elasticsearch indexes and rows from the MySQL databases on each of the processing pipelines to minimize resource drain and keep performance quick. This should be done every few months and only after all ingests have been successfully QAed.  

When the ES index is dropped, backups and logs from `/srv/am-est-backups` and `/var/log/elasticsearch` may also be deleted. This will help to save space on the local disk.

<a name="reindexing"></a>
## Reindexing AIPs Archival Storage indexes  

To re-index an AIP in an Archival Storage index on a given pipeline, you can use the `rebuild-aip-index.py` and `reindex-aip.sh` scripts from the Archivematica folder of the [CCA scripts repo](https://github.com/timothyryanwalsh/cca-scripts/tree/master/archivematica) on the pipeline where you would like the AIPs to be re-indexed. This is necessary, for example, to request deletion of an AIP from the AIP Store.

The bash script `reindex-aip.sh` reindexes an AIP using the [Archivematica devtools](https://github.com/artefactual/archivematica-devtools).

The Pythons script `rebuild-aip-index.py` allows you to specify the UUIDs of the AIPs you would like to index by adding them as strings to the list "aip_list", then calls `reindex-aip.sh` for each of the AIPs.

Before using the scripts:  
* Clone the `archivematica-devtools repo` to your home folder on the pipeline server  
* Change paths in the scripts to point to correct locations  

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
* Extraction rules for RAW, ISO, and AFF disk images are disabled so that disk images can be stored alongside files that are exported by the Disk Image Processor pre-ingest  
* Ghostscript PDF->PDF/A command replaced with a bash script that prevents errors when output filepaths are longer than 255 characters  
* Normalization rules for Adobe Flash, Macromedia Flash, and Generic SWF are disabled (by default, Archivematica attempts to normalize these formats to ffv1/Matroska video, which failed nearly 100% of the time)  

<a name="configsettings"></a>
## Archivematica configuration settings  

* Elasticsearch request_timeout value changed from 10 to 60 seconds  
* Storage Service will be set to use all available cores for bagit-python fixity checking (default is 1; shoudl be user-configurable in SS/0.11)  
