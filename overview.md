## Metadata Schemas

### The GeoBlacklight Schema
The primary metadata record for each resource is in the GeoBlacklight schema. This lightweight schema was designed specifically for the GeoBlacklight application and is geared towards discoverability. [The schema is documented on the OpenGeoMetadata project](https://opengeometadata.github.io/aardvark/aardvarkMetadata.html).

**General Features of the GeoBlacklight Schema**
- Lightweight schema primarily for discovery of resources
- Based upon and shares most of its elements with [Dublin Core](http://dublincore.org/documents/dcmi-terms/)
- Includes a few elements from other schemas or custom fields
- Published as a JSON document

**B1G Project Specific Features of the GeoBlacklight Schema**
- The B1G profile of the GeoBlacklight Schema includes nine custom elements specific to our project’s implementation of GeoBlacklight
- Metadata records are stored and edited in a custom application, [GEOMG](https://github.com/BTAA-Geospatial-Data-Project/geomg)


### Supplemental Metadata
All other forms of metadata, such as ISO 19139, FGDC Content Standard for Digital Geospatial Metadata, attribute table definitions, or custom schemas are treated as Supplemental Metadata.
- Supplemental Metadata is not usually edited directly for inclusion in the project.
- If this metadata is available as XML or HTML, it can be added as a hosted link for the Metadata preview tool in GeoBlacklight.
- XML or HTML files can be parsed to extract metadata that forms the basis for the item’s GeoBlacklight schema record.
- Hosting: Supplemental metadata is generally harvested from external sites and hosted in the [project’s web server directory](http://btaagdp.org/metadata/). 
- The file formats that can be viewed within the geoportal application include:
    - ISO 19139 XML
    - FGDC XML
    - MODS XML
    - HTML (any standard)

