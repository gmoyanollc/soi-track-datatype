#Simple, Agile Data Sets
A service-oriented messaging data model should support the communication of simple, agile data sets.  This is evidenced, in part, by the popularity of [JSON](https://en.wikipedia.org/wiki/JSON), which during the last 5 years has become the de-facto standard text format for marshaling data between software components.  

Why has JSON supplanted XML?  One reason is that JSON is intentionally simpler, focused, and more flexible ["XML is toast, long live JSON"](http://www.cio.com/article/3082084/web-development/xml-is-toast-long-live-json.html).  

In 2005, as Google's VP of Product Management, XML and web pioneer [Adam Bosworth](https://en.wikipedia.org/wiki/Adam_Bosworth) highlighted "unintuitive lessons" in his article ["Learning from THE WEB"](http://queue.acm.org/detail.cfm?id=1103833).  The article takes place after an era of rigid, centralized systems with restrictive messaging contracts, at a point in time when new messaging paradigms were needed to properly support service-oriented web architectures and various non-relational data-store types, such as, key-value, document, and network-graph. 
 
As a side note, Adam Boswell, prior to Google, was senior VP architect of BEA Framework Division after BEA System's had acquired Crossgain, the company he co-founded, whose product became BEA WebLogic Workshop.  Prior to BEA System's, Boswell was at Microsoft, where he at one point was the General Manager of the WebData group, a team that focused on defining and driving XML strategy.  During his tenure at Microsoft, Boswell also pioneered XML technology with contributions to W3C XML specifications development and lead the team that developed Microsoft Internet Explorer's "Trident" HTML browser engine.

In his article, Bosworth highlighted the "unintuitive lessons", and specifically applied them to XML and databases.  This was when XML dominated text format messaging and relational databases reigned supreme.  This is also about the same time JSON emerged as a text format for messaging.  In 2005, companies like Yahoo! began offering some of its web services in JSON format [Yahoo! JSON API](http://ajaxian.com/archives/yahoo-json-api), and in December 2006, Google started offering JSON feeds for its GData web protocol [Google Deprecates Their SOAP Search API]( http://radar.oreilly.com/2006/12/google-deprecates-their-soap-s.html)..

A key component of the "unintuitive lessons" learned is the need to represent and communicate simple sets of data.  For messaging data models this means the design should facilitate the construction and communication of simple data sets.  

Therefore, in consideration of JSON's ultimate success and learned lessons, service oriented messaging data models should facilitate the communication of simple, agile data sets.  Complex, deep data structures and rigid rules should be avoided by data models, regardless of their text format representation.

An example of how a data model may support simple, agile data sets is introduced in the following section with a conceptual data model called "Track-Datatype-2.0".

#Track-Datatype-2.0 Data Model
The Track-Datatype-2.0 data model is a conceptual datatype for [observation acts [OGC and ISO 19156:2011(E)](https://portal.opengeospatial.org/files/?artifact_id=41579).  An observation act is also known as a “track” in certain domains.  

The Track-Datatype-2.0 data model describes data structures for object identity, association, and contextual meaning.  These data structures are foundational for representing simple data sets. 

##Identity, Association, and Contextual Meaning
The Track-Datatype-2.0 data model includes data structures for object identity, association, and contextual meaning.  These data structures support [Uniform Resource Identifier (URI)](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier) formatted values that are assigned at run-time.  The run-time values may uniquely identify an object, establish its relationship to other data objects, local or remote, and represent its contextual meaning in that specific instance. 

For example, the following tree diagram represents a conceptual Track-Datatype-2.0 Track message with an object called "PositionCollection".  This data set contains several geospatial position data objects with observation results.  URL values represent unique object identifiers and establish relationships to dependent remote objects: 
```
  Track
    |
    `-- PositionCollection (id="PositionCollection/01" 
          |   rdfa:about="MilitaryUnit/01" rdfa:rel="bySensor" rdfa:href="Sensor/01")
          |
          `-- PositionEclipse (id="PositionCollection/01/PositionEclipse/01")
          |
          `-- PositionEclipse (id="PositionCollection/01/PositionEclipse/02")
          |
          `-- PositionEclipse (id="PositionCollection/01/PositionEclipse/03")
```
The URL data structures `rdfa:about`, `rdfa:rel` and `rdfa:href` are set at run-time and establish relationships between observation results, in this case, `id="PositionCollection/01"`, and that which was observed, `rdfa:about="MilitaryUnit/01"`.  That which has observed, `rdfa:href="Sensor/01"`, is also associated at run-time.  The run-time assignments allow messages to reference data set objects contained in a message instance or those contained in other instances.

The following depicts the logical relationship of geospatial position objects and a military unit object:

```
                      /-------------------\
                      |  MilitaryUnit/01  |
                      \-------------------/
                                ^
                                |
                   /-------------------------\
                   |  PositionCollection/01  |
                   \-------------------------/
                        ^       ^       ^ 
                        |       |       |
                       /        |        \ 
                      /         |         \ 
                     /          |          \
                    /           |           \
                   /            |            \
                  |             |             |
   /----------------\  /----------------\  /----------------\
   |  ..Eclipse/01  |  |  ..Eclipse/02  |  |  ..Eclipse/03  |
   \----------------/  \----------------/  \----------------/
```
The association of objects at run-time provides a means for use-cases that are best served by the communication and processing of geospatial position data, which tends to be fresh and active, separately from organizational data, which is often stale and lazy.  For example, discrete specialized sensors may primarily communicate observation results.  Because of this specialization, characteristics about the observed military unit, such as affiliation and force capability, need to be obtained from other authoritative data sources.  

In contrast, consider data models that describe complex concepts by physically associating dependent objects at design-time.  An example is today's TSOA SOI TrackInfo data model.    

The following tree diagram represents an example instance of today's TSOA SOI TrackInfo message:  
```
  TrackInfo
    |
    `-- Track (type=Unit")
    |     |
    |     `-- TrackType="Unit"
    |     |
    |     `-- Identifiers
    |           |
    |           `-- GUID="CBR01 10MAR"
    |           |
    |           `-- NickName="2235868"
    |
    `-- Event
    |     |
    |     `-- DTG="2014-10-03T11:41:03-04:00"
    |     |
    |     `-- Location
    |           |
    |           `-- Position
    |
    `-- Event
    |     |
    |     `-- DTG="2014-10-03T11:42:03-04:00"
    |     |
    |     `-- Location
    |           |
    |           `-- Position
    |
    `-- Event
          |
          `-- DTG="2014-10-03T11:43:03-04:00"
          |
          `-- Location
                |
                `-- Position                
```  
A valid TrackInfo message requires both a Track object, that which is observed, and at least one Event object, an observation result.  This design-time association is rigid for certain use-cases because both objects must be included in a message instance and communicated at the same time.    

#Conclusion
A service oriented messaging data model should address lessons learned after an era of rigid, centralized systems and the dawn of service-oriented web architectures and various non-relational data-store types.  A key component of the lessons learned is to facilitate the communication of simple, agile data sets.  This calls for messaging data models that avoid having complex, deep data structures and rigid rules, regardless of their text format representation.
 
