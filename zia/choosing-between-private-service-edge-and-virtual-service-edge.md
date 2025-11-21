# Choosing Between Private Service Edges and Virtual Service Edges
Source: https://help.zscaler.com/zia/choosing-between-private-service-edge-and-virtual-service-edge
PDF: https://help.zscaler.com/pdf/com/en/1401146.pdf

Zscaler can extend its patented cloud architecture to an organization's premise by providing ZIA Private Service Edge and Virtual Service Edge. These platforms are part of the Zscaler cloud and perform the same service as the [ZIA Public Service Edge](/zia/about-zscaler-enforcement-nodes).
You can deploy Private Service Edges and Virtual Service Edges in locations that meet the following technical requirements:
- Locations with certain geopolitical requirements and regulations
- Locations that experience high latency when connecting to Public Service Edges
- Applications that require an organization's IP address as the source IP address
- Users who need to see localized content
Although they both provide the full benefits of the Zscaler cloud, there are still some differences between the two systems. The following table provides a high-level overview of the benefits and requirements for Private Service Edges and Virtual Service Edges. For more information on the right choice for your deployment, contact your Zscaler Account team.
[](/zia/understanding-private-service-edge)[](/zia/about-virtual-service-edge)
-
-
-
-
-
-
- [](/zia/forwarding-traffic-virtual-service-edges#traffic-from-home-user)
-
-
-
-
-
-
-
- [](/zia/maintenance-support-service-edge-pzens)
-
-
-
- [](https://www.marvell.com/documents/zp00wx3p3215m8sbzykb/)
-
| **Private Service Edges** | **Virtual Service Edges** |
| ------------------------- | ------------------------- |
| Private Service Edges are devices installed in your organization's data center. They function as a full-featured Public Service Edge dedicated to your organization's traffic. To learn more, see Understanding Private Service Edge. | Virtual Service Edges use a virtual machine (VM) to function as a full-featured Public Service Edge dedicated to your organization's traffic. To learn more, see About Virtual Service Edge. |
| **Benefits**Full benefits of the Zscaler cloud.Good choice for high throughput, especially when the overall uplink throughput traffic is above 1 Gbps.Supports remote user traffic.Have the inbuilt ability to perform SSL inspection. | **Benefits**Full benefits of the Zscaler cloud.Easy to deploy.Can handle remote user traffic. To learn more, see Traffic from Home Users.Flexible deployment in the DMZ, your internal network, or in the public cloud.Virtual form factor that is horizontally scalable.Instantly available, with no need to wait for shipping.No need to use or purchase public IPs.Built-in load balancer. |
| **Requirements**Need at least two Private Service Edges for redundancy.Need to install and maintain the devices in your data centers.Cloud Operations configures, maintains, and monitors the Private Service Edge. To learn more, see Maintenance Support for Private Service Edge.Zscaler provides hardware and software for Private Service Edge. | **Requirements**Must be deployed either in clusters or standalone for production.You are responsible for the deployment, configuration, and maintenance. However, upgrades are automatic.An SSL acceleration card is recommended for deployments requiring a throughput of 100 Mbps or more in order to perform SSL inspection on Virtual Service Edges. To learn more, see NITROX® XL CNN35XX Security Adapter Family.You provide the hardware and hypervisor, while Zscaler provides the Zscaler host software that runs on the VMs. |