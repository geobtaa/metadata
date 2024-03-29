## Purpose

To scan the [DCAT 1.1 API](https://resources.data.gov/resources/dcat-us/) of ArcGIS Hubs and return the metadata for all suitable items as a CSV file in the GeoBTAA Metadata Application Profile.

!!! warning " "

	This recipe includes steps that use the GBL Admin toolkit. Access to this tool is restricted to UMN BTAA-GIN staff and requires a login account. External users can create their own list or use one provided in this repository.
	

``` mermaid
graph TB

A{{STEP 1. <br>Download arcHubs.csv}}:::green --> B[[STEP 2. <br>Run Jupyter Notebook harvest script]]:::green;
B --> C{Did the script run successfully?};
C --> |No| D[Troubleshoot]:::yellow;
D --> H{Did the script stall because of a Hub?};
H --> |Yes| I[Refer to the page Update ArcGIS Hubs]:::yellow;
H --> |No & I can't figure it out.| F[Refer issue back to Product Manager]:::red;
H --> |No| J[Try updating your Python modules or investigating the error]:::yellow;
J --> B;
I --> A;
C --> |Yes| K[[STEP 3. Validate and Clean]]:::green; 
K --> E[STEP 4. <br>Publish/unpublish records in GBL Admin]:::green; 


classDef green fill:#E0FFE0
classDef yellow fill:#FAFAD2
classDef red fill:#E6C7C2


classDef questionCell fill:#fff,stroke:#333,stroke-width:2px;
class C,H questionCell;

```

## Step 1: Download the list of active ArcGIS Hubs

We maintain a list of active ArcGIS Hub sites in GBL Admin. 

!!! tip inline end "Shortcut"

	[Pre-formatted GBL Admin query link](https://geo.btaa.org/admin/documents?f%5Bb1g_dct_accrualMethod_s%5D%5B%5D=DCAT+US+1.1&f%5Bgbl_resourceClass_sm%5D%5B%5D=Websites&rows=20&sort=score+desc)

1. Go to the Admin (https://geo.btaa.org/admin) dashboard
2. Filter for items with these parameters:
  	 - Resource Class: Websites
  	 - Accrual Method: DCAT US 1.1
3. Select all the results and click Export -> CSV
4. Download the CSV and rename it `arcHubs.csv`



!!! info
    
	Exporting from GBL Admin will produce a CSV containing all of the metadata associated with each Hub. For this recipe, the only fields used are:

	* **ID**: Unique code assigned to each portal. This is transferred to the "Is Part Of" field for each dataset.
	* **Title**: The name of the Hub. This is transferred to the "Provider" field for each dataset
	* **Publisher**: The place or administration associated with the portal. This is applied to the title in each dataset in brackets
	* **Spatial Coverage**: A list of place names. These are transferred to the Spatial Coverage for each dataset
	* **Member Of**: a larger collection level record. Most of the Hubs are either part of our [Government Open Geospatial Data Collection](https://geo.btaa.org/catalog/ba5cc745-21c5-4ae9-954b-72dd8db6815a) or the [Research Institutes Geospatial Data Collection](https://geo.btaa.org/catalog/b0153110-e455-4ced-9114-9b13250a7093)

	However, it is not necessary to take extra time and manually remove the extra fields, because the Jupyter Notebook code will ignore them.

-------------------

## Step 2: Run the harvest script

1. Start Jupyter Notebook and navigate to the Recipes directory.
2. Open [R-01_arcgis-hubs.ipynb](https://github.com/geobtaa/harvesting-guide/blob/main/recipes/R-01_arcgis-hubs)
3. Move the downloaded file `arcHubs.csv` into the same directory as the Jupyter Notebook.
4. Run all cells.

??? info "Expand to read about the R-01_arcgis-hubs.ipynb Jupyter Notebook"

	This code reads data from `hubFile.csv` using the `csv.DictReader` function. It then iterates over each row in the file and extracts values from specific columns to be used later in the script.

	For each row, the script also defines default values for a set of metadata fields. It then checks if the URL provided in the CSV file exists and is a valid JSON response. If the response is not valid, the script prints an error message and continues to the next row. Otherwise, it extracts dataset identifiers from the JSON response and passes the response along with the identifiers to a function called metadataNewItems.

	It also includes a function to drop duplicate rows. ArcGIS Hub administrators can include datasets from other Hubs in their own site. As a result, some datasets are duplicated in other Hubs. However, they always have the same Identifier, so we can use pandas to detect and remove duplicate rows.


## Troubleshooting (as needed)

!!! warning " "

	The Hub sites are fairly unstable and it is likely that one or more of them will occasionally fail and interrupt the script. 


1. Visit the URL for the Hub to check and see if the site is down, moved, etc. 
2. Refer to the [Update ArcGIS Hubs list page](update-hub-list.md) for more guidance on how to edit the website record.
	* **If a site is missing**: Unpublish it from GBL Admin, indicate the Date Retired, and make a note in the Status field.  
	* If a site is still live, but **the JSON API link is not working**: remove the value "DCAT US 1.1" from the Accrual Method field and make a note in the Status field.
	* If the site has moved to a **new URL**, update the website record with the new information.
3. Start over from Step 1.

## Step 3: Validate and Clean

Although the harvest notebook will produce valide metadata for most of the items, there may still be some errors. [Run the cleaning script](clean.md) to ensure that the records are valid before we try to ingest them into GBL Admin.


## Step 4: Upload all records

1. Review the previous upload. Check the Date Accessioned field of the last harvest and copy it. 
2. Upload the new CSV file. This will overwrite the Date Accessioned value for any items that were already present.
3. Use the old Date Accessioned value to search for the previous harvest date. This example uses 2023-03-07: (https://geo.btaa.org/admin/documents?f%5Bb1g_dct_accrualMethod_s%5D%5B%5D=ArcGIS+Hub&q=%222023-03-07%22&rows=20&sort=score+desc)
4. Unpublish the ones that have the old date in the Date Accessioned field 
5. Record this number in the GitHub issue for the scan under Number Deleted
6. Look for records in the uploaded batch that are still "Draft" - these are new records. 
7. Publish them and record this number in the GitHub issue under Number Added
