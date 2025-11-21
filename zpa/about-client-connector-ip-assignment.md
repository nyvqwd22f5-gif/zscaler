# About Client Connector IP Assignment
Source: https://help.zscaler.com/zpa/about-client-connector-ip-assignment
PDF: https://help.zscaler.com/pdf/com/en/1485591.pdf

Client Connector IP Assignment controls the Zscaler virtual IP addresses assigned to clients during connectivity to the Zero Trust Exchange. These IP addresses do not appear in the Zscaler Client Connector interface list, but are unique IP addresses within each Zscaler Client Connector. These virtual IP addresses are used for [server-to-client connectivity](/zpa/understanding-server-client-connectivity) and client-to-client connectivity where applications cannot use FQDNs to connect. For server-to-client connectivity, these IP address ranges must be non-overlapping and routed to the Branch Connector or Cloud Connector as the next hop router.
Zscaler Client Connector IP assignment provides the following benefits and enables you to:
- Assign Zscaler virtual IP addresses to Zscaler Client Connector.
- Complete the first step to configure a server-to-client connection.
To configure server-to-client connectivity, you must configure an IP address range and create application segments with the Zscaler virtual IP address of the client that is creating the IP-based connection. To learn more, see [Configuring Server-to-Client Connectivity](/zpa/configuring-server-client-connectivity).
About the IP Ranges Page
On the IP Ranges page (Configuration & Control** **> Administration Control > Client Connector IP Assignment > IP Ranges), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the IP Ranges page to reflect the most current information.
- Filter the IP address range information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add an IP address range](/zpa/adding-ip-ranges).
- Expand all of the rows in the table to see more information about each IP address range.
- View a list of all IP address ranges that are configured for your organization. For each IP address range, you can see:
- **Name**: The unique name of the IP address range. You can also click the **Sort **icon (![Reorder icon in the ZPA Admin Portal](/downloads/tech-pubs-drafts/zpa-draft-articles/about-client-connector-ip-assignment/zpa-reorder-icon-in-table-columns.png)
) to sort the **Name** column in ascending order. Click the icon again to sort the column in descending order.
- **IP Range or IP Subnet**: The IP address ranges or IP address subnets of the client or destination device.
- **Location Details**: The location that is bound to the IP range in the following format: City, State, Country.
- **Total IPs**: The total number of IP addresses in the range.
- **Used IPs**: The total number of IP addresses currently used.
- **Status**: The status of the IP range (**Enabled **or **Disabled**). You can also click the **Sort** icon to sort the **Status **column in ascending order. Click the icon again to sort the column in alphabetical order.
- Enable an existing disabled IP address range. Enabling a disabled IP address range opens the **Enable IP Range **window. Click **Enable** to proceed.
- Copy an existing IP address range. Copying an existing IP address range opens the **Add IP Range** window with duplicate details of the selected IP range.
- [Edit an existing IP address range](/zpa/editing-ip-ranges).
- Delete an IP address range.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Go to the [Administrators](/zpa/about-administrators) page to add new admins or manage existing admins.
- Go to the [Roles](/zpa/about-roles) page to add new admin roles or manage existing roles.
- Go to the [Audit Logs](/zpa/about-audit-logs) page to view and download admin audit log records.
- Go to the [Acceptable Use Policy](/zpa/about-user-portal-acceptable-use-policy) page to view or update the AUP for your [user portals](/zpa/user-portal).
- Go to the [Microtenants](/zpa/about-microtenants) page to add new Microtenants or manage existing Microtenants.
The Microtenants page is only visible for Default Microtenant admins.
- Go to the [Client Sessions](/zpa/about-client-sessions) page to view or delete current sessions.
- Go to the [Disaster Recovery](/zpa/understanding-disaster-recovery) page to view critical application segments, ZPA Private Service Edge groups, or App Connector groups that are designated for disaster recovery.
-
Go to the [Integrations](/zpa/about-integrations) page to set up File Transfer via Zscaler Internet Access (ZIA).
The Integrations page is read-only for [Microtenant](/zpa/about-microtenants) admins.
- Go to the [IP Bindings](/zpa/about-ip-bindings) page to view and download the IP addresses bound to Zscaler Client Connector.
![Viewing the IP Ranges page ](/downloads/zpa/administration/peer-peer-connectivity/configuring-server-client-connectivity/zpa-client-ip-assignment-ip-ranges-page-blur-ip.png)
IP address ranges must be non-overlapping. Zscaler recommends that IP address ranges are broad enough to cover your endpoints based on geolocation criteria. Otherwise, the IP address from another available IP address range is assigned.