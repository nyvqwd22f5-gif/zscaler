# Best Practices for Traffic Forwarding
Source: https://help.zscaler.com/unified/best-practices-traffic-forwarding
PDF: https://help.zscaler.com/pdf/com/en/1495216.pdf

Zscaler recommends that organizations forward all internet traffic (traffic for all protocols and destined for all ports) to the Zscaler service so it can secure your internet traffic and apply policies accordingly.
Zscaler recommends that you use a combination of tunneling, PAC files, Surrogate IP, and Zscaler Client Connector to forward traffic to the Zscaler service to avoid any [SLAs](https://www.zscaler.com/productsheets) or performance impact.
Zscaler supports the following combinations of traffic forwarding methods:
- [Using Tunneling, PAC Files, Surrogate IP, and Zscaler Client Connector](#best-practice)
- [Using Tunneling, PAC Files, and Surrogate IP](#A)
- [Using Tunneling and PAC Files](#B)
- [Using Tunneling and Surrogate IP](#C)
- [Using PAC Files to Forward Traffic to a Dedicated Proxy Port](#E)
If you cannot deploy any of the recommended combinations of traffic forwarding methods at all locations, you can choose the traffic forwarding method that best suits your organizational needs and environment. For more information on each traffic forwarding method that Zscaler supports, see [Choosing Traffic Forwarding Methods](/unified/choosing-traffic-forwarding-methods).
[]Zscaler recommends using a combination of tunneling, PAC files, Surrogate IP, and Zscaler Client Connector on your users' devices, to forward traffic to the Zscaler service as the best practice. Zscaler also recommends that organizations deploy mechanisms, such as IP SLA, to monitor tunnel health and enable tunnel failover.
If the tunnel's originating router is located after NAT traversal, Surrogate IP is not effective.
The benefits of these best practices are:
- [](/unified/about-bandwidth-control)[](/unified/understanding-firewall-capabilities)
-
- [](/unified/understanding-sub-locations)
| Benefits |
| -------- |
| You can leverage all of the features of the Zscaler platform, which includes Bandwidth Control, Firewall, and creating group and department policies.Users cannot bypass the Zscaler service.You can create sub-locations to implement different policies based on IP addresses. To learn more about sub-locations, see Understanding Sub-Locations. |
If you cannot deploy this combination at all locations, you can choose any of the alternative combination of traffic forwarding methods for some locations, which are listed subsequently.
[]The benefits and limitations of using a combination of tunneling, PAC files, and Surrogate IP are:
-
-
-
-
| **Benefits** | **Limitations** |
| ------------ | --------------- |
| You can leverage all of the features of the Zscaler platform when the users' traffic is forwarded from known locations.Users cannot bypass the Zscaler service. | When user traffic is forwarded from unknown locations with a PAC file, some features of the Zscaler platform are unavailable, such as Firewall, sub-locations, and Surrogate IP.Not all applications support PAC files, therefore not all traffic is secured by Zscaler. |
[]The benefits and limitations of using a combination of tunneling and PAC files are:
-
-
-
-
-
| Benefits | Limitations |
| -------- | ----------- |
| You can leverage all of the features of the Zscaler platform when the users' traffic is forwarded from known locations.Users cannot bypass the Zscaler service. | When user traffic is forwarded from unknown locations with a PAC file, some features of the Zscaler platform are unavailable, such as Firewall, sub-locations, and Surrogate IP.Not all applications support PAC files, therefore not all traffic is secured by Zscaler.Because the Zscaler service is not able to perform user-to-IP mapping without Surrogate IP, users need to re-authenticate every time they use a new user agent, such as a new browser. |
[]The benefits and limitations of using a combination of tunneling and Surrogate IP are:
-
-
-
-
| Benefits | Limitations |
| -------- | ----------- |
| You can leverage all of the features of the Zscaler platform when the users' traffic is forwarded from known locations.Users cannot bypass the Zscaler service from a known location. | There is no protection for remote users outside of the office, because that traffic cannot be forwarded to the Zscaler service.Managing applications that need to be excluded from the Zscaler service becomes difficult without PAC files. |
[]Your organization can subscribe to one or more ports, associate them with a [location](/unified/about-locations), and then forward your traffic to those ports. A dedicated proxy port is considered a known location. To learn more about dedicated proxy ports, see [Configuring Dedicated Proxy Ports](/unified/configuring-dedicated-proxy-ports).
In this deployment, do not specify specific Internet & SaaS Public Service Edges by host names or IP addresses in the PAC file to prevent failover. In the PAC file, you must use the variables `${GATEWAY_FX}` and `${SECONDARY_GATEWAY_FX}` to send web traffic to Internet & SaaS Public Service Edge closest to the user.
The benefits and limitations of using PAC files to forward traffic to one or more dedicated proxy ports are:
-
-
-
-
-
-
-
-
| **Benefits** | **Limitations** |
| ------------ | --------------- |
| The service can apply location, group, and user policies to the traffic.If your router can attach X-Forwarded-For (XFF) headers and if it is enabled on your location, you can leverage the Surrogate IP feature. | This method may not work when users connect to guest Wi-Fi (for example, at hotels and cafés) if that network only allows port 80/443 traffic and blocks the dedicated proxy port.Not all applications support PAC files, therefore not all traffic is secured by Zscaler.End users may be able to bypass the Zscaler service by disabling PAC files.Unless XFF headers are inserted, Zscaler loses internal IP address visibility, and you cannot leverage the sub-location feature.SLAs and performance may be impacted if you don't implement GRE or IPSec tunnels.Because the Zscaler service is not able to perform user to IP mapping without Surrogate IP, users need to re-authenticate every time they use a new user agent, such as a new browser. |