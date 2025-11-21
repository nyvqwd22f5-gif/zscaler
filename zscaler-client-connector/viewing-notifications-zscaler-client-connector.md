# Viewing Notifications on Zscaler Client Connector
Source: https://help.zscaler.com/zscaler-client-connector/viewing-notifications-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1370041.pdf

This article provides an overview of the **Notifications **window of Zscaler Client Connector.
- [Windows](#win)
- [macOS](#macos)
- [Linux](#linux)
- [Android](#android)
- [Android on ChromeOS](#chrome)
- [iOS](#ios)
For information about other Zscaler Client Connector features, see [Using Zscaler Client Connector](/zscaler-client-connector/using-zscaler-client-connector).
[]This section covers the following topics:
- [Viewing Notifications on Windows](#win-notification)
- [Enabling Notifications in the System Tray](#show-notifications-system-tray)
[]In the Notifications window, you can view the following information:
- **Application**: Displays the name of the application relevant to the action that triggered the notification. In the following example, **Zscaler Client Connector** is listed in the **Application** column when the notification is relevant only to Zscaler Client Connector. For example, you received a notification after the app required you to reauthenticate into the Zscaler Private Access (ZPA) service, in order to access internal applications. As another example, if you attempted to upload content to Dropbox.com in violation of one of your organization's cloud app control policies in the Zscaler Internet Access (ZIA) service, you would receive a notification and see Dropbox.com in the **Application** column.
- **Time**: Displays the time when the notification was received.
- **Message**:** **Displays the notification message.
Click **Clear All** to clear all notifications from this page.
![The Notifications window of Zscaler Client Connector for Windows](/downloads/tech-pubs-drafts/client-connector-draft-articles/viewing-notifications-zscaler-client-connector-windows-0/zscaler-app-shown-notifications-windows_0.png)
[]To display notifications from the system tray icon:
- Click **More**.
- In the **Settings **section, you can:
- Manually enable or disable [pop-up notifications](/zscaler-client-connector/zscaler-client-connector-pop-notifications). The default setting is set by the admin. If notifications are enabled, notifications appear in the tray icon. This setting doesn’t affect ZPA reauthentication notifications.
- Override the default setting that was configured in the Zscaler Client Connector Portal to show ZPA reauthentication notifications.
- Pause notifications by enabling **Do Not Disturb (DND) Mode**. You can pause notifications in 30-minute, 1-hour, or 2-hour increments.
![Show notifications in Zscaler tray icon](/downloads/zscaler-client-connector/end-user-guide/viewing-notifications-zscaler-client-connector/zscaler-client-connector-more-window.png)
For Zscaler Client Connector version 3.8 and later for Windows, you can instead use Zscaler's Notification Framework. You cannot disable notifications in Windows settings. To learn more, see [About the Zscaler Notification Framework](/zscaler-client-connector/about-zscaler-notification-framework).
[]This section covers the following topics:
- [Viewing Notifications on macOS](#macos-notification)
- [Enabling Notifications on the Menu Bar](#show-notifications-menu-bar)
[]In the Notifications window, you can view the following information:
-
**Application**: Displays the name of the application relevant to the action that triggered the notification.
In the following example, **Zscaler Client Connector **is listed in the **Application **column because the notification was relevant only to Zscaler Client Connector. For example, you received the notification after disabling the app's Zscaler Internet Access (ZIA) service. As another example, if you attempted to upload content to Dropbox.com in violation of one of your organization's cloud app control policies, you would receive a notification and see Dropbox.com in the **Application** column.
- **Time**: Displays the time when the notification was received.
- **Message**:** **Displays the notification message.
Click **Clear All** to clear all notifications from this page.
![The Notifications window of Zscaler Client Connector for macOS](/downloads/z-app/end-user-guides/viewing-notifications-zscaler-client-connector/ZClient-Conn-notification-macos.png)
[]To display notifications from the menu bar icon:
- Click **More**.
- In the **Settings** section, you can:
- Manually enable or disable menu bar notifications. The default setting is set by the admin. If notifications are enabled, you see notifications on the app icon.
- Override the default setting that was configured in the Zscaler Client Connector Portal to show ZPA reauthentication notifications.
![Enabling Zscaler Client Connector for macOS to show menu bar notifications](/downloads/tech-pubs-drafts/client-connector-draft-articles/viewing-notifications-zscaler-client-connector-doc-55419/Notifications_macOS.png)
[]This section covers the following topics:
- [Viewing Notifications on Linux](#linux-notification)
- [Enabling Notifications in the System Tray](#show-notifications-linux-menu-bar)
[]In the Notifications window, you can view the following information:
-
**Application**: Displays the name of the application relevant to the action that triggered the notification.
**Zscaler **is listed in the **Application **column because the notification was relevant only to Zscaler Client Connector. For example, you received the notification after disabling the app's Zscaler Internet Access (ZIA) service. As another example, if you attempted to upload content to Dropbox.com in violation of one of your organization's cloud app control policies, you would receive a notification and see Dropbox.com in the **Application** column.
- **Time**: Displays the time when the notification was received.
- **Message**:** **Displays the notification message.
Click **Clear All** to clear all notifications from this page.
![The Notifications window of Zscaler Client Connector for Linux](/downloads/tech-pubs-drafts/client-connector-draft-articles/viewing-notifications-zscaler-client-connector-draft-doc-50360/zscaler-client-connector-notifications-linux.png)
[]To display notifications in the system tray:
- Click **More**.
- In the **Settings** section, you can:
- Manually enable or disable system tray notifications. The default setting is set by the admin. If notifications are enabled, you see notifications on the app icon. This setting doesn't affect ZPA reauthentication notifications.
- Override the default setting that was configured in the Zscaler Client Connector Portal to show ZPA reauthentication notifications.
![Enabling Zscaler Client Connector for Linux to show system tray notifications](/downloads/tech-pubs-drafts/client-connector-draft-articles/viewing-notifications-zscaler-client-connector-doc-55419/Linux_app_More.png)
[]This section covers the following topics:
- [Viewing Notifications on Android](#android-notification)
- [Enabling Notifications on the App Icon](#enable-notification-android)
[]In the Notifications screen, you can view the following information:
- The name of the application and the action that triggered it. For example, the following image shows a notification you’d receive after the app’s Zscaler Private Access (ZPA) service started. As another example, if you attempted to upload content to Dropbox.com in violation of one of your organization’s cloud app control policies, you'd receive a notification with Dropbox.com listed.
- The notification message and the time when it was received.
Tap the **Delete** icon in the top-right corner to clear all notifications from this screen.
Use the drop-down menu to filter the notifications by the predefined time frames. You can view notifications from **Today**, the **Last 7 Days**, the **Last 10 Days**, or view **All** notifications.
![The Notifications screen of Zscaler Client Connector for Android](/downloads/tech-pubs-drafts/client-connector-draft-articles/viewing-notifications-zscaler-client-connector-doc-55419/client-connector-notifications-android.png)
[]To display notifications on the app icon:
- Tap **More**.
- In the **Settings** section, you can:
- Manually enable or disable pop-up notifications. The default setting is set by the admin. If notifications are enabled, notifications appear on the app icon. This setting doesn’t affect ZPA reauthentication notifications.
- Override the default setting that was configured in the Zscaler Client Connector Portal to enable or disable ZPA reauthentication notifications.
![Notification screen on Zscaler Client Connector for Android](/downloads/tech-pubs-drafts/client-connector-draft-articles/viewing-notifications-zscaler-client-connector-doc-55419/Settings_Android.jpg)
[]This section covers the following topics:
- [Viewing Notifications on Android on ChromeOS](#chrome-notification)
- [Enabling Notifications on the App Icon](#enable-notification-chrome)
[]In the Notifications screen, you can view the following information:
- The name of the application and the action that triggered it. For example, the following image shows a notification you’d receive after the app’s Zscaler Private Access (ZPA) service started. As another example, if you attempted to upload content to Dropbox.com in violation of one of your organization’s cloud app control policies, you'd receive a notification with Dropbox.com listed.
- The notification message and the time when it was received.
Tap the **Delete** icon in the top-right corner to clear all notifications from this screen.
Use the drop-down menu to filter the notifications by the predefined time frames. You can view notifications from **Today**, the **Last 7 Days**, the **Last 10 Days**, or view **All** notifications.
![The Notifications screen of Zscaler Client Connector for Chrome OS](/downloads/tech-pubs-drafts/client-connector-draft-articles/viewing-notifications-zscaler-client-connector-doc-55419/client-connector-notifications-android.png)
[]To display notifications on the app icon:
- Tap **More**.
- In the **Settings** section, you can:
- Manually enable or disable menu bar notifications. The default setting is set by the admin. If notifications are enabled, you see notifications on the app icon.
- Override the default setting that was configured in the Zscaler Client Connector Portal to enable or disable ZPA reauthentication notifications.
![Notification screen on Zscaler Client Connector for Chrome OS](/downloads/tech-pubs-drafts/client-connector-draft-articles/viewing-notifications-zscaler-client-connector-doc-55419/ChromeOS_More_Settings_Notifications.png)
[]This section covers the following topics:
- [Viewing Notifications on iOS](#ios-notification)
- [Enabling Notifications on the App Icon](#enable-notification-ios)
[]In the Notifications screen, you can view the following information:
- The name of the application relevant to the action that triggered it. In the following example, **Zscaler Client Connector Private Access** is listed because the notification was relevant only to Zscaler Client Connector. For example, you received the notification after the app’s Zscaler Internet Access (ZIA) service was turned on. For example, if you attempted to upload content to Dropbox.com in violation of one of your organization’s cloud app control policies, you would receive a notification and see Dropbox.com listed.
- The notification message and the time when it was received.
Tap the **Delete** icon in the top-right corner to clear all notifications from this screen.
![Enabling Zscaler Client Connector for iOS to show app icon notifications](/downloads/client-connector/end-user-guide/viewing-notifications-zscaler-client-connector/zscaler-client-connector-notifications-ios.png)
[]To display notifications on the app icon:
- Tap **More**.
- In the **Settings** section, you can enable or disable app icon notifications.
![Enabling Zscaler Client Connector for iOS to show app icon notifications](/downloads/client-connector/end-user-guide/viewing-notifications-zscaler-client-connector/zscaler-client-connector-notificationsettings-ios.png)