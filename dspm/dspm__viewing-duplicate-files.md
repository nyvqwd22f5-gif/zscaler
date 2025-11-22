# Viewing Duplicate Files
Source: https://help.zscaler.com/dspm/viewing-duplicate-files
PDF: https://help.zscaler.com/pdf/com/en/1529294.pdf

Data duplication refers to the presence of one or more identical copies of data, either intentionally or unintentionally, in different locations in an organization’s infrastructure. These copies could be in the form of duplicate files.
DSPM scans the data stores and detects duplicate files, allowing you to validate and delete the extra copies to limit the exposure of data to unauthorized users and protect sensitive data.
The Data Duplications page has the following benefits and enables you to:
- View all the duplicate copies of files and tables in the data stores.
- View DLP engines and dictionaries that were triggered to detect duplicate files and tables.
- Remove duplicate data to save on storage, backup, and operational costs.
- Reduce the possibility of users creating duplicate files.
- Delete potentially outdated data.
About the Data Duplications Page
On the Data Duplications page (Analytics > Data Duplications), you can do the following:
- Apply [filters ](/dspm/using-filters)to view specific information.
- View the list of duplicate file and tables. For each file copy you can see:
- **File Path:** The path of the file.
-
**Copies:** The total number of copies detected (including the original file). Click the number for a detailed view of all the file copies and their attributes in a drawer.
[See image.](#ds-filecopyview)
- **DLP Engines** : The DLP engines that match the files.
- **DLP Dictionaries: **The DLP dictionaries that match the files.
- **Document Types:** The document type that matches the files.
- **Hash:** The file’s MD5 sum.
- **File Size:** The size of the file in KB (Kilobyte).
- **File Type:** The string representing the file type.
- **No. of Regions:** The number of regions where the duplicate copies are found.
- **No. of Accounts:** The number of cloud accounts in which duplicate copies are found.
- **Clouds:** The cloud service provider in which the duplicate copies are found.
-
Export the data and [download the report](/dspm/downloading-reports) as an Excel file.
[See image.](#ds-downloads)
[]
![Detailed view of all the file copies and their attributes.](/downloads/dspm/analytics/viewing-duplicate-files/ds-newcopies.png)
![Shows duplicated files detected in your system.](/downloads/dspm/analytics/viewing-duplicate-files/ds-data-duplications-counter.png)
[]
![Download the exported duplicate file report from My Downloads page.](/downloads/tech-pubs-drafts/dspm-draft-articles/data-duplications-dashboard-draft/ds-dataduplication_download.png)