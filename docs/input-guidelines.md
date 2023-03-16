For the following elements, the GeoBTAA Metadata Profile has input guidelines beyond what is documented in the OpenGeoMetadata schema:

### Title
**Maps**: The title for scanned maps is generally left as it was originally cataloged by a participating library. MARC subfields are omitted and can be inserted in the Description field.

**Datasets**: Harvested datasets often are lacking descriptive titles and may need to be augmented with place names. Dates may also be added to the end, but if the dataset is subject to updates, the data should be left off.  Acronyms should be spelled out. The preferred format for dataset titles is:
`Theme [place] {date}`. This punctuation allows for batch processing and splitting title elements.

### Language
Although [Language is optional in the OGM schema](https://opengeometadata.org/docs/ogm-aardvark/language), a three-digit code is required for the BTAA Geoportal.

### Creator
When possible, Creators should be drawn from a value in the [Faceted Application of Subject Terminology (FAST)](https://www.oclc.org/research/areas/data-science/fast.html).

### Creator ID
If the Creator value is from a name authority, insert the ID in this field.

### Publisher
**Maps**: Publisher values for maps are pulled from the original catalog record. Remove subfields for place names and dates.

**Datasets**: The BTAA Geoportal does not use the Publisher field for Datasets.

### Provider
This is the name of the organization hosting the resources. If the organization is part of the BTAA library network, a university icon will display next to the resource's title. However, most Providers will not have an icon.

### Spatial Coverage
This should be in the format used by the [Faceted Application of Subject Terminology (FAST)](https://www.oclc.org/research/areas/data-science/fast.html).  

For US counties and cities, the format should be `state--county` or `state--city`. The state itself should also be included. Examples:

!!! Example
	
	- Wisconsin--Dane County

	- Wisconsin--Madison

	- Wisconsin


### Bounding Box
On the Metadata Editing Template, provide Bounding Boxes in this format: **W,S,E,N** This order matches the DCAT API and is how the Klokan Bounding Box provides coordinates with their "CSV" setting.

This format will be programmatically converted to other formats when it is published to the Geoportal:

 - The OpenGeoMetadata Bounding Box field (`dcat_bbox_s`) uses this order: `ENVELOPE(W,E,N,S)`

 - The OpenGeoMetadata Geometry field (`locn_geometry`) uses a WKT format and the coordinate order will be converted to this layout: `POLYGON((W N, E N, E S, W S, W N))`

 
 - The OpenGeoMetadata Centroid field (`dcat_centroid`) will be calculated to display longitude,latitude.

!!! example

    Metadata CSV: **-120,10,-80,35**

    converts to

    `dcat_bbox_s:` `ENVELOPE(-120,-80,35,10)`

    `locn_geometry:` `POLYGON((-120 35, -80 35, -80 10, -120 10, -120 35))`
    
    `dcat_centroid`: `"22.5,-100.0"`