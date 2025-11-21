# Networking Flows for Cloud Connector
Source: https://help.zscaler.com/unified/networking-flows-cloud-connector
PDF: https://help.zscaler.com/pdf/com/en/1517916.pdf

Every Zscaler Cloud Connector has a minimum of two network interfaces that communicate with the Zscaler cloud for different purposes.
- [Management Interface](#managementinterfacelist)
- [Service Interfaces](#serviceinterfaceslist)
[See image.](#CCTrafficFlowschart)
[]A management interface can manage and configure security devices. There are outbound and inbound network flows that operate with a management interface.
The outbound network flows provide:
- Control plane communications with Zscaler cloud for enrollment, service discovery, log streaming, and software updates
- Retrieval of security credentials from cloud providers
- Control plane DNS resolution
- Control plane Network Time Protocol (NTP) traffic
- Zscaler remote support services
Inbound network flows provide Secure Socket Shell (SSH) access for troubleshooting.
[]Service interfaces can communicate with devices and services on a network. There are inbound and outbound network flows that operate with service interfaces.
The outbound network flows provide:
- Internet & SaaS forwarding
- Private Applications forwarding
- Direct (bypass Zscaler) forwarding
- Data plane DNS resolution
The inbound network flows provide:
- Load balancer health checks
- Workload traffic
For Amazon Web Services (AWS) only, outbound/inbound network flow enables GENEVE Protocol.
Traffic Forwarding
Cloud Connectors receive traffic from load balancers via the service network interface. They then determine where to send the traffic. There are currently four types of traffic forwarding rule types that you can configure to send traffic to different destinations. To learn more, see [Configuring Traffic Forwarding Rules](/cloud-branch-connector/configuring-traffic-forwarding-rule).
- ZIA: Forwards internet-bound traffic that matches an Internet & SaaS rule to Internet & SaaS gateways over a configurable encrypted or unencrypted tunnel.
- ZPA: Forwards the private application traffic that matches a Private Applications rule to Private Applications over an encrypted tunnel.
- Direct: Bypasses Internet & SaaS/Private Applications and forwards traffic directly to the destination server using the Zscaler service IP address.
- Drop: Discards packets matching the Drop rule.
[See image.](#TrafficForwardingMethods)
[]
DNS Forwarding
DNS forwarding operates when workloads are configured to send DNS through Cloud Connectors. However, this is not required in every instance. The following use cases describe cases where DNS is required. To learn more, see [About DNS Policies](/cloud-branch-connector/about-dns-policies).
- [Private Applications App Segments Defined by DNS Hostnames, FQDNs, and Domains](#ZPAAppSegmentsDNS)
- [Internet & SaaS DNS Controls](#zianonmatchzpa)
- [Synthetic IP Pools](#SyntheticIPPools)
[]When you deploy Cloud Connector with Private Applications, the workload forwards DNS queries to the Cloud Connector to match against Private Applications app segments. The Cloud Connector matches the DNS query against known Private Applications app segments, and upon a match, the Cloud Connector queries the Zscaler service to obtain a synthetic IP address. The synthetic IP address returns to the workload as the resolved IP.
[See image.](#ZPAAppSegmentDNSMatch)
DNS queries that do not match a Private Applications app segment can reach a direct traffic forwarding rule. Cloud Connector forwards the DNS query to an upstream DNS server for resolution. The DNS server attempts to resolve the query and responds with the resolved IP address.
[See image.](#NonZPAMatchDirect)
[]When you are using Internet & SaaS DNS Controls, DNS from workloads forwards through Cloud Connector. When the DNS matches an Internet & SaaS traffic forwarding rule, the DNS query is tunneled to the Internet & SaaS gateway for DNS resolution. The resolved IP is returned to the workload when the Internet & SaaS DNS Control allows it.
[See image.](#ZPANonMatchZIA)
[]You can configure Cloud Connector DNS rules to allocate Private Applications synthetic IP pools based on various criteria. You can configure Cloud Connector DNS and traffic forwarding rules to determine where DNS requests are redirected and forwarded to.
The Zscaler service can support environments with overlapping IP addresses and decouple workloads from the destination application networks using a zero trust networking approach. If you define applications using DNS hostnames or domains in Private Applications, the true private IP addresses of the servers are hidden from the requesting workloads through Cloud and Branch Connectors.
The default Private Applications IP pool in Zscaler connector tenants is 10.254.0.0/19. Administrators can either change the IP pool to a desired Classless Inter-Domain Routing (CIDR) range or provide different IP pools based on Cloud or Branch Connector locations.
When you register a Cloud Connector or Branch Connector with Zscaler, it learns the private applications defined in Private Applications, and the Cloud Connector or Branch Connector is permitted to process via Private Applications client forwarding and access policies. When a workload or server makes a DNS query for the application, such as `sharepoint.acme.net`, the Cloud Connector or Branch Connector matches it against the learned application segments. If the query matches a segment, the Cloud Connector or Branch Connector maps or receives a new synthetic IP address from Zscaler to use for this application. The synthetic IP address is returned via the DNS response to the originating workload server, which uses the address for the application traffic. The Zero Trust Exchange (ZTE) polls all App Connectors to determine which can successfully resolve and connect to the requested application.
Zscaler saves the true IP address for troubleshooting and logging purposes, but the workload server never knows what that private IP address is. This arrangement is helpful if the workload and target application are on different networks with IP overlap, such as both applications using 192.0.2.0/24. Because the workload has a synthetic IP address and routes through the Cloud Connector or Branch Connector, you can access the application successfully if policy configuration allows.
[See image.](#SyntheticIPPool)
[]
![Cloud Connector Traffic Flows](/downloads/cloud-branch-connector/deployment-management/cloud-connector-deployment-management/networking-flows-cloud-connector/CCTrafficFlowschart.png)
[]
![Traffic Forwarding Methods](/downloads/cloud-branch-connector/deployment-management/cloud-connector-deployment-management/networking-flows-cloud-connector/TrafficForwardingMethods.png)
[]
![ZPA App Segment DNS Match](/downloads/cloud-branch-connector/deployment-management/cloud-connector-deployment-management/networking-flows-cloud-connector/ZPAAppSegmentDNSMatch.png)
[]
![Non-ZPA Match (Direct)](/downloads/cloud-branch-connector/deployment-management/cloud-connector-deployment-management/networking-flows-cloud-connector/NonZPAMatchDirect.png)
[]
![ZPA Non Match (ZIA) flows](/downloads/cloud-branch-connector/deployment-management/cloud-connector-deployment-management/networking-flows-cloud-connector/ZPANonMatchZIA.png)
[]![Cloud Connector DNS rules configured to allocate ZPA synthetic IP pools](/downloads/cloud-branch-connector/deployment-management/cloud-connector-deployment-management/networking-flows-cloud-connector/Synthetic%20IP%20Pools%20Diagram.png)