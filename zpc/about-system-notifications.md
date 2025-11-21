# About System Notifications
Source: https://help.zscaler.com/zpc/about-system-notifications
PDF: https://help.zscaler.com/pdf/com/en/1420031.pdf

Notifications provide information about any security issues or events within your cloud infrastructure. For example, a notification is triggered when a security vulnerability is detected or an anomalous activity has occurred in your cloud accounts.
Notifications also provide information about security events that occur in your cloud workloads. ZPC proactively detects any activity that could be a security risk and triggers notifications. These notifications are sent by email to recipients for further investigation and remediation.
Notifications provide the following benefits and enable you to:
- Check if the ZPC service has lost connectivity with the public cloud infrastructure.
- Check if the reports are not delivered.
- Check if the alert rules are created or deleted.
- Check if the alerts are not sent to third-party tools.
- Check if vulnerability scanning is enabled or disabled.
- Check if the vulnerability scans fail and the reason for failure.
- Check if the IaC scans fail and the reason for failure.
- A red dot on the notification icon (![Red dot icon for new notifications](/downloads/zpc/getting-started/admin-portal/about-notifications/zpc-red-dot-icon.png)
) indicates that there are new notifications.
- If you delete any cloud account, then ZPC automatically deletes the notifications.
- ZPC automatically deletes resolved notifications after 30 days.
- IaC notifications are retained only for 7 days and then the logs are not displayed in the ZPC Admin Portal.
About the Notification Center Page
On the Notification Center page (**Notification **icon ![Notification icon](/downloads/zpc/administration/notifications/notification-icon.png)
), you can do the following:
- View the list of notifications. For each notification, you can see:
- **Last Detected**: The date and timestamp for when the issue was last detected.
- **ID**: The ID of the notification. Click to view the details of the configuration errors, permission errors, and resolution. [See image.](#errors)
- **Module**: The module (Data Collection or Vulnerability Management) for which the notification is detected.
- **Summary**: The description of the notification.
- **Severity**: The severity of the notification (Critical, High, Medium, and Low).
- **Status**: The status of the notification (Open, Resolved).
- **First Detected**: The date and timestamp for when the issue was first detected.
- Use the filters to view specific data in the table.
- Search for a specific notification.
- Sort the column data.
- [Modify the table and its columns](/zpc/using-tables).
- Select and apply a saved filter to view specific notifications.
- Hide the filters.
![View the Notification Center page](/downloads/zpc/getting-started/admin-portal/about-system-notifications/zpc-notifications-page1.png)
[![View configuration error details](/downloads/zpc/getting-started/admin-portal/about-system-notifications/zpc-notification-dataerrors.png)
]