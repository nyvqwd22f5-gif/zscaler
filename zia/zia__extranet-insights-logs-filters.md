# Extranet Insights Logs: Filters
Source: https://help.zscaler.com/zia/extranet-insights-logs-filters
PDF: https://help.zscaler.com/pdf/com/en/1507046.pdf

Filters define the traffic information that you view in your Extranet Insight Logs. To learn more about logs, see [About Insights Logs](/zia/about-insights-logs).
Certain filters, like** Users**, **Departments**, **Locations**, and others, support the selection of multiple values. You can select up to 200 values in a single filter. You can also choose to include or exclude the selected values. Some filters support additional operators (i.e., Does Not Contain, Does Not Start With, Does Not End With, Is Null, Is Not Null) for filters that perform string match.
Some filter combinations that appear together in Insights Logs when applied, don't appear together in Insights. For example, the **Department** and **Location** filters appear together in Insights Logs when applied, but don't appear together in Insights.
Following are the Extranet Insights Log filters that you can select:
- **Client Destination Name**: Use this filter to limit the data to traffic associated with a specific destination FQDN.
- **Client Source IP**: Use this filter to limit the data about traffic associated with a specific client source IP address. Choose **Match **and enter an IP address, a range of IP addresses, or an IP address and netmask, as shown in the examples below the text box.
- **Client Source Port**: Use this filter to limit the data to traffic associated with a specific client source port.
- **Client Tunnel IP**: Use this filter to limit the data to traffic associated with a specific client tunnel IP address.
- **Data Center**: Use this filter to limit the data to traffic associated with a specific data center.
- **Department**: Use this filter to limit the data to the traffic of a specific [department](/zia/about-departments). Use the Search function to find a specific department.
- **Device Appversion**: Use this filter to limit the data to the traffic of a specific device app version.
- **Device Hostname**: The hostname information from support devices. This filter is not available for admins with [device information obfuscation](/zia/obfuscating-device-information-admins) enabled.
- **Device Model**: Use this filter to view transactions associated with a specific device model. Enter all or part of the device model in the text field and an operator such as: **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **Device Name**: Use this filter to view transactions associated with a specific device name. Enter all or part of the device name in the text field and an operator such as: **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**. This filter is not available for admins with [device information obfuscation](/zia/obfuscating-device-information-admins) enabled.
- **Device Type**: Use this filter to view transactions associated with a specific device type.
- **Device Owner**: Use this filter to view transactions associated with a specific device owner. Enter all or part of the device owner in the text field and an operator such as: **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**. This filter is not available for admins with [device information obfuscation](/zia/obfuscating-device-information-admins) enabled.
- **Device Platform**: Use this filter to view transactions associated with a specific device platform. Enter all or part of the device model in the text field and an operator such as: **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **Enrolled Device appversion**: Use this filter to view transactions associated with a specific enrolled device app version. Enter all or part of the enrolled device app version in the text field and an operator such as: **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **External Device ID**: Use this filter to view transactions associated with a specific external device ID. Enter all or part of the device model in the text field and choose an operator such as: **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **Extranet Gateway IP**: Use this filter to view transactions associated with a specific extranet gateway IP address.
- **Extranet Gateway Port**: Use this filter to limit the data to the extranet gateway port. Enter a value from 1 to 65536.
- **Extranet Location**: Use this filter to view the transactions associated with a specific extranet location. The default option for this filter is **Any**. You can search for specific locations.
- **Extranet Location Port**: Use this filter to limit the data to the extranet location port.
- **Extranet Tunnel Data Center**: Use this filter to limit the data to the extranet tunnel data center.
- **Extranet Name**: Use this filter to limit the data to the business partner name configured by your organization.
- **Inbound Bytes**: Use this filter to limit the data to packets sent from the server to the client that were within a specific size range. The corresponding column shows the total inbound bytes for aggregated sessions, which were limited to the selected filter range. Choose a predefined range or specify a custom range.
- **Location**: Use this filter to limit the data to a location's traffic. Choose a location from the list of internet gateway locations specified in the Locations page. The list includes Road Warrior, the default location for transactions that did not originate from a predefined location. This filter lists 200 results at a time. Use the Search function to find a specific location.
- **Location Group**: Use this filter to limit the data to a location group’s traffic. Choose a location group from the list. Use the Search function to find a specific location group.3
- **Location Type**: Use this filter to limit the data to a specific location type. The default option for this filter is **None**. The following location types appear under this filter:
- Corporate User Traffic Group
- Guest Wifi Group
- IoT Traffic Group
- Server Traffic Group
- Unassigned Locations
- Workload Traffic Group
- **OS Type**: The OS type of the device.
- **OS Version**: The OS version the device uses.
- **Outbound Bytes**: Use this filter to limit the data to packets that were received by the server within a specific size range. The corresponding column shows the total outbound bytes for aggregated sessions, which were limited to the selected filter range. Choose a predefined range or specify a custom range.
- **Protocol**: Improve the visibility of protocols that traverse within Zscaler’s cloud. The default option for this filter is **None**. You can search for specific protocols. The following protocols appear under this filter:
- ICMP
- TCP
- UDP
- **Server Destination IP**: Use this filter to limit the data to traffic associated with a specific server destination IP address. Choose **Match **and enter an IP address, a range of IP addresses, or an IP address and netmask, as shown in the examples below the text box.
- **Server Destination Port**: Use this filter to limit the data to traffic associated with a specific server destination IP port.
- **Server Source IP**: Use this filter to limit the data to traffic associated with a specific server source IP address. Choose **Match **and enter an IP address, a range of IP addresses, or an IP address and netmask, as shown in the examples below the text box.
- **Server Source Port**: Use this filter to limit the data to traffic associated with a specific server source port.
- **Session Duration**: Use this filter to limit the data to traffic based on the session time.
- **Source Country**: Use this filter to limit the data to traffic associated with specific source countries.
- **Status**: Use this filter to limit the data to traffic associated with a specific status.
- **VPN Credentials**: Use this filter to view metrics associated with a specific VPN credential. The default option for this filter is **All**. You can search for specific VPN credentials.
- **User**: Use this filter to limit the data to the traffic of specific [users](/zia/about-users). Choose the user names from the list.