## Purpose

To scan the [Action API for CKAN data portals](https://docs.ckan.org/en/2.9/api/) and retrieve metadata for new items while returning a list of deleted items.


``` mermaid
graph TB

A((STEP 1. <br>Set up directories)) --> B[STEP 2. <br>Run Jupyter Notebook script] ;
B --> C{Did the script run successfully?};
C --> |No| D[Troubleshoot];
D -->A;
C --> |No & I can't figure it out.| F[Refer issue back to Product Manager];
C --> |Yes| E[STEP 3. <br>Edit places names & titles]; 
E --> G[STEP 4. <br>Upload new records];
G --> H[STEP 5. <br>Unpublish deleted records];

classDef goCell fill:#99d594,stroke:#333,stroke-width:2px
class A,B,C,E,G goCell;
classDef troubleCell fill:#ffffbf,stroke:#333,stroke-width:2px;
class D troubleCell;
classDef endCell fill:#fc8d59,stroke:#333,stroke-width:2px
class F,H endCell;
classDef questionCell fill:#fff,stroke:#333,stroke-width:2px;
class C questionCell;



```

	
## Step 1: Set up your directories

1. Navigate to your local Recipes directory for [R-03_ckan](https://github.com/geobtaa/harvesting-guide/blob/main/recipes/R-03_ckan).

2. Verify that there are two folders
	* `resource`: contains a CSV for each portal per harvest that lists all of the dataset identifiers
	* `reports`: combined CSV metadata files for all new and deleted datasets per harvest

3.  Review the CKANportals.csv file. Each active portal should have values in the following fields:
	* portalName
	* URL
	* Provider
	* Publisher
	* Spatial Coverage
	* Bounding Box 

## Step 2: Run the harvest script

1. Start Jupyter Notebook 
2. Open your local copy of [R-03_ckan.ipynb](https://github.com/geobtaa/harvesting-guide/blob/main/recipes/R-03_ckan)

!!! info 

	This script will harvest from a set of CKAN data portals. It saves a list of datasets found in each portal and will compare the output between runs. The result will be two CSVs: new items and deleted items.
	
	The script only harvests items that can be identified as shapefiles or imagery.
	
## Step 3: Edit the metadata for new items

The new records can be found in `reports/allNewItems_{today's date}.csv` and will need some manual editing. 

* **Spatial Coverage**: Add place names related to the datasets.
* **Title**: Concatenate values in the Alternative Title column with the Spatial Coverage of the dataset. 


## Step 4: Upload metadata for new records

Open GEOMG and upload the new items found in `reports/allNewItems_{today's date}.csv`

## Step 5: Delete metadata for retired records

Unpublish records found in `reports/allDeletedItems_{today's date}.csv`. This can be done in GEOMG manually (one by one) or with the [GEOMG documents update script](https://github.com/geobtaa/workflows/tree/main/editing/geomg-documents-update).




	

