# About Destination IP Groups for Internet & SaaS
Source: https://help.zscaler.com/unified/about-destination-ip-groups-internet-saas
PDF: https://help.zscaler.com/pdf/com/en/1494191.pdf

You can create groups of destination IP addresses, countries where servers are located, and [URL categories](/unified/about-url-categories), and apply firewall policies to them.
Destination IP groups provide the following benefits and enable you to:
- Combine destination IP addresses/FQDNs, destination countries, and URL categories into groups to manage them collectively in security policies.
- Configure firewall filtering rules, NAT rules, DNS rules, IPS Control policies, and forwarding rules based on destination IP groups to control your outbound traffic and enforce condition-based actions on your network traffic.
The groups are created and managed for IPv4 and IPv6 addresses separately. The Zscaler service provides two predefined groups, namely All IPv4 and All IPv6, for encompassing all IP addresses of the respective type into a single group. You can also create custom groups based on IPv4 addresses.
Custom groups based on IPv6 addresses are not currently supported.
[]About the Destination IPv4 Groups Page
On the Destinations IPv4 Groups page (Policies > Access Control > Firewall > IP & FQDN Groups > Destination IPv4 Groups), you can do the following:
- [Configure a destination IPv4 group](/unified/configuring-destination-ip-groups).
- View a list of all destination IPv4 groups. For each IPv4 group, you can view:
- **Name**: The name of the destination group. You can sort this column.
- **Type**: The type of the destination group. The destination group type can either be **IP Address**, **FQDN**, **Wildcard FQDN**, or **Other**.
- **IP Address, FQDN or Wildcard FQDN**: The IP addresses, FQDNs, or wildcard FQDNs included in the group.
- **Countries**: The countries included in this group.
- **Description**: The description of the group, if available. You can sort this column.
- **Categories:** The custom URL categories included in this group.
- Edit a destination IPv4 group.
- [Modify the table and its columns](/unified/using-tables).
- Search for a destination IPv4 group.
- Go to the [Source IPv4 Groups](/unified/about-source-ip-groups#ipv4), [Source IPv6 Groups](/unified/about-source-ip-groups#ipv6), [Destination IPv6 Groups](#ipv6), and [IP Pool](/unified/about-ip-pool) pages.
![Destination IPv4 Groups page](/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-policy-resources/about-destination-groups/destination-ipv4-group.png)
[]About the Destination IPv6 Groups Page
On the Destination IPv6 Groups page (Policies > Access Control > Firewall > IP & FQDN Groups > Destination IPv6 Groups), you can:
- View the details of the predefined **All IPv6** group.
- [Modify the table and its columns](/unified/using-tables).
- Go to the [Source IPv4 Groups](/unified/about-source-ip-groups#ipv4), [Source IPv6 Groups](/unified/about-source-ip-groups#ipv6), [Destination IPv4 Groups](#ipv4), and [IP Pool](/unified/about-ip-pool) pages.
![Destination IPv6 groups page](/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-policy-resources/about-destination-groups/destination-ipv6-group.png)