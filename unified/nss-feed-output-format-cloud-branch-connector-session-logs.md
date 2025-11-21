# NSS Feed Output Format: Cloud & Branch Connector Session Logs
Source: https://help.zscaler.com/unified/nss-feed-output-format-cloud-branch-connector-session-logs
PDF: https://help.zscaler.com/pdf/com/en/1519576.pdf

The Session NSS feed specifies the data from the Session logs that the Nanolog Streaming Service (NSS) sends to the security information and event management (SIEM) system. You can configure an NSS feed by including one or more fields. The fields and their values display in the NSS feed output.
The following tables display information about the Session fields and possible values for those fields.
Date/Time
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{time} | The log time (i.e., when the NSS logs a transaction) | Tue Nov 12 22:55:48 2024 |
| %s{eventtime} | The time and date of the transaction. This excludes the time zone. | Tue Nov 12 22:55:48 2024 |
| %s{tz} | The time zone. This is the same as the time zone you specified when you configured the NSS feed. | GMT |
| %02d{ss} | Second of timestamp (0–59) | 48 |
| %02d{mm} | Minute of timestamp (0–59) | 55 |
| %02d{hh} | Hour of timestamp (0–23) | 22 |
| %02d{dd} | Day of timestamp (1–31) | 12 |
| %02d{mth} | Month of timestamp (1-12) | 11 |
| %04d{yyyy} | Year | 2024 |
| %s{mon} | The name of the month | Nov |
| %s{day} | The day of the week | Tue |
Client Information
| Field in Logs | Description | Example |
| ------------- | ----------- | ------- |
| %s{clt_dst_name} | Client destination host name | Hostname |
| %s{oclt_dest_name} | Obfuscated client destination host name |  |
| %s{clt_src_ip} | Client source IPv4 address. For aggregated sessions, this is the client source IP address of the last session in the aggregate. | 192.0.2.6 |
| %d{clt_src_port} | Client source port. For aggregated sessions, this is the client source port of the last session in the aggregate. | 22 |
| %s{clt_dst_ip} | Client destination IPv4 address. For aggregated sessions, this is the client destination IP address of the last session in the aggregate. | 192.0.2.184 |
| %d{clt_dst_port} | Client destination port. For aggregated sessions, this is the client destination port of the last session in the aggregate. | 80 |
| %s{fwdtypename} | Traffic forwarding method used to send the traffic to the firewall | L2 tunnel |
| %s{zapptunname} | Zscaler Client Connector tunnel name used to send the traffic to the firewall |  |
Server Information
| Field in Logs | Description | Example |
| ------------- | ----------- | ------- |
| %d{srv_dst_port} | Server destination port. For aggregated sessions, this is the server destination port of the last session in the aggregate. | 443 |
| %d{gw_dst_port} | Gateway destination port | 443 |
| %d{zia_src_port} | Internet & SaaS source port | 443 |
| %s{srv_dst_ip} | Server destination IPv4 address. For aggregated sessions, this is the server destination IP address of the last session in the aggregate. | 203.0.113.199 |
| %s{gw_name} | Gateway name | FWD_1 |
| %s{ogw_name} | Obfuscated gateway name |  |
| %s{gw_dst_ip} | Gateway destination IPv4 address | 203.0.113.1 |
| %s{zia_src_ip} | Internet & SaaS source IPv4 address | 198.51.100.48 |
| %s{srv_src_ip} | Server source IPv4 address. For aggregated sessions, this is the server source IP address of the last session in the aggregate. | 203.0.113.64 |
| %d{srv_src_port} | Server source port. For aggregated sessions, this is the server source port of the last session in the aggregate. | 22 |
| %s{srv_ip_country} | Abbreviated code of the country of the server IP address | USA |
Session Information
| Field | Description | Example |
| ----- | ----------- | ------- |
| %ld{session_duration} | Session duration in milliseconds | 600000 |
| %d{num_sess} | Number of sessions | 36 |
| %d{num_aggr_sess} | Number of sessions that were aggregated | 5 |
| %s{aggrname} | Type of aggregation |  |
Forwarding Control
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{rdrrulename} | Name of redirect rule that was applied to the transaction | FWD_Rule_1 |
| %s{ordrrulename} | Obfuscated redirect rule name |  |
| %s{self_rulename} | Cloud Connector or Branch Connector self-rule name that was applied to the transaction | CONNECTOR_SELF |
| %s{oself_rulename} | Obfuscated Cloud Connector or Branch Connector self rule name | AVG |
Transaction Information
| Field | Description | Example |
| ----- | ----------- | ------- |
| %ld{clt_tx_bytes} | Number of bytes sent from the server to the client | 10000 |
| %ld{clt_rx_bytes} | Number of bytes sent from the client to the server | 10000 |
| %s{nw_service} | The network service that was used | HTTP |
| %s{traffic_type} | Traffic type | INTERNAL |
| %s{clt_nw_protocol} | Client network protocol | TCP |
| %s{srv_nw_protocol} | Server network protocol | TCP |
| %s{zia_gw_protocol} | Internet & SaaS gateway protocol |  |
| %s{zpa_appseg} | Private Applications application segment | Any |
Cloud & Branch Connector Information
-
-
-
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{name} | Cloud Connector or Branch Connector name | CC_304 |
| %s{vm_name} | Cloud Connector or Branch Connector virtual machine (VM) name | zs-cc-vpc-xxxx |
| %s{group_name} | Cloud Connector or Branch Connector group name | zs-cc-vpc-xxxx-us-west-2x |
| %s{region_name} | Cloud Connector or Branch Connector region name | (US) West US 2 |
| %s{location} | Cloud Connector or Branch Connector location | Headquarters |
| %s{platform_name} | Cloud Connector or Branch Connector platform name | Azure |
| %s{platformgeo_name} | Cloud Connector or Branch Connector platform geolocation name (availability zone) | San Jose, United States |
| %s{account_id} | Amazon Web Services (AWS) account ID, Microsoft Azure subscription ID, or Google Cloud Platform (GCP) project ID | 506xxx032xxx (AWS)f60abxxx-bb7d-43xx-84xx-4axxxx7xxxxx (Azure)gcs-xxx-cc-gcp-project (GCP) |
Base64 Fields
A SIEM can have parsing issues whenever a string field has nonprintable or delimiter characters. For that reason, the Zscaler service has URL encoding for fields such as `clt_dst_name`. There are several other fields that have the same parsing issue, but URL encoding is not suitable. Such fields are encoded using Base64.
Turning on Base64 encoding for all supported fields may result in approximately a 20% drop in performance.
The following fields have been added as Base64 fields:
- b64clt_dst_name
- b64gw_name
- b64rdrrulename
- b64self_rulename
Hex-Encoded Fields
When the Zscaler service send logs to the NSS, it hex encodes all nonprintable ASCII characters that are in URLs. Any URL character that is less than or equal to 0x20, or greater than or equal to 0x7F, is encoded as `%HH`. This ensures that your SIEM can parse the URLs that contain control characters. For example, a `\n` character in a URL is encoded as `%0A`, and a space is encoded as `%20`.
- eclt_dst_name
- egw_name
- erdrrulename
- eself_rulename