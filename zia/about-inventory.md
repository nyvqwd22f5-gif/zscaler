# About Inventory
Source: https://help.zscaler.com/zia/about-inventory
PDF: https://help.zscaler.com/pdf/com/en/1515431.pdf

The inventory provides visibility into the use of removable storage devices (e.g., USB drives, external hard drives), printers, and portable devices (e.g., mobile phones and cameras) within an organization. It automatically detects the usage of these devices and displays the permission access based on the device control policy. By doing so, the inventory helps ensure compliance, enhance security, and proactively prevent data exfiltration. Additionally, you can drill down into specific devices to view detailed usage information and the associated activities and incidents.
The Inventory page provides the following benefits and enables you to:
- Gain visibility into the devices connected by a user in an organization.
- Analyze Endpoint Data Loss Prevention (DLP) activities and incidents from various perspectives, like departments, DLP engines, AI & ML categories, file type, etc. for each device.
- Effectively create device control rules for removable storage and printers using the inventory data, which includes details such as devices, users, departments, and endpoint names.
About the Inventory Page
On the Inventory page (Analytics > Endpoint Data Scan > Inventory) you can view the following tabs:
- [Removable Storage Devices](#about_removable_storage)
- [Printers](#about_printers_page)
- [Portable Devices](#about_portable_devices)
[]On the Removable Storage Devices page (Analytics > Endpoint Data Scan > Inventory > Removable Storage Devices), you can do the following:
- **Overview**:
- **Usage Distribution by Department**: The percentage-wise distribution of removable storage device usage by department.
- **Usage Distribution by Action**: The percentage-wise distribution of removable storage device violation by action.
- Filter the data for a specific **User**, **Department**, or **Action** or search the data for a specific device.
- **Export**: Export the removable storage device-related data into a CSV file.
- View a list of devices with endpoints. For each device, you can view:
- **Device-Friendly Name**: The device name. Click a device name to open a drawer that shows removable storage device details. To learn more, see [Analyzing Device Details](/zia/analyzing-device-details).
- **Serial Number**: The removable storage device's serial number.
- **VID**: Vendor ID, the removable storage device's manufacturer.
- **PID**: The removable storage device's product ID number.
- **Endpoint Name: **The name of the endpoints connected to the user's device.
- **User: **The email address of the user.
- **Action: **The action taken when the policy rule was triggered.
- **Customize columns**: Rearrange the columns and search for column names on the page.
- **Create Device Rule**: Click **Create Device Rule **if you want to create a rule based on the parameters of the selected device. You are redirected to the **Add New Storage Device Rule** window. Make the changes as required and save. To learn more see, [Managing a Storage Rule](https://help.zscaler.com/zia/managing-removable-storage-rule).
Use the arrows at the bottom of the page to go to view the next entries. You can also select the number of entries you want to view in the table (15, 25, 50, or 100 rows).
![This image shows the Removable Storage Device Page](/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/inventory/about-inventory/Inventory_removable_storage_device.png)
[]On the Printers page (Analytics > Endpoint Data Scan > Inventory > Printers), you can do the following:
- **Overview**:
- **Usage Distribution by Department**: The percentage-wise distribution of printer usage by department.
- **Usage Distribution by Action**: The percentage-wise distribution of printer rule violation by action.
- Filter the data for a specific **User**, **Department**, or **Action** or search data for a specific printer.
- **Export**: Export the printer-related data into a CSV file.
- View a list of printers with endpoints. For each printer, you can view:
- **Printer Name**: The printer's name as it appears in the operating system list of printers. Click the printer's name to open a drawer that shows details of that printer. To learn more, see [Analyzing Printer Details](/zia/analyzing-printer-details).
- **UNC Path**: The Universal Naming Convention (UNC) path identifies the network location of the printer.
- **Port**: The communication endpoint through which a computer sends print jobs to a printer.
- **Endpoint Name: **The name of the endpoints connected to the user's device.
- **User: **The email address of the user.
- **Action: **The action taken when the policy rule was triggered.
- **Customize Columns**: Rearrange the columns and search for column names on the page.
- **Create Printer Rule**: Click **Create Printer Rule** if you want to create a rule based on the parameters of the selected printer. You are redirected to the **Add Printer Rule **window. Make the changes as required and save. To learn more see, [Managing a Printer Rule](https://help.zscaler.com/zia/managing-printer-rule).
Use the arrows at the bottom of the page to go to view the next entries. You can also select the number of entries you want to view in the table (15, 25, 50, or 100 rows).
![This image shows the Printers tab in the Inventory Page](/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/inventory/about-inventory/Inventory_printers.png)
[]On the Portable Devices page (Analytics > Endpoint Data Scan > Inventory > Portable Devices), you can do the following:
- Overview:
- **Usage Distribution by Department**: The percentage-wise distribution of portable storage device usage by department.
- **Usage Distribution by Action**: The percentage-wise distribution of portable storage device violation by action.
- Filter the data for a specific **User**, **Department**, or **Action **or search the data for a specific device.
- **Export**: Export the portable device-related data into a CSV file.
- View a list of devices with endpoints. For each device, you can view:
- **Portable Device Name**: The portable device name. Click the portable device name to open a drawer that shows scan details for that device. To learn more, see [Analyzing Portable Device Details](/zia/analyzing-portable-device-details).
- **Serial Number**: The portable device's serial number.
- **VID**: Vendor ID, the portable device's manufacturer.
- **PID**: The portable device's product ID number.
- **Endpoint Name: **The name of the endpoints connected to the user's device.
- **User: **The email address of the user.
- **Action**: The action taken when the policy rule was triggered.
- **Customize Columns**: Rearrange the columns and search for column names on the page.
Use the arrows at the bottom of the page to go to view the next entries. You can also select the number of entries you want to view in the table (15, 25, 50, or 100 rows).
![This image shows the Portable Devices tab in the Inventory Page](/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/inventory/about-inventory/Inventory_removable_portable_devices.png)
![This image shows the Inventory page](/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/inventory/about-inventory/Inventory_page.png)