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

Description to come.

<a name="accessworkflow"></a>  
## Current access workflow 

All access to born-digital content happens on a by-request basis through Reference. For now, when Reference receives a request they contact the Digital Archivist, who creates a DIP from each of the requested AIPs and copies them to the Research Material folder, where they are made available to the researcher on CCA's Study Room CAD workstation and virtualization workstation.  

The Study Room CAD workstation and virtualization workstation have no internet access and USB ports are blocked. For now, researchers may not make copies of files for their personal use off of the Study Room machines. They are welcome, however, to use their own phones or cameras to take photos of the screen.  

<a name="accessplans"></a>  
## Access plans  

Description of DIP Access Interface to come.
