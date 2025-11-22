# Troubleshooting Zscaler Client Connector
Source: https://help.zscaler.com/zscaler-client-connector/troubleshooting-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1364391.pdf

This article details the **Troubleshoot** section features of Zscaler Client Connector on different OSs:
- [Windows](#win)
- [macOS](#macos)
- [Linux](#Linux)
- [Android](#android)
- [Android on ChromeOS](#chrome)
- [iOS](#ios)
[]The **Troubleshoot** section includes the following features on Windows devices:
![The Troubleshoot menu features of Zscaler Client Connector for Windows](/downloads/zscaler-client-connector/end-user-guide/troubleshooting-zscaler-client-connector/Export_Logs_Zapp_Windows.png)
- **Start Packet Capture: **If your organization's admin enabled packet captures, use this feature when reproducing an issue. To modify the settings for Start Packet Capture, see [Enabling Packet Capture for Zscaler Client Connector](/zscaler-client-connector/enabling-packet-capture-zscaler-client-connector).
- **Report an Issue: **If your organization's admin enabled in-app support access, use this feature to report an issue. When you submit the form, depending on your organization's setup, Zscaler Client Connector can send an email to your organization's support admin or submit a ticket directly to Zscaler Support. Your support admin receives a copy of this ticket. After you submit the form, you receive an email acknowledging the support request. For instructions on completing the form, see [Reporting an Issue with Zscaler Client Connector](/zscaler-client-connector/reporting-issue-zscaler-client-connector#win).
- **Export Logs**: Click this option to export logs to a ZIP file, then email that folder to your organization’s support admin.
- **Restart Service: **Click to restart the app. Restarting does not impact security enforcement.
- **Repair App: **If you select this option, the app attempts to repair itself by reinstalling app drivers and services. Zscaler recommends trying this option before reporting an issue.
- **Revert App:** If your organization’s admin enabled the revert option, click this option to revert to the previous version of Zscaler Client Connector. Depending on your organization’s policies, you might be required to enter a password.
- **Disable Tamper Protection**: Click this option to disable anti-tampering protection. When prompted, provide the [Disable Anti-Tampering OTP](/zscaler-client-connector/viewing-device-fingerprint-enrolled-device). To learn more, see [Anti-Tampering for Zscaler Client Connector](/zscaler-client-connector/anti-tampering-zscaler-client-connector).
- **Clear Logs: **Click this option to clear stored logs.
-
**Log Mode: **Change the mode in which Zscaler Client Connector generates logs. The change is effective for that connection session only. At the start of the next connection session, the app returns to the default log mode set by your organization. The following is a description of each log mode.
- **Error: **Logs only when the app encounters an error and functionality is affected.
- **Warn: **Logs when the app is functioning but is encountering potential issues, or logs when conditions for the Error log mode are met.
- **Info: **Logs general app activity, or logs when conditions for the Warn log mode are met.
- **Debug:** Logs all app activity that could assist Zscaler Support in debugging issues, or logs when conditions for the Info log mode are met.
To see where the logs are stored, click **Report an Issue** and** **then click **Show/Hide logs**. To learn more, see [Reporting an Issue with Zscaler Client Connector](/zscaler-client-connector/reporting-issue-zscaler-client-connector#win).
[]The **Troubleshoot** section includes the following features on macOS devices:
![The Troubleshoot menu features of Zscaler Client Connector for macOS](/downloads/zscaler-client-connector/end-user-guide/troubleshooting-zscaler-client-connector/troubleshoot-macos_0.png)
- **Start Packet Capture: **If your organization's admin enabled packet captures, use this feature when reproducing an issue. For instructions on using this option, see [Using the Start Packet Capture Option](/zscaler-client-connector/enabling-packet-capture-zscaler-app#using-start-packet-capture).
- **Report an Issue**:** **If your organization's admin enabled in-app support access, use this feature to report an issue. When you submit the form, depending on your organization's setup, Zscaler Client Connector can send an email to your organization's support admin or submit a ticket directly to Zscaler Support. Your support admin receives a copy of this ticket. After you submit the form, you receive an email acknowledging the support request. For instructions on completing the form, see [Reporting an Issue with Zscaler Client Connector](/zscaler-client-connector/reporting-issue-zscaler-client-connector#win).
- **Restart Service**:** **Click to restart the app. Restarting does not impact security enforcement.
- **Revert App:** If your organization’s admin enabled the revert option, click this option to revert to the previous version of Zscaler Client Connector. Depending on your organization’s policies, you might be required to enter a password.
- **Clear Logs**:** **Click this option to clear stored logs.
- **Log Mode**:** **Change the mode in which Zscaler Client Connector generates logs. The change is effective for that connection session only. At the start of the next connection session, the app returns to the default log mode set by your organization. The following is a description of each log mode.
- **Error**:** **Logs only when the app encounters an error and functionality is affected.
- **Warn**:** **Logs when the app is functioning but is encountering potential issues, or logs when conditions for the Error log mode are met.
- **Info**:** **Logs general app activity, or logs when conditions for the Warn log mode are met.
- **Debug**: Logs all app activity that could assist Zscaler Support in debugging issues, or logs when conditions for the Info log mode are met.
- **Run Zscaler Diagnostics**: Provides a one-time snapshot of the system's network state by performing various diagnostic tests. To run diagnostics using CLI, see [Interacting with Zscaler Client Connector Remotely](/zscaler-client-connector/interacting-zscaler-client-connector-remotely).
- **Export Logs**: Click this option to export logs to a ZIP file, then email that folder to your organization’s support admin.
[]The **Troubleshoot** section includes the following features on Android devices:
![Troubleshooting Options on Zscaler Client Connector for Android](/downloads/tech-pubs-drafts/client-connector-draft-articles/troubleshooting-zscaler-client-connector-doc-55419/Troubleshooting_Android.jpg)
- **Packet Capture: **If your organization's admin enabled packet captures, use this feature when reproducing an issue. For instructions on using this option, see [Using the Start Packet Capture Option](/zscaler-client-connector/enabling-packet-capture-zscaler-app#using-start-packet-capture).
- **Report an Issue**: If your organization’s admin enabled in-app support access, use this feature to report an issue. When you submit the form, depending on your organization's setup, Zscaler Client Connector can send an email to your organization's support admin or submit a ticket directly to Zscaler Support. Your support admin receives a copy of this ticket. After you submit the form, you receive an email acknowledging the support request. For instructions on completing the form, see [Reporting an Issue with Zscaler Client Connector](/zscaler-client-connector/reporting-issue-zscaler-client-connector#win).
- **Restart Service**: Tap this option to restart the app. Restarting does not impact security enforcement. However, you can click **Restart Service** only once within a 30-second period.
- **Clear Logs**: Tap this option to clear stored logs.
- **Export Logs**: Tap this option to export logs to a ZIP file, then email that file to your organization’s support admin.
- **Log Mode**: Change the mode in which the app generates logs. The change is effective for that connection session only. At the start of the next connection session, the app returns to the default log mode set by your organization. The following is a description of each log mode.
- **Error**: Logs only when the app encounters an error and functionality is affected.
- **Warn**: Logs when the app is functioning but is encountering potential issues or when conditions for the Error log mode are met.
- **Info**: Logs general app activity or when conditions for the Warn log mode are met.
- **Debug**: Logs all app activity that could assist Zscaler Support in debugging issues or when conditions for the info log mode are met.
- **Verbose**: Logs when invoked by some external events (e.g., Firebase Push Notification or Mobile Manager flags).
[]The **Troubleshoot** section includes the following features on Android on ChromeOS devices:
![Troubleshooting Options on Zscaler Client Connector for Chrome OS](/downloads/tech-pubs-drafts/client-connector-draft-articles/troubleshooting-zscaler-client-connector-doc-55419/ChromeOS_Troubleshooting.png)
- **Packet Capture: **If your organization's admin enabled packet captures, use this feature when reproducing an issue. For instructions on using this option, see [Using the Start Packet Capture Option](/zscaler-client-connector/enabling-packet-capture-zscaler-app#using-start-packet-capture).
- **Report an Issue**: If your organization’s admin enabled in-app support access, use this feature to report an issue. When you submit the form, depending on your organization's setup, Zscaler Client Connector can send an email to your organization's support admin or submit a ticket directly to Zscaler Support. Your support admin receives a copy of this ticket. After you submit the form, you receive an email acknowledging the support request. For instructions on completing the form, see [Reporting an Issue with Zscaler Client Connector](/zscaler-client-connector/reporting-issue-zscaler-client-connector#win).
- **Restart Service**: Tap this option to restart the app. Restarting does not impact security enforcement. However, you can click **Restart Service** only once within a 30-second period.
- **Clear Logs**: Tap this option to clear stored logs.
- **Export Logs**: Tap this option to export logs to a ZIP file, then email that file to your organization’s support admin.
- **Log Mode**: Change the mode in which the app generates logs. The change is effective for that connection session only. At the start of the next connection session, the app returns to the default log mode set by your organization. The following is a description of each log mode.
- **Error**: Logs only when the app encounters an error and functionality is affected.
- **Warn**: Logs when the app is functioning but is encountering potential issues or when conditions for the Error log mode are met.
- **Info**: Logs general app activity or when conditions for the Warn log mode are met.
- **Debug**: Logs all app activity that could assist Zscaler Support in debugging issues or when conditions for the info log mode are met.
[]The **Troubleshoot** section includes the following features on iOS devices:
![The Troubleshoot Option on Zscaler Client Connector for iOS](/downloads/client-connector/end-user-guide/troubleshooting-zscaler-client-connector/zscaler-client-connector-troubleshooting-ios.png)
- **Start Packet Capture: **If your organization's admin enabled packet captures, use this feature when reproducing an issue. For instructions on using this option, see [Using the Start Packet Capture Option](/zscaler-client-connector/enabling-packet-capture-zscaler-app#using-start-packet-capture).
- **Report an Issue**: If your organization’s admin enabled in-app support access, use this feature to report an issue. When you submit the form, depending on your organization's setup, Zscaler Client Connector can send an email to your organization's support admin or submit a ticket directly to Zscaler Support. Your support admin receives a copy of this ticket. After you submit the form, you receive an email acknowledging the support request. For instructions on completing the form, see [Reporting an Issue with Zscaler Client Connector](/zscaler-client-connector/reporting-issue-zscaler-client-connector#win).
- **Restart Service**: Tap this option to restart the app. Restarting does not impact security enforcement.
- **Export Logs**: Tap this option to export logs to a ZIP file, then email that file to your organization’s support admin.
- **Clear Logs**: Tap this option to clear stored logs.
- **Log Level**: Change the mode in which the app generates logs. The change is effective for that connection session only. At the start of the next connection session, the app returns to the default log mode set by your organization. The following is a description of each log mode.
- **Error**: Logs only when the app encounters an error and functionality is affected.
- **Warn**: Logs when the app is functioning but is encountering potential issues or when conditions for the Error log mode are met.
- **Info**: Logs general app activity or when conditions for the Warn log mode are met.
- **Debug**: Logs all app activity that could assist Zscaler Support in debugging issues or when conditions for the info log mode are met.
[]The **Troubleshoot** section includes the following features on Linux devices:
![Zscaler Client Connector More page in Linux highlighting the Troubleshoot section](/downloads/tech-pubs-drafts/client-connector-draft-articles/troubleshooting-zscaler-client-connector-draft-doc-41077/Client%20Connector%20Linux.png)
- **Start Packet Capture: **If your organization's admin enabled packet captures, use this feature when reproducing an issue. For instructions on using this option, see [Using the Start Packet Capture Option](/zscaler-client-connector/enabling-packet-capture-zscaler-app#using-start-packet-capture).
- **Export Logs**: Click this option to export logs to a ZIP file, then email that folder to your organization’s support admin.
- **Restart Service**: Click this option to restart the app. Restarting does not impact security enforcement.
- **Clear Logs**: Click this option to clear stored logs.
- **Log Mode: **Change the mode in which Zscaler Client Connector generates logs. The change is effective for that connection session only. At the start of the next connection session, the app returns to the default log mode set by your organization. The following is a description of each log mode:
- **Error: **Logs only when the app encounters an error and functionality is affected.
- **Warn: **Logs when the app is functioning but is encountering potential issues, or logs when conditions for the Error log mode are met.
- **Info: **Logs general app activity, or logs when conditions for the Warn log mode are met.
- **Debug:** Logs all app activity that could assist Zscaler Support in debugging issues, or logs when conditions for the Info log mode are met.