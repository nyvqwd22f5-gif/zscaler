# About Destination IP Groups
Source: https://help.zscaler.com/zia/about-destination-ip-groups
PDF: https://help.zscaler.com/pdf/com/en/1400196.pdf

[Watch a video about IP and FQDN Groups](https://fast.wistia.net/embed/iframe/t9xati8hoh)
You can create groups of destination IP addresses, countries where servers are located, and [URL categories](/zia/about-url-categories), and apply firewall policies to them.
Destination IP groups provide the following benefits and enable you to:
- Combine destination IP addresses and FQDNs, destination countries, and URL categories into groups to manage them collectively in security policies.
- Use destination IP groups as rule criteria in [Firewall Filtering](/zia/configuring-firewall-filtering-policy), [NAT Control](/zia/configuring-nat-control-policy), [DNS Control](/zia/configuring-dns-control-policy), [IPS Control](/zia/configuring-ips-control-policy), and [Forwarding Control](/zia/configuring-forwarding-policy) rules to control your outbound traffic and enforce condition-based actions on your network traffic.
These destination groups are created and managed for IPv4 and IPv6 addresses separately. The Zscaler service provides two predefined groups, namely All IPv4 and All IPv6, for encompassing all IP addresses of the respective type into a single group. You can also create custom groups based on IPv4 addresses.
- In [SSL Inspection](/zia/configuring-ssl-inspection-policy) and [DNS Control](/zia/configuring-dns-control-policy) policies, IP-based destination groups used in rule criteria are ignored during policy evaluation if an SNI value is present in HTTPS requests.
- Custom groups based on IPv6 addresses are not currently supported.
[]About the Destination IPv4 Groups Page
On the Destinations IPv4 Groups page (Administration > IP & FQDN Groups), you can do the following:
- [Configure a destination IPv4 group](/zia/configuring-destination-ip-groups).
- View a list of all destination IPv4 groups. For each IPv4 group, you can view:
- **Name**: The name of the destination group. You can sort this column.
- **Type**: The type of the destination group. The destination group type can either be **IP Address**, **FQDN**, **Wildcard FQDN**, or **Other**.
- **IP Address, FQDN or Wildcard FQDN**: The IP addresses, FQDNs, or wildcard FQDNs included in the group.
- **Countries**: The countries included in the group.
- **Description**: The description of the group, if available. You can sort this column.
- **Categories:** The custom URL categories included in the group.
- [Edit a destination IPv4 group](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal).
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
- Search for a destination IPv4 group.
- Go to the [Source IPv4 Groups](/zia/about-source-ip-groups#ipv4), [Source IPv6 Groups](/zia/about-source-ip-groups#ipv6), [Destination IPv6 Groups](#ipv6), and [IP Pool](/zia/about-ip-pool) pages.
![Destination IPv4 Groups page](/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-policy-resources/about-destination-groups/destination-ipv4-group.png)
[]About the Destination IPv6 Groups Page
On the Destination IPv6 Groups page (Administration > IP & FQDN Groups), you can do the following:
- View the details of the predefined **All IPv6** group.
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
- Go to the [Source IPv4 Groups](/zia/about-source-ip-groups#ipv4), [Source IPv6 Groups](/zia/about-source-ip-groups#ipv6), [Destination IPv4 Groups](#ipv4), and [IP Pool](/zia/about-ip-pool) pages.
![Destination IPv6 groups page](/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-policy-resources/about-destination-groups/destination-ipv6-group.png)