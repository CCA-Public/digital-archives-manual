# Arrangement of born-digital archives  

The first step of processing archives (whether in digital or analog formats) is arrangement. This guide describes CCA's approach to arrangement of born-digital archives, and includes:  

* [Arrangement of born-digital archives in principle](#arrprinciple)
* [Factors affecting the arrangement of born-digital records](#arrfactors)
    * [How the records arrive at CCA](#howarrive)
         * [As large transfers](#largetransfers)
         * [Spread across smaller storage media](#spreadtransfers)
    * [Existing organization](#existingorganization)
    * [Context of creation and active use](#context)  
    * [Archivematica requirements](#archivematicarequirements)
    * [Nature of archival collection to which they belong](#nature)
    * [Institutional priorities](#institutionalpriorities)
* [Developing a processing plan](#processingplan)
* [The exception: Extensible processing of born-digital records](#extensible)
* [Packaging SIPs for Archivematica](#sippackaging)
* [Processing disk images with Disk Image Processor](#diskimageprocessor)  
* [Processing directories of files with Folder Processor](#folderprocessor)  
* [Creating single SIPs from directories and files with SIP Creator](#sipcreator)  
* [Manual normalization for Archivematica](#mannorm)
* [Processing forward-migrated files](#processfm)

<a name="arrprinciple"></a>  
## Arrangement of born-digital archives in principle  

There are a number of potential approaches to arranging born-digital records, especially when these records comprise only part of a larger, hybrid archive. Born-digital records can be arranged:  

* In a separate "born-digital" series (e.g. Fonds -> Series: Digital files)  
* In separate "born-digital" sub-series within existing series (e.g. Fonds -> Series: Projects -> Sub-series: Digital files)  
* Co-arranged with other formats (e.g. Fonds -> Series: Projects -> Project File: Example Project -> File-level group of digital 3D models)  

At CCA, we may take any of these approaches for a born-digital processing project. Which approach is taken depends on a number of [factors](#arrfactors), including but not limited to institutional priorities, the way in which the records arrived at CCA, the records' existing state of organization, the context of the records' creation and active use, anticipated researcher use, and the requirements of our access interface for born-digital archives. Most often, we will seek to co-arrange born-digital records with similar records in other formats when possible.  

As with physical materials, the level of work involved in arrangement will vary between fonds and processing projects. In some instances it may mean keeping and describing all files from a single piece of media together as a file-level group. In other cases it may mean identifying different directories that were stored together on the same physical media as separate file-level groups and arranging them into different project files or series, or intellectually co-locating files that had been saved on separate pieces of storage media.  

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

Another factor to consider is the existing organization of the material. Does the existing order appear to be meaningful? Is there evidence that this constitutes an original order, as used by the records creator? Does the existing order reflect a conscious management approach or is it just the result of material constraints of storage media (e.g. a backup split between many floppy disks or CDs due to limited storage space on each disk)? Documentation from the record creators and/or donation sources can greatly help in making these determinations.  

The original order of material must also be balanced against user needs. Is the existing order self-evident or accessible for researchers? Can it be made accessible through your fonds, series, and file-level descriptions? If the answer to both of these questions is no, the situation may call for rearrangement or an alternative processing approach.  

In cases where any rearrangement occurs, we will make information about the existing organization of files at time of transfer available to researchers via alternate means, such as searchable Excel documents attached to the fonds-level record.  

<a name="context"></a>
### Context of creation and active use  

An additional factor to consider is the context of the files' creation and use. What relationships, if any, do the digital materials have with analogue and physical materials in the fonds? Were records in different formats kept together when the records were in active use?  

What are the relationships between the files in the accession? Do the files link to external references (e.g. a title block used in a number of AutoCAD files)? If so, what work must be done to ensure that we do not break the links to such external resources?  

<a name="nature"></a>
### Nature of archival collection to which they belong    

Another factor to consider when thinking about arrangement is the nature of the archive to which the records belong. Did the CCA acquire the full fonds of this creator, or do the records belong to a project archive/assembled collection? Does CCA expect to receive additional accessions that will need to be integrated into the archive at a later date?  

<a name="archivematicarequirements"></a>  
### Archivematica requirements  

Transfers of more than 15-20,000 files or so must be split into multiple AIPs. These can then be recombined in Archivematica in an Archival Information Collection (AIC). Future versions of Archivematica should address the scaling issues that necessitate splitting large collections across multiple transfers.   

<a name="institutionalpriorities"></a>
### Institutional priorities  

* Relationship to other CCA projects  
* Anticipated researcher use  

<a name="processingplan"></a>
## Developing a processing plan  

Once consultation copies of files, reports, and other documentation have been placed in the Catalogers network share for consultation, the processor should spend 1-2 weeks becoming familiar with the material. This takes place during or just following the Survey phase, and involves analyzing the organizational structure of the records, reading through documentation, and browsing through files on their own computer and/or one of the CAD workstations.  

Following this period, the Processor, Digital Archivist, Conservation, Archivist/Associate Director, and stakeholders from other CCA divisions will hold a pre-processing meeting. As part of this meeting, the participants will collectively analyze reports, draft an arrangement plan, set descriptive standards for the project (if they are to differ from typical practice), identify preservation concerns and manual file format normalization work plans (if necessary), discuss how original physical storage media will be handled, and set dates for project milestones. During the meeting, decisions will be formalized through the creation of a Processing Plan document that will live in the project "Acquisition et traitement" folder.  

<a name="extensible"></a>  
## The exception: Extensible processing of born-digital records  

In some cases, based on the factors listed above, it may make more sense not to arrange born-digital records and to provide only minimal higher-level description (e.g. just a fonds or series-level record). In cases where no arrangement is done (once our Archivematica installation has been upgraded to 1.6), we will simply ingest the "raw" SIP in the "processed" pipeline, allowing Archivematica to normalize, characterize, and create AIPs and DIPs, and name the re-ingested package according to the material's processed identifier.  

<a name="sippackaging"></a>  
## Packaging SIPs for Archivematica  

Once the content of your SIP has been decided, CCA workflow tools like [Folder Processor and Disk Image Processor](https://github.com/CCA-Public/cca-tools) will help you package each SIP so that it meets our local requirements for ingest into Archivematica. All SIPs should have one of the two following structures:  

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

### Non-bagged SIP (preferred)  

* Submission Information Package (SIP) : Named after identifier (typically, an AP or ARCH number)
   * objects/ : folder for digital objects to be ingested  
      * diskimage/ : (optional folder, use only when both disk image and files are ingested together)  
      * files/ : (optional folder, use only when both disk image and files are ingested together)  
   * metadata / : folder for metadata associated with digital objects  
      * checksum.md5 : manifest containing checksums for each file in objects
      * submissionDocumentation/ : folder containing any additional documentation related to the digital objects  
 
<a name="diskimageprocessor"></a>  
## Processing disk images with Disk Image Processor 

*Instructions valid for Disk Image Processor v1.0.0*

[Disk Image Processor](https://github.com/CCA-Public/diskimageprocessor) takes a folder of disk images and turns each into a ready-to-ingest SIP packaged for Archivematica. The tool also writes a pre-populated description spreadsheet including information for each SIP. SIPs include an md5deep-generated checksum.md5 file in the "metadata" directory by default, but can optionally be bagged instead. The tool populates each "objects" directory with a raw disk image (even if the source disk image is EWF/E01) and logical files carved with either tsk_recover or the HFSExplorer command line utility unhfs. Files in the source directory that are not disk images are ignored (the exception to this is files that share the same basename, such as .info sidecar metadata files for disk images, which will be copied into the "objects/diskimage" file at the end of processing.)  

This workflow assumes that each piece of storage media in an accession will be assigned a file-level description. If the contents of media are to be split into multiple files, a different approach is required.  

For this walkthrough we will start with an example directory containing 4 disk images:  

![diskimage1](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/diskimage1.png)  

Steps:  

* Double-click on the "Disk Image Processor" icon in the "CCA Tools" folder on the Bitcurator desktop.  

![diskimage2](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/diskimage2.png)  

* Enter the path of the source folder containing the disk images in "Source" (or select using the "Browse" button) and the path of a new folder for the outputs in "Destination". Choose between your desired options. Press the "Start" button to begin processing.  

![diskimage3](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/diskimage3.png)  

* When the tool has finished processing, in the Destination folder you will now see the following: a CSV file containing pre-populated archival description for each disk image, a log file for the Disk Image Processor tool, and a folder containing each processed SIP.  

![diskimage6](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/diskimage6.png)  

![diskimage7](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/diskimage7.png)  

* Each individual SIP contains a standard structure, as demonstrated in the picture below. At the highest level, the SIP contains "object" and "metadata" folders. The "object" folder is further subdivided to contain a copy of a raw disk image for the disk, and a copy of all of the logical files carved from the disk image. The "metadata" folder contains a checksum.md5 file that can later be used by Archivematica to ensure file fixity and a "submissionDocumentation" folder, which contains a Brunnhilde report for the SIP, a DFXML file for the disk image, and a text file containing the disktype output for the raw disk image.  

![diskimage8](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/diskimage8.png)  

* From here, simply continue to describe the SIPs in the spreadsheet and rename the SIP directories with the following scheme: [identifier]---[accession number].    


<a name="folderprocessor"></a>  
## Processing directories of files with Folder Processor  

[Folder Processor](https://github.com/CCA-Public/folderprocessor) allows users to create consistently-packaged SIPs from each of any number of selected input directories. Each SIP is packaged for Archivematica and contains a copy of the files, an md5 manifest, a DFXML file, and Brunnhilde reports.

![folderprocessor](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/folderprocessor.png)

To create SIPs with Folder Processor:

* Press the "Select source" button at the top of the GUI and choose the directory you want to be able to select input directories from. The "Directory Selector" window will then populate with a checkbox interface.  
* Select all directories you wish to create SIPs from by checking the box to the left of the directory name. Any files that are selected will be ignored.  
* Input the destination for your SIPs in "Destination", either by entering the path directory in the box or by selecting a folder using the "Browse" button. If you do the latter, double-check to make sure that the correct path is entered in the box before moving on (it is easy to accidentally select a directory above what you intend when creating new output directories through the GUI).  
* If desired, select the "Bag SIPs" or "Run bulk_extractor" options. In most cases, leave these unchecked.  
* When you are ready to start, press the "Create SIPs" button. The process will begin working, and the Status bar should increment for each directory that is successfully turned into a SIP. Be patient - for large input directories, this can take some time. If you need to cancel the process at any time, you can use the "Cancel" button in the lower-right corner of the GUI.  
* When the process is completed, the destination directory will contain a description CSV (containing pre-populated archival description for the SIPs) and a directory containing each of the SIPs. From here, simply continue to describe the SIPs in the spreadsheet and rename the SIP directories with the following scheme: [identifier]---[accession number]. Original directory names are retained in the SIP within the "objects" directory.  

<a name="sipcreator"></a>  
## Creating single SIPs from directories and files with SIP Creator  

[SIP Creator](https://github.com/CCA-Public/sipcreator) allows users to create a single SIP from any number of input directories and files. The resulting SIP is packaged for Archivematica and contains a copy of the files, an md5 manifest, a DFXML file, and Brunnhilde reports.

![sipcreator](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/sipcreator.png)

To create SIPs with SIP Creator:

* Press the "Select source" button at the top of the GUI and choose the directory you want to be able to select files from. The "Directory Selector" window will then populate with a checkbox interface.  
* Select all files and directories you wish to add to the SIP by checking the box to the left of the file name.  
* Input the destination for your SIPs in "Destination", either by entering the path directory in the box or by selecting a folder using the "Browse" button. If you do the latter, double-check to make sure that the correct path is entered in the box before moving on (it is easy to accidentally select a directory above what you intend when creating new output directories through the GUI).  
* If desired, select the "Bag SIP" or "Run bulk_extractor" options. In most cases, leave these unchecked.  
* When you are ready to start, press the "Create SIP" button. The process will begin working, and the Status bar should increment once when the SIP is created, and again when the description CSV has been generated. Be patient - for large SIPs, this can take some time. If you need to cancel the process at any time, you can use the "Cancel" button in the lower-right corner of the GUI.  
* When the process is completed, the destination directory will contain a description CSV (containing pre-populated archival description for the SIPs) and a directory containing the newly generated SIP. From here, simply continue to describe the SIP in the spreadsheet (you may want to copy and paste this line into an existing spreadsheet so that there isn't a spreadsheet for every file) and rename the SIP directory with the following scheme: [identifier]---[accession number].  

<a name="mannorm"></a>
## Manual normalization for Archivematica

There are instances where Archivematica will not automatically normalize files into their preservation formats. This primarily occurs in instances where a file type is not up to specification and not recognized by Siegfried, but still has the expected playback. (See the MP3s manipulated by Virtools software in AP167: ONL NSA Muscle project records for an example.) When this occurs, these file types will have to be manually normalized for preservation.

* Create the SIP as usual.
* In the *objects* folder, create a folder titled *manualNormalization*. 
* In *manualNormalization*, create a folder titled *preservation*.
* In *preservation*, manually recreate the directory structure beginning with the top directory. 
* Normalize the file type(s) using the command line if possible. Save them to the directory in *preservation* that corresponds with their original directory.

The final directory structure of the SIP should look like: 

* top directory 
     * metadata
     * objects
          * top directory name (with objects)
          * manualNormalization
               * preservation
                    * top directory name
                         * recreated directory structure
                              * preservation copies
                              
* Update the checksum.md5 file accordingly. In order to do this, delete the original checksum.md5 file in Top Directory/metadata. Open Terminal, and cd into this folder. Then run the following script to create a new manifest: 
```
md5deep -rl ../objects > checksum.md5
```
In some cases after ingest, the Archivematica report for the manually normalized SIP will have a status of "failed" for "Relate manual normalized preservation files to the original files." According to Archivematica, this occurs when two or more files have the same name. In practice, it also often occurs when there are a large number of files in a SIP or if the SIP has a complicated directory hierarchy. 

To resolve the error, create a normalization.csv spreadsheet following the guidelines <a href="https://www.archivematica.org/en/docs/archivematica-1.6/user-manual/ingest/manual-normalization/#normalizing-files-with-the-same-name">here</a>, update the checksum, and reingest the SIP. 

<a name="processfm"></a>
## Processing forward-migrated files

For exhibition, research and access purposes, some records which are part of the Archaeology of the Digital ensemble were migrated to a more recent version of their original format. These new versions of the records could be used as access copies, as they are easier to consult with the CCA’s existing equipment. Below are the guidelines allowing to retain these records and to provide access to them while preserving the link to their original versions.

Gather the forward-migrated files into one top-level file folders corresponding to an existing file-level description. It is not necessary to recreate directories as the original structure will be provided by listing the file paths in the archival description. 

Name the new file folder by using the reference number of its source and add FM (forward-migrated) at the end. For example, if the original folder is numbered AP222.S2.002, the folder containing its forward-migrated files will be identified as AP222.S2.002.FM. 
SIPs may now be created with SIP Creator. Complete the SIP’s identification number with its related accession number: e.g. AP222.S2.002.FM---AR2020.0056

There may be instances where, in the future, another migration event will occur. For example, a new software version may be released or CCA might obtain new software for previously unaccessible files. In this instance, create a new SIP with the new forward-migrated files, and retain the old one. The numbering schema is as follows: AP222.S2.002.FM1, AP222.S2.002.FM2, etc.

A corresponding description record needs to be added in TMS. It should be arranged alongside its originating file-level description (“est inclus dans” the same series or project). It should also be related to the accession with “provient de”. Refer to the FILE descriptive standard for general guidance and to the following for more specific considerations:

* Reference code (ISAD(G) 3.1.1)/Object Number:
   * Duplicate original file reference number and add “FM”: e.g.:  AP222.S2.002.FM
* Title (ISAD(G) 3.1.2)/Title:
   * Follow titling guidelines for File-level description. Title must indicate the nature of files (i.e. they are forward-migrated versions). Title should include some level of detail about the formats whenever possible as to increase access to records. e.g. "Forward-migrated formZ 6 and 7 files for 3 of RUR digital working files"
* Scope and content note (ISAD(G) 3.3.1)/Description du contenu:
   * Detail and contextualize files which were migrated: list file paths of original file and indicate any specificity to new file versions if they do not appear in the processing spreadsheet. Refer to the original’s file description identification number.Add information about the migration process, if known: who, how, when and why.
   e.g. "Files were migrated by a CCA collaborator in 2014 as part of the preparation for the Archeology of the Digital Complexity and Convention exhibit."
* Physical characteristics and technical requirements (ISAD(G) 3.4.4)/Physical Description field:
   * Indicate designated software for file access. e.g. “Files may be accessed using form\*Z version 6 to 8.”
   
Finally, in the scope and content note for the folder with the original files (e.g. AP222.S2.002), indicate that the files have been migrated to a more recent software version and provide the folder titles for the forward-migrated files (e.g. AP222.S2.002.FM). List the forward-migrated files and their file paths, and indicate their software version.

If the number of files would make this type of list difficult to include in TMS, the archivists should move the list to a log or readme file in the forward-migrated SIP.
