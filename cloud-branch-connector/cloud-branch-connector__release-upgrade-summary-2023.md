# Release Upgrade Summary (2023)
Source: https://help.zscaler.com/cloud-branch-connector/release-upgrade-summary-2023

This article provides a summary of all new features and enhancements for Zscaler Cloud & Branch Connector.

**Clouds:** connector.zscaler.net, connector.zscalerone.net, connector.zscalertwo.net, connector.zscalerthree.net, connector.zscloud.net, connector.zscalerbeta.net
The following service updates were deployed to connector.zscaler.net on

## December 18, 2023
### Feature Available
#### Zscaler Cloud Connector Deployment in China with Microsoft Azure
Zscaler Cloud Connector supports deployment in China with Microsoft Azure. To enable this feature, contact Zscaler Support.
To learn more, see [Deploying Zscaler Cloud Connector with Microsoft Azure](/cloud-branch-connector/deploying-zscaler-cloud-connector-microsoft-azure).

## December 15, 2023
### Feature Available
#### Support for AWS User-Defined Tags and Attributes in Security Policies
Zscaler supports applying security policies by leveraging user-defined tags and attributes for workloads deployed in Amazon Web Services (AWS). Contact Zscaler Support to enable this feature.
To learn more, see [About Partner Integrations](/cloud-branch-connector/about-partner-integrations), [Adding an Amazon Web Services Account](/cloud-branch-connector/adding-amazon-web-services-account), and [Configuring Workload Tagging Settings in Amazon Web Services](/cloud-branch-connector/configuring-workload-tagging-settings-amazon-web-services).

### Feature Available
#### Zscaler VDI Agent
The Zscaler Virtual Desktop Infrastructure (VDI) Agent is now available. The Zscaler VDI Agent is a lightweight software Windows application that runs in the user space of the VDI session to authenticate multiple users, establish tunnels to Zscaler Cloud Connector or Zscaler Branch Connector, and exchange user context within the Cloud Connector or Branch Connector. To enable this feature, contact Zscaler Support.
[]![The Connectivity tab of the Zscaler VDI Agent. ](/sites/default/files/downloads/cloud-branch-connector/zscaler-vdi-agent-management/step-step-configuration-guide-zscaler-vdi-agent/ZscalerVDIAgent_ConnectivityTab-3.jpg)
[See image.](#ZSVDIA)
To learn more, see [What Is Zscaler VDI Agent?](/cloud-branch-connector/what-zscaler-vdi-agent), [Step-by-Step Configuration Guide for Zscaler VDI Agent](/cloud-branch-connector/step-step-configuration-guide-zscaler-vdi-agent), and [Customizing Zscaler VDI Agent with Install Options for MSI](/cloud-branch-connector/customizing-zscaler-vdi-agent-install-options-msi).

## December 11, 2023
### Feature Available
#### Zscaler Branch Connector Deployment on Zero Trust Branch Device 400 (ZT400)
Zscaler Branch Connector supports deployment on Zero Trust Branch Device 400 (ZT400). To enable this feature, contact Zscaler Support.
[]![ZeroTrustBranchDevice-ZT400.jpg](/sites/default/files/downloads/ZeroTrustBranchDevice-ZT400.jpg)
[See image.](#ZT400)
To learn more, see [Installing Zero Trust Branch Devices](/cloud-branch-connector/installing-zero-trust-branch-devices) and [Deploying Zero Trust Branch Devices](/cloud-branch-connector/deploying-zero-trust-branch-devices).

## November 17, 2023
### Feature Available
#### Event and Metrics Logs in NSS and Cloud NSS Feeds
You can configure NSS and Cloud NSS feeds for events and health metrics in the Zscaler Cloud & Branch Connector Admin Portal. Select Event or Metrics as the log type for a NSS or Cloud NSS feed.
[See image.](#EventMetricsRelease)
[]![The Event Log Type while adding a NSS feed in the Zscaler Cloud & Branch Connector Admin Portal.](/sites/default/files/downloads/cloud-branch-connector/release-notes/release-upgrade-summary-2023/Event%20release.png)
![The Metrics Log Type while adding a NSS feed in the Zscaler Cloud & Branch Connector Admin Portal.](/sites/default/files/downloads/cloud-branch-connector/release-notes/release-upgrade-summary-2023/Metrics%20release.png)
To learn more about NSS Feeds, see [Adding NSS Feeds for Event Logs](/cloud-branch-connector/adding-nss-feeds-event-logs) and [Adding NSS Feeds for Metrics Logs](/cloud-branch-connector/adding-nss-feeds-metrics-logs). To learn more about Cloud NSS Feeds, see [Adding Cloud NSS Feeds for Event Logs](/cloud-branch-connector/adding-cloud-nss-feeds-event-logs) and [Adding Cloud NSS Feeds for Metrics Logs](/cloud-branch-connector/adding-cloud-nss-feeds-metrics-logs).

## November 13, 2023
### Feature Available
#### Zscaler Branch Connector Deployment on Zero Trust Branch Devices
Zscaler Branch Connector supports deployment on Zero Trust Branch Devices. To enable this feature, contact Zscaler Support.
To learn more, see [Understanding Zero Trust Branch Devices](/cloud-branch-connector/understanding-zero-trust-branch-devices), [Installing Zero Trust Branch Devices](/cloud-branch-connector/installing-zero-trust-branch-devices), and [Deploying Zero Trust Branch Devices](/cloud-branch-connector/deploying-zero-trust-branch-devices).

## November 10, 2023
### Feature Available
#### Update to Zscaler Cloud Connector Amazon Machine Image (AMI)
The Amazon Machine Image (AMI) for Zscaler Cloud Connector has been updated to version ZS6.1.26.1, which provides a general security fix.
To learn more, see [Deploying Zscaler Cloud Connector with Amazon Web Services](/cloud-branch-connector/deploying-zscaler-cloud-connector-amazon-web-services) and [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector).

## October 20, 2023
### Feature Available
#### Update to Zscaler Cloud Connector Amazon Machine Image (AMI)
The Amazon Machine Image (AMI) for Zscaler Cloud Connector has been updated to version ZS6.1.26.0, which provides:
- Auto scaling enablement via the Cloud Provisioning Template. To enable auto scaling, contact Zscaler Support.
- Medium and Large virtual machine (VM) size support via the Cloud Provisioning Template.
- Deployment configuration updates to the Cloud Connector VM network interface association order utilizing the primary interface as service and secondary interface as management to support auto scaling and non-auto scaling deployments.
- Updates to the AWS deployment templates for CloudFormation and Terraform in GitHub.
To learn more, see [Configuring a Cloud Provisioning Template](/cloud-branch-connector/configuring-cloud-provisioning-template), [Deployment Templates for](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector) [Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector), and [Deploying](/cloud-branch-connector/deploying-cloud-connector-amazon-web-services) [Zscaler Cloud Connector with Amazon Web Services](/cloud-branch-connector/deploying-cloud-connector-amazon-web-services).

## October 16, 2023
### Feature Available
#### Zscaler Cloud Connector Deployment on the Google Cloud Platform (GCP)
Zscaler Cloud Connector now supports deployment on the Google Cloud Platform (GCP).
To learn more, see [Deploying Zscaler Cloud Connector on the Google Cloud Platform](/cloud-branch-connector/deploying-zscaler-cloud-connector-google-cloud-platform).

## October 02, 2023
### Feature Available
#### Update to Azure Virtual Machine for Zscaler Cloud Connector
The Microsoft Azure virtual machine (VM) for Zscaler Cloud Connector has been updated, which includes the option to enable encryption at host, providing end-to-end encryption for your VM data.
To learn more, see [Deploying Zscaler Cloud Connector with Microsoft Azure ](/cloud-branch-connector/deploying-cloud-connector-microsoft-azure)and [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector).

## September 22, 2023
### Feature Available
#### Cloud NSS Feeds
Cloud Nanolog Streaming Service (NSS) allows you to instantly stream logs from the Zscaler Cloud & Branch Connector Admin Portal directly into a cloud-based security information and event management (SIEM) system without the need to deploy an NSS VM. Cloud NSS Feeds allow you to use cloud-to-cloud log streaming.
You can configure a Cloud NSS Feed that is automatically assigned to Cloud NSS. Also, you can use Cloud NSS Feeds to configure SIEM connectivity across cloud-based SIEMs. To enable this feature, your organization must have a Cloud NSS subscription. Contact Zscaler Support for further assistance.
[]![The Cloud NSS Feeds window in the Zscaler Cloud & Branch Connector Admin Portal. ](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/Cloud-NSSFeed-Window.png)
[See image.](#CloudNSSFeeds)
To learn more, see [About Cloud NSS Feeds](/cloud-branch-connector/about-cloud-nss-feeds).

## September 05, 2023
### Feature Available
#### Support for 50k Application Segments
Cloud & Branch Connector now supports up to 50k ZPA Application Segments. Contact Zscaler Support to enable this feature.
To learn more, see [Configuring Defined Application Segments](/zpa/configuring-application-segments).

## June 30, 2023
### Feature Available
#### Enable, Disable, and Delete Cloud & Branch Connector VMs
You can enable or disable the operational status of your Cloud Connector and Branch Connector virtual machines (VMs) from the Edit Connectors window.
[]![Enable or Disable the Operational Status from the Edit Connectors window.](/sites/default/files/downloads/cloud-branch-connector/release-notes/release-upgrade-summary-2022/EditConnectors_OperationalStatus_Enable_Disable.png)
[See image.](#OperationalStatus)
You can also delete individual Cloud or Branch Connectors by clicking the Delete icon on the Connector Groups pages. This action cannot be undone.
[]![The Delete icon next to a Cloud Connector from the Cloud Connector Groups page.](/sites/default/files/downloads/cloud-branch-connector/release-notes/release-upgrade-summary-2022/EditCloudConnectors_DeleteIcon_2.png)
[See image.](#Delete)
To learn more, see [About Cloud Connector Groups](/cloud-branch-connector/about-cloud-connector-groups), [Editing Cloud Connectors](/cloud-branch-connector/editing-cloud-connectors), [About Branch Connector Groups](/cloud-branch-connector/about-branch-connector-groups), and [Editing Branch Connectors](/cloud-branch-connector/editing-branch-connectors).

## June 27, 2023
### Feature Available
#### Update to Azure Virtual Machine for Zscaler Cloud Connector
The Microsoft Azure virtual machine (VM) for Zscaler Cloud Connector has been updated to introduce additional OS Hardening, including OpenSSL vulnerability fixes.
To learn more, see[ Deploying Cloud Connector with Microsoft Azure](/cloud-branch-connector/deploying-cloud-connector-microsoft-azure).

## June 16, 2023
### Feature Available
#### Update to AWS Deployment Templates in GitHub
The Amazon Web Services (AWS) Deployment Templates for Zscaler Cloud Connector have been updated to include the new Amazon Machine Image (AMI) version and Instance Metadata Service Version 2 (IMDSv2) enforced by default.
To learn more, see[ Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector).

### Feature Available
#### Update to Zscaler Cloud Connector Amazon Machine Image (AMI)
The Amazon Machine Image (AMI) for Zscaler Cloud Connector has been updated to version ZS6.1.25.0, which introduces additional OS Hardening including OpenSSL vulnerability fixes.
To learn more, see [Deploying Cloud Connector with Amazon Web Services](/cloud-branch-connector/deploying-cloud-connector-amazon-web-services).

## May 26, 2023
### Feature Available
#### HTTP Monitoring for Zscaler Cloud Connector
Zscaler Cloud Connector now performs automatic HTTP monitoring to ZIA Gateways via each connected tunnel in order to monitor service health. This ensures quicker failover detection.
To learn more, see [About Zscaler Internet Access Gateways](/cloud-branch-connector/about-zia-gateways).

### Feature Available
#### ICMP Access for Cloud and Branch Connector
ICMP access to application segments is available for Zscaler Cloud and Branch Connector. When setting up an application segment, you can choose whether Cloud and Branch Connector allow ICMP communication in the ZPA Admin Portal.
To learn more, see [Configuring Defined Application Segments](/zpa/configuring-application-segments).

## May 01, 2023
### Feature Available
#### Support for Combined Branch Connector & App Connector VMs
You can now download and deploy your combined Branch Connector & App Connector virtual machine (VM) images. [Branch Connector Images](/cloud-branch-connector/downloading-branch-connector-images) include App Connectors that have not yet been provisioned. In order to deploy Branch Connector & App Connector, you must select the hypervisor host (VMware ESXi or Linux KVM) and configure the deployment properties accordingly. To learn more, see [Deployment Templates for Zscaler Branch Connector & App Connector](/cloud-branch-connector/deployment-templates-zscaler-branch-connector-app-connector), [Deploying Branch Connector & App Connector on VMware Platforms](/cloud-branch-connector/deploying-branch-connector-app-connector-vmware-platforms), and [Deploying Branch Connector & App Connector with Linux KVM](/cloud-branch-connector/deploying-branch-connector-app-connector-linux-kvm).

## February 17, 2023
### Feature Available
#### EUSA in the Zscaler Cloud Connector Portal
An End User Subscription Agreement (EUSA) appears in the Zscaler Cloud Connector Portal when you log in for the first time. One admin per organization is required to accept the agreement. To learn more, see [Accepting the End User Subscription Agreement (EUSA)](/cloud-branch-connector/accepting-end-user-subscription-agreement-eusa).

### Feature Available
#### Update to Scheduled Upgrades
You can select the day of the week to schedule the software upgrade for your Cloud Connectors from the Edit Connectors window.
[]![The Edit Connectors window highlighting the day of the week selection for scheduled upgrades.](/sites/default/files/downloads/EditConnectors_ZscalerCloudConnector_DayoftheWeek.png)
[See image.](#EditConnectors-Dayoftheweek)
To learn more, see [About Cloud Connector Groups](/cloud-branch-connector/about-cloud-connector-group), [Editing Cloud Connectors](/cloud-branch-connector/edit-connectors), and[ Managing Cloud Connector Upgrades](/cloud-branch-connector/managing-cloud-connector-upgrades).

## January 27, 2023
### Feature Available
#### Update to Azure Virtual Machine for Zscaler Cloud Connector
The Microsoft Azure virtual machine (VM) for Zscaler Cloud Connector has been updated, which provides improvements to support bringing up new Cloud Connectors when there are pending activations from other users and reducing the boot-up time. To learn more, see [Deploying Cloud Connector with Microsoft Azure](/cloud-branch-connector/deploying-cloud-connector-microsoft-azure).

## January 20, 2023
### Feature Available
#### Update to Zscaler Cloud Connector Amazon Machine Image (AMI)
The Amazon Machine Image (AMI) for Zscaler Cloud Connector has been updated to version ZS6.1.24.6, which provides improvements to support bringing up new Cloud Connectors when there are pending activations from other users and reducing the boot-up time. To learn more, see [Deploying Cloud Connector with Amazon Web Services](/cloud-branch-connector/deploying-cloud-connector-amazon-web-services).
