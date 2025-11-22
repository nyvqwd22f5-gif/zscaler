# About Audit, Error, and Debug Logs
Source: https://help.zscaler.com/deception/about-audit-error-debug-logs
PDF: https://help.zscaler.com/pdf/com/en/1531380.pdf

You can view and manage audit, error, and debug logs.
The Logs page provides the following benefits and enables you to:
- View or export audit logs in the Zscaler Deception Admin Portal.
- View and analyze system-generated error logs that require manual intervention.
- Download debug logs to share with Zscaler Support to perform root cause analysis.
About the Logs Page
On the Logs page (Settings > Logs), you can see the following tabs:
- [Audit Logs](#deception-log-audit)
- [Messages](#deception-log-error-message)
- [Debug Logs](#deception-log-debug)
![About the Logs page](/downloads/deception/settings/audit-logs-messages/about-logs-and-system-messages/zscaler-deception-logs-page-2.png)
[]Audit logs are chronological records of user activities that occur in the Deception Admin Portal. These logs record activities such as login attempts, decoy creation, modification or deployment, user profile updates, etc. You can use the audit logs to trace back to the source of a change. Audit logs allow you to evaluate the events and check for any anomalies in user behavior. You can export audit logs as a CSV file.
The audit logs contain the following information:
- **Timestamp**: The time when the user activity occurred.
- **Username**: The ID of the user who performed the activity.
- **Module**: The Deception module (Login, Retention Policy, etc.) on which the activity occurred.
- **Description**: The description of the activity.
[See image.](#about-audit-logs)
Exporting Audit Logs
To export audit logs:
-
Go to **Settings** > **Logs** > **Audit Logs**.
The audit logs appear.
-
Click **Export Logs**.
[See image.](#deception-exp-audit-logs-img)
A CSV file with audit logs is downloaded to your system.
[]Error logs include error messages for failed events such as invalid user credentials, failed authentication, landmine agent version mismatch, etc. Each message provides the following information:
- **Timestamp**: The time when the error occurred.
- **Category**: The component (Containment, Enrichment, etc.) which caused the error.
- **Module**: The Deception entity (ZPA, Email, etc.) on which the error occurred.
- **Message**: A brief explanation of the error.
- **Metadata**: The metadata that provides context about the error.
- **Error**: Hover over the information icon to view the error message.
- **Count:** The number of times the error occurred.
- **Actions**: Click the **Delete** icon to delete the message, or click the checkmark to mark the message as read.
[See image.](#about-system-messages)
Click the **Actions** menu and select **Delete all** to delete all the messages, or select **Mark all as read** to mark all the messages as read.
[See image.](#deception-error-action-menu)
[]Debug logs provide information on the errors that occurred in the Deception Admin Portal. The debug logs help Zscaler Support to identify the root cause of a problem and provide a resolution. You can download debug logs for the last 2 hours, 24 hours, or 7 days.
Downloading Debug Logs
- Go to **Settings** > **Logs** >** Debug Logs**.
- Select a time range (**Last 2 hours**, **Last 24 hours**, or **Last 7 days**).
- Click **Request** to create an archive file with the logs for the requested time range.
-
When the debug logs are ready to download after a couple of minutes, click the **here** link.
[See image.](#deception-request-debug-logs)
The **Debug Logs** window appears.
-
Click the **Download** icon to download the file to your system.
[See image.](#download-debug-logs)
Click the **Delete** icon to delete the file containing the debug logs from the Deception Admin Portal.
- Click **Close**.
[]![View audit logs](/downloads/deception/settings/audit-logs-messages/about-logs-and-system-messages/zscaler-deception-logs-audit-3.png)
[]![View error logs](/downloads/deception/settings/logs/about-audit-error-debug-logs/zscaler-deception-logs-error-message-4.png)
[]![Export audit logs](/downloads/deception/settings/audit-logs-messages/about-audit-logs-error-messages-debug-logs/zscaler-deception-export-audit-log-csv-2.png)
[]![View the Actions menu](/downloads/deception/settings/logs/about-audit-error-debug-logs/zscaler-deception-error-logs-action-menu-3.png)
[]![Click the here link](/downloads/deception/settings/audit-logs-messages/about-audit-error-debug-logs/zscaler-deception-debug-logs-here-link-2.png)
[]![Download debug logs](/downloads/deception/settings/audit-logs-messages/about-audit-error-debug-logs/zscaler-deception-debug-logs-dwnld.png)