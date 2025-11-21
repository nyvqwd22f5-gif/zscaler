# Viewing Device Fingerprint Information for Failed Posture Devices
Source: https://help.zscaler.com/zscaler-client-connector/viewing-device-fingerprint-information-failed-posture-devices
PDF: https://help.zscaler.com/pdf/com/en/1529433.pdf

Device Posture Failure is available for Windows users only.
From the Zscaler Client Connector Portal, you can view device fingerprint information for [Failed Posture Devices](/zscaler-client-connector/about-failed-posture-devices).
To view device fingerprint information for failed posture devices:
- In the Zscaler Client Connector Portal, go to **Enrolled Devices** > **Failed Posture Devices**.
[See image.](#enrolled-failed-posture-devices)
[]![Failed Posture Devices](/downloads/zscaler-client-connector/monitoring-usage/viewing-device-fingerprint-information-failed-posture-devices/enrolled-devices-failed-posture_0.jpg)
The page displays a menu of failed posture devices.
[See image.](#list-failed-posture-devices)
[]![Failed posture list](/downloads/zscaler-client-connector/monitoring-usage/viewing-device-fingerprint-information-failed-posture-devices/list-failed-postures_0.jpg)
- From the drop-down list, select a **Failed Device Posture**.
- Click the view icon to view details of a failed device.
- In the **Zscaler Client Connector Registered Device Details** window, you can view:
-
Under **Registration Details**:
[See image.](#failed-pos-registration-details)
- **User ID**: The username used for Zscaler Client Connector during enrollment.
- **Department**: Department information synced from Zscaler Internet Access (ZIA).
Contact Zscaler Support to enable this feature.
- **Policy Name**: The Zscaler Client Connector profile assigned to the device. To learn more, see [About Zscaler Client Connector Profiles](/zscaler-client-connector/about-zscaler-app-profiles).
- **Device ID**: An internal Zscaler identifier for the device.
- **External Device ID**: The identifier that associates an external Mobile Device Management (MDM) device ID with devices in the Zscaler Client Connector Portal. This feature is not supported on Zscaler Client Connector versions earlier than 4.0 for Windows.
- **Last Registration Time**: The last time the user logged in to Zscaler Client Connector on the device.
- **Last Deregistration Time**: The last time the user logged out of Zscaler Client Connector on the device.
- **Zscaler Client Connector Version**: The Zscaler Client Connector version on the device.
- **Tunnel Version**: The last Zscaler Tunnel (Z-Tunnel) version the device connected with.
- **Zscaler Digital Experience Version**: The Zscaler Digital Experience (ZDX) version, if enabled on the device.
- **Active Tunnel SDK Version**: The current tunnel SDK version to allow admins to track the devices switching between multiple tunnel SDK versions.
- **Installation Type**:
- **Strict Enforcement**: All internet traffic is blocked until the end user logs in to Zscaler Client Connector.
- **General Deployment**: The end user can access the internet before they log in to Zscaler Client Connector.
-
Under **Device Details**:
[See image.](#failed-pos-device-details)
- **Owner**: If [Collect Device Owner Information](/zscaler-client-connector/configuring-zscaler-app-collect-device-owner-information) is enabled, this field displays the device owner information. This is the locally logged in user. When disabled, this field does not display device owner information.
- **Machine Hostname**: If [Collect Machine Hostname Information](/zscaler-client-connector/configuring-zscaler-app-collect-hostnames) is enabled, this field displays the machine hostname. When disabled, this field does not display the machine hostname.
- **Unique-ID**: The device's unique identifier.
- **OS**: The device's operating system.
- **Model**: The device's model.
- **Manufacturer**: The device's manufacturer.
- **MAC Address**: The device's media access control address.
- **Device Locale**: The device's locale.
- **Hardware Fingerprint**: The device fingerprint.
- **Serial Number**: The device’s serial number. Applies only to Zscaler Client Connector version 4.7 and later for Windows.
- **Imprivata User**: **Yes **indicates an Imprivata user is logged in to Zscaler Client Connector.
-
Under **Service Status**:
[See image.](#failed-pos-ServiceStatus)
- **ZIA Enabled**: Displays **True **if the user is entitled for the ZIA service in Zscaler Client Connector. Displays **False **if the user is not entitled for the ZIA service in Zscaler Client Connector.
- **ZIA Health**:** **Displays **Active **if Zscaler Client Connector is connected to ZIA. Displays **Inactive **if Zscaler Client Connector is not connected to ZIA.
- **Last Seen Connected to ZIA**:** **The last known date and time of connection to ZIA.
- **ZPA Enabled**: Displays **True **if the user is entitled for the Zscaler Private Access (ZPA) service in Zscaler Client Connector. Displays **False **if the user is not entitled for the ZPA service in Zscaler Client Connector.
- **ZPA Health**: Displays **Active **if Zscaler Client Connector is connected to ZPA. Displays **Inactive **if Zscaler Client Connector is not connected to ZPA.
- **Last Seen Connected to ZPA**: The last known date and time of connection to ZPA.
- **ZDX Enabled**: Displays **True **if the user is entitled for the ZDX service in Zscaler Client Connector. Displays **False **if the user is not entitled for the ZDX service in Zscaler Client Connector.
- **ZDX Health**: Displays **Active **if Zscaler Client Connector is connected to ZDX. Displays **Inactive **if Zscaler Client Connector is not connected to ZDX.
- **Last Seen Connected to ZDX**: The last known date and time of connection to ZDX.
- **Zscaler Deception Enabled**: Displays **True **if the user is entitled for the Deception service in Zscaler Client Connector. Displays **False **if the user is not entitled for the Deception service in Zscaler Client Connector.
- **Zscaler Deception Health**: Displays **Active **if Zscaler Client Connector is connected to Deception. Displays **Inactive **if Zscaler Client Connector is not connected to Deception.
- **Last Seen Connected to Zscaler Deception**: The last known date and time of connection to Deception.
-
Under **Compliance Status**:
[See image.](#failed-pos-compliance-status)
- **Device State**: The device’s policy status. To learn more, see [Device States for Enrolled Devices](/zscaler-client-connector/policy-statuses-enrolled-devices).
- **Last Seen with Zscaler Client Connector Active**: The last time that Zscaler Client Connector was active on the device.
- **Last Configuration Download Time**: The last time the Zscaler Client Connector profile was updated. To learn more, see [Zscaler Client Connector Update Intervals](/zscaler-client-connector/zscaler-app-update-intervals).
- **Configuration Download Count**: The total number of times the app profile was updated since enrollment.
- **One-Time Password**: Displays a temporary password for login.
- **Logout, Disable, Uninstall Password**: The password associated with the device’s app profile. Applies to Zscaler Client Connector version 4.0 for Windows. To learn more, see [Configuring Zscaler Client Connector Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-profiles).
-
For Zscaler Client Connector version 4.0 and later for Windows, the following optional one-time passwords listed are associated with the device’s app profile and are configured in [app profiles](/zscaler-client-connector/configuring-zscaler-client-connector-profiles):
Click the **Copy** icon to copy the password to your clipboard.
- **Logout OTP**: The password users must enter to log out of Zscaler Client Connector.
- **Revert OTP**: The password users must enter to revert to the previous Zscaler Client Connector version.
- **Uninstall OTP**: The password users must enter to uninstall Zscaler Client Connector.
- **Exit OTP**: The password that users can enter to exit the app from the system tray without disabling ZIA.
- **Disable ZIA OTP**: The password users must enter to disable the ZIA service.
- **Disable ZPA OTP**: The password users must enter to disable the ZPA service.
- **Disable ZDX OTP**: The password users must enter to disable the ZDX service.
- **Disable Endpoint DLP OTP**: The password users must enter to disable data protection in Zscaler Client Connector.
- **Device Trust Level**: Displays the device trust level based on the configured levels in [ZIA posture profiles](/zscaler-client-connector/adding-zia-posture-profiles). Trust levels are **Low**, **Medium**, **High**, or **Unknown**.
- **Anti-Tampering Status**: Displays whether anti-tampering is enabled or disabled.
-
Under **Fetch Logs**:
[See image.](#failed-pos-log-details)
These fields reflect the process to remotely fetch logs from the device. The **Fetch Logs** button becomes active for a registered device if an email address has already been configured in **Administration **> **Client Connector Support** > **App Supportability** > **Enable Support Access in Zscaler Client Connector**. When you click **Fetch Logs**, Zscaler Client Connector uploads logs from the previous 14-day period to the web server.
- **Fetch Log Status**: The following messages display to keep you informed of the fetch log status:
- **Waiting for KeepAlive**: Displays after the fetch log request is initiated.
- **Extraction in progress**: Displays after the KeepAlive message is displayed.
- **Completion**: Displays if the fetch log request is successful.
- **Error while fetching logs**: Displays if the fetch log request fails.
- **Log Timestamp**: Displays the date and time you clicked **Fetch Logs** and Zscaler Client Connector began uploading the logs to the web server.
- **Log Acknowledge Timestamp**: Displays the date and time the log fetch successfully completed.
- **Log URL**: Displays the URL provided after Zscaler Client Connector completes uploading logs.
-
**Force Remove**: When viewing device fingerprint information for an enrolled device, you can also force remove the device from the Zscaler Client Connector Portal. To force remove a device, click **Force Remove**.
You can only force remove devices with the device state of **Removal Pending**. To learn more about device states, see [Device States for Enrolled Devices](/zscaler-client-connector/device-states-enrolled-devices).
[See image.](#failed-pos-force-remove)
-
**Quarantine**: You can quarantine a device by clicking **Quarantine**. This prevents the device from re-enrolling. If a device is in quarantine, click **Unquarantine**. To learn more, see [Device States for Enrolled Devices](/zscaler-client-connector/policy-statuses-enrolled-devices).
[See image.](#failed-pos-quarantine)
[]![Registration details on Registered Device Details screen](/downloads/client-connector/monitoring-usage/viewing-device-fingerprint-enrolled-device/Zscaler-client-connector-registered-devices-registration-details_0.jpg)
[]![Device details on the Registered Device Details screen](/downloads/client-connector/monitoring-usage/viewing-device-fingerprint-enrolled-device/ZSclientconnector-device-details.png)
[]![Compliance status on the Registered Device Details screen](/downloads/tech-pubs-drafts/client-connector-draft-articles/viewing-device-fingerprint-enrolled-device-draft-win-40/Compliance%20Status.png)
[]![Fetch log details on the Registered Device Details screen](/downloads/z-app/monitoring-usage/viewing-device-fingerprint-enrolled-device/client-connector-fetch-logs_0.png)
[]![Service-Status.jpg](/downloads/zscaler-client-connector/monitoring-usage/viewing-device-fingerprint-information-failed-posture-devices/Service-Status.jpg)
[]![Force Remove and Quarantine buttons in Device Details](/downloads/tech-pubs-drafts/client-connector-draft-articles/viewing-device-fingerprint-enrolled-device-doc-44899/Client_Connector-Force%20Remove_Quarantine.png)
[]![Quarantine button in Device Details](/downloads/tech-pubs-drafts/client-connector-draft-articles/viewing-device-fingerprint-enrolled-device-doc-56783/client_connector-enrolled_devices_quarantine_unquarantine.png)