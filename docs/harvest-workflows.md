HARVEST WORKFLOWS  
the prefix indicates the primary strategy we use to process the records, even when it is a multistep workflow:

* **template** : creating the records directly in the GeoBTAA metadata profile. Typically, we are using a CSV or even the GBL Admin form view.  
* **tools** : relying on existing metadata software tools & apps to obtain and/or process the metadata.  Right now, the tools are the [OAI validator,](https://validator.oaipmh.com) [OpenRefine](https://openrefine.org), and [MarcEdit](https://marcedit.reeset.net).  
* **py** : python modules and scripts do most of the work. Any additional steps should be described within the code or its accompanying documentation

| Harvest Workflow | Description |
| :---- | :---- |
| template\_website| author a website only record directly in the GeoBTAA profile |
| template\_children | author a website and children records directly in the GeoBTAA profile |
| template\_csv | receive a spreadsheet of metadata and do some minor cleanup |
| tools\_oai\_openrefine | access the OAI-PMH API [OAI validator](https://validator.oaipmh.com); export an XML; load it into OpenRefine for cleanup and conversion to CSV |
| tools\_marcedit | use the MarcEdit tool to convert MARC records into a CSV |
| py\_arcgis\_hub | ArcGIS Hubs |
| py\_arcgis\_online | ArcGIS Online data collections |
| py\_socrata | Socrata portals |
| py\_ckan | CKAN portals |
| py\_hdx | Humanitarian Data Exchange CKAN portal |
| py\_ogm\_wisc | Individual JSONs in UW-Madison’s GBL 1.0 metadata  |
| py\_ogm\_gbl1 | Individual JSONs in the OGM GBL 1.0 metadata |
| py\_ogm\_aardvark | individual JSONs in the OGM Aardvark metadata |
| py\_pasda | PASDA custom data portal (HTML parser) |
| py\_isgs | ISGS custom data portal  (HTML parser) |
| py\_umedia | UMN UMedia modified Blacklight portal |
| py\_opex | OPEX / MODs files from Michigan |
| py\_oaipmh | OAI-PMH endpoints (use Python instead of tools) |
| py\_mods | MODS metadata files |
|  |  |
|  |  |

