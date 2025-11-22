# About NAT64 Prefixes
Source: https://help.zscaler.com/unified/about-nat64-prefixes
PDF: https://help.zscaler.com/pdf/com/en/1495061.pdf

A NAT64 prefix is used in the algorithmic translation of a synthetic IPv6 address to an IPv4 address. The Zscaler service provides a default NAT64 prefix, supports the well-known prefix (64:ff9b::/96), and also allows you to add your network-specific prefixes to the Admin Portal. During the NAT64 mechanism, these prefixes are used to match against the destination address prefix in the inbound IPv6 packets and derive an IPv4 address for the destination server. The extracted IPv4 address is then used to establish an IPv4 connection with the destination server from the Zscaler service. To learn more, see [Understanding IPv6 Support](/unified/understanding-ipv6-support).
NAT64 prefixes provide the following benefits and enable you to:
- Configure the DNS64 prefix used for synthesizing AAAA records for IPv4 destinations.
- Identify synthetic IPv6 addresses of destinations in inbound packets and extract IPv4 packets from those addresses.
- Establish a connection between IPv6 clients and IPv4 destinations (IPv4-only or dual-stack destinations) by performing address translation from IPv6 to IPv4 address using Zscaler's NAT64 mechanism.
About the NAT64 Prefixes Page
On the NAT64 Prefixes page (Infrastructure > Internet & SaaS > Traffic Forwarding > IPv6 Configurations > NAT64 Prefixes), you can:
- [Configure a NAT64 prefix.](/unified/configuring-ipv6-settings#configure-nat64-prefix)
- View a list of all the NAT64 prefixes configured. For each NAT64 prefix, you can view and sort:
- **Name**: The name of the NAT64 prefix.
- **Prefix/Mask**: The NAT64 prefix and the subnet mask for the prefix.
- **Description**: The description of the configured NAT64 prefix.
- Edit or delete a NAT64 prefix.
- [Modify the table and its columns.](/unified/using-tables)
- Search for a NAT64 prefix.
- Go to the [DNS64 Prefix](/unified/about-dns64-prefix) page.
- Go to the Settings page.
![A screenshot of the NAT64 Prefixes page](/downloads/zia/policies/ipv6/about-nat64-prefixes/nat64-prefix-page.png)