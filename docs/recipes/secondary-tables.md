# How to upload links in secondary tables in GBL Admin

* We use two compound metadata fields, `Multiple Download Links` and `Institutional Access Links`, that include multiple links that are formatted with both a label + a link. 
* Because these fields are not regular JSON flat key:value pairs, they are stored in secondary tables within GBL Admin.
    * When using GBL Admin's **Form** view, these values can be entered by clicking into a side page linked from the record.
    * For **CSV uploads**, these values are uploaded with a separate CSV from the one used for the main import template.

!!! tip

	See the [opengeometadata.org page on multiple downloads](https://opengeometadata.org/configure-references-links/#multiple-downloads) for how these fields are formatted in JSON

## Manual entry

### Multiple Download Links

1. On the Form view, scroll down to the end of the Links section  and click the text "Multiple Download Links"
1. Click the New Download URL button
1. Enter a label (i.e., "Shapefile") and the download URL
1. Repeat for as many as needed

	
### Institutional Access Links

1. On the Form view, scroll down to the bottom of the right-hand navigation and click the text "Institutional Access Links" 
1. Click the New Access URL button
1. Select an institution code and the access URL
1. Repeat for as many as needed

	
## CSV Upload for either type

1. Go to Admin Tools - Multiple Downloads or Access Links
1. Upload a CSV in on of these formats:



!!! Info "CSV field headers for secondary tables"

    === "Multiple Downloads"

        ``` markdown
        
			| friendlier_id       | label            | value      |
			|---------------------|------------------|------------|
			| ID of target record |  any string      | the link   |
        ```

    === "Institutional Access Links"

        ``` markdown
			| friendlier_id       | institution_code | access_URL |
			|---------------------|------------------|------------|
			| ID of target record |  2 digit code    | the link   |
        ```