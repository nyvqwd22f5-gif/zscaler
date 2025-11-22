# Managing Advanced Setting
Source: https://help.zscaler.com/deception/managing-advanced-settings
PDF: https://help.zscaler.com/pdf/com/en/1531388.pdf

Advanced Settings allow you to view license details, manage events logs and evidence files, configure a retention policy for logs, and more.
To view and manage advanced settings:
- Go to **Settings** > **Advanced Settings**.
- Select any of the following options:
- [License](#deception-adv-settings-license-page-section)
- [Manage Events & Evidence](#deception-adv-settings-maintenance-page-section)
- [Retention](#deception-adv-settings-retention-page-section)
- [Show/Hide Internal Components](#deception-show-zpa-comp-section)
[]On the License tab, you can view the details of your current Deception license:
- **Client**: The customer name the license is issued to.
- **Plan**: The active Deception subscription plan your organization is licensed to.
- **Expiration**: The expiration date of your current subscribed license.
- **Retention Policy**: The number of days after which all events and evidence files are permanently deleted.
- **Decoys**: The number of decoys configured out of the total decoys included in your subscription plan.
- **Landmine Users**: The number of users that have landmine configured out of the total landmine users included in your subscription plan.
- **Admin Portal Version**: The current version of Deception.
[See image.](#itdr-adv-set-license-details-image)
[]On the Manage Events & Evidence tab, do the following.
- [Export Event Logs](#export-event-logs-section)
- [Delete Event Logs](#export-delete-logs-section)
- [Download an Evidence File](#download-evidence-file-section)
- [Delete an Evidence File](#delete-evidence-file-section)
[]On the Retention tab, you can configure the retention period to store event logs, audit logs, etc. The retention policy is defined in the Deception license agreement. The default retention period is 365 days, and it can be reduced if required. Data is permanently deleted after the retention period expires.
The retention period of the following events or logs cannot be modified:
- Events that are [marked as safe](/deception/taking-action-from-the-dashboard) are retained for 7 days.
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
[]To download an evidence file from a Decoy Connector:
- On the **Manage Events & Evidence **tab, under **Download & Delete Evidence**, select a date and time from the **From** and **To** drop-down menus.
- Select a Decoy Connector from the drop-down menu.
-
Select the evidence type (e.g., select **pcap**).
[See image.](#download-evidence-time-frame)
-
Click **Download**.
The evidence file is downloaded to your local system.
[]To delete an evidence file from a Decoy Connector:
- On the **Manage Events & Evidence **tab, under **Download & Delete Evidence**, select a date and time from the **From** and **To** drop-down menus.
- Select a Decoy Connector from the drop-down menu.
-
Select the evidence type (e.g., select **ioc**).
[See image.](#delete-evidence-time-frame)
- Click **Delete**.
-
Click **OK** in the confirmation window.
The evidence file for the specified time frame is deleted.
The download and delete evidence operations trigger a download of up to 10,000 files or 3 GB of uncompressed evidence at a time. You might have to run these operations multiple times to clear evidence for large date ranges.
[]The Zscaler Deception Admin Portal uses the Zscaler Private Access (ZPA) service to deploy decoys in a dedicated Zscaler Deception cloud. To learn more, see [Understanding the Zscaler Deception Architecture](/deception/understanding-zscaler-deception-architecture). You can show or hide ZPA components, such as ZPA Decoy Connectors and interfaces, in the Deception Admin Portal.
To show ZPA interfaces:
-
On the **Show/Hide Internal Components **tab, enable **Show internal components**.
[See image.](#show-internal-components)
- Click **Save**.
-
Go to **Settings** > **Topology** > **Interfaces**.
The ZPA interfaces appear on the **Interfaces** page.
[See image.](#zpa-interfaces)
[]![Show or hide internal components](/downloads/deception/settings/advanced-settings/about-advanced-settings/zscaler-deception-adv-set-show-hide-int-com.png)
[]![View ZPA components](/downloads/deception/settings/advanced-settings/displaying-zscaler-private-access-components/zscaler-deception-show-zpa-interfaces-2.png)
[]![Download evidence file](/downloads/deception/settings/advanced-settings/about-advanced-settings/zscaler-deception-adv-set-download-evidence-4.png)
[]![Delete an evidence file](/downloads/deception/settings/advanced-settings/about-advanced-settings/zscaler-deception-adv-set-delete-evidence-5.png)
[]![View Deception license details](/downloads/deception/settings/advanced-settings/about-advanced-settings/zscaler-deception-adv-set-license-details-3.png)
[]![Export events logs](/downloads/deception/settings/advanced-settings/managing-events-and-evidence/zscaler-deception-adv-set-export-events-4.png)
[]![Delete event logs](/downloads/itdr/settings/advanced-settings/about-advanced-settings/itdr-advance-settings-delete-events-1.png)
[]![Configure retention period](/downloads/itdr/settings/advanced-settings/about-advanced-settings/itdr-advance-settings-config-retention-1.png)
![View Advanced Settings tabs](/downloads/deception/settings/managing-advanced-settings/deception-adv-settings-tabs-3.png)