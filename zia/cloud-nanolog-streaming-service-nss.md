# Cloud Nanolog Streaming Service (NSS)
Source: https://help.zscaler.com/zia/cloud-nanolog-streaming-service-nss

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /nssDownload/{nssId}`

Downloads the NSS server virtual appliance information based on the specified NSS server ID in a .ova format. To learn more, see [About NSS Servers](/zia/about-nss-servers).

**Tags:** Cloud Nanolog Streaming Service (NSS)
**Consumes:** application/json
**Produces:** application/octet-stream

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| nssId | path | integer | Yes | Specifies the NSS server ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /nssFeeds`

Retrieves the cloud NSS feeds configured in the ZIA Admin Portal

**Tags:** Cloud Nanolog Streaming Service (NSS)
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| feedType | query | string | No | The cloud NSS feed type |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[ZmanageNssFeed] |

## `POST /nssFeeds`

Adds a new cloud NSS feed. To learn more, see [Adding Cloud NSS Feeds](/zia/adding-cloud-nss-feeds).

**Tags:** Cloud Nanolog Streaming Service (NSS)
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | ZmanageNssFeed | Yes | The cloud NSS feed configuration |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | ZmanageNssFeed |

## `GET /nssFeeds/feedOutputDefaults`

Retrieves the default cloud NSS feed output format for different log types

**Tags:** Cloud Nanolog Streaming Service (NSS)
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| type | query | string | No | The type of logs that you are streaming |
| multiFeedType | query | string | No | This field is used to set the multi-feed type to Tunnel |
| fieldFormat | query | string | No | The feed output type of your SIEM |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | object |

## `GET /nssFeeds/testConnectivity/{feedId}`

Tests the connectivity of cloud NSS feed based on the specified ID

**Tags:** Cloud Nanolog Streaming Service (NSS)
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| feedId | path | integer | Yes | Unique identifier for the cloud NSS feed |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | CloudNssSiemConfiguration |

## `POST /nssFeeds/validateFeedFormat`

Validates the cloud NSS feed format and returns the validation result

**Tags:** Cloud Nanolog Streaming Service (NSS)
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| type | query | string | No | The cloud NSS log type |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | SMMsgStatusInfo |

## `DELETE /nssFeeds/{feedId}`

Deletes cloud NSS feed configuration based on the specified ID

**Tags:** Cloud Nanolog Streaming Service (NSS)
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| feedId | path | integer | Yes | Unique identifier for the cloud NSS feed |
| cloudNss | query | boolean | No | A Boolean value indicating whether the feed is cloud NSS feed |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /nssFeeds/{feedId}`

Retrieves information about cloud NSS feed based on the specified ID

**Tags:** Cloud Nanolog Streaming Service (NSS)
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| feedId | path | integer | Yes | Unique identifier for the cloud NSS feed |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | ZmanageNssFeed |

## `PUT /nssFeeds/{feedId}`

Updates cloud NSS feed configuration based on the specified ID. To learn more, see [Adding Cloud NSS Feeds](/zia/adding-cloud-nss-feeds).

**Tags:** Cloud Nanolog Streaming Service (NSS)
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | ZmanageNssFeed | Yes | The cloud NSS feed configuration |
| feedId | path | integer | Yes | Unique identifier for the cloud NSS feed |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | ZmanageNssFeed |

## `GET /nssServers`

Retrieves a list of registered NSS servers. To learn more, see [About NSS Servers](/zia/about-nss-servers).

**Tags:** Cloud Nanolog Streaming Service (NSS)
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| type | query | string | No | The server type |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[SwNode] |
| 401 | Unauthorized |  |
| 500 | Internal Server Error |  |

## `POST /nssServers`

Adds a new NSS server. To learn more, see [Adding NSS Servers](/zia/adding-nss-servers).

**Tags:** Cloud Nanolog Streaming Service (NSS)
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | NssNode | No | NSS server information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | SwNode |
| 201 | Created | SwNode |
| 401 | Unauthorized |  |
| 500 | Internal Server Error |  |

## `DELETE /nssServers/{nssId}`

Deletes an NSS server based on the specified ID

**Tags:** Cloud Nanolog Streaming Service (NSS)
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| nssId | path | integer | Yes | Specifies the NSS ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | NSS server deleted successfully |  |
| 401 | Unauthorized |  |
| 404 | Not Found |  |
| 500 | Internal Server Error |  |

## `GET /nssServers/{nssId}`

Retrieves the registered NSS server based on the specified ID

**Tags:** Cloud Nanolog Streaming Service (NSS)
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| nssId | path | integer | Yes | Specifies the NSS ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | SwNode |
| 401 | Unauthorized |  |
| 404 | Not Found |  |
| 500 | Internal Server Error |  |

## `PUT /nssServers/{nssId}`

Updates an NSS server based on the specified ID

**Tags:** Cloud Nanolog Streaming Service (NSS)
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| nssId | path | integer | Yes | Specifies the NSS ID |
| body | body | NssNode | No | NSS server information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | SwNode |
| 401 | Unauthorized |  |
| 404 | Not Found |  |
| 500 | Internal Server Error |  |

## Models
### CloudNssSiemConfiguration
Cloud NSS SIEM configuration
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| authenticationToken | string | No | The authentication token value |
| authenticationUrl | string | No | Authentication URL applicable when SIEM type is set to Azure Sentinel |
| base64EncodedCertificate | string | No | Base64-encoded certificate |
| clientId | string | No | Client ID applicable when SIEM type is set to S3 or Azure Sentinel |
| clientSecret | string | No | Client secret applicable when SIEM type is set to S3 or Azure Sentinel |
| connectionHeaders | array[string] | No | The HTTP Connection headers |
| connectionURL | string | No | The HTTPS URL of the SIEM log collection API endpoint |
| grantType | string | No | Grant type applicable when SIEM type is set to Azure Sentinel |
| lastSuccessFullTest | integer (int32) | No | The timestamp of the last successful test. Value is in Unix time |
| maxBatchSize | integer (int32) | No | The maximum batch size in KB |
| nssType | string | No | NSS type |
| oauthAuthentication | boolean | No | A Boolean value indicating whether OAuth 2.0 authentication is enabled or not |
| scope | string | No | Scope applicable when SIEM type is set to Azure Sentinel |
| siemType | string | No | Cloud NSS SIEM type |
| testConnectivityCode | integer (int32) | No | The code from the last test |
| testConnectivityStatus | string | No | The connectivity test status |

### EntityIdName
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| deleted | boolean | No |  |
| description | string | No |  |
| getlId | integer (int64) | No |  |
| id | integer (int32) | No |  |
| name | string | No |  |
| pid | integer (int32) | No |  |

### EntityReference
This is an immutable reference to an entity that mainly consists of an ID and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### NssNode
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| icapSvrId | integer (int32) | No | The ICAP server ID |
| id | integer (int32) | No | System-generated identifier for the NSS server |
| name | string | No | NSS server name |
| state | string | No | The health of the NSS server |
| status | string | No | Enables or disables the status of the NSS server |
| type | string | No | The server type. The NSS for Web type is selected by default. |

### NssWebApplication
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| backendName | string | No |  |
| deprecated | boolean | No |  |
| extended | boolean | No |  |
| misc | boolean | No |  |
| name | string | No |  |
| originalName | string | No |  |
| val | integer (int32) | No |  |
| webApplicationClass | string | No |  |

### SMMsgStatusInfo
Error message information that is returned when an invalid pattern is identified within a custom DLP dictionary
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| errMsg | string | No |  |
| errParameter | string | No |  |
| errPosition | integer (int32) | No |  |
| errSuggestion | string | No |  |
| idList | array[integer (int32)] | No |  |
| status | string (byte) | No |  |

### SwNode
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| icapSvrId | integer (int32) | No | The ICAP server ID |
| id | integer (int32) | No | System-generated identifier of the NSS server based on the software platform |
| name | string | No | NSS server name |
| state | string | No | The health of the NSS server |
| status | string | No | Enables or disables the status of the NSS server |

### ZmanageNssFeed
Cloud NSS feed configuration
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| actionFilter | string | No | Policy action filter |
| activity | array[string] | No | CASB activity filter |
| advUserAgents | array[string] | No | Filter based on custom user agent strings |
| advancedThreats | array[string] | No | Advanced threats filter |
| alerts | array[string] | No | Alert filter |
| auditLogType | array[string] | No | Audit log type filter |
| authenticationToken | string | No | The authentication token value |
| authenticationUrl | string | No | Authentication URL applicable when SIEM type is set to Azure Sentinel |
| base64EncodedCertificate | string | No | Base64-encoded certificate |
| buckets | array[EntityIdName] | No | Filter based on public cloud storage buckets |
| casbAction | array[string] | No | CASB policy action filter |
| casbApplications | array[string] | No | CASB application filter |
| casbFileType | array[string] | No | Endpoint DLP file type filter |
| casbFileTypeSuperCategories | array[string] | No | Endpoint DLP file type category filer |
| casbPolicyTypes | array[string] | No | CASB policy type filter |
| casbSeverity | array[string] | No | Zscaler's Cloud Access Security Broker (CASB) severity filter |
| casbTenant | array[EntityIdName] | No | CASB tenant filter |
| channelName | array[string] | No | Collaboration channel name filter |
| clientDestinationIps | array[string] | No | Client's destination IPv4 addresses in Firewall policy |
| clientDestinationPorts | array[string] | No | Firewall logs filter based on a client's destination |
| clientId | string | No | Client ID applicable when SIEM type is set to S3 or Azure Sentinel |
| clientIps | array[string] | No | Filter to limit the logs based on a client's public IPv4 addresses |
| clientSecret | string | No | Client secret applicable when SIEM type is set to S3 or Azure Sentinel |
| clientSourceIps | array[string] | No | Filter based on a client's source IPv4 address in the Firewall policy |
| clientSourcePorts | array[string] | No | Firewall log filter based on a client's source ports |
| clientType | array[string] | No | The client type filter |
| connectionHeaders | array[string] | No | The HTTP Connection headers |
| connectionStatus | array[string] | No | The connection status filter |
| connectionURL | string | No | The HTTPS URL of the SIEM log collection API endpoint |
| countries | array[string] | No | Countries filter in the Firewall policy |
| customDownloadFiletype | array[string] | No | Filter to limit logs based on the [custom or user-defined file types](/zia/configuring-custom-file-types) downloaded during the transaction. To obtain the list of custom file types, use `GET /customFileTypes`. |
| customEscapedCharacter | array[string] | No | Characters that need to be encoded using hex when they appear in URL, Host, or Referrer. This is an optional field. |
| customUploadFiletype | array[string] | No | Filter to limit logs based on the [custom or user-defined file types](/zia/configuring-custom-file-types) uploaded during the transaction. To obtain the list of custom file types, use `GET /customFileTypes`. |
| departments | array[EntityIdName] | No | Department filter |
| direction | string | No | Traffic direction filter specifying inbound or outbound |
| dlpDictionaries | array[EntityReference] | No | DLP dictionary filter |
| dlpEngines | array[EntityReference] | No | DLP engine filter |
| dnsActions | array[string] | No | DNS Control policy action filter |
| dnsRequestTypes | array[string] | No | DNS request types filter |
| dnsResponseTypes | array[string] | No | DNS response types filter |
| dnsResponses | array[string] | No | DNS responses filter |
| domains | array[string] | No | Filter to limit the logs to sessions associated with specific domains |
| downloadTime | array[string] | No | Download time filter |
| durations | array[string] | No | Filter based on time durations |
| emailDLPLogType | array[string] | No | Email DLP record type filter |
| emailDlpPolicyAction | string | No | Action filter for Email DLP log type |
| endPointDLPLogType | array[string] | No | Endpoint DLP log type filter |
| epsRateLimit | integer (int32) | No | Event per second limit |
| event | string | No | CASB event filter |
| externalCollaborators | array[EntityReference] | No | Filter logs to specific recipients outside your organization |
| externalOwners | array[EntityReference] | No | Filter logs associated with file owners (inside or outside your organization) who are not provisioned to ZIA services |
| feedOutputFormat | string | No | Output format used for the feed |
| feedStatus | string | No | The status of the feed |
| fileName | array[string] | No | Filter based on the file name |
| fileSizes | array[string] | No | File size filter |
| fileSource | array[string] | No | Filter based on the file source |
| fileTypeCategories | array[string] | No | Filter based on the file type in download |
| fileTypeSuperCategories | array[string] | No | Filter based on the category of file type in download |
| firewallActions | array[string] | No | Firewall and IPS Control policy actions filter |
| firewallLoggingMode | string | No | Filter based on the Firewall Filtering policy logging mode |
| fullUrls | array[string] | No | Filter to limit the logs based on specific full URLs |
| grantType | string | No | Grant type applicable when SIEM type is set to Azure Sentinel |
| hostNames | array[string] | No | Filter to limit the logs based on specific hostnames |
| id | integer (int32) | No | Unique identifier of the cloud NSS feed |
| inBoundBytes | array[string] | No | Filter based on inbound bytes |
| internalCollaborators | array[EntityReference] | No | Filter logs to specific recipients within your organization |
| internalIps | array[string] | No | Filter based on internal IPv4 addresses |
| itsmObjectType | array[EntityReference] | No | ITSM object type filter |
| jsonArrayToggle | boolean | No | A Boolean value indicating whether streaming of logs in JSON array format (e.g., [{JSON1},{JSON2}]) is enabled or disabled for the JSON feed output type |
| lastSuccessFullTest | integer (int32) | No | The timestamp of the last successful test. Value is in Unix time. |
| locations | array[EntityIdName] | No | Location filter |
| malwareClasses | array[string] | No | Malware category filter |
| malwareNames | array[string] | No | Filter based on malware names |
| maxBatchSize | integer (int32) | No | The maximum batch size in KB |
| messageSize | array[string] | No | Message size filter |
| name | string | No | The name of the cloud NSS feed |
| natActions | array[string] | No | NAT Control policy actions filter |
| nssFeedType | string | No | NSS feed format type (e.g. CSV, syslog, Splunk Common Information Model (CIM), etc. |
| nssLogType | string | No | The type of NSS logs that are streamed (e.g. Web, Firewall, DNS, Alert, etc.) |
| nssType | string | No | NSS type |
| nwApplications | array[string] | No | Firewall network applications filter |
| nwServices | array[EntityReference] | No | Firewall network services filter |
| oauthAuthentication | boolean | No | A Boolean value indicating whether OAuth 2.0 authentication is enabled or not |
| objectName | array[string] | No | CRM object name filter |
| objectType | array[string] | No | CRM object type filter |
| objectType1 | array[string] | No | CASB activity object type filter |
| objectType2 | array[string] | No | CASB activity object type filter if applicable |
| outBoundBytes | array[string] | No | Filter based on outbound bytes |
| pageRiskIndexes | array[string] | No | Page Risk Index filter |
| policyReasons | array[string] | No | Policy reason filter |
| projectName | array[string] | No | Repository project name filter |
| protocolTypes | array[string] | No | Protocol types filter |
| refererUrls | array[string] | No | Referrer URL filter |
| repoName | array[string] | No | Repository name filter |
| requestMethods | array[string] | No | Request methods filter |
| requestSizes | array[string] | No | Request size filter |
| responseCodes | array[string] | No | Response codes filter |
| responseSizes | array[string] | No | Response size filter |
| rules | array[EntityReference] | No | Policy rules filter (e.g., Firewall Filtering or DNS Control rule filter) |
| scanTime | array[string] | No | Scan time filter |
| scope | string | No | Scope applicable when SIEM type is set to Azure Sentinel |
| senderName | array[EntityIdName] | No | Filter based on sender or owner name |
| serverDestinationIps | array[string] | No | Filter based on the server's destination IPv4 addresses in Firewall policy |
| serverIps | array[string] | No | Filter to limit the logs based on the server's IPv4 addresses |
| serverSourceIps | array[string] | No | Filter based on the server's source IPv4 addresses in Firewall policy |
| serverSourcePorts | array[string] | No | Firewall log filter based on the traffic destination name |
| sessionCounts | array[string] | No | Firewall logs filter based on the number of sessions |
| sessionStatus | array[string] | No | The session status filter |
| siemType | string | No | Cloud NSS SIEM type |
| testConnectivityCode | integer (int32) | No | The code from the last test |
| threatNames | array[string] | No | Filter based on threat names |
| timeZone | string | No | Specifies the time zone that must be used in the output file |
| trafficForwards | array[string] | No | Filter based on the firewall traffic forwarding method |
| transactionSizes | array[string] | No | Transaction size filter |
| tunnelDestIps | array[string] | No | Destination IPv4 addresses of tunnels |
| tunnelIps | array[string] | No | Filter based on tunnel IPv4 addresses in Firewall policy |
| tunnelSourceIps | array[string] | No | Source IPv4 addresses of tunnels |
| tunnelSourcePort | array[string] | No | Filter based on the tunnel source port |
| tunnelTypes | array[string] | No | Tunnel type filter |
| uploadFileTypeCategories | array[string] | No | Filter to limit logs based on the file types uploaded during the transaction |
| uploadFileTypeSuperCategories | array[string] | No | Filter to limit logs based on the categories of file types uploaded during the transaction |
| urlCategories | array[EntityReference] | No | URL category filter |
| urlClasses | array[string] | No | URL category filter |
| urlSuperCategories | array[string] | No | URL supercategory filter |
| userAgents | array[string] | No | Predefined user agents filter |
| userObfuscation | string | No | Specifies whether user obfuscation is enabled or disabled |
| users | array[EntityIdName] | No | User filter |
| vpnCredentials | array[EntityIdName] | No | Filter based on specific VPN credentials |
| webApplicationClasses | array[string] | No | Cloud application categories Filter |
| webApplications | array[NssWebApplication] | No | Cloud applications filter |
| webTrafficForwards | array[string] | No | Filter based on the web traffic forwarding method |
