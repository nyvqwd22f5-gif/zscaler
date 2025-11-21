# About Private Service Edge Metrics Log Fields
Source: https://help.zscaler.com/unified/about-private-service-edge-metrics-log-fields
PDF: https://help.zscaler.com/pdf/com/en/1495981.pdf

The Log Streaming Service can send Private Service Edge Metrics log information for Private Applications to any third-party log analytics tool. By default, the Private Service Edge Metrics log type includes the fields listed in the following table for each log template (i.e., CSV, JSON, TSV). While configuring your log receiver, you can edit the default log stream content to capture only specific fields, and create a Custom log template.
- [View a Private Service Edge Metrics log example](#PseMetricsLogExample)
The following table includes descriptions and supported field format specifications for each field within the template. To learn more about the format specifications listed for each field, including examples, see [Log Field Format Specifications](/unified/understanding-log-stream-content-format).
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
| LogTimeStamp | Timestamp when the log was generated | %[OPT]s%[OPT]j%[OPT]J |
| PrivateSE | Name of the Private Service Edge for Private Applications | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| CPUUtilization | The maximum CPU usage in the past 5 minutes | %[OPT]s%[OPT]j%[OPT]J%[OPT]d |
| SystemMemoryUtilization | The memory utilization of the entire virtual machine (VM) | %[OPT]s%[OPT]j%[OPT]J%[OPT]d |
| ProcessMemoryUtilization | The memory utilization of the Private Service Edge for Private Applications process | %[OPT]s%[OPT]j%[OPT]J%[OPT]d |
| UsedTCPPortsIPv4 | The number of used TCP ports for an IPv4 connection | %[OPT]s%[OPT]j%[OPT]J%[OPT]d |
| UsedUDPPortsIPv4 | The number of used UDP ports for an IPv4 connection | %[OPT]s%[OPT]j%[OPT]J%[OPT]d |
| UsedTCPPortsIPv6 | The number of used TCP ports for an IPv6 connection | %[OPT]s%[OPT]j%[OPT]J%[OPT]d |
| UsedUDPPortsIPv6 | The number of used UDP ports for an IPv6 connection | %[OPT]s%[OPT]j%[OPT]J%[OPT]d |
| AvailablePorts | The number of usable ports | %[OPT]s%[OPT]j%[OPT]J%[OPT]d |
| SystemMaximumFileDescriptors | The number of total Private Service Edge for Private Applications system file descriptors | %[OPT]s%[OPT]j%[OPT]J%[OPT]d |
| SystemUsedFileDescriptors | The number of used Private Service Edge for Private Applications system file descriptors | %[OPT]s%[OPT]j%[OPT]J%[OPT]d |
| ProcessMaximumFileDescriptors | The number of total Private Service Edge for Private Applications process file descriptors | %[OPT]s%[OPT]j%[OPT]J%[OPT]d |
| ProcessUsedFileDescriptors | The number of used Private Service Edge for Private Applications process file descriptors | %[OPT]s%[OPT]j%[OPT]J%[OPT]d |
| AvailableDiskBytes | The number of free bytes available for the Private Service Edge for Private Applications | %[OPT]s%[OPT]j%[OPT]J%[OPT]d |
| MicroTenantID | The Microtenant ID of the Private Service Edge for Private Applications | %[OPT]s%[OPT]j |
[]{"LogTimestamp":"Fri May  6 11:40:00 2022,"PrivateSE":"TestPrivateServiceEdge","CPUUtilization":"1","SystemMemoryUtilization":%j{SystemMemoryUtilization},"ProcessMemoryUtilization":%j{ProcessMemoryUtilization},"UsedTCPPortsIPv4":"1","UsedUDPPortsIPv4":"4","UsedTCPPortsIPv6":"1","UsedUDPPortsIPv6":"5","AvailablePorts":"28223","SystemMaximumFileDescriptors":"960344","SystemUsedFileDescriptors":"1211","ProcessMaximumFileDescriptors":"421000","ProcessUsedFileDescriptors":"122","AvailableDiskBytes":"261886394368", "MicroTenantID": "145257480799129312"}