These tutorials are short, easy to complete exercises to help someone get the basics of running and writing scripts to harvest metadata. They are available as Jupyter Notebooks hosted in GitHub in the [Harvesting Guide repository](https://github.com/geobtaa/harvesting-guide).

## 1. [Setting up your environment](https://github.com/geobtaa/harvesting-guide/tree/main/tutorials/T-01_setting-up)

* These tutorials will guide users on how to set up your environment for harvesting.
* Getting Started with GitHub: Provides an introduction to GitHub and a walkthrough of creating a repository.
* Getting Started with Jupyter Notebooks: Provides an introduction and overview of cell types.

## 2. [Navigating paths](https://github.com/geobtaa/harvesting-guide/blob/main/tutorials/T-02_changing_paths)

This tutorial shows how to navigate and list directories. Techniques covered include:

* Using the `cd` command in the terminal
* Navigating to and from the home directory
* Listing the current path
* Listing documents within the current path

## 3. [Iterating over files](https://github.com/geobtaa/harvesting-guide/tree/main/tutorials/T-03_iterating-files)

* This guide will assist users in how to open, read, and print the results of a CSV.
* The module `os.Walk` will be introduced to read through multiple directories to find files.
* The pandas module will be used to display a CSV for records.

## 4. [Merge CSV files based on a shared column](https://github.com/geobtaa/harvesting-guide/tree/main/tutorials/T-04_merge-csv-files)

This tutorial will take two CSV files and combine them using a shared key.

## 5. [Transform a batch of JSON files into a single CSV file](https://github.com/geobtaa/harvesting-guide/tree/main/tutorials/T-05_json-to-csv)

This tutorial uses the Python module **pandas** (Python Data Analysis Library) to open a batch of JSON files and transform the contents into a single CSV.

## 6. [Extract Place Names](https://github.com/geobtaa/harvesting-guide/tree/main/tutorials/T-06_extract-place-names)

This tutorial scans the two columns from a CSV file ('Title' and 'Description') to look for known place names and writes the values to a separate field.


## 7. [Parsing HTML with Beautiful Soup](https://github.com/geobtaa/harvesting-guide/tree/main/tutorials/T-07_parsing-html-beautiful-soup)

This tutorial will guide users through Hyper Text Mark-Up Language (HTML) site parsing using the BeautifulSoup Python module, including:

* how to install the BeautifulSoup module
* scan and list web pages
* return titles, descriptions, and dates
* writing parsed results to CSV format

## 8. [Use OpenStreetMap to generate bounding boxes](https://github.com/geobtaa/harvesting-guide/tree/main/tutorials/T-08_bboxes-from-osm)

This tutorial demonstrates how to query the OpenStreetMap API using place names to return bounding box coordinates.

!!! info "Credits"

	These tutorials were prepared by Alexander Danielson and Karen Majewicz in April 2023.
