<div align="center">
<h1>Metadata Workflow Handbook<br/>for Task Force Members</h1>
<div>Big Ten Academic Alliance Geospatial Data Project</div>
<br/>
<br/>
<br/>
<img src="https://geo.btaa.org/assets/btaa-logo-e622d081b6b06b467cc6fdf105f8bd4d127734fc25ace50d8178cde95df26d67.jpg"> 
<br/>
<br/>
<h4>Prepared by: Karen Majewicz, Project Metadata Coordinator</h4>
<h4>Version 3.3</h4>
<h4>Published July 2021</h4>
Updated December 15, 2020<br/>
Updated January 8, 2020<br/>
Updated May 13, 2020<br/>
<br/><br/><br/>
</div>





<hr>
<h2 align="center">Introduction</h2>
This guide was prepared with the objective of assisting Task Force members in the [Big Ten Academic Alliance Geospatial Data Project](http://z.umn.edu/btaagdp) and includes:

- overviews of collections scope and metadata schemas
- a general description of the full workflow process
- the roles and activities undertaken by Task Force members and the Metadata Coordinator

The [project glossary](https://sites.google.com/umn.edu/btaa-gdp/about/project-documents/glossary) defines many of the terms in this guide.

> **_Changes for version 3 (Oct, 2019)_**
- GeoNetwork and Omeka deprecated
- all GeoBlacklight records are stored in a master spreadsheet in Google - Sheets
- records are transformed from CSV to GeoBlacklight JSON with a Python script
- additional metadata fields were added for administrative purposes
- IsPartOf field now holds a code pointing to the collection record
- Administrative groupings such as “State agencies geospatial data” are now subjects, not a Collection
- updated editing templates available
- all supplemental metadata can be stored as XML or HTML in project hosted folder
- updated links to collections database 

> **_Changes for version 3.1 (Dec 19, 2019)_**
- Added collection level records metadata schema

> **_Changes for version 3.2 (Jan 8, 2020)_**
- Added Date Range element

> **_Changes for version 3.3 (May 13, 2020)_**
- Added University of Nebraska
- Reorganized Metadata Elements to match [editing template](https://docs.google.com/spreadsheets/d/1dZoO1WZeyfWJnxqT9x7lJsH0MsSqlih8T-mXXjvzLNU/edit?usp=sharing)
- Updated the “Update the Collections” section to match new administrative process for tracking records





<hr>
<h2 align="center">Metadata Schemas</h2>

### The GeoBlacklight Schema
The primary metadata record for each resource is in the GeoBlacklight schema. This lightweight schema was designed specifically for the GeoBlacklight application and is geared towards discoverability. [The schema is documented on our project website](https://sites.google.com/umn.edu/btaa-gdp/about/project-documents/metadata-guides/metadata-profile-of-geoblacklight-schema), and in the [Collections Management Database](https://airtable.com/shruGYkqsNqj8USyQ).

> **_General Features of the GeoBlacklight Schema_**
- Based upon and shares most of its elements with [Dublin Core](http://dublincore.org/documents/dcmi-terms/)
- Includes a few GeoBlacklight custom elements for spatial metadata
- Published as a JSON document

> **_B1G Project Specific Features of the GeoBlacklight Schema_**
- The B1G profile of the GeoBlacklight Schema includes several custom elements specific to our project’s implementation of GeoBlacklight
- The records are created with spreadsheets and stored in Google Drive
- The JSONs are created by transforming the CSV spreadsheets to JSON with a Python script


### Supplemental Metadata
All other forms of metadata, such as ISO 19139, FGDC Content Standard for Digital Geospatial Metadata, attribute table definitions, or custom schemas are treated as Supplemental Metadata.
- Supplemental Metadata is not usually edited directly for inclusion in the project.
- If this metadata is available as XML or HTML, it can be added as a hosted link for the Metadata preview tool in GeoBlacklight.
- XML or HTML files can be parsed to extract metadata that forms the basis for the item’s GeoBlacklight schema record.
- Hosting: Supplemental metadata is generally harvested from external sites and hosted in the [project’s web server directory](http://btaagdp.org/metadata/). 
- The file formats that can be viewed within the geoportal application include:
    - ISO 19139 XML
    - FGDC XML
    - HTML (any standard)





<hr>
<h2 align="center">Submit Records</h2>

The B1G Geoportal holds metadata records that point to geospatial data, maps, aerial imagery, and websites hosted online by external organizations. It is the role of the Task Force members to seek out new content for the geoportal. Task Force members are responsible for finding records in their own or adjacent states. Regional or national collections will be selected by the Collections Steering Group. 

### Criteria for submission
- Resources need to be accessible over the web. Datasets should have a download or web services link. Maps should have a scanned image with a thumbnail and download link.
- The resources should be out of copyright and publicly available.
- Places to find public domain collections:
    - State GIS clearinghouses
    - State agencies
    - County or City GIS departments
    - University libraries or research repositories
    - Nonprofit organizations, especially those with an environmental focus.
- The resources should have a spatial component. Nonspatial data tables are out of scope.
- If you are unsure if the collection meets these criteria, go ahead and submit it as "prospective". The Metadata Coordinator will review it in consultation with you.


### How to submit new records 
**_1. Optional: Contact the organization_**
- Use [this template](https://docs.google.com/document/d/1xqYbutgsrH5UTjKC9m5oBagIgk-8sSCpbYiZ5-tlZr8/edit?usp=sharing) to inform the organization that we plan to include their resources in our geoportal.
- If metadata for the resources are not readily available, the organization may be able to send them to you.

**_2. Send an email to the Metadata Coordinator_**

**_3. The submission will be added to our Collections Management Database_**
The Metadata Coordinator will assign an alphanumeric code for the group. This code will also be added to each metadata record to facilitate administrative tasks and for grouping items by their source.


### Code Naming Schema 
| First part of string | Contributing institution |
| --- | ----------- |
| 01 | Indiana University |
| 02 | University of Illinois Urbana-Campaign |
| 03 | University of Iowa | 
| 04 | University of Maryland |
| 05 | University of Minnesota |
| 06 | Michigan State University |
| 07 | University of Michigan |
| 08 | Pennsylvania State University |
| 09 | Purdue University |
| 10 | University of Wisconsin-Madison | 
| 11 | The Ohio State University |
| 12 | University of Chicago |
| 13 | University of Nebraska-Lincoln |

| Second part of string | Type of organization hosting the datasests |
| --- | ----------- |
| a | State |
| b | County |
| c | Municipality | 
| d | University |
| f | Other (ex. NGOs, Regional Groups, Collaborations)|
| g | Federal |

| Third part of string | The sequence number added in order of accession |
| --- | ----------- |
| -01  | First collection added from same institution and type of organization |
| -02 | Second collection added from same institution and type of organization |





<hr>
<h2 align="center">Metadata Transition</h2>

This stage involves batch processing of the records, including harvesting, transformations, crosswalking information. This stage is carried out by the Metadata Coordinator, who may contact Task Force members for assistance.

Regardless of the method used for acquiring the metadata, it is always transformed into a spreadsheet for editing. These spreadsheets are stored in Google Drive. 

Once the records have been harvested, the activity is recorded as an “Accession” in the Collections Management Database on the Actions Tab.

Because of the variety of platforms and standards, this process can take many forms. The Metadata Coordinator will contact Task Force members if they need to supply metadata directly. Here are the most common methods per resource type:


### Geospatial data
> **_API Harvesting_**
- Most data portals have APIs that can be programmatically parsed to obtain metadata for each record. 
- DCAT enabled portals: ArcGIS Open Data Portals (HUB), Socrata portals, and some others share metadata in the [DCAT standard](https://www.w3.org/TR/vocab-dcat/). This is typically accessed by appending “/data.json” to the end of the portal’s base URL. Our project created Python scripts to harvest from these portals that are stored in the GitHub Repository [BTAA-Geospatial-Data-Project/dcat-metadata](https://github.com/BTAA-Geospatial-Data-Project/dcat-metadata) 
- CKAN / DKAN portals: This application uses a custom metadata schema for their API. Our project uses the Python scripts found in the BTAA fork of the CKAN project at [BTAA-Geospatial-Data-Project/ckanapi-exporter](https://github.com/BTAA-Geospatial-Data-Project/ckanapi-exporter).

> **_HTML Parsing_**
- If a data portal or website does not have an API, we may be able to parse the HTML pages to obtain the metadata needed to create GeoBlacklight schema records. 
- This is done using the project created Python scripts found in  [BTAA-Geospatial-Data-Project/parse-html](https://github.com/BTAA-Geospatial-Data-Project/parse-html).

> **_Individual Geospatial Metadata Standard files_**
- Geospatial metadata standards are expressed in the XML format, which can be parsed to extract metadata needed to create GeoBlacklight schema records. 
- The following file types are accepted for metadata extraction and can serve as Supplemental Metadata:
    - **ISO 19139 XML and FGDC XML files**: These records are uploaded to our [project’s web server directory](http://btaagdp.org/metadata/). They are next parsed to extract metadata values for GeoBlacklight metadata using the project created Python scripts found in [BTAA-Geospatial-Data-Project/parse-xml](https://github.com/BTAA-Geospatial-Data-Project/parse-xml)
    - **ArcGIS 1.0 Metadata XML files**: These records are transformed to ISO 19139 using XSLT. They are then treated the same as the ISO as described above.

> **_Downloading Data_**
- Some metadata is only available as part of a zipped download of the datasets. 
- In this case, the Metadata Coordinator will use scripts to batch download the records, unzip them, and process their metadat


### Maps
> **_OAI-PMH_**
- The [Open Archives Initiative Protocol for Metadata Harvesting (OAI-PMH)](https://www.openarchives.org/pmh/) is a framework that can be used to harvest metadata records from enabled repositories. 
- The records are usually available as a simple Dublin Core XML format. 
- If the protocol is not set up to include extra fields, such as the map image's download link or bounding box, this method may not be sufficient on its own. 

> **_Spreadsheets_**
- Administrators for university repositories for scanned maps or data can often export metadata into a spreadsheet, especially for Dublin Core. 
- This method is preferred, because the University IT professionals and librarians can control which fields to export, and because transformations by the Metadata Coordinator are not necessary.

> **_MARC files_**
- The best way to transfer this type of metadata is to send a single file containing multiple records in the .MRC or MARC XML format. 
- The Metadata Coordinator will use MarcEdit to transform the records to GeoBlacklight using the project-designated MARC to GBL crosswalk, but Task Force members can specify preferences.





<hr>
<h2 align="center">Edit Records</h2>

Once the metadata is in spreadsheet form, it is ready to be normalized and augmented. The Metadata Coordinator will add template information that each record in a group shares, and use spreadsheet functions or scripts to programmatically complete the metadata records.


### Editing Template
[The GBL Metadata Template](https://docs.google.com/spreadsheets/d/1dZoO1WZeyfWJnxqT9x7lJsH0MsSqlih8T-mXXjvzLNU/edit?usp=sharing) is for creating GeoBlacklight metadata. The first row includes dropdown lists for controlled vocabularies or italicized examples on how to format the entry. See the next section for details on each column in the template.


### Element Details
> #### IDENTIFICATION 
#### _`DESCRIPTIVE`_
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Title
: When practical, titles for GIS data are changed to the format theme:place. Dates can be added at the end if the dataset is for a specific time period. Most dates or numbers are moved from the beginning of the title to facilitate browsing in the geoportal. Titles for scanned maps are not altered from their official title in a library catalog.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Alternative Title
: This field keeps the original title from the data provider.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Description
: These are plain text fields, so HTML formatting is removed. The description may be a concatenation of multiple fields from another metadata format to include things such as scale, rights, or purpose. If no description is available, it can be created by combining the GeoBlacklight metadata elements: geometry type, format, theme, place, date, publisher.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Language
: The language(s) used in the dataset or map. Spell the name of the language out in English (e.g., "French")


#### _`CREDITS`_
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Creator
: This field can contain multiple creators. For maps, it may include the surveyor, cartographer, and lithographer. For GIS data, it can be personal names or specific agencies. Often, it will further refine the Collection & Publisher fields. Example: “Collection: State Agencies Geospatial Data; Publisher: State of Iowa; Creator: Iowa Department of Transportation”

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Publisher
: The concept of publisher for digital resources is not well defined. For the Geospatial data in our project, we indicate the administrative body that made the resource available. Choose from the name of a state, county, city, regional organization, NGO, or University/College. Example: “State of Maryland” or “University of Minnesota.” In most cases, the publisher should correspond to the collection. Ex. “Collection: State Agencies Geospatial Data; Publisher: State of Maryland”. For scanned maps in our project, this field can include the publisher of the original map, but also the University Library that published the digital version.


#### _`CATEGORIES`_
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Genre
: This is a custom field for the B1G geoportal for users to be able to easily filter between resource types. The three options are: “Geospatial data”, “Maps”, or “Aerial imagery”.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Subject
: These terms are chosen from controlled vocabulary lists. Geospatial data should have an ISO Topic Category, and Maps should have a Library of Congress Cartographic Genre (if applicable). Aerial imagery should have the ISO Topic Category of “Imagery and Base Maps”.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Keyword
: These free form terms are not part of a controlled vocabulary. They are searchable by users, but not viewable in the interface.


#### _`TEMPORAL`_
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Date Issued
: This is the publication date, if known.  It can be in the form YYYY or YYYY-MM-DD.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Temporal Coverage
: This is a string value and can be formatted in any way that clarifies the time period. Examples: “1910?”, “1800-1805”, “before 2000”.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Date Range
: This is a Solr date type field. Multiple ranges can be entered. The format should be [1900 TO 1900] or [1900 TO 1950]. This field is used for indexing the Year & Time Period facet.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Solr Year
: This is an integer field in the form YYYY that is used for indexing in the Year & Time Period facet. Use the earliest date in the temporal coverage field, or the Date Issued. If no date is provided, it will default to 9999, so an estimate is preferred.


#### _`SPATIAL`_
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Spatial Coverage
: Our place name keywords are normalized to the state level for all values in the United States. Place names from other nations should be written out to the country level.
: - City, state - ”Dublin, Ohio”
: - County, state - “Cook County, Illinois”
: - Feature, state (optional)- “Mississippi River”
: - State or territory, country - “British Columbia, Canada”
: - Country - “Maldives”

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;GeoNames
: This optional field records a GeoNames URI in the form http://sws.geonames.org/numericcode

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Bounding Box
: The four coordinates should be provided as decimal degrees in the form W,S,E,N. This is the same format as the CSV output setting on the [Klokan Bounding Box](http://boundingbox.klokantech.com/).



> #### DISTRIBUTION
#### _`OBJECT`_
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Type
: This field observes the Dublin Core controlled vocabulary for [Type](https://github.com/geoblacklight/geoblacklight/wiki/Type-values). Values used in the Geoportal include: Dataset, Image, Collection, Service, and Interactive Resource.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Geometry Type
: This field helps to differentiate between vector (Point, Line, Polygon), raster (Raster, Image), nonspatial formats (table), or a combination (Mixed). The value will trigger an associated icon that displays next to an item in the search results.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Format
: It is preferred to select a format type from the dropdown lists provided in the templates.  However, custom file formats or general terms are allowed. This term appears in the Download button in the geoportal as Download {format}.


#### _`ACCESS LINKS`_
In the spreadsheet, each link type will have its own column. There can only be one link per type:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Information
: This link is for an external web page. Ideally, it is a landing page for the single resource. If that is unavailable, the home page for the resource’s publisher can be added.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Download
: The first choice for this link is a direct download file. If that is unavailable, a landing page for the item can be added. Even if it duplicates the Information page, there should always be a value here to facilitate a standardized user experience.


#### _`GEOSPATIAL WEB SERVICES`_
Geospatial web services will only display if they are in the Web Mercator projection. All web services must be hosted over a secure protocol (https://). 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ArcGIS REST SERVICES
: These should be a single layer, rather than a group of layers. For example, this service https://gis.ohiodnr.gov/arcgis/rest/services/DGS_Services/Earthquakes/MapServer/1 with the “1” at the end displays. If we remove the 1, there are two layers at that address. They may show up in the geoportal web preview, but often they will not, especially if there are many of them.

: The link itself will contain one of the phrases to indicate which column to add it to:
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**FeatureServer**
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**MapServer**
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**ImageServer**
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**TileServer**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;OGC WEB SERVICES
: These services generally come from GeoServer.
: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**WFS (Web Feature Service)**
: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Only the base URL should be added here. Example: “https://bloomington.in.gov/geoserver/wfs”
: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**WMS (Web Map Service)**
: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Only the base URL should be added here. Example: “https://bloomington.in.gov/geoserver/wms”
: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Layer ID**
: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The layer for these types of services needs to be added to a second field called Layer ID. Example for the Layer ID field: “publicgis:MPOPlanningArea”

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Open Index Map
: A link to an online GeoJSON document in the [Open Index Map specification](https://openindexmaps.org/) that functions as a selectable index map in the geoportal.


#### _`IMAGES`_
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Image
: A static image URL that will be used for a thumbnail on the Search Results page and on the item view page if there is no web service. Use the highest quality image available online for this value. It will be compressed for display in the geoportal.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;IIIF
: This is for the International Image Interoperability Framework Image API. The URL will end with “.json”

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Manifest
: This is another form of IIIF Json that includes metadata and multiple items, known as a Presentation Manifest.


#### _`METADATA`_
This is for the supplemental metadata file that will display in an iframe when the user clicks the “Metadata” text in the Tools palette. XML files must be valid as they are transformed on the fly by an application internal XSLT.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ISO Metadata
: Valid ISO 19139 XML file

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;FGDC Metadata
: Valid FGDC XML file

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;HTML
: Any standard

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Documentation
: Link or downloadable file representing a codebook, attribute table, or other supporting information.



> #### ADMINISTRATIVE ELEMENTS
#### _`CODES`_
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Identifier
: This is a long alphanumeric string that is assigned to the metadata file for the resource. If available and sufficiently unique, the original identifier for the item will be used. Otherwise, it will be generated as a [Version 4 UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier#Version_4_(random)). The identifier is also part of the slug for a record’s URL address in the geoportal.
Collection records will use the group’s Code as the Identifier.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Provenance
: The name of the institution that holds the resource or acts as the custodian for the metadata record. The value is the short name for the Institution:
Illinois, Iowa, Maryland, Minnesota, Michigan State, Michigan, Penn State, Purdue, Wisconsin, Ohio State, Chicago

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Code
: The alphanumeric code assigned to the collection (see Code Naming Schema chart on page 5).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Is Part Of
: This field is used to establish collection-item records. The Code of the collection is added to this field in each of the item records.  Do not add a value to the parent record. The GeoBlacklight application will display this relationship in the interface. [More information about this widget](https://github.com/geoblacklight/geoblacklight/wiki/Using-data-relations-widget).
: When records are retired, this field is set to empty.


#### _`LIFE CYCLE`_
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Status
: This field indicates if the status of the record is ACTIVE, RETIRED, or UNKNOWN.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Accrual Method
: This field indicates how the record was obtained. Values include ArcGIS Hub, Socrata, DCAT, HTML, ISO, FGDC, GeoBlacklight, Dublin Core, and Manual Download.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Accrual Periodicity
: Used for collection level records to indicate frequency of re-accessions.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Date Accessioned
: The date the record was added to the Geoportal in the form YYYY-MM-DD

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Date Retired
: This field indicates when the record was retired from the Geoportal.  This record will still be accessible via a direct link, but will be suppressed in search results and will be noted as “Retired” in the Description field.


#### _`ACCESSIBILITY`_
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Rights
: Values are “Public” or “Restricted.” Restricted items will display a padlock next to the title, and any download or web services links will be suppressed.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Access Rights
: Free text field for information about rights, access, or licenses.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Suppressed
: This is a boolean field with the values TRUE or FALSE. If set to TRUE, the record will not appear in search results, but can still be accessed via a direct link.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Child
: This is a boolean field with the values TRUE or FALSE. If set to TRUE, the record will not be boosted in search results and should appear towards the end of the list.


### Collection Level Records Schema
All records are grouped into collections that are represented by collection level records. These records have a reduced schema:
- Identifier
- Code
- Accrual Method
- Accrual Periodicity
- Title
- Description
- Genre
- Keywords
- Type - “Collection”
- Geometry Type - “Table”
- Bounding Box
- Spatial Coverage
- Provenance
- Publisher
- Information Link





<hr>
<h2 align="center">Publish Records</h2>

The following actions are carried out by the Metadata Coordinator. They require the Python scripts found in the [BTAA-Geospatial-Data-Project/workflow](https://github.com/BTAA-Geospatial-Data-Project/workflow) GitHub Repository, and a University of Minnesota VPN connection.

**_1. Convert spreadsheet to GeoBlacklight JSONs_**
- Download the selected records to a CSV file
- Use the [csv_to_gbljson.py](https://github.com/BTAA-Geospatial-Data-Project/workflow/blob/master/csv_to_gbljson.py) script to transform the files
- Inspect a sample of the files to manually scan for errors
- Note: this script will convert two fields into different formats
    - Bounding Box: The values will be re-ordered and set to the format `Envelope(W,E,N,S)`
    - References: The script will combine the links into `dct_references_s` as key:value pairs separated by a comma.

**_2. Publish to Dev_**
- Connect to the University of Minnesota Libraries VPN. 
- Change the Solr address in the `config.py` script to point to the development server. 
- Open the Terminal and change directories into your workflow folder
- In the terminal, type `python publish.py -aj NameOfJSONFolder`
- Review the records in https://geodev.btaa.org to check for errors and omissions. 
- If additional review is needed, notify task force members to look over the records.

**_3. Publish to Prod_**
- Change the Solr address in the config.py script to point to the production server. 
- In the Terminal, type `python publish.py -aj NameOfJSONFolder`
- Review the records in https://geo.btaa.org to check for errors and omissions. 
- Notify task force members that the records are public

**_4. Update the Collections Management Database_**
Create a new CSV of updated records with the following fields: Title, Status, Code, Is Part Of, Date Accessioned, and Date Retired
Go to the Records tab in the Collections Management Database
Use the CSV module to upload the updated records

**_5. Publish to GitHub_**
- Completed records are synced to the workflow GitHub online repository as needed. 
- Records that are deemed stable and complete can be shared with the [OpenGeoMetadata community](https://github.com/OpenGeoMetadata/big-ten).





<hr>
<h2 align="center">Maintenance</h2>

### General Maintenance
All project team members are encouraged to review the geoportal records assigned to their institutions periodically to check for issues. Use the feedback form at the top of each page in the geoportal to report errors or suggestions.  This submission will include the URL of the last page you were on, and it will be sent to the Metadata Coordinator.


### Broken Links
The geoportal will be programmatically checked for broken links on a monthly basis. Systematic errors will be fixed by the Metadata Coordinator. Some records from this report may be referred back to Task Force members for investigating broken links.


### Subsequent Accessions
- ArcGIS Hubs, Socrata, and CKAN portals that utilize the DCAT metadata standard will be re-accessioned monthly using scripts in the project’s GitHub repository called [dcat-metadata](https://github.com/BTAA-Geospatial-Data-Project/dcat-metadata).
- Other GIS data portals will be periodically re-accessioned by the Metadata Coordinator at least once per year.
- The Metadata Coordinator and Graduate Research Assistants carry out this work in batches.
- Task Force members may be asked to review this work and provide input on decisions for problematic records.



