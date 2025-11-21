# Analyzing Traffic Flow
Source: https://help.zscaler.com/unified/analyzing-traffic-flow
PDF: https://help.zscaler.com/pdf/com/en/1516846.pdf

The Traffic Flow page provides information about the **Traffic Overview** and **DNS Overview** pages. You can access the Traffic Flow page by clicking the **View** icon in the [Traffic Monitoring](/unified/analyzing-traffic-monitoring) Cloud & Branch Connector table, where you can see the throughput and session count forwarded via Zscaler Internet Access (ZIA), Zscaler Private Access (ZPA), Direct, or Log & Control for the selected Cloud or Branch Connector.
Analyzing the Traffic Flow Page
The **Traffic Overview** tab displays the Session Count, Total Traffic, and their corresponding trends.
Session Count
The Session Count table displays all the session count data for the Cloud or Branch Connector VMs that are provisioned and deployed in your cloud or branch. The Session Count demonstrates data for:
- **ZIA**: The session count data forwarded through the ZIA cloud.
- **ZPA**: The session count data forwarded through the ZPA cloud.
- **Direct**: The session count data forwarded directly.
- **Log & Control GW**: The session count data forwarded through the [Log and Control ](/unified/about-log-and-control-forwarding)gateway.
![Session Count Table displaying the session count data for Cloud and Branch Connector VMs. ](/downloads/cloud-connector/analytics-monitoring/about-traffic-flow/C%26B%20Connector%20Session%20Count.jpg)
Session Count Trend
The Session Count Trend lists the session count across the ZIA, ZPA, Direct, Log & Control GW, and total services for the Cloud & Branch Connector VMs that are provisioned and deployed in your cloud or branch accounts. You can adjust the time and service filter using the drop-down menus above the graph.
Select a point on the graph to see the value for the specified time period. **Click for more info** displays the [session logs](/unified/session-insights-logs-columns), where you can view real-time log consolidation for each transaction.
![The Session Count Trend Values in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/about-traffic-flow-draft/Session%20Count%20Trend%20in%20Traffic%20Flow.jpg)
Total Traffic
The total traffic displays the total inbound and outbound traffic with the corresponding Tx Bytes and Rx Bytes for each of the services:
- **Rx Bytes**: Displays the number of inbound bytes received by the service per second.
- **Tx Bytes**: Displays the number of inbound bytes transmitted by the service per second.
- **Inbound**: Displays the total inbound traffic.
![Total Traffic for Inbound and Outbound Traffic in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/analytics-monitoring/about-traffic-flow/C%26B%20Connector%20Total%20Traffic.jpg)
Traffic Trend
The Traffic Trend lists the inbound and outbound traffic flow across the ZIA, ZPA, Direct, Log & Control, and total services for the Cloud & Branch Connector VMs that are provisioned and deployed in your cloud or branch. You can adjust the time and service filter using the drop-down menus above the graph.
Click a point on the graph to see the value for the specified time period. **Click for more info** displays the session logs, where you can view real-time log consolidation for each transaction.
![Traffic Trend values for inbound and outbound traffic in the Zscaler Cloud & Branch Connector Admin Portal ](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/about-traffic-flow-draft/Traffic%20Trend%20in%20Traffic%20Flow.jpg)
Analyzing the DNS Overview Page
The DNS Overview Tab displays the DNS Monitor and the corresponding DNS Transaction Trends.
DNS Monitor
The DNS Monitor table displays data about the [DNS](/unified/dns-insights-logs-filters-0) traffic that is configured by the [DNS Filtering Rule](/unified/configuring-dns-filtering-rule). The DNS Monitor demonstrates the total transactions under the following network traffic actions:
- **Allow**: Allows DNS requests and responses that match the rule.
- **Block**: Silently blocks all DNS requests and responses that match the rule.
- **Resolve by ZPA**: Requests the Cloud or Branch Connector to resolve DNS requests using the ZPA IP pool.
![DNS Monitor Table with Total Transactions in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/analytics-monitoring/about-traffic-flow/C%26B%20Connector%20DNS%20Monitor.jpg)
DNS Transactions Trend
The DNS Transaction Trend lists the transactions that are allowed, blocked, or resolved by ZPA for the Cloud & Branch Connector VMs that are provisioned and deployed in your cloud or branch accounts. You can adjust the time and service filter using the drop-down menus above the graph.
Click a point on the graph to see the value for the specified time period. **Click for more info** displays the session logs, where you can view real-time log consolidation for each transaction.