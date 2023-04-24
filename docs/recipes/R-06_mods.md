## Purpose:

To extract metadata from XML files in the MODS metadata format. 

## Step 1: Obtain a list of URLs for the XML files

This list may be supplied by the submitter or we may need to query the website to find them.

## Step 2: Run the extraction script

1. Start Jupyter Notebook and navigate to the Recipes directory.
2. Open [R-06-mods.ipynb](https://github.com/geobtaa/harvesting-guide/blob/main/docs/2-Recipes/R-06_MODS/R-06_MODS.ipynb)
3. Move the downloaded file `arcHubs.csv` into the same directory as the Jupyter Notebook.
4. Run all cells.

## Step 3: Format as OpenGeoMetadata

Manually adjust the names of the columns to match metadata into our [GeoBTAA metadata template.](https://z.umn.edu/b1g-template)

## Step 4: Upload to GEOMG