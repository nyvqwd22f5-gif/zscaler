# Configuring ZPA Gateway
Source: https://help.zscaler.com/zia/configuring-zpa-gateway
PDF: https://help.zscaler.com/pdf/com/en/1401526.pdf

You need to configure Zscaler Private Access (ZPA) gateways in the ZIA Admin Portal to map them to the [ZPA server groups](/zpa/about-server-groups) and its associated [application segments](/zpa/about-applications) that require [Source IP Anchoring](/zia/about-source-ip-anchoring).
To forward traffic through ZPA gateways, ensure that your ZIA tenant is paired with your ZPA tenant with Source IP Anchoring enabled.
To configure a ZPA gateway:
- Go to **Administration** > **Zscaler Private Access**.
-
Click **Add Gateway for ZPA**.
[See image](#access-zpa)
The **Add Gateway for ZPA** window appears.
-
In the **Add Gateway for ZPA** window:
- **Gateway Name**: Enter a name for the gateway.
- **Server Group**: From the drop-down menu, select the server group that you configured on ZPA for Source IP Anchoring.
- **Application Segment**: After you select the server group, all the application segments (with Source IP Anchoring enabled) associated with the server group appear in this field.
- **Description**: (Optional) Enter additional notes or information for the gateway.
[See image.](#add-zpa-gateway-image)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![The Add Gateway for ZPA option on the Zscaler Private Access page in the ZIA AdminPortal](/downloads/zia/policies/forwarding-control/dedicated-ip/customer-managed-dedicated-ip-source-ip-anchoring/configuring-zpa-gateway/ZIA-configuring-zpa-gateway-add-zpa-gateway-button.png)
![The Add ZPA Gateway window in the Zscaler Private Access page](/downloads/zia/policies/forwarding-control/dedicated-ip/customer-managed-dedicated-ip-source-ip-anchoring/configuring-zpa-gateway/ZIA-configuring-zpa-gateway-add-zpa-gateway-window.png)
[]