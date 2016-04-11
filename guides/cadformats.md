# CAD, BIM, and 3D modeling software/file formats  

Vendor/software-specific formats:  

* [AutoCAD (.dwg, .dxf, .dwf)](#autocad)
* [Revit (.rvt)](#revit)
* [3DS Max (.3ds, .max)](#3ds)  
* [Rhinoceros (.3dm)](#rhino)  
* [Microstation (.dgn)](#microstation)  
* [Maya (.ma, .mb)](#maya)  
* [Alias (.wire)](#alias)
* [form-Z (.fmz)](#formz)  
* [CATIA (.CATPart, .CATProduct, others)](#catia)  
* [Digital Project (.CATPart, .CATProduct)](#digitalproject)  
* [SOLIDWORKS (.SLDPRT)](#solidworks)  
* [SketchUp (.skp)](#sketchup)  

Vendor-neutral formats:  

* [STL (.stl)](#stl)  
* [IGES (.iges, .igs)](#iges)  
* [STEP (.step)](#step)  
* [COLLADA (.dae)](#dae)  
* [IFC (.ifc)](#ifc)  

GENERAL NOTE: ALSO CHECK OUT [NAVISWORKS](https://knowledge.autodesk.com/support/navisworks-products/troubleshooting/caas/sfdcarticles/sfdcarticles/Supported-file-formats-and-applications-for-Autodesk-Navisworks-2009-to-2012.html) AS MULTI-CAD VIEWER.  

<a name="autocad"></a>  
## AutoCAD  

**Associated file extensions**: .dwg, .dxf, .dwf  
**Vendor:** Autodesk  

#### Summary  

First released in 1982, AutoCAD is the world's most widely-used 2D and 3D desktop (and, since 2010, cloud-based) computer-aided design and drafting tool.  

#### Associated file formats    

**DWG:** AutoCAD's proprietary binary native file format. Although DWG is a proprietary format, it has been reverse-engineered and made compatible (to varying degrees) with many non-AutoDesk software platforms.  

**DXF (Drawing Interchange Format, or Drawing Exchange Format):** An open data transfer format developed by Autodesk, with [published specifications available](http://images.autodesk.com/adsk/files/autocad_2012_pdf_dxf-reference_enu.pdf) online. DXF exists in both ASCII and binary forms. ASCII DXF files are text files that can be read and modified with any text editor.  

**DWF (Design Web Format):** An open 2D and 3D data visualization format developed by Autodesk. DWF files are highly compressed, and are not intended as a replacement for original design files.  

#### How to view files on CCA CAD workstations  

All three file types can be opened with AutoCAD 2014 (read/write), DWG TrueView (read-only), and Bentley View (read-only).  

Due to DWG's popularity, it can also be viewed (less efficiently) with general image format software such as QuickView Plus.  

Typically, DWG TrueView is the easiest comprehensive tool for viewing standard AutoCAD file formats. If you need to investigate a file via the command terminal, use AutoCAD instead.  

#### Backup (BAK) and auto-save files  

"Drawing backup files are typically created every time that you manually save a .dwg file. By default the file will be saved in the same location as the .dwg and will have the same name as the drawing but with a .bak extension, such as, site_topo.bak. A backup file is an exact copy of the drawing file prior to the last save. As such, backup files are always one version older than the currently saved drawing. Only one backup file is retained at a time so newly created backups will always replace older backups of the same name.  

Note: Backup files are created only if the system variable ISAVEBACK is set to 1.  

Backup files are essentially renamed .dwg files. You can recover data saved in .bak files by renaming the .bak extension to dwg and then opening that file in AutoCAD."  

Source: ["Understanding AutoCAD backup and autosave files," Autodesk, Jan 30, 2015](https://knowledge.autodesk.com/support/autocad/troubleshooting/caas/sfdcarticles/sfdcarticles/Understanding-AutoCAD-backup-and-autosave-files.html)  

#### Features of note  

AutoCAD 2014 is capable of reading all versions of DWG file formats and writing some older DWG formats (R14 and newer).  

AutoCAD was not produced for Mac between 1994 and 2010.   

#### Can import  

.3ds, .dgn, .dwg, .dws, .dwt, .dxf, .fbx, .sat, .wmf  

#### Can export  

.3ds, .bmp, .dgb, .dwf, .dwg, .dxf, .fbx, .pdf  

#### Preferred terminology in description  

lorem ipsum  

<a name="revit"></a>  
## Revit 

**Associated file extensions:** .rvt  
**Vendor:** Autodesk  

#### Summary  

Revit, first released in 2000, is Building Information Modeling (BIM) software for use by architects, engineers, designers, and contractors. BIM software allows the same file to be used for 3D design, 2D drafting, annotation, and integration of building information such as standard parts catalogues. It includes tools to be used at every stage in a building's lifecycle, including design, construction, maintenance, and demolition.  

#### How to view files on CCA CAD workstations  

Most Revit files should open in Revit 2014. If you are having difficulty opening a file, attempt to open it with the "Audit" button checked in Revit.  

#### Features of note  

Revit projects can be exported as IFC files. Some Revit-specific information may be lost in the process, but IFC is the closest thing to a comprehensive vendor-neutral/standard format available for BIM.  

#### Can import  

.dgn, .dwg, .dxf, .jpg, .png, .sat, .skp, .tif  

#### Can export  

.avi, .dgn, .dwf, .dwg, .dxf, .fbx, .ifc, .jpg, .pdf, .png, .sat, .tif  

#### Preferred terminology in description  

lorem ipsum  

<a name="3ds"></a>  
## 3ds Max  

**Associated file extensions:** .3ds, .max  
**Vendor:** Autodesk  

#### Summary  

3ds Max was first released as 3D Studio in 1990. Over the years, the name evolved from 3D Studio to 3D Studio Max (1996) to 3ds Max (2006). 3ds Max is a desktop application for 3D modeling, rendering, and animation used by the architectural, gaming, film, and animation industries. It can be used to, for example, create high-defintion renderings of projects designed in Revit.  

#### File types  

**3DS:** 3DS is a native binary file format for 3ds Max. Unlike MAX, 3DS is interoperable with other 3D modeling software programs.  
**MAX:** MAX is the native internal file format for 3ds Max.  

#### How to view files on CCA CAD workstations  

Both 3DS and MAX files can be opened in 3ds Max 2015.  

#### Can import  

3D Studio (.3DS)  
Adobe Illustrator (.AI)  
ASCII Scene Export (.ASE)  
Lightscape - Material (.ATR), Blocks (.BLK), Parameter (.DF), Layers (.LAY), Preparation (.LP), View (.VW)  
Autodesk DWF (.DWF)  
Autocad DWG (.DWG)  
Autocad DXF (.DXF)  
Autodesk FBX (.FBX, .DAE)  
Motion Analysis HTR File (.HTR)  
IGES (.IGS)  
JSR-184 (.M3G)  
Wavefront Object (.OBJ) and Material (.MTL)  
StereoLitho (.STL)  
Shockwave 3D (.W3D)  
VRML97 (.WRL)  

#### Can export  

3D Studio (.3DS, .PRJ)  
Adobe Illustrator (.AI)  
LandXML / DEM / DDF (.XML, .DEM, .DDF) Autocad Drawing (.DWG, .DXF)  
Legacy Autocad (.DWG)  
Autodesk FBX (.FBX, .DAE)  
Motion Analysis HTR File (.HTR)  
IGES (.IGE,.IGS,.IGES)  
Autodesk Inventor (.IPT, .IAM)  
Lightscape (.LS, .LP, .VW)  
Wavefront Object (.OBJ) and Material (.MTL) 3D Studio Shape (.SHP)  
StereoLitho (.STL)  
Motion Analysis TRC File (.TRC) VRML (.WRL, WRZ)  
VIZ Material XML (.XML)  

#### Features of note  

lorem ipsum  

#### Preferred terminology in description  

lorem ipsum  

<a name="rhino"></a>  
## Rhinoceros  

**Associated file extensions:** .3dm  
**Vendor:** Robert McNeel & Associates  

#### Summary  

Rhinoceros (most commonly referred to as Rhino) is a NURBS-based 3D design tool for Windows and Mac OS X, first released in 1998 and commonly used for computer-aided design, manufacturing, 3D printing, and multimedia work. Rhino's wide appeal can be attributed in part to the Grasshopper visual scripting add-on, V-Ray rendering plug-in, and other such plug-ins that can expand Rhino's native feature set.  

#### How to view files on CCA CAD workstations  

Open files in Rhinoceros 5.  

#### Features of note  

Rhino's 3DM file format has been openly documented as part of Robert McNeel & Associates' openNURBS Initiative, and can be read and written by the open-source openNURBS toolkit.  

When opening CAD file formats not in Rhino native file format, the program will always create a new drawing called "Untitled" and convert the file, meaning that for the file to remain in its old file format it must be re-converted to its original format.  

Although Rhino can import DWG files, it may not always be able to read the newest versions of this format. This delay can be attributed to the time it takes to reverse-engineer new versions of the DWG format after they are released by Autodesk. Rhino 5 can import and export DWG/DXF file formats up to version 2014.  

In the absence of full-licensed Microstation, Rhino is the best tool available for importing DGNs for export into other formats for use in, e.g., e-publications.  

#### Can import/export  

DWG/DXF (up to version 2014), IGES, STEP, SLDPRT, SAT, DGN, FBX, 3DS, LWO, STL, SLC, OBJ, AI, RIB, POV, UDO, VRML, CSV, BMP, TGA, TIFF, VDA, GHS, GTS, KML, PLY, SketchUp  

Other formats may be supported via third-party plugins.  

#### Preferred terminology in description  

lorem ipsum  

<a name="microstation"></a>  
## Microstation  

**Associated file extensions:** .dgn  
**Vendor:** Bentley Systems  

#### Summary  

lorem ipsum  

#### How to view files on CCA CAD workstations  

lorem ipsum  

#### Features of note  

lorem ipsum  

#### Preferred terminology in description  

lorem ipsum  

<a name="maya"></a>  
## Maya   

**Associated file extensions:** .ma, .mb  
**Vendor:** Autodesk (originally Alias)  

#### Summary  

lorem ipsum  

#### How to view files on CCA CAD workstations  

lorem ipsum  

#### Features of note  

lorem ipsum  

#### Preferred terminology in description  

lorem ipsum  

<a name="alias"></a>  
## Alias  

**Associated file extensions:** .wire  
**Vendor:** Autodesk (originally Alias)  

#### Summary  

lorem ipsum  

#### How to view files on CCA CAD workstations  

lorem ipsum  

#### Features of note  

lorem ipsum  

#### Preferred terminology in description  

lorem ipsum  

<a name="formz"></a>  
## form-Z   

**Associated file extensions:** .fmz  
**Vendor:** AutoDesSys  

#### Summary  

lorem ipsum  

#### How to view files on CCA CAD workstations  

lorem ipsum  

#### Features of note  

lorem ipsum  

#### Preferred terminology in description  

lorem ipsum  

<a name="catia"></a>  
## CATIA   

**Associated file extensions:** .CATPart, .CATProduct, others  
**Vendor:** Dassault Systèmes  

#### Summary  

lorem ipsum  

#### How to view files on CCA CAD workstations  

lorem ipsum  

#### Features of note  

lorem ipsum  

#### Preferred terminology in description  

lorem ipsum  

<a name="digitalproject"></a>  
## Digital Project   

**Associated file extensions:** .CATPart, .CATProduct  
**Vendor:** Gehry Technologies  

#### Summary  

lorem ipsum  

#### How to view files on CCA CAD workstations  

lorem ipsum  

#### Features of note  

lorem ipsum  

#### Preferred terminology in description  

lorem ipsum  

<a name="solidworks"></a>  
## SOLIDWORKS   

**Associated file extensions:** .SLDPRT  
**Vendor:** Dassault Systèmes   

#### Summary  

lorem ipsum  

#### How to view files on CCA CAD workstations  

lorem ipsum  

#### Features of note  

lorem ipsum  

#### Preferred terminology in description  

lorem ipsum  

<a name="sketchup"></a>  
## Sketchup  

**Associated file extensions:** .skp  
**Vendor:** Trimble Navigation (originally Google)  

#### Summary  

lorem ipsum  

#### How to view files on CCA CAD workstations  

lorem ipsum  

#### Features of note  

lorem ipsum  

#### Preferred terminology in description  

lorem ipsum  

<a name="stl"></a>  
## STL   

**Associated file extensions:** .stl  
**Vendor:** Non-vendor specific 

#### Summary  

lorem ipsum  

#### How to view files on CCA CAD workstations  

lorem ipsum  

#### Features of note  

lorem ipsum  

#### Preferred terminology in description  

lorem ipsum  

<a name="iges"></a>  
## IGES  

**Associated file extensions:** .iges, .igs  
**Vendor:** Non-vendor specific 

#### Summary  

lorem ipsum  

#### How to view files on CCA CAD workstations  

lorem ipsum  

#### Features of note  

lorem ipsum  

#### Preferred terminology in description  

lorem ipsum  

<a name="step"></a>  
## STEP  

**Associated file extensions:** .iges  
**Vendor:** Non-vendor specific 

#### Summary  

lorem ipsum  

#### How to view files on CCA CAD workstations  

lorem ipsum  

#### Features of note  

lorem ipsum  

#### Preferred terminology in description  

lorem ipsum  

<a name="step"></a>  
## COLLADA  

**Associated file extensions:** .dae  
**Vendor:** Non-vendor specific 

#### Summary  

lorem ipsum  

#### How to view files on CCA CAD workstations  

lorem ipsum  

#### Features of note  

lorem ipsum  

#### Preferred terminology in description  

lorem ipsum  

<a name="step"></a>  
## IFC  

**Associated file extensions:** .ifc  
**Vendor:** Non-vendor specific 

#### Summary  

lorem ipsum  

#### How to view files on CCA CAD workstations  

lorem ipsum  

#### Features of note  

lorem ipsum  

#### Preferred terminology in description  

lorem ipsum  
