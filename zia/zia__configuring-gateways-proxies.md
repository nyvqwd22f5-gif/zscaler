# Configuring Gateways for Proxies
Source: https://help.zscaler.com/zia/configuring-gateways-proxies
PDF: https://help.zscaler.com/pdf/com/en/1401511.pdf

You can create gateway objects to configure the [Third-Party Proxy Chaining](/zia/about-third-party-proxy-chaining) feature which enables you to forward traffic to a third-party proxy service. A proxy gateway allows you to define a primary proxy and a secondary proxy to which the traffic can be forwarded from Zscaler and define how traffic should be handled when both the proxies are not reachable. You can also define if SSL inspection should be performed on the proxy chain traffic or not.
To configure a proxy gateway for the third-party proxy service:
- Go to **Administration** >** Proxies & Gateways **page.
- Select the **Proxy** **Gateways** tab.
- Click **Add Gateway for Proxies**. The **Add Gateway for Proxies** window appears.
- Enter the following information:
- **Gateway Name**: Enter a user-friendly name for the gateway to be created for a third party proxy service.
- **Fail Close**: Choose how to handle the traffic when both primary and secondary proxies defined in this gateway are unreachable:
- **Enable**: (Default) Drops the traffic when both proxies are unreachable.
- **Disable**: Allows the traffic directly to the web server without forwarding it to the proxy service when both proxies are unreachable.
- **Primary Proxy**: Select the primary proxy for the gateway. For information on configuring a proxy, see [Configuring Third-Party Proxies](/zia/configuring-third-party-proxies).
- **Secondary Proxy**: Select the secondary proxy for the gateway. This is used when the primary proxy is unreachable.
- **Description**: (Optional) Enter additional notes or information. The description cannot exceed 256 characters.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
You can create up to 32 gateway objects.