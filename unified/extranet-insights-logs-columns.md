# Extranet Insights Logs: Columns
Source: https://help.zscaler.com/zia/extranet-insights-logs-columns
PDF: https://help.zscaler.com/pdf/com/en/1506991.pdf

You can customize your extranet logs using the columns. To learn more about logs, see [About Insights Logs](/zia/about-insights-logs).
You can select the following extranet field columns:
- **Aggregated Session**: Indicates if sessions were aggregated into this log entry.
- **Application Segment**: A group of applications that are organized together, based upon access type or user privileges. [Application segments](/zpa/about-applications) are configured through Zscaler Private Access (ZPA), and now via Zscaler Internet Access (ZIA), Zscaler can forward traffic to these application segments.
- **Client Destination IP**: This is the IP address to which the end user wants to connect. For aggregated sessions, this is the client destination IP address of the last session in the aggregate.
- **Client Destination Name**: The client destination FQDN for Advanced Firewall. For aggregated sessions, this is the client destination FQDN of the last session in the aggregate.
- **Client Destination Port**: The client-side destination IP address. For aggregated sessions, this is the client destination port of the last session in the aggregate. For ICMP traffic, you might see source port and destination port values. This means, for ICMP, the destination port shows as ICMP Sequence Number.
- **Client Source IP**: This is the IP address of the end user trying to access the internet via Zscaler Internet Access (ZIA). For aggregated sessions, this is the client source IP address of the last session in the aggregate. You can sort and search through this column.
- **Client Source Port**: The client-side source port. For aggregated sessions, this is the client source port of the last session in the aggregate. For ICMP traffic, you might see source port and destination port values. This means, for ICMP, the source port shows the ICMP Identifier.
- **Client Tunnel IP**: The tunnel IP address of the client (source). For aggregated sessions, this is the client's tunnel IP address corresponding to the last session in the aggregate.
- **Data Center**: The data center associated with the transaction.
- **Department**: The department of the user. You can sort and search through this column.
- **Device appversion**: Use this filter to view transactions associated with a specific enrolled device app version. Enter all or part of the enrolled device app version in the text field and **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **Device Hostname**: The hostname information from support devices.
- **Device Model**: The model of the device.
- **Device Name**: The name of the device.
- **Device Owner**: The owner of the device.
- **Device Platform**: The platform of the device.
- **Device Type**: The type of device used to connect to the network.
- **Extranet Gateway IP**: This is the Zscaler data center IPsec IP.
- **Extranet Gateway Port**: This is the Zscaler data center IPsec VPN port.
- **Extranet Location**: The extranet location configured for your organization.
- **Extranet Location IP**: The partner side public IP which is used to establish the IPSec VPN tunnel.
- **Extranet Location Port**: The partner side port which is used to establish the IPSec VPN tunnel.
- **Extranet Name**: The extranet name configured for your organization.
- **External Device ID**: The external device ID that associates a user’s device with the mobile device management (MDM) solution.
- **Event Time**: The date and time the event occurred.
- **Inbound Bytes**: The number of bytes sent from the server to the client. For aggregated sessions, this is the total bytes sent from the server across all sessions in the aggregate.
- **Location**: The name of the location from which the session was initiated. You can sort and search through this column.
- **Logged Time**: The date and time the event was logged.
- **OS Type**: The OS type of the device.
- **OS Version**: The OS version the device uses.
- **Outbound Bytes**: The number of bytes received by the server. For aggregated sessions, this is the total bytes received by the server across all sessions in the aggregate.
- **Protocol**: Indicates the protocol that is used to establish a connection. **ICMP**, **TCP**, and **UDP** are the options available.
-
**Server Destination IP**: This is the IP address to which the end user's traffic is directed. For example, if a redirect rule is actionable on the client destination IP to forward the traffic to a different IP address, this column shows the IP address to which the traffic was directed. For aggregated sessions, this is the server destination IP address of the last session in the aggregate.
When you use Source IP Anchoring for the URL or domain, Zscaler doesn't log the server IP address at the proxy layer because the client request is forwarded to Zscaler Private Access (ZPA), and the proxy code is already completed. Therefore, the IP address 0.0.0.1 is logged to indicate the internal redirection within Zscaler.
- **Server Destination Port**: The server-side destination port. For aggregated sessions, this is the server destination port of the last session in the aggregate.
- **Session Duration**: The duration of the session in milliseconds. For aggregated sessions, this indicates the sum of individual session durations.
- **Server Source IP**: This is the Zscaler IP address from which the end user request is sent. For aggregated sessions, this is the server source IP address of the last session in the aggregate.
- **Server Source Port**: The server-side source port. For aggregated sessions, this is the server source port of the last session in the aggregate.
- **Source Country**: The source country that corresponds to the public IP where the traffic generated.
- **Source Location**: The location that corresponds to internet gateway locations specified in the [Locations](/zia/about-locations) page.
- **User**: The user name. If this is blank, then location-based authentication is set. You can sort and search through this column.
- **VPN Credentials**: The VPN credential associated with the IPSec VPN tunnel.
- **Zscaler Client Connector Tunnel Version**: The version of the Zscaler Client Connector Z-Tunnel.