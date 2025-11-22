# Managing Alerts
Source: https://help.zscaler.com/dspm/managing-alerts
PDF: https://help.zscaler.com/pdf/com/en/1478181.pdf

You can resolve, snooze, unsnooze, or reset the alerts as required.
Resolving Alerts
DSPM generates [alerts](/dspm/about-alerts) for any [policy ](/dspm/about-data-posture-policies)violations or misconfigurations that are detected in your cloud resources. You might want to manually resolve alerts that are not critical or do not pose any issues.
- To resolve an alert, you must be assigned either an [administrator role](/dspm/predefined-roles-and-permissions) or a custom role with the Resolve Alerts permission. If you have Resolve Alerts permission, you are automatically assigned permissions to reset manually resolved alerts.
- When you manually resolve an alert, the alert is resolved only in the DSPM Admin Portal and the policy violation persists in the cloud service provider (CSP). The alert remains in the resolved state until you reset it.
To resolve a single alert or multiple alerts:
- Go to **Alerts **> **Alert Views** > **Alerts**.
-
Select the **All Alerts** tab, and resolve the alert on the Alerts page or drawer:
- [Alerts Page](#alerts-table)
- [Alerts Drawer](#alerts-page)
You can also access the Alerts page and Alerts drawer on the [Grouped by Policy](/dspm/viewing-alerts-grouped-policy) tab, [Grouped by Resource](/dspm/viewing-alerts-grouped-resource) tab, [Dashboard](/dspm/about-dashboard), and the [Resource Inventory](/dspm/about-resource-inventory) page.
- In the **Resolve Alert** window, enter the reason for resolving the alert.
-
Click **Resolve**.
[See image.](#policywindow)
A message appears indicating that the alerts are successfully resolved.
Snoozing Alerts
When you do not want to take any action for an alert at the moment, or you do not want to be notified for an alert, you can manually snooze the alert and specify the duration. When you snooze an alert, the alert notifications are paused and not shared with the recipients or [third-party integrations](/dspm/about-third-party-integrations) within the specified snooze period.
- To snooze an alert, you must be assigned either an [administrator role](/dspm/predefined-roles-and-permissions) or a custom role with Snooze Alerts permission. If you have Snooze Alerts permission, you are automatically assigned permissions to reset snoozed alerts.
- A snoozed alert remains snoozed for the specified duration if the issue is resolved in the CSP or if the resource or policy is deleted.
To snooze a single alert or multiple alerts:
- Go to **Alerts **> **Alert Views** > **Alerts**.
-
Select the **All Alerts** tab, and snooze the alert on the Alerts page or drawer:
- [Alerts Page](#snoozealerts-table)
- [Alerts Drawer](#snoozealerts-page)
You can also access the Alerts page and Alerts drawer on the [Grouped by Policy](/dspm/viewing-alerts-grouped-policy) tab, [Grouped by Resource](/dspm/viewing-alerts-grouped-resource) tab, [Dashboard](/dspm/about-dashboard), and the [Resource Inventory](/dspm/about-data-inventory) page.
- In the **Snooze Alert** window:
- **Reason for Snooze**: Enter the reason for snoozing the alert.
-
**Snooze End Date**: Select the duration until when you want to snooze the alert.
By default, the alert is snoozed for 1 day.
-
Click **Snooze**.
[See image.](#snooze-alert-window)
A message appears indicating that the alerts are snoozed.
Unsnoozing Alerts
If you've accidentally snoozed an alert, or you want to start receiving notifications for a snoozed alert, you can unsnooze it. When you unsnooze an alert, the status of the alert is updated based on the latest policy findings.
To unsnooze a single alert or multiple alerts:
- Go to **Alerts **> **Alert Views** > **Alerts**.
- Select the **All Alerts** tab, and unsnooze the alert on the Alerts page or drawer:
- [Alerts Page](#unsnoozealerts-table)
- [Alerts Drawer](#unsnoozealerts-page)
-
In the **Unsnooze Alert** window, click **Unsnooze**.
[See image.](#unsnoozealert-window)
A message appears indicating that the alerts are unsnoozed.
Reseting Alerts
If you've accidentally resolved an alert, you can reset the alert. When you reset an alert, the status of the alert is updated based on the latest policy findings.
To reset a single alert or multiple alerts:
- Go to **Alerts **> **Alert Views** > **Alerts**.
- Select the **All Alerts** tab, and reset the alert on the Alerts page or drawer:
- [Alerts Page](#resetalerts-table)
- [Alerts Drawer](#resetalerts-page)
-
In the **Reset Alert** window, click **Reset**.
[See image.](#resetalert)
A message appears indicating that the alerts are reset based on the latest policy findings.
-
[]Locate the required snoozed alert, click the **Actions** (![dspm-action-icon.png](/downloads/dspm/alerts/alert-ignore-filters/editing-or-deleting-ignore-filters/dspm-action-icon.png)
) icon, then select **Unsnooze**.
[See image.](#unsnooze-alert)
-
To unsnooze multiple snoozed alerts, select the corresponding checkboxes. From the **Actions** drop-down menu, select **Unsnooze**.
[See image.](#bulkunsnooze)
[]Click the **Alert ID** of the snoozed alert to view the drawer. From the **Actions** drop-down menu, select **Unsnooze**.
[See image.](#alertdetails-unsnooze)
-
[]Locate the required alert, click the **Actions** (![dspm-action-icon.png](/downloads/dspm/alerts/alert-ignore-filters/editing-or-deleting-ignore-filters/dspm-action-icon.png)
) icon, then select **Snooze**.
[See image.](#snooze-single-alert)
-
To snooze multiple alerts, select the corresponding checkboxes. From the **Actions** drop-down menu, select **Snooze**.
[See image.](#snooze-bulk-alerts)
[]Click the **Alert ID** to view the alert drawer. From the **Actions** drop-down menu, select **Snooze**.
[See image.](#snooze-alert-drawer)
-
[]Locate the required alert, click the **Actions** (![dspm-action-icon.png](/downloads/dspm/alerts/alert-ignore-filters/editing-or-deleting-ignore-filters/dspm-action-icon.png)
) icon, then select **Resolve**.
[See image.](#resolvealert)
-
To resolve multiple alerts, select the corresponding checkboxes. From the **Actions** drop-down menu, select **Resolve**.
[See image.](#multiplealerts)
[]Click the **Alert ID** to view the alert drawer. From the **Actions** drop-down menu, select **Resolve**.
[See image.](#drawer)
-
[]Locate the required resolved alert, click the **Actions** (![dspm-action-icon.png](/downloads/dspm/alerts/alert-ignore-filters/editing-or-deleting-ignore-filters/dspm-action-icon.png)
) icon, then select **Reset**.
[See image.](#reset-single-alert)
-
To reset multiple resolved alerts, select the corresponding checkboxes. From the **Actions** drop-down menu, select **Reset**.
[See image.](#reset-bulk-alerts)
[]Click the **Alert ID** of the resolved alert to view the drawer. From the **Actions** drop-down menu, select **Reset**.
[See image.](#reset-alert-drawer)
[]![Resolve alert window](/downloads/dspm/alerts/managing-alerts/managing-alerts/resolve-alerts-window.png)
[]![Resolve alert from Alerts tab](/downloads/dspm/alerts/managing-alerts/resolving-alerts/dspm-resolve-alerts_0.png)
[]![Resolve multiple alerts](/downloads/dspm/alerts/managing-alerts/resolving-alerts/dspm-bulk-resolve-alerts.png)
[]![Alert drawer](/downloads/dspm/alerts/managing-alerts/resolving-alerts/dspm-drawer-resolve.png)
[]![Reset Alert window](/downloads/dspm/alerts/managing-alerts/managing-alerts/dspm-reset-alert-window.png)
[]![Snooze Alert window](/downloads/dspm/alerts/managing-alerts/managing-alerts/dspm-snooze-alert-window.png)
[]![Snooze bulk alerts](/downloads/dspm/alerts/managing-alerts/resolving-alerts/dspm-bulk-snooze-alerts.png)
[]![Snooze a single alert](/downloads/dspm/alerts/managing-alerts/resolving-alerts/dspm-snooze-single-alert.png)
[]![Snooze an alert from the drawer](/downloads/dspm/alerts/managing-alerts/resolving-alerts/dspm-drawer-snooze.png)
[]![Reset a single alert](/downloads/dspm/alerts/managing-alerts/resolving-alerts/dspm-reset-single-alert_0.png)
[]![Reset bulk alerts](/downloads/dspm/alerts/managing-alerts/resolving-alerts/dspm-reset-bulk-alerts.png)
[]![Reset an alert](/downloads/dspm/alerts/managing-alerts/resolving-alerts/dspm-reset-alert-drawer.png)
[]![The All Alerts tab listing the alerts in the DSPM Admin Portal and annotation around Unsnooze action.](/downloads/dspm/alerts/managing-alerts/managing-alerts/dspm-all-alerts-unsnooze.png)
[]![The Alert Details window displaying the alert details and annotation around the Actions drop-down menu.](/downloads/dspm/alerts/managing-alerts/managing-alerts/dspm-alert-details-unsnooze.png)
[]![The All Alerts tab listing the alerts in the DSPM Admin Portal and annotation around the Actions drop-down menu.](/downloads/dspm/alerts/managing-alerts/managing-alerts/dspm-bulk-unsnooze-alerts.png)
[]![The Unsnooze Alert window with the selected alert details.](/downloads/dspm/alerts/managing-alerts/managing-alerts/dspm-unsnooze-alert-window.png)