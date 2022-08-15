### 1. Save edited template as a CSV file
[Use the B1G Template](https://z.umn.edu/b1g-template)

### 2. Upload the spreadsheet to GEOMG
- This is done via the batch imports function. 
- When logged into GEOMG, go to Admin Tools and select Imports. Click "New Import".
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

### 3. Spot check records for errors and consistency
- The newly uploaded records will be listed as Draft under the Publication State on the main dashboard
- Select 'Draft' under Publication State and select an item. This will open it in editing view.
- Click the button **View in Geoportal**
- Inspect the record and test the links. (note: Metadata and Web Service links will not open while the item is still in Draft)
- Repeat this process for about 3 records.


### 4. Convert records from 'Draft' to 'Published'

- If the records are satisfactory, return to the Dashboard view and select all Draft items in the upload. 
- Select All and then select the text "Select all results that match this search"
- Click the State button. From the dropdown, select Published.
- On the _Bulk Action_ page, click the button **Run Bulk Action**
- Review 3-5 of the published records and test all the links.

### 5. Publish to OpenGeoMetadata
- Completed records are synced to the workflow GitHub online repository as needed. 
- Records that are deemed stable and complete can be shared with the [OpenGeoMetadata community](https://github.com/OpenGeoMetadata).
