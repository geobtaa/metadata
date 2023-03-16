# Custom Elements


This page documents the custom metadata elements for the GeoBTAA Metadata Profile. These elements extend the [official OpenGeoMetadata (Aardvark) schema](https://opengeometadata.org).

| b1g-id | Label                                         | URI                             | Obligation  |
| ------ | --------------------------------------------- | ------------------------------- | ----------- |
| b1g-01 | [Code](#code)                               | `b1g_code_s`                    | Required    |
| b1g-02 | [Status](#status)                           | `b1g_status_s`                 | Optional    |
| b1g-03 | [Accrual Method](#accrual-method)           | `b1g_dct_accrualMethod_s`      | Required    |
| b1g-04 | [Accrual Periodicity](#accrual-periodicity) | `b1g_dct_accrualPeriodicity_s`| Optional    |
| b1g-05 | [Date Accessioned](#date-accessioned)       | `b1g_dateAccessioned_s`        | Required    |
| b1g-06 | [Date Retired](#date-retired)               | `b1g_dateRetired_s`             | Conditional |
| b1g-07 | [Child Record](#child-record)               | `b1g_child_record_b`           | Conditional    |
| b1g-08 | [Mediator](#mediator)                       | `b1g_dct_mediator_sm`          | Conditional |
| b1g-09 | [Access](#access)                           | `b1g_access_s`                  | Conditional |
| b1g-10 | [Image](#image)                             | `b1g_image_ss`                  | Optional |
| b1g-11 | [GeoNames](#geonames)                       | `b1g_geonames_sm`                  | Optional |
| b1g-12 | [Publication State](#publication-state)     |`b1g_publication_state_s`                  | Required |
| b1g-13 | [Language String](#language-string)         |`b1g_language_sm`                  | Required |
| b1g-14 | [Creator ID](#creator-id)                   |`b1g_creatorID_sm`               |Optional|

## Code

| Label                 | Code                                                                                                                                                                                                                                                                                          |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| URI                   | `b1g_code_s`                                                                                                                                                                                                                                                                                    |
| Profile ID            | b1g-01                                                                                                                                                                                                                                                                                        |
| Obligation            | Required                                                                                                                                                                                                                                                                                      |
| Multiplicity          | 1-1                                                                                                                                                                                                                                                                                           |
| Field type            | string                                                                                                                                                                                                                                                                                        |
| Purpose               | To group records based upon their source                                                                                                                                                                                                                                                      |
| Entry Guidelines      | Codes are developed by the metadata coordinator and indicate the provider, the type of institution hosting the resources, and a numeric sequence number. For more details, see [Code Naming Schema ](codeNamingSchema.md)                                                                                                                                     |
| Commentary            | This administrative field is used to group and track records based upon where they are harvested. This is frequently an identical value to "Member Of". The value will differ for records that are retired (these are removed from "Member Of") and records that are part of a subcollection. |
| Controlled Vocabulary | yes-strict                                                                                                                                                                                                                                                                                    |
| Example value         | 12d-01                                                                                                                                                                                                                                                                                        |
| Element Set           | B1G                                                                                                                                                                                                                                                                                           |

## Status

| Label                 | Status                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| URI                   | `b1g_status_s `                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Profile ID            | b1g-02                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Obligation            | Optional                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Multiplicity          | 0-1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Field type            | string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Purpose               | To indicate if a record is currently active, retired, or unknown. It can also be used to indicate if individual data layers from website has been indexed in the Geoportal.                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Entry Guidelines      | Plain text string is acceptable                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Commentary            | This is a legacy admin field that was previously used to track published vs retired items. The current needs are still TBD.  |
| Controlled Vocabulary | no                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Example value         | Active                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Element Set           | B1G                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |


## Accrual Method

| Label                 | Accrual Method                                                                                                                                                            |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| URI                   | `b1g_dct_accrualMethod_s`                                                                                                                                                   |
| Profile ID            | b1g-03                                                                                                                                                                    |
| Obligation            | Required                                                                                                                                                                  |
| Multiplicity          | 1-1                                                                                                                                                                       |
| Field type            | string                                                                                                                                                                    |
| Purpose               | To describe how the record was obtained                                                                                                                                   |
| Entry Guidelines      | Some values, such as "ArcGIS Hub" should be entered consistently. Others may be more descriptive, such as "Manually entered from text file."                              |
| Commentary            | This allows us to find all of the ArcGIS records in one search. It also can help track records that have been harvested via different methods within the same collection. |
| Controlled Vocabulary | no                                                                                                                                                                        |
| Example value         | ArcGIS Hub                                                                                                                                                                |
| Element Set           | B1G/ Dublin Core                                                                                                                                                          |

## Accrual Periodicity

| Label                 | Accrual Periodicity                                                                      |
|-----------------------|------------------------------------------------------------------------------------------|
| URI                   | `b1g_dct_accrualPeriodicity_s`                                                             |
| Profile ID            | b1g-04                                                                                   |
| Obligation            | Optional                                                                                 |
| Multiplicity          | 0-1                                                                                      |
| Field type            | string                                                                                   |
| Purpose               | To indicate how often a collection is reaccessioned                                      |
| Entry Guidelines      | Enter one of the following values: Annually, Semiannually, Quarterly, Monthly, As Needed |
| Commentary            | This field is primarily for collection level records.                                    |
| Controlled Vocabulary | yes-not strict                                                                           |
| Example value         | As Needed                                                                                |
| Element Set           | B1G/ Dublin Core                                                                         |

## Date Accessioned

| Label                 | Date Accessioned                                                                                                             |
|-----------------------|------------------------------------------------------------------------------------------------------------------------------|
| URI                   | `b1g_dateAccessioned_s`                                                                                                        |
| Profile ID            | b1g-05                                                                                                                       |
| Obligation            | Required                                                                                                                     |
| Multiplicity          | 1-1                                                                                                                          |
| Field type            | string                                                                                                                       |
| Purpose               | To store the date a record was harvested                                                                                     |
| Entry Guidelines      | Enter the date a record was harvested OR when it was added to the geoportal using the format yyyy-mm-dd                      |
| Commentary            | This field allows us to track how many records are ingested into the portal in a given time period and to which collections. |
| Controlled Vocabulary | no                                                                                                                           |
| Example value         | 2021-01-01                                                                                                                   |
| Element Set           | B1G                                                                                                                          |

## Date Retired

| Label                 | Date Retired                                                                                                                 |
|-----------------------|------------------------------------------------------------------------------------------------------------------------------|
| URI                   | `b1g_dateRetired_s`                                                                                                            |
| Profile ID            | b1g-06                                                                                                                       |
| Obligation            | Conditional                                                                                                                  |
| Multiplicity          | 0-1                                                                                                                          |
| Field type            | string                                                                                                                       |
| Purpose               | To store the date the record was removed from the geoportal public interface                                                 |
| Entry Guidelines      | Enter the date a record was removed from the geoportal                                                                       |
| Commentary            | This field allows us to track how many records have been removed from the geoportal interface by time period and collection. |
| Controlled Vocabulary | no                                                                                                                           |
| Example value         | 2021-01-02                                                                                                                   |
| Element Set           | B1G                                                                                                                          |

## Child Record

| Label                 | Child Record                                                                                                                                                                      |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| URI                   | `b1g_child_record_b`                                                                                                                                                                |
| Profile ID            | b1g-07                                                                                                                                                                            |
| Obligation            | Optional                                                                                                                                                                          |
| Multiplicity          | 0-1                                                                                                                                                                               |
| Field type            | string boolean                                                                                                                                                                    |
| Purpose               | To apply an algorithm to the record that causes it to appear lower in search results                                                                                              |
| Entry Guidelines      | Only one of two values are allowed: true or false                                                                                                                                 |
| Commentary            | This is used to lower a record's placement in search results. This can be useful for a large collection with many similar metadata values that might clutter a user's experience. |
| Controlled Vocabulary | string boolean                                                                                                                                                                    |
| Example value         | true                                                                                                                                                                              |
| Element Set           | B1G                                                                                                                                                                               |

## Mediator

| Label                 | Mediator                                                                                                                                                     |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| URI                   | `b1g_dct_mediator_sm`                                                                                                                                          |
| Profile ID            | b1g-08                                                                                                                                                       |
| Obligation            | Conditional                                                                                                                                                  |
| Multiplicity          | 0-0 or 1-*                                                                                                                                                   |
| Field type            | string                                                                                                                                                       |
| Purpose               | To indicate the universities that have licensed access to a record                                                                                           |
| Entry Guidelines      | The value for this field should be one of the names for each institution that have been coded in the GeoBlacklight application.                              |
| Commentary            | This populates a facet on the search page so that users can filter to only databases that they are able log into based upon their institutional affiliation. |
| Controlled Vocabulary | yes                                                                                                                                                          |
| Example value         | University of Wisconsin-Madison                                                                                                                              |
| Element Set           | B1G/ Dublin Core                                                                                                                                             |

## Access

| Label                 | Access                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| URI                   | `b1g_access_s`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Profile ID            | b1g-09                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Obligation            | Conditional                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Multiplicity          | 0-0 or 1-1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Field type            | string JSON                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Purpose               | To supply the links for restricted records                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Entry Guidelines      | The field value is an array of key/value pairs, with keys representing an insitution code and values the URL for the library catalog record. See the Access Template for entry.                                                                                                                                                                                                                                                                                                                             |
| Commentary            | This field is challenging to construct manually, is it is a JSON string of institutional codes and URLs. The codes are used instead of the actual names in order to make the length of the field more manageable and to avoid spaces.                                                                                                                                                                                                                                                                       |
| Controlled Vocabulary | no                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Example value         | {\"03\":\"https://purl.lib.uiowa.edu/PolicyMap\",\"04\":\"https://www.lib.umd.edu/dbfinder/id/UMD09180\",\"05\":\"https://primo.lib.umn.edu/permalink/f/1q7ssba/UMN_ALMA51581932400001701\",\"06\":\"http://catalog.lib.msu.edu/record=b10238077~S39a\",\"07\":\"https://search.lib.umich.edu/databases/record/39117\",\"09\":\"https://libraries.psu.edu/databases/psu01762\",\"10\":\"https://digital.library.wisc.edu/1711.web/policymap\",\"11\":\"https://library.ohio-state.edu/record=b7869979~S7\"} |
| Element Set           | B1G                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |

## Image

| Label                 | Image                                                                                                                                                     |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| URI                   | `b1g_image_ss`                                                                                                                                          |
| Profile ID            | b1g-10                                                                                                                                                       |
| Obligation            | Optional                                                                                                                                                  |
| Multiplicity          | 0-0 or 0-1                                                                                                                                                   |
| Field type            | stored string (URL)                                                                                                                                                       |
| Purpose               | To show a thumbnail on the search results page                                                                                          |
| Entry Guidelines      | Enter an image file using a secure link (https). Acceptable file types are JPEG or PNG                            |
| Commentary            | This link is used to harvest an image into the Geoportal server for storage and display. Once it has been harvested, it will remain in storage, even if the orginal link to the image stops working. |
| Controlled Vocabulary | no                                                                                                                                                          |
| Example value         | https://gis.allencountyohio.com/GIS/Image/countyseal.jpg                                                                                                                              |
| Element Set           | B1G                                                                                                                                            |

## GeoNames

| Label                 | GeoNames                                                                                                                                                     |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| URI                   | `b1g_geonames_sm`                                                                                                                                           |
| Profile ID            | b1g-11                                                                                                                                                       |
| Obligation            | Optional                                                                                                                                                  |
| Multiplicity          | 0-*                                                                                                                                                  |
| Field type            | stored string (URI)                                                                                                                                                       |
| Purpose               | To indicate a URI for a place name from the [GeoNames database](https://www.geonames.org)                                                                                         |
| Entry Guidelines      | Enter a value in the format "http://sws.geonames.org/`URI`"                            |
| Commentary            | This URI provides a linked data value for one or more place names. It is optional as there is currently no functionality tied to it in the GeoBlacklight application |
| Controlled Vocabulary | yes                                                                                                                                                          |
| Example value         | https://sws.geonames.org/2988507                                                                                                                           |
| Element Set           | B1G                                                                                                                                            |

## Publication State

| Label                 | Publication State                                                                                                                                                     |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| URI                   | `b1g_publication_state_s`                                                                                                                                          |
| Profile ID            | b1g-12                                                                                                                                                       |
| Obligation            | Required                                                                                                                                                 |
| Multiplicity          | 1-1                                                                                                                                                  |
| Field type            | string |                                                                                                                                     
| Purpose               | To communicate to Solr if the item is public or hidden                                                                                      |
| Entry Guidelines      | Use the dropdown or batch editing functions to change the state              |
| Commentary            | When items are first added to GEOMG, they are set as Draft by default. When they are ready to be published, they can be manually changed to Published. If the record is retired or needs to be hidden, it can be changed to Unpublished
| Controlled Vocabulary | yes                                                                                                                                                          |
| Example value         | Draft                                                                                                                           |
| Element Set           | B1G                                                                                                                                          |


## Language string

| Label                 | Language string                                                                                                                                                     |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| URI                   | `b1g_language_sm`                                                                                                                                          |
| Profile ID            | b1g-13                                                                                                                                                       |
| Obligation            | Required                                                                                                                                                 |
| Multiplicity          | 1-*                                                                                                                                                  |
| Field type            | string |                                                                                                                                     
| Purpose               | To display the spelled out string (in English) of a language code to users                                                                                      |
| Entry Guidelines      | This field is automatically generated from the [Language](https://opengeometadata.org/docs/ogm-aardvark/language) field in the main form              |
| Commentary            | The OGM schema specified using a 3-digit code to indicate lanuage. In order to display this to users, it needs to be translated into a human-readable string. 
| Controlled Vocabulary | yes                                                                                                                                                          |
| Example value         | French                                                                                                                          |
| Element Set           | B1G                                                                                                                                          |

## Creator ID

| Label                 | Creator ID                                                                                                                                                     |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| URI                   | `b1g_creatorID_sm`                                                                                                                                          |
| Profile ID            | b1g-14                                                                                                                                                       |
| Obligation            | Optional                                                                                                                                                 |
| Multiplicity          | 0-*                                                                                                                                                  |
| Field type            | string |                                                                                                                                     
| Purpose               | To track the URI of a creator value                                                                                     |
| Entry Guidelines      | This field is entered as a URI representing an authority record            |
| Commentary            | These best practices recommend consulting one or two name registries when deciding how to standardize names of creators: the Faceted Application of Subject Terminology (FAST) or the Library of Congress Name Authority File (LCNAF). FAST is a controlled vocabulary based on the Library of Congress Subject Headings (LCSH) that is well-suited to the faceted navigation of the Geoportal. The LCNAF is an authoritative list of names, events, geographic locations and organizations used by libraries and other organizations to collocate authorized creator names to make searching and browsing easier.
| Controlled Vocabulary | yes                                                                                                                                                          |
| Example value         | fst02013467                                                                                                                          |
| Element Set           | B1G                                                                                                                                          |