# About Internet & SaaS Virtual Service Edge Clusters
Source: https://help.zscaler.com/unified/about-internet-saas-virtual-service-edge-clusters
PDF: https://help.zscaler.com/pdf/com/en/1495641.pdf

For production environments, Internet & SaaS [Virtual Service Edge](/unified/about-virtual-service-edges) is deployed in a cluster. A cluster requires at least two Virtual Service Edges for active-active redundancy and load balancing. Each Virtual Service Edge cluster can contain a maximum of 16 Virtual Service Edge instances. Each Virtual Service Edge in a cluster requires a separate Virtual Service Edge subscription.
As shown in the diagram below, each Virtual Service Edge has a load balancer (LB) bundled in. The load balancer is specifically designed to distribute user traffic evenly across the Virtual Service Edges.
Zscaler does not recommend using external load balancers. However, if your organization must use an external load balancer, see [Using an External Load Balancer with Internet & SaaS Virtual Service Edges](/unified/using-external-load-balancer-internet-saas-virtual-service-edge-clusters).
To ensure high availability, the Zscaler load balancers use the Common Address Redundancy Protocol (CARP) for active-passive fault tolerance. As shown in the diagram, all Virtual Service Edge instances in the cluster are active, and one load balancer instance is active at a time. The active load balancer receives ingress traffic through the cluster IP address and directs the traffic to the appropriate Virtual Service Edge. If the active load balancer fails, then the passive load balancer automatically takes over, ensuring no disruption in service. Virtual Service Edges also run in Direct Server Return (DSR) mode. DSR allows the requests to go through the load balancer to the Virtual Service Edge, but the response flows from the Virtual Service Edge to the user, skipping the load balancer on the return.
[![Diagram of a Virtual Service Edge load balancing.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/about-virtual-service-edge-clusters/ZIA-Virtual-Service-Edge-Traffic.png?1602578726)
](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/about-virtual-service-edge-clusters/ZIA-Virtual-Service-Edge-Traffic.png)
For evaluation purposes with test traffic, you can configure a Virtual Service Edge in standalone mode, which does not support failover. Zscaler does not support standalone Virtual Service Edges for production environments with live user traffic.
About the Virtual Service Edge Clusters Page
On the Virtual Service Edge Clusters page (Infrastructure > Internet & SaaS > Traffic Forwarding > Virtual Service Edges > Virtual Service Edge Clusters), you can:
- [Add a Virtual Service Edge Cluster](/unified/adding-virtual-service-edge-clusters).
- View a list of all Virtual Service Edge clusters that were configured for your organization. For each Virtual Service Edge cluster, you can see the following information:
- **Name**: The name of the Virtual Service Edge cluster. You can sort this column.
- **Status**: Displays whether the Virtual Service Edge cluster is enabled or disabled. You can sort this column.
- **Virtual Service Edges**: The Virtual Service Edge instances that are included in the cluster. You can sort this column.
- **Cluster IP**: The cluster IP address. You can sort this column.
- **IPSec Local Termination**: The status of IPSec local termination for the Virtual Service Edge cluster. You can sort this column.
- Edit a Virtual Service Edge Cluster.
- [Modify the table and its columns](/unified/using-tables).
- Search for a Virtual Service Edge cluster.
- Go to the [Virtual Service Edges](/unified/about-virtual-service-edges) page to manage and configure Virtual Service Edges.
[![Screenshot highlighting the different features on the Virtual Service Edge Clusters page.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/about-virtual-service-edge-clusters/ZIA-Virtual-Service-Edge-Clusters-Page.png)
](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/about-virtual-service-edge-clusters/ZIA-Virtual-Service-Edge-Clusters-Page.png)