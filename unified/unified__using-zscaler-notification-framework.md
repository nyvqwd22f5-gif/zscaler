# Using the Zscaler Notification Framework
Source: https://help.zscaler.com/unified/using-zscaler-notification-framework
PDF: https://help.zscaler.com/pdf/com/en/1491896.pdf

This article provides an overview of the Zscaler Notification Framework that, when enabled, overrides the Windows-based and macOS-based notification systems. Only Administrators can enable and disable the Zscaler Notification Framework in the Admin Portal.
This feature is only available for Zscaler Client Connector for Windows version 3.8 and later and for macOS version 4.1 and later.
Zscaler notifications display in the bottom right corner of the screen. Up to 5 notifications can appear and time out after 5 seconds. You can move and dismiss these notifications by clicking anywhere on the window. You can also view these notifications in the Zscaler Client Connector Notifications window.
This notification framework limits duplicate messages. Duplicate messages that display within a 2-minute interval are suppressed.
Enabling the Zscaler Notification Framework
This feature is required for Data Loss Prevention (DLP) notifications.
- [Windows](#windows)
- [macOS](#macOS)
[]To enable the Zscaler Notification Framework on Windows devices:
- In the Admin Portal, go to **Infrastructure > Connectors > Client.**
- Under Platform Settings, select **Windows** and click **Add Windows Policy**.
- Enable **Use Zscaler Notification Framework**.
- Click **Save**.
![Use Zscaler Notifications Framework switch](/downloads/unified/administration/client-connector/identity/zscaler-client-connector-notifications/using-zscaler-notification-framework/clientconnector-windows-notification-framework.png)
[]To enable the Zscaler Notification Framework on macOS devices:
- In the Admin Portal, go to **Infrastructure > Connectors > Client.**
- Under Platform Settings, select **macOS** and click **Add macOS Policy**.
- Enable **Use Zscaler Notification Framework**.
- Click **Save**.
![Enable Zscaler Notification Framework on macOS devices in App Profiles](/downloads/unified/administration/client-connector/identity/zscaler-client-connector-notifications/using-zscaler-notification-framework/clientconnector-macOS-notification-framework.png)