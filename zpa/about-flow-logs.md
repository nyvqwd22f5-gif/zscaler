# About Flow Logs
Source: https://help.zscaler.com/zpa/about-flow-logs
PDF: https://help.zscaler.com/pdf/com/en/1498211.pdf

Flow Logs give insight into your organization's network and agent flows. They allow you to monitor and analyze the flow data at an organizational level.
The Flow Logs page provides the following benefits and enables you to:
- View a summary of network flows that have occurred in your organization.
- View, monitor, and analyze flows from a single location.
- Take appropriate actions based on the data displayed on the page about the flows.
- Discover insights about the processing of the flows.
About the Flow Logs Page
On the Flow Logs page (Microsegmentation > Analytics > Flow Logs), you can do the following:
- Filter the time range using **Last N time** or using a custom time range. You can select **Last N time **from the drop-down menu: 1 hour, 4 hours, etc., up to 14 days.
- Refresh the Flow Logs page to reflect the most current information.
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](https://help.zscaler.com/zpa/using-tables).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Filter the information by **Agent ID**,** Source IP**,** Destination IP**, **Action**,** Rule Name**, **AppZone Name**, **Count**, **Destination Port**, **Direction**, **Enforcement Reason**, **Resource Group Name**,** **and** Resource Name**. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](https://help.zscaler.com/zpa/using-tables).
- Expand the table to view the complete information of all flow logs.
- View a list of all flow logs that are configured for your organization. For each admin, you can see:
- **Timestamp**: The date and time of the flow log.
- **Source IP**: The IP address that initiated the flow log.
- **Destination IP**: The IP address that received the flow log.
- **Destination Port**: The port number that received the flow log.
- **Protocol**: The type of communication of the flow log.
- **AppZone Name**: The name of the AppZone connected to the flow log.
- Expand a row in the table to see more information about a flow log.
- [Modify the columns displayed in the table.](https://help.zscaler.com/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](https://help.zscaler.com/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the Zscaler Private Access (ZPA) Admin Portal.
- Go to the [Agent Telemetry](/zpa/about-agent-telemetry) page to view, monitor, and analyze agent telemetrics.
- Go to the [Agent Connection Status Logs](/zpa/about-agent-connection-status-logs) page to view, monitor, and analyze agent connection log status.
If two or more matching events occur within the flow log aggregation interval, the system combines these events into a single log entry and shows a count greater than one.
![A view of the Flow Logs page. ](/downloads/zpa/microsegmentation/analytics/about-flow-logs/About-the-Flow-Logs-page7.png)