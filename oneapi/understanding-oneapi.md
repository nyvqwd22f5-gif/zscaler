# Understanding OneAPI
Source: https://help.zscaler.com/oneapi/understanding-oneapi
PDF: https://help.zscaler.com/pdf/com/en/1497101.pdf

Zscaler OneAPI provides programmatic access to different Zscaler services with consistency in API design and experience across all products, reliability, and high performance of the APIs. Zscaler OneAPI allows for a centralized management of key components and features of APIs, including but not limited to API authentication, tenant access policies and management, rate limiting, caching, API lifecycle management, etc., thereby providing a consistent and uniform cross-product API experience and offering enhanced support for automation and integration with external services.
To access OneAPI, contact your Zscaler Account team.
Before using the APIs, Zscaler recommends reviewing [Getting Started](/oneapi/getting-started) for information regarding prerequisites, authentication, and how to make API calls. For detailed information on all available API calls, endpoints, and parameters, see the Reference Guides listed in [Understanding OneAPI Endpoints](/oneapi/understanding-oneapi-endpoints). For a summary of the rate limits used by the endpoints, see [Understanding Rate Limiting](/oneapi/understanding-rate-limiting). To try out requests and responses for API calls using the Postman application, see [Configuring the Postman REST API Client](/oneapi/configuring-postman-rest-api-client).
Zscaler can make periodic updates to the request and response parameters used by OneAPI endpoints. If you encounter any issues with using the API endpoints, contact Zscaler Support.
The following sections provide information on features across different Zscaler services that you can access and manage using OneAPI.
ZIA API
Zscaler Internet Access (ZIA) API endpoints give you programmatic access to manage the following ZIA features:
- [Activation](#Activation)
- [Admin Audit Logs](#AuditLogs)
- [Admin and Role Management](#AdminsAndRoles)
- [Isolation](#BrowserIsolation)
- [Data Loss Prevention (DLP)](#DLP)
- [Device Groups](#DeviceGroups)
- [Event Logs](#EventLogs)
- [Firewall Policies](#FirewallPolicies)
- [Forwarding Control Policy](#ForwardingControlPolicy)
- [Intermediate CA Certificates](#IntermediateCaCertificates)
- [IoT Report](#IoTReport)
- [Location Management and Traffic Forwarding](#LocationMgmt)
- [Rule Labels](#RuleLabels)
- [Sandbox Report](#SandboxReports)
- [Sandbox Settings](#CloudSandboxSettings)
- [Security Policy Settings](#SecurityPolicySettings)
- [Shadow IT Report](#ShadowITReport)
- [URL Categories](#URLCategories)
- [URL Filtering Policies](#URLFilteringPolicies)
- [User Authentication Settings](#UserAuthenticationSettings)
- [User Management](#UserManagement)
- [Workload Groups](#WorkloadGroups)
ZPA API
Zscaler Private Access (ZPA) API endpoints give you programmatic access to manage the following ZPA features:
- [Alternative Cloud Domains](#altClouds)
- [Application Segments](#appsegments)
- [Segment Groups](#segmentgrps)
- [App Connectors](#AppConnectors)
- [App Connector Groups](#AppConnectorGroups)
- [Certificates](#Certificates)
- [Cloud Connector Groups](#CloudConnectorGroups)
- [Customers](#Customers)
- [Emergency Access](#EmergencyAccess)
- [Enrollment Certificates](#EnrollmentCertificates)
- [IdP Configurations](#IdPConfigurations)
- [Isolation Profiles](#IsolationProfiles)
- [Access Policies](#accesspolicy)
- [Client Forwarding Policies](#clientforwardingpolicy)
- [Timeout Policies](#timeoutpolicy)
- [AppProtection Policies](#inspectionPolicy)
- [Isolation Policies](#IsolationPolicies)
- [Privileged Policies](#PrivilegedPolicies)
- [Redirection Policies](#RedirectionPolicies)
- [Log Streaming Service (LSS) Configurations](#LSSConfigurations)
- [Machine Groups](#MachineGroups)
- [Microtenants](#Microtenants)
- [Posture Profiles](#PostureProfiles)
- [Privileged Approvals](#PrivilegedApprovals)
- [Privileged Consoles](#PrivilegedConsoles)
- [Privileged Credentials](#PrivilegedCredentials)
- [Privileged Portals](#PrivilegedPortals)
- [Provisioning Keys](#ProvisioningKeys)
- [SAML Attributes](#SAMLAttributes)
- [SCIM Attributes](#SCIMAttributes)
- [SCIM Groups](#SCIMGroups)
- [Servers](#appservers)
- [Server Groups](#servergrps)
- [Service Edges](#ServiceEdges)
- [Service Edge Groups](#ServiceEdgeGroups)
- [Trusted Networks](#TrustedNetworks)
- [Version Profiles](#VersionProfiles)
Zscaler Client Connector API
Zscaler Client Connector API endpoints give you programmatic access to manage the following Zscaler Client Connector features:
- [Devices](#PublicController)
Zscaler Cloud & Branch Connector API
Cloud & Branch Connector API endpoints give you programmatic access to the following Cloud & Branch Connector features:
- [Activation](#activation)
- [Admin & Role Management](#adminrolemanagement)
- [Authentication](#authentication)
- [Cloud & Branch Connector Groups](#cloudandbranchconnectorgroups)
- [Forwarding Gateways](#ForwardingGateways)
- [Location Management](#locationmanagement)
- [Partner Integrations](#cloud&branchpartnerintegrations)
- [Policy Management](#PolicyManagement)
- [Policy Resources](#PolicyResources)
- [Provisioning](#provisioning)
ZDX API
Zscaler Digital Experience (ZDX) API endpoints give you programmatic access to manage the following ZDX features:
- [Authentication](#zdx-authentication)
- [Administration](#zdx-administration)
- [Alerts](#zdx-alerts)
- [Inventory](#zdx-inventory)
- [Reports](#zdx-reports)
- [Troubleshooting](#zdx-troubleshooting)
If you are using ZDX API, be aware of the caveats:
- [Inconsistency in data](#zdx-inconsistency)
- [Delay in data](#zdx-delay)
- [ZDX Score value of -1](#ZDX-Score)
ZIdentity API
ZIdentity API endpoints give you programmatic access to manage the following ZIdentity features:
- [API Clients](#zid-api-client)
- [Users](#zid-users)
- [Resource Servers](#zid-resource-servers)
- [Groups](#zid-groups)
[]You can retrieve information about isolation profiles.
[]You can download and export CSV-formatted admin audit log reports that include all policy changes and API calls. Audit log reports are stored for the last 6 months, and you can download reports for up to 31 days or a maximum of 1,000 records at a time.
[]A denylist is a list of malicious URLs to and from which Zscaler blocks all internet traffic. Zscaler provides a continuously updated global denylist, and each organization can manage a custom denylist. To retrieve or replace a denylist, use the `/security/advanced` endpoint. To add or remove individual URLs in a denylist, use the `security/advanced/blacklistUrls` endpoint.
An allowlist is a list of URLs that Zscaler exempts from security scanning. Zscaler does not provide a global allowlist, but each organization can manage a custom allowlist. A local allowlist can contain up to 255 URLs. To retrieve or replace an allowlist, use the `/security` endpoint. However, you cannot add or remove individual URLs to an allowlist using the API.
For your organization's custom denylist and allowlist, you can add up to 25K custom URLs and IP addresses across all categories (custom and predefined).
[]The Zscaler service performs SSL inspection by acting as a full SSL proxy or a trusted man-in-the-middle (MITM) proxy. To perform SSL inspection, Zscaler must generate domain certificates (end-entity certificates) dynamically using a Certificate Authority (CA) issued by either Zscaler or your organization. Using Intermediate CA Certificates API resources, you can:
- Create a custom intermediate CA certificate.
- Generate a key pair.
- Generate and download a Certificate Signing Request (CSR).
- Upload a signed intermediate CA certificate and certificate chain.
- Finalize a certificate.
- Mark a certificate as default.
[]Predefined and custom URL categories provide a way to classify URLs for your organization. Using URL Categories API resources, you can:
- Add or remove a URL for a predefined URL category.
- Get information about predefined and custom categories.
- Look up the categorization of specified URLs.
- Add, update, and delete custom categories.
- Update custom categories with IP addresses and URLs.
- Find matching entries for URLs in existing custom URL categories and add related entries to a single category.
[]With User Management API resources, you can retrieve user, group, and department information, as well as add, update, and delete users.
[]Location Management API resources allow you to retrieve all attributes of a Zscaler service-defined location or sublocation as a request, add or update locations with VPN credentials or static IP addresses, add or update sublocations, and delete locations and sublocations.
Getting and Updating VPN Credentials for Specific Locations
[]The Zscaler service also inspects internal traffic within an organization's corporate network using ZIA Public Service Edges or secure web gateways. Traffic forwarding is enabled through IPSec VPN tunneling, and requires that the proper user credentials are configured. Using Location Management endpoints, you can obtain and update VPN credentials for specific locations.
To retrieve VPN credential information for locations, use the `/vpnCredentials` endpoint. To retrieve and update individual VPN credentials for a VPN ID, use the `/vpnCredentials/{vpnId}` endpoint.
User passwords can be randomly regenerated at regular intervals (e.g., every 30 days).
Managing IPSec VPN Tunnels for SD-WAN Partner Integrations
[]The API resources used to support this functionality are for SD-WAN partner use only.
A Software-Defined Wide Area Network (SD-WAN) partner API key enables technology partner access to the Location Management resources and a VPN Credentials resource within the cloud service API. For details and SD-WAN deployment configuration guides for each partner, see the [SD-WAN partner site](https://www.zscaler.com/partners/technology/sd-wan) or contact your Zscaler Account team.
Getting GRE Tunnel, Static IP Address, Virtual IP Address, and Region Information
ZIA enables you to self-provision your static IP addresses or GRE tunnels to connect to the Zscaler service. Virtual IP addresses (VIPs) are used to establish IPSec VPN tunnels. The Traffic Forwarding API resources allow you to retrieve self-service GRE tunnel, static IP provisioning, data center VIP, and region-specific information.
[]Sandbox Settings API resources allow each organization to create and manage a custom blocklist of MD5 file hashes for files that go through behavioral analysis by Sandbox. To retrieve or replace the custom blocklist, use the `/behavioralAnalysisAdvancedSettings` endpoint. To retrieve quota availability information for the MD5 file hashes, use the `/behavioralAnalysisAdvancedSettings/fileHashCount` endpoint.
You can add up to 10K MD5 file hashes to your custom blocklist.
[]Sandbox Report API resources allow you to get a full or summary Sandbox Detail Report for any file that was sent for analysis from any organization on the Zscaler cloud.
[]Admin & Role Management API resources allow you to retrieve admin role information, which dictates the level of access that admins have in the ZIA Admin Portal. These resources also allow you to add, update, or delete admins within your organization.
[]Data Loss Prevention (DLP) API resources allow you to retrieve information for DLP dictionaries, engines, incident receivers, Internet Content Adaptation Protocol (ICAP) servers, etc. In addition, you can create and update DLP predefined dictionaries, Exact Data Match (EDM) and Indexed Document Match (IDM) dictionaries, notifications, and policy rules. You can also create and delete custom DLP engines, update predefined and custom DLP engines, and validate DLP engine expressions formed by combining DLP dictionaries using logical operators.
[]Device Groups API resources allow you to retrieve device group information. ZIA maintains a list of all devices in your organization that have Zscaler Client Connector deployed on them. These devices are categorized under predefined groups based on their OS type.
[]Firewall Policies API resources allow you to create, read, update, and delete Firewall Filtering policy rules and their criteria.
[]Rule Labels API resources allow you to create labels and associate them with URL Filtering policy rules.
[]URL Filtering Policies API resources allow you to retrieve information about and manage rules that limit your exposure to liability by managing access to web content based on a site's URL categorization.
[]User Authentication Settings API resources allow you to exempt URLs from cookie authentication.
[]You can generate and download CSV-formatted event log reports that include provisioning and user and group management activities performed by System for Cross-domain Identity Management (SCIM) clients. The SCIM client's activities are recorded only if SCIM-based provisioning is enabled for users on the Zscaler service.
[]For the configuration changes to take effect, you must activate the changes. Activation API resources allow you to activate your configuration changes by pushing them to the Central Authority (CA).
[]You can export the Shadow IT Report for the cloud applications that Zscaler recognizes based on their usage in your organization. These reports include various security parameters of the cloud applications, information about users who have interacted with the applications, the list of locations from where the applications are accessed, and application usage details, as applicable.
[]Forwarding Control Policy API resources allow you to create, modify, retrieve, and delete forwarding rules. Additionally, these resources allow you to create, modify, retrieve, and delete Zscaler Private Access (ZPA) gateways that are used in forwarding rules for ZPA.
[]Workload Groups API resources allow you to retrieve information about the workload groups configured in the ZIA Admin Portal. The workload groups can be configured as criteria in security policies such as DLP, URL Filtering, SSL Inspection, and Firewall Filtering rules.
[]The IoT Report API allows you to retrieve a list of devices (unmanaged user devices, servers, and IoT devices) that are identified by the Zscaler AI/ML engine from unauthenticated web traffic. You can also obtain the key contexts about the discovered devices, such as locations, ML auto-labels, classifications, etc.
[]Alternative Cloud Domain API resources allow you to read alternative cloud domains.
[]Application Segment API resources allow you to create, read, update, and delete application segments.
[]Segment Group API resources allow you to create, read, update, and delete segment groups.
[]Server API resources allow you to create, read, update, and delete servers.
[]Server Group API resources allow you to create, read, update, and delete server groups.
[]App Connector API resources allow you to read, update, and delete App Connectors.
[]App Connector Group API resources allow you to create, read, update, and delete App Connector groups.
[]Certificate API resources allow you to create, read, update, and delete certificates.
[]Cloud Connector Group API resources allow you to read Cloud Connector groups.
[]Customer API resources allow you to read authentication domains for a customer.
[]Emergency Access API resources allow you to create, read, update, and delete emergency access users.
[]Enrollment Certificate API resources allow you to read enrollment certificates.
[]IdP Configuration API resources allow you to read IdP configurations.
[]Isolation Profiles API resources allow you to read isolation profiles.
[]Policy Set Controller API resources allow you to create, read, update, and delete access policies.
[]Policy Set Controller API resources allow you to create, read, update, and delete client forwarding policies.
[]Policy Set Controller API resources allow you to create, read, update, and delete timeout policies.
[]Policy Set Controller API resources allow you to create, read, update, and delete AppProtection policies.
[]Policy Set Controller API resources allow you to create, read, update, and delete isolation policies.
[]Policy Set Controller API resources allow you to create, read, update, and delete privileged credential policies.
[]Policy Set Controller API resources allow you to create, read, update, and delete redirection policies.
[]LSS Configuration API resources allow you to create, read, update, and delete LSS configurations.
[]Machine Group API resources allow you to read machine groups.
[]Microtenant API resources allow you to create, read, update, and delete Microtenants.
[]Posture Profile API resources allow you to read posture profiles.
[]Privileged Approval API resources allow you to create, read, update, and delete privileged approvals.
[]Privileged Console API resources allow you to create, read, update, and delete privileged consoles.
[]Privileged Credential API resources allow you to create, read, update, and delete privileged credentials.
[]Privileged Portal API resources allow you to create, read, update, and delete privileged portals.
[]Provisioning Key API resources allow you to create, read, update, and delete provisioning keys.
[]SAML Attribute API resources allow you to read SAML attributes.
[]SCIM Attribute API resources allow you to read SCIM attributes.
[]SCIM Group API resources allow you to read SCIM groups.
[]ZPA Private Service Edge API resources allow you to read, update, and delete ZPA Private Service Edges.
[]ZPA Private Service Edge Group API resources allow you to create, read, update, and delete ZPA Private Service Edge groups.
[]Trusted Network API resources allow you to read trusted networks.
[]Version Profile API resources allow you to read version profiles.
[]Devices API resources allow you to retrieve a list of devices, their basic details, OTP single-use passwords and app profile passwords for a device, etc.
[]Authentication API resources allow you to check whether the API is authenticated and retrieve other related information.
You can only check your API authentication status using this resource (via GET `/auth`). POST and DELETE operations of the authentication endpoint are not applicable in OneAPI. To learn about API client authentication, see [Getting Started](/oneapi/getting-started).
[]Activation API resources allow you to activate your configuration changes by pushing them to the Central Authority (CA). In order for any configuration changes to take effect, the Zscaler service requires you to activate the changes.
[]Admin & Role Management API resources allow you to retrieve admin user and role information to configure the level of access admins have in the Zscaler Cloud & Branch Connector Admin Portal and API. These resources also allow you to add, update, or delete admins within your organization.
[]Cloud & Branch Connector group API resources allow you to apply policies to a group of deployed Cloud & Branch Connectors. They also make it easy to upgrade Cloud & Branch Connectors belonging to the same group to maintain redundancy while upgrades are being executed.
[]Location Management API resources allow you to retrieve location, such as IP address and VPN information, and location template information. These resources also allow you to create, update, and delete location templates.
[]Partner Integrations API resources allow you to retrieve Amazon Web Services (AWS) accounts and AWS account group information. These resources also allow you to create, update, and delete AWS accounts and account groups. Additionally, you can retrieve other AWS information, such as the CloudFormation template URL and a list of AWS regions supported for workload discovery settings (WDS).
[]Provisioning API resources allow you to retrieve information about provisioning templates and public cloud account details (for Cloud Connector).
API key-related operations included in these resources (via `/apiKeys`) are not applicable in OneAPI.
[]Policy Management API resources allow you to create and update traffic forwarding rules and retrieve the list of available rules and the count of rules using the following endpoints.
[]Policy Resources API endpoints allow you to create and manage specific objects used in policy configuration, such as IP & FQDN groups, network services, and ZPA application segments.
[]Forwarding Gateways API resources allow you to retrieve the list of available ZPA application segments.
[]Authentication API generates a bearer token for access to ZDX API.
[]Reports API retrieves ZDX Scores for applications and specific device health metrics and events.
Most Report API endpoints require a 2-hour time range to provide 2 hours of data. If more data is required for a longer duration, another request with a different 2-hour time frame must be sent. For example, you cannot send an API request from 12:00 PM to 4:00 PM as this exceeds 2 hours. You must send an API request with a time range from 12:00 PM to 2:00 PM and another one from 2:00 PM to 4:00 PM.
The endpoint, `/devices/{deviceid}/events`, does not require a time range.
[]Administration API retrieves a list of the active locations and departments for a tenant.
[]Alerts API retrieves alert details such as device, application, network performance, and ZDX Score.
Some Alert API endpoints require a 2-hour time range to provide 2 hours of data. If more data is required for a longer duration, another request with a different 2-hour time frame must be sent. For example, you cannot send an API request from 12:00 PM to 4:00 PM as this exceeds 2 hours. You must send an API request with a time range from 12:00 PM to 2:00 PM and another one from 2:00 PM to 4:00 PM.
The following endpoints do not require a time range:
- `/alerts/{alert_id}`
- `/alerts/{alert_id}/affected_devices`
[]Troubleshooting API starts a deep tracing session on a specific user and their respective device.
[]Inventory API retrieves the distribution of software information across your organization.
[]The data returned by the ZDX API might not exactly match the data on the ZDX UI. The difference between the data is a marginal 2% because the aggregated metrics compute using approximate functions. The ZDX API does this to maximize performance. For example, the Page Fetch Time (PFT) for a Web probe on the ZDX UI is 89ms while the API shows PFT as 90ms.
[]Zscaler Client Connector collects all the telemetry and reporting. This can cause a delay from collection to reporting, which is estimated to be 20 minutes. To get the full data for one hour, ensure that you use the correct timestamp and adjust for this delay.
[]If you receive a ZDX Score of -1 on the ZDX API, then there is no data available.
[]API Client API resources allow you to create, retrieve, update, and delete API clients.
[]Users API resources allow you to create, retrieve, update, and delete users. The APIs allow you to assign admin or service entitlements to the users.
[]Resource Servers API resources allow you to retrieve a list of resource servers. Resource servers or API resources refer to the Zscaler APIs available via the OneAPI gateway.
[]Groups API resources allow you to create, retrieve, update, and delete groups. The APIs allow you to assign multiple users to the Zscaler services.