# Accessing App Connector Status Diagnostics
Source: https://help.zscaler.com/zpa/accessing-connector-diagnostics
PDF: https://help.zscaler.com/pdf/com/en/1483786.pdf

You can view and filter App Connector status data for past events.
Viewing App Connector Status Diagnostics
To view diagnostics for App Connectors:
- Go to **Analytics** > **Diagnostics**.
- Under **Log Type**, choose **App Connector Status**.
By default, the detailed status and activity information for all App Connectors is displayed for events that occurred in the last 24 hours. You can do the following:
- Click the **Calendar **drop-down menu to select a preset range or specify a custom start and end date. If you use a **Custom Range**, the start date must be within the last 14 days.
- Click the **Time Zone** icon to change the time zone.
- Click the **Settings** icon to configure the [diagnostics settings](#settings).
Zscaler retains logs for rolling periods of at least 14 days during the subscription term. You can also view your logs or stream logs in real time using the [Log Streaming Service (LSS)](/zpa/about-log-streaming). The data in the [dashboard](/zpa/dashboard-diagnostics) might be more recent than the data presented within Diagnostics.
![Time Range for the App Connector Status Diagnostics page](/downloads/zpa/dashboard-diagnostics/app-connector-monitoring/accessing-connector-diagnostics/zpa-app-connector-status-diagnostics-tools.png)
Also, by default, the table displays the **Total** number of App Connector requests. You can change this by choosing one of the following filters:
- **Errors**: The total number of App Connector access errors.
- **Successful**: The total number of successful App Connector requests.
![Totals for the App Connector Status Diagnostics page](/downloads/zpa/dashboard-diagnostics/app-connector-monitoring/accessing-connector-diagnostics/zpa-app-connector-status-diagnostics-tools2.png)
[]Configuring Settings
To configure settings for diagnostics pages in the ZPA Admin Portal:
- Go to **Analytics** > **Diagnostics**.
- Click the **Settings** icon (![Settings icon within the diagnostics pages](/downloads/tech-pubs-drafts/configuring-diagnostics-settings-doc-60060/zpa-diagnostics-settings-icon.png)
).
The **Settings** drawer appears.
-
In the **Settings** drawer, select the default filter operator (i.e., **Equals** or **Contains**) from the** **drop-down menu. The **Default Filter Operator** is set to **Equals** by default.
[See image.](#settingsDrawer)
-
Click **Save** to apply your changes.
The selected filter operator is saved for future sessions.
[]![Settings drawer in the diagnostics pages](/downloads/tech-pubs-drafts/configuring-diagnostics-settings-doc-60060/zpa-diagnostics-settings-drawer.png)
Filtering App Connector Status Diagnostics
On the App Connector Status page, you can apply filters or drill down further into the log data using the Query Builder. By default, no filters are applied. If you want to view and filter App Connector Status for real-time events, use [Live Logs](/zpa/accessing-live-logs).
To configure filters using the Query Builder:
- Click **Add Filters** and select a filter from the drop-down menu. To learn more, see [App Connector Status Filters](#filterdata).
- Select a Boolean operator from the drop-down menu (e.g., **Contains**, **Ends With**, **Equals**, **Not Equals**, **Starts With**). The operators available are determined by the filter you are configuring.
- Select the fields from the drop-down menu or enter the values required for the filter. The field or value required is determined by the filter you are configuring.
Filters using the **Contains **operator allow a maximum of 7 entries. All filters using operators that require text input must use a semicolon (;) to separate multiple entries (e.g., 137; 138; 139). When configuring multiple text entries and using the **Less Than** operator, the results show transactions starting from the largest entry provided. When configuring multiple text entries and using the **Greater Than** operator, the results show transactions starting from the smallest entry provided.
- Click **Apply**.
![zpa-connectorstatus-qbexample.png](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/connectorsDiagnostics/zpa-connectorstatus-qbexample.png)
To apply more filters, click **Add Filters** again or click on the **Filter **icon (![zpa-filtericon.png](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/connectorsDiagnostics/zpa-filtericon.png)
) within the table. To remove an added filter, click the **Close** icon then click **Apply**. To remove all filters, click **Clear All**.
You can also click the **Copy icon** to save the filter query details. If you or another ZPA admin accesses **Diagnostics**, you can paste the query into the field by clicking the **Clipboard** icon.
[See image.](#QueryBuilder_CopyPaste)
[]App Connector Status Filters
You can add the following filters:
- **Connection: Status Code**: See logs with **Authenticated**, **Authentication Failed**, or **Disconnected** connections.
- **App Connector: Connection Type**: See logs for a specific App Connector connection type.
- **App Connector: Name**: See logs for a specific App Connector you've configured.
- **App Connector: Private IP Address**: See logs for a private App Connector IP address, which is the internal IP address configured for the App Connector.
- **App Connector: Public IP Address**: See logs for a public App Connector IP address, which is used to reach out to the ZPA Public Service Edge or ZPA Private Service Edge.
- **Private Cloud Controller: Name**: See logs for a specific Private Cloud Controller.
- **Service Edge: Name (Public/Private)**: See logs for a specific ZPA Public Service Edge or ZPA Private Service Edge.
[]The table displays the following data about App Connector status and activity. You can expand each row to see more details, or click the **Expand**/**Collapse** icon to expand or collapse all rows within the table. By default, the table displays 20 transactions. You can scroll to load more transactions.
- [Session](#status)
- [Auth Log Timestamp](#authlog)
- [Authentication Time](#auth_time)
- [Disconnect Time](#deauth_time)
- [Name](#name)
- [Private Cloud Controller](#privateCloudController)
- [Service Edge](#connection)
Within the table, you can click the **Filter **icon next to certain field names to drill down further into the data. The filter query section within the page updates automatically to include the proper filter for the field name you selected, along with the applicable Boolean operator configuration for that field.
[]Displays one of the following session status codes:
- **Authenticated**: The App Connector successfully authenticated.
- **Authentication Failed**: The App Connector was unable to authenticate to the Zscaler cloud.
- **Disconnected**: The App Connector successfully disconnected.
For every status code, the following fields are displayed:
- **Session ID**: The internal ID associated with the connection.
- **Connection Type**: The type of connection the App Connector made. The different connection types are:
- Control Connection
- Data Connection
- Log Connection
- Service Edge Control Connection
- Stats Connection
- Private Cloud Controller AppProtection Log Connection
- Private Cloud Controller Control Connection
- Private Cloud Controller Stats Connection
- **App Connector Version**: The version number of the App Connector.
- **App Connector Restart Reason**: If the App Connector disconnects and restarts, theApp Connector reason is displayed. If the Unavailable status is displayed, the reason for the restart is not available among the listed restart reasons.
- **Connection Status Log**: View, download, and copy the raw JSON for the request.
- Click the **View Log **icon to display the raw** JSON** for the request within the ZPA Admin Portal.
- Click the **Download **icon to download the raw JSON for the request to a text (.txt) file.
- Click the **Copy **icon to copy the raw JSON text for the request to your clipboard.
[]The data and time when the log was generated. The column sorts requests by the date and start time in descending order. You can click the arrow icon to sort the requests in ascending order.
The time displayed is based on the time you choose for [your account setting](/zpa/about-zpa-admin-portal#username) in the ZPA Admin Portal.
[]The time the App Connector authenticated to the Zscaler cloud. The column initially sorts requests based on the **Auth Log Timestamp** column date and time. You can click the arrow icon to sort the table in ascending or descending order based on this column.
[]The time that the App Connector disconnected from the Zscaler cloud. The column initially sorts requests based on the **Auth Log Timestamp** column date and time. You can click the arrow icon to sort the table in ascending or descending order based on this column.
- []**App Connector Name**: The name of the App Connector used to connect the application to the user. You can click on the name to open the [Edit App Connector](/zpa/about-connector/edit) window.
- **App Connector ID**: The internal ID (created by ZPA) for the connection request to the application. You can click the **Copy **icon to copy the ID to your clipboard.
- **App Connector IP**: The IP address used by the App Connector to connect to the ZPA Public Service Edge or ZPA Private Service Edge.
- **Private IP**: The internal IP address configured for the App Connector.
- **Location**: The city and country that the App Connector is connecting from.
- **App Connector Group Name**: The name of the group the App Connector is included in. You can click on the name to open the [Edit App Connector Group](/zpa/about-connectorgroup/edit) window.
- **App Connector Group ID**: The internal ID (created by ZPA) for the App Connector group. You can click the **Copy **icon to copy the ID to your clipboard.
- []**Private Cloud Controller Name**: The name of the Private Cloud Controller.
- **Private Cloud Controller ID**: The ID of the Private Cloud Controller.
- **Private Cloud Controller Group Name**: The Private Cloud Controller group name.
- **Private Cloud Controller Group ID**: The Private Cloud Controller group ID.
- []**Name**: The name of the ZPA Public Service Edge or ZPA Private Service Edge that processed the connection.
- **Location**: The city or country where the ZPA Public Service Edge or ZPA Private Service Edge is located.
[]![zpa-qbcopypaste.png](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/connectorsDiagnostics/zpa-qbcopypaste.png)