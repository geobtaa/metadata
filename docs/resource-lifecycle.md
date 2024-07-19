# Resource Lifecycle

## 1. Identify

:fontawesome-solid-user: BTAA-GIN Team Members and Product Manager 

Team members seek out new content for the geoportal. See the page [How to Submit Resources to the BTAA Geoportal](submit-resources.md) for more information.

## 2. Harvest

:fontawesome-solid-user: Graduate Research Assistants and Product Manager 

This stage involves obtaining the metadata for resources.  At a minimum, this will include a title and and access link. However, it will ideally also include descriptions, dates, authors, rights, keywords, and more. 

Here are the most common ways that we obtain the metadata:

1. a BTAA-GIN Team Member sends us the metadata values as individual documents or as a combined spreadsheet
2. we are provided with (or are able to find) an API that will automatically generate the metadata in a structured file, such as JSON or XML
3. we develop a customized script to scrape directly from the HTML on a source's website
4. we manually copy and paste the metadata into a spreadsheet
5. a combination of one or more of the above

## 3. Crosswalk

This step involves using a crosswalk to convert the metadata into the schema needed for the Geoportal. Our goal is to end up with a spreadsheet containing columns matching our [metadata template](https://z.umn.edu/b1g-template).

!!! info "Why do we rely on CSV?"

	CSV (Comma Separated Values) files organize tabular data in plain text format, where each row of data is separated by a line break, and each column of data is separated by a delimiter.
	
	We have found this tabular format to be the most human-readable way to batch create, edit, and troubleshoot metadata records. We can visually scan large numbers of records at once and normalize the values in ways that would be difficult with native nested formats, like JSON or XML. Therefore, many of our workflow processes involve transforming things to and from CSV.

## 4. Edit

:fontawesome-solid-user: Graduate Research Assistants and Product Manager 

When working with metadata, it is common to come across missing or corrupted values, which require troubleshooting and manual editing in our spreadsheets. Refer to the [Collections Project Board](https://github.com/orgs/geobtaa/projects/4) for examples of this work.

## 5. Validate

After compiling the metadata, we run a validation and cleaning script to ensure the records conform to the required elements of our schema. 

## 6. Index

:fontawesome-solid-user: Product Manager 

We upload the completed spreadsheet to GBL Admin, which serves as the administrative interface for the Geoportal. If GBL Admin detects any formatting errors, it will issue a warning and may reject the upload.

Once the metadata is successfully uploaded to GBL Admin, we can publish the records to the Geoportal. The technology that actually stores the records and enables searching is called [Solr](https://solr.apache.org). The action of adding records is known as "Indexing."



## 7. Maintain

:fontawesome-solid-user: BTAA-GIN Team Members, Graduate Research Assistants, and Product Manager 

Periodically, we need to remove records from the Geoportal. To do this, we use GBL Admin to either delete them or change their status to "unpublished."


We monitor currentness and re-harvest based on how frequently sources update their content. See the [Collections Dashboard](https://github.com/orgs/geobtaa/projects/4) for this schedule.


##  Sequence diagram of Resource Lifecycle

``` mermaid

	
	

	sequenceDiagram
   		actor Team Member
    		actor Product Manager
    		participant GitHub
    		actor Research Assistant
    		participant GBL Admin
    		participant Geoportal	
    			
    		
    		Note right of Team Member:  IDENTIFY
    		 
    		Team Member->>Product Manager: Submit Resources
    		Product Manager->>GitHub: Create GitHub issue
    		GitHub ->>Research Assistant: Assign issue
    		Note left of Research Assistant:  HARVEST
    		Note left of Research Assistant:  EDIT 
    		
    		Research Assistant->>GBL Admin: Upload records
    		Research Assistant ->>GitHub: Update GitHub issue
    		Note right of GBL Admin:  PUBLISH 
    		
    		Product Manager->>GBL Admin: Publish records
    		GBL Admin->>Geoportal: Send records online 
    		Product Manager->>GitHub: Close GitHub issue
    		Product Manager ->> Team Member: Share link to published records
    		
    		Note left of Research Assistant:  MAINTAIN 
    		
```

