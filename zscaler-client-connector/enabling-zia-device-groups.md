# Enabling ZIA for Device Groups
Source: https://help.zscaler.com/zscaler-client-connector/enabling-zia-device-groups
PDF: https://help.zscaler.com/pdf/com/en/1411316.pdf

You can use Zscaler Service Entitlement to enroll Device Groups in Zscaler Internet Access (ZIA). Configuring ZIA using device groups allows you to assign entitlements and policy settings based on ownership through device posture profiles. For example, one user can have two devices, one personal and one employer-provided. The personal device can be enrolled in ZIA, and the employer-provided device can be enrolled in ZIA and Zscaler Private Access (ZPA).
To enable ZIA for device groups, you must deploy Zscaler Client Connector 3.9 or later. Contact Zscaler Support to enable this feature.
Enabling ZIA for Device Groups
To enable ZIA for device groups:
- In the Zscaler Client Connector Portal, go to **Administration**.
- In the left menu, select **Zscaler Service Entitlement**.
- Click the **Zscaler Internet Access (ZIA) **tab.
- To enable ZIA for device groups, ensure that **ZIA Enabled by Default **is disabled. If this setting is enabled, ZIA is available for all users and you cannot assign ZIA to a device group.
- Select one or more groups from the **Device Groups** drop-down menu.
Groups are defined in the Device Groups section in the Zscaler Client Connector Portal under Administration. For more information, see [About Device Groups](/zscaler-client-connector/about-device-groups-0).
- Select **Logout ZCC when ZIA Entitlement is Enabled **to automatically log users out of Zscaler Client Connector when ZIA is enabled for a device group. Users can then log in again to enable the ZIA service. This applies to customers using ZPA only or ZPA and Zscaler Deception. When disabled, Zscaler Client Connector runs without the ZIA service until the next Zscaler Client Connector login.
![Enable ZIA for Device Groups](/downloads/tech-pubs-drafts/client-connector-draft-articles/enabling-zia-device-groups/Client_Connector_ZIA_Entitlement_1.png)
- Click **Save**.
Your users' devices are updated the next time they connect. If they're already connected, devices automatically update in 60 minutes. Users can manually update their devices in Zscaler Client Connector. On the **More **page, click **Update Policy**. After manually refreshing the device, they must reauthenticate on the** Private Access** page.