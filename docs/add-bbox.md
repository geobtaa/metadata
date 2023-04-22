---
hide:
  - toc
---

!!! summary

	This page describes processes for obtaining bounding box coordinates for our scanned maps. The coordinates will be used for indexing the records in the Big Ten Academic Alliance Geoportal.

**About bounding box coordinates for the BTAA Geoportal
**
* Bounding boxes enable users to search for items with a map interface. 
* The format is 4 coordinates in decimal degrees 
* Provide the coordinates in this order: West, South, East, North. 
* The bounding boxes do not need to be exact, particularly with old maps that may not be very precise anyways.

## Manual method

### Part A: Setup

1. Open and inspect the image file.
2. Try to identify a single / combined region that the map or atlas represents
3. You can also check to see if the map has the bounding coordinates printed in the text anywhere or you are able to find the bounds by inspecting the edges.  
4. Open another window with the [Klokan Bounding Box](https://boundingbox.klokantech.com) tool.
5. Set the Copy & Paste section to CSV.

### Part B: Find the coordinates

#### Option 1: Search for a place name

1. Use the search boxes on the Klokan Bounding Box tool to zoom to the region.  (For example, search for “Illinois”.
2. Manually adjust the grey overlay box in the Klokan site to line up the edges to the edges of the map. 
3. Try to line it up reasonably closely


#### Option 2: Draw a shape

1. Switch to the Polygon tool by clicking on the pentagon icon
2. Click as many points on the screen as needed to approximate the map extent.
3. Click on the first point to close the polygon
4. The interface will display a dotted line showing the bounding box rectangle.

### Part C: Copy back to GeoBTAA metadata

1. Click the “Copy to Clipboard” icon on the Klokan site.
2. Paste the coordinates into the Bounding Box field in the GeoBTAA metadata template or in the GEOMG metadata editor.

## Programmatic method

The OpenStreetMap offers and API that allows users to query with place names and return a bounding box

Here is a sample script:

	```
	import pandas as pd
	import requests
	
	# Define function to geocode a place name using Nominatim API
	def geocode_place_name(place_name):
	    url = "https://nominatim.openstreetmap.org/search"
	    params = {
	        "q": place_name,
	        "format": "jsonv2"
	    }
	    response = requests.get(url, params=params)
	    if response.ok:
	        data = response.json()
	        if len(data) > 0 and "boundingbox" in data[0]:
	            bbox = data[0]["boundingbox"]
	            return [bbox[2], bbox[0], bbox[3], bbox[1]]
	    return None
	
	# Load the CSV file into a pandas dataframe
	df = pd.read_csv("02d-03.csv")
	
	# Apply the geocode_place_name function to the "place" column
	df["bbox"] = df["place"].apply(geocode_place_name)
	
	# Write the results to a new CSV file
	df.to_csv("02d-03-output.csv", index=False)
	```





