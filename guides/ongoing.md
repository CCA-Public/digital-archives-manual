# Ongoing activities

<a name="fixity"></a>  
## Fixity checking and repair  

Fixity checks of all AIPs are conducted on a quarterly basis using the [Fixity](https://github.com/artefactual/fixity) application. Fixity's "scanall" function is run via a Bash script. Logs are saved on the Archivematica Storage Service server and results are emailed to Storage Service administrators.    

When AIP corruption is detected, the AIP is restored from backups according to the Storage Service's [Recovery](https://www.archivematica.org/en/docs/storage-service-0.7/recovery/#recovery) procedures.  

<a name="access"></a>  
## Access  

In the short term, all access to born-digital content happens on a by-request basis through Reference. When Reference receives a request, they contact the Digital Archivist, who places consultation copies of content into the Research Material folder, where it will be made available to the researcher on CCA's Study Room CAD workstation.  This approach has a number of limitations:  

* It is a manual and time-consuming process  
* Files must be copied from "raw" accessions, because Archivematica's AIPs and DIPs are meant to be machine processed, not browsed directly by end users in a file system  
* Not all files can be copied to Research Materials or consulted on the CAD workstation due to Windows file path limits and other technical considerations  
* Following this approach, we are unable to leverage any of the technical metadata Archivematica gathers for access purposes. Files without extensions, for example, will be confusing and/or unusable to researchers without extensive intervention by CCA staff  

The Study Room CAD workstation has no internet access and USB ports are blocked. For now, researchers may not make copies of files for their personal use off of the Study Room machine. They are welcome, however, to use their own phones or cameras to take photos of the screen.  

Over the long-term, we aim to leverage the Dissemination Information Packages (DIPs) created by Archivematica alongside the extensive technical and descriptive metadata in the AIP METS file to faciliate access to digital files. This might happen through AtoM, where item-level records for digital files (as well as the files themselves, viewable in browser or downloadable to the desktop) could be automatically created by Archivematica/AtoM under file-level descriptions created by our archivists and catalogers.  
