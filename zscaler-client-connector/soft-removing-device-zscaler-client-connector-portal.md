# Soft Removing a Device from the Zscaler Client Connector Portal
Source: https://help.zscaler.com/zscaler-client-connector/soft-removing-device-zscaler-client-connector-portal
PDF: https://help.zscaler.com/pdf/com/en/1390891.pdf

This article provides instructions on how to soft remove a device from the Zscaler Client Connector Portal as an admin. Soft removing a device does not immediately remove it from the portal. To force remove a device, see [Force Removing a Device from the Zscaler Client Connector Portal](/zscaler-client-connector/force-removing-device-zscaler-client-connector-portal). When you remove a device, Zscaler Client Connector logs out the user but does not uninstall the app from the device. To uninstall the app, see [Uninstalling Zscaler Client Connector](/zscaler-client-connector/uninstalling-zscaler-client-connector).
After soft removal, the following circumstances may require you to [force remove](/zscaler-client-connector/force-removing-device-zscaler-client-connector-portal) a device:
- The device state of **Device Removal Pending** stays on the **Device Overview** page for more than a day. This means that the user is inactive. If the user becomes active, Zscaler Client Connector sends a keepalive and logs out the user automatically.
A device can be in Device Removal Pending if the admin soft removed the device from the portal or [removed the user from User Management](/zia/deleting-users) in Zscaler Internet Access (ZIA).
- Zscaler Client Connector fails to send the keepalive or Zscaler Client Connector is uninstalled before the keepalive is sent.
To soft remove a device from the Zscaler Client Connector Portal:
- In the Zscaler Client Connector Portal, go to **Enrolled Devices**.
- From the left-side navigation, go to **Device Overview**.
- Search for the **Device ID **or** **the** User ID** you want to remove.
![Search for user ID in enrolled devices](/downloads/z-app/policy-administration-settings/deprovisioning-user-zscaler-client-connector-portal/Enrolled-devices-User.png)
- Select the checkbox on the right and click **Remove Checked Devices**. The device state changes to **Removal Pending**.
![Remove enrolled device](/downloads/z-app/policy-administration-settings/deprovisioning-user-zscaler-client-connector-portal/Remove-Enrolled-Device.png)
After the update is complete, typically in one hour, the **Removal Pending** device state changes to **Removed**, and the device is removed from the portal.
Device removal can take up to an hour. The end user can immediately remove the device from Zscaler Client Connector. To learn more, see [Deprovisioning Your Device from Zscaler Client Connector​​​​​​](/zscaler-client-connector/deprovisioning-zscaler-client-connector?check_logged_in=1).