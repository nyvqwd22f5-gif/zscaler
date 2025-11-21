# DNS Insights Logs: Filters
Source: https://help.zscaler.com/zia/dns-insights-logs-filters
PDF: https://help.zscaler.com/pdf/com/en/1400991.pdf

Filters define the DNS traffic information that you view in your DNS Insight Logs. To learn more about logs, see [About Insights Logs](/zia/about-insights-logs).
Certain filters, like** Users**, **Departments**, **Locations**, and others, support the selection of multiple values. For these, you can select up to 200 values in a single filter. You can also choose to include or exclude the selected values. Also, certain filters support additional operators (i.e., Does Not Contain, Does Not Start With, Does Not End With, Is Null, Is Not Null) for filters that perform string match, like **Threat Category** and others.
There are certain filter combinations that appear together in Insights Logs when applied, but won't appear together in Insights. For example, the **Department** and **Location** filters appear together in Insights Logs when applied, but won't appear together in Insights.
Following are the DNS log filters you can select:
- **Action**: Use this filter to limit the data to a specific action taken by your DNS Control policy.
- **Capture**: Use this filter to limit the data to view transactions that were captured into a PCAP file.
- **Client IP**: Use this filter to limit the data about traffic associated with a specific client IP address. Choose **Match **and enter an IP address, a range of IP addresses, or an IP address and netmask, as shown in the examples below the text box.
- **ECS Object Name**: Use this filter to limit the data to traffic associated with an ECS object.
- **ECS Prefix**: Use this filter to limit the data to traffic associated with the ECS prefix.ECS Prefix Length: Use this filter to limit the data to traffic associated with the
- **ECS prefix length**. Enter the prefix length in the **Min **and **Max **fields to view the logs within that range.
- **Data Center**: Use this filter to limit the data to traffic associated with a specific data center.
- **Department**: Use this filter to limit the data to the traffic of a specific department. It lists 200 results at a time. Use the Search function to find a specific department. You can choose to include or exclude certain departments.
- **Device Hostname**: The hostname information from support devices. This filter is not available for admins with [device information obfuscation](/zia/obfuscating-device-information-admins) enabled.
- **Device Model**: Use this filter to view transactions associated with a specific device model. Enter all or part of the device model in the text field and **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **Device Name**: Use this filter to view transactions associated with a specific device name. Enter all or part of the device name in the text field and **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**. This filter is not available for admins with [device information obfuscation](/zia/obfuscating-device-information-admins) enabled.
- **Device OS Type**: Use this filter to view transactions associated with a specific device OS type. Enter all or part of the device OS type in the text field and **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **Device OS Version**: Use this filter to view transactions associated with a specific device OS version. Enter all or part of the device OS version in the text field and **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **Device Owner**: Use this filter to view transactions associated with a specific device owner. Enter all or part of the device owner in the text field and **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**. This filter is not available for admins with [device information obfuscation](/zia/obfuscating-device-information-admins) enabled.
- **DNS Gateway Flags**: Use this filter to limit the data for DNS transactions that used a DNS Gateway. The following flags appear under this filter:
- Primary Server Attempted
- Secondary Server Attempted
- Query Forwarded to Destination
- Error Response Returned to Client
- Query Dropped
- **DNS Request Type**: Use this filter to limit the data to the traffic associated with a specific type of DNS Request. Choose the request type from the list.
- **DNS Response**: Use this filter to limit the data to the traffic associated with a specific DNS response. The following sub-filters appear:
- Resolved Name
- Resolved IPv4 Address
- Resolved IPv6 Address
- DNS Error Code
The following Zscaler internal error codes might appear in the DNS Error Code column:
- Empty_Resp
- Bypass
- Int_Error
- Srv_TimeOut
These codes are not listed under the DNS Error Code filter. Zscaler uses these error codes for diagnostic purposes. If you need further assistance, contact Zscaler Support.
- **DNS Tunnel & Network App Categories**: Use this filter to limit the data to traffic that comes from a specific tunneling or network application category. Use the search function to find a specific category.
- **DNS Tunnels & Network Apps**: Use this filter to view information about the type of tunnels and network applications used. Use the search function to find a specific application.
- **Enrolled Device appversion**: Use this filter to view transactions associated with a specific enrolled device app version. Enter all or part of the enrolled device app version in the text field and **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **HTTP Status Code**: Use this filter to limit the data to traffic associated with a HTTP status code.
- **Request Categories**: Use this filter to limit the data to the traffic associated with the request category of the requested domain.
- **Response Categories**: Use this filter to limit the data to the traffic associated with the response category of the response IP or the canonical name (CNAME).
- **Location**: Use this filter to limit the data to a location's traffic. Choose a location from the list of Internet gateway locations specified in the Locations page. The list includes Road Warrior, the default location for transactions that did not originate from a predefined location. This filter lists 200 results at a time. Use the Search function to find a specific location. You can choose to include or exclude certain locations.
- **Location Group**: Use this filter to limit the data to a location group’s traffic. Choose a location group from the list. Use the Search function to find a specific location group.
- **Location Type**: Use this filter to view transactions associated with a specific location type. The default option for this filter is **None**. The following location types appear under this filter:
- Corporate User Traffic Group
- Guest Wifi Group
- IoT Traffic Group
- Server Traffic Group
- Unassigned Locations
- Workload Traffic Group
- **Protocol Type**: Use this filter to limit data to TCP, UDP, or DNS over HTTP traffic.
- **Request Duration**: Use this filter to limit the data to the traffic associated with the specified request duration.
- **Requested Domain**: Use this filter to limit the data to the traffic associated with the domain for which DNS resolution was requested. Enter all or part of the domain in the text field and choose **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **Resolver Gateway**: Use this filter to limit the data to traffic associated with a resolver gateway.
- **Rule Name**: Use this filter to limit the data to specific rules in the firewall policy. Choose the rules from the list.
- **Server IP**: Use this filter to limit the data to traffic associated with a specific server IP address. Choose **Match **and enter an IP address, a range of IP addresses, or an IP address and netmask, as shown in the examples below the text box.
- **Server Port**: Use this filter to limit the data to traffic associated with a specific server port.
- **Server Protocol**: Use this filter to limit the data to traffic associated with a server protocol.
- **Show Delayed Logs**: Use this filter to limit the data to traffic based on delayed logs.
- **User**: Use this filter to limit the data to the traffic of specific users. Choose the usernames from the list. You can choose to include or exclude certain users.