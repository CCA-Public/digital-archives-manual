# Accessioning and stabilizing born-digital archives

This guide describes CCA standards for accessioning and stabilizing born-digital archival material in whatever form it might arrive at CCA.  It includes:  

* [General overview](#triageoverview)  
* [Network transfers](#networktransfer)  
* [Temporary physical media](#temporarymedia)  
* [Original physical media](#originalphysicalmedia)  
  * [Identifying and separating physical media in Collection](#idandremoval)  
  * [Disk imaging original physical media](#diskimaging)  
    * [Disk imaging with Guymager](#guymager)  
    * [Disk imaging with FTK Imager](#ftkimager)  
* [Ingesting "raw" versement data into digital repository](#rawingest)  

<a="triageoverview"></a>  
## General overview  

In general, digital content arrives at CCA in one of three ways: as a network transfer (e.g. FTP, Dropbox, WeTransfer), on temporary physical transfer media (e.g. USB thumb drive, external hard drive), or on original physical storage media. A single accession (versement) may contain digital files that arrived at CCA via any or all of these methods.    

The following procedures describe how CCA accessions and stabilizes contents from each of these delivery methods, as well as how CCA ingests the total "raw" contents of an accession into its digital repository once all of the preparatory steps have been completed.  

**Note: In order to keep track of all media and files, CCA has created a [versement stabilization spreadsheet](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/forms/versement_stabilization.xlsx). This spreadsheet must be completed for every versement containing digital records in any form that arrives at CCA.** This file should be saved with the actual versement number in place of the word "versement", replacing any full stops or colons with underscores (e.g. "AR2014_0068_stabilization.xlsx"), and saved in the appropriate project folder in "Acquisitions et traitement". Please consult with the Digital Archivist on the proper use of this spreadsheet prior to your first digital processing project.  

<a name="networktransfer"></a>
## Network transfers

Steps:  

UPDATE WHEN APPROVED  

<a name="temporarymedia"></a>
## Temporary physical media

Steps:  

UPDATE WHEN APPROVED   

<a name="originalphysicalmedia"></a>
## Original physical media  

Note: This is a broad category that might include, e.g., floppy disks, optical media (CDs/DVDs), computers, internal hard drives, backup tape formats such as LTO, etc. For assistance in correctly identifying media types, please see the [Computer Media Identification Guide](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/guides/mediaIDGuide.docx).  

Steps:  

UPDATE WHEN APPROVED   

<a name="idandremoval"></a>
### Identifying and separating physical media in Collection

Steps:  

1. Print (on brightly colored paper, if possible) and complete out two copies of the [CCA Digital Media Removal Sheet](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/forms/Digital.Media.Removal.Sheet.pdf).  
2. Leave one of the copies of the Removal Sheet in the box or folder where you found the media, as close to where the media was found as possible.  
3. Put the media and the second copy of the completed Digital Media Removal Sheet in a new envelope or box and store this container in cool vault shelving.  
4. Create a TMS record for the new container:
    * Object number: "(accession number).DM##", e.g. "AR2013.0050.DM01"  
    * Link the container record as an child of the versement, using the "Est composé de" association.  
5. Label the new container:
    * Object number  
    * Fonds or Collection number (when appropriate)  
    * Name of fonds or collection (short name is okay, e.g. you can write "Siza" instead of "Alvaro Siza fonds")  
6. If the media in the container (note: the specific media, not the folder or "groupe" they were found within) already have ARCH, DR, or PH numbers, link the ARCH/DR/PH records to the DM container record as children with the "Est composé de" association.  
7. Give information about the new container to the Registrar, as per usual localisation procedures.  

<a name="diskimaging"></a>
### Disk imaging original physical media  

At CCA, we capture the contents of original physical media as forensic disk images. A disk image is a computer file that is an exact replica of the contents of a disk or other digital storage volume as that information exists on a particular physical storage medium. Because disk images can be stored redundantly, backed up, and audited in ways that physical carriers like DVDs or external hard drives cannot, they are a much better suited for preservation of digital information over time, while retaining all characteristics of the original physical media as a storage volume.  

Except when circumstances require different solutions, CCA prefers the [Expert Witness Compression Format (also known as EWF or E01)](https://github.com/libyal/libewf/blob/master/documentation/Expert%20Witness%20Compression%20Format%20%28EWF%29.asciidoc) disk image format.  

**Note: In order to ensure that the source media is unchanged by the process of data capture and transfer, hard drives and removable media drives should always be connected to the capture workstation through a hardware write-blocker.**  

We will typically use one of two tools for creating disk images of media: [Guymager](#guymager) or [FTK Imager](#ftkimager). Regardless of which tool you use, always complete the following steps first:  

1. Give each piece of media an ARCH number identifier if it doesn't have one already, and create a corresponding "Record for Management Need" object record in TMS. The identifier should be written on the media or its case with a felt tip pen or (very lightly) in pencil.  
2. Take an identification photo of the media and save it to a folder named "versement_mediaPhotos", replacing any full stops or colons with underscores - e.g. "AR2015_0050_mediaPhotos". Save this folder to your project folder in H:\Acquisitions et traitement.  

<a name="guymager"></a>
#### Disk imaging with Guymager  

Guymager is an open source disk imaging utility found in the Bitcurator environment, and the preferred tool for disk imaging at CCA. At CCA we use Guymager to create disk images in the Expert Witness (E01) format.  

Before starting to create disk images from an accession, create a folder on the Bitcurator desktop in which you will save your work.  

Steps for imaging physical media with Guymager:  

* Prior to creating a disk image, virus scan the media using ClamTK:  
  * Open ClamTK (from the 'Additional Tools' folder on the Bitcurator desktop).  
  * From the 'Scan' menu, click 'Recursive Scan' and then select the media to begin virus scanning.  
  * If there are no viruses, proceed with the next step. If ClamTK finds viruses, stop, note the virus(es) encountered in the versement stabilization spreadsheet, set the media aside, and consult the Digital Archivist.  
* Open Guymager (from the 'Imaging Tools' folder on the Bitcurator desktop).  
* Rick-click on the drive you wish to image and select 'Acquire image'. If the drive/device you wish to image does not appear, refresh the screen by clicking "Rescan" in the upper left hand corner of the Guymager interface.  

![Bitcurator1](http://wiki.bitcurator.net/images/4/45/Acquire_image_guymager.jpg)  

* Choose the 'Expert Witness Format' (E01) file format. Split size can be kept at 2047 MB (the default). Enter the following metadata/settings:
  * **Case number:** Versement
  * **Evidence number:** Identifier of the media being imaged
  * **Examiner:** Your name
  * **Description:** Transcribe any annotations on the media here
  * **Notes:** Guymager will automatically enter information about the device here. Do not edit this field.    
  * **Image directory:** Give the path to the folder you created for your project on the Bitcurator desktop. The path should be 'home/bcadmin/Desktop/(insert name of folder you created here)/'.  
  * **Image filename:** Enter the disk's identifier with no spaces. Replace any full stops ('.') or colons (':') with underscores ('_').  
  * **Info filename:** This should be automatically created based on your image filename. Do not edit this field.  
  * **Hash calculation/verification:**  
    * Check "Calculate MD5"  
    * Leave "Calculate SHA-256" unchecked  
    * Leave "Re-read source after acquisition for verification" unchecked
    * Check "Verify image after acquisition"  
  
![Bitcurator2](http://wiki.bitcurator.net/images/b/b7/Acquire_image_window.jpg)  

* Once all metadata has been entered and the settings have been checked, click 'OK' to start the disk imaging process.
* Guymager will track its progress and give you color-coded indications when the process has been completed successfully or has failed. If it fails, make a note of this in the versement stabilization spreadsheet and set the disk aside for review by the Digital Archivist.  
* If the image is successfully created, go to your project folder on the desktop and do a quick visual check that all looks good. You should see at least two files: the disk image(s) themselves (potentially split into several files with the same file name but extensions of .E01, .E02, etc.) and a '.info' metadata file.  
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

* Select Image type 'E01'.  
* FTK Imager will prompt you to add metadata for your disk image. Enter the following metadata:  
  * **Case number:** Versement  
  * **Evidence number:** Identifier of the media being imaged  
  * **Unique description:** Transcribe any annotations on the media here  
  * **Examiner:** Your name  
  * **Notes:** Leave this blank  

![FTK5](https://blogs.sans.org/computer-forensics/files/2009/06/evidence-info.png)

 * FTK Imager will now ask you for information about where to save the resulting disk image and metadata files. Enter the following and then select 'Finish':
  * **Image destination folder:** Enter the network location of your current work folder in the Catalogers drive.
  * **Image filename:** Enter the disk's identifier with no spaces. Replace any full stops ('.') or colons (':') with underscores ('_').  

* Double-check to make sure that the Image Destination and settings appear correct and then select 'Start' to begin the disk imaging process.  

![FTK6](https://blogs.sans.org/computer-forensics/files/2009/06/ready-to-create.png)  

* A progress window will not appear and keep you informed of how the disk imaging is progressing. If disk imaging fails or seems to get hung up on a large number of bad sectors, make note of this in the versement stabilization spreadsheet and set the disk aside for review by the Digital Archivist.  
* If the image is successfully created, go to your project folder in the Catalogers drive and do a quick visual check that all looks good. You should see at least two files: the disk image(s) themselves (potentially split into several files with the same file name but extensions of .E01, .E02, etc.) and a '.txt' metadata file.  
* If all looks good, repeat this process with the next disk until all media has been imaged.  Once all media has been imaged, copy the entire project folder from the Catalogers drive into the "Dépôts" folder and alert the Digital Archivist.    

<a name="rawingest"></a>
## Ingesting "raw" accession data into digital repository  

Once data from all of the network transfer, temporary media, and original media in an accession has been stabilized, the digital component of the accession is ingested into CCA's Archivematica-based digital repository.  The aim of this step is to retain and safely store a copy of the data exactly as it arrived at CCA in the digital repository.  

This SIP (Submission Information Package, in OAIS parlance) is composed of all files, archive packages, and disk images in the Shipping Space that correspond to an accession. It is named according to the convention "(versement number)_raw". --ADD NOTE ABOUT SUBMISSION DOCUMENTATION--  

For the ingest of raw unprocessed data, Archivematica is set not to extract packages, examine contents, or normalize any files. An AIP is created and stored, but no DIP is created. These settings must be manually selected for now, but eventually these will be fixed settings in a separate Archivematica pipeline used exclusively for ingest of "raw" data.  

Once an accession has been ingested into Archivematica, the Digital Archivist deletes the temporary copies from the Shipping Space and notifies the Registrar. The Registrar then updates the location for the appropriate accession records to "Digital Repository".  
