# Configuring a DNS Gateway
Source: https://help.zscaler.com/unified/configuring-dns-gateway
PDF: https://help.zscaler.com/pdf/com/en/1519031.pdf

DNS gateways redirect the DNS request received by the Zscaler Cloud or Branch Connector to specific DNS servers. To learn more, see [About DNS Gateways](/unified/about-dns-gateways-0).
To add a DNS gateway:
- Go to **Infrastructure** > **Common Resources** >** Gateways** >** DNS**.
- Select the **DNS** **Gateway** tab.
-
Click **Add DNS Gateway**.
[See image.](#adddnsgatewaybutton)
The **Add DNS Gateway** window appears.
- In the **Add DNS Gateway** window:
- **Name**: Enter a user-friendly name for the gateway.
- **Primary DNS Server**: From the drop-down menu, select a primary DNS server:
- **Custom DNS Server**: Enter an IP address of your choice. Zscaler only supports IPv4 addresses.
- **LAN Primary DNS Server**: Select the local area network (LAN) primary DNS server to reference the primary LAN DNS server configured in gateway mode of the [Branch Connector Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template#GatewayLAN).
-
**LAN Secondary DNS Server**: Select the LAN secondary DNS server to reference the primary LAN DNS server configured in gateway mode of the [Branch Connector Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template#GatewayLAN).
In gateway mode of the Branch Connector Configuration Template, if the template dictates a WAN override, it uses WAN DNS resolvers. For non-gateway hardware devices, the LAN DNS servers default to the primary and secondary DNS servers configured in the forwarding interface section.
- **Secondary DNS Server**:** **From the drop-down menu, select a secondary DNS server:
- **Custom DNS Server**: Enter an IP address of your choice. Zscaler only supports IPv4 addresses.
- **LAN Primary DNS Server**: Select the LAN primary DNS server to reference the secondary LAN DNS server configured in gateway mode of the [Branch Connector Configuration Template](/unified/configuring-branch-configuration-template).
-
**LAN Secondary DNS Server**: Select the LAN secondary DNS server to reference the secondary LAN DNS server configured in gateway mode of the Branch Connector Configuration Template.
In gateway mode of the Branch Connector Configuration Template, if the template dictates a WAN override, it uses WAN DNS resolvers. For non-gateway hardware devices, the LAN DNS servers default to the primary and secondary DNS servers configured in the forwarding interface section.
-
**Failure Behavior**: Choose what happens if the DNS server is unreachable:
- **Return error response**: The DNS gateway returns the message `smedge will return SERVFAIL`.
- **Forward to Original DNS Server**: The DNS packet is sent to the original destination IP.
[See image.](#adddnsgatewaywindow)
-
Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
You can create up to 255 DNS gateways. To learn more, see [Ranges & Limitations](/unified/ranges-limitations#Rules).
[]![The Add DNS Gateway button on the DNS Gateway tab in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/forwarding-methods/configuring-dns-gateway/Add%20DNS%20Gateway%20button.png)
[]![The Add DNS Gateway window in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/forwarding-methods/configuring-dns-gateway/Add%20DNS%20Gateway%20window_0.png)