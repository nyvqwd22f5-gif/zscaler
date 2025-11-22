# Understanding Outbound Email Policy Enforcement
Source: https://help.zscaler.com/unified/understanding-outbound-email-policy-enforcement
PDF: https://help.zscaler.com/pdf/com/en/1503656.pdf

Zscaler Outbound Email Data Loss Prevention (DLP) lets you monitor and act on sensitive data in outbound email sent to external domains. You can use Zscaler custom and predefined DLP engines to detect sensitive data and to specify DLP actions (i.e., Allow, Block, and Custom Header Insertion) when an email triggers an outbound email policy rule. If you don't use Zscaler DLP engines, the service functions instead as a filter, only flagging content based on specific criteria.
At a high level, the Zscaler Outbound Email Policy monitors activity and enforces policy in the following ways:
- Gmail and Microsoft Exchange use Simple Mail Transfer Protocol (SMTP) to send mail to and receive mail from the Zscaler smart host.
- The Zscaler service evaulates all outbound email policy rules on a per-recipient basis. If multiple rules match for a recipient, the Zscaler service applies the rule with most restrictive action.
- If multiple rules with the same restrictive action match for a recipient, then the Zscaler service matches the rule with most restrictive action and the highest rule order.
- Before executing the matching rule, however, the Zscaler service checks whether the matching rule contains any exception rules. When evaluating exception rules, the Zscaler service uses rule order and stops evaluating rules at the first match. A matching exception rule takes the place of the parent rule.
- When content triggers outbound email policy rules, the Zscaler service adds headers to those emails and sends them back to the email server for enforcement. Depending on how outbound email policy rules are configured, the headers instruct the email server to take a default action (i.e., allow or block content), or an action mapped to a custom header configured on the server.
As a result, the Zscaler service enforces your outbound email policy at a granular level, meaning that an email with sensitive information sent to multiple users isn't necessarily be blocked outright. Instead, the Zscaler service can allow one user to receive the same email that's blocked for another user.
To learn more about configuring your outbound email policy, see [Step-by-Step Configuration Guide for Zscaler Outbound Email DLP](/unified/step-step-configuration-guide-zscaler-outbound-email-dlp).
Outbound Email Policy Enforcement Examples
Knowing how the Zscaler service applies your policies in different scenarios helps you understand why certain policy rules do or do not trigger based on sensitive content. It also ensures that your organization's data is secured as expected. The following examples provide an overview of how outbound email policy works as part of basic use cases.
- [Example with Basic Rules](#example-1-rules)
- [Example with Recipient Profiles](#example-2-recipient-profiles)
- [Example with Exception Rules](#example-3-exception-rules)
[]Consider the following policy enforcement example that uses Zscaler DLP engines and consists of the following rules:
| **Rule ID** | **Rule Order** | Description | Content Locations | User/Group | Action | Severity |
| ----------- | -------------- | ----------- | ----------------- | ---------- | ------ | -------- |
| R1 | 1 | Allow emails from Finance Department that contain HIPAA info | Email Attachments, Email Body, Email Subject | Finance | Allow | Low |
| R2 | 2 | Add custom header to emails sent from HR Department that contain PII information | Email Attachments, Email Body, Email Subject | HR | Custom Header Insertion | Medium |
| R3 | 3 | Block all emails that contain GLBA information | Email Attachments, Email Body, Email Subject | Any | Block | High |
Rules Scenario 1
A member of the Finance department emails an attachment that includes HIPAA and GLBA data. The Zscaler service determines the following:
- R1 and R3 match. R1 has a higher rule order, but R3 has the most restrictive action.
- The Zscaler service executes R3, with an action of Block and a severity of High.
- R1 is logged as having matched.
Rules Scenario 2
A member of the HR department emails an attachment that includes HIPAA and PII data. The Zscaler service determines the following:
- R2 is matched.
- The Zscaler service executes R2, with an action of Custom Header Insertion with a severity of Medium.
- No other rules are logged as having matched.
[]Now, consider the following policy enforcement example that adds recipient profiles, which give you granular control over your outbound email policy (i.e., a single email that contains sensitive data can be allowed for one recipient and blocked for another). To learn more, see [About Email Profiles](/unified/about-email-profiles).
| **Rule ID** | **Rule Order** | Description | Content Locations | Email Recipient Profile | User/Group | Action | Severity |
| ----------- | -------------- | ----------- | ----------------- | ----------------------- | ---------- | ------ | -------- |
| R1 | 1 | Allow emails that contain HIPAA information sent to benefits.admin@safemarch.com | Email Attachments, Email Body, Email Subject | Recipient profile includes benefits.admin@safemarch.com | Any | Allow | Low |
| R2 | 2 | Add custom header to emails that contain PII information | Email Attachments, Email Body, Email Subject | None | Any | Custom Header Insertion | Medium |
| R3 | 3 | Block all emails that contain GLBA information | Email Attachments, Email Body, Email Subject | Recipient profile includes sysadmin@safemarch.com | Any | Block | High |
Recipient Profiles Scenario
An employee emails an attachment that includes HIPAA and GLBA data to two recipients: sysadmin@safemarch.com and benefits.admin@safemarch.com. The Zscaler service determines the following:
- R1 matches for benefits.admin@safemarch.com, and R3 matches for sysadmin@safemarch.com. R2 is not matched.
- The Zscaler service executes R1 with an action of Allow for the email sent to benefits.admin@safemarch.com.
- The Zscaler service executes R3 with an action of Block for the email sent to sysadmin@safemarch.com.
- R1 and R3 are both logged as having matched.
[]Now, consider the following exception rules to exclude specific users that must perform tasks as part of a necessary workflow that would otherwise violate outbound email policy.
| **Rule ID** | **Rule Order** | Description | Content Locations | User/Group | Action | Severity |
| ----------- | -------------- | ----------- | ----------------- | ---------- | ------ | -------- |
| R1 | 1 | Allow emails from the Finance Department that contain HIPAA information | Email Attachments, Email Body, Email Subject | Finance | Allow | Low |
| R2 | 2 | Add custom header to emails sent from Finance Department that contain PII information | Email Attachments, Email Body, Email Subject | HR | Custom Header Insertion | Medium |
| R2.1 | 2.1 | Exclude Director of HR (Jeff Doyle) | Email Attachments | jeffrey.doyle@safemarch.com | Allow | Info |
| R3 | 3 | Block all emails that contain GLBA information | Email Attachments, Email Body, Email Subject | Any | Block | High |
| R3.1 | 3.1 | Exclude Executive Director of Finance (Megan Williams) | Email Attachments, Email Body, Email Subject | megan.williams@safemarch.com | Allow | Info |
| R3.2 | 3.2 | Exclude Executive Committee | Email Attachments, Email Body, Email Subject | Executive Committee | Custom Header Insertion | Medium |
Exception Rules Scenario 1
The Director of HR (Jeff Doyle) emails an attachment that includes PII data. The Zscaler service determines the following:
- R2 is matchced, with an action of Custom Header Insertion. However, R2 has an exception rule (R2.1) that's also matched.
- The Zscaler service executes R2.1, with an action of Allow and a severity of Info.
- R2 and R2.1 are logged as having matched.
Exception Rules Scenario 2
The Executive Director of Finance (Megan Williams) sends an email that contains GLBA information in the body text. The Zscaler service determines the following:
- R3 matches but has two exception rules. The Zscaler service determines that R3.1 matches and stops evaluating exception rules (even though R3.2 also matches, as Megan Williams is a member of the Executive Committee group).
- The Zscaler service executes R3.1, with an action of Allow and a severity of Info.
- R3 and R3.1 are logged as having matched.