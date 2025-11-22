# Configuring ZPA Machine Tunnel for All
Source: https://help.zscaler.com/zscaler-client-connector/configuring-zpa-machine-tunnel-all
PDF: https://help.zscaler.com/pdf/com/en/1380151.pdf

Zscaler Client Connector provides tunnel settings for Zscaler Private Access (ZPA) in the [Zscaler Service Entitlement](/zscaler-client-connector/about-zscaler-service-entitlement) page.
The user tunnel settings determine which users can access ZPA when logged in to Zscaler Client Connector. If **ZPA Enabled by Default for User Tunnel** is enabled, the ZPA service is available for all users. If this setting is disabled, you can enable the ZPA service for a select group of users or for device groups.
You can also configure a machine tunnel to establish a connection to ZPA before users log in to Zscaler Client Connector on a Windows or macOS device. If **Enable Machine Tunnel For All** is enabled, all users with a **Machine Token** configured in the [app profile](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles) can establish a connection to ZPA without being logged in. To learn more, see [About Machine Tunnels](/zscaler-client-connector/about-machine-tunnels).
If **Enable Machine Tunnel For All** is disabled, any existing machine tunnels remain connected until a user’s app profile policy is updated and the user logs out.
To configure the machine tunnel for all devices:
- In the Zscaler Client Connector Portal, go to **Administration**.
- From the left-side navigation, select **Zscaler Service Entitlement**.
- On the **Zscaler Private Access (ZPA)** tab, enable or disable **Enable Machine Tunnel for All**.
![Configure Machine Tunnel for All](/downloads/client-connector/zscaler-service-entitlement/selective-entitlement-configuring-zpa-machine-tunnel-all/zscaler-client-connector-enable-machine-tunnel_0.png)
- Click **Save**.