# Managing Advanced Setting
Source: https://help.zscaler.com/itdr/managing-advanced-settings
PDF: https://help.zscaler.com/pdf/com/en/1531708.pdf

Advanced Settings allow you to view license details, manage events logs, configure a retention policy for logs, and more.
To view and manage advanced settings:
- Go to **Settings** > **Advanced Settings**.
- Select any of the following options:
- [License](#itdr-adv-settings-license-page-section)
- [Manage Events & Evidence](#itdr-adv-settings-maintenance-page-section)
- [Retention](#itdr-adv-settings-retention-page-section)
[]On the License tab, you can view the details of your current ITDR license:
- **Client**: The customer name the license is issued to.
- **Plan**: The active ITDR subscription plan your organization is licensed to.
- **Expiration**: The expiration date of your current subscribed license.
- **Retention Policy**: The number of days after which all events and evidence files are permanently deleted.
- **Decoys**: The number of decoys configured out of the total decoys included in your subscription plan.
- **Landmine Users**: The number of users that have landmine configured out of the total landmine users included in your subscription plan.
- **Admin Portal Version**: The current version of ITDR.
[See image.](#itdr-adv-set-license-details-image)
[]On the Manage Events & Evidence tab, do the following.
- [Export Event Logs](#export-event-logs-section)
- [Delete Event Logs](#export-delete-logs-section)
[]On the Retention tab, you can configure the retention period to store event logs, audit logs, etc. The retention policy is defined in the ITDR license agreement. The default retention period is 365 days, and it can be reduced if required. Data is permanently deleted after the retention period expires.
The retention period of the following events or logs cannot be modified:
- Events that are marked as safe are retained for 7 days.
- Okta system logs for threat detection are retained for 14 days.
To configure the retention period:
-
On the **Retention **tab, enter the retention period in days.
[See image.](#itdr-adv-setting-retention-image)
- Click **Save**.
[]To export event logs:
-
On the **Manage Events & Evidence **tab, under **Export Events (Serializable JSON)**, select a date and time from the **From** and **To** drop-down menus.
[See image.](#itdr-export-events-json-time-frame)
-
Click **Export**.
The event logs are downloaded to your system in the JSON format.
[]To delete event logs that are marked as safe, or delete all event logs for a specified time frame.:
- On the **Manage Events & Evidence**, under **Delete Events**, select a date and time from the **From** and **To** drop-down menus.
-
Select an option:
- **All Events**: All the events for the specified time frame are deleted.
- **Marked as safe only**: Only events that are marked as safe are deleted.
[See image.](#itdr-delete-events-time-frame)
-
Click **Delete**.
The event logs for the specified time frame are deleted.
[]![Image]()
![View the license tab](/downloads/itdr/settings/about-advanced-settings/itdr-adv-settings-license-4.png)
[]![Export events logs](/downloads/deception/settings/advanced-settings/managing-events-and-evidence/zscaler-deception-adv-set-export-events-4.png)
[]![Delete event logs](/downloads/itdr/settings/advanced-settings/about-advanced-settings/itdr-advance-settings-delete-events-1.png)
[]![Configure retention period](/downloads/itdr/settings/advanced-settings/about-advanced-settings/itdr-advance-settings-config-retention-1.png)
![View Advance Settings tabs](/downloads/itdr/settings/advanced-settings/about-advanced-settings/itdr-advance-settings-all-tabs-2.png)