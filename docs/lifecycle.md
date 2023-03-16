---
toc:
  baselevel:2
---


![Metadata Workflow](./images/btaa-metadata-workflow.png)


## 1. Submit Records

It is the role of the Team members to seek out new content for the geoportal. See the page [How to Submit Resources to the BTAA Geoportal](/submit-resources) for more information.


## 2. Metadata Transition

This stage involves batch processing of the records, including harvesting, transformations, crosswalking information. This stage is carried out by the Metadata Coordinator, who may contact Team members for assistance.

Regardless of the method used for acquiring the metadata, it is always transformed into a spreadsheet for editing. These spreadsheets are uploaded to GEOMG Metadata Editor.

Because of the variety of platforms and standards, this process can take many forms. The Metadata Coordinator will contact Team members if they need to supply metadata directly. 


## 3. Edit Records

Once the metadata is in spreadsheet form, it is ready to be normalized and augmented. UMN Staff will add template information and use spreadsheet functions or scripts to programmatically complete the metadata records.

- [The GeoBTAA Metadata Template](http://z.umn.edu/b1g-template) is for creating GeoBlacklight metadata.
- Refer to the documentation for the [OpenGeoMetadata, version Aardvark fields](https://opengeometadata.org/docs/ogm-aardvark) and the [GeoBTAA Custom Elements](b1g-custom-elements.md) for guidance on values and formats.


## 4. Publish Records

Once the editing spreadsheets are completed, UMN Staff uploads the records to `GEOMG`, a metadata management tool. GEOMG validates records and performs any needed field transformations. Once the records are satisfactory, they are published and available in the BTAA Geoportal.

[Read more on the GEOMG documentation page.](geomg.md)


## 5. Maintenance

**General Maintenance**

All project team members are encouraged to review the geoportal records assigned to their institutions periodically to check for issues. Use the feedback form at the top of each page in the geoportal to report errors or suggestions.  This submission will include the URL of the last page you were on, and it will be sent to the Metadata Coordinator.


**Broken Links**

The geoportal will be programmatically checked for broken links on a monthly basis. Systematic errors will be fixed by UMN Staff. Some records from this report may be referred back to Team Members for investigating broken links.


**Subsequent Accessions**

* Portals that utilize the DCAT metadata standard will be re-accessioned monthly.
* Other GIS data portals will be periodically re-accessioned by the Metadata Coordinator at least once per year.
* Team members may be asked to review this work and provide input on decisions for problematic records.

**Retired Records**

When an external resource has been moved, deleted, or versioned to a new access link, the original record is retired from the BTAA Geoportal. This is done by converting the Publication State of the record from 'Published' to 'Unpublished'. The record is not deleted from the database and can still be accessed via a direct link. However, it will not show up in any search queries.


