# Editing the Default Firewall Filtering Rule
Source: https://help.zscaler.com/zia/editing-default-firewall-filtering-rule
PDF: https://help.zscaler.com/pdf/com/en/1399896.pdf

The Firewall Filtering policy has one default rule, which handles all the traffic that does not match any user-defined rule with a higher rule order. The default rule always maintains the lowest precedence and cannot be deleted. Only admins with the [super admin role](/zia/what-super-admin-role) can modify the default rule.
To edit the default Firewall Filtering rule:
- Go to **Policy **>** Firewall Control**.
- Navigate to the **Default Firewall Filtering Rule**, and click the **Edit** icon.
[See image.](#seeimage1)
- In the **Edit Firewall Filtering Rule** window, you can view and modify the following fields:
- **Rule Label**: Choose a [rule label](/zia/about-rule-labels) to associate it with the rule.
- **Network Traffic**: Choose a network traffic action.
- **Allow**: Allows packets that match the rule to pass through the firewall.
- **Block/Drop**: Silently drops all packets that match the rule. This is the default action.
- **Block/ICMP**: Drops all packets that match the rule and sends the client an ICMP error message of Type 3 (Destination Unreachable) and Code 13 (Communication Administratively Prohibited).
- **Block/Reset**: For TCP traffic, the Zscaler service drops all packets that match the rule and sends the client a TCP reset (a TCP packet with the *reset* (RST) flag is set to 1 in the TCP header, indicating that the TCP connection must be instantly stopped). For non-TCP traffic, this is the same as **Block/Drop**.
- **Logging**: Choose the logging action.
- **Aggregate**: The service groups together individual sessions based on the user, rule, network service, and network application and records the sessions periodically. Log aggregation happens approximately every 15 minutes.
-
**Full**: The service logs all sessions of the rule individually, except HTTP(S).
In Standard Firewall, full logging is supported only for Block rules. Full logging for all other rules requires the Full Logging license or Advanced Firewall.
[See image.](#seeimage2)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![A screenshot of the default firewall filtering rule](/downloads/zia/policies/firewall/firewall-control/firewall-filtering/editing-default-firewall-filtering-rule/default_firewall_filtering_rule.png)
[]![Screenshot of the Edit Firewall Filtering Rule window for the default rule](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/firewall/firewall-policies/editing-default-firewall-filtering-rule/ZIA-Edit-Firewall-Filtering-Rule-Window.png)