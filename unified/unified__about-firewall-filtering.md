# About Firewall Filtering
Source: https://help.zscaler.com/unified/about-firewall-filtering
PDF: https://help.zscaler.com/pdf/com/en/1494056.pdf

Firewall Filtering allows you to configure policies that define which types of your network traffic are allowed from specific sources and to reach specific destinations. It allows you to safeguard your network traffic by creating granular policies and enforcing condition-based actions on the traffic. Firewall Filtering rules can also be extended to traffic managed by the web proxy in specific cases when the rules contain Layer 3 or Layer 4 or FQDN conditions or when non-web traffic appears in flows managed by the web proxy. Zscaler's firewall offerings come in Standard and Advanced Firewall subscriptions. To learn more about the capabilities supported in each subscription, see [Understanding Firewall Capabilities](/unified/understanding-firewall-capabilities).
When the firewall is enabled, Zscaler's Default Firewall Filtering Rule blocks all traffic from your network to the internet. You must modify this rule or configure Firewall Filtering rules with a higher order to allow traffic.
Firewall Filtering provides the following benefits and enables you to:
- Protect your organization's internal network from unauthorized access or connections to the internet by monitoring and applying policies on all network traffic, particularly non-HTTP/HTTPS traffic or when non-web traffic appears on presumed web connections.
- Define granular Firewall Filtering rules using a number of conditions, such as users, groups, or departments, client locations, network services, network applications, source IP addresses, destination IP addresses/FQDNs, etc. Enforce condition-based actions on your traffic, such as allowing traffic, silently blocking traffic, or blocking traffic by informing clients about the firewall action.
- Extend the Firewall Filtering policy to traffic managed by web proxy using rules configured based on source IP address, destination IP address, or destination FQDN. For example, if a destination IP address is blocked by a firewall rule, then the web proxy would apply the rule and block the traffic. This is supported with Standard or Advanced Firewall subscription.
- Extend the Firewall Filtering policy to non-web traffic handed over to firewall by the web proxy with Advanced Firewall. For example, with the Advanced Firewall, if SSH (non-web traffic) uses destination port 443 (typically a secure web traffic port), the web proxy hands over that traffic to the firewall for full non-web identification and policy application.
- Identify web traffic that is bypassing the web proxy and forward it to the web proxy for policy application with Advanced Firewall. This requires [auto-proxy configuration](/unified/configuring-advanced-settings#auto-proxy-forwarding) in the Advanced Settings. For example, with the Advanced Firewall subscription, the firewall can identify web traffic that uses non-standard web ports and is not configured to go to the web proxy, or deliberately evasive web traffic, and forward it to the web proxy for complete web security coverage.
You can enable the firewall for specific locations by configuring the appropriate option for the location. To learn more, see [Configuring Locations](/unified/configuring-locations). If your organization uses Zscaler Tunnel (Z-Tunnel) 1.0 or PAC files to route traffic, ensure that the firewall is enabled for this type of traffic in the [Advanced Settings](/unified/configuring-advanced-settings#firewall-remote-users).
Firewall Filtering also includes a [dashboard](/unified/about-dashboards), giving your organization visibility into your networks. To see how this policy fits into the overall order of policy enforcement, see [About Policy Enforcement](/unified/understanding-policy-enforcement).
About the Firewall Filtering Page
For organizations that have subscribed to an enhanced limit for Firewall Filtering rules (4,000 rules), the following additional user interface elements are present:
- [Pagination](#pagination)
- [Category-Based Search](#category-search)
The enhanced limit for Firewall Filtering rules requires an audit for each proposed customer tenant seeking to upgrade. To learn more about the enhanced limit and the qualified use cases for an upgrade, contact your Zscaler Account team.
On the Firewall Filtering page (Policies > Access Control > Firewall > Firewall Filtering Policy), you can do the following:
- [Configure a Firewall Filtering rule](/unified/configuring-firewall-filtering-policy).
- View a list of all configured Firewall Filtering policy rules. For each rule, you can see the following:
- **Rule Order**: The rule order number. Firewall Filtering policy rules are evaluated in ascending numerical order. You can sort this column.
- **Admin Rank**: The Admin Rank for this rule. This is only visible if you have enabled it in the [Advanced Settings](/unified/configuring-advanced-settings). You can sort this column.
- **Rule Name**: The name of the policy rule. You can sort this column.
- **Criteria**: The policy rule's criteria (e.g., Users or Departments).
- **Action**: Displays the action for the policy rule (e.g., Allow).
- **Label and Description**: The label and description of the policy rule, if available.
- Edit or duplicate a Firewall Filtering policy rule.
- [Modify the table and its columns](/unified/using-tables).
- Search for a Firewall Filtering rule.
- Select one of the following **View by** option to see the Firewall Filtering rules accordingly:
-
**Rule Order**: Displays the rules based on the rule order. By default, the rules are listed in the ascending rule order.
[See image.](#rule-order-firewall-control)
-
**Rule Label**: Displays the rules by grouping them under the associated rule labels. You can expand or collapse all the rule labels using the **Expand All** or **Collapse All** buttons.
[See image.](#rule-label-firewall-control)
- View the [Recommended Firewall Filtering Policy](/unified/recommended-firewall-control-policy).
- View the NAT Control page. To learn more, see [About NAT Control](/unified/about-nat-control).
![Firewall filtering rules page](/downloads/zia/policies/firewall/firewall-control/firewall-filtering/about-firewall-filtering/ZIA-Firewall-Filtering-Page.png)
[]The Firewall Filtering rules are paginated with up to 100 rules displayed per page.
[See image.](#firewall-filtering-page-4K-rules-pagination)
[]A generic text search is replaced by category-based filtering, requiring the admin to select a specific category in which they want to search, and the search results span across all pages in the selected category. A wide range of search categories are available, enabling more granular and precise filtering.
[List of Search Categories](#search-filters)
[See image.](#firewall-filtering-page-4K-rules-search-categories)
- []Rule Label
- Rule Name
- Rule Order
- Description
- Action
- Location
- Department
- Group
- User
- Device
- Device Group
- Device Trust Level
- Source IP Addresses
- Destination IP Addresses
- Source IP Group
- Destination Group
- Network Application
- Network Services
- Destination IP Categories
[]![Firewall filtering rules page sorted by Rule Order](/downloads/zia/policies/firewall/firewall-control/firewall-filtering/about-firewall-filtering/ZIA-Firewall-Filtering-Page-SortBy-RuleOrder.png)
[]![Firewall filtering rules page sorted by Rule Label](/downloads/zia/policies/firewall/firewall-control/firewall-filtering/about-firewall-filtering/ZIA-Firewall-Filtering-Page-SortBy-RuleLabels.png)
[]![Firewall filtering rules search categories with 4K rules subscription](/downloads/zia/policies/firewall/firewall-control/firewall-filtering/about-firewall-filtering/Firewall-Filtering-Rules-Page-Search-Categories.png)
[]![Firewall filtering rules paginated with 4K rules subscription](/downloads/zia/policies/firewall/firewall-control/firewall-filtering/about-firewall-filtering/Firewall-Filtering-Rules-Paginated.png)