# Release Upgrade Summary (2023)
Source: https://help.zscaler.com/zpa/release-upgrade-summary-2023

This article provides a summary of all new features and enhancements per Zscaler cloud for the ZPA Admin Portal. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com/).
When Zscaler cloud and Admin Portal updates are deploying, some functionality will not be available until the deployment process completes.

**Clouds:** private.zscaler.com, zpatwo.net, zpabeta.net, zpapreview.net
The following service updates were deployed to private.zscaler.com on

## December 18, 2023
### Feature Available
#### Session Proctoring
ZPA allows you to join, monitor, and share live privileged sessions. You can enable these Session Proctoring options when you create a privileged capabilities policy. The live privileged sessions can be managed on the Live tab on the Privileged Sessions page. This feature is only available with a license. Contact your account manager for more information.
To learn more, see [Configuring Privileged Capabilities Policies](/zpa/configuring-privileged-capabilities-policies), [Accessing Privileged Sessions](/zpa/accessing-privileged-sessions), and [Accessing a Privileged Remote Access Portal](/zpa/accessing-privileged-remote-access-portal).
Privileged Consoles Update
The default limitation for privileged consoles is 10. The maximum number of privileged consoles is 6,000, based on licenses.
To learn more, see [Ranges & Limitations](/zpa/ranges-limitations).

## December 12, 2023
### Feature Available
#### App Connector Deployment on OpenShift
App Connector deployment on the Red Hat OpenShift platform is available. To learn more, see [App Connector Deployment Guide for OpenShift](/zpa/app-connector-deployment-guide-openshift).

## December 11, 2023
### Feature Available
#### Customer Activation of Intelligent Application Segmentation
An update was made to let customers activate the ZPA Intelligent Application Segmentation feature on the Recommended Application Segments page.
[See image](#activate-recommendations).
To learn more, see[ About Recommended Application Segments](/zpa/about-recommended-application-segments). If you are interested in this feature, contact Zscaler Support.
[]![Activate Recommendations button in Recommended Application Segments tab](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2023/activate-recommendation-button-in-recommended-tab-03.png)

### Feature Available
#### Manager Software Updates
A recommended update was released for the App Connector and ZPA Private Service Edge software that includes the following updates:
- New App Connector and ZPA Private Service Edge RPM packages to provide support for Red Hat Enterprise Linux 7.x and 8.x.
- Support for DigiCert G2 certificates.
You can download the Manager Software for [App Connector](/zpa/connector-deployment-guide-centos-oracle-and-redhat#Deployment) or [ZPA Public Service Edges](/zpa/service-edge-deployment-guide-centos-oracle-and-redhat#step3deploy) from our repository. To learn more, see [Understanding the Manager Software](/zpa/about-manager-software#managerUpgrades), [App Connector Deployment Guide for CentOS, Oracle, and Redhat](/zpa/connector-deployment-guide-centos-oracle-and-redhat), and [Service Edge Deployment Guide for CentOS, Oracle, and Redhat](/zpa/service-edge-deployment-guide-centos-oracle-and-redhat).

## December 01, 2023
### Feature Available
#### Status Column Removal
An update was released that removes the Status column in the tables for the Branch Connector, Branch Connector Groups, Cloud Connector, and Cloud Connector Group pages of the ZPA Admin Portal.
To learn more, see [About Branch Connectors](/zpa/about-branch-connectors), [About Branch Connector Groups](/zpa/about-branch-connector-groups), [About Cloud Connectors](/zpa/about-cloud-connectors), and [About Cloud Connector Groups](/zpa/about-cloud-connector-groups).

## November 30, 2023
### Feature Available
#### Updates to the App Connector Dashboard
The App Connector dashboard includes a new widget: Peak Inspection Tunnel Count in Past 14 Days. The User Activity Diagnostics page has a new filter for Logs: Inspection Status.
To learn more, see [About the App Connector Dashboard](/zpa/about-app-connector-dashboard) and [About User Activity Diagnostics](/zpa/about-user-activity-diagnostics).

## November 17, 2023
### Feature Available
#### KVM Image Support
New App Connector and ZPA Private Service Edge images are available in the KVM qcow2 format to support Equinix Network Edge.

### Feature Available
#### VMware Image Updates
New App Connector and ZPA Private Service Edge images are available in VMware that address routine security patches.
To learn more, see [App Connector Deployment Guide for VMware Platforms](/zpa/connector-deployment-guide-vmware-platforms), [App Connector Deployment Guide for Nutanix AHV](/zpa/app-connector-deployment-guide-nutanix-ahv), and [ZPA Private Service Edge Deployment Guide for VMware Platforms](/zpa/service-edge-deployment-guide-vmware).

## November 14, 2023
### Feature Available
#### Domain Name Changes for Email Notifications
An update was released for email notifications that changed the sender email domain to no-reply@private.zscaler.com.
To learn more, see [About Notifications](/zpa/about-notifications).

### Feature in Limited Availability
#### Browser Protection Updates
You can set fingerprint timeouts for sessions within a Browser Protection profile. You can also select a JA3 hash for a Browser Protection profile. You have the option to select the User Portal criteria for a Browser Protection policy. This option allows you to assign user portals to inspect traffic with Browser Protection. You can review the data for these features on the Clientless Access Diagnostics page.
To learn more, see [Configuring AppProtection Profiles](/zpa/configuring-appprotection-profiles), [Configuring Browser Protection Policies](/zpa/configuring-browser-protection-policies), and [Accessing Clientless Access Diagnostics](/zpa/about-clientless-access-diagnostics).

## November 07, 2023
### Feature Available
#### RPM Package and Manager Software Updates
A recommended update was released that includes:
- Updated App Connector and ZPA Private Service Edge RPM packages for Red Hat Enterprise Linux 7.x and 8.x.
- Support for App Connector deployment on the Red Hat OpenShift Platform.
To learn more, see [Understanding the Manager Software](/zpa/about-manager-software#managerUpgrades), [App Connector Deployment Guide for CentOS, Oracle, and Red Hat](/zpa/connector-deployment-guide-centos-oracle-and-redhat), and [Service Edge Deployment Guide for CentOS, Oracle, and Red Hat](/zpa/service-edge-deployment-guide-centos-oracle-and-redhat), and [App Connector Deployment Guide for OpenShift](/zpa/app-connector-deployment-guide-openshift).

### Feature Available
#### Troubleshooting Enhancements
An update was released for App Connectors and ZPA Private Service Edges to further improve the effectiveness of the current troubleshooting procedures available to customers.
To learn more, see [App Connector Managing & Troubleshooting](/zpa/app-connector-management/app-connector-managing-troubleshooting) and [Private Service Edge Managing & Troubleshooting](/zpa/private-service-edge-management/private-service-edge-managing-troubleshooting).

## October 30, 2023
### Feature Available
#### Resolved Issues
A fix was released to address an issue where the Control Connection Disconnected and CPU Starvation events were not being triggered properly.
To learn more, see [Viewing and Managing Events Diagnostics](/zpa/viewing-and-managing-events-diagnostics) and [Configuring Notifications](/zpa/configuring-notifications)

## October 25, 2023
### Feature Available
#### Auto Delete for App Connectors
You can configure Auto Delete in your App Connector settings. This feature removes App Connectors with a disconnected status after a set number of days.
To learn more, see [Configuring App Connectors Page Settings](/zpa/configuring-app-connectors-settings).

### Feature Available
#### Service Edge Renamed to Private Service Edge
An update was released that renamed the labels for Service Edge to Private Service Edge in the ZPA Admin Portal. This doesn’t change any current functionality.
To learn more, see [Accessing and Navigating the ZPA Admin Portal](/zpa/accessing-and-navigating-zpa-admin-portal#NavigatingZPAAdminPortal).

### Feature Available
#### ZPA API Improvements
The ability to configure Auto Delete for disconnected App Connectors is available via the cloud service API.
To learn more, see [Configuring Auto Delete for Disconnected App Connectors Using API](/zpa/configuring-auto-delete-disconnected-app-connectors-using-api).

### Feature Available
#### ZPA API Improvements to Support Search by Policy Rule Action
The ability to search by policy rule action is supported for the endpoint that gets the policy set ID by policy type.
To learn more, see [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api), [Configuring Client Forwarding Policies Using API](/zpa/configuring-client-forwarding-policies-using-api), [Configuring Isolation Policies Using API](/zpa/configuring-isolation-policies-using-api), [Configuring AppProtection Policies Using API](/zpa/configuring-appprotection-policies-using-api), and the [Reference Guide](/zpa/policy-set-controller).

## October 09, 2023
### Feature Available
#### Flattened PDF for File Transfers in Isolation
Admins can enable per ZPA isolation profile how the user downloads file transfers. Users in isolation can download a file as a flattened PDF version, which renders it with no active content, or as the original file.
[See image.](#flatpdf)
To learn more, see [Creating Isolation Profiles for ZPA](/isolation/creating-isolation-profiles-zpa) and [Transferring and Viewing Files in Isolation](/isolation/transferring-and-viewing-files-cloud-browser-isolation).
[![Enable or disable the options in the Security section.](/sites/default/files/downloads/isolation/profiles/zia-profiles/creating-zia-isolation-profile-isolation/ZIA_Add-Profile_Security_allow-file-transfers_iso-to-computer_enabled_Flat-PDF-selection_RN.png)
]

### Feature Available
#### Persisting Isolation Banner
Isolation banners are displayed for a period of 15 seconds before they disappear. Administrators can enable the banners per ZPA isolation profile to persist throughout the duration of the isolation session without disappearing.
[See image.](#persist-banner)
To learn more, see [Adding a Banner Theme for the Isolation End User Notification in ZPA](/isolation/adding-banner-theme-isolation-end-user-notification-zpa) and [Creating Isolation Profiles for ZPA](/isolation/creating-isolation-profiles-zpa).
[![Enable or disable the options available.](/sites/default/files/downloads/isolation/profiles/zia-profiles/editing-your-isolation-profile-zia/persist-banner.png)
]

### Feature Available
#### Persisting Isolation URL Bar
Admins can enable the option per ZPA isolation profile for the user to see a persistent isolation URL bar during their isolation session.
[See image.](#persist-bar)
To learn more, see [Creating Isolation Profiles for ZPA](/isolation/creating-isolation-profiles-zpa) and [Editing Your Isolation Profile for ZPA](/isolation/editing-your-isolation-profile-zpa).
[![Enable or disable the option.](/sites/default/files/downloads/isolation/profiles/zia-profiles/editing-your-isolation-profile-zia/ZIA_Add-Isolation-Profile_Iso-UX_Persist-Isolation-URL-Bar_squircle.png)
]

### Feature Available
#### Watermark for Isolation User Experience
The watermarking capability for isolation allows admins to create a watermark to display whenever the user enters a web page in isolation. Admins can enable watermarking per isolation profile and choose to display the user ID, date and timestamp, and a custom message.
[See image.](#watermarking)
To learn more, see [Creating Isolation Profiles for ZPA](/isolation/creating-isolation-profiles-zpa) and [Transferring and Viewing Files in Isolation](/isolation/transferring-and-viewing-files-cloud-browser-isolation).
[![Go to Isolation Experience and enable the desired toggles for Watermarking.](/sites/default/files/downloads/isolation/profiles/zia-profiles/creating-zia-isolation-profile-isolation/ZIA_Add-Isolation-Profile_Iso-UX_Watermarking.png)
]

## October 02, 2023
### Feature Available
#### Application Segment Limit Enhancements
An update was released that increases the limit of Source IP Anchoring-enabled application segments.
To learn more, see [Ranges & Limitations](/zpa/ranges-limitations).

## September 25, 2023
### Feature Available
#### Updates to SCIM Users and SCIM Groups
The following updates were made to the SCIM Users and SCIM Groups pages in the ZPA Admin Portal:
- The total number of users and the number of active users associated with the SCIM group are visible on the SCIM Groups page of the ZPA Admin Portal. To learn more, see [About SCIM Groups](/zpa/about-scim-groups).
- The ability to filter by SCIM attributes is available on the SCIM Users page of the ZPA Admin Portal. To learn more, see [About SCIM Users](/zpa/about-scim-users).

### Feature Available
#### ZPA API Improvements
An update was released that includes the ability to sort when fetching SCIM groups using the ZPA cloud service API.
To learn more, see [Obtaining SCIM Group Details Using API](/zpa/obtaining-scim-group-details-using-api).
Resolved Issues
An update was released to fix an issue where the startIndex and count attributes returned values for pageNumber when using the ZPA cloud service API to fetch SCIM users or groups.

## September 19, 2023
### Feature Available
#### Mobile User Experience in Isolation for ZPA
Isolation is supported on iOS and Android mobile platforms. When traffic is generated from a mobile browser and triggers a policy on ZPA that has the action as Isolate, that traffic is isolated.
To learn more, see [Mobile User Experience in Isolation](/isolation/mobile-user-experience-isolation) and [About Isolation Policy](/zpa/about-isolation-policy).

### Feature in Limited Availability
#### ZPA Private Service Edge Resiliency
An update was released that allows an extension of the user's authentication when the ZPA Private Service Edge cannot communicate to the ZPA cloud during a network outage.
[See image.](#maxAge)
Contact Zscaler Support to enable this feature for your organization.
To learn more, see [Configuring Authentication Settings](/zpa/configuring-authentication-settings).
[]![Settings page in the ZPA Admin Portal](/sites/default/files/downloads/zpa-settings-page-max-age-for-authentication.png)

## September 15, 2023
### Feature Available
#### Privileged Consoles Update
SSH-enabled privileged consoles in Privileged Remote Access (PRA) support the following modern elliptic-curve host key algorithms:
- ecdsa-sha2-nistp521
- ecdsa-sha2-nistp384
- ecdsa-sha2-nistp256
To learn more, see [Configuring Privileged Consoles](/zpa/configuring-privileged-consoles#LinkType).

## September 14, 2023
### Feature Available
#### Bypass ZPA During Reauthentication
The option to bypass ZPA during reauthentication is available when configuring an application segment. The same option is also available using the Zscaler cloud service API. This feature requires Zscaler Client Connector version 4.3 or later.
[See image.](#bypassDuringReauth)
To learn more, see [Configuring Defined Application Segments](/zpa/configuring-application-segments) and [Configuring Application Segments Using API](/zpa/application-segment-use-cases).
[]![Configuring an application segment](/sites/default/files/downloads/zpa-configuring-app-segments-client-connector.png)

## September 11, 2023
### Feature in Limited Availability
#### AppProtection Log Enhancements
Raw AppProtection logs show if malicious strings are present and display the matched malicious strings in the App Connector.

## September 05, 2023
### Feature Available
#### FQDN Update
An update was released to have ZPA check the uniqueness of the FQDN across user portals, Privileged Remote Access portals, and Browser Access applications.

## September 01, 2023
### Feature Available
#### Privileged Remote Access Scalability
The concurrency restrictions for Privileged Remote Access (PRA) privileged sessions for each App Connector have been removed. To use the File Transfer feature in a VNC privileged console for PRA, you need to configure SSH on the target system on port 22. File Transfer leverages the SFTP channel using SSH to transfer files. If you are using a cloud with FIPS enabled, the Connection Security options NLA and Windows aren’t supported with PRA.
To learn more, see [Configuring Defined Application Segments](/zpa/configuring-application-segments) and [Configuring Privileged Capabilities Policies](/zpa/configuring-privileged-capabilities-policies).

### Feature Available
#### Provisioning Keys Update
You can download App Connector provisioning keys and ZPA Private Service Edge provisioning keys to your system.
To learn more, see [About App Connector Provisioning Keys](/zpa/about-connector-provisioning-keys) and [About ZPA Private Service Edge Provisioning Keys](/zpa/about-zpa-service-edge-provisioning-keys).

## August 31, 2023
### Feature Available
#### Session Recording
ZPA allows you to record activity in a privileged console session for Privileged Remote Access (PRA). You can enable this feature when creating a privileged capabilities policy. The recordings are available for review on the Privileged Sessions page. This feature is only available with a license, contact your account manager for more information.
To learn more, see [Configuring Privileged Capabilities Policies](/zpa/configuring-privileged-capabilities-policies), [Accessing Privileged Sessions](/zpa/accessing-privileged-sessions), and [Accessing a Privileged Remote Access Portal](/zpa/accessing-privileged-remote-access-portal).

## August 30, 2023
### Feature Available
#### Forwarding Traffic from ZPA Profiles to ZIA in Isolation
When this feature is enabled on an isolation profile, any web traffic that a ZPA client doesn't forward to the Microtunnel is forwarded to ZIA instead of going directly to the internet. The user is prompted to log in to ZIA if their corresponding company information exists in ZIA. If it doesn't, they are asked to authenticate to ZIA inside the ZPA session. All traffic forwarded via ZIA is enforced with the matching ZIA policies and is logged by ZIA.
This feature can also be used to extend secure access to Sanctioned SaaS applications from unmanaged devices. To learn more, see [Secure SaaS Access from Unmanaged Devices via User Portal](/isolation/secure-saas-access-unmanaged-devices-user-portal).
[See image.](#forward-traffic)
To learn more, see [Creating Isolation Profiles for ZPA](/isolation/creating-isolation-profiles-zpa) and [Forwarding Traffic from ZPA Profiles to ZIA in Isolation](/isolation/forwarding-traffic-zpa-profiles-zia-isolation).
[![Enable to forward traffic via ZIA instead ZPA .](/sites/default/files/downloads/isolation/profiles/zpa-profiles/forwarding-traffic-zpa-profiles-zia-isolation/Add-Isolation-Profile_traffic-forwarding.png)
]

### Feature Available
#### Inspect with ZIA
You can inspect the Microtunnel traffic of an application segment from ZPA, using Zscaler Internet Access (ZIA). Inspection for application segments is also available using the ZPA cloud service API.
To learn more, see [About Applications](/zpa/about-applications), [Configuring Application Segments](/zpa/configuring-application-segments), [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api), and [Configuring Segment Groups Using API](/zpa/configuring-segment-groups-using-api).

### Feature Available
#### User Risk Scores
ZPA lets you view user risk scores and configure them as a criteria type in access policy rules to further enhance role-based access control. You can edit and override user risk scores and expiration dates to adjust user risk scores to your organization's needs.
To learn more, see [About User Risk Scores](/zpa/about-user-risk-scores), [Editing and Overriding User Risk Scores](/zpa/editing-user-risk-scores), and [Configuring Access Policies](/zpa/configuring-access-policies).

## August 29, 2023
### Feature Available
#### ZPA Integration with ZSLogin
The following updates were made to support the Zscaler Private Access (ZPA) integration with ZSLogin:
- For ZSLogin-enabled users:
- The SAML Attributes and IdP Configuration pages are hidden within the ZPA Admin Portal. To learn more, see [About SAML Attributes](/zpa/about-saml-attributes) and [About IdP Configuration](/zpa/about-idp-configuration).
- The SAML and SCIM Attributes criteria are replaced with User and Group Attributes when configuring policy rules. To learn more, see [Policies](/zpa/policies).
- The SAML and SCIM Attributes options are replaced with User and Group Attributes when defining a streaming policy on your log receiver. To learn more, see [Configuring a Log Receiver](/zpa/configuring-log-receiver#Step2).
- The SCIM Users, SCIM Groups, and SAML Attributes fields are replaced with ZSLogin Users, User Groups, and User Attributes in the user activity diagnostics logs. To learn more, see [Accessing User Activity Diagnostics](/zpa/accessing-user-activity-diagnostics#user).
- A new resource type called User Attribute was added to the Audit Logs. To learn more, see [About Audit Logs](/zpa/about-audit-logs).

## August 28, 2023
### Feature Available
#### Internal ZDX Caching Optimizations
An update was released for App Connectors and ZPA Private Service Edges that includes internal ZDX caching optimizations.

### Feature Available
#### Private Service Edge Memory Requirements
An update was released for ZPA Private Service Edges that prevents them from starting when physical memory on the VM is less than 2 GB. Ensure you follow [the recommended guidelines when deploying ZPA Private Service Edges](/zpa/zpa-service-edge-deployment-prerequisites#SpecsSizing). Additionally, [monitor the memory usage and performance of your ZPA Private Service Edges](/zpa/monitoring-private-service-edge-performance). Contact Zscaler Support to learn more.

### Feature Available
#### ZDX Cloud Path Optimizations
An update was released for App Connectors to provide support for ZDX cloud path optimizations for private applications. Optimizations include:
- A significant acceleration of the MTR implementation process without compromising accuracy.
- A reduction of probing time to enhance overall performance.

## August 24, 2023
### Feature Available
#### AWS, Azure, and Docker Hub Image Updates
New App Connector and ZPA Private Service Edge images are available in AWS Marketplace, Microsoft Azure Marketplace, and Docker Hub to address routine security vulnerabilities.
To learn more, see the App Connector Deployment Guides for [AWS](/zpa/connector-deployment-guide-amazon-web-services), [Azure](/zpa/connector-deployment-guide-microsoft-azure), and [Docker](/zpa/app-connector-deployment-guide-docker), and the ZPA Private Service Edge Deployment Guides for [AWS](/zpa/service-edge-deployment-guide-amazon-web-services) and [Azure](/zpa/service-edge-deployment-guide-microsoft-azure).

## August 22, 2023
### Feature Available
#### Intelligent Application Segmentation
An update was made to the Zscaler Private Access (ZPA) Intelligent Application Segmentation feature to let users select the SCIM Attribute (SCIM Group or SCIM Department) to display for recommended users on the Recommended Application Segments page.
[See image](#scimattributedropdown).
To learn more, see [About Application Segments Settings](/zpa/about-application-segments-settings) and [About Recommended Application Segments](/zpa/about-recommended-application-segments).
[]![SCIM Attribute drop-down](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2023/SCIMAttributeDrop-down-02.png)

## August 07, 2023
### Feature Available
#### Active Directory Protection
ZPA provides Active Directory (AD) Protection inspection for protocol traffic (Kerberos, SMB, and LDAP). You can view the log and trend data results on the AD Protection Diagnostics page. You can enable AD Protection when configuring an application segment.
To learn more, see [Accessing AD Protection Diagnostics](/zpa/about-ad-protection-diagnostics) and [Configuring Application Segments](/zpa/configuring-application-segments#ADProtection).

### Feature Available
#### ZPA API Improvements
Active Directory (AD) Protection to provide inspection of protocol traffic (LDAP, SMB, and Kerberos) is supported for the ZPA cloud service APIs.
To learn more, see [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api) and [Configuring AppProtection Policies Using API](/zpa/configuring-inspection-policies-using-api).

## August 01, 2023
### Feature Available
#### Adaptive Access
An enhancement was released to reevaluate access when there are changes to posture profiles.
To learn more, see [About Device Posture Profiles](/client-connector/about-device-posture-profiles).

### Feature Available
#### App Connectors to Resolve Wildcard CNAME Records
An update was released for App Connectors to resolve wildcard CNAME records.

### Feature Available
#### Client Connections with Geofencing
An enhancement was released to let clients connect or remain connected to ZPA Public Service Edges within a geofence-enforced region.

### Feature Available
#### Events and Notifications Enhancements
An update was released to add connectivity and upgrade metrics to the events and notifications for when the control connection of an App Connector or ZPA Private Service Edge disconnects. A new event for App Connector CPU starvation was also added.
To learn more, see [Viewing and Managing Events Diagnostics](/zpa/viewing-and-managing-events-diagnostics) and [Configuring Notifications](/zpa/configuring-notifications).

### Feature Available
#### Manager Software Update
An optional update was released for App Connector and ZPA Private Service Edge Manager software to support the full list of OS trusted certificate authority (CA) bundles for updating components.
To learn more, see [Understanding the Manager Software](/zpa/about-manager-software#managerUpgrades).

### Feature Available
#### Role-Based Administration Control
The ability to delegate role-based administration control is available in the ZPA Admin Portal via a Microtenant. A Microtenant is a delegated responsibility that is defined by an authentication domain and assigned by an admin with Microtenant administrator privileges. This allows admins to manage application segments, segment groups, App Connectors, App Connector groups, etc.
Contact Zscaler Support to enable this feature for your organization.
To learn more, see [About Microtenants](/zpa/about-microtenants).

### Feature Available
#### ZPA API Improvements
The following improvements were made to the Zscaler Private Access (ZPA) cloud service APIs:
- Customer-facing APIs for managing Microtenants are available in the ZPA API Portal.
- The option to move application segments from one Default tenant to a Microtenant, and the option to share application segments between Microtenants, is available when using the Zscaler Private Access (ZPA) cloud service API.
- An endpoint to get all configured isolation profiles is available in the ZPA API Portal. CRUD APIs are also supported for isolation policy use cases using the endpoints in the policy-set-controller.
To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api), [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api), [Configuring Isolation Profiles Using API](/zpa/obtaining-isolation-profile-details-using-api), and [Configuring Isolation Policies Using API](/zpa/configuring-isolation-policies-using-api).

### Feature in Limited Availability
#### Support for Server-Initiated Remote Administration Workflows
Zscaler Private Access (ZPA) supports server-to-client use cases for remote assistance, remote troubleshooting, and software distribution based on either the FQDN or IP-based connectivity. Zscaler Client Connector versions 4.2 for Windows and later is required for IP-based connectivity. Zscaler Client Connector versions 3.9.0.169 or later for Windows, versions 1.4 or later for Linux, or versions 3.7 or later for macOS are required for FQDN-based connectivity.
Contact Zscaler Support to enable this feature for your organization.
To learn more, see [Understanding Server-To-Client Connectivity](/zpa/understanding-server-client-connectivity) and [Configuring Server-To-Client Connectivity](/zpa/configuring-server-client-connectivity).

## July 12, 2023
### Feature Available
#### VMware Image Updates
New App Connector and ZPA Private Service Edge images are available in VMware to address routine security vulnerabilities.
To learn more, see [App Connector Deployment Guide for VMware Platforms](/zpa/connector-deployment-guide-vmware-platforms), [App Connector Deployment Guide for Nutanix AHV](/zpa/app-connector-deployment-guide-nutanix-ahv), and [ZPA Private Service Edge Deployment Guide for VMware Platforms](/zpa/service-edge-deployment-guide-vmware).

## July 05, 2023
### Feature Available
#### Audit Logs Enhancements
A new resource type for Policy Reorder was added to the Audit Logs in the ZPA Admin Portal (Configuration & Control > Administration Control > Audit Logs) that allows you to filter and review audit logs for policy reordering.
[See image.](#policyReorder)
To learn more, see [About Audit Logs](/zpa/about-audit-logs#resourceType).
[]![Policy Reorder Resource Type in the Audit Logs](/sites/default/files/downloads/zpa-policy-reorder-resource-type.png?1687804639)

## June 27, 2023
### Feature Available
#### Registration of FQDNs for Client-to-Client Applications
An update was released for ZPA Private Service Edges to fix an issue with registration of FQDNs for client-to-client applications.
To learn more, see [About the Manager Software](/zpa/about-manager-software#managerUpgrades).

## June 19, 2023
### Feature Available
#### LSS Updates
The following changes were made to the Log Streaming Service (LSS):
- An update was released that changed the labels for the ConnectorUpTime and HostUpTime log fields to ConnectorStartTime and HostStartTime, respectively. To learn more, see [About Private Service Edge Status Log Fields](/zpa/about-private-service-edge-status-log-fields) and [About App Connector Status Log Fields](/zpa/about-connector-status-log-fields).
- An update was released that added the log fields ClientCity and City to the LSS for the User Activity and User Status log types. To learn more, see [About User Activity Log Fields](/zpa/about-user-activity-log-fields) and [About User Status Log Fields](/zpa/about-user-status-log-fields).
- An update was released that changed the label for the isClientAudit log field to clientAuditUpdate. To learn more, see [About Audit Log Fields](/zpa/about-audit-log-fields).

### Feature Available
#### ZPA Admin Password Improvements
An update was released that improves the way passwords are created and updated in the ZPA Admin Portal. Certain passwords are rejected if they are included in the compromised password list. Contact Zscaler Support to learn more.

### Feature Available
#### ZPA API Improvements
The certificate, enrollment certificate, IdP configuration, posture profile, SAML attribute, LSS (Log Streaming Service) configuration, and trusted network controllers were updated to remove the version two (v-2) labels, and were consolidated into their related controllers.
To learn more, see the ZPA [API Developer & Reference Guide](/zpa/zpa-api/api-developer-reference-guide/reference-guide).

## June 15, 2023
### Feature Available
#### App Connector Deployment on Docker
App Connector deployments on Docker platforms are now available. To learn more, see the [App Connector Deployment Guide for Docker](/zpa/app-connector-deployment-guide-docker).

## June 14, 2023
### Feature Available
#### Intelligent Application Segmentation
The following updates were made to the Zscaler Private Access (ZPA) Intelligent Application Segmentation feature to:
- Provide the ability to view a list of recommended users.
- Offer a visualization of the attack surface that would be reduced by accepting recommended application segments.
- Include two additional recommendation factors: Domain Name Similarity and Co-occurring Applications Similarity.
To learn more, see [About Recommended Application Segments](/zpa/about-recommended-application-segments) and [About the Application Dashboard](/zpa/about-applications-dashboard).

## June 13, 2023
### Feature Available
#### Browser-in-Browser User Experience Mode Update for Isolation
Browser-in-browser experience mode for Isolation has been simplified for reliability and a streamlined workflow. Each tab on the native browser is mapped to a tab on the isolation browser. When a user is in an isolation session with browser-in-browser mode enabled, the user cannot see multiple tabs on the isolation browser displayed in a single native browser tab.
If a user opens a new tab in the isolation browser, a new tab on the native browser is launched, providing access to the new tab on the isolation container.
[See image.](#Browser-in-browser-mode-view)
To learn more, see [User Experience Modes in Isolation](/isolation/user-experience-modes-cloud-browser-isolation).
[![Browser-in-browser mode view](/sites/default/files/downloads/isolation/end-user-isolation-experience/user-experience-modes-cloud-browser-isolation/Browser-in-browser_mode_editbale-URL_squircle.png)
]

### Feature Available
#### Enhanced File Type Support for Isolation
Isolation has enhanced the ability to access, transfer, and view additional file types.
Users can now decompress and view the following compressed file types in an isolated environment:
- .ZIP
- .TAR
- .7Z
- .RAR
Users can now view the following Office file types in an isolated environment:
- .PPT
- .DOC
- .XLS
- .CSV
- .RTF
- .TXT
- .ODP
- .ODS
- .ODT
- Visio
Isolation has also enhanced file rendering capabilities to support password-protected Office files. If a user accesses a password-protected Office file, the user is prompted to enter the file-specific password, after which the file is rendered on the isolation browser for the duration of the isolated session.
To learn more, see [Transferring and Viewing Files in Isolation](/isolation/transferring-and-viewing-files-cloud-browser-isolation).

## June 07, 2023
### Feature in Limited Availability
#### Browser Protection
Zscaler Private Access (ZPA) provides Browser Protection profiles that allow you to set attributes used to create fingerprints for browser access sessions. You can create Browser Protection policies to monitor users and fingerprint browser access sessions. You can view the results for monitored users and the inspected browser access sessions in the Browser Protection Dashboard and the Clientless Access Diagnostics page.
To learn more, see [About Browser Protection Profile](/zpa/about-browser-protection-profiles), [About Browser Protection Policy](/zpa/about-browser-protection-policy), [About Browser Protection Dashboard](/zpa/about-browser-protection-dashboard), and [About Clientless Access Diagnostics](/zpa/about-clientless-access-diagnostics).

## June 05, 2023
### Feature Available
####  Updates to Root Certificates for Isolation
An update was released that changed the label for the Root Certificates page to Root Certificates for Isolation in the Zscaler Private Access (ZPA) Admin Portal.
To learn more, see [About Root Certificates for Isolation](/isolation/about-root-certificates-isolation-zpa).

## June 02, 2023
### Feature Available
#### Clipboard Feature
Zscaler Private Access (ZPA) allows your users to copy and paste text between their local devices and privileged consoles with Privileged Remote Access (PRA). You can set copy and paste permissions in a privileged capabilities policy. Contact Zscaler Support to enable this feature for your organization.
To learn more, see [About Privileged Capabilities Policy](/zpa/about-privileged-capabilities-policy) and [Copying and Pasting with Clipboard](/zpa/copying-and-pasting-clipboard).

### Feature Available
#### Country Code Updates
Access policies include country codes as a criteria option. You can allow or block the country that a user’s IP address is located in. If deployed, the minimum required ZPA Private Service Edge version is [22.385.2](/zpa/zpa-private-service-edge-release-summary-2023?applicable_category=private.zscaler.com&applicable_version=22.385.2&deployment_date=2023-01-24&id=1436456) and later.
To learn more, see [Configuring Access Policies](/zpa/configuring-access-policies).

### Feature Available
#### File Transfer with VNC
Zscaler Private Access (ZPA) supports using File Transfer in a privileged console with a VNC protocol for Privileged Remote Access (PRA).
To learn more, see [Configuring Privileged Consoles](/zpa/configuring-privileged-consoles).

### Feature Available
#### Resolved Issues
An update was released to correct the Brazil time zone to GMT-03:00 and the Mexico time zone to CST.

### Feature Available
#### Supporting Files for ZPA Private Service Edges
A new field is available in the Service Edges page when expanding a ZPA Private Service Edge. The new field indicates the upgrade status of supporting files used to map the public IP of the ZPA Private Service Edge to the country where the IP is registered.
To learn more, see [About ZPA Private Service Edges](/zpa/about-zpa-private-service-edges).

## May 31, 2023
### Feature Available
#### Manager Software Updates
An optional update was released for the Manager software based on Red Hat Enterprise Linux 7 to support [Zscaler Branch Connector](/cloud-branch-connector/what-zscaler-branch-connector).
To learn more, see [About the Manager Software](/zpa/about-manager-software#managerUpgrades).

### Feature Available
#### Required Password Change
An update was released for App Connectors and ZPA Private Service Edges that requires admins to change the default password.
To learn more, see [Upgrading the App Connector Host OS](/zpa/upgrading-app-connector-host-os), [App Connector Deployment Prerequisites](/zpa/connector-deployment-prerequisites#SecurityAndFirewallReqs), [Managing Deployed App Connectors](/zpa/managing-deployed-connectors), [Managing Deployed ZPA Private Service Edges](/zpa/managing-deployed-zpa-private-service-edges), [ZPA Private Service Edge Deployment Prerequisites](/zpa/zpa-service-edge-deployment-prerequisites#Firewall), and [About the Manager Software](/zpa/about-manager-software#managerUpgrades).

### Feature Available
#### Restrict Number of Applications Downloaded
An update was released for ZPA Private Service Edges to support a large number of applications.
To learn more, see [About the Manager Software](/zpa/about-manager-software#managerUpgrades).

### Feature Available
#### ZPA Private Service Edge Support for Cloud and Branch Connectors
An update was released for ZPA Private Service Edges that provides support for Branch Connectors and Cloud Connectors.

## May 30, 2023
### Feature Available
#### ZPA Integration with Browser Isolation
The ZPA Admin Portal has been completely integrated with Browser Isolation. Details like Zscaler Root Certificates, Isolation Profiles, and Isolation Banners can be managed by ZPA admins.
[See image.](#zpa-leftnav)
To learn more, see [What Is Isolation?](/isolation/what-isolation)
[![Isolation integrated into ZPA](/sites/default/files/downloads/zpa/documentation-knowledgebase/admin-settings/admins-and-roles/configuring-administrator-roles/ZPA_leftnavbar_Isolation.png)
]

## May 19, 2023
### Feature Available
#### AWS and Azure Image Updates
New App Connector and ZPA Private Service Edge images are available in AWS Marketplace to address security vulnerabilities. A new App Connector image is also available in the Azure Portal to address the same issue.
To learn more, see [App Connector Deployment Guide for Amazon Web Services](/zpa/connector-deployment-guide-amazon-web-services), [ZPA Private Service Edge Deployment Guide for Amazon Web Services](/zpa/service-edge-deployment-guide-amazon-web-services), and [App Connector Deployment Guide for Microsoft Azure](/zpa/connector-deployment-guide-microsoft-azure).

### Feature Available
#### Docker Hub and VMware Image Updates
New App Connector and ZPA Private Service Edge images are available in VMware and Docker Hub to address security vulnerabilities.
To learn more, see the App Connector Deployment Guides for [Docker](/zpa/app-connector-deployment-guide-docker) and [VMware Platforms](/zpa/connector-deployment-guide-vmware-platforms), and the ZPA Private Service Edge deployment guides for [VMware Platforms](/zpa/service-edge-deployment-guide-vmware).

## May 18, 2023
### Feature Available
#### Simplifying Isolation URLs
Isolation URLs appear more like URLs from non-isolated sessions. Isolation information is hidden from the URL when in isolation view. Isolation URLs can still be copied and shared with other users.
The isolation URL appears in its simple version whether a user is in native or browser-in-browser mode. It contains a domain in the format of <clusterid>.isolation.zscaler.com. The region identifier and the tenant identifier are still available as a query string in the URL.
To learn more, see [User Experience Modes in Isolation](/isolation/user-experience-modes-cloud-browser-isolation).

## May 16, 2023
### Feature Available
#### RPM Package and Manager Software Updates
A new App Connector and ZPA Private Service Edge RPM package is available to provide support for Red Hat Enterprise Linux 8 with the SHA-256 security hash algorithm for Federal Information Processing Standards (FIPS) Mode compliance. FIPS Mode is not supported for App Connector deployments on Red Hat Enterprise Linux 8 if Privileged Remote Access (PRA) is enabled on the App Connector. The RPM package version is 23.63.1. This RPM can only be deployed on Red Hat Enterprise Linux 8 platforms.
To learn more, see [About the Manager Software](/zpa/about-manager-software#managerUpgrades), [App Connector Deployment Guide for CentOS, Oracle, and Redhat](/zpa/connector-deployment-guide-centos-oracle-and-redhat), and [Service Edge Deployment Guide for CentOS, Oracle, and Redhat](/zpa/service-edge-deployment-guide-centos-oracle-and-redhat).

## May 15, 2023
### Feature Available
#### Audit Log Search Enhancements
An update was released that allows the filtering of multiple conditions on the Audit Logs page of the Zscaler Private Access (ZPA) Admin Portal.

### Feature in Limited Availability
#### Emergency Access
Emergency access is available in the Zscaler Private Access (ZPA) Admin Portal. Emergency access allows a ZPA admin to invite third-party users to access approved application segments in a time-bound window. The invited third-party users are created on a configured Okta identity provider (IdP). You can create a user designated for emergency access when creating a [privileged approval](/zpa/about-privileged-approvals) for the user, and then manage them on the Emergency Access Users page of the ZPA Admin Portal. Emergency access is only supported for [Privileged Remote Access](/zpa/privileged-remote-access-management).
Contact Zscaler Support to enable this feature for your organization.
To learn more, see [About Emergency Access Users](/zpa/about-emergency-access-users), [Configuring Emergency Access](/zpa/configuring-emergency-access), and [Configuring Privileged Approvals](/zpa/configuring-privileged-approvals).

## May 12, 2023
### Feature Available
#### Events and Notifications Enhancements
An update was released to add ZPA Private Service Edge usage metrics to the notification management and events diagnostics. A new event for tracking source port consumption was also added.
To learn more, see [Configuring Notifications](/zpa/configuring-notifications) and [Viewing and Managing Events Diagnostics](/zpa/viewing-and-managing-events-diagnostics).
Resolved Issues
An update was released to remove Machine Tunnels from the list of available components for the notifications feature. Zscaler recommends deleting the notification if it is missing a component value in the Component field on the Notifications page of the ZPA Admin Portal.
[See image.](#missingComponent)
To learn more, see [Configuring Notifications](/zpa/configuring-notifications).
[]![Machine Tunnel component missing in the Notifications page](/sites/default/files/downloads/zpa-removing-machine-tunnels-notification.png)

### Feature in Limited Availability
#### AppProtection Update
If you have AppProtection enabled, you can disable AppProtection for App Connector Groups. The ability to disable AppProtection is also available via the ZPA cloud service API.
To learn more, see [Configuring App Connectors](/zpa/configuring-connectors) and [Configuring App Connector Groups Using API](/zpa/configuring-app-connector-groups-using-api).

## May 05, 2023
### Feature Available
#### Credential Mapping
Zscaler Private Access (ZPA) provides the ability to set up allocated credentials for users to access designated privileged consoles for Privileged Remote Access (PRA). These credentials allow access to be given to users in a controlled manner. Please contact Zscaler Support to enable this feature for your organization.
To learn more, see [About Privileged Credentials Policy](/zpa/about-privileged-credentials-policy).

## May 01, 2023
### Feature Available
#### Branch Connector Support
Zscaler Private Access (ZPA) supports a new client type called Branch Connector. Using Branch Connector Groups and Locations as a criteria, Admins can view and configure policy rules to Branch Connectors and Branch Connector Groups in the ZPA Admin Portal.
Zscaler recommends you consider the following when configuring Branch Connectors:
- All existing Branch Connectors appear as Cloud Connectors in the ZPA Admin Portal after April 10, 2023. You must configure a new Branch Connector in the Zscaler Cloud & Branch Connector Admin Portal for it to be visible in the Branch Connector and Branch Connector Groups pages of the ZPA Admin Portal.
- Provisioning templates created before April 10, 2023, are no longer valid and must not be used. New [provisioning templates](/cloud-branch-connector/about-branch-provisioning-template) must be used to properly provision a Branch Connector.
To learn more, see [About Branch Connectors](/zpa/about-branch-connectors), [About Branch Connector Groups](/zpa/about-branch-connector-groups), and [Configuring Access Policies](/zpa/configuring-access-policies).

### Feature Available
#### Resolved Issues
An update was released to address a load balancing issue that, in limited circumstances, impacted App Connectors used for Source IP Anchoring applications.

## April 12, 2023
### Feature Available
#### Disaster Recovery Improvements
An update was released for App Connectors and ZPA Private Service Edges that allows for the backup and management of disaster recovery configuration. Additionally, debugging commands are available for disaster recovery troubleshooting.
To learn more, see [About Disaster Recovery App Connector Groups](/zpa/about-disaster-recovery-app-connector-groups), [About Disaster Recovery ZPA Private Service Edge Groups](/zpa/about-disaster-recovery-service-edge-groups), [Managing Disaster Recovery Configuration and Binary Snapshots](/zpa/managing-disaster-recovery-configuration-and-binary-snapshots), [Troubleshooting App Connectors](/zpa/troubleshooting-app-connectors), and [Troubleshooting ZPA Private Service Edges](/zpa/troubleshooting-zpa-private-service-edges).

### Feature Available
#### Notification for Reauthentication in Zscaler Client Connector
An update was released that enhances the ZPA Public Service Edge and ZPA Private Service Edge Microtunnel (M-Tunnel) connections to Zscaler Client Connector. This allows Zscaler Client Connector to notify users prior to losing access to certain applications.
To learn more, see [Zscaler Client Connector 4.2 Enhancements and Fixes](/client-connector/client-connector-app-release-summary-2023?applicable_category=Windows&applicable_version=4.2&deployment_date=2023-04-12).

### Feature Available
#### Resolved Issues
A fix was released to address an issue where the App Connector IP for UDP connections was not correctly displayed on the [Diagnostics](/zpa/dashboard-diagnostics) pages.

## March 20, 2023
### Feature Available
#### Admin Portal Updates
The following updates were made to the Zscaler Private Access (ZPA) Admin Portal:
- The left-side navigation bar in the ZPA Admin Portal has been updated. An option to return to the original left-side navigation is temporarily available within the Account settings. To learn more, see [Accessing and Navigating the ZPA Admin Portal](/zpa/accessing-and-navigating-zpa-admin-portal).
- An update was released to change Forwarding Service Edge to Control Service Edge in the Diagnostics. To learn more, see [About User Activity Diagnostics](/zpa/about-user-activity-diagnostics).
- Web Probe Cacheless, HTTP Web Probe, and HTTPS Web Probe have been added as values to the Connection Type filter on the User Activity Diagnostics page. To learn more, see [About User Activity Diagnostics](/zpa/about-user-activity-diagnostics).
- An update was released to the Add Session form to include both App Connectors and ZPA Private Service Edges when collecting data for remote troubleshooting. To learn more, see [About Support Information](/zpa/about-support-information).
- The Administrators page includes filtering based on an admin's role.
Resolved Issues
An update was released that prevents the selection of a provisioning key when the maximum utilization counts are reached.

## March 10, 2023
### Feature Available
#### AWS, Azure, VMware, and Docker Hub Image Updates
A new App Connector and ZPA Private Service image is available in Microsoft Azure Marketplace, VMware, and Docker Hub to address a security vulnerability. A new App Connector image is also available in AWS Marketplace to address the same issue.
To learn more, see [About the Manager Software](/zpa/about-manager-software#managerUpgrades), the App Connector Deployment Guides for [AWS](/zpa/connector-deployment-guide-amazon-web-services), [Azure](/zpa/connector-deployment-guide-microsoft-azure), [Docker](/zpa/app-connector-deployment-guide-docker), and [VMware Platforms](/zpa/connector-deployment-guide-vmware-platforms), and the ZPA Private Service Edge deployment guides for [Azure](/zpa/service-edge-deployment-guide-microsoft-azure) and [VMware Platforms](/zpa/service-edge-deployment-guide-vmware).

## March 03, 2023
### Feature Available
#### AWS and Azure Image Updates
New App Connector and ZPA Private Service Edge images are available in AWS Marketplace to provide support for the latest [Manager software updates](/zpa/release-upgrade-summary-2023%3Fapplicable_category%3Dprivate.zscaler.com%26deployment_date%3D2023-01-24%26id%3D1436441). A new App Connector image is also available in the Azure Portal to provide the same improvements.
To learn more, see [App Connector Deployment Guide for Amazon Web Services](/zpa/connector-deployment-guide-amazon-web-services), [ZPA Private Service Edge Deployment Guide for Amazon Web Services](/zpa/service-edge-deployment-guide-amazon-web-services), and [App Connector Deployment Guide for Microsoft Azure](/zpa/connector-deployment-guide-microsoft-azure).

## February 10, 2023
### Feature Available
#### Ranges & Limitations Update
The Zscaler Private Access (ZPA) Source IP Anchoring-enabled application segment limit has increased to 255.
To learn more, see [Ranges & Limitations](/zpa/ranges-limitations).

## February 07, 2023
### Feature Available
#### File Transfer
Zscaler Private Access (ZPA) provides the ability to upload and download files from privileged consoles for Privileged Remote Access (PRA). You can inspect file uploads using the Zscaler Internet Access (ZIA) Sandbox which prevents malicious files from becoming available within the privileged console. Please contact Zscaler Support to enable this feature for your organization.
To learn more, see [About Privileged Capabilities Policy](/zpa/about-privileged-capabilities-policy).

## February 06, 2023
### Feature Available
#### Intelligent Application Segmentation
An update was released for the Zscaler Private Access (ZPA) Intelligent Application Segmentation feature that allows users to see a list of defined application segments on the Recommended Application Segments page under Number of Defined Application Segments. You can click each defined application segment in the list to view its details.
To learn more, see [About Recommended Application Segments](/zpa/about-recommended-application-segments).

### Feature Available
#### Resolved Issues
An update was released to fix an issue where the root user was populated in the Admin ID column of the Audit Logs table when an App Connector version was upgraded.

## January 31, 2023
### Feature Available
#### Updates to the Application Dashboard
The Application dashboard includes two new widgets: Top Application Segments by Bandwidth and Top Disaster Recovery App Segments by Bandwidth. These widgets and expanded visualization of this data allow you to see the top related application segments that used the most bandwidth for your organization in the specified time frame.
To learn more, see [About the Applications Dashboard](/zpa/about-applications-dashboard).

## January 30, 2023
### Feature Available
#### User Platform Mirroring in User Agent String
Cloud Browser Isolation mirrors the client's device platform as part of the isolated browser's user agent function, so that web pages accessed in isolation respond accordingly. The web pages receiving HTTP requests from the isolation browser can look at the platform portion of the user agent string, and serve the platform-appropriate content. For example, if a user attempts to download a file via an isolated browser, the file type served will be whatever the platform deems appropriate.
To learn more, see [Transferring and Viewing Files in Cloud Browser Isolation](/isolation/transferring-and-viewing-files-cloud-browser-isolation).

### Feature Available
#### Zoom In/Out Settings for Isolation
You can now zoom in and out of any web page while in isolation. The isolation function of zoom is the same as a non-isolated browser, so you can use the CTRL +/- keys for Windows devices or Command =/0 for Linux devices. You can also use the Zoom options in the View menu of your native browser.
To learn more, see [User Experience Modes in Cloud Browser Isolation](/isolation/user-experience-modes-cloud-browser-isolation).

### Feature Available
#### Zscaler DNS Record Generator Improvements
An update was released that provides improvements to the Zscaler DNS Record Generator. The improvements include the option to enable Zscaler Internet Access (ZIA) or Zscaler Private Access (ZPA) for disaster recovery, and include enhancements to the start time configuration.
To learn more, see [About the Zscaler DNS Record Generator](/zpa/about-zscaler-dns-record-generator) and [Creating DNS TXT Records](/zpa/creating-dns-txt-records).

## January 24, 2023
### Feature Available
#### Manager Software Updates
An optional update was released for the Manager software to support internal Zscaler-only cloud configurations.
To learn more, see [About the Manager Service](/zpa/about-manager-software#managerUpgrades).

## January 23, 2023
### Feature Available
#### Inspection Renamed to AppProtection
The term Inspection was changed to AppProtection. AppProtection is how traffic is inspected and managed for OWASP predefined controls, WebSocket controls, custom controls, and ThreatLabZ controls.
To learn more, see [About AppProtection Profiles](/zpa/about-inspection-profiles).

## January 18, 2023
### Feature Available
#### Updates to Policy Criteria
Platform as a policy criteria option can be used for access policies, timeout policies, client forwarding policies, isolation policies, and inspection policies. This feature requires Zscaler Client Connector versions:
- 3.0 or above for Windows and Mac
- 1.9 or above for iOS and Android
- 1.1 or above for Linux
To learn more, see [Configuring Access Policies](/zpa/configuring-access-policies), [Configuring Timeout Policies](/zpa/configuring-timeout-policies), [Configuring Client Forwarding Policies](/zpa/configuring-client-forwarding-policies), [Configuring Isolation Policies](/zpa/configuring-isolation-policies), and [Configuring Inspection Policies](/zpa/configuring-inspection-policies).

## January 13, 2023
### Feature Available
#### Virtual Network Computing
Zscaler Private Access (ZPA) provides the ability to assign the Virtual Network Computing (VNC) protocol type to privileged consoles for Privileged Remote Access (PRA). VNC is supported on [App Connector version 22.354.4](/zpa/app-connector-release-summary-2023?applicable_category=private.zscaler.com&applicable_version=22.354.4&deployment_date=2023-01-11&id=1433656).
To learn more, see [Configuring Application Segments](/zpa/configuring-application-segments) and [Accessing a Privileged Remote Access Portal](/zpa/accessing-privileged-remote-access-portal).

## January 09, 2023
### Feature Available
#### Resolved Issues
A fix was released to resolve a performance degradation issue for ZPA Public Service Edges that was due to high memory consumption in the logging services of the ZPA cloud.
