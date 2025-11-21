# DNS Insights Logs: Columns
Source: https://help.zscaler.com/unified/dns-insights-logs-columns-0
PDF: https://help.zscaler.com/pdf/com/en/1516886.pdf

You can customize your DNS logs by using column fields. To learn more about logs, see [About Insights Logs.](/unified/about-insights-logs-0)
You can select the following DNS Insights Logs columns to view:
- **AWS Account ID**: The Amazon Web Services (AWS) Account ID associated with your Cloud Connector.
- **AWS Availability Zone**: The availability zone where Cloud Connector for AWS is deployed.
- **AWS Region**: The location of your AWS cloud account.
- **Azure Availability Zone**: The availability zone where Cloud Connector for Azure is deployed.
- **Azure Region**: The location of your Azure cloud account.
- **Azure Subscription ID**: The Azure subscription ID associated with your Cloud Connector.
- **Client IP**: The client IP address.
- **Connector Instance**: The specific Zscaler software instance from which you want to view the DNS logs.
- **Connector VM**: The Cloud Connector virtual machine.
- **Connector Group**: The name of the Cloud Connector group.
- **DNS Error Status**: The error status returned in the DNS response.
- **DNS Gateway Flag**: The DNS gateway flag status.
- **DNS Gateway Name**: The name of the DNS gateway.
- **DNS Request Type**: The type of DNS request.
- **Event Time**: The date and time of the transaction.
- **Forwarding Type**: The type of traffic forwarding mechanism for this session.
- **GCP Availability Zone**: The availability zone where Cloud Connector for GCP is deployed.
- **GCP Region**: The location of your GCP cloud account.
- **LAN Rx**: Outbound transaction bytes to Cloud Connector.
- **LAN Tx**: Inbound transaction bytes to Cloud Connector.
- **Location**: The name of the location from which the DNS request was initiated.
- **Logged Time**: The date and time the transaction was logged.
- **Platform**: The hypervisor or the cloud platform associated with the DNS insights.
- **Protocol Type**: The IP protocol type.
- **Request Action**: The action taken on the DNS request.
- **Request Duration**: The request duration in seconds.
- **Requested Domain**: The domain for which DNS resolution was requested.
- **Request Rule Name**: Name of the rule that was applied to the DNS request.
- **Resolved IP**: The resolved IP or CNAME in the response.
- **Response Action**: The action taken on the DNS response. The Zscaler service does not apply DNS policies to responses, so this column always shows **None**.
- **Response Rule Name**: The name of the rule that was applied to the DNS response. The Zscaler service only applies the DNS policy to requests. A rule applied to the response is labeled **None**, but the response itself is not.
- **Server IP**: The server IP address.
- **Server Port**: The server port.