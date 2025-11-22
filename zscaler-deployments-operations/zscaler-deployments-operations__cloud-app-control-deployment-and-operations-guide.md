# Cloud App Control Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/cloud-app-control-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1417301.pdf

This guide describes the benefits of using Cloud App Control and the steps necessary for configuring Zscaler Internet Access (ZIA) to add Cloud App Control to your security posture.
Cloud App Control policies provide granular control over popular websites and applications. They are organized by function into categories for easy reference and to facilitate defining rules for similar apps.
To learn more, see [About Cloud App Control](/zia/about-cloud-app-control).
Value of Deploying Cloud App Control
Using Cloud App Control provides the following benefits:
- Controls users’ access to specific cloud applications.
- Controls access using a predefined set of [cloud application policy rules](/zia/adding-rules-cloud-app-control-policy).
- Defines daily access limits via criteria such as bandwidth or time.
- Uses the [Cloud Application Risk Profile](/zia/about-cloud-application-risk-profile).
Deployment Phase
The deployment phase includes initially setting up and integrating ZIA solutions into an existing network infrastructure. During the deployment phase, you configure ZIA Cloud App Control to meet the needs of your infrastructure. The following sections discuss steps to deploy ZIA Cloud App Control.
Prerequisites
One of the following Zscaler subscriptions is required:
- ZIA Business Edition and later.
- Cloud Apps Control subscription.
Deployment Steps
The following steps explain how to deploy ZIA Cloud App Control:
- Determine whether to apply URL Filtering Policies even after a Cloud App Control policy explicitly allows a transaction. To learn more, see [Advanced Web App Control Options](/zia/about-advanced-settings#web-app-control).
Refer to [About Policy Enforcement](/zia/about-policy-enforcement) for an in-depth understanding of policy enforcement and the policy evaluation workflow.
- Collect the list of the cloud categories and applications for which you would like to control access. For the list of supported cloud applications, see [Understanding Cloud App Categories](/zia/understanding-cloud-app-categories).
- Configure the required rules:
- [AI & ML Applications](/zia/adding-ai-ml-applications-rule-cloud-app-control)
- [Collaboration & Online Meetings](/zia/adding-collaboration-online-meetings-rule-for-cloud-app-control)
- [Consumer](/zia/adding-consumer-rule-cloud-app-control)
- [Custom Applications](/zia/adding-custom-applications-rule-cloud-app-control)
- [DNS Over HTTPS Services](/zia/adding-dns-over-https-services-rule-cloud-app-control)
- [File Sharing](/zia/adding-file-sharing-rule-cloud-app-control)
- [Finance](/zia/adding-finance-rule-cloud-app-control)
- [Health Care](/zia/adding-health-care-rule-cloud-app-control)
- [Hosting Providers](/zia/adding-hosting-providers-rule-cloud-app-control)
- [Human Resources](/zia/adding-human-resources-rule-cloud-app-control)
- [Instant Messaging](/zia/adding-instant-messaging-rule-cloud-app-control)
- [IT Services](/zia/adding-it-services-rule-cloud-app-control)
- [Legal](/zia/adding-legal-rule-cloud-app-control)
- [Productivity & CRM Tools](/zia/adding-productivity-crm-tools-rule-cloud-app-control)
- [Sales & Marketing](/zia/adding-sales-marketing-rule-cloud-app-control)
- [Social Networking](/zia/adding-social-networking-rule-cloud-app-control)
- [Streaming Media](/zia/adding-streaming-media-rule-cloud-app-control)
- [System & Development](/zia/adding-system-development-rule-cloud-app-control)
- [Webmail](/zia/adding-webmail-rule-cloud-app-control)
You can select the [Cloud Application Risk Profile](/zia/about-cloud-application-risk-profile) or the Cloud Applications field when defining rules for the Cloud App Category.
Considerations
Review the following considerations:
- The default policy behavior is Allow All.
- Rules evaluation proceeds in order from top to bottom.
- If a user requests a cloud app that you explicitly allow with a Cloud App Control policy rule, the service only applies the Cloud App Control policy and does not apply a URL Filtering policy. You can change this by enabling [Allow Cascading to URL Filtering](/zia/about-advanced-settings#web-app-control).
- Cloud App Control policies do not support custom End User Notifications (EUNs).
- The Cloud App Control policy rule applies to all specified cloud applications if you select the [cloud application risk profile criterion](/zia/about-cloud-application-risk-profile).
- You can select the Cloud Application Risk Profile or the Cloud Applications field for the rule.
Operations Phase
This section describes standard practices used to operate Zscaler solutions when integrated with your environment. You can monitor and tune ZIA Cloud App Control during the operations phase to meet your infrastructure needs.
Prerequisites
For Cloud App Control operation, complete the following prerequisites:
- Document the [Allow Cascading to URL Filtering](/zia/about-advanced-settings#web-app-control) settings to understand the flow of the evaluated rules to help internal personnel and Zscaler Support troubleshoot issues.
- Generally, allow Cloud App Control policies over URL filtering rules to use the predefined Cloud Applications.
Common Troubleshooting Items
The following list describes common issues related to Cloud App Control operation:
- Zscaler is blocking an allowed cloud app: Verify that you enabled [Allow Cascading to URL Filtering](/zia/about-advanced-settings#web-app-control). If so, verify that you have a corresponding URL filtering rule that allows this traffic.
- Users can still access a blocked cloud app:
- Verify if transactions from the affected users are visible in Zscaler Web/Firewall Insights. If not, it’s possible the traffic goes direct and bypasses the rules. The [PAC file / Proxy settings](/zia/writing-pac-file) can block the traffic.
- Verify if the protocol used is QUIC in Zscaler Firewall Insights. If yes, disable QUIC in Internet Browser settings.
Deployment and Operations Checklist
Zscaler recommends downloading the [Cloud App Control Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zia-deployments-operations/cloud-app-control-deployment-and-operations-guide/Cloud-App-Control-Deployment-Operations-Checklist.pdf) to help plan and implement ZIA Cloud App Control: [Download PDF](/downloads/zscaler-deployments-operations/zia-deployments-operations/cloud-app-control-deployment-and-operations-guide/Cloud-App-Control-Deployment-Operations-Checklist.pdf)
Additional Information
For more Cloud App Control information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and [Zscaler Zenith Community](http://community.zscaler.com).