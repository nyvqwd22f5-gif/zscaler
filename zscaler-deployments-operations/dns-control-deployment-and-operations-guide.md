# DNS Control Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/dns-control-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1417401.pdf

This guide describes the benefits of using DNS Control and the steps necessary for configuring Zscaler Internet Access (ZIA) to add DNS Control to your security posture.
DNS Control mitigates the risk of malware transmission, identifies infected endpoints using DNS tunnels, and restricts domains visited to comply with organizational standards and acceptable use.
The Zscaler service also detects and controls DNS tunneling occurring in your networks. The service operates as a DNS proxy. You can use this proxy as a firewall for DNS traffic. The service logs all traffic that goes through this proxy.
To learn more, see [About DNS Control](/zia/about-dns-control).
Value of Deploying DNS
- Implements DNS security.
- Detects and controls DNS tunneling.
- Redirects requests to your organization’s trusted public DNS resolver.
- Improves DNS performance.
- Gives visibility into every DNS request and response.
- Controls DNS traffic regardless of the DNS resolver selected by the end user.
- Protections from evasive behavior even for TLS-encrypted traffic.
- Logs every transaction in a forensically complete and enriched format.
Deployment Phase
The deployment phase includes initially setting up and integrating Zscaler solutions into an existing network infrastructure. During the deployment phase, you configure DNS Control to meet the needs of your infrastructure. The following sections discuss steps to deploy DNS Control.
Prerequisites
DNS Control might require an additional license for your organization. Check with your Zscaler Account team to verify the necessary licensing requirements.
Deployment Steps
The following steps explain how to deploy DNS Control:
- Choose between the following scenarios:
- Your organization wants to [send all traffic to Zscaler (office and remote users)](/zia/about-dns-control#client_traffic).
- Your organization wants to [forward DNS traffic to the internal DNS server and then redirect it to Zscaler](/zia/about-dns-control#dns_server_traffic).
- Modify the [Firewall Filtering policies](/zia/configuring-firewall-filtering-policy) so that DNS traffic passes through the cloud firewall.
- Configure the [DNS Control policy](/zia/configuring-dns-control-policy).
- (Optional) Configure [DNS tunneling detection](/zia/about-dns-tunnel-detection).
- After adding rules to the DNS Control policy, you might also need to do the following before [enabling the firewall](/zia/enabling-firewall-locations) for your locations.
- Modify the rules for the [NAT Control policy](/zia/about-nat-control) and [Firewall Filtering policy](/zia/configuring-firewall-filtering-policy) to allow traffic to pass.
- Configure [custom ports](/zia/configuring-custom-ports) as applicable.
- (Optional) [Define application groups](/zia/about-dns-application-groups).
Considerations
- The DNS proxy model of DNS Control allows the DNS to be intercepted and resolved as soon as the request reaches the ZIA Public Service Edge. The DNS is configurable by endpoint and many other conditions in the destination NAT policy and essentially amounts to two modes:
- Transit Option: This mode passes DNS requests through the proxy. A proxy safely hides the customer's IP address from third parties, including the external resolver (DNS security policy is still applied). Hiding the IP address is good for iterative requests that Zscaler can’t resolve, but DNS Control can secure.
- Resolver Option: This option sees and intercepts the DNS request at the Public Service Edge and resolves the request pending DNS Control policy. This option provides all the security and performance benefits of quickly resolving DNS requests with a geographic context where users get the closest Microsoft or Amazon Web Services (AWS) point of presence.
- Zscaler recommends using the Resolver option. You can enable traffic to reach Zscaler's Trusted DNS Resolver in two ways:
- Enable a [NAT control rule](/zia/configuring-nat-control-policy).
- Use a [Z-Tunnel 2.0 with specified DNS exclusions and inclusions](https://community.zscaler.com/t/configuring-client-connector-for-dns-control-and-cloud-firewall/19101).
Operations Phase
This section describes common practices used to operate Zscaler solutions when integrated with your environment. You can monitor and tune DNS Control during operations to meet your infrastructure needs.
Prerequisites
For DNS Control operation, verify the following prerequisites:
- Document the methodology for deploying DNS Control (either the Transit or Resolver option).
- Consider [destination NAT for selective queries](/zia/about-nat-control) and its performance impact.
- Give the support team access to the DNS dashboard. This provides visibility into the most blocked domain categories and users, providing insights into incidents raised due to malicious domains getting blocked.
Common Troubleshooting Items
The following list describes common issues related to DNS Control operation:
- Internal domains are blocked or not accessible: Check if the internal domains are part of DNS exclusions.
- Iterative queries are not getting resolved: Iterative DNS requests require additional policy configurations to transit the traffic through the Zscaler service (depending on your methodology). Disable the default rule in NAT Control or create a higher precedence rule to support iterative queries transiting the ZIA service. To learn more, see [About NAT Control](/zia/about-nat-control).
- New DNS domains are getting blocked: Domains that fall under malicious domains might get blocked per your policy. Verify whether these domains are getting blocked under blocked domains in the [DNS Overview dashboard](/zia/about-dashboards#DNS-overview).
Deployment Checklist
Zscaler recommends downloading the [DNS Control Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zia-deployments-operations/dns-control-deployment-and-operations-guide/DNS-Control-Deployment-Operations-Checklist.pdf) to help plan and implement DNS Control: [Download PDF](/downloads/zscaler-deployments-operations/zia-deployments-operations/dns-control-deployment-and-operations-guide/DNS-Control-Deployment-Operations-Checklist.pdf)
Additional Information
For more SaaS Security information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](http://community.zscaler.com/).