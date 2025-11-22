# Release Upgrade Summary (2022)
Source: https://help.zscaler.com/zpa/release-upgrade-summary-2022

This article provides a summary of all new features and enhancements per Zscaler cloud for the Zscaler Private Access (ZPA) Admin Portal. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com/).
When Zscaler cloud and Admin Portal updates are deploying, some functionality will not be available until the deployment process completes.

**Clouds:** private.zscaler.com, zpatwo.net, zpabeta.net, zpapreview.net
The following service updates were deployed to private.zscaler.com on

## December 16, 2022
### Feature in Limited Availability
#### Zscaler Client Connector Support for Multiple Tenants
Multiple tenant support is available when establishing Zscaler Tunnels (Z-Tunnels) between Zscaler Client Connector and a ZPA Public Service Edge or ZPA Private Service Edge. This allows Zscaler Client Connector to establish a Z-Tunnel with the tenant, and then establish a separate Z-Tunnel with the partner tenant. The second Z-Tunnel works without any additional setup or configuration. Additionally, access policies include the Client Connector Partner client type option.
To learn more, see [Zscaler Client Connector Windows 4.1 Enhancements and Fixes](/client-connector/client-connector-app-release-summary-2022?applicable_category=Windows&applicable_version=4.1&deployment_date=2022-12-16&id=1440671), [About Client Connector Support for Multiple Tenants](/zpa/about-client-connector-support-multiple-tenants), [About the ZPA Cloud Architecture](/zpa/about-zpa-cloud-architecture), and [Configuring Access Policies](/zpa/configuring-access-policies).

## December 08, 2022
### Feature Available
#### DPI Settings Update for Isolation
An isolation container's DPI settings match the DPI settings of the user's device. Even when the isolation session is moved from one display to another, the isolation container keeps the DPI settings consistent with the new display from that device.
To learn more, see [What is Isolation](/isolation/what-is-isolation)?

## December 05, 2022
### Feature Available
#### Login Hint Option
The Login Hint option is available in the Zscaler Private Access (ZPA) Admin Portal when configuring or editing an IdP. When enabled, the username of the admin or user is sent in the authentication request to the IdP and can be prepopulated on the sign-in page of the external IdP.
To learn more, see [Configuring an IdP for Single Sign-On](/zpa/configuring-idp-single-sign#Collapse2).

### Feature Available
#### ZPA Private Service Edge Platform Details
ZPA Private Service Edge platform (e.g., AWS, Azure, ESXi) details are added in the Private Service Edge Status Diagnostics and the Service Edge page of the ZPA Admin Portal.
[See image.](#serviceEdgePlatformDetail)
To learn more, see [About ZPA Private Service Edges](/zpa/about-zpa-private-service-edges).
[]![Viewing the platform type of a ZPA Private Service Edge](/sites/default/files/downloads/tech-pubs-drafts/zpa-draft-articles/about-client-connector-support-multiple-tenants/zpa-pse-platform-type.png)

## December 02, 2022
### Feature Available
#### ThreatLabZ Controls
Zscaler Private Access (ZPA) provides ThreatLabZ as an Inspection Control option. Zscaler predefined controls published by Zscaler ThreatLabZ protect your business-critical applications against confirmed Common Vulnerabilities and Exposures (CVEs) and zero-day vulnerabilities. You can filter for ThreatLabZ controls in Web Inspection Diagnostics. To learn more, see [About ThreatLabZ Controls](/zpa/about-threatlabz-controls).

## November 29, 2022
### Feature Available
#### App Connector Closest to Application or Closest to User
You can now select the App Connector that is closest to the application when configuring an application segment in the ZPA Admin Portal. ZPA uses this setting to select the App Connector for connectivity.
To learn more, see [Configuring Defined Application Segments](/zpa/configuring-application-segments#define-cmnconfig).

### Feature Available
#### ZPA API Improvements
ZPA APIs include the selectConnectorCloseToApp field to support the App Connector Closest to Application feature.
To learn more, see [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api).

## November 28, 2022
### Feature Available
#### Cloud Updates
The following updates were made to the Zscaler Private Access (ZPA) cloud:
- An optional update was released for the Manager software that improves the internal routing of the distribution of binaries. To learn more, see [About the Manager Software](/zpa/about-manager-software#managerUpgrades).
- Enhancements were made to the ZPA cloud for improving load balancing of application requests across App Connectors. As part of this enhancement, ZPA accounts for CPU, memory, and UDP port consumption for each eligible App Connector, and selects an App Connector with lower utilization by using a probability mass function (PMF) algorithm.
- The ConnectionLogType custom log field is available in the Log Streaming Service (LSS) when using the App Connector Status log type. The custom log field distinguishes between [AppProtection](/zpa/appprotection-private-application-traffic-formerly-inspection) and event logs. To learn more, see [About App Connector Status Log Fields](/zpa/about-connector-status-log-fields).

## November 22, 2022
### Feature Available
#### Disaster Recovery
ZPA supports Disaster Recovery Mode to ensure business continuity in the event of a disaster scenario by providing users with access to critical applications. You can configure and designate application segments, App Connector groups, or ZPA Private Service Edge groups for disaster recovery in the ZPA Admin Portal.
To learn more, see [Understanding Disaster Recovery](/zpa/understanding-disaster-recovery).

## November 14, 2022
### Feature Available
#### OVA Updates
New App Connector and ZPA Private Service Edge OVAs are available to address incorrect recommended VM specifications (e.g., memory and disk space) within the VMware images to align with the Zscaler Help Portal documentation.
To learn more, see [App Connector Deployment Guide for VMware Platforms](/zpa/connector-deployment-guide-vmware-platforms), [App Connector Deployment Guide for Nutanix AHV](/zpa/app-connector-deployment-guide-nutanix-ahv), and [ZPA Private Service Edge Deployment Guide for VMware Platforms](/zpa/service-edge-deployment-guide-vmware).

## November 10, 2022
### Feature Available
#### AWS and Azure Image Updates
New App Connector and ZPA Private Service images are available in the AWS Marketplace to provide enhancements to dependent libraries for Privileged Remote Access (PRA). A new App Connector image is also available in the Microsoft Azure Portal to provide the same improvements.
To learn more, see [App Connector Deployment Guide for Amazon Web Services](/zpa/connector-deployment-guide-amazon-web-services), [ZPA Private Service Edge Deployment Guide for Amazon Web Services](/zpa/service-edge-deployment-guide-amazon-web-services), and [App Connector Deployment Guide for Microsoft Azure](/zpa/connector-deployment-guide-microsoft-azure).

## November 03, 2022
### Feature Available
#### Updates to Terminate All Sessions on Timeout
The option to terminate all running application sessions upon timeout is enabled by default. Existing admins can still enable or disable this option. To learn more, see [About Timeout Policy](/zpa/about-timeout-policy).

## November 02, 2022
### Feature Available
#### Default Inspection Profile
A default inspection profile is included with your Zscaler Private Access (ZPA) account. You can use this default profile as a template to create custom inspection profiles. To learn more, see [About Inspection Profiles](/zpa/about-inspection-profiles).

### Feature Available
#### ZPA API Improvements
An endpoint to get the platform types for a customer is available in the Zscaler Private Acess (ZPA) API Portal. To learn more, see [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api), [Configuring Timeout Policies Using API](/zpa/configuring-timeout-policies-using-api), and [Configuring Client Forwarding Policies Using API](/zpa/configuring-client-forwarding-policies-using-api).

## October 31, 2022
### Feature Available
#### Network Service Update
The network services NTP service with the UDP port 123 and Kerberos Password Change with the TCP and UDP port 464 are available for admins in the Zscaler Private Access (ZPA) Admin Portal. To learn more, see [Configuring Access to Distributed File Servers](/zpa/configuring-access-distributed-file-servers).

### Feature Available
#### Update to Inspection Profiles
You can copy existing inspection profiles on the Inspection Profiles page. To learn more, see [About Inspection Profiles](/zpa/about-inspection-profiles).

### Feature Available
#### ZPA API Improvements
The endpoint to get details of all client types is deprecated and a new endpoint is provided. To learn more, see Configuring [Log Streaming Service Configurations Using API](/zpa/configuring-log-streaming-service-configurations-using-api), [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api), [Configuring Timeout Policies Using API](/zpa/configuring-timeout-policies-using-api), [Configuring Client Forwarding Policies Using API](/zpa/configuring-client-forwarding-policies-using-api), and [Configuring AppProtection Policies Using API](/zpa/configuring-appprotection-policies-using-api).

## October 28, 2022
### Feature Available
#### ZPA API Improvements
The following improvements were made to the Zscaler Private Access (ZPA) cloud service APIs:
- The endpoints marked for deprecation are removed from the Zscaler Private Access (ZPA) API Portal. To learn more, see [ZPA API Improvements](/zpa/release-upgrade-summary-2021?applicable_category=private.zscaler.com&deployment_date=2021-10-20&id=1386016).
- The endpoints to get all certificates or a particular certificate are deprecated. New endpoints to get all certificates, get a particular certificate, create a certificate, and delete a certificate are available. To learn more, see [Configuring Certificates Using API](/zpa/configuring-certificates-using-api).
- The endpoint to dissociate all predefined controls from an inspection profile is deprecated and a new endpoint is available. To learn more, see [Configuring Inspection Profiles Using API](/zpa/configuring-inspection-profiles-using-api).
- An update was released for certificate-related endpoints to use certificate instead of clientlessCertificate in the request endpoints. To learn more, see [Configuring Certificates Using API](/zpa/configuring-certificates-using-api).
- An update was released for the ZPA APIs to change the label of the app-server-controller for the server-related endpoints. To learn more, see [Configuring Servers Using API](/zpa/configuring-servers-using-api).
- The endpoint to get details of all client types is deprecated and a new endpoint is provided. To learn more, see Configuring [Log Streaming Service Configurations Using API](/zpa/configuring-log-streaming-service-configurations-using-api), [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api), [Configuring Timeout Policies Using API](/zpa/configuring-timeout-policies-using-api), [Configuring Client Forwarding Policies Using API](/zpa/configuring-client-forwarding-policies-using-api), and [Configuring AppProtection Policies Using API](/zpa/configuring-appprotection-policies-using-api).
To learn more, see the [API Developers & Reference Guide](/zpa/zpa-api/api-developer-reference-guide).

## October 27, 2022
### Feature Available
#### Cloud Updates
The following updates were made to the Zscaler Private Access (ZPA) Cloud:
- An update was released to address an issue where access to SAN domain names failed when creating a certificate signing request (CSR).
- An update was released that includes the CPU usage for App Connectors in the journalctl logs every minute.

## October 25, 2022
### Feature Available
#### Privileged Approvals and Time Bound Access
Zscaler Private Access (ZPA) provides the ability to define who is able to use the Privileged Remote Access portal for a set window of time. You can manage this in the Privileged Approvals page of the ZPA Admin Portal.
Please contact Zscaler Support to enable this feature for your organization.
[See image.](#PATB)
To learn more, see [About Privileged Approvals](/zpa/about-privileged-approvals).
[]![Configuring a privileged approval in the Add Approval window](/sites/default/files/downloads/zscaler-tech-pubs-style-guide/draft-articles/accessing-privileged-remote-access-portal-draft/Add%20Approval%20window.png)

## October 20, 2022
### Feature in Limited Availability
#### Application Limit Enhancements
An update was released that increases the limits of configurable applications and application segments. Zscaler Client Connector 4.0 is required for this enhancement. To learn more, see [Zscaler Client Connector 4.0 Enhancements and Fixes](/client-connector/client-connector-app-release-summary-2022?applicable_category=Windows&applicable_version=4.0&deployment_date=2022-10-20&id=1418191) and [Downloading Zscaler Client Connector](/client-connector/downloading-zscaler-client-connector).

## October 10, 2022
### Feature Available
#### Cloud Updates
The following updates were made to the Zscaler Private Access (ZPA) cloud:
- An update was released for ZPA Private Service Edges to allow correlation of journal logs between ZPA Private Service Edges and Zscaler Client Connector, Machine Tunnels, and App Connectors.
- An optional update was released for the Manager software to display the Manager software version in the command line interface. To learn more, see [About the Manager Software](/zpa/about-manager-software#managerUpgrades).
- Privileged Remote Access (PRA)-enabled applications using SSH or RDP consoles disconnect when the server group is configured with Dynamic Server Discovery (DSD) turned off. When you map the PRA-enabled application segment to a server with DSD turned off, use the Fully Qualified Domain Name (FQDN) you used for the application segment. This allows the privileged console to connect to the server configured with the FQDN in the server group.

## October 08, 2022
### Feature Available
#### Force Authentication Option for IdP Configuration
A Force Authentication option is available when configuring an IdP. When you enable Force Authentication, users for that specific IdP are required to re-enter their login credentials at the time of authentication, regardless of any session state/cookie for SAML IdP. To learn more, see [Configuring an IdP for Single Sign On](/zpa/configuring-idp-single-sign).

## September 27, 2022
### Feature Available
#### Intelligent Application Segmentation
Zscaler Private Access (ZPA) provides Intelligent Application Segmentation. This feature recommends application segments that can be added to your existing defined application segments. You can manage your recommended application segments on the Recommended Application Segments page in the ZPA Admin Portal.
To learn more, see [About the Applications Dashboard](/zpa/about-applications-dashboard), [About Recommended Application Segments](/zpa/about-recommended-application-segments), and [About Application Segment Settings](/zpa/about-application-segments-settings).

## September 22, 2022
### Feature Available
#### Special Characters in ZPA Isolation Profiles
When configuring or editing ZPA isolation profiles in the Cloud Browser Isolation Portal, a validation message tells you which character symbols entered are invalid. This clarification provides context for why isolation profile names are rejected.
To learn more, see [Creating a ZPA Isolation Profile for Cloud Browser Isolation](/zia/creating-zpa-isolation-profile-cloud-browser-isolation).

## September 20, 2022
### Feature Available
#### TCP Quick Acknowledgement
The option to enable TCP Quick Acknowledgement is available for App Connector Groups in the Zscaler Private Access (ZPA) Admin Portal. ZPA APIs also include new fields to support TCP Quick Acknowledgement at the App Connector Group level.
To learn more, see [Configuring App Connectors](/zpa/configuring-connectors#createconnectorgroup) and [App Connector Group Use Cases](/zpa/app-connector-group-use-cases#AddingFieldDescriptions).

## September 19, 2022
### Feature Available
#### App Connector Platform Details
App Connector platform (e.g., AWS, Azure, ESXi, Docker, Nutanix) details are specified in the App Connector Status Diagnostics and the App Connectors page of the Zscaler Private Access (ZPA) Admin Portal.
[See image.](#image)
[]![App Connector platform details ](/sites/default/files/downloads/zpa-app-connector-platform-details.png)
To learn more, see [About App Connectors](/zpa/about-connectors).

### Feature Available
#### Machine Provisioning Keys Update
The machine provisioning key usage count is no longer needed. As a result, the Provisioning Key Utilization Count column on the Machine Provisioning Keys page has been removed. The Maximum Reuse of Key section in the Add and Edit windows for a Machine Provisioning Key has also been removed. To learn more, see [About Machine Provisioning Keys](/zpa/about-machine-provisioning-keys).

### Feature Available
#### WebSocket Controls
Zscaler Private Access (ZPA) provides WebSocket as an Inspection Control option. This option allows inspection of custom and predefined controls via a WebSocket. You can filter for WebSocket controls in Web Inspection Diagnostics. To learn more, see [About WebSocket Controls](/zpa/about-websocket-controls).

### Feature in Limited Availability
#### Application Segments Inspection Update
Zscaler Private Access (ZPA) supports access to applications with inspection when using private CA certificates. To learn more, see [Configuring Application Segments](/zpa/configuring-application-segments).

## September 14, 2022
### Feature Available
#### Interactive Authentication
Zscaler Private Access (ZPA) provides the ability for users to authenticate when accessing a privileged console in the Privileged Remote Access portal. This enables Network Level Authentication in Windows-based privileged consoles and SSH keys in SSH-based privileged consoles. A pop-up window will appear where the user can log in using their respective credentials. There are different requirements for SSH and RDP protocols; each pop-up window provides the necessary fields for that specific protocol.
To learn more, see [Accessing a Privileged Remote Access Portal](/zpa/accessing-privileged-remote-access-portal). Contact Zscaler Support to enable this feature for your organization.
Application Segments Update
Zscaler Private Access (ZPA) now includes Any as a Connection Security option when configuring an application segment.
To learn more, see [Configuring Application Segments](/zpa/configuring-application-segments).

### Feature Available
#### Updated Images in Microsoft Azure Marketplace, VMware, and Docker Hub
A new App Connector image is available in Microsoft Azure Marketplace, VMware, and Docker Hub to address a security vulnerability. A new ZPA Private Service image is also available in Microsoft Azure Marketplace and VMware to address the same issue. To learn more, see the App Connector Deployment Guides for [Azure](/zpa/connector-deployment-guide-microsoft-azure), [Docker](/zpa/app-connector-deployment-guide-docker), and [VMware Platforms](/zpa/connector-deployment-guide-vmware-platforms), and the ZPA Private Service Edge deployment guides for [Azure](/zpa/service-edge-deployment-guide-microsoft-azure) and [VMware Platforms](/zpa/service-edge-deployment-guide-vmware).

## September 08, 2022
### Feature Available
#### Events and Notifications
Events and Notifications are now supported in the Zscaler Private Access (ZPA) Admin Portal. You can add, view, and filter notifications for events in the ZPA Admin Portal under Administration > Notifications. Event logs are now visible on the Diagnostics page under the Events log type.
To learn more, see [About Events Diagnostics](/zpa/about-events-diagnostics) and [About Notifications.](/zpa/about-notifications)

## September 06, 2022
### Feature Available
#### TLS Encryption for LSS Traffic with Self-Signed Certificates
TLS encryption for Log Streaming Service (LSS) traffic now supports certificates signed by a custom certificate authority (CA). To learn more, see [About the Log Streaming Service](/zpa/about-log-streaming-service).
Resolved Issues
The following issues were resolved:
- A recommended update was released for the App Connector and ZPA Private Service Edge Manager Software to address an OpenSSL vulnerability. To learn more, see [About the Manager Software](/zpa/about-manager-software#managerUpgrades).
- An update was released to address bandwidth utilization issues on ZPA Private Service Edges.
- An update was released to address performance issues on App Connectors.
- An update was released to provide support for mandatory RDP Network Level Authentication regarding Privileged Remote Access (PRA) connections.
- An update was released to provide support for VMware’s Unified Access Gateway (UAG) for use with Browser Access. To learn more, see [Configuring Timeout Policies](/zpa/configuring-timeout-policies).

## August 29, 2022
### Feature Available
#### SCIM API Enhancements
An update was released for the SCIM APIs that changes the value for the id, userId, and groupId fields to universal unique identifier (UUID) format.
To learn more, see [SCIM API Examples](/zpa/scim-api-examples).

### Feature Available
#### Updates to SCIM Sync Logs
An update was released for the SCIM Sync Logs that changes the following: External ID to IdP SCIM Entity ID, External Entity ID to IdP SCIM Entity ID, and Internal ID to Internal Entity ID. There is a new column titled Internal Entity ID in the SCIM Sync Logs table. There is also a new search option, Internal Entity ID, for users and groups in SCIM screens.
To learn more, see [About SCIM Sync Logs](/zpa/about-scim-sync-logs).

## August 24, 2022
### Feature Available
#### AMI Updates
New App Connector and ZPA Private Service Edge AMIs are available to address a security vulnerability issue. To learn more, see [App Connector Deployment Guide for Amazon Web Services](/zpa/connector-deployment-guide-amazon-web-services) and [Service Edge Deployment Guide for Amazon Web Services](/zpa/service-edge-deployment-guide-amazon-web-services).

## August 23, 2022
### Feature Available
#### Arbitrary Domains
The following updates were made to the Zscaler Private Access (ZPA) Admin Portal:
- Zscaler Private Access (ZPA) includes the option to enable arbitrary domains when configuring an IdP for single sign-on. This allows third-party users to use any authentication domain without needing to select an existing domain for clientless access. Please contact Zscaler Support to enable this feature for your tenant. To learn more, see [Configuring an IdP for Single Sign-On](/zpa/configuring-idp-single-sign).
- New session status codes are added to the Zscaler Private Access (ZPA) Admin Portal to indicate Microtunnel (M-Tunnel) failures due to internal limits. To learn more, see [About ZPA Session Status Codes](/zpa/about-zpa-session-status-codes).

### Feature Available
#### Configuration Warning Settings for Application Segments
Application segment configuration warnings can be set in the Application Segments page. By default, configuration warnings appear for application segments, notifying you of an error or existing issue. If you do not want to view configuration warnings for application segments, you can disable them. To learn more, see [Setting Application Segment Configuration Warnings](/zpa/setting-application-segment-configuration-warnings).

### Feature Available
#### Delete Disconnected App Connectors
The ability to delete disconnected App Connectors in bulk is now available on the App Connectors page of the Zscaler Private Access (ZPA) Admin Portal when using the Disconnected filter. To learn more, see [About App Connectors](/zpa/about-connectors) and [Deleting Disconnected App Connectors](/zpa/deleting-disconnected-app-connectors).

### Feature Available
#### Session ID Removal
An update was released that removes Session ID from the Client Sessions and Audit Logs pages in the Zscaler Private Access (ZPA) Admin Portal to address security vulnerabilities. To learn more, see [About Client Sessions](/zpa/about-client-sessions) and [About Audit Logs](/zpa/about-audit-logs).

## August 22, 2022
### Feature Available
#### Manager Software Improvements
An optional update was released for the App Connector and ZPA Private Service Edge Manager software to support improvements to how provisioning keys are handled. To learn more, see [About the Manager Service](/zpa/about-manager-software#managerUpgrades).

## August 02, 2022
### Feature Available
#### Update to Access Policies
Access policies can configure posture profile criteria for the client type machine tunnel. This update requires end-user devices to use Zscaler Client Connector version 3.9 and later. To learn more, see [Configuring Access Policies](/zpa/configuring-access-policies).

## July 12, 2022
### Feature Available
#### Resolved Issues
An update was released to address dashboard issues for some widgets where data was not being shown.

## June 07, 2022
### Feature Available
#### PCAP Support for Remote Troubleshooting
Zscaler Private Access (ZPA) now supports the PCAP command on an App Connector when collecting data for remote troubleshooting. To learn more, see [About Support Information](/zpa/about-support-information).

## June 06, 2022
### Feature Available
#### Admin Portal Update
An update was released for Zscaler Private Access (ZPA) that adds a new session status code for client-based remote assistance when the connection is unavailable. To learn more, see [About ZPA Session Status Codes](/zpa/about-zpa-session-status-codes).

### Feature Available
#### Rate Limit on Microtunnels from Client and Cloud Connectors
The rate limits for Microtunnels for client type management and Cloud Connector management are now available. To learn more, see [Ranges & Limitations](/zpa/ranges-limitations).

### Feature Available
#### Updates to Applications
The TCP Keepalive option was moved from Segment Groups to Application Segments under Client Connector Access to provide enhanced control. To learn more, see [Configuring Application Segments](/zpa/configuring-application-segments#define-clientconnector).

### Feature Available
#### Updates to Remote Troubleshooting
Zscaler Private Access (ZPA) now supports ICMP, TCP, and PCAP commands on ZPA Private Service Edges when collecting data for remote troubleshooting. To learn more, see [About Support Information](/zpa/about-support-information).

### Feature in Limited Availability
#### IP Restrictions on App Connectors
You can now restrict your App Connector Groups by IP address or subnet when configuring App Connectors. To enable this feature, contact Zscaler Support. To learn more, see [Configuring App Connectors](/zpa/configuring-connectors#createconnectorgroup).

## June 02, 2022
### Feature Available
#### ZPA Private Service Edge Dashboard
The Private Service Edge dashboard is now available and includes different metrics, new widgets, and expanded visualization to help you monitor the health and diagnose issues for your organization's ZPA Private Service Edges. To learn more, see [About the Private Service Edge Dashboard](/zpa/about-private-service-edge-dashboard).

## May 17, 2022
### Feature Available
#### ZPA Private Service Edge Metrics in the LSS
ZPA Private Service Edge stats are now supported in the Log Streaming Service (LSS). The new log type can be selected when [configuring a log receiver](/zpa/configuring-log-receiver#Step2). To learn more, see [About the Private Service Edge Metrics Log Fields](/zpa/about-private-service-edge-metrics-log-fields).

## May 09, 2022
### Feature Available
#### Cloud Update
An update was released to address an application routing issue that caused applications with Health Reporting set to None to be routed to disabled App Connectors in certain scenarios.

## April 15, 2022
### Feature Available
#### Resolved Issues
An update was released to address an issue where clicking on an App Connector section in the Health Dashboard resulted in a blank screen.

## April 14, 2022
### Feature Available
#### Admin Portal Updates
The following updates were made to the Zscaler Private Access (ZPA) Admin Portal:
- An update was released that removes the option to allow full access when adding new roles for the Zscaler Client Connector Portal. To learn more, see [Configuring Administrator Roles](/zpa/configuring-administrator-roles).
- An update was released that provides adjustments to active sessions when users with ZPA Administrator role privileges perform operations on other users with ZPA Administrator role privileges. To learn more, see [About Roles](/zpa/about-roles).

## April 13, 2022
### Feature Available
#### CORS and SameSite Authentication and Permissions
The Settings page now includes CORS Request and SameSite Cookie Attribute options for Browser Access applications. These options allow you to request access to selected resources from a different origin and set the SameSite cookie attribute to None for authentication and application cookies. To learn more, see [Configuring Authentication Settings](/zpa/configuring-authentication-settings).
The Roles page now includes the option to enable the CORS and SameSite permission under Authentication. When you enable this permission, the CORS Request and SameSite Cookie Attribute options are included in the Settings page. To learn more, see [Configuring Administrator Roles](/zpa/configuring-administrator-roles).
The Audit Logs page now includes CORS/SameSite as a Resource Type option. To learn more, see [About Audit Logs](/zpa/about-audit-logs).

### Feature Available
#### ZPA Inspection API
Zscaler Private Access (ZPA) now supports customer-facing APIs for managing inspection application segments, inspection policies, inspection controls, and inspection profiles. To learn more, see [Application Segment Use Cases](/zpa/application-segment-use-cases), [Access Policy Use Cases](/zpa/access-policy-use-cases), [Timeout Policy Use Cases](/zpa/timeout-policy-use-cases), [Client Forwarding Policy Use Cases](/zpa/client-forwarding-policy-use-cases), [Inspection Policy Use Cases](/zpa/inspection-policy-use-cases), [Inspection Control Use Cases](/zpa/inspection-control-use-cases), [Inspection Profile Use Cases](/zpa/inspection-profile-use-cases-1), and the [ZPA API Reference Guide](/zpa/zpa-api/api-developer-reference-guide/reference-guide).

## March 28, 2022
### Feature Available
#### AMI, OVA, and RPM Package Updates
New App Connector and ZPA Private Service Edge AMI, OVA, and RPM packages are available to address security vulnerability issues. The RPM package version is 22.137.1 for App Connectors and 22.73.4 for ZPA Private Service Edges. To learn more, see [About the Manager Software](/zpa/about-manager-software#managerUpgrades), [App Connector Deployment Guide for Amazon Web Services](/zpa/connector-deployment-guide-amazon-web-services#Step1_SelectAnAMI), [App Connector Deployment Guide for VMware Platforms](/zpa/connector-deployment-guide-vmware-platforms), [Service Edge Deployment Guide for Amazon Web Services](/zpa/service-edge-deployment-guide-amazon-web-services#wizard), and [Service Edge Deployment Guide for VMware](/zpa/service-edge-deployment-guide-vmware).

## March 18, 2022
### Feature Available
#### Cloud Update
An update was released to address an Open SSL issue.

## March 04, 2022
### Feature Available
#### Cloud and Admin Portal Updates
The following updates were made to the Zscaler Private Access (ZPA) Cloud and Admin Portal:
- An update was released for the Diagnostics pages in the ZPA Admin Portal that allows multiple entries to be separated by a semicolon (;) for all filters that require text input (e.g., Application: Server Port, App Connector: Port). To learn more, see [About User Activity Diagnostics](/zpa/about-user-activity-diagnostics).
[See image.](#multipleEntries)
- The IdP Configuration page now includes expiry icons for IdP certificates. They provide a warning if the IdP certificate has expired or is about to expire. To learn more, see [About IdP Configuration](/zpa/about-idp-configuration#Redicon).
- Application segments that are Source IP Anchoring-enabled now have an information icon in the table on the Application Segment page. You can’t use Double Encryption with Source IP Anchoring-enabled application segments. To learn more, see [About Applications](/zpa/about-applications#SIPAicon) and [Configuring Application Segments](/zpa/configuring-application-segments#define-clientconnector).
[]![Multiple entries separated by a semicolon](/sites/default/files/downloads/zpa-multiple-entries-semicolon.png)

## March 02, 2022
### Feature Available
#### SCIM API Enhancements
An update was released for SCIM APIs that enhances the performance of the GET and PATCH requests to fetch and partially update all groups. To learn more, see [SCIM API Examples](/zpa/scim-api-examples).

### Feature Available
#### Updates to Diagnostics
The Bandwidth Trends table has been renamed to the Total Data Transferred table in User Activity Diagnostics. To learn more, see [About User Activity Diagnostics](/zpa/about-user-activity-diagnostics#trends-totaldatatransferred).

## February 25, 2022
### Feature Available
#### Remote Troubleshooting Enhancements
Zscaler Private Access (ZPA) now supports collecting App Connector and ZPA Private Service Edge data remotely to assist in troubleshooting. You can execute TCP and ICMP ping commands for App Connectors, and DNS and restart commands for ZPA Private Service Edges. To learn more, see [About Support Information](/zpa/about-support-information).

## February 18, 2022
### Feature in Limited Availability
#### App Connector Deployment on Docker
App Connector deployments on Docker platforms are now in limited availability. To learn more, see the [App Connector Deployment Guide for Docker](/zpa/app-connector-deployment-guide-docker).

## February 14, 2022
### Feature Available
#### Admin Portal Update
The Zscaler Client Connector cloud name is now indicated in parentheses when configuring Client Connector Trusted Networks or Client Connector Posture Profiles criteria in access, timeout, or client forwarding policies.
[See image.](#ClientConnectorCloudName)
To learn more, see [About ZPA, ZIA, and Zscaler Client Connector Clouds](/zpa/about-zpa-zia-and-zscaler-client-connector-clouds).
[]![ZIA Cloud Name in Access Policies](/sites/default/files/downloads/zpa/documentation-knowledgebase/applications/application-segments/validating-client-hostname/testCloudExamples.png)

## February 11, 2022
### Feature Available
#### Privileged Remote Access
Zscaler Private Access (ZPA) now provides clientless access to applications that support fully isolated Secure Shell Protocol (SSH) and Remote Desktop Protocol (RDP). You have the ability to define applications for Privileged Remote Access and where they are accessible. You can manage access using the Privileged Portals and Privileged Consoles pages in the ZPA Admin Portal. Privileged Remote Access is supported on [App Connector release 22.31.1](/zpa/app-connector-release-summary-2022?deployment_date=2022-02-08).
To learn more, see [Configuring Application Segments](/zpa/configuring-application-segments), [About Privileged Portals](/zpa/about-privileged-portals), and [About Privileged Consoles](/zpa/about-privileged-consoles).

## February 01, 2022
### Feature Available
#### Lateral Movement Detection with Deception
ZPA now supports integrated application deception, allowing you to use decoys that detect lateral threat movement of active in-network threats that have already bypassed existing defenses. No additional virtual machines (VMs) or hardware is required. To learn more, see [About Applications](/zpa/about-applications), [About App Connectors](/zpa/about-connectors), and [About Access Policy](/zpa/about-access-policy).

### Feature Available
#### ZPA API Updates
The endpoint to get all authentication domains for a customer is now available. To learn more, see [Customer Use Cases](/zpa/customer-use-cases).

## January 31, 2022
### Feature Available
#### ZDX Support for ZPA Private Service Edges
ZPA Private Service Edges now support Zscaler Digital Experience (ZDX) so you can measure performance in the cloud path for internal applications. To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard) and [About ZDX Web Probe Rate Limiting](/zpa/about-zdx-web-probe-rate-limiting).

## January 27, 2022
### Feature Available
#### Resolved Issues
An update was released to address an issue where the Update button on the SCIM Users and SCIM Groups pages did not function properly after selecting some filters.
An update was released to address an issue where the Time Range filter would not function properly on the SCIM Users, SCIM Groups, and Audit Logs pages. The page would remain frozen until you refreshed the page.

## January 26, 2022
### Feature Available
#### Cloud and Admin Portal Updates
The following updates were made to the Zscaler Private Access (ZPA) cloud and Admin Portal:
- An update was released to address an issue where the Service Edge: Name (Public/Private) filter in App Connector Status Diagnostics would only fetch ZPA Public Service Edge details.
- Layout enhancements were made to the Applications, Users, Health, and App Connectors dashboards in the ZPA Admin Portal.
- An update was released for the Diagnostics pages in the ZPA Admin Portal that limits the maximum number of entries to 7 for filters using the Contains operator.

### Feature Available
#### ZPA Inspection
Zscaler Private Access (ZPA) now supports the ability to protect private web applications through the use of inspection controls, inspection profiles, and inspection policies. They work together to restrict user interaction with applications by using pre-approved positive security models. In particular, the inspection controls provide standard and custom protections against application vulnerabilities, such as the OWASP Top 10 issues, non-compliant behavior, and protocol issues.
To learn more, see [About Inspection Controls](/zpa/about-inspection-controls), [About Inspection Profiles](/zpa/about-inspection-profiles), [About Inspection Policy](/zpa/about-inspection-policy), and [About the Inspection Dashboard](/zpa/about-inspection-dashboard).

## January 25, 2022
### Feature Available
#### Updates to SCIM Sync Logs
The SCIM Sync Logs page now includes the Entity Name and Payload Search Entity Name** **as filter options. You can now filter by the user or group name, or by a user's internal ID in the SCIM Sync Payload. The Entity Name also appears as a new column in the table, where you can see the user and group names listed. To learn more, see [About SCIM Sync Logs](/zpa/about-scim-sync-logs).

## January 20, 2022
### Feature Available
#### Admin Portal Update
An update was released to address an issue on the ZPA Diagnostics pages where the Contains filter was not showing entries properly.

## January 13, 2022
### Feature Available
#### Cloud and ZPA API Updates
The following updates were made to the Zscaler Private Access (ZPA) Cloud and API:
- The Log Streaming Service (LSS) now supports Private Service Edge status logs. The new log type can be selected when [configuring a log receiver](/zpa/configuring-log-receiver#Step2).
- The endpoint to get all LSS log formats is now deprecated and is replaced with a new API. To learn more, see [Log Streaming Service Configuration Use Cases](/zpa/log-streaming-service-configuration-use-cases).
- An update was released for ZPA Public Service Edges that adds new ZPA Public Service Edge and ZPA Private Service Edge session status codes for tunnel termination. To learn more, see [About ZPA Session Status Codes](/zpa/about-zpa-session-status-codes).
- Web Probe has been added as a new Connection Type filter in the User Activity Diagnostics page. To learn more, see [About User Activity Diagnostics](/zpa/about-user-activity-diagnostics).
- An update was released that includes the Manager version in the Private Service Edge page of the ZPA Admin Portal.

## January 11, 2022
### Feature Available
#### Remote Troubleshooting on App Connectors
Zscaler Private Access (ZPA) now supports collecting App Connector data remotely to assist in troubleshooting by executing DNS resolve and restart commands on App Connectors when enabled. To learn more, see [About Support Information](/zpa/about-support-information).

### Feature Available
#### ZPA Cloud and Admin Portal Updates
The following updates were made to the Zscaler Private Access (ZPA) Cloud and Admin Portal:
- An update was released that improves the drop-down menus in the Zscaler Private Access (ZPA) Admin Portal when selecting, removing, and viewing items. Users can now navigate the drop-down menus and select or deselect items using Tab and Space on your keyboard.
- An update was released that allows a default ZPA Administrator role to be disabled if another admin role with ZPA Administrator privileges exists. To learn more, see [About Administrators](/zpa/about-administrators).
