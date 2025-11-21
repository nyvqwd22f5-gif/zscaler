# Adding NSS Servers for Internet & SaaS
Source: https://help.zscaler.com/unified/adding-nss-servers-internet-saas
PDF: https://help.zscaler.com/pdf/com/en/1496651.pdf

Before reading this article, see the Nanolog Streaming Service (NSS) deployment guide for your platform:
- [NSS Deployment Guide for Amazon Web Services](/unified/nss-deployment-guide-amazon-web-services)
- [NSS Deployment Guide for Google Cloud Platform](/unified/nss-deployment-guide-google-cloud-platform)
- [NSS Deployment Guide for Microsoft Azure](/unified/nss-deployment-guide-microsoft-azure)
- [NSS Deployment Guide for VMware vSphere](/unified/nss-deployment-guide-vmware-vsphere)
To add an NSS server:
- Go to **Logs **>** Log Streaming **>** Nanolog Streaming Service**.
- From the **NSS Servers **tab, click **Add NSS Server**.
-
In the **Add NSS Server **window:
- **Name**: Enter a name for the NSS server.
-
**Type**: The **NSS for Web **type is selected by default. To configure NSS for firewall logs, select **NSS for Firewall**.
If you have a subscription to Cloud & Branch Connector, the **NSS for Firewall** (NSS type) is displayed as **NSS for Firewall, Cloud & Branch Connector**.
- **Status**: Enable or disable the status of the NSS server.
- **State**: The health of the NSS server. This field is not able to be configured.
[See image.](#add-window)
-
Click **Save**.
The NSS server is added to the Admin Portal.
To download the SSL certificate:
- Click the **Edit** icon corresponding to the NSS server.
-
In the **Edit NSS Server** window, under the **SSL Certificate** field, you can either download the SSL certificate or generate a new certificate for that NSS server. You can upload this SSL certificate to the desired platform.
[See image.](#edit-window)
[]![Screenshot of the Edit NSS Server window displaying the SSL Certificate field](/downloads/zia/analytics/nanolog-streaming-service/adding-nss-servers/zia-adding-nss-server-edit-window.png)
[]![Screenshot of Add NSS Server window in the ZIA Admin Portal](/downloads/zia/analytics/nanolog-streaming-service/adding-nss-servers/zia-adding-nss-server-add-window.png)