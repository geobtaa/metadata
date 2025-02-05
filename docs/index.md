---
hide:
  - navigation
  - toc
---

# GeoBTAA Metadata Handbook
This handbook describes how to harvest and format metadata records for the [BTAA Geoportal](https://geo.btaa.org).

-----
<div class="grid cards" markdown>

- ### [Reference](geobtaa-metadata-application-profile.md)

	Information about the GeoBTAA Metadata Application Profile and our harvest guidelines.

- ### [Explanation](resource-lifecycle.md)

	Descriptions and clarifications of processes, content organization, policies, and tools
	
</div>

<div class="grid cards" markdown>

- ### [Tutorials](tutorials.md)
	
	Short, easy to complete exercises to help someone get the basics of running and writing scripts to harvest metadata.

- ### [Recipes](recipes/index.md)

	Multi-step workflows for harvesting and editing metadata for the BTAA Geoportal.

</div>

----------

## Who is this handbook for?

* Team Members in the [Big Ten Academic Alliance Geospatial Information Network](http://gin.btaa.org) (BTAA-GIN)

* Development & Operations Staff in the BTAA-GIN

* Users & developers of open-source geospatial projects, such as [OpenGeoMetadata](https://opengeometadata.org) and [GeoBlacklight](https://geoblacklight.org)

* Contributors to the  [BTAA Geoportal](https://geo.btaa.org)

* Users of the [BTAA Geoportal](https://geo.btaa.org)


??? info "Metadata Handbook Version History"

	_Changes for Version 5.2 (February 4, 2025)_
	
	This release includes documentation for several new metadata fields and updated worflows.
	
	* 	Five new metadata fields on the [Custom Elements](b1g-custom-elements.md) page
	*  An updated workflow for the [ArcGIS Hub recipe](recipes/R-01_arcgis-hubs.md)
	*  Description of a new tutorial about changing paths in the Terminal.
	*  Removing links to documentation about GEOMG, now replaced by GBL Admin
	*  An updated and refined the [Resource Lifecycle steps and accompanying graphics](resource-lifecycle/).
	
	_Changes for Version 5.1 (September 25, 2023)_
	
	This version adds several new recipes and page cleanups.
	
	* New recipes for: 
		* cleaning metadata
		* adding bounding boxes
		* normalizing creators
		* updating our list of ArcGIS Hubs
		* how to add multiple download links in GEOMG
	* Updates the documentation for the ArcGIS, Socrata, and PASDA recipes. 
	* Updates the DCAT and CKAN documentation pages.
	
	
	_Changes for Version 5.0 (May 24, 2023)_
	
	This version incorporates the Harvesting Guide notebooks and includes documentation for harvesting metadata from different sources.
	
	* New page describing the Tutorials in the Harvesting Guide
	* Eight Recipe pages corresponding to Harvesting Guide
	* Updated header design to match Geoportal	 	
	
	_Changes for Version 4.6 (March 15, 2023)_
	
	* New page for manually adding bounding boxes
	* Restructure using Diataxis framework
	* Remove some GEOMG how to guidelines (moved to GEOMG Wiki)
	* Clarify Editing Template differences from OGM-Aaardvark documentation
	* Added Collection Development Policy and Curation Priorities documents
	* Update input guidelines for Spatial Coverage (FAST IDs)
	
	
	_Changes for Version 4.5.1 (February 28, 2023)_
	
	* Update version documentation
	* Add link to generated PDF
	
	_Changes for Version 4.5 (February 28, 2023)_
	
	* Add Creator ID
	* Update input guidelines for Creator, Creator ID
	* Remove Harvesting Guide info (migrating to separate site)
	* Edit Submitting Metadata page
	* Minor copy editing
	* Add PDF export capability
	
	_Changes for Version 4.4 (August 23, 2022)_
	
	- updated theme
	- reorganized and expanded navigation menu
	- new sections for Harvesting Guide and using GEOMG
	
	_Changes for Version 4.3 (August 15, 2022)_
	
	- migrate to MkDocs.org platform
	- update bounding box entry guidelines
	- add GEOMG page
	
	_Changes for Version 4.2 (March 24, 2022)_
	
	- New Entry and Usage Guidelines page
	- Expands content organization model documentation
	- Changes the name of the schema from 'Aardvark' to 'OpenGeoMetadata (version Aardvark)'
	- Cleans up outdated links
	
	_Changes for Version 4.1 (Jan 2022)_
	
	- updates Status as optional; removes controlled vocabulary
	- Clarifies relationship model
	
	_Changes for Version 4.0 (July 2021)_
	
	- Incorporation of GEOMG Metadata Editor
	- Upgrade to Aardvark Metadata Schema for GeoBlacklight
	
	_Changes for version 3.3 (May 13, 2020)_
	
	- Added University of Nebraska
	- Reorganized Metadata Elements to match editing template
	- Updated the “Update the Collections” section to match new administrative process for tracking records
	
	_Changes for version 3.2 (Jan 8, 2020)_
	
	- Added Date Range element
	
	_Changes for version 3.1 (Dec 19, 2019)_
	
	- Added collection level records metadata schema
	
	_Changes for version 3 (Oct 2019)_
	
	- GeoNetwork and Omeka deprecated
	- all GeoBlacklight records are stored in a spreadsheet in Google Sheets
	- records are transformed from CSV to GeoBlacklight JSON with a Python script
	- additional metadata fields were added for administrative purposes
	- IsPartOf field now holds a code pointing to the collection record
	- Administrative groupings such as “State agencies geospatial data” are now subjects, not a Collection
	- updated editing templates available
	- all supplemental metadata can be stored as XML or HTML in project hosted folder
	- updated links to collections database 



<!--
## Credits

Handbook prepared by:

- Karen Majewicz, Geospatial Product Manager
- Ziying (Gene) Cheng - Graduate Research Assistant-->
