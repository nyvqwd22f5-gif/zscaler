# Accessing AD Protection Diagnostics
Source: https://help.zscaler.com/unified/accessing-ad-protection-diagnostics
PDF: https://help.zscaler.com/pdf/com/en/1496461.pdf

You can view and filter Active Directory (AD) Protection log data and trend data for past events.
To view diagnostics for AD Protection:
- Go to **Logs **> **Insights** > **Diagnostics**.
- Under **Log Type**, select **AD Protection**.
By default, the data is displayed for AD Protection log and trend events that occurred in the last 24 hours. To change the time range, click the **Calendar** menu and select a preset range or specify a custom start and end date. If you use a **Custom Range**, the start date must be within the last 14 days. To change the time zone, click the current **Time Zone** button.
Zscaler retains logs for rolling periods of at least 14 days during your subscription term.
[See image.](#timerange)
By default, the log activity for AD Protection is displayed. To see trend chart information, click **Trends**. To learn more, see [**Viewing Trends**](#Trend).
[See image.](#LogsTrends)
Viewing Logs
Log activity is automatically displayed after selecting the **AD Protection** log type.
By default, the table displays the **Total** number of AD Protection-related requests made by users. You can change this by choosing one of the following filters:
- **LDAP**: The total number of AD Protection logs associated with the application segments configured for detecting and inspecting LDAP protocol traffic.
- **SMB**: The total number of AD Protection logs associated with the application segments configured for detecting and inspecting SMB protocol traffic.
- **Kerberos**: The total number of AD Protection logs associated with the application segments configured for detecting and inspecting Kerberos protocol traffic.
- **Unclassified**: The total number of AD Protection logs associated with the application segments where the protocol could not be classified.
- **Errors**: The total number of AD Protection-related errors.
[See image.](#Totals)
Filtering AD Protection Logs
On the AD Protection page, you can apply filters or drill down further into the log data using the Query Builder. By default, no filters are applied. If you want to view and filter AD Protection logs for real-time events, use [Live Logs](/unified/about-live-logs).
To configure filters using the Query Builder:
- Click **Add Filters** and select a filter from the drop-down menu:
[View query builder filters:](#Filters)
- Select an operator from the drop-down menu (e.g., **Contains**, **Ends With**, **Equals**, **Not Equals**, **Starts With**). The operators available are determined by the filter you are configuring.
- Select the fields from the drop-down menu or enter the values required for the filter. The field or value required is determined by the filter you are configuring.
Filters using the **Contains** operator allow a maximum of 7 entries. All filters using operators that require text input must use a semicolon (;) to separate multiple entries (e.g., 137; 138; 139). When configuring multiple text entries and using the **Less Than** operator, the results show transactions starting from the largest entry provided. When configuring multiple text entries and using the **Greater Than** operator, the results show transactions starting from the smallest entry provided.
- Click **Apply**.
![Filters for the AD Protection Logs table on the AD Protection Diagnostics page](/downloads/zpa/dashboard-diagnostics/about-ad-protection-diagnostics/Filter.png)
To apply more filters, click **Add Filters** again or click on the **Apply Filter **icon (![zpa-filtericon.png](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/txnUsersDiagnostics/zpa-filtericon.png)
) within the table. The filter query section within the page updates automatically to include the proper filter for the field name you selected, along with the applicable operator configuration for that field.
To remove an added filter, click the **Close** icon then **Apply**. To remove all filters, click **Clear All**.
You can also click the **Copy **icon to save the filter query details. If you or another admin access **Diagnostics**, you can paste the query into the field by clicking the **Clipboard** icon.
[See image.](#clipboard)
The table displays the following data for AD Protection-related requests:
- [AD Connection](#ADconnection)
- [AD Protocol](#ADProtocol)
- [App Connector](#AppConnector)
- [Application](#Application)
You can expand each row to see more details or click the **Expand**/**Collapse** icon to expand or collapse all rows within the table. By default, the table displays 20 transactions. You can scroll to load more transactions.
[]Viewing Trends
The AD Protection Diagnostics provides charts that track trends for different aspects of AD Protection-related requests.
Filtering AD Protection Trends
On the AD Protection Diagnostics page, you can apply filters using the Query Builder to focus the trends charts to specific data. By default, no filters are applied.
To configure filters using the Query Builder:
- Click **Add Filters** and select a filter from the drop-down menu:
[View query builder filters:](#Trendfilters)
- Select an operator from the drop-down menu (e.g., **Contains**, **Ends With**, **Equals**, **Not Equals**, **Starts With**). The operators available are determined by the filter you are configuring.
- Select the fields from the drop-down menu or enter in the values required for the filter. The field or value required is determined by the filter you are configuring.
- Click **Apply**.
The trends charts available are:
- [LDAP Query Trend](#LDAPquery)
- [SMB Trend](#SMBquery)
- [Kerberos Trend](#Kerberosquery)
By default, all trend charts are displayed. Deselect a chart to remove it from the page.
When the AD Protection Diagnostics Trend page is refreshed the legend colors for the trend charts might change.
[See image.](#trendoption)
You can move over the chart to view the values along different points in time and to see how the values changed. Select a portion of the chart to drill down further into the data displayed. Click **Zoom Out** to return the chart to its original view.
[See image.](#zoom)
[]Some of the filter options below only appear with specific AD Protection log types selected:
- **AD Protocol:** Filter AD Protection logs based on the AD Protection protocol type.
- **App Connector Name**: See requests by App Connector name as configured in the Admin Portal.
- **Application**:** Domain**: See requests for a specific application. Enter the FQDN or IP address of the application.
- **Application**: **Segment Name**: See requests by application segment name as configured in the Admin Portal.
- **Application**: **Server Port**: See requests for connections using a specific port.
- **Application**: **Transport**: See requests based on TCP or UDP transport.
- **KRB TGS Error**: See requests with Kerberos error messages from TGS requests.
- **KRB TGS Request**: See requests for TGS requests.
- **KRB TGS Response**: See requests with successful completions of TGS requests.
- **KRB TGT Error**: See requests with Kerberos error messages from TGT requests.
- **KRB TGT Request**: See requests for TGS requests.
- **KRB TGT Response**: See requests with successful completions of TGT requests.
- **LDAP ACL Queries**: See requests based on ACL queries.
- **LDAP Group Queries**: See requests based on LDAP-related group queries.
- **LDAP Object Property Queries**: See requests based on LDAP-related queries of an object in the AD database.
- **Policy: AppProtection Policy Name**: See requests by the policy name configured in an AppProtection policy.
- **SMB Session Enumeration**: See requests for SMB-related session enumeration data.
- **SMB User Enumeration**: See requests for SMB-related user enumeration data.
- **Username**: See requests for a particular username. This is the NameID in the SAML assertion from the IdP and not the username entered in Zscaler Client Connector. You can select up to 5 for this filter option.
[]![Clipboard icon in the AD Protection Log Filter field ](/downloads/zpa/dashboard-diagnostics/about-ad-protection-diagnostics/Clipboard%20icon_0.png)
- []**AD Log Start Time**: The time the Active Directory log started.
- **AD Log End Time**: The time the Active Directory log ended. The default time is set to 15 seconds.
- **Username**: The Zscaler Client Connector username that had logged in.
- **MTunnel Count**: The number of [[variable:microtunnel-​​​​​m-tunnel]]-inspected connections during the set log time.
- **Total Request Bytes**: The total number of bytes that were requested from the client to the server.
- **Total Response Bytes**: The total number of bytes that responded to the request from server to client.
- **Errors**: The number of M-tunnels that detected protocol errors.
- **Connection Status Log**: View, download, and copy the raw JSON for the request:
- Click the **View** icon to view details about the connection status log in JSON format.
- Click the **Download **icon to download this JSON file.
- Click the **Copy** icon to copy the raw JSON text for the request to your clipboard.
- []**Protocol Class**: The protocol type associated with the application segment domain and port that logged into Zscaler Client Connector.
- **Traffic Class**: Displays Classified if the App Connector identified the protocol. It is displayed as Unclassified if the App Connectorr is unable to identify the protocol.
- **Transport**: Displays the connection as either TCP or UDP transport.
- **Version**: The version of the specific protocol for classified traffic.
Depending on the log type you select, the following AD Protection fields are shown in addition to the ones above:
LDAP
- **Bind Requests**: The number of queries that were used to authenticate the client.
- **Search Requests**: How many search queries the client requested the protocol requested that match certain criteria. The search requests are also tracked based on their sub-queries.
- **General Requests**: Any additional LDAP operations (i.e., unbind, abandon) fall into this category.
- **Update Request**: Queries related to modifications of the data structure.
- **Base Object Queries**: Specific search requests of the scope of the base object.
- **Single Level Queries**: Specific search requests of a single level.
- **Whole Subtree Queries**: A search request of a whole subtree.
- **ACL Queries**: Access Control List (ACL) queries for user and system permissions.
- **Object Property Queries**: Queries for a specific attribute of an object in the AD database.
- **Group Queries**: Queries for retrieving attributes of a specific group or a domain name from the AD database.
SMB
- **Session Control Requests**: How many SMB session control requests have been identified (i.e., negotiate protocol, session control, and keepalive).
- **File Operations Requests**: Any SMB commands related to file operations (i.e., read a file, write a file, and find).
- **General Requests**: General SMB commands (i.e, get info, set info, and tree connect).
- **RPC Requests**: The number of M-tunnels running Microsoft RPC traffic. It is a sub-type of an SMB protocol.
- **Session Enumeration**: The number of M-tunnels carrying SMB Microsoft RPC traffic specific to session enumerations.
- **User Enumeration**: The number of M-tunnels carrying SMB Microsoft RPC traffic specific to user enumerations.
Kerberos
- **TGT Request**: The number of ticket granting ticket (TGT) requests. Another commonly used name is authentication server request (AS REQ).
- **TGT Response**: The response to TGT requests for a successful completion of the TGT request.
- **TGT Error**: A Kerberos error message is responded by the Key Distribution Center (KDC) in the case of an unsuccessful TGT request.
- **TGS Request**: The number of ticket granting service (TGS) requests. This is used for requesting service tickets (ST) from KDC.
- **TGS Response**: The response to TGS requests for a successful completion of the TGS request.
- **TGS Error**: A Kerberos error message is responded by the Key Distribution Center (KDC) in the case of an unsuccessful TGS request.
Unclassified
- **Inspection Protocol**: The inspection pipeline was unable to classify to a specific protocol.
- []**App Connector Name**: See logs for a specific App Connector you've configured.
- **App Connector ID**: The ID associated with the application. You can click the **Copy** icon to copy the ID to your clipboard.
- **App Connector Group Name**: The name of the group the App Connector is included in. You can click on the name to open the [Edit App Connector Group](/unified/editing-app-connector-groups) window.
- **App Connector Group ID**: The internal ID (created by Private Applications) for the App Connector group. You can click the **Copy** icon to copy the ID to your clipboard.
- []**Application Port & Transport**: Application domain of the end user who logged into Zscaler Client Connector.
- **Application Segment**: The application segment name as configured in the Admin Portal. You can click on the name to open the [Edit Application Segment](/unified/editing-defined-application-segments) window, which includes the defined application.
- **Application ID**: The ID associated with the application. You can click the **Copy** icon to copy the ID to your clipboard.
- **AppProtection Policy Name**: See logs by the name of one or more specific AppProtection policies.
- **AppProtection Policy ID**: See requests by the ID associated with the AppProtection request.
[]![AD Protection Diagnostics Time Range](/downloads/zpa/dashboard-diagnostics/about-ad-protection-diagnostics/Diagnostics%20high%20level%20top%20section.png)
[]![Logs and Trends tabs in the AD Protection Diagnostics page in the Admin Portal](/downloads/zpa/dashboard-diagnostics/about-ad-protection-diagnostics/Logs%20selection.png)
[]![Logs and Trends tabs in the AD Protection Diagnostics page in the Admin Portal](/downloads/zpa/dashboard-diagnostics/about-ad-protection-diagnostics/Log%20Totals_0.png)
- []**App Connector Name**: See requests by App Connector name as configured in the Admin Portal.
- **Application**:** Domain**: See requests for a specific application. Enter the FQDN or IP address of the application.
- **Application**: **Segment Name**: See requests by application segment name as configured in the Admin Portal.
- **Application**: **Server Port**: See requests for connections using a specific port.
- **Username**: See requests for a particular username. This is the NameID in the SAML assertion from the IdP and not the username entered in Zscaler Client Connector. You can select up to 5 for this filter option.
[]The LDAP Query Trend chart shows the number of LDAP-related queries that occurred in the selected time range. By default, the chart shows the following LDAP-related queries, which you can deselect to narrow the focus of the chart to look into the stats of a specific query type. The dotted lines in the trend charts show the average for the set amount of time. If you don't see a dotted line, it means the average is zero. The solid lines in the trend chart are the actual results from the LDAP queries. Where there are spikes in the data, there is a potential for malicious activity.
- **Object Property Queries**
- **ACL Queries**
- **Group Queries**
Click **View Logs** to view the logs based on the date specified in the LDAP Query Trend chart.
![LDAP Query Trend for the AD Protection Diagnostic page on the Admin Portal ](/downloads/zpa/dashboard-diagnostics/about-ad-protection-diagnostics/LDAP%20trend%20chart%20details%20w%20arrows.png)
[]The SMB Query Trend chart shows the number of SMB-related queries that occurred in the selected time range. By default, the chart shows the following SMB-related queries, which you can deselect to narrow the focus of the chart to look into the stats of a specific query type. The dotted lines in the trend charts show the average for the set amount of time. If you don't see a dotted line, it means the average is zero. The solid lines in the trend chart are the actual results from the SMB queries. Where there are spikes in the data, there is a potential for malicious activity.
- **User Enumeration**
- **Session Enumeration**
Click **View Logs** to view the logs based on the date specified in the SMB Query Trend chart.
![SMB Query Trend Chart for the AD Protection Diagnostics page on the Admin Portal](/downloads/zpa/dashboard-diagnostics/about-ad-protection-diagnostics/SMB%20Trend%20chart%20details%20w%20arrows.png)
[]The Kerberos Query Trend chart shows the number of Kerberos-related queries that occurred in the selected time range. By default, the chart shows the following Kerberos-related queries, which you can deselect to narrow the focus of the chart to look into the stats of a specific query type. The dotted lines in the trend charts show the average for the set amount of time. If you don't see a dotted line, it means the average is zero. The solid lines in the trend chart are the actual results from the Kerberos queries. Where there are spikes in the data, there is a potential for malicious activity.
- **TGS Error**
- **TGT Success**
- **TGT Total**
- **TGS Total**
- **TGT Error**
- **TGS Success**
Click **View Logs** to view the logs based on the date specified in the Kerberos Query Trend chart.
![Kerberos Query Trend Chart for the AD Protection Diagnostics page on the Admin Portal ](/downloads/zpa/dashboard-diagnostics/about-ad-protection-diagnostics/Kerberos%20Trend%20chart%20details%20w%20arrows_0.png)
[]![Trend Chart options for User Activity in the Diagnostics page on the Admin Portal](/downloads/zpa/dashboard-diagnostics/accessing-ad-protection-diagnostics/AD%20Protection%20Diagnostics.png)
[]![Zoom Out of a Trends Chart in the User Activity Diagnostics in the Admin Portal](/downloads/zpa/dashboard-diagnostics/about-user-activity-diagnostics/Zoom%20out.png)