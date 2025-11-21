# Release Upgrade Summary (2025)
Source: https://help.zscaler.com/zia/release-upgrade-summary-2025

This article provides a summary of all new features and enhancements per Zscaler cloud for Zscaler Internet Access (ZIA). Zscaler will email a notification to your organization's registered support contacts approximately one week before your cloud is upgraded. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com).

**Clouds:** zscaler.net, zscalerone.net, zscalertwo.net, zscalerthree.net, zscloud.net, zscalerbeta.net
The following service updates were deployed to zscaler.net on

## November 18, 2025
### Feature in Limited Availability
#### Traffic Capture for NDR
The Zscaler service can capture traffic in multiple ways:
- Traffic Capture Essentials: Capture traffic as PCAP files with supported actions in ZIA policies when traffic matches policy criteria.
- Traffic Capture for Network Detection and Response (NDR): Capture traffic as PCAPNG files based on criteria specified by the Traffic Capture policy.
Traffic Capture for NDR introduces a standalone Traffic Capture policy page (Policy > Traffic Capture) that enables granular control of Traffic Capture triggers, sampling, and how much traffic is collected per captured connection.
[See image.](#traffic-capture-policy-page)
Information in Traffic Capture for NDR data can be obfuscated on the Traffic Capture Settings page (Administration > Traffic Capture).
[See image.](#traffic-capture-obfuscation)
To access Traffic Capture Essentials and Traffic Capture for NDR, contact your Zscaler Account team.
All Zscaler Traffic Capture methods are enabled and disabled on the Traffic Capture Settings page (Administration > Traffic Capture). Connection to your organization's Amazon S3 bucket is also configured on the Traffic Capture Settings page. To learn more, see [About Traffic Capture Settings](/zia/about-traffic-capture).
To learn more about the Traffic Capture policy, see [About Traffic Capture Policy](/zia/about-traffic-capture-policy).
Update to Cloud Service API
The cloud service API includes the following new endpoints to create, update, and delete Traffic Capture policy rules as well as retrieve information for all or specific rules. In addition, they allow you to retrieve the rule count, rule order information, and rule label associations.
- `GET /trafficCaptureRules`
- `POST /trafficCaptureRules`
- `GET /trafficCaptureRules/{ruleId}`
- `PUT /trafficCaptureRules/{ruleId}`
- `DELETE /trafficCaptureRules/{ruleId}`
- `GET /trafficCaptureRules/count`
- `GET /trafficCaptureRules/order`
- `GET /trafficCaptureRules/ruleLabels`
To learn more, see the [API Reference](/zia/zia-api/api-developer-reference-guide/reference-guide).
[]![The Traffic Capture policy page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-about-traffic-capture-policy.png)
[]![Obfuscate User Name and Device information from captured traffic on the Traffic Capture Settings page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-traffic-capture-obfuscation.png)

## November 14, 2025
### Feature Available
#### Enhancement to Extranet Application Support
Extranet Application Support can be configured bidirectionally, allowing partners to access your organization's resources securely.
To access Extranet Application Support, contact your Zscaler Account team.
As part of this enhancement:
-
[Custom IP pools](/zia/adding-ip-pool) can be configured for Extranet Application Support.
[See image.](#add-ip-pool)
- [Static IP addresses](/zia/about-static-ip), [GRE tunnels](/zia/about-gre-tunnels), and [sublocations](/zia/understanding-sublocations) are configurable for extranet locations.
- [Firewall Control](/zia/about-firewall-filtering) is automatically enabled for extranet locations.
- [IPS Control](/zia/about-ips-control) is available for extranet locations.
-
Three default policy rules are added to the [Forwarding Control policy](/zia/about-forwarding-policies) when Extranet Application Support is enabled.
[See image.](#default-forwarding-control-policies)
-
One predefined policy rule is added to the [DNS Control policy](/zia/about-dns-control) when Extranet Application Support is enabled.
[See image.](#default-dns-control-policy)
To learn more, see [Understanding Extranet Application Support](/zia/understanding-extranet-application-support).
[]![The Add IP pool window on the IP Pool page](/sites/default/files/downloads/zia/policies/forwarding-control/dedicated-ip/zscaler-managed-dedicated-ip/geolocalization-ip/understanding-geolocalization-ip/ZIA-add-ip-pool.png)
[]![Allow Extranet DNS Traffic, Extranet Traffic to ZPA. and Stray Extranet Traffic from ZPA default Forwarding Control policy rules](/sites/default/files/downloads/zia/policies/forwarding-control/dedicated-ip/zscaler-managed-dedicated-ip/geolocalization-ip/understanding-geolocalization-ip/ZIA-forwarding-control-extranet-defaults.png)
[]![ZPA Resolver for Extranet Locations default DNS Control policy rule](/sites/default/files/downloads/zia/policies/forwarding-control/dedicated-ip/zscaler-managed-dedicated-ip/geolocalization-ip/understanding-geolocalization-ip/ZIA-dns-control-extranet-default.png)

## November 11, 2025
### Feature Available
#### Apply MIP Label as Manual Remediation Action in SaaS Security Assets
For file sharing applications OneDrive and SharePoint, you can apply the MIP label as a manual remediation action from the SaaS Security Assets with Incidents page (Analytics > SaaS Security > Assets > Assets with Incidents).
[See image.](#apply_mip_tag_img)
To learn more, see [Understanding the Assets Report: Assets with Incidents](/zia/understanding-assets-report-assets-with-incidents) and [Understanding SaaS Security API Supported Capabilities](/zia/understanding-saas-security-apis).
![Manual Remediation Apply MIP Tag in the Assets with Incidents page. ](/sites/default/files/downloads/apply_mip_label_rn.png)
[]

## November 10, 2025
### Feature Available
#### Additional Logging of Users Performing Actions on File
You can identify and report not only the owner of the file, but also the user who last modified or shared a file that caused a DLP violation, in the ZIA Admin Portal. As part of this feature, the following enhancements are available for Insights Logs and NSS Feeds:
Insights Logs
The following filters and columns are available on the SaaS Security Insights and SaaS Assets With Incidents page:
- Filters: Last Modified User and Last Shared User
- Columns: Last Modified User, Last Shared User, and Last Shared On
[See image.](#saas_insights_rn)
To learn more, see [About the SaaS Security Insights Logs Page](/zia/about-saas-security-insights-logs) and [Understanding the Assets Report: Assets with Incidents](/zia/understanding-assets-report-assets-with-incidents).
NSS Feeds
You can add the following fields to the SaaS Security logs Feed Output Format when configuring NSS or Cloud NSS feeds for file applications. These fields provide information on the user who last modified the file, shared the file, and the timestamp when the file was shared, which triggered DLP violations:
- `%s{last_edit_user}`
- `%s{last_share_user}`
- `%s{last_shared_on}`
To learn more, see [NSS Feed Output Format: SaaS Security Logs](/zia/nss-feed-output-format-saas-security-logs).
![Filters, Last Modified User and Last Shared User in the SaaS Security Insights Logs Page ](/sites/default/files/downloads/zia/dashboard-analytics/reports/viewing-post-quantum-cryptography-visibility-report/Saas_Insights_filters.png)
![The SaaS Assets With Incidents page showing the columns for identifying the user who caused a DLP violation.](/sites/default/files/downloads/assests_filters.png)
[]

## November 03, 2025
### Feature Available
#### Enhancement to Custom Views in 3rd-Party App Governance
When creating and saving a custom view in 3rd-Party App Governance, you can update the saved view to include your current tenant selection on the global platform filters.
[See image.](#Custom-View-Confirmation-Window)
To learn more, see [Custom Views](/zia/custom-views).
[]![Confirmation Window to update custom view with global filters](/sites/default/files/downloads/zia/apptotal/getting-started/connecting-your-platforms/adding-outbound-integrations/CustomView_ConfirmationMessage.png)

## October 31, 2025
### Feature Available
#### Creative Commons Search Results
Zscaler supports Creative Commons (CC) search for certain search engines (i.e., Bing, Google, and Yahoo). This allows you to see only search results that are licensed under CC. The Enable Creative Commons Search Results option is added to the Policy > URL & Cloud App Control > Advanced Policy Settings page as part of this feature.
This option is disabled by default.
[See image.](#adv-policy-settings-CC)
To learn more, see [Configuring Advanced Policy Settings](/zia/configuring-advanced-policy-settings).
[]![ZIA Advanced Policy Settings Page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-Advanced-Policy-Settings-Creative-Commons-Search-Results-RN.png)

### Feature Available
#### Zscaler Client Connector EUNs for Firewall, DNS, and IPS Policies
Beginning with Zscaler Client Connector version 4.8 for Windows, ZIA Firewall policies—including Firewall Filtering, DNS Control, and IPS Control—support end user notifications (EUNs) via Zscaler Client Connector. When configuring these policy rules, you can select to show a notification to users and select the notification message that must appear when the rule is triggered. This feature is available on Windows devices running Zscaler Client Connector version 4.8 or later over Z-Tunnel 2.0.
[See image.](#enable-custom-eun-firewall-policy)
To learn more, see [Configuring the Firewall Filtering Policy](/zia/configuring-firewall-filtering-policy), [Configuring the DNS Control Policy](/zia/configuring-dns-control-policy), and [Configuring the IPS Control Policy](/zia/configuring-ips-control-policy).
You can customize the EUNs for these policy rules under Administration > End User Notifications > Client Connector. You can modify the default notification message and additionally create custom messages to allow the selection of different notification messages for individual policy rules.
[See image.](#custom-eun-message-firewall-policy)
To learn more, see [Configuring EUNs for Firewall Filtering](/zia/configuring-euns-firewall-filtering), [Configuring EUNs for DNS Control](/zia/configuring-euns-dns-control), [Configuring EUNs for IPS Control](/zia/configuring-euns-ips-control).
[]![Enabling Zscaler Client Connector end user notification and selecting notification message](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/firewall-policies-client-connector-eun.png)
[]![Adding custom notification message for Firewall EUN](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/firewall-zscaler-client-connector-eun-custom-message.png)

## October 27, 2025
### Feature in Limited Availability
#### Support for Sublocation Scopes
You can define scope types and values to map the workload traffic to a sublocation. Defining scopes allows you to apply granular ZIA and Cloud Connector security policies to the workload traffic from that sublocation. You can configure scopes only for Workload traffic type sublocations whose parent locations are associated with Amazon Web Services (AWS) Cloud Connector groups.
As part of this feature, the following fields are added to the Administration > Location Management > Locations > Add Sublocation window:
- Scope
- Account
- Namespace
- VPC
- VPC Endpoint
[See image.](#RN-scope-field)
To learn more, see [Viewing Sublocations](/zia/viewing-sublocations), [Configuring Sublocations](/zia/configuring-sublocations), and [Using Sublocation Scopes to Group Cloud Connector Workloads](/cloud-branch-connector/using-sublocation-scopes-group-cloud-connector-workloads-amazon-web)
Update to Cloud Service API
The `Location` and `LocationLite` models used in `/locations` endpoints within the cloud service API include the following new attributes to support these functionalities via API:
- `subLocScopeEnabled`
- `subLocScope`
- `subLocScopeValues`
- `subLocAccIds`
To learn more, see the [API Reference](/zia/zia-api/api-developer-reference-guide/reference-guide).
![The Scope field and the supported scope types for a sublocation on the Add Sublocation page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-RN-configuring-sublocations-scope-types-vpc.png)
[]

## October 24, 2025
### Feature Available
#### JWT Authentication
JSON Web Token (JWT) authentication is available for Zscaler Cloud & Branch Connector workloads. JWT authentication is enabled when [configuring locations](/zia/configuring-locations).
[See image.](#enable-jwt-auth)
JWT authentication is not supported for the Extranet and IoT Traffic location types.
You can configure JWT authentication exemptions on the [Advanced Settings page](/zia/configuring-advanced-settings).
[See image.](#jwt-auth-exemptions)
Token validators for JWT authentication are [configured in the ZIdentity Admin Portal](/tech-pubs-drafts/about-token-validators).
To learn more, see [Understanding JWT Authentication](/tech-pubs-drafts/understanding-jwt-authentication-draft-doc-56628).
[]![The option to enable JWT authentication for a location](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-enable-jwt-auth-location.png)
[]![JWT Authentication Exemptions on the Advanced Settings page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-jwt-authentication-exemptions.png)

### Feature Available
#### JWT Authentication Support for Workloads on Management Portal for Partners
The ZIA Admin Portal supports a new method, JWT authentication, to authenticate workloads from Cloud & Branch Connector.
In the Management Portal for Partners, you can enable this feature in ZIA for your tenants by using the JWT Auth for Workload field on the Tenant Details page (Tenant > Tenant Details page > Special Settings). To enable this for your tenants, contact the Zscaler Support team.
[See image.](#jwt-auth-for-workload)
[]![JWT Auth for Workload field in Tenant's Special Settings.](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/viewing-tenant-details/jwt-auth-for-workload-mpp.png)
To learn more, see [Viewing Tenant Details](/zia/viewing-tenant-details).

### Feature Available
#### Support for Enhanced US Driver's License Dictionary and Sub-Dictionaries
The Zscaler service supports the Enhanced Driver's License (United States) predefined Data Loss Prevention (DLP) dictionary. The parent dictionary contains predefined sub-dictionaries for all 50 U.S. states, plus the District of Columbia, and each sub-dictionary can be individually referenced in your DLP engines.
On the DLP Dictionaries & Engines page (Administration > DLP Dictionaries & Engines), you can expand the Enhanced Driver's License (United States) to see each of the state sub-dictionaries.
[See image.](#DLP-Enhanced-USDL-rn)
You can then configure each of the individual state sub-dictionaries to set the Confidence Score Threshold, Proximity Length, and any Custom High Confidence Phrases.
[See image.](#DLP-Enhanced-USDL-Alabama-rn)
- The Enhanced Driver's License (United States) dictionary is not supported for Endpoint DLP.
- The legacy Driver's License (United States) dictionary has been replaced, but not deprecated, by the Enhanced Driver's License (United States) predefined dictionary.
To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).
[]![DLP Parent Driver's License (United States) Dictionary with State Sub-Dictionaries on the DLP Dictionaries & Engines Page in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-Enhanced-USDL-Parent-RN.png)
[]![Editing the Alabama Driver's License Sub-Dictionary](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-Enhanced-USDL-Alabama-RN.png)

## October 17, 2025
### Feature Available
#### Updates to SaaS Security Endpoints
You can retrieve the SaaS Security Scan Configuration information and the validation status of a SaaS application tenant using the following endpoints:
- `GET /casbTenant/scanInfo`
- `GET /casbTenant/validate/status/{tenantId}`
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection is also updated to include new and updated resources.
To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

## October 15, 2025
### Feature Available
#### Automatic Session Restore for Isolation
Isolated sessions now automatically restore their web pages if they time out on a user's device. If a session is idle for longer than the timeout of 10 minutes, the isolated page automatically refreshes itself, and the user does not have to sign in again. When this action occurs, the banner notification announcing the start of isolation is disabled. This feature is different than Persistent State, which is enabled per isolation profile to carry over data from an expired session to a new session.
To learn more, see [Using Persistent State for Isolation](https://help.zscaler.com/isolation/using-persistent-state-isolation).

### Feature in Limited Availability
#### Original URL of Website Name in Isolation
When users enter an isolated session, they will now see the original URL of the website they are on instead of the isolation web page URL. This provides users with a more native browser look-and-feel vs the container view of being isolated. The existing tools from [the Isolation bar](https://help.zscaler.com/isolation/using-isolation-bar-native-browser-experience) are still viewable and accessible unless [Native Browser Mode](https://help.zscaler.com/isolation/user-experience-modes-isolation) is enabled.
To learn more, see [User Experience Modes in Isolation](https://help.zscaler.com/isolation/user-experience-modes-isolation).

## October 06, 2025
### Feature Available
#### New AI/ML Cloud Applications
New cloud applications are added to the cloud application categories. You can download the list of newly added cloud applications to the respective categories: [Download](https://help.zscaler.com/sites/default/files/downloads/zia/documentation-knowledgebase/policies/cloud-apps/cloud-app-control-policies/cloud-app-categories/New_Cloud_Apps_Sep_2025.xlsx)
The risk index and risk attribute values for these new applications are visible only after they are available on all the clouds.

## September 26, 2025
### Feature Available
#### Document Classification and Logging
AI or machine language classification is extended to support around 200 new document types across 10 common document categories.
As part of this extended support, Insights Logs and the Nanolog Streaming Service (NSS) are enhanced to provide enriched auto-classification of documents that are uploaded or downloaded during transactions.
The following enhancements are available in the ZIA Admin Portal:
Updates to Insights Logs
A new filter and column, Subdocument Type, is added to the Web Insights Logs and SaaS Security Insights Logs pages to capture, categorize, and log document subtypes related to administrative documents, invoices, expense reports, and more.
[See image.](#insights_logs)
To learn more, see [Web Insights Logs: Filters](/zia/web-insights-logs-filters), [Web Insights Logs: Columns](/zia/web-insights-logs-columns), and [About SaaS Security Insights Logs](/zia/about-saas-security-insights-logs).
Updates to NSS Feeds
The field `%s{upload_doc_sub_type}` can be added to the Feed Output Format when configuring an NSS or Cloud NSS feed for web logs. Additionally, the field `%s{upload_doc_subtype}` is available for SaaS Security feeds configured for file applications (e.g., Box). Both fields log the subtype (e.g., Financial Statements: Income Statements (Profit and Loss Statements)) of uploaded or downloaded documents.
To learn more, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs)​​​​​​ and [NSS Feed Output Format: SaaS Security Logs](/zia/nss-feed-output-format-saas-security-logs).
![Subdocument Type filter is available on the SaaS Security Insights Logs and Web Insights Logs Pages](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/about-inventory-draft-doc-57038/Sub_document_type_RN.png)
[]

### Feature Available
#### Enhancement to SafeSearch
SafeSearch allows granular control of applications. This allows you to apply SafeSearch to specific applications. As part of this change, on the Advanced Policy Settings page (Policies > URL & Cloud App Control > Advanced Policy Settings), the SafeSearch Applications drop-down appears when you enable the Enforce SafeSearch option, which lists applications.
[See image.](#safesearch-apps)
To learn more, see [Configuring Advanced Policy Settings](/zia/configuring-advanced-policy-settings).
[]![ZIA Advanced Policy Settings](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-Advanced-Policy-Settings-SafeSearch-Applications-RN.jpg)
Enhancement to the URL & Cloud App Control Policy Settings Endpoint
A new field `safeSearchApps` is available for the `AdvancedUrlFilteringCloudAppOptions` model, referenced in the `/advancedUrlFilterAndCloudAppSettings `endpoint.
To learn more, go to `AdvancedUrlFilteringCloudAppOptions` from [URL & Cloud App Control Policy Settings](/zia/url-cloud-app-control-policy-settings).

### Feature Available
#### File Type Support for File Type Control & DLP
The File Type Control and Data Loss Prevention (DLP) policies support the following file types in the Other category:
- UTF-8 BOM
- UTF-16 LE
- UTF-16 BE
The file types are available when creating the following policies:
- [File Type Control](#file-type-control-utf-1530841)
- [DLP (Rule without content inspection)](#add-dlp-rule-utf-1530841)
To learn more, see [About File Type Control](/zia/about-file-type-control) and [About Data Loss Prevention](/zia/about-data-loss-prevention).
[]![Upload UTF file types in the Other category in the Add File Type Control Rule window](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/utf-ftc.png)
[]![Add UTF file types to DLP Rules with no content matching](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/dlp-no-matching-utf.png)

### Feature Available
#### New Network Applications in Firewall Control
Zscaler includes support for identifying several new network applications using deep packet inspection and controlling the network application traffic using Firewall Filtering rules. These network applications are listed on the Network Applications page (Administration > Network Applications) and are available to be configured in Firewall Filtering rules (Policy > Firewall Control > Firewall Filtering Policy).
[List of New Network Applications](#new-network-apps-list)
To learn more, see [About Network Applications](/zia/about-network-applications) and [Configuring the Firewall Filtering Policy](/zia/configuring-firewall-filtering-policy).
- []Signal
- HTTP/3
- Proton VPN
- ngrok
- Discord
- Ammyy Admin
- libp2p
- Foureverproxy (4everproxy)
- AnchorFree
- Evasive Protocol
- iTop VPN
- SoftEther VPN
- Wire VPN

### Feature Available
#### Shadow IT Report Enhancements
You can view information about the number of transactions per application based on their status (blocked or allowed) in the Cloud Applications table of the Shadow IT Report.
A new column, No. of Transactions, is added to the Cloud Applications table.
[See image.](#shadow_it_report_rn)
To learn more, see [About the Shadow IT Report](/zia/about-shadow-it-report).
![The Shadow IT Report showing all the widgets and cloud applications table](/sites/default/files/downloads/zia/dashboard-analytics/reports/about-shadow-it-report/No_Transactions_Shadow_It_Report.png)
[]

### Feature Available
#### Support for Adaptive Access Control
Adaptive Access Control dynamically manages access based on real-time assessments of risk and trust by continuously evaluating contextual signals, user behavior, device health, location, and other factors to determine whether to allow or block access to websites or apps at any given moment. You can configure URL Filtering and Cloud App Control policies using adaptive access profiles.
[See image.](#adaptive-profile-img-zia)
This feature is currently not functional in the ZIA Admin Portal and is only supported in Experience Center. To subscribe to [Experience Center](/unified/upgrading-zscaler-experience-center), contact your Zscaler Account team.
To learn more, see [Adding Rules to the Cloud App Control Policy](/zia/adding-rules-cloud-app-control-policy) and [Configuring the URL Filtering Policy](/zia/configuring-url-filtering-policy).
Logs for Adaptive Access Profile
As part of this update, a filter and column, Adaptive Access Profile, is added to Web Insights Logs.
[See image.](#aae_profile)
To learn more, see [Web Insights Logs: Columns](/zia/web-insights-logs-columns) and [Web Insights Logs: Filters](/zia/web-insights-logs-filters).
[]![Add URL Filtering Rule Window with Adaptive Access Profile Field](/sites/default/files/downloads/business-insights/authentication-administration/saml-admins/configuring-saml-admins-business-insights/ZIA-6.2r-Adaptive-Access-in-Policy.png)
![Select Adaptive Access Profile from the Web Insights Logs Filters field.](/sites/default/files/downloads/release-notes-drafts/Adaptive%20Access%20Profile.png)
[]

### Feature Available
#### Support for Custom File Types in DLP and File Type Control Policies
You can create custom file types and use them when creating Data Loss Prevention (DLP) and File Type Control policies. You can then filter and view logs for these custom file types in Web Insights Logs and the Nanolog Streaming Service (NSS).
[See image.](#add-custom-file-type-1529772)
As part of this enhancement, the Download User-Defined File Type and Upload User-Defined File Type filters and columns are added to the Web Insights Logs.
[See Image.](#filters_logs_rn)
To learn more, see:
- [Configuring Custom File Types](/zia/configuring-custom-file-types)
- [Configuring the File Type Control Policy](/zia/configuring-file-type-control-policy)
- [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled)
- [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection)
- [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection)
- [Web Insights Logs: Columns](/zia/web-insights-logs-columns)
- [Web Insights Logs: Filters](/zia/web-insights-logs-filters)
Additionally, filters for Download User-Defined File Type and Upload User-Defined File Type are added to NSS and Cloud NSS feeds for web logs as well as Microsoft Cloud App Security (MCAS) NSS feeds. You can use these filters to limit the logs sent to your security information and event management (SIEM) system based on the custom type of files that were downloaded or uploaded during the transaction.
[See image.](#img-nss-filters-1529772)
To learn more, see [Adding NSS Feeds for Web Logs](/zia/adding-nss-feeds-web-logs), [Adding Cloud NSS Feeds for Web Logs](/zia/adding-cloud-nss-feeds-web-logs), and [Adding MCAS NSS Feeds](/zia/adding-mcas-nss-feeds).
Update to Cloud Service API
The cloud service API includes the following new endpoints to create, update, and delete custom file types, retrieve information about custom file types and the count of custom file types, and retrieve information about all file types that can be used as rule conditions in DLP and File Type Control policies.
- `GET /fileTypeCategories`
- `GET /customFileTypes`
- `POST /customFileTypes`
- `PUT /customFileTypes`
- `GET /customFileTypes/{id}`
- `DELETE /customFileTypes/{id}`
- `GET /customFileTypes/count`
In addition, the `fileTypes` attribute used in `/webDlpRules` and `/fileTypeRules` endpoints is replaced with a new `fileTypeCategories` attribute to specify both predefined and custom file types along with their ID, name, and parent file category. Zscaler recommends updating your API configurations to use the new attribute. The `ZmanageNssFeed` model used in the `/nssFeeds` endpoints additionally includes two new attributes, namely `customDownloadFiletype` and `customUploadFiletype`, to filter logs based on the custom file types downloaded and uploaded during the transaction, respectively.
To learn more, see the [API Reference](/zia/zia-api/api-developer-reference-guide/reference-guide).
[]![Create a custom file type in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/add-custom-file-type.png)
[]![Download and Upload User-Defined File Type filters on the NSS feed configuration page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/nss-filters-download-upload-user-defined-file-type.png)
![Upload and Download User-Defined File Types filters in the Web Insights Logs](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/configuring-custom-file-types-doc-56905/File_type_extension.png)
[]

### Feature Available
#### Support for Custom File Types in File Type Policies and DLP
The File Type Control and Data Loss Prevention (DLP) policies now support custom file types with extension-based detection.
On the Management Portal for Partners, partner tenants can see a new field, Custom File Type Limit, in their Technical Information section. The Custom File Type Limit indicates the number of custom file types that can be created for File Type Control and DLP policies in the ZIA Admin Portal.
[See image.](#custom-file-type)
To learn more, see [About File Type Control](/zia/about-file-type-control), [Configuring the File Type Control Policy](/zia/configuring-file-type-control-policy), and [Viewing Tenant Details](/zia/viewing-tenant-details).
[]![Custom File Type Limit in Technical Details](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/viewing-tenant-details/custom-file-type-limit-mpp.png)

### Feature Available
#### Support for Quarantine File to Desired Location
The SaaS Security Data at Rest Scanning DLP and Malware policies support specifying the location to quarantine files for the file sharing applications Google Drive, Microsoft OneDrive, and Microsoft SharePoint.
SaaS Application Tenant Onboarding
Onboarding a SaaS application tenant with Data at Rest Scanning DLP and Malware policies includes the functionality to specify your quarantine location for policy violating files. Provide a quarantine location and a DLP admin mail ID while onboarding the SaaS tenant. Also note, the DLP admin should have read/write access to the quarantine folder path.
[See image.](#onboardquar)
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
Quarantine Files That Violate DLP Policy in a Desired Location
On the SaaS Security Data at Rest Scanning Edit DLP / Malware policy page, select the Admin Quarantine action to isolate sensitive files in the location of your choice.
[See image.](#quarantine-location)
To learn more, see [About Data at Rest Scanning DLP](/zia/about-data-rest-scanning-dlp), [Configuring the Data at Rest Scanning DLP Policy with Content Inspection](/zia/configuring-data-rest-scanning-dlp-policy-content-inspection), and [Configuring the Data at Rest Scanning DLP Policy without Content Inspection](/zia/configuring-data-rest-scanning-dlp-policy-without-content-inspection).
Remediation Actions in Assets with Incidents Page
The following options are added as part of remediation actions for file sharing applications Google Drive, Microsoft OneDrive, and Microsoft SharePoint on the Assets with Incidents page (Analytics > SaaS Security > Assets > Assets with Incidents):
- Admin Quarantine: To quarantine sensitive files to a specific file location
- Restore Admin Quarantine: To restore a file that was previously quarantined to the admin-specified location.
[See image.](#admin_quarantine_assets_rn)
To learn more, see [Understanding the Assets Report: Assets with Incidents](/zia/understanding-assets-report-assets-with-incidents) and [Understanding SaaS Security API Supported Capabilities](/zia/understanding-saas-security-apis).
[]![The Admin Quarantine action on SaaS Security Data at Rest Scanning DLP Policy.](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/about-data-rest-scanning-dlp-draft-doc-57420/admin-quarantine-dlp.png)
[]![Specify the Quarantine Location step in ZIA SaaS Application Tenant Onboarding](/sites/default/files/downloads/zia/zia-api/api-developer-reference-guide/getting-started-zia-api/Quarantine_location.png)
![Remediation Action - Admin Quarantine option available in the Assets Page to isolate sensitive files in a location of your choice.](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/logs/web-insights-logs-columns/admin_quarantine_rn.png)
[]

## September 25, 2025
### Feature Available
#### Support for New SSPM Controls for Snowflake
The number of SaaS Security Posture Management (SSPM) controls for Snowflake in Advanced SSPM has been increased. Forty-six new SSPM controls are supported for Snowflake.

## September 24, 2025
### Feature Available
#### Logs for Post-Quantum Cryptography Visibility
Zscaler is proactively preparing for post-quantum cryptography (PQC) by evaluating quantum-safe algorithms, supporting hybrid encryption systems, and enabling scalable integration of quantum-resilient technologies across its cloud infrastructure. Zscaler collaborates globally with standardization bodies like NIST, provides customers with enablement tools, and ensures its platform is future-proofed for crypto-agility, facilitating a seamless transition to secure PQC solutions.
Enhancements to Insights Logs and the Nanolog Streaming Service (NSS) provide visibility into the PQC capabilities of TLS client- and server-side connections. You can filter and view ZIA web logs based on key exchange and digital signature algorithms.
As part of the update, the following changes are available in the ZIA Admin Portal:
Interactive Reports: Post-Quantum Cryptography Visibility
The Post-Quantum Cryptography Visibility Report (Analytics > Interactive Reports > Web Activity) provides insights into the most frequently used PQC Key Algorithms and SSL/TLS versions. It also displays the distribution of transactions, differentiating between traffic processed with PQC and non-PQC methods. To further investigate the types of PQC methods used, you can drill down to the Web Logs.
[See image.](#interactive_reports)
To learn more, see [About Interactive Reports](/zia/about-interactive-reports), [Understanding the Post-Quantum Cryptography Visibility Report](/zia/understanding-post-quantum-cryptography-visibility-report), and [Viewing the Post-Quantum Cryptography Visibility Report](/zia/viewing-post-quantum-cryptography-visibility-report).
Web Insights Data Types
The following data types are added to Web Insights:
- PQC vs. Classical Key Exchange
- Top PQC Key Exchange Algorithms
- Top Users with PQC Key Exchange
[See image.](#web_insights_data_types)
To learn more, see [Web Data Types and Filters](/zia/web-data-types-and-filters).
Web Insights Logs
The following filters and columns are added to Web Insights Logs:
- Client Digital Signature Proposal
- Client Key Exchange Proposal
- Client-Side Key Exchange Algorithm
- Server-Side Key Exchange Algorithm
- Client-Side Digital Signature Algorithm
- Server-Side Digital Signature Algorithm
[See image.](#web_logs_filters)
To learn more, see [Web Insights Logs: Columns](/zia/web-insights-logs-columns) and [Web Insights Logs: Filters](/zia/web-insights-logs-filters).
NSS Feeds for Web Logs
The following fields can be added to the Feed Output Format when configuring an NSS or Cloud NSS feed for web logs:
- `%d{client_tls_keyex_pqc_offers}`
- `%d{client_tls_keyex_non_pqc_offers}`
- `%d{client_tls_keyex_hybrid_offers}`
- `%d{client_tls_keyex_unknown_offers}`
- `%d{client_tls_sig_pqc_offers}`
- `%d{client_tls_sig_non_pqc_offers}`
- `%d{client_tls_sig_hybrid_offers}`
- `%d{client_tls_sig_unknown_offers}`
- `%s{client_tls_keyex_alg}`
- `%s{server_tls_keyex_alg}`
- `%s{client_tls_sig_alg}`
- `%s{server_tls_sig_alg}`
To learn more, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs).
![All PQC Related Data Types in the Web Insights Page.](/sites/default/files/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/inventory/analyzing-application-details/Web_insights_datatypes_rn.png)
[]
![The Interactive Reports showing the Post-Quantum Cryptography Visibility Charts allowing you to drill down to Web Logs page..](/sites/default/files/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/inventory/analyzing-application-details/interactive_reports.png)
[]
![New filters added to the Web Logs page for PQC visiblity.](/sites/default/files/downloads/zia/dashboard-analytics/reports/understanding-post-quantum-cryptography-pqc-report/web_insights_logs_rn.png)
[]

## September 19, 2025
### Feature Available
#### Async Location Download
For organizations that have thousands of locations or sublocations, the loading time on the Locations page and in any policy that references locations when selected might incur noticeable loading time to retrieve and display the full location list.
To learn more, see [About Locations](/zia/about-locations).

### Feature Available
#### Enhancement to the IP Destination Groups Endpoint
A new query parameter `override` is available for the `PUT /ipDestinationGroups/{ipGroupId}` endpoint. The `override` parameter is a Boolean that you can set to override IPs when required.
To learn more, go to `PUT /ipDestinationGroups/{ipGroupId}` from [Firewall Policies](/zia/firewall-policies).

### Feature Available
#### Gen AI Application Category in NSS Feeds for SaaS Security Logs
Gen AI is added as an application category in NSS and Cloud NSS feeds for SaaS Security Logs. When configuring a feed, you can select the Gen AI application category and available generative AI SaaS applications (e.g., ChatGPT) to stream the related logs from Zscaler to your security information and event management (SIEM) system. Additionally, you can edit the default Feed Output Format for the Gen AI-based feed to further define the data displayed in the SIEM output.
[See image.](#img-gen-ai-application-category)
To learn more, see [Adding NSS Feeds for SaaS Security Logs](/zia/adding-nss-feeds-saas-security-logs), [Adding Cloud NSS Feeds for SaaS Security Logs](/zia/adding-cloud-nss-feeds-saas-security-logs), and [NSS Feed Output Format: SaaS Security Logs](/zia/nss-feed-output-format-saas-security-logs).
[]![Gen AI application category in NSS feeds for SaaS Security logs](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/nss-saas-security-gen-ai-feed.png)

### Feature Available
#### Update to Cloud Nanolog Streaming Service (NSS) Endpoints
The Cloud Nanolog Streaming Service (NSS) endpoint category in the cloud service API includes a new endpoint, `GET /nssDownload/{nssId}`, that enables you to download the NSS virtual appliance information based on the specified NSS server ID.
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection is also updated to include new and updated resources.
To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

### Feature Available
#### Updates to Virtual Service Edge Endpoints
You can create, update, and delete a ZIA Virtual Service Edge and retrieve the Virtual Service Edge for an organization using the following endpoints:
- `GET /virtualZenNodes`
- `POST /virtualZenNodes`
- `GET /virtualZenNodes/{virtualZenNodeId}`
- `PUT /virtualZenNodes/{virtualZenNodeId}`
- `DELETE /virtualZenNodes/{virtualZenNodeId}`
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection is also updated to include new and updated resources.
To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

### Feature Available
#### Updates to Workload Groups Endpoints
You can add workload groups for an organization and update, delete, and retrieve the workload groups by specifying the ID using the following endpoints:
- `POST /workloadGroups`
- `GET /workloadGroups/{workloadGroupId}`
- `PUT /workloadGroups/{workloadGroupId}`
- `DELETE /workloadGroups/{workloadGroupId}`
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection is also updated to include new and updated resources.
To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

## September 15, 2025
### Feature Available
#### New Cloud Applications
New cloud applications are added to the cloud application categories. You can download the list of newly added cloud applications to the respective categories: [Download](/sites/default/files/downloads/zia/documentation-knowledgebase/policies/cloud-apps/cloud-app-control-policies/cloud-app-categories/New_Cloud_Apps_Aug_2025.xlsx)
The risk index and risk attribute values for these new applications are visible only after they are available on all the clouds.

## September 12, 2025
### Feature Available
#### Advanced SaaS Security Posture Management Support for Docusign
Docusign is supported as a SaaS application tenant and can be onboarded for Advanced SaaS Security Posture Management (SSPM) scans.
[See image.](#docu_icon)
When onboarding a Docusign tenant, you can enable Advanced SSPM scanning by selecting the SSPM Scan checkbox.
[See image.](#Docusign-sspm-onboarding)
The SSPM Scan checkbox is available only when you have Advanced SSPM enabled for your tenant.
To learn more, see [What Is Advanced Posture Management?](/zia/what-advanced-posture-management) and [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
[]![Docusign Onboarding Section showing the SSPM Scan Checkbox](/sites/default/files/downloads/zia/policies/saas-security/posture-management/posture-management-advanced/about-control-panel/Adavanced%20SSPM-Workday2.png)
[]![ZIA Supported SaaS Applications list with Docusign highlighted](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/Docusign%20apps%20list.png)

### Feature Available
#### SSL Inspection for IoT Devices
You can specify the type of IoT devices to perform or bypass SSL Inspection. Admins can create an SSL Inspection policy based on IoT AI/ML classifications to perform or bypass SSL Insepction.
This enhancement requires IoT enablement for your organization.
As part of this enhancement, the following changes appear in the ZIA Admin Portal:
-
Added IoT group to the Device Groups criterion in the SSL Inspection Policy page (Policy > SSL Inspection > SSL Inspection Policy).
[See image.](#iot-device-image)
-
Added the predefined rule, Unauthenticated Traffic Bypass for IoT Classifications, to the SSL Inspection Policy page.
[See image.](#predefined-rule-image)
To learn more, see [Configuring SSL Inspection Policy](/zia/configuring-ssl-inspection-policy) and [About SSL Inspection Policy](/zia/about-ssl-inspection-policy).
[]![ZIA SSL Inspection Policy Page with IoT Device Group ](/sites/default/files/downloads/IoT%20for%20SSL%20Inspection.png)
[]![ZIA SSL Inspection Policy Page with Predefined IoT Rule](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/tlsssl-inspection-zscaler-internet-access/Predefined%20Rule.png)

### Feature Available
#### Support for New SaaS Application Tenant
Microsoft Copilot is supported as a SaaS application tenant and can be onboarded for Advanced SaaS Security Posture Management (SSPM) scans.
[See image.](#copilot_icon)
When onboarding a Microsoft Copilot tenant, you can enable Advanced SSPM scanning by selecting the SSPM Scan checkbox.
[See image.](#copilot-sspm-onboarding)
The SSPM Scan checkbox is available only when you have Advanced SSPM enabled for your tenant.
To learn more, see [What Is Advanced Posture Management?](/zia/what-advanced-posture-management) and [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
[]![Docusign Onboarding Section showing the SSPM Scan Checkbox](/sites/default/files/downloads/zia/policies/saas-security/posture-management/posture-management-advanced/about-control-panel/Adavanced%20SSPM-Workday2.png)
[]![ZIA Supported SaaS Applications list with Docusign highlighted](/sites/default/files/downloads/Copilot%20apps%20list.png)

## September 09, 2025
### Feature Available
#### Strict Checking of Popular Date Formats in EDM
To obtain access to this feature, contact Zscaler Support.
You can configure Data Loss Prevention (DLP) Exact Data Match (EDM) to have strict checking against popular date formats.
This feature supports 6- to 8-digit date formats that contain hyphens (`-`) or periods (`.`) (i.e., `25-12-2025`, `25-12-25`, `25.12.2025`, and `25.12.25`).
To learn more, see [Creating an Exact Data Match Template](/zia/creating-exact-data-match-template#Date).

## September 08, 2025
### Feature Available
#### Support for Expandable Limit for Users, Groups, Locations, & Departments in Policies
The default limit of Users, Groups, Locations and Departments in policies has been increased to 32 from 4 and 8. This limit can be further expanded on a need basis. You can contact the Zscaler Sales or Zscaler Account team to further increase this limit, if required.
On the Management Portal for Partners, this limit helps you allow more users and groups to access a blocked site with the block action.
To learn more, see [About Policy Templates](/zia/about-policy-templates) and [Edit Policy Templates in the ZIA Admin Portal](/zia/edit-policy-templates-zia-admin-portal).

## September 05, 2025
### Feature Available
#### Source Countries for the URL Filtering Rules
You can select the countries from which traffic originates for the URL Filtering rules. This allows you to control the traffic originating from specific countries. As part of this change, the Source Countries field is added to the Add URL Filtering Rule window (Policies > URL & Cloud App Control > URL Filtering Policy > Add URL Filtering Rule).
[See image.](#source-country)
To learn more, see [Configuring the URL Filtering Policy](/zia/configuring-url-filtering-policy).
[]![Add URL Filtering Rule Window ](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-URL-Filtering-Policy-Page-With-Add-Icon-RN.png)

### Feature Available
#### Support for Expandable Limit for Users, Groups, Locations, & Departments per Rule
The limit of users, groups, departments, and locations for a rule is increased to 32 from 4 users, 8 groups, 8 departments, and 8 locations. You can contact Zscaler Support to increase this limit further as needed.
The following categories under the policy are supported:
- Bandwidth Control
- Secure Browsing
- URL & Cloud App Control
- Data Loss Prevention (DLP)
- Outbound Email Policy
- Endpoint Data Loss Prevention (DLP)
- Firewall Control
- FTP Control
- DNS Control
- IPS Control
- Forwarding Control
- Mobile App Store Control
- Sandbox
- SSL Inspection
- SaaS Security
To learn more, see [Adding a Custom Applications Rule for Cloud App Control](/zia/adding-custom-applications-rule-cloud-app-control), [Configuring URL Filtering Policy](/zia/configuring-url-filtering-policy), and [Configuring the Firewall Control Policy](/zia/configuring-firewall-filtering-policy).

## September 02, 2025
### Feature Available
#### Enhancements to App Panel and Control Panel
A Notes tab is added to the App Panel in 3rd-Party App Governance and the Control Panel in Advanced SaaS Security Posture Management (SSPM). This tab allows you to communicate with and leave notes for multiple other users. You can add notes to each app or control and also comment on notes that other users add.
[See image.](#Control-Panel-Notes-Tab)
To learn more, see [About the App Panel](/zia/about-app-panel) and [About the Control Panel](/zia/about-control-panel).
[]![Control Panel Notes Tab showing user notes](/sites/default/files/downloads/zia/policies/saas-security/posture-management/posture-management-advanced/about-saas-dashboard/Notes_Tab_RN.png)

## September 01, 2025
### Feature Available
#### New Endpoints for 3rd-Party App Governance
The 3rd-Party App Governance API adds the following new endpoints to perform bulk actions as well as retrieve scan results and lists of filters and controls from the Posture page in the 3rd-Party App Governance Admin Portal:
- `/posture/controls/status`
- `/posture/assets/status`
- `/posture/assets`
- `/posture/controls/filters`
- `/posture/controls`
To learn more about these endpoints, see the [Understanding ZIA APIs](/zia/understanding-zia-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).

## August 29, 2025
### Feature Available
#### Support for Cloud-to-Cloud Forwarding in DLP
You can now forward information about transactions that violate various Data Loss Prevention (DLP) incidents directly to your appliances you've defined in the ZIA Admin Portal by going to Administration > Data Loss Prevention and selecting Cloud-to-Cloud Forwarding.
[See image.](#c2c-forwarding-1526251)
Cloud-to-Cloud Incident Forwarding can be configured to different appliances such as the Google Cloud Platform, an EC2 instance on Amazon Web Services (AWS), or an Azure VM. Following configuration, you can select Cloud-to-Cloud Forwarding in the DLP Incident Receiver section of policy rules that you add or edit for Inline Web DLP, Data at Rest Scanning DLP, Outbound Email DLP, and Endpoint DLP. The following example shows the Cloud-to-Cloud Forwarding options for Inline DLP policy rules.
[See image.](#configure-c2c-1526251)
To learn more, see:
- [Configure DLP Cloud-to-Cloud Incident Forwarding](/zia/configure-dlp-cloud-cloud-incident-forwarding)
- [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection)
- [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection)
- [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled)
- [Configuring the Data at Rest Scanning DLP Policy with Content Inspection](/zia/configuring-data-rest-scanning-dlp-policy-content-inspection)
- [Configuring the Data at Rest Scanning DLP Policy without Content Inspection](/zia/configuring-data-rest-scanning-dlp-policy-without-content-inspection)
- [Configuring Outbound Email Policy Rules](/zia/configuring-outbound-email-policy-rules)
- [Configuring Endpoint DLP Policy Rules](/zia/configuring-endpoint-dlp-policy-rules)
Update to Cloud Service API
The cloud service API allows you to associate the newly supported Cloud-to-Cloud Incident Receivers with DLP policy rules using `/webDlpRules` and `/casbDlpRules` endpoints. To support this, new endpoints are added to retrieve information about the DLP Incident Receivers configured for Cloud-to-Cloud Incident Forwarding, retrieve the count of configured Incident Receivers, and validate whether specific cloud storage configurations of an Incident Receiver can be deleted. In addition, two existing attributes in `/webDlpRules` and `/casbDlpRules` endpoints are deprecated in favor of a new attribute.
- [New API Endpoints](#new-api-endpoints-cloud-to-cloud-incident-forwarding)
- [Deprecated API Attributes](#deprecated-api-attribute-dlp-incident-receiver)
The deprecated attributes are no longer supported, and the API calls using these attributes are not successful. To ensure continued API operation, you must immediately update your configurations to use the new attribute in the corresponding endpoints.
To learn more, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
- []`GET /cloudToCloudIR`
- `GET /cloudToCloudIR/{id}`
- `GET /cloudToCloudIR/lite`
- `GET /cloudToCloudIR/count`
- `GET /cloudToCloudIR/config/{id}/validateDelete`
[]Affected Models/EndpointsDeprecated AttributesNew AttributesImplemented Changes`WebDlpRule` and `WebDlpSubRule` models in `/webDlpRules` endpoints
- `zscalerIncidentReceiver`
- `icapServer`
`receiver`Previously, `icapServer` was used in combination with `zscalerIncidentReceiver` (Boolean) to specify the Zscaler Incident Receiver or ICAP server details for a rule. Currently, the `receiver` attribute specifies the DLP Incident Receiver for all three ncident Receiver types: Zscaler Incident Receiver, ICAP server, and Cloud-to-Cloud Incident Forwarding.`CASBDlpRule` model in `/casbDlpRules` endpoints
- `zscalerIncidentReceiver`
- `icapServer`
`receiver`Previously, `zscalerIncidentReceiver` and `icapServer` were used to specify the Zscaler Incident Receiver or an ICAP server respectively to associate with a rule. Currently, the `receiver` attribute specifies the DLP Incident Receiver for all three Incident Receiver types: Zscaler Incident Receiver, ICAP server, and Cloud-to-Cloud Incident Forwarding.
[]![Image]()
![Cloud-to-Cloud Forwarding page in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/c2c-incident-forwarding-page.png)
[]![Cloud-to-Cloud Incident Forwarding in SaaS Security DLP](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/c2c-dlp-policy.png)

## August 22, 2025
### Feature Available
#### Gen AI Security Report Enhancements
The Gen AI Security Report is improved, making it interactive and intuitive, with the following enhancements:
- Option to view the sanctioned and unsanctioned Gen AI application usage.
- Prompt Classification to categorize the prompts used in the Gen AI applications by users.
- Analyze More option to drill down and view details for Content Types, Prompt Classification, and Document Classification used, as well as department-level visibility.
[See Image.](#gen_ai_security_report_img)
To learn more, see [About the Gen AI Security Report](/zia/about-generative-ai-security-report).
Logs for Prompt Classification
A filter and column, Prompt Classification, is added to Web Insights Logs.
[See Image.](#prompt_class_img)
To learn more, see [Web Insights Logs: Columns](/zia/web-insights-logs-columns) and [Web Insights Logs: Filters](/zia/web-insights-logs-filters).
![Prompt Classification Filter and its categories in the Web Insights Logs page.](/sites/default/files/downloads/zia/dashboard-analytics/reports/about-generative-ai-security-report/Prompt_classification.png)
[]
![Gen AI Security Report with all the widgets.](/sites/default/files/downloads/zia/dashboard-analytics/reports/about-generative-ai-security-report/Gen_AI_security%20report_RN.png)
[]

### Feature Available
#### Improvements to the Zscaler Incident Receiver JSON Metadata File
To help improve incident management on the Zscaler Incident Receiver, the JSON file that contains Data Loss Prevention (DLP) policy scan metadata for Inline Web DLP policy violations (with Evaluate All Rules mode enabled) has been updated with the following fields:
- `otherMatchedRules`: This is an existing field that previously reported 8 rules, but now reports 16 rules.
- `severity`: This is a new field that reports the severity of the DLP policy violation for other matched rules.
- `actionTaken`: This is a new field that reports the action taken as a result of the DLP policy violation (i.e., Allowed, Blocked, etc.) for other matched rules.
To learn more and to download a sample JSON file, see [Configuring the Zscaler Incident Receiver for On-Premises VMs](/zia/configuring-zscaler-incident-receiver), [Configuring the Zscaler Incident Receiver for Amazon Web Services EC2 VMs](/zia/configuring-zscaler-incident-receiver-for-ec2), and [Configuring the Zscaler Incident Receiver for Azure VMs](/zia/configuring-zscaler-incident-receiver-azure-vms).

### Feature Available
#### Third-Party URL Category Lookup
Zscaler supports lookup for uncategorized URLs using a third-party database. You can control the lookup for such uncategorized URLs using the newly added Enable 3rd-Party URL Category Lookup option on the Advanced Policy Settings tab (Policy > URL & Cloud App Control).
[See image.](#3rd-party-database)
To learn more, see [Configuring Advanced Policy Settings](/zia/configuring-advanced-policy-settings).
[]![Advanced Policy Settings Page with Third-Party URL Category Lookup](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-Advanced-Policy-Settings-3rd-Party-URL-Category-Lookup-RN.jpg)

## August 19, 2025
### Feature Available
#### OpenOffice File Type Support for DLP
The Data Loss Prevention (DLP) policies support the OpenOffice Drawings (.odg, .otg) file type in the OpenOffice category:
- [DLP - Rule with Content Inspection](#open-office-ftc-1525596)
To learn more, see [About Data Loss Prevention](/zia/about-data-loss-prevention).
[]![Select Open Office Drawing file types to DLP Rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/open-office-with-content-inspection-1525596.png)

## August 15, 2025
### Feature Available
#### Search for Configuration Changes in Audit Logs
You can search for configuration changes on the Audit Logs page by selecting Changes** **from the search options.
[See image.](#audit-log-search-changes)
The configuration change search applies to JSON attribute values, not attribute names. Search strings must contain a minimum of 4 characters. Search results can be exported as a CSV file.
To learn more, see [About Audit Logs](/zia/about-audit-logs).
[]![The option to search for changes on the Audit Logs page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-audit-logs-search-changes.png)

### Feature Available
#### Updated Search for Firewall Filtering Rules
The following update is applicable only to tenants approved for an increased rule limit of up to 4,000 Firewall Filtering rules, based on qualified use cases.
On the Firewall Filtering Policy page (Policy > Firewall Control), the search is updated to include the following additional search categories based on various rule conditions:
- Source IP Addresses
- Destination IP Addresses
- Source IP Group
- Destination Group
- Network Application
- Network Services
- Destination IP Categories
[See image.](#new-search-filters-firewall-filtering-rules)
To learn more, [About Firewall Filtering](/zia/about-firewall-filtering).
Update to Cloud Service API
The cloud service API is also updated to include the following new request parameters in the `GET /firewallFilteringRules` endpoint to support these additional search functionalities via API:
- `srcIps`
- `destAddresses`
- `srcIpGroups`
- `destIpGroups`
- `nwApplication`
- `nwServices`
- `destIpCategories`
To learn more, see the [API Reference](/zia/zia-api/api-developer-reference-guide/reference-guide).
[]![Additional search filters for Firewall Filtering rules](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/new-search-filters-firewall-filtering-rules_0.png)

### Feature Available
#### Updates to End User Subscription Agreement (EUSA) Endpoints
The cloud service API includes the Activation endpoint category to extend programmatic access to retrieve the EUSA acceptance status using the following endpoints:
- `GET /eusaStatus/latest`
- `PUT /eusaStatus/{eusaStatusId}`
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection is also updated to include new and updated resources.
To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

## August 14, 2025
### Feature Available
#### SaaS Security DLP Policies Support Folder Level Changes
When a folder's permissions are modified or a folder is shared with a new collaborator, files previously in violation of the SaaS Security DLP policy rules in the folder are rescanned against those rules. This feature is presently being rolled out to Microsoft OneDrive and SharePoint applications.
- If the files in a folder remain unchanged, the system only rescans the files previously in violation of the SaaS Security DLP Policy rules when a folder share activity takes place.
- When a folder is shared with an AD (Active Directory) group in OneDrive and SharePoint, the folder share activity is not tracked or logged due to a SaaS limitation.
To learn more, see [About Data at Rest Scanning DLP](/zia/about-data-rest-scanning-dlp) and [Understanding SaaS Security API Supported Capabilities](/zia/understanding-data-rest-scanning-policy).

## August 13, 2025
### Feature Available
#### Logs for SSL Inspection Policy Rule Name
You can filter and view logs to learn which specific [SSL Inspection](/zia/about-ssl-inspection-policy) policy rules were applied to web transactions. You can use the logs to analyze and refine your policies, enabling you to improve SSL inspection rates and simplify troubleshooting of URL & Cloud App Control-related use cases.
As part of the update, the following changes are available in the ZIA Admin Portal:
Web Insights Logs
A filter and column, SSL Policy Name, is added to the Web Insights Logs.
[See image.](#ssl_policy_rn)
To learn more, see [Web Insights Logs: Filters](/zia/web-insights-logs-filters) and [Web Insights Logs: Columns](/zia/web-insights-logs-columns)
NSS Feeds
The field `%s{ssl_rulename}` can be added to the Feed Output Format when configuring an NSS or Cloud NSS feed for web logs.
To learn more, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs).
![The SSL Policy Name Filter in the Web Insights Logs Page.](/sites/default/files/downloads/SSL_Policy_Name.png)
[]

## August 08, 2025
### Feature Available
#### Multifile Support for Isolation in ZIA
Users can now upload multiple files simultaneously while in an isolated session. There is no minimum or maximum limit while uploading.
[See image.](#Multi-File-Upload)
To learn more, see [Transferring and Viewing Files in Isolation](https://help.zscaler.com/isolation/transferring-and-viewing-files-isolation).
[]![A view of the upload log while in Isolation.](/sites/default/files/downloads/isolation/end-user-isolation-experience/transferring-and-viewing-files-isolation/Multi-File-Upload_RNs.png)

### Feature Available
#### Support for Device Groups in Forwarding Control
In the Policy > Forwarding Control > Add Forwarding Rule window, under the General section, a new Device Groups criterion is added. This criterion allows you to select device groups based on the device platform to which the configured forwarding rule applies.
[See image.](#RN-device-groups-forwarding-control)
To learn more, see [Configuring Forwarding Policy](/zia/configuring-forwarding-policy).
![The Forwarding Control > Add Forwarding Rule window displaying the Device Groups criterion under the General Section](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-RN-forwarding-control-device-groups-criterion.png)
[]

### Feature in Limited Availability
#### Support for Step-Up Authentication
Step-up authentication is a security mechanism that ensures users can only access sensitive or high-risk resources after completing an additional level of identity verification. Conditional access is supported for step-up authentication in the ZIA Admin Portal when configuring URL Filtering and Cloud App Control policies for accessing websites and cloud apps with sensitive or regulated data.
Using step-up authentication, you can configure stronger authentication methods such as multi-factor authentication (MFA), one-time password (OTP), or validation through an authenticator app supported by your IdP. This provides an added layer of security, ensuring that users can access high-value or sensitive resources only after completing advanced authentication requirements.
[See image.](#conditinal-access-zia)
This feature is only supported for tenants who are subscribed to ZIdentity for end users and requires configuration of authentication levels within the ZIdentity Admin Portal prior to configuring a policy within the ZIA Admin Portal. To enable step-up authentication for your tenant, raise a provisioning support ticket.
To learn more, see [Understanding Step-Up Authentication](/zidentity/understanding-step-up-authentication), [Adding Rules to the Cloud App Control Policy](/zia/adding-rules-cloud-app-control-policy), and [Configuring the URL Filtering Policy](/zia/configuring-url-filtering-policy).
[]![Add URL Filtering Rule with Conditional access option](/sites/default/files/downloads/ZIA-6.2r-Conditional-Access-in-Policy.png)

## August 07, 2025
### Feature Available
#### Support for Collaborator Groups
You can filter and view logs for External Collaborator Group and Internal Collaborator Group for the File Sharing Applications category. As part of the update, the following changes are available in the ZIA Admin Portal:
SaaS Security Insights Logs
Filters and columns External Collaborator Group and Internal Collaborator Group are added to the File Sharing Applications category in the SaaS Security Insights Logs.
[See image.](#collab_filters_saas)
To learn more, see [About SaaS Security Insights Logs](/zia/saas-security-insights-logs).
SaaS Security Assets with Incidents
The following changes are available under the Assets with Incidents page (Analytics > SaaS Security > Assets > Assets with Incidents) for the File Sharing Applications category:
-
Files tab: The columns External Collaborator Group and Internal Collaborator Group are added.
[See image.](#files_tab)
-
Advanced Filters tab: The filters External Collaborator Group and Internal Collaborator Group are added.
[See image.](#adv_filters)
To learn more, see [Understanding the Assets Report: Assets with Incidents](/zia/understanding-assets-report-assets-with-incidents).
NSS Feeds
You can add the following fields for internal and external collaborator groups to the Feed Output Format when configuring SaaS Security NSS or Cloud NSS feeds for File applications:
- `%s{intcollab_groups}`
- `%s{ointcollab_groups}`
- `%s{b64intcollab_groups}`
- `%s{extcollab_groups}`
- `%s{oextcollab_groups}`
- `%s{b64extcollab_groups}`
To learn more, see [NSS Feed Output Format: SaaS Security Logs](/zia/nss-feed-output-format-saas-security-logs).
![External Collaborator Groups and Internal Collaborator Groups Filters in the SaaS Security Insights Logs.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/SaaS_Insights_collab_group.png)
[]
![Select Collaborator Groups from the Advanced Filters tab.](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/logs/about-insights-logs/Collaborators_Group_advanced_filters.png)
[]
![Assets With Incidents page with details of File Sharing App in a table.](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/logs/about-insights-logs/Collaborators_Group_file_table.png)
[]

### Feature Available
#### Support for Number of Collaborators for Google Drive in DLP
The SaaS Security Data at Rest Scanning Data Loss Prevention (DLP) policy supports the number of internal and external collaborators as scoping criteria for Google Drive. Administrators can apply the scope to collaborators by choosing a range for the number of internal and external collaborators to monitor file sharing among collaborators.
[See image.](#collaborators-count-for-gdrive)
To learn more, see [Configuring the Data At Rest Scanning DLP Policy](/zia/configuring-data-rest-scanning-dlp-policy) and [About Data at Rest Scanning DLP](/zia/about-data-rest-scanning-dlp).
[]![Number of internal and external collaborators](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/configuring-data-rest-scanning-dlp-policy-draft/collaborator-count-dlp.png)

## August 01, 2025
### Feature Available
#### Content Location Match Criteria for Web DLP Rules
You can choose a content location as a match criteria to target specific sections of a file or transaction when defining a Data Loss Prevention (DLP) rule.
To enable this feature, contact Zscaler Support.
- File
- Document Properties: Matches are based on the file metadata (i.e., MIP labels).
- File Content: Matches are based on the actual content of the file, not including metadata.
- File Name: Matches are based on the name of the file.
- HTTP Body
- HTTP Body: Matches are based on the body of the HTTP request. Note: you must also select non-file file type when selecting HTTP Body as a content location.
[See image.](#content-locations-1530752)
To learn more, see [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection) and [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled).
Update to Cloud Service API
The cloud service API is also updated to include a new `dlpContentLocationsScopes` attribute in the `WebDlpRule` model used in `/webDlpRules` endpoints to configure this option via API.
To learn more, see the [API Reference](/zia/about-api).
[]![Select one or more content locations when adding a DLP Rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/content-locations-add-dlp-rule.png)

## July 28, 2025
### Feature Available
#### Improvements to the Users Page
Multiple enhancements have been made to improve the load time and performance of the Users page in 3rd-Party App Governance. This significantly improves the user experience.
To learn more, see [About User Inventory](/zia/about-user-inventory).

### Feature Available
#### Support for Detecting Internal Apps
Multiple improvements help to automatically detect internal apps and relate publishers to those internal apps in 3rd-Party App Governance.
To learn more, see [About the App Inventory](/zia/about-app-inventory).

### Feature Available
#### Support for Excessive Data Permissions Finding for GitHub Apps
A new finding, Excessive Data Permissions, is created for GitHub apps in 3rd-Party App Governance. Applications with excessive data permissions can access or modify multiple data types like emails, files, chats, and calendars, which puts the organization at risk of non-compliance and malicious actions, including privacy breaches, data abuse, theft, and misuse. The Excessive Data Permissions finding indicates the security or posture issues associated with GitHub apps.
To learn more, see [Integrating with GitHub](/zia/integrating-github) and [About the App Panel](/zia/about-app-panel).

### Feature Available
#### Support for SaaS Application Tenants Label Management
You can add and manage labels for Software as a Service (SaaS) application tenants from the Integrations banner in 3rd-Party App Governance and Advanced SSPM. You can also filter the platforms by label. This allows you to identify the differences between the tenants for effective prioritization and take actions based on each tenant's needs, enabling better security assessment.
[See image.](#Labels-Filter)
You must have user or admin permissions to add or manage labels.
To learn more, see [About the 3rd-Party App Governance Dashboard](/zia/about-3rd-party-app-governance-dashboard) and [About the SaaS Dashboard](/zia/about-saas-dashboard).
[]![Integrations Banner showing the Labels Filters](/sites/default/files/downloads/Filter_Labels_RN.png)

### Feature in Limited Availability
#### Support for Correlated View of App Users and DLP File Access
A new tab, Files, is added to the User Panel in 3rd-Party App Governance. This tab provides visibility into files associated with Data Loss Prevention (DLP) violations for a given user over a selected period of time. You can quickly identify the top files with DLP violations, enabling more targeted investigation of risky data access by sanctioned app users.
[See image.](#Files-Tab)
To view the information on the Files tab, you must have a license for SaaS Security Data at Rest Scanning DLP and the DLP scan must be previously configured. To upgrade your license, contact your Zscaler Account team.
To learn more, see [About the User Panel](/zia/about-user-panel).
[]![User Panel showing Files Tab](/sites/default/files/downloads/UserPanel_FilesTab_RN_0.png)

### Feature in Limited Availability
#### Support for SaaS Dashboard in Advanced SSPM
You can view the Software as a Service (SaaS) dashboard when you access Zscaler Advanced SaaS Security Posture Management (SSPM). The dashboard displays information about the overall posture score and risk score across all apps, platforms, and user accounts. It also displays the posture score over time, and top risky controls, accounts, and apps.
[See image.](#SaaS-Dashboard)
To learn more, see [About the SaaS Dashboard](/zia/about-saas-dashboard).
[]![SaaS Dashboard showing all widgets](/sites/default/files/downloads/Saas_Dashboard_RN.png)

## July 18, 2025
### Feature Available
#### Add Comments for ATP Blocked Malicious URLs
You can now add comments to malicious URLs you have added to Advanced Threat Protection (ATP) Blocked Malicious URLs.
To learn more, see [Adding URLs to the ATP URL Allowlist or Denylist](/zia/adding-urls-denylist).
[]

### Feature Available
#### Customizable User Confirmation Templates
You can now create and manage multiple user confirmation templates for enhanced policy-level customization in the ZIA Admin Portal by going to Administration > Notification Templates > User Confirmation and clicking Add Custom Message. When configuring Endpoint DLP or Inline Web DLP rules with the Confirm action, you can select the specific user confirmation template to be displayed to the end user.
[See image.](#configure-user-notification-templates-1530759)
To learn more, see:
- [Configuring User Confirmation Notification Templates](/zia/configuring-user-confirmation-notification-templates)
- [Configuring Settings for User Confirmation Notification Templates](/zia/configuring-settings-user-confirmation-notification-templates)
- [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection)
- [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection)
- [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled)
[]![Add Custom User Notification Template in the Add Custom Message window](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/add-custom-message-window.png)

### Feature Available
#### Enhancement to EDM Match Count
The Zscaler Data Loss Prevention (DLP) Exact Data Match (EDM) dictionary search score total `matchCount` has been enhanced to be based on the number of unique sets of matches found in the content.
Previously, `matchCount` was determined by the number of matches across all rows and all templates specified in active dictionaries, and only unique templates contributed to the `matchCount` total. If multiple dictionaries used the same template, each instance of the template was counted as a separate match. With this update, `matchCount` is based on unique token matches, irrespective of the templates or dictionaries used, and only unorder unique sets of matches are counted. Additionally, the distinction between primary and secondary fields is no longer applicable; all matches are counted equally.
To learn more, see [Understanding Exact Data Match Index Templates](/zia/understanding-edm-index-templates).

### Feature Available
#### Enhancements to Cybersecurity Insights
You can now view and download the latest Zscaler ThreatLabz updates of all newly generated or updated content by the Zscaler ThreatlabZ team in a PDF from the Cybersecurity Insights page.
[See image.](#savepdf_img)
To learn more, see [About Cybersecurity Insights](https://help.zscaler.com/zia/about-cybersecurity-insights).
![Download the latest Zscaler Threatlabz Updates in Cybersecurity Insights.](/sites/default/files/downloads/release-notes-drafts/Save_as_pdf.png)
[]

### Feature Available
#### Logs for Allowed File Type Rule
You can filter and view logs for [File Type Control](/zia/about-file-type-control) policy rules that use the Allow action and have been triggered by the transaction. The following changes are available in the ZIA Admin Portal:
Web Insights Logs
A filter and column, Allowed File Type Rule, is added to Web Insights Logs.
[See image.](#allowed_ft_rule_img)
To learn more, see [Web Insights Logs: Columns](/zia/web-insights-logs-columns) and [Web Insights Logs: Filters](/zia/web-insights-logs-filters).
NSS Feeds
The field `%s{ft_rulename}` can be added to the Feed Output Format when configuring an NSS or Cloud NSS feed for web logs.
To learn more, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs).
![Allowed File Type Rule Filter in Web Insights Logs](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/logs/web-insights-logs-columns/Allowed_file_type_rn_modified.png)
[]

## July 11, 2025
### Feature Available
#### Downloading Policies
On the Print All Policies page (Administration > Print All Policies), you can download your organization's configured policies as JSON files by selecting the ZIP file format. A single ZIP file containing JSON representation of the policies is downloaded, with one JSON file created for each policy type within the ZIP file. In addition, you can download policies as a PDF file.
[See image.](#download-ZIA-policies-JSON)
[]![Option to download ZIA policies as PDF and JSON files](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/download-ZIA-policies-JSON.png)

### Feature Available
#### Location Groups Filter in NSS Feeds
A Location Groups filter is added to NSS and Cloud NSS feeds for Web, Firewall, and DNS logs as well as Microsoft Cloud App Security (MCAS) NSS feeds. You can use the filter when configuring a feed to limit the logs to specific location groups.
[See image.](#img-location-groups-nss-filter)
To learn more, see:
- [Adding NSS Feeds for Web Logs](/zia/adding-nss-feeds-web-logs#Fwhere)
- [Adding Cloud NSS Feeds for Web Logs](/zia/adding-cloud-nss-feeds-web-logs#Fwhere)
- [Adding NSS Feeds for Firewall Logs](/zia/adding-nss-feeds-firewall-logs#Source)
- [Adding Cloud NSS Feeds for Firewall Logs](/zia/adding-cloud-nss-feeds-for-firewall-logs#Source)
- [Adding NSS Feeds for DNS Logs](/zia/adding-nss-feeds-dns-logs)
- [Adding Cloud NSS Feeds for DNS Logs](/zia/adding-cloud-nss-feeds-dns-logs)
- [Adding MCAS NSS Feeds](/zia/adding-mcas-nss-feeds#from)
Updates to Cloud Service API
The `/nssFeeds` endpoints within the cloud service API is also updated to include a new `locationGroups` attribute in the `ZmanageNssFeed` model.
To learn more, see the [API Reference](/zia/about-api).
[]![Location Groups NSS filter](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/nss-location-groups-filter.png)

### Feature Available
#### Update to Firewall and Forwarding Rules
In Firewall and Forwarding rules, the Department field was accessible to some customers without the appropriate entitlement (requires Advanced Firewall). An update has been made to ensure that this field availability matches the admin’s entitlement to the field licensed with Advanced Firewall. For customers who had access to this field without Advanced Firewall, any existing rules that use the Department condition will continue to function normally without any changes. However, these rules are non-editable and can only be deleted.
To manually replace such rules, it is recommended to first define a higher order rule with conditions applicable to your entitlements. After verifying the optimal behavior of the new rule considering the changed functionality, you can safely delete the lower order rule with the Department field.

## July 07, 2025
### Feature Available
#### EDM and DLP Support for New PII Dictionaries
The following predefined DLP and EDM dictionaries now support an additional format for Australian Passport numbers:
AAn(6), where AA is a combination of two letters (PA - PF, PU, PW, PX, PZ, and RA - RZ) and n is a combination of 6 digits. A delimiter (hyphen, spaces, or period) after the letters and before the numbers is supported.
[See image.](#add-dlp-dictionary-1499556)
To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries) and [Creating an Exact Data Match Template](/zia/creating-exact-data-match-template).
[]![Edit the DLP Dictionary for Australian Passport numbers](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/add-aus-dlp-dictionary.png)

### Feature Available
#### Index Tool Single Sign-On
Single sign-on (SSO) can be configured for the ZIA [Index Tool](/zia/about-index-tool) when adding or editing an Index Tool configuration.
[See image.](#Index-tool-sso)
To learn more, see [Configuring Single Sign-On for the Index Tool](/zia/configuring-single-sign-index-tool).
[]![View of the SSO Configurations for the Index Tool](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-index-tool-sso-config.png)

### Feature Available
#### New EDM Data Types
When creating your Zscaler Data Loss Prevention (DLP) EDM templates, you can now select the following data types:
- National Document ID (Uruguay)
- National Identification Number (Chile)
- National Identification Number (Peru)
To learn more, see [Creating an Exact Data Match Template](/zia/creating-exact-data-match-template).

## June 25, 2025
### Feature Available
#### Custom Browser EUN Support for File Type Control Policy
The File Type Control policy rules support Custom Browser end user notifications (EUN). You can create a custom EUN template for the File Type Control policy and associate it with the policy rules. This allows you to show the custom notification messages on the endpoints when the File Type Control rules are triggered. As part of this change, in the Add File Type Control Rule window (Policy > File Type Control > Add File Type Control Rule), the Browser Notification Template field is added, which appears when the rule access is set to block or caution.
[See image.](#add-file-type-control)
To learn more, see [Configuring Browser EUN Template](/zia/configuring-browser-eun-template) and [Configuring the File Type Control Policy](/zia/configuring-file-type-control-policy).
[]![ZIA Add File Type Control Rule with the Browser Notification Template](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-Add-File-Type-Control-Rule-RN.png)

### Feature Available
#### Support for Microsoft as an IdP in 3rd-Party App Governance
Zscaler 3rd-Party App Governance supports Microsoft as an identity provider (IdP) to authenticate admins and users logging in to the 3rd-Party App Governance Admin Portal. You can select Microsoft as the IdP when connecting a web-based platform to Advanced SaaS Security Posture Management (SSPM) from the 3rd-Party App Governance Admin Portal.
[See image.](#Microsoft-as-IdP)
To learn more, see [Connecting Your Platforms to Advanced SSPM](/zia/connecting-your-platforms-advanced-sspm).
[]![Identity Provider Drop-Down Menu](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/Add_Integration_RN.png)

## June 24, 2025
### Feature Available
#### SaaS Security Data at Rest Scanning DLP Redaction Support
The SaaS Security Data at Rest Scanning Data Loss Prevention (DLP) policy for file sharing applications supports redacting sensitive data in supported file types. To use this functionality, you first create a redaction profile that specifies whether the Zscaler service uses an asterisk (`*`) or hash (`#`) to mask sensitive data.
[See image.](#rights-management-redaction-profile-rn)
With the redaction profile in place, you can then create Data at Rest Scanning DLP policy rules for file sharing applications that apply the redaction settings to [supported file types](/zia/adding-editing-redaction-profiles#Supported-Redaction-Filetypes) that trigger the policy rule.
[See image.](#rights-management-redaction-rule-rn)
Redaction is not supported for the Smartsheet file sharing application and when configuring Data at Rest Scanning DLP policies without content inspection.
To learn more, see [About Rights Management](/zia/about-rights-management).
Updates to Assets with Incidents Page
You can remove redaction characters that were applied to a file via a redaction profile in the SaaS Assets Report: Assets with Incidents page (Analytics > SaaS Security Report > Assets) as a remediation action.
[See image.](#restore_recent_version_rn)
To learn more, see [SaaS Assets Report: Assets with Incidents](/zia/saas-assets-report-assets-incidents).
[]![The Add Redaction Profile Window](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-DLP-Rights-Management-Add-Redaction-Profile-RN.png)
[]![The Redaction option for a SaaS Security Data at Rest Scanning DLP policy rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-DLP-Rights-Management-Redaction-Rule-RN.png)
![Assets with Incidents Page showing Remediation Action](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/logs/web-insights-logs-columns/restore_most_recent_redacted_file.png)
[]

### Feature Available
#### SaaS Security Data at Rest Scanning DLP Support for Trusted Users and Trusted Domains
The SaaS Security Data at Rest Scanning Data Loss Prevention (DLP) policy supports specifying trusted users (i.e., users with email addresses outside your organization) and trusted domains (i.e., domains outside your organization) as part of your policy rules. The Zscaler service treats trusted domains and trusted users the same as internal domains and internal users.
[See image.](#data-at-rest-trusted-users-domains-rn)
Trusted users and trusted domains are configured as recipient profiles and domain profiles, respectively, in the Email Profiles for your organization.
When evaluating rules, if a file matches all rule criteria *and* the trusted users or trusted domains set for the rule, the Zscaler service does not consider a transaction to be a rule violation and does not take action on the file.
To learn more, see [Configuring the Data at Rest Scanning DLP Policy with Content Inspection](/zia/configuring-data-rest-scanning-dlp-policy-content-inspection), [Configuring the Data at Rest Scanning DLP Policy without Content Inspection](/zia/configuring-data-rest-scanning-dlp-policy-without-content-inspection), and [About Email Profiles](/zia/about-email-profiles).
[]![The SaaS Security Data at Rest Scanning Window with Trusted Users and Trusted Domains](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-Data-at-Rest-DLP-Trusted-Users-Domains-RN.png)

## June 23, 2025
### Feature Available
#### New Cloud Applications
New cloud applications are added to the cloud application categories. You can download the list of newly added cloud applications to the respective categories: [Download](/sites/default/files/downloads/zia/documentation-knowledgebase/policies/cloud-apps/cloud-app-control-policies/cloud-app-categories/New_Cloud_Apps_July_2025.xlsx)
The risk index and risk attribute values for these new applications are visible only after they are available on all the clouds.

## June 20, 2025
### Feature Available
#### Ability to Set an Endpoint DLP Exception Rule To Take No Action
You can apply the None action to exception rules in Endpoint Data Loss Prevention (DLP) to exclude specific activities that match exception rule criteria from being reported (i.e., you might want to exclude specific users or groups from reporting incidents).
[See image.](#endpoint-dlp-policy-action-none-RN)
To learn more, see [Configuring Endpoint DLP Policy Rules](/zia/configuring-endpoint-dlp-policy-rules).
[]![The None Action Option on an Exception Rule for Endpoint DLP](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-Endpoint-DLP-Action-Equals-None-RN.png)

### Feature Available
#### DLP Support for New ML-Based Dictionaries
The following are new predefined DLP dictionaries that use ML-based detection:
- ID Card
- Medical Imaging
- Satellite Data
- Schematic Data
To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).

### Feature Available
#### Endpoint DLP Support for Predefined Dictionaries
The Zscaler service now supports the following existing predefined Data Loss Prevention (DLP) dictionaries for Endpoint DLP:
- CNPJ Number (Brazil)
- Mexico Unique Population Registration Code
- National Economic Registry Number (Poland)
- Personal Identification Number (Croatia)
- Unique Master Citizen Number
To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).

### Feature Available
#### Enhancement to Posture Management Page
The Remediate option is removed from the policy drawer and Asset Summary tab on the Posture Management page. This option is available only if you subscribed to the Advanced SSPM service.
[See image.](#Policy-Drawer)
To learn more, see [About Posture Management Report](/zia/about-posture-management-report) and[ What Is Advanced Posture Management?](/zia/what-advanced-posture-management)
[]![Policy Drawer showing Actions drop-down menu](/sites/default/files/downloads/PolicyDrawer_RemediateRN.png)

### Feature Available
#### Expanded Onboarding Options for Salesforce
The Zscaler service supports custom, client-side connector onboarding for access to both sandbox and production Salesforce tenants. With this functionality, instead of requiring full administrator credentials, the Zscaler service can use a minimum set of credentials to access Salesforce.
[See image.](#SF_custom)
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants) and [Authorizing a Custom Zscaler Connector for Salesforce](/zia/authorizing-custom-zscaler-connector-salesforce).
[]![Salesforce custom tenant onboarding authorization](/sites/default/files/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/sf_addtenant_authorize.png)

### Feature Available
#### New Macros Available for DLP Notification Templates
Zscaler added three new inline web DLP macros for your DLP notification templates:
- `${DEPARTMENT}`: Shows the department of the user who triggered the DLP rule.
- `${FILESIZE}`: Specifies the size of the file that triggered the DLP rule.
- `${REFERRER_URL`}: Shows the referrer URL of the user who triggered the DLP rule.
To learn more, see [Configuring DLP Notification Templates](/zia/configuring-dlp-notification-templates).

### Feature Available
#### Support for EDM and IDM in Outbound Email DLP Policies
The Zscaler service supports using Exact Data Match (EDM) and Indexed Document Match (IDM) dictionaries and engines in your Outbound Email Data Loss Prevention (DLP) policy rules.
[See image.](#data-at-rest-trusted-users-domains-rn)
To learn more, see [Configuring Outbound Email Policy Rules](/zia/configuring-outbound-email-policy-rules), [About Exact Data Match](/zia/about-exact-data-match) and [About Indexed Document Match](/zia/about-indexed-document-match).
[]![The SaaS Security Data at Rest Scanning Window with Trusted Users and Trusted Domains](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-Outbound-Email-DLP-rule-EDM-Engine-RN.png)

### Feature Available
#### Support for Parent DLP Dictionaries and Sub-Dictionaries
The Zscaler service supports using Patterns and Phrases Data Loss Prevention (DLP) dictionaries to create custom parent dictionaries and sub-dictionaries as a means of grouping similar dictionaries. For parent dictionaries, you can define patterns or phrases, or you can leave them blank so that they act simply as a container for sub-dictionaries.
On the DLP Dictionaries & Engines page (Administration > DLP Dictionaries & Engines) you can click Add DLP Sub Dictionary on an existing Patterns and Phrases dictionary to create a sub-dictionary. The sub-dictionaries you create appear under their parent dictionary.
[See image.](#DLP-create-sub-dictionary-rn)
After you create parent dictionaries and sub-dictionaries, you can use them to create custom DLP engines.
[See image.](#DLP-create-engine-with-parent-sub-dictionaries-rn)
Parent dictionaries and sub-dictionaries, as well as the engines that use them, are not supported for Endpoint DLP.
To learn more, see [Adding Custom DLP Dictionries](/zia/adding-custom-dlp-dictionaries) and [Adding Custom DLP Engines](/zia/adding-custom-dlp-engines).
[]![DLP Parent Dictionary with Sub-Dictionaries on the DLP Dictionaries & Engines Page in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-Create-DLP-Sub-Dictionary-RN.png)
[]![Creating a Custom DLP Engine with a Parent Dictionary and Sub-Dictionary](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-Create-DLP-Engine-Parent-Sub-Dictionary-RN.png)

### Feature Available
#### Support for User Groups and Departments in Device Control Policy
Administrators can now define Device Control rules criteria (Analytics > Endpoint Data Scan > Device Control) based on User Groups and Departments.
[See image.](#device_control_rules)
To learn more, see [Managing a Removable Storage Rule](/zia/managing-removable-storage-rule), [Managing a Printer Rule](/zia/managing-printer-rule), and [Managing a Nearby Sharing Rule](/zia/managing-nearby-share-rule).
![User Groups and Departments in the Add Removable Storage Device Rule Window](/sites/default/files/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/inventory/analyzing-application-details/user_groups_departments.png)
[]

### Feature Available
#### Update to Zscaler Client Connector-based Notifications
You can embed links and add line breaks in the custom messages for Zscaler Client Connector-based End User Notifications (EUNs) (Administration > End User Notifications > Client Connector) and User Confirmation notifications (Administration > Notification Templates > User Confirmation).
[See image.](#zscaler-client-connector-eun-embedded-links)
To learn more, see [Configuring User Confirmation Notification Templates](/zia/configuring-user-confirmation-notification-templates) and the EUN configuration articles for individual policies that can be accessed from [About Zscaler Client Connector-Based End User Notifications](/zia/about-zscaler-client-connector-based-end-user-notifications).
[]![Zscaler Client Connector Notification Message Customization](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/zscaler-client-connector-eun-embed-links.png)

### Feature Available
#### Updates to Cloud Service API: SaaS Security Endpoints
The cloud service API includes the following endpoint categories to extend programmatic access to various ZIA features and functionalities:
- [SaaS Security API](#saas-security-1529212-api)
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection is also updated to include new and updated resources.
To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).
[]You can create, update, and retrieve SaaS Security APIs for the Data at Rest Scanning policies using the following endpoints:
- `GET /casbDlpRules`
- `POST /casbDlpRules`
- `GET /casbDlpRules/all`
- `GET /casbDlpRules/{ruleId}`
- `PUT /casbDlpRules/{ruleId}`
- `DELETE /casbDlpRules/{ruleId}`
- `GET /casbMalwareRules`
- `POST /casbMalwareRules`
- `GET /casbMalwareRules/all`
- `GET /casbMalwareRules/{ruleId}`
- `PUT /casbMalwareRules/{ruleId}`
- `DELETE /casbMalwareRules/{ruleId}`
- `GET /casbEmailLabel/lite`
- `GET /casbTenant/{tenantId}/tags/policy`
- `GET /casbTenant/lite`
- `GET /quarantineTombstoneTemplate/lite`

## June 17, 2025
### Feature Available
#### Tenancy Restriction Support for Amazon Web Services CLI
Tenancy restriction support is extended to Amazon Web Services CLI.
To learn more, see [Adding Tenant Profiles](/zia/adding-tenant-profiles).

## June 13, 2025
### Feature Available
#### Multiple Sandbox API Token Support
Zscaler Sandbox (Administration > Cloud Service API Security > Sandbox API Token) supports up to 5 Sandbox API Tokens. The Sandbox token name field has a limit of 10 characters.
[See image.](#multiple_tokens)
Web Insight Logs (Analytics > Web Insights > Logs) allow for filtering by Sandbox API Key Name. Select the API Key Name column category to see the token name in the log records.
[See image.](#api_key)
To learn more, see [About Sandbox API Tokens](/zia/about-sandbox-api-token) and [About Insights Logs](/zia/about-insights-logs).
[]![Cloud Service API Security, multiple Sandbox API Tokens](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/Multiple%20Tokens02.png)
[]![Insight Logs Sandbox API Key filtering](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/Insights%20Logs%20API%20key.png)

### Feature Available
#### Support for Filtering for Advanced Threat Protection
Users can now add URLs and MD5 file hashes to an Allowlist for Advanced Threat Protection (ATP) to explicitly allow or deny access to specific URLs or files.
[See image.](#allowlist-1526711)
To learn more, see [Adding URLS to the Allowlist](/zia/adding-urls-allowlist), [Add Custom File Hashes](/zia/add-custom-file-hashes), [Configuring Security Exceptions for the Malware Protection Policy](/zia/configuring-security-exceptions-malware-protection-policy), and [Configuring the Advanced Threat Protection Policy](/zia/configuring-advanced-threat-protection-policy).
[]![Add a URL to the Allowlist.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/sandbox-allowlist.png)

## June 06, 2025
### Feature Available
#### Exclude Selected Applications from NSS Feeds
A filter to include or exclude selected cloud applications has been added to the existing Cloud Applications filter in NSS and Cloud NSS feeds for web logs as well as Microsoft Cloud App Security (MCAS) NSS feeds. When configuring a feed, you can select cloud applications and include them in the logs by default or choose to exclude them from the logs.
[See image.](#img-nss-cloud-applications-include-exclude-filter)
To learn more, see [Adding NSS Feeds for Web Logs](/zia/adding-nss-feeds-web-logs#Twhere), [Adding Cloud NSS Feeds for Web Logs](/zia/adding-cloud-nss-feeds-web-logs#Twhere), and [Adding MCAS NSS Feeds](/zia/adding-mcas-nss-feeds#to).
Additionally, the filter has been added to the existing Network Applications filter in NSS and Cloud NSS feeds for Firewall logs to include or exclude selected network applications.
[See image.](#img-nss-network-applications-include-exclude-filter)
The added filter enables you to separate feeds based on application and reduce the volume of data streamed to your security information and event management (SIEM) system.
To learn more, see [Adding NSS Feeds for Firewall Logs](/zia/adding-nss-feeds-firewall-logs#Protocol) and [Adding Cloud NSS Feeds for Web Logs](/zia/adding-cloud-nss-feeds-for-firewall-logs#Protocol).
Update to Cloud Service API: New Attributes for Cloud NSS Feeds
The `/nssFeeds` endpoints within the cloud service API include two new attributes, `webApplicationsExclude` and `nwApplicationsExclude`, in the `ZmanageNssFeed` model. These attributes are used to exclude specific cloud applications and network applications from the logs, respectively, when configuring cloud NSS feeds.
To learn more, see the [API Reference](/zia/about-api).
[]
![Cloud Applications filter with Include/Exclude functionality in the NSS feed for web logs configuration page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/include-exclude-filter-nss-web-logs.png)
[]
![Network Applications filter with Include/Exclude functionality in the NSS feed for Firewall logs configuration page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/include-exclude-filter-nss-fw-logs.png)

### Feature Available
#### Gen AI Prompt Configuration for Writer and Deepseek
Zscaler's Gen AI prompt configuration is extended to the Writer and Deepseek generative AI applications. You can enable prompts for these generative AI applications to categorize and store the prompts for the respective applications.
[See image.](#gen-ai-writer-deepseek)
To learn more, see [Configuring Advanced Policy Settings](/zia/configuring-advanced-policy-settings#gen-AI-prompt).
[]![ZIA Advanced Policy Settings Page with Writer and Deepseek Gen AI Applications](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-Advanced-Policy-Settings-Writer-Deepseek-RN.png)
Added Deepseek and Writer Capabilities to URL & Cloud App Control Policy Settings Endpoint
Two new Boolean fields, `enableDeepSeekPrompt` and `enableWriterPrompt`, are available for the `AdvancedUrlFilteringCloudAppOptions` model in the `/advancedUrlFilterAndCloudAppSettings` APIs. These fields allow users to use generative AI prompts with Deepseek and Writer.
To learn more, go to `AdvancedUrlFilteringCloudAppOptions` from [URL & Cloud App Control Policy Settings](/zia/url-cloud-app-control-policy-settings).

### Feature Available
#### Increase in the Default Number of Allowed File Type Control Policy Rules
The default limit of File Type Control Policy rules has been increased to 2,048 from 1,024.
To learn more, see [Ranges & Limitations](/zia/ranges-limitations#Rules).

### Feature Available
#### Support for New SaaS Security Application Tenant
The SaaS Security Data at Rest Scanning DLP and Malware policies support configuring tenants for Zoom, a collaboration application.
[See image.](#add-tenant-zoom)
To learn more, see [About SaaS Application Tenants](/zia/about-saas-application-tenants) and [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
You can configure the application for the SaaS Security Data at Rest Scanning policies and also view them on the following pages:
- [About the Assets Report](/zia/about-assets-report)
- [About SaaS Assets Summary Report](/zia/saas-assets-summary-report)
- [SaaS Security Insights](/zia/saas-security-insights) and [About SaaS Security Insights Logs](/zia/saas-security-insights-logs)
- [Adding NSS Feeds for SaaS Security Logs](/zia/adding-nss-feeds-saas-security-logs) and [Adding Cloud NSS Feeds for SaaS Security Logs](/zia/adding-cloud-nss-feeds-saas-security-logs)
To learn more, see [Understanding the Data at Rest Scanning Policy](/zia/understanding-data-rest-scanning-policy), [Configuring the Data at Rest Scanning DLP Policy](/zia/configuring-data-rest-scanning-dlp-policy), and [Configuring the Data at Rest Scanning Malware Detection Policy](/zia/configuring-data-rest-scanning-malware-detection-policy).
[]![Add SaaS Application Tenants for Zoom](/sites/default/files/downloads/zia/policies/saas-security/data-rest-scanning-policies/about-data-rest-scanning-dlp/Tenant%20Onboarding%20page.png)

### Feature Available
#### Support for Quarantine Tombstone Template in the Assets Report
You can now choose the Tombstone Template when quarantining files to the user root folder in the Assets Report (Analytics > SaaS Security > Assets).
[See image.](#tombstone_template_img)
To learn more, see [About Quarantine Tombstone File Templates](/zia/about-quarantine-tombstone-file-templates), [Configuring Quarantine Tombstone Notification Templates](/zia/configuring-quarantine-tombstone-notification-templates), and [Understanding the Assets Report: Assets with Incidents](/zia/understanding-assets-report-assets-with-incidents).
![Choose Tombstone Template in SaaS Security Assets Reports - Assets with Incidents page.](/sites/default/files/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/configuration/configuring-endpoint-data-scan-endpoint-settings/Tombstone_template_Assets_report.png)
[]

### Feature Available
#### Update to Cloud Service API: Enhancement to Location Group Endpoint
A new query parameter `fetchLocations` is available for the `GET /locations/groups` endpoint. The `fetchLocations` parameter is a Boolean that you can set to fetch locations associated with the group.
To learn more, go to `GET /locations/groups` from [Location Management](/zia/location-management).

### Feature Available
#### Update to Custom IPS Signature Rules CSV Import
When importing custom IPS signature rules using CSV files (Administration > Custom IPS), you must enclose comma-separated values for individual fields within three single quotes (`'''`) instead of double quotes (`"`). This update has been made to prevent parsing errors that might occur with certain Perl Compatible Regular Expressions (PCRE) options used in custom IPS signature rules.
[See example rule.](#sample-ips-rule-triple-quotes)
This update pertains to the Custom IPS feature that is enabled with Advanced Firewall.
To learn more, see [Importing and Exporting Custom IPS Signature Rules](/zia/importing-exporting-custom-signature-rules).
[]
Old Rule FormatNew Rule Format`+,"Rule_1","alert tcp any any -> any 8080 ( msg:"http_header found"; content:"|2f|wp|2d|admin|2f|"; flow:established,to_server; http_uri; pcre:"/\w{0,6}/Ri"; sid:6; )","ADVANCED_SECURITY","","Enable"``'''+''','''Rule_1''','''alert tcp any any -> any 8080 ( msg:"http_header found"; content:"|2f|wp|2d|admin|2f|"; flow:established,to_server; http_uri; pcre:"/\w{0,6}/Ri"; sid:6; )''','''ADVANCED_SECURITY''','''''','''Enable'''`

## June 02, 2025
### Feature in Limited Availability
#### Support for Zscaler-Managed Business Continuity Cloud
The Zscaler-managed Business Continuity Cloud is a fully managed private cloud solution that is built on the isolated and dedicated ZIA and Zscaler Private Access (ZPA) infrastructures to ensure consistent cyber and data protection during critical outages. Zscaler deploys and hosts the private ZIA and ZPA cloud in third-party data centers, for simplified operations and faster business continuity enablement.
This service leverages the ZIA Private Service Edges with two new components, the Private Policy Cache and the Private PAC Server, that help apply the last known good policy configurations, maintaining seamless traffic flow when the Zscaler cloud is unreachable.
To subscribe to the Business Continuity Cloud service, contact your Zscaler Sales Representative.
To learn more, see [Understanding Zscaler-Managed Business Continuity Cloud](/zia/understanding-zscaler-managed-business-continuity-cloud) and [Understanding the Components of Business Continuity](/zia/understanding-components-business-continuity).

## May 30, 2025
### Feature Available
#### Advanced SaaS Security Posture Management Support for Workday
You can configure Advanced SaaS Security Posture Management (SSPM) for Workday tenants. Select the SSPM Scan checkbox when onboarding a Workday tenant to enable the Advanced SSPM scan capability for the specific tenant.
[See image.](#workday-sspm-onboarding)
The SSPM Scan checkbox is enabled only when you have Advanced SSPM enabled for your tenant.
To learn more, see [What Is Advanced Posture Management?](/zia/what-advanced-posture-management) and [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
[]![Workday Onboarding Section showing the SSPM Scan Checkbox](/sites/default/files/downloads/zia/policies/saas-security/posture-management/posture-management-advanced/about-control-panel/Adavanced%20SSPM-Workday2.png)

### Feature Available
#### Gen AI Prompt Configuration for Grok AI
Zscaler's Gen AI prompt configuration is extended to the Grok AI generative AI application. You can enable prompts for this application to categorize and store the prompts for it.
[See image.](#gen-ai-grok-ai)
To learn more, see [Configuring Advanced Policy Settings](/zia/configuring-advanced-policy-settings#gen-AI-prompt).
[]![ZIA Advanced Policy Settings Page with Grok AI Gen AI Application](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-Advanced-Policy-Settings-Grok-AI-RN.png)
Added Grok Capability to URL & Cloud App Control Policy Settings Endpoint
A new Boolean field, `enableGrokPrompt`, is available for the `AdvancedUrlFilteringCloudAppOptions` model in the `/advancedUrlFilterAndCloudAppSettings` APIs. This field allows users to use generative AI prompts with Grok.
To learn more, go to `AdvancedUrlFilteringCloudAppOptions` from [URL & Cloud App Control Policy Settings](/zia/url-cloud-app-control-policy-settings).

### Feature Available
#### SaaS Security Posture Management Support for Webex Teams
You can configure the SaaS Security Posture Management (SSPM) Scan for Webex Teams tenants. Select the SSPM Scan checkbox when onboarding a Webex Teams tenant to enable the SSPM scan capability for the specific tenant.
[See image.](#workday-sspm-onboarding)
The SSPM Scan checkbox is enabled only when you have Advanced SSPM enabled for your tenant.
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants) and [What is Advanced Posture Management?](/zia/what-advanced-posture-management)
[]![Workday Onboarding Section showing the SSPM Scan Checkbox](/sites/default/files/downloads/zia/policies/saas-security/posture-management/posture-management-advanced/about-control-panel/Adavanced%20SSPM-Workday2.png)

## May 28, 2025
### Feature Available
#### Support for Dedicated IP and Geolocalization IP
The Dedicated IP feature allows organizations to subscribe to dedicated IP addresses for the Zscaler data centers of their choice. Users can use these dedicated IP addresses (unique to the organization) as their source IP address to reach destinations that require source IP-based access.
The Geolocalization IP feature allows organizations located across countries to forward traffic via source IP addresses mapped to the country from where the traffic originates. This enables users to access destinations (e.g., government websites) that require the country's local source IP address for access.
The dedicated IP and the geolocalization IP features leverage ZIA forwarding policies to forward traffic.
As part of this feature, the following enhancements are available in the ZIA Admin Portal:
Dedicated IP
A new page, Dedicated IP, is added to the Administration menu. This page displays two tabs: Gateways and IP Addresses.
-
Gateways: This page allows you to create gateway objects using dedicated IP addresses provisioned to your organization to forward traffic.
[See image.](#RN-dedicated-ip-gateways)
To learn more, see [About Dedicated IP Gateways](/zia/about-dedicated-ip-gateways).
-
IP Addresses: This page lists the dedicated IP addresses provisioned for your organization by Zscaler for the Zscaler data centers you have selected.
[See image.](#RN-dedicated-ip-addresses)
To learn more, see [About Dedicated IP Addresses](/zia/about-dedicated-ip-addresses).
Forwarding Policy
Two new forwarding methods, Dedicated IP and Geo IP, are added when configuring traffic forwarding rules.
- Use the Dedicated IP forwarding method to forward traffic to destinations using the source IP addresses provisioned for the organization.
- Use the Geo IP forwarding method to forward traffic to destinations using the source IP address mapped to the country from where the traffic originates.
[See image.](#RN-forwarding-control)
To learn more, see [Configuring Forwarding Policy](/zia/configuring-forwarding-policy), [Understanding Zscaler-Managed Dedicated IP](/zia/understanding-zscaler-managed-dedicated-ip), and [Understanding Geolocalization IP](/zia/understanding-geolocalization-ip).
Insights and Logs
Forwarding Methods, Dedicated IP and Geo IP, are introduced to the Firewall Insights Logs page.
[See image.](#RN_insights_logs_img)
To learn more, see [Firewall Insights Logs: Columns](/zia/firewall-insights-logs-columns) and [Firewall Insights Logs: Filters](/zia/firewall-insights-logs-filters).
Updates to Cloud Service API
The cloud service API includes the `GET /dedicatedIPGateways/lite` endpoint to the Forwarding Control Policy category to retrieve a list of dedicated IP gateways.
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
![Dedicated IP > Gateways page in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/zia-RN-dedicated-ip-gateways-page.png)
[]
![Dedicated IP > IP Addresses page in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/zia-RN-dedicated-ip-addresses-page.png)
[]
![Dedicated IP and Geo IP forwarding methods in the Forwarding Control policy page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/zia-RN-dedicated-ip-geo-ip-forwardig-control-policy.png)
[]
![Firewall Insights Logs showing the Forwarding Method filters.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/Reports_Logs_forwarding_methods_geo_ip.png)
[]

### Feature Available
#### Update to Web Insights for Bandwidth Control
Web Insights includes additional information for Bandwidth Control with the new filter Bandwidth by Data Center.
[See image.](#bandwidth-insights-1529599)
To learn more, see [Web Data Types and Filters](/zia/web-data-types-and-filters).
[]![Filter Bandwidth Control data by Data center.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/bwc-datacenter-insights.png)

## May 27, 2025
### Feature Available
#### Support for Unified Onboarding of SaaS Application Tenants
You can onboard, edit, and delete new Software as a Service (SaaS) application tenants enabled with 3rd-Party App Governance or the Advanced SaaS Security Posture Management (SSPM) feature from the Add SaaS Application Tenant page in the ZIA Admin Portal. You can continue editing or deleting the existing tenants enabled with the 3rd-Party App Governance feature in the 3rd-Party App Governance Admin Portal.
[See image.](#App-Governance-Checkbox)
Onboarding of Atlassian tenants is supported only in the 3rd-Party App Governance Admin Portal.
To learn more, see [Connecting Your Platforms to 3rd-Party App Governance](/zia/connecting-your-platforms-3rd-party-app-governance) and [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
[]![Add SaaS Application Tenant page showing App Governance Checkbox](/sites/default/files/downloads/AppGovernance_Chkbox_RN.png)

## May 26, 2025
### Feature Available
#### Support for Risk Explainability in 3rd-Party App Governance and Advanced SSPM
On the App Panel header, you can hover over the risk score to view a breakdown of the score. On the Control Panel header, you can hover over the control severity level to view a breakdown of the severity. These actions allow you to view the components and criteria used to calculate the app risk score and control severity level.
[See image.](#App-Panel-Header)
To learn more, see [About the App Panel](/zia/about-app-panel) and [About the Control Panel](/zia/about-control-panel).
[]![App Panel Header showing breakdown of risk score](/sites/default/files/downloads/Risk_Exp_RN.png)

## May 23, 2025
### Feature Available
#### Cloud Application Updates
As part of a continuous review, Zscaler has updated cloud applications across various cloud application categories. To obtain the list of updated cloud applications, download the list: [Download](/sites/default/files/downloads/zia/documentation-knowledgebase/policies/cloud-apps/cloud-app-control-policies/cloud-app-categories/Updated-Cloud-Apps-April-2025.xlsx)
Cloud applications are updated in phases. Refer to the [trust post](https://trust.zscaler.com/zscaler.net/notification/223176) for details.

### Feature Available
#### New Cloud Applications
New cloud applications are added to the cloud application categories. You can download the list of newly added cloud applications to the respective categories: [Download](/sites/default/files/downloads/zia/documentation-knowledgebase/policies/cloud-apps/cloud-app-control-policies/cloud-app-categories/New-Cloud-Apps-April-2025.xlsx)
The risk index and risk attribute values for these new applications are visible only after they are available on all the clouds. Refer to the [trust post](https://trust.zscaler.com/zscaler.net/notification/223166) for details.

### Feature Available
#### SCIM-Based User Lookup For Outbound Email DLP
Zscaler Outbound Email DLP supports System for Cross-domain Identity Management (SCIM)-based user lookup to map email addresses with ZIA login names.
To learn more, see [Step-by-Step Configuration Guide for Zscaler Outbound Email DLP](/zia/step-step-configuration-guide-zscaler-outbound-email-dlp#prerequisites).
NSS Feeds for Email DLP Logs
The field `%s{sender}` can be added to the Feed Output Format when configuring an NSS or Cloud NSS feed for Email DLP logs.
To learn more, see [NSS Feed Output Format: Email DLP Logs](/zia/nss-feed-output-format-email-dlp-logs).

## May 21, 2025
### Feature Available
#### Zoom in Tenant Profile
The Tenant Profiles feature supports Zoom. This allows granular control of actions (e.g., disable file transfer in meetings, disable recording locally on the device, etc.) in Zoom.
[See image.](#tr-zoom-rn)
To learn more, see [Adding Tenant Profiles](/zia/adding-tenant-profiles).
[]![Screenshot of ZIA Tenant Profiles with Zoom](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2023/ZIA-Add-Tenant-Profile-Zoom-RN.png)

## May 16, 2025
### Feature Available
#### Expanded File Type Support for File Type Control and DLP
The File Type Control and Data Loss Prevention (DLP) policies now support the Appinstaller Files (.appinstaller) file type in the Other Documents** **category.
- [File Type Control](#appinstaller-ftc-1529187)
- [DLP (Rule without content inspection)](#dlp-appinstaller-1529187)
To learn more, see [About File Type Control](/zia/about-file-type-control) and [About Data Loss Prevention](/zia/about-data-loss-prevention).
[]![Add .appinstaller file type to File Type Control Policy](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/appinstaller-ftc.png)
[]![Add .appinstaller file type to DLP policy without content matching](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/appinstaller-dlp-nomatching.png)

### Feature Available
#### File Type Control Enhancements
You can configure file type control rules based on Password-Protected criteria. This criteria is applicable for the following formats:
- Password-Protected/Encrypted
- Portable Document Format (.pdf)
- Encrypted Office Documents
- ZIP
- RAR
- 7-Zip
- ZIP w/Suspicious Script
- Zipx
[See Image.](#password-protected-file-1515481)
To learn more, see [Configuring File Type Policy](/zia/configuring-file-type-control-policy).
Update to Cloud Service API
The `/fileTypeRules` endpoints within the cloud service API include a new rule criterion, `passwordProtected`, to apply the rule to password-protected files in specific file formats.
To learn more, see the [API Reference](/zia/about-api).
[]![Enable Password Protected Files in the Add File Type Control Rule window](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/enable-password-protected-file.png)

### Feature Available
#### Microphone and Camera Functionality for Isolation Profiles in ZIA
Isolation allows microphone and camera functionality on the user's device while in an isolated browser. This can be enabled per isolation profile if Turbo Mode is also enabled.
[See image.](#mic-and-camera-toggle)
To learn more, see [Creating Isolation Profiles for ZIA](/isolation/creating-isolation-profiles-zia).
[]![Enable the toggle to allow microphone and camera functionality for your device while in Isolation.](/sites/default/files/downloads/isolation/profiles/zpa-profiles/creating-isolation-profiles-zpa/ZPA_toggle_mic-and-camera.png)

### Feature Available
#### Support for SaaS Security API Data at Rest Scanning DLP Policy Rules without Content Inspection
To enable this feature for your organization, contact Zscaler Support.
On the Data at Rest Scanning page (Policy > Saas Security > Data at Rest Scanning), you can create Data at Rest Scanning Data Loss Prevention (DLP) policies without content matching.
[See image.](#saas-dlp-policy-without-inspection-RN)
To learn more, see [Configuring the Data at Rest Scanning DLP Policy without Content Inspection](/zia/configuring-data-rest-scanning-dlp-policy-without-content-inspection).
[]![A Data at Rest Scanning Policy Rule without Content Inspection](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-Data-at-Rest-Scanning-DLP-Rule-without-Content-Inspection-RN.png)

### Feature Available
#### Support for Site Groups in SaaS Application Tenants and DLP Policy
SaaS Application Tenants (Administration > SaaS Application Tenants > Manage SaaS Application Components) supports the management of SharePoint tenant Sites and Site Groups. In the Components tab, you can view a list of the SharePoint sites that are available under the selected SharePoint tenant. In the Groups tab, you can view, add, and edit groups of SharePoint sites that are used to configure DLP policies. You can also perform a bulk upload of SharePoint sites to a group via CSV files. Each group can contain a maximum of 10,000 sites.
[See image.](#tenant_group)
The SaaS Security Data at Rest Scanning DLP Policy supports Sites and Site Groups as policy criteria for SharePoint tenants. You can choose to either include or exclude up to 256 site groups from the policy, or apply the policy to 1,024 individual sites. The two fields can't be chosen together.
[See image.](#site-groups-dlp)
To learn more, see [About SaaS Application Tenants](/zia/about-saas-application-tenants), [Manage SaaS Application Components](/zia/manage-saas-application-components), [About Data at Rest Scanning DLP](/zia/about-data-rest-scanning-dlp), and [Configuring the Data at Rest Scanning DLP Policy](/zia/configuring-data-rest-scanning-dlp-policy).
[]![Manage SaaS Application Components with Groups tab selected](/sites/default/files/downloads/zia/configuring-saas-security-api-dlp-policy/Manage%20Tenant%20groups%20annot02.png)
[]![Sites and Site Groups in policy criteria](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/configuring-data-rest-scanning-dlp-policy-draft/site-groups-dlp.png)

## May 13, 2025
### Feature Available
#### Enhancements to Endpoint Data Scan
The following enhancements are made to the Endpoint Data Scan page (Analytics > Endpoint Data Scan):
Nearby Sharing
Zscaler Device Control is enhanced to prevent nearby sharing between endpoints and devices that are close by. The Nearby Sharing rule restricts the use of nearby sharing methods and blocks file transfers to adjacent devices. This restriction does not provide protocol granularity or control over particular target destination devices, nor is it based on content inspection. You can access Nearby Sharing from Analytics > Endpoint Data Scan > Device Control. The supported nearby sharing methods include:
- Windows: File transfer over Bluetooth, Nearby Share, and Phone Link.
- macOS: AirDrop, Universal Clipboard, iPhone Sync & Mirroring, and File transfer over Bluetooth.
[See image.](#nearby_sharing_img)
To learn more, see [About Device Control](/zia/about-device-control) and [Managing Nearby Sharing Rules](/zia/managing-nearby-share-rule).
Export Inventory
The Export option in the Inventory page provides you with the ability to export inventory data, such as removable storage devices and printers, into a CSV file.
[See image.](#export_option)
To learn more, see [About Inventory](/zia/about-inventory).
Persistent Columns
The persistent columns support saving column selections and resizing preferences for user convenience and customization.
![Nearby Sharing tab in the Device Control tabwith the rules created.](/sites/default/files/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/inventory/analyzing-application-details/Nearby_Sharing_RN.jpg)
[]
![The Export option is introduced in the Inventory Page.](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/logs/web-insights-logs-columns/Inventory_Export.png)
[]

### Feature Available
#### HTTP Header Control
The HTTP Header Control feature allows you to create URL Filtering policy rules based on HTTP headers. As part of this change, the following profiles are added to the ZIA Admin Portal:
- HTTP Header Profile (Administration > HTTP Header Control)
- HTTP Header Insertion Profile (Administration > HTTP Header Control > HTTP Header Insertion Profile)
[See image.](#http-header-contol)
To learn more, see [About HTTP Header Profile](/zia/about-http-header-profile) and [About HTTP Header Insertion Profile](/zia/about-http-header-insertion-profile).
Logs for HTTP Header Profile and HTTP Header Insertion Profile
Filters and columns, HTTP Header Profile and HTTP header Insertion Profile, are added to Web Insights Logs.
To learn more, see [Web Insights Logs Columns](/zia/web-insights-logs-columns) and [Web Insights Logs Filters](/zia/web-insights-logs-filters).
[]![The HTTP Header Control Page in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-HTTP-Header-Control-RN.png)

### Feature Available
#### Update to Zscaler Client Connector-Based Notifications
Zscaler Client Connector-based End User Notifications (EUNs) and user confirmation messages for Inline Web DLP and Cloud App Control policies can be enabled without having an Endpoint DLP subscription.
These policy EUNs are supported (without requiring Endpoint DLP) on the following Zscaler Client Connector versions:
- For Windows: 4.6.0.123 and later
- For macOS: 4.3.1.56 and later
To learn more, see [About Zscaler Client Connector-Based End User Notifications](/zia/about-zscaler-client-connector-based-end-user-notifications) and [About User Confirmation Notification Templates](/zia/about-user-confirmation-notification-templates).

## May 09, 2025
### Feature Available
#### Added Alert for Unknown and Suspicious C2 Traffic
You can enable the service to send alerts for unknown or suspicious C2 traffic. This feature is enabled by default.
[See image.](#enable-alerts-c2traffic-1508871)
To learn more, see [Configuring the Advanced Threat Protection Policy](/zia/configuring-advanced-threat-protection-policy).
[]![Enable Alert for Unknown or suspicious C2 traffic in Advanced Threat Protection](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/enable-alert-for-unknownc2traffic.png)

### Feature Available
#### Enhancements to Admin Role Management
The Administration > Role Management page is enhanced to provide admins more granular access to major ZIA features. Super admins or admins with full access to the ZIA Admin Portal can assign admins field-wise permissions (Full, View Only, and None) to access individual ZIA features. This enhancement enables you to have granular control over defining the level of access the admins have based on the scope of their responsibility.
This enhancement to role-based administration also extends to SD-WAN partner API roles and API roles to access the Zscaler cloud service APIs.
[See image.](#RN-granular-rabc)
To learn more, see [About Role Management](/zia/about-role-management), [Adding Admin Roles](/zia/adding-admin-roles), [Adding SD-WAN Partner API Roles](/zia/adding-sd-wan-partner-api-roles), and [Adding API Roles](/zia/adding-api-roles).
[]![The Add Administrator Role window with the granular role-based access on the Role Management Page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/zia-RN-role-management-add-administrator-role-window.png)

### Feature Available
#### Instance Discovery Report Enhancements
The Instance Discovery Report provides visibility into the instances accessed by users at the various levels of hierarchy for different SaaS applications.
The Instance Discovery Report includes the following enhancements:
- New applications are supported with various levels of instance discovery types.
- Applications supporting level one of instance discovery: Google Drive, Gmail, Box, OneDrive, Microsoft Outlook, Microsoft Teams, Salesforce, and ServiceNow.
- Applications supporting level two of instance discovery: SharePoint and Slack.
- Applications supporting level three of instance discovery: Google Cloud Platform.
- New instance level types are added: Domain, Tenant, Site, and Workspace.
- A drill down from the Instance Discovery Report to monitor and view logs for the Resource Discovery Report for the various SaaS Applications for instance types, such as Domain, Tenant, Site, and Workspace.
[See image.](#inst_disc_img)
To learn more, see [About the Instance Discovery Report](/zia/about-instance-discovery-report) and [Viewing the Resource Discovery Report](/zia/viewing-resource-discovery-report).
![Instance Discovery Report showing all the widgets and the applications.](/sites/default/files/downloads/release-notes-drafts/Instance_Discovery_Report_RN.png)
[]

### Feature Available
#### Update to Cloud Service API: Cloud Application Instance Endpoints
The cloud service API includes the following new endpoints to create, update, and delete cloud application instances:
- `POST /cloudApplicationInstances`
- `PUT /cloudApplicationInstances/{instanceId}`
- `DELETE /cloudApplicationInstances/{instanceId}`
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).

### Feature Available
#### Update to Cloud Service API: User Endpoint Rate Limit
The rate limit for the `GET /users` request within the cloud service API has been updated to 10 calls/minute and up to 40 calls/hour.
To learn more, see the [API Rate Limit Summary](/zia/api-rate-limit-summary).

### Feature Available
#### Updates to Cloud Service API
The cloud service API includes the following new categories of endpoints to extend programmatic access to various ZIA features and functionalities:
- [Alerts](#alerts-api)
- [Bandwidth Control & Classes](#bandwidth-control-classes-api)
- [Cloud Nanolog Streaming Service](#nss-1527016-api)
- [Forwarding Control Policy](#forwarding-control-policy-1527016-api)
- [FTP Control Policy](#ftpcontrol-policy-api)
- [Mobile Malware Protection Policy](#mobile-malware-protect-policy-api)
- [Time Intervals](#Time-Intervals-api)
- [Admin & Role Management](#admin-role-management-1527016-api)
- [Cloud Applications](#cloud-app-1527016-api)
- [NAT Control Policy](#dnat-rules-1527016-api)
- [Firewall Policies](#firewall-policies-1527016-api)
- [Cloud App Control Policies](#cloudapp-control-policies-1527016-api)
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection is also updated to include new and updated resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).
[]You can create and update alert subscriptions and retrieve a list of alert subscriptions using the following endpoints:
- `GET /alertSubscriptions`
- `POST /alertSubscriptions`
- `GET /alertSubscriptions/{alertSubscriptionId}`
- `PUT /alertSubscriptions/{alertSubscriptionId}`
[]You can create, update, and delete Bandwidth Control rules and retrieve information about the rules using the following endpoints:
- `GET /bandwidthControlRules`
- `POST /bandwidthControlRules`
- `GET /bandwidthControlRules/lite`
- `GET /bandwidthControlRules/{ruleId}`
- `PUT /bandwidthControlRules/{ruleId}`
- `DELETE /bandwidthControlRules/{ruleId}`
[]You can create, update, and delete bandwidth classes and retrieve the bandwidth class information for an organization using the following endpoints :
- `GET /bandwidthClasses`
- `POST /bandwidthClasses`
- `GET /bandwidthClasses/lite`
- `GET /bandwidthClasses/{bandwidthClassId}`
- `PUT /bandwidthClasses/{bandwidthClassId}`
- `DELETE /bandwidthClasses/{bandwidthClassId}`
[]You can create, update, and delete NSS servers and retrieve a list of registered NSS servers using the following endpoints:
- `GET /nssServers`
- `POST /nssServers`
- `GET /nssServers/{nssId}`
- `PUT /nssServers/{nssId}`
- `DELETE /nssServers/{nssId}`
[]You can update the Mobile Malware Protection rules and retrieve information about the rules using the following endpoints:
- `GET /mobileAdvanceThreatSettings`
- `PUT /mobileAdvanceThreatSettings`
[]You can update the FTP Control settings and retrieve the FTP Control status and the list of URL categories for which FTP is allowed using the following endpoints:
- `GET /ftpSettings`
- `PUT /ftpSettings`
[]You can create, update, and delete a proxy for a third-party proxy service and retrieve information about them using the following endpoints:
- `GET /proxies`
- `POST /proxies`
- `GET /proxies/lite`
- `GET /proxies/{proxyId}`
- `PUT /proxies/{proxyId}`
- `DELETE /proxies/{proxyId}`
[]You can create, update, and delete time intervals and retrieve a list of configured time intervals using the following endpoints:
- `GET /timeIntervals`
- `POST /timeIntervals`
- `GET /timeIntervals/{Id}`
- `PUT /timeIntervals/{Id}`
- `DELETE /timeIntervals/{Id}`
[]You can update and retrieve information about password expiration using the following endpoints:
- `GET /passwordExpiry/settings`
- `PUT /passwordExpiry/settings`
[]You can create, update, and delete cloud application risk profiles and retrieve them using the following endpoints:
- `GET /riskProfiles`
- `POST /riskProfiles`
- `GET /riskProfiles/lite`
- `GET /riskProfiles/{profileId}`
- `PUT /riskProfiles/{profileId}`
- `DELETE /riskProfiles/{profileId}`
[]You can create, update, and delete DNAT Control policies and retrieve a list of all configured and predefined DNAT Control policies using the following endpoints:
- `GET /dnatRules`
- `POST /dnatRules`
- `GET /dnatRules/{ruleId}`
- `PUT /dnatRules/{ruleId}`
- `DELETE /dnatRules/{ruleId}`
[]You can create, update, and delete DNS Gateways and retrieve a list of DNS Gateways using the following endpoints:
- `GET /dnsGateways`
- `POST /dnsGateways`
- `GET /dnsGateways/lite`
- `GET /dnsGateways/{id}`
- `PUT /dnsGateways/{id}`
- `DELETE /dnsGateways/{id}`
[]You can create, update, and delete tenant profiles and retrieve information about restricted tenant profiles using the following endpoints:
- `GET /tenancyRestrictionProfile`
- `POST /tenancyRestrictionProfile`
- `GET /tenancyRestrictionProfile/app-item-count/{appType}/{itemType}`
- `GET /tenancyRestrictionProfile/{profileId}`
- `PUT /tenancyRestrictionProfile/{profileId}`
- `DELETE /tenancyRestrictionProfile/{profileId}`

### Feature Available
#### Updates to Cloud Service API: Service Edges
The cloud service API includes the following new categories of endpoints to extend programmatic access to various ZIA features and functionalities:
- [Service Edges](#service-edges1529212-api)
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection is also updated to include new and updated resources.
To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).
[]You can create, update, and delete Virtual Service Edge clusters and retrieve a list of Virtual Service Edge clusters using the following endpoints :
- `GET /virtualZenClusters`
- `POST /virtualZenClusters`
- `GET /virtualZenClusters/{virtualZenClusterId}`
- `PUT /virtualZenClusters/{virtualZenClusterId}`
- `DELETE /virtualZenClusters/{virtualZenClusterId}`

### Feature Available
#### Updates to the Add UEBA Alerts Page
The Trigger Multi-Factor Authentication action under Adding Alert Rule for UEBA Alert is deprecated and alert triggers with Multi-Factor Authentication is no longer supported. You can choose between Trigger an Alert or Place user in group to trigger the alert rule.
[See image.](#ueba-actions-for-rules)
To learn more, see [Configuring an Alert Rule](/zia/configuring-alert-rule).
[]![The available actions for UEBA Alerts to trigger the rule.](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/configuring-alert-rule-draft-ueba/UEBA%20Actions.png)

### Feature Available
#### WebSocket Protocol Type in DLP Rules
You can choose either WebSocket or WebSocket SSL/TLS as a protocol type when defining a Data Loss Prevention (DLP) rule. On the Policy > URL Filtering & Cloud App Control > Advanced Policy Settings tab, a Microsoft Copilot toggle is added under the Gen AI Prompt Configuration section. Enabling this option allows you to categorize and store the prompts for the Microsoft Copilot application.
WebSocket protocol is supported only for the Microsoft Copilot application.
[See image.](#WebSocket-Protocol-Options)
To learn more, see [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection), [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection), [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled), and [Configuring Advanced Policy Settings](/zia/configuring-advanced-policy-settings).
[]![Add DLP Rule Window showing WebSocket Protocol Options](/sites/default/files/downloads/WebSocket_Protocol.png)

## May 07, 2025
### Feature Available
#### ChatGPT in Tenant Profile
The Tenant Profiles feature is extended to the ChatGPT application. This allows you to provide access to specific workspace IDs for ChatGPT.
[See image.](#chatgpt-tenant-profile)
To learn more, see [Adding Tenant Profiles](/zia/adding-tenant-profiles).
[]![Add Tenant Profile Window with the ChatGPT application selected](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-Add-Tenant-Profile-ChatGPT-RN.png)

## May 02, 2025
### Feature Available
#### Update to Sandbox Scanning Portal URL
The Sandbox Scanning Portal is now more secure with the change to an HTTPS URL: [https://filecheck.zscaler.com/](https://filecheck.zscaler.com/)
If you have bookmarks to the previous URL for the Sandbox Scanning Portal, update them as they no longer work.
To learn more, see [Using the Sandbox Scanning Portal](/zia/using-sandbox-scanning-portal).

## April 29, 2025
### Feature Available
#### Email Notification Support for Policies in 3rd-Party App Governance
When creating a policy, you can choose to send an email through one or more default email addresses to notify the users whenever the policy is triggered.
[See image.](#Set-Policy-Window)
To learn more, see [3rd-Party App Governance Policies](/zia/3rd-party-app-governance-policies).
[]![Set Policy Window showing Email option](/sites/default/files/downloads/SetPolicy_WindowRN.png)

### Feature Available
#### Support for Viewer Role in 3rd-Party App Governance
You can assign a new predefined role called Viewer to a user. When assigned this role, the user can only view data and export reports across the 3rd-Party App Governance Admin Portal, but cannot take any action or make changes.
To manage role assignments, contact Zscaler Support.
To learn more, see [About Roles in 3rd-Party App Governance](/zia/about-roles-3rd-party-app-governance).

## April 28, 2025
### Feature Available
#### Email Notification Support for Revoking or Banning Apps in 3rd-Party App Governance
When you revoke or ban an app for users in your organization, you can send an email to notify them that the previously accessible app is revoked or banned. You can also select the email address from which you want to send the email.
[See image.](#Revoke/Ban-Confirmation-Window)
You can only view the default email to be sent, but you cannot edit it.
To learn more, see [Revoking and Banning Apps](/zia/revoking-banning-apps) and[ Adding Outbound Integrations](/zia/adding-outbound-integrations).
[]![Revoke/Ban Confirmation Window showing Send email checkbox](/sites/default/files/downloads/RevokeBan_Confirmation.png)

## April 18, 2025
### Feature Available
#### Auditor Email Notifications for Outbound Email DLP
You can configure notification templates so that email notifications are sent automatically to specified auditors when outbound email transactions trigger Outbound Email DLP rules.
On the Notification Templates page (Administration > Notification Templates > DLP), you can create a customized message detailing why the content triggered the Outbound Email DLP rule:
[See image.](#email-dlp-notification-template-RN)
With the template in place, you can include the notification template as part of your Outbound Email DLP rules (Policy > Outbound Email Policy):
[See image.](#email-dlp-rule-notification-template-RN)
To learn more, see [Configuring DLP Notification Templates](/zia/configuring-dlp-notification-templates) and [Configuring Outbound Email Policy Rules](/zia/configuring-outbound-email-policy-rules).
[]![An Outbound Email DLP Notification Template](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-Outbound-Email-DLP-Notification-Template-RN.png)
[]![An Outbound Email DLP Rule with a Notification Template](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-Outbound-Email-DLP-Rule-with-Notification-Template-RN.png)

### Feature Available
#### Configure External Trusted Domain & User Profiles in Tenant Onboarding
SaaS Application tenant onboarding for SaaS Security API now supports configuring external trusted domains and users.
[See image.](#config_domain)
To learn more, see [About Email Profiles](/zia/about-email-profiles), [Adding Email Profiles](/zia/adding-email-profiles), and [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
[]![Configure External Trusted Domain Profiles and User Profiles step during tenant onboarding](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/Config_domains2.png)
![Dropdown menu for External Trusted Domains with two example items selected.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/Config_domains_dropdown2.png)

### Feature Available
#### Support for Number of Collaborators for File Sharing Applications in DLP
The SaaS Security Data at Rest Scanning Data Loss Prevention (DLP) policy supports the number of internal and external collaborators as a scoping criteria for SharePoint and OneDrive to monitor file sharing among collaborators. Administrators can choose a range for the number of internal and external collaborators to apply the scope to.
[See image.](#collaborator-count-image)
To learn more, see [Configuring the Data At Rest Scanning DLP Policy](/zia/configuring-data-rest-scanning-dlp-policy) and [About Data at Rest Scanning DLP](/zia/about-data-rest-scanning-dlp).
[]
![The Number of External Collaborators and Number of Internal Collaborators fields where you can select a range.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/collaborator-count-dlp.png)

## April 04, 2025
### Feature Available
#### Developer Tools URL Category
The Developer Tools predefined URL category is added to the Information Technology super category. It consists of sites that provide tools used by developers for coding, debugging, testing, and managing software projects.
This category is enabled from the backend after it is deployed across all production clouds. Refer to the [trust post](https://trust.zscaler.com/notification/223061) for details.
[See image.](#developer-tools)
To learn more, see [About URL Categories](/zia/about-url-categories#Business).
[]![The URL Categories page with the Developer Tools category in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-URL-Categories-Page_RN.png)

### Feature Available
#### Enhancements to the SaaS Security Scan Configuration
You can refresh the status of a scheduled SaaS Security DLP or malware scan by clicking the Refresh icon next to the status of an ongoing scan on the SaaS Security Scan Configuration page.
[See image.](#scan-status-refresh)
To learn more, see [About SaaS Security Scan Configuration](/zia/about-saas-security-scan-configuration) and [Configuring SaaS Security Scan Schedules](/zia/configuring-saas-security-scan-schedules).
[]![Refresh the scan status to view the updated status of an ongoing scan.](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/about-saas-security-dlp-policy-doc-53484/Scan%20Config%20Status_0.png)

### Feature Available
#### New Predefined DLP Engines Available
The following are new predefined DLP engines available on the DLP Engines page (Administration > DLP Dictionaries & Engines > DLP Engines).
These engines are available by default for customers with tenants enabled on April 4, 2025, or later. For enablement on existing tenants, contact Zscaler Support.
- CCPA - High Volume
- CCPA - Low Volume
- Credentials and Secrets
- DPDPA
- Finance
- FISMA - High Volume
- FISMA - Low Volume
- GDPR - High Volume
- GDPR - Low Volume
- Legal
- LGPD - High Volume
- LGPD - Low Volume
- Medical
- NIST (RMF for DoD IT) - High Volume
- NIST (RMF for DoD IT) - Low Volume
- PDPA - DBs
- PDPA - High Volume
- PDPA - Low Volume
- PII (US) - High Volume
- PII (US) - Low Volume
- PIPEDA - DBs
- PIPEDA - High Volume
- PIPEDA - Low Volume
To learn more, see [Editing Predefined DLP Engines](/zia/editing-predefined-dlp-engines).

### Feature Available
#### Support for MIP Labels for PowerPoint Files in Data at Rest Scanning DLP Policy
For file sharing applications, you can configure MIP labels on PowerPoint files from the Data at Rest Scanning DLP policy in the Add DLP Rule window (Policy > Data at Rest Scanning > Data Loss Prevention). Choose from the list of OneDrive and SharePoint tenants to see this action.
[See image.](#apply-mip-label-data-at-rest-dlp)
You can also apply this action to Microsoft Excel, Microsoft Word, and PDF file types.
To learn more, see [Configuring the Data at Rest Scanning DLP Policy](/zia/configuring-data-rest-scanning-dlp-policy).
[]![The Apply MIP Label action for a PowerPoint file in a Data at Rest Scanning DLP Policy Rule](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-MIP-Labels-for-PPT-Files-RN.png)

### Feature Available
#### Support for New SaaS Application Tenants
Twilio and Trello are supported as SaaS application tenants. Both can only be configured for SSPM scan which requires an Advanced SSPM license. If you don't have the correct license, a message to upgrade your license appears next to the SSPM Scan checkbox during the onboarding process.
[See image.](#twilio_pic)
To learn more, see [About SaaS Application Tenants](/zia/about-saas-application-tenants) and [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
[]![List of supported SaaS Application tenants with annotations around Trello and Twilio](/sites/default/files/downloads/zia/policies/saas-security-api/saas-application-tenants/authorizing-custom-zscaler-connector-microsoft-applications/twilio_pic2.png)

### Feature Available
#### UCaaS One Click Configuration Support for Talkdesk
Unified Communications as a Service (UCaaS) one-click configuration support is now extended to the Talkdesk cloud application.
[See image.](#ucaas-talkdesk)
To learn more, see [Configuring Advanced URL Filtering Policy](/zia/configuring-advanced-url-policy-settings).
[][![The ZIA Advanced Policy Settings page with different configuration toggles and the Talkdesk toggle highlighted](/sites/default/files/downloads/zia/UCaaS_talkdesk_RN.png)
](/sites/default/files/downloads/zia/UCaaS_talkdesk_RN.png)

## March 28, 2025
### Feature Available
#### Changes to Policy Action Reasons in Web Insights and NSS Reports
The following policy actions seen in the Insights and NSS Reports have changed to ensure consistency with the field values from the Web Insights in the ZIA Admin Portal:
Old Policy ReasonNew Policy ReasonReputation block outbound request: adware/spyware siteNot allowed to use Adware/Spyware sitesNot allowed because URL is blacklistedNot allowed because URL is placed on the denylistNot allowed to access internetBlock Internet AccessNot allowed to browse this category, needs overrideNot allowed to browse this categoryIPS block: cryptomining & blockchain trafficIPS block: cryptomining trafficNot allowed to upload media files to this siteNot allowed to upload files to this siteCommunication with unknown serversBlocked Mobile App communicating with remote unknown serversCommunication with ad sitesBlocked Mobile App communicating to Ad websitesInformation identifying the deviceBlocked Mobile App leaking Device Identifier informationLocation information leakBlocked Mobile App leaking Location informationInsecure user credentialsBlocked Mobile App leaking user credentials insecurelyMalicious behaviorBlocked Mobile App exhibiting malicious behaviorPersonally Identifiable Information (PII)Blocked Mobile App leaking Personally Identifiable Information (PII)Known security vulnerabilitiesBlocked Mobile App with known security vulnerabilitiesCautioned to use this Social Network siteCautioned the use of this Social Network siteCautioned to use this Streaming Media siteCautioned to use this Streaming/Media siteNot allowed to use this Streaming Media siteNot allowed to use this Streaming/Media siteUnenrolled user is not allowed to establish SSL connection, use non-SSL URL to enrollUnenrolled user is not allowed to establish SSL connection
To learn more, see [Policy Reasons](/zia/policy-reasons).

### Feature Available
#### Expanded Python File Type Support for Sandbox
The Zscaler Sandbox supports additional file types:
- Python Source Code file (.py)
- Pickle files (.p, .pkl, and .pickle)
- Python Dynamic Module file (.pyd)
- Python Script file (.pyw)
[See image.](#file_type)
To learn more, see [About Sandbox](/zia/about-sandbox) and [Configuring the Sandbox Policy](/zia/configuring-sandbox-policy%20).
[]![Sandbox Rules, file types](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/Python%20file%20types.png)

### Feature Available
#### Hex-Encoded Requested Domain Field in NSS Feeds
The field `%s{ednsreq}` is available when adding an NSS or Cloud NSS feed for DNS logs. The field output is the hex-encoded FQDN in the DNS request.
To learn more, see [NSS Feed Output Format: DNS Logs](/zia/nss-feed-output-format-dns-logs).

### Feature Available
#### Update to Cloud Service API
To provide a unified and streamlined API experience through [Zscaler OneAPI](/oneapi/understanding-oneapi), our centralized API management solution for the Zscaler platform, Zscaler is applying the following changes to ZIA:
-
Going forward, the availability of the following endpoints within the ZIA cloud service API is limited to OneAPI only:
- `/adminRoles`
- `/departments`
- `/groups`
However, GET operations for these endpoints will continue to be supported in the ZIA cloud service API as well as OneAPI.
- Zscaler is expanding the range of API endpoints available in OneAPI to allow more functions to be automated for the Zscaler platform. So, the availability of newly added ZIA cloud service API endpoints, such as `/configAudit`, and any other endpoints added in future will be exclusively available via OneAPI.

### Feature Available
#### Update to Cloud Service API
The cloud service API is updated to include a new `GET /locations/supportedCountries` endpoint that retrieves an up-to-date list of countries supported in location configuration.
To learn more, see the [API Reference](/zia/about-api).

### Feature Available
#### Updates to Cloud Service API
The cloud service API includes updates to the following categories of endpoints to extend programmatic access to specific ZIA features and functionalities:
- [Admin & Role Management](#current-user-api)
- [System Audit Report](#system-audit-report)
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
[]You can retrieve information about the current administrator or auditor user accessing the API using the new `GET /adminUsers/me` endpoint.
[]You can retrieve the System Audit Report and the information available in specific report sections using the following endpoints:
- `GET /configAudit`
- `GET /configAudit/ipVisibility`
- `GET /configAudit/pacFile`

## March 27, 2025
### Feature Available
#### Support for Number of Collaborators in DLP Policy
The SaaS Security Data at Rest Scanning Data Loss Prevention (DLP) policy now supports the number of collaborators as a scoping criteria for file sharing applications. When enabled for a partner tenant, the CASB Collaborator Count field under Special Settings of the Tenant Details page specifies the number of collaborators who can access certain files and folders in a SaaS application.
[See image.](#collaborator-count-partner-portal)
[]![Specify Number of Collaborators on DLP](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/edit-policy-templates-zia-admin-portal/mpp-special-settings-update-rn.png)
To learn more, see [Configuring the Data At Rest Scanning DLP Policy](/zia/configuring-data-rest-scanning-dlp-policy) and [About Data at Rest Scanning DLP](/zia/about-data-rest-scanning-dlp).

### Feature Available
#### Zscaler EUN Web Page for DNS Control Policy
Using the DNS Control policy, you can redirect users to a new Zscaler-provided end user notification (EUN) web page to inform users of your organization policy when they access restricted domains. You can do this by selecting the Redirect Response action in the DNS Control rule and by manually specifying the following IP address for the Zscaler-hosted notification web page: `34.215.46.88`.
[See image.](#zscaler-eun-dns-rules)
To learn more, see [Configuring the DNS Control Policy](/zia/configuring-dns-control-policy).
[]![End user notification page provided by Zscaler for DNS Control policy](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/zscaler-eun-dns-rule.png)

## March 21, 2025
### Feature Available
#### DLP Support for New PII Dictionaries
The following are new predefined DLP Dictionaries:
- National Identification Number (Chile RUN)
- National Identification Number (Peru CUI)
- National Document ID (Uruguay)
To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).

## March 14, 2025
### Feature Available
#### Cookie Persistence Renamed to Persistent State for Isolation Profiles
In ZIA isolation profiles, the cookie persistence toggle has been updated to be called Persistent State.
[See image.](#new-toggle-name)
To learn more, see [Using Persistent State for Isolation](/isolation/using-persistent-state-isolation) and [Creating Isolation Profiles for ZIA](/isolation/creating-isolation-profiles-zia).
[]![Persistent State toggle enabled](/sites/default/files/downloads/isolation/profiles/zpa-profiles/creating-isolation-profiles-zpa/Persistent-State_enabled.png)

### Feature Available
#### Enhancement to Secure Browsing
You can configure granular Smart Browser Isolation policies for specific users or groups from the Secure Browsing page. As part of this change, the following fields are added to the Smart Isolate tab (Policy > Secure Browsing > Smart Isolate):
- Users
- Groups
These fields appear only when the Enable AI/ML based Smart Browser Isolation option is enabled.
[See image.](#secure-browsing-users-groups)
To learn more, see [Configuring Smart Browser Isolation Policy](/zia/configuring-smart-browser-isolation-policy).
[]![Screenshot of ZIA Secure Browsing Page with Users and Groups fields](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Secure-Browsing-RN.png)

### Feature Available
#### Isolation of Miscellaneous and Unknown Category in ZIA
Isolation creates preconfigured profiles for admins. These profiles can configure only the URL category "Miscellaneous and Unknown" in their Zscaler Internet Access (ZIA) policy. Some fields in this profile are permanently enabled, others permanently disabled, and some the admin can [edit](/isolation/editing-your-isolation-profile-zia).
To learn more, see [Understanding Isolation of Miscellaneous and Unknown Category in ZIA](/isolation/understanding-isolation-miscellaneous-and-unknown-category-zia) and [Creating Isolation Profiles for ZIA.](/isolation/creating-isolation-profiles-zia)

### Feature Available
#### Update to Application Service Groups
The Firewall policy allows you to manage outbound and inbound traffic for cloud service providers such as Amazon Web Services (AWS) and Google Cloud Platform (GCP), along with their subservices, using the newly added AWS and GCP application service groups. These application service groups are defined using the metadata including IP addresses published by the respective providers to identify the traffic belonging to their services. Zscaler continuously updates and validates the latest IP addresses published by the providers, ensuring that organizations have the most up-to-date information for traffic identification and policy enforcement.
[See image.](#AWS-GCP-application-service-groups)
To learn more, see [About Application Service Groups](/zia/about-application-service-groups) and [Configuring the Firewall Filtering Policy](/zia/configuring-firewall-filtering-policy).
[]![Firewall filtering rule with AWS and GCP application service groups as criteria to allow or block traffic from these services](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/AWS-GCP-application-service-groups.png)

## March 13, 2025
### Feature Available
#### Multiple VM Sandbox Report Analysis
For Advanced Sandbox users, all malicious samples are analyzed twice automatically, first through an unpatched vulnerable VM (Zero Day Report or Fully Patched VM Report) and then a second time through the fully patched secured VM (Regular Report). This allows you to compare the report outputs to identify mitigation effectiveness and potential risk.
[See image.](#report)
To learn more, see [About Sandbox](/zia/about-sandbox) and [Viewing Sandbox Reports and Data](/zia/viewing-sandbox-reports-data).
[]![An unpatched, vulnerable report with the Threat Score, Zero Day Report, and Virus and Malware highlighted.](/sites/default/files/downloads/zia/release-notes/Zero%20Day%20Report%2000_2.png)
![A patched, secure analysis with Threat Score, Regular Report, and Virus and Malware highlighted.](/sites/default/files/downloads/zia/release-notes/Zero%20Day%20Report%2001_2.png)

## March 07, 2025
### Feature Available
#### Remote Assistance Notification
The Zscaler service displays a notification when Remote Assistance is enabled.
[See image.](#ra-notification)
The maximum time limit for both view-only and full access is 90 days.
To learn more, see [Enabling Remote Assistance](/zia/enabling-remote-assistance).
[]![Image of the Remote Access Notification](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/ZIA-remote-assistance-notification.png)

### Feature Available
#### Updates to Cloud Service API
The cloud service API includes the following new categories of endpoints to extend programmatic access to various ZIA features and functionalities:
- [Admin & Role Management](#admin-role-api)
- [User Management](#user-management-api)
- [Traffic Forwarding](#traffic-forwarding-api)
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection is also updated to include new and updated resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).
[]You can create, update, and delete admin roles and retrieve a list of admin roles using the following endpoints:
- `GET /adminRoles`
- `GET /adminRoles/lite`
- `POST /adminRoles`
- `GET /adminRoles/{roleId}`
- `PUT /adminRoles/{roleId}`
- `DELETE /adminRoles/{roleId}`
[]You can create, update, and delete departments and retrieve a list of departments using the following endpoints:
- `GET /departments`
- `POST /departments`
- `GET /departments/lite`
- `GET /departments/{id}`
- `GET /departments/lite/{id}`
- `PUT /departments/{departmentId}`
- `DELETE /departments/{departmentId}`
[]You can create, update, and delete groups and retrieve a list of groups using the following endpoints:
- `GET /groups`
- `POST /groups`
- `GET /groups/lite`
- `GET /groups/{groupId}`
- `GET /groups/lite/{groupId}`
- `PUT /groups/{groupId}`
- `DELETE /groups/{groupId}`
[]You can update a subcloud and retrieve information about subclouds using the following endpoints:
- `GET /subclouds`
- `GET /subclouds/isLastDcInCountry/{id}`
- `PUT /subclouds/{id}`

## February 21, 2025
### Feature Available
#### DLP and EDM Support for PII
The existing predefined Credit Card dictionary and EDM data type now support the additional popular formats:
- Credit Card Number (China UnionPay)
- Debit Card Number (Maestro)
To learn more, see [Creating an Exact Data Match Template](/zia/creating-exact-data-match-template) and [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).

### Feature Available
#### Enhancement to HTTP/2 in SSL Inspection Policy
The Enable HTTP/2 option is enabled by default when configuring an SSL Inspection rule. This feature is only available when it is enabled for your organization.
[See image.](#http2-ssl)
To learn more, see [About SSL Inspection](/zia/about-ssl-inspection) and [Configuring SSL Inspection Policy](/zia/configuring-ssl-inspection-policy).
[]![Enable or disable HTTP/2 for SSL Inspection rules.](/sites/default/files/downloads/HTTP2%20SSL%20Inspection%20Rule.png)

### Feature Available
#### Tenant-to-Tenant Firewall Control and Logging Improvements
Additional Firewall Control and Logging capabilities have been added for scenarios where an organization's roaming user (i.e., remote user from a Home tenant) is a guest user visiting another organization's tenant location (i.e., Host tenant) in the same Zscaler cloud and that Host tenant allows such guest users.

### Feature Available
#### Update to DNS Control Policy
The DNS Control policy includes a new action, Block with Response Code, which allows you to block DNS traffic and send a response code to the client. The response code can be chosen from a predefined list that appears in a new Response Code field when this action is selected. When there is a policy match with the traffic, the transaction appears in DNS logs with the response code populated against the existing DNS Error Code column and the rule action is indicated by a "Block" value in the Request Action or Response Action columns.
[See image.](#dns-rule-block-response-code)
To learn more, see [Configuring the DNS Control Policy Action](/zia/configuring-dns-control-policy).
Update to Cloud Service API
The cloud service API is updated to include a new action value, `BLOCK_WITH_RESPONSE`, and a new `blockResponseCode` attribute for specifying the response code in the `FirewallDnsRule` model when the `BLOCK_WITH_RESPONSE` action is used.
To learn more, see the [API Reference](/zia/about-api).
[]![Action to block DNS by sending response code in DNS Filtering rules](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2025/dns-rule-block-response-code.png)

### Feature Available
#### Zscaler Incident Receiver Configuration Enhancement
Zscaler now supports the SSH key, ED25519.
To learn more on upgrading the SSH key to ED25519, see [Configuring the Zscaler Incident Receiver for On-Premises VMs](/zia/configuring-zscaler-incident-receiver), [Configuring the Zscaler Incident Receiver for Amazon Web Services EC2 VMs](/zia/configuring-zscaler-incident-receiver-for-ec2), and [Configuring the Zscaler Incident Receiver for Azure VMs](/zia/configuring-zscaler-incident-receiver-azure-vms).

## February 17, 2025
### Feature Available
#### Enhancement to Posture Page in Advanced SSPM
The Complexity column and filter are added to the Posture page. You can view the complexity level of a control and filter the controls displayed in the table by using this filter option. The Control Panel header for each control displays its complexity level. You can also view the** **Failed Controls Remediation graph, which displays the severity and implementation complexity of failed controls.
[See image.](#Control-Complexity)
To learn more, see [About Posture](/zia/about-posture) and[ About the Control Panel](/zia/about-control-panel).
[]![Posture Page showing Complexity column and Graph](/sites/default/files/downloads/zia/release-notes/Complexity_RN.png)

## February 14, 2025
### Feature Available
#### Enhancements to Assets Tab of the Control Panel in Advanced SSPM
The Assets tab of the Control Panel in Advanced SSPM includes the following enhancements:
- You can export the assets report to a CSV file.
- You can copy the asset evidence or download it as a JSON file.
[See image.](#ZIA-Assets-Tab-Enhancements)
To learn more, see [About the Control Panel](/zia/about-control-panel#Assets-Tab).
[]![Screenshot of Assets Tab Enhancements](/sites/default/files/downloads/Assets_Tab_RN.png)

### Feature Available
#### Update to Cloud Service API: Data Center Exclusion
The cloud service API includes the following new endpoints to support excluding a Zscaler data center (DC) in the event of service disruption by disabling all tunnels terminating at a virtual IP (VIP) address of the DC. Using these endpoints, you can add, modify, and delete DC exclusions and retrieve the list of configured exclusions. You can also retrieve the list of DCs that can be excluded from service.
- `GET /datacenters`
- `GET /dcExclusions`
- `POST /dcExclusions`
- `PUT /dcExclusions`
- `DELETE /dcExclusions`
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection has also been updated to include new and updated resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

## February 07, 2025
### Feature Available
#### Administrator Scope Department Limit
When configuring ZIA [admins](/zia/adding-zia-admins) and [super admins](/zia/adding-zia-super-admins), the maximum number of departments that can be selected for an admin with Department Scope is increased to 2,048.
To learn more, see [Ranges & Limitations](/zia/ranges-limitations).

### Feature Available
#### Enhancements to the IoT Report
The IoT Report has been enhanced to report IoT policy status and statistics for IoT devices.
To learn more, see [About the IoT Report](/zia/about-iot-discovery-report).
You can get an overview of the IoT web policies status and deep dive into their action impact on IoT web communications, such as domains/IPs and the corresponding policy action statistics in the IoT Report > Discovered Devices > Selected IP Address.
[See Image.](#web_policy_drilldown)
To learn more, see [About Discovered Devices](/zia/about-discovered-devices).
![The Web Policy drill down drawer that contains more details about the policy.](/sites/default/files/downloads/zia/RN_Discovered%20devices.png)
[]

### Feature Available
#### Increase in Query Limit for Sandbox Report API
The resource access quota for retrieving Sandbox Detail Reports is increased to 3,000 requests per day, with a rate limit of 2/sec and 1,000/hour.
To learn more, see the [Obtaining Sandbox Reports Using API](/zia/obtaining-sandbox-reports-using-api) and [Sandbox Report](/zia/sandbox-report) articles.

### Feature Available
#### Logs for Source and Destination IP Countries
You can filter and view logs for Source IP Countries, Destination IP Countries, Is Source IP Country Risky? and Is Destination IP Country Risky? As part of the update, the following changes are available in the ZIA Admin Portal:
Web Insights Logs
The following filters and columns are added to Web Insights Logs:
- Destination IP Countries
- Is Destination IP Country Risky?
- Is Source IP Country Risky?
- Source IP Countries
[See image.](#Destin_source_IP_img)
To learn more, see [Web Insights Logs: Columns](/zia/web-insights-logs-columns) and [Web Insights Logs: Filters](/zia/web-insights-logs-filters).
NSS Feeds
The following fields can be added to the Feed Output Format when configuring an NSS or Cloud NSS feed for web logs:
- `%s{srcip_country}`
- `%s{dstip_country}`
- `%s{is_src_cntry_risky}`
- `%s{is_dst_cntry_risky}`
To learn more, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs).
![Filter for Destination IP Countries and Source IP Countries](/sites/default/files/downloads/zia/dashboard-analytics/reports/about-instance-discovery-report/Filter_column_dest_source_country_risky.png)
[]

### Feature Available
#### Update to Cloud Service API
The cloud service API includes a new `POST /exportPolicies` endpoint for exporting rules configured for various policy types to JSON files.
To learn more, see the [API Reference](/zia/about-api).
The Postman collection has also been updated to include the new resource. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

## February 05, 2025
### Feature Available
#### Real-Time DLP Support for Files and Messages for Webex
Zscaler supports real-time Data Loss Prevention (DLP) for messages and file attachments sent via Webex Teams.
To learn more, see [Step-by-Step Configuration Guide for Webex Teams Real-time DLP](/zia/step-step-configuration-guide-webex-teams-real-time-dlp), [About Insights Logs](/zia/about-insights-logs), and [About SaaS Security Insights Logs](/zia/saas-security-insights-logs).

### Feature Available
#### Support for Case-Sensitive Logging for Select Domains
Zscaler supports case-sensitive URL logging for select domains. Some sites and services, such as URL shorteners, use case sensitivity within the URL path when generating links. For example, `bit.ly/ABcDEf` has a different destination URL than `bit.ly/abcdef`. With added support for case-sensitive logging, URLs are stored in Web Insights Logs and NSS feeds for web logs with the original case retained.
Case-sensitive logging is supported for, but not limited to, the following domains:
The list of domains is neither comprehensive nor complete and might expand over time. To obtain additional domains for specific use cases for case-sensitive URL support, contact your Zscaler Account team.
- adf.ly
- bit.ly
- bl.ink
- cutt.ly
- goo.gl
- link.ly
- ow.ly
- rebrand.ly
- snip.ly
- t.ly
- tiny.cc
- tinyurl.com
To learn more, see [Web Insights Logs: Columns](/zia/web-insights-logs-columns).

## January 20, 2025
### Feature Available
#### Enhancement to Posture Controls Report in Advanced SSPM
When exporting the controls report to a CSV file from the Posture page, you can view additional attributes like Description, Tenant Name, Platform, Severity, etc. in the exported file.
To learn more, see [About Posture](/zia/about-posture).

## January 13, 2025
### Feature Available
#### Enhancements to Endpoint DLP
Optical Character Recognition (OCR) Support
The Zscaler service supports OCR for Endpoint DLP to scan PNG, JPEG, TIFF, and BMP files for sensitive text data. This functionality does not require configuration and is automatically available based on whether your subscription includes the ZS-DP-CLASS-ADV SKU.
To learn more about which SKUs are available as part of your subscription, see [Viewing Tenant Details](/zia/viewing-tenant-details).
The following enhancements are made to the Endpoint Data Scan page (Analytics > Endpoint Data Scan):
Endpoint Data Scan
You can filter and export users based on sensitive data stored locally. The exported data also includes additional file attributes like the Last Modification Time, Last Accessed Time and Creation Time columns.
User Investigation
The Analytics dashboard is enhanced to display a streamlined Timeline View which shows all user activities and incidents in chronological order. You can also view additional attributes by channel type, including the vendor ID, product ID, and serial number. You can also access detailed information about other matched rules when applicable.
Device Control
Zscaler Device Control enables your organization to regulate and monitor device (removable storage devices and printers) usage by implementing device control policy rules that restrict access and mitigate security risks. This is done by intercepting as soon as the device is plugged into the endpoint, thereby preventing exfiltration of sensitive information.
To learn more, see [About Device Control](/zia/about-device-control), [Managing Removable Storage Device Rules](/zia/managing-removable-storage-rule), and [Managing Printer Rules](/zia/managing-printer-rule).
Inventory
The Inventory provides visibility into the use of removable storage devices (e.g., USB drives, external hard drives), printers, and portable devices (e.g., mobile phones and cameras) within your organization. This functionality automatically detects the usage of these devices and displays permission access based on the device control policy. You can also analyze Endpoint Data Loss Prevention (DLP) activities and incidents from various perspectives, like departments, DLP engines, AI & ML categories, file type, etc. for each device.
To learn more, see [About Inventory](/zia/about-inventory), [Analyzing Device Details](/zia/analyzing-device-details), [Analyzing Printer Details](/zia/analyzing-printer-details), and [Analyzing Portable Device Details](/zia/analyzing-portable-device-details).
Activation
From the Activation menu, you can view the activation status and activate any changes made to the Device Control Policy Rules and Endpoint Configuration Settings.
To learn more, see [Activating Device Control Policy Rules and Configuration Changes](/zia/about-policy-activation).
Configuration
The Configuration menu allows administrators to configure endpoint data scan and other endpoint settings, such as continuous classification and endpoint DLP exemption duration.
[See Image.](#endpoint_data_scan_image)
To learn more, see [Configuring Endpoint Data Scan and Endpoint Settings](/zia/about-policy-activation).
![This image shows the Endpoint Data Scan tabs](/sites/default/files/downloads/zia/policies/endpoint-data-loss-prevention/analyzing-device-details/Endpoint_data_scan_tabs.png)
[]

## January 10, 2025
### Feature Available
#### Advanced SaaS Security Posture Management Support for Zoom
You can configure Advanced SaaS Security Posture Management (SSPM) for Zoom tenants. Select the SSPM Scan checkbox when onboarding a Zoom tenant to enable the Advanced SSPM scan capability for the specific tenant. Existing users can also enable Advanced SSPM support by selecting the SSPM Scan checkbox under the onboarding section for the specific tenants and then validating and saving the changes.
[See image.](#zoomsspm)
The SSPM Scan checkbox is enabled only when you have the Advanced SSPM enabled for your tenant.
To learn more, see [About SaaS Application Tenants](/zia/about-saas-application-tenants), [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants), [Understanding the SaaS Security Posture Management Policy](/zia/understanding-saas-security-posture-management-policy), and [Viewing and Managing the Supported SSPM Policies](/zia/viewing-and-managing-supported-sspm-policies).
[]![SSPM Scan option for onboarding](/sites/default/files/downloads/zia/policies/sandbox/configuring-sandbox-policy/Adavanced%20SSPM-Zoom.png)

## January 08, 2025
### Feature in Limited Availability
#### Extranet Application Support
To access Extranet Application Support, contact your Zscaler Account team.
Zscaler Extranet Application Support provides organizations with a secure way to access resources from partners that are not using the Zscaler service. This is typically accomplished with site-to-site VPN tunnels which present organizational, financial, and security drawbacks. Zscaler Extranet Application Support provides access to partner resources through IPSec tunnels, retaining the benefits of the Zscaler Zero Trust Exchange (ZTE) without requiring partners to install hardware and software.
Extranet resources are created on the Extranet page. Each resource is configured with one or more traffic selectors and DNS servers.
[See image.](#extranet-page)
Extranet resources must be assigned to locations in order to grant users access to the partner resource. Extranet is available as a Location Type when configuring locations.
[See image.](#extranet-location)
Selecting Extranet as the Location type prompts the user to select an Extranet Resource, Traffic Selector, and DNS Server.
[See image.](#Extranet-location-settings)
After extranet locations are configured in the ZIA Admin Portal, they become available in the ZPA Admin Portal when configuring [server groups](/zpa/configuring-server-groups) and [application segments](/zpa/configuring-application-segments). You can configure [ZPA access policies](/zpa/configuring-access-policies) to manage extranet applications.
To learn more about Extranet Application Support, see [Understanding Extranet Application Support](/zia/understanding-extranet-application-support), [About Extranet](/zia/about-extranet), and [Configuring an Extranet](/zia/configuring-extranet). Ranges and limitations for Extranet Application Support are listed on [Ranges & Limitations](/zia/ranges-limitations#extranet).
Extranet Insights
With the new Extranet Insights (Analytics > Extranet Insights), you can view IPSec tunnel data, as well as monitor the health and status of your configured extranets.
[See image.](#extranet_insights)
To learn more about Extranet Insights, see [About Insights](/zia/about-insights), [About Insights Logs](/zia/about-insights-logs), [Extranet Insights Logs: Columns](/zia/extranet-insights-logs-columns), and [Extranet Insights Logs: Filters](/zia/extranet-insights-logs-filters).
Tunnel Insights Logs
A filter and column, Extranet Name, is added to Tunnel Insights Logs.
To learn more, see [Tunnel Insights Logs: Columns](/zia/tunnel-insights-logs-columns) and [Tunnel Insights Logs: Filters](/zia/tunnel-insights-logs-filters).
NSS Feeds
When configuring an NSS or Cloud NSS feed for Tunnel logs, you can select **Extranet** in the **Tunnel Type** filter to limit the logs based on this tunnel type.
[See image.](#NSS-feed-tunnel-type)
To learn more, see [Adding NSS Feeds for Tunnel Logs](/zia/adding-nss-feeds-tunnel-logs) and [Adding Cloud NSS Feeds for Tunnel Logs](/zia/adding-cloud-nss-feeds-tunnel-logs).
Update to Cloud Service API
The cloud service API includes new endpoints to configure and manage extranet resources. The following endpoints are introduced to retrieve the list of configured extranet resources and add, modify, and delete extranet resources:
- `GET /extranet`
- `POST /extranet`
- `PUT /extranet`
- `GET /extranet/lite`
- `GET /extranet/{id}`
- `DELETE /extranet/{id}`
In addition, the following attributes are added to the `Location` model to assign an extranet to a location:
- `extranet`
- `extranetIpPool`
- `extranetDns`
- `defaultExtranetTsPool`
- `defaultExtranetDns`
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection has also been updated to include new and updated resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).
[]![Image of the Extranet page in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-Extranet-page.png)
[]![Image if the Extranet Location Type in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-extranet-location-type.png)
[]![Image of the Extranet location settings in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/ZIA-location-extranet-section.png)
[]![Extranet tunnel type in Add NSS Feed window](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2024/nss-feed-tunnel-type-extranet.png)
[]![This image shows the Extranet Insights page](/sites/default/files/downloads/zia/dashboard-analytics/extranet-data-types-and-filters/Extranet_Insights.png)
