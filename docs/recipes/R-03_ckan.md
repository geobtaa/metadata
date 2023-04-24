## Purpose

To scan the CKAN data portals and retrieve metadata for new items while returning a list of deleted items.

## Step 1: Download the list of active ArcGIS Hubs

We maintain a list of active CKAN sites in GEOMG. 

!!! tip inline end "Shortcut"

	[Pre-formmated GEOMG query link](https://geomg.lib.umn.edu/documents?f%5Bdct_format_s%5D%5B%5D=CKAN+data+portal&rows=20&sort=score+desc)

1. Go to the [GEOMG](https://geomg.lib.umn.edu) dashboard
2. Filter for items with these parameters:
  	 - Resource Class: Websites
  	 - Format: CKAN data portal
3. Select all the results and click Export -> CSV
4. Download the CSV and rename it `ckanPortals.csv`

!!! info
    
	Exporting from GEOMG will produce a CSV containing all of the metadata associated with each Hub. For this recipe, the only fields used are:

	* **ID**: Unique code assigned to each portal. This is transferred to the "Is Part Of" field for each dataset.
	* **Title**: The name of the Hub. This is transferred to the "Provider" field for each dataset
	* **Publisher**: The place or administration associated with the portal. This is applied to the title in each dataset in brackets
	* **Spatial Coverage**: A list of place names. These are transferred to the Spatial Coverage for each dataset
	* **Member Of**: a larger collection level record. Most of the CKAN portals are either part of our [Government Open Geospatial Data Collection](https://geo.btaa.org/catalog/ba5cc745-21c5-4ae9-954b-72dd8db6815a) or the [Research Institutes Geospatial Data Collection](https://geo.btaa.org/catalog/b0153110-e455-4ced-9114-9b13250a7093)

	However, it is not necessary to take extra time and manually remove the extra fields, because the Jupyter Notebook code will ignore them.
	
## Step 2: Set up directories

1. Navigate to the Recipes directory for [R-03_ckan.ipynb](https://github.com/geobtaa/harvesting-guide/blob/main/recipes/R-03_ckan/R-03_ckan.ipynb).

2. Verify that there are two folders

- `resource` folder: a set of resource names by portal for each re-accession
- `reports` CSV metadata files for all new and deleted datasets

3. Move the downloaded ckanPortals.csv into this directory.

## Step 2: Run the harvest script

1. Start Jupyter Notebook 
2. Open [R-03_ckan.ipynb](https://github.com/geobtaa/harvesting-guide/blob/main/recipes/R-03_ckan)


??? info "Expand to read about the R-03_ckan.ipynb Jupyter Notebook"

	This script will harvest from a set of CKAN data portals. It saves metadata files and will compare the output between runs. The result will be two CSVs: new items and deleted items.
	
## Step 3: Edit the metadata for new items

These records in `reports/allNewItems_{today's date}.csv` may need manual editing. 

!!! info "in progress"
	
	This section will be expanded after the CKAN harvest script is updated.
	

## Step 4: Upload metadata for new records

Open GEOMG and upload the new items found in `reports/allNewItems_{today's date}.csv`

## Step 5: Delete metadata for retired records

Use the [GEOMG documents update script](https://github.com/geobtaa/workflows/tree/main/editing/geomg-documents-update) to unpublish records that are no longer active found in `reports/allDeletedItems_{today's date}.csv` 




	

