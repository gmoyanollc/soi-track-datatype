[![Join the chat at https://gitter.im/soi-track-datatype/Lobby](https://badges.gitter.im/soi-track-datatype/Lobby.svg)](https://gitter.im/soi-track-datatype/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

#SOI Track Datatype 2.0 is now TSOA Track 2.0
SOI Track Datatype 2.0 development has halted and transitioned to TSOA Track 2.0 development.  A change in course took place for strict NIEM-conformance with a new data model initiatied by [Georgia Tech Research Institute (GTRI)](https://gtri.gatech.edu/), in coordination with managers of the [NIEM MilOps Domain](https://www.niem.gov/communities/MilOps/Pages/MilOps.aspx).

##NIEM-Conformance
The [National Information Exchange Model (NIEM)](https://www.niem.gov/aboutniem) components that primarily guide the NIEM-conformance of a data exchange data model product are the following:

  * [Naming and Design Rules (NDR)](https://reference.niem.gov/niem/specification/naming-and-design-rules/3.0/niem-ndr-3.0.html) and 
  
  * [Model Package Description (MPD)](http://reference.niem.gov/niem/specification/model-package-description/3.0/model-package-description-3.0.html).
  
###SOI Track Datatype 2.0 NIEM-Conformance Issue
Deviations from NIEM NDR guidance were deemed unacceptable, regardless of any perceived benefit.  SOI Track Datatype 2.0 development took the following notable deviations from NIEM NDR guidance:

  1. [W3C Resource Description Framework (RDF)](https://en.wikipedia.org/wiki/Resource_Description_Framework) modeling is asserted by [W3C RDF with Attributes (RDFa)](https://en.wikipedia.org/wiki/RDFa) data components rather than described by contextual definitions and representations expressed as XML elements.
  
  2. Associations between data components may be asserted by RDFa data components rather than physically associating dependent objects at design-time and contextualizing definitions and representations expressed as XML elements.  

####Deviation Backdrop
The backdrop for taking the initial development deviations are the following:

  1. A demand for simple data sets.  The paper [Simple, Agile Data Sets](./src/main/resources/documentation/simple-agile-data-sets.md) positions this approach for SOI Track Datatype 2.0 from lessons learned over a decade ago.
  
  2. A flatter message format that is lighter and simplifies processing.  The document [Data Model Design](./src/main/resources/documentation/data-model-design.md) describes a design whereby relationships between objects are set at run-time using RDFa.  

##Authoritative Sources
The authoritative and complete work is maintained on Software Forge.mil Project [USMC - MAGTF C2](https://software.forge.mil/sf/projects/magtf_c2).

###TSOA Track 2.0 
The development artifacts for NIEM-conformant TSOA Track 2.0 are located at Source Code repository *soi-messaging.git/tsoa-track*.  The Git repository address is `https://gmoyano@svn.forge.mil/gerrit/p/soi-messaging` .

###SOI Track Datatype 2.0
The initial development artifacts for SOI Track Datatype 2.0, which deviates from NIEM NDR guidance, are located at Source Code repository [SoiMessaging/TsoaInformationModel/DataFormat/soi-track-datatype](https://svn.forge.mil/svn/repos/soimessaging/TsoaInformationModel/DataFormat/soi-track-datatype). 

A subset of this work, primarily documentation, is on GitHub at [gmoyanollc/soi-track-datatype](https://github.com/gmoyanollc/soi-track-datatype).

  
  
