# Viewing Software Inventory
Source: https://help.zscaler.com/zdx/viewing-software-inventory
PDF: https://help.zscaler.com/pdf/com/en/1391206.pdf

Software Inventory allows you to view current and historical information about software versions and updates on your users' devices.
Prerequisites
To view Software Inventory data, ensure:
- You're running the minimum required versions of Zscaler Client Connector and ZDX Module. To learn more, see [Supported Versions & Feature Compatibility](/zdx/supported-versions-feature-compatibility#SoftwareAndDeviceInventory).
- Your ZDX subscription level supports Software Inventory. To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
- You've enabled the setting for inventory data collection. To learn more, see [Configuring Inventory Settings](/zdx/configuring-inventory-settings).
Availability of Software Inventory data might take up to one day after Data Collection is enabled.
Viewing the Software Overview
You can access the Software Inventory page by doing either of the following:
- Go to **Inventory **> **Software Overview**. Use the filters to help you find specific software or applications, and select the associated color-coded tile.
- Go to **Inventory **> **Software Inventory**. Use the filters to help you find specific software or applications listed within the table.
Use the filters on the Software Overview page to narrow your scope of inventory information:
- **Software App Groups**: Supported vendor software or individual applications, grouped by name.
- **Vendors**: Software or application vendors.
- **Zscaler Locations**: The list of locations where a user accessed a device, as defined in Zscaler Internet Access (ZIA). To learn more, see [About Locations](/zia/about-locations).
- **Geolocations**: The geographic areas where users accessed their devices.
View the current count for installed software and vendors, and the total users from the day Software Inventory was enabled until the start of the UTC day. The percentage in each card indicates how the count has increased or decreased over the past 24 hours.
![Software Overview cards](/downloads/zdx/analytics/inventory/viewing-software-inventory/zdx-sw-overview-cards3.png)
Select the Software or Application
Installed software and applications are grouped and color-coded according to their vendors, with the size of each tile visually indicating the number of installations per software or application relative to other software or applications installed on user devices. For example, the following image shows the grouping of vendors, with Microsoft Teams and Microsoft Visual C++ as having the most installations among Microsoft Corporation applications:
![Software Inventory vendor grouping](/downloads/zdx/analytics/about-software-inventory-draft/zdx-sw-overview-vendor-tree.png)
To view details about a specific application or software:
- Hover over the software or application tile within the vendor group. A tooltip displays the total number of installations for the software or application, as well as the total number of version names for the software or application.
- Select the tile.
![Example of tile tooltip on Software Overview page](/downloads/zdx/analytics/about-software-inventory-draft/zdx-sw-overview-tile-tooltip.png)
One of the following pages is displayed:
- If the software or application has more than one version name, the version names are displayed within a table on the [Software Inventory](#view-sw-inventory) page.
- If the software or application does not have more than one version name, the [software details](#view-sw-details) page is displayed.
[]Viewing Software Inventory
The Software Inventory page provides a snapshot of your users' installed applications and software. Use the filters at the top of the page to narrow your search for a specific application or software. The table on the Software Inventory page provides the following information:
- **Name**: The software or application version name.
- **Version: **The numbered version of the software or application.
- **Software Group**: The group name to which the software or application belongs.
- **OS**: The operating system on which the software or application is run.
- **Users**: The number of software or application users.
- **Devices**: The number of hardware devices on which the software or application is running.
- **End of Life**: The date when the installed software is no longer supported or maintained by the vendor.
- **End of Support**: The date when the installed software no longer receives updates, patches, or technical assistance from the vendor.
- **Vendor**: The software or application provider.
![Example of Software Inventory Table ](/downloads/zdx/analytics/inventory/viewing-software-inventory/zdx-sw-inventory-view.png)
The following actions are available within the software inventory table:
- To view details about a specific version of the software or application, select its name within the table. The software details page is displayed.
- To capture all filtered installations within the table in CSV format, click **Export**, then click the **Download **icon. The download process captures all known installations every 24 hours.
[]View Software Details
The software details page provides granular information about a specific version of an application or software:
- **Users**: A percentage indicates how the user count for the selected software or application has increased or decreased over the past 24 hours.
- **OS Distribution**: On hover, the bar chart shows the operating systems and number of users per operating system for the selected software or application, delineated by color.
- **Version Distribution**: On hover, the bar chart shows the selected software or application versions and number of users per version, delineated by color.
[See image.](#sw-details-page)
The software details table provides the following information for each software or application version:
- **Device**: The hardware device on which the software or application is running.
- **User**: The name of the user running the software or application. To learn more, see [View User Details](#view-user-details).
- **Software Version**: The numbered version of the software or application.
- **OS**: The operating system on which the software or application is run.
- **Location**: The folder on the user's system where the software or application is found.
- **Install Date**: The date when the software or application was originally installed.
- **End of Life**: The date when the installed software is no longer supported or maintained by the vendor.
- **End of Support**: The date when the installed software no longer receives updates, patches, or technical assistance from the vendor.
- **Version History**: Click the **View **icon to display the date when the software or application was last updated.
[See image.](#version-history)
To view user details about the software or application, select the user name in the table.
[]View User Details
The user details page provides granular information about the applications or software installed for a specific user. The **Vendor Distribution** bar chart indicates the user's total software or application count per vendor. Hover over any color within the chart to view an individual vendor and its associated software count.
![Vendor Distribution graph](/downloads/zdx/analytics/about-software-inventory-draft/zdx-user-details-vendor-distribution2.png)
The user details table provides the following information for the selected user:
- **Name**: The software or application name run by the user.
- **Device**: The hardware device on which the software or application is running.
- **Version**: The specific version of the software or application.
- **Status**: Indicates whether the software or application is currently installed.
- **Vendor**: The name of the software or application provider.
- **Location**: Indicates where the software or application is installed on the user's system.
- **Install Date**: The date when the software or application was originally installed.
- **Version History**: Launches a window to display the date when the software or application version was last updated.
[See image.](#user-details-page)
[]![Software Details Page](/downloads/zdx/analytics/inventory/viewing-software-inventory/zdx-sw-details-tables.png)
[]![Pop-up to view software version history](/downloads/zdx/analytics/about-software-inventory-draft/zdx-sw-details-version-history.png)
[]![Software Inventory user details page](/downloads/zdx/analytics/inventory/viewing-software-inventory/zdx-user-details-page3.png)