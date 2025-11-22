# Firewall Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/cloud-firewall-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1417316.pdf

This guide describes the benefits of using Firewall and the steps necessary for configuring Zscaler Internet Access (ZIA) to add Firewall to your security posture.
Firewall provides the capabilities of traditional firewalls by monitoring and controlling an organization’s outbound traffic. These features include traditional network service control, dynamic application identification with deep packet inspection (DPI), and identification of web traffic on non-default ports. To learn more, see [Understanding Firewall Capabilities](/zia/understanding-firewall-capabilities).
Value of Deploying Firewall
Using Firewall provides the following benefits:
- Full protection for work-from-anywhere users, on-premises or remote.
- Catch evasive attacks on non-standard ports.
- Secure local internet breakout for internet and SaaS applications.
Deployment Phase
The deployment phase initially sets up and integrates ZIA solutions into an existing network infrastructure. During the deployment phase, you configure Firewall in ZIA to meet the needs of your infrastructure. The following sections discuss steps to deploy Firewall.
Prerequisites
For Firewall deployment, verify and complete the following prerequisites:
- Validate and review one of the needed subscriptions (i.e., Standard Firewall or Advanced Firewall). For information about subscriptions, see [Understanding Firewall Capabilities](/zia/understanding-firewall-capabilities).
- Define a global rule set that identifies all needed criteria objects such as source/destination IPs, location groups, departments, etc.).
- Validate that you have mapped the identified objects in the first two prerequisites to [Nanolog Streaming Service (NSS) firewall criteria](/zia/configuring-firewall-filtering-policy).
- Validate that all parameters are within the [ZIA product limits](/zia/ranges-limitations).
Deployment Steps
The following steps explain how to deploy Firewall:
- Create the objects used as rule criteria (i.e., [Locations](/zia/configuring-locations), [Network Services](/zia/adding-network-service), [Destination Groups](/cloud-branch-connector/configuring-destination-groups), etc.).
- [Create the Firewall rules](/zia/configuring-firewall-filtering-policy) in a disabled state.
- Using NSS, deploy [Zscaler's Nanolog Streaming Service (NSS)](/zia/about-nanolog-streaming-service) firewall and [configure the NSS firewall feeds](/zia/adding-nss-feeds-firewall-logs).
- Gradually [enable firewall rules and firewall features](/zia/enabling-firewall-locations) on locations.
- Perform a controlled test per location before enabling all rules on all locations.
- Enable a firewall for Z-Tunnel 1.0 and PAC remote users via the [advanced settings](/zia/about-advanced-settings).
- Ensure traffic is forwarded to the ZIA Firewall from Zscaler Client Connector [using Z-Tunnel 2.0](/z-app/best-practices-deploying-z-tunnel-2.0).
Considerations
Review the following considerations:
- Understand and respect the default [firewall control policy recommendations](/zia/recommended-firewall-control-policy).
- Build a rule set with specific rules first and less specific rules last. The order ensures that more specific policies are matched first in case of overlap.
- Be familiar with [predefined firewall filtering rules](/zia/about-predefined-firewall-filtering-rules).
- Understand the [difference between Network Service and Network Application](/zia/about-network-applications), and if possible, combine both on the same firewall rule to restrict DPI processes to the specific port.
- Be familiar with the [log fields in Zscaler Insights](/zia/firewall-insights-logs-columns).
Operations Phase
This section describes common practices used to operate ZIA solutions when integrated with your environment. You can monitor and tune Firewall during the operations phase to meet your infrastructure needs.
Prerequisites
For Firewall operation, complete the following prerequisites:
- Comment all firewall rules so the operations team can understand their purpose. Include other related objects (IP groups, URL categories, etc.) and Reference Change IDs/numbers (if you track these in internal tools).
- If not all locations use Firewall, document the reasoning for disabling firewalls for the specific locations.
- Validate that the team is familiar with all the essential concepts (i.e., Network Application vs. Network Service, NSS logs, etc.).
Common Troubleshooting Items
Transactions marked as Allow due to insufficient app data: If transactions are logged as Allow due to insufficient app data on Firewall Insights, it might relate to [a match from our DPI mechanism and specific rule](/zia/about-network-applications).
Deployment and Operations Checklist
Zscaler recommends downloading the [Firewall Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zia-deployments-operations/cloud-firewall-deployment-and-operations-guide/Firewall-Deployment-Operations-Checklist.pdf) to help plan and implement Firewall: [Download PDF](/downloads/zscaler-deployments-operations/zia-deployments-operations/cloud-firewall-deployment-and-operations-guide/Firewall-Deployment-Operations-Checklist.pdf)
Additional Information
For more SaaS Security information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](http://community.zscaler.com/).