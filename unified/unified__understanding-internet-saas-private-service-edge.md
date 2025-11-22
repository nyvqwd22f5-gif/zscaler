# Understanding Internet & SaaS Private Service Edge
Source: https://help.zscaler.com/unified/understanding-internet-saas-private-service-edge
PDF: https://help.zscaler.com/pdf/com/en/1494951.pdf

Zscaler can extend its patented cloud architecture to an organization's premises by providing Internet & SaaS Private Service Edge. Private Service Edge is part of the Zscaler cloud and performs the same service as the [Internet & SaaS Public Service Edge](/unified/about-public-service-edges). It includes support for features such as Firewall, Sandbox, and Data Loss Prevention (DLP). It communicates with other nodes in the cloud, such as the Central Authority (CA) for user authentication and policy updates, and the cloud routers and Nanolog clusters for logging and reporting.
Private Service Edges are installed in an organization’s data center and are dedicated to the organization’s traffic, but they are managed and maintained by Zscaler Cloud Operations. Zscaler monitors and maintains the Private Service Edges with a near-zero touch from your organization.
Zscaler treats Private Service Edge as an extension of the Internet & SaaS service. Even when you install and maintain it on your data center, Private Service Edge is subject to maintenance or alterations, updates, enhancements, additions, or improvements at any time. To learn more, see [Maintenance Support for Internet & SaaS Private Service Edge](/unified/maintenance-support-private-service-edge).
Private Service Edges typically benefit organizations that have certain geopolitical requirements or those that use applications that require an organization's IP address as the source IP address.
Private Service Edge supports IPv6 traffic only if it's forwarded via supported IPv4-based tunnels. To learn more about supported traffic forwarding mechanisms, see [Understanding IPv6 Support](/unified/understanding-ipv6-support). Contact Zscaler Support to enable and configure IPv6 for your organization. You must ensure that the upstream path of your organization's network supports IPv6.
![Diagram showing a Private Service Edge Deployment](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/service-edge/about-service-edge/ZIA-About-Private-Service-Edge-Diagram.png)
Private Service Edge comprises two Zscaler components, Service Edge instances and Zscaler load balancers (LBs). The Service Edge instance processes the following transactions:
- Upload (Request): Transmission of user traffic from the LB instance to the destination.
- Download (Response): Transmission of traffic from the destination to the user.
The LB instance processes the upload transactions from the users evenly across the Service Edge instances. Standard deployments of all the Private Service Edge models consist of integrated LB instances and process upload and download transactions within the same hardware. However, larger deployments require significant upload and download throughput, which requires the Private Service Edge 5 with the Dedicated LB cluster design.
The Private Service Edge is available in both hardware and virtual form. Virtual Service Edge can be deployed on [VMware ESX/ESXi](/unified/configuring-virtual-service-edge-clusters), [Microsoft Azure](/unified/configuring-virtual-service-edge-microsoft-azure), [Amazon Web Services (AWS) EC2](/unified/configuring-virtual-service-edge-amazon-web-services), [Microsoft Hyper-V](/unified/configuring-virtual-service-edge-microsoft-hyper-v), and [Google Cloud Platform (GCP)](/unified/configuring-virtual-service-edge-google-cloud-platform). To learn more, see [About Virtual Service Edge](/unified/about-virtual-service-edges).
The following table shows the details and throughput capabilities of the Private Service Edge hardware platform:
| Cluster Design | Description | Sized for ISP Link Speeds of Download |
| -------------- | ----------- | ------------------------------------- |
| Private Service Edge 3 with Integrated LB | An annual subscription to Private Service Edge with 3 Service Edge instances, an integrated LB, and a 1GE network interface. | 1 Gbps |
| Private Service Edge 5 with Integrated LB | An annual subscription to Private Service Edge with 5 Service Edge instances, an integrated LB, and a 10GE network interface. | 2 Gbps |
| Private Service Edge 5 with Dedicated LB | An annual subscription to Private Service Edge with 6 Service Edge instances, a dedicated LB with up to 4 LB instances, and a 10GE network interface. | Greater than 5 Gbps |
The preceding sizing suggestion is based on the assumption that the upload throughput is around 30% of the download throughput. The maximum upload throughput per cluster is limited to 800 Mbps on Private Service Edge 3, 2.5 Gbps on Private Service Edge 5, and 6 Gbps per LB instance on Private Service Edge 5 with Dedicated LB.
Private Service Edge Architecture
All Private Service Edge cluster designs are built with high availability, resiliency, and scalability in mind. To ensure redundancy, they are deployed with a minimum of N+1 hardware. The LB instances are configured for active-passive fault tolerance and share a virtual IP address (VIP) using Common Address Redundancy Protocol (CARP). All Service Edge instances are active-active behind the cluster VIP address and are automatically removed from the load balancing pool via active health monitoring if an instance or node were to fail.
All traffic destined for the Private Service Edge must be sent to the cluster VIPs. The active LB instance listening on behalf of the VIP then forwards the packet to one of the Service Edge instances in the cluster pool for processing. The Service Edge instance requests the web server, which then responds to the Service Edge instance that processed the original request, which forwards the response directly to the user.
Zscaler uses the Direct Server Return (DSR) method of load balancing, so the response doesn't traverse through the LB on the return path.
The following are examples of Private Service Edge cluster designs and their packet flow:
- [Private Service Edge 3 with Integrated LB](#pse3-integrated-lb)
- [Private Service Edge 5 with Integrated LB](#pse5-integrated-lb)
- [Private Service Edge 5 with Dedicated LB](#pse5-dedicated-lb)
[]The following diagram illustrates a cluster of 2 Private Service Edge 3 servers with a total of 2 Zscaler LB instances and 6 Service Edge instances that are all connected to the same L2 switching fabric. All traffic sent to the cluster VIP is forwarded to the active LB instance. For example, the user sends a request to access a web server on the internet. The VIP sends the request to the active LB instance (LB (A)), which then forwards the request to one of the Service Edge instances (Service Edge 3) on one of the Private Service Edge 3 servers (Private Service Edge 3 (B)) of the cluster. The Service Edge instance makes the request to the web server. The web server then responds to the Service Edge instance that made the request, which forwards the response directly to the user. Zscaler uses the DSR method of load balancing, so the response doesn't traverse through the LB.
![Diagram illustrating the request and response traffic flow for Private Service Edge 3.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/service-edge/about-service-edge/ZIA-Private-Service-Edge-Traffic-PSE3.png)
[]The following diagram illustrates a cluster of 2 Private Service Edge 5 servers with a total of 2 Zscaler LB instances and 10 Service Edge instances that are all connected to the same L2 switching fabric. All traffic sent to the VIP is forwarded to the active LB instance. For example, the user sends a request to access a web server on the internet. The VIP sends the request to the active LB instance (LB (A)), which then forwards the request to one of the Service Edge instances (Service Edge 1) on one of the Private Service Edge 5 servers (Private Service Edge 5 (B)) of the cluster. The Service Edge instance makes the request to the web server. The web server then responds to the Service Edge instance that made the request, which forwards the response directly to the user. Zscaler uses the DSR method of load balancing, so the response doesn't traverse through the LB.
![Diagram illustrating the request and response traffic flow for Private Service Edge 5.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/service-edge/about-service-edge/ZIA-Private-Service-Edge-Traffic-PSE5.png?1681813824)
[]The following diagram illustrates a cluster of 4 Private Service Edge 5 servers and 2 Zscaler Dedicated LBs with a total of 4 LB instances and 24 Service Edge instances that are all connected to the same L2 switching fabric. All traffic sent to the VIP is forwarded to an active LB instance, in one of the Dedicated LBs. For example, the user sends a request to access a web server on the internet. The VIP sends the request to the active LB instance (LB 1), in one of the Dedicated LBs (Dedicated LB (Y)), which then forwards the request to one of the Service Edge instances (Service Edge 1) on one of the Private Service Edge 5 servers (Private Service Edge 5 (A)). The Service Edge instance makes the request to the web server. The web server then responds to the Service Edge instance that made the request, which forwards the response directly to the user. Zscaler uses the DSR method of load balancing, so the response doesn't traverse through the LB.
![Diagram illustrating the request and response traffic flow for Private Service Edge 5 with Dedicated LB.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/service-edge/about-service-edge/ZIA-Private-Service-Edge-Traffic-PSE5-Dedicated-LB.png?1681890194)
Zscaler does not support standalone Private Service Edge deployments. Each Private Service Edge cluster must have a minimum of two Private Service Edges to ensure redundancy. If dedicated LBs are included in the design, they also must be deployed in a minimum of two.
[]Network and IP Address Requirements
Private Service Edge is part of the Zscaler cloud. It communicates with other nodes in the cloud, such as the Central Authority (CA) for user authentication and policy updates, and the cloud routers and Nanolog clusters for logging and reporting. Zscaler Cloud Operations also needs remote access to the Private Service Edge for monitoring and maintenance, as well as updates as the cloud expands.
Therefore, Zscaler recommends that an organization deploy the Private Service Edge inside their DMZ and restrict access to Zscaler IP addresses listed in config.zscaler.com/<Zscaler Cloud Name>/zia-sedge. In this scenario, your organization configures your firewall to allow Zscaler cloud communications and remote access to Zscaler Cloud Operations. An organization can deploy a Private Service Edge:
- Inside the DMZ
- Outside the corporate firewall
- Behind the network firewall
The following table shows the IP addresses and switch port requirements for Private Service Edge 3 and Private Service Edge 5 with Integrated LB:
|  | Private Service Edge 3 | Private Service Edge 5 |
| --- | ---------------------- | ---------------------- |
| Service IP AddressesIPv6 addresses are required only if your organization needs IPv6 traffic to egress their Private Service Edges. | 3 IPv4 and 3 IPv6 addresses per Private Service Edge node | 5 IPv4 and 5 IPv6 addresses per Private Service Edge node |
| Management IP Addresses | 1 | 1 |
| IPMI IP Address | 1 | 1 |
| Integrated LB IP Address | 1 | 1 |
| Virtual IP Address per Cluster | 1 | 1 |
| Switch Ports | 6 x 1GE | 2 x 10GE, 3 x 1GE |
The following table shows the IP addresses and switch port requirements for Private Service Edge 5 with Dedicated LB:
|  | Private Service Edge 5 |
| --- | ---------------------- |
| Service IP AddressesIPv6 addresses are required only if your organization needs IPv6 traffic to egress their Private Service Edges. Dedicated LB doesn't require any IPv6 address. | 6 IPv4 and 6 IPv6 addresses per Private Service Edge node |
| LB IP Address | Up to 4 |
| MTS IP Address | 1 |
| Management IP Addresses | 1 |
| IPMI IP Address | 1 |
| Virtual IP Address per Cluster | Up to 4 |
| Switch Ports | 3 x 1GE, up to 8 x 10GE |
These IP addresses must be public. Forwarding IPv6 traffic via the IPv4-based IPSec tunnel requires an additional IPv4 or IPv6 address for each Private Service Edge node.
If the deployment requires RFC 1918 IP addresses and NAT, the IP addresses for the Internet & SaaS Private Service Edges must be with 1:1 static NAT to a public IP address. IPv6 is not supported in this type of deployment.
Additionally, you must provide the following network information to Zscaler:
- The gateway address
- The IP addresses of your organization's NTP servers. Otherwise, Zscaler uses public NTP servers.
- The IP addresses of your organization's DNS servers. Otherwise, Zscaler uses public DNS servers.
- The installation location address and contact details
To learn more, see [Deploying Internet & SaaS Private Service Edge](/unified/deploying-internet-saas-private-service-edge) and [Installing Internet & SaaS Private Service Edge](/unified/installing-internet-saas-private-service-edge).
Sizing Guidelines
The following table shows the specifications for the available Private Service Edge and Dedicated LB hardware platforms:
|  | Private Service Edge 3 with Integrated LB | Private Service Edge 5 with Integrated LB | Private Service Edge 5 with Dedicated LB |
| --- | ----------------------------------------- | ----------------------------------------- | ---------------------------------------- |
| Number of Service Edge Instances | 3 | 5 | 6 |
| Number of LB Instances | 1 | 1 | Up to 4 |
| Maximum Upload Throughput per Cluster | 800 Mbps | 2.5 Gbps | Up to 24 Gbps |
| Maximum Private Service Edge per Cluster | 3 | 3 | 10 |
| Minimum Private Service Edge per Cluster | 2 | 2 | 2 |
| Dedicated LB per Cluster | N/A | N/A | 2 |
| Network Interface | 1GE | 10GE | 10GE |
For more than 1 Gbps of download throughput, Zscaler recommends deploying Private Service Edges. Any deployment requiring more than 5 Gbps of total throughput must include the Dedicated LB hardware. Contact your Zscaler Sales representative for further details.
Private Service Edge sizing is done based on throughput. You must consider both upload and download throughput when sizing a Private Service Edge deployment. If the upload throughput is unknown, 30% of the expected download throughput is considered as upload throughput based on the industry average.
The following is an example of Private Service Edge 3 deployment based on an organization's throughput:
An organization has a data center with a 1GE switch port and requires a network with 800 Mbps of download throughput. In this scenario, the upload throughput required is 240 Mbps, which is 30% of the 800 Mbps download throughput. The total throughput that the Private Service Edge cluster must support is 1.04 Gbps (800 Mbps + 240 Mbps = 1.04 Gbps). Also, the deployment must be on Private Service Edge hardware supporting 1GE network interfaces. To meet these sizing requirements, Zscaler recommends deploying 2 nodes of Private Service Edge 3 because:
- Private Service Edge 3 is always quoted with N+1 redundancy to meet the Zscaler SLA requirements and ensure service continuity. The 2 instances of Private Service Edge 3 provide additional support for traffic bursts and redundancy in case of a hardware failure.
- Private Service Edge 3 cluster handles up to 1.2 Gbps of download throughput and 2 Gbps of total throughput.
- Private Service Edge 3 hardware supports 1GE network interfaces.
The following is an example of Private Service Edge 5 deployment based on an organization's throughput:
An organization has a data center with a 10GE switch port and requires a network with 1.8 Gbps of download throughput. In this scenario, the upload throughput required is 540 Mbps, which is 30% of the 1.8 Gbps download throughput. The total throughput that the Private Service Edge cluster must support is 2.34 Gbps (1.8 Gbps + 540 Mbps = 2.34 Gbps). Also, the deployment must be on Private Service Edge hardware supporting 10GE network interfaces. To meet these sizing requirements, Zscaler recommends deploying 2 nodes of Private Service Edge 5 because:
- Private Service Edge 5 is always quoted with N+1 redundancy to meet the Zscaler SLA requirements and ensure service continuity. The 2 instances of Private Service Edge 5 provide additional support for traffic bursts and redundancy in case of a hardware failure.
- Private Service Edge 5 cluster services up to a maximum of 3.9 Gbps of download throughput and 5 Gbps of total throughput.
- Private Service Edge 5 hardware supports 10GE network interfaces.
SFPs are not shipped along with the server. To learn more about the SFP requirements, refer to the [Intel product support](https://www.intel.com/content/www/us/en/support/articles/000007045/ethernet-products/700-series-network-adapters-up-to-40gbe.html) page.
The following table shows the Private Service Edge deployment options for other sizing requirements:
| Required Download Throughput | Required Upload Throughput | Total Throughput | Deployment Options |
| ---------------------------- | -------------------------- | ---------------- | ------------------ |
| 560 Mbps | 170 Mbps | 730 Mbps | 2 x Private Service Edge 3 |
| 700 Mbps | 210 Mbps | 1 Gbps | 2 x Private Service Edge 3 |
| 1 Gbps | 300 Mbps | 1.3 Gbps | 2 x Private Service Edge 3 |
| 1.75 Gbps | 525 Mbps | 2.27 Gbps | 2 x Private Service Edge 5 |
| 2.45 Gbps | 735 Mbps | 3.18 Gbps | 3 x Private Service Edge 5 |
| 3.5 Gbps | 1.05 Gbps | 4.55 Gbps | 3 x Private Service Edge 5 |
For more than 1 Gbps of download throughput, Zscaler recommends deploying Private Service Edge 5. Any deployment requiring more than 5 Gbps of total throughput must be reviewed by Zscaler Cloud Operations.
Locations for Private Service Edges
Adding a [location](/unified/configuring-locations) to a Private Service Edge cluster allows you to:
- View, categorize, and generate reports of transaction logs for their clusters.
- Manage various settings (Authentication settings, IP Surrogacy settings, XFF consumption, and Location group settings for SSL inspection & web filtering policies).
- Map traffic and enforcement in a NAT environment.
However, creating a new location for the Private Service Edges can make the cluster an open proxy, as the CA doesn't have an automatic link between the newly created Private Service Edge locations and your organization's actual Private Service Edge clusters. If you choose to make the Private Service Edge a part of a location, then here are a few best practices:
- Use the Static IP addresses provisioned by you in the Admin Portal for the locations. One Static IP address per cluster.
- The public IP must be owned by your organization and must not be in use or assigned in any way to the Private Service Edge cluster.
- Share your organization's known traffic forwarding ranges for the allowlist with Zscaler.
- Contact Zscaler Support to ensure the locations are mapped to the Private Service Edges. Zscaler adds the location IP address and known traffic forwarding ranges to all the Private Service Edge instances for the respective cluster.
Zscaler Support ensures that the Private Service Edge cluster is not an open proxy by configuring the location IP address and adding your organization's known traffic forwarding ranges, so that only your organization's traffic is mapped to the respective Private Service Edge location policies. Any traffic not coming from your organization's allowlist is treated as a remote user and forced to authenticate.
There can be disruption in service while Zscaler maps the location to their Private Service Edges, and you must follow standard Network Operations Center (NOC) change protocols if the cluster is already in production.
Deployable Locations
Zscaler can deploy Private Service Edges in locations that meet the following requirements:
Lower bandwidths can be considered as exceptions.
- Locations with certain geopolitical requirements and regulations.
- Locations that experience high latency when connecting to Public Service Edges.
- Applications that require an organization's IP address as the source IP address.
- Users who need to see localized content.
- Organizations and locations where the overall upload throughput traffic is beyond 1 Gbps or download throughput traffic is beyond 2 Gbps.