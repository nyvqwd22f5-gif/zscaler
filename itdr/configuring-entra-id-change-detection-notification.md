# Configuring an Entra ID Change Detection Notification
Source: https://help.zscaler.com/itdr/configuring-entra-id-change-detection-notification
PDF: https://help.zscaler.com/pdf/com/en/1531784.pdf

You can configure an Entra ID change detection notification to generate emails after your Entra ID tenants are successfully [scanned](/itdr/connecting-entra-id-tenant-zscaler-itdr-admin-portal)[ ]and [bad changes](/itdr/about-entra-id-change-detection-dashboard) are detected. You can customize the notification for specific scan or issue types.
Some bad changes might generate a huge volume of emails and overload email servers and inboxes. You can limit the number of emails per user in a 24-hour window.
To configure an Entra ID change detection notification:
- Go to **ITDR** > **Notifications** > **Configure**.
-
Click **Configure Notification**.
[See image.](#itdr-notification-entra-id-cd-config-button)
-
In the **Configure Notifications** window:
- Select **Enabled**.
- **Name**: Enter the name of the notification.
- **Alert Type**: Select **Entra Change Detection** from the drop-down menu.
- **Entra Domains**: Select one or more Entra ID tenants from the drop-down menu.
- Under **Entra Change Detection Notifications**, do one of the following:
- Select **Enable All** to enable notification for all the scan types that you select in the following step.
- Under **Scan Categories**, enable one or more scan or issue types (e.g., **Users without MFA**, **Excessive Global Admins**, **Privilege guest accounts**, etc.).
-
**Number of emails in a 24-hr window**: Enter a number less than or equal to 20.
If the number of emails exceeds this limit, Zscaler pauses the notifications and sends an email recommending you to review the configuration.
[See image.](#itdr-notification-entra-id-cd-email-paused)
- **Users**: Select one or more email recipients or users from the drop-down menu.
[See image.](#itdr-notification-entra-id-cd-config)
-
Click **Save**.
The Entra ID change detection notification is configured.
After the configured Entra ID tenants are successfully scanned, users receive emails with [bad change](/itdr/about-entra-id-change-detection-dashboard) details. The email provides details, such as the affected Entra ID identities, issue details remediation details, etc. You can review the bad changes and remediate the issues.
[See image.](#itdr-notification-entra-id-cd-email)
[]![Configure Notification button](/downloads/itdr/notifications/configuring-entra-id-change-detection-notification/itdr-notification-config-button.png)
[]![itdr-notification-entra-id-cd-config-1.png](/downloads/itdr/notifications/configuring-entra-id-change-detection-notification/itdr-notification-entra-id-cd-config-1.png)
[]![Entra ID change detection notification email](/downloads/itdr/notifications/configuring-entra-id-change-detection-notification/itdr-notification-entra-id-cd-email.png)
[]![Email about pausing email notification](/downloads/itdr/notifications/configuring-entra-id-change-detection-notification/itdr-notification-entra-id-cd-email-limit.png)