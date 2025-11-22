# App Connector Deployment Prerequisites
Source: https://help.zscaler.com/unified/app-connector-deployment-prerequisites
PDF: https://help.zscaler.com/pdf/com/en/1496101.pdf

Before deploying an App Connector on any supported platform, Zscaler highly recommends reading the following information and making the necessary changes to your organization's environment, where applicable.
- [App Connector Specifications and Sizing Requirements](#SpecsAndSizing)
- [App Connector Platform Prerequisites](#PlatformPrereqs)
- [App Connector Security Guidance and Firewall Requirements](#SecurityAndFirewallReqs)
After you have met all of the prerequisites, you can deploy the App Connector on a supported platform.
[]The following specifications are recommended by Zscaler for each App Connector:
- Memory: 4 GB RAM
For Digital Experience Monitoring deployments, Zscaler recommends App Connectors to have 8 GB of RAM.
- CPU:
- 2 CPU cores (Xeon E5 class) for physical machines without hyperthreading
- 4 CPU cores (Xeon E5 class) for virtual machines (VMs) with hyperthreading
- Both Amazon Web Services (AWS) and Google Cloud Platform (GCP) require a minimum of 4 CPU cores due to hyperthreading
- To deploy an App Connector on AWS, Zscaler recommends using t3.xlarge (for non-production or low traffic App Connectors) or m5a.xlarge (for production or high traffic App Connectors)
- To deploy an App Connector on GCP, Zscaler recommends using a Linux RPM on n1-standard-4 or n1-highcpu-4
- Azure VMs older than V3 require 2 CPU cores, while VMs V3 and higher require 4 CPU cores due to hyperthreading
- To deploy an App Connector on Azure, Zscaler recommends using Standard_F4s_v2 or Standard_D4s_v3
For Digital Experience Monitoring deployments, Zscaler recommends App Connectors to have 4 CPU cores.
For Privileged Remote Access connections, Zscaler recommends adjustments to the CPU cores and RAM on your App Connectors. To learn more, contact Zscaler Support.
Privileged Remote Access is only supported on App Connectors running CentOS 7.8 and later.
Using the [PassMark Software Pty Ltd](https://www.cpubenchmark.net/cpu_list.php) benchmark to verify the CPU Mark score, Zscaler recommends using a minimum CPU benchmark score of 2640 when choosing a CPU processor. The Intel Advanced Encryption Standard New Instructions (AES-NI) instruction set must also be enabled on the CPU processor.
To learn more, see the [App Connector Deployment Guide](/unified/networking/private-applications/app-connector-management/app-connector-deployment-guides-supported-platforms) for your platform.
- Disk Space: 64 GB (thin provisioned) for all deployment platforms
- Network Card: 1 NIC (minimum)
For VMware platform deployment, the default configuration to allow the host to dynamically allocate VM resources is not recommended. Configure the VM setting to reserve the following memory and CPU allocations:
- Memory: 8 GB RAM
- CPU: total CPU GHz (the number of cores (2 or 4 cores) multiplied by the GHz per core)
To learn more, see [VMware Resource Allocation Reservation](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.resmgmt.doc/GUID-8B88D3D8-E9D9-4C05-A065-B3DE1FFFB401.html).
Using these specifications, each App Connector supports up to 500 Mbps of throughput. To learn more, see [Understanding App Connector Throughput](/unified/app-connector-deployment-prerequisites#ConnectorThroughput) in this article. Based on Zscaler's recommendations, determine the App Connector sizing requirements for your deployment. If disk space fills up in the App Connector, Zscaler recommends archiving files and creating more log space. To learn more, see [Monitoring App Connector Performance](/unified/monitoring-app-connector-performance#diskspace_archive).
After an App Connector is enrolled, an outbound TLS tunnel over port 443 is established to the cloud infrastructure. This communication channel provides various functionality and utilizes minimal bandwidth, which includes the following traffic:
- Periodic keepalives to Public Service Edges or Private Service Edges
- Application learning
- Application health reporting
- App Connector software upgrades (upgrades are completed based on a weekly schedule)
You can deploy additional App Connectors at any time, using the same provisioning key to add them to the [existing App Connector Group](/unified/about-app-connector-groups), while ensuring network and internet connectivity. App Connectors are designed to scale elastically. You can deploy additional App Connectors, in the same App Connector Group, to increase the total throughput as required by your deployment. Zscaler recommends you have a minimum of two healthy App Connectors to always ensure an available path. To learn more, see [About Deploying App Connectors](/unified/about-deploying-app-connectors) and [Supported Platforms for App Connectors](/unified/networking/private-applications/app-connector-management/app-connector-deployment-guides-supported-platforms).
After deployment, ensure that the App Connector meets your sizing requirements. To learn more, see [Verify App Connector Sizing Requirements](/unified/managing-deployed-app-connectors#VerifySizing).
[]Understanding App Connector Throughput
Throughput numbers are aggregate (i.e., total inbound and outbound). The following best practices apply regarding App Connector throughput sizing:
- Check your existing VPN solution's average and peak throughput. Be sure to only account for user/client VPN traffic and not any site-to-site tunnel traffic.
- App Connectors communicate over the provided (default) gateway, which is most likely your ISP WAN broadband connection.
- Using double encryption affects throughput. However, the effect varies based on the number of applications that are enabled for double encryption.
So, if you have a 1 Gbps connection (aggregate) in your data center, you can use the throughput guidelines in the table to make sure that you have enough App Connectors to support the connection and room for failover (N+1). For example, with a 1 Gbps connection, you would need to deploy 2 to 3 App Connectors if your applications are not using double encryption, but 4 to 6 App Connectors if they are. To learn more, see [About Double Encryption](/unified/about-double-encryption).
The following throughput guidelines apply based upon the recommended App Connector specifications:
| % of Applications with Double Encryption | Per App Connector Throughput |
| ---------------------------------------- | ---------------------------- |
| 0% | 500 Mbps |
| 25% | 437.5 Mbps |
| 50% | 375 Mbps |
| 75% | 312.5 Mbps |
| 100% | 250 Mbps |
It is possible to increase App Connector throughput up to 1 Gbps per App Connector by running the App Connector on hardware with more memory and CPUs along with increased network link speed. If you have a 10 Gbps connection (aggregate) in your data center, and you want to increase the App Connector throughput up to 1 Gbps per App Connector, you can increase the underlying VM spec as follows:
- 8 vCPU cores for virtual machines or 4 CPU cores for physical machines
- 8 GB RAM
The exact throughput can vary and depends on other network factors such as your internal network setup, latency, and whether you have double encryption, App Protection, and/or Digital Experience Monitoring enabled. Make sure that you have enough App Connectors to support the connection and room for failover (N+1).
Zscaler recommends that you have more App Connectors with lower specifications rather than fewer App Connectors with higher specifications in order to horizontally scale your deployment. For example, if you have fewer App Connectors with higher specifications and one fails, you could adversely affect more user application traffic/sessions than a smaller App Connector that fails.
[]Before you begin any procedures within the [App Connector Deployment Guide](/unified/networking/private-applications/app-connector-management/app-connector-deployment-guides-supported-platforms) for your platform, make sure that you have met all of the following prerequisites:
-
Intel x86_64/AMD64 based architecture
-
systemd
-
Root or sudo access to the system in order to configure a new package repository and install packages
-
DNS resolution and network access
-
An App Connector [provisioning key](/unified/about-app-connector-provisioning-keys) obtained from the Admin Portal
-
A static MAC address
[][App Connector]s can be deployed in different ways (as private cloud VMs, public cloud VMs, or OS packages), so the security features for each deployment type are slightly different.
Zscaler recommends treating access to App Connectors as privileged, so only authorized personnel can access an App Connector's console. By limiting access, there is the added benefit of shielding inter-process communication within the App Connector from attack.
Operating System Security
The App Connector VMs distributed by Zscaler for use in private clouds are configured without any remotely accessible services running. Swap partitions are disabled on the App Connector VMs to ensure that memory growths do not have an impact on App Connector performance. For enhanced security, you must use the `passwd` command to change the credentials on the default admin account. To learn more, see the [App Connector Deployment Guide](/unified/networking/private-applications/app-connector-management/app-connector-deployment-guides-supported-platforms) for the platform you're using.
Both the private and public cloud VM images provided by Zscaler are configured with minimal listening services to reduce the remotely exploitable attack surface. Because these are essentially unmodified operating systems (currently based on CentOS 7.x), you can patch these systems when necessary by using the standard yum OS update mechanism. To learn more, see [Update App Connector System Software](/unified/managing-deployed-app-connectors#Updating).
Due to the fact that vulnerabilities are regularly found in core open-source components such as DNS resolvers and the Linux Kernel, Zscaler recommends either patching or using new Zscaler-distributed VM images on a regular basis, or protecting App Connectors using firewall policies. Additionally, if you've installed the App Connector as a package, Zscaler recommends that you take similar precautions.
Some organizations choose to firewall or otherwise restrict outbound traffic to the internet from the data center. It is possible to deploy an App Connector in such an environment as long as the App Connector is able to reach all Zscaler data centers containing Public Service Edges. For firewall configuration information for your deployment, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud).
Firewall Requirements and Interoperability Guidelines
All of the Zscaler data centers containing Public Service Edges must be allowed. A partial firewall configuration can result in connectivity problems for end users. Zscaler’s policy is to provide a 90-day notice for activating additional IP CIDR ranges, in order to provide organizations with sufficient opportunity for changing control policies.
Because the service enforces TLS certificate pinning for both client and server certificates, all forms of inline or man-in-the-middle TLS interception or inspection must be disabled. App Connectors do not function if the TLS certificates presented by the Public Service Edges or Private Service Edges do not cryptographically verify against Zscaler-trusted public keys.
By design, certificate verification is not configurable in order to maintain the integrity of the service. So ensure that *.prod.zpath.net is in your SSL bypass list for traffic originating from the App Connector. This is necessary for allowing the App Connector to resolve and reach Public Service Edges or Private Service Edges. If you need to allowlist additional Zscaler IP addresses, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud).
For Private Application integration with Digital Experience Monitoring, App Connector firewall requirements must align with the respective Digital Experience Monitoring configuration. You must configure the firewall to allow egress traffic on the TCP, UDP, and ICMP protocols. App Connectors must be able to egress traffic to port 443 for Zscaler Service Edge connections and the ports of all configured applications (i.e., ports that are configured in all application segments that are registered on the App Connector).