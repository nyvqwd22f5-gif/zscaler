# Configuring an Entra ID Posture Notification
Source: https://help.zscaler.com/itdr/configuring-entra-id-posture-notification
PDF: https://help.zscaler.com/pdf/com/en/1531783.pdf

You can configure an Entra ID posture notification to generate emails after Entra ID tenants are [scanned](/itdr/connecting-entra-id-tenant-zscaler-itdr-admin-portal) for vulnerabilities and [executive summary reports](/itdr/downloading-zscaler-itdr-microsoft-entra-id-assessment-posture-report) are generated. Emails are sent to the configured users with the Entra ID executive summary reports for further analysis and remediation.
To configure an alert notification for Entra ID posture:
- Go to **ITDR** > **Notifications** > **Configure**.
-
Click **Configure Notification**.
[See image.](#itdr-entra-id-posture-_config-noti-button)
-
In the **Configure Notifications** window:
- Select **Enabled**.
- **Name**: Enter the name of the notification.
- **Alert Type**: Select **Entra Posture** from the drop-down menu.
- **Entra Domains**: Select one or more Entra ID tenants from the drop-down menu.
- **Users**: Select one or more email recipients or users from the drop-down menu.
[See image.](#itdr-notification-entra-id-posture-config)
-
Click **Save**.
The Entra ID posture notification is configured.
After the configured Entra ID tenants are successfully scanned, users receive an email with the attached [executive summary report](/itdr/downloading-zscaler-itdr-microsoft-entra-id-assessment-posture-report). You can analyze the report to identify vulnerabilities, quantify risk scores, and view remediation guidance to secure your Entra ID tenant.
[See image.](#itdr-notification-entra-id-posture-email)
[]![Configure Notification button](/downloads/itdr/notifications/configuring-entra-id-posture-notification/itdr-notification-config-button.png)
[]![Configure Entra ID posture scan](/downloads/itdr/notifications/configuring-entra-id-posture-notification/itdr-notification-entra-id-config-details.png)
[]![Entra ID posture notification email ](/downloads/itdr/notifications/configuring-entra-id-posture-notification/itdr-notification-entra-id-config-email.png)