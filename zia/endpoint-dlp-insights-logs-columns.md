# Endpoint DLP Insights Logs: Columns
Source: https://help.zscaler.com/zia/endpoint-dlp-insights-logs-columns
PDF: https://help.zscaler.com/pdf/com/en/1452616.pdf

You can customize your Zscaler Endpoint Data Loss Prevention (DLP) logs by using column fields. To learn more about logs, see [About Insights Logs](/zia/about-insights-logs).
The following are the Endpoint DLP column fields:
- **Action Taken**: The action taken on the user activity per the configured rule.
- **Activity Type**: The type of activity performed by the user (e.g., copy, print, upload, download, etc.).
- **Channel**: The channel through which the activity takes place.
- **Confirm Action**: The action taken by the user when the user is prompted with a confirmation dialog box for the activity, if applicable.
- **Confirm Justification**: The justification provided by the user for the activity.
- **Data Center**: The data center associated with the activity.
- **Department**: The department to which the user belongs. You can sort and search this column.
- **Destination Type**: The destination type for the item associated with the activity (e.g., application, local drive, printer, etc.).
- **Destination Name**: The name of the destination for the item associated with the activity.
- **DLP Dictionaries**: Indicates if data leakage was detected by a DLP dictionary.
- **DLP Engine**: Indicates if data leakage was detected by a DLP engine.
- **DLP Identifier**: A unique identifier used to search for the activity. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors.
- **Document Type**: The type of document uploaded or downloaded during the activity.
- **Event Time**: The date and time of the activity. You can sort this column.
- **File Destination Location**: The source location of the item for the activity.
- **File MD5**: The MD5 hash for the file that triggered the DLP rule. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing the MD5 hash of the file is sent to your auditors.
- **File SHA256**: Displays the hash of identical files.
- **File Size**: The size of the file associated with the activity.
- **File Source Location**: The source location of the item for the activity.
- **File Type Category**: The category of the file associated with the activity.
- **File Type**: The file type associated with the activity.
- **Item Name**: The name of the item associated with the activity.
- **Item Type**: The type of item associated with the activity (e.g., file, email, email attachment, etc.).
- **Logged Time**: The date and time the activity was logged.
- **Other Rules**: The name of any other policy rule that was also triggered by the user activity.
- **Record Type**: The type of activity (i.e., DLP Incident or Sensitive Activity).
- **Rule Name**: The name of the Endpoint DLP rule triggered by the activity performed by the user.
- **Scan Time**: The total time taken to perform the scan on the activity.
- **Severity**: The severity of the activity as per the triggered rule (e.g., Information, Medium, etc.).
- **Source Name**: The name of the source for the item associated with the activity.
- **Source Type**: The source type for the item associated with the activity (e.g., application, local drive, web, etc.).
- **User**: The email address of the user who performed the activity. You can sort and search this column.
- **ZDP Mode**: The Endpoint DLP mode for the activity. When a user enables the exemption mode from the Zscaler Client Connector to bypass the Endpoint DLP policy rules to successfully perform an activity (e.g., copy a file), the ZDP Mode column displays Exemption Mode. When the exemption mode is disabled, the column displays Block Mode.