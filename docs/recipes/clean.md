# Validate and Clean Metadata

!!! info

	Find the cleaning script here: https://github.com/geobtaa/harvesting-guide/tree/main/recipes/R-00_clean

As a final step of [Edit stage of the resource lifecycle](../../resource-lifecycle/#3-edit), we run a cleaning script to fix common errors:

## Required fields

* **Resource Class**: Checks that an entry exists and that it is one of the controlled values. If the field is empty, the cleaning script will insert `Datasets` as a default.
* **Access Rights**: Checks that it contains either `Public` or `Restricted`. If empty, the script will insert `Public` as a default.

## Conditionally required fields

* **Format**: If the "Download" field has a value, Format must also be present. If empty, the script will insert `File` as a default.


## Syntax

* **Date Range**: If present, checks that it is valid with a range in the format `yyyy-yyyy`, where the second value is earlier than the first. If the second value is earlier (lower) than the first, the script will reorder them.
* **Bounding Box**: There are numerous possible conditions that the script will fix:
	* Rounding: The script will round all coordinates to two decimal points. (For some collections, we change this to three). This is done because the bounding boxes function as a finding aid and overly precise coordinates can be misleading. It also saves on the memory load for geometry and centroid calculations.
	* non-degrees: If one of the coordinates exceeds the earth's coordinates (over 180 for longitude or 90 for latitude), the coordinates are considered invalid and the entire field will be cleared for that record.
	* lines or points: If the script finds that easting and westing or north and south coordinates are equal, it will add a .001 to the end.

## Reports

After cleaning, the script will produce two CSVS:

1. Cleaned Metadata: All of the original rows with fixes applied. A new column called "Cleaned" will indicate if the row was edited by the script.
2. Cleaning Log: A list of all the records and fields that were cleaned and what was done.
