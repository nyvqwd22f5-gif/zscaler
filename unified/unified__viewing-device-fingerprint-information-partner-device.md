# Viewing Device Fingerprint Information for a Partner Device
Source: https://help.zscaler.com/unified/viewing-device-fingerprint-information-partner-device
PDF: https://help.zscaler.com/pdf/com/en/1497186.pdf

From the Admin Portal, you can view device fingerprint information for [partner devices](/unified/about-partner-devices).
To view device fingerprint information for a partner device:
- In the Admin Portal, go to **Infrastructure > Connectors > Client > Partner Devices**.
-
Click the **Partner Device Details** icon to view the device fingerprint from the enrolled device.
The **Zscaler Client Connector Registered Partner Device Details** window appears.
[See image.](#Device-Details)
- In the **Zscaler Client Connector Registered Partner Device Details** window, you can view:
- Under **Registration Details**:
- **User ID**: The username used for Zscaler Client Connector.
- **Device ID**: An internal Zscaler identifier for the device.
- **Last Registration Time**: The last time the user logged in to Zscaler Client Connector on the device.
- **Last Deregistration Time**: The last time the user logged out of Zscaler Client Connector on the device.
- **Zscaler Client Connector Version**: The Zscaler Client Connector version on the device.
- **Tunnel Version**: The last Zscaler Tunnel (Z-Tunnel) version the device connected with.
- **Device State**: The registration status of the device.
Unregistered partner devices are removed if inactive in the previous 24 hours, allowing the same user or a new user to log in.
[See image.](#Device-Registration-Details)
-
Under **Device Details**:
- **Owner**: If the [Collect Device Owner Information switch](/unified/configuring-zscaler-client-connector-collect-device-owner-information) is enabled, this field displays the device owner information. For Windows and macOS, this is the locally logged in user. For Android and iOS, this is the Zscaler Client Connector username. If the switch is disabled, this field does not display the device owner information.
- **Machine Hostname**: If the [Collect Machine Hostname Information switch](/unified/configuring-zscaler-client-connector-collect-hostnames) is enabled, this field displays the machine hostname. If the switch is disabled, this field does not display the machine hostname.
- **Unique-ID**: The device's unique identifier.
- **OS**: The device's operating system.
- **Model**: The device's model.
- **Manufacturer**: The device’s manufacturer.
- **MAC Address**: The device’s media access control address.
- **Device Locale**: The device’s locale.
- **Hardware Fingerprint**: The device fingerprint.
[See image.](#Device-Details-section)
-
Under **Service Status**:
- **ZPA Enabled**: Displays whether Private Applications is enabled or disabled.
- **ZPA Health**: Displays whether the health of Private Applications is active or inactive.
- **Last Seen Connected to ZPA**: The last known date and time of connection to Private Applications.
[See image.](#Service-Status-Details)
-
Under **Compliance Status**:
- **Device State**: The device’s policy status. To learn more, see [Device States for Enrolled Devices](/unified/device-states-enrolled-devices).
- **Last Seen with Zscaler Client Connector Active**: The last time that Zscaler Client Connector was active on the device.
- **Last Configuration Download Time**: The last time the Zscaler Client Connector profile was updated. To learn more, see [Zscaler Client Connector Update Intervals](/unified/zscaler-client-connector-update-intervals).
- **Configuration Download Count**: The total number of times the app profile was updated since enrollment.
[See image.](#Compliance-Status-details)
When viewing device fingerprint information for a partner device, you can also force remove the device from the Admin Portal. To force remove a device, click **Force Remove**. To learn more, see [Force Removing a Device from the Admin Portal](/unified/force-removing-device-admin-portal).
[]![Click to view device details](/downloads/z-app/monitoring-usage/viewing-device-fingerprint-partner-device/ZPA-partner-login_view-device-fingerprint.png)
[]![Device registration details](/downloads/z-app/monitoring-usage/viewing-device-fingerprint-partner-device/ZCC_Partner-Devices_Registration-Details_blur.png)
[]![Device Details](/downloads/client-connector/monitoring-usage/viewing-device-fingerprint-partner-device/ZCC-partner-devices-Device-Details.png)
[]![Service Status Details](/downloads/z-app/monitoring-usage/viewing-device-fingerprint-partner-device/ZPA_Service-Staus.png)
[]![Compliance Status details](/downloads/z-app/monitoring-usage/viewing-device-fingerprint-partner-device/ZPA_Compliance-Status.png)