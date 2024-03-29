## Purpose

To scan the [DCAT API](https://resources.data.gov/resources/dcat-us/) of Socrata Data Portals and return the metadata for all suitable items as a CSV file in the GeoBTAA Metadata Application Profile.

Note: This recipe is very similar to the ArcGIS Hubs Scanner.

!!! warning " "

	This recipe includes steps that use the metadata toolkit [GBL Admin](https://geobtaa.github.io/metadata/GBL Admin/). Access to GBL Admin is restricted to UMN BTAA-GIN staff and requires a login account. External users can create their own list or use one provided in this repository.

``` mermaid
graph TB

A{{STEP 1. <br>Download socrataPortals.csv}}:::green --> B[[STEP 2. <br>Run Jupyter Notebook harvest script]]:::green;
B --> C{Did the script run successfully?}:::white;
C --> |No| D[Troubleshoot]:::yellow;
D --> H{Did the script stall because of a portal?}:::white;
H --> |Yes| I[Remove or update the portal from the list]:::yellow;
H --> |No & I can't figure it out.| F[Refer issue back to Product Manager]:::red;
H --> |No| J[Try updating your Python modules or investigating the error]:::yellow;
J --> B;
I --> A;
C --> |Yes| K[[STEP 3. Validate and Clean]]:::green; 
K --> E[STEP 4. <br>Publish/unpublish records in GBL Admin]:::green; 

classDef green fill:#E0FFE0
classDef yellow fill:#FAFAD2
classDef red fill:#E6C7C2
classDef white fill:#FFFFFF

```


## Step: Download the list of active Socrata Data Portals

We maintain a list of active Socrata Hub sites in GBL Admin. 

!!! tip inline end "Shortcut"

	[Pre-formatted GBL Admin query link](https://GBL Admin.lib.umn.edu/documents?f%5Bb1g_publication_state_s%5D%5B%5D=published&f%5Bdct_format_s%5D%5B%5D=Socrata+data+portal&q=&rows=20&sort=score+desc)

1. Go to the [GBL Admin](https://GBL Admin.lib.umn.edu) dashboard
2. Use the Advanced Search to filter for items with these parameters:
  	 - Format: "Socrata data portal"
3. Select all the results and click Export -> CSV
4. Download the CSV and rename it `socrataPortals.csv`


!!! info
    
	Exporting from GBL Admin will produce a CSV containing all of the metadata associated with each Hub. For this recipe, the only fields used are:

	* **ID**: Unique code assigned to each portal. This is transferred to the "Is Part Of" field for each dataset.
	* **Title**: The name of the Hub. This is transferred to the "Provider" field for each dataset
	* **Publisher**: The place or administration associated with the portal. This is applied to the title in each dataset in brackets
	* **Spatial Coverage**: A list of place names. These are transferred to the Spatial Coverage for each dataset
	* **Member Of**: a larger collection level record. Most of the Hubs are either part of our [Government Open Geospatial Data Collection](https://geo.btaa.org/catalog/ba5cc745-21c5-4ae9-954b-72dd8db6815a) or the [Research Institutes Geospatial Data Collection](https://geo.btaa.org/catalog/b0153110-e455-4ced-9114-9b13250a7093)

	It is not necessary to take extra time and manually remove the unused fields, because the Jupyter Notebook code will ignore them.

-------------------

## Step 2: Run the harvest script

1. Start Jupyter Notebook and navigate to the Recipes directory.
2. Open [R-02_socrata.ipynb](https://github.com/geobtaa/harvesting-guide/blob/main/recipes/R-02_socrata)
3. Move the downloaded file `socrataPortals.csv` into the same directory as the Jupyter Notebook.


## Troubleshooting (as needed)

1. Visit the URL for the Socrata Portal to check and see if the site is down, moved, etc. 
2. **If a site is missing**
	- Unpublish it from GBL Admin and indicate the Date Retired, and make a note in the Status field.  
3. Start over from Step 1.

## Step 3: Validate and Clean

Although the harvest notebook will produce valide metadata for most of the items, there may still be some errors. [Run the cleaning script](clean.md) to ensure that the records are valid before we try to ingest them into GBL Admin.


## Step 4: Upload to GBL Admin

1. Review the previous upload. Check the Date Accessioned field of the last harvest and copy it. 
2. Upload the new CSV file. This will overwrite the Date Accessioned value for any items that were already present.
3. Use the old Date Accessioned value to search for the previous harvest date. 
4. Unpublish the ones that have the old date in the Date Accessioned field 5. Record this number in the GitHub issue for the scan under Number Deleted
6. Look for records in the uploaded batch that are still "Draft" - these are new records. 
7. Publish them and record this number in the GitHub issue under Number Added
