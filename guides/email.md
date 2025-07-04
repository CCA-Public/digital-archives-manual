# Email archives and ePADD

Email formats require additional processing, as they often contain sensitive or personal information, and as a format, are difficult to access by an end-user. [ePADD](https://www.epaddproject.org/). developed by Stanford University Libraries, allows the processing archivist to search through email, restrict possibly sensitive materials, create access and preservation copies, and provide a user-friendly access interface.

Full documentation on ePADD can be found in their [User Guide](https://docs.google.com/document/d/1PWzKyonRdogAChtHOQs-CVjCTMuQi00pLsHZRJateKw/edit) and the [Community Forum](https://groups.google.com/g/epaddusers). 

ePADD can be downloaded [here](https://www.epaddproject.org/using-epadd/download-and-install), and installation instructions can be found [here](https://docs.google.com/document/d/1PWzKyonRdogAChtHOQs-CVjCTMuQi00pLsHZRJateKw/edit). CCA recommends installing ePADD into Mac or Windows environments.

This documentation is up-to-date as of ePADD v10 (January 2023).

* [Email formats](#emailformats)
* [Import and appraisal module](#emailappraisal)
* [Processing module](#emailprocessing)
* [Export, SIPs, AIPs, and DIPs](#emailexport)
* [Delivery module](#emaildelivery)
* [Accessing email](#emailaccess)
* [Cleaning up ePADD](#cleanupepadd) 


<a name="emailformats"></a>  
## Email formats 

ePADD works with live email accounts (including IMAP) and email archives in the MBOX format. If your email archives are in a different email format, they will need to be converted using [Emailchemy](https://weirdkid.com/emailchemy/), an email format converter located on the CD imaging workstation. Note that the readpst command line utility is not recommended.

To use Emailchemy: 
1. Confirm the following settings are selected in Emailchemy, under Tools > Options >: 
    * General, check: 
       * De-duplicate messages while converting
       * Automatically clear de-duplicator memory after conversions
    * Files/Folders, check: 
       * Preserve folder structure
       * Allow non-English characters in new file and folder names
       * Replace disallowed filename characters with a dash
    * Logging, check: 
       * Write Conversion Log
       * Use default log file location
       * Log source file checksums before and after conversion
    * Headers, check: 
       * Strict RFC-2822 compliance for parsing
       * Preserve optional Extension and User-Defined header fields
       * Standardize dates
    * Outlook (Win), check: 
       * Save encrypted message text as attachment
       * Translate Exchange-style email address to Internet-style (SMTP)
       * Extract all message object types
2. Using the email conversion wizard, choose your source file type and click next. 
3. On the next screen, find the file or folder containing your email archives files. Click next.
4. Ensure the "filter duplicate messages" box is checked, and all others are unchecked. Click convert. This may take some time. 
5. Find the log file created during conversion and save it. It will eventually be included in your SIP-level metadata.

<a name="emailappraisal"></a>  
## Import and appraisal module
**NOTE:** Before importing new archives into ePADD, ensure that the previous user properly [cleaned up ePADD](#cleanupepadd) from their session.

The Appraisal module is the default starting screen after launching ePADD. Appraisal is intended to be used by the donor to do initial review and restriction of their own email. Notably, the “Do not transfer” flag will effectively delete emails, preventing them from being moved to the processing module.

For CCA's purposes, the appraisal module will typically only be used for its importer, as donors do not usually review their own materials. Additional review and restriction will occur in the processing module. To import your MBOX files into ePADD: 
1. Launch ePADD by clicking epadd.exe. By default, ePADD runs with 4GB of RAM, but additional RAM may be needed for larger collections. If this is the case, download epadd-standalone.jar, and launch ePADD using the code below, where # specifies the amount of RAM (in GB) you wish to allocate. 8 GB is typically sufficient.
   ```
   java -Xmx#g -jar /file/path/to/epadd-standalone.jar
   ```
2. Click "Import" at the top of the ePADD browser. 
3. Enter as much metadata as possible. This can be added to and edited in the processing module. 
4. Point ePADD to the emails to process:
   * For public email accounts (e.g. Google, Yahoo), enter the email address and password for the account. (Note that at the time of writing, we have not been able to test this feature.) 
   * For private IMAP accounts (e.g. CCA's Outlook inboxes), enter the IMAP server, email address, and password for the account. You may need to be in touch with the donor or their IT provider to access their server.
   * For MBOX files, select the directory where the MBOX files are located. The files need to be in a single directory. You may also enter the name of the email source, which is an optional field.
5. Click continue. The next screen will load all of the MBOX files or IMAP folders in the designated location. This may take some time. Check the box next to the appropriate folder and click Continue. (It is not necessary to input the date range.)
6. ePADD will work to read the selected files. This may take some time. When this process is complete, ePADD displays the emails in the appraisal module.

Because the appraisal module does not provide any unique functionality, and because CCA's use case does not anticipate donor review, the next step is to export the email from the appraisal module to the processing module. In order to do so: 

1. Click the Export tab at the top of the screen.
2. Under "Export messages and attachments," click Browse, and choose C:/Users/user. Click Export (NOT "Export to MBOX"). This may take some time. It will save as "ePADD archive of (name of archive creator)." This folder is now ready to be imported into the processing module.

<a name="emailprocessing"></a>  
## Processing module

The archivist can begin reviewing, restricting, and assigning metadata in the processing module. To do so: 

1. Switch ePADD to the processing module by clicking the blue question mark in the top right corner. Click "ePADD Mode." Choose "PROCESSING" from the drop-down menu.
2. Add your archives by clicking the Add tab. Next to "Accession folder," click Browse and choose the "Archive of (archive creator) folder" created in the previous module. Fill out as much metadata as possible. You can return to this later. Click "Import Accession." This may take some time.

### The Browse tab

Once ePADD has finished importing the accession, the archivist can begin processing the materials from the Browse screen which looks like: 

![Screenshot of ePADD Browse tab](../media/photos/epadd_screenshot.JPG)

The majority of this processing involves reviewing the email to ensure that it is within scope and does not contain sensitive material. While reviewing email, the Labels tab can be used to restrict materials. The labels "stick" when the archives is exported to the next module. The "Cleared for Release" and "Reviewed" flags are carried forward with their labels, and the emails marked "Do Not Transfer" are not moved to the next module, effectively restricting/deleting them from the preservation and access copy. Emails can also be scheduled for temporary restriction; see the [User Guide](https://docs.google.com/document/d/1PWzKyonRdogAChtHOQs-CVjCTMuQi00pLsHZRJateKw/edit) for more information.

![Screenshot of ePADD labels](../media/photos/epadd_labels.JPG)

**THROUGHOUT THIS PROCESSES YOU MUST SAVE YOUR WORK, USING THE SAVE TAB AT THE TOP OF THE SCREEN.** Your changes will not stick unless you save the archive. 

The review process need not occur in any particular order. ePADD provides the following tools:

1. *Correspondents:* A list of all email addresses (to, from, mentioned) in the archive, and ePADD's best guess at the contact's name and other email addresses. 
   * Edit correspondents list to correctly pair contacts with their email addresses.
   * Browse correspondents and label emails for out of scope correspondents (e.g. friends and family members) as "Do Not Transfer." When the processing module is exported, it will reindex the correspondents list so that none of the out of scope correspondents will be included in the final copy.
2. *Person entities:* A list of all people recognized by ePADD.
3. *Other entities:* A list of all places and corporate names recognized by ePADD.
4. *Folder view:* All emails sorted by folder (e.g. Inbox, Sent, Drafts). 
   * Determine whether all folders are within scope of the collection.
   * Review "Deleted Items" folders to determine whether they should be kept. 
5. *Image attachments:* A gallery of all images attached to emails.
6. *Other attachments:* All other file types attached to emails, available for download.
7. *Lexicon search:* Keyword searching based on defined lexicons to identify sensitive materials. A [CCA lexicon](../media/cca_lexicon) was created based on existing ePADD lexicons in order to collocate sensitive words relevant to CCA's use case. A [German lexicon](../media/german_lexicon) and [French lexicon](../media/french_lexicon.txt) were developed to provide additional (limited) language functionalities. Note that these lexicons should be considered in beta, and all lexicons should be considered in light of a collection's particular context.
   * Use lexicon searching to identify potentially sensitive and out of scope material. Lexicons can be added manually or installed directly; see the [Lexicon ReadMe file](https://docs.google.com/document/d/1RWU1kXUPa1kEf5_mEaNP_veQ8IX-Sw1J0mBJ8rRhS3Q/edit) and the [User Guide](https://docs.google.com/document/d/1PWzKyonRdogAChtHOQs-CVjCTMuQi00pLsHZRJateKw/edit) for more information.
8. *Labels:* Summary of labels used. New labels can be added here if needed.
9. *Data:* Import log. 
   * Ensure there were no major import errors.

### The Search Tab

In addition to using the lexicons, the Search tab allows for keyword searching. You may want to do this if you notice out of scope email that is not flagged by lexicon searching. For example, in AP195, the archive creator used her personal email to find a new apartment. None of the relevant words were flagged by the lexicons, and keyword searching terms like "rent," "lease," and "flat" made it possible to screen out this material.

### The Authorities Tab

The Authorities tab can be used to assign name authorities from LCNAF, VIAF, FAST, and Wikipedia. Current descriptive practices at CCA do not involve in-depth subject analysis; however, assigning authorities at this phase might be useful for later description and access, particularly when populating the "Names" field for file-level description. 

<a name="emailexport"></a>  
### Export to the Delivery module

When you have finished reviewing all emails, you can export the emails to the next ePADD modules, Discovery and Delivery. To do so: 

1. Click the Export tab at the top of the screen.
2. Under "Export messages and attachments," click Browse, and choose C:/Users/user. Click Export (NOT "Export to MBOX"). This may take some time. It will save two module folders: "ePADD archive of (archive creator) - delivery" and "ePADD archive of (archive creator) - discovery." The Discovery folder is not used at CCA and can be deleted.
3. You may also wish to export just the email attachments, or CSV files of the assigned authorities or email subject lines based on the processing needs for a particular collection; these options are also available on this screen. Note that they will export EVERYTHING from the Appraisal module, including the materials flagged "Do Not Transfer."

Note that the final MBOX file should not be exported from the Appraisal module, as it will include all of the restricted material. 

<a name="emaildelivery"></a>  
## Delivery module 

The delivery module is the access interface intended for researchers. For CCA's current use case, it is also used to create a final preservation copy of the files. It can be opened in the "ePADD mode" tab, like with the other modules. To launch the delivery module: 

1. Move the "Archive of (Archive Creator) Delivery module" file (exported from the Appraisal module) to a folder titled "epadd-delivery" in C:/Users/user
2. Launch ePADD.
3. Click the gear in the top-right corner and select "ePADD Mode." From the drop-down menu, choose "DELIVERY."

In order to export a preservation copy in the MBOX format: 

1. Navigate to the Search tab. 
2. Without entering anything in the search bar, click "Search." This should return all of the emails in the collection.
3. Click the "Export these messages as MBOX" button (the down arrow). ePADD will prepare your MBOX file. This may take some time.

![Screenshot of Export button](../media/photos/epadd_export.JPG)

4. On the next screen, click "Download MBOX file." This may take some time and often fails. Internet Explorer is recommended for this step.
5. This MBOX is ready to be packaged into a SIP using [SIP Creator](https://github.com/CCA-Public/sipcreator). After the SIP is packaged, be sure to include your Emailchemy log, as well as any additional CSV reports in the metadata folder of your SIP.

For AP195, the original files and the Appraisal module were kept, in recognition of the fact that email processing technology and workflows are rapidly improving. It is possible that we may want to return to these files as they appeared originally and at the time restriction was completed. These files were packaged into their own SIP and are restricted from user access.

### Leaving the Delivery module

Once you are in the ePADD delivery module, you cannot easily return to the previous modules. This is to prevent researcher interference with collections in process. (This is also true for the discovery module.) To return to previous modules: 

1. Make a note of which local host ePADD is using, by consulting your browser's URL. (It is typically 9099.)
2. Close out of all ePADD tabs in your browser.
3. Launch the Terminal and run the following command, where localhost is replaced by the number noted in Step 1: 
   ```
   netstat –ano |findstr :localhost
   ```
4. This will return a number of values. Look for where it says LISTENING, and make a note of the number next to it. This number is called a process identifier, or PID.
5. Run the following command in Terminal, replacing PID with the number noted in Step 4: 
   ```
   tskill PID
   ```
6. Relaunch ePADD. It will start in the Appraisal module by default.

This can also be achieved by logging out of the workstation and logging in again.

<a name="emailaccess"></a>
## Accessing email

In order to provide access to these files, the MBOX file in the SIP can be re-imported into ePADD and walked through each export phase to the Delivery module. The researcher can use the Delivery module to navigate within the email archives using many of the same tools as were available to the archivist during processing. They can flag and annotate material, much like in the appraisal and delivery modules, and save and download a marked-up version of the email archive for their personal use.

MBOX files can also be opened using other email tools, like [Thunderbird](https://www.thunderbird.net/), or in a text editor.


<a name="cleanupepadd"></a>
## Cleaning up ePADD
For each module, ePADD saves its contents to a corresponding directory in C:/Users/user. All of emails in those directories will display in the corresponding module, regardless of provenance, meaning that they must be deleted between processing projects so that materials are not accidentally mixed. In order to clean up ePADD:
1. Go to C:/Users/user.
2. There will be a number of directories whose titles begin with "epadd-." Delete all of these directories EXCEPT "epadd-settings." 

ePADD can now be used to process a new group of emails.
