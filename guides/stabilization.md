# Accessioning and stabilizing born-digital archives

This guide describes CCA standards for accessioning and stabilizing born-digital archival material in whatever form it might arrive at CCA.  It includes:  

* [General overview](#triageoverview)  
* [Network transfers](#networktransfer)  
* [Temporary physical media](#temporarymedia)  
* [Original physical media](#originalphysicalmedia)  
  * [Identifying and separating physical media in Collection](#idandremoval)  
* [Ingesting "raw" versement data into digital repository](#rawingest)  

<a name="triageoverview"></a>  
## General overview  

In general, digital content arrives at CCA in one of three ways: as a network transfer (e.g. FTP, Dropbox, WeTransfer), on temporary physical transfer media (e.g. USB thumb drive, external hard drive), or on original physical storage media. A single accession (versement) may contain digital files that arrived at CCA via any or all of these methods.    

The following procedures describe how CCA accessions and stabilizes contents from each of these delivery methods, as well as how CCA ingests the total "raw" contents of an accession into its digital repository once all of the preparatory steps have been completed.  

**Note: In order to keep track of all media and files, CCA has created a [versement stabilization spreadsheet](https://github.com/CCA-Public/digital-archives-manual/blob/master/forms/versement_stabilization.xlsx). This spreadsheet must be completed for every versement containing digital records in any form that arrives at CCA.** This file should be saved with the actual versement number in place of the word "versement", replacing any full stops or colons with underscores (e.g. "AR2014_0068_stabilization.xlsx"), and saved in the appropriate project folder in "Acquisitions et traitement". Please consult with the Digital Archivist on the proper use of this spreadsheet prior to your first digital processing project.  

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

*Note: This is a broad category that might include, e.g., floppy disks, optical media (CDs/DVDs), computers, internal hard drives, backup tape formats such as LTO, etc. For assistance in correctly identifying media types, please see the [Computer Media Identification Guide](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/mediaIDGuide.docx) or the UTSA Libraries' [Know Your Media](http://lib.utsa.edu/knowyourmedia/) page.*  

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

**Note: For digital media that will be disk imaged and accessioned immediately, a more steamlined procedure may be followed. Nonetheless, removal sheets should always be used to track where digital media were originally located.**

Steps:  

1. Print (on blue acid-free paper) and complete out two copies of the [CCA Digital Media Removal Sheet](https://github.com/CCA-Public/digital-archives-manual/blob/master/forms/Digital.Media.Removal.Sheet.pdf).  
2. Leave one of the copies of the Removal Sheet in the box or folder where you found the media, as close to where the media was found as possible.  
3. Put the media and the second copy of the completed Digital Media Removal Sheet in a new envelope or box and store this container in cool vault shelving.  
4. Create a TMS record for the new container (use the Digital Media Removal model):
    * **Object number:** "(accession number).DM##", e.g. "AR2013.0050.DM01"  
    * **Classification:** "médias numériques retirés"  
    * **Status flag:** "record for management need"  
    * **Nom de l'objet:** "digital media"  
    * **Title:** "Separated digital media"  
    * **Description du contenu:** Enter a brief description of the material and (optionally) the title of the folder from which it was taken.  
5. Add the following associations: 
    * **a classifier:** The fonds or collection to which the media belongs  
    * **Provient de:** The accession to which the media belongs  
    * **Est inclus dans (if applicable):** The groupe to which the separated media belongs  
6. Label the new container:
    * Object number  
    * Fonds or Collection number (when appropriate)  
    * Name of fonds or collection (short name is okay, e.g. you can write "Siza" instead of "Alvaro Siza fonds")  
7. If the media in the container (*note: specific pieces of media, not the folder or "groupe" they were found within*) already have ARCH, DR, or PH numbers, link the ARCH/DR/PH records to the DM container record as children with the "Est composé de" association.  
8. Give information about the new container to the Registrar as per usual localisation procedures, and request that the material is localised to the Digital Media storage in the Cool Vault.  

<a name="rawingest"></a>
## Ingesting "raw" accession data into digital repository  

Once data from all of the network transfer, temporary media, and original media in an accession has been stabilized, the digital component of the accession is ingested into CCA's Archivematica-based digital repository.  The aim of this step is to retain and safely store a copy of the data exactly as it arrived at CCA in the digital repository.  **Note that all files from network transfers or temporary media must be packaged in some time of archive format (zip, tar, rar, etc.), or else Archivematica will change original filenames and timestamps, defeating part of the purpose of the "raw" ingest. At CCA, we typically prefer to package in tar files. Note also that this step may not be necessary if disk images are to be retained as part of the processed material.**  

This SIP (Submission Information Package, in OAIS parlance) is composed of all files, archive packages, and disk images in the Shipping Space that correspond to an accession. It is named according to the convention "(versement number)\_raw".   

For the ingest of raw unprocessed data, we use the csp-arch-02 processing pipeline. In this pipeline, Archivematica is set not to extract packages, examine contents, or normalize any files. An AIP is created and stored, but no DIP is created. These settings must be manually selected for now, but eventually these will be the default settings in a "raw ingest" watched directory that will process material through Archivematica using Automation Tools scripts.    

Once an accession has been ingested into Archivematica, the Digital Archivist deletes the temporary copies from the Shipping Space and notifies the Registrar. The Registrar then updates the location for the appropriate accession records to "Dark archive".  
