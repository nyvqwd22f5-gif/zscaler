# About the Processing Queue
Source: https://help.zscaler.com/business-insights/about-processing-queue
PDF: https://help.zscaler.com/pdf/com/en/1506896.pdf

The Processing Queue page provides status information for uploaded contract files that are processed for metadata. Successfully processed contracts are moved to the [All Contracts](/business-insights/about-contracts) page.
The Processing Queue page provides the following benefits and enables you to:
- Track the status of the uploaded contract files.
- Stay informed about the action required to fix errors encountered during parsing the files.
About the Processing Queue Page
On the Processing Queue page (Applications > All Contracts > Processing Queue), you can do the following:
- [Upload contracts](/business-insights/uploading-application-contracts).
- Filter contracts by **Status**, **Date Added**, **Uploaded By**, **Vendor**, or **Applications**. Click the **Add** icon to show or hide the filter options.
- Export the data to a CSV file.
- Search for a contract in the table.
- View a list of uploaded contracts.
- [View elements for each uploaded file](#elements)
- [Modify the column menu](/business-insights/using-tables-business-insights).
- [Edit a contract](/business-insights/managing-queued-contracts). Use this option to fix any errors or warnings encountered during the processing of a contract file.
- Download the contract file. Only AI processed contracts are available for download.
-
Delete an uploaded contract file.
![The Processing Queue Page](/downloads/business-insights/processing-queue-contracts/Business-Insights-Processing-Queue-Page.png)
- []**File**: The name of the file.
- **Date Added**: The date when the file was uploaded.
- **Uploaded By**: The name and email address of the person that uploaded the contract file.
- **Vendor**: The name of the contract vendor.
- **Applications**: The name of the applications that are part of the contract.
- **Processing Status**: The status of the uploaded contract file:
- **In** **Progress**: The data is currently being processed from the contract file.
- **Error**: The Business Insights service encountered an error while processing the data in the file. Click the **Edit** icon for the contract to view the error and fix it.
- **Warning**: The warning status indicates that the contract is not mapped to an application. Click the **Edit** icon for the contract to fix it.