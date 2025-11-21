# About Forwarding Control
Source: https://help.zscaler.com/unified/about-forwarding-control
PDF: https://help.zscaler.com/pdf/com/en/1497766.pdf

Forwarding Control is used to forward selective Zscaler traffic to specific destinations based on your needs. By configuring appropriate forwarding rules, you can forward specific web traffic to a [third-party proxy service](/unified/understanding-third-party-proxy-chaining), to a dedicated IP address provisioned for you, or to a Geo IP address mapped to your location. You can forward [source IP anchored](/unified/understanding-source-ip-anchoring) application traffic to a specific Zscaler Private Applications App Connector or internal application traffic through Internet & SaaS threat and data protection engines.
- Forwarding Control policies are applicable to traffic originating from a known location or a user using PAC files or Zscaler Client Connector with Z-Tunnel 2.0 and Z-Tunnel 1.0.
- Any Forwarding Control policy (including Source IP Anchoring) based on user conditions such as users, groups, and departments requires a subscription to the Advanced Firewall.
Forwarding Control provides the following benefits and enables you to:
- Forward traffic directly to the destination server using the Zscaler service IP address.
- Define criteria for traffic that needs to be forwarded to a third-party proxy service of your choice.
- Define criteria for traffic that needs to be forwarded through the dedicated IP gateway to specific destinations.
- Define criteria for traffic that needs to be forwarded through the Geo IP address mapped to the user's country.
- Redirect Source IP Anchored traffic to Private Applications App Connector through the Private Applications cloud.
- Forward selected traffic to Private Applications for scanning of internal applications.
The Forwarding Control policy provides you with the following predefined rules that help to forward traffic to Private Applications:
- **Fallback mode of ZPA Forwarding**: Forwards all source IP anchored traffic that matches the fallback Private Applications IP pools to Private Applications. This rule is disabled by default and cannot be deleted. It is only enabled during Internet & SaaS control plane maintenance.
- **ZIA Inspected ZPA Apps**: Forwards all Private Applications application segment traffic for Internet & SaaS inspection that has the Inspect Traffic with ZIA field enabled in the Admin Portal.
- **ZPA Pool For Stray Traffic**: Drops all Private Applications traffic that does not match any IP address range from the Private Applications IP pool.
The rules are enabled by default and cannot be deleted. You can only modify the Rule Label for these rules and cannot edit other attributes.
About the Forwarding Control Page
On the Forwarding Control page (Infrastructure > Internet & SaaS > Network Policies > Forwarding Control Policy), you can do the following:
- [Add a forwarding rule](/unified/configuring-forwarding-policy).
- View a list of all forwarding rules. For each forwarding rule, you can view the following information:
- **Rule Order**: The order of the rule.
- **Admin Rank**: The admin rank of the rule.
- **Rule Name**: The name of the rule.
- **Criteria**: The criteria defined for the rule.
- **Forwarding Method**: The forwarding method used in the rule. It can be Direct, Proxy Chaining, or Private Applications.
- **Gateway**: The gateway that is used to forward the traffic that hits the rule.
- **Status**: The status of the rule, which indicates if the rule is enabled or disabled.
- **Label and Description**: The label and description of the policy rule, if available.
- Edit a forwarding rule.
- Duplicate a forwarding rule.
- [Modify the table and its columns](/unified/using-tables).
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