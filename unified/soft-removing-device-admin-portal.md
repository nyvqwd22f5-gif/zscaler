# Soft Removing a Device from the Admin Portal
Source: https://help.zscaler.com/unified/soft-removing-device-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1496591.pdf

This article provides instructions on how to soft remove a device from the Admin Portal as an admin. Soft removing a device does not immediately remove it from the portal. To force remove a device, see [Force Removing a Device from the Admin Portal](/unified/force-removing-device-admin-portal). When you remove a device, Zscaler Client Connector logs out the user but does not uninstall the app from the device. To uninstall the app, see [Uninstalling Zscaler Client Connector](/unified/uninstalling-zscaler-client-connector).
After soft removal, the following circumstances may require you to [force remove](/unified/force-removing-device-admin-portal) a device:
-
The device state of **Device Removal Pending** stays on the **Device Overview** page for more than a day. This means that the user is inactive. If the user becomes active, Zscaler Client Connector sends a keepalive and logs out the user automatically.
A device can be in Device Removal Pending if the admin soft removed the device from the portal or [removed the user](/zidentity/about-users) in ZIdentity for Internet & SaaS.
- Zscaler Client Connector fails to send the keepalive or Zscaler Client Connector is uninstalled before the keepalive is sent.
To soft remove a device from the Admin Portal:
- Go to **Infrastructure > Connectors > Client > Device Overview**.
- Search for the device you want to remove.
- Select the checkbox and click **Delete** from the **Actions** drop-down menu. The device state changes to **Removal Pending**.
![client-connector-soft-remove-enrolled-device.png](/downloads/unified/infrastructure/client-connector/enrolled-devices/soft-removing-device-admin-portal/client-connector-soft-remove-enrolled-device.png)
After the update is complete, typically in one hour, the **Removal Pending** device state changes to **Removed**, and the device is removed from the portal.
Device removal can take up to an hour. The end user can click **Update Policy** on the More window in the app to immediately remove the device from Zscaler Client Connector.