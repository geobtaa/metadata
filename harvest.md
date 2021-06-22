layout: page
title: "Harvest & Transition"
permalink: /harvest.md/


2\. METADATA HARVEST & TRANSITION
=======================

This stage involves batch processing of the records, including harvesting, transformations, crosswalking information. This stage is carried out by the Metadata Coordinator, who may contact Task Force members for assistance.

Regardless of the method used for acquiring the metadata, it is always transformed into a spreadsheet for editing. These spreadsheets are stored in Google Drive. 

Once the records have been harvested, the activity is recorded as an "Accession" in the Collections Management Database on the Actions Tab.

Because of the variety of platforms and standards, this process can take many forms. The Metadata Coordinator will contact Task Force members if they need to supply metadata directly. Here are the most common methods per resource type:

Geospatial data
---------------

### API harvesting

-   Most data portals have APIs that can be programmatically parsed to obtain metadata for each record. 

-   DCAT enabled portals: ArcGIS Open Data Portals (HUB), Socrata portals, and some others share metadata in the [DCAT standard.](https://www.w3.org/TR/vocab-dcat/) This is typically accessed by appending "/data.json" to the end of the portal's base URL. Our project created Python scripts to harvest from these portals that are stored in the GitHub Repository [BTAA-Geospatial-Data-Project](https://github.com/BTAA-Geospatial-Data-Project)/[dcat-metadata](https://github.com/BTAA-Geospatial-Data-Project/dcat-metadata) 

-   CKAN / DKAN portals: This application uses a custom metadata schema for their API. Our project uses the Python scripts found in the BTAA fork of the CKAN project at [BTAA-Geospatial-Data-Project](https://github.com/BTAA-Geospatial-Data-Project)/[ckanapi-exporter.](https://github.com/BTAA-Geospatial-Data-Project/ckanapi-exporter)

### HTML parsing

-   If a data portal or website does not have an API, we may be able to parse the HTML pages to obtain the metadata needed to create GeoBlacklight schema records. 

-   This is done using the project created Python scripts found in [BTAA-Geospatial-Data-Project](https://github.com/BTAA-Geospatial-Data-Project)/[parse-html](https://github.com/BTAA-Geospatial-Data-Project/parse-html).

### Individual Geospatial Metadata Standard files

-   Geospatial metadata standards are expressed in the XML format, which can be parsed to extract metadata needed to create GeoBlacklight schema records. 

-   The following file types are accepted for metadata extraction and can serve as Supplemental Metadata:

-   ISO 19139 XML and FGDC XML files: These records are uploaded to our project's [project's web server directory](http://btaagdp.org/metadata/). They are next parsed to extract metadata values for GeoBlacklight metadata using the project created Python scripts found in [BTAA-Geospatial-Data-Project](https://github.com/BTAA-Geospatial-Data-Project)/[parse-xml](https://github.com/BTAA-Geospatial-Data-Project/parse-xml)

-   ArcGIS 1.0 Metadata XML files: These records are transformed to ISO 19139 using XSLT. They are then treated the same as the ISO as described above.

### Downloading data

-   Some metadata is only available as part of a zipped download of the datasets. 

-   In this case, the Metadata Coordinator will use scripts to batch download the records, unzip them, and process their metadata.

Maps
----

### OAI-PMH

-   The [Open Archives Initiative Protocol for Metadata Harvesting (OAI-PMH)](https://www.openarchives.org/pmh/) is a framework that can be used to harvest metadata records from enabled repositories.

-   The records are usually available as a simple Dublin Core XML format. 

-   If the protocol is not set up to include extra fields, such as the map image's download link or bounding box, this method may not be sufficient on its own. 

### Spreadsheets

-   Administrators for university repositories for scanned maps or data can often export metadata into a spreadsheet, especially for Dublin Core. 

-   This method is preferred, because the University IT professionals and librarians can control which fields to export, and because transformations by the Metadata Coordinator are not necessary.

### MARC files

-   The best way to transfer this type of metadata is to send a single file containing multiple records in the .MRC or MARC XML format. 

-   The Metadata Coordinator will use MarcEdit to transform the records to GeoBlacklight using the project-designated MARC to GBL crosswalk, but Task Force members can specify preferences.
