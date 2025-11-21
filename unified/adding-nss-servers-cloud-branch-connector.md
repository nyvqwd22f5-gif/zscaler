# Adding NSS Servers for Cloud & Branch Connector
Source: https://help.zscaler.com/unified/adding-nss-servers-cloud-branch-connector
PDF: https://help.zscaler.com/pdf/com/en/1519481.pdf

Before you set up a Nanolog Streaming Service (NSS) server on the Zscaler Admin Portal, you're required to enter information about your traffic and users so the Zscaler service can compute the appropriate resources for your NSS. The NSS buffers the logs for at least one hour. If a security information and event management (SIEM) goes offline for maintenance or if the connection between the NSS and the SIEM is disrupted, the NSS buffers the logs and sends them after the connection is re-established. The amount of memory required to buffer the logs is incorporated into the VM spec computation. The buffer size increases proportionally to the amount of RAM allocated to the NSS.
To add an NSS server:
- Go to **Infrastructure **>** Connectors** > **Cloud** > **Nanolog Streaming Service**.
- On the **NSS Servers **tab, click **Add NSS Server**.
- In the **Add NSS Server **window:
- **Server Name**: Enter a name for the NSS server.
- **NSS Type**: The type is set to** NSS for Firewall, Cloud and Branch Connector** by default.
- **Status**: Enable or disable the status of the NSS server.
- **State**: The health of the NSS server. This field is non-configurable.
[See image.](#add-window)
- Click **Save**.
To download the SSL Certificate:
- Click the **Edit** icon corresponding to the NSS Server.
- In the **Edit NSS Server** window, under **SSL Certificate**, you can either download the SSL Certificate or generate a new certificate for that NSS Server. You can upload this SSL certificate to the desired platform.
[See image.](#edit-window)
[]![Screenshot of the Edit NSS Server window displaying the SSL Certificate field](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/adding-nss-servers-draft/zcloudconnector-edit-nss-server.png)
[]![Screenshot of Add NSS Server window in the Zscaler Cloud Connector Portal](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/adding-nss-servers-draft/zcloudconnector-add-nss-server.png)