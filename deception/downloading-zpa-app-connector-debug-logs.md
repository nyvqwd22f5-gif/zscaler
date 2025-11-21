# Downloading ZPA App Connector Debug Logs
Source: https://help.zscaler.com/deception/downloading-zpa-app-connector-debug-logs
PDF: https://help.zscaler.com/pdf/com/en/1531571.pdf

Debug logs are system-generated logs that are stored on a ZPA App Connector. Debug logs are copied to the Zscaler Deception Admin Portal when you initiate a download request. The logs contain timestamps and messages that help you troubleshoot any issues with network decoys that use App Connectors.
For an App Connector, you can download either the most recent or all debug logs.
Make sure that the App Connector is connected to the Deception Admin Portal before you download the debug logs.
To download debug logs:
- Go to **Settings** > **Topology** > **ZPA App Connectors**.
- Click **Logs **for an App Connector to download the debug logs.
-
Select an option from the **Logs** drop-down menu:
- **Request recent debug logs**: Download the last 1,000 lines from each log file.
- **Request all debug logs**: Download the complete log files.
[See image.](#deception-zpa-app-conn-request-debug-logs)
-
After the download logs request is initiated and completed, click **Download debug logs**.
[See image.](#deception-zpa-app-conn-download-debug-logs)
-
In the **Debug Logs** window, click the **Download** icon.
[See image.](#deception-zpa-app-conn-download-debug-logs-icon)
The debug logs are downloaded and formatted in a .tar.xz file. Extract the file using a file compression tool (e.g., WinZip, 7-zip, etc.).
- Click **Close**.
If the debug log files consume a large amount of disk space, you can periodically delete them. Click the **Delete** icon to delete the logs from the Deception Admin Portal.
[See image.](#deception-zpa-app-connector-conn-delete-logs)
[]![Request ZPA App Connector debug logs](/downloads/deception/settings/topology/zpa-app-connectors/downloading-zpa-app-connector-debug-logs/zscaler-deception-zp-app-con-request-logs.png)
[]![Download ZPA Connector debug logs](/downloads/deception/settings/topology/zpa-app-connectors/downloading-zpa-app-connector-debug-logs/zscaler-deception-zp-app-con-download-logs.png)
[]![Debug logs download icon ](/downloads/deception/settings/topology/zpa-app-connectors/downloading-zpa-app-connector-debug-logs/zscaler-deception-zp-app-con-debug-logs.png)
[]![Delete ZPA App Connector debug logs](/downloads/deception/settings/topology/zpa-app-connectors/downloading-zpa-app-connector-debug-logs/zscaler-deception-zp-app-con-delete-debug-logs.png)