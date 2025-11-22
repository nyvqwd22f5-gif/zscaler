# Release Upgrade Summary (2024)
Source: https://help.zscaler.com/cloud-branch-connector/release-upgrade-summary-2024

This article provides a summary of all new features and enhancements for Zscaler Cloud & Branch Connector. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com).

**Clouds:** connector.zscaler.net, connector.zscalerone.net, connector.zscalertwo.net, connector.zscalerthree.net, connector.zscloud.net, connector.zscalerbeta.net
The following service updates were deployed to connector.zscaler.net on

## December 06, 2024
### Feature Available
#### Zero Trust Branch Device SFP Port Support
The ZT800 Zero Trust Branch Device has support for the following copper and fiber small form-factor pluggable (SFP) ports in gateway mode:
- Copper: Finisar - FCLF8522P2BTL
- Cat5e or later Ethernet cable
- Fiber short range (SR): Finisar - FTLF8519P3BNL
- Multi-mode: Aqua fiber optic cable
- Signal distance: 500 meters
- Rate category for the interface type: 1000BASE-SX
- Fiber long range (LR): Finisar - FTLF1318P3BTL
- Single-mode: Yellow fiber optic cable
- Signal distance: 10 kilometers
- Rate category for the interface type: 1000BASE-LX
Additionally, GE1 and GE2 ports are selectable as WAN and LAN ports, hot swappable, and only available for SFP ports.
To learn more, see [Configuring a Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template).

## October 25, 2024
### Feature Available
#### Zscaler Client Connector for VDI Port and Protocol Forwarding Support
Port and protocol forwarding enable granularity in inclusion and exclusion policies by allowing you to enter an IP address:port range or an IP address:port:protocol range.
To learn more, see [Configuring VDI Forwarding Profiles](/cloud-branch-connector/configuring-vdi-forwarding-profiles).

## October 14, 2024
### Feature Available
#### ZPA Access Policy Support for Cloud Connector Workload Groups
Zscaler Cloud Connector supports Zscaler Private Access (ZPA) access policies based on the user-defined tags and cloud attributes mapped to a source workload. Security teams can leverage workload groups to use user-defined and attribute tags in Zscaler Internet Access (ZIA) policies. These workload groups extend to ZPA access policies. Workload group can be a criterion of a ZPA access policy, so Cloud Connector traffic can be matched by workload group criteria.
To learn more, see [About Access Policy](/zpa/about-access-policy), [About Workload Groups](/zia/about-workload-groups), [Understanding Workload Groups](/zia/understanding-workload-groups), and [Configuring Workload Groups](/zia/configuring-workload-groups).

## September 23, 2024
### Feature Available
#### Enhancements to Zero Trust Branch Devices
Several enhancements have been made to Zero Trust Branch Devices. The functionalities include:
- Predefined DNS and forwarding rules added to the Zscaler Cloud & Branch Connector Admin Portal:
- One predefined DNS rule and three predefined traffic forwarding rules, which use Zscaler domains groups, LAN destination groups, WAN destination groups, and app service groups for Zscaler domains, are available.
- The rules are disabled by default, but you can enable them. They are only applicable to Zero Trust Branch Devices deployed in gateway mode and should not be applied to other form factors or Zscaler Cloud Connectors.
- Branch configuration template Dynamic Host Configuration Protocol (DHCP) enhancements made to Zero Trust Branch Devices deployed in gateway mode:
- The default lease time's default value increased from 600 seconds to 86400 seconds.
- The maximum lease time's default value increased from 86400 seconds to 604800 seconds.
- You can specify up to 4 domain names and 4 DNS servers in the DHCP Options section.
- You can configure peer DHCP when high availability (HA) is enabled.
- You can monitor ZIA gateway tunnel and ZPA broker tunnel data for Zero Trust Branch Devices deployed in gateway mode.
- An LED indicator on the front of Zero Trust Branch Devices changes to reflect the progress of a deployment. A solid green light indicates that all services are running, and the device is operating normally.
To learn more, see [About DNS Gateways](/cloud-branch-connector/about-dns-gateways), [About Traffic Forwarding](/cloud-branch-connector/about-traffic-forwarding), [Configuring Traffic Forwarding Rules](/cloud-branch-connector/configuring-traffic-forwarding-rule), [About DNS Policies](/cloud-branch-connector/about-dns-policies), [About Destination IP Groups](/cloud-branch-connector/about-destination-ip-groups), [Configuring a Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template), [Analyzing Branch Connector Details](/cloud-branch-connector/analyzing-branch-connector-details), and [Deploying Zero Trust Branch Devices](/cloud-branch-connector/deploying-zero-trust-branch-devices).

### Feature Available
#### Update to Azure Virtual Machine for Zscaler Cloud Connector
The Microsoft Azure virtual machine (VM) for Zscaler Cloud Connector has been updated to version 24.3.3. This version addresses deployments in environments that contain a large number of network interface resources. To learn more, see [Deploying Zscaler Cloud Connector with Microsoft Azure](/cloud-branch-connector/deploying-zscaler-cloud-connector-microsoft-azure).

## September 17, 2024
### Feature Available
#### Amazon Machine Image (AMI) Availability in AWS China Marketplace
Zscaler Cloud Connector is available in the Amazon Web Services (AWS) China Marketplace. CloudFormation automation deployment templates were updated with support for Amazon Machine Image (AMI) version 24.3.1 in the AWS China (Beijing) region and the AWS China (Ningxia) region.
To learn more, see [Deploying Zscaler Cloud Connector with Amazon Web Services](/cloud-branch-connector/deploying-zscaler-cloud-connector-amazon-web-services).

## September 05, 2024
### Feature in Limited Availability
#### Cloud Connector Virtual Machine Scale Sets with Microsoft Azure
The Zscaler Cloud Connector Microsoft Azure virtual machine (VM) was updated to version 24.3.2 and supports Virtual Machine Scale Sets (VMSS) deployment with Microsoft Azure. In the Zscaler Cloud & Branch Connector Admin Portal, references to Auto Scaling also refer to VMSS. To enable VMSS, contact Zscaler Support.
To learn more, see [About Cloud Provisioning Templates](/cloud-branch-connector/about-cloud-provisioning-templates), [Configuring a Cloud Provisioning Template](/cloud-branch-connector/configuring-cloud-provisioning-template), [About Cloud Connector Groups](/cloud-branch-connector/about-cloud-connector-groups), [Troubleshooting Cloud Connector with Microsoft Azure](/cloud-branch-connector/troubleshooting-cloud-connector-microsoft-azure), [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector), and [Deploying Zscaler Cloud Connector with Microsoft Azure](/cloud-branch-connector/deploying-zscaler-cloud-connector-microsoft-azure).

## September 03, 2024
### Feature Available
#### Zscaler Branch Connector Deployment on the Microsoft Hyper-V Platform
Zscaler Branch Connector now supports deployment on the Microsoft Hyper-V platform.
To learn more, see [Deploying Branch Connector with Hyper-V](/cloud-branch-connector/deploying-branch-connector-hyper-v), [Deploying Branch Connector & App Connector with Hyper-V](/cloud-branch-connector/deploying-branch-connector-app-connector-hyper-v), [Deployment Templates for Zscaler Branch Connector & App Connector](/cloud-branch-connector/deployment-templates-zscaler-branch-connector-app-connector), [Downloading Branch Connector Images](/cloud-branch-connector/downloading-branch-connector-images), [About Branch Configuration Templates](/cloud-branch-connector/about-branch-configuration-templates), and [Configuring a Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template).

## August 30, 2024
### Feature Available
#### Amazon Machine Image (AMI) Availability in AWS China Marketplace
Zscaler Cloud Connector is available in the Amazon Web Services (AWS) China Marketplace. Terraform automation deployment templates were updated with support for Amazon Machine Image (AMI) version 24.3.1 in the AWS China (Beijing) region and the AWS China (Ningxia) region.
To learn more, see [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector).

## August 26, 2024
### Feature Available
#### Deploying Zscaler Cloud Connector with Azure China Marketplace
Zscaler Cloud Connector deployment is available from the Azure China Marketplace. If you are deploying from China, you no longer need to request a private Azure VHD from Zscaler Support. Instead, you can deploy to the Azure China Marketplace through Terraform deployment templates available on GitHub.
To learn more, see [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector) and [Deploying Zscaler Cloud Connector with Microsoft Azure](/cloud-branch-connector/deploying-zscaler-cloud-connector-microsoft-azure).

### Feature Available
#### Support for Amazon Web Services Account Tagging
You can leverage user-defined tags across Amazon Web Services (AWS) accounts in cross-account deployments with workload communications. To learn more, see [About Amazon Web Services Accounts](/cloud-branch-connector/about-partner-integrations), [Adding an Amazon Web Services Account](/cloud-branch-connector/adding-amazon-web-services-account), [About Amazon Web Services Account Groups](/cloud-branch-connector/about-amazon-web-services-account-groups), and [Adding an Amazon Web Services Account Group](/cloud-branch-connector/adding-amazon-web-services-account-group).

## June 21, 2024
### Feature Available
#### Zscaler Client Connector for VDI Name Update
The name of the Zscaler VDI Agent has changed to Zscaler Client Connector for VDI in the Zscaler Cloud & Branch Connector Admin Portal. To learn more, see [What is Zscaler Client Connector for VDI](/cloud-branch-connector/what-zscaler-client-connector-vdi), [Downloading Zscaler Client Connector for VDI](/cloud-branch-connector/downloading-zscaler-client-connector-vdi), [Step-by-Step Configuration Guide for Zscaler Client Connector for VDI](/cloud-branch-connector/step-step-configuration-guide-zscaler-client-connector-vdi), and [Zscaler Client Connector for VDI Management](/cloud-branch-connector/zscaler-client-connector-vdi-management).

### Feature Available
#### Zscaler Cloud & Branch Connector Admin Portal Login Update
The Zscaler Cloud & Branch Connector Admin Portal login process was updated to allow Zscaler to check if ZIdentity is enabled for your account depending on your Login ID.
[See image.](#LoginID)
To learn more, see [Accessing and Navigating the Zscaler Cloud & Branch Connector Admin Portal](/cloud-branch-connector/accessing-navigating-zscaler-cloud-branch-connector-admin-portal) and [Accessing and Navigating the ZIdentity Landing Page](/zslogin/accessing-and-navigating-zslogin-landing-page).
[]![The Login ID field for Zscaler Cloud & Branch Connector](/sites/default/files/downloads/ZscalerCloud%26BranchConnLogin.png)

## June 10, 2024
### Feature Available
#### Update to Zscaler Client Connector for VDI
The Zscaler Client Connector for Virtual Desktop Infrastructure (VDI) application version 1.3.0.14 is available for download from the Zscaler Cloud & Branch Connector Admin Portal, but it does not have 32-bit support. This version contains a new installer parameter, `USEEMBEDDEDBROWSER`, which enables embedded browser support.

## May 24, 2024
### Feature Available
#### Update to Zscaler Client Connector for VDI
The Zscaler Client Connector for Virtual Desktop Infrastructure (VDI) application version 1.2.0.19 is available for download from the Zscaler Cloud & Branch Connector Admin Portal, but it does not have 32-bit support. This version changes the name of the application from Zscaler VDI Agent to Zscaler Client Connector for VDI. It also contains a new installer parameter, `HIDEAPPONUILAUNCH`, which minimizes the application when launching. To learn more, see [Downloading Zscaler VDI Agent](/cloud-branch-connector/downloading-zscaler-vdi-agent).

## May 22, 2024
### Feature Available
#### Update to Azure Virtual Machine for Zscaler Cloud Connector
The Microsoft Azure virtual machine (VM) for Zscaler Cloud Connector has been updated to version 24.3.1. This version contains improvements to the Azure Linux VM Agent.
To learn more, see [Deploying Zscaler Cloud Connector with Microsoft Azure](/cloud-branch-connector/deploying-zscaler-cloud-connector-microsoft-azure) and [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector).

## April 19, 2024
### Feature Available
#### Update to Zscaler VDI Agent
The Zscaler Virtual Desktop Infrastructure (VDI) Agent application version 1.1.0.12 is available for download from the Zscaler Cloud & Branch Connector Admin Portal. This version fixes an issue where the policy was not updating after restarting the Zscaler VDI Agent. It also fixes an issue where the driver was not being installed due to a race condition. Improvements were also made to rate limit reauthentication prompts for users.
To learn more, see [Downloading Zscaler VDI Agent](/cloud-branch-connector/downloading-zscaler-vdi-agent).

## April 01, 2024
### Feature Available
#### Support for App Segments in Traffic Forwarding Rules
App segments allow more granularity and control in traffic forwarding policies. You can enable all app segments, which applies them to a ZPA or Drop traffic forwarding rule.
[See image.](#Applytoallappsegments)
Alternatively, you can disable all app segments and select one of the following:
- Configure neither application segments or segment groups and the rule bypasses this setting.
- Configure a specific application segment and/or segment group and the rule only matches configured segments or groups.
[See image.](#Disableapplytoallappsegments)
To learn more, see [Configuring Traffic Forwarding Rules](/cloud-branch-connector/configuring-traffic-forwarding-rule) and [Ranges & Limitations](/cloud-branch-connector/ranges-limitations).
[]![Apply to all App Segments in the Add Traffic Forwarding Rule window of the Cloud & Branch Connector Admin Portal.](/sites/default/files/downloads/tech-pubs-drafts/cloud-connector-draft-articles/configuring-traffic-forwarding-rules-draft-doc-45415/Apply%20to%20all%20App%20Segments.png)
[]![Disabling the Apply to all App Segments option in the Add Traffic Forwarding Rule window of the Cloud & Branch Connector Admin Portal.](/sites/default/files/downloads/tech-pubs-drafts/cloud-connector-draft-articles/configuring-traffic-forwarding-rules-draft-doc-45415/Disable%20Apply%20to%20all%20App%20Segments.png)

## March 15, 2024
### Feature Available
#### Update to Zscaler VDI Agent
The Zscaler Virtual Desktop Infrastructure (VDI) Agent application version 1.1.0.8 is now available for download from the Zscaler Cloud & Branch Connector Admin Portal. This version fixes an issue where the Zscaler VDI Agent caused packet fragmentation, resulting in failed connections to internal Microsoft Azure endpoints. It also moves the Zscaler VDI Agent's user configuration file to the user's roaming profile folder, which allows you to restore the user-specific configurations using tools such as Citrix UPM or FSLogix.
To learn more, see [Downloading Zscaler VDI Agent](/cloud-branch-connector/downloading-zscaler-vdi-agent).

## March 08, 2024
### Feature Available
#### Wildcard Domains and FQDNs in Traffic Forwarding Rules
You can add wildcard domains and fully qualified domain names (FQDNs) as criteria for traffic forwarding rules in the Zscaler Cloud & Branch Connector Admin Portal. The wildcard domain and FQDN feature require you to ensure firewalls do not restrict communication between grouped Cloud or Branch Connectors.
To learn more, see [Configuring Traffic Forwarding Rules](/cloud-branch-connector/configuring-traffic-forwarding-rule), [Configuring Destination IP Groups](/cloud-branch-connector/configuring-destination-ip-groups), [Troubleshooting Cloud Connector with Amazon Web Services](/cloud-branch-connector/troubleshooting-cloud-connector-amazon-web-services), [Troubleshooting Cloud Connector with Microsoft Azure](/cloud-branch-connector/troubleshooting-cloud-connector-microsoft-azure), and [Troubleshooting Cloud Connector with Google Cloud Platform](/cloud-branch-connector/troubleshooting-cloud-connector-google-cloud-platform).

## March 01, 2024
### Feature Available
#### Support for Sublocations
Zscaler Cloud Connector and Zscaler Branch Connector sublocations configured within the ZIA Admin Portal (Administration > Location Management) can now be selected when configuring traffic forwarding rules and DNS filtering rules within the Zscaler Cloud & Branch Connector Admin Portal. Additionally, Cloud & Branch Connector sublocations can be selected when configuring policies within the ZPA Admin Portal. Sublocations enable Cloud & Branch Connector to create new locations that reference IP addresses encapsulated within Cloud & Branch Connector tunnels.
To learn more, see [About Locations](/cloud-branch-connector/about-locations), [Understanding Sub-Locations](/zia/understanding-sub-locations), [Configuring Sub-Locations](/zia/configuring-sub-locations), [Configuring Traffic Forwarding Rules](/cloud-branch-connector/configuring-traffic-forwarding-rule), and [Configuring the DNS Filtering Rule](/cloud-branch-connector/configuring-dns-filtering-rule).

## February 28, 2024
### Feature Available
#### DNS Enhancements for Zscaler Cloud & Branch Connector
Zscaler Cloud & Branch Connector supports DNS gateways and split DNS policies, which provide enhancements to DNS features. To learn more, see [About DNS Gateways](/cloud-branch-connector/about-dns-gateways), [Configuring a DNS Gateway](/cloud-branch-connector/configuring-dns-gateway), [Configuring the DNS Filtering Rule](/cloud-branch-connector/configuring-dns-filtering-rule), and [Modifying the Default DNS Control Rule](/cloud-branch-connector/modifying-default-dns-control-rule).

### Feature Available
#### Endpoints for Managing Cloud & Branch Connector Interface and Routes
New endpoints are added to extend programmatic access for managing Cloud & Branch Connector interfaces and routes. The following endpoints allow you to create, update, delete, and retrieve interfaces and routes:
- [Interface APIs](#interfaceendpoints)
- [Route APIs](#routeendpoints)
To learn more about each endpoint, see the [API Reference Guide](/cloud-branch-connector/cloud-branch-connector-groups).
- []`GET /ecgroup/{ecgroupId}/vm/{vmId}/intf`
- `POST /ecgroup/{ecgroupId}/vm/{vmId}/intf`
- `GET /ecgroup/{ecgroupId}/vm/{vmId}/intf/{intfId}`
- `PUT /ecgroup/{ecgroupId}/vm/{vmId}/intf/{intfId}`
- `DELETE /ecgroup/{ecgroupId}/vm/{vmId}/intf/{intfId}`
- []`GET /ecgroup/{ecgroupId}/vm/{vmId}/route`
- `POST /ecgroup/{ecgroupId}/vm/{vmId}/route`
- `DELETE /ecgroup/{ecgroupId}/vm/{vmId}/route`
- `GET /ecgroup/{ecgroupId}/vm/{vmId}/route/{ecRouteId}`
- `PUT /ecgroup/{ecgroupId}/vm/{vmId}/route/{ecRouteId}`
- `DELETE /ecgroup/{ecgroupId}/vm/{vmId}/route/{ecRouteId}`

### Feature Available
#### Zero Trust Branch Devices as a Gateway
Zero Trust Branch Devices (ZT400, ZT600, and ZT800) can be deployed in gateway mode. Gateway mode deployment provides the following functionalities:
- Multiple wide area network (WAN) uplinks
- Internet service provider (ISP) uplink path monitoring with quality score
- Multiple Layer 3 local area network (LAN) interfaces
- Virtual local area network (VLAN) tags (802.1q encapsulation)
- Dynamic host configuration protocol (DHCP) server and client enablement
- Static routing
- WAN redundancy (Active/Active or Active/Standby)
- LAN redundancy (High Availability per VLAN interface)
- Device redundancy (High Availability for WAN interface failure)
- LAN-to-LAN traffic filtering
- DNS security through DNS gateways and DNS policy
- Application-aware path selection based on uplink quality score
- Enhanced monitoring and visibility of Zero Trust Branch Devices
- Integrated App Connector deployment servicing all LAN ports
- Ability to edit Zero Trust Branch Device configurations after deployment
To enable this feature, contact Zscaler Support.
To learn more, see [Configuring a Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template), [Configuring Traffic Forwarding Rules](/cloud-branch-connector/configuring-traffic-forwarding-rule), [Configuring a DNS Gateway](/cloud-branch-connector/configuring-dns-gateway), [Configuring the DNS Filtering Rule](/cloud-branch-connector/configuring-dns-filtering-rule), [Analyzing Branch Connector Details](/cloud-branch-connector/analyzing-branch-connector-details), [Installing Zero Trust Branch Devices](/cloud-branch-connector/installing-zero-trust-branch-devices), and[ Deploying Zero Trust Branch Devices](/cloud-branch-connector/deploying-zero-trust-branch-devices).

## February 21, 2024
### Feature Available
#### Download Zscaler VDI Agent from the Zscaler Cloud & Branch Connector Admin Portal
The Zscaler Virtual Desktop Infrastructure (VDI) Agent is available for download from the Zscaler Cloud & Branch Connector Admin Portal. You can download the latest version, 1.0.0.95, or one of the older versions still available for download.
[]![The Zscaler VDI Agent download page in the Cloud & Branch Connector Admin Portal.](/sites/default/files/downloads/cloud-branch-connector/zscaler-vdi-agent-management/downloading-zscaler-vdi-agent/VDIAgent_App-Download_0.png)
[See image.](#ZSVDIADownload)
To learn more, see [Downloading Zscaler VDI Agent](/cloud-branch-connector/downloading-zscaler-vdi-agent).
