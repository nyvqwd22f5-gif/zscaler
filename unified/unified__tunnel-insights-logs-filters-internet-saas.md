# Tunnel Insights Logs: Filters for Internet & SaaS
Source: https://help.zscaler.com/unified/tunnel-insights-logs-filters-internet-saas
PDF: https://help.zscaler.com/pdf/com/en/1497381.pdf

Filters define the traffic information that you view in your Tunnel Insights Logs. To learn more about logs, see [About Insights Logs](/unified/about-insights-logs).
Certain filters, like** Users**, **Departments**, **Locations**, and others, support the selection of multiple values. For these, you can select up to 200 values in a single filter. You can also choose to include or exclude the selected values. Also, certain filters support additional operators (i.e., Does Not Contain, Does Not Start With, Does Not End With, Is Null, Is Not Null) for filters that perform string match, like **Threat Category** and others.
Following are the tunnel log filters you can select:
- **Extranet Name**: Use this filter to view the metrics associated with a specific extranet name. The default option for this filter is **Any**. You can search for a specific name.
- **Location**: Use this filter to view metrics associated with a specific [location](/unified/about-locations). The default option for this filter is **All**. You can search for specific locations.
- **Location Group**: Use this filter to view metrics associated with a specific [location group](/unified/about-location-groups). The default option for this filter is **None**. You can search for specific location groups.
- **Location Type**: Use this filter to view transactions associated with a specific location type. The default option for this filter is **None**. The following location types appear under this filter:
- Corporate User Traffic Group
- Guest Wifi Group
- IoT Traffic Group
- Server Traffic Group
- Unassigned Locations
- **Tunnel Destination IP**: Use this filter to view metrics associated with a destination IP address. If you want to filter by multiple IP addresses, you can enter:
- individual IP addresses separated by commas (e.g., 192.0.2.0, 192.0.2.1)
- a range of IP addresses (e.g., 192.0.2.0-192.0.2.100)
- a subnet mask (e.g., 192.0.2.0/24)
- **Tunnel Source IP**: Use this filter to view metrics associated with a source IP address. If you want to filter by multiple IP addresses, you can enter:
- individual IP addresses separated by commas (e.g., 192.0.2.0, 192.0.2.1)
- a range of IP addresses (e.g., 192.0.2.0-192.0.2.100)
- a subnet mask (e.g., 192.0.2.0/24)
- **Tunnel Type**: Use this filter to view metrics based on different types of tunnels. The default option for this filter is **All**. You can search for a specific tunnel type. The following types appear under this filter:
- All
- GRE
- IPSec
- **VPN Credential**: Use this filter to view metrics associated with a specific [VPN credential](/unified/about-vpn-credentials). The default option for this filter is **All**. You can search for specific VPN credentials.