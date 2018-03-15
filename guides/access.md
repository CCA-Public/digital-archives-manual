# DIP Generation and Access

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

<a name="accessworkflow"></a>  
## Current access workflow 

All access to born-digital content happens on a by-request basis through Reference. For now, when Reference receives a request they contact the Digital Archivist, who creates a DIP from each of the requested AIPs and copies them to the Research Material folder, where they are made available to the researcher on CCA's Study Room CAD workstation and virtualization workstation.  

The Study Room CAD workstation and virtualization workstation have no internet access and USB ports are blocked. For now, researchers may not make copies of files for their personal use off of the Study Room machines. They are welcome, however, to use their own phones or cameras to take photos of the screen.  

<a name="accessplans"></a>  
## Access plans  

Description of DIP Access Interface to come.
