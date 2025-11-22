# About Event Logs
Source: https://help.zscaler.com/zia/about-event-logs
PDF: https://help.zscaler.com/pdf/com/en/1403226.pdf

The Event Logs page lists all the recorded SCIM client activity, such as creating, updating, deleting, etc. user or group accounts in the ZIA Admin Portal. This page also displays the SCIM client's logs (timestamps, error codes, status codes, etc.) and any configuration changes made by them.
The SCIM client's activities are recorded only if the SCIM-based provisioning is enabled for users on the Zscaler service. Additionally, only one SCIM log is audited per day for wrong domain errors.
Event logs provide the following benefits and enable you to:
- View and download all recorded SCIM client activity.
- Search for and filter logs by a variety of criteria.
About the Event Logs Page
On the Event Logs page (Administration > Event Logs), you can do the following:
-
Filter by time range, category, sub-category, and result.
The Time Range filter allows you to filter the event logs for a specified time range within the last 14 days.
- Search for an event log by message, error code, or status code.
- Download a CSV file. The times in the CSV file are in PDT.
- View a list of SCIM events. For each event, you can see:
- **Timestamp**: The local time of the SCIM client's last activity or action.
- **Category**: The category where the action is performed (i.e., Provisioning).
- **Sub-Category**: The sub-category where the action is performed (i.e., SCIM).
- **Message**: The action performed by the SCIM client.
- **Result**: The outcome of the action.
- If the action is a success, a green circle with a checkmark inside is displayed.
- If the action is a failure, a red circle with an X inside is displayed.
- **Error Code**: The error code that occurred during the action.
- **Status Code**: The status code corresponding to the result of the action.
- [Modify the table and its columns.](/zia/how-do-i-use-tables-admin-portal)
- See configuration changes. You can view the differences between the pre-configuration and post-configuration changes.
![The Events Logs page in ZIA Admin Portal](/downloads/zia/authentication-administration/administrator-role-management/about-event-logs/zia-about-event-logs.png)