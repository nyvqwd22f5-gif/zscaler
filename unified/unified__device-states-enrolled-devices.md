# Device States for Enrolled Devices
Source: https://help.zscaler.com/unified/device-states-enrolled-devices
PDF: https://help.zscaler.com/pdf/com/en/1497131.pdf

In [Enrolled Devices](/unified/about-enrolled-devices), you can view a device’s state and the Zscaler Client Connector[ app profile](/unified/about-zscaler-client-connector-app-profiles) applied to it. Possible states are:
The maximum number of devices you can enroll under one username is 16. To learn more, see [Removing a Device if the Number of Devices Limit is Reached](/unified/removing-device-if-number-devices-limit-reached).
[](/unified/configuring-automated-device-cleanup)
[](/unified/viewing-device-fingerprint-enrolled-device)[](/unified/quarantining-device-admin-portal)
[](/unified/soft-removing-device-admin-portal)
- [](/unified/zscaler-client-connector-update-intervals)
- [](/unified/configuring-automated-device-cleanup)
- [](/unified/configuring-automated-device-cleanup)[](/unified/viewing-device-fingerprint-enrolled-device)
- [](/unified/force-removing-device-admin-portal)
[](/unified/configuring-automated-device-cleanup)
| Device State | Description | Applies to Device Limit? |
| ------------ | ----------- | ------------------------ |
| Registered | Zscaler Client Connector is enrolled on the device and logged in with a user. | Yes |
| Unregistered | The user manually logged out of the app.The device is permanently removed from the Admin Portal when it's been in the Unregistered** **state for the time configured in the Permanently Delete Removed Devices After field in Configuring Automated Device Cleanup. | No |
| Quarantined | The administrator quarantined the device to prevent access to Zscaler applications for security reasons. The device cannot be re-enrolled based on its unique device fingerprint.You can quarantine a device from the Zscaler Client Connector Registered Device Details page in Enrolled Devices. To learn more, see Quarantining a Device in the Admin Portal. | No |
| Removal Pending | The administrator soft removed the device from the Admin Portal, and Zscaler Client Connector hasn't sent a keepalive message. To learn more, see Soft Removing a Device from the Admin Portal. | Yes |
| Removed | Occurs when any of the following conditions exist:Zscaler Client Connector sent the next keepalive message or a policy was manually updated from Zscaler Client Connector on a device that was soft removed. To learn more, see Zscaler Client Connector Update Intervals.A user exceeded the maximum number of devices enrolled, as configured in the Force Remove Oldest Device After User Enrolls field in Configuring Automated Device Cleanup.The device has been inactive for the time configured in the Automatically Force Remove Inactive Devices After** **field in Configuring Automated Device Cleanup. An inactive device is based on the Last Seen Connected to ZIA** **timestamp associated with the Zscaler Client Connector registration.The administrator force removed the device from the Admin Portal. The device is permanently removed from the Admin Portal when it's been in Removed** **state for the time configured in the Permanently Delete Removed Devices After field in Configuring Automated Device Cleanup. | No |
On the Device Management page in the Zscaler Client Connector Portal, you can filter by device state using the States drop-down menu. Select the state or states you want to display in the table and then click Apply.
![States menu in Enrolled Devices](/downloads/tech-pubs-drafts/client-connector-draft-articles/device-states-enrolled-devices-doc-57958/Client-Connector-Device_States.png)