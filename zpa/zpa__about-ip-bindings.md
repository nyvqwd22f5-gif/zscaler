# About IP Bindings
Source: https://help.zscaler.com/zpa/about-ip-bindings
PDF: https://help.zscaler.com/pdf/com/en/1485596.pdf

IP bindings indicate that the Zscaler IP address is bound to the client's destination device via Zscaler Client Connector. [Zscaler IP addresses](/zpa/about-client-connector-ip-assignment) are virtual IP addresses that are bound to the client's destination device for use with [server-to-client connectivity](/zpa/understanding-server-client-connectivity) or client-to-client connectivity over IP.
IP bindings provide the following benefits and enable you to:
- Review the Zscaler IP address associated with a client running Zscaler Client Connector for a server-to-client connection.
- Trace client devices by Zscaler IP addresses used for either server-to-client or client-to-client connectivity based on IP address.
- Use the Zscaler IP address to initiate IP-based connectivity from the tools on your internal server for server-initiated workflows.
To configure server-to-client connectivity based on IP, you must configure a Zscaler IP address and create application segments with the Zscaler IP address of the client that is creating the IP-based connection. To learn more, see [Configuring Server-To-Client Connectivity](/zpa/configuring-server-client-connectivity).
About the IP Bindings Page
On the IP Bindings page (Configuration & Control > Administration Control > Client Connector IP Assignment > IP Bindings), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the IP Bindings page to reflect the most current information.
- Download the IP bindings as a CSV file.
You cannot download the IP bindings as a CSV if the total number of records exceeds the maximum allowed limit of one million configured CSV records. Zscaler recommends applying filters to reduce the CSV record count so that the number of records is below the configured limit.
- Filter the IP binding information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- View a list of all IP bindings that are configured for your organization. For each IP binding, you can see:
- **Zscaler IP**: The Zscaler virtual IP address of the client's destination device. You can also click the **Sort **icon (![Reorder icon in the ZPA Admin Portal](/downloads/tech-pubs-drafts/zia-draft-articles/about-ip-bindings/zpa-reorder-icon-in-table-columns.png)
) to sort the **Zscaler IP** column in ascending order. Click the icon again to sort the column in descending order.
- **Range Name**: The name of the IP address ranges that are bound to the client's destination device.
- **Range Location**: The location of the IP address ranges that are bound to the client's destination device.
- **Username**: The username authenticated on the IP address ranges that are bound to the client's destination device. You can also click the **Sort **icon to sort the **Username** column in ascending order. Click the icon again to sort the column in descending order.
- **Platform**: The operating system of Zscaler Client Connector. You can also click the **Sort **icon to sort the **Platform** column in ascending alphabetical order. Click the icon again to sort the column in descending alphabetical order.
- **Client Hostname**: The FQDN for the server-to-client connection to Zscaler Client Connector.
- **Last Updated**: The date and time the IP binding was last updated.
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
- Go to the [IP Ranges](/zpa/about-client-connector-ip-assignment) page to add new IP address ranges or manage existing IP address ranges.
![Viewing the IP Bindings page](/downloads/zpa/administration/peer-peer-connectivity/about-ip-bindings/zpa-ip-bindings-page.png)