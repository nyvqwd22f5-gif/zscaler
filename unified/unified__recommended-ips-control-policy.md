# Recommended IPS Control Policy
Source: https://help.zscaler.com/unified/recommended-ips-control-policy
PDF: https://help.zscaler.com/pdf/com/en/1494311.pdf

You can configure the following recommended [IPS Control](/unified/about-ips-control) policy in the Admin Portal to leverage Zscaler's Intrustion Prevention System (IPS):
- **Rule Order**: Create this rule with a **Rule Order** of **1**. Since rules are evaluated in ascending numerical order, this rule is evaluated first.
- **Rule Status**: Select **Enabled**. Enabled rules are actively enforced.
- **Threat Categories**: Select **Any** to apply this rule to all threat categories, or select specific threat categories based on your organization's needs. Threat categories group common threats (e.g., viruses, botnets, exploits) together.
- **Action**: Select **Block/Drop**. This silently blocks packets that match the rule.
To learn more about how to configure this rule, see [Configuring IPS Control Policy](/unified/configuring-ips-control-policy).
![Screenshot of the recommended IPS Control policy.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/firewall/firewall-policies/recommended-ips-control-policy/zia-recommended-ips-policy.png)