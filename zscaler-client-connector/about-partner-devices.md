# About Partner Devices
Source: https://help.zscaler.com/zscaler-client-connector/about-partner-devices
PDF: https://help.zscaler.com/pdf/com/en/1420126.pdf

From the Zscaler Client Connector Portal, you can view a list of partner devices with access to your organization's tenant. You can give partner organizations access to your organization's tenant by enabling access. To learn more, see [Enabling ZPA Partner Logins](/zscaler-client-connector/enabling-zpa-partner-logins).
The Partner Devices page provides the following benefits:
- Organizes your partner devices by filtering and viewing the list of partner devices.
- Allows users to perform an exact match and select what displays on the Partner Devices page.
- Exports the device fingerprint as a CSV file, sorts device details, and views the device fingerprint for each partner device.
- Allows users to select and soft remove devices.
About the Partner Devices Page
On the Partner Devices page (Enrolled Devices > Partner Devices), you can do the following:
- Filter the list of partner devices with the following options:
- **Active From**: View devices active from **7 Days**, **30 Days**, **60 Days**, **90 Days**, **120 Days**, **150 Days**, **180 Days**, or **Older than 180 Days**.
- **Users**: View devices for all users or a specific user. Use the search function to find a specific user.
- **States**: View devices that are identified as **Registered**, **Unregistered**, **Removal Pending**, **Removed**, or **Quarantined**. By default, all states except **Removed** are shown in the table.
- **OS**: View devices for all operating systems or a specific operating system. By default,** **all operating systems are shown in the table.
- [Soft remove selected devices from the Zscaler Client Connector Portal](/zscaler-client-connector/soft-removing-device-zscaler-client-connector-portal) by either clicking **Delete** from the **Actions** drop-down menu or clicking the **Delete** icon.
-
View a list of all partner devices for your organization. For each partner device, you can view:
- **User ID**: The enrolled user for the device.
- **OS Type**: The device operating system.
- **Device Model**: The device model.
- **Zscaler Client Connector Version**: The Zscaler Client Connector version installed on the device.
- **Device State**: The status of the device. To learn more, see [Device States for Enrolled Devices](/zscaler-client-connector/device-states-enrolled-devices).
By default, the list is filtered to display devices for all users, all states, and all operating systems.
- Select devices for soft removal from the Zscaler Client Connector Portal.
- Perform an exact match search of partner devices by:
- **Device ID**: The unique ID for each device in the Zscaler Client Connector Portal database. The unique ID is generated for each new enrollment in the Zscaler Client Connector Portal and continues for subsequent enrollments.
- **UDID**: The Unique Device Identifier that Zscaler Client Connector generates for every new installation. The same UDID continues during uninstalling, reinstalling, and rebooting of the devices.
- **Machine Hostname**: A name assigned to a device on a network. The end user or the operating system can customize the value.
- **Hardware Fingerprint**: The unique ID created from the device’s hardware, such as a serial number, BIOS ID, battery ID, etc.
- **Zscaler Client Connector Version**: The Zscaler Client Connector version installed on the devices.
- **App Profile Name**: A custom name that an administrator configures when creating or modifying app profiles for each OS (Windows, macOS, Linux, etc.).
- [View the device fingerprint for each partner device](/zscaler-client-connector/viewing-device-fingerprint-partner-device). You can also view the [one-time password](/zscaler-client-connector/about-one-time-passwords-enrolled-devices) for each device.
- Export the device fingerprint as a CSV file for all partner devices.
- **Device Details (All Fields)**: Includes fields such as manufacturer, model, username, machine hostname, UDID, etc.
- **Device Details (Custom Fields)**: Includes fields such as **User**, **OS Type**, **Device Model**, **OS Version**, and **VPN State**.
- **Disable Reasons**: Displays the reason a device is disabled.
- **Service Status**: The status of Zscaler Internet Access (ZIA), Zscaler Private Access (ZPA), and Zscaler Digital Experience (ZDX). Can be in an **On**, **Off**, or **Error** state. This only applies if you have those services enabled for your organization.
![Partner devices page ](/downloads/zscaler-client-connector/monitoring-usage/about-partner-devices/zscaler-client-connector-partner-devices.png)
By default, each page shows up to 100 devices. View more devices by using the table pagination feature located at the bottom of each page.