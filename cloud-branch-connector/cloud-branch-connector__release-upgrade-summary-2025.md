# Release Upgrade Summary (2025)
Source: https://help.zscaler.com/cloud-branch-connector/release-upgrade-summary-2025

This article provides a summary of all new features and enhancements for Zscaler Cloud & Branch Connector. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com).

**Clouds:** connector.zscaler.net, connector.zscalerone.net, connector.zscalertwo.net, connector.zscalerthree.net, connector.zscloud.net, connector.zscalerbeta.net
The following service updates were deployed to connector.zscaler.net on

## November 10, 2025
### Feature Available
#### Cloud Connector Traffic Enhancements
The Zscaler Cloud Connector traffic forwarding capabilities have been extended to secure east-west network traffic. This includes subnet-to-subnet and virtual private cloud (VPC)-to-VPC communication across cloud providers (i.e., Amazon Web Services (AWS), Microsoft Azure, and Google Cloud Platform (GCP)). The forwarding capabilities also support ingress traffic for public applications hosted in AWS for Cloud Connector and Zero Trust Gateways. You can use the Local traffic forwarding option to allow the traffic communication for east-west and ingress use cases.
[See image.](#eastwest)
To learn more, see [About Traffic Forwarding](/cloud-branch-connector/about-traffic-forwarding), [Configuring Traffic Forwarding Rules](/cloud-branch-connector/configuring-traffic-forwarding-rule), [What Is Zscaler Cloud Connector?](/cloud-branch-connector/what-zscaler-cloud-connector), and [What Are Zero Trust Gateways?](/cloud-branch-connector/what-zero-trust-gateways)
[]
![Selecting the Local option from the Forwarding Method drop-down menu when configuring a traffic forwarding rule in the Zscaler Cloud & Branch Connector Admin Portal](/sites/default/files/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-amazon-web-services-account-group-details/Local.png)

## October 27, 2025
### Feature in Limited Availability
#### Sublocation Scopes to Group Cloud Connector Workloads in AWS
Sublocation scopes allow you to group workload traffic into sublocations at various levels within your Amazon Web Services (AWS) account. These levels, or scopes, are VPC Endpoint, VPC, Account, and Namespace. For example, the VPC scope groups workloads from one or more Virtual Private Clouds (VPCs) into a sublocation.
If you define scopes for sublocations, a single location can have multiple sublocations with different Cloud Connector and Zscaler Internet Access (ZIA) policies applied to them, policy lookup can distinguish between multiple workloads with the same source IP address space, and logs can indicate the correct workload when there are overlapping IP address spaces.
All sublocations within a location must be configured with the same criteria: scope only, combination of scope and IP address range, or IP address range only. You can add a scope to existing sublocations that already have a defined IP address range.
You configure sublocations for Cloud Connector locations in the ZIA Admin Portal. The Locations page in the Cloud & Branch Connector Admin Portal shows the scope type for sublocations that have scope criteria.
[See image.](#ScopeTypeColumn)
To learn more, see [Using Sublocation Scopes to Group Cloud Connector Workloads](/cloud-branch-connector/using-sublocation-scopes-group-cloud-connector-workloads-amazon-web), [Support for Sublocation Scopes](/node/1529990), and [Configuring Sublocations](/zia/configuring-sublocations).
[][/cloud-branch-connec]![xxx](/sites/default/files/downloads/cloud-branch-connector/release-notes/release-upgrade-summary-2022/Subloc_Scope_RN.png)

## October 24, 2025
### Feature Available
#### Amazon Web Services Endpoints for Partner Integrations
The following Amazon Web Services (AWS) endpoints are added for partner integrations. These endpoints extend programmatic access to features and functionalities for AWS accounts and AWS account groups:
- [AWS Account and AWS Account Group APIs](#cb-rn-aws-api-list)
To learn more about each endpoint, see the [API Reference Guide](/cloud-branch-connector/partner-integrations).
[]You can create, update, and delete AWS accounts and account groups. You can also retrieve the list of available AWS accounts and account groups with metadata. Additionally, you can retrieve the CloudFormation template URL, a list of AWS regions supported for workload discovery settings (WDS), etc. using the following APIs:
- `GET /publicCloudInfo`
- `POST /publicCloudInfo`
- `GET /publicCloudInfo/cloudFormationTemplate`
- `GET /publicCloudInfo/count`
- `POST /publicCloudInfo/generateExternalId`
- `GET /publicCloudInfo/lite`
- `GET /publicCloudInfo/supportedRegions`
- `GET /publicCloudInfo/{id}`
- `PUT /publicCloudInfo/{id}`
- `DELETE /publicCloudInfo/{id}`
- `PUT /publicCloudInfo/{id}/changeState`
- `GET /discoveryService/workloadDiscoverySettings`
- `PUT /discoveryService/{id}/permissions`
- `GET /accountGroups`
- `POST /accountGroups`
- `GET /accountGroups/count`
- `GET /accountGroups/lite`
- `GET /accountGroups/{id}`
- `PUT /accountGroups/{id}`
- `DELETE /accountGroups/{id}`

### Feature in Limited Availability
#### JSON Web Token Authentication
JSON Web Token (JWT) authentication is available for Zscaler Cloud & Branch Connector workloads. You configure JWT authentication in the ZIA Admin Portal. You configure token validators for JWT authentication in the ZIdentity Admin Portal. Sessions that include JWT authentication are logged in Web Insights logs in the ZIA Admin Portal with the user ID from the JWT.
JWT authentication is not enabled by default, and requires a provisioning ticket to be submitted to [Zscaler Support](https://help.zscaler.com/zia-submit-ticket).
To learn more, see [JWT Authentication](/node/1529432) and [Understanding JWT Authentication](/zia/understanding-jwt-authentication).

### Feature in Limited Availability
#### Support for Google Cloud Platform User-Defined Tags and Attributes in Security Policies
Zscaler supports applying security policies by leveraging user-defined tags and attributes for workloads deployed in Google Cloud Platform (GCP). Additionally, Zscaler supports applying labels and network tags in GCP.
To learn more, see [About Google Cloud Platform Accounts](/cloud-branch-connector/about-google-cloud-platform-accounts), [Adding a Google Cloud Platform Account](/cloud-branch-connector/adding-google-cloud-platform-account), [Analyzing Google Cloud Platform Account Details](/cloud-branch-connector/analyzing-google-cloud-platform-account-details), and [Configuring Workload Discovery for Workloads in Google Cloud Platform](/cloud-branch-connector/configuring-workload-discovery-workloads-google-cloud-platform).

## September 26, 2025
### Feature Available
#### Endpoints for Managing Cloud & Branch Connector VMs by Instance ID
New endpoints are added to extend programmatic access for managing Cloud & Branch Connector virtual machines (VMs). The following APIs allow you to retrieve detailed information about a VM and delete a VM using its native public cloud instance ID:
- `GET /ecVm/uuid/{vmInstanceId}`
- `DELETE /ecVm/uuid/{vmInstanceId}`
To learn more about each endpoint, see the [API Reference Guide](/cloud-branch-connector/cloud-branch-connector-groups).

## September 11, 2025
### Feature Available
#### Update to Zscaler Branch Connector Virtual Machine
The Zscaler Branch Connector virtual machine (VM) image has been updated. This image provides a general security enhancement. Zscaler strongly recommends updating and redeploying the image as soon as possible to take advantage of the improved security instead of waiting for the [scheduled upgrade](/cloud-branch-connector/managing-cloud-branch-connector-upgrades).
To learn more, see the deployment guides per platform in [Branch Connector Deployment Management](/cloud-branch-connector/deployment-management/branch-connector-deployment-management), [Downloading Branch Connector Image](/cloud-branch-connector/downloading-branch-connector-images), and [Deployment Templates for Branch Connector and App Connector](/cloud-branch-connector/deployment-templates-zscaler-branch-connector-zpa-app-connector).

### Feature Available
#### Update to Zscaler Cloud Connector Image
Zscaler Cloud Connector has been updated to version zs1.145.84_6.2.425577. This version provides a general security enhancement. Zscaler strongly recommends updating and redeploying this version as soon as possible to take advantage of the improved security instead of waiting for the [scheduled upgrade](/cloud-branch-connector/managing-cloud-branch-connector-upgrades).
To learn more, see the deployment guides per platform in [Cloud Connector Deployment Management](/cloud-branch-connector/deployment-management/cloud-connector-deployment-management) and [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector).

## August 27, 2025
### Feature Available
#### Update to Zscaler Branch Connector Virtual Machine Image for Hyper-V
The Zscaler Branch Connector virtual machine (VM) image for Hyper-V has been updated. This image contains ZscalerOS 42, which provides additional OS hardening and vulnerability fixes. Zscaler strongly recommends updating and redeploying the image as soon as possible to take advantage of the improved security.
To learn more, see [Downloading Branch Connector Images](/cloud-branch-connector/downloading-branch-connector-images), [Deploying Branch Connector with Hyper-V](/cloud-branch-connector/deploying-branch-connector-hyper-v), [Deploying Branch Connector & App Connector with Hyper-V](/cloud-branch-connector/deploying-branch-connector-app-connector-hyper-v), and [Deployment Templates for Branch Connector and App Connector](/cloud-branch-connector/deployment-templates-zscaler-branch-connector-zpa-app-connector).

### Feature Available
#### Update to Zscaler Branch Connector Virtual Machine Image for Linux KVM
The Zscaler Branch Connector virtual machine (VM) image for Linux KVM has been updated. This image contains ZscalerOS 42, which provides additional OS hardening and vulnerability fixes. Zscaler strongly recommends updating and redeploying the image as soon as possible to take advantage of the improved security.
To learn more, see [Downloading Branch Connector Images](/cloud-branch-connector/downloading-branch-connector-images), [Deploying Branch Connector with Linux KVM](/cloud-branch-connector/deploying-branch-connector-linux-kvm), [Deploying Branch Connector & App Connector with Linux KVM](/cloud-branch-connector/deploying-branch-connector-app-connector-linux-kvm), and [Deployment Templates for Branch Connector & App Connector](/cloud-branch-connector/deployment-templates-zscaler-branch-connector-zpa-app-connector).

### Feature Available
#### Update to Zscaler Branch Connector Virtual Machine Image for VMware ESXi
The Zscaler Branch Connector virtual machine (VM) image for VMware ESXi has been updated. This image contains ZscalerOS 42, which provides additional OS hardening and vulnerability fixes. Zscaler strongly recommends updating and redeploying the image as soon as possible to take advantage of the improved security.
To learn more, see [Downloading Branch Connector Images](/cloud-branch-connector/downloading-branch-connector-images), [Deploying Branch Connector on VMware Platforms](/cloud-branch-connector/deploying-branch-connector-vmware-platforms), [Deploying Branch Connector & App Connector on VMware Platforms](/cloud-branch-connector/deploying-branch-connector-app-connector-vmware-platforms), and [Deployment Templates for Branch Connector & App Connector](/cloud-branch-connector/deployment-templates-zscaler-branch-connector-zpa-app-connector).

## June 30, 2025
### Feature Available
#### TLS Tunnel Support for Cloud Connectors
You can select TLS as the Zscaler Internet Access (ZIA) tunnel mode when editing a Cloud Connector. You can also enable or disable fallback to TLS, which detects when the tunnel is unhealthy and switches the tunnel from Unencrypted UDP or DTLS to TLS.
[See image.](#fallbacktotls)
To learn more, see [Editing Cloud Connectors](/cloud-branch-connector/editing-cloud-connectors).
[]
![The Fallback to TLS button when editing a physical or virtual branch device in the Zscaler Cloud & Branch Connector Admin Portal](/sites/default/files/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/analyzing-zero-trust-gateway-details/fallbacktotls.png)

### Feature in Limited Availability
#### Zscaler Cloud Connector TCP Optimization with SNI Learning
Cloud Connector supports an integrated TCP optimization module that learns server name indication (SNI) and maintains a database of learned IP addresses, fully qualified domain names (FQDNs), and wildcard FQDN mappings. The module is native to Cloud Connectors, and you can use FQDNs, wildcard FQDNs, and Zscaler Private Access (ZPA) without requiring the DNS requests and resolutions to flow through Cloud Connector. The traffic must be web HTTP/HTTPS-based. To access this feature, contact Zscaler Support.
To learn more, see [Configuring Traffic Forwarding Rules](/cloud-branch-connector/configuring-traffic-forwarding-rule) and [Configuring Destination IP Groups](/cloud-branch-connector/configuring-destination-ip-groups).

## May 23, 2025
### Feature in Limited Availability
#### Support for Microsoft Azure User-Defined Tags and Attributes in Security Policies
Zscaler supports applying security policies by leveraging user-defined tags and attributes for workloads deployed in Microsoft Azure. To request this feature, contact Zscaler Support.
To learn more, see [About Microsoft Azure Accounts](/cloud-branch-connector/about-microsoft-azure-accounts), [Configuring the Workload Discovery Service for Microsoft Azure Accounts](/cloud-branch-connector/configuring-workload-discovery-service-microsoft-azure-accounts), [Analyzing Microsoft Azure Account Details](/cloud-branch-connector/analyzing-microsoft-azure-account-details), and [Configuring IAM Roles and Permissions for Microsoft Azure](/cloud-branch-connector/configuring-iam-roles-and-permissions-microsoft-azure).

## May 19, 2025
### Feature in Limited Availability
#### Zscaler Zero Trust Gateways in Amazon Web Services
Zscaler has introduced a fully managed, cloud-native SaaS security offering in Amazon Web Services (AWS) that allows you to secure your workload traffic and eliminate the need to manage your security infrastructure in your AWS environment. It provides the same security controls for cloud-to-internet and cloud-to-cloud communication.
To learn more, see [About Zero Trust Gateways](/cloud-branch-connector/about-zero-trust-gateways), [Adding a Zero Trust Gateway](/cloud-branch-connector/adding-zero-trust-gateway), [Analyzing Zero Trust Gateway Details](/cloud-branch-connector/analyzing-zero-trust-gateway-details), and [Analyzing Zero Trust Gateways](/cloud-branch-connector/analyzing-zero-trust-gateways).

## May 08, 2025
### Feature Available
#### Update to Zscaler Cloud Connector Amazon Machine Image
The AMI for Zscaler Cloud Connector has been updated to version ZS6.1.26.2. This image contains ZscalerOS 42, which provides additional OS hardening and vulnerability fixes. Zscaler strongly recommends updating and redeploying the image as soon as possible to take advantage of the improved security.
To learn more, see [Deploying Zscaler Cloud Connector with Amazon Web Services](/cloud-branch-connector/deploying-zscaler-cloud-connector-amazon-web-services) and [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector).

## April 23, 2025
### Feature Available
#### Update to Zscaler Cloud Connector Azure Virtual Machine
The Azure VM image for Zscaler Cloud Connector has been updated to version 24.3.5. This image contains ZscalerOS 42, which provides additional OS hardening and vulnerability fixes. Zscaler strongly recommends updating and redeploying the image as soon as possible to take advantage of the improved security.
To learn more, see [Deploying Zscaler Cloud Connector with Microsoft Azure](/cloud-branch-connector/deploying-zscaler-cloud-connector-microsoft-azure) and [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector).

## April 04, 2025
### Feature Available
#### Update to Cloud & Branch Connector API
The Cloud & Branch Connector API has been updated to include the following new categories of endpoints to extend programmatic access to various features and functionalities:
- [Policy Management](#traffic-forwarding-rules-api)
- [Policy Resources](#policy-resources-api)
- [Forwarding Gateways](#gateways-api)
To learn more about each endpoint, see the [API Reference](/cloud-branch-connector/zscaler-cloud-branch-connector-api/api-developer-reference-guide/reference-guide).
The Postman collection has also been updated to include the new resources. To learn more, see [Configuring the Postman REST API Client](/cloud-branch-connector/configuring-postman-rest-api-client).
[]You can create and update traffic forwarding rules and retrieve the list of available rules and the count of rules using the following endpoints:
- `GET /ecRules/ecRdr`
- `POST /ecRules/ecRdr`
- `PUT /ecRules/ecRdr/{ruleId}`
- `GET /ecRules/ecRdr/count`
[]You can programmatically create and manage the following objects that are used in policy configuration in Cloud & Branch Connector.
- [IP and FQDN Groups](#ip-groups-api)
- [Network Services](#network-services-api)
- [ZPA Application Segments](#zpa-app-segments-api)
[]You can create, update, and delete source IP groups, destination IP groups, and IP pools, and retrieve the list of each of these policy resources using the following endpoints:
- `GET /ipSourceGroups`
- `GET /ipSourceGroups/lite`
- `POST /ipSourceGroups`
- `DELETE /ipSourceGroups/{ipGroupId}`
- `GET /ipDestinationGroups`
- `GET /ipDestinationGroups/lite`
- `POST /ipDestinationGroups`
- `DELETE /ipDestinationGroups/{ipGroupId}`
- `GET /ipGroups`
- `GET /ipGroups/lite`
- `POST /ipGroups`
- `DELETE /ipGroups/{ipGroupId}`
[]You can create, update, and delete custom network services and retrieve the list of available network services and network service groups using the following endpoints:
- `GET /networkServices`
- `POST /networkServices`
- `PUT /networkServices/{serviceid}`
- `DELETE /networkServices /{serviceid}`
- `GET /networkServiceGroups`
[]You can retrieve the list of available ZPA application segments using the `GET /zpaResources/applicationSegments` endpoint.
[]You can create and delete ZIA gateways and Log and Control gateways and retrieve the list of these gateways using the following endpoints:
- `GET /gateways`
- `GET /gateways/lite`
- `POST /gateways`
- `DELETE /gateways/{gatewayId}`

## March 31, 2025
### Feature Available
#### Zscaler Client Connector for VDI ZPA Support
Support for Zscaler Private Access (ZPA) using Zscaler Client Connector for VDI is available.
To learn more, see [What Is Zscaler Client Connector for VDI?](/cloud-branch-connector/what-zscaler-vdi-agent), [Step-by-Step Configuration Guide for Zscaler Client Connector for VDI](/cloud-branch-connector/step-step-configuration-guide-zscaler-vdi-agent), [Configuring VDI Forwarding Profiles](/cloud-branch-connector/configuring-vdi-agent-forwarding-profiles), and [Configuring VDI Templates](/cloud-branch-connector/configuring-vdi-agent-templates).

## March 17, 2025
### Feature Available
#### Automatic Fail Open for Physical Branch Devices
Zscaler Branch Connector supports automatic fail open for physical branch devices deployed in gateway mode, which allows all local and internet-destined traffic to flow without policy validation or content inspection if a policy enforcement engine fails or is stopped for upgrades.
[See image.](#failopen)
To learn more, see [Editing Physical Branch Devices](/cloud-branch-connector/editing-physical-branch-devices).
[]
![The Automatic Failover button under Fail Open in the Edit Physical Branch Device window of the Zscaler Cloud & Branch Connector Admin Portal](/sites/default/files/downloads/tech-pubs-drafts/cloud-connector-draft-articles/editing-physical-branch-devices-draft-doc-55177-doc-53148/failopen.png)

### Feature Available
#### Custom DHCP Options for Physical Branch Devices
You can add custom Dynamic Host Configuration Protocol (DHCP) options when configuring a branch configuration template for physical branch devices deployed in gateway mode.
[See image.](#CustomDHCPOption)
To learn more, see [Configuring a Branch Connector Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template#GatewayLAN).
[]
![The Custom Option option under DHCP Options in the LAN section of the branch configuration template in the Zscaler Cloud & Branch Connector Admin Portal](/sites/default/files/downloads/tech-pubs-drafts/cloud-connector-draft-articles/configuring-destination-ip-groups-draft-doc-55201/CustomDHCPOption1.png)

## March 14, 2025
### Feature Available
#### Azure Virtual Machine Availability in Microsoft Azure Marketplace for Spain
The Zscaler Cloud Connector virtual machine (VM) is available in the Microsoft Azure Marketplace for the Spain Central region. If you deploy Cloud Connector using Terraform, use the latest [Azure Terraform scripts](https://github.com/zscaler/terraform-azurerm-cloud-connector-modules) (v0.7.0).
To learn more, see [Deploying Zscaler Cloud Connector with Microsoft Azure](/cloud-branch-connector/deploying-zscaler-cloud-connector-microsoft-azure) and [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector#azure-terraform).

## February 14, 2025
### Feature Available
#### Zscaler Cloud Connector Integration with HashiCorp Vault
You can use a HashiCorp Vault to store and manage secret credentials for new Zscaler Cloud Connectors deployed on the Google Cloud Platform (GCP). HashiCorp Vault is a cloud-agnostic identity-based secret management system that can be used as an alternative to GCP Secret Manager. Use the latest [GCP Terraform scripts](https://github.com/zscaler/terraform-gcp-cloud-connector-modules/releases) (v0.2.0) and Cloud Connector image (zs-cc-ga-02022025) in Google Cloud Marketplace to integrate Cloud Connector with HashiCorp Vault.
To learn more, see [Deploying Zscaler Cloud Connector on the Google Cloud Platform](/cloud-branch-connector/deploying-zscaler-cloud-connector-google-cloud-platform), [Storing Your Secret Credentials in HashiCorp Vault for Google Cloud Platform-Based Cloud Connectors](/cloud-branch-connector/storing-your-secret-credentials-hashicorp-vault), and [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector).
