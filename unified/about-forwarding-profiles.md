# About Forwarding Profiles
Source: https://help.zscaler.com/zscaler-client-connector/about-forwarding-profiles
PDF: https://help.zscaler.com/pdf/com/en/1317646.pdf

[Watch a video about forwarding profiles.](https://fast.wistia.net/embed/iframe/45hhpbxghv)
The forwarding profile tells Zscaler Client Connector how to treat traffic from your users' systems in different network environments for the Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA) services.
Zscaler Client Connector Forwarding Profiles provide the following benefits and allow you to:
- Control how traffic flows from user devices in various network environments.
- Configure different forwarding profiles with different network settings within multiple locations.
- Save time locating a profile using the Search feature.
- Easily manage existing profiles using view, edit, copy, and delete features.
Zscaler Client Connector recognizes the following network environments:
- **On-Trusted Network**: When a user is connected to a private network that belongs to your organization. To allow the app to detect this network, you must set the [Trusted Network Criteria](/zscaler-client-connector/configuring-forwarding-profiles-zscaler-app#trusted-network-criteria).
-
**VPN-Trusted Network**: When a user is connected to a trusted network through a VPN in full-tunnel mode. The VPN must be configured to capture all, and not just some, of the user's traffic to the trusted network by installing a default route in the routing table of the client device.
The app does* *not* *consider the network a VPN-Trusted network and treats the user as connected to an Off-Trusted Network in the following scenarios:
- The VPN doesn't install a default route and uses some other mechanism to capture all of the user's traffic.
-
The default interface description does not contain the words Cisco, Juniper, Fortinet, PanGP, or VPN.
macOS does not check the interface description for keywords. Instead, it only checks if the VPN created an utun, PPP, or GPD interface.
- The VPN runs in split-tunnel mode, so that the app takes only some of the user traffic. The VPN can do this by only installing routes for some subnets (e.g., `10/8` or `192.168/16`) or by installing a DNS on the device to resolve specific requests.
- **Off-Trusted Network**: When a user is connected to an untrusted network.
- **Split VPN-Trusted Network**: When a user is connected to a trusted network in split-tunnel mode through a VPN. The app does not consider the network a Split VPN-Trusted Network if:
- The VPN runs as a default adapter.
- The VPN interface description does not contain the words Cisco, Juniper, Fortinet, PanGP, or VPN. If these words are missing, the app treats the user as connected to an Off-Trusted Network.
- The defined Trusted Network Criteria evaluated against the VPN adapter does not match.
When a user connects to a network, the app checks to determine what type of network the user is connected to and displays the network type on the [Internet Security](/zscaler-client-connector/viewing-information-about-internet-security-zscaler-client-connector) window and the [Private Access window](/zscaler-client-connector/viewing-information-about-private-access-zscaler-client-connector). You can configure as many forwarding profiles as you need, and then select the appropriate one when configuring your [app profiles](/zscaler-client-connector/configuring-zscaler-app-profiles). For example, if you have multiple locations with different network information, you can configure different forwarding profiles so that the app can recognize the correct network for different users and know how to respond upon detecting those networks.
If your users are running the app in conjunction with a VPN client, see [Best Practices for Zscaler Client Connector and VPN Client Interoperability](/zscaler-client-connector/best-practices-zscaler-app-and-vpn-client-interoperability) for important additional steps.
About the Forwarding Profile Page
On the Forwarding Profile page, you can do the following:
- [Add a forwarding profile.](/zscaler-client-connector/configuring-forwarding-profiles-zscaler-app)
- [Search for a forwarding profile](/zscaler-client-connector/searching-forwarding-profile?check_logged_in=1).
- View a list of all configured forwarding profiles.
- [Edit a forwarding profile.](/zscaler-client-connector/editing-or-deleting-items-zscaler-app-portal)
- [Copy an existing forwarding profile that you can customize to create a new profile.](/zscaler-client-connector/copying-forwarding-profile)
- [Delete a forwarding profile.](/zscaler-client-connector/editing-or-deleting-items-zscaler-app-portal)
- [View the default forwarding profile.](#default-forwarding-profile)
![Forwarding Profile page](/downloads/zclient-connector-forwarding-profile-page.png)
[]If you don't configure additional forwarding profiles, Zscaler provides a default forwarding profile that is applied automatically. It is always the last forwarding profile in the table on the Forwarding Profile page. Click the **View **icon to see the profile's settings.
Default Forwarding Profile Action for ZIA
- **On-Trusted Network**: When the user is connected to a trusted network, Zscaler Client Connector uses the** **Tunnel** **mode to forward user traffic to Zscaler. It also disables System Proxy settings so that users cannot change proxy settings to bypass Zscaler Client Connector for internet security.
- **VPN-Trusted Network**: When a VPN client on the user's device is running in full-tunnel mode, the app does not forward user traffic to Zscaler. All proxy settings are disabled to ensure users do not send their traffic to a different proxy.
- **Off-Trusted Network**: When the user is off a trusted network, the app uses the Tunnel mode to forward user traffic to Zscaler. It also disables System Proxy settings so that users cannot change proxy settings to bypass the app for internet security.
Default Forwarding Profile Action for ZPA
- **On-Trusted Network**: Zscaler Client Connector uses the ZPA service to provide users with access to internal applications even when users are on trusted networks.
- **VPN-Trusted Network**: ZPA is disabled, and the app does not provide users with access to internal applications.
- **Off-Trusted Network**: The app uses the ZPA service to provide users with access to internal applications even when users are on trusted networks.