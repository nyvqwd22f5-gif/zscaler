# Viewing the Sensitive Data Details
Source: https://help.zscaler.com/dspm/viewing-sensitive-data-details
PDF: https://help.zscaler.com/pdf/com/en/1478121.pdf

You can view additional details of sensitive data that is present in the cloud resources (data stores).
To view the sensitive data:
- Go to **Analytics **> **Resource Inventory**.
The **Resource Inventory **page appears.
-
Click any **Resource Name** to view the drawer.
[See image.](#ds-di-clickrname)
- Select the **Sensitive Data** tab.
[See image.](#ds-sensitive-data-tab)
The sensitive data detected in an AWS EBS volume is provided here as an example.
- **Matched Files**: The total number of files that matched the DLP engines.
- **Triggers**: The total number of records that matched the DLP engines.
- **DLP Engines**: The total number of [DLP engines](/dspm/understanding-dlp-engines-and-dictionaries) used to classify sensitive data.
- **DLP Dictionaries**: The total number of [DLP dictionaries](/dspm/understanding-dlp-engines-and-dictionaries) in the DLP engines.
- **Document Types**: The total number of documents (financial, legal, etc.) based on the ML categories.
-
**View Sensitive data for**: Select the resource for which you want to view sensitive data. This option is only available for AI services.
[See image.](#ds-sensitivedata-dropdown)
- **File Name**: The name of the file containing sensitive data. Click to view the file details in a drawer that includes the following tabs:
- [Details](#ds-details-tshow-hide)
- [File Access](#ds-file-access-show-hide)
- [Evidence](#ds-evidence-show-hide)
- **File Path**: The file path.
- **Volume**: The EBS volume attached to the EC2 instance. For Azure, it is a storage account container.
- **File Type**: The type of file (e.g., .txt, .doc, etc.).
- **File Size**: The file size.
- **DLP Engines**: The DLP engines used to classify sensitive data.
- **DLP Dictionaries**: The DLP dictionaries within the DLP engines.
- **Document Types**: The list of documents (financial, legal, etc.) found in this resource.
- **File Hash**: The hash of the file.
- **Last Completed Scan**: The date and time the file was last scanned.
- **Created Date**: The date and time the file was created.
[]View the file properties. Click **Actions **and select **View Original File** to go to the exact file location on the third-party console.
[See image.](#ds-detailstab)
[]Evidence lets you validate the findings and view trigger data along with the last scan. This tab is shown for some AWS and Azure files depending on the data.
[See image.](#ds-evidencetab)
[]View the details of identities having access to the file containing sensitive data along with the actions performed on the file in the last 7 days. Gaining visibility into the user activities, particularly if there is any malicious activity, such as exfiltration of sensitive data, uploaded data that could corrupt the storage bucket used for generative AI (Gen AI), etc., helps mitigate any risks and protect the sensitive data.
[See image.](#ds-fileaccesstab)
File access information is shown for files stored in AWS S3 buckets and for those files that match the DLP engine and Gen AI classification.
- **Event Name: **The specific action (read or edit) performed on the file.
- **Principal Name: **The identity that accessed the file.
- **Principal Type**: The type of the principal.
- **Source IP: **The source IP address of the entity.
- **Last Activity Time:** The date and time the identity last performed any action on the file.
[]
![Sensitive data discovered in an EBS volume](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-sensitive-data-details/ds-sensitive-data-details.png)
[]
![Click the resource name to view the sensitive data details](/downloads/dspm/analytics/data-inventory/viewing-sensitive-data-details/ds-awsebsvolume.png)
[]
![Select resource types from the drop-down.](/downloads/tech-pubs-drafts/business-insights-draft-articles/draft-viewing-sensitive-data-details/ds-sensitivedata-drop-down.png)
[]
![Displays property details of the selected file.](/downloads/tech-pubs-drafts/dspm-draft-articles/1-11-0-viewing-statistics-scanned-data-draft-1/ds-details_tab.png)
[]
![Shows the trigger data along with the timestamp of the last scan time.](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-sensitive-data-details/DS-evidence.png)
[]
![Shows the details of file access](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-sensitive-data-details/ds-fileaccesstab.png)