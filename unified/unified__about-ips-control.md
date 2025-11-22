# About IPS Control
Source: https://help.zscaler.com/unified/about-ips-control
PDF: https://help.zscaler.com/pdf/com/en/1494301.pdf

Zscaler's Intrusion Prevention System (IPS) uses signature-based detection to monitor and protect your network traffic from intrusion over all ports and protocols. Zscaler's IPS Control uses custom IPS signature rules built and updated by Zscaler's security research team, as well as signatures from industry-leading vendors. In addition to the signatures managed by Zscaler, you can create and deploy custom IPS signatures that are specific to your organization’s requirements. The Zscaler service monitors your traffic in real time using these signatures. As soon as the IPS has examined the contents of your traffic and found a pattern match, it can enforce your security policies inline.
IPS Control provides the following benefits and enables you to:
- Use signature-based detection to monitor your network traffic for malicious activities and prevent attacks by enforcing policies in real time.
- Define granular IPS Control rules using a number of conditions, such as users, groups, or departments, locations, threat categories, network services, source IP addresses, destination IP addresses/FQDNs, etc. Zscaler provides a default IPS rule that blocks all traffic. You can create granular policies of higher precedence (i.e., higher admin rank) than the default rule to explicitly allow specific traffic (e.g., IT Security group traffic matching threats) while blocking all other traffic via the default rule.
- Enforce condition-based actions on your network traffic, such as allowing or blocking traffic. You can also configure rules to allow specific types of traffic to bypass Zscaler's IPS.
- Enhance your security posture by employing custom IPS signatures built using the Snort syntax to identify specific threats.
- Leverage Zscaler Firewall logs to investigate and analyze threats detected in your network.
IPS Control enables you to defend your organization against threats from both web traffic and non-web traffic. This includes protection for HTTP, HTTPS, FTP, DNS, TCP, UDP, and IP-based ports and protocols. However, IPS Control based on [custom IPS signature rules](/unified/about-custom-ips-signature-rules) protects only non-web traffic. IPS Control also enables you to create granular rules for specific users, groups, departments, and so on.
You can enable IPS Control policies for specific locations by configuring the appropriate option for the location. To learn more, see [Enabling the Firewall for Locations](/unified/enabling-firewall-locations). If your organization uses Z-Tunnel 1.0 or PAC files to route traffic, ensure that the firewall is enabled for this type of traffic in the [Advanced Settings](/unified/configuring-advanced-settings). Threats detected in your network traffic are displayed under Firewall Insights > Logs. Threats detected in web-only traffic also appear on the Security Dashboard.
- IPS Control is available only with Advanced Firewall. For more information, see [Understanding Firewall Capabilities](/unified/understanding-firewall-capabilities). If you have [Advanced Threat Protection](/unified/configuring-advanced-threat-protection-policy) and IPS Control, rules created for Advanced Threat Protection are evaluated first.
- Only traffic that transits the [Internet & SaaS Private Service Edge](/unified/understanding-internet-saas-private-service-edge) or [Internet & SaaS Virtual Service Edge](/unified/about-internet-saas-virtual-service-edges) can be inspected against custom IPS signature rules. To leverage custom IPS signature rules, your organization must have one of these Internet & SaaS Service Edge deployments.
About the IPS Control Page
On the IPS Control page (Policies > Cybersecurity > Inline Security > IPS Control), you can do the following:
- [Configure an IPS Control rule](/unified/configuring-ips-control-policy).
- View a list of all configured IPS Control rules. For each rule you can view the following information:
- **Rule Order**: The policy rule's order number. IPS Control policy rules are evaluated in ascending numerical order. You can sort this column.
- **Admin Rank**: The assigned [admin rank](/unified/about-admin-rank) for the rule. This is visible only if admin ranking is enabled in the [Advanced Settings](/unified/configuring-advanced-settings#admin-ranking). You can sort this column.
- **Rule Name**: The name of this rule. You can sort this column.
- **Criteria**: A description of the different criteria that have been added to this rule.
- **Action**: The action configured for the policy rule.
- **Label and Description**: The label and description of the policy rule, if available.
- Edit, duplicate, or delete an IPS Control rule.
- [Modify the table and its columns](/unified/using-tables).
- Search for an IPS Control rule.
- Select one of the following **View by** options to see the IPS Control rules accordingly:
-
**Rule Order**: Displays the rules based on the rule order. By default, the rules are listed in the ascending rule order.
[See image.](#rule-order-IPS-control)
-
**Rule Label**: Displays the rules based on the rule labels. The rules are grouped under the associated rule labels.
You can expand or collapse all the rule labels using the **Expand All** or **Collapse All** buttons.
[See image.](#rule-label-IPS-control)
- View the [recommended IPS Control policy](/unified/recommended-ips-control-policy).
![Screenshot showing the features for the IPS Control page](/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-policies/ips-control/about-ips-control/ZIA-IPS-Control-Policy-Page.png)
[]![Screenshot of the IPS Control page with Rule Order view selected.](/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-policies/ips-control/about-ips-control/ZIA-IPS-Control-Policy-Page-Viewby-Rule-Order.png)
[]![Screenshot of the IPS Control page with Rule Label view selected.](/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-policies/ips-control/about-ips-control/ZIA-IPS-Control-Policy-Page-Viewby-Rule-Label.png)