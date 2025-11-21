# Understanding the Zscaler Client Connector Dashboard
Source: https://help.zscaler.com/unified/understanding-zscaler-client-connector-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1496991.pdf

The Zscaler Client Connector Dashboard provides information [about enrolled devices](/unified/about-enrolled-devices) for your organization, including information about service status..
To view dashboard information, go to Analytics > Client Connector > Dashboard.
Dashboard
The Dashboard option in the left-side navigation covers the following information:
- [Platform Details](#platform-details)
- [Device Posture](#device-posture-failure)
- [Device Events](#device-events)
[]This page provides OS platform details such as device model and device state.
Dashboard Filters
Use the following filters to modify the content shown in the Platform Details page widgets. After you select filters, click **Apply** in the upper-right corner of the page.
- **States**: View data for devices with all [device states](/unified/device-states-enrolled-devices), or a specific state (i.e., **Registered**, **Unregistered**, **Removal Pending**, **Removed**, **Quarantined**).
- **OS**: View data for all operating systems or a specific operating system.
Widgets
The Platform Details page provides the following widgets:
- [Version Distribution](#Sup-Unsupported)
- [Device Model](#Device-Model)
- [Device OS](#Device-OS)
- [Device State](#Device-State)
- [Enrolled Devices by Platform](#Zscaler-App-by-Platform)
- [License Usage](#Zscaler-App-License)
![Zscaler Client Connector Portal Dashboard](/downloads/zscaler-client-connector/monitoring-usage/about-failed-posture-devices/zclient-connector-platform-details-main-page.png)
[]This widget displays your organization's subscription and license information.
This widget only applies to Internet & SaaS. You won't see this widget if you only have Private Applications.
![ Zscaler Client Connector Portal License dashboard chart](/downloads/zscaler-client-connector/monitoring-usage/about-failed-posture-devices/zclient-connector-platform-details-license-usage.png)
-
Hover over the chart to view the following:
- **Subscribed**: The number of user subscriptions for Zscaler Client Connector.
- **Used**: The number of users that are enrolled to Zscaler Client Connector.
Licenses are calculated based on the unique username. For example, even if a user has Zscaler Client Connector installed on three devices, the user still has only one license.
- To view a list of all enrolled devices, click a category in the chart.
[]This widget displays the enrolled device models. It displays the top 5 device models and groups all other models in the Others category.
![Zscaler Client Connector Portal Device Model chart](/downloads/zscaler-client-connector/monitoring-usage/about-failed-posture-devices/zclient-connector-platform-details-device-model.png)
- Hover over the chart to view the following:
- The details for a specific device model, which includes:
- The model name
- The number of enrolled devices for the model
- The percentage of enrolled devices for the model
- The details for the Others category, which includes:
- The number of enrolled devices grouped under Others
- The percentage of enrolled devices grouped under Others
- To view a list in **Enrolled Devices **for all devices for a specific model, click the model in the chart.
- To view a list in **Enrolled Devices** for all devices in the Others category, click **Others **in the chart. The list of devices is organized by device model.
[]This widget displays the enrolled devices operating systems. It displays the top 5 OSs and groups all other OSs in the Others category.
![Zscaler Client Connector Portal Dashboard Device OS chart](/downloads/zscaler-client-connector/monitoring-usage/about-failed-posture-devices/zclient-connector-platform-details-device-os.png)
- Hover over the chart to view the following:
- The details for a specific OS, which includes:
- The OS name
- The number of enrolled devices for the OS
- The percentage of enrolled devices for the OS
- The details for the Other category, which includes:
- The number of enrolled devices grouped under Others
- The percentage of enrolled devices grouped under Others
- To view a list in **Enrolled Devices** for all devices for a specific OS, click the OS in the chart.
- To view a list in **Enrolled Devices** for all devices in the Others category, click **Others **in the chart. The list of devices is organized by OS.
[]This widget displays the states of the enrolled devices and the [app profiles](/unified/configuring-zscaler-client-connector-app-profiles) applied to the devices.
The possible device states are:
- Registered
- Unregistered
- Removal Pending
- Removed
- Quarantined
To learn more about device states, see [Device States for Enrolled Devices](/unified/device-states-enrolled-devices).
![Zscaler Client Connector Portal Device State dashboard chart](/downloads/zscaler-client-connector/monitoring-usage/about-failed-posture-devices/zclient-connector-platform-details-device-state.png)
- Hover over the chart to view the following:
- The state name
- The number of enrolled devices for the state
- The percentage of enrolled devices for the state
- To view a list in **Enrolled Devices** for all devices for a specific state, click the state in the chart.
[]This widget displays the enrolled devices platforms.
![Zscaler Client Connector Portal By Platform dashboard chart ](/downloads/zscaler-client-connector/monitoring-usage/about-failed-posture-devices/zclient-connector-platform-details-enrolled-devices.png)
- Hover over the chart to view the following:
- The platform name
- The number of enrolled devices for the platform
- To view a list in **Enrolled Devices** for all devices for a specific platform, click the platform in the chart.
[]This widget displays the number of devices installed with supported and unsupported versions of Zscaler Client Connector by OS.
![Zscaler Client Connector Portal Version Distribution dashboard chart](/downloads/zscaler-client-connector/monitoring-usage/about-failed-posture-devices/zclient-connector-platform-details-version-dist.png)
Hover over the chart to view the number of devices installed with supported and unsupported versions of Zscaler Client Connector, shown by percentage for each OS. Click the graph to view a list of all devices installed with either supported or unsupported versions of Zscaler Client Connector in Enrolled Devices.
[]This page provides information about Internet & SaaS and Zscaler Private Access (ZPA) service status and about users turning off the services via passwords.
This page is available for Windows users only. You must also have Digital Experience Monitoring or Zscaler Client Connector Telemetry (formerly [Health Metrics](/unified/configuring-zscaler-client-connector-app-profiles#Health_Metrics)) enabled.
Dashboard Filter
Use the **Time Range** filter to view data for the selected time range. After you select the filter, click** Apply** in the upper-right corner of the page.
Widgets
The Device Events page provides the following widgets:
- [ZIA and ZPA Device Service Status](#zia-zpa-device-service-status)
- [ZIA Service Turn Off](#zia-service-turn-off)
- [ZPA Service Turn Off](#zpa-service-turn-off)
- [Number of Times ZIA and ZPA Turned Off](#num-times-turned-off)
- [Password Usage](#password-usage)
- [Password Usage By Type](#password-usage-by-type)
![View the Device Events page of the Dashboard](/downloads/zscaler-client-connector/monitoring-usage/understanding-zscaler-client-connector-portal-dashboard/zclient-connector-device-events-dashboard_0.png)
[]This widget displays information about the total number of devices enrolled in each service. You can view the following:
- **ZDX**: The number of enrolled devices with the Digital Experience Monitoring service enabled.
- **Non-ZDX**: The number of enrolled devices without the Digital Experience Monitoring service enabled.
- **ZIA**: The number of enrolled devices with the Internet & SaaS service enabled.
- **ZPA**: The number of enrolled devices with the Private Applications service enabled.
- **Off ZIA**: The number of enrolled devices that have had the Internet & SaaS service turned off
- **Off ZPA**: The number of enrolled devices that have had the Private Applications service turned off.
[]This widget displays information about the enrolled devices that have had the Internet & SaaS service turned off. You can view the following:
- **Users**: The number of unique users who have turned off the service, even if they have turned it back on.
- **Total Number**: The total number of times the service has been turned off by the users, even if a user has turned it back on.
[]This widget displays information about the enrolled devices that have had the Private Applications service turned off. You can view the following:
- **Users**: The number of unique users who have turned off the service, even if they have turned it back on.
- **Total Number**: The total number of times the service has been turned off by the users, even if a user has turned it back on.
[]This widget displays information about the number of times Internet & SaaS and Private Applications were turned off over the course of the past 24 hours. Hover over the graph lines to display the number of devices turned off per service for a particular time.
[]This widget displays information about the passwords used to turn off the services. You can view the following:
- **Users**: The number of individual users who have turned off the service.
- **OTP**: The number of users who used the Disable ZIA OTP password or Disable ZPA OTP password from the [Device Details](/unified/viewing-device-fingerprint-enrolled-device) for the enrolled device.
- **Master**: The number of users who used the Disable Password ZIA password or Disable Password ZPA password from the [app profile](/unified/configuring-zscaler-client-connector-app-profiles).
[]This widget displays information about the passwords used to turn off the services. You can view the following:
- **ZIA OTP**: The number of times Internet & SaaS was turned off using the Disable ZIA OTP password.
- **ZPA OTP**:The number of times Private Applications was turned off using the Disable ZPA OTP password.
- **ZPA Master**: The number of times Private Applications was turned off using the Disable Password ZPA password.
- **ZIA Master**: The number of times Internet & SaaS was turned off using the Disable Password ZIA password.
[]The Device Posture dashboard is available for Windows users only.
In the Device Posture section of the Dashboard, admins can find information on the trendline of the top 10 posture profiles that have the highest number of devices failing their posture checks.
![Failed devices](/downloads/tech-pubs-drafts/client-connector-draft-articles/understanding-zscaler-client-connector-dashboard-mr-7703-doc-51391/zscaler-client-connector-portal-dashboard-device-posture-failed-devices-top-10.png)
Use the **Time** filter to modify the failed postures times ranging from three-hour intervals up to 24 hours. You can set the filter to show data up to the past 7 days.
To learn more, see [About Failed Posture Devices](/unified/about-failed-posture-devices). To view a complete list of devices that are failing for a specific posture, see [Viewing Device Fingerprint Information for a Failed Device Posture](/unified/viewing-device-fingerprint-information-failed-posture-devices).