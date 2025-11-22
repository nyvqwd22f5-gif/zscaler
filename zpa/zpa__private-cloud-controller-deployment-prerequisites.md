# Private Cloud Controller Deployment Prerequisites
Source: https://help.zscaler.com/zpa/private-cloud-controller-deployment-prerequisites
PDF: https://help.zscaler.com/pdf/com/en/1507421.pdf

Before deploying a Private Cloud Controller on any supported platform, Zscaler highly recommends reading the following information and making the necessary changes to your organization's environment, where applicable.
Each Private Cloud Controller supports between 100 to 250 Mbps of SIEM throughput. Use the information on this page to determine the Private Cloud Controller sizing requirements for your deployment. Private Cloud Controller sizing must be based on the number of users that need to be redirected and the expected SIEM throughput.
- [ZPA Private Cloud Controller Specifications and Sizing Requirements](#SpecsSizing)
- [ZPA Private Cloud Controller Platform Prerequisites](#PlatformPrereqs)
- [ZPA Private Cloud Controller Security Guidance and Firewall Requirements](#Firewall)
- [ZPA Private Cloud Controller Zscaler Client Connector Requirements](#ClientConnector)
After you have met all of the prerequisites, you can deploy the Private Cloud Controller on a supported platform.
[]The following specifications are recommended by Zscaler for up to 250 Mbps SIEM throughput based on the sizing. Refer to the following table for the sizing and relevant SIEM data throughput.
- Memory (RAM), vCPU (for virtual machines), SIEM throughput, or CPU (for physical machines) cores:
| Active Users | Memory | SIEM Throughput | vCPU or CPU Cores |
| ------------ | ------ | --------------- | ----------------- |
| Up to 2,000 | 16 GB | 100 Mbps | 4 vCPUs or 4 CPUs |
| Up to 4,000 | 32 GB | 150 Mbps | 8 vCPUs or 8 CPUs |
| Up to 10,000 | 64 GB | 250 Mbps | 16 vCPUs or 16 CPUs |
- Disk Space: 64 GB (thin provisioned) for all deployment platforms
- Network Card: 1 NIC (minimum)
Depending on your deployment use case, each Private Cloud Controller must be able to accept incoming connections from either internal or external sources or both internal and external sources on TCP port 443. For example, if you enable ZPA for both remote and office users, each Private Cloud Controller needs to accept incoming connections from both internal and external endpoints running Zscaler Client Connector.
Private Cloud Controllers are reachable over the internet for remote users in Business Continuity.
In the scenario where a Private Cloud Controller is deployed behind a firewall, the firewall performs destination network address translation (DNAT) for the Private Cloud Controller's private IP address. In this case, the flow of traffic is from Zscaler Client Connector to the Private Cloud Controller. The firewall then translates the destination public IP address that Zscaler Client Connector connects to on the private IP address of the Private Cloud Controller. The firewall advertises a public IP address on the internet. It is necessary to configure the public IP address advertised by the firewall as a publish IP of the respective Private Cloud Controller. In the case of disaster recovery, you must add this IP address as the A record for that Private Cloud Controller.
Your firewalls must be configured to let the Private Cloud Controller establish outbound connections to the IP addresses of the ZPA Public Service Edge, and establish inbound connections from App Connectors, ZPA Private Service Edges, and Zscaler Client Connectors.
The following conditions apply to each Private Cloud Controller that is placed behind a firewall:
- They must accept incoming connections from internal sources and remote users and on-premises users (as applicable and dependent on your use case) on TCP port 443.
- They must have a unique private IP address that can be reached over the internal network.
After a Private Cloud Controller is enrolled, an outbound TLS tunnel over TCP port 443 is established to the ZPA cloud infrastructure. This communication channel provides various functionality and includes the following traffic:
- Periodic keepalives to the ZPA Public Service Edge
- Tenant-specific configuration and policy download
- ZPA Private Cloud Controller software upgrades (upgrades are completed based on a weekly schedule)
You can deploy additional ZPA Private Cloud Controllers at any time, using the same provisioning key to add them to the existing Private Cloud Controller group, while ensuring network and internet connectivity. Private Cloud Controllers are designed to scale elastically. You can deploy additional Private Cloud Controllers in the same Private Cloud Controller group to increase the total throughput as required by your deployment. Zscaler recommends that you deploy Private Cloud Controllers in pairs (N+1), where N is the number of Private Cloud Controllers as per the sizing requirements. To learn more, see [About Deploying Private Cloud Controllers](/zpa/about-deploying-private-cloud-controllers) and [Private Cloud Controller Deployment Guides for Supported Platforms](/zpa/business-continuity-management/private-cloud-controller-deployment-guides-supported-platforms).
After deployment, ensure that the Private Cloud Controller meets your sizing requirements. If disk space fills up in the Private Cloud Controller, Zscaler recommends archiving files and creating more log space.
Understanding Private Cloud Controller Throughput
Throughput numbers are aggregate (i.e., total inbound and outbound). Each Private Cloud Controller supports up to 250 Mbps SIEM throughput. Private Cloud Controllers communicate over the provided (default) gateway, which is most likely your ISP WAN broadband connection.
Zscaler recommends that you check your existing VPN solution's average and peak throughput and the number of users when determining your sizing requirements. Be sure to only account for user or client VPN traffic and not any site-to-site tunnel traffic.
Private Cloud Controller sizing must be based on the number of users that need to be redirected and the expected SIEM throughput. The exact throughput can vary and depends on other network factors such as your internal network setup and latency. Make sure that you have enough Private Cloud Controllers to support the connection and room for failover (N+1).
To horizontally scale your deployment, Zscaler recommends that you have more Private Cloud Controllers with lower specifications rather than fewer Private Cloud Controllers with higher specifications. For example, if you have fewer Private Cloud Controllers with higher specifications and one fails, you could adversely affect more user application traffic or sessions than a smaller Private Cloud Controller that fails.
[]Before you begin any procedures within the [Private Cloud Controller Deployment Guide for Linux](/zpa/private-cloud-controller-deployment-guide-linux), make sure that you have all of the following prerequisites:
- Intel x86_64/AMD 64-based architecture
- systemd
- Root or sudo access to the system to configure a new package repository and install packages
- DNS resolution and network access
- A [Private Cloud Controller provisioning key](/zpa/about-private-cloud-controller-provisioning-keys) obtained from the ZPA Admin Portal
- A static MAC address
[]Private Cloud Controllers can be deployed in different ways, so the security features for each deployment type are slightly different.
Operating System Security
Some organizations choose to firewall or otherwise restrict outbound traffic to the internet from the data center. It is possible to deploy a Private Cloud Controller in such an environment as long as the Private Cloud Controller can reach all Zscaler data centers containing ZPA Public Service Edges. For firewall configuration information for your deployment, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
Firewall Requirements and Interoperability Guidelines
All of the Zscaler data centers containing Public Service Edges must be allowed. A partial firewall configuration will result in connectivity problems for end users. Zscaler’s policy is to provide a 90-day notice for activating additional IP CIDR ranges to provide organizations with sufficient opportunity for changing control policies.
Because the service enforces TLS certificate pinning for both client and server certificates, all forms of inline or man-in-the-middle TLS interception or inspection must be disabled. Private Cloud Controllers do not function if the TLS certificates presented by the ZPA Public Service Edges do not cryptographically verify against Zscaler-trusted public keys.
By design, certificate verification is not configurable to maintain the integrity of the service, so ensure that *.prod.zpath.net is in your SSL bypass list for traffic originating from the Private Cloud Controller. This is necessary to allow the Private Cloud Controller to resolve and reach ZPA Public Service Edges. Private Cloud Controller requires your firewall configuration to accept the incoming connections from the users. Also, if you need to allowlist additional Zscaler IP addresses, refer to [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa) It might be possible to allowlist based on Zscaler cloud hostnames instead of IP addresses.
[]Private Cloud Controllers require that the [Zscaler Client Connector](/z-app) is at least on version 4.6 or later for Windows.