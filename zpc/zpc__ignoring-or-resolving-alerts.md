# Ignoring or Resolving Alerts
Source: https://help.zscaler.com/zpc/ignoring-or-resolving-alerts
PDF: https://help.zscaler.com/pdf/com/en/1408271.pdf

ZPC triggers alerts for any security policy violations or misconfigurations that are detected in your cloud resources. Sometimes, you might want to ignore or resolve a few alerts that are not critical and instead focus on high-priority alerts. You can also configure alert filters to ignore specific alerts that are not critical. To learn more, see [Adding Ignore Filters](/zpc/adding-ignore-filters).
Ignoring an Alert
To ignore a single alert or multiple alerts:
- On the **Alerts** page, click the **Cloud Alerts** or **IaC Alerts** tab, as required.
- Click the **All Alerts List** tab.
- You can choose to ignore alerts from various locations in the Zscaler Posture Control (ZPC) Admin Portal:
- [Alerts page](#ignore-pageoptions)
- [Alerts drawer](#ignore-draweroption)
- In the** Ignore Alert** window, enter the reason and select the duration for ignoring the alert.
[See image.](#ignorealertwindow)
- Click **Ignore**.
The alert is ignored, but whenever ZPC detects a security policy violation, it triggers the alert. However, the alert notification is not sent to third-party tools.
Resolving Alerts
To resolve a single alert or multiple alerts:
- On the **Alerts** page, click the **Cloud Alerts** or **IaC Alerts** tab, as required.
- Click the **All Alerts List** tab.
- You can choose to resolve alerts from various locations in the ZPC Admin Portal:
- [Alerts page](#resolve-page)
- [Alerts drawer](#resolveactions)
- In the** Resolve Alert** window, enter the reason for resolving the alert.
[See image.](#resolvealertwindow)
- Click **Resolve**.
The alerts are resolved and the alert status changes to **Resolved** on the **Alerts** page.
- []Click the **Actions** icon  (![Edit Icon](/downloads/zpc/alerts/editing-or-deleting-ignore-filters/action-icon.png)
), then select **Ignore**.
[See image.](#ignore-page)
- Select the checkbox for an alert. You can also select and ignore multiple alerts. From the **Actions** menu that appears, select **Ignore**.
[See image.](#ignore-action)
- []Click the **Alert ID** to view the alert drawer. From the **Actions** drop-down menu, select **Ignore**.
[See image.](#alert-drawer)
[![Ignore a single alert](/downloads/zpc/alerts/managing-alerts/ignoring-or-resolving-alerts/zpc-ignorealert-page.png)
]
[![Select and ignore a single or multiple alerts](/downloads/zpc/alerts/managing-alerts/ignoring-or-resolving-alerts/zpc-ignorealert-action.png)
]
[![Alert drawer](/downloads/zpc/alerts/managing-alerts/ignoring-or-resolving-alerts/zpc-ignorealertdrawer.png)
]
[![Enter the details for ignoring the alert](/downloads/zpc/alerts/managing-alerts/ignoring-or-resolving-alerts/zpc-ignore-alertwindow.png)
]
- []Click the **Actions** icon  (![Edit Icon](/downloads/zpc/alerts/editing-or-deleting-ignore-filters/action-icon.png)
), then select **Resolve**.
[See image.](#resolve-onealert)
- Select the checkbox for an alert. You can also select and resolve multiple alerts. From the **Actions** menu that appears, select **Resolve**.
[See image.](#resovemorealerts)
- []Click the **Alert ID** to view the alert drawer. From the **Actions** drop-down menu, select **Resolve**.
[See image.](#resolvealertdrawer)
[![Resolve a single alert](/downloads/zpc/alerts/managing-alerts/ignoring-or-resolving-alerts/zpc-resolvealert-page.png)
]
[![Resolve one or more alerts](/downloads/zpc/alerts/managing-alerts/ignoring-or-resolving-alerts/zpc-resolvealertaction.png)
]
[![Resolve alert from drawer](/downloads/zpc/alerts/managing-alerts/ignoring-or-resolving-alerts/zpc-resolvealerts-drawer.png)
]
[![View the Resolve Alert window](/downloads/zpc/alerts/managing-alerts/ignoring-or-resolving-alerts/zpc-resolvealert-window.png)
]