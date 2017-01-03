# Pre-processing: Triage and evaluation of born-digital archives  

When an accession is to be processed, the Digital Archivist downloads the "raw" AIPs containing all digital data and begins the triage and reporting process. The result of this process will be working files for the processor to arrange and describe as well as detailed reports to aid in the decision-making process surrounding arrangement, description, and preservation of the archives. This guide describes the steps taking in this pre-processing stage, and includes:  

* [Extracting files from packages and disk images](#diskimageextract)  
    * [Extracting files from disk images with Bitcurator](#bitcuratorfiles)  
      * [Bitcurator Disk Image Access Interface](#bcaccess)  
      * [Mount Disk Image script](#mountscript)  
    * [Extracting files from disk images with FTK Imager](#ftkimagerfiles)  
    * [Extracting files from images of Hierarchical File System (HFS) disks](#hfsfiles)  
* [Reporting](#reporting)  
* [Moving files to processing location](#moving)  

<a name="diskimageextract"></a>
## Extracting files from packages and disk images  

In order to analyze, arrange, and describe the digital objects that make up a versement, it is first necessary to extract the file contents from any archive packages (7zips) and disk images that were created during the accessioning and stabilization process.  

Files can be extracted from archive packages via the use of the free and open source software such as 7zip (Windows/Linux) or The Unarchiver (Mac).  

The simplest way to extract files from disk images is to do so as part of the reporting processing using [Brunnhilde](https://github.com/timothyryanwalsh/brunnhilde).  

For extracting files from disk images outside of the reporting process, we typically use one of two tools for extracting files from disk images: [Bitcurator](#bitcuratorfiles) or [FTK Imager](#ftkimagerfiles).  

<a name="bitcuratorfiles"></a>  
### Extracting files from disk images with Bitcurator  

Bitcurator has two native tools for extracting files from disk images: the [Bitcurator Disk Image Access Interface](#bcaccess) and the [Mount Disk Image script](#mountscript).  

<a name="bcaccess"></a>  
#### Bitcurator Disk Image Access Interface  

Steps:  

* Open the Bitcurator Disk Image Access tool from the "Forensics Tools" folder on the Bitcurator desktop.  

![bcaccess1](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/media/photos/bcaccess1.png)  

* Choose "Open disk image" from the top menu panel. In the pop-up window, select the correct disk image and then press "Open".  

![bcaccess2](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/media/photos/bcaccess2.png)  

* If the disk image is read successfully, you will see "Done" as the last line in the Messages pane, and a path to the disk image in the main (white) pane. If you wish, you can open the tree by clicking on the arrow to the left of "Disk Image" to navigate the contents of the disk image.  

![bcaccess3](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/media/photos/bcaccess3.png)  

* Choose "Select All" from the top menu panel to select all of the files stored on the disk.  

![bcaccess4](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/media/photos/bcaccess4.png)  

* Once all files have been selected, choose "Export selections" from the top menu and create a folder in your project folder on the desktop (putting the disk's identifier in place of "FOLDER NAME HERE" in the below example.)  

![bcaccess5](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/media/photos/bcaccess5.png)  

* The Disk Image Access Interface logs its progress in the Messages pane. If the process is successful, you will see a list of the exported files followed by the line "Copied checked files to the directory: <PATH>".  

![bcaccess6](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/media/photos/bcaccess6.png)  

* Just to be sure, visually verify that files have been copied to the Desktop folder you created. If all looks good, you can choose "Close disk image" from the top menu of the Disk Image Access Interface and start the process over for the next disk.  

If you encounter any errors during this process, make a note of this in your versement stabilization spreadsheet and then attempt to extract files via the next method: Bitcurator's [Mount Disk Image script](#mountscript).  

<a name="mountscript"></a>  
#### Mount Disk Image script  

If the Disk Image Access Interface is unable to export files, Bitcurator offers another option: mounting disk images as drives via an included Mount Disk Image file system script and manually copying over files.  

Steps:

* Right-click on the disk image. From the Scripts menu, choose "Mount Disk Image".  

![mountscript1](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/media/photos/mountscript1.png)  

* If the script was able to successfully mount the disk image, you will see a new drive available on the Desktop and in the dock on the left-hand side of the screen.  

![mountscript2](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/media/photos/mountscript2.png)  

* Click on the drive icon on the dock (or the desktop). This will allow you access to the files on the disk through the graphical user interface. From here, copy and paste the root directory or any files into a new folder in your project folder on the desktop (named after the disk's identifier).  

![mountscript3](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/media/photos/mountscript3.png)  

Note: As you can see from the terminal window in the screenshot below, the Mount Disk Image script works by mounting the disk in the /media directory. The image will remain mounted as a drive in this directory until you unmount the disk image. **Please be sure to unmount the disk image after you have finished copying all files.** In order to unmount the disk image, right-click on the disk image file. From the Scripts menu, choose "Unmount Disk Image". If you are unsure if the image has been unmounted, you can open a Terminal and enter the following command:  

```ls /media```  

If you see the disk's identifier listed in the results, the disk image has not yet been unmounted.  

![mountscript4](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/media/photos/mountscript4.png)  

<a name="ftkimagerfiles"></a>  
### Extracting files from disk images with FTK Imager  

* From the File menu, select "Add Evidence Item..."  

![ftkextract1](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/media/photos/ftkextract1.jpg)  

* In the Select Source menu, select "Image File" and then press "Next".  

![ftkextract2](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/media/photos/ftkextract2.jpg)  

* In the Evidence Source Selection menu, click "Browse", find the disk image file you would like to extract files from, then press "Open" and "Finish".  

![ftkextract3](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/media/photos/ftkextract3.jpg)  

* You should now see the media listed in the Evidence Tree window. In the Evidence Tree (not the File List, as pictured below), right-click on the root folder you would like to extract and choose "Export Files...".  

![ftkextract4](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/media/photos/ftkextract4.jpg)  

* Select a Destination for the files that you are extracting.  

![ftkextract5](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/media/photos/ftkextract5.jpg)  

* If the process is successful, you should see an "Export Results" pop-up with details on the number of folders, files, and bytes copied. If the process was successful, press "OK" and visually verify through the file explorer that the files have been saved in the location you intended. If all looks good, note that files have been extracted in the versement stabilization spreadsheet, and move on to the next disk image. If there were any errors, make a note of this in the versement stabilization spreadsheet and consult the Digital Archivist.  

![ftkextract6](https://github.com/timothyryanwalsh/cca-digitalprocessingmanual/blob/master/media/photos/ftkextract6.jpg)  

<a name="hfsfiles"></a>
### Extracting files from images of Hierarchical File System (HFS) disks   

You may find in some cases that neither Bitcurator nor FTK Imager is able to extract files from a disk image. Typically this will be because the media is formatted using a file system that modern operating systems cannot read.  

Nine times out of ten, when a disk image cannot be read or mounted on a modern machine it is because the disk is using the HFS file system. HFS (Hierarchical File System) is an Apple file system associated with "Classic" versions of the Mac operating system (i.e., those prior to OS X). Although modern machines cannot read HFS natively, we can use an open source tool called HFSExplorer (included in Bitcurator) to export usable files from such disks. This is the same tool used by Brunnhilde to characterize and extract files from HFS-formatted disks.

HFSExplorer can only read raw disk images. If starting with an EWF/E01 forensic disk image, you must first convert our E01 disk image into a raw format that HFSExplorer can read. To do this we will utilize a command-line utility called ewfexport.  In Bitcurator, open a command line terminal, navigate to the directory containing the target .E01 disk image, and enter the command

```ewfexport [FILENAME.E01]```  

If the Encase disk image has been split into multiple parts (E01, E02, etc.), it is only necessary to point ewfexport to the E01 file.  

At this point, ewfexport will ask you for some additional input. Enter the following:  

* **Export to format:** raw (this should be the default; if so, just press enter)  
* **Target path and filename without extension... :** ./FILENAME  
* **Evidence segement file size in bytes:** 0 (this should be the default; if so, just press enter)  
* **Start export at offset:** 0 (this should be the default; if so, just press enter)  
* **Number of bytes to export:** maximum value in range (this should be the default; if so, just press enter)  

At this point, ewfexport will tell you the process might take a few minutes and get started. When the process is completed, there should be a *.raw file in your target destination to match the E01 file you selected as the input.  

Once you have the raw disk image, open HFSExplorer (located in the 'Additional Tools' folder on the Desktop).  

![hfsexplorer1](http://wiki.bitcurator.net/images/c/c2/HFS1.png)  

From the 'File' menu, select 'Load file system from file' and then select the raw disk image file.  

![hfsexplorer2](http://wiki.bitcurator.net/images/3/30/HFS2.png)  

If attempting to load the raw image results in an error, the media probably wasn't formatted as an HFS disk. At this point, make a note in your versement stabilization spreadsheet and consult with the Digital Archivist.  

If HFSExplorer can read the disk it will give you an option of which partition to read. Typically you will want to choose HFS (if this is not an option or you are not sure here, consult the Digital Archivist). You should now see a list of files.  

The final step is to export these files from HFSExplorer to a desktop or network location. To export files:

* Select all files to be exported (at this stage, this should be everything - including system files) and press the 'Extract' button.  

![hfsexplorer3](http://wiki.bitcurator.net/images/8/88/HFSextract1.png)  

* Choose your destination location and select 'Extract Here'.  

![hfsexplorer4](http://wiki.bitcurator.net/images/6/61/HFSextract2.png)  

* A pop-up window will appear asking if you want to follow symbolic links while extracting. Select 'Yes'.  

![hfsexplorer5](http://wiki.bitcurator.net/images/0/0a/HFSextract3.png)  

* If all goes well, you will get a message saying 'Extraction finished.' NOTE: It is common for HFSExplorer to run into an issue with invalid characters in file names during the export process, due to the differences in allowable file name characters between HFS and modern file systems. When HFSExplorer runs into files will such characters, a pop-up window will appear asking you to auto-rename or manually rename the files. You may select auto-rename, which will replace 'illegal' characters such as forward slashes ('/') and full spots ('.') with underscores ('_').

<a name="reporting"></a>  
## Reporting  

The goal of the reporting step is to gain a more thorough understanding of the content to be arranged and described, as well as to automate some of the more rote elements of description and flag potential preservation issues.  

In order to accomplish this task, Processing Archivists can use the Brunnhilde GUI tool (in the "Additional Tools" folder on CCA-configured Bitcurator worksations) to gather information such as:

1. File format types and versions  
2. Existing organizational structure  
3. Extents and prevalent file types across directories  
4. Duplicate content  
5. Potential preservation issues  
6. Potential personal information and confidentiality issues  

<a name="moving"></a>  
## Moving files to processing location  

Once the files are ready to be arranged and described and preliminary reporting has been completed, working copies of the files are moved to a folder in the Catalogers network share. These are temporary copies solely for consultation on CAD workstations and other networked computers at CCA. "Master" copies of SIPs should be kept on the Bitcurator desktop while being worked on.