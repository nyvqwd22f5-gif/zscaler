# About Resource Inventory
Source: https://help.zscaler.com/dspm/about-resource-inventory
PDF: https://help.zscaler.com/pdf/com/en/1478076.pdf

Sensitive data such as personally identifiable information (PII), protected health information (PHI), financial records, social security number, etc., are confidential and valuable information that must be protected and kept secure at all times. Not knowing where the sensitive data is stored or not protecting this data is a huge risk, which could lead to data breaches such as hackers accessing valuable data and exploiting the vulnerabilities in the system. In addition, it could also lead to financial and compliance issues. Therefore, it is crucial to know where your sensitive data is stored within your cloud environment, so you can implement strong security controls to keep the data secure.
DSPM [scans your cloud resources](/dspm/about-scan-settings) or data stores for sensitive data and vulnerabilities and displays the scan results on the Resource Inventory page. You can view the list of resources containing sensitive data, the cloud accounts in which the resources are stored, regions where these accounts are located, severity of risk associated with the resources, different types of sensitive data, security posture, the predefined [DLP engines and dictionaries](/dspm/understanding-dlp-engines-and-dictionaries) that matched the sensitive records, document types, scan schedule, and much more. You can also export this data and download the report as an Excel file.
The scan results are also displayed as [graphs](/dspm/viewing-data-inventory-graph) that provide granular information on the resource and the sensitive records stored in it, including the [public exposure path](/dspm/viewing-public-exposure-path) and [user access path](/dspm/viewing-user-access-path).
Resource inventory has the following benefits and enables you to:
- View the scan results for the resources.
- View the type of sensitive data stored in the resources.
- View the vulnerabilities detected in the primary and associated resources.
- View the malware in the resources.
- Know the geographic location of the resource.
- View the severity of risk associated with the resource containing sensitive data.
- View the security posture of the resource.
- View the IAM entities that can access the resource.
- View the different types of documents classified by categories, which are present in the data stores.
- Take immediate action to resolve the issues and protect your sensitive data.
About the Resource Inventory Page
On the Resource Inventory page (Analytics > Resource Inventory), you can do the following:
- View the list of resources. For each resource, you can see:
- **Resource Name**: The name of the cloud resource.
- **Resource ID**: The unique identifier for the resource.
- **Cloud Account**: The unique identifier for the cloud account that contains this resource.
- **Business Unit**: The [business unit](/dspm/about-business-units) to which the account belongs.
- **Risk Level**: The severity of the risk (Critical, High, Medium, or Low) associated with the resource.
- **Malware**: The resources containing malware.
- **DLP Engines**: The number of sensitive records that match the DLP engine.
- **DLP Dictionaries**: The number of sensitive records that match the dictionaries.
-
**Document Types**: The different types of documents detected by [machine learning (ML)-based DLP dictionaries](/zia/understanding-predefined-dlp-dictionaries).
[See image.](#ds-documenttypes)
- **Document Categories**: The category (**Financial**, **Legal**, **Health**, etc.) to which the document belongs.
- **Open Alerts**: The number of [alerts](/dspm/viewing-alert-details) in Open state.
-
**Posture**: The security posture (publicly exposed, no logging, etc.) of the resource. Hover over the label to see the description for each posture. To learn more, see [Understanding the Security Posture State](/dspm/understanding-security-posture-state).
[See image.](#ds-posturetooltip)
- **Region**: The region where the resource is located.
- **Last Completed Scan**: The date and time the resource was last scanned.
- **First Discovered**: The date and time the sensitive data was first discovered in this resource.
- **Total Scanned**: The total number of files scanned.
- **Data Scanned**: The total amount of data processed during the scan. The data scanned is shown only for the resources configured with a full scan. To learn more, see [About Scan Settings](/dspm/about-scan-settings).
- **Latest Scan Status**: The latest scan status indicates the state of the scanning process. To learn more, see [Understanding Scan Status](/dspm/understanding-scan-status). For failed or unsupported scans, hover over the **Failed **or **Unsupported **labels to see the error message. The error message contains the timestamp to indicate when the error occurred, resource ID, and error reason. Click the **Copy** icon to copy the resource ID.
[See image.](#scan-settings-tool-tip)
- **File Hash**: The hash of the file.
- [Click the Resource Name to](/dspm/understanding-scan-status)[ view additional details](/dspm/viewing-resource-details) about the resource.
- Apply [filters](/dspm/using-filters) to view specific data.
- Click the Add icon (![ds-addfiltericon.png](/downloads/dspm/data-inventory/about-data-inventory/ds-addfiltericon.png)
) to apply additional filters.
-
View the security posture of the resource.
[See image.](#ds-posturetypes)
-
View the list of DLP engines that match the sensitive records.
[See image.](#dataengine)
-
View the list of DLP dictionaries included in the DLP engine.
[See image.](#dictionary)
- Sort the column data.
- [Show or hide columns in the table](/dspm/using-tables).
- Search for specific data in the searchable columns.
- Export the results and [download the report](/dspm/about-reports) as an Excel file. If you are unable to view all the records in the downloaded report, Zscaler recommends you apply relevant filters before exporting.
-
Customize the page view by applying filters, sorting the column data, modifying the table columns, or increasing the number of rows and saving this setting so you can see the same view every time you visit the page.
- [Saving a Page View](#ds-save-view-steps)
[See image.](#ds-saved-view)
You can save multiple page views and delete a view as required.
![The scan results for various resources](/downloads/tech-pubs-drafts/dspm-draft-articles/1-14-0-about-resource-inventory/ds-resource-inventory-14.png)
[]
- On the **Resource Inventory **page, click **Default View** and select **Save as New View**.
The **Save View** window appears.
- In the **Save View** window:
- **View Name**: Enter the name for the view.
- **Description **(Optional): Enter a description if required.
- Select the **Set as Default View** checkbox to set this view as default.
-
Click **Save**.
![Shows steps to create a page view](/downloads/tech-pubs-drafts/dspm-draft-articles/1-14-0-about-resource-inventory/ds-save-steps.png)
[]![The DLP engines that match the sensitive records](/downloads/dspm/analytics/data-inventory/about-data-inventory/ds-dlpengineinfo.png)
[]![The list of DLP dictionaries that match the sensitive ecords](/downloads/dspm/analytics/data-inventory/about-data-inventory/ds-dictionaryinfo.png)
[]![The document types that are stored in the resource](/downloads/dspm/analytics/data-inventory/about-data-inventory/ds-documenttypes.png)
[]![The different security posture labels applied to the resource](/downloads/dspm/analytics/data-inventory/about-data-inventory/Posture%20Types.png)
[]![The details of the security posture applied to the resource](/downloads/dspm/analytics/data-inventory/about-data-inventory/About%20Data%20Inventory%20-%20PMK%20Encrypted.png)
[]
![The reason why the scan failed](/downloads/dspm/analytics/data-inventory/about-data-inventory/ds-failedscanreason.png)
[]
![Shows the steps to save a view](/downloads/tech-pubs-drafts/dspm-draft-articles/1-14-0-about-resource-inventory/ds-saved-view-ui.png)