# About VPN Service Edges
Source: https://help.zscaler.com/unified/about-vpn-service-edges
PDF: https://help.zscaler.com/pdf/com/en/1532360.pdf

A VPN Service Edge manages the connections between Zscaler Client Connector and [Network Connectors](/unified/about-network-connectors). VPN Service Edges are a single-tenant instance, deployed in the Zscaler cloud. They are managed and maintained by Zscaler. The VPN Service Edge assigns Zscaler Client Connector the region and an IP address based on the client IP address pool that is assigned to the VPN Service Edge.
VPN Service Edges provide the following benefits and enable you to:
- Connect the user to the applications via a Network Connector.
- Define client IP pools that are assigned to users accessing the VPN Service Edge.
About the VPN Service Edges Page
On the VPN Service Edges page (Infrastructure > Private Access > Component > VPN (for Legacy Apps) > VPN Service Edges), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/unified/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the VPN Service Edges page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/unified/using-tables#filterData).
- [Add a new VPN Service Edge.](/unified/configuring-vpn-service-edges)
- View a list of all deployed VPN Service Edges. For each VPN Service Edge, you can see:
- **Name**: The name of the VPN Service Edge.
- **Region**: This is the location where the VPN Service Edge instance is hosted.
- **IP Address**: The IP address of the VPN Service Edge.
- **Operational Status**: Displays either **Down** or **Up**. If the status shown is **Down**, the VPN Service Edge is off. If the status shown is **Up**, the VPN Service Edge is on.
- **Status**: Displays one of the following statuses:
- **Disabled**: The VPN Service Edge connection is disabled.
- **Enrolling**: The VPN Service Edge connection is enrolling.
- **Enrolled**: The VPN Service Edge connection is enrolled.
- **Online**: The VPN Service Edge connection is online.
- **Unenrolling**: The VPN Service Edge connection is unenrolling.
- **Unhealthy**: The VPN Service Edge connection is online but new clients cannot use this connection.
- **Client Networks**: The IP address range that the VPN Service Edge uses to assign to Zscaler Client Connector.
- **Listener Port**: The listener port number that the VPN Service Edge listens on for connection requests from clients and Network Connectors.
-
**Next Periodic Software Update**: The date and time that the VPN Service Edge is scheduled to receive a software update. If an update window is not set, the software updates on Sunday at 2:00 AM UTC.
Zscaler strongly recommends scheduling updates to avoid service interruption when the device reboots during a software update.
- [Edit the VPN Service Edge](/unified/editing-vpn-service-edges).
- Delete the VPN Service Edge.
- [Modify the display of columns in the table](/unified/using-tables).
- Display more rows or a different page of the table.
![VPN Service Edges page in the Admin Portal](/downloads/zpa/vpn-legacy-apps/vpn-configuration/about-vpn-service-edges/VPN-Service-Edges-page-w-steps-software-update_1.png)