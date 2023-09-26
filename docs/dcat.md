# DCAT Metadata

## Overview

DCAT (Data Catalog Vocabulary) is metadata schema for web-based data catalogs. It is intended to facilitate interoperability and many data platforms offer a DCAT API for metadata sharing.

The most up-to-date documentation of the schema can be found here: https://www.w3.org/TR/vocab-dcat-3/

Documentation that is older, but still in use for United States portals can be found here: https://resources.data.gov/resources/dcat-us/


## JSON Structure

Many of the data platforms in the United States use a DCAT profile documented as "Project Open Data Catalog".  The following JSON template shows the generic structure of a DCAT JSON document:

```

{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "id": "https://project-open-data.cio.gov/v1.1/schema/catalog.json#",
  "title": "Project Open Data Catalog",
  "description": "Validates an entire collection of Project Open Data metadata JSON objects. Agencies produce said collections in the form of Data.json files.",
  "type": "object",
  "dependencies": {
    "@type": [
      "@context"
    ]
  },
  "required": [
    "conformsTo",
    "dataset"
  ],
  "properties": {
    "@context": {
      "title": "Metadata Context",
      "description": "URL or JSON object for the JSON-LD Context that defines the schema used",
      "type": "string",
      "format": "uri"
    },
    "@id": {
      "title": "Metadata Catalog ID",
      "description": "IRI for the JSON-LD Node Identifier of the Catalog. This should be the URL of the data.json file itself.",
      "type": "string",
      "format": "uri"
    },
    "@type": {
      "title": "Metadata Context",
      "description": "IRI for the JSON-LD data type. This should be dcat:Catalog for the Catalog",
      "enum": [
        "dcat:Catalog"
      ]
    },
    "conformsTo": {
      "description": "Version of Schema",
      "title": "Version of Schema",
      "enum": [
        "https://project-open-data.cio.gov/v1.1/schema"
      ]
    },
    "describedBy": {
      "description": "URL for the JSON Schema file that defines the schema used",
      "title": "Data Dictionary",
      "type": "string",
      "format": "uri"
    },
    "dataset": {
      "type": "array",
      "items": {
        "$ref": "dataset.json",
        "minItems": 1,
        "uniqueItems": true
      }
    }
  }
}
```


##  How to find the DCAT API

Most sites, including **Socrata**:

To find a data API, a good place to start is to try appending the string "/data.json" to the base URL.  If available, your browser will display the data catalog as a JSON file.

**ArcGIS Hubs**:

* **Version 1**: append the string "/api/feed/dcat-us/1.1.json". [Esri made this change was made in 2022](https://www.esri.com/arcgis-blog/products/arcgis-hub/announcements/upcoming-changes-to-dcat-configurations-on-arcgis-hub-sites/) to differentiate the older DCAT version from 2.0. Our harvest recipe current uses this version.
* **Version 2**: use the string "api/feed/dcat-ap/2.0.1.json". We plan to evaluate the newer format and will consider migrating our recipe in 2024.








