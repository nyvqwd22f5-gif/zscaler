# Best Practices for Zscaler Client Connector and VPN Client Interoperability
Source: https://help.zscaler.com/unified/best-practices-zscaler-client-connector-and-vpn-client-interoperability
PDF: https://help.zscaler.com/pdf/com/en/1495626.pdf

If your users are running Zscaler Client Connector in conjunction with a corporate VPN client, follow these best practices:
- [Step 1: Select Forwarding Profile Action](#forwarding-profile-action)
- [Step 2: Configure Proxy Settings for Users' Devices](#proxy-settings)
- [Step 3: Configure Zscaler Client Connector for Different Tunnel Modes](#tunnel-mode)
Recommendation for Using Tunnel (Route-Based) Forwarding Profile Action
[]If your organization decides to use **Tunnel (Route-Based)** as the forwarding profile action, follow these recommendations for different deployment modes to ensure users don't experience connectivity issues.
- [Full-Tunnel Mode](#tunnel-route-based-full-tunnel-mode)
- [Split-Tunnel Mode](#tunnel-route-based-split-tunnel-mode)
- [Firewall Functionality](#tunnel-route-based-firewall)
- [Trusted Network Criteria](#tunnel-route-based-trusted-network-criteria)
- [Troubleshooting Temporary Network Instability](#tunnel-route-based-troubleshooting)
[]To ensure maximum interoperability between the VPN client and Zscaler Client Connector, you must select the appropriate [forwarding profile action](/unified/configuring-forwarding-profiles-zscaler-client-connector) that determines if Zscaler Client Connector works at the network (IP) layer or the application layer to tunnel traffic (or whether Zscaler Client Connector tunnels traffic at all).
[](/unified/configuring-forwarding-profiles-zscaler-client-connector)[](/unified/configuring-forwarding-profiles-zscaler-client-connector)
| **Forwarding Profile Action** | **How Zscaler Client Connector Traffic** |
| ----------------------------- | ---------------------------------------- |
| Tunnel (Route-Based) as the Tunnel Driver Type | Tunnels traffic at the network (IP) layer and captures user traffic by setting IP routes on users’ devices. |
| Tunnel (Packet Filter Based) as the Tunnel Driver Type | Uses Windows packet filtering to send traffic directly to Zscaler Client Connector to process. |
| Tunnel with Local Proxy | Tunnels traffic to the application layer and captures traffic by applying proxy settings on users' devices.This option has advantages over the Enforce Proxy option because the app transparently handles authentication for users. Users don't have to reauthenticate for applications when they open new browsers and rarely run into issues accessing applications that aren't browser-based. |
| Enforce Proxy | Does not tunnel any traffic. Only sets proxy settings on the users' devices and prohibits users from changing those proxy settings. |
| None | Does not tunnel any traffic. Performs no actions on users' devices. |
To prevent interoperability issues, Zscaler recommends the following forwarding profile actions for the different platforms:
- [Windows and macOS](#recommended-forwarding-action-windows-macOS)
- [iOS](#recommended-forwarding-action-iOS)
- [Linux](#recommended-forwarding-action-linux)
For Android, you cannot run Zscaler Client Connector and any third-party VPN simultaneously because the Android OS only allows one concurrent VPN at a time.
[]You must ensure that the VPN client is not configured to change proxy settings on users’ devices (even if you select **Tunnel with Local Proxy** as the forwarding profile action for **VPN Trusted Network**). If VPN clients tamper with proxy settings in any way, Zscaler Client Connector does not forward traffic properly.
[]Your VPN can run in full-tunnel mode or split-tunnel mode, but each mode requires different Zscaler Client Connector configurations:
- [Full-Tunnel Mode](#full-tunnel-mode-config)
- [Split-Tunnel Mode](#split-tunnel-mode-config)
[]For Windows and macOS, Zscaler recommends you use the following settings:
- Windows:
- Full-Tunnel Mode: Only **Tunnel with Local Proxy**.
- Split-Tunnel Mode: Either **Tunnel with Local Proxy** or **Tunnel **(**Packet Filter Based**).
- macOS: Only **Tunnel with Local Proxy**.
Since Zscaler Client Connector works at the application layer for **Tunnel with Local Proxy** and **Tunnel** (**Packet Filter Based**) and doesn’t compete with the VPN client at the IP layer, users don’t experience interoperability issues. Instead, the app allows the VPN to take traffic as needed but sets proxy settings or packet filters to ensure that all user traffic is still protected by Zscaler.
Zscaler highly recommends that you don't select Tunnel (Route-Based) as the forwarding profile for VPN Trusted Network. Because Zscaler Client Connector works at the same IP layer as VPN clients for Tunnel mode, it may cause interoperability problems. To learn more, see [Recommendation for using Tunnel (Route-Based) Forwarding Profile Action](#recommendation-tunnel(route-based)-forwarding-profile-action) below.
[]For iOS, Zscaler recommends you use **Tunnel** for the forwarding profile action. The iOS platform allows multiple VPNs to run simultaneously, as long as each VPN is of a different type; personal, per-app, or enterprise. For example, Zscaler Client Connector runs as an enterprise VPN. So you can simultaneously run another personal or per-app VPN, but not an enterprise VPN.
Zscaler Client Connector for iOS does not support **Tunnel with Local Proxy**.
[]For Linux, Zscaler recommends using the following settings if your VPN runs in full-tunnel mode:
- [Forwarding Profile Action for ZIA](#forward-action-zia)
- [Forwarding Profile Action for ZPA](#forward-action-zpa)
[]Choose the following options based on the trusted network type:
- **On Trusted Network**: Select **Tunnel with Local Proxy**.
- **VPN Trusted Network: **Select **Same as "On Trusted Network"**.
- **Off-Trusted Network**: Select **Same as "On Trusted Network"**.
If Internet & SaaS experiences connection loss upon VPN startup, the VPN client may have failed to install the VPN bypass route for the Zscaler Client Connector administration site (e.g., the SME IP). If this occurs, add the SME IP to the **Hostname or IP Address Bypass for VPN Gateway** field in **App Profiles** in the Admin Portal.
[]Choose the following options based on the trusted network type:
- **On Trusted Network**: Select **Tunnel**.
- **VPN Trusted Network: **Select **None**.
- **Off-Trusted Network**: Select **Same as "On Trusted Network"**.
Disable the VPN client's route monitoring option (e.g., Cisco AnyConnect VPN).
[]When your VPN runs full-tunnel mode, all of your users’ traffic is routed to the VPN client. Zscaler Client Connector treats the network as a **VPN Trusted Network **and applies the forwarding profile action you chose for that network. However, the following important caveats apply to this configuration:
- Zscaler strongly recommends against using the forwarding profile Tunnel (Route-Based) for VPN Trusted Network. It can cause interoperability issues because Zscaler Client Connector in Tunnel mode works on the IP layer (the same layer as the VPN client). Zscaler recommends selecting **Tunnel with Local Proxy** in this scenario for Windows and macOS.
- If your VPN doesn't set a default route, select **Tunnel with Local Proxy**. Zscaler Client Connector detects a full tunnel VPN by looking for a default route in the routing table. If the VPN doesn’t set a default route and uses a different mechanism to capture all traffic, Zscaler Client Connector won't consider the VPN a full-tunnel VPN. It won't treat the user as connected to a VPN Trusted Network. Instead, the app treats the user as **Off Trusted Network** and applies the corresponding forwarding profile action.
- Zscaler Client Connector looks for the following words in the default interface description to detect a **VPN Trusted Network**: Cisco, Juniper, Fortinet, PanGP, Check Point, and VPN. If these words are missing, the app treats the user as **Off Trusted Network**.
[]When your VPN runs split-tunnel mode, only some of your users’ traffic is routed to the VPN client. For example, the VPN can set routes only for specific subnets, such as 10/8 or 192.168/16. Additionally, the VPN can set the DNS on the device to capture traffic for internal hosts. Zscaler Client Connector treats the device as **Off Trusted Network** and applies the forwarding profile action you chose for that network. For a simpler configuration, Zscaler recommends selecting **Tunnel with Local Proxy** or **Tunnel **(**Packet Filter Based**)** **in this scenario.
If you choose to run Zscaler Client Connector in Tunnel mode and your VPN runs split-tunnel mode, you must take steps to ensure that the app interoperates with your VPN client. To learn more, see [Recommendation for using Tunnel (Route-Based) Forwarding Profile Action](#recommendation-tunnel(route-based)-forwarding-profile-action) below.
[]If your VPN runs in full-tunnel mode, Zscaler strongly recommends against selecting **Tunnel** (**Route-Based**) for the forwarding profile action.
[]If your VPN runs in split-tunnel mode:
- [Allow traffic destined for the VPN gateway to bypass Zscaler Client Connector.](#allow-traffic-bypass-Z-App)
- [Ensure that any DNS used by the VPN can resolve both internal and external domains.](#ensure-DNS-resolves-domains)
[]When you select **Tunnel** (**Route-Based**) and your VPN runs split-tunnel mode, Zscaler Client Connector can only forward traffic properly if you allow traffic destined for the VPN gateway to bypass Zscaler Client Connector.
To configure this, you must specify the hostnames and IP addresses for all your VPN gateways in the **Hostname or IP Address Bypass for VPN Gateway** field when you configure the [app profile](/unified/configuring-zscaler-client-connector-app-profiles). Zscaler Client Connector sets the routing table to exclude all traffic destined for the VPN gateway, ensuring that this traffic is allowed to bypass the app tunnel and properly go to the VPN.
To ensure against connectivity issues, it's critical that you include all VPN hostnames or all IP addresses to which these hostnames can be resolved.
[]On Windows devices, when Zscaler Client Connector runs in **Tunnel** (**Route-Based**) mode, the app sets the DNS on the interface to point to 100.64.0.3, 100.64.0.4, and 100.64.0.5. When a user launches a VPN connection, the app detects this network change and responds accordingly.
If the VPN client runs in split-tunnel mode, Zscaler Client Connector applies the forwarding profile action for **Off Trusted Network**. While this is the expected behavior, sometimes the following scenario can occur even when you configure the DNS to resolve only internal domains: Upon launch, the VPN client sets its own DNS on the interface to make it the prioritized DNS to resolve internal domains. Zscaler Client Connector detects this change and reverts it, so that 100.64.0.3 (Zscaler's DNS) is again the prioritized DNS for the user device. However, the app redirects any DNS query that comes to 100.64.0.3 to the original prioritized DNS (i.e., the VPN client DNS).
At this point, if the DNS query is for an external domain, and the original VPN DNS is configured only to resolve internal domains, the DNS query should continue to be redirected to the next DNS in the priority list, until it finds a server that can resolve the requested external domain.
However, some Windows programs do not redirect DNS queries to the next DNS in the priority list. In this scenario, the DNS query can't find a server to resolve the requested external domain, and the user can't reach the external domain. To prevent this, ensure that all VPN clients set the DNS so that they can resolve both internal and external domains.
If a third-party VPN operates in split-tunnel mode, you must configure DNS search domains in the VPN connection profile. Otherwise, Zscaler Client Connector intercepts the VPN connection's DNS requests and forwards them to the system DNS server, which might be unable to resolve the VPN domains.
[]If your VPN has any firewall functionality, you must disable it or allowlist Zscaler Client Connector in the firewall. Otherwise, the VPN firewall can interfere with app tunnel processes.
[]When configuring the Trusted Network Criteria for your forwarding profile, Zscaler recommends that you select **DNS Server** and **DNS Search Domain**. To learn more, see [Trusted Network Criteria](/unified/configuring-forwarding-profiles-zscaler-client-connector).
[]Keep in mind that users can see some momentary network instability when a VPN client initially launches while Zscaler Client Connector is running.
On Windows devices, when Zscaler Client Connector runs in **Tunnel** (**Route-Based**), the app sets the DNS on the interface to point to 100.64.0.3, 100.64.0.4, and 100.64.0.5. When a user launches a VPN connection, the app detects this network change and responds accordingly. If the VPN client runs in full-tunnel mode, the app removes all of its own DNS settings to allow all traffic to properly go to the VPN. If the VPN client runs in split-tunnel mode, the app reconfigures DNS settings so it can properly apply the forwarding profile action for **Off Trusted Network**.
While that is the ultimate expected outcome, the user can experience some temporary network instability. When the app removes its own DNS settings, this is detected as a network change by the VPN client. In response, the VPN client can disconnect and attempt to reestablish the connection. The user can experience some connectivity issues until this process is complete and the app and VPN client reach equilibrium.