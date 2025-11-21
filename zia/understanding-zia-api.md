# Understanding ZIA APIs
Source: https://help.zscaler.com/zia/understanding-zia-api
PDF: https://help.zscaler.com/pdf/com/en/1400486.pdf

Zscaler Internet Access (ZIA) provides three APIs: the cloud service API, Sandbox Submission API, and 3rd-Party App Governance API. To learn more about authentication, making API calls, and activating configuration changes, see [Getting Started](/zia/api-getting-started). For detailed information on all available API calls, endpoints, and parameters, see the [Reference Guide](/zia/about-api). For a table summarizing all available API calls, endpoints, and rate limits, see the [API Rate Limit Summary](/zia/api-rate-limit-summary). To try out requests and responses for API calls using the Postman app, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).
[]Cloud Service API
Availability of the cloud service API is limited. To enable this API for your organization, contact Zscaler Support.
The cloud service API gives you programmatic access to the following ZIA features:
- [Activation](#Activation)
- [Admin Audit Logs](#AuditLogs)
- [Admin & Role Management](#AdminsAndRoles)
- [Advanced Settings](#AdvancedSettings)
- [Advanced Threat Protection Policy](#AdvancedThreatProtectionPolicy)
- [Alerts](#AlertsSubscription)
- [API Authentication](#APIAuthentication)
- [Authentication Settings](#auth-settings)
- [Bandwidth Control & Classes](#BandwidthCC)
- [Browser Control Policy](#Browser-control)
- [Browser Isolation](#browser-isolation)
- [Cloud Applications](#cloud-apps)
- [Cloud App Control Policy](#cloud-app-control-policy)
- [Cloud Nanolog Streaming Service (NSS)](#CloudNSS)
- [Data Loss Prevention (DLP)](#DLP)
- [Device Groups](#DeviceGroups)
- [DNS Control Policy](#DnsControlPolicy)
- [End User Notifications](#EndUserNotifications)
- [Event Logs](#EventLogs)
- [File Type Control Policy](#filetype-policy)
- [Firewall Policies](#FirewallPolicies)
- [Forwarding Control Policy](#ForwardingControlPolicy)
- [FTP Control Policy](#FTPControl)
- [Intermediate CA Certificates](#IntermediateCaCertificates)
- [IoT Report](#iot-report)
- [IPS Control Policy](#IpsControlPolicy)
- [Location Management and Traffic Forwarding](#LocationMgmt)
- [Malware Protection Policy](#MalwareProtectionPolicy)
- [Mobile Malware Protection Policy](#Mobilemp)
- [NAT Control Policy](#DNAT)
- [Organization Details](#OrganizationDetails)
- [PAC Files](#pac-files)
- [Policy Export](#PolicyExport)
- [Remote Assistance Support](#RemoteAssistanceSupport)
- [Rule Labels](#RuleLabels)
- [SaaS Security API](#Saas-security)
- [Sandbox Policy & Settings](#SandboxPolicySettings)
- [Sandbox Report](#SandboxReports)
- [Security Policy Settings](#SecurityPolicySettings)
- [Service Edges](#ServiceEdges)
- [Shadow IT Report](#ShadowITReport)
- [SSL Inspection Policy](#sslinspection-policy)
- [System Audit Report](#sysaud-rep)
- [Time Intervals](#TimeIntervals)
- [Traffic Capture Policy](#TrafficCapturePolicy)
- [URL Categories](#URLCategories)
- [URL Filtering Policy](#URLFilteringPolicy)
- [URL & Cloud App Control Policy Settings](#UrlCloudAppControlSettings)
- [User Authentication Settings](#UserAuthenticationSettings)
- [User Management](#UserManagement)
- [Workload Groups](#WorkloadGroups)
[]Sandbox Submission API
To obtain access to the Sandbox Submission API, contact your Zscaler Account team.
The Sandbox Submission API gives you programmatic access to Zscaler Sandbox, which allows you to submit files to perform behavioral analysis. By default, files are directly submitted to the Sandbox to obtain a verdict. If a verdict already exists for the file, you can optionally force the Sandbox to reanalyze the file. You can submit up to 100 raw and archive files (e.g., ZIP) per day for Sandbox analysis. To learn more about the file types supported, see [About Sandbox](/zia/about-sandbox).
The Sandbox Submission API also allows you to perform out-of-band file inspection to generate real-time verdicts. Zscaler leverages capabilities such as Malware Prevention, Advanced Threat Prevention, Sandbox cloud effect, AI/ML-driven file analysis, and integrated third-party threat intelligence feeds to inspect files and classify them as benign or malicious instantaneously. You can submit raw and archive files (e.g., ZIP), and each file is limited to a maximum size of 400 MB. All file types that are supported by the [Malware Protection policy](/zia/configuring-malware-protection-policy) and [Advanced Threat Protection](/zia/configuring-advanced-threat-protection-policy) policy are supported.
Dynamic file analysis is not included in out-of-band file inspection.
- [Reference Guide > Sandbox Submission](/zia/cloud-sandbox-submission)
- [Configuring the Sandbox Policy](/zia/configuring-sandbox-policy)
- [Configuring the Default Sandbox Rule](/zia/configuring-default-sandbox-rule)
3rd-Party App Governance API
To access the 3rd-Party App Governance API, you must have an 3rd-Party App Governance trial or license. To obtain a trial or license, contact your Zscaler Account team.
The 3rd-Party App Governance API gives you programmatic access to [Zscaler 3rd-Party App Governance](/zia/what-apptotal), which allows you to search the 3rd-Party App Governance Catalog for an application by name, app ID, or a valid URL (i.e., consent or marketplace link). If the application is not found in the catalog, it is automatically submitted to the 3rd-Party App Governance Sandbox for analysis. After analysis is complete, you can perform a subsequent search for the application and retrieve its information.
The 3rd-Party App Governance API also allows you to retrieve the list of [custom views](/zia/custom-views/) that you have configured in the 3rd-Party App Governance Admin Portal and includes all configurations that define the custom view. You can then retrieve all applications that are related to a specified custom view.
To learn more, see [Reference Guide > 3rd-Party App Governance](/zia/apptotal-api).
[]You can retrieve information about Isolation profiles.
To learn more, see:
-
[Reference Guide > Browser Isolation](/zia/browser-isolation)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with Browser Isolation permission under Policy & Components > Shared Policy Components.
- [What Is Isolation?](/isolation/what-isolation)
- [Creating Isolation Profiles for ZIA](/isolation/creating-zia-isolation-profile-isolation)
[]You can retrieve information about Cloud App Control policy rules.
To learn more, see:
-
[Reference Guide > Cloud App Control Policy](/zia/cloud-app-control-policy)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full access to URL & Cloud App Control permission under Policy & Components > Access Control. The tenant profiles API resources require full access under Administration > Tenant Profiles.
- [About Cloud App Control](/zia/about-cloud-app-control)
- [About Tenant Profiles](/zia/about-tenant-profiles)
[]You can download and export CSV-formatted admin audit log reports that include all policy changes and API calls. Audit log reports are stored for the last 6 months, and you can download reports for up to 31 days or a maximum of 1,000 records at a time.
To learn more, see:
-
[Reference Guide > Admin Audit Logs](/zia/admin-audit-logs)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Audit Logs permission under Administration Controls.
- [Admin Audit Logs Use Cases](/zia/audit-log-use-cases)
- [About Audit Logs](/zia/about-audit-logs)
[]A denylist is a list of malicious URLs to and from which Zscaler blocks all internet traffic. Zscaler provides a continuously updated global denylist, and each organization can manage a custom denylist. To retrieve or replace a denylist, use the `/security/advanced` endpoint. To add or remove individual URLs in a denylist, use the `security/advanced/blacklistUrls` endpoint.
An allowlist is a list of URLs that Zscaler exempts from security scanning. Zscaler does not provide a global allowlist, but each organization can manage a custom allowlist. A local allowlist can contain up to 255 URLs. To retrieve or replace an allowlist, use the `/security` endpoint. However, you cannot add or remove individual URLs to an allowlist using the API.
For your organization's custom denylist and allowlist, you can add up to 25K custom URLs and IPs across all categories (custom and predefined).
To learn more, see:
-
[Reference Guide > Security Policy Settings](/zia/security-policy-settings)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Advanced Threat Protection permission under Policy & Components > Security.
- [Security Policy Settings Use Cases](/zia/security-policy-settings-use-cases)
- [About Policy Enforcement](/zia/about-policy-enforcement)
- [Adding URLs to the Denylist](/zia/adding-urls-denylist)
- [Adding URLs to the Allowlist](/zia/adding-urls-allowlist)
[]The Zscaler service performs SSL inspection by acting as a full SSL proxy or a trusted man-in-the-middle (MITM) proxy. To perform SSL inspection, Zscaler needs to generate domain certificates (end-entity certificates) dynamically using a Certificate Authority (CA) issued by either Zscaler or your organization. Using Intermediate CA Certificates API resources, you can:
- Create a custom intermediate CA certificate.
- Generate a key pair.
- Generate and download a Certificate Signing Request (CSR).
- Upload a signed intermediate CA certificate and certificate chain.
- Finalize a certificate.
- Mark a certificate as default.
To learn more, see:
-
[Reference Guide > Intermediate CA Certificates](/zia/intermediate-ca-certificates)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Intermediate CA Certificates permission under Policy & Components > Decryption.
- [Intermediate CA Certificates Use Cases](/zia/intermediate-ca-certificates-use-cases)
- [SSL Inspection](/zia/about-ssl-inspection)
[]Predefined and custom URL categories provide a way to classify URLs for your organization. Using URL Categories API resources, you can:
- Add or remove a URL for a predefined URL category.
- Get information about predefined and custom categories.
- Look up the categorization of specified URLs.
- Add, update, and delete custom categories.
- Update custom categories with IP addresses and URLs.
- Find matching entries for URLs in existing custom URL categories and add related entries to a single category.
To learn more, see:
-
[Reference Guide > URL Categories](/zia/url-categories)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full permission for the respective URL Categories components under Policy & Components.
- [URL Categories Use Cases](/zia/url-categories-use-cases)
- [About URL Categories](/zia/about-url-categories)
[]Using User Management API resources, you can retrieve user, group, and department information as well as add, update, and delete users.
To learn more, see:
-
[Reference Guide > User Management](/zia/user-management)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full User Management permission under Administration Controls.
- [User Management Use Cases](/zia/user-management-use-cases)
- [About Authentication Profile](/zia/about-authentication-profile)
- [Authenticating and Managing Users](/zia/about-provisioning-authenticating-users)
[]Location Management API resources allow you to retrieve all attributes of a Zscaler service-defined location or sublocation as a request, add or update locations with VPN credentials or static IP addresses, add or update sublocations, and delete locations and sublocations. You can also retrieve an up-to-date list of countries that are used in location configuration.
To learn more, see:
-
[Reference Guide > Location Management](/zia/location-management)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Locations and VPN Credentials Management permissions under Traffic Forwarding.
- [Location Management Use Cases](/zia/location-management-use-cases)
- [About Locations](/zia/about-locations)
- [Understanding Sublocations](/zia/understanding-sublocations)
- [About VPN Credentials](/zia/about-vpn-credentials)
Getting and Updating VPN Credentials for Specific Locations
[]The Zscaler service also inspects internal traffic within an organization's corporate network using ZIA Public Service Edges or secure web gateways. Traffic forwarding is enabled through IPSec VPN tunneling, and requires that the proper user credentials are configured. Using Location Management endpoints, you can get and update VPN credentials for specific locations.
To retrieve VPN credential information for locations, use the `/vpnCredentials` endpoint. To retrieve and update individual VPN credentials for a VPN ID, use the `/vpnCredentials/{vpnId}` endpoint.
User passwords can be randomly regenerated at regular intervals (e.g., every 30 days).
To learn more, see:
-
[Reference Guide > Traffic Forwarding](/zia/traffic-forwarding-0)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full VPN Credentials Management permissions under Traffic Forwarding.
- [VPN Credentials Use Cases](/zia/vpn-credentials-use-cases)
- [About VPN Credentials](/zia/about-vpn-credentials)
- [Configuring an IPSec VPN Tunnel](/zia/configuring-ipsec-vpn-tunnel)
Managing IPSec VPN Tunnels for SD-WAN Partner Integrations
[]The API resources used to support this functionality are for SD-WAN partner use only.
A Software-Defined Wide Area Networking (SD-WAN) partner API key enables technology partner access to the [Location Management](/zia/about-api) resources and a [VPN Credentials](/zia/about-api) resource within the cloud service API. For details and SD-WAN deployment configuration guides for each partner, refer to the [SD-WAN partner site](https://www.zscaler.com/partners/technology/sd-wan) or contact Zscaler Business Development.
To learn more, see:
- [Reference Guide > Location Management](/zia/location-management)
-
[Reference Guide > Traffic Forwarding for information on the `POST /vpnCredentials` resource](/zia/traffic-forwarding-0#/vpnCredentials-post)
To make calls to Locations and VPN Credentials resources, the authenticated [SD-WAN partner API client](/zia/adding-sd-wan-partner-api-clients) must have **SD-WAN Partner Access** for their [SD-WAN partner API role](/zia/adding-sd-wan-partner-api-roles) as well as a [partner API key](/zia/configuring-sdwan-integration#AddNewKey). To learn more, see [SD-WAN API Integration for IPSec VPN Tunnel Provisioning](/zia/sd-wan-api-integration) and [Getting Started](/zia/api-getting-started).
- [SD-WAN API Integration for IPSec VPN Tunnel Provisioning](/zia/sd-wan-api-integration)
- [About Locations](/zia/about-locations)
- [About VPN Credentials](/zia/about-vpn-credentials)
- [Configuring an IPSec VPN Tunnel](/zia/configuring-ipsec-vpn-tunnel)
Getting GRE Tunnel, Static IP Address, Virtual IP Address, and Region Information
ZIA enables you to self-provision your static IP addresses or GRE tunnels to connect to the Zscaler service. Virtual IP addresses (VIPs) are used to establish IPSec VPN tunnels. The Traffic Forwarding API resources allow you to retrieve self-service GRE tunnel, static IP provisioning, data center VIP, and region-specific information.
To learn more, see:
-
[Reference Guide > Traffic Forwarding](/zia/traffic-forwarding-0)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full GRE Tunnels and Static IPs permissions and the necessary permissions for other individual components under Traffic Forwarding.
- [About Generic Routing Encapsulation](/zia/about-generic-routing-encapsulation-gre)
- [About Static IP](/zia/about-static-ip)
- [SD-WAN API Integration for IPSec VPN Tunnel Provisioning](/zia/sd-wan-api-integration)
Configuring and Managing Extranet Resources
You can configure and manage extranets that enable an organization to connect its internal network with another organization's network (e.g., partners, third-party vendors, etc.) that does not use a Zscaler service through Extranet Application Support. Extranet Application Support enables Zscaler-managed organization users to securely access extranet resources through an IPSec VPN tunnel established between a Zscaler data center and the external organization's data center, without requiring additional hardware or software installations. Using these resources, you can add, modify, and delete extranets and retrieve the list of extranets configured for your organization.
To learn more, see:
-
[Reference Guide > Traffic Forwarding](/zia/traffic-forwarding-0)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Locations and VPN Credentials Management permissions under Traffic Forwarding.
- [Understanding Extranet Application Support](/zia/understanding-extranet-application-support)
- [About Extranet](/zia/about-extranet)
- [Configuring an Extranet](/zia/configuring-extranet)
Managing Data Center Exclusion
Data Center (DC) Exclusion API resources allow you to disable the tunnels terminating at a virtual IP (VIP) address of a Zscaler DC, triggering a failover from primary to secondary tunnels in the event of service disruptions, Zscaler Trust Portal incidents, disasters, etc. This capability is supported by excluding DCs from service based on the traffic forwarding method. You can retrieve the list of Zscaler DCs that can be excluded from service to your organization and the list of DCs that are currently excluded from service based on your configured exclusions. Additionally, you can add, edit, and delete exclusions.
Currently, only the IPSec VPN tunnel forwarding method is supported for DC exclusion.
To learn more, see:
-
[Reference Guide > Traffic Forwarding](/zia/traffic-forwarding-0)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Subclouds & DC Exclusion permissions under Traffic Forwarding.
- [About Data Center Exclusion Based on Traffic Forwarding Method](/zia/about-data-center-exclusion-based-traffic-forwarding-method)
- [Excluding a Data Center Based on Traffic Forwarding Method](/zia/excluding-data-center-based-traffic-forwarding-method)
[]Sandbox Policy & Settings API resources allow you to create, read, update, and delete Sandbox policy rules via the `/sandboxRules` endpoints. In addition, these resources allow each organization to create and manage a custom blocklist of MD5 file hashes for files that go through behavioral analysis by Sandbox. To retrieve or replace the custom blocklist, use the `/behavioralAnalysisAdvancedSettings` endpoint. To retrieve quota availability information for the MD5 file hashes, use the `/behavioralAnalysisAdvancedSettings/fileHashCount` endpoint.
You can add up to 10K MD5 file hashes to your custom blocklist.
To learn more, see:
-
[Reference Guide > Sandbox Policy & Settings](/zia/sandbox-policy-settings)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Sandbox permission under Policy & Components > Security.
- [About Sandbox](/zia/about-sandbox)
- [Configuring the Sandbox Policy](/zia/configuring-sandbox-policy)
- [Add Custom File Hashes](/zia/add-custom-file-hashes)
[]Sandbox Report API resources allow you to get a full or summary [Sandbox Detail Report](/zia/viewing-sandbox-reports-data) for any file that was sent for analysis from any organization on the Zscaler cloud.
To learn more, see:
-
[Reference Guide > Sandbox Report](/zia/cloud-sandbox-report)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Sandbox permission under Policy & Components > Security.
- [Sandbox Report Use Cases](/zia/sandbox-report-use-cases)
- [About Sandbox](/zia/about-sandbox)
- [Viewing Sandbox Reports and Data](/zia/viewing-sandbox-reports-data)
[]Admin & Role Management API resources allow you to retrieve admin role information, which dictates the level of access that admins have in the ZIA Admin Portal. These resources also allow you to add, update, or delete admins within your organization. You can also retrieve information about the current administrator or auditor user accessing the API, and update and retrieve the password expiration information.
To learn more, see:
-
[Reference Guide > Admin & Role Management](/zia/admin-role-management)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Administrator Management and Role Management permissions under Administration Controls.
- [About Role Management](/zia/about-role-management)
- [About Administrators](/zia/about-administrators)
- [Configuring Password Expiration](/zia/configuring-password-expiration)
[]Data Loss Prevention (DLP) API resources allow you to retrieve information for DLP dictionaries, engines, incident receivers, Internet Content Adaptation Protocol (ICAP) servers, Cloud-to-Cloud Incident Receivers, etc. In addition, you can create and update DLP predefined dictionaries, Exact Data Match (EDM) and Indexed Document Match (IDM) dictionaries, notifications, and policy rules. You can also create and delete custom DLP engines, update predefined and custom DLP engines, and validate DLP engine expressions formed by combining DLP dictionaries using logical operators.
To learn more, see:
-
[Reference Guide > Data Loss Prevention (DLP)](/zia/data-loss-prevention)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Data Loss Prevention permission and the necessary individual policy components under Policy & Components > Data Protection.
- [About Data Loss Prevention (DLP)](/zia/about-data-loss-prevention)
- [About DLP Dictionaries](/zia/about-dlp-dictionaries)
- [About DLP Notification Templates](/zia/about-dlp-notification-templates)
- [About Exact Data Match](/zia/about-exact-data-match)
- [About Indexed Document Match](/zia/about-indexed-document-match)
- [About DLP Engines](/zia/about-dlp-engines)
- [Understanding DLP Engines](/zia/understanding-dlp-engines)
- [About Cloud-to-Cloud Incident Forwarding](/zia/about-cloud-cloud-incident-forwarding)
[]Device Groups API resources allow you to retrieve device group information. ZIA maintains a list of all the devices in your organization that have Zscaler Client Connector deployed on them. These devices are categorized under predefined groups based on their OS type.
To learn more, see:
-
[Reference Guide > Device Groups](/zia/device-groups)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with Device Management permission under Policy & Components > Shared Policy Components.
- [About Device Groups](/zia/about-device-groups)
[]Firewall Policies API resources allow you to create, read, update, and delete Firewall Filtering policy rules and their criteria.
To learn more, see:
-
[Reference Guide > Firewall Policies](/zia/firewall-policies)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Firewall Control permission under Policy & Components > Access Control. Policy resources, such as network services and network applications, can be managed with any Firewall policy permission. However, some policy objects, such as IP & FQDN groups and time intervals have separate permissions alongside the respective policy permissions.
- [Configuring Firewall Policies](/zia/configuring-firewall-policies)
[]Rule Labels API resources allow you to create labels and associate them with URL Filtering policy rules.
To learn more, see:
-
[Reference Guide > Rule Labels](/zia/rule-labels)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with the associated policy permissions.
- [About Rule Labels](/zia/about-rule-labels)
- [About URL Filtering](/zia/about-url-filtering)
[]URL Filtering Policy API resources allow you to retrieve information about and manage rules that limit your exposure to liability by managing access to web content based on a site's URL categorization.
To learn more, see:
-
[Reference Guide > URL Filtering Policy](/zia/url-filtering-policy)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full URL & Cloud App Control policy permission under Policy & Components > Access Control.
- [About URL Filtering](/zia/about-url-filtering)
[]User Authentication Settings API resources allow you to exempt URLs from cookie authentication.
To learn more, see:
-
[Reference Guide > User Authentication Settings](/zia/user-authentication-settings)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Advanced Settings permission under Administration Controls.
- [About Zscaler Cookies](/zia/about-zscaler-cookies)
[]You can generate and download CSV-formatted event log reports that include provisioning and user and group management activities performed by System for Cross-domain Identity Management (SCIM) clients. The SCIM client's activities are recorded only if the SCIM-based provisioning is enabled for users on the Zscaler service.
To learn more, see:
-
[Reference Guide > Event Logs](/zia/event-logs)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Audit Logs permission under Administration Controls.
- [About Event Logs](/zia/about-event-logs)
- [About SCIM](/zia/about-scim)
[]To make the configuration changes take effect, you must activate the changes. Activation API resources allow you to activate your configuration changes by pushing them to the Zscaler Central Authority (CA). You can also update the End User Subscription Agreement (EUSA) status and retrieve the EUSA acceptance status using these API resources.
To learn more, see:
- [Reference Guide > Activation](/zia/activation)
- [Getting Started](/zia/getting-started-zia-api)
- [Saving and Activating Changes in the ZIA Admin Portal](/zia/saving-and-activating-changes-admin-portal)
- [End User Subscription Agreement](https://www.zscaler.com/legal/end-user-subscription-agreement)
[]Authentication API resources allow you to authenticate and create an API session, check for an existing API session, and delete an API session.
To learn more, see:
- [Reference Guide > API Authentication](/zia/api-authentication)
- [Getting Started](/zia/getting-started-zia-api)
[]You can export the Shadow IT Report for the [cloud applications](/zia/about-cloud-applications) that Zscaler recognizes based on their usage in your organization. These reports include various security parameters of the cloud applications, information about users who have interacted with the applications, the list of locations from where the applications are accessed, and application usage details, as applicable.
To learn more, see:
-
[Reference Guide > Shadow IT Report](/zia/shadow-it-report-api)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with the Web Data permission under Reporting Data.
- [About Shadow IT Report](/zia/about-shadow-it-report)
- [About Application Information](/zia/about-application-information)
[]SSL Inspection Policy API resources allow you to create, update, retrieve, and delete SSL Inspection policy rules and their criteria.
To learn more, see:
-
[Reference Guide > SSL Inspection Policy](/zia/ssl-inspection-policy)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full SSL/TLS Inspection policy permission under Policy & Components > Decryption.
- [Configuring SSL Inspection Policy](/zia/configuring-ssl-inspection-policy)
- [About SSL Inspection Policy](/zia/about-ssl-inspection-policy)
[]Forwarding Control Policy API resources allow you to create, modify, retrieve, and delete forwarding rules. Additionally, these resources allow you to create, modify, retrieve, and delete Zscaler Private Access (ZPA) gateways that are used in forwarding rules for ZPA. You can also retrieve information about all proxy gateways using the Forwarding Control Policy API resources.
To learn more, see:
-
[Reference Guide > Forwarding Control Policy](/zia/forwarding-control-policy)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Forwarding Control permission and the necessary permissions for traffic forwarding components under Traffic Forwarding.
- [About Forwarding Control](/zia/about-forwarding-policies)
- [Configuring Forwarding Policy](/zia/configuring-forwarding-policy)
- [About Zscaler Private Access (ZPA) Gateway](/zia/about-zpa-gateway)
- [Configuring ZPA Gateway](/zia/configuring-zpa-gateway)
- [About Gateways for Proxies](/zia/about-gateways-proxies)
- [Configuring Gateways for Proxies](/zia/configuring-gateways-proxies)
[]Workload Groups API resources allow you to add, update, delete, and retrieve workload groups configured in the ZIA Admin Portal. The workload groups can be configured as criteria in security policies such as Data Loss Prevention, URL Filtering, SSL Inspection, and Firewall Filtering rules.
To learn more, see:
-
[Reference Guide > Workload Groups](/zia/workload-groups)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with the associated policy permissions.
- [About Workload Groups](/zia/about-workload-groups)
- [Configuring Workload Groups](/zia/configuring-workload-groups)
[]The IoT report API allows you to retrieve a list of devices (unmanaged user devices, servers, and IoT devices) that are identified by the Zscaler AI/ML engine from unauthenticated web traffic. You can also obtain the key contexts about the discovered devices, such as locations, ML auto-labels, classifications, etc. To learn more, see [Reference Guide > IoT Report](/zia/iot-report).
Access to these resources requires an [admin role](/zia/adding-admin-roles#administrators-access) with the IoT Discovery permission under Reporting Data.
[]PAC Files API resources allow you to add and manage proxy auto-configuration (PAC) files in the ZIA Admin Portal. PAC files are one of the [traffic forwarding methods](/zia/choosing-traffic-forwarding-methods) supported by Zscaler and they allow you to forward your users' web traffic to the Zscaler service. All major browsers support PAC files and browsers simply require the address of the PAC file (i.e., PAC file URL) so they can fetch the file from the specified address, execute the file contents, and forward the web traffic to Zscaler's proxy server specified in the file. PAC files can be hosted on a workstation, an internal web server, or a server outside the corporate network. The Zscaler service hosts a default PAC file that uses geolocation technology to forward traffic to the nearest ZIA Public Service Edge. You can also upload custom PAC files to the Zscaler service.
Using these API resources, you can retrieve the list of hosted PAC files, add custom PAC files, validate the PAC file content and check for errors, branch an existing PAC file to create a new version, retrieve all or specific versions of a PAC file, and delete a PAC file.
To learn more, see:
-
[Reference Guide > PAC Files](/zia/pac-files)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Hosted PAC Files permission under Traffic Forwarding.
- [About Hosted PAC Files](/zia/about-hosted-pac-files)
- [Using Custom PAC Files to Forward Traffic to ZIA](/zia/using-custom-pac-file-forward-traffic-zia)
- [Writing a PAC File](/zia/writing-pac-file)
[]Authentication Settings API resources allow you to retrieve or update your organization's default authentication settings information.
To learn more, see:
-
[Reference Guide > Authentication Settings](/zia/authentication-settings)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Authentication Settings permission under Administration Controls.
- [About Authentication Default Settings](/zia/about-authentication-default-settings)
[]Cloud Applications API resources allow you to retrieve a list of cloud applications associated with Advanced Settings, Bandwidth Classes, DLP rules, Cloud App Control rules, File Type Control rules, and SSL Inspection rules. You can also create, update, delete, and retrieve cloud application risk profiles using the Cloud Applications API resources.
To learn more, see:
-
[Reference Guide > Cloud Applications](/zia/cloud-applications)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with the associated policy permissions.
- [About Cloud Applications](/zia/about-cloud-applications)
- [About Cloud Application Risk Profile](/zia/about-cloud-application-risk-profile)
[]File Type Control Policy API resources allow you to create, update, retrieve, and delete File Type Control policy rules and their criteria. In addition, you can create, update, and delete custom file types, retrieve information about custom file types and the count of custom file types, and retrieve information about all file types that can be used as rule conditions in File Type Control and DLP policies.
To learn more, see:
-
[Reference Guide > File Type Control Policy](/zia/file-type-control-policy)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full File Type Control permission under Policy & Components > Access Control.
- [Configuring the File Type Control Policy](/zia/configuring-file-type-control-policy)
- [About File Type Control](/zia/about-file-type-control)
- [Configuring Custom File Types](/zia/configuring-custom-file-types)
[]Organization Details API resources allow you to retrieve your organization's information, including headquarter location, geolocation, address, and contact details. It also allows you to retrieve your subscriptions to the Zscaler service.
To learn more, see:
- [Reference Guide > Organization Details](/zia/organization-details)
- [About the Company Profile](/zia/about-company-profile)
- [Viewing Subscriptions](/zia/viewing-subscriptions)
[]DNS Control Policy API resources allow you to create, read, update, and delete DNS filtering rules and their criteria.
To learn more, see:
-
[Reference Guide > DNS Control Policy](/zia/dns-control-policy)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full DNS Control permission under Policy & Components > Access Control.
- [Configuring the DNS Control Policy](/zia/configuring-dns-control-policy)
[]IPS Control Policy API resources allow you to create, read, update, and delete DNS filtering rules and their criteria.
To learn more, see:
-
[Reference Guide > IPS Control Policy](/zia/ips-control-policy)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full IPS Control permission under Policy & Components > Security.
- [Configuring the IPS Control Policy](/zia/configuring-ips-control-policy)
[]These API resources allow you to update the Malware Protection policy and retrieve information about the policy configurations.
To learn more, see:
-
[Reference Guide > Malware Protection Policy](/zia/malware-protection-policy)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Malware Protection permission under Policy & Components > Security.
- [Configuring the Malware Protection Policy](/zia/configuring-malware-protection-policy)
[]These API resources allow you to update the Advanced Threat Protection policy and retrieve information about the policy configurations.
To learn more, see:
-
[Reference Guide > Advanced Threat Protection Policy](/zia/advanced-threat-protection-policy)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Advanced Threat Protection permission under Policy & Components > Security.
- [Configuring the Advanced Threat Protection Policy](/zia/configuring-advanced-threat-protection-policy)
[]These API resources allow you to update the advanced settings available for URL Filtering and Cloud App Control policies and retrieve information about the advanced settings.
To learn more, see:
-
[Reference Guide > URL & Cloud App Control Policy Settings](/zia/url-cloud-app-control-policy-settings)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with either full URL & Cloud App Control permission under Policy & Components > Access Control or full Advanced Settings permission under Administration Controls.
- [Configuring Advanced Policy Settings](/zia/configuring-advanced-policy-settings)
[]These API resources allow you to update the advanced cloud configuration settings in the ZIA Admin Portal and retrieve information about the settings.
To learn more, see:
-
[Reference Guide > Advanced Settings](/zia/advanced-settings)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Advanced Settings permission under Administration Controls.
- [Configuring Advanced Settings](/zia/configuring-advanced-settings)
[]Cloud Nanolog Streaming Service (NSS) API resources allow you to add, update, validate, and delete cloud NSS feeds, retrieve information about the feeds, test connectivity, and get feed output format. Additionally, you can create, update, and delete NSS servers, retrieve a list of registered NSS servers, and download the NSS virtual appliance information based on the specified NSS server ID using these API resources.
To learn more, see:
-
[Reference Guide > Cloud Nanolog Streaming Service (NSS)](/zia/cloud-nanolog-streaming-service-nss)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Nanolog Streaming Service permission under Cloud Configuration & Integration > Cloud Configuration.
- [Adding Cloud NSS Feeds](/zia/adding-cloud-nss-feeds)
- [About NSS Servers](/zia/about-nss-servers)
[]These API resources allow you to update Remote Assistance preferences and retrieve information about the preferences.
To learn more, see:
-
[Reference Guide > Remote Assistance Support](/zia/remote-assistance-support)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Remote Assistance Management permission under Administration Controls.
- [Enabling Remote Assistance](/zia/enabling-remote-assistance)
[]End User Notifications API resources allow you to update browser-based end user notification (EUN) configuration and also retrieve the configuration details.
To learn more, see:
-
[Reference Guide > End User Notifications](/zia/end-user-notifications)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with the respective policy permission for which the EUN is configured.
- [Understanding Browser-Based End User Notifications](/zia/understanding-browser-based-end-user-notifications)
[]Policy Export API resources allow you to export the rules configured for various policy types to JSON files. To learn more, see [Reference Guide > Policy Export](/zia/policy-export).
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with permission for the policies that need to be exported. Only policies to which the user or the API client has access are exported and other policies are excluded from the response.
[]These API resources allow you to create, update, and retrieve alert subscriptions.
To learn more, see:
-
[Reference Guide > Alerts](/zia/alerts)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full permission under Administration > Alerts.
- [About Alert Subscriptions](/zia/about-alert-subscriptions)
[]Bandwidth Control & Classes API resources allow you to create, update, delete, and retrieve Bandwidth Control policy rules and their criteria. These API resources also allow you to create, update, delete, and retrieve bandwidth classes. Bandwidth classes identify the URL categories and cloud applications to which the service allocates bandwidth. You must configure the bandwidth classes before you can reference them in the Bandwidth Control policy rules.
To learn more, see:
-
[Reference Guide > Bandwidth Control & Classes](/zia/bandwidth-control-classes)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full permission under Policy > Bandwidth Control.
- [About Bandwidth Classes](/zia/about-bandwidth-classes)
- [About Bandwidth Control](/zia/about-bandwidth-control)
[]Mobile Malware Control Policy API resources allow you to update and retrieve Mobile Malware Protection policy rules and their criteria.
To learn more, see:
-
[Reference Guide > Mobile Malware Protection Policy](/zia/mobile-malware-protection-policy)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Mobile Malware Protection permission under Policy > Mobile.
- [Understanding Mobile Malware Protection](/zia/understanding-mobile-malware-protection)
[]NAT Control Policy API resources allow you to create, update, delete, and retrieve DNAT Control policy rules and their criteria.
To learn more, see:
-
[Reference Guide > NAT Control Policy](/zia/nat-control-policy)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full NAT Control permission under Policy > Firewall Control.
- [About NAT Control](/zia/about-nat-control)
[]Time Intervals API resources allow you to create, update, and delete time intervals and retrieve a list of all configured time intervals.
To learn more, see:
-
[Reference Guide > Time Intervals](/zia/time-intervals)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with the respective policy permission for which the Time Interval is configured.
- [About Time Intervals](/zia/about-time-intervals)
[]FTP Control Policy API resources allow you to update the FTP Control settings and retrieve the FTP Control status and the list of URL categories for which FTP is allowed.
To learn more, see:
-
[Reference Guide > FTP Control Policy](/zia/ftp-control-policy)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full FTP Control permission under Policy > Access Control.
- [About FTP Control](/zia/about-ftp-control)
[]System Audit Report API resources allow you to retrieve various configuration audit reports, such as System Audit Report, PAC File Audit Report, and IP Visibility Audit Report.
To learn more, see:
-
[Reference Guide > System Audit Report](/zia/system-audit-report)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full permission under Analytics > System Audit Report.
- [About the System Audit Report](/zia/about-system-audit-report)
[]ZIA Virtual Service Edge API resources allow you to create, update, and delete Virtual Service Edge clusters and retrieve a list of Virtual Service Edge clusters.
To learn more, see:
-
[Reference Guide > Service Edges](/zia/service-edges)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with respective permission under Administration > Cloud Configuration.
- [About Virtual Service Edge Clusters](/zia/about-virtual-service-edge-clusters)
[]Browser Control Policy API resources allow you to update the Browser Control settings and retrieve the Browser Control status and list of configured browsers.
To learn more, see:
-
[Reference Guide > Browser Control Policy](/zia/browser-control-policy)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full permission under Policy > Secure Browsing.
- [Configuring the Browser Control Policy](/zia/configuring-browser-control-policy)
[]SaaS Security API resources allow you to create, update, and delete the SaaS Security Data at Rest Scanning Data Loss Prevention (DLP) and Malware Detection rules. You can also retrieve all the SaaS Security Data at Rest Scanning DLP and Malware Detection rules using the SaaS Security API resources.
To learn more, see:
-
[Reference Guide > SaaS Security API](/zia/saas-security-api)
Access to these resources requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full permission under Policy > SaaS Security.
- [About Data at Rest Scanning DLP](/zia/about-data-rest-scanning-dlp)
- [About Data at Rest Scanning Malware Detection](/zia/about-data-rest-scanning-malware-detection)
[]Traffic Capture Policy API resources allow you to create, update, and delete Traffic Capture policy rules as well as retrieve information for all or specific rules. In addition, they allow you to retrieve the rule count, rule order information, and rule label associations.
To learn more, see:
-
[Reference Guide > Traffic Capture Policy](/zia/traffic-capture-policy)
Access to this resource requires an [admin](/zia/adding-admin-roles#administrators-access) or [API role](/zia/adding-api-roles#administrators-access) with full Traffic Capture permission under Traffic Forwarding > Traffic Forwarding Components > Traffic Capture.
- [About Traffic Capture Policy](/zia/about-traffic-capture-policy)
- [Configuring the Traffic Capture Policy](/zia/configuring-traffic-capture-policy)