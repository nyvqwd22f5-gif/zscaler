# Enabling Digital Experience Monitoring for Device Groups
Source: https://help.zscaler.com/unified/enabling-digital-experience-monitoring-device-groups
PDF: https://help.zscaler.com/pdf/com/en/1491181.pdf

You can use Zscaler Service Entitlement to enroll Device Groups in Digital Experience Monitoring. Configuring Digital Experience Monitoring for device groups allows you to assign entitlements and policy settings based on ownership through device posture profiles. For example, one user can have two devices, one personal and one employer-provided. The personal device can be enrolled in Digital Experience Monitoring, and the employer-provided device can be enrolled in Digital Experience Monitoring and Private Applications.
To enable Digital Experience Monitoring for device groups, you must deploy Zscaler Client Connector 3.9 or later.
Enabling Digital Experience Monitoring for Device Groups
To enable Digital Experience Monitoring for device groups:
- In the Admin Portal, go to **Administration > Entitlements > Digital Experience**.
- To enable Digital Experience Monitoring for device groups, ensure that **ZDX Enabled by Default** is disabled. If this setting is enabled, Digital Experience Monitoring is available for all users and you cannot assign Digital Experience Monitoring to a device group.
- To configure user groups, see [Enabling Digital Experience Monitoring for a Group of Users](/unified/enabling-digital-experience-monitoring-group-users).
- Select one or more groups from the **Device Groups **drop-down menu.
Groups are defined in the Device Groups section in the Admin Portal under Infrastructure. For more information, see [About Device Groups](/unified/about-device-groups).
- Select **Logout ZCC when ZDX Entitlement is Enabled **to automatically log users out of Zscaler Client Connector when Digital Experience Monitoring is enabled for a device group. Users can then log in again to enable the Digital Experience Monitoring service. This applies to customers using Private Applications only or Private Applications and Zscaler Deception. When disabled, Zscaler Client Connector runs without the Digital Experience Monitoring service until the next Zscaler Client Connector login.
![Enable ZDX for Device Groups](/downloads/tech-pubs-drafts/client-connector-draft-articles/enabling-zdx-device-groups/Client_Connector_ZDX_Device_Grps_5.png)
- Click **Save**.
Your users' devices are updated the next time they connect. If users are already connected, devices automatically update in 60 minutes. Users can manually update their devices in Zscaler Client Connector. On the **More **page, click **Update Policy**. After manually refreshing the device, they must reauthenticate on the **Private Access** page.