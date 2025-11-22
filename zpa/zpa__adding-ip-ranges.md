# Adding IP Ranges
Source: https://help.zscaler.com/zpa/adding-ip-ranges
PDF: https://help.zscaler.com/pdf/com/en/1485601.pdf

Configuring an [IP range](/zpa/about-client-connector-ip-assignment) allows an admin to create a virtual IP address range that is assigned to Zscaler Client Connector. The virtual IP address range is considered the Zscaler IP address, and is used for [server-to-client connectivity](/zpa/understanding-server-client-connectivity) based on IP address. To use this in Zscaler Private Access (ZPA), complete the following steps.
To configure an IP address range:
- Go to **Configuration & Control **> **Administration Control** > **Client Connector IP Assignment** > **IP Ranges**.
- Click **Add**.
The **Add IP Range** window appears.
- In the **Add IP Range **window:
- **Name**: Enter the name of the IP address range.
- **Status**: Select the status of the IP address range (**Enabled** or **Disabled**). By default, this is **Enabled**.
Active IP addresses are unavailable to your users after you disable them.
- **IP Range or IP Subnet**: Indicates if an IP address range or IP address subnet is used. By default, **IP Range** is selected.
- **IP Range**: The beginning and ending IP address range used for server-to-client connectivity. This field is only visible if **IP Range** is selected for **IP Range or IP Subnet**. The beginning IP address range must be less than or equal to the ending IP address range.
- **IP Subnet**: The IP address subnet in Classless Inter-Domain Routing (CIDR) notation used for server-to-client connectivity. This field is only visible if **IP Subnet** is selected for **IP Range or IP Subnet**.
IPv6 IP address ranges and IPv6 IP address subsets are not supported. IP address ranges must be non-overlapping. Zscaler recommends that the IP address ranges are broad enough to cover your endpoints based on geolocation criteria. Otherwise, the IP address from another available IP address range is assigned.
- **Description**: Enter the description of the IP address range.
- **IP Range Location**: Enter the location of the IP address range. The map displays the location you've entered. If you click the location marker on the map, the **Latitude**, **Longitude**, **Country Code**, and **Location Details** fields are automatically populated.
- **Latitude**: Displays the latitude coordinate.
- **Longitude**: Displays the longitude coordinate.
- **Country Code**: Displays the country code for the location address you've entered.
- **Location Details**: Displays the location address you've entered.
- **Send Location Hint to Client Connector**: (Optional) Select the checkbox to enter a location hint. The location hint is sent along with a Zscaler IP address to Zscaler Client Connector if it is configured. If Zscaler Client Connector receives the location hint, Zscaler Client Connector creates a pseudo network adapter and applies the location hint to the name of the adapter for the [System Center Configuration Manager](/zpa/supporting-microsoft-sccm) (SCCM) location boundary.
![Add IP Range window in the ZPA Admin Portal](/downloads/tech-pubs-drafts/zpa-draft-articles/adding-ip-ranges/zpa-adding-ip-ranges.png)
- Click **Save**.