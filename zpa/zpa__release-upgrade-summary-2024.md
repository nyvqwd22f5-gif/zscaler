# Release Upgrade Summary (2024)
Source: https://help.zscaler.com/zpa/release-upgrade-summary-2024

This article provides a summary of all new features and enhancements per Zscaler cloud for the ZPA Admin Portal. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com/).
When Zscaler cloud and Admin Portal updates are deploying, some functionality will not be available until the deployment process completes.

**Clouds:** private.zscaler.com, zpatwo.net, zpabeta.net, zpapreview.net
The following service updates were deployed to private.zscaler.com on

## December 31, 2024
### Feature Available
#### Idle Connection Timeout Update for Timeout Policy Rules
The timeout for an open TCP session was updated from Never to 2 hours when Default is selected for the Idle Connection Timeout setting in a timeout policy rule.
To learn more, see [Configuring Timeout Policies](/zpa/configuring-timeout-policies).

## December 18, 2024
### Feature Available
#### Language Translation in Isolation for ZPA
Users can translate web pages into different languages while in an isolated session through [Google Translate](http://translate.google.com/). They can translate the content of an entire page, or they can select specific text from the page to translate. For the duration of the session, users can click the Translate icon in the isolation bar menu or use [the right-click menu](/isolation/using-right-click-menu-isolation) to access the translation options. The default selected language depends on the user's region. This function can be enabled by admins per isolation profile. Google Translate is being used to power the translation within the application that is being isolated, and Zscaler uses Google Translate APIs in order to provide the translation service.
[See image.](#translattion-menu)
To learn more, see [Creating Isolation Profiles for ZPA](/isolation/creating-isolation-profiles-zpa) and [Using the Isolation Bar in Native Browser Experience](/isolation/using-isolation-bar-native-browser-experience).
[]![Dialog-Box.png](/sites/default/files/downloads/isolation/end-user-isolation-experience/using-right-click-menu-isolation/Dialog-Box.png)

## December 17, 2024
### Feature Available
#### Active Directory Controls
ZPA provides Active Directory as an AppProtection Control option. ZPA also provides Active Directory Protection inspection for protocol traffic (Kerberos, SMB, and LDAP). You can enable Active Directory Protection when configuring an application segment. After an Active Directory control is created, you can add it to an AppProtection profile. You can view the suspicious activity, errors, and violations on the Active Directory Dashboard page.
To learn more, see [About Active Directory Controls](/zpa/about-active-directory-controls) and [Viewing the Active Directory Protection Dashboard](/zpa/viewing-active-directory-protection-dashboard).

### Feature Available
#### STIG Platform Image Support on Microsoft Azure
A new Red Hat Enterprise Linux 9 App Connector image that supports Security Technical Implementation Guide (STIG) is available for Microsoft Azure.
To learn more, see [App Connector Software by Platform](/zpa/zpa-app-connector-software-by-platform).
Passwords for STIG-hardened images automatically expire after 60 days. If the password expires without disabling or changing its expiration, admin access to the App Connector becomes unavailable. When admin access expires, the only recovery method is to deploy a new App Connector.
To learn how to disable password expiration for STIG-hardened images, see [Disabling Password Expiration for STIG-Hardened App Connector Images](/zpa/disable-password-expiration-stig-hardened-app-connector-images).

## December 16, 2024
### Feature Available
#### STIG Platform Image Support on Nutanix and VMware
New Red Hat Enterprise Linux 9 App Connector and ZPA Private Service Edge images that support Security Technical Implementation Guide (STIG) are available for Nutanix and VMware.
To learn more, see [App Connector Software by Platform](/zpa/zpa-app-connector-software-by-platform) and [ZPA Private Service Edge Software by Platform](/zpa/zpa-private-service-edge-software-by-platform).
Passwords for STIG-hardened images automatically expire after 95 days (60 days + a 35-day grace period). If the password expires without disabling or changing its expiration, admin access to an App Connector or ZPA Private Service Edge becomes unavailable. When admin access expires, the only recovery method is to deploy a new App Connector or Private Service Edge.
To learn how to disable password expiration for STIG-hardened images, see [Disabling Password Expiration for STIG-Hardened App Connector Images](/zpa/disable-password-expiration-stig-hardened-app-connector-images) or [Disabling Password Expiration for STIG-Hardened ZPA Private Service Edge Images](/zpa/disable-password-expiration-stig-hardened-private-service-edge-images).

### Feature Available
#### Understanding Persistent State for Isolation in ZPA
Persistent State allows users to have isolation sessions automatically restored with current state data when they time out. Admins can allow this feature per user profile by enabling Cookie Persistence.
To learn more, see [Creating Isolation Profiles for ZPA](/isolation/creating-isolation-profiles-zpa).

## December 05, 2024
### Feature Available
#### File Size Limit Increase in Isolation for PDFTron
The file size limit for viewing files in Isolation while using PDFTron is 100 MB. A strong internet connection is ideal for maximum rendering performance while using PDFTron. To learn more, see [Transferring & Viewing Files in Isolation](/isolation/transferring-and-viewing-files-isolation).

## December 04, 2024
### Feature Available
#### Primary Domain Updates
An update was released for default primary domains to include the cloud name. The new format for primary domains is <customerId>-<cloudName>.zpa-customer.com. This applies to primary domains created after December 4, 2024.

## December 02, 2024
### Feature Available
#### Manager Software Updates
A recommended update was released that includes updated App Connector and ZPA Private Service Edge RPM packages for Red Hat Enterprise Linux 7.x, 8.x, and 9.x.
You can download the Manager Software for [App Connectors](/zpa/app-connector-deployment-guide-linux) or [ZPA Private Service Edges](/zpa/private-service-edge-deployment-guide-linux) from our repository. The Manager software version is 24.650.5. To learn more, see [Understanding the Manager Software](/zpa/about-manager-software#managerUpgrades).

### Feature Available
#### Minimum Version Control for App Connectors and ZPA Private Service Edges
An update was released to support the version check and automated upgrades of App Connectors version 24.650.5 and ZPA Private Service Edges version 24.650.5 and later during the initial connection.
To learn more, refer to the [Zscaler Trust Portal](https://trust.zscaler.com/private.zscaler.com/security-advisories).

## November 26, 2024
### Feature Available
#### STIG Platform Image Support
New Red Hat Enterprise Linux 9 App Connector and ZPA Private Service Edge images that support Security Technical Implementation Guide (STIG) are available for the following platforms:
- Amazon Web Services (AWS)
- Google Cloud Platform (GCP)
To learn more, see [App Connector Software by Platform](/zpa/zpa-app-connector-software-by-platform) and [ZPA Private Service Edge Software by Platform](/zpa/zpa-private-service-edge-software-by-platform).
Passwords for STIG-hardened images automatically expire after 60 days. If the password expires without disabling or changing its expiration, admin access to an App Connector or ZPA Private Service Edge becomes unavailable. When admin access expires, the only recovery method is to deploy a new App Connector or ZPA Private Service Edge.
To learn how to disable password expiration for STIG-hardened images, see [Disabling Password Expiration for STIG-Hardened App Connector Images](/zpa/disable-password-expiration-stig-hardened-app-connector-images) or [Disabling Password Expiration for STIG-Hardened ZPA Private Service Edge Images](/zpa/disable-password-expiration-stig-hardened-private-service-edge-images).

## November 19, 2024
### Feature in Limited Availability
#### Updates to the PRA Portal and Privileged Consoles
When you click the Settings icon in a Privileged Remote Access (PRA) Portal, you can select a keyboard language, display resolution, display quality, and time zone for the privileged consoles assigned to that privileged portal. The display resolution Fit to Bounds is the default option, and the display quality High option is for Windows.
[See image.](#prasettings)
After you sign in to a privileged console, you can view a collapsible menu that includes the favicon, name of the privileged console, Recording icon, Participants icon, Keyboard icon, Full Screen icon, Copy icon, and Clipboard icon. The menu also includes the length of time the privileged console is active, and an End option to end the live session for that privileged console.
[See image.](#praconsolemenu)
[]![Settings window in the PRA Portal ](/sites/default/files/downloads/Update%20to%20Settings%20window.png)
[]![Collapsible menu within a privileged console](/sites/default/files/downloads/Update%20to%20privileged%20console.png)

## November 14, 2024
### Feature Available
#### Enterprise RealVNC Connectivity in Privileged Remote Access (PRA)
ZPA provides the ability to configure Enterprise RealVNC targets as privileged consoles in PRA. Unlike the existing RFB-compliant VNC protocol, this uses a proprietary RealVNC protocol to provide end-to-end encryption as well as support for Enterprise username and password credentials.
To learn more, see [Configuring Defined Application Segments](/zpa/configuring-application-segments) and [Configuring Privileged Consoles](/zpa/configuring-privileged-consoles).

## November 08, 2024
### Feature Available
#### Active Apps in App Connector Details
The App Connector details for Active Apps in the Health dashboard has been updated to reflect data in the Application Reachability graph.
[See image.](#app-connector-details)
To learn more, see [About the Health Dashboard](/zpa/about-health-dashboard#cdetails).
[]![App Connector details](/sites/default/files/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/about-health-dashboard/app-connector-details_1.png)

## October 31, 2024
### Feature Available
#### Privileged Remote Access (PRA) File Transfer System
The PRA File Transfer System feature in the PRA Portal allows a user to upload files on the My Files page of a PRA Portal. An admin can assign portals policy rules to enable a user to delete uploaded files, and enable file scanning using the Zscaler Internet Access (ZIA) cloud Sandbox. This feature is only available with a license. Contact your Zscaler Account team for more information.
To learn more, see [About the PRA File Transfer System](/zpa/about-pra-file-system) and [About Portals Policy](/zpa/about-portals-policy).

## October 30, 2024
### Feature Available
#### Access Policy Updates for Require Approval
The Require Approval rule action has been replaced by the Conditional Access rule action. This rule action provides access to sensitive resources. Privileged approvals for Privileged Remote Access (PRA) require using the Conditional Access rule action with the Allow with Privileged Approval checkbox selected when configuring an access policy.
[See image.](#AllowWithPrivilegedApproval)
To learn more, see [Configuring Access Policies](/zpa/configuring-access-policies).
[]![Using the Conditional Access rule action in the Add Access Policy window](/sites/default/files/downloads/zpa-add-access-policy-window-allow-with-privileged-approval.png)

### Feature Available
#### App Connector Selection Method Updates
The App Connector Selection Method feature has moved to the Traffic Steering section in the Add Access Policy and Edit Access Policy windows when configuring an access policy. There are no changes to the existing functionality.
[See image.](#AddAccessPolicy)
To learn more, see [Configuring Access Policies](/zpa/configuring-access-policies) and [Editing Access Policies](/zpa/editing-access-policies).
[]![Traffic Steering in the Add Access Policy window](/sites/default/files/downloads/zpa-add-access-policy-window-traffic-steering-conditional-access.png)

## October 28, 2024
### Feature in Limited Availability
#### Workload Groups for Access Policy
You can select Workload Groups as a criteria for access policy. Workload groups allow you to apply security policies for your cloud workloads that are deployed on a public cloud service provider.
[See image.](#WorkloadGroups)
Contact Zscaler Support to enable this feature for your organization.
To learn more, see [About Workload Groups](/zia/about-workload-groups) and [About Access Policy](/zpa/about-access-policy).
[]
![Workload Groups](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2024/ZPA-WorkloadGroups.png)

## October 25, 2024
### Feature Available
#### Manager Software Updates
A recommended update was released that includes updated App Connector and ZPA Private Service Edge RPM packages for Red Hat Enterprise Linux 7.x, 8.x, and 9x.
You can download the Manager Software for[ App Connectors](/zpa/app-connector-deployment-guide-linux) or [ZPA Private Service Edges](/zpa/private-service-edge-deployment-guide-linux) from our repository. To learn more, see [Understanding the Manager Software](/zpa/understanding-manager-software).

## October 22, 2024
### Feature Available
#### Kubernetes Support for App Connector
Kubernetes support for App Connector is now available.
To learn more, see [App Connector Deployment Guide for Kubernetes](/zpa/app-connector-deployment-guide-kubernetes) and [ZPA App Connector Software by Platform](/zpa/zpa-app-connector-software-by-platform).

## October 17, 2024
### Feature Available
#### Visual Differentiation for Isolated Web Pages
To make sure users can differentiate between isolated and non-isolated browsers, the following updates have been made:
- An isolated web page displays a blue rectangular border surrounding it to indicate that it's in Isolation.
- The favicon, or the image that represents the web page in the tab header, displays a blue rectangular border surrounding it to indicate that the tab holds an isolated web page.
- Prefixing the isolated tab name is either a lock icon "🔒" when on a supported browser or a pound sign "#" when on an unsupported browser.
[See image.](#borders-and-icon)
[]![Blue-borders-all-3_arrows.png](/sites/default/files/downloads/isolation/end-user-isolation-experience/Blue-borders-all-3_arrows.png)

## October 14, 2024
### Feature Available
#### Turbo Mode for Isolation with ZPA
Turbo mode for Isolation leverages the GPU on the user's machine, capturing the rendering instructions from an isolated web page and replaying them in the user's browser window. This method of rendering content is faster and uses less bandwidth than pixel streaming. You can enable this feature [per isolation profile](/isolation/profiles).
[See image.](#Enable-Turbo-Mode)
To learn more, see [Using Turbo Mode for Isolation](/isolation/using-turbo-mode-isolation) and [Creating Isolation Profiles for ZPA](/isolation/creating-isolation-profiles-zpa).
[]![Add-Isolation-Profile_Enable-Turbo-Mode.png](/sites/default/files/downloads/isolation/end-user-isolation-experience/using-turbo-mode-isolation/Add-Isolation-Profile_Enable-Turbo-Mode.png)

## October 09, 2024
### Feature Available
#### Resolved Issues
A fix was released to address an issue where the Move action appeared for applications when a Microtenant wasn't available.
To learn more, see [Moving Resources from a Microtenant](/zpa/moving-resources-microtenant) and [About Applications](/zpa/about-applications).

## September 26, 2024
### Feature Available
#### Manager Software Updates
A recommended update was released that includes updated App Connector and ZPA Private Service Edge RPM packages for Red Hat Enterprise Linux 7.x, 8.x, and 9x.
You can download the Manager Software for [App Connectors](/zpa/app-connector-deployment-guide-linux) or [ZPA Private Service Edges](/zpa/private-service-edge-deployment-guide-linux#step3deploy) from our repository. To learn more, see [Understanding the Manager Software](/zpa/understanding-manager-software#managerUpgrades).

## September 20, 2024
### Feature in Limited Availability
#### Introducing Zscaler Microsegmentation
Zscaler Microsegmentation is a host-based segmentation solution that extends ZPA to perform granular segmentation of private applications. This solution also enables administrators to visualize private application inventory and flows within the [ZPA Admin Portal](/zpa/accessing-and-navigating-zpa-admin-portal).
It is a multi-tenant software-as-a-service where the Zscaler cloud and agents work together to collect and analyze application flow and telemetry data as well as monitor system health.
If you want Microsegmentation provisioned for your organization, contact the Zscaler Account team.
[See image.](#navbar-Microsegmentation)
To learn more, see [What Is Microsegmentation?](/zpa/what-microsegmentation)
[]![A view of the ZPA navigation bar with the new Microsegmentation menu section added.](/sites/default/files/downloads/zpa/microsegmentation/what-microsegmentation/navbar-squircle.png)

## September 11, 2024
### Feature Available
#### Google Cloud Platform Image Support
New Red Hat Enterprise Linux 9 App Connector and ZPA Private Service Edge images are available for Google Cloud Platform (GCP).
To learn more, see [App Connector Software by Platform](/zpa/zpa-app-connector-software-by-platform) and [ZPA Private Service Edge Software by Platform](/zpa/zpa-private-service-edge-software-by-platform).

## September 06, 2024
### Feature Available
#### Max Age for Authentication Disaster Recovery Improvements
An update was released to support a maximum value of up to 380 days for the Max Age for Authentication field on the Disaster Recovery Settings page.
To learn more, see [About Disaster Recovery Settings](/zpa/about-disaster-recovery-settings).

### Feature Available
#### ZPA Admin Account Update
The Account section of the ZPA Admin Portal has been updated so the user can update the language, time zone, and password for their ZPA Admin Portal account. They can also view their username and customer ID.
[See image.](#Account)
To learn more, see [Accessing and Navigating the ZPA Admin Portal](/zpa/accessing-and-navigating-zpa-admin-portal#Account).
[]![Account page in the ZPA Admin Portal](/sites/default/files/downloads/zpa/getting-started/admin-portal/accessing-and-navigating-zpa-admin-portal/Updated2Account%20page%20in%20ZPA%20Admin%20portal.png)

## September 03, 2024
### Feature Available
#### ZPA API Improvements for Segment Group
A new endpoint to update a segment group is available in the ZPA API Portal.
To learn more, see [Configuring Segment Groups Using API](/zpa/configuring-segment-groups-using-api) and [Segment Group Controller Reference Guide](/zpa/segment-group-controller).

## August 26, 2024
### Feature Available
#### SAML and SCIM Attributes in Redirection Policy
ZPA redirection policy rules allow you to set criteria for preferring ZPA Private Service Edges over ZPA Public Service Edges based on SAML and SCIM attributes. You can also set this criteria via the ZPA cloud service API.
To learn more, see [About Redirection Policy](/zpa/about-redirection-policy), [Configuring Redirection Policies](/zpa/configuring-redirection-policies), and [Configuring Redirection Policies Using API](/zpa/configuring-redirection-policies-using-api).

## August 21, 2024
### Feature in Limited Availability
#### Protocol Discovery
When configuring an application segment, you can enable the Dynamic protocol which allows the application segment and its configured domains, ports, and protocols to be inspected. To use this feature, you need to generate an AppProtection enrollment (CA) certificate. After you have enabled the Dynamic protocol, you can select to inspect the application segment on the Protocol Discovery Dashboard and view the analytics on the Protocol Discovery Diagnostics page.
To learn more, see [Configuring Defined Application Segments](/zpa/configuring-application-segments), [Viewing the Protocol Discovery Dashboard](/zpa/viewing-protocol-discovery-dashboard), and [Accessing Protocol Discovery Diagnostics](/zpa/accessing-protocol-discovery-diagnostics).

## August 15, 2024
### Feature in Limited Availability
#### Server-Validated Client Certificate for Posture Validation
An update was released to support server-validated client certificate for posture validation. Contact your Zscaler Account team to enable this feature for your organization.
To learn more, see [Configuring Device Posture Profiles](/client-connector/configuring-device-posture-profiles).

## August 12, 2024
### Feature Available
#### Manager Software Updates
A recommended update was released that includes updated App Connector and ZPA Private Service Edge RPM packages for Red Hat Enterprise Linux 7.x, 8.x, and 9x.
You can download the Manager Software for [App Connectors](/zpa/app-connector-deployment-guide-linux#Deployment) or [ZPA Private Service Edges](/zpa/private-service-edge-deployment-guide-linux#step3deploy) from our repository. To learn more, see [Understanding the Manager Software](/zpa/understanding-manager-software#managerUpgrades).

## August 06, 2024
### Feature Available
#### OWASP Predefined Controls Update
The OWASP predefined controls have been updated to support version OWASP_CRS/3.3.5. By default, the version is set to OWASP_CRS/3.3.5 on the OWASP Predefined Controls page and the AppProtection Profiles page. The OWASP_CRS/3.3.5 version is supported on [App Connector version 23.313.1](/zpa/app-connector-release-summary-2023) and later.
To learn more, see [About AppProtection Controls](/zpa/about-appprotection-controls).

## August 05, 2024
### Feature Available
#### API Protection
ZPA provides API Protection controls that allow you to designate application segments for API traffic inspection. After you have assigned application segments with API Protection, you can view the results for API transactions and violations in the API Protection Dashboard page and API Protection Diagnostics page.
Contact Zscaler Support to enable this feature for your organization.
To learn more, see [About API Protection Controls](/zpa/about-api-protection-controls), [Configuring Defined Application Segments](/zpa/configuring-application-segments), [Configuring AppProtection Profiles](/zpa/configuring-appprotection-profiles), [Viewing the API Protection Dashboard](/zpa/viewing-api-protection-dashboard), and [Accessing API Protection Diagnostics](/zpa/accessing-api-protection-diagnostics).

## August 01, 2024
### Feature Available
#### Customer Support URL Resource Type Update
An update was released that changed the Customer Support URL Resource Type to Admin Configurations in the Audit Logs.
To learn more, see [About Audit Logs](/zpa/about-audit-logs).

## July 31, 2024
### Feature Available
#### International Keyboard Support for Privileged Remote Access
If you are using a privileged console with an RDP protocol for Privileged Remote Access (PRA), you can select French, German, and Spanish languages for the keyboard. English is the default language.

## July 30, 2024
### Feature Available
#### Additional Print Options in Isolation for ZPA
More options are available for printing web pages and documents in Isolation.
To learn more, see [Transferring and Viewing Files in Isolation](/isolation/transferring-and-viewing-files-isolation).

## July 29, 2024
### Feature Available
#### Privileged Session Control and Monitoring
The host of a live privileged session for Privileged Remote Access (PRA) can invite other users to attend and monitor the session. When an invited user is given control of a live privileged session, they receive mouse and keyboard control of the session. The original host of the live privileged session can regain control of the session at any time. During the session, the host can invite other participants or eject current participants, or disconnect the session which terminates the session for all participants.
To learn more, see [Configuring Privileged Capabilities Policies](/zpa/configuring-privileged-capabilities-policies) and [Accessing a Privileged Remote Access Portal](/zpa/accessing-privileged-remote-access-portal).

## July 09, 2024
### Feature Available
#### User Risk Score Enhancements
An enhancement was released to let clients remain connected to ZPA Private Service Edges when the user risk feature is enabled or disabled at the admin level.

## July 01, 2024
### Feature Available
#### AWS and Azure Image Updates
New Red Hat Enterprise Linux 9 App Connector images are available for AWS EC2 and Microsoft Azure. New ZPA Private Service Edge images are available in AWS EC2.
To learn more, see the App Connector Deployment Guides for [AWS](/zpa/connector-deployment-guide-amazon-web-services) and [Azure](/zpa/connector-deployment-guide-microsoft-azure), and the ZPA Private Service Edge Deployment Guides for [AWS](/zpa/service-edge-deployment-guide-amazon-web-services).

## June 27, 2024
### Feature Available
#### Application Deep Linking for Isolation in ZPA
Zscaler Isolation supports the ability for ZPA users to invoke a client application from the user's end machine via an isolated session. When a user clicks on a deep link within an isolated web page, the client application is invoked on the end user's machine. Admins can enable this feature per isolation profile, and can specify the URL scheme associated with the invoked client application. This provides the organization granular control over which client applications users can invoke from the isolated web pages.
If this feature is disabled for the isolation profile, or an application invoked by the user is not added to the application list in the isolation profile, the user sees an error message explaining that the application isn't allowed by policy.
To learn more, see [Creating Isolation Profiles for ZPA](/isolation/creating-isolation-profiles-zpa).

## June 25, 2024
### Feature Available
#### Updated ZPA Login Screen
The ZPA Admin Portal login screen has been updated. All users see the same login screen. The steps that follow vary based on your setup and access.
[See image.](#Signin)
To learn more, see [Accessing and Navigating the ZPA Admin Portal](/zpa/accessing-and-navigating-zpa-admin-portal).
[]![First page logging into the ZPA portal](/sites/default/files/downloads/tech-pubs-drafts/zpa-draft-articles/editing-deployed-zpa-private-service-edge-doc-51920/New%20Sign%20In%20page.png)

## June 24, 2024
### Feature Available
#### Docker Hub Image Updates
New Red Hat Enterprise Linux 9 App Connector images are available for Docker. New ZPA Private Service Edge images are available in Docker.
To learn more, see the App Connector Deployment Guides for [Docker](/zpa/app-connector-deployment-guide-docker), and the ZPA Private Service Edge Deployment Guides for [Docker](/zpa/private-service-edge-deployment-guide-docker).

### Feature Available
#### KVM Image Support
New Red Hat Enterprise Linux 9 App Connector and ZPA Private Service Edge images are available in the KVM qcow2 format to support Equinix Network Edge.
To learn more, see [ZPA App Connector Software by Platform](/zpa/zpa-app-connector-software-by-platform) and [ZPA Private Service Edge Software by Platform](/zpa/zpa-private-service-edge-software-by-platform).

## June 20, 2024
### Feature Available
#### Manager Software Updates
A recommended update was released that includes updated App Connector and ZPA Private Service Edge RPM packages for Red Hat Enterprise Linux 7.x, 8.x, and 9x.
You can download the Manager Software for [App Connectors](/zpa/app-connector-deployment-guide-linux#Deployment) or [ZPA Private Service Edges](/zpa/private-service-edge-deployment-guide-linux#step3deploy) from our repository. To learn more, see [Understanding the Manager Software](/zpa/understanding-manager-software#managerUpgrades).

## June 19, 2024
### Feature Available
#### MITRE ATT&CK Framework for AppProtection
You can analyze your organization's risk with the MITRE ATT&CK framework, a cybersecurity framework funded by the government that is used to detect, identify, and classify various tactics, techniques, and procedures (TTPs) used for cyber attacks by attackers. The MITRE ATT&CK page (Insights > MITRE ATT&CK) helps you assess your organization's security posture and calculate the risk of a cyber attack.
[See image.](#MITRE)
To learn more, see [Analyzing Risk with MITRE ATT&CK for AppProtection](/zpa/analyzing-risk-mitre-attck).
[]![The MITRE ATT&CK framework page in the ZPA Admin portal](/sites/default/files/downloads/zpa/dashboard-diagnostics/appprotection-and-browser-protection-monitoring/analyzing-risk-mitre-attck/Updated%20page.png)

## June 06, 2024
### Feature Available
#### Privileged Remote Access Privileged Session Playback
ZPA allows you to transcode privileged session recordings from a raw format to a streamable format. After a privileged session is transcoded, a user can stream it from the Privileged Sessions page. When configuring an administrator role, you can select session recordings to have full access, which allows you to download privileged session recordings from the Privileged Sessions page.
To learn more, see [Accessing Privileged Sessions](/zpa/accessing-privileged-sessions) and [Configuring Administrator Roles](/zpa/configuring-administrator-roles).

## June 05, 2024
### Feature Available
#### VMware Image Updates
New Red Hat Enterprise Linux 9 App Connector and ZPA Private Service Edge images are available for VMware.
To learn more, see [App Connector Deployment Guide for VMware Platforms](/zpa/connector-deployment-guide-vmware-platforms), [App Connector Deployment Guide for Nutanix AHV](/zpa/app-connector-deployment-guide-nutanix-ahv), and [ZPA Private Service Edge Deployment Guide for VMware Platforms](/zpa/service-edge-deployment-guide-vmware).

## June 04, 2024
### Feature Available
#### Manager Software Updates
A recommended update was released that includes updated App Connector and ZPA Private Service Edge RPM packages for Red Hat Enterprise Linux 7.x, 8.x, and 9x.
You can download the Manager Software for [App Connectors](/zpa/app-connector-deployment-guide-linux#Deployment) or [ZPA Private Service Edges](/zpa/zpa-private-service-edge-deployment-guide-linux#step3deploy) from our repository. To learn more, see [Understanding the Manager Software](/zpa/about-manager-software#managerUpgrades).

### Feature Available
#### Red Hat Enterprise Linux 9 Support
New App Connector and ZPA Private Service Edge RPM packages are available to provide support for Red Hat Enterprise Linux 9 (RHEL 9). These RPM packages can only be deployed on Red Hat Enterprise Linux 9 platforms.
To learn more about migrating App Connectors and ZPA Private Service Edges to RHEL 9, see [App Connector Red Hat Enterprise Linux 9 Migration](/zpa/app-connector-red-hat-enterprise-linux-9-migration) and [ZPA Private Service Edge Red Hat Enterprise Linux 9 Migration](/zpa/zpa-private-service-edge-red-hat-enterprise-linux-9-migration).

## June 03, 2024
### Feature Available
#### Public Service Edge Proximity Improvements
The Public Service Edge Proximity Override feature has been improved to consider all ZPA Private Service Edge groups and their proximity override configuration before redirecting users to the ZPA Private Service Edges.
To learn more, see [Configuring ZPA Private Service Edge Groups](/zpa/configuring-service-edges#addgroup).

## May 31, 2024
### Feature Available
#### Permission Group Validations for Custom Roles
An update was released that adds validations for missing permissions of custom roles in the Roles page of the ZPA Admin Portal, and in groups when configuring or editing a custom role.
To learn more, see [About Roles](/zpa/about-roles) and [Configuring Administrator Roles](/zpa/configuring-administrator-roles).

## May 28, 2024
### Feature Available
#### ZPA Integration with ZIdentity Enhancements
For tenants subscribed to ZIdentity for users, the following enhancements were made to support the ZPA integration with ZIdentity:
- The IdP Configuration page is read-only, and the Add IdP Configuration action is hidden. To learn more, see [About IdP Configuration](/zpa/about-idp-configuration).
- The SAML Attributes page is replaced by the Session Attributes page. The Add SAML Attributes, Edit, and Delete actions are hidden. To learn more, see [About SAML Attributes](/zpa/about-saml-attributes).
- The SAML and SCIM Attributes criteria are replaced with Session and User Attributes when configuring policy rules. To learn more, see [Policies](/zpa/policies).
- The SAML and SCIM Attributes options are replaced with Session and Group Attributes when defining a streaming policy on your log receiver. To learn more, see [Configuring a Log Receiver](/zpa/configuring-log-receiver).
- The SAML Attributes field is replaced with Session Attributes in the user activity diagnostics logs. To learn more, see [Accessing User Activity Diagnostics](/zpa/accessing-user-activity-diagnostics).
- The SAML Attribute and SCIM Attribute resource types are replaced with the Session Attribute and User Attribute resource types in the Audit Logs. To learn more, see [About Audit Logs](/zpa/about-audit-logs).

## May 16, 2024
### Feature Available
#### User Risk Scores Enhancements
The following enhancements were made to user risk scores:
- The ability to filter by IdP Name is supported on the User Risk Scores page of the ZPA Admin Portal.
- User risk scores associated to an IdP are automatically deleted if the IdP was deleted.
To learn more, see [About User Risk Scores](/zpa/about-user-risk-scores) and [About IdP Configuration](/zpa/about-idp-configuration).

### Feature Available
#### User Risk Scores Resource Type in Audit Logs
A new resource type for User Risk Scores was added to the Audit Logs page of the ZPA Admin Portal.
[See image.](#resourceTypeRisk)
To learn more, see [About Audit Logs](/zpa/about-audit-logs).
[]![Viewing the Audit Logs page](/sites/default/files/downloads/zpa-user-risk-scores-resource-type.png)

## May 13, 2024
### Feature Available
#### CNAME Filter Available in User Status Diagnostics
An update was made that lets customers filter the user status by CNAME.
To learn more, see [Viewing User Status Diagnostics](/zpa/viewing-user-status-diagnostics).

### Feature Available
#### Inspect ZPA Traffic with ZIA Security Services
Updates to ZPA and Zscaler Internet Access (ZIA) to inspect the private application traffic of a ZPA application segment include the addition of:
- Optimized traffic flow from ZPA to ZIA security services including:
- TLS inspection
- Firewall Control
- Malware protection
- Advanced Threat Protection (ATP)
- URL Filtering & Cloud App Control Policy
- File Type Control
- Firewall Control
- IPS Control
- Data Protection for download
- A ZIA Inspection client type filter in the ZPA User Status Diagnostics page.
- ZIA Inspection filters for enablement status and transaction type in the ZPA User Activity Diagnostics page.
- Session status codes for ZIA inspection.
To learn more, see [Viewing User Status Diagnostics](/zpa/viewing-user-status-diagnostics), [Accessing User Activity Diagnostics](/zpa/accessing-user-activity-diagnostics), [Understanding ZPA Session Status Codes](/zpa/understanding-zpa-session-status-codes), [Configuring Defined Application Segments](/zpa/configuring-application-segments#define-generalinfo), and [Configuring Forwarding Policy](/zia/configuring-forwarding-policy#source-ip-anchoring).

## May 08, 2024
### Feature Available
#### Updates to App Connector Status Diagnostics
The App Connector Status Diagnostics page includes a new field: App Connector Restart Reason.
To learn more, see [Accessing App Connector Status Diagnostics](/zpa/accessing-connector-diagnostics).

## May 02, 2024
### Feature Available
#### Increased Privileged Consoles Limit
The maximum number of privileged consoles available in an account has increased to 35,000. Each Microtenant can contain up to 6,000 privileged consoles.
You need licenses to access this increased limit. Contact your account manager for more information.
To learn more, see [Ranges & Limitations](/zpa/ranges-limitations).

### Feature Available
#### Updates to the PRA Portal
The Privileged Remote Access (PRA) Portal has a search bar designated for each section: Microtenants, Shared Sessions, and My Consoles. You can also filter and paginate the displayed privileged consoles.
To learn more, see [Accessing a Privileged Remote Access Portal](/zpa/accessing-privileged-remote-access-portal).

## April 30, 2024
### Feature Available
#### Events and Notifications Enhancements
The following enhancements were made to the events and notifications feature:
- An update was released that provides support for ZPA Private Service Edges when configuring the Bandwidth Utilization Exceeded Limit event. The threshold limit for this event was also decreased from 350 Mbps to 250 Mbps.
- An update was released that changed the labels for the SYSTEM_CONTROL_DISCONNECTED and SYSTEM_RESOURCE_CPU_STARVATION events to Control Connection Disconnected and CPU Starvation. These events are now supported in the ZPA Admin Portal when configuring notifications.
To learn more, see [Configuring Notifications](/zpa/configuring-notifications#events) and [Viewing and Managing Events and Notifications](/zpa/viewing-and-managing-events-diagnostics#Event).

## April 19, 2024
### Feature Available
#### Ranges & Limitations Update
The ZPA limits for intelligent segmentation tiers have been updated. The tiers show the different ML run frequencies based on the organization's SKU for ZPA.
To learn more, see [Ranges & Limitations](/zpa/ranges-limitations).

## April 16, 2024
### Feature Available
#### Updated Filters for App Connectors and ZPA Private Service Edges
There are new filters for the App Connectors and ZPA Private Service Edges pages: Current Software Version, ID, Manager Version, and Upgrade Status. The total number of App Connectors or ZPA Private Service Edges and the amount currently displayed on the page is at the bottom of the table.

## April 15, 2024
### Feature Available
#### Debug Mode for Isolation in Zscaler Private Access (ZPA)
Admins can enable debug mode for isolation profiles, which allows the user to record and gather troubleshooting data for any isolation sessions they create. The recorded session generates diagnostics for basic session information, HTTP Archive format files, console logs, and network logs exported from the web browser.
[See image.](#Enable-Debug-Mode)
To learn more, see [Using Debug Mode for Isolation](/isolation/using-session-debug-mode-isolation).
[]![Enabled toggle for Session Debug Mode.](/sites/default/files/downloads/isolation/profiles/enable_debug-mode.png)

## April 09, 2024
### Feature Available
#### Assistant to Connector in the ZPA API
An update was released that changed the labels from assistant to connector for the following endpoints in the ZPA cloud service API:
- GET /mgmtconfig/v1/admin/customers/{customerId}/assistantSchedule
- POST /mgmtconfig/v1/admin/customers/{customerId}/assistantSchedule
- PUT /mgmtconfig/v1/admin/customers/{customerId}/assistantSchedule/{id}
To learn more, see [Configuring Auto Delete for Disconnected App Connectors Using API](/zpa/configuring-auto-delete-disconnected-app-connectors-using-api) and the [App Connector Controller](/zpa/connector-controller).

## April 01, 2024
### Feature Available
#### Automated Software Updates
An update was released to enhance the automated software update mechanism for App Connectors and ZPA Private Service Edges. Failed component updates will be retried in each periodic software update until all App Connectors and ZPA Private Service Edges are upgraded.
To learn more, see [Understanding App Connector Software Upgrades](/zpa/understanding-connector-software-updates) and [Understanding ZPA Private Service Edge Software Upgrades](/zpa/understanding-zpa-private-service-edge-software-upgrades).

### Feature Available
#### Support for Title SCIM Attribute
An update was released that provides support for the Title SCIM Attribute for existing IdPs in the ZPA Admin Portal. As part of support for this functionality across ZPA, the Zscaler Operations team will perform a one-time update to the ZPA database that results in an Audit Log corresponding to the Admin ID showing [user]@root.zscaler.com. Admin audit log records are available to review in an organization’s tenant under Configuration & Control > Administration Control > Audit Logs.
To learn more, see [About SCIM](/zpa/about-scim) and [About Audit Logs](/zpa/about-audit-logs).

## March 28, 2024
### Feature Available
#### Internationalization
The ZPA Admin Portal supports the following languages, which you can select when signing into the portal: English, Spanish, French, German, Chinese, and Japanese.
To learn more, see [Accessing and Navigating the ZPA Admin Portal](/zpa/accessing-and-navigating-zpa-admin-portal#LoggingIn).

## March 26, 2024
### Feature Available
#### AppProtection UI Wizard
You can create a dynamic rule for an AppProtection profile to inspect the traffic of domains assigned to that AppProtection profile.
To learn more, see [Configuring AppProtection Dynamic Rules](/zpa/configuring-appprotection-dynamic-rules).

### Feature Available
#### Automatic Certificate Generation
You can enable AppProtection to inspect the traffic for an application segment with AppProtection. You can then select an AppProtection enrollment (CA) certificate to enroll AppProtection-enabled application segments. You can view the data for AppProtection-enabled application segment events on the Application Protocol Diagnostics page.
To learn more, see [Configuring Defined Application Segments](/zpa/configuring-application-segments), [Generating Zscaler-Issued Enrollment (CA) Certificates](/zpa/generating-zscaler-issued-enrollment-ca-certificates), and [Accessing Application Protocol Diagnostics](/zpa/accessing-application-protocol-diagnostics).

### Feature Available
#### Update to the Use Untrusted Certificate Option
When you are adding an application segment and you enable both Auto AppProtection and Browser Access, and if you are using an untrusted certificate, you must select Use Untrusted Certificates to access the related domain.
To learn more, [Configuring Defined Application Segments](/zpa/configuring-application-segments).

### Feature Available
#### ZPA API Improvements for Automatic Certificate Generation
The field autoAppProtectEnabled was added to the ZPA cloud service API to indicate if the application segment's traffic is inspected by AppProtection.
To learn more, see [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api).

## March 18, 2024
### Feature Available
#### Alternative Cloud Domain
ZPA provides the option to select an Alternative Cloud Domain that can override the default cloud domain for a ZPA Private Service Edge group. If deployed, the minimum required ZPA Private Service Edge version is 23.191.2 or later, the minimum required ZPA Public Service Edge version is 23.191.2 or later, and the minimum required App Connector version is 23.191.4 or later.
To learn more, see [Configuring ZPA Private Service Edges](/zpa/configuring-service-edges).

### Feature Available
#### Update to Only Forward Allowed Applications Rule Action
An update was released for ZPA Public Service Edges that allows users to use the Only Forward Allowed Applications rule action with Cloud Connector client types.
To learn more, see [Configuring Client Forwarding Policies](/zpa/configuring-client-forwarding-policies).

## March 11, 2024
### Feature Available
#### Version Profile Update for Previous Default
The Previous Default version profile option for App Connector Groups and ZPA Private Service Edge Groups was changed to a weekly update instead of daily. The version profile is configurable when setting up an App Connector Group or a ZPA Private Service Edge Group, and it includes designating a day and time each week when updates are scheduled to occur.
To learn more, see [Configuring App Connectors](/zpa/configuring-connectors#createconnectorgroup), [Configuring ZPA Private Service Edges](/zpa/configuring-service-edges#addgroup), and [Configuring a Version Profile](/zpa/configuring-version-profile).

## March 04, 2024
### Feature Available
#### App Connector Group Limits for Access Policies
An update was released that restricts the selection count of App Connector groups to 48 when configuring an access policy. This limit applies to new or edited policy rules after March 4, 2024.
To learn more, see [Configuring Access Policies](/zpa/configuring-access-policies) and [Ranges & Limitations](/zpa/ranges-limitations).

### Feature Available
#### Viewable Client and ZPA Private/Public Service Edge Traffic
An update was released that makes traffic between clients and ZPA Private Service Edges or ZPA Public Service Edges, and traffic between ZPA Private Service Edges and ZPA Public Service Edges, viewable in diagnostics for user status.
To learn more, see [Viewing User Status Diagnostics](/zpa/viewing-user-status-diagnostics#name).

## February 29, 2024
### Feature Available
#### Manager Software Updates
A recommended update was released that includes updated App Connector and ZPA Private Service Edge RPM packages for Red Hat Enterprise Linux 7.x and 8.x.
You can download the Manager Software for [App Connector](/zpa/connector-deployment-guide-centos-oracle-and-redhat#Deployment)s or [ZPA Private Service Edges](/zpa/service-edge-deployment-guide-centos-oracle-and-redhat#step3deploy) from our repository. To learn more, see [Understanding the Manager Software](/zpa/about-manager-software#managerUpgrades).

## February 28, 2024
### Feature Available
#### Privileged Remote Access API
ZPA supports customer-facing APIs for managing privileged portals, privileged approvals, privileged consoles, privileged credentials, privileged policies, and emergency access users.
To learn more, see [Understanding ZPA API](/zpa/understanding-zpa-api), [Configuring Privileged Portals Using API](/zpa/configuring-privileged-portals-using-api), [Configuring Privileged Approvals Using API](/zpa/configuring-privileged-approvals-using-api), [Configuring Privileged Consoles Using API](/zpa/configuring-privileged-consoles-using-api), [Configuring Privileged Credentials Using API](/zpa/configuring-privileged-credentials-using-api), [Configuring Privileged Policies Using API](/zpa/configuring-privileged-policies-using-api), [Configuring Emergency Access Users Using API](/zpa/configuring-emergency-access-users-using-api), and the [API Developer & Reference Guide](/zpa/zpa-api/api-developer-reference-guide/reference-guide).

### Feature Available
#### SRA to PRA in the ZPA API
An update was released that changed the labels from SRA to PRA in the ZPA cloud service API.
To learn more, see the [API Developer & Reference Guide](/zpa/zpa-api/api-developer-reference-guide/reference-guide).

### Feature Available
#### ZPA API Improvements to the Policy Set Controller
The following new endpoints to create and update a policy rule are exposed in the policy set controller for the ZPA cloud service API:
- POST /mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule
- PUT /mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}
To learn more, see the [API Developer and Reference Guide](/zpa/zpa-api/api-developer-reference-guide) and the [Policy Set Controller](/zpa/policy-set-controller).

### Feature in Limited Availability
#### Microtenant Support for Privileged Remote Access
Role-based administration control via a Microtenant is supported for Privileged Remote Access (PRA). Additionally, the ability to enable approval-based access without an authentication domain is available when adding a Microtenant.
[See image.](#AddMicrotenant)
Contact Zscaler Support to enable this feature for your organization.
To learn more, see [About Microtenants](/zpa/about-microtenants), [Configuring Microtenants](/zpa/configuring-microtenants), [Moving Resources from a Microtenant](/zpa/moving-resources-microtenant), and [Privileged Remote Access Management](/zpa/privileged-remote-access-management).
[]![Add Microtenant window ](/sites/default/files/downloads/zpa-add-microtenant-window.png)

## February 27, 2024
### Feature Available
#### ZPA Private Service Edge Deployment on Docker
ZPA Private Service Edge deployments on Docker platforms are available. To learn more, see the [Private Service Edge Deployment Guide for Docker](/zpa/private-service-edge-deployment-guide-docker).

## February 20, 2024
### Feature Available
#### External Device ID
The identifier that associates an external MDM device ID with devices in the Zscaler Client Connector Portal is available in ZPA User Status Diagnostics and Live Logs.
To learn more, see [Viewing User Status Diagnostics](/zpa/viewing-user-status-diagnostics) and [About Live Logs](/zpa/about-live-logs).

### Feature Available
#### Role-Based Administration Control Enhancements
The following enhancements were made to role-based administration control:
- Dashboards, Support Information, and events and notifications are supported within a Microtenant.
- The ability to filter requests by the Microtenant that belongs to the application segment, or by the Microtenant that the application segment has been shared to, is available in the User Activity Diagnostics and Live Logs.
Contact Zscaler Support to enable this feature for your organization.
To learn more, see [About Microtenants](/zpa/about-microtenants), [Accessing User Activity Diagnostics](/zpa/about-user-activity-diagnostics), [About Live Logs](/zpa/about-live-logs), and [About Support Information](/zpa/about-support-information).

## February 07, 2024
### Feature Available
#### Disabling Print for ZPA Isolation Profiles
Disabling the printing feature for an isolation profile disables all possibility of being able to print the web page or document that is rendered in isolation. When printing is disabled on an isolation profile, you cannot see the print option from the right-click menu, or the print button in the Isolation Bar. If you try to select File > Print from the browser menu, or enter the key command CTRL/CMD+P shortcut, a message appears stating that it is disabled by policy.
To learn more, see [Creating Isolation Profiles for ZPA](/isolation/creating-isolation-profiles-zpa).

## February 06, 2024
### Feature Available
#### Bypass During Reauthentication Disabled Depending on App Segment Configuration
If you select Always for the Bypass option when configuring a defined application segment, the option for Bypass during Reauthentication is automatically disabled.
[See image.](#bypass-always-example)
To learn more, see [Configuring Defined Application Segments](/zpa/configuring-application-segments).
[]![add-app-seg_bypass-by-reauth-disabled-by-default.png](/sites/default/files/downloads/zpa/draft-clientless-config-application-segments/add-app-seg_bypass-by-reauth-disabled-by-default.png)

### Feature Available
#### Resolved Issues
An update was released to address an issue where some admins were prevented from logging in to the ZPA Admin Portal using single sign-on (SSO). This was due to a case mismatch between the SAML assertion from the IdPs and the user emails for the admin accounts in ZPA.

## January 31, 2024
### Feature Available
#### Server-Side Certificate Posture Validation
An update was released that provides support for server-side certificate posture validation. Contact Zscaler Support to enable this feature for your organization.
To learn more, see [Configuring Device Posture Profiles](/client-connector/configuring-device-posture-profiles).

### Feature in Limited Availability
#### Enhancement of Client-to-Client Connectivity
An update was released that ensures client-to-client connectivity is successful when source and destination users are connected to different ZPA Private Service Edges or ZPA Public Service Edges and there is no dedicated application segment configured for client-to-client functionality. Contact Zscaler Support to enable this feature for your organization.

## January 19, 2024
### Feature Available
#### Source IP Anchoring Dashboard
The Source IP Anchoring dashboard is available in the ZPA Admin Portal and includes tools and widgets to help you monitor the usage and metrics of your organization's Source IP Anchoring.
[See image](#sipa-dashboard).
To learn more, see [Viewing the Source IP Anchoring Dashboard](/zpa/viewing-source-ip-anchoring-dashboard).
[]![sipa-dashboard-full-rev02-01.png](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2024/sipa-dashboard-full-rev02-01.png)

## January 17, 2024
### Feature Available
#### AWS, Azure, and Docker Hub Image Updates
New App Connector images are available for AWS EC2, Microsoft Azure, and Docker to address routine security patches. New ZPA Private Service Edge images are available in AWS EC2 to address routine security patches.
To learn more, see the App Connector Deployment Guides for [AWS](/zpa/connector-deployment-guide-amazon-web-services), [Azure](/zpa/connector-deployment-guide-microsoft-azure), and [Docker](/zpa/app-connector-deployment-guide-docker), and the ZPA Private Service Edge Deployment Guide for [AWS](/zpa/service-edge-deployment-guide-amazon-web-services).

### Feature Available
#### KVM Image Support
New App Connector and ZPA Private Service Edge images are available in the KVM qcow2 format to support Equinix Network Edge.

### Feature Available
#### VMware Image Updates
New App Connector and ZPA Private Service Edge images are available for VMware that address routine security patches.
To learn more, see [App Connector Deployment Guide for VMware Platforms](/zpa/connector-deployment-guide-vmware-platforms#VM_VCENTER), [App Connector Deployment Guide for Nutanix AHV](/zpa/app-connector-deployment-guide-nutanix-ahv#deploy), and [ZPA Private Service Edge Deployment Guide for VMware Platforms](/zpa/service-edge-deployment-guide-vmware#vcenter).

## January 16, 2024
### Feature Available
#### Redirection Policy
ZPA supports redirection policy rules that allow you to set criteria for preferring ZPA Private Service Edges over ZPA Public Service Edges. You can configure redirection policy rules to prefer ZPA Private Service Edges based on country code and client type. You can also configure redirection to prefer ZPA Private Service Edges based on geographical proximity.
To learn more, see [About Redirection Policy](/zpa/about-redirection-policy) and[ Configuring Redirection Policies](/zpa/configuring-redirection-policies).

### Feature Available
#### ZPA API Improvements for Bulk Updating Policy Rules
The ability to bulk update the order of all rules within a policy set is available via the cloud service API.
To learn more, see [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api#bulkUpdatingRuleOrder) and the ZPA cloud service API [Reference Guide](/zpa/policy-set-controller).

## January 11, 2024
### Feature Available
#### File Size Limit Increase in Isolation for ZPA
The size limit for downloading and uploading files in Isolation has increased to 1 GB. End users can expect an increase of time to upload files from 9 minutes to 10 minutes. If downloading or uploading multiple files at once, the size limit is 2 GB.
To learn more, see [Transferring and Viewing Files in Isolation](/isolation/transferring-and-viewing-files-isolation) and [Limits in Isolation](/isolation/limits-isolation).

### Feature Available
#### Last Known Public and Private IP Addresses
The Public IP and Private IP fields in the tables of the App Connectors and Private Service Edges pages show the last known public or private IP address when an App Connector or ZPA Private Service Edge disconnects.
To learn more, see [About App Connectors](/zpa/about-connectors) and [About ZPA Private Service Edges](/zpa/about-zpa-private-service-edges).

### Feature Available
#### OS Update for App Connectors and ZPA Private Service Edges
The App Connector Platform and Private Service Edge Platform fields have been renamed to App Connector Host Platform and Private Service Edge Host Platform on the App Connector and ZPA Private Service Edge pages, respectively. The App Connector Host OS and Private Service Edge Host OS fields have a new value—the run time OS that the binary is running on for each respective feature. The previous Host OS information is displayed in the new App Connector Package OS and Private Service Edge Package OS fields on the App Connectors and ZPA Private Service Edge pages, respectively.
To learn more, see [About App Connectors](/zpa/about-connectors) and [About ZPA Private Service Edges](/zpa/about-zpa-private-service-edges).
