The [GeoBTAA Metadata Template](https://z.umn.edu/b1g-template) ([https://z.umn.edu/b1g-template](https://z.umn.edu/b1g-template)) is a set of spreadsheets that are formatted for our metadata editor, GEOMG. 

Users will need to make a copy of the spreadsheet to use for editing.  In some cases, the Metadata Coordinator can provide a customized version of the sheets for specific collections.

The Template contains the following tabs:

- Map Template
- Dataset Template
- Website Record Template
- Values: All of the controlled vocabulary values for the associated fields.
- Access Links and Multiple Downloads: Fields for adding secondary tables.

!!! Warning "Note"

	The input format for some fields in this template may differ from how the field is documented in [OpenGeoMetadata](https://opengeometadata.org). These differences are intended to make it easier to enter values, which will be transformed when we upload the record to GEOMG.

	- **Bounding Box** coordinates should be entered as `W,S,E,N`. The coordinates are automatically transformed to a different order `ENVELOPE(W,E,N,S)`. Read more under the [Local Input Guidelines](input-guidelines.md).

	- **Date Range **should be entered as `yyyy-yyyy`. This is automatically transformed to [yyyy TO yyyy].

	- External links are added separately under column headers for the type of link. These are combined into the `dct_references_s` field as a string of key:value pairs.