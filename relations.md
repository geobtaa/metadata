# Relations and the Collection Model

This document describes how to organize and relate the records in the BTAA Geoportal.

## Collections
The BTAA Geoportal interprets the Resource Class, "Collections," as top-level, custom groupings. 
These reflect our curation activities and priorities.


### Relationship Field
Individual records are linked to Collections using the `Member Of` field. The ID of the parent record is added to the child record only.

### Current Collections

#### General Land Office Township Plats
Plat drawings created from public land surveys completed in the Big Ten Academic Alliance States.

#### Government Open Geospatial Data Collection
Open geospatial datasets, web services, interactive maps, and data portals distributed by a federal, state, county, municipal, or regional agency.

#### Indigenous Lands
Resources and projects that address issues related to indigenous people, territories, reservations, languages, land grants, and more.

#### Libraries Geospatial Data Collection
Geospatial data that has been curated at academic libraries. Many of the datasets are outputs from research projects or sponsored initiatives. This collection also encompasses government data that was curated and archived at a library.
The items in this collection are known to have high quality standards metadata and stable access links.
These records are shared on OpenGeoMetadata under each institution's repository.

#### Libraries Historical Maps Collection
This collection contains scanned images of historical maps held in libraries.
The geographic scope of this collection features a concentration on the states in the Big Ten Academic Alliance region, but also includes maps from all over the world. 
The items in this collection are known to have high quality metadata and stable access links.
These records are shared on OpenGeoMetadata under each institution's repository.

#### Licensed Resources Collection
Licensed resources are authorized for use by an individual university, or by multiple universities in the Big Ten Academic Alliance through a subscription. Access to these databases is paid for by an institution for affiliates to use, unlike free public use data.

#### Public Health Dashboards
Links to dashboards and hubs that track public health statistics related to the Covid-19 Coronavirus pandemic.

#### Research Institutes Geospatial Data Collection
Resources from various nonprofit institutions, commercial entities, and research repositories. The geographic scope is worldwide. The topical focus includes environment, climate, humanitarian issues, and racial equity.

----------------
## Websites
The BTAA Geoportal uses the Resource Class, "Websites," to create parent records for data portals, digital libraries, dashboards, and interactive maps. These often start off as standalone records.
Once the items in a website have been indexed, they will have child records.

### Relationship Field
Individual data layers, maps, or web services  are linked to the Website they came from using the `Is Part Of` field. The ID of the parent record is added to the child record only.

### Current Websites
View all of the current websites in the geoportal at this link: [https://geo.btaa.org/?f%5Bgbl_resourceClass_sm%5D%5B%5D=Websites](https://geo.btaa.org/?f%5Bgbl_resourceClass_sm%5D%5B%5D=Websites)

-----------------
 ## Provider
The BTAA Geoportal populates the `Provider` field with the name of the website or organization from which the item was harvested.

The provider field comes from schema.org, where is is broadly defined as "The service provider, service operator, or service performer; the goods producer."

For many other GeoBlacklight instances, this field is always the name of a university or college and is attached to logo icons. 

### Relationship Field
This value is inserted as plain text into the Provider field. Most of the time, this will match the value displayed in the Is Part Of widget. 

### Current Providers
Use the Provider facet on the Geoportal to browse all of the providers.

------------------
## Multipart Items
Many items in the geoportal are multipart. There may be individual pages from an atlas, sublayers from a larger project, or datasets broken up into more than one download.
In these cases, the `Is Part Of` field is used. As a result, these items many have more than one record that it Is Part Of: the original website and the parent for the multipart items.

### Relationship Field
First, create a parent record describing the top level work. Individual data layers or pages are linked using the `Is Part Of` field. The ID of the parent record is added to the child record only.






