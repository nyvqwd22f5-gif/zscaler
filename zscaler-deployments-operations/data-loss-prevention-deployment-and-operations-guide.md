# DLP Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/data-loss-prevention-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1417451.pdf

This guide describes the benefits of using Data Loss Prevention (DLP) and the steps necessary for configuring Zscaler Internet Access (ZIA) to add DLP to your security posture. DLP detects potential data breaches and data ex-filtration transmissions and prevents them by monitoring, detecting, and blocking sensitive data while in use and motion.
To learn more, see [About Data Loss Prevention](/zia/about-data-loss-prevention).
Value of Deploying DLP
Using DLP provides the following benefits:
- Protects your organization from data loss by monitoring or blocking content according to configured policies.
- Forwards information about transactions that trigger third-party DLP policies.
- Maintains compliance and data privacy.
Deployment Phase
The deployment phase includes initially setting up and integrating Zscaler solutions into an existing network infrastructure. During the deployment phase, you configure ZIA DLP to meet the needs of your infrastructure. The following sections discuss the steps to deploy ZIA DLP.
Prerequisites
One of the following Zscaler subscriptions is required:
- ZIA ELA Edition.
- Data Loss Prevention subscription.
Deployment Steps
The following steps explain how to deploy ZIA DLP.
- Identify the dataset and data categories that need protection from ex-filtration. Refer to your organization’s security and compliance policy for this information. For example, if an organization is Payment Card Industry Data Security Standard (PCI-DSS) compliant, you might need to consider monitoring all traffic related to the payment card industry (e.g., credit card, debit card, etc.).
- Decide which DLP policy rules to configure. Your policy can simultaneously use all of the following options:
- [Monitor or block data using Zscaler DLP engines](/zia/about-data-loss-prevention#option1).
- [Monitor or block data using Zscaler DLP engines, then forward information to a third-party DLP solution](/zia/about-data-loss-prevention#opt2).
- [Monitor or block data based on specific criteria, then forward information to a third-party DLP solution](/zia/about-data-loss-prevention#opt3).
- Configure a DLP policy rule with [content inspection](/zia/configuring-policy-using-zscaler-dlp-engines) or [without content inspection](/zia/how-do-i-configure-policy-using-external-dlp-engines).
- (Optional) Configure an End User Notification (EUN) that alerts users that the data they sent is not allowed to leave the organization. Zscaler recommends you add hyperlinks to company security policies in the EUN for better user education.
- Start by configuring DLP policies that alert users to potential policy violations across a small subset of users and applications. This allows you to analyze false positives before taking action on policy notifications.
Considerations
Review the following considerations:
- You can decide to use Zscaler DLP with or without content inspection.
- You can configure Zscaler DLP policies not to use Zscaler DLP engines. Traffic is forwarded to third-party DLP solutions based on matched criteria.
- Decide if a policy’s initial action should be Block or Allow. As a best practice, new policies are only monitored first, so you can fine-tune them to reduce false positives. When the policy shows low false positives, change the action to Block.
- Configure a custom [End User Notification](/zia/configuring-end-user-notifications).
Operations Phase
This section describes common practices used to operate Zscaler solutions when integrated with your environment. During the operations phase, you can monitor and tune ZIA DLP to meet your infrastructure needs.
Prerequisites
For DLP operation, complete the following prerequisites:
- Determine the false positive percentage of a DLP policy and let operations and support teams know what to expect while triaging incidents.
- Consider end user education for top actors to learn how to handle the sensitive data they use.
Common Troubleshooting Items
If you see the message `Error: unable to update SSH public key`, review [Configuring the Zscaler Incident Receiver](/zia/configuring-zscaler-incident-receiver).
Deployment Checklist
Zscaler recommends downloading the [DLP Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zia-deployments-operations/data-loss-prevention-deployment-and-operations-guide/DLP-Deployment-Operations-Checklist.pdf) to help plan and implement ZIA DLP: [Download PDF](/downloads/zscaler-deployments-operations/zia-deployments-operations/data-loss-prevention-deployment-and-operations-guide/DLP-Deployment-Operations-Checklist.pdf)
Additional Information
For more SaaS Security information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](http://community.zscaler.com/).