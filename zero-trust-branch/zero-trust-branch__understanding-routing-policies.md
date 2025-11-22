# Understanding Routing Policies
Source: https://help.zscaler.com/zero-trust-branch/understanding-routing-policies
PDF: https://help.zscaler.com/pdf/com/en/1532641.pdf

Zero Trust Branch allows you to create routing policies and control traffic from branch sites to specific destinations based on defined criteria, ensuring secure and optimized routing. These policies allow granular control over how traffic flows to Zscaler Internet Access (ZIA), Zscaler Private Access (ZPA), or directly to the internet.
Zero Trust Branch provides a comprehensive set of capabilities to enable secure and efficient routing:
- **Policy-Based Routing**: Dynamically route traffic based on defined criteria such as source, destination, port, device, user, etc. to ensure optimal traffic flow.
- **Granular Segmentation**: Apply routing policies at the network, device, domain, application, or user level for precise control and visibility.
- **High Availability**: Use redundant gateways and interfaces to maintain continuous traffic flow and prevent service disruption.
- **Integrated Security**: Seamlessly integrate with ZIA and ZPA to enforce zero trust principles across all traffic paths.
- **Simplified Management**: Provide centralized configuration and monitoring via the Zero Trust Branch Admin Portal.
- **Performance Optimization**: Direct critical traffic along optimal paths to minimize latency and enhance the user experience.
When a new site is created, Zero Trust Branch automatically generates the following default routing policies:
- **Default-ZPA-PBR**: Ensures all traffic originating from the Airgap network and destined for any Zscaler application segment is routed through ZPA. This rule provides branches secure, zero trust access to internal applications based on the source.
- **Default ZIA Rule**: Ensures all internet-bound or Software as a Service (SaaS) traffic originating from the Airgap network is routed to ZIA via IPSec. This rule ensures secure access to the internet and SaaS applications for branch sites. It uses auto-established IPSec tunnels for secure branch-to-ZIA connectivity.
- **Default-App-Segment-PBR**: Ensures traffic originating directly from Zero Trust Branch destined for Zscaler app segments is routed to ZPA.
- **Default Zscaler Rule**: A catch-all routing rule that ensures any traffic from any IPv4 network destined for Zscaler IP addresses is sent through the LAN/WAN interfaces. It routes traffic to the nearest Zscaler data center and uses primary and secondary interfaces for redundancy.
By leveraging default policies, you can immediately enforce zero trust principles while maintaining seamless connectivity to internal applications, cloud services, and the internet.
Policy-Based Routing
Zero Trust Branch makes routing decisions based on defined criteria in the routing policies, allowing traffic to be steered dynamically between WAN interfaces. Zero Trust Branch can load-balance, fail over, or programmatically optimize distribution. For example, you can configure a routing policy that connects a source (e.g., a virtual machine (VM), endpoints, or users) to the internet via two WAN links, using the primary interface for active traffic and the secondary interface for failover or redundancy. The following image illustrates the topology for policy-based routing:
![Illustration of polciy-based routing topology](/downloads/zero-trust-branch/administration/deployment-configuration/understanding-routing-policies/dia_zero-trust-branch_policy-routing.png)
With these policies, IT teams can define routing rules to optimize performance, maintain compliance, and adapt to evolving business needs, ensuring that every connection and device is protected at all times.
To learn more, see [Configuring Routing Policies](/tech-pubs-drafts/configuring-routing-policies) and [Managing Routing Policies](/tech-pubs-drafts/managing-routing-policies).