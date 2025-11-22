# Release Upgrade Summary (2024)
Source: https://help.zscaler.com/dspm/release-upgrade-summary-2024

This article provides a summary of all new features and enhancements for Posture Control (DSPM). To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com/).

**Clouds:** app.zsdpc.net, app.eu.zsdpc.net
The following service updates were deployed to app.zsdpc.net on

## December 09, 2024
### Feature Available
#### Data Posture Policies
The following new data posture policies are available for cloud service providers:
- [AWS](#ds-awspolicy-dec160)
- [Azure](#ds-azurepolicy-dec160)
- [GCP](#ds-gpolicy-dec160)
[]
| Policy Title |
| ------------ |
| S3 bucket contains malware. |
| S3 bucket containing sensitive data does not have a bucket policy with secure transport enforced for data in motion |
| EC2 instance containing malware has access to other data stores. |
| EC2 instance has EBS volumes containing malware. |
| EC2 instance containing sensitive data is connected to the default VPC. |
| EC2 instances with sensitive data in shutdown state for more than 30 days. |
| EC2 instance containing sensitive data can be accessed by identities with permissions to modify their security groups. |
| Publicly exposed AWS EC2 instance has EBS volumes containing malware. |
| RDS DB cluster containing sensitive data does not have auto minor version upgrade enabled. |
| RDS DB cluster containing sensitive data is accessed by a Lambda function that can be invoked via an unauthenticated public URL with risky IAM role. |
| RDS DB cluster containing sensitive data can be accessed by a Lambda function that has an unauthenticated public URL running deprecated Python and Node.js versions. |
| RDS DB instance containing sensitive data can be accessed by a Lambda function that has an unauthenticated public URL running deprecated Python and Node.js versions. |
| RDS DB instance containing sensitive data is accessed by a Lambda function that can be invoked via an unauthenticated public URL with risky IAM role. |
[]
| Policy Title |
| ------------ |
| Azure virtual machine containing sensitive data can be accessed by Entra ID applications that accept external or personal Azure accounts with high privileges. |
| Publicly exposed Azure virtual machine with CVSS 7 or higher has IAM access that can be exploited for ransomware attacks to delete resource locks, modify diagnostic logs, or delete backups. |
| Publicly exposed Azure virtual machine contains malware. |
| Azure virtual machine has disks containing malware. |
| Azure virtual machine containing malware has access to other data stores. |
| Azure virtual machine containing sensitive data has login with Entra AD enabled and is at risk of privileged access by users without MFA. |
| Azure SQL server with databases containing sensitive data can be accessed by Entra ID applications that accept external or personal Azure accounts with high privileges. |
| Azure SQL server with databases containing sensitive data can be accessed by publicly exposed Linux web app that have SSH enabled |
| Azure storage account containing sensitive blob data has infrastructure encryption disabled at storage account level. |
| Azure storage account has blob data containing malware. |
| Azure storage account containing sensitive blob data can be accessed by publicly exposed Linux web app that has SSH enabled. |
[]
| Policy Title |
| ------------ |
| GCP storage bucket with managed folders containing sensitive data has soft delete disabled. |
| GCP storage bucket containing sensitive data encrypted with KMS keys has keys that can be accessed by users without MFA. |
| GCP storage bucket with managed folders containing sensitive data encrypted with KMS keys has keys that can be accessed by users without MFA. |
| GCP storage bucket contains malware. |
| GCP storage bucket containing sensitive data can be accessed by users without MFA and they can disable soft delete and versioning. |
| GCP storage bucket with managed folders containing sensitive data can be accessed by users without MFA and they can disable soft delete and versioning |
| GCP storage bucket is publicly exposed with anonymous write access. |
| GCP storage bucket containing sensitive data does not have Admin, Data Read, and Data Write logs enabled. |
| GCP storage bucket with managed folders containing sensitive data does not have Admin, Data Read, and Data Write logs enabled. |

### Feature Available
#### DSPM Engine Scope
Scan scope allows you to run DLP engines on file types that are relevant for these engines. This enables optimized data scanning and reduces false data detection.
[See image.](#scan_scope)
To learn more, see [Configuring Scan Scope](/dspm/configuring-scan-scope) and [Understanding DLP Engines and Dictionaries](/dspm/understanding-dlp-engines-and-dictionaries).
[]![Configuring the scan scope in scan settings page](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/rn_scan_scope.png)

### Feature Available
#### DSPM Integrated with Zscaler Cloud Connector Scan Framework
The DSPM scan framework now supports networks using the Zscaler Cloud Connector for internet-bound traffic. This integration enables to route the DSPM outbound internet traffic through Zscaler Cloud Connector, eliminating the need for public IP addresses.

### Feature Available
#### Enhancements to Alert Graph
The alert graph includes the following enhancements:
-
Interactive CVEs: Click a CVE ID to view the vulnerability details.
[See image.](#CVE_ID)
-
Vulnerability Search: Locate specific vulnerabilities, severity, and risk score using the search and filter options.
[See image.](#search_options)
-
Number of Files containing Sensitive Data: View the number of files containing the sensitive data under each node.
[See image.](#View_number_of_sensitive_files)
-
Link to Data Inventory page: Click the primary resource to view more details on the Data Inventory page.
[See image.](#Primary_resource_link)
To learn more, see [Viewing the Alert Graph](/dspm/viewing-alert-graph) and [Viewing the Data Inventory Graph](/dspm/viewing-data-inventory-graph).
[]
![CVE ID](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/CVE%20ID.png)
[]
![Search and filter options](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/Search%20and%20Filter%20Option.png)
[]
![Viewing number of sensitive files](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/Sensitive%20Files%20Label_1.png)
[]
![Primary resource link](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/Primary%20Resource.png)

### Feature Available
#### Enhancements to Data Inventory
The data inventory includes the following enhancements:
Renamed Columns
To enhance clarity, the following columns are renamed in the Data Inventory table:
- Last Scanned is now Last Completed Scan.
- Scan Status is now Latest Scan Status.
[See image.](#Last_completed_scan_and_Latest_scan_status)
Timestamped Error Messages
A timestamp is included in scan error messages to indicate when the error occurred.
[See image.](#Timestamped_error_messages)
Risk Level Filter
The risk level filter allows you to identify resources based on the risk levels. You can select one or more of the following risk levels:
- Critical
- High
- Medium
- Low
[See image.](#risk_level_filter)
Directly Access Individual Resources
You can directly access the individual resources from the Data Inventory Graph page.
[See image.](#redirecting_to_specific_resource)
Cloud Service Provider Appended to Resource Types
The cloud service provider (CSP) name is appended to the resource types (e.g., AWS EC Instance, Azure SQL Server, GCP Storage Bucket) to easily identify the resources.
[See image.](#cloud_context_in_datastores)
View Publicly Exposed Files
You can verify the list of publicly exposed files and folders that can be anonymously accessed by external users.
[See image.](#exposed_files)
To learn more, see [Viewing the Data Inventory Graph](/dspm/viewing-data-inventory-graph) and [Viewing the Public Exposure Path](/dspm/viewing-public-exposure-path).
Quantity of Data Scanned
The Data Inventory page displays the amount of data scanned for individual resources.
[See image.](#data_scanned)
View Access Levels
You can view the specific access levels associated with entities.
[See image.](#View_access_path)
To learn more, see [About Data Inventory](/dspm/about-data-inventory) and [Viewing the Data Inventory Graph](/dspm/viewing-data-inventory-graph).
[]
![Last completed scan and latest scan status](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/Scan%20Status%20Enhancements.png)
[]
![Timestamped error messages](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/Timestamped%20Error%20Messages.png)
[]
![View risk level filter](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/Risk%20Level%20Filter.png)
[]
![View redirecting to specific resource ](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/Redirect%20to%20Specific%20Resource%20in%20CSP.png)
[]
![Viewing cloud context in datastore types](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/Cloud%20Provider%20Context%20in%20Datastore%20Types_0.png)
[]
![Verify exposed files](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/Exposure%20Validation%20for%20Storage%20Accounts.png)
[]
![View data scanned for individual resources](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/Data%20Scanned%20New.png)
[]
![Viewing access path](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/Access%20Levels%20for%20Entitlements.png)

### Feature Available
#### Enhancements to Entitlements
Access Control with IAM Policies
AWS IAM policies allow you to define actions and controls based on context keys. The following context keys can be used in IAM policies, trust relationships, resource-based policies, and service control policies:
- aws:PrincipalTag/tag-key
- aws:ResourceTag/tag-key
- aws:PrincipalOrgID
- aws:PrincipalArn
Discover API Gateways with Access to Primary Resource
DSPM discovers API Gateways that have access to the primary resource via an IAM role.
To learn more, see [About Data Posture Policies](/dspm/about-data-posture-policies) and [Viewing the Resource Access Levels](/dspm/viewing-resource-access-levels).

### Feature Available
#### Insights Report
The Insights Report provides a quick overview of the key issues detected by DSPM across AWS, Azure, and GCP. Each tile displays a summary of all the alerts generated for the three CSPs, along with the associated threat category, total number of alerts, and the severity. You can click a tile to view the alerts related to the issue on the All Alerts page.
[See image.](#rn-insights-reports)
To learn more, see [About the Insights Report](/dspm/about-insights-report).
[]![DSPM Insights Report](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/dspm-insights-report.png)

### Feature Available
#### Investigation and Policy Query Enhancements
The investigation and policy queries are enhanced with the following predicates and operators for improved metadata analysis and enrichment.
Not Included In Operator
For the Access Level predicate, you can select the Not Included In (⊈) operator to exclude the required access level.
[See image.](#Not_Included_In_Operator)
iLike and Not iLike Operators
In addition to the existing Like and Not Like operators that allow string comparison using wild cards, you can now use the iLike (i%) and Not iLike (!i%) operators that are case-agnostic. These operators are useful for Azure-related queries, as some paths and metadata attributes with different case variants (e.g., customScript and customscript) might be shared by the Azure service in different scenarios.
[See image.](#View_iLike_and_Not_iLike_operator)
Predicates for DynamoDB
You can use the following relationship predicates to query DynamoDB resources:
- Can be accessed by
- Access Level over Parent Resource
[See image.](#DynamoDB_Entitlements)
To learn more, see [Creating an Investigation](/dspm/creating-new-investigation) and [Creating Custom Policies](/dspm/creating-custom-policies).
[]
![Select Not Included In Operator](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/Not%20Included%20In%20Operator.png)
[]
![View DynamoDB Entitlements](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/DynamoDB%20Entitlements.png)
[]
![View iLike and Not iLike operator](/sites/default/files/downloads/dspm/analytics/graphs/viewing-public-exposure-path/iLike%20and%20Not%20iLike%20Operator.png)

### Feature Available
#### Support for AWS DynamoDB
AWS DynamoDB is supported as a data store. Based on the scan setting configuration, DSPM scans and classifies data in the relevant DynamoDB tables and checks for misconfigurations and posture issues. All findings are displayed on the [Data Inventory page](/dspm/about-data-inventory).
NoSQL Data Stores
With the introduction of DynamoDB support, NoSQL data store is available as a new category in scan settings and the scan statistics are displayed on the dashboard.
[See image.](#Scan_NoSQL_Datastores)
To learn more, see [Configuring Scan Settings for AWS NoSQL Data Stores](/dspm/configuring-scan-settings-dynamodb).
[]![Selecting NoSQL Datastores](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/rn_%20select_nosqldb.png)

### Feature Available
#### View Reasons for Failed Integrations
You can see the reason for failed integrations. The message allows you to troubleshoot and resolve the issue.
[See image.](#integrations_page)
To learn more, see [About Third-Party Integrations](/dspm/about-third-party-integrations).
[]![Error Message in Third-Party Integrations Page](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/rn_dspm_tp_integrations.png)

## November 04, 2024
### Feature Available
#### Dashboard Enhancements
The dashboard provides a comprehensive view of risk and data insights through Risk and Data Discovery tabs, along with the data security posture risk score with a supporting trend chart.
Dashboard Tabs
The dashboard is updated to provide an extensive view of risk and data insights. The dashboard features two tabs: Risk and Data Discovery.
Risk tab: Displays Risk Score, Risk Score Trend, Top Risk Data Stores, and Open Alerts by Category.
Data Discovery tab: Displays Data Types and Data Regions.
[See image.](#dashboard_tabs)
To learn more, see [About the Dashboard](/dspm/about-dashboard).
[]
![View dashboard tabs](/sites/default/files/downloads/Dashboard%20Tabs_0.png)
Risk Score and Risk Score Trend Chart
The dashboard displays the current overall risk score for data security posture and a trend chart that illustrates risk score changes over time.
[See image.](#risk_tab)
To learn more, see [About the Dashboard](/dspm/about-dashboard) and [Understanding the Security Posture State.](/dspm/understanding-security-posture-state)
[]
![View risk tab](/sites/default/files/downloads/dspm/analytics/data-inventory/about-data-inventory/Risk%20Tab.png)

### Feature Available
#### Data Inventory Table Enhancement
The data inventory table is updated to provide a clear focus on key objects, enhancing user experience.
[See image.](#data_inventory_table)
To learn more, see [Viewing the Data Inventory Graph.](/dspm/viewing-data-inventory-graph)
[]
![Viewing data inventory table](/sites/default/files/downloads/Data%20Inventory%20Table.png)

### Feature Available
#### Data Posture Policies
The following data posture policies are available for cloud service providers:
- [AWS](#dspm-aws-oct150)
- [Azure](#dspm-azure-oct150)
- [GCP](#dspm-gcp-oct150)
[]
| Policy Title |
| ------------ |
| S3 buckets hosting a static website should not be directly exposed and must leverage CloudFront distributions. |
| S3 bucket containing sensitive data should deny access via presigned URL. |
| S3 bucket containing sensitive data has a bucket policy that allows access via presigned URL. |
[]
| Policy Title |
| ------------ |
| Azure virtual machine containing sensitive data can be accessed by users who have not logged in interactively for more than 90 days but have logged in via cached sessions or OAuth consent grant in the last 7 days. |
| Azure storage account containing sensitive blob data can be accessed by users who have not logged in interactively for more than 90 days but have logged in via cached sessions or OAuth consent grant in the last 7 days. |
| Azure virtual machine containing sensitive data can be accessed by users who have not logged in for more than 90 days. |
| Azure storage account containing sensitive blob data can be accessed by users who have not logged in for more than 90 days. |
| Azure SQL server has databases containing sensitive data that can be accessed by users who have not logged-in interactively for more than 90 days but have logged in via cached sessions or OAuth consent grant apps in the last 7 days. |
| Azure SQL server has databases containing sensitive data that can be accessed by users who have not logged in for more than 90 days. |
| Azure virtual machine containing sensitive data can be accessed by Entra ID applications with risky permissions and without certificate-based authentication. |
| Azure virtual machine with risky access to storage accounts containing sensitive blob data can be accessed by users with VM run commands. |
| Publicly exposed Azure storage account containing sensitive blob data has access keys enabled with Key 2 not rotated for more than 90 days. |
| Publicly exposed Azure storage account containing sensitive blob data has access keys enabled with Key 1 not rotated for more than 90 days. |
| Azure storage account containing sensitive blob data has anonymous read access enabled. |
| Azure virtual machines containing sensitive data can be accessed by external Entra ID users with risky permissions. |
| Publicly exposed Azure virtual machines with CVSS 7 or higher have IAM permissions that might lead to privilege escalation. |
| Azure storage account containing sensitive data can be accessed by Entra ID applications with risky permissions and without certificate-based authentication. |
| Azure storage account hosting a static website is publicly exposing sensitive data via $web container. |
[]
| Policy Title |
| ------------ |
| GCP storage bucket with managed folders containing sensitive data has a bucket lock that does not have a retention policy greater than or equal to 7 days. |
| GCP storage bucket with managed-folders containing sensitive data is publicly accessible. |
| GCP storage bucket with managed folders containing sensitive data is at risk of ransomware attack, as versioning, soft delete, and logging is disabled. |
| GCP storage bucket with managed folders containing sensitive data is not encrypted using customer-managed encryption keys. |
| GCP storage buckets containing sensitive data are not encrypted with customer-managed encryption keys. |
| GCP storage buckets containing sensitive data is publicly accessible. |
| GCP storage buckets containing sensitive data are at risk of ransomware attack, as versioning, soft delete, and logging are disabled. |
| GCP storage bucket containing sensitive data has soft delete disabled. |
| GCP storage bucket containing sensitive data does not have Admin, Data Read, and Data Write logs enabled. |
| Publicly accessible GCP bucket does not have usage logging enabled. |
| GCP storage buckets containing sensitive data encrypted with KMS keys do not have key rotation configured. |
| GCP storage bucket with managed folders containing sensitive data is encrypted with KMS keys that do not have key rotation configured. |

### Feature Available
#### Improved Scan Efficiency for EBS Volumes
EBS volumes attached to multiple EC2 instances or part of an Auto Scaling group are now scanned efficiently. The scanner maintains a cache of the previously scanned EBS volumes. When a new scan or a scheduled scan is initiated, the scanner takes into account the cache, resulting in improved scan performance, optimization, and reduced scan costs.
To learn more, see [About Scan Settings](/dspm/about-scan-settings).

### Feature Available
#### Investigation and Policy Query Enhancements
The investigation and policy queries are enhanced with the following predicates and operators for improved metadata analysis and enrichment:
Malware Predicates
You can use the malware-related predicates to check for the presence of any malware in the resources. The following predicates are available:
Has Malware: Check whether the resource has malware by selecting any of the following options:
- Malware Name: Specify the malware name.
- Malware Category: Specify the [malware category](https://threatlibrary.zscaler.com/).
- Detection Accuracy Level: Use the accuracy level to determine whether this is malware.
[See image.](#ds-malwarepredicate)
Resource Property Predicate
You can use the And operator and check for an object's multiple attributes in a metadata array.
[See image.](#ds-objectvalues)
AWS IAM Roles as Resource Types
The following AWS identity and management (IAM) role types are added as resource types. You can check if the role type is either associated with or can access the primary resource:
- IAM Role: A role that is the service principal of either the user or service.
- IAM Unmanaged Role: The service principal is a role and the service principal's ARN contains an account ID that is part of the onboarded AWS organization and also part of an AWS account that is not onboarded to DSPM.
- IAM External Role: The service principal is a role and the service principal's ARN contains an account ID that is not part of the onboarded AWS organization.
Predefined Lists
You can choose a predefined list of values for predicates. Lists allow a single point of management for multiple values usually used in policies. Currently, DSPM provides a predefined list of regions and vulnerabilities that are used as part of an active campaign.
[See image.](#ds-predefinedlist)
To learn more, see [Creating an Investigation](/dspm/creating-new-investigation) and [Creating Custom Policies](/dspm/creating-custom-policies).
[]![Select multiple object values](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/ds-multipleobjectvalues.png)
[]![Check if the resource contains malware](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/ds-malware.png)
[]![Select a list](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/ds-cvelist.png)

### Feature Available
#### Malware Analysis and Alerts
DSPM provides predefined policies to detect malware in data stores (AWS S3 bucket, AWS EC2 instance, Azure virtual machine, Azure storage account, Google Cloud Storage bucket) and generate alerts.
To learn more, see [Viewing Alert Details](/dspm/viewing-alert-details) and [Understanding Malware Scanning](/dspm/understanding-malware-scanning).

### Feature Available
#### Selecting Regions While Onboarding Accounts
While onboarding cloud accounts, you can specify the regions where you want DSPM to monitor the data. DSPM limits the deployment of scanner instances and the creation of roles to those specified regions only.
To learn more, see:
- [Onboarding an AWS Organization](/dspm/onboarding-aws-organization).
- [Onboarding a Microsoft Entra Tenant](/dspm/onboarding-microsoft-azure-tenant).
- [Onboarding a GCP Organization](/dspm/onboarding-gcp-organization).
- [Managing Regions](/dspm/managing-regions).

## September 30, 2024
### Feature Available
#### Adding Custom Tags to DSPM Resources
You can add custom tags to resources that are created by DSPM while onboarding cloud accounts. The tags enable efficient resource grouping, billing calculations, and applying security controls.
To learn more, see:
- [Onboarding an AWS Organization](/dspm/onboarding-aws-organization)
- [Onboarding a Microsoft Azure Tenant](/dspm/onboarding-microsoft-azure-tenant)
- [Onboarding a GCP Organization](/dspm/onboarding-gcp-organization)
- [Managing Custom Tags](/dspm/managing-custom-tags)

### Feature Available
#### Azure App Services Displayed in Data Inventory Graph
DSPM detects Azure App Services that have access to the primary data store and displays the details in the Data Inventory graph.
[See image.](#View_app_services)
To learn more, see [Viewing the Data Inventory Graph](/dspm/viewing-data-inventory-graph).
[]
![View app services details](/sites/default/files/downloads/dspm/analytics/data-inventory/viewing-malware-details/App%20Services.png)

### Feature Available
#### Data Posture Policies
The following data posture policies are available for cloud service providers:
- [AWS](#ds-awspolicies-sep140)
- [Azure](#ds-azurepolicies-sep140)
- [GCP](#ds-gcppolicies-sep140)
To learn more, see [About Data Posture Policies](/dspm/about-data-posture-policies).
[]
| Policy Title |
| ------------ |
| RDS DB clusters containing sensitive data can be modified, updated, or deleted by IAM users with stale access keys. |
| Publicly exposed RDS Aurora DB cluster containing sensitive data is running with a default master username and has IAM authentication disabled. |
| Publicly exposed RDS Aurora, MySQL, and PostgreSQL DB instances containing sensitive data are running with default master username and have IAM authentication disabled. |
| S3 buckets containing sensitive data can be accessed by an external user. |
| S3 buckets containing sensitive data can be accessed by external users with entitlements to modify block public access setting. |
| RDS MySQL and PostgreSQL DB clusters containing sensitive data do not have Cross-Region replication enabled. |
[]
| Policy Title |
| ------------ |
| Azure virtual machine containing sensitive data has disks that are at risk of public exposure and data exfiltration. |
| Azure storage account containing sensitive blob data can be accessed by publicly exposed vulnerable virtual machines with admin privileges. |
| Publicly exposed Azure Windows virtual machine with CVSS 7 or higher can access data stores and has automatic patching via Azure platform/OS disabled. |
| Publicly exposed Azure Linux virtual machine containing sensitive data with CVSS 7 or higher can access data stores and has automatic patching via Azure platform disabled. |
| Azure Linux virtual machine containing sensitive data and critical vulnerabilities does not have automatic patching via Azure platform enabled. |
| Publicly exposed Azure Linux virtual machines that can access other data stores have easy to guess usernames and have password authentication enabled. |
| Azure virtual machines that can access other data stores have default or easy to guess usernames. |
| Azure storage account containing sensitive blob data can be accessed by Entra ID applications that accept external or personal Azure accounts with high privileges. |
| Azure virtual machines contain more than one network interface. |
| Publicly exposed Azure virtual machines are at high risk of ransomware infection due to known exploited vulnerabilities used in ransomware campaigns and have an IAM identity that provides risky access to data stores. |
| Publicly exposed Azure virtual machines are at high risk of ransomware infection due to known exploited vulnerabilities used in ransomware campaigns. |
[]
| Policy Title |
| ------------ |
| GCP Storage buckets with managed folders containing sensitive data have versioning enabled and do not have lifecycle policies configured. |
| GCP Storage buckets with managed folders containing sensitive data do not have Bucket Lock with retention policy enabled. |
| GCP Storage buckets with managed folders containing sensitive data are not multi-region or dual-region. |
| GCP Storage buckets with managed folders containing sensitive data have versioning disabled. |
| GCP Storage buckets with managed folders containing sensitive data have soft delete enabled and have a retention period of less than 30 days. |
| GCP Storage buckets with managed folders containing sensitive data do not have usage and storage logging enabled. |
| GCP Storage buckets with a static website should not have uniform access control enabled. |
| GCP Storage buckets containing sensitive data do not have uniform access control. |
| GCP buckets containing sensitive data have versioning enabled but do not have lifecycle policies configured. |
| GCP Storage buckets containing sensitive data with Bucket Lock do not have a retention policy greater than or equal to 7 days. |
| GCP Storage buckets containing sensitive data do not have Bucket Lock with retention policy enabled. |
| GCP Storage bucket containing sensitive data is not multi-region or dual-region. |
| GCP Storage buckets containing sensitive data have versioning disabled. |
| GCP Storage buckets containing sensitive data have soft delete enabled with a retention period of less than 30 days. |
| GCP Storage bucket containing sensitive data does not have usage and storage logging enabled. |

### Feature Available
#### Filter Scope Enhancements in Alert Notifications & Ignore Alert Filter
The following enhancements are available for filter scope while adding an ignore alert filter and alert rule:
-
The Cloud Accounts filter includes GCP to filter alerts generated for GCP projects.
[See image.](#gcp-filterscope)
-
A new filter, DLP Engine, is available to filter alerts generated for resources containing files with the specified DLP engines.
[See image.](#dlpengines)
To learn more, see [Adding an Alert Rule](/dspm/adding-alert-rule) and [Adding Ignore Alert Filters](/dspm/adding-ignore-filters).
[]![View the Filter Scope](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/rn-dspm-gcp-filter-scope.png)
[]![View the Filter Scope](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/rn-dspm-dlp-engine.png)

### Feature Available
#### Investigation & Policy Query Enhancements
The investigation and policy queries are enhanced to include additional predicates and operators:
Azure App Services as Resource Type
When building an investigation or policy query, you can select Azure App Services as the resource type to check if they can access the primary data store.
[See image.](#ds-azureapps)
Permissions over Parent Data Store Predicates
When building a policy or an investigation query, it is now easier to identify the scope of permissions a specific resource has over the parent data store.
The following predicates are available:
- Action over Parent Resource
- Access Level over Parent Resource
[See image.](#ds-entitlements)
CVE Severity Predicates
You can use the "Include In (⊆)" operator to add multiple CVE severity values in an investigation or policy query.
[See image.](#ds-cveseverity)
External & Unmanaged User Resource Types
You can set a higher granularity level in the investigation and custom policy queries by selecting the following IAM resource types: IAM Users, Unmanaged Users, and External Users. These resource types are displayed in the Data Inventory and Access Path graphs.
[See image.](#ds-iamuser-entities)
Like & Not Like Operators
You can use the following operators to select wildcards as predicate values. This allows you to check for a partial match against any string value (single or array):
- (%): Like
- ! (%): Not Like
- [!(%)]: Not Like (no match for all array records)
[See image.](#ds-like-operators)
External & Internal Cross Account Access Paths
AWS provides a few ways to access resources that are outside the AWS account in which the data resides. DSPM investigation and custom policies can now identify risks related to data access, such as cross account or cross AWS organization access.
To learn more about all the preceding enhancements, see [Creating an Investigation](/dspm/creating-new-investigation) and [Creating Custom Policies](/dspm/creating-custom-policies).
[]![IAM resource types](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/ds-iamusers.png)
[]![Like operators](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/ds-likeoperators.png)
[]![Azure App Services](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/ds-azureappservices.png)
[]![Permission scope over parent data store](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/ds-parentaccess.png)
[]![Include the CVE severity](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/ds-cves.png)

### Feature Available
#### Scanner Update Service
The scanner update service is now gated behind Zscaler private endpoints. As a result, outbound connections from the orchestrator are now limited to specific service IPs.
To learn more, see [About Cloud Accounts](/dspm/about-cloud-accounts).

### Feature Available
#### Support for GCP Storage
DSPM provides support for onboarding and scanning Google Cloud Platform (GCP) Cloud Storage buckets and managed folders. You can onboard the required GCP projects and configure the scan settings. DSPM scans the onboarded accounts for sensitive data and misconfigurations.
The scan results are displayed on the [Data Inventory page](/dspm/about-data-inventory). You can create [custom policies](/dspm/about-data-posture-policies) and [investigation queries](/dspm/about-investigation) to further optimize the protection.
[See image.](#gcpcloud)
To learn more, see [Configuring Scan Settings for Google Cloud Storage](/dspm/configuring-scan-settings-gcp-cloud-storage).
[]![Select the GCP cloud and resource type](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/gcp-select-cloud.png)

### Feature Available
#### Support for Malware Scanning
DSPM now supports the scanning for malware threats in file-based data stores such as AWS S3 bucket, AWS EC2 instance, Azure Storage account, Azure Virtual Machine, and Google Cloud Storage.
You can select the option to perform a malware scan while [configuring the scan settings](/dspm/about-scan-settings). The scan results include the malware details, which are displayed in the [Data Inventory drawer](/dspm/viewing-malware-details).
[See image.](#malwarescan)
To learn more, see [Understanding Malware Scanning](/dspm/understanding-malware-scanning), and [About Scan Settings](/dspm/about-scan-settings).
[]![Enable Malware Scanning](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/malwarescan.png)

### Feature Available
#### Update to the Managed Identities Permissions
The permission list for managed identities created by DSPM is updated. DSPM can now update or delete only the resources that it creates in the Microsoft Entra tenant.
To learn more, see [IAM Roles and Permissions for Microsoft Azure](/dspm/iam-roles-and-permissions-microsoft-azure).

## August 22, 2024
### Feature Available
#### Cloud Accounts Onboarding
While onboarding cloud accounts using Terraform templates, you can specify the regions where you want DSPM to monitor and scan data. DSPM creates required resources for data scanning only in those specified regions.
[See image.](#specify-regions)
To learn more, see [Onboarding an AWS Organization](/dspm/onboarding-aws-organization) and [Onboarding a Microsoft Azure Tenant](/dspm/onboarding-microsoft-azure-tenant).
[]![Specify the regions](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/dspm-specify-regions.png)

### Feature Available
#### Data Posture Policies
The following data posture policies are available for cloud service providers:
- [AWS](#ds-awspolicies-aug130)
- [Azure](#ds-azurepolicies-aug130)
[]
| Policy Title |
| ------------ |
| RDS PostgreSQL or MySQL database instances containing sensitive data have multi-AZ standby enabled. |
| RDS MySQL and PostgreSQL database instances containing sensitive data do not have cross region replication enabled. |
| MySQL RDS instances containing sensitive data should have logging configured to export audit and error logs to CloudWatch. |
| MySQL and Aurora MySQL RDS clusters containing sensitive data should have logging configured to export audit and error logs to CloudWatch. |
| S3 buckets containing sensitive data can be accessed by a Lambda function which can be invoked via an unauthenticated public URL with risky IAM role. |
| S3 buckets that are publicly accessible have server access logging disabled. |
| S3 buckets leveraging ACLs have the object owner set as ObjectWriter. |
| S3 buckets containing sensitive data should not have bucket ACLs enabled. |
| S3 bucket containing sensitive data does not have a bucket policy attached. |
| RDS DB instance with sensitive data that can be accessed by IAM users who have not changed their passwords in 90 days. |
| RDS DB instance containing sensitive data can be accessed by IAM users with stale access keys. |
| RDS PostgreSQL DB cluster containing sensitive data should have logging configured to export PostgreSQL logs to CloudWatch. |
| S3 buckets containing sensitive data do not have object lock with retention policy configured. |
| S3 buckets containing sensitive data can be accessed by a Lambda function that has an unauthenticated public URL running deprecated Python and Node.js versions. |
[]
| Policy Title |
| ------------ |
| Azure Blob Storage account containing sensitive blob data has container point-in-time restore disabled. |
| Azure Blob Storage account that contains sensitive blob data is vulnerable to ransomware attacks. |
| Azure Storage account containing sensitive blob data has change feed disabled. |
| Azure Storage account containing sensitive data has network access list bypass that allows access from Azure Services. |
| Azure Storage account containing sensitive data can be accessed by external Entra ID users with risky permissions. |

### Feature Available
#### DSPM Filter Enhancements
Region Filter on the Dashboard
You can filter the data by regions to view data stored in specific locations.
[See image.](#region-filter)
To learn more, see [About the Dashboard](/dspm/about-dashboard) and [Using Filters](/dspm/using-filters).
[]
![Region Filter](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/Region%20Filter.png)
Exclude Filter for DLP Engines and Dictionaries
You can exclude specific DLP Engines or dictionaries by applying the Not In (≠) operator on the Data Inventory page.
[See image.](#exclude-option)
To learn more, see [Using Filters](/dspm/using-filters).
[]
![Not In filter](/sites/default/files/downloads/dspm/analytics/graphs/viewing-data-inventory-graph/Exclude%20Option%20in%20DLP%20Engines%20and%20Filters_0.png)

### Feature Available
#### Enhancements to RBAC Permissions
The user permissions to resolve or snooze alerts are updated. If you have permission to snooze alerts, you can also reset those alerts but cannot reset alerts that are manually resolved by other users, and vice versa.
To learn more, see [Managing Alerts](/dspm/managing-alerts).

### Feature Available
#### Enhancements to the Alert Details Tab
The Alert Details tab includes the following additional details:
- Policy Category
- Compliance Benchmark
- Compliance Category
[See image.](#alert-details)
To learn more, see [Viewing the Alert Details](/dspm/viewing-alert-details).
[]![Viewing the Alert Details tab](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/dspm-rn-alert-details-tab.png)

### Feature Available
#### Exclude VM Operating System Directories and Files from Data Scanning
You can exclude the operating system (OS) directories and files when you are scanning Azure and AWS virtual machines. This prevents unwanted scanning of specific data types, such as source code, OS files, and lengthy data scanning processes.
[For an AWS Virtual Machine](#exclude_awsvmos)
[For an Azure Virtual Machine](#exclude_azurevmos)
To learn more, see [Configuring Scan Settings for AWS Virtual Machine](/dspm/configuring-scan-settings-aws-virtual-machine), and [Configuring Scan Settings for Azure Virtual Machine](/dspm/configuring-scan-settings-azure-virtual-machine).
[]![Exclude AWS virtual machine operating system directories and files from data scans](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/exclude_awsvmos.png)
[]![Exclude Azure virtual machine operating system directories and files from data scans](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/exclude_azurevmos.png)

### Feature Available
#### Investigation and Policy Query Enhancements
Additional operators are available when creating an investigation or policy query:
**Fixed and Relative Time Operators**
The following operators are available for the Date predicate:
- Fixed time operators (related to a specific date)
- = : On (a specific date)
- |...| : Between (specific dates)
- ⇠| : Before a specific date
- ⇢| : After a specific date
- Relative time operators
- < : Less than (x days)
- > : More than (x days)
**Included In Operator**
For the Resource Property predicate, you can use the Included In (⊆ ) operator for Boolean values. This allows you to create queries with combinations of Null (∅), Doesn't Exist, and Boolean values.
To learn more, see [Creating a New Investigation](/dspm/creating-new-investigation) and [Creating Custom Policies](/dspm/creating-custom-policies).
Investigate Secondary Resources Attached to Primary Resource
When creating a custom policy or investigation, you can query secondary and tertiary cloud service provider (CSP) resources attached to the primary resource. This allows DSPM to access and detect risks in the secondary or tertiary resources (e.g., virtual machines and network security groups, or EC2 instance and network interface). You can use the Associated With predicate and leverage the resource relationships.
[See image.](#ds-secres)
To learn more, see [Creating a New Investigation](/dspm/creating-new-investigation) and [Creating Custom Policies](/dspm/creating-custom-policies).
[]![Querying a secondary resource](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/ds-secondaryresource.png)

### Feature Available
#### Records Renamed to Triggers
To align the terminology with other Zscaler products, Records and Matched Records are renamed to Triggers.
[See image.](#viewing-data-inventory)
To learn more, see:
- [Viewing Data Regions](/dspm/viewing-data-regions)
- [About Dashboard](/dspm/about-dashboard)
- [Viewing Data Inventory Graph](/dspm/viewing-data-inventory-graph)
- [Viewing Sensitive Data Details](/dspm/viewing-sensitive-data-details)
- [Viewing Alert Details](/dspm/viewing-alert-details)
[]
![Data Inventory](/sites/default/files/downloads/dspm/analytics/graphs/viewing-data-inventory-graph/Triggers.png)

## July 18, 2024
### Feature Available
#### Azure SQL Server Support
DSPM provides support for Azure SQL server as a datastore. Based on the configuration of scan settings, DSPM scans and classifies the data in all databases on Azure SQL servers. It identifies misconfigurations and posture issues, and runs dedicated predefined policies for Azure SQL.
[See image.](#azuredb-selectcloudtype)
You can see the scan results on the [Data Inventory page](/dspm/about-data-inventory) and [Alerts page](/dspm/about-alerts). You can create [custom policies](/dspm/about-data-posture-policies) and [investigation queries](/dspm/about-investigation) to further optimize the protection.
To learn more, see [Configuring Scan Settings for Azure Database](/dspm/configuring-scan-settings-azure-database).
[]![Select the cloud and resource type](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/azuredb-selectcloudtype.png)

### Feature Available
#### Critical Issues Notification
Post login, you can see a notification about issues that prevent DSPM from accessing the cloud accounts for data scan. For example, when you've modified the permissions in the cloud account due to which DSPM cannot access the data in your cloud accounts. You can access the Issues tab to investigate and resolve the issue.
[See image.](#ds-banner)
To learn more, see [Resolving Onboarding Issues](/dspm/resolving-onboarding-issues).
[]![Notification about critical issues](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/ds-configissuesbanner.png)

### Feature Available
#### Data Posture Policies
The following data posture policies are available for cloud service providers:
- [AWS](#ds-awspolicies-july120)
- [Azure](#ds-azurepolicies-july120)
To learn more, see [About Data Posture Policies](/dspm/about-data-posture-policies).
[]
-
-
-
| Policy Title |
| ------------ |
| Publicly exposed RDS cluster with sensitive data is running on the default port. |
| RDS database cluster containing sensitive data is at risk of ransomware attack. |
| S3 bucket with sensitive data that has versioning enabled does not have lifecycle rules configured. |
| EC2 instances containing sensitive data are not exposed to the internet but have public IP attached. |
| EC2 instances containing sensitive data without NITRO Enclaves enabled. |
| Publicly exposed EC2 instances have an IAM Instance profile attached and IMDS configuration with HttpPutResponseHopLimit greater than 1. |
| EC2 instances containing sensitive data have more than one network interface with source destination check disabled. |
| EC2 instances contain more than one network interface with source destination check disabled. |
| EC2 Instances containing sensitive data has the default network security group attached |
| EC2 Instances has the default network security group attached. |
| Publicly exposed AWS EC2 instances are at high risk of ransomware infection due to known exploited vulnerabilities used in ransomware campaigns and have IAM instance profile attached. |
| Publicly exposed AWS EC2 instances are at high risk of ransomware infection due to known exploited vulnerabilities used in ransomware campaigns and contain clear text access keys. |
| Publicly exposed AWS EC2 instances are at high risk of ransomware infection due to known exploited vulnerabilities used in ransomware campaigns. |
| **Intelligence-driven policies**: Prioritizing vulnerability issues based on vulnerabilities that are used in active campaigns is now easy to achieve with a new set of policies that highlight such issues. These are updated on an ongoing basis to keep the data up-to-date.Publicly exposed AWS EC2 instances are at high risk of ransomware infection due to known exploited vulnerabilities used in ransomware campaigns and have IAM instance profile attached.Publicly exposed AWS EC2 instances are at high risk of ransomware infection due to known exploited vulnerabilities used in ransomware campaigns and contain clear text access keys.Publicly exposed AWS EC2 instances are at high risk of ransomware infection due to known exploited vulnerabilities used in ransomware campaigns. |
[]
| Policy Title |
| ------------ |
| Azure virtual machine containing sensitive data is not encrypted using Azure Disk Encryption(ADE). |
| Azure storage account containing sensitive blob data has access keys enabled but expiry interval or logging action is not configured. |
| Azure storage account containing sensitive blob data has cross-tenant replication enabled. |
| Publicly Exposed Azure SQL Database server has databases containing sensitive data is susceptible to ransomware. |
| Azure SQL database server with Entra authentication enabled can be accessed by Azure Virtual Machines with critical vulnerabilities. |
| Azure SQL database server has databases containing sensitive data that has retention period of less than 7 days. |
| Azure SQL database server containing sensitive data has blob audit logging enabled with low data retention. |
| Azure SQL server has databases containing sensitive data that does not have Always Encrypted enabled. |
| Azure SQL server has databases containing sensitive data that do not have resource locks enabled. |
| Publicly exposed Azure SQL server has a database containing sensitive data. |
| Azure SQL server containing databases with sensitive data is not encrypted. |
| Azure SQL database server containing sensitive data can be accessed by insecure user credentials without MFA with risky permissions. |
| Azure SQL database server with Entra authentication enabled can be accessed by Publicly exposed Azure Virtual Machines with admin privileges and critical vulnerabilities. |
| Azure SQL database server containing sensitive data is at risk of data exfiltration. |
| Azure SQL server has databases containing sensitive data that does not have a replica configured. |
| Azure SQL database server has databases containing sensitive data that is not encrypted using Customer Managed Key. |
| Azure SQL server has databases containing sensitive data and does not have SQL ledger enabled. |
| Azure SQL Server has databases containing sensitive data with minimum TLS version set to an insecure version. |

### Feature Available
#### Enhancements to the Alert Details Tab
The Alert Details tab includes the following enhancements:
- The Resource Name has a link to access the resource details on the Data Inventory page for additional investigation.
- The Alert Status Reason describes the reason for the alert's transition state. It also indicates whether the alert transition is manual or automatic.
- The alert graph displays the vulnerabilities that are associated with primary and entity (IAM nodes) resources in CVE or software package view.
[See image.](#alert-details-tab)
To learn more, see [Viewing Alert Details](/dspm/viewing-alert-details) and [Viewing the Alert Graph](/dspm/viewing-alert-graph).
[]![Viewing the Alert Details Tab](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/dspm-rn-alert-tab.png)

### Feature Available
#### Folder Exclusion in Amazon S3 Buckets
Exclude specific Amazon S3 buckets or folders from data scans and classification by adding exclude rules in the scan settings. This prevents lengthy data scanning processes for buckets or folders containing irrelevant data, such as log files.
[See image.](#aws-cs-exclude)
To learn more, see [Configuring Scan Settings for AWS Cloud Storage](/dspm/configuring-scan-settings-aws-cloud-storage).
[]![Exclude S3 buckets](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/aws-cs-exclude.png)

### Feature Available
#### Investigation and Policy Query Enhancement
DSPM provides support for the following operators and functions:
The policy or investigation query using the Included In (**⊆** ) operator allows a combination of custom values and preset values such as Null (∅) and Doesn't Exist.
To learn more, see [Creating a New Investigation](/dspm/creating-new-investigation) and [Creating Custom Policies](/dspm/creating-custom-policies).

### Feature Available
#### Scan Statistics Displayed on the Dashboard
The DSPM dashboard displays the number of discovered and scanned resources categorized by databases, cloud storage, and compute services. You can click the displayed number to view the resource details on the Data Inventory page.
[See image.](#ds-statistics)
To learn more, see [About the Dashboard](/dspm/about-dashboard).
[]![ds-statistics.png](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/ds-statistics.png)

### Feature Available
#### Sensitive DLP Engine Filter
A new Sensitive DLP Engine filter is available on the Sensitive Data tab. You can filter the data to view files or tables that have one or more DLP engines marked as sensitive.
[See image.](#ds-dlpfilter)
To learn more, see [Viewing the Sensitive Data Details](/dspm/viewing-sensitive-data-details).
[]![Sensitive DLP Engine filter](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/ds-dlpenginefilter.png)
