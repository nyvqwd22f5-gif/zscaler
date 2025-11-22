# Understanding Endpoint Policy Enforcement
Source: https://help.zscaler.com/unified/understanding-endpoint-policy-enforcement
PDF: https://help.zscaler.com/pdf/com/en/1493191.pdf

Zscaler Endpoint Data Loss Prevention (DLP) service uses Data Loss Prevention (DLP) engines consisting of rules and exception rules to inspect and enforce policies that monitor activities that users take on endpoints. Your Endpoint Data Loss Prevention (DLP) policy can monitor activities across multiple channels (i.e., printing, saving to removable storage, uploading to personal cloud accounts, or saving to network shares) that involve sensitive data on endpoints.
At a high level, Endpoint DLP monitors activity and enforces policy in the following ways:
- At startup, Endpoint DLP runs inventory and classification scans on an endpoint to identify and categorize data. Classification scans always run after inventory scans. Each time the Endpoint DLP policy changes, an inventory and classification scan runs on the endpoint.
- When a user performs a monitored activity that involves sensitive data, the rule engine evaluates all rules. If multiple rules match, the rule engine selects the rule with the most restrictive action and the highest rule order.
- Before executing the matching rule, however, the rule engine looks for exception rules, which inherit rule order from parent rules. The engine evaluates exception rules according to rule order and selects the first matching exception rule, which then takes the place of the parent rule.
To learn more, see [Step-by-Step Configuration Guide for Zscaler Endpoint DLP](/unified/step-step-configuration-guide-zscaler-endpoint-dlp).
Endpoint Policy Enforcement Examples
Knowing how the Zscaler service applies your policies in different scenarios helps you understand why certain policies do or do not trigger based on end-user activity. It also ensures that your organization's data is secured as expected. Consider the following policy enforcement examples:
Example 1 (Rules)
Consider an Endpoint DLP policy that consists of the following rules:
| **Rule ID** | **Rule Order** | Channel | Description | User/Group | Action | Severity | **Email Notification** |
| ----------- | -------------- | ------- | ----------- | ---------- | ------ | -------- | ---------------------- |
| R1 | 1 | Removable Storage | Request user confirmation when copying files that contain Payment Card Industry (PCI) data | Any | Confirm | Low | Yes |
| R2 | 2 | Removable Storage | Block copying of source code | Engineering | Block | Medium | No |
| R3 | 3 | Removable Storage | Block copying of HIPAA information | Any | Block | High | No |
Rules Scenario 1
An end user in the Engineering department copies a ZIP file that includes files with PCI data, source code, and HIPAA information. Endpoint DLP determines the following:
- All three rules match, but R2 and R3 have the most restrictive action.
- R2 has a higher rule order, so the service executes that rule, with a severity of Medium and no email notification.
- R1 and R3 are logged as having matched.
Rules Scenario 2
An end user in the HR department copies a ZIP file that includes files with PCI data, source code, and HIPAA information. Endpoint DLP determines the following:
- R1 and R3 match, but R3 has the most restrictive action.
- The service executes R3, with a severity of High and no email notification.
- R1 is logged as having matched.
Example 2 (Exception Rules)
Now, consider the following exception rules associated with the same Endpoint DLP rules:
| **Rule ID** | **Rule Order** | Channel | Description | User/Group | Action | Severity | **Email Notification** |
| ----------- | -------------- | ------- | ----------- | ---------- | ------ | -------- | ---------------------- |
| R1 | 1 | Removable Storage | Request user confirmation when copying files that contain Payment Card Industry (PCI) data | Any | Confirm | Low | Yes |
| *R1.1* | 1.1 | Removable Storage | Block if contains data marked *Confidential* | Any | Block | High | Yes |
| *R1.2* | 1.2 | Removable Storage | Exclude VP of Finance and CFO | VP Finance, CFO | Allow | Info | No |
| R2 | 2 | Removable Storage | Block copying of source code | Engineering | Block | Medium | No |
| *R2.1* | 2.1 | Removable Storage | Request user confirmation if Director or VP | Director or VP | Confirm | Medium | No |
| R3 | 3 | Removable Storage | Block copying of HIPAA information | Any | Block | High | No |
Exception Rules Scenario 1
The Director of Engineering copies a ZIP file that includes files with PCI data, source code, and HIPAA information. Endpoint DLP determines the following:
- All three rules match, but R1 and R2 have exception rules.
- R1.1 does not match (ZIP does not contain files marked *Confidential*).
- R1.2 does not match (user is not a VP or CEO).
- R2.1 matches (user is Director of Engineering), so R2.1 replaces R2.
- The matched rules are R1, R2.1, and R3; however, R3 has the most restrictive action, so the engine executes R3. The incident has a severity of High and does not trigger an email notification.
- Rules R1 and R2.1 are logged as having matched.
Exception Rules Scenario 2
The Chief Financial Officer (CFO) copies a ZIP file that includes files with PCI data, source code, and HIPAA information. Endpoint DLP determines the following:
- R1 and R3 match.
- R1 has exception rules.
- R1.1 does not match (ZIP does not contain files marked *Confidential*).
- R1.2 matches (user is CFO), so R1.2 replaces R1.
- The matched rules are R1.2 and R3; however, R3 has the most restrictive action, so the engine executes R3. The incident has a severity of High and does not trigger an email notification.
- Rule R1.2 is logged as having matched.