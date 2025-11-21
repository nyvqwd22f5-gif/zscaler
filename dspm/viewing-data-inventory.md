# Viewing the Data Inventory
Source: https://help.zscaler.com/dspm/viewing-data-inventory
PDF: https://help.zscaler.com/pdf/com/en/1529820.pdf

Data Inventory provides details of files and tables containing sensitive data, and the locations where they are stored. Knowing where the files exist enables you to quickly locate the file and evaluate what type of sensitive data is stored and then take preventive actions to protect the files or remove sensitive data.
To view the file or table details:
- Go to **Analytics **> **Data Inventory**.
-
On the **Data Inventory** page, you can view the following details:
- **File/Table Name**: The name of the file or table. Click to view additional information:
- [Details](#ds-details_tab)
- [Evidence](#ds-evidence_tab)
- [Data Duplication](#ds-dataduplications_tab)
- **Path**: The file path.
- **Cloud Account**: The unique identifier for the cloud account that contains the file.
- **DLP Engines**: The DLP engines that match the file.
- **Document Types**: The document type to which the file belongs.
- **Hash**: The hash value is a unique identifier of the file or table. It is the same for identical files. A file hash is used as an indicator of compromise, which helps detect and respond to threats.
- **Last Modified Time**: The date and time the file was last modified.
- **Last Accessed Time**: The date and time the file was last accessed.
[See image.](#ds-datainventorypage)
- Export the data and [download the report](/dspm/downloading-reports) as an Excel file.
[]
Shows the properties of the selected file. Here you can view the file properties.
- **File Type**: The file format.
- **Last Modified Date**: The date when file was last modified.
- **File Path**: The path of the file.
- **File Size**: The size of the file.
- **DLP Engines**: The DLP engines that match the data in the file.
- **DLP Dictionaries**: The DLP dictionaries associated with the DLP engines.
- **Document Types**: The document type to which the file belongs.
- **Primary Resource Name**: The name of the primary resource.
- **Primary Resource ID**: The unique identifier for the primary resource.
- **Primary Resource Type**: The type of the primary resource.
- **Data Hosting Resource Name**: The name of the resource that hosts the file. It is the actual resource that contains the file.
- **Data Hosting Resource ID: **The unique identifier for the resource that hosts the file.
- **Data Hosting Resource Type**: The type of the resource that hosts the file.
[See image.](#ds-detailstab)
[]
Shows evidence data for the discovered file, which lets you validate the findings. You can view the trigger data along with the timestamp of the last scan time.
[See image.](#ds-evidencetab)
[]
Shows all the duplicate copies of the selected file or table.
[See image.](#ds-duplicatetab)
[]
![Shows the Data Inventory page that displays the scan results for sensitive files and tables.](/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-about-data-inventory-draft/ds-rn-datainventory.png)
[]
![Shows the property details of the selected file.](/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-about-data-inventory-draft/ds-new-details.png)
[]
![Shows the list of duplicate sensitive files.](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-data-inventory/ds-data_dupli.png)
[]
![Shows the evidence data for the scanned files and tables.](/downloads/dspm/analytics/viewing-data-inventory/DS-evidence.png)