# Editing an Alert Rule
Source: https://help.zscaler.com/zdx/editing-alert-rule
PDF: https://help.zscaler.com/pdf/com/en/1364461.pdf

After configuring an alert rule and saving it, you can edit certain rule fields. The editable fields for a rule depend on the rule type.
The ZDX Score alert rule type is no longer recommended for use. Any pre-existing ZDX Score alert rule type has migrated to an Application alert rule type. If you have an existing ZDX Score alert rule type, you must create an alert rule with the type as Application or Network and then select ZDX Score as a criteria.
- [Example](#exampleMigration)
[]
| **Configuration Field Name** | **Example Values** | **Translated Example Values** |
| ---------------------------- | ------------------ | ----------------------------- |
| Type | ZDX Score | Application or Network |
| Criteria | ZDX Score < 33 | ZDX Score < 33 |
The throttling and other field values remain the same.
- Go to **Alerts** > **Rules**.
-
Click the **Edit** icon listed next to the details for a particular rule.
The **Edit **window opens.
- In the **Edit **window:
- [a. Configure Rule](#Configure_Rule)
- [b. Filters](#Filters)
- [c. Criteria](#Criteria)
- [d. Actions](#Action)
- [e. Review](#Review)
- Click **Save** and [activate the changes](/zdx/saving-and-activating-changes-admin-portal).
The alerts triggered have a display delay of 30 minutes.
[]
On the **Configure Rule** tab, you can edit:
- **Name**: Enter a name to identify the rule.
- **Status**: Select from **Enabled** or **Disabled**. Select **Enabled** to enable the rule.
- **Severity**: Select **High**, **Medium**, or **Low** options for severity, depending on the impact of this event on users.
-
**Type**: This was previously selected.
Application and Network include ZDX Score and ZDX Score Drops detection as a criteria for Dynamic Alerting. This feature and its procedures are available based on your subscription level. To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
If you selected **Incident** as your type, you can specify which Incident Types to configure an alert rule for. To learn more, see [Monitoring the Incidents Dashboard](/zdx/monitoring-incidents-dashboard).
[See image.](#IncidentTypeAlertRule)
- **Labels (Optional)**: Select the applicable labels for the alert rule. You can also search for the label name to select. To learn more, see [About Labels](/zdx/about-labels).
[See image.](#Edit-Configure-Rule)
[]
On the **Filters** tab, depending on your rule type, modify the parameters and filters as necessary. To learn more, see [Configuring an Alert Rule](/zdx/configuring-alert-rule).
[]
On the **Criteria** tab and depending on what you select as your Rule Type in the Configure Rule tab, modify the fields as necessary. To learn more, see [Configuring an Alert Rule](/zdx/configuring-alert-rule).
[]
On the **Actions** tab and depending on what you select as your Rule Type in the Configure Rule tab, modify the fields as necessary. To learn more, see [Configuring an Alert Rule](/zdx/configuring-alert-rule).
[]
On the **Review** tab, review your rule configuration and click **Submit**.
[]
![Editing an Alert Rule](/downloads/zdx/alerts/editing-alert-rule/ZDX-EditAlertRule-Action-2.png)
[]
![Editing an Incident Alert Rule Type](/downloads/zdx/alerts/editing-alert-rule/ZDX-EditAlertRule-Configure-Incident-1.png)