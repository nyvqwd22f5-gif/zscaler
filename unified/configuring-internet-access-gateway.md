# Configuring an Internet Access Gateway
Source: https://help.zscaler.com/unified/configuring-internet-access-gateway
PDF: https://help.zscaler.com/pdf/com/en/1519141.pdf

You can create gateway objects to configure the proxy gateway that enables you to forward any traffic to specific destinations via Zscaler Internet & SaaS. A proxy gateway allows you to define a primary proxy and a secondary proxy to which the traffic can be forwarded and define how traffic should be handled when both the proxies are unreachable.
To add an Internet Access gateway:
- Go to **Infrastructure** > **Common Resources** > **Gateways** > **Internet Access**.
- Click **Add Internet Access Gateway**.
- Enter the following information in the window:
- **Name**: Enter a user-friendly name for the gateway.
- **Fail Close**: Choose how to handle the traffic when both primary and secondary proxies defined in this gateway are unreachable.
- **Enable**: (Default) Drops the traffic when both proxies are unreachable.
- **Disable**: Allows the traffic directly to the server without forwarding it to the proxy service when both proxies are unreachable.
- **Primary**: Select the primary proxy for the gateway.
- **Automatic**: Forwards traffic through an automatic proxy.
- **Manual**: Forwards traffic through the selected data centers.
- **Override**: Forwards traffic through the specified IP address or domain name.
- **Secondary**: Select the secondary proxy for the gateway. This is used when the primary proxy is unreachable. The secondary proxy switches to the primary proxy upon confirmation of reachability.
- **Automatic**: Forwards traffic through an automatic proxy.
- **Manual**: Forwards traffic through the selected data centers.
- **Override**: Forwards traffic through the specified IP address or domain name.
-
**Description**: (Optional) Enter additional notes or information. The description cannot exceed 10,240 characters.
[See image.](#ZIAGateway)
-
Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
You can create up to 32 gateway objects. For more information, see [Ranges & Limitations](/unified/ranges-limitations#Rules).
[![Adding a ZIA Gateway Configuration Window in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/administration/forwarding-methods/configuring-zia-gateway/Add%20ZIA%20Gateway%20window.jpg)
][]