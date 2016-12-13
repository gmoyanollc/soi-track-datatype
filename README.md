#SOI Track Datatype 2.x

[![Join the chat at https://gitter.im/soi-track-datatype/Lobby](https://badges.gitter.im/soi-track-datatype/Lobby.svg)](https://gitter.im/soi-track-datatype/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
SOI Track is a data type that represents concepts related to tracks, or more specifically, observation acts.

An observation act is an observation "associated with a discrete time instant or period through which results are assigned" to a thing-of-interest. The results are obtained by "a specified procedure, such as a sensor, instrument, algorithm or process chain" [OGC and ISO 19156:2011(E), [Observations and Measurements](https://en.wikipedia.org/wiki/Observations_and_Measurements)].  For example, `a military unit's location at discrete time intervals is observed by a platform sensor`.

##NIEM
SOI Track Datatype 2.x meets the [National Information Exchange Model (NIEM)](https://www.niem.gov/aboutniem) [Naming and Design Rules 3.0 (NDR)](https://reference.niem.gov/niem/specification/naming-and-design-rules/3.0/niem-ndr-3.0.html) Schematron conformance rules and generally follows its guidelines.

The following are notable deviations from NIEM NDR guidance:

  1. [Resource Description Framework (RDF)](https://en.wikipedia.org/wiki/Resource_Description_Framework) modeling is asserted by W3C  [RDF with Attributes (RDFa)] data components rather than described by contextual definitions and representations expressed as XML elements.
  
  2. Associations between data components may be asserted by RDFa data components rather than references described by contextual definitions and representations expressed as XML elements.

SOI Track Datatype 2.x also follows guidance provided by the NIEM [Model Package Description (MPD)](http://reference.niem.gov/niem/specification/model-package-description/3.0/model-package-description-3.0.html#appendix_E) specification for documenting and packaging artifacts.

##[Data model design](./src/main/resources/documentation/data-model-design.md)

##Authoritative Sources
The authoritative and complete work is maintained on Software Forge.mil at Project [USMC - MAGTF C2](https://software.forge.mil/sf/projects/magtf_c2) Source Code repository [SoiMessaging/TsoaInformationModel/DataFormat/soi-track-datatype](https://svn.forge.mil/svn/repos/soimessaging/TsoaInformationModel/DataFormat/soi-track-datatype). 

A subset of this work, primarily documentation, is on GitHub at [gmoyanollc/soi-track-datatype](https://github.com/gmoyanollc/soi-track-datatype).

  
  
