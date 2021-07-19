# Workflow

![Metadata Workflow](/images/btaa-metadata-workflow.png)


## 1. Submit Records

The B1G Geoportal holds metadata records that point to geospatial data, maps, aerial imagery, and websites hosted online by external organizations. It is the role of the Task Force members to seek out new content for the geoportal. Task Force members are responsible for finding records in their own or adjacent states. Regional or national collections will be selected by the Collections Steering Group. 

**Criteria for submission**
- Review the [Collections Strategy](https://docs.google.com/document/d/1aRjH36dM76G_LCIUGJo1cIl4IGBizvA-Qncp39_DMic/edit?usp=sharing) from the Collections Development Committee.
- Resources need to be accessible over the web. Datasets should have a download or web services link. Maps should have a scanned image with a thumbnail and download link.
- Websites and Interactive Applications will be evaluated for accession on a case by case basis.
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
**1. Optional: Contact the organization**
- Use [this template](https://docs.google.com/document/d/1xqYbutgsrH5UTjKC9m5oBagIgk-8sSCpbYiZ5-tlZr8/edit?usp=sharing) to inform the organization that we plan to include their resources in our geoportal.
- If metadata for the resources are not readily available, the organization may be able to send them to you.

**2. Send an email to the Metadata Coordinator**
- Include a link to the collection
- Provide a Title and Description for the collection record

**3. The submission will be added to our collections processing queue**
The Metadata Coordinator will assign an alphanumeric code for the collection. This code will also be added to each metadata record to facilitate administrative tasks and for grouping items by their source.


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

| Third part of string | The sequence number added in order of accession or a county FIPs code|
| --- | ----------- |
| -01  | First collection added from same institution and type of organization |
| -02 | Second collection added from same institution and type of organization |
| -55079 | County FIPS code for Milwaukee County, Wisconsin |

Example code for a collection sourced from Milwaukee County: '10b-55079'

## 2. Metadata Transition

This stage involves batch processing of the records, including harvesting, transformations, crosswalking information. This stage is carried out by the Metadata Coordinator, who may contact Task Force members for assistance.

Regardless of the method used for acquiring the metadata, it is always transformed into a spreadsheet for editing. These spreadsheets are uploaded to GEOMG Metadata Editor.

Because of the variety of platforms and standards, this process can take many forms. The Metadata Coordinator will contact Task Force members if they need to supply metadata directly. Here are the most common methods per resource type:


### Geospatial data
**_API Harvesting_**
- Most data portals have APIs that can be programmatically parsed to obtain metadata for each record. 
- DCAT enabled portals: ArcGIS Open Data Portals (HUB), Socrata portals, and some others share metadata in the [DCAT standard](https://www.w3.org/TR/vocab-dcat/). This is typically accessed by appending “/data.json” to the end of the portal’s base URL. Our project created Python scripts to harvest from these portals that are stored in the GitHub Repository [BTAA-Geospatial-Data-Project/dcat-metadata](https://github.com/BTAA-Geospatial-Data-Project/dcat-metadata) 
- CKAN / DKAN portals: This application uses a custom metadata schema for their API. Our project uses the Python scripts found in the BTAA fork of the CKAN project at [BTAA-Geospatial-Data-Project/ckanapi-exporter](https://github.com/BTAA-Geospatial-Data-Project/ckanapi-exporter).

**_HTML Parsing_**
- If a data portal or website does not have an API, we may be able to parse the HTML pages to obtain the metadata needed to create GeoBlacklight schema records. 
- This is done using the project created Python scripts found in  [BTAA-Geospatial-Data-Project/parse-html](https://github.com/BTAA-Geospatial-Data-Project/parse-html).

**_Individual Geospatial Metadata Standard files_**
- Geospatial metadata standards are expressed in the XML format, which can be parsed to extract metadata needed to create GeoBlacklight schema records. 
- The following file types are accepted for metadata extraction and can serve as Supplemental Metadata:
    - **ISO 19139 XML and FGDC XML files**: They are parsed to extract metadata values for GeoBlacklight metadata using the project created Python scripts found in [BTAA-Geospatial-Data-Project/parse-xml](https://github.com/BTAA-Geospatial-Data-Project/parse-xml)
    - **ArcGIS 1.0 Metadata XML files**: These records are transformed to ISO 19139 using XSLT. They are then treated the same as the ISO as described above.

**_Downloading Data_**
- Some metadata is only available as part of a zipped download of the datasets. 
- In this case, the Metadata Coordinator will use scripts to batch download the records, unzip them, and process their metadata locally.


### Maps
**_OAI-PMH_**
- The [Open Archives Initiative Protocol for Metadata Harvesting (OAI-PMH)](https://www.openarchives.org/pmh/) is a framework that can be used to harvest metadata records from enabled repositories. 
- The records are usually available as a simple Dublin Core XML format. 
- If the protocol is not set up to include extra fields, such as the map image's download link or bounding box, this method may not be sufficient on its own. 

**_Spreadsheets_**
- Administrators for university repositories for scanned maps or data can often export metadata into a spreadsheet, especially for Dublin Core. 
- This method is preferred, because the University IT professionals and librarians can control which fields to export, and because transformations by the Metadata Coordinator are not necessary.
- The [B1G Map Template](https://z.umn.edu/b1g-template) shows all of the fields needed for GeoBlacklight.

**_MARC files_**
- The best way to transfer this type of metadata is to send a single file containing multiple records in the .MRC or MARC XML format. 
- The Metadata Coordinator will use MarcEdit or XML parsing to transform the records to GeoBlacklight using the project-designated MARC to GBL crosswalk, but Task Force members can specify preferences.




## 3. Edit Records

Once the metadata is in spreadsheet form, it is ready to be normalized and augmented. The Metadata Coordinator will add template information that each record in a group shares, and use spreadsheet functions or scripts to programmatically complete the metadata records.

This work is carried out by the Metadata Coordinator and Graduate Research Assistants.

### Editing Template
- [The GBL Metadata Template](http://z.umn.edu/b1g-template) is for creating GeoBlacklight metadata.
- Refer to the documentation for the [Aardvark fields](https://opengeometadata.github.io/aardvark/aardvarkMetadata.html) and the [B1G profile fields](b1gProfile.html) for guidance on values and formats.



## 4. Publish Records

The following actions are carried out by the Metadata Coordinator and Graduate Research Assistants.

### 1. Save edited template as a CSV file

### 2. Upload the spreadsheet to GEOMG
- This is done via the batch imports function. 
- When logged into GEOMG, go to Admin Tools and select Imports. Click "New Import".
- Give a name to the upload and enter details about the source and description. These details are helpful later in tracking imports.
- Select the CSV file for upload
- For Type, choose the BTAA CSV. 
- Click the **Create Import** button
- Review the _Field Mappings_ page. If the CSV was formatted with column headers spelled the same way as the template, the fields should automatically map to the correct elements. Otherwise, manually choose the crosswalk mapping.
- Scroll to the bottom and click the button **Create Mapping**
- On the _Import_ page, check that the number in the CSV Row Count matches your CSV.
- Click the button **Run Import**
- The import may take a few minutes. During the process, you can view the Import Results tab. Items in the queue will show up in the first sub-tab ("Failed"), but will transfer to the second tab upon import ("Success").
- When complete, review any items that did not import in the Failed tab. See Troubleshooting (_coming soon_) for help.

### 3. Spot check records for errors and consistency
- The newly uploaded records will be listed as Draft under the Publication State on the main dashboard
- Select 'Draft' under Publication State and select an item. This will open it in editing view.
- Click the button **View in Geoportal**
- Inspect the record and test the links. (note: Metadata and Web Service links will not open while the item is still in Draft)
- Repeat this process for about 3 records.


### 4. Convert records from 'Draft' to 'Published'

- If the records are satisfactory, return to the Dashboard view and select all Draft items in the upload. 
- Select All and then select the text "Select all results that match this search"
- Click the State button. From the dropdown, select Published.
- On the _Bulk Action_ page, click the button **Run Bulk Action**
- It will take 3-5 minutes for the items to publish in the BTAA Geoportal. 
- Review 3-5 of the published records and test all the links.

### 5. Publish to OpenGeoMetadata
- Completed records are synced to the workflow GitHub online repository as needed. 
- Records that are deemed stable and complete can be shared with the [OpenGeoMetadata community](https://github.com/OpenGeoMetadata/big-ten).






## Maintenance

### General Maintenance
All project team members are encouraged to review the geoportal records assigned to their institutions periodically to check for issues. Use the feedback form at the top of each page in the geoportal to report errors or suggestions.  This submission will include the URL of the last page you were on, and it will be sent to the Metadata Coordinator.


### Broken Links
The geoportal will be programmatically checked for broken links on a monthly basis. Systematic errors will be fixed by the Metadata Coordinator. Some records from this report may be referred back to Task Force members for investigating broken links.


### Subsequent Accessions
- ArcGIS Hubs, Socrata, and CKAN portals that utilize the DCAT metadata standard will be re-accessioned monthly using scripts in the project’s GitHub repository called [dcat-metadata](https://github.com/BTAA-Geospatial-Data-Project/dcat-metadata).
- Other GIS data portals will be periodically re-accessioned by the Metadata Coordinator at least once per year.
- The Metadata Coordinator and Graduate Research Assistants carry out this work in batches.
- Task Force members may be asked to review this work and provide input on decisions for problematic records.

### Retired Records
When an external resource has been moved, deleted, or versioned to a new access link, the original record is retired from the BTAA Geoportal. This is done by converting the Publication State of the record from 'Published' to 'Unpublished'. 
The record is not deleted from the database and can still be accessed via a direct link. However, it will not show up in any search queries.


