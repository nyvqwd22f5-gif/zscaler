# Configuring Automated Device Cleanup
Source: https://help.zscaler.com/zscaler-client-connector/configuring-automated-device-cleanup
PDF: https://help.zscaler.com/pdf/com/en/1296741.pdf

Zscaler Client Connector allows you to configure automatic device cleanup of old, inactive, and removed devices.
After modifying settings, it can take up to a week for Enrolled Devices to reflect changes.
To configure automatic device cleanup:
- In the Zscaler Client Connector Portal, go to **Administration**.
- In the left-side navigation, click **Client Connector Support**.
- Click the **Device Cleanup **tab.
- **Force Remove Oldest Device After User Enrolls**: Select the threshold number of devices. If a user attempts to enroll a device after reaching the threshold number, Zscaler Client Connector force removes the oldest device. The default setting is **Restrict**, which means no devices are removed. An error is displayed when a user tries to enroll more than 16 devices.
Contact Zscaler Client Connector to change the minimum threshold to 1 device.
- **Automatically Force Remove Inactive Devices After**: Select the period after which Zscaler Client Connector automatically removes a device if it doesn't connect to Zscaler Internet Access (ZIA) in the defined period and becomes inactive. Select from the following intervals: **30**, **60**, **90**, **120**, **150**, **180** days, or **Never**. The default setting is **Never**. A device becomes inactive when the most recent **KeepAlive Timestamp** is older than the defined period.
- **Permanently Delete Removed Devices After**: Select the period after which a device is permanently removed from the portal after being in the **Removed **or **Unregistered **state. Select from the following intervals: **60**, **90**, **120**, **150**, or **180** days. Zscaler Client Connector uses the device’s Last Deregistration Timestamp to determine how long the device was in the [Removed or Unregistered](/zscaler-client-connector/device-states-enrolled-devices) state since the time it was deregistered.
Removing the registration from the Zscaler Client Connector Portal doesn’t [remove Zscaler Client Connector from the device](/zscaler-client-connector/uninstalling-zscaler-client-connector).
![Zscaler Client Connector Portal Device Cleanup](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-automated-device-cleanup/Client-Connector-Configuring%20Automated%20Device%20Cleanup.png)
- Click **Save**.
To learn more about other Zscaler Client Connector Support features, see [About Zscaler Client Connector Support](/zscaler-client-connector/about-zscaler-app-support).