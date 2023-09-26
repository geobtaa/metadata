# Overview of CKAN Data Portals and its APIs

"CKAN is a tool for making open data websites". (https://docs.ckan.org/en/2.10/user-guide.html#what-is-ckan) CKAN is often utilized by governments and organizations and is an open-source alternative to platforms like ArcGIS Hubs.

## Content Organization

The content organization model of a CKAN site uses the term **Datasets** for each item record. A Dataset may have multiple **Resources**, such as downloadable files, thumbnails, supplemental metadata files, and external links. This model can give data providers flexibility on how they organize their files, but can be challenging for harvesting into the BTAA Geoportal. 

Unlike CKAN, GeoBlacklight was designed to have only *one* data file per record, so it can be challenging to programmatically sort through all of the possible access points for a **Dataset** and attach them to a single record in GeoBlacklight. To mitigate this, we use the [multiple downloads option when possible](/recipes/secondary-tables/).

## Metadata

CKAN metadata contains several basic fields (documented at https://ckan.org/features/metadata) along with an "extras" group that can be customized by site. Some portals have many custom fields in "extras" and some do not use them at all.


## API

CKAN offers several types of APIs for sharing metadata. The most useful one for the BTAA Geoportal is the `package_search`, which can be accessed by appending "api/3/action/package_search" to a base URL. 

!!! example

	https://demo.ckan.org/api/3/action/package_search
