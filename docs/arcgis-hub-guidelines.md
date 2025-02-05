# BTAA-GIN Scanning Guidelines for ArcGIS Hubs

`Version 2.0 - April 24, 2023`


## Overview

This document describes the BTAA-GIN Scanning Guidelines for ArcGIS Hubs, including eligible sites and records, harvest schedules, and remediation work. This policy may change at any time in response to updates to the ArcGIS Hub architecture platform and/or the BTAA-GIN harvesting and remediation processes.

## Eligible sites

**Guideline**: Any ArcGIS Hub (Hub) that serves public geospatial data is eligible for inclusion in the BTAA Geoportal (“the Geoportal”). Our scope includes public Hubs from the states in the BTAA geographic region and Hubs submitted by Team Members that are of interest to BTAA researchers. 

**Explanation**: See the [BTAA-GIN Collection Development Policy](https://geobtaa.github.io/metadata/collection-development-policy/) for more details.

## Eligible records

**Guideline**: The only records that will be harvested from Hubs are Esri REST Services of the type Map Service, Feature Service, or Image Service. This is further restricted to only items that are harvestable through the DCAT API. By default, the following records types will not be accessioned on a regular basis:

* Web applications
* Nonspatial data, tabular data, PDFs
* Single records that describe many different associated files to download, such as imagery services with a vast number of sublayers

**Explanation**: Hubs are structured to automatically create item records from submitted Esri REST services.  However, Hub administrators are able to manually add records for other types of resources, such as external websites or documents.  These may not be spatial datasets and may not have consistently formed metadata or access links, which impedes automated accessioning.

## Frequency

**Guideline**: The Hubs included in the Geoportal will be scanned weekly to harvest complete lists of eligible records. The list will be published and overwrite the previous scan.

**Explanation**: Broken links negatively impact user experience. Over the course of a week, as many as 10% of the ArcGIS Hub records in the Geoportal can break or include outdated information. 

## Metadata Remediation

**Guideline**: The harvesting script, `R-01_arcgis-hubs`, programmatically performs all of the remediation for each record. 

**Explanation**: We now scan a large number of ArcGIS Hubs, which makes manual remediation unrealistic.  This is in contrast to the previous policy established in 2018, when our collection was smaller.


!!! info

	This document replaces the [BTAA GDP Accession Guidelines for ArcGIS Open Data Portals, version 1.0](arcgis-harvest-policy-2018.md).

