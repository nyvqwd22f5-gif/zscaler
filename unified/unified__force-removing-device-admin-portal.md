# Force Removing a Device from the Admin Portal
Source: https://help.zscaler.com/unified/force-removing-device-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1496596.pdf

From the Admin Portal, you can force remove devices to remove them from the portal. You can only force remove devices one at a time. If you want to remove multiple devices at once, see [Soft Removing a Device from the Admin Portal](/unified/soft-removing-device-admin-portal). You can also configure the Admin Portal to automatically remove devices. To learn how to configure the number of devices threshold, see [Configuring Automated Device Cleanup](/unified/configuring-automated-device-cleanup).
When you remove a device, Zscaler Client Connector logs out the user but does not uninstall the app from the device. To uninstall the app, see [Uninstalling Zscaler Client Connector](/unified/uninstalling-zscaler-client-connector).
To force remove a device:
- Go to **Infrastructure > Connectors > Client > Device Overview**.
- Click the **Device Details** icon next to the device that you want to remove the app from. You can only force remove devices with the device states of Registered and Removal Pending.
- Click **Force Remove**.
The device is removed immediately and the device state changes to **Removed**. After a device is successfully force removed, the user might experience service interruption or authentication errors.