# Enabling Private Applications for Device Groups
Source: https://help.zscaler.com/unified/enabling-private-applications-device-groups
PDF: https://help.zscaler.com/pdf/com/en/1491161.pdf

You can use Zscaler Service Entitlement to enroll Device Groups in Private Applications. Configuring Private Applications using device groups allows you to assign entitlements and policy settings based on ownership through device posture profiles. For example, one user can have two devices, one personal and one employer-provided. The personal device can be enrolled in Private Applications, and the employer-provided device can be enrolled in Private Applications and Internet & SaaS.
When using device groups, the user must belong to both the device group and user group to avoid disconnecting Private Applications services.
To enable Private Applications for device groups:
- In the Admin Portal, go to **Administration > Entitlements > Private Access.**
- To enable Private Applications for device groups, ensure that **ZPA Enabled by Default for User Tunnel **is disabled. If this setting is enabled, Private Applications is available for all users and you cannot assign Private Applications to a group.
-
Enable **Device Groups **and select one or more groups from the drop-down menu.
Groups are defined in the Device Groups section in the Admin Portal under Infrastructure. For more information, see [About Device Groups](/unified/about-device-groups).
![Enable ZPA for Device Groups](/downloads/tech-pubs-drafts/client-connector-draft-articles/enabling-zpa-device-groups-doc-56322/image1.png)
- Click **Save**.
Your users' devices are updated the next time they connect. If they're already connected, devices automatically update in 60 minutes. Users can manually update their devices in Zscaler Client Connector by clicking **Update Policy **in the **More **window. After manually refreshing the device, they must reauthenticate on the **Private Access** page.