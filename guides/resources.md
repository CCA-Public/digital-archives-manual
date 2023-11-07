# Additional resources  

Helpful resources, including:  

* [Reading material](#readings)  
* [Digital storage media identification and information](#media)  
* [File format identification and information](#formats)  
* [Digital preservation tools](#tools)  
* [Scripting resources](#scripting)
* [Preservation of computer-aided design](#cadpres)  
* [General resources](#general)  

<a name="readings"></a>  
## Reading material

#### Digital Preservation 101  

* Lavoie, Brian. "[The Open Archival Information System (OAIS) Reference Model: Introductory Guide (2nd Edition)](http://www.dpconline.org/component/docman/doc_download/1359-dpctw14-02)," DPC Technology Watch Report, 2014.  
* Trace, Ciaran. "[Beyond the Magic to the Mechanism: Computers, Materiality, and What it Means for Records to Be 'Born Digital'](https://www.ischool.utexas.edu/~cbtrace/pubs/CBT_Archivaria_2011.pdf)," Archivaria 72, 2011.  
* Caplan, Priscilla. "[Understanding PREMIS](http://www.loc.gov/standards/premis/understanding-premis-rev2017.pdf)," Library of Congress Network Development and MARC Standards Office, revised 2017.

#### On archival description  

* Callahan, Maureen. "[The Value of Archival Description Considered](https://icantiemyownshoes.wordpress.com/2014/04/04/the-value-of-archival-description-considered/)," Chaos->Order, 2014: Not strictly a digital preservation read, but something that anyone arranging and describing archives should read and occasionally revisit.  

#### On code/software  

* Ford, Paul. ["What is code?"](http://www.bloomberg.com/graphics/2015-paul-ford-what-is-code/), Bloomberg Businessweek, June 11, 2015: Quite possibly the best (and most entertaining) piece on the nature of code/software ever written.  

<a name="media"></a>  
## Digital storage media identification and information  

* [Know Your Media](http://lib.utsa.edu/knowyourmedia/)  

<a name="formats"></a>  
## File format identification and information  

* [Siegfried](http://www.itforarchivists.com/siegfried): Have a file with a missing or suspect file extension? Drag the file onto Siegfried's hammer and this site will do its best to recognize the file for you.  
* [All known extensions](http://www.digipres.org/formats/extensions/): Don't know anything about a file other than its extension? This is a good place to start.  
* [PRONOM](http://www.nationalarchives.gov.uk/PRONOM/Default.aspx): The most inclusive and detailed file format registry. Developed and maintained by the UK National Archives.  
* [Sustainability of Digital Formats Planning for Library of Congress Collections](http://www.digitalpreservation.gov/formats/index.shtml)  

<a name="tools"></a>  
## Digital preservation tools  

* [COPTR](http://coptr.digipres.org/Main_Page): The Community Owned digital Preservation Tool Registry. Includes the helpful Tools Grid, which categorizes digital preservation tools by function.  
* [BagIt 0.97 Specification](http://www.digitalpreservation.gov/documents/bagitspec.pdf): The specifications for the widely used packaging and validation scheme developed by the Library of Congress.  
* [Bitcurator wiki](http://wiki.bitcurator.net/index.php?title=Main_Page)  
* [Archivematica documentation](https://www.archivematica.org/en/docs/archivematica-1.4/)  
* [Preserving optical media from the command line](http://blog.kbresearch.nl/2015/11/13/preserving-optical-media-from-the-command-line/)  

<a name="scripting"></a>  
## Scripting resources

* [Script Ahoy](http://dd388.github.io/crals/): "Our community resource is intended to provide helpful one-liners and script code specifically drawn from real-life examples in archives and libraries."  
* [Command Line Crash Course](https://learnpythonthehardway.org/book/appendixa.html): From *Learn Python the Hard Way*  

<a name="scripting"></a>  
## Useful command line scripts

*  **Batch convert files in a directory and subdirectories using LibreOffice.**
    ```
    cd topDirectory
    for f in $(find . -type f -name "*EXT"); do libreoffice --convert-to doc $f --outdir $(dirname $f); done
    ```
    
  Change "EXT" to the file extension of the original files; note that it is case-sensitive. Change "doc" to the extension that the files should convert to. See ["Supported File Formats"](https://en.wikipedia.org/wiki/LibreOffice) for more information.

* **Recursively unzip files into a new folder with the title of the zip file into their current place in the directory, and then delete the original zip file when it's done:**
    
      cd topDirectory
      for F in $(find . -type f -name *.zip); do unzip "$F" -d "${F%.*}/" && rm "$F"; done
  
  ([Source](https://stackoverflow.com/a/30339287/9459120))
  
  For the same result with .rar files use:
      
      cd topDirectory
      for F in $(find . -name "*.rar"); do unrar x "$F" "${F%.*}/" && rm "$F"; done
  
  
  Note that the find command is case-sensitive, and will have to be changed according to the case of your zip or rar filenames. Both formats must not have spaces in their filename, or else the command will fail. If needed, use [Detox](https://linux.die.net/man/1/detox) prior to extracting files.
  
* **Identify duplicate directories across a collection:**
     
     Trying using [direct-dedupe](https://github.com/stefanabreitwieser/direct-dedupe) and then follow the Excel instructions below. It was built off of the following commands: 
     
     Run the following scripts in the command line individually. (Replace topDirectory with the file path for the highest level directory.) 
            
            cd topDirectory/
            find . -type d >> /home/bcadmin/Desktop/directories.csv
            for D in $(find . -type d); do du -sh $D >> /home/bcadmin/Desktop/filesize.csv; done
            for D in $(find . -type d); do find $D -type f -exec md5sum {} + | awk '{print $1}' | sort | md5sum >> /home/bcadmin/Desktop/checksums.csv; done

     This final command may take some time depending on the size of the collection. Together, these commands will create three CSV spreadsheets on the Bitcurator desktop, containing the list of directories, their human-readable size, and their checksums respectively. Move the columns into one spreadsheet, being mindful that the columns will require some light data clean up in order to get them to line up. It may be easier to have the TOPDIRECTORY be a subdirectory and combine all the spreadsheets at the end if you have more than a few thousand directories total.
     
     Once you've ensured that they match up correctly, create headers for each column and insert filters (Data/Filters or Donnees/Filtrer). Highlight the checksum column and do Home/Conditional formatting/Rules for highlighting cells/Duplicates or Accueil/Mise en forme conditionnelle/Regles de mise en surbrillance des cellules/Valeurs en double. This will change the color of all duplicate checksums, allowing you to identify and delete duplicate directories.

* **Identify all files with problematic timestamps in a directory and modify the timestamps:**
  
      cd topDirectory
      find . -type f -newermt "YYYY-MM-DD" ! -newermt "YYYY-MM-DD" -exec touch -t "YYYYMMDDHHMM" {} +
  
  ([Source 1](https://askubuntu.com/questions/191044/how-to-find-files-between-two-dates-using-find) and [Source 2](https://stackoverflow.com/questions/3718645/unix-shell-script-update-timestamp-on-all-sub-directories-and-sub-files-includ))
  
  In which, the script will look for files (-type f) in a certain range of dates (-newermt "YYYY-MM-DD" ! -newermt "YYYY-MM-DD") and then it will change those dates to the one specified by "YYYYMMDDHHMM".
  
  Prior to December 2018, it was determined that if the modification was required by an issue in timestamp's interpretation by UNIX time system, the new date should be "197001010000" which correspond to time 0 in UNIX time system. This strategy was reassessed, and the new date should be derived from the content of the archive being processed. Confirm replacement date with Digital Archivist.
  
* **Detox utility cleans file and directory names by removing spaces and translating/cleaning up Latin-1 (ISO 8859-1) characters encoded in 8-bit ASCII, Unicode characters encoded in UTF-8, and CGI escaped characters.**
     
     To do a test run (i.e. see proposed file name changes without actually making the changes): 
            
            detox -rn topDirectory
            
     To make the changes: 
     
            detox -r topDirectory

* **List and delete empty files and directories.**

    To list all empty files and directories: 
            
            cd [topDirectory]
            find . -empty
            
    To delete empty files: 
    
            find . -type f -empty -delete
    
    To delete empty directories: 
            
            find . -type d -empty -delete  

* **Print checksum mismatches between checksum.md5 file and objects directory to terminal**  

        cd /path/to/metadata/directory 
        md5deep -rlX checksum.md5 ../objects

    (the -X flag displays the hash and filename for each file in the objects directory that does not match the list of known hashes in  the checksum.md5 file)          

* **Batch remove commas from file names and replace with underscores**  

        cd /path/to/directory
        for f in $(find . -name "*,*"); do rename -v 's/,/_/' $f; done
        
    Note that this will only change the first comma in every file name. For example, if a file name contains five commas, you will have to run the command five times to replace every comma. 

* **Sync folders**

    This script copies or syncs a source folder with a destination folder. This is particularly useful if you have a copy of your files on a RAID and on Processing, and would like to update one to reflect processing with out having to copy-and-paste the whole thing. For large archives, this will be much faster as it keeps all files that stay the same.
    
    This script will copy a folder with the same name as the source folder in the destination directory. If that folder title already exists, it will sync the files. `-qam` is for quiet (i.e. error messages only), archival copy, and trims empty directories. `--delete` deletes any files at the destination that do not exist at the source.
    
    Note that this script **overwrites, deletes, and uses sudo** meaning that it is **very powerful.** It's not recommended that you use it without having some rsync experience.

        sudo rsync -qam --delete "/PATH/TO/SIPs/" "/PATH/TO/PARENT_OF_SIPs/"
  
* **Unlock folders**

    This script unlocks a folder's contents using sudo.
    
  Often when disk imaging, a file may be created in a locked mode. If you need to unlock a folder change the * to the folder path.
    
           sudo chmod 777 *    
        
<a name="cadpres"></a>  
## Preservation of computer-aided design  

* Ball, Alex. "[Preserving Computer-Aided Design (CAD)](http://dx.doi.org/10.7207/twr13-02)," DPC Technology Watch Report 13-02, April 2013.  
* Barrett, Anne. "[Born-digital Architectural Records: Defining the Archivable Record](https://cdr.lib.unc.edu/indexablecontent/uuid:4b813f81-387f-4fb7-9f5e-daa7f7b764f1)," UNC Master's Thesis, 2012.  
* Smith, MacKenzie. "[Curating Architectural 3D CAD Models](http://www.ijdc.net/index.php/ijdc/article/viewFile/105/80)," The International Journal of Digital Curation 1, vol. 4, 2008.  

<a name="general"></a>  
## General resources  

* [Digital Curation Google group](https://groups.google.com/forum/?fromgroups#!forum/digital-curation)  
* [DPC Digital Preservation Handbook](www.dpconline.org/advice/preservationhandbook/contents): Revised handbook by the UK's Digital Preservation Coalition.  
* [The Signal](http://blogs.loc.gov/digitalpreservation/): Library of Congress digital preservation blog.  
* [DSHR's blog](http://blog.dshr.org/): Blog of David S. Rosenthal, digital preservation veteran and developer of LOCKSS.  
* [Bentley Historical Library ArchivesSpace-Archivematica-DSpace Integration project blog](http://archival-integration.blogspot.ca/): Despite being the project blog of a particular project, this features many good posts on issues universally faced by archivists and institutions dealing with born-digital archives.  
