# About ThreatParse Rules
Source: https://help.zscaler.com/deception/about-threatparse-rules
PDF: https://help.zscaler.com/pdf/com/en/1531548.pdf

ThreatParse is a technology used by Zscaler Deception to parse details of an attack event and translate them into plain English using natural language reconstruction. To translate those details, the ThreatParse engine uses rules that use multiple parameters such as risk score, conditions, MITRE ID, MITRE tactic, etc. By default, Zscaler Deception provides various ThreatParse rules for common attack events. You can also create custom rules suitable for your business needs.
ThreatParse Rules provide the following benefits and enable you to:
- Simplify analysis of details of an attack using [ThreatParse technology](/deception/about-threatparse-rules).
- Use various parameters such as risk score, conditions, MITRE ID, etc. to create custom rules to parse details of an attack event and translate them into plain English.
About the ThreatParse Rules Page
On the ThreatParse Rules Page (Miragemaker > ThreatParse Rules), you can do the following:
- View the list of default and custom ThreatParse rules, and search for a specific entry by name. For each ThreatParse rule, you can see:
- **Title**: The name of the ThreatParse rule.
- **Description**: The detailed description of when the rule triggers. This description is the natural language reconstruction of the attack event details.
- **Score**: The risk score that must be assigned to an attack event if the rule is triggered for the event.
- **Show in UI**: Indicates whether the rule must be shown if triggered on the [Investigate page](/deception/viewing-and-managing-zscaler-deception-dashboard). A green checkmark indicates that the rule is shown when a triggering event occurs, and a red X mark indicates that the rule is not shown when a triggering event occurs.
- **Enabled**: Indicates whether the rule is enabled or disabled. An enabled rule, indicated by a green checkmark, is triggered for events matching the rule conditions. A disabled rule, indicated by a red X mark, is not triggered for events matching the rule conditions.
- [Configure a ThreatParse rule](/deception/configuring-threatparse-rule).
- [Edit or delete a ThreatParse rule](/deception/editing-or-deleting-threatparse-rule).
![A screenshot capturing the ThreatParse Rules page](/downloads/deception/miragemaker/about-threatparse-rules/zscaler-deception-threatparse-rules-about-page.png)