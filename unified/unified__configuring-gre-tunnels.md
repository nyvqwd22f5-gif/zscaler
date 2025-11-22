# Configuring GRE Tunnels
Source: https://help.zscaler.com/unified/configuring-gre-tunnels
PDF: https://help.zscaler.com/pdf/com/en/1492886.pdf

The following diagram is an example GRE tunnel configuration.
![A diagram of an example GRE tunnel configuration](/downloads/zia/traffic-forwarding/gre/configuring-gre-tunnels/zia-traffic-forwarding-gre-tunnel-configuration-diagram.png)
To configure GRE tunnels from your corporate network to the Zscaler service:
- [1. Review the configuration guidelines.](#step1)
- [2. Provision a GRE tunnel to your account.](#step2)
- [3. Log in to the Admin Portal and add your gateway location.](#step3)
- [4. Configure your router or firewall to allow the GRE tunnel.](#step-4)
You can go to Logs > Insights > Tunnel Insights to see data, as well as monitor the health and status of your configured GRE tunnels. To learn more, see [About Insights](/unified/about-insights) and [About Insights Logs](/unified/about-insights-logs).
- []Zscaler recommends configuring two separate GRE tunnels to two Internet & SaaS Public Service Edges that are each located in a different data center for high availability. If the primary GRE tunnel or an intermediate connection goes down, all traffic is then rerouted through the backup GRE tunnel to the secondary Internet & SaaS Public Service Edge.
Ensure that if the primary tunnel goes down, that the router detects it and changes the routing table or routing instance so that the secondary tunnel is used for traffic forwarding and vice versa.
- Use the GRE tunnel to forward internet traffic to the service. If supported, use policy-based routing (PBR) to ensure that only internet-bound traffic is sent through the GRE tunnel. PBR is a mechanism that enables a router to determine where to forward packets based on configured policies. When you configure a GRE tunnel, you can use PBR to ensure that only internet-bound traffic is sent through the tunnel. A policy typically includes match criteria and the action that the router takes on the traffic. Match criteria can include the source and destination IP addresses and ports, and the protocol, such as HTTP or HTTPS. The action specifies the next hop of the packets. When a packet arrives at a router with PBR enabled, it determines if the packet matches a configured policy and then routes it accordingly. PBR enables packets to take different paths based on the match criteria.
- If supported, enable GRE keepalives in the primary and secondary tunnels. When you configure a GRE tunnel to the service, enable GRE keepalives so the traffic can switch from the primary to the secondary tunnel in the event of a failure. Additionally, ensure that the settings are neither too aggressive nor too slow in detecting when the tunnel is down. If your router does not support GRE keepalives, you can configure ICMP probes instead.
- For Cisco routers, you can use IPSLAs to monitor the tunnels. You can set a threshold so the traffic can switch from the primary to the secondary tunnel when the threshold is exceeded. For Juniper routers, you can use real-time performance monitoring (RPM) to monitor the VPNs.
- Most routers apply the policy-based route to redirect traffic to the tunnel before they apply network address translation (NAT) to the traffic. Therefore, the internal client IP addresses of traffic routed through the tunnel are preserved. If your router performs NAT before it sends traffic through the tunnel, consider disabling NAT to allow the Zscaler service to see internal IP addresses. This enables the service to use internal IP addresses for logging and reporting. Additionally, you can configure sublocations to identify internal networks whose outbound traffic is encapsulated in the GRE tunnel. When using sublocations, the service can retrieve the IP addresses of the internal networks and apply custom policies to the traffic of the internal networks.
- If your firewall has an ACL blocking inbound connections, configure a rule to allow GRE traffic (protocol 47).
[]You can provision a GRE tunnel to your account by using one of the following methods:
- [Use the Admin Portal to self-provision your GRE tunnel.](/unified/self-provisioning-gre-tunnels)
- [Contact your Zscaler representative or Zscaler Support to provision your GRE tunnel.](#step2-substep)
[]Contact Zscaler Support and provide the following information so Zscaler can provision the GRE tunnels:
- The public IP address of the tunnel source
- The physical location of your router
Zscaler then assigns VIPs (virtual IP addresses) for use as the source and destination addresses inside the tunnel. Zscaler assigns these addresses from a pool of non-routable address space that Zscaler manages to ensure that no two customers attempt to use the same IP addresses.
The following table provides an example of what Zscaler sends to an organization that wants to configure GRE tunnels, together with an example for each IP address:
| Example | Explanation |
| ------- | ----------- |
| Tunnel Source IP: 192.0.2.2 | The IP address of the tunnel source. This is provided by the customer. |
| Internal Range: 172.18.58.120–172.18.58.127 | The IP address range that Zscaler assigned to the organization |
| Primary Destination: 216.66.5.49 | The IP address of the Internet & SaaS Public Service Edge, which is the primary tunnel destination |
| Internal Router IP: 172.18.58.121/30 | The VIP of the tunnel source |
| Internal Internet & SaaS Public Service Edge IP: 172.18.58.122/30 | The VIP of the tunnel destination |
| Secondary Destination: 199.169.149.79 | The IP address of the Internet & SaaS Public Service Edge, which is the secondary tunnel destination |
| Internal Router IP: 172.18.58.125/30 | The VIP of the tunnel source |
| Internal Internet & SaaS Public Service Edge IP: 172.18.58.126/30 | The VIP of the tunnel destination |
Zscaler has Internet & SaaS Public Service Edges worldwide and selects the most appropriate Internet & SaaS Public Service Edges as destinations for your tunnels.
When Zscaler assigns the VIPs, the Zscaler service binds the source and destination addresses to the specified primary and secondary Internet & SaaS Public Service Edges. The Internet & SaaS Public Service Edge listens specifically for traffic from the source VIP and addressed to its destination VIP. When your GRE tunnel sends traffic to the Zscaler service, the Internet & SaaS Public Service Edge associates the virtual source and destination addresses with your organization.
[]After your IP addresses have been provisioned on the Zscaler service, log in to the Admin Portal and define your organization’s gateway location as follows:
- Go to **Infrastructure **>** Internet & SaaS **>** Traffic Forwarding **>** Location Management**.
- On the **Locations** page, click **Add Location**.
- Enter general information about the location:
- **Name**: Enter a name for the location.
- **Country**:** **Choose the country of the location.
- **City/State/Province**: Enter the name of the location's city, state, or province, if applicable.
- **Time Zone**: Choose the time zone of the location.
When you specify the location in a policy, the service applies the policy according to the location's time zone. For example, if a Cloud App Control policy blocks posting to Facebook between 8:00 AM and 5:00 PM, and the rule is applied to locations in Spain and California, users at each location are blocked during their respective daytime hours.
- Choose the IP addresses for the location:
- The **Public IP Addresses** list displays the IP addresses that you sent to Zscaler when it provisioned your organization. Choose IP addresses for the location.
- Optionally, enable the other features on this page.
- Click **Save** and activate the change.
[]For redundancy reasons, Zscaler recommends configuring multiple GRE tunnels to Zscaler. After completing the previous step, you have the following two types of addresses:
- Internet-routable public IP addresses outside the GRE tunnels
- Internal range IP addresses (i.e., RFC1918 private IP addresses) inside the GRE tunnels
The static IP address that you assigned to your location is the public source IP address for both the GRE tunnels. Zscaler assigns a /29 subnet for the GRE tunnels. You need to split it into two /30 subnets. For the first /30 subnet, assign the first host IP address to your location and the second host IP address to the Zscaler data center. This process should be repeated with the second /30 subnet on the other GRE tunnel.
To learn more about the configuration instructions, refer to the help documentation of your router or firewall.
For sample configurations, see the following articles:
- [GRE Configuration Example: Cisco 881 ISR](/unified/gre-configuration-guide-cisco-881-isr)
- [GRE Configuration Example: Juniper SRX](/unified/gre-configuration-guide-juniper-srx)