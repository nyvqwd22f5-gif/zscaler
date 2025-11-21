# Adding NSS Servers
Source: https://help.zscaler.com/zia/adding-nss-servers
PDF: https://help.zscaler.com/pdf/com/en/1400036.pdf

Before reading this article, see the Nanolog Streaming Service (NSS) deployment guide for your platform:
- [NSS Deployment Guide for Amazon Web Services](/zia/nss-deployment-guide-aws)
- [NSS Deployment Guide for Google Cloud Platform](/zia/nss-deployment-guide-google-cloud-platform)
- [NSS Deployment Guide for Microsoft Azure](/zia/nss-deployment-guide-azure)
- [NSS Deployment Guide for VMware vSphere](/zia/nss-deployment-guide-vsphere)
To add an NSS server:
- Go to **Administration **>** Nanolog Streaming Service**.
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
- Click **Save**. The NSS server is added to the ZIA Admin Portal.
To download the SSL certificate:
- Click the **Edit** icon corresponding to the NSS server.
-
In the **Edit NSS Server** window, under the **SSL Certificate** field, you can either download the SSL certificate or generate a new certificate for that NSS server. You can upload this SSL certificate to the desired platform.
[See image.](#edit-window)
[]![Screenshot of the Edit NSS Server window displaying the SSL Certificate field](/downloads/zia/analytics/nanolog-streaming-service/adding-nss-servers/zia-adding-nss-server-edit-window.png)
[]![Screenshot of Add NSS Server window in the ZIA Admin Portal](/downloads/zia/analytics/nanolog-streaming-service/adding-nss-servers/zia-adding-nss-server-add-window.png)