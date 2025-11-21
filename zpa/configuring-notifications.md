# Configuring Notifications
Source: https://help.zscaler.com/zpa/configuring-notifications
PDF: https://help.zscaler.com/pdf/com/en/1485441.pdf

Within the ZPA Admin Portal, you can create notifications.
Adding a Notification
[]To add a new notification:
- Go to **Configuration & Control** > **Notification Management **> **Notifications**.
-
Click **Add**.
Notifications that are managed by Zscaler are read only and cannot be configured, edited, or deleted.
The **Add Notification **page appears.
- On the **Add Notification** page:
- [1. General Information](#generalinformation)
- [2. Events](#events)
- [3. Action](#Action)
- [4. Review](#review)
[]On the **General Information **tab, provide the following information:
- **Name**: The name of the notification.
- **Status**: Indicates the status of the notification (i.e., **Enabled** or **Disabled**). By default, the status is set to **Enabled**.
- [Select a Component](#components)
- [Select a Category](#categories)
- [Select a Priority](#priorities)
[See image.](#addNotificationWindow)
[]On the **Events** tab:
- Click **Add Events**.
- Select the desired event.
For events that require text input, enter an integer value within the supported range. To learn more, see the [events table](#eventsTable).
[See image.](#image1)
- Click **Next**.
The following table provides a list of events, as well as the category and component the event belongs to:
[]
[](/zpa/about-backup-and-restore)[](/zpa/restoring-policies-and-configurations-backup)[](/zpa/about-backup-and-restore)[](/zpa/restoring-policies-and-configurations-backup)[](/zpa/monitoring-connector-performance#cpu)[](/zpa/monitoring-connector-performance#diskspace)[](/zpa/about-enrollment-ca-certificates)[](/zpa/monitoring-connector-performance#filedscrpt)[](/zpa/about-backup-and-restore)[](/zpa/restoring-policies-and-configurations-backup)[](/zpa/about-backup-and-restore)[](/zpa/restoring-policies-and-configurations-backup)[](/zpa/monitoring-connector-performance#memory)
| Event | Category | Component | Description |
| ----- | -------- | --------- | ----------- |
| Application Exceeded Count Limit | Usage Metrics | App Connectors | An event indicating when the component's application count has exceeded the limit. The Application Exceeded Count Limit value must be an integer between 4500 and 6000. The default value is set to 4500. |
| Backup Completed | Backup Configuration | Backup and Restore | An event indicating when the backup is completed. To learn more, see About Backup and Restore and Restoring Policies and Configurations from a Backup. |
| Backup Failed | Backup Configuration | Backup and Restore | An event indicating when the backup has failed. To learn more, see About Backup and Restore and Restoring Policies and Configurations from a Backup. |
| Bandwidth Utilization Exceeded Limit | Usage Metrics | App Connectors, Private Service Edges | An event indicating when the component's bandwidth utilization has exceeded the limit. The Bandwidth Utilization Exceeded Limit value must be an integer greater than or equal to 250 Mbps. The default value is set to 250. |
| Control Connection Disconnected | Connectivity and Upgrade | App Connectors, Private Cloud Controllers, Private Service Edges | An event indicating when the control connection for an App Connector, Private Cloud Controller, or ZPA Private Service Edge disconnects. |
| CPU Exceeded Limit | Usage Metrics | App Connectors, Private Service Edges | An event indicating when the component's CPU utilization has exceeded the limit. The CPU Exceeded Limit value must be an integer between 75% and 99%. The default value is set to 75. To learn more, see Monitoring App Connector Performance. |
| CPU Starvation | System Resource | App Connectors, Private Cloud Controllers, Private Service Edges | An event indicating when the component's CPU is missing resources needed for operations. |
| Disk Space Exceeded Limit | Usage Metrics | App Connectors, Private Service Edges | An event indicating when the component's available disk space is less than the indicated threshold. The Disk Space Exceeded Limit value must be an integer between 0 and 2048 MB. The default value is set to 2048. To learn more, see Monitoring App Connector Performance. |
| Enrollment Certificate Expired | Enrollment | App Connectors, Private Service Edges | An event indicating when an enrollment certificate has expired for the selected component. To learn more, see About Enrollment (CA) Certificates. |
| Enrollment Completed | Enrollment | App Connectors, Private Cloud Controllers, Private Service Edges, Cloud Connectors | An event indicating when the enrollment of the component is completed. |
| Enrollment Failed | Enrollment | App Connectors, Private Service Edges | An event indicating when the enrollment for the selected component has failed. |
| File Descriptors Exhausted | Usage Metrics | App Connectors, Private Cloud Controllers, Private Service Edges | An event indicating when the component's file descriptors are exhausted. The File Descriptors Exhausted value must be an integer between 75% and 99%. The default value is set to 75. To learn more, see Monitoring App Connector Performance. |
| Invalid System Listen IP Configuration | System Resource | Private Cloud Controllers, Private Service Edges | An event indicating when the listen IP address configuration for a ZPA Private Service Edge or Private Cloud Controller is invalid. |
| Last Component Disconnected | Connectivity and Upgrade | App Connectors, Private Cloud Controllers, Private Service Edges | An event indicating that all App Connectors in an App Connector group, all Private Cloud Controllers in a Private Cloud Controller group, or all ZPA Private Service Edges in a ZPA Private Service Edge group are disconnected. |
| Outdated Component Manager Version | Connectivity and Upgrade | App Connectors, Private Cloud Controllers, Private Service Edges | An event indicating the Manager version is outdated for the selected components. |
| Provisioning Key Utilization Exceeded Limit | Enrollment | App Connectors, Private Cloud Controllers, Private Service Edges, Cloud Connectors | An event indicating when the provisioning key has exceeded the limit for the selected components. |
| Restore Completed | Backup Configuration | Backup and Restore | An event indicating when the restore is completed. To learn more, see About Backup and Restore and Restoring Policies and Configurations from a Backup. |
| Restore Failed | Backup Configuration | Backup and Restore | An event indicating when the restore has failed. To learn more, see About Backup and Restore and Restoring Policies and Configurations from a Backup. |
| SCIM Users Successfully Deleted | Enrollment | Zscaler Client Connector | An event indicating when SCIM users are deleted successfully. |
| Source Port Consumption Exhausted | Usage Metrics | App Connectors, Private Service Edges | An event indicating when the component's source TCP or UDP ports are exhausted. The exhausted values must be an integer between 75% and 99%. The default value is set to 75. |
| System Memory Exceeded Limit | Usage Metrics | App Connectors, Private Service Edges | An event indicating when the component's system memory has exceeded the limit. The System Memory Exceeded Limit value must be an integer between 75% and 99%. The default value is set to 75. To learn more, see Monitoring App Connector Performance. |
| Upgrade Complete | Connectivity and Upgrade | App Connectors, Private Cloud Controllers, Private Service Edges | An event indicating when an upgrade is complete for the selected components. |
| Upgrade Failed | Connectivity and Upgrade | App Connectors, Private Cloud Controllers, Private Service Edges | An event indicating when an upgrade fails for the selected components. |
[]On the **Action **tab:
- [Configure the Throttling](#configureThrottling)
- [Configure the Recipients](#configureRecipients)
- []Review your configured settings.
- Click **Save**.
[]Select a component from the drop-down menu. The following is a list of available components:
- **App Connectors**: To learn more, see [About App Connectors](/zpa/about-connectors).
- **Backup and Restore**: To learn more, see [About Backup and Restore](/zpa/about-backup-and-restore).
- **Private Cloud Controller**: To learn more, see [About Private Cloud Controllers](/zpa/about-private-cloud-controllers).
- **Private Service Edges**: To learn more, see [About ZPA Private Service Edges](/zpa/about-zpa-private-service-edges).
- **Cloud Connectors**: To learn more, see [About Cloud Connectors](/zpa/about-cloud-connectors).
- **Zscaler Client Connector**: To learn more, see [What Is Zscaler Client Connector?](/zscaler-client-connector/what-is-zscaler-client-connector)
If you are within a [Microtenant](/zpa/about-microtenants), you can only create notifications for App Connectors, ZPA Private Service Edges, or Private Cloud Controllers.
Click the **Delete **icon (![Delete icon in the ZPA Admin Portal](/downloads/zpa-add-notification-delete-icon.png)
) to remove a selected component. After a component is selected, a drop-down menu appears for the **Categories**, **Priorities**, and selection of the components.
After a component is selected, select the desired App Connectors, Cloud Connectors, Private Cloud Controllers, or Private Service Edges from the list of available components:
- **App Connectors**: Select an App Connector from the drop-down menu. You can search for a specific App Connector, select an individual App Connector, click** Select All Displayed** to select all App Connectors displayed in the drop-down menu, click **Clear All** to remove all selections, or click the **Delete **icon next to the selected App Connector to remove it. All App Connectors are selected by default.
- **Cloud Connectors**: Select a Cloud Connector from the drop-down menu. You can search for a specific Cloud Connector, select an individual Cloud Connector, click **Select All Displayed** to select all Cloud Connectors displayed in the drop-down menu, click **Clear All** to remove all selections, or click the **Delete **icon next to the selected Cloud Connector to remove it. All Cloud Connectors are selected by default.
- **Private Cloud Controllers**: Select a Private Cloud Controller from the drop-down menu. You can search for a specific Private Cloud Controller, select an individual Private Cloud Controller, click **Select All Displayed** to select all Private Cloud Controllers displayed in the drop-down menu, click **Clear All** to remove all selections, or click the **Delete** icon next to the selected Private Cloud Controller to remove it. All Private Cloud Controllers are selected by default.
- **Private Service Edges**: Select a Private Service Edge from the drop-down menu. You can search for a specific Private Service Edge, select an individual Private Service Edge, click **Select All Displayed** to select all Private Service Edges displayed in the drop-down menu, click **Clear All** to remove all selections, or click the **Delete **icon next to the selected Private Service Edge to remove it. All Private Service Edges are selected by default.
A drop-down menu is not available for the **Backup and Restore** and **Zscaler Client Connector** components.
[]Select a category from the drop-down menu. You can select an individual category, click **Select All Displayed** to select all categories displayed in the drop-down menu, or click **Clear All** to remove all selections. All categories are selected by default. The following is a list of supported categories:
- **Backup Configuration**: Indicates notifications regarding configuration backups and backups that are created manually or automatically.
- **Connectivity and Upgrade**: Indicates notifications regarding the component connectivity and component upgrades.
- **Enrollment**: Indicates notifications regarding the component enrollment.
- **System Resource**: Indicates notifications regarding the component system resources.
- **Usage Metrics**: Indicates notifications regarding the component usage metrics.
[]Select the priority of the notification (i.e., **Low**, **Medium**, and **High**). You can select an individual priority, click **Select All Displayed** to select all priorities displayed in the drop-down menu, or click **Clear All **to remove all selections. All priorities are selected by default.
[]**Throttling **enforces limits and timeout durations on the notification. Throttling is set to **Disabled** by default. When **Throttling **is **Enabled**, the Throttling Limit and Throttling Timeout fields appear.
- **Throttling Limit**: Enter an integer value to indicate the throttling limit.
- **Throttling Timeout**: Enter an integer value in hours to indicate the throttling timeout.
For example, the **Throttling Limit** value is 3, and the **Throttling Timeout** value is 1 hour. If the notification is set to trigger when the App Connector CPU is greater than 80%, the recipients receive only three email notifications within the last hour if the CPU of the App Connector exceeds the 80% threshold.
[See image.](#image3)
[]Under the **Recipients **section:
- Select the recipients from the drop-down menu. You can search for a specific recipient, select an individual recipient, click **Select All Displayed** to select all recipients displayed in the drop-down menu, click **Clear All **to remove all selections, or click the **Delete **icon next to the selected recipient to remove it.
- In the **Distribution List** field, enter the desired distribution list in the following format: `example@test.com`.
- Click **Add Items** so that the distribution list receives notifications after the notification is configured.
[See image.](#image4)
- Click **Next**.
[Click here to see an example email sent to a configured recipient.](#sampleEmail)
[]![Add Notification page](/downloads/zpa/notification-management/configuring-notifications/zpa-notifications-add-notification-page.png)
[]![Configuring the event in the Add Notification Window](/downloads/zpa/notification-management/configuring-notifications/zpa-notifications-add-notification-page-events-step.png)
[]![Enabling Throttling in the Add Notifications window](/downloads/zscaler-tech-pubs-style-guide/draft-articles/configuring-notifications-draft/zpa-add-notification-window-step3-throttling.png)
[]![Action tab of the Add Notifications page](/downloads/zpa/notification-management/configuring-notifications/zpa-notifications-add-notification-page-action-step.png)
[]
`Subject: [!] ZPA: Automatic Usage Metrics for Connector Lab App Connector with HIGH priority`
`Body: You are receiving this message because you requested notifications for:`
- `Tenant Name: SafemarchTenant ID: 198745983939657747ZPA`
- `Cloud Name: ProductionZPA`
- `Component: App ConnectorName: Lab App Connector`
- `Priority: HIGH`
- `Event/Notification alert: Event triggered as a result of Memory exceeded`
- `Review the relevant dashboards, analytics, and configuration settings in the ZPA Admin Portal.`
`Thank you,`
`Zscaler`
The sender email domain for the notifications might come from no-reply@private.zscaler.com or no-reply@zpatwo.net depending on your organization's assigned cloud. To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
Editing a Notification
[]To edit a notification:
- Go to **Configuration & Control **>** Notification Management **> **Notifications**.
-
In the table, locate the notification you want to modify and click the **Edit **icon (![Edit icon in the ZPA Admin Portal](/downloads/zscaler-tech-pubs-style-guide/draft-articles/editing-notifications-draft/zpa-about-notifications-edit-icon.png)
).
Notifications that are managed by Zscaler are read only and cannot be configured, edited, or deleted.
The **Edit Notification** page appears.
- On the **Edit Notification** page, modify fields as necessary, and then continue the steps to edit a notification. To learn more about each field and the steps to edit a notification, see the steps to [add a notification](#add).
Copying a Notification
[]To copy a notification:
- Go to **Configuration & Control** > **Notification Management **> **Notifications**.
- In the table, locate the notification you want to copy and click the **Copy **icon (![zpa-copy-icon.png](/downloads/tech-pubs-drafts/zpa-draft-articles/configuring-notifications-draft/zpa-copy-icon.png)
).
The **Add Notification** page appears that contains the prepopulated fields from the copied notification.
- On the **Add Notification** page, modify fields as necessary, and then continue the steps to add the new notification. To learn more about each field and the steps to add a notification, see the steps to [add a notification](#add).