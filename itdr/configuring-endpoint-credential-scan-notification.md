# Configuring an Endpoint Credential Scan Notification
Source: https://help.zscaler.com/itdr/configuring-endpoint-credential-scan-notification
PDF: https://help.zscaler.com/pdf/com/en/1531782.pdf

You can configure an endpoint credential scan notification to generate emails after [endpoints are scanned for exposed credentials](/itdr/configuring-endpoint-credential-exposure-scan) and the [executive summary report](/itdr/understanding-credential-exposure-summary) is generated. Emails are sent to the configured users with the executive summary report for further analysis and remediation.
To configure an alert notification for an endpoint credential scan:
- Go to **ITDR** > **Notifications** > **Configure**.
-
Click **Configure Notification**.
[See image.](#itdr-endpoit-cred-config-notification-button)
-
In the **Configure Notifications** window:
- Select **Enabled**.
- **Name**: Enter the name of the notification.
- **Alert Type**: Select **Credential Scanning** from the drop-down menu.
- **Send Notification Every**: Select the notification frequency (**Daily**, **Weekly**, **Monthly**, or **Quarterly**).
- **Trigger Time**: Select a time to trigger the notification.
- **Users**: Select one or more email recipients or users from the drop-down menu.
[See image.](#itdr-endpoint-cred-config)
-
Click **Save**.
The endpoint credential scan notification is configured.
After the endpoints are scanned, the users receive an email with the [executive summary report](/itdr/understanding-credential-exposure-summary). You can leverage this report to identify credential exposure risks, prioritize what issue to focus on first, and mitigate issues before the credentials are compromised.
[See image.](#itdr-endpoint-cred-notification-email)
[]![Configure Notification button](/downloads/itdr/notifications/configuring-endpoint-credential-scan-notification/itdr-notification-config-button.png)
[]![Configure endpoint credential scan notification](/downloads/itdr/notifications/configuring-endpoint-credential-scan-notification/itdr-notification-cred-config.png)
[]![Endpoint credential scan notification email template](/downloads/itdr/notifications/configuring-endpoint-credential-scan-notification/itdr-notification-cred-email-template.png)