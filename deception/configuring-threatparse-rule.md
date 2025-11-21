# Configuring a ThreatParse Rule
Source: https://help.zscaler.com/deception/configuring-threatparse-rule
PDF: https://help.zscaler.com/pdf/com/en/1531549.pdf

You can create custom ThreatParse rules using various attack parameters and conditions to reconstruct attack details into plain English. The rules are triggered by the ThreatParse engine when an event matching the rule conditions occurs, simplifying the threat analysis.
To create a custom ThreatParse rule:
- Go to **Miragemaker **> **ThreatParse Rules**.
-
Click **Add Rule**.
[See image.](#zd-tp-add-option)
-
In the **Rule Details** window:
- **Enabled**: Select to trigger the rule for matching attack events.
- **Title**: Enter a title for the ThreatParse rule.
- **Rule Type**: Select how the rule should be triggered. Select **Single **if the rule must be triggered by criteria defined for a single event. Select **Multi Attacker Facet **if the rule must be triggered by criteria defined across multiple events.
- **Description**: Enter a detailed description of the attack event. This is the actual natural language reconstruction of the attack event details.
- **Score**: Enter a risk score that you want to assign for the event if the rule is triggered.
- **Allowlist**: Enable to move the trigger source (client) to the allowlist if the rule is triggered.
- **Don't Show in UI**: Enable if you do not want to show the rule on the Investigate page if the rule is triggered.
- **Delete**: Enable to delete the event that triggered the rule.
- **Conditions**: Configure the conditions that must be used to trigger the rule. The conditions are created using the custom query language. To learn more about the custom query language, see [Understanding and Building Queries](/deception/understanding-and-building-queries).
- **Additional Details**: Add the following parameters as required:
- **Mitigation**: Enter an advisory on the next steps to be taken that can be used by the analysts.
- **MITRE ID**: Enter the MITRE ID if the rule is designed to detect a specific MITRE technique.
- **CVE ID**: Enter the CVE identifier associated with the vulnerability.
- **MITRE Tactic**: Enter the MITRE tactic if the rule is designed to detect a specific MITRE tactic.
- **Example Threat Groups**: Enter the examples of threat groups that have used this technique.
- **Important Event Fields**: Enter the most important event fields in the log for additional context.
[See image.](#zd-threatparse-add)
- Click **Submit**.
[]![A screenshot capturing the option to add new ThreatParse rule](/downloads/deception/miragemaker/threatparse-rules/configuring-threatparse-rule/zscaler-deception-add-rule-tp.png)
[]![A screenshot capturing the Rule Details Window](/downloads/deception/miragemaker/threatparse-rules/configuring-threatparse-rule/deception-rule-details-window.png)