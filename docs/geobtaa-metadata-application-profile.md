---
hide:
  - toc
---

The GeoBTAA Metadata Application Profile consists of the following components:

### 1. OpenGeoMetadata Elements

- The BTAA Geoportal uses the OpenGeoMetadata Schema for each resource. 
- The current version of OpenGeoMetadata is called 'Aardvark'. 
- This lightweight schema was designed specifically for the GeoBlacklight application and is geared towards discoverability. 
- The GeoBTAA Metadata Profile aligns with all of the guidelines and recommendations in the official OpenGeoMetadata documentation. 
- **The schema is documented on the [OpenGeoMetadata website :octicons-link-external-16:](https://opengeometadata.org/docs/ogm-aardvark).** 

### 2. Custom Elements

- The GeoBTAA profile includes custom fields for lifecycle tracking and administration
- These elements are generally added to the record by admin staff. When they appear on editing templates, they are grayed out.
- They all start with the namespace `b1g`
- **See the [Custom Elements page](b1g-custom-elements.md) for more detail**


### 3. GeoBTAA Input Guidelines

- For the content in some fields, the GeoBTAA profile has specific guidelines that extends or differs from what is documented in the OpenGeoMetadata schema.

- **See the [GeoBTAA Input Guidelines page](input-guidelines.md) for more detail**




!!!Info
	The GeoBTAA Metadata Template can be found at [https://z.umn.edu/b1g-template](https://z.umn.edu/b1g-template)