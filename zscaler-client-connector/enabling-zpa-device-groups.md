# Enabling ZPA for Device Groups
Source: https://help.zscaler.com/zscaler-client-connector/enabling-zpa-device-groups
PDF: https://help.zscaler.com/pdf/com/en/1409571.pdf

You can use Zscaler Service Entitlement to enroll device groups in Zscaler Private Access (ZPA). Configuring ZPA using device groups allows you to assign entitlements and policy settings based on ownership through device posture profiles. For example, one user can have two devices, one personal and one employer-provided. The personal device can be enrolled in ZPA, and the employer-provided device can be enrolled in ZPA and Zscaler Internet Access (ZIA).
When using device groups, the user must belong to both the device group and user group to avoid disconnecting ZPA services.
To enable ZPA for device groups:
- In the Zscaler Client Connector Portal, go to **Administration **> **Zscaler Service Entitlement**.
- Click the **Zscaler Private Access (ZPA) **tab.
- To enable ZPA for device groups, ensure that **ZPA Enabled by Default for User Tunnel **is disabled. If this setting is enabled, ZPA is available for all users and you cannot assign ZPA to a group.
- Enable **Device Groups **and select one or more groups from the drop-down menu.
Groups are defined in the Device Groups section in the Zscaler Client Connector Portal under Administration. For more information, see [About Device Groups](/zscaler-client-connector/about-device-groups-0).
![Enable ZPA for Device Groups](/downloads/tech-pubs-drafts/client-connector-draft-articles/enabling-zpa-device-groups-doc-56322/image1.png)
- Click **Save**.
Your users' devices are updated the next time they connect. If they're already connected, devices automatically update in 60 minutes. Users can manually update their devices in Zscaler Client Connector by clicking **Update Policy **in the **More **window. After manually refreshing the device, they must reauthenticate on the Private Access page.