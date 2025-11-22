# About NAT Control
Source: https://help.zscaler.com/zia/about-nat-control
PDF: https://help.zscaler.com/pdf/com/en/1399906.pdf

[Watch a video about Firewall Control](https://fast.wistia.net/embed/iframe/67lc77bxsf)
You can create rules that enable the Zscaler firewall to perform destination NAT and redirect traffic to specific IP addresses and ports. You cannot select network applications with your NAT Control rules.
Zscaler provides a predefined NAT rule, Zscaler Trusted DNS Resolver which is enabled by default. This rule directs your standard DNS traffic (dest:53) to the Zscaler Trusted DNS resolver but drops the iterative DNS queries as they are not supported. However, you can configure a separate NAT rule with a higher rank that redirects the iterative queries to an external DNS resolver.
You can also disable the predefined rule if you want to resolve all your standard DNS traffic using an external DNS provider that supports both iterative and recursive DNS queries (e.g., 8.8.8.8:53).
NAT Control policy provides the following benefits and enables you to:
- Define granular NAT Control rules to redirect network traffic based on customizable conditions to configurable internet destinations by performing destination NAT.
- Enhance your DNS performance by redirecting your users' DNS traffic to the Zscaler Trusted DNS Resolver to perform DNS resolution.
NAT policy-related activities are recorded and displayed in Firewall Insights Logs for all types of traffic, except for DNS traffic. NAT logs for DNS traffic are displayed in DNS Insights Logs. To learn more, see [About Insights Logs](/zia/about-insights-logs).
The Zscaler service does not monitor the health or the availability status of an endpoint to which NAT rules forward traffic. This means that NAT rules forward traffic to the specified destination irrespective of whether the destination endpoint is reachable or not. So, ensure that the NAT destination endpoint is always available to prevent connection failures.
About the NAT Control Page
On the NAT Control page (Policy > Firewall Control > NAT Control Policy), you can do the following:
- [Configure a NAT Control rule](/zia/configuring-nat-control-policy).
- View a list of all configured and predefined NAT Control policies. Here you can view the following:
- **Rule Order**: The policy rule's order number. NAT Control policy rules are evaluated in ascending numerical order. You can sort this column.
- **Admin Rank**: The assigned [admin rank](/zia/about-admin-rank) for the rule. This is visible only if admin ranking is enabled in the [Advanced Settings](/zia/about-advanced-settings#admin-ranking). You can sort this column.
- **Rule Name**: The name of the rule. You can sort this column.
- **Criteria**: Which criteria triggers the rule. You can sort this column.
- **Action**: Traffic that matches the criteria is redirected to the specified destination or port.
- **Label and Description**: The label and description of the policy rule, if available.
- [Edit or duplicate a NAT Control policy rule](/zia/editing-deleting-duplicating-items).
- [Modify the table and its columns](/zia/using-tables).
- Search for a NAT Control policy rule.
- Select one of the following **View by** option to see the NAT Control rules accordingly:
- **Rule Order**: Displays the rules based on the rule order. By default, the rules are listed in the ascending rule order.
[See image.](#rule-order-NAT-control)
- **Rule Label**: Displays the rules based on the rule labels. The rules are grouped under the associated rule labels.
You can expand or collapse all the rule labels using the **Expand All** or **Collapse All** buttons.
[See image.](#rule-label-NAT-control)
- Click **Recommended Policy** to view the policy Zscaler recommends.
- Click the **Firewall Filtering Policy** tab to configure the Firewall Filtering policies. To learn more, see [About Firewall Control](/zia/about-firewall-control).
![Screenshot of NAT Control Policy page showing buttons used to control this policy](/downloads/zia/documentation-knowledgebase/policies/firewall/nat-control/about-nat-control/ZIA-NAT-Control-Policy-Page.png)
[]![Screenshot of NAT Control Policy page with Rule Order view selected.](/downloads/zia/documentation-knowledgebase/policies/firewall/nat-control/about-nat-control/ZIA-NAT-Control-Policy-Page-Viewby-Rule-Order.png)
[]![Screenshot of NAT Control Policy page with Rule Label view selected.](/downloads/zia/documentation-knowledgebase/policies/firewall/nat-control/about-nat-control/ZIA-NAT-Control-Policy-Page-Viewby-Rule-Label.png)