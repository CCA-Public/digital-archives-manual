# CAD, BIM, and 3D modeling software/file formats  

Vendor/software-specific formats:  

* [AutoCAD (.dwg, .dxf, .dwf)](#autocad)
* [Revit (.rvt)](#revit)
* [3DS Max (.3ds, .max)](#3ds)  
* [Rhinoceros (.3dm)](#rhino)  
* [Microstation (.dgn)](#microstation)  
* [Maya (.ma, .mb)](#maya)  
* [Alias (.wire)](#alias)
* [form·Z (.fmz)](#formz)  
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

**DXF (Drawing Interchange Format, or Drawing Exchange Format):** An open data transfer format developed by Autodesk, with [published specifications](http://images.autodesk.com/adsk/files/autocad_2012_pdf_dxf-reference_enu.pdf) available online. DXF exists in both ASCII and binary forms. ASCII DXF files are text files that can be read and modified with any text editor.  

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

#### Navigation and use 

In AutoCAD, an be interacted with through the Command terminal or through the graphical interface. Basic navigational functions (such as pan, zoom, and orbit) are mostly supported through the [Navigation Bar](https://knowledge.autodesk.com/support/autocad/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/AutoCAD-Core/files/GUID-17225A0F-7A50-41B9-8404-7D415518DEFB-htm.html).

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

#### Navigation and use    

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

#### Navigation and use 

There are many ways to view and navigate 3D space in 3ds Max. For a good introduction, see [this guide](https://knowledge.autodesk.com/support/3ds-max/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/3DSMax/files/GUID-CDA67D65-73D5-4F91-9378-D00B85ED6898-htm.html).  

The easiest way to navigate a 3D file in 3ds Max is likely through the [ViewCube](https://knowledge.autodesk.com/support/3ds-max/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/3DSMax/files/GUID-F8D9EF38-A2BB-4502-95A7-4897A7F30F21-htm.html).  

<a name="rhino"></a>  
## Rhinoceros  

**Associated file extensions:** .3dm  
**Vendor:** Robert McNeel & Associates  

#### Summary  

Rhinoceros (most commonly referred to as Rhino) is a NURBS-based 3D design tool for Windows and Mac OS X, first released in 1998 and commonly used for computer-aided design, manufacturing, 3D printing, and multimedia work. Rhino's wide appeal can be attributed in part to its extensive library of plug-ins, such as Grasshopper (visual scripting) and V-Ray (rendering), that extend Rhino's native feature set.  

#### How to view files on CCA CAD workstations  

You can open .3dm (and many other) files in Rhinoceros 5.  

#### Features of note  

Rhino's 3DM file format has been openly documented as part of Robert McNeel & Associates' openNURBS Initiative, and can be read and written by the open-source openNURBS toolkit.  

When opening CAD file formats not in Rhino native file format, the program will always create a new drawing called "Untitled" and convert the file, meaning that for the file to remain in its old file format it must be re-converted to its original format.  

Although Rhino can import DWG files, it may not always be able to read the newest versions of this format. This delay can be attributed to the time it takes to reverse-engineer new versions of the DWG format after they are released by Autodesk. Rhino 5 can import and export DWG/DXF file formats up to version 2014.  

In the absence of full-licensed Microstation, Rhino is the best tool available for importing DGNs for export into other formats for use in, e.g., e-publications.  

#### Can import/export  

DWG/DXF (up to version 2014), IGES, STEP, SLDPRT, SAT, DGN, FBX, 3DS, LWO, STL, SLC, OBJ, AI, RIB, POV, UDO, VRML, CSV, BMP, TGA, TIFF, VDA, GHS, GTS, KML, PLY, SketchUp  

Other formats may be supported via third-party plugins.  

#### Navigation and use  

Start familiarizing yourself with Rhino 5's navigational features by watching [this short video](https://vimeo.com/58212839).  

In perspective view:

* **Rotate**: Right mouse button + drag  
* **Pan**: Shift + right mouse button + drag  
* **Zoom**: Ctrl + right mouse button + drag OR scroll wheel  
  
In ortho views (top, front, right):  

* **Pan**: Right mouse button + drag  
* **Zoom**: Ctrl + right mouse button + drag OR scroll wheel  

Be aware that elements of a 3D model may exist in layers that are not turned on at the time the file is opened.  To manage layers, go to the "Layers" tab on the right-hand side of the screen. Click the light bulb icon to turn layers on and off.  

<a name="microstation"></a>  
## Microstation  

**Associated file extensions:** .dgn  
**Vendor:** Bentley Systems  

#### Summary  

Microstation is a 2D and 3D CAD software product developed and sold by Bentley Systems, first released in 1985. Microstation is commonly used for infrastructural projects. Its largest user base in the UK. The current version of Microstation as of April 2016 is Microstation V8i.  

#### How to view files on CCA CAD workstations  

Although CCA does not have a fully-licensed version of Microstation, DGN files can be viewed read-only in the free Bentley View software installed on our CAD workstations. DGN files can also be imported (and subsequently re-exported in other formats) in Rhino 5.  

#### Features of note  

Although Microstation historically offered Mac and UNIX versions of its software projects, Microstation is now a Windows-only product.  

<a name="maya"></a>  
## Maya   

**Associated file extensions:** .ma, .mb  
**Vendor:** Autodesk (originally Alias)  

#### Summary  

Maya is an application used to generate 3D assets for use in film, television, game development and architecture. The software was initially developed by Alias Systems (later Alias|Wavefront, which was owned by Silicon Graphics Inc.) and released for the IRIX operating system in February 1998. However, this support was discontinued in August 2006 after the release of version 6.5. Maya was available in both "Complete" and "Unlimited" editions until August 2008, when it was turned into a single suite.  

Users define a virtual workspace (scene) to implement and edit media of a particular project. Scenes can be saved in a variety of formats, the default being .mb (Maya Binary). Maya exposes a node graph architecture. Scene elements are node-based, each node having its own attributes and customization. As a result, the visual representation of a scene is based entirely on a network of interconnecting nodes, depending on each other's information. For the convenience of viewing these networks, there is a dependency and a directed acyclic graph.  

Maya continues to be used in Windows and Mac OS X for many major film, gaming, and architectural projects.  

#### File types  

**MA**: Maya ASCII (text-based format)  
**MB**: Maya Binary (compressed, binary format)  

#### How to view files on CCA CAD workstations  

You can open .ma and .mb files in Autodesk Maya 2014.   

#### Features of note  

The Maya ASCII file format has changed as of Maya 2013. This breaks backwards compatibility, particularly when the .ma file includes meshes.   

#### Navigation and use  

In Maya 2014:  

**Pan**: Alt + middle mouse button  
**Rotate**: Alt + left mouse button  
**Zoom**: Alt + right mouse button  

For more information, see [this tutorial on Viewport navigation in Maya](http://www.worldofleveldesign.com/categories/3d_modeling/maya-tutorial-for-beginners-04-viewport-navigation.php).  

<a name="alias"></a>  
## Alias  

**Associated file extensions:** .wire  
**Vendor:** Autodesk (originally Alias)  

#### Summary  

Can refer to either Alias Studio, etc. (set of industrial design tools) or PowerAnimator (3D modeling, animation, and visual effects suite that was the precursor to Maya).   

#### How to view files on CCA CAD workstations  

lorem ipsum  

#### Features of note  

lorem ipsum  

#### Navigation and use  

lorem ipsum  

<a name="formz"></a>  
## form·Z   

**Associated file extensions:** .fmz  
**Vendor:** AutoDesSys  

#### Summary  

Form·Z is a computer-aided (CAD) design tool developed by AutoDesSys for all design fields that deal with the articulation of 3D spaces and forms and which is used for 3D modeling, drafting, animation and rendering.  

In general, form·Z allows design in 3D or in 2D, using numeric or interactive graphic input through either line or smooth shaded drawings (OpenGL)among drafting, modeling, rendering, and animation platforms.  

#### How to view files on CCA CAD workstations  

CCA has two versions of form·Z installed on its CAD workstations: form·Z 8 Pro and form·Z 6.73. form·Z 8 Pro will be able to open only relatively new form·Z files or files that have been migrated to the newest version of the .fmz format. form·Z 6.73 will be able to read some (but still not all) older .fmz files, making it the de facto choice for attempting to open .fmz files in the archives.  

It may be that neither of the versions of form·Z on the CAD workstations are able to open files in an archive. If this is the case, please notify the Digital Archivist, so that we can explore options for gaining access to the files in question.  

#### Features of note  

Form·Z is notoriously not backwards-compatible. Newer versions of the software are unable to open files created in older version of form·Z.  

#### Navigation and use    

See the following resources:  

* [View navigation and control](http://www.formz.com/manuals/formz7/!SSL!/WebHelp/01020_View_navigation_and_control.html)  
* [form·Z video: Navigation](https://www.youtube.com/watch?v=x0ipLHhbZjY)  

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

#### Navigation and use    

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

#### Navigation and use    

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

#### Navigation and use    

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

#### Navigation and use    

lorem ipsum  

<a name="stl"></a>  
## STL   

**Associated file extensions:** .stl  
**Vendor:** Non-vendor specific 

#### Summary  

STL is a vendor-neutral file format most typically used for 3D printing and computer-aided manufacturing (CAM). There are ASCII and binary variants of the STL format. 

#### How to view files on CCA CAD workstations  

STL file are best viewed in Rhino.  

#### Features of note  

STL files only contain information on surface geometry. See the [STL wikipedia page](https://en.wikipedia.org/wiki/STL_(file_format)) for more detailed information.  

<a name="iges"></a>  
## IGES  

**Associated file extensions:** .iges, .igs  
**Vendor:** Non-vendor specific 

#### Summary  

IGES, or the Initial Graphics Exchange Specification, is a vendor-neutral, lightweight CAD format for the exchange of geometric data. It is an ASCII – meaning ASCII-encoded, text-based format. In practical terms, this means that you can open IGES files in a text editor to explore their content and even make changes to models.

IGES was published in 1980 and is supported as an import/export format in most CAD products. Although ubiquitous, its main drawback is that IGES files cannot contain anything more than basic geometric information. It’s for this reason that the last published version of the IGES format happened in 1996, right around the same time that STEP was gaining popularity.

#### How to view files on CCA CAD workstations  

IGES files can be viewed from most CAD programs. Because not all software complies precisely with the IGES standard, it is advised to open files in software as close as possible to the software that created the file, if known.

<a name="step"></a>  
## STEP  

**Associated file extensions:** .iges  
**Vendor:** Non-vendor specific 

#### Summary  

STEP, or Standard for the Exchange of Product Model Data, is an ISO format started in 1984 as a more fully-featured and rigorously defined replacement for existing standards such as IGES. Development has continued since, with elements of the standard being published throughout the 1990s and 2000s.

A number of more specific file formats have been specified under the STEP standard, allow of which are collectively referred to as STEP files. The most common implementations of STEP are AP203; AP214, which extends on AP203 with support for information such as layers; and AP242, a more heavy-weight format intended for use in the manufacturing and aerospace industries.

Although converting most proprietary CAD models to STEP does imply some degree of data loss (such as parametric data), STEP is the closest thing to a full-featured vendor-neutral exchange format for CAD files, and has often been floated as a potential preservation format. Many CAD products now support STEP importers and exporters, in part due to the efforts of groups such as the CAx Implementors Forum, which have helped to develop these tools.
 
#### How to view files on CCA CAD workstations  

STEP files can be opened in a number of CAD programs. Due to the possibility that the originated software may not comply precisely with the STEP standard, it is advised to open files in software as close as possible to the software that created the file, if known.

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
