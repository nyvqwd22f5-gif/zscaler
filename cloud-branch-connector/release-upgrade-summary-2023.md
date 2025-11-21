# Release Upgrade Summary (2023)
Source: https://help.zscaler.com/zpc/release-upgrade-summary-2023

This article provides a summary of all new features and enhancements for Zscaler Posture Control (ZPC). To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com/).

**Clouds:** app.zpccloud.net, eu.zpccloud.net
The following service updates were deployed to app.zpccloud.net on

## October 30, 2023
### Feature Available
#### Enhancement to Asset Property Predicate Operators
The asset property predicate supports two new operators for IP address and integer property types: Included In (**⊆**) and Not Included In (**⊈**).
To learn more, see [Creating Custom Security Policies](/zpc/creating-custom-security-policies).

### Feature Available
#### Enhancement to Ignore Compliance Rules
ZPC allows you to configure ignore rules to exclude irrelevant compliance findings. ZPC does not display any ignore compliance findings on the compliance dashboards or reports. Using compliance ignore filters can affect ZPC's compliance score evaluation. When you ignore or include an asset or policy on ZPC, the compliance score might change.
You can configure compliance ignore rules based on a combination of policies, asset types, regions, and accounts.
[See image.](#compliance-auto-ignore-rule-2-13)
To learn more, see [Configuring an Automatic Compliance Ignore Filter](/zpc/configuring-automatic-compliance-ignore-filter).
[]
![View the compliance ignore rules page on ZPC.](/sites/default/files/downloads/zpc/cloud-posture/compliance/about-compliance/zpc-compliance-auto-ignore-rule-rn-img.png)

### Feature Available
#### Security Policies
The following security policies are available for cloud service providers:
- [Kubernetes](#kubernetes-2-13-security-policy)
To learn more, see [About Security Policies](/zpc/about-security-policies).
[]
Security Policy TitleEKS CIS - Avoid use of system:masters groupEKS CIS - Limit use of the Bind, Impersonate and Escalate permissions in the Kubernetes cluster [Role]EKS CIS - Ensure Image Vulnerability Scanning using Amazon ECR image scanning or a third party providerAKS CIS - Restrict Access to the Control Plane EndpointAKS CIS - Ensure clusters are created with Private Endpoint Enabled and Public Access DisabledAKS CIS - Use Azure RBAC for Kubernetes AuthorizationGKE CIS - Manage Kubernetes RBAC users with Google Groups for GKEGKE CIS - Ensure Kubernetes Web UI is DisabledK8s CIS - Limit use of the Bind, Impersonate and Escalate permissions in the Kubernetes cluster [ClusterRole]K8s CIS - Ensure that all Namespaces have Network Policies definedK8s CIS - Minimize access to create pods through Cluster RoleK8s CIS - Minimize access to secrets through Cluster RoleK8s CIS - Minimize access to secrets through RoleK8s CIS - Ensure that Service Account Tokens are only mounted where necessary for Service AccountK8s CIS - Ensure that default service accounts are not actively usedK8s CIS - Minimize access to create pods through RoleK8s CIS - Minimize wildcard use in ClusterRolesK8s CIS - Minimize wildcard use in RolesK8s CIS - Ensure that the --event-qps argument is set to 0 or a level which ensures appropriate event capture

### Feature Available
#### Trusted IP Management
ZPC allows you to create and upload a list of trusted IP addresses used by your organization to access the public environment. ZPC excludes these trusted IPs when examining assets or identities that are publicly exposed and eliminates false alerts generated for IPs.
The trusted IP list helps identify public exposure scenarios and distinguishes between either an exposure that serves a legitimate business purpose or one that poses a security risk.
[See image.](#trusted-ip)
To learn more, see [About Trusted IPs](/zpc/about-trusted-ips).
[![View the Trusted IP Management page](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-trusted-ip-management.png)
]

## September 27, 2023
### Feature Available
#### Ignore Compliance Filters
You can selectively ignore compliance security policies or assets on your cloud deployment from being evaluated by ZPC. You can use the compliance ignore filters to perform actions such as:
- Ignore specific compliance security policies for all AWS S3 buckets in your cloud deployment because you use S3 buckets exclusively for internal testing.
- Ignore non-production EC2 instances for specific compliance security policies.
Using compliance ignore filters can affect ZPC's compliance score evaluation. When you ignore or include an asset or policy on ZPC, the compliance score might change.
To learn more, see [Configuring a Compliance Ignore Filter](/zpc/configuring-compliance-ignore-filter).

## September 13, 2023
### Feature Available
#### Alert Payload with Additional Attributes Sent to IT Service Management
Cloud and IaC alert payloads that are sent from ZPC to ITSM (Jira and ServiceNow) are enhanced to include additional attributes: Audit Procedure, Remediation, and Resource Metadata.
[See image.](#metadata)
To learn more, see [About Alerts](/zpc/about-alerts#viewing-alert-notifications-tab) and [Adding Alert Rules](/zpc/adding-alert-rules).
[![View the additional alert attributes](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-alert-metadata.png)
]

### Feature Available
#### Alert Timeline
You can view all activities of a cloud alert, the timestamp for when the alert was created and when the alert status was updated, and the ZPC user who performed the action on the alert.
[See image.](#timeline-tab)
To learn more, see [Viewing Alert Details](/zpc/viewing-alert-details).
[![View the Alert Timeline tab](/sites/default/files/downloads/zpc/alerts/alert-details/viewing-cloud-alerts-grouped-policy/zpc-cloud-alerts-timeline-tab.png)
]

### Feature Available
#### AWS Local Identities Support
ZPC offers authentication information such as access keys, passwords, or certificates for all AWS local identities. ZPC supports AWS local identities in the investigation and custom policy query creator. You can use AWS local identity predicates for queries such as:
- Find all active identities that have an access key that expired last month.
- Find all identities that have set up both password-based authentication and have access keys.
[See image.](#aws-local-identity-2-12)
To learn more, see [Viewing Cloud Identity Details](/zpc/viewing-cloud-identity-details) and [Creating a New Investigation](/zpc/creating-new-investigation#identity-authentication).
[]
![View the identity authentication tab on ZPC.](/sites/default/files/downloads/zpc/cloud-posture/cloud-identities/viewing-cloud-identity-details/zpc-identity-details-authentication-release-note.png)

### Feature Available
#### Cloud Alerts Export Option Enhancement
You can select additional attributes to export for cloud alerts along with the alerts table to an Excel file and download the report.
[See image.](#export)
To learn more, see [About Alerts](/zpc/about-alerts) and [Downloading Reports](/zpc/downloading-reports).
[![Select the Alert attributes to export](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-export-cloud-alerts.png)
]

### Feature Available
#### Enhancements to IaC Scanning
The following enhancements are available for IaC Scanning:
View IaC Errors and Remediation in Code Repositories
ZPC performs IaC scans of templates in code repositories and displays the IaC errors and remediation steps within the code, allowing developers to investigate the issues immediately.
[See image.](#iac-remediation)
To learn more, see [About IaC Integrations](/zpc/about-iac-integrations).
IaC Scanning Support for Amazon Linux 2
ZPC provides support for IaC CI/CD scanning on Amazon Linux 2 operating systems.
To learn more, see [Supported OS Versions for IaC Scanning](/zpc/supported-os-versions-iac-scanning).
[![View the remediation procedure](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-iac-azure-remediation.png)
]

### Feature Available
#### Enhancements to Vulnerability Scanning
The following enhancements are available for Vulnerability Scanning:
Default Weekly Schedule for Vulnerability Scanning
The default scan schedule is set to weekly for cloud workloads. The scan schedule can be switched to daily if required.
[See image.](#weekly)
To learn more, see [Adding a Vulnerability Scanning Rule for Cloud Workloads](/zpc/adding-vulnerability-scanning-rule-cloud-workloads).
Detailed Error Messages for Failed Scans
Comprehensive error messages are displayed for failed vulnerability scans.
[See image.](#errormsg)
To learn more, see [Viewing the Cloud Workload Details](/zpc/viewing-cloud-workload-details).
[![Default scan schedule is weekly](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-vm-weeklyscan.png)
]
[![Error message for failed scans](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-vm-errormsg.png)
]

### Feature Available
#### Identity Type Classification Enhancement
ZPC aligns tightly with how each cloud service provider classifies identities as human and non-human. Each cloud service provider offers different best practices for managing human identities and workload identities and enable them to safely perform actions in your cloud deployment. ZPC can check for violations of these best practices across cloud service providers and generate alerts.
To learn more, see [Understanding Identity Types](/zpc/understanding-identity-types).

### Feature Available
#### Schedule an Executive Report
You can schedule executive reports for regular distribution to specified recipients at the specified frequency.
[See image.](#add)
To learn more, see [Scheduling Executive Reports](/zpc/scheduling-executive-report) and [Managing Scheduled Executive Reports](/zpc/managing-scheduled-executive-reports).
[![Add a Schedule Report](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-add-schedule-report.png)
]

### Feature Available
#### Security Policies
The following security policies are available for cloud service providers:
- [AWS](#aws-2-12-security-policy)
- [Microsoft Azure](#microsoft-azure-2-12-security-policy)
- [GCP](#gcp-2-12-security-policy)
- [Kubernetes](#kubernetes-2-12-security-policy)
- [OCI](#oci-2-12-security-policy)
To learn more, see [About Security Policies](/zpc/about-security-policies).
[]
Security Policy Title
Minimize user access to Amazon ECR
Abnormal Unused Permissions
[]
Security Policy Title
Ensure that Auto provisioning of 'Vulnerability assessment for machines' is Set to 'On'
Ensure that Auto provisioning of 'Microsoft Defender for Containers components' is Set to 'On'
Ensure That Microsoft Defender for IoT Hub Is Set To 'On'
Ensure that SKU Basic/Consumption is not used on artifacts that need to be monitored (Particularly for Production Workloads)
Ensure that Public IP addresses are Evaluated on a Periodic Basis
Ensure that ‘Enable Infrastructure Encryption’ for Each Storage Account in Azure Storage is Set to ‘enabled’
Ensure 'TLS Version' is set to 'TLSV1.2' for MySQL flexible Database Server
[]
Security Policy Title
Ensure the Latest Operating System Updates Are Installed On Your Virtual Machines in All Projects
Ensure 'Access Transparency' is 'Enabled'
Ensure Secrets are Not Stored in Cloud Functions Environment Variables by Using Secret Manager
Ensure Essential Contacts is Configured for Organization
[]
Security Policy Title
Manage Kubernetes RBAC users with AWS IAM Authenticator for Kubernetes or Upgrade to AWS CLI v1.16.156 or greater
Ensure clusters are created with Private Nodes
Ensure clusters are created with Private Endpoint Enabled and Public Access Disabled
[AKS CIS] Enable audit Logs
[GKE CIS] Ensure use of Binary Authorization
[GKE CIS] Ensure Legacy Authorization (ABAC) is Disabled
[GKE CIS] Ensure Stackdriver Kubernetes Logging and Monitoring is Enabled
[GKE CIS] Ensure clusters are created with Private Nodes
[GKE CIS] Ensure clusters are created with Private Endpoint Enabled and Public Access Disabled
[GKE CIS] Ensure Master Authorized Networks is Enabled
[GKE CIS] Ensure use of VPC-native clusters
[GKE CIS] Enable VPC Flow Logs and Intranode Visibility
[GKE CIS] Ensure Shielded GKE Nodes are Enabled
[GKE CIS] When creating New Clusters - Automate GKE version management using Release Channels
[GKE CIS] Ensure Kubernetes Secrets are encrypted using keys managed in Cloud KMS
[GKE CIS] Ensure Secure Boot for Shielded GKE Nodes is Enabled
[GKE CIS] Ensure Integrity Monitoring for Shielded GKE Nodes is Enabled
[GKE CIS] Ensure Node Auto-Upgrade is enabled for GKE nodes
[GKE CIS] Ensure Node Auto-Repair is enabled for GKE nodes
[GKE CIS] Ensure Container-Optimized OS (cos_containerd) is used for GKE node images
[GKE CIS] Ensure legacy Compute Engine instance metadata APIs are Disabled
[GKE CIS] Enable Customer-Managed Encryption Keys (CMEK) for GKE Persistent Disks (PD)
[GKE CIS] Ensure GKE clusters are not running using the Compute Engine default service account
[]
Security Policy Title
Ensure user auth tokens rotate within 90 days or less
Ensure user customer secret keys rotate within 90 days or less
Ensure user API keys rotate within 90 days or less

### Feature Available
#### System Notifications for Vulnerability Scan Errors
Information about vulnerability scan errors related to insufficient privileges or missing cloud resources are displayed on the Notification Center page in the ZPC Admin Portal.
[See image.](#system-notify)
To learn more, see [About System Notifications](/zpc/about-system-notifications).
[![View the notifications for vulnerability scanning](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-vm-notify.png)
]

## August 17, 2023
### Feature Available
#### Executive Reports
The Executive Report provides insight into the assets deployed in your cloud accounts, risks and vulnerabilities associated with the asset, policy violations and misconfigurations associated with the accounts, and much more. You can customize the report and share the report in PDF format.
[See image.](#executive-report)
To learn more, see [About the Executive Report](/zpc/about-executive-report) and [Managing Executive Reports](/zpc/managing-executive-reports).
[![View the Executive Report](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/executive-report.png)
]

### Feature Available
#### Ignore Filter Rule Enhancements
The following improvements are available for the Ignore filter:
- The Add Ignore filter action is now available by default to the Administrator and Security Operations (SecOps) role. All other ZPC users have view-only permission. You can enable the Add Ignore Filter action for other ZPC users by adding or modifying Ignore Rules permissions in Global Modules using custom roles.
- The Cloud Accounts attribute on the Filter Scope page is optional. You can select any one of the attributes on the Filter Scope page to define the filter.
[See image.](#filter-scope)
To learn more, see [Adding Ignore Filters](/zpc/adding-ignore-filters) and [Adding a Custom Role](/zpc/adding-custom-role).
[![View the Ignore Filter Scope page](/sites/default/files/downloads/zpc/adding-ignore-filters-draft/ignore-cloud-filter-scope.png)
]

### Feature Available
#### Improved Service Coverage
ZPC now offers security posture for the following services for cloud service providers:
- [Microsoft Azure](#microsoft-azure-2-11-services)
- [GCP](#gcp-2-11-services)
To learn more, see [About Cloud Asset Types and Asset Categories](/zpc/cloud-asset-types-and-asset-categories).
[]
Service Name
Microsoft.Security/assessments
Microsoft.Compute/virtualMachineScaleSets/virtualMachines
[]
Service Name
CloudBuild - WorkerPool
CloudBuild - Build
CloudBuild - Trigger
VertexAI - SpecialistPool
VertexAI - MetadataStore
VertexAI - Model
VertexAI - Dataset

### Feature Available
#### Investigation and Custom Policy Query Enhancements
ZPC supports the asset property predicate which offers the ability to investigate AWS assets based on any key-value pair in the asset metadata. ZPC accommodates for array, multiple, and partial value matching.
[See image.](#asset-property-predicate)
To learn more, see [Creating a New Investigation](/zpc/creating-new-investigation#asset-property-properties).
[]
![View the asset property predicate.](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2022/zpc-investigation-asset-property-release.png)

### Feature Available
#### New Remediation Attributes and Filters
Four new remediation attributes and filters are added to the Cloud Alerts table: Supports Remediation, Remediation Allowed, Remediation Status, and Remediation Initiated By. You can see these in the main Alerts table.
[See image.](#remediation-filters)
To learn more, see [About Alerts](/zpc/about-alerts) and [Using Filters](/zpc/using-filters).
[![View the Alerts page](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/remediation-filters-columns.png)
]

### Feature Available
#### Onboarding Private GKE Clusters
In addition to onboarding public and hybrid clusters, ZPC supports onboarding private GKE clusters. When onboarded, ZPC can collect configuration metadata and offer cloud posture insights.
To learn more, see [Onboarding a Private Google Kubernetes Engine Cluster](/zpc/onboarding-private-google-kubernetes-engine-cluster).

### Feature Available
#### Security Advisory Support for Vulnerability Scanning
Security advisories are notifications about significant new trends or developments related to threats impacting the information systems of an organization. These advisories are typically the early stages of common vulnerabilities and exposures (CVEs). ZPC scans your cloud assets and provides more information on detected security advisories along with accessible links to understand in detail about the threat methods and associated risks.
[See image.](#cvedetails)
To learn more, see [About Vulnerability Management](/zpc/about-vulnerability-management).
[![View the vulnerability details](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-vs-data1.png)
]

### Feature Available
#### Security Policies
The following security policies are available for cloud service providers:
- [Microsoft Azure](#microsoft-azure-2-11-security-policy)
- [Kubernetes](#kubernetes-2-11-security-policy)
To learn more, see [About Security Policies](/zpc/about-security-policies).
[]
Security Policy Title
Ensure an Azure Bastion Host Exists
Ensure that 'Enable key rotation reminders' is enabled for each Storage Account
Ensure That 'Firewalls & Networks' Is Limited to Use Selected Networks Instead of All Networks
Ensure server parameter 'audit_log_events' has 'CONNECTION' set for MySQL Database Server
Ensure server parameter 'audit_log_enabled' is set to 'ON' for MySQL Database Server
Ensure Azure Database for MariaDB servers enable encryption in transit
[]
Security Policy Title
Ensure that Service Account Tokens are only mounted where necessary for Statefulset
Ensure that Service Account Tokens are only mounted where necessary for DaemonSet
Ensure that Service Account Tokens are only mounted where necessary for CronJob
Ensure that Service Account Tokens are only mounted where necessary for Job
Ensure that Service Account Tokens are only mounted where necessary for Deployment
Ensure that Service Account Tokens are only mounted where necessary for Pod
Ensure that a limit is set on pod PIDs
Ensure that the RotateKubeletServerCertificate argument is set to true
Ensure that the --make-iptables-util-chains argument is set to true
Ensure that the --protect-kernel-defaults argument is set to true
Ensure that the --authorization-mode argument is not set to AlwaysAllow
Ensure that the --anonymous-auth argument is set to false

## July 31, 2023
### Feature Available
#### Improved RBAC Features
The role-based access control (RBAC) feature has undergone enhancements. ZPC now supports the ability for administrators to be part of multiple groups including single sign-on (SSO) groups. The concept of business units was earlier tightly coupled with defining roles, but now customers can define roles and business units separately. Business units are now mapped to groups.
Existing administrators need not make any changes, as all the roles and permissions are updated to the new model.
To learn more, see [About Administrators](/zpc/about-administrators), [About Groups](/zpc/about-groups), and [About Roles](/zpc/about-roles).

## July 12, 2023
### Feature Available
#### Admin's Last Login Details
ZPC provides additional information by displaying the last login time of each administrator on the Administrators page. The login time indicates the time they last logged in to the ZPC Admin Portal.
[See image.](#logintime)
To learn more, see [About Administrators](/zpc/about-administrators).
[![View the admin's last log in time](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-adminlogintime.png?1685441295)
]

### Feature Available
#### Alert Payload to Third-Party Integrations
Alerts sent from ZPC to the cloud storage service (Amazon S3, Azure Blob Storage, Splunk, or AWS Security Lake) are enhanced to include the following attributes: Audit Procedure, Remediation, and Resource Metadata.
[See image.](#alert-attrib)
To learn more, see [About Third-Party Integrations](/zpc/about-third-party-integrations) and [Adding Cloud Alert Rules](/zpc/adding-cloud-alert-rules).
[![Alert attributes](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-alert-attributes.png)
]

### Feature Available
#### API Improvements
Internal server errors return a correlation ID in an optional response header and the response body to support troubleshooting.
[See image.](#correlationId)
To learn more, see [API Response Codes and Error Messages](/zpc/api-response-codes-and-error-messages).
[]![Correlation ID in the response body of error 500](/sites/default/files/downloads/zpc/zpc-api/api-developer-reference-guide/working-apis/obtaining-alerts-using-api/zpc-correlationId.png)

### Feature Available
#### Cloud Identities Enhancements
The following enhancements are available for ZPC's Cloud Identities:
- The Cloud Identities page now offers complete metadata, power score, authentication methods, and open alert count.
- Clicking the open alert count directly opens the alert drawer showing all open alerts for a particular identity.
[See image.](#cloud-identities-release-image)
To learn more, see [About Cloud Identities](/zpc/about-cloud-identities).
[ ]
[![View the Identities page on ZPC.](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-identities-release-notes.png)
]

### Feature Available
#### Customized Default Filters
You can define a default filter to view customized data in the ZPC Admin Portal. You can also select a saved filter as the default filter. Default filters are retained so you can view customized data every time you revisit the page or when you log out and log back in to the ZPC Admin Portal.
To learn more, see [Using Filters](/zpc/using-filters).

### Feature Available
#### Improved Service Coverage
ZPC now offers security posture for the following services for cloud service providers:
- [AWS](#aws-2-10-services)
- [Microsoft Azure](#microsoft-azure-2-10-services)
- [GCP](#gcp-2-10-services)
- [OCI](#oci-2-10-services)
To learn more, see [About Cloud Asset Types and Asset Categories](/zpc/cloud-asset-types-and-asset-categories).
[]
Service Name
AWS::DocumentDB::DBCluster
AWS::Neptune::DBCluster
AWS::Neptune::DBInstance
AWS::GuardDuty::Detector
AWS::ServerlessRepo::Applications
Amazon SageMaker Ground Truth
AWS::WAF::IPSet
AWS::WAF::RuleGroup
AWS::WAFv2::IPSet
AWS::WAFRegional::Rule
AWS::WAFRegional::WebACL
AWS::WAFRegional::IPSet
AWS::WAFRegional::RuleGroup
[]
Service Name
Object Anchors
Microsoft Energy Data Services
Project Bonsai
Remote Rendering
Spatial Anchors
[]
Service Name
CertificateAuthorityService - CertificateRevocationList
CertificateAuthorityService - Certificate
CertificateAuthorityService - CaPool
CertificateAuthorityService - Certificate Authority
FileStoreInstance - Backup
Secret Manager - SecretVersion
[]
Service Name
OCI WAF
OCI Streaming
OCI Service Connector Hub
OCI Network Load Balance
OCI Logging Management
OCI File Storage
OCI Networking
OCI VNIC
OCI ONS Topic
OCI Event Rule

### Feature Available
#### Investigation and Custom Policy Query Enhancements
ZPC supports all cloud service provider supported tags in the investigation and custom policy query creator. You can use tag-based predicates for queries such as:
- Display all EC2 instances that do not contain specific mandatory tags.
- Set up an alert when an EC2 instance is running in production is detected with specific missing set of tags.
To learn more, see [Creating a New Investigation](/zpc/creating-new-investigation#build-query).

### Feature Available
#### Manual Remediation of AWS Alerts
ZPC supports manual remediation of AWS alerts. You can remediate single alerts, bulk alerts, or all alerts generated by a specific policy.
[See image.](#remediate-action)
To learn more, see [Remediating Alerts](/zpc/remediating-alerts).
[![View the Cloud Accounts Page](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-aws-alerts-remediation1.png)
]

### Feature Available
#### Security Policies
The following security policies are available for cloud service providers:
- [Microsoft Azure](#microsoft-azure-2-10-security-policy)
- [GCP](#gcp-2-10-security-policy)
- [Oracle Cloud Infrastructure](#oci-2-10-security-policy)
To learn more, see [About Security Policies](/zpc/about-security-policies).
[]
Security Policy Title
Ensure 'Infrastructure double encryption' for PostgreSQL Database Server is 'Enabled'
Ensure Application Gateway redirects HTTP traffic to HTTPS
Ensure Azure Database for MariaDB servers backups are 'Geo-Redundant'
Ensure Azure Database for PostgreSQL servers backups are 'Geo-Redundant'
Ensure that Activity Log Alert exists for Create or Update Public IP Address rule
Ensure that Activity Log Alert exists for Delete Public IP Address rule
Ensure Azure Database for MySQL servers backups are 'Geo-Redundant'
Ensure Azure Database for MySQL servers enable Infrastructure double encryption
Ensure That Microsoft Defender for Resource Manager Is Set To 'On'
Ensure That Microsoft Defender for Cosmos DB Is Set To 'On'
Ensure That Microsoft Defender for DNS Is Set To 'On'
Ensure That Microsoft Defender for Open-Source Relational Databases Is Set To 'On'
Ensure the "Minimum TLS version" for storage accounts is set to "Version 1.2"
Ensure that logging for Azure AppService 'HTTP logs' is enabled
Ensure Azure Monitor Log Profile is collecting all activity categories
[]
Security Policy Title
GCP Artifact Registry is running an image with critical vulnerabilities
Ensure Instance IP assignment is set to private
Internet facing virtual machine potentially exposes a vulnerable service to the internet
[]
Security Policy Title
Ensure a notification is configured for network security group changes
Ensure a notification is configured for user changes
Ensure a notification is configured for changes to network gateways
Ensure a notification is configured for VCN changes
Ensure a notification is configured for Identity Provider changes
Ensure a notification is configured for security list changes
Ensure a notification is configured for IdP group mapping changes
Ensure a notification is configured for IAM group changes
Ensure all OCI IAM user accounts have a valid and current email address
Ensure a notification is configured for IAM policy changes
Ensure a notification is configured for changes to route tables

### Feature Available
#### Slack Integration
Slack integration is available. You can receive ZPC alert notifications on Slack channels and streamline the mitigation directly into your developer tool.
[See image.](#r-slack)
To learn more, see [Integrating ZPC with Slack](/zpc/integrating-slack).
[![Add a Slack integration](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-slack.png)
]

### Feature Available
#### Vulnerability Scanning of AKS Containers
ZPC identifies all active images used by containers in monitored Azure Kubernetes Service (AKS) clusters and scans the images for vulnerabilities. Administrators can generate vulnerability reports for the findings, run investigation queries, and set custom policies based on CVE findings.
To learn more, see [About Vulnerability Scanning](/zpc/about-vulnerability-scanning).

## June 19, 2023
### Feature Available
#### Cloud Accounts Enhancements
The following enhancements are available for cloud accounts:
- Exporting cloud account details as an Excel file are now available with the following naming conventions:
- **Cloud Accounts**: Cloudaccounts_<timestamp>
- **Organizations**: Cloudaccounts_organizations_<timestamp>
- **Kubernetes**: Cloudaccount_kubernetes_<timestamp>
- The Cloud Accounts page displays a new column called Onboarded Date for each cloud account.
To learn more, see [About Cloud Accounts](/zpc/about-cloud-accounts).

### Feature Available
#### Container Workloads Investigation Enhancement
The following enhancements are available for Kubernetes workload investigation:
- ZPC supports additional predicates for investigation queries and custom policies over Kubernetes clusters. You can identify running containers as opposed to idle or stale ones and detect publicly exposed containers.
- Kubernetes container investigation results can now be exported as an Excel file.
To learn more, see [About Investigation](/zpc/about-investigation).

### Feature Available
#### Improved Service Coverage
ZPC now offers security posture for the following services for cloud service providers:
- [AWS](#aws-2-9-services)
- [Microsoft Azure](#microsoft-azure-2-9-services)
- [GCP](#gcp-2-9-services)
To learn more, see [About Cloud Asset Types and Asset Categories](/zpc/cloud-asset-types-and-asset-categories).
[]
Service Name
AWS Glue
AWS Personalize
AWS CodeArtifact
[]
Service Name
Azure Static Sites
Virtual WAN
Microsoft Genomics
Azure Media Services
Azure Maps
Azure Web PubSub
Azure Virtual Network Manager
Azure Video Indexer
Azure Time Series Insights
Azure Spring Apps
Azure Resource Mover
Azure Resource Manager templates
[]
Service Name
Compute Engine - VpnGateway
Network Intelligence Center - ConnectivityTest
Compute Engine - NodeGroup
NetworkConnectivity: Spoke
NetworkConnectivity: Hub
Run - Service
Compute - HealthCheck
Compute - InstanceTemplate
Compute Engine - Address
Compute Engine - Autoscaler

### Feature Available
#### Onboarding AKS clusters with Local Authentication
In addition to AKS clusters authenticated by Azure RBAC and Kubernetes RBAC, ZPC supports onboarding AKS clusters with local authentication.
To learn more, see [Onboarding AKS clusters with Local Authentication](/zpc/onboarding-aks-local-authentication).

### Feature Available
#### Security Policies
The following security policies are available for cloud service providers:
- [AWS](#aws-2-9-security-policy)
- [Microsoft Azure](#microsoft-azure-2-9-security-policy)
- [GCP](#gcp-2-9-security-policy)
- [Kubernetes](#kubernetes-2-9-security-policy)
To learn more, see [About Security Policies](/zpc/about-security-policies).
[]
Security Policy Title
High privileged identity with access keys
Amazon ECR is running an image with critical vulnerabilities
[]
Security Policy Title
Ensure private endpoints are used to access storage accounts
[]
Security Policy Title
High privileged identity with access keys
GCP Container Registry is running an image with critical vulnerabilities
[]
Security Policy Title
CIS EKS - Ensure Network Policy is Enabled and set as appropriate
CIS AKS - Ensure Network Policy is Enabled and set as appropriate
CIS GKE - Ensure Network Policy is Enabled and set as appropriate
Manage Kubernetes RBAC users with Azure AD
Ensure Kubernetes Secrets are encrypted
Verify that admission controllers are working as expected
Ensure clusters are created with Private Nodes
Prefer using secrets as files over secrets as environment variables [DEAMONSETS]
Prefer using secrets as files over secrets as environment variables [STATEFULSETS]
Prefer using secrets as files over secrets as environment variables [DEPLOYMENTS]
Prefer using secrets as files over secrets as environment variables [CRONJOBS]
Prefer using secrets as files over secrets as environment variables [JOBS]
Apply Security Context to Your Pods and Containers associated with STATEFULSETS
Apply Security Context to Your Pods and Containers associated with Deployments
Apply Security Context to Your Pods and Containers associated with CRONJOBS
Apply Security Context to Your Pods and Containers associated with JOBS

### Feature Available
#### Support for Amazon Security Lake Integration
ZPC continues to support the integration with Amazon Security Lake with appropriate adjustments to align with the formal GA release that Amazon published.
To learn more, see [Integrating with Amazon Security Lake](/zpc/integrating-amazon-security-lake).

### Feature Available
#### Support for Scanning Azure Workload Images Created in Compute Gallery
ZPC now provides support for scanning cloud workload images created in Azure Compute Gallery. Previously, ZPC provided support only for scanning workload images in the Azure Marketplace.
To learn more, see [Integrating Vulnerability Management for Microsoft Azure Workloads](/zpc/integrating-vulnerability-management-microsoft-azure-workloads).

### Feature Available
#### View Container Status in Vulnerability Management
You can easily differentiate between active and non-active containers. ZPC displays the status of the containers in the Containers tab on the Vulnerability Management page. You can also apply the Running Status filter to view either the active or non-active containers.
[See image.](#cont-status)
To learn more, see [Viewing the Containers Tab](/zpc/viewing-containers-tab).
[![View the container status](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-vm-runningstatus-container.png)
]

### Feature Available
#### View Publicly Exposed Cloud Workloads on the Vulnerability Management Page
You can view the list of cloud workloads that are publicly exposed on the Vulnerability Management page. You can also apply the filter to see the list of publicly exposed workloads. This allows you to prioritize these workloads and fix the vulnerabilities.
[See image.](#publicworkloads)
The Vulnerability Dashboard for cloud workloads shows the summary of the top publicly exposed cloud workloads with vulnerabilities.
[See image.](#dashboard-exposedworkloads)
To learn more, see [Viewing the Cloud Workloads Tab](/zpc/viewing-cloud-workloads-tab) and [About the Vulnerability Dashboard](/zpc/about-vulnerability-dashboard).
[![View publicly exposed cloud workloads](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-vm-publicexposure.png)
]
[![Publicly exposed cloud workloads](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-dashboard-publicworkloads.png)
]

### Feature Available
#### View Redundant Packages and Versions
ZPC detects vulnerabilities in the same package and version that is located in different locations. You can view the file path of packages and take the necessary action.
[See image.](#packagepath)
To learn more, see [Viewing the Cloud Workload Details](/zpc/viewing-cloud-workload-details).
[![View the package file path](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-vm-workloadinstance-packagepath.png)
]

### Feature Available
#### View Repository Details of Scanned Container Images
You can view the repository details of the image that is scanned for vulnerabilities. Knowing the repository in which the image resides allows you to easily locate the image and fix vulnerabilities.
[See image.](#repo-name)
To learn more, see [Viewing the Container Details](/zpc/viewing-container-details).
[![View the container repository details](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-vm-containerreponame.png)
]

### Feature Available
#### Vulnerability Detection on Ubuntu
ZPC supports the detection of vulnerabilities present in cloud workloads having Ubuntu 23.04 (Lunar Lobster) OS version.
[See image.](#ubuntu)
To learn more, see [About Vulnerability Management](/zpc/about-vulnerability-management).
[![Support for Ubuntu workloads](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-vs-ubuntu.png)
]

### Feature Available
#### Vulnerability Scanning of GKE Containers
ZPC identifies all active images used by containers in monitored Google Kubernetes Engine (GKE) clusters and scans the images for vulnerabilities. Administrators can get vulnerability reports for the findings, run investigation queries, and set custom policies based on the common vulnerability and exposure (CVE) findings.
To learn more, see [Adding a Vulnerability Scanning Rule for Containers](/zpc/adding-vulnerability-scanning-rule-containers).

### Feature Available
#### ZPC API
ZPC supports REST APIs that allow for code-based alert retrieval. API access requires an API key, which you can create and manage in the ZPC Admin Portal. API key management entails updates to RBAC, expiration handling, and deletion of API keys.
[See image.](#apiKeysPage)
To learn more, see [Understanding ZPC API](/zpc/understanding-zpc-api), [Getting Started](/zpc/getting-started-zpc-api), and [About API Key Management](/zpc/about-api-key-management).
[]![Viewing the API Keys page in the ZPC Admin Portal](/sites/default/files/downloads/zpc-api-keys-page.png)

### Feature in Limited Availability
#### Oracle Cloud Infrastructure (OCI) Support
ZPC extends its public cloud support with coverage for OCI services:
- Onboard your OCI cloud accounts on ZPC.
- Gain visibility of your OCI infrastructure's security posture on the Cloud Asset Inventory.
To learn more, see [Onboarding an Oracle Cloud Infrastructure (OCI) Tenant](/zpc/onboarding-oracle-cloud-infrastructure-oci-tenant).

## May 17, 2023
### Feature Available
#### Alert Payload with Additional Attributes Sent to Cloud Storage Services
Cloud and IaC alert payloads that are sent from ZPC to cloud storage services (AWS S3, Azure Blob, and AWS Security Lake) are enhanced to include additional attributes: Audit Procedure and Remediation.
[See image.](#attrib)
To learn more, see [About Alert Rules](/zpc/about-alert-rules), [Adding Cloud Alert Rules](/zpc/adding-cloud-alert-rules), and [Adding IaC Alert Rules](/zpc/adding-iac-alert-rules).
[![Select additional attributes for cloud storage](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-iacalert-notification.png)
]

### Feature Available
#### Container Workloads Investigation
ZPC introduces you to container workloads investigation by offering you to investigate Kubernetes workloads and gain insight into your container workload security posture without creating alerts or filtering dashboards. You can create investigations based on Kubernetes asset properties and images used by AWS EKS workloads.
[See image.](#investigate-container-workloads)
To learn more, see [About Investigation](/zpc/about-investigation).
[]
![View the Investigation page on ZPC.](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-investigate-kubernetes.png)

### Feature Available
#### Enhanced Cloud Account Filter
The common filter Accounts now displays both the cloud account name and cloud account ID.
[See image.](#enhanced-cloud-account-filter)
To learn more, see [Using Filters](/zpc/using-filters).
[]
![View the accounts filter on ZPC.](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-cloud-account-filter-enhancement.png)

### Feature Available
#### Generate Excel Copy for Security Policy Catalog
You can export the security policy catalog to an Excel file from the Policies page on the ZPC Admin Portal.
[See image.](#view-policy-catalog-export)
To learn more, see [About Security Policies](/zpc/about-security-policies).
[]
![View the export policy catalog option on ZPC.](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-export-policy-catalog.png)

### Feature Available
#### Ignore Filters Based on Clusters and Namespaces
Alert Ignore filters can now filter on Kubernetes clusters and namespaces.
[See image.](#kubernetes-ignore-filter)
To learn more, see [Adding Ignore Filters](/zpc/adding-ignore-filters).
[![Kubernetes Ignore Filter](/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-ignore-cloud-alert.png)
]

### Feature Available
#### Improved Service Coverage
ZPC now offers security posture for the following services for cloud service providers:
- [AWS](#aws-2-8)
- [Microsoft Azure](#microsoft-azure-2-8)
- [GCP](#gcp-2-8)
To learn more, see [About Cloud Asset Types and Asset Categories](/zpc/cloud-asset-types-and-asset-categories).
[]
Service Name
S3 Glacier
Amazon Connect
IoT SiteWise
AWS IoT Events
AWS IoT Core
AWS IoT Analytics
AWS AppFlow
AWS Trusted Advisor
AWS Backup
AWS SageMaker
[]
Service Name
Azure Red Hat OpenShift Cluster
Azure Private Link
Azure Kubernetes Fleet Manager
Azure Deployment Environments
Azure Digital Twins
Azure Confidential Ledger
Azure Communication Services
Azure Cognitice Search
Azure Virtual Machine Extensions
Azure Automation Account Runbook
Azure Resource Manager Templates
Policy Definition
Smart Alert Rules
Azure Server Farms
Azure SQL Virtual Mahcine
Azure Network Watcher
Azure Private Link
Azure Devtest Lab Schedules
Azure DNS
Azure Files
[]
Service Name
DataMigration - Migration Job
DataMigration - Connection Profile
Dataplex - Zone
Healthcare - Dataset
Datastream - Stream
Datastream - Connection Profile
Dataplex - Lake
Dataplex - Assets
Cloud Scheduler - Jobs
Cloud CDN - Backend Bucket

### Feature Available
#### Public Exposure Details for Assets
Assets that are publicly exposed carry higher risk. ZPC now shares a visual indication for publicly exposed assets in the Assets drawer and the Assets table, and includes a filter to search for such assets.
[See image.](#public-exposure-asset)
To learn more, see [About Cloud Asset Type Details](/zpc/about-cloud-asset-type-details) and [Using Filters](/zpc/using-filters).
[![Public Exposure Asset Column](/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-public-exposure-asset-table.png)
]

### Feature Available
#### Scanning Google Artifact Registry for CVEs
ZPC provides support for scanning container images stored in the Google Artifact Registry (GAR). This is in addition to the previous support for scanning container images in the Google Container Registry (GCR).
GCR is expected to be deprecated in the near future and GAR is going to be the default registry for container images and packages.
To learn more, see [Integrating Vulnerability Management for Google Cloud Platform Accounts](/zpc/integrating-vulnerability-management-google-cloud-platform-accounts).

### Feature Available
#### Security Policies
The following security policies are available for cloud service providers:
- [AWS](#security-policy-aws-2-8)
- [Microsoft Azure](#security-policy-microsoft-azure-2-8)
- [GCP](#security-policy-gcp-2-8)
To learn more, see [About Security Policies](/zpc/about-security-policies).
[]
Security Policy Title
EC2 Instance contains sensitive data
EC2 Instance is running an image with critical vulnerabilities
Ensure Amazon EFS file systems data is encrypted with KMS Customer Managed Keys (CMKs)
Ensure Auto Renew is enabled for Route 53 domain
Ensure Classic Load Balancer's listeners use secure protocols
Ensure DNSSEC signing is enabled for Route 53 hosted zone
Ensure Load Balancer's listeners use secure protocols
Ensure Privacy Protection is enabled for Route 53 domain
Ensure RDS DB clusters 'auto minor version upgrade' is set to 'Enabled'
Ensure RDS DB clusters 'deletion protection' is set to 'Enabled'
Ensure RDS DB clusters encryption is set to 'Enabled'
Ensure RDS DB instance automated backup feature is enabled
Ensure RDS DB instances 'auto minor version upgrade' is set to 'Enabled'
Ensure RDS DB instances 'deletion protection' is set to 'Enabled'
Ensure RDS DB instances are encrypted with KMS Customer Managed Keys (CMKs)
Ensure RDS DB instances encryption is set to 'Enabled'
Ensure SNS topica server-side encryption at rest use an up to date key
Ensure Transfer Lock is enabled for Route 53 domain
Ensure access logs are enabled for Classic Load Balancer
Ensure access logs are enabled for Load Balancer
Ensure query logging is enabled for Route 53 hosted zone
External account can access EC2 instance contains sensitive data
Publicly exposed EC2 instance contains sensitive data
RDS Snapshot is shared with an external account
Route 53 domain has expired
Route 53 domain is about to expire in 30 days or less
User without MFA can access EC2 instance that contains sensitive data
Vulnerable publicly exposed EC2 instance contains sensitive data
[]
Security Policy Title
Ensure Application Gateway uses WAF
Ensure Azure API Management APIs uses HTTPS rather than HTTP
Ensure Azure SQL servers are encrypted with customer-managed keys
Ensure Azure SQL servers are not publicly accessible
Ensure access logs are enabled for Application Gateway
Ensure audit logging is enabled for Azure SQL servers
Ensure firewall logs are enabled for Application Gateway
Ensure private endpoint is configured for Azure Key Vault Vaults
Ensure transparent data encryption is enabled for Azure SQL databases
Function application with a risky role combination is open to the internet
Old Credentials for Privileged Service Principal
Old Credentials for Service Principal
Ensure that the Expiration Date is set for all Secrets in Non-RBAC Key Vaults
Ensure that the Expiration Date is set for all Keys in Non-RBAC Key Vault
Ensure that 'Enable infrastructure encryption' for each Storage Accounts in Azure Storage is set to 'Enabled'
Ensure that the Expiration Date is set for all Keys in RBAC Key Vaults
Ensure that the Expiration Date is set for all Secrets in RBAC Key Vaults
[]
Security Policy Title
Ensure that Cloud Storage bucket is not anonymously or publicly accessible
Critical virtual machine instance allows login with project level SSH keys enabled
Ensure HTTP/S Load Balancer uses HTTPS rather than HTTP
Ensure cloud functions do not have admin privileges
Ensure logging is enabled for HTTP/S Load Balancing backend services
Ensure to use Cloud Armor security policies for HTTP/S Load Balancing backend services
Identity without MFA can elevate privileges by delegating as service accounts
Non-human identity can create keys for service accounts
Virtual machine instance with access to stale data snapshots is exposed to the public internet

### Feature Available
#### System Notifications
ZPC supports system notifications that provide information about any possible errors or failures related to configurations or functionality in your cloud infrastructure. Currently, ZPC displays system notifications for cloud account onboarding and data collection failures. These notifications allow you to easily track and resolve the issues immediately.
[See image.](#notificationpage)
To learn more, see [About System Notifications](/zpc/about-system-notifications).
[![Notification Center page](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-notificationcenter.png)
]

### Feature Available
#### Vulnerability Detection in Microsoft Packages
ZPC supports the detection of vulnerabilities in some of the Microsoft packages such as .NET Framework, .NET Core Runtime, .NET Runtime, ASP .NET, Visual Studio, PowerShell, and SQL Server Management Studio.
To learn more, see [About Vulnerability Management](/zpc/about-vulnerability-management).

## April 19, 2023
### Feature Available
#### Cloud Account Onboarding Enhancements
The Cloud Accounts page offers visibility into onboarding and configuration metadata collection status. Administrators can view configuration metadata issues and possible solutions.
To learn more, see [About Cloud Accounts](/zpc/about-cloud-accounts).

### Feature Available
#### Dashboard for Container CVE Scans
ZPC already provides support for the CVE scanning of Amazon Elastic Kubernetes Service (EKS) containers. You can now view a detailed dashboard of the container vulnerabilities that ZPC discovered in monitored EKS deployments. Use the filters to view vulnerabilities related to specific Kubernetes clusters.
[See image.](#cdashboard)
To learn more, see [About the Vulnerability Dashboard](/zpc/about-vulnerability-dashboard).
[![View the container dashboard](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-containerdashboard.png?1680755401)
]

### Feature Available
#### Enhanced Asset Misconfiguration Detection
EC2 instances connected to a subnet with a default subnet-ACL and a public ID were not detected as publicly exposed. This is now corrected and as a result, a higher number of publicly exposed instances may be observed.
To learn more, see [About Cloud Assets](/zpc/about-cloud-assets) and [About Alerts](/zpc/about-alerts).

### Feature Available
#### IaC Support for Bitbucket
ZPC provides support for scanning IaC files in the Bitbucket repositories. You can use Zscaler IaC Scan to scan the IaC files, view the scan results in Bitbucket, and view alerts for IaC policy violations in the ZPC Admin Portal.
[See image.](#bitbucket)
To learn more, see [Configuring IaC Scan for Bitbucket](/zpc/configuring-iac-scan-bitbucket).
[![IaC scan support for Bitbucket](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-bitbucket.png)
]

### Feature Available
#### Improved Service Coverage
ZPC now offers security posture for the following services for cloud service providers:
- [AWS](#aws-2-7)
- [Microsoft Azure](#microsoft-azure-2-7)
- [GCP](#gcp-2-7)
To learn more, see [About Cloud Asset Types and Asset Categories](/zpc/cloud-asset-types-and-asset-categories).
[]
Service Name
Route 53
AWS Batch
AWS CodeDeploy
AWS Step Functions
AWS SimSpace Weaver
AWS Serverless Application Repository
Amazon MemoryDB for Redis
AWS CodeBuild
Amazon Inspector
EC2 Networking - Transit Gateways, VPC Peering and VPNs
AWS Athena
AWS Elastic Beanstalk
AWS Fargate
Datalake GEN2
Amazon Kinesis
AWS DocumentDB
[]
Service Name
Azure Fluid Relay
Azure Managed Instance for Apache Cassandra
Azure Route Server
Azure Database Migration Service
Azure IoT Central
Azure Data Explorer
Azure Health Data Services
Azure Managed Grafana
Azure Chaos Studio
Container Apps
Azure HPC Cache
Azure Health Bot
Azure Load Testing
Azure Cloud Services (classic)
Azure Batch
Azure Quantum
Azure Internet Analyzer
Azure Firewall Manager
Azure Blueprints
Azure Analysis Services
Datalake GEN2
[]
Service Name
ApiGateway Gateway
App Engine
Cloud Functions
Cloud Tasks - Queue
Cloud Tasks - Tasks
Filestore - Snapshot
Filestore - Instance
ApiGateway API Config
Logging LogBucket
Cloud Tasks Queue
Cloud TPU Node
DataFusion Instance

### Feature Available
#### Kubernetes Support Enhancement
ZPC offers improved Kubernetes support:
- ZPC collects configuration metadata and offers security posture for K8S IAM entities such as roles, role bindings, and service accounts allowing you visibility into the Kubernetes cluster RBAC.
- ZPC collects configuration metadata for Kubelet configurations.
- ZPC closes previously generated alerts for offboarded Kubernetes clusters.
- ZPC offers insight into Kubernetes metadata collection. ZPC displays a new status called Warning when it's unable to collect configuration metadata for certain services.
- ZPC collects configuration metadata only user-generated jobs.
To learn more, see [About Cloud Accounts](/zpc/about-cloud-accounts#kubernetes).

### Feature Available
#### New Tags Tab in Alerts Drawer
A Tags tab is available in the Alerts drawer. The Tags tab gives quick access to the asset or identity tags that triggered the alert.
[See image.](#alert-drawer-tags-tab)
To learn more, see [Viewing the Cloud Alert Details](/zpc/viewing-cloud-alert-details).
[![Alert Drawer Tags Tab](/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-alerts-drawer-tags-tab.png)
]

### Feature Available
#### Package Displayed by Vulnerability Severity
The Asset Vulnerability tab is updated to display packages in ascending order of vulnerabilities, with the highest CVEs count based on severity first.
To learn more, see [About Cloud Asset Details](/zpc/about-cloud-asset-details).

### Feature Available
#### Policy Focus Option Added in Create Ignore Filter
When creating an Ignore filter, you can select Policy Focus under the Policies dropdown on the Filter Scope screen. The Policy Focus option selects if the Ignore filter focuses on assets, identities, or both.
[See image.](#ignore-filter-policy-focus)
To learn more, see [Adding Ignore Filters](/zpc/adding-ignore-filters).
[![Ignore Filter Policy Focus](/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-ignore-filter-policy-focus.png)
]

### Feature Available
#### Remediation Recommendation in JetBrains IDE
You can now view the remediation steps within the JetBrains IDE for policy violations detected in the IaC templates.
[See image.](#jetbrainsremediation)
To learn more, see [Configuring IaC Scan for JetBrains IDEs](/zpc/configuring-iac-scan-jetbrains-ides).
[![View the remediation steps](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-jetbrains-remediation.png)
]

### Feature Available
#### Revamped Scanning Rules Workflow for Containers and Cloud Workloads
The vulnerability scanning rules for cloud workloads and containers are consolidated under a single tile to simplify the process for creating vulnerability scan rules.
[See image. ](#singletile)
To learn more, see [Adding a Vulnerability Scanning Rule for Cloud Workloads](/zpc/adding-vulnerability-scanning-rule-cloud-workloads) and [Adding a Vulnerability Scanning Rule for Containers](/zpc/adding-vulnerability-scanning-rule-containers).
[![Cloud workloads and containers under one tile](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-vm-wrkloadcontainers.png)
]

### Feature Available
#### Security Policies
The following security policies are added for cloud service providers:
- [AWS](#aws-2-7-policy)
- [Microsoft Azure](#microsoft-azure-2-7-policy)
- [GCP](#gcp-2-7-policy)
- [Kubernetes](#kubernetes-2-7-policy)
To learn more, see [About Security Policies](/zpc/about-security-policies).
[]
Security Policy Title
EC2 Instance is running an image with critical vulnerabilities
Ensure that ElastiCache cluster with Replication Group is not listening on the default port
Ensure that encryption at rest is enabled for ElastiCache Redis cluster with Replication Group
Ensure Amazon Redshift databases are not using the default port
Ensure Amazon Redshift clusters are created within a VPC
Ensure Amazon Redshift clusters 'cross-region snapshot' feature is set to 'Enabled'
Ensure Amazon Redshift clusters are encrypted with KMS Customer Managed Keys (CMKs)
Ensure RDS DB clusters are encrypted with KMS Customer Managed Keys (CMKs)
Ensure RDS DB clusters are not deployed with the default port
Ensure RDS DB instances are not deployed with the default port
Ensure RDS DB clusters IAM database authentication is set to 'Enabled'
AWS - Ensure RDS DB instances IAM database authentication is set to 'Enabled'
Ensure RDS DB instances are deployed as Multi-AZ
Ensure RDS DB clusters 'Log exports' feature is configured
Ensure RDS DB instances 'Log exports' feature is configured
Ensure RDS DB clusters 'copy tags to snapshots' feature is set to 'Enabled'
Ensure RDS DB instances 'copy tags to snapshots' feature is set to 'Enabled'
Ensure Aurora DBs clusters encryption is set to 'Enabled'
Ensure Aurora DBs 'log exports' feature is set to 'Enabled'.
Ensure Aurora DB clusters 'copy tags to snapshots' feature is set to 'Enabled'.
Ensure Aurora 'deletion protection' feature is set to 'Enabled'
Ensure SNS delivery status logging is enabled
Ensure SNS topic server-side encryption at rest is enabled
Ensure that SNS topic does not allow everyone to publish to the SNS topic
Ensure that SNS topic does not allow everyone to subscribe to the SNS topic
Ensure Classic Load Balancer's Desync mitigation mode is not set to 'Monitor'
Ensure Application Load Balancer's Desync mitigation mode is not set to 'Monitor'.
Ensure Application Load Balancer redirects HTTP traffic to HTTPS.
Ensure CloudFront distribution uses at least one kind of logs
Ensure CloudFront distribution standard logging is enabled
Ensure CloudFront distribution realtime logging is enabled
Internet facing EC2 instance can elevate to Admin using ec2-instance-connect
[]
Security Policy Title
Virtual machines with powerful identity
Ensure that no custom subscription owner roles are created
Ensure Custom Role is assigned for Administering Resource Locks
Function App with power identity is open to the internet
Power identity without MFA
Internet facing virtual machine potentially exposes a vulnerable service to the internet
Internet facing virtual machine attached with a powerful managed identity and is running an image with critical vulnerabilities
Internet facing virtual machine attached with a managed identity is running an image with critical vulnerabilities
Internet facing virtual machine attached with a powerful managed identity is running a vulnerable image
Internet facing virtual machine attached with a managed identity is running a vulnerable image
Virtual machine Instance is running an image with critical vulnerabilities
Virtual Machine with privileged role assignment is open to the internet
Function App with privileged role assignment is open to the internet
Function application with a risky role combination is open to the internet
Service principal with credentials can access unattached disk from the internet
Virtual machine with a risky role combination is open to the internet
[]
Security Policy Title
New External Keys for privileged service account that already has external keys
Non-human identity can create keys for service accounts
[]
Security Policy Title
Apply Security Context to Your Pods and Containers associated with Deployments

### Feature Available
#### Updated Filters for Alerts
The following cloud and IaC alert filters are available:
- Policy Name
- Policy ID
- Theme
- Threat Category
- MITRE ATT&CK
- Cloud Account ID
- Cloud Account Name
- Focus
To learn more, see [Using Filters](/zpc/using-filters).

### Feature Available
#### Vulnerability Scanning Support for Amazon Linux Versions
ZPC provides vulnerability scanning support for Amazon Linux 2022 and Amazon Linux 2023 versions.
To learn more, see [Supported OS and Application Packages for Vulnerability Scanning](/zpc/supported-operating-systems-and-application-packages-vulnerability-scanning).

## March 23, 2023
### Feature Available
#### Enhanced Search Functionality
The search option across all tables and pages in the ZPC Admin Portal is enhanced for improved usability.
You can see the following improvements:
- The list of columns that can be searched for.
- The column headings in tables are highlighted for better visualization.
- The search functionality detects all items containing the search strings and displays the results in the table.
For example, the following image shows the searchable columns on the Business Units Management page.
[See image.](#search-columns)
[![Searchable columns](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-searchfields-rn.png?1678865348)
]

### Feature Available
#### IaC Support for JetBrains IDEs
You can install the Zscaler IaC Scan plugin on the JetBrains Integrated Development Environments (IDEs) and scan IaC templates. You can scan individual files and directories for misconfigurations.
[See image.](#ides)
To learn more, see [Configuring IaC Scan for JetBrains IDEs](/zpc/configuring-iac-scan-jetbrains-ides).
[![IntelliJ IDE](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-ides.png?1678427439)
]

### Feature Available
#### Improved Date and Time Formats
The date and time formats are now adjusted and displayed using the format that the user has selected for their browser or operating system (OS). For example, the following image shows the date and time format on the Audit Logs page.
[See image. ](#date-timeformat)
[![Date and time format based on browser locale](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-timeformat-rn.png)
]

### Feature Available
#### Kubernetes Support Enhancement
ZPC now supports Microsoft Azure Kubernetes Service (AKS) clusters. You can onboard Microsoft Azure AKS clusters and gain insight into their security posture via the asset inventory.
[See image.](#aks-select-cluster)
To learn more, see [Onboarding an Azure Kubernetes Service Cluster](/zpc/onboarding-azure-kubernetes-service-cluster).
[]
![View the AKS clusters on ZPC.](/sites/default/files/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-azure-kubernetes-service-cluster/zpc-aks-add-cluster.png)

### Feature Available
#### New Alert Age Filter
An Alert Age filter was added to the alert filter capabilities for more granularity and flexibility. The Alert Age allows you to filter based on the Alert Age attribute. By selecting Alert Age from the additional Alert Filter options, you can filter alerts by exact age, alerts older than a specific age, and alerts newer than a specific age. All ages are measured in days.
[See image.](#zpc-alert-age-filter)
To learn more, see [Using Filters](/zpc/using-filters).
[![Alert Age Filter](/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-alert-age-filter.png)
]

### Feature Available
#### New Alert Attributes
Four new alert attributes are added to the Cloud Alerts table: Cluster Name, Cluster Type, Namespaces, and Associated Cloud. Users can see these in the main Alerts table and the Alert Details Drawer.
You can also search for these alerts using the Alerts Filters.
[See image.](#new-alert-filters)
To learn more, see [About Alerts](/zpc/about-alerts).
[![New Alert Filters](/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-new-alert-filters.png)
]

### Feature Available
#### Security Policies
The following security policies are available for cloud service providers:
- [AWS](#aws-2-6)
- [Microsoft Azure](#microsoft-azure-2-6)
- [GCP](#gcp-2-6)
- [Kubernetes](#kubernetes-2-6)
To learn more, see [About Security Policies](/zpc/about-security-policies).
[]
Security Policy Title
Internet-facing Lambda function can manage users and permissions
Internet-facing Lambda function without WAF protection
Instance accepts inbound internet traffic
Role can be assumed by anyone
Ensure that SNS topic does not allow everyone to subscribe to the SNS topic
Ensure ElastiCache cluster is not listening on the default port
Ensure Amazon Redshift clusters are not publicly accessible
Internet facing EC2 instance with role is running vulnerable image
Internet facing EC2 instance with role is running a vulnerable image and enables IMDVs1
Internet facing EC2 instance with a powerful role is running a vulnerable image and enables IMDVs1
Internet facing EC2 instance with a role is running an image with critical vulnerabilities and enables IMDVs1
Internet facing EC2 instance has a powerful role and is running an image with critical vulnerabilities and enables IMDVs1
Block-public-access control not enforced on private bucket
Internet-facing Lambda function with admin privileges requires no authentication
Internet facing Lambda function with privilege escalation risk with ec2 connect
Internet-facing Lambda function with privilege escalation risk using PassRole action
Internet facing EC2 instance can elevate to Admin using ec2-instance-connect
Lambda Function With Anonymous URL Access is privileged
EC2 Instance is running a vulnerable image
Internet facing EC2 instance potentially exposes a vulnerable service to the internet
Ensure ElastiCache cluster encryption in transit is enabled
Ensure ElastiCache Redis cluster encryption at rest is enabled
Ensure that encryption in transit is enabled for Redis ElastiCache cluster with Replication Group
Ensure Amazon Redshift clusters enable encryption in transit
Ensure Amazon Redshift clusters 'enhanced vpc routing' feature is set to 'Enabled'
Ensure Amazon Redshift clusters 'automated snapshot' feature is set to 'Enabled'
Ensure DynamoDB tables stream is set to 'Enabled'
Ensure DynamoDB tables are encrypted with KMS Customer Managed Keys
[]
Security Policy Title
Ensure RBAC is configured for data plane access control in Azure Key Vault vaults
Ensure private endpoint is configured for Azure Key Vault vaults
Ensure public access is disabled for Azure Key Vault vaults
Function app with power identity is open to the internet
Ensure Purge Protection is enabled for Azure Key Vault vaults
Power identity without MFA
Instance is open to all ports and all IP ranges
Virtual Machine accepts inbound internet traffic
Ensure that the Expiration Date is set for all Secrets in Non-RBAC Key Vaults
Ensure the storage account containing the container with activity logs is encrypted with BYOK
Ensure RBAC is configured for data plane access control in Azure Key Vault vaults
[]
Security Policy Title
Ensure that Separation of duties is enforced while assigning service account related roles to users
Ensure that IAM users are not assigned the Service Account User or Service Account Token Creator roles at project level
Ensure that Service Account has no Admin privileges
Ensure that Separation of duties is enforced while assigning KMS related roles to users
[]
Security Policy Title
Ensure Kubernetes Secrets are encrypted using Customer Master Keys (CMKs) managed in AWS KMS
Restrict Access to the Control Plane Endpoint
Enable audit logs

### Feature Available
#### Vulnerability Scanning of Containers in Amazon EKS Clusters
ZPC supports the scanning of containers deployed to Amazon Elastic Kubernetes Service (EKS) clusters. ZPC identifies all active images used by containers in monitored Kubernetes clusters and scans the images present in elastic container registries (ECR) for vulnerabilities. You can view and download reports, run investigation queries, and set custom policies based on the common vulnerabilities and exposure (CVE) findings.
[See image.](#cont-tab)
To learn more, see [About Vulnerability Management](/zpc/about-vulnerability-management).
Vulnerability Scanning Rule for Containers
You can configure vulnerability scanning rules and schedule the scan to run at regular intervals to detect vulnerabilities in container images within the production environment.
[See image.](#cimages)
To learn more, see [Adding a Vulnerability Scanning Rule for Containers](/zpc/adding-vulnerability-scanning-rule-containers).
[![View the Container tab ](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-containertab-rn.png)
]
[![Add a scan rule for container images](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-vs.png?1678428668)
]

## March 01, 2023
### Feature Available
#### Alert Age Attribute
A new Alert Age attribute was added to the alert data. The Alert Age is the number of days since the last time the Alert Status was set to Open.
[See image.](#alert-age)
To learn more, see [About Alerts](/zpc/about-alerts).
[![View the Alert Age](/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-alert-age.png)
]

### Feature Available
#### Cloud Account Management
ZPC now supports changing business units for multiple cloud accounts.
[See image.](#view-change-business-units)
To learn more, see [Managing Cloud Accounts](/zpc/managing-cloud-accounts).
[]
![View the change business unit option for cloud accounts.](/sites/default/files/downloads/zpc/administration/cloud-accounts/about-cloud-accounts/zpc-change-bu-button.png)

### Feature Available
#### Generate Excel Report for Asset Package Inventory
You can export asset package data to an Excel file from the Vulnerabilties tab of the Asset drawer.
[See image.](#export-package-vulnerabilities)
To learn more, see [About Cloud Asset Details](/zpc/about-cloud-asset-details).
[![Export Package Vulnerabilities](/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-vulnerabilities-tab-2.png)
]

### Feature Available
#### Identity Classification Algorithm Enhancement
The ZPC proprietary ML algorithm can now determine cloud identity types as human or non-human with more precision.
To learn more, see [About Identity Types](/zpc/about-identity-types).

### Feature Available
#### New Time Filters for Alerts
The alert time range filter capabilities are modified and expanded for more granularity and flexibility:
- Cloud alerts have two time range filters: Created Date and Updated Date.
[See image.](#cloud-alert-time)
[ ]
- IaC alerts have three time range filters: Scan Time, Created Date, and Update Date.
[ ]
[See image.](#iac-alert-time)
The Created Date is the first time the misconfiguration is identified on the customer's public cloud. The Update Date is either the most recent occurrence of the misconfiguration or the latest action performed by the ZPC admin on this alert. The Scan Date is the last time the alert was set to open.
The change allows for filtering on the entire alert lifecycle (in which alerts can close and reopen).
To learn more, see [Using Filters](/zpc/using-filters).
[![Cloud Alert Time Filters](/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-alert-time.png)
]
[![IaC Alert Time Filters](/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-iac-time.png)
]

### Feature Available
#### Policy Catalog Enhancement
You can now enable or disable a security policy from the policy catalog table. When disabled, the policy is not run against the collected configuration metadata.
[See image.](#view-actions-state-policy-catalog)
To learn more, see [About Security Policies](/zpc/about-security-policies).
[]
![View the policy catalog table.](/sites/default/files/downloads/zpc/policies/about-security-policies/zpc-enable-disable-policies.png)

### Feature Available
#### Query Predicate Enhancement
ZPC now supports the following query predicates to be entered via text along with selecting from the available drop-down menu:
- Asset Name
- Asset ID
- Asset Type
- Identity Name
- Identity ID
- Permission Set Name
- Allowed Action
- Permission Set Type
- Group Membership
- Account ID
- CVE ID
- Package Name
- Image ID
To learn more, see [Creating a New Investigation](/zpc/creating-new-investigation).

### Feature Available
#### Regex Patterns for Including or Excluding File Paths in IaC Scan
Zscaler IaC Scan supports limited scanning of specific directories within a version control system. You can use regular expression (regex) patterns to specify the file paths that must be included or excluded in IaC scans. The option to include the file path is available under Advanced Settings for GitHub, GitLab, and Azure Repos.
[See image.](#regex)
To learn more, see [Configuring IaC Scan for GitHub](/zpc/configuring-iac-scan-github), [Configuring IaC Scan for GitLab](/zpc/configuring-iac-scan-gitlab), and [Configuring IaC Scan for Azure Repos](/zpc/configuring-iac-scan-azure-repos).
[![Use regex patterns to include or exclude file paths](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-rn-iac.png)
]

### Feature Available
#### Security Policies
Added the following security policies for cloud service providers:
- [Microsoft Azure](#microsoft-azure-2-5)
To learn more, see [About Security Policies](/zpc/about-security-policies).
[]
Security Policy Title
Ensure That Microsoft Defender for App Services Is Set To 'On'
Ensure That Microsoft Defender for Azure SQL Databases Is Set To 'On'
Ensure That Microsoft Defender for Containers Is Set To 'On'
Ensure That Microsoft Defender for Key Vault Is Set To 'On'
Ensure That Microsoft Defender for Servers Is Set to 'On'
Ensure That Microsoft Defender for SQL Servers on Machines Is Set To 'On'
Ensure That Microsoft Defender for Storage Is Set To 'On'
Ensure that Microsoft Defender for Cloud Apps (MCAS) Integration with Microsoft Defender for Cloud is Selected
Ensure that Microsoft Defender for Endpoint (WDATP) integration with Microsoft Defender for Cloud is selected
Ensure That Auto provisioning of 'Log Analytics agent for Azure VMs' is Set to 'On'
Ensure 'Additional email addresses' is Configured with a Security Contact Email
Ensure That 'Notify about alerts with the following severity' is Set to 'High'
Ensure That 'All users with the following roles' is set to 'Owner'

### Feature Available
#### Software Package Inventory for Cloud Workloads and Container Images
Customers can run queries on software packages and on threats associated with packages across workloads and container images to help with compliance.
[See image.](#package-threats)
To learn more, see [About Cloud Asset Details](/zpc/about-cloud-asset-details).
[![See Package Threats](/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-package-vulnerabilities.png)
]

### Feature Available
#### Supported Asset Types
The following asset types are now supported by ZPC:
- [AWS](#aws-2-5)
- [Microsoft Azure](#azure-2-5)
- [GCP](#gcp-2-5)
- [Kubernetes](#kubernetes-2-5)
To learn more, see [ Cloud Asset Types and Asset Categories](/zpc/cloud-asset-types-and-asset-categories).
[]
- Service
[]
- AWS Key Management Service (KMS)
- Elastic Load Balancing (ELB)
[]
- Azure Bastion
- Blob Storage
- App Service
- Azure Policy
- Azure Cosmos DB
- Key Vault
- LoggingAndMonitoring
- API Management
[]
- SQL Server on Google Cloud
- Cloud Spanner
- Firestore
- Resource Manager
- Cloud Logging
- Cloud Storage
- Cloud Functions
- Cloud Bigtable
- Cloud Load Balancing
- Cloud Source Repositories
- Cloud Composer

### Feature Available
#### Vulnerability Scanning Support for Google Cloud Platform Workloads
ZPC supports the agentless vulnerability scanning of both Linux and Windows Google Cloud Platform (GCP) workloads. ZPC supports the vulnerability scanning of both non-encrypted and encrypted (Google-managed encryption) workloads.
To learn more, see [Configuring Vulnerability Scanning for GCP Workloads](/zpc/configuring-vulnerability-scanning-gcp-workloads).

## January 19, 2023
### Feature Available
#### Asset Risk Level
The Asset Risk Level shows an asset's risk level based on the number and type of open alerts associated with the asset. The Asset Risk Level is Low, Medium, High, or Critical.
The Asset Risk Level is shown in a column on the Assets page, and users can use the score to filter assets.
[See image.](#zpc-asset-risk-level)
[![ZPC Asset Risk Level](/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-asset-risk-level.png)
]
To learn more, see [About the Cloud Assets Dashboard](/zpc/about-cloud-assets-dashboard).

### Feature Available
#### Audit Logs
Audit logs now integrate with additional ZPC modules (vulnerability management and KSPM onboarding) and show information on actions performed in the specific modules.
To learn more, see [About Audit Logs](/zpc/about-audit-logs) and [Audit Log Events](/zpc/audit-log-events).

### Feature Available
#### Cloud Account Onboarding Enhancements
The following improved usability and expanded functionality are implemented to the cloud account onboarding experience:
- ZPC now monitors every account, organization, and Kubernetes cluster's state. You can view the status on the Cloud Accounts page.
- ZPC offers clear recommendations for configuration errors and permission handling.
- ZPC offers enabling vulnerability settings, KSPM settings, and AWS CloudTrail settings after onboarding a cloud account.
To learn more, see [About Cloud Accounts](/zpc/about-cloud-accounts), [Configuring Vulnerability Scanning for Cloud Accounts](/zpc/configuring-vulnerability-scanning-cloud-accounts), and [Configuring CloudTrail S3 Buckets for AWS Organization](/zpc/configuring-cloud-trail-s3-buckets-aws-organization).

### Feature Available
#### Error Message for Vulnerability Scan Failure
Error messages are displayed for vulnerability scan failures. Whenever a cloud workload or container image is not scanned due to an internal or permission error, the scan status is displayed as Failed along with the relevant error message on the ZPC Admin Portal. This message enables you to investigate and resolve the issue.
[See image.](#errormsg)
To learn more, see [About Vulnerability Scanning](/zpc/about-vulnerability-scanning).
[![View the error message for failed scans](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-vm-failedmsg.png)
]

### Feature Available
#### Ignore Filter End Date
You can now define an end date for an Alert's Ignore filter. When the date is passed, the Ignore status is removed from the alert and the alert returns to either Open or Resolved, depending on whether ZPC still detects the misconfiguration.
[See image](#ignore-filter-end-date).
[![ZPC Ignore Filter End Date](/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-ignore-filter-end-date.png)
]
To learn more, see [About Alerts](/zpc/about-alerts).

### Feature Available
#### Ignore Rules Operationalization
ZPC notifies you when an Ignore rule is no longer valid or operational.
An icon indicating the ignore rule is no longer valid appears at the top-level Ignore Rule table, and the rule is automatically disabled.
[See image.](#ignore-rule-icon)
[![Ignore Rule Icon](/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-ignore-rule-icon.png)
]
The item that invalidates the alert rule is indicated in the Ignore Rule Details view.
[See image.](#ignore-rule-details-reason)
[![Ignore Rule Details Reason](https://help.zscaler.com/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-ignore-rule-details-reason.png)
]
To learn more, see [About Alerts](/zpc/about-alerts?check_logged_in=1#all-tab).

### Feature Available
#### Include Directory Paths in IaC
Zscaler IaC Scan now supports the scanning of specific directories within a version control repository. Organizations leveraging monorepository (monorepo) might not want to scan the entire repository, as it could generate a lot of alerts. By including only the specific directory path, you can use the IaC Scan to focus on improving the security posture of specific parts of the repository.
To learn more, see [Configuring IaC Scan for GitHub](/zpc/configuring-iac-scan-github), [Configuring IaC Scan for GitLab](/zpc/configuring-iac-scan-gitlab), and [Configuring IaC Scan for Azure Repos](/zpc/configuring-iac-scan-azure-repos).

### Feature Available
#### Investigation Enhancements
The following enhancements are implemented in Investigation:
- You can now export investigation data to an Excel file and download the report.
[See image.](#export-investigation-image)
- You can now investigate all deployed packages on workloads and container images.
To learn more, see [Creating a New Investigation](/zpc/creating-new-investigation).
[]
![View the export option on the investigation page.](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/zpc-investigation-export.png)

### Feature Available
#### Kubernetes Support Enhancement
The following enhancements are implemented in Kubernetes support:
- ZPC now supports Google Kubernetes Engine (GKE) clusters. You can onboard GCP GKE clusters and gain insight into their security posture via the asset inventory.
- ZPC now supports onboarding EKS and GKE clusters for multiple accounts belonging to an organization.
To learn more, see [Onboarding a Google Kubernetes Engine Cluster](/zpc/onboarding-google-kubernetes-engine-cluster) and [Onboarding an Amazon Elastic Kubernetes Service Cluster](/zpc/onboarding-amazon-elastic-kubernetes-service-cluster).

### Feature Available
#### New Alert Table Capabilities
The Alerts table has new capabilities:
- The left-most and right-most columns are sticky, simplifying alert navigation and actions.
- New indicators appear to show which columns were sorted and filtered in the Alerts table.
- An Ignore End Date filter is available that allows you to sort on the alert end date.
[See image.](#alerts-table-new-capabilities)
[![ZPC New Alert Table Capabilities](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/ZPC-new-alert-table-capabilities.png)
]
- You can navigate from the individual alert drawer to the policy drawer to learn more details about the policy that triggered the alert.
[See image.](#alert-to-policy-link)
[![ZPC Alert to Policy link](/sites/default/files/downloads/zpc/release-notes/release-upgrade-summary-2023/ZPC-alert-policy-link.png)
]
To learn more, see [About Alert Rules](/zpc/about-alert-rules).

### Feature Available
#### Policy Catalog Enhancements
The policy catalog table now displays the following additional columns:
- Updated by: View the ZPC Administrator username who last edited the security policy.
- Last Updated: View the timestamp of the last edit on the security policy.
- State: View whether the security policy is enabled or disabled.
- Focus: View whether the security policy is asset focused or identity focused.
To learn more, see [About Security Policies](/zpc/about-security-policies).

### Feature Available
#### Secrets Detection
IaC scanning obfuscates secrets such as access keys and database passwords which are present in the Terraform and CloudFormation templates.
To learn more, see [About IaC Integrations](/zpc/about-iac-integrations).

### Feature Available
#### Security Policies
The following security policies are added for cloud service providers:
- [Amazon Web Services](#aws-2-3)
- [Google Cloud Platform](#gcp-2-3)
To learn more, see [About Security Policies](/zpc/about-security-policies).
[]
Security Policy Title
Ensure cloud functions do not have admin privileges
[]
Security Policy Title
Lambda with Admin Identity
Internet-facing Lambda function with admin privileges
Ensure Auto Minor Version Upgrade feature is Enabled for RDS Instances
Ensure that encryption is enabled for EFS file systems
Ensure that public access is not given to RDS Instance
Ensure no security groups allow ingress from ::/0 to remote server administration ports (RDP Port: 3389)
Ensure no security groups allow ingress from ::/0 to remote server administration ports (SSH Port: 22)

### Feature Available
#### Support for Terraform Cloud Pre-Plan
Zscaler IaC Scan supports the scanning of Terraform Cloud templates during the pre-plan phase. This option allows you to see policy violations for specific lines of code within the template file.
To learn more, see [Configuring IaC Scan for Terraform Cloud](/zpc/configuring-iac-scan-terraform-cloud).

### Feature Available
#### Updated Ignore Filter Rules
There is now greater flexibility when creating ignore filters. Ignore filters allow admins to set specific criteria for ignoring any new or updated alerts. The new options include:
- Cloud: Admins can ignore alerts for an entire cloud service provider, such as Amazon Webs Services (AWS), Microsoft Azure, Google Cloud Platform (GCP), and Kubernetes.
- Policy Severity: Admins can ignore alerts generated for Critical, High, Medium, and Low policy severities.
- Individual Policies: Admins can create and ignore rules based on individual users.
- Ignore Filter End Date: The new Ignore Filter End Date feature lets Admins add an end date to an ignore policy.
These conditions can correlate with each other and other existing criteria.
To learn more, see [Ignore Filters](/zpc/about-alerts#ignore-filters).
