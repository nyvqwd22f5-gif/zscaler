# Configuring an Active Directory Change Detection Notification
Source: https://help.zscaler.com/itdr/configuring-active-directory-change-detection-notification
PDF: https://help.zscaler.com/pdf/com/en/1531781.pdf

You can configure an Active Directory (AD) change detection notification to generate emails after AD domains are [successfully scanned](/itdr/scanning-active-directory) and [bad changes](/itdr/about-change-detection-dashboard) are detected. You can customize the notification for specific scan or issue types.
The AD change detection scan runs every 15 minutes. Some bad changes might generate a huge volume of emails and overload email servers and inboxes. To avoid this, you can limit the number of emails per user in a 24-hour window.
To configure an AD change detection notification:
- Go to **ITDR** > **Notifications** > **Configure**.
-
Click **Configure Notification**.
[See image.](#itdr-notification-ad-cd-config-button)
- In the **Configure Notifications** window:
- Select **Enabled**.
- **Name**: Enter the name of the notification.
- **Alert Type**: Select **Active Directory Change Detection** from the drop-down menu.
- **Active Directory Domains**: Select one or more AD domains from the drop-down menu.
- Under **Active Directory Change Detection Notifications**, do one of the following:
- Select **Enable All** to enable notification for all the scan types that you select in the following step.
- Under **Scan Categories**, enable one or more scan types (e.g., **Vulnerable to AS-REP roasting**, **Privileged Accounts**, **Kerberoastable Accounts**, etc.).
-
**Number of emails in a 24-hr window**: Enter a number less than or equal to 20.
If the number of emails exceeds this limit, Zscaler pauses the notifications and sends an email recommending you to review the configuration.
[See image.](#itdr-notification-ad-cd-email-limit)
-
**Users**: Select one or more email recipients or users from the drop-down menu.
[See image.](#itdr-notification-ad-cd-config)
-
Click **Save**.
The Active Directory (AD) change detection notification is configured.
After the configured AD domains are [successfully scanned](/itdr/scanning-active-directory)[, ]users receive emails with [bad change](/itdr/about-change-detection-dashboard) details. The email provides details such as the affected AD domain and identities, issue details, remediation details, etc. You can review the bad changes and remediate the issues.
[See image.](#itdr-notification-ad-cd-email-template)
[]![Configure Notification button](/downloads/itdr/notifications/configuring-active-directory-change-detection-notification/itdr-notification-config-button.png)
[]![Notification on email limit](/downloads/itdr/notifications/configuring-active-directory-change-detection-notification/itdr-notification-config-ad-change-detection-limit-exceed-1.png)
[]![Configure AD change detection notification](/downloads/itdr/notifications/configuring-active-directory-change-detection-notification/itdr-notification-config-ad-change-detection-details.png)
[]![AD change detection notification email](/downloads/itdr/notifications/configuring-active-directory-change-detection-notification/itdr-notification-config-ad-change-detection-email-template.png)