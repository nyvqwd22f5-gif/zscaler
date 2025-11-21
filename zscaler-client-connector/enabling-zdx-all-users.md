# Enabling ZDX for All Users
Source: https://help.zscaler.com/zscaler-client-connector/enabling-zdx-all-users
PDF: https://help.zscaler.com/pdf/com/en/1497836.pdf

You can use Zscaler Service Entitlement to enable ZDX for all users.
Enabling ZDX for All Users
To enable ZDX for all users:
- In the Zscaler Client Connector Portal, go to **Administration**.
- From the left-side navigation, select **Zscaler Service Entitlement**.
- Click the **Zscaler Digital Experience **tab.
- To enable ZDX for all users, ensure that **ZDX Enabled by Default** is enabled. If this setting is disabled and posture based service feature is enabled, you can enable [ZDX for Device Groups](/zscaler-client-connector/enabling-zdx-device-groups).
![Configure ZDX user groups for Zscaler Service Entitlement](/downloads/client-connector/zscaler-service-entitlement/enabling-zdx-all-users/ZSclientconnector-ZDX-enabled-by-default.png)
5. Click **Save**.
This updates your users' devices the next time they connect. If they are already connected, the devices automatically update in 60 minutes. To manually update their devices, users can go into Zscaler Client Connector and click **Update Policy** from the **More** window. After manually refreshing, they must reauthenticate on the **Digital Experience** window.