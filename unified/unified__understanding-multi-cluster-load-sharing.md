# Understanding Multi-Cluster Load Sharing
Source: https://help.zscaler.com/unified/understanding-multi-cluster-load-sharing
PDF: https://help.zscaler.com/pdf/com/en/1495271.pdf

The Multi-Cluster Load Sharing feature allows multiple Internet & SaaS Public Service Edge clusters in different network address blocks to participate in a Virtual IP (VIP) from any network address block in a data center. The ingress traffic will enter a given VIP and access the end destination via any instance of the Service Edge clusters from any of the network address blocks listed for the data center (DC). To view the complete list of Data Center information, go to config.zscaler.com/<Zscaler Cloud Name>/cenr.
You can find the name of your cloud in the URL your admins use to log in to the Zscaler service. For example, if an organization logs into admin.zscalertwo.net, then that organization's cloud name is zscalertwo.net. In this case, you should go to config.zscaler.com/zscalertwo.net/cenr.
All the traffic is distributed across every participating cluster load balancer (LB) instance, and they can forward traffic to any service node in any participating cluster.
![Schematic Diagram of Multi-Cluster Load Sharing](/downloads/zia/documentation-knowledgebase/traffic-forwarding/about-multi-cluster-load-sharing/Multi-Cluster%20Load%20Balancer.png?1624945091)
This feature allows Zscaler to scale its DCs without the need to migrate your clusters while using the same existing VIPs.
For example, in the following table, ZSC Cluster 1 resides in the `165.225.80.0/23` network address block, and ZSC Cluster 3 in the `147.161.166.0/23` network address block. Both these clusters can serve the GRE VIP `165.225.80.36`, allowing us to add more Service Edge capacity without impacting your GRE VIP destination. So, you no longer need to move your GRE tunnels to a new VIP when a new cluster is added to a DC.
| Cluster | VIP | Cluster Type | Network address block |
| ------- | --- | ------------ | --------------------- |
| ZSC Cluster 1 | 165.225.80.36 | GRE | 165.225.80.0/23 |
| 165.225.80.37 | VPN | 165.225.80.0/23 |
| 165.225.81.247 | PAC | 165.225.80.0/23 |
| ZSC Cluster 3 (Shared VIPs with Cluster1) | 165.225.80.36 | GRE | 147.161.166.0/23 |
| 165.225.80.37 | VPN | 147.161.166.0/23 |
| 165.225.81.247 | PAC | 147.161.166.0/23 |