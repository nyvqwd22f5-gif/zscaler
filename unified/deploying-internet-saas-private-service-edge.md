# Deploying Internet & SaaS Private Service Edge
Source: https://help.zscaler.com/unified/deploying-internet-saas-private-service-edge
PDF: https://help.zscaler.com/pdf/com/en/1495581.pdf

A Private Service Edge is part of the Zscaler cloud. It communicates with other nodes in the cloud, such as the Central Authority (CA) for user authentication and policy updates, and the cloud routers and Nanolog clusters for logging and reporting. To learn more, see [Understanding Private Service Edge](/unified/understanding-private-service-edge).
To deploy a Private Service Edge:
-
Review the following deployment methods and determine the best one for your environment:
- [Deploy Inside the DMZ](#DeployInsideDMZ)
- [Deploy Outside the Corporate Firewall](#DeployOutsideCorporateFirewall)
- [Deploy Behind the Network Firewall](#DeployInsideInternalNetwork)
For all design review questions and architecture considerations, contact your Zscaler Sales representative, who assists in choosing the appropriate Private Service Edge deployment option depending on your environment and requirements.
-
Ensure that you provide Zscaler with the necessary [network and IP address requirements](/unified/understanding-private-service-edge#network-ip-address).
Private Service Edge supports IPv6 traffic if it's only forwarded via IPSec or GRE tunnels. Contact Zscaler Support to enable and configure IPv6 for your organization.
- Upon receipt of the Private Service Edges from Zscaler, [install them](/unified/installing-private-service-edge).
-
Ensure the following for network configuration:
- If the Private Service Edges are deployed in the DMZ of your organization, inside your internal network or behind any network device that might filter or otherwise interfere with communication to and from Zscaler, all relevant network devices must be configured to allow the necessary traffic per the firewall rules posted on config.zscaler.com/<Zscaler Cloud Name>/zia-sedge.
- For the correct functioning of Direct Server Return (DSR) load balancing, enable Gratuitous ARP on the network switches directly connected to the Private Service Edges.
- The Private Service Edges and load balancers (LBs) do not support VLAN tagging. All traffic to and from the Private Service Edges and LB NIC ports must not be VLAN tagged. The switch ports connecting to the Private Service Edges or LBs should be configured as Access mode.
Contact your network equipment provider for best practices and network configuration if required.
- Zscaler Operations provisions the Private Service Edges and informs your organization after the Private Service Edges are operational. Zscaler Operations is responsible for the ongoing maintenance of the Private Service Edges. To learn more, see [Maintenance Support for Private Service Edge](/unified/maintenance-support-private-service-edge).
- Test the deployment:
- If authentication is enabled for your location, browse to an external site and verify that the Zscaler service requests your credentials before it allows access to the internet.
- Ensure that your policies are enforced. Verify that the service blocks access to a site due to policy.
- View and check the logs using the [dashboard](/unified/about-dashboards) in the Admin Portal.
- (Optional) If your organization uses PAC files to forward traffic to the Zscaler service, edit the PAC files and ensure that the variables that point to the Private Service Edges specify the subcloud that Zscaler configured for your organization. To learn more, see [Using PAC Files for Private Service Edge Deployments](/unified/using-pac-files-private-service-edge-deployments). Also, if applicable, ensure that your [firewall allows the devices from your internal network to reach the Zscaler PAC servers](/unified/firewall-configuration-requirements-private-service-edge-deployments).
-
(Optional) If your organization uses GRE tunnels to forward traffic to the Zscaler service, follow the standard procedure for [Self-Provisioning of GRE Tunnels](/unified/self-provisioning-gre-tunnels). Private Service Edge VIP addresses are available for selection on the GRE Tunnels page in the Admin Portal.
Self-provisioning of GRE tunnels towards Private Service Edge clusters is only supported for clusters deployed on public IP space (i.e., a non-NAT environment). If you need to build a GRE tunnel towards a Private Service Edge cluster deployed within a NAT environment, contact Zscaler Support or submit a Zscaler Support ticket.
[]This deployment method requires configuration changes to your firewall to allow Zscaler cloud communications. This can impact firewall performance because internet traffic is sent through the firewall to the Private Service Edge in the DMZ, and then through the firewall again to the internet. This might lead to port or session table exhaustion.
![Diagram of Service Edges in the DMZ.](/downloads/zscaler-tech-pubs-style-guide/draft-articles/deploying-service-edges/zia-service-edge-in-dmz.png)
The following requirements must be met for this deployment method:
- Configure the firewall to allow the Private Service Edges to communicate with the other nodes in the Zscaler cloud and Zscaler Operations to maintain and monitor the Private Service Edges. This deployment also requires ongoing maintenance as the Zscaler cloud expands. To learn more, see [Firewall Configuration Requirements for Private Service Edge Deployments](/unified/firewall-configuration-requirements-private-service-edge-deployments).
- Configure a backup tunnel to Private Service Edges at another data center or to Internet & SaaS Public Service Edges for redundancy.
- Requires multiple public IP addresses per Private Service Edge. To learn more, see [Network and IP Address Requirements](/unified/understanding-private-service-edge#network-ip-address).
[]Zscaler highly recommends that you send your HTTP/HTTPS traffic through a GRE or IPSec tunnel from your firewall to the Private Service Edges. The primary incentive is to group all outbound internet traffic inside a tunnel to remediate and avoid potential port or session table exhaustion on the firewall. It does not require configuration changes to your firewall to accommodate the communication requirements of the Private Service Edge.
If you use PAC files to forward your traffic to the Private Service Edges, see [Using PAC Files for Internet & SaaS Private Service Edge Deployments](/unified/using-pac-files-private-service-edge-deployments).
![Diagram of Service Edge Outside the Firewall](/downloads/zscaler-tech-pubs-style-guide/draft-articles/deploying-service-edges/zia-service-edge-outside-firewall.png?1602585288)
The following requirements must be met for this deployment method:
-
Configure GRE or IPSec VPN tunnels to the Private Service Edges.
- Send only HTTP/HTTPS traffic to the Private Service Edges. Send all other traffic directly to the internet.
- Send un-NATed traffic through the tunnels for visibility into user traffic.
To learn more, see [Understanding Generic Routing Encapsulation (GRE)](/unified/understanding-generic-routing-encapsulation-gre) and [Understanding IPSec VPNs](/unified/understanding-ipsec-vpns).
- Configure backup tunnels to Private Service Edges at another data center or to Public Service Edges for redundancy.
- Requires multiple public IP addresses per Private Service Edge. To learn more, see [Network and IP Address Requirements](/unified/understanding-private-service-edge#network-ip-address).
[]You might decide to install the Private Service Edges behind the corporate firewall. This deployment option also requires configuration changes to the firewall to allow the Zscaler nodes to communicate with each other and Zscaler cloud Operations remote access to the Private Service Edges.
![Diagram of Service Edge behind firewall](/downloads/zscaler-tech-pubs-style-guide/draft-articles/deploying-service-edges/ZIA-service-edge-behind-firewall.png)
The following requirements must be met for this deployment method:
- Configure the firewall to allow the Private Service Edges to communicate with the other nodes in the Zscaler cloud and Zscaler cloud Operations to maintain and monitor the Private Service Edges. This deployment also requires ongoing maintenance as the Zscaler cloud expands. To learn more, see [Firewall Configuration Requirements for Private Service Edge Deployments](/unified/firewall-configuration-requirements-private-service-edge-deployments).
- Configure a backup tunnel to Private Service Edges at another data center or to Public Service Edge for redundancy.
- Requires multiple public IP addresses per Private Service Edge and RFC1918 IP addresses, along with 1:1 static NAT on your organization's NAT devices, for this deployment type. To learn more, see [Network and IP Address Requirements](/unified/understanding-private-service-edge#network-ip-address).