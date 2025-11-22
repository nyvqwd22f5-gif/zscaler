# Zscaler Endpoint Data Loss Prevention (DLP) Integration with Zscaler Client Connector
Source: https://help.zscaler.com/unified/zscaler-endpoint-data-loss-prevention-dlp-integration-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1494566.pdf

This feature is supported on devices running Zscaler Client Connector version 4.3 and later for Windows and Zscaler Client Connector version 4.2 and later for macOS. The Endpoint DLP feature is only supported on devices running macOS Monterey (12) and later versions. To learn about the prerequisites of this feature, see [Step-by-Step Configuration Guide](/unified/step-step-configuration-guide-zscaler-endpoint-dlp) for Zscaler Endpoint Data Loss Prevention (DLP).
Zscaler Endpoint Data Loss Prevention (DLP) safeguards your company’s data by monitoring activities that users take on endpoints such as, removable storage (e.g., USB external drives), printers, network shares, and personal cloud storage (e.g., Dropbox). To learn more, see [About Endpoint Data Loss Prevention](/unified/about-endpoint-data-loss-prevention) and [Understanding Endpoint Policy Enforcement](/unified/understanding-endpoint-policy-enforcement).
When you configure and activate the Endpoint DLP policy in Internet & SaaS, endpoints automatically use Zscaler Client Connector to retrieve the policy from the Zscaler cloud.
Endpoint DLP requires [Full Disk Access](/unified/deploying-zscaler-client-connector-jamf-pro-macos) for proper operation. MDM profiles that grant Full Disk Access must be deployed to endpoints prior to Endpoint DLP installation.
Configuring Endpoint DLP in the Admin Portal
Admins can enable Zscaler Endpoint DLP using the Admin Portal. For steps to enable the **Install Endpoint DLP** feature, see [Configuring Zscaler Client Connector App Profiles](/unified/configuring-zscaler-client-connector-app-profiles).
Endpoint DLP Integration With Zscaler Client Connector
On Zscaler Client Connector, the **Data Protection** window refers to the Zscaler Endpoint DLP feature. On the **Data Protection** window, the end-users can view the connection status of the service and perform troubleshooting.
![Data Protection on Zscaler Client Connector](/downloads/client-connector/zscaler-client-connector-profile-management/zscaler-endpoint-data-loss-protection-dlp-integration-zscaler-client-connector/data-protection-on-zscaler-client-connector.jpg)
Endpoint DLP enforces rules without an internet connection. After the connection is retrieved, it sends all the incidents and activities to the cloud.
Endpoint DLP Notifications
When a user violates an Endpoint DLP rule, and the user notifications are enabled, they receive a message on the endpoint based on the triggered rule.
![Endpoint DLP notifications](/downloads/client-connector/zscaler-client-connector-profile-management/zscaler-endpoint-data-loss-protection-dlp-integration-zscaler-client-connector/endpoint-dlp-notifications.png)
You can [configure Endpoint DLP policy rules](/unified/configuring-endpoint-dlp-policy-rules) to Allow, Block, or ask end users to Confirm activities that match the rule. If you select Allow, the service allows and logs the activity. If you select Block, the service blocks and logs the activity. If you select Confirm, the end user can justify the activity to continue or cancel the activity altogether; in both cases, the service logs the activity accordingly.
Examples of Endpoint DLP Notifications
- [Allow notification](#allow-notification)
- [Block notification](#block-notification)
- [Confirm notification](#confirm-notification)
[]When a user violates or triggers an Endpoint DLP rule that is configured for the Allow action and the[ End User Notification is selected as Show](/unified/configuring-endpoint-dlp-policy-rules), the Allow notification is displayed. The user can click **Learn more** for more details about the notification or click **Do Not Disturb** to prevent the notification from reappearing. The allow notification automatically disappears in 10 seconds.
![Allow notification](/downloads/client-connector/zscaler-client-connector-profile-management/zscaler-endpoint-data-loss-protection-dlp-integration-zscaler-client-connector/allow-notification.PNG)
[]When a user violates or triggers an Endpoint DLP rule that is configured for the Allow action and the [End User Notification is selected as Show](/unified/configuring-endpoint-dlp-policy-rules), the Block notification is displayed. The user can click **Learn more** to understand why their activity was blocked, and then click the **More options** drop-down menu and choose **Do Not Disturb** or **Request Exemption**.
![Block notification](/downloads/client-connector/zscaler-client-connector-profile-management/zscaler-endpoint-data-loss-protection-dlp-integration-zscaler-client-connector/block-notification.PNG)
[]If the admin has set rules with a confirm action, end users receive a notification requesting action. The user has 5 minutes to select an option. If the user doesn’t provide input within the time period, Zscaler blocks the user activity.
![Confirm notification](/downloads/client-connector/zscaler-client-connector-profile-management/zscaler-endpoint-data-loss-prevention-dlp-integration-zscaler-client-connector/confirm-notification.png)
Mute Notifications
Users can turn off Endpoint DLP user notifications on the **Zscaler Client Connector** > **More** > **Settings** >**Show all notifications**. Even if this setting is turned off, the Endpoint DLP notifications are still logged on the **Notifications** window.
Requesting Exemption from Data Protection
Authorized users can enter a One-Time Password (OTP) to disable the Endpoint DLP service on Zscaler Client Connector. End users can request exemptions on the Data Protection window in the Zscaler Client Connector app.