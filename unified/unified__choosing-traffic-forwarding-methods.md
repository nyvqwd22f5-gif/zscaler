# Choosing Traffic Forwarding Methods
Source: https://help.zscaler.com/unified/choosing-traffic-forwarding-methods
PDF: https://help.zscaler.com/pdf/com/en/1495001.pdf

Zscaler supports the following traffic forwarding mechanisms. Depending on your environment and requirements, you can choose one or a combination of the following traffic forwarding methods. Zscaler recommends that you use a combination of tunneling, PAC files, Zscaler Cloud Connector, and Zscaler Client Connector to forward traffic to the Zscaler service. To learn more, see [Best Practices for Traffic Forwarding](/unified/best-practices-traffic-forwarding).
- [Zscaler Client Connector](#zscaler-client-connector)
- [GRE Tunnels](#gre)
- [IPSec Tunnels](#ipsec)
- [PAC Files](#pac)
- [Proxy Chaining](#proxy)
- [Zscaler Cloud Connector](#zscaler-cloud-connector)
[]Zscaler recommends that you install Zscaler Client Connector on your users' devices to protect their web traffic when they are accessing the internet from an unknown location (i.e., remote user).
With Zscaler Client Connector's internet security feature, you can protect your users' web traffic even when they are outside your corporate network. The app forwards user traffic to the Zscaler service and ensures that your organization's security and access policies are enforced wherever they might be accessing the internet from. The app automatically detects when the user is no longer within the secure network, then automatically creates a connection to the Zscaler service from an unknown location.
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
| Benefits | Limitations |
| -------- | ----------- |
| Supports Windows, macOS, Linux, iOS, Android, and virtual computing environments. Supports all authentication mechanisms supported by the Zscaler service.Provides device fingerprinting and reporting.Easy to enforce.Supports auto and managed updates.Detects trusted networks and can disable its service automatically.Zscaler Client Connector forwards traffic for all ports and protocols to the Zscaler service for inspection from any location and ensures that your configured security and access policies are always enforced.Zscaler Client Connector can be configured to prevent your users from disabling, bypassing, or uninstalling it.When traffic is forwarded to the Zscaler service, Zscaler provisions your organization's IP addresses, which can then be added as known locations in the Admin Portal.You can deploy SSL inspection for Zscaler Client Connector users. | Location-based policies do not apply to the Zscaler Client Connector users.Features such as Sub-locations, Surrogate IP, and Bandwidth Control cannot be enabled for your organization.A software application needs to be deployed, managed, and maintained on all end devices. |
| **Requirements** |
| The Zscaler Client Connector users must be provisioned on the Zscaler service and an authentication method must be configured for them to authenticate.If you are using the app for Private Applications, your organization must use SAML authentication.If you are using the app for internet security, your firewall must be configured to allow the necessary connections. |
[]A GRE tunnel can be used for forwarding internet-bound traffic from your corporate network to the Zscaler service. If your organization has an internal router or switch that supports GRE and its egress port has a static address, you can configure a GRE tunnel. To learn more, see [Understanding Generic Routing Encapsulation (GRE)](/unified/understanding-generic-routing-encapsulation-gre). Zscaler recommends that you configure two GRE tunnels from an internal router behind the firewall to the Internet & SaaS Public Service Edges: a primary tunnel to an Internet & SaaS Public Service Edge in one data center and a secondary tunnel to an Internet & SaaS Public Service Edge in another data center. These deployments provide visibility into internal IP addresses, which can be used for security policies and logging.
-
-
-
-
-
-
-
- [](/unified/about-surrogate-ip)
-
-
-
-
-
-
-
-
-
[](/unified/configuring-gre-tunnels)
| Benefits | Limitations |
| -------- | ----------- |
| Supports all ports and protocols for traffic forwarding.Supports failover in case primary Internet & SaaS Public Service Edge becomes unavailable.Minimal overhead.No configuration on computers or laptops.Users on your corporate network (known location) cannot bypass the service.You can leverage all of the features of the Zscaler platform when the users' traffic is forwarded from known locations.Tunneling can provide internal IP address information to Zscaler for use in policy design and logging. | Because the Zscaler service is not able to perform user-to-IP mapping without Surrogate IP, users need to re-authenticate every time they use a new user agent, such as a new browser. To learn more, see About Surrogate IP.Not all applications support PAC files, therefore not all traffic is secured by Zscaler.There is no protection for remote users outside of the office because that traffic cannot be forwarded to the Zscaler service.Managing applications that need to be excluded from the Zscaler service becomes difficult without PAC files. |
| **Bandwidth** |
| Zscaler supports a maximum bandwidth of 1 Gbps for each GRE tunnel if its internal IP addresses are not behind NAT.If the internal subnet is behind source NAT, Zscaler can only support up to 250 Mbps of traffic for each GRE tunnel. The restriction also applies when performing source NAT with source PAT.If your organization wants to forward more than 1 Gbps of traffic, Zscaler recommends configuring more GRE tunnels with different public source IP addresses.For example, if your organization forwards 2 Gbps of traffic, you can configure two primary GRE tunnels and two backup GRE tunnels. If your organization forwards 3 Gbps of traffic, you can configure three primary GRE tunnels and three backup GRE tunnels. |
| **Requirements** |
| Your organization’s perimeter edge router must support GRE and its egress port must have a static IP address.Make sure that you have the appropriate software and hardware required to build, monitor, and failover the tunnels. |
| To learn more about setting up GRE tunnels, see Configuring GRE Tunnels. |
[]IPSec is a suite of protocols that provide network-layer security to a Virtual Private Network (VPN). If your router does not support GRE or if you use dynamic IP addresses, you can configure IPSec VPN tunnels. To learn more, see [Understanding IPSec VPNs](/unified/understanding-ipsec-vpns). Zscaler recommends that you configure two IPSec tunnels from an internal router behind the firewall to the Internet & SaaS Public Service Edges: a primary tunnel to an Internet & SaaS Public Service Edge in one data center and a secondary tunnel to an Internet & SaaS Public Service Edge in another data center. These deployments provide visibility into internal IP addresses, which can be used for security policies and logging.
-
-
-
-
-
-
-
-
- [](/unified/about-surrogate-ip)
-
-
-
-
-
-
-
-
-
[](/unified/configuring-ipsec-vpn-tunnel)
| Benefits | Limitations |
| -------- | ----------- |
| Supports all ports and protocols for traffic forwarding.Supports failover if primary Internet & SaaS Public Service Edge becomes unavailable.No configuration on computers or laptops.Users on your corporate network (known location) cannot bypass the service.You can leverage all of the features of the Zscaler platform when the users' traffic is forwarded from known locations.Tunneling can provide internal IP address information to Zscaler for use in policy design and logging.Supports locations with dynamic IP addresses. | Compared to GRE tunnels, IPSec tunnels have additional processing overhead on your equipment.Because the Zscaler service is not able to perform user-to-IP mapping without Surrogate IP, users need to re-authenticate every time they use a new user agent, such as a new browser. To learn more, see About Surrogate IP.Not all applications support PAC files, therefore not all traffic is secured by Zscaler.There is no protection for remote users outside of the office because that traffic cannot be forwarded to the Zscaler service.Managing applications that need to be excluded from the Zscaler service becomes difficult without PAC files. |
| **Bandwidth** |
| Zscaler IPSec tunnels support a limit of 400 Mbps for each public source IP address.If your organization wants to forward more than 400 Mbps of traffic, Zscaler recommends using one of the following configurations:Configure multiple IPSec tunnels with different public source IP addresses.Configure multiple IPSec VPN tunnels with the same public source IP address using NAT-T and source port randomization with IKEv2.For example, if your organization forwards 800 Mbps of traffic, you can configure two primary VPN tunnels and two backup VPN tunnels. |
| **Requirements** |
| Make sure that you have the appropriate software and hardware required to build, monitor, and failover the tunnels.Ensure that your vendor provides a VPN failover mechanism to provide resilience. |
| To learn more about setting up IPSec VPN tunnels, see Configuring IPSec VPN Tunnels. |
[]A PAC file is a text file that directs the browser to forward traffic to an Internet & SaaS Public Service Edge. To learn more about PAC files, see [Understanding PAC Files](/unified/understanding-pac-files). You can install a PAC file for each of your users to ensure coverage outside the corporate network. If certain applications need to be excluded from the Zscaler service, it is easy to write an exclude statement in your PAC file to send traffic directly. Using PAC files allows you to set exceptions for forwarding your traffic, such as excluding intranet corporate sites from the Zscaler service.
-
-
-
-
-
-
-
-
-
-
-
- [](/unified/about-surrogate-ip)
[](#gre)[](#ipsec)
-
-
[](/unified/networking/internet-saas/traffic-forwarding/pac-files/using-pac-files)
| Benefits | Limitations |
| -------- | ----------- |
| All major browsers support PAC files.Users on and off the corporate network are protected by the service.Microsoft Internet Explorer PAC settings can be enforced organization-wide using Microsoft Active Directory Group Policies (GPO).You can create locations if traffic is coming from a static public IP address.If your router can use XFF headers and it is enabled on your location, you can leverage the Surrogate IP feature. | You are not able to leverage some of the features of the Zscaler platform, such as Bandwidth Control and Firewall, because you need tunneling to use them.Not all applications support PAC files, therefore not all traffic is secured by Zscaler.End users can bypass the Zscaler service by disabling PAC files.Unless XFF headers are inserted, Zscaler loses internal IP address visibility, and customers are not able to leverage the sub-location feature.SLAs and performance can be impacted if you don't implement GRE or IPSec tunnels.The service can apply group and user policies, but not sub-location policies.Because the Zscaler service is not able to perform user-to-IP mapping without Surrogate IP, users need to re-authenticate every time they use a new user agent, such as a new browser. To learn more, see About Surrogate IP. |
| **Bandwidth** |
| When PAC file-based traffic is forwarded through a GRE or IPSec tunnel, the throughput restriction of the tunnel applies. |
| **Requirements** |
| Ensure that users do not have admin rights so they cannot circumvent the service by installing a nonstandard browser.Users can have local admin rights, but require network admin rights to change the PAC file. |
| To learn more about configuring PAC files, see Using PAC Files. |
[]Proxy chaining involves forwarding traffic from one proxy server to another. It's a quick and easy way to forward traffic to the Zscaler service from an existing on-premises proxy. Though Zscaler supports proxy chaining, it is not recommended as a long-term solution in production environments. If you use proxy chaining, SLAs can be affected.
-
-
-
-
-
-
-
-
-
[](/unified/configuring-proxy-chaining)
| Benefits | Limitations |
| -------- | ----------- |
| Easy to set up.Multiple rules offer full redundancy.Supported by every major web proxy.Users on your corporate network cannot bypass the service.If available, ‘X-Forwarded-For’ headers can be used to provide internal IP addresses to Zscaler. | Users of the corporate network must use another method, such as PAC files, to forward traffic to the service.The latency of the proxy server affects the traffic forwarding latency.If the proxy server also performs caching, downstream authentication could be an issue.If the local proxy has a cache, it could affect policy enforcement and reporting. |
| **Requirements** |
| Ensure that your organization is provisioned and the IP address of your endpoint is sent to Zscaler Support, or to your Zscaler representative if you are evaluating the service. |
| To learn how to configure proxy chaining, see Configuring Proxy Chaining. |
[]Zscaler Cloud Connector works similarly to Zscaler Client Connector, using software-defined networking (SDN) principles. It relies on a unified Zero Trust Architecture for connectivity, security, and access to the Zscaler cloud. It works by establishing zero trust access for server-to-server traffic, east-west traffic in a public cloud, IT/OT networks, and data centers. Cloud Connector simplifies traffic forwarding to the Zscaler service by securing server access to the internet and providing highly secure and simplified access to the Zscaler cloud. Using Cloud Connector, you can forward specific web traffic or application traffic through the Zscaler cloud.
-
-
-
-
-
-
-
-
-
-
-
| Benefits | Limitations |
| -------- | ----------- |
| Supports platforms such as AWS and Azure.Secures all inbound and outbound traffic to the internet.Easy to deploy.Deploy SSL inspection, Intrusion Prevention System, Firewall, and Data Loss Prevention for Cloud Connector.Provides seamless connectivity from public cloud applications to the internet.Ensures better end-user experience and application performance by peering into relationships with SaaS providers (e.g., Microsoft Office 365, Amazon Web Services, and Microsoft Azure). | You are not able to configure location-based policies.Your organization is not able to leverage some features, such as sub-locations. |
| **Requirements** |
| The Cloud Connector users must be provisioned on the Zscaler service for them to authenticate.If you are using Private Applications, ensure that your organization’s DNS traffic must go through Cloud Connector.Cloud Connector is currently supported for AWS and Azure platforms. |