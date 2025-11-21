# Force Removing a Device from the Zscaler Client Connector Portal
Source: https://help.zscaler.com/zscaler-client-connector/force-removing-device-zscaler-client-connector-portal
PDF: https://help.zscaler.com/pdf/com/en/1408176.pdf

From the Zscaler Client Connector Portal, you can force remove devices to remove them from the portal. You can only force remove devices one at a time. If you want to remove multiple devices at once, see [Soft Removing a Device from Zscaler Client Connector Portal](/zscaler-client-connector/soft-removing-device-zscaler-client-connector-portal). You can also configure the Zscaler Client Connector Portal to automatically remove devices. To learn how to configure the number of devices threshold, see [Configuring Automated Device Removal](/zscaler-client-connector/configuring-automated-device-removal).
When you remove a device, Zscaler Client Connector logs out the user but does not uninstall the app from the device. To uninstall the app, see [Uninstalling Zscaler Client Connector](/zscaler-client-connector/uninstalling-zscaler-client-connector).
To force remove a device:
- In the Zscaler Client Connector Portal, click **Enrolled Devices**.
- In the left-side navigation, click **Device Overview**.
- Click the **Device Details** icon next to the device that you want to remove the app from. You can only force remove devices with the device states of Registered and Removal Pending.
![The device details icon for a device in the Zscaler Client Connector Portal](/downloads/z-app/policy-administration-settings/force-removing-device-zscaler-client-connector-portal/device%20state_0.png)
- Click **Force Remove**.
![The Force Remove button for a device in the Zscaler Client Connector Portal](/downloads/tech-pubs-drafts/miscellaneous-draft-articles/force-removing-device-zscaler-client-connector-portal/force-remove.png)
The device is removed immediately and the device state changes to **Removed**. After a device is successfully force removed, the user might experience service interruption or authentication errors.