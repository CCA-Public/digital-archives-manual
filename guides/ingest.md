# Ingesting processed born-digital archives into the CCA digital repository  

This page describes the configurations and policies utilized by Archivematica during ingest. It includes:  

* [Archivematica processing configuration for ingest of "raw" data](#rawingestconfig)  
* [Archivematica processing configuration for ingest of "processed" data](#processedingestconfig) 
* [Adding descriptive metadata to the AIP](#dcmetadata)
* [CCA file format policies](#fileformatpolicies)  
* [Future developments with Archivematica](#amaticadevelopments)  

<a name="rawingestconfig"></a>  
## Archivematica processing configuration for ingest of "raw" data  

| Type | Checked? | Option |
| -------- | -------- | -------- |
| Send transfer to quarantine | yes | "No" |
| Approve normalization | yes | "Yes" |
| Store AIP | yes | "Yes" |
| Transcribe files (OCR) | yes | "No" |
| Generate transfer structure report | yes | "Yes" |
| Remove from quarantine after | no | n/a |
| Create SIP(s) | yes | "Create single SIP and continue processing" |
| Extract packages | yes | "No" |
| Normalize | yes | "Do not normalize" |
| Reminder: add metadata if desired | no | n/a |
| Examine contents | yes | "Skip examine contents" |
| Select file format identification command (Transfer) | yes | "Siegfried" |
| Select file format identification command (Ingest) | yes | "Siegfried" |
| Select file format identification command (Submission documentation & metadata) | yes | "Siegfried" |
| Delete packages after extraction | yes | "Yes" |
| Select compression algorithm | yes | "7z using bzip2" |
| Select compression level | yes | "5 - normal compression mode" |
| Store AIP location | yes | "Dark Archive AIP Storage" |
| Store DIP location | yes | "Media Archive dip storage" |  

<a name="processedingestconfig"></a>  
## Archivematica processing configuration for ingest of "processed" data  

| Type | Checked? | Option |
| -------- | -------- | -------- |
| Send transfer to quarantine | yes | "No" |
| Approve normalization | yes | "Yes" |
| Store AIP | yes | "Yes" |
| Transcribe files (OCR) | yes | "No" |
| Generate transfer structure report | yes | "Yes" |
| Remove from quarantine after | no | n/a |
| Create SIP(s) | yes | "Create single SIP and continue processing" |
| Extract packages | yes | "Yes" |
| Normalize | yes | "Normalize for preservation and access" |
| Reminder: add metadata if desired | no | n/a |
| Examine contents | yes | "Examine contents" |
| Select file format identification command (Transfer) | yes | "Siegfried" |
| Select file format identification command (Ingest) | yes | "Siegfried" |
| Select file format identification command (Submission documentation & metadata) | yes | "Siegfried" |
| Delete packages after extraction | yes | "Yes" |
| Select compression algorithm | yes | "7z using bzip2" |
| Select compression level | yes | "5 - normal compression mode" |
| Store AIP location | yes | "Dark Archive AIP Storage" |
| Store DIP location | yes | "Media Archive dip storage" |  

<a name="dcmetadata"></a>  
## Adding descriptive metadata to the AIP  

CCA adds descriptive metadata to every AIP to aid in discoverability and re-use of data. In most cases, metadata will be entered automatically after being pulled from TMS or a processing spreadsheet (TBD). CCA's local standards for metadata entry are as follows:  

| Field | Value |  
| ----- | ----- |  
| Title | Title of groupe |  
| Part of AIC | Identifier of AIC (if applicable) |  
| Creator | Creator of archive (should be same as constituent in TMS) |  
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
| Coverage | Identifier of parent (series, subseries, or project) -- for "raw" ingests, leave this blank |  
| Rights | n/a |  

<a name="fileformatpolicies"></a>
## CCA file format policies  

Currently in process of being reviewed. When complete, CCA's file format policies will be published as a document and implemented in our local instance of the Archivematica Format Policy Registry (FPR) 

<a name="amaticadevelopments"></a>
## Future developments with Archivematica  

* Appraisal tab (AM/1.6) - triage and arrangement inside Archivematica interface  
* Access system - may require changes to local metadata schema  
* Automation Tools - will allow for watched directories, "drag and drop" ingest  
