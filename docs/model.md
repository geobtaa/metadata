---
hide:
  - toc
---

# Content Organization Model

GeoBlacklight organizes records with a network model rather than with a hierarchical model. It is a flat system whereby every database entry is a "Layer" and uses the same metadata fields. Unlike many digital library applications, it does not have different types of records for entities such as "communities," "collections," or "groups." As a result, it does not present a breadcrumb navigation structure, and all records appear in the same catalog directory with the URL of https:geo.btaa.org/catalog/`ID`.

Instead of a hierarchy, GeoBlacklight relates records via metadata fields. These fields include `Member Of`, `Is Part Of`, `Is Version Of`, `Source`, and a general `Relation`. This flexibility allows records to be presented in several different ways. For example, records can have multiple parent/child/grandchild/sibling relationships. In addition, they can be nested (i.e., a collection can belong to another collection). They can also connect data layers about similar topics or represent different years in a series.

The following diagram illustrates how the BTAA Geoportal organizes records. The connecting arrow lines indicate the name of the relationship. The labels reflect each record's [Resource Class](https://opengeometadata.org/docs/ogm-aardvark/resource-class) (**Collections**, **Websites**, **Datasets**, **Maps**, **Web services**).

![Chart](./images/contentOrganization.png)








