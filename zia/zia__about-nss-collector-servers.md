# About NSS Collector Servers
Source: https://help.zscaler.com/zia/about-nss-collector-servers
PDF: https://help.zscaler.com/pdf/com/en/1463371.pdf

The NSS Collector functionality and the data collected using this functionality are exclusive to Shadow IT Report. To enable this feature for your organization, contact Zscaler Support.
Zscaler supports real-time ingestion of traffic logs from third-party firewall and web proxy services. The log data from third-party security solutions is integrated with Zscaler's unified console to provide advanced reporting and analytics of the cloud applications used by the organization through a comprehensive [Shadow IT Report](/zia/about-shadow-it-report) in the ZIA Admin Portal. To do this, Zscaler requires you to deploy an NSS Collector, typically within your organization’s network perimeter, to collect logs from third-party feeds, process the log data, and push the logs securely to the Zscaler cloud. To learn more, see [Understanding Nanolog Streaming Service (NSS)](/zia/understanding-nanolog-streaming-service).
The NSS Collector server provides the following benefits and enables you to:
- Collect traffic logs from third-party firewalls and web proxy services used by your organization in real time.
- Process the log data collected from third-party security solutions to resolve user information via the identity provider (IdP) integration with Zscaler, resolve URL information for cloud application discovery and analysis in Zscaler, serialize the log feed to a format supported by Zscaler, etc.
- Securely transmit the logs to the Zscaler cloud to allow for cloud application discovery and analysis within the Zscaler’s unified console.
You can configure the NSS Collector server in the ZIA Admin Portal to obtain the packaged software (VM image) for installation. The NSS Collector can be deployed on VMware. To learn more about the deployment procedure, see [NSS Collector Deployment Guide for VMware vSphere](/zia/nss-collector-deployment-guide-vmware-vsphere).
Zscaler supports log ingestion from Palo Alto Networks, Blue Coat, and Fortinet.
About the NSS Collector Servers Page
On the NSS Collector Servers page (Administration > Nanolog Streaming Service), you can do the following:
- [Add an NSS Collector server.](/zia/adding-nss-collector-servers)
- View the list of all configured NSS Collector servers. By default, the table displays the following information:
- **Server Name**: The name of the NSS Collector server.
- **Vendor**: The third-party vendor of the firewall or web proxy services used by your organization.
- **Status**: The server status that indicates whether it is enabled or disabled.
- **SSL Certificate**: The option to download the SSL certificate for the server.
- Download the SSL certificate for an NSS Collector server.
- [Edit an NSS Collector server.](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal)
- [Modify the table and its columns.](/zia/how-do-i-use-tables-admin-portal)
- Search for an NSS Collector server.
- Go to the [NSS Servers](/zia/about-nss-servers), [NSS Feeds](/zia/about-nss-feeds), or [Cloud NSS Feeds](/zia/about-cloud-nss-feeds) tabs.
![A screenshot of the NSS Collector Servers page](/downloads/zia/nanolog-streaming-service/about-nss-collector-servers/nss-collector-servers-page.png)