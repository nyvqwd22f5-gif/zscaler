# NSS Feed Output Format: DNS Logs
Source: https://help.zscaler.com/zia/nss-feed-output-format-dns-logs
PDF: https://help.zscaler.com/pdf/com/en/1400571.pdf

The DNS Nanolog Streaming Service (NSS) feed specifies the data from the DNS logs that the NSS sends to the security information and event management (SIEM) system. You can configure an NSS feed by including one or more fields. The fields and their values display in the NSS feed output.
- [View a sample DNS log.](#nss-feed-output-dns-example)
The following tables display information about the DNS fields and example values for those fields. If applicable, the DNS fields are mapped to their corresponding columns in [DNS Insights Logs](/zia/dns-insights-logs-columns) (Analytics > DNS Insights > Logs).
Date/Time
| Field | Description | Example | Insights Logs |
| ----- | ----------- | ------- | ------------- |
| %s{time} | The time and date of the transaction. This excludes the time zone. | Mon Oct 16 22:55:48 2023 | Logged Time |
| %s{tz} | The time zone. This is the same as the time zone you specified when you configured the NSS feed. | GMT |  |
| %02d{ss} | Seconds (0–59) | 48 | This field is derived from Logged Time |
| %02d{mm} | Minutes (0–59) | 55 | This field is derived from Logged Time |
| %02d{hh} | Hours (0–23) | 22 | This field is derived from Logged Time |
| %02d{dd} | The day of the month (1–31) | 16 | This field is derived from Logged Time |
| %02d{mth} | The month of the year | 10 | This field is derived from Logged Time |
| %04d{yyyy} | Year | 2023 | This field is derived from Logged Time |
| %s{mon} | The name of the month | Oct | This field is derived from Logged Time |
| %s{day} | The day of the week | Mon | This field is derived from Logged Time |
| %d{epochtime} | The epoch time of the transaction | 1578128400 |  |
[]Transaction Action
| Field | Description | Example | Insights Logs |
| ----- | ----------- | ------- | ------------- |
| %s{reqrulelabel} | The name of the rule that was applied to the DNS request |  | Request Rule Name |
| %s{reqaction} | The name of the action that was applied to the DNS request | REQ_ALLOWRES_BLOC | Request Action |
| %s{resrulelabel} | The name of the rule that was applied to the DNS response |  | Response Rule Name |
| %s{resaction} | The name of the action that was applied to the DNS response |  | Response Action |
| %s{ecs_slot} | The name of the EDNS Client Subnet (ECS) rule that was applied to the DNS transaction | ECS Slot #17 | ECS Object Name |
| %s{dnsgw_slot} | The name of the DNS Gateway rule | DNS GATEWAY Rule 1 | Resolver Gateway |
[]Transaction Information
-
-
[](/zia/about-company-profile)[](/zia/dns-insights-logs-columns)
-
-
-
-
-
-
-
-
-
| Field | Description | Example | Insights Logs |
| ----- | ----------- | ------- | ------------- |
| %d{istcp} | Indicates if the DNS transaction uses TCP | 1 = Yes0 = No |  |
| %s{cip} | The IP address of the user. This can be the internal IP address if it is visible (e.g., traffic sent through a GRE tunnel or an internal IP address indicated using XFF). Otherwise, it's the client's internet (NATed Public) IP address. | 203.0.113.5, 2a02:2e0:40c:102:1:2b:10:80, 2001:db8::2:1 | Client IP |
| %d{durationms} | The duration of the DNS request in milliseconds |  | Request Duration |
| %s{sip} | The server IP address of the request | 192.168.2.200, 2a02:2e0:40c:102:1:2b:10:80, 2001:db8::2:1 | Server IP |
| %d{recordid} | The unique record identifier for each log |  | This field is specific to NSS |
| %s{pcapid} | The path of the packet capture (PCAP) file that captured the transaction. The PCAP ID has the following format: `<Company ID>/<Directory>/<PCAP File Name>`. The company ID is the internal ID of an organization and can be found on the Company Profile page. The directory is the log type. To download the PCAP file, go to the Capture column on the DNS Insights Logs page. | 43139974/dns/663ba8fd30b50001.pcap | Capture |
| %s{location} | The gateway location or sublocation of the source | Headquarters | Location |
| %s{req} | The Fully Qualified Domain Name (FQDN) in the DNS request | mail.safemarch.com | Requested Domain |
| %s{res} | The resolved IP or NAME in the DNS response | 192.168.2.200, 2a02:2e0:40c:102:1:2b:10:80, 2001:db8::2:1, EMPTY_RESP | Resolved IP or Name |
| %s{domcat} | The category of the content of the DNS request | Professional Services | Request Categories |
| %s{respipcat} | The category of the content of the DNS response | Adult Themes | Response Categories |
| %s{reqtype} | The DNS request type | A record | DNS Request Type |
| %s{restype} | The DNS response type. The means or format of the response. | IPv4, IPv6 | DNS Response Type |
| %d{sport} | The server port of the request |  | Server Port |
| %s{eedone} | Indicates if the characters specified in the Feed Escape Character field of the NSS configuration page were hex encoded | Yes | This field is specific to NSS |
| %s{error} | The DNS error code. Usually an incomplete or failed transaction. | EMPTY_RESP | DNS Error Code |
| %s{ecs_prefix} | The EDNS Client Subnet (ECS) prefix used in the DNS request. This field displays a numeric string. | 192.168.0.0 | ECS Prefix |
| %s{dnsgw_srv_proto} | The DNS Gateway server protocol | TCP, UDP, HTTP | Server Protocol |
| %s{dnsgw_flags} | Flags indicating the DNS Gateway status for the transaction | PRIMARY_SERVER_RESPONSE_PASS (i.e., Primary Server Attempted)SECONDARY_SERVER_RESPONSE_PASS (i.e., Secondary Server Attempted)FO_DEST_PASS (i.e., Query Forwarded to Destination)FO_DEST_ERR (i.e., Error Response Returned to Client)FO_DEST_DROP (i.e., Query Dropped)None | DNS Gateway Flags |
| %s{http_code} | The HTTP return code used in DNS over HTTPS sessions | 100 - Continue | HTTP Status Code |
| %s{dnsappcat} | The DNS tunnel or network application category | Commonly Blocked Tunnels | DNS Tunnel & Network App Categories |
| %s{dnsapp} | The type of DNS tunnel or network application | Google DNS | DNS Tunnels & Network Apps |
| %s{protocol} | The protocol type | TCPUDPDoH (DNS over HTTP) | Protocol Type |
User Information
| Field | Description | Example | Insights Logs |
| ----- | ----------- | ------- | ------------- |
| %s{login} | The login name in email address format | jdoe@safemarch.com | User |
| %s{dept} | The department | Sales | Department |
| %s{company} | The company name | Zscaler | This field is specific to NSS |
| %s{cloudname} | The Zscaler cloud name | zscaler.net | This field is specific to NSS |
Zscaler Client Connector Device Information
-
-
-
-
| Field | Description | Example | Insights Logs |
| ----- | ----------- | ------- | ------------- |
| %s{devicehostname} | The hostname of the device | THINKPADSMITH | Device Hostname |
| %s{devicename} | The name of the device | admin | Device Name |
| %s{deviceowner} | The owner of the device | jsmith | Device Owner |
| %s{devicemodel} | The model of the device | VMware7,1 | Device Model |
| %s{deviceosversion} | The OS version that the device uses | Microsoft Windows 10 Enterprise;64 bit | Device OS Version |
| %s{deviceostype} | The OS type of the device | Windows OS | Device OS Type |
| %s{deviceappversion} | The app version that the device uses | 4.3.0.18 | Enrolled Device appversion |
| %s{devicetype} | The type of device | Zscaler Client ConnectorCloud Browser isolationVDIIOTG |  |
Data Center
| Field | Description | Example | Insights Logs |
| ----- | ----------- | ------- | ------------- |
| %s{datacenter} | The name of the data center | CA Client Node DC | Data Center |
| %s{datacentercity} | The city where the data center is located | Sa |  |
| %s{datacentercountry} | The country where the data center is located | US |  |
Obfuscated Fields
Select DNS fields support obfuscation, as indicated by the prefix `o`. For example, the field `%d{ocip}` is the obfuscated version of `%s{cip}`. Instead of displaying the client IP address, the obfuscated field displays a random string in the NSS feed output.
The following are obfuscated fields:
- %d{ocip}
- %s{odomcat}
- %s{odevicehostname}
- %s{odevicename}
- %s{odeviceowner}
Hex-Encoded Fields
The Zscaler service hex encodes all non-printable ASCII characters that are in URLs when it sends logs to the NSS. Any URL character that is less than or equal to 0x20, or greater than or equal to 0x7F, is encoded as `%HH`. This ensures that your SIEM can parse the URLs that contain control characters. For example, a `\n` character in a URL is encoded as `%0A`, and a space is encoded as `%20`.
The following are hex-encoded fields:
- %s{elocation}
- %s{edepartment}
- %s{erulelabel}: This field is the hex-encoded version of `%s{reqrulelabel}`, which is listed in the [Transaction Action](#transaction-action-table) table.
- %s{elogin}
- %s{edevicehostname}
- %s{ednsreq}: This field is the hex-encoded version of `%s{req}`, which is listed in the [Transaction Information](#transaction-information-table) table.
[]"Mon Jun 20 14:56:51 2022","sales@zscaler.com","Service Admin","Road Warrior","Allow","Allow","DNS_1","Zscaler Bypass Traffic","AAAA","wpad.test.com","EMPTY_RESP","53","0","10.66.16.9","10.66.69.21","Corporate Marketing","Other","Zscaler","DESKTOP-J1E9T1L"