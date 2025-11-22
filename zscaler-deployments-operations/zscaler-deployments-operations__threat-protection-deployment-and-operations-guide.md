# Threat Protection Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/threat-protection-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1420101.pdf

This guide describes the benefits of using Threat Protection and the steps necessary for configuring Zscaler Internet Access (ZIA) to add Threat Protection to your security posture.
Today, web pages don't just contain plain text nested inside HTML tags. Instead, they use Java applets, Adobe Flash videos, ActiveX, and other objects designed to run programs. Hackers routinely embed malicious scripts and applications on illegitimate or hacked websites.
The Zscaler service uses an industry-leading antivirus (AV) vendor for signature-based detection and protection to provide comprehensive web security. ZIA identifies various objects and scripts, and prevents the end user browser from downloading them.
To learn more, see [Advanced Threat Protection (ATP)](/zia/policies/advanced-threat-protection), [Malware Protection](/zia/policies/malware-protection), and [Mobile Security](/zia/policies/mobile-security).
Value of Deploying Threat Protection
Using Threat Protection provides the following benefits:
- Improves your organization's security posture by protecting against zero-day threats and unknown malware.
- Analyzes network traffic to monitor your network for security and operational anomalies.
- Leverages threat data from the world’s largest security cloud and shares threat protection cloud-wide in real time.
Deployment Phase
The deployment phase initially sets up and integrates ZIA solutions into an existing network infrastructure. During the deployment phase, configure Threat Protection in ZIA to meet the needs of your infrastructure. The following sections discuss steps to deploy Threat Protection.
Prerequisites
For Threat Protection deployment, verify and complete the following prerequisites:
- User traffic must traverse the Zscaler infrastructure to be evaluated by Threat Protection policies. To learn more, see the [Zscaler Client Connector Deployment and Operations Guide](/zscaler-deployments-operations/zscaler-client-connector-deployment-and-operations-guide) and the [Local Breakouts Deployment and Operations Guide](/zscaler-deployments-operations/local-breakouts-deployment-and-operations-guide).
- Identify your organization’s risk tolerances, and use them to guide how you configure Threat Protection.
Deployment Steps
The following steps explain how to deploy Threat Protection:
- [Configure Malware Protection policies](/zia/configuring-malware-protection-policy) in the ZIA Admin Portal, using the Zscaler [recommended Malware Protection policy](/zia/recommended-malware-protection-policy) as a guide.
- [Configure ATP policies](/zia/configuring-advanced-threat-protection-policy) in the ZIA Admin Portal, using the Zscaler [recommended ATP policy](/zia/recommended-advanced-threat-protection-policy) as a guide.
- [Configure Mobile Malware Protection policies](/zia/about-mobile-malware-protection) in the ZIA Admin Portal, using the Zscaler [recommended Mobile Malware Protection policy](/zia/recommended-mobile-malware-protection-policy) as a guide.
- [Configure Mobile App Store Control policies](/zia/about-mobile-app-store-control) if you want to restrict access to sites from which users can download apps for their mobile devices.
- (Optional) Configure the security exceptions in the ZIA Admin Portal, which is done separately for [Malware Protection](/zia/configuring-security-exceptions-malware-protection-policy) and [ATP](/zia/configuring-security-exceptions-advanced-threat-protection-policy).
Considerations
Review the following considerations:
- Malware Protection, ATP, and Mobile Malware Protection work separately from the URL and Cloud App policies, and are handled by separate Zscaler features. To learn more, see [About Policy Enforcement](/zia/about-policy-enforcement).
- Zscaler recommends [raising a support ticket with Zscaler](/submit-ticket-links) if you think that Zscaler is detecting a false-positive. Reduce security exceptions to an absolute minimum.
- ATP security exceptions also apply to Malware Protection, but not vice versa. ATP exceptions also cover Sandbox policies.
- To allow a specific destination across all Zscaler, you must create exceptions in ATP, URL Filtering, and File Type Control policies.
- When troubleshooting destination accessibility issues, remember that threat protection policies are global policies configured for all users.
Operations Phase
This section describes common practices used to operate ZIA solutions when integrated with your environment. You can monitor and tune Threat Protection during operations to meet your infrastructure needs.
Prerequisites
For Threat Protection operation, keep a list of known security exceptions (such as partner websites and currently running or scheduled phishing campaigns) available to security administrators.
Common Troubleshooting Items
If users cannot download a file or load a website due to threat protection, check the Web and Firewall [Insights logs](/zia/about-insights-logs) to determine which threat protection prohibits users from accessing the desired content. Carefully consider whether placing the file or content on the allowlist aligns with your security compliance.
Deployment and Operations Checklist
Zscaler recommends downloading the [Threat Protection Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zia-deployments-operations/threat-protection-deployment-and-operations-guide/Threat-Protection-Deployment-Operations-Checklist.pdf) to help plan and implement Threat Protection in ZIA: [Download PDF](/downloads/zscaler-deployments-operations/zia-deployments-operations/threat-protection-deployment-and-operations-guide/Threat-Protection-Deployment-Operations-Checklist.pdf)
Additional Information
For more Threat Protection information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](http://community.zscaler.com).