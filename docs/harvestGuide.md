!!! Warning "This guide is a work in progress (August 2022)"

## Harvesting Options

The BTAA Geoportal holds metadata records that point to geospatial data, maps, aerial imagery, web services, and websites hosted online by external organizations. This metadata is acquired by harvesting from the organization. Here are the most common harvesting methods:


**API Harvesting or HTML Parsing**

Most data portals have APIs or HTML structures that can be programmatically parsed to obtain metadata for each record.

* DCAT enabled portals: ArcGIS Open Data Portals (HUB), Socrata portals, and some others share metadata in the [DCAT standard](https://www.w3.org/TR/vocab-dcat/).

* CKAN / DKAN portals: This application uses a custom metadata schema for their API.

* HTML Parsing: If a data portal or website does not have an API, we may be able to parse the HTML pages to obtain the metadata needed to create GeoBlacklight schema records. This is done using custom [View our harvesting scripts for HTML parsing here.](https://github.com/geobtaa/workflows/tree/main/harvesting/parse-html)


**Individual Geospatial Metadata Standard files**

Geospatial metadata standards are expressed in the XML format, which can be parsed to extract metadata needed to create GeoBlacklight schema records. 
The following file types are accepted for metadata extraction and can serve as Supplemental Metadata:

* **ISO 19139 XML and FGDC XML files**: They are parsed to extract metadata values for GeoBlacklight metadata using the project created Python scripts found in [BTAA-Geospatial-Data-Project/parse-xml](https://github.com/BTAA-Geospatial-Data-Project/parse-xml)

* **ArcGIS 1.0 Metadata XML files**: These records are transformed to ISO 19139 using XSLT. They are then treated the same as the ISO as described above.

**Downloading Data**

Some metadata is only available as part of a zipped download of the datasets. In this case, UMN staff will use scripts to batch download the records, unzip them, and process their metadata locally.


**OAI-PMH**

The [Open Archives Initiative Protocol for Metadata Harvesting (OAI-PMH)](https://www.openarchives.org/pmh/) is a framework that can be used to harvest metadata records from enabled repositories. The records are usually available as a simple Dublin Core XML format. If the protocol is not set up to include extra fields, such as the map image's download link or bounding box, this method may not be sufficient on its own. 

**Spreadsheets**

Administrators for university repositories for scanned maps or data can often export metadata into a spreadsheet, especially for Dublin Core. This method is preferred, because the University IT professionals and librarians can control which fields to export, and because transformations by the Metadata Coordinator are not necessary. The [B1G Map Template](https://z.umn.edu/b1g-template) shows all of the fields needed for GeoBlacklight.

**MARC files**
The best way to transfer this type of metadata is to send a single file containing multiple records in the .MRC or MARC XML format. The Metadata Coordinator will use MarcEdit or XML parsing to transform the records to GeoBlacklight using the project-designated MARC to GBL crosswalk, but Team Members can specify preferences.



---

## DCAT Harvesting

DCAT stands for [Data Catalog](https://www.w3.org/TR/2020/REC-vocab-dcat-2-20200204/), which is a standard schema and vocabulary to organize datasets and data services. This is typically accessed by appending “/data.json” to the end of the portal’s base URL. [View our harvesting scripts for DCAT enabled portals here.](https://github.com/geobtaa/workflows/tree/main/harvesting/dcat)

We normally harvest the DCAT portals once a month to compare the JSON files with latest reaccession, add the new records into our geoportal, and also retire the deleted records as well. By saying records, we only want to harvest data types that are either **Datasets** or **Imagery**.


GitHub Repository: 

This [repository](https://github.com/geobtaa/dcat-metadata) stores up-to-date **harvest script** as well as the **basic portal information**. It also stores the **historic harvest data** and **harvest report** (without manual edits). Remember to pull down the latest repo to your local machine before regular reaccession. Here're some import files or folders:

- [arcPortals.csv](https://github.com/geobtaa/dcat-metadata/blob/main/arcPortals.csv) includes the details about each portal that will be used for metadata construction every time. 

- [harvest.py](https://github.com/geobtaa/dcat-metadata/blob/main/harvest.py) is written in Python and mainly does the following jobs:
    1. Request the JSON by portal and store them to local folder [jsons](https://github.com/geobtaa/dcat-metadata/tree/main/jsons)
    2. For each portal, compare the new JSON with the latest one from last reaccession, and output the new records as well as the deleted records. 
        - For new records, create the metadata by following the dcat metadata format and write into one CSV report called `allNewItems_yyyymmdd.csv` and store in the folder [reports](https://github.com/geobtaa/dcat-metadata/tree/main/reports). 
        - For deleted records, we only need to know their IDs rather the metadata, so that write all retired records' ID into one CSV called `allDeletedItems_yyyymmdd.csv` and store in [reports](https://github.com/geobtaa/dcat-metadata/tree/main/reports) as well.
    3. Test the download links from `allNewItems_yyyymmdd.csv` to check if valid. If it is valid, calculate and add the file size for this new record. Test again if it is not. Leave a message in the Title field for manual test later.
    4. Populate spatial coverage based on bounding box for each record in `allNewItems_yyyymmdd.csv`.
    5. Check duplicated records by same tile and bounding box, or same ID. If duplicates exist, leave a message in the Title field for manual delete later.

- [retired_items_GEOMG.ipynb](https://github.com/geobtaa/dcat-metadata/blob/main/retired_items_GEOMG.ipynb) is to retire the deleted records on GEOMG, change them to unpublished and set the retire date by Python script. 

There are still some manual work on harvest report, so that we need to upload them on [google drive](https://drive.google.com/drive/u/0/folders/1ERBc0LFQ2hbdrjOxHohFPTUEuFiywqtt) after creating a new folder for each harvest. Open the `allNewItems_yyyymmdd.csv` with google sheets and do following things:
1. Check whether there are message added in **Title** field. 
2. Check whether the auto-populated Title has the right format of `AlternativeTitle [titleSource] {year if it exists}`
3. Choose a proper [Theme](https://opengeometadata.org/docs/ogm-aardvark/theme#controlled-vocabulary) value for each record.



---
## CKAN Harvesting

[CKAN](http://docs.ckan.org/en/2.9/contents.html) (Comprehensive Knowledge Archive Network) is an open-source data management system (DMS) for powering data hubs and data portals. Different from DCAT, we cannot access the JSON data by adding the `/data.json` after the portal's URL. 

Instead, we need to request the **package URL** for each CKAN portal to get a JSON-formatted list of  **resource names**. By comparing with the latest reaccession, we find the new resource names, and deleted resource names. Then we use the resource name as an identifier to query this resource's metadata. 

Since datasets are not frequently updated on CKAN portals, we only perform reaccession once a quarter. CKAN uses the similar metadata template as DCAT does.


**GitHub Repository**

This [repository](https://github.com/geobtaa/workflows/tree/main/harvesting/ckan) stores the **harvest script**, **basic portal information**, **resource name list** by portal for each harvest, and the **harvest report** (without manual edits).

- [CKANportals.csv](https://github.com/geobtaa/workflows/tree/main/harvesting/ckan/CKANportals.csv) stores the basic portal information.

- [harvest.ipynb](https://github.com/geobtaa/workflows/blob/main/harvest.ipynb) is the harvest script written in Jupyter Notebook. It will request the resource name list for each portal, store in [resource](https://github.com/geobtaa/workflows/ckan/tree/main/resource) folder and compare and get both new and missing resource name. For new resource name, request the resource by name to create metadata into CSV `allNewItems_yyyymmdd.csv` and store in [reports](https://github.com/geobtaa/ckan-metadata/tree/main/reports) folder. Normally we get many new resource names, however, after filter out data types and keep **datasets** and **imagery**, only a few left.
