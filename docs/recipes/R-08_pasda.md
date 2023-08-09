## Purpose 

To harvest metadata from [Pennsylvania Spatial Data Access (PASDA)](https://www.pasda.psu.edu), a custom data portal. To begin, start the Jupyter Notebook:

1. Start Jupyter Notebook and navigate to the Recipes directory.
2. Open [R-08_pasda.ipynb](https://github.com/geobtaa/harvesting-guide/blob/main/recipes/R-08_08a-01_pasda)


## Step 1: Obtain a list of landing pages

Run Part 1 of the Notebook to obtain a list of all of the records currently in PASDA. This list can be found by doing a blank search on the PASDA website: (https://www.pasda.psu.edu/uci/SearchResults.aspx?Keyword=+)

Since this is a large result list, the recipe recommends downloading the HTML file to your desktop (In the Safari browser, this is *File-Save As - Save As Page Source*)

Then, we can use the Beautiful Soup module to query this page and harvest the following values:

* Title
* Date Issued
* Publisher
* Description
* Metadata file link
* Download link


## Step 2: Download the supplemental metadata files

!!! info "Context"
	
	Bounding boxes & keywords are not found in the landing pages, but most of the PASDA datasets have a supplemental metadata document, which does contain coordinates. The link to this document was scraped to the 'Metadata File" column during the previous step.

Most of the records have supplemental metadata in ISO 19139 or FGDC format. The link to this document is found in the 'Metadata File" column. Although these files are created as XMLs, the link is a rendered HTML.

There is additional information in these files that we want to scrape, including bounding boxes and geometry type.

At the end of Step 2, you will have a folder of HTML metadata files.
  
## Step 3: Query the downloaded supplemental metadata files

This section of the script will scan each HTML metadata file. If it contains bounding box information, it will pull the coordinates. Otherwise, it will assign a default value of the State of Pennsylvania extents.

It will also pull the geometry type and keywords, if available.


## Step 4: Add default and calculated values

This step will clean up the harvested metadata and add our administrative values to each row.  At the end, there will be a CSV file in your directory named for today's date.

## Step 5: Upload the CSV to GEOMG

1. Upload the new records to GEOMG
2. Use the Date Accessioned field to search for records that were not present in the current harvest. Retire any records that have the code "08a-01" but were not part of this harvest.