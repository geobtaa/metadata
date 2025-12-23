# Local Controlled Values

This page provides reference for some local controlled values.

## Harvest Workflow codes

The prefix indicates the primary strategy we use to process the records, even when it is a multistep workflow:

* **template** : creating the records directly in the GeoBTAA metadata profile. Typically, we are using a CSV or even the GBL Admin form view.  
* **tools** : relying on existing metadata software tools & apps to obtain and/or process the metadata.  Right now, the tools are the [OAI validator,](https://validator.oaipmh.com) [OpenRefine](https://openrefine.org), and [MarcEdit](https://marcedit.reeset.net).  
* **py** : python modules and scripts do most of the work. Any additional steps should be described within the code or its accompanying documentation

| Harvest Workflow | Description |
| :---- | :---- |
| template\_website| author a website only record directly in the GeoBTAA profile |
| template\_children | author a website and children records directly in the GeoBTAA profile |
| template\_csv | receive a spreadsheet of metadata and do some minor cleanup |
| tools\_oai\_openrefine | access the OAI-PMH API [OAI validator](https://validator.oaipmh.com); export an XML; load it into OpenRefine for cleanup and conversion to CSV |
| tools\_marcedit | use the MarcEdit tool to convert MARC records into a CSV |
| py\_arcgis\_hub | ArcGIS Hubs |
| py\_arcgis\_online | ArcGIS Online data collections |
| py\_socrata | Socrata portals |
| py\_ckan | CKAN portals |
| py\_hdx | Humanitarian Data Exchange CKAN portal |
| py\_ogm\_wisc | Individual JSONs in UW-Madison’s GBL 1.0 metadata  |
| py\_ogm\_gbl1 | Individual JSONs in the OGM GBL 1.0 metadata |
| py\_ogm\_aardvark | individual JSONs in the OGM Aardvark metadata |
| py\_pasda | PASDA custom data portal (HTML parser) |
| py\_isgs | ISGS custom data portal  (HTML parser) |
| py\_umedia | UMN UMedia modified Blacklight portal |
| py\_opex | OPEX / MODs files from Michigan |
| py\_oaipmh | OAI-PMH endpoints (use Python instead of tools) |
| py\_mods | MODS metadata files |
|  |  |
|  |  |


## Resource Types for Websites

### Data portals

* Purpose: to enable users to search, discover, and access datasets and web services for their own use.
* Examples: A CKAN search portal or an ArcGIS Hub

### Static web pages

* Purpose: simple, direct distribution of files. The content does not change in response to user interaction.  
* Examples: A basic HTML page with a list of links to download ZIP files or an FTP site.  

### Digital repositories

* Purpose: long-term, stable preservation and scholarly citation of digital objects, which may include datasets but also papers, images, and other media. The emphasis is on archival quality and persistent identification.  
* Examples: University digital conservancies, library collections on platforms like DSpace or Fedora, research institutes with data collections


### Interactive resources

* Purpose: to guide a user through a narrative or a curated data exploration. The user is consuming a finished information product.  
* Examples: Esri StoryMaps or web map applications.  


## Accrual method values

This is how we obtain the metadata (not how we process it)

### Automated retrieval

​​**Definition:** Metadata was actively retrieved from a live, external source using an automated or semi-automated tool. This is a "pull" method; we get the metadata ourselves.

**Examples:**

* Running a Python script to query an API  
* Using a tool to connect to an OAI-PMH endpoint  
* Scraping a web page

This is a passive harvest, we can redo it anytime.

### Mediated deposit

**Definition:** Metadata was sent as a discrete file or set of files from an external party. This is a "push" method; we are receiving a package.

**Examples:**

* A data provider emails you a CSV spreadsheet.  
* You are given a link to download a ZIP file containing XML records.  
* You download a JSON file from a repository's export page.

This relies on someone submitting records, we need them to send us files. We might reprocess those files for metadata augmentation but cannot get new ones ourselves.

### Manual curation

**Definition:** Metadata was created record-by-record through direct human input into a system or template, often by looking at a source website or document.

**Examples:**

* Typing metadata into the GBL Admin interface.  
* Filling out a GeoBTAA spreadsheet template from scratch by examining a web map.

This is a passive harvest, but is generally laborious to replicate. This should only be done for website level records or things we deem high priority and very stable.
