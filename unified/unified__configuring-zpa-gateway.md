# Configuring ZPA Gateway
Source: https://help.zscaler.com/unified/configuring-zpa-gateway
PDF: https://help.zscaler.com/pdf/com/en/1497706.pdf

You need to configure ZPA gateways in the Admin Portal to map it to the Private Applications server groups and the associated application segments that require [Source IP Anchoring](/unified/understanding-source-ip-anchoring).
To configure a ZPA gateway for Source IP Anchoring:
- Go to **Infrastructure** > **Internet & SaaS** > **Network Policies** > **Zscaler Private Access**.
- Click **Add Gateway for ZPA**. The **Add Gateway for ZPA** window appears.
- In the **Gateway** field, enter a name for the gateway.
- From the **Server Group** drop-down menu, select the server group that you configured on Private Applications for Source IP Anchoring. All the application segments that are associated with the selected server group for which Source IP Anchoring is enabled appear in the **Application Segment** field.
- Click **Save **and activate the change.