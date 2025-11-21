# Monitoring the Self Service Dashboard
Source: https://help.zscaler.com/zdx/monitoring-self-service-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1462916.pdf

[Watch a video about Monitoring the Self Service Dashboard.](https://fast.wistia.net/embed/iframe/3lcjrdtwo6)
Self Service can help users identify the root cause of issues related to CPU usage and Wi-Fi access, allowing users to investigate potential solutions without the need to contact customer support. When enabled for your users, Self Service provides notifications when issues are detected and might need attention. Each notification contains a brief diagnosis and recommendation that might help resolve the CPU or Wi-Fi issue. To learn more about the notifications, see [Viewing Self Service User Notifications](/zdx/viewing-self-service-user-notifications). To learn more about configuring the notifications for your users, see [Configuring Self Service Settings](/zdx/configuring-self-service-settings).
The Self Service Dashboard consolidates user data pulled from the user notifications, and can provide a correlation between your users and the number, type, and frequency of notifications. To access the Self Service Dashboard in the ZDX Admin Portal, go to **Dashboard** > **Self Service Dashboard**.
Prerequisites
Before you can monitor notification and user data in the Self Service Dashboard, ensure:
- You're running the required versions of Zscaler Client Connector and ZDX Module. To learn more, see [Supported Versions & Feature Compatibility](/zdx/supported-versions-feature-compatibility#SelfService).
- Your subscription level supports Self Service. To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
- Your admin role is configured for Self Service. To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
Selecting Filters
Use the time range filter and page filters to help narrow the scope of notifications. Time range options are available in increments from the previous **2 Hours** to **14 Days**.
- **Departments**: Your departments, as defined in ZIA. To learn more, see [About Departments](/zia/about-departments).
- **Zscaler Locations**: Your locations, as defined in ZIA. To learn more, see [About Locations](/zia/about-locations).
- **Geolocations**: The geographic areas where your users are located.
- **Notification Types**: Identified as Wi-Fi, CPU, or Other.
Viewing Notification and User Counts
View the numerical counts for notifications and users, based on your selected time range:
- **Total Notifications Sent**: The number of notifications sent, including a percentage increase or decrease.
- **Notifications By Type**: The number of notifications related to Wi-Fi, CPU, or Other.
- **Total Users Notified**: The number of users who received notifications, including a percentage increase or decrease.
- **Users Found Notifications Helpful**: The number of users who provided feedback and indicated their notifications were helpful, including a percentage increase or decrease.
- **Active Users with Self Service Enabled**: The number of active users who have Self Service enabled, including a percentage increase or decrease.
- **Users Who Disabled Notifications**: The number of users who disabled their notifications, including a percentage increase or decrease.
![Notification and user counts](/downloads/zdx/analytics/monitoring-self-service-dashboard/zdx-ssit-overview-cards10.png)
Viewing Notifications Sent Over Time
The **Notifications Sent Over Time** graph shows the number of user notifications that were generated during your selected time range. The corresponding table provides a detailed list of user notifications that are specific to the time or dates within that time range:
- **User**: The user who received the notification.
- **Device**: The user's device that launched the notification.
- **Notification Type**: Indicates whether the notification was related to CPU, Wi-Fi, or another issue.
- **Found It Helpful?**: Indicates **Yes **or **No** if feedback was provided by the user. **Not available** indicates feedback was not provided.
- **Timestamp**: The date and time of the notification.
![Graph and table that show notifications](/downloads/tech-pubs-drafts/zdx-draft-articles/zdx-sandbox-config/zdx-ssit-overview-sot-and-table4.png)
Viewing User Device Events
Click the username in the notifications table to view the related event in the **User Device Events** graph. Notification icons indicate the dates and times when a notification was sent to the user. For example:
![Notification icon shown in User Device Events graph](/downloads/zdx/analytics/monitoring-self-service-dashboard/zdx-ssit-overview-device-events-icon2.png)