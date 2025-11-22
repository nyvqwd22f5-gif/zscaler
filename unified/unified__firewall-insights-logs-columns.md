# Firewall Insights Logs: Columns
Source: https://help.zscaler.com/unified/firewall-insights-logs-columns
PDF: https://help.zscaler.com/pdf/com/en/1497356.pdf

You can customize your firewall logs by using column fields. To learn more about logs, see [About Insights Logs](/unified/about-insights-logs).
Following are the Firewall Insight Log columns you can select to view:
- **Action**: The action that was performed on the session or aggregated sessions.
- **Application Segment**: A group of applications that are organized together, based upon access type or user privileges. [Application segments](/unified/about-applications) are configured through the Private Applications, and now via the Internet & SaaS, Zscaler can forward traffic to these application segments.
- **Aggregated Session**: Indicates if sessions were aggregated into this log entry.
- **Bypassed Session**: Indicates whether the traffic bypassed the Zscaler Client Connector.
- **Bypassed Session Event Time**: The date and time when the traffic bypassed the Zscaler Client Connector.
- **Capture**: The name of the packet capture (PCAP) file that captured the transaction. You can download the file by clicking the **Download **icon next to the file name.
- **Client Destination IP**: This is the IP address to which the end-user wants to connect. For aggregated sessions, this is the client destination IP address of the last session in the aggregate.
- **Client Destination Name**: The client destination FQDN for Advanced Firewall. For aggregated sessions, this is the client destination FQDN of the last session in the aggregate.
- **Client Destination Port**: The client-side destination IP address. For aggregated sessions, this is the client destination port of the last session in the aggregate. For ICMP traffic, you might see source port and destination port values. This means, for ICMP, the destination port shows as ICMP Sequence Number.
- **Client Source IP**: This is the IP address of the end-user trying to access the internet via the Internet & SaaS. For aggregated sessions, this is the client source IP address of the last session in the aggregate. You can sort and search through this column.
- **Client Source Port**: The client-side source port. For aggregated sessions, this is the client source port of the last session in the aggregate. For ICMP traffic, you may see source port and destination port values. This means, for ICMP, the source port shows the ICMP Identifier.
- **Client Tunnel IP**: The tunnel IP address of the client (source). For aggregated sessions, this is the client's tunnel IP address corresponding to the last session in the aggregate.
- **Department**: The department of the user. You can sort and search through this column.
- **Dest Country**: The destination country that corresponds to the server IP.
- **Device Hostname**: The hostname information from support devices.
- **Device Model**: The model of the device.
- **Device Name**: The name of the device.
- **Device OS Type**: The OS type of the device.
- **Device OS Version**: The OS version the device uses.
- **Device Owner**: The owner of the device.
- **DNAT Destination Name**: The DNAT FQDN for Advanced Firewall. For aggregated sessions, this is the DNAT FQDN of the last session in the aggregate.
- **DNAT Rule Name**: The name of the [NAT Control](/unified/about-nat-control) rule used.
- **Event Time**: The date and time of the transaction. You can sort this column.
- **External Device ID**: The external device ID that associates a user’s device with the mobile device management (MDM) solution.
- **Flow Type**: The flow type of the traffic.
- **Inbound Bytes**: The number of bytes sent from the server to the client. For aggregated sessions, this is the total bytes sent from the server across all sessions in the aggregate.
- **IPS Custom Signature**: This shows if the session triggered a custom IPS signature rule.
- **IPS Rule Name**: The name of the IPS rule that triggered on the session or aggregated sessions.
- **IPS Threat Name**: The name of the threat detected by the IPS. If you click on the threat name, you are taken to Zscaler's [Threat Library](https://threatlibrary.zscaler.com/). On this page, you find detailed information about the threat.
- **Location**: The name of the location from which the session was initiated. You can sort and search through this column.
- **Logged Time**: The date and time the transaction was logged.
- **NAT Action**: The NAT action that was performed on this session.
- **Network Application**: The network application associated with the session or aggregated sessions.
- **Network Protocol**: The IP Network Protocol
- **Network Service**: The network service associated with the session or aggregated sessions.
- **Outbound Bytes**: The number of bytes received by the server. For aggregated sessions, this is the total bytes received by the server across all sessions in the aggregate.
- **Rule Name**: The name of the rule that triggered on the session or aggregated sessions. You can sort this column. This column is displayed in the logs only when the traffic is blocked. By default, this column is not displayed for allowed traffic.
- The Zscaler Bypass Traffic rule populates in logs when:
- The web module does not accept the control for the traffic evaluation from the firewall module because the handshake abruptly terminates during flow establishment.
- The traffic is forwarded from a firewall-enabled sublocation but not enabled for the parent location or another sublocation under the same parent location. This happens due to the latency in identifying these location differences, such as in the X-Forwarded-For (XFF) configuration.
- The Blocked by Web Proxy Policy rule populates in logs when a web policy blocks traffic while it is being evaluated by deep packet inspection to identify the network application to which the traffic belongs.
- **Server Country Code**: The country code corresponding to the server IP.
-
**Server Destination IP**: This is the IP address to which the end user's traffic is directed. For example, if a redirect rule is actionable on the Client Destination IP to forward the traffic to a different IP address, this column shows the IP address to which the traffic was directed. For aggregated sessions, this is the server destination IP address of the last session in the aggregate.
When you use Source IP Anchoring for the URL or domain, Zscaler doesn't log the server IP address at the proxy layer because the client request is forwarded to the Private Applications, and the proxy code is already completed. Therefore, the IP address 0.0.0.1 is logged to indicate the internal redirection within Zscaler.
- **Server Destination Port**: The server-side destination port. For aggregated sessions, this is the server destination port of the last session in the aggregate.
- **Server IP Category**: The URL category that corresponds to the server IP.
- **Server Source IP**: This is the Zscaler IP address from which the end-user request is sent. For aggregated sessions, this is the server source IP address of the last session in the aggregate.
- **Server Source Port**: The server-side source port. For aggregated sessions, this is the server source port of the last session in the aggregate.
- **Session Duration**: The duration of the session in milliseconds. For aggregated sessions, this indicates the sum of individual session durations.
- **Source Country**: The source country that corresponds to the public IP where the traffic generated.
- **Advanced Threat Category**: The name of the advanced threat category.
- **Threat Score**: The score of the threat detected in the Firewall session by the IPS engine. The score is assigned to the threat in the Zscaler Threat Library. The score ranges from 0–100, from the least to the greatest threat.
- **Threat Severity**: The severity of the threat detected in the Firewall session by the IPS engine. The severity relates directly to the threat score. The following threat severities appear:
- Critical: If the value of the threat score is 90–100.
- High: If the value of the threat score is 75–89.
- Medium: If the value of the threat score is 46–74.
- Low: If the value of the threat score is 1–45.
- None: If the value of the threat score is 0.
- **Traffic Forwarding**: The type of traffic forwarding mechanism for this session. For aggregated sessions, this is the traffic forwarding type of the last session in the aggregate.
- **User**: The user name. If this is blank, then location-based authentication is set. You can sort and search through this column.
- **Zscaler Client Connector Tunnel Version**: The version of the Zscaler Client Connector** **Z-Tunnel.