# Using Zscaler Client Connector
Source: https://help.zscaler.com/zscaler-client-connector/using-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1361641.pdf

[Watch a video about Using Zscaler Client Connector.](https://fast.wistia.net/embed/iframe/wf00p384ss)
Overview
Zscaler Client Connector is an application installed on your device to ensure that your internet traffic and access to your organization's internal apps are secure and in compliance with your organization’s policies, even when you're off your corporate network.
No matter where you're accessing the web, Zscaler Client Connector ensures that your traffic is forwarded to and protected by the [Zscaler Internet Access (ZIA)](/zia/understanding-zscaler-cloud-architecture) service. You might also have the following services enabled:
- [Zscaler Private Access (ZPA)](/zpa/what-zscaler-private-access): Securely access your organization's internal resources from any location.
- [Zscaler Digital Experience (ZDX)](/zdx/what-is-zscaler-digital-experience): Perform synthetic probing to a desired Software as a Service (SaaS) application or internet-based service (e.g., OneDrive, Gmail, etc.) to triage and pinpoint the source of performance issues.
- [Zscaler Endpoint Data Loss Prevention (DLP)](/zia/about-endpoint-dlp): Protect your organization from data loss on endpoints.
Zscaler Client Connector is designed to provide a seamless user experience. It automatically recognizes when you are connected to a trusted network (for example, your corporate office network) and depending on your organization's configuration, can disable ZIA, ZPA, ZDX, and Endpoint DLP services accordingly. It can also recognize when you connect to Wi-Fi hotspots (for example, at airports, hotels, and cafés) where you must pay or accept a use policy before connecting. The app disables its services for a period of time and re-enables itself after you've had a chance to complete the steps necessary to connect.
After you log in with your user ID and complete a one-step device enrollment process, you can begin safely connecting to the web and to your organization's internal applications and services with Zscaler Client Connector. To learn more, see [Enrolling in the Zscaler Service on Zscaler Client Connector](/zscaler-client-connector/enrolling-zscaler-service-zscaler-client-connector).
[]Zscaler Client Connector Features
After you enroll with the Zscaler service, you can view the features that are supported on your OS within the Zscaler Client Connector app interface:
- [Windows](#windows)
- [macOS](#macos)
- [Linux](#linux)
- [Android](#android)
- [Android on ChromeOS](#chrome)
- [iOS](#ios)
To learn more about the tasks you can perform with Zscaler Client Connector, see the following articles:
- [Viewing Information About Zscaler Client Connector](/zscaler-client-connector/viewing-information-about-zscaler-client-connector)
- [Viewing Information About Private Access on Zscaler Client Connector](/zscaler-client-connector/viewing-information-about-private-access-zscaler-client-connector)
- [Viewing Information About Internet Security on Zscaler Client Connector](/zscaler-client-connector/viewing-information-about-internet-security-zscaler-client-connector)
- [Viewing Information About Digital Experience on Zscaler Client Connector](/zscaler-client-connector/viewing-information-about-digital-experience-zscaler-client-connector)
- [Viewing Information About Zscaler Endpoint DLP on Zscaler Client Connector](/zscaler-client-connector/viewing-information-about-zscaler-endpoint-dlp-zscaler-client-connector)
- [Viewing Notifications on Zscaler Client Connector](/zscaler-client-connector/viewing-notifications-zscaler-client-connector)
- [Troubleshooting Zscaler Client Connector](/zscaler-client-connector/troubleshooting-zscaler-client-connector)
[]![The features of Zscaler Client Connector for Windows](/downloads/client-connector/end-user-guide/using-zscaler-client-connector/using-zscaler-client-connector-windows.png)
- Click the **Log Out** icon on the top right-side corner to log out of Zscaler Client Connector. You might be required to enter a password your organization's admin has set for the app. If you log out of the app, you must complete enrollment again when you log back in.
- Click the **Minimize** icon to minimize the window without closing it.
- Click the **Maximize** icon to maximize the window.
- Click the **Close** icon to close the window. This does not log you out of the app.
The app displays Zscaler Client Connector's services in the left-side navigation. The previous example shows the services for an organization that has subscribed to the ZPA, ZIA, and ZDX services. If your organization is not subscribed to one of these services, you do not see that option in the left-side navigation.
The app might display in a language other than English based on your system language. To learn more, see [Localization Support](/zscaler-client-connector/localization-support).
Zscaler Client Connector System Tray Icon Options
Zscaler Client Connector displays an icon in the system tray, as shown in the following image:
![Zscaler Client Connector system tray icon](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/zscaler-app-user-guide-windows/what-are-zscaler-app-tray-icon-options-windows/system_tray_icon_screenshot.png)
You can right-click the icon to display the following options:
- **Open Zscaler**: Click to open the app window.
- **Authenticate:** Click to authenticate Zscaler Client Connector without opening the application.
- **Authenticate Early**: Click to reauthenticate before your authentication expires.
- **Register**: Click to complete the device enrollment.
- **Export Logs**: Click to export logs. Logs are saved as a text file on your device.
- **Report an Issue**: If your organization has enabled this option, you can click to report an issue. For instructions on completing the form, see [Reporting an Issue with Zscaler Client Connector for Windows](/zscaler-client-connector/reporting-issue-zscaler-client-connector#win).
- **Exit**: Click to exit the app and disable the Zscaler service. Depending on your organization's policies, you might be required to enter a password configured by your organization's admin.
![Enabling Zscaler Client Connector for Windows to show system tray notifications](/downloads/tech-pubs-drafts/client-connector-draft-articles/using-zscaler-client-connector-DOC-56936/Client-Connector-Windows_Shortcut_Menu.png)
If notifications are enabled, you see notifications in the system tray icon, as shown in the following images. To learn how to enable the system tray notifications, see [Viewing Notifications on Zscaler Client Connector for Windows](/zscaler-client-connector/viewing-notifications-zscaler-client-connector#win).
![Zscaler Client Connector system tray notifications](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/zscaler-app-user-guide-windows/what-are-zscaler-app-tray-icon-options-windows/zscaler-app-tray-notification.png)
[]![The features of Zscaler Client Connector for macOS](/downloads/zia/zia-zapp-about%20%28mac%29.png)
- Click the **Log Out** icon on the top right-side corner to log out of Zscaler Client Connector. You might be required to enter a password your organization's admin has set for the app. If you log out of the app, you must complete enrollment again when you log back in.
- Click the **Minimize** icon to minimize the window without closing it.
- Click the **Maximize** icon to maximize the window.
- Click the **Close** icon to close the window. This does not log you out of the app.
The app displays Zscaler Client Connector's services in the left-side navigation. The previous example shows the services for an organization that has subscribed to the ZPA, ZIA, and ZDX services. If your organization is not subscribed to one of these services, you do not see that option on the left-side navigation.
The app might display in a language other than English based on your system language. To learn more, see [Localization Support](/zscaler-client-connector/localization-support).
Zscaler Client Connector Menu Bar Options
Zscaler Client Connector displays an icon in the menu bar, as shown in the following image.
![Zscaler Client Connector menu bar icon](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/zscaler-app-user-guide-macos/what-are-zscaler-app-menu-bar-options-macos/zscaler_app_menu_bar_icon_screenshot.png)
You can click the icon to display the following options:
- **Open**: Click to open the app window.
- **Export Logs**: Click to export logs. Logs are saved as a text file on your device.
- **Report an Issue**: If your organization has enabled this option, you can click to report an issue. For instructions on completing the form, see [Reporting an Issue with Zscaler Client Connector for macOS](/zscaler-client-connector/reporting-issue-zscaler-client-connector#macos).
- **Exit**: Click to exit the app and disable the Zscaler service. Depending on your organization's policies, you might be required to enter a password configured by your organization's admin.
![Zscaler Client Connector menu bar icon options](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/zscaler-app-user-guide-macos/what-are-zscaler-app-menu-bar-options-macos/zscaler_app_menu_bar_options_screenshot.png)
If notifications are enabled, you see notifications, as shown in the following image. To learn how to enable the menu bar notifications, see [Viewing Notifications on Zscaler Client Connector for macOS](/zscaler-client-connector/viewing-notifications-zscaler-client-connector#macos).
![Zscaler Client Connector menu bar notifications](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/zscaler-app-user-guide-macos/what-are-zscaler-app-menu-bar-options-macos/menu_bar_notification_screenshot.png)
[]![Using Zscaler Client Connector for Linux](/downloads/client-connector/end-user-guide/using-zscaler-client-connector/using-zscaler-client-connector-linux.png)
The Zscaler Client Connector app displays services your organization subscribes to in the left-side navigation and can include ZPA, ZIA, and ZDX. The following image shows that this organization is subscribed to the ZPA and ZIA services.
Navigate the main controls in the app as follows:
- Click the **Minimize **icon to hide the window to your system tray without closing the app.
- Click the **Close **icon to close the window. This does not sign you out of the app. If you click the **Log Out **icon instead of clicking **Close**, you must complete enrollment again when you sign in.
- Click the **Log Out** icon on the top menu bar to log out of Zscaler Client Connector. Enter a password if required.
Zscaler Client Connector displays an icon in the system tray, as shown in the following image. Right-click the Zscaler Client Connector icon to display the following options:
- **Open Zscaler**: Opens the app window.
- **Export Logs**: Exports log files and saves them as text files on your device.
- **Report An Issue**: Your organization must enable this option. For instructions on completing the form, see [Reporting an Issue with Zscaler Client Connector for Linux](/zscaler-client-connector/reporting-issue-zscaler-client-connector#linux).
- **Exit**: Exits the app and disables the Zscaler service. Depending on your organization's policies, you might be required to enter a password configured by your organization's admin.
![task bar icon](/downloads/z-app/end-user-guides/using-zscaler-client-connector/Tray%20icon%20Options.png)
If notifications are enabled, they appear in the system tray icon as shown in the following images.
![status notification on the task bar](/downloads/z-app/end-user-guides/using-zscaler-client-connector/ZIA%20ZPA%20notifications.png?1680141418)
In the Zscaler Client Connector window for Android, you can:
- Tap the **Log Out** icon in the top right-side corner to log out of the app. You might be required to enter a password that your organization’s admin has set for the app. If you log out of the app, you must complete enrollment again when you log back in.
- View Zscaler Client Connector’s services in the menu at the bottom. The following image shows that an organization has subscribed to the ZPA, ZIA, and ZDX services. If your organization has not subscribed to one of these services, that service does not display.
[]![Zscaler Client Connector Features on Android](/downloads/tech-pubs-drafts/client-connector-draft-articles/using-zscaler-client-connector-doc-58262/Using_Zscaler_Android_updated.png)
Zscaler Client Connector Home Screen Icon Options
Zscaler Client Connector displays an icon on the device’s home screen, as shown in the following image:
![Android_icon_home_screen_75.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/using-zscaler-client-connector-DOC-56936/Android_icon_home_screen_75.png)
When authentication expires, the Zscaler Client Connector icon displays with an exclamation point(![Android_auth_expired_25px.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/using-zscaler-client-connector-doc-58262/Android_auth_expired_25px.png)
).
Press and hold the icon to display the following options:
- **Reauthenticate**: This option only displays when your authentication expires. Click to authenticate.
- **Export Logs**: Click to export logs. Logs are saved as a text file on your device.
- **Report an Issue**: If your organization has enabled this option, you can click to report an issue to Zscaler. For instructions on completing the form, see [Reporting an Issue with Zscaler Client Connector for Android](/zscaler-client-connector/reporting-issue-zscaler-client-connector#android).
![Client Connector Android Shortcut Menu](/downloads/tech-pubs-drafts/client-connector-draft-articles/using-zscaler-client-connector-DOC-56936/Client_Connector_Android_shortcut_menu.png)
In the Zscaler Client Connector window for Android on ChromeOS, you can:
- Tap the **Log Out** icon in the top right-side corner to log out of the app. You might be required to enter a password that your organization’s admin has set for the app. If you log out of the app, you must complete enrollment again when you log back in.
- View Zscaler Client Connector's services in the left-side navigation. The following image shows that an organization has subscribed to the ZPA, ZIA, and ZDX services. If your organization has not subscribed to one of these services, that service does not display.
[]![Client Connector Android on ChromeOS ](/downloads/tech-pubs-drafts/client-connector-draft-articles/using-zscaler-client-connector-doc-58262/Using_Zscaler_ChromeOS.png)
Zscaler Client Connector Home Screen Icon Options
Zscaler Client Connector displays an icon on the device’s home screen, as shown in the following image:
![Android_icon_home_screen_75.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/using-zscaler-client-connector-DOC-56936/Android_icon_home_screen_75.png)
When authentication expires, the Zscaler Client Connector icon displays with an exclamation point (![reauthenticate%20icon.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/using-zscaler-client-connector-doc-58262/reauthenticate%20icon.png)
).
Press and hold the icon to display the following options:
- **Reauthenticate**: This option only displays when your authentication expires. Click to authenticate.
- **Export Logs**: Click to export logs. Logs are saved as a text file on your device.
- **Report an Issue**: If your organization has enabled this option, you can click to report an issue to Zscaler. For instructions on completing the form, see [Reporting an Issue with Zscaler Client Connector for Android on ChromeOS](/zscaler-client-connector/reporting-issue-zscaler-client-connector#chrome).
![Client Connector Shortcut Menu Options](/downloads/zscaler-client-connector/end-user-guide/using-zscaler-client-connector/Client_Connector_ChromeOS_shortcut.png)
[]![Zscaler Client Connector Features on iOS](/downloads/z-app/end-user-guides/using-zscaler-client-connector/zscaler-client-connector-features-ios.PNG)
- Tap the **Log Out** icon on the top right-side corner to log out of the app. You might be required to enter a password your organization’s admin has set for the app. If you log out of the app, you must complete enrollment again when you log back in.
- The app displays Zscaler Client Connector’s services in the menu at the bottom. The previous example shows the services for an organization that has subscribed to both the ZPA and ZIA services. If your organization is not subscribed to one of those services, you do not see that option in the bottom menu.