# Release Upgrade Summary (2025)
Source: https://help.zscaler.com/dspm/release-upgrade-summary-2025

This article provides a summary of all new features and enhancements for DSPM. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com/).

**Clouds:** app.zsdpc.net, app.eu.zsdpc.net
The following service updates were deployed to app.zsdpc.net on

## November 10, 2025
### Feature Available
#### Additional Details of AI Resources
You can now view additional details of AI resources listed on the AI Inventory page. You can click the Resource Name to view the resource and metadata details.
[See image.](#ds-services-tile)
[]
![Resource details of the selected AI resource](/sites/default/files/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-57695-configuring-teams-outegration/ds-resource-details-ai.png)
To learn more, see [Viewing the AI Inventory Details](/dspm/viewing-ai-inventory-details).

### Feature Available
#### Data Posture Policies
The following new data posture policies are available:
- [AWS](#ds-aws-policy-115)
- [Azure](#ds-azure-policy-115)
- [GCP](#ds-gcp-policy-115)
- [On-Premises](#ds-onprem-policy-115)
- [Snowflake](#ds-snowflake-policy-115)
- [Databricks](#ds-dbricks-policy-115)
[]
| Policy Title |
| ------------ |
| AWS Bedrock Custom Model is associated with an S3 bucket that can be accessed by external or public IAM entities with high privileges |
| EC2 instance has AI packages with vulnerabilities and can access RDS instances containing sensitive data |
| EC2 instance has AI packages with vulnerabilities and can access RDS clusters containing sensitive data |
| EC2 instance has AI packages with vulnerabilities and can access DynamoDB tables containing sensitive data |
[]
| Policy Title |
| ------------ |
| Azure virtual machine has AI packages with vulnerabilities and can access Flexible PostgreSQL servers containing sensitive data |
| Azure virtual machine has AI packages with vulnerabilities and can access SQL servers containing sensitive data |
[]
| Policy Title |
| ------------ |
| GCP Compute VM instance containing Model Context Protocol packages is publicly exposed |
| GCP Compute VM instance has AI packages with vulnerabilities and can access storage buckets containing sensitive data |
| GCP Compute VM instance containing Agentic AI packages is publicly exposed |
| GCP Compute VM instance hosting unmanaged AI models with low downloads |
[]
| Policy Title |
| ------------ |
| Snowflake database containing sensitive table data is publicly exposed |
| Snowflake database containing sensitive table data has account level public exposure |
| Snowflake database containing sensitive table data can be accessed by dormant users |
| Snowflake database containing sensitive table data can be accessed by console users without MFA |
| Snowflake database containing sensitive table data can be accessed by PAT with risky access to a public table that does not have retention applied |
| Snowflake database containing sensitive table data can be accessed by dormant users without MFA and is publicly exposed |
| Snowflake database containing sensitive table data can be accessed by console users without MFA and retention is not applied on tables |
| Snowflake database containing sensitive table data can be accessed by dormant users without MFA and is publicly exposed with retention not applied |
| Snowflake database containing sensitive table data is at risk of ransomware attacks |
| Snowflake database containing sensitive table data can be accessed by legacy users with risky access |
[]
| Policy Title |
| ------------ |
| On-premises Oracle pluggable database has tables containing sensitive data and does not have logging enabled |
| On-premises Oracle database instance has tables containing sensitive data and is not encrypted with TDE |
| On-premises Oracle pluggable database has tables containing sensitive data and is not encrypted with TDE |
| On-premises Oracle database instance has tables containing sensitive data and does not have logging enabled |
[]
| Policy Title |
| ------------ |
| Azure Databricks schema has tables containing sensitive data and the workspace is not encrypted with a customer-managed key |
| Azure Databricks schema has tables containing sensitive data and the workspace configuration has legacy access enabled |
| Azure Databricks schema has tables containing sensitive data and workspace configuration allows users to download SQL results from the Databricks SQL editor |
| Azure Databricks schema has tables containing sensitive data and logging is not enabled |
| Azure Databricks schema has tables containing sensitive data and data retention is not applied |

### Feature Available
#### Data Scan Enhancements
The data scan feature includes the following enhancements:
Support for Scanning Azure File Shares
DSPM supports Azure File Shares scanning over SMB and NFS to discover and classify sensitive data.
[See image.](#img-ds-rn-azure-fileshare)
To learn more, see [Configuring Scan Rule for Azure File Shares](/dspm/configuring-scan-rule-azure-file-shares).
Data Collection and Posture for AWS Databricks
DSPM supports the discovery and classification of sensitive data in AWS Databricks workspaces and accounts.
[See image.](#img-ds-rn-aws-databricks)
To learn more, see [About Service Registration](/dspm/about-service-registration), [Adding a Databricks Workspace or Account](/dspm/adding-databricks-workspace), [Supported Data Stores and File Types](/dspm/supported-data-stores-and-file-types), and [Configuring the Scan Rule for AWS Databricks](/dspm/configuring-scan-rule-aws-databricks-workspace).
[]![Select Cloud and Resource Type page with Azure Cloud Type, Cloud Storage Resource Category, and File Shares Resource Type selected. ](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-rn-azure-fileshare.png)
[]![Select Cloud and Resource Type page with AWS Cloud Type, Database Resource Category, and Databricks Resource Type selected. ](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-rn-aws-databricks.png)

### Feature Available
#### Enhancement to AWS IAM Condition Operators
DSPM supports the following AWS IAM condition operators for managing principal-based (identity-based) and resource-based access to scan data:
- `NotPrincipal`
- `ArnNotLike`
- `IfExists`
To learn more, see [Supported AWS IAM Condition Keys and Operators](/dspm/supported-aws-iam-condition-keys-and-operators).

### Feature Available
#### Enhancements to On-Premises Scanning
On-premises data scanning includes the following enhancements:
Hyper-V Support for On-Premises Scanner
DSPM on-premises scanner now supports a Hyper-V deployment mode. Download the Hyper‑V scanner image and run it over a Hyper‑V service in the data center to register the scanner.
[See image.](#ds-rn-onprem-scanner-hyperv)
To learn more, see [About On-Premises Scanner Integrations](/dspm/about-premises-scanner-integrations).
[]![Scanner integration details showing Hyper-V and VMware platform support.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-rn-onprem-scan-hyperv.png)
NFS Protocol Support for On‑Premises File Servers
DSPM supports the NFS protocol for adding on-premises file servers, in addition to SMB, allowing the scanner to access and analyze files on Linux and Windows systems to discover and classify sensitive data.
[See image.](#img-ds-rn-on-prem-file-server-nfs)
To learn more, see [Adding an On-Premises File Server](/dspm/adding-premises-file-servers).
[]![Add On-Premises File Servers drawer with NFS details.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-rn-on-prem-file-server.png)

### Feature Available
#### Posture Label Enhancements
The following enhancements are available for posture labels:
Renamed Over-Privileged Access Posture Label
The posture label Over-Privileged Access is renamed to Privileged Access. The Privileged Access posture label is assigned when an entity has full or edit access permissions on one or more data stores containing sensitive data.
Posture Labels for Resource Types
The following posture labels are supported for these resource types:
- AWS Databricks
- Data Retention
- Logging
- Encryption
- Public Exposure
- Azure OpenAI and Azure AI Foundry
- Encryption
- Logging
- Guardrails
- Public Exposure
To learn more, see [Understanding the Security Posture State](/dspm/understanding-security-posture-state).

### Feature Available
#### Resource Inventory Enhancements
The Resource Inventory feature includes the following enhancements:
Azure AI Foundry Renamed to Azure AI Foundry Hub
Azure AI Foundry is renamed to Azure AI Foundry Hub. The following associated resources are also renamed:
- Azure AI Foundry Hub Connection
- Azure AI Foundry Hub Datastore
- Azure AI Foundry Hub Deployments
- Azure AI Foundry Hub Projects
- Azure AI Foundry Hub RAI Policies
To learn more, see [Viewing the AI Inventory Details](/dspm/viewing-ai-inventory-details).
Supported Data Stores
The following data stores are scanned for sensitive data:
- AWS Databricks
- Azure OpenAI
- Azure AI Foundry (formerly Azure AI Services)
To learn more, see [Supported Data Stores and File Types](/dspm/supported-data-stores-and-file-types).

## September 25, 2025
### Feature Available
#### AI Inventory
The AI Inventory is dedicated to the inventory, management, and analysis of Artificial Intelligence (AI) and Machine Learning (ML) resources within a cloud environment.
[See image.](#ds-ai-inventory)
To learn more, see [Viewing the AI Inventory Details.](/dspm/viewing-ai-inventory-details)
[]
![Artificial Intelligence (AI) Inventory provides a tabular view of AI models, AI services, and AI tools and packages](/sites/default/files/downloads/tech-pubs-drafts/dspm-draft-articles/1-14-0-viewing-identity-inventory-details/ds-ai-inventory-rn.png)

### Feature Available
#### AI Security Dashboard: Summary Tiles
The summary tiles at the top of the dashboard provide additional details:
- Data Shared with AI: The number of files and data stores shared with the AI.
- AI Tools & Packages Vulnerabilities: AI tools and packages that have vulnerabilities.
- Open Alerts on AI Resources: The number of open alerts triggered for AI resources, and these alerts are represented by severity.
[See image.](#ds-ai-metrics)
To learn more, see [Viewing the Statistics for AI Service Details.](/dspm/viewing-the-statistics-for-ai-service-details)
[]
![Shows the summary tiles on AI Security tab](/sites/default/files/downloads/tech-pubs-drafts/dspm-draft-articles/1-14-0-about-resource-inventory/ds-ai-metrics.png)

### Feature Available
#### Data Posture Policies
The following new data posture policies are available:
- [AWS](#ds-awspolicy-140)
- [Azure](#ds-azurepolicy-140)
- [On-Premises](#ds-onprempolicy-140)
- [Snowflake](#ds-snowflakepolicy-140)
[]
| Policy Title |
| ------------ |
| Unmanaged AWS MySQL server has databases containing sensitive data that are not encrypted with transparent data encryption |
| Unmanaged AWS MySQL server has databases containing sensitive data and allows insecure TLS versions |
| Unmanaged AWS MySQL server has databases with tables containing sensitive data and has SSL enforcement disabled |
| Unmanaged AWS Oracle database instance has tables containing sensitive data that are not encrypted with transparent data encryption |
| Unmanaged AWS Oracle database instance has tables containing sensitive data and does not have logging enabled |
| Unmanaged AWS Oracle database instance has tables containing sensitive data and does not have RMAN backup |
| Unmanaged AWS Oracle pluggable database has tables containing sensitive data and is not encrypted with transparent data encryption |
| Unmanaged AWS Oracle pluggable database has tables containing sensitive data and does not have logging enabled |
| Unmanaged AWS Oracle pluggable database has tables containing sensitive data and does not have RMAN backup |
| AWS Custom Model has sensitive training data |
| AWS Bedrock Custom Model containing sensitive data can be invoked by external entities |
| AWS Bedrock Custom Model containing sensitive training data is not CMK encrypted |
| AWS Bedrock Custom Model containing sensitive data can be accessed by IAM users without MFA |
| AWS Bedrock Custom Model containing sensitive data does not have model invocation logging enabled |
| AWS Bedrock Custom Model containing sensitive data can be accessed by newly created IAM users |
| AWS Bedrock Imported Model is associated with an S3 bucket that can be accessed by external or public IAM entities with high privileges |
| AWS Bedrock Imported Model is importing models from an S3 bucket containing malware |
| AWS Bedrock Imported Model has model invocation logging disabled |
[]
| Policy Title |
| ------------ |
| Azure virtual machine hosting unmanaged AI models with low downloads |
| Azure virtual machine has AI packages with vulnerabilities and can access storage accounts containing sensitive data |
| Azure virtual machine containing Model Context Protocol packages is publicly exposed |
| Azure virtual machine containing Agentic AI packages is publicly exposed |
| Azure PostgreSQL Flexible server has databases containing sensitive data and is associated with Azure Key Vault without RBAC authorization |
| Azure AI Foundry Hub is associated with a storage account containing sensitive blob data that is publicly exposed and has shared key access enabled |
| Azure AI Foundry Hub is associated with a storage account containing sensitive blob data and with a Key Vault that has RBAC enabled and can be accessed by external users |
| Azure AI Foundry Hub is associated with a storage account containing sensitive blob data and with a Key Vault without RBAC authorization |
| Unmanaged Azure MySQL server has databases containing sensitive data and allows insecure TLS versions |
| Unmanaged Azure Oracle pluggable database has tables containing sensitive data and does not have logging enabled |
| Unmanaged Azure Oracle pluggable database has tables containing sensitive data and does not have RMAN backup |
[]
| Policy Title |
| ------------ |
| On-premises MySQL server has databases with tables containing sensitive data and has SSL enforcement disabled |
| On-premises MySQL server has databases containing sensitive data that are not encrypted with transparent data encryption |
| On-premises MySQL server has databases containing sensitive data and allows insecure TLS versions |
[]
| Policy Title |
| ------------ |
| Snowflake database containing PCI or HIPAA data in tables is not CMK encrypted |

### Feature Available
#### DSPM Integration with ZIdentity
DSPM is migrated to ZIdentity, a unified identity service for Zscaler that centralizes identity management, user authentication and authorization. You can access the DSPM Admin Portal via the [ZIdentity Landing Page](/zidentity/accessing-and-navigating-zidentity-landing-page).
You need to add and assign users, user groups, and roles in the ZIdentity Admin Portal.
[See image.](#zidentitylandingpage)
To learn more, see [Accessing and Navigating the DSPM Admin Portal](/dspm/accessing-and-navigating-dspm-admin-portal), [About Users](/zidentity/about-users), and [About Access Roles](/dspm/about-roles).
[]![The ZIdentity landing page with the list of entitlements.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/dspm-rn-zidentity-dspm-tile.png)

### Feature Available
#### Enhancements to Data Scanning
The following enhancements are available for data scanning:
Automatic Exclusion Data Stores Used for Storing Logs
DSPM automatically excludes data stores used for storing logs of cloud-native services such as Network Flow, RDS Audit, ALB, or NLB transactions from scanning. This optimization applies to AWS, Azure, and GCP resources and improves the scan efficiency by excluding non-sensitive log data.
To learn more, see [Selecting the Orchestrator and Monitoring Scope](/dspm/selecting-orchestrator-and-monitoring-scope), [Onboarding a GCP Organization](/dspm/onboarding-gcp-organization), and [Onboarding an AWS Organization](/dspm/onboarding-aws-organization).
Scan Rules
DSPM introduces scan rules for greater flexibility and granularity in configuring the data scan schedule for data stores.
[See image.](#ds-scan-rule)
To learn more, see [About Scan Settings](/dspm/about-scan-settings).
[]![Overview of scan rules for the onboarded platforms displaying status, type, and other scan rule configuration details.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-rn-scan-rule.png)

### Feature Available
#### Notification Emails
You can now send emails to specific recipients about any configuration or permission issues encountered with the onboarded organization or tenant. You can add multiple email addresses of recipients who need to receive the notifications during or after the onboarding process.
[See image.](#orgdetails-notificationemails)
To learn more, see:
- [Onboarding an AWS Organization](/dspm/onboarding-aws-organization)
- [Onboarding an AWS Account](/dspm/onboarding-single-aws-account)
- [Onboarding a Microsoft Entra Tenant](/dspm/onboarding-microsoft-azure-tenant)
- [Onboarding a GCP Organization](/dspm/onboarding-gcp-organization)
[]![The Organization Details section with the list of AWS organization details blurred.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/dspm-rn-email-notification.png)

### Feature Available
#### Resource Inventory Enhancements
The Resource Inventory includes the following enhancements:
Resource Names for AWS EC2 Virtual Machines
You can see the resource names of AWS EC2 virtual machines instead of their instance ID on the Resource Inventory page.
Posture Label Support
The following posture labels are supported:
- Azure File Share
- Encryption
- Data Retention
- Backup
- Logging
- Azure Storage Account Table
- Logging
- Encryption
- Snowflake
- Public Exposure
- Azure Databricks
- Encryption
- Data Retention
- Public Exposure
- Logging
To learn more, see [Understanding the Security Posture State.](/dspm/understanding-security-posture-state)
Support for Scanning On-Premises File Servers with On-Premises Scanner
DSPM deploys the on-premises scanner on on-premises file servers to scan file shares to discover and classify sensitive data.
[See image.](#on-prem-file-server)
To learn more, see [About On-Premises Scanner Integrations](/dspm/about-premises-scanner-integrations), [About Service Registration](/dspm/about-service-registration), [Adding an On-Premises File Server](/dspm/adding-premises-file-servers), and [Configuring Scan Rule for On-Premises File Servers](/dspm/configuring-scan-rule-premises-file-servers).
Data Collection and Posture for Azure Databricks
DSPM supports the discovery and classification of sensitive data in Azure Databricks workspaces.
[See image.](#dtabricks)
To learn more, see [About Service Registration](/dspm/about-service-registration), [Adding a Databricks Workspace](/dspm/adding-databricks-workspace), and [Configuring Scan Rule for Azure Databricks Workspace](/dspm/configuring-scan-rule-azure-databricks-workspace).
[]![The Service Registration page with On-Premises File Server tab selected displays the with details for file servers.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-rn-on-prem-file-servers.png)
[]![The Service Registration page with Databricks tab selected displays the with details for databricks.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-rn-on-databricks.png)

### Feature Available
#### Saved Views
You can apply filters, modify table columns, and other settings on a page and save this customized view, so whenever you access the page later, it is displayed with the same settings. Saved view is available on the Resource Inventory, AI Inventory, and Compliance pages.
[See image.](#ds-saved-view)
To learn more, see [About Resource Inventory.](/dspm/about-resource-inventory)
[]
![Shows the details on creating a saved view](/sites/default/files/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/iam-roles-and-permissions-aws/ds-saved-view-img.png)

### Feature Available
#### Snowflake Predicates in Investigation & Policy Query
The investigation and policy queries include the following posture predicates that can be used to query Snowflake resources:
-
Is Dormant
-
Stale Access Keys
[See image.](#ds-posturepredicates)
[]
![Shows the predicates for Snowflake](/sites/default/files/downloads/ds-dormant.png)
To learn more, see [Creating a New Investigation](/dspm/creating-new-investigation) and [Creating Custom Policies](/dspm/creating-custom-policies).

### Feature Available
#### Unmanaged Identities in Identity Inventory
Identities from unmanaged and Snowflake databases are shown in the Identity Inventory, providing visibility into the resources and data types that the identities can access.
[See image.](#ds-image)
To learn more, see[ Viewing the Identity Inventory Details.](/dspm/viewing-identity-inventory-details)
[]
![View the Identity Inventory page](/sites/default/files/downloads/ds-identity.png)

## August 18, 2025
### Feature Available
#### Custom Tag Validation
While onboarding accounts, you can define and assign custom tags to resources created by DSPM. These tags are included in the templates generated by DSPM. Tag validation is now aligned with the specific guidelines of each CSP to ensure accuracy and avoid incorrect tag syntax in the templates.
[See image.](#managecustomtags)
To learn more, see [Managing Custom Tags](/dspm/managing-custom-tags).
[]![The AWS manage custom tags page displaying the list of key value pair added and the guidelines to follow while adding.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/dspm-aws-custom-tags.png)
![The Azure manage custom tags page displaying the list of key value pair added and the guidelines to follow while adding.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/dspm-azure-custom-tags.png)

### Feature Available
#### Dashboard Enhancements
The Dashboard includes the following enhancements:
AI Security Dashboard
The AI Security dashboard includes the following changes:
- The summary tiles at the top of the dashboard showing details about deployed AI, data stores shared with AI, and open alerts on AI resources are now clickable. Click each tile to access the relevant list of resources, files, or alerts.
- You can view the resource type by hovering over the resource icon on the AI Services tab.
[See image.](#ds-AIsecurityinsights)
[]
![Shows the insights on the AI Security dashboard](/sites/default/files/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-query-builder-policies-and-investigation/ds-tiles.png)
Detection of Unmanaged AI Services and Models
DSPM now scans and discovers unmanaged AI services and models installed on virtual machines. DSPM identifies these services by DSPM policies for specific risk alerts.
[See image.](#ds-unmanagedmodels)
[]
![Shows the unmanaged AI models](/sites/default/files/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-query-builder-policies-and-investigation/ds-unmanaged-ai.png)
Stale Data Detection
DSPM discovers stale data that has not been accessed or modified for more than 90 days. This allows security teams to identify and remove sensitive stale data that poses a risk.
The Data Discovery dashboard displays the following insights:
- Files Accessed 90 Days Ago (supported for AWS S3 buckets)
- Files Modified 90 Days Ago (supported across AWS, Azure, and GCP resources)
You can click the number on the tile to view the details on the Resource Inventory page. Stale data can also be identified under the Last Accessed Time column on the Data Inventory page.
[See image.](#ds-insights)
To learn more, see [Viewing the Statistics for Scanned Data](/dspm/viewing-statistics-scanned-data) and [Viewing the Data Inventory](/dspm/viewing-data-inventory).
Support for AWS Bedrock Custom Models
DSPM now provides visibility into AWS Bedrock Custom Models and AWS Bedrock Imported Models. This enhancement allows to correlate data and AI risks associated with both customized and imported models, providing a more complete security posture.
[See image.](#ds-awsmodels)
To learn more, see [Viewing the AI Service Details](/dspm/viewing-ai-service-details).
[]
![Shows the AWS Bedrock resource types](/sites/default/files/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-query-builder-policies-and-investigation/ds-resourcetypes.png)
[]
![Shows the insights of scanned data](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-release-notes/ds-data_insights.png)

### Feature Available
#### Data Posture Policies
The following new data posture policies are available:
- [AWS](#ds-awspolicy-130)
- [Azure](#ds-azurepolicy-130)
- [GCP](#ds-gcppolicy-130)
- [Snowflake](#ds-snowflakepolicy-130)
- [On-Premises](#ds-onprempolicy-130)
[]
| Policy Title |
| ------------ |
| AWS Bedrock Knowledge Base is associated with a publicly accessible S3 bucket containing sensitive data |
| AWS Bedrock Knowledge Base is associated with a sensitive S3 bucket that can be publicly accessed and modified |
| EC2 instance hosting unmanaged AI models with low downloads |
| EC2 instance has AI packages with vulnerabilities and can access S3 buckets containing sensitive data |
| EC2 instance containing Model Context Protocol packages is publicly exposed |
| EC2 instance containing Agentic AI packages is publicly exposed |
| Unmanaged AWS MySQL server has databases containing sensitive data and allows insecure admin TLS versions |
[]
| Policy Title |
| ------------ |
| Azure AI Foundry Hub is associated with the hub workspace's storage account containing sensitive blob data that can be accessed by external users |
| Publicly accessible Azure AI Foundry Hub has projects with connected storage account containers containing sensitive blob data |
| Unmanaged Azure Oracle pluggable database has tables containing sensitive data that are not TDE encrypted |
| Unmanaged Azure Oracle database instance has tables containing sensitive data and does not have logging enabled |
| Unmanaged Azure Oracle database instance has tables containing sensitive data that are not TDE encrypted |
| Unmanaged Azure MySQL server has databases containing sensitive data in tables and has SSL enforcement disabled |
| Unmanaged Azure MySQL server has databases containing sensitive data and allows insecure admin TLS versions |
| Unmanaged Azure MySQL server has databases containing sensitive data that are not encrypted with transparent data encryption |
[]
| Policy Title |
| ------------ |
| GCP Compute Engine VM instance and disk containing sensitive data does not have appropriate retention period configured |
| GCP Compute VM instance containing sensitive data has automatic restart feature disabled |
| GCP Compute VM instance containing sensitive data has a default service account attached to it |
| GCP Compute VM instance containing sensitive data has auto-delete for persistent disk enabled |
[]
| Policy Title |
| ------------ |
| Snowflake database containing sensitive table data does not have masking policy configured |
| Snowflake database containing sensitive table data does not have data retention configured correctly |
[]
| Policy Title |
| ------------ |
| On-premises PostgreSQL server has databases containing sensitive data and allows insecure TLS versions |
| On-premises Microsoft SQL server has databases containing sensitive data that are not encrypted with transparent data encryption (TDE) |
| On-premises MySQL server has databases containing sensitive data and allows insecure admin TLS versions |

### Feature Available
#### Identity Inventory
DSPM scans your data stores to identify identities with excessive privileges and provides a comprehensive view of the identities within the cloud environment. The Identity Inventory shows details about an identity, such as entity type, the sensitive data stores accessed by the entity, the entity's security posture, and so on. Maintaining a comprehensive inventory of identities and their associated access levels helps evaluate the identity posture and mitigate identity-based threats.
[See image.](#ds-identity-inventory)
To learn more, see [About Identity Inventory](/dspm/about-identity-inventory).
[]
![Shows the list of all identities in the cloud environement.](/sites/default/files/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-query-builder-policies-and-investigation/ds-identitynventory.png)

### Feature Available
#### Resource Inventory Enhancements
The Resource Inventory includes the following enhancements:
Snowflake Entitlements
DSPM now provides identity permissions and access details for a Snowflake database. View and analyze database access and permission grants to ensure that only authorized users and applications have access to the database resources. This information is available in reports and graphs. You can also use investigation queries to determine database access.
To learn more, see [Viewing the Access Levels](/dspm/viewing-access-levels).
Evidence UI Enhancements
The Evidence tab includes the following enhancements:
- For file-based evidence, you can now see additional context (prefix and suffix of a specific trigger) to the matched content.
-
DLP engines relevant to the DLP dictionaries are displayed.
-
The link to the original file is under the Actions menu.
[See image.](#ds-evidencedetails)
To learn more, see [Viewing the Sensitive Data Details.](/dspm/viewing-sensitive-data-details)
[]
![Shows the trigger matches on the Evidence tab](/sites/default/files/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-query-builder-policies-and-investigation/DS-evidence_0.png)
Monitor Identities Having Access to Sensitive Files
The File Access tab shows identity details, the actions performed by identities, and the source IP address used to access the files containing sensitive data in the last 7 days. This is supported for file access events in AWS (S3 buckets). The file access is shown only for files that have a DLP Engine or Gen AI classification match.
To learn more, see [Viewing the Sensitive Data Details.](/dspm/viewing-sensitive-data-details)

### Feature Available
#### Use Wildcards to Exclude Data Stores from Scanning
AWS, Azure, and GCP data stores can now be excluded from scanning by using wildcards to match the data store names. This provides an easier and broader exclusion criteria. Based on the wildcards chosen, all the matching AWS S3 buckets, Azure storage accounts, or Google cloud storage buckets are excluded from scanning. Both the existing and any future data store names that match the wildcards are excluded.
To learn more, see [Configuring Scan Settings for AWS Cloud Storage](/dspm/configuring-scan-settings-aws-cloud-storage), [Configuring Scan Settings for Azure Cloud Storage](/dspm/configuring-scan-settings-azure-cloud-storage), and [Configuring Scan Settings for Google Cloud Storage](/dspm/configuring-scan-settings-google-cloud-storage).

## July 10, 2025
### Feature Available
#### Azure AI Foundry Enhancements
The following enhancements are made to Azure AI Foundry:
Investigation Predicates
You can use the Has Model predicate to query the correlation of AI model information and sensitive data for Azure AI Foundry along with the following additional predicates:
- Model Name
- Model Format
- Model Version
To learn more, see [Creating an Investigation](/dspm/creating-new-investigation).
Security Posture Label for Guardrails
The security posture label is added for Guardrails in Azure AI Foundry deployments.
To learn more, see [Understanding the Security Posture.](/dspm/understanding-security-posture-state)

### Feature Available
#### Compliance Framework Enhancements
The Compliance dashboard is enhanced with the following features:
- The following new compliance frameworks are supported:
- Australian Signals Directorate Essential Eight
- Transportation Security Administration Security Directive Pipeline 2021-02
- Healthcare and Public Health Sector's Cybersecurity Performance Goals
- Digital Operational Resilience Act
- You can now configure custom compliance frameworks by cloning the existing ones or creating new ones from scratch.
- You can enable or disable frameworks. You can also hide the disabled frameworks on the dashboard.
[See image.](#compliance-dashboard)
To learn more, see:
- [About Compliance](/dspm/about-compliance)
- [Supported Frameworks](/dspm/supported-frameworks)
- [Adding a Custom Compliance Framework](/dspm/adding-custom-compliance-framework)
- [Managing Compliance Frameworks](/dspm/managing-compliance-frameworks)
[]![The Compliance dashboard displaying the list of supported frameworks.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/dspm-compliance-dashboard.jpg)

### Feature Available
#### Data Classification Evidence in Azure
DSPM generates evidence data for scanned files and tables which allows data security analysts to access the triggers related to the data classification and perform in-context investigation and validation of sensitive data. The evidence data is securely stored in a storage account that resides in one of the onboarded accounts and access to this data is protected by a specific role and permission.
To learn more, see [Managing Evidence Configuration](/dspm/managing-evidence-configuration) and [Predefined Roles and Permissions](/dspm/predefined-roles-and-permissions).

### Feature Available
#### Data Inventory
The new Data Inventory page provides a comprehensive overview of all the sensitive files and tables that exist across your clouds, accounts, and data stores. Identifying and listing all instances of files and tables with certain data is required for auditing and compliance tasks. For example, you can list all the files with PCI data that have not been modified for over 9 months.
[See image.](#ds-datainventorydashboard)
To learn more, see [Viewing the Data Inventory](/dspm/viewing-data-inventory-page).
[]
![Shows the list of files and tables containing sensitive data.](/sites/default/files/downloads/ds-rn-datainventory.png)

### Feature Available
#### Data Posture Policies
The following new data posture policies are available:
- [AWS](#ds-awspolicy-112)
- [Azure](#ds-azurepolicy112)
- [GCP](#ds-gcppolicy112)
- [On-Premises](#ds-onprempolicy112)
[]
| Policy Title |
| ------------ |
| RDS DB cluster containing sensitive data can be accessed by a misconfigured GitLab OIDC IAM role |
| RDS DB instance containing sensitive data can be accessed by a misconfigured GitLab OIDC IAM role |
| EC2 instances containing sensitive data can be accessed by a misconfigured GitLab OIDC IAM role |
| S3 bucket containing sensitive data can be accessed by a misconfigured GitLab OIDC IAM role |
[]
| Policy Title |
| ------------ |
| Azure AI Foundry Hub is associated with the hub workspace's storage account containing sensitive blob data and is associated with an Azure Key Vault that has public network access enabled |
| Azure AI Foundry Hub is associated with the hub workspace's storage account containing sensitive blob data and does not use user-assigned managed identity |
| Azure AI Foundry Hub is associated with the hub workspace's storage account containing sensitive blob data and with Azure Key Vault that has soft delete retention of less than 90 days |
| Azure AI Foundry Hub is associated with the hub workspace's storage account containing sensitive blob data and has AI deployments with poorly configured content filter with protected and prompt shield categories |
| Azure AI Foundry Hub is associated with the hub workspace's storage account containing sensitive blob data and is associated with Azure Key Vault that has purge protection disabled |
| Azure AI Foundry Hub has access to storage account containing sensitive blob data and does not use user-assigned managed identity |
| Azure AI Foundry Hub has access to a storage account containing sensitive blob data and has AI deployments with poorly configured content filter with protected and prompt shield categories |
| Azure PostgreSQL Flexible server has databases containing sensitive data and is associated with Azure Key Vault that has purge protection disabled |
[]
| Policy Title |
| ------------ |
| GCP Compute VM instance containing sensitive data has deletion protection disabled |
| GCP Compute VM instance containing sensitive data has block project-wide SSH keys disabled |
| GCP Compute VM instance containing sensitive data has a default service account with full API access attached to it |
| GCP Compute VM instance containing sensitive data has auto-delete for OS disk enabled |
| GCP Compute VM instance containing sensitive data has only disk backup enabled |
| GCP Compute VM instance containing sensitive data has backup disabled |
| GCP Compute VM instance containing sensitive data does not have Ops Agent installed |
| GCP Compute VM instance containing sensitive data is not encrypted with customer-managed key |
| GCP Compute VM instance containing sensitive data has Shielded VM disabled |
| GCP Compute VM instance containing sensitive data has Confidential Computing service disabled |
| GCP Cloud MySQL instance has databases containing sensitive data and is publicly exposed and susceptible to ransomware attack |
| GCP Cloud MS SQL instance has databases containing sensitive data and is publicly exposed and susceptible to ransomware attack |
| GCP Cloud PostgreSQL instance has databases containing sensitive data and is publicly exposed and susceptible to ransomware attack |
| GCP Cloud SQL instance has databases containing sensitive data and can be accessed with a long-lived service account key |
| GCP Cloud SQL instance has databases containing sensitive data and can be accessed by users with risky permissions |
| GCP Cloud MS SQL instance has databases containing sensitive data and has remote access flag enabled |
[]
| Policy Title |
| ------------ |
| On-premises PostgreSQL server has databases containing sensitive data and does not have appropriate logging configured |
| On-premises PostgreSQL server has databases containing sensitive data and has SSL disabled |
| On-premises Microsoft SQL server does not have audit logging with audit specifications configured |
| On-premises Microsoft SQL server has databases containing sensitive data and does not have any backups |

### Feature Available
#### Data Scanning Enhancements
The following enhancements are made to data scanning:
On-Demand Scanning
You can now use the On-Demand scan option to run the scans manually. This is supported for all resource types including virtual machines, databases, NoSQL databases and unmanaged databases. Use this option only when ad hoc scans are required.
[See image.](#img-on-demand)
Data Scanning Inclusions and Exclusions
In addition to multiple existing scan settings options to include and exclude data stores in data scanning, the following options are available:
-
Specific virtual machines and databases can be included in the scan settings.
[See image.](#img-ds-rn-select-resource-label)
-
Cloud resource tags can be used as the exclusion factor, allowing to exclude resources with certain tags from scanning.
[See image.](#img-exclude-resources)
Scan Setting UI Enhancements
You can select specific resources while configuring the scan settings.
[See image.](#img-rn-new-ui-selection)
Scan Start Time Configuration for Unmanaged Databases
You can configure a specific time window for scanning unmanaged databases so that the scans run when databases are least used, reducing any performance impact during active periods.
[See image.](#img-scan-start-time)
Stop In-Progress Scans
Scheduled or on-demand scans that are currently in progress can be stopped for the following resources:
- Virtual machines
- Managed and unmanaged databases
- NoSQL data stores
[See image.](#img-stop-in-progress-scans)
To learn more, see [Starting or Stopping a Scan](/dspm/starting-stopping-scan), and [About Scan Settings](/dspm/about-scan-settings).
[]![Scan Settings page displaying the Stop Scan option, to stop an in-progress scan.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/img-stop-in-progress-scans.png)
[]![Scan Schedule page allowing to set scan frequency, including specific days and times to trigger scans.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-rn-scan-start-time.png)
[]![Select Resources to Scan page with annotation around the new UI for the resource selection.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-rn-new-ui-resource-selection.png)
[]![Select Resources to Scan page with an annotation around Select by Labels option.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-rn-select-resource-label.png)
[]![Optionally exclude resources page with an annotation around the exclude scanning by label using key-value pairs.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-rn-scan-exclude.png)
[]![Scan Schedule page displaying Daily, Weekly, Monthly, or On Demand scan optionswith an annotation around the On Demand scan option.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-rn-scan-on-demand.png)

### Feature Available
#### Database Enhancements
The following are the database enhancements:
Snowflake Database Support
Zscaler DSPM now supports Snowflake and scans databases within the onboarded Snowflake accounts for sensitive data and provides security assessments.
[See image.](#img-snowflake)
To learn more, see [About Snowflake](/dspm/about-snowflake), [Adding Snowflake Database Account](/dspm/adding-snowflake-database-account), and [Configuring Scan Settings for Snowflake Databases](/dspm/configuring-scan-settings-snowflake-databases).
HashiCorp Vault for Secret Storage
HashiCorp's self-hosted secret store HashiCorp Vault is now supported for hosting keys used for database scanning.
Tokens and secrets used for database access are typically stored in CSP-based secret stores, such as Amazon secret manager or Azure Key Vault. DSPM uses these storages to gain secure access to scan unmanaged databases running in CSPs or on-premises.
[See image.](#img-hashicorp)
To learn more, see [Adding Unmanaged Databases](/dspm/adding-unmanaged-database).
[]![Add Unmanaged Database window with HashiCorp Vault Selected as Secret Provider](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-rn-hashicorp.png)
[]![Cloud and Resource Type page with an annotation around the Snowflake as cloud type and Database as resource type.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-rn-snowflake.png)

### Feature Available
#### Resource Inventory Enhancements
The resource inventory includes the following enhancements:
Data Inventory Renamed to Resource Inventory
Data Inventory has been renamed to Resource Inventory.
[See image.](#ds-resourceinventory)
[]
![Shows the list of all the data detected.](/sites/default/files/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-viewing-graph-gcp-data-stores/rn-resourceinventory.png)
Evidence for Sensitive Data
DSPM generates evidence data for scanned files and tables which allows in-context investigation and validation of sensitive data. This is now supported for Azure.
To learn more, see [Viewing the Sensitive Data Details](/dspm/viewing-sensitive-data-details).
Hash of Scanned Files for Malware Scanning
DSPM calculates the hash of scanned files within unstructured data stores and displays this information on the Sensitive tab. A file hash can be used as an indicator of compromise (IoC) for creating and tracking incidents.
[See image.](#ds-hashof_file)
To learn more, see [About Resource Inventory](/dspm/about-data-inventory) and [Viewing the Data Inventory](/dspm/viewing-data-inventory-page).
[]
![Shows the sensitive data details.](/sites/default/files/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-viewing-graph-gcp-data-stores/rn-hash.png)
Resource Timeline
The Timeline tab displays Azure and GCP event details such as configuration and management changes for a specific time period, who made the change, what was the change, when it was made, etc.
[See image.](#ds-timeline)
To learn more, see [Viewing the Timeline Details for Resources](/dspm/viewing-timeline-details-resources).
[]
![Shows the timeline of events for the resource.](/sites/default/files/downloads/ds-timeline-rn_0.png)
AI & ML Tab for Virtual Machines
The AI & ML tab provides a comprehensive list of all the AI & Machine Learning packages and models installed on virtual machines across your cloud environment. This helps to ensure that only approved packages and models are used in the cloud.
[See image.](#ds-ai&mltab)
To learn more, see [Viewing the AI Service Details](/dspm/viewing-ai-service-details).
[]
![Shows the list of AI and ML models and packages.](/sites/default/files/downloads/ds-AI%26MLtab.png)

### Feature Available
#### Unmanaged AI Service Discovery
The DSPM dashboard provides a detailed view of all the unmanaged and custom AI models and services installed on virtual machines across AWS, Azure, and GCP. These services can also be identified by DSPM policies for specific risk alerts.
[See image.](#ds-unmanagedai)
To learn more, see [Viewing the AI and Machine Learning Details](/dspm/viewing-ai-and-machine-learning-details).
[]
![Shows the list of all the unmanaged AI models that have access to sensitive data.](/sites/default/files/downloads/ds-unmanagedaimodel.png)

## June 09, 2025
### Feature Available
#### Additional Predefined DSPM Role
DSPM offers a new predefined role, Data Analyst, with permissions for data investigation, analysis, and evidence. The role can be assigned to a specific group of users that need to access evidence data displayed on the Evidence tab.
[See image.](#data-analyst-role)
To learn more, see [Predefined DSPM Roles and Permissions](/dspm/predefined-roles-and-permissions) and [Viewing the Sensitive Data Details](/dspm/viewing-sensitive-data-details).
[]![The Roles page listing the predefined and custom roles.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/dspm-rn-user-access-management.png)

### Feature Available
#### Dashboard Enhancements
The DSPM dashboard includes the following enhancement:
Viewing Insights for AI Services
The DSPM dashboard includes the AI Security tab which provides detailed insights into the generative AI services that have access to data stores containing sensitive data, and the security posture risks associated with this data, such as improper guardrails, whether the sensitive data is publicly exposed, etc., along with the following details:
- The total number of AI services deployed in your organization.
- The total number of data stores that can be accessed by the AI service.
- The volume of sensitive data exposed to the AI service by models.
- The total number of files and tables that can be accessed by the AI services.
- The total number of open alerts for the AI services.
[See image.](#ds-aidashboard)
To learn more, see [Viewing the Statistics for AI Services.](/dspm/viewing-insights-ai-services)
[]
![Provides visibility into the types of sensitive data that AI services have access to.](/sites/default/files/downloads/dspm/analytics/graphs/viewing-graph-azure-data-stores/ds-aidashboard.gif)

### Feature Available
#### Data Duplication
DSPM detects duplicate files and displays the details on the Data Duplications page, allowing you to take corrective actions. Identifying copies of similar sensitive files at multiple locations is critical for multiple reasons, including data reduction, attack surface reduction, and for limiting the exposure to unauthorized users.
[See image.](#ds-dataduplications)
[]
![Shows copies of similar sensitive files at multiple locations.](/sites/default/files/downloads/tech-pubs-drafts/dspm-draft-articles/1-11-0-understanding-security-posture-state-draft/ds-data_duplications_dashboard.png)
To learn more, see [Viewing Duplicate Files](/dspm/viewing-duplicate-files).

### Feature Available
#### Data Inventory Enhancements
The data inventory includes the following enhancements:
Evidence for Sensitive Data
DSPM discovers files and tables containing sensitive data and generates evidence data, allowing you to review that there is sensitive data, and it is not a false positive. You can investigate and validate the findings with the respective DLP engines and dictionaries. Evidence is currently available for AWS resources.
[See image.](#ds-evidence-tab)
To learn more, see [Viewing the Sensitive Data Details](/dspm/viewing-sensitive-data-details).
Resource Timeline
The Timeline tab on the Data Inventory page is displayed for AWS data stores, providing visibility into the configuration and management changes for a specific time period. You can explore details like who made the change, the type of change, when it was made, etc.
[See image.](#ds-resourcetimeline)
[]
![Timeline tab provides visibility into the configuration and management changes made to a resource.](/sites/default/files/downloads/dspm/dashboard/viewing-insights-ai-services/ds-resourcetimeline-tab.png)
To learn more, see [Viewing the Timeline Details for Resources](/dspm/viewing-timeline-details-resources).
[]
![Shows the evidence generated for the detected sensitive data.](/sites/default/files/downloads/dspm/analytics/graphs/viewing-graph-azure-data-stores/ds-evidence-evidence.png)

### Feature Available
#### Data Posture Policies
The following new data posture policies are available:
- [AWS](#ds-aws-policies-1-11-0)
- [Azure](#ds-azure-policies-1-11-0)
- [GCP](#ds-gcp-policies-1-11-0)
[]
| Policy Title |
| ------------ |
| EC2 instances are encrypted with a KMS key that does not belong to AWS organization |
| EC2 instances containing sensitive data can be accessed by a misconfigured GitHub OIDC IAM role |
| RDS DB instance is encrypted with a KMS key that does not belong to AWS organization |
| RDS DB instance containing sensitive data can be accessed by a misconfigured GitHub OIDC IAM role |
| RDS DB cluster is encrypted with a KMS key that does not belong to AWS organization |
| RDS DB cluster containing sensitive data can be accessed by a misconfigured GitHub OIDC IAM role |
| S3 bucket containing sensitive data can be accessed by a misconfigured GitHub OIDC IAM role |
| AWS Bedrock Knowledge Base containing sensitive S3 data has public write access |
| AWS Bedrock Knowledge Base containing sensitive S3 data has excessive permissions |
| AWS Bedrock Knowledge Base containing sensitive S3 data is associated with AWS Bedrock Agent that has guardrails attached with PII filtering disabled |
| AWS Bedrock Knowledge Base containing sensitive S3 data is associated with AWS Bedrock Agent that has guardrails attached with prompt attack filter disabled |
| AWS Bedrock Knowledge Base containing sensitive S3 data is associated with AWS Bedrock Agent, where the agent session is encrypted with platform-managed key |
| AWS Bedrock Knowledge Base containing sensitive S3 data is associated with AWS Bedrock Agent where the confirmation for action group invocation is disabled |
| AWS Bedrock Knowledge Base containing sensitive S3 data is connected to Bedrock Agent where the action group is using Lambda with excessive permissions |
| AWS Bedrock Knowledge Base containing sensitive S3 data is associated with AWS Bedrock Agent with excessive permissions |
[]
| Policy Title |
| ------------ |
| Unmanaged Azure PostgreSQL server has databases containing sensitive data and allows insecure TLS versions |
| Unmanaged Azure PostgreSQL server has databases containing sensitive data and has SSL disabled |
| Unmanaged Azure PostgreSQL server has databases containing sensitive data and does not have appropriate logging configured |
| Azure PostgreSQL Flexible server has databases containing sensitive data that can be accessed by Azure Web App that is not integrated with a VNet |
| Azure PostgreSQL Flexible server has databases containing sensitive data and can be accessed by Azure Web App leveraging insecure basic SCM or FTP authentication publishing credentials |
| Azure PostgreSQL Flexible server has databases containing sensitive data and can be accessed by publicly exposed Azure Web App that allows insecure FTP access |
| Azure PostgreSQL Flexible server has databases containing sensitive data with Microsoft Entra authentication enabled and can be accessed by Azure virtual machines with critical vulnerabilities |
| Azure PostgreSQL Flexible server has databases containing sensitive data and can be accessed by Azure Web App that allows insecure TLS versions |
| Azure PostgreSQL Flexible server has databases containing sensitive data and can be accessed by publicly exposed Azure Linux Web App that is running deprecated versions of PHP, Python, and Node.js runtime application stacks |
| Azure AI Foundry Hub has access to a storage account containing sensitive blob data and has AI deployments with poorly configured content filter categories |
| Azure AI Foundry Hub has access to a storage account containing sensitive blob data and has AI deployments with default content filter policies |
| Azure AI Foundry Hub is associated with the hub workspace's storage account containing sensitive blob data that does not have private link enabled |
| Azure AI Foundry Hub is associated with the hub workspace's storage account containing sensitive blob data and has AI deployments with default content filter policies |
| Azure AI Foundry Hub is associated with the hub workspace's storage account containing sensitive blob data that is leveraging key-based access |
| Azure AI Foundry Hub is associated with the hub workspace's storage account containing sensitive blob data and has AI deployments with poorly configured content filter categories |
| Azure AI Foundry Hub that does not have diagnostic logging enabled is associated with hub workspace's Azure storage account containing sensitive blob data |
| Azure AI Foundry Hub that does not have diagnostic logging enabled has access to Azure storage account containing sensitive blob data |
[]
| Policy Title |
| ------------ |
| GCP Cloud SQL instance has databases containing sensitive data and has automated daily backup disabled |
| GCP Cloud MySQL instance has databases containing sensitive data and has point-in-time recovery disabled |
| GCP Cloud MS SQL instance has databases containing sensitive data and has point-in-time recovery disabled |
| GCP Cloud MS SQL instance has databases containing sensitive data and the server audit log retention period is less than 7 days |
| GCP Cloud MS SQL server has databases containing sensitive data and has server audit log disabled |
| GCP Cloud MySQL instance has databases containing sensitive data and has audit logging disabled |
| GCP Cloud PostgreSQL instance has databases containing sensitive data and has point-in-time recovery disabled |
| GCP Cloud PostgreSQL instance has databases containing sensitive data and has audit logging disabled |

### Feature Available
#### Scan Support for Additional Databases
DSPM provides support for scanning the following databases in AWS and Azure cloud environments:
- Unmanaged MySQL Database
- Unmanaged Oracle Database
DSPM expands the support for scanning unamanged MySQL and Oracle databases on cloud and on-premises environments (private and public data centers) through remote agentless scanning. Scan settings can be configured to define the scan scope and frequency, and databases can be assigned to data center objects for ease of reporting.
Based on these configurations, DSPM scans and classifies the data in all databases and tables in MySQL and Oracle servers, checks for misconfigurations, posture issues, and runs dedicated predefined policies for the service. All findings are displayed on the [Data Inventory page](/dspm/about-data-inventory). You can create [custom policies](/dspm/about-data-posture-policies) and [investigation queries](/dspm/about-investigation) to further optimize the protection.
To learn more, see:
- [About On-Premises Data Center](/dspm/about-data-center)
- [Adding Unmanaged Databases](/dspm/adding-unmanaged-database)
- [Configuring Scan Settings for Azure Unmanaged Database](/dspm/configuring-scan-settings-azure-unmanaged-database)
- [Configuring Scan Settings for AWS Unmanaged Database](/dspm/configuring-scan-settings-aws-unmanaged-databases)
- [Configuring Scan Settings for On-Premises Unmanaged Database](/dspm/configuring-scan-settings-premise-unmanaged-database)

## May 07, 2025
### Feature Available
#### Cloud Accounts Onboarding Enhancements
The following enhancements are introduced in cloud accounts onboarding:
Onboarding AWS Services
You can now select and onboard a subset of the supported AWS services (e.g., Storage bucket, Database, NoSQL Datastores, etc.). This option allows DSPM to have minimal permissions to monitor and scan the data only in these services.
[See image.](#select-services-tomonitor)
To learn more, see [Onboarding an AWS Organization](/dspm/onboarding-aws-organization), [Onboarding a Single AWS account](/dspm/onboarding-single-aws-account), and [Managing Services](/dspm/managing-services).
Onboarding GCP Accounts: Custom Network Settings for Orchestrator & Scanner Services
In addition to the existing GCP account onboarding flow in which the network settings for the orchestrator and scanner services are automatically set, DSPM now allows embedding the orchestrator and scanner services in the existing network settings and supports full functionality of the scanning platform.
[See image.](#rn-ds-custom)
To learn more, see [Onboarding a GCP Organization](/dspm/onboarding-gcp-organization).
[]![Choosing the custom network configuration window](/downloads/dspm/release-notes/release-upgrade-summary-2024/rn_custom_network_config.png)
[]
![The select services page listing the AWS services that must be monitored by DSPM.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/dspm-select-services-tomonitor.png)

### Feature Available
#### Compliance Dashboard Enhancements
To assess compliance improvements or degradations, you can view the number of failed policies and resources for the control category on the compliance dashboard. This information is available for each compliance framework.
[See image.](#rn-summarytab)
To learn more, see [Viewing Compliance Details](/dspm/viewing-compliance-details).
[]
![The Compliance page summary tab displaying the failed policies by severity and category, and compliance trend.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/rn-compliance-trend.png)

### Feature Available
#### Dashboard Enhancements
The DSPM dashboard includes the following enhancements:
AI Services Widget
AWS Bedrock Knowledge Bases and Agents are now monitored as a primary data store. The dashboard provides high-level visibility of AI services and exposed sensitive data stores. DSPM performs data scans and classification, inspects exposure, assesses posture, and detects misconfigurations.
[See Image.](#ai-services-widget)
To learn more, see [Viewing the Graph for AI Services](/dspm/viewing-graph-ai-services).
[]
![Lists the sensitive data exposed to AI services.](/sites/default/files/downloads/ds-aiservices-widget.png)
Models in AI Services
AI services in the cloud allow a variety of AI models to be used, which could be sanctioned or unsanctioned, and might pose risk to sensitive data. The AI Models tab on the DSPM dashboard provides a summary of the models in use across your AI services. This gives you visibility into all models in your cloud environment and allows quick detection of risky models that should be avoided.
[See Image.](#ds-ai-services-models)
To learn more, see [Viewing the Risk Scores](/dspm/viewing-risk-scores).
[]
![Lists the sensitive data exposed to AI models.](/sites/default/files/downloads/ds-ai-services-modeltab.png)

### Feature Available
#### Data Inventory Enhancements
The Data Inventory includes the following enhancements:
Access Tab for Unmanaged Databases
DSPM now analyzes unmanaged databases (MSSQL, PostgreSQL, etc.) for access permissions. The Access tab on the Data Inventory page displays details regarding who can access the data, their access level, roles, etc. On the Access tab, you can view the following information:
- Aggregation and visualization of database privileges.
- Privileged users and potential security issues related to sensitive data access.
- Actionable insights for improving database access policies.
[See image.](#ds-access-tab-unmanageddb)
To learn more, see [Viewing the Access Levels](/dspm/viewing-access-levels).
[]
![Access tab shows the access details of entities.](/sites/default/files/downloads/access-tab-unmanaged-mssql.png)
AI Service Details
DSPM scans AWS Bedrock Knowledge Bases and Agents as a primary resource type, and the scan results are displayed on the Data Inventory page. This allows you to review security misconfigurations, public exposure, data access, and more.
To learn more, see [Viewing the Graph for AI Services](/dspm/viewing-graph-ai-services).
Graph for AWS Bedrock Knowledge Base
DSPM now detects AWS Bedrock Knowledge Bases and Agents that can access data stores containing sensitive data. The scan results are displayed as a graph on the Risk Explorer** **tab.
[See image.](#ds-aws-bedrock-graph)
[]
![Graph nodes of AWS Bedrock Knowledge Base can be viewed.](/sites/default/files/downloads/ds-aws-bedrock-main-graph.png)

### Feature Available
#### Data Posture Policies
The following new data posture policies are available:
- [AWS](#ds-awspolicy-110)
- [Azure](#ds-azurepolicy-110)
- [GCP](#ds-gcppolicy-110)
[]
| Policy Title |
| ------------ |
| Unmanaged AWS Microsoft SQL server does not have audit logging with audit specifications configured |
| Unmanaged AWS Microsoft SQL server has databases containing sensitive data that do not have any backups |
| Unmanaged AWS Microsoft SQL server has databases containing sensitive data that are not encrypted with transparent data encryption (TDE) |
| Unmanaged AWS PostgreSQL server has databases containing sensitive data and has SSL disabled |
| Unmanaged AWS PostgreSQL server has databases containing sensitive data and does not have appropriate logging configured |
| Unmanaged AWS PostgreSQL server has databases containing sensitive data and allows insecure TLS versions |
| AWS DynamoDB table with sensitive data is encrypted with a KMS key that does not belong to AWS organization |
| S3 bucket containing sensitive data is encrypted with a KMS key that does not belong to AWS organization |
| AWS Bedrock Knowledge Base containing sensitive S3 data has logging disabled |
| AWS Bedrock Knowledge Base contains sensitive S3 data |
| AWS Bedrock Knowledge Base containing sensitive S3 data is associated with AWS Bedrock Agent that has guardrails attached but is encrypted with PMK |
| AWS Bedrock Knowledge Base containing sensitive S3 data is associated with AWS Bedrock Agent that does not have guardrails attached to it |
| AWS Bedrock Knowledge Base containing sensitive S3 data that is associated with AWS Bedrock Agent is using default post-processing template |
| AWS Bedrock Knowledge Base containing sensitive S3 data that is associated with AWS Bedrock Agent is using default preprocessing template |
| AWS Bedrock Knowledge Base containing sensitive S3 data that is associated with AWS Bedrock Agent has default orchestration template |
| AWS Bedrock Knowledge Base containing sensitive S3 data is associated with AWS Bedrock Agent that has code interpretation enabled without guardrails |
[]
| Policy Title |
| ------------ |
| Azure AI Foundry Hub has access to a storage account containing sensitive blob data and has risky models deployed |
| Azure AI Foundry Hub is associated with the hub workspace's storage account containing sensitive blob data and has risky models deployed |
| Azure AI Foundry Hub that is not encrypted with CMK is associated with an Azure storage account containing sensitive blob data |
| Azure AI Foundry Hub that is not encrypted with CMK has access to Azure storage account containing sensitive blob data |
| Azure AI Foundry Hub with unrestricted outbound access control is associated with a hub workspace's storage account containing sensitive blob data |
| Azure AI Foundry Hub with unrestricted outbound access control has access to Azure storage account containing sensitive blob data |
| Publicly accessible Azure AI Foundry Hub is associated with storage accounts containing sensitive blob data |
| Publicly accessible Azure AI Foundry Hub has access to storage accounts containing sensitive blob data |
[]
| Policy Title |
| ------------ |
| GCP Cloud SQL instance has databases containing sensitive data and has deletion protection disabled |
| GCP Cloud SQL instance has databases containing sensitive data and is deployed in a non-high availability zone |
| GCP Cloud SQL instance has databases containing sensitive data and is encrypted with CMK that does not have key rotation enabled |
| GCP Cloud SQL instance has databases containing sensitive data and is without CMK |
| GCP Cloud SQL instance has databases containing sensitive data and is publicly exposed |
| GCP Cloud SQL instance has databases containing sensitive data and allows unencrypted incoming connections |

### Feature Available
#### Data Scan Enhancements
The data scan includes the following enhancements:
Support for Scanning GCP Compute Engines
DSPM scans and classifies the data in disks associated with GCP compute engines, checks for misconfigurations and posture issues, performs vulnerability analysis, checks for access and entitlements issues, and runs dedicated predefined policies. GCP compute engines can now be explored and investigated on the dashboard, and the [Data Inventory](/dspm/about-data-inventory) and [Alerts](/dspm/about-alerts) pages. You can create [custom policies](/dspm/about-data-posture-policies) and [investigation queries](/dspm/about-investigation) to further optimize the protection.
[See image.](#rn-ds-scan-gcp-vm)
To learn more, see [Configuring Scan Settings for GCP Virtual Machine](/dspm/configuring-scan-settings-gcp-virtual-machine).
On-Premises Database Scanning for MSSQL
DSPM provides support for on-premises database scanning. DSPM can perform remote agentless scanning of the MSSQL database servers stored in private and public data centers. This enables the scanning of sensitive data in unmanaged databases. Databases can be assigned to data center objects for ease of reporting. Scan settings can be configured to define the scan scope and frequency.
[See image.](#ds-admin-on-premise-ds)
To learn more, see [About On-Premises Data Center](/dspm/about-data-center) and [Configuring Scan Settings for On-Premises Data Center](/dspm/configuring-scan-settings-premise-unmanaged-database).
[]![Select cloud type and resource type page annotating GCP as cloud type and Virtual Machine as resource type.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/rn-ds-scan-gcp-vm.png)
[]![Image]()
![DSPM Admin page displaying the configuration tiles with an annotation around On-Premises Data Centers.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/rn-ds-admin-on-premises-dc.png)

### Feature Available
#### Investigation and Policy Query Enhancements
The investigation and policy queries are enhanced with the following predicates and operators for improved metadata analysis and enrichment:
Predicates for Unmanaged PostgreSQL
You can use the following relationship predicate to query the unmanaged PostgreSQL database: Can be accessed by.
To learn more, see [Creating an Investigation](/dspm/creating-new-investigation) and [Creating Custom Policies](/dspm/creating-custom-policies).
Predicates for GCP Compute VM
You can use the following relationship predicates to query the GCP Compute VM:
- Can be accessed by
- Has Entitlement
- Has Access to
To learn more, see [Creating an Investigation](/dspm/creating-new-investigation).
Predicate for AI Service
The Exposed to AI service predicate allows you to check whether any storage account containing sensitive data is exposed to an AI service. The exposure could be through a permission or an access configuration in the AI service or a combination of both.
To learn more, see [Viewing Graph for AI Services](/dspm/viewing-graph-ai-services).

## March 27, 2025
### Feature Available
#### AI Service Details in Data Inventory
AI services such as Azure AI Foundry Hub are considered as data stores and explored for content and security posture, allowing you to review security misconfigurations, public exposure, data access, and more. DSPM monitors the AI services and displays the findings on the Data Inventory page and graph.
Graph for Azure AI Services
DSPM now detects AI services (Azure AI Foundry Hub) that can access data stores containing sensitive data. The scan results for an AI service are displayed on the Data Inventory page and graph.
[See image.](#ds-rn-aigraph)
Public Exposure for AI Services
An Azure AI Foundry Hub attached to machine learning (ML) workspaces can be exposed to the internet, leading to unauthorized access. The graph shows the public exposure details.
[See image.](#ds-rn-pedetails)
To learn more, see [Viewing the Graph for AI Services](/dspm/viewing-graph-ai-services%20%20) and [About Data Inventory](/dspm/about-data-inventory).
New Posture Label: Exposed to AI Service
Sensitive data exposed to AI services is at risk of unwanted public exposure to AI service users and applications. DSPM analyzes the permissions and configurations that lead to exposing data stores containing sensitive data to the AI service. Such data stores are highlighted with a new posture label called Exposed to AI Service. You can see this information on the Data Inventory page.
[See image.](#ds-rn-accountposture)
To learn more, see [Understanding the Security Posture State](/dspm/understanding-security-posture-state).
[]![Graph showing the sensitive records exposed to the Azure AI Foundry Hub](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-ai-graph2.png)
[]![Details of how the Azure AI Foundry is exposed to the internet.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/d-ai-publicexposuredetails.png)
[]![Security posture label applied to the storage account](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-di-aiposturelabel.png)

### Feature Available
#### AWS Single Account Onboarding
DSPM now supports the onboarding of AWS single accounts to monitor and scan the data stores within them. This option can be used when there are restrictions for onboarding accounts at the organization level.
[See image.](#aws-standalone-account)
To learn more, see [Onboarding an AWS Account](/dspm/onboarding-aws-account).
[]![The Select Cloud Provider page with the list of available cloud types and AWS onboarding types.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/dspm-rn-aws-standalone-account.png)

### Feature Available
#### Compliance Dashboard Enhancements
The Compliance dashboard includes the following enhancements:
-
On the Summary tab, you can view the number of failed policies by severity and control category.
[See image.](#summary-tab)
-
The Policies tab displays the list of policies that failed to comply with the benchmark.
[See image.](#policies-tab)
-
The Resources tab displays the list of failed resources.
[See image.](#resources-tab)
To learn more, see [Viewing Compliance Details](/dspm/viewing-compliance-details).
[]![The policies tab with the list of failed policies.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/dspm-rn-compliance-policies-tab.png)
[]![The Resources tab with the list of failed resources.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/dspm-rn-compliance-resources-tab.png)
[]![The summary tab with the list of failed policies by severity and control category.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/dspm-rn-compliance-summary-tab.png)

### Feature Available
#### Dashboard Enhancements
DSPM provides support for detecting AI services that have access to data stores containing sensitive data, the security posture of the AI services, and the overall risks. This information is crucial so you can apply security controls and manage the sensitive data that is exposed to the AI services.
AI Services Widget
The dashboard provides high-level visibility into the exposure of sensitive data to Azure AI Foundry Hubs, the foundational models that are used in your cloud environments, including the type of data being consumed, the number of triggers that can be accessed by the AI service and the associated risk.
[See image.](#ds-rn-risktab)
Changes in the Top Risk Data Stores Widget
The See All link in the Top Risk Data Stores widget directs you to the Data Inventory page.
[See image.](#ds-rn-seeall)
To learn more, see [Viewing the Risk Scores](/dspm/viewing-risk-scores).
View Top Accounts and Data Stores on the Data Discovery Tab
The Data Discovery tab on the dashboard displays the top accounts and data stores along with insights into the data in your cloud environment.
- Top Accounts: View high-level metrics of the top accounts in your cloud environment to prioritize the remediation actions. This widget provides a summary of the top 5 accounts in descending order based on the amount of sensitive data in each account.
- Top Data Stores: View the top 5 data stores that have the maximum amount of sensitive data. The data stores are listed in descending order based on the amount of sensitive data.
[See image.](#ds-rn-datatab)
To learn more, [Viewing the Statistics for Scanned Data](/dspm/viewing-statistics-scanned-data).
[]
![The AI Services widget shows details of the AI services having access to sensitive data](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-db-aiwidget.png)
[]
![Statistics of the data discovered and scanned, top risk accounts and data stores](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-db-datadiscoverytab.png)
[]
![Click the See All link to view resource details on the Data Inventory page](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-db-seealllink.png)

### Feature Available
#### Data Posture Policies
The following new data posture policies are available:
- [AWS](#ds-awspolicy-190)
- [Azure](#ds-azurepolicy-190)
- [GCP](#ds-gcppolicy-190)
[]
| Policy Title |
| ------------ |
| RDS DB instance containing sensitive GDPR data has data stored outside EU. |
| RDS DB instance containing sensitive data does not have SNS topic subscription for all RDS event types. |
| RDS DB cluster containing sensitive GDPR data has data stored outside EU. |
| EC2 instance containing GDPR data has data stored outside EU. |
| S3 bucket containing sensitive GDPR data has data stored outside EU. |
| AWS DynamoDB table containing GDPR data has data stored outside EU. |
[]
| Policy Title |
| ------------ |
| Azure storage account containing sensitive blob data has GDPR data stored outside EU. |
| Azure storage account containing sensitive blob data is associated with Azure Key Vault that has RBAC enabled and can be accessed by Entra ID applications accepting external or personal Azure accounts with high privileges. |
| Azure storage account containing sensitive blob data is associated with Azure Key Vault that has RBAC enabled and can be accessed by external users. |
| Azure storage account containing sensitive blob data is associated with Azure Key Vault without RBAC authorization. |
| Azure storage account containing sensitive blob data is associated with Azure Key Vault that has soft delete retention of less than 90 days. |
| Azure storage account containing sensitive blob data is associated with Azure Key Vault that has soft delete disabled. |
| Azure storage account containing sensitive blob data is associated with Azure Key Vault that has purge protection disabled. |
| Azure storage account containing sensitive blob data is associated with Azure Key Vault that has public network access enabled. |
| Azure virtual machine containing sensitive data does not have Azure Monitor Agent deployed and diagnostic logging enabled. |
| Azure virtual machine containing GDPR data has data stored outside EU. |
| Azure SQL server has databases containing GDPR data and data is stored outside EU. |
| Azure SQL server has databases containing sensitive data that do not have long-term backups configured. |
| Azure PostgreSQL Flexible server has databases containing sensitive data that can be accessed by Azure Web App that allows insecure FTP access. |
| Azure PostgreSQL Flexible server has databases containing GDPR data and data is stored outside EU. |
| Azure PostgreSQL Flexible server has databases containing sensitive data that do not have replication configured. |
| Azure PostgreSQL Flexible server has databases containing sensitive data that do not have high availability configured. |
| Azure PostgreSQL Flexible server has databases containing sensitive data that do not have server log export configured. |
| Unmanaged Azure Microsoft SQL server has databases containing sensitive data that do not have any backups. |
| Unmanaged Azure Microsoft SQL server does not have audit logging with audit specifications configured. |
| Unmanaged Azure Microsoft SQL server has databases containing sensitive data that are not encrypted with transparent data encryption (TDE). |
[]
| Policy Title |
| ------------ |
| GCP storage bucket containing sensitive GDPR data has data stored outside EU. |
| GCP storage bucket with managed folders containing sensitive GDPR data has data stored outside EU. |

### Feature Available
#### Document Types and Categories
AI or machine language (ML) classification is extended to support over 100 new document types across 10 common document categories. This classification can be applied over any scanned file and can be used in DSPM policies.
Document types and categories are visible on the Data Inventory page, dashboard, and data classification reports, and there is no need for any additional configuration.
[See image.](#ds-rn-doctypelist)
To learn more, see [Understanding Data Classification](/dspm/understanding-data-classification).
[]
![The Data Inventory page shows the files that match specific document types and categories.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-di-doctypes.png)

### Feature Available
#### Expanded Data Store Support
DSPM now provides support for scanning the following data stores:
- Google Cloud SQL Instances (MSSQL, PostgreSQL, MySQL)
- Unmanaged PostgreSQL databases on Azure and AWS
- AWS Unmanaged MSSQL databases on AWS EC2 instances, in addition to unmanaged MSSQL support over Azure which is already supported for versions 2016, 2017, 2019, 2022.
Based on the scan setting configuration, DSPM scans and classifies data in the relevant databases and tables, checks for misconfigurations and posture issues, and runs dedicated predefined policies.
You can see the scan results on the [Data Inventory page](/dspm/about-data-inventory) and [Alerts page](/dspm/about-alerts). You can create [custom policies ](/dspm/about-data-posture-policies)and [investigation queries](/dspm/about-investigation) to further optimize the protection.
[See image.](#rn-img)
To learn more, see [Configuring Scan Settings for Azure Unmanaged Database](/dspm/configuring-scan-settings-azure-unmanaged-database), [Configuring Scan Settings for AWS Unmanaged Database](/dspm/configuring-scan-settings-aws-unmanaged-databases), and [Configuring Scan Settings for GCP Database](/dspm/configuring-scan-settings-gcp-database).
[]![The cloud and resource screen with annotations around Google Cloud, and Database resource.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-scan-gcp-database.png)
![The cloud and resource screen with annotations around Azure Cloud, Database resource, and Unmanaged Database type.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-scan-azure-umdb.png)
![The cloud and resource screen with annotations around AWS Cloud, Database resource, and Unmanaged Database type.](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-scan-aws-database-unmanaged.png)

### Feature Available
#### Investigation - Updates to Has Data Predicate
The Has Data relationship predicate is updated with new predicates that allow querying data stores based on the number of discovered DLP triggers, volume of sensitive data discovered or number of sensitive files or rows discovered.
The following new predicates are available:
- Sensitive Data Triggers
- Sensitive Data Matches
- Sensitive Data Volume
- Last Completed Scan
[See image.](#ds-rn-hasdatapredicates)
To learn more, see [Creating a New Investigation](/dspm/creating-new-investigation).
[]![Additional sub-predicates to find more details about the data](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/ds-invest-hasdatapred.png)

## February 20, 2025
### Feature Available
#### Azure AI Foundry and Storage Account Association
AI services such as Azure AI Foundry Hub leverage storage accounts to host the AI training data. DSPM provides visibility of sensitive data that is exposed to Azure AI services and machine learning workspaces on the Data Inventory page. This information allows you to create policies or investigation queries and search for sensitive data exposed to the AI services.
To learn more, see [About Data Inventory](/dspm/about-data-inventory) and [Creating a New Investigation](/dspm/creating-new-investigation).

### Feature Available
#### Data Posture Policies
The following new data posture policies for Azure are available:
- [Azure](#ds-azurepolicy-180)
[]
| Policy Title |
| ------------ |
| Azure PostgreSQL Flexible server with databases containing sensitive data is publicly exposed. |
| Azure PostgreSQL Flexible server with databases containing sensitive data is publicly exposed and has password authentication enabled. |
| Azure PostgreSQL Flexible server with databases containing sensitive data can be accessed by publicly exposed App Service with risky permissions. |
| Azure PostgreSQL Flexible server has databases containing sensitive data that can be accessed by Entra ID applications that accept external or personal Azure accounts with high privileges. |
| Azure PostgreSQL Flexible server has databases containing sensitive data that do not have audit logging enabled. |
| Azure PostgreSQL Flexible server has databases containing sensitive data that do not have private access VNet configured. |
| Azure PostgreSQL Flexible server has databases containing sensitive data that do not have geo-redundant backups enabled. |
| Azure PostgreSQL Flexible server has databases containing sensitive data that can be accessed by publicly exposed Linux Web App that has SSH enabled. |
| Azure PostgreSQL Flexible server has databases containing sensitive data that can be accessed by users who have not logged in for more than 90 days. |
| Azure PostgreSQL Flexible server has databases containing sensitive data that can be accessed by users who have not logged in for more than 90 days but have logged in via cached sessions or OAuth-based SaaS apps in the last 7 days. |
| Azure PostgreSQL Flexible server has databases containing sensitive data that are susceptible to ransomware. |
| Azure PostgreSQL Flexible server has databases containing sensitive data that can be accessed by users without MFA and with highly risky permissions. |
| Azure PostgreSQL Flexible server has databases containing sensitive data that do not have resource locks enabled. |
| Azure PostgreSQL Flexible server has databases containing sensitive data that do not have logging enabled for diagnostic settings. |
| Azure PostgreSQL Flexible server has databases containing sensitive data that do not have secure transport enabled. |
| Azure PostgreSQL Flexible server has databases containing sensitive data that are not encrypted using customer-managed keys. |
| Azure PostgreSQL Flexible server has databases containing sensitive data that have Entra authentication enabled and can be accessed by publicly exposed Azure virtual machines with admin privileges and critical vulnerabilities. |
| Azure SQL server has databases containing sensitive data and can be accessed by publicly exposed Azure Linux Web App that is running deprecated versions of PHP, Python, and Node.js runtime application stacks. |
| Azure SQL server with databases containing sensitive data can be accessed by Azure Web App leveraging insecure basic SCM or FTP authentication publishing credentials. |
| Azure SQL server with databases containing sensitive data can be accessed by publicly exposed Azure Web App that allows insecure FTP access. |
| Azure SQL server has databases containing sensitive data that can be accessed by Azure Web App that is not integrated with a VNET. |
| Azure SQL server has databases containing sensitive data that can be accessed by Azure Web App that allows insecure FTP access. |
| Azure storage account containing sensitive blob data can be accessed by Azure Web App that is not integrated with a VNet. |
| Azure storage account containing sensitive blob data can be accessed by publicly exposed Azure Web App that allows insecure FTP access. |
| Azure storage account containing sensitive blob data can be accessed by Azure Web App that allows insecure FTP access. |
| Azure storage account containing sensitive blob data can be accessed by Azure Web App leveraging insecure basic SCM or FTP authentication publishing credentials. |

### Feature Available
#### Enhancements for Onboarding Azure Accounts
The Azure onboarding process is updated with the following enhancements:
Onboard Management Groups
DSPM now supports the onboarding of Azure management groups and scans the subscriptions within them. This option can be used when there are restrictions for onboarding at the tenant level.
[See image.](#azuremanagementgroup)
To learn more, see [Onboarding a Microsoft Azure Tenant](/dspm/onboarding-microsoft-azure-tenant).
Onboard Azure Services
You can now select and onboard a subset of the supported Azure services (storage accounts, databases, etc.). This option allows DSPM to have minimal permissions to monitor and scan the data only in these services.
[See image.](#servicestomonitor)
To learn more, see [Onboarding a Microsoft Azure Tenant](/dspm/onboarding-microsoft-azure-tenant) and [Managing Services](/dspm/managing-services).
[]![List of services and selected checkboxes for those chosen to be monitored](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/dspm-select-services-to-monitor.png)
[]![Select Cloud Provider page with cloud types in tiles and onboarding types in tiles](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/dspm-azure-management-group.png)

### Feature Available
#### Support for Scanning Unmanaged MSSQL Databases
DSPM provides support for onboarding and scanning unmanaged Microsoft SQL Server (MSSQL) databases hosted on Azure virtual machines. Based on the scan setting configuration, DSPM scans and classifies data in these databases and identifies misconfigurations and posture issues.
The scan results are displayed on the [Data Inventory page](/dspm/about-data-inventory). You can create [custom policies](/dspm/about-data-posture-policies) and [investigation queries](/dspm/about-investigation) to further optimize the protection.
[See image.](#img_umdb)
To learn more, see [About Unmanaged Databases](/dspm/about-unmanaged-database) and [Configuring Scan Settings for Azure Unmanaged Databases](/dspm/configuring-scan-settings-azure-unmanaged-database).
[]![Administration page with tile list of configurations and an annotation around Unmanaged Databases tile. ](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/rn_unmanagedDB.png)

## January 16, 2025
### Feature Available
#### Compliance Dashboard
The Compliance dashboard provides an overview of the compliance breaches detected by DSPM for industry-standard data protection regulations and benchmarks such as CIS, NIST, PCI DSS, HIPAA, GDPR, DPDP, CCPA, RBI, ISO 27001, and SOC2. The Compliance dashboard provides insights into the overall compliance status and the total number of policies that failed to comply with each benchmark. You can also view the policy summary and compliance configuration details. The dashboard also provides actionable steps to remediate compliance violations.
[See image.](#compliance_frameworks)
To learn more, see [About Compliance](/dspm/about-compliance) and [Viewing Compliance Details](/dspm/viewing-compliance-details).
[]
![View compliance frameworks](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/Compliance.png)

### Feature Available
#### Dashboard Enhancements
The dashboard includes the following enhancements:
- A legend is added to provide context to the risk score values displayed on the dashboard.
[See image.](#risk_score_legend)
- The scan statistics is moved to the Data Discovery tab.
[See image.](#scan_statistics)
To learn more, see [About the Dashboard](/dspm/about-dashboard).
[]
![View risk score legend ](/sites/default/files/downloads/dspm/analytics/compliance/about-compliance/Dashboard_Risk%20Legend.png)
[]
![View scan statistics](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/Dashboard_Scan%20Statistics.png)

### Feature Available
#### Data Posture Policies
The following new data posture policies are available for cloud service providers:
- [AWS](#ds-aws-policy-170)
- [Azure](#ds-azure-policy-170)
[]
| Policy Title |
| ------------ |
| RDS DB instance containing sensitive data encrypted with customer-managed key has KMS key rotation disabled. |
| RDS DB instance containing sensitive data can be accessed by external users. |
| RDS DB cluster containing sensitive data encrypted with customer-managed key has KMS key rotation disabled. |
| RDS DB cluster containing sensitive data can be accessed by external users. |
| S3 bucket containing sensitive data encrypted with customer-managed key has KMS key rotation disabled. |
| S3 bucket with sensitive data can be accessed by IAM entities with high privilege roles that have not been used for more than 90 days. |
| EC2 instance containing sensitive data has VPC flow logs disabled. |
| Virtual machine containing sensitive data can be accessed by identities with permissions to modify network security groups. |
| RDS Aurora, MySQL, and PostgreSQL DB clusters containing sensitive data have IAM authentication enabled with a weak IAM password policy. |
| RDS Aurora, MySQL, and PostgreSQL DB instances containing sensitive data have IAM authentication enabled with a weak IAM password policy. |
| AWS DynamoDB table containing sensitive data can be accessed by external entities with risky access. |
| AWS DynamoDB table containing sensitive data has data logging disabled. |
| AWS DynamoDB table containing sensitive data is readable externally. |
| AWS DynamoDB table containing sensitive data is accessible by all IAM principals. |
| AWS DynamoDB table with sensitive data is publicly exposed. |
| AWS DynamoDB table containing sensitive data does not have deletion protection enabled. |
| AWS DynamoDB table containing sensitive data does not have global tables replica configured. |
| AWS DynamoDB table does not have point-in-time restore enabled. |
| AWS DynamoDB table containing sensitive data is not encrypted using a customer-managed key. |
[]
| Policy Title |
| ------------ |
| Azure SQL server database containing sensitive data can be accessed by publicly exposed App Service with risky permissions. |
| Azure SQL Server with databases containing sensitive data can be accessed by Azure Web App that allows insecure TLS versions. |
| Azure SQL database server has databases containing sensitive data that do not have logging enabled for diagnostic settings. |
| Azure storage account containing sensitive blob data can be accessed by publicly exposed App Service with risky permissions. |
| Azure storage account containing sensitive blob data can be accessed by a publicly exposed Azure Linux Web App that is running deprecated versions of PHP, Python, and Node.js runtime application stacks. |
| Azure storage account containing sensitive blob data can be accessed by Azure Web App that allows insecure TLS versions. |
| Azure storage account containing sensitive blob data should be accessed only through Azure private endpoints. |
| Azure virtual machine containing sensitive data has public IP with basic SKU and no network security group attached to the interface and subnet. |
| Virtual machine containing sensitive data can be accessed by identities with permissions to modify network security groups. |

### Feature Available
#### Enhancements to Cloud Accounts Onboarding Workflow
The Cloud Accounts onboarding process is updated with the following enhancements:
Deploy Orchestrator and Scanner Instances in Custom Network
DSPM provides support for deploying the orchestrator and scanner instances in your organization's existing network settings.
[See image.](#custom_network)
To learn more, see [Onboarding an AWS Organization](/dspm/onboarding-aws-organization) and [Onboarding a Microsoft Azure Tenant](/dspm/onboarding-microsoft-azure-tenant).
Azure Diagnostic Logs Storage
You can specify an existing Azure storage account or configure a new Azure storage account to store the diagnostic logs.
[See image.](#byonconfigure-regions)
To learn more, see [Onboarding a Microsoft Azure Tenant](/dspm/onboarding-microsoft-azure-tenant).
[]![Choosing the custom network configuration window](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2024/rn_custom_network_config.png)
[]![Select the regions that must be monitored](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/LogStorage_RN1.png)

### Feature Available
#### Investigation and Policy Query Enhancements
The investigation and policy queries are enhanced with the following predicates and operators for improved metadata analysis and enrichment:
Custom Policy and Investigation Queries for AWS DynamoDB
DSPM supports entitlements for AWS DynamoDB and allows you to create custom policies and investigation queries. The predefined policies for DynamoDB are also extended to support entitlements.
[See image.](#aws_dynamodb_Table)
To learn more, see [Creating an Investigation](/dspm/creating-new-investigation) and [Creating Custom Policies](/dspm/creating-custom-policies).
Security Posture Logging for AWS EC2 Instances
The Logging state is added as a security posture for AWS EC2 instances. You can use the Logging predicate in policy and investigation queries to monitor the logging state of your EC2 instances.
[See image.](#logging_predicate_for_EC2_Instance)
To learn more, see [Creating an Investigation](/dspm/creating-new-investigation), [Creating Custom Policies](/dspm/creating-custom-policies), and [Understanding the Security Posture State](/dspm/understanding-security-posture-state).
[]
![View AWS DynamoDB Table predicates](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/DynamoDB%20in%20Policy%20and%20Investigation_0.png)
[]
![View logging predicate for EC2 Instance](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/Logging%20for%20EC2%20Instance.png)

### Feature Available
#### MFA for Local Users
To improve the security of user authentication, DSPM has enabled multi-factor authentication for local users while logging in. After entering the login ID, a verification code is sent to the registered email address, and this code is valid for 10 minutes.
[See image.](#dspm-verification-code)
To learn more, see [Accessing and Navigating the DSPM Admin Portal](/dspm/accessing-and-navigating-dspm-admin-portal).
[]![Enter the Verification Code](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/dspm-verification-code.png)

### Feature Available
#### Scan Settings Enhancements
The scan settings include the following enhancements:
Support for Azure-Managed PostgreSQL Flexible Server
DSPM provides support for scanning the Azure-Managed PostgreSQL Flexible Server. Based on the scan setting configuration, DSPM scans and classifies data in the relevant SQL servers, checks for misconfigurations, posture issues, and runs dedicated predefined policies for Azure PostgreSQL. All findings are displayed on the [Data Inventory page](/dspm/about-data-inventory). You can create [custom policies](/dspm/about-data-posture-policies) and [investigation queries](/dspm/about-investigation) to further optimize the protection.
To learn more, see [Configuring Scan Settings for Azure Database](/dspm/configuring-scan-settings-azure-database).
Database Scanning Options
You can select the following options while configuring the scan settings for databases:
- **Data Sampling Scan**: Scans a sample of recent data in the database, providing a faster approach with lower cost.
- **Full Scan**: Scans all the databases across all onboarded accounts, providing a detailed data scan report.
[See image.](#img_scantype)
To learn more, see [Configuring Scan Settings for Azure Database](/dspm/configuring-scan-settings-azure-database) and [Configuring Scan Settings for AWS Database](/dspm/configuring-scan-settings-aws-database).
[]![Select Scan Type](/sites/default/files/downloads/dspm/release-notes/release-upgrade-summary-2025/scan_type.png)
