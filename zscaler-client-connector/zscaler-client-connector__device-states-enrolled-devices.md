# Device States for Enrolled Devices
Source: https://help.zscaler.com/zscaler-client-connector/device-states-enrolled-devices
PDF: https://help.zscaler.com/pdf/com/en/1342396.pdf

In [Enrolled Devices](/zscaler-client-connector/about-enrolled-devices), you can view a device’s state and the Zscaler Client Connector[ profile](/zscaler-client-connector/about-zscaler-client-connector-profiles) applied to it. The following table lists the device states, a description of the device state, and if it applies to the device limit:
The maximum number of devices you can enroll under one username is 16. To learn more, see [Removing a Device if the Number of Devices Limit is Reached](/zscaler-client-connector/removing-device-if-number-devices-limit-reached).
[](/zscaler-client-connector/configuring-automated-device-cleanup)
[](/zscaler-client-connector/viewing-device-fingerprint-enrolled-device)[](/zscaler-client-connector/quarantining-device-zscaler-client-connector-portal)
[](/zscaler-client-connector/soft-removing-device-zscaler-client-connector-portal)
- [](/zscaler-client-connector/zscaler-app-update-intervals)
- [](/zscaler-client-connector/configuring-automated-device-cleanup)
- [](/zscaler-client-connector/configuring-automated-device-cleanup)[](/zscaler-client-connector/viewing-device-fingerprint-enrolled-device)
- [](/zscaler-client-connector/force-removing-device-zscaler-client-connector-portal)
[](/zscaler-client-connector/configuring-automated-device-cleanup)
| Device State | Description | Applies to Device Limit? |
| ------------ | ----------- | ------------------------ |
| Registered | Zscaler Client Connector is enrolled on the device and logged in with a user. | Yes |
| Unregistered | The user manually logged out of the app.The device is permanently removed from the Zscaler Client Connector Portal when it's been in the Unregistered** **state for the time configured in the Permanently Delete Removed Devices After field in Configuring Automated Device Cleanup. | No |
| Quarantined | The administrator quarantined the device to prevent access to Zscaler applications for security reasons. The device cannot be re-enrolled based on its unique device fingerprint.You can quarantine a device from the Zscaler Client Connector Registered Device Details page in Enrolled Devices. To learn more, see Quarantining a Device in the Zscaler Client Connector Portal. | No |
| Removal Pending | The administrator soft removed the device from the Zscaler Client Connector Portal, and Zscaler Client Connector hasn't sent a keepalive message. To learn more, see Soft Removing a Device from the Zscaler Client Connector Portal. | Yes |
| Removed | Occurs when any of the following conditions exist:Zscaler Client Connector sent the next keepalive message or a policy was manually updated from Zscaler Client Connector on a device that was soft removed. To learn more, see Zscaler Client Connector Update Intervals.A user exceeded the maximum number of devices enrolled, as configured in the Force Remove Oldest Device After User Enrolls field in Configuring Automated Device Cleanup.The device has been inactive for the time configured in the Automatically Force Remove Inactive Devices After** **field in Configuring Automated Device Cleanup. An inactive device is based on the Last Seen Connected to ZIA** **timestamp associated with the Zscaler Client Connector registration.The administrator force removed the device from the Zscaler Client Connector Portal. The device is permanently removed from the Zscaler Client Connector Portal when it's been in Removed** **state for the time configured in the Permanently Delete Removed Devices After field in Configuring Automated Device Cleanup. | No |
On the Device Management page in the Zscaler Client Connector Portal, you can filter by device state using the States drop-down menu. Select the state or states you want to display in the table and then click Apply.
![States menu in Enrolled Devices](/downloads/tech-pubs-drafts/client-connector-draft-articles/device-states-enrolled-devices-doc-57958/Client-Connector-Device_States.png)