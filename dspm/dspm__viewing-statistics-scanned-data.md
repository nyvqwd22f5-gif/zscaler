# Viewing the Statistics for Scanned Data
Source: https://help.zscaler.com/dspm/viewing-statistics-scanned-data
PDF: https://help.zscaler.com/pdf/com/en/1524381.pdf

The dashboard displays statistics of the total amount of data that was scanned in different data stores, the number of DLP engines and dictionaries used to classify the sensitive data, the geographic location of your cloud accounts, the number of alerts triggered for data stores containing sensitive data or vulnerabilities, and the ones that contain the maximum amount of sensitive data.
[See image.](#ds-datadiscovery-dashboard-gif)
Widgets
The Data Discovery tab on the dashboard includes the following widgets. You can apply filters to view specific data by business units, accounts, clouds, accounts, and regions.
- [Data Stores Discovered and Scanned](#ds-datadiscovered)
- [Data Discovery](#ds-datadiscoverywidget)
- [Top Accounts](#ds-topaccounts)
- [Top Data Stores](#ds-topdstores)
- [Data Insights](#ds-datainsights)
- [Data Region](#ds-mapregion)
[]
![The total amount of data discovered and scanned, including the data insight details](/downloads/dspm/dashboard/viewing-statistics-scanned-data/data-discovery-gif.gif)
[]The total number of records that are scanned and discovered in different types of data stores (resources) by category. Click the number to view additional details on the [Resource Inventory page](/dspm/about-resource-inventory).
DSPM classifies the data stores (resources) into the following categories:
- Storage
- Database
- Compute
- NoSQL Data Store
- Backup
- AI and Machine Learning
[]The chart displays the total number of files and tables that are scanned and discovered from all data stores.
-
**Gen AI Classification**: Click each circle to view the total number of files for a specific document type along with the documents' subcategories. Click the document number to view the resource details on the [Resource Inventory page](/dspm/about-resource-inventory).
[See image.](#ds-genai-classification-image)
-
**DLP Engines**: Click each circle to view the total number of files and tables along with DLP engines and dictionaries. You can select the **Show Sensitive Data Only** checkbox to view only those DLP engines that are marked as sensitive. Click the trigger number to view the resource details on the [Resource Inventory page](/dspm/about-resource-inventory).
[See image.](#ds-dlp-engine-image)
[]
![Shows total number of files for a specific document type along with the sub-categories of documents.](/downloads/dspm/dashboard/viewing-statistics-scanned-data/ds-data-dicovr-1.png)
[]
![Shows total number of files and tables along with DLP engines and dictionaries. ](/downloads/dspm/dashboard/viewing-statistics-scanned-data/ds-dlp-eng.png)
[]A world map shows the geographic regions where your sensitive data is located. Click the circle to view the number of data stores and data types (DLP engines used to classify the data) found in that region. You can also view the total number of sensitive records detected in different data stores and different data types. Click any record number to go to the [Resource Inventory page](/dspm/about-resource-inventory) and view additional resource details.
The size of the circles is relative to each other and depends on the number of sensitive records located in each region. A bigger circle indicates that the region has more number of sensitive records when compared to the region represented by the smaller circle. The number in the circle indicates that there are multiple regions in the same geographical location. Click the circle to view the details for each region.
[See image.](#data_region_image)
[]A high-level metric of the top 10 accounts that contain sensitive data and are at high risk. The accounts are displayed in descending order based on the amount of sensitive data in each account. Click the **Account Name** to view the resource details on the [Resource Inventory page](/dspm/about-resource-inventory).
[]The list of data stores that contain the maximum amount of sensitive data and are at high risk. The data stores are displayed in descending order based on the amount of sensitive data detected in them. Click the **Data Store** name to view the [Resource Inventory graph](/dspm/viewing-resource-inventory-graph) that visually depicts the records containing sensitive data, associated resources, entities that can access the data store, and whether the data store is publicly exposed to the internet.
[]View high-level information about the data in your cloud environments, such as files that were last accessed 90 days ago, the files that were not modified for more than 90 days, duplicate files, unencrypted data, etc. Click the number to view the details on the [Resource Inventory page](/dspm/about-resource-inventory).
![Shows the insights of the scanned data.](/downloads/dspm/dashboard/viewing-statistics-scanned-data/ds-data_insights.png)
[]![Regions where resources containing sensitive data are located](/downloads/dspm/dashboard/Regions%20where%20resources%20containing%20sensitive%20data%20are%20located_new.png)