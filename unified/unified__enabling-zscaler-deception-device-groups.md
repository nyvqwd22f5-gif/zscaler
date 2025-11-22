# Enabling Zscaler Deception for Device Groups
Source: https://help.zscaler.com/unified/enabling-zscaler-deception-device-groups
PDF: https://help.zscaler.com/pdf/com/en/1491171.pdf

You can use Zscaler Service Entitlement to enroll Device Groups in Zscaler Deception. Configuring Deception for device groups allows you to assign entitlements and policy settings based on ownership through device posture profiles. For example, one user can have two devices, one personal and one employer-provided. The personal device can be enrolled in Deception and the employer-provided device can be enrolled in Deception and Private Applications.
To enable Zscaler Deception for device groups, you must install Zscaler Client Connector 3.9 or later.
Enabling Zscaler Deception for Device Groups
To enable Zscaler Deception for device groups:
- In the Admin Portal, go to **Administration > Entitlements > Deception**.
- To enable Deception for device groups, ensure that **Zscaler Deception Enabled by Default **is disabled. If this setting is enabled, Deception is available for all users and you cannot assign Deception to a device group.
- Select one or more groups from the **Device Groups **drop-down menu.
Groups are defined in the Device Groups section in the Admin Portal under Infrastructure. For more information, see [About Device Groups](/unified/about-device-groups).
- Select **Logout Zscaler Client Connector when Zscaler Deception Entitlement is Enabled **to automatically log users out of Zscaler Client Connector when Deception is enabled for a device group. Users can then log in again to enable the Deception service. This applies to customers using Private Applications only. When not enabled, Zscaler Client Connector runs without the Deception service until the next Zscaler Client Connector login.
![Enable ZDX for Device Groups](/downloads/z-app/policy-administration-settings/zscaler-service-entitlement/enabling-zscaler-deception-device-groups/Deception_device_grps.png)
- Click **Save**.
Your users’ devices are updated the next time they connect. If users are already connected, devices automatically update in 60 minutes. Users can manually update their devices in Zscaler Client Connector. On the **More **page, click **Update Policy**. After manually refreshing the device, they must reauthenticate on the **Private Access** page.