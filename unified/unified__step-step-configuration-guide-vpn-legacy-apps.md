# Step-by-Step Configuration Guide for VPN (for Legacy Apps)
Source: https://help.zscaler.com/unified/step-step-configuration-guide-vpn-legacy-apps
PDF: https://help.zscaler.com/pdf/com/en/1532356.pdf

This guide takes you through the configuration steps for using VPN (for Legacy Apps) for your organization.
Prerequisites
Before the feature can be enabled, make sure that you have:
-
A RedHat Enterprise Linux (RHEL) 9 server with a static, private IP address for installing a Network Connector. The FIPS module must be disabled.
[See instructions.](#ConfigureRHEL9)
- A private IP address range for the VPN client's IP address pool. The IP address range must not overlap with existing subnets.
- A route from the servers to the VPN Service Edge's client IP address pools using a Network Connector’s IP address as the next hop.
- Ensure that the Network Connector has a route to reach Network Segments (the server) that need to be accessed via VPN.
- An outbound firewall rule for each Network Connector to the internet. If traffic from the Network Connector to the internet needs to be restricted, allow at a minimum a UDP destination port of 51820 to VPN Service Edges and traffic to the Zero Trust Exchange (ZTE) cloud. To learn more, see [Zscaler Private Access (ZPA) Firewall Whitelist](https://config.zscaler.com/private.zscaler.com/zpa) for ZPA ONE or [Zscaler Private Access (ZPA) Firewall Whitelist](https://config.zscaler.com/zpatwo.net/zpa) for ZPA TWO.
VPN (for Legacy Apps) is available to users running supported Zscaler Client Connector versions.
[]On the RHEL 9 server with a static IP address, configure the following:
-
Enable traffic forwarding to route traffic:
`$ sudo sysctl -w net.ipv4.ip_forward=1`
Ensure that traffic forwarding settings persist after a reboot.
-
Log in as `root` and edit the `/etc/sysctl.conf` file:
`net.ipv4.ip_forward = 1`
- Restart the server.
-
Verify that `net.ipv4.ip_forward` is set to `1` after restarting:
`$ sudo sysctl -a  | grep net.ipv4.ip_forward
net.ipv4.ip_forward = 1`
-
Ensure that `#includedir /etc/sudoers.d` is included in the `/etc/sudoers` directory:
`$ sudo cat /etc/sudoers | grep includedir
#includedir /etc/sudoers.d`
-
Ensure that FIPS is not enabled:
`$  sudo fips-mode-setup --check`
If a message of `Installation of FIPS modules is not completed` is returned, FIPS is not disabled.
To disable FIPS:
`$ sudo  fips-mode-setup --disable`
Configuring VPN (for Legacy Apps)
To configure VPN (for Legacy Apps):
- [Step 1: Configuring User Enablement](#Step-ConfigureUserEnablement)
- [Step 2: Configuring a VPN Service Edge](#Step-CreateVPNServiceEdge)
- [Step 3: Adding a Network Connector](#Step-CreateNetworkConn)
- [Step 4: Deploying the Network Connector](#Step-DeployNetworkConn)
- [Step 5: Verifying the Network Connector is added](#VerifyNetworkConnector)
- [Step 6: Adding Network Segments](#Step-AddNetworkSegment)
- [Step 7: Configuring the Client Connector App Profile Bypass VPN Service Edge](#ConfigureAppProfile)
- [Step 8: Verifying Connected Users](#VerifyUserConnections)
[]VPN user enablement lets you create VPN rules to manage access to the tunnels. To configure a user enablement rule, you must first define the users. For this step, define the SAML or SCIM attributes for users of VPN (for Legacy Apps). You can also add a posture profile validation in user enablement.
To configure user enablement, see the following articles:
- [About VPN User Enablement](/unified/about-vpn-user-enablement)
- [Configuring VPN User Enablement](/unified/configuring-vpn-user-enablement)
[See image.](#UserEnablement)
[]VPN Service Edges manage the connections between Zscaler Client Connector and Network Connectors. Create a VPN Service Edge to specify a service region and provision the client IP pool.
You can use one VPN Service Edge for a tenant, with a default of three VPN Service Edges. Each VPN Service Edge requires a different client IP pool.
To create VPN Service Edges and review recommendations, see the following articles:
- [About VPN Service Edges](/unified/about-vpn-service-edges)
- [Configuring VPN Service Edges](/unified/configuring-vpn-service-edges)
[]Network Connectors build a secure VPN tunnel that connects applications to VPN Service Edges. You can configure a single Network Connector per Network Connector group.
When creating the provisioning key, use an intuitive name such as the group name.
To create Network Connectors and review recommendations, see the following articles:
- [About Network Connectors](/unified/about-network-connectors)
- [Configuring Network Connectors](/unified/configuring-network-connectors)
[]On a RedHat Linux (RHEL) 9 machine with a static IP address, ensure you have met all Network Connector deployment prerequisites and deploy the Network Connector.
To deploy Network Connectors, see the following articles:
- [Network Connector Deployment Prerequisites](/unified/network-connector-deployment-prerequisites)
- [Network Connector Deployment Guide for Linux](/unified/network-connector-deployment-guide-linux)
[]After deploying the Network Connector, applying the provisioning key, and restarting the service in the previous step, go to the Network Connectors page to verify that the Network Connector appears in the table. To learn more, see [About Network Connectors](/zpa/about-network-connectors).
[]A Network segment is a local area network (LAN) IP subnet that is assigned to a Network Connector group to define access to servers that are accessed via the VPN tunnel.
To add a Network segment, see the following articles:
- [About Network Segments](/unified/about-network-segments)
- [Configuring Network Segments](/unified/configuring-network-segments)
[]Copy the IP address for a VPN Service Edge from the VPN Service Edges page to the **Hostname or IP Address Bypass for VPN Gateway**.
To configure the Client Connector App Profile Bypass:
- [About VPN Service Edges](/unified/about-vpn-service-edges)
- [Configuring Zscaler Client Connector App Profiles](/unified/configuring-zscaler-client-connector-app-profiles#global)
[See image.](#AppProfileBypass)
[]Verify that users can successfully connect to the VPN Service Edge. To learn more, see [About VPN Connected Users](/unified/about-vpn-connected-users).
[See image.](#VerifyUsers)
[]
[]![Example of User Enablement for VPN (for Legacy Apps)](/downloads/zpa/step-step-configuration-guide-vpn-legacy-apps/vpn-user-enablement_0.png)
![VPN (for Legacy Apps) User Enablement Page with Device Posture](/downloads/zpa/step-step-configuration-guide-vpn-legacy-apps/vpn-user-enablement-device-posture_0.png)
[]![Example of User Enablement for VPN (for Legacy Apps)](/downloads/zpa/step-step-configuration-guide-vpn-legacy-apps/zpa-edit-windows-policy_1.png)
[]![Example of User Enablement for VPN (for Legacy Apps)](/downloads/zpa/step-step-configuration-guide-vpn-legacy-apps/vpn-verify-connected-user.png)