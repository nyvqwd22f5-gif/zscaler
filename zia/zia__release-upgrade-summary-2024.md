# Release Upgrade Summary (2024)
Source: https://help.zscaler.com/zia/release-upgrade-summary-2024

This article provides a summary of all new features and enhancements per Zscaler cloud for Zscaler Internet Access (ZIA). Zscaler will email a notification to your organization's registered support contacts approximately one week before your cloud is upgraded. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com).

**Clouds:** zscaler.net, zscalerone.net, zscalertwo.net, zscalerthree.net, zscloud.net, zscalerbeta.net
The following service updates were deployed to zscaler.net on

## December 20, 2024
### Feature Available
#### Optical Character Recognition Support for Outbound Email DLP
The Zscaler service supports optical character recognition (OCR) for Outbound Email DLP. You can enable OCR settings on the DLP Advanced Settings page in the ZIA Admin Portal (Administration > DLP Advanced Settings) for inline DLP, SaaS Security API, and Outbound Email DLP.
[See image.](#ocr-outbound-email-dlp-rn)
To learn more, see [Configuring DLP Advanced Settings](/zia/configuring-dlp-advanced-settings).
[]![Apply optical character recognition settings for DLP rules](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-OCR-support-for-Outbound-Email-DLP_RN.png)

## December 18, 2024
### Feature Available
#### Enhancement to Posture Page in Advanced SSPM
The Platforms filter is added to the Posture page. You can filter the controls displayed in the table by using this filter option.
To learn more, see [About Posture](/zia/about-posture).

### Feature Available
#### Enhancement to Users Page in 3rd-Party App Governance
The Findings and Findings Severity filters are added to the Users page. You can filter the users displayed in the table by using these filter options.
To learn more, see [About User Inventory](/zia/about-user-inventory).

### Feature Available
#### Expanded File Type Support for File Type Control
The File Type Control and Data Loss Prevention (DLP) policies now support the following file types:
- Microsoft Outlook Mac Data (.olm)
- Microsoft Publisher Files (.pub)
- Microsoft TNEF file (.tnef)
- LZH Archive (.lzh, .lha)
- CPIO File (.cpio)
- Binhex files (.hqx)
- QuarkXPress files (.qxd, .qxp)
- AutoCAD (.dxf)
- AutoCAD Drawing (.dwg)
- Domino Server Database (.dxl)
The File Type Control and DLP policies support new file types in the following categories:
- [Microsoft Office](#microsoft-1509286)
- [Archive](#archive-1509286)
- [Other Documents](#otherdocuments-1509286)
- [Database](#database-1509286)
To learn more, see [About File Type Control](/zia/about-file-type-control) and [About Data Loss Prevention](/zia/about-data-loss-prevention).
[]The Microsoft Office file types are available when creating the following polices in the Microsoft Office category:
- [File Type Control](#microsoft-ftc-1509286)
[]
- Microsoft Outlook Mac Data (.olm)
- Microsoft Publisher Files (.pub)
- Microsoft TNEF file (.tnef)
![microsoft-office-ftc-1509286.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/microsoft-office-ftc-1509286.png)
[]The Archive file types are available when creating the following polices in the Archive category:
- [File Type Control](#archive-filetypecontrol-1509286)
[]
- LZH Archive (.lzh, .lha)
- CPIO File (.cpio)
- ![archive-file-types-54191.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/archive-file-types-54191.png)
[]The Other Document file types are available when creating the following policies in Other Documents category:
- [File Type Control](#other-docs-ftc-1509286)
[]
- Binhex files (.hqx)
- QuarkXPress files (.qxd, .qxp)
- AutoCAD (.dxf)
- AutoCAD Drawing (.dwg)
![other-docs-without-content-matching-54191.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/other-docs-without-content-matching-54191.png)
[]The Database file types are available when creating the following policies in the Database category:
- [File Type Control](#database-ftc-1509286)
[]
- Domino Server Database files (.dxl)
![database-ftc-54191.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/database-ftc-54191.png)

### Feature Available
#### Expanded File Type Support for Sandbox
The Zscaler Sandbox supports additional file types:
- Microsoft Software Installer (msi)
- Windows Batch File (bat)
- Windows Script File (wsf)
[See image.](#file_type)
To learn more, see [About Sandbox](/zia/about-sandbox) and [Configuring the Sandbox Policy](/zia/configuring-sandbox-policy%20).
[]![Sandbox Rules, file types](/sites/default/files/downloads/zia/policies/sandbox/about-sandbox/Sandbox%20file%20types02.png)

### Feature Available
#### Support for Changing Control Severity in Advanced SSPM
You can change the control severity on the Posture page or the Control Panel header, specifying the severity level as per your organization's perspective. The defined control severity will override any future system recalculations. You can revert to the default severity.
To learn more, see [Updating the Control Severity](/zia/updating-control-severity).

## December 16, 2024
### Feature Available
#### Understanding Persistent State for Isolation in ZIA
Persistent State allows users to have isolation sessions automatically restored with current state data when they time out. Admins can allow this feature per user profile by enabling Cookie Persistence.
To learn more, see [Creating Isolation Profiles for ZIA](/isolation/creating-isolation-profiles-zia).

## December 13, 2024
### Feature Available
#### Added File Type Support for File Type Control & DLP
The File Type Control and Data Loss Prevention (DLP) policies now support the following file types:
- Microsoft Excel Add-On (.xla)
- Open Document Files (.odt)
- Public Key File (.pub)
- Binary Files (.bin)
The File Type Control and DLP policies are available in the following categories:
- [Microsoft Office](#microsoft-office-1510071)
- [Open Office Files](#open-office-1510071)
- [Other Documents](#other-documents-1510071)
To learn more, see [About File Type Control](/zia/about-file-type-control) and [About Data Loss Prevention](/zia/about-data-loss-prevention).
[]The following file types are available when creating the following policies in the Microsoft Office category:
- [File Type Control](#microsoft-office-ftc-1510071)
- [DLP without Content Inspection](#microsoft-office-without-CI-1510071)
[]
- Microsoft Excel Add-On (.xla)
![Add Microsoft Office File Types to File Type Control Rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/microsoft-office-ftc-55049.png)
[]
- Microsoft Excel Add-On (.xla)
![Add Microsoft Office File Types to DLP Rule without Content Inspection](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/microsoft-no-ci-55049.png)
[]The following file types are available when creating the following policies in Other Documents category:
- [File Type Control](#other-docs-ftc-1510071)
- [DLP - Rule without Content Inspection](#other-docs-without-CI-1510071)
[]
- Public Key File (.pub)
- Binary Files (.bin)
![Add Other Documents File Types to File Type Control Rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/other-docs-ftc-55049.png)
[]
- Public Key File (.pub)
- Binary Files (.bin)
![Add Other Documents File Types to DLP Rule without Content Inspection](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/other-docs-no-ci-55049.png)
[]The following file types are available when creating the following policies in Open Office category:
- [DLP without Content Inspection](#open-office-without-CI-1510071)
- [DLP with Content Inspection](#open-office-contentinspection-1510071)
[]
- Open Document Files (.odt)
![Add Open Office Documents File Types to DLP Rule without Content Inspection](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/open-office-no-ci-55049.png)
[]
- Open Document Files (.odt)
![Add Open Office Documents File Types to DLP Rule with Content Inspection](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/open-office-content-inspection-55049.png)

### Feature Available
#### Advanced SaaS Security Posture Management Support for ShareFile
You can configure Advanced SaaS Security Posture Management (SSPM) for ShareFile tenants. Select the SSPM Scan checkbox when onboarding a ShareFile tenant to enable the Advanced SSPM scan capability for the specific tenant. Existing users can also enable Advanced SSPM support by selecting the SSPM Scan checkbox under the onboarding section for the specific tenants and then validating and saving the changes.
[See image.](#servicenow-sspm-onboarding)
The SSPM Scan checkbox is enabled only when you have the Advanced SSPM enabled for your tenant.
To learn more, see [Understanding the SaaS Security Posture Management Policy](/zia/understanding-saas-security-posture-management-policy) and [Viewing and Managing the Supported SSPM Policies](/zia/viewing-and-managing-supported-sspm-policies).
[]![Select the required onboarding function to enable for the ShareFile tenant.](/sites/default/files/downloads/Adavanced%20SSPM-ShareFile.png)

### Feature Available
#### Advanced SaaS Security Posture Management Support for Slack
You can configure Advanced SaaS Security Posture Management (SSPM) for Slack tenants. Select the SSPM Scan checkbox when onboarding a Slack tenant to enable the Advanced SSPM scan capability for the specific tenant. Existing users can also enable Advanced SSPM support by selecting the SSPM Scan checkbox under the onboarding section for the specific tenants and then validating and saving the changes.
[See image.](#slack-sspm-onboarding)
The SSPM Scan checkbox is enabled only when you have the Advanced SSPM enabled for your tenant.
To learn more, see [Understanding the SaaS Security Posture Management Policy](/zia/understanding-saas-security-posture-management-policy) and [Viewing and Managing the Supported SSPM Policies](/zia/viewing-and-managing-supported-sspm-policies).
[]![Screenshot of Slack SaaS Application Onboarding](/sites/default/files/downloads/Adavanced%20SSPM-SlackNew.png)

### Feature Available
#### Advanced Sandbox Submission API Quota
With Advanced Sandbox, organizations have by default a quota of 100 API file submissions per day. If you are interested in raising the API file submission limit, contact your Zscaler Account Team or Zscaler Support.
To learn more, see [About Sandbox](/zia/about-sandbox), [Obtaining Sandbox Reports Using API](/zia/obtaining-sandbox-reports-using-api), and [Sandbox Submission API](/zia/sandbox-submission-api).

### Feature Available
#### Configure Atlassian Label for Data at Rest Scanning DLP Policy
You can now apply an Atlassian Label when configuring the Data at Rest Scanning DLP Policy in the Add DLP Rule window. This action is only applicable for Atlassian Confluence users. To access this feature, go to the Add DLP Rule window (Policy > Data at Rest Scanning) and choose an Atlassian tenant from the SaaS Applicant Tenant drop-down menu.
[See image.](#apply-atlassian-label-1509786)
To learn more, see [Configuring the Data at Rest Scanning DLP Policy](/zia/configuring-saas-security-api-dlp-policy).
[]![Choose an Atlassian tenant from the SAAS Applicant Tenant drop-down menu. ](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/apply-atlassian-label.png)

### Feature Available
#### Custom Bandwidth Classes Limits
You can add up to 245 custom bandwidth classes (Administration > Bandwidth Classes) for Cloud Applications in the ZIA Admin Portal.
To learn more, see [Adding Bandwidth Classes](/zia/adding-bandwidth-classes) and [Ranges & Limitations](/zia/ranges-limitations).

### Feature Available
#### DLP Support for New PII Dictionaries
The following are new predefined DLP dictionaries to detect personally identifiable information (PII):
- Addresses (Japan)
- First Names (Japan)
- Last Names (Japan)
- Full Names (Japan)
To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).

### Feature Available
#### DLP Support for United States Driver's Licenses
Driver's License (United States) predefined DLP dictionaries now support 2-letter state codes for all US states (e.g., WA for Washington or CA for California) as part of high confidence phrases.
[See image.](#2-letter-state-code-1510146)
To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).
[]![Add high confidence phrases including 2-letter state codes to a predefined DLP dictionary](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/2-letter-state-codes.png)

### Feature Available
#### Improvements to the Incident Receiver JSON Metadata File
To help improve incident management on the Zscaler Incident Receiver, the JSON file that contains Inline Web DLP policy scan metadata for policy violations has been updated with the following new fields:
- `fileSize`: The size of the file that violated the DLP policy
- `documentType`: The document type (i.e., Corporate Finance, Insurance, etc.) of the file that violated the DLP policy
To learn more and to download sample JSON files, see [Configuring the Zscaler Incident Receiver for On-Premises VMs](/zia/configuring-zscaler-incident-receiver), [Configuring the Zscaler Incident Receiver for Amazon Web Services EC2 VMs](/zia/configuring-zscaler-incident-receiver-for-ec2), and [Configuring the Zscaler Incident Receiver for Azure VMs](/zia/configuring-zscaler-incident-receiver-azure-vms).

### Feature Available
#### Increase in the Number of Custom Domains Allowed per Domain Profile
The number of custom domains allowed per domain profile has been increased from 32 to 1,024.
To learn more, see [Ranges & Limitations](/zia/ranges-limitations) and [About Email Profiles](/zia/about-email-profiles).

### Feature Available
#### Instance Discovery Report
The Instance Discovery Report provides visibility about the different instances accessed by the users at the various levels of hierarchy, such as Organization, Project, and Resource Type for Google Cloud Platform (GCP).
The Instance Discovery Report includes the following enhancements:
-
A new page to monitor and view logs for the Instance Discovery Report (Analytics > Instance Discovery Report).
[See image.](#instance-discovery-report)
-
A drill down from the Instance Discovery Report to monitor and view logs for the Resource Discovery Report (Analytics > Instance Discovery Report > Resource Discovery Report).
[See image.](#resource_discovery)
To learn more, see [About the Instance Discovery Report](/zia/about-instance-discovery-report) and [Viewing the Resource Discovery Report](/zia/viewing-resource-discovery-report).
Instance Discovery Report Logs
The following enhancements are made to the Web Insights Logs:
- You can filter and view logs for the discovered instances of the cloud applications. The following columns are added to Web Insights Logs (Analytics > Insights > Web Insights):
- App Instance Level 1
- App Instance Level 2
- App Instance Level 3
- App instance Level 1 Type
- App instance Level 2 Type
- App instance Level 3 Type
- The following filters are added to Web Insights Logs (Analytics > Insights > Web Insights):
- App Instance Level 1
- App Instance Level 2
- App Instance Level 3
To learn more, see [Web Insights Logs: Columns](/zia/web-insights-logs-columns) and[ Web Insights Logs: Filters](/zia/web-insights-logs-filters).
[]![This image shows the Instance Discovery Report page.](/sites/default/files/downloads/zia/dashboard-analytics/reports/about-instance-discovery-report/Instance_discovery_report_overview_RN.png)
![This image shows the Resource Discovery Report page](/sites/default/files/downloads/zia/dashboard-analytics/reports/about-resource-discovery-report/Resource_discovery_report_RN.png)
[]

### Feature Available
#### Outbound Email Data Loss Prevention for Gmail
You can use Zscaler Outbound Email Data Loss Prevention (DLP) policies with your Gmail server to prevent the exfiltration of sensitive data by enforcing policy rules on email content sent to external domains, including content in subject lines, body text, and attachments. As part of your larger DLP strategy, Zscaler Outbound Email DLP for Gmail lets you use the same DLP policy tools that you already use across other channels (i.e., Inline Web DLP, Endpoint DLP, and SaaS Security DLP), eliminating the need for different DLP point solutions and the operational overhead involved in maintaining those solutions. Additionally, you can monitor outbound email activity with dashboards and reports, and NSS feeds. This enhancement supplements existing Outbound Email DLP support for Microsoft Exchange.
As you set up Email tenants in the ZIA Admin Portal (Administration > Email Tenants), you now have the option to select a Gmail tenant.
[See image.](#gmail-tenant-option)
To learn more about setting up Zscaler Outbound Email DLP for your organization, see [Step-by-Step Configuration Guide for Zscaler Outbound Email DLP](/zia/step-step-configuration-guide-zscaler-outbound-email-dlp).
[]![Email Tenants page in ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Email-Tenants-Gmail-Option-RN.png)

### Feature Available
#### Site Review Enhancement
The Zscaler's Site Review shows the cloud application for the site that is looked up. As part of this change, the Cloud Application column is added to Step 2. Request Review on the Site Review page.
A cloud application is shown in the Cloud Application column only if it's associated with the looked-up URL.
[See image.](#site-review-cloud-app)
To learn more, see [Looking Up URLs in Site Review](/zia/using-site-review-lookup-urls).
[]![Screenshot of Zscaler Site Review Page with Cloud Application Column](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/Site-Review-Cloud-Application.png)

### Feature Available
#### Support for Email Subdomains
You can choose whether to include subdomains as part of your email domain profiles (e.g., blog.example.com is a subdomain of example.com). When you include subdomains (Administration > Email Profiles > Domain Profiles), the Zscaler service automatically evaluates subdomains as part of any policy rules associated with the affected email domain profile.
[See image.](#email-subdomains-new-knob-rn)
To learn more, see [Adding Email Profiles](/zia/adding-email-profiles).
[]![Configuring the Include Subdomains option for Domain Profiles in ZIA](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Email-Subdomains-Knob-RN.png)

### Feature Available
#### Update to Cloud Service API
The `GET /pacFiles` endpoint is updated with new request parameters such as `pageSize` and `page` to support pagination. The default value of `pageSize` is 100 and the request retrieves up to 100 PAC files at a time.
To learn more, see the [API Reference](/zia/about-api).

## December 06, 2024
### Feature Available
#### Cloud Applications Update in NSS
Zscaler has updated the names of select cloud applications. The updates synchronize the cloud application names across Web Insights and NSS and Cloud NSS web log feeds. To verify and address any impacts related to the updates, Zscaler recommends that admins review the following:
-
NSS and Cloud NSS web log feeds that use the Cloud Applications filter
[See image.](#img-to-where-cloud-apps-filter)
-
SIEM filters and any other SIEM post-processing logic based on the `%s{appname}` field in NSS and Cloud NSS web log feeds
[See image.](#img-appname-field)
To learn more about the updates and see the list of impacted cloud applications, refer to the [Trust Post](https://trust.zscaler.com/posts/20891).
To learn more about NSS and Cloud NSS web log feeds, filters, and fields, see [Adding NSS Feeds for Web Logs](/zia/adding-nss-feeds-web-logs#Twhere), [Adding Cloud NSS Feeds for Web Logs](/zia/adding-cloud-nss-feeds-web-logs#Twhere), and [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs).
[]![Cloud Applications filter in To Where section of Add NSS Feed configuration window](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/nss-feed-to-where-cloud-applications.png)
[]![Cloud applications field in the Feed Output Format for NSS feed for web logs](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/nss-feed-feed-output-format-appname.png)

### Feature Available
#### Update to Audit Logs
Audit logs include a new Trace ID value that is generated for transactions associated with ZIA API requests made through [Zscaler OneAPI](/oneapi/understanding-oneapi).
[See image.](#audit-logs-traceId)
To learn more, see [About Audit Logs](/zia/about-audit-logs).
The cloud service API was also updated to include a new `traceId` field in the `AuditLogEntryRequest` model used in the `/auditlogEntryReport` endpoint.
To learn more, see the [API Reference](/zia/about-api).
[]![ZIA Audit Logs showing Trace ID value for API transactions via OneAPI](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/trace-id-audit-logs.png)

### Feature Available
#### Update to Cloud Service API: End User Notification Endpoints
The cloud service API includes the following new endpoints to retrieve information about browser-based end user notifications (EUNs) and to update the EUN configuration:
- `GET /eun`
- `PUT /eun`
To learn more, see the [API Reference](/zia/about-api).
The Postman collection has also been updated to include the new resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

### Feature Available
#### Updates to Cloud Service API
The cloud service API includes the following new categories of endpoints to extend programmatic access to various ZIA features and functionalities:
- [Malware Protection Policy](#malware-protection-policy-api)
- [Advanced Threat Protection Policy](#advanced-threat-protection-policy-api)
- [File Type Control Policy](#filetype-rules-api)
- [Sandbox Policy](#sandbox-policy-api)
- [URL Filtering and Cloud App Control Settings](#url-cloud-app-policy-settings-api)
- [DNS Control Policy](#DNS-control-policy-api)
- [IPS Control Policy](#IPS-control-policy-api)
- [Cloud Applications](#cloud-applications-api)
- [Proxy Gateways](#proxy-gateways-api)
- [Authentication Settings](#auth-settings-api)
- [Advanced Settings](#advanced-settings-api)
- [Cloud Nanolog Streaming Service (NSS)](#cloud-nss-feeds-api)
- [Organization Details](#org-information-api)
- [Remote Assistance Support](#remote-assistance-api)
- [SSL Inspection Policy](#sslinspection-policy-api)
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection is also updated to include new and updated resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).
[]You can create, update, and delete DNS Control policy rules and retrieve information about the rules using the following endpoints:
- `GET /firewallDnsRules`
- `POST /firewallDnsRules`
- `GET /firewallDnsRules/{ruleId}`
- `PUT /firewallDnsRules/{ruleId}`
- `DELETE /firewallDnsRules/{ruleId}`
[]You can create, update, and delete IPS Control policy rules and retrieve information about the rules using the following endpoints:
- `GET /firewallIpsRules`
- `POST /firewallIpsRules`
- `GET /firewallIpsRules/{ruleId}`
- `PUT /firewallIpsRules/{ruleId}`
- `DELETE /firewallIpsRules/{ruleId}`
[]You can retrieve a list of cloud applications associated with Advanced Settings, Bandwidth Classes, DLP rules, Cloud App Control rules, File Type Control rules, and SSL Inspection rules using the following endpoints:
- `GET /cloudApplications/policy`
- `GET /cloudApplications/sslPolicy`
[]You can retrieve organization and Zscaler service subscription information using the following endpoints:
- `GET /orgInformation`
- `GET /orgInformation/lite`
- `GET /subscriptions`
[]You can retrieve information about proxy gateways using the following endpoints:
- `GET /proxyGateways`
- `GET /proxyGateways/lite`
[]You can retrieve your organization's default authentication settings information or update it using the following endpoints:
- `GET /authSettings`
- `GET /authSettings/lite`
- `PUT /authSettings`
[]You can create, update, and delete file type rules and retrieve information about the rules using the following endpoints:
- `GET /fileTypeRules`
- `GET /fileTypeRules/lite`
- `POST /fileTypeRules`
- `GET /fileTypeRules/{ruleId}`
- `PUT /fileTypeRules/{ruleId}`
- `DELETE /fileTypeRules/{ruleId}`
[]You can update Remote Assistance preferences and retrieve information about them using the following endpoints:
- `GET /remoteAssistance`
- `PUT /remoteAssistance`
[]You can create, update, and delete file type rules and retrieve information about the rules using the following endpoints:
- `GET /sandboxRules`
- `POST /sandboxRules`
- `GET /sandboxRules/{ruleId}`
- `PUT /sandboxRules/{ruleId}`
- `DELETE /sandboxRules/{ruleId}`
[]You can update the Malware Protection policy and retrieve information about the policy configurations using the following endpoints:
- `GET /cyberThreatProtection/atpMalwareInspection`
- `PUT /cyberThreatProtection/atpMalwareInspection`
- `GET /cyberThreatProtection/atpMalwareProtocols`
- `PUT /cyberThreatProtection/atpMalwareProtocols`
- `GET /cyberThreatProtection/malwareSettings`
- `PUT /cyberThreatProtection/malwareSettings`
- `GET /cyberThreatProtection/malwarePolicy`
- `PUT /cyberThreatProtection/malwarePolicy`
[]You can update the Advanced Threat Protection policy and retrieve information about the policy configurations using the following endpoints:
- `GET /cyberThreatProtection/advancedThreatSettings`
- `PUT /cyberThreatProtection/advancedThreatSettings`
- `GET /cyberThreatProtection/maliciousUrls`
- `PUT /cyberThreatProtection/maliciousUrls`
- `GET /cyberThreatProtection/securityExceptions`
- `PUT /cyberThreatProtection/securityExceptions`
[]You can update the advanced settings of URL Filtering and Cloud App Control policies and retrieve information about the settings using the following endpoints:
- `GET /advancedUrlFilterAndCloudAppSettings`
- `PUT /advancedUrlFilterAndCloudAppSettings`
[]You can update the advanced settings of cloud configuration and retrieve information about the settings using the following endpoints:
- `GET /advancedSettings`
- `PUT /advancedSettings`
[]You can add, update, validate, and delete cloud NSS feeds, retrieve information about the feeds, test connectivity, and get feed output format using the following endpoints:
- `GET /nssFeeds`
- `POST /nssFeeds`
- `GET /nssFeeds/{feedId}`
- `PUT /nssFeeds/{feedId}`
- `DELETE /nssFeeds/{feedId}`
- `GET /nssFeeds/feedOutputDefaults`
- `GET /nssFeeds/testConnectivity/{feedId}`
- `POST /nssFeeds/validateFeedFormat`
[]You can create, update, and delete SSL Inspection rules and retrieve information about the rules using the following endpoints:
- `GET /sslInspectionRules`
- `POST /sslInspectionRules`
- `GET /sslInspectionRules/{ruleId}`
- `PUT /sslInspectionRules/{ruleId}`
- `DELETE /sslInspectionRules/{ruleId}`

## December 05, 2024
### Feature Available
#### File Size Limit Increase in Isolation for PDFTron
The file size limit for viewing files in Isolation while using PDFTron is 100 MB. A strong internet connection is ideal for maximum rendering performance while using PDFTron. To learn more, see [Transferring & Viewing Files in Isolation](/isolation/transferring-and-viewing-files-isolation).

## December 04, 2024
### Feature Available
#### Update to DNS Gateways
DNS Gateways support a customized URL path for DNS servers that use the DNS over HTTP (DoH) protocol.
[See image.](#DNS-gateway-DoH-custom-URL-path)
To learn more, see [Adding DNS Gateways](/zia/adding-dns-gateways).
[]![DNS Gateway configuration page for DoH queries](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/DNS-gateway-DoH-custom-path-URL.png)

## December 02, 2024
### Feature Available
#### Enhancement to App Inventory in 3rd-Party App Governance
When searching for an app on the App Inventory page, you can use the filter to view search results from the inventory, 3rd-Party App Governance catalog, or both. By default, the search results from the inventory are displayed.
[See image.](#Inventory-Search-Filter)
To learn more, see [About the App Inventory.](/zia/about-app-inventory)
[]![Screenshot of Inventory Search Filter](/sites/default/files/downloads/zia/policies/data-loss-prevention/3rd-party-app-governance/using-3rd-party-app-governance/searching-apps/SearchBar_Inventory_New.png)

### Feature Available
#### Enhancements to Integrations Banner in 3rd-Party App Governance
The Integrations banner in 3rd-Party App Governance includes the following enhancements:
- When a single tenant or multiple tenants are onboarded, a pending icon appears next to the tenants and the relevant platform to indicate that the tenants are still being processed.
- An error icon appears next to the tenant and the relevant platform to indicate an error.
To learn more, see [About the 3rd-Party App Governance Dashboard](/zia/about-3rd-party-app-governance-dashboard#at-integrations).

### Feature Available
#### Support for Compliance in Advanced SSPM
Zscaler Advanced SaaS Security Posture Management (SSPM) enables you to monitor your Software as a Service (SaaS) applications’ security posture against various compliance frameworks such as GDPR, NIST, etc. On the Compliance page, you can view a complete mapping of controls within various compliance frameworks and verify whether they are enforced according to the security checks.
Contact Zscaler Support to configure the subscription for your tenant to include Advanced SSPM.
[See image.](#Compliance-Page)
To learn more, see [About Compliance](/zia/about-compliance).
[]![Screenshot of Compliance Page](/sites/default/files/downloads/CompliancePg_RN.png)

## November 20, 2024
### Feature Available
#### Enhancements to the Control Panel in Advanced SSPM
The Control Panel in Advanced SSPM includes the following enhancements:
- Information about the MITRE ATT&CK  tactic and techniques is added to the Remediation tab to help you understand the threat behavior and attack movement.
- The CSA STAR compliance framework is added to the Compliance tab.
To learn more, see [About the Control Panel](/zia/about-control-panel).

### Feature Available
#### GitHub in Tenant Profile
The Tenant Profiles feature is extended to the GitHub application. This allows you to provide access to specific enterprise slugs.
[See image.](#github-tenant-profile)
To learn more, see [Adding Tenant Profiles](/zia/adding-tenant-profiles).
[]![ZIA-Add-Tenant-Profile-GitHub-RN.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Add-Tenant-Profile-GitHub-RN.png)

## November 18, 2024
### Feature Available
#### Updated Executive Insights App
Zscaler's updated Executive Insights Mobile App aims to curate the most important and actionable data for CXOs to monitor, react, and collaborate on their digital transformation, equipping them with a modern, efficient, and frictionless experience. This app provides valuable insights into your enterprise security, risk, infrastructure, and digital experience on your mobile device. This app is supported on both Android and iOS devices.
[See image.](#new-exec-insights-app)
To learn more, see [Accessing and Using the Executive Insights App](/zia/accessing-and-using-executive-insights-app).
[]![Zscaler Executive Insights App's Welcome Screen](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/Zscaler-New-Executive-Insights-App_Welcome-Screen.png)

## November 15, 2024
### Feature Available
#### Improvements to the Incident Receiver JSON Metadata File for Endpoint DLP
To help improve incident management on the Zscaler Incident Receiver, the JSON file that contains Endpoint DLP policy scan metadata for policy violations has been updated with the new `department` field, which provides the department of the user whose file violated the DLP policy.
To learn more and to download sample JSON files, see [Configuring the Zscaler Incident Receiver for On-Premises VMs](/zia/configuring-zscaler-incident-receiver), [Configuring the Zscaler Incident Receiver for Amazon Web Services EC2 VMs](/zia/configuring-zscaler-incident-receiver-for-ec2), and [Configuring the Zscaler Incident Receiver for Azure VMs](/zia/configuring-zscaler-incident-receiver-azure-vms).

### Feature Available
#### Improvements to the Incident Receiver JSON Metadata File for Inline Web DLP
To help improve incident management on the Zscaler Incident Receiver, the JSON file that contains Inline Web DLP policy scan metadata for policy violations has been updated with the following new fields:
- `referrerUrl`: The URL from which the HTTP request originated for the file that violated the DLP policy
- `department`: The department of the user whose file violated the DLP policy
To learn more and to download sample JSON files, see [Configuring the Zscaler Incident Receiver for On-Premises VMs](/zia/configuring-zscaler-incident-receiver), [Configuring the Zscaler Incident Receiver for Amazon Web Services EC2 VMs](/zia/configuring-zscaler-incident-receiver-for-ec2), and [Configuring the Zscaler Incident Receiver for Azure VMs](/zia/configuring-zscaler-incident-receiver-azure-vms).

### Feature Available
#### Improvements to the Incident Receiver JSON Metadata File for Saas Security DLP
To help improve incident management on the Zscaler Incident Receiver, the JSON file that contains Saas Security DLP policy scan metadata for policy violations has been updated with the following new fields:
- For email and non-email policy violations:
- `fileModification`: The date and time (in GMT) of the most recent modification to the file that violated the DLP policy
- `collaborationScope`: The collaboration scope (i.e., External Collaborators, External Link, etc.) of the file that violated the DLP policy
- `department`: The department of the user whose file violated the DLP policy
- `numberOfCollaborators`: The number of internal collaborators on the file that violated the DLP policy
- `numberOfExternalCollaborators`: The number of external collaborators on the file that violated the DLP policy
- `numberOfRecipients`: The number of internal recipients on the file that violated the DLP policy
- `numberOfExternalRecipients`: The number of external recipients on the file that violated the DLP policy
- For non-email policy violations:
- `filePath`: The file path for the file that violated the DLP policy
- `fileSize`: The size of the file that violated the DLP policy
- `fileType`: The type of file that violated the DLP policy
- `documentType`: The document type (i.e., Corporate Finance, Insurance, etc.) of the file that violated the DLP policy
- For email policy violations (nested under the `attachments` heading):
- `fileType`: The file type of the attachment that violated the DLP policy
- `fileName`: The file name of the attachment that violated the DLP policy
- `fileSize`: The file size of the attachment that violated the DLP policy
- `documentType`: The document type (i.e., Corporate Finance, Insurance, etc.) of the attachment that violated the DLP policy
- `dlpMD5`: The MD5 value for the attachment that violated the DLP policy
To learn more and to download sample JSON files, see [Configuring the Zscaler Incident Receiver for On-Premises VMs](/zia/configuring-zscaler-incident-receiver), [Configuring the Zscaler Incident Receiver for Amazon Web Services EC2 VMs](/zia/configuring-zscaler-incident-receiver-for-ec2), and [Configuring the Zscaler Incident Receiver for Azure VMs](/zia/configuring-zscaler-incident-receiver-azure-vms).

### Feature Available
#### Support for ATP Notification Block for SSL Inspection
You can enable notifications for Advanced Threat Protection (ATP) blocked traffic. Enable Show Notification for ATP Blocks under Show Notifications for Blocked Traffic to send End User Notifications (EUN) for ATP blocks.
You can enable Show Notification for ATP Blocks from the Action section under Policy > SSL Inspection > Add SSL Inspection Rule. This field is visible only when you enable Show Notifications for Blocked Traffic.
[See image.](#add-ssl-rule-atp-block)
To learn more, see [Configuring SSL Inspection Policy](/zia/configuring-ssl-inspection-policy).
[]![The Add SSL Inspection Rule allows you to configure various SSL Inspection rules.](/sites/default/files/downloads/Add%20SSL%20Inspection%20Rule.png)

## November 08, 2024
### Feature Available
#### SaaS Security Data at Rest Scanning
Gen AI is added as a new SaaS application category for Data at Rest Scanning DLP and Malware Detection policies. You can configure tenants for ChatGPT, a Gen AI application.
[See image.](#add-tenant-chatgpt)
To learn more, see [About SaaS Application Tenants](/zia/about-saas-application-tenants) and [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
You can configure the application for the SaaS Security API Control policies and also view them on the following pages:
- [Saas Assets Report](/zia/saas-assets-report)
- [SaaS Assets Summary Report](/zia/saas-assets-summary-report)
- [SaaS Security Insights](/zia/saas-security-insights) and [Insights Logs](/zia/saas-security-insights-logs)
- [NSS Feeds](/zia/adding-nss-feeds-saas-security-logs) and [Cloud NSS Feeds for SaaS Security Logs](/zia/adding-cloud-nss-feeds-saas-security-logs)
To learn more, see [Understanding the Data at Rest Scanning Policy](/zia/configuring-saas-security-api-control-policy).
[]![The tenant onboarding page allows you to add tenants for each SaaS application.](/sites/default/files/downloads/zia/policies/saas-security-api/saas-security-api-policies/saas-security-api-control/configuring-saas-security-api-scan-schedules/SaaS%20Security%20Tenant%20Onboarding.png)

### Feature Available
#### Support for Dashboard and Insights Using Standard Firewall
Standard Firewall users can now view DNS dashboards, insights, and logs within the ZIA Admin Portal, eliminating the need for exporting to an external log collector or SIEM via NSS.
Standard Firewall supports the following functionalities for DNS dashboards, insights, and logs:
- Full logging (i.e., detailed logs) only for Block rules
-
Aggregated logs for Allow rules
Log aggregation happens approximately every 15 minutes.
Standard Firewall logs do not contain user information, network applications, IPS data, such as threat categories, and any other data associated with the Advanced Firewall functionality.
To learn more, see [Understanding Firewall Capabilities](/zia/understanding-firewall-capabilities).

## November 06, 2024
### Feature Available
#### Box Custom Connector
When onboarding Box as a SaaS application tenant (Administration > SaaS Application Tenants), you can configure a Custom SaaS Connector using a private key JSON file so that the Zscaler service can access the application.
A Zscaler-defined connector grants the Zscaler service full administrator privileges to the application; whereas, a custom connector grants only necessary permissions.
[See image.](#box_custom)
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
[]![Custom connector option](/sites/default/files/downloads/zia/test/Box-upload.png)

## November 05, 2024
### Feature Available
#### Enhancement to Integrations Banner in 3rd-Party App Governance
The Integrations banner is enhanced to display buttons for the currently integrated platforms. Each button consists of a drop-down menu that lists the related tenants. You can select multiple tenants at a time from multiple platforms.
To learn more, see[ About the 3rd-Party App Governance Dashboard](/zia/about-3rd-party-app-governance-dashboard#at-integrations).

### Feature Available
#### Enhancements to User Panel and Users Page in 3rd-Party App Governance
On the User Panel Findings tab, you can view and change the status of the findings. The findings include user findings from both 3rd-Party App Governance and Advanced SaaS Security Posture Management (SSPM). On the Users page, the User Findings column name in the Users table is changed to Findings.
To learn more, see [About User Inventory](/zia/about-user-inventory) and [About the User Panel](/zia/about-user-panel).

### Feature Available
#### Support for Tenant Filter in 3rd-Party App Governance
The Tenant filter is added to the App Inventory, Posture, and Users pages. You can filter the apps, controls, and users by tenants using this filter option.

## November 01, 2024
### Feature Available
#### Ability to Edit Admin Scope with ZIdentity
For ZIdentity-enabled tenants, an admin can edit the scopes of other admins from the Administrators page (Administration > Administrator Management > Administrators) in the ZIA Admin Portal.
To learn more, see [About Administrators](/zia/about-administrators).

### Feature Available
#### Added Context for DLP Triggers
You can now see an additional 15-byte prefix and suffix to the left and right of the DLP Trigger that provides more information about the DLP incident. The additional context can be seen in the Incident Receiver, Zscaler Workflow Automation, and Email Notifications.
For example: {"prefix": "Beautiful ", "trigger": "British", "suffix": " Columbia"}
[See Image.](#zwa-1504516)
To learn more, see [Configuring DLP Notification Templates](/zia/configuring-dlp-notification-templates), [Configuring the Zscaler Incident Receiver for On-Premises VMs](/zia/configuring-zscaler-incident-receiver), [Configuring the Zscaler Incident Receiver for Amazon Web Services EC2 VMs](/zia/configuring-zscaler-incident-receiver-for-ec2), and [Configuring the Zscaler Incident Receiver for Azure VMs](/zia/configuring-zscaler-incident-receiver-azure-vms).
[]![DLP Incident Trigger Context in ZWA](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/dlp-trigger-context-zwa.png)

### Feature Available
#### Adding Exception Capabilities for Collaboration Applications for Data at Rest Scanning
The Exceptions page is added for all Collaboration applications under the Policy > SaaS Security > Data at Rest Scanning page. Using this page, admins can create exceptions for DLP policies, allowing certain users, user groups, or departments to bypass content inspection.
[See image.](#collaboration-exceptions)
To learn more, see [Configuring the Data At Rest Scanning DLP Policy Exceptions](/zia/configuring-saas-security-api-dlp-policy-exceptions).
[]![The Exceptions page allows admins to create exceptions for DLP policies, allowing certain users, user groups, or departments to bypass content inspection.](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/configuring-saas-security-data-rest-scanning-dlp-policy-exceptions-doc-51422/Exceptions%20under%20Collaboration%20for%20SaaS%20Security%20DLP.png)

### Feature Available
#### Additional Microsoft SharePoint Custom Onboarding Requirements
When onboarding Microsoft SharePoint as a SaaS application tenant (Administration > SaaS Application Tenants), you can configure a Custom SaaS Connector using your Client ID, Client Secret, and Tenant ID in addition to uploading a private key JSON file so that the Zscaler service can access the application.
[See image.](#SP_custom_json)
To learn more, see [Authorizing a Custom Zscaler Connector for Microsoft Applications](/zia/authorizing-custom-zscaler-connector-microsoft-applications) and [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
[]![Authorizing SharePoint SaaS Application with new Private Key JSON file upload requirement](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/SP%20Authorize.png)

### Feature Available
#### Enhancement to Cloud NSS and Amazon S3 Integration
As an enhancement to Zscaler’s Cloud NSS integration with Amazon S3, you can specify the file extension (e.g., GZIP) of the log data stored in your configured S3 bucket, according to your integration requirements. To enable and set the file extension, contact Zscaler Support.
To learn more, see [Zscaler SaaS Security API and Amazon S3 Deployment Guide](/zscaler-technology-partners/zscaler-saas-security-api-and-amazon-s3-deployment-guide).

### Feature Available
#### Expanded File Type Support for DLP
The File Type Control and Data Loss Prevention (DLP) policies now support the following file types:
- Microsoft Outlook Mac Data (.olm)
- Microsoft Publisher Files (.pub)
- Microsoft TNEF file (.tnef)
- Microsoft Outlook Data File (.ost)
- Microsoft Outlook Personal Storage Table File (.pst)
- LZH Archive (.lha)
- CPIO File (.cpio)
- Open Office Presentations (.odp)
- Open Office Spreadsheets (.ods)
- Binhex files (.hqx)
- QuarkXPress files (.qxd, .qxp)
- AutoCAD (.dxf)
- AutoCAD Drawing (.dwg)
- Windows Executable (.exe)
- Windows Library (.dll)
- ELF files (.elf)
- Domino Server Database (.dxl)
The File Type Control and DLP policies support new file types in the following categories:
- [Microsoft Office](#microsoft-1509226)
- [Archive](#archive-1509226)
- [Open Office Files](#openoffice-1509226)
- [Other Documents](#otherdocuments-1509226)
- [Executable](#executable-1509226)
- [Database](#database-1509226)
To learn more, see [About File Type Control](/zia/about-file-type-control) and [About Data Loss Prevention](/zia/about-data-loss-prevention).
[]The Microsoft Office file types are available when creating the following polices in the Microsoft Office category:
- [DLP - Rule without Content Inspection](#microsoft-without-content-inspection-1509226)
- [DLP - Rule with Content Inspection](#microsoft-office-with-inspection-1509226)
[]
- Microsoft Outlook Mac Data (.olm)
- Microsoft Publisher Files (.pub)
- Microsoft TNEF file (.tnef)
![microsoft-office-no-content-matching-54191.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/microsoft-office-no-content-matching-54191.png)
[]
- Microsoft Outlook Mac Data (.olm)
- Microsoft Publisher Files (.pub)
![microsoft-office-with-contentmatching.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/microsoft-office-with-contentmatching.png)
[]The Archive file types are available when creating the following polices in the Archive category:
- [DLP - Rule without Content Inspection](#archive-without-content-inspection-1509226)
[]
- LZH Archive (.lha)
- CPIO File (.cpio)
![archive-no-matching-54191.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/archive-no-matching-54191.png)
[]The Open Office file types are available when creating the following policies in Open Office category:
- [DLP - Rule without Content Inspection](#openoffice-without-content-inspection-1509226)
- [DLP - Rule with Content Inspection](#open-office-content-inspection-1509226)
[]
- Open Office Presentations (.odp)
- Open Office Spreadsheets (.ods)
![open-office-no-matching-54191.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/open-office-no-matching-54191.png)
[]
- Open Office Presentations (.odp)
- Open Office Spreadsheets (.ods)
![open-office-with-matching-54191.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/open-office-with-matching-54191.png)
[]The Other Document file types are available when creating the following policies in Other Documents category:
- [DLP - Rule without Content Inspection](#otherdocswithoutcontentinspection-1509226)
[]
- Binhex files (.hqx)
- QuarkXPress files (.qxd, .qxp)
- AutoCAD (.dxf)
- AutoCAD Drawing (.dwg)
![other-docs-without-content-matching-54191.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/other-docs-without-content-matching-54191.png)
[]These Executable file types are available when creating the following policies in Executable category:
- [DLP - Rule without Content Inspection](#executable-without-content-inspection-1509226)
[]
- Windows Executable (.exe)
- Windows Library (.dll)
- ELF files (.elf)
![executable-no-content-matching-54191.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/executable-no-content-matching-54191.png)
[]The Database file types are available when creating the following policies in the Database category:
- [DLP - Rule without Content Inspection](#database-without-content-inspection-1509226)
[]
- Domino Server Database files (.dxl)
![database-no-content-matching-54191.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/database-no-content-matching-54191.png)

### Feature Available
#### Expansion of Supported Data Types for EDM Popular Format Check
You can configure DLP Exact Data Match (EDM) policies to enable or disable text format checks on the DLP Advanced Settings page (Administration > DLP Advanced Settings) to match additional popular data type formats including:
- ABA Bank Routing Numbers
- Alphanumeric Popular Formats
- Austria Social Security Number (ATSSN)
- Austria Tax Identification Number (ATTIN)
- Australian Medicare Number
- Australia Passport Number (AUPP)
- Australia Tax File Numbers (TFN)
- Belgium Tax Identification Number (BTIN)
- Brazil CNPJ Numbre (CNPJ)
- Brazil Individual Taxpayer Registry ID (CPF)
- National Identification Number (Bulgaria EGN)
- Chinese Identity Card Number
- Credit Cards (Diner's Club, AMEX pop formats, Visa, Mastercard, Discover, jcb)
- Denmark Tax Identification Number (DTIN)
- France National Identification Number (INSEE)
- France Tax Identification Number (FRTIN)
- Hungary Tax Identification Number (HUTIN)
- India Aadhaar Card Number
- Indonesian Tax Identification Number (NPWP)
- Japan Company Number
- Japan My Number (Individual Numbers)
- Korea Resident Registration Number (RRN)
- Luxembourg Tax Identification Number (LUTIN) pop formats
- Malaysia Identity Card Number (MYKAD)
- Mexico Standardized Bank Code (CLABE)
- National Economic Registry Number (REGON)
- National Provider Identifier (NPI)
- Netherlands Citizen Service Numbers (BSN)
- New Zealand Tax Identification Number (NZTIN)
- Numeric popular formats
- Peru Tax Identification Number (PERUC)
- Poland Tax Identification Number (PLTIN)
- Poland National Identification Number (PESEL)
- Portugal Tax Identification Number (PTIN)
- Singapore NRIC Numbers (UIN and FIN)
- Spanish Social Security Number
- Spain National Identification Number (DNI)
- Spain Tax Identification Number (CIF)
- Sweden Tax Identification Number (STIN)
- Switzerland Social Security Number (AHV)
- Taiwanese National Identification Number
- Thailand Identity Card Number
- UK National Health Service Number (NHS)
- UK National Insurance Number (NINO)
- Unique Master Citizen Number
- US Tax Identification Number (USITIN)
After it's enabled, the EDM match applies to all currently supported dictionaries and only succeeds if the format matches the popular data type format.
[See image](#enable-edm-popular-format)
To learn more, see [Configuring DLP Advanced Settings](/zia/configuring-dlp-advanced-settings).
[]
![Enable EDM Check for Popular Formats](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/edm-check-for-popular-formats.png)

### Feature Available
#### File Type Support for File Type Control & DLP
The File Type Control and Data Loss Prevention (DLP) policies now support the following file types in the Other Documents category:
- [File Type Control](#ohter-documents-ftc-1507906)
- [DLP - Rule without Content Matching](#other-docs-no-content-matching-1507906)
- [DLP - Rule with Content Matching](#other-docs-with-content-matching-1507906)
To learn more, see [About File Type Control](/zia/about-file-type-control) and [About Data Loss Prevention](/zia/about-data-loss-prevention).
Update to Cloud Service API
The cloud service API includes the following new file types for the `fileTypes` attribute within the `WebDlpRule` model used in `/webDlpRules` endpoints:
- `FTCATEGORY_JSON`
- `FTCATEGORY_XML`
- `FTCATEGORY_HTTP`
- `FTCATEGORY_UNK_TXT`
To learn more, see the [API Reference](/zia/about-api).
[]
- JSON files (.json)
- XML files (.xml)
![other-docs-ftc-54195.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/other-docs-ftc-54195.png)
[]
- JSON files (.json)
- XML files (.xml)
- Text files with unknown extensions
- HTTP non-file text data
![other-docs-jsonxml-with-content-matching-54195.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/other-docs-jsonxml-with-content-matching-54195.png)
[]
- JSON files (.json)
- XML files (.xml)
- Text files with unknown extensions
- HTTP non-file text data
![other-docs-jsonxml-no-content-matching-54195.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/other-docs-jsonxml-no-content-matching-54195.png)

### Feature Available
#### Hex-Encoded Device Hostname Field in NSS Feeds
The field `%s{edevicehostname}` is available when adding an NSS or Cloud NSS feed for the following ZIA log types:
- Web
- Firewall
- DNS
- Endpoint DLP
The field output is the hex-encoded device hostname associated with the transaction. To learn more, see:
- [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs)
- [NSS Feed Output Format: Firewall Logs](/zia/nss-feed-output-format-firewall-logs)
- [NSS Feed Output Format: DNS Logs](/zia/nss-feed-output-format-dns-logs)
- [NSS Feed Output Format: Endpoint DLP Logs](/zia/nss-feed-output-format-endpoint-dlp-logs)

### Feature Available
#### Logs for Application Status
You can filter and view logs for application status. The following changes are available in the ZIA Admin Portal:
Web Insights Logs
A filter and column, Application Status, is added to Web Insights Logs.
[See image.](#img_app_status)
To learn more, see [Web Insights Logs: Columns](/zia/web-insights-logs-columns) and [Web Insights Logs: Filters](/zia/web-insights-logs-filters).
NSS Feeds
The field `%s{app_status}` is available when adding an NSS or Cloud NSS feed for web logs.
To learn more, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs).
[]![This image shows the Application Status column and filter.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/Application_Status.png)

### Feature Available
#### New File Type Support for Open Office Files for Data Loss Prevention (DLP)
The Data Loss Prevention (DLP) policies support new file types in the Open Office category:
- Open Office Presentations (.odp, .otp)
- Open Office Spreadsheets (.ods, .ots)
The file types are available in the following categories:
- [DLP - Rule without Content Inspection](#openoffice-without-content-inspection-1507276)
- [DLP - Rule with Content Inspection](#open-office-content-inspection-1507276)
To learn more, see [About Data Loss Prevention](/zia/about-data-loss-prevention).
[]
- Open Office Presentations (.odp, .otp)
- Open Office Spreadsheets (.ods, .ots)
![open-office-no-matching-54191.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/open-office-no-matching-54191.png)
[]
- Open Office Presentations (.odp, .otp)
- Open Office Spreadsheets (.ods, .ots)
![open-office-with-matching-54191.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/open-office-with-matching-54191.png)

### Feature Available
#### NSS Support for Google Cloud Platform
Zscaler’s Nanolog Streaming Service (NSS) supports the configuration and deployment of an NSS virtual machine (VM) on Google Cloud Platform (GCP).
After deploying an NSS VM on GCP, you can stream your organization’s Web or Firewall logs from the Zscaler cloud to your security information and event management system.
To learn more, see [NSS Deployment Guide for Google Cloud Platform](/zia/nss-deployment-guide-google-cloud-platform).

### Feature Available
#### SaaS Security Posture Management Support for New Applications
You can configure Advanced SaaS Security Posture Management (SSPM) for Box, Dropbox, and GitLab tenants. Select the SSPM Scan checkbox when onboarding a tenant to enable the Advanced SSPM scan capability for the specific tenant. Existing users can also enable Advanced SSPM support by selecting the SSPM Scan checkbox under the onboarding section for the specific tenants and then validating and saving the changes.
[See image.](#servicenow-sspm-onboarding)
The SSPM Scan checkbox is enabled only when you have the Advanced SSPM enabled for your tenant.
To learn more, see [Understanding the SaaS Security Posture Management Policy](/zia/understanding-saas-security-posture-management-policy) and [Viewing and Managing the Supported SSPM Policies](/zia/viewing-and-managing-supported-sspm-policies).
[]![Select the required onboarding function to enable for the GitLab tenant.](/sites/default/files/downloads/Adavanced%20SSPM-ShareFile.png)

### Feature Available
#### Support for DICOM Files in DLP
The Data Loss Prevention (DLP) policies support the DICOM file type in the Image category:
- [DLP - Rule without Content Inspection](#image-without-content-matching-1509231)
- [DLP - Rule with Content Inspection](#image-with-content-matching-1509231)
Text Extraction for DICOM Files
We can now extract sensitive information from DICOM files and perform DLP inspection. For example, we can extract information such as:
- Patient Name
- Patient ID
- Patient Birth Data
- Patient Gender
- Patient Birth Name
- Patient Age
- Patient Weight
- Patient BI
- Patient Address
- Patient Insurance Plan Identification
- Patient Mother's Name
- Patient Country of Residence
- Patient Region of Residence
- Patient Telephone Number
- Patient Occupation
- Patient Telecom Info
- Institute Name
- Institute Address
- Referring Physician Name
- Referring Physical Address
- Referring Physician Telephone Number
- Consulting Physician Name
- Study Description
To learn more, see [About Data Loss Prevention](/zia/about-data-loss-prevention).
[]
- DICOM
![image-no-content-matching-54191.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/image-no-content-matching-54191.png)
[]
- DICOM
![image-no-content-matching-54191.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/image-no-content-matching-54191.png)

### Feature Available
#### Update to DNS Gateway
DNS Gateways support a new failure behavior to forward DNS requests to the Zscaler Trusted DNS Resolver over TCP or UDP when the configured DNS service is unavailable or unhealthy.
[See image.](#dns-gatewary-failover-forward-to-ZTR)
A DNS Gateway configured with this failure behavior can be used in DNS filtering rules along with one of the following rule actions:
- Redirect Request Using TCP (incoming requests can be over TCP or DoH)
- Redirect Request Using UDP (incoming requests can be over UDP or DoH)
- Redirect Request & Keep Sender Protocol (incoming requests can be over any protocol, i.e., TCP or UDP in this case)
To learn more, see [Adding DNS Gateways](/zia/adding-dns-gateways) and [Configuring the DNS Control Policy](/zia/configuring-dns-control-policy).
[]![DNS Gateway with new failover behavior to forward requests to Zscaler Trusted Resolver](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/DNS-gateway-failover-forward-to-ZTR.png)

### Feature Available
#### Updates to DNS Control Policy
The DNS Control policy supports additional DNS record types such as CSYNC, HTTPS, SVCB, and ZONEMD in the DNS Request Type criteria.
[See image.](#dns-rule-new-request-types-https)
In addition, DNS Logs include a new DNS Request Type filter option, namely SVCB-compatible type for use with HTTP, to filter transactions that have a match with the HTTPS record type.
[See image.](#dns-logs-https-request-type-filter-option)
To learn more, see [Configuring the DNS Control Policy](/zia/configuring-dns-control-policy).
[]![A screenshot of the DNS Control rule with additional record types such as CSYNC, HTTPS, SVCB, and ZONEMB](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/dns-rule-new-request-types-https.png)
[]![A screenshot of DNS logs with the new request type filter option for HTTPS](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/dns-logs-https-request-type-filter-option.png)

## October 30, 2024
### Feature Available
#### Zscaler Custom EUN Messages for Inline Web DLP on macOS
With the release of Zscaler Client Connector version 4.3.1.59 for macOS, Data Loss Prevention (DLP) policy rules support end user notification (EUN) messages when user activity triggers a policy rule on a macOS endpoint. When configuring DLP policy rules, you can select to Show or Hide an EUN message on endpoints when content triggers the DLP policy rule. If you select Show, you can specify the custom EUN message that appears when the rule is triggered.
[See image.](#unified-eun-dlp-macos)
To learn more, see [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection), [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection), and [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled).
You can customize the EUNs for DLP policy rules under Administration > End User Notifications > Client Connector. You can modify the default notification message and additionally create custom messages to allow the selection of different notification messages for individual DLP rules.
[See image.](#inline-web-dlp-custom-eun-macos)
To learn more, see [Configuring EUNs for Inline Web DLP](/zia/configuring-euns-inline-web-dlp) and [Configuring Settings for Zscaler Client Connector-Based EUNs](/zia/configuring-settings-zscaler-client-connector-based-euns).
[]![ZIA Inline Web DLP Policy rule window with Client Connector-based EUN option](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-DLP-Unified-EUN-Policy-Rule-RN.png)
[]![Inline Web DLP custom EUN message](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/inline-web-dlp-custom-eun.png)

## October 25, 2024
### Feature Available
#### Enhancements to Management Portal for Partners
The following enhancements are available in the Zscaler Management Portal for Partners:
Update to Tenants
You can view a complete list of tenants, and other details including subscription information, renewal dates, added domains, groups they belong to, and much more.
[See image.](#tenants-mpp)
To learn more, see [About Tenants in the Management Portal for Partners](/zia/about-tenants-management-portal-partners) and [Viewing Tenant Details](/zia/viewing-tenant-details).
[]
![Enhancements to the Tenants page](/sites/default/files/downloads/release-notes-drafts/improvements-to-management-portal-for-partners/update-to-tenants.png)
Support for Tenant Groups
You can group tenants across clouds or industry and assign a policy template to the group.
[See image.](#tenant-groups-mpp)
To learn more, see [About Tenant Groups](/zia/about-tenant-groups) and [Configuring Tenant Groups](/zia/configuring-tenant-groups).
[]
![Enhancements to the Tenant Groups page](/sites/default/files/downloads/release-notes-drafts/improvements-to-management-portal-for-partners/update-to-tenant-groups.png)
Support for Role Templates
You can create a customized role template for Zscaler partner admin users. You can also define permissions on a granular level.
[See image.](#role-templates-mpp)
To learn more, see [About Roles in the Management Portal for Partners](/zia/about-roles-management-portal-partners) and [Managing Roles in the Management Portal for Partners](/zia/managing-roles-management-portal-partners).
[]
![Introducing Roles](/sites/default/files/downloads/release-notes-drafts/improvements-to-management-portal-for-partners/update-to-roles.png)
Updates to Admins
When adding a new admin, you can assign a role template, tenants, or tenant groups to the admin.
[See image.](#admins-mpp)
To learn more, see [About Admins in the Management Portal for Partners](/zia/about-admins-management-portal-partners) and [Adding a New Admin in the Management Portal for Partners](/zia/adding-new-admin-management-portal-partners).
[]
![update-to-admins.png](/sites/default/files/downloads/release-notes-drafts/improvements-to-management-portal-for-partners/update-to-admins.png)
Support for Policy Templates
The Policy Templates drawer is added to the Management Portal for Partners page. You can add, edit, or delete a policy template for an individual tenant or tenant groups.
[See image.](#policy-template)
To learn more, see [About Policy Templates](/zia/about-policy-template).
Support for Audit Logs
The Management Portal records the login name and IP address of every admin who logs in to the portal and adds or modifies configurations. The audit logs display a list of actions performed in the portal.
[See image.](#Audit-Logs)
To learn more, see [About Audit Logs in the Management Portal for Partners](/zia/about-audit-logs-management-portal-partners).
The audit logs in the ZIA Admin Portal display the partner usernames when requests are initiated to the ZIA Admin Portal from the Management Portal for Partners. To learn more about audit logs in the ZIA Admin Portal, see [About Audit Logs](/zia/about-audit-logs).
[]![Screenshot of Audit Logs](/sites/default/files/downloads/Audit_Logs_RN.png)
[]![Policy Templates Page in the Management Portal for Partners](/sites/default/files/downloads/Policy%20Template%20RN1.png)

### Feature Available
#### Support for Zscaler Advanced SaaS Security Posture Management
Zscaler’s Advanced SaaS Security Posture Management (SSPM) enhances your organization’s SaaS security, by providing comprehensive visibility and control over your SaaS environment and third-party applications. With a broader coverage of the SaaS applications, enhanced security controls, and configuration drift management, Advanced SSPM enables you to identify and mitigate misconfiguration quickly.
To upgrade to Advanced SSPM, contact your Zscaler Account team.
Use Advanced SSPM for deeper insights into the third-party application behaviors and users at risk, and to strengthen your security posture. Advanced SSPM, along with 3rd-Party App Governance and Data at Rest Scanning, forms the unified SaaS Security provided by Zscaler.
Additionally, the ZIA Admin Portal is enhanced to align with the Advanced SSPM capabilities. Refer to the following table for a list of updated labels:
| Old UI Labels | New UI Labels |
| ------------- | ------------- |
| SaaS Security API (Policy > SaaS Security API) | SaaS Security (Policy > SaaS Security) |
| SaaS Security API Control (Policy > SaaS Security API > SaaS Security API Control) | Data at Rest Scanning (Policy > SaaS Security > Data at Rest Scanning) |
| SaaS Security Posture Management (Policy > SaaS Security API > SaaS Security Posture Management) | Posture Management (Policy > SaaS Security > Posture Management) |
| Applications - Shadow IT Report (Analytics > SaaS Security Report > Applications) | Applications - Shadow IT Report (Analytics > SaaS Security > Applications) |
| SaaS Activities (Analytics > SaaS Security Report > SaaS Activities) | Activities (Analytics > SaaS Security > Activities) |
| Security Configuration (Analytics > SaaS Security Report > Security Configuration) | Posture Management (Analytics > SaaS Security > Posture Management) |
| 3rd Party Applications (Analytics > SaaS Security Report > 3rd Party Applications) | 3rd-Party App Governance (Analytics > SaaS Security > 3rd-Party App Inventory) |
To learn more about Advanced SSPM, see What is [Advanced Posture Management?](/zia/what-advanced-posture-management) and [About Posture](/zia/about-posture).

### Feature Available
#### The Endpoint Data Scan Report
The new Endpoint Data Scan Report provides visibility into sensitive data stored locally on all endpoints connected to your organization's network. The report allows you to drill down by user to analyze activities, incidents, and sensitive data stored on the endpoint.
[See image.](#data-scan)
To learn more, see [Accessing and Navigating the Endpoint Data Scan Report](/zia/accessing-and-navigating-endpoint-data-scan-report), [About Endpoint Data Scan](/zia/about-endpoint-data-scan), [About User Investigation](/zia/about-user-investigation), and [Analyzing Endpoint DLP Scan for a User](/zia/analyzing-endpoint-dlp-scan-user).
[]![Endpoint Data Scan](/sites/default/files/downloads/tech-pubs-drafts/risk360-draft-articles/configuring-alert-rule-draft-54732/Endpoint-Scan-Data-Report.png)

### Feature Available
#### Update to Cloud Service API: Hosted PAC Files
The cloud service API includes new endpoints to manage the Zscaler-hosted PAC files. The following endpoints are introduced to retrieve the list of hosted PAC files, add custom PAC files, validate the PAC file content and check for errors, branch an existing PAC file to create a new version, retrieve all or specific versions of a PAC file, and delete a PAC file:
- `GET /pacFiles`
- `POST /pacFiles`
- `POST /pacFiles/validate`
- `POST /pacFiles/{pacId}/version/{clonedPacVersion}`
- `GET /pacFiles/{pacId}/version`
- `GET /pacFiles/{pacId}/version/{pacVersion}`
- `DELETE /pacFiles/{pacId}`
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection has also been updated to include new and updated resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

### Feature Available
#### Update to ZIA Analytics for Isolation
ZIA Analytics includes additional information for Isolation data:
-
There is a new Web Insights filter for Isolation Policy Reason.
[See image.](#Web-Insights-filter)
- There is a new widget for Policy Reason in Browser Isolation Consumption Reports.
[See image.](#new-Policy-Reason-widget)
To learn more, see [Web Data Types and Filters](/zia/web-data-types-and-filters) and [Interactive Reports for Isolation in the ZIA Admin Portal](/isolation/isolation-reports-zia-admin-portal).
[]![Policy-Reason-addition-Consumption-Report.png](/sites/default/files/downloads/isolation/analytics/isolation-reports-zia-admin-portal/Policy-Reason-addition-Consumption-Report.png)
[]![Web-Insights-filter-Isolation-Policy-Reason.png](/sites/default/files/downloads/isolation/analytics/Web-Insights-filter-Isolation-Policy-Reason.png)

## October 15, 2024
### Feature Available
#### Turbo Mode for Isolation with ZIA
Turbo mode for Isolation leverages the GPU on the user's machine, capturing the rendering instructions from an isolated web page and replaying them in the user's browser window. This method of rendering content is faster and uses less bandwidth than pixel streaming. You can enable this feature [per isolation profile](/isolation/profiles).
[See image.](#Enable-Turbo-Mode)
To learn more, see [Using Turbo Mode for Isolation](/isolation/using-turbo-mode-isolation) and [Creating Isolation Profiles for ZIA](/isolation/creating-isolation-profiles-zia).
[]![Add-Isolation-Profile_Enable-Turbo-Mode.png](/sites/default/files/downloads/isolation/end-user-isolation-experience/using-turbo-mode-isolation/Add-Isolation-Profile_Enable-Turbo-Mode.png)

## October 07, 2024
### Feature Available
#### Enhancements to Endpoint DLP
The following enhancements are available in Endpoint DLP:
- Customized end user notification (EUN) and confirmation messages in the following languages:
- English (Default)
- Chinese (Traditional)
- French
- German
- Japanese
- Spanish
If the endpoint OS is set to one of the supported languages, then the EUN or confirmation message appears in that language on the endpoint. If the endpoint OS is set to an unsupported language, then the EUN or confirmation message appears in English.
- The ability to apply Endpoint DLP policy rules to print jobs in LibreOffice, Chrome, and Microsoft Edge.
To learn more, see [About Client Connector-Based End User Notifications](/zia/about-client-connector-based-end-user-notifications), [Configuring User Confirmation Notification Templates](/zia/configuring-user-confirmation-notification-templates), and [Configuring Endpoint DLP Policy Rules](/zia/configuring-endpoint-dlp-policy-rules).

### Feature Available
#### New Confirm Action for Inline Web DLP
The Inline Web Data Loss Prevention (DLP) policy supports a Confirm action that allows users to justify a transaction to continue, or cancel the transaction altogether; in both cases, the service logs the transaction accordingly.
[See image.](#inline-web-dlp-confirm-action-rn)
When you select the Confirm action for a policy rule, the Zscaler service automatically notifies users with a confirmation message that can be localized into one of the following supported languages:
- English (Default)
- Chinese (Traditional)
- French
- German
- Japanese
- Spanish
[See image.](#inline-web-dlp-confirm-message-rn)
If the endpoint OS is set to one of the supported languages, then the confirmation message appears in that language on the endpoint. If the endpoint OS is set to an unsupported language, then the confirmation message appears in English.
To learn more, see [Configuring Settings for User Confirmation Notification Templates](/zia/configuring-settings-user-confirmation-notification-templates), [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection), [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection), and [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled).
[]![Inline Web DLP Policy with Confirm Action option](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Example-DLP-Policy-rule_with-Confirm-RN.png)
[]![Inline Web DLP Customizable Confirmation Message](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Inline-Web-DLP-Confirm-Message-RN.png)

### Feature Available
#### User Messages for Advanced Threat Protection Policy
To access this feature, contact your Zscaler Account team.
If the Advanced Threat Protection policy is configured to block malicious activity, and a user's traffic matches a blocked activity on files greater than 10MB (client streaming), Zscaler Client Connector displays a notification that the activity was blocked as potentially harmful.
[See image.](#atp-block-message-v1)
This feature requires one of the following versions:
- For Windows:
- Zscaler Client Connector version 4.4.500.11 (contact Zscaler Support for this custom build)
- Zscaler Client Connector version 4.6.x or later
- Zscaler Data Protection build 24.08.0.42 or later
- For macOS:
- Zscaler Client Connector version 4.3.0.240 or later
- Zscaler Data Protection build 24.8.0.810 or later
The Zscaler service logs transactions in real time and shows the information on the Security Dashboard (Dashboard > Security) in the ZIA Admin Portal.
To learn more, see [Configuring the Advanced Threat Protection Policy](/zia/configuring-advanced-threat-protection-policy) and [About Dashboards](/zia/about-dashboards).
[]![Advanced Threat Protection Block Message](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-ATP-Client-Connector-Notifications-v1-RN.png)

## September 27, 2024
### Feature Available
#### Block SSL Traffic with No Server Name Indication (SNI)
The new toggle, Block No Server Name Indication (SNI), is added under the Policies > SSL Inspection > Add SSL Inspection Rule. Enabling this option blocks any traffic that does not contain the SNI in the Client Hello message. This option is disabled by default.
[See Image.](#block-no-sni)
To enable the Block No Server Name Indication (SNI) option while adding an SSL Inspection Rule, contact Zscaler Support.
To learn more, see [Configuring SSL Inspection Policy](/zia/configuring-ssl-inspection-policy).
[]![Block No Server Name Indication (SNI)](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/Block%20No%20Server%20Name%20Indication%20(SNI)%20Default.png)

### Feature Available
#### New File Type Support for File Type Control Policy & DLP
The File Type Control and Data Loss Prevention (DLP) policies now support the following file types:
- Zipx File (.zipx)
- Microsoft Outlook Data (.ost)
The file types are available when creating File Type Control and DLP policies in the following categories:
- [Archive](#archive-zipx-file)
- [Microsoft Office](#microsoft-office-ost-file)
To learn more, see [About File Type Control](/zia/about-file-type-control) and [About Data Loss Prevention](/zia/about-data-loss-prevention).
[]
The Zipx File (.zipx) file type is available when creating the following polices in the Archive category:
- [File Type Control](#archive-file-type-zipx-file)
- [DLP (Rule without content inspection)](#dlp-archive-file-type-zipx-file)
[]![Add new Image File Type Control rules](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-File-Type-zipx-file-support-RN.png)
[]![Add new file type to DLP rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-DLP-zipx-file-support-RN.png)
[]
The Microsoft Outlook Data (.ost) file type is available when creating the following polices in the Microsoft Office category:
- [File Type Control](#other-microsoft-file-type-ost-file)
- [DLP (Rule without content inspection)](#other-microsoft-dlp-file-ost-file)
[]![Add new Archive File Type Control rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-File-Type-ost-file-support-RN.png)
[]![Add new file type to DLP rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-DLP-ost-file-support-RN.png)

### Feature Available
#### SaaS Security API DLP Watermark Support
The SaaS Security API Data Loss Prevention (DLP) policy for file sharing applications supports adding watermarks to supported file types that contain sensitive data. To use this functionality, you first create a watermark profile, which contains the watermark text, as well as an optional header and footer.
[See image.](#rights-management-watermark-profile-rn)
With the watermark profile in place, you can then create SaaS Security API rules for file sharing applications that apply the watermark settings to [supported file types](/zia/configuring-saas-security-api-dlp-policy#filesharing-watermark) that trigger the policy rule.
[See image.](#rights-management-watermark-rule-rn)
To learn more, see [About Rights Management](/zia/about-rights-management).
You can remove a watermark that was applied to a file via a watermark profile in the SaaS Assets Report: Assets with Incidents page (Analytics > SaaS Security Report > Assets) as a remediation action. This option is not available for image files.
To learn more, see [SaaS Assets Report: Assets with Incidents](/zia/saas-assets-report-assets-incidents).
[]![Screenshot of the Add Watermark Profile Window](/sites/default/files/downloads/zia/policies/saas-security-api/rights-management/ZIA-DLP-Rights-Management-Add-Watermark-Profile-RN.png)
[]![Screenshot of the Watermarking option for a SaaS Security API rule](/sites/default/files/downloads/zia/policies/saas-security-api/rights-management/ZIA-DLP-Rights-Management-Watermark-Rule-RN.png)

### Feature Available
#### Support for Non-delimited Unicode Detection
You can now enable Non-delimited Unicode phrase matching in the Add DLP Dictionary window. With this feature enabled, Unicode phrases defined in the Phrases list is matched even if they are similar to characters without any delimiter in between. For example, a phrase of “クレジットカード” matches a string of “クレジットカードのコピーをください。” Matches happen even when no spaces are detected. If the checkbox is not enabled, the payload only matches the exact phrase.
[See image.](#non-delimited-unicode-1499546)
To learn more, see [Adding Custom DLP Dictionaries](/zia/adding-custom-dlp-dictionary) and [Defining Phrases for Custom DLP Dictionaries](/zia/defining-phrases-custom-dictionaries).
[]![Select checkbox for Non-delimited Unicode phrase matching](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/add-dlp-dictionary-unicode-checkbox.png)

### Feature Available
#### ZPA Application Segment Limits
You can add up to 2,000 Zscaler Private Access (ZPA) application segments while configuring Source IP Anchoring in the ZIA Admin Portal. To increase the application segment limits, contact Zscaler Support.
To learn more, see [Configuring Source IP Anchoring](/zia/configuring-source-ip-anchoring) and [Ranges & Limitations](/zia/ranges-limitations).

## September 23, 2024
### Feature Available
#### Language Translation in Isolation for ZIA
Users can translate web pages into different languages while in an isolated session through [Google Translate](http://translate.google.com/). They can translate the content of an entire page, or they can select specific text from the page to translate. For the duration of the session, users can click the Translate icon in the isolation bar menu or use [the right-click menu](/isolation/using-right-click-menu-isolation) to access the translation options. The default selected language depends on the user's region. This function can be enabled by admins per isolation profile. Google Translate is being used to power the translation within the application that is being isolated, and Zscaler uses Google Translate APIs in order to provide the translation service.
[See image.](#translattion-menu)
To learn more, see [Creating Isolation Profiles for ZIA](/isolation/creating-isolation-profiles-zia) and [Using the Isolation Bar in Native Browser Experience](/isolation/using-isolation-bar-native-browser-experience).
[]![Dialog-Box.png](/sites/default/files/downloads/isolation/end-user-isolation-experience/using-right-click-menu-isolation/Dialog-Box.png)

## September 20, 2024
### Feature Available
#### Ability to Include or Exclude Specific Social Security Numbers in DLP Dictionaries
You can add specific Social Security numbers to the predefined Data Loss Prevention (DLP) Social Security Numbers (US) dictionary or its clones so that the numbers are included in or excluded from DLP scan match.
[See image.](#dlp-dictionary-ssn-include-exclude)
To learn more, see [Editing Predefined DLP Dictionaries](/zia/editing-predefined-dlp-dictionaries).
The DLP endpoints within the cloud service API include the following attributes to include or exclude a list of Social Security numbers from the predefined DLP Social Security Numbers (US) dictionary or its clones.
- `includeSsnNumbers`
- `ssnNumbers`
To learn more, see the [API Reference](/zia/about-api).
[]![Support for Social Security number include/exclude in Data Loss Prevention (DLP) Social Security Numbers (US) dictionary in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-DLP-SSN-US-Dictionary-Include-Exclude-RN.png)

### Feature Available
#### DLP Inspection on HTTP GET Query Parameters
You can configure DLP rules to inspect HTTP GET Query Parameters to detect sensitive data exfiltrations from different URL categories (e.g., search engines, translation tools, or custom URLs). To enable this feature, go to the DLP page and enable Inspect HTTP GET Query Parameters, then select the URL categories from the drop-down menu.
[See image.](#enableinspectgetheaders-1499741)
To learn more, see [Configuring DLP Advanced Settings](/zia/configuring-dlp-advanced-settings), [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection), and [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled).
[]![inspect-url-categories.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/inspect-url-categories.png)

### Feature Available
#### Restore a Quarantined File
A new option, Restore, is added as part of remediation actions in the Incidents section of the SaaS Assets Report for the collaboration application Slack.
[See Image.](#img_restore_remediation_action)
To learn more, see [SaaS Assets Report: Assets with Incidents](/zia/saas-assets-report-assets-incidents#messages-collab).
[]![This image displays the Remediation Action Restore option.](/sites/default/files/downloads/zia/documentation-knowledgebase/release-notes/release-upgrade-summary-2024/Restore_option_for_slack.png)

### Feature Available
#### Zscaler Incident Receiver Health Check Feature
The new Incident Receiver health check feature is enabled by default and produces an additional file in your evidence folder:
`<systmld>_<iphash>_ir_health_status_timestamp.json`
After configuring your Incident Receiver, the health check periodically adds a health status to the evidence folder with a new time stamp. By default, the health check is set to run every 5 minutes.
To learn more, see [Configuring the Zscaler Incident Receiver for Amazon Web Services EC2 VMs](/zia/configuring-zscaler-incident-receiver-for-ec2), [Configuring the Zscaler Incident Receiver for On-Premises VMs](/zia/configuring-zscaler-incident-receiver), or [Configuring the Zscaler Incident Receiver for Azure VMs](/zia/configuring-zscaler-incident-receiver-azure-vms).

## September 13, 2024
### Feature Available
#### Generative AI Enhancements
The Zscaler service enables you to configure the prompts for generative AI applications such as ChatGPT, Google Gemini, Perplexity, Poe, and Meta AI. As part of this change, in the Policy > URL Filtering & Cloud App Control > Advanced Policy Settings page, the Gen AI Prompt Configuration section is added with the options to enable prompts for these generative AI applications. Enabling these options allows you to categorize and store the prompts for the respective applications.
[See image.](#gen-ai-prompt)
To learn more, see [Configuring Advanced Policy Settings](/zia/configuring-advanced-url-policy-settings).
Gen AI Security Report and Logs
The Gen AI Security Report gives visibility and insight into your organization’s use of generative AI applications.
The Gen AI security report includes the following enhancements:
- A new page to monitor and view logs for the Gen AI Security Report (Analytics > Gen AI Security Report).
- A filter and column, Prompt, is added to [Web Insights Logs](/zia/about-insights-logs) (Analytics > Insights > Web Insights). You can filter and view logs for the different prompts entered by users in the generative AI applications.
[See image.](#gen-ai-report)
To learn more, see [About the Gen AI Security Report](/zia/about-generative-ai-security-report), [Web Insights Logs: Columns](/zia/web-insights-logs-columns), and[ Web Insights Logs: Filters](/zia/web-insights-logs-filters).
[]![Screenshot of ZIA's Advanced Policy Settings page with Gen AI Prompt Configuration](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Advanced-Policy-Settings-Gen-AI-Prompt-Configuration-wo-copilot-RN.png)
[]![Gen AI Security Report](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/Gen_AI_Security_Report_RN.png)

## September 09, 2024
### Feature Available
#### Enhancement to 3rd-Party App Governance for Okta
Federation Broker mode is supported for Okta apps. These apps rely on external identity providers (IdPs) instead of directly managed users. They allow automatic app access assignment based on sign-in policies and authorization rules.

## September 06, 2024
### Feature Available
#### Enhancement to Advanced Settings
On the Advanced Settings page, you can configure the Insert XFF Header for SSL Inspected Traffic field to insert XFF header for traffic forwarded from ZIA to Zscaler Private Access (ZPA) ([Source IP Anchored](/zia/understanding-source-ip-anchoring), [Zscaler-Managed Dedicated IP](/zia/understanding-zscaler-managed-dedicated-ip), and [ZIA-inspected ZPA application traffic](/zia/configuring-forwarding-policy)). This field is enabled by default.
[See image.](#RN-xff-header-zpa-traffic)
To learn more, see [Configuring Advanced Settings](/zia/configuring-advanced-settings).
![Insert XFF Header for ZPA Traffic field ](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/zia-RN-xff-header-advanced-settings.png)
[]

### Feature Available
#### SaaS Security API
You can now configure tenants for Smartsheet, a file sharing application.
[See image.](#add-tenant-smartsheet)
To learn more, see [About SaaS Application Tenants](/zia/about-saas-application-tenants) and [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
You can configure the application for the SaaS Security API Control policies and also view them on the following pages:
- [Saas Assets Report](/zia/saas-assets-report)
- [SaaS Assets Summary Report](/zia/saas-assets-summary-report)
- [SaaS Security Insights](/zia/saas-security-insights) and [Insights Logs](/zia/saas-security-insights-logs)
- [NSS Feeds](/zia/adding-nss-feeds-saas-security-logs) and [Cloud NSS Feeds for SaaS Security Logs](/zia/adding-cloud-nss-feeds-saas-security-logs)
To learn more, see [Configuring the SaaS Security API Control Policy](/zia/configuring-saas-security-api-control-policy).
[]![Add SaaS Application Tenants for Smartsheet](/sites/default/files/downloads/add-tenant-smartsheet.png)

## September 03, 2024
### Feature Available
#### Enhancement to 3rd-Party App Governance Dashboard
The Zscaler 3rd-Party App Governance dashboard is enhanced to display an overview of all active and deactivated apps across your business. You can also view the number of active, deactivated, and risky apps, as well as affected users over a specific time period.
[See image.](#3rd-Party-App-Governance-Dashboard)
To learn more, see [About the 3rd-Party App Governance Dashboard](/zia/about-3rd-party-app-governance-dashboard).
[]![3rd-Party App Governance Dashboard](/sites/default/files/downloads/Dashboard%20_%20RN1.png)

### Feature Available
#### Support for Zoom, Webex, and Box Apps with the 3rd-Party App Governance Catalog
You can search for, pre-vet, and manage Zoom, Webex, and Box apps across the 3rd-Party App Governance catalog and upload them to your inventory to gain continuous visibility and support pre-vetting scenarios.

## August 30, 2024
### Feature Available
#### Enhancement to Malware Protection Policy
You can now allow or block downloads from tools that are common from remote access sites when configuring the Malware Protection policy. To learn more, see [Configuring the Malware Protection Policy.](/zia/configuring-malware-protection-policy)
[See image.](#remote-access-tool)
[]
![Remote Access Tool option on the Malware Protection page](/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-malware-protection-policy-remote-access-tool.png)

## August 23, 2024
### Feature Available
#### Zscaler Client Connector-Based EUN for Tenancy Restriction
The end user notification (EUN) is extended to Zscaler Client Connector. This allows you to show client connector-based notification messages (custom or default) on the endpoints for the tenancy restriction feature. As part of this change, in the Cloud App Control Policy rule windows that support tenancy restrictions, the following fields are added:
- End User Notification
- Custom Message
[See image.](#tenant-restriction-eun)
To learn more, see [Configuring EUNs for Cloud App Control](/zia/configuring-euns-cloud-app-control) and [Adding Rules to the Cloud App Control Policy](/zia/adding-rules-cloud-app-control-policy).
[]![Screenshot of ZIA Cloud App Control Policy rule with Client Connector-based notification for Tenancy Restriction Feature](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Add-Cloud-App-Control-Rule-EUN-RN.png)

## August 16, 2024
### Feature Available
#### Adding EDM Popular Format Check
You can now configure DLP Exact Data Match (EDM) policies to enable or disable text format checks on the DLP Advanced Settings page (Administration > DLP Advanced Settings) to match popular data type formats including US Social Security Number (SSN), Credit Card Number (CCN), and Canadian Social Insurance Number (CSIN). After it's enabled, the EDM match applies to all currently supported dictionaries and only succeeds if the format matches the popular data type format (SSN, CCN, or CSIN).
[See image](#enable-edm-popular-format)
To learn more, see [Configuring DLP Advanced Settings](/zia/configuring-dlp-advanced-settings).
[]
![Enable EDM Check for Popular Formats](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/edm-check-for-popular-formats.png)

### Feature Available
#### Advanced SSPM Support for New Platforms
Advanced SSPM supports the following new platforms:
- Asana
- AuthO
- Calendly
- ClickUp
- Databricks
- JFrog
- Miro
- monday
- MuleSoft
- OneLogin
- Smartsheet
- Snowflake
- Workday
- Zendesk
To learn more about onboarding supported platforms for Advanced SSPM, see [Connecting Your Platforms to Advanced SSPM](/zia/connecting-your-platforms-advanced-sspm).

### Feature Available
#### Captured Traffic Data Field in NSS Feeds
The field `%s{pcapid}` is available when adding an NSS feed or Cloud NSS feed for Web, Firewall, and DNS logs. The field output is the path of the packet capture (PCAP) file that captured the transaction.
To learn more, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs), [NSS Feed Output Format: Firewall Logs](/zia/nss-feed-output-format-firewall-logs), and [NSS Feed Output Format: DNS Logs](/zia/nss-feed-output-format-dns-logs).

### Feature Available
#### OAuth 2.0 Support for Microsoft Cloud App Security (MCAS) Partner Integration
The Zscaler partner integration with MCAS (i.e., Microsoft Defender for Cloud Apps) supports secure OAuth 2.0-based authentication. In contrast to legacy token-based authentication in which a key is generated based on the user’s security context, the OAuth 2.0 method grants access based on the application’s context. Permissions are set at the application level and not inherited by the user, whose roles and permissions in Azure can change over time.
To access MCAS with application context, create an application in Microsoft Entra ID (previously Microsoft Active Directory). In creating the application, you generate the values of the parameters (e.g., client ID, client secret, etc.) required for OAuth 2.0-based authentication. You later provide the values when configuring the integration on the Partner Integrations page in the ZIA Admin Portal (Administration > Partner Integrations).
[See image.](#img-zia-mcas-oauth)
Support for Existing Token-Based Integrations
If you have an existing MCAS partner integration using token-based authentication, your integration remains supported for backward compatibility. On the Partner Integrations page in the ZIA Admin Portal, you see the Select Authentication Method setting with the Token option enabled.
[See image.](#img-zia-mcas-token)
You cannot make any configuration changes to your existing integration or create a new token-based integration. Zscaler recommends converting your existing integration to the OAuth 2.0-based authentication method for improved security. After you convert your integration, the token method is no longer available as an option.
If you do not have an existing integration using token-based authentication, the token method is not available as an option in the portal at all.
To learn more, see [Integrating with Microsoft Cloud App Security](/zia/integrating-microsoft-cloud-app-security).
[]![OAuth 2.0-based Partner Integration configuration](/sites/default/files/downloads/unified/analytics/internet-saas/reports/viewing-internet-saas-quarterly-business-review-reports/mcas-integration-oauth-setup.png)
[]![Token-based Partner Integration](/sites/default/files/downloads/unified/analytics/internet-saas/reports/viewing-internet-saas-quarterly-business-review-reports/zia-mcas-integration-token-method.png)

## August 12, 2024
### Feature Available
#### Sandbox File Size Limit Increase for Select File Types
Zscaler Sandbox (Policy > Sandbox) supports file sizes up to 50MB for the following file types:
- Windows EXEs
- Android APKs
- Archives
To learn more, see [About Sandbox](/zia/about-sandbox).

## August 09, 2024
### Feature Available
#### Logs for Other DLP Rules and Server Destination Port
You can filter and view logs for different server destination ports and other DLP rules. As part of the update, the following changes are available in the ZIA Admin Portal:
Web Insights Logs
The filters and columns, Other DLP Rules and Server Destination Port, are added to Web Insights Logs.
[See image.](#img_otherdlprules-serverdestinationport)
To learn more, see [Web Insights Logs: Columns](/zia/web-insights-logs-columns) and [Web Insights Logs: Filters](/zia/web-insights-logs-filters).
NSS Feeds
The fields `%d{srv_dport}`, `%s{other_dlprulenames}`, and `%s{all_dlprulenames}` can be added to the Feed Output Format when configuring an NSS or Cloud NSS feed for web logs.
To enable logging for Server Destination Port, contact Zscaler Support.
To learn more, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs).
[]![Web Insights - Other DLP Rules and Server Destination Filters and Columns](/sites/default/files/downloads/zia/release-notes/Destination_server_port_DLP_rules_with_values.png)

### Feature Available
#### New Activities for File Share Applications
For file sharing applications (OneDrive and SharePoint), two new activities, Download Sync and Upload Sync, are added to the **SaaS Security Activities Report**.
[See Image.](#img_download_upload_sync_activity)
To learn more, see [SaaS Security Activities Report](/zia/saas-security-activities-report).
[]![This image shows the Download and Upload Sync Activities.](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-security-activities-report/Download_Upload_Sync.png)

### Feature Available
#### New File Type Support for File Type Control Policy & DLP
The File Type Control and Data Loss Prevention (DLP) policies now support the following file types:
- FinalCode File (.fcl)
- AAC File (.aac)
- Greenshot Files (.greenshot)
- High Efficiency Image Files (.heic, .heif)
- IMG (.img)
- Microsoft Netmon Packet Capture File (.cap)
- Windows Registry HIVE files (.sam)
The file types are available when creating File Type Control and DLP policies in the following categories:
- [Archive](#archive-1487061)
- [Audio](#audio-1487061)
- [Image](#image-1487061)
- [Other Microsoft](#other_microsoft-1487061)
To learn more, see [About File Type Control](/zia/about-file-type-control) and [About Data Loss Prevention](/zia/about-data-loss-prevention).
[]
The FinalCode File (.fcl) file type is available when creating the following polices in the Archive category:
- [File Type Control](#archive-file-type-1487061)
- [DLP (Rule without content inspection)](#dlp-archive-file-type-1487061)
[]
The AAC File (.aac) file type is available when creating the following policies in the Audio category:
- [File Type Control](#audio-file-type-1487061)
- [DLP (Rule without content inspection)](#audio-file-type-dlp-1487061)
[]
These file types in the Image category are available when creating policy rules:
- Greenshot Files (.greenshot)
- High Efficiency Image Files (.heic, .heif)
- IMG (.img)
These file types are available for the following policies:
- [File Type Control](#image-file-type-1487061)
- [DLP (Rule without content inspection)](#image-dlp-file-1487061)
[]
These file types in the Other Microsoft category are available when creating policy rules:
- Microsoft Netmon Packet Capture File (.cap)
- Windows Registry HIVE files (.sam)
These file types are available for the following policies:
- [File Type Control](#other-microsoft-file-type-1487061)
- [DLP (Rule without content inspection)](#other-microsoft-dlp-file-1487061)
[]![Add new Archive File Type Control rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/archive-file-type.png)
[]![Add new file type to DLP rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/archive-file-type-dlp.png)
[]![Add new Audio File Type Control rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/audio-file-type.png)
[]![Add new file type to DLP rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/audio-file-type-dlp.png)
[]![Add new Image File Type Control rules](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/img-file-type.png)
[]![Add new file type to DLP rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/img-file-type-dlp.png)
[]![Add new Other Microsoft File Type Control rules ](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/other-microsoft-file-type.png)
[]![Add new Other Microsoft DLP file types](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/other-microsoft-file-dlp.png)

### Feature Available
#### NSS-to-Zscaler Cloud Connection DNS Resolution via Explicit Proxy
The NSS in explicit proxy mode can tunnel Zscaler cloud-bound connections without the need for internet-facing DNS resolution. To enable this capability, you can use the `dnsoverproxy` flag when configuring the NSS in explicit proxy mode.
To learn more, see [Configuring NSS in Explicit Proxy Mode](/zia/configuring-advanced-nss-settings#proxy).

### Feature Available
#### Traffic Capture When Policy Is Set to Allow
Traffic Capture is available for [IPS control](/zia/configuring-ips-control-policy) and [Advanced Threat Protection](/zia/configuring-advanced-threat-protection-policy) policies when the action is set to Allow.
To learn more, see [About Traffic Capture](/zia/about-traffic-capture).

### Feature Available
#### Update to Cloud Service API: Cloud App Control Policies API
The cloud service API includes the following new endpoints to create, modify, retrieve, and delete cloud app control policy rules:
- `GET /webApplicationRules/ruleTypeMapping`
- `GET /webApplicationRules/{rule_type}`
- `POST /webApplicationRules/{rule_type}`
- `POST /webApplicationRules/{rule_type}/availableActions`
- `POST /webApplicationRules/{rule_type}/duplicate/{ruleId}`
- `POST /webApplicationRules/{rule_type}/{ruleId}`
- `PUT /webApplicationRules/{rule_type}/{ruleId}`
- `DELETE /webApplicationRules/{rule_type}/{ruleId}`
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection has also been updated to include new and updated resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

## August 02, 2024
### Feature Available
#### New Cloud Applications
New cloud applications are added to the cloud application categories. You can download the list of newly added cloud applications to the respective categories: [Download](/sites/default/files/downloads/zia/documentation-knowledgebase/policies/cloud-apps/cloud-app-control-policies/cloud-app-categories/New-Cloud-Apps-July-2024.xlsx)
The risk index and risk attribute values for these new applications are visible only after they are available on all the clouds.

### Feature Available
#### Updates to Cloud Applications
As part of a continuous review, Zscaler has updated cloud applications across various cloud application categories. To obtain the list of cloud applications that have been updated, download the list: [Download](/sites/default/files/downloads/zia/documentation-knowledgebase/policies/cloud-apps/cloud-app-control-policies/cloud-app-categories/Updated-Cloud-Apps-July-2024.xlsx)
Cloud applications are updated in phases. Refer to the [trust post](https://trust.zscaler.com/zscaler.net/posts/19351) for details.

## August 01, 2024
### Feature Available
#### Enhancement to 3rd-Party App Governance for Okta
When an Okta app is installed multiple times on the same tenant, you can view the instance name next to the application name to further distinguish between different Okta app instances. You can also see the instance name on the App Panel Details tab.

## July 30, 2024
### Feature Available
#### Additional Print Options in Isolation for ZIA
More options are available for printing web pages and documents in Isolation.
To learn more, see [Transferring and Viewing Files in Isolation](/isolation/transferring-and-viewing-files-isolation).

## July 26, 2024
### Feature Available
#### Enhancement to HTTP Tunnel Control
You can block non-HTTP traffic on HTTP/HTTPS ports to restrict traffic to HTTP/HTTPS traffic only and prevent all other data types from being sent or received by going to Administration > Advanced Settings and enabling Block Non HTTP Traffic on HTTP/HTTPS Ports.
[See image.](#block-non-http-traffic-1507801)
To learn more, see [Configuring Advanced Settings](/zia/configuring-advanced-settings).
[]![Enable to Block non-HTTP Traffic on HTTP and HTTPS Ports](/sites/default/files/downloads/zia/policies/configuring-advanced-settings/block-non-http-traffic-on-http-ports.png)

### Feature Available
#### File Type Control & DLP Support for Base64-Encoded Files
The File Type Control and DLP policies support the decoding of Base64-encoded files to determine the original file type and to inspect file contents for sensitive data.
To learn more, see [About File Type Control](/zia/about-file-type-control) and [About Data Loss Prevention](/zia/about-data-loss-prevention).

### Feature Available
#### SD-WAN Partner API Roles and Clients Support for ZSLogin Admins
ZIdentity admins can create and view SD-WAN partner API clients and SD-WAN partner API roles in the ZIA Admin Portal.
Partner Administrator and Partner Administrator Role have been renamed to SD-WAN Partner API Client and SD-WAN Partner API Role, respectively.
To learn more, see [Adding SD-WAN Partner API Clients](/zia/adding-partner-admins) and [Adding SD-WAN Partner API Roles](/zia/adding-partner-admin-roles).

### Feature Available
#### Support for ZSTD Encoding Format
Zscaler proxy servers support the Zstandard (ZSTD) encoding. To learn more, refer to [RFC 8878: Zstandard Compression and the 'application/zstd' Media Type](https://www.rfc-editor.org/rfc/rfc8878). This encoding format is used majorly by websites, such as Meta, Instagram, and WhatsApp. Addition of this support helps Zscaler users to continue to inspect traffic from these websites without having to disable ZSTD on the browser.

## July 24, 2024
### Feature Available
#### Custom Browser EUN Templates for Cloud App Control & URL Filtering
You can create custom end user notification (EUN) templates for the Cloud App Control and URL Filtering features and associate them with the respective policy rules. This allows you to show the custom notification messages on the endpoints when the Cloud App Control Policy and URL Filtering rules are triggered. As part of this change, in the Cloud App Control Policy and URL Filtering rule windows, the Browser Notification Template field is added, which appears when the application access is set to block or caution.
[See image.](#browser-eun)
To learn more, see [Configuring Browser EUN Template](/zia/configuring-browser-eun-template), [Adding Rules to the Cloud App Control Policy](/zia/adding-rules-cloud-app-control-policy), and [Configuring the URL Filtering Policy](/zia/configuring-url-filtering-policy).
[]![Screenshot of ZIA Browser End User Notification Templates Window](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-End-User-Notifications-Browser-Templates-RN.png)
![Screenshot of ZIA Cloud App Control Policy rule window with Browser Notification Template](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Add-Cloud-App-Control-Rule-AI-ML-Browser-Notification-Template-RN.png)
![Screenshot of ZIA Add URL Filtering rule window with Browser Notification Template](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Add-URL-Filtering-Rule-Browser-Notification-RN.png)

### Feature Available
#### Zscaler Client Connector-Based EUN for Cloud App Control
The end user notification (EUN) is extended to Zscaler Client Connector. This allows you to show Zscaler Client Connector-based notification messages (custom or default) on the endpoints for the Cloud App Control feature. As part of this change, in the Cloud App Control Policy rule windows that support applications with granular actions, the following fields are added:
- End User Notification
- Custom Message
[See image.](#eun-cloud-app-granular-action)
To learn more, see [Configuring EUNs for Cloud App Control](/zia/configuring-euns-cloud-app-control) and [Adding Rules to the Cloud App Control Policy](/zia/adding-rules-cloud-app-control-policy).
You can customize the EUNs for Cloud App Control policy under Administration > End User Notifications > Client Connector. You can modify the default notification message and additionally create custom messages to allow the selection of different notification messages for individual Cloud App Control rules.
[See image.](#cloud-app-control-custom-eun)
To learn more, see [Configuring EUNs for Cloud App Control](/zia/configuring-euns-cloud-app-control) and [Configuring Settings for Client Connector-Based EUNs](/zia/configuring-settings-client-connector-based-euns).
[]![Screenshot of ZIA Cloud App Control Policy rule window with Client Connector-based notification for applications with granular actions](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Add-Cloud-App-Control-Rule-AI-ML-ChatGpt-Client-Connector-Notification-RN.png)
[]![Custom EUN for Cloud App Control Policy](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/cloud-app-control-custom-eun.png)

## July 19, 2024
### Feature Available
#### DSPM SSO Integration
A new option, Zscaler DSPM Portal, is now available under Dashboard and Policy. This option allows you to access the DSPM Admin Portal from the ZIA Admin Portal using SSO.
Contact Zscaler Support to configure the subscription for your tenant to include DSPM.
[See image.](#DSPM-SSO-Links)
To learn more, see [Accessing the DSPM Admin Portal using SSO.](/zia/accessing-zscaler-dspm-admin-portal-using-sso)
[]![Screenshot of DSPM SSO Links](/sites/default/files/downloads/zia/policies/ssl-inspection/configuring-ssl-inspection-policy/DSPM_SSO_Links.png)

### Feature Available
#### IoT Policy Control based on ML Classifications
You can apply URL Filtering and Cloud App Control Policy rules to IoT devices that are discovered and classified by the Zscaler AI/ML for locations or sub-locations that have Enforce IoT Policy Control option enabled. In the policy rules, all the IoT classifications supported by the Zscaler AI/ML are listed under the new IoT group in the Device Groups criterion.
This enhancement requires the IoT Discovery option enabled at the locations or sub-locations.
The predefined URL filtering and cloud app control policy rules (i.e., Allow Unauthenticated Traffic for IoT Classifications) provided by Zscaler can be enabled to temporarily allow unauthenticated traffic that could be blocked by other rules, so that Zscaler AI/ML can discover and classify devices.
As part of this enhancement, the following changes appear in the ZIA Admin Portal:
-
Added Enforce IoT Policy Control option in the Gateway Options section of the Add Location window (Administration > Location Management > Locations > Add Location) and Add Sub-Location window (Administration > Location Management > Locations > Add Sub-Location icon).
[See image.](#enforce-iot-control)
-
Added the IoT-Policy-Enable field to the Import CSV file in the Locations page (Administration > Location Management >Locations) to enforce IoT Policy Control for multiple locations or sub-locations.
[See sample field value for enforcing IoT Policy Control for multiple locations.](#multiple-locations-iot-policy)
-
Added IoT group to the Device Groups criterion in the URL Filtering Policy page (Policy > URL & Cloud App Control > URL Filtering Policy) and Cloud App Control Policy page (Policy > URL & Cloud App Control > Cloud App Control Policy).
[See image.](#iot-device-group)
-
Added the predefined rule, Allow Unauthenticated Traffic for IoT Classifications, to the URL Filtering Policy page and Cloud App Control Policy page.
[See image.](#predefined-rules)
To learn more, see [About Cloud App Control](/zia/about-cloud-app-control), [About URL Filtering](/zia/about-url-filtering), [Configuring Locations](/zia/configuring-locations), [Configuring Sub-Locations](/zia/configuring-sub-locations), and [Configuring Multiple Locations and Sub-Locations](/zia/configuring-multiple-locations-and-sub-locations).
[]+, Location, locationName1, 10.10.100.242, California, United States, America/San Francisco, Auth-Enable, XFF-Enable, Firewall-Enable, Bandwidth-Enable, 10, 100, SurrogateIP-Enable, 8Hours, FQDN, qwe@gsolanki1.com, Dedicated port,, vse1, vse2, SurrogateIP-Enforced-KnownBrowsers, 4Hours, GRE-Enable, AUP-Enable, 12Hours, ManagedBy, Group Name, aupBlockInternetAccess-Enable, aupForceSSLInspection-Enable, Caution-Enable, IPS-Enable, Exclude-Manual-Group, Exclude-Dynamic-Group, Kerberos-Enable, Digest-Auth-Enable, CORPORATE, This is a sample description for the location, Basic-Auth-Enable, IoT-Discovery-Enable, 5332748,,,, CookiesAndProxy-Enable, IoT-Policy-Enable
+, Location, locationName2, 10.10.100.244, California, United States, America/San Francisco, Auth-Enable, XFF-Enable, Firewall-Enable, Bandwidth-Enable, 10, 100, SurrogateIP-Enable, 8Hours, FQDN, qwe@gsolanki1.com, Dedicated port,, vse1, vse2, SurrogateIP-Enforced-KnownBrowsers, 4Hours, GRE-Enable, AUP-Enable, 12Hours, ManagedBy, Group Name, aupBlockInternetAccess-Enable, aupForceSSLInspection-Enable, Caution-Enable, IPS-Enable, Exclude-Manual-Group, Exclude-Dynamic-Group, Kerberos-Enable, Digest-Auth-Enable, CORPORATE, This is a sample description for the location, Basic-Auth-Enable, IoT-Discovery-Enable, 5332748,,,, CookiesAndProxy-Enable, IoT-Policy-Enable
+, Location, locationName3, 10.10.100.246, California, United States, America/San Francisco, Auth-Enable, XFF-Enable, Firewall-Enable, Bandwidth-Enable, 10, 100, SurrogateIP-Enable, 8Hours, FQDN, qwe@gsolanki1.com, Dedicated port,, vse1, vse2, SurrogateIP-Enforced-KnownBrowsers, 4Hours, GRE-Enable, AUP-Enable, 12Hours, ManagedBy, Group Name, aupBlockInternetAccess-Enable, aupForceSSLInspection-Enable, Caution-Enable, IPS-Enable, Exclude-Manual-Group, Exclude-Dynamic-Group, Kerberos-Enable, Digest-Auth-Enable, CORPORATE, This is a sample description for the location, Basic-Auth-Enable, IoT-Discovery-Enable, 5332748,,,, CookiesAndProxy-Enable, IoT-Policy-Enable
[]![Screenshot of ZIA Add URL Filtering Rule Page with IoT Device Group](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Add-URL-Filtering-Rule-Device-Groups.png)
[]![Screenshot of ZIA Add Location Page with Enforce IoT Policy Control](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Add-Location-Enforce-IoT-Policy-RN.png)
[]![Screenshot of ZIA URL Filtering Policy Page with Predefined IoT Rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-URL-Filtering-Policy-Page-IOT-Predefined-Rule.png)

### Feature Available
#### Update to Cloud Service API: Device Groups Endpoint
The `includeIOTGroups` parameter is added to the `/deviceGroups` endpoint of the cloud service API.
To learn more, see the [API Reference](/zia/understanding-cloud-service-and-sandbox-submission-apis).

## July 12, 2024
### Feature Available
#### Application Deep Linking for Isolation in ZIA
Zscaler's Isolation supports the ability for ZIA users to invoke a client application from the user's end machine via an isolated session. When a user clicks on a deep link within an isolated web page, the client application is invoked on the end user's machine. Admins can enable this feature per isolation profile, and can specify the URL scheme associated with the invoked client application. This provides the organization granular control over which client applications users can invoke from the isolated web pages.
If this feature is disabled for the isolation profile, or an application invoked by the user is not added to the application list in the isolation profile, the user sees an error message explaining that the application isn't allowed by policy.
To learn more, see [Creating Isolation Profiles for ZIA](/isolation/creating-isolation-profiles-zia).

### Feature Available
#### Votiro Secure File Gateway Integration with Isolation
Zscaler Isolation is integrated with Votiro CDR services for ZIA. The use of the Votiro Secure File Gateway to Disarm and Reconstruct Files means that files uploaded or downloaded through an isolated browser are based on the polices defined on Votiro. You can enable this functionality on ZIA isolation profiles to allow the file sanitization capability for users in Isolation.
To learn more, see [Zscaler and Votiro Deployment Guide](/zscaler-technology-partners/zscaler-and-votiro-deployment-guide) and [Creating Isolation Profiles for ZIA](/isolation/creating-isolation-profiles-zia).

## July 10, 2024
### Feature Available
#### Enhancements to Endpoint DLP
The following enhancements are available in Endpoint DLP:
- Customized end user notification (EUN) and confirmation messages
- On Endpoint DLP policy rules, a new Protect action encrypts files copied to removable storage devices so that the files can be safely shared only within an organization.
- Support in macOS for the Block action for the Network Share channel on Endpoint DLP policy rules
- Support Shift JIS Encoding for extracting Japanese text from files
- Added support for the following predefined DLP dictionaries:
- Australia Passport Number
- Diseases Information
- Drugs Information
- National Health Index Number (New Zealand)
- National Provider Identifier
- NDC Number (Package)
- NDC Number (Product)
- Social Security Number (Austria)
- Tax Identification Number (Finland)
- Tax Identification Number (Greece)
- Tax Identification Number (Ireland)
- Tax Identification Number (Peru)
- Tax Identification Number (Poland)
- Tax Identification Number (Spain)
- Tax Identification Number (US)
- Treatments Information
- VAT Number (Ireland)
To learn more, see [About Client Connector-Based End User Notifications](/zia/about-client-connector-based-end-user-notifications), [Configuring User Confirmation Notification Templates](/zia/configuring-user-confirmation-notification-templates), [Configuring Endpoint DLP Policy Rules](/zia/configuring-endpoint-dlp-policy-rules), and [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).

### Feature Available
#### Outbound Email Data Loss Prevention
You can use Zscaler Outbound Email Data Loss Prevention (DLP) policies to prevent the exfiltration of sensitive data by enforcing policy rules on email content sent to external domains, including content in subject lines, body text, and attachments. As a part of your larger DLP strategy, Zscaler Outbound Email DLP lets you use the same DLP policy tools that you already use across other channels (i.e., Inline Web DLP, Endpoint DLP, and SaaS Security API DLP), eliminating the need for different DLP point solutions and the operational overhead involved in maintaining those solutions. Additionally, you can monitor outbound email activity with dashboards and reports, and NSS feeds.
Zscaler Outbound Email DLP includes enhancements to the following areas:
- [Outbound Email Rules and Resources](#outbound-email-dlp-rules)
- [Outbound Email DLP NSS Feeds and Logs](#outbound-email-dlp-nss)
- [Outbound Email DLP Dashboards, Reports, and Logs](#outbound-email-dlp-dashboards)
To learn more about setting up Zscaler Outbound Email DLP for your organization, see [Step-by-Step Configuration Guide for Zscaler Outbound Email DLP](/zia/step-step-configuration-guide-zscaler-outbound-email-dlp).
[]Using connectors and mail flow rules configured on the Exchange server, the Zscaler smart host receives, inspects, and returns email from Exchange. After the Zscaler smart host inspects email content for sensitive data, it adds headers that define DLP actions to emails that trigger outbound email policy. When the Exchange server receives inspected email from the Zscaler smart host, it uses those headers to determine enforcement actions.
Configuring the Zscaler smart host in the ZIA Admin Portal involves setting up the following:
- [Email tenants](#email-tenants)
- [Email profiles](#email-profiles)
- [Outbound email policy rules](#policy-rules)
[]Email tenants (Administration > Email Tenants) let you specify which tenants use the Zscaler smart host.
[See image.](#email-tenants-screenshot)
[]![Email Tenants Page in ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Email-Tenants-RN.png)
[]Email profiles (Administration > Email Profiles) let configure domain and recipient profiles to control your outbound email policy at a granular level.
[See image.](#email-profiles-screenshot)
[]![Email Profiles Page in ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Email-Profiles-RN.png)
[]You can use outbound email policy rules (Policy > Outbound Email Policy) to detect data, allow or block activities, and add custom headers when an email sent to an external domain contains sensitive content. You can also create exception rules, which are child rules that allow you to exclude specific users or groups in your organization that must perform tasks as part of a necessary workflow that might otherwise violate outbound email policy.
[See image.](#email-policy-rules-screenshot)
[]![Outbound Email Policy Page in ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Email-Policy-Rules-RN.png)
[]A new log type, Email DLP, is available for the Nanolog Streaming Service (NSS). You can configure an NSS feed or Cloud NSS feed to stream Email DLP log data from ZIA to your security information and event management (SIEM) system.
[See image.](#img-outbound-email-dlp-nss)
To learn more, see [Adding NSS Feeds for Email DLP Logs](/zia/adding-nss-feeds-email-dlp-logs), [Adding Cloud NSS Feeds for Email DLP Logs](/zia/adding-cloud-nss-feeds-email-dlp-logs), and [NSS Feed Output Format: Email DLP Logs](/zia/nss-feed-output-format-email-dlp-logs).
[]The following pages are added to monitor and view logs for the Email DLP activities:
- Email DLP Insights (Analytics > Email DLP Insights > Insights)
- Email DLP Insights Logs (Analytics > Email DLP Insights > Logs)
- Email DLP Report (Analytics > Email DLP Report)
- Email DLP Dashboard (Dashboard > Email DLP)
To learn more, see [Email DLP Insights Logs: Filters](/zia/email-dlp-insights-logs-filters), [Email DLP Insights Logs: Columns](/zia/email-dlp-insights-logs-columns), [Email DLP Data Types and Filters](/zia/email-dlp-data-types-and-filters), [About Email DLP Report](/zia/about-email-security-report), and [About Dashboards](/zia/about-dashboards).
[]![Email DLP Log Type in Add NSS Feed window in ZIA Admin Portal](/sites/default/files/downloads/img-outbound-email-dlp-nss.png)

## July 03, 2024
### Feature Available
#### Zscaler Custom EUN Messages for Inline Web DLP
Data Loss Prevention (DLP) policy rules support Zscaler Client Connector-based end user notification (EUN) messages when user activity triggers a policy rule on an endpoint. When configuring DLP policy rules, you can select to Show or Hide an EUN message on endpoints when content triggers the DLP policy rule. If you select Show, you can specify the custom EUN message that appears when the rule is triggered.
[See image.](#unified-eun-dlp)
To learn more, see [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection), [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection), and [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled).
You can customize the EUNs for DLP policy rules under Administration > End User Notifications > Client Connector. You can modify the default notification message and additionally create custom messages to allow the selection of different notification messages for individual DLP rules.
[See image.](#inline-web-dlp-custom-eun)
To learn more, see [Configuring EUNs for Inline Web DLP](/zia/configuring-euns-inline-web-dlp) and [Configuring Settings for Client Connector-Based EUNs](/zia/configuring-settings-client-connector-based-euns).
[]![ZIA Inline Web DLP Policy rule window with Client Connector-based EUN option](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-DLP-Unified-EUN-Policy-Rule-RN.png)
[]![Inline Web DLP custom EUN message](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/inline-web-dlp-custom-eun.png)

## June 28, 2024
### Feature Available
#### Additional Compliance Support for Microsoft 365 SaaS Security Posture Management Policies
The Microsoft 365 tenants comply with CIS Microsoft 365 v3.0 in addition to the existing list of compliances for the SaaS Security Posture Management (SSPM) policies.
[See image.](#sspm-complaince-m365)
To learn more, see [Understanding the SaaS Security Posture Policy](/zia/configuring-saas-security-posture-control-policy) and [SaaS Security Posture Report](/zia/about-saas-security-posture-report).
[]![The compliance list for Microsoft 365 tenants.](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/understanding-saas-security-posture-management-policy/SSPM-Compliance-M365.png)

### Feature Available
#### DLP Support for Microsoft Access DB Files
The DLP policy supports Microsoft Access files (.accdb) in the Database category.
[See image.](#access-db-files-dlp-support-rn)
To learn more, see [About Data Loss Prevention](/zia/about-data-loss-prevention).
[]![Selecting the Access DB File Type for a DLP Policy](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Access-DB-File-Types-dlp-RN.png)

### Feature Available
#### Enhancement to Custom URL Category
From the Review Matches drop-down menu, you can see if either the URLs or wildcard domains added to a custom URL category match any other custom categories with either the corresponding wildcard or a specific match, respectively. Choose a matching custom category from the drop-down menu if you want to add the URLs or wildcard domains to it. This menu is added to the Administration > URL Categories > Add or Edit URL Category window.
[See image.](#url-category-review-matches)
To learn more, see [Configuring Custom URL Categories](/zia/configuring-custom-url-categories).
Update to Cloud Service API
The cloud service API includes a new `/urlCategories/review/domains` endpoint to find matching entries for URLs in existing custom URL categories. This helps you identify similar URLs to group-related entries in a single category. This endpoint can be accessed using POST and PUT methods.
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection has also been updated to include the new resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).
[]![ZIA-Add-URL-Category-Review-Matches-RN.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Add-URL-Category-Review-Matches-RN.png)

### Feature Available
#### Enhancement to URL Filtering Policy Rule
The URL filtering policy rules support pairing of URL categories. You can create rules with an `AND` logic between categories to block specific combination of URL categories and avoid false positives. As part of this change, in the Add/Edit URL Filtering Rule window (Policy > URL & Cloud App Control > URL Filtering Policy > Add/Edit URL Filtering Rule), when the Add icon next to the URL Categories field is clicked, an additional URL Categories field appears with an `AND` logic between the fields.
[See image.](#additional-url-cat-add-icon)
To learn more, see [Configuring the URL Filtering Policy](/zia/configuring-url-filtering-policy).
Update to Cloud Service API
The `UrlFilteringRule` model (object) within the cloud service API has also been updated to include the `urlCategories2` parameter. This allows you to trigger URL Filtering policy rules when the service matches the selected categories in both the `urlCategories` and `urlCategories2` fields.
To learn more, see [API Reference](/zia/understanding-cloud-service-and-sandbox-submission-apis).
[]![Screenshot of ZIA Add URL Filtering Rule Page with Add Icon](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-URL-Filtering-Policy-Page-With-Add-Icon-RN.png)
![Screenshot of ZIA Add URL Filtering Rule Page with Two URL Categories](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-URL-Filtering-Policy-Page-Two-URL-Categories-RN.png)

### Feature Available
#### Expanded Onboarding Options for Google Applications
The Zscaler service supports custom, client-side connector onboarding for access to Gmail, Google Drive, and Google Workspace. With this functionality, instead of requiring full administrator credentials, the Zscaler service can use a minimum set of credentials to access these Google applications.
When onboarding these Google applications as application tenant (Administration > SaaS Application Tenants), you can configure a Custom SaaS Connector by uploading the Private Key JSON file so that the Zscaler service can access the application.
[See image.](#Google_Custom_RN)
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants) and [Authorizing a Custom Zscaler Connector for Google Applications](/zia/authorizing-custom-zscaler-connector-google-applications).
[]![New Custom Onboarding for Google Applications](/sites/default/files/downloads/zia/RN_Google.png)

### Feature Available
#### Expanded Onboarding Options for Google Cloud Platform
The Zscaler service supports custom, client-side connector onboarding for access to Google Cloud Platform (GCP). With this functionality, instead of requiring full administrator credentials, the Zscaler service can use a minimum set of credentials to access GCP.
When onboarding GCP as an application tenant (Administration > SaaS Application Tenants), you can configure a Custom SaaS Connector, using the Quarantine Bucket name (for Read Write selection only), Organization ID, and upload the Private Key JSON file so that the Zscaler service can access the application.
[See image.](#GCP_Custom_RN)
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants) and [Authorizing a Custom Zscaler Connector for Google Applications](/zia/authorizing-custom-zscaler-connector-google-applications).
[]![Custom Connector functionality for Google Cloud](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/authorizing-custom-zscaler-connector-google-applications-doc-50840/RN_GCP_Custom.png)

### Feature Available
#### Expanded SaaS Application Categories
When viewing or onboarding application tenants (Administration > SaaS Application Tenants), you can view the Owner category to indicate whether the SaaS application tenant was created in Zscaler Internet Access (ZIA) or Zscaler Digital Experience (ZDX).
[See image.](#ziazdxrn)
To learn more, see [About SaaS Application Tenants](/zia/about-saas-application-tenants).
[]![Owner category in the SaaS Application Tenants page](/sites/default/files/downloads/zia/release-notes/zia%20zdx%20RN.png)

### Feature Available
#### Logs for Threat Severity and Threat Score
You can filter and view logs for different threat severities and threat scores. As part of the update, the following changes are available in the ZIA Admin Portal:
Firewall Insights Logs
A filter and column, Threat Severity, and a column Threat Score are added to Firewall Insights Logs.
[See image.](#img_threat-score-threat-severity-insights-logs)
To learn more, see [Firewall Insights Logs: Columns](/zia/firewall-insights-logs-columns) and [Firewall Insights Logs: Filters](/zia/firewall-insights-logs-filters).
NSS Feeds
The fields `%d{threat_score}` and `%s{threat_severity}` are available when adding an NSS or Cloud NSS feed for firewall logs.
[See image.](#img-nss-threat-score-threat-severity)
To learn more, see [NSS Feed Output Format: Firewall Logs](/zia/nss-feed-output-format-firewall-logs).
[]![zia-nss-fw-threat-score-threat-severity.png](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/nss/nss-feeds/formatting-nss-feeds/nss-feed-output-format-firewall-logs/zia-nss-fw-threat-score-threat-severity.png)
[]![This image shows the Threat Severity and Threat Score columns and filter in the Firewall Insights Logs](/sites/default/files/downloads/Threat_score_threat_severity_logs.png)

### Feature Available
#### New File Type Support for File Type Control and DLP Policies
The File Type Control and Data Loss Prevention (DLP) policies now support the following file types:
- CATIA files (.catpart, .catproduct, .catdrawing, .3dxml)
- Certificate files (.pfx)
The .pfx file type was already supported by the Zscaler service. This update is strictly a UI change to indicate support for both .p12 and .pfx certificate files.
- Greenshot files (.greenshot)
- KeePass Password Manager files (.kdbx)
- OneNote file types (.one, .onetoc, .onetoc2, .onesrvcache, .onecache, .onepkg)
- PGP Encrypt File (.pgp)
- XZ Utils (.xz)
The file types are available when creating File Type Control and DLP policies in the following categories:
- [Archive](#archive-1487921)
- [Database](#database-1487921)
- [Image](#image-1487921)
- [Other Documents](#otherdoc-1487921)
- [Other Microsoft](#other_microsoft-1487921)
To learn more, see [About File Type Control](/zia/about-file-type-control) and [About Data Loss Prevention](/zia/about-data-loss-prevention).
[]
The XZ Utils (.xz) file type is available when creating the following policies in the Archive category:
- [File Type Control](#archive-file-type-1487921)
- [DLP (Rule without content inspection)](#archive-dlp-files-1487921)
[]
The KeePass Password Manager (.kdbx) file type is available when creating the following policies in the Database category:
- [File Type Control](#database-file-type-1487921)
- [DLP (Rule without content inspection)](#database-dlp-files-1487921)
[]
The Greenshot (.greenshot) file type is available when creating the following policies in the Image category:
- [File Type Control](#image-file-type-1487921)
- [DLP (Rule without content inspection)](#image-dlp-files-1487921)
[]
- CATIA files (.catpart, .catproduct, .catdrawing, . 3dxml)
- Certificate files (.pfx)
- PGP Encrypt File (.pgp)
These file types are available for the following policies in the Other Document category:
- [File Type Control](#other-documents-file-type-1487921)
- [DLP (Rule without content inspection)](#other-documents-dlp-files-1487921)
[]
These OneNote file types (.one, .onetoc, .onetoc2, .onesrvcache, .onecache, .onepkg) are available when creating the following policies in the OneNote category:
- [File Type Control](#other-microsoft-ftc-1487921)
- [DLP (Rule without content inspection)](#other-microsoft-dlp-files-1487921)
[]![Add new Archive File Type Control rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/xz-file-type-control.png)
[]![Add new Archive DLP rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/archive-file-dlp.png)
[]![Add new Database File Type Control rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/kdbx-file-type-control.png)
[]![Add new Database DLP rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/kdbx-file-dlp.png)
[]![Add new Image File Type Control rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/greenshot-file-type-control.png)
[]![Add new Image DLP rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/greenshot-file-dlp.png)
[]![Add new Other Documents File Type Control rules ](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/catia-pgp-pfx-file-types.png)
[]![Add new Other Documents files to DLP policy](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/catia-pgp-pfx-dlp-files.png)
[]![Add new Other Microsoft File Type Control rules](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/onenote-file-types.png)
[]![Add Other Microsoft file type](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/OneNote-dlp-file-types.png)

### Feature Available
#### New IPS Threat Category
A new predefined IPS threat category, Risky Behaviors, has been added to IPS Control to include IPS signatures that are considered risky but might have some legitimate usage. Organizations have the flexibility to exclude this threat category from being blocked for users by creating a higher order IPS rule with the Risky Behaviors threat category as a condition and the action set to Allow or Bypass IPS.
[See image.](#IPS-control-rule-risky-behaviors-criteria)
Traffic matches with the Risky Behaviors criteria in IPS Control rules are recorded in Firewall Logs (Analytics > Firewall Insights > Logs) and can be filtered using the new Risky Behaviors option under the Advanced Threat Category filter.
[See image.](#firewall-logs-risky-behaviors-filter)
To learn more, see [About Threat Categories](/zia/about-threat-categories), [Configuring IPS Control Policy](/zia/configuring-ips-control-policy), and [Firewall Insights Logs: Filters](/zia/firewall-insights-logs-filters).
[]![A screenshot of an IPS Control rule configured with the Risky Behaviors criteria](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/IPS-rule-risky-behaviors-condition.png)
[]![A screenshot of firewall logs filtered using the Risky Behaviors advanced threat category filter](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/firewall-logs-risky-behaviors-threat-category.png)

## June 21, 2024
### Feature Available
#### AppTotal Renamed to 3rd-Party App Governance
In line with the Zscaler product naming convention, AppTotal is now 3rd-Party App Governance.

### Feature Available
#### Changes in How You Access the ZIA Admin Portal
Signing in to the ZIA Admin Portal is now a two-step process. After you enter your login ID, the Zscaler service checks if ZIdentity is enabled for your account or not.
Based on the outcome, the Zscaler service either redirects you to the ZIdentity authentication page, where you can authenticate using your ZIdentity credentials or the Zscaler service shows a password page to enter your ZIA Admin Portal password for authentication.
[See image.](#login-page)
To learn more, see [Accessing and Navigating the ZIA Admin Portal](/zia/accessing-and-navigating-zia-admin-portal).
![ZIA Admin Portal login page.](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/accessing-and-navigating-zia-admin-portal-draft/ZIA-6.2r-Sign-In-Page.png)
[]

### Feature Available
#### Support for File Name Inspection in Inline Web DLP Policy
File names for all supported files are included as part of the text content that is extracted for inspection by Zscaler Data Loss Prevention (DLP) engines. As a result, your inline web DLP policy now detects sensitive information included in file names (e.g., social security numbers, specific keywords, etc.).
File names for password-protected files are not extracted for inspection by DLP engines.
To learn more, see [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection) and [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled).

## June 12, 2024
### Feature Available
#### Identifying Managed Devices When Configuring Zscaler Identity Proxy
A new option, Is Device Managed Attribute True, can be enabled to identify managed devices when configuring Zscaler Identity Proxy for ZIdentity-enabled tenants.
[See image.](#is-device-managed)
Additionally, the existing options, Proxied via Zscaler and Proxied via Zscaler with IdP Attribute, for tenants without ZIdentity are merged into a single option called Device Trust Attribute Matches the Configured Value.
[See image.](#device-trust-attribute)
To learn more, see [Configuring the Zscaler Identity Proxy for Cloud Apps](/zia/configuring-zscaler-identity-proxy-cloud-apps).
![Is Device Managed Attribute True Button in the Configuring Identity Proxy for Cloud Apps](/sites/default/files/downloads/zia/dashboard-analytics/reports/about-email-security-report/ZIA6.2r-Is-Managed-Device-Attribute-True-Option-for-ZSLogin-Tenants.png)
[]
![Device trust Attribute Matches the Configured Value Button in the Configuring Identity Proxy for Cloud Apps](/sites/default/files/downloads/zia/dashboard-analytics/reports/about-email-security-report/ZIA6.2r-Device-Trust-Attribute-Option.png)
[]

## June 05, 2024
### Feature Available
#### View Logs for Tenant Restricted Transactions
A new Policy Action filter option, Blocked - Tenant Restricted, is added to the Web Insights Logs for you to filter blocked transactions because of [Tenancy Restriction ](/zia/about-tenant-profiles)policies.
[See image.](#blocked-restricted)
To learn more, see [Web Insights Logs: Filters](/zia/web-insights-logs-filters) and [Policy Reasons](/zia/policy-reasons).
[]![Web Insights Logs Page](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA6.2r-blocked-restricted.png)

## June 03, 2024
### Feature Available
#### Enhancement to 3rd-Party App Governance Policy Engine
The policy engine has been enhanced so that it is triggered when you reinstall an app. You should consider adding the App Status filter when creating custom views to be used in policies, so if an app is reinstalled, the policy will be triggered again.
To learn more, see [3rd-Party App Governance Policies](/zia/apptotal-policies).

### Feature Available
#### Enhancements to 3rd-Party App Governance Processing Engine
The processing engine has been enhanced so that the data integrity for both contextual and non-contextual third-party apps is improved. As a result, you can see limited changes to some of the apps' permissions, risk score, and metadata such as category, description, origin, logo URL, privacy policy, terms of service, consent screenshot, etc.

### Feature Available
#### Stability and Performance Improvements in 3rd-Party App Governance
Multiple enhancements have been made to improve the stability and overall performance of 3rd-Party App Governance.

## May 03, 2024
### Feature Available
#### Enhancement to GitHub Instance Type
The organizations that follow similar naming convention through a single keyword can use the newly added keyword instance identifier to identify a large number of GitHub repositories. As part of this change, in the Administration > Cloud Applications > Instances > Add/Edit Cloud Application Instance page, for the GitHub instance type, the Keyword instance identifier is added in addition to URL. You can create GitHub instances with both the URLs and keywords as instance identifiers.
[See image.](#cloud-application-instance-github)
To learn more, see [Adding a Cloud Application Instance](/zia/adding-cloud-application-instance).
[]![ZIA-Add-Cloud-Application-Instance-GitHub-RN.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Add-Cloud-Application-Instance-GitHub-RN.png)

### Feature Available
#### Enhancements to Inspecting ZPA Application Segment Traffic
A new option, ZPA Microtunnels (M-Tunnels), is added under the Traffic Forwarding filter on the Web Insights Logs and Firewall Insights Logs to capture the traffic forwarded to Zscaler Private Access (ZPA) through the ZIA Inspected ZPA Apps forwarding rule.
[See image.](#TF-filter-image)
To learn more, see [Web Insights Logs: Filters](/zia/web-insights-logs-filters), [Firewall Insights Logs: Filters](/zia/firewall-insights-logs-filters), and [Configuring Forwarding Policy](/zia/configuring-forwarding-policy).
[]![Screenshot of the ZPA Microtunnels (M-tunnels) option in Traffic Forwarding filter in Web and Firewall Insights Logs](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-RN-web-firewall-insights-logs-M-tunnel-filter.png)

### Feature Available
#### Expanded Onboarding Options for Microsoft Applications
The Zscaler service supports custom, client-side connector onboarding for access to Microsoft applications. With this functionality, instead of requiring full administrator credentials, the Zscaler service can use a minimum set of credentials to access your Microsoft applications.
When onboarding a Microsoft SaaS application tenant (Administration > SaaS Application Tenants), you can configure a Custom SaaS Connector, using the Client ID, Client Secret, and Tenant ID, as well as add role assignments (Azure Blob Storage only) so that the Zscaler service can access the application.
[See image.](#saas-app-tenant-ms-custom-onboarding-rn)
The Zscaler service supports custom onboarding options for the following Microsoft SaaS applications:
- Azure Blob Storage
- Exchange
- OneDrive
- SharePoint
- Teams
To learn more see, [Authorizing a Custom Zscaler Connector for Microsoft Applications](/zia/authorizing-custom-zscaler-connector-microsoft-applications) and [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
Additionally, when adding a Microsoft Information Protection (MIP) account (Administration > Labels and Tags > Microsoft Information Protection (MIP) Labels), you can use the same options to configure a Custom SaaS Connector so that the Zscaler service can access your MIP labels on Microsoft servers.
[See image.](#mip-ms-custom-onboarding-rn)
To learn more, see [Adding an MIP Account](/zia/adding-mip-account).
[]![Screenshot of SaaS Application Tenant Onboarding Page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-SaaS-Application-Tenant-Custom-Connector-RN.png)
[]![Screenshot of Add MIP Account Page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-MIP-Account-Custom-Connector-RN.png)

### Feature Available
#### Filter and View Tags for Apps in the Shadow IT Report
You can filter the Shadow IT Report for specific tags and view the tag assigned to applications in the Clouds Applications table.
[See image.](#tags-img)
To learn more, see [About Shadow IT Report](/zia/about-shadow-it-report).
![Tags filter and column in the Shadow IT Report](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/about-shadow-it-report-draft-50406/ZIA-6.2r-tags-fitler-column.png)
[]

### Feature Available
#### New File Type Support for File Type Control & DLP
The File Type Control and Data Loss Prevention (DLP) policies support the following categories:
- [Other Documents](#other-docs-1475446)
- [Source Code](#source-files-1475446)
- [Other Microsoft](#other-microsoft-1475446)
- [Database](#database-1475446)
To learn more, see [About File Type Control](/zia/about-file-type-control) and [About Data Loss Prevention](/zia/about-data-loss-prevention).
[]
- ICS files
- HBS files (.hbs)
- VDA files (.vda)
- ACIS files (.sat)
- PS2 files (.ps2)
- PS3 files (.ps3)
- PRT files (.prt)
- Parasolid files (.x_b, .x_t)
- IGS files (.igs, .iges)
- draw.io files (.drawio)
- TMP files (.tmp)
- MUI files (.mui)
These file types in the Other Documents category are available for the following policies:
- [File Type Control](#ft-other-docs-1475446)
- [DLP (Rule without content inspection)](#dlp-other-docs-1475446)
[]
- Export files (.exp)
- TLB files (.tlb)
- ASHX files (.ashx)
These file types in the Source Code category are available for the following policies:
- [File Type Control](#source-code-ft-1475446)
- [DLP (Rule without content inspection)](#dlp-source-code-1475446)
[]
- Microsoft Catalog file (.cat)
- OneNote files (.onetoc2)
These file types in the Other Microsoft category are available for the following policies:
- [File Type Control](#ft-othermicrosoft-1475446)
- [DLP (Rule without content inspection)](#dlp-other-microsoft-1475446)
[]
- Virtual Hard Disk files (.vmdk)
- SDB files (.sdb)
These file types in the Database category are available for the following policies:
- [File Type Control](#database-ft-1475446)
- [DLP (Rule without content inspection)](#dlp-database-window-1475446)
[]![Screenshot of Add File Type Control Rule window for selecting new file types in the Other Documents Category](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-FT-Other-Documents-RN.png)
[]![Screenshot of Add DLP Rule window for selecting new file types in the Other Documents category](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-DLP-Other-Documents.png)
[]![Screenshot of Add File Type Control window for selecting new file types in the Source Code category](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-FT-Source-Code-RN.png)
[]![Screenshot of Add DLP Rule window for selecting new file types in the Source Code category](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-DLP-Source-Code-RN.png)
[]![Add new File Type Controls in the Other Microsoft Category](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/add-FTC-rule-other-microsoft.png)
[]![Add DLP rules to the Other Microsoft Category](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/add-DLP-rule-other-microsoft.png)
[]![Screenshot of Add File Type Control window for selecting new file types in the Database category](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-FT-Database-RN.png)
[]![Screenshot of Add DLP Rule window for selecting new file types in the Database category](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-DLP-Database-RN.png)

### Feature Available
#### Support for Data Center Exclusion Based on Traffic Forwarding Method
You can disable all tunnels terminating at a virtual IP (VIP) address of a Zscaler data center (DC) directly from the ZIA Admin Portal, triggering a failover from primary to secondary tunnels in the event of service disruptions, [Zscaler Trust Portal](https://trust.zscaler.com/) incidents, disasters, etc. This capability is supported by excluding DCs from service based on the traffic forwarding method (e.g., IPSec VPN tunnels).
As part of this feature, a new page, Traffic Forwarding Method, is added to the Administration > Resources menu in the ZIA Admin Portal. On the Traffic Forwarding Method page, you can add, edit, and delete DC exclusions.
[See image.](#img-zia-traffic-forwarding-method)
To learn more, see [About Data Center Exclusion Based on Traffic Forwarding Method](/zia/about-data-center-exclusion-based-traffic-forwarding-method%20) and [Excluding a Data Center Based on Traffic Forwarding Method](/zia/excluding-data-center-based-traffic-forwarding-method%20).
Updates to Audit Logs, Role Management, Tunnel Insights Logs, and NSS
After you activate the DC exclusion, existing tunnels to the excluded DC are brought down immediately and logs from the event are generated for audit and troubleshooting purposes.
- [View the list of updates.](#zia-dc-exclusion-updates)
To learn more, see: [About Audit Logs](/zia/about-audit-logs), [Adding Admin Roles](/zia/adding-admin-roles#traffic-forwarding%20), [Tunnel Insights Logs: Columns](/zia/tunnel-insights-logs-columns%20), and [NSS Feed Output Format: Tunnel Logs](/zia/nss-feed-output-format-tunnel-logs).
-
[]The category **DC Exclusion** and the subcategory **Traffic Forwarding Method** are added to the Audit Logs page (Administration > Audit Logs) to view the audit logs related to DC exclusion.
[See image.](#img-zia-audit-logs-categories-subcategories)
-
The feature **Subclouds & DC Exclusion** is available under the Traffic Forwarding functional scope for admin roles configured on the Role Management page (Administration > Role Management).
[See image.](#img-zia-admin-role-traffic-forwarding)
- The value `Org excluded from DC` populates under the Event Reason column on the Tunnel Insights Logs page (Analytics > Tunnel Insights) when a tunnel is brought down due to DC exclusion.
- The value `ORG_EXCLUDED` populates under the Nanolog Streaming Service (NSS) field `%s{eventreason}` when a tunnel is brought down due to DC exclusion.
[]![Screenshot of the Traffic Forwarding Method page in the ZIA Admin Portal](/sites/default/files/downloads/zia/traffic-forwarding/excluding-data-center-based-traffic-forwarding-method/zia-traffic-forwarding.png)
[]![Screenshot of the Audit Logs page in the ZIA Admin Portal](/sites/default/files/downloads/zia/traffic-forwarding/excluding-data-center-based-traffic-forwarding-method/zia-audit-logs-categories-subcategories.png)
[]![Screenshot of the Add Administrator Role window in the ZIA Admin Portal](/sites/default/files/downloads/zia/traffic-forwarding/excluding-data-center-based-traffic-forwarding-method/zia-admin-role-traffic-forwarding.png)

### Feature Available
#### Update to Cloud Service API
The `/dlpDictionaries` endpoints within the cloud service API have been updated to support two new attributes, `dictionaryCloningEnabled` and `customPhraseSupported`, that indicate whether the cloning option and custom phrases are supported for a predefined DLP dictionary respectively. Earlier, these options were configured implicitly using the `proximityLengthEnabled` field. The new attributes are included in the `DlpDictionaryDom` model.
To learn more about each attribute, see the [API Reference](/zia/about-api).

## April 26, 2024
### Feature Available
#### Basic Authentication Exemption
When configuring [Advanced Settings](/zia/configuring-advanced-settings) in the ZIA Admin Portal, you can exempt specific [URL categories](/zia/about-url-categories), [cloud app categories](/zia/understanding-cloud-app-categories), or specific cloud apps from Basic Authentication.
This feature is not enabled by default. To have this feature enabled for your organization, contact your Zscaler Account team.
[See image.](#basic-auth-exemptions)
A maximum of 25K URLs (across all categories) and 64 categories can be exempted. To learn more, see [Ranges & Limitations](/zia/ranges-limitations).
[]![Image of the Basic Authentication Exemptions section in the Advanced Settings of the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-basic-auth-exemptions.png)

## April 19, 2024
### Feature Available
#### Additional SaaS Security Posture Management Policy Support for Microsoft 365
The Zscaler posture management allows you analyze your organization's security posture based on your requirements. You can now configure additional SaaS Security Posture Management (SSPM) policies for Microsoft 365 tenants. Select the SSPM checkbox when onboarding a Microsoft 365 tenant to enable the SSPM scan capability for the specific tenant. Existing users should reauthorize and validate the onboarded tenant to leverage the additional SSPM policies for Microsoft 365.
To use the full functionality of the SSPM policies, it is recommended to use Zscaler-defined SaaS connectors only. To view the list of SSPM policies for Microsoft 365 tenants, see [Configuring the SaaS Security Posture Policy](/zia/configuring-saas-security-posture-control-policy).
[See image.](#sspm-m365-powershell)
To learn more, see [Configuring the SaaS Security Posture Policy](/zia/configuring-saas-security-posture-control-policy) and [SaaS Security Posture Report](/zia/about-saas-security-posture-report).
[]![The onboarding page allows you to select the SSPM Scan checkbox to enable SSPM capabilities for Microsoft 365 PowerShell tenants.](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-security-activities-report/M365%20PowerShell%20Onboarding.png)

### Feature Available
#### Enhancement to URL Categories
The following updates are available on the URL Categories page (Administration > URL Categories):
- Added the following new predefined URL categories:
- File Convertors to the Information Technology super category.
- General AI and ML Applications to the Information Technology super category.
- Insurance to the Business and Economy super category.
- Renamed the following URL categories:
- AI and ML Applications to Generative AI and ML Applications.
- Online Trading, Brokerage, Insurance to Online Trading and Brokerage.
To learn more, see [About URL Categories](/zia/about-url-categories).
After the cloud upgrade, these URL categories will be displayed within the ZIA Admin Portal. These categories are in preview at this time and are not yet available for use in implementing your policies. These categories will become available for setting and enforcing policies after all Zscaler clouds have been upgraded. A follow-up notification will be sent at that time.

### Feature Available
#### IBM SmartCloud in Tenant Profile
The Tenant Profiles feature is extended to the IBM SmartCloud application. This allows you to provide access to certain IBM accounts.
[See image.](#IBM-smart-cloud-tenant-profile)
To learn more, see [Adding Tenant Profiles](/zia/adding-tenant-profiles).
[]![ZIA-Add-Tenant-Profile-IBM%20SmartCloud.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Add-Tenant-Profile-IBM%20SmartCloud.png)

### Feature Available
#### Interactive Isolation Reports in ZIA
The ZIA Admin Portal has a section for interactive reports with Isolation data. The Interactive Isolation Reports consist of data for for Consumption, Isolation Traffic Summary Overview, Security Overview, and File and Document in Isolation.
To find the Interactive Isolation Reports, go to Analytics > Interactive Reports > Standard Reports > Browser Isolation.
To learn more, see [Isolation Reports in the ZIA Admin Portal](/isolation/isolation-reports-zia-admin-portal) and [About Interactive Reports](/zia/about-interactive-reports).
[See image.](#Isolation_reports)
[]![Analytics_Interactive-Reports_Standard%20Reports_Browser%20Isolation_squircle.png](/sites/default/files/downloads/isolation/getting-started/Analytics_Interactive-Reports_Standard%20Reports_Browser%20Isolation_squircle.png)

### Feature Available
#### New Cloud Applications
New cloud applications are added to the cloud application categories in the Cloud App Control policy. You can download the list of newly added cloud applications to the respective categories: [Download](/sites/default/files/downloads/zia/documentation-knowledgebase/policies/cloud-apps/cloud-app-control-policies/cloud-app-categories/New_Cloud_Apps_Apr_2024.csv)
The risk index for these new applications is visible only after they are available on all the clouds.

### Feature Available
#### Optimized URL Search Filter for Web Logs
The URL Search filter in the Web Insights Logs page (Analytics > Web Insights > Logs) is enhanced with a Recommendation pop-up window for your search entries to optimize and expedite the log generation process.
[See image.](#recommendation-window-url-search)
To learn more, see [Web Insights Logs: Filters](/zia/web-insights-logs-filters#URLS).
[]![Recommendation Pop-Up Window](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/web-insights-logs-filters-doc-51630/ZIA6.2r-URL-search-filter-recommendation-window-pop-up.png)

### Feature in Limited Availability
#### Increased Limit for Firewall Filtering Rules
This capability allows selective increases in the number of firewall filtering rules for an organization from the current limit of 1,000 rules to 4,000 rules on approved tenants.
This feature requires an audit for each proposed customer tenant seeking to upgrade. To learn more about the increased limit and the qualified use cases for an upgrade, contact your Zscaler Account team.
With this upgrade, the following user interface changes are implemented in the ZIA Admin Portal:
- The Firewall Filtering rules (under Policy > Firewall Control > Firewall Filtering Policy) are paginated with up to 100 rules displayed per page.
- With pagination, the search option on the Firewall Filtering Policy page has been updated from supporting a generic string search to providing individual categories of search fields, which are *currently* limited to specific rule criteria, action, and other rule attributes. In the updated search, the admin has to select a specific category in which they want to search and the search results span across all pages in the selected category.
[See image.](#firewall-filtering-page-4K-rules)
These user interface changes are only applicable to tenants that are registered for an upgrade in the number of firewall filtering rules to 4,000 rules. The search functionality remains unchanged for tenants with the current 1,000 rule limit.
[]
![ZIA Firewall Filtering Rules page with 4K rule limit](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Firewall-Filtering-Page-4K-Rules.png)

## April 08, 2024
### Feature Available
#### Enhancement to App Finding in 3rd-Party App Governance
You can update the status of an app finding on the App Panel Overview tab. After you update the status of the finding to Resolved or Dismissed, the system recalculates the app risk score and displays a new risk score.
[See image.](#Finding-Drop-Down)
To learn more, see [Updating the App Finding Status](/zia/updating-app-finding-status).
[]![Screenshot of App Finding Status Drop Down](/sites/default/files/downloads/zia/policies/data-loss-prevention/apptotal/using-apptotal/updating-app-finding-status/AppFinding_DropDown.png)

### Feature Available
#### Enhancement to Policy Notifications in 3rd-Party App Governance
In the notification that you receive when a policy is triggered, you can view the automated actions such as classification and automated workflow that the triggered policy has taken on the applications. The notification title is enhanced to indicate the policy that matches the detected apps.
To learn more, see [3rd-Party App Governance Policies](/zia/apptotal-policies).

### Feature Available
#### Support for Changing Risk Score in 3rd-Party App Governance
You can change the risk score for an app in the App Inventory or the App Panel header, specifying the risk score as per your organization's perspective. The defined risk score will override any future system recalculations. You can revert to the default score.
To learn more, see [Updating the App Risk Score](/zia/updating-app-risk-score)[.]

### Feature Available
#### Support for Exporting App Risk Score in 3rd-Party App Governance
You can export the risk score for an app from the App Inventory to a CSV file.
To learn more, see [About the App Inventory](/zia/about-app-inventory).

## April 05, 2024
### Feature Available
#### Debug Mode for Isolation in Zscaler Internet Access (ZIA)
Admins can enable debug mode for isolation profiles, which allows the user to record and gather troubleshooting data for any isolation sessions they create. The recorded session generates diagnostics for basic session information, HTTP Archive format files, console logs, and network logs exported from the web browser.
[See image.](#Enable-Debug-Mode)
To learn more, see [Using Debug Mode for Isolation](/isolation/using-session-debug-mode-isolation).
[]![Enabled toggle for Session Debug Mode.](/sites/default/files/downloads/isolation/profiles/enable_debug-mode.png)

### Feature Available
#### Enhancement to Advanced Settings
You can remove HTTP range headers for specific URL categories. As part of this change, the URL Categories field is added under the Remove Range Headers section on the Advanced Settings page (Administration > Advanced Settings).
[See image.](#advanced-settings-remove-range-headers)
To learn more, see [Configuring Advanced Settings](/zia/configuring-advanced-settings).
[]![ZIA-Advanced-Settings-Page-RN_0.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Advanced-Settings-Page-RN_0.png)

### Feature Available
#### Enhancement to UCaaS One Click Configuration
The support of Unified Communications as a Service (UCaaS) one-click configuration is extended to the Webex cloud application.
[See image.](#ucaas-webex)
To learn more, see [Configuring Advanced URL Filtering Policy](/zia/configuring-advanced-url-policy-settings).
[][![Screenshot of ZIA Advanced Policy Settings Page with Webex UCAAS](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Advanced-Policy-Settings-RN.png)
](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Advanced-Policy-Settings-RN.png)

### Feature Available
#### Proximity Length Available for Certain DLP Dictionaries
For custom Patterns & Phrases DLP dictionaries and the Driver’s License (United States) predefined DLP dictionary, you can use proximity length to define how close a phrase must be to an instance of the pattern (that the dictionary detects) to count as a match.
For custom Patterns & Phrases DLP dictionaries, if you select Match Any Patterns and Any Phrases as the Match Type, you can enable and specify proximity length.
[See image.](#Proximity-Custom-Dictionary)
For the Driver's License (United States) predefined DLP dictionary, if you select High as the Confidence Score Threshold, you can specify proximity length.
[See image.](#Proximity-USDL-Dictionary)
To learn more, see [Adding Custom DLP Dictionaries](/zia/adding-custom-dlp-dictionary) and [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).
Updates to Cloud Service API
The cloud service API has been updated to include a new `proximityEnabledForCustomDictionary` attribute in `/dlpDictionaries` endpoints to indicate whether proximity length is enabled or disabled for custom DLP dictionaries. To learn more, see the [API Reference](/zia/about-api).
[]![Screenshot of Proximity Length for Custom DLP Dictionaries](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-DLP-Custom-Dicts-Proximity-RN.png)
[]![Screenshot of Proximity Length for Driver's License (United States) Predefined DLP Dictionary](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-DLP-USDL-Predefined-Dict-Proximity-RN.png)

## March 22, 2024
### Feature Available
#### Changes to IoT Report API Rate Limits
The rate limit for IoT Report API endpoints within the cloud service API has been updated to the following values:
| API Endpoint | Updated Rate Limit |
| ------------ | ------------------ |
| /iotDiscovery/categories | 2/sec and up to 1000/hr |
| /iotDiscovery/classifications | 2/sec and up to 1000/hr |
| /iotDiscovery/deviceList | 1/min and up to 4/hr |
| /iotDiscovery/deviceTypes | 2/sec and up to 1000/hr |
To learn more, see the [API Rate Limit Summary](/zia/api-rate-limit-summary) and [API Reference](/zia/about-api).

## March 19, 2024
### Feature Available
#### 3rd-Party App Governance API Support for Search by Consent or Marketplace Link
The Zscaler 3rd-Party App Governance API endpoint `GET /apps/app` has been enhanced to support searching for an application by consent link or marketplace link in addition to searching by application ID. You can submit a valid URL and retrieve the applicable application. If the application is valid but doesn't exist in the 3rd-Party App Governance App Catalog, it is automatically submitted to the 3rd-Party App Governance Sandbox for further analysis, and a notification email is sent to you when analysis is complete.
To learn more, see the [API Reference](/zia/apptotal-api).

## March 04, 2024
### Feature Available
#### Enhancement to App Panel Header in 3rd-Party App Governance
On the App Panel header, you can view if an app is verified by the Zscaler 3rd-Party App Governance Threat Intelligence team. A Zscaler-verified app can still be malicious or pose a risk due to a compromised publisher, vulnerabilities, and overprivileged permissions.
[See image.](#app-panel-header)
To learn more, see [About the App Panel](/zia/about-app-panel).
[]![Screenshot of App Panel Header](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/about-app-panel-draft-doc-50703/Zscaler_Verified_App_RN.png)

### Feature Available
#### Enhancement to Automated Workflow of Apps in 3rd-Party App Governance
When taking an automated workflow action (e.g., end user review) on multiple apps on the Inventory page, you can view a summary indicating the number of apps for which the action was successful, failed, or non-applicable.
[See image.](#End-User-Review-Summary)
To learn more, see [Taking Bulk Actions on Apps](/zia/bulk-actions).
[]![Screenshot of End User Review Summary](/sites/default/files/downloads/End-user%20Review%20_%20Succeeded_1.png)

### Feature Available
#### Update to 3rd-Party App Governance API
The Zscaler 3rd-Party App Governance API includes the following new endpoints:
- `GET /apps/search`: Searches for an app by name and retrieves any app whose name contains the search term.
- `GET /app_views/list`: Retrieves the list of [custom views](/zia/custom-views) that you have configured in the 3rd-Party App Governance Admin Portal.
- `GET /app_views/{appViewId}/apps`: Retrieves the assets (i.e., apps) that are related to a specified custom view.
Additionally, the endpoint `GET /apps/app` has been enhanced to include an app’s `riskScore` and `instances` as part of the response.
To learn more about each endpoint, see the [API Reference](/zia/apptotal-api).

## February 23, 2024
### Feature Available
#### Support for Removing File Collaborators From SaaS Assets Report
In addition to the already existing option of removing all external file collaborators, you can also remove all (internal and external) or specific external collaborators for the File Sharing Applications from the SaaS Assets Report: Assets with Incidents page (Analytics > SaaS Security Report > Assets > click on a file sharing application).
[See image.](#remove-collaboration)
To learn more, see [SaaS Assets Report: Assets with Incidents](/zia/saas-assets-report-assets-incidents).
[![Screenshot of the Remove Collaborators window for file sharing apps](/sites/default/files/downloads/ZIA-6.2r-remove-collaborators.png)
]

## February 16, 2024
### Feature Available
#### Logs for Threat Severity
You can filter and view logs for different threat severities. As part of the update, the following changes are available in the ZIA Admin Portal:
Web Insights Logs
A filter and column, Threat Severity, is added to Web Insights Logs.
[See image.](#threat-severity-in-weblogs)
To learn more, see [Web Insights Logs: Columns](/zia/web-insights-logs-columns) and [Web Insights Logs: Filters](/zia/web-insights-logs-filters).
NSS Feeds
The field` %s{threatseverity}` is available when adding an NSS or Cloud NSS feed for web logs.
[See image.](#img-zia-nss-web-log-threat-severity)
To learn more, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs).
[]![Screenshot of the Threat Severity field in the NSS Feed Output Format for Web Logs](/sites/default/files/downloads/zia/release-notes/zia-nss-web-log-threat-severity.png)
[]![ZIA-6.2r-threat-severity-web-logs.png](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/web-insights-logs-filters-draft/ZIA-6.2r-threat-severity-web-logs.png)

### Feature Available
#### New Predefined DNS Control and Firewall Filtering Rules
New predefined DNS Control and Firewall Filtering rules are added to block traffic with known or suspected security threats. These rules are preconfigured to block specific types of traffic using built-in criteria and can be readily used to protect an organization’s traffic against malicious traffic. The predefined rules are listed as follows:
-
DNS Control rules
- Critical Risk DNS Categories
- Critical Risk DNS Tunnels
- High-Risk DNS Categories
- High-Risk DNS Tunnels
- Risky DNS Categories
- Risky DNS Tunnels
[See image.](#dns-rules-block-malicious-traffic)
-
Firewall Filtering rule
- Block Malicious IPs and Domains
[See image.](#firewall-filtering-rule-block-malicious-traffic)
To learn more, see [Modifying the Predefined DNS Control Rules](/zia/modifying-predefined-dns-control-rules) and [Understanding Predefined Firewall Filtering Rules](/zia/understanding-predefined-firewall-filtering-rules). For information about how the new rules are added to existing and new tenants, [see migration details.](#firewall-dns-rule-migration-block-malicious-content)
[]The following table provides information about the default status of each new predefined rule in existing tenants vs. new tenants
| Rule Name | Default Status for Existing Tenants | Default Status for New Tenants |
| --------- | ----------------------------------- | ------------------------------ |
| Critical Risk DNS Categories | Disabled | Enabled |
| Critical Risk DNS Tunnels | Disabled | Enabled |
| High-Risk DNS Categories | Disabled | Enabled |
| High-Risk DNS Tunnels | Disabled | Enabled |
| Risky DNS Categories | Disabled | Disabled |
| Risky DNS Tunnels | Disabled | Disabled |
| Block Malicious IPs and Domains | Disabled | Enabled |
[]![New predefined DNS rules to block malicious traffic ](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/dns-rules-block-malicious-traffic_0.png)
[]![New predefined firewall filtering rules to block malicious traffic ](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/firewall-rule-block-malicious-traffic_0.png)

### Feature Available
#### SaaS Security API
You can now configure tenants for Dynamics 365, a CRM application.
[See image.](#addingsaas)
To learn more, see [About SaaS Application Tenants](/zia/about-saas-application-tenants) and [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
You can configure the application for the SaaS Security API Control policies and also view them on the following pages:
- [Saas Assets Report](/zia/saas-assets-report)
- [SaaS Assets Summary Report](/zia/saas-assets-summary-report)
- [SaaS Security Insights](/zia/saas-security-insights) and [Insights Logs](/zia/saas-security-insights-logs)
- [NSS Feeds](/zia/adding-nss-feeds-saas-security-logs) and [Cloud NSS Feeds for SaaS Security Logs](/zia/adding-cloud-nss-feeds-saas-security-logs)
To learn more, see [Configuring the SaaS Security API Control Policy](/zia/configuring-saas-security-api-control-policy).
[]![SaaS Application Tenants.](/sites/default/files/downloads/List%20of%20SaaS%20Application%20Tenant%20page.png)

### Feature Available
#### Source IP Groups Criterion in Policies
The following policies support the Source IP Groups criterion in addition to the [firewall policies](/zia/configuring-firewall-policies) and [SSL inspection policy](/zia/configuring-ssl-inspection-policy):
- DLP policy rule [with content inspection](/zia/configuring-dlp-policy-rules-content-inspection), [without content inspection](/zia/configuring-dlp-policy-rules-without-content-inspection), and [with Evaluate All Rules Mode enabled](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled)
- [URL filtering policy](/zia/configuring-url-filtering-policy)
As part of this change, the Source IP Groups field has been added to the Add DLP Rule and Add URL Filtering Rule windows.
[See image.](#policies-source-ip-groups)
[]![Screenshot of ZIA Add DLP Rule window](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Add-DLP-Rule-Source-IP-Groups-RN.png)
![Screenshot of ZIA Add URL Filtering Rule window](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Add-URL-Filtering-Rule-Source-IP-Groups-RN.png)

### Feature Available
#### Update to Cloud Service API - IoT Report API
The new IoT report API includes the following new endpoints to retrieve the device classifications, categories and types supported by the Zscaler AI/ML and a list of devices (unmanaged user devices, servers and IoT devices) identified by the Zscaler AI/ML:
- `GET /iotDiscovery/classifications`
- `GET /iotDiscovery/categories`
- `GET /iotDiscovery/deviceTypes`
- `GET /iotDiscovery/deviceList`
The following changes were made as part of this update:
-
Added the `enableIOT` query for the following endpoints to find out all locations that enable the IoT discovery:
It can also be used to obtain location ID to location name mapping.
- `GET /locations`
- `GET /locations/lite`
- `GET /locations/{locationId}/sublocations`
- Added following parameters in the `Location` model (object) for the city geo location information and IoT discovery enable status:
- `city`
- `geoOverride`
- `latitude`
- `longitude`
- `iotDiscoveryEnabled`
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection has also been updated to include new and updated resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

### Feature Available
#### User Risk Scores
The risk score for each user is displayed on the [User Management](/zia/about-users) page in the User Risk Profile column. The display allows for users with scores higher than Low to have their score reset.
[See image.](#user-risk-profile)
To learn more, see [Understanding User Risk Scores](/zia/understanding-user-risk-score).
[]![Image of the User Risk Profile on the User Management page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-user-risk-profile.png)

## February 07, 2024
### Feature Available
#### Disabling Print for ZIA Isolation Profiles
Disabling the printing feature for an isolation profile disables all possibility of being able to print the web page or document that is rendered in isolation. When printing is disabled on an isolation profile, you cannot see the print option from the right-click menu, or the print button in the Isolation Bar. If you try to select File > Print from the browser menu, or enter the key command CTRL/CMD+P shortcut, a message appears stating that it is disabled by policy.
To learn more, see [Creating Isolation Profiles for ZIA](/isolation/creating-zia-isolation-profile-isolation).

## January 26, 2024
### Feature Available
#### DLP Support for New Hierarchical PII Dictionaries
The following new predefined DLP dictionaries allow you to select one or more subdictionaries to detect personally identifiable information (PII):
- [International Bank Account Number (IBAN)](#IBAN)
- [Passport Number (Asia)](#AsiaPassport)
To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).
[]This dictionary allows you to select IBAN dictionaries for one or more of the following countries.
- Andorra (AD)
- Austria (AT)
- Bosnia (BA)
- Belgium (BE)
- Bulgaria (BG)
- Switzerland (CH)
- Cyprus (CY)
- Czechia (CZ)
- Germany (DE)
- Denmark (DK)
- Estonia (EE)
- Spain (ES)
- Finland (FI)
- Faroe Islands (FO)
- France (FR)
- United Kingdom (GB)
- Gibraltar (GI)
- Greenland (GL)
- Greece (GR)
- Croatia (HR)
- Hungary (HU)
- Ireland (IE)
- Israel (IL)
- Iceland (IS)
- Italy (IT)
- Liechtenstein (LI)
- Lithuania (LT)
- Luxembourg (LU)
- Latvia (LV)
- Monaco (MC)
- Montenegro (ME)
- Malta (MT)
- Netherlands (NL)
- North Macedonia (MK)
- Norway (NO)
- Poland (PL)
- Portugal (PT)
- Romania (RO)
- Serbia (RS)
- Sweden (SE)
- Slovenia (SI)
- Slovakia (SK)
- San Marino (SM)
- Tunisia (TN)
- Turkey (TR)
[See image.](#IBAN_Screenshot)
[]![The Selection Options for the International Bank Account Number (IBAN) DLP Dictionary](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-DLP-IBAN-Dictionary-RN.png)
[]This dictionary allows you to select passport number dictionaries for one or more of the following countries.
- China (CN)
- Japan (JP)
- South Korea (KR)
- Malaysia (MY)
- Philippines (PH)
- Singapore (SG)
- Taiwan (TW)
- Turkey (TR)
[See image.](#AsiaPassport_Screenshot)
[]![The Selection Options for the Passport Number (Asia) DLP Dictionary](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-DLP-Asia-Passport-Dictionary-RN.png)

### Feature Available
#### DLP Support for New Numeric PII Dictionaries
The following are new predefined DLP dictionaries to detect personally identifiable information (PII):
- CNPJ Number (Brazil)
- Mexico Unique Population Registration Code
- National Economic Registry Number (Poland)
- Personal Identification Number (Croatia)
- Tax Identification Number (Luxembourg)
The Tax Identification Number (Luxembourg) dictionary has been updated to support 11-digit numbers, in addition to existing support for 13-digit numbers.
- Unique Master Citizen Number
To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).

### Feature Available
#### Support for Domain Profiles in Inline DLP Rules
The Zscaler service supports email recipient domain profiles for inline DLP rules with and without content inspection. When creating DLP rules for Gmail or Outlook, you can select to include or exclude up to 8 domain profiles as part of your rule criteria.
[See image.](#inline-dlp-domain-profiles-rn)
To learn more, see [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection), [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection), and [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled).
The `/webDlpRules` endpoints within the cloud service API are also updated to include two new optional fields, namely `includedDomainProfiles` and `excludedDomainProfiles`.
To learn more, see the [API Reference](/zia/about-api).
[]![Screenshot of Email Recipient Domain Profiles on the DLP Add Rule Page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-DLP-InlineRules-Domain-Profiles_RN.png)

## January 19, 2024
### Feature Available
#### IP Surrogacy for Known Browsers Using Authentication Methods That Are Not Cookie Based
For cookie-based authentication, the behavior for IP surrogacy from known browsers is that when the IP-to-user mapping has been established, there are no further authentication challenges for traffic originating from that source IP address until the surrogate IP entry times out. This behavior can now be applied to authentication methods that are not cookie based, such as Kerberos, digest, and basic authentication.
As part of this change, the Supported Authentication Methods field is available when [configuring locations](/zia/configuring-locations). Selecting Cookie and Proxy**** ****prevents additional authentication challenges to traffic using both cookie and non-cookie-based authentication methods after the initial challenge.
[See image.](#supported-auth-methods)
[]![Image of the Supported Authentication Methods field](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/Supported%20Authentication%20Methods.png)

### Feature Available
#### Upgrade to Third-Party DPI Agent and Protocol Bundle
Qosmos has been upgraded to the latest PB 1.670.
The following newly supported network apps are added:
- AnyDesk
- CyberGhost
- DotVPN
- ExpressVPN
- FIX
- HMAVPN
- IGMP
- IMAP
- IMAPS
- IPVanish
- POP3
- POP3S
- SMTP
- WireGuard
To learn more, see [About Network Applications](/zia/about-network-applications).

## January 12, 2024
### Feature Available
#### Configuring Domain Fronting and DNS Optimization in Advanced Settings
In Advanced Settings (Administration > Advanced Settings), there are two new options available to configure:
-
Block CONNECT Host and SNI Mismatch: Enable to block forward proxy connections where the CONNECT host doesn't match the SSL/TLS client hello SNI.
[See image.](#block-connect-host)
-
Prefer SNI over CONNECT Host for DNS Resolution: Enable to use the SSL/TLS client hello SNI for DNS resolution instead of the CONNECT host for forward proxy connections.
[See image.](#prefer-sni)
You can enable the Block CONNECT Host and SNI Mismatch option, but if you have a use case where an upstream proxy puts the IP into the CONNECT host name received by Zscaler, there will be a mismatch (so traffic is blocked). In this case, you can enable the Prefer SNI over CONNECT Host for DNS option.
To learn more, see [Configuring Advanced Settings](/zia/configuring-advanced-settings).
[]![Block CONNECT Host and SNI Mismatch knob](/sites/default/files/downloads/zia/configuring-advanced-settings/AS_block%20connect%20host%20sni%20mismatch.png)
[]![Prefer SNI over CONNECT Host for DNS Resolution](/sites/default/files/downloads/zia/configuring-advanced-settings/DNS%20settings.png)

## January 11, 2024
### Feature Available
#### File Size Limit Increase in Isolation for ZIA
The size limit for downloading and uploading files in Isolation has increased to 1 GB. End users can expect an increase of time to upload files from 9 minutes to 10 minutes. If downloading or uploading multiple files at once, the size limit is 2 GB.
To learn more, see [Transferring and Viewing Files in Isolation](/isolation/transferring-and-viewing-files-isolation) and [Limits in Isolation](/isolation/limits-isolation).
