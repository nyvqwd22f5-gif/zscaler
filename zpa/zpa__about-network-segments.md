# About Network Segments
Source: https://help.zscaler.com/zpa/about-network-segments
PDF: https://help.zscaler.com/pdf/com/en/1529078.pdf

A Network segment is a local area network (LAN) IP subnet that is assigned to a [Network Connector group](/zpa/about-network-connector-groups) to define access to servers that are accessed via the VPN tunnel. Network segments define which traffic flows through the VPN tunnel from [Zscaler Client Connector](/client-connector/using-zscaler-client-connector). Each Network segment has a LAN IP address range for a data center with running servers. You can also assign an FQDN and domain name server to the Network segment. You can create multiple Network segments to define which traffic flows over the VPN tunnel. When you assign a Network segment to a Network Connector group, ensure that the Network Connector and the server associated with the LAN IP address are from the same data center.
Defining your Network segments enables you to:
- Define the traffic flow between Zscaler Client Connector and the server IP address.
- Handle exception traffic for transformation towards Zero Trust access.
About the Network Segments Page
On the Network Segments page (VPN (for Legacy Apps) > Network Segments > Network Segments), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Network Segments page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add a Network segment.](/zpa/configuring-network-segments)
- View a list of all Network segments that were configured for VPN for Legacy Apps. For each Network segment, you can see:
- **Name**: The name of the Network segment.
- **LAN IP Address**: The IP subnet associated with the Network segment that is assigned to the Network Connector group.
- **FQDN**: The fully qualified domain name (FQDN) assigned to this Network segment.
- **DNS Server**: The domain name server assigned to this Network segment.
- **Network Connector Group**: The Network Connector group this Network segment is assigned to.
- [Edit an existing Network segment](/zpa/editing-network-segments).
- Delete a Network segment.
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
![Network Segments page in the ZPA Admin Portal](/downloads/zpa/about-vpn-segments/Network%20Segments%20page%20w%20steps_0.png)