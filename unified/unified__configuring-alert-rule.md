# Configuring an Alert Rule
Source: https://help.zscaler.com/unified/configuring-alert-rule
PDF: https://help.zscaler.com/pdf/com/en/1491761.pdf

You can configure alert rules to modify an expression to create criteria based on real-time user experience.
To configure a rule for an alert:
- Go to **Administration **>**Alerts** > **Rules**.
-
Click **Add Alert Rule**.
The **Add Alert Rule** window appears.
[See image.](#Add_New_Alert_Rule_Page)
- In the **Add Alert Rule** window:
- [a. Configure Rule](#Configure_Rule)
- [b. Filters](#Filters)
- [c. Criteria](#Criteria)
- [d. Action](#Action)
- [e. Review](#Review)
- Click **Save** and activate the changes.
The alerts triggered have a display delay of 30 minutes.
You can create a dynamic alert rule whenever the Network or Application rule type is applied. You can then modify the expression and add dynamic alerting with ZDX Score or ZDX Score Drops in the Criteria step. To learn more about Dynamic Alerting, see [Evaluating Individual Alert Details](/unified/evaluating-individual-alert-details).
[]On the **Configure Rule** tab:
- **Name**: Enter a name to identify the rule.
- **Status**: Select from **Enabled** or **Disabled**. Select **Enabled** to enable the rule.
- **Severity**: Select **High**, **Medium**, or **Low** options for severity, depending on the impact of this event on users.
-
**Type**: Choose from **Application**, **Device**, **Incident**, or **Network**.
Application and Network include ZDX Score and ZDX Score Drops detection as a criterion for Dynamic Alerting. This feature and its procedures are available based on your subscription level. To learn more, see [Ranges & Limitations](/unified/ranges-limitations#alerts).
If you select **Incident** as your type, you can specify which Incident Types to configure an alert rule for. If you select multiple incidents, the criteria are predefined for you based on their minimum thresholds. To learn more, see [Monitoring the Incidents Dashboard](/unified/monitoring-incidents-dashboard) and [Understanding Alert Triggers](/unified/triggering-alert).
[See image.](#IncidentAlertRuleType)
- **Labels (Optional)**: Select the applicable labels for the alert rule. You can also search for the label name to select. To learn more, see [About Labels](/unified/about-labels).
[See image.](#Configure-Rule)
[]
On the **Filters** tab, depending on your rule type, you get different parameters and filters.
You can also make additional selections from the drop-down menu or add multiple filters to further sort the information. You can select to include or exclude items from a filter, but you cannot choose to have both include and exclude for the same filter. For example, you can select Geolocations as a filter and specify to include North America. You cannot select Geolocations as a filter again to exclude other Geolocations.
[See image.](#SelectFilters)
When configuring an alert rule, consider the following:
- You cannot select deleted or unknown users for the include and exclude criteria.
- The limitation for selected items in the **Add Filter** menu is 250 items.
- [](/unified/about-applications-digital-experience-monitoring)
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
- [](/unified/adding-custom-application)
-
-
-
-
-
-
-
-
[](/unified/about-applications-digital-experience-monitoring)
-
-
-
-
-
-
-
| Rule Type | Parameters | Filters |
| --------- | ---------- | ------- |
| Application | **Application**: Choose a predefined application or custom application.**Web Probe**: Choose the Web probe for this application. | GeolocationsLocationsLocation GroupsDepartmentsUser GroupsUsersDevices |
| Device | Filters only | GeolocationsLocationsLocation GroupsDepartmentsUser GroupsUsersDevices |
| Incident | Filters only | GeolocationsDevicesUsers |
| Network | **Application**: Choose a predefined application or custom application that is a network application type.**Cloud Path Probe**: Choose the Cloud Path probe for this application. | GeolocationsLocationsLocation GroupsDepartmentsUser GroupsUsersDevices |
| Call Quality | **Application**: Choose a predefined application that is a Unified Communications as a Service (UCaaS) application. | GeolocationsLocationsLocation GroupsDepartmentsUser GroupsUsersDevices |
[]On the **Criteria** tab and depending on what you select as your Rule Type in the Configure Rule tab, you can select metrics.
[See image.](#Criteria_ZDX-Score)
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
[](/unified/triggering-alert)
-
-
-
-
-
-
-
-
| Rule Type | Metric |
| --------- | ------ |
| Application | DNS TimePage Fetch TimeServer Response TimeWeb Request AvailabilityZDX ScoreZDX Score Drops |
| Device | Bandwidth in mbpsBattery LevelCPU IdleCPU Kernel UsageCPU UsageCPU User UsageDisk Reads in bpsDisk UsageDisk Writes in bpsMemory UsageMemory UsedReceived Bits in mbpsSent Bits in mbpsWi-Fi Signal |
| Incident | Impacted DevicesEach incident type or subtype has a different minimum number of impacted devices. To learn more, see Understanding Alert Triggers.If you select multiple incidents, the criteria are already configured for you based on their minimum thresholds. |
| Network | LatencyNumber of HopsPacket CountPacket LossZDX ScoreZDX Score Drops |
| Call Quality | MOSZDX Score |
You can change the boolean logic of the metrics for the alert rule. Select **ALL** (and) for the alert to trigger if all of these thresholds are reached. Select **ANY **(or) for the alert to trigger if any of these thresholds are reached.
[See image.](#ANYALLSelection)
You can select additional metrics for the alert rule type by clicking **Add**. Depending on the metric, the criteria can use the <, >, **<=**,** **or **>=** symbols and the time (in ms) or percent (%) options to set up the criteria for your alert rule. For ZDX Score, choose between 1 and 100 for your alert rule. For ZDX Score Drops, you can choose the threshold sensitivity (e.g., high, medium, low), which is based on a baseline score.
Click **Show Preview** to show the modified expression of your selected criteria, or click **Hide Preview** to hide them.
[See image.](#preview)
[]
On the **Action** tab:
- Depending on what type you selected, the **Throttling** options are:
- **Network**, **Application**, or **Device**:
- **Alert Only if Repeated**: Enter the number of times a triggering event occurs before an alert is sent. Zscaler recommends entering 3 or more.
- **Number of Active Devices**: Enter the number of active devices.
- **Minimum Devices Impacted**: Choose by **Number** or **Percentage**. The alert triggers only if this minimum number is reached. Alerts trigger even if only one device is present in a specific group and the device meets the alert criteria.
-
**In Group**: Select the groups these throttling options apply to: **Departments**, **Cities**, **Organization**, **Regions**, or **Locations**.
These options apply to the **Number** or **Percentage** of impacted devices, and the devices are also grouped based on these options.
For example, in the following criteria:
- **Number of Active Devices**: 5 **Minimum Devices Impacted**: 20%
- **Page Fetch Time (PFT)**: >1000ms
- **In Group**: Cities (city = Cairo)
- **Alert Only if Repeated** 3 **Times in a Row**
If only one device is present in Cairo, the PFT of a device exceeds 1000ms, and this situation repeats 3 times in a row, an alert is not triggered. The alert won't trigger because there must be at least 5 active devices in Cairo.
An alert is sent when all the criteria you have set up for [triggering an alert](/unified/triggering-alert) are met.
-
**Incident**: Incident type alert rules can only configure **Action** options.
[See image.](#IncidentActionOptions)
-
**Call Quality**:
- **Number of Meetings is**: Enter the number of impacted meetings in a 15-minute rolling time duration within the range of 1 and 10.
- **Minimum Number of Active Participants is**: Enter the number of total active participants in a meeting within the range of 3 and 10.
- **Number of Impacted Active Participants is:** Enter the number of impacted active participants within the range of 1 and 20 from a selected group (**Department**, **Organization**)
[See image.](#throttling-callquality)
- For the **Action**:
- If **Muted** is enabled, no alerts are sent and you can view the status of alerts on the Alerts** **page in the Admin Portal.
- If **Muted** is disabled, select the **Alert Delivery Method** from the drop-down menu:
- **Email**: Enter the email address you want the alerts to be sent to. Click **Email Preview** to preview the email that will be sent. To learn more about the information sent, see [Understanding the Alert Email](/unified/understanding-alert-email).
- **Webhook**: Set up a webhook to provide alerts. In the drop-down menu, select from previously configured webhooks or configure a new webhook. To learn more, view [Configuring Webhooks](/unified/configuring-webhooks).
-
**Workflow Automation**: If you are subscribed to Workflow Automation, you can select Workflow Automation to send alerts to. To learn more, see What is Workflow Automation?
You cannot select Webhook and Workflow Automation together, therefore your options for Alert Delivery Methods are:
- You can select Email and Workflow Automation together, but not with Webhook.
- You can select Email and Webhook together, but not with Workflow Automation.
- You can select Email, Webhook, or Workflow Automation individually.
You can access the Workflow Automation Admin Portal to configure workflows.
[See image.](#Throttling)
[]
On the **Review** tab, review your rule configuration and then click **Submit**.
[See image.](#ZDX_ReviewRulePage)
[]
![Configure Rule](/downloads/zdx/alerts/configuring-alert-rule/zdx-add-alert-rule-1configure-rule.png)
[]
![Under Type, select ZDX Score to see Group ZDX Score By](/downloads/zdx/alerts/configuring-alert-rule/zdx-add-alert-rule-1configure-rule-2.png)
[]
![ZDX Score Value](/downloads/zdx/alerts/configuring-alert-rule/zdx-add-alert-rule-3criteria_0.png)
[]
![Review Configured Alert Rule ](/downloads/zdx/alerts/configuring-alert-rule/ZDX-AddNewAlertRule-Review-1.png)
[]
![Dynamic Alerting with ZDX Score](/downloads/zdx/alerts/configuring-alert-rule/ZDX-Alerts-IndividualAlertDetails-impacted-user-devices.png)
[]
![Select Filteres](/downloads/zdx/alerts/configuring-alert-rule/ZDX-add-alert-rule-filters.gif)
[]
![Throttling](/downloads/zdx/alerts/configuring-alert-rule/ZDX-AddNewAlertRule-Throttling-1.png)
[]
![Configuring an Alert Rule for Incident](/downloads/zdx/alerts/configuring-alert-rule/zdx-add-alert-rule-1configure-rule-incident.png)
[]
![Incident Alert Rule Action](/downloads/zdx/alerts/configuring-alert-rule/ZDX-AlertRule-Incident-Action-1.png)
[]
![Choose All or Any](/downloads/zdx/alerts/configuring-alert-rule/AnyAllSelection.png)
[]
![Show Preview displays the expression](/downloads/zdx/alerts/configuring-alert-rule/zdx-add-alert-rule-3criteria-preview.png)
[]
![Enter the throttling options for a Call Quality alert rule](/downloads/zdx/alerts/configuring-alert-rule/zdx-configure-alert-rule-throttling-cqm.png)