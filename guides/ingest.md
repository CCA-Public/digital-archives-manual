# Ingesting processed born-digital archives into the CCA digital repository  

*Current version of Archivematica: 1.6.0*  

This page describes the configurations and policies utilized by Archivematica during ingest. It includes:  

* [Methods for ingesting digital archives into Archivematica](#ingestmethods)  
  * [Automation Tools](#automationtools)  
  * [Using the Archivematica Web UI](#webui)  
* [Archivematica processing configuration for ingest of "raw" data](#rawingestconfig)  
* [Archivematica processing configuration for ingest of "processed" data](#processedingestconfig) 
* [Adding descriptive metadata to the AIP](#dcmetadata)
* [CCA file format policies](#fileformatpolicies)  

<a name="ingestmethods"></a>  
## Methods for ingesting digital archives into Archivematica  

There are two primary methods for ingesting data into Archivematica at CCA: using [Automation Tools](https://github.com/artefactual/automation-tools) or manually through the Archivematica web dashboard.  

When possible, we will use Automation Tools, as this allows for more efficient ingest and automated addition of metadata from TMS.  

**NOTE: Because we want our AIPs to be complete and self-describing, archival description must be complete and entered into TMS for all files/SIPs prior to ingest into Archivematica.**  

<a name="autotools"></a>  
### Automation Tools  

Automation Tools is currently set up only for ingest of "processed" data and only on csp-arch-03 (this will change soon). Automation Tools checks the /mnt/incoming/auto-transfers directory on csp-arch-03 every 5 minutes, verifies that nothing is currently being transferred or ingested, runs pre-transfer scripts (that verify the transfer is the correct type, pass the transfer's accession number on to Archivematica, and add metadata to the transfer using the TMS API), and starts the next transfer.  The rest of the transfer and ingest process is automated. Your job as a processing archivist is simply to QA the results of this process and ensure that all processes completed within acceptable parameters for success.  

Here is the procedure for conducting ingests of processed SIPs with Automation Tools:  

1. When your processed SIPs are ready in /mnt/1TB_RAID on one of the BitCurator machines, all SIPs are named with the scheme [identifier]---[accession number], and data entry for all SIPs has been completed in TMS, advise the Digital Archivist that you are ready to move on to the Ingest phase of the project.  
2. The Digital Archivist will copy the SIPs to the /mnt/incoming/transfers "staging area" on csp-arch-03 using rsync and schedule a time for ingest.  
3. When it is time for ingest, the Digital Archivist will move the appropriate SIPs to the Automation Tools watched folder for ingest in batches of <50 SIPs at a time. Archivematica will then ingest each of the SIPs, one at a time.  
4. QA the ingests, marking all information in an [Archivematica ingest spreadsheet](https://github.com/timothyryanwalsh/cca-digitalarchivesmanual/blob/master/forms/amatica_ingest_spreadsheet.xlsx):  
    * For each SIP, ensure that Transfer and Ingest completed successfully and that the AIP was stored.  
    * For each SIP, add the following information to your Ingest spreadsheet:  
        * Identifier  
        * Accession  
        * Fonds number  
        * Pipeline (csp-arch-02 or csp-arch-03)  
        * Ingest successful? (True/False)  
        * Notes  
        * AIP UUID  
        * Standard QA (True/False)  
    * For every 5th SIP, conduct a more complete QA check. Verify the following and then put "True" in the Full QA column of the Ingest spreadsheet:  
        * Look at the normalization report and ensure that no files that should have been normalized for preservation failed.  
        * Download the AIP and look at the METS file and ensure that descriptive metadata was written to the dmdSec.   
5. When Ingest and QA is complete, inform the Digital Archivist, save your ingest spreadsheet to the appropriate "Acquisition et traitement" folder, and delete the local copy of the SIPs from the BitCurator machine.  
6. Create an object package for the files in TMS corresponding to the SIPs. Send an email to Deplacement requesting that each of the files in the object package be localized with the location "Dark archive", CCing the Digital Archivist.  

<a name="webui"></a>  
### Using the Archivematica Web UI  

Alternatively, transfers may be started and monitored from within the web dashboard. Before starting, verify that the transfer type for the material you're ingesting is correct and amend the processing configuration so that it pauses the process when metadata must be entered. You will need to manually enter metadata according to the schema outlined in [Adding descriptive metadata to the AIP](#dcmetadata).  

 When your processed SIPs are ready in /mnt/1TB_RAID on one of the BitCurator machines, all SIPs are named with the scheme [identifier]---[accession number], and data entry for all SIPs has been completed in TMS, advise the Digital Archivist that you are ready to move on to the Ingest phase of the project. The Digital Archivist will copy the SIPs to the /mnt/incoming/transfers "staging area" on csp-arch-03 using rsync and schedule a time for ingest.  

<a name="rawingestconfig"></a>  
## Archivematica processing configuration for ingest of "raw" data (currently default on csp-arch-02)    

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
| Reminder: add metadata if desired | n/a |
| Examine contents | "Skip examine contents" |
| Select file format identification command (Transfer) | "Siegfried" |
| Select file format identification command (Ingest) | "Use existing data" |
| Select file format identification command (Submission documentation & metadata) | "Siegfried" |
| Delete packages after extraction | "No" |
| Select compression algorithm | "Uncompressed" |
| Select compression level | "5 - normal compression mode" |
| Store AIP location | yes | "Dark Archive AIP Storage" |
| Store DIP location | "None" |  

<a name="processedingestconfig"></a>  
## Archivematica processing configuration for ingest of "processed" data (currently default on csp-arch-03)  

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
| Reminder: add metadata if desired | n/a |
| Examine contents | "Skip examine contents" |
| Select file format identification command (Transfer) | "Siegfried" |
| Select file format identification command (Ingest) | "Use existing data" |
| Select file format identification command (Submission documentation & metadata) | "Siegfried" |
| Delete packages after extraction | "Yes" |
| Select compression algorithm | "Uncompressed" |
| Select compression level | "5 - normal compression mode" |
| Store AIP location | yes | "Dark Archive AIP Storage" |
| Store DIP location | "None" |   

*Note: Normalization for access will begin post-sponsored development for more appropriate DIPs.*

<a name="dcmetadata"></a>  
## Adding descriptive metadata to the AIP  

CCA adds descriptive metadata to every AIP to aid in discoverability and re-use of data. In most cases, metadata will be entered automatically during the ingest process using [Automation Tools](https://github.com/artefactual/automation-tools) and [add-tms-metadata.py](https://github.com/timothyryanwalsh/cca-scripts/blob/master/add_tms_metadata.py). CCA's local standards for metadata entry are as follows:  

| Field | Value |  
| ----- | ----- |  
| Title | Title |  
| Part of AIC | Identifier of AIC (if applicable) |  
| Creator | Creator of archive creator (should be same as constituent in TMS) |  
| Subject | n/a |  
| Description | Scope and content note (optional) |  
| Publisher | Centre Canadien d'Architecture |  
| Contributor | n/a |  
| Date | Follow ISO8601 standards. Allowable values: YYYY, YYYY-MM, YYYY-MM-DD, YYYY/YYYY, YYYY-MM/YYYY-MM, YYYY-MM-DD/YYYY-MM-DD |  
| Format | n/a |  
| Identifier | Identifier of material being ingested |  
| Source | Accession (e.g. versement) number -- for "raw" ingests, leave this blank |  
| Relation | Fonds number (AP###) -- for "raw" ingests, leave this blank |  
| Language | n/a |  
| Coverage | Identifier of immediate parent (series, subseries, or project) -- for "raw" ingests, leave this blank |  
| Rights | n/a |  

<a name="fileformatpolicies"></a>
## CCA file format policies  

Currently in process of being reviewed. When complete, CCA's file format policies will be published as a document and implemented in our local instance of the Archivematica Format Policy Registry (FPR).  
