# Accessing Application Protocol Diagnostics
Source: https://help.zscaler.com/unified/accessing-application-protocol-diagnostics
PDF: https://help.zscaler.com/pdf/com/en/1496471.pdf

You can view and filter Application Protocol data for past AppProtection-enabled application segment events.
To view diagnostics for Application Protocol data:
- Go to **Logs** > **Insights** > **Diagnostics**.
- Under **Log Type**, choose **Application Protocol**.
By default, the detailed activity for all application protocols is displayed for events that occurred in the last 24 hours. To change the time range, click the **Calendar **menu and select a preset range or specify a custom start and end date. If you use a **Custom Range**, the start date must be within the last 14 days. To change the time zone, click the current **Time Zone** button.
Zscaler retains logs for rolling periods of at least 14 days during your subscription term. You can also view your logs or stream logs in real time using the [Log Streaming Service (LSS)](/unified/about-log-streaming-service). Data in the dashboard might be more recent than the data presented within Diagnostics for the same time range.
[See image.](#Timerange)
Viewing Logs
Log activity is automatically displayed after selecting the Application Protocol log type.
By default, the table displays the **Total** number of application protocol requests. You can change this by choosing one of the following filters:
- **HTTP**: The total number of application protocol logs associated with the application segments where the HTTP protocol traffic was auto-detected and inspected.
- **HTTPS**: The total number of application protocol logs associated with the application segments where the HTTPS protocol traffic was auto-detected and inspected.
- **KRB**: The total number of application protocol logs associated with the application segments where the Kerberos protocol traffic was auto-detected and inspected.
- **LDAP**: The total number of application protocol logs associated with the application segments where the LDAP protocol traffic was auto-detected and inspected.
- **SMB**: The total number of application protocol logs associated with the application segments where the SMB protocol traffic was auto-detected and inspected.
- **TLS**: The total number of application protocol logs associated with the application segments where the TLS protocol traffic was auto-detected and inspected.
- **Unclassified**: The total number of application protocol logs associated with the application segments where the protocol couldn't be classified.
[See image.](#Logwidgets)
Filtering Application Protocol Logs
On the Application Protocol page, you can apply filters or drill down further into the log data using the Query Builder. By default, no filters are applied.
To configure filters using the Query Builder:
- Click **Add Filters** and select a filter from the drop-down menu:
[View query builder filters:](#Filters)
- Select an operator from the drop-down menu (e.g., **Contains**, **Ends With**, **Equals**, **Not Equals**, **Starts With**). The operators available are determined by the filter you are configuring.
- Select the fields from the drop-down menu or enter the values required for the filter. The field or value required is determined by the filter you are configuring.
Filters using the **Contains** operator allow a maximum of 7 entries. All filters using operators that require text input must use a semicolon (;) to separate multiple entries (e.g., 137; 138; 139). When configuring multiple text entries and using the** Less Than** operator, the results show transactions starting from the largest entry provided. When configuring multiple text entries and using the **Greater Than **operator, the results show transactions starting from the smallest entry provided.
- Click **Apply**.
![Filters for the Application Protocol Logs table on the Application Protocol Diagnostics page](/downloads/zpa/dashboard-diagnostics/accessing-application-protocol-diagnostics/Filters.png)
To apply more filters, click **Add Filters** again or click on the **Apply Filter **icon (![zpa-filtericon.png](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/txnUsersDiagnostics/zpa-filtericon.png)
) within the table. The filter query section within the page updates automatically to include the proper filter for the field name you selected, along with the applicable operator configuration for that field.
To remove an added filter, click the **Close** icon then **Apply**. To remove all filters, click **Clear All**.
If you have selected filters previously, the **Recent Filters** icon appears. You can click this icon to repopulate recent filters. You can also click the **Copy** icon to save the filter query details. If you or another admin access **Diagnostics**, you can paste the query into the field by clicking the **Clipboard** icon.
[See image.](#Clipboard)
The table displays the following data for Application Protocol requests:
- [App Connection](#AppConnection)
- [Protocol](#Protocol)
- [App Connector](#AppConnect)
- [Application](#Application)
[See image.](#Table)
You can expand each row to see more details or click the Expand/Collapse icon to expand or collapse all rows within the table. By default, the table displays 20 transactions. You can scroll to load more transactions.
- []**App Connector Name**: See requests by App Connector name as configured in the Admin Portal.
- **AppProtection Profile**: **Name**: See requests by the AppProtection profile name as configured in the Admin Portal.
- **Application Protocol**: See requests by the Application Protocol log type. To use this filter, select the Total Application Protocol log type a the top of the page.
- **Application**: **Domain**: See requests for a specific application. Enter the FQDN or IP address of the application.
- **Application**: **Segment Name**: See requests by application segment name as configured in the Admin Portal.
- **Application**: **Server Port**: See requests for connections using a specific port.
- **Application**: **Transport**: See requests based on TCP or UDP transport.
- **Policy**: **AppProtection Policy Name**: See requests by the policy name configured in an AppProtection policy.
- **Username**: See requests for a particular username. This is the NameID in the SAML assertion from the IdP and not the username entered in Zscaler Client Connector.
- []**Log Start Time**: The date, time, and time zone that the connection started.
- **Log End Time**: The date, time, and time zone that the connection was completed.
- **Username**: The user who requested the application. This is the NameID in the SAML assertion from the IdP and not the username entered in Zscaler Client Connector.
- **MTunnel Count**: The total number of Microtunnels for which the data is captured in specific application protocol logs.
- **Total Request Bytes**: The total number of bytes that were requested from the application protocol connection.
- **Total Response Bytes**: The total number of bytes that responded to the request from the application protocol connection.
- **Errors**: The number of Microtunnels that detected application protocol errors.
- **Connection Status Logs**: View, download, and copy the raw JSON for the request:
- Click the **View **icon to view details about the connection status log in JSON format.
- Click the **Download** icon to download this JSON file.
- Click the **Copy** icon to copy the raw JSON text for the request to your clipboard.
- []**Protocol Class**: The protocol type associated with the application segment domain and port that logged into Zscaler Client Connector.
- **Traffic Class**: Displays Classified if the App Connector identified the protocol. It is displayed as Unclassified if the App Connector is unable to identify the protocol.
- **Transport**: Displays the connection as either TCP or UDP transport.
- **Version**: The version of the specific protocol for classified traffic.
- []**App Connector Name**: The name of the App Connector used to connect the application to the user. You can click on the name to open the [Edit App Connector](/unified/editing-deployed-app-connector) window.
- **App Connector ID**: The internal ID (created by Private Applications) for the connection request to the application. You can click the **Copy** icon to copy the ID to your clipboard.
- **App Connector Group Name**: The name of the group the App Connector is included in. You can click on the name to open the [Edit App Connector Group](/unified/editing-app-connector-groups) window.
- **App Connector Group ID**: The internal ID (created by Private Applications) for theApp Connector group. You can click the **Copy** icon to copy the ID to your clipboard.
- []**Application**: **Port & Transport**: Application domain of the end user who logged into Zscaler Client Connector.
- **Application Segment**: The application segment name as configured in the Admin Portal. You can click on the name to open the [Edit Application Segment](/unified/editing-defined-application-segments) window, which includes the defined application.
- **Application ID**: The ID associated with the application. You can click the **Copy** icon to copy the ID to your clipboard.
- **App Protection Policy Name**: See logs by the name of one or more specific AppProtection policies.
- **App Protection Policy ID**: See requests by the ID associated with the AppProtection request.
- **App Protection Profile ID**: The ID of the AppProtection profile. You can click the **Copy** icon to copy the ID to your clipboard.
- **App Protection Profile Name**: The name of the AppProtection profile.
[]![Application Protocol Diagnostics Time Range](/downloads/zpa/dashboard-diagnostics/accessing-application-protocol-diagnostics/Time%20range.png)
[]![Logs tab in the Application Protocol Diagnostics page in the Admin Portal](/downloads/zpa/dashboard-diagnostics/accessing-application-protocol-diagnostics/Protocol%20log%20types.png)
[]![Clipboard icon in the AD Protection Log Filter field](/downloads/zpa/dashboard-diagnostics/accessing-application-protocol-diagnostics/Icons.png)
[]![Application Protocol Diagnostics page within the Admin Portal](/downloads/zpa/dashboard-diagnostics/accessing-application-protocol-diagnostics/Full%20page_1.png)