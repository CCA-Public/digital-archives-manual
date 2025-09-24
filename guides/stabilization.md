# Accessioning and stabilizing born-digital archives

This guide describes CCA standards for accessioning and stabilizing born-digital archival material in whatever form it might arrive at CCA.  It includes:  

* [General overview](#triageoverview)
* [Stabilization](#stabilization)  
  * [Network transfers](#networktransfer)  
  * [Temporary physical media](#temporarymedia)  
  * [Original physical media](#originalphysicalmedia)  
* [Ingesting "raw" versement data into digital repository](#rawingest)  

<a name="triageoverview"></a>  
## General overview  

In general, digital content arrives at CCA in one of three ways: as a network transfer (e.g. FTP, Dropbox, WeTransfer), on temporary physical transfer media (e.g. USB thumb drive, external hard drive), or on original physical storage media. A single accession (versement) may contain digital files that arrived at CCA via any or all of these methods.    

The following procedures describe how CCA accessions and stabilizes contents from each of these delivery methods, as well as how CCA ingests the total "raw" contents of an accession into its digital repository once all of the preparatory steps have been completed. This guide is meant to complement the accessioning checklist located on the server.  

Please note that prior to receiving born-digital material, the CCA sends out two questionnaires to the donor to gather information on the context of creation and the use of the digital files.

This guide is currently being updated following the implementation of ArchivesSpace in our workflow.

<a name="stabilization"></a>
## Stabilization
<a name="networktransfer"></a>
### Network transfers

Steps:  

* **Staff member who receives the transfer (typically Digital Archivist): Receive**  
  * Create accession record in ArchivesSpace
  * Ensure administration documents related to acquisition and shipment are in the appropriate folders on the server (ex. Deed of gift, pro forma, inventories, correspondence, shipping docs, etc.).
  * Send the transfer to the Digital Archives Technician  
* **Digital archives technician: Stabilize**
  * Download and save file to AP/CD folder on the Shipping Space server
  * Run a virus scan on the entire accession
  * Verify the metadata, specifically the last date modified to make sure that nothing was modified during the transfer
  * Verify the donor provided inventory against the contents of the material, if available
  * Package content as an Archivematica SIP by zipping the files in some kind of archive format (zip, tar, rar, etc.). 
  * Name the SIP as per the [procedures for ingesting "raw" data](#rawingest)
  * Let Digital Archivist know that the SIP is ready for ingest
* **Digital Archivist: Ingest**  
  * Ingest the SIP into Archivematica, following the [procedures for ingesting "raw" data](#rawingest).
  * Send a request to the Digital Archives Technician for the files to be localized to Dark Archive.
  * Delete extraneous copies of files from Digital Shipping Space, BitCurator workstations, etc.
* **Digital Archives Technician: Update location**  
  * Add "Dark archive" as a location to accession record in ArchivesSpace  

<a name="temporarymedia"></a>
### Temporary physical media

Steps:  

* **Staff member who received the temporary physical media (typically Digital Archivist): Receive**  
  * Create accession record in ArchivesSpace 
  * Ensure administration documents related to acquisition and shipment are in the appropriate folders on the server (ex. Deed of gift, pro forma, inventories, correspondence, shipping docs, etc.).
  * Give temporary physical media to Digital Archives Technician for stabilizing
* **Digital Archives Technician: Stabilize**
  * Use the write blocker and disk image the temporary physical media using Guymager on one of the BitCurator workstations
  * Run a virus scan on the entire accession 
  * Verify the metadata, specifically the last date modified to make sure that nothing was modified during stabilization
  * Verify the donor provided inventory against the contents of the material, if available
  * Package content as an Archivematica SIP by zipping the files in some kind of archive format (zip, tar, rar, etc.). 
  * Name the SIP as per the [procedures for ingesting "raw" data](#rawingest)
  * Transfer SIP to the to AP/CD folder on Shipping Space server.
  * Let Digital Archivist know that the SIP is ready for ingest
* **Digital Archivist: Ingest**  
  * Ingest the SIP into Archivematica, following the [procedures for ingesting "raw" data](#rawingest)  
  * Delete extraneous copies of files from Digital Shipping Space, BitCurator workstations, etc.
  * Send request to Digital Archives Technician for the files to be localized to Dark Archive.
  * Reformat (erase) media and return to donor, repurpose, or weed as appropriate
* **Digital Archives Technician: Update location**  
  * Add "Dark archive" as location to accession record in ArchivesSpace

<a name="originalphysicalmedia"></a>
### Original physical media  

*Note: This is a broad category that might include, e.g., floppy disks, optical media (CDs/DVDs), computers, internal hard drives, backup tape formats such as LTO, etc. For assistance in correctly identifying media types, please see the [Computer Media Identification Guide](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/mediaIDGuide.docx) or the UTSA Libraries' [Know Your Media](http://lib.utsa.edu/knowyourmedia/) page.*  

Steps:  

* **Collection management staff member (GesCo): Receive**  
  * Create accession records  
  * Determine if it is possible to separate digital media on arrival
    * IF YES: GesCo separates digital media from physical materials upon arrival (stored in cool vault shelving) and creates separate versement-objets for the container(s) of digital media.
    * IF NO: GesCo makes note in the “Description du contenu“ field of versement objet records that they contain digital media. This material will then be stabilized according to Media Backlog workflows by the Digital Archives Technician as part of their regular work, or at the moment of processing.   
* **Digital Archives Technician: Stabilize** 
  * *Note: These steps may occur after some delay*
  * Consult the Media Backlog Excel spreadsheet and select stabilization project by priority
  * Note current location of the selected accession, physically retrieve it and bring it to the digital lab
  * Update location of accession in ArchivesSpace  
  * Stabilize physical media according to type of media by following the workflow found [here](diskimaging.md)
  * Physically identify each physical media with an AS identifier, with a pencil or pen
  * Track your work in the Versement_Stabilization Excel spreadsheet located on the server
  * Run a virus scan on the entire accession 
  * If archive is not immediately going to be processed, package raw content as an Archivematica SIP by zipping the files in some kind of archive format (zip, tar, rar, etc.), save it on the RAID on one of the BitCurator machines and name the SIP as per the [procedures for ingesting "raw" data](#rawingest)
  * Otherwise, you can package each individual physical media in their own SIP, using the CCA tools. Save it on the RAID on one of the BitCurator machines and name the folder by the identifier of the fonds followed by a short version of the name of the fonds (e.g. AP149_MCHG)
  * Let Digital Archivist know that the SIP is ready for ingest
* **Digital Archivist: Ingest** 
  * Ensure administration documents related to acquisition and shipment are in the appropriate folders on the server (ex. Deed of gift, pro forma, inventories, correspondence, shipping docs, etc.)
  * If accession was packaged as a single Archivematica SIP, ingest into Archivematica following the [procedures for ingesting "raw" data](#rawingest)
  * QA the newly ingested SIP to make sure everything went smoothly and that there are no encountered errors
  * Delete extraneous copies of files from Digital Shipping Space, BitCurator workstations, etc.
  * Send request to Digital Archives Technician for the files to be localized to Dark Archive 
* **Digital Archives Technician: Update location**
  * Add "Dark archive" as location to accession (versement) record  
* **Digital Archivist: Assess**  
  * During or after processing, Digital Archivist assess media for artefactual value and confirm with Associate Director, Collection. There are three possible results to this assessment:  
    * Media have artefactual value and will be kept permanently at CCA in their entirety  
    * Media have artefactual value and a sample will be kept permanently at CCA  
    * Media do not have artefactual value and will be destroyed or returned to the donor  
  * Any media that are kept at CCA are retained solely for their artefactual value, not as storage media or “backups” of digital files in the CCA collection. The description and arrangement of these objects should be discussed with the Digital Archivist and appropriate Archivist/Head/Cataloguer. Any time media are returned or destroyed, the Processing Archivist make a note of this in the "Appraisal-destruction" text entry field in TMS at the fonds-level.   


<a name="rawingest"></a>
## Ingesting "raw" accession data into digital repository  

Once data from all of the network transfer, temporary media, and original media in an accession has been stabilized, the digital component of the accession is ingested into CCA's Archivematica-based digital repository.  The aim of this step is to retain and safely store a copy of the data exactly as it arrived at CCA until a processing archivist processes the accession.  

**Note that all files from network transfers or temporary media must be packaged in some kind of archive format (zip, tar, rar, etc.), or else Archivematica will change original filenames and timestamps, defeating part of the purpose of the "raw" ingest. At CCA, we typically prefer to package in tar files.**

**Test that the files were successfully compressed and can be reopened, as faulty zip files can result in the loss of collection material. Note also that this step may not be necessary if disk images are to be retained as part of the processed material.**  

This SIP is composed of all files, archive packages, and disk images in the Shipping Space that correspond to an accession. It is named according to the convention `<accession number>_raw`, with all punctuation replaced by underscores (e.g., `AR2018_0001_raw`).  

For the ingest of raw unprocessed data, we use the VSP-AMPL-01 processing pipeline. In this pipeline, Archivematica is set by default not to extract packages, examine contents, or normalize any files.

**Procedure:** 

1. Create a SIP named `<accession number>_raw`, containing the files as sent by the donor and/or disk images. If an accession has not yet been created in TMS, temporarily store the SIP in the Digital Shipping Space until the accession number has been assigned and a record created in TMS.  
2. Copy the SIP to the VSP-AMPL-01 pipeline using the `send_to_archivematica.py` script.  
3. (Digital Archivist/Archivematica administrator) Move the SIP to the Automation Tools watched folder for ingest. Follow typical ingest and QA procedures.

Once the accession has been ingested into Archivematica, delete any extraneous copies from the BitCurator machines, Digital Shipping Space, etc. and ask Déplacement to update the location for the appropriate accession records to "Dark archive".  
