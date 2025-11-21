# Monitoring the Device Health Dashboard
Source: https://help.zscaler.com/zdx/monitoring-device-health-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1529520.pdf

The Device Health dashboard uses existing user and device data to create a comprehensive device health scoreboard that monitors the performance of Windows and macOS devices. The dashboard provides useful data in evaluating trends to identify and understand the root causes of poor-performing devices. Then you can proactively collect device data and identify which devices require an IT's attention to remedy the device's poor performance (e.g., high CPU usage). With a dedicated dashboard, you can target hardware upgrades based on the device's usage for greater cost-effectiveness.
The Device Health Score provides a comprehensive view of struggling devices across an entire organization, department, user group, or location. The score is determined by individual contributing metrics (e.g., CPU usage, memory usage, disk usage). The Device Health Scores are categorized as:
- **Good**: The usage profile has an acceptable Device Health Score and ranges from 66-100. The color for this range is green.
- **Okay**: The usage profile has an acceptable Device Health Score and ranges from 34-65. The color for this range is amber.
- **Poor**: The usage profile has a below an acceptable Device Health Score and ranges from 0-33. The color for this range is red.
All scores are rounded to the nearest whole number.
Prerequisites
To monitor device performance within the Device Health dashboard, ensure:
- Your ZDX subscription level supports monitoring the Device Health dashboard. To learn more, see [Ranges & Limitations](https://help.zscaler.com/zdx/ranges-limitations).
- Your ZDX role has the proper permission level. To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
Viewing the Device Health Dashboard
To access the Device Dashboard, go to **Dashboard** > **Device Health Dashboard**. You can view [Thresholds](#thresholds) to understand the device metrics.
Access the [Summary](#summary), [Device List](#devicelist), or [Hardware Analysis](#hardwareanalysis) tab to monitor device performance at varying levels in your organization.
[]Summary
The Summary provides device health analysis, a geographical map of impacted devices, and profiles based on device usage. You can filter by **Vendors**, **Models**, **Profiles**, **Operating System**, **Geolocations**, **User Groups**, or **Departments**. Time range options are available in increments from the previous **2 Hours** to **48 Hours**, or a **Custom Range** within the last 14 days. Use the time range filter and page filters to help narrow your scope of information.
You can view the following:
- **Organization Device Health Score**: Displays the overall health of devices across the organization by using key performance indicators (e.g., CPU Usage, Memory Usage, Disk Usage).
- **Devices Health Over Time**: View how devices are impacted over time. Switch between the **Device Health Trend** or **Impacted Device** views.
- **Device Health Trend**: Displays the health of devices using the categories of Good, Okay, and Poor devices.
- **Impacted Device**: Displays the number of impacted devices over time.
- **Device Health by Region**: A map to highlight the most impacted geolocations with a high number of impacted devices with poor experience.
- **Useful Links**: Navigate to additional device monitoring data pages on the ZDX Admin Portal.
- **Hardware Usage Analysis**: Devices are categorized into usage profiles based on their average CPU and memory usage.
- **Device Count By Usage Profile**: The number of impacted devices are categorized into Light, Normal, and Power based on their device usage profile.
- **Device Count by Hardware Profile**: The number of impacted devices are categorized into Low, Standard, and High based on the hardware profiles,
[See image.](#img_summary)
[]Device List
The Device List provides an exportable list of impacted devices for viewing purposes.
You can filter by **Device Scores**, **Vendors**, **Models**, **Profiles**, **Operating System**, **Geolocations**, **User Groups**, or **Departments**. Time range options are available in increments from the previous **2 Hours** to **48 Hours**, or a **Custom Range** within the last 14 days. Use the time range filter and page filters to help narrow your scope of information.
On the **Device List** tab, you can view a list of impacted devices with the following information:
- **Name**: The name of the device. Clicking the device name allows you to [evaluate user details](/zdx/evaluating-user-details).
- **User**: The user associated with the device name. Clicking the user allows you to [evaluate user details](/zdx/evaluating-user-details).
- **Device Health**: The Device Health Score and its classification (**Poor**, **Okay**,** **or **Good**).
- **User Groups**: The user group of the user.
- **OS**: The operating system of the device.
- **Device Vendor**: The hardware vendor of the device.
- **Hardware Model**: The hardware model number.
- **Software Crashes**: The number of software crashes the device experienced in the selected time range.
- **Software Hangs**: The number of software hangs the device experienced in the selected time range.
- **Total Software Issues**: The total number of software issues when the device experienced in the selected time range.
-
**Software Issues Score**: The calculated score for software stability and performance based on the number of software issues (i.e., software crashes or software hangs).
There might be inaccurate scores due to insufficient data if the device is unavailable for the majority of the time. You can opt to hide these data points.
You can export the Device List as a CSV file.
[See image.](#img_devicelist_overview)
Contributing Factors
You can configure the view of the Device List if you click **Select Contributing Factors**. Each Contributing Factor view adds additional information about the factor on the Device List:
- **CPU Usage**: View the **CPU Usage Score** that reflects the device's CPU usage.
- **Memory Usage**: View the **Memory Usage Score** that reflects the device's RAM usage.
- **Disk Usage**: View the **Disk Usage Score** to reflect the device's disk usage.
- **Average Disk Queue Length**: View the **Average Disk Queue Length Score** that reflects disk queue length as a metric for disk I/O performance.
- **Battery**: View the **Battery Score** that reflects the device's battery usage performance.
- **Wi-Fi Signal Quality**: View the **Wi-Fi Signal Quality Score** that reflects the Wi-Fi performance that the device is connected to.
- **System Crashes**: View the **Software Issues Score** that reflects the overall device system's health, which includes system crashes. You can also view the number of Unexpected Shutdowns and Unexpected Reboots for system crashes.
- **Software Crashes**: View the **Software Issues Score** that reflects the stability of the software by measuring the number of Software Crashes (i.e., Software Crashes and Software Hangs).
Click **Clear Selection** to reset to the default view.
When you are on a **Contributing Factor** view, and you see inaccurate scores, you can hide them by enabling the toggle. You can then focus on which scores are accurate.
[See image.](#img_devicelist_factors)
[]Hardware Analysis
View Hardware Analysis to understand the profiling of hardware and usage. Devices are categorized into profiles based on real-time usage and current hardware resources. Hardware Analysis includes:
- **Usage Analysis**: Comprehensive analysis of device usage (e.g., CPU usage, memory usage) and the number of impacted devices.
- **Inventory**: Holistic view of your organization's current hardware information (e.g., OS, vendor, memory, disk).
You can switch between the **Usage Analysis** and **Inventory** views.
Usage Analysis
Usage Analysis provides a comprehensive analysis of device usage (e.g., hardware usage, CPU usage, memory usage) and the number of impacted devices. This information is useful in identifying devices that are using a high number of resources based on their usage. An IT admin can focus and analyze the data to determine if a remediation solution is required. The Usage Analysis analyzes every 7 days, and you can look up to the previous 14 days of data.
You can filter by **Vendors**, **Models**, **Profiles**, **Operating System**, **Geolocations**, **User Groups**, or **Departments**.
You can view:
-
**Hardware Usage Analysis**: The hardware profiles and usage profiles for each device. A hardware profile is based on the hardware allocation, while a usage profile is based on the users and device usage trends.
Each device is categorized based on its hardware profile and usage profile as follows:
- **Over Provisioned**: A device has a higher number of acceptable hardware resources. This indicates there is an inefficient use of resources allocated and there is an opportunity to optimize resource allocation to reduce costs or redistribute resources. The color for this range is amber.
- **Right Sized**: A device is right sized when the acceptable amount of resources matches its usage level. This indicates an efficient allocation of resources. The color for this range is green.
- **Under Provisioned**: A device does not have enough resources for its current usage level. This indicates potential performance issues. Zscaler recommends upgrading hardware to adjust for the device's necessary resources. The color for this range is red.
-
**Device Count By Usage Profile** or **Hardware Profile**: Switch between **Usage Profile** or **Hardware Profile** views.
- **Usage Profile**: The number of devices based on CPU and memory usage over the previous 14 days and based on the OS. The usage profiles are categorized into:
- **Light**: The device uses a lower than acceptable amount of processing usage.
- **Normal**: The device uses an acceptable amount of processing usage.
- **Power**: The device uses a higher than acceptable amount of processing usage.
- **Hardware Profile**: The number of devices and their hardware profile of RAM, Disk Size, Disk Type, CPU speed, number of cores, and logical processors. The hardware profiles are categorized into:
- **Low**: The device uses a lower than acceptable hardware configuration.
- **Standard**: The device uses an acceptable hardware configuration.
- **High**: The device uses a higher than acceptable hardware configuration.
Each profile is categorized using [predefined thresholds](#thresholds) for comparison.
- **Device Distribution**: View hardware distribution based on the number of devices.
- Switch between **Vendor**, **Model**, **CPU**, **Memory**, or **Disk** views.
- **Vendor**: View the distribution of devices across vendors.
- **Model**: View the distribution of devices across device models.
- **CPU**: View the distribution of devices with CPUs.
- **Memory**: View the distribution of devices with RAM allocation.
- **Disk**: View the distribution of devices with disk storage allocated.
- Switch between **Department** and **User Groups** views.
- **Department**: View the number of devices associated with a department.
- **User Groups**: view the number of devices associated with a user group.
- A Device List table with the following information:
- **Name**: The name of the device. Clicking the device name allows you to [evaluate user details](/zdx/evaluating-user-details).
- **User**: The user associated with the device name. Clicking the user allows you to [evaluate user details](/zdx/evaluating-user-details).
- **Device Health**: The Device Health Score and its classification.
- **User Groups**: The user group of the user.
- **OS**: The operating system of the device.
- **Hardware Profile**: The hardware profile classification of the device.
- **Usage Profile**: The usage profile classification of the device.
[See image.](#img_hardwareanalysis_usage)
Inventory
Inventory allows you to view all current hardware information (e.g., **OS**, **Vendor**, **Memory**, **Disk**) and provide a holistic view of your organization's device inventory. The device data are gathered from the previous 14 days.
You can filter by **Vendors**, **Models**, **Operating System**, **Geolocations**, **User Groups**, or **Departments**.
You can view:
- **Device Distribution**: View hardware distribution based on the number of devices.
- Switch between the **OS**, **Vendor**, or **Model** views.
- **OS**: View a pie chart of the number of devices associated with an OS.
- **Vendor**: View a bar chart of the number of devices associated with a vendor.
- **Model**: View a bar chart of the number of devices and their respective device model.
- Switch between **Department**, **User Groups**, **CPU**, **Memory**, or **Disk** views.
- **Department**: View a bar chart of the number of devices associated with a department.
- **User Groups**: View a bar chart of the number of devices associated with a user group.
- **CPU**: View a bar chart of the distribution of devices with CPUs.
- **Memory**: View a bar chart of the distribution of devices with RAM allocation.
- **Disk**: View a bar chart of the distribution of devices with disk storage allocated.
-
A Device List table with the following information:
- **Name**: The name of the device. Clicking the device name allows you to [evaluate user details](/zdx/evaluating-user-details).
- **User**: The user associated with the device name. Clicking the user allows you to [evaluate user details](/zdx/evaluating-user-details).
- **Operating System**: The operating system of the device.
- **Geo Location**: The geolocation of the device.
- **Device Vendor**: The vendor of the device.
- **Device Model**: The model name of the device.
- **CPU**: The CPU of the device.
- **Memory (RAM)**: The amount of memory RAM of the device.
- **Disk Size**: The storage disk size of the device.
- **Disk Type**: The type of storage disk for the device.
You can export to download a CSV file of the device list.
[See image.](#img_hardwareanalysis_inventory)
[]Thresholds
You can view the thresholds for Device Scoring or Hardware Performance to understand how scoring is determined by clicking the Thresholds icon (![Click the Thresholds icon](/downloads/zdx/analytics/monitoring-devices-dashboard/ZDX-Devices-Dashboard-Thresholds.png)
) located in the upper-right corner of the page.
- [Device Scoring](#device_scoring)
- [Hardware Performance](#hardware_performance)
[]The key performance metrics are determined by the optimal values for what is considered Good, Warning, or Critical health. The thresholds are predetermined for the following metrics:
- **CPU Usage**: The percentage of processing power used by the device's central processing unit (CPU).
- **Memory Usage**: The percentage of RAM used by a device for a specific application.
- **Disk Usage**: The percentage of disk space used by a device.
- **Average Disk Queue Length**: The average amount of disk read and write requests the device experiences.
- **Battery**: The percentage of battery power used for the device.
- **Wi-Fi Signal Quality**: The percentage of Wi-Fi signal quality the device is connected to.
- **System Crashes**: The number of system crashes a device experiences.
- **Software Crashes**: The number of software crashes a device experiences.
[See image.](#img_thresholds_device_scoring)
[]The hardware profile is calculated based on the CPU speed, RAM, disk type, number of cores, and logical processors to distribute each profile into:
- **Low**: The hardware profile is categorized for less than 10% of the organization's distribution.
- **Standard**: The hardware profile is categorized for greater than 10% and below 90% of the organization's distribution.
- **High**: The hardware profile is categorized for greater than 90% of the organization's distribution.
Each hardware profile is compared to other devices within the organization.
The Utilization Profile Calculation calculates and categorizes based on the device's CPU and memory usage for the previous 14 days. The Utilization Profile Calculation distributes each usage profile into:
- **Light Usage**: The usage profile is considered acceptable when the device's CPU and memory usage is below 80%
- **Normal Usage**: The usage profile is considered moderate and acceptable when the device's CPU and memory usage range from 80 to 90%.
- **Power Usage**: The usage profile is considered high and strained when the device's CPU and memory usage is above 90%.
[See image.](#img_thresholds_hardware_performance)
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
![View the Summary tab](/downloads/zdx/analytics/monitoring-devices-dashboard/ZDX-Device-Health-Dashboard-Summary-1.png)
[]
![Analyze the device usage](/downloads/zdx/analytics/monitoring-devices-dashboard/ZDX-Devices-Hardware-Analysis.png)
[]
![View the inventory of your devices](/downloads/zdx/analytics/monitoring-devices-dashboard/ZDX-Devices-Hardware-Analysis-inventory.png)
[]
![View the Device Scoring thresholds](/downloads/zdx/analytics/monitoring-devices-dashboard/ZDX-Devices-Dashboard-Thresholds-Device-Scoring.png)
[]
![View the thresholds for Hardware Performance](/downloads/zdx/analytics/monitoring-devices-dashboard/ZDX-Devices-Dashboard-Thresholds-Hardware-Performance.png)
[]
![View the Device List Tab](/downloads/zdx/analytics/monitoring-devices-dashboard/ZDX-Devices-Dashboard-DeviceList.png)
[]
![Select a Contributing Factor to view](/downloads/zdx/analytics/monitoring-devices-dashboard/ZDX-Devices-Dashboard-Contributing-Factors.png)