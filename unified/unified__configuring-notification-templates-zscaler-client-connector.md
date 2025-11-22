# Configuring Notification Templates for Zscaler Client Connector
Source: https://help.zscaler.com/unified/configuring-notification-templates-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1533749.pdf

You can configure notification templates for various settings for user notifications in Zscaler Client Connector and assign a template to specific groups of users in the app profile. Some of these settings are enabled after a user’s device is enrolled in the Zscaler service and can be changed by a user in Zscaler Client Connector.
This feature is available only for Zscaler Client Connector version 4.8 and later for Windows and you must have the [Zscaler Notification Framework](/unified/using-zscaler-notification-framework) enabled. When you enable this feature, the [End User Notifications](/unified/configuring-end-user-notifications-zscaler-client-connector) tab no longer displays and the existing settings from that tab are copied to a Legacy Notification Settings template.
To configure a notification template:
- Go to **Policies **>** Common Configuration **>** Resources > Client Connector Notifications**.
-
On the **Notification Templates** tab, click **Add** to create a new template or click **Edit** beside an existing template.
![Notification Template tab](/downloads/zscaler-client-connector/administration/zscaler-client-connector-notifications/configuring-notification-templates-zscaler-client-connector/zclient-connector-notification-template-tab.png)
- On the Notification Template window, configure the following settings:
- **Name**: Enter a name for the template. The default Legacy Notification Settings template name cannot be changed.
- **Default**: If you are configuring a template that is not the Legacy Notification Settings template, select whether this notification template is the default template for new app profiles.
- **Show ZCC Notification Popups by Default**: Select this option to have users receive pop-up notifications from Zscaler Client Connector. This setting is enabled after a user is enrolled. Users can turn this option off from Zscaler Client Connector in the More window in the app.
- **Enable App Updates Notifications**: Select this option to have users receive app upgrade notifications.
- **Enable Service Status Notifications**: Select this option to have users receive status notifications for Zscaler services, such as when a service is in Disaster Relief (DR) mode.
- **Enable ZIA Notifications**: Select this option to have users receive notifications from Internet & SaaS, such as data loss prevention (DLP) notifications. To learn more, see [About Zscaler Client Connector-Based End User Notifications](/unified/about-zscaler-client-connector-based-end-user-notifications).
- **Enable Notifications for ZPA reauthentication**: Select this option to have users prompted for authentication. This option is enabled after a user is enrolled. Users can turn this option off from Zscaler Client Connector in the More window in the app.
- **Show ZPA Reauthentication Notifications Every (In Minutes)**: Select this option to show Private Access reauthentication notifications at a specific time interval. This setting is enabled by default. Enter a value from `2` to `1440` to set the interval in minutes.
- **Custom Timer (In Seconds)**: Set the amount of time that the notification displays for the user. Enter a time between `5` and `60` seconds.
- **Enable Persistent Notifications**: When enabled, overrides the Custom Timer. This setting displays critical notifications until the user dismisses them. Critical notifications include Private Access reauthentication, captive portal detection, and request for a system reboot.
- **ZIA Notification Persistent**: When enabled, overrides the Custom Timer and makes [Endpoint Data Loss Prevention (DLP) notifications](/unified/configuring-euns-endpoint-dlp) persistent.
- **Do not disturb**: When enabled, Zscaler Client Connector pop-up notifications include a Do not Disturb button. The default value is enabled, but you can clear this option to prevent the button from displaying.
- **ZIA Firewall**: Select this option to show firewall notifications from Internet & SaaS in the Notifications window in the app. If enabled, you can select **Firewall Popup Notifications** to also display them as pop-up notifications. To learn more, see [Configuring EUNs for Firewall Filtering](/unified/configuring-euns-firewall-filtering).
- **DNS**: Select this option to show DNS notifications from Internet & SaaS in the Notifications window in the app. If enabled, you can select **DNS Popup Notifications** to also display them as pop-up notifications. To learn more, see [Configuring EUNs for DNS Control](/unified/configuring-euns-dns-control).
-
**IPS**: Select this option to show IPS notifications from Internet & SaaS in the Notifications window in the app. If enabled, you can select **IPS Popup Notifications** to also display them as pop-up notifications. To learn more, see [Configuring EUNs for IPS Control](/unified/configuring-euns-ips-control).
You must also select** Enable ZIA Notifications** to display the ZIA Firewall, DNS, and IPS notifications for users.
After you create a template, you can assign it to an app profile to apply the notification settings to a group of users.