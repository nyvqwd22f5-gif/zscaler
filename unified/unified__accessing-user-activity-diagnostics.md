# Accessing User Activity Diagnostics
Source: https://help.zscaler.com/unified/accessing-user-activity-diagnostics
PDF: https://help.zscaler.com/pdf/com/en/1498051.pdf

You can view and filter user activity log data and trend data for past events.
To view diagnostics for user activity:
- Go to **Diagnostics **(Logs> Insights > Diagnostics).
- Under **Log Type**, choose **User Activity**.
By default, the detailed activity for all users is displayed for events that occurred in the last 24 hours. To change the time range, click the **Calendar **menu and select a preset range or specify a custom start and end date. If you use a **Custom Range**, the start date must be within the last 14 days. To change the time zone, click the current **Time Zone** button.
Zscaler retains logs for rolling periods of at least 14 days during your subscription term. You can also view your logs or stream logs in real time using the [Log Streaming Service (LSS)](/unified/about-log-streaming-service). Data in the [dashboard](/unified/analytics/private-applications) might be more recent than the data presented within Diagnostics for the same time range.
[See image.](#img-timerange)
By default, the log activity for all users is displayed. To see trend chart information, click the **Trends **tab. To learn more, see [Viewing Trends](#Trends) below.
[See image.](#img-tabs)
Viewing Logs
Log activity is automatically displayed after selecting the User Activity log type.
By default, the table displays the **Total** number of application requests made by users. You can change this by choosing one of the following filters:
- **Errors**: The total number of application access errors.
- **Access Policy Blocks**: The total number of application requests blocked by an access policy rule.
- **Timeout Policy Blocks**: The total number of application requests blocked by a timeout policy rule.
- **Successful**: The total number of successful application requests.
- **Info**: The total number of application connections that terminated because the user or App Connector abruptly ended the TLS session (e.g., user laptop enters sleep mode which ends the TLS session) or the application's connection gracefully timed out.
[See image.](#img-logtotals)
Filtering User Activity Logs
On the User Activity page, you can apply filters or drill down further into the log data using the Query Builder. By default, no filters are applied. If you want to view and filter User Activity for real-time events, use [Live Logs](/zpa/about-live-logs).
To configure filters using the Query Builder:
- Click **Add Filters** and select a filter from the drop-down menu:
[View query builder filters:](#filters)
- Select an operator from the drop-down menu (e.g., **Contains**, **Ends With**, **Equals**, **Not Equals**, **Starts With**). The operators available are determined by the filter you are configuring.
- Select the fields from the drop-down menu or enter the values required for the filter. The field or value required is determined by the filter you are configuring.
Filters using the **Contains **operator allow a maximum of 7 entries. All filters using operators that require text input must use a semicolon (;) to separate multiple entries (e.g., 137; 138; 139). When configuring multiple text entries and using the **Less Than** operator, the results show transactions starting from the largest entry provided. When configuring multiple text entries and using the **Greater Than** operator, the results show transactions starting from the smallest entry provided.
- Click **Apply**.
![zpa-useractivity-qbexample.png](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/txnUsersDiagnostics/zpa-useractivity-qbexample.png)
To apply more filters, click **Add Filters** again or click on the **Apply Filter **icon (![zpa-filtericon.png](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/txnUsersDiagnostics/zpa-filtericon.png)
) within the table. The filter query section within the page updates automatically to include the proper filter for the field name you selected, along with the applicable operator configuration for that field.
To remove an added filter, click the **Close** icon then **Apply**. To remove all filters, click **Clear All**.
You can also click the **Copy** icon to save the filter query details. If you or another admin access **Diagnostics**, you can paste the query into the field by clicking the **Clipboard **icon.
[See image.](#QueryBuilder_CopyPaste)
[]The table displays the following data for application requests:
- [Connection](#time)
- [Policy](#policy)
- [User](#user)
- [Service Edge](#se)
- [App Connector](#connector)
- [Application](#application)
You can expand each row to see more details or click the **Expand**/**Collapse** icon to expand or collapse all rows within the table. By default, the table displays 20 transactions. You can scroll to load more transactions.
[]Viewing Trends
The User Activity Diagnostics provides charts that track trends for different aspects of user activity.
Filtering User Activity Trends
On the User Activity page, you can apply filters using the Query Builder to focus the trends charts to specific data. By default, no filters are applied.
- Click **Add Filters** and select a filter from the drop-down menu:
- **App Connector Name**: See data in the charts by App Connector name as configured in the Admin Portal.
- **Application: Domain**: See requests for a specific application. Enter the FQDN or IP address of the application.
- **Application: Segment Name**: See data in the charts by application segment name as configured in the Admin Portal.
- **Application: Server Port**: See requests for connections using a specific port.
- **Connection: Status Code**: See requests that resulted in a specific status code. To learn more, see [Session Status Codes](/unified/understanding-session-status-codes).
- **Dispatcher ID**: See requests by the ID associated with the dispatcher.
- **Machine Tunnel**: See requests by machine tunnel.
- **Service Edge: Name (Public/Private)**: See data in the charts by specific Public Service Edge or Private Service Edge.
- **User: Client Type**: See requests by the client type the user's device is connecting from (i.e., **Branch Connector**, **Web Browser**, **Internet & SaaS Service Edge**, **Client Connector**, **Client Connector Partner**, **Cloud Connector**, **Machine Tunnel**, **Web Browser Unauthenticated**, or **Cloud Browser**).
- **Username**: See requests for a particular username. This is the NameID in the SAML assertion from the IdP and not the username entered in Zscaler Client Connector. You can select up to 5 for this filter option.
- **Internet & SaaS Inspection**: See logs by Internet & SaaS Inspection transaction type.
- Select an operator from the drop-down menu (e.g., **Contains**, **Ends With**, **Equals**, **Not Equals**, **Starts With**). The operators available are determined by the filter you are configuring.
- Select the fields from the drop-down menu or enter in the values required for the filter. The field or value required is determined by the filter you are configuring.
- Click **Apply**.
The trends charts available are:
- [Transaction Trend](#trends-transaction)
- [Unique Users Trend](#trends-uniqueuser)
- [Total Data Transferred Trend](#trends-totaldatatransferred)
- [Unique Domains Trend](#trends-unqiuedomain)
- [Policy Blocks Trend](#trends-policyblocks)
- [Reauth Blocks Trend](#trends-reauth)
By default, all trend charts are displayed. Deselect a chart to remove it from the page.
[See image.](#img-trendcharts)
You can move over the chart to view the values along different points in time and to see how the values changed. Select a portion of the chart to drill down further into the data displayed. Click **Zoom Out** to return the chart to its original view.
[See image.](#img-zoomout)
[]![User Activity Time Range](/downloads/zpa/dashboard-diagnostics/about-user-activity-diagnostics/zpa-useractivity-logtypeandtimerange_0.png)
![Logs and Trends tabs in the User Activity Diagnostic page in the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/about-user-activity-diagnostics/zpa-useractivity-logstrends.png)
[]
[]![User Activity Totals](/downloads/zpa/dashboard-diagnostics/about-user-activity-diagnostics/zpa-useractivity-totals_0.png)
- []**Access Type: Client to Client**: See requests for whether the domain being accessed by the Zscaler Client Connector allows client-to-client communication or not.
- **App Connector: IP Address: **See requests by App Connector IP address.
- **App Connector Name**: See requests by App Connector name as configured in the Admin Portal.
- **App Connector: Port**: See requests by App Connector port.
- **App Connector: Session Type**: See requests by App Connector session type.
- **Application: Domain**: See requests for a specific application. Enter the FQDN or IP address of the application.
- **Application: Double Encryption**: See requests that have [Double Encryption](/zpa/about-double-encryption) enabled or disabled for the application.
- **Application: Duration**: See requests for a specific duration.
- **Application: Protocol**: See requests for connections using a specific protocol.
- **Application: Segment Name**: See requests by application segment name as configured in the Admin Portal.
- **Application: Server IP Address**: See requests by application server IP address.
- **Application: Server Port**: See requests for connections using a specific port.
- **Connection: Connection ID**: See requests by the ID associated with the application request.
- **Connection: Status**: See requests with **Open**, **Active**, or **Closed **connections.
- **Connection: Status Code**: See requests that resulted in a specific status code. To learn more, see [Session Status Codes](/unified/understanding-session-status-codes).
- **Connection: Setup Time**: See requests based on the latency in milliseconds (ms) for the App Connector to set up the connection to the application server.
- **Control Service Edge: Name (Public/Private)**: See requests by the control Public Service Edge or Private Service Edge.
- **Connection Type**: See requests by the connection type (i.e., **Private Applications**, **Digital Experience Monitoring**, **Web Probe Cacheless**, **HTTP Web Probe**, or **HTTPS Web Probe**). By default, the Connection Type is set to Private Applications.
- **Dispatcher ID:** See requests based on the dispatcher ID.
- **Extranet Location**: See requests based on the locations and location groups that can connect to an application at a partner's site using an IPSec tunnel.
- **Extranet Resource**: See requests based on the partner's resource name that accesses applications at the partner's site.
- **From a Microtenant**: See logs by the Microtenant (i.e., within the current Microtenant or within the shared Microtenants).
- **Hop based transaction logs**: See logs by the number of hops that occurred. Typically, hops occur when the connection goes from Zscaler Client Connector to a Public Service Edge, and then to another Public Service Edge managed by Zscaler.
- **Inspection Status**: See the status of inspection tunnel connections.
- **Machine Tunnel**: See requests by machine tunnel.
- **Policy: Access Policy Name**: See requests that triggered a specific access policy.
- **Policy: AppProtection Policy Name**: See requests by the policy name configured in an AppProtection policy.
- **Policy: IdP Name**: See requests from users authenticated by the Identity Provider (IdP) name as configured in the Admin Portal.
- **Policy: Timeout Policy Name**: See requests that triggered a specific timeout policy.
- **Privileged Session Recording**: See requests by availability status for privileged session recordings (i.e., **Started** or **Available**).
- **Service Edge: Name (Public/Private)**: See requests with connections through a specific Public Service Edge or Private Service Edge.
- **Service Edge: Rx From Client**: See bytes received by a Public Service Edge or Private Service Edge from a client.
- **Service Edge: Rx From App Connector**: See bytes received by a Public Service Edge or Private Service Edge from an App Connector.
- **Service Edge: Tx To Client**: See bytes transmitted by a Public Service Edge or Private Service Edge to a client.
- **Service Edge: Tx To App Connector**: See bytes transmitted by a Public Service Edge or Private Service Edge to an App Connector.
- **Service Edge: Type**: See logs by the Service Edge type (i.e., **Public** or **Private**).
- **Source IP Address:** See logs by the IP address of the Branch Connector, Cloud Connector, or Service Edge.
- **User: Client IP**: See requests from a specific device IP address.
- **User: Client Type**: See requests by the client type the user's device is connecting from (i.e., **Branch Connector**, **Zscaler Client Connector**, **Client Connector Partner**, **Web Browser**, **Web Browser Unauthenticated**, or **Internet & SaaS Public Service Edge**).
- **User: Platform**: See logs based on the device platform (i.e., Windows, Linux, macOS, iOS, or Android).
- **User: System Public IP**: See requests from a specific system IP.
- **Username**: See requests for a particular username. This is the NameID in the SAML assertion from the IdP and not the username entered in Zscaler Client Connector. You can select up to 5 for this filter option.
To see users that are accessing applications using Browser Access through unauthenticated HTTP preflight OPTIONS request, the username appears as **Private Applications BA Unauthenticated**. To learn more, see [Configuring Application Segments](/zpa/configuring-application-segments#BrowserAccess_NewAppSeg).
If you are using the [Log Streaming Service (LSS)](/zpa/about-log-streaming), be aware that the Private Applications LSS Client user represents the LSS service, not an actual user. By default, Diagnostic information for the Private Applications LSS Client is captured but not displayed. You must explicitly select this from the **User** field to display its log information. Also, each log receiver is displayed as an application, to reflect the data coming in from the service. To learn more, including how to stop the LSS service from streaming Private Applications LSS Client logs, see [Configuring a Log Receiver](/zpa/configuring-log-receiver#Step2).
- **Internet & SaaS Inspection**: See requests based on whether Inspection is enabled.
The **Connection **column sorts requests by the connection date and start time in descending order. You can click the **Arrow** icon to sort the requests in ascending order. The time displayed is based on the time you choose for [your account setting](/zpa/about-zpa-admin-portal#username) in the Admin Portal.
- []**Start Time**: The time the connection started.
- **End Time**: The time the connection ended.
- **Status Code**: The status of the application request. For errors and policy blocks, you can click the connection status name to learn more about it. To see a complete list of session statuses, see [Session Status Codes](/unified/understanding-session-status-codes).
- **Internal Status Code**: The internal status reason. You can click the **Copy **icon to copy the internal reason to your clipboard. This field only applies to errors and policy blocks. To see a complete list of internal reasons per connection status, see [Session Status Codes](/unified/understanding-session-status-codes).
If you [configure an application](/unified/configuring-defined-application-segments) for ICMP Access, the [IP](/unified/accessing-user-activity-diagnostics#connector) data appears and the status may show as successful (e.g., BRK_MT_TERMINATED) after the App Connector is selected, even when it is unreachable. This may occur if the App Connector is set up to provide on access or no [health reporting](/unified/understanding-health-reporting).
- **Status**: Displays one of the following connection states:
- **Open Connection** ![Screenshot of the Open Connection arrow.](/downloads/zpa/documentation-knowledgebase/diagnostics/txnUsersDiagnostics/open_connection.png)
: The user is currently connected to the application.
- **Active Connection** ![Screenshot of the Active Connection arrow.](/downloads/zpa/documentation-knowledgebase/diagnostics/txnUsersDiagnostics/active_connection.png)
: The user is currently using the application.
- **Closed Connection** ![Closed Connection Arrow.png](/downloads/zpa/documentation-knowledgebase/diagnostics/txnUsersDiagnostics/becbz2w8ckdckcjuga5hr5u7n4zwwle9eh-d9j0idvobc8efmyacpswneprpi1g8jk6kvi-e1kxuwywr4p8jzhxtt_rr0rm-th_smmi7wziizcwzniv14np2aarwtl9cb60gujea.png)
: The user's connection has ended.
- **Duration**: The duration of the connection to the application.
- **Total Bytes**: The total bytes (B) and kilobytes (KB) of the request and the response, respectively.
- **Access Type**: The access type associated with the request. This field is only visible when the Access Type is client-to-client.
- **Connection ID**: The ID associated with the application request. You can click the **Copy **icon to copy the ID to your clipboard.
- **Connection Type**: The connection type of the application request (i.e., **Private Applications**, **Digital Experience Monitoring**, **Web Probe Cacheless**, **HTTP Web Probe**, or **HTTPS Web Probe**). By default, the Connection Type is set to Private Applications.
- **Hop Connection ID**: The ID associated with the connection hop. Connections without a hop do not show this ID. You can click the **Copy **icon to copy the ID to your clipboard.
A hop occurs when a user's request is forwarded to a Public Service Edge as the App Connector is not able to reach the Private Service Edge. (This is the first part of the hop, and the log information is what appears for the connection.) The Private Service Edge then forwards the request to a Public Service Edge. This is the second part of the hop.
You can click the link to view the log details for the second part of the hop. The log details appear below the session log.
[See image.](#hopidlog)
If there is a hop in the connection, a hop icon appears.
![User activity connection with a hop](/downloads/zpa/dashboard-diagnostics/about-user-activity-diagnostics/zpa-useractivity-hop_0.png)
- **Connection Status Log**: View, download, and copy the raw JSON for the request:
- Click the **View Log **icon to display the **Raw JSON** for the request within the Admin Portal.
- Click the **Download **icon to download the raw JSON for the request to a text (.txt) file.
- Click the **Copy **icon to copy the raw JSON text for the request to your clipboard.
[]![Hop Connection ID logs on the User Activity Diagnostics page](/downloads/zpa/dashboard-diagnostics/about-user-activity-diagnostics/zpa-hop-connection-id.png)
- []**Access Policy Name**: The access policy name as configured in the Admin Portal. You can click on the name to open the [Edit Access Policy](/unified/about-access-policy) window.
- **Action**: Whether the access policy allowed or denied the user access to the application.
- **Policy ID**: The ID associated with the access policy. You can click the **Copy **icon to copy the ID to your clipboard.
- **Timeout Policy Name**: The timeout policy name as configured in the Admin Portal. You can click on the name to open the [Edit Timeout Policy](/unified/editing-timeout-policies) window.
- **Action**: Whether the timeout policy allowed or denied the user access to the application.
- **Inspection Policy Name**: The inspection policy name as configured in the Admin Portal. You can click the name to open the Edit Inspection Policy window. To learn more, see [Editing AppProtection Policies](/unified/editing-appprotection-policies).
- **Inspection Policy ID**: The ID associated with the inspection policy. You can click the **Copy **icon to copy the ID to your clipboard.
- **Timeout Policy ID**: The ID associated with the access or timeout policy. You can click the **Copy **icon to copy the ID to your clipboard.
- **Capabilities Policy ID**: The ID associated with the privileged capabilities policy. You can click the **Copy** icon to copy the ID to your clipboard. To learn more, see [Editing Privileged Capabilities Policies](/zpa/editing-privileged-capabilities-policies).
- **File**: You can click the **View** icon to open the File window to view the downloaded files.
- **Credentials Policy ID**: The ID associated with the privileged credentials policy. You can click the **Copy** icon to copy the ID to your clipboard. To learn more, see [Editing Privileged Credentials Policies](/unified/editing-appprotection-policies).
- []**Username**: The user who requested the application. This is the NameID in the SAML assertion from the IdP and not the username entered in Zscaler Client Connector.
If you are using the [Log Streaming Service (LSS)](/zpa/about-log-streaming), be aware that the Private Applications LSS Client user represents the LSS service, not an actual user. By default, Diagnostic information for the Private Applications LSS Client is captured but not displayed. You must explicitly select this user from the **User** field to display its log information. Also, each log receiver is displayed as an application, to reflect the data coming in from the service. To learn more, including how to stop the service from capturing Private Applications LSS Client logs, see [Configuring a Log Receiver](/zpa/configuring-log-receiver#Step2).
- **IP**: The IP address of the user's device.
- **Location**: The city and country the user is connecting from. If Private Applications is unable to determine the user's location, then the private IP address is shown.
- **Client Type**: The name of the client the user's device is connecting from (i.e., **Branch Connector**, **Zscaler Client Connector**, **Client Connector Partner**, **Web Browser**, **Web Browser Unauthenticated**, or **Internet & SaaS Public Service Edge**).
- **User Metadata**: The metadata of the user who requested the application:
- **IdP Name**: The name of the IdP as configured in the Admin Portal.
- **IdP ID**: The ID associated with the IdP. You can click the **Copy **icon to copy the ID to your clipboard.
- **SAML Attributes **or **Session Attributes**: View, download, and copy the SAML attributes for the user:
- Click the **View Log **icon to display the **SAML Attributes** for the user within the Admin Portal.
- Click the **Download **icon to download the SAML attributes statement for the user to a text (.txt) file.
- Click the **Copy **icon to copy the SAML attribute statement for the user to your clipboard.
If you are subscribed to ZIdentity and have this feature enabled for your tenant, the **SAML Attributes** field is replaced with **Session Attributes**. The user attributes are populated from the ZIdentity Admin Portal and are used for defining various sign-on policies.
- **SCIM Users** or **ZIdentity Users**: The user that is provisioned for SCIM.
If you are subscribed to ZIdentity and have this feature enabled for your tenant, the **SCIM Users** field is replaced with **ZIdentity Users**. The ZIdentity users are populated from the ZIdentity Admin Portal.
- **SCIM Groups** or **User Groups**: The group that is provisioned for SCIM.
If you are subscribed to ZIdentity and have this feature enabled for your tenant, the **SCIM Groups** field is replaced with **Groups**. The groups are populated from the ZIdentity Admin Portal.
- **Hostname**: The hostname of the user's device.
- **Platform**: The platform on the user's device.
- **Zscaler App Trusted Networks**: The names of the trusted networks accessible by the user's device.
- **Posture Profiles Verified**: If Zscaler Client Connector verified the user's device against the criteria specified in the posture profile, then a list of verified posture profiles are displayed for this field. If it displays **Unavailable**, there are no posture profiles to display.
- **Posture Profiles Unverified**: If Zscaler Client Connector was unable to verify the user's device against the criteria specified in the posture profile, then a list of unverified posture profiles are displayed for this field. If it displays **Unavailable**, there are no posture profiles to display.
- []**Name**: The name of the Public Service Edge or Private Service Edge that processed the connection. If the Service Edge is a Private Service Edge, you can click on the name to open the [Edit Service Edge](/unified/editing-deployed-private-service-edge-for-private-applications) window.
Depending on who hosts the Service Edge(Zscaler or your organization), a different icon appears with the Service Edge name.
![The hosted service edge on the user activity page](/downloads/zpa/dashboard-diagnostics/about-user-activity-diagnostics/zpa-serviceedge-hostedby.png)
As part of setting up the TLS session, Zscaler hosted Service Edge directs the user's Zscaler Client Connector to connect with another Service Edge at a particular location. When this happens, a redirect icon (![Retarget service edge icon](/downloads/zpa/dashboard-diagnostics/about-user-activity-diagnostics/zpa-retargeticon.png)
) appears next to the Service Edge name instead of the Service Edge icon above. ​​​​​
- **ID**: The internal ID for the connection request for the Private Service Edge to the App Connector. You can click the **Copy **icon to copy the ID to your clipboard.
- **Group Name**: The name of the group that the Private Service Edge is included in. You can click on the name to open the [Edit Service Edge Group](/unified/editing-private-service-edge-groups-private-applications) window.
- **Group ID**: The internal ID for the Private Service Edge group. You can click the **Copy **icon to copy the ID to your clipboard.
- **Location**: The location of the Public Service Edge or Private Service Edge used to connect the application to the user.
- **Origin Service Edge**: Displays the original Service Edge if a hop occurs between two or more Service Edges.
- **Control Service Edge**: The name of the control Public Service Edge or Private Service Edge forwarded in the request.
- **Control Service Edge ID**: The ID of the control Public Service Edge or Private Service Edge forwarded in the request.
- **Control Service Edge Location**: The location of the control Public Service Edge or Private Service Edge forwarded in the request.
- **Policy Processing**: The latency in milliseconds (ms) between the Public Service Edge or Private Service Edge and the Central Authority (CA).
- **RX From Client**: See bytes received by a Public Service Edge or Private Service Edge from a client.
- **RX From Private Service Edge**: See bytes received by a Public Service Edge from a Private Service Edge.
- **TX To App Connector**: See bytes transmitted by a Public Service Edge or Private Service Edge to an App Connector.
- **RX From App Connector**: See bytes received by a Public Service Edge or Private Service Edge from an App Connector.
- **TX To Client**: See bytes transmitted by a Public Service Edge or Private Service Edge to a client.
- **TX To Private Service Edge**: See bytes transmitted by a Public Service Edge from a Private Service Edge.
- []App Connector details:
- **Name**: The name of the App Connector used to connect the application to the user. You can click on the name to open the [Edit App Connector](/unified/about-app-connectors) window.
- **IP:Port & Protocol**: The IP address, port, and protocol of the App Connector.
- **Location**: The location of the App Connector that was used for accessing the application.
- **App Connector ID**: The internal ID (created by Private Applications) for the connection request to the application. You can click the **Copy **icon to copy the ID to your clipboard.
- **Connection Setup Time**: The latency in milliseconds (ms) for the App Connector to set up the connection to the application server.
- **App Connector Group Name**: The name of the group the App Connector is included in. You can click on the name to open the [Edit App Connector Group](/unified/about-app-connectors) window.
- **App Connector Group ID**: The internal ID (created by ZPA) for the App Connector group. You can click the **Copy **icon to copy the ID to your clipboard.
-
Extranet details:
Values for the following fields appear as **Unavailable **because they apply to the App Connector Name, IP:Port & Protocol, Location, App Connector ID, Connection Setup Time, App Connector Group Name, and App Connector Group ID.
- **Session Type**: The type of session selected during configuration.
- **Extranet Location**: The locations connected to an application at a partner's site using an IPSec tunnel. You can click the **Configuration Graph** icon (![zpa-diagnostics-config-graph-icon.png](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/about-user-activity-diagnostics/zpa-diagnostics-config-graph-icon.png)
) to view a diagram of the application segments and server groups associated with these locations.
- **Extranet Location Group**: The name of the location group that represents the set of all the IPSec tunnels that can reach the application at partner locations. If your organization doesn't use location groups, this field appears as **Unavailable**.
- **Extranet Resource Name**: The name of the partner outside of your organization's network whose application is being accessed.
- []**Application:Port & Protocol**: The destination port and protocol of the requested application.
- **Application Segment**: The application segment name as configured in the Admin Portal. You can click on the name to open the [Edit Application Segment](/unified/editing-defined-application-segments) window, which includes the defined application.
- **Server IP: Port & Protocol**: The IP address, port, and protocol of the server that hosts the application.
- **Application ID**: The ID associated with the application. You can click the **Copy **icon to copy the ID to your clipboard.
- **Server ID**: The ID associated with the server. You can click the **Copy **icon to copy the ID to your clipboard.
- **Double Encryption**: Lists whether [Double Encryption](/unified/about-double-encryption) is enabled or disabled for the application.
- **Credential Username**: The username used to log into a privileged console.
- **Credential Login Type**: The credential type used to log into a privileged console (i.e., password, SSH private key, or passphrase). These vary based on the protocol and authentication supported in the privileged console.
- **Credential ID**: The ID associated with the privileged credential. You can click the ID to view the configurations for that privileged credential. You can click the Copy icon to copy the ID to your clipboard.
- **Credential Pool ID**: The ID associated with the privileged credential pool. You can click the ID to view the configurations for that privileged credential pool. You can click the Copy icon to copy the ID to your clipboard.
- **Files**: You can click the **View** icon to open the File window to [view the downloaded files.](#Files)
- **PRA Error**: If there is an error related to Privileged Remote Access, it is shown here. This field doesn’t show if there isn’t an error.
- **Session Recording**: If there are privileged session recordings available, the field shows as **Available** with a play icon. Click the play icon to go to the page for that specific privileged session recording where you can download or play the video. If there are no privileged session recordings available, the field shows as **Unavailable**. If a privileged session recording is in progress, it shows as **Started**.
- **Sharing Session ID**: The ID associated with sharing a privileged session.
- **Sharing Users**: The end users that the privileged session has been shared with. You can click on the View icon to open the Sharing Users window. The Sharing Users window includes the following:
- **User**: Information on the user.
- **Session Join Time**: The date, time, and time zone the user joined the privileged session.
- **Session Disconnect Time**: The date, time, and time zone that the user disconnected from the privileged session.
[See image.](#Sharing)
- **Internet & SaaS Inspection**: Lists whether Inspection is enabled or disabled for the application.
[]![zpa-qbcopypaste.png](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/txnUsersDiagnostics/zpa-qbcopypaste.png)
[]The Transaction Trend chart shows the number of transactions that occurred in the selected time range. By default, the chart shows the following transaction types, which you can deselect to narrow the focus of the chart:
- Total Transactions
- Error Transactions
- Successful Transactions
- Info Transactions
The trend of Info Transactions varies over time to reflect that user transactions have moved from an open state, for ongoing requests, to a closed state (Success).
Click **View Logs** to view the logs based on the date specified in the Transaction Trends chart and filtered by the top error.
![Transaction Trends Chart for User Activity in the Diagnostic page on the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/about-user-activity-diagnostics/zpa-useractivity-trends-transaction-options.png)
Click **Show Error Codes** to see the top errors for the selected time range. A list of errors appears below the chart. Hover over an error to see the total transactions in relation to the number of errors. You can drill down further to analyze by **Applications** or **App Connectors**. You can also view the logs filtered by the error and, if selected, by applications and App Connectors.
![Top Errors of Transaction Trends Chart for User Activity in the Diagnostic page on the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/about-user-activity-diagnostics/zpa-useractivity-trends-transaction-toperrors.png)
[]The Unique Users Trend chart shows the number of unique users in the selected time range.
![Unique Users Trends Chart for User Activity in the Diagnostic page on the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/about-user-activity-diagnostics/zpa-useractivity-trends-uniqueusers.png)
[]The Total Data Transferred Trend chart shows the total data received within the selected time range.
![Total Data Transferred Trend Chart for User Activity in the Diagnostic page on the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/about-user-activity-diagnostics/Total%20Data%20Transferred%20Trend.png)
[]The Unique Domains Trend chart shows the number of unique domains accessed by users in the selected time range.
![Unique Domains Trends Chart for User Activity in the Diagnostic page on the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/about-user-activity-diagnostics/zpa-useractivity-trends-uniquedomains.png)
[]The Policy Blocks Trend chart shows the number of policy blocks experienced by users in the selected time range.
[]The Reauth Blocks Trend chart shows the number of reauthorization blocks that occurred in the selected time range.
![Reauth Blocks Trends Chart for User Activity in the Diagnostic page on the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/about-user-activity-diagnostics/zpa-useractivity-trends-reauthblocks.png)
[]![Trend Chart options for User Activity in the Diagnostics page on the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/about-user-activity-diagnostics/zpa-diagnostics-trends-chartoptions.png)
[]![Zoom Out of a Trends Chart in the User Activity Diagnostics in the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/about-user-activity-diagnostics/zpa-useractivity-trends-zoomout.png)
[]
- **File Name**: The name of the file that was uploaded or downloaded.
- **Action**: Whether the file was downloaded or uploaded.
- **File Inspected**: The status of the inspected file.
For inspection to work, you need to have a privileged capabilities policy for the privileged console set to **Enable Inspection** and have Integrations for the Internet & SaaS Sandbox configured.
- **File Type**: The file type format that was uploaded (e.g., pdf, jpg, etc.).
- **MD5Hash**: The MD5 hash value for that specific file.
- **Status**: If the file was downloaded or uploaded, then the status shows as Success. If the file wasn’t downloaded or uploaded, then the status shows Denied.
If you expand a file, you can also see the following fields:
- **Start Time**: The date, time, and time zone that the upload started.
- **End Time**: The date, time, and time zone that the upload was completed.
There are also two additional fields for inspected files:
- **Inspection Time**: The amount of time that it took for the file to be inspected.
- **Inspection Verdict**: The details of the file’s inspection.
[See image.](#Fileswindow)
[]
[]![View the Sharing Users window for Privileged Remote Access](/downloads/zpa/dashboard-diagnostics/about-user-activity-diagnostics/Updated%20SessUserstable.png)