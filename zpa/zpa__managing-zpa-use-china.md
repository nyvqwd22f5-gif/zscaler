# Managing ZPA Use in China
Source: https://help.zscaler.com/zpa/managing-zpa-use-china
PDF: https://help.zscaler.com/pdf/com/en/1516656.pdf

Zscaler's China Premium Service for Zscaler Private Access (ZPA) feature provides a way for users residing in mainland China to access private applications both inside and outside of mainland China. If you are looking for China Premium Internet Access for Zscaler Internet Access (ZIA), see [Managing ZIA Use in China](/zia/managing-zia-use-china).
The China Premium service for ZPA uses a ZPA Private Service Edge hosted at a partner site within China. The ZPA Private Service Edge uses a premium Chinese internet service provider (ISP) with access to both the domestic private applications in China and premium access to international private applications. This service allows you to break and inspect traffic within China, and use the partner premium fabric for any destination (domestic or international).
The key benefits of using Zscaler’s China Premium Service for ZPA are:
- Providing consistent access and improved latency speeds with premium connectivity.
- Reliable access with multiple ISPs resulting in improved peering among ISPs in premium data centers (i.e., Beijing and Shanghai).
- Multi-region dual premium data centers where traffic goes based on the user's proximity to the data centers.
- Data redundancy in the event that a premium data center is unreachable.
- Overcoming the limitations of the Great Firewall of China.
- Users in China have premium connectivity to private applications both inside and outside of China.
Premium Services
The following China Premium service options are available for organizations where users are working from mainland China:
- [Accessing private applications outside of China](#outside)
- [Accessing private applications inside of China](#inside)
Prerequisites for China Premium Service for ZPA
To ensure you are prepared to use the China Premium service for ZPA:
- ZPA should be operational in China with private applications access provided to users in China.
- Ensure your ZPA bandwidth is appropriately sized based on megabits per second (Mbps) for the configured private applications. Contact Zscaler Support if you need help.
- Refer to the [Zscaler Private Access Firewall Whitelist](https://config.zscaler.com/private.zscaler.com/zpa) to ensure you are using the correct IP address protocols, ports, domains, and IP addresses. This list allows you to firewall outbound traffic. Contact Zscaler Support if you need help.
- This feature is only available with a license. Contact your account manager for more information. The license allows ZPA users from China to be connected to ZPA Private Service Edge with the Premium Circuit.
[]A user in China makes a connection with a ZPA Private Service Edge within China with a premium circuit in China. The user doesn’t connect to the public data center. The user connects to the closest ZPA Private Service Edge, based on the user’s location (either the Beijing or Shanghai Premium data centers), creating a Zscaler Tunnel (Z-Tunnel) which forms the Microtunnel (M-Tunnel). The App Connector outside of China connects through this premium circuit back to the ZPA Private Service Edge, creating a Z-Tunnel which forms the M-Tunnel. The Great Firewall of China doesn’t block it as it is a private application. After the Z-Tunnel is formed, the connection is established and the user can then access the private applications outside of China.
Zscaler is the single point of contact for ZPA China Premium services.
![Accessing private applications outside of China using the premium service for ZPA](/downloads/zpa/managing-zpa-use-china/Outside%20of%20China%20ztunnel.png)
[]A user in China makes a connection with a Private Service Edge within China with a premium circuit in China. The user doesn’t connect to the public data center. The user connects to the closest ZPA Private Service Edge, based on the user’s location (either in Beijing or Shanghai Premium data centers), creating a Z-Tunnel which forms the M-Tunnel. The App Connector in China then connects to the ZPA Private Service Edge in China, creating a Z-Tunnel which forms the M-Tunnel. The user then connects to private applications within China. The Great Firewall of China doesn’t apply in this use case as the traffic is inside China and never crosses the China borders.
Zscaler is the single point of contact for ZPA China Premium services.
![Accessing private applications inside of China using the premium service for ZPA](/downloads/zpa/managing-zpa-use-china/Inside%20of%20China%20ztunnel.png)