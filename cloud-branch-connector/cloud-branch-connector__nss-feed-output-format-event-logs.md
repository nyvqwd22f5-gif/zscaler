# NSS Feed Output Format: Event Logs
Source: https://help.zscaler.com/cloud-branch-connector/nss-feed-output-format-event-logs
PDF: https://help.zscaler.com/pdf/com/en/1459131.pdf

The Event NSS feed specifies the data from the Event logs that the Nanolog Streaming Service (NSS) sends to the security information and event management (SIEM) system. You can configure an NSS feed by including one or more fields. The fields and their values display in the NSS feed output.
Zscaler Cloud Connector or Branch Connector generates the Event logs when a status change occurs for a Cloud Connector or Branch Connector health check, Zscaler data center reachability, a data plane health check, a software upgrade, a control plane health check, or a tunnel to Zscaler data centers.
Event Log Attributes
Each Event log has date and time, metadata, and event-specific attributes in it. The event-specific attributes depend on the type and severity of the event. Therefore, the values of the attributes change depending on the event type and severity.
There are 9 event-specific attributes in each Event log:
- Attribute 1 Type: The data type for the first event attribute.
- Attribute 1 Value: The value for the first event attribute.
- Attribute 2 Type: The data type for the second event attribute.
- Attribute 2 Value: The value for the second event attribute.
- Attribute 3 Type: The data type for the third event attribute.
- Attribute 3 Value: The value for the third event attribute.
- Attribute 4 Type: The data type for the fourth event attribute.
- Attribute 4 Value: The value for the fourth event attribute.
- Error Code: The error code associated with an event if an error code is available.
The following list shows all the possible Event Type/Severity combinations that can occur:
- [ZIA_TUNNEL/Info](#ZIATunnelInfo)
- [ZIA_TUNNEL/Error](#ZIATunnelError)
- [ZIA_GATEWAY/Warn](#ZIAGatewayWarn1)
- [ZIA_GATEWAY/Warn](#ZIAGatewayWarn2)
- [ZIA_GATEWAY/Error](#ZIAGatewayError)
- [ZIA_GATEWAY/Info](#ZIAGatewayInfo)
- [SVC_HEALTH_CHECK/Info](#SVCHealthCheckInfo)
- [SVC_HEALTH_CHECK/Error](#SVCHealthCheckError)
- [INST_HEALTH_CHECK/Warn](#InstHealthCheckWarn)
- [INST_HEALTH_CHECK/Info](#InstHealthCheckInfo)
- [CONTROL_PLANE/Info](#ControlPlaneInfo)
- [CONTROL_PLANE/Error](#ControlPlaneError)
- [DATA_PLANE/Info](#DataPlaneInfo)
- [DATA_PLANE/Error](#DataPlaneError)
- [UPGRADE_START/Info](#UpgradeStartInfo)
- [UPGRADE_END/Info](#UpgradeEndInfo)
- [UPGRADE_END/Error](#UpgradeEndError)
[]
- Event Name: ZIA_TUNNEL
- Severity: Info
- Attribute 1 Type: Previous State
- Attribute 1 Value: Inactive
- Attribute 2 Type: Current State
- Attribute 2 Value: Active
- Attribute 3 Type: Gateway Name
- Attribute 3 Value: <gw_name>
- Attribute 4 Type: Tunnel Destination IP Address
- Attribute 4 Value: <Tunnel Destination IP Address>
- Error Code: N/A
[]
- Event Name: ZIA_TUNNEL
- Severity: Error
- Attribute 1 Type: Previous State
- Attribute 1 Value: Active
- Attribute 2 Type: Current State
- Attribute 2 Value: Inactive
- Attribute 3 Type: Gateway Name
- Attribute 3 Value: <gw_name>
- Attribute 4 Type: Tunnel Destination IP Address
- Attribute 4 Value: <Tunnel Destination IP Address>
- Error Code: <error_code>
[]
- Event Name: ZIA_GATEWAY
- Severity: Warn
- Attribute 1 Type: Previous State
- Attribute 1 Value: Secondary
- Attribute 2 Type: Current State
- Attribute 2 Value: Primary
- Attribute 3 Type: Gateway Name
- Attribute 3 Value: <gw_name>
- Attribute 4 Type: N/A
- Attribute 4 Value: N/A
- Error Code: N/A
[]
- Event Name: ZIA_GATEWAY
- Severity: Warn
- Attribute 1 Type: Previous State
- Attribute 1 Value: Primary
- Attribute 2 Type: Current State
- Attribute 2 Value: Secondary
- Attribute 3 Type: Gateway Name
- Attribute 3 Value: <gw_name>
- Attribute 4 Type: N/A
- Attribute 4 Value: N/A
- Error Code: N/A
[]
- Event Name: ZIA_GATEWAY
- Severity: Error
- Attribute 1 Type: Previous State
- Attribute 1 Value: Active
- Attribute 2 Type: Current State
- Attribute 2 Value: Inactive
- Attribute 3 Type: Gateway Name
- Attribute 3 Value: <gw_name>
- Attribute 4 Type: N/A
- Attribute 4 Value: N/A
- Error Code: N/A
[]
- Event Name: ZIA_GATEWAY
- Severity: Info
- Attribute 1 Type: Previous State
- Attribute 1 Value: Inactive
- Attribute 2 Type: Current State
- Attribute 2 Value: Active
- Attribute 3 Type: Gateway Name
- Attribute 3 Value: <gw_name>
- Attribute 4 Type: N/A
- Attribute 4 Value: N/A
- Error Code: N/A
[]
- Event Name: SVC_HEALTH_CHECK
- Severity: Info
- Attribute 1 Type: Previous State
- Attribute 1 Value: Inactive
- Attribute 2 Type: Current State
- Attribute 2 Value: Active
- Attribute 3 Type: N/A
- Attribute 3 Value: N/A
- Attribute 4 Type: N/A
- Attribute 4 Value: N/A
- Error Code: N/A
[]
- Event Name: SVC_HEALTH_CHECK
- Severity: Error
- Attribute 1 Type: Previous State
- Attribute 1 Value: Active
- Attribute 2 Type: Current State
- Attribute 2 Value: Inactive
- Attribute 3 Type: N/A
- Attribute 3 Value: N/A
- Attribute 4 Type: N/A
- Attribute 4 Value: N/A
- Error Code: N/A
[]
- Event Name: INST_HEALTH_CHECK
- Severity: Warn
- Attribute 1 Type: Previous State
- Attribute 1 Value: Active
- Attribute 2 Type: Current State
- Attribute 2 Value: Degraded
- Attribute 3 Type: Number of active instances
- Attribute 3 Value: <integer>
- Attribute 4 Type: Total instances
- Attribute 4 Value: <integer>
- Error Code: N/A
[]
- Event Name: INST_HEALTH_CHECK
- Severity: Info
- Attribute 1 Type: Previous State
- Attribute 1 Value: Degraded
- Attribute 2 Type: Current State
- Attribute 2 Value: Active
- Attribute 3 Type: Number of active instances
- Attribute 3 Value: <integer>
- Attribute 4 Type: Total instances
- Attribute 4 Value: <integer>
- Error Code: N/A
[]
- Event Name: CONTROL_PLANE
- Severity: Info
- Attribute 1 Type: Previous State
- Attribute 1 Value: Inactive
- Attribute 2 Type: Current State
- Attribute 2 Value: Active
- Attribute 3 Type: N/A
- Attribute 3 Value: N/A
- Attribute 4 Type: N/A
- Attribute 4 Value: N/A
- Error Code: <error_code>
[]
- Event Name: CONTROL_PLANE
- Severity: Error
- Attribute 1 Type: Previous State
- Attribute 1 Value: Active
- Attribute 2 Type: Current State
- Attribute 2 Value: Inactive
- Attribute 3 Type: N/A
- Attribute 3 Value: N/A
- Attribute 4 Type: N/A
- Attribute 4 Value: N/A
- Error Code: N/A
[]
- Event Name: DATA_PLANE
- Severity: Info
- Attribute 1 Type: Previous State
- Attribute 1 Value: Inactive
- Attribute 2 Type: Current State
- Attribute 2 Value: Active
- Attribute 3 Type: N/A
- Attribute 3 Value: N/A
- Attribute 4 Type: N/A
- Attribute 4 Value: N/A
- Error Code: N/A
[]
- Event Name: DATA_PLANE
- Severity: Error
- Attribute 1 Type: Previous State
- Attribute 1 Value: Active
- Attribute 2 Type: Current State
- Attribute 2 Value: Inactive
- Attribute 3 Type: N/A
- Attribute 3 Value: N/A
- Attribute 4 Type: N/A
- Attribute 4 Value: N/A
- Error Code: N/A
[]
- Event Name: UPGRADE_START
- Severity: Info
- Attribute 1 Type: Current Version
- Attribute 1 Value: <version>
- Attribute 2 Type: New Version
- Attribute 2 Value: <version_1>
- Attribute 3 Type: Package Name
- Attribute 3 Value: <janus>
- Attribute 4 Type: N/A
- Attribute 4 Value: N/A
- Error Code: N/A
[]
- Event Name: UPGRADE_END
- Severity: Info
- Attribute 1 Type: Current Version
- Attribute 1 Value: <version>
- Attribute 2 Type: Upgrade Status
- Attribute 2 Value: Success for Info, Fail for Error
- Attribute 3 Type: Package Name
- Attribute 3 Value: <janus/edgeconnector>
- Attribute 4 Type: N/A
- Attribute 4 Value: N/A
- Error Code: N/A
[]
- Event Name: UPGRADE_END
- Severity: Error
- Attribute 1 Type: Current Version
- Attribute 1 Value: <version>
- Attribute 2 Type: Upgrade Status
- Attribute 2 Value: Success for Info, Fail for Error
- Attribute 3 Type: Package Name
- Attribute 3 Value: <janus/edgeconnector>
- Attribute 4 Type: N/A
- Attribute 4 Value: N/A
- Error Code: N/A
The following tables display information about the Event fields and possible values for those fields.
Date/Time
| **Field** | **Description** | **Example** |
| --------- | --------------- | ----------- |
| %d{inteventtime} | Event time in epoch format | 1687170925 |
| %d{abstime} | Event time if logs are delayed | 0 |
| %s{time} | Time at which events are generated | Mon Oct 14 03:35:25 2024 |
| %s{tz} | Time zone specified when configuring the NSS feed | GMT |
| %02d{ss} | Second of timestamp (0–59) | 25 |
| %02d{mm} | Minute of timestamp (0–59) | 35 |
| %02d{hh} | Hour of timestamp (0-23) | 03 |
| %02d{dd} | Day of timestamp (1–31) | 14 |
| %02d{mth} | Month of timestamp (1-12) | 10 |
| %04d{yyyy} | Year of timestamp | 2024 |
| %s{day} | Name of the day | Mon |
| %s{mon} | Name of the month | Oct |
| %s{rtime} | Log time at which NSS receives the logs | Mon Oct 14 03:35:28 PDT 2024 |
| %s{rmon} | Name of the month | Oct |
Metadata
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
| **Field** | **Description** | **Example** |
| --------- | --------------- | ----------- |
| %s{company} | Company name | Test2 |
| %s{location} | Location name | TempLoc |
| %s{name} | Cloud Connector or Branch Connector name | Instance 5 |
| %s{vm_name} | Cloud Connector or Branch Connector virtual machine (VM) name | zs-cc-vps-xxxx |
| %s{group_name} | Cloud Connector or Branch Connector group name | zs-cc-vpc-xxxx-us-east-2-x |
| %s{platform_name} | Cloud Connector or Branch Connector platform name | AWS |
| %s{platformgeo_name} | Cloud Connector or Branch Connector platform geolocation name | Columbus, United States |
| %s{region_name} | Region name | vk_location-us-east-2-x |
| %s{connector_type} | The type of connector | CC |
| %s{event_name} | Event type | VM_HEALTHZIA_TUNNELZIA_GWSVC_HEALTH_CHKINST_HEALTH_CHKCTL_PLANEDATA_PLANEUPGRADE_STUPGRADE_END |
| %s{category} | Category | TRAFF_FWDCONN_VMCONN_INST |
| %s{severity} | Severity | ERRINFOWARN |
Events
| **Field** | **Description** | **Example** |
| --------- | --------------- | ----------- |
| %s{attr1_name}, %s{attr1_val} | Attribute 1 name, Attribute 1 string value | prev_state, Inactive |
| %s{attr2_name},%s{attr2_val} | Attribute 2 name, Attribute 2 string value | curr_state, Active |
| %s{attr3_name}, %s{attr3_val} | Attribute 3 name, Attribute 3 string value | gid, 613x53 |
| %s{attr4_name}, %s{attr4_val} | Attribute 4 name, Attribute 4 string value | gwip, 192.0.2.1 |
| %s{error_code} | Error code (if any) | None |
| %s{account_id} | Account ID (alphanumeric string) | subscription_id2 |