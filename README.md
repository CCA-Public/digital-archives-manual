# CCA Digital Archives Processing Manual

This is the CCA's processing manual for born-digital archives. It is a living, continually edited document that functions as a component of the larger CCA Processing Manual. The Digital Archives Processing Manual covers each step of the processing process, including capture of data, arrangement, description, ingest into our Archivematica-based digital repository, and access. It includes general policies and procedures as well as specific information about tools used in this process.

## Table of Contents

### Overview

* **[Detailed guides](#details)**
* **[Introduction to processing born-digital archives](#processingintro)**
* **[Born-digital archives workflow at a glance](#overview)** 
* **[Layperson's primer on digital preservation at CCA](#primer)**

<a name="details"></a>  
### Detailed guides  

* **[Accession and stabilization](guides/stabilization.md)**
    * [Network transfers](guides/stabilization.md/#networktransfer)
    * [Temporary physical media](guides/stabilization.md/#temporarymedia)
    * [Original physical media](guides/stabilization.md/#originalphysicalmedia)  
    * [Ingesting "raw" accession data into digital repository](guides/stabilization.md/#rawingest)  
* **[Disk imaging original physical media](guides/diskimaging.md)**
   * [Disk imaging with Guymager (Bitcurator)](guides/diskimaging.md/#guymager)  
   * [Disk imaging with FTK Imager](guides/diskimaging.md/#ftkimager)
   * [Disk imaging with IsoBuster](guides/diskimaging.md/#isobuster)
   * [Disk imaging 5.25" floppy disks with FC5025](guides/diskimaging.md/#fc5025)
   * [Disk imaging with the Kryoflux](guides/diskimaging.md/#kryoflux)
* **[Pre-processing: Triage and evaluation](guides/triage.md)**  
    * [Analyzing disk images with Disk Image Processor](guides/triage.md/#analysis)
   * [Extracting files from disk images](guides/triage.md/#diskimageextract)  
       * [Extracting files from disk images with Bitcurator](guides/triage.md/#bitcuratorfiles)  
         * [BitCurator Reporting Tool - File Access](guides/triage.md/#bcaccess)  
         * [Mount Disk Image script](guides/triage.md/#mountscript)  
       * [Extracting files from disk images with FTK Imager](guides/triage.md/#ftkimagerfiles)  
       * [Extracting files from images of Hierarchical File System (HFS) disks](guides/triage.md/#hfsfiles)  
   * [Extracting archives and reporting on logical files](guides/triage.md/#reporting)  
   * [Moving files to processing location](guides/triage.md/#moving)  
   * [Submitting files to PRONOM](guides/triage.md/#pronom)
* **[Arrangement](guides/arrangement.md)**  
    * [Arrangement of born-digital archives in principle](guides/arrangement.md/#arrprinciple)  
    * [Factors affecting the arrangement of born-digital records](guides/arrangement.md/#arrfactors)   
    * [Developing a processing plan](guides/arrangement.md/#processingplan)  
    * [The exception: Extensible processing of born-digital records](guides/arrangement.md/#extensible)   
    * [Packaging SIPs for Archivematica](guides/arrangement.md/#packagingsips)  
    * [Processing disk images with Disk Image Processor](guides/arrangement.md/#diskimageprocessor)  
    * [Processing directories of files with Folder Processor](guides/arrangement.md/#folderprocessor)  
    * [Creating single SIPs from directories and files with SIP Creator](guides/arrangement.md/#sipcreator)
    * [Manual normalization for Archivematica](guides/arrangement.md#mannorm)
    * [Processing forward-migrated files](guides/arrangement.md#processfm)
* **[Description](guides/description.md)**  
    * [Principles and practical guidelines for description of born-digital archives](guides/description.md/#descriptionprincipleandpractice)  
    * [Preferred terminology](guides/description.md/#terminology)  
    * [Fonds-, series-, and project-level description](guides/description.md/#higherlevel)  
    * [File ("groupe")-level description](guides/description.md/#groupdesc)   
    * [Item ("pièce")-level description](guides/description.md/#itemdesc)  
* **[Ingest](guides/ingest.md)**  
    * [Archivematica configuration at CCA](guides/ingest.md/#architecture)
    * [Archivematica ingest workflows](guides/ingest.md/#ingestmethods)  
    * [Archivematica processing configurations](guides/ingest.md/#processingconfigs)
    * [Adding descriptive metadata to the AIP](guides/ingest.md/#dcmetadata)  
    * [CCA file format policies](guides/ingest.md/#fileformatpolicies)  
* **[DIP generation and Access](guides/access.md)**  
    * [Definition of CCA-style DIPs](guides/access.md/#dipdefinition)  
    * [Creating CCA-style DIPs](guides/access.md/#dipcreation)  
    * [Current access workflow](guides/access.md/#accessworkflow)  
    * [Access plans](guides/access.md/#accessplans)  
* **[Archivematica administration](guides/administration.md)**  
    * [Fixity checking and repair](guides/administration.md/#fixity)   
    * [Dropping MySQL and ES data in pipelines](guides/administration.md/#flushing)  
    * [Reindexing AIPs in Archival Storage indexes](guides/administration.md/#reindexing)  
    * [Deleting AIPs not indexed on a pipeline](guides/administration.md/#deletingaips) 
    * [Cleaning up after successful Automation Tools ingests](guides/administration.md/#autotoolssuccess)  
    * [Responding to failed Automation Tools ingests](guides/administration.md/#autotoolsfailure) 
    * [Adding and switching AIP Store locations](guides/administration.md/#locations)  
    * [Clearing space when local disk is nearly full](guides/administration.md/#clearingspace)  
    * [Restarting services](guides/administration.md/#restarting)  
    * [Log of changes to default Archivematica FPR](guides/administration.md/#fprchanges)  
    * [Archivematica configuration settings](guides/administration.md/#configsettings)  
* **[CAD, BIM, and 3D modeling software/file formats](guides/cadformats.md)**  
* **[Additional resources](guides/resources.md)**  
   * [Reading material](guides/resources.md/#readings)  
   * [Digital storage media identification and information](guides/resources.md/#media)  
   * [File format identification and information](guides/resources.md/#formats)  
   * [Digital preservation tools](guides/resources.md/#tools)
   * [Scripting resources](guides/resources.md#scripting)
   * [Useful command line scripts](guides/resources.md#useful-command-line-scripts)  
   * [Preservation of computer-aided design](guides/resources.md/#cadpres)  
   * [General resources](guides/resources.md/#general)  

<a name="processingintro"></a>  
## Introduction to processing born-digital archives  

The accession-to-access workflow for making born-digital archives available to researchers consists of several distinct stages that are best thought of as discrete projects unto themselves. As an archivist or digital archives technician, you will be involved in the Stabilization, Pre-processing (triage), Processing (arrangement and description), and Ingest stages. Each stage should typically begin only when the previous stage has been completed in full (some projects may necessitate a different approach). Within a single archive or even a single accession, these stages may be completed by different people.  

The detailed guides in this manual give more precise instructions for how to complete each stage of the workflow. While these should generally apply, it is important to note that because of the early digital material CCA collects and its interest in notoriously difficult media such as computer-aided design, some cases may require a different approach that will be clarified in pre-processing.  

A few general principles to keep in mind when processing born-digital materials:  

* The general principles of archival theory and management (original order, respect du fonds, aggregate description) apply to born-digital materials to the same degree that they apply to analogue materials.  
* Few fonds consist of solely born-digital material. When digital material exists alongside records in other formats, make sure that your decisions and actions in processing the digital material consider and respect the fonds as a whole.
* As with analogue materials, the fundamental goal of processing work is to make materials available for researchers in a timely fashion and provide our users with the appropriate tools to search, identify, select, and obtain materials that meet their research needs.  
* As with analogue materials, we should be flexible in our arrangement practices to best respect original order and meet our users' needs. Often this will mean co-locating records of different formats together in the same series and project files. However, the realities of a particular set of born-digital files and other factors may necessitate other approaches to arrangement on a case-by-case basis.  
* Born-digital materials already contain much of their own description and can be algorithmically processed in ways that analogue materials cannot. Let machines do the tasks that machines are best at and focus your efforts on the tasks at which humans excel (namely, analysis of content and context).  
* Arrangement and description work should typically focus on higher-level folders in a directory structure or on a piece of media as a whole. Manual arrangement and description of individual files is the exception, and should be undertaken only in extraordinary cases and when agreed upon in pre-processing planning.  
* All actions taken during each stage of the digital archives workflow are documented. This documentation is crucial to demonstrate the authenticity of digital files and enable future preservation efforts.  

<a name="overview"></a>
## Born-digital archives workflow at a glance  

1. Archival material (born-digital or hybrid) is accessioned and stabilized:
   * Files sent via network transfers or temporary media (e.g. USB drives, external hard drives) are packaged as tar files and stored in the Dark Archive as a "raw" copy of the accession data.
   * Original physical media are disk imaged and disk images are stored in the Dark Archive as a "raw" copy of the accession data.
2. Pre-processing triage and evaluation:  
   * Digital Archivist or Processing Archivist downloads AIPs containing raw data of all accessions to be processed.  
   * Digital Archivist or Processing Archivist extracts files from archive packages as necessary.  
   * Digital Archivist or Processing Archivist triages and evaluates content using tools like [Brunnhilde](https://github.com/timothyryanwalsh/brunnhilde) and [Disk Image Processor](https://github.com/timothyryanwalsh/cca-diskimageprocessor).
   * A working "reference" copy of files can be moved onto network drives, where the files can be consulted from CAD workstations during processing.
   * Processing Archivist develops proposed processing plan for accession(s).
   * Digital Archivist, Processing Archivist, Conservation, and potentially others have consultation meeting to discuss processing plan.
3. Arrangement and description:
   * Processing Archivist conducts manual file format normalizations and other preservation actions and explores contents of files in Bitcurator and CAD workstations as needed.
   * Processing Archivist uses tools like [Folder Processor, SIP Creator, and/or Disk Image Processor](https://github.com/timothyryanwalsh/cca-tools) to create processed SIPs from raw accession data and begin the file-level processing spreadsheet.
   * Processing Archivist supplements and finishes file-level description in standard processing spreadsheet generated by Folder Processor or Disk Image Processor.
   * Processing Archivist drafts fonds, series, and project-level descriptions in plain text files.
   * Descriptions are reviewed with Digital Archivist and approved for entry into TMS.
   * Processing Archivist copies and pastes descriptions from text files and processing spreadsheet into TMS and creates object packages of newly-processed materials. 
4. Processed SIPs are ingested into Archivematica:  
   * Final processed SIPs are copied to a watched folder on the main Archivematica processing pipeline server.  
   * Processing Archivist QAs ingest (automated fetching of descriptive metadata from TMS, normalization, etc.) and stores DIPs  
   * Digtial Archivist performs final QA check when all data from an accession is ingested  
   * "Raw" copy of accession data is deleted from Dark Archive unless there is sufficient reason to keep it  
5. Ongoing activities:  
   * Monitoring health of AIPs in Archivematica  
   * Restoring from backups as needed  
   * Access
   
<a name="primer"></a>
## Layperson's primer on digital preservation at CCA  

CCA takes a number of steps with all digital files in its Collection that help to ensure their ongoing accessibility for research use over time. All files in CCA digital archives are:

* Virus scanned;  
* Precisely identified through automated comparison against international file format databases such as the UK National Archives PRONOM;  
* Duplicated, when necessary and possible, in vendor-neutral and preservation-friendly file formats that are more likely to remain accessible as current software and hardware becomes obsolete;  
* "Fingerprinted" through the use of cryptographic hashes (also known as checksums) and routinely audited to ensure their ongoing authenticity; and  
* Stored and backed up in a redundant and geographically distributed system according to industry best practices.

All actions that take place on files once they are ingested into CCA's digital repository are documented through an implementation of the PREMIS (PREservation Metadata: Implementation Strategies) metadata standard.  
