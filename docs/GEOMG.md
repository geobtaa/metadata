!!! Warning "This guide is a work in progress (August 2022)"

## About

**What is it?**

: [GEOMG](https://github.com/geobtaa/geomg) is a custom tool that functions as a backend metadata editor and manager for the GeoBlacklight application. 

**Who uses it?**

: BTAA-GIN [Operations technical staff](https://sites.google.com/umn.edu/btaa-gdp/about/community#h.gtto9fewuh3z) at the University of Minnesota

**Who developed it?**

: The BTAA Geoportal Lead Developer, Eric Larson, created GEOMG, with direction from the BTAA-GIN. It is based upon the [Kithe framework.](https://github.com/sciencehistory/kithe)

**Can other GeoBlacklight projects adopt it?**

Not yet. We are currently working on offering this tool as a plugin for GeoBlacklight. Our tentative plan for release is early 2023.  In the meantime, this presentation describes the motivation for building the tool and a few screencasts showing how it works:

<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vQAlzzbZxoS__W9ZoLQ1A3GbiwEE9lkvPzTw_VLrlY_7dkPrc8k5ApappPv35-1IjyIM1--Rh0UO28j/embed?start=false&loop=false&delayms=3000" frameborder="0" width="400" height="400" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>

----------------------

## Layout

Dashboard (Home page)
![](images/geomg-dashboard.png)

The Dashboard shows a list of all records in the index. These can be selected or filtered. The search functionality mimics the GeoBlacklight interface:

* a search bar at the top: lets a user enter text searches
* a list of facets on the left: lets a user filter records
* a Date Range filter above the facets: lets a user select items by Date Created (when they were first added to GEOMG).

Use the check boxes to select individual records or click the right arrow to select all records on the page.
![](images/checkbox.png)

To select all records in the list, first select all records on the page. Then, click the text, "Select all results that match this search."

![](images/selectAll.png)




## Adding new records
There are two ways to add new records to GEOMG: with the Form view or with a CSV upload.

### Form view
A user can create records one by one using the form view. 

1. Start on the main dashboard
2. click the button labeled **+New Document**
3. Manually type in values. Some fields need to be entered before the record can be saved including:
	* Title
	* Resource Class
	* ID
	* Access Rights


### Uploading as a CSV

1. Save edited template as a CSV file
[Use the B1G Template](https://z.umn.edu/b1g-template)

2. Upload the spreadsheet to GEOMG

- Go to Admin Tools and select Imports. Click "New Import".
- Give a name to the upload and enter details about the source and description. These details are helpful later in tracking imports.
- Select the CSV file for upload
- For Type, choose the BTAA CSV. 
- Click the **Create Import** button
- Review the _Field Mappings_ page. If the CSV was formatted with column headers spelled the same way as the template, the fields should automatically map to the correct elements. Otherwise, manually choose the crosswalk mapping.
- Scroll to the bottom and click the button **Create Mapping**
- On the _Import_ page, check that the number in the CSV Row Count matches your CSV.
- Click the button **Run Import**
- The import may take a few minutes. During the process, you can view the Import Results tab. Items in the queue will show up in the first sub-tab ("Failed"), but will transfer to the second tab upon import ("Success").
- When complete, review any items that did not import in the Failed tab. See Troubleshooting (_coming soon_) for help.

3. Spot check records for errors and consistency

- The newly uploaded records will be listed as Draft under the Publication State on the main dashboard
- Select 'Draft' under Publication State and select an item. This will open it in editing view.
- Click the button **View in Geoportal**
- Inspect the record and test the links. (note: Metadata and Web Service links will not open while the item is still in Draft)
- Repeat this process for about 3 records.


4. Convert records from 'Draft' to 'Published'

- If the records are satisfactory, return to the Dashboard view and select all Draft items in the upload. 
- Select All and then select the text "Select all results that match this search"
- Click the State button. From the dropdown, select Published.
- On the _Bulk Action_ page, click the button **Run Bulk Action**
- Review 3-5 of the published records and test all the links.