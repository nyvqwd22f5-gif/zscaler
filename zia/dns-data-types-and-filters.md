# DNS Data Types and Filters
Source: https://help.zscaler.com/zia/dns-data-types-and-filters
PDF: https://help.zscaler.com/pdf/com/en/1399516.pdf

There are two ways you work with DNS data types and filters to define the web traffic information that you want to view: in a dashboard or report [widget](/zia/what-widget), or when analyzing charts on an Insights page. To learn more about how to analyze your Insights traffic, see [Analyzing Traffic Using Insights](/zia/analyzing-traffic-using-insights).
When you add or edit a widget in a [dashboard](/zia/about-dashboards) or [report](/zia/about-interactive-reports) and select DNS in the Widget Settings dialog, you select a data type to view from the Data Type menu and apply filters that you choose from the Add Filter menu.
[See image.](#seeimage1)
In the Analytics >** **DNS Insights page, you select a data type to view from the menu above the chart and apply filters that you choose from the Add Filter menu on the left pane.
[See image.](#seeimage2)
Data Types and Filters
Certain filters, like** **Users, Departments, Locations, and others, support the selection of multiple values. For these, you can select up to 200 values in a single filter. You can also choose to include or exclude the selected values.
There are certain filter combinations that won't appear together in Insights, but appear together in Insights Logs. For example, the Department and Location filters don't appear together in Insights, but appear together in Insights Logs when applied.
Certain data types only appear on the DNS Insights page and not on the Dashboard > New Widget window. The following are the DNS data types and their associated filters that appear on both the pages:
- [Action](#action)
- [Department](#department)
- [DNS Tunnel & Network App Categories](#networkappcat)
- [DNS Tunnels & Network Apps](#networkapp)
- [IP Domain Category](#IP-domain-category)
- [Location](#location)
- [Location Group](#location-group)
- [Location Type](#location-type)
- [Overall Traffic](#overall-traffic)
- [Rule Name](#rule-name)
- [User](#user)
The following are the DNS data types that only appear on the DNS Insights page:
- [Client IP](#client-IP)
- [Server IP](#SIP)
[]Displays data about the action that the service took on your organization's traffic. You can view either the number of sessions or bytes. You can apply the following filters:
- **Action**: Use this filter to limit the data to a specific action taken by your DNS Control policy. You can search for a specific action.
- **Department**: Use this filter to limit the data to the traffic of a specific department. It lists 200 results at a time. You can search for a specific department. You can choose to include or exclude certain departments.
- **DNS Tunnel & Network App Categories**:** **Use this filter to limit the data to traffic that comes from a specific tunneling or network application category. You can search for a specific category.
- **DNS Tunnels & Network Apps**:** **Use this filter to view information about the type of tunnels and network applications used. You can search for a specific application.
- **IP Domain Category**:** **Use this filter to limit the data to the traffic associated with the URL category of the requested domain. You can search for a specific category.
- **Location**: Use this filter to limit the data to a location's traffic. Choose a location from the list of Internet gateway locations specified in the Locations page. The list includes **Road Warrior**, the default location for transactions that did not originate from a predefined location. This filter lists 200 results at a time. You can search for a specific location. You can choose to include or exclude certain locations.
- **Location Group**: Use this filter to limit the data to the traffic of a specific location group. You can search for a specific location group.
- **Location Type**: Use this filter to limit the data to a specific location type. The default option for this filter is **None**. The following location types appear under this filter:
- Corporate User Traffic Group
- Guest Wifi Group
- IoT Traffic Group
- Server Traffic Group
- Unassigned Locations
- Workload Traffic Group
- **Rule Name**: Use this filter to limit the data to specific rules in the DNS policy. You can search for a specific rule.
- **User**: Use this filter to limit the data to the traffic of specific users. You can search for a specific user. You can choose to include or exclude certain users.
[]Displays data on the traffic associated with a specific client IP address. You can apply the following filters:
- **Action**: Use this filter to limit the data to a specific action taken by your DNS Control policy. You can search for a specific action.
- **Client IP**: Use this filter to view data about traffic associated with a specific client IP address.
- **Department**: Use this filter to limit the data to the traffic of a specific department. It lists 200 results at a time. You can search for a specific department. You can choose to include or exclude certain departments.
- **Device Hostname**: The hostname of the device.
- **Device Model**: The model of the device.
- **Device Name**: The name of the device.
- **Device OS Type**: The OS type of the device.
- **Device OS Version**: The OS version the device uses.
- **Device Owner**: The owner of the device.
- **DNS Request Type**: Use this filter to limit the data to the traffic associated with a specific type of DNS request. You can search for a specific request type.
- **DNS Response**: Use this filter to limit the data to the traffic associated with a specific DNS response.
- **DNS Tunnel & Network App Categories**:** **Use this filter to limit the data to traffic that comes from a specific tunneling or network application category. You can search for a specific category.
- **DNS Tunnels & Network Apps**:** **Use this filter to view information about the type of tunnels and network applications used. You can search for a specific application.
- **IP Domain Category**: Use this filter to limit the data to the traffic associated with the URL category of the requested domain. You can search for a specific category. You can search for a specific category.
- **Location**: Use this filter to limit the data to a location's traffic. Choose a location from the list of Internet gateway locations specified in the Locations page. The list includes **Road Warrior**, the default location for transactions that did not originate from a predefined location. This filter lists 200 results at a time. You can search for a specific location. You can choose to include or exclude certain locations
- **Location Group**: Use this filter to limit the data to the traffic of a specific location group. You can search for a specific location group.
- **Request Duration**: Use this filter to limit the data to the traffic associated with the specified request duration.
- **Requested Domain**: Use this filter to limit the data to the traffic associated with the domain for which DNS resolution was requested. Enter all or part of the domain in the text field and choose **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **Rule Name**: Use this filter to limit the data to specific rules in the DNS policy. You can search for a specific rule name.
- **Server IP**: Use this filter to limit the data to traffic associated with a specific server IP address.
- **Server Port**: Use this filter to limit the data to traffic associated with a specific server port.
- **Show Delayed Logs**: Use this filter to limit the data to traffic associated with delayed logs.
- **User**: Use this filter to limit the data to the traffic of specific users. You can search for a specific user. You can choose to include or exclude certain users.
[]Displays data on the traffic associated with a specific department. You can apply the filters listed below.
- **Action**: Use this filter to limit the data to a specific action taken by your DNS Control policy. You can search for a specific action.
- **Client IP**: Use this filter to view data about traffic associated with a specific client IP address.
- **Department**: Use this filter to limit the data to the traffic of a specific department. It lists 200 results at a time. You can search for a specific department. You can choose to include or exclude certain departments.
- **Device Hostname**: The hostname of the device.
- **Device Model**: The model of the device.
- **Device Name**: The name of the device.
- **Device OS Type**: The OS type of the device.
- **Device OS Version**: The OS version the device uses.
- **Device Owner**: The owner of the device.
- **DNS Request Type**: Use this filter to limit the data to the traffic associated with a specific type of DNS request. You can search for a specific request type.
- **DNS Response**: Use this filter to limit the data to the traffic associated with a specific DNS response.
- **DNS Tunnel & Network App Categories**:** **Use this filter to limit the data to traffic that comes from a specific tunneling or network application category. You can search for a specific category.
- **DNS Tunnels & Network Apps**:** **Use this filter to view information about the type of tunnels and network applications used. You can search for a specific application.
- **Enrolled Device appversion**: Use this filter to limit the data to the app version of the enrolled device.
- **IP Domain Category**: Use this filter to limit the data to the traffic associated with the URL category of the requested domain. You can search for a specific category.
- **Protocol Type**:** **Use this filter to limit data to TCP, UDP, or DNS over HTTP traffic.
- **Request Duration**: Use this filter to limit the data to the traffic associated with the specified request duration.
- **Requested Domain**: Use this filter to limit the data to the traffic associated with the domain for which DNS resolution was requested. Enter all or part of the domain in the text field and choose **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **Rule Name**: Use this filter to limit the data to specific rules in the DNS policy. You can search for a specific rule.
- **Server IP**: Use this filter to limit the data to traffic associated with a specific server IP address.
- **Server Port**: Use this filter to limit the data to traffic associated with a specific server port.
- **Show Delayed Logs**: Use this filter to limit the data to traffic associated with delayed logs.
- **User**: Use this filter to limit the data to the traffic of specific users. You can search for a specific user. You can choose to include or exclude certain users.
[]Displays data on the traffic associated with a specific IP Domain category. You can apply the following filters:
- **Action**: Use this filter to limit the data to a specific action taken by your DNS Control policy. You can search for a specific action.
- **Department**: Use this filter to limit the data to the traffic of a specific department. It lists 200 results at a time. You can search for a specific department. You can choose to include or exclude certain departments.
- **IP Domain Category**: Use this filter to limit the data to the traffic associated with the URL category of the requested domain. You can search for a specific category.
- **Location**: Use this filter to limit the data to a location's traffic. Choose a location from the list of Internet gateway locations specified in the Locations page. The list includes **Road Warrior**, the default location for transactions that did not originate from a predefined location. This filter lists 200 results at a time. You can search for a specific location. You can choose to include or exclude certain locations.
- **Location Group**: Use this filter to limit the data to the traffic of a specific location group. You can search for a specific location group.
- **Location Type**: Use this filter to limit the data to a specific location type. The default option for this filter is **None**. The following location types appear under this filter:
- Corporate User Traffic Group
- Guest Wifi Group
- IoT Traffic Group
- Server Traffic Group
- Unassigned Locations
- Workload Traffic Group
- **User**: Use this filter to limit the data to the traffic of specific users. You can search for a specific user. You can choose to include or exclude certain users.
[]Displays data about a location's DNS traffic. You can apply the following filters:
- **Action**: Use this filter to limit the data to a specific action taken by your DNS Control policy. You can search for a specific action.
- **Client IP**: Use this filter to view data about traffic associated with a specific client IP address.
- **Device Hostname**: The hostname of the device.
- **Device Model**: The model of the device.
- **Device Name**: The name of the device.
- **Device OS Type**: The OS type of the device.
- **Device OS Version**: The OS version the device uses.
- **Device Owner**: The owner of the device.
- **DNS Request Type**: Use this filter to limit the data to the traffic associated with a specific type of DNS request. You can search for a specific request type.
- **DNS Response**: Use this filter to limit the data to the traffic associated with a specific DNS response.
- **DNS Tunnel & Network App Categories**:** **Use this filter to limit the data to traffic that comes from a specific tunneling or network application category. You can search for a specific category.
- **DNS Tunnels & Network Apps**:** **Use this filter to view information about the type of tunnels and network applications used. You can search for a specific application.
- **Enrolled Device appversion**: Use this filter to limit the data to the app version of the enrolled device.
- **IP Domain Category**: Use this filter to limit the data to the traffic associated with the URL category of the requested domain. You can search for a specific category.
- **Location**: Use this filter to limit the data to a location's traffic. Choose a location from the list of Internet gateway locations specified in the Locations page. The list includes **Road Warrior**, the default location for transactions that did not originate from a predefined location. This filter lists 200 results at a time. You can search for a specific location. You can choose to include or exclude certain locations.
- **Location Group**: Use this filter to limit the data to the traffic of a specific location group. You can search for a specific location group.
- **Location Type**: Use this filter to limit the data to a specific location type. The default option for this filter is **None**. The following location types appear under this filter:
- Corporate User Traffic Group
- Guest Wifi Group
- IoT Traffic Group
- Server Traffic Group
- Unassigned Locations
- Workload Traffic Group
- **Protocol Type**:** **Use this filter to limit data to TCP, UDP, or DNS over HTTP traffic.
- **Request Duration**: Use this filter to limit the data to the traffic associated with the specified request duration.
- **Requested Domain**: Use this filter to limit the data to the traffic associated with the domain for which DNS resolution was requested. Enter all or part of the domain in the text field and choose **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **Rule Name**: Use this filter to limit the data to specific rules in the DNS policy. You can search for a specific rule name.
- **Server IP**: Use this filter to limit the data to traffic associated with a specific server IP address.
- **Server Port**: Use this filter to limit the data to traffic associated with a specific server port.
- **Show Delayed Logs**: Use this filter to limit the data to traffic associated with delayed logs.
- **User**: Use this filter to limit the data to the traffic of specific users. You can search for a specific user. You can choose to include or exclude certain users.
[]Displays data about the traffic associated with a specific location group. You can apply the following filters:
- **Action**: Use this filter to limit the data to a specific action taken by your DNS Control policy. You can search for a specific action.
- **DNS Tunnel & Network App Categories**: Use this filter to limit the data to traffic that comes from a specific tunneling or network application category. You can search for a specific category.
- **DNS Tunnels & Network Apps**: Use this filter to view information about the type of tunnels and network applications used. You can search for a specific application.
- **IP Domain Category**: Use this filter to limit the data to the traffic associated with the URL category of the requested domain. You can search for a specific category.
- **Location**: Use this filter to limit the data to a location's traffic. Choose a location from the list of Internet gateway locations specified in the Locations page. The list includes **Road Warrior**, the default location for transactions that did not originate from a predefined location. This filter lists 200 results at a time. You can search for a specific location. You can choose to include or exclude certain locations.
- **Location Group**: Use this filter to limit the data to the traffic of a specific location group. You can search for a specific location group.
- **Location Type**: Use this filter to limit the data to a specific location type. The default option for this filter is **None**. The following location types appear under this filter:
- Corporate User Traffic Group
- Guest Wifi Group
- IoT Traffic Group
- Server Traffic Group
- Unassigned Locations
- Workload Traffic Group
- **Rule Name**: Use this filter to limit the data to specific rules in the DNS policy. You can search for a specific rule name.
- **User**: Use this filter to limit the data to the traffic of specific users. You can search for a specific user. You can choose to include or exclude certain users.
[]Displays data about the traffic associated with a specific location type. You can apply the following filters:
- **Action**: Use this filter to limit the data to a specific action taken by your DNS Control policy. You can search for a specific action.
- **DNS Tunnel & Network App Categories**: Use this filter to limit the data to traffic that comes from a specific tunneling or network application category. You can search for a specific category.
- **DNS Tunnels & Network Apps**: Use this filter to view information about the type of tunnels and network applications used. You can search for a specific application.
- **IP Domain Category**: Use this filter to limit the data to the traffic associated with the URL category of the requested domain. You can search for a specific category.
- **Location**: Use this filter to limit the data to a location's traffic. Choose a location from the list of Internet gateway locations specified in the Locations page. The list includes **Road Warrior**, the default location for transactions that did not originate from a predefined location. This filter lists 200 results at a time. You can search for a specific location. You can choose to include or exclude certain locations.
- **Location Group**: Use this filter to limit the data to the traffic of a specific location group. You can search for a specific location group.
- **Location Type**: Use this filter to limit the data to a specific location type. The default option for this filter is **None**. The following location types appear under this filter:
- Corporate User Traffic Group
- Guest Wifi Group
- IoT Traffic Group
- Server Traffic Group
- Unassigned Locations
- Workload Traffic Group
- **Rule Name**: Use this filter to limit the data to specific rules in the DNS policy. You can search for a specific rule name.
- **User**: Use this filter to limit the data to the traffic of specific users. You can search for a specific user. You can choose to include or exclude certain users.
[]Displays data about the overall traffic for the selected time period. You can apply the following filters:
- **Action**: Use this filter to limit the data to a specific action taken by your DNS Control policy. You can search for a specific action.
- **Department**: Use this filter to limit the data to the traffic of a specific department. It lists 200 results at a time. You can search for a specific department. You can choose to include or exclude certain departments.
- **DNS Tunnel & Network App Categories**:** **Use this filter to limit the data to traffic that comes from a specific tunneling or network application category. You can search for a specific category.
- **DNS Tunnels & Network Apps**:** **Use this filter to view information about the type of tunnels and network applications used. You can search for a specific application.
- **IP Domain Category**:** **Use this filter to limit the data to the traffic associated with the URL category of the requested domain. You can search for a specific category.
- **Location**: Use this filter to limit the data to a location's traffic. Choose a location from the list of Internet gateway locations specified in the Locations page. The list includes **Road Warrior**, the default location for transactions that did not originate from a predefined location. This filter lists 200 results at a time. You can search for a specific location. You can choose to include or exclude certain locations.
- **Location Group**: Use this filter to limit the data to the traffic of a specific location group. You can search for a specific location group.
- **Location Type**: Use this filter to limit the data to a specific location type. The default option for this filter is **None**. The following location types appear under this filter:
- Corporate User Traffic Group
- Guest Wifi Group
- IoT Traffic Group
- Server Traffic Group
- Unassigned Locations
- Workload Traffic Group
- **Rule Name**: Use this filter to limit the data to specific rules in the DNS policy. You can search for a specific rule.
- **User**: Use this filter to limit the data to the traffic of specific users. You can search for a specific user. You can choose to include or exclude certain users.
[]Displays data about traffic associated with specific rules in the DNS Control policy. You can apply the following filters:
- **Action:** Use this filter to limit the data to traffic that was either allowed or blocked due to the DNS policy. You can search for a specific action.
- **Department**: Use this filter to limit the data to the traffic of a specific department. It lists 200 results at a time. You can search for a specific department. You can choose to include or exclude certain departments.
- **Location:** Use this filter to limit the data to a location's traffic. Choose a location from the list of Internet gateway locations specified in the Locations page. The list includes **Road Warrior**, the default location for transactions that did not originate from a predefined location. This filter lists 200 results at a time. You can search for a specific location.
- **Location Group**: Use this filter to limit the data to the traffic of a specific location group. You can search for a specific location group.
- **Location Type**: Use this filter to limit the data to a specific location type. The default option for this filter is **None**. The following location types appear under this filter:
- Corporate User Traffic Group
- Guest Wifi Group
- IoT Traffic Group
- Server Traffic Group
- Unassigned Locations
- Workload Traffic Group
- **Rule Name**: Use this filter to limit the data to specific rules in the DNS policy. You can search for a specific rule name.
- **User**: Use this filter to limit the data to the traffic of specific users. You can search for a specific user. You can choose to include or exclude certain users.
[]Displays data about traffic associated with a destination server. The pie chart and trend line are unavailable for this data type. You can apply the following filters:
- For the full filter list, see [DNS Insights Logs: Filters](/zia/dns-insights-logs-filters).
[]Displays data about traffic associated with a specific user. You can apply the following filters:
- **Action**: Use this filter to limit the data to a specific action taken by your DNS Control policy.
- **Client IP**: Use this filter to view data about traffic associated with a specific client IP address.
- **Department**: Use this filter to limit the data to the traffic of a specific department. It lists 200 results at a time. You can search for a specific department. You can choose to include or exclude certain departments.
- **Device Hostname**: The hostname of the device.
- **Device Model**: The model of the device.
- **Device Name**: The name of the device.
- **Device OS Type**: The OS type of the device.
- **Device OS Version**: The OS version the device uses.
- **Device Owner**: The owner of the device.
- **DNS Request Type**: Use this filter to limit the data to the traffic associated with a specific type of DNS request. You can search for a specific request type.
- **DNS Response**: Use this filter to limit the data to the traffic associated with a specific DNS response.
- **DNS Tunnel & Network App Categories**:** **Use this filter to limit the data to traffic that comes from a specific tunneling or network application category. You can search for a specific category.
- **DNS Tunnels & Network Apps**:** **Use this filter to view information about the type of tunnels and network applications used. You can search for a specific application.
- **Enrolled Device appversion**: Use this filter to limit the data to the app version of the enrolled device.
- **IP Domain Category**: Use this filter to limit the data to the traffic associated with the URL category of the requested domain. You can search for a specific category.
- **Location**: Use this filter to limit the data to a location's traffic. Choose a location from the list of Internet gateway locations specified in the Locations page. The list includes **Road Warrior**, the default location for transactions that did not originate from a predefined location. This filter lists 200 results at a time. You can search for a specific location.
- **Location Group**: Use this filter to limit the data to the traffic of a specific location group. You can search for a specific location group.
- **Location Type**: Use this filter to limit the data to a specific location type. The default option for this filter is **None**. The following location types appear under this filter:
- Corporate User Traffic Group
- Guest Wifi Group
- IoT Traffic Group
- Server Traffic Group
- Unassigned Locations
- Workload Traffic Group
- **Request Duration**: Use this filter to limit the data to the traffic associated with the specified request duration.
- **Requested Domain**: Use this filter to limit the data to the traffic associated with the domain for which DNS resolution was requested. Enter all or part of the domain in the text field and choose **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **Rule Name**: Use this filter to limit the data to specific rules in the DNS policy. You can search for a specific rule name.
- **Server IP**: Use this filter to limit the data to traffic associated with a specific server IP address.
- **Server Port**: Use this filter to limit the data to traffic associated with a specific server port.
- **Show Delayed Logs**: Use this filter to limit the data to traffic associated with delayed logs.
- **User**: Use this filter to limit the data to the traffic of specific users. You can search for a specific user. You can choose to include or exclude certain users. If applicable, enable **Exclude Location** to limit data to only users. By default, user-related widgets include locations and users.
[]Displays data associated with [network applications](/zia/about-network-applications). You can apply the following filters:
- **Action**: Use this filter to limit the data to a specific action taken by your DNS Control policy. You can search for a specific action.
- **Department**: Use this filter to limit the data to the traffic of a specific department. It lists 200 results at a time. You can search for a specific department. You can choose to include or exclude certain departments.
- **DNS Tunnel & Network App Categories**:** **Use this filter to limit the data to traffic that comes from a specific tunneling or network application category. You can search for a specific category.
- **DNS Tunnels & Network Apps**:** **Use this filter to view information about the type of tunnels and network applications used. You can search for a specific application.
- **Location**: Use this filter to limit the data to a location's traffic. Choose a location from the list of Internet gateway locations specified in the Locations page. The list includes **Road Warrior**, the default location for transactions that did not originate from a predefined location. This filter lists 200 results at a time. You can search for a specific location. You can choose to include or exclude certain locations.
- **Location Group**: Use this filter to limit the data to the traffic of a specific location group. You can search for a specific location group.
- **Location Type**: Use this filter to limit the data to a specific location type. The default option for this filter is **None**. The following location types appear under this filter:
- Corporate User Traffic Group
- Guest Wifi Group
- IoT Traffic Group
- Server Traffic Group
- Unassigned Locations
- Workload Traffic Group
- **User**: Use this filter to limit the data to the traffic of specific users. You can search for a specific user. You can choose to include or exclude certain users.
[]Displays data associated with the DNS tunneling categories and network services. You can apply the following filters:
- **Action**: Use this filter to limit the data to a specific action taken by your DNS Control policy. You can search for a specific action.
- **Department**: Use this filter to limit the data to the traffic of a specific department. It lists 200 results at a time. You can search for a specific department. You can choose to include or exclude certain departments.
- **DNS Tunnel & Network App Categories**:** **Use this filter to limit the data to traffic that comes from a specific tunneling or network application category. You can search for a specific category.
- **DNS Tunnels & Network Apps**:** **Use this filter to view information about the type of tunnels and network applications used. You can search for a specific application.
- **Location**: Use this filter to limit the data to a location's traffic. Choose a location from the list of Internet gateway locations specified in the Locations page. The list includes **Road Warrior**, the default location for transactions that did not originate from a predefined location. This filter lists 200 results at a time. You can search for a specific location. You can choose to include or exclude certain locations.
- **Location Group**: Use this filter to limit the data to the traffic of a specific location group. You can search for a specific location group.
- **Location Type**: Use this filter to limit the data to a specific location type. The default option for this filter is **None**. The following location types appear under this filter:
- Corporate User Traffic Group
- Guest Wifi Group
- IoT Traffic Group
- Server Traffic Group
- Unassigned Locations
- Workload Traffic Group
- **User**: Use this filter to limit the data to the traffic of specific users. You can search for a specific user. You can choose to include or exclude certain users.
[]![Screenshot of Data Type and Filters menus for Zscaler New Widget window](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/dashboard-and-reporting-tools/dns-data-types-and-filters/zia-dns-widget-data_type-filters.png)
[]![Screenshot of DNS Insights showing the Data Types and Filters options highlighted](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/dashboards-and-reports-tools/dns-data-types-and-filters/zia-dns-insights-types-and%20filters.png)