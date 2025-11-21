# Configuring a Log and Control Gateway
Source: https://help.zscaler.com/unified/configuring-log-and-control-gateway
PDF: https://help.zscaler.com/pdf/com/en/1519131.pdf

You can configure a log and control gateway to control the traffic logs and the operational messages that are forwarded to the Zscaler cloud. This gateway allows you to define a primary proxy and a secondary proxy to which the traffic can be forwarded.
To configure a log and control gateway:
- Go to **Infrastructure **>** Common Resources** > **Gateways** > **Log and Control**.
- Click **Add Log And Control Gateway**.
- Enter the following information in the window:
- **Name**: Enter a user-friendly name for the gateway.
- **Primary**: Select the primary proxy for the gateway.
- **Automatic**: Forwards traffic through an automatic proxy.
- **Manual**: Forwards traffic through the selected data centers.
- **Override**: Forwards traffic through the specified IP address or domain name.
- **Secondary**: Select the secondary proxy for the gateway. This is used when the primary proxy is unreachable.
- **Automatic**: Forwards traffic through an automatic proxy.
- **Manual**: Forwards traffic through the selected data centers.
- **Override**: Forwards traffic through the specified IP address or domain name.
-
**Description**: (Optional) Enter additional notes or information.
[See image.](#LogControlGatewayWindow)
- Click **Save** and [activate the changes](/unified/saving-and-activating-changes-admin-portal).
[]
[![Log and Control Gateway Configuration Window in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/administration/forwarding-methods/configuring-zia-gateway/add%20log%20and%20control%20gateway%20window.jpg)
]