# Release Upgrade Summary (2022)
Source: https://help.zscaler.com/zia/release-upgrade-summary-2022

This article provides a summary of all new features and enhancements per Zscaler cloud for Zscaler Internet Access (ZIA). Zscaler will email a notification to your organization's registered support contacts approximately one week before your cloud is upgraded. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com).

**Clouds:** zscaler.net, zscalerone.net, zscalertwo.net, zscalerthree.net, zscloud.net, zscalerbeta.net
The following service updates were deployed to zscaler.net on

## December 09, 2022
### Feature Available
#### Logs for SSL Handshake Failure
The following enhancements are now available for the client SSL handshake failure:
Updates to the Web Insights Logs
Two new filters and columns, Client SSL Handshake Failure Reason and Client SSL Handshake Failure Aggregate Count, are added to the Web Insights Logs.
[See image.](#ssl-handshake-failure-logs)
To learn more, see [Web Insights Logs: Filters](/zia/web-insights-logs-filters) and [Web Insights Logs: Columns](/zia/web-insights-logs-columns).
**Updates to NSS Feed Outputs for Web Logs**
Two new fields, `%s{cltsslfailreason}` and `%d{cltsslfailcount}`, are available when adding an NSS feed for web logs.
To learn more, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs).
[]![SSL Handshake Failure logs in the Web Insights Logs page](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-security-posture-report/ZIA-6.2-Client%20SSL%20handshake%20failure%20RN.png)

### Feature Available
#### New Apple File Type Support for File Type Control & DLP
The File Type Control and Data Loss Prevention (DLP) policies support a new Apple Documents file type in the Other Documents category. The Apple Documents file type encompasses the keynote, numbers, and pages file types.
[See image.](#apple-file-types)
[See image.](#File-Types-File-Type-Control)
To learn more, see [About File Type Control](/zia/about-file-type-control) and [About Data Loss Prevention](/zia/about-data-loss-prevention).
[] ![Selecting the Apple File Type for a DLP Policy](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Apple-File-Types.png?1671125512)
[] ![Selecting the Apple File Type for a File Type Control Policy](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Apple-File-Types-File-Type-Control.png)

## December 08, 2022
### Feature Available
#### DPI Settings Update for Isolation
An isolation container's DPI settings match the DPI settings of the user's device. Even when the isolation session is moved from one display to another, the isolation container keeps the DPI settings consistent with the new display from that device.
To learn more, see [What is Isolation](/isolation/what-is-isolation)?

## December 02, 2022
### Feature Available
#### SaaS Security API
The following enhancements are now available for SaaS Security API.
Updates to SaaS Application Support
You can configure tenants for the following applications:
- Jira Software (ITSM Application)
- Bitbucket (Source Code Repository Application)
[See image.](#saas_applications)
To learn more, see [About SaaS Application Tenants](/zia/about-saas-application-tenants).
Updates to SaaS Security API Control Policies & Scan Configuration
You can configure the SaaS Security API Control policies and scan schedules for the following applications:
- Jira Software (ITSM Application)
- Bitbucket (Source Code Repository Application)
To learn more, see [Configuring the SaaS Security API DLP Policy](/zia/configuring-saas-security-api-dlp-policy) and [Configuring the SaaS Security API Malware Detection Policy](/zia/configuring-saas-security-api-malware-detection-policy).
Updates to the SaaS Assets Summary Report
You can view the following applications in the SaaS Assets Summary Report:
- Jira Software (ITSM Application)
- Bitbucket (Source Code Repository Application)
To learn more, see [SaaS Assets Summary Report](/zia/saas-assets-summary-report).
Updates to the SaaS Assets Report
You can view the following applications in the SaaS Assets Report:
- Jira Software (ITSM Application)
- Bitbucket (Source Code Repository Application)
To learn more, see [Saas Assets Report](/zia/saas-assets-report) and [SaaS Assets Report: Assets with Incidents](/zia/saas-assets-report-assets-incidents).
Updates to SaaS Security Insights & Insights Logs
You can view the following applications in SaaS Security Insights and Insights Logs:
- Jira Software (ITSM Application)
- Bitbucket (Source Code Repository Application)
To learn more, see [SaaS Security Insights](/zia/saas-security-insights) and [SaaS Security Insights Logs](/zia/saas-security-insights-logs).
Updates to NSS Feeds for SaaS Security Logs
You can view the following applications in the SaaS Security application category:
- Jira Software (ITSM Application)
- Bitbucket (Source Code Repository Application)
To learn more, see [Adding NSS Feeds for SaaS Security Logs](/zia/adding-nss-feeds-saas-security-logs) and [Adding Cloud NSS Feeds for SaaS Security Logs](/zia/adding-cloud-nss-feeds-saas-security-logs).
[]![List of SaaS Applications.](/sites/default/files/downloads/M365_01_Providers_Comm_03.png)

### Feature Available
#### SaaS Security Posture Control
The following enhancements are now available for SaaS Security Posture Control.
New SaaS Application Support
You can now configure tenants for Bitbucket.
[See image.](#saas-apps-bitbucket)
To learn more, see [About SaaS Application Tenants](/zia/about-saas-application-tenants).
Updates to the SaaS Security Posture Control Policy & Report
Bitbucket is now available for the SaaS Security Posture Control policy and SaaS Security Posture Report.
To learn more, see [Configuring the SaaS Security Posture Policy](/zia/configuring-saas-security-posture-control-policy) and [SaaS Security Posture Report](/zia/saas-security-posture-report).
[]![List of SaaS Applications.](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/what-zscaler-business-intelligence-zbi/M365_01_Providers_Comm_03.png)

## November 18, 2022
### Feature Available
#### Support for Device Trust Levels
You can select a device trust level for all Zscaler Client Connector traffic while configuring various policies in the ZIA admin portal. This new criterion is added to the following policies:
- [SSL Inspection](/zia/configuring-ssl-inspection-policy)
- [Firewall Filtering](/zia/configuring-firewall-filtering-policy)
- [File Type Control](/zia/configuring-file-type-control-policy)
- [Cloud App Control](/zia/adding-rules-cloud-app-control-policy)
- [URL Filtering](/zia/configuring-url-filtering-policy)
The trust levels assigned to the devices are based on the [posture configurations](/client-connector/adding-zia-posture-profiles) in the Zscaler Client Connector Portal.
The Firewall Policies and URL Filtering Policies resources within the cloud service API have been updated to support rule criteria based on devices, device groups, and device trust levels. The following endpoints support `devices`, `deviceGroups`, and `deviceTrustLevels `within the request body and the response:
- `GET /firewallFilteringRules`
- `POST /firewallFilteringRules`
- `GET /firewallFilteringRules/{ruleId}`
- `PUT /firewallFilteringRules/{ruleId}`
- `GET /urlFilteringRules`
- `POST /urlFilteringRules`
- `GET /urlFilteringRules/{ruleId}`
- `PUT /urlFilteringRules/{ruleId}`
To learn more about each endpoint, see the [API Reference](/zia/about-api).

## November 11, 2022
### Feature Available
#### New Attributes for Cloud Applications
You can select the following cloud application attributes under the Administration > Risk Profiles > Add/Edit Cloud Application window:
- File Sharing
- SSL Cert Key Size
- Vulnerable to Heartbleed
- Vulnerable to Poodle
- Vulnerable to Logjam
- Support for WAF
- Remote Access Screen Sharing
- Vulnerability Disclosure Policy
- Sender Policy Framework
- DomainKeys Identified Mail
- Domain-Based Message Authentication
As part of this enhancement, the following cloud application attributes are renamed:
- TLS 1.1 Support is now Data Encryption in Transit
- SSL Certificate Validity is now Valid SSL Certificate
- Vulnerability is now Published CVE Vulnerability
[See image.](#add-cloud-app-risk-profile)
You can also see these attributes on the following pages:
- Application Information (Analytics > SaaS Security Report > Applications)
[See image.](#app-info-attributes)
- Cloud Application Dashboard (Dashboard > Cloud Applications)
[See image.](#cloud-app-dashboard)
To learn more, see [Adding a Cloud Application Risk Profile](/zia/adding-cloud-application-risk-profile), [Shadow IT Report](/zia/shadow-it-report), and [About Dashboard](/zia/about-dashboards#CSV-desc).
[]![Attributes on the Application Information Page](/sites/default/files/downloads/ZIA-6.2-Application-Information-Page-RN.png)
[]![Screenshot of the Add Cloud Application Risk Profile Window with New Attributes](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Add-Cloud-Application-Risk-Profile.png)
[]![Screenshot of the Cloud Application Dashboard](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Cloud-Application-Dashboard.png)

## November 04, 2022
### Feature Available
#### User Risk Report
You can monitor your organization's risk exposure from a user's perspective from the User Risk Report page. The report shows the risk score generated based on user anomalies, DLP violations, risky user behavior and other suspicious factors.
[See image.](#user-risk-report-page)
To learn more, see [User Risk Report](/zia/user-risk-report).
[]![User Risk Report in the ZIA Admin Portal](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report/RN-ZIA-6.2-user%20risk%20report.png)

## October 21, 2022
### Feature Available
#### Cloud HSM Support for Intermediate CA Certificates
Zscaler introduces Cloud HSM support for custom intermediate CA certificates. You can also configure multiple intermediate CA certificates for a single tenant (up to 8 for cloud HSM protection type and up to 2 for software protection type).
The enhancements to the intermediate CA certificates include the following updates in the ZIA Admin Portal:
SSL Inspection Policy
The following updates appear on the Policy > SSL Inspection page:
- The Advanced SSL Inspection Settings tab is deprecated and replaced with a new Intermediate CA Certificates tab. You can configure custom intermediate certificates signed by your trusted CA for your organization for the following protection types:
- Software Protection
- Cloud HSM Protection
[See image.](#intermediate-ca-certificate)
- Two new criteria, Override Default Intermediate CA Certificate and Intermediate CA Certificates, are added to the SSL Inspection Policy page.
[See image.](#add-ssl-inspection-rule)
In addition to the above updates, the `/sslSettings` endpoints within the cloud service API are deprecated in favor of new `/intermediateCaCertificate` endpoints. The new endpoints allow you to configure and manage multiple intermediate CA certificates with software or cloud HSM protection for SSL inspection.
- [Deprecated Endpoints](#deprecated-sslsettings-endpoints)
- [New Endpoints](#new-intermediatecacertificate-endpoints)
The Postman collection has also been updated to include new and updated resources.
To learn more, see [About Intermediate CA Certificates](/zia/about-intermediate-ca-certificates), [About SSL Inspection Policy](/zia/about-ssl-inspection-policy), [API Reference](/zia/about-api), [API Rate Limit Summary](/zia/api-rate-limit-summary), [Intermediate CA Certificates Use Cases](/zia/intermediate-ca-certificates-use-cases), and [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).
**Insights Logs**
A new weblog field, Intermediate CA Protection Type, is added to capture transactions associated with intermediate CA certificates. This field is available for filtering and as a new column in Web Insights Logs.
[See image.](#intermediate-ca-certificate-type-filter)
The following actions are added to the SSL Policy Reason field in Web Insights Logs:
- Not inspected because of HSM error
- Not inspected because of mutual TLS authentication
- Not inspected because of undecryptable traffic
- Not inspected because of Zscaler service domains
To learn more, see [Web Insights Logs: Filters](/zia/web-insights-logs-filters) and [Web Insights Logs: Columns](/zia/web-insights-logs-columns).
NSS Feeds
The field `%s{keyprotectiontype}` is available when adding an NSS feed for web logs.
To learn more, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs).
[]The following `/sslSettings` endpoints are deprecated:
- `POST /sslSettings/generatecsr`
- `GET /sslSettings/downloadcsr`
- `GET /sslSettings/showcert`
- `POST /sslSettings/uploadcert/text`
- `POST /sslSettings/uploadcertchain/text`
- `DELETE /sslSettings/certchain`
[]The SSL Inspection Settings resources include the following new endpoints:
- `GET /intermediateCaCertificate`
- `POST /intermediateCaCertificate`
- `GET /intermediateCaCertificate/downloadAttestation/{certId}`
- `GET /intermediateCaCertificate/downloadCsr/{certId}`
- `GET /intermediateCaCertificate/downloadPublicKey/{certId}`
- `POST /intermediateCaCertificate/finalizeCert/{certId}`
- `POST /intermediateCaCertificate/generateCsr/{certId}`
- `POST /intermediateCaCertificate/keyPair/{certId}`
- `GET /intermediateCaCertificate/lite`
- `GET /intermediateCaCertificate/lite/{certId}`
- `PUT /intermediateCaCertificate/makeDefault/{certId}`
- `GET /intermediateCaCertificate/readyToUse`
- `GET /intermediateCaCertificate/showCert/{certId}`
- `GET /intermediateCaCertificate/showCsr/{certId}`
- `POST /intermediateCaCertificate/uploadCert/{certId}`
- `POST /intermediateCaCertificate/uploadCertChain/{certId}`
- `POST /intermediateCaCertificate/verifyKeyAttestation/{certId}`
- `GET /intermediateCaCertificate/{certId}`
- `PUT /intermediateCaCertificate/{certId}`
- `DELETE /intermediateCaCertificate/{certId}`
[![Screenshot of Intermediate CA Certificate tab in the SSL Inspection Policy page](/sites/default/files/downloads/zia/policies/ssl-inspection/configuring-intermediate-ca-certificates/Zia-intermediate-ca-certificate-release-note-image.png)
]
[![Screenshot of Intermediate CA Certificate Type in the Web Insights Logs](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/zia-web-logs-intermediate-ca-cert-release-note.png)
]
[![Screenshot of Add SSL Inspection Rule in the SSL Inspection policy page](/sites/default/files/downloads/zia/policies/ssl-inspection/configuring-intermediate-ca-certificates/Zia-ssl-inspection-policy-release-note-image.png)
]

## October 14, 2022
### Feature Available
#### Enhancement to File Type Control Rule
The Cloud Applications criterion is added to the File Type Control rule. You can select any number of cloud applications or cloud application classes for this rule.
[See image.](#file-type-control-policy)
To learn more, see [Configuring the File Type Control Policy](/zia/configuring-file-type-control-policy).
[]![Screenshot of the Add File Type Control Rule Window with Cloud Applications](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Add-File-Type-Control-Rule-6.2.png)

### Feature Available
#### File Type Control Enhancements
You can configure file type control rules based on two new criteria:
- Active Content: Applies the rule to files with active content. This criterion is applicable only for Microsoft Office and PDF file formats.
- Unscannable Files: Applies the rule to files that the Zscaler service is unable to scan.
[See image.](#ftp-active-content-unscannable-file)
To learn more, see [Configuring the File Type Control Policy](/zia/configuring-file-type-control-policy).
[]![Active content and unscannable file criteria in file type control rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ftp-active-content-unscannable-file.png)

## October 07, 2022
### Feature Available
#### API Authentication Using OAuth 2.0
The Zscaler service supports OAuth 2.0 authentication to securely access the cloud service API. The Zscaler service uses the Client Credentials flow, in which client applications exchange their credentials for an access token and gain access to protected resources outside the context of users. The Zscaler service supports OAuth 2.0 implementation with PingFederate, Okta, and Azure AD.
To learn more, see [About API Authentication Using OAuth 2.0](/zia/about-api-authentication-using-oauth-2.0) and [Getting Started](/zia/getting-started-zia-api).
OAuth 2.0 Authentication relies on the following new configurations in the ZIA Admin Portal:
Configuring API Roles
An API role defines a client application's permission and access to the different API categories in the Zscaler Cloud Service API. An API role is not assigned to an admin. Instead, it is used during the configuration of an external OAuth 2.0 authentication server for API authentication.
Configuring an API role is one of the tasks you must complete before configuring an external OAuth 2.0 authentication server for API authentication. You can configure API roles under Administration > Role Management > Add API Role.
[See image.](#api-role-configuration-window)
The `GET /adminRoles/lite` endpoint within the cloud service API has also been updated to support a new `includeApiRole` query parameter.
To learn more, see [About Role Management](/zia/about-role-management), [Adding API Roles](/zia/adding-api-roles), and [API Reference](/zia/about-api).
Adding OAuth 2.0 Authorization Servers
The Zscaler service requires you to add your authorization servers to the ZIA Admin Portal to verify the authenticity of the access token (JSON Web Token) in API requests and optionally validate against various supported claims.
You can add and manage your authorization servers under Administration > Cloud Service API Security > OAuth 2.0 Authorization Servers.
[See image.](#auth-server-configuration-window)
To learn more, see [About OAuth 2.0 Authorization Servers](/zia/about-oauth-2.0-authorization-servers) and [Managing OAuth 2.0 Authorization Servers](/zia/managing-oauth-2.0-authorization-servers).
[]![A screenshot of the API Role configuration window](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/API-role-configuration-window_0.png)
[]![A screenshot of the OAuth 2.0 Authorization server configuration window](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/auth-server-configuration-window.png?1660848388)

### Feature Available
#### Cloud App Control Policy Rules Enhancement
You can caution users with an EUN before allowing access to the selected cloud applications by using the newly added Caution button to the Add/Edit Cloud App Category Rule page (Policy > URL & Cloud App Control > Cloud App Control Policy > Add).
[See image.](#caution-action)
The Caution button is unavailable for the DNS Over HTTPS Services cloud app category.
To learn more, see [Adding Rules to the Cloud App Control Policy](/zia/adding-rules-cloud-app-control-policy).
[]![Screenshot of the Add Cloud App Control Rule window with Caution.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Add-Cloud-App-Control-Rule-Window-with-Caution.png)

### Feature Available
#### Cloud Application Instances
The cloud application instances feature allows you to create instances for cloud applications using instance identifiers. This provides granular control of the actions in the Cloud App Control policy and DLP policy based on the domain types.
[See image.](#cloud-app-instances)
To learn more, see [About Cloud Application Instances](/zia/about-cloud-application-instances).
[]![Screenshot of Cloud Application Instances](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Cloud-Applications-Instances-RN.png)

### Feature Available
#### Cyber Risk Report
The Cyber Risk Report (Analytics > Cyber Risk Report) gives high-level visibility and insight into your organization’s policy structure to holistically evaluate and compare the posture against emerging cyber threats. The report provides a risk score by evaluating the organization's policy configuration, traffic patterns, and feature capabilities against Zscaler's best practices.
[See image.](#cyber-risk-report)
[]![The Cyber Risk Report page ](/sites/default/files/downloads/ZIA-6.2-cyber%20risk%20report.png)
To learn more, see [Cyber Risk Report](/zia/cyber-risk-report).

### Feature Available
#### DLP Support for Italian Fiscal Codes and Hong Kong Identity Card Numbers
We have added two new predefined DLP dictionaries:
- Fiscal Code (Italy): This dictionary detects Italian fiscal codes from Italy.
- Identity Card Number (Hong Kong): This dictionary detects identity card (HKID) numbers from Hong Kong.
[See image.](#DLP-Dictionaries-Page)
To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).
[]![Viewing the Fiscal Code (Italy) and Identity Card Number (Hong Kong) Dictionaries in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-DLP-Dictionaries-Engines-Fiscal-Code-Italy-Identity-Card-Number-HongKong.png?1676489416)

### Feature Available
#### End of Support for Microsoft Internet Explorer
Zscaler no longer supports Microsoft Internet Explorer (IE) as [Microsoft](https://www.microsoft.com/en-us/download/internet-explorer.aspx) has phased out IE since June 2022.
To learn more, see [About Supported Browsers](/zia/supported-browsers) within the ZIA Admin Portal.

### Feature Available
#### Enhancement to Data Loss Prevention
Inspect Downloads is a new option available for Data Loss Prevention (DLP) policy rules with content inspection. This enhancement allows you to enable DLP inspection for content downloaded from specific cloud applications.
[See image.](#inspect-downloads-image)
To learn more, see [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection).
[]![The Inspect Downloads option for ZIA Data Loss Prevention policy rules](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-DLP-Inspect-Downloads.png)

### Feature Available
#### Enhancement to System & Development Cloud App Control Rule
You can granularly control the actions of the System & Development cloud app control rule. As part of this enhancement, the following action-specific options are added to the Add System & Development Rule window:
- Viewing
- Allow: Allows users to view content on the application
- Block: Blocks users from viewing content on the application
- Isolate: Isolates traffic that matches the cloud app control rule through a remote browser
- Uploading
- Allow: Allows users to upload content to the application
- Block: Blocks users from uploading content to the application
[See image.](#add-system-development-rule-window)
To learn more, see [Adding a System & Development Rule for Cloud App Control](/zia/adding-system-development-rule-cloud-app-control).
[]![Screenshot of Add System and Development Rule window.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Add-System-and-Development-Rule.png)

### Feature Available
#### Enhancement to URL Category
The URL category, Sexuality, is now known as Body Art.
[See image.](#url-category-body-art)
To learn more, refer to the [Help Browser](/zia/using-zscaler-help-browser) within the Admin Portal.
[] ![Screenshot of ZIA URL Categories page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-URL-Categories-Body-Art.png)

### Feature Available
#### Minimum Threat Score Customization in Sandbox Policy
With AI Quarantine enabled in a sandbox policy, you can now enter a custom minimum threat score value between 40 and 70 to allow downloading of files below the entered value. The default value is 40, but manually entering a value can be useful if you work with files that may otherwise be flagged as a threat.
[See image.](#threatscore)
This feature introduces the following enhancements to the sandbox rule configuration and insights logs:
Configuring the Sandbox Policy
The following categories are added to the Sandbox Rules categories:
- Sandbox Offsec Tools
- Sandbox Ransomware
- Sandbox Suspicious
[See image.](#sandbox-categories)
To learn more, see [Configuring the Sandbox Policy](/zia/configuring-sandbox-policy).
Insights Logs
The following categories are added to the Threat Category filter on the Web and Mobile Insights Logs pages:
- Sandbox Offensive Security Tools
- Sandbox Ransomware
- Suspicious
[See image.](#web-logs-sandbox)
To learn more, see [Web Data Types and Filters](/zia/web-data-types-and-filters) and [Mobile Insights Logs: Filters](/zia/mobile-insights-logs-filters).
[] ![Sandbox Categories drop-down in the Edit Sandbox Rule window](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-6.2-Sandbox%20categories.png)
[] ![Threat Categories for Sandbox ](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/logs/web-insights-logs-filters/ZIA-6.2-Sandbox%20logs.png)
[![Edit Sandbox Rule window.](/sites/default/files/downloads/zia/policies/sandbox/configuring-sandbox-policy/sandbox_rule_2022.png)
]

### Feature Available
#### New File Types Supported for File Type Control & DLP
The File Type Control and Data Loss Prevention (DLP) policies support new file types in the following categories:
- Archive
- Audio
- Database
- Executable
- Image
- Mac Documents
- Media
- Microsoft Office
- Mobile
- Online Gaming
- Open Office Files
- Other Documents
- Source Code
- Video
- Web Content
Mac Documents, Media, and Open Office Files are new categories.
To see the new file types added for each category, go to the [File Type Control](/zia/about-file-type-control) and [Data Loss Prevention](/zia/about-data-loss-prevention) pages in the ZIA Admin Portal.

### Feature Available
#### Secure Browsing
The Secure Browsing module is added to the Policy section in the Admin Portal. You can configure the Smart Browser Isolation policy from this module, which automatically isolates potentially malicious web content using the AI/ML models.
As part of this enhancement, the Browser Control policy has been moved to the Secure Browsing module.
[See image.](#smart-browser-isolate)
To learn more, see [Configuring Smart Browser Isolation Policy](/zia/configuring-smart-browser-isolation-policy).
[![Screenshot of Smart Browser Isolation in the Secure Browsing module. ](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Secure-Browsing.png)
]

### Feature Available
#### Support for Admin User Deletion Through SCIM
You can configure the future action taken against an admin account when it is deleted using SCIM. This setting is found in the new Advanced Configuration section of the Administrator Management page.
[See image.](#Administrator-Management)
To learn more, see [About Administrator Management](/zia/about-administrator-management) and [Configuring Advanced Configuration for Admins](/zia/configuring-advanced-configuration-admins).
[]![Defining Advanced Configuration on the Administrator Management Page in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Administrator-Management-Page-Advanced-Config-Section.png)

### Feature Available
#### Support for Custom File Hashes
You can now add custom MD5 file hashes in the sandbox advanced policy settings.
[See image.](#customhash)
In addition, the cloud service API includes the following endpoints to read or update the custom blocklist for MD5 file hashes:
- `GET /behavioralAnalysisAdvancedSettings `
- `PUT /behavioralAnalysisAdvancedSettings `
- `GET /behavioralAnalysisAdvancedSettings/fileHashCount `
The Postman collection has also been updated to include the new resources.
To learn more, see [Add Custom File Hashes](/zia/add-custom-file-hashes), [API Reference](/zia/about-api), [API Rate Limit Summary](/zia/api-rate-limit-summary), and [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).
[![Add custom file hashes in the sandbox Advanced Policy Settings tab.](/sites/default/files/downloads/zia/policies/sandbox/custom_file_hash.png)
]

### Feature Available
#### Support for Event Logs
A new Event Logs page is added to the ZIA Admin Portal under Administration. This page lists all the recorded SCIM client activity, such as creating, updating, deleting, etc. user or group accounts.
[See image.](#event-logs)
In addition, the cloud service API now includes the following endpoints to generate and download event log reports for SCIM client activities:
- `GET /eventlogEntryReport`
- `POST /eventlogEntryReport`
- `DELETE /eventlogEntryReport`
- `GET /eventlogEntryReport/download`
The Postman collection has also been updated to include the new resources.
To learn more, see [About Event Logs](/zia/about-event-logs), [API Reference](/zia/about-api), [API Rate Limit Summary](/zia/api-rate-limit-summary), and [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).
[![Screenshot of Event Logs page in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/zia-event-logs-page-release-notes.png)
]

### Feature Available
#### Support for PAC File Versioning
The following enhancements are now available for the PAC file versioning feature:
Updates to the Hosted PAC Files
The following updates appear on the Administration > Hosted PAC Files page:
- The Hosted PAC Files table includes the following new columns:
- Name
- Number of Hits
- Currently Deployed Version
[See image.](#hosted-pac-files-table)
- A new Export icon is added to the Hosted PAC Files table. You can export a PAC file as a text, PAC, or JS file.
[See image.](#Export-icon)
- A new Preview Version Details page is added. This page allows you to create multiple versions of your custom PAC files. You can host up to 10 versions of a PAC file in the ZIA Admin Portal at a time.
[See image.](#preview-version-details)
- A new Manage PAC File page is added. This page allows you to manage all versions of your custom PAC files and compare the contents of any two PAC file versions. You can also view the details of the currently deployed PAC file version in the View Deployed Version tab.
[See image.](#manage-pac-file)
- The PAC file verification is updated with an enhanced library to capture broader JavaScript errors in the PAC file syntax. An error message displays the line number and the type of error in the PAC file content.
[See image.](#pac-file-verification-error)
- The maximum number of PAC files per organization is 256 by default. Contact Zscaler Support to increase the limit of PAC files to 1024.
To learn more, see [About Hosted PAC Files](/zia/about-hosted-pac-files) and [Using Custom PAC Files to Forward Traffic to ZIA](/zia/using-custom-pac-file-forward-traffic-zia).
Updates to the Audit Logs
The following actions are added to the Administration > Audit Logs page:
- Change Deployed PAC Version
- Create New PAC Version
- Delete PAC
- Delete PAC Version
- Stage PAC Version
[See image.](#audit-log-actions)
To learn more, see [About Audit Logs](/zia/about-audit-logs).
[![Screenshot of Hosted PAC Files table in ZIA Admin Portal](/sites/default/files/downloads/zia/traffic-forwarding/pac-files/about-hosted-pac-files/zia-hosted-pac-files-table-release-note.png)
]
[![Screenshot of Export icon on the Hosted PAC Files page in ZIA Admin Portal](/sites/default/files/downloads/zia/traffic-forwarding/pac-files/about-hosted-pac-files/zia-hosted-pac-files-eport-icon-release-note.png)
]
[![Screenshot of Preview Version Details page in the Hosted PAC Files page](/sites/default/files/downloads/zia/traffic-forwarding/pac-files/about-hosted-pac-files/zia-hosted-pac-files-preview-page-release-note.png)
]
[![Screenshot of the PAC File actions in the Audit Logs page](/sites/default/files/downloads/zia/traffic-forwarding/pac-files/about-hosted-pac-files/zia-hosted-pac-files-audit-logs-page.png)
]
[![Screenshot of Manage PAC Files page in Administration > Hosted PAC Files](/sites/default/files/downloads/zia/traffic-forwarding/pac-files/about-hosted-pac-files/zia-hosted-pac-files-manage-pac-release-note.png)
]
[]![Screenshot of PAC file verification error on the Hosted PAC Files page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/zia-hosted-pac-files-verification-error.png)

### Feature Available
#### Support for Risk Index Override
You can now alter and override the Zscaler-computed risk index value for the cloud applications on the Application Information page.
[See image.](#override-risk-index)
To learn more, see [Shadow IT Report](/zia/shadow-it-report).
[]![Override Zscaler-Computed Risk Index](/sites/default/files/downloads/zslogin/administration/user-management/about-users/ZIA-6.2-edit-risk-index-shadow-it-report.png)

### Feature Available
#### Support for Subcloud Management
The subclouds feature within the ZIA Admin Portal allows you to view and edit the subclouds that are set up for your organization. You can now edit a subcloud from the Subclouds page in the ZIA Admin Portal to temporarily disable the data centers under scheduled maintenance or data centers with capacity issues, trust incidents, site or region service issues, excessive latency, congestion, peering issues, etc.
[See image.](#Subclouds-Page)
To learn more, see [Understanding Subclouds](/zia/understanding-subclouds).
[]![Screenshot of Edit Subcloud](/sites/default/files/downloads/zia/traffic-forwarding/editing-subcloud/Edit_Subcloud_0.png)

### Feature Available
#### Support for Wildcard FQDN in Control Policies & Destination Groups
You can now configure wildcard fully qualified domain names (FQDNs) as a policy criterion and destination group besides FQDNs. The following fields are renamed because of this enhancement:
- The IP Address or FQDN field is renamed to IP Address or Wildcard FQDN in the following traffic control settings:
- [Firewall Filtering Policy](/zia/configuring-firewall-filtering-policy) (Policy > Firewall Control > Firewall Filtering Policy > Add Firewall Filtering Rule > Destination IP > IP Address or Wildcard FQDN)
- [NAT Control Policy](/zia/configuring-nat-control-policy) (Policy > Firewall Control > NAT Control Policy > Add NAT Control Rule > Destination IP > IP Address or Wildcard FQDN)
- [IPS Control](/zia/configuring-ips-control-policy) (Policy > IPS Control > Add IPS Control Rule > Destination IP > IP Address or Wildcard FQDN)
[See image.](#wildcard-common)
- The Destination IP Address / FQDN field is renamed to Destination IP Address / Wildcard FQDN in the Policy > Forwarding Control > Add Forwarding Rule > Destination tab.
[See image.](#forwardpol-wildcard)
To learn more, see [Configuring Forwarding Policy](/zia/configuring-forwarding-policy).
- The FQDN Domain type is renamed to Wildcard FQDN in the Administration > IP & FQDN Groups > Destination Groups > Add Destination Groups window.
[See image.](#zia-wildcardfqdn)
To learn more, see [Configuring Destination IP Groups](/zia/configuring-destination-ip-groups).
[]![IP Address or Wildcard FQDN Screenshot](/sites/default/files/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-control/configuring-firewall-filtering-policy/zia-wildcard.png)
[]![Destination IP Address / Wildcard FQDN Screenshot](/sites/default/files/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-control/configuring-firewall-filtering-policy/forwardpolicy.png)
[]![Wildcard FQDN Screenshot](/sites/default/files/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-control/configuring-firewall-filtering-policy/des-wildcard.png)

### Feature Available
#### Update to the Country Variable in PAC Files
The MaxMind GeoIP Legacy database is deprecated and replaced with MaxMind GeoIP2, which supports the countries listed on [GeoNames](https://www.geonames.org/countries/). Refer to the GeoNames link when configuring the `${COUNTRY}` variable in your PAC file.
To learn more, see [Writing a PAC File](/zia/writing-pac-file).

### Feature Available
#### Updates to Firewall Insights Logs
Firewall Insights Logs have been improved to enhance clarity around sessions that are handled by the web proxy (secure web gateway). Firewall Insights Logs use a new Blocked by Web Proxy Policy firewall filtering rule to indicate these sessions. The full details of these transactions continue to be displayed in Web Insights Logs.
To learn more, see [Firewall Insights Logs: Columns](/zia/firewall-insights-logs-columns) and [About Network Applications](/zia/about-network-applications).

### Feature Available
#### Updates to SaaS Security API Control Policies
The following enhancements are available for the SaaS Security API Control Policies:
Updates to the Data Loss Prevention Policy
You can configure various actions for the following applications under the DLP Rule for the SaaS Security API Control policies:
- CRM Application:
- Change to Read Only for All Collaborators
- Change to Read Only for External Collaborators
- Change to Read Only for Internal Collaborators
- Quarantine
- Remove
- Remove External Collaborators and Shareable Link
- Remove Internal Collaborators and Shareable Link
- Remove Public Shareable Link
- Remove Sharing
- Report Incident Only
[See image.](#dlp-crm)
- ITSM Applications
- Quarantine
- Remove
- Report Incident Only
[See image.](#dlp-itsm)
To learn more, see [Configuring the SaaS Security API DLP Policy](/zia/configuring-saas-security-api-dlp-policy).
Updates to the Malware Detection Policy
You can now configure the Remove Malware action for the following applications under the Malware Detection Rule for the SaaS Security API Control policies:
- CRM Application
[See image.](#malware-detection-rule-crm)
- ITSM Applications
[See image.](#malware-detection-rule-itsm)
To learn more, see [Configuring the SaaS Security API Malware Detection Policy](/zia/configuring-saas-security-api-malware-detection-policy).
[]![The Add Malware Detection Rule window allows you to create malware rules for each tenant under CRM.](/sites/default/files/downloads/zia/policies/saas-security-api/saas-security-api-policies/saas-security-api-control/configuring-saas-security-api-malware-detection-policy/SaaS%20Security%20API_Malware_CRM.png)
[]![The Add Malware Detection Rule window allows you to create malware rules for each tenant under ITSM.](/sites/default/files/downloads/zia/policies/saas-security-api/saas-security-api-policies/saas-security-api-control/configuring-saas-security-api-malware-detection-policy/SaaS%20Security%20API_Malware_ITSM.png)
[]![The Add DLP Rule window allows you to create DLP rules for each tenant under CRM.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/DLP_Policy_Actions_for_CRM.png)
[]![The Add DLP Rule window allows you to create DLP rules for each tenant under ITSM.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/DLP_Policy_Actions_for_ITSM.png)

## September 24, 2022
### Feature Available
#### Enhancement to the EDM Template Process
An EDM Indexing Failed Schemas notification is displayed on the Notification pane of the ZIA Admin Portal when an EDM template is processed and it exceeds the duplicate primary key limit of 2048 for your organization. The EDM template that exceeded the duplicate primary key limit also receives an error status in the Index Tool with a primary key limit error type.
[See image.](#EDM-Schema-Notification)
To learn more, see [About Notification](/zia/about-notification) and [About Exact Data Match](/zia/about-exact-data-match).
[![Viewing the Notification Pane in the ZIA Admin Portal](/sites/default/files/downloads/zia/policies/data-loss-prevention/dlp-exact-data-match/about-exact-data-match/ZIA_DLP_EDM_Indexing_Failed_Schema_Notification_RN.png)
]

## September 22, 2022
### Feature Available
#### Accessing Multiple Sessions In Isolation
Users can access multiple active isolation sessions at a time per device per browser window type. For example, if a user begins an isolation session in a Chrome browser window, they can start an additional isolation session for a different web page in a Firefox browser window.
To learn more, see [Accessing Multiple Sessions In Isolation](/isolation/accessing-multiple-sessions-isolation) and [Limits in Cloud Browser Isolation](/zia/limits-cloud-browser-isolation).

## September 07, 2022
### Feature Available
#### Zscaler Deception SSO Integration
A new option, Zscaler Deception, is now available under Policy. This option allows you to access the Zscaler Deception Admin Portal from the ZIA Admin Portal using SSO.
[See image.](#Deception-Link)
To learn more, see [Accessing the Zscaler Deception Admin Portal using SSO](/zia/accessing-zscaler-deception-portal-using-sso).
Contact Zscaler Support to configure the subscription for your tenant to include Zscaler Deception.
[]![Screenshot of Deception Link on ZIA Admin Portal](/sites/default/files/downloads/zia/documentation-knowledgebase/policies/accessing-zscaler-deception-portal-using-sso/Deception_SSO_0.png)

## August 29, 2022
### Feature Available
#### DLP Support for Microsoft Information Protection (MIP) Labels
You can easily define an inline web Data Loss Prevention (DLP) policy for MIP labels. The following enhancements were made to support using MIP labels in DLP policies:
- A new MIP Labels page (Administration > Microsoft Information Protection (MIP) Labels) was added. This page enables you to:
- Add and edit a MIP account so that MIP labels in Microsoft can be retrieved from Microsoft and associated with the MIP account in the ZIA Admin Portal.
- View all of the MIP labels associated with different MIP accounts in the ZIA Admin Portal.
- A new dictionary type of Microsoft Information Protection (MIP) was added for DLP dictionaries. This enables you to add a custom DLP dictionary for specific MIP labels using the Add DLP Dictionary window (Administration > DLP Dictionaries & Engines > Add DLP Dictionary).
To learn more, see [About Microsoft Information Protection (MIP) Labels](/zia/about-microsoft-information-protection-labels), [Adding a MIP Account](/zia/adding-mip-account), [Retrieving MIP Labels from Microsoft to the MIP Account](/zia/retrieving-mip-labels-microsoft-zscaler), [Adding Custom DLP Dictionaries](/zia/adding-custom-dlp-dictionaries), and [Defining Microsoft Protection Labels for Custom DLP Dictionaries](/zia/defining-microsoft-information-protection-labels-custom-dlp-dictionaries).

## August 12, 2022
### Feature Available
#### Renamed MCAS Unsanctioned Apps Custom URL Category
The custom URL category created for all the unsanctioned app URLs while integrating Zscaler service with Microsoft Cloud App Security (MCAS) is renamed from MCAS Unsanctioned Apps to MS Defender Unsanctioned Apps.
[See image.](#url-category-ms-defender-unsanctioned-apps)
To learn more, see [Integrating with Microsoft Cloud App Security](/zia/integrating-microsoft-cloud-app-security).
[]![Screenshot of URL Categories page within the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-MS-Defender-Custom-URL-Category.png)

## August 09, 2022
### Feature Available
#### Bookmarking in Cloud Browser Isolation
Users can now access bookmarks from their original browser while in an isolated session. The URL of the bookmarked web page appears as an isolation URL during the isolated session. If a user shares the bookmarked URL while in isolation, the URL sent redirects and appears as a typical, non-isolated URL.
To learn more, see [Bookmarking Web Pages in Cloud Browser Isolation](/zia/bookmarking-web-pages-cloud-browser-isolation).

### Feature Available
#### Read-Only Mode In Isolation
Read-only mode in isolation is a new setting admins can enable per isolation profile in their organization.
This setting restricts the use of keystrokes for a user during isolation. Isolation profiles with this setting enabled cannot enter text anywhere on the page, paste copied text into text fields, or use virtual keyboards to insert text.
The user can still navigate within an isolated web page using other command keys (`Enter`, `Escape`, and `the arrow keys`).
[See image.](#restrict-keystrokes)
To learn more, see [Read-Only Mode In Cloud Browser Isolation](/zia/read-only-mode-cloud-browser-isolation).
[![Read-Only Isolation](/sites/default/files/downloads/zia/cloud-browser-isolation/bookmarking-web-pages-cloud-browser-isolation/Edit_ZIA_Profile_Read-Only-Isolation.jpg)
]

## July 14, 2022
### Feature Available
#### Printing Files from Isolation
Cloud Browser Isolation now allows you to print files that are rendered within an isolated browser in addition to printing entire web pages and inline content.
You can enable the Print function for users per [ZIA](/zia/editing-your-zia-isolation-profile) or [ZPA](/zia/editing-your-zpa-isolation-profile) isolation profile.
[See image.](#Print-inline-content-window)
To learn more, see [Using the Isolation Bar in Native Browser Experience](/zia/using-isolation-bar-native-browser-experience) and [Transferring and Viewing Files in Cloud Browser Isolation](/zia/transferring-and-viewing-files-cloud-browser-isolation).
[![Print window for files](/sites/default/files/downloads/zia/cloud-browser-isolation/transferring-and-viewing-files-cloud-browser-isolation/PDF_print-option.jpg)
]

### Feature Available
#### Right-Click Menu In Isolation Update
Cloud Browser Isolation has added the capability to print content by using the right-click menu.
[See image.](#Default-menu)
To learn more, see [Using the Right-Click Menu in Cloud Browser Isolation](/zia/using-right-click-menu-cloud-browser-isolation).
[![Default Menu: Reload, Print](/sites/default/files/downloads/zia/cloud-browser-isolation/using-right-click-menu-cloud-browser-isolation/Default-Menu_Print.jpg)
]

## June 24, 2022
### Feature Available
#### New Cloud Apps and Cloud Risk
New cloud apps have been added to the following cloud app categories for use in the Cloud App Control policy:
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
Risk attribute database has been expanded with additional attributes, such as data purge, data retention, encryption support, and other definitions.
To learn more, see [About Cloud App Categories](/zia/about-cloud-app-categories) and [About Cloud Application Risk Profile](zia/about-cloud-application-risk-profile).

### Feature Available
#### SaaS Security API
The following enhancements are now available for SaaS Security API.
SaaS Application Tenant Onboarding
You can now discover, allow, and block third-party SaaS applications authenticated via a corporate Google account in the ZIA Admin Portal after adding Google Workspace Marketplace as a tenant. You can see general information about each tenant, such as the authorization status and configured policies.
To learn more, see [About SaaS Application Tenants](/zia/about-saas-application-tenants), [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants), and [SaaS Application Validation Error Codes](/zia/saas-application-validation-error-codes).
Third-Party Applications Report
The Third-Party Applications Report displays all the third-party applications that employees log in to using their corporate Google Workspace account. It shows you the date they were discovered, how many employees are using them, the state of an application, and more.
[See image.](#third-party)
[]![Third-Party Application Report page](/sites/default/files/downloads/ZIA-6.1r-Third-Party-Apps-page.png)
To learn more, see [Third-Party Applications Report](/zia/third-party-applications-report).

### Feature Available
#### Security Alerts
The new security alerts within the ZIA Admin Portal provide a comprehensive solution to view, manage, create, and adjust the alert rules. It provides high level statistics of each event type and severity. It is a centralized console to view and manage all alerts within the existing tenants. You can configure various events under Alerts. Alerts are classified into Security alerts and User Behavior alerts. The Security alerts span detection across advanced threat protection and malware. The User Behavior alerts span detection across access, data, and privileged activity. Additionally, upon triggering suspicious events or behaviors, risk can be reduced either by logging the user out, or by forcing the user for Multi-factor Authentication (MFA) or re-authentication.
[See image for Alert Rules.](#alert-rules)
[See image for Add Alert Rule.](#add-alert-rule)
To learn more, see [About Security Alerts](/zia/about-security-alerts) and [About Webhooks](/zia/about-webhooks).
[]![Screenshot of ZIA Alert Rules](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Alert-Rules.png)
![Screenshot of Add Alert Rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Add-Alert-Rule.png)
[]

## June 03, 2022
### Feature Available
#### Deprecation of Carbon Black Sandbox Integration
Zscaler no longer supports the integration of ZIA Sandbox with Carbon Black Endpoint Standard (formerly CB Defense) and Carbon Black Enterprise EDR (formerly CB ThreatHunter). Carbon Black recently deprecated the APIs that are used by Zscaler for this integration. As a result, ZIA Sandbox can no longer initiate API calls to Carbon Black to fetch telemetry. Nor can Zscaler, optionally, network-contain the impacted host.
To learn more, see the [Zscaler and Carbon Black Deployment Guide](/zscaler-technology-partners/zscaler-and-vmware-carbon-black-deployment-guide).

### Feature Available
#### DLP Support for Spanish Names and Canadian Names
There are two new predefined DLP dictionaries:
- Names (Canada): This dictionary detects names from Canada.
- Names (Spain): This dictionary detects names from Spain.
To learn more, see [Editing Predefined DLP Dictionaries](/zia/editing-predefined-dlp-dictionaries).

### Feature Available
#### Support for Client Authentication by ICAP and Zscaler Incident Receivers
ICAP and Zscaler Incident receivers can be configured to support client authentication. Mutual Transport Layer Security (MTLS) Certificate Authority (CA) Certificates have been provided for both the ICAP and Zscaler Incident receivers. For ICAP receivers, you can now download the MTLS CA Certificate from the ICAP Receivers page (Administration > ICAP Receivers) or the ICAP Setting page (Administration > DLP Incident Receiver) and install it in the ICAP receiver stunnel configuration. For Zscaler Incident receivers, the certificate can be used by enabling the icaps-mtls-enabled parameter for the Zscaler Incident receiver.
To learn more, see [About ICAP Receivers for DLP](/zia/about-icap-receivers-dlp), [About ICAP Receivers](/zia/about-icap-receivers), [Configuring the Zscaler Incident Receiver](/zia/configuring-zscaler-incident-receiver), and [Configuring the ICAP Server with the Mutual Transport Layer Security (MTLS) CA Certificate](/zia/configuring-icap-server-mutual-transport-layer-security-mtls-certificate).

### Feature Available
#### Updates to SaaS Security API Control Policies
You can now configure the quarantine malware action for the following applications under the Malware Detection Rule for the SaaS Security API Control policies:
- Salesforce (CRM Application)
[See Image](#Salesforce-API-Control-Policies)
- ServiceNow (ITSM Application)
[See image](#ServiceNow-API-Control-Policies)
To learn more, see [Configuring the SaaS Security API Malware Detection Policy](/zia/configuring-saas-security-api-malware-detection-policy).
[![The quarantine malware action for salesforce under malware detection rule.](/sites/default/files/downloads/zscaler-tech-pubs-style-guide/draft-articles/configuring-saas-security-api-scan-schedules-draft/Quarantine-Action-Salesforce.png)
]
[![The quarantine malware action for servicenow under malware detection rule.](/sites/default/files/downloads/zscaler-tech-pubs-style-guide/draft-articles/configuring-saas-security-api-scan-schedules-draft/Quarantine-Action-ServiceNow.png)
]

## May 27, 2022
### Feature Available
#### Printing Inline Content from Isolation
Cloud Browser Isolation now allows you to print inline content from within an isolated browser. In addition to printing entire web pages, isolation provides the option to choose specific content from a web page to print.
You can enable the Print function for users per [ZIA](/zia/editing-your-zia-isolation-profile) or [ZPA](/zia/editing-your-zpa-isolation-profile) isolation profile.
[See image.](#Print-inline-content-window)
To learn more, see [Using the Isolation Bar in Native Browser Experience](/zia/using-isolation-bar-native-browser-experience) and [Transferring and Viewing Files in Cloud Browser Isolation](/zia/transferring-and-viewing-files-cloud-browser-isolation).
[![Print window for inline content](/sites/default/files/downloads/zia/cloud-browser-isolation/transferring-and-viewing-files-cloud-browser-isolation/Print-Inline-Content_isolation-browser-Print-window.jpg)
]

### Feature Available
#### Using Search in Cloud Browser Isolation
Cloud Browser Isolation has created a search function to find text on web pages in isolated browsers. The Search function in Cloud Browser Isolation replicates a typical find-in-page experience for users. It allows you to search for text within a web page, and scroll through all possible results.
[See image.](#Search)
To learn more, see [Using Search in Cloud Browser Isolation](/zia/using-search-cloud-browser-isolation) and [Using the Isolation Bar in Native Browser Experience](/zia/using-isolation-bar-native-browser-experience).
[![Blank search bar](/sites/default/files/downloads/zscaler-tech-pubs-style-guide/draft-articles/using-isolation-bar-native-browser-experience-draft-print-b/Search-bar_isolation-browser_blank.jpg)
]

## April 21, 2022
### Feature Available
#### Printing Web Pages In Isolation
Cloud Browser Isolation has enabled the ability to print web pages from an isolated browser. You can enable the Print function for users per [ZIA](/zia/editing-your-zia-isolation-profile) or [ZPA](/zia/editing-your-zpa-isolation-profile) isolation profile.
[See image.](#print)
To learn more, see [Using the Isolation Bar in Native Browser Experience](/zia/using-isolation-bar-native-browser-experience) and [Transferring and Viewing Files in Cloud Browser Isolation](/zia/transferring-and-viewing-files-cloud-browser-isolation).
[![Print button in isolated browser](/sites/default/files/downloads/zia/cloud-browser-isolation/transferring-and-viewing-files-cloud-browser-isolation/isolation-bar_Print-squircle.png)
]

## April 12, 2022
### Feature Available
#### Default Isolation Profiles for Cloud Browser Isolation
A default isolation profile is now created for any organization using Cloud Browser Isolation. This allows a quick setup for your organization without manually creating the first isolation profile needed to [configure browser isolation](/zia/configuring-browser-isolation).
Organizations already using Cloud Browser Isolation now also see a default isolation profile in their list of profiles in the Cloud Browser Isolation Portal. If your organization uses both [ZIA](/zia/about-cloud-browser-isolation) and [ZPA](/zpa/about-isolation-policy), there is a default isolation profile for each, which can be used in [ZIA](/zia/configuring-browser-isolation) or [ZPA](/zpa/configuring-isolation-policies) isolation policies.
All details can be changed by admins, but these default profiles cannot be deleted.
To learn more, see [Default Isolation Profiles in Cloud Browser Isolation](/zia/default-isolation-profiles-in-Cloud-Browser-Isolation).

## April 08, 2022
### Feature Available
#### Enhancement to Microsoft Login Services in Tenant Profiles
The following enhancements were made to the Administration > Tenant Profiles > Add Tenant Profile window for the Microsoft Login Services cloud application:
- A version toggle was added. This enables you to create the following tenant profile types for Microsoft Login Services:
- Version 1: This profile type is the same as the existing tenant profile of Microsoft Login Services.
- Version 2: This profile type consists only the Tenant Directory Id: Policy Id (e.g., f4c77d8d-6bb8-41a2-a3c9-69dd3edaa158:quadsj) attribute.
- The Office 365 Tenants field was renamed to Microsoft 365 Tenants or Tenant IDs. You can now add tenant names or tenant IDs (e.g., corp1.safemarch.com or 784b1673-628c-56e3-c3b2-5d2f0d59524m) to this field.
[See image.](#MLS-version-1-2)
To learn more, see [Adding Tenant Profiles](/zia/adding-tenant-profiles#microsoft-login-services).
[]![Screenshot of ZIA Tenant Profiles Microsoft Login Services Version 1](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Tenant-Profiles-MLS-Version-1.png)
![Screenshot of ZIA Tenant Profiles Microsoft Login Services Version 2](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Tenant-Profiles-MLS-Version-2.png)

### Feature Available
#### Enhancement to the DNS Configuration Criteria
The Requested Domain/Resolved IP Categories field is split into two separate fields, Requested Categories and Resolved Categories, in the Policy > DNS Control > Add DNS Filtering Rule window.
[See image.](#dns-config)
To learn more, see [Configuring the DNS Control Policy](/zia/configuring-dns-control-policy).
This enhancement introduces the following updates to the DNS Insights Logs and the DNS Overview pages:
- The column and filter Domain Category is replaced by Request Categories in the DNS Insights Logs page.
- A new column and filter, Response Categories, is added to the DNS Insights Logs page.
[See image.](#dns-logs)
- The widgets** **Top IP Domain Categories and Top Blocked IP Domain Categories are replaced by Top Request Categories and Top Blocked Request Categories in the DNS Overview page.
- Two new widgets, Top Response Categories and Top Blocked Response Categories, are added to the DNS Overview page.
[See image.](#dns-overview)
To learn more, see [About Dashboards](/zia/about-dashboards#DNS-overview), [DNS Insights Logs: Columns](/zia/dns-insights-logs-columns), and [DNS Insights Logs: Filters](/zia/dns-insights-logs-filters).
[]![Screenshot of DNS Overview page](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/third-party-applications-report/ZIA-6.1r-DNS-overview.png)
[]![Screenshot of the DNS Application tab of the DNS Filtering Rule window](/sites/default/files/downloads/zia-6.1r-dns-configuring.png)
[![Screenshot of the DNS Insights Logs ](/sites/default/files/downloads/zia-6.1r-dns-insights-logs.png)
]

### Feature Available
#### Enhancements to DLP Advanced Settings
With the Cloud Apps & URL Exceptions for DLP list, you can exempt custom URL categories and URL encoded data from DLP evaluation.
[See image.](#Image-DLP-Advanced-Settings-New-Fields)
To learn more, see [Exempting Cloud Apps and URLs from DLP Evaluation](/zia/exempting-cloud-apps-and-urls-dlp-evaluation).
[]![The Exempted User-Defined URL Categories and Exempt URL Encoded Data fields for the ZIA DLP Advanced Settings page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-DLP-Advanced-Settings-New-Fields.png)

### Feature Available
#### Update to the Data Loss Prevention Policy
When configuring Data Loss Prevention (DLP) policy rules, you can choose to exclude or include certain users, groups, or departments. In other words, you can specify whether the rule applies or doesn’t apply to selected users, groups, or departments.
[See image.](#Image-DLP-Rule-Exclude-Include)
The DLP endpoints within the cloud service API have also been updated. You can now exclude certain users, groups, or departments from a policy rule via API request.
To learn more, see [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection), [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection), and the [API Reference](/zia/about-api).
[]![The Add DLP Rule window with the Exclude and Include options for Users, Groups, and Departments](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-DLP-Rule-Include-Exclude.png)

## April 06, 2022
### Feature Available
#### Right-Click Menu In Isolation
Cloud Browser Isolation now provides contextual right-click menus on isolated browser web pages. This allows users to perform typical functions from isolated web pages as they would in a non-isolated browser. The options for the right-click menu change depending on where you right-click on the web page.
[See image.](#screenshot)
To learn more, see [Using the Right-Click Menu in Cloud Browser Isolation](/zia/using-right-click-menu-cloud-browser-isolation).
[![Cloud Browser Isolation Right-Click Menu options](/sites/default/files/downloads/zia/cloud-browser-isolation/using-right-click-menu-in-cloud-browser-isolation/Anchor-Image-Menu_0.png)
]

## March 25, 2022
### Feature Available
#### SaaS Security API
The following enhancements are available for SaaS Security API.
To enable Google Cloud Platform and Microsoft Azure for your organization, contact your Zscaler Account Team.
Updates to SaaS Application Tenant Onboarding
You can authorize Google Cloud Platform and Microsoft Azure as SaaS applications with Zscaler by adding them as tenants. You can see general information such as the authorization status and configured policies.
To learn more, see [About SaaS Application Tenants](/zia/about-saas-application-tenants), [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants), and [SaaS Application Validation Error Codes](/zia/saas-application-validation-error-codes).
Updates to SaaS Security API Control Policies & Scan Configuration
You can configure the SaaS Security API Control policies and scan schedules for Google Cloud Platform and Microsoft Azure. Both applications are public cloud storage applications.
To learn more, see [Configuring the SaaS Security API Control Policy](/zia/configuring-saas-security-api-control-policy).
Updates to the SaaS Assets Summary Report
You can view Google Cloud Platform and Microsoft Azure (public cloud storage applications) in the SaaS Assets Summary Report.
To learn more, see [SaaS Assets Summary Report](/zia/saas-assets-summary-report).
Updates to the SaaS Assets Report
You can view Google Cloud Platform and Microsoft Azure (public cloud storage applications) in the SaaS Assets Report.
To learn more, see [SaaS Assets Report](/zia/saas-assets-report) and [SaaS Assets Report: Assets with Incidents](/zia/saas-assets-report-assets-incidents).
Updates to SaaS Security Insights & Insights Logs
You can view Google Cloud Platform and Microsoft Azure (public cloud storage applications) in SaaS Security Insights and Insights Logs.
To learn more, see [SaaS Security Insights](/zia/saas-security-insights) and [SaaS Security Insights Logs](/zia/saas-security-insights-logs).

## March 18, 2022
### Feature Available
#### Enhancement to the Newly Registered Domains URL Category
The URL category, Newly Registered Domains, is now known as Newly Registered and Observed Domains. This category comprises domains that were created in the last 30 days, and it also includes the newly observed domains that we encounter for the first time. These domains are often considered unsafe until they are well known or categorized.
[See image.](#URL-category-NROD)
As part of this enhancement, the Enable Newly Registered Domain Lookup option on the Policy > Cloud App & Control > Advanced Policy Settings tab is renamed to Enable Suspicious New Domains Lookup. This option quickly identifies the newly registered and observed domains and improves the overall security posture.
[See image.](#enable-suspicious-new-domains-lookup)
To learn more, see [About URL Categories](/zia/about-url-categories#Surfing) and [Configuring Advanced URL Policy Settings](/zia/configuring-advanced-url-policy-settings#DomainLookup).
[]![Screenshot of the Edit URL Category Window.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-6.2-Edit-URL-Categories.png)
[]![Screenshot of the Advanced Policy Settings tab.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-6.2-Advanced-Policy-Settings.png)

## February 25, 2022
### Feature Available
#### Update to Cloud Service API
The `getVpnEndpoints` endpoint was updated to provide the data center name (`dcName`) in the response. Now, city and country information for virtual IP addresses (VIPs) is more accurate.
To learn more, see [SD-WAN API Integration for IPSec VPN Tunnel Provisioning](/zia/sd-wan-api-integration).

### Feature Available
#### Zscaler Cloud Performance Test Tool
Zscaler introduces a new Cloud Network Performance Test tool that collects performance troubleshooting information for end users when connecting to the internet through the Zscaler Internet Access (ZIA) cloud service.
This tool is hosted only on HTTP.
To learn more, see [Using the Zscaler Cloud Performance Test Tool](/zia/using-zscaler-cloud-performance-test-tool).

## February 18, 2022
### Feature Available
#### Enhancement to URL Categories
You can now add IP address ranges to predefined and custom URL categories. The following enhancements were made to the URL Categories page (Administration > URL Categories):
- The URL Categories page displays the number of custom IP ranges and the number of IP ranges retaining parent category for a category.
- Added the following fields to the Add/Edit URL Category window (Administration > URL Categories > Add/Edit URL Category):
- Custom IP Ranges
- IP Ranges Retaining Parent Category
[See image.](#url-categories)
The URL Categories endpoints within the cloud service API have also been updated. So you can now read, create, and update IP address ranges for predefined and custom URL categories via API requests.
To learn more, see [About URL Categories](/zia/about-url-categories), [Configuring Custom URL Categories](/zia/adding-custom-url-categories), and the [API Reference](/zia/about-api).
[]![Screenshot of the URL Categories page with IP Ranges](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-URL-Categories.png)
![Screenshot of the Add URL Category Window with IP Ranges.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Add-URL-Category.png)

### Feature Available
#### Update to Cloud Service API: New Subcloud Parameter
You can now filter by subcloud when retrieving the list of virtual IP addresses (VIPs) for your Zscaler cloud. The following cloud service API endpoints now support `subcloud` as a query parameter:
- `GET /vips`
- `GET /vips/groupByDatacenter`
- `GET /vips/recommendedList`
To learn more about each endpoint, see the [API Reference](/zia/about-api). To learn more about subclouds, see [Understanding Subclouds](/zia/understanding-subclouds).

## February 04, 2022
### Feature Available
#### New Macros Available for DLP Notification Templates
Zscaler has added 3 new inline web DLP macros for your DLP Notification Templates:
- `${ACTION}`: This macro specifies the action of the triggered DLP rule (i.e., whether the transaction was allowed or blocked).
- `${TOTAL_TRIGGERED_DICTIONARIES}`: This macro specifies the total number of DLP dictionaries triggered across all DLP rules.
- `${TOTAL_TRIGGERED_ENGINES}`: This macro specifies the total number of DLP engines triggered across all DLP rules.
To learn more, see [Configuring DLP Notification Templates](/zia/configuring-dlp-notification-templates).

## January 31, 2022
### Feature Available
#### User Experience Modes in Cloud Browser Isolation
Cloud Browser Isolation now allows admins to select an isolation browser experience for their users. The two options are Native Browser Experience and Browser-in-Browser Experience.
Native Browser Experience presents the isolated session to a user as if they are using a regular browser window. When this mode is enabled, the Isolation Menu controls are accessible, but hidden from view by default. To learn more, see [User Experience Modes In Cloud Browser Isolation](/zia/user-experience-modes-cloud-browser-isolation) and [Using the Isolation Bar in Native Browser Experience](/zia/using-isolation-bar-native-browser-experience).
Browser-in-Browser Experience displays both the isolated session window and the original browser window that contains it. When this mode is enabled, all Isolation Menu controls are shown by default.
Admins can change the isolation experience mode for a user profile at any time. To learn more, see [Editing Your ZIA Isolation Profile](/zia/editing-your-zia-isolation-profile) and [Editing Your ZPA Isolation Profile](/zia/editing-your-zpa-isolation-profile).
[See image.](#Edit-Isolation-UX)
[![Edit Isolation User Experience](/sites/default/files/downloads/zia/cloud-browser-isolation/editing-your-zia-isolation-profile/Edit-ZIA-Profile_Native-Browser-Experience.png)
]

## January 28, 2022
### Feature Available
#### Microsoft Login Services Enhancement in Tenant Profiles
The Allow Personal Office 365 Domains field is now added to the Add Tenant Profile page (Administration > Tenant Profiles > Add Tenant Profile) for the Microsoft Login Services cloud application. The field allows users to access the personal Office 365 domains in the tenant profile based on the selection.
[See image.](#microsoft-tenant-profile)
To learn more, see [Adding Tenant Profiles](/zia/adding-tenant-profiles).
[]![Screenshot of the Add Tenant Profile Window with Microsoft.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Microsoft-Add-Tenant-Profile.png)

### Feature Available
#### OCR and ML-Based Image Recognition for Data Loss Prevention
Zscaler now supports ML-based image recognition, such as passports and driver's license as well as optical character recognition (OCR) for Data Loss Prevention (DLP) policy rules with content inspection. This enhancement allows Zscaler’s DLP engines to scan images in files.
[See image.](#DLP-OCR-image)
To learn more, see [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection).
[]![The OCR option for the Zscaler Data Loss Prevention policy rules with content inspection](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-Add-DLP-Rule-OCR.png)

## January 21, 2022
### Feature Available
#### Obfuscate Device Information
You can choose whether the device information (i.e., device name, device hostname, and device owner) should be visible or obfuscated for the admins and Zscaler Support on the Dashboard and Analytics page of the ZIA Admin Portal. By default, the device information is visible.
For admins, you can configure this setting while adding or editing an administrator role under Administration > Role Management.
[See image.](#add-admin)
[]![Device Information option in the Add Administrator Role window](/sites/default/files/downloads/ZIA-6.1r-Device-Information.png)
For Zscaler Support, you can configure this while enabling remote assistance under Help > Remote Assistance.
[See image.](#remote)
[]![Device Information option in the Remote Assistance window](/sites/default/files/downloads/zia/troubleshooting/enabling-remote-assistance/ZIA-6.1r-Remote-Assistance-Device-Info%20(1).png)
To learn more, see [Adding Admin Roles](/adding-admin-roles), [Obfuscating Device Information](/zia/obfuscating-device-information-admins), and [Enabling Remote Assistance](/enabling-remote-assistance).

### Feature Available
#### Proximity Length
For applicable predefined DLP dictionaries, you can now configure proximity lengths. This allows you to define how close a high confidence phrase must be to an instance of the pattern (that the dictionary detects) to count as a match.
[See image.](#proximity-length)
To learn more, see [Editing Predefined DLP Dictionaries](/zia/editing-predefined-dlp-dictionaries).
[]![The Proximity Length field for Zscaler Predefined DLP Dictionaries](/sites/default/files/downloads/zia/policies/data-loss-prevention/editing-predefined-dlp-dictionaries/ZIA-Edit_Predefined-DLP-Dictionary-Phrases.png)

### Feature Available
#### Update to Cloud Service API: New DLP-related Endpoints
The cloud service API now includes the following for endpoints in order to full support Data Loss Prevention (DLP) rule creation and updates:
- `GET /deviceGroups`
- `GET /deviceGroups/devices`
- `GET /deviceGroups/devices/lite`
- `GET /dlpEngines`
- `GET /dlpEngines/{dlpEngineId}`
- `GET /dlpEngines/lite`
- `GET /dlpExactDataMatchSchemas`
- `GET /dlpExactDataMatchSchemas/lite`
- `GET /dlpNotificationTemplates`
- `GET /dlpNotificationTemplates/lite`
- `GET /dlpNotificationTemplates/{templateId}`
- `POST /dlpNotificationTemplates`
- `PUT /dlpNotificationTemplates/{templateId}`
- `DELETE /dlpNotificationTemplates/{templateId}`
- `GET /icapServers`
- `GET /icapServers/lite`
- `GET /icapServers/{icapServerId}`
- `GET /idmprofile`
- `GET /idmprofile/lite`
- `GET /idmprofile/{profileId}`
- `GET /incidentReceiverServers`
- `GET /incidentReceiverServers/lite`
- `GET /incidentReceiverServers/{incidentReceiverServerId}`
- `GET /ruleLabels`
- `GET /ruleLabels/{ruleLabelId}`
- `POST /ruleLabels`
- `PUT /ruleLabels/{ruleLabelId}`
- `DELETE /ruleLabels/{ruleLabelId}`
- `GET /users/auditors`
- `GET /webDlpRules`
- `GET /webDlpRules/{ruleId}`
- `GET /webDlpRules/lite`
- `POST /webDlpRules`
- `PUT /webDlpRules/{ruleId}`
- `DELETE /webDlpRules/{ruleId}`
The `/dlpDictionaries` endpoints were also updated to support Exact Data Match (EDM) and Indexed Document Match (IDM) dictionary creation and updates.
To learn more about each endpoint, see the [API Reference](/zia/api/) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection was also updated to include new and updated resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

### Feature Available
#### Update to Cloud Service API: New Virtual IP Address Endpoint
A new endpoint, `GET /vips/groupByDatacenter`, was added to the cloud service API. When called, this endpoint returns the same set of virtual IP addresses (VIPs) as `GET /vips/recommendedList`, but grouped by the data center name (`datacenter`).
- [See example response](#groupByDatacenter_Example)
[][
{
"datacenter": "BOM4",
"latitude": 20,
"longitude": 72,
"city": "Mumbai",
"countryCode": "IN",
"region": "Asia",
"greVips": [
{
"id": 23211,
"virtualIp": "129.12.15.65"
},
{
"id": 23212,
"virtualIp": "129.12.15.66"
}
]
},
{
"datacenter": "BOM6",
...
...
To learn more, see the [API Reference](/zia/about-api) and [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

## January 07, 2022
### Feature Available
####  SaaS Security Report Enhancements
Following are the updates to the Shadow IT Reports that you access by navigating to Analytics > SaaS Security Report > Applications:
- The new Filter icon replaces the Filter section.
[See image.](#filter-option)
- The Cloud Applications table includes the following new columns:
- Upload Bytes
- Download Bytes
- Users
[See image.](#column-options)
- The application information page that opens when you click on an application:
- Displays the filter range and last seen date.
- Displays the upload bytes, download bytes, total users, and the sanctioned state of the application.
- Displays the description, activities supported, and the application's category information under the Basic Information section.
- Includes a new Users table that displays user-specific data for an application.
[See image.](#app-info-page)
To learn more, see [Shadow IT Report](/zia/shadow-it-report).
[]![Updates to the Application Information Page](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/shadow-it-report/ZIA-6.1r-Application-Information-Page-Changes_0.png)
[]![Filter option for the Reports](/sites/default/files/downloads/ZIA-6.1r-Filtering-option.png)
[]![Column options in the Cloud Applications table](/sites/default/files/downloads/ZIA-6.1r-columns.png)

### Feature Available
#### New Macros Available for DLP Notification Templates
Zscaler has added 5 new inline web DLP macros for your DLP Notification Templates:
- ${FILETYPE}: This macro specifies the file type of the file that triggered the DLP rule.
- ${DICTIONARIES_IN_RULE}: This macro lists the DLP dictionaries associated with the triggered DLP rule.
- ${DICTIONARIES_NOT_IN_RULE}: This macro lists the triggered DLP dictionaries that aren’t associated with the triggered DLP rule, but are associated with other DLP rules.
- ${ENGINES_IN_RULE}: This macro lists the DLP engines associated with the triggered DLP rule.
- ${ENGINES_NOT_IN_RULE}: This macro lists the triggered DLP engines that aren’t associated with the triggered DLP rule, but are associated with other DLP rules.
Additionally, the Subject line for notifications will use the ${RULENAME} macro instead of the ${ENGINE} macro by default.

### Feature Available
#### Support for Webex Login Services in Tenant Profiles
The Tenant Profiles feature now supports Webex Login Services. This allows you to provide access only to your organizations' Webex Teams and Meetings.
[See image.](#webex-tenant-profile)
To learn more, see [Adding Tenant Profiles](/zia/adding-tenant-profiles).
[]![Screenshot of the Add Tenant Profile Window with Webex.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2021/ZIA-6.1r-Webex-Add-Tenant-Profile.png)
