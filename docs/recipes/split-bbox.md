# Split Bounding Boxes that cross the 180th Meridian

## Problem

The BTAA Geoportal does not display bounding boxes that cross the 180th meridian (also known as the International Date Line.) In these circumstances, the West coordinate will be a positive number, but the East coordinate will be negative.

## Solution

One way to mitigate this is to create two bounding boxes for the OGM Aardvark `Geometry` field. The Bounding Box value will be the same, but the Geometry field will have a multipolygon that is made up of two adjacent boxes.

The following script will scan a CSV of the records, identify which cross the 180th Meridian, and insert a multipolygon into a new column. 

The script was designed with the assumption that the input CSV will be in the OGM Aardvark format, likely exported from GBL Admin. The CSV file must contain a field for `Bounding Box`.  It may contain a `Geometry` field with some values that we do not want to overwrite.

This script will create a new field called "Bounding Box (WKT)". Items that crossed the 180th Meridian will have a multipolygon in that field. Items that don't cross will not have a value in that field. Copy and paste only the new values into the `Geometry` column and reupload the CSV to GBL Admin.

```
import csv

def split_coordinates(coordinate_str):
    if not coordinate_str:
        return ''

    coordinates = coordinate_str.split(',')

    west, south, east, north = map(float, coordinates)

    if west > 0 and east < 0:
        polygon1 = f'({west} {south}, {179.9} {south}, {179.9} {north}, {west} {north}, {west} {south})'
        polygon2 = f'({-179.9} {south}, {-179.9} {north}, {east} {north}, {east} {south}, {-179.9} {south})'
        return f'MULTIPOLYGON(({polygon1}), ({polygon2}))'

    return coordinate_str

# Specify the input CSV file path
input_file = 'your_input_file.csv'

# Specify the output CSV file path
output_file = 'your_output_file.csv'

# Specify the name of the column with the Bounding Box coordinates
coordinate_column = 'Bounding Box'

# Specify the name of the new column to store the updated coordinates
new_coordinate_column = 'New Bounding Box (WKT)'

# Read the input CSV and process the coordinates
with open(input_file, 'r') as file:
    reader = csv.DictReader(file)
    fieldnames = reader.fieldnames + [new_coordinate_column]

    with open(output_file, 'w', newline='') as output:
        writer = csv.DictWriter(output, fieldnames=fieldnames)
        writer.writeheader()

        for row in reader:
            bounding_box = row[coordinate_column]
            new_bounding_box = split_coordinates(bounding_box)
            row[new_coordinate_column] = new_bounding_box
            writer.writerow(row)

print("CSV processing completed!")
```