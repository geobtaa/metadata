# BTAA Specific Entry Guidelines

The BTAA Geoportal has more specific guidelines for some fields from [OpenGeoMetadata](https://opengeometadata.org) (OGM).

## Title
**Maps**: The title for scanned maps is generally left as it was originally cataloged by a participating library. MARC subfields are omitted and can be inserted in the Description field.

**Datasets**: Harvested datasets often are lacking descriptive titles and may need to be augmented with place names. Dates may also be added to the end, but if the dataset is subject to updates, the data should be left off.  Acronyms should be spelled out. The preferred format for dataset titles is:
`Theme [place] {date}`. This punctuation allows for batch processing and splitting title elements.

## Language
Although [Language is optional in the OGM schema](https://opengeometadata.org/docs/ogm-aardvark/language), a three-digit code is required for the BTAA Geoportal.

## Creator
Spell all Acronyms out.

## Publisher
**Maps**: Publisher values for maps are pulled from the original catalog record. Remove subfields for place names and dates.

**Datasets**: The BTAA Geoportal does not use the Publisher field for Datasets.

## Provider
This is the name of the organization hosting the resources. If the organization is part of the BTAA library network, a university icon will display next to the resource's title. However, most Providers will not have an icon.

The BTAA Geoportal has a much longer list of Providers than other GeoBlacklight instances. This is because we are harvesting metadata from external sources, rather than just participating library institutions.

## Bounding Box
Provide Bounding Boxes in this format: **W,S,E,N**

When the record is published to the Geoportal, these coordinates will be programmatically converted to other formats. The Bounding Box field (`dcat_bbox_s`) uses this order: `ENVELOPE(W,E,N,S)`

The Geometry field (`locn_geometry`) uses a WKT format and the coordinate order will be converted to this layout: `POLYGON((W N, E N, E S, W S, W N))`

**Example:**
Metadata CSV: **-120,10,-80,35**

*converts to*

`dcat_bbox_s:` `ENVELOPE(-120,-80,35,10)`

`locn_geometry:` `POLYGON((-120 35, -80 35, -80 10, -120 10, -120 35))`




