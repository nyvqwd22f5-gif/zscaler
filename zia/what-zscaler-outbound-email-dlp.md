# What Is Zscaler Outbound Email DLP?
Source: https://help.zscaler.com/zia/what-zscaler-outbound-email-dlp
PDF: https://help.zscaler.com/pdf/com/en/1492656.pdf

Zscaler Outbound Email Data Loss Prevention (DLP) stops the exfiltration of sensitive data by enforcing policy rules on outbound email content sent to external domains, including content in subject lines, body text, and attachments. Using connectors and rules, your email server sends email to, and receives email from, the Zscaler smart host. The Zscaler smart host receives the email and sends it to the Zscaler DLP service for inspection. The Zscaler DLP service then inspects the email content for sensitive data, adding headers that define DLP actions to emails that trigger outbound email policy. When your email server receives inspected email from the Zscaler smart host, it uses those headers to determine enforcement actions.
As a part of your larger DLP strategy, Zscaler Outbound Email DLP lets you use the same DLP policy tools that you already use across other channels (i.e., Inline Web DLP, Endpoint DLP, and SaaS Security API DLP), eliminating the need for different DLP point solutions and the operational overhead involved in maintaining those solutions. Additionally, Zscaler Outbound Email DLP lets you enforce your DLP policy at a granular level, so that a single email containing sensitive information can be blocked for one recipient and allowed for another.
To learn more about how the Zscaler service enforces outbound email policy rules, see [Understanding Outbound Email Policy Enforcement](/zia/understanding-outbound-email-policy-enforcement).
The following diagram shows a high-level overview of how Zscaler Outbound Email DLP enforces outbound email policy:
- A user sends an email containing sensitive information to an external domain.
- The rules configured on your email server instruct Gmail or Microsoft Exchange to send the email to the Zscaler smart host via Simple Mail Transfer Protocol (SMTP) for DLP inspection.
- The Zscaler DLP service performs DLP inspection and inserts email headers based on the verdict of the policy evaluation.
- Inspected email is sent back to your email server.
- Your email server enforces the DLP action based on the mail flow/transport rules and inserted headers in the email.
- If the email is allowed to be sent, it is delivered to the next hop MTA or to the intended recipient.
[]![Zscaler Outbound Email DLP Diagram](/downloads/zia/policies/outbound-email-policy/ZIA-Email-DLP_Workflow-Diagram_v4.png)
To learn more about configuring Zscaler Outbound Email DLP, see [Step-by-Step Configuration Guide for Zscaler Outbound Email DLP](/zia/step-step-configuration-guide-zscaler-outbound-email-dlp).