# Viewing the Flow Dashboard
Source: https://help.zscaler.com/zpa/viewing-flow-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1498176.pdf

The Flow dashboard provides information about agent flows and connections in your organization. You can see a maximum of 10 top metrics for each category.
To view the Flow dashboard, go to **Microsegmentation **> **Dashboard **> **Flow**.
![A view of the Flow dashboard.](/downloads/zpa/microsegmentation/Flow-dashboard4.png)
Dashboard Tools
The Flow dashboard displays the following information and functionality:
- **Time Range Filter**: View flow data from 1 Hour to 14 Days.
- **Refresh icon**: Refresh the dashboard to reflect the most current information.
- **Top Permitted Talkers**: The allowed resources and IP addresses sending out the number of flows in the network (Source IP and Protocol). These resources send the most outbound flows and initiate the connection to a given protocol.
- **Top Blocked Talkers**: The blocked resources and IP addresses sending out the number of flows in the network (Source IP and Protocol). These resources send the most outbound flows and initiate the connection to a given protocol.
- **Top Permitted Listeners**: The allowed resources and port combinations receiving the number of flows in the network (IP, Protocol, and Listening Port).
- **Top Blocked Listeners**: The blocked resources and port combinations receiving the number of flows in the network (IP, Protocol, and Listening Port).
- **Top Permitted Agent-to-Agent Flows**: The flows between multiple agents.
- **Top Permitted Flows Between Agent and Non-Agent**: The flows between agents and resources not connected to any agents.
- **Source Information**: Hover over one of the port data lines to display its Resource Name, Resource ID, IP Address, Protocol, and Count.