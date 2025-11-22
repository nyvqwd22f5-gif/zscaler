# About Forwarding Control
Source: https://help.zscaler.com/zia/about-forwarding-policies
PDF: https://help.zscaler.com/pdf/com/en/1401491.pdf

Forwarding Control is used to forward selective Zscaler traffic to specific destinations based on your needs. By configuring appropriate forwarding rules, you can forward specific web traffic to a [third-party proxy service](/zia/about-third-party-proxy-chaining), to a [dedicated IP address](/zia/understanding-zscaler-managed-dedicated-ip) provisioned for you, or to a [geo IP address](/zia/understanding-geolocalization-ip) mapped to your country. You can forward [source IP anchored](/zia/about-source-ip-anchoring) application traffic to a specific Zscaler Private Access (ZPA) App Connector or internal application traffic through ZIA threat and data protection engines.
- Forwarding Control policies are applicable to traffic originating from a known location or a user using PAC files or Zscaler Client Connector with Z-Tunnel 2.0 and Z-Tunnel 1.0.
- Any Forwarding Control policy (including Source IP Anchoring) based on user conditions such as users, groups, and departments requires a subscription to the Advanced Firewall.
Forwarding Control provides the following benefits and enables you to:
- Forward traffic directly to the destination server using the Zscaler service IP address.
- Define criteria for traffic that needs to be forwarded to a third-party proxy service of your choice.
- Define criteria for traffic that needs to be forwarded through the dedicated IP gateway to specific destinations.
- Define criteria for traffic that needs to be forwarded through the Geo IP address mapped to the user's country.
- Redirect Source IP Anchored traffic to ZPA App Connector through the ZPA cloud.
- Forward selected traffic to ZPA for scanning of internal applications.
The Forwarding Control policy provides you with the following predefined rules that help to forward traffic to ZPA:
- **Fallback mode of ZPA Forwarding**: Forwards all source IP anchored traffic that matches the fallback ZPA IP pools to ZPA. This rule is disabled by default and cannot be deleted. It is only enabled during ZIA control plane maintenance.
- **ZIA Inspected ZPA Apps**: Forwards all ZPA application segment traffic for ZIA inspection that has the Inspect Traffic with ZIA field enabled in the ZPA Admin Portal.
- **ZPA Pool For Stray Traffic**: Drops all ZPA traffic that does not match any IP address range from the ZPA IP pool.
The predefined rules are enabled by default and cannot be deleted. You can only modify the Rule Label for these rules and cannot edit other attributes.
If your organization has [Extranet Application Support](/zia/understanding-extranet-application-support) enabled, the following default rules are added:
- **Allow Extranet DNS Traffic**: Allows DNS traffic from extranet locations.
- **Extranet Traffic to ZPA**: Forwards all extranet traffic to ZPA.
- **Stray Extranet Traffic from ZPA**: Drops all extranet traffic that does not match any IP address range from any extranet IP pool. A default IP pool is created for extranet traffic, and you can configure custom IP pools for extranet traffic as well. To learn more, see [About IP Pool](/zia/about-ip-pool).
To access Extranet Application Support, contact your Zscaler Account team.
About the Forwarding Control Page
On the Forwarding Control page (Policies > Forwarding Control), you can do the following:
- [Add a forwarding rule](/zia/configuring-forwarding-policies).
- View a list of all forwarding rules. For each forwarding rule, you can view the following information:
- **Rule Order**: The order of the rule.
- **Admin Rank**: The admin rank of the rule.
- **Rule Name**: The name of the rule.
- **Criteria**: The criteria defined for the rule.
- **Forwarding Method**: The forwarding method used in the rule. It can be Direct, Proxy Chaining, or ZPA.
- **Gateway**: The gateway that is used to forward the traffic that hits the rule.
- **Status**: The status of the rule, which indicates if the rule is enabled or disabled.
- **Label and Description**: The label and description of the policy rule, if available.
- [Edit a forwarding rule](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal).
- [Duplicate a forwarding rule](/zia/editing-deleting-duplicating-items).
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
- Search for a forwarding rule.
- Select one of the following **View by** option to see the forwarding rules:
-
**Rule Order**: Displays the rules based on the rule order. By default, the rules are listed in the ascending rule order.
[See image.](#rule-order-forwarding-policy)
-
**Rule Label**: Displays the rules based on the rule labels. The rules are grouped under the associated rule labels.
You can expand or collapse all the rule labels using the **Expand All** or **Collapse All** buttons.
[See image.](#rule-label-forwarding-policy)
![Screenshot of Forwarding Control page showing buttons and list used to manage Zscaler Forwarding Policies](/downloads/zia/policies/forwarding-control/about-forwarding-control/ZIA-forwarding-rules-page.png)
[]![Screenshot of Forwarding Control page with Rule Order view selected.](/downloads/zia/policies/forwarding-control/about-forwarding-policies/ZIA-Forwarding-Control-Policy-Page-Viewby-Rule-Order.png)
[]![Screenshot of Forwarding Control page with Rule Label view selected.](/downloads/zia/policies/forwarding-control/about-forwarding-policies/ZIA-Forwarding-Control-Policy-Page-Viewby-Rule-Label.png)