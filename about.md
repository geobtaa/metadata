# About GeoBlacklight Metadata

## The GeoBlacklight Schema (Aardvark)
- The primary metadata record for each resource uses the official GeoBlacklight schema, currently versioned as 'Aardvark'. 
- This lightweight schema was designed specifically for the GeoBlacklight application and is geared towards discoverability. 
- [The schema is documented on the OpenGeoMetadata project](https://opengeometadata.github.io/aardvark/aardvarkMetadata.html).


## B1G Project Specific Features of the Aardvark for GeoBlacklight Schema
- The B1G profile of the GeoBlacklight Schema adds 9 custom elements to Aardvark
- [The B1G custom elements are documented here](b1gProfile.html)


## Supplemental Metadata
All other forms of metadata, such as ISO 19139, FGDC Content Standard for Digital Geospatial Metadata, attribute table definitions, or custom schemas are treated as Supplemental Metadata.
- Supplemental Metadata is not usually edited directly for inclusion in the project.
- If this metadata is available as XML or HTML, it can be added as a hosted link for the Metadata preview tool in GeoBlacklight.
- XML or HTML files can be parsed to extract metadata that forms the basis for the item’s GeoBlacklight schema record.
- The file formats that can be viewed within the geoportal application include:
    - ISO 19139 XML
    - FGDC XML
    - MODS XML
    - HTML (any standard)

