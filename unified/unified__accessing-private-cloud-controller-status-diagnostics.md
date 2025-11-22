# Accessing Private Cloud Controller Status Diagnostics
Source: https://help.zscaler.com/unified/accessing-private-cloud-controller-status-diagnostics
PDF: https://help.zscaler.com/pdf/com/en/1528766.pdf

You can view and filter Private Cloud Controller status data for past events.
Viewing Private Cloud Controller Status Diagnostics
To view diagnostics for Private Cloud Controllers:
- Go to **Logs **> **Insights **> **Diagnostics**.
- Under **Log Type**, choose **Private Cloud Controller Status**.
By default, the detailed status and activity information for all Private Cloud Controllers is displayed for events that occurred in the last 24 hours. To change the time range, click the **Calendar** menu and select a preset range or specify a custom start and end date. If you use a **Custom Range**, the start date must be within the last 14 days. To change the time zone, click the current **Time Zone** button.
Zscaler retains logs for rolling periods of at least 14 days during the subscription term. You can also view your logs or stream logs in real time using the [Log Streaming Service (LSS)](/unified/about-log-streaming-service). The data in the dashboard might be more recent than the data presented within Diagnostics.
![Time Range for the Private Cloud Controller Diagnostics page](/downloads/zpa/dashboard-diagnostics/accessing-private-cloud-controller-status-diagnostics/zpa-pcc-diagnostics-time-range.jpg)
Also, by default, the table displays the **Total** number of Private Cloud Controller requests. You can change this by choosing one of the following filters:
- **Errors**: The total number of Private Cloud Controller access errors.
- **Successful**: The total number of successful Private Cloud Controller requests.
![Totals for the Private Cloud Controller Status Diagnostics page](/downloads/zpa/dashboard-diagnostics/accessing-private-cloud-controller-status-diagnostics/zpa-pcc-diagnostics-tools.jpg)
Filtering Private Cloud Controller Status Diagnostics
On the Private Cloud Controller Status page, you can apply filters or drill down further into the log data using the Query Builder. By default, no filters are applied.
To configure filters using the Query Builder:
- Click **Add Filters** and select a filter from the drop-down menu. To learn more, see [Private Cloud Controller Status Filters](#filterdata).
- Select a Boolean operator from the drop-down menu (e.g., **Contains**, **Ends With**, **Equals**, **Not Equals**, **Starts With**). The operators available are determined by the filter you are configuring.
- Select the fields from the drop-down menu or enter the values required for the filter. The field or value required is determined by the filter you are configuring.
Filters using the **Contains **operator allow a maximum of 7 entries. All filters using operators that require text input must use a semicolon (;) to separate multiple entries (e.g., 137; 138; 139). When configuring multiple text entries and using the **Less Than** operator, the results show transactions starting from the largest entry provided. When configuring multiple text entries and using the **Greater Than** operator, the results show transactions starting from the smallest entry provided.
- Click **Apply**.
![zpa-connectorstatus-qbexample.png](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/connectorsDiagnostics/zpa-connectorstatus-qbexample.png)
To apply more filters, click **Add Filters** again or click on the **Filter** icon (![zpa-filtericon.png](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/connectorsDiagnostics/zpa-filtericon.png)
) within the table. To remove an added filter, click the **Close **icon then click **Apply**. To remove all filters, click **Clear All**.
You can also click the **Copy **icon to save the filter query details. If you or another admin accesses **Diagnostics**, you can paste the query into the field by clicking the **Clipboard** icon.
[See image.](#QueryBuilder_CopyPaste)
[]Private Cloud Controller Status Filters
You can add the following filters:
- **Connection: Status Code**: See logs with **Authenticated**, **Authentication Failed**, or **Disconnected** connections.
- **Private Cloud Controller: Connection Type**: See logs for a specific Private Cloud Controller connection type.
- **Private Cloud Controller: Name**: See logs for a specific Private Cloud Controller you've configured.
- **Private Cloud Controller: Private IP Address**: See logs for a private Private Cloud Controller IP address, which is the internal IP address configured for the Private Cloud Controller.
- **Private Cloud Controller: Public IP Address**: See logs for a public Private Cloud Controller IP address, which is used to reach out to the Public Service Edge for Private Applications.
- **Service Edge: Name**: See logs for a specific Public Service Edge for Private Applications.
[]The table displays the following data about Private Cloud Controller status and activity. You can expand each row to see more details, or click the **Expand**/**Collapse** icon to expand or collapse all rows within the table. By default, the table displays 20 transactions. You can scroll to load more transactions.
- [Connection Status Code](#status)
- [Auth Log Timestamp](#authlog)
- [Authentication Time](#auth_time)
- [Disconnect Time](#deauth_time)
- [Name](#name)
- [Service Edge](#connection)
Within the table, you can click the** Filter** icon next to certain field names to drill down further into the data. The filter query section within the page updates automatically to include the proper filter for the field name you selected, along with the applicable Boolean operator configuration for that field.
[]Displays one of the following session status codes:
- **Authenticated**: The Private Cloud Controller successfully authenticated.
- **Authentication Failed**: The Private Cloud Controller was unable to authenticate to the Zscaler cloud.
- **Disconnected**: The Private Cloud Controller successfully disconnected.
For every status code, the following fields are displayed:
- **Session ID**: The internal ID associated with the connection.
- **Session Type**: The session type associated with the connection (e.g., **TLS**).
- **Connection Type**: The type of connection the Private Cloud Controller made. The supported connection type is **Private Cloud Controller Control Connection**.
- **Private Cloud Controller Version**: The version number of the Private Cloud Controller.
- **Connection Status Log**: View, download, and copy the raw JSON for the request.
- Click the **View Log **icon to display the raw JSON for the request within the Admin Portal.
- Click the **Download **icon to download the raw JSON for the request to a text (.txt) file.
- Click the **Copy **icon to copy the raw JSON text for the request to your clipboard.
[]The data and time when the log was generated. The column sorts requests by the date and start time in descending order. You can click the arrow icon to sort the requests in ascending order.
The time displayed is based on the time you choose for [your account setting](/unified/signing-admin-portal) in the Admin Portal.
[]The time the Private Cloud Controller authenticated to the Zscaler cloud. The column initially sorts requests based on the **Auth Log Timestamp** column date and time. You can click the arrow icon to sort the table in ascending or descending order based on this column.
[]The time that the Private Cloud Controller disconnected from the Zscaler cloud. The column initially sorts requests based on the **Auth Log Timestamp** column date and time. You can click the arrow icon to sort the table in ascending or descending order based on this column.
- []**Private Cloud Controller Name**: The name of the Private Cloud Controller used to connect the application to the user. You can click on the name to open the [Edit Private Cloud Controller](/unified/editing-deployed-private-cloud-controller) window.
- **Private Cloud Controller ID**: The ID (created by Private Applications) of the Private Cloud Controller. You can click the **Copy** icon to copy the ID to your clipboard.
- **Private Cloud Controller IP**: The IP address used by the Private Cloud Controller.
- **Private IP**: The internal IP address configured for the Private Cloud Controller.
- **Location**: The city and country that the Private Cloud Controller is connecting from.
- **Private Cloud Controller Group Name**: The name of the group the Private Cloud Controller is included in. You can click on the name to open the [Edit Private Cloud Controller Group](/unified/editing-private-cloud-controller-groups) window.
- **Private Cloud Controller Group ID**: The ID (created by Private Applications) for the Private Cloud Controller group. You can click the **Copy** icon to copy the ID to your clipboard.
- []**Name**: The name of the Public Service Edge for Private Applications that processed the connection.
- **Location**: The city or country where the Public Service Edge for Private Applications is located.
[]![zpa-qbcopypaste.png](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/connectorsDiagnostics/zpa-qbcopypaste.png)