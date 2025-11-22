# Configuring End User Notifications for Zscaler Client Connector
Source: https://help.zscaler.com/zscaler-client-connector/configuring-end-user-notifications-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1296721.pdf

In the Zscaler Client Connector Portal, you can configure various settings for [user notifications in Zscaler Client Connector](/zscaler-client-connector/zscaler-client-connector-pop-notifications). Some of these settings are enabled after a user’s device is enrolled in the Zscaler service and can be changed by a user in Zscaler Client Connector.
If you use notification templates, this tab does not display, and you must configure the end user notification settings on the Notification Templates tab. To learn more, see [Configuring Notification Templates for Zscaler Client Connector](/zscaler-client-connector/configuring-notification-templates-zscaler-client-connector).
Configure user notifications as follows:
- Go to **Administration **> **Client Connector Notifications**.
- Click the **End User Notifications** tab and select from the following options:
- **Enable Notifications by Default**: This setting is enabled when a user is enrolled. Users can turn this option off from Zscaler Client Connector.
- **Enable App Updates Notifications**: Select this option to have users receive app upgrade notifications.
- **Enable Service Status Notifications**: Select this option to have users receive status notifications for Zscaler services, such as when a service is in Disaster Relief (DR) mode.
- **Enable ZIA Notifications**: Select this option to have users receive notifications from ZIA, such as data loss prevention (DLP) notifications.
- **Enable Notifications for ZPA reauthentication**: Select this option to have users prompted for Zscaler Private Access (ZPA) authentication. This option is enabled after a user is enrolled. Users can turn off this option from Zscaler Client Connector.
- **Show ZPA Reauthentication Notifications Every (In Minutes)**: Select this option to show ZPA reauthentication notifications at a specific time interval. This setting is enabled by default. Enter a value from `2` to `1440` to set the interval in minutes.
For Windows and macOS only, you can configure the following settings for the Zscaler Notification Framework.
You must have Zscaler Client Connector version 4.2 and later for Windows and version 4.2 and later for macOS to[ enable the Zscaler Notification Framework](/zscaler-client-connector/about-zscaler-notification-framework) in App Profiles.
- **Custom Timer (In Seconds)**: Set the amount of time that the notification displays for the user. Enter a time between 5 and 60 seconds.
- **Enable Persistent Notifications**: When enabled, overrides the **Custom Timer**. This setting displays critical notifications until the user dismisses them. Critical notifications include ZPA reauthentication, captive portal detection, and request for a system reboot.
- **ZIA Notification Persistent**: When enabled, overrides the **Custom Timer** and makes certain ZIA notifications persistent. Currently, the ZIA Notification Persistent option only applies to DLP notifications.
![Configuring End User Notifications](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-end-user-notifications-zscaler-client-connector-doc-48688/ZClientConnector-end-user-notifications.png)
- Click **Save**.