# Configuring Self Service Settings
Source: https://help.zscaler.com/zdx/configuring-self-service-settings
PDF: https://help.zscaler.com/pdf/com/en/1459021.pdf

[Watch a video about Self Service.](https://fast.wistia.net/embed/iframe/3lcjrdtwo6)
Self Service can help users identify the root cause of issues related to CPU usage and Wi-Fi access, allowing users to investigate potential solutions without the need to contact customer support. When enabled for your users, Self Service provides notifications when issues are detected and need attention. Each notification contains a brief diagnosis and recommendation that might resolve the CPU or Wi-Fi issue.
Prerequisites
In order to enable Self Service notifications for users, you must:
- Have the minimum required versions of Zscaler Client Connector and ZDX Module. To learn more, see [Supported Versions & Feature Compatibility](/zdx/supported-versions-feature-compatibility#SelfService).
- Your ZDX subscription level supports Self Service. To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
- Full permission level for Self Service on ZDX. To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
- Enable Zscaler Client Connector Notification Framework on the Notifications page in the Zscaler Client Connector Portal. To learn more, see [Using the Zscaler Notification Framework](/client-connector/using-zscaler-notification-framework).
Configure Self Service Notifications for Users
Admins can configure the Self Service Settings page to enable Self Service notifications for users.
To configure the Self Service notifications for users:
- Go to **Administration** > **Settings** > **Self Service**.
- Select **Enable Self Service** to create criteria for Self Service notifications.
-
After enabling, you can configure the following:
-
**General Settings**: Admins can configure the General Settings of Self Service to include and exclude specific users, user groups, locations, location groups, departments, and devices. This allows specific users to receive a diagnosis and recommendations to solve their own IT issues when the Zscaler Notifications are enabled.
You cannot select deleted or unknown users for the include and exclude criteria.
- **Notification Settings**: Admins can configure the Notification Settings of Self Service to send push notifications via Zscaler Client Connector or enable users the ability to configure notifications.
[See image.](#SelfServiceSettings)
- **Save** your Self Service Settings.
If Self Service is enabled and notifications have started, you can review the notifications sent to the impacted users on the Self Service Overview dashboard. To learn more, see [Monitoring the Self Service Dashboard](/zdx/monitoring-self-service-dashboard).
[]
![Enable Self Service](/downloads/zdx/administration/configuring-self-service-settings/ZDX-Administration-SelfService-1.png)