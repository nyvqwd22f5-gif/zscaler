# About NSS Servers
Source: https://help.zscaler.com/cloud-branch-connector/about-nss-servers
PDF: https://help.zscaler.com/pdf/com/en/1420736.pdf

The Nanolog Streaming Service (NSS) uses a virtual machine (VM) to stream traffic logs in real-time from the Zscaler Nanolog to your security information and event management (SIEM) system, enabling real-time alerting, correlation with the logs of your other devices, and long-term local log archival. An NSS server is the representation of the NSS VM in the Zscaler Cloud & Branch Connector Admin Portal.
NSS Servers provide the following benefits and enable you to:
- Issue a client certificate and a private key that you can install on the NSS VM.
- Authenticate to the Zscaler service.
- Assign up to 16 NSS feeds to a server. ([Session Logs](/cloud-branch-connector/adding-nss-feeds-session-logs) are limited to 8 feeds per server to ensure optimal performance.)
About the NSS Servers Page
On the NSS Servers page (Administration > Nanolog Streaming Service > NSS Servers), you can do the following:
- [Add an NSS server](/cloud-branch-connector/adding-nss-servers).
- Deploy an NSS virtual appliance.
To learn more about adding an NSS server and deploying an NSS virtual appliance, see the [NSS Deployment Guides](/cloud-branch-connector/deploying-nss-virtual-appliances).
- Download MIB files.
- View a list of all configured NSS servers.
- **Server Name**: The name of the server.
- **Type**: The server type, which is set to **NSS for Firewall, Cloud and Branch Connector **by default.
- **Status**: The server status.
- **State**: The health state of the server.
- **SSL Certificate**: Download the SSL Certificate.
- [Edit an NSS server](/cloud-branch-connector/editing-deleting-or-duplicating-items#edit).
- [Delete an NSS server](/cloud-branch-connector/editing-deleting-or-duplicating-items#delete).
- Modify the table and its columns.
- View the[ NSS Feeds ](/cloud-branch-connector/about-nss-feeds)page.
- View the** **[Cloud NSS Feeds ](/cloud-branch-connector/about-cloud-nss-feeds)page.
![NSS Servers page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/nanolog-streaming-service/NSSServers.png)