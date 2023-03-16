---
hide:
  - navigation
  - toc
---

# GeoBTAA Metadata Handbook
This handbook describes how to curate metadata records for the [BTAA Geoportal](https://geo.btaa.org).


## Who is this for?

* Team Members in the [Big Ten Academic Alliance Geospatial Information Network](http://z.umn.edu/btaagdp) (BTAA-GIN)

* Development & Operations Staff in the BTAA-GIN

* Users & developers of open-source geospatial projects, such as [OpenGeoMetadata](https://opengeometadata.org) and [GeoBlacklight](https://geoblacklight.org)

* Contributors to the  [BTAA Geoportal](https://geo.btaa.org)

* Users of the [BTAA Geoportal](https://geo.btaa.org)

-----

## Contents:

### [GeoBTAA Metadata Profile](components.md)


:   The GeoBTAA Metadata Profile combines the [OpenGeoMetadata](https://opengeometadata.org) schema, local input guidelines, and custom elements.

### [Content Organization Model for the BTAA Geoportal](model.md)


: The Content Organization Model defines how records are organized and how they are related within the BTAA Geoportal.


### [Curation workflows](lifecycle.md)


: Step by step guides for selecting, submitting, harvesting, editing, publishing, and maintaining metadata records in the BTAA Geoportal


----------


## Version History

**_Changes for Version 4.4 (August 23, 2022)_**

- updated theme
- reorganized and expanded navigation menu
- new sections for Harvesting Guide and using GEOMG

**_Changes for Version 4.3 (August 15, 2022)_**

- migrate to MkDocs.org platform
- update bounding box entry guidelines
- add GEOMG page

**_Changes for Version 4.2 (March 24, 2022)_**

- New Entry and Usage Guidelines page
- Expands content organization model documentation
- Changes the name of the schema from 'Aardvark' to 'OpenGeoMetadata (version Aardvark)'
- Cleans up outdated links

**_Changes for Version 4.1 (Jan 2022)_**

- updates Status as optional; removes controlled vocabulary
- Clarifies relationship model

**_Changes for Version 4.0 (July 2021)_**

- Incorporation of GEOMG Metadata Editor
- Upgrade to Aardvark Metadata Schema for GeoBlacklight

**_Changes for version 3.3 (May 13, 2020)_**

- Added University of Nebraska
- Reorganized Metadata Elements to match editing template
- Updated the “Update the Collections” section to match new administrative process for tracking records

**_Changes for version 3.2 (Jan 8, 2020)_**

- Added Date Range element

**_Changes for version 3.1 (Dec 19, 2019)_**

- Added collection level records metadata schema

**_Changes for version 3 (Oct, 2019)_**

- GeoNetwork and Omeka deprecated
- all GeoBlacklight records are stored in a master spreadsheet in Google - Sheets
- records are transformed from CSV to GeoBlacklight JSON with a Python script
- additional metadata fields were added for administrative purposes
- IsPartOf field now holds a code pointing to the collection record
- Administrative groupings such as “State agencies geospatial data” are now subjects, not a Collection
- updated editing templates available
- all supplemental metadata can be stored as XML or HTML in project hosted folder
- updated links to collections database 




## Credits

Handbook prepared by:

- Karen Majewicz, Geospatial Product Manager
- Ziying (Gene) Cheng - Graduate Research Assistant
