# Configuring Trusted Networks for Zscaler Client Connector
Source: https://help.zscaler.com/unified/configuring-trusted-networks-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1494986.pdf

To have Zscaler Client Connector identify one of your organization’s [trusted networks](/unified/about-trusted-networks), you must define conditions for that network as criteria that Zscaler Client Connector uses for verification.
To configure criteria for a trusted network:
- In the Admin Portal, go to **Infrastructure > Locations > Trusted Networks**.
-
Click **Add Trusted Network**.
The **Add Trusted Network** window appears.
-
In the **Add Trusted Network** window:
- For **Network Definition**: In the **Network Name** field, enter a unique alphanumeric name for the trusted network.
-
For **Trusted Network Criteria**: Define the network information and conditions that your network must meet in order for Zscaler Client Connector to verify that it's one of your trusted networks.
To configure the Trusted Network Criteria:
-
**Add Condition**: Select one of the following conditions, then click the **Add Condition** button.
Zscaler recommends using static properties, such as **DNS Server** and **DNS Search Domains**, for Trusted Network Criteria. In contrast, **Hostname and IP** resolution is a dynamic property because Zscaler Client Connector must resolve a hostname to see if it resolves to the IP address specified in Trusted Network Criteria. There is a chance that a resolution might fail because of network transition processes. If a resolution fails, the app could incorrectly determine that the network is an untrusted one, in which case it applies the incorrect forwarding profile action.
- **DNS Server**: The DNS servers to which your corporate network sends DNS requests. Enter the DNS servers, separated by commas. IPv6 addresses are supported if you’re using Zscaler Client Connector version 3.4 and later for Windows. The app verifies at least one DNS server.
- **DNS Search Domains**: The search domains configured as the primary domains for the network adapter used for connecting to Zscaler. Enter the search domains, separated by commas. The app only verifies the primary domains assigned to the active network adapter.
- **Hostname and IP**: A hostname and the IP addresses to which the hostname resolves when users are on the corporate network. For **Hostname**, enter the hostname. For **Resolved IPs for Hostname**, enter the IP addresses that the hostname resolves to, separated by commas. IPv6 addresses are supported if you’re using Zscaler Client Connector version 3.4 and later for Windows. The app verifies at least one IP address.
- **Network Range**: The network range for subnets and private IPs. Enter the valid network ranges, separated by commas.
- **Default Gateway**: Enter the IP address of the default gateway to the internet.
- **DHCP Server**: Enter the valid DHCP server, separated by commas.
- **Egress IP**: Enter the egress IP address of the network. This option allows you to differentiate a location that matches the trusted network criteria of other locations. Applies only to Zscaler Client Connector version 4.6 and later for Windows.
Repeat this step if you want to specify more than one condition.
- **Condition Match**: This field appears after you configure a condition.
- If specifying only one condition for the criteria, skip this step.
- If specifying multiple conditions for the criteria, select one of the following options:
- **Any**: Select if you want the app to validate only one of the conditions to determine if the network is trusted.
- **All**: Select if you want the app to validate all of the conditions to determine if the network is trusted.
[See image.](#network-definition-and-criteria)
- Click **Save**.
[]
![Add Network Definition and Network Criteria.](/downloads/zscaler-client-connector-trusted-network-criteria.png)