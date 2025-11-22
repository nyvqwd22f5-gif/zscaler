# Viewing Device Events Reports
Source: https://help.zscaler.com/zdx/viewing-device-events-reports
PDF: https://help.zscaler.com/pdf/com/en/1529314.pdf

Device events are captured in the ZDX Admin Portal to provide aggregated insights into common system and software crashes that impact users and their devices. You can analyze system crashes and software crashes across your organization or drill down into the user details page to understand the specific device event's information. You can then plan your next course of action to remediate the crashes.
Go to Analytics > Reporting > Device Events to view the aggregated view of critical device events.
The System Crashes and Software Crashes reports are shown for the previous 30 days by default.
Prerequisites
To view the Device Events reports, ensure:
- You have an Advanced subscription level for the Device Events reports. To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
- You're running the required versions of Zscaler Client Connector and ZDX Module. To learn more, see [Supported Versions & Compatibility](/zdx/supported-versions-feature-compatibility).
- Your admin role is configured to view the Device Events reports. To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
System Crashes Report
The System Crashes report displays impacted Windows devices that experience system crashes.
System crashes are categorized into:
- Blue Screens, commonly referred to as Blue Screen of Death (BSOD): System events that occur when the system reboots due to a stop code or bug check code.
- Unexpected Shutdown/Reboots: System events that occur when the system reboots without a stop code (e.g., long power button press).
In the System Crashes report, you see:
- Filter tools to view System Crashes data:
- Time range selection (**2 Hours** to **30 Days**)
- Filters (**Users**, **Devices**, **Vendors**, **Models**, **Operating System**, **User Groups**, **Departments**, or **Geolocations**)
- An overview of the total impacted users, devices, and system crashes for the selected time range.
- **Total Users Affected**: The total number of users affected that experience software crashes and its percentage change.
- **Total Devices Affected**: The total number of devices affected that experience software crashes and its percentage change.
- **Total System Crashes**: The total number of system crashes across your organization and its percentage change.
- View the supported versions of Zscaler Client Connector and ZDX Module. To learn more, see [Supported Versions & Feature Compatibility](/zdx/supported-versions-feature-compatibility).
- **Impacted Devices and Users**: Displays the number of impacted users and devices by date (i.e., the previous 30 days) when there is a system crash.
- **System Crashes By Type**: Displays the number of Blue Screens and Unexpected Shutdowns/Reboots.
- **System Crashes Tables**: Switch between views to review the following information:
- **Impacted Operating System**: Displays Impacted OS, Blue Screens, Unexpected Shutdowns/Reboots, and Total Devices.
- **Impacted Geolocations**: Displays Impacted Geolocations, Blue Screens, Unexpected Shutdowns/Reboots, and Total Devices.
- **Impacted Vendors**: Displays Impacted Vendors, Blue Screens, Unexpected Shutdowns/Reboots, and Total Devices.
- **Impacted Models**: Displays Impacted Models, Blue Screens, Unexpected Shutdowns/Reboots, and Total Devices.
-
**Device List**: Displays a list of impacted devices with the following information:
- **Device Name**: The name of the device.
- **User**: The user associated with the device name.
- **OS**: The operating system the device runs on.
- **Vendor**: The vendor that manufactured the device.
- **Model**: The device model.
- **Blue Screen (BSOD)**: The number of Blue Screens.
- **Unexpected Shutdowns/Reboots**: The number of unexpected shutdowns or reboots.
-
**Crashes Timeline**: View the Crashes Timeline to understand the types of crash events that occurred and their metrics details.
Under **Time**, you can [evaluate user details](/zdx/evaluating-user-details) at the selected time, and then you can analyze granular information (e.g., Applications, CPU Utilization, Memory, Battery Level, Disk, Network Bandwidth, User Device Events). You can access the user details page from the previous 14 days.
[See image.](#img_crashes-timeline)
On the Device list, you can:
- Download the **Device List** table by clicking the **Export** button.
- Arrange the displayed columns with the **Table Options** button.
- Sort the **Device List** based on the field (**Device Name**, **User**, **OS**, **Vendor**, **Model**, **Crashes**, **Hangs, Total Issues)**.
- Navigate through pages of impacted devices.
[See image.](#img_systemcrashes)
Software Crashes Report
The Software Crashes report displays impacted devices that experience software crashes or software hangs. You can view software crashes for both Windows and macOS devices, while software hangs are shown for Windows devices only.
In the Software Crashes report, you see:
- Filter tools to view Software Crashes data:
- Filter by **Users**, **Devices**, **Software Crash Types**, **Vendors**, **Models**, **Operating System**, **User Groups**, **Departments**, or **Geolocations**.
- Select a time range to display Software Crashes data.
- Search for software by name.
-
In the Software list, you see:
- **Name**: The name of the impacted software that experienced a software crash. Select a software to view its [details](#details).
- **OS**: The operating system of the software.
- **Publisher**: The publisher of the software.
- **User Interface:** Whether there is a user interface impacted.
- **Total Crashes**: The total number of software crashes.
- **Total Hangs**: The total number of hangs.
- **Impacted Devices**: The number of impacted devices.
On the Software list, you can:
- Arrange the displayed columns with the **Table Options** button.
- Sort the **Device List** based on the field (**Device Name**, **User**, **OS**, **Vendor**, **Model**, **Blue Screen (BSOD)**, **Unexpected Shutdowns/Reboots**).
- Navigate through pages of impacted devices.
[See image.](#img_softwarecrashes)
[Software details](#details) are not displayed until a software is selected.
[]Software Details
When you select software, you see:
-
**Software Name**: The name of the software. You can opt to select a different software to view by clicking **Expand to select different software** and then selecting a different software.
[See image.](#img_softwarecrash_expand_selection)
- **Software Overview**: An overview of the total impacted users, devices, and software crashes.
- **Total Users Affected**: The total number of users affected that experience software crashes and its percentage change
- **Total Devices Affected**: The total number of devices affected that experience software crashes and its percentage change.
- **Total Software Crashes**: The total number of software crashes across your organization and its percentage change.
- View the supported versions of Zscaler Client Connector and ZDX Module. To learn more, see [Supported Versions & Feature Compatibility](/zdx/supported-versions-feature-compatibility).
- **Impacted Devices and Users**: The number of impacted devices and users across the selected time range.
- **Software Crashes By Type**: The number of software crashes across the selected time range.
-
**Software Crashes and Hangs Tables**: Switch between views to analyze where the most impacted software crashes and hangs are.
- **Versions**: A list of impacted software versions.
- **Geolocations**: A list of impacted geolocations.
- **Vendors**: A list of impacted vendors.
- **Models**: A list of impacted models.
- **OS**: A list of impacted OSs.
Each selected view contains:
- **Software Crashes**: The number of software crashes.
- **Software Hangs**: The number of software hangs associated.
- **Total Devices**: The total number of impacted devices.
-
**Device List**: View the device list for the following information:
- **Device Name**: The name of the device.
- **User**: The user associated with the device name.
- **OS**: The operating system of the software.
- **Vendor**: The vendor that manufactured the device.
- **Model**: The device model.
- **Crashes**: The total number of crashes the device is experiencing.
- **Hangs**: The total number of software hangs the device is experiencing.
- **Total Issues**: The total number of crashes and hangs.
-
**Issues Timeline**: View the Issues Timeline to understand the types of crash events that occurred and their metrics details.
Under **Time**, you can [evaluate user details](/zdx/evaluating-user-details) at the selected time, and then you can analyze granular information (e.g., Applications, CPU Utilization, Memory, Battery Level, Disk, Network Bandwidth, User Device Events). You can access the user details page from the previous 14 days.
[See image.](#img_issues-timeline)
On the Device list, you can:
- Download the **Device List** table by clicking the **Export** button.
- Arrange the displayed columns with the **Table Options** button.
- Sort the **Device List** based on the field (**Device Name**, **User**, **OS**, **Vendor**, **Model**, **Blue Screen (BSOD)**, **Unexpected Shutdowns/Reboots**).
- Navigate through pages of impacted devices.
[See image.](#img_individual_software)
Caveat
ZDX collects data for single-user access per device. If there are multiple users on a device, then ZDX collects data for each user and the associated device. This scenario increases the device data aggregation.
For example:
- User A is on Device X.
- User B is also on Device X.
- User A and User B access Device X at different times.
In this scenario, ZDX collects two separate device data when:
- User A is on Device X.
- User B is on Device X.
[]
![View which devices are experiencing system crashes](/downloads/zdx/analytics/viewing-device-events/zdx-device-events-1-B.png)
[]
![View the Crashes Timeline of a user's device](/downloads/zdx/analytics/viewing-device-events/zdx-device-events-crashes-timeline.png)
[]
![Expand to select a different software](/downloads/zdx/analytics/viewing-device-events/zdx-expand-to-select-different-software_0.png)
[]
![View which software are experiencing crashes](/downloads/zdx/analytics/viewing-device-events/zdx-device-events-software-crashes.png)
[]
![Select to view an individual software details on the crash](/downloads/zdx/analytics/viewing-device-events/zdx-expand-to-select-different-software-1.png)
[]
![View the Issues Timeline to view device event metrics](/downloads/zdx/analytics/viewing-device-events/zdx-device-events-issues-timeline.png)