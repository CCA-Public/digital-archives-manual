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

CCA-style DIPs can be created from AIPs registered in the Storage Service using the [create_dip.py](https://github.com/artefactual/automation-tools/blob/master/aips/create_dip.py) script included as part of Artefactual's Automation Tools. Best practice to generate a DIP on demand from a stored AIP is to call the Python script with all necessary parameters using the [create_dip_script.sh](https://github.com/artefactual/automation-tools/blob/master/etc/create_dip_script.sh) shell script. See the [Automation Tools repo](https://github.com/artefactual/automation-tools#dip-creation) for more details.  

On Archivematica pipeline VSP-AMPL-02, the [create_dips_job.py](https://github.com/artefactual/automation-tools/blob/master/aips/create_dips_job.py) script is configured within Automation Tools to automatically generate a DIP for every AIP stored in appropriate AIP Stores (excluding those used for storing unprocessed "raw" AIPs).  

A local version of Automation Tools has also been installed and configured on each of the dedicated BitCurator workstations to enable local creation of DIPs in BitCurator as need be - for instance, to help with filling a reference request. To create a DIP on one of the BitCurator stations:

* Go look up and copy the UUID for the relevant AIP from the Storage Service  
* Run the `create_dip_script.sh` script, passing the AIP UUID as the first argument:  
`/mnt/1TB_RAID/dips/automation-tools/create_dip_script.sh <UUID>`  

The DIP will be created in `/mnt/1TB_RAID/dips/dips`.  

<a name="accessworkflow"></a>  
## Current access workflow 

After the first phase of [SCOPE](https://github.com/CCA-Public/dip-access-interface) development, all access to born-digital content happens on a by-request basis through Reference. For now, when Reference receives a request they contact the Digital Processing Archivists, who create a DIP from each of the requested AIPs and upload them to SCOPE, where they are made available to the researcher on CCA's Study Room CAD workstation and virtualization workstation.

The Study Room CAD workstation and virtualization workstation have no internet access and USB ports are blocked. Researchers can take screenshots of material as needed, and reference will package them into a low-resolution PDF file and email them to the researcher.

SCOPE is only available on the workstations, at the reference desk, and for digital processing archivists and reference staff. Research access is limited to the reading room only, including for all other CCA staff.

<a name="accessplans"></a>  
## Access plans  

After the second phase of development, SCOPE will automatically point to Archivematica's Media Server (DIP storage) in order to reduce the workload of linking DIPs manually. At this time, all processed digital collection material will be made available via SCOPE, which will be continually added to as new collections are processed.
