# Configuring Self Service Settings
Source: https://help.zscaler.com/unified/configuring-self-service-settings
PDF: https://help.zscaler.com/pdf/com/en/1493476.pdf

[Watch a video about Self Service.](https://fast.wistia.net/embed/iframe/3lcjrdtwo6)
Self Service can help users identify the root cause of issues related to CPU usage and Wi-Fi access, allowing users to investigate potential solutions without the need to contact customer support. When enabled for your users, Self Service provides notifications when issues are detected and need attention. Each notification contains a brief diagnosis and recommendation that might resolve the CPU or Wi-Fi issue.
Prerequisites
In order to enable Self Service notifications for users, you must:
- Have the minimum required versions of Zscaler Client Connector and ZDX Module.
- Your Digital Experience Monitoring subscription level supports Self Service. To learn more, see [Ranges & Limitations](/unified/ranges-limitations#analytics).
- Full permission level for Self Service on Digital Experience Monitoring. To learn more, see [Adding Digital Experience Monitoring Roles](/unified/adding-digital-experience-monitoring-roles).
- Enable Zscaler Client Connector Notification Framework on the Notifications page in the Admin Portal. To learn more, see [Using the Zscaler Notification Framework](/unified/using-zscaler-notification-framework).
Configure Self Service Notifications for Users
Admins can configure the Self Service Settings page to enable Self Service notifications for users.
To configure the Self Service notifications for users:
- Go to **Policies** > **Digital Experience Monitoring** > **Self Service**.
-
Select **Enable Self Service** to create criteria for Self Service notifications.
[See image.](#ZDX-Disabled)
- After enabling, you can configure the following:
- [General Settings](#general-settings)
- [Notification Settings](#notification-settings)
- **Save** your Self Service Settings.
If Self Service is enabled and notifications have started, you can review the notifications sent to the impacted users on the Self Service Overview dashboard. To learn more, see [Monitoring the Self Service Dashboard](/unified/monitoring-self-service-dashboard-0).
[]Admins can configure the Self Service Settings to include and exclude specific users, user groups, locations, location groups, departments, and devices. This allows specific users to receive a diagnosis and recommendations to solve their own IT issues when the Zscaler Notifications are enabled.
[See image.](#ZDX-GeneralSettings)
You cannot select deleted or unknown users for the include and exclude criteria.
[]Admins can configure the Notification Settings of Self Service to send push notifications via Zscaler Client Connector or enable users the ability to configure notifications.
[See image.](#ZDX-Notifications)
[]
![Enable Self Service](/downloads/zdx/administration/configuring-self-service-settings/ZDX-SelfServiceSettings-NotEnabled.png)
[]
![User Selection for Self Service Notifications](/downloads/zdx/administration/configuring-self-service-settings/ZDX-SelfServiceSettings-GeneralSettings.png)
[]
![Configure Self Service Notifications Settings](/downloads/zdx/administration/configuring-self-service-settings/ZDX-SelfServiceSettings-NotificationsSettings.jpg)