# Enabling Internet & SaaS for Device Groups
Source: https://help.zscaler.com/unified/enabling-internet-saas-device-groups
PDF: https://help.zscaler.com/pdf/com/en/1491186.pdf

You can use Zscaler Service Entitlement to enroll Device Groups in Internet & SaaS. Configuring Internet & SaaS using device groups allows you to assign entitlements and policy settings based on ownership through device posture profiles. For example, one user can have two devices, one personal and one employer-provided. The personal device can be enrolled in Internet & SaaS, and the employer-provided device can be enrolled in Internet & SaaS and Private Applications.
To enable Internet & SaaS for device groups, you must deploy Zscaler Client Connector 3.9 or later.
Enabling Internet & SaaS for Device Groups
To enable Internet & SaaS for device groups:
- In the Admin Portal, go to **Administration > Entitlements > Internet Access**.
- To enable Internet & SaaS for device groups, ensure that **ZIA Enabled by Default **is disabled. If this setting is enabled, Internet & SaaS is available for all users and you cannot assign Internet & SaaS to a device group.
- Select one or more groups from the **Device Groups** drop-down menu.
Groups are defined in the Device Groups section in the Admin Portal under Infrastructure. For more information, see [About Device Groups](/unified/about-device-groups).
- Select **Logout ZCC when ZIA Entitlement is Enabled **to automatically log users out of Zscaler Client Connector when Internet & SaaS is enabled for a device group. Users can then log in again to enable the Internet & SaaS service. This applies to customers using Private Applications only or Private Applications and Zscaler Deception. When disabled, Zscaler Client Connector runs without the Internet & SaaS service until the next Zscaler Client Connector login.
![Enable ZIA for Device Groups](/downloads/tech-pubs-drafts/client-connector-draft-articles/enabling-zia-device-groups/Client_Connector_ZIA_Entitlement_1.png)
- Click **Save**.
Your users' devices are updated the next time they connect. If they're already connected, devices automatically update in 60 minutes. Users can manually update their devices in Zscaler Client Connector. On the **More **page, click **Update Policy**. After manually refreshing the device, they must reauthenticate on the** Private Access** page.