# Release Upgrade Summary (2022)
Source: https://help.zscaler.com/cloud-branch-connector/release-upgrade-summary-2022

This article provides a summary of all new features and enhancements for Zscaler Cloud Connector.

**Clouds:** connector.zscaler.net, connector.zscalerone.net, connector.zscalertwo.net, connector.zscalerthree.net, connector.zscloud.net, connector.zscalerbeta.net
The following service updates were deployed to connector.zscaler.net on

## December 16, 2022
### Feature Available
#### GitHub Migration for Zscaler Cloud Connector Deployment Templates
Deployment Templates for Zscaler Cloud Connector have migrated from the Zscaler Cloud Connector Portal to GitHub. To learn more, see [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector).

## December 09, 2022
### Feature Available
#### DNS Resolutions for Zscaler Cloud Connector
Zscaler Cloud Connector supports the ability to forward workload-initiated DNS requests to custom DNS resolvers and cloud-native DNS servers, such as Amazon Web Services (AWS) Route 53 DNS Server or Microsoft Azure DNS Server. This enables ZPA application domains to be resolved by Cloud Connectors, while non-ZPA domains are forwarded to the target DNS resolvers.
To learn more, see [Handling DNS Resolutions for Zscaler Cloud Connector](/cloud-branch-connector/dns-forwarding-zscaler-cloud-connector).

### Feature Available
#### Update to Tunnel Encryption
The Zscaler Cloud Connector software has been updated to allow users to select between DTLS or Unencrypted options for the tunnel encryption mode. This is the encryption mode used when forwarding your Cloud Connector’s traffic to ZIA. The ZIA tunnel encryption can be selected from the Edit Connectors window. To use this feature, you must have a Tunnel Encryption subscription.
[]![The Edit Connectors window highlighting ZIA Tunnel Mode.](/sites/default/files/downloads/cloud-connector/administration/about-cloud-connector-group/EditConnectors_ZscalerCloudConnector3.png)
[See image.](#TunnelEncryption)
To learn more, see [About Cloud Connector Groups](/cloud-branch-connector/about-cloud-connector-group),[ About Branch and Cloud Connector Upgrades](/cloud-branch-connector/about-zscaler-cloud-connector-upgrades), and [Editing Cloud Connectors](/cloud-branch-connector/edit-connectors).

## October 28, 2022
### Feature Available
#### Accelerated Networking in the Azure Marketplace
Accelerated networking is enabled by default when deploying Zscaler Cloud Connector as a virtual machine (VM) with Microsoft Azure using Terraform scripts or the Azure Marketplace solution. To learn more, see [Deploying Cloud Connector with Microsoft Azure](/cloud-branch-connector/deploying-cloud-connector-microsoft-azure) and [About Cloud Automation Scripts](/cloud-branch-connector/about-cloud-automation-scripts).

## October 07, 2022
### Feature Available
#### API Key Exclusivity
The API key is now exclusive to the Zscaler Cloud Connector Portal and is no longer shared with the Zscaler Internet Access (ZIA) Admin Portal. During this transition, both the ZIA Admin Portal and the Zscaler Cloud Connector Portal start with the same API key. Users can then change each API key separately from the respective portals. To learn more, see [About API Key Management](/cloud-branch-connector/about-api-key-management) and[ Managing Organization API Keys](/cloud-branch-connector/managing-organization-api-keys).

### Feature Available
#### Multiple Language Support
With the support of multiple languages, admins can display the Zscaler Cloud Connector Portal in the following languages: English, French, German, Japanese, Spanish, or Simplified Chinese.
[]![Multiple Language Support accessed from the My Profile page in the Zscaler Cloud Connector Portal.](/sites/default/files/downloads/cloud-connector/administration/customizing-your-admin-account-settings/Zcloudconnector-multilanguage-support.png)
[See image.](#MultiLanguageSupport)
To learn more, see [Customizing Your Admin Account Settings](/cloud-branch-connector/customizing-your-admin-account-settings).

## August 05, 2022
### Feature Available
#### Gateway Load Balancer Support in AWS
You can deploy Zscaler Cloud Connectors with the Gateway Load Balancer (GWLB) from Amazon Web Services (AWS). GWLB is a combination of network gateway and load balancer that enables horizontal scalability and fault tolerance for Cloud Connector deployments. Admins can deploy GWLB with Zscaler Cloud Connector by using the new GWLB templates for CloudFormation and configurations for Terraform. To learn more, see[ About Cloud Automation Scripts](/cloud-branch-connector/about-cloud-automation-scripts) and [Deploying Cloud Connector with Amazon Web Services](/cloud-branch-connector/deploying-cloud-connector-amazon-web-services).

## June 03, 2022
### Feature Available
#### Update to Cloud Connector Admins Location Scope
Admins can now select None as their Location scope when Allow for Creation of New Locations is enabled in the Add Cloud Connector Admin window. This allows admins to set their scope without creating a location first. After the new location is created, the new location is automatically added to their scope.
[]![The Add Cloud Connector Admin window demonstrating "None" in the Location Scope.](/sites/default/files/downloads/cloud-connector/release-notes/release-upgrade-summary-2022/AddCloudConnectorAdminWindow2.png)
[See image.](#AddCloudConnectorAdmin)
To learn more, see [Adding Cloud Connector Admins](/cloud-branch-connector/adding-cloud-connector-admins).

## May 13, 2022
### Feature Available
#### Advanced Settings
You can now enable the option to import your AWS Account ID and Azure Subscription ID into the Zscaler Cloud Connector Portal from the Advanced Settings page. To learn more, see [About Advanced Settings](/cloud-branch-connector/about-advanced-settings).

### Feature Available
#### Update to Scheduled Upgrades
You can now select a 2-hour window of time to schedule your upgrade for your Cloud or Branch Connector(s).
[]![The View Connectors window highlighting the upgrade schedule. ](/sites/default/files/downloads/cloud-connector/release-notes/release-upgrade-summary-2022/ScheduledUpgrades.png)
[See image.](#UpgradeSchedule)
To learn more, see [About Branch and Cloud Connector Groups](/cloud-branch-connector/about-cloud-connector-group),[ About Branch and Cloud Connector Upgrades](/cloud-branch-connector/about-zscaler-cloud-connector-upgrades), and [Editing Connectors](/cloud-branch-connector/edit-connectors).

### Feature Available
#### Update to Tunnel Encryption
You can now select DTLS or Unencrypted for the tunnel encryption mode to be used when forwarding your connector's traffic to ZIA. The ZIA Tunnel Mode is located in the View Connectors window.
[]![The View Connectors window highlighting ZIA Tunnel Mode.](/sites/default/files/downloads/cloud-connector/release-notes/release-upgrade-summary-2022/TunnelEncryptionMode.png)
[See image.](#TunnelEncryption)
To learn more, see [About Branch and Cloud Connector Groups](/cloud-branch-connector/about-cloud-connector-group),[ About Branch and Cloud Connector Upgrades](/cloud-branch-connector/about-zscaler-cloud-connector-upgrades), and [Editing Connectors](/cloud-branch-connector/edit-connectors).

## March 04, 2022
### Feature Available
#### Update to Add Cloud Connector Role: Addition of Template Permissions
You can now control an admin's access to Templates (Location & Provisioning) in the Add Cloud Connector Role window.
[]![The Add Cloud Connector Role window accessed from the Zscaler Cloud Connector Portal](/sites/default/files/downloads/cloud-connector/release-notes/release-upgrade-summary-2022/AddCloudConnectorRole5.png)
[See image.](#CloudConnectorRole)
To learn more, see [Adding Cloud Connector Roles](/cloud-branch-connector/adding-cloud-connector-roles).
