# Ranges & Limitations
Source: https://help.zscaler.com/zpa/ranges-limitations
PDF: https://help.zscaler.com/pdf/com/en/1484356.pdf

This article lists the ranges and limitations for policies, fields, and other features. All values are per organization unless noted otherwise.
If you need to increase a maximum limit for your organization, send a request to Zscaler Support.
[]Administration
The following table shows the ranges and limitations for [administration](/zpa/administration) settings:
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
-
-
-
-
-
| **Feature** | **Limit** |
| ----------- | --------- |
| Applications | 6,000 applicationsContact Zscaler Support to increase the limit up to 50K. This is only available with certain versions of Zscaler Client Connector:Version 4.0 and later for WindowsVersion 4.1 and later for macOSVersion 3.9 and later for AndroidVersion 4.4 and later for iOSVersion 4.2 and later for Linux2,000 applications per application segmentThe 2,000 applications per application segment limit applies to both IP addresses and domains. Wildcards also fall in the same category (i.e., every entry for the application in the ZPA Admin Portal counts as one).4,000 Source IP Anchoring-enabled domains or IP addressesDNS resolution can resolve a single domain (such as example.com or host.example.com) to no more than 200 IP addresses on the App Connector.The ZPA cloud can only handle up to 100 TXT records for any domain that it looks up. The DNS TXT records are ignored if the lookup surpasses 100 DNS TXT records. |
| Application Segments | 6,000 segments240 Source IP Anchoring-enabled segments |
| DNS Suffixes | 50 suffixes |
| Segment Groups | 200 groups |
| Servers | 10,000 servers |
| Server Groups | 1,000 groups |
| Pattern Matching | 500 patterns |
[]AppProtection Management
The following table shows the ranges and limitations for [AppProtection](/zpa/appprotection-private-application-traffic-formerly-inspection) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| Custom Control Parameters | 100 custom control parameters per custom control100 custom control parameters per AppProtection profile |
[]Authentication
The following table shows the ranges and limitations for [authentication](/zpa/authentication) configuration:
| **Feature** | **Limit** |
| ----------- | --------- |
| IdP Configurations | 10 configurations |
| SAML Attributes | 100 attributes |
[]Backup and Restore
The following table shows the ranges and limitations for [Backup and Restore](/zpa/about-backup-and-restore):
| Feature | Limit |
| ------- | ----- |
| Backups | 10 backups per dayThe 10 backups per day limit applies to manually added backups, scheduled backups, and backups that are created within a Microtenant and have a **Completed** or **In Progress** status. |
| Restores | 10 restores per day |
[]Browser Protection Management
The following table shows the ranges and limitations for [Browser Protection](/zpa/about-browser-protection-profiles) configuration:
| **Feature** | **Limit** |
| ----------- | --------- |
| Monitored Users | 20,000 users |
[]Certificate Management
The following table shows the ranges and limitations for [certificate](/zpa/certificate-management) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| (web server) Certificates | 1,000 certificates |
| Enrollment Certificates | 1,000 certificates |
[]Client Type Management
The following table shows the ranges and limitations for ZPA client type management:
[](/zpa/about-user-activity-diagnostics#user)
| **Feature** | **Limit** |
| ----------- | --------- |
| Client Type Microtunnel (M-Tunnel) Requests | 100 M-Tunnels per secondThe 100 M-Tunnels per second limit applies to the Zscaler Client Connector, Web Browser, Web Browser Unauthenticated, or ZIA Public Service Edge client types. To learn more, see About User Activity Diagnostics.The 100 M-Tunnels per second limit can be changed. To learn more, contact Zscaler Support. |
[]Cloud Connector Management
The following table shows the ranges and limitations for [Cloud Connector](/zpa/about-cloud-connectors) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| Cloud Connector M-Tunnel Requests | 200 M-Tunnels per secondThe 200 M-Tunnels per second limit can be changed. To learn more, contact Zscaler Support. |
| Workload Groups | 64 workload groups |
[]Identity Management
The following table shows the ranges and limitations for [identity](/zpa/identity-management) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| SCIM updates | 50 per second |
| SCIM Groups | 1,000 groups per userThe 1,000 groups per user limit means that if a user is a part of more than 1,000 groups, the remaining groups are not synced until some of them are removed for the user on the IdP. There is no limit to the number of SCIM groups that can be synced. |
[]Machine Management
The following table shows the ranges and limitations for [machine](/zpa/authentication/machine-authentication) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| Machine Groups | 100 groups |
[]Microtenants
The following table shows the ranges and limitations for [Microtenant](/zpa/about-microtenants) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| Microtenants | 500 Microtenants |
[]Organization
The following table shows the organization ranges and limitations for [organization](/zpa/documentation-knowledgebase/admin-settings/admins-and-roles) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| Admin User Password | 100 characters |
[]Policies
The following table shows the ranges and limitations for [policy](/zpa/access-timeout-policies) management:
[](/zpa/configuring-access-policies)
| **Feature** | **Limit** |
| ----------- | --------- |
| Access Policy | 2,000 policy rules1,000 application segments per policy rule48 App Connector groups per policy ruleThe 48 App Connector groups per policy rule limit applies even if **All App Connector groups for the application** is selected when configuring an access policy rule. To learn more, see Configuring Access Policies.50 locations for extranet application support10 location groups for extranet application support |
| AppProtection Policy | 500 policy rules1,000 application segments per policy rule |
| Client Forwarding Policy | 500 policy rules1,000 application segments per policy rule |
| Isolation Policy | 500 policy rules1,000 application segments per policy rule |
| Log Receiver Policy | 1,000 application segments per policy rule |
| Privileged Capabilities Policy | 5,000 policy rules200 privileged consoles per privileged capabilities policy |
| Privileged Credentials Policy | 5,000 policy rules1,000 privileged consoles per privileged credentials policy |
| Redirection Policy | 2,000 policy rules |
| Timeout Policy | 500 policy rules1,000 application segments per policy rule |
[]Private Cloud Controller Management
The following table shows the ranges and limitations for [Private Cloud Controller](/zpa/about-private-cloud-controllers) management:
| Feature | Limit |
| ------- | ----- |
| Private Cloud Controllers | 100 Private Cloud Controllers |
| Private Cloud Controller Groups | 100 Private Cloud Controller groups |
| Private Cloud Controller Provisioning Keys | 100 keys |
| Maximum Number of Backups | 100 backups |
[]Privileged Remote Access
The following table shows the ranges and limitations for [Privileged Remote Access](/zpa/privileged-remote-access-management):
[](/zpa/about-my-approvals)
[](/zpa/about-microtenants)
| **Feature** | **Limit** |
| ----------- | --------- |
| Privileged Approvals | 20,000 privileged approvals200 application segments per privileged approvalOnly privileged approvals with approval statuses of Future or Active are counted. Privileged approvals with an approval status of Expired are not considered as part of the total amount. Each user can create up to 20 privileged approval requests on the My Requests page in the PRA Portal. |
| Privileged Consoles | 10 privileged consolesWith a license, this can be increased to the maximum limit of 9,000 privileged consoles. Contact your Zscaler Account team for more information. |
| Privileged Credentials | 10,000 privileged credentials |
| Privileged Credential Pools | 500 privileged credential pools100 privileged credentials per privileged credential pool |
| Privileged Portals | 100 privileged portalsWhen configuring a privileged portal within the Default Microtenant, you can link a maximum of 9,000 privileged consoles to the privileged portal. |
[]Support Information
The following table shows the ranges and limitations for [Support Information](/zpa/accessing-and-viewing-support-information) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| App Connectors | 100 App Connectors per session |
| Private Service Edges | 100 Private Service Edges per session |
| Private Cloud Controllers | 100 Private Cloud Controllers per session |
| Actions | 10 Actions per session |
| Targets | 10 Targets per session |
| Concurrent Sessions | 5 Concurrent Sessions per customerThe 5 Concurrent Sessions per customer limit is only on sessions that are in a Pending or Processing state. There is no limit on Completed, Failed, or Partially_completed sessions. |
[]User Portal
The following table shows the ranges and limitations for [user portal](/zpa/user-portal):
[](/zpa/configuring-application-links-user-portals)
| **Feature** | **Limit** |
| ----------- | --------- |
| Portal Links | 500 linksYou can only configure 150 links at a time when configuring portal links in the ZPA Admin Portal. |
[]VPN (for Legacy Apps)
The following table shows the ranges and limitations for VPN for legacy apps:
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
| Number of LAN IP Addresses and Subnets per Network Segment | 64 per Network segment |
[]ZPA Private Service Edge Management
The following table shows the ranges and limitations for ZPA [Private Service Edge](/zpa/private-service-edge-management/private-service-edge) management:
| **Feature** | **Limit** |
| ----------- | --------- |
| Private Service Edges | 100 Private Service Edges |
| Private Service Edge Groups | 100 groups |
| Private Service Edge Provisioning Keys | 100 keys |