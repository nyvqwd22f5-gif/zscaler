# About Discovered Devices
Source: https://help.zscaler.com/unified/about-discovered-devices
PDF: https://help.zscaler.com/pdf/com/en/1497591.pdf

The Discovered Devices page shows detailed information about all the discovered devices in the [Internet of Things (IoT) Discovery Report](/unified/about-iot-discovery-report), which includes Internet of Things (IoT) devices, servers, and unmanaged user devices. You can filter the table by device type, category, classification, or location.
Discovered Devices provide the following benefits and enable you to:
- Gain comprehensive insights into all the IoT devices, servers, and unmanaged user devices connected to your organization's traffic.
- Provide feedback on inaccurate or unknown device classification.
- Understand and evaluate IoT policy status and its impact on IoT device behavior.
- Analyze web logs for each device's traffic to secure your organization's traffic from potential threats posed by diverse device environments.
About the Discovered Devices Page
On the Discovered Devices page (Analytics > Internet & SaaS > Analytics > IoT Discovery Report > any section of the IoT Discovery Report), you can do the following:
- Show or hide filters.
- Download the data in a CSV format.
- Filter the table by Device Type, Category, Classification, Policy Status, or Location.
- Search for a device by its IP address or auto label.
- View a list of devices. For each device, you can see the following columns:
-
**IP Address**: The IP address of the device. Click on an IP address to open the page to get more insightful information on this device.
- [Detailed Information per IP Address](#slide-pane)
- **Device Type**: The device type.
- **Auto Label**: The device descriptor based on its internet traffic that allows users familiar with the network to identify the device. It may contain a model number, model name, OS, or manufacturer name.
- **Classification**: The IoT device classification for the device.
-
**Category**: The categorization of the classifications that the device falls under. The following categories are available:
- [Categories](#category-list)
- **Location**: The location from which the device is connected.
- **Policy Status**: The status of the policy (All, No Policies, or Applied). Policy Status is only applicable for IoT devices, not servers or unmanaged user devices.
- View all the insights logs related to the IP address. You are redirected to the [Web Insights Logs](/unified/about-insights-logs) page.
- [Provide feedback on an inaccurate or unknown device classification](/unified/providing-feedback-iot-device-classifications).
![The Discovered Devices page with a table, different data, and annotated sections.](/downloads/zia/dashboard-analytics/reports/about-discovered-devices/Discovered_devices_page.png)
- []Automotive
- Business & Industrial
- Consumer Electronics
- Laptops & Desktops
- Networking & Storage
- Servers
- Smart Home & Office
- Smart Phones, Tablets & Watches
- Unknown
[]The detailed information per IP address page consists of the following sections:
- [1. Device Details](#device_details)
- [2. Web Policy](#web_policy)
- [3. Data Consumption Trend](#data_consumption_trend)
- [4. Traffic Flows](#traffic_flows)
Additionally, you can click **View Logs** to open Web Insights Logs for the device or click [Submit Feedback](/unified/providing-feedback-iot-device-classifications) to provide feedback on incorrect or unknown device classification to the AI/ML engine.
![A page showing detailed information per IP address with data and charts.](/downloads/zia/dashboard-analytics/reports/about-discovered-devices/Discovered_devices_ipaddress.png)
[]This section shows the auto label, category, classification, location, type, and protocols used.
[]This section shows the following details:
- **Timestamp**: The reporting period that summarizes when the web policy was applied and when the policy action took place on the device.
- **Policy Status**: Displays if the IoT policy is applied or not.
- **Total IoT Policies**: Total number of IoT policies.
-
**Policy Action tables**: You can view details pertaining to the policy action (**Allow** or **Block**) in a table which provides details such as policy name, type of policy, and number of hits. You can click the number of hits to further drill down to view details of Policy Type, Policy Action, Total Hits, Allowed Domains, or Blocked Domains corresponding to the option you selected. You can view a list of Domain/IP with the Protocols and the number of hits for the allowed and blocked domains. You can additionally view logs, export data, or search for a particular domain.
[See Image.](#web_policy_drilldown)
Currently, only URL Filtering policy status and statistics data are available in the IoT Report. The default policy **None (default)** is a URL Filtering policy and not an IoT specific policy. Therefore, it is not counted as an IoT policy.
![The Web Policy section shows details of the total IoT Policies, the status of the policy, and a policy action table](/downloads/zia/dashboard-analytics/reports/about-discovered-devices/Web_policy1.png)
[]This section shows a graph with hourly details of the inbound, outbound, and total bandwidth consumption for the device in the last 24 hours.
[]This section shows a chart which displays a detailed traffic flow for the device on which IPs and corresponding domains it communicates with, along with the action that was taken.
[]![The Web Policy drill down drawer that contains more details about the policy.](/downloads/zia/dashboard-analytics/reports/about-discovered-devices/Web_policy_drilldown.png)