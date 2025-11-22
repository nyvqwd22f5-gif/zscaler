# Release Upgrade Summary (2023)
Source: https://help.zscaler.com/zia/release-upgrade-summary-2023

This article provides a summary of all new features and enhancements per Zscaler cloud for Zscaler Internet Access (ZIA). Zscaler will email a notification to your organization's registered support contacts approximately one week before your cloud is upgraded. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com).

**Clouds:** zscaler.net, zscalerone.net, zscalertwo.net, zscalerthree.net, zscloud.net, zscalerbeta.net
The following service updates were deployed to zscaler.net on

## December 15, 2023
### Feature Available
#### Support for Workload Groups Tagging
You can create workload groups to apply security policies for your workloads deployed on the public cloud service provider, such as the Amazon Web Service (AWS). They can be used as a criterion in ZIA policies such as SSL Inspection, Firewall Filtering, URL Filtering, and Data Loss Prevention (DLP) to apply security policies to the workload traffic.
As part of this feature:
- A new page, Workload Groups, is added to the Administration > Workload Groups menu.
[See image.](#workloads-groups-RN-image)
- A new Workload Groups field is added to the following policies:
- [DLP Policy with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection)
- [DLP Policy without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection)
- [Firewall Filtering](/zia/configuring-firewall-filtering-policy)
- [URL Filtering](/zia/configuring-url-filtering-policy)
- [SSL Inspection](/zia/configuring-ssl-inspection-policy)
To learn more, see [Understanding Workload Groups](/zia/understanding-workload-groups), [About Workload Groups](/zia/about-workload-groups) and [Configuring Workload Groups](/zia/configuring-workload-groups).
Update to Cloud Service API
The cloud service API includes a new `GET /workloadGroups` endpoint to retrieve the list of preconfigured workload groups. It also includes a new `workloadGroups` attribute to configure the workload groups as policy criteria. The `workloadGroups` attribute is supported in the following policy endpoints:
- `/firewallFilteringRules`
- `/webDlpRules`
- `/urlFilteringRules`
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection has also been updated to include new resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).
![Screenshot of the navigation to Workload Groups page (Administration> Workload Groups) from the menu ](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/zia-RN-workloads-groups-menu.png)
[]

## December 01, 2023
### Feature Available
#### Evaluate All Rules Mode for Inline DLP
To access this feature, contact your Zscaler Account team.
For inline DLP policy, you can use Evaluate All Rules mode to specify how the Zscaler service evaluates configured DLP rules. On the DLP Advanced Settings page (Administration > DLP Advanced Settings) in the ZIA Admin Portal, you can select whether the Zscaler service evaluates all rules or uses rule order.
[See image.](#dlp-rule-evaluation-setting)
You configure your inline DLP policy rules based on that setting. If you select Evaluate All Rules, the Zscaler service evaluates all rules before enforcing the rule with the most restrictive action. You can also specify the severity of the violation and create exception rules, which are child rules that allow you to exclude specific users or groups in your organization that need to perform tasks as part of a necessary workflow that might otherwise violate inline DLP policy.
To learn more, see [Configuring DLP Advanced Settings](/zia/configuring-dlp-advanced-settings) and [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode).
Update to Web Insights Logs
A new filter and column field, DLP Severity, is added to the Web Insights Logs page (Analytics > Web Insights > Logs) that indicates the severity of violated DLP rules.
[See image.](#severity-log-field)
To learn more, see [Web Insights Logs: Columns](/zia/web-insights-logs-columns) and [Web Insights Logs: Filters](/zia/web-insights-logs-filters).
Update to Cloud Service API
The `/webDlpRules` endpoints within the cloud service API have been updated to include three new attributes, namely `parentRule`, `subRules`, and `severity`. The `parentRule` and `subRules` fields are exclusive to exception rule configuration, which is available when the DLP engines are configured to evaluate all DLP rules instead of using rule order.
To learn more, see the [API Reference](/zia/about-api).
[]![Screenshot of Inline DLP Rule Evaluation Settings on the DLP Advanced Settings Page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-DLP-Advanced-Settings-RuleEval_RN.png)
[]![Severity Field in Web Inisgths Logs](/sites/default/files/downloads/risk360/dashboard-analytics/about-factors/ZIA-6.2r-Severity-field.png)

### Feature Available
#### Updates to Endpoint DLP
The following enhancements are available in Endpoint DLP:
- Support for endpoints running macOS 12, 13, or 14 (Monterey, Ventura, or Sonoma)
- The ability to import DLP resources via CSV files
- The ability to group DLP resources
- Support for Google Drive (Personal) and iCloud (macOS)
- The ability to delete all exception rules when a parent rule is deleted
- Increased limit of 32 exception rules per parent rule
- Support for password-protected and encrypted files
- Support for external storage devices that use Media Transfer Protocol (MTP)
- The ability to use a Block action when files are copied to network shares from endpoints running Windows
- Added support for the following predefined DLP dictionaries:
- Bulgaria Uniform Civil Number
- Credentials and Secrets
- Driver’s License (United States)
- Passport Number (European Union)
- VAT Number (Austria)
- VAT Number (Belgium)
- VAT Number (France)
- VAT Number (Germany)
- VAT Number (Luxembourg)
- VAT Number (Netherlands)
To learn more, see [About Endpoint Data Loss Prevention](/zia/about-endpoint-dlp), [About DLP Resources](/zia/about-dlp-resources), [Configuring Endpoint DLP Policy Rules](/zia/configuring-endpoint-dlp-policy-rules), [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).

## November 17, 2023
### Feature Available
#### Support for Zscaler Cloud & Branch Connector Log Types
If you have subscribed to Zscaler Cloud & Branch Connector, you can configure Nanolog Streaming Service (NSS) and Cloud NSS feeds for two new log types from the ZIA Admin Portal: Event and Metrics. The log types are available when you select Cloud/Branch Connector as the Log Domain.
[See image.](#img-zia-nss-event-metrics)
To learn more, see the following Cloud & Branch Connector articles:
- [Adding NSS Feeds for Event Logs](/cloud-branch-connector/adding-nss-feeds-event-logs)
- [Adding NSS Feeds for Metrics Logs](/cloud-branch-connector/adding-nss-feeds-metrics-logs)
- [Adding Cloud NSS Feeds for Event Logs](/cloud-branch-connector/adding-cloud-nss-feeds-event-logs)
- [Adding Cloud NSS Feeds for Metrics Logs](/cloud-branch-connector/adding-cloud-nss-feeds-metrics-logs)
[][![Zscaler Cloud & Branch Connector Event and Metrics log types in the ZIA Admin Portal](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-microsoft-azure/img-zia-nss-cloud-branch-connector-event-metrics.png)
]

## November 10, 2023
### Feature Available
#### DLP Support for New Medical Information Dictionaries
The following are new predefined medical DLP dictionaries:
- Diseases Information
- Drugs Information
- Treatments Information
To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).

### Feature Available
#### Enhancement to Virtual Service Edges
You can forward your organizational traffic to the Virtual Service Edges using IPSec tunnels that terminate at the Virtual Service Edge.
As part of this enhancement, the IPSec Local Termination option is added to the Add Virtual Service Edge (Administration > Virtual Service Edges > Add Virtual Service Edge) and Add Virtual Service Edge Cluster (Administration > Virtual Service Edges > Virtual Service Edge Clusters > Add Virtual Service Edge Cluster) windows.
[See image.](#virtual-service-edge-node-IPSec-local-termination)
To learn more, see [Adding Virtual Service Edge Instances](/zia/adding-virtual-service-edge-instances) and [Adding Virtual Service Edge Clusters](/zia/adding-virtual-service-edge-clusters).
[]![Screenshot of Add Virtual Service Edge window with IPSec Local Termination](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Add-Virtual-Service-Edge-Standalone-with-IPSec-Local-termination.png)
![Screenshot of the Add Virtual Service Edge Cluster window with IPSec Local Termination](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Add-Virtual-Service-Edge-Clusters-with-IPSec-Local-termination.png)

### Feature Available
#### File Type Control Size Limits
The following categories have been added to the File Type Control rules to limit file sizes:
- Minimum File Size (KB)
- Maximum File Size (KB)
[See image.](#filesize)
To learn more, see [Configuring the File Type Control Policy](/zia/configuring-file-type-control-policy).
[]![Minimum and Maximum File Size settings in the Add File Type Control Rule window.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/File%20Type%20Control_MinMax%20File%20Size.png)

### Feature Available
#### Filter SaaS Activities Report by User's Role
You can filter the SaaS Activities Report for activities performed by a specific role type using the new filter option Activity Role Type.
[See image.](#activity-role)
To learn more, see [SaaS Security Alerts & Activities Report](/zia/saas-security-alerts-activities-report).
NSS Feeds
The field `%s{is_admin_act}` is available when adding an NSS or Cloud NSS feed for SaaS Security Activity logs.
To learn more, see [NSS Feed Output Format: SaaS Security Activity Logs](/zia/nss-feed-output-format-saas-security-activity-logs).
[![SaaS Activities Report](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/saas-security-alerts-activities-report-doc-49103/ZIA-6.2r-SaaS-Security-Activities-Report-rn.png)
]

### Feature Available
#### Google Cloud Platform in Tenant Profile
The Tenant Profiles feature supports the Google Cloud Platform. This allows you to restrict users to certain organization IDs in respective Google Cloud accounts.
[See image.](#gcp-tenant-profile)
To learn more, see [Adding Tenant Profiles](/zia/adding-tenant-profiles).
[]![Screenshot of ZIA Tenant Profiles with Google Cloud Platform](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Add-Tenant-Profile-GCP-RN.png)

### Feature Available
#### Optical Character Recognition Support for SaaS Security API DLP
The Zscaler service supports optical character recognition (OCR) for SaaS Security API Data Loss Prevention (DLP). Additionally, you can configure OCR settings for your organization, instead of having to apply the settings to individual DLP rules. You apply OCR settings on the DLP Advanced Settings page in the ZIA Admin Portal (Administration > DLP Advanced Settings) for both inline DLP and SaaS Security API DLP.
[See image.](#ocr-dlp-global-setting)
To learn more, see [Configuring DLP Advanced Settings](/zia/configuring-dlp-advanced-settings).
Updates to Cloud Service API
The `ocrEnabled` attribute in the `/webDlpRules` API endpoints has been deprecated as the OCR configuration is no longer supported on a per-DLP rule basis.
[]![Screenshot of Optical Character Recognition Settings on the DLP Advanced Settings Page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-OCR-global-setting-for-DLP-RN.png)

### Feature Available
#### Support in SaaS Security API DLP Policy for Quarantine of Sensitive Content in Webex Teams
The SaaS Security API Control policy supports a new option to quarantine sensitive content in Webex Teams. You can specify a tombstone message that end users see when messages or files in Webex Teams are quarantined.
[See image.](#ZIA-Webex-CASB-Quarantine)
After a message or file has been quarantined in Webex Teams, admins can use the SaaS Assets Report to review and remove the quarantined content.
[See image.](#ZIA-Webex-SaaS-Assets-Report-Quarantine)
To learn more, see [Configuring the SaaS Security API DLP Policy](/zia/configuring-saas-security-api-dlp-policy), [About Quarantine Tombstone File Templates](/zia/about-quarantine-tombstone-file-templates), and [SaaS Assets Report: Assets with Incidents](/zia/saas-assets-report-assets-incidents).
[]![Webex Teams Quarantine feature in SaaS Security DLP Rules](/sites/default/files/downloads/zia/about-saas-security-api-dlp/ZIA-Webex-CASB-Quarantine-RN.png)
[]![SaaS Asset report removal of quarantine item](/sites/default/files/downloads/zia/about-saas-security-api-dlp/ZIA-Webex-SaaS-Assets-Report-Quarantine-RN.png)

### Feature Available
#### Updates to Cloud Service API: Forwarding Control-related Endpoints
The cloud service API includes the following new endpoints to create, modify, retrieve, and delete forwarding rules:
- `GET /forwardingRules`
- `GET /forwardingRules/{ruleId}`
- `POST /forwardingRules`
- `PUT /forwardingRules/{ruleId}`
- `DELETE /forwardingRules/{ruleId}`
- `GET /users/references`
In addition, the cloud service API includes the following new endpoints to create, modify, retrieve, and delete Zscaler Private Access (ZPA) gateways that are used in forwarding rules for ZPA:
- `GET /zpaGateways`
- `GET /zpaGateways/{gatewayId}`
- `POST /zpaGateways`
- `PUT /zpaGateways/{gatewayId}`
- `DELETE /zpaGateways/{gatewayId}`
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection has also been updated to include new resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

## November 09, 2023
### Feature Available
#### Enhancements to 3rd-Party App Governance Inbound Integration Process
The 3rd-Party App Governance Integrations window is enhanced to give you a better onboarding experience, additional functionality, and enhanced visibility into your connected platforms. The Inbound tab in this window contains the following enhancements:
- You can add multiple instances (domains) of a given SaaS platform as required.
- After integration is completed, you can view the list of added domains.
- You can view the integration status for each domain.
- You can view the date and time a domain was added and last synced.
- You can update or delete an integration.
[See image.](#Integrations-Window)
You can also view the integration status on the 3rd-Party App Governance dashboard and App Inventory.
To learn more, see [Connecting Your Platforms to 3rd-Party App Governance](/zia/connecting-your-platforms-apptotal).
[![Screenshot of Integrations Window](/sites/default/files/downloads/integration%20modal%20RN.png)
]

### Feature Available
#### Enhancements to App Inventory Filters in 3rd-Party App Governance
You can apply the user count and risk score filters to your app inventory to filter the apps based on the user count and risk score, supporting parameters such as bigger than, smaller than, and within a given range. You can also filter based on the low, medium, and high risk scores by using the risk rating filter.

### Feature Available
#### Support for Adding a Note to an App in 3rd-Party App Governance
You can add a note to an app from the App Panel header, detailing the reasons for actions such as sanctioning, unsanctioning, or reviewing the app. You can also add a custom notation and a score on an app.
[See image.](#App-Panel-Header)
To learn more, see [About the App Panel](/zia/about-app-panel).
[![Screenshot of App Panel Header](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/about-app-panel-doc-49454/AppPanelNote_RN.png)
]

## November 07, 2023
### Feature Available
#### Enhancements to Workflow Automation
The following enhancements are available in Workflow Automation:
- Incident group mapping and workflow mapping are enhanced. When adding an incident group mapping or workflow mapping, some of the properties display the values for your organization that you can select from (e.g., severity and matchingPolicies.rules[*].name). Otherwise, you must enter the value for the property.
[See image.](#property-mapping)
- Incident filters can be applied, saved, and reused to view the various incidents on the Incidents page.
[See image.](#filters)
- The Workflow Automation API is enhanced with the following updates:
- A new parameter `pageId` is added to the POST `/dlp/v1/incidents/search` endpoint. The page ID is a unique identifier returned in the response of the first search request. You can use the value in subsequent search requests for faster and more efficient results.
The Postman collection is also updated to include new resources.
To learn more, see [Managing Incident Group Mappings](/zia/managing-incident-group-mappings), [Managing Workflow Mappings](/zia/managing-workflow-mappings), [About Incidents](/zia/about-incidents), [Using Incident Filters in Workflow Automation](/zia/using-incident-filters-workflow-automation), and [Understanding Workflow Automation API](/zia/understanding-workflow-automation-api).
[][![Mapping a Property on the Incident Group Mapping Page in the Workflow Automation Admin Portal ](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-Incident-Group-Mapping-PG-Property-Field.png)
](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-Incident-Group-Mapping-PG-Property-Field.png)
[![Mapping a Property on the Workflow Mapping Page in the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-Workflow-Mapping-PG-Property-Field.png)
](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-Workflow-Mapping-PG-Property-Field.png)
[][![Viewing the Saved Filters on the Filters Window in the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-Filters-Win-My-Filters.png)
](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-Filters-Win-My-Filters.png)

## October 27, 2023
### Feature Available
#### Support for HTTP/2
To enable this feature, contact Zscaler Support.
The support for HTTP/2 now includes the following enhancements to the ZIA Admin Portal:
Non-Browser Traffic
You can enable HTTP/2 as the default web protocol for accessing various applications at your organizational level.
You can enable HTTP/2 under the Administration > Advanced Settings page in the ZIA Admin Portal.
[See image.](#http2-advanced-settings)
To learn more, see [Configuring Advanced Settings](/zia/configuring-advanced-settings).
SSL Inspection
You can enable HTTP/2 as the web protocol used for accessing all applications.
You can enable HTTP/2 from the Action section under Policy > SSL Inspection > Add SSL Inspection Rule.
[See image.](#http2-ssl-inpection-rule)
To learn more, see [Configuring SSL Inspection Policy](/zia/configuring-ssl-inspection-policy).
Dashboard
A new data type, Response HTTP Version, is added to the New Widget window on Dashboard pages.
[See image.](#http-version-data-type)
To learn more, see [Web Data Types and Filters](/zia/web-data-types-and-filters).
Web Insights Logs
Two new filters and columns, Request Version and Response HTTP Version, are added to the Analytics > Web Insights > Logs page.
[See image.](#http-version-filter-column)
To learn more, see [Web Insights Logs: Filters](/zia/web-insights-logs-filters) and [Web Insights Logs: Columns](/zia/web-insights-logs-columns).
[]![Enable the HTTP/2 toggle button to set HTTP2.0 as the default web protocol for accessing various applications.](/sites/default/files/downloads/ZIA-Advanced-Settings-HTTP2.0_0.png)
[]![The Add SSL Inspection window enables configuring HTTP2.0 as the default web protocol for accessing various applications.](/sites/default/files/downloads/ZIA-Add-SSL-Inspection-Rule-Window.png)
[]![Response HTTP Version data type in New Widget window](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/logs/web-insights-logs-columns/ZIA-6.2-http-version-data-type.png)
[]![HTTP Version filter and columns in Web Insights Logs](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/logs/web-insights-logs-columns/ZIA-6.2-http-version-filter-column.png)

### Feature Available
#### Updates to Cloud Service API
The following updates have been made to the cloud service API:
- Added the `GET /browserIsolation/profiles` endpoint to read the browser isolation profiles.
- Added `ISOLATE` action and the `cbiprofile` parameter to the following endpoints:
- `GET /urlFilteringRules`
- `POST /urlFilteringRules`
- `GET /urlFilteringRules/{ruleId}`
- `PUT /urlFilteringRules/{ruleId}`
The Postman collection has also been updated to include new resources.
To learn more, see [What Is Isolation?](/isolation/what-isolation), [Creating Isolation Profiles for ZIA](/isolation/creating-zia-isolation-profile-isolation), [URL Filtering Policies](/zia/url-filtering-policies), [API Reference](/zia/about-api), [API Rate Limit Summary](/zia/api-rate-limit-summary), and [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

## October 19, 2023
### Feature Available
#### Enhancements to Workflow Automation
The following enhancements are available in Workflow Automation:
- The Template Mapping page is redesigned. Using the Add Template Mapping and the Edit Template Mapping windows, you can add and edit an incident template mapping.
[See image.](#template-mapping)
- Closed incidents can be reopened by clicking the Reopen button on the Incident Details page.
[See image.](#reopen-incidents)
- Duplicate incidents can be viewed for an incident by clicking the duplicate incident link on the Incident Details page.
[See image.](#Duplicate-Incidents)
- The table columns that appear on the Incidents page are configurable.
[See image.](#table-columns-configurable)
- Workflows can be deleted by clicking the Delete Workflow Settings icon for a workflow on the Workflows page.
[See image.](#delete-workflow)
To learn more, see [About Incidents](/zia/about-incidents), [Viewing & Managing Incident Details](/zia/viewing-managing-incident-details), [Managing Incident and Digest Template Mappings](/zia/managing-incident-and-digest-template-mappings), and [Managing Workflows](/zia/managing-workflows).
[]![Screenshot of the Add Template Mapping Window in the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-Release-Note-Add-Template-Mapping-Window.png)
![Screenshot of the Edit Template Mapping Window in the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-Release-Note-Edit-Template-Mapping-Window.png)
![Screenshot of the Incident Details Page Showing the Re-Open Button on the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-Release-Note-Incident-Detail-Page-Reopen.png)
[]
[]![Screenshot of the Incident Details Page with the Duplicate Link Showing in the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-Release-Note-Incident-Detail-PG-Duplicate-1.png)
![Screenshot of the Duplicate Incidents window in the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-Release-Note-Incident-Detail-PG-Duplicate-2.png)
![Screenshot of the Workflows Page in the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-Release-Note-Workflows-PG.png)
[]
[]![Screenshot of the Incident Details Page with the Table Options icon on the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-Release-Note-Incidents-Page-Table-Options-1.png)
![Screenshot of the Table Options window in the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-Release-Note-Incidents-PG-Table-Options-2.png)

## October 06, 2023
### Feature Available
#### ChatGPT Application Recategorizing
The ChatGPT cloud application is recategorized under the AI & ML Applications category from the Productivity & CRM Tools category.
[See image.](#ai-ml-apps-cat)
To learn more, see [Viewing Supported Cloud Applications](/zia/understanding-cloud-app-categories#view-cloud-apps).
[] ![Screenshot of ZIA Add Cloud Application Rule of AI & ML Apps with ChatGPT in the Cloud Applications Field](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Add-Cloud-App-Control-Rule-AI-ML-ChatGpt.png)

### Feature Available
#### DLP Support for New Alphanumeric PII Dictionaries
The following are new predefined DLP dictionaries:
- National Health Index Number (New Zealand)
- Tax Identification Number (Finland)
- Tax Identification Number (Ireland)
- VAT Number (Ireland)
To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).

### Feature Available
#### DLP Support for New PII Dictionaries
The following are new predefined DLP dictionaries:
- Australia Passport Number
- Bulgaria Uniform Civil Number (EGN)
- National Provider Identifier
- Social Security Number (Austria)
- Tax Identification Number (Greece)
- Tax Identification Number (Peru)
- Tax Identification Number (Poland)
- Tax Identification Number (Spain) (CIF)
- Tax Identification Number (US)
To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).

### Feature Available
#### Quarantine to User Root Folder for SaaS Security API File Sharing Apps
SaaS Security API DLP policies support quarantining to the user root folder and tombstone templates for all supported file sharing apps.
To learn more, see [Configuring the SaaS Security API DLP Policy](/zia/configuring-saas-security-api-dlp-policy).

### Feature Available
#### Support for Custom Applications in Shadow IT Report
The Shadow IT Report displays custom applications that you add using the [Cloud Applications](/zia/about-cloud-applications) page (Administration > Cloud Applications). It displays transaction information such as upload bytes, download bytes, users, and location information for custom applications.
You can filter the Shadow IT Report (Analytics > SaaS Security Report > Applications) for custom applications by selecting the Custom Applications option under the Application Category filter.
[See image.](#cust-app-img)
To learn more, see [About Shadow IT Report](/zia/about-shadow-it-report) and [About Application Information](/zia/about-application-information).
![Screenshot of the Custom Aplication option in the Shadow IT Report in the ZIA Admin Portal](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/about-application-information/ZIA-6.2r-custom-application-option.png)
[]

### Feature Available
#### Support for MS Chromium Edge User-Agent Criteria in Policies
A new browser type, MS Chromium Edge, is introduced under the user-agent criterion of the URL Filtering, Cloud App Control, and SSL Inspection policies.
MS Chromium Edge is now separated from the Microsoft Edge Browser type. So, if you previously configured the URL Filtering, Cloud App Control, and SSL Inspection policies for the Microsoft Edge browser type, ensure that you configure MS Chromium Edge, as well, to maintain consistency in policy behavior.
[See image.](#img-ms-chromium-edge)
[![Screenshot of the Add URL Filtering Rule window with MS Chromium Edge highlighted](/sites/default/files/downloads/img-zia-url-filtering-rule-ms-chromium-edge.png)
]

### Feature Available
#### Update to Cloud Service API: New Cloud Applications Endpoints
The cloud service API includes the following new endpoints to retrieve the list of predefined and custom cloud applications, update information for the cloud applications, and retrieve the list of custom tags available to assign to the cloud applications.
- `PUT /cloudApplications/bulkUpdate`
- `GET /cloudApplications/lite`
- `GET /customTags`
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection has also been updated to include new resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

### Feature Available
#### Zscaler Index Tool Configuration Enhancement
You can deploy the Zscaler Index Tool on Azure VMs. Upon request, Zscaler Support shares the Index Tool virtual hard disk (VHD) shared access signature (SAS) token token to use when deploying the Azure instance that hosts the Zscaler Index Tool VM.
To learn more, see [Configuring the Index Tool for Azure VMs](/zia/configuring-index-tool-azure-vms).

## September 29, 2023
### Feature Available
#### DLP Support for Shift JIS Encoding
The Zscaler DLP engines support Shift JIS Encoding for extracting Japanese text from files.
To learn more, see [About Data Loss Prevention](/zia/about-data-loss-prevention).

### Feature Available
#### Site Review Enhancement
The Zscaler's site review website supports the following languages:
- Chinese
- Chinese Taiwan (Optional)
- English (United States)
- English (United Kingdom)
- French
- German
- Japanese
- Russian
- Spanish
To learn more, see [Looking Up URLs in Site Review](/zia/using-site-review-lookup-urls).

## September 26, 2023
### Feature Available
#### Enhancements to Workflow Automation
The following enhancements are available in Workflow Automation:
- A new critical priority is available.
- On the Priorities page, you can assign a critical priority to incident groups.
- On the Incidents and Incident Detail pages, you can assign a critical priority to incidents using the Assign Priority action.
- On the Admins page, you can include the critical incident priority to be included in the digest notification.
[See image.](#Critical-Priority-Image)
- The Template Mapping page is enhanced.
- A new Default source action is available when configuring incident template mappings. Workflow Automation provides Default template mappings for the different incident source DLP types (e.g., Inline, SaaS Security API, and Endpoint) and notification types. These Default template mappings are mapped to the default notification and survey templates provided by Workflow Automation.
- Additional source actions are available for selection if you want to configure additional incident template mappings for the different incident source DLP types.
[See image.](#template-mapping)
- Additional user attributes (Manager Name, Manager Email, and Department) for a user associated with an incident appear in the Violation Details section on the Incident Details page.
[See image.](#Additional-User-Attributes)
- The CloudFormation template provided by Workflow Automation is enhanced to make configuring the DLP application integration in Amazon Web Services (AWS) simpler. Additional parameters added to the template enable the CloudFormation script in AWS to perform the following:
- Secure access to the incident data by Workflow Automation AWS account ID and role.
- Create a KMS key and link that key to the S3 buckets and SNS topic for encryption.
- Create an additional support role that can be assumed by Zscaler Support to assist you with troubleshooting any integration configuration issues you might have in your AWS account.
In addition, the Support User Role ARN field is added to the AWS Zscaler DLP Integration page in Workflow Automation. When this field is populated on the page, it makes it simpler for Zscaler Support to easily identify and assume the support role for your organization and assist you with troubleshooting the issues you have in AWS. Entering the Support User Role ARN is optional.
[See image.](#Support-Role)
This enhancement does not affect any customer that has already successfully configured the DLP application integration in AWS.
To learn more, see [Managing Priorities](/zia/managing-priorities), [Managing Admins](/zia/managing-admins), [About Incidents](/zia/about-incidents), [Viewing & Managing Incident Details](/zia/viewing-managing-incident-details), [Managing Incident and Digest Template Mappings](/zia/managing-incident-and-digest-template-mappings), and [Configuring the DLP Application Integration Using Amazon Web Services](/zia/configuring-dlp-application-integration-using-amazon-web-services).
[]![Viewing the Critical Priority option on the Priorities page in the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-Priorities-Page.png)
![Viewing the Critical Priority Option on the Assign Priority Window in the Workflow Automation Admin Portal ](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-Assign-Priority-Window.png)
![Viewing the Critical Priority Option on the Add Admin Assignment window in the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-Add-Admin-Assignment-Window.png)
[] ![Viewing the Default Incident Template Mappings on the Template Mapping Page in the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-Template-Mapping-Page.png)
![Viewing the Additional User Fields in the Violation Details window in the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-Violation-Details-Sect.png)
[]
![Viewing the New Support User Role ARN field that was Added to the Add Zscaler DLP Integration Page in the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-Add-AWS-Zscaler-DLP-Integration-Page.png)
[]

## September 22, 2023
### Feature Available
#### Support for Zscaler Cloud & Branch Connector in Cloud NSS
If you have subscribed to Zscaler Cloud & Branch Connector, you can configure Cloud NSS for your Cloud & Branch Connector from the ZIA Admin Portal by selecting the NSS type as NSS for Firewall, Cloud and Branch Connector.
[See image.](#nss-firewall-cloud-branch-connector)
To learn more, see [Adding Cloud NSS Feeds for Firewall Logs](/zia/adding-cloud-nss-feeds-for-firewall-logs) and [Adding Cloud NSS Feeds for DNS Logs](/zia/adding-cloud-nss-feeds-dns-logs).
[]![Screenshot of NSS for Firewall, Cloud and Branch Connector (NSS type) in ZIA Cloud NSS](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-RN-cloud-branch-connector-support-cloud-nss-image.png)

## September 19, 2023
### Feature Available
#### Mobile User Experience in Isolation for ZIA
Isolation is supported on iOS and Android mobile platforms. When traffic is generated from a mobile browser and triggers a policy on ZIA that has the action as Isolate, that traffic is isolated.
To learn more, see [Mobile User Experience in Isolation](/isolation/mobile-user-experience-isolation) and [Configuring ZIA for Isolation](/isolation/configuring-zia-isolation).

## September 18, 2023
### Feature Available
#### URL Removed from Microsoft 365 One Click Rule
The *.blob.core.windows.net URL has been removed from the Microsoft 365 One Click Rule. The Zscaler service no longer exempts this wildcard FQDN from SSL inspection when Microsoft-Recommended One Click Microsoft 365 Configuration is enabled. However, if you want to exempt this URL from SSL inspection, you can create an [SSL inspection](/zia/configuring-ssl-inspection-policy) rule to exempt it.

## September 15, 2023
### Feature Available
#### DLP Support for New Predefined Dictionaries
The following are new predefined National Drug Code (NDC) DLP dictionaries:
- NDC Number (Package)
- NDC Number (Product)
Additionally, the new dictionaries support an Action option to configure how each dictionary evaluates matching numbers.
[See image.](#ZIA-DLP-NDC-DictionariesActionOption-RN)
To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).
[] ![The Action Options for the NDC DLP Dictionaries](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-NDC-Number-ActionDropDownMenu-RN.png)

### Feature Available
#### Enhancement to Virtual Service Edge
On the ZIA Admin Portal, you can initiate a support tunnel or allow Zscaler to initiate a support tunnel to a Virtual Service Edge. As part of this change, the Support Information section has been added to the Add/Edit Virtual Service Edge window (Administration > Virtual Service Edges) with the following fields:
- Zscaler Initiated On-Demand Support Tunnel
- Establish Support Tunnel
- Virtual Service Edge ID
[See image.](#add-vse-support-info)
To learn more, see [Adding Virtual Service Edge Instances](/zia/adding-virtual-service-edge-instances).
[]![Screenshot of ZIA Add Virtual Service Edge window with Support Information](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Add-Virtual-Service-Edge-Support-Information-RN.png)

### Feature Available
#### Exact Data Match with No Primary Keys
You can now configure DLP Exact Data Match (EDM) policies to use templates, dictionaries, and engines created with no primary keys. Previously, EDM required that you specify one or two primary fields within a template which could be selected when creating a dictionary. EDM with no primary keys allows you to specify all fields from your template as mandatory or optional to match.
Before enabling EDM with No Primary Keys, all existing EDM schema (templates, dictionaries, engines, and policies) must be deleted or unassigned. New schema with No Primary Keys functionality can be created after the feature is enabled.
As part of this change:
- A new option, EDM with No Primary Keys, is added to the DLP Advanced Setting page (Administration > DLP Advanced Settings).
[See image.](#NPK-Option)
- Alternate settings for creating an EDM dictionary (if the No Primary Keys option is enabled) are added.
[See image.](#NPK-dictionary-settings)
To learn more, see [Configuring EDM with No Primary Keys](/zia/configuring-exact-data-match-no-primary-keys).
[]![Image of the EDM with No Primary Keys setting](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/EDM-NPK-Setting.png)
[]![Image of the dictionary settings for EDM with no primary keys](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/NPK-dictionary-settings.png)

### Feature Available
#### SaaS Security API DLP and Malware Detection Policy Support for Slack Canvas
The SaaS Security API DLP and Malware Detection policies support scanning files and messages in Slack Canvas.
To learn more, see [Configuring the SaaS Security API DLP Policy](/zia/configuring-saas-security-api-dlp-policy) and [Configuring the SaaS Security API Malware Detection Policy](/zia/configuring-saas-security-api-malware-detection-policy).

### Feature Available
#### Update to Predefined DLP Names Dictionaries
The Predefined Data Loss Protection (DLP) dictionaries for Names (Canada), Names (Spain), and Names (US) support an Action option to configure how the dictionary evaluates matching names:
[See image.](#ZIA-DLP-NamesDictionariesActionOption-RN)
To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).
Update to Cloud Service API
The `/dlpDictionaries` endpoints within the cloud service API is updated to support a new `predefinedCountActionType` field within the request body to specify whether duplicate matches of a phrase must be counted individually toward the match count or ignored in [predefined Names dictionaries](/zia/understanding-predefined-dlp-dictionaries).
To learn more, see the [API Reference](/zia/about-api).
[] ![The Action Options for the Names DLP Dictionaries](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-DLP-NamesDictionariesActionOption.png)

## September 11, 2023
### Feature Available
#### Maintenance Mode for ZIA Admin Portal
During a scheduled ZIA upgrade, the ZIA Admin Portal switches to maintenance mode. In this mode, you can only view the Dashboard data and navigate through the ZIA Admin Portal, but cannot configure or edit any parameters. Also, the API operations that use POST, PUT, or DELETE methods fail during the maintenance mode and return the 403 response code.
After the upgrade is complete, the ZIA Admin Portal automatically refreshes and switches back to edit mode.
To learn more, see [About the ZIA Admin Portal](/zia/about-zia-admin-portal).

## September 08, 2023
### Feature Available
#### Additional Actions for GitHub Application in Cloud Application Control Policy
In the Add System & Development Rule window for the GitHub application, the following actions are newly added:
- Creating
- Editing
- Sharing
- Commenting
- Reacting
This allows you to granularly control the actions for this application.
[See images.](#s-d-cac-rule)
To learn more, see [Adding a System & Development Rule for Cloud App Control](/zia/adding-system-development-rule-cloud-app-control).
[]![Screenshot of ZIA Add System & Development Rule window for GitHub](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Add-System-Development-Rule-RN.png)

### Feature Available
#### Support for Domain Profiles and Removing File Share App Collaborators in SaaS Security API DLP Policies
ZIA users can create and edit domain profiles (Administration > Domain Profiles) for use in the creation of SaaS Security API Data Loss Prevention (DLP) and cloud app control rules.
[See image.](#domain_main)
To use domain profiles in SaaS Security API Control Data Loss Prevention (Policy > SaaS Security API Control > File Sharing > Data Loss Prevention > Policy > Add DLP Rule), select a SaaS Application Tenant. Then choose to remove external collaborators for the action and select the desired domain profiles and whether you want to include or exclude the collaborators in the selected domain profiles.
[See image.](#domain_collab)
To learn more, see [About Domain Profiles](/zia/about-domain-profiles), [Adding Domain Profiles](/zia/adding-domain-profiles) and [Configuring the SaaS Security API DLP Policy](/zia/configuring-saas-security-api-dlp-policy).
[]![Domain profile page in ZIA.](/sites/default/files/downloads/zia/adding-domain-profiles/Domain_main.png)
[]![Removing External Collaborator Functionality](/sites/default/files/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Remove%20External%20Collaborators_Email%20Recipient%20Domain%20Profiles.png)

## September 04, 2023
### Feature Available
#### Enhancements to Workflow Automation
The following enhancements are available in Workflow Automation:
- Endpoint DLP incidents are displayed in Workflow Automation. You can remediate these incidents using the various actions on the Incident and Incident Detail pages in Workflow Automation and through the predefined workflows provided by Workflow Automation.
[See image.](#endpoint-incidents)
- The data protection incidents that have violated the policies (DLP, Saas Security API, and Endpoint DLP) are displayed on the Incidents page and the Incident Details page in the local time zone of the user. They used to be displayed in the GMT (UTC) time zone.
- The Incident Details page is enhanced with a Next Incident icon and Previous Incident icon at the top of the page. These icons enable you to traverse to the next or previous incident as per the list of incidents seen on the Incidents page.
[See image.](#previous-next-icons)
- The Incidents page is enhanced to include Current Day in the time range field.
[See image.](#current-day)
- The Close Incident action is enhanced on the Incidents page and the Incident Details page. When closing an incident, you can add a resolution label to associate with the ticket closure.
[See image.](#close-incident-action)
- Workflow enhancements:
- The new Auto Close Data Loss Protection Incident With Resolution Label Workflow template is available. This template enables you to automatically close incidents with a resolution label that you specify.
- The Auto Close Data Protection Incident Workflow template has been removed. The new Auto Close Data Loss Protection Incident With Resolution Label template replaces this template.
[See image.](#workflow-templates)
To learn more, see [About Incidents](/zia/about-incidents), [Viewing & Managing Incident Details](/zia/viewing-managing-incident-details), and [Understanding Workflows in Workflow Automation](/zia/understanding-workflows-workflow-automation).
[]![Viewing Endpoint Incidents on the Incidents Page in the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-190-Release-Notes-Incidents-Page.png)
[] ![Viewing the Next Incident icon and Previous Incident icon on the Incident Details page in the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-190-Release-Notes-Incident-Details-Page.png)
[] ![Viewing the time range options on the Incidents page in the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-190-Release-Notes-Incidents-Page-time-range.png)
[]![Viewing the close incident window in the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-190-Release-Notes-Close-Incident-Window.png)
[] ![Viewing the list of Workflow templates on the Workflow Template page in the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-190-Release-Notes-Workflow-Templates-Page-New-Close-Workflow.png)

## September 01, 2023
### Feature Available
#### Enhancement to Virtual Service Edge
The Deployment Status field with the following values is added to the Add Virtual Service Edge window (Administration > Virtual Service Edges > Add Virtual Service Edge):
- In Production
- Trial
With this feature, you can differentiate a Virtual Service Edge instance for production from internal uses or test purposes.
[See image.](#add-vse-deployment-status)
To learn more, see [Adding Virtual Service Instances](/zia/adding-virtual-service-edge-instances).
[]![Screenshot of ZIA Add Virtual Service Edge with Deployment Status](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Add-Virtual-Service-Edge-Deployment-Status-RN.png)

### Feature Available
#### Enhancements to Advanced Threat Protection Policy
The Advanced Threat Protection Policy includes an option to block domains that are suspected to be generated by Domain Generation Algorithms (DGA).
[See image.](#domain-generation-algorithm-domains)
In addition:
- You can block these domains via the DNS Control policy or IPS Control policy by selecting the appropriate options in the fields shown in the following image:
[See image.](#dns-filtering-rule-block-dga-domains)
- A new option, Domain Generation Algorithm (DGA) Domains, is added under the Advanced Threat Category filter on the following pages:
- Web Insights Logs
- Firewall Insights Logs
- Mobile Insights Logs.
[See image.](#dga-option-web-logs)
To learn more, see [Configuring the Advanced Threat Protection Policy](/zia/configuring-advanced-threat-protection-policy), [Configuring the DNS Control Policy](/zia/configuring-dns-control-policy), [Configuring the IPS Control Policy](/zia/configuring-ips-control-policy), [Web Insights Logs: Filters](/zia/web-insights-logs-filters), [Firewall Insights Logs: Filters](/zia/firewall-insights-logs-filters), [Mobile Insights Logs: Filters](/zia/mobile-insights-logs-filters), [About SaaS Security Insights Logs,](/zia/saas-security-insights-logs) and [Web Data Types and Filters](/zia/web-data-types-and-filters).
[]![Domain Generation Algorithms (DGA) Domains](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/logs/firewall-insights-logs-filters/ZIA-6.2r-Domain-Generation-Algorithm-option-web-logs.png)
[]![Support for blocking DGA domains using Advanced Threat Protection](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/block-DGA-domains-ATP.png)
[]![Support for blocking DGA domains in DNS and IPS Control rules](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/DGA-domains-dns-ips-rules.png)

### Feature Available
#### SaaS Security API
The following enhancements are available for SaaS Security API.
Updates to SaaS Security API Scan Configuration
You can select the Source Code Repository applications to set scanning schedules manually or automatically for DLP or Malware rules. You can also see a scannable and unscannable repositories list based on the selected application.
[See image.](#googlecloudplatform-bucketstabel)
To learn more, see [Configuring SaaS Security API Scan Schedules](/zia/configuring-saas-security-api-scan-schedules).
Updates to the SaaS Assets Report
The SaaS Assets Report for the Source Code Repository category is enhanced with:
- A relevant overview section for the source code repository category.
- Two new tabs: Scanned Repositories and Unscanned Repository.
- The existing information moved inside the Files tab.
[See image.](#saas-assets-report-img)
To learn more, see [SaaS Assets Report](/zia/saas-assets-report).
[] ![SaaS Assets Report](/sites/default/files/downloads/zia/dashboard-analytics/reports/about-cybersecurity-insights/ZIA-6.2r-SaaS-Assets-Report.png)
[]![The Google Cloud Platform Buckets table for the Add Scan Schedule window](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/configuring-saas-security-api-scan-schedules-draft/Google%20Cloud%20Platform%20Buckets.png)

### Feature Available
#### Support in SaaS Security API DLP Policy for Quarantine of Sensitive Content in Slack
The SaaS Security API Control policy supports a new option to quarantine sensitive content in Slack. You can specify a tombstone message that end users see when messages or files in Slack are quarantined.
[See image.](#ZIA-Slack-CASB-Quarantine)
After a message or file has been quarantined in Slack, admins can use the SaaS Assets Report to review and remove the quarantined content.
[See image.](#ZIA-Slack-SaaS-Assets-Report-Quarantine)
To learn more, see [Configuring the SaaS Security API DLP Policy](/zia/configuring-saas-security-api-dlp-policy), [About Quarantine Tombstone File Templates](/zia/about-quarantine-tombstone-file-templates), and [SaaS Assets Report: Assets with Incidents](/zia/saas-assets-report-assets-incidents).
[] ![The Selection Options for Quarantine of Sensitive Content in Slack](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Slack-CASB-Quarantine-RN.png)
[] ![Options to Remove or Restore Quarantined Slack Content in the SaaS Assets Report](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Slack-SaaS-Assets-Report-Quarantine-RN.png)

### Feature Available
#### Support in SaaS Security API DLP Policy for Quarantine to User Root Folder
The SaaS Security API Control policy supports a new option to quarantine sensitive content to a user's root folder in Box, OneDrive, and SharePoint. Additionally, you can select a tombstone template that is used to create a tombstone file that replaces the quarantined file in its original location to explain the quarantine action to end users.
[See image.](#ZIA-Box-SP-OD-CASB-QuarantineToRoot)
Admins can also use the SaaS Assets Report to manually move incident-reported files to a user's root folder.
[See image.](#ZIA-Box-SP-OD-SaaS-Assets-Report-QuarantineToRoot)
Admins can then use the SaaS Assets Report to remove or restore the quarantined files.
[See image.](#ZIA-Box-SP-OD-SaaS-Assets-Report-RemoveRestore)
You can filter the SaaS Security logs sent via Nanolog Streaming Service (NSS) to your security information and event management (SIEM) system based on the quarantine action.
[See image.](#nss-policy-action-filter)
To learn more, see [Configuring the SaaS Security API DLP Policy](/zia/configuring-saas-security-api-dlp-policy), [About Quarantine Tombstone File Templates](/zia/about-quarantine-tombstone-file-templates), [SaaS Assets Report: Assets with Incidents](/zia/saas-assets-report-assets-incidents), and [Adding NSS Feeds for SaaS Security Logs](/zia/adding-nss-feeds-saas-security-logs).
[] ![The Selection Option for Quarantine to Root Folder for Sensitive Files in Box](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Box-CASB-QuarantineToRoot-RN.png)
[] ![Option to Quarantine to Root Folder for Sensitive Files in Box, OneDrive, or SharePoint in the SaaS Assets Report](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Box-SaaS-Assets-Report-QuarantineToRoot-RN.png)
[] ![Options to Remove or Restore Quarantined Box, OneDrive, or SharePoint Content in the SaaS Assets Report](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Box-SaaS-Assets-Report-RemoveRestore-RN.png)
[![Screenshot of Policy Action filter in NSS feed for SaaS Security logs](/sites/default/files/downloads/nss_policy_action_quarantine_user_root_folder_0.png)
]

### Feature Available
#### Updates to Cloud Service API
The cloud service API includes the following new endpoints to obtain geographical information about the region or a city in order to use it for specific configurations in the ZIA Admin Portal:
- `GET /region/byGeoCoordinates`
- `GET /region/byIPAddress/{ip}`
- `GET /region/search`
These endpoints allow you to retrieve the geographical information by specifying the geographical coordinates or the IP address, or by running a prefix search using the city name.
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection has also been updated to include the new resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

## August 31, 2023
### Feature Available
#### 3rd-Party App Governance SSO Integration in Reports
[Zscaler AppTotal](/zia/what-apptotal) allows you to discover, manage, reduce, and control the attack surface introduced by third-party apps, extensions, and add-ons to corporate SaaS platforms (e.g., Google Workspace, Microsoft 365, etc.). With 3rd-Party App Governance, you can uncover and maintain an up-to-date app inventory, gaining full visibility into what is connected, the risks posed, and how each app is used in your environment. You can effectively govern your environment by monitoring an app's usage, security posture, and compliance. You can then manually or automatically streamline remediation actions (e.g., classifying an app as unsanctioned, revoking an app token, etc.) all within a centralized console.
A new option, AppTotal, is available under Analytics > Reporting. This option allows you to access the 3rd-Party App Governance Admin Portal from the ZIA Admin Portal using SSO.
[See image.](#AppTotal-SSO-Link)
To learn more, see [Accessing and Navigating the 3rd-Party App Governance Admin Portal](/zia/accessing-and-navigating-apptotal-admin-portal).
Contact Zscaler Support to configure the subscription for your tenant to include 3rd-Party App Governance.
[]![Screenshot of AppTotal SSO Link](/sites/default/files/downloads/ZIA_SSO_AppTotal.png)
Select 3rd-Party App Governance data has been integrated into the SaaS Security Report in the ZIA Admin Portal, providing the following enhancements:
Shadow IT Report
In the Shadow IT Report (Analytics > SaaS Security Report > Applications), a dashboard widget shows the number of applications that have access to your corporate SaaS platforms. In the Cloud Applications table, if the number in the Integrations column is greater than zero, then the application has access.
[See image.](#img-shadow-it-dashboard-widget)
In the Cloud Applications table, two corresponding columns have been added: Integrations and Integration Risks. Also, the Risk Index column has been renamed to Application Risk Index.
[See image.](#img-shadow-it-cloud-apps-table)
Application Information Page
When you select an application in the Shadow IT Report, you can view three data-rich tabs within the Application Information page, providing insight into the application’s risk attributes, third-party integrations (if applicable), and usage:
- [Risk Attributes](#risk-attributes)
- [3rd-Party Integrations](#3rd-party-integration)
- [Usage](#usage)
SaaS Assets Report
In the SaaS Assets Report (Analytics > SaaS Security Report > Assets), the 3rd-Party Integrations tab has been added to the following applications:
- Collaboration Applications (Slack, Microsoft Teams)
- File Sharing Applications (OneDrive, SharePoint, Google Drive)
- Email Applications (Exchange, Gmail)
- CRM Applications (Salesforce)
The tab is populated by 3rd-Party App Governance data if the application has third-party integrations. The tab shows the total number of integrations as well the number of integrations that are considered potentially harmful, dormant, and overprivileged.
[See image.](#img-saas-assets-3rd-party-apps-tab)
If you have a subscription to 3rd-Party App Governance, you can go directly to the [3rd-Party App Governance Admin Portal](https://apptotal.zscaler.com/) from multiple locations in the SaaS Security Report. If you do not have a subscription, the same links direct you to [learn more about 3rd-Party App Governance](https://www.zscaler.com/platform/third-party-app-security).
To learn more, see [About Shadow IT Report](/zia/about-shadow-it-report), [About Application Information](/zia/about-application-information), and [About SaaS Assets Report](/zia/saas-assets-report).
[]The Risk Attributes tab shows basic, hosting, and security information about the application. New fields have been added to the Basic Information and Hosting Information sections. The fields are populated with 3rd-Party App Governance data if applicable to the application. Data includes the number of integrations associated with the application, any certifications (e.g., HIPAA) claimed by the application, as well the application's data residency and retention details.
[See image.](#img-risk-attributes)
[]The 3rd-Party Integrations tab shows a table populated with 3rd-Party App Governance data if applicable to the application. The table lists the application’s third-party integrations with your corporate SaaS platforms (e.g., Google Workspace) and details their unique security posture.
[See image.](#img-3rd-party-integration)
[]The Users and Location tables have been relocated to the Usage tab.
[See image.](#img-usage)
[![Shadow IT Report dashboard widget with Zscaler AppTotal data](/sites/default/files/downloads/zia/dashboard-analytics/reports/about-application-information/application_access_widget.png)
]
[![Cloud Applications table with Zscaler AppTotal columns in Shadow IT Report](/sites/default/files/downloads/zia/dashboard-analytics/reports/about-application-information/zia_saas_security_report_cloud_applications_columns.png)
]
[![Risk Attributes tab on the Application Information page of the SaaS Security Report](/sites/default/files/downloads/zia/dashboard-analytics/reports/about-application-information/zia_saas_security_risk_attributes_tab.png)
]
[![3rd Party Integration tab on the Application Information page of the SaaS Security Report](/sites/default/files/downloads/shadowIT_3rd_party_integrations.png)
]
[![Usage tab on the Application Information page of the SaaS Security Report](/sites/default/files/downloads/usage_tab.png)
]
[![3rd-Party Integrations tab with Zscaler AppTotal data in SaaS Assets Report](/sites/default/files/downloads/zia/dashboard-analytics/reports/about-application-information/saas_assets_3rd_party_integrations.png)
]

### Feature Available
#### DLP Support for New PII Dictionaries
The following new predefined DLP dictionaries allow you to select one or more subdictionaries to detect specific kinds of sensitive information:
- [Credentials and Secrets](#CredentialsAndSecrets)
- [Driver's License (United States)](#USDL)
- [Passport Numbers (European Union)](#EUPassport)
To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).
The Data Loss Prevention resources within the cloud service API have also been updated to include a new `GET /dlpDictionaries/{dictId}/predefinedIdentifiers` endpoint to retrieve the list of identifiers that are available for selection within the newly introduced DLP dictionaries. In addition, the following new attributes are added to the `/dlpDictionaries` endpoints:
- `hierarchicalIdentifiers`: Indicates whether a DLP dictionary is hierarchical
- `hierarchicalDictionary`: The list of identifiers selected within a hierarchical dictionary
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection has also been updated to include new and updated resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).
[]This dictionary allows you to select one or more credentials and secrets dictionaries (i.e., tokens, keys, passwords, etc.) for the following:
- Amazon MWS Auth Token
- Git Token
- GitHub Token
- Google API Key
- Google OAuth Access Token
- Google OAuth ID
- JWT Token
- PayPal Braintree Access Token
- Picatic API Key
- Private Key
- SendGrid API Key
- Slack Access Token
- Slack Webhook
- Square Access Token
- Square OAuth Secret
- Stripe API Key
[See image.](#CredentialsAndSecrets_Screenshot)
[] ![The Selection Options for the Credentials and Secrets DLP Dictionary](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-CredentialsAndSecrets-RN.png)
[]This dictionary allows you to select driver's license dictionaries for one or more of the 50 U.S. states plus the District of Columbia.
[See image.](#USDL_Screenshot)
[] ![The Selection Options for the United States Driver's License DLP Dictionary](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-US_DL-RN.png)
[]This dictionary allows you to select passport number dictionaries for one or more European Union countries.
[See image.](#EUPassport_Screenshot)
[] ![The Selection Options for the European Union Passport DLP Dictionary](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-EUPassport-RN.png)

### Feature Available
#### Endpoint Data Loss Prevention
You can use Endpoint Data Loss Prevention (DLP) policies to monitor end-user activities that involve sensitive data on endpoints, including printing, uploading to personal cloud accounts, saving to removable storage, and saving to network shares. Additionally, you can monitor activity with dashboards and reports, and NSS feeds.
- [Endpoint DLP Rules and Resources](#endpoint-dlp-rules-resources)
- [Endpoint DLP NSS Feeds and Logs](#endpoint-dlp-nss)
- [Endpoint DLP Dashboards, Reports, and Logs](#endpoint-dlp-reports-dashboards)
End users can view and configure Endpoint DLP information in Zscaler Client Connector. To learn more, see [Configuring Zscaler Client Connector Profiles](/client-connector/configuring-zscaler-client-connector-profiles).
[]Zscaler's Endpoint DLP policy allows you to protect your organization from data loss on endpoints (i.e., printing, saving to removable storage, saving to network shares, or uploading to personal cloud storage accounts).
You can use Zscaler's custom and predefined DLP engines to detect sensitive data, allow or block activities, and notify your organization's auditor when a user's activity on an endpoint triggers an Endpoint DLP rule. When you configure and activate Endpoint DLP policy in ZIA, endpoints automatically use Zscaler Client Connector to retrieve the policy from the Zscaler cloud. After that, the DLP policy is enforced and incidents are logged even if endpoints don't have a network connection.
In the ZIA Admin Portal, you can add DLP resources (Administration > DLP Resources), and then use those resources to configure Endpoint DLP policy rules (Policy > Endpoint Data Loss Prevention).
To learn more, see [Step-by-Step Configuration Guide for Zscaler Endpoint DLP](/zia/step-by-step-endpoint-dlp) and [About Endpoint DLP](/zia/about-endpoint-dlp).
[]A new log type, Endpoint DLP, is available for the Nanolog Streaming Service (NSS). You can configure an NSS feed or Cloud NSS feed to stream Endpoint DLP log data from ZIA to your security information and event management (SIEM) system.
[See image.](#img-zia-nss-endpoint-dlp)
To learn more, see [Adding NSS Feeds for Endpoint DLP Logs](/zia/adding-nss-feeds-endpoint-dlp-logs), [Adding Cloud NSS Feeds for Endpoint DLP Logs](/zia/adding-cloud-nss-feeds-endpoint-dlp-logs), and [NSS Feed Output Format: Endpoint DLP Logs](/zia/nss-feed-output-format-endpoint-dlp-logs).
[]The following new pages are added to monitor and view logs for the Endpoint DLP activities:
- Endpoint DLP Insights (Analytics > Endpoint DLP Insights > Insights)
- Endpoint DLP Insights Logs (Analytics > Endpoint DLP Insights > Logs)
- Endpoint DLP Report (Analytics > Endpoint DLP Report)
- Endpoint DLP Dashboard (Dashboard > Endpoint DLP)
To learn more, see [Endpoint DLP Insights Logs: Filters](/zia/endpoint-dlp-insights-logs-filters), [Endpoint DLP Insights Logs: Columns](/zia/endpoint-dlp-insights-logs-columns), [Endpoint DLP Data Types and Filters](/zia/endpoint-dlp-data-types-and-filters), [About Endpoint DLP Report](/zia/about-endpoint-dlp-report), and [About Dashboards](/zia/about-dashboards).
[![Screenshot of the Endpoint DLP log type in the Add NSS Feed window in the ZIA Admin Portal](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/nss/nss-feeds/adding-nss-feeds/adding-nss-feeds-firewall-logs/zia_nss_feed_endpoint_dlp.png)
]

### Feature Available
#### Enhancement to Advanced Threat Protection Policy
The Advanced Threat Protection Policy can analyze URLs using the AI/ML tools to detect C2 botnets, credential theft, and phishing URLs to categorize them under one of the following categories:
- Fraud Protection (Phishing)
- Botnet Protection
- Miscellaneous or Unknown
The AI/ML tools analyze only the URLs under the Miscellaneous or Unknown category and the uncategorized URLs.
To learn more, see [Configuring the Advanced Threat Protection Policy](/zia/configuring-advanced-threat-protection-policy) and [About Threat Categories](/zia/about-threat-categories#threat-category-list).

### Feature Available
#### Flattened PDF and Sandbox Options for File Transfers in Isolation
Admins can enable and select the option per ZIA isolation profile for how the user downloads file transfers. Users can download files as a flattened PDF version, which renders it with no active content, a sandbox-scanned file version, or the original file.
[See image.](#flatpdf)
To learn more, see [Sandbox Integration with Isolation](/isolation/sandbox-integration-isolation), [Creating Isolation Profiles for ZIA](/isolation/creating-zia-isolation-profile-isolation), and [Transferring and Viewing Files in Isolation](/isolation/transferring-and-viewing-files-cloud-browser-isolation).
[![Enable or disable the options in the Security section.](/sites/default/files/downloads/isolation/profiles/zia-profiles/editing-your-isolation-profile-zia/sandbox-enable.png)
]

### Feature Available
#### Introducing Cybersecurity Insights
The new Cybersecurity Insights page (Analytics > Cybersecurity Insights) provides a unified real-time visibility into critical security incidents and policy actions to understand the security efficacy of layered defense across [Advanced Threat Protection](/zia/configuring-advanced-threat-protection-policy) (ATP), [Sandbox](/zia/about-sandbox), [Firewall](/zia/configuring-firewall-policies), and [Isolation](/isolation/what-isolation) for your organization. You can view metrics for different types of threat incidents that Zscaler blocked, such as the threat category, number of threats, and attack trends, among many other things.
The page also displays information about new threat protection that Zscaler has equipped your organization with. You can read the complete blog or article on the threat written by our ThreatLabZ team across various media outlets referenced from this page. Also, it integrates the Threat Insights data that was previously viewed separately.
[See image.](#cybersecurity-insights-img)
To learn more, see [About Cybersecurity Insights](/zia/about-cybersecurity-insights).
![Cybersecurity Insights in ZIA Admin Portal](/sites/default/files/downloads/risk360/getting-started/what-risk360/ZIA-6.2r-Cybersecurity-Insights-page.png)
[]

### Feature Available
#### New Cloud Application Category
The AI & ML Applications category is newly added to the Cloud App Control Policy page (Policy > URL & Cloud App Control > Cloud App Control Policy > Add). It includes applications that support artificial intelligence and machine learning.
[See image.](#ai-ml-cloud-app)
To learn more, see [Understanding Cloud App Categories](/zia/understanding-cloud-app-categories).
[]![Screenshot of ZIA Cloud App Control Policy with AI & ML Category](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Cloud-App-Control-Policy-AI-ML-RN.png)

### Feature Available
#### Quarantine and Isolate in Sandbox Policy
Sandbox and browser isolation integration allows users to access unknown Microsoft Office and PDF documents as view-only in an isolated browser in real-time without waiting for the final sandbox verdict. The end user can download the file if the verdict is benign in the original file. If the sandbox verdict is suspicious or malicious, you can choose to receive a flattened PDF after content disarmament to remove the suspicious or malicious content. To learn more, see [Configuring Sandbox Policy](/zia/configuring-sandbox-policy).
[See image.](#QandI)
[]![Quarantine and Isolate feature for Sandbox Policy](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/configuring-sandbox-policy-doc-51356-ben-h/Quarantine%20and%20Isolate.png)

### Feature Available
#### Support for Inspecting ZPA Application Segment Traffic
A predefined forwarding rule, ZIA Inspected ZPA Apps, is available on the Policy > Forwarding Control page to inspect the Microtunnel traffic of a ZPA application segment using ZIA. This rule is applied automatically to the traffic from ZPA application segments with the Inspect Traffic with ZIA field enabled in the ZPA Admin Portal.
[See image.](#zia-inspected-zpa-apps-predefined-rule)
As part of this feature, a predefined Auto ZPA Gateway is available on the Administration > Zscaler Private Access Gateway page. This new gateway is the default gateway for the predefined ZIA Inspected ZPA Apps forwarding rule.
[See image.](#auto-zpa-gateway-predefined-rule)
To learn more, see [Configuring Forwarding Policy](/zia/configuring-forwarding-policy) and [About Zscaler Private Access Gateway](/zia/about-zpa-gateway).
![Screenshot of the ZIA Inspected ZPA Apps predefined rule in the Forwarding Control page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/zia-RN-forwarding-control-predefined-rule-zia-inspected-zpa-apps.png)
[]
![Screenshot of the Auto ZPA Gateway predefined rule in Zscaler Private Access Gateway page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/zia-RN-zpa-gateway-predefined-rule-auto-zpa-gateway.png)
[]

### Feature Available
#### Support for Okta and GitHub Integration with 3rd-Party App Governance
You can connect your Okta and GitHub organizations to Zscaler 3rd-Party App Governance to gain continuous visibility and governance for third-party apps installed in these environments, including automation of your vetting and governance processes.
[See image.](#Okta-Integration-Window)
[]![Screenshot of Okta Integration Window](/sites/default/files/downloads/Okta%20GitHub%20Integration%20Window.png)
To learn more, see [Integrating with Okta](/zia/integrating-okta) and [Integrating with GitHub](/zia/integrating-github).

### Feature Available
#### Support for Okta as SAML IdP in 3rd-Party App Governance
Zscaler 3rd-Party App Governance supports identity provider (IdP)-initiated SAML to authenticate admins and users logging in to the 3rd-Party App Governance Admin Portal. This feature enables users to securely access 3rd-Party App Governance using their organization credentials without the need to remember multiple passwords. It also helps to ensure that users adhere to their organizational guidelines regarding passwords and secure authentication. You can configure Okta as an IdP in 3rd-Party App Governance.
You must contact Zscaler Support to complete the configuration process.
To learn more, see [SAML Configuration Guide for Okta](/zia/saml-configuration-guide-okta).

### Feature Available
#### Updates to Sandbox Submission API
The AI-Powered Deep Inspection using Sandbox Submission API supports out-of-band file inspection for known and unknown files. It generates real-time verdicts for the files and classifies them as benign or malicious by leveraging capabilities such as Malware Prevention, Advanced Threat Protection, Sandbox cloud effect, AI/ML-driven file analysis, and integrated third-party threat intelligence feeds.
All file types supported by Malware Protection and Advanced Threat Protection policy can be inspected with an increased file size of up to 400 MB and a larger volume of the files.
To learn more about the endpoint, see the [API Reference](/zia/about-api).

## August 30, 2023
### Feature Available
#### Recent Risk Increases Section in the User Risk Report
The user risk report includes the following enhancements to the ZIA Admin Portal:
The Recent Risk Increases Section
The Overview Section of the User Risk Report is enhanced with the Recent Risk Increases section.
[See image.](#recent-risk)
To learn more, see [About the User Risk Report](/zia/user-risk-report).
Enable Real-Time Risk Score Updates
You can view the recent risk increases in the User Risk Report when the real-time risk score is enabled in the Advanced Settings (Administration > Advanced Settings).
[See image.](#real-time)
To learn more, see [Configuring Advanced Settings](/zia/configuring-advanced-settings).
[]![Recent Risk Increases Section screenshot](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/rn-draft/Recent%20Risk%20Score.png)
[]![Enable Real Time Risk Score Updates screenshot](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/rn-draft/Recent%20Risk%20Score%20RN.png)

## August 29, 2023
### Feature Available
#### Enhanced SaaS Security Posture Control
The following enhancements are available for SaaS Security Posture Control in the ZIA Admin Portal:
SaaS Security Posture Control
The SaaS Security Posture Control page (Policy > SaaS Security Posture Control) lists all the predefined policies supported by the SaaS application and allows you to enable or disable various posture control policies based on your business requirements.
For each application and tenant, you can filter the Policy table to display Risk Level, Compliance Check, and Status. Each policy further opens a drawer that provides general information about the selected policy including the resource type, the risk level, the description, and the potential threat if the policy is not implemented.
[See image.](#saas-security-posture-control-page)
SaaS Security Posture Report
The SaaS Security Posture Report (Analytics > SaaS Security Report > Security Configuration) provides more easy-to-read widgets and information on the incidents and attributes to help you better understand the risks and have better posture control at your organizational level.
The SaaS Security Posture Report is updated with the following enhancements:
- A new widget for a Compliance centric view of the policies applicable for each compliance with their statuses.
- A new drawer that provides you with more context about the scan results. The drawer opens for each policy to show the Policy Overview, Asset Summary, and Remediation Steps.
- The filter options are moved to the top of the page to populate the entire report as per your filter selections.
- New columns (i.e., Total Assets, Failed Assets, Excluded Assets, and Partial Assets) are added to the Policies table.
[See image.](#sspm-report)
To learn more, see [Configuring the SaaS Security Posture Policy](/zia/configuring-saas-security-posture-control-policy) and [SaaS Security Posture Report](/zia/about-saas-security-posture-report).
[] ![The SaaS Security Report](/sites/default/files/downloads/zia/dashboard-analytics/reports/about-cybersecurity-insights/ZIA-6.2r-SSPM-Report.png)
[]![The SaaS Security Posture Control page displays a list of all posture control policies that you can enable or disable.](/sites/default/files/downloads/ZIA-SaaS-Security-Posture-Control-Policy.png)

### Feature Available
#### SaaS Security Posture Management Support for ServiceNow
You can configure SaaS Security Posture Management (SSPM) policy for ServiceNow tenants. Select the SSPM checkbox when onboarding a ServiceNow tenant to enable the SSPM scan capability for the specific tenant. Existing users can also enable the SSPM support by selecting the SSPM checkbox under the onboarding section for the specific tenants, and then validating and saving the changes.
[See image.](#servicenow-sspm-onboarding)
To learn more, see [Supported SaaS Security Posture Control Policies](/zia/supported-saas-security-posture-control-policies)[,] [Configuring the SaaS Security Posture Policy](/zia/configuring-saas-security-posture-control-policy), and [SaaS Security Posture Report](/zia/about-saas-security-posture-report).
[]![The tenant onboarding page allows you to select multiple functionalities based on your organizational requirements.](/sites/default/files/downloads/zia/policies/saas-security-api/saas-security-api-policies/saas-security-posture-management/supported-saas-security-posture-control-policies/SaaS%20Tenant%20Onboarding%20Settings.png)

### Feature Available
#### Sandbox for Zero-Day Threat Protection
Zscaler extends its Sandbox capability to offer advanced protection against zero-day threats. An exclusive virtual machine that is up to date with the latest security patches is included to identify and analyze true zero-day threats. Zscaler detonates sample files of zero-day exploits in this fully patched, controlled, and isolated environment to observe the behavior of malicious files and determine whether the file is a zero-day threat. This functionality leverages the MITRE ATT&CK framework to detect, organize, and prioritize the Indicators of Compromise (IoC) to help understand the threat behavior and attack movement. It can serve as a tool for forensics and threat hunting, enabling cybersecurity professionals, security operations center (SOC) teams, and Security Engineers to study and understand zero-day threats and mitigate security incidents. This extended functionality is available on a subscription basis.

### Feature Available
#### Support for User Enrollment to ZIA Service from ZSLogin
You can use ZSLogin to enroll users in the ZIA service.
To support this feature:
- The following pages are view-only with limited options in the ZIA Admin Portal with a ZSLogin subscription:
- [Users](/zia/about-users) (Administration > User Management > Users)
- [Groups](/zia/about-groups) (Administration > User Management > Groups)
- [Departments](/zia/about-departments) (Administration > User Management > Departments)
- [Default Settings](/zia/about-authentication-default-settings) (Administration > Authentication Settings)
- The following pages are unavailable in the ZIA Admin Portal with a ZSLogin subscription:
- [Identity Providers](/zia/about-identity-providers) (Administration > Authentication Settings > Identity Providers)
- [Authentication Bridges](/zia/about-zscaler-authentication-bridge) (Administration > Authentication Settings > Authentication Bridges)
- [Authentication Profiles](/zia/about-authentication-profiles) (Administration > Authentication Settings > Authentication Profiles)
The features in the preceding pages are either moved to the ZSLogin Admin Portal or are no longer required with a ZSLogin subscription.
To learn more, see [ Accessing and Navigating the ZSLogin Admin Portal](/zslogin/accessing-and-navigating-zslogin-admin-portal) and [What Is ZSLogin?](/zslogin/what-zslogin)

### Feature Available
#### Support Large Number of Cloud Applications
The ZIA Admin Portal supports more than 40K additional predefined cloud applications across various cloud application categories. This allows you to manage traffic, view data in interactive charts, analyze traffic through charts, and view every transaction performed for the newly added cloud applications.
As part of this change, the following enhancements are made to the ZIA Admin Portal:
Dashboard
The newly added lesser-known predefined cloud applications for a category (e.g., Finance) are grouped under the Miscellaneous <Cloud Application Category> Apps (e.g., Miscellaneous Finance Apps) in the widgets of the Cloud Application dashboard (Dashboard > Cloud Applications). You can also view logs or analyze charts for these Miscellaneous <Cloud Application Category> Apps.
[See image.](#misc-in-dashboard)
To learn more, see [About Dashboards](/zia/about-dashboards#cloud-applications).
Policies
You can manage traffic to the newly added lesser-known predefined cloud applications using the policies. As part of this change, the infinite scrolling nested list is replaced with a paginated list containing 100 applications per page. This significantly improves the performance and load time of the applications.
[See image.](#cloud-apps-with-pagination)
To learn more about selecting these Cloud Applications, see:
- [Adding Rules to the Cloud App Control Policy](/zia/adding-rules-cloud-app-control-policy)
- [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection)
- [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection)
- [Configuring the File Type Control Policy](/zia/configuring-file-type-control-policy)
- [Configuring SSL Inspection Policy](/zia/configuring-ssl-inspection-policy)
Administration
For the newly added lesser-known predefined cloud applications, you can add bandwidth classes, exempt from authentication, and exempt from DLP evaluation. As part of this change, the infinite scrolling nested list is replaced with a paginated list containing 100 applications per page in the following places:
- Cloud Applications field on the Bandwidth Classes page
- Exempted Applications on the Advanced Settings page
- Exempted Cloud Applications fields on the DLP Advanced Settings page
This significantly improves the performance and load time of the applications.
[See images.](#admin-cloud-app-options)
To learn more about selecting these Cloud Applications, see [Adding Bandwidth Classes](/zia/adding-bandwidth-classes), [Exempting URLs and Cloud Apps from Authentication](/zia/exempting-urls-cloud-apps-authentication), and [Exempting Cloud Apps and URLs from DLP Evaluation](/zia/exempting-cloud-apps-and-urls-dlp-evaluation).
Reports & Insights Logs
The newly added lesser-known predefined cloud applications for different application categories (e.g., Finance) are grouped under the Miscellaneous <Cloud Application Category> Apps (e.g., Miscellaneous Finance Apps) options under the Cloud Application filter on the Web Insights and Insights Logs page.
The Shadow IT Report (Analytics > SaaS Security Report > Applications) now supports more than 40K applications.
[See images.](#cloud-app-filter)
To learn more, see [Web Insights Logs: Filters](/zia/web-insights-logs-filters) and [About Shadow IT Report](/zia/about-shadow-it-report).
NSS
The Miscellaneous <Cloud Application Category> Apps (e.g., Finance > Miscellaneous Finance Apps) option is available in the Cloud Applications filter (To Where > Cloud Applications) when configuring NSS and Cloud NSS feeds for web logs as well as MCAS feeds.
[See image.](#img-nss-cloud-apps-filter)
To learn more, see [Adding NSS Feeds for Web Logs](/zia/adding-nss-feeds-web-logs), [Adding Cloud NSS Feeds for Web Logs](/zia/adding-cloud-nss-feeds-web-logs), and [Adding MCAS NSS Feeds](/zia/adding-mcas-nss-feeds).
[]![Screenshot of ZIA Cloud Applications Dashboard with Miscellaneous <Cloud Application Category> Name](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Cloud-Applications-Dashboard-RN.png)
[]![Screenshot of ZIA Add Cloud Application Rule with Click to See More in the Cloud Applications Field](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Add-Cloud-App-Control-Rule-Window-Click-See-More-RN.png)
[![Screenshot of the Cloud Applications filter with the Miscellaneous Apps option selected](/sites/default/files/downloads/zia_nss_cloud_apps_misc_apps.png)
]
[]![Screenshot of ZIA Add Bandwidth Classes with Cloud Applications field](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Add-Bandwidth-Classes-RN.png)
![Screenshot of ZIA Advanced Settings Page with Cloud Applications field](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Advanced-Settings-Page-RN.png)
![Screenshot of ZIA DLP Advanced Settings Page with Cloud Applications field](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-DLP-Advanced-Settings-Page-RN.png)
[] ![Miscellaneous Apps options for Cloud Application fitler in Web Logs](/sites/default/files/downloads/ZIA-6.2r-misc-option-cloud-apps.png)

## August 25, 2023
### Feature Available
#### Data Transformation Service
Zscaler Data Protection provides the ability to secure collaboration workflows for SaaS applications by delivering the following services:
- Encryption
- Privacy Control (Redaction/Masking)
- Permission Controls (Read Only, Clipboard Control, Print Control)
- Watermarking (Customization with Tilt and Fonts)
- Tokenization of data in structured data sources
These services are integrated as a part of the data protection policy structure and can be configured by DLP admins. End user workflows for encryption and decryption are done using native control and a secure OTP. The SaaS application end users can also selectively encrypt, redact, or watermark any file.

### Feature Available
#### Internet Traffic Capture
You can capture traffic data and store it as a PCAP file in an Amazon S3 bucket for analysis. You can configure capture settings on the newly added Traffic Capture Settings page (Administration > Traffic Capture). As part of this change:
- A new page is added to manage traffic capture settings.
[See image.](#Capture-Settings)
- A new Capture option is added to the following policies when Traffic Capture is enabled and the action is set to block:
- File Type Control
- URL Filtering
- Firewall Filtering
- IPS Control
- DNS Filtering
- Malware Protecction
- Advanced Threat Protection
- A new filter and column option, Capture, is added to the following Insights Logs pages:
- Web Insights Logs (Analytics > Web Insights** **> Logs)
- Firewall Insights Logs (Analytics > Firewall Insights** **> Logs)
- DNS Insights Logs (Analytics > DNS Insights** **> Logs)
- A Download icon is added next to the PCAP file names, in the Capture column, that can be used to download the captured traffic data file.
[See image.](#capture-logs)
To learn more, see [About Traffic Capture](/zia/about-traffic-capture), [Firewall Insights Logs: Filters](/zia/firewall-insights-logs-filters), [Firewall Insights Logs: Columns](/zia/firewall-insights-logs-columns), [Web Insights Logs: Filters](/zia/web-insights-logs-filters), [Web Insights Logs: Columns](/zia/web-insights-logs-columns), [DNS Insights Logs: Filters](/zia/dns-insights-logs-filters), and [DNS Insights Logs: Columns](/zia/dns-insights-logs-columns).
[]![Image of the Traffic Capture Settings page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/traffic-capture-settings.png)
[]![Capture filter and column fields in the Insights Logs Page](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/logs/web-insights-logs-columns/ZIA-6.2r-Capture-Filter-and-Column%20(1).png)

## August 21, 2023
### Feature Available
#### Updates to Cloud Service API
The cloud service API includes the following endpoints to export the Shadow IT Report for the cloud applications recognized by Zscaler based on their usage in your organization:
- `POST /shadowIT/applications/export`
- `POST /shadowIT/applications/{entity}/exportCsv`
These reports include various security parameters of the cloud applications, information about users who have interacted with the applications, the list of locations from where the applications are accessed, and application usage details, as applicable.
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection has also been updated to include new and updated resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

## August 18, 2023
### Feature Available
#### SaaS Security API DLP Policy Support for Google Drive Labels
When creating SaaS Security API DLP policy rules for your Google Drive tenants, you can now apply classification labels defined in Google Drive.
[See image.](#google-drive-labels)
To learn more, see [Configuring the SaaS Security API DLP Policy](/zia/configuring-saas-security-api-dlp-policy).
[]![Screenshot of Apply Classification label for Google Drive files in the Add DLP Rule page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-saas-security-api-apply-google-drive-label-RN.png?1682539592)

### Feature Available
#### WebSocket Protocol Type in Rules and Insights
You can choose either WebSocket or WebSocket SSL as a protocol type when creating an URL Filtering Rule or Bandwidth Control Rule. Logs can also be filtered by WebSocket or WebSocket SSL Protocol Type in Web Insights and Mobile Insights. You can define firewall filtering rules using WebSocket as a network application criterion.
To learn more, see [Configuring the URL Filtering Policy](/zia/configuring-url-filtering-policy), [Adding Rules to the Bandwidth Control Policy](/zia/adding-rules-bandwidth-control-policy), [Web Insights Logs: Filters](/zia/web-insights-logs-filters#Proto), [Mobile Insights Logs: Filters](/zia/mobile-insights-logs-filters#Protocol), and [Configuring the Firewall Filtering Policy](/zia/configuring-firewall-filtering-policy).

## August 11, 2023
### Feature Available
#### Enhancements to Workflow Automation
The following enhancements are available in Workflow Automation:
- Workflow Automation can integrate with Microsoft Teams, a sanctioned SaaS application for Zscaler.
- To enable Microsoft Teams from the ZIA Admin Portal, select Workflow Automation when you onboard Microsoft Teams as a SaaS application tenant.
[See image.](#MS-Teams-Integration)
- When integrated, during the remediation process for a data protection incident in Workflow Automation, admins or the application can initiate different notifications (user, escalation, and digest) to remediate the incident. When Workflow Automation is integrated with the Microsoft Teams application, these different notifications can be delivered through Microsoft messages versus emails to the appropriate users or admins associated with the incident.
- Workflow Automation can integrate with Jira Software, a sanctioned SaaS application for Zscaler.
- To enable Jira Software from the ZIA Admin Portal, select Workflow Automation when you onboard Jira Software as a SaaS application tenant.
[See image.](#Jira-Software-Integration)
- When integrated, admins can create and associate a Jira ticket to an incident during the remediation process for that incident in Workflow Automation. Using the ticket action on the Incident Details page, admins can create a Jira ticket for an incident. After the ticket is created, the admins can view the ticket details and click a link to access the Jira ticket in the Ticket section on the Incident Details page.
- The Audit Logs page is enhanced to capture changes made to incidents and digest template mappings. You can filter the audit logs based on Template Mapping entries.
- The new Notify Owner and Escalate to Manager workflow template notifies the user and only sends an escalation notification to the manager.
- The Workflow Automation API is enhanced with the following endpoint to update DLP incidents:
- POST `/incidents/{dlpIncidentId}/incident-groups/search`. You can use this endpoint to filter a list of DLP incident groups to which the specified DLP incident ID belongs. The endpoint returns parameters such as ID, name, type, and status of the incident groups.
The Postman collection is also updated to include new resources.
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants), [Managing Workflow Automation Integration with Microsoft Teams](/zia/managing-workflow-automation-integration-microsoft-teams), [Managing Workflow Automation Integration with Jira Software](/zia/managing-workflow-automation-integration-jira-software), [About Audit Logs in Workflow Automation](/zia/about-audit-logs-in-workflow-automation), [Understanding Workflows in Workflow Automation](/zia/understanding-workflows-workflow-automation), and [Understanding Workflow Automation API](/zia/understanding-workflow-automation-api).
[] ![Enabling Workflow Automation when adding Microsoft Teams as a SaaS Application Tenant  on the Add SaaS Application Tenant Page in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-Add-SaaS-Application-Tenant-Page-MSTeams-Release-Note-Image.png)
[]![Enabling Workflow Automation when adding Jira Software as a SaaS Application Tenant  on the Add SaaS Application Tenant Page in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-WA-Add-SaaS-Application-Tenant-Page-Jira-Release-Note.png)

### Feature Available
#### Support for Custom Signature Rules and Threat Categories
The IPS Control policy includes the following enhancements to the ZIA Admin Portal:
Custom Signature Rules
You can create custom signature rules to protect your organization’s network traffic from intrusion. You can build custom signature rules using Snort syntax and deploy them on Zscaler’s IPS via IPS Control rules. The Zscaler service will compare your organization’s traffic with custom signature rules to enforce policies inline when there is a pattern match. You must have ZIA Private Service Edges installed in your organization’s data center to deploy custom signature rules on the Zscaler service.
You can create custom signature rules under Administration > Custom IPS > Custom Signature Rules.
[See image.](#custom-signature-rules-tab)
To learn more, see [About Custom Signature Rules](/zia/about-custom-signature-rules), [Adding Custom Signature Rules](/zia/adding-custom-signature-rules), [Importing and Exporting Custom Signature Rules](/zia/importing-exporting-custom-signature-rules), and [Specifications and Limitations for Custom Signature Rules](/zia/specifications-limitations-custom-signature-rules).
Custom Threat Categories
You can define custom threat categories and associate custom signature rules with them. You can use these threat categories when defining IPS Control rules.
You can create custom threat categories under Administration > Custom IPS > Threat Categories.
[See image.](#threat-categories-tab)
To learn more, see [About Threat Categories](/zia/about-threat-categories) and [Adding Threat Categories](/zia/adding-threat-categories).
Firewall Insights logs
A new filter, Show Only Custom Signature Rules, and a new column, IPS Custom Signature, are added to the Firewall Insights Logs.
[See image.](#firewall-logs)
To learn more, see [Firewall Insights Logs: Filters](/zia/firewall-insights-logs-filters) and [Firewall Insights Logs: Columns](/zia/firewall-insights-logs-columns).
**Audit Logs**
Two new sub-categories, Custom Signature Rule and Custom Threat Category, are added to the Administration > Audit Logs Page.
[See image.](#audit-logs)
To learn more, see [About Audit Logs](/zia/about-audit-logs).
**NSS Feeds**
The field `%d{ips_custom_signature}` is available when adding an NSS feed output for firewall logs.
To learn more, see [NSS Feed Output Format: Firewall Logs](/zia/nss-feed-output-format-firewall-logs).
[] ![Show Only Custom Signature Rules filter & IPS Custom Signature column in Firewall Insights Logs](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/zia-6.2-custom-signature-firewall-logs%20(2).png)
[![Screenshot of Custom IPS Category and Custom IPS Rules in the Audit Logs page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/zia-custom-threat-signature-rule-audit-logs-page.png)
]
[]![Custom Signature Rules](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/custom-signature-rules.png)
[]![Threat Categories](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/threat-categories.png)

## August 04, 2023
### Feature Available
#### AI Instant Verdict for Unknown Files in Sandbox Policy
You can enable AI Instant Verdict as part of your Sandbox policy to analyze an unknown file in real time to determine the likelihood of it being benign or suspicious, based on the threat score it is assigned by Zscaler artificial intelligence (AI). If AI analysis assigns a threat score higher than 90, the Zscaler service identifies the file as high-confidence malicious and blocks download. If AI analysis assigns a threat score between 70-90 and the sandbox policy First-Time Action is Allow and scan, the file is sent to quarantine for further analysis. After analysis, the service allows or blocks the file download based on your configured Action for Subsequent Downloads.
[See image.](#ai-instant-verdict-toggle)
To learn more, see [Configuring the Sandbox Policy](/zia/configuring-sandbox-policy).
[]![Screenshot of AI Instant Verdict toggle in the Add Sandbox Rule page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Sandbox-Rule-AI-Instant-Verdict-Toggle.png)

### Feature Available
#### Delete SaaS Application Tenants
You can now delete SaaS application tenants you have created directly from the About SaaS Application Tenants page table.
[See image.](#delete_saas)
To learn more, see [About SaaS Application Tenants](/zia/about-saas-application-tenants).
[]![New About SaaS Application functionality](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/about-shadow-it-report/SaaS%20Application%20Tenants%20Page%20delete.png)

### Feature Available
#### Enhancement to Cloud Applications Page
The service redirects you to the Application Information** **page (Analytics > SaaS Security Report > Applications > Application you clicked on the Cloud Applications page) when you click a predefined cloud application name link on the Cloud Applications page (Administration > Cloud Applications).
[See image.](#cloud-apps-with-name-link)
As part of this change, undiscovered cloud applications are displayed on the Shadow IT Reports page (Analytics > SaaS Security Report > Applications). You can also view the security attributes of undiscovered cloud applications on the Application Information page (Analytics > SaaS Security Report > Applications > any undiscovered application on the Shadow IT Report page).
To learn more, see [About Cloud Applications](/zia/about-cloud-applications), [About Shadow IT Report](/zia/about-shadow-it-report), and [About Application Information](/zia/about-application-information).
[]![Screenshot of ZIA Cloud Applications Page With Cloud Applications Name Links](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Cloud-Applications-Applications-with-Name-Link-RN.png)
![Screenshot of ZIA Application Information Page for Salesforce](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Application-Information-Page-SalesForce-RN.png)

### Feature Available
#### Enhancement to Third-Party Proxy Chaining
The Zscaler service allows the upstream proxies to consume authenticated user's login name information (i.e., user ID) from the X-Authenticated-User header value passed from a downstream proxy, avoiding re-authentication of users. You can create user ID-based policies with this change.
As part of this change, the following fields are added to the Add Proxy window (Administration > Proxies & Gateways > Add Proxy):
- Insert X-Authenticated-User
- Base64 encode XAU
[See image.](#add-proxies-xau)
To learn more, see [Configuring Third-Party Proxy](/zia/configuring-third-party-proxies).
[]![Screenshot of ZIA Add Proxy with Insert X-Authenticated-User Option](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Add-Proxy-Page-RN.png)

### Feature Available
#### Enhancements to Sandbox Report
The Sandbox BAUI Report includes a new Malware Configuration Extraction tile to view the details of the malware that was extracted.
[See image.](#MalwareExtraction_tile)
To learn more, see [Viewing Sandbox Reports and Data](/zia/viewing-sandbox-reports-data).
[]![Malware Configuration Extraction tile in Sandbox BAUI Report](/sites/default/files/downloads/zia/about-nothing/MalwareConfigurationExtraction_2.png)

### Feature Available
#### Firewall Filtering Rules Based on Source Countries
You can configure firewall filtering rules to allow or block traffic based on the country of origin of the traffic by using the new Countries field on the Source IP tab of the firewall filtering rule. The source country of the traffic is determined using the geolocation of the client's IP address.
[See image.](#source-country-criteria-firewall-filtering-rule)
To learn more, see [Configuring the Firewall Filtering Policy](/zia/configuring-firewall-filtering-policy).
Firewall Insights Logs
The Firewall Insights Logs is enhanced with the following changes:
- The existing Country filter and Server Country column are renamed to Dest Country.
- A new filter and column, Source Country, is added to the firewall logs.
[See image.](#firewall-logs)
To learn more, see [Firewall Insights Logs: Filters](/zia/firewall-insights-logs-filters) and [Firewall Insights Logs: Columns](/zia/firewall-insights-logs-columns).
NSS Feeds
The field `%s{srcip_country}` is now available when adding an NSS feed for Firewall logs:
To learn more, see [NSS Feed Output Format: Firewall Logs](/zia/nss-feed-output-format-firewall-logs).
Updates to Cloud Service API
The `/firewallFilteringRules` endpoints within the cloud service API are also updated to include the following new fields to support policies based on source countries:
- `sourceCountries`
- `excludeSrcCountries`
To learn more, see the [API Reference](/zia/about-api).
[]![A screenshot of the Source Countries criteria in firewall filtering rules](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/firewall-filtering-source-ip-tab.png)
[] ![Destination and Source Country fields In Firewall Insights Logs](/sites/default/files/downloads/ZIA-6.2r-dest-source-country.png)

### Feature Available
#### IoT Discovery Report enhancements
The following enhancements are now available for IoT Discovery Report:
- IoT Device Classification shows all classifications, not just the top ones. If you have more than 12 classifications, you see carousel buttons that allow you to scroll and see the other classifications you have.
- In Device Type Distribution, View All was added to show you all devices in the Discovered Devices page.
[See Image.](#IoT_Discovery)
The following enhancements are now available for Discovered Devices:
- The total bandwidth consumption chart has larger, color-coded data points to improve readability.
- The traffic flows diagram has been updated to show 50 flows.
[See image.](#discovered_devices)
To learn more, see [About IoT Discovery Report](/zia/about-iot-discovery-report) and [About Discovered Devices](/zia/about-discovered-devices).
[![New bandwidth consumption and traffic flow diagrams.](/sites/default/files/downloads/zia/about-nothing/ZIA-6.3-IoT-discovery-report-slide-pane.png)
]
[]![New IoT Discovery Report page](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/about-shadow-it-report/IoT%20Discovery%20Report%20basicish.png)

### Feature Available
#### Persisting Isolation Banner
Isolation banners are displayed for a period of 15 seconds before they disappear. Administrators can enable the banners per ZIA isolation profile to persist throughout the duration of the isolation session without disappearing.
[See image.](#persist-banner)
To learn more, see [Adding a Banner Theme for the Isolation End User Notification in ZIA](/isolation/adding-banner-theme-isolation-end-user-notification-zia) and [Creating Isolation Profiles for ZIA](/isolation/creating-zia-isolation-profile-isolation).
[![Enable or disable the options available.](/sites/default/files/downloads/isolation/profiles/zia-profiles/editing-your-isolation-profile-zia/persist-banner.png)
]

### Feature Available
#### Persisting Isolation URL Bar
Admins can enable the option per ZIA isolation profile for the user to see a persistent isolation URL bar during their isolation session.
[See image.](#persist-bar)
To learn more, see [Creating Isolation Profiles for ZIA](/isolation/creating-zia-isolation-profile-isolation) and [Editing Your Isolation Profile for ZIA](/isolation/editing-your-isolation-profile-zia).
[![Enable or disable the option.](/sites/default/files/downloads/isolation/profiles/zia-profiles/editing-your-isolation-profile-zia/ZIA_Add-Isolation-Profile_Iso-UX_Persist-Isolation-URL-Bar_squircle.png)
]

### Feature Available
#### Source IP Groups Criterion in SSL Inspection Policy
The Source IP Groups criterion is added to the Add SSL Inspection Rule window. You can select any number of source IP groups for a rule.
[See image.](#Add-SSL-Inspection-Rule-Window)
To learn more, see [Configuring SSL Inspection Policy](/zia/configuring-ssl-inspection-policy).
[]![Screenshot of Add SSL Inspection Rule Window](/sites/default/files/downloads/zia/documentation-knowledgebase/policies/ssl-inspection/configuring-ssl-inspection-policy/sourcegroupsRN.png)

### Feature Available
#### Support for DNS Gateway
DNS Gateway enables support for DNS high availability and translation of protocols when performing DNS lookup using external DNS services. You can ensure the high availability of your DNS service by configuring primary and secondary DNS servers. You can configure specific protocols (DoH, UDP, or TCP) that must be used to send your users' DNS traffic to the external DNS service via the Zscaler service. If the incoming DNS request uses a protocol that is different from the configured server-side protocol, then the Zscaler service performs the necessary translation and sends the DNS request to the external DNS service.
The following sections provide information on the user interface changes introduced in the ZIA Admin Portal for the DNS Gateway feature and the changes automatically implemented in your policy configurations for backward compatibility:
- [What's New](#whats-new)
- [Deprecated Rule Actions](#deprecated-policy-actions)
- [Backward Compatibility](#backward-compatibility)
[]The DNS Gateway feature introduces new actions and modifications within DNS Control policy rules and NAT Control rules. To ensure that these changes are 100% backward compatible with your existing policy configurations prior to this upgrade, Zscaler adds automatically generated-DNS Gateway objects and implements policy modifications to preserve the intended behavior of your existing configurations.
You can view the auto-generated DNS Gateways but cannot modify them.
Migration Scenarios and Rule Changes
This section covers the list of scenarios in which your policies that existed before the upgrade may be modified by Zscaler to ensure backward compatibility.
- [DNS Control Rules](#dns-rules)
- [NAT Control Rules: Zscaler Trusted DNS Resolver](#zscaler-trusted-resolver-nat-rule)
[]This upgrade affects only the DNS Control policy rules that are configured with the Redirect Request action, including the policies currently configured in the ZIA Admin Portal and the backup. DNS Control rules configured with other actions are not impacted.
The migration scenarios and the corresponding rule changes are as follows:
**Migration Scenario 1: Includes DoH and Non-DoH (TCP/UDP) Protocol Criteria**
Each DNS Control rule that is configured with DoH and non-DoH (TCP/UDP) protocol criteria and the Redirect Request action is split into two new rules:
| Rule | Protocol Criteria | Action |
| ---- | ----------------- | ------ |
| Original Rule | DoH and non-DoH (TCP/UDP), or ANY protocol | Redirect Request |
| New Rule 1 | DoH | Redirect Request Using UDP |
| New Rule 2 | TCP and/or UDP, as in the original rule | Redirect Request & Keep Sender Protocol |
New Rule 1 retains the name and the rule order of the original rule, whereas New Rule 2 gets an auto-generated name and the next rule order in the sequence. As a result, the rules consecutive to your original rule have their rule order increased by one level.
A new DNS Gateway object is created with an auto-generated name for each new rule and is associated with the respective rule:
| DNS Gateway For Rules | Primary Resolver | Protocol | TCP Port | UDP Port | DoH Port | Failure Behavior |
| --------------------- | ---------------- | -------- | -------- | -------- | -------- | ---------------- |
| New Rule 1 | DNS Server IP in the original rule | TCP, UDP | 53 | 53 | - | Return Error Response |
| New Rule 2 | DNS Server IP in the original rule | TCP, UDP | - | - | - | Return Error Response |
[See image.](#DNS-rule-migration-scenario-1)
**Migration Scenario 2: Includes Only Non-DoH (TCP/UDP) Protocol Criteria**
Each DNS Control rule that is configured with only non-DoH (TCP/UDP) protocol criteria and the Redirect Request action is modified as follows:
| Rule | Protocol Criteria | Action |
| ---- | ----------------- | ------ |
| Original Rule | TCP and/or UDP | Redirect Request |
| New Rule | TCP and/or UDP, as in the original rule | Redirect Request & Keep Sender Protocol |
A new DNS Gateway object is created with an auto-generated name and is associated with the new rule:
| Primary Resolver | Protocol | TCP Port | UDP Port | DoH Port | Failure Behavior |
| ---------------- | -------- | -------- | -------- | -------- | ---------------- |
| DNS Server IP in the original rule | TCP, UDP | - | - | - | Return Error Response |
[See image.](#DNS-rule-migration-scenario-2)
**Migration Scenario 3: Includes Only DoH Protocol Criteria**
Each DNS Control rule that is configured with only DoH protocol criteria and the Redirect Request action is modified as follows:
| Rule | Protocol Criteria | Action |
| ---- | ----------------- | ------ |
| Original Rule | DoH | Redirect Request |
| New Rule | DoH | Redirect Request Using UDP |
A new DNS Gateway object is created with an auto-generated name and is associated with the new rule:
| Primary Resolver | Protocol | TCP Port | UDP Port | DoH Port | Failure Behavior |
| ---------------- | -------- | -------- | -------- | -------- | ---------------- |
| DNS Server IP in the original rule | TCP, UDP | 53 | 53 | - | Return Error Response |
[See image.](#DNS-rule-migration-scenario-3)
In case of server failure with migrated DNS rules, the failover behavior configured for the associated DNS Gateway (auto-generated during migration) is not triggered, and the DNS server's health is not monitored by Zscaler. Instead, the Zscaler service continues to forward the DNS queries to the DNS server in order to maintain backward compatibility.
[]With this upgrade, a new DNS Gateway object is created with the name, Zscaler Trusted DNS Resolver, and is associated with the predefined Zscaler Trusted DNS Resolver NAT rule that directs your standard DNS traffic to the Zscaler Trusted DNS resolver.
| Primary Resolver | Protocol | TCP Port | UDP Port | DoH Port | Failure Behavior |
| ---------------- | -------- | -------- | -------- | -------- | ---------------- |
| zstrustedresolver.<Zscaler Cloud Name> | TCP, UDP | 53 | 53 | - | Return Error Response |
[See image.](#Zscaler-trusted-dns-resolver-nat-rule-migration)
This is only a user interface change, and there are no functionality changes to the rule. Other NAT Control rules are not impacted by this upgrade.
[]In DNS Control policy rules, the Redirect Request action has been deprecated in favor of the new protocol-based actions.
[]DNS Gateways
You can configure DNS Gateways under Administration > Proxies & Gateways > DNS Gateways. After configuring DNS Gateways, you can use them in DNS Control policy rules and NAT Control rules to enable DNS high availability and protocol translation when using external DNS services.
[See image.](#DNS-gateways-page)
To learn more, see [About DNS Gateways](/zia/about-dns-gateways).
DNS Control Policy
The DNS Control policy rules include the following new actions to specify the protocol that must be used to send users’ DNS queries to the external DNS service via a secured DNS Gateway:
- Redirect Request Using DoH
- Redirect Request Using TCP
- Redirect Request Using UDP
- Redirect Request & Keep Sender Protocol
When these actions are selected, a new DNS Gateway field is shown for specifying the DNS Gateway that must be used to route the DNS requests.
[See image.](#DNS-rule-new-redirect-request-actions)
The Protocol criterion within the rule is validated based on the action selected. For example, when Redirect Request Using TCP is selected, only DNS Over HTTPS** **and TCP are shown under the Protocol criteria, whereas DNS Over HTTPS and UDP are shown when Redirect Request Using UDP is selected.
To learn more, see [Configuring the DNS Control Policy](/zia/configuring-dns-control-policy).
NAT Control Policy
The NAT Control rules include the following new actions to redirect DNS requests to the external DNS service via a secured DNS Gateway:
- Redirect Request Using DoH
- Redirect DNS & Keep Sender Protocol
When these actions are selected, a new DNS Gateway field is shown for specifying the DNS Gateway that must be used to route the DNS requests.
These options are shown only when the Network Services and/or Network Service Groups criteria are exclusively configured to match DNS, without being combined with other network services.
[See image.](#NAT-rule-new-redirect-request-actions)
To learn more, see [Configuring the NAT Control Policy](/zia/configuring-nat-control-policy).
DNS Insights Logs
The following fields are added to the DNS Insights Logs:
- DNS Gateway Flags
- Resolver Gateway
- HTTP Status Code
- Server Protocol
To learn more, see [DNS Insights Logs: Filters](/zia/dns-insights-logs-filters) and [DNS Insights Logs: Columns](/zia/dns-insights-logs-columns).
NSS Feeds
The following fields are available when adding an NSS feed for DNS logs:
- `%s{dnsgw_slot}`
- `%s{dnsgw_srv_proto}`
- `%s{dnsgw_flags}`
- `%s{http_code}`
To learn more, see [NSS Feed Output Format: DNS Logs](/zia/nss-feed-output-format-dns-logs).
[]![A screenshot of the new DNS Gateways page ](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/dns-gateway-tab.png)
[]![A screenshot of the new Redirect Request actions in DNS Control rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/dns-rule-redirect-request-actions.png)
[]![A screenshot of the new Redirect Request actions in NAT Control rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/nat-rule-redirect-reponse-actions.png)
[]![Screenshots of a DNS rule pre- and post-migration (scenario 1)](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/DNS-rule-migration-scenario-1.png)
[]![Screenshots of a DNS rule pre- and post-migration (scenario 3)](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/DNS-rule-migration-scenario-3.png)
[]![Screenshots of a DNS rule pre- and post-migration (scenario 2)](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/DNS-rule-migration-scenario-2.png)
[]![Screenshots of a Zscaler Trusted DNS Resolver NAT rule pre- and post-migration](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/trusted-dns-resolver-nat-rule-migration.png?1683531822)

### Feature Available
#### Support for Enabling Client Connector Notifications in Web DLP Rules
You can enable or disable Client Connector notifications for web DLP rules when violations occur. This setting can be found on the Add DLP Rule page for rules with or without content inspection.
[See image.](#ZIA-Enable-Client-Connector-Notification)
To learn more, see [Configuring End User Notifications](/zia/configuring-end-user-notifications).
[]![Configuring Client Connector Notification on the Add DLP Rule page in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA_Add_DLP_Rule_Enable_Client_Connector_Notification.png)

### Feature Available
#### Support for Running the DLP Index Tool Service without Elevated Privileges
You can now configure the Data Loss Prevention (DLP) Index Tool service to run without elevated privileges.
To learn more, see [Configuring the Index Tool with VMware](/zia/configuring-index-tool-vmware) and [Configuring the Index Tool with Amazon Web Services](/zia/configuring-index-tool-amazon-web-services).

### Feature Available
#### Updates to Ranges & Limitations
The following ranges and limitations changes were made to the Admin Portal:
For Policies > SSL inspection policy rules: You can add up to 255 SSL inspection policy rules.
To learn more, see [Ranges & Limitations](/zia/ranges-limitations).

### Feature Available
#### Watermark for Isolation User Experience
The watermarking capability for isolation allows admins to create a watermark to display whenever the user enters a web page in isolation. Admins can enable watermarking per isolation profile and choose to display the user ID, date and timestamp, and a custom message.
[See image.](#watermarking)
To learn more, see [Creating Isolation Profiles for ZIA](/isolation/creating-zia-isolation-profile-isolation) and [Transferring and Viewing Files in Isolation](/isolation/transferring-and-viewing-files-cloud-browser-isolation).
[![Go to Isolation Experience and enable the desired toggles for Watermarking.](/sites/default/files/downloads/isolation/profiles/zia-profiles/creating-zia-isolation-profile-isolation/ZIA_Add-Isolation-Profile_Iso-UX_Watermarking.png)
]

## July 24, 2023
### Feature Available
#### Slack and ServiceNow Integration with Workflow Automation
The following enhancements to Slack and ServiceNow are available in Workflow Automation:
- Workflow Automation can integrate with Slack, a sanctioned SaaS application for Zscaler. During the remediation process for a data protection incident in Workflow Automation, admins or the application can initiate different notifications (user, escalation, and digest) to remediate the incident. When Workflow Automation is integrated with the Slack application, these different notifications can be delivered through Slack messages versus emails to the appropriate users or admins associated with the incident.
- Workflow Automation can integrate with ServiceNow, a sanctioned SaaS application for Zscaler. When Workflow Automation is integrated with the ServiceNow application, admins can create and associate a ServiceNow ticket to an incident during the remediation process for that incident in Workflow Automation. A new ticket action is available on the Incident Details page to enable admins to create a ServiceNow ticket for an incident. After the ticket is created, the admins can view the ticket details and click a link to access ServiceNow for that ticket in the new Ticket section on the Incident Details page.
- The Auto Create Tickets workflow template is available. This template enables tickets to be automatically created in an integration ticketing application (e.g., ServiceNow) and assigned to the appropriate user in that application.
[See image.](#addingsaas)
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants), [Managing Workflow Automation Integration with Slack](/zia/managing-workflow-automation-integration-slack), and [Managing Workflow Automation with ServiceNow](/zia/managing-workflow-automation-integration-servicenow).
[]![SaaS Application Tenants ZWA](/sites/default/files/downloads/zia/adding-saas-application-tenants/Onboard%20SaaS%20Application_nonum_jira_0.png)

## July 21, 2023
### Feature Available
#### Custom Authentication Timeout Profiles
To access this feature, contact your Zscaler Account Team.
You can create custom authentication timeout profiles and assign them to locations within your organization. These profiles allow for a higher degree of control over the authentication timeout than the previous global timeout. As part of this change:
- A new tab, Authentication Profiles, is added to the Authentication Settings page (Administration > Authentication Settings > Authentication Profiles).
[See image.](#Auth-Profiles-Page)
- A new field, Authentication Profile, is added to the Edit Location window on the Location Management page (Administration > Location Management).
[See image.](#Auth-Profile-Field)
To learn more, see [Configuring Custom Authentication Timeout Profiles](/zia/configuring-custom-authentication-timeout-profiles).
[]![Image of the Authentication Profile page](/sites/default/files/downloads/zia/authentication-administration/user-management-authentication-settings/configuring-custom-authentication-timeout-profiles/Auth%20Profile%20Page.png)
[]![Image of the Authentication Profile field on the Edit Location page](/sites/default/files/downloads/zia/authentication-administration/user-management-authentication-settings/configuring-custom-authentication-timeout-profiles/Auth%20Profile%20Field.png)

### Feature Available
#### Renamed Cyber Risk Report
The Cyber Risk Report is renamed to Configuration Risk Report.
[See image.](#config-risk-report)
To learn more, see [About Configuration Risk Report](/zia/about-configuration-risk-report).
[]![Configuration Risk Report ](/sites/default/files/downloads/zia/dashboard-analytics/reports/configuration-risk-report/ZIA-6.2r-Config-risk-report%20(1).png)

### Feature Available
#### Support for IPv6
You can forward your organization's IPv6 traffic from a location to the Zscaler service and extend existing security policies to IPv6 traffic. Zscaler requires the packets arriving at the ZIA Service Edges to be IPv4 packets. Therefore, you need to forward IPv6 traffic in one of the following ways, depending on where your client is placed:
- **Clients inside known locations**: Use GRE or IPSec tunneling mechanism to forward IPv6 traffic inside IPv4 tunnels from clients inside locations.
- **Remote clients**: Use a self-hosted or ISP-provided NAT64 gateway (with Zscaler Client Connector or PAC files) to forward IPv6 traffic from remote users.
Zscaler supports customized DNS64/NAT64 mechanisms to enable your IPv6-only clients to communicate with IPv4 services. To perform DNS64/NAT64, Zscaler selects NAT64 and DNS64 prefixes from a set of supported prefixes that includes the well-known prefix (64:ff9b::/96), Zscaler's default prefix, and your network-specific prefixes configured in the ZIA Admin Portal or discovered by Zscaler Client Connector.
You can enable IPv6 support at the organization level and configure related settings on the Administration > IPv6 Configuration page. After IPv6 support is enabled at the organization level, it can be enabled on a per location basis.
[See image.](#configure-ipv6)
To learn more, see [Understanding IPv6 Support](/zia/understanding-ipv6-support), [About NAT64 Prefixes](/zia/about-nat64-prefixes), [About the DNS64 Prefix](/zia/about-dns64-prefix), and [Configuring IPv6 Settings](/zia/configuring-ipv6-settings).
The Zscaler service brings in the following enhancements to include IPv6 support:
Locations
Zscaler introduces the following options under the Administration > Location Management > Add/Edit Location window to enable IPv6 support on both existing and new locations:
- Enable IPv6
- DNS64 Prefix
[See image.](#add-location-ipv6)
To learn more, see [Configuring Locations](/zia/configuring-locations).
URL Categories
You can add IPv6 addresses to predefined and custom URL categories using the following options under the Administration > URL Categories > Add/Edit URL Category window:
- Custom URLs
- URLs Retaining Parent Category
[See image.](#url-categories-IPv6)
To learn more, see [Configuring Custom URL Categories](/zia/adding-custom-url-categories).
Virtual Service Edge and Private Service Edge
You can forward IPv6 traffic to Virtual Service Edges and Private Service Edges via IPSec or GRE tunnels as described in the preceding section, Support for IPv6.
To learn more, see [Forwarding Traffic to Virtual Service Edges](/zia/forwarding-traffic-virtual-service-edges) and [Deploying Private Service Edge](/zia/deploying-private-service-edge).
IP & FQDN Groups
Zscaler introduces two predefined IP groups, All IPv4 and All IPv6 for grouping all IPv4 addresses and IPv6 addresses, respectively. As part of this enhancement, separate configuration options for source and destination groups based on the address type (IPv4 or IPv6) have been added to the Administration > IP & FQDN Groups page.
[See image.](#configure-group-ipv4-ipv6)
This distinction among groups based on the address type is also reflected in firewall policy criteria.
[See image.](#source-destination-ip-groups)
Custom groups are currently not** **supported for IPv6 addresses.
To learn more, see [About Source IP Groups](/zia/about-source-ip-groups), [About Destination IP Groups](/zia/about-destination-ip-groups), [Configuring the Firewall Filtering Policy](/zia/configuring-firewall-filtering-policy), [Configuring the NAT Control Policy](/zia/configuring-nat-control-policy), [Configuring the DNS Control Policy](/zia/configuring-dns-control-policy), [Configuring IPS Control Policy](/zia/configuring-ips-control-policy), and [Configuring Forwarding Policy](/zia/configuring-forwarding-policy).
Firewall Filtering Rule
Zscaler introduces a predefined firewall filtering rule (Block All IPv6) under Policy > Firewall Control > Firewall Filtering Rule that blocks all IPv6 traffic from your organization to any destination. When IPv6 support is enabled at the organization level, this rule is automatically created and enabled by default. You need to modify this rule to allow IPv6 traffic.
[See image.](#block-all-ipv6-firewall-filtering-rule)
To learn more, see [About Predefined Firewall Filtering Rules](/zia/about-predefined-firewall-filtering-rules).
Insights Logs
The Client IPv6 option is removed from the Web Insights Logs filters and columns.
You can view logs for traffic related to IPv6 addresses in addition to IPv4 traffic logs, using the following filters and columns under the respective Insights Logs page:
- Web Insights Logs:
- Client External IP
- Client IP
- Server IP
- Firewall Insights Logs:
- Client Destination IP
- Client Source IP
- Server Destination IP
- Server Source IP
- DNS Insights Logs:
- Client IP
- Server IP
- DNS Response (Filter) and Resolved IP or Name (Column)
[See image.](#ipv6-insights-logs)
To learn more, see [Web Insights Logs: Filters](/zia/web-insights-logs-filters), [Firewall Insights Logs: Filters](/zia/firewall-insights-logs-filters), and [DNS Insights Logs: Filters](/zia/dns-insights-logs-filters).
**NSS Feeds**
The field `%s{cltipv6}` is deprecated and removed from the NSS feed for web logs.
The following fields under the respective logs support IPv6 addresses in addition to IPv4 addresses on the NSS feed:
- Web logs:
- `%s{cip}`
- `%s{cintip}`
- `%s{sip}`
- Firewall logs:
- `%s{csip}`
- `%s{cdip}`
- `%s{sdip}`
- `%s{ssip}`
- DNS logs:
- `%s{cip}`
- `%s{sip}`
- `%s{res}`
- `%s{restype}`
To learn more, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs), [NSS Feed Output Format: Firewall Logs](/zia/nss-feed-output-format-firewall-logs), and [NSS Feed Output Format: DNS Logs](/zia/nss-feed-output-format-dns-logs).
Updates to Cloud Service API
The cloud service API now includes the following endpoints to retrieve IPv6 enablement status, NAT64 and DNS64 prefixes, and source and destination IPv6 address groups:
- `GET /ipv6config`
- `GET /ipv6config/dns64prefix`
- `GET /ipv6config/nat64prefix`
- `GET /ipSourceGroups/ipv6SourceGroups`
- `GET /ipSourceGroups/ipv6SourceGroups/lite`
- `GET /ipDestinationGroups/ipv6DestinationGroups`
- `GET /ipDestinationGroups/ipv6DestinationGroups/lite`
The Location Management resources have been updated to support new parameters, namely `ipv6Enabled`, `ipv6Dns64Prefix`, `other6SubLocation`, and `otherSubLocation`. These parameters allow you to configure IPv6 settings and retrieve default sub-locations created for a location. The following endpoints support these parameters:
- `GET /locations`
- `POST /locations`
- `GET /locations/lite`
- `GET /locations/{locationId}`
- `PUT /locations/{locationId}`
The Firewall Policies resources have been updated to support new parameters, namely `srcIpv6Groups` and `destIpv6Groups`, which specify source IPv6 group and destination IPv6 group criteria respectively. The following endpoints support these parameters:
- `GET /firewallFilteringRules`
- `POST /firewallFilteringRules`
- `GET /firewallFilteringRules/{ruleId}`
- `PUT /firewallFilteringRules/{ruleId} `
The Postman collection has also been updated to include new and updated resources.
To learn more, see the [API Reference](/zia/about-api), [API Rate Limit Summary](/zia/api-rate-limit-summary), and [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).
[]![IPv6 Support in Firewall and Web Insights Logs](/sites/default/files/downloads/ZIA-6.2-IPv6-Insights-Logs.png)
[]![Screenshot of Add Location window with IPv6 enabled](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Add-Location-Gateway-Options-IPv6.png)
[]![Screenshot of URL Categories page with support for IPv6.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Add-URL-Categories.png)
[![IPv6 Configuration](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ipv6-nat-dns-prefix.png)
]
[![IP Group Configuration](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ipv4-ipv6-groups.png)
]
[]![A screenshot of the Block All IPv6 firewall filtering rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/block-all-ipv6.png)
[]![A screenshot of the source and destination IP groups in firewall policy criteria](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/source-destination-groups.png?1669362637)

## July 14, 2023
### Feature Available
#### Customization for Quarantine Notification
You can customize the quarantine notification that appears for the Sandbox policy configured to quarantine unknown files. This customization is available on the End User Notifications page (Administration > End User Notifications).
[See image.](#quarantine-end-user-notification-customization)
To learn more, see [Configuring the Quarantine Notification](/zia/configuring-quarantine-notification).
[]![A screenshot of the quarantine end user notification customization window](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/quarantine-notification.png?1685428143)

### Feature Available
#### DLP Support for New PII Dictionaries
The following are new predefined DLP dictionaries:
- VAT Number (Austria)
- VAT Number (Belgium)
- VAT Number (France)
- VAT Number (Germany)
- VAT Number (Luxembourg)
- VAT Number (Netherlands)
To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).

### Feature Available
#### Enhancement to SaaS Assets Summary Report
The SaaS Assets Summary Report now shows the data for Data Loss Prevention (DLP) and malware *incidents*. An incident is the violation of a DLP or malware policy.
[See image.](#saas-summary-report)
To learn more, see [SaaS Assets Summary Report](/zia/saas-assets-summary-report).
New Event Type in NSS Feeds for SaaS Security Logs
You can now select **Violation** as the event type when configuring an NSS feed for SaaS Security Logs. The new option filters logs to events in which data loss or malware was detected.
[See image.](#zia-nss-saas-security-event-violation)
To learn more, see [Adding NSS Feeds for SaaS Security Logs](/zia/adding-nss-feeds-saas-security-logs) and [Adding Cloud NSS Feeds for SaaS Security Logs](/zia/adding-cloud-nss-feeds-saas-security-logs).
[]![SaaS Assets Summary Report](/sites/default/files/downloads/ZIA-6.2r-SaaS-Assets-Summary-Report.png)
[![Screenshot of the Violation option in the Event filter, which can be configured in NSS feeds for SaaS Security logs in the ZIA Admin Portal.](/sites/default/files/downloads/zia_nss_saas_security_event_violation.png)
]

### Feature Available
#### Enhancements to Cloud Application Instances
The cloud application instances feature is extended to the GDrive and Gmail applications.
[See image.](#cloud-app-instance-gdrive-gmail)
To learn more, see [About Cloud Application Instances](/zia/about-cloud-application-instances).
[]![Screenshot of ZIA Add Cloud Application Instance Window with GDrive](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/Add%20Cloud%20Application%20Instance%20with%20GDrive-RN.png)
![Screenshot of ZIA Add Cloud Application Instance Window with Gmail](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/Add%20Cloud%20Application%20Instance%20with%20Gmail-RN.png)

### Feature Available
#### Enhancements to Workflow Automation
The following enhancements are available in Workflow Automation:
- Two additional privacy flags (hide policy details for - remediation owners and hide policy details for - managers/approvers) are available. These flags enable you to control whether the policy details for an incident can be seen by the users in user notifications and if the policy details can be seen by approvers or managers in escalation notifications.
- The Audit Logs page is enhanced with new Modules and Resource filters. You can filter the audit logs based on these entries: API Keys, DLP, Customers, Incident Groups, Integrations, and Workflow.

### Feature Available
#### File Attachment Support for File Share Activity
The File Share Activity filter in the Web Insights Logs is enhanced with the following updates:
- Two new activities, With File Uploads Only and Without File Uploads, are added.
- The existing Upload and View activities are removed.
[See image.](#file-share-activity)
To learn more, see [Web Insights Logs: Filters](/zia/web-insights-logs-filters) and [Web Data Types and Filters](/zia/web-data-types-and-filters).
[]![Web Insights Logs: Filters screenshots](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/web-insights-logs-filter-drafts/File%20Share%20Activity.jpg)

### Feature Available
#### New Action Support for Selected Applications in the File Sharing Rule for Cloud App Control
You can Allow** **or Block certain granular actions for applications such as Box, Dropbox, OneDrive, OneDrive Business, and Google Drive while creating a File Sharing rule for Cloud App Control Policy. The actions include Downloading, Sharing, Editing, Inviting, Renaming, Creating, Deleting, and Form Sharing.
[See image.](#image)
To learn more, see [Adding a File Sharing Rule for Cloud App Control](/zia/adding-file-sharing-rule-cloud-app-control).
[]![Add file sharing rule screenshot](/sites/default/files/downloads/zia/policies/cloud-apps/tenant-restriction/adding-tenant-profiles/Add%20File%20Sharing%20Rule.jpg)

### Feature Available
#### SaaS Application Tenants
You can now use a single CloudTrail account to onboard multiple AWS tenants.
To learn more, see [About SaaS Application Tenants](/zia/about-saas-application-tenants) and [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).

### Feature Available
#### SaaS Security API
You can now configure tenants for GitLab, a source code repository application.
[See image.](#addingsaas)
To learn more, see [About SaaS Application Tenants](/zia/about-saas-application-tenants) and [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
You can configure the application for the SaaS Security API Control policies and also view them on the following pages:
- [Saas Assets Report](/zia/saas-assets-report)
- [SaaS Assets Summary Report](/zia/saas-assets-summary-report)
- [SaaS Security Insights](/zia/saas-security-insights) and [Insights Logs](/zia/saas-security-insights-logs)
- [NSS Feeds](/zia/adding-nss-feeds-saas-security-logs) and [Cloud NSS Feeds for SaaS Security Logs](/zia/adding-cloud-nss-feeds-saas-security-logs)
To learn more, see [Configuring the SaaS Security API Control Policy](/zia/configuring-saas-security-api-control-policy).
[]![SaaS Application Tenants.](/sites/default/files/downloads/zia/adding-saas-application-tenants/Adding%20SaaS_tenants_05.30.23.png)

### Feature Available
#### Unicode Support and Syntax Updates for DLP Patterns
The Zscaler service supports Unicode characters in Data Loss Prevention (DLP) patterns. The following additional updates are available:
- DLP patterns no longer need to begin with a base token.
- Nested repeats are no longer prohibited.
- Each pattern can have a maximum of 256 bytes.
- Tokens (`?i` and `?-i`) for case-insensitive matches are supported.
To learn more, see [Defining Patterns for Custom DLP Dictionaries](/zia/defining-patterns-custom-dictionaries).

### Feature Available
#### Zoho Login Services in Tenant Profile
The Tenant Profiles feature supports Zoho Login Services. This allows you to provide access to specific Zoho IDs.
[See images.](#zoho-login-rn)
To learn more, see [Adding Tenant Profiles](/zia/adding-tenant-profiles).
[]![Screenshot of ZIA Add Tenant Profile for Zoho Login Services](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Add-Tenant-Profile-Zoho-RN.png)

## June 23, 2023
### Feature Available
#### Cloud Application Tags
Cloud application tags allow you to logically group cloud applications for your organization, which enables you to handle traffic to specific cloud applications. As part of this change:
- A new tab, Cloud Application Tags, is added to the Labels & Tags page (Administration > Labels & Tags > Cloud Application Tags).
[See image.](#cloud-app-tags)
- A new field, Tags, is added to the Application Information page (Analytics > SaaS Security Report > Applications > any application on the Shadow IT Report page).
[See image.](#tags-app-info)
To learn more, see [About Cloud Application Tags](/zia/about-cloud-application-tags) and [About Application Information](/zia/about-application-information).
[]![Screenshot of ZIA Cloud Application Tags page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Cloud-Application-Tag-RN.png)
[]![Tags field in the Application Information Page](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/about-application-information/ZIA-6.2-tags-Application-Information-Page5(1).png)

### Feature Available
#### Configuring DLP Policy Block Rules to Match Only Specified Engines
The DLP policy to configure a rule that only triggers when transactions match the DLP engines specified in the rule and doesn’t match any other engines from different rules, has been extended to include Block rules. This ability allows you to influence how the DLP policy evaluates all of its rules and prevent users from leaking sensitive data when sending out non-sensitive data. You can do this by selecting the Match Only option when configuring a DLP rule that blocks transactions that match its criteria.
[See image.](#match-only-image)
To learn more, see [DLP Policy Configuration Example: Match Only](/zia/dlp-policy-configuration-example-match-only) and [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection).
[]![The Match Only option for DLP Policy Rules](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-DLP-match-only-block-action.png)

### Feature Available
#### Enhancement to Subcloud Management
When editing a subcloud, you can now disable all the data centers in a country.
[See image.](#Confirmation-Window)
To learn more, see [Editing a Subcloud](/zia/editing-subcloud).
[![Screenshot of Edit Subcloud Confirmation Window](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-summary-report/EditSubcloud_Confirm2.png)
]

### Feature Available
#### Enhancements to the SaaS Security API Application Tenants
There are new fields when adding AWS S3 as a SaaS application tenant. When adding the tenant, you need to fill in the External ID field.
[See image.](#AWS_S3)
[![The external ID field for adding a SaaS application tenant.](/downloads/zia/adding-saas-application-tenants/Amazon%20S3%20External%20ID.png)
]
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).

### Feature Available
#### Enhancements to Workflow Automation
The following enhancements were made to Workflow Automation:
- Workflows can be configured in Workflow Automation to assist you with remediating the data protection incidents that occur for your organization. Using the workflow templates provided by Workflow Automation, you can configure workflows to perform the following actions against an incident:
- Automatically close the data protection incident.
- Automatically escalate the incident to the user's manager or to an approver if the manager is not found in the system.
- Automatically notify the user that generated the incident.
- Automatically notify the user that generated the incident, as well as automatically escalate the incident to their manager or approver without waiting for a response from the user.
- Automatically notify the user that generated the incident and escalate to their manager or approver if a response is not received after a configurable time period from the user.
The workflows are automatically triggered for those incidents that match the mapped criteria configured for the workflows.
- The Audit Logs page displays log entries when a user deletes an Amazon Web Services or Azure integration.
- DLP integrations in Workflow Automation are validated with the Amazon Web Services integration when adding or editing an integration on the Integration Dashboard.
- Improved table functionality in Workflow Automation. Table columns are resizeable and the number of entries in the table appears at the bottom of the table.
- The Workflow Automation API includes the following enhancements:
- The following endpoints are added to read or update the DLP incidents:
- POST `/incidents/{dlpIncidentId}/notes`. You can use this endpoint to add notes or comments about the progress of an incident.
- GET `/incidents/{dlpIncidentId}/evidence`. You can use this endpoint to get the evidence URL of the incident to download the actual data that triggered the incident.
- The POST `/incidents/search` endpoint is enhanced to filter and search for DLP incidents by their labels.

### Feature Available
#### IKEv1 Support Update
New tenants of an organization can no longer establish IKEv1 IPSec VPN tunnels from vendor products to forward traffic to ZIA. To enable IKEv1 support for new tenants, contact Zscaler Support.
To learn more, see [Understanding IPSec VPNs](/zia/understanding-ipsec-vpns#ikev1-supported-parameters).

### Feature Available
#### New File Type Support for File Type Control & DLP
The File Type Control and Data Loss Prevention (DLP) policies support new file types in the following categories:
- [Database](#database-category)
- [Excecutable](#excecutable-category)
- [Other Microsoft](#other-microsoft-category)
- [Other Documents](#other-documents-category)
- [Source Code](#source-code-category)
To learn more, see [About File Type Control](/zia/about-file-type-control) and [About Data Loss Prevention](/zia/about-data-loss-prevention).
[]The database (.db) file type is available for the following policies:
- [File Type Control](#datbase-ftc)
- [DLP - Rule without content inspection](#database-dlp-without-inspection)
[] ![Selecting the Database File Type for a File Type Control Policy](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Database-File-Types-ftc.png)
[] ![Selecting the Database File Type for a DLP Policy without Content Inspection](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Database-File-Types-dlp.png)
[]The driver file type (.drv) is available for the following policies:
- [File Type Control](#executable-ftc)
- [DLP - Rule without content inspection](#executable-dlp-without-inspection)
[] ![Selecting the Driver File Type for a File Type Control Policy](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Driver-File-Types-ftc.png)
[] ![Selecting the Driver File Type for a DLP Policy without Content Inspection](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Driver-File-Types-dlp.png)
[]The OneNote file type (.one) is available for the following policies:
- [File Type Control](#other-microsoft-ftc)
- [DLP - Rule without content inspection](#other-microsoft-dlp-without-inspection)
[] ![Selecting the OneNote File Type for a File Type Control Policy](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-OneNote-ftc.png)
[] ![Selecting the OneNote File Type for a DLP Policy without Content Inspection](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-OneNote-dlp.png)
[]The following file types are available for the indicated policies:
- [File Type Control (.dat, .eml, .emlx, .ini, .pcapng, .pcap)](#other-docs-ftc)
- [DLP - Rule with content inspection (.dat, .eml, .emlx)](#other-docs-dlp-with-inspection)
- [DLP - Rule without content inspection (.dat, .eml, .emlx, .ini, .pcapng, .pcap)](#other-docs-dlp-without-inspection)
[] ![Selecting the Data, Email, Apple Email, Initialization, PCAP, and PCAP Next Generation File Types for a File Type Control Policy](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Other-Documents-Category-ftc.png?1686227729)
[] ![Selecting the Data, Email, and Apple Email File Types for a DLP Policy with Content Inspection](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Other-Documents-Category-dlp-with-inspection.png?1686227783)
[] ![Selecting the Data, Email, Apple Email, Initialization, PCAP, and PCAP Next Generation File Types for a DLP Policy without Content Inspection](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Other-Documents-Category-dlp-without-inspection.png?1686227871)
[]The following file types are available for the indicated policies:
- [File Type Control (.au3, .bgi, .manifest, .nls)](#source-code-ftc)
- [DLP - Rule with content inspection (.au3)](#source-code-dlp-with-inspection)
- [DLP - Rule without content inspection (.au3, .bgi, .manifest, .nls)](#source-code-dlp-without-inspection)
[] ![Selecting the Automated Script, BgInfo, Application Manifest, and National Language Support File Types for a File Type Control Policy](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Source-Code-Category-ftc.png?1686167089)
[] ![Selecting the Automated Script File Type for a DLP Policy with Content Inspection](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Source-Code-Category-dlp-with-inspection.png?1686167130)
[] ![Selecting the Automated Script, BgInfo, Application Manifest, and National Language Support File Types for a DLP Policy without Content Inspection](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Source-Code-Category-Types-dlp-without-inspection.png)

### Feature Available
#### Restore or Delete Quarantined File
Two new options, Remove and Restore, are added as part of remediation actions in the Incidents section of the SaaS Assets Report for file sharing applications.
[See image.](#remove-restore-action)
To learn more, see [SaaS Assets Report: Assets with Incidents](/zia/saas-assets-report-assets-incidents).
[]![Remove and Restore Action in the SaaS Assets with Incidents page](/sites/default/files/downloads/ZIA-6.2r-remove-restore-action.png)

### Feature Available
#### Risk Index in Web Insights Logs
A new filter and column, Risk Index, is added to the Web Insights Logs.
[See image.](#risk-index-field)
To learn more, see [Web Insights Logs: Filters](/zia/web-insights-logs-filters) and [Web Insights Logs: Columns](/zia/web-insights-logs-columns).
![Risk Index filter and column in the Web Insights Logs page](/sites/default/files/downloads/zslogin/administration/user-management/adding-users/ZIA-6.2r-risk-index-web-logs.png)
[]

### Feature Available
#### Security Fixes
The proper verification of cryptographic signatures in the SAML authentication flow of ZIA Admin Portal ensures that it no longer allows a privilege escalation (CVE-2023-28801).

### Feature Available
#### Updates to SaaS Security API Scan Configuration
For SharePoint tenants, you can set all sites to be automatically scanned for DLP or Malware rules, or you can manually choose which sites are scanned. Each SharePoint site can be scanned by the list of discovered sites or by entering a custom list of sites.
[See image.](#sharepoint-discovered-sites)
These sites can be selected in the corresponding DLP or Malware Detection rule for the SharePoint tenant.
[See image.](#sharepoint-dlp)
To learn more, see [Configuring the SaaS Security API Control Policy](/zia/configuring-saas-security-api-policies).
[]![The SharePoint Sites table for the Add Scan Schedule window.](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/configuring-saas-security-api-scan-schedules-draft/SharePoint%20Sites.png)
[]![The SharePoint sites that can be associated with each DLP rule.](/sites/default/files/downloads/zia/policies/saas-security-api/saas-security-api-policies/saas-security-api-control/configuring-saas-security-api-scan-schedules/SharePoint-Sites-for-DLP-Rules_0.png)

## June 16, 2023
### Feature Available
#### Shadow IT Report for Third-Party Vendor Data
The Shadow IT Report can display the data logged by third-party vendors such as Palo Alto Networks to provide comprehensive Shadow IT reporting that is achieved by ingesting near real-time firewall and web proxy logs, then collecting necessary data points, masking sensitive information, and securely streaming the data further to the Zscaler cloud for Shadow IT reporting.
[See image.](#shadow-it-report)
To learn more, see [About Shadow IT Report](/zia/about-shadow-it-report).
NSS Collectors
To collect logs from third-party vendor devices and stream them to the Zscaler cloud, you need to configure an NSS Collector server in the ZIA Admin Portal and deploy it on your organization's network perimeter. The NSS Collector server configuration is available under Administration > Nanolog Streaming Service > NSS Collector Servers.
[See image.](#nss-collector-servers-page)
To learn more, see [About NSS Collector Servers](/zia/about-nss-collector-servers) and [Understanding Nanolog Streaming Service](/zia/understanding-nanolog-streaming-service).
[]![Shadow IT Report in ZIA Admin Portal](/sites/default/files/downloads/ZIA-6.2r_shadow_IT_report-rn_0.png)
[]![A screenshot of the NSS Collector server configuration page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/nss-collector-servers.png)

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

## June 02, 2023
### Feature Available
#### Custom TLD Categories
The use of custom top-level domain (TLD) categories in policies can match traffic to specific TLDs and act accordingly. To learn more about selecting custom TLD categories, see:
- [Configuring the DNS Control Policy](/zia/configuring-dns-control-policy)
- [Configuring the File Type Control Policy](/zia/configuring-file-type-control-policy)
- [Configuring the Firewall Filtering Policy](/zia/configuring-firewall-filtering-policy)
- [Configuring IPS Control Policy](/zia/configuring-ips-control-policy)
- [Configuring the Sandbox Policy](/zia/configuring-sandbox-policy)
- [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection)
- [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection)
- [Configuring Forwarding Policy](/zia/configuring-forwarding-policy)
- [Configuring SSL Inspection Policy](/zia/configuring-ssl-inspection-policy)
- [About URL Filtering](/zia/about-url-filtering)

### Feature Available
#### Enhanced Shadow IT Report
The Shadow IT report is updated with the following enhancements:
- New filter options and time periods for computing the report
- Intelligible sections for a holistic and intuitive shadow IT analysis
- Ability to schedule daily and weekly reports
- Add notes and view the policies applied to an application
- New tables and columns
[See image.](#shadow-it-report-image)
To learn more, see [Shadow IT Report](/zia/shadow-it-report).
[]![Shadow IT Report in the ZIA Admin Portal](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/about-application-information/ZIA-6.2r-shadow-IT-report.rn_.png)

### Feature Available
#### Enhancement to Cloud Application Status
On the Cloud Applications (formerly Cloud Application Status) page (Administration > Cloud Applications), you can add or delete custom cloud applications that do not belong to predefined categories. These custom cloud applications belong to the newly added Custom Cloud Applications category and can be used in the Cloud App Control Policy and DLP Policy.
[See image.](#cloud-applications)
You can also create rules to control access to specific custom cloud applications.
[See image.](#custom-applications-rule)
To learn more, see [About Cloud Applications](/zia/about-cloud-applications), [Adding a Custom Applications Rule for Cloud App Control](/zia/adding-custom-applications-rule-cloud-app-control), and [About Data Loss Prevention](/zia/about-data-loss-prevention).
[]![Screenshot of ZIA Cloud Applications page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Cloud-Applications-Applications-RN.png?1674462731)
[]![Screenshot of ZIA Cloud App Control Policy Rule for Custom Applications](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Add-Custom-Rule-Cloud-App-Control-RN.png)

### Feature Available
#### Enhancements to Workflow Automation
The following enhancements were made to Workflow Automation:
- Separate privacy flags are available to admins, users, and managers/approvers to control access to the evidence file and the trigger data associated with an incident.
- The admin flags determine if admins can view the evidence file and/or trigger data for an incident on the Incidents Details page.
- The user flags determine if a user (remediation owner) can view the evidence file and/or trigger data in the notification when they are notified about an incident.
- The manager/approver flags determine if a manager/approver (escalation user) can view the evidence file and trigger data in the escalation notification when an incident is escalated to them.
- All templates, including default notification and survey, as well as any customized templates can be cloned. Access to the default templates has been modified so that you can only view them. You can no longer modify the default templates provided by Workflow Automation.
- The Audit Logs page is available in Workflow Automation. It records the actions of every admin in the Workflow Automation Admin Portal and the actions that occur through the Workflow Automation APIs.

### Feature Available
#### Logs for Bypassed Traffic
The logs for bypassed traffic include the following enhancements to the ZIA Admin Portal:
Insights Logs
The following new filters and columns are added to the respective Insights Logs page:
- Web Insights Logs:
- Bypassed Transaction Event Time
- Flow Type
- Bypassed Transaction
[See image.](#bypassed-for-web-logs)
- Firewall Insights Logs:
- Bypassed Session Event Time
- Flow Type
- Bypassed Session
[See image.](#bypassed-for-firewall)
To learn more, see [Web Insights Logs: Filters](/zia/web-insights-logs-filters), [Web Insights Logs: Columns](/zia/web-insights-logs-columns), [Firewall Insights Logs: Filters](/zia/firewall-insights-logs-filters), and [Firewall Insights Logs: Columns](/zia/firewall-insights-logs-columns).
**NSS Feeds**
The following fields are available under the respective logs when adding an NSS feed:
- Web logs:
- `%d{bypassed_traffic}`
- `%s{bypassed_etime}`
- `%s{flow_type}`
- Firewall logs:
- `%d{bypassed_session}`
- `%s{bypass_etime}`
- `%s{flow_type}`
To learn more, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs) and [NSS Feed Output Format: Firewall Logs](/zia/nss-feed-output-format-firewall-logs).
[]![Bypassed Transaction Logs in Web Insights Logs](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/logs/firewall-insights-logs-columns/ZIA-6.2-Bypass-Transaction.png)
[]![Bypassed Session Logs in Firewall Insights Logs](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/logs/firewall-insights-logs-columns/ZIA-6.2-Bypass-Session.png)

### Feature Available
#### URL Lookup Enhancement
The Cloud Application field is added to the URL Lookup window (Help > URL Lookup). You can view the cloud application category and cloud application with which the URL is associated.
[See image.](#url-lookup-window)
To learn more, see [Looking Up URLs in the ZIA Admin Portal](/zia/lookup-urls-admin-portal).
[]![Screenshot of ZIA URL Lookup Window](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-URL-Lookup-Window-RN.png)

### Feature Available
#### Zscaler Incident Receiver Configuration Enhancement
You can now deploy the Zscaler Incident Receiver on Azure VMs. Upon request, Zscaler Support shares the Incident Receiver virtual hard disk (VHD) shared access signature (SAS) token token to use when deploying the Azure instance that hosts the Zscaler Incident Receiver VM.
To learn more, see [Configuring the Zscaler Incident Receiver for Azure VMs](/zia/configuring-zscaler-incident-receiver-azure-vms).

## May 26, 2023
### Feature Available
#### SaaS Security Posture Control
The following enhancements are now available for SaaS Security Posture Control.
New SaaS Application Support
You can configure tenants for the Okta application.
[See image.](#saas-app-tenant-okta)
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
Updates to the SaaS Security Posture Control Policy & Report
Okta is available for the SaaS Security Posture Control policy and SaaS Security Posture Report.
To learn more, see [Configuring the SaaS Security API Control Policy](/zia/configuring-saas-security-posture-control-policy) and [SaaS Security Posture Report](/zia/saas-security-posture-report).
[]![The list of all the available SaaS application Tenants.](/sites/default/files/downloads/List%20of%20SaaS%20Applications.png)

## May 19, 2023
### Feature Available
#### UEBA Alerts for Inline and API Channels
Zscaler has introduced the UEBA Alert rules for the inline channel that cover multiple events and alert types based on your organizational requirements.
You can view the list of both inline and API rules listed under the Alert Rules page (Alerts > Alert Rules) for UEBA alerts. Click Add Alert Rules on the Alert Rules page to select the Inline or API channel to configure alert rules for each of these channels.
[See image.](#ueba-add-alert-rule)
The following list provides the details of each alert type for Inline and API channels.
- [API Alert Types](#api-alert-types-table)
- [Inline Alert Types](#inline-alert-types-table)
Each of the preceding alert rules can be completely customized based on your requirements and can have customized sets of alert trigger criteria.
Each of the alerts have dynamic actions, such as:
**For API Channels**:
- **Alert**: An email notification for the alert.
- **Place user in a group**: Identified user triggering the alert can be placed in a custom group, which can be further used in a DLP rule, URL Filtering, or Cloud App Control policy to apply further actions.
[See image.](#alert-action-for-api)
**For Inline Channels**:
- **Alert**: An email notification for the alert.
- **Place user in a group**: Identified user triggering the alert can be placed in a custom group, which can be further used in a DLP rule, URL Filtering, or Cloud App Control policy to apply further actions.
- **Trigger Multi-Factor Authentication**: Identified user can be forced to do a step-up authentication, if the alert trigger criteria is met.
[See image.](#alert-action-for-inline)
To learn more, see [About Security & UEBA Alerts](/zia/about-security-ueba-alerts).
Realignment of SaaS Security Alerts
The SaaS Security alert is moved from the SaaS Security API Control > Activities & Alerts page and the SaaS Security Report page to align with the Security & UEBA Alerts page.
SaaS Security API Control Policy
You can configure the default SaaS Security Activity alerts using the Add Alert Rule page (Alerts > Alert Rules > Add Alert Rules). Select Access or Data under Event Types to view the relevant options under Alert Type for configuring the alerts.
[See image.](#add-alert-rule)
SaaS Security Report
The SaaS Security Report page no longer displays the alert details. For the detailed alert history, view the Alert History page under Security & UEBA Alerts.
[See image.](#alert-history-page)
To learn more, see [About Alert History](/zia/about-alert-history) and [About Alert Rules](/zia/about-alert-rules).
[]![The UEBA add alert page that helps you select the Inline or API rule.](/sites/default/files/downloads/UEBA-Add-Alert-Rule.png)
[]![The UENA Alert action type for API channels.](/sites/default/files/downloads/Alert-Action-For-API.png)
[]![The UENA Alert action type for inline channels.](/sites/default/files/downloads/Alert-Action-For-Inline.png)
[]
| Alert Type | Description |
| ---------- | ----------- |
| Impossible Travel | Identify users accessing the organization’s applications from different locations in a short period of time. |
| Multiple Failed Logins | Identify users with multiple failed login attempts to the organization’s applications in a short period of time. |
| Bulk Download | Identify users with large amounts of download activities in a short period of time. |
| Bulk Upload | Identify users with large amounts of upload activities in a short period of time. |
| Code Repo Shared Externally | Identify external users accessing the organization’s code repositories. |
| Code Repo Made Public | Identify if the organization’s code repositories are made public. |
| Bulk Files Delete | Identify users with large amounts of delete activities in a short period of time. |
| Bulk Share of Data | Identify users with large amounts of share activities in a short period of time. |
| Excessive Admin Activities | Identify users performing high admin activities in a short period of time. |
[See image.](#ueba-api-alert-types)
[]
| Alert Type | Description |
| ---------- | ----------- |
| Upload of Invoice | Identify users who have uploaded invoices in a short period of time. |
| Upload of Tax documents | Identify users who have uploaded tax documents in a short period of time. |
| Upload of Resumes | Identify users who have uploaded resumes in a short period of time. |
| Upload of Medical documents | Identify users who have uploaded medical documents in a short period of time. |
| Upload of Real Estate documents | Identify users who have uploaded real estate documents in a short period of time. |
| Upload of Legal documents | Identify users who have uploaded legal documents in a short period of time. |
| Upload of Court Form documents | Identify users who have uploaded court form documents in a short period of time. |
| Upload of Technical documents | Identify users who have uploaded technical documents in a short period of time. |
| Upload of Transportation and Motor documents | Identify users who have uploaded documents related to transportation and motor in a short period of time. |
| Upload of Immigration documents | Identify users who have uploaded immigration documents in a short period of time. |
| Upload of Insurance documents | Identify users who have uploaded insurance documents in a short period of time. |
| Upload of Corporate Finance documents | Identify users who have uploaded corporate finance documents in a short period of time. |
| Upload of Corporate Legal documents | Identify users who have uploaded legal documents in a short period of time. |
| Data exfiltration by password protected or encrypted docs | Identify users who have shared data after applying encryption or passwords to avoid content inspection. |
| Upload to high risk countries | Identify users who have uploaded data to locations in suspicious countries. |
| Upload from high risk countries | Identify users who have uploaded data from locations in suspicious countries. |
| Bulk Activity Alert | Identify users who have performed a certain set of activities in a short period of time. Through this alert multiple activities for the SaaS Security API can be tracked for a user.Supported Activities: Upload, Share, Create, Edit, Delete, Comment, Download, Rename, Form Sharing, File Transfer, Chat, Post, Send email, Send Attachments, and Comment |
| Bulk upload of sensitive data | Identify users who have uploaded sensitive data in a short period of time. |
| Bulk download of sensitive data | Identify users who have downloaded sensitive data in a short period of time. |
[See image.](#ueba-inline-alert-types)
[]![The UEBA Alert types for API channels.](/sites/default/files/downloads/tech-pubs-drafts/miscellaneous-draft-articles/ueba-alerts-inline-and-api-channels/UEBA-API-Alert-Types.png)
[]![The UEBA Alert types for inline channels.](/sites/default/files/downloads/tech-pubs-drafts/miscellaneous-draft-articles/ueba-alerts-inline-and-api-channels/UEBA-Inline-Alert-Types.png)
[]![This screen allows you to configure different types of alerts nd events.](/sites/default/files/downloads/Add%20Alert%20Rule.png)
[]![This page provides the detailed view of all past alerts.](/sites/default/files/downloads/Alert%20History%20Page.png)

## May 18, 2023
### Feature Available
#### Simplifying Isolation URLs
Isolation URLs appear more like URLs from non-isolated sessions. Isolation information is hidden from the URL when in isolation view. Isolation URLs can still be copied and shared with other users.
The isolation URL appears in its simple version whether a user is in native or browser-in-browser mode. It contains a domain in the format of <clusterid>.isolation.zscaler.com. The region identifier and the tenant identifier are still available as a query string in the URL.
To learn more, see [User Experience Modes in Isolation](/isolation/user-experience-modes-cloud-browser-isolation).

## May 12, 2023
### Feature Available
#### Cloud App Control Policy Enhancement
You can granularly control cascading to URL filtering for a particular Cloud App Control policy. As part of this change, the Cascade to URL Filtering option is added to the Add/Edit Cloud App Control policy rule page (Policies > URL & Cloud App Control > Cloud App Control Policy > Add).
[See image.](#img-cascade-url-filtering)
To learn more, see [Adding Rules to Cloud App Control Policy](/zia/adding-rules-cloud-app-control-policy).
[![Screenshot of ZIA Cloud App Control Policy with Cascade to URL Filtering](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Cloud-App-Control-Policy-RN.png)
]

### Feature Available
#### DLP Support for New PII Dictionaries
The following are new predefined DLP dictionaries:
- Tax Identification Number (Austria)
- Tax Identification Number (Belgium)
- Tax Identification Number (Denmark)
- Tax Identification Number (France)
- Tax Identification Number (Germany)
- Tax Identification Number (Hungary)
- Tax Identification Number (Luxembourg)
- Tax Identification Number (New Zealand)
- Tax Identification Number (Portugal)
- Tax Identification Number (Sweden)
To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).

### Feature Available
#### Enhancements to Workflow Automation
The following enhancements were made to Workflow Automation:
- DLP application integrations (AWS and Azure) are managed on the Integrations dashboard in Workflow Automation. You can delete a DLP application integration (AWS and Azure) using the Integrations dashboard. Deleted DLP application integrations are listed on their respective Zscaler DLP Integrations details pages within the Integrations dashboard. The Zscaler DLP Integration details pages display the integration name with a status of Deleted. You can edit the privacy settings for a deleted DLP application integration.
- A Notification Center page is available in Workflow Automation. This page lists the different alert notifications that have an impact on Workflow Automation, such as when the default incident group has not been assigned to an admin and when there is no active channel for notifications.
- Specific incident groups can be assigned to admins with Full Access to Workflow Automation on the Admins page. You have the option to assign all incident groups or one or more specific incident groups to these admins. Full Access admins can still view and edit all incidents, even if they are assigned to specific incident groups. Privileges for Restricted Access admins are not affected by this enhancement.

### Feature Available
#### New File Type Support for File Type Control & DLP
The File Type Control and Data Loss Prevention (DLP) policies support the following file types in the Other Documents category:
- [AutoCAD (.dxf)](#autocad-file-types)
- [Integrated Circuit File (.gds, .gds2, .oas, .oasis)](#integrated-circuit-file-types)
- [Tableau (.twb, .tbm, .twbx, .hyper, .tde, .tds, .tdsx)](#tableau-file-types)
To learn more, see [About File Type Control](/zia/about-file-type-control) and [About Data Loss Prevention](/zia/about-data-loss-prevention).
[]AutoCAD file types are available for the following policies:
- [File Type Control](#autocad-ftc)
- [DLP (Rule without content inspection)](#autocad-dlp)
[]Integrated Circuit File types are available for the following policies:
- [File Type Control](#integrated-circuit-ftc)
- [DLP (Rule without content inspection)](#integrated-circuit-dlp)
[]Tableau file types are available for the following policies:
- [File Type Control](#tableau-ftc)
- [DLP (Rule with and without content inspection)](#tableau-dlp)
[] ![Selecting the AutoCAD File Type for a File Type Control Policy](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-AutoCAD-File-Types-ftc.png)
[] ![Selecting the AutoCAD File Type for a DLP Policy](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-AutoCAD-File-Types-dlp.png)
[] ![Selecting the Integrated Circuit File Type for a File Type Control Policy](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-IntegratedCircuitFile-File-Types-ftc.png)
[] ![Selecting the Integrated Circuit File Type for a DLP Policy](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-IntegratedCircuitFile-File-Types-dlp.png)
[] ![Selecting the Tableau File Type for a File Type Control Policy](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-tableau-File-Types-ftc.png)
[] ![Selecting the Tableau File Type for a DLP Policy](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-tableau-File-Types-dlp.png)

### Feature Available
#### Support for Multi-Alphanumeric Identities in EDM Templates
When creating an EDM Template, you have the option to configure an alphanumeric field with the Multi-alphanumeric Identity data type. This type of field can also be configured as a primary field for the EDM template.
[See image.](#index-tool-named-identity-alphanumeric)
To learn more, see [Creating an Exact Data Match Template](/zia/creating-exact-data-match-template).
[] ![Selecting the Multi-alphanumeric Identity data type for a field on the EDM template in the Zscaler Index Tool](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Zscaler-Index-Tool-Multi-Alphanumeric-Identity.png)

### Feature Available
#### Support for Quarantine Tombstone Template in SaaS Security API DLP and Malware Policies
The SaaS Security API Control policies support a new Tombstone Template action that allows you to associate a tombstone template file with a quarantine action to provide customized tombstone messages.
Tenants under the following application types support tombstone templates for DLP rules:
- CRM Application
- ITSM Application
[See image.](#saas-security-api-tombstone-template)
Tenants under the following application types support tombstone templates for malware rules:
- Collaboration Application
- CRM Application
- File Sharing Application
- ITSM Application
- Public Cloud Storage Application
[See image.](#casb-tombstone-template-malware-rule)
You can add and manage multiple tombstone templates on the Notification Templates > Quarantine > Tombstone Templates page in the ZIA Admin Portal.
[See image.](#quaratine_templates_add)
To learn more, see [Configuring the SaaS Security API DLP Policy](/zia/configuring-saas-security-api-dlp-policy), [Configuring the SaaS Security API Malware Detection Policy](/zia/configuring-saas-security-api-malware-detection-policy) and [About Quarantine Tombstone File Templates](/zia/about-quarantine-tombstone-file-templates).
[]![The Tombstone Template action enables you to select the Quarantine Tombstone Template to apply to the rule.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-SaaS-Security-API-DLP-Tombstone-Templates.png)
[]![Quarantine Notification Template page for creating new custom templates.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-SaaS-Security-API-Quarantine%20Notification%20About.png)
[]![The Tombstone Template action enables you to select the Quarantine Tombstone Template to apply to the malware rule.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-SaaS-Security-API-Malware-Tombstone-Templates.png)

### Feature Available
#### Workflow Automation API
Workflow Automation supports customer-facing APIs for managing DLP incidents. API management is automatically enabled when you subscribe to Workflow Automation.
To learn more, see [About the Workflow Automation API](/zia/about-workflow-automation-api).
As part of the Workflow Automation API feature, a new API Keys page is added to the Workflow Automation Admin Portal to create and manage API keys. API access requires a Key ID and Key Secret for authentication.
[See image.](#api-keys-page)
To learn more, see [About API Keys](/zia/about-api-keys) and [Managing Workflow Automation API Keys](/zia/managing-workflow-automation-api-keys).
[]![Screenshot of the API Keys page in the Workflow Automation Admin Portal](/sites/default/files/downloads/zia/workflow-automation/api-management/about-api-keys/workflow-automation-api-release-notes.png)

## May 05, 2023
### Feature Available
#### Data Protection Enhancement for Managing and Resolving Incidents
The new Workflow Automation application integrates with ZIA, which enables you to manage and resolve the different Data Protection incidents that occur in your organization. Workflow Automation captures those Data Protection incidents generated from the different Data Loss Prevention (DLP) policies defined in ZIA and provides a closed loop Incidents page where you can review and remediate those Data Protection incidents all in one location. The Incidents page lists all of the Data Protection incidents along with the details for each of those incidents. The incident details include the metadata for the incident and the data that triggered the incident.
[See image.](#Incidents-Dashboard)
To learn more, see [What is Zscaler Workflow Automation?](/zia/what-zscaler-workflow-automation), [About Incidents](/zia/about-incidents), and [Viewing and Managing Incident Details](/zia/viewing-managing-incident-details).
To use the Workflow Automation application, admins are provisioned in ZIA with an admin role that has the new Workflow Access permission defined. Admin roles can be configured with either Full workflow access or Restricted workflow access to the Workflow Automation application.
[See image.](#add-administrator-role-window)
To learn more, see [Adding Admin Roles](/zia/adding-admin-roles).
[]![Viewing DLP Incidents on the Incidents Dashboard in ZWA](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZWA-Incidents-Dashboard-Overview.png)
[] ![Viewing Workflow Access Permission on the Add Administrator Role Window](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Add-Administer-Role-Window-Workflow-Access.png)

### Feature Available
#### Support for ZPA Application Segment
You can configure rules for source IP anchored traffic in the following ZIA policies using the new criterion, ZPA Application Segment.
- [DLP Policy](/zia/about-data-loss-prevention)
- [DLP Policy with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection)
- [DLP Policy without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection)
- [File Type Control](/zia/configuring-file-type-control-policy)
- [Firewall Filtering](/zia/configuring-firewall-filtering-policy)
- [IPS Control](/zia/configuring-ips-control-policy)
- [Sandbox](/zia/about-sandbox)
- [SSL Inspection](/zia/configuring-ssl-inspection-policy)
The policies support only those ZPA application segments that have Source IP anchoring enabled in the ZPA Admin Portal.
Updates to Dashboard & Web Insights
The following updates are available for ZPA Application Segments:
- A new data type, Application Segment, is added to the Firewall and Web data classes in the New Widget window.
- A new widget, Top Application Segments, is added to the following dashboard pages:
- Web Overview
- Security
- Web Browsing
- Firewall Overview
- IPS Overview
To learn more, see [Firewall Data Types and Filters](/zia/firewall-data-types-and-filters), [Web Data Types and Filters](/zia/web-data-types-and-filters), and [About Dashboards](/zia/about-dashboards).

## April 21, 2023
### Feature Available
#### Support for EDNS Client Subnet (ECS) Injection
The Zscaler service extends support to include EDNS Client Subnet (ECS) in DNS queries that allows you to pass the IP address or subnet information of the requesting client to DNS resolvers. Using ECS, an authoritative or intermediate DNS nameserver can provide geo-located responses for clients.
You can configure ECS prefixes under Administration > EDNS Client Subnet Prefix Objects and then designate one of the ECS prefixes to be added to DNS requests on the Advanced Settings page.
[See image.](#configure-and-select-ecs-prefix)
To learn more, see [About EDNS Client Subnet (ECS) Injection](/zia/about-edns-client-subnet-ecs-injection).
DNS Insights Logs
The following new filters and columns are added to the DNS Insights Logs page:
- ECS Object Name
- ECS Prefix
- ECS Prefix Length
[See image.](#ecs-logs)
To learn more, see [DNS Insights Logs: Columns](/zia/dns-insights-logs-columns) and [DNS Insights Logs: Filters](/zia/dns-insights-logs-filters).
NSS Feeds
The fields `%s{ecs_prefix}` and `%s{ecs_slot}` are now available when adding an NSS feed for DNS logs.
To learn more, see [NSS Feed Output Format: DNS Logs](/zia/nss-feed-output-format-dns-logs).
[]![ECS logs in DNS Insights Logs](/sites/default/files/downloads/ZIA-6.2r-ednscs-logspng.png)
[]![Screenshots of ECS prefix creation and configuration pages](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/create-and-configure-ecs-prefix.png)

## April 14, 2023
### Feature Available
#### AI and ML Applications URL Category
The AI and ML Applications URL category is added to the Information Technology super category. It consists of sites that provide tools, services, or information related to generative AI (i.e., a subfield of artificial intelligence that can generate new text, images, videos, or audio.).
This category is enabled from the backend after it is deployed across all production clouds.
[See image.](#url-categories-ai-ml)
To learn more, see [About URL Categories](/zia/about-url-categories).
[]![Screenshot of ZIA URL Categories Page with AI and ML Applications](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-URL-Categories-Page-RN.png)

### Feature Available
#### Bank Identification Number (BIN) Support in DLP Credit Card Dictionaries
You can define a list of BIN numbers in the predefined Data Loss Prevention (DLP) credit card dictionary or its clones so that the numbers are included in or excluded from DLP scan match.
[See image.](#dlp-dictionary-bin-support)
To learn more, see [Editing Predefined DLP Dictionaries](/zia/editing-predefined-dlp-dictionaries).
The DLP endpoints within the cloud service API include the following attributes to include or exclude a list of BIN values from the predefined DLP credit card dictionary or its clones.
- `binNumbers`
- `includeBinNumbers`
To learn more, see the [API Reference](/zia/about-api).
[]![Support for Bank Identification Numbers (BIN) in Data Loss Prevention (DLP) credit card dictionaries for Zscaler Internet Access (ZIA)](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-DLP-Dictionary-BIN-support-Release-Note.png)

### Feature Available
#### Changes to Backup & Restore
The maximum number of restore points allowed per organization has been changed to 12. To learn more, see [About Backup and Restore](/zia/about-backup-and-restore).
If you currently have more than 12 restore points, only the most recent 12 restore points are retained after this upgrade. All other older restore points except the golden restore point are deleted. The golden restore point is retained as part of the 12 restore points, irrespective of the time of creation.

### Feature Available
#### Cloning of ID-based Predefined DLP Dictionaries
You can clone identification-based predefined Data Loss Prevention (DLP) dictionaries, such as Credit Cards, Social Security Numbers, National Identification Numbers, etc. Cloning dictionaries allows you to use separate versions of the same dictionary with different Confidence Score Thresholds, as well as with different dictionary-specific parameters.
[See image.](#dlp-clone-dlp-dictionaries)
To learn more, see [Cloning Predefined DLP Dictionaries](/zia/cloning-predefined-dlp-dictionaries).
The DLP endpoints within the cloud service API include the following attributes to clone identification-based predefined DLP dictionaries:
- `predefinedClone`
- `dictTemplateId`
To learn more, see the [API Reference](/zia/about-api).
[]![Support for cloning Data Loss Prevention (DLP) dictionaries for Zscaler Internet Access (ZIA)](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Clone-Predefined-DLP-Dictionary-RN.png)

### Feature Available
#### Data Discovery Report
You can use the Data Discovery Report (Analytics > Data Discovery Report) as a single location to access a high-level overview of your organization's Data Loss Prevention (DLP) content. The report contains a series of widgets and allows you to click items on charts to drill down to more granular data.
[Show image.](#data-discovery-dashboard-full-page)
Based on what you click on the report and the filters you set, the Data Discovery Details page provides more specific information about content, applications, and users.
[Show image.](#data-discovery-details-full-page)
To learn more, see [About the Data Discovery Report](/zia/about-data-discovery-report).
[]![Screenshot of the Data Discovery Report page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/zia-data-discovery-report-page-RN.png)
[]![Screenshot of the Data Discovery Details page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/zia-data-discovery-details-page.png?1676586167)

### Feature Available
#### DLP Support for Machine Learning-Based Dictionaries
There are 13 new predefined ML-Based DLP dictionaries:
- Corporate Finance Document: Detects corporate finance documents, like earnings reports, Form 10-K, etc.
- Corporate Legal Document: Detects corporate legal documents, like LLC operational agreements, Secretary of State forms, etc.
- Court Document: Detects court documents, like attorney forms, witness subpoenas, etc.
- Immigration Document: Detects immigration documents, like passport renewal forms, I-485, I-856, I-907, etc.
- Insurance Document: Detects insurance documents, like employee insurance, home insurance, commercial insurance, medical insurance, etc.
- Invoice Document: Detects invoice documents, like Bill of Sale forms, purchase orders, etc.
- Legal Document: Detects legal documents, like living wills, name change certificates, etc.
- Medical Document: Detects medical documents, like medical consent forms, HIPAA forms, medical record forms, etc.
- Real Estate Document: Detects real estate documents, like personal or commercial lease agreements, property buying or selling agreements, etc.
- Resume Document: Detects resume documents.
- Tax Document: Detects tax documents, like 1040 forms, 1099 forms, 1998-T forms, 3921 forms, etc.
- Technical Document: Detects technical documents, like computer user manuals, white papers, technical publications, etc.
- Transportation and Motor Department Document: Detects transportation and motor department documents, like sale or transfer of a vehicle, license forms, driving records, etc.
[See image.](#ml-document-dictionaries)
To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).
[![Viewing Machine Learning Document Dictionaries in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-DLP-Dictionaries-Engines-ML-Based-Dictionaries.png?1677774842)
]

### Feature Available
#### Enhanced Logs for Upload and Download Files
The following enhancements are available for Insights, Insights Logs, Reports, and NSS Feeds to show the logs for uploaded and downloaded files separately in the ZIA Admin Portal:
Insights Logs
A new advanced filter, Document Type, is added for all applications in the SaaS Assets Report: Assets with Incidents Page.
A new filter and column, Document Type, is added to the SaaS Security Insights Logs page.
The following data types are added to the Web Insights:
- Download File Type
- Upload File Type
The following filters are added to the Web Insights Logs:
- Document Type
- Download File Name
- Download File Type
- Download File Type Super Category
- Upload File Name
- Upload File Type
- Upload File Type Super Category
The following columns are added to the Web Insights Logs:
- Document Type
- Upload File Name
- Upload File Type
- Download File Name
- Download File Type
[See image.](#enhanced-logs-for-files)
To learn more, see [SaaS Assets Report: Assets with Incidents](/zia/saas-assets-report-assets-incidents), [SaaS Security Insights Logs](/zia/saas-security-insights-logs), [Web Data Types and Filters](/zia/web-data-types-and-filters), [Web Insights Logs: Filters](/zia/web-insights-logs-filters), and [Web Insights Logs: Columns](/zia/web-insights-logs-columns).
NSS Feeds
The following fields are available when adding an NSS feed for Web Logs. These fields log the uploaded file information.
- `%s{upload_filetype}`
- `%s{upload_filename}`
- `%s{upload_filesubtype}`
- `%s{upload_fileclass}`
- `eupload_filename` (Hex Encoded Field)
- `b64upload_filename` (b64 Field)
The following existing fields now log the downloaded file information:
- `%s{filetype}`
- `%s{filename}`
- `%s{filesubtype}`
- `%s{fileclass}`
- `efilename` (Hex Encoded Field)
- `b64filename` (b64 Field)
The field `%s{upload_doctypename}` is added to the Web Logs and the SaaS Security Logs to log the type of document uploaded or downloaded.
To learn more, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs)​​​​​​ and [NSS Feed Output Format: SaaS Security Logs](/zia/nss-feed-output-format-saas-security-logs).
[![Enhanced Logs for Upload and Download Files](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/logs/web-insights-logs-filters/ZIA-6.2-rn-enhanced%20file.png)
]

### Feature Available
#### Enhancement to Cloud NSS Feeds
A JSON Array Notation toggle is now available in the Add Cloud NSS Feed window. This setting is enabled by default when you select JSON as the Feed Output Type. You can disable this setting.
[See image.](#zia-cloud-nss-feed-json-array-toggle)
To learn more, see [Adding Cloud NSS Feeds](/zia/adding-cloud-nss-feeds).
[![Screenshot of JSON Array Notation toggle in the Add Cloud NSS Feed window in the ZIA Admin Portal](/sites/default/files/downloads/zia_cloud_nss_feed_json_array.png)
]

### Feature Available
#### Enhancement to Google App in Tenant Profiles
The Allow Visitor Access field is added to the Add Tenant Profile page (Administration > Tenant Profiles > Add Tenant Profile) for Google App. The field allows visitors access to the domains in the tenant profile based on the selection.
[See image.](#allow-visitor-access)
To learn more, see [Adding Tenant Profiles](/zia/adding-tenant-profiles).
[]![Screenshot of Add Tenant Profile for Google App](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Add-Tenant-Profile.png?1669027925)

### Feature Available
#### Enhancements to Indexed Document Match (IDM) Dictionary
When configuring Indexed Document Match settings for Data Loss Prevention (DLP) dictionaries, you can exclude documents that are a 100% match to already-indexed documents.
[See image.](#IDM-exact-match-toggle)
You can also configure the exclusion setting using Data Loss Prevention endpoints within the cloud service API.
To learn more, see [Defining IDM Match Accuracy for Custom DLP Dictionaries](/zia/defining-idm-match-accuracy-custom-dlp-dictionaries) and [API Reference](/zia/about-api).
[]![Selecting the Indexed Document Match dictionary type](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Add-DLP-Dictionary-IDM-ignore-exact-match.png)

### Feature Available
#### Sum-Based Expressions in DLP Engines
You can use the Sum operator in expressions when creating, editing, or cloning Data Loss Prevention (DLP) engines. The Sum operator allows you to specify the sum total of matches that trigger a group of dictionaries specified in the DLP engine.
[See image.](#dlp-engines-sum-operator)
To learn more, see [Understanding DLP Engines](/zia/understanding-dlp-engines).
[]![Support for the Sum Operator in Data Loss Prevention (DLP) Engines for Zscaler Internet Access (ZIA)](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-DLP-Engine-Builder-Sum-Operator-RN.png)

### Feature Available
#### Support for Cloning DLP Engines
You can duplicate a predefined or custom Data Loss Prevention (DLP) engine to quickly copy the functionality of an existing engine for a different use. To learn more, see [Cloning DLP Engines](/zia/cloning-dlp-engines).
[See image.](#dlp-engine-cloning-support)
[]![Support for Cloning Data Loss Prevention (DLP) Engines for Zscaler Internet Access (ZIA)](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-DLP-Engine-Cloning-Release-Note.png)

### Feature Available
#### Support for Email Labels in SaaS Security API DLP and Malware Policies
The SaaS Security API DLP and Malware policies support a new email label action. This action allows you to assign email labels based on the content sensitivity of an email within Gmail and Microsoft Exchange clients.
[See image.](#email-labels-labels-and-tags)
To learn more, see [About Email Labels](/zia/about-email-labels).
[]![Email Labels allows you to assign email labels based on the content sensitivity of an email within Gmail and Microsoft Exchange clients.](/sites/default/files/downloads/ZIA-Labelsandtags-Email-Labels-RN.png)

### Feature Available
#### Support for IoT Device Discovery and Report
The IoT Discovery Report shows the device inventory and their insights discovered from unauthenticated web traffic. This gives awareness into your organization’s traffic discovered from different IoT devices, the number of devices connected from each device type and classification, the number of devices discovered at each location, the applications they connect to, their traffic destinations, and more.
[See image.](#iot-report-page)
To learn more, see [About the IoT Discovery Report](/zia/about-iot-discovery-report).
As part of the IoT Device Discovery feature, the following enhancement is made to the ZIA Admin Portal:
Locations and Sub-Locations
You can discover IoT/OT devices, servers, and unmanaged devices (e.g., personal user devices) at both existing and new locations and sub-locations. As part of this change, the following fields are added to the Add/Edit Location (Administration > Location Management > Add Location) window and Add/Edit Sub-Location (Administration > Location Management > Add Sub-Location icon) window:
- City Geolocation
- Enable IoT Discovery
[See image.](#iot-discovery)
You can also enable IoT discovery for multiple locations and sub-locations using the CSV file.
To learn more, see [Configuring Locations](/zia/configuring-locations), [Configuring Sub-Locations](/zia/configuring-sub-locations), and [Configuring Multiple Locations and Sub-Locations](/zia/configuring-multiple-locations-and-sub-locations).
[]![IoT Discovery Report Page in the ZIA Admin Portal](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/about-iot-discovery-report/ZIA-6.2r-IoT-Discovery-Report2.png)
[]![Screenshot of ZIA Add Location Window with City Geolocation field](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Add-Location-Location-Section-RN.png)
![Screenshot of ZIA Add Location Window with Enable IoT Discovery option](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Add-Location-Gateway-Options-IoT-Discovery-RN.png)

## April 07, 2023
### Feature Available
#### Enhancement to Locations and Sub-Locations
Added the Enable Basic Authentication option in the Add Location window (Administration > Location Management > Add Location) and Add Sub-Location window (Administration > Location Management > Add Sub-Location). You can enforce basic authentication on all traffic from a location or a sub-location. You can also enforce basic authentication on all traffic from multiple locations or sub-locations using the Import CSV file.
[See image.](#basic-auth-location-sub-loc)
To learn more, see [Configuring Locations](/zia/configuring-locations), [Configuring Sub-Locations](/zia/configuring-sub-locations), and [Configuring Multiple Locations and Sub-Locations](/zia/configuring-multiple-locations-and-sub-locations).
[]![Screenshot of ZIA Add Locations and Add Sub-locations Window with Enable Basic Authentication](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Locations-Sub-Locations-Basic-Auth-RN.png)

### Feature Available
#### Support for ICMP Requests in Source IP Anchoring
Source IP Anchoring supports ICMP echo requests and/or responses for ICMP-enabled ZPA application segments.
To learn more, see [Understating Source IP Anchoring](/zia/about-source-ip-anchoring).

## March 31, 2023
### Feature Available
#### SaaS Security API
The following enhancements are now available for SaaS Security API.
Updates to SaaS Application Support
You can configure tenants for Confluence, the file sharing application.
[See image.](#saas_applications)
To learn more, see [About SaaS Application Tenants](/zia/about-saas-application-tenants).
Updates to SaaS Security API Control Policies & Scan Configuration
You can configure the SaaS Security API Control policies and scan schedules for Confluence, the file sharing application.
To learn more, see [Configuring the SaaS Security API DLP Policy](/zia/configuring-saas-security-api-dlp-policy) and [Configuring the SaaS Security API Malware Detection Policy](/zia/configuring-saas-security-api-malware-detection-policy).
Updates to the SaaS Assets Summary Report
You can view Confluence, the file sharing application, in the SaaS Assets Summary Report.
To learn more, see [SaaS Assets Summary Report](/zia/saas-assets-summary-report).
Updates to the SaaS Assets Report
You can view Confluence, the file sharing application, in the SaaS Assets Report.
To learn more, see [Saas Assets Report](/zia/saas-assets-report) and [SaaS Assets Report: Assets with Incidents](/zia/saas-assets-report-assets-incidents).
Updates to SaaS Security Insights & Insights Logs
You can view Confluence, the file sharing application, in SaaS Security Insights and Insights Logs.
To learn more, see [SaaS Security Insights](/zia/saas-security-insights) and [SaaS Security Insights Logs](/zia/saas-security-insights-logs).
Updates to NSS Feeds for SaaS Security Logs
You can view Confluence, the file sharing application, in the SaaS Security application category.
To learn more, see [Adding NSS Feeds for SaaS Security Logs](/zia/adding-nss-feeds-saas-security-logs) and [Adding Cloud NSS Feeds for SaaS Security Logs](/zia/adding-cloud-nss-feeds-saas-security-logs).
[]![List of SaaS Applications.](/sites/default/files/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/M365_01_Providers_Comm_02.png)

## March 24, 2023
### Feature Available
#### Cloud NSS Support for New SIEMs
Cloud Nanolog Streaming Service (NSS) allows you to stream ZIA logs directly into a cloud-based security information and event management (SIEM) system without deploying an NSS virtual machine.
Cloud NSS now supports two new SIEM types: Microsoft Azure Sentinel and Amazon Simple Storage Service (S3).
[See image.](#zia-cloud-nss-sentinel-s3)
To learn more, see [ZIA and Microsoft Azure Sentinel Integration Guide](/zia/zia-microsoft-azure-sentinel-integration-guide) and [ZIA and Amazon S3 Integration Guide](/zia/zia-amazon-s3-integration-guide).
[![Screenshot of Cloud NSS SIEM Type menu with Azure Sentinel and Amazon S3 selected](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/zia_cloud_nss_s3_sentinel.png)
]

### Feature Available
#### SaaS Security Logs
The following enhancements are available for SaaS Security Logs:
SaaS Security Insights Logs and SaaS Assets Report
The External Owner field is renamed to Non-Provisioned Owner in the SaaS Security Insights Logs and SaaS Assets Report.
[See image.](#non-provisioned-owner-logs)
To learn more, see [SaaS Security Insights Logs](/zia/saas-security-insights-logs) and [SaaS Assets Report: Assets with Incidents](/zia/saas-assets-report-assets-incidents).
NSS Feeds
In the SaaS Security NSS Feeds, the filter External Owner is renamed to Non-Provisioned Owner for all SaaS Security application categories.
To learn more, see [Adding NSS Feeds for SaaS Security Logs](/zia/adding-nss-feeds-saas-security-logs) and [Adding Cloud NSS Feeds for SaaS Security Logs](/zia/adding-cloud-nss-feeds-saas-security-logs).
[]![Screenshot of Non-Provisioned Owner field in SaaS Insights Logs](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/logs/saas-security-insights-logs/ZIA-6.2r-non-provisioned-owner-logs.png)

### Feature Available
#### SaaS Security Posture Control
Jira Software and Confluence are now available for the SaaS Security Posture Control policy and SaaS Security Posture Report. Additionally, new policies are added for the following applications:
- Bitbucket
- GitHub
- Google Workspace
- Microsoft 365
- Salesforce
New Compliance Support
The following new compliances are supported in the SaaS Security Posture Report:
- CIS Google Workspace v1.0.0
- CIS Microsoft 365 v1.4
- HIPAA
- ISO 27001
- NIST 800-53 Rev.4
- NIST 800-53 Rev.5
- PCI DSS v3.2
- SOC2 AICPA TSC 2017
- GDPR
To learn more, see [Configuring the SaaS Security Posture Policy](/zia/configuring-saas-security-posture-control-policy) and [About SaaS Security Posture Report](/zia/about-saas-security-posture-report).

### Feature Available
#### User Risk Profile
The User Risk Profile applies the policies to users based on their risk scores. You can select the users belonging to any of the following risk score range levels:
- Low
- Medium
- High
- Critical
This feature is added as a criterion in the following policies:
- [Cloud App Control](/zia/adding-rules-cloud-app-control-policy)
- [Data Loss Prevention with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection) and [Data Loss Prevention without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection)
- [URL Filtering](/zia/configuring-url-filtering-policy)
[See image.](#policies-with-user-risk-profile)
[]![Screenshot of Add Cloud App Category Rule Window with User Risk Profile](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Add-Cloud-App-Category-Rule-6.2.png)
![Screenshot of Add DLP Rule Window with User Risk Profile](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Add-DLP-Rule-6.2.png)
![Screenshot of Add URL Filtering Rule Window with User Risk Profile](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Add-URL-Filtering-Rule-6.2.png)

### Feature Available
#### Zscaler Incident Receiver Configuration Enhancement
You can use an Amazon Machine Image (AMI) to deploy the Zscaler Incident Receiver on Amazon Web Services (AWS) EC2 VMs. This deployment supports either Amazon S3 or SFTP storage. Upon request, Zscaler support shares the AMI ID and description for you to use when deploying the Incident Receiver on an EC2 VM.
To learn more, see [Configuring the Zscaler Incident Receiver for Amazon Web Services EC2 VMs](/zia/configuring-zscaler-incident-receiver-for-ec2).

## March 07, 2023
### Feature Available
#### ZIA Integration with Browser Isolation
The ZIA Admin Portal is now completely integrated with Browser Isolation. Details like Zscaler Root Certificates, Isolation Profiles, and Isolation Banners can be managed by ZIA admins.
To learn more, see [What is Isolation?](/isolation/what-isolation)
[See image.](#Admin_Secure-Browsing_Browser-Isolation)
[![To view the new update, go to Administration > Secure Browsing > Browser Isolation.](/sites/default/files/downloads/isolation/profiles/zia-profiles/creating-zia-isolation-profile-isolation/ZIA_Admin_Secure-Browsing_Browser-Isolation_squircles.png)
]

## March 03, 2023
### Feature Available
#### Security Alerts
The new security alerts feature within the ZIA Admin Portal provides a comprehensive solution to view, manage, create, and adjust the alert rules. It provides high level statistics of each event type and threat severity. It is a centralized console to view and manage all alerts within the existing tenants. You can configure various events under Security Alerts. Additionally, you can create a webhook to deliver alerts for the configured events to third-party applications (e.g., ServiceNow, Splunk, etc.) for incident management.
[See image](#securityalerts-RN).
To learn more, see [About Security Alerts](/zia/about-security-alerts) and [About Webhooks](/zia/about-webhooks).
[]![The security alerts page provides details of the ongoing alerts and alert history and also the steps to configure an alert rule.](/sites/default/files/downloads/zia/security-alerts/about-alert-history/Alerts-SecurityAlerts-RN.png)

### Feature Available
#### Support for Amazon Web Services in Tenant Profiles
The Tenant Profiles feature supports Amazon Web Services. This allows you to provide access to specific account IDs.
[See image.](#amazon-web-services)
To learn more, see [Adding Tenant Profiles](/zia/adding-tenant-profiles).
[]![Screenshot of Add Tenant Profiles for Amazon Web Services. ](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Add-Tenant-Profile-Amazon-Web-Services.png)

## February 24, 2023
### Feature Available
#### Enhancements to Cloud Application Instances
The cloud application instances feature is extended to new cloud applications. You can create cloud application instances for the following cloud applications:
- Appspace
- Bitbucket
- GitHub
- Launchpad
- Quick Base
- Slack
- SourceForge
- Workday
- Zeplin
- Zoom
To learn more, see [About Cloud Application Instances](/zia/about-cloud-application-instances).

## February 17, 2023
### Feature Available
#### DLP EDM Index Tool Configuration Enhancement
You can configure the DLP EDM Index Tool with Amazon Web Services (AWS). Upon request, Zscaler support shares the Amazon Machine Image (AMI) ID and description for you to use during the configuration of the Index Tool with AWS.
To learn more, see [Configuring the Index Tool with Amazon Web Services](/zia/configuring-index-tool-amazon-web-services).

### Feature Available
#### Enhancement to the SaaS Security API Scan Schedules
The scan limit for Amazon S3 buckets, Google Cloud Platform buckets, and Azure blob containers has been expanded from 32 to 1000.
To enable increased scanning capacity, contact your Zscaler Account Team.
Additionally, you can search by column headings and select all objects in the tables for Amazon S3 buckets, Bitbucket repositories, Google Cloud Platform buckets, and Microsoft Azure blob containers.
[See image.](#S3BucketsTableAddScanSchedule)
To learn more, see [Configuring SaaS Security API Scan Schedules](/zia/configuring-saas-security-api-scan-schedules) and [Ranges & Limitations](/zia/ranges-limitations#Rules).
[]![Screenshot of the Amazon S3 Buckets table for the Add Scan Schedule window](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/configuring-saas-security-api-scan-schedules-draft-doc-44719/6.2/Amazon-S3-Buckets-Table.png)

### Feature Available
#### Logs for External Devices
The following enhancements are available for Web Insights Logs, Firewall Insights Logs, and NSS Feeds to support the logs for external devices:
Insights Logs
A new column and filter option, External Device ID, that associates a user’s device with the mobile device management (MDM) solution is available in the Firewall and Web Insights Logs.
[See image.](#external-device-id)
To learn more, see [Firewall Insights Logs: Filters](/zia/firewall-insights-logs-filters), [Firewall Insights Logs: Columns](/zia/firewall-insights-logs-columns), [Web Insights Logs: Filters](/zia/web-insights-logs-filters), and [Web Insights Logs: Columns](/zia/web-insights-logs-columns).
NSS Feeds
The fields `%s{external_devid}` and `%s{external_deviceid}` are available when adding an NSS feed to Web logs and Firewall logs, respectively.
To learn more, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs) and [NSS Feed Output Format: Firewall Logs](/zia/nss-feed-output-format-firewall-logs)
[![External Device ID in the Web & Firewall Insights Logs](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/logs/firewall-insights-logs-columns/ZIA-6.2-external-device-id.png)
]

### Feature Available
#### Support for Multiple SFTP Connections on Zscaler Incident Receiver
You can configure your Zscaler Incident Receiver VM to allow multiple simultaneous SFTP connections by updating the `storage_sftp_conn_max` parameter to a value from 1-16 (e.g., `storage_sftp_conn_max=2`). This setting can improve SFTP upload speed and can prevent the Zscaler Incident Receiver internal queue from becoming full.
To learn more, see [Configuring the Zscaler Incident Receiver](/zia/configuring-zscaler-incident-receiver#multiple-sftp-connections).

### Feature Available
#### Updates to SaaS Security API Control Policies
You can apply an email tag for the following applications under the Actions dropdown of DLP or Malware rules that are configured from the SaaS Security API Control policies:
- Gmail
- Microsoft Exchange
[See image.](#applying-email-labels-dlp)
To learn more, see [Configuring the SaaS Security API DLP Policy](/zia/configuring-saas-security-api-dlp-policy) and [Configuring the SaaS Security API Malware Detection Policy](/zia/configuring-saas-security-api-malware-detection-policy).
[]![The Add DLP Rule window allows you to add email labels to Gmail and Microsoft Exchange clients using the Apply Email Tags option under the Actions drop-down.](/sites/default/files/downloads/ZIA-SaaS-Security-API-Email-Tagging.png)

## January 30, 2023
### Feature Available
#### User Platform Mirroring in User Agent String
Cloud Browser Isolation mirrors the client's device platform as part of the isolated browser's user agent function, so that web pages accessed in isolation respond accordingly. The web pages receiving HTTP requests from the isolation browser can look at the platform portion of the user agent string, and serve the platform-appropriate content. For example, if a user attempts to download a file via an isolated browser, the file type served will be whatever the platform deems appropriate.
To learn more, see [Transferring and Viewing Files in Cloud Browser Isolation](/isolation/transferring-and-viewing-files-cloud-browser-isolation).

### Feature Available
#### Zoom In/Out Settings for Isolation
You can now zoom in and out of any web page while in isolation. The isolation function of zoom is the same as a non-isolated browser, so you can use the CTRL +/- keys for Windows devices or Command =/0 for Linux devices. You can also use the Zoom options in the View menu of your native browser.
To learn more, see [User Experience Modes in Cloud Browser Isolation](/isolation/user-experience-modes-cloud-browser-isolation).

## January 27, 2023
### Feature Available
#### Support for MIP Labels in SaaS Security API DLP Policy
For file sharing applications, you can now configure MIP labels from the SaaS Security API Control policy, in the Add DLP Rule window (Policy > SaaS Security API > SaaS Security API Control). Choose from the list of OneDrive and SharePoint tenants to see this action.
[See image.](#apply-mip-label-saas-security-api-dlp)
This action is only applicable for Microsoft Excel, Microsoft Word, and PDF file types.
To learn more, refer to the [Help Browser](/zia/using-zscaler-help-browser) within the Admin Portal.
[]![The Apply MIP Label action enables you to select the MIP Label to apply the rule to the tenant.](/sites/default/files/downloads/zia/policies/ssl-inspection/configuring-ssl-inspection-policy/ZIA-Apply-MIP-Labels-CASB9.0-DLP.png)

## January 20, 2023
### Feature Available
#### Enhancements to Virtual Service Edges
ZIA Virtual Service Edge supports Microsoft Hyper-V Hypervisor. You can create Virtual Service Edge virtual machines (VMs) in Hyper-V and configure a cluster to load balance traffic across them. The Hyper-V VM files can be downloaded from the Virtual Service Edges page (Administration > Virtual Service Edges).
[See image.](#hyper-v-vm)
To learn more, see [Configuring Virtual Service Edge for Microsoft Hyper-V](/zia/configuring-virtual-service-edge-microsoft-hyper-v).
[]![Screenshot of Virtual Service Page with Download Hyper-V VM File](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2022/ZIA-Virtual-Service-Edges-Hyper-V.png)

### Feature Available
#### Logs for Client Source Port
Logs for client source port include the following enhancements to the ZIA Admin Portal:
Web Insights Logs
A new filter and column, Client Source Port, is added to the Web Insights Logs.
[See image.](#source-port)
To learn more, see [Web Insights Logs: Filters](/zia/web-insights-logs-filters) and [Web Insights Logs: Columns](/zia/web-insights-logs-columns).
NSS Feeds
The field `%d{clt_sport}` is now available when adding an NSS feed for web logs.
To learn more, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs).
[]![Client Source Port field in the Web Insights Logs](/sites/default/files/downloads/ZIA-6.2r-source-port.png)

### Feature Available
#### Support for Admin Audit Log Type
A new log type, Admin Audit, is added to the NSS Feeds and Cloud NSS Feeds. This log type provides support for the following admin audit log reports:
- Branch Connector Portal Audit Log
- Client Connector Portal Audit Log
- ZDX Portal Audit Log
- ZIA Portal Audit Log
[See image.](#admin-audit-log-type)
To learn more, see [Adding NSS Feeds for Admin Audit Logs](/zia/adding-nss-feeds-admin-audit-logs) and [Adding Cloud NSS Feeds for Admin Audit Logs](/zia/adding-cloud-nss-feeds-admin-audit-logs).
[![Screenshot of Admin Audit log type in the Adding NSS Feeds page](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/nss/nss-feeds/adding-nss-feeds/adding-nss-feeds-admin-audit-logs/zia-adding-nss-feeds-admin-audit-release-note-image.png)
]
