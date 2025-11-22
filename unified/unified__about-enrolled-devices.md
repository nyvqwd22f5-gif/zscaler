# About Enrolled Devices
Source: https://help.zscaler.com/unified/about-enrolled-devices
PDF: https://help.zscaler.com/pdf/com/en/1496996.pdf

From the Admin Portal, you can view a list of enrolled devices, view device fingerprint information, and soft remove devices.
The Device Management page provides the following benefits:
- Create a custom view by filtering the list of enrolled devices and selecting the columns that display on the page.
- Find information quickly by performing an exact match search.
- Sort and capture data by exporting device details as a CSV file.
- Easily manage devices by soft removing devices.
About the Device Management Page
On the Device Management page (Infrastructure > Connectors > Client > Device Overview), you can do the following:
- Filter the list of enrolled devices with the following options:
- **States**: View devices that are identified as **Registered**, **Unregistered**, **Removal Pending**, **Removed**, or **Quarantined**. By default, all states are shown in the table. To learn more, see [Device States for Enrolled Devices](/unified/device-states-enrolled-devices).
- **OS**: View devices for all operating systems or a specific operating system. By default,** **all operating systems are shown in the table.
- **Active From**: View devices active from **7 Days**, **30 Days**, **60 Days**, **90 Days**, **120 Days**, **150 Days**, **180 Days**, or **Older than 180 Days**.
-
View a list of enrolled devices for your organization.
[For each enrolled device, you can view these fields.](#Item1)
You can customize what you see on the screen. For details, refer to step 5.
[]
- **User ID**: The enrolled user for the device.
- **OS Type**: The device operating system.
- **Device Model**: The device model.
- **Zscaler Client Connector Version**: The Zscaler Client Connector version installed on the device.
- **Device State**: The status of the device. To learn more, see [Device States for Enrolled Devices](/unified/device-states-enrolled-devices).
- **Zscaler Digital Experience (ZDX) Version**: The Digital Experience Monitoring version installed on the device.
- **Zscaler Deception Version**: The Deception version installed on the device.
- **Unique-ID**: The Zscaler-provided device's unique identifier.
- **Hardware Fingerprint**: The unique ID created from the device’s hardware, such as a serial number, BIOS ID, battery ID, etc.
- **Configuration Download Count**: The total number of times the app profile was updated on the device since enrollment.
- **Tunnel Version**: The last Zscaler Tunnel (Z-Tunnel) version the device connected with.
- **Policy Name**: The Zscaler Client Connector profile assigned to the device. To learn more, see [About Zscaler Client Connector App Profiles](/unified/about-zscaler-client-connector-app-profiles).
- **OS Version**: The version of the operating system for the device.
- **Machine Hostname**: If Collect Machine Hostname Information is enabled, this field displays the machine hostname. When disabled, this field does not display the machine hostname.
- **MAC Address**: The device's media access control address.
- **Manufacturer**: The device's manufacturer.
- **Owner**: If Collect Device Owner Information is enabled, this field displays the device owner information. For Windows and macOS, this is the locally logged in user. For Android and iOS, this is the Zscaler Client Connector username. When disabled, this field does not display device owner information.
- **Last Registration Time**: The last time the user logged in to Zscaler Client Connector on the device.
- **KeepAlive Time**: The keepalive occurs every 80 minutes.
- **Last Deregistration Time**: The last time the user logged out of Zscaler Client Connector on the device.
- **Last Configuration Download Time**: The last time the Zscaler Client Connector profile was updated. To learn more, see [Zscaler Client Connector Update Intervals](/unified/zscaler-client-connector-update-intervals).
- **Last Seen with Client Connector Active**: The last time that Zscaler Client Connector was active on the device.
- **Last Seen Connected to ZIA**: The last known date and time of connection to Internet & SaaS.
- **Zscaler Client Connector Revert Status**: Status of revert: Unknown, InProgress, PreviousBuildNotAvailable, RevertFailed, and RevertSuccess.
- **Department**: Department information synced from Internet & SaaS.
- **Active Tunnel SDK Version**: The current tunnel SDK version to allow admins to track the devices switching between multiple tunnel SDK versions.
- **Installation Type**: The type of installation (Strict Enforcement or General Deployment).
- **Serial Number**: The device’s serial number.
- **DC Location Method**: The method used to locate the nearest data center (Source IP or Device Geolocation).
- Perform an exact match search of enrolled devices by:
- **Users**: View devices for all users or a specific user. Use the **Search **function to find a specific user.
- **Device ID**: The unique ID for each device in the Admin Portal database. The unique ID is generated for each new enrollment in the Zscaler Client Connector and continues for subsequent enrollments.
- **UDID**: The Unique Device Identifier that Zscaler Client Connector generates for every new installation. The same UDID continues during uninstalling, re-installing, and rebooting of the devices. The UDID is unique to each user and device and changes from user to user for the same device.
- **Machine Hostname**: A name assigned to a device on a network. The end user or the operating system can customize the value.
- **Hardware Fingerprint**: The unique ID created from the device’s hardware, such as a serial number, BIOS ID, battery ID, etc.
- **Zscaler Client Connector Version**: The Zscaler Client Connector version installed on the devices.
- **App Profile Name**: A custom name that an administrator configures when creating or modifying app profiles for each OS (Windows, macOS, Linux, etc.).
- Export device fingerprint as a CSV file for all enrolled devices.
- **Device Details (All Fields)**: Includes fields such as manufacturer, model, username, machine hostname, UDID, etc.
- **Device Details (Custom Fields)**: Includes fields such as User, OS Type, Device Model, OS Version, and VPN State.
- **Disable Reasons**: Displays the reason a device is disabled.
- **Service Status**: The status of Internet & SaaS, Private Applications, and Digital Experience Monitoring. Can be in an ON, OFF, or ERROR state. This only applies if you have those services enabled for your organization.
- **Partner Login Details**: Includes partner device fields such as UDID, Platform, Device ID, login name, and cloud.
- Create a custom view of the Device Management page by modifying the columns that display and the number of rows that display.
- To modify the columns that display:
- Click the **Table Options** icon. Verify that **Columns **is selected. Select the checkboxes of the fields you want to view on the page. Clear the checkboxes of fields you don't want to view on the page.
- To reorder columns, click the column name and drag-and-drop it to the desired position.
- To modify the number of rows that display, click **Rows **and select either **50 **or **100**.
- [View device details for each enrolled device](/unified/viewing-device-fingerprint-enrolled-device). You can also view the [one-time password](/unified/accessing-one-time-passwords-enrolled-devices) for each device.
- Select devices for soft removal from the Admin Portal.
- [Soft remove selected devices from the Admin Portal](/unified/soft-removing-device-admin-portal) by either clicking **Delete **from the **Actions **drop-down menu or clicking the **Delete **icon.
![About Device Management](/downloads/tech-pubs-drafts/client-connector-draft-articles/about-enrolled-devices-doc-doc-47165/Enrolled-Devices-Device-Management.png)