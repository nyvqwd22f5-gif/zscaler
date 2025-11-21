# About Traffic Capture Policy
Source: https://help.zscaler.com/zia/about-traffic-capture-policy
PDF: https://help.zscaler.com/pdf/com/en/1532181.pdf

Traffic Capture policy rules enable you to capture and store network traffic in PCAPNG file format with granular control of match criteria and how much traffic is captured. You must enable Traffic Capture in the Administration section, and link an Amazon S3 bucket to use the Traffic Capture policy. To learn more, see [Configuring Traffic Capture Settings](/zia/configuring-traffic-capture).
Traffic Capture policy rules can only be used on locations that have Firewall enabled.
The Traffic Capture policy provides the following benefits and enables you to:
- Engage in deep threat hunting and fast forensic investigation by providing raw traffic to reconstruct incidents with full visibility.
- Validate and analyze traffic behind security alerts, allowing analysts to confirm attacks, reduce false positives, and understand attacker techniques.
- Support testing and deploying new threat detection methods by leveraging captures for new custom IPS, tuning, and validation before broad roll-out.
- Meet regulatory compliance through traffic record retention, ensuring traceability and auditable evidence for compliance needs.
About the Traffic Capture Policy Page
On the Traffic Capture page (Policy > Traffic Capture), you can do the following:
- [Configure a Traffic Capture rule](/zia/configuring-traffic-capture-policy).
- Select one of the following **View by** option to see the Traffic Capture rules accordingly:
- **Rule Order**: Displays the rules based on the rule order. By default, the rules are listed in the ascending rule order.
- **Rule Label**: Displays the rules by grouping them under the associated rule labels. You can expand or collapse all the rule labels using the **Expand All** or **Collapse All** buttons.
- Search for a Traffic Capture rule.
- View a list of all configured Traffic Capture policy rules. For each rule, you can see the following:
- **Rule Order**: The policy rule's order number. Traffic Capture policy rules are evaluated in ascending numerical order. You can sort this column.
- **Rule Name**: The name of the policy rule. You can sort this column.
- **Criteria**: The policy rule's criteria (i.e., Users, Departments, etc.).
- **Action**: Displays either the action for the policy rule (Capture or Skip), or that the rule is disabled.
- **Label and Description**: The label and description of the policy rule, if available.
- **Admin Rank**: The admin rank for this rule. This is only visible if you have enabled it in the [Advanced Settings](/zia/about-advanced-settings). You can sort this column.
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
- [Edit or](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal)[ duplicate a Traffic Capture policy rule](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal).
![Traffic Capture policy page](/downloads/zia/policies/traffic-capture/about-traffic-capture-policy/ZIA-about-the-traffic-capture-policy.png)