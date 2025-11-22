# Accessing Protocol Discovery Diagnostics
Source: https://help.zscaler.com/zpa/accessing-protocol-discovery-diagnostics
PDF: https://help.zscaler.com/pdf/com/en/1486016.pdf

You can view and filter Protocol Discovery data for the ports enabled with application segments associated with AppProtection.
Accessing Protocol Discovery Diagnostics
To view diagnostics for Protocol Discovery data:
- Go to **Analytics** > **Diagnostics**.
- Under **Log Type**, choose **Protocol Discovery**.
By default, the detailed activity for all application protocols is displayed for events that occurred in the last 24 hours. You can do the following:
- Click the **Calendar **drop-down menu to select a preset range or specify a custom start and end date. If you use a **Custom Range**, the start date must be within the last 14 days.
- Click the **Time Zone** icon to change the time zone.
- Click the **Settings** icon to configure the [diagnostics settings](#settings).
Zscaler retains logs for rolling periods of at least 14 days during your subscription term. To learn more, see [Customer Logs and Data](/zpa-customer-logs-and-data).
[]![Protocol Discovery Diagnostics Time Range](/downloads/zpa/dashboard-diagnostics/accessing-protocol-discovery-diagnostics/Tools_0.png)
Viewing Logs
Log activity is automatically displayed after selecting the **Protocol Discovery** log type.
By default, the table displays the **Total** number of Protocol Discovery logs generated for domains with application segments that have AppProtection disabled. The logs are generated for domains with relevant protocol traffic (KRB, LDAP, SMB, TLS, and HTTP). You can change this by choosing one of the following filters:
- **TCP**: The total number of Protocol Discovery logs associated with application segments configured for detecting and inspecting traffic with TCP ports.
- **UDP**: The total number of Protocol Discovery logs associated with application segments configured for detecting and inspecting traffic with UDP ports.
[See image.](#logs)
Configuring Settings
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
Filtering Protocol Discovery Logs
On the Protocol Discovery page, you can apply filters or drill down further into the log data using the Query Builder. By default, no filters are applied. If you want to view and filter Protocol Discovery logs for real-time events, use [Live Logs](/zpa/about-live-logs).
To configure filters using the Query Builder:
- Click **Add Filters** and select a filter from the drop-down menu:
- [View query builder filters.](#Query)
- Select an operator from the drop-down menu (e.g., **Contains**, **Ends With**, **Equals**, **Not Equals**, **Starts With**). The operators available are determined by the filter you are configuring.
- Select the fields from the drop-down menu, or enter the values required for the filter. The field or value required is determined by the filter you are configuring.
Filters using the **Contains** operator allow a maximum of 7 entries. All filters using operators that require text input must use a semicolon (;) to separate multiple entries (e.g., `137`; `138`; `139`). When configuring multiple text entries and using the **Less Than** operator, the results show transactions starting from the largest entry provided. When configuring multiple text entries and using the **Greater Than** operator, the results show transactions starting from the smallest entry provided.
- Click **Apply**.
![Filters for the Protocol Discovery Logs table on the Protocol Discovery Diagnostics page](/downloads/zpa/dashboard-diagnostics/accessing-protocol-discovery-diagnostics/filter.png)
To apply more filters, click **Add Filters** again or click on the **Filter** icon (![zpa-filtericon.png](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/txnUsersDiagnostics/zpa-filtericon.png)
) within the table. The filter query section within the page updates automatically to include the proper filter for the field name you selected, along with the applicable operator configuration for that field.
To remove an added filter, click the **Close** icon then** Apply**. To remove all filters, click **Clear All**.
You can also click the **Copy** icon to save the filter query details. If you or another ZPA admin access **Diagnostics**, you can paste the query into the field by clicking the **Clipboard** icon.
[See image.](#Clipboard)
The table displays the following data for Protocol Discovery-related requests:
- [App Connection](#acinfo)
- [Protocol](#protocol)
- [App Connector](#appconnector)
- [Application](#application)
[See image.](#table)
You can expand each row to see more details, or click the **Expand**/**Collapse** icon to expand or collapse all rows within the table. By default, the table displays 20 transactions. You can scroll to load more transactions.
[]![Logs for the Protocol Discovery Diagnostics page](/downloads/zpa/dashboard-diagnostics/accessing-protocol-discovery-diagnostics/Logs.png)
[]![Clipboard icon in the Protocol Discovery Log Filter field](/downloads/zpa/dashboard-diagnostics/accessing-protocol-discovery-diagnostics/clipboard.png)
- []**Protocol Discovery Time**: The time that the inspection of the application occurred.
- **Connection ID**: The ID associated with the application request. You can click the **Copy** icon to copy the ID to your clipboard.
- **Total Request Bytes**: The total number of bytes that were requested from the client to the server.
- **Total Response Bytes**: The total number of bytes that responded to the request from server to client.
- **Connection Status Log**: View, download, and copy the raw JSON for the request:
- Click the **View** icon to view details about the connection status log in JSON format.
- Click the **Download** icon to download this JSON file.
- Click the **Copy** icon to copy the raw JSON text for the request to your clipboard.
- []**Protocol Class**: The protocol type associated with the application segment domain and port that logged in to Zscaler Client Connector (KRB, LDAP, SMB, HTTP, and TLS).
- **Traffic Class**: Displays **Classified** if the App Connector identified the protocol. It is displayed as **Unclassified** if the App Connector is unable to identify the protocol.
- **Transport**: Displays the connection as either TCP or UDP transport.
- []**App Connector Name**: The name of the App Connector.
- **App Connector ID**: The ID associated with the application. You can click the **Copy** icon to copy the ID to your clipboard.
- **App Connector Group Name**: The name of the group the App Connector is included in. You can click on the name to open the [Edit App Connector Group](/zpa/about-connectorgroup/edit) window.
- **App Connector Group ID**: The internal ID (created by ZPA) for the App Connector group. You can click the **Copy** icon to copy the ID to your clipboard.
- []**Application: Port & Transport**: The application domain of the end user who logged in to Zscaler Client Connector.
- **Application Segment**: The application segment name as configured in the ZPA Admin Portal. You can click on the name to open the **Edit Application Segment** window, which includes the defined application.
- **Application ID**: The ID associated with the application. You can click the **Copy** icon to copy the ID to your clipboard.
- **Application Domain**: The domain of the application in the transaction request.
[]Some of the following filter options only appear with specific Protocol Discovery log types selected:
- **App Connector Name**: See logs by a specific App Connector you’ve configured.
- **Application Protocol**: See requests by the Application Protocol log type.
- **Domain Name**: See requests by the domain name.
- **Segment Name**: See requests by application segment name as configured in the ZPA Admin Portal.
- **Server Port**: See requests for connections using a specific port.
- **Transport**: See requests based on TCP or UDP transport.
- **Connection ID**: See requests by the ID associated with the application request.
[]![Protocol Discovery table on the Protocol Discovery Diagnostics page](/downloads/zpa/dashboard-diagnostics/accessing-protocol-discovery-diagnostics/PD%20table.png)