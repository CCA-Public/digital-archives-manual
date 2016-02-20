# CCA Digital Archives Processing Manual

---THIS IS A DRAFT/WORK IN PROGRESS---

This is the CCA's processing manual for born-digital archives. It functions as a component of the larger CCA Processing Manual. The Digital Archives Processing Manual covers each step of the processing process, including capture of data, arrangement, description, ingest into our Archivematica-based digital repository, and access. It includes general policies and procedures as well as specific information about tools used in this process.

## Table of Contents

### Overview

* **[Detailed guides](#details)**
* **[Introduction to processing born-digital archives](#processingintro)**
* **[Born-digital archives workflow at a glance](#overview)** 
* **[Layperson's primer on digital preservation at CCA](#primer)**

<a name="details"></a>  
### Detailed guides  

* **[Pre-accession](guides/preaccession.md)**  
    * [Data transfer guide for donors](guides/preaccession.md/#donorguide)
* **[Accession and stabilization](guides/stabilization.md)**
    * [Network transfers](guides/stabilization.md/#networktransfer)
    * [Temporary physical media](guides/stabilization.md/#temporarymedia)
    * [Original physical media](guides/stabilization.md/#originalphysicalmedia)
      * [Identifying and separating physical storage media](guides/stabilization.md/#idandremoval)
      * [Disk imaging original physical media](guides/stabilization.md/#diskimaging)  
   * [Ingesting "raw" versement data into digital repository](guides/stabilization.md/#rawingest)  
* **[Pre-processing: Triage and evaluation](guides/triage.md)**
      * [Extracting files from packages and disk images](guides/triage.md/#diskimageextract)
         * [Extracting files from disk images with Bitcurator](guides/triage.md/#bitcuratorfiles)
         * [Extracting files from disk images with FTK Imager](guides/triage.md/#ftkimagerfiles)  
         * [Extracting files from images of Hierarchical File System (HFS) disks](guides/triage.md/#hfsfiles)        
      * [Reporting](guides/triage.md/#reporting)  
      * [Moving files to processing location](guides/triage.md/#moving)  
* **[Arrangement](guides/arrangement.md)**
      * [Arrangement of born-digital archives in principle](guides/arrangement.md/#arrprinciple)
      * [Factors affecting the arrangement of born-digital records](guides/arrangement.md/#arrfactors)
         * [How the records arrive at CCA](guides/arrangement.md/#howarrive)
         * [Existing organization](guides/arrangement.md/#existingorganization)
         * [Context of creation and active use](guides/arrangement.md/#context)
         * [Nature of archival collection to which they belong](guides/arrangement.md/#nature)
         * [Access requirements](guides/arrangement.md/#accessrequirements)
         * [Institutional priorities](guides/arrangement.md/#institutionalpriorities)
      * [Developing a processing plan](guides/arrangement.md/#processingplan)
      * [The exception: Extensible processing of born-digital records](guides/arrangement.md/#extensible)  
* **[Description](guides/description.md)**
      * [Principles and practical guidelines for description of born-digital archives](guides/description.md/#descriptionprincipleandpractice)
      * [Fonds-, series-, and project-level description](guides/description.md/#higherlevel)
      * [File ("groupe")-level description](guides/description.md/#groupdesc)
         * [Required elements of description](guides/description.md/#grouprequiredelements)  
         * [Optional elements of description](guides/description.md/#groupoptionalelements)  
      * [Item ("pièce")-level description](guides/description.md/#itemdesc)  
* **[Ingest](guides/ingest.md)**
     * [Archivematica processing configuration for ingest of "raw" data](guides/ingest.md/#rawingestconfig)  
     * [Archivematica processing configuration for ingest of "processed" data](guides/ingest.md/#processedingestconfig)  
     * [Adding descriptive metadata to the AIP](guides/ingest.md/#dcmetadata)  
     * [CCA file format policies](guides/ingest.md/#fileformatpolicies)  
     * [Future developments with Archivematica](guides/ingest.md/#amaticadevelopments)
* **[Ongoing activities](guides/ongoing.md)**  
   * [Fixity checks](guides/ongoing.md/#fixity)  
   * [Access](guides/ongoing.md/#access)  
* **[Additional resources](guides/resources.md)**  
   * [Required reading: aka Digital Preservation 101](guides/resources.md/#digipresbasics)  
   * [Digital storage media identification and information](guides/resources.md/#media)  
   * [File format identification and information](guides/resources.md/#formats)  
   * [Digital preservation tools](guides/resources.md/#tools)  
   * [Preservation of computer-aided design](guides/resources.md/#cadpres)  
   * [General resources](guides/resources.md/#general)  

<a name="processingintro"></a>  
## Introduction to processing born-digital archives  

The accession-to-access workflow for making born-digital archives available to researchers consists of several distinct stages that are best thought of as discrete projects unto themselves. As an archivist or cataloguer, you will be involved in the Stabilization, Pre-processing (triage), Processing (arrangement and description), and (eventually) Ingest stages. Each stage should begin only when the previous stage has been completed in full. Within a single archive or even a single accession, these stages may be completed by different people.  

The detailed guides in this manual give more precise instructions for how to complete each stage of the workflow. While these should generally apply, it is important to note that because of the early digital material CCA collects and its interest in notoriously difficult media such as computer-aided design, some cases may require a different approach that will be clarified in pre-processing.  

A few general principles apply in stabilizing and processing born-digital materials:  

* The general principles of archival theory and management (original order, respect du fonds, aggregate description) apply to born-digital materials to the same degree that they apply to analogue materials.  
* As with analogue materials, the fundamental goal of processing work is to make materials available for researchers in a timely fashion and provide our users with the appropriate tools to search, identify, select, and obtain materials that meet their research needs.  
* As with analogue materials, we should be flexible in our arrangement practices to best meet our users' needs. Often this will mean co-locating records of different formats together in the same series and project files. However, the realities of a particular set of born-digital files and other factors may necessitate other approaches to arrangement on a case-by-case basis.  
* Born-digital materials already contain much of their own description and can be algorithmically processed in ways that analogue materials cannot. Let machines do the tasks that machines are best at and focus your efforts on the tasks that humans excel at (namely, analysis of content and context).  
* Arrangement and description work should typically focus on higher-level folders in a directory structure or on a piece of media as a whole. Manual arrangement and description of individual files is the exception, and should be undertaken only in extraordinary cases and when agreed upon in pre-processing planning.  
* All actions taken during each stage of the digital archives workflow are documented. This documentation is crucial to demonstrate the authenticity of digital files and enable future preservation efforts.  

<a name="overview"></a>
## Born-digital archives workflow at a glance  

1. Archival material (born-digital or hybrid) is accessioned and stabilized:
   * Files sent via network transfers or temporary media (e.g. USB drives, external hard drives) are packaged and stored temporarily in the Digital Shipping Space (a secure, limited-access network location).
   * Original physical media are disk imaged; disk images are stored in Digital Shipping Space.
2. "Raw" data is ingested from the Digital Shipping Space into digital repository, to retain and safely store a copy of data exactly as it arrived at CCA:
   * Digital Archivist creates an SIP according to the BagIt specification, naming the package according to the convention "(versement number)_raw", and oversees ingest into Archivematica.
   * The "raw ingest" Archivematica pipeline is set not to extract packages, examine contents, or normalize files; creates and stores an AIP only.  
3. Pre-processing triage and evaluation:  
   * Digital Archivist downloads AIPs containing raw data of all accessions to be processed.  
   * Digital Archivist or processor extracts files from 7zips and disk images as necessary.  
   * Digital Archivist triages and evaluates content, creating reports for use by processor.  
   * Digital Archivist moves working copies of files to network location that archivists and cataloguers can access.  
4. Arrangement and description:
   * Processor describes in standard processing spreadsheet, adding descriptive metadata (title, scope and content, etc.) to pre-generated technical metadata (dates, file types, etc.).
   * Digital archivist creates Bags for ingest corresponding to described groups.
   * Processing spreadsheet is imported into AtoM to create finding aid through which files in DIP will be accessible.
   * Descriptive metadata is copied and pasted from spreadsheet into TMS.
5. Processed SIPs are ingested into Archivematica:  
   * This is performed by the Digital Archivist for now, but may become one of the processor's responsibilities when developments in Archivematica and CCA's general IT infrastructure allow.  
   * The "processed ingest" Archivematica pipeline is set to extract packages, examine contents, and noramlize files; creates and stores AIPs and DIPs.  
   * Descriptive metadata is manually entered into Archivematica to retain the link to the TMS record.  
6. Ongoing activities:  
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