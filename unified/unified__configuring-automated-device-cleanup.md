# Configuring Automated Device Cleanup
Source: https://help.zscaler.com/unified/configuring-automated-device-cleanup
PDF: https://help.zscaler.com/pdf/com/en/1496571.pdf

Zscaler Client Connector allows you to configure automatic device cleanup of old, inactive, and removed devices.
After modifying settings, it can take up to a week for Enrolled Devices to reflect changes.
To configure automatic device cleanup:
- In the Admin Portal, go to **Infrastructure > Connectors > Client > Client Connector Device Management**.
-
On the **Device Cleanup **tab:
-
**Force Remove Oldest Device After User Enrolls**: Select the threshold number of devices. If a user attempts to enroll a device after reaching the threshold number, Zscaler Client Connector force removes the oldest device. The default setting is **Restrict**, which means no devices are removed. An error is displayed when a user tries to enroll more than 16 devices.
Contact Zscaler Client Connector to change the minimum threshold to 1 device.
- **Automatically Force Remove Inactive Devices After**: Select the period after which Zscaler Client Connector automatically removes a device if it doesn't connect in the defined period and becomes inactive. Select from the following intervals: **30**, **60**, **90**, **120**, **150**, **180** days, or **Never**. The default setting is **Never**. A device becomes inactive when the most recent **KeepAlive** Timestamp is older than the defined period.
-
**Permanently Delete Removed Devices After**: Select the period after which a device is permanently removed from the portal after being in the **Removed **or **Unregistered **state. Select from the following intervals: **60**, **90**, **120**, **150**, or **180** days. Zscaler Client Connector uses the device’s **Last Deregistration Timestamp** to determine how long the device was in the[ Removed or Unregistered](/unified/device-states-enrolled-devices)** **state since the time it was deregistered.
Removing the registration from the Admin Portal doesn’t [remove Zscaler Client Connector from the device](/unified/uninstalling-zscaler-client-connector).
![Device clean up](/downloads/zscaler-client-connector/managing-devices/configuring-automated-device-cleanup/Client-Connector-Configuring-Automated-Device-Cleanup.png)
- Click **Save**.
To learn more about other Zscaler Client Connector Support features, see [About Zscaler Client Connector Support](/unified/about-zscaler-client-connector-support).