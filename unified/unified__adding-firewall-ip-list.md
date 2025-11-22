# Adding a Firewall IP List
Source: https://help.zscaler.com/unified/adding-firewall-ip-list
PDF: https://help.zscaler.com/pdf/com/en/1533782.pdf

You can add a list of host and remote IP addresses, ports, and protocols to use for inbound and outbound firewall rules when adding a ruleset to manage endpoint firewall rules to use with location-based policies. To learn more, see [About Location-Based Policies](/unified/about-location-based-policies).
This feature is available only for Zscaler Client Connector version 4.8 and later for Windows. Contact Zscaler Support to enable this feature.
To add a firewall IP list:
- Go to **Infrastructure **>** Connectors **>** Client** > **Location-Based Policies**.
-
Select the **Firewall IP Lists** tab and click **Add IP List**.
[See image.](#firewall-ip-list-tab)
The **Add Firewall IP List** window appears.
[See image.](#add-firewall-ip-list-window)
- In the **Add Firewall IP List** window:
- **Name**: Enter a unique alphanumeric name for your list.
-
**IPv4 Addresses**: Enter a 5-tuple value with each field separated by a colon (i.e., `hostIP:hostport:remoteIP:remoteport:protocol`). For example, to define an inbound 5-tuple that allows inbound access from the `172.23.10.0/24` network to the host's default RDP port, enter `*:3389:172.23.10.0/24:*:tcp`.
The following formats are supported:
- An IP address, subnet using CIDR notation, or wildcard (e.g., `192.0.2.1`, `192.0.2.0/24`, or `*`)
- A port, port range, or port wildcard (e.g., `:80`, `:80-100`, or `:*`)
- A protocol or wildcard (e.g., `:tcp`, `:udp`, or `:*`)
You can click **Download CSV** to download a comma-separated value file with the entries in the list, and you can click **Upload CSV** to upload a comma-separated value file that replaces the existing entries. The maximum number of characters is 65,535 (approximately 1,213 IPv4 5-tuples).
-
**IPv6 Addresses**: Enter a 5-tuple value with each field separated by a colon (i.e., `[hostIP]:hostport:[remoteIP]:remoteport:protocol`).
- An IP address, subnet using CIDR notation, or wildcard (e.g., `[2001:db8:1::18]`, `[2001::db8:2::/64]`, `[::/0]`, or `[*]`)
- A port, port range, or port wildcard (e.g., `:4000`, `:5060-5061`, or `:*`)
- A protocol or wildcard (e.g., `:tcp`, `:udp`, or `:*`)
You can click **Download CSV** to download a comma-separated value file with the entries in the list, and you can click **Upload CSV** to upload a comma-separated value file that replaces the existing entries. The maximum number of characters is 65,535 (approximately 600 IPv6 5-tuples).
- **List Description**: Enter any notes regarding the list.
- Click **Save**.
You can enter a maximum of 300 firewall IP lists. After you create a list, you can select it in [inbound](/unified/adding-ruleset#inbound-rule) and [outbound](/unified/adding-ruleset#outbound-rule) firewall rules when adding a ruleset.
[]![Firewall IP Lists tab](/downloads/zscaler-client-connector/location-based-policies/adding-domain-list/zclient-connector-firewall-ip-lists-tab.png)
[]
![Add Firewall IP List window](/downloads/zscaler-client-connector/location-based-policies/adding-domain-list/zclient-connector-add-firewall-ip-list.png)