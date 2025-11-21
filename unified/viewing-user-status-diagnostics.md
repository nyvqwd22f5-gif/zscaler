# Viewing User Status Diagnostics
Source: https://help.zscaler.com/unified/viewing-user-status-diagnostics
PDF: https://help.zscaler.com/pdf/com/en/1498056.pdf

You can view and filter user status and authentication data for past events.
Accessing User Status Diagnostics
To view diagnostics for user activity:
- Go to Diagnostics (Logs> Insights > Diagnostics).
- Under **Log Type**, choose **User Status**.
By default, the detailed status and authentication information for all users is displayed for events that occurred in the last 24 hours. To change the time range, click the **Calendar **menu and select a preset range or specify a custom start and end date. If you use a **Custom Range**, the start date must be within the last 14 days. To change the time zone, click the current **Time Zone** button.
Zscaler retains logs for rolling periods of at least 14 days during the Subscription Term. You can also view your logs or stream logs in real time using the [Log Streaming Service (LSS)](/unified/about-log-streaming-service). Data in the [dashboard](/unified/dashboard-diagnostics) might be more recent than the data presented within Diagnostics.
![User Status Time Range](/downloads/zpa/dashboard-diagnostics/about-user-authentication-diagnostics/zpa-userstatus-logtypeandtimerange.png)
Also, by default, the table displays the **Total** number of authentication requests made by users. You can change this by choosing one of the following filters:
- **Errors**: The total number of access errors.
- **Successful**: The total number of successful authentication requests.
![User Status Totals](/downloads/zpa/dashboard-diagnostics/about-user-authentication-diagnostics/zpa-userstatus-totals.png)
Filtering User Status Diagnostics
On the User Status page, you can apply filters or drill down further into the log data using the Query Builder. By default, no filters are applied. If you want to view and filter User Status for real-time events, use [Live Logs](/unified/about-live-logs).
To configure filters using the Query Builder:
- Click **Add Filters **and select a filter from the drop-down menu. To learn more, see [User Status Filters](#filterdata) below.
- Select a Boolean operator from the drop-down menu (e.g., **Contains**, **Ends With**, **Equals**, **Not Equals**, **Starts With**). The operators available are determined by the filter you are configuring.
- Select the fields from the drop-down menu or enter the values required for the filter. The field or value required is determined by the filter you are configuring.
Filters using the **Contains **operator allow a maximum of 7 entries. All filters using operators that require text input must use a semicolon (;) to separate multiple entries (e.g., 137; 138; 139). When configuring multiple text entries and using the **Less Than** operator, the results show transactions starting from the largest entry provided. When configuring multiple text entries and using the **Greater Than** operator, the results show transactions starting from the smallest entry provided.
- Click **Apply**.
![zpa-userstatus-qbexample.png](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/authUsersDiagnostics/zpa-userstatus-qbexample.png)
To apply more filters, click **Add Filters** again or click on the **Apply Filter** icon (![zpa-filtericon.png](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/authUsersDiagnostics/zpa-filtericon.png)
) within the table. To remove an added filter, click the **Close** icon then **Apply**. To remove all filters, click **Clear All**.
You can also click the **Copy** icon** **to save the filter query details. If you, or another admin, accesses **Diagnostics**, you can paste the query into the field by clicking the **Clipboard** icon.
[See image.](#QueryBuilder_CopyPaste)
[]User Status Filters
You can add the following filters:
- **Connection: Connection ID**: See logs by the ID associated with the authentication request.
- **Connection: Reason Code**: See logs that resulted in a specific reason code.
- **Connection: Status Code**: See logs with **Authenticated**, **Authentication Failed**, or **Disconnected **connections.
- **External Device ID**: See logs from users with the identifier that associates an external MDM device ID with devices in the Zscaler Client Connector Portal.
- **Hop Based Auth Logs**: See logs by the number of hops that occurred. Typically, hops occur when the session goes from Zscaler Client Connector to a Private Service Edge and then to a Public Service Edge managed by Zscaler.
- **Policy: IdP Name**: See requests from users authenticated by the Identity Provider (IdP) name, as configured in the Admin Portal.
- **Policy: Redirection Policy Name**: See logs of users by redirection policy name.
- **Private Service Edge Selection Method**: See logs of users by Private Service Edge Selection method.
- **Redirection Policy**: See logs of users that have redirection policy enabled.
- **Service Edge: Name (Public/Private)**: See logs for a specific Public Service Edge or Private Service Edge.
- **Service Edge: Type**: See logs by the Service Edge type (i.e., **Public** or **Private**).
- **User: Client Private IP**: See logs by client private IP address.
- **User: Client Public IP**: See logs by client public IP address.
- **User: Client Type**: See logs by the client type the user's device is connecting from (i.e., **Branch Connector**, **Zscaler Client Connector**, **Client Connector Partner**, **Web Browser**, **Web Browser Unauthenticated**, **Internet & SaaS Inspection**, or **Internet & SaaS Public Service Edge**).
- **User: Cname**: See logs by client CNAME.
- **User: Location**: See logs from users in a specific location.
- **User: Platform**: See logs from users on a specific platform.
- **User: Trusted Network**: See logs from users on a specific trusted network.
- **Username**: See logs for a particular username. This is the NameID in the SAML assertion from the IdP and not the username entered in Zscaler Client Connector.
- **Client-To-Client Enrolled**: Indicates whether the domain being accessed by the Zscaler Client Connector matches the regular expression or not. To learn more, see [Validating a Client Hostname](/unified/validating-client-hostname).
If you are using the [Log Streaming Service (LSS)](/unified/about-log-streaming-service), be aware that the Private Applications LSS Client user represents the LSS service, not an actual user. By default, Diagnostic information for the Private Applications LSS Client is captured but not displayed. You must explicitly select this from the **User** field to display its log information. Also, each log receiver is displayed as an application, to reflect the data coming in from the service. To learn more, including how to stop the LSS service from streaming Private Applications LSS Client logs, see [Configuring a Log Receiver](/unified/configuring-log-receiver#Step2).
[]The table displays the following data for authentication requests. You can expand each row to see more details or click the **Expand**/**Collapse** icon** **to expand or collapse all rows within the table. By default, the table displays 20 transactions. You can scroll to load more transactions.
- [Connection: Status Code](#status)
- [Auth Log Timestamp](#authlog)
- [Authentication Time](#auth_time)
- [Disconnect Time](#deauth_time)
- [Client](#name)
- [Service Edge](#connection)
Within the table, you can click the **Apply Filter** icon next to certain field names to drill down further into the data. The filter query section within the page updates automatically to include the proper filter for the field name you selected, along with the applicable Boolean operator configuration for that field.
[]Displays one of the following session status codes:
- **Authenticated**: Authenticated represents that an authenticated user has connected to Private Applications. This is true for first time authentication and subsequent reauthentications.
- **Authentication Failed**: The user was unable to authenticate.
- **Disconnected**: The user successfully disconnected.
For every status code, the following fields are displayed:
- **Client Type**: The name of the client the user's device is connecting from (i.e., **Branch Connector**, **Zscaler Client Connector**, **Client Connector Partner**, **Web Browser**, **Web Browser Unauthenticated**, **Internet & SaaS Inspection**, or **Internet & SaaS Public Service Edge**).
- **Client Version**: The version number of the client the user uses (e.g., the Zscaler Client Connector version on the user's device).
- **Connection ID**: The ID associated with the application request. You can click the **Copy** icon to copy the ID to your clipboard.
- **Redirection Policy Name**: The redirection policy name as configured in the Admin Portal. You can click on the name to open the [Edit Redirection Policy](/unified/editing-redirection-policies) window.
- **Private Service Edge Selection**: The Private Service Edge Selection method (e.g, Default, Preferred, or Always) associated with the user's redirection policy.
- **Client-To-Client Enrolled**: Indicates whether the domain being accessed by the Zscaler Client Connector matches the regular expression or not. To learn more, see [Validating a Client Hostname](/unified/validating-client-hostname).
- **Show Hop Details**: The hop logs for the session. You can click the link to view the hop logs. Sessions without a hop do not show this link.
There are two parts to every hop: the user's Zscaler Client Connector connecting to a Private Service Edge and then the Private Service Edge connecting to a Public Service Edge. The first part are the logs that already appear for the session. Click the link to view the log details for the second part of the hop. They appear below the session log.
[See image.](#hopdetails)
If there is a hop in the session, it shows a hop icon.
![User status diagnostics with session hops](/downloads/zpa/dashboard-diagnostics/about-user-authentication-diagnostics/show-hop-details-01.png)
- **Connection Status Log**: View, download, and copy the raw JSON for the request:
- Click the **View Log** icon to display the **Raw JSON** for the request within the Admin Portal.
- Click the **Download** icon to download the raw JSON for the request to a text (.txt) file.
- Click the **Copy** icon to copy the raw JSON text for the request to your clipboard.
[]![Hop details for the user status diagnostics](/downloads/zpa/dashboard-diagnostics/about-user-authentication-diagnostics/coneection-status-details-02.png)
[]The data and time when the log was generated. The column sorts requests by the date and time in descending order. You can click the **Arrow** icon to sort the requests in ascending order.
The time displayed is based on the time you choose for [your account setting](/unified/getting-started-zscaler/admin-portal-access-navigation) in the Admin Portal.
[]The time that the user authenticated. The column initially sorts requests based on the **Auth Log Timestamp** column date and time. You can click the **Arrow** icon to sort the table in ascending or descending order based on this column.
[]The time that the user disconnected. The column initially sorts requests based on the **Auth Log Timestamp** column date and time. You can click the **Arrow** icon to sort the table in ascending or descending order based on this column.
- []**Client Name**: The name of the client that the user authenticated or attempted to authenticate with.
- **Client IP**: The IP address associated with the client.
- **Private IP**: The private IP address of the client.
- **Zscaler IP**: The virtual IP that is assigned to Zscaler Client Connector for server-to-client connectivity.
- **Location**: The city and country the client is connecting from. If Private Applications is unable to determine the location, then the **Private IP** is shown.
- **Tx to Client**: See bytes transmitted by a Public Service Edge or Private Service Edge to a client.
- **Rx from Client**: See bytes received by a Public Service Edge or Private Service Edge from a client.
- **Tx to Private Service Edge**: See bytes transmitted by a Public Service Edge to a Private Service Edge.
- **Rx from Private Service Edge**: See bytes received by a Public Service Edge from a Private Service Edge.
- **User Metadata**: The metadata of the user who requested the application:
- **IdP Name**: The name of the IdP as configured in the Admin Portal.
- **IdP ID**: The ID associated with the IdP. You can click the **Copy** icon to copy the ID to your clipboard.
- **SAML Attributes**: View, download, and copy the SAML attributes for the user:
- Click the **View Log** icon to display the **SAML Attributes** for the user within the Admin Portal.
- Click the **Download** icon to download the SAML attributes statement for the user to a text (.txt) file.
- Click the **Copy** icon to copy the SAML attribute statement for the user to your clipboard.
- **SCIM Users**: The user that is provisioned for SCIM.
- **SCIM Groups**: The group that is provisioned for SCIM.
- **Hostname**: The hostname of the user's device.
- **Platform**: The platform on the user's device.
- **Client Connector Trusted Networks**: The names of the trusted networks accessible by the user's device.
- **Posture Profiles Verified**: If Zscaler Client Connector verified the user's device against the criteria specified in the posture profile, then TBD is displayed for this field.
- **Posture Profiles Unverified**: If Zscaler Client Connector was unable to verify the user's device against the criteria specified in the posture profile, then TBD is displayed for this field.
- **External Device ID**: See logs from users with the identifier that associates an external MDM device ID with devices in the Zscaler Client Connector Portal.
If you are using the [Log Streaming Service (LSS)](/zpa/about-log-streaming), be aware that the Private Applications LSS Client user represents the LSS service, not an actual user. By default, Diagnostic information for the Private Applications LSS Client is captured but not displayed. You must explicitly select this user from the **User** field to display its log information. Also, each log receiver is displayed as an application to reflect the data coming in from the service. To learn more, including how to stop the LSS service from streaming Private Applications LSS Client logs, see [Configuring a Log Receiver](/unified/configuring-log-receiver#Step2).
- []**Name**: The name of the Public Service Edge or Private Service Edge that processed the connection. If the Service Edge is a Private Service Edge, you can click on the name to open the [Edit Service Edge](/unified/editing-deployed-private-service-edge-for-private-applications) window.
Depending on who hosts the Service Edge (Zscaler or your organization), a different icon appears with the Service Edge name.
![The hosted service edge on the user status page](/downloads/zpa/dashboard-diagnostics/about-user-authentication-diagnostics/zpa-serviceedge-hostedby.png)
As part of setting up the TLS session, Zscaler hosted Public Service Edge directs the user's Zscaler Client Connector to connect with another Service Edge at a particular location. When this happens, a redirect icon (![Retarget service edge icon](/downloads/zpa/dashboard-diagnostics/about-user-authentication-diagnostics/zpa-retargeticon.png)
) appears next to the Service Edge name instead of the Service Edge icon above.​​​
- **ID**: The internal ID for the connection request for the Private Service Edge to the App Connector. You can click the **Copy** icon to copy the ID to your clipboard.
- **Group Name**: The name of the group that the Private Service Edge is included in. You can click on the name to open the [Edit Service Edge Group](/unified/editing-private-service-edge-groups-private-applications) window.
- **Group ID**: The internal ID for the Private Service Edge group. You can click the **Copy** icon to copy the ID to your clipboard.
- **Location**: The city or country where the Public Service Edge or Private Service Edge is located.
[]![zpa-qbcopypaste.png](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/authUsersDiagnostics/zpa-qbcopypaste.png)