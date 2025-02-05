The [GeoBTAA Metadata Template](https://z.umn.edu/b1g-template) ([https://z.umn.edu/b1g-template](https://z.umn.edu/b1g-template)) is a set of spreadsheets that are formatted for our metadata editor, GBL Admin. 

Users will need to make a copy of the spreadsheet to use for editing.  In some cases, the Metadata Coordinator can provide a customized version of the sheets for specific collections.

The Template contains the following tabs:

- `Primary Template minimal`
:	This tab provides the essential fields for most collections.

- `Primary Template full`
: 	This tab contains all of fields in our profile and is useful for records with more extensive metadata.
	
- `Distributions Template`
:	This tab is for each resource's links, including landing pages, downloads, web services, and supplemental documentation.
	
- `Field Definitions`
:	This lists all of the fields, their definitions, and key attributes.

- `Licensed Access Links`
:	A special template for uploading access links for licensed databases
	
- `Controlled Vocabulary`
:	A list of the acceptable values for certain fields. This tab powers the dropdown fields in the templates.

!!! Warning "Note"

	The input format for some fields in this template may differ from how the field is documented in [OpenGeoMetadata](https://opengeometadata.org). These differences are intended to make it easier to enter values, which will be transformed when we upload the record to GBL Admin.

	- **Bounding Box** coordinates should be entered as `W,S,E,N`. The coordinates are automatically transformed to a different order `ENVELOPE(W,E,N,S)`. Read more under the [Local Input Guidelines](input-guidelines.md).

	- **Date Range **should be entered as `yyyy-yyyy`. This is automatically transformed to [yyyy TO yyyy].
