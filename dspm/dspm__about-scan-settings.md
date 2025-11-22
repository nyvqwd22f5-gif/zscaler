# About Scan Settings
Source: https://help.zscaler.com/dspm/about-scan-settings
PDF: https://help.zscaler.com/pdf/com/en/1474741.pdf

DSPM regularly scans the cloud resources (data stores) such as cloud storage devices, databases, virtual machines. etc., within your cloud accounts and detects sensitive data and vulnerabilities. DSPM performs the scan by leveraging the[ local scan orchestrator](/dspm/understanding-orchestrator) that is deployed in your AWS, Azure, Google Cloud Platform (GCP), or On-Premises Data Centers account during the [onboarding process](/dspm/about-cloud-accounts). The resources are scanned against a set of standard [security policies](/dspm/about-data-posture-policies) and a scan schedule. In the scan rules, you can select the resources you want to scan, the scan type, and set the scan frequency. DSPM supports data scanning for different data stores and file types. To learn more, see [Supported Data Stores and File Types](/dspm/supported-data-stores-and-file-types).
The scan rule provides granular control over scan configurations. You can define custom scan types and schedules for individual data stores based on:
- Account
- Region
- Tags
- Specific resources
You can create multiple scan rules for supported data stores such as virtual machines, databases, and Snowflake accounts.
- You need to first onboard your cloud accounts before configuring the scan rule. To learn more, see [About Cloud Accounts](/dspm/about-cloud-accounts).
- Although overlapping scan rules are allowed, they can lead to duplicate scans and increased compute costs. DSPM displays warnings during rule creation to help you avoid redundant configurations.
- If a resource is deleted from the account after configuring the scan schedule, then DSPM ignores this resource during the scan.
The scan framework in DSPM provides the following benefits and enables you to:
- Configure the scan rule to scan your accounts and identify sensitive data.
- Regularly monitor your cloud accounts for any vulnerabilities.
- Select the required accounts for scanning and exclude some accounts from scanning.
- Configure the scan frequency and scan type.
Scan Types
DSPM supports the scanning of the following data stores. The scan type varies for each data store.
-
-
-
-
-
-
-
-
-
| Data Store | Scan Type |
| ---------- | --------- |
| Compute | **On-Demand Scan**: Perform an on-demand scan instantly. |
| Storage | **Full Scan**: Scan all the data in the selected data or object stores. This includes both the historic data and the newer data. Newer data scan is prioritized over historic data scan.**Scan Only New or Modified Files**: Scan only new or modified data or files in the accounts.**Historical Scan: Scan data or files over a lookback period in terms of days (max of 365 days).** |
| Managed Database | **Full Scan**: Scan all the data in the selected data or object stores. This includes both the historic data and the newer data. Newer data scan is prioritized over historic data scan.**Data Sampling Scan**: Scans a sample of recent data in the database. |
| NoSQL Datastore | **Full Scan**: Scan all the data in the selected data or object stores. This includes both the historic data and the newer data. Newer data scan is prioritized over historic data scan.**Scan Only Recent Data**: Scan only those files that are newly added or modified since the previous scan. This scan type is also applicable for unmanaged databases. |
| Unmanaged Database | **Data Sampling Scan**: Scans a sample of recent data in the database. |
About the Scan Settings Page
On the Scan Settings page (Administration > Scan Settings), you can see the following tabs:
- [Scan Rules](#scan_settings)
- [Scan Scopes](#scan_scope)
[]On the Scan Scopes tab, you can do the following:
- [Create a new scan scope.](/dspm/configuring-scan-scope)
- View the scan scope configurations. For each configuration, you can view the following information:
- **Scope**: Name of the scan scope. Click the scan scope name to view the following details.
- [Scan Scope Details](#Viewing_the_Scan_Scope)
- **Description**: A concise summary of the purpose and objectives of each scan scope.
- **Scan Rules**: Information on whether the scan scope is linked to any specific scan rule.
- **Created by**: The user who created the scan scope.
- **Created on**: The date and time when the scan scope was created
- [Show or hide the columns on the table.](/dspm/using-tables)
- Click the **Action** icon to [edit](/dspm/editing-or-deleting-scan-scopes) or [delete](/dspm/editing-or-deleting-scan-scopes) the scan scope.
[]![The Scan Scope page details all scan scopes.](/downloads/dspm/scan-settings/about-scan-settings/scanscope.png)
[]For each scan scope configuration, you can view:
- Name of the scan scope.
- **General Information**: Provides an overview of the scan scope, including:
- **Created by**: Name of the user who created the scan scope.
- **Created on**: Date and time the scan scope was created.
- **Description**: Brief summary of the scope.
- **Scope Criteria**: Defines the scan scope.
- **DLP Engines**: List of the DLP engines included in the scan scope.
- **File Type**: List of the file types included in the scan scope.
- **ML Categories**: Whether machine learning categories are enabled or disabled for the scan scope.
- **Scan Rules**: List of scan rules associated with the scan scope.
[See image.](#img_scan_scope_details)
[]![Scan Scope Details](/downloads/dspm/scan-settings/about-scan-settings/scan_scope_details.png)
[]On the Scan Rule tab, you can do the following:
- Add new scan rule for AWS, GCP, Azure, On-Premises, or Snowflake data center accounts.
- View the scan rule configurations for various resources. For each rule configuration, you can view:
- **Scan Rule**: Name of the scan rule. Click the scan rule name to view the following details.
- [Scan Rule Details](#Viewing_the_scanrule-details)
- **Description**: Optional summary that explains the purpose of the scan rule.
- **Cloud**: The name of the cloud service (AWS, Azure, GCP, or On-Premises Data Centers).
- **Resource Type**: The type of resource or data store (cloud storage, database, or virtual machine).
- **Scan Scope**: Information on whether the scan rule is linked to any specific scan scope.
- **Scan Status**: The scan status indicates the state of the scanning process. To learn more, see [Understanding Scan Status](/dspm/understanding-scan-status).
-
**Scan Enable/Disable**: The enabled or disabled state of the scan setting.
By default, the scan setting is disabled. After configuring the scan setting, you must [enable the scan setting](/dspm/enabling-or-disabling-scan-rule) to initiate the scan.
- **Added By**: Name of the user who created the scan scope.
- **Added On**: Date and time the scan scope was created.
- Sort the column data.
- [Show or hide the columns in the table](/dspm/using-tables).
- Click the **Action** icon to:
- [Edit or delete the scan rule](/dspm/editing-scan-setting).
- [Stop the scan](/dspm/starting-stopping-scan).
-
[Run an on-demand scan](/dspm/running-demand-scan)[.]
You can perform an on-demand scan only on databases and virtual machines.
[]![The Scan Rules page details all scan rules.](/downloads/dspm/scan-settings/about-scan-settings/ds-scan-rule-page.png)
[]For each scan rule configuration, you can view:
- **Name**: Name of the scan rule.
- **Description**: Optional summary that explains the purpose of the scan rule.
- **Status**: The scan status indicates whether the scan is enabled or disabled.
- **Cloud**: The name of the cloud service (AWS, Azure, GCP, or On-Premises Data Centers).
- **Resource Type**: The type of resource or data store (cloud storage, database, or virtual machine).
- **Scan Scope**: Information on whether the scan rule is linked to any specific scan scope.
- **Scan Type**: The method used to scan the resource.
- **Resources Scanned**: The number of resources discovered and scanned by this scan rule.
- **Added On**: Date and time the scan scope was created.
- **Added By**: Name of the user who created the scan scope.
[See image.](#ds-scandetails)
![The Scan Settings page details all the scan scopes and rules.](/downloads/dspm/scan-settings/about-scan-settings/ds-scan-settings.png)
[]![View the scan setting details](/downloads/dspm/scan-settings/about-scan-settings/ds-scan-rule-details.png)