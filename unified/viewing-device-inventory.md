# Viewing Device Inventory
Source: https://help.zscaler.com/zdx/viewing-device-inventory
PDF: https://help.zscaler.com/pdf/com/en/1396666.pdf

Device Inventory allows you to view current information about your organization's devices and their associated users.
Prerequisites
To view Device Inventory data, ensure:
- You're running the minimum required versions of Zscaler Client Connector and ZDX Module. To learn more, see [Supported Versions & Feature Compatibility](/zdx/supported-versions-feature-compatibility).
- Your ZDX subscription level supports Device Inventory. To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
- Your ZDX role has the proper permission level. To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
Viewing the Device Overview
You can access the Device Inventory page by doing either of the following:
- Go to **Inventory **> **Device Overview**. Use the filters to help you find specific devices, and select the associated color-coded tile.
- Go to **Inventory **> **Device Inventory**. Use the filters to help you find specific devices listed within the table.
Use the filters on the Device Overview page to narrow your scope of inventory information:
- **Vendors**: Supported hardware vendors.
- **Models**: The device model name.
- **Zscaler Locations**: The list of locations where a user accessed a device, as defined in Zscaler Internet Access (ZIA). To learn more, see [About Locations](/zia/about-locations).
- **Geolocations**: The geographic areas where users accessed their devices.
View the current device count and the total active users from the last 14 days until the start of the UTC day. The percentage in each card indicates how the count has increased or decreased over the past 24 hours.
![Cards that show current counts for Devices and Users](/downloads/zdx/analytics/about-device-inventory-draft/zdx-device-user-count_0.png)
Hover over the bar charts to view memory distribution and OS distribution:
- **Memory Distribution**: Amount of memory installed and allotted per device.
- **OS Distribution**: Number of devices per OS.
![Memory and OS Distribution](/downloads/zdx/analytics/about-device-inventory/zdx-device-memory-os.png)
Select the Device Model
The Device Inventory tiles are color-coded according to device, with the size of each tile visually indicating the number of device models relative to other models. For example, the following image shows the same number of Lenovo models (in green) being used as the number of Apple models (in blue):
![Device Inventory colored tiles per device model](/downloads/zdx/analytics/inventory/viewing-device-inventory/zdx-device-inventory-tiles4.png)
To view details about a specific device model:
- Hover over the tile to view the total number of users of that device model.
- Select the tile.
[See image.](#os-tile)
The Device Inventory page is displayed with all models associated with the device and with device users automatically filtered and applied per model.
[]Viewing Device Inventory
The Device Inventory page provides a current snapshot of your users' devices. Use the filters at the top of the page to narrow your search for a specific device and its associated user. The table on the Device Inventory page provides the following information for each listed device:
- **Name**: The vendor device name, with model and OS.
- **User**: The device user.
- **OS**: The operating system running on the device.
- **Vendor**: The name of the device provider.
- **Hardware Model**: The specific model name of the device.
- **CPU**: The processor model.
- **Memory (RAM)**: The amount of memory installed on the device.
![Device Inventory table](/downloads/zdx/analytics/inventory/viewing-device-inventory/zdx-device-inventory-table-headings6.png)
Additionally, the following actions are available within the Device Inventory table:
- To view more information about a specific device, first select its name, and then select the **Hardware**, **Network**, or **Software **tab in the **User Device Information** window.
[See image.](#user-device-info)
- To view more information about the user associated with the device, select the user in the device inventory table to display user details. To learn more, see [Viewing Software Inventory](/zdx/viewing-software-inventory).
- To capture all device information within the table in CSV format, click **Export**, and then click the **Download **icon. The download process captures all currently known devices.
[]![Tile tooltip upon hover](/downloads/zdx/analytics/inventory/about-device-inventory/zdx-device-inventory-tile_tooltip2.png)
[]![User Device Information window](/downloads/zdx/analytics/inventory/viewing-device-inventory/zdx-device-inventory-user-device-information3.png)