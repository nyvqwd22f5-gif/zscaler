# About Failed Posture Devices
Source: https://help.zscaler.com/zscaler-client-connector/about-failed-posture-devices
PDF: https://help.zscaler.com/pdf/com/en/1529280.pdf

Failed Posture Devices is available for Windows users only. You must also have Zscaler Digital Experience (ZDX) or Zscaler Client Connector Telemetry (formerly [Health Metrics](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles#Health_Metrics)) enabled.
From the Zscaler Client Connector Portal, you can view a list of devices that failed posture checks. To view a trend of devices failing posture checks and what posture profiles are involved, see [Understanding the Zscaler Client Connector Dashboard](/zscaler-client-connector/understanding-zscaler-client-connector-portal-dashboard).
Failed posture devices provide the following benefits and allow you to:
- Review the list of devices that failed their posture check.
- Filter the list by time or posture profile to immediately identify devices.
- Quickly identify the users and attributes of those devices to accelerate remediation.
About Failed Posture Devices Page
On the Failed Posture Devices page (Enrolled Devices > Failed Posture Devices), you can do the following:
- Choose a **Time** for failed postures ranging from three-hour intervals up to 24 hours.
- Select a **Failed Device Posture** and show failed devices for that specific posture.
- View a list of all failed devices for a specific failed device posture. For each device, you can view:
- **User ID**: The enrolled user for the device.
- **OS Type**: The device operating system.
- **Device Model**: The device model.
- **Zscaler Client Connector Version**: The Zscaler Client Connector version installed on the device.
- **Device State**: The status of the device. To learn more, see [Device States for Enrolled Devices](/zscaler-client-connector/device-states-enrolled-devices).
- **Keep Alive Time**: The keep alive occurs every 80 minutes.
By default, the list displays devices that have failed a particular posture.
- [Soft remove selected devices from the Zscaler Client Connector Portal](/zscaler-client-connector/soft-removing-device-zscaler-client-connector-portal) by either clicking **Delete** from the Actions drop-down menu or clicking the **Delete** icon.
- [View device fingerprint information for failed posture devices](/zscaler-client-connector/viewing-device-fingerprint-information-failed-posture-devices).
![Failed device posture page](/downloads/zscaler-client-connector/monitoring-usage/about-failed-posture-devices/about-failed-posture-devices-.png)
By default, each page shows up to 50 devices. View more devices by using the table pagination feature located at the bottom of each page.