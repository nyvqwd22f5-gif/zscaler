# Adding a Traffic Steering IP List
Source: https://help.zscaler.com/zscaler-client-connector/adding-traffic-steering-ip-list
PDF: https://help.zscaler.com/pdf/com/en/1532878.pdf

You can add a list of IP addresses to use for IP inclusions and exclusions when adding a ruleset for traffic steering to use with location-based policies. To learn more, see [About Location-Based Policies](/zscaler-client-connector/about-location-based-policies).
This feature is available only for Zscaler Client Connector version 4.8 and later for Windows. Contact Zscaler Support to enable this feature.
The following default lists are provided:
- **Default IP Inclusion List**: Includes `0.0.0.0/0` for IPv4 Addresses.
-
**Default IP Exclusion List**:
- For IPv4 addresses, includes the `224.0.0.0/4` multicast range, the `169.254.0.0/16` link-local range, the `255.255.255.255` broadcast address, and the RFC 1918 default private networks (`10.0.0.0/8`, `172.16.0.0/12`, `192.168.0.0/16`). To learn more, refer to [RFC 1918 Address Allocation for Private Internets](https://datatracker.ietf.org/doc/html/rfc1918).
- For IPv6 addresses, includes the `FF00::/8` multicast range, the `FE80::/10` link-local range, and the `FC00::/7` unique local range.
These lists are view only, but you can click **Download CSV** to download a comma-separated value file with the entries in the list. You can use these default lists as is in the rulesets, or you can copy the values to include in a custom list.
To add an IP list:
- Go to **Administration** > **Location-Based Policies**.
-
Select the **Traffic Steering IP Lists** tab and click **Add IP List**.
[See image.](#traffic-steering-ip-list-tab)
The **Add Traffic Steering IP List** window appears.
[See image.](#add-traffic-steering-ip-list-window)
- In the **Add Traffic Steering IP List** window:
- **Name**: Enter a unique alphanumeric name for your list.
-
**IPv4 Addresses**: Enter the specific subnets in the following formats:
- An IP address, subnet, or wildcard (e.g., `192.0.2.1`, `192.0.2.0/24`, or `*`)
- An IP:Port, IP:Port range, or IP:Port wildcard (e.g., `192.0.2.1:80`, `192.0.2.1:80-100`, or `192.0.2.1:*`)
- An IP:Port:Protocol or IP:Port:Protocol wildcard (e.g., `192.0.2.1:80:tcp`, `192.0.2.1:80-100:udp`, or `192.0.2.1:80:*`)
You can click **Download CSV** to download a comma-separated value file with the entries in the list, and you can click **Upload CSV** to upload a comma-separated value file that replaces the existing entries. The maximum number of characters is 6,144 (approximately 682 IPv4 addresses).
-
**IPv6 Addresses**: Enter the specific subnets in the following formats:
- An IP address, subnet, or wildcard (e.g., `[2001:0000::]`, `[2001::/32]`, or `[*]`)
- An IP:Port, IP:Port range, or IP:Port wildcard (e.g., `[2001:0000::]:80`, `[2001:0000::]:80-100`, or `[2001:0000::]:*`)
- An IP:Port:Protocol or IP:Port:Protocol wildcard (e.g., `[2001:0000::]:80:tcp`, `[2001:000::/32]80-100:udp]`, or `[2001:0000::]:80:*`)
You can click **Download CSV** to download a comma-separated value file with the entries in the list, and you can click **Upload CSV** to upload a comma-separated value file that replaces the existing entries. The maximum number of characters is 6,144 (approximately 307 IPv6 addresses).
- **List Description**: Enter any notes regarding the list.
- Click **Save**.
You can enter a maximum of 300 traffic steering IP lists. After you create a list, you can select it in the IP Inclusion List and IP Exclusion List when [adding a ruleset](/zscaler-client-connector/adding-ruleset). You must use the list in a ruleset, and you cannot use it directly in an app profile.
[]![Traffic Steering IP Lists tab](/downloads/zscaler-client-connector/location-based-policies/adding-ruleset/zscaler-client-connector-traffic-steering-ip-lists.png)
[]
![Add Traffic Steering List IP window](/downloads/zscaler-client-connector/location-based-policies/adding-ruleset/zclient-connector-add-traffic-steering-ip-list.png)