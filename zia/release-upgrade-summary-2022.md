# Release Upgrade Summary (2022)
Source: https://help.zscaler.com/zpc/release-upgrade-summary-2022

This article provides a summary of all new features and enhancements for Zscaler Posture Control (ZPC). To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com/).

**Clouds:** app.zpccloud.net, eu.zpccloud.net
The following service updates were deployed to app.zpccloud.net on

## December 08, 2022
### Feature Available
#### Alerts Page Enhancements
Bulk Operation Support
You can now perform actions (i.e., Resolve, Unresolve, Ignore, or Unignore) on multiple alerts simultaneously by selecting the checkbox on the Alerts table.
[See image.](#alert-checkbox)
To learn more, see [About Alerts](/zpc/about-alerts) and [Ignoring or Resolving Alerts](/zpc/ignoring-or-resolving-alerts).
Cloud Alert Drawer Enhancements
The cloud alert drawer now allows you to:
- View properties, remediation, and compliance associated with the cloud alert.
- Perform actions (i.e., Resolve, Unresolve, Ignore, or Unignore), depending on the cloud alert status.
[See image.](#alert-drawer)
To learn more, see [About Alerts](/zpc/about-alerts).
[![View the Cloud Alert Drawer](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/cloud-alerts-drawer-enhancement.png)
]
[![View the Alert page](/sites/default/files/downloads/zpc/alerts/about-alerts/ignore-alerts-checkbox.png)
]

### Feature Available
#### Asset Timeline Enhancements
On the Asset Timeline tab, you can now:
- View the changes on the cloud asset, investigate incidents, and perform potential root cause analysis of the same. For Amazon Web Services (AWS), you can also view the account ID and request parameters during resource state creation or update.
[See image.](#timeline-asset-details)
- View the alerts triggered by the events as part of the data collection activity. Users can now figure out what led to a violation or incident by looking at the preceding events captured in the timeline.
[See image.](#timeline-alerts)
To learn more, see [About Cloud Asset Details](/zpc/about-cloud-asset-details).
[![View the Alert details](/sites/default/files/downloads/zpc/cloud-posture/cloud-assets/about-cloud-asset-details/zpc-timeline-alerts.png)
]
[![View the Cloud Asset details](/sites/default/files/downloads/zpc/cloud-posture/cloud-assets/about-cloud-asset-details/zpc-timeline-resource-param.png)
]

### Feature Available
#### Audit Logs Support
ZPC now supports the audit logs feature and records session information for every administrator who signs in to the ZPC Admin Portal. The audit logs provide a chronological list of activities performed by users in the tenants that are onboarded to ZPC.
[See image.](#audit-log)
To learn more, see [About Audit Logs](/zpc/about-audit-logs).
[![View the Audit Log details](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/audit-log.png)
]

### Feature Available
#### AWS Windows Workload Scanning
The agentless vulnerability scanning of Amazon Web Services (AWS) Windows workloads is supported. The following Windows server versions are supported: 2016, 2019, and 2022.
To learn more, see [Configuring Vulnerability Scanning for AWS Workloads](/zpc/configuring-vulnerability-scanning-aws-workloads).

### Feature Available
#### Filter Enhancements
ZPC offers new filters for security policies:
- Policy Severity: Returns security policies of specific severity (Critical, High, Medium, or Low).
- Theme: Returns security policies of specific theme (Compliance, Security Events, or Security Exposure).
- Policy Threat Category: Returns security policies of specific threat category (Ransomware, Misconfiguration, or Account takeover).
- MITRE ATT&CK: Returns security policies of a specific MITRE technique.
- Policy State: Returns enabled or disabled security policies.
- Allow Skip: Returns security policies that have Allow Skip enabled.
To learn more, see [Using Filters](/zpc/using-filters).

### Feature Available
#### Ignore Alerts
You can now ignore alerts that are triggered for a specific policy violation when the issue is not critical and does not require immediate action.
[See image.](#ignore-alerts)
You can also create ignore filters to ignore newly triggered alerts.
[See image.](#ignore-filters)
To learn more, see [About Alerts](/zpc/about-alerts) and [Ignoring or Resolving Alerts](/zpc/ignoring-or-resolving-alerts).
[]![View the Alert details](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/ignore-alert.png)
[![View the Ignored alerts](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/ignore-filter.png)
]

### Feature Available
#### Infrastructure as Code (IaC)
Support for Scanning Bicep Files
IaC now supports the scanning of Bicep files. You can use the Bicep CLI to convert Bicep files into JSON files (Azure Resource Manager (ARM) templates) and scan the JSON files for misconfigurations and policy violations.
To learn more, see [Parsing Bicep Files](/zpc/parsing-bicep-files).
Minor Improvements
A few improvements have been implemented in the IaC onboarding workflow.
To learn more, see [About IaC Integrations](/zpc/about-iac-integrations).

### Feature Available
#### Kubernetes Support
ZPC now supports Kubernetes accounts. You can onboard AWS EKS Kubernetes clusters and gain insight into their security posture via the asset inventory.
To learn more, see [Onboarding an Amazon Elastic Kubernetes Service Cluster](/zpc/onboarding-amazon-elastic-kubernetes-service-cluster).

### Feature Available
#### Security Policies
Added the following security policies for cloud service providers:
- [Amazon Web Services](#aws-2-2)
- [Microsoft Azure](#azure-2-2)
To learn more, see [About Security Policies](/zpc/about-security-policies).
[]
Security Policy Title
Ensure that Diagnostics logs enabled with storage account have a retention period of at least 365 days for Azure Key Vaults
Ensure that Diagnostics logs enabled with storage account have a retention period of at least 365 days for Azure Kubernetes Service
Ensure that Resource Locks are set for mission critical Azure resources
Ensure that Soft Delete is enabled for Key Vault
Ensure that diagnostics settings should be enabled on Application Gateway
Ensure that Logging is enabled for Azure Key Vault
Ensure that diagnostic settings should be enabled for SQL managed instance service
Ensure that 'Public access level' is set to Private for Blob Containers
Ensure web app has 'Client Certificates (Incoming client certificates)' set to 'On'
Internet-facing Virtual Machine is vulnerable to a OpenSSL high severity vulnerability
Virtual machine is vulnerable to a OpenSSL high severity vulnerability
[]
Security Policy Title
EC2 instance is vulnerable to a OpenSSL high severity vulnerability
Internet-facing EC2 instance is vulnerable to a OpenSSL high severity vulnerability

## October 13, 2022
### Feature Available
#### Azure Windows Workload Scanning
The agentless vulnerability scanning of Azure Windows workloads is supported. The following Windows server versions are supported: 2016, 2019, and 2022.
To learn more, see [Configuring Vulnerability Scanning or Azure Linux and Windows Workloads](/zpc/configuring-vulnerability-scanning-azure-linux-and-windows-workloads).

### Feature Available
#### Custom Roles
You can add, edit, or delete custom roles and set permissions for users to access or manage specific modules in the ZPC Admin Portal.
[See image.](#add-role)
To learn more, see [Adding a Custom Role](/zpc/adding-custom-role), [Editing a Role](/zpc/editing-role), and [Deleting a Custom Role](/zpc/deleting-custom-role).
[![Add a custom role](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/add-custom-role.png)
]

### Feature Available
#### Enhancements to Vulnerability Scanning
The following enhancements are implemented in Vulnerability Scanning:
- You can perform vulnerability scanning on Amazon Web Services (AWS) managed keys encrypted volumes, in addition to Customer Managed Keys (CMKs) encrypted volumes.
- The vulnerability scanning for Linux workloads that are created using AWS marketplace Amazon Machine Images (AMIs) is supported, except appliance AMIs.
To learn more, see [Configuring Vulnerability Scanning for AWS Linux Workloads](/zpc/configuring-vulnerability-scanning-aws-linux-workloads).

### Feature Available
#### Export Alert Data
You can export the Cloud or IaC alert data to an Excel file and download the report.
[See image.](#export)
To learn more, see [About Alerts](/zpc/about-alerts) and [Downloading Reports](/zpc/downloading-reports).
[![Exporting alert data](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/alerts-export.png)
]

### Feature Available
#### Filter Enhancements
The following enhancements are now available for ZPC filters:
- ZPC offers filter management. You can save a filter, and edit and delete a saved filter.
[See image.](#managing-filters)
- ZPC offers new filters for security policies:
- Policy Severity: Returns security policies of specific severity (Critical, High, Medium, or Low).
- Theme: Returns security policies of specific theme (Compliance, Security Events, or Security Exposure).
- Policy Threat Category: Returns security policies of specific threat category (Ransomware, Misconfiguration, or Account takeover).
- MITRE ATT&CK: Returns security policies of a specific MITRE technique.
- Policy State: Returns enabled or disabled security policies.
- Allow Skip: Returns security policies that have Allow Skip enabled.
- ZPC offers new filters for Microsoft Azure compliance benchmarks:
- Resource Group: Returns compliance benchmark details for a specific resource group.
- Tags: Returns compliance benchmark information for assets with specific tags.
To learn more, see [Using Filters](/zpc/using-filters).
[]
![View how to manage saved filters](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/zpc-save-filter.png)

### Feature Available
#### IaC Alerts Table Enhancement
You can view the list of alerts triggered for misconfigurations detected in your IaC infrastructure in the following tabs:
- Scans: Lists the scans completed for an alert.
- Policies: Lists the policies for an alert.
- All: Lists all the alerts.
[See image.](#iac)
To learn more, see [About Alerts](/zpc/about-alerts).
[![View the Alert details](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/iac-alerts-tab.png)
]

### Feature Available
#### Infrastructure as Code (IaC)
Supported Functions
Zscaler IaC Scan can parse the following functions:
- The Date and Numeric functions in ARM templates are supported.
- The Date, Time, and File System functions in Terraform templates are supported.
To learn more, see [About IaC Templates and Supported Functions](/zpc/about-iac-templates-and-supported-functions).
Reauthorization of IaC Integrations
You can reauthorize the IaC integration with Azure DevOps and GitLab in the event the authorization has expired or if the integration was unintentionally revoked.
To learn more, see [Configuring IaC Scan for GitLab](/zpc/configuring-iac-scan-gitlab) and [Configuring IaC Scan for Azure Repos](/zpc/configuring-iac-scan-azure-repos).
Advanced Settings for Terraform Cloud Integration
You can use the Advanced Settings for Terraform Cloud integration and select the severity level for failing a build.
[See image.](#terraform)
To learn more, see [Configuring IaC Scan for Terraform Cloud](/zpc/configuring-iac-scan-terraform-cloud).
Authentication for Visual Studio and CLI
Authentication for Visual Studio Code and command-line interface (CLI) now launches into the browser and supports users mapped to multiple tenants.
To learn more, see [Configuring IaC Scan for Visual Studio](/zpc/configuring-iac-scan-visual-studio) and [Configuring the IaC CLI Scanner](/zpc/configuring-iac-cli-scanner).
Remediation Procedure in IDE/CLI
The remediation procedure is now available within the Visual Studio integrated development environment (IDE) window and the command-line interface (CLI) along with the option to access the alert details in the ZPC Admin Portal. This enables developers to follow the remediation steps and easily resolve the misconfigurations and policy violations.
To learn more, see [Configuring IaC Scan for Visual Studio](/zpc/configuring-iac-scan-visual-studio) and [Configuring the IaC CLI Scanner](/zpc/configuring-iac-cli-scanner).
[![Advanced settings for Terraform Cloud integration](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/zpc-terraform-advancedsettings.png)
]

### Feature Available
#### Security Policies
Added the following security policies for cloud service providers:
- [Amazon Web Services](#aws-2-1)
- [Microsoft Azure](#azure-2-1)
- [Google Cloud Platform](#gcp-2-1)
To learn more, see [About Security Policies](/zpc/about-security-policies).
[]
Security Policy Title
Ensure that ADS - Vulnerability Assessment (VA) is enabled on a SQL server by setting a Storage Account
Ensure that 'HTTP Version' is the latest, if used to run the web app
Ensure Azure Active Directory RBAC is enabled for Azure Kubernetes Services (AKS)
Ensure the 'Allow access to Azure services' flag is disabled for SQL Server
Ensure that 'Data encryption' is set to 'On' for SQL Databases
Ensure that Network Security Group Flow Log retention period is 'greater than 90 days'
Ensure that data disks are encrypted for Linux Virtual Machines
Ensure that data disks are encrypted for Windows Virtual Machines
Ensure that operating system disks are encrypted for Linux Virtual Machines
Ensure that operating system disks are encrypted for Windows Virtual Machines
Ensure that periodic recurring scans is enabled for SQL server
Ensure that 'Send scan reports to' is set for SQL Server
Ensure storage for critical data are encrypted with Customer Managed Key
Ensure SQL server's TDE protector is encrypted with BYOK
Ensure that 'Also send email notification to admin and subscription owners' in Periodic recurring scan is enabled for SQL Server
Ensure web app is using the latest version of TLS encryption
Ensure that Azure Active Directory Admin is configured for SQL Server
Ensure soft delete is enabled for Azure Storage
Ensure that RDP access is restricted from the internet on NSG's
Ensure that SSH access is restricted from the internet on NSG's
Ensure that UDP Services are restricted from the Internet
Ensure that diagnostics is enabled on Virtual Machine
Ensure that 'Advanced Data Security' on a SQL server is set to 'On'
Ensure that Diagnostics is enabled for SQL Databases
Ensure that diagnostics log is enabled for Azure Data Lake Storage Gen2
Ensure that diagnostics settings should be enabled on Express route circuit
Ensure that diagnostics settings should be enabled on Front Door
Ensure that diagnostics settings should be enabled on Traffic Manager Profile
Internet facing virtual machine attached with a powerful managed identity and is running an image with critical vulnerabilities
Internet facing virtual machine attached with a managed identity is running an image with critical vulnerabilities
Internet facing virtual machine attached with a powerful managed identity is running a vulnerable image
Internet facing virtual machine attached with a managed identity is running a vulnerable image
Virtual machine Instance is running an image with critical vulnerabilities
[]
Security Policy Title
Internet facing virtual machine attached with a service account is running an image with critical vulnerabilities
Internet facing virtual machine attached with a powerful service account is running a vulnerable image
Internet facing virtual machine attached with a service account is running a vulnerable image
Internet facing virtual machine attached with a powerful service account and is running an image with critical vulnerabilities
[]
Security Policy Title
EC2 Instance is running an image with critical vulnerabilities
Internet facing EC2 instance with role is running vulnerable image
Internet facing EC2 instance with role is running a vulnerable image and enables IMDVs1
Internet facing EC2 instance with a powerful role is running a vulnerable image
Internet facing EC2 instance with a powerful role is running a vulnerable image and enables IMDVs1
Internet facing EC2 instance with a role is running an image with critical vulnerabilities and enables IMDVs1
Publicly-exposed EC2 instance running a vulnerable image has access to S3 bucket contains sensitive data
Internet facing EC2 instance has a powerful role and is running an image with critical vulnerabilities and enables IMDVs1

### Feature Available
#### Serverless Support
ZPC now supports GCP Functions as an identity in the IAM module when calculating an entitlement path.
To learn more, see [About Cloud Identity Details.](/zpc/about-cloud-identity-details#entitlements-tab)

### Feature Available
#### Threat Correlation Enhancements
You can now use vulnerability information when creating custom security policies or conducting an investigation. ZPC offers the following new predicates:
- CVE ID: The standard identifier number for a CVE as defined in the National Vulnerability Database (NVD).
- CVE Security: The security level of the vulnerability (i.e., Critical, High, Medium, Low, or Unknown).
- CVSS Score v3.0: The CVSS score associated with the vulnerability.
- Vulnerability Fix Available: The vulnerability fix availability based on the NVD database (i.e., True or False).
- CVE Age: The number of days since the CVE was first published.
- Package Name: The name of the vulnerable package.
- Package Version: The version of the vulnerable package.
- Image ID: The ID for the vulnerable image.
You can use the new predicates to create advanced custom security policies such as finding all EC2 instances which are publicly exposed, have severe vulnerabilities, and have access to sensitive resources. To learn more, see [Creating Custom Security Policies](/zpc/creating-custom-security-policies) and [Creating a New Investigation](/zpc/creating-new-investigation).

### Feature Available
#### Time Range Filter Enhancement
The Time Range filter is enhanced to include the following filter options:
- Last 12 hours: View the alerts that were generated or updated in the last 12 hours.
- Last day: View the alerts that were modified the previous day.
- Last week: View the alerts that were modified the previous week.
- Last month: View the alerts that were modified the previous month.
- Exact Date: View the alerts that are modified on the selected date.
- Custom Range: View the alerts that are modified on the selected date range along with time.
[See image.](#time-range)
To learn more, see [About Alerts](/zpc/about-alerts).
[![Time Range filter options](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/time-range.png)
]

## September 06, 2022
### Feature Available
#### Asset Table Enhancements
On the Asset Type Details page (Cloud Assets > Asset Type), you can view the total number of alerts generated and vulnerabilities present for a specific cloud asset.
[See image.](#asset-table)
To learn more, see [About Cloud Asset Type Details](/zpc/about-cloud-asset-type-details).
[![View the number of alerts and vulnerabilities](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/cloud-assets-alerts-vulnerabilities.png)
]

### Feature Available
#### Asset Timeline
You can view all the Cloud Service Provider (CSP) events and activities performed on a cloud asset and also identify the modifier and the timestamp for when the asset was last modified.
[See image.](#timeline-tab)
To learn more, see [About Cloud Asset Details](/zpc/about-cloud-asset-details).
[![View the Timeline tab](/sites/default/files/downloads/zpc/cloud-assets/about-cloud-asset-details/cloud-assets-timeline-tab.png)
]

### Feature Available
#### Azure Linux Workloads Support
Vulnerability scanning of Azure Linux workloads is supported with limited availability. You can enable the vulnerability scanning for specific instances within the cloud workload and schedule the scan to run at regular intervals.
[See image.](#azure)
To learn more, see [Configuring Vulnerability Scanning for Azure Linux Workloads](/zpc/configuring-vulnerability-scanning-azure-linux-workloads).
[![Vulnerability scanning of Azure Linux workloads](/sites/default/files/downloads/zpc/release-notes/zpc-rn-azurecldwrkld.png)
]

### Feature Available
#### Cloud Alerts Table Enhancement
You can view the list of alerts triggered for security policy violations that occur within your cloud resources in two tabs:
- All: Lists all the alerts.
- Policy: Lists alerts grouped by the policies.
[See image.](#all-policies-tab)
To learn more, see [About Alerts](/zpc/about-alerts).
[![View the Cloud Alerts page](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/cloud-alerts-tabs.png)
]

### Feature Available
#### Cloud Asset Alerts
You can view the alert details for all the alerts related to a cloud asset.
[See image.](#alert-details)
To learn more, see [About Cloud Asset Details](/zpc/about-cloud-asset-details).
[![View the Alert details](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/cloud-assets-alerts.gif)
]

### Feature Available
#### Cloud Asset Vulnerabilities
You can view and export the list of all vulnerabilities associated with a cloud asset.
[See image.](#vulnerabilities-tab)
To learn more, see [About Cloud Asset Details](/zpc/about-cloud-asset-details).
[![View the Vulnerabilties tab](/sites/default/files/downloads/zpc/cloud-assets/about-cloud-asset-details/cloud-assets-vulnerabilities-tab.png)
]

### Feature Available
#### Custom Policy Enhancements
You can now edit and delete custom policies:
- ZPC now allows you to edit all attributes and the custom policy logic. When you edit the query, existing alerts are closed and new alerts are generated based on the new custom policy query logic.
- You can also delete custom policies. When you delete a custom policy, all alerts generated by the policy are closed.
To learn more, see [Managing Custom Policies](/zpc/managing-custom-security-policies).

### Feature Available
#### Export Vulnerability Scan Data
You can export the vulnerability scan results to an Excel file and download the report.
[See image.](#export)
To learn more, see [About Vulnerability Management](/zpc/about-vulnerability-management).
[![Export vulnerability data](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/zpc-rn-export.png)
]

### Feature Available
#### IaC Scan of Push Events in Azure Repos
ZPC provides support for the IaC scanning of push events in Microsoft Azure Repos. ZPC triggers a scan on push events and detects misconfigurations and policy violations.
[See image.](#pushevents)
To learn more, see [Configuring IaC Scan for Microsoft Azure Repos](/zpc/configuring-iac-scan-microsoft-azure-repos).
[![Enable scan on push events](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/zpc-iac-azure-advanced-settings.png)
]

### Feature Available
#### Security Policies
Added the following security policies for cloud service providers:
- [Microsoft Azure](#azure-2-0)
- [Google Cloud Platform](#gcp-2-0)
- [Amazon Web Services](#aws-2-0)
[]
Security Policy Title
Ensure 'Enforce SSL connection' is set to 'ENABLED' for MySQL Database Server
Ensure FTP deployments are disabled for Web app
Ensure FTP deployments are disabled for Mobile app
Ensure that 'App Service Authentication' is enabled for Web apps
Ensure that 'App Service Authentication' is enabled for Mobile Apps
Ensure 'Trusted Microsoft Services' is enabled for Storage Account access
Ensure default network access rule for Storage Accounts is set to deny
Ensure that 'Secure transfer required' is 'Enabled' for Storage Account
Ensure that 'Auditing' Retention is 'greater than 90 days' for SQL Servers
Ensure that 'Auditing' is set to 'On' for SQL Server
Ensure server parameter 'log_retention_days' is greater than 3 days for PostgreSQL Database Server
Ensure server parameter 'log_disconnections' is set to 'ON' for PostgreSQL Database Server
Ensure server parameter 'connection_throttling' is set to 'ON' for PostgreSQL Database Server
Ensure that 'App Service Authentication' is enabled for Function Apps
Ensure that 'App Service Authentication' is enabled for API Apps
Ensure web app redirects all HTTP traffic to HTTPS in Azure App Service
[]
Security Policy Title
Ensure that privileged service accounts do not have external keys that never expire
Ensure virtual machine instances with powerful access permissions are not exposed to the internet
[]
Security Policy Title
Ensure IAM users can either use password-based console access or access key based API access

### Feature Available
#### Support for ARM Templates and Functions
The Azure Resource Manager (ARM) templates and specific functions are now fully supported for infrastructure-as-code (IaC), with partial support of CIS benchmark compliance coverage.
To learn more, see [About IaC Templates and Supported Functions](/zpc/about-iac-templates-and-supported-functions).

### Feature Available
#### Terraform Cloud Support
You can integrate the Zscaler IaC Scan app with Terraform Cloud and scan run tasks in Terraform workspaces.
[See image.](#terraform)
To learn more, see [Configuring IaC Scan for Terraform Cloud](/zpc/configuring-iac-scan-terraform-cloud).
[![Integrate Zscaler IaC Scan with Terraform Cloud](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/zpc-rn-tf.png)
]

### Feature Available
#### User Experience Improvements to Dashboards
You can view descriptions of the following widgets on the Cloud Threats and Cloud Identities Dashboards to improve usability:
- Security Event & Attack Vector Alerts
[See image.](#security-event)
- Security Exposure Alerts
[See image.](#security-exposure)
- Top Power Categories
[See image.](#power-categories)
To learn more, see [About the Cloud Threats Dashboard](/zpc/about-cloud-threats-dashboard) and [About the Cloud Identities Dashboard](/zpc/about-cloud-identities-dashboard).
[![View the widgets description](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/cloud-identities-dashboard.gif)
]
[![View the widgets description](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/cloud-threats-security-event.gif)
]
[![View the widgets description](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/cloud-threats-security-exposure.gif?1661510373)
]
