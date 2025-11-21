# Enabling or Disabling an Alert Rule
Source: https://help.zscaler.com/dspm/enabling-or-disabling-alert-rule
PDF: https://help.zscaler.com/pdf/com/en/1477781.pdf

You can enable or disable the [alert rule](/dspm/about-alert-notification-rules) you've added, as required. By default, the alert rule is enabled.
When you disable an alert rule, DSPM stops sending alert notifications to the configured [third-party tools](/dspm/about-third-party-integrations).
An alert rule is disabled with an exclamation mark on the alert name in the following scenarios:
- The third-party tools are not configured while adding the alert rule.
- The selected filters in the filter scope are deleted (e.g., policies are deleted, accounts are offboarded, or the business unit is deleted).
[See image.](#alert-notifications)
You can enable the alert rule only after at least one filter scope is available and at least one third-party tool is configured.
To enable or disable the alert rule:
- Go to **Alerts **> **Alert Settings** >** Alert Notification**.
-
Click the toggle under the **State** column to enable or disable the alert rule.
[See image.](#enable-button)
-
A confirmation message appears indicating that the alert rule is going to be enabled or disabled. Click **Enable** or **Disable** depending on the action.
[See image.](#confirmationwindow)
[]![Enable or Disable an alert notification rule](/downloads/dspm/alerts/alert-notification-rules/enabling-or-disabling-alert-rule/dspm-enable-disable-toggle.png)
[]![Disable an alert notification](/downloads/dspm/alerts/alert-notification-rules/enabling-or-disabling-alert-rule/dspm-disable-alert-rule.png)
[]![Viewing the Alert Notifications page](/downloads/dspm/alerts/alert-notification-rules/enabling-or-disabling-alert-rule/dspm-invalid-alert-rule.png)