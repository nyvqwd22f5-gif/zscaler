# Enabling ZDX for Device Groups
Source: https://help.zscaler.com/zscaler-client-connector/enabling-zdx-device-groups
PDF: https://help.zscaler.com/pdf/com/en/1411311.pdf

You can use Zscaler Service Entitlement to enroll Device Groups in Zscaler Digital Experience (ZDX). Configuring ZDX for device groups allows you to assign entitlements and policy settings based on ownership through device posture profiles. For example, one user can have two devices, one personal and one employer-provided. The personal device can be enrolled in ZDX, and the employer-provided device can be enrolled in ZDX and Zscaler Private Access (ZPA).
To enable ZDX for device groups, you must deploy Zscaler Client Connector 3.9 or later.
Enabling ZDX for Device Groups
To enable ZDX for device groups:
- In the Zscaler Client Connector Portal, go to **Administration**.
- In the left menu, select **Zscaler Service Entitlement**.
- Click the **Zscaler Digital Experience** **(ZDX) **tab.
- To enable ZDX for device groups, ensure that **ZDX Enabled by Default** is disabled. If this setting is enabled, ZDX is available for all users and you cannot assign ZDX to a device group.
- To configure user groups, see [Enabling ZDX for a Group of Users](/zscaler-client-connector/selective-entitlement-enabling-zdx-group-users).
- Select one or more groups from the **Device Groups **drop-down menu.
Groups are defined in the Device Groups section in the Zscaler Client Connector Portal under Administration. For more information, see [About Device Groups](/zscaler-client-connector/about-device-groups-0).
- Select **Logout ZCC when ZDX Entitlement is Enabled **to automatically log users out of Zscaler Client Connector when ZDX is enabled for a device group. Users can then log in again to enable the ZDX service. This applies to customers using ZPA only or ZPA and Zscaler Deception. When disabled, Zscaler Client Connector runs without the ZDX service until the next Zscaler Client Connector login.​​​​​​
![Enable ZDX for Device Groups](/downloads/tech-pubs-drafts/client-connector-draft-articles/enabling-zdx-device-groups/Client_Connector_ZDX_Device_Grps_5.png)
- Click **Save**.
Your users' devices are updated the next time they connect. If users are already connected, devices automatically update in 60 minutes. Users can manually update their devices in Zscaler Client Connector. On the **More **page, click **Update Policy**. After manually refreshing the device, they must reauthenticate on the **Private Access** page.