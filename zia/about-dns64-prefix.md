# About the DNS64 Prefix
Source: https://help.zscaler.com/zia/about-dns64-prefix
PDF: https://help.zscaler.com/pdf/com/en/1404796.pdf

The DNS64 prefix is an IPv6 address prefix used by Zscaler's purpose-built DNS64 mechanism to synthesize AAAA records from A records returned for servers that can be reached via IPv4. Zscaler facilitates the DNS64 mechanism with its own default IPv6 prefix and the well-known prefix (64:ff:9b::/96), without requiring any additional configurations by ZIA administrators. However, organizations can configure and use their network-specific DNS64 prefixes instead of the default prefixes supported by Zscaler. You can designate one of the configured [NAT64 prefixes](/zia/about-nat64-prefixes) as the DNS64 prefix for your organization. You can also configure a DNS64 prefix for individual locations and override the global DNS64 prefix for those locations. For more information, see [Configuring Locations](/zia/configuring-locations).
Zscaler's support for the DNS64 prefix provides the following benefits:
- Enable synthesizing of AAAA records for IPv4 destinations using the DNS64 mechanism.
- Allow flexibility in prefix selection for synthetic IPv6 addresses by supporting Zscaler's default prefix, the well-known prefix (64:ff9b::/96), and an organization's network-specific prefix.
DNS64 prefix selection by Zscaler from the prefixes available at different sources follows a specific order, as explained in the following bulleted list:
- Zscaler Client Connector-Shared Prefix
- Customer-configured prefix for a location in the ZIA Admin Portal
- Customer-configured prefix for an organization in the ZIA Admin Portal
- Zscaler's default prefix for the cloud on which your organization is provisioned
- Well-known prefix for NAT64 (64:ff9b::/96)
To learn more, see [Understanding IPv6 Support](/zia/understanding-ipv6-support).
About the DNS64 Prefix page
On the DNS64 Prefixes page (Administration > IPv6 Configuration), you can do the following:
- [Configure DNS64 prefix at the organization level.](/zia/configuring-ipv6-settings#configure-dns64-prefix)
- View the DNS64 prefix configured at the organization level. You can view:
- **Name**: The name of the DNS64 prefix.
- **Prefix/Mask**: The DNS64 prefix and the subnet mask for the prefix.
- **Description**: The description of the DNS64 prefix.
- [Edit the DNS64 prefix.](/zia/editing-deleting-duplicating-items)
- [Modify the table and its columns.](/zia/how-do-i-use-tables-admin-portal)
- Search for a DNS64 prefix.
- Go to the [NAT64 prefixes](/zia/about-nat64-prefixes) and Settings pages.
![A screenshot of the DNS64 Prefix page ](/downloads/zia/traffic-forwarding/ipv6/about-dns64-prefix/dns64-prefix-page_0.png)