# Removing a Device if the Number of Devices Limit is Reached
Source: https://help.zscaler.com/unified/removing-device-if-number-devices-limit-reached
PDF: https://help.zscaler.com/pdf/com/en/1496581.pdf

You can only enroll up to 16 devices under one username. If you want to enroll another device but have reached the maximum number of devices, you must remove at least one device from the Admin Portal. You can also configure the Admin Portal to automatically remove devices. To learn how to configure the number of devices threshold, see [Configuring Automated Device Cleanup](/unified/configuring-automated-device-cleanup).
You can enroll a removed device again if you have fewer than 16 enrolled devices. If you have fewer than 16 active devices but see an error for exceeding the number of devices limit, contact Zscaler Support.
What Counts as a Device?
In the Admin Portal, a removed device has a device state of **Unregistered **or **Removed**.** **Devices with a device state of **Unregistered **or **Removed** do not count against the number of devices limit. These are displayed in the Admin Portal for statistical purposes only. Devices with a device state of **Removal Pending** count against the number of devices limit. To learn more about device states, see [Device States for Enrolled Devices](/unified/device-states-enrolled-devices).
Removing a Device
To remove users' devices in the Admin Portal, you can use either of the following methods:
| **Soft Remove** | **Force Remove** |
| --------------- | ---------------- |
| The soft removal takes effect when Zscaler Client Connectorr sends its next keepalive. | The force removal takes effect immediately. |
| The user does not experience service interruption or authentication errors. | The user may experience service interruption or authentication errors. |
To learn how to soft remove a device, see [Soft Removing a Device from the Admin Portal](/unified/soft-removing-device-admin-portal).
To learn how to force remove a device, see [Force Removing a Device from the Admin Portal](/unified/force-removing-device-admin-portal).