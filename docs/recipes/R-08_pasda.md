## Purpose to harvest metadata from [Pennsylvania Spatial Data Access (PASDA](https://www.pasda.psu.edu), a custom data portal.

## Step 1: Start the Jupyter Notebook

1. Start Jupyter Notebook and navigate to the Recipes directory.
2. Open [R-08_pasda.ipynb](https://github.com/geobtaa/harvesting-guide/blob/main/docs/2-Recipes/R-08_08a-01_pasda/R-08_8a-01-pasda.ipynb)
3. Move the folder with the metadata JSONs into the same directory as the Jupyter Notebook.
4. Declare the paths and folder name in the Notebook.

## Step 2: Obtain a list of landing pages

Run part 1 of the Notebook to obtain a list of all of the records currently in PASDA. 

The resulting CSV will be called `URLS_{today's date}.csv` which is just a list of the landing pages for the datasets in the PASDA portal.


## Step 3: Parse each page the PASDA portal

1. Manually update the second cell in **Part 2: Parse the discovery metadata on each page** of the Notebook where it says 

    `with open('pasdaURLS_{today's date}.csv') as fr:`

    Change {today's date} to the date your ran the previous cells so that the CSV filename matches. For example, it might look like:

    `with open('URLs_20230218.csv') as fr:`

2. Run Part 2.
3. The resulting CSV will be called `output_{today's date}.csv`.
    
  
## Step 4: Extract the bounding boxes

!!! info "Context"
	
	Bounding boxes are not found in the landing pages, but most of the PASDA datasets have a supplemental metadata document, which does contain coordinates. The link to this document was scraped to the 'Metadata" column during the previous step.

1. Copy the "Metadata" column into a new CSV that is just a list of these URLs.

2. Use the getBbox.py script to parse the files and extract the bounding boxes.


## Step 5: Merge and edit the metadata

1. Merge these bounding boxes into the output CSV from Step 1.
2. Manually augment the metadata to match the GeoBTAA Metadata Profile.

## Step 6: Upload to GEOMG