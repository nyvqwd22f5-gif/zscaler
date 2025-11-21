# Local Breakouts Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/local-breakouts-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1414406.pdf

This guide describes the benefits of using Software-Defined Wide Area Networking (SD-WAN) local breakouts and the steps necessary for integrating Zscaler Internet Access (ZIA) into your local breakout security posture.
Backhauling over Multi-Protocol Label Switching (MPLS) to a centralized internet gateway via a hub-and-spoke architecture is inadequate when deploying cloud applications. Delivering a fast user experience and supporting cloud applications and services requires locally-routed internet traffic.
SD-WAN simplifies branch traffic routing in the branch, and makes it easy to establish local internet breakouts. Software-defined policies select the best path to route traffic connecting the branch to the internet, cloud applications, and the data center.
Deploying Zscaler with your new local breakouts secures and simplifies your local branch infrastructure by protecting user and application traffic, and reducing unneeded security hardware.
Value of Deploying ZIA with SD-WAN Local Breakouts
Integrating ZIA with SD-WAN local breakout deployments provides the following benefits:
- Fast and secured user experience.
- Reduced costs.
- Simplified branch IT operations.
- Protected users, wherever they connect.
Deployment Phase
The deployment phase includes the process to initially set up and integrate Zscaler solutions into an existing network infrastructure. During the deployment phase, you configure ZIA to work with your local breakout SD-WAN infrastructure. The following sections discuss steps to deploy ZIA with local breakouts using SD-WAN.
Prerequisites
For local breakout deployment, verify and complete the following prerequisites:
- Endpoint evaluation:
- Identify hardware (such as routers and firewalls) at the Public Service Edge.
- Identify SD-WAN capabilities.
- Estimate traffic and consumption.
- [Evaluate suitable traffic forwarding methods and validate the respective deployment prerequisites](/zia/choosing-traffic-forwarding-methods).
- Evaluate security requirements.
- Identify egress IPs.
- (Optional) Identify clients that need different treatment than the regular users at the endpoint.
- [Identify suitable data centers](https://config.zscaler.us/).
Deployment Steps
The following steps explain how to integrate ZIA with local breakout SD-WAN:
- [Provision static egress IPs](/zia/self-provisioning-static-ip-addresses) or review how to [configure a location without a static egress IP](/zia/configuring-location-without-static-public-ip-address).
- [Create individual locations per local breakout](/zia/configuring-locations).
- (Optional) [Create sub-locations](/zia/configuring-sub-locations).
- Choose and implement the most [suitable traffic forwarding method](/zia/choosing-traffic-forwarding-methods) for your organization, [GRE](/zia/traffic-forwarding/gre), or [IPSec](/zia/traffic-forwarding/ipsec) tunneling.
Considerations
Review the following considerations:
- Verify the cloud enforcement node status before choosing a suitable data center ([Zscaler Cloud Configuration Requirements](https://config.zscaler.us/)):
- Some data centers have a regional surcharge applied to them. Contact your Zscaler Account team to confirm your organization can use surcharged data centers.
- Data centers that have a regional surcharge or are not marked with Auto Geo Proximity Enabled won’t be chosen as the preferred data centers. Contact your Zscaler Account team for instructions on how to include all possible Zscaler data centers in your infrastructure.
- Check round-trip times between the egress and Zscaler’s Public Service Edges to identify the Zscaler data center with the least latency. Reach out to Zscaler Support for assistance.
Operations Phase
This section describes common practices used to operate Zscaler solutions when integrated with your environment. During the operations phase, you can monitor and tune ZIA to meet your SD-WAN local breakout infrastructure needs.
Prerequisites
Make sure to document all ZIA policies and traffic forwarding methods that are defined for entire branch locations to use as a reference to help your engineers or Zscaler contacts with troubleshooting processes.
Common Troubleshooting Tips
The following list describes common issues related to deploying ZIA in SD-WAN local breakouts:
- Performance Issues: When faced with performance issues, you can analyze infrastructure performance using the [Zscaler Cloud Performance Test Tool](/zia/using-zscaler-cloud-performance-test-tool).
- Tunnel Flaps: If your tunnels start flapping, review the [GRE ](/zia/configuring-gre-tunnels#step1)and [IPSec ](/zia/configuring-ipsec-vpn-tunnel)configuration guidelines and ensure that you've properly provisioned the tunnel for your organization. Check [Zscaler Trust](https://trust.zscaler.us/zscalergov.net) to see if there is an associated outage with respect to the detected flapping behavior.
- Tunnel Failover Issues: Review [tunnel configuration guidelines](/zia/configuring-gre-tunnels#step1) to verify that everything is correctly configured.
Deployment and Operations Checklist
Zscaler recommends downloading the [Local Breakouts Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zia-deployments-operations/local-breakouts-deployment-and-operations-guide/Local-Breakouts-Deployment-Operations-Checklist.pdf) to help plan and implement your SD-WAN local breakout deployment for ZIA: [Download PDF](/downloads/zscaler-deployments-operations/zia-deployments-operations/local-breakouts-deployment-and-operations-guide/Local-Breakouts-Deployment-Operations-Checklist.pdf)
Additional Information
For more SaaS Security information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](http://community.zscaler.com/).