## Purpose

To convert OpenGeoMetadata (GeoBlacklight) JSONs to a CSV in the GeoBTAA Metadata Profile

## Step 1: Obtain the JSONs

Collect the metadata JSONs. This type of metadata typically is obtain in one of the following ways:

- Direct submission (Team Members from Wisconsin)
- Via an [OpenGeoMetadata repository](https://opengeometadata.org/about-ogm-repositories/)

## Step 2: Run the conversion script

1. Start Jupyter Notebook and navigate to the Recipes directory.
2. Open [R-07_openGeoMetadata.ipynb](https://github.com/geobtaa/harvesting-guide/blob/main/recipes/R-07_OpenGeoMetadata)
3. Move the folder with the metadata JSONs into the same directory as the Jupyter Notebook.
4. Declare the paths and folder name in the Notebook.
5. Run all cells

!!! tip

	Depending upon the source, you may want to adjust the script to accomodate custom fields.
	
## Step 3: Edit the output CSV

The GeoBTAA Metadata Profile may have additional or different requirements. Consult with the Product Manager on which fields may need augmentation.

## Step 4: Upload to GBL Admin