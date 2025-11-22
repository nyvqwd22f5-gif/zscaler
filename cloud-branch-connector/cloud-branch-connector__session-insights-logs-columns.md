# Session Insights Logs: Columns
Source: https://help.zscaler.com/cloud-branch-connector/session-insights-logs-columns
PDF: https://help.zscaler.com/pdf/com/en/1420691.pdf

You can customize your Session logs by using column fields. To learn more about logs, see [About Insights Logs](/cloud-branch-connector/about-insights-logs).
You can select the following Session Insights Logs columns to view:
- **Application Segment**: The transactions associated with a specific application segment.
- **AWS Availability Zone**: The availability zone where Cloud Connector for AWS is deployed.
- **AWS Region**: The location of your AWS cloud account.
- **Azure Availability Zone**: The availability zone where Cloud Connector for Azure is deployed.
- **Azure Region**: The location of your Azure cloud account.
- **Azure Subscription ID**: The Azure subscription ID associated with your Cloud Connector.
- **CC Instance**: The specific Zscaler software instance from which you want to view the session logs.
- **CC VM**: The Cloud Connector virtual machine.
- **Client Destination IP**: The client destination IP address. For aggregated sessions, this is the client destination IP address of the last session in the aggregate.
- **Client Destination Name**: The client destination FQDN for Advanced Firewall. For aggregated sessions, this is the client destination FQDN of the last session in the aggregate.
- **Client Destination Port**: The client-side destination IP address. For aggregated sessions, this is the client's destination port of the last session in the aggregate.
- **Client Received Bytes**: The number of bytes sent from the server to the client.
- **Client Sent Bytes**: The number of bytes sent from the client to the server.
- **Client Source IP**: The client source IP address. For aggregated sessions, this is the client source IP address of the last session in the aggregate.
- **Client Source Port**: The client-side source port. For aggregated sessions, this is the client source port of the last session in the aggregate.
- **Cloud Connector Group**: The name of the Cloud Connector group.
- **Cloud Connector Source IP**: The Cloud Connector source IP address.
- **Cloud Connector Source Port**: The source port of the Cloud Connector that is used to connect to the forwarding gateway.
- **Country**: The country that corresponds to the server IP.
- **Event Time**: The date and time of the transaction.
- **Forwarding Rule**: The forwarding policy list. If the client destination IP address entered is the service IP address of the Cloud or Branch Connector instance, the forwarding rule is logged as 0.
- **Forwarding Type**: The type of traffic forwarding mechanism for this session.
- **GCP Availability Zone**: The availability zone where Cloud Connector for GCP is deployed.
- **GCP Project ID**: The GCP project ID associated with your Cloud Connector.
- **GCP Region**: The location of your GCP cloud account.
- **Gateway Destination IP**: The gateway destination IP address used for the Cloud or Branch Connector.
- **Gateway Destination Port**: The destination port of the forwarding gateway.
- **Gateway Name**: The name of the gateway.
- **Location**: The name of the location from which the session was initiated.
- **Network Service**: The network service associated with the session or aggregated sessions.
- **Platform**: The hypervisor or the cloud platform associated with the session insights.
- **Server Destination IP**: The server destination IP address. For aggregated sessions, this is the server destination IP address of the last session in the aggregate.
- **Server Destination Port**: The server-side destination port. For aggregated sessions, this is the server destination port of the last session in the aggregate.
- **Server Received Bytes**: The number of bytes received by the server.
- **Server Sent Bytes**: The number of bytes sent by the server.
- **Server Source IP**: The server source IP address. For aggregated sessions, this is the server source IP address of the last session in the aggregate.
- **Server Source Port**: The server-side source port. For aggregated sessions, this is the server source port of the last session in the aggregate.
- **Session Duration**: The duration of the session in milliseconds. For aggregated sessions, this indicates the sum of individual session durations.