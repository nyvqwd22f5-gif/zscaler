# ZIA Performance Troubleshooting Runbook
Source: https://help.zscaler.com/troubleshooting-runbooks/zia-performance-troubleshooting-runbook
PDF: https://help.zscaler.com/pdf/com/en/1532325.pdf

The ZIA Performance Troubleshooting Runbook outlines a systematic approach to troubleshooting performance slowness experienced by users. It emphasizes understanding the scope of issues, including differentiating between affected traffic types and assessing user connections to the nearest Zscaler data centers. The troubleshooting steps involve validating traffic forwarding methods, configurations, collecting and analyzing data through performance tests and network diagnostic tools. By following this methodology, you can effectively identify the root causes of performance issues and implement corrective actions to optimize user experience.
Improving ZIA Performance
The following article describes how to improve ZIA performance, if issues are noted. Solutions are categorized into three main sections: the type of traffic impacted, whether Z-Tunnel is affected, and if the Public Service Edge is affected.
What Type of Traffic is Impacted?
First, determine whether all traffic is affected or if only non-web traffic is impacted and web browsing remains unaffected. For instance, users might report performance issues with Zscaler because they experience disconnects or choppy audio with Microsoft Teams meetings, and other types of access remain unaffected.
By gathering this information, you can analyze and determine if web and non-web traffic are following different routes (e.g., using PAC or Z-Tunnel 1.0 to forward non-web traffic directly to the internet). Similarly, for issues with all traffic, a different approach is needed.
[Non-Web Traffic or Traffic on Non-Standard Ports](#non-web-traffic)
[]In cases when only non-web traffic is affected (e.g., Microsoft Teams meeting issues), you must ensure users are forwarding non-web traffic or are forwarding the non-web traffic for the affected service through Zscaler.
You can filter the Web Insight logs to identify an affected user or location and can check the Traffic Forwarding column to validate the traffic forwarding method.
How to Validate if the User is Forwarding Non-Web Traffic to Zscaler
- Check **Firewall Insights** on **Top 100 Network Service** for any non-web (not HTTP or HTTPS) traffic.
- See if there are other network services like DNS, ICMP, SNMP, SFTP traffic that indicate that the user is forwardiing all ports and protocols to Zscaler’s Zero Trust Exchange (ZTE).
[See image.](#Firewall-Insights)
PAC or Z-Tunnel 1.0
Non-web traffic is not forwarded to Zscaler when using Proxy Auto-Configuration (PAC) or Z-Tunnel 1.0. Check the internal network (like PBR or routing) to see if non-web traffic is being forwarded to Zscaler or local breakouts.
GRE, IPSec, Z-Tunnel 2.0
Non-web traffic can be forwarded to Zscaler using Generic Routing Encapsulation (GRE) or IPSec or Z-Tunnel 2.0 with additional configuration. If you are not seeing non-web traffic on the Zscaler Firewall Insights logs, then check the internal network (like PBR or routing or Zscaler Client Connector Forwarding profile) to see if non-web traffic is being forwarded via different paths or local breakouts.
[Web Only or All Traffic](#web-only-traffic)
[]
Check if the user is connected to the nearest Zscaler data center. The syntax is:
`https://pac.``<cloudname>``.net/getGatewayEndpoints?srcip=x.x.x.x`
Replace `<cloudname>` with your production Zscaler cloud and `x.x.x.x` as Egress IP of user (e.g., [https://pac.zscalertwo.net/getGatewayEndpoints?srcip=170.85.8.25](https://pac.zscalertwo.net/getGatewayEndpoints?srcip=170.85.8.25)).
[See image.](#nearest-zscaler-dc)
The output shows the three nearest Zscaler public data centers (excluding regional surcharge data centers).
There could be a few reasons why the user is not connected to the nearest Zscaler data center:
- Incorrect geo IP mapping in MaxMind.
- Incorrect subcloud configuration.
Incorrect Geo IP Mapping in MaxMind
Zscaler uses MaxMind for geo IP tagging. When the user turns on Zscaler Client Connector for the first time, it presents its public Egress IP to the Zscaler PAC server. The PAC server performs a lookup for the geolocation of the IP address against MaxMind's database and assigns the nearest Zscaler data center to it.
There could be instances where a user's public IP is mapped to an incorrect location on MaxMind. In such cases, Zscaler can't return the nearest Zscaler data center to the user, which results in Zscaler Client Connector connecting to a location other than the nearest Zscaler data center, thereby causing suboptimal performance.
As part of troubleshooting, go to [https://www.maxmind.com/en/geoip-demo](https://www.maxmind.com/en/geoip-demo) and search for the egress IP of the user (obtained from [ip.zscaler.com](https://ip.zscaler.com) and Your Gateway IP Address section).
If MaxMind returns an incorrect location against a user's public IP, this often means that the user isn't connecting to the nearest Zscaler data center. This inaccuracy needs to be corrected as soon as possible. The customer or Zscaler can rectify the inaccuracy with MaxMind mapping.
Customer initiated:
- Customers can request the correction of the geo IP mapping by raising a request with MaxMind. They must submit a correction request by following the instructions presented here.
- MaxMind performs corrections only twice a week, so the customer's request to rectify the geo IP tagging might be delayed.
Zscaler initiated:
- Zscaler can perform a geo IP Override of a given IP address upon customer's request.
- After Zscaler performs a manual geo IP override, Zscaler stops using the MaxMind geo tags to determine the nearest Zscaler data center, but bases the IP mapping on the data from the local database to determine the nearest Zscaler data center.
If you would like to raise a request to perform a geo IP override, open a Zscaler Support case.
Incorrect Subcloud Configuration
A [subcloud](/zia/understanding-subclouds) is a subset of ZIA public data centers or Private Service Edges, where you can pick and choose to which data centers users should connect.
If there is a misconfiguration in the subcloud, users might connect to a location other than the nearest Zscaler data center.
If you already have a subcloud provisioned in the ZIA Admin Portal, check to see if the desired Zscaler data center is part of the subcloud.
[See image.](#edit-subcloud)
Check the App Profile PAC file and confirm that users have no special PAC statements to forward the traffic (from a specific country or a specific egress IP) to a specific Zscaler data center.
If you would like to request that a missing data center be added to your subcloud, or request a new subcloud, contact [Zscaler Support](/contact-support) with details of your subcloud name.
Check if the Nearest Data Center is Enabled with Auto Geo Proximity
To identify a data center with the **Auto Geo Proximity** option enabled, go to [config.zscaler.com](https://config.zscaler.com) and locate the green checkbox next to the **Proxy Hostname** of a data center.
[See image.](#auto-geo-proximity)
For content localization, if users are connected from a location which is closer to a Zscaler data center in the neighboring countries, users should leverage the Country Gateway Variable to connect with an in-country Zscaler data center (if available). The Country Gateway Variable supports auto geo proximity and the subcloud.
Data centers that do not have the Auto Geo Proximity flag enabled are not part of ${GATEWAY} and ${COUNTRY_GATEWAY} PAC resolution by default. The Auto Geo Proximity flags are not enabled for a few Regional Surcharge data centers and some newly provisioned data centers. If a user wants to connect to a data center by proximity, they either must use a subcloud (and include the non-auto proximity data center in it), or must manually add a PAC statement in the App Profile PAC file to connect to that particular data center.
Here are the PAC samples if not using subcloud, where users in Taiwan would like to connect to Zscaler Taipei data center.
Z-Tunnel 1.0:
`var country = "${COUNTRY}";
if (shExpMatch(country,"Taiwan")) {
/* User is in Taiwan*/
return "PROXY tpe2.sme.zscloud.net:443; PROXY ${SECONDARY_GATEWAY}:443;DIRECT";
}`
Z-Tunnel 2.0:
`var country = "${COUNTRY}";
var tunnel2 = "${ZT2_REQUEST}";
if ((shExpMatch(country,"Taiwan")) && (tunnel2 == "true")) {
/* User is in Taiwan*/
return "PROXY <SVPN VIP>:443; PROXY ${SECONDARY_GATEWAY}:443;DIRECT";
}`
If the nearest Zscaler data center has **Auto Geo Proximity **enabled, but a user still can't connect to it, Zscaler uses MaxMind's services to learn the geotagging of an IP address. The most probable cause of this issue is that MaxMind has incorrectly geotagged the user's IP address. Submit a correction request by following the instructions in this section to initiate a correction to the geo IP mapping of the user's egress IP Address.
Does the Issue Affect Z-Tunnel 2.0 Only, Specific Destination, or a Poor Speedtest Result?
To address the performance issue effectively, it is crucial to determine the scope of the problem and identify if any specific destinations are affected. It is important to gather information to understand if certain applications or services are experiencing issues, or if all traffic is impacted.
At the same time, it is also important to understand how the user is measuring performance, if complaints are based solely on speed test results, even though the browser is functioning properly.
When you have a clear understanding of the extent of the impact, you can proceed with the troubleshooting process according to this guide.
[Does the Issue Only Apply to Z-Tunnel 2.0](#z-tunnel-2.0)
[]
If the traffic forwarding method is Z-Tunnel 2.0, you must rule out if the performance issue is experienced only with Z-Tunnel 2.0 or with other traffic forwarding methods as well. If the issue is observed only with Z-Tunnel 2.0, focus on troubleshooting Zscaler Client Connector.
Compare performance of Z-Tunnel 2.0, PAC, or Manual proxy to find if any slowness issues persist.
How to Perform a Manual Proxy Test
- Go to [http://ip.zscaler.com](http://ip.zscaler.com) to find which data center the customer is connected to.
[See image.](#data-center)
- Logout from Zscaler Client Connector.
- Then go to [https://config.zscaler.com](https://config.zscaler.com) to find the FQDN of PAC VIP for the data center.
[See image.](#FQDN-PAC-VIP)
- Go to the browser's **Internet Options** > **Connections **> **LAN Settings**, set a manual proxy server to FQDN of data center with port 80/443. Add the relevant IdP authentication domains in the proxy bypass.
[See image.](#lan-settings)
- Visit an HTTP website (e.g., [http://httpforever.com/](http://httpforever.com/)) to complete the Zscaler cookie authentication process.
- Ask the user to access day-to-day applications and note any improvement in performance.
If slowness occurs with both Z-Tunnel 1.0/PAC and Z-Tunnel 2.0, go to [Speedtest Poor Result](#speed-poor-result-anchor) to continue with troubleshooting.
If you observe slowness only with Z-Tunnel 2.0, see [Zscaler Client Connector Performance Troubleshooting Runbook](/troubleshooting-runbooks/zscaler-client-connector-performance-troubleshooting-runbook).
[Specific Destination](#specific-destination)
[]
If only specific destinations are affected, first check to which public data centers the specific destinations are routed. Based on this information, you can then determine the appropriate next course of action.
You can ask the user to provide [ip.zscaler.com](https://ip.zscaler.com) output to verify traffic forwarding information.
Assess Website Performance without Zscaler
Find an affected user who is connected to a non-Zscaler environment, such as Guest Wi-Fi or a mobile hotspot, and test the performance. This step helps isolate whether the performance problem is related to Zscaler or the destination server.
- If the result is `Slow Loading with Direct Access`, then you can involve the destination webmaster to investigate any ongoing issues with the server.
- If the result is `Normal Loading with Direct Access,` then continue to collect Wireshark capture, browser's header trace and MTR to the impacted destination server for baseline measurements while accessing the domain directly.
Check for Any Active Cloud Incidents on the Zscaler Trust Portal
Check for any open cloud incidents for the affected domain or Zscaler data center on the Trust Portal. If an active incident Trust Post is found, check if the affected website is working through a different Zscaler data center.
Potential Workaround: Redirect the impacted traffic to another Zscaler data center (PAC Modification or Policy Based Routing modification), or bypass Zscaler (PAC Modification or Policy Based Routing modification).
Compile all the data collected and open a support case with [Zscaler Support](/contact-support).
[][Poor Speedtest Result](#speed-poor-result)
[]
Assess user impact in terms of performance, or if the user complaint is about poor speed test results.
Overall Browsing Experience is Slow
Relying solely on Speedtest results is insufficient to determine performance issues. It is important to determine if the issue is about performance and if the user experience is impacted.
If there is an actual impact on end user performance, go to [Zscaler Public Data Center](#scope-3-zia) to continue with the troubleshooting.
Only Poor Speedtest Result
If users are not experiencing any significant issues with their day-to-day internet activities, it is likely that their actual performance is not affected, even if the Speedtest results appear lower than expected.
Speedtest results serve as a general indicator of network performance, but they might not always accurately reflect the actual experience of end users. There are various factors that can contribute to the difference between Speedtest results and actual performance.
Some common measurement tools such as Speedtest or iperf have issues that might impact reporting. Zscaler recommends using the [Zscaler Cloud Performance Test Tool](/zia/using-zscaler-cloud-performance-test-tool). To learn more, see [Measuring the Performance of the Zscaler Service](/zia/measuring-performance-zscaler-service).
Run the Zscaler Cloud Performance Test Tool to get the Download and Upload speed results.
[See image.](#cloud-performance-test-tool)
Study the output indicators, such as a map view of the user's location, user location, and the Zscaler data center, latency, jitter, and packet loss that can contribute to slow speeds.
The More Diagnostics tab can give a comparison between Zscaler Client Connector and Direct speed results (Z-Tunnel 2.0 only).
Even with the Zscaler Speedtest tool, Speedtest results do not guarantee the maximum bandwidth they have subscribed to. The bandwidth is typically shared among multiple users, so one user might use the entire allocated bandwidth. Even if the user has 50 Mbps internet link, it doesn't mean that the Speedtest returns 50Mbps.
You can also use Performance Monitor from Windows's Task Manager to check the Upload(Send) and download(Receive) throughput by downloading multiple files.
How to Leverage Windows Task Manager Performance Monitor
- Click **Start **and then enter `Task Manager` into the search bar. Click the icon to open the Task Manager.
[See image.](#best-match)
- Go to the **Performance **option and the active Network connection (Ethernet, Wi-Fi, etc.).
- Start downloading a few large files from different download servers. For example:
- [https://sgp-ping.vultr.com/](https://sgp-ping.vultr.com/)
- [https://www.thinkbroadband.com/download](https://www.thinkbroadband.com/download%20)
- [https://kb.leaseweb.com/kb/network/network-link-speeds/](https://kb.leaseweb.com/kb/network/network-link-speeds/)
- Take note of the Send and Receive throughput and compare between with and without Zscaler (the following outputs show that both scenarios are reaching a potential 500 Mbps download):
[See image.](#without-zscaler)
[]Zscaler Public Data Center
This section assumes that all customer traffic is being affected by specific locations. This runbook focuses on user traffic forwarded to Zscaler public data center only.
[All Destinations](#all-destination)
[]
The following sections describe how to review performance for traffic from all destinations.
Assess Website Performance without Zscaler
Find an affected user connecting to a non-Zscaler environment, such as the Guest Wi-Fi or a Mobile hotspot, and test the performance. This step helps isolate whether the performance problem is related to Zscaler or the destination server.
If the result is `Slow Loading with Direct Access`, then you can involve the destination webmaster to investigate any ongoing issues with the server.
If the result is `Normal Loading with Direct Access`, then continue to collect Wireshark capture, browser's header trace and MTR to the impacted destination server to obtain baseline measurements while accessing the domain directly.
Check for Any Active Cloud Incidents on Zscaler’s Admin Portal
Check for any open cloud incidents for the affected domain or Zscaler data center on Trust Portal.
If an active incident Trust Post is found, complete the following:
- Check if the performance improves when using a different Zscaler Data Center and perform traffic failover according to Traffic Forwarding methods.
- Compile all the data collected and open a support case with [Zscaler Support](/contact-support).
Check for Traffic Imbalance
For a GRE tunnel or Zscaler Client Connector over a GRE Tunnel, sending Zscaler Client Connector Z-Tunnel 2.0 over a GRE tunnel causes suboptimal processing of traffic. This is not a recommended setup due to additional overhead on both Z-Tunnel 2.0 and the GRE tunnel.
How to Check Z-Tunnel 2.0 over GRE Tunnel?
- Find the public egress IP address of the GRE tunnel using [ip.zscaler.com](https://ip.zscaler.com).
- Find from Web Insights logs for any matching transaction from the affected user where both:
- Traffic Forwarding: Zscaler Client Connector over GRE.
- Zscaler Client Connector Tunnel Version: **Z-Tunnel 2.0 TLS** OR **ztunnel_2.0 dtls1.0** OR **ztunnel_2.0 dtls1.2** OR **ztunnel_2.0 udp**.
[See image.](#insight-logs)
Recommendations:
- Switch to Z-Tunnel 1.0 for **On-Trusted **network behind a GRE tunnel and Enable IP surrogacy on all locations for both Known or Unknown User agents.
- Bypass Zscaler's Recommended Hub IP addresses at the router and firewall level, using Policy Based Routing from the GRE tunnel, so that Z-Tunnel 2.0 traffic goes DIRECT to the internet. Ensure the Public Egress IP is configured and associated as a *Known Location*.
Zscaler supports a maximum bandwidth of 1 Gbps for each GRE tunnel if the internal tunnel endpoint IP addresses are not source network address translated (NAT'd).
- Configure more GRE tunnels with different public source IP addresses.
For an IPSec tunnel or Zscaler Client Connector over an IPSec tunnel, sending the Zscaler Client Connector Z-Tunnel 2.0 over the IPSec tunnel causes suboptimal processing of traffic. This is not a recommended setup due to additional overhead on both Z-Tunnel 2.0 and IPSec tunnel.
How to Check Z-Tunnel 2.0 over IPSec
To check the Z-Tunnel 2.0 over IPSec:
- Find the public egress IP address of the IPSec tunnel using ip.zscaler.com.
- Find from Web Insights logs for any matching transaction from the affected user where both:
- Traffic Forwarding: Zscaler Client Connector over IPSec Tunnel.
- Zscaler Client Connector Tunnel Version is **Z-Tunnel 2.0 TLS**, **ztunnel_2.0 dtls1.0**, **ztunnel_2.0 dtls1.2**, or **ztunnel_2.0 udp**.
[See image.](#insight-logs-2)
Recommendations:
- Switch to Z-Tunnel 1.0 for **On-Trusted** network behind an IPSec tunnel and Enable IP surrogacy on all locations for both Known or Unknown User agents.
- Bypass Zscaler's Recommended Hub IP addresses at the router and firewall level, using Policy Based Routing from the IPSec tunnel, so that Z-Tunnel 2.0 traffic goes DIRECT to the Internet. Ensure the Public Egress IP is configured and associated as a Known Location.
Zscaler IPSec tunnels support a limit of 400 Mbps for each public source IP address.
- Configure multiple IPSec tunnels with different public source IP addresses.
- Configure multiple IPSec VPN tunnels with the same public source IP address using NAT-T and source port randomization with IKEv2.
For Explicit/PAC or Zscaler Client Connector Tunnel 1.0/TWLP
Recommendation:
- Verify the PAC file and suggest the following:
- Use the `${GATEWAY_FX}` variable for the Zscaler Client Connector method.
- Use the `${GATEWAY_Fn}` variable for PAC method.
- Add more IP address in the NAT pool for better load distribution per Proxy instance.
- Zscaler recommends adopting Z-Tunnel 2.0 and ensure the Egress IP is associated to a Known Location.
Review Client and Zscaler Data Center MTR
The following sections describe reviewing data center MTR.
Collecting Forward MTR
- Use a tool called WinMTR that can be downloaded from sites such as [sourceforge.net](https://sourceforge.net/) or [winmtr.en.uptodown.com](https://winmtr.en.uptodown.com).
- Prepare a different environment to extract the data using WinMTR. Generally, traffic forwarding options include Zscaler Client Connector, GRE, IPSec, or a PAC file. In Zscaler Client Connector, there are Z-Tunnel 1.0, Z-Tunnel 2.0, and Tunnel with Local Proxy. Take note when collecting MTR for the following Traffic Forwarding Methods:
- Zscaler Client Connector: Z-Tunnel 2.0: With this forwarding method, log out of Zscaler Client Connector and collect the MTR.
- IPSec and GRE: There are two options in this case. You can either exempt the ICMP traffic completely from your Edge Device (e.g., Firewall, Router, etc.) or exempt one system from the GRE or IPSec configuration on the Firewall. As a result, the traffic from this system would go directly over the internet. You can then turn the MTR on for this system to get the desired output.
- Get the Proxy IP address from the output of ip.zscaler.com.
[See image.](#proxy-ip-address)
- Take note of the Proxy IP address (first line) from the output in the preceding step and enter this IP address in the **Host **option in the WinMTR tool. Then click **Start**.
[See image.](#winmtr-tool)
Remember to uncheck **Resolves name** before collecting this data so that you can see the IP addresses of all the Hops.
[See image.](#winmtr-tool-2)
- After the MTR is started, keep it running for at least 300 packets. You can run it for more packets, however, 300 is the minimum count needed. You can stop MTR after it is done.
[See image.](#winmtr-tool-4)
- Next, save the output by clicking **Export Text**. The sample output snippet is as follows:
[See image.](#forward-mtr-txt)
Analyzing MTR
- Verify latency. ICMP rate limiting can also create the appearance of latency. The latency between hops 4 and 5 draws attention. However, after the 5th hop, the latency drops drastically. The actual latency measured here is about 40ms. In cases like this, MTR draws attention to an issue that does not affect the service. Consider the latency to the final hop when evaluating an MTR report. The amount of latency jumps significantly between hops 3 and 4 and remains high. This might point to a network latency issue as round trip times remain high after the 4th hop. While there is a large jump in latency between hosts 3 and 4, the latency does not increase unusually in any subsequent hops. From this, it is logical to assume that there is some issue with the 4th hop.
[See image.](#verify-latency)
This next image shows the final hop.
[See image.](#final-hop)
- Verify packet loss. The loss reported between hops 1 and 2 is likely due to rate limiting on the second hop. If the loss continues for more than one hop, then it is possible that there are packet loss or routing issues.
[See image.](#packet-loss)
There is a 60% loss between hops 2 and 3 as well as between hops 3 and 4. We can assume that the third and fourth hops lose some amount of traffic because no subsequent host reports zero loss. However, some of the losses are due to rate limiting because several of the final hops experience only a 40% loss. When different amounts of loss are reported, always trust the reports from later hops. Some loss can also be explained by problems in the return route. Packets reach their destination without error but have difficulty making the return trip.
[See image.](#packet-loss-2)
Check Zscaler Bandwidth Control Policy
- Check **Location Management** configuration, if no Sublocation, check the reported main Locations and verify that Bandwidth Control is enabled.
[See image.](#location-management)
- Check L**ocation Management** configuration and, if Sublocations exist, and verify that Bandwidth Control is enabled.
[See image.](#view-sub-location)
- Check Web Insights on **Bandwidth Consumption** with filters and verify that the **Bandwidth Action** is **Throttled **for each impacted **Location **or **SubLocation**.
[See image.](#throttled-action)
- Alternatively, you can check Web Insights Logs with filters like **Throttled response bytes **and **Throttled request bytes**, and review the impacted Location or Sublocation.
[See image.](#web-insights-logs)
- If users of a Known Location and bandwidth control policy are enabled, Zscaler suggests creating a sublocation with less client IPs and disabling the bandwidth control policy on the sublocation.
- If the performance improves, then review the top bandwidth users and the bandwidth control policy.
Additional Checks
- Investigate any network changes that might have lead to the issue.
- Revert the most recent network change to see if it addresses the problem.
- Review the ISP details (Single or Multi, Provider Name, Link size).
- Check to see if traffic load is balanced between multiple ISPs.
- Check your ISP utilization.
- Check for any failovers to a secondary ISP link.
Further Steps
Compile all the data collected and open a support case with [Zscaler Support](/contact-support).
[]![Web Insights Logs](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/Web-Insights-Logs.png)
[]![Throttled Action](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/Throttled-Action.png)
[]![View Sub Location](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/View-Sub-Location.png)
[]![Location Management](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/Location-Management.png)
[]![Packet Loss 2](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/Packet-Loss-2.png)
[]![Packet Loss](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/Packet-Loss.png)
[]![Final Hop](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/Final-Hop.png)
[]![Verify Latncy](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/Verify-Latency.png)
[]![Forward MTR .txt](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/forwardmtr.txt.png)
[]![WinMTR Tool-4](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/WinMTR-tool-4.png)
[]![WinMTR Tool-2](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/WinMTR-tool-2.png)
![WinMTR Tool-3](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/WinMTR-tool-3.png)
[]![WinMTR Tool](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/WinMTR-tool.png)
[]![Proxy IP Address](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/Proxy-IP-Address.png)
[]![Insight Logs 2](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/Insight-Logs-2.png)
[]![Insight Logs](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/Insight-Logs.png)
[]![Without Zscaler](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/Without-Zscaler.png)
![With Zscaler](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/With-Zscaler.png)
[]![Best Match](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/Best-Match.png)
[]![Zscaler Cloud Performance Test Tool](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/Zscaler-Cloud-Performance-Test-Tool.png)
[]![LAN Settings](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/LAN-Settings.png)
[]![FQDN of PAC VIP](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/FQDN-PAC-VIP.png)
[]![Data Center](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/data-center.png)
[]![Auto-Geo-Proximity.png](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/Auto-Geo-Proximity.png)
[]![Edit Subcloud](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/Edit-Subcloud.png)
[]![Nearest Zscaler Data Center](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/Nearest-Zscaler-DC.png)
[]![Firewall Insights](/downloads/troubleshooting-runbooks/zia-performance-troubleshooting-runbook/Firewall-Insights.png)