# Disk imaging with the Kryoflux

Note: Elements from the guidelines below have been gathered from the [Archivist’s Guide to KryoFlux](https://docs.google.com/document/d/1LViSnYpvr2jf1TrCh6ELuL-FWo14ICw-WZeb8j5GGpU/edit#), a comprehensive resource for practitioners working with born-digital materials in an archival context. 

The [Kryoflux](https://www.kryoflux.com/) is a floppy disk controller card developed by the [Software Preservation Society](http://www.softpres.org/) for imaging a wide variety of legacy floppies. Its particularity lies in its capacity to capture raw track data by sampling the fluctuation in the bit cells on the platter, enabling the capture of any type of 5.25" or 3.5" floppy disk, despite
its format.

## Capturing disk images using the graphical user interface (GUI)
1.	From the BitCurator03 work station, launch the KryoFlux GUI by double-clicking on the file called kryoflux-ui.jar located on the Desktop.
2.	At the beginning of each imaging session, calibrate the floppy drive by selecting the correct drive from the *Drive* menu then selecting *Calibrate* from the same menu. The 5.25" drive corresponds to *Drive 0* and the 3.5" drive to *Drive 1*. You should only need to calibrate the drive once per imaging session and any time you switch between disk drives. 

![Kryoflux](https://github.com/timothyryanwalsh/cca-digitalarchivesmanual/blob/master/media/photos/kryoflux_step2_calibrate.png)

3.	Configure the KryoFlux GUI to select the output directory for your newly-created disk images and log files. To do so, select *File → Settings* and click on the *Output* tab. Browse to the appropriate path to storage. Ensure that the Logs button is checked, and then click *OK*.
4.	For each disk, enter a unique identifier. Click on *Enter name…* and type in a unique ID associated with the disk. The text entered here will become the filename for any disk images and log files created. Do not include the extension of the file name.
5.	Select the image format(s) for the disk image using the dropdown list below the filename field. 

![Kryoflux](https://github.com/timothyryanwalsh/cca-digitalarchivesmanual/blob/master/media/photos/kryoflux_step5_selectformat_02.png)

Use the tables below to select the right image format(s). In order to choose multiple outputs, hold down the *Control (Ctrl)* key while making your selections.  In most cases, selecting an image format to obtain a sector image requires that you know something about the media in hand (physical format, system format, density, etc.)

**Common Media Types and Image Formats**

|Physical Format|	System Format	| Encoding	| Capacity | Image Profile/Format |
| ------------- |:-------------:| -------- | -------- | -------------------- |
| 3.5” double density |	Macintosh |	GCR	| 400 KB; 800 KB | Apple DOS 400K/800K sector image
| 3.5” double density |	PC	| MFM	| 720 KB | MFM sector image |
| 3.5” high density |	Any	| MFM	| 1440 KB | MFM sector image |
| 5.25” double density	| PC	| MFM	| 320 KB; 360 KB | MFM sector image [40 tracks] |
| 5.25” high density	| PC	| MFM	| 1200 KB | MFM sector image [1.2MB] |


**Specifications for Commonly Used Image Profiles** 

| Profile Name |	Start Track	| End track	| Side Mode | Sector Size | Sector Count | Track Distance | Target RPM |
| ------------ | ----------- | --------- | --------- | ----------- | ------------ | -------------- | ---------- |
| MFM sector image [1.2MB] |	At least 0 |	At most 83	| Both sides | 512 Bytes | Exactly 15 | 80 Tracks | 360 |
| MFM sector image |	At least 0 |	At most 83	| Both sides | 512 Bytes | Any | 80 Tracks | By image type |
| MFM sector image [40 tracks] | At least 0 | At most 83 | Both sides | 512 Bytes | Any | 40 Tracks | By image type |
| Apple DOS 400K/800K sector image | At least 0 | At most 83 | Both sides | 512 Bytes | Any | 80 Tracks | By image type |


6.	Once you have everything set up, insert the disk into the appropriate drive and click *Start*. In the Tracks section of the window, you should see the cells fill progressively with different colours. Here is each colors’ signification:


| Color | Meaning |
| ------------- | ------------- |
| Green | Good: The track was imaged successfully! |
| Orange | Good + modified: The track was imaged successfully but has one or more sectors that were modified after formatting or mastering. |  
| Red | Bad: The track was not imaged successfully |
| Grey | Unknown: The Kryoflux software could not determine the status of this track. This may or may not mean that it was read successfully. It could indicate that this track was unformatted or that the wrong format was selected prior to capture. If you are creating only preservation stream files, all sectors will be grey. | 

7.	Once you hear the read head returning to its starting point (0), the disk stops spinning and the drive’s indicator light goes off meaning that the capture is done. A log file will automatically be generated in the directory you selected at step 3.
8.	To image another disk, go back to step 4 and go on from there. If you switch drive and have not calibrated the other drive, continue from step 3. 

![Kryoflux](https://github.com/timothyryanwalsh/cca-digitalarchivesmanual/blob/master/media/photos/kryoflux_step7_cells.png)
 
 *The coloured cells show that the chosen Image Profile was not appropriate for the disk. Whenever you see a result pattern alternating between Unknown and Good (+ Modified), you probably have a 40 tracks disk. Retry imaging with the MFM sector image [40 tracks] profile and compare results.* 

### Capturing floppy disks with physical damage or reading difficulties

IMPORTANT NOTE: Whenever you notice the presence of mould or fungus on a piece digital media, consult Conservation and the Digital Archivist before capturing the disk image. Mould could spread inside the drive and on the read head and would risk contaminating other disks subsequently. To reduce the risk of contamination, you could use a drive exclusively dedicated to imaging contaminated media.
For stubborn disks that appear to have multiple bad sectors and physical damage, here is the procedure:

1.	In the output formats dropdown list, select **the format you believe the disk to be** and the **Kryoflux stream files, preservation** formats. This way you can verify if the disk was read correctly, and perform retries in case of errors. In addition, the raw stream files will act as preservation files if the selected encoding format doesn’t correspond to the format of the disk. They can also be used to output new disk image files in [deviceless mode](#deviceless).
2. **WARNING: Running the drive's head multiple times on the same sector of a disk can create permanent physical damage to the media. Only use this option if data preservation prevails on the media's physical preservation.**	
You can set the number of retries to a larger value if the disk is particularly difficult to read. Each time the head retries to read a sector, it “polishes” it by cutting through intrusive substances, such as dust, fungus and mould. We have set the number of retries to 20 – which is already more significant than the default number of 5 retries – but you could go up to 100.
To set the number of retries, go to *File > Settings > Output* and enter the number of retries you wish to execute in the “Retries” field. 
3.	Follow steps 6 to 8 from the previous section.
4.	Pay attention: Listen to the sound of the drive and notice any abnormalities. Look at the status in the Kryoflux GUI and note any bad sector or unknown format in your processing spreadsheet. 

*Instructions in this section were inspired by Dr. Gough's Tech Zone article on [Dealing with difficult disks and drives](http://goughlui.com/2013/05/19/project-kryoflux-part-6-dealing-with-difficult-disks-and-drives/). Please refer to the full article for more details about hardware care and data recovery using the Kryoflux.*

<a name="deviceless"></a>
### Using the GUI in deviceless mode
Once captured, Kryoflux stream files can be used directly from the GUI to produce encoded image files and avoid running any piece of external hardware. This technique can be useful to process fragile disks that shouldn't be read multiple times to avoid permanent physical damage. It can also be used for processing preservation files at a later time in your workflow. On the down side, Kryoflux streamfiles are proprietary and are much larger in size than the disk image files: their long term rentention is thus not encouraged at the CCA.

Here are the steps to output new encoded image files out of Kryoflux stream files:
1. Go to *Drive* and select *Stream Files*
2. Select the output destination.
2. For each disk, enter a unique identifier. Click on *Enter name…* and type in a unique ID associated with the disk. The text entered here will become the filename for any disk images and log files created. Do not include the extension of the file name.
3.	Select the image format(s) for the disk image using the dropdown list below the filename field.
4. Click on *Start* and select the folder containing the stream files you want to process. Click on *Open* and the disk image file creation will start right away. The results will show up in the cells of the GUI, as usual.
