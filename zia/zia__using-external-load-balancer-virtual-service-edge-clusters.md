# Using an External Load Balancer for Virtual Service Edge Clusters
Source: https://help.zscaler.com/zia/using-external-load-balancer-virtual-service-edge-clusters
PDF: https://help.zscaler.com/pdf/com/en/1420291.pdf

Zscaler recommends deploying ZIA Virtual Service Edges in cluster mode with a minimum of two Virtual Service Edges to ensure redundancy. The virtual machine (VM) images include a load balancer (LB) along with the Virtual Service Edge. Zscaler recommends using the built-in LB. The benefits of using the Zscaler built-in LB are:
- Distributing the traffic to Virtual Service Edges on a per-session basis.
- Monitoring the health of the Virtual Service Edges and pruning those that fail health checks, automatically adding them to the LB when they report good health.
- Updating Virtual Service Edges in a cluster consecutively, resulting in zero downtime during updates.
Using the built-in LB requires enabling Promiscuous mode on the virtualization platform.
Promiscuous mode can instead be restricted to a dedicated port group, which contains just the Zscaler VMs.
If your organization's compliance requirements do not allow you to make the required changes to the virtual switches to use the built-in LB, an external LB can be used instead. There are two options for configuring Virtual Service Edges to use an external LB:
- [Clustered Virtual Service Edges Without the Required Switches (Recommended)](#Clustered-VSE)
- [Standalone Virtual Service Edges](#Standalone-VSE)
Monitoring
Zscaler recommends using one of the following methods to monitor Virtual Service Edges using an external LB:
- ICMP ping to the service IP. This will ensure services are up and running
- TCP portcheck to the proxy ports
- HTTP probes to an external hosted web server via proxy can also be used. This method will need a suitable policy on the Virtual Service Edge to allow the probes.
[]You can configure Virtual Service Edges in cluster mode without enabling the required switches. In this mode, because the Virtual Service Edges cannot talk to each other, each one assumes that it is the only member of the cluster and becomes the primary member of the cluster. As a result, all Virtual Service Edges in the cluster declare themselves as primary members of the cluster and own the cluster IP.
To configure an external LB for clustered Virtual Service Edges:
- Configure your external LB to forward traffic directly to the Virtual Service Edge IP (not the cluster IP).
- Set the load balancing method to per session basis.
- (Optional) Enable Client IP based persistence.
- Configure the external LB to use one of the monitoring methods listed in the Monitoring section of this article.
Monitor the Virtual Service Edge IP address (not the cluster IP).
Updates
Though all members of the cluster declare themselves as primary members of the cluster, from the cloud point of view, they are considered individual members of the same cluster. Therefore, updates occur to the Virtual Service Edges consecutively, resulting in zero downtime when the cluster is updated. Updates can also be scheduled at your convenience. To learn more, see [Configuring Virtual Service Edge Clusters](/zia/configuring-virtual-service-edge-clusters#Scheduling-Virtual-Service-Edge-Cluster-Updates).
[]You can deploy the Virtual Service Edges in standalone mode and use an external LB to distribute the load.
To configure an external LB for standalone Virtual Service Edges:
- Set the load balancing method to per session basis.
- (Optional) Enable Client IP based persistence.
- Configure the external LB to use one of the monitoring methods listed in the Monitoring section of this article.
Updates
Updates for Virtual Service Edges in standalone mode using an external LB should be scheduled to avoid downtime. To learn more, see [Configuring Virtual Service Edge Clusters](/zia/configuring-virtual-service-edge-clusters#Scheduling-Virtual-Service-Edge-Cluster-Updates).