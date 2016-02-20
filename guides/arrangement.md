# Arrangement of born-digital archives  

The first step of processing archives (whether in digital or analog formats) is arrangement. This guide describes CCA's approach to arrangement of born-digital archives, and includes:  

* [Arrangement of born-digital archives in principle](#arrprinciple)
* [Factors affecting the arrangement of born-digital records](#arrfactors)
    * [How the records arrive at CCA](#howarrive)
         * [As large transfers](#largetransfers)
         * [Spread across smaller storage media](#spreadtransfers)
    * [Existing organization](#existingorganization)
    * [Context of creation and active use](#context)
    * [Nature of archival collection to which they belong](#nature)
    * [Access requirements](#accessrequirements)
    * [Institutional priorities](#institutionalpriorities)
* [Developing a processing plan](#processingplan)
* [The exception: Extensible processing of born-digital records](#extensible)

<a name="arrprinciple"></a>  
## Arrangement of born-digital archives in principle  

There are a number of potential approaches to arranging born-digital records, especially when these records comprise only part of a larger, hybrid archive. Born-digital records can be arranged:  

* In a separate "born-digital" series (e.g. Fonds -> Series: Digital files)  
* In separate "born-digital" sub-series within existing series (e.g. Fonds -> Series: Projects -> Sub-series: Digital files)  
* Co-arranged with other formats (e.g. Fonds -> Series: Projects -> Project File: Example Project -> File-level group of digital 3D models)  

At CCA, we may take any of these approaches for a born-digital processing project. Which approach is taken depends on a number of [factors](#arrfactors), including but not limited to institutional priorities, the way in which the records arrived at CCA, the records' existing state of organization, the context of the records' creation and active use, anticipated researcher use, and the requirements of our access interface for born-digital archives. Most often, we will seek to co-arrange born-digital records with similar records in other formats when possible.  

As with physical materials, the level of work involved in arrangement will vary between fonds and processing projects. In some instances it may mean keeping and describing all files from a single piece of media together as a file-level group. In other cases it may mean identifying different directories that were stored together on the same physical media as separate file-level groups and arranging them into different project files or series, or intellectual co-locating files that had been saved on separate pieces of storage media.  

Except in extraordinary circumstances (which should be discussed with the Digital Archivist in pre-processing meetings and/or check-ins during processing), seek to arrange directories, not individual files.  

<a name="arrfactors"></a>  
## Factors affecting the arrangement of born-digital records  

As noted above, arrangement practices will vary depending on a number of factors. These include:  

<a name="howarrive"></a>  
### How the records arrive at CCA  

One of these factors is how the material arrived at CCA: as one or a few large transfer(s) (such as a hard drive or a network transfer) or spread across many smaller pieces of storage media (such as floppy disks or CDs). The realities of how born-digital records were stored and arrive at CCA sets the parameters for our approach to arrangement during processing.  

<a name="largetransfers"></a>  
#### As large transfers

* (For instance, the entire contents of a hard drive or a large network transfer)  
* More likely to retain original organizational structure  
* More likely to contain unknown dependencies between files that could break with re-arrangement  
* Higher-level description and less manual arrangement in processing might be preferable 

<a name="spreadtransfers"></a>
#### Spread across smaller storage media

* Was the material spread across various media out of necessity, or does this reflect an organizational choice?  
* More likely to have detailed relationship to specific physical material (e.g. floppy in a folder with correspondence or project records)  
* Co-located records will require more active arrangement and/or more precise description  

<a name="existingorganization"></a>  
### Existing organization  

* Is the existing order meaningful? Original? Does the existing order reflect a conscious records management approach or was it just a result of the material constraints of the storage media?  
* Is the existing order self-evident or accessible for researchers?  

<a name="context"</a>
### Context of creation and active use  

* Relationship with analogue/physical materials  
* File types & external references  
* Influence of personal or corporate records management practices  

<a name="nature"></a>
### Nature of archival collection to which they belong    

* Fonds?  
* Project archive?  
* Are we expecting additional accessions?  

<a name="accessrequirements"></a>  
### Access requirements  

* Archivematica-AtoM requirements  

<a name="institutionalpriorities"></a>
### Institutional priorities  

* Relationship to other CCA projects  
* Anticipated researcher use  

<a name="processingplan"></a>
## Developing a processing plan  

Once consultation copies of files, reports, and other documentation have been placed in the Catalogers network share for consultation, the processor should spend 1-2 weeks becoming familiar with the material. This involves analyzing the organizational structure of the records, reading through documentation, and browsing through files on their own computer and/or one of the CAD workstations. Following this period, the Processor, Digital Archivist, Conservation, and optionally the Archivist/Associate Director will hold a pre-processing meeting. During this meeting, the participants will collectively analyze reports, draft an arrangement plan, set descriptive standards for the project (if they are to differ from typical practice), identify preservation concerns and manual file format normalization work plans (if necessary), discuss how original physical storage media will be handled, and set dates for project milestones. During the meeting, decisions will be formalized through the creation of a Processing Plan document that will live in the project "Acquisition et traitment" folder. Following the meeting, the Processor and Digital Archivist will create a pthe Digital Archivist will create and pre-populate a processing spreadsheet in accordance with decisions made about arrangement for use by the Processor in the Description phase of processing.  

<a name="extensible"></a>  
## The exception: Extensible processing of born-digital records  

In some cases, based on the factors listed above, it may make more sense not to arrange born-digital records and to provide only minimal higher-level description (e.g. just a fonds or series-level record). In cases where no arrangement is done (once our Archivematica installation has been upgraded to 1.5), we will simply re-ingest the "raw" SIP in the "processed" pipeline, allowing Archivematica to normalize, characterize, and create AIPs and DIPs, and name the re-ingested package according to the material's processed identifier.  

Following this procedure, we will still end up with two versions of the data (a "raw" AIP and a "processed" AIP/DIP), but the two will only differ in terms of the interventions that the Archivematica makes in the ingest process.