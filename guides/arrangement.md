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
* [Packaging SIPs for Archivematica](#sippackaging)
* [Processing disk images with Disk Image Processor (CCA Tools)](#diskimageprocessor)  
* [Processing directories of files with Folder Processor (CCA Tools)](#folderprocessor)  

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
##### As large transfers

* (For instance, the entire contents of a hard drive or a large network transfer)  
* More likely to retain original organizational structure  
* More likely to contain unknown dependencies between files that could break with re-arrangement  
* Higher-level description and less manual arrangement in processing might be preferable 

<a name="spreadtransfers"></a>
##### Spread across smaller storage media

* Was the material spread across various media out of necessity, or does this reflect an organizational choice?  
* More likely to have detailed relationship to specific physical material (e.g. floppy in a folder with correspondence or project records)  
* Co-located records will require more active arrangement and/or more precise description  

<a name="existingorganization"></a>  
### Existing organization  

Another factor to consider is the existing organization of the material. Does the existing order appear to be meaningful? Is there evidence that this constitutes an original order, as used by the records creator? Does the existing order reflect a conscious management approach or is it just the result of material contraints of storage media (e.g. a backup split between many floppy disks or CDs due to limited storage space on each disk)? Documentation from the record creators and/or donation sources can greatly help in making these determinations.  

The original order of material must also be balanced against user needs. Is the existing order self-evident or accessible for researchers? Can it be made accessible through your file-level description? If the answer to both of these questions is no, the situation may call for rearrangement or an alternative processing approach.  

In cases where any rearrangement occurs, we will make information about the existing organization of files at time of transfer available to researchers via alternate means, such as searchable Excel documents attached to the fonds-level record.  

<a name="context"</a>
### Context of creation and active use  

An additional factor to consider is the context of the files' creation and use. What relationships, if any, do the digital materials have with analogue and physical materials in the fonds? Were records in different formats kept together when the records were in active use?  

What are the relationships between the files in the accession? Do the files link to external references (e.g. a title block used in a number of AutoCAD files)? If so, what work must be done to ensure that we do not break the links to such external resources?  

<a name="nature"></a>
### Nature of archival collection to which they belong    

Another factor to consider when thinking about arrangement is the nature of the archive to which the records belong. Did the CCA acquire the full fonds of this creator, or do the records belong to a project archive/assembled collection? Does CCA expect to receive additional accessions that will need to be integrated into the archive at a later date?  

<a name="accessrequirements"></a>  
### Access requirements  

* Archivematica-AtoM requirements  

<a name="institutionalpriorities"></a>
### Institutional priorities  

* Relationship to other CCA projects  
* Anticipated researcher use  

<a name="processingplan"></a>
## Developing a processing plan  

Once consultation copies of files, reports, and other documentation have been placed in the Catalogers network share for consultation, the processor should spend 1-2 weeks becoming familiar with the material. This takes place during or just following the Survey phase, and involves analyzing the organizational structure of the records, reading through documentation, and browsing through files on their own computer and/or one of the CAD workstations. Following this period, the Processor, Digital Archivist, Conservation, Archivist/Associate Director, and stakeholders from other CCA divisions will hold a pre-processing meeting. As part of this meeting, the participants will collectively analyze reports, draft an arrangement plan, set descriptive standards for the project (if they are to differ from typical practice), identify preservation concerns and manual file format normalization work plans (if necessary), discuss how original physical storage media will be handled, and set dates for project milestones. During the meeting, decisions will be formalized through the creation of a Processing Plan document that will live in the project "Acquisition et traitment" folder. Following the meeting, the Digital Archivist will create and pre-populate a processing spreadsheet in accordance with decisions made about arrangement for use by the Processor in the Description phase of processing.  

<a name="extensible"></a>  
## The exception: Extensible processing of born-digital records  

In some cases, based on the factors listed above, it may make more sense not to arrange born-digital records and to provide only minimal higher-level description (e.g. just a fonds or series-level record). In cases where no arrangement is done (once our Archivematica installation has been upgraded to 1.6), we will simply re-ingest the "raw" SIP in the "processed" pipeline, allowing Archivematica to normalize, characterize, and create AIPs and DIPs, and name the re-ingested package according to the material's processed identifier.  

Following this procedure, we will still end up with two versions of the data (a "raw" AIP and a "processed" AIP/DIP), but the two will only differ in terms of the interventions that the Archivematica makes in the ingest process.  

<a name="sippackaging"></a>  
## Packaging SIPs for Archivematica  

Once the content of your SIP has been decided, CCA workflow tools like [Folder Processor and Disk Image Processor](https://github.com/timothyryanwalsh/cca-tools) will help you package each SIP so that it meets our local requirements for ingest into Archivematica. All SIPs should have one of the two following structures:  

### Bagged SIP
* Submission Information Package (SIP) : Named after identifier (typically, an AP or ARCH number)  
   * bag-info.txt : bagit file  
   * bagit.txt : bagit file  
   * manifest-md5.txt : bagit file  
   * tagmanifest-md5.txt : bagit file  
   * data : bagit folder containing contents of transfer
      * objects/ : folder for digital objects to be ingested  
         * diskimage/ : (optional folder, use only when both disk image and files are ingested together)  
         * files/ : (optional folder, use only when both disk image and files are ingested together)  
      * metadata/ : folder for metadata associated with digital objects  
         * submissionDocumentation/ : folder containing any additional documentation related to the digital objects  

### Non-bagged SIP  

* Submission Information Package (SIP) : Named after identifier (typically, an AP or ARCH number)
   * objects/ : folder for digital objects to be ingested  
      * diskimage/ : (optional folder, use only when both disk image and files are ingested together)  
      * files/ : (optional folder, use only when both disk image and files are ingested together)  
   * metadata / : folder for metadata associated with digital objects  
      * checksum.md5 : manifest containing checksums for each file in objects
      * submissionDocumentation/ : folder containing any additional documentation related to the digital objects  
 
<a name="diskimageprocessor"></a>  
## Processing disk images with Disk Image Processor (CCA Tools)  

lorem ipsum  

<a name="folderprocessor"></a>  
## Processing directories of files with Folder Processor (CCA Tools)  

lorem ipsum  
