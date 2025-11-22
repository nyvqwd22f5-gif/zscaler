# About Virtual Service Edges
Source: https://help.zscaler.com/zia/about-virtual-service-edges
PDF: https://help.zscaler.com/pdf/com/en/1401226.pdf

[Watch a video about Virtual Service Edges.](https://fast.wistia.net/embed/iframe/xa3h5zhhg8)
New or clean deployment of ZIA Virtual Service Edge requires a VM image running on Zscaler OS version 24.
Zscaler typically recommends that organizations forward traffic to the [ZIA Public Service Edges](/zia/about-public-service-edges) in the Zscaler cloud. However, some organizations might have certain requirements, such as:
- Locations with certain geopolitical requirements and regulations.
- Locations that experience high latency when connecting to Public Service Edge.
- Applications that require an organization's IP address as the source IP address.
- Users who need to see localized content.
If your organization has similar requirements, then with Zscaler's approval, you can extend the Zscaler patented cloud architecture to your organization's premise by licensing and deploying Virtual Service Edge. Virtual Service Edge uses a virtual machine (VM) to function as a full-featured Public Service Edge dedicated to your organization's traffic. Virtual Service Edges perform the same service as the Public Service Edges in the Zscaler cloud, including support for features, such as Firewall, Sandbox, and Data Loss Prevention (DLP).
The Source IP Anchoring feature is not supported with Virtual Service Edges.
Virtual Service Edges provide the following benefits and allow you to:
- Retain your organization's Source IP address when accessing SaaS or internet applications that require it.
- Let users access certain geolocal content.
- Use a fully managed, on-premises Service Edge with automated, non-intrusive, and periodic software upgrades and security updates.
Virtual Service Edges are part of the Zscaler cloud. They communicate with the Zscaler cloud for user authentication, policy updates, logging, and reporting. Admins define policies only once through the ZIA Admin Portal. Additionally, after users are signed in and authenticated to the Zscaler service, the service always applies their policies, whether they connect to an on-premises Virtual Service Edge or to a Public Service Edge anywhere in the world. Logs are transmitted to and stored on the Zscaler cloud as a central repository for integrated analytics, so you can view and monitor internet traffic activity on the dashboard and make full use of the real-time logging and interactive reporting capabilities of the service. Your organization has full access to the Virtual Service Edges for monitoring and configuration. Zscaler does not require access to the Virtual Service Edges.
Virtual Service Edges are supported on [VMware ESX/ESXi](/zia/configuring-virtual-service-edge-clusters), [Microsoft Azure](/zia/configuring-virtual-service-edge-microsoft-azure), [Amazon Web Services (AWS) EC2](/zia/configuring-virtual-service-edge-amazon-web-services), [Microsoft Hyper-V](/zia/configuring-virtual-service-edge-microsoft-hyper-v), and [Google Cloud Platform (GCP)](/zia/configuring-virtual-service-edge-google-cloud-platform).
![Diagram showing how a Virtual Service Edge forwards traffic.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/about-virtual-service-edges/About-Virtual-Service-Edge.png)
Ensure that your firewall allows the outbound connections listed on the ZIA Virtual Service Edge config page (i.e., config.zscaler.com/<Zscaler Cloud Name>/zia-v-sedge) and access to and from the IP addresses on the Zscaler Hub IP Addresses page (i.e., config.zscaler.com/<Zscaler Cloud Name>/hubs).
You can find the name of your cloud in the URL your admins use to log in to the Zscaler service. For example, if an organization logs in to admin.zscalertwo.net, then that organization's cloud name is zscalertwo.net. In this case, you should go to config.zscaler.com/zscalertwo.net/zia-v-sedge. To learn more, see [What Is My Cloud Name for ZIA?](/zia/what-my-cloud-name-zia)
[]Specifications and Sizing
Virtual Service Edge is available in a single-sized VM that supports up to 600 Mbps of total throughput. An SSL acceleration card (sold separately) is recommended for deployments requiring a throughput of 100 Mbps or more in order to perform SSL inspection on Virtual Service Edge.
Following are the Virtual Service Edge specifications and sizing:
| Virtual Service Edge |
| -------------------- |
| Hypervisor Support | VMware ESXi 6.0 and above | Microsoft Azure | AWS EC2 | Microsoft Hyper-V | GCP |
| Number of Public Service Edge Instances per VM | 1 | 1 | 1 | 1 | 1 |
| Number of Load Balancers per VM | 1 | 1 | 1 | 1 | - |
| Maximum VMs per Cluster | 16 | - | - | 16 | - |
| vMotion Support | VMware ESXi 7.0 and above | - | - | - | - |
| **Hypervisor Resource Requirements** |
| Number of V-CPUs | 4 | 4 | 4 | 4 | 4 |
| Minimum Required Memory Allocation for Standalone deployments | 32 GB | 32 GB | 32 GB | 32 GB | 32 GB |
| Minimum Required Memory Allocation for Cluster deployments | 48 GB | - | - | 48 GB | - |
| Recommended Memory Allocation | 48 GB | 48 GB | 48 GB | 48 GB | 48 GB |
| Virtual Interfaces | 3 | 3 | 3 | 3 | 3 |
| SSL Acceleration Card per VM | 1 x Marvell NITROX CNN3510-500-C5-NHB-2.0-G | - | - | - | - |
| Disk Space | 500 GB | 500 GB | 500 GB | 500 GB | 500 GB |
| **Throughput & SSL Specifications** |
| Total Throughput | 600 Mbps | - | - | - | - |
| SSL CPS with Acceleration Card | 3500 CPS | - | - | - | - |
| SSL CPS without Acceleration Card | 400 CPS | 400 CPS | 400 CPS | 400 CPS | 400 CPS |
Zscaler recommends Virtual Service Edge clusters with at least two Virtual Service Edge instances to provide n+1 redundancy for production. In the VMware ESXi and Microsoft Hyper-V environments, Zscaler recommends utilizing the in-built load balancer for Virtual Service Edges deployed in cluster mode. In certain [situations](/zia/using-external-load-balancer-virtual-service-edge-clusters), the Virtual Service Edges can be deployed with an External Load Balancer. In public cloud environments such as Microsoft Azure, AWS EC2, Microsoft Hyper-V, and GCP, the native cluster mode of deployment is not supported, and public cloud load balancers can be used to ensure redundancy between the Virtual Service Edges.
Maintenance
The Zscaler service automatically upgrades Virtual Service Edges during scheduled maintenance windows. The dates of these maintenance windows are published in the [Zscaler Trust Portal](https://trust.zscaler.com/). This does not require intervention from an admin or Zscaler Cloud Operations. In addition, the Virtual Service Edges aren't monitored or managed by the Zscaler Cloud Operations team.
Hardening
The Virtual Service Edge virtual appliance is locked down by allowing only a limited number of commands to be run on the appliance. This setup is commonly referred to as a "jailed environment". The operating system itself is hardened and all unnecessary packages and libraries are removed to minimize the attack surface.
Zscaler also hardens the TCP stack used for proxying and keeps up with any Common Vulnerabilities and Exposures (CVEs) that are disclosed. CVEs are patched immediately if they can potentially cause harm to the system. Updates and patches are also automatically downloaded and applied, so no manual updating or patching is required.
Access to the Virtual Service Edge virtual appliance is limited to the VMware console and Microsoft Azure web console view, and Hyper-V Manager console, as well as the management interface for SSH access. Access to the Virtual Service Edge can be locked down by setting up proper access control to the console and the management interface. Consider using methods such as access control lists, authentication, and authorization to achieve this.
Authentication attempts as well as an audit log of the commands run on the appliance, are accessible and stored in /var/log/auth.log. This file can be monitored remotely or checked periodically to detect unauthorized commands or authentication attempts.
About the Virtual Service Edges Page
On the Virtual Service Edges page (Administration > Virtual Service Edges), you can do the following:
- [Add a Virtual Service Edge instance](/zia/adding-virtual-service-edge-instances).
- [Download a Virtual Service Edge VM](/zia/downloading-virtual-service-edge-vm).
- [Download the SNMP MIB files](/zia/about-the-zscaler-snmp-mibs).
- [Download the Hyper-V VM](/zia/configuring-virtual-service-edge-microsoft-hyper-v#download-hyper-v).
- Search for a Virtual Service Edge.
- View a list of all Virtual Service Edges that were configured for your organization. For each Virtual Service Edge, you can see the following:
- **Name**: The name of the Virtual Service Edge. You can sort this column.
- **Status**: Displays whether the Virtual Service Edge is enabled or disabled. You can sort this column.
- **Type**: The Virtual Service Edge subscription type.
- **Deployment Status**: The Virtual Service Edge deployment status (**In Production** or **Trial**).
- **Deployment Mode**: The Virtual Service Edge deployment mode (**Cluster **or **Standalone**). You can sort this column.
- **Load Balancer IP Address**: The load balancer IP address for Virtual Service Edges in **Cluster **deployment mode. You can sort this column.
- **Proxy IP Address**: The proxy IP address for the Virtual Service Edge. You can sort this column.
- **Cluster Name**: The Virtual Service Edge cluster name. You can sort this column.
- **IPSec Local Termination**: The status of IPSec local termination for the Virtual Service Edge.
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
- [Download the Virtual Service Edge SSL certificate](/zia/downloading-virtual-service-edge-certificates).
- [Edit a Virtual Service Edge configuration](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal).
- Go to the [Virtual Service Edge Clusters](/zia/about-virtual-service-edge-clusters) page to manage and configure Virtual Service Edge clusters.
[![Screenshot highlighting the different features on the Virtual Service Edges page.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/about-virtual-service-edge/ZIA-Virtual-Service-Edges-Page.png)
](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/about-virtual-service-edge/ZIA-Virtual-Service-Edges-Page.png)