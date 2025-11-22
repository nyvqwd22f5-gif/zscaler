# Configuring an Active Directory Posture Notification
Source: https://help.zscaler.com/itdr/configuring-active-directory-posture-notification
PDF: https://help.zscaler.com/pdf/com/en/1531780.pdf

You can configure an Active Directory (AD) posture notification to generate emails after the AD domains are successfully [scanned](/itdr/scanning-active-directory) for vulnerabilities and the [executive summary reports](/itdr/downloading-itdr-active-directory-executive-report) are generated. Emails are sent to the configured users or recipients with AD executive summary reports for further analysis and remediation.
To configure an alert notification for AD posture:
- Go to **ITDR** > **Notifications** > **Configure**.
-
Click **Configure Notification**.
[See image.](#itdr-notification-ad-posture-config-button)
-
In the **Configure Notifications** window:
- Select **Enabled **to enable notifications.
- **Name**: Enter the name of the notification.
- **Alert Type**: Select **Active Directory Posture** from the drop-down menu.
- **Active Directory Domains**: Select one or more AD domains from the drop-down menu.
- **Users**: Select one or more email recipients or users from the drop-down menu.
[See image.](#itdr-notification-ad-posture-config-details)
-
Click **Save**.
The AD posture notification is configured.
After the configured AD domains are successfully scanned, users receive emails with the [executive summary reports](/itdr/downloading-itdr-active-directory-executive-report). You can analyze the report to identify vulnerabilities, quantify the risk score, and view remediation guidance to secure your AD domains.
[See image.](#itdr-notifications-ad-posture-email-template)
[]![Configure Notification button](/downloads/itdr/notifications/configuring-active-directory-posture-notification/itdr-notification-config-button.png)
[]![Configure AD posture notification](/downloads/itdr/notifications/configuring-active-directory-posture-notification/itdr-notification-config-details.png)
[]![AD posture notification email template](/downloads/itdr/notifications/configuring-active-directory-posture-notification/itdr-notification-config-ad-posture-email-template.png)