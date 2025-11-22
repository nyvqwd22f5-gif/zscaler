# About Network Connectors
Source: https://help.zscaler.com/unified/about-network-connectors
PDF: https://help.zscaler.com/pdf/com/en/1532370.pdf

VPN (for Legacy Apps) enables support for legacy applications that require server-to-client traffic using the real IP address binding (e.g., VoIP or Active FTP). This service uses [VPN Service Edges](/unified/about-vpn-service-edges), Network Connectors, [Network segments](/unified/about-network-segments), and Zscaler Client Connector. The Network Connector is deployed within your application server's data center, and connects to all known VPN Service Edges. Organizations must configure the route to the client IP pool using the Network Connector’s IP address as the next hop.
These VPN (for Legacy Apps) connections are only established if each entity (Network Connectors, VPN Service Edges, and Zscaler Client Connector) has the public and private key pairs of the other entities. You can configure a single Network Connector per Network Connector group.
Network Connectors provide the following benefits and enable you to:
- Build a secure a tunnel to the VPN (for Legacy Apps) gateway.
- Connect the applications as part of a Network Connector group to the VPN Service Edge.
The following platforms are supported for VPN (for Legacy Apps): Windows and macOS. Network Connectors can only be deployed with RHEL9 in the RPM format for Linux.
About the Network Connectors Page
On the Network Connectors page (Infrastructure > Private Access > Component > VPN (For Legacy Apps) > Network Connectors), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/unified/using-tables#filter).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Network Connectors page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/unified/using-tables#filter).
- [Add a new Network Connector.](/unified/configuring-network-connectors)
- Expand all of the rows in the table to see more information about each Network Connector.
- View a list of all deployed Network Connectors. Network Connectors that you've added, but have not deployed, are not listed. For each deployed Network Connector, you can see:
- **Name**: The name of the Network Connector. When expanded, the following information is displayed depending on the defined Network Connector:
- **Description**: The description of the Network Connector, if available.
- **Network Connector Group**: The Network Connector group that the Network Connector is a member of.
- **Package OS**: The compile time OS on which the .rpm binary is packaged (e.g., Linux).
- **Last Connection to Zscaler**: The last time the Network Connector connected to Zscaler.
- **Public IP**: The public IP address of the Network Connector. Disconnected Network Connectors show the last known public IP address.
- **Enrollment Certificate**: The certificate the Network Connector uses for enrollment.
- **Host Platform**: The platform that the Network Connector is deployed on (e.g., Linux).
- **Last Software Update**: The date and time the Network Connector was last updated to a newer software version.
- **Last Disconnect from Zscaler: **The last time the Network Connector disconnected from Zscaler.
- **Private IP**: The private IP address of the Network Connector. Disconnected Network Connectors show the last known private IP address.
- **Host OS**: The run time OS on which the Network Connector is running (e.g., Linux).
- **Public Service Edge**: The Public Service Edge for Private Applications that the Network Connector connects to.
- **Location**: The location where the Network Connector group that the Network Connector belongs to is set up.
- **Uptime**: The period of time the Network Connector is available for use. Disconnected Network Connectors are shown as **Not Available**.
- **Manager Version**: The current Network Connector Manager software version.
- **Current Software Version**: The current Network Connector software version.
- **Connection Status**: The status of the Network Connector connection.
- **Upgrade Status**: The status of the last Network Connector software update.
- **Status**: Indicates whether the Network Connector is enabled or disabled.
- [Edit the configuration of a deployed Network Connector.](/unified/editing-deployed-network-connector)
- Delete a deployed Network Connector configuration.
- Display more rows or a different page of the table.
![View and Manage Network Connectors within the Admin Portal](/downloads/unified/infrastructure/private-applications/infrastructure-components/vpn-legacy-apps/network-connectors/unified-network-connectors-page.png)