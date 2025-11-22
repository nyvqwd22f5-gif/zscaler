# Understanding Alert Triggers
Source: https://help.zscaler.com/zdx/understanding-alert-triggers
PDF: https://help.zscaler.com/pdf/com/en/1389151.pdf

[Watch a video about configuring alerts in ZDX](https://fast.wistia.net/embed/iframe/5ozc9luba9)
Each alert rule can be triggered differently based on the type of alert rule. Each alert rule type (Application, Device, Incident, Network, or Call Quality) has different criteria for an alert rule to trigger based on their metrics. If the criteria are met, then the alert triggers and provides notification through an [alert email](/zdx/understanding-alerts-email).
The alerts triggered have a display delay of 30 minutes.
Based on the alert rule type, you get the following throttling criteria:
- [Application, Device, or Network](#appdevnet)
- [Incident](#inc)
- [Call Quality](#CallQuality)
Alert Criteria Examples
The following are examples of alert criteria based on the rule type:
- [Application, Device, or Network](#ex-app-dev-net)
- [Incident](#ex-inc)
- [Call Quality](#ex-call-quality)
[]
- **Alert Only if Repeated**: The number of times a situation should repeat for an alert to be triggered.
- **Number of Active Devices is**: The number of active devices impacted based on the In Group selection.
- **Minimum Devices Impacted**: The number or percentage of devices impacted based on the In Group selection.
- **In Group**: The Departments, Cities, Organization, Regions, or Zscaler Locations the alert applies to.
[]
For any [incident type](/zdx/monitoring-incidents-dashboard#understand), you can configure throttling criteria based on Impacted Devices. The minimum number of impacted devices depends on the incident type.
If you select multiple incident types, the criteria are predefined to meet the minimum devices and, if applicable, the global minimum threshold.
[]For Call Quality, you can configure the following throttling criteria:
- **MOS**: The Mean Opinion Score (MOS) is integrated into the ZDX Score to rate a call's quality.
-
**ZDX Score**: The following Call Quality metrics are used to determine the score:
- **Latency**: The time taken to send a data packet from point A to point B, such as the hop between legs within the Cloud Path.
- **Jitter**: The variance in time delay between data packets over a network.
- **Packet Loss**: When data packets that travel across a computer network fail to reach their destination.
The ZDX Score for Call Quality is calculated by one of the following methods, utilizing values for latency, jitter, and packet loss:
- Using the MOS (Rated from 1 to 5, worst to best)
- Using metric thresholds
To learn more, see [About the ZDX Score](/zdx/about-zdx-score).
[]
You can have the following alert criteria for application, device, or network type:
- **Alert Only if Repeated** 3 **Times in a Row**
- **Number of Active Devices**: 5
- **Minimum Devices Impacted**: 20%
- **Page Fetch Time (PFT)**: > 1000ms
- **In Group**: Cities (city = Cairo)
Scenario with Alert Criteria Not Met
If there is only one device present in Cairo and the following conditions are not met:
- The PFT of the device exceeds `1000`ms.
- This situation repeats `3` times in a row.
- The minimum devices impacted is `1`.
The alert won't trigger because there is only one active device in Cairo and therefore does not meet the **Number of Active Devices: 5** condition.
Scenario with Alert Criteria Met
If there are 5 active devices (Device 1 to 5) and the following conditions are met:
- The PFT of the device exceeds `1000`ms.
- This situation repeats `3` times in a row.
- The minimum devices impacted is `1`.
Then an alert is triggered at T3 as shown in the following table.
| **Device #** | **Times in a Row (T1)** | **Times in a Row (T2)** | **Times in a Row (T3)** | **Alert Result** |
| ------------ | ----------------------- | ----------------------- | ----------------------- | ---------------- |
| **Device 1** | Device impacted | Device impacted | Device impacted | Alert triggered |
| **Device 2** | Device impacted | Device impacted | Device impacted | Alert triggered |
| **Device 3** | Device impacted | Device impacted | Device impacted | Alert triggered |
| **Device 4** | Device impacted | Device impacted | Device impacted | Alert triggered |
| **Device 5** | Device impacted | Device impacted | Device impacted | Alert triggered |
Alerts by Cities Filter
If you are setting up alerts based on the cities the devices are in, select **Cities** from the **In Group** drop-down menu. An alert triggers when the criteria you have set up for the alert are met. In this example, an alert triggers when all of the following occur:
- Page Fetch Time (PFT) of an application exceeds `1000`ms (added in the Configure Rule tab).
- There are `10` devices in `<city_name>` city.
- There are at a minimum `5` devices impacted.
- The above situation repeats `5` times in a row.
Alerts by Organization Filter
If you are setting up alerts based on the organization the devices are in, select **Organization** from the **In Group** drop-down menu. An alert triggers when the criteria you have set up for the alert are met. In this example, an alert triggers when all of the following occur:
- Page Fetch Time (PFT) of an application exceeds `1000`ms (added in the Configure Rule tab).
- There are `10` devices across the organization.
- There are at a minimum `5` devices impacted.
- The above situation repeats `5` times in a row.
Alerts by Cities and Geolocations Filter
If you are setting up alerts based on city grouping using the geolocation filter, click **Add Filter** in the **Filters** tab, and select **Geolocations**. Choose the desired cities from the drop-down menu. An alert triggers when the criteria you have set up for the alert are met. In this example, an alert triggers when all of the following occur:
- Cities are defined in the **Geolocations** filter (e.g., city = Atlanta).
- Page Fetch Time (PFT) of an application exceeds `1000`ms (added in the Configure Rule tab).
- There are `10` devices in group=city.
- There are at a minimum `5` devices impacted.
- The above situation repeats `5` times in a row.
[][]
An incident requires a minimum number of devices impacted depending on if it is impacted globally (across an organization) or locally (per location).
An incident that requires both a global and local threshold (Last Mile ISP - Brownout, ZIA Public Service Edge, ZPA Public Service Edge), must meet both requirements for the alert to trigger. For example, if a Last Mile ISP - Brownout incident involves the following:
- Globally, there are 14 impacted devices.
- Locally, there are 4 or 5 impacted devices per location.
Since there are 4 impacted devices for a location, the alert does not trigger because it requires a minimum of 5 impacted devices per location. This is because the minimum global threshold (10) and local threshold (5) are not met.
For ZPA - App Connector incidents, you must have at least 10 impacted devices across all ZPA App Connector locations to trigger an alert.
In the following table are the alert conditions and example totals to trigger an alert:
- **Incident Type**: The type of incident.
- **Global Minimum**: The minimum number of global impacted devices required.
- **Local Minimum**: The minimum number of local impacted devices required.
- **Global Total**: The actual total number of global impacted devices as an example.
- **Local Total**: The actual total number of local impacted devices as an example.
- **Alert Result**: The alert result is based on the conditions given (Not Triggered, Triggered).
| Incident Type | Global Minimum | Local Minimum | Global Total | Local Total | Alert Result |
| ------------- | -------------- | ------------- | ------------ | ----------- | ------------ |
| Application | 50 | N/A | 40 | N/A | Not triggered |
| Application | 50 | N/A | 50 | N/A | Triggered |
| Device - System Software Crash | 50 | N/A | 49 | N/A | Not triggered |
| Device - System Software Crash | 50 | N/A | 55 | N/A | Triggered |
| Device - System Software Hang | 50 | N/A | 45 | N/A | Not Triggered |
| Device - System Software Hang | 50 | 50 | N/A | N/A | Triggered |
| Last Mile ISP - Blackout | 20 | N/A | 19 | N/A | Not Triggered |
| Last Mile ISP - Blackout | 20 | N/A | 22 | N/A | Triggered |
| Wi-Fi | 4 | N/A | 3 | N/A | Not Triggered |
| Wi-Fi | 4 | N/A | 5 | N/A | Triggered |
| ZIA Public Service Edge | 15 | 120 | 10 | 120 | Not triggered |
| ZIA Public Service Edge | 15 | 120 | 16 | 90 | Not triggered |
| ZIA Public Service Edge | 15 | 120 | 16 | 120 | Triggered |
| ZPA - App Connector | N/A | 10 per App Connector location | N/A | 9 | Not Triggered |
| ZPA - App Connector | N/A | 10 per App Connector location | N/A | 11 | Triggered |
| ZPA - Public Service Edge | 100 | 10 | 90 | 11 | Not Triggered |
| ZPA - Public Service Edge | 100 | 10 | 110 | 9 | Not Triggered |
| ZPA - Public Service Edge | 100 | 10 | 110 | 11 | Triggered |
| Last Mile ISP - Brownout | 10 | 5 | 9 | 5 | Not Triggered |
| Last Mile ISP - Brownout | 10 | 5 | 12 | 4 | Not Triggered |
| Last Mile ISP - Brownout | 10 | 5 | 12 | 5 | Triggered |
| Wi-Fi | 4 | N/A | 3 | N/A | Not triggered |
| Wi-Fi | 4 | N/A | 5 | N/A | Triggered |
| ZIA Public Service Edge | 15 | 120 | 10 | 120 | Not triggered |
| ZIA Public Service Edge | 15 | 120 | 16 | 90 | Not triggered |
| ZIA Public Service Edge | 15 | 120 | 16 | 120 | Triggered |
| ZPA - App Connector | N/A | 10 per App Connector location | N/A | 9 | Not Triggered |
| ZPA - App Connector | N/A | 10 per App Connector location | N/A | 11 | Triggered |
| ZPA - Public Service Edge | 100 | 10 | 90 | 11 | Not Triggered |
| ZPA - Public Service Edge | 100 | 10 | 110 | 9 | Not Triggered |
| ZPA - Public Service Edge | 100 | 10 | 110 | 11 | Triggered |
[]
An alert for Call Quality is triggered when the Mean Opinion Score (MOS) or ZDX Score criteria and throttling conditions are met. For example, if you configured an alert with the following:
- Criteria
- MOS < 2
- ZDX Score < 60
- Throttling Conditions
- Number of Meetings is: 5
- Minimum Number of Active Participants is: 5
- Number of Impacted Active Participants is: 10
The alert for Call Quality triggers only if all the criteria and conditions are met.