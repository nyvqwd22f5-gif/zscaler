# Configuring User Access to Logging Controls for Zscaler Client Connector
Source: https://help.zscaler.com/unified/configuring-user-access-logging-controls-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1495771.pdf

From the [App Supportability](/unified/about-app-supportability) page, you can configure your users’ access to the logging controls for Zscaler Client Connector. Your users can access these features from the **More **window of the app and the Zscaler Client Connector icon's shortcut menu from the system tray.
For Zscaler Client Connector 2.1.2 or later for Windows and macOS, exported logs aren't encrypted, but logs included in the **Report an Issue** form are encrypted. If you're using a Zscaler Client Connector version earlier than 2.1.2 for Windows or macOS, exported logs are always encrypted and users can't view them.
[See image.](#more-window-tray-icon-image)
About Logging Controls for Users
You can choose to show or hide logging controls for users. If you keep logging controls visible on Zscaler Client Connector, your users can:
-
See where encrypted logs are stored on their devices by clicking **Show/Hide Logs** in the **Report an Issue** form.
[See image.](#encrypted-logs-stored-pt-1)
-
Export logs from the Zscaler Client Connector system tray icon shortcut menu. Upon export, the logs are saved as a ZIP file on the user's device.
[See image.](#export-log-option-pt-2)
- Send encrypted logs to support by email and send a copy of the email to themselves and others. When users request support from the app, an email with encrypted logs is automatically sent to your organization's support admin. If the option is enabled, it's also forwarded to Zscaler Support. An email is also sent to any recipient the user adds to the **CC** field of the **Report an Issue** form. Users cannot view the encrypted logs.
-
Change the log mode in the** More **window of Zscaler Client Connector. Using [App Profiles](/unified/about-zscaler-client-connector-app-profiles), you can determine how the app generates logs. The following log modes are available to users depending on the app profile configuration:
- **Error**: Logs only when the app encounters an error and functionality is affected.
- **Warn**: Logs when the app is functioning but is encountering potential issues, or when conditions for the Error log mode are met.
- **Info**: Logs general app activity, or when conditions for the Warn log mode are met.
- **Debug**: Logs all app activity that could assist Zscaler Support in debugging issues, or when conditions for the Info log mode are met.
- **Verbose**:** **Logs when invoked by some external events (e.g., Firebase Push Notification or Mobile Manager flags). This log mode is only available for Zscaler Client Connector version 1.5 and later for Android.
[See image.](#change-log-mode-pt-4)
-
**Clear logs** from the **More** window of Zscaler Client Connector.
[See image.](#clear-logs-pt-5)
[]![The More window of the Zscaler Client Connector and the tray icon menu](/downloads/z-app/configuring-policy-and-administration-settings/zscaler-app-support-settings/app-supportability/configuring-user-access-logging-controls-zscaler-client-connector/Client-Connector-More-Window-icon-shortcut-menu_3.png)
[]![The Show/Hide Logs option for the Zscaler Client Connector Report an Issue form](/downloads/z-app/configuring-policy-and-administration-settings/zscaler-app-support-settings/app-supportability/configuring-user-access-logging-controls-zscaler-app/show-hide-logs-option_0.png)
[]![The Export Logs option from the Zscaler Client Connector tray icon menu](/downloads/z-app/configuring-policy-and-administration-settings/zscaler-app-support-settings/configuring-user-access-support-and-logging-zscaler-app/export-logs-option.png)
[]![Client-Connector-Verbose-Logging.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-user-access-logging-controls-zscaler-client-connector/Client-Connector-Verbose-Logging.png)
[]![The Clear Logs options for Zscaler Client Connector](/downloads/z-app/configuring-policy-and-administration-settings/zscaler-app-support-settings/configuring-user-access-support-and-logging-zscaler-app/clear-log-options.png)
Configuring User Access to Logging Controls
To configure users' access to logging controls:
- In the Admin Portal, go to **Infrastructure > Connectors > Client > App Supportability**.
-
On the **App Supportability** tab, enable **Hide Logging Controls on Zscaler Client Connector **to block users from using logging controls for Zscaler Client Connector. Disable **Hide Logging Controls on Zscaler Client Connector **to allow users to use logging controls.
[See image.](#hide-logging-controls-zscaler-app-switch)
- Click **Save**.
To learn more about other Zscaler Client Connector Support features, see [About Zscaler Client Connector Support](/unified/about-zscaler-client-connector-support).
[]![The App Supportability tab in Zscaler Client Connector Settings](/downloads/unified/networking/client-connector/configuration/zscaler-client-connector-support-settings/app-supportability/configuring-user-access-logging-controls-zscaler-client-connector/client-connector-configuring-user-access-logging.png)