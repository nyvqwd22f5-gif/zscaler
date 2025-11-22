# Enabling Email Notifications for Source Run Failures
Source: https://help.zscaler.com/uvm/enabling-email-notifications-source-run-failures
PDF: https://help.zscaler.com/pdf/com/en/1529806.pdf

Data sources ingest data into the Zscaler Security Operations (SecOps) platform on an automated schedule, based on either the individual source's Scheduling settings or the global Auto Scheduling settings. Each time a source is processed, either manually or automatically, is considered a source run. To learn more, see [Creating Data Sources](/uvm/creating-data-sources) and [Managing Data Sources](/uvm/managing-data-sources).
Source runs fail for various reasons, including API rate limits, expired or invalid credentials, schema changes, or upstream outages. To ensure visibility into these failures and reduce the need to manually check each source's status, admins can enable email notifications. These emails summarize all failed source runs across selected accounts from the past 24 hours, and are delivered at a configurable time to the inbox of the admin who enabled the notifications.
To enable email notifications:
- Click the **Profile** menu located in the top right of the navigation bar.
- Select **Profile Settings**.
-
Under **Email Notifications**, select **Enable failure alert notifications**.
The **Email Notifications** settings appear.
- In the **Email Notifications** settings:
- **Select accounts**: Select one or more accounts for which you want to receive failure alerts.
- **Frequency**: The default setting is **Daily**. This setting cannot be modified.
- **Time**: Set the local time you want the email delivered (based on your time zone).
- Click **Save**.
The emails are sent at the configured time to the email address associated with the admin who enabled the notifications.
To learn more about viewing and troubleshooting failed source runs and common potential errors, see [Tracking Source Runs](/uvm/tracking-source-runs).