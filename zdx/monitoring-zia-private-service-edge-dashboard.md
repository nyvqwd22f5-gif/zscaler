# Monitoring the ZIA Private Service Edge Dashboard
Source: https://help.zscaler.com/zdx/monitoring-zia-private-service-edge-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1525341.pdf

Zscaler Internet Access (ZIA) Private Service Edge Health provides a statistical overview of Zscaler Private Service Edges deployed in your data centers. View details of overall traffic, internal latency, and transactions within the previous 24 hours to 14 days, as allowed per your ZDX subscription level.
Prerequisites
To monitor ZIA Private Service Edge metrics within the dashboard, ensure:
- Your ZDX subscription level supports monitoring the ZIA Private Service Edge Health dashboard. To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
- Your admin role has view permission. To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
Viewing the Dashboard
To access the ZIA Private Service Edge Health dashboard, go to **Dashboard **> **ZIA PSE Health Dashboard**. The tiles provide metrics from the previous 24-hour period to the current time. Click **Refresh **in the upper-right corner of the page to reload any real-time updates.
- **Total PSE Data Centers**: The total number of data centers with Private Service Edges within your organization.
- **Total Throughput**: The average amount of data (in bits) processed in your data centers within the previous 24 hours.
- **Transactions/Sec**: The aggregate number of transactions processed per second in your data centers within the previous 24 hours.
![ZIA PSE Health Dashboard ](/downloads/zdx/analytics/monitoring-zia-private-service-edge-dashboard/zdx-renamed-PSE-health-dashboard.png)
The **Overall Traffic** chart provides an overview of traffic from all data centers processed by [PSE instances](#pse-inst) within your selected time range. If you select 24 Hours or 48 Hours, traffic displays in 5-minute intervals. If you select 7 Days or 14 Days, traffic displays in 1-hour intervals.
Optionally, click **Export CSV** to capture total throughput for the data centers, designated by date and time.
The dashboard table provides the following information:
- **PSE Data Center Name**: The specific data center in your organization with Private Service Edges.
- **Location**: The geographic location of the data center.
- **Instances**: The number of Private Service Edge proxy instances.
- **Throughput**: The average amount of data processed per second for the date and time within your selected time range.
- **Latency**: The average time (in milliseconds) to send data from the beginning to the end of your selected time range.
- **Transactions/Sec**: The aggregate number of transactions processed per second within your selected time range.
Click any data center name to view its details, including all Private Service Edges deployed within it.
Viewing a Data Center
The time range selected for **Overall Traffic** from the dashboard is carried over to the data center page by default. If you change the time range, all chart metrics reflect your updated selection, accordingly.
You can download metrics for each data center chart in CSV format. You also have the option to click **Report Issue** and submit a help ticket if you experience issues that require administrator support.
- **PSE Details**: A summary of metrics for the selected data center within the data time range.
- **Throughput**: The average amount of data processed per second within the data time range.
- **Latency**: The time (in milliseconds) to send data within the data time range.
- **Location**: The geographic location of the data center.
- **VIP Address**: The Virtual IP address.
- **Cluster**: The individual names for the VIP address.
- **Overall Traffic**: The overview of traffic from all your data centers, as shown in the ZIA Private Service Edge Health dashboard.
- **PSE Internal Latency**: The P95 latency (in milliseconds) calculated for the data point within the selected time range.
- **Transactions/Sec**: The total number of transactions processed per second for the data point within the selected time range.
The data center table provides the following information:
- **Instance**: A Private Service Edge identified by node name extension (e.g., pchi1-**1a1-sme**, pchi1-**1a2-sme**, pchi1-**1a3-sme**, etc). Each Private Service Edge instance belongs to a node cluster that is grouped by a physical node name (e.g., **1a**, **1b**, **1c**, etc).
- **Node Name**: The name of the physical server on which the instance resides. Optionally, you can use the Node Name drop-down menu to search for Private Service Edge clusters:
[See image.](#node-name)
- **Service IP Address**: The IP address for the corresponding Private Service Edge instance.
- **Asset Tag**: A physical ID label for the Private Service Edge.
- **Model Number**: The provided Zscaler server model number.
Click any Private Service Edge instance to view its details.
[See image.](#view-dc)
[]Viewing a Private Service Edge Instance
For each Private Service Edge instance, metrics are provided for the following charts:
- **Traffic**: The traffic processed by the Private Service Edge instance.
- **Latency**: Includes the average P95 latency (in milliseconds) for the Private Service Edge.
- **Memory Usage**: Indicates usage (in gigabytes) for the selected time range. Metrics for memory usage can be useful for troubleshooting purposes.
[See image.](#view-indiv-instance)
[]![View Data Center metrics](/downloads/tech-pubs-drafts/zdx-draft-articles/monitoring-private-service-edge-health-dashboard-draft-doc-52336/zdx-pse-health-dc3.png)
[]![Node Name drop-down menu](/downloads/tech-pubs-drafts/zdx-draft-articles/monitoring-private-service-edge-health-dashboard-draft-doc-52336/zdx-pse-health-node-name.png)
[]![PSE instance](/downloads/tech-pubs-drafts/zdx-draft-articles/monitoring-private-service-edge-health-dashboard-draft-doc-52336/zdx-pse-health-inst.png)