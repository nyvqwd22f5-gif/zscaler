# Email DLP Insights Logs: Columns
Source: https://help.zscaler.com/zia/email-dlp-insights-logs-columns
PDF: https://help.zscaler.com/pdf/com/en/1479356.pdf

You can customize your Email Data Loss Prevention (DLP) logs by using the column fields. To learn more about logs, see [About Insights Logs](/zia/about-insights-logs).
The following are the Email DLP column fields:
- **Application: **The name of the email application.
- **User**: The user who sent the email and is provisioned to ZIA.
- **Triggered Recipients**: The users who received email and a policy action was taken.
- **Other Recipients**: The users who received emails, but no policy was triggered.
- **Rule Name**: The name of the DLP rule that triggered by the activity performed by the user.
- **Tenant**: The name of the email tenant.
- **Subject:** The subject of the email.
- **DLP Identifier**: A unique identifier used to search for the activity. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors.
- **DLP Dictionaries**: Indicates if data leakage was detected by a DLP dictionary.
- **DLP Engine**: Indicates if data leakage was detected by a DLP engine.
- **Severity**: The severity of the activity as per the triggered rule (e.g., Information, Medium, etc.).
- **Action Taken**: The action taken on the user activity per the configured rule.
- **File Name**: The name of the file that was attached with the email. You can click the file name to view attachments that have details such as file name, document type, file size, file type category, and MD5.
- **Mail Sent Time**: The date and time when the email was sent.
- **Scan Time**: The total time taken to perform the scan on the activity in milliseconds..
- **Department**: The department to which the user belongs.
- **Message ID**: The unique email message identifier. Click this field to view details of the recipient, action, rule name, and severity.
- **External User**: The user who sent the email but is not provisioned to ZIA.
- **Record Type**: The event type that was triggered.