## Purpose

To scan the [DCAT 1.1 API](https://resources.data.gov/resources/dcat-us/) of ArcGIS Hubs and return the metadata for all suitable items as a CSV file in the GeoBTAA Metadata Application Profile.

!!! warning " "

	This recipe includes steps that use the GBL Admin toolkit. Access to this tool is restricted to UMN BTAA-GIN staff and requires a login account. External users can create their own list or use one provided in this repository.
	

``` mermaid
graph TB

A{{STEP 1. <br>Download arcHubs.csv}}:::green --> B[[STEP 2. <br>Run Jupyter Notebook harvest script]]:::green;
B --> C{Did the script run successfully?};
C --> |Yes| K[[STEP 3. Validate and Clean]]:::green; 
K --> E[[STEP 4. <br>Upload the CSV]]:::green; 
E --> L[[STEP 5. <br>Publish and republish records]]:::green; 
L --> M[[STEP 6. <br>Unpublish retired records]]:::green; 
M --> N{{STEP 7. <br>Record changes}}:::red; 
C --> |No| D[Troubleshoot]:::yellow;
D --> H{Did the script stall because of a Hub?};
H --> |Yes| I[Refer to the page Update ArcGIS Hubs]:::yellow;
H --> |No & I can't figure it out.| F{{Refer issue back to Product Manager}}:::red;
H --> |No| J[Try updating your Python modules or debugging the error message]:::yellow;
J --> B;
I --> A;


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
	
	- **ID**: Unique code assigned to each portal. This is transferred to the "Is Part Of" field for each dataset.
	- **Title**: The name of the Hub. This is transferred to the "Provider" field for each dataset
	- **Publisher**: The place or administration associated with the portal. This is applied to the title in each dataset in brackets
	- **Spatial Coverage**: A list of place names. These are transferred to the Spatial Coverage for each dataset
	- **Member Of**: a larger collection level record. Most of the Hubs are either part of our [Government Open Geospatial Data Collection](https://geo.btaa.org/catalog/ba5cc745-21c5-4ae9-954b-72dd8db6815a) or the [Research Institutes Geospatial Data Collection](https://geo.btaa.org/catalog/b0153110-e455-4ced-9114-9b13250a7093)
	
	However, it is not necessary to take extra time and manually remove the extra fields from the CSV export, because the Jupyter Notebook code will ignore them.

-------------------

## Step 2: Run the harvest script

1. Start Jupyter Notebook and navigate to the Recipes directory.
2. Open [R-01_arcgis-hubs.ipynb](https://github.com/geobtaa/harvesting-guide/blob/main/recipes/R-01_arcgis-hubs)
3. Move the downloaded file `arcHubs.csv` into the same directory as the Jupyter Notebook.
4. Run all cells.


### Troubleshooting script failures

!!! warning

	The Hub sites are fairly unstable and it is likely that one or more of them will occasionally fail and interrupt the script. 

If the script stalls or fails to parse certain Hub sites, try the following:

1. Visit the URL for the Hub to check and see if the site is down, moved, etc. 
2. Refer to the page on [How to remove broken or deprecated ArcGIS Hubs](../update-hub-list/#how-to-remove-broken-or-deprecated-arcgis-hubs) for more guidance on how to edit the website record.
	* **If a site is missing**: Unpublish it from GBL Admin, indicate the Date Retired, and make a note in the Status field.  
	* If a site is still live, but **the JSON API link is not working**: remove the value "DCAT US 1.1" from the Accrual Method field and make a note in the Status field.
	* If the site has moved to a **new URL**, update the website record with the new information.
3. Start over from Step 1.

## Step 3: Validate and Clean

Although the harvest notebook will produce valide metadata for most of the items, there may still be some errors. [Run the cleaning script](clean.md) to ensure that the records are valid before we try to ingest them into GBL Admin.
1. Move the scanned records csv into the cleaned-00 recipe folder
2. In Jupyter Notebook, navigate to the R-00 folder
3. Replace the name of the csv in the first cell in the notebook to reflect the current csv’s filename
4. Run all cells. Takes less than a minute. 

## Step 4: Upload the CSV 

!!! tip

	See also: [General Import Instructions](https://gin.btaa.org/geoblacklight_admin_docs/import/)

1. In GBL Admin, select **Imports** in the **Admin Tools** menu at the top of the page, then **New Import**.
2. Enter the Name "[GitbHub Issue Number] ArcGIS Hubs scan YYYY-MM-DD" and the type "BTAA CSV." 
3. Click **Choose File** and upload the cleaned scanned records of today’s date (likely still located in the **R-00_clean recipe** folder). 
4. Click **Create Import**. Wait! The page may not immediately change. 
5. Briefly review the Field Mappings to make sure none of the fields are blank. No changes should be needed. Click **Create Mapping** at the bottom of the page. 

    !!!	tip "Optional verification"

        Check that the **CSV Row Count** matches the actual row count of your CSV. (In Excel, select any column header, then find the row count at the bottom of the window. It will be 1 greater than expected because it includes the column header row.) 

6. Click **Run Import**, then wait for about 30 minutes or more. Refresh the page to see how many records have been imported so far. The import is complete when the Total count under **Imported Documents** matches the **CSV Row Count**. There is no notification. 

## Step 5: Publish and republish records 

#### Convert new records from Draft to Published:

1. Click the GBL*Admin logo to return to the [Documents view](https://geo.btaa.org/admin/documents).
2. Click **Imports** at the top of the left column menu and click on today’s ArcGIS Hub import.
3. Under publication state, click on **Draft**. 
4. Record the number of Draft records in a comment on the GitHub issue. This is the “New” stat used in the last step. 
5. Check the box to select all, **Select all results that match this search**, select **Bulk Actions** > **Published**, and **Run Bulk Action**. Reload the page to see the results.

#### Republish previously unpublished records that have returned:

1. Return to the [Documents view](https://geo.btaa.org/admin/documents), click on Imports, and select today’s import.
2. Under publication state, click on Unpublished. 
	- These are items that were found in past scans, then not found and therefore removed in subsequent scans, but have now been found once again in today’s scan. 
3. In a comment on the GitHub issue, record the number of unpublished records. This is the “Republished” stat used in the last step. 
4. Check the box to select all, Select all results that match this search, and select Bulk Actions > Published, Run Bulk Action. Again, reload the page to see the results. 
5. Return to the [Documents view](https://geo.btaa.org/admin/documents), click on Imports, and select today’s import.
6. Under **Publication State**, confirm that “published” is now the only category and that the number of records matches the row count of your CSV upload. 
7. Click the red X next to the title of today’s important so that all records are shown.

## Step 6: Unpublish retired records 

!!! purpose "Purpose" 

	The purpose of this step is to unpublish from the Geoportal any records that have been removed from their source hub by their owners. When an existing record is found and imported in a new scan, its Date Accessioned is updated. We want to keep records found in the most recent two scans (including today's) but unpublish everything older than that. This should remove intentionally retired records but leave any that were just temporarily unavailable. 

1. If you're not there already, return to the [Documents view](https://geo.btaa.org/admin/documents) so you're viewing *all* records. Scroll down to **Accrual Method** and click **ArcGIS Hub**. 
2. Click **Published** under **Publication State** to see all published Hub records.
3. Under **Date Accessioned**, identify any results with a date earlier than the two most recent dates, including today's. (There might be only one or none). Note that they are sorted by number of records, not by date! 
4. In a comment on the GitHub issue, record the total number of records on those earlier dates as “Retired.”
5. For each of these earlier dates: Select the date, check the box to select all records, click **Select all results that match this search**, select **Bulk Actions** > **Unpublished**, and click **Run Bulk Action**. Again, reload the page to see the results. 

!!! tip

	If you see weird behavior during this step, scroll down to “Notes and Troubleshooting”

## Step 7: Record what has changed 
1. Optional but helpful: save your GitHub comment with the numbers you recorded of new, republished, and retired records. 
2. Mandatory: In the right sidebar, expand **Collections** under **Projects**. Put the sum of new + republished in the **Records Added** field, and fill in the **Records Retired** field. 

!!! info

	This information gets exported and added to a monthly report to showcase the way our collection fluctuates. As a general rule of thumb, the total change in records shouldn’t be much more than 100 - if it’s a lot more, try to evaluate why or ask for help. 

## Note on records that do not respond to edits

- Sometimes GBL Admin records will appear in the list that you get when you click “published” under publication state and then click the older date accessioned saved queries, but when viewed in the results list, have a red “unpublished” label. (this mismatch can also happen in reverse - if something’s unpublished but you can’t publish it, or if there are any other records are not updated and syncing)
- The record lives in 2 places: admin (database - back end) and geoportal (solr - front end). If it’s corrupted, it “freezes” in the front end. No changes you make to it will apply, and it may display incorrect values. This is almost always because of the bounding box, but it can also be because of the date range. To resolve:
    1. Click on the record title
    2. Click under “admin view” 
    3. Scroll down to the Spatial section and either clear or fix the Bounding Box and Geometry fields.
	    - If you don't know the correct values, it's fine to leave both fields blank.
	    - If you're going to add corrected values, it's fine to just fill in the Bounding Box field. When you click save, it will automatically generate the geometry based on the bounding box.
	    - If you know the specific geometry that should applied, you can add it, but it's not important. 
