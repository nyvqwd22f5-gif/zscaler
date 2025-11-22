# Downloading Decoy Connector Debug Logs
Source: https://help.zscaler.com/deception/downloading-decoy-connector-debug-logs
PDF: https://help.zscaler.com/pdf/com/en/1531260.pdf

Debug logs are system-generated logs that are stored on a Decoy Connector. Debug logs are copied to the Zscaler Deception Admin Portal when you initiate a download request. The logs contain timestamps and messages that help you troubleshoot any issues with network decoys or other integrations that use Decoy Connectors.
For a Decoy Connector, you can download either the most recent or all debug logs.
Make sure that the Decoy Connector is connected to the Deception Admin Portal before you download the debug logs.
To download debug logs:
- Log in to the Deception Admin Portal.
- Go to **Settings** > **Topology** > **Decoy Connectors**.
- Select a Decoy Connector for which you want to download the debug logs, and then click **Logs**.
-
Select an option from the **Logs** drop-down menu:
- **Request recent debug logs**: Download the last 1,000 lines from each log file.
- **Request all debug logs**: Download the complete log files.
[See image.](#debug-logs-option)
- After the download logs request is initiated and completed, click **Download debug logs**.
-
In the **Debug Logs** window, click the **Download** icon.
The debug logs are downloaded. The debug log files are formatted in a .tar.xz file. Extract the file using a file compression tool (e.g., WinZip, 7-zip, etc.).
[See image.](#download-debug-logs)
- Click **Close**.
If the debug log files consume a large amount of disk space, you can periodically delete them. Click the **Delete** icon to delete the logs from the Deception Admin Portal.
[See image.](#delete-debug-logs)
[]![Request debug logs options](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-management/downloading-decoy-connector-debug-logs/zscaler-deception-logs-dc.png)
[]![Download debug logs](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-management/downloading-decoy-connector-debug-logs/zscaler-deception-edit-log.png)
[]![Delete debug logs](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-management/downloading-decoy-connector-debug-logs/zscaler-deception-delete-log.png)