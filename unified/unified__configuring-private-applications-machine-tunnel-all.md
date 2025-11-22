# Configuring Private Applications Machine Tunnel for All
Source: https://help.zscaler.com/unified/configuring-private-applications-machine-tunnel-all
PDF: https://help.zscaler.com/pdf/com/en/1491101.pdf

Zscaler Client Connector provides tunnel settings for Private Applications in the [Zscaler Service Entitlement](/unified/about-zscaler-service-entitlement) page.
The user tunnel settings determine which users can access Private Applications when logged in to Zscaler Client Connector. If **ZPA Enabled by Default for User Tunnel** is enabled, the Private Applications service is available for all users. If this setting is disabled, you can enable the Private Applications service for a select group of users or for device groups.
You can also configure a machine tunnel to establish a connection to Private Applications before users log in to Zscaler Client Connector on a Windows or macOS device. If **Enable Machine Tunnel For All** is enabled, all users with a **Machine Token** configured in the [app profile](/unified/configuring-zscaler-client-connector-app-profiles) can establish a connection to Private Applications without being logged in. To learn more, see [About Machine Tunnels](/unified/about-machine-tunnels).
If **Enable Machine Tunnel For All** is disabled, any existing machine tunnels remain connected until a user’s app profile policy is updated and the user logs out.
To configure the machine tunnel for all devices:
- Go to **Administration > Entitlements > Private Access**.
-
Enable or disable the **Enable Machine Tunnel For All**.
![Configure Machine Tunnel for All](/downloads/client-connector/zscaler-service-entitlement/selective-entitlement-configuring-zpa-machine-tunnel-all/zscaler-client-connector-enable-machine-tunnel_0.png)
- Click **Save**.