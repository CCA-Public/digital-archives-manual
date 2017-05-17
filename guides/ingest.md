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

TEXT

<a name="autotools"></a>  
### Automation Tools  

TEXT

<a name="webui"></a>  
### Using the Archivematica Web UI  

TEXT

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
