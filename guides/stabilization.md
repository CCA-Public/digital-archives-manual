# Accessioning and stabilizing born-digital archives

This guide describes CCA standards for accessioning and stabilizing born-digital archival material in whatever form it might arrive at CCA.  It includes:  

* [General overview](#triageoverview)  
* [Network transfers](#networktransfer)  
* [Temporary physical media](#temporarymedia)  
* [Original physical media](#originalphysicalmedia)  
  * [Identifying and separating physical media in Collection](#idandremoval)  
  * [Disk imaging original physical media](#diskimaging)  
    * [Disk imaging with Guymager (Bitcurator)](#guymager)  
    * [Disk imaging with FTK Imager](#ftkimager)  
* [Ingesting "raw" versement data into digital repository](#rawingest)  

<a name="triageoverview"></a>  
## General overview  

In general, digital content arrives at CCA in one of three ways: as a network transfer (e.g. FTP, Dropbox, WeTransfer), on temporary physical transfer media (e.g. USB thumb drive, external hard drive), or on original physical storage media. A single accession (versement) may contain digital files that arrived at CCA via any or all of these methods.    

The following procedures describe how CCA accessions and stabilizes contents from each of these delivery methods, as well as how CCA ingests the total "raw" contents of an accession into its digital repository once all of the preparatory steps have been completed.  

**Note: In order to keep track of all media and files, CCA has created a [versement stabilization spreadsheet](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/forms/versement_stabilization.xlsx). This spreadsheet must be completed for every versement containing digital records in any form that arrives at CCA.** This file should be saved with the actual versement number in place of the word "versement", replacing any full stops or colons with underscores (e.g. "AR2014_0068_stabilization.xlsx"), and saved in the appropriate project folder in "Acquisitions et traitement". Please consult with the Digital Archivist on the proper use of this spreadsheet prior to your first digital processing project.  

<a name="networktransfer"></a>
## Network transfers

Steps:  

* **Staff member who receives the transfer**  
  * *Note: Who receives files and how should also be streamlined and better documented in future*
  * Notify Registrar and Digital Archivist  
  * Move files into a new folder in Digital Shipping Space (or, if staff member does not have access to Digital Shipping Space, into "Dépot numérique" network folder)  
* **Registrar: Create accession records**  
  * For Archives, create only a versement record (no versement objet or ARCH records). Include a brief identifying note for the accession in "Description du contenu" (e.g. the name of the Dropbox folder)  
  * *For Photo/P&D, create groupe or pièce records as usual*  
* **Digital Archivist: Ingest**  
  * Add brief descriptive note about content to versement "Description du contenu"  
  * If files were not already in an archive format, package them as a .tar file  
  * Package content according to BagIt specification and ingest into Archivematica according to procedures for ingesting "raw" data  
  * Inform Registrar when ingest is completed  
  * Delete copies of files from Digital Shipping Space/Dépot numérique  
* **Registrar**  
  * Add "Dark archive" as location to accession (e.g. versement) record  

<a name="temporarymedia"></a>
## Temporary physical media

Steps:  

* **Registrar: Create accession records**  
  * For Archives, create only a versement record (no versement objet or ARCH records). Include a brief note in "Description du contenu" indicating how the files arrived (e.g. "Files arrived at CCA on a 64GB USB thumb drive")  
  * *For Photo/P&D, create groupe or pièce records as usual*  
* **Digital Archivist: Ingest**  
  * Add brief descriptive note regarding content to versement "Description du contenu"  
  * If files were not already in an archive format, package them as a .tar file  
  * Package content according to BagIt specification and ingest into Archivematica according to procedures for ingesting "raw" data  
  * Inform Registrar when ingest is completed  
  * Delete extra copies of files on network shares
  * Reformat (erase) media and return to donor or repurpose as appropriate
* **Registrar**  
  * Add "Dark archive" as location to accession (versement) record  

<a name="originalphysicalmedia"></a>
## Original physical media  

*Note: This is a broad category that might include, e.g., floppy disks, optical media (CDs/DVDs), computers, internal hard drives, backup tape formats such as LTO, etc. For assistance in correctly identifying media types, please see the [Computer Media Identification Guide](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/guides/mediaIDGuide.docx) or the UTSA Libraries' [Know Your Media](http://lib.utsa.edu/knowyourmedia/) page.*  

Steps:  

* **Registrar**  
  * Create accession records as described below  
  * Determine if it is possible to separate digital media on arrival
   * IF YES: Registrar separates digital media from physical materials upon arrival (stored in cool vault shelving) and creates “DM” versement objet records for containers of digital media (see [Identifying and separating physical media in Collection](#idandremoval)). All staff should use Digital Media Removal Sheets when removing digital media from original boxes or folders. The media is localized at the level of these DM containers.  
   * IF NO: Registrar makes note in the “Description du contenu“ field of versement objet records that they contain digital media that should be separated. This material will then be separated by a technician, archivist, or cataloguer at a later date.  
* **Digital Archivist** 
  * *Note: These steps may occur after some delay*
  * Oversee disk imaging of media and transfer of files to Digital Shipping Space  
  * Ensure that all digital material related to an accession is located in a folder named after the accession in the Digital Shipping Space  
  * Package the content according to the BagIt specification and ingests this material into Archivematica according to procedures for ingesting “raw” data  
  * Inform Registrar when ingest is completed  
  * Delete copy of files from Digital Shipping Space  
* **Registrar**
  * Add "Dark archive" as location to accession (versement) record  
* **Digital Archivist, Archivist/Chef/Curator, Associate Director**  
  * During or after processing, Digital Archivist and either the Archivist or appropriate Curator/Chef assess media for artefactual value and confirm with Associate Director, Collection. There are three possible results to this assessment:  
    * Media have artefactual value and will be kept permanently at CCA in their entirety  
    * Media have artefactual value and a sample will be kept permanently at CCA  
    * Media do not have artefactual value and will be destroyed or returned to the donor  
  * Any media that are kept at CCA are retained solely for their artefactual value, not as storage media or “backups” of digital files in the CCA collection. The description and arrangement of these objects should be discussed with the Digital Archivist and appropriate Archivist/Head/Cataloguer  
* **Registrar**
  * Any time media are returned or destroyed, the Registrar will make a note of the action taken in the appropriate accession (e.g. versement) record. Please consult Digital Archivist on how to responsibly destroy digital media  


<a name="idandremoval"></a>
### Identifying and separating physical media in Collection

Steps:  

1. Print (on blue acid-free paper) and complete out two copies of the [CCA Digital Media Removal Sheet](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/forms/Digital.Media.Removal.Sheet.pdf).  
2. Leave one of the copies of the Removal Sheet in the box or folder where you found the media, as close to where the media was found as possible.  
3. Put the media and the second copy of the completed Digital Media Removal Sheet in a new envelope or box and store this container in cool vault shelving.  
4. Create a TMS record for the new container:
    * **Object number:** "(accession number).DM##", e.g. "AR2013.0050.DM01"  
    * **Classification:** "médias numériques retirés"  
    * **Status flag:** "record for management need"  
    * **Nom de l'objet:** "digital media"  
    * **Title:** "Separated digital media"  
    * **Description du contenu:** Enter a brief description of the material and (optionally) the title of the folder from which it was taken.  
5. Add the following associations: 
    * **a classifier:** The fonds or collection to which the media belongs  
    * **Provient de:**The accession to which the media belongs  
    * **Est inclus dans (if applicable):** The groupe to which the separated media belongs  
6. Label the new container:
    * Object number  
    * Fonds or Collection number (when appropriate)  
    * Name of fonds or collection (short name is okay, e.g. you can write "Siza" instead of "Alvaro Siza fonds")  
7. If the media in the container (*note: specific pieces of media, not the folder or "groupe" they were found within*) already have ARCH, DR, or PH numbers, link the ARCH/DR/PH records to the DM container record as children with the "Est composé de" association.  
8. Give information about the new container to the Registrar as per usual localisation procedures, and request that the material is localised to the Digital Media storage in the Cool Vault.  

<a name="diskimaging"></a>
### Disk imaging original physical media  

At CCA, we capture the contents of original physical media as raw disk images. A disk image is a computer file that is an exact replica of the contents of a disk or other digital storage volume as that information exists on a particular physical storage medium. Because disk images can be stored redundantly, backed up, and audited in ways that physical carriers like DVDs or external hard drives cannot, they are a much better suited for preservation of digital information over time, while retaining all characteristics of the original physical media as a storage volume.  

Except when circumstances require different solutions, CCA prefers raw disk image formats (e.g. "dd" or "raw").  

**Note: In order to ensure that the source media is unchanged by the process of data capture and transfer, hard drives and removable media drives should always be connected to the capture workstation through a hardware write-blocker.**  

We will typically use one of two tools for creating disk images of media: [Guymager](#guymager) or [FTK Imager](#ftkimager). Regardless of which tool you use, always complete the following step first:  

Give each piece of media an ARCH number identifier if it doesn't have one already, and create a corresponding "Record for Management Need" object record in TMS. The identifier should be written on the media or its case with a felt tip pen or (very lightly) in pencil, or affixed to the case using a label maker if available.

<a name="guymager"></a>
#### Disk imaging with Guymager (Bitcurator)  

Guymager is an open source disk imaging utility found in the Bitcurator environment, and one of the preferred tools for disk imaging at CCA. At CCA we use Guymager to create disk images in the raw (dd) format.  

Before starting to create disk images from an accession, create a folder in the /mnt/1TB_RAID directory in which you will save your work. Name this folder something memorable and meaningful, such as an accession number or other identifier.  

Steps for imaging physical media with Guymager:  

* Prior to creating a disk image, virus scan the media using ClamTK:  
  * Open ClamTK (from the 'Additional Tools' folder on the Bitcurator desktop).  
  * Ensure that settings are correct: Double-click on 'Settings', and ensure that everything except 'Scan for PUAs' is selected.    
  * Double-click on 'Scan a directory' from the 'Analysis' tabe and then choose directory to scan.  
  * If there are no viruses, proceed with the next step. If ClamTK finds viruses, stop, note the virus(es) encountered in the versement stabilization spreadsheet, set the media aside, and consult the Digital Archivist.  
* Open Guymager (from the 'Imaging Tools' folder on the Bitcurator desktop).  
* Rick-click on the drive you wish to image and select 'Acquire image'. If the drive/device you wish to image does not appear, refresh the screen by clicking "Rescan" in the upper left hand corner of the Guymager interface.  

![Bitcurator1](http://wiki.bitcurator.net/images/4/45/Acquire_image_guymager.jpg)  

* Choose the 'Linux dd raw image' (file extension .dd or .xxx) file format.  
* Make sure split size is unchecked.  
* Enter the following metadata/settings:  
  * **Image directory:** Select the directory you created in /mnt/1TB_RAID.
  * **Image filename:** Enter the disk's identifier with no spaces. Replace any full stops ('.') or colons (':') with underscores ('_').  
  * **Info filename:** This should be automatically created based on your image filename. Do not edit this field.  
  * **Hash calculation/verification:**  
    * Check "Calculate MD5", "Calculate SHA-1", and "Verify image after acquisition" 
    * Keep other options unchecked   
  
![Bitcurator2](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/media/photos/guymager_settings.png)  

* Once settings have been confirmed, press 'Start' to start the disk imaging process.
* Guymager will track its progress and give you color-coded indications when the process has been completed successfully or has failed. If it fails, make a note of this in the versement stabilization spreadsheet and set the disk aside for review by the Digital Archivist.  
* If the image is successfully created, go to your project folder on the desktop and do a quick visual check that all looks good. You should see at two files: the disk image itself and a '.info' metadata file.  
* If all looks good, repeat this process with the next disk until all media has been imaged.  Once all media has been imaged, copy the entire project folder from the Bitcurator desktop into the "Dépôts" folder and alert the Digital Archivist.  

<a name="ftkimager"></a>
#### Disk imaging with FTK Imager  

AccessData FTK Imager is a free but proprietary Windows-based disk imaging tool that forms part of the (very much not free) larger Forensics Toolkit software suite. At CCA we use FTK Imager to create disk images for media which Guymager is unable to image.  

Before starting to create disk images from an accession, create a folder on the Catalogers network share in which you will save your work.

Steps for imaging physical media with FTK Imager:  

* Prior to creating a disk image, virus scan the media using ESET:  
  * Open ESET Endpoint Antivirus.  
  * From the 'Analyse de l'ordinator' menu, click 'Analyse personnalisée' and then select the media to begin virus scanning.  
  * If there are no viruses, proceed with the next step. If ESET finds viruses, stop, note the virus(es) encountered in the versement stabilization spreadsheet, set the media aside, and consult the Digital Archivist.  
* Open FTK Imager.  

![FTK1](https://blogs.sans.org/computer-forensics/files/2009/06/ftkimager.png)  

* From the File menu, select Create a Disk Image and choose the appropriate source and drive.  
  * **Source:** For full hard drives, the appropriate source will be 'Physical drive'. For most other media types (including CDs, DVDs, and floppy disks), the source will be 'Logical drive'.  
  * **Drive:** Select the appropriate drive from the list.  
  
![FTK2](https://blogs.sans.org/computer-forensics/files/2009/06/select-source.png)  

![FTK3](https://blogs.sans.org/computer-forensics/files/2009/06/select-device.png)  

* Select 'Add' to add the image destination. Check 'Verify images after they are created', but leave 'Create directory listings...' unchecked.  

![FTK4](https://blogs.sans.org/computer-forensics/files/2009/06/device-selected.png)  

* Select Image type 'raw (dd)'.  
* FTK Imager will prompt you to add metadata for your disk image. Enter the following metadata:  
  * **Case number:** Versement  
  * **Evidence number:** Identifier of the media being imaged  
  * **Unique description:** Enter a brief description of the media and/or its annotations (e.g., '3.5" floppy disk labelled "FOA Photos 2002"')  
  * **Examiner:** Your name  
  * **Notes:** Leave this blank  

![FTK5](https://blogs.sans.org/computer-forensics/files/2009/06/select-image-type.png)
![FTK6](https://blogs.sans.org/computer-forensics/files/2009/06/evidence-info.png)

 * FTK Imager will now ask you for information about where to save the resulting disk image and metadata files. Enter the following and then select 'Finish':
  * **Image destination folder:** Enter the network location of your current work folder in the Catalogers drive.
  * **Image filename:** Enter the disk's identifier with no spaces. Replace any full stops ('.') or colons (':') with underscores ('_').  

* Double-check to make sure that the Image Destination and settings appear correct and then select 'Start' to begin the disk imaging process.  

![FTK7](https://blogs.sans.org/computer-forensics/files/2009/06/ready-to-create.png)  

* A progress window will not appear and keep you informed of how the disk imaging is progressing. If disk imaging fails or seems to get hung up on a large number of bad sectors, make note of this in the versement stabilization spreadsheet and set the disk aside for review by the Digital Archivist.  
* If the image is successfully created, go to your project folder in the Catalogers drive and do a quick visual check that all looks good. You should see at least two files: the disk image(s) themselves (potentially split into several files with the same file name but extensions of .001, .002, etc.) and a '.txt' metadata file.  
* If all looks good, repeat this process with the next disk until all media has been imaged.  Once all media has been imaged, copy the entire project folder from the Catalogers drive into the "Dépôts" folder and alert the Digital Archivist.    

<a name="rawingest"></a>
## Ingesting "raw" accession data into digital repository  

Once data from all of the network transfer, temporary media, and original media in an accession has been stabilized, the digital component of the accession is ingested into CCA's Archivematica-based digital repository.  The aim of this step is to retain and safely store a copy of the data exactly as it arrived at CCA in the digital repository.  **Note that all files from network transfers or temporary media must be packaged in some time of archive format (zip, tar, rar, etc.), or else Archivematica will change original filenames and timestamps, defeating part of the purpose of the "raw" ingest. At CCA, we typically prefer to package in tar files. Note also that this step may not be necessary if disk images are to be retained as part of the processed material.**  

This SIP (Submission Information Package, in OAIS parlance) is composed of all files, archive packages, and disk images in the Shipping Space that correspond to an accession. It is named according to the convention "(versement number)_raw".   

For the ingest of raw unprocessed data, we use the csp-arch-02 processing pipeline. In this pipeline, Archivematica is set not to extract packages, examine contents, or normalize any files. An AIP is created and stored, but no DIP is created. These settings must be manually selected for now, but eventually these will be the default settings in a "raw ingest" watched directory that will process material through Archivematica using Automation Tools scripts.    

Once an accession has been ingested into Archivematica, the Digital Archivist deletes the temporary copies from the Shipping Space and notifies the Registrar. The Registrar then updates the location for the appropriate accession records to "Dark archive".  
