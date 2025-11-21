# Release Upgrade Summary (2021)
Source: https://help.zscaler.com/zia/release-upgrade-summary-2021

This article provides a summary of all new features and enhancements per Zscaler cloud for Zscaler Internet Access (ZIA). Zscaler will email a notification to your organization's registered support contacts approximately one week before your cloud is upgraded. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com).

**Clouds:** zscaler.net, zscalerone.net, zscalertwo.net, zscalerthree.net, zscloud.net, zscalerbeta.net
The following service updates were deployed to zscaler.net on

## December 10, 2021
### Feature Available
#### Firewall Support for Remote Users
The following changes are introduced in the ZIA Admin Portal to support firewall rules for all remote users:
- A new option, Enable Firewall for Z-Tunnel 1.0 and PAC Road Warriors, is added to the Administration > Advanced Settings page. Enabling this option automatically enables Source IP Anchoring support for Z-Tunnel 1.0 traffic. This option is enabled by default for new organizations, but disabled for existing ones.
[See image.](#road-warrior-button)
[]![Screenshot of Enable Firewall for PAC and Z-Tunnel 1.0 option](/sites/default/files/downloads/firewall-road-warrior%20(1%20(1).png)
- A new option, Road Warrior, is added under the Location criterion in the [firewall](/zia/configuring-firewall-policies) and [forwarding](/zia/configuring-forwarding-policies) policy, exclusively for remote user traffic (i.e., Z-Tunnel 1.0, Z-Tunnel 2.0, and PAC).
[See image.](#road-warrior-policy)
[]![Screenshot of Road Warrior as Location criterion](/sites/default/files/downloads/ZIA-6.1r-road-warriors-option.png)
To learn more, see [About Advanced Settings](/zia/about-advanced-settings).

### Feature Available
#### SaaS Security API
The following enhancements are available for SaaS Security API.
Updates to SaaS Application Tenants
You can add Webex Teams as a SaaS Application Tenant.
[See image.](#Webex_Teams)
To learn more, see [Adding SaaS Application Tenants](https://help.zscaler.com/zia/adding-saas-application-tenants).
Updates to SaaS Security API Control Policies & Scan Configuration
You can configure the SaaS Security API Control policies and scan schedules for Webex Teams, a collaboration application.
To learn more, see [Configuring the SaaS Security API Control Policy](/zia/configuring-saas-security-api-control-policy).
Updates to the SaaS Assets Summary Report
You can view Webex Teams (collaboration application category) in the SaaS Assets Summary Report.
To learn more, see [SaaS Assets Summary Report](/zia/saas-assets-summary-report).
Updates to the SaaS Assets Report
You can view Webex Teams (collaboration application category) in the SaaS Assets Report.
To learn more, see [Saas Assets Report](/zia/saas-assets-report) and [SaaS Assets Report: Assets with Incidents](/zia/saas-assets-report-assets-incidents).
Updates to SaaS Security Insights & Insights Logs
You can view Webex Teams (collaboration application category) in SaaS Security Insights and Insights Logs.
To learn more, see [SaaS Security Insights](/zia/saas-security-insights) and [SaaS Security Insights Logs](/zia/saas-security-insights-logs).
[![Webex Teams tenant application icon](/sites/default/files/downloads/WebexTeams_01_AddSaaS.png)
]

### Feature Available
#### SaaS Security Posture Control
The following enhancements are available for SaaS Security Posture Control.
Updates to SaaS Application Tenants
You can add Microsoft 365 as a SaaS Application Tenant.
[See image.](#M365Tenant)
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
Updates to the SaaS Security Posture Control Policy & Report
Microsoft 365 is an available application for the SaaS Security Posture Control policy and SaaS Security Posture Report.
To learn more, see [Configuring the SaaS Security Posture Policy](/zia/configuring-saas-security-posture-control-policy) and [SaaS Security Posture Report](/zia/saas-security-posture-report).
[![Microsoft 365 SaaS Application Tenant](/sites/default/files/downloads/M365_01_Provider3.png)
]

### Feature Available
#### Shadow IT Enhancements
The following enhancements are now available for the Shadow IT feature:
Added Cloud Application Risk Profile
The cloud application risk profile feature within the ZIA Admin Portal (Administration > Risk Profiles) allows you to create risk profiles with cloud application attributes and associate them with the cloud app control rules. This feature provides granular cloud application attributes as criteria for the cloud app control rules.
You can select either the Cloud Applications or Cloud Application Risk Profile field in the Add Cloud App Control rule window.
[See image.](#risk-profile)
To learn more, see [About Cloud Application Risk Profile](/zia/about-cloud-application-risk-profile).
[]![Screenshot of the Cloud Application Risk Profile page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-6.1r-Cloud-Application-Risk-Profile.png)
Updates to Administration
You can view and edit the sanctioned state (Sanctioned or Unsanctioned) of an application from the Cloud Application Status page (Administration > Cloud Application Status).
[See image.](#cloud-app)
[]![Screenshot of the Cloud Application Status page](/sites/default/files/downloads/ZIA-6.1r-Cloud%20Application%20Status.png)
To learn more, see [Shadow IT Report](/zia/shadow-it-report).
Updates to the SaaS Security Report
You can click the Edit Application Status button from the Analytics > SaaS Security Report > Applications > Application Information page for the application you select to view. You'll be redirected to the Edit Cloud Application window on the Cloud Application Status page, where you can edit the sanctioned state of that application.
[See image.](#edit-cloud-app)
[]![Screenshot of the Edit Cloud Application Status button](/sites/default/files/downloads/ZIA-6.1r-Edit-Cloud-Application-Status.png)
To learn more, see [About Cloud Application Status](/zia/about-cloud-application-status).

### Feature Available
#### Support for TLS 1.3
Zscaler supports hardware based acceleration for TLS 1.3 on this cloud with the following latest cipher suites:
- TLS_AES_256_GCM_SHA384
- TLS_CHACHA20_POLY1305_SHA256
- TLS_AES_128_GCM_SHA256
For TLS traffic that is subject to SSL inspection, this is a seamless upgrade, after which the service will prefer and propose TLS 1.3 on the client side and server side connections respectively.
To learn more, see [Zscaler SSL/TLS Support](/zia/zscaler-ssl-tls-support).

## November 19, 2021
### Feature Available
#### Google App Enhancement in Tenant Profiles
The Allow Consumer Access field is now added to the Add Tenant Profile page (Administration > Tenant Profiles > Add Tenant Profile) for Google App. The field allows consumers access to the domains in the tenant profile based on the selection.
[See image.](#tenant-profile)
To learn more, see [Adding Tenant Profiles](/zia/adding-tenant-profiles).
[] ![Screenshot of the Add Tenant Profile Window.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-6.1r-Add-Tenant-Profile.png)

### Feature Available
#### One Click Enhancements
The following enhancements are now available for the one click feature:
New URL Super Category for SSL Inspection Policy
The Microsoft Office 365 super-category is added under the URL Categories field on the SSL Inspection Policy rule page (Policy > SSL Inspection > SSL Inspection Policy > Add SSL Inspection Rule). This super-category consists of the following categories:
- MS O365 Allow
- MS O365 Default
- MS O365 Optimize
[See image.](#ssl-inspection-policy)
To learn more, see [About URL Categories](/zia/about-url-categories#Business).
Predefined Office 365 One Click Rule in the Cloud App Control Policy
A predefined Office 365 One Click rule is enabled on the Cloud App Control Policy page (Policy > URL & Cloud App Control > Cloud App Control Policy) for the following categories when you select the Enable Microsoft-Recommended One Click Office 365 Configuration on the Advanced Policy Settings tab (Policy > URL & Cloud App Control > Advanced Policy Settings):
- Collaboration & Online Meetings: The predefined rule in this category allows the traffic for the following cloud applications.
- Yammer
- SharePoint Online
- Microsoft Teams
- Microsoft Sway
- Productivity and CRM Tools: The predefined rule in this category allows the traffic for the following cloud applications.
- Common Office 365 Applications
- Microsoft Dynamics 365
- Microsoft Delve
- Microsoft Power BI
- Microsoft Planner
- File Sharing: The predefined rule in this category allows the traffic for the OneDrive cloud application.
- Hosting Providers: The predefined rule in this category allows the traffic for the Microsoft Azure cloud application.
- IT Services: The predefined rule in this category allows the traffic for the following cloud applications.
- Microsoft Azure AD
- Microsoft Intune
- Webmail: The predefined rule in this category allows the traffic for the Outlook cloud application.
To learn more, see [About Microsoft One Click Options](/zia/about-microsoft-one-click-options#effectsnew).
Predefined UCaaS One Click Rule in the Cloud App Control Policy
A predefined UCaaS One Click rule is enabled on the Cloud App Control Policy page for the Collaboration & Online Meetings category when you select the UCaaS applications (Zoom, RingCentral, or LogMeIn) on the Advanced Policy Settings tab. This rule allows the traffic for the selected UCaaS applications.
To learn more, see [Configuring Advanced URL Policy Settings](/zia/configuring-advanced-url-policy-settings#ucaas).
[]![Screenshot of the Add SSL Inspection Rule Window.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-6.1r-Add-SSL-Inspection-Rule.png)

## November 12, 2021
### Feature Available
#### Access Control for Zscaler Client Connector Portal
A new option, Zscaler Client Connector Portal is now available in the Administration > Role Management > Add Administrator Role page under the Access Control (Web and Mobile) functional scope. Using this option, you can choose to enable or disable access to Zscaler Client Connector Portal for the admins.
[See image.](#zscaler-client-connector-portal)
To learn more, see [Adding Admin Roles](/zia/adding-admin-roles).
[]![Screenshot of Zscaler Client Connector Portal option under Access Control (Web and Mobile) in Role Management page](/sites/default/files/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-admin-roles/ZIA-release-note-access-control-zscaler-client-connector-portal.png)

### Feature Available
#### Blocking Domain Fronting
The existing option, Block on URL FQDN & Host Header Mismatch is renamed to Block Domain Fronting in the Advanced Settings page (Administration > Advanced Settings).
Enabling this option blocks domain fronting for HTTP/S transactions that have an FQDN mismatch between:
- The request URL and the request's host header
- The SNI (Server Name Indication) and the inner request's host header
[See image.](#block-domain-fronting)
[]![Screenshot for the Block Domain Fronting option in Advanced Settings](/sites/default/files/downloads/ZIA-6.1r-Block-Domain-Fronting.png)
To learn more, see [About Advanced Settings](/zia/about-advanced-settings).
Updates to the Insights and NSS Reports
The policy reason, Access denied due to URL FQDN and Host Header Mismatch seen in Insights and NSS reports is renamed to Access denied due to Domain Fronting.
To learn more, see [Policy Reasons](/zia/policy-reasons).

### Feature Available
#### Cloud App & URL Exceptions for DLP
You can now exempt specific cloud applications and URLs from DLP evaluation by adding them to the Cloud Apps & URL Exceptions for DLP list.
[See image.](#URLCloudAppimage)
To learn more, see [Exempting Cloud Apps and URLs from DLP Evaluation](/zia/exempting-cloud-apps-and-urls-dlp-evaluation).
[]![The Cloud App & URL Exceptions for DLP page in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Cloud-App-URL-Exceptions-DLP.png)

### Feature Available
#### Cloud App Control Policy Enhancement
You can now create a cloud app control policy rule with the new Action option, Isolate. If your organization uses Cloud Browser Isolation, you will see this new option in addition to the existing Actions of Allow and Block. When the Isolate action is selected, the policy framework allows you to select one of the isolation profiles created for your organization in the Cloud Browser Isolation Portal. Any traffic matching the defined rule will be isolated as per the selected isolation profile.
The Isolate action is not applicable for the DNS Over HTTPS Services Rule for Cloud App Control.
[See image](#isolate-action).
To use this action, you must first [create isolation profiles](/zia/configuring-browser-isolation) for your organization in the Zscaler Cloud Browser Isolation Portal.
To learn more, see [Adding Rules to Cloud App Control Policy](/zia/adding-rules-cloud-app-control-policy).
[]![Screenshot of the Add Cloud App Control Rule with Isolate action.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Cloud-App-Control-Rule-with-Isolate-action.png)

### Feature Available
#### DLP & EDM Support for Spanish Social Security Numbers
We have added a new predefined DLP dictionary: Social Security Number (Spain). This dictionary detects social security numbers from Spain.
When creating your EDM templates, you can also select Social Security Number (Spain) as a Data Type.
To learn more, see [Editing Predefined DLP Dictionaries](/zia/editing-predefined-dlp-dictionaries) and [Creating an Exact Data Match Template](/zia/creating-exact-data-match-template).

### Feature Available
#### DLP Support for Japanese PII
We have added two new predefined DLP dictionaries:
- Corporate Number (Japan): This dictionary detects corporate numbers from Japan.
- My Number (Japan): This dictionary detects My Numbers from Japan.
Zscaler supports adding phrases in Japanese for custom DLP dictionaries, and only supports Unicode for Japanese phrases.
To learn more, see [Editing Predefined DLP Dictionaries](/zia/editing-predefined-dlp-dictionaries) and [Defining Phrases for Custom DLP Dictionaries](/zia/defining-phrases-custom-dictionaries).

### Feature Available
#### Support for Devices and Device Groups
A new Device Groups page is added to the ZIA Admin Portal under Administration.
- The Devices page displays all the devices in your organization that have the Zscaler Client Connector (formerly Zscaler App or Z App) deployed.
[See image.](#devices)
To learn more, see [About Devices](/zia/about-devices).
- The Device Groups page displays a list of predefined groups that are defined based on the OS types of the devices. The devices that have the Zscaler Client Connector (formerly Zscaler App or Z App) deployed are categorized under respective groups based on their OS type.
[See image.](#device_groups)
To learn more, see [About Device Groups](/zia/about-device-groups).
Two new criteria, Devices and Device Groups are also added to the following policies:
- [URL Filtering](/zia/configuring-url-filtering-policy)
- [Cloud App Control](/zia/adding-rules-cloud-app-control-policy)
- [SSL Inspection](/zia/configuring-ssl-inspection-policy)
- [Firewall Control](/zia/configuring-firewall-filtering-policy)
- [File Type Control](/zia/configuring-file-type-control-policy)
[]![Screenshot of the Devices tab in Adminstration > Device Groups page](/sites/default/files/downloads/zia/policies/about-devices/ZIA-release-note-devices-page.png)
[]![Screenshot of the Device Groups tab in Adminstration > Device Groups page](/sites/default/files/downloads/zia/policies/about-device-groups/ZIA-release-note-device-groups-page.png)

## November 05, 2021
### Feature Available
#### IPS Control Enhancements
The following enhancements were made to the IPS Control page (Policy > IPS Control > Add IPS Control Rule):
- The Threat Category field is renamed to Advanced Threat Category.
- The following categories under the Advanced Threat Category field are no longer available:
- Suspicious Content
- Suspicious Destinations
- Advanced Security
[See image.](#ips)
Updates to Insights Logs
The following enhancements were made to the Insights Logs pages:
- The filter Threat Category is renamed to Advanced Threat Category in Firewall Insights Logs.
- The filter Advanced Threat Super Category is renamed to Advanced Threat Category in Mobile and Web Insights Logs.
[See image.](#logs)
To learn more, see [About IPS Control](/zia/about-ips-control).
[]      ![Advanced Threat Category criterion in IPS Control](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/logs/mobile-insights-logs-filters/ZIA-6.2-advanced-threat-category.jpg)
[] ![Advanced Threat Category filter in Insights Logs](/sites/default/files/downloads/ZAI-6.2-advanced-threat-cat-logs.jpg)

### Feature Available
#### Managing Users Accessing Cloud App from Unmanaged Devices
You can now define what a managed device is for a cloud app in the Administration > Identity Proxy Settings > Add/Edit Cloud Application window and subsequently block or browser isolate sessions from the unmanaged devices. If you choose to browser isolate, the users get view-only access to the cloud app without the ability to modify or download data to their unmanaged devices.
[See image.](#zia-unmanaged-devices)
This feature introduces the following updates to the Add/Edit IdP window and the End User Notifications (EUNs) page:
- Two new fields, Device Trust Attribute and Device Trust Attribute Value are added to the Administration > Authentication Settings > Identity Provider > Add/Edit IdP window, where you can enter the trust attribute and the trust attribute value mapping to your IdP configuration to identify managed devices.
[See image.](#idp-device-trust)
- A new Notification Text field is added in the IdP Proxy Notification section of the Administration > End User Notifications page, where you can enter the policy request message that appears when a user is blocked due to a violation in the IdP Proxy settings.
[See image.](#zia-idp-message)
To learn more, see [Configuring Block Notifications](/zia/configuring-block-notifications), [Configuring the Zscaler Identity Proxy for Cloud Apps](/zia/configuring-zscaler-identity-proxy-cloud-apps), and [Adding Identity Providers](/zia/adding-identity-providers).
[]![IdP Proxy notification in EUNs](/sites/default/files/downloads/EUNs-Idp-Proxy.png)
[] ![Device trust field in the IdP configuration](/sites/default/files/downloads/ZIA-device-trust.png)
[]![Define unmanaged device and manage traffic in the ZIA admin Portal](/sites/default/files/downloads/zia-manage%20device.png)

### Feature Available
#### Support for Zscaler Management Portal for Partners
As Zscaler partners, you can now manage your provisioned customers and tenants from the new Zscaler Management Portal for Partners. The Management Portal provides visibility over your customer and tenant accounts.
Using the Management Portal, you can:
- Oversee customers across different Zscaler clouds
- View customer and tenant account configurations and policies
- View the policy templates that are applied to your tenants
- White label the ZIA Admin Portal that your tenants access
- Access the tenants' ZIA Admin Portal via SSO
To learn more, see [What is Zscaler Management Portal for Partners?](/zia/what-zscaler-management-portal-partners)

## October 08, 2021
### Feature Available
#### Enhancements to Sandbox Report
The Sandbox BAUI Report now includes the following enhancements:
- An HTTPS section under Network Packets which includes new JA3 and JA3 Digest information compared to the HTTP section.
[See image.](#HTTPS)
- A new MITRE Adversarial Tactics, Techniques, and Common Knowledge (ATT&CK) tile to view the MITRE ATT&CK Techniques page and see which techniques have been hit by the corresponding color-coded number.
[See image.](#MITRE)
[![Screenshot of new HTTPS section with JA3 and JA3 Digest information](/sites/default/files/downloads/zia/HTTPS%20section%20v2.png)
]
[![Screenshot of new MITRE tile.](/sites/default/files/downloads/zia/MITRE%20Tile%20v2.png)
]![New MITRE page](/sites/default/files/downloads/zia/MITRE%20Page%20v2.png)

## September 24, 2021
### Feature Available
#### Custom High Confidence Phrases
For applicable predefined DLP dictionaries, you can now configure custom high confidence phrases. As part of this enhancement, the dictionaries will also display all of their default high confidence phrases.
[See image.](#image)
To learn more, see [Editing Predefined DLP Dictionaries](/zia/editing-predefined-dlp-dictionaries).
[]![Adding custom high confidence phrases for predefined DLP dictionaries](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Predefined-DLP-Dictionary-Phrases.png)

### Feature Available
#### Enhancements to the SaaS Security API DLP Policy
The following enhancements are now available for the SaaS Security API DLP policy.
Support for Zscaler Incident Receiver & Email Notifications
The SaaS Security API DLP policy now supports the following features for all application types:
- Zscaler Incident Receiver
- Email Notification
[See image.](#CASB-DLP-Rule)
To learn more, see [About SaaS Security API DLP](/zia/about-saas-security-api-dlp).
[]![Screenshot of the SaaS Security API DLP Rule page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-CASB-Add-DLP-Rule.jpg)
Support for Box Classification Labels
When creating SaaS Security API DLP policy rules for your Box tenants, you can now apply classification labels defined in Box.
[See image.](#box-file-label)
To learn more, see [Configuring the SaaS Security API DLP Policy](https://help.zscaler.com/zia/configuring-saas-security-api-dlp-policy).
[]![Screenshot of Apply Classification label for Box files in the Add DLP Rule page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-saas-security-api-apply-box-classification-label.png)

## September 03, 2021
### Feature Available
#### Support for External Syslog Server Forwarding on Zscaler Incident Receiver
You can now configure external syslog server forwarding on your Zscaler Incident Receiver VM using the following command:
sudo zirsvr configure-syslog-server
To learn more, see [Configuring the Zscaler Incident Receiver](/zia/configuring-zscaler-incident-receiver).

## August 20, 2021
### Feature Available
#### Additional Language Support for EUNs
The language support for EUNs is now extended to the following languages:
- Italian
- Indonesian
- Korean
- Spanish (Latin America)
- Turkish
- Thai
- Vietnamese
To learn more, see [Multiple Language Support for EUNs](/zia/multiple-language-support-for-euns).

### Feature Available
#### Enable or Disable Default Admins
You can now enable or disable the Default Admin account using the Status option.
[See image.](#status-default-admin)
You can also update the account's status (i.e., disabled or enabled) using Admin & Role Management endpoints within the cloud service API.
To learn more, see [About Administrators](/zia/about-administrators) and [Adding ZIA Admins](/zia/adding-zia-admins).
[]![Screenshot of the Status field for Default Admins in the Administrators page](/sites/default/files/downloads/zia/authentication-administration/administrator-role-management/administrators/about-administrators/ZIA-release-note-default-admin-status-option.png)

### Feature Available
#### Rule Labels
The rule labels feature within the ZIA Admin Portal allows you to create labels and associate them with policy rules. This feature enables you to logically group your organization's policies by label.
The URL Filtering Policies resources within the cloud service API have also been updated. So you can now create rule labels for [URL Filtering](/zia/about-url-filtering) policy rules using `POST` and `PUT /urlFilteringRules`.
[See image.](#rule-label-option)
To learn more, see [About Rule Labels](/zia/about-rule-labels) and [API Reference](/zia/about-api).
[]![Screenshot of the Add URL Filtering Rule window with the Rule Label option.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Add-URL-Filtering-Rule-Window.png)

### Feature Available
#### SaaS Security Activities & Alerts
The following features are now available for SaaS Security API.
If you have Microsoft OneDrive or SharePoint tenants created prior to this release, you must reauthorize them to use these features. To learn more, see [About SaaS Application Tenants](/zia/about-saas-application-tenants#seeimage-reauth).
SaaS Security Activity Alerts
With SaaS Security Activity Alerts, you can now configure alerts that allow you to track specific SaaS application activities and view the users who performed those activities. When a user performs an activity that triggers an alert, the Zscaler service logs it in the SaaS Security Activities & Alerts Report.
[See image.](#activity-alerts-image)
To learn more, see [About SaaS Security Activity Alerts](/zia/about-saas-security-activity-alerts).
SaaS Security Activities & Alerts Report
The SaaS Security Alerts & Activities Report gives you an overview of all your users’ SaaS application activities and triggered SaaS Security activity alerts. You can also view further details about each alert and activity.
[See image.](#report-image)
To learn more, see [SaaS Security Alerts & Activities Report](/zia/saas-security-alerts-activities-report).
New Log Type for SaaS Security Activity
A new log type has been added to NSS Feeds for SaaS Security Activity.
To learn more, see [Adding NSS Feeds for SaaS Security Activity Logs](/zia/adding-nss-feeds-saas-security-activity-logs).
New SaaS Security Activity Fields for NSS Feed Outputs
The following web log fields were added to NSS Feeds for SaaS Security Activity:
- `%d{intlogtime}`
- `%d{inteventtime}`
- `%d{userid}`
- `%d{cid}`
- `%d{tid}`
- `%d{src_id}`
- `%d{appid}`
- `%d{abstime}`
- `%d{objtype1}`
- `%d{objcnt1}`
- `%d{objtype2}`
- `%d{objcnt2}`
- `%s{logtime}`
- `%s{eventtime}`
- `%s{loc_name}`
- `%s{username}`
- `%s{tenant}`
- `%s{appname}`
- `%s{objnames1}`
- `%s{objnames2}`
[]![The SaaS Security Activity Alerts page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Activity-Alerts-page.png)
[]![The SaaS Security Alerts & Activities tab with the Alerts Report being displayed](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-6.1-SaaS-Alerts-Activities.png)

### Feature Available
#### SaaS Security API
The following enhancements are now available for SaaS Security API.
Updates to SaaS Application Tenants
To add a Dropbox tenant, you must now enter your Dropbox Enterprise ID.
[See image.](#DropboxUpdate1)
To add a Salesforce tenant, you must now choose between using your Salesforce Sandbox or Production environments. The sandbox environment allows you to test changes without affecting your users, while changes in the production environment go live for your users.
[See image.](#SalesforceRelease1)
To learn more, see [Add SaaS Application Tenant](/zia/adding-saas-application-tenants).
SaaS Security API Scanning Exceptions
For file sharing applications, you can now exempt specific folders from the SaaS Security API Control policy in the new Scanning Exceptions tab (Policy > SaaS Security API Control).
When you configure a scanning exception for a folder, the Zscaler service completely ignores the files within the folder, i.e., its files aren’t evaluated with the SaaS Security API DLP and Malware Detection policies.
[See image.](#saas-security-api-scanning-exceptions)
To learn more, see [Configuring SaaS Security API Scanning Exceptions](/zia/configuring-saas-security-api-scanning-exceptions).
New Column in SaaS Assets Report
A new column, Remediation Action, was added to the SaaS Assets Report: Assets with Incidents page, under File Sharing Applications.
To learn more, see [SaaS Assets Report: Assets with Incidents](/zia/saas-assets-report-assets-incidents).
[![New UI for adding Dropbox as a SaaS tenant](/sites/default/files/downloads/zia/saas-security-api-policy/Dropbox%20Release%20Note.png)
]
[![Adding Salesforce as a tenant](/sites/default/files/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Salesforce%20Release%20Note.png)
]
[]![SaaS Security API Scanning Exceptions](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-SaaS-Security-API-Scanning-Exceptions.png)

### Feature Available
#### Support for Restricted Admin Access to ZIA Admin Portal
You can now enforce access restrictions to the ZIA Admin Portal based on the source IP address of the admin trying to log in.
[See image.](#restricted-access-admin-portal)
To learn more, see [Configuring Restricted Access for Admins](/zia/configuring-restricted-access-admins).
[]![Screenshot of Restricted Access section in the Administration Management page.](/sites/default/files/downloads/zia/authentication-administration/administrator-role-management/configuring-restricted-access-admins/zia-configuring-restricted-access-admins-image.png)

## August 06, 2021
### Feature Available
#### Updates to Cloud Service API
The cloud service API now fully supports create, read, update, and delete (CRUD) for Data Loss Prevention (DLP) Dictionaries:
- `GET /dlpDictionaries`
- `POST /dlpDictionaries`
- `GET /dlpDictionaries/lite`
- `GET /dlpDictionaries/{dlpDictId}`
- `PUT /dlpDictionaries/{dlpDictId}`
- `DELETE /dlpDictionaries/{dlpDictId}`
- `POST /dlpDictionaries/validateDlpPattern`
To learn more about each endpoint, see the [API Reference](/zia/api/) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection was also updated to include new and updated resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

## July 23, 2021
### Feature Available
#### Block HTTP/S Traffic on URL FQDN & Host Header Mismatch
You can now block HTTP/S transactions if an FQDN mismatch is found between the request URL and the request's host header by enabling the Block on URL FQDN & Host Header Mismatch option from the  Administration > Advanced Settings page in the ZIA Admin Portal.
[See image.](#Block-Mismatch)
[]![Option to block mismatch in URL FQDN and Host Header](/sites/default/files/downloads/ZIA-url%20and%20host%20mismatch.png)
To learn more, see [About Advanced Settings](/zia/about-advanced-settings).
This feature introduces the following updates to the Web Insights Logs and the corresponding NSS feed output formats:
- A new weblog field, Domain Fronted Host Header is added to capture the HTTP/S request host header in case of a mismatch with the URL FQDN. This field is available for filtering and as a new column in Web Insights. It is also available for streaming through NSS with the syntax `%s{df_hosthead}`. If there is no mismatch, the field value will be empty. To detect such blocks in the weblogs, you can search for the policy reason string, Access denied due to URL FQDN and Host Header Mismatch.
- The existing field, Domain Fronted Hostname is renamed to Domain Fronted SNI in Web Insights. This field captures mismatches between SNI and the corresponding HTTPS request host headers.
[See image.](#weblogs-filter)
[]![Updates to the filtering option in the Web Insights Logs page](/sites/default/files/downloads/ZIA-SNI-hostheader.png)
To learn more, see [Web Insights Logs Filters](/zia/web-insights-logs-filters), [Web Insights Logs Columns](/zia/web-insights-logs-columns), and [NSS Feed Output Format Web Logs](/zia/nss-feed-output-format-web-logs).

### Feature Available
#### Enhancements to Microsoft 365 Dashboard
You can now drill down the widgets on the Microsoft 365 dashboard using the following options:
- View Logs: This shows the logs associated with the widget directly on the Insights Logs page. The logs are filtered based on the specific section of the widget that you select.
- Analyze Chart: This shows the trend charts associated with the widget directly on the Web Insights page.
[See image.](#office-365-dashboard)
To learn more, see [About Dashboards](/zia/about-dashboards).
[![Screenshot of the Office 365 Dashboard](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-6.1-Office-365-Dashboard.png)
]

### Feature Available
#### New Cloud Apps
Added new cloud apps to the following cloud app categories for use in the Cloud App Control policy:
- Hosting Providers
- Human Resources
- Instant Messaging
- IT Services
- Productivity & CRM Tools
- Sales & Marketing
- Social Networking
- Streaming Media
- System & Development
- Webmail
To learn more, see [About Cloud App Categories](/zia/cloud-app-categories).

### Feature Available
#### View Logs for IPS Overview Widgets
You can now go to the Insights Logs page directly from any widget in the IPS Overview dashboard. Use the View Logs option to view the logs, filtered based on the specific section of the widget that you select.
[See image.](#view-logs-from-ips-overview)
[]![View Insights Logs for IPS Widgets in ZIA Admin Portal](/sites/default/files/downloads/View-Logs-IPS-Overview.png)
To learn more, see [About Dashboards](/zia/about-dashboards) and [About Insights Logs](/zia/about-insights-logs).

## July 09, 2021
### Feature Available
#### Enable or Disable Admins, Auditors, and Users
You now can enable or disable the following types of accounts using the new Status option:
- Administrators
- Partner Administrators
- Executive Insight App Administrators
- Auditors
- Users
[See image.](#seeimage-status)
You can also control the account Status using Admin & Role Management endpoints within the cloud service API.
To learn more, see [About Administrators](/zia/about-administrators), [Adding Auditors](/zia/adding-auditors), [Adding Users](/zia/adding-users), and [API Reference](/zia/about-api).
[]![The Status field in the Add Administrator window.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Add-Administrator-Window-Status-Field.png)

### Feature Available
#### Enhancement to Locations and Sub-Locations
You can now add descriptions to both existing and new locations and sub-locations. You can also add descriptions using Location Management endpoints within the cloud service API.
To learn more, see [About Locations](/zia/about-locations), [Configuring Sub-Locations](/zia/configuring-sub-locations), and the [API Reference](/zia/about-api).

### Feature Available
#### Zscaler Identity Proxy Support for Slack
Zscaler now supports configuring Identity Proxy for Slack cloud app from the Administration > Identity Proxy Settings page of the ZIA Admin Portal.
[See image.](#add-cloud-app-slack)
To learn more, see [About Identity Proxy Settings](/zia/about-identity-proxy-settings).
[]![Screenshot of Add Cloud Application for Slack](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Add-Cloud-Application-Slack-IdP.png)

## June 25, 2021
### Feature Available
#### Identity Provider Migration Enchancement
You can now migrate seamlessly from one SAML identity provider (IdP) to another. When you add a new IdP, the "What do you want to do?" window appears and asks if you'd like to migrate to a new IdP. You can then select the IdP and update the SAML Portal URL, IdP SAML Certificate, and Vendor.
[See image.](#idp-migration)
To learn more, see [Migrating to a New SAML IdP](/zia/migrating-new-saml-idp).
[]![The What do you want to do? window on the Identity Providers page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-IdP-What-do-you-want-to-do-Window.png?1623972283)

### Feature Available
#### SaaS Security API
The following enhancements are now available for SaaS Security API.
New SaaS Application Support
You can now configure tenants for Slack.
[See image.](#slack-sn-tenant2)
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
Updates to SaaS Security API Policies
You can now configure the SaaS Security API Control policies and scan schedules for collaboration applications.
To learn more, see [Configuring the SaaS Security API Control Policy](/zia/configuring-saas-security-api-policies).
Updates to the SaaS Assets Summary Report
You can now view collaboration application category in the SaaS Assets Summary Report.
To learn more, see [SaaS Assets Summary Report](/zia/saas-assets-summary-report).
Updates to the SaaS Assets Report
You can now view the collaboration application category in the SaaS Assets Report.
To learn more, see [Saas Assets Report](/zia/saas-assets-report) and [SaaS Assets Report: Assets with Incidents](/zia/saas-assets-report-assets-incidents).
Updates to SaaS Security Insights & Insights Logs
You can now view the collaboration application category in SaaS Security Insights and Insights Logs.
To learn more, see [SaaS Security Insights](/zia/saas-security-insights) and [SaaS Security Insights Logs](/zia/saas-security-insights-logs).
New Application Categories for NSS Feeds
There is a new application category in NSS feeds for SaaS Security API: SaaS Security Collaboration. These application categories provide support for Slack (Collaboration).
There is also a new tab for Collaboration in the SaaS Security Log Filters.
To learn more, see [Adding NSS Feeds for SaaS Security Logs](/zia/adding-nss-feeds-saas-security-logs).
New SaaS Security Fields for NSS Feed Outputs
The following web log fields were added to NSS Feeds under Collaboration:
- `%s{internal_recptnames}`
- `%s{external_recptnames}`
- `%s{ointernal_recptnames}`
- `%s{oexternal_recptnames}`
- `%s{sharedchannel_hostname}`
- `%s{osharedchannel_hostname`
- `%s{sender}`
- `%s{osender}`
- `%s{esender}`
- `%s{channel_name}`
- `%s{ochannel_name}`
To learn more, see [NSS Feed Output Format: SaaS Security Logs](/zia/nss-feed-output-format-saas-security-logs).
[]![The Slack and ServiceNow applications on the Add SaaS Application Tenant page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Add-SaaS-Application-Tenant-Slack.png)

## June 18, 2021
### Feature Available
#### Microsoft Defender for Endpoint Partner Integration
Zscaler's integration leverages Microsoft Defender for Endpoint APIs to provide endpoint detection and response (EDR) visibility for Cloud Sandbox-detected malware. Once the integration is configured, the Zscaler service calls the Microsoft Defender for Endpoint API and requests information for endpoints that have been exposed to the malicious file. Microsoft Defender for Endpoint uses the new file signature to detect compromised points throughout your organization's network.
You can view information about the affected endpoints in the Sandbox logs and reports. You can also isolate endpoints, start automated investigation and remediation (AIR), and stop malicious file executions from the ZIA Admin Portal. For further investigation and remediation, you can go to the Microsoft Defender for Endpoint portal. These automated workflows reduce the threat dwell time and remediation time.
[See image.](#ms-defender-endpoint)
To learn more, see [About Partner Integrations](/zia/about-partner-integrations).
[]![The Microsoft Defender for Endpoint tab on the Partner Integrations page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Partner-Integrations-Microsoft-Defender-for-Endpoint.png)

### Feature Available
#### SaaS Security API
The following enhancements are now available for SaaS Security API.
To enable Amazon S3 for your organization, contact your Zscaler Account Team.
New SaaS Application Support
You can now configure tenants for Microsoft Teams and Amazon S3.
[See image.](#seeimage-s3-teams)
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
Updates to SaaS Security API Control Policies & Scan Configuration
You can now configure the SaaS Security API Control policies and scan schedules for public cloud storage applications. Additionally, you can configure policies and scan schedules for Microsoft Teams, a collaboration application.
To learn more, see [Configuring the SaaS Security API Control Policy](/zia/configuring-saas-security-api-policies).
Updates to the SaaS Assets Summary Report
You can now view Microsoft Teams (collaboration application category) and Amazon S3 (public cloud storage application category) in the SaaS Assets Summary Report.
To learn more, see [SaaS Assets Summary Report](/zia/saas-assets-summary-report).
Updates to the SaaS Assets Report
You can now view Microsoft Teams (collaboration application category) and Amazon S3 (public cloud storage application category) in the SaaS Assets Report.
To learn more, see [Saas Assets Report](/zia/saas-assets-report) and [SaaS Assets Report: Assets with Incidents](/zia/saas-assets-report-assets-incidents).
Updates to SaaS Security Insights & Insights Logs
You can now view Microsoft Teams (collaboration application category) and Amazon S3 (public cloud storage application category) in SaaS Security Insights and Insights Logs.
To learn more, see [SaaS Security Insights](/zia/saas-security-insights) and [SaaS Security Insights Logs](/zia/saas-security-insights-logs).
New Application Categories for NSS Feeds
A new Public Cloud Storage application category has been added to NSS feeds for SaaS Security API. Public Cloud Storage provides support for Amazon S3.  There is also support for Microsoft Teams with the SaaS Security Collaboration application category.
To learn more, see [Adding NSS Feeds for SaaS Security Logs](/zia/adding-nss-feeds-saas-security-logs).
New SaaS Security Fields for NSS Feed Outputs
The following web log fields were added to NSS Feeds under Public Cloud Storage:
- `%d{bucketid}`
- `%s{bucketname}`
- `%s{bucketowner}`
- `%s{collabnames}`
- `%s{collabscope}`
- `%s{ebucketname}`
- `%s{ebucketowner}`
- `%s{ecollabname}`
- `%s{efilename}`
- `%s{efilesource}`
- `%s{efullurl}`
- `%d{ehostname}`
- `%s{eowner}`
- `%d{epochlastmodtime}`
- `%s{fileid}`
- `%s{filemd5}`
- `%s{filename}`
- `%d{filesize}`
- `%s{filesource}`
- `%s{filetypecategory}`
- `%s{filetypename}`
- `%s{fullurl}`
- `%s{hostname}`
To learn more, see [NSS Feed Output Format: SaaS Security Logs](/zia/nss-feed-output-format-saas-security-logs).
[]![Microsoft Teams and Amazon S3 SaaS applications in the Choose SaaS Application Provider section.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Choose-SaaS-Application-Provider-msteams-amazons3.png)

## June 11, 2021
### Feature Available
#### New Macro Available for DLP Notification Templates
Zscaler has added a new macro for your DLP Notification Templates. The ${FILENAME} macro specifies the name of the file that triggered the DLP rule.
To learn more, see [Configuring DLP Notification Templates](/zia/configuring-dlp-notification-templates).

### Feature Available
#### SaaS Security Posture Control
The following enhancements are now available for SaaS Security Posture Control.
New SaaS Application Support
You can now configure tenants for Google Workspace.
[See image.](#tenants-google-workspace)
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
Updates to the SaaS Security Posture Control Policy & Report
Google Workspace and GitHub are now available applications for the SaaS Security Posture Control policy and SaaS Security Posture Report.
To learn more, see [Configuring the SaaS Security Posture Policy](/zia/configuring-saas-security-posture-policy) and [SaaS Security Posture Report](/zia/saas-security-posture-report).
[]![Google Workspace application on the Add SaaS Application Tenant page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Add-SaaS-Application-Tenant-Google-Workspace.png?1622759621)

## June 04, 2021
### Feature Available
#### Zscaler Identity Proxy Support for ServiceNow
Zscaler now supports configuring Identity Proxy for ServiceNow cloud app from the Administration > Identity Proxy Settings page of the ZIA Admin Portal.
[See image.](#add-cloud-app-servicenow)
To learn more, see [About Identity Proxy Settings](/zia/about-identity-proxy-settings).
[]![Screenshot of Add Cloud Application for ServiceNow](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Add-Cloud-Application-ServiceNow-IdP.png)

## May 21, 2021
### Feature Available
#### Updates to VMware SD-WAN
There is a new field for the VMware SD-WAN SSO URL in Partner Integrations. After adding a URL, you can follow the VMware SD-WAN link on the Location Management page to the VMware SD-WAN Portal.
[See image.](#VMwareAddPartnerKey)
To learn more, see [Managing SD-WAN Partner Keys](/zia/configuring-sdwan-integration).
[]![Screenshot of the Add Partner Key page for VMware SD-WAN](/sites/default/files/downloads/zscaler-tech-pubs-style-guide/draft-articles/managing-sd-wan-partner-keys-draft/VMware%20SD-WAN%20Partner%20Key_0.png)

## May 07, 2021
### Feature Available
#### Cloud Sandbox Submission API
You can now submit files to Cloud Sandbox for analysis via the new Cloud Sandbox Submission API and POST /zscsb/submit resource.
This API supports the submission of raw and archive files (e.g., ZIP, GZIP), and you can submit up to 100 files per day. By default, files are submitted directly to the sandbox for analysis in order to obtain a verdict. However, you can also force the service to reanalyze the file if a verdict already exists. The API also supports all file types that are currently supported by Cloud Sandbox.
In order to obtain access to the Cloud Sandbox Submission API, contact your Zscaler Account Team.
To learn more, see [Getting Started](/zia/api-getting-started), [API Reference](/zia/about-api), and [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

### Feature Available
#### Deprecating Executive Reports
Executive Reports is now deprecated. Zscaler recommends utilizing the [Executive Insights Report](/zia/executive-insights-report) and [Executive Insights App](/zia/executive-insights-app).
To learn more, see [Executive Insights Report](/zia/executive-insights-report) and [About the Executive Insights App](/zia/executive-insights-app).

### Feature Available
#### Multi-Cluster Load Sharing
The Multi-Cluster Load Sharing feature allows the ingress traffic to enter a given Virtual IP (VIP) and access the end destination from any instance of public service edge clusters participating in the VIP. This allows Zscaler to scale up its data centers (DCs) without migrating your clusters while using the same VIPs.
The subcloud resolution works the same as the PAC file traffic while adding new clusters to the DCs with this feature. If you are utilizing subclouds, your traffic is routed via all the participating networks at the site. However, you must ensure that the appropriate network ranges are placed in the allowlist for this to work.
The range announcement is made 24 hours before the rollout on the [Zscaler Trust Portal](https://trust.zscaler.com/zscaler.net).
To learn more, see [About Multi-Cluster Load Sharing](/zia/about-multi-cluster-load-sharing).

## April 23, 2021
### Feature Available
#### Backup & Restore Enhancements
The following updates were made to the Backup & Restore feature:
- You can now mark a restore point as a Golden Restore Point.
- You can now schedule the automatic creation of restore points in the new Backup Configuration tab.
[See Image.](#backup-configuration)
- This feature was extended to include additional configurations:
- [See the list of configurations.](#additional-configuration)
- You can now view all of the configuration settings along with the policies that are backed up.
[See Image.](#stored-configuration)
To learn more, see [About Backup & Restore](/zia/about-backup-and-restore).
- []Admin Settings
- Administrators
- Administrator Management Settings
- Auditors
- Authentication Settings
- Authentication Bridges
- Authentication Profile
- Identity Providers
- Dedicated Proxy Ports
- Location Management
- Locations
- Location Groups
- Nanolog Streaming Service
- NSS Servers
- NSS Feeds
- Partner Integrations
- Azure Virtual WAN
- Carbon Black
- Crowdstrike
- Microsoft Cloud App Security
- SD-WAN
-
Provisioned IPs
- Tenant Profiles
- VPN Credentials
[]![Screenshot of the Stored Configurations page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-6.1-View%20Stored%20Configuration.png)
[] ![Screenshot of the Backup Configuration page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-6.1-Backup-Configuration.png)

## April 16, 2021
### Feature Available
#### Changes to NSS URL Category Field Values
The following NSS URL Category field, `%s{urlcat}`, values have changed to ensure consistency with the field values from the Web Insights in the ZIA Admin Portal:
Old NSS Name
New NSS Name
Adult Material
Other Adult Material
Adult themes
Adult Themes
Business and Economy
Other Business and Economy
Drugs
Other Drugs
Education
Other Education
Entertainment/Recreation
Other Entertainment/Recreation
Radio and Audio Streaming
Radio
Government and Politics
Other Government and Politics
Illegal or Questionable
Other Illegal or Questionable
Information Technology
Other Information Technology
Image host
Image Host
File host
FileHost
Shareware download
Shareware Download
Web host
Web Host
Web search
Web Search
DoH Service
DoH
Internet Communication
Other Internet Communication
Online chat
Online Chat
Peer to Peer Site
Peer-to-Peer Site
ZScaler Proxy IPs
Zscaler Proxy IPs
Miscellaneous
Other Miscellaneous
Religion
Other Religion
Social and Family Issues
Other Social and Family Issues
Society and Lifestyle
Other Society and Lifestyle
Shopping and Auctions
Other Shopping and Auctions
Security
Other Security
Adv Security
Advanced Security
Botnets
Botnet Callback
Malicious URLs
Malicious Content
Peer to peer
Peer-to-Peer
Suspicious Destinations
Suspicious Destination
PageRisk
Suspicious Content
Suspected Spyware or Adware
Spyware Callback
Crypto Mining
Cryptomining & Blockchain
To learn more, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs).

### Feature Available
#### Cloud NSS Feeds
Cloud NSS allows you to instantly stream logs from ZIA directly into a Cloud based SIEM, without the need to to deploy an NSS VM for Web or Firewall. Cloud NSS Feeds allows you to use cloud-to-cloud log streaming.
You can configure a Cloud NSS Feed that will be automatically be assigned to Cloud NSS. Also, you can use Cloud NSS Feeds to configure SIEM connectivity across cloud-based SIEMs.
[See image](#SIEMConnectivity)
To learn more, see [About Cloud NSS Feeds](https://help.zscaler.com/zia/about-cloud-nss-feeds).
[![Screenshot of the SIEM Connector.](/sites/default/files/downloads/zia/cloud-nss-feeds/SIEM%20Connectivity.png)
]

### Feature Available
#### Cloud Sandbox
The following enhancements are now available for Cloud Sandbox.
Sandbox Activity Report Enhancements
You can now do the following for the Sandbox Activity Report:
- Print the report.
- Export the report as a PDF or JSON file.
- Schedule a weekly email delivery of the report to specific recipients.
[See image.](#sandbox-activity)
To learn more, see [About the Sandbox Activity Report](/zia/about-sandbox-activity-report).
Sandbox Files Found Malicious Report Enhancements
You can now do the following for the Sandbox Files Found Malicious report:
- Print the report.
- Export the report as a PDF or CSV file.
- Schedule a weekly email delivery of the report to specific recipients.
[See image.](#sandbox-files-malicious)
To learn more, see [About the Sandbox Files Found Malicious Report](/zia/about-sandbox-files-found-malicious-report).
New File Types Supported
Sandbox now supports the following file types when adding a Sandbox Policy rule:
- Visual Basic Script (.vbs)
- Windows PowerShell Script (.ps1)
- HTML Application (.hta)
To learn more, see [Configuring the Sandbox Policy](/zia/configuring-sandbox-policy).
[]![The Print, Export, and Schedule icons for the Sandbox Activity Report.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Sandbox-Activity-Report-Print-Export-Schedule-Icons.png)
[]![The Print, Export, and Schedule icons for the Sandbox Files Found Malicious report.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Sandbox-Files-Found-Malicious-Report-Print-Export-Schedule-Icons.png?1615310788)

### Feature Available
#### Data Loss Prevention & Exact Data Match
The following enhancements are now available for Data Loss Prevention (DLP) and Exact Data Match (EDM).
Increased DLP Dictionaries & Engines in Insights Logs
Insights Logs now displays up to 16 DLP dictionaries and 8 DLP engines for a transaction. Prior to this release, Insights Logs displayed up to 4 DLP dictionaries and one DLP engine.
Variable Length Primary Fields for Alphanumeric & Numeric EDM Data Types
For EDM, Zscaler now supports primary fields with up to 5 separate variable lengths for the Alphanumeric and Numeric data types.
To learn more, see [Creating an Exact Data Match Template](/zia/creating-exact-data-match-template).

### Feature Available
#### DNS Protocol Type in Rules, Insights, and Dashboard
You can now choose a protocol type of UDP, TCP, or DNS over HTTPS when creating a DNS Filtering Rule.
Logs can also now be filtered by Protocol Type in DNS Insights. Additionally, the new DNS Protocol Distribution widget in Dashboard > DNS Overview shows what protocols are in use and which rule they are associated with.
[See image.](#Screenshot1)
To learn more, see [Configuring the DNS Control Policy](/zia/configuring-dns-control-policy) and [About Dashboards](/zia/about-dashboards).
[![Screenshot of new DNS Protocol Distribution Widget in DNS Overview](/sites/default/files/downloads/DNS-widget-2.png)
]

### Feature Available
#### Enhanced Cloud Browser Isolation Integration
The integration between ZIA and Cloud Browser Isolation is now enhanced for better user experience and administrative workflow. Users are no longer prompted for authentication when entering an isolation session if they have already been authenticated in ZIA or have Zscaler Client Connector running on their device.
Admins can create a URL filtering policy rule with the new Action option, Isolate. If your organization uses Cloud Browser Isolation, you will see this new option in addition to the existing Actions of Block, Caution, and Allow. When the Isolate action is selected, the policy framework allows you to select one of the isolation profiles created for your organization in the Cloud Browser Isolation Portal. Any traffic matching the defined rule will be isolated in accordance with the selected isolation profile.
[See image.](#url-rule)
In order to use this action, you must first create isolation profiles for your organization in the Zscaler Cloud Browser Isolation Portal.
The ZIA Web Logs have been enhanced to represent the isolated traffic better without losing the context of the user's original location or IP address.
To learn more, see [Configuring ZIA for Cloud Browser Isolation](/zia/configuring-browser-isolation).
[![New Isolate Action shown in ZIA URL Filtering Policy Rule Criteria](/sites/default/files/downloads/internal%20documentation/ZIA_URL-filtering-policy_action-isolate-dropdown-cropped-small.png)
]

### Feature Available
#### Enhancement to DNS Control Policy
Added the Protocol field in the DNS Application tab (Policy > DNS Control > Add DNS Filtering Rule). You can now control the following protocol types with the DNS Control policy rules:
- DNS over HTTPS
- TCP
- UDP
[See image.](#protocol)
To learn more, see [Configuring the DNS Control Policy](/zia/configuring-dns-control-policy).
[]![Screenshot of the Add DNS Filtering Rule page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-6.1-DNS%20Control-DNS%20Application.png)

### Feature Available
#### Enhancement to Locations and Sub-Locations
You can now select any of the following location types on the Locations or Sub-Locations page to represent the primary type of traffic for a location or sub-location:
- Corporate user traffic
- Guest Wi-Fi traffic
- IoT traffic
- Server traffic
To learn more, see [About Locations](/zia/about-locations) and [Configuring Locations](/zia/configuring-locations).

### Feature Available
#### Enhancement to URL Categories
Added the following new predefined URL categories:
- Dynamic DNS Host: It includes DNS server URLs that support Dynamic DNS resolution.
- Military: It includes sites related to the armed forces.
To learn more, see [About URL Categories](/zia/about-url-categories).

### Feature Available
#### Indexed Document Match
Indexed Document Match (IDM) allows you to fingerprint your organization’s critical documents containing sensitive data and create a document repository that the Zscaler service can use to identify completely or partially matching documents when evaluating outbound traffic with the Data Loss Prevention (DLP) policy.
To create a document repository for IDM, you must use the Index Tool to upload documents and create an IDM template. This template can be applied to a custom DLP dictionary or engine.
To learn more, see [About Indexed Document Match](/zia/about-indexed-document-match).

### Feature Available
#### Interactive Reports: Page Redesign
The Interactive Reports page has been redesigned to improve user experience. The redesign includes a new layout, a Search bar to locate your reports faster, and more.
[See image.](#interactive-reports)
To learn more, see [About Interactive Reports](/zia/about-interactive-reports).
[]![The Interactive Reports page with a list of standard reports and the page's tabs and Search bar](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-6.1-Interactive-Reports.png)

### Feature Available
#### New Events for System Alerts
Traffic Increase and Traffic decrease are two new events that can trigger System Alerts.
To learn more, see [About Alerts](/zia/about-alerts).

### Feature Available
#### PAC File Verification Status
You can now view the verification status of the Zscaler-hosted PAC files from the Administration > Hosted PAC Files page.
The verification status can be:
- Verified: Indicates that the PAC file is verified on the ZIA Admin Portal.
- Error-Accepted: Indicates that the PAC file has some errors and the admin has accepted and saved it with errors at the time of verification on the ZIA Admin Portal.
- Unverified (---): Indicates that the PAC file is not yet verified.
[See Image.](#verification-status)
After the Zscaler service upgrade, all the pre-existing custom PAC files will be in Unverified status until you verify it because Zscaler does not have the record of previous verification status. You must edit the contents of the file to enable the Verification button for it.
To learn more, see [About Hosted PAC Files](/zia/about-hosted-pac-files).
[] ![Screenshot of Hosted PAC Files Page with Verification Status](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/zia-hosted-pac-file-verification-status.png)

### Feature Available
#### Predefined NAT Rule to Control DNS Traffic
Zscaler added a predefined NAT rule, Zscaler Trusted DNS Resolver, that allows you to either forward your standard DNS traffic to the Zscaler Trusted DNS resolver or redirect the traffic to an external DNS resolver.
[See image.](#nat-rule)
![NAT rule to control iterative DNS queries](/downloads/zscaler-tech-pubs-style-guide/draft-articles/pre-defined-nat-rule-control-dns-queries/NAT%20rule.jpeg)
[]
To learn more, see [About NAT Control](/zia/about-nat-control) and [About DNS Control](/zia/about-dns-control).

### Feature Available
#### Self Provisioning of GRE Tunnels and Static IP Addresses
You can now self provision your static IP addresses or GRE tunnels to connect to the Zscaler service via the ZIA Admin Portal or the cloud service API.
- To self-provision your GRE tunnels, you can use the Add GRE Tunnel Configuration wizard from the Administration > Static IPs & GRE Tunnels > GRE Tunnels page.
[See Image.](#gre-tunnel)
- To self-provision your static IP addresses, you can use the Add Static IP Configuration wizard from the Administration > Static IPs & GRE Tunnels > Static IP page.
[See Image.](#static-ip)
To learn more, see [About GRE Tunnels](/zia/about-gre-tunnels) and [About Static IP](/zia/about-static-ip).
[]![Screenshot of Add Static IP Configuration Wizard](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Add-Static-IP.png)
[]![Screenshot of Add GRE Tunnel Configuration Wizard](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Add-GRE-Tunnel.png)

### Feature Available
#### Shadow IT Report
The Shadow IT Report shows the number of sanctioned and unsanctioned applications being used and their number of users. It also shows the application categories, the risk index, and the certifications for each of these applications.
[See image.](#report-img)
To learn more, see [Shadow IT Report](/zia/shadow-it-report).
[]![The Shadow IT Report and all its different sections and filters](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-6.1-Shadow-IT-Report.png)

### Feature Available
#### SSL Inspection Policy Engine Redesign
[Watch a feature video about the Redesigned SSL Inspection Policy](https://fast.wistia.net/embed/iframe/lulzbdyug1)
As part of the ongoing effort to simplify the adoption and ongoing operation of the ZIA service, Zscaler has redesigned the SSL inspection policy engine. The new design consolidates all the various existing SSL inspection settings into a centralized rule-based engine with a multitude of source and destination based criteria, actions, and sub-actions. Together, they enable great flexibility in implementing your organization’s SSL inspection policies based on your specific needs, such as privacy requirements, user groups, OS platform types, and more.
The following sections cover the new and deprecated SSL inspection settings and the automated migration rules implemented in your ZIA Admin Portal for backwards compatibility with the deprecated SSL inspection settings:
- [What's New](#whats-new)
- [Deprecated SSL Settings](#deprecated)
- [Backwards Compatibility](#backward-compatibility)
To learn more, see [About SSL Inspection Policy](/zia/about-ssl-inspection-policy).
[]You can now define granular SSL policies using the ZIA Admin Portal to perform SSL scanning on a multitude of criteria pertaining to the source and destination of the SSL traffic. Using this, you can tailor your policies better to simplify the deployment and ongoing operations of SSL inspection and address the compliance and operational environment requirements.
- All the previous SSL Inspection controls have been replaced with a flexible rule-based engine.
- The policy engine supports 12 criteria and evaluates the rules in top-down order and stops at the first match.
- Each policy action supports a variety of special settings for ensuring validity and revocation status of certificates, enforcement of minimum TLS version, and more.
- All criteria in the rules are organized into multiple OR groups nested inside AND groups. The logical operators between the criteria are visible in the Admin Portal. If you do not select a value for a criterion which is indicated as `---`, then the rule ignores the criterion for the policy evaluation. For example, if you do not select any value for the *Users* criterion, then the rule matches for all the users. If you select a specific user value, then the rule matches only for traffic from the specified user.
[See Image.](#add-ssl-inspection-policy)
- A new weblog field, *SSL Policy Reason* is now available under Analytics > Web Insights > Logs and in NSS. This field captures the following SSL inspection policy actions:
- Blocked
- Inspected
- N/A
- Not inspected because of O365 bypass
- Not inspected because of SSL policy
- Not inspected because of UCaaS bypass
- Not inspected because of Zscaler best practices
- Not inspected because SSL inspection is off for gateway
- The *Policy Action* weblog field now includes the following values:
- Access denied due to low TLS version
- Not allowed to establish SSL connection due to policy
- Access denied due to bad server certificate
[]![Screenshot of Add SSL Inspection Rule](/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-6.1-Add-SSL-Inspection-Policy.png)
[]All the previous SSL inspection settings have been removed:
- The following settings were removed from the Administration > Location Management page of the ZIA Admin Portal:
- *Enable SSL Inspection*: It was the global SSL inspection settings to enable SSL inspection on individual locations or sub-locations. You can now select locations, sub-locations or location-groups as criteria within an SSL inspection rule.
[See Image.](#global-enable-ssl)
- *Enforce Zscaler Client Connector SSL Setting*: It was used to override the location's SSL policy settings with the Zscaler Client Connector's setting if the Zscaler Client Connector traffic was forwarded from a known location.
[See Image.](#enforce-client-conn)
If you need to configure these settings, you must now use the appropriate criteria in the new SSL Inspection Policy page.
- The following settings were removed from the Policy > SSL Inspection page of the ZIA Admin Portal:
- *If SSL Inspection Is Disabled, Block HTTPS to These Sites:* This configuration blocked the specified URL categories or hosts when SSL inspection was disabled on the location or Zscaler Client Connector. This setting was used when Zscaler service had to bypass URL Filtering or Cloud App Control policies due to lack of user context at the time of SSL connection. This was required only when organizations did not use the modern authentication settings, such as Zscaler Client Connector, Surrogate IP, or Policy for Unauthenticated Traffic. You can now configure block rules assigned to these URL Categories and Destination group criteria.
- *Show Notifications for Blocked Traffic*: This was a global setting on the tenant which determined whether to display End User Notification for the traffic that were blocked when not subject to SSL inspection. You can now configure the show notification settings within a Do Not Inspect or Block SSL inspection rule.
[See Image.](#block-https-sites)
- The following settings under the *Policy For SSL Inspection* section: These were global settings on the tenant to configure which destination traffic should be inspected or exempted from SSL inspection and other policies. You can now configure granular rules to inspect or exempt inspection for the traffic on the specified destination and many other criteria.
- *Inspect Sessions for These URL Categories*
- *Exempt These URL Categories from Inspection & Other Policies*
- *Exempt These Hosts from Inspection & Other Policies*
- *Exempt These Applications from Inspection & Other Policies*
[See Image.](#ssl-inspection-exemption-list)
- *Block Undecryptable Traffic*: This was a global setting on the tenant to block undecryptable traffic, such as non-standard cipher suites. You can now configure how to handle this type of traffic within an SSL inspection rule.
[See Image.](#block-undecrypt-traffic)
- *Untrusted Server Certificates* and *Block Site With Revoked Server Certificate*: This was a global setting on the tenant to determine how to handle untrusted or revoked certificates for traffic subject to SSL inspection. You can now configure untrusted or revoked certificate settings for both inspected and uninspected traffic within the SSL inspection rules.
[See Image.](#untrusted-revoked-server-cert)
- *Enable SSL Inspection for Remote Users with Kerberos*: This was a global setting on the tenant to enable or disable SSL inspection for remote user traffic using Kerberos authentication. You can now configure whether to inspect remote user traffic using Kerberos authentication within an SSL inspection rule.
[See Image.](#remote-user-kerberos)
- All the platform settings under the *Policy for Zscaler Client Connector* section: These were the global settings on the tenant to enable or disable SSL inspection for specific Zscaler Client Connector platforms. You can now configure the platforms within an SSL inspection rule.
[See Image.](#z-client-conn-platform-settings)
- The *SSL Inspection* setting under Administration > Proxies & Gateways > Gateway for Proxies > Add Gateway for Proxies was deprecated. This setting determined whether to disable SSL inspection for traffic forwarded to a third-party proxy service by overriding the SSL inspection settings on the location. You can now disable SSL inspection for traffic forwarded to a third-party proxy service using the Forwarding Gateway criteria within an SSL inspection rule.
[See Image.](#add-proxy-gateway)
- The *Override Zscaler Global SSL Exemptions List* setting under Administration > Advanced Settings was deprecated. This was a global setting on the tenant that determined whether to disable the Zscaler recommended SSL exemption list. You can now choose to disable the auto-generated Zscaler Recommended Exemptions rule from the Policy > SSL Inspection page of the ZIA Admin Portal.
[See Image.](#override-global-exemption)
- The following SSL inspection settings related resources were removed from the cloud service API:
- The following endpoints are no longer supported. If you need to manage SSL bypass lists via API, you must use the destination group or a custom URL category:
- GET /sslSettings/exemptedUrls
- POST /sslSettings/exemptedUrls
- The following Location Management parameters no longer have an effect on SSL policy. They remain supported in the API payload in order to maintain backwards compatibility with existing scripts, but will be removed in future:
- sslScanEnabled
- zappSSLScanEnabled
[]![Screenshot of Deprecated Override Zscaler Global SSL Exemptions List](/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Override-Global-SSL-Adv-Setting-Deprecate.png)
[]![Screenshot of Deprecated Enable SSL Inspection for Remote Users with Kerberos](/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-SSL-Inspection-Remote-Users-Kerberos-Deprecate.png)
[]![Screenshot of Block Undecryptable Traffic Deprecated](/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Block-Undecryptable-Traffic-Deprecated.png)
[]![Screenshot of Untrusted Server Certificates and Block Site With Revoked Server Certificate Deprecated](/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Untrusted-Revoked-Server-Cert-Deprecate.png)
[]![Screenshot of Deprecated SSL Inspection Inclusion Exclusion List](/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-SSL-Policy_Inspection_Exemption-Deprecated.png)
[]![Screenshot of Deprecated Global Enable SSL Inspection](/downloads/zia/release-notes/release-upgrade-summary-2021/zia-global-enable-ssl-inspection-deprecated.png)
[]![Screenshot of Deprecated Block HTTPS to These Sites Setting](/downloads/zia/release-notes/release-upgrade-summary-2021/zia-block-https-section-deprecated.png)
[]![Screenshot of Policy for Zscaler Client Connector Settings - Deprecated](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Policy-Zscaler-Client-Connector-Deprecated.png)
[]![Screenshot of Add Gateway for Proxy - SSL Inspection Setting Deprecated](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Gateway-Proxy-SSL-Inspection-Deprecated.png)
[]![Screenshot of Deprecated Enforce Zscaler Client Connector Settings](/downloads/zia/release-notes/release-upgrade-summary-2021/zia-enforce-zcc-setting-deprecated.png)
[]To ensure that the new rule-based policies are 100% backwards compatible with your previous policy settings, Zscaler automatically generates a set of rules, manual location groups, and destination IP and FQDN groups based on your configuration to preserve the intended behaviour. The number of rules generated ranges between 4 and 17 based on your previous configurations that were in use.
You can now assign the destination IP addresses and FQDN to the SSL inspection policies as well. You could assign these only to the cloud firewall policies in the earlier releases.
Ensure that you review the following sections thoroughly to understand the changes:
- [Rule Order](#rule-order)
- [Auto-generated Entities](#entities)
- [Action Settings](#action-settings)
Migration Scenarios and Rules
This section covers the list of migration rules that are auto-generated for various SSL inspection configuration scenarios that existed before the ZIA service upgrade.
Following are the descriptions of the terms used in the rule tables provided in this section:
- CltCon: Zscaler Client Connector
- O365-TR: Microsoft 365 Tenant Restriction
- RWKRB: SSL inspection for Remote users with Kerberos authentication
- Blocked Categories: URL categories that were configured in *If SSL Inspection Is Disabled, Block HTTPS to These Sites*
- Bypassed URL Categories: URL categories that that were configured in *Exempt These URL Categories from Inspection & Other Policies*
- Inclusion List Categories: URL categories that that were configured in *Inspect Sessions for These URL Categories*
- Bypassed Applications: Cloud Applications that were configured in *Exempt These Applications from Inspection & Other Policies*
**Migration Scenario 1: Enforce Zscaler Client Connector Disabled for All Locations**
Enforce Zscaler Client Connector was disabled for all locations.
- [Rule 1: Zscaler Recommended Exemptions](#m1-z-rec-exm)
- [Rule 2: O365-TR Locations](#m1-o365-tr-loc)
- [Rule 3: O365-TR Remote Users](#m1-o365-tr-remote-users)
- [Rule 4: Microsoft 365 One Click](#m1-o365-one-click)
- [Rule 5: UCaaS One Click](#m1-ucaas-one-click)
- [Rule 6: Block No SSL Locations](#m1r6)
- [Rule 7: Block Remote Users](#m1r7)
- [Rule 8: Organization SSL Bypass](#m1r8)
- [Rule 9: Inspect Locations](#m1r9)
- [Rule 10: Inspect Remote Users](#m1r10)
- [Rule 11: Default SSL Inspection Rule](#m1-default-ssl-rule)
**Migration Scenario 2: Enforce Zscaler Client Connector Enabled only for SSL Inspection-Disabled Locations**
Location SSL inspecton setting is flipped from disabled to enabled for some Zscaler Client Connector platforms.
- [Rule 1: Zscaler Recommended Exemptions](#m2-z-rec-exm)
- [Rule 2: O365-TR CltCon on No-SSL Locs](#m2-o365-tr-CltCon-No-SSL-Locs)
- [Rule 3: O365-TR Locations](#m2-o365-tr-loc)
- [Rule 4: O365-TR Remote Users](#m2-o365-tr-remote-users)
- [Rule 5: Microsoft 365 One Click](#m2-o365-one-click)
- [Rule 6: UCaaS One Click](#m2-ucaas-one-click)
- [Rule 7: Blk CltCon on No-SSL Locs](#m2r7)
- [Rule 8: Blk NoSSL CltCon on NoSSL Locs](#m2r8)
- [Rule 9: Blk Non-CltCon on No-SSL Locs](#m2r9)
- [Rule 10: Blk Remote Users](#m2r10)
- [Rule 11: SSL Bypass](#m2r11)
- [Rule 12: Inspect CltCon on No-SSL Locs](#m2r12)
- [Rule 13: Inspect Locs](#m2r13)
- [Rule 14: Inspect Remote Users](#m2r14)
- [Rule 15: Default SSL Inspection Rule](#m2-default-ssl-rule)
**Migration Scenario 3: Enforce Zscaler Client Connector Enabled only for SSL Inspection-Enabled Locations**
Location SSL inspection setting is flipped from enabled to disabled for some Zscaler Client Connector platforms.
- [Rule 1: Zscaler Recommended Exemptions](#m3-z-rec-exm)
- [Rule 2: O365-TR All CltCon on SSL Locs](#m3-o365-tr-all-CltCon-SSL-Locs)
- [Rule 3: O365-TR CltCon on SSL Locs](#m3-o365-tr-CltCon-SSL-Locs)
- [Rule 4: O365-TR Non-CltCon on Locs](#m3-o365-tr-non-CltCon-Locs)
- [Rule 5: O365-TR Remote Users](#m3-o365-tr-remote-users)
- [Rule 6: Microsoft 365 One Click](#m3-o365-one-click)
- [Rule 7: UCaaS One Click](#m3-ucaas-one-click)
- [Rule 8: Block CltCon on No-SSL Locs](#m3r8)
- [Rule 9: Block No-SSL CltCon on Locs](#m3r9)
- [Rule 10: Block No-SSL Locs](#m3r10)
- [Rule 11: Block Remote Users](#m3r11)
- [Rule 12: SSL Bypass](#m3r12)
- [Rule 13: Inspect All CltCon on SSL Locs](#m3r13)
- [Rule 14: Inspect CltCon on SSL Locs](#m3r14)
- [Rule 15: Inspect Non-CltCon on Locs](#m3r15)
- [Rule 16: Inspect Remote Users](#m3r16)
- [Rule 17: Default SSL Inspection Rule](#m3-default-ssl-rule)
**Migration Scenario 4: Enforce Zscaler Client Connector Enabled for All Locations**
Enforce Zscaler Client Connector was enabled for locations with SSL disabled and for locations with SSL enabled. Location SSL is flipped from disabled to enabled or from enabled to disabled for some Zscaler Client Connector platforms:
- [Rule 1: Zscaler Recommended Exemptions](#m4-z-rec-exm)
- [Rule 2: O365-TR All CltCon on SSL Locs](#m4-o365-tr-all-CltCon-SSL-Locs)
- [Rule 3: O365-TR CltCon on Locs](#m4-o365-tr-CltCon-Locs)
- [Rule 4: O365-TR Non-CltCon on Locs](#m4-o365-tr-non-CltCon-Locs)
- [Rule 5: O365-TR Remote Users](#m4-o365-tr-remote-users)
- [Rule 6: Microsoft 365 One Click](#m4-o365-one-click)
- [Rule 7: UCaaS One Click](#m4-ucaas-one-click)
- [Rule 8: Block CltCon on No-SSL Locs](#m4r8)
- [Rule 9: Block No-SSL CltCon on Locs](#m4r9)
- [Rule 10: Block No-SSL Locs](#m4r10)
- [Rule 11: Block Remote Users](#m4r11)
- [Rule 12: SSL Bypass](#m4r12)
- [Rule 13: Inspect All CltCon on SSL Locs](#m4r13)
- [Rule 14: Inspect CltCon on Locs](#m4r14)
- [Rule 15: Inspect Non-CltCon on Locs](#m4r15)
- [Rule 16: Inspect Remote Users](#m4r16)
- [Rule 17: Default SSL Inspection Rule](#m4-default-ssl-rule)
**Migration Scenario 5: Third-Party Proxy Chaining Rule**
This rule will be created only for organizations with a Forwarding Gateway that was configured to override the location SSL inspection setting. It will be added immediately after the SSL bypass rules in the scenarios above.
**Rule Name**: **Upstream Proxy Bypass** - Bypass traffic forwarded to a third-party proxy service.
Source CriteriaDestination CriteriaAction
Forwarding Gateways:
All with *Disable SSL Inspection and Override Location*
AnyDo Not Inspect & Evaluate
[]Predefined rule to automatically exempt known destinations that cannot be SSL inspected. This rule is disabled if the *Override Zscaler Global SSL Exemptions* setting was enabled in your previous configuration.
Source CriteriaDestination CriteriaActionAny
URL Category:
Recommended SSL Exemptions
Do Not Inspect & Bypass
[]Predefined rule to automatically exempt known destinations that cannot be SSL inspected. This rule is disabled if the *Override Zscaler Global SSL Exemptions* setting was enabled in your previous configuration.
Source CriteriaDestination CriteriaActionAny
URL Category:
Recommended SSL Exemptions
Do Not Inspect & Bypass
[]Predefined rule to automatically exempt known destinations that cannot be SSL inspected. This rule is disabled if the *Override Zscaler Global SSL Exemptions* setting was enabled in your previous configuration.
Source CriteriaDestination CriteriaActionAny
URL Category:
Recommended SSL Exemptions
Do Not Inspect & Bypass
[]Predefined rule to automatically exempt known destinations that cannot be SSL inspected. This rule is disabled if the *Override Zscaler Global SSL Exemptions* setting was enabled in your previous configuration.
Source CriteriaDestination CriteriaActionAny
URL Category:
Recommended SSL Exemptions
Do Not Inspect & Bypass
[]Mandatory rule to enable Microsoft 365 Tenancy Restrictions for location traffic. This rule is created only if an Microsoft 365 tenant profile existed in your previous configuration.
Source CriteriaDestination CriteriaAction
Location Group:
Locations_SSL
Cloud Application:
Microsoft Login Services
Inspect
[]Mandatory rule to enable Microsoft 365 Tenancy Restrictions for location traffic. This rule is created only if an Microsoft 365 tenant profile existed in your previous configuration.
Source CriteriaDestination CriteriaAction
Location Group:
Locations_SSL
Cloud Application:
Microsoft Login Services
Inspect
[]Mandatory rule to enable Microsoft 365 Tenancy Restrictions for remote user traffic. This rule is created only if a Microsoft 365 tenant profile existed in your previous configuration.
Source CriteriaDestination CriteriaAction
Location Group:
Road Warrior
Zscaler Client Connector:
Platforms with SSL enabled or RWKRB enabled
Cloud Application:
Microsoft Login Services
Inspect
[]Mandatory rule to enable Microsoft 365 Tenancy Restrictions for remote user traffic. This rule is created only if an Microsoft 365 tenant profile existed in your previous configuration.
Source CriteriaDestination CriteriaAction
Location Group:
Road Warrior
Zscaler Client Connector:
Platforms with SSL enabled or RWKRB enabled
Cloud Application:
Microsoft Login Services
Inspect
[]Mandatory rule to enable Microsoft 365 Tenancy Restrictions for remote user traffic. This rule is created only if an Microsoft 365 tenant profile existed in your previous configuration.
Source CriteriaDestination CriteriaAction
Location Group:
Road Warrior
Zscaler Client Connector:
Platforms with SSL enabled or RWKRB enabled
Cloud Application:
Microsoft Login Services
Inspect
[]Mandatory rule to enable Microsoft 365 Tenancy Restrictions for remote user traffic. This rule is created only if an Microsoft 365 tenant profile existed in your previous configuration.
Source CriteriaDestination CriteriaAction
Location Group:
Road Warrior
Zscaler Client Connector:
Platforms with SSL enabled or RWKRB enabled
Cloud Application:
Microsoft Login Services
Inspect
[]Mandatory rule to enable Microsoft 365 Tenancy Restrictions for traffic from SSL inspection-enabled Zscaler Client Connector platforms on SSL inspection-disabled locations. This rule is created only if an Microsoft 365 tenant profile existed in your previous configuration.
Source CriteriaDestination CriteriaAction
Location Group:
Locations_NoSSL_CltCon_NoEnforce
Zscaler Client Connector:
Platforms with SSL enabled
Cloud Application:
Microsoft Login Services
Inspect
[]Mandatory rule to enable Microsoft 365 Tenancy Restrictions for traffic from any Zscaler Client Connector platform on SSL inspection-enabled locations. This rule is created only if an Microsoft 365 tenant profile existed in your previous configuration.
Source CriteriaDestination CriteriaAction
Location Group:
Locations_SSL_CltCon_NoEnforce
Zscaler Client Connector:
Windows, MacOS, Android, iOS
Cloud Application:
Microsoft Login Services
Inspect
[]Mandatory rule to enable Microsoft 365 Tenancy Restrictions for traffic from SSL inspection-enabled Zscaler Client Connector platforms on SSL-inspection enabled locations. This rule is created only if an Microsoft 365 tenant profile existed in your previous configuration.
Source CriteriaDestination CriteriaAction
Location Group:
Locations_SSL_CltCon_Enforce
Zscaler Client Connector:
Only platforms with SSL enabled
Cloud Application:
Microsoft Login Services
Inspect
[]Mandatory rule to enable Microsoft 365 Tenancy Restrictions for non-Zscaler Client Connector traffic from SSL inspection-enabled locations. This rule is created only if an Microsoft 365 tenant profile existed in your previous configuration.
Source CriteriaDestination CriteriaAction
Location Group:
Locations_SSL
Zscaler Client Connector:
No Zscaler Client Connector
Cloud Application:
Microsoft Login Services
Inspect
[]Mandatory rule to enable Microsoft 365 Tenancy Restrictions for traffic from any Zscaler Client Connector platform on SSL inspection-enabled locations. This rule is created only if an Microsoft 365 tenant profile existed in your previous configuration.
Source CriteriaDestination CriteriaAction
Location Group:
Locations_SSL_CltCon_NoEnforce
Zscaler Client Connector:
Windows, MacOS, Android, iOS
Cloud Application:
Microsoft Login Services
Inspect
[]Mandatory rule to enable Microsoft 365 Tenancy Restrictions for traffic from SSL inspection-enabled Zscaler Client Connector platforms on locations. This rule is created only if an Microsoft 365 tenant profile existed in your previous configuration.
Source CriteriaDestination CriteriaAction
Location Group:
Locations_CltCon_Enforce
Zscaler Client Connector:
Only platforms with SSL enabled
Cloud Application:
Microsoft Login Services
Inspect
[]Mandatory rule to enable Microsoft 365 Tenancy Restrictions for non-Zscaler Client Connector traffic from SSL inspection-enabled locations. This rule is created only if an Microsoft 365 tenant profile existed in your previous configuration.
Source CriteriaDestination CriteriaAction
Location Group:
Locations_SSL
Zscaler Client Connector:
No Zscaler Client Connector
Cloud Application:
Microsoft Login Services
Inspect
[]Predefined rule, controlled by the Microsoft-Recommended and Legacy Microsoft 365 One Click Setting.
Source CriteriaDestination CriteriaActionAny
Cloud Applications:
All O365 applications [Applicable, only if Microsoft-recommended One Click is enabled]
URL Category:
O365 Internal Category [Applicable, if either Microsoft-recommended or legacy One Click is enabled]
Do Not Inspect & Bypass
[]Predefined rule, controlled by the Microsoft-Recommended and Legacy Microsoft 365 One Click Setting.
Source CriteriaDestination CriteriaActionAny
Cloud Applications:
All O365 applications [Applicable, only if Microsoft-recommended One Click is enabled]
URL Category:
O365 Internal Category [Applicable, if either Microsoft-recommended or legacy One Click is enabled]
Do Not Inspect & Bypass
[]Predefined rule, controlled by the Microsoft-Recommended and Legacy Microsoft 365 One Click Setting.
Source CriteriaDestination CriteriaActionAny
Cloud Applications:
All O365 applications [Applicable, only if Microsoft-recommended One Click is enabled]
URL Category:
O365 Internal Category [Applicable, if either Microsoft-recommended or legacy One Click is enabled]
Do Not Inspect & Bypass
[]Predefined rule, controlled by the Microsoft-Recommended and Legacy Microsoft 365 One Click Setting.
Source CriteriaDestination CriteriaActionAny
Cloud Applications:
All O365 applications [Applicable, only if Microsoft-recommended One Click is enabled]
URL Category:
O365 Internal Category [Applicable, if either Microsoft-recommended or legacy One Click is enabled]
Do Not Inspect & Bypass
[]Predefined rule, controlled by the UCaaS One Click Configuration.
Source CriteriaDestination CriteriaActionAny
Application Service:
Zoom, LogMeIn, RingCentral
Do Not Inspect & Bypass
[]Predefined rule, controlled by the UCaaS One Click Configuration.
Source CriteriaDestination CriteriaActionAny
Application Service:
Zoom, LogMeIn, RingCentral
Do Not Inspect & Bypass
[]Predefined rule, controlled by the UCaaS One Click Configuration.
Source CriteriaDestination CriteriaActionAny
Application Service:
Zoom, LogMeIn, RingCentral
Do Not Inspect & Bypass
[]Predefined rule, controlled by the UCaaS One Click Configuration.
Source CriteriaDestination CriteriaActionAny
Application Service:
Zoom, LogMeIn, RingCentral
Do Not Inspect & Bypass
[]The default SSL inspection rule takes the last rule order.
Source CriteriaDestination CriteriaAction------Do Not Inspect & Evaluate
[]The default SSL inspection rule takes the last rule order.
Source CriteriaDestination CriteriaAction------Do Not Inspect & Evaluate
[]The default SSL inspection rule takes the last rule order.
Source CriteriaDestination CriteriaAction------Do Not Inspect & Evaluate
[]The default SSL inspection rule takes the last rule order.
Source CriteriaDestination CriteriaAction------Do Not Inspect & Evaluate
[]Block traffic from SSL inspection-disabled locations.
Source CriteriaDestination CriteriaAction
Location Group:
Locations_NoSSL
URL Categories:
Blocked Categories
Destination Group:
NoSSL_Blocked_IPs, NoSSL_Blocked_Domains
Block
[]Block remote user traffic:
- If it is from SSL inspection-disabled Zscaler Client Connector platforms.
or
- If it is with Kerberos authentication.
Source CriteriaDestination CriteriaAction
Locations:
Road Warrior
Zscaler Client Connector:
Platforms with SSL disabled
URL Categories:
Blocked Categories
Destination Group:
NoSSL_Blocked_IPs, NoSSL_Blocked_Domains
Block
[]Whitelist from SSL inspection and other policies.
Source CriteriaDestination CriteriaActionAny
URL Categories:
Bypassed URL Categories
Destination Group:
NoSSL_NoOtherPolicies_IPs, NoSSL_NoOtherPolicies_Domains
Cloud Applications:
Bypassed Applications
Do Not Inspect & Bypass
[]Inspect traffic from SSL inspection-enabled locations.
Source CriteriaDestination CriteriaAction
Location Group:
Locations_SSL
URL Categories:
Inclusion List Categories
Inspect
[]Inspect remote user traffic:
- If it is from SSL inspection-enabled Zscaler Client Connector platforms
or
- If it is with Kerberos authentication.
Source CriteriaDestination CriteriaAction
Locations:
Road Warrior
Zscaler Client Connector:
Platforms with SSL enabled or RWKRB enabled
URL Categories:
Inclusion List Categories
Inspect
[]Block traffic from any Zscaler Client Connector platform on SSL inspection-disabled locations.
Source CriteriaDestination CriteriaAction
Location group:
<!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}-->
Locations_NoSSL_CltCon_NoEnforce
Zscaler Client Connector:
Windows, MacOS, Android, iOS
URL Categories:
Blocked Categories
Destination Group:
NoSSL_Blocked_IPs, NoSSL_Blocked_Domains
Block
[]Block traffic from SSL inspection-disabled Zscaler Client Connector platforms on SSL inspection-disabled locations.
Source CriteriaDestination CriteriaAction
Location Group:
<!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}-->
Locations_NoSSL_CltCon_Enforce
Zscaler Client Connector:
Platforms with SSL disabled
URL Categories:
Blocked Categories
Destination Group:
NoSSL_Blocked_IPs, NoSSL_Blocked_Domains
Block
[]Block non-Zscaler Client Connector traffic on SSL inspection-disabled locations.
Source CriteriaDestination CriteriaAction
Location Group:
Locations_NoSSL
Zscaler Client Connector:
No Zscaler Client Connector
URL Categories:
Blocked Categories
Destination Group:
NoSSL_Blocked_IPs, NoSSL_Blocked_Domains
Block
[]Block remote user traffic:
- If it is from SSL inspection-disabled Zscaler Client Connector platforms.
or
- If it is with Kerberos authentication.
Source CriteriaDestination CriteriaAction
Locations:
Road Warrior
Zscaler Client Connector:
Platforms with SSL disabled
URL Categories:
Blocked Categories
Destination Group:
NoSSL_Blocked_IPs, NoSSL_Blocked_Domains
Block
[]Whitelist from SSL inspection and other policies.
Source CriteriaDestination CriteriaActionAny
URL Categories:
Bypassed URL Categories
Destination Group:
NoSSL_NoOtherPolicies_IPs, NoSSL_NoOtherPolicies_Domains
Cloud Applications:
Bypassed Applications
Do Not Inspect & Bypass
[]Inspect traffic from SSL inspection-enabled Zscaler Client Connector platforms on SSL inspection-disabled locations.
Source CriteriaDestination CriteriaAction
Location Group:
<!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}-->
Locations_NoSSL_CltCon_Enforce
Zscaler Client Connector
Platforms with SSL enabled
URL Categories:
Inclusion List Categories
Inspect
[]Inspect traffic from SSL inspection-enabled locations.
Source CriteriaDestination CriteriaAction
Location Group:
Locations_SSL
URL Categories:
Inclusion List Categories
Inspect
[]Inspect remote user traffic, if:
- It is from SSL inspection-enabled Zscaler Client Connector platforms.
or
- It is with Kerberos authentication.
Source CriteriaDestination CriteriaAction
Locations:
Road Warrior
Zscaler Client Connector:
Platforms with SSL enabled or RWKRB enabled
URL Categories:
Inclusion List Categories
Inspect
[]Block traffic from any Zscaler Client Connector platforms on SSL inspection-disabled locations.
Source CriteriaDestination CriteriaAction
Location group:
<!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}-->
Locations_NoSSL_CltCon_NoEnforce
Zscaler Client Connector:
Windows, MacOS, Android, iOS
URL Categories:
Blocked Categories
Destination Group:
NoSSL_Blocked_IPs, NoSSL_Blocked_Domains
Block
[]Block traffic from SSL inspection-disabled Zscaler Client Connector platforms on locations.
Source CriteriaDestination CriteriaAction
Location Group:
Locations_CltCon_Enforce
Zscaler Client Connector:
Platforms with SSL disabled
URL Categories:
Blocked Categories
Destination Group:
NoSSL_Blocked_IPs, NoSSL_Blocked_Domains
Block
[]Block non-Zscaler Client Connector traffic from SSL inspection-disabled locations.
Source CriteriaDestination CriteriaAction
Location group:
Locations_NoSSL
Zscaler Client Connector:
No Zscaler Client Connector
URL Categories:
Blocked Categories
Destination Group:
NoSSL_Blocked_IPs, NoSSL_Blocked_Domains
Block
[]Block remote user traffic:
- If it is from SSL inspection-disabled Zscaler Client Connector platforms
or
- If it is not with Kerberos authentication.
Source CriteriaDestination CriteriaAction
Locations:
Road Warrior
Zscaler Client Connector:
Platforms with SSL disabled
URL Categories:
Blocked Categories
Destination Group:
NoSSL_Blocked_IPs, NoSSL_Blocked_Domains
Block
[]Whitelist from SSL inspection and other policies.
Source CriteriaDestination CriteriaActionAny
URL Categories:
Bypassed URL Categories
Destination Group:
NoSSL_NoOtherPolicies_IPs, NoSSL_NoOtherPolicies_Domains
Cloud Applications:
Bypassed Applications
Do Not Inspect & Bypass
[]Inspect traffic from any Zscaler Client Connector platforms on SSL inspection-enabled locations.
Source CriteriaDestination CriteriaAction
Location Group:
<!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}-->
Locations_SSL_CltCon_NoEnforce
Zscaler Client Connector:
Windows, MacOS, Android, iOS
URL Categories:
Inclusion List Categories
Inspect
[]Inspect traffic from certain Zscaler Client Connector platforms on SSL inspection-enabled locations.
Source CriteriaDestination CriteriaAction
Location Group:
<!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}-->
Locations_SSL_CltCon_Enforce
Zscaler Client Connector:
Only platforms with SSL enabled
URL Categories:
Inclusion List Categories
Inspect
[]Inspect non-Zscaler Client Connector traffic from SSL inspection-enabled locations.
Source CriteriaDestination CriteriaAction
Location Group:
Locations_SSL
Zscaler Client Connector:
No Zscaler Client Connector
URL Categories:
Inclusion List Categories
Inspect
[]Inspect remote user traffic:
- If it is from SSL inspection-enabled Zscaler Client Connector platforms.
or
- If it is with Kerberos authentication.
Source CriteriaDestination CriteriaAction
Locations:
Road Warrior
Zscaler Client Connector:
Platforms with SSL enabled or RWKRB enabled
URL Categories:
Inclusion List Categories
Inspect
[]Block traffic from any Zscaler Client Connector platform on SSL inspection-disabled locations.
Source CriteriaDestination CriteriaAction
Location Group:
<!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}-->
Locations_NoSSL_CltCon_NoEnforce
Zscaler Client Connector:
Windows, MacOS, Android, iOS
URL Categories:
Blocked Categories
Destination Group:
NoSSL_Blocked_IPs, NoSSL_Blocked_Domains
Block
[]Block traffic from SSL inspection-disabled Zscaler Client Connector platforms on locations.
Source CriteriaDestination CriteriaAction
Location Group:
Locations_CltCon_Enforce
Zscaler Client Connector:
Platforms with SSL disabled
URL Categories:
Blocked Categories
Destination Group:
NoSSL_Blocked_IPs, NoSSL_Blocked_Domains
Block
[]Block non-Zscaler Client Connector traffic from SSL inspection-disabled locations.
Source CriteriaDestination CriteriaAction
Location Group:
Locations_NoSSL
Zscaler Client Connector:
No Zscaler Client Connector
URL Categories:
Blocked Categories
Destination Group:
NoSSL_Blocked_IPs, NoSSL_Blocked_Domains
Block
[]Block remote user traffic:
- If it is from SSL inspection-disabled Zscaler Client Connector platforms.
or
- If it is without Kerberos authentication.
Source CriteriaDestination CriteriaAction
Locations:
Road Warrior
Zscaler Client Connector:
Platforms with SSL disabled
URL Categories:
Blocked Categories
Destination Group:
NoSSL_Blocked_IPs, NoSSL_Blocked_Domains
Block
[]Whitelist from SSL inspection and other policies.
Source CriteriaDestination CriteriaActionAny
URL Categories:
Bypassed URL Categories
Destination Group:
NoSSL_NoOtherPolicies_IPs, NoSSL_NoOtherPolicies_Domains
Cloud Applications:
Bypassed Applications
Do Not Inspect & Bypass
[]Inspect traffic from all Zscaler Client Connector platforms on locations.
Source CriteriaDestination CriteriaAction
Location Group:
<!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}-->
Locations_SSL_CltCon_NoEnforce
Zscaler Client Connector:
Windows, MacOS, Android, iOS
URL Categories:
Inclusion List Categories
Inspect
[]Inspect traffic from SSL inspection-enabled Zscaler Client Connector platforms on locations.
Source CriteriaDestination CriteriaAction
Location Group:
Locations_CltCon_Enforce
Zscaler Client Connector:
Platforms with SSL enabled
URL Categories:
Inclusion List Categories
Inspect
[]Inspect non-Zscaler Client Connector traffic from SSL inspection-enabled locations.
Source CriteriaDestination CriteriaAction
Location Group:
Locations_SSL
Zscaler Client Connector:
No Zscaler Client Connector
URL Categories:
Inclusion List Categories
Inspect
[]Inspect remote user traffic:
- If it is from SSL inspection-enabled Zscaler Client Connector platforms.
or
- If it is with Kerberos authentication.
Source CriteriaDestination CriteriaAction
Locations:
Road Warrior
Zscaler Client Connector:
Platforms with SSL enabled or RWKRB enabled
URL Categories:
Inclusion List Categories
Inspect
[]The auto-generated rules are created in the following order:
- Special rules: Zscaler recommended exemptions rule, O365 tenant restriction inspection rules, O365/UCaaS One Click rules
- Block rules when SSL inspection is disabled
- Organization exemption rules
- Inspection rules
- Default exemption rule
[]The following group entities are automatically created and assigned to the auto-generated SSL inspection rules after the ZIA service upgrade:
- [Location Groups](#location-group)
- [Destination Groups](#destination-group)
[]The following action settings are pre-configured in the auto-generated rules based on your previous global SSL inspection settings:
- For Inspect action:
- *Untrusted Server Certificates*, *OCSP Revocation Check*, *Show End User Notifications*, *Block Undecryptable Traffic*: Inherited from your previous configuration
- *Client and Server Min TLS Version*: TLS 1.0
- For Do Not Inspect & Evaluate action:
- *Untrusted Server Certificates*, *OCSP Revocation Check*: Disabled
- *Show End User Notifications*: Inherited from your previous configuration
- *Min TLS Version*: TLS 1.0
- For Block action:
- *Show End User Notifications*: Inherited from your previous configuration
[]Group NameDescriptionLocations_SSL
Includes locations with the following settings:
- *Enable SSL inspection*: Enabled
This is applicable for migration scenarios 1, 2, 3, and 4.
Locations_NoSSL
Includes all locations with the following settings:
- *Enable SSL inspection*: Disabled
This is applicable for migration scenarios 1, 2, 3, and 4.
Locations_CltCon_Enforce
Includes all locations with the following settings:
- *Enforce Zscaler Client Connector SSL Setting*: Enabled
This is applicable for migration scenarios 3 and 4.
<!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}-->
Locations_SSL_CltCon_Enforce
Includes all locations with the following settings:
- *Enable SSL inspection*: Enabled
- *Enforce Zscaler Client Connector SSL Setting*: Enabled
This is applicable for migration scenario 3.
<!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}-->
Locations_SSL_CltCon_NoEnforce
Includes all locations with the following settings:
- *Enable SSL inspection*: Enabled
- *Enforce Zscaler Client Connector SSL Setting*: Disabled
This is applicable for migration scenarios 3 and 4.
<!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}-->
Locations_NoSSL_CltCon_Enforce
Includes all locations with the following settings:
- *Enable SSL inspection*: Disabled
- *Enforce Zscaler Client Connector SSL Setting*: Enabled
This is applicable for migration scenario 2.
<!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}-->
Locations_NoSSL_CltCon_NoEnforce
Includes all locations with the following settings:
- *Enable SSL inspection*: Disabled
- *Enforce Zscaler Client Connector SSL Setting*: Disabled
This is applicable for migration scenarios 2, 3, and 4.
[]Group NameDescriptionNoSSL_Blocked_IPsIP address destination group to include all the IP addresses that were configured in *If SSL Inspection Is Disabled, Block HTTPS to These Sites*.NoSSL_Blocked_DomainsDomain destination group to include all the wildcard domains and FQDNs that were configured in* If SSL Inspection Is Disabled, Block HTTPS to These Sites*.NoSSL_NoOtherPolicies_IPsIP address destination group to include all the IP addresses that were configured in *Exempt These Hosts from Inspection & Other Policies*.NoSSL_NoOtherPolicies_DomainsDomain destination group to include all the wildcard domains and FQDNs that were configured in *Exempt These Hosts from Inspection & Other Policies*.

### Feature Available
#### Support for Data Center Filters
There are three new filters under Web Insights for Data Center.
New NSS Feed Outputs
The following web logs fields were added to NSS Feeds for Data Center:
- `%s{datacenter}`
- `%s{datacentercity}`
- `%s{datacentercountry}`
To learn more, see [About NSS Feeds](/zia/about-nss-feeds).

### Feature Available
#### Updates to Cloud Service API
The following updates were made to the cloud service API:
- [Firewall Policies resources are now available. With this update the API now fully supports create, read, update, and delete (CRUD) for these resources.](#FirewallAPI)
- [Traffic Forwarding resources are now available. These new resources are available for self-service GRE tunnel and static IP provisioning.](#TrafficForwardingAPI)
- [SSL Inspection Settings resources were removed. If you need to manage SSL bypass lists via API, you must use the destination group or a custom URL category.](#SSLAPI)
- [Location Management parameters no longer have an effect on SSL policy. They remain supported in the API payload in order to maintain backwards compatibility with existing scripts, but will be removed in future.](#LocationAPI)
With this update, the base URL for the cloud services API was changed from `admin.<Zscaler Cloud Name>/api/v1` to `zsapi.<Zscaler Cloud Name>/api/v1`. Where `<Zscaler Cloud Name>` is the cloud name that was provisioned for your organization (e.g., `zsapi.zscalerbeta.net/api/v1`). Zscaler highly recommends that you update your scripts to use the new base URL.
To learn more, see [API Reference](/zia/about-api) and [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).
- []POST /firewallFilteringRules
- PUT /firewallFilteringRules/{ruleId}
- DELETE /firewallFilteringRules/{ruleId}
- POST /ipDestinationGroups
- PUT /ipDestinationGroups/{ipGroupId}
- DELETE /ipDestinationGroups/{ipGroupId}
- POST /ipSourceGroups
- PUT /ipSourceGroups/{ipGroupId}
- DELETE /ipSourceGroups/{ipGroupId}
- POST /networkServices
- PUT /networkServices/{serviceId}
- DELETE /networkServices/{serviceId}
- POST /networkServiceGroups
- PUT /networkServiceGroups/{serviceGroupId}
- DELETE /networkServiceGroups/{serviceGroupId}
- []GET /greTunnels
- POST /greTunnels
- GET /greTunnels/availableInternalIpRanges
- PUT /greTunnels/{id}
- DELETE /greTunnels/{id}
- GET /vips/recommendedList
- GET /staticIP
- POST /staticIP
- POST /staticIP/validate
- GET /staticIP/{id}
- PUT /staticIP/{id}
- DELETE /staticIP/{id}
- []GET /sslSettings/exemptedUrls
- POST /sslSettings/exemptedUrls
- []sslScanEnabled
- zappSSLScanEnabled

### Feature Available
#### User Agent Support for Policies
You now can select a user agent when configuring the URL Filtering and Cloud App Control policies.
[See image.](#user-agent-url-cloud)
To learn more, see [Configuring the URL Filtering Policy](/zia/configuring-url-filtering-policy) and [Adding Rules to the Cloud App Control Policy](/zia/adding-rules-cloud-app-control-policy).
[]![Screenshot highlighting the User Agent field in the Add URL Filtering Rule window.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Add-URL-Filtering-Rule-User-Agent.png)

### Feature Available
#### ZIA Admin Portal Color Theme Enhancement
You can now choose a personalized color theme for the ZIA Admin Portal interface. The selected theme is only applicable to your admin profile.
[See image.](#user-icon-color-theme)
To learn more, see [Customizing Your Admin Account Settings](/zia/customizing-your-admin-account-settings).
[]![Screenshot of ZIA Admin Portal User icon displaying the UI color themes](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Admin-Portal-Color-Theme-Enhancement.png)

## April 12, 2021
### Feature Available
#### Local Browser Rendering for Cloud Browser Isolation
Cloud Browser Isolation now allows admins to choose if hyperlinks clicked by users in isolation are rendered in the isolation browser or the user's local browser. If this feature is enabled for an isolation profile, hyperlinks will be evaluated by the isolation session, and links leading to domains other than the one in the isolation session will be pushed outside of the isolation environment and rendered in the user's local browser.
[See image. ](#Local-Browser-Rendering)
To learn more, see [Local Browser Rendering for Cloud Browser Isolation](https://help.zscaler.com/zia/local-browser-rendering-cloud-browser-isolation).
[![CBI portal security control to allow local rendering ](/sites/default/files/downloads/zia/cloud-browser-isolation/editing-your-isolation-profile/add-new-ZIA-profile-Security-Control_Allow-Local-Browser-Rendering.png)
]

## March 15, 2021
### Feature Available
#### SaaS Security API
The following enhancements are now available for SaaS Security API.
New SaaS Application Support
You can now configure tenants for ServiceNow.
[See image.](#slack-sn-tenant)
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
Updates to SaaS Security API Policies
You can now configure the SaaS Security API Control policies and scan schedules for ITSM applications.
As part of this enhancement, the SaaS Security API page was renamed to SaaS Security API Control.
[See image.](#saas-security-api-control)
Additionally, the SaaS Security Posture Policy page was renamed to SaaS Security Posture Control.
[See image.](#saas-security-posture-control)
To learn more, see [Configuring the SaaS Security API Control Policy](/zia/configuring-saas-security-api-policies) and [Configuring the SaaS Security Posture Control Policy](/zia/configuring-saas-security-posture-policy).
Updates to the SaaS Assets Summary Report
You can now view ITSM application categories in the SaaS Assets Summary Report.
To learn more, see [SaaS Assets Summary Report](/zia/saas-assets-summary-report).
Updates to the SaaS Assets Report
You can now view the ITSM, CRM, and source code repository application categories in the SaaS Assets Report.
To learn more, see [Saas Assets Report](/zia/saas-assets-report) and [SaaS Assets Report: Assets with Incidents](/zia/saas-assets-report-assets-incidents).
Updates to SaaS Security Insights & Insights Logs
You can now view the updates to the SaaS Assets Summary Report in SaaS Security Insights and Insights Logs.
To learn more, see [SaaS Security Insights](/zia/saas-security-insights) and [SaaS Security Insights Logs](/zia/saas-security-insights-logs).
New Application Categories for NSS Feeds
There is a new application category in NSS feeds for SaaS Security API: SaaS Security ITSM. These application categories provide support for ServiceNow (ITSM).
There is also a new tab for ITSM in the SaaS Security Log Filters.
To learn more, see [Adding NSS Feeds for SaaS Security Logs](/zia/adding-nss-feeds-saas-security-logs).
New SaaS Security Fields for NSS Feed Outputs
The following web log fields were added to NSS Feeds under ITSM:
- `%d{num_internal_collab}`
- `%d{num_external_collab}`
- `%s{objectname}`
- `%s{objecttype}`
- `%s{file_msg_id}`
- `%s{filetypecategory}`
- `%s{hostname}`
- `%s{ohostname}`
- `%s{ofullurl}`
- `%s{internal_collabnames}`
- `%s{external_collabnames}`
- `%s{ointernal_collabnames}`
- `%s{oexternal_collabnames}`
- `%d{filesize}`
- `%s{file_msg_mod_time}`
- `%s{filepath}`
- `%s{component}`
- `%s{sha}`
To learn more, see [NSS Feed Output Format: SaaS Security Logs](/zia/nss-feed-output-format-saas-security-logs).
[]![The Slack and ServiceNow applications on the Add SaaS Application Tenant page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Add-SaaS-Application-Tenant-ServiceNow.png)
[]![The SaaS Security API Control policies](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-SaaS-Security-API-Control.png)
[]![The SaaS Security Posture Control policy](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-SaaS-Security-Posture-Control-policy.png)

## February 01, 2021
### Feature Available
#### SaaS Security Posture Report & Policy
The new SaaS Security Posture Report shows you the current state of your organization’s security posture for SaaS applications in relation to recommended security standards. It also allows you to see information on recommended security policies, security threats and their risk levels, and remediation activities.
[See image.](#report)
With the SaaS Security Posture Policy, you can configure the number of recommended security policies that the SaaS Security Posture Report includes in its analysis of your organization’s security posture.
[See image.](#policy)
To learn more, see [SaaS Security Posture Report](/zia/saas-security-posture-report) and [Configuring the SaaS Security Posture Policy](/zia/configuring-saas-security-posture-policy).
[]![The SaaS Security Posture Report and its different widgets and sections](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-SaaS-Security-Posture-Report.png)
[]![The SaaS Security Posture Policy page with all the policies listed and the status of each.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-SaaS-Security-Posture-Policy.png)

## January 29, 2021
### Feature Available
#### Sandbox Analysis Supported for SaaS Security API
Zscaler now supports Sandbox analysis for malware with SaaS Security API.
To learn more, see [About Sandbox](/zia/about-sandbox) and [About SaaS Application Tenants](/zia/about-saas-application-tenants).

## January 22, 2021
### Feature Available
#### SaaS Security API
The following enhancements are now available for SaaS Security API.
New SaaS Application Support
You can now configure tenants for GitHub.
[See image.](#github-tenant)
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
Updates to SaaS Security API Policies & Scan Configuration
You can now configure the SaaS Security API policies and scan schedules for source code repositories.
[See image.](#policy-image)
To learn more, see [Configuring SaaS Security API Policies](/zia/configuring-saas-security-api-policies).
Updates to the SaaS Assets Summary Report
You can now view GitHub in the SaaS Assets Summary Report.
To learn more, see [SaaS Assets Summary Report](/zia/saas-assets-summary-report).
Updates to SaaS Security Insights & Insights Logs
You can now view GitHub in SaaS Security Insights and Insights Logs.
To learn more, see [SaaS Security Insights](/zia/saas-security-insights) and [SaaS Security Insights Logs](/zia/saas-security-insights-logs).
[]![Screenshot highlighting GitHub under Choose the SaaS Application Provider on the Add SaaS Application Tenant page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Choose-SaaS-Application-Provider-github.png)
[]![Configuring the SaaS Security API policies for source code repository applications](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/SaaS-Policies-Source-Code-Repository.png)

## January 15, 2021
### Feature Available
#### SaaS Security API
The following enhancements are now available for SaaS Security API.
New SaaS Application Support
You can now configure tenants for Citrix ShareFile.
[See image.](#sharefile-tenant)
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
Updates to SaaS Security API Policies & Scan Configuration
You can now configure the SaaS Security API policies and scan schedules for ShareFile, a file sharing application.
Updates to the SaaS Assets Summary Report
You can now view ShareFile in the SaaS Assets Summary Report.
To learn more, see [SaaS Assets Summary Report](/zia/saas-assets-summary-report).
Updates to the SaaS Assets Report
You can now view ShareFile in the SaaS Assets Report.
To learn more, see [SaaS Assets Report](/zia/saas-assets-report).
Updates to SaaS Security Insights & Insights Logs
You can now view ShareFile in SaaS Security Insights and Insights Logs.
To learn more, see [SaaS Security Insights](/zia/saas-security-insights) and [SaaS Security Insights Logs](/zia/saas-security-insights-logs).
[]![Screenshot highlighting Citrix ShareFile under Choose the SaaS Application Provider on the Add SaaS Application Tenant page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Choose-SaaS-Application-Provider-ShareFile.png)
