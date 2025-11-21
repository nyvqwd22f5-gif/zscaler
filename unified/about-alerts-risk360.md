# About Alerts in Risk360
Source: https://help.zscaler.com/unified/about-alerts-risk360
PDF: https://help.zscaler.com/pdf/com/en/1533797.pdf

Alerting helps you meet your security compliance requirements and reduce potential financial losses by getting timely notifications when the configured criteria in the alert rule are met. This also helps take swift action towards events impacting your organization's risk exposure.
Alerts provide the following benefits and enable you to:
- Configure alert rules that help trigger alerts when an alert rule is activated.
- Configure rules for various criteria (i.e., change in risk score at the organization, factor group, and factor levels, and change in potential financial loss).
- Receive triggered notifications sent via emails and webhooks.
- Get actionable recommendations as part of alerts to tackle security events.
How Alerting Works
- When the alert rule's criteria is satisfied for the throttling period defined in the alert rule, the alert becomes an ongoing alert and starts to get displayed on the Ongoing Alerts tab.
- The users receive an alert notification in the form of an email and webhook, depending on the configured delivery method.
- The Started On field in the alert notification shows the date and time when the alert started and the Ended On field shows Ongoing because the alert is still persisting.
- Users receive a daily alert notification as long as the alert criteria are true and until the alert rule is not modified, disabled, deleted, or muted.
- Disabling an alert rule causes the alerting engine not to evaluate the alert criteria. However, the alert rule stays configured on the Alert Rules tab. You can enable the alert at a later time based on your alert requirement.
- Deleting an alert removes the alert rule from the Alert Rules page.
- Muting an ongoing alert stops sending alert notifications. However, it doesn't impact the evaluation of the alert, and you can still track the ongoing alert on the Ongoing Alerts tab.
- When the criteria of the alert are no longer satisfied, the alert stops and is listed under the Alert History tab. Subsequently, the users receive an alert notification with the Ended On field in the notification showing the date and time when the alert ended.
About the Alerts Page
The Alerts page contains the following 4 tabs to manage various alerting stages:
- [Ongoing Alerts](#ongoing)
- [Alerts History](#history)
- [Alert Rules](#rules)
- [Webhooks](#webhooks)
[]The Ongoing Alerts tab (Analytics > Risk360 > Alerts > Ongoing Alerts) shows alerts that are currently being triggered and persisting. On this page, you can do the following:
- Filter the data on the page for the last 1 day, 2, 5, 7, or 14 days.
- Filter the ongoing alerts by Severity or Rule Name.
- View a list of ongoing alerts. For each alert, you can view:
- **Severity**: The severity of the alert rule (Critical, High, Medium, or Low).
- **Rule Name**: The name of the rule.
- **Alert ID**: The unique ID assigned to the alert.
- **Criteria**: The criteria added in the rule that triggers the rule.
-
**Cause**: The reason the criteria in the rule were satisfied and the alert was triggered. Alert rules can be defined at the following 4 levels:
- Organization
- Category
- Factor group
- Factor
The cause of an alert is due to risk score or financial loss changes at one level below the defined alert criteria. For example, if the criteria is defined at the organization level, then the cause is due to changes in the 4 attack stages.
When the alert criteria is a composite rule with the criteria at different levels, the alerting engine breaks the rule into each element and derives the cause for each element separately. For example, if the rule criteria has an Org level and factor group elements, the causes would be due to changes at the 4 attack stages of the attack and the changes in the factors under the factor group.
- **Throttling**: The time frame during which the criteria in the rule persisted.
- **Delivery Method**: The method by which the alert was delivered to the recipients (i.e., Webhook or Email).
- **Muted?**: Whether the alert is currently on mute or not.
-
**Started On**: The date and time when the alert started.
Click an alert to view the following information in the drawer view.
- [Drawer](#drawer)
![Ongoing Alerts Tab](/downloads/risk360/administration-authentication/alerts/about-alerts/Risk360-Ongoing-Alerts.png)
[]The Alert History tab (Analytics > Risk360 > Alerts > Alert History) shows all the historically configured alerts. On this page, you can do the following:
- Filter the data on the page for the last 1 day, 2, 5, 7, or 14 days.
- Filter completed alerts by Severity, Rule Name, or Status.
- View a list of completed alerts. For each alert, you can view:
- **Severity**: The severity of the alert rule (Critical, High, Medium, or Low).
- **Rule Name**: The name of the rule.
- **Criteria**: The criteria added in the rule that triggers the rule.
- **Alert ID**: The unique ID assigned to the alert.
-
**Cause**: The reason the criteria in the rule were satisfied and the alert was triggered. Alert rules can be defined at the following 4 levels:
- Organization
- Category
- Factor group
- Factor
The cause of an alert is due to risk score or financial loss changes at one level below the defined alert criteria. For example, if the criteria is defined at the organization level, then the cause is due to changes in the 4 attack stages.
When the alert criteria is a composite rule with the criteria at different levels, the alerting engine breaks the rule into each element and derives the cause for each element separately. For example, if the rule criteria has an Org level and factor group elements, the causes would be due to changes at the 4 attack stages of the attack and the changes in the factors under the factor group.
- **Throttling**: The time frame during which the criteria in the rule persisted.
- **Delivery Method**: The method by which the alert was delivered to the recipients (i.e., Webhook or Email).
- **Started On**: The date and time when the alert started.
-
**Ended On**: The date and time when the alert ended.
Click an alert to view the following information in the drawer view.
- [Drawer](#history-drawer)
![Alert History Tab](/downloads/risk360/administration-authentication/alerts/about-alerts/Risk360-Alerts-History%20(2).png)
[]The Alert Rules tab (Analytics > Risk360 > Alerts > Alert Rules) shows all the configured alerts. On this page, you can do the following:
- Filter the alerts by Severity or Rule Name.
- [Add an alert rule](/unified/configuring-alert-rule-risk360).
- View a list of alerts. For each alert, you can view:
- **Rule Name**: The name of the rule.
- **Severity**: The severity of the alert rule (Critical, High, Medium, or Low).
- **Criteria**: The criteria added in the rule that triggers the rule alert.
- **Throttling**: The time frame during which the criteria in the rule were satisfied.
- **Delivery Method**: The method by which the alert was delivered to the recipients (i.e., Webhook or Email).
- **Status**: The status of the alert, whether enabled or disabled.
- Edit a rule.
- Mute or unmute notifications from an alert rule. This ensures the rule is enabled, but no notification is initiated when the alert is triggered.
- Delete an alert rule or clone the rule to configure a new alert rule.
![Alert Rules Tab](/downloads/risk360/administration-authentication/alerts/about-alerts/Risk360-Alerts-Rules%20(2).png)
[]The Webhook tab (Analytics > Risk360 > Alerts > Webhook) shows all the configured webhook integrations. You can use integrations into an alert rule from the third-party provider to receive alerts. On this page, you can do the following:
- Filter the ongoing alerts by Name, Authentication Type, or Status.
- [Add webhook](/unified/configuring-alert-webhooks-risk360).
- View a list of configured integrations. For each integration, you can view:
- **Name**: The name of the integration.
- **URL**: The URL of the integration.
- **Authentication Type**: The authentication type configured for the integration (Basic or Token).
- **Authentication Status**: This shows the integration authentication status (Active, Error, or In Progress). Fix the configuration if the field displays an error.
- **Alert Status**: The status of the alert, whether enabled or disabled.
- Edit an integration.
- Delete an integration.
![Webhooks Tab](/downloads/risk360/administration-authentication/alerts/about-alerts/Risk360-Alerts-Webhooks_0%20(1).png)
[]The drawer consists of the following two tabs:
Details
The Details tab shows the following information about the alert:
- **Alert ID**: The unique ID assigned to the alert.
- **Criteria**: The criteria added in the rule that triggers the alert.
- **Throttling**: The time frame during which the criteria in the rule persisted.
- **Alert Delivery Method**: The method by which the alert was delivered to the recipients (i.e., Webhook or Email).
-
**Cause**: The change in the risk score or potential loss at different levels (i.e., organization, category, factor group, and factor) in the last 24 hours. The red, green, and gray colors indicate an increase, decrease, and no change in the risk score or potential financial loss, respectively.
[See image.](#ongoing-drawer-details)
Alert Cause History
The Alert Cause History tab shows the history of whenever the alert is triggered for the change in the risk score or potential loss at different levels (i.e., organization, category, factor group, and factor). The red, green, and gray colors indicate an increase, decrease, and no change in the risk score or potential financial loss, respectively. Click the dropdowns to view the change cause for that date.
[See image.](#ongoing-drawer-cause-history)
[]The drawer shows the following information about the alert:
- **Alert ID**: The unique ID assigned to the alert.
- **Criteria**: The criteria added in the rule that triggers the alert.
- **Throttling**: The time frame during which the criteria in the rule persisted.
- **Alert Delivery Method**: The method by which the alert was delivered to the recipients (i.e., Webhook or Email).
-
**Cause**: The change in the risk score or potential loss at different levels (i.e., organization, category, factor group, and factor) in the last 24 hours. The red, green, and gray colors indicate an increase, decrease, and no change in the risk score or potential financial loss, respectively.
[See image.](#history-details-drawers)
[]![Details Drawer](/downloads/risk360/administration-authentication/alerts/about-alerts/Risk360-Ongoing-Alerts-Drawer-Details.png)
[]![Cause History](/downloads/risk360/administration-authentication/alerts/about-alerts/Risk360-Ongoing-Alerts-Drawer-Cause-History.png)
[]![Alerts History Drawer](/downloads/risk360/administration-authentication/alerts/about-alerts/Risk360-Alerts-History-Drawer%20(2).png)