# DNS Insights Logs: Columns
Source: https://help.zscaler.com/zia/dns-insights-logs-columns
PDF: https://help.zscaler.com/pdf/com/en/1400996.pdf

You can customize your DNS logs by using column fields. To learn more about logs, see [About Insights Logs](/zia/about-insights-logs).
Following are the DNS Insight Log columns you can select to view:
- **Capture**: The name of the packet capture (PCAP) file that captured the transaction. You can download the file by clicking the **Download **icon next to the file name.
- **Client IP**:** **The IP address from which the transaction originated. This is the IP address of the client device. You can sort this column.
-
**DNS Error Code**:** **The error code returned in the DNS response. All error codes derive from the standard set by the [Internet Engineering Task Force Organization](https://tools.ietf.org/html/rfc2929#section-2.3).
An error code is populated in this field in the following scenarios:
- When the traffic matches with a DNS Control rule configured with the Block with Response Code action, the corresponding response code is populated in this field.
- When using [DNS Gateways](/zia/about-dns-gateways) to forward DNS queries (inbound over UDP/TCP/DoH) to an external DNS service over DoH, the Zscaler service may receive an HTTP response without a DNS response due to an error. In that case, the service tries to translate the HTTP status code into an equivalent DNS response and logs it using the DNS Error Code field.
- [Possible DNS Error Codes Displayed in the DNS Response](#error_desc)
- **DNS Gateway Flags**: The DNS request status at the DNS Gateway level.
- **DNS Request Type**: The DNS request type.
- **DNS Response Type**: The DNS response type.
- **Department**: The department of the user. You can sort and search through this column.
- **Device Hostname**: The hostname information from support devices.
- **Device Model**: The model of the device.
- **Device Name**: The name of the device.
- **Device OS Type**: The OS type of the device.
- **Device OS Version**: The OS version the device uses.
- **Device Owner**: The owner of the device.
- **ECS Object Name**: The unique name assigned to and identifying the ECS object.
- **ECS Prefix**: The ECS prefix used for the Client Subnet option in the DNS query.
- **ECS Prefix Length**: The length of the client’s IP address specified for the Client Subnet option in the DNS query.
- **HTTP Status Code**: The status code returned by the DNS Over HTTPS (DoH) server, and is applicable only when the protocol used between the ZIA service and the DNS server is DoH.
- **Request Categories**: The request category corresponding to the requested domain. If this is blank, then the domain is not categorized.
- **Response Categories**: The response category corresponding to the response for the requested domain. If this is blank, then the resolved IP or the canonical name (CNAME) is not categorized.
- **Event Time**: The date and time of the transaction. You can sort this column.
- **Location**: The name of the location from which the DNS request was initiated. You can sort and search through this column.
- **Logged Time**: The date and time the transaction was logged.
- **Protocol Type**: UDP, TCP, or DNS over HTTP.
- **Response Rule Name**: Name of the rule that was applied to the DNS response.
-
**Request Action**: The action taken on the DNS request.
For block rules configured with either Block or Block with Response Code action, this field populates a "Block" value.
-
**Response Action**: The action taken on the DNS response.
For block rules configured with either Block or Block with Response Code action, this field populates a "Block" value.
- **Request Duration**: The request duration in milliseconds.
- **Request Rule Name**: Name of the rule that was applied to the DNS request.
- **Requested Domain**: The domain for which DNS resolution was requested. You can sort and search through this column.
- **Resolved IP or Name**: The resolved IP or CNAME in the response. Whether this is an IP or Name is determined by the DNS response type field. You can sort this column.
- **Resolver Gateway**: The name of the DNS resolver (primary or secondary, within the configured DNS Gateway of the triggered rule) that was successfully used to resolve the DNS request or displays the error resolution, if any. One of the following flags appears:
- Primary Server Attempted
- Secondary Server Attempted
- Query Forwarded to Destination
- Error Response Returned to Client
- Query Dropped
- **Rule Name**: The rule that was triggered by the DNS request, response, or both. You can sort this column. This column is only displayed in the logs if the traffic is blocked. By default, this column is not displayed for allowed traffic.
- The following are the reasons why the Zscaler Bypass Traffic rule populates in the logs:
- When the domain name in the DNS request query matches a Zscaler cloud domain.
- When the DNS request query matches an Microsoft 365 endpoint listed in the [Office 365 One Click predefined firewall filtering rules](/zia/about-predefined-firewall-filtering-rules#office-one-click), if enabled.
- When the DNS response does not contain a resolved IP or CNAME.
- When the DNS response is not completely analyzed because of its resource record type. DNS Control performs detailed analysis of responses for A, AAAA, CNAME, and PTR record types.
- **Server IP**: The actual DNS server IP address that resolves the DNS request. The user-targeted DNS server and the actual DNS server can vary depending on the NAT rule configuration for DNS traffic. To learn more, see [About DNS Control](/zia/about-dns-control). You can sort this column.
- **Server Port**: The server port.
- **Server Protocol**: The protocol used to communicate with the DNS server.
- **Time**: The timestamp of the DNS request.
- **User**: The user name. If this is blank, then location-based authentication is set. You can sort and search through this column.
[]
| Sl. No. | DNR Error Code | Description |
| ------- | -------------- | ----------- |
| 1 | UNSUPPORTED | The DNS parser cannot decode, but there is no error in the DNS header. |
| 2 | BYPASS | DNS transaction bypassed due to cloud domain/bypass list. |
| 3 | INT_ERROR | DNS parser failed to parse supported types. |
| 4 | SRV_TIMEOUT | DNS transaction timed out as server didn't respond. |
| 5 | EMPTY_RESP | DNS response has no error, but the answer section is empty. |
| 6 | REQ_BLOCKED | DNS request blocked by firewall, hence no DNS response. |
| 7 | ADMIN_DROP | DNS transaction prematurely terminated due to the session being forced-dropped via CLI command. |
| 8 | WCDN_TIMEOUT | DNS transaction timed out while waiting for Zscaler Message Transport System (MTS) to sync a wildcard domain resolution. |
| 9 | IPS_BLOCK | DNS transaction blocked by IPS signature match. |
| 10 | FQDN_RESOLV_FAIL | DNS Gateway server value for FQDN could not be resolved. |