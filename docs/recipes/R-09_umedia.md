## Purpose: To harvest new records added to the [University Of Minnesota's UMedia Digital Library](https://umedia.lib.umn.edu).



##  Step 1: Set up folders

1. Navigate to the UMedia Recipe directory at [R-09_umedia.ipynb](https://github.com/geobtaa/harvesting-guide/blob/main/docs/2-Recipes/R-09_05d-01-umedia)
2. Verify the following folders are present:

`requests`

This folder stores all search results in JSON format for each reaccession as `request_YYYYMMDD.json`. 

`jsons`

This folder stores all JSON files by different added month for UMedia maps. After we get the search result JSON file from each reaccession, we will read this `request_YYYYMMDD.json` file in detail to filter out the included maps by month, and store them to `dateAdded_YYYYMM.json` individually.

`reports`

This folder stores all CSV files for metadata by month. Once we have JSON files for different month, we extract all useful metadata and contribute in the `dateAdded_YYYYMM.csv` in this folder.

## Step 2: Run the harvesting script

1. Start Jupyter Notebook and open [R-09_umedia.ipynb](https://github.com/geobtaa/harvesting-guide/blob/main/docs/2-Recipes/R-09_05d-01-umedia/R-09_05d-01_umedia.ipynb)
2. The second code cell will ask for an input on how many map records you want to harvest.
3. The third code cell will ask for a date range. Select a month (in the form `yyyy-mm`)  based on the last time you ran the script.

## Step 3: Edit the metadata

## Step 4: Upload to GEOMG


