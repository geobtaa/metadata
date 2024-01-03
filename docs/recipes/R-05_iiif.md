## Purpose

To extract metadata from IIIF JSON Manifests.


## Step 1: Download the JSONs

1. Create a CSV file called "jsonUrls.csv" with just the URLs of the JSONs.
2. Navigate to the Terminal/Command Line and into a directory where you can save files
3. Type: `wget -i jsonUrls.csv`
4. Review that all of the JSONs downloaded to a local directory

## Step 2: Run the extraction script

1. Start Jupyter Notebook and navigate to the Recipes directory.
2. Open [R-05_iiif.ipynb](https://github.com/geobtaa/harvesting-guide/blob/main/recipes/R-05_IIIF)
3. Move the downloaded file `jsonUrls.csv` into the same directory as the Jupyter Notebook.
4. Run all cells

!!! Warning

	This will lump all the subsections into single fields and the user will still need to split them.

## Step 3: Merge the metadata

Although the Jupyter Notebook extracts the metadata to a flat CSV, we still need to merge this with any existing metadata for the records.

## Step 4: Upload to GBL Admin