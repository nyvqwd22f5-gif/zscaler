# NSS Feed Output Format: Firewall Logs
Source: https://help.zscaler.com/zia/nss-feed-output-format-firewall-logs
PDF: https://help.zscaler.com/pdf/com/en/1400561.pdf

The Firewall Nanolog Streaming Service (NSS) feed specifies the data from the Firewall logs that the NSS sends to the security information and event management (SIEM) system. You can configure an NSS feed by including one or more fields. The fields and their values display in the NSS feed output.
- [View a sample Firewall log.](#nss-feed-output-firewall-example)
For the Standard Firewall subscription, allowed sessions are logged in aggregate form, resulting in fewer logs for the allowed transactions. Blocked transactions have detailed logs and produce a log for every blocked session.
If you want detailed logging for all sessions, including blocked and allowed transactions, you must have the Advanced Firewall subscription. However, detailed logging for DNS transactions is available with both Standard and Advanced Firewall subscriptions. To learn more, see [Understanding Firewall Capabilities](/zia/understanding-firewall-capabilities).
Logs are aggregated for each of the following fields within a 15-minute time window: User, Rule Slot, Network Service, Network Application, and IP Category. For consecutive sessions with the same values across these fields, Zscaler only records a single log, in which the remaining fields are taken from the last session in the 15-minute time window.
The following tables display information about the Firewall fields and example values for those fields. If applicable, the Firewall fields are mapped to their corresponding columns in [Firewall Insights Logs](/zia/firewall-insights-logs-columns) (Analytics > Firewall Insights > Logs).
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
Client Information
| Field | Description | Example | Insights Logs |
| ----- | ----------- | ------- | ------------- |
| %s{csip} | The client source IP address. For aggregated sessions, this is the client source IP address of the last session in the aggregate. | 192.0.2.10, 2a02:2e0:40c:102:1:2b:10:80, 2001:db8::2:1 | Client Source IP |
| %d{csport} | The client source port. For aggregated sessions, this is the client source port of the last session in the aggregate. | 22 | Client Source Port |
| %s{cdip} | The client destination IP address. For aggregated sessions, this is the client destination IP address of the last session in the aggregate. | 198.51.100.54, 2a02:2e0:40c:102:1:2b:10:80, 2001:db8::2:1 | Client Destination IP |
| %d{cdport} | The client destination port. For aggregated sessions, this is the client destination port of the last session in the aggregate. | 22 | Client Destination Port |
| %s{cdfqdn} | The client destination FDQN (e.g., the HTTP host header) | www.example.com | Client Destination Name |
| %s{tsip} | The tunnel IP address of the client (source). For aggregated sessions, this is the client's tunnel IP address corresponding to the last session in the aggregate. | 192.0.2.15 | Client Tunnel IP |
| %s{location} | The name of the location from which the session was initiated | Headquarters | Location |
| %s{ttype} | The traffic forwarding method used to send the traffic to the Firewall | L2 tunnel | Traffic Forwarding |
| %s{aggregate} | Indicates whether the Firewall session is aggregated | Yes | Aggregated Session |
| %s{srcip_country} | The traffic's source country, which is determined by the client IP address location. There is no source country value in logs for aggregated sessions that are allowed. | United States | Source Country |
IPS
-
-
-
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
| %s{threatcat} | The category of the threat in the Firewall session by the IPS engine | Botnet CallbackDenial of Service AttackMalicious Content | Advanced Threat Category |
| %s{threatname} | The name of the threat detected in the Firewall session by the IPS engine | Linux.Backdoor.TsunamiWin32.Trojan.DNSpionage | Threat Name |
| %d{threat_score} | The score of the threat detected in the Firewall session by the IPS engine. The score is assigned to the threat by Zscaler ThreatLabz and reflected in the Zscaler Threat Library. The score ranges from 0–100, from the least to the greatest threat. | 10 | Threat Score |
| %s{threat_severity} | The severity of the threat detected in the Firewall session by the IPS engine. The severity relates directly to the threat score. For example, if the value of `%d{threat_score}` is between `90` and `100`, then the value of `%s{threat_severity}` is `Critical`. | Critical (90–100)High (75–89)Medium (46–74)Low (1–45)None (0) | Threat Severity |
| %s{ipsrulelabel} | The name of the IPS policy that was applied to the Firewall session | Default IPS Rule | IPS Rule Name |
| %d{ips_custom_signature} | Indicates if a custom IPS signature rule was applied. It is a numeric value (1 or 0). | 1 indicates a custom IPS rule0 indicates a non-custom IPS rule | IPS Custom Signature |
Server Information
| Field | Description | Example | Insights Logs |
| ----- | ----------- | ------- | ------------- |
| %d{sdport} | The server destination port. For aggregated sessions, this is the server destination port of the last session in the aggregate. | 443 | Server Destination Port |
| %s{sdip} | The server destination IP address. For aggregated sessions, this is the server destination IP address of the last session in the aggregate. | 198.51.100.100, 2a02:2e0:40c:102:1:2b:10:80, 2001:db8::2:1 | Server Destination IP |
| %s{ssip} | The server source IP address. For aggregated sessions, this is the server source IP address of the last session in the aggregate. | 198.51.100.100, 2a02:2e0:40c:102:1:2b:10:80, 2001:db8::2:1 | Server Source IP |
| %d{ssport} | The server source port. For aggregated sessions, this is the server source port of the last session in the aggregate. | 22 | Server Source Port |
| %s{ipcat} | The URL category that corresponds to the server IP address | Finance | Server IP Category |
Session Information
| Field | Description | Example | Insights Logs |
| ----- | ----------- | ------- | ------------- |
| %d{avgduration} | The average session duration, in milliseconds, if the sessions were aggregated | 600,000 |  |
| %d{duration} | The session or request duration in seconds | 600 |  |
| %d{durationms} | The session or request duration in milliseconds | 600,000 | Session Duration |
| %d{numsessions} | The number of sessions that were aggregated | 5 |  |
| %s{stateful} | Indicates if the Firewall session is stateful | Yes |  |
Transaction Action
-
- [](/zia/about-nat-control)
| Field | Description | Example | Insights Logs |
| ----- | ----------- | ------- | ------------- |
| %s{rulelabel} | The name of the rule that was applied to the transaction | Default Firewall Filtering Rule | Rule Name |
| %s{action} | The action that the service took on the transaction: Allowed or Blocked | Blocked | Action |
| %s{dnat} | Indicates if the destination NAT policy was applied | Yes |  |
| %s{dnatrulelabel} | The name of the destination NAT policy that was applied | DNAT_Rule_1Any name under the Rule Name column on the NAT Control page (Policy > Firewall Control > NAT Control Policy) | DNAT Rule Name |
Transaction Information
[](/zia/about-company-profile)[](/zia/firewall-insights-logs-columns)
| Field | Description | Example | Insights Logs |
| ----- | ----------- | ------- | ------------- |
| %d{recordid} | The record ID |  | This field is specific to NSS |
| %s{pcapid} | The path of the packet capture (PCAP) file that captured the transaction. The PCAP ID has the following format: `<Company ID>/<Directory>/<PCAP File Name>`. The company ID is the internal ID of an organization and can be found on the Company Profile page. The directory is the log type. To download the PCAP file, go to the Capture column on the Firewall Insights Logs page. | 43139974/fw/663ba8fd30b50001.pcap | Capture |
| %ld{inbytes} | The number of bytes sent from the server to the client | 10,000 | Inbound Bytes |
| %ld{outbytes} | The number of bytes sent from the client to the server | 10,000 | Outbound Bytes |
| %s{nwapp} | The network application that was accessed | SSH | Network Application |
| %s{nwsvc} | The network service that was used | HTTP | Network Service |
| %s{ipproto} | The type of IP protocol | TCP | Network Protocol |
| %s{destcountry} | The abbreviated code of the country of the destination IP address | USA | Dest Country |
| %s{eedone} | Indicates if the characters specified in the Feed Escape Character field of the NSS feed configuration page were hex encoded | Yes | This field is specific to NSS |
User Information
| Field | Description | Example | Insights Logs |
| ----- | ----------- | ------- | ------------- |
| %s{login} | The user's login name in email address format | jdoe@safemarch.com | User |
| %s{dept} | The department of the user | Sales | Department |
Zscaler Client Connector Device Information
-
-
-
-
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
| %s{devicehostname} | The hostname of the device | THINKPADSMITH | Device Hostname |
| %s{devicemodel} | The model of the device | 20L8S7WC08 | Device Model |
| %s{devicename} | The name of the device | admin | Device Name |
| %s{deviceostype} | The OS type of the device | iOSAndroid OSWindows OSmacOSOther OS | OS Type |
| %s{deviceosversion} | The OS version that the device uses | Version 10.14.2 (Build 18C54) | OS Version |
| %s{deviceowner} | The owner of the device | jsmith | Device Owner |
| %s{deviceappversion} | The app version that the device app uses | 2.0.0.120 | Enrolled Device appversion |
| %s{external_deviceid} | The external device ID that associates a user’s device with the mobile device management (MDM) solution | 1234 | External Device ID |
| %s{ztunnelversion} | The Z-Tunnel version | ZTUNNEL_1_0 | Zscaler Client Connector Tunnel Version |
| %d{bypassed_session} | Indicates whether the traffic bypassed the Zscaler Client Connector. It is a numeric value (1 or 0). | 1 indicates that the traffic bypassed Zscaler Client Connector0 indicates that the traffic did not bypass Zscaler Client Connector | Bypassed Session |
| %s{bypass_etime} | The date and time when the traffic bypassed the Zscaler Client Connector | Mon Oct 16 22:55:48 2023 | Bypassed Session Event Time |
| %s{flow_type} | The flow type of the transaction | DirectLoopbackVPNVPN TunnelZIAZPA | Flow Type |
Data Center
| Field | Description | Example | Insights Logs |
| ----- | ----------- | ------- | ------------- |
| %s{datacenter} | The name of the data center | CA Client Node DC | Data Center |
| %s{datacentercity} | The city where the data center is located | Sa |  |
| %s{datacentercountry} | The country where the data center is located | US |  |
Forwarding Control
-
- [](/zia/about-forwarding-policies)
| Field | Description | Example | Insights Logs |
| ----- | ----------- | ------- | ------------- |
| %s{rdr_rulename} | The name of the redirect/forwarding policy | FWD_Rule_1Any name under the Rule Name column on the Forwarding Control page (Policy > Forwarding Control) | Forwarding Rule |
| %s{fwd_gw_name} | The name of the gateway defined in a forwarding rule | FWD_1 | Gateway Name |
| %s{zpa_app_seg_name} | The name of the Zscaler Private Access (ZPA) application segment | ZPA_test_app_segment | Application Segment |
[]"Mon Jun 20 15:35:48 2022","new-gre","Default Department","new-gre","80","36084","80","0","172.17.3.49","216.113.179.53","0.0.0.0","216.113.179.53","10.66.89.115","0","GRE","Drop","No","Yes","No","HTTP","ebay","TCP","Online Shopping","United States","21","Firewall_1","14693","548","0","21","1","None","None","None","NA","NA"
Obfuscated Fields
Select Firewall fields support obfuscation, as indicated by the prefix `o`. For example, the field `%d{ocsip}` is the obfuscated version of `%s{csip}`. Instead of displaying the client source IP address, the obfuscated field displays a random string in the NSS feed output.
The following are obfuscated fields:
- %d{ocsip}
- %s{oipsrulelabel}
- %s{oipcat}
- %s{orulelabel}
- %s{odnatrulelabel}
- %s{odevicehostname}
- %s{odevicename}
- %s{odeviceowner}
- %s{ordr_rulename}
- %s{ofwd_gw_name}
- %s{ozpa_app_seg_name}
Hex-Encoded Fields
The Zscaler service hex encodes all non-printable ASCII characters that are in URLs when it sends logs to the NSS. Any URL character that is less than or equal to 0x20, or greater than or equal to 0x7F, is encoded as `%HH`. This ensures that your SIEM can parse the URLs that contain control characters. For example, a `\n` character in a URL is encoded as `%0A`, and a space is encoded as `%20`.
The following are hex-encoded fields:
- %s{ethreatname}
- %s{elocation}
- %s{edepartment}
- %s{erulelabel}
- %s{elogin}
- %s{edevicehostname}