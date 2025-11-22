# Ranges & Limitations
Source: https://help.zscaler.com/unified/ranges-limitations
PDF: https://help.zscaler.com/pdf/com/en/1492411.pdf

This article lists the ranges and limitations of rules, policies, fields, and other features. All values are per organization unless noted otherwise.
- [Digital Experience Monitoring Ranges and Limitations](#digital-experience)
- [Internet & SaaS Ranges and Limitations](#internet-saas)
- [Private Applications Ranges and Limitations](#private-applications)
- [Cloud & Branch Connector Ranges and Limitations](#cloud-branch)
- [ZIdentity Ranges and Limitations](#Zidentity-ranges-&-limitations)
[]
[]Alerts
The following table shows the ranges and limitations for [Alerts](/unified/administration/digital-experience-monitoring/alerts) settings:
| **Feature** | **Standard** | **Microsoft 365** | **Advanced** | **Advanced Plus** |
| ----------- | ------------ | ----------------- | ------------ | ----------------- |
| Total Alerts | 512 | 512 | 512 | 512 |
| Total Active Alerts (Alerts with Incident Correlation) | Up to 3 | 10 | 25 | 100 |
| Total Alert Rules | Up to 3 | 10 | 25 | 100 |
| Dynamic Alerting | Not supported | Not supported | Supported | Supported |
[]Analytics
The following table shows the support settings for [Analytics](/unified/analytics/digital-experience-monitoring):
| **Feature** | **Standard** | **Microsoft 365** | **Advanced** | **Advanced Plus** |
| ----------- | ------------ | ----------------- | ------------ | ----------------- |
| Hop View (Granular Expanded Cloud Path) | Supported | Supported | Supported | Supported |
| Software and Device Inventory | Not supported | Not supported | Supported | Supported |
| Process Inventory | Not supported | Not supported | Not supported | Supported |
| Software Patch Inventory | Supported | Supported | Supported | Supported |
| UCaaS Monitoring | Not supported | Microsoft Teams Call Quality (only) | Supported | Supported |
| UCaaS Monitoring (tenant limit) | Not supported | 40 | 40 | 40 |
| Root Cause Analysis | Not supported | Not supported | Supported | Supported |
| System-Generated Reports | Not supported | Not supported | Supported | Supported |
| Incidents | Not supported | Not supported | Not supported | Supported |
| Digital Experience Monitoring Snapshots | Not supported | Not supported | Supported | Supported |
| Self Service | Not supported | Not supported | Not supported | Supported |
| Data Explorer Views | Not supported | Not supported | 30 | 100 |
| Data Explorer Applications | Not supported | Not supported | 1 | 4 |
| Data Explorer Metrics | Not supported | Not supported | 1 | 4 |
| Wi-Fi | Not supported | Not supported | Supported | Supported |
| Hosted Monitoring* | Supported only as add-on | Supported only as add-on | Supported only as add-on | 1 probe per 1,000 users for each hosted location |
*Identical ranges and limitations across add-ons for Standard, Microsoft 365, and Advanced subscriptions.
[]Applications and Probes
The following table shows the ranges and limitations for [Applications and Probes](/unified/policies/digital-experience-monitoring/configuration) settings:
| **Feature** | **Standard** | **Microsoft 365** | **Advanced** | **Advanced Plus** |
| ----------- | ------------ | ----------------- | ------------ | ----------------- |
| Total Number ofInternet Web Applications | 512 | 512 | 512 | 512 |
| Active Applications (per tenant) | 3 | 7 | 30 | 100 |
| Active Probes (per user) | 3 | 7 | 30 | 30 |
| Total Number of Cloud Pathand Web Monitoring Probes | 512 | 512 | 512 | 512 |
| Active Probes | 6 | 13 | 30 | 100 |
| Probing Interval | 15 minutes | 5 minutes | 5 minutes | 5 minutes |
| Page Fetch Time Server Redirects | Not supported | Not supported | Not supported | Supported |
| Autosense (Webex Call Quality) | Not supported | Not supported | Supported | Supported |
| Autosense (Zoom Call Quality) | Not supported | Not supported | Supported | Supported |
| Autosense (Microsoft Teams Call Quality) | Not supported | Supported | Supported | Supported |
[]Diagnostics
The following table shows the ranges and limitations for [Diagnostics](/unified/analytics/digital-experience-monitoring/diagnostics) settings:
| **Feature** | **Standard** | **Microsoft 365** | **Advanced** | **Advanced Plus** |
| ----------- | ------------ | ----------------- | ------------ | ----------------- |
| Total Diagnostics Sessions | Not supported | 25 | 25 | 100 |
| Total Active Sessions | Not supported | 25 | 25 | 100 |
[]Integrations and Data Retention
The following table shows the ranges and limitations for Integrations and Data Retention settings:
| **Feature** | **Standard** | **Microsoft 365** | **Advanced** | **Advanced Plus** |
| ----------- | ------------ | ----------------- | ------------ | ----------------- |
| Webhooks | Not supported | 10 | 10 | 50 |
| Digital Experience Monitoring APIs | Not supported | Supported for Microsoft 365 events | Supported | Supported |
| Query LimitData Retention | 2 days | 14 days | 14 days | 14 days |
| Query LimitTime Span Selection Range | 2 to 24 hours | 2 to 48 hours | 2 to 48 hours | 2 to 48 hours |
| Digital Experience Monitoring Snapshots | Not supported | Not supported | 90 days | 90 days |
| Copilot | Not supported | Not supported | Not supported | Supported |
[]Organization
Following are the organization ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Admin Users per Organization | 10K adminsAdmin users can reside in Internet & SaaS or Private Applications. |
| Active Admins | 255 active adminsAdmins connected to the cloud are considered active admins. |
[]
[]Active Directory & OpenLDAP Synchronization
Following are the Active Directory (AD) and OpenLDAP synchronization ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Primary/Secondary Directory Name | 255 characters |
| Authentication Agent URL | 1,023 characters |
| Directory Server Address | 1,023 characters |
| Port | 0–65,535 ports |
| Bind DN | 255 characters |
| Bind Password | 255 characters |
| Base DN | 1,023 characters |
| User Login | 255 characters |
| User Full Name | 255 characters |
| User Search Filter | 1,023 bytes |
| Department Membership | 255 characters |
| Group Name | 255 characters |
| Group Membership (AD only) | 255 characters |
| Group Search Filter | 1,023 bytes |
| Group Base DN (OpenLDAP only) | 255 characters |
| User Attribute (OpenLDAP only) | 255 characters |
| User Membership (OpenLDAP only) | 255 characters |
| User Entry | 1,023 characters |
| Users/Groups/Departments Search (Synchronization Results) | 255 characters |
| User Authentication Filter | 1,023 bytes |
| Test User Login | 255 characters |
| Test User Password | 255 characters |
[]Advanced Threat Protection
Following is the blocked malicious URLs limitation:
| Feature | Limit |
| ------- | ----- |
| Blocked Malicious URLs | 25K FQDNs, domains, or URLs |
[]Data Loss Prevention
Following are the Data Loss Prevention (DLP) ranges and limitations:
-
-
-
-
| Feature | Limit |
| ------- | ----- |
| Custom DLP Dictionaries | 801 dictionaries (with DLP Dictionary Expansion enabled)160 dictionaries (with DLP Dictionary Expansion disabled) |
| Custom DLP Parent Dictionaries | 64 dictionaries |
| Custom DLP Sub-Dictionaries | 63 per parent dictionary |
| Custom DLP Engines | 480 engines (with DLP Engine Expansion enabled)58 engines (with DLP Engine Expansion disabled) |
[]Departments
Following are the department ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Departments per Organization | 140K departments |
| Departments per admin with Department Scope | 2,048 departments |
| Department Name | 128 characters |
| Comments | 10,240 KB |
| Imported Departments per CSV file | 3,000 entries |
[]EUNs
Following are the EUN ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Custom Messages for Zscaler Client Connector-Based EUNs | 64 custom messages |
| Notification Message Length for Zscaler Client Connector-Based EUNs | 500 characters |
| Custom Redirect URL | 1,023 characters |
| Notification Message | 15K bytes |
| AUP Message | 30K bytes |
| URL Categorization Notification | 15K bytes |
| Security Violation Notification | 15K bytes |
| DLP Violation Notification | 15K bytes |
| Caution Notification Text | 15K bytes |
| Support Phone Number | 20 characters |
| Policy Link | 1,023 characters |
| IT Support Email | 254 characters |
[]Extranet
Following are the extranet ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Extranet resources | 1,000 extranets |
| Extranet locations | 5,000 extranet locations |
| Traffic selectors per extranet | 16 traffic selectors |
| DNS servers per extranet | 16 DNS servers |
[]Groups
Following are the group ranges and limitations:
[](#other)
| Feature | Limit |
| ------- | ----- |
| Group Name | 128 characters or 127 bytes |
| Comments | 10,240 bytes |
| Imported Groups per CSV file | 3,000 entries |
| Network Services Groups | 121 groups |
| Network Applications Groups | 126 groups |
| Source IP Address Groups | 4,000 groups |
| Destination Groups (Destination IP or FQDN Groups) | 4,000 groups |
| FQDNs or IP Address Entries per Group | 8,000 IP address entriesThe total number of IP entries across groups must adhere to the overall base IP limit, as noted in the Other section. |
HTTP Header Control
The following are the HTTP Header Control ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| HTTP headers per HTTP Header Profile | 16 HTTP headers |
| HTTP header profiles per Rule | 16 HTTP header profiles |
| HTTP headers per HTTP Header Insertion Profile | 16 HTTP headers |
| HTTP header insertion profiles per Rule | 16 HTTP header insertion profiles |
| HTTP header (Key) | Up to a maximum of 128 characters. |
| Value | Up to a maximum of 1,024 characters. |
[]Locations
Following are the location ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Locations and Sublocations per Organization | 32K locationsContact Zscaler Support for a possible increase in this limit from 32K locations to 64K locations. |
| Sublocations per Location | 2,000 sublocations |
| IP Address Ranges per Sublocation | 2,000 IP address ranges |
| Scopes per Workload traffic type Sublocations |  |
| Namespace Scope per Sublocation10 scope values | 10 scope values |
| Account Scope per Sublocation | 10 scope values |
| VPC Scope per Sublocation | 50 scope values |
| VPC Endpoint Scope per Sublocation | 50 scope values |
| Location Name | 128 characters |
| Location State | 128 characters |
| Location Groups per Organization | 256 groups |
| Locations and Sublocations per Group | 32K locationsContact Zscaler Support for a possible increase in this limit from 32K locations to 64K locations. |
| Imported Locations per CSV file | 1,000 entries |
| Download CSV file | One file per hour |
[]NSS
Following are the Nanolog Streaming Service (NSS) ranges and limitations:
| Feature | Limit | Comments |
| ------- | ----- | -------- |
| Number of Users per NSS Feed Filter | 1,024 users |  |
| Number of Departments per NSS Feed Filter | 1,024 departments |  |
| Number of Locations per NSS Feed Filter | 1,024 locations |  |
| Number of Clients per NSS Feed Filter | 1,024 clients |  |
| Number of Threat Names per NSS Feed Filter | 1,024 threat names |  |
| Number of Web Transactions per Nanolog Cluster | 1 billion web transactions | If your organization surpasses more than 1 billion web transactions, additional Nanolog clusters are required. |
| Number of Nanolog Clusters per NSS Virtual Machine (VM) Server | 1 Nanolog cluster | If additional Nanolog clusters are required, your organization must support an adequate number of NSS VM servers. |
[]Organization
Following are the organization ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Address Line 1 | 10,240 bytes |
| Address Line 2 | 10,240 bytes |
| City/State/ZIP | 1,024 bytes |
| Name/Title/Phone/Alternate Phone | 1,024 bytes |
| Admin Users per Organization | 10K admins |
| Admin User Login ID | 128 characters |
| Admin User Email | 254 characters |
| Admin User Name | 256 characters |
| Admin User Comments | 10,240 bytes |
| Admin User Password | 100 characters |
| ADP Clients | 16 clients |
| Admin Roles | 64 roles |
| API Roles | 16 roles |
| Identity Providers | 64 identity providers |
[]Outbound Email Data Loss Prevention
Following are the outbound email DLP ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Domain Profiles per Organization | 32 profiles |
| Recipient Profiles per Organization | 32 profiles |
| Recipients per Recipient Profile | 32 recipientsContact Zscaler Support for a possible increase in this limit to 8,192 total recipients. |
| Domain Profiles per Rule | 8 profiles |
| Recipient Profiles per Rule | 8 profiles |
| Custom Domains per Domain Profile | 32 domainsContact Zscaler Support for a possible increase in this limit from 32 domains to 1,024 domains. |
| Outbound Email Policies | 1,024 policies |
[]PAC File
Following are the PAC file ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Name | 255 characters |
| Description | 255 characters |
| File Size | 256 KB |
| PAC Files per Organization | 256 PAC filesContact Zscaler Support to increase the limit of PAC files to 1,024. |
| Non-ASCII Characters | The file can contain up to 12% of non-ASCII characters (binary). |
[]Policies
Following are the policy and rule ranges and limitations:
[](/unified/about-url-categories)[](#url-filter-cloud-app-control)
[]
| Feature | Limit | Comments |
| ------- | ----- | -------- |
| Bandwidth Control Policy Rules per Organization | 125 rules |  |
| Cloud App Control Policy Rules per Cloud App Category | 127 rules | Contact Zscaler Support for a possible increase in the limit of Cloud App Control policy rules per cloud app category from 127 to 2,047. |
| File Type Control Policy | 2,048 rules |  |
| SaaS Security API Scans |  |  |
| Amazon S3 | 1,000 buckets | To enable scanning of up to 1,000 Amazon S3 buckets, contact your Zscaler Account team. |
| Bitbucket | 32 repositories |  |
| Google Cloud Platform | 1,000 buckets | To enable scanning of up to 1,000 Google Cloud Platform buckets, contact your Zscaler Account team. |
| Microsoft Azure | 1,000 blob containers | To enable scanning of up to 1,000 Azure blob containers, contact your Zscaler Account team. |
| DNS Control Policy Rules per Organization | 1,000 rules, if subscribed to Advanced DNS Control. Only 64 rules are supported for Essential DNS Control. |  |
| NAT Control Policy Rules per Organization | 1,023 rules |  |
| Firewall Filtering Policy Rules (including DNAT) per Organization | 1,021 rules, if subscribed to Advanced Firewall. Only 10 rules are supported for Standard Firewall. |  |
| Source IP/Destination Groups IP Address Entries and FQDNs per Organization | 16K IP address entriesThe limit for destination IP entries can be increased by using Custom URL Categories with Custom URLs and Custom IP Ranges. This applies only to the destination IP addresses. To learn more, see the URL Filtering & Cloud App Control section. | Contact Zscaler Support for a possible increase in this limit from 16K IP address entries to 64K IP address entries. |
| Destination Groups FQDNs per Organization | 5,000 address entries16K address entries with Advanced Firewall |  |
| Source IP Groups IP Address Entries per Rule | 8,000 IP address entries |  |
| Destination Groups IP Address Entries and FQDNS per Rule | 8,000 IP address entries |  |
| Source IP/Destination Groups per Rule | 1,000 groups |  |
| Service Groups/Application Groups per Rule | 1,000 groups |  |
| Destination Groups FQDNs per Rule | 5,000 address entries |  |
| Destination Groups IP Address Entries and FQDNs per Group | 8,000 IP address entries |  |
| Destination Groups FQDNs per Group | 100 address entries8,000 address entries with Advanced Firewall |  |
| URL Filtering Policy Rules | 1,000 rules |  |
| Forwarding Policy Rules per Organization | 1,000 rules |  |
| Third-Party Proxies Rules | 8 rules |  |
| Gateways for Third-Party Proxies Rules | 8 rules |  |
| ZPA Gateways Rules | 55 gateways |  |
| Source IP Anchoring Application Segments | 255 segments |  |
| SSL Inspection Policy Rules | 255 rules (245 custom rules and 10 predefined rules) |  |
| All Other Policy Rules (i.e., DLP Policy, Inline Web DLP Policy, IPS Control Policy, etc.) | 1,024 rules | Contact your Zscaler Account team for a possible increase in this limit from 1,024 rules to 2,048 rules. |
| All Policy Rule Types: |  |  |
| Users per Rule | 32 users |  |
| Groups per Rule | 32 groups |  |
| Departments per Rule | 32 departments |  |
| Locations per Rule | 32 locations |  |
| Location Groups per Rule | 32 groups |  |
| Rule Labels | 1,024 labels |  |
| Times per Rule | 8 times |  |
| Devices per Rule | 64 devices |  |
| Device Groups per Rule | 8 device groups |  |
| Workload Groups per Rule | 8 workload groups |  |
| Comments | 10,240 bytes | Some languages use multi-byte characters, so they have fewer characters than bytes. |
| File Type Control Policy File Size | 400 MB |  |
[]Reporting
Following are the reporting ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Interactive Report Name | 50 characters |
| Widget Name | 50 characters |
| Widgets | 20 widgets |
| Favorites per User | 50 favorites |
| Scheduled Report Recipient (i.e., Email Address) | 254 characters |
| Export to CSV (Web, Mobile, Firewall, DNS, and Tunnel Insights Logs) | 20 requests/hour |
[]SaaS Application Tenants
Following are the SaaS application tenant ranges and limitations:
[](/unified/adding-saas-application-tenants)[](/unified/about-email-profiles)
| Feature | Limit | Comments |
| ------- | ----- | -------- |
| Number of tenants per SaaS application | 16 tenants | Up to 16 tenants can be added for each sanctioned SaaS application. Contact Zscaler Support for a possible increase in this limit. |
| Number of external trusted domain and user profiles per application | 32 profiles | Up to 32 profiles can be added for each sanctioned SaaS application. To learn more, see Adding SaaS Application Tenants and About Email Profiles. |
[]URL Filtering & Cloud App Control
Following are the URL filtering and cloud app control ranges and limitations:
-
-
-
-
-
-
| Feature | Limit | Comments |
| ------- | ----- | -------- |
| Custom Keywords per Category | 256 keywords | There can be a maximum of 2,048 custom keywords across all categories. |
| Keywords retaining parent category per Category | 2,048 keywords | There can be a maximum of 2,048 keywords retaining the parent category across all categories. |
| Total Custom Keywords and Keywords retaining parent category per Organization | 2,048 keywords |  |
| Custom URLs/TLDs | 25K URLs/TLDs | Includes:Custom URLs/TLDs in all URL Categories/TLD CategoriesAuth Exemption URLs in Advanced settingsBlocked Malicious URLs in Advanced Threat Protection settingsBlocked URLs in SSL Inspection settingsAllowed URLs in FTP Control settingsBandwidth Class DomainsDuplicate URLs/TLDs are counted once.The default limit for custom URLs/TLDs is 25K. Contact your Zscaler Account team to subscribe to up to an additional 50K custom URLs/TLDs. You can subscribe up to 5 times to additional URLs/TLDs, which are added beyond the default limit at an additional cost and license. |
| Do Not Scan Content from these URLs | 1,024 URLs |  |
| Custom Categories/TLD Categories | 64 categories | The default limit for custom categories is 64. Contact Zscaler Support to increase the limit to a maximum of 1,024 categories. |
| Custom Cloud Applications per Organization | 64 applications |  |
| URLs per Custom Cloud Application | 128 URLs |  |
| URLs | 253 characters |  |
| IP Ranges | 2,048 IP ranges |  |
| Cloud Application Instance | 512 cloud application instances | Contact Zscaler Support for a possible increase in the limit of cloud application instances from 512 to 4,096. |
| Instance Identifiers | 1,024 instance identifiers | Each instance identifier can have up to 128 characters. There can be a maximum of 2,048 instance identifiers across all instances.Contact Zscaler Support for a possible increase in the limit of instance identifiers across all instances per organization from 2,048 to 8,192. |
| Cloud Application Instance per Rule | 8 cloud application instances |  |
| Cloud Application Tags per Organization | 16 tags | Each tag can have up to 127 characters. |
| Tenant Profiles per Rule | 16 tenant profiles | Each Cloud App Control Policy rule can have up to 16 tenant profiles associated with it. |
| Amazon Web Services | 256 account IDs | Each account ID must have 12 digits. There can be a maximum of 2,048 account IDs across all profiles. |
| ChatGPT | 128 workspace IDs | Each workspace ID can have up to 64 characters.You can associate a maximum of 16 tenant profiles or 20 workspace IDs per rule. |
| Dropbox Team ID | 100 team IDs | Each team ID can have up to 64 characters. |
| GitHub | One enterprise slug | Each enterprise slug can have up to 256 characters. There can be a maximum of 100 tenant profiles per organization.You can associate only one tenant profile per rule. |
| Google App Domains | 100 domains | Each domain name can have up to 160 characters. There can be a maximum of 2,048 domains across all profiles. |
| Google Cloud Platform | 100 organization IDs | Each organization ID can have up to 64 characters. There can be a maximum of 2,048 organization IDs across all profiles. |
| IBM SmartCloud | 100 account IDs | Each account ID can have up to 64 characters. There can be a maximum of 100 account IDs per rule and 256 account IDs across all profiles. |
| Microsoft Login Services (Version 1) Tenant Directory ID | One tenant directory | Each tenant directory can have up to 64 characters. |
| Microsoft Login Services (Version 2) Tenant Directory ID:Policy ID | One tenant directory:policy ID | Each tenant directory:policy ID can have up to 256 characters. |
| Microsoft Login Services (Version 1) Microsoft 365 Tenants or Tenant IDs | 500 Microsoft 365 tenants | Each Microsoft 365 tenant or tenant ID can have up to 64 characters. |
| Slack Your Workspace ID | 100 workspace IDs | Each workspace ID can have up to 64 characters. |
| Slack Allowed Workspace ID | 256 workspace IDs | Each workspace ID can have up to 64 characters. |
| YouTube Channel ID | 200 channel IDs | Each channel ID can have up to 100 characters. |
| YouTube School ID | 100 school IDs | Each school ID can have up to 127 characters. |
| Webex Login Services | 100 Webex tenants | There can be a maximum of 250 tenants across all profiles. |
| Zoho Login Services | 120 Zoho IDs | Each Zoho ID can have up to 127 characters. There can be a maximum of 2,048 Zoho IDs across all profiles. |
| Zoom | One policy label | Each policy label can have up to 64 characters. |
[]Users
Following are the user ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Users per Organization | 1,400K users |
| User Name | 128 characters |
| User Password | 255 characters |
| Groups per User | 127 groups by default |
| Comments | 10,240 bytes |
| Imported Users per CSV file | 3,000 entries |
| User Groups per Organization | 140K groups |
| User Temporary Authentication Email | 254 characters |
[]VPN Credentials
Following are the VPN credentials ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| VPN Credentials per Organization | 16K credentialsContact Zscaler Support for a possible increase in this limit from 16K credentials to 64K IP credentials. |
| Imported VPN Credentials per CSV file | 3,000 entries |
| User ID (for FQDN authentication type) | 256 characters |
| Pre-Shared Key (for FQDN and IP authentication types) | 255 characters |
| Comments | 10,240 bytes |
[]Static IPs
Following are the static IP ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Static IP Address Entries per Organization | 100 IP address entries by defaultContact Zscaler Support to increase the limit for your organization. |
| Imported Static IPs per CSV file | 3,000 entries |
| Description | 10,240 characters |
[]Other
Following are other Internet & SaaS ranges and limitations:
[](/unified/about-url-categories)[](#url-filter-cloud-app-control)
| Feature | Limit |
| ------- | ----- |
| Source IP and Destination Groups | 4,000 groups |
| IP Address Entries or FQDNs per Group | 8,000 IP address entriesThe total number of IP entries across groups must adhere to the overall base IP limit. |
| IP Address Entries per Organization | 16K IP address entriesThe limit for destination IP entries can be increased by using Custom URL Categories with Custom URLs and Custom IP Ranges. This applies only to the destination IP addresses. To learn more, see the URL Filtering & Cloud App Control section. |
| Predefined Bandwidth Classes | 8 classes |
| Custom Bandwidth Classes | 245 classes |
| Bandwidth Class Name | 255 characters |
| Time Intervals | 64 intervals |
| Virtual Service Edge Nodes per Cluster | 16 nodes |
| Exported Transactions | 100K entries |
| Admin Role Name | 128 characters |
| SAML Certificate Filename | 128 characters |
| SAML Certificate Key Name | 1,024 characters |
| Alerts | 128 alerts |
| Alert Definition Comments | 10,240 bytes |
| Alert Subscription Email | 254 characters |
| Restore Point Name | 128 characters |
| Restore Point Description | 10,240 bytes |
| ICAP Name | 128 characters |
| ICAP Receiver URL | 128 characters |
| Firewall Network Services | 832 services |
| Network Service Name | 255 characters |
| Network Service Description | 1,024 bytes |
| Custom IPS Signature Rules | 500 signature rules |
| Custom IPS Threat Categories | 64 threat categories |
| Auditor Email | 254 characters |
| Admin Audit Log | 1,000 entries |
| Workload Groups | 1,024 entries |
| SCIM Servers | 5 requests/second |
| EDNS Client Subnet (ECS) Prefix Objects per Organization | 128 prefixes |
| DNS Gateways | 254 DNS Gateways |
| Custom Path URL Length for DNS Gateway Server | 1,024 characters |
| URL Length in Destination Group | 255 characters |
| Sub-URL Length in Insight Logs display and CSV file | 2,041 charactersSub-URLs are truncated if they exceed the character limit. |
| Remote Assistance View-Only and Full Access | 90 days |
[]
[]Administration
The following table shows the ranges and limitations for [administration](/unified/administration/private-applications) settings:
| **Feature** | **Limit** |
| ----------- | --------- |
| Admins | 5,000 admins |
| Roles | 100 roles |
[]App Connector Management
The following table shows the ranges and limitations for [App Connector](/zpa/app-connector-management) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| App Connectors | 100 App Connectors |
| App Connector Groups | 100 groups |
| App Connector Provisioning Keys | 100 keys |
[]Application Management
The following table shows the ranges and limitations for [application](/zpa/application-management) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| Applications | 6,000 applicationsContact Zscaler Support to increase the limit up to 50K for Zscaler Client Connector version 4.0 and later for Windows, Zscaler Client Connector version 4.1 and later for macOS, and Zscaler Client Connector version 3.9 and later for Android.2,000 applications per application segmentThe 2,000 applications per application segment limit applies to both IPs and domains. Wildcards also fall in the same category (i.e., every entry for the application in the Admin Portal counts as one).4,000 Source IP Anchoring-enabled domains or IP addressesDNS resolution can resolve a single domain (such as example.com or host.example.com) to no more than 200 IP addresses on the App Connector.The cloud can only handle up to 100 TXT records for any domain that it looks up. The DNS TXT records are ignored if the lookup surpasses 100 DNS TXT records. |
| Application Segments | 6,000 segments240 Source IP Anchoring-enabled segments |
| DNS Suffixes | 50 suffixes |
| Segment Groups | 200 groups |
| Servers | 10,000 servers |
| Server Groups | 1,000 groups |
| Pattern Matching | 500 patterns |
[]AppProtection Management
The following table shows the ranges and limitations for [AppProtection](/unified/policies/private-applications/cybersecurity) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| Custom Control Parameters | 100 custom control parameters per custom control100 custom control parameters per AppProtection profile |
[]Authentication
The following table shows the ranges and limitations for [authentication](/unified/administration/private-applications/identity/idp-device-configuration/idp-configuration) configuration:
| **Feature** | **Limit** |
| ----------- | --------- |
| IdP Configurations | 10 configurations |
| SAML Attributes | 100 attributes |
[]Backup and Restore
| Feature | Limit |
| ------- | ----- |
| Backups | 10 backups per dayThe 10 backups per day limit applies to manually added backups, scheduled backups, and backups that are created within a Microtenant and have a **Completed** or **In Progress** status. |
| Restores | 10 restores per day |
[]Browser Protection Management
The following table shows the ranges and limitations for [Browser Protection](/unified/about-browser-protection-profiles) configuration:
| **Feature** | **Limit** |
| ----------- | --------- |
| Monitored Users | 20,000 users |
[]Certificate Management
The following table shows the ranges and limitations for [certificate](/unified/policies/private-applications/access-control/clientless/certificate-management) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| (web server) Certificates | 1,000 certificates |
| Enrollment Certificates | 1,000 certificates |
[]Client Type Management
The following table shows the ranges and limitations for Private Applications client type management:
[](/unified/accessing-user-activity-diagnostics)
| **Feature** | **Limit** |
| ----------- | --------- |
| Client Type Microtunnel (M-Tunnel) Requests | 100 M-Tunnels per secondThe 100 M-Tunnels per second limit applies to the Zscaler Client Connector, Web Browser, Web Browser Unauthenticated, or Internet & SaaS Public Service Edge client types. To learn more, see Accessing User Activity Diagnostics.The 100 M-Tunnels per second limit can be changed. To learn more, contact Zscaler Support. |
[]Cloud Connector Management
The following table shows the ranges and limitations for [Cloud Connector](/unified/infrastructure/private-applications/infrastructure-components/cloud-connector-management) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| Cloud Connector M-Tunnel Requests | 200 M-Tunnels per secondThe 200 M-Tunnels per second limit can be changed. To learn more, contact Zscaler Support. |
| Workload Groups | 64 workload groups |
[]Identity Management
The following table shows the ranges and limitations for [identity](/unified/administration/private-applications/identity/scim-configuration) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| SCIM updates | 50 per second |
| SCIM Groups | 1,000 groups per userThe 1,000 groups per user limit means that if a user is a part of more than 1,000 groups, the remaining groups are not synced until some of them are removed for the user on the IdP. There is no limit to the number of SCIM groups that can be synced. |
[]Machine Management
The following table shows the ranges and limitations for [machine](/unified/administration/private-applications/identity/idp-device-configuration/machine-authentication) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| Machine Groups | 100 groups |
[]Microtenants
The following table shows the ranges and limitations for [Microtenant](/unified/about-microtenants) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| Microtenants | 500 Microtenants |
[]Organization
The following table shows the organization ranges and limitations for [organization](/unified/administration/private-applications/admin-user-role-management/admins-and-roles) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| Admin User Password | 100 characters |
[]Policies
Following are the policy and rule ranges and limitations.
[](/unified/policies/private-applications/access-control)
| Feature | Limit |
| ------- | ----- |
| Access Policy | 2,000 policy rules1,000 application segments per policy rule48 App Connector groups per policy ruleThe 48 App Connector groups per policy rule limit applies even if **All App Connector groups for the application** is selected when configuring an access policy rule. To learn more, see Configuring Access Policies.50 locations for extranet application support10 location groups for extranet application support |
| AppProtection Policy | 500 policy rules1,000 application segments per policy rule |
| Client Forwarding Policy | 500 policy rules1,000 application segments per policy rule |
| Isolation Policy | 500 policy rules1,000 application segments per policy rule |
| Log Receiver Policy | 1,000 application segments per policy rule |
| Privileged Capabilities Policy | 5,000 policy rules200 privileged consoles per privileged capabilities policy |
| Privileged Credentials Policy | 5,000 policy rules1,000 privileged consoles per privileged credentials policy |
| Redirection Policy | 2,000 policy rules |
| Timeout Policy | 500 policy rules1,000 application segments per policy rule |
[]Private Applications Private Service Edge Management
The following table shows the ranges and limitations for Private Applications [Private Service Edge](/zpa/private-service-edge-management/private-service-edge) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| Private Service Edges | 100 Private Service Edges |
| Private Service Edge Groups | 100 groups |
| Private Service Edge Provisioning Keys | 100 keys |
[]Private Cloud Controller Management
The following table shows the ranges and limitations for [Private Cloud Controller](/unified/about-private-cloud-controllers) management:
| Feature | Limit |
| ------- | ----- |
| Private Cloud Controllers | 100 Private Cloud Controllers |
| Private Cloud Controller Groups | 100 Private Cloud Controller Groups |
| Private Cloud Controller Provisioning Keys | 100 keys |
| Maximum Number of Backups | 100 backups |
[]Privileged Remote Access
The following table shows the ranges and limitations for [Privileged Remote Access](/unified/policies/private-applications/access-control/clientless/privileged-remote-access-management):
[](/unified/about-my-approvals)
[](/unified/about-microtenants)
| **Feature** | **Limit** |
| ----------- | --------- |
| Privileged Approvals | 20,000 privileged approvals200 application segments per privileged approvalOnly privileged approvals with approval statuses of Future or Active are counted. Privileged approvals with an approval status of Expired are not considered as part of the total amount. Each user can create up to 20 privileged approval requests on the My Requests page in the PRA Portal. |
| Privileged Consoles | 10 privileged consolesWith a license, this can be increased to the maximum limit of 9,000 privileged consoles. Contact your Zscaler Account team for more information. |
| Privileged Credentials | 10,000 privileged credentials |
| Privileged Credential Pools | 500 privileged credential pools100 privileged credentials per privileged credential pool |
| Privileged Portals | 100 privileged portalsWhen configuring a privileged portal within the Default Microtenant, you can link a maximum of 9,000 privileged consoles to the privileged portal. |
[]Support Information
The following table shows the ranges and limitations for [Support Information](/unified/accessing-and-viewing-support-information) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| App Connectors | 100 App Connectors per session |
| Private Service Edges | 100 Private Service Edges per session |
| Private Cloud Controllers | 100 Private Cloud Controllers per session |
| Actions | 10 Actions per session |
| Targets | 10 Targets per session |
| Concurrent Sessions | 5 Concurrent Sessions per customerThe 5 Concurrent Sessions per customer limit is only on sessions that are in a Pending or Processing state. There is no limit on Completed, Failed, or Partially_Completed sessions. |
[]User Portal
The following table shows the ranges and limitations for [user portal](/unified/policies/private-applications/access-control/clientless/user-portal):
[](/unified/configuring-user-portal-links)
| **Feature** | **Limit** |
| ----------- | --------- |
| Portal Links | 500 linksYou can only configure 150 links at a time when configuring portal links in the Admin Portal. |
[]VPN (for Legacy Apps)
The following table shows the ranges and limitations for [VPN for legacy apps](/unified/infrastructure/private-applications/infrastructure-components/vpn-legacy-apps):
| **Feature** | **Limit** |
| ----------- | --------- |
| Number of Regions per Customer | 3 per customer |
| Number of VPN Service Edges (VPN for Legacy Apps Gateway) per Customer | 3 per customer |
| Number of Network Segments per Customer | 100 per customer |
| Number of Network Connector Groups per Customer | 100 per customer |
| Number of LAN Subnets (Network Segments) per Network Connector Group | 64 per Network Connector group |
| Number of Client Subnets per VPN Service Edge (VPN for Legacy Apps Gateway) | 16 per VPN Service Edge (VPN for Legacy Apps Gateway) |
| Number of Peer Routes per VPN Service Edge | 1,024 peer routes per VPN Service Edge |
| Number of Peer Routes per Network Connector | 1,024 peer routes per Network Connector |
| Number of LAN IP Addresses and Subnets per Network Segment | 64 per Network Segment |
[]
[]Groups
The following table shows the ranges and limitations for groups:
| **Feature** | **Limit** |
| ----------- | --------- |
| Group Name | 255 characters |
| Network Services Groups | 126 groups |
| Source IP Address Groups | 4,000 groups |
| Destination Groups (Destination IP or FQDN Groups) | 4,000 groups |
| Fully Qualified Domain Names (FQDNs) or IP Addresses per Group | 8,000 addresses |
| Cloud Connector Groups | 1,000 groups |
| Branch Connector Groups | 1,000 groups |
| Virtual Machines (VMs) per Group | 16 VMs |
| Application Segment Groups | 600 groups |
[]Locations
The following table shows ranges and limitations for locations:
| **Feature** | **Limit** |
| ----------- | --------- |
| Locations | 1,000 locations |
| Location Name | 255 characters |
| Location Templates | 500 templates |
[]NSS
The following table shows the ranges and limitations for Nanolog Streaming Service (NSS) filter feeds:
| **Feature** | **Standard** |
| ----------- | ------------ |
| NSS Servers | 2 servers |
| NSS Feeds per Server | 8 feeds |
| NSS Users per Feed | 1,024 users |
| NSS Departments per Feed | 1,024 departments |
| NSS Locations per Feed | 1,024 locations |
| NSS Clients per Feed | 1,024 clients |
| NSS Threat Names per Feed | 1,024 threat names |
[]Organization
The following table shows the ranges and limitations for organization:
| **Feature** | **Limit** |
| ----------- | --------- |
| Address Line 1 | 10,240 bytes |
| Address Line 2 | 10,240 bytes |
| City/State/ZIP | 1,024 bytes |
| Name/Title/Phone/Alternate Phone | 1,024 bytes |
| Admin Users per Organization | 10K admins |
| Admin User Login ID | 128 characters |
| Admin User Email | 254 characters |
| Admin User Name | 256 characters |
| Admin User Comments | 10,240 bytes |
| Admin User Password | 100 characters |
| Admin Roles | 64 roles |
| Identity Providers | 16 identity providers |
[]Forwarding
The following table shows the ranges and limitations for forwarding:
| **Feature** | **Limit** |
| ----------- | --------- |
| Traffic Forwarding Rules | 1,020 rules |
| Log & Control Forwarding Rules | 1,020 rules |
| Domains/FQDNs per Organization | 1,024 domains/FQDNs |
| Domains/FQDNs per Rule | 1,024 domains/FQDNs |
| ZIA Gateways | 1,000 gateways |
| Log and Control Gateways | 1,000 gateways |
| DNS Gateways | 255 gateways |
| DNS Control Policy Rules | 1,020 rules |
| Application Segments | 50,000 segments |
| Description | 10,240 characters |
[]Provisioning Control
The following table shows the provisioning and configuration ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Cloud Provisioning Templates | 1,000 templates |
| Branch Configuration Templates | 1,000 templates |
| Branch Connector Static Routes | 32 routes |
| Branch Connector DHCP Server Static Leases | 32 leases |
| Branch Connector Virtual local area networks (VLANs) per Interface | 9 subinterface VLANs and one main untagged VLAN per interface, or 10 subinterface VLANs without the main untagged VLAN |
[]
Advanced Settings
The following table shows the ranges and limitations for advanced settings:
| Feature | Minimum Limit | Maximum Limit |
| ------- | ------------- | ------------- |
| Session Timeout | 5 seconds | 600 minutes |
API Client
The following table shows the ranges and limitations for API clients:
| Feature | Limit |
| ------- | ----- |
| API clients per tenant | 256 |
External Identities
The following table shows the ranges and limitations for secondary identity providers (IdP):
| Feature | Limit |
| ------- | ----- |
| Number of secondary IdPs a tenant can have | 64 |
IP Locations
The following table shows the ranges and limitations for IP locations:
| Feature | Limit |
| ------- | ----- |
| Total IP Locations | 65,536 |
| Total IP addresses within a single IP Location | 2,048 |
IP Location Groups
The following table shows the ranges and limitations for IP location groups:
| Feature | Limit |
| ------- | ----- |
| Total IP Location Groups | 4,096 |
| IP Locations within a single Location Group | 2,048 |
Policies
The following table shows the ranges and limitations for sign-on and password policies:
| Feature | Minimum Limit | Maximum Limit |
| ------- | ------------- | ------------- |
| Admin Sign-On Policy: Total policy numbers and maximum criteria within a single policy | 0 | 256 |
| Password Policy: Password expiration period | 15 days | 365 days |
Users, Groups, and User Attributes
The following table shows the ranges and limitations for users, groups, and user attributes:
| Feature | Limit |
| ------- | ----- |
| Maximum groups allowed per user | 1000 |
| Maximum groups per tenant | 140K |
| User attributes | 128 |
Zscaler Services
The following table shows the ranges and limitations for Zscaler services:
| Feature | Limit |
| ------- | ----- |
| User or group assignment using the Add operation | 4,096 |
| Maximum admins for each service | 10,000 |