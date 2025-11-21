# Understanding Private Service Edge Status Log Fields
Source: https://help.zscaler.com/zpa/understanding-private-service-edge-status-log-fields
PDF: https://help.zscaler.com/pdf/com/en/1485071.pdf

The Log Streaming Service (LSS) can send ZPA Private Service Edge log information to any third-party log analytics tool. By default, the Private Service Edge Status log type includes the fields listed in the following table for each log template (i.e., CSV, JSON, TSV). While configuring your log receiver, you can edit the default log stream content to capture only specific fields, and create a Custom log template.
- [View an example Private Service Edge Status log](#ExamplePrivateServiceEdgeStatusLog)
The following table includes descriptions and supported field format specifications for each field within the template. To learn more about the format specifications listed for each field, including examples, see [Log Field Format Specifications](/zpa/understanding-log-stream-content-format).
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
-
-
-
-
| Field | Description | Supported Field Format Specifications |
| ----- | ----------- | ------------------------------------- |
| LogTimestamp | Timestamp when the log was generated | %[OPT]s%[OPT]j%[OPT]J |
| Customer | The customer name | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| SessionID | The TLS session ID | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| SessionType | The type of session. The expected value for this field is:ZPN_TUNNEL_CONTROL: Session from the ZPA Private Service Edge towards the closest ZPA Public Service Edge for management | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| SessionStatus | The status of the session. The expected values for this field are:ZPN_STATUS_AUTHENTICATED: ZPA Private Service Edge successfully authenticated in ZPAZPN_STATUS_AUTH_FAILED: ZPA Private Service Edge failed to authenticate in ZPAZPN_STATUS_DISCONNECTED: ZPA Private Service Edge disconnected from a ZPA Service Edge | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| PackageVersion | The ZPA Private Service Edge package version | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| Platform | The host platform | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| ZEN | The ZPA Public Service Edge that was selected for the connection | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| ServiceEdge | The ZPA Service Edge name | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| ServiceEdgeGroup | The ZPA Service Edge group name | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| PrivateIP | The private IP address of the ZPA Private Service Edge | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| Latitude | The latitude coordinate of the ZPA Private Service Edge location | %[OPT]f%[OPT]o |
| Longitude | The longitude coordinate of the ZPA Private Service Edge location | %[OPT]f%[OPT]o |
| CountryCode | The country code | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| TimestampAuthentication | Timestamp in microseconds when the ZPA Private Service Edge was authenticated | %[OPT]s%[OPT]j%[OPT]J |
| TimestampUnAuthnetication | Timestamp in microseconds when the ZPA Private Service Edge was unauthenticated | %[OPT]s%[OPT]j%[OPT]J |
| CPUUtilization | The CPU utilization in % | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| MemUtilization | The memory utilization in % | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| InterfaceDefRoute | The name of the interface to default route | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| DefRouteGW | The IP address of the gateway to default route | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| PrimaryDNSResolver | The IP address of the primary DNS resolver | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| HostStartTime | Time in seconds at which host was started | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| ServiceEdgeStartTime | Time in seconds at which the ZPA Private Service Edge was started | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| NumOfInterfaces | The number of interfaces on the ZPA Private Service Edge host | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| BytesRxInterface | The bytes received on the interface | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| PacketsRxInterface | The packets received on the interface | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| ErrorsRxInterface | The errors received on the interface | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| DiscardsRxInterface | The discards received on the interface | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| BytesTxInterface | The bytes transmitted on the interface | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| PacketsTxInterface | The packets transmitted on the interface | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| DiscardsTxInterface | The discards transmitted on the interface | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| ErrorsTxInterface | The errors transmitted on the interface | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| TotalBytesRx | The total bytes received | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| TotalBytesTx | The total bytes transmitted | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| MicroTenantID | The Microtenant ID of the ZPA Private Service Edge | %[OPT]s%[OPT]j |
[]{"LogTimestamp": "Wed Dec  1 10:38:41 2021","Customer": "ayyappats","SessionID": "W9zkTJ90MQjP/1wmYZo/","SessionType": "ZPN_TUNNEL_CONTROL","SessionStatus": "ZPN_STATUS_AUTHENTICATED","Version": "21.268.1-341-g71d6f30-asan","PackageVersion": "","Platform": "el7","ZEN": "ZPA-zdx3","ServiceEdge": "PB1-1637740498039","ServiceEdgeGroup": "PB1","PrivateIP": "10.66.96.147","PublicIP": "199.168.150.161","Latitude": 0.000000,"Longitude": 0.000000,"CountryCode": "","TimestampAuthentication": "2021-12-01T10:34:42.067Z","TimestampUnAuthentication": "","CPUUtilization": 0,"MemUtilization": 3,"InterfaceDefRoute": "","DefRouteGW": "10.66.96.254","PrimaryDNSResolver": "10.66.98.1","HostStartTime": "1916930","ServiceEdgeStartTime": "1638354879","NumOfInterfaces": 2,"BytesRxInterface": 15435341381,"PacketsRxInterface": 144152768,"ErrorsRxInterface": 0,"DiscardsRxInterface": 2058,"BytesTxInterface": 22304497040,"PacketsTxInterface": 149703945,"ErrorsTxInterface": 0,"DiscardsTxInterface": 0,"TotalBytesRx": 5257,"TotalBytesTx": 7543, "MicroTenantID": "145257480799129312"}