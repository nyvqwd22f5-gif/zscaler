# Viewing and Managing Events Diagnostics
Source: https://help.zscaler.com/zpa/viewing-and-managing-events-diagnostics
PDF: https://help.zscaler.com/pdf/com/en/1485451.pdf

This article describes how to view and filter event logs for notifications. Admins subscribe to events to receive email notifications from the ZPA Admin Portal. After an event is triggered, admins receive alerts of these notifications via email. To learn more, see [About Notifications](/zpa/about-notifications). The Events Diagnostics page displays these notifications.
Accessing Events Diagnostics
To access diagnostics for events:
- Go to **Analytics > Diagnostics**.
- Under **Log Type**, select **Events**.
By default, the information for all events is displayed for notifications that occurred in the last 24 hours. You can do the following:
- Click the **Calendar** drop-down menu to change the time range. In the **Calendar** drop-down menu, you can select a preset range or specify a custom start and end date. If you use a **Custom Range**, the start date must be within the last 14 days.
- Click the **Time Zone** icon to change the time zone.
- Click the **Refresh** icon to refresh the diagnostics page.
- Click the **Settings **icon to configure the [diagnostics settings](#settings).
[See image.](#eventsDiagnosticsTools)
[]![Events Diagnostics tools](/downloads/zpa/dashboard-diagnostics/about-events-diagnostics/EventsDiagnosticsGIF2.gif)
[Dashboard](/zpa/dashboard-diagnostics) data might be more recent than the data presented within Diagnostics.
By default, the table displays the **Total **number of events. To change this, select one of the following filters:
- **High Priority**: The number of high priority events.
- **Medium Priority**: The number of medium priority events.
- **Low Priority**: The number of low priority events.
![Diagnostics widgets](/downloads/zpa/dashboard-diagnostics/about-events-diagnostics/zpa-events-diagnostics-total-events2.png)
[]Configuring Settings
To configure settings for diagnostics pages in the ZPA Admin Portal:
- Go to **Analytics** > **Diagnostics**.
- Click the **Settings** icon (![Settings icon within the diagnostics pages](/downloads/tech-pubs-drafts/configuring-diagnostics-settings-doc-60060/zpa-diagnostics-settings-icon.png)
).
The **Settings** drawer appears.
-
In the **Settings** drawer, select the default filter operator (i.e., **Equals** or **Contains**) from the** **drop-down menu. The **Default Filter Operator** is set to **Equals** by default.
[See image.](#settingsDrawer)
-
Click **Save** to apply your changes.
The selected filter operator is saved for future sessions.
[]![Settings drawer in the diagnostics pages](/downloads/tech-pubs-drafts/configuring-diagnostics-settings-doc-60060/zpa-diagnostics-settings-drawer.png)
Filtering Event Diagnostics
On the Events page, you can apply filters or drill down further into the log data. By default, no filters are applied.
To configure filters using the Query Builder:
- Click **Add Filters** and select a filter from the drop-down menu. To learn more, see the [Event Filters](#eventFilters) section.
- Select a Boolean operator from the drop-down menu (e.g., **Equals**, **Not Equals**).
- Select the fields from the drop-down menu or enter the values required for the filter. The field or value required is determined by the filter you are configuring.
![Events Diagnostics filtering](/downloads/zpa/dashboard-diagnostics/about-events-diagnostics/zpa-events-diagnostics-filtering2.png)
- Click **Apply**.
To apply more filters, click **Add Filters** again or click on the **Filter **icon (![Apply Filter icon](/downloads/zpa/dashboard-diagnostics/about-events-diagnostics/zpa-apply-filter-icon.png)
) within the table. To remove an added filter, click the **Delete **icon (![Delete icon](/downloads/zpa/dashboard-diagnostics/about-events-diagnostics/zpa-delete-icon.png)
), then click **Apply**. To remove all filters, click **Clear All**. You can also click the **Copy **icon to save the filter query details. If you or another ZPA admin access **Diagnostics**, you can paste the query into the field by clicking the **Clipboard **icon.
[See image.](#FilteringTools)
[]![Filtering tools](/downloads/zpa/dashboard-diagnostics/about-events-diagnostics/zpa-events-diagnostics-filtering-tools2.png)
[]Event Filters
You can add the following filters:
- **App Connector: Name**: See event logs by the App Connector.
- **Backup Name**: See event logs by the [backup](/zpa/about-backup-and-restore).
- **Cloud Connectors**: See event logs by the Cloud Connector.
- **Event Category: **See event logs by category** **(i.e.,** Authentication**,** Backup Configuration**, **Connectivity and Upgrade**, **Enrollment**, **System Resource**, **Usage Metrics**).** **To learn more, see the [Category](#Category) section.
- **Event Component: **See event logs by component (i.e., **App Connectors**, **Backup and Restore**, **Cloud Connectors**, **Private Service Edges**,** **and **Zscaler Client Connector**).** **To learn more, see the [Component](#Component) section.
- **Event Name: **See event logs by the type of the event. To learn more, see the [Events table](#eventTable).
- **Event Priority: **See event logs by the priority of the event (i.e.,** High**, **Medium**, **Low**). To learn more, see the [Priority ](#Priority)section.
- **Private Service Edge: Name**: See event logs by the ZPA Private Service Edge.
The table displays the following data about events. You can expand each row to see more details or click **Expand All** or **Collapse All** to expand or collapse all rows within the table. You can scroll to load more transactions.
The table of events provides the following information:
- [Timestamp](#Timestamp)
- [Event](#Event)
- [Category](#Category)
- [Component](#Component)
- [Priority](#Priority)
- [Action](#Action)
[]The data and time when the event log was generated. The column sorts requests by the date and start time in descending order. You can click the **Arrow **icon (![Arrow icon](/downloads/zpa/dashboard-diagnostics/about-events-diagnostics/zpa-arrow-icon.png)
) to sort the requests in ascending order.
The time displayed is based on the time the event was triggered.
Expanding an event provides the following:
- Event Log: View, download, and copy the raw JSON for the event:
- Click the **View Log** icon (![View Log icon](/downloads/zpa/dashboard-diagnostics/about-events-diagnostics/zpa-view-log-icon.png)
) to display the Raw JSON for the event within the ZPA Admin Portal.
- Click the **Download **icon (![Download icon](/downloads/zpa/dashboard-diagnostics/about-events-diagnostics/zpa-download-icon.png)
) to download the raw JSON for the event to a text (.txt) file.
- Click the **Copy** icon (![Copy icon](/downloads/zpa/dashboard-diagnostics/about-events-diagnostics/zpa-copy-icon.png)
) to copy the raw JSON text for the event to your clipboard.
[]The type of event that triggered the notification.
Expanding an event provides the following provides information regarding the status and outcome of the event.
The following table provides a list of events, as well as the category and component the event belongs to:
[]
[](/zpa/about-backup-and-restore)[](/zpa/restoring-policies-and-configurations-backup)[](/zpa/about-backup-and-restore)[](/zpa/restoring-policies-and-configurations-backup)[](/zpa/monitoring-connector-performance#cpu)[](/zpa/monitoring-connector-performance#diskspace)[](/zpa/about-enrollment-ca-certificates)[](/zpa/ranges-limitations)[](/zpa/monitoring-connector-performance#filedscrpt)[](/zpa/about-backup-and-restore)[](/zpa/restoring-policies-and-configurations-backup)[](/zpa/about-backup-and-restore)[](/zpa/restoring-policies-and-configurations-backup)[](/zpa/monitoring-connector-performance#memory)
| Event | Category | Component | Description |
| ----- | -------- | --------- | ----------- |
| Application Exceeded Count Limit | Usage Metrics | App Connectors | An event indicating when the component's application count has exceeded the limit. The Application Exceeded Count Limit value must be an integer between 4500 and 6000. The default value is set to 4500. |
| Backup Completed | Backup Configuration | Backup and Restore | An event indicating when the backup is completed. To learn more, see About Backup and Restore and Restoring Policies and Configurations from a Backup. |
| Backup Failed | Backup Configuration | Backup and Restore | An event indicating when the backup has failed. To learn more, see About Backup and Restore and Restoring Policies and Configurations from a Backup. |
| Bandwidth Utilization Exceeded Limit | Usage Metrics | App Connectors, Private Service Edges | An event indicating when the component's bandwidth utilization has exceeded the limit. The Bandwidth Utilization Exceeded Limit value must be an integer greater than or equal to 250 Mbps. The default value is set to 250. |
| Control Connection Disconnected | Connectivity and Upgrade | App Connectors, Private Service Edges | An event indicating when the control connection for App Connectors or ZPA Private Service Edges disconnects. This event cannot be configured and is disabled by default. To learn more, contact Zscaler Support |
| CPU Exceeded Limit | Usage Metrics | App Connectors, Private Service Edges | An event indicating when the component's CPU utilization has exceeded the limit. The CPU Exceeded Limit value must be an integer between 75% and 99%. The default value is set to 75. To learn more, see Monitoring App Connector Performance. |
| CPU Starvation | System Resource | App Connectors | An event indicating when the App Connector's CPU is missing resources needed for operations. This event cannot be configured and is disabled by default. To learn more, contact Zscaler Support |
| Certificate Signing Request Invalid | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating Certificate Signing Request (CSR) is invalid for the selected components. |
| Certificate Signing Request Not Found | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating when the CSR is not found for the selected components. |
| Certificate Signing Request Not Found for Issued Certificate | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating when the CSR for the selected components is not found for the issued certificate. |
| Disk Space Exceeded Limit | Usage Metrics | App Connectors, Private Service Edges | An event indicating when the component's available disk space is less than the indicated threshold. The Disk Space Exceeded Limit value must be an integer between 0 and 2048 MB. The default value is set to 2048. To learn more, see Monitoring App Connector Performance. |
| Duplicate Certificate Signing Request | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating that there is a duplicate CSR for the selected components. |
| Duplicate Serial Number | Enrollment | Zscaler Client Connector | An event indicating that there is a duplicate serial number during Zscaler Client Connector enrollment. |
| Enrollment Certificate Expired | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating when an enrollment certificate has expired for the selected component. To learn more, see About Enrollment (CA) Certificates. |
| Enrollment Certificate Invalid | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating an invalid enrollment certificate for the selected components. |
| Enrollment Completed | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating when the enrollment of the component is completed. |
| Enrollment Failed | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating when the enrollment for the selected component has failed. |
| Entity Limit Exceeded | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating when an entity limit is exceeded for a component. To learn more, see Ranges & Limitations. |
| File Descriptors Exhausted | Usage Metrics | App Connectors, Private Service Edges | An event indicating when the component's file descriptors are exhausted. The File Descriptors Exhausted value must be an integer between 75% and 99%. The default value is set to 75. To learn more, see Monitoring App Connector Performance. |
| Invalid Fingerprint | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating when a fingerprint for the selected components is invalid. |
| Invalid Signature | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating when a signature for the selected components is invalid. |
| Invalid System Listen IP Configuration | System Resource | Private Service Edges | An event indicating when the listen IP address configuration for a ZPA Private Service Edge is invalid. |
| Issued Certificate Missing | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating when the issued certificate is missing for the selected components. |
| Issued Certificate Revoked | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating when the issued certificate is revoked for the selected components. |
| Last Component Disconnected | Connectivity and Upgrade | App Connectors, Private Service Edges | An event indicating when the component last disconnects for the selected component. |
| Missing Signature | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating when the signature for the selected components is missing during enrollment. |
| Outdated Component Manager Version | Connectivity and Upgrade | App Connectors, Private Service Edges | An event indicating when the Manager version is outdated for the selected components. |
| Provisioning Key Disabled | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating when the provisioning key is disabled for the selected components. |
| Provisioning Key Expired | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating when the provisioning key is expired for the selected components. |
| Provisioning Key Mismatched | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating when the provisioning key is mismatched for the selected components. |
| Provisioning Key Utilization Exceeded Limit | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating when the provisioning key has exceeded the limit for the selected components. |
| Public Key in Certificate Signing Request and Issued Certificate Mismatched | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating when the public key in the CSR and the issued certificate are mismatched for the selected components. |
| Restore Completed | Backup Configuration | Backup and Restore | An event indicating when the restore is completed. To learn more, see About Backup and Restore and Restoring Policies and Configurations from a Backup. |
| Restore Failed | Backup Configuration | Backup and Restore | An event indicating when the restore has failed. To learn more, see About Backup and Restore and Restoring Policies and Configurations from a Backup. |
| SCIM Users Successfully Deleted | Enrollment | Zscaler Client Connector | An event indicating when SCIM users are successfully deleted. |
| Source Port Consumption Exhausted | Usage Metrics | App Connectors, Private Service Edges | An event indicating when the component's source TCP or UDP ports are exhausted. The exhausted values must be an integer between 75% and 99%. The default value is set to 75. |
| System Memory Exceeded Limit | Usage Metrics | App Connectors, Private Service Edges | An event indicating when the component's system memory has exceeded the limit. The System Memory Exceeded Limit value must be an integer between 75% and 99%. The default value is set to 75. To learn more, see Monitoring App Connector Performance. |
| Timestamp Expired | Enrollment | App Connectors, Private Service Edges, Cloud Connectors | An event indicating when the timestamp is expired for the selected components (e.g., an App Connector sends an old timestamp due to a Network Time Protocol error). |
| Upgrade Complete | Connectivity and Upgrade | App Connectors, Private Service Edges | An event indicating when an upgrade is complete for the selected components. |
| Upgrade Failed | Connectivity and Upgrade | App Connectors, Private Service Edges | An event indicating when an upgrade fails for the selected components. |
[]The category of the event. Events are grouped by the component issues related to the following categories:
- **Authentication**: Issues related to authentication.
- **Backup Configuration**: Issues related to configuration backups and backups that are created manually or automatically.
- **Connectivity and Upgrade**: Issues related to component connectivity and upgrades.
- **Enrollment**: Issues related to enrollment.
- **System Resource**: Issues related to component system resources.
- **Usage Metrics**: Issues related to usage metrics.
[]The component associated with the event. The following components are applicable to the events:
- **App Connectors**: To learn more, see [About App Connectors](/zpa/about-connectors).
- **Backup and Restore**: To learn more, see [About Backup and Restore](/zpa/about-backup-and-restore).
- **Private Service Edges**: To learn more, see [About ZPA Private Service Edges](/zpa/about-zpa-private-service-edges).
- **Cloud Connectors**: To learn more, see [About Cloud Connectors](/zpa/about-cloud-connectors).
- **Zscaler Client Connector**: To learn more, see [What Is Zscaler Client Connector?](/zscaler-client-connector/what-is-zscaler-client-connector)
Expanding an event provides the following:
- **App Connector Name**: The name of the App Connector.
- **App Connector ID**: The ID of the App Connector. Click the **Copy** icon to copy the ID to your clipboard.
- **Backup Name**: The name of the backup.
- **Backup ID**: The ID of the backup. Click the **Copy **icon to copy the ID to your clipboard.
- **Cloud Connector Name**: The name of the Cloud Connector.
- **Cloud Connector ID**: The ID of the Cloud Connector. Click the **Copy **icon to copy the ID to your clipboard.
- **Private Service Edge Name**: The name of the ZPA Private Service Edge.
- **Private Service Edge ID**: The ID of the Private Service Edge. Click the **Copy **icon to copy the ID to your clipboard.
[]Indicates the priority of the notification (i.e., **Low**, **Medium**, and **High**).
[]Click the **Add Notification** icon (![Add Notification icon](/downloads/zpa/dashboard-diagnostics/about-events-diagnostics/zpa-events-diagnostics-add-notifications-icon.png)
) to open the **Add Notification** window.
In the **Add Notification** window:
- [Step 1: General Information](#Step1GeneralInformation)
- [Step 2: Events](#Step2Events)
- [Step 3: Action](#Step3Action)
- [Step 4: Review](#Step4Review)
- []On the **General Information** tab, provide the necessary details for the following sections:
- **Name**: The name of the notification.
- **Status**: Indicates the status of the notification (i.e., **Enabled **or **Disabled**). By default, the status is set to **Enabled**.
- [Select a Component](#SelectaComponent)
- [Select a Category](#SelectaCategory)
- [Select a Priority](#SelectaPriority)
- Click **Next**.
![Add Notification window](/downloads/zpa/dashboard-diagnostics/about-events-diagnostics/zpa-add-notification-step1-updated-ui.png)
[]On the **Events **tab:
- Click **Add Events**.
- Select the desired event.
For events that require text input, enter an integer value within the supported range. To learn more, see the [Events table](#eventTable).
[See image.](#Step2SeeImage)
- Click **Next**.
[]On the **Action **tab:
- [Configure the Throttling](#ConfiguretheThrottling)
- [Configure the Recipients](#ConfiguretheRecipients)
- []Review your notification settings.
- Click **Save**.
[]![Step 2 of the Add Notification window](/downloads/zpa-events-diagnostics-add-notifications-step2.png)
[]Select a component from the drop-down menu. The following is a list of available components. To learn more, see the [Component](#Component) section.
Click the **Delete **icon (![Delete icon](/downloads/zpa/dashboard-diagnostics/about-events-diagnostics/zpa-add-notification-delete-icon.png)
) to remove a selected component. After a component is selected, a drop-down menu appears for the **Categories**, **Priorities**, and selection of the components.
After a component is selected, select the desired App Connectors, Cloud Connectors, or Private Service Edges from the list of available components:
- **App Connectors**: Select an App Connector from the drop-down menu. You can search for a specific App Connector, select an individual App Connector, click **Select All Displayed** to select all App Connectors displayed in the drop-down menu, click **Clear All** to remove all selections, or click the **Delete **icon next to the selected App Connector to remove it. All App Connectors are selected by default.
- **Cloud Connectors**: Select a Cloud Connector from the drop-down menu. You can search for a specific Cloud Connector, select an individual Cloud Connector, click **Select All Displayed** to select all Cloud Connectors displayed in the drop-down menu, click **Clear All** to remove all selections, or click the **Delete **icon next to the selected Cloud Connector to remove it. All Cloud Connectors are selected by default.
- **Private Service Edges**: Select a Private Service Edge from the drop-down menu. You can search for a specific Private Service Edge, select an individual Private Service Edge, click **Select All Displayed** to select all Private Service Edges displayed in the drop-down menu, click **Clear All** to remove all selections, or click the **Delete **icon next to the selected Private Service Edge to remove it. All Private Service Edges are selected by default.
A drop-down menu is not available for the **Zscaler Client Connector **component.
[]Select a category from the drop-down menu. You can select an individual category, click **Select All Displayed** to select all categories displayed in the drop-down menu, or click **Clear All** to remove all selections. All categories are selected by default. To learn more, see the [Category ](#Category)section.
[]Select the priority of the notification (i.e., **Low**, **Medium**, and **High**). You can select an individual priority, click **Select All Displayed** to select all priorities displayed in the drop-down menu, or click **Clear All** to remove all selections. All priorities are selected by default.
[]**Throttling **enforces limits and timeout durations on the notification. Throttling is set to **Disabled **by default. When **Throttling **is **Enabled**, the **Throttling Limit** and **Throttling Timeout** fields appear.
- **Throttling Limit**: Enter an integer value to indicate the throttling limit.
- **Throttling Timeout**: Enter an integer value in hours to indicate the throttling timeout.
For example, the **Throttling Limit** value is 3, and the **Throttling Timeout **value is 1 hour. If the notification is set to trigger when the App Connector CPU is greater than 80%, the recipients receive only three email notifications within the last hour if the CPU of the App Connector exceeds the 80% threshold.
[See image.](#ThrottlingImage)
[]![Throttling](/downloads/zpa-events-diagnostics-add-notification-step3-throttling.png)
[]Under the Recipients section:
- Select the recipients from the drop-down menu. You can search for a specific recipient, select an individual recipient, click **Select All Displayed** to select all recipients displayed in the drop-down menu, click **Clear All** to remove all selections, or click the **Delete** icon next to the selected recipient to remove it.
- In the **Distribution List** field, enter the desired distribution list alias in the following format: `example@test.com`.
A maximum of 5 recipients combined (this includes both **Recipients** and **Distribution Lists**) is allowed.
- Click **Add Items** so that the distribution list receives notifications after the notification is configured.
[See image.](#Step3RecipientsImage)
- Click **Next**.
[]![Step 3 of the Add Notification window](/downloads/zpa-events-diagnostics-add-notification-step3-updated-UI.png)