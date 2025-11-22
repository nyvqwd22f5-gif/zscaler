# About Destination IP Groups
Source: https://help.zscaler.com/cloud-branch-connector/about-destination-ip-groups
PDF: https://help.zscaler.com/pdf/com/en/1420381.pdf

Destination IP Groups simplify policy creation by grouping multiple IP addresses into one destination, reducing the chance for error to occur. You can create groups of destination IP addresses, countries where servers are located, and URL categories, and apply firewall policies to them.
Destination IP Groups provide the following benefits and enable you to:
- Configure security and forwarding policies for a group of destinations based on IP addresses and fully qualified domain names (FQDNs).
- Add and remove destinations from the group and apply the same policies to the workloads.
About the Destination IP Groups Page
On the Destinations IP Groups page (Administration > IP & FQDN Groups > Destination IP Groups), you can do the following:
- [Add a destination IP group](/cloud-branch-connector/configuring-destination-ip-groups).
Although destination IP groups can be created for Wildcard Domain and Other, these destination IP group types are currently not supported in Cloud & Branch Connector forwarding policies.
- View a list of all destination IP groups. For each group, you can view:
- **Name**: The name of the destination IP group.
- **Type**: The type of destination IP group.
- **IP Address Or FQDN Or WildCard FQDN**: The IP addresses and FQDNs included in the group.
- **Countries**: The countries included in this group.
- **Description**: The description of the group, if available.
-
View a list of predefined groups created by Zscaler. They are disabled by default, but you can enable them. Predefined rules appear based on the licenses enabled in your tenant:
- **LAN Destinations Group**: This group contains all LAN directly connected networks and configured static routes from a given Branch Connector.
- **WAN Destinations Group**: This group contains all WAN directly connected networks and DNS servers.
- **Zscaler Domains**: This group contains all Zscaler public cloud domains (i.e., Zscaler Internet Access (ZIA), Zscaler Private Access (ZPA), and Zscaler Digital Experience (ZDX)).
Predefined groups are only applicable to hardware devices deployed in gateway mode.
- [Edit a destination IP group](/cloud-branch-connector/editing-deleting-or-duplicating-items).
- [Delete a destination IP group](/cloud-branch-connector/editing-deleting-or-duplicating-items).
- View a destination IP group.
- Modify the table and its columns.
- Go to the** **[Source IP Groups](/cloud-branch-connector/about-source-ip-groups) page.
- Go to the** **[IP Pool](/cloud-branch-connector/about-ip-pool) page.
![The Destination IP Groups page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/firewall-filtering/about-destination-ip-groups/About%20Destination%20IP%20Groups%20MVP%201.1.png)