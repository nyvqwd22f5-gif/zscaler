# About NSS Servers
Source: https://help.zscaler.com/zia/about-nss-servers
PDF: https://help.zscaler.com/pdf/com/en/1402076.pdf

An NSS server is the representation of the NSS virtual machine (VM) in the ZIA Admin Portal. After you create a server, Zscaler issues a client certificate and private key that you can install on the NSS VM so that it can authenticate to the Zscaler service.
NSS servers provide the following benefits and enable you to:
- Stream traffic logs from the Zscaler [Nanolog](/zia/understanding-zscaler-cloud-architecture) to your security information and event management (SIEM) system, allowing for real-time alerting, correlation with the logs of your other devices, and long-term local log archival.
- Assign as many as 16 unique NSS feeds per NSS server for broad and in-depth logging. ([Web](/zia/adding-nss-feeds-web-logs) and [Firewall](/zia/adding-nss-feeds-firewall-logs) logs are each limited to 8 feeds per server to ensure optimal performance.)
About the NSS Servers Page
On the NSS Servers page (Administration > Nanolog Streaming Service), you can do the following:
- [Add an NSS server](/zia/adding-nss-servers).
-
Deploy an NSS virtual appliance.
To learn more about adding an NSS server and deploying an NSS virtual appliance, see the [NSS Deployment Guides](/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides).
- [Download MIB files](/zia/about-the-zscaler-snmp-mibs).
- Search for an NSS server.
- View a list of all configured NSS servers. For each server, you can see:
- **Server Name**: The name of the server.
- **Type**: The server type.
- **Status**: The server status.
- **State**: The health state of the server.
- **SSL Certificate**: The option to download the SSL certificate.
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
- [Edit an NSS server](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal).
- [Add an NSS feed](/zia/about-nss-feeds).
- [Add a Cloud NSS feed.](/zia/about-cloud-nss-feeds)
- [Add an NSS Collector server](/zia/adding-nss-collector-servers).
****![Screenshot of the NSS Servers page in the ZIA Admin Portal](/downloads/zia/nanolog-streaming-service/about-nss-servers/zia-nss-add-nss-server-page.png)
****