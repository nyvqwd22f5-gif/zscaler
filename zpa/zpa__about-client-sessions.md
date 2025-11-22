# About Client Sessions
Source: https://help.zscaler.com/zpa/about-client-sessions
PDF: https://help.zscaler.com/pdf/com/en/1484761.pdf

Every admin who signs in to the ZPA Admin Portal or authenticates using an API key has a unique session. Zscaler allows the termination of these sessions from the Client Sessions page. Only admins with the corresponding role can initiate a termination. To learn more, see [Configuring Administrator Roles](/zpa/configuring-administrator-roles#ClientSessions).
Client Sessions provide the following benefits and enable you to:
- View active client sessions for admins who sign in to the ZPA Admin Portal or authenticate using an API key.
- View and filter user activity and user status diagnostic logs.
About the Client Sessions Page
On the Client Sessions page (Configuration & Control > Administration Control > Client Sessions), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Client Sessions page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Select another filter to filter the information in the table. By default, the **API Key Name** filter is selected.
- View a list of all client sessions. For each session, you can see:
- **Admin ID**: The ID for the admin with a current session in the ZPA Admin Portal.
- **API Key Name**: The name of the API key for a current API session.
- **Client IP**: The IP address associated with the client. This only applies to an Admin ID.
- **Active Time**: The amount of time the current session has been active.
- **Expires In**: The amount of time until the current session ends.
- Delete a session.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Go to the [Administrators](/zpa/about-administrators) page to add new admins or manage existing admins.
- Go to the [Roles](/zpa/about-roles) page to add new admin roles or manage existing roles.
- Go to the [Audit Logs](/zpa/about-audit-logs) page to view and download admin audit log records.
- Go to the [Acceptable Use Policy](/zpa/about-user-portal-acceptable-use-policy) page to view or update the AUP for your [user portals](/zpa/user-portal).
- Go to the [Microtenants](/zpa/about-microtenants) page to add new Microtenants or manage existing Microtenants.
The Microtenants page is only visible for Default Microtenant admins.
- Go to the [Disaster Recovery](/zpa/understanding-disaster-recovery) page to view critical application segments, ZPA Private Service Edge groups, or App Connector groups that are designated for disaster recovery. You can also view and configure the [disaster recovery settings](/zpa/about-disaster-recovery-settings).
-
Go to the [Integrations](/zpa/about-integrations) page to set up File Transfer via Zscaler Internet Access (ZIA).
The Integrations page is read-only for [Microtenant](/zpa/about-microtenants) admins.
- Go to the [Client Connector IP Assignment](/zpa/about-client-connector-ip-assignment) page to manage Zscaler virtual IP addresses and view IP bindings for use with server-to-client connectivity.
![View the Client Sessions page](/downloads/zpa/administration/about-client-sessions/zpa-client-sessions-page.png)