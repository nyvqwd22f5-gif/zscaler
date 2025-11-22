# Viewing Software Patch Inventory
Source: https://help.zscaler.com/unified/viewing-software-patch-inventory
PDF: https://help.zscaler.com/pdf/com/en/1529982.pdf

Software Patch Inventory allows you to monitor the current distribution of software patches on user devices across your organization. Each patch is associated with a user and device, and identified as either a software or security patch update, as applicable.
Prerequisites
To view software patches, first ensure:
- You're running the required versions of Zscaler Client Connector and ZDX Module.
- Your Digital Experience Monitoring subscription level supports Software Patch Inventory. To learn more, see [Ranges & Limitations](/unified/ranges-limitations).
- Your admin role is configured for inventory management. To learn more, see [Adding Digital Experience Monitoring Roles](/unified/adding-digital-experience-monitoring-roles).
- You've enabled the setting to collect Software Patch Inventory data. To learn more, see [Configuring Inventory Settings](/unified/configuring-inventory-settings).
Viewing Software Patch Inventory
To access current software patches, go to **Analytics > Digital Experience Management > Inventory > Software Patch Inventory**. The page consolidates the distribution of all software patches with their associated devices.
Use the page filters to help narrow the scope of patches, based on Zscaler location and geolocation. View the numerical counts for software patches and devices:
- **Patches**: The current number of software patches available.
- **Devices**: The current number of devices with software patches.
- **OS Distribution**: Visually indicates the number of devices per operating system.
The Software Patch Inventory table provides the following details:
- **Patch Name**: The alphanumeric name of the software patch.
- **Patch Type**: Identified as an **Update**, **Security Update**, or **N/A **(Not Applicable).
- **Devices**: The number of devices on which the software patch is installed.
Click a patch name or its **View **icon to access details about the software patch.
![Software Patch Inventory page](/downloads/zdx/analytics/inventory/viewing-software-patch-inventory/zdx-patch-inventory-landing2.png)
Viewing Patch Details
The software patch details page provides details of a specific patch selected from the Software Patch Inventory page:
- **Device**: The user device on which the software patch is installed.
- **User**: The user of the software patch.
- **Hostname**: The device hostname.
- **OS**: The associated operating system.
- **Version**: The version of the operating system.
- **Install Date**: The date when the software patch was installed on the corresponding device.
Click the patch device, user, or **View **icon to access user details about the patch. If selecting the device, a device ID is appended to the URL and the device is automatically included in the **Devices **filter on the corresponding user details page.
![Software patch details page](/downloads/zdx/analytics/inventory/viewing-software-patch-inventory/zdx-patch-inventory-details.png)
Viewing User Details
The details page for a specific user provides the following software patch information:
- **Patch Name**: The alphanumeric name of the software patch.
- **Device**: The user device on which the software patch is installed.
- **Patch Type**: Identified as an **Update**, **Security Update**, or **N/A **(Not Applicable).
- **Install Date**: The date when the software patch was installed on the corresponding device.
![Software patch inventory user details](/downloads/zdx/analytics/inventory/viewing-software-patch-inventory/zdx-patch-inventory-user-details.png)