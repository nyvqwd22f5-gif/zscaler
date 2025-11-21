# About Alert Notifications
Source: https://help.zscaler.com/dspm/about-alert-notifications
PDF: https://help.zscaler.com/pdf/com/en/1487196.pdf

Alert rules define the criteria for generating alert notifications. The criteria could be the occurrence of specific misconfigurations or [data posture policy](/dspm/about-data-posture-policies) violations in the [cloud accounts](/dspm/about-cloud-accounts).
You can create alert rules to export alert notifications to [third-party integrations](/dspm/about-third-party-integrations) (Jira, Slack, etc.) for further investigation and remediation. These alert notifications are sent whenever the alert status changes. For example, you can add an alert rule to export notifications to Jira for high-severity policies. When these policies are triggered and their [alert status](/dspm/alert-status) changes, the notification is sent to Jira.
DSPM must be integrated with third-party tools to export alert notifications. To learn more, see [About Third-Party Integrations](/dspm/about-third-party-integrations).
The alert rules provide the following benefits and enable you to:
- Send alert notifications to third-party integrations.
- Investigate the alert and take immediate action based on the alert severity.
- Focus on critical alerts.
About the Alert Notifications Page
On the Alert Notifications page (Alerts > Alert Settings > Alert Notifications), you can do the following:
- [Add an alert rule.](/dspm/adding-alert-notification-rule)
- Search for a specific alert rule.
- View the list of alert rules. For each rule, you can see:
- **Alert Rule Name**: The name of the alert rule. Click to view additional details of the rule or edit the rule in the alert rule drawer. [See image.](#additional-details)
- **Filter Scope**: The scope ([business unit](/dspm/about-business-units), [policy](/dspm/about-data-posture-policies), tags, etc.) selected for the alert rule.
- **Integration Type**: The third-party tools to which the alert notifications are sent.
- **Updated By**: The user who updated the alert rule.
- **Last Updated**: The date and time the alert rule was last updated.
- **Created By**: The user who created the alert rule.
- **Created Date**: The date and time the alert rule was created.
-
**State**: The state (**Enabled**, **Disabled**) of the alert rule.
An alert rule is disabled with an exclamation mark indicating that it is invalid in the following scenarios:
- The third-party tools are not configured while adding the alert rule.
- The selected filters in the filter scope are deleted (e.g., policies are deleted, accounts are offboarded, or the business unit is deleted).
[See image.](#alert-notification-disabled)
Click the alert rule to see the reason why the alert rule is disabled. [See image.](#alert-rule-drawer-disabled-state)
You can enable the alert rule only after at least one filter scope is available and at least one third-party tool is configured.
- Sort the column data.
- [Modify the table and its columns.](/dspm/using-tables)
-
[Enable or disable the alert rule.](/dspm/enabling-or-disabling-alert-notification-rule)
By default, the alert rule is enabled.
- [Edit or delete an alert rule.](/dspm/editing-or-deleting-alert-notification-rule)
![About Alert Notifications](/downloads/dspm/alerts/alert-notification-rules/about-alert-notifications/dspm-about-alert-notifications_0.png)
[]![Additional details of the alert notification rule](/downloads/dspm/alerts/alert-notification-rules/about-alert-notifications/dspm-alert-rule-drawer_0.png)
[]![Viewing the Alert Notifications page](/downloads/dspm/alerts/alert-notification-rules/about-alert-notifications/dspm-invalid-alert-rule.png)
[]![Viewing the Alert Rule drawer](/downloads/dspm/alerts/alert-notification-rules/about-alert-notifications/dspm-invalid-alert-rule-drawer.png)