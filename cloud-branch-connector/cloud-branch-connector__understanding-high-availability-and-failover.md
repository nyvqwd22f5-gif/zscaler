# Understanding High Availability and Failover
Source: https://help.zscaler.com/cloud-branch-connector/understanding-high-availability-and-failover
PDF: https://help.zscaler.com/pdf/com/en/1455436.pdf

High Availability (HA) is critical to ensure continued secure access to applications for workloads routing through Zscaler Cloud Connector. The various areas to consider when deploying are, but not limited to:
- Cloud Connectors to Zero Trust Exchange (ZTE) HA and failover
- Cloud-Native Load Balancers to support horizontal scaling and failover of Cloud Connectors
- Using cloud provider best practices to ensure HA across availability zones within regions
[See image.](#highavailabilityfailover)
[][![High availability and failover flows for Cloud Connector.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/understanding-high-availability-and-failover-draft-doc-44779/High%20Availability%20and%20Failover.png)
]
Blue arrows indicate primary, or active, Zscaler Zscaler Internet Access (ZIA) tunnels. Green lines indicate secondary ZIA tunnels.
Load Balancing
Zscaler integrates with the native load balancing services offered by respective cloud providers. The load balancers conduct HTTP health probes on a defined port selected during deployment to determine the health of each Cloud Connector. Cloud Connector listens to the configured port for HTTP health probes on the `?cchealth` path from the load balancers. A healthy Cloud Connector has a 200 HTTP response code, and an unhealthy Cloud Connector has a 503 HTTP response code or no response. Health probes ensure that the Cloud Connector VM is functional and can successfully forward workload traffic to ZIA Public Service Edges or Private Service Edges and ZPA Public Service Edges or Private Service Edges.
Cloud Connectors scale horizontally and are all active, enabling organizations to add more Cloud Connectors into a group to support higher throughput per egress location. New sessions should be sent to healthy Cloud Connectors. In some cases, such as existing connections flowing through a Cloud Connector that becomes unhealthy, the sessions might temporarily fail until the flow ages or times out and the load balancer begins to send the session through a healthy Cloud Connector.
- [Health Probe Intervals](#HealthProbeIntervalsLB)
[]Zscaler deployment templates utilize a recommended default configuration for health check intervals. The Microsoft Azure Load Balancer defaults to 15 seconds, and Amazon Web Services (AWS) Gateway Load Balancer defaults to 30 seconds.
The default settings are optimized to take unhealthy Cloud Connectors out of the rotation efficiently, avoiding network "bumps."
While the default deployment templates are configurable, contact Zscaler Support before changing any settings to ensure an optimal configuration is made.
Data Plane
The data plane is used to process and forward workload traffic to ZIA Public Service Edges or Private Service Edges and ZPA Public Service Edges or Private Service Edges. The data plane is composed of outbound connections from the service interface of each Cloud Connector.
- [Internet Egress (ZIA)](#InternetEgressZIADP)
- [Private Apps (ZPA)](#PrivateAppsZPADP)
[]By default, each Cloud Connector tenant comes with a default rule to forward internet-bound traffic to ZIA using automatically selected gateways. Similar to the control plane, the ZIA Public Service Edges or Private Service Edges and ZPA Public Service Edges or Private Service Edges are selected using geolocation. It is possible to configure traffic forwarding rules to utilize specific Public Service Edges, Virtual Service Edges, or sub-clouds for various Cloud Connector groups and locations.
Workload traffic that is processed by traffic forwarding rules configured with the ZIA forwarding method uses the primary gateway as the active tunnel to the ZIA Public Service Edges or Private Service Edges and ZPA Public Service Edges or Private Service Edges. The default gateway configuration will fail-close, meaning that internet-bound traffic from workloads is dropped if none of the Cloud Connectors in the same group are able to establish connectivity to any of the ZIA Service Edges. Customers can change this configuration to fail-open, allowing workloads that are accessing the internet to continue doing so. The fail-open option means the egressing traffic is flowing through Zscaler for inspection and policy control.
In the event of a failed connection, Cloud Connector marks the secondary gateway as the active tunnel and forwards workload traffic via the secondary gateway to the ZIA Public Service Edges or Private Service Edges and ZPA Public Service Edges or Private Service Edges. When the primary gateway is healthy again, it is marked as active and Cloud Connector forwards new sessions to the ZIA Public Service Edges or Private Service Edges and ZPA Public Service Edges or Private Service Edges via the primary gateway tunnel.
Cloud Connector monitors the gateway connections to ensure the data path exists so that traffic can be inspected at the ZIA Public Service Edges or Private Service Edges and ZPA Public Service Edges or Private Service Edges. If the active tunnel forwarding workload traffic to the ZIA Public Service Edges or Private Service Edges and ZPA Public Service Edges or Private Service Edges fails, the Cloud Connector will fail over to the secondary tunnel in approximately 30 seconds.
By default, Cloud Connector automatically tries to connect to a tertiary ZIA Public Service Edge or Private Service Edge and ZPA Public Service Edge or Private Service Edge if the primary and secondary have failed. This is important to note because Cloud Connector is not limited to just the two ZIA Public Service Edges or Private Service Edges and ZPA Public Service Edges or Private Service Edges that are selected for tunneling.
To learn more about the ZIA Gateways, see [About Zscaler Internet Access Gateways](/cloud-branch-connector/about-zia-gateways).
[]Cloud Connectors that are enrolled with Zscaler Private Access (ZPA) automatically establish a secure connection to an optimal ZPA Public Service Edge or Private Service Edge in the ZTE. This secure connection allows for the workloads accessing private applications to be securely tunneled to the ZPA Public Service Edge or Private Service Edge and allows the data path to be connected through App Connectors configured for the accessed application.
Cloud Connector, similar to Zscaler Client Connector, attempts to resolve the most optimal or nearest ZPA Public Service Edge or Private Service Edge for private application access.
Zero Trust Exchange (ZTE)
Cloud Connector is a Zscaler purpose-built Zero Trust gateway to forward traffic to the ZTE. With over 150 global data centers, the ZIA and ZPA Public Service Edges enable deployments in almost any region with optimal connectivity.
Organizations can forward users, workload, and Internet of Things (IoT) devices to the ZTE using:
- Zscaler Client Connector
- Cloud Connector
- Branch Connector
- PAC Files (ZIA only)
- GRE Tunnels (ZIA only)
- IPSec Tunnels (ZIA only)
The ZTE HA is identical to the aforementioned forwarding methods.
Cloud Providers
Zscaler uses the best practices for HA with cloud providers such as AWS and Azure. Regions and availability zones are HA aspects to take into consideration when deploying Cloud Connector.
- [Regions](#RegionsCP)
- [Availability Zones](#AvailabilityZonesCP)
[]In most cases, Cloud Connector is deployed into groups or locations that serve the same internet egress. Whether centralized, using AWS Transit Gateway or Azure Virtual WAN Hub, or decentralized, where each Virtual Private Cloud (VPC) or Azure Virtual Network (VNet) has direct internet access, each region serves a number of different egress points for Cloud Connector and does not affect other regions even if there is a cloud provider outage.
[]Zscaler recommends deploying at least two Cloud Connectors per availability zone and across at least two availability zones. This takes into account HA without service interruption intra or inter availability zone per egress location.
Zscaler also recommends enabling AWS Gateway Load Balancer (GWLB) cross-zone load balancing for all production deployments. This setting ensures that GWLB VPC endpoints deployed across multiple availability zones can use Cloud Connector in all availability zones instead of only its own.