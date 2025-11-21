# About Source IP Groups for Internet & SaaS
Source: https://help.zscaler.com/unified/about-source-ip-groups-internet-saas
PDF: https://help.zscaler.com/pdf/com/en/1494181.pdf

Source IP groups allow you to group and control source IP addresses in the [firewall policies](/unified/configuring-firewall-policies), the DLP policy rule [with content inspection](/unified/configuring-dlp-policy-rules-content-inspection) or [without content inspection](/unified/configuring-dlp-policy-rules-without-content-inspection), [URL filtering policy, ](/unified/configuring-url-filtering-policy)and the[ ](/zia/configuring-url-filtering-policy)[SSL inspection policy](/unified/configuring-ssl-inspection-policy).
Source IP groups provide the following benefits and enable you to:
- Group source IP addresses into a single entity to manage them collectively in security policies.
- Configure firewall filtering rules, NAT rules, DNS rules, IPS Control policies, forwarding rules, DLP rules, URL filtering rules, and SSL inspection rules based on source IP groups to control your inbound traffic and enforce condition-based actions on your network traffic.
The groups are created and managed for IPv4 and IPv6 addresses separately. The Zscaler service provides two predefined groups, namely All IPv4 and All IPv6, for encompassing all IP addresses of the respective type into a single group. In addition, you can create custom groups for IPv4 addresses by specifying individual, subnet, or range of addresses.
Custom groups for IPv6 addresses are not currently supported.
[]About the Source IPv4 Groups Page
On the Source IPv4 Groups page (Policies > Access Control > Firewall > IP & FQDN Groups), you can do the following:
- [Add a source IPv4 group](/unified/configuring-source-ip-groups).
- Search for a source IPv4 group.
- View a list of all source IPv4 groups. For each group, you can view:
- **Name**: The name of the source IPv4 group. You can sort this column.
- **IP Addresses**: The IPv4 addresses included in the group.
- **Description**: The description of the group, if available. You can sort this column.
- [Modify the table and its columns](/unified/using-tables).
- Edit a source IPv4 group.
- Go to the [Source IPv6 Groups](#ipv6), [Destination IPv4 Groups](/unified/about-destination-ip-groups#ipv4), [Destination IPv6 Groups](/unified/about-destination-ip-groups#ipv6), and [IP Pool](/unified/about-ip-pool) pages.
![Source IPv4 groups page](/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-policy-resources/about-source-ip-groups/ZIA-Source-IPv4-Groups.png)
[]About the Source IPv6 Groups Page
On the Source IPv6 Groups page (Policies > Access Control > Firewall > IP & FQDN Groups > Source IPv6 Groups), you can do the following:
- View information about the predefined **All IPv6** group.
- [Modify the table and its columns](/unified/using-tables).
- Go to the [Source IPv4 Groups](#ipv4), [Destination IPv4 Groups](/unified/about-destination-ip-groups#ipv4), [Destination IPv6 Groups](/unified/about-destination-ip-groups#ipv6), and [IP Pool](/unified/about-ip-pool) pages.
![Source IPv6 groups page](/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-policy-resources/about-source-ip-groups/ZIA-Source-IPv6-Groups.png)