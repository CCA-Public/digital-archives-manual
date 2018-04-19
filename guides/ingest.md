# Ingest in Archivematica

*Current version of Archivematica: 1.6.1*  

This page describes the configurations and policies utilized by Archivematica during ingest. It includes:  

* [Archivematica configuration at CCA](#architecture)
* [Methods for ingesting digital archives into Archivematica](#ingestmethods)  
  * [Automation Tools](#automationtools)  
    * [Procedure for Automation Tools ingest: digital archives](#automationtoolsarchives)  
    * [Procedure for Automation Tools ingest: digitized A/V](#automationtoolsav)  
  * [Using the Archivematica Web UI](#webui)  
* [Archivematica processing configurations](#processingconfigs)
  * [Configuration for ingest of "raw" data](#rawingestconfig)  
  * [Configuration for ingest of "processed" data](#processedingestconfig) 
  * [Configuration for re-ingest](#reingestconfig)
  * [Configuration for metadata-only re-ingest](#metadatareingestconfig)
* [Adding descriptive metadata to the AIP](#dcmetadata)
* [CCA file format policies](#fileformatpolicies)  

<a name="architecture"></a>  
## Archivematica configuration at CCA  

In addition to supporting fileservers, CCA's Archivematica infrastructure runs on four virtual machines (VMs):

| VM | Name | Usage |
| -------- | -------- | -------- |
| VSP-AMPL-01 | Pipeline 1 | Pipeline 1 is used for assets that are described in TMS and for which no extraction or format normalization is desired. Sample use cases: ingest a .tar of files as received by a donor which have not yet been processed, ingesting digitized A/V materials that are described in TMS. |
| VSP-AMPL-02 | Pipeline 2 | Pipeline 2 is used for assets that are described in TMS and which will be fully processed by Archivematica. This is the pipeline that should be used for processed digital archives. |
| VSP-AMPL-03 | Pipeline 3 | Pipeline 3 is used for assets that are described in Horizon. There is not yet a protocol for ingest of library materials. |
| VSP-AMSS-01 | Storage Service | The Storage Service manages storage, indexing, and retrieval of Archival Information Packages (AIPs) and conducts fixity checks of the AIP store. |

<a name="ingestmethods"></a>  
## Archivematica ingest workflows 

There are two primary methods for ingesting data into Archivematica at CCA: using [Automation Tools](https://github.com/artefactual/automation-tools) or manually through the Archivematica web dashboard.  

When possible we will use Automation Tools, as this allows for more efficient ingest and automated retrieval of metadata from TMS (and eventually, perhaps, Horizon).  

**NOTE: Because we want our AIPs to be complete and self-describing, archival description must be complete and entered into TMS for all files/SIPs prior to ingest into Archivematica.**  

<a name="autotools"></a>  
### Automation Tools  

Automation Tools is currently set up on Pipelines 1 and 2. On these VMs, Automation Tools checks the /mnt/incoming/auto-transfers directory every 5 minutes, verifies that nothing is currently being transferred or ingested, runs pre-transfer scripts (that verify the transfer is the correct type, pass the transfer's accession number on to Archivematica, and add metadata to the transfer using the TMS API), and starts the next transfer.  The rest of the transfer and ingest process is automated. 

It is the responsibility of the archivist processing digital materials to QA the results of this process and ensure that all processes completed within acceptable parameters for success.  

<a name="automationtoolsarchives"></a>  
#### Procedure for Automation Tools ingest: digital archives
Here is the procedure for conducting ingests of processed SIPs with Automation Tools:  

1. Verify that all of the following are true:  
  * Your processed SIPs are ready in /mnt/1TB_RAID on one of the BitCurator machines  
  * All SIPs are named with the scheme [identifier]---[accession number]. If SIPs consist of unprocessed material, a disk image for example, only use its identifier to name it.
  * Data entry for all SIPs has been completed in TMS  
2. Copy the SIPs to Pipeline 2 Transfer Source using the "send_to_archivematica.py" script with option "--pipeline 2":`python3 /path/to/send_to_archivematica.py --pipeline 2 '/path/to/transfer'`
3. Alert the Digital Archivist that your SIPs are ready for ingest.  
4. When the pipeline is clear, the Digital Archivist will move the appropriate SIPs to the Automation Tools watched folder for ingest in batches of <50 SIPs at a time. Archivematica will then ingest each of the SIPs, one at a time.  
5. QA the ingests, marking all information in an [Archivematica ingest spreadsheet](https://github.com/CCA-Public/digital-archives-manual/blob/master/forms/amatica_ingest_spreadsheet.xlsx):  
    * For each SIP, ensure that Transfer and Ingest completed successfully and that the AIP was stored. Click “Archival storage” at the top of the Archivematica page, and ensure all of your SIPs are there. If they are listed, then they have successfully completed. 
    * For each SIP, add the following information to your Ingest spreadsheet:  
        * Identifier  
        * Accession  
        * Fonds number  
        * Pipeline (VSP-AMPL-01 or VSP-AMPL-02 or VSP-AMPL-03)  
        * Ingest successful? (True/False)  
        * Notes  
        * AIP UUID  
        * Standard QA (True/False)  
    * For every 5th SIP, conduct a more complete QA check. Verify the following and then put "True" in the Full QA column of the Ingest spreadsheet:  
        * Look at the normalization report and ensure that no files that should have been normalized for preservation failed.  
        * Download the AIP and upload the AIP METS file to [METSFlask](http://bitarchivist.pythonanywhere.com/) for examination. Verify that Dublin Core descriptive metadata was written to the METS file, and quickly confirm that the information about the original files, particularly format identification and last modified date, appears correct. Please remember to delete your METS file from the list when you have finished.
   * You may have also received a number of normalization failure report emails from Archivematica during ingest. In instances where the failed files have exit codes 0 or 2, these can be ignored. In instances where the failed files have exit code 1, it is worth confirming that the file type is actually normalized at CCA; if so, it may be worth investigating further, as these files may need to be [manually normalized](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/arrangement.md#mannorm) and reingested.
6. When Ingest and QA is complete:
  * Inform and send a copy of your ingest spreadsheet to the Digital Archivist  
  * Save your ingest spreadsheet to the appropriate "Acquisition et traitement" folder  
  * Delete the local copy of the SIPs from the BitCurator machine 
7. Create an object package for the files in TMS corresponding to the SIPs. Send an email to Deplacement requesting that each of the files in the object package be localized with the location "Dark archive", CCing the Digital Archivist.  
8. The Digital Archivist will delete the successfully ingested SIPs from /mnt/incoming/auto-transfers (in Pipeline 1, the `transfer.py` script has been amended to delete the transfer source automatically after successful ingest, but it is still necessary to manually delete transfer sources from Pipelines 2 and 3).  

<a name="automationtoolsav"></a>  
#### Procedure for Automation Tools ingest: digitized A/V  

Procedures to come. 

<a name="webui"></a>  
### Using the Archivematica Web UI  

Alternatively, transfers may be started and monitored from within the web dashboard. Before starting, verify that the transfer type for the material you're ingesting is correct and amend the processing configuration so that it pauses the process when metadata must be entered. You will need to manually enter metadata according to the schema outlined in [Adding descriptive metadata to the AIP](#dcmetadata).  

When your processed SIPs are ready in /mnt/1TB_RAID on one of the BitCurator machines, all SIPs are named with the scheme [identifier]---[accession number], and data entry for all SIPs has been completed in TMS, advise the Digital Archivist that you are ready to move on to the Ingest phase of the project and then copy the SIPs to /mnt/incoming/transfers on the appropriate Pipeline using the "send_to_archivematica.py" script. If SIPs consist of unprocessed material, a disk image for example, only use its identifier to name it.

<a name="processingconfigs"></a>
## Archivematica processing configurations  

<a name="rawingestconfig"></a>  
### Configuration for ingest of "raw" data (Pipeline 1 default)    

| Type | Value |
| -------- | -------- |
| Send transfer to quarantine | "No" |
| Approve normalization | "Yes" |
| Store AIP | "Yes" |
| Transcribe files (OCR) | "No" |
| Generate transfer structure report | "Yes" |
| Remove from quarantine after | n/a |
| Create SIP(s) | "Create single SIP and continue processing" |
| Extract packages | "No" |
| Normalize | "Do not normalize" |
| Reminder: add metadata if desired | "Continue" |
| Examine contents | "Skip examine contents" |
| Select file format identification command (Transfer) | "Siegfried" |
| Select file format identification command (Ingest) | "Use existing data" |
| Select file format identification command (Submission documentation & metadata) | "Siegfried" |
| Delete packages after extraction | "No" |
| Select compression algorithm | "Uncompressed" |
| Select compression level | "5 - normal compression mode" |
| Store AIP | "Yes" |
| Store AIP location | *appropriate AIP store* |
| Store DIP location | "None" |  

*Note: Each AIP Store location is 5TB in size. These locations are filled sequentially. For easier integration with Automation Tools, each AIP store should be used for only one of: AIPs for which DIPs are being generated, or AIPs with no corresponding DIP.*

<a name="processedingestconfig"></a>  
### Configuration for ingest of "processed" data (Pipeline 2 default)  

| Type | Value |
| -------- | -------- |
| Send transfer to quarantine | "No" |
| Approve normalization | "Yes" |
| Store AIP | "Yes" |
| Transcribe files (OCR) | "No" |
| Generate transfer structure report | "Yes" |
| Remove from quarantine after | n/a |
| Create SIP(s) | "Create single SIP and continue processing" |
| Extract packages | "Yes" |
| Normalize | "Normalize for preservation" |
| Reminder: add metadata if desired | "Continue"|
| Examine contents | "Skip examine contents" |
| Select file format identification command (Transfer) | "Siegfried" |
| Select file format identification command (Ingest) | "Use existing data" |
| Select file format identification command (Submission documentation & metadata) | "Siegfried" |
| Delete packages after extraction | "Yes" |
| Select compression algorithm | "Uncompressed" |
| Select compression level | "5 - normal compression mode" |
| Store AIP | "Yes" |
| Store AIP location | *appropriate AIP store* |
| Store DIP location | "None" |   

*Note: CCA creates DIPs from our AIPs through the [create_dip.py](https://github.com/artefactual/automation-tools/blob/dev/aip2dip/aips/create_dip.py) script rather than through the standard Archivematica "Normalization for access" option.*  

<a name="reingestconfig"></a>  
### Configuration for re-ingest  

*Saved as processing configuration "reingest" on pipelines*

| Type | Value |
| -------- | -------- |
| Send transfer to quarantine | "No" |
| Approve normalization | "Yes" |
| Store AIP | "Yes" |
| Transcribe files (OCR) | "No" |
| Generate transfer structure report | "Yes" |
| Remove from quarantine after | n/a |
| Create SIP(s) | "Create single SIP and continue processing" |
| Extract packages | "Yes" |
| Normalize | "Normalize for preservation" |
| Reminder: add metadata if desired | "Continue" |
| Examine contents | "Skip examine contents" |
| Select file format identification command (Transfer) | "Siegfried" |
| Select file format identification command (Ingest) | "Siegfried" |
| Select file format identification command (Submission documentation & metadata) | "Siegfried" |
| Delete packages after extraction | "Yes" |
| Select compression algorithm | "Uncompressed" |
| Select compression level | "5 - normal compression mode" |
| Store AIP | "Yes" |
| Store AIP location | *appropriate AIP store* |
| Store DIP location | "None" |   

<a name="metadatareingestconfig"></a>  
### Configuration for metadata-only re-ingest  

*Saved as processing configuration "update_metadata" on pipelines*

| Type | Value |
| -------- | -------- |
| Send transfer to quarantine | "No" |
| Approve normalization | "Yes" |
| Store AIP | "Yes" |
| Transcribe files (OCR) | "No" |
| Generate transfer structure report | "Yes" |
| Remove from quarantine after | n/a |
| Create SIP(s) | "Create single SIP and continue processing" |
| Extract packages | "Yes" |
| Normalize | "Normalize for preservation" |
| Reminder: add metadata if desired | "None" |
| Examine contents | "Skip examine contents" |
| Select file format identification command (Transfer) | "Siegfried" |
| Select file format identification command (Ingest) | "Siegfried" |
| Select file format identification command (Submission documentation & metadata) | "Siegfried" |
| Delete packages after extraction | "Yes" |
| Select compression algorithm | "Uncompressed" |
| Select compression level | "5 - normal compression mode" |
| Store AIP | "Yes" |
| Store AIP location | *appropriate AIP store* |
| Store DIP location | "None" |   

<a name="dcmetadata"></a>  
## Adding descriptive metadata to the AIP  

CCA adds descriptive metadata to every AIP to aid in discoverability and re-use of data. In most cases, metadata will be entered automatically during the ingest process using [Automation Tools](https://github.com/artefactual/automation-tools) and [add-tms-metadata.py](https://github.com/CCA-Public/cca-scripts/blob/master/archivematica/add_tms_metadata.py). The `add-tms-metadata.py` script retrieves metadata using a minimal GET-only TMS API implemented by a former CCA programmer, based on similar work that was open sourced by MoMA. To retrieve some basic metadata (with limited fields) for a record in TMS, make a GET API call to `http://api.tms.cca.qc.ca/API/Object/<enter ObjectNumber here>`. For example, information for the fonds-level record for the Testa & Weiser project records (AP174) can be accessed at [http://api.tms.cca.qc.ca/API/Object/AP174](http://api.tms.cca.qc.ca/API/Object/AP174). 

CCA's local standards for metadata entry are as follows:  

| Field | Value |  
| ----- | ----- |  
| Title | Title |  
| Part of AIC | Identifier of AIC (if applicable) |  
| Creator | Archive creator (should be same as constituent in TMS) |  
| Subject | n/a |  
| Description | Scope and content note (optional) |  
| Publisher | Centre Canadien d'Architecture |  
| Contributor | n/a |  
| Date | Follow ISO8601 standards. Allowable values: YYYY, YYYY-MM, YYYY-MM-DD, YYYY/YYYY, YYYY-MM/YYYY-MM, YYYY-MM-DD/YYYY-MM-DD |  
| Format | Extent and medium statement - e.g. "10 digital files (25 MB)" |  
| Identifier | Identifier of material being ingested |  
| Source | Accession (e.g. versement) number -- for "raw" ingests, leave this blank |  
| Relation | Fonds number (AP###) -- for "raw" ingests, leave this blank |  
| Language | n/a |  
| Coverage | n/a |  
| Rights | n/a |  

<a name="fileformatpolicies"></a>
## CCA file format policies  

Current version: [Format Policy Registry, version 2](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/CCA%20Format%20Policy%20Registry%20v2%20201804.pdf) 
