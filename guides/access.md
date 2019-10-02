# Access

* [Definition of CCA-style DIPs](#dipdefinition)  
* [Creating CCA-style DIPs](#dipcreation)  
* [Current access workflow](#accessworkflow)
* [Access plans](#accessplans)

<a name="dipdefinition"></a>  
## Definition of CCA-style DIPs  

CCA-style DIPs take the following form:

`[transfer name]_[AIP UUID]_DIP` (top directory)  
----`METS.[AIP UUID].xml` (METS file describing contents of DIP)  
----`objects` directory  
--------`[transfer name].zip` (DIP contents zipped as single file)

The zip file in the `objects` directory contains a copy of all original files included in the transfer - with filenames and last modified dates restored to their original values - as well as a copy of the AIP's `submissionDocumentation` directory and the AIP METS file.  

<a name="dipcreation"></a>  
## Creating CCA-style DIPs  

CCA-style DIPs can be created from AIPs registered in the Storage Service using the [create_dip.py](https://github.com/artefactual/automation-tools/blob/master/aips/create_dip.py) script included as part of Artefactual's Automation Tools. Best practice (without using SCOPE) is to generate a DIP on demand from a stored AIP is to call the Python script with all necessary parameters using the [create_dip_script.sh](https://github.com/artefactual/automation-tools/blob/master/etc/create_dip_script.sh) shell script. See the [Automation Tools repo](https://github.com/artefactual/automation-tools#dip-creation) for more details.  

On Archivematica pipeline VSP-AMPL-02, the [create_dips_job.py](https://github.com/artefactual/automation-tools/blob/master/aips/create_dips_job.py) script is configured within Automation Tools to automatically generate a DIP for every AIP stored in appropriate AIP Stores (excluding those used for storing unprocessed "raw" AIPs).  

A local version of Automation Tools has also been installed and configured on each of the dedicated BitCurator workstations to enable local creation of DIPs in BitCurator as need be - for instance, to help with filling a reference request. To create a DIP on one of the BitCurator stations:

* Go look up and copy the UUID for the relevant AIP from the Storage Service  
* Run the `create_dip_script.sh` script, passing the AIP UUID as the first argument:  
`/mnt/1TB_RAID/dips/automation-tools/create_dip_script.sh <UUID>`  

The DIP will be created in `/mnt/1TB_RAID/dips/dips`.  

<a name="accessworkflow"></a>  
## Access workflow 

[SCOPE](https://github.com/CCA-Public/dip-access-interface) is a born-digital archives access inteface developed by the CCA and Artefactual Systems. When new material is ingested through Pipeline 2 in Archivematica, a DIP is automatically created and pulled into SCOPE. When a researcher requests access to proccessed born-digital material, Reference makes them a login to SCOPE and the researcher can access the material in a self-directed manner. 

SCOPE is only available to the researcher on CCA's Study Room CAD workstation and virtualization workstation. The Study Room CAD workstation and virtualization workstation have no internet access and USB ports are blocked. Researchers can take screenshots of material as needed, and reference will package them into a low-resolution PDF file and email them to the researcher. 

CCA archives staff (not internal researchers) can access SCOPE via the BitCurator machines and at the reference desk. Research access is limited to the reading room only, including for all other CCA staff.

Unprocessed digital collection material can be made available on a case-by-case basis. Reference staff should make the Digital Archivist aware of the request. Then the Digital Archivist will create a DIP based on the workflow [above](#dipcreation) and move the files to the researcher's Research Materials folder. The researcher can then access the files via the Study Room workstations. 
