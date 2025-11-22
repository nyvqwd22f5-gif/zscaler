# GRE Deployment Scenarios
Source: https://help.zscaler.com/zia/gre-deployment-scenarios
PDF: https://help.zscaler.com/pdf/com/en/1399116.pdf

Zscaler recommends that organizations use a combination of GRE tunneling, [PAC files](/zia/what-pac-file), [Surrogate IP](/zia/what-surrogate-ip), and [Zscaler Client Connector](/z-app/what-zscaler-app) to forward traffic to the Zscaler service. This article describes the most common GRE tunnel deployments.
GRE Tunnels from the Internal Router to the ZIA Public Service Edges
Zscaler recommends that you configure two GRE tunnels from an internal router behind the firewall to the ZIA Public Service Edges: a primary tunnel from the router to a ZIA Public Service Edge in one data center and a secondary tunnel from the router to a ZIA Public Service Edge in another data center. This type of deployment provides visibility into the internal IP addresses, which can be used for the Zscaler security policies and logging.
In this deployment, the GRE tunnel source IP address is a public IP address that is configured on the loopback interface of the router. On the firewall, you'll need to define a rule that allows GRE traffic from the router. Additionally, if your organization has redundant routers or ISPs, or both as shown in the following diagram, you can configure the routers, so failover to a redundant ISP is automatic.
![Diagram of GRE tunnels configured from internal routers to ZIA Public Service Edges](/downloads/zia/traffic-forwarding/gre/gre-deployment-scenarios/GRE_Internal_Router.png)
GRE Tunnels from the Border Router to the ZIA Public Service Edges
If configuring GRE tunnels from an internal router to the ZIA Public Service Edges is not feasible, then you can configure a GRE tunnel from your border router to the ZIA Public Service Edges. In this type of deployment, you need to configure the border router to send internet-bound traffic to the ZIA Public Service Edges. You also need to disable NAT on your firewall to provide internal IP address visibility to the ZIA Public Service Edges.
![Diagram of GRE tunnel configured from border router to ZIA Public Service Edges](/downloads/zia/traffic-forwarding/gre/gre-deployment-scenarios/GRE_Border_Router.png)
**GRE Tunnels in Explicit Proxy Mode**
To configure GRE tunnels with the explicit proxy mode in no default route environment, use the following set of global Public Service Edge IP addresses:
- 185.46.212.88
- 185.46.212.89
- 185.46.212.90
- 185.46.212.91
- 185.46.212.92
- 185.46.212.93
- 185.46.212.97
- 185.46.212.98
To learn more, see [About Global Public Service Edges](/zia/about-global-zscaler-enforcement-nodes).