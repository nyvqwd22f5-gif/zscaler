# IPS Control Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/ips-control-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1417456.pdf

This guide describes the benefits of using Intrusion Prevention System (IPS) Control and the steps necessary for configuring Zscaler Internet Access (ZIA) to add IPS Control to your security posture.
IPS Control uses signature-based detection to control and protect your traffic from intrusion over all ports and protocols. The Zscaler service uses custom signatures built and updated by Zscaler's security research team and signatures from industry-leading vendors. Using these signatures, the Zscaler service monitors your traffic in real time. When the IPS finds a pattern match in your traffic, it enforces your policies inline.
To learn more, see [About IPS Control](/zia/about-ips-control).
Value of Deploying IPS Control
Using IPS Control provides the following benefits:
- Increases company security posture.
- Protects against threats from both web traffic and non-web traffic such as HTTP, HTTPS, FTP, DNS, TCP, UDP, and IP-based ports and protocols.
- Centralizes granular policy enforcement.
Deployment Phase
The deployment phase includes initially setting up and integrating Zscaler solutions into an existing network infrastructure. During the deployment phase, you configure IPS Control to meet the needs of your infrastructure. The following sections discuss steps to deploy IPS Control.
Prerequisites
One of the following Zscaler subscriptions is required:
- ZIA Transformation Edition and later.
- Advanced Firewall subscription.
Deployment Steps
The following steps explain how to deploy IPS Control:
- [Review Zscaler’s recommended IPS Control policy](/zia/recommended-ips-control-policy).
- [Configure the IPS Control policy for your locations](/zia/configuring-ips-control-policy).
- [Enable Firewall Control for your locations](/zia/enabling-firewall-locations). To learn more, see [About Firewall](/zia/about-firewall).
- [Enable IPS Control for your locations](/zia/release-upgrade-summary-2019?applicable_category=zscaler.net&deployment_date=2019-09-20&id=1352466).
Considerations
Review the following considerations:
- Detected threats for both web and non-web traffic display in [Firewall Insights > Logs](/zia/firewall-insights-logs-filters). Threats detected from web-only traffic also appear in the [Security Dashboard](/zia/about-dashboards#security).
- Firewall Control is enabled by default for Zscaler Client Connector Z-Tunnel 2.0 remote users.
- You can enable Firewall Control for [Zscaler Client Connector Z-Tunnel 1.0 and PAC remote users](/zia/about-advanced-settings#firewall-remote-users).
- IPS Control is enabled by default for Zscaler Client Connector Z-Tunnel 2.0 remote users.
- You can enable IPS Control by enabling [Firewall Control for Zscaler Client Connector Z-Tunnel 1.0 and PAC remote users](/zia/about-advanced-settings#firewall-remote-users).
Operations Phase
This section describes common practices used to operate Zscaler solutions when integrated with your environment. You can monitor and tune IPS Control during the operations phase to meet your infrastructure needs.
Common Troubleshooting Items
The following list describes common issues related to IPS Control operation:
- IPS Control blocks a commonly used website and labels it as phishing/botnet callback/malware/etc.: This might be a false positive detection. Submit a ticket with [Zscaler Support](/submit-ticket-links) so that the Security Research team can investigate and analyze this behavior.
- I can see in the logs that my SSH tunnel traffic is blocked by IPS Control, and I have configured an IPS Control rule to allow the traffic, but the traffic is still showing as blocked: [SSH tunneling is blocked, or allowed, for your entire tenant](/zia/configuring-advanced-threat-protection-policy#Unauthorized). It can’t be granularly allowed for specific users or groups.
Deployment and Operations Checklist
Zscaler recommends downloading the [IPS Control Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zia-deployments-operations/ips-control-deployment-and-operations-guide/IPS-Control-Deployment-Operations-Checklist.pdf) to help plan and implement IPS Control in ZIA: [Download PDF](/downloads/zscaler-deployments-operations/zia-deployments-operations/ips-control-deployment-and-operations-guide/IPS-Control-Deployment-Operations-Checklist.pdf)
Additional Information
For more SaaS Security information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](http://community.zscaler.com/).