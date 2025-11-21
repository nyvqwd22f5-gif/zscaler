# Configuring a ZIA Gateway
Source: https://help.zscaler.com/cloud-branch-connector/configuring-zia-gateway
PDF: https://help.zscaler.com/pdf/com/en/1420561.pdf

[Watch a video about ZIA gateways.](https://fast.wistia.net/embed/iframe/gv4u5q32dx)
You can create gateway objects to configure the proxy gateway which enables you to forward any traffic to specific destinations via Zscaler Internet Access (ZIA). A proxy gateway allows you to define a primary proxy and a secondary proxy to which the traffic can be forwarded and define how traffic should be handled when both the proxies are unreachable.
In the Add ZIA Gateway window:
- Go to **Administration** >** Gateways**.
- Select the **ZIA** **Gateway** tab.
-
Click **Add ZIA Gateway**.
[See image.](#AddZIAGateway)
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
Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
You can create up to 32 gateway objects. For more information, see [Ranges & Limitations](/cloud-branch-connector/ranges-limitations).
[![Adding a ZIA Gateway Configuration Window in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/administration/forwarding-methods/configuring-zia-gateway/Add%20ZIA%20Gateway%20window.jpg)
][]
[![Add ZIA Gateway Button in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/Add%20ZIA%20Gateway%20button.png)
][]