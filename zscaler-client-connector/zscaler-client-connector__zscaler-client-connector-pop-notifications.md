# Zscaler Client Connector: Pop-Up Notifications
Source: https://help.zscaler.com/zscaler-client-connector/zscaler-client-connector-pop-notifications
PDF: https://help.zscaler.com/pdf/com/en/1506376.pdf

The following table provides a list of pop-up notifications for Zscaler Client Connector.
This list applies only to Zscaler Client Connector version 4.4 and later for Windows and for Zscaler Client Connector version 4.3 and later for macOS.
There are 6 types of notifications:
- **Default**: General notifications about Zscaler Client Connector.
- **Service Status**: Notifications about the status of a Zscaler service, such as when a service is in Disaster Recovery mode.
- **App Updates**: Notifications about the upgrade process for Zscaler Client Connector.
- **ZIA Notifications**: Notifications from Zscaler Internet Access (ZIA), such as Data Loss Prevention (DLP) or device posture.
- **ZPA Reauthentication**: Notifications that users must reauthenticate Zscaler Private Access (ZPA).
- **Critical:** Notifications that display regardless of end user notification configuration. These notifications cannot be turned off.
The types of notifications that display are based on the end user notifications configuration in the Zscaler Client Connector Portal. Users can disable or pause notifications. To learn more, see [Configuring End User Notifications for Zscaler Client Connector](/zscaler-client-connector/configuring-end-user-notifications-zscaler-client-connector) and [Viewing Notifications on Zscaler Client Connector](/zscaler-client-connector/viewing-notifications-zscaler-client-connector).
If a customizable [Strict Enforcement Notification](/zscaler-client-connector/configuring-fail-open-settings-zscaler-client-connector) is configured, an additional notification is displayed if users try to access the internet before enrolling in Zscaler Client Connector.
| Component | Notification Type | Notification Message | User Action | Notes |
| --------- | ----------------- | -------------------- | ----------- | ----- |
| ZPA | ZPA Reauthentication | Access to all or certain private applications will expire soon. Reauthenticate before your access expires. | Click **Authenticate Early** on the Private Access window to avoid losing access. |  |
| ZPA | ZPA Reauthentication | Access to certain applications requires you to reauthenticate into Zscaler Client Connector. | Click **Authenticate** on the Private Access window. |  |
| General | App Updates | App has been updated. | None required. |  |
| ZPA | Default | Application access is blocked by Private Access policy. | Contact your organization’s support admin. | Usually indicates a posture block. Customize this message in the ZPA Admin Portal. |
| General | Critical | Captive Portal detected. Please resolve it to access the internet. | Click **Open Browser** to access the internet. |  |
| ZDX | Default | Digital Experience is Enabled as per latest policy. Login again to register with Digital Experience. | Log out of the app and log back in again. |  |
| ZIA | ZIA Notification | Data Loss Protection | Click **Learn More** to view a report of the violation. | Customize this message in the ZIA Admin Portal. |
| General | App Updates | Failed to check for updates. Please try again after some time. | Retry the action later. |  |
| General | App Updates | Failed to check for ZDP updates. Please try again after some time. | Retry the action later. |  |
| General | App Updates | Failed to check for ZDX updates. Please try again after some time. | Retry the action later. |  |
| General | Default | Failed to report issue. | None required. |  |
| General | Critical | Finished capturing packets. | None required. |  |
| ZIA | Service Status | Internet Security is Connected. | None required. | Duplicate messages that display within a 1-minute interval are suppressed. |
| ZIA | Service Status | Internet Security is Disconnected. | None required. | Duplicate messages that display within a 1-minute interval are suppressed. |
| ZIA | Service Status | Internet Security is Enabled as per latest policy. Log in again to register with Internet Security. | Log out of the app and log back in again. |  |
| ZIA | Default | Internet Security is in Driver Error. | Click **Restart Service** on the More window. | Zscaler Client Connector experienced an error after you clicked **Repair App** on the More window. |
| Disaster Recovery | Service Status | Internet Security Safe Mode has started. (Your access to the internet will be limited.) | None required. | Duplicate messages that display within a 12-hour interval are suppressed. |
| Disaster Recovery | Service Status | Internet Security Safe Mode has stopped. | None required. |  |
| General | Default | Issue reported. | None required. |  |
| General | App Updates | Latest available app is already running. | None required. |  |
| General | App Updates | New update is available. App will auto-update now. | None required. |  |
| ZPA | Service Status | Partner Private Access is Connected. | None required. | Duplicate messages that display within a 1-minute interval are suppressed. |
| ZPA | Service Status | Partner Private Access is Disconnected. | None required. | Duplicate messages that display within a 1-minute interval are suppressed. |
| General | Default | Please restart the system for driver repair to complete. | Click **Restart Service** on the More window. |  |
| ZPA | Service Status | Private Access is Connected. | None required. | Duplicate messages that display within a 1-minute interval are suppressed. |
| ZPA | Critical | Private Access is Connected. (Business Continuity mode) | None required. |  |
| ZPA | Critical | Private Access is Connected. (Exited Business Continuity mode) | None required. |  |
| ZPA | Service Status | Private Access is Disconnected. | None required. | Duplicate messages that display within a 1-minute interval are suppressed. |
| ZPA | Default | Private Access is in Driver Error. | Click **Restart Service** on the More window. | Zscaler Client Connector experienced an error after you clicked **Repair App** on the More window. |
| Disaster Recovery | Service Status | Private Access Safe Mode has started. (Your access to the internet will be limited). | None required. | Duplicate messages that display within a 12-hour interval are suppressed. |
| General | Service Status | Service has been administratively disabled. | None required. |  |
| General | Service Status | Services are down because the network is disconnected. | None required. |  |
| General | Critical | Started capturing packets. | None required |  |
| General | Default | The SSL certificate could not be trusted automatically. Please trust the certificate from the keychain. | None required. | Applies to macOS only. |