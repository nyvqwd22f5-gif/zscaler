# Accessing ZPA Private Service Edge Status Diagnostics
Source: https://help.zscaler.com/zpa/accessing-zpa-service-edge-status-diagnostics
PDF: https://help.zscaler.com/pdf/com/en/1484516.pdf

You can view and filter ZPA Private Service Edge status data for past events.
Viewing Private Service Edge Status Diagnostics
To view diagnostics for ZPA Private Service Edge status:
- Go to **Analytics **> **Diagnostics**.
- Under **Log Type**, choose **Private Service Edge Status**.
By default, the detailed status and activity information for all ZPA Private Service Edges are displayed for events that occurred in the last 24 hours. You can do the following:
- Click the **Calendar **drop-down menu to select a preset range or specify a custom start and end date. If you use a **Custom Range**, the start date must be within the last 14 days.
- Click the **Time Zone** icon to change the time zone.
- Click the **Settings** icon to configure the [diagnostics settings](#settings).
Zscaler retains logs for rolling periods of at least 14 days during the subscription term. You can also view your logs or stream logs in real time using the [Log Streaming Service (LSS)](/zpa/about-log-streaming). The data in the [dashboard](/zpa/dashboard-diagnostics) might be more recent than the data presented within Diagnostics.
![Private Service Edge log type](/downloads/zpa/dashboard-diagnostics/about-zpa-service-edge-status-diagnostics/zpa-privateserviceedgestatus-logtypetimerange_0.png)
Also, by default, the table displays the **Total** number of ZPA Private Service Edge requests. You can change this by choosing one of the following filters:
- **Errors**: The total number of ZPA Private Service Edge access errors.
- **Successful**: The total number of successful ZPA Private Service Edge requests.
![Private Service Edge status totals ](/downloads/zpa/dashboard-diagnostics/about-zpa-service-edge-status-diagnostics/zpa-privateserviceedgestatus-totals_0.png)
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
Filtering Private Service Edge Status Diagnostics
After choosing the ZPA Private Service Edge Status log type, you can apply filters or drill down further into the log data using the Query Builder. By default, no filters are applied. If you want to view and filter ZPA Private Service Edge Status for real-time events, use [Live Logs](/zpa/accessing-live-logs).
To configure filters using the Query Builder:
- Click **Add Filters **and select a filter from the drop-down menu. To learn more, see [Status Filters](#filters).
- Select a Boolean operator from the drop-down menu (e.g., **Contains**, **Ends With**, **Equals**, **Not Equals**, **Starts With**). The operators available are determined by the filter you are configuring.
- Select the fields from the drop-down menu or enter the values required for the filter. The field or value required is determined by the filter you are configuring.
Filters using the **Contains **operator allow a maximum of 7 entries. All filters using operators that require text input must use a semicolon (;) to separate multiple entries (e.g., 137; 138; 139). When configuring multiple text entries and using the **Less Than** operator, the results show transactions starting from the largest entry provided. When configuring multiple text entries and using the **Greater Than** operator, the results show transactions starting from the smallest entry provided.
- Click **Apply**.
![Apply filters](/downloads/zpa/dashboard-diagnostics/about-zpa-service-edge-status-diagnostics/zpa-privateserviceedgestatus-filterexample.png)
To apply more filters, click **Add Filters** again or click on the **Filter **icon (![Filter icon ](/downloads/zpa/dashboard-diagnostics/private-service-edge-monitoring/accessing-zpa-service-edge-status-diagnostics/zpa-show-hide-filter-icon.png)
) within the table. To remove an added filter, click the **Close** icon** **then click **Apply**. To remove all filters, click **Clear All**.
You can also click the **Copy** icon** **to save the filter query details. If you or another ZPA admin accesses **Diagnostics**, you can paste the query into the field by clicking the **Clipboard** icon.
[See image.](#copypaste)
[]Status Filters
You can add the following filters:
- **Connection: Status Code**: See logs with **Authenticated**, **Authentication Failed**, or **Disconnected **connections.
- **Private Service Edge: Connection Type**: See logs for a specific ZPA Private Service Edge connection type.
- **Private Service Edge​: Name**: See logs for a specific ZPA Private Service Edge you've configured.
- **Private Cloud Controller: Name**: See logs for a specific Private Cloud Controller.
- **Service Edge: Name**: See logs for a specific ZPA Public Service Edge.
- **Service Edge​​: Private IP Address**: See logs for a ZPA Private Service Edge's private IP address, which is the internal IP address configured for the Private Service Edge.
- **Service Edge​​​​​: Public IP Address**: See logs for a ZPA Private Service Edge's public IP address, which is used to reach out to ZPA.
The table displays the following data about ZPA Private Service Edge status and activity. You can expand each row to see more details, or click the **Expand**/**Collapse** icon to expand or collapse all rows within the table. By default, the table displays 20 transactions. You can scroll to load more transactions.
- [Session](#status)
- [Auth Log Timestamp](#authlog)
- [Authentication Time](#authentication)
- [Disconnect Time](#disconnect)
- [Name](#name)
- [Private Cloud Controller](#privateCloudController)
- [Service Edge](#se)
Within the table, you can click the **Filter **icon next to certain field names to drill down further into the data. The filter query section within the page updates automatically to include the proper filter for the field name you selected, along with the applicable Boolean operator configuration for that field.
[]Displays one of the following session status codes:
- **Authenticated**: The ZPA Private Service Edge successfully authenticated to the Zscaler cloud.
- **Authentication Failed**: The ZPA Private Service Edge was unable to authenticate to the Zscaler cloud.
- **Disconnected**: The ZPA Private Service Edge successfully disconnected from the Zscaler cloud.
For every session status code, the following fields are displayed:
- **Session ID**: The ID associated with the session.
- **Connection Type**: The type of connection the ZPA Private Service Edge makes. The different connection types are:
- Service Edge Control Connection
- Service Edge Log Connection
- Private Cloud Controller Control Connection
- **Service Edge Version**: The version number of the ZPA Private Service Edge.
- **Connection Status Log**: View, download, and copy the raw JSON for the request:
- Click the **View Log** icon to display the **Raw JSON** for the request within the ZPA Admin Portal.
- Click the **Download** icon to download the raw JSON for the request to a text (.txt) file.
- Click the **Copy **icon to copy the raw JSON text for the request to your clipboard.
[]The data and time when the log was generated. The column sorts requests by the date and start time in descending order. You can click the arrow icon to sort the requests in ascending order.
The time displayed is based on the time you choose for [your account setting](/zpa/about-zpa-admin-portal#username) in the ZPA Admin Portal.
[]The time the ZPA Private Service Edge authenticated to the Zscaler cloud. The column initially sorts requests based on the **Auth Log Timestamp** column date and time. You can click the arrow icon to sort the table in ascending or descending order based on this column.
[]The time that the ZPA Private Service Edge disconnected from the Zscaler cloud. The column initially sorts requests based on the **Auth Log Timestamp** column date and time. You can click the arrow icon to sort the table in ascending or descending order based on this column.
- []**Service Edge Name**: The name of the ZPA Private Service Edge used to process the connection between the user and the App Connector. You can click on the name to open the [Edit Service Edge](/zpa/editing-deployed-service-edge) window.
- **Service Edge ID**: The internal ID (created by ZPA) for the connection request to the application. You can click the **Copy** icon to copy the ID to your clipboard.
- **Public IP**: The IP address used by the ZPA Private Service Edge to connect to ZPA.
- **Private IP**: The internal IP address configured for the ZPA Private Service Edge.
- **Location**: The city and country where the ZPA Private Service Edge is located.
- **Service Edge Group Name**: The name of the group the ZPA Private Service Edge is included in. You can click on the name to open the [Edit Service Edge Group](/zpa/editing-service-edge-groups) window.
- **Service Edge Group ID**: The internal ID (created by ZPA) for the ZPA Private Service Edge group. You can click the **Copy **icon to copy the ID to your clipboard.
- []**Private Cloud Controller Name**: The name of the Private Cloud Controller.
- **Private Cloud Controller ID**: The ID of the Private Cloud Controller.
- **Private Cloud Controller Group Name**: The name of the Private Cloud Controller group.
- **Private Cloud Controller Group ID**: The ID of the Private Cloud Controller group.
- []**Name**: The name of the ZPA Public Service Edge.
- **Location**: The city or country where the ZPA Public Service Edge is located.
[]![Copy and paste filter options](/downloads/zpa/dashboard-diagnostics/about-zpa-service-edge-status-diagnostics/zpa-copypaste.png)