---
toc:
  baselevel:2
---

!!! Warning "This guide is a work in progress (August 2022)"


![Metadata Workflow](./images/btaa-metadata-workflow.png)


## 1. Submit Records

**1. Optional: Contact the organization**

- Use [this template](https://docs.google.com/document/d/1xqYbutgsrH5UTjKC9m5oBagIgk-8sSCpbYiZ5-tlZr8/edit?usp=sharing) to inform the organization that we plan to include their resources in our geoportal.
- If metadata for the resources are not readily available, the organization may be able to send them to you.

**2. Send an email to the Metadata Coordinator**

Things to include:

- a link to the website
- Title and Description of the collection
- (If known) information about how to harvest the metadata or construct access links

**3. The submission will be added to our collections processing queue**

Metadata processing tasks are tracked on our public [GitHub project dashboard](https://github.com/orgs/geobtaa/projects/4).


## 2. Metadata Transition

This stage involves batch processing of the records, including harvesting, transformations, crosswalking information. This stage is carried out by the Metadata Coordinator, who may contact Team members for assistance.

!!! info "See our [Harvest Guide](harvestGuide.md) for more information on formats and techniques for harvesting metadata"

Regardless of the method used for acquiring the metadata, it is always transformed into a spreadsheet for editing. These spreadsheets are uploaded to GEOMG Metadata Editor.

Because of the variety of platforms and standards, this process can take many forms. The Metadata Coordinator will contact Team members if they need to supply metadata directly. 




## 3. Edit Records

Once the metadata is in spreadsheet form, it is ready to be normalized and augmented. UMN Staff will add template information and use spreadsheet functions or scripts to programmatically complete the metadata records.

- [The GBL Metadata Template](http://z.umn.edu/b1g-template) is for creating GeoBlacklight metadata.
- Refer to the documentation for the [Aardvark fields](https://opengeometadata.github.io/aardvark/aardvarkMetadata.html) and the [B1G profile fields](b1g-custom-elements.md) for guidance on values and formats.


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


