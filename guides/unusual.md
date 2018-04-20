# Processing unusual file types

Certain file types require atypical processing workflows, often using specialized software. This guide documents CCA's workflows for processing unusual file types and their related software, which include:  

* [Email archives and ePADD](#email)
    * [Email formats](#emailformats)
    * [Import and appraisal module](#emailappraisal)
    * [Processing module](#emailprocessing)
    * [Export, SIPs, AIPs, and DIPs](#emailexport)
    * [Delivery module](#emaildelivery)
    * [Cleaning up ePADD](#cleanupepadd)
    
<a name="email"></a>  
## Email archives and ePADD

Email formats require additional processing, as they often contain sensitive or personal information, and as a format, are difficult to access by an end-user. [ePADD](https://library.stanford.edu/projects/epadd), developed by Stanford University Libraries, allows the processing archivist to search through email, restrict possibly sensitive materials, and provide a user-friendly access interface.

Full documentation on ePADD can be found in their [User Guide](https://docs.google.com/document/d/1ZMuWU0z-IVsk80_lUEYMfVrwfCsS1bp0sjL28GBGcMU/edit) and the [Community Forum](https://epadd.nimeyo.com/). 

ePADD can be downloaded [here](https://library.stanford.edu/projects/epadd/download), and installation instructions can be found in the User Guide. CCA recommends installing ePADD into Mac or Windows environments.

<a name="emailformats"></a>  
### Email formats 

ePADD only works with live email accounts (including IMAP) and email archives in the MBOX format. If your email archives are in a different email format, like Microsoft Outlook PST, they will need to be converted using [Emailchemy](https://weirdkid.com/emailchemy/), an email format converter located on the CD imaging workstation. The readpst command line utility is not recommended, as it throws errors in ePADD. 

Confirm the following settings are selected in Emailchemy: 

SCREENSHOT HERE.


<a name="emailappraisal"></a>  
### Import and appraisal module
**NOTE:** Before importing new archives into ePADD, ensure that the previous user properly [cleaned up ePADD](#cleanupepadd) from their session.

<a name="emailprocessing"></a>  
### Processing module

<a name="emailexport"></a>  
### Export, SIPs, AIPs, and DIPs

<a name="emaildelivery"></a>  
### Delivery module 

The delivery module is the access interface intended for researchers. It can be opened in the "ePADD mode" tab, like with the other modules. To launch the delivery module: 

1. Move the "epadd-delivery" folder to C:/Users/user
2. Launch ePADD
3. Click the gear in the top-right corner and select "ePADD Mode." From the drop-down menu, choose "DELIVERY."

The researcher can now navigate within the email archives. They can flag and annotate material, much like in the appraisal and delivery modules, and save a marked-up version of the email archive for their personal use. 

**NOTE:** Once you are in the ePADD delivery module, you cannot easily return to the previous modules. This is to prevent researcher interference with collections in process. (This is also true for the discovery module.) To return to previous modules: 

1. Make a note of which local host ePADD is using, by consulting your browser's URL. (It is typically 9099.)
2. Close out of all ePADD tabs in your browser.
3. Launch the Terminal and run the following command, where localhost is replaced by the local host number noted in Step 1: 
   ```
   netstat –ano |findstr :localhost
   ```
4. This will return a number of values. Look for where it says LISTENING, and make a note of the number next to it. This number is called a process identifier or PID.
5. Run the following command in Terminal, replacing PID with the number noted in Step 4: 
   ```
   tskill PID
   ```
6. Relaunch ePADD.

This can also be achieved by logging out of the workstation and logging in again.

<a name="cleanupepadd"></a>
### Cleaning up ePADD
For each module, ePADD save its contents to a corresponding directory in C:/Users/user. All of emails in those directories will display in the corresponding module, regardless of provenance, meaning that they must be deleted between processing projects so that materials are not accidentally mixed. In order to clean up ePADD:
1. Go to C:/Users/user.
2. There will be a number of directories whose titles begin with "epadd-." Delete all of these directories EXCEPT "epadd-settings." 
