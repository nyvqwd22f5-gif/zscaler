# Accessing Private Service Edge Status Diagnostics
Source: https://help.zscaler.com/unified/accessing-private-service-edge-status-diagnostics
PDF: https://help.zscaler.com/pdf/com/en/1496296.pdf

Below you can learn about how to view and filter Private Service Edge for Private Applications status data for past events.
To see diagnostics for Private Service Edge for Private Applications status:
- Go to **Logs **> **Insights** > **Diagnostics**.
- Under **Log Type**, choose **Private Service Edge Status**.
By default, the detailed status and activity information for all Private Service Edges for Private Applications are displayed for events that occurred in the last 24 hours. You can change the time range by clicking the **Calendar **menu and selecting a preset range or specify a custom start and end date. If you use a **Custom Range**, the start date must be within the last 14 days. You can also change the time zone by clicking the current **Time Zone** button.
Log information is limited to 14 days. For longer access to the logs, use the [Log Streaming Service (LSS)](/zpa/about-log-streaming).
![Private Service Edge log type](/downloads/zpa/dashboard-diagnostics/about-zpa-service-edge-status-diagnostics/zpa-privateserviceedgestatus-logtypetimerange_0.png)
[Dashboard](/zpa/documentation-knowledgebase/dashboard-diagnostics) data might be more recent than the data presented within Diagnostics.
Also, by default, the table displays the **Total** number of Private Service Edge for Private Applications requests. You can change this by choosing one of the following filters:
- **Errors**: The total number of Private Service Edge for Private Applications access errors.
- **Successful**: The total number of successful Private Service Edge for Private Applications requests.
![Private Service Edge status totals ](/downloads/zpa/dashboard-diagnostics/about-zpa-service-edge-status-diagnostics/zpa-privateserviceedgestatus-totals_0.png)
Filtering Private Service Edge Status Diagnostics
After choosing the Private Service Edge for Private Applications Status log type, you can apply filters or dive further into the log data using the Query Builder. By default, no filters are applied. If you want to view and filter Private Service Edge for Private Applications Status for real-time events, use [Live Logs](/zpa/about-live-logs).
To configure filters using the Query Builder:
- Click **Add Filters **and select a filter from the drop-down menu. To learn more, see [Status Filters](#filters) below.
- Select a Boolean operator from the drop-down menu (e.g., **Contains**, **Ends With**, **Equals**, **Not Equals**, **Starts With**). The operators available are determined by the filter you are configuring.
- Select the fields from the drop-down menu or enter the values required for the filter. The field or value required is determined by the filter you are configuring.
Filters using the **Contains **operator allow a maximum of 7 entries. All filters using operators that require text input must use a semicolon (;) to separate multiple entries (e.g., 137; 138; 139). When configuring multiple text entries and using the **Less Than** operator, the results show transactions starting from the largest entry provided. When configuring multiple text entries and using the **Greater Than** operator, the results show transactions starting from the smallest entry provided.
- Click **Apply**.
![Apply filters](/downloads/zpa/dashboard-diagnostics/about-zpa-service-edge-status-diagnostics/zpa-privateserviceedgestatus-filterexample.png)
To apply more filters, click **Add Filters** again or click on a **Apply Filter **icon within the table. To remove an added filter, click the **Close** icon** **then **Apply**. To remove all filters, click **Clear All**.
You can also click the **Copy** icon** **to save the filter query details. If you, or another admin, accesses **Diagnostics**, you can paste the query into the field by clicking the **Clipboard** icon.
[See image.](#copypaste)
[]Status Filters
You can add the following filters:
- **Connection: Status Code**: See logs with **Authenticated**, **Authentication Failed**, or **Disconnected **connections.
- **Private Service Edge: Connection Type**: See logs for a specific Private Service Edge for Private Applications connection type.
- **Private Service Edge​: Name**: See logs for a specific Private Service Edge for Private Applications you've configured.
- **Service Edge: Name**: See logs for a specific Public Service Edge for Private Applications.
- **Service Edge​​: Private IP Address**: See logs for a Private Service Edge for Private Applications private IP address, which is the internal IP address configured for the Private Service Edge.
- **Service Edge​​​​​: Public IP Address**: See logs for a Private Service Edge for Private Applications public IP address, which is used to reach out to Private Applications.
The table displays the following data about Private Service Edge for Private Applications status and activity. You can expand each row to see more details or click the **Expand**/**Collapse** icon to expand or collapse all rows within the table. By default, the table displays 20 transactions. You can scroll to load more transactions.
- [Session](#status)
- [Auth Log Timestamp](#authlog)
- [Authentication Time](#authentication)
- [Disconnect Time](#disconnect)
- [Name](#name)
- [Service Edge](#se)
Within the table, you can click the **Apply Filter **icon next to certain field names in order to dive further into the data. The filter query section within the page updates automatically to include the proper filter for the field name you selected, along with the applicable Boolean operator configuration for that field.
[]Displays one of the following session status codes:
- **Authenticated**: The Private Service Edge for Private Applications successfully authenticated to the Zscaler cloud.
- **Authentication Failed**: The Private Service Edge for Private Applications was unable to authenticate to the Zscaler cloud.
- **Disconnected**: The Private Service Edge for Private Applications successfully disconnected from the Zscaler cloud.
For every session status code, the following fields are displayed:
- **Session ID**: The ID associated with the session.
- **Connection Type**: The type of connection the Private Service Edge for Private Applications makes. The different connection types are:
- Service Edge Control Connection
- Service Edge Log Connection
- **Service Edge Version**: The version number of the Private Service Edge for Private Applications.
- **Connection Status Log**: View, download, and copy the raw JSON for the request:
- Click the **View Log** icon to display the **Raw JSON** for the request within the Admin Portal.
- Click the **Download** icon to download the raw JSON for the request to a text (.txt) file.
- Click the **Copy **icon to copy the raw JSON text for the request to your clipboard.
[]The data and time when the log was generated. The column sorts requests by the date and start time in descending order. You can click the **Arrow** icon to sort the requests in ascending order.
The time displayed is based on the time you choose for [your account setting](/unified/signing-admin-portal) in the Admin Portal.
[]The time the Private Service Edge for Private Applications authenticated to the Zscaler cloud. The column initially sorts requests based on the **Auth Log Timestamp** column date and time. You can click the **Arrow** icon to sort the table in ascending or descending order based on this column.
[]The time that the Private Service Edge for Private Applications disconnected from the Zscaler cloud. The column initially sorts requests based on the **Auth Log Timestamp** column date and time. You can click the **Arrow** icon to sort the table in ascending or descending order based on this column.
- []**Service Edge Name**: The name of the Private Service Edge for Private Applications used to process the connection between the user and the App Connector. You can click on the name to open the [Edit Service Edge](/unified/editing-private-service-edge-groups-private-applications) window.
- **Service Edge ID**: The internal ID (created by Private Applications) for the connection request to the application. You can click the **Copy** icon to copy the ID to your clipboard.
- **Public IP**: The IP address used by the Private Service Edge for Private Applications to connect.
- **Private IP**: The internal IP address configured for the Private Service Edge for Private Applications.
- **Location**: The city and country where the Private Service Edge for Private Applications is located.
- **Service Edge Group Name**: The name of the group the Private Service Edge for Private Applications is included in. You can click on the name to open the [Edit Service Edge Group](/unified/editing-private-service-edge-groups-private-applications) window.
- **Service Edge Group ID**: The internal ID (created by Private Applications) for the Private Service Edge group for Private Applications. You can click the **Copy **icon to copy the ID to your clipboard.
- []**Name**: The name of the Public Service Edge for Private Applications.
- **Location**: The city or country where the Public Service Edge for Private Applications is located.
[]![Copy and paste filter options](/downloads/zpa/dashboard-diagnostics/about-zpa-service-edge-status-diagnostics/zpa-copypaste.png)