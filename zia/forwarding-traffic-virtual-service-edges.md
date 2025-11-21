# Forwarding Traffic to Virtual Service Edges
Source: https://help.zscaler.com/zia/forwarding-traffic-virtual-service-edges
PDF: https://help.zscaler.com/pdf/com/en/1401276.pdf

ZIA Virtual Service Edges are hosted within an organization's premises. Zscaler recommends that you deploy Virtual Service Edges behind your firewall, though you can deploy them in the DMZ as well. The following sections describe the different ways that your organization can forward traffic to a Virtual Service Edge cluster.
Virtual Service Edges support IPv6 traffic if it's only forwarded via GRE tunnels. Contact Zscaler Support to enable and configure IPv6 for your organization.
GRE Tunnels
Zscaler recommends that you configure a [GRE tunnel](/zia/configuring-gre-tunnels) from your internal router to the Virtual Service Edge cluster IP address. Because you are using internal IP addresses for the tunnel, you don't need to contact Zscaler to register the tunnel IP addresses. Though a Virtual Service Edge cluster provides failover and redundancy, you can also configure backup GRE tunnels between the internal router and ZIA Public Service Edges.
GRE tunnels configured on Virtual Service Edges are dynamically established with no internal IP addresses, similar to unnumbered GRE tunnels. This requires Virtual Service Edges to be configured as locations. Zscaler uses any internal IP address configured on the router side of GRE tunnels for routing purposes only. Proxy settings or ICMP ping on these internal ranges is not supported. You must use GRE keepalives and ICMP pings to the Virtual Service Edge Virtual IP (VIP) for tunnel monitoring.
![Diagram of GRE tunnels and Virtual Service Edge traffic flow](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/forwarding-traffic-virtual-service-edges/zia-vse-gre-diagram.png)
PAC Files
You can configure your users' devices to use a PAC file to forward their traffic to the internal Virtual Service Edge. You can edit the Zscaler default PAC file and add the Virtual Service Edge Cluster IP address as the proxy, for example:
return "PROXY 10.84.0.188:80; DIRECT";
You can configure a failover to the Public Service Edge too, as shown in the following example:
Return "PROXY 10.84.0.188:80; PROXY ${GATEWAY}:80; PROXY ${SECONDARY_GATEWAY}:80;DIRECT";
If you want a user to browse through the Virtual Service Edge while in the office and automatically switch over to a Public Service Edge when the user is out of the office, add the variable `${SRCIP}` to direct the browser to send traffic to the Virtual Service Edge. The following is a sample argument:
var egressip = "${SRCIP}";
if (shExpMatch(egressip,"203.0.113.10")) {
/* User is in the office */
return "PROXY 10.84.0.188:80;DIRECT";
}
L2 Redirect
If your router or switch is in the same subnet as the Virtual Service Edge cluster IP address, then you can configure your router or switch to use L2 forwarding to redirect packets to the Virtual Service Edge.
Cisco Web Cache Communication Protocol (WCCP) configurations don't work with Virtual Service Edges.
![Diagram of L2 Redirect and Virtual Service Edge traffic flow](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/forwarding-traffic-virtual-service-edges/zia-vse-l2-redirect-diagram.png)
To learn more, see [Configuring Virtual Service Edge Clusters](/zia/configuring-virtual-service-edge-clusters).
[]Traffic from Home Users
A location for Virtual Service Edge is created to allow home users to utilize Virtual Service Edges. However, this could lead to a Denial of Service (DoS) attack. To mitigate the risk of a DoS attack and avoid unauthorized access to the Virtual Service Edge, you can configure parameters on the Virtual Service Edge so that only the users' Zscaler Client Connector and GRE tunnel traffic are processed.
Virtual Service Edges supports traffic forwarding only by GRE or Z-Tunnels method if this configuration is made.
Ensure that your firewall allows the outbound connections listed on the ZIA Virtual Service Edge config page (i.e., config.zscaler.com/<Zscaler Cloud Name>/zia-v-sedge) and access to and from the IP addresses on the Zscaler Hub IP Addresses page (i.e., config.zscaler.com/<Zscaler Cloud Name>/hubs).
You can find the name of your cloud in the URL your admins use to log in to the Zscaler service. For example, if an organization logs in to admin.zscalertwo.net, then that organization's cloud name is zscalertwo.net. In this case, you should go to config.zscaler.com/zscalertwo.net/zia-v-sedge. To learn more, see [What Is My Cloud Name for ZIA?](/zia/what-my-cloud-name-zia)
To configure Virtual Service Edge for home users:
- Remove the Virtual Service Edge as a location from the ZIA Admin Portal.
The logs are recorded as coming from a remote user and not coming from a location.
- Stop the Virtual Service Edge using the following command:
sudo vzen stop
- Create the vzen_custom.config file using the following command:
vi/sc/sme/conf/vzen_custom.conf
The vzen_custom.config file pre-exists if your organization uses the dual arm configuration for Virtual Service Edge.
- Add the following line to the vzen_custom.config file:
[SME]
forbid_nongvzt_users=1
[-end-of-SME-]
- Save and quit the file.
- Start the Virtual Service Edge using the following command:
sudo vzen start