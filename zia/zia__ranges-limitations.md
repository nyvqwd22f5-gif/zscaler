# Ranges & Limitations
Source: https://help.zscaler.com/zia/ranges-limitations
PDF: https://help.zscaler.com/pdf/com/en/1400846.pdf

This article lists the ranges and limitations of rules, policies, fields, and other features. All values are per organization unless noted otherwise.
[]Active Directory & OpenLDAP Synchronization
The following are the Active Directory (AD) and OpenLDAP synchronization ranges and limitations:
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
Advanced Threat Protection
The following is the blocked malicious URLs limitation:
| Feature | Limit |
| ------- | ----- |
| Blocked Malicious URLs | 25K FQDNs, domains, or URLs |
[]Data Loss Prevention
The following are the Data Loss Prevention (DLP) ranges and limitations:
- [](/zia/viewing-tenant-details)
- [](/zia/viewing-tenant-details)
- [](/zia/viewing-tenant-details)
- [](/zia/viewing-tenant-details)
| Feature | Limit |
| ------- | ----- |
| Custom DLP Dictionaries | 801 dictionaries (with DLP Dictionary Expansion enabled)160 dictionaries (with DLP Dictionary Expansion disabled) |
| Custom DLP Parent Dictionaries | 64 dictionaries |
| Custom DLP Sub-Dictionaries | 63 per parent dictionary |
| Custom DLP Engines | 480 engines (with DLP Engine Expansion enabled)58 engines (with DLP Engine Expansion disabled) |
[]Departments
The following are the department ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Departments per Organization | 140K departments |
| Departments per admin with Department Scope | 2,048 departments |
| Department Name | 128 characters |
| Comments | 10,240 KB |
| Imported Departments per CSV file | 3,000 entries |
[]EUNs
The following are the EUN ranges and limitations:
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
The following are the extranet ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Extranet resources | 1,000 extranets |
| Extranet locations | 5,000 extranet locations |
| Traffic selectors per extranet | 16 traffic selectors |
| DNS servers per extranet | 16 DNS servers |
[]Groups
The following are the group ranges and limitations:
[](#Other)
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
The following are the location ranges and limitations:
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
The following are the Nanolog Streaming Service (NSS) ranges and limitations:
[](/zia/understanding-zscaler-cloud-architecture)[](/zia/understanding-zscaler-cloud-architecture)[](/zia/understanding-zscaler-cloud-architecture)[](/zia/understanding-zscaler-cloud-architecture)[](/zia/understanding-zscaler-cloud-architecture)
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
The following are the organization ranges and limitations:
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
The following are the outbound email DLP ranges and limitations:
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
The following are the PAC file ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Name | 255 characters |
| Description | 255 characters |
| File Size | 256 KB |
| PAC Files per Organization | 256 PAC filesContact Zscaler Support to increase the limit of PAC files to 1,024. |
| Non-ASCII Characters | The file can contain up to 12% of non-ASCII characters (binary). |
[]Policies
The following are the policy and rule ranges and limitations:
[](/zia/about-url-categories)[](#URLFiltering_CloudAppControl)
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
The following are the reporting ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Interactive Report Name | 50 characters |
| Widget Name | 50 characters |
| Widgets | 20 widgets |
| Favorites per User | 50 favorites |
| Scheduled Report Recipient (i.e., Email Address) | 254 characters |
| Export to CSV (Web, Mobile, Firewall, DNS, and Tunnel Insights Logs) | 20 requests/hour |
[]SaaS Application Tenants
The following are the SaaS application tenant ranges and limitations:
[](/zia/adding-saas-application-tenants)[](/zia/about-email-profiles)
| Feature | Limit | Comments |
| ------- | ----- | -------- |
| Number of tenants per SaaS application | 16 tenants | Up to 16 tenants can be added for each sanctioned SaaS application. Contact Zscaler Support for a possible increase in this limit. |
| Number of external trusted domain and user profiles per application | 32 profiles | Up to 32 profiles can be added for each sanctioned SaaS application. To learn more, see Adding SaaS Application Tenants and About Email Profiles. |
[]URL Filtering & Cloud App Control
The following are the URL filtering and cloud app control ranges and limitations:
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
The following are the user ranges and limitations:
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
The following are the VPN credentials ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| VPN Credentials per Organization | 16K credentialsContact Zscaler Support for a possible increase in this limit from 16K credentials to 64K IP credentials. |
| Imported VPN Credentials per CSV file | 3,000 entries |
| User ID (for FQDN authentication type) | 256 characters |
| Pre-Shared Key (for FQDN and IP authentication types) | 255 characters |
| Comments | 10,240 bytes |
[]Static IPs
The following are the static IP ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Static IP Address Entries per Organization | 100 IP address entries by defaultContact Zscaler Support to increase the limit for your organization. |
| Imported Static IPs per CSV file | 3,000 entries |
| Description | 10,240 characters |
[]Other
The following are other ranges and limitations:
[](/zia/about-url-categories)[](#URLFiltering_CloudAppControl)
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