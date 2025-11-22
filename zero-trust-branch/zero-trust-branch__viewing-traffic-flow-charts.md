# Viewing Traffic Flow Charts
Source: https://help.zscaler.com/zero-trust-branch/viewing-traffic-flow-charts
PDF: https://help.zscaler.com/pdf/com/en/1509071.pdf

Zero Trust Branch provides extensive visibility into lateral traffic. Every communication between the endpoints is logged and mapped onto the traffic flow chart. The traffic flow chart visualizes the entire network, connected endpoints, and the communication between them. Note that it can take up to 10 minutes after an event before the traffic is reflected in the traffic flow chart. For more real-time response, consider using flow logs. To learn more, see [Monitoring & Logs](/zero-trust-branch/monitoring-logs).
The traffic flow chart is built on the graph database. Each endpoint is a node in the graph, and communication between endpoints is shown as an edge between the nodes. Clicking a node provides additional details on the endpoint, including network details, tags, and other endpoint attributes.
To access the traffic flow chart:
-
Go to **Dashboard > Charts**.
[See image.](#traffic-chart-image)
-
Click any node to see details on the endpoint attributes. Double-click a node to drill down into that node.
Each of the edges/communications is color-coded based on the policy outcomes (allow vs. deny). Clicking the edge further shows the flow details in a table following the chart.
[]
![A typical traffic flow chart.](/downloads/device-segmentation/analytics-monitoring/viewing-traffic-flow-charts/traffic-chart.png)