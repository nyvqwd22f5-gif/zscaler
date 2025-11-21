# About NSS Servers for Cloud & Branch Connector
Source: https://help.zscaler.com/unified/about-nss-servers-cloud-branch-connector
PDF: https://help.zscaler.com/pdf/com/en/1519476.pdf

The Nanolog Streaming Service (NSS) uses a virtual machine (VM) to stream traffic logs in real-time from the Zscaler Nanolog to your security information and event management (SIEM) system, enabling real-time alerting, correlation with the logs of your other devices, and long-term local log archival. An NSS server is the representation of the NSS VM in the Zscaler Admin Portal.
NSS Servers provide the following benefits and enable you to:
- Issue a client certificate and a private key that you can install on the NSS VM.
- Authenticate to the Zscaler service.
- Assign up to 16 NSS feeds to a server. ([Session Logs](/unified/adding-nss-feeds-session-logs) are limited to 8 feeds per server to ensure optimal performance.)
About the NSS Servers Page
On the NSS Servers page (Infrastructure > Connectors > Cloud > Nanolog Streaming Service > NSS Servers), you can do the following:
- [Add an NSS server](/unified/adding-nss-servers-cloud-branch-connector).
- Deploy an NSS virtual appliance.
To learn more about adding an NSS server and deploying an NSS virtual appliance, see the [NSS Deployment Guides](/unified/deploying-nss-virtual-appliances-cloud-branch-connector).
- Download MIB files.
- View a list of all configured NSS servers.
- **Server Name**: The name of the server.
- **Type**: The server type, which is set to **NSS for Firewall, Cloud and Branch Connector **by default.
- **Status**: The server status.
- **State**: The health state of the server.
- **SSL Certificate**: Download the SSL Certificate.
- Edit an NSS server.
- Delete an NSS server.
- Modify the table and its columns.
- View the [NSS Feeds](/unified/about-nss-feeds-cloud-branch-connector) page.
- View the** **[Cloud NSS Feeds](/unified/about-cloud-nss-feeds-cloud-branch-connector) page.
![NSS Servers page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/about-nss-servers-draft-doc-46401/AboutNSSServers_FCB2.png)