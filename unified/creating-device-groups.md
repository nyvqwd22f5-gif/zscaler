# Creating Device Groups
Source: https://help.zscaler.com/unified/creating-device-groups
PDF: https://help.zscaler.com/pdf/com/en/1491136.pdf

You can create device groups based on device posture profiles. Assign these groups to policies and [service entitlements](/unified/about-zscaler-service-entitlement), such as enrolling device groups in Private Applications, Internet & SaaS, Digital Experience Monitoring, and Zscaler Deception. You can add up to 4 device groups. To learn more, see [About Device Groups](/unified/about-device-groups).
To create device groups for Android, you must first enable** Use Device Groups in Service Entitlement** on the Android tab in **Platform Settings**.
- In the Admin Portal, go to **Infrastructure > Common Resources > Device Groups**.
- Click **Add Device Group**.
The **Add Device Group** window appears.
-
In the **Add Device Group** window:
- **Define Device Group: **Enter a name for the device group.
- **Platform**: Select the applicable platforms.
- **Device Group Configuration**: Select one or more device postures from the **Select Device Posture** drop-down menu.
- When selecting multiple device postures, the `AND` operator is added after each device posture. Click out of the drop-down menu when finished selecting device postures.
- (Optional) Click **Add **to use the `OR` operator and then select a device posture from the drop-down menu. Click out of the drop-down menu when finished selecting a device posture. You can continue to add up to 5 device postures.
- Review your expression in **Expression Preview**. Within a group, the logic is `AND`. Between groups, the logic is `OR`.
- (Optional) **Device Group Description**: Add a description of the device group.
![Add Device Group in the Zscaler Client Connector Portal](/downloads/tech-pubs-drafts/client-connector-draft-articles/creating-device-groups-doc-56526-revised/Device_groups_one.png)
- Click **Save**.