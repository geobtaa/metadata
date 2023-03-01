The BTAA Geoportal holds metadata records that point to geospatial data, maps, aerial imagery, web services, and websites hosted online by external organizations. These records can be submitted directly using the [GeoBTAA Metadata Template](https://z.umn.edu/b1g-template) or the metadata can be harvested via parsing scripts.

### Spreadsheets (direct submission)

Administrators for university repositories for scanned maps or data can often export metadata into a spreadsheet, especially for Dublin Core. This method is preferred, because the University IT professionals and librarians can control which fields to export, and because transformations by the Metadata Coordinator are not necessary. The [GeoBTAA Metadata Template](https://z.umn.edu/b1g-template) shows all of the fields needed for GeoBlacklight.


### API Harvesting or HTML Parsing

Most data portals have APIs or HTML structures that can be programmatically parsed to obtain metadata for each record.

* **DCAT** enabled portals: ArcGIS Open Data Portals (HUB), Socrata portals, and some others share metadata in the [DCAT standard](https://www.w3.org/TR/vocab-dcat/).

* **CKAN / DKAN** portals: This application uses a custom metadata schema for their API.

* **HTML** Parsing: If a data portal or website does not have an API, we may be able to parse the HTML pages to obtain the metadata needed to create GeoBlacklight schema records. This is done using custom [View our harvesting scripts for HTML parsing here.](https://github.com/geobtaa/workflows/tree/main/harvesting/parse-html)

* **OAI-PMH**: The [Open Archives Initiative Protocol for Metadata Harvesting (OAI-PMH)](https://www.openarchives.org/pmh/) is a framework that can be used to harvest metadata records from enabled repositories. The records are usually available as a simple Dublin Core XML format. If the protocol is not set up to include extra fields, such as the map image's download link or bounding box, this method may not be sufficient on its own. 


### Individual Metadata files

Geospatial metadata standards are expressed in the XML format, which can be parsed to extract metadata needed to create GeoBlacklight schema records. 
The following file types are accepted for metadata extraction and can serve as Supplemental Metadata:

* **ISO 19139 XML and FGDC XML files**: They are parsed to extract metadata values for GeoBlacklight metadata using the project created Python scripts found in [BTAA-Geospatial-Data-Project/parse-xml](https://github.com/BTAA-Geospatial-Data-Project/parse-xml)

* **ArcGIS 1.0 Metadata XML files**: These records are transformed to ISO 19139 using XSLT. They are then treated the same as the ISO as described above.\

* **MARC files**
The best way to transfer this type of metadata is to send a single file containing multiple records in the .MRC or MARC XML format. The Metadata Coordinator will use MarcEdit or XML parsing to transform the records to GeoBlacklight using the project-designated MARC to GBL crosswalk, but Team Members can specify preferences.

