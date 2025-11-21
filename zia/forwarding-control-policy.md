# Forwarding Control Policy
Source: https://help.zscaler.com/zia/forwarding-control-policy

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /dedicatedIPGateways/lite`

Retrieves a list of dedicated IP gateways. To learn more, see [About Dedicated IP Gateways](/zia/about-dedicated-ip-gateways).

**Tags:** Forwarding Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer | No | Specifies the page offset |
| pageSize | query | integer | No | Specifies the page size |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[DedicatedIPGateway] |

## `GET /forwardingRules`

Gets the list of [forwarding rules](/zia/configuring-forwarding-policy) configured in the ZIA Admin Portal. To learn about forwarding control, see [About Forwarding Control](/zia/about-forwarding-policies).

**Tags:** Forwarding Control Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[ForwardingRule] |

## `POST /forwardingRules`

Adds a new forwarding rule. To learn more, see [Configuring Forwarding Policy](/zia/configuring-forwarding-policy).

**Tags:** Forwarding Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | ForwardingRule | No | Forwarding rule information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | ForwardingRule |

## `DELETE /forwardingRules/{ruleId}`

Deletes a forwarding rule using the specified ID

**Tags:** Forwarding Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | The ID of the forwarding rule |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /forwardingRules/{ruleId}`

Gets information for a forwarding rule using the specified ID

**Tags:** Forwarding Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | The ID of the forwarding rule |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful operation | ForwardingRule |

## `PUT /forwardingRules/{ruleId}`

Updates information for a forwarding rule using the specified ID

**Tags:** Forwarding Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | The ID of the forwarding rule |
| body | body | ForwardingRule | No | Forwarding rule infomration |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | ForwardingRule |

## `GET /proxies`

Retrieves a list of all proxies configured for third-party proxy services. To learn more, see [About Third-Party Proxies](/zia/about-third-party-proxies).

**Tags:** Forwarding Control Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[Proxy] |

## `POST /proxies`

Adds a new proxy for a third-party proxy service. To learn more, see [Configuring Third-Party Proxies](/zia/configuring-third-party-proxies).

**Tags:** Forwarding Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | Proxy | No | Information about the proxy |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Proxy |

## `GET /proxies/lite`

Retrieves a list of all proxies configured for third-party proxy services

**Tags:** Forwarding Control Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[Proxy] |

## `DELETE /proxies/{proxyId}`

Deletes an existing proxy based on the specified ID

**Tags:** Forwarding Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| proxyId | path | integer | Yes | Unique identifier for the proxy |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /proxies/{proxyId}`

Retrieves the proxy information based on the specified ID

**Tags:** Forwarding Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| proxyId | path | integer | Yes | Unique identifier for the proxy |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Proxy |

## `PUT /proxies/{proxyId}`

Updates an existing proxy based on the specified ID

**Tags:** Forwarding Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| proxyId | path | integer | Yes | Unique identifier for the proxy |
| body | body | Proxy | No | Information about the proxy |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Proxy |

## `GET /proxyGateways`

Retrieves the proxy gateway information. To learn more, see [About Gateways for Proxies](/zia/about-gateways-proxies).

**Tags:** Forwarding Control Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[ProxyGateway] |

## `GET /proxyGateways/lite`

Retrieves the name and ID of the proxy. To learn more, see [About Gateways for Proxies](/zia/about-gateways-proxies).

**Tags:** Forwarding Control Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[ProxyGateway] |

## `GET /zpaGateways`

Gets the list of Zscaler Private Access (ZPA) gateways configured in the ZIA Admin Portal. To learn about ZPA gateways, see [About Zscaler Private Access Gateway](/zia/about-zpa-gateway).

**Tags:** Forwarding Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | The search string used to match against a ZPA gateway name or an associated Server Group name |
| appSegment | query | array | No | Filters the list by Application Segment |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[ZpaGateway] |

## `POST /zpaGateways`

Adds a new custom ZPA gateway. The ZPA gateway can be used in a [forwarding control policy](/zia/configuring-forwarding-policy) to forward traffic to ZPA for [Source IP Anchoring](/zia/about-source-ip-anchoring). To learn more, see [Configuring ZPA Gateway](/zia/configuring-forwarding-policy).

**Tags:** Forwarding Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | ZpaGateway | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | ZpaGateway |

## `DELETE /zpaGateways/{gatewayId}`

Deletes a ZPA gateway using the specified ID

**Tags:** Forwarding Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| gatewayId | path | integer | Yes | The ID of the ZPA gateway |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /zpaGateways/{gatewayId}`

Gets information for a ZPA gateway using the specified ID

**Tags:** Forwarding Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| gatewayId | path | integer | Yes | The ID of the ZPA gateway |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | ZpaGateway |

## `PUT /zpaGateways/{gatewayId}`

Updates information for a ZPA gateway using the specified ID

**Tags:** Forwarding Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| gatewayId | path | integer | Yes | The ID of the ZPA gateway |
| body | body | ZpaGateway | No | ZPA gateway information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | ZpaGateway |

## Models
### AppSegment
Application Segment information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| externalId | integer (int64) | No | Indicates the external ID. Applicable only when this reference is of an external entity. |
| id | integer (int32) | No | A unique identifier assigned to the Application Segment |
| name | string | No | The name of the Application Segment |
| zpaTenantId | integer (int64) | No | ID of the ZPA tenant where the Application Segment is configured |

### DedicatedIPGateway
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| createTime | integer (int32) | No | Timestamp of when the dedicated IP gateway was created |
| default | boolean | No | The gateway that is included by default |
| description | string | No | Additional notes or information about the gateway |
| id | integer (int32) | No | System-generated dedicated IP gateway identifier |
| lastModifiedBy | EntityReference | No | Last user that modified the dedicated IP gateway |
| lastModifiedTime | integer (int32) | No | Timestamp of when the dedicated IP gateway was last modified |
| name | string | No | Dedicated IP gateway name |
| primaryDataCenter | EntityReference | No | The location of the primary data center for the gateway |
| secondaryDataCenter | EntityReference | No | The location of the secondary data center for the gateway. The secondary data center location is used when the primary data center is unreachable. |

### EntityReference
This is an immutable reference to an entity that mainly consists of id and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### ForwardingRule
Forwarding rule information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| departments | array[EntityReference] | No | Name-ID pairs of the departments to which the forwarding rule applies. If not set, the rule applies to all departments. |
| description | string | No | Additional information about the forwarding rule |
| destAddresses | array[string] | No | List of destination IP addresses or FQDNs for which the rule is applicable. CIDR notation can be used for destination IP addresses. If not set, the rule is not restricted to a specific destination addresses unless specified by `destCountries`, `destIpGroups`, or `destIpCategories`. |
| destCountries | array[string] | No | Destination countries for which the rule is applicable. If not set, the rule is not restricted to specific destination countries. |
| destIpCategories | array[string] | No | List of destination IP categories to which the rule applies. If not set, the rule is not restricted to specific destination IP categories. |
| destIpGroups | array[EntityReference] | No | User-defined destination IP address groups to which the rule is applied. If not set, the rule is not restricted to a specific destination IP address group.
**Note**: For organizations that have enabled IPv6, the `destIpv6Groups` field lists the IPv6 source address groups for which the rule is applicable. |
| destIpv6Groups | array[EntityReference] | No | Destination IPv6 address groups for which the rule is applicable. If not set, the rule is not restricted to a specific source IPv6 address group.
**Note**: User-defined groups for IPv6 addresses are currently not supported. |
| deviceGroups | array[EntityReference] | No | Name-ID pairs of device groups for which the rule must be applied. This field is applicable for devices that are managed using Zscaler Client Connector. If no value is set, this field is ignored during the policy evaluation. |
| devices | array[EntityReference] | No | Name-ID pairs of devices for which the rule must be applied. Specifies devices that are managed using Zscaler Client Connector. If no value is set, this field is ignored during the policy evaluation. |
| ecGroups | array[EntityReference] | No | Name-ID pairs of the Zscaler Cloud Connector groups to which the forwarding rule applies |
| forwardMethod | string | Yes | The type of traffic forwarding method selected from the available options |
| groups | array[EntityReference] | No | Name-ID pairs of the user groups to which the forwarding rule applies. If not set, the rule applies to all groups. |
| id | integer (int32) | No | A unique identifier assigned to the forwarding rule |
| labels | array[EntityReference] | No | Labels that are applicable to the rule |
| lastModifiedBy | EntityReference | No | Admin user that last modified the rule. This field is not applicable for POST or PUT request. |
| lastModifiedTime | integer (int32) | No | Timestamp when the rule was last modified. This field is not applicable for POST or PUT request. |
| locationGroups | array[EntityReference] | No | Name-ID pairs of the location groups to which the forwarding rule applies |
| locations | array[EntityReference] | No | Name-ID pairs of the locations to which the forwarding rule applies. If not set, the rule is applied to all locations. |
| name | string | Yes | The name of the forwarding rule |
| nwApplicationGroups | array[EntityReference] | No | User-defined network service application groups to which the rule applied. If not set, the rule is not restricted to a specific network service application group. |
| nwApplications | array[string] | No | User-defined network service applications to which the rule applies. If not set, the rule is not restricted to a specific network service application. |
| nwServiceGroups | array[EntityReference] | No | User-defined network service group to which the rule applies. If not set, the rule is not restricted to a specific network service group. |
| nwServices | array[EntityReference] | No | User-defined network services to which the rule applies. If not set, the rule is not restricted to a specific network service.
**Note**: When the forwarding method is Proxy Chaining, only TCP-based network services are considered for policy match . |
| order | integer (int32) | No | The order of execution for the forwarding rule order |
| proxyGateway | EntityReference | No | The proxy gateway for which the rule is applicable. This field is applicable only for the Proxy Chaining forwarding method. |
| rank | integer (int32) | Yes | Admin rank assigned to the forwarding rule |
| resCategories | array[string] | No | List of destination domain categories to which the rule applies |
| srcIpGroups | array[EntityReference] | No | Source IP address groups for which the rule is applicable. If not set, the rule is not restricted to a specific source IP address group.
**Note**: For organizations that have enabled IPv6, the `srcIpv6Groups` field lists the IPv6 source address groups for which the rule is applicable. |
| srcIps | array[string] | No | User-defined source IP addresses for which the rule is applicable. If not set, the rule is not restricted to a specific source IP address. |
| srcIpv6Groups | array[EntityReference] | No | Source IPv6 address groups for which the rule is applicable. If not set, the rule is not restricted to a specific source IPv6 address group.
**Note**: User-defined groups for IPv6 addresses are currently not supported. |
| state | string | No | Indicates whether the forwarding rule is enabled or disabled |
| timeWindows | array[EntityReference] | No | The time interval at which the forwarding rule applies |
| type | string | No | The rule type selected from the available options |
| users | array[EntityReference] | No | Name-ID pairs of the users to which the forwarding rule applies. If not set, user criteria is ignored during policy enforcement. |
| zpaAppSegments | array[AppSegment] | No | The list of ZPA Application Segments for which this rule is applicable. This field is applicable only for the ZPA Gateway forwarding method. |
| zpaApplicationSegmentGroups | array[ZpaApplicationSegmentGroup] | No | List of ZPA Application Segment Groups for which this rule is applicable. This field is applicable only for the ECZPA forwarding method (used for Zscaler Cloud Connector). |
| zpaApplicationSegments | array[ZpaApplicationSegment] | No | List of ZPA Application Segments for which this rule is applicable. This field is applicable only for the ECZPA forwarding method (used for Zscaler Cloud Connector). |
| zpaBrokerRule | boolean | No | The predefined ZPA Broker Rule generated by Zscaler |
| zpaGateway | EntityReference | No | The ZPA Server Group for which this rule is applicable. Only the Server Groups that are associated with the selected Application Segments are allowed. This field is applicable only for the ZPA forwarding method. |

### Proxy
Proxy information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| address | string | Yes | The IP address or the FQDN of the third-party proxy service |
| base64EncodeXauHeader | boolean | No | Flag indicating whether the added X-Authenticated-User header is Base64 encoded. When enabled, the user ID is encoded using the Base64 encoding method. |
| cert | EntityReference | No | The root certificate used by the third-party proxy to perform SSL inspection. This root certificate is used by Zscaler to validate the SSL leaf certificates signed by the upstream proxy. The required root certificate appears in this drop-down list only if it is uploaded from the Administration > Root Certificates page. |
| description | string | No | Additional notes or information |
| id | integer (int32) | No | Proxy ID |
| insertXauHeader | boolean | No | Flag indicating whether X-Authenticated-User header is added by the proxy. Enable to automatically insert authenticated user ID to the HTTP header, X-Authenticated-User. |
| lastModifiedBy | EntityReference | No | Last user that modified the proxy |
| lastModifiedTime | integer (int32) | No | Timestamp of when the proxy was last modified |
| name | string | Yes | Proxy name |
| port | integer (int32) | Yes | The port number on which the third-party proxy service listens to the requests forwarded from Zscaler |
| type | string | No | Gateway type |

### ProxyGateway
Proxy gateway information. This is applicable only for traffic forwarding to a third-party proxy service.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| description | string | No | Additional notes or information about the gateway. This field is not applicable to the Lite API. |
| failClosed | boolean | No | Indicates whether fail close is enabled to drop the traffic or disabled to allow the traffic when both primary and secondary proxies defined in this gateway are unreachable. |
| id | integer (int32) | No | Unique identifier for the proxy |
| lastModifiedBy | object | No | The admin that modified the gateway last. This is a read-only field. This field is not applicable to the Lite API. |
| lastModifiedTime | integer (int32) | No | Timestamp when the gateway was last modified. This is a read-only field. This field is not applicable to the Lite API. |
| name | string | No | Name of the proxy. You can sort this column. |
| primaryProxy | object | No | The primary proxy for the gateway. This field is not applicable to the Lite API. |
| secondaryProxy | object | No | The secondary proxy for the gateway. This field is not applicable to the Lite API. |
| type | string | No | Proxy type |

### ZpaApplicationSegment
Information about the ZPA Application Segment
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| deleted | boolean | No | Indicates whether the ZPA Application Segment has been deleted |
| description | string | No | Additional information about the Application Segment |
| id | integer (int32) | No | A unique identifier assigned to the Application Segment |
| name | string | No | The name of the Application Segment |
| zpaId | integer (int64) | No | ID of the ZPA tenant where the Application Segment is configured |

### ZpaApplicationSegmentGroup
Information about the Application Segment Group
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| deleted | boolean | No | Indicates whether the ZPA Application Segment Group has been deleted |
| id | integer (int32) | No | A unique identifier assigned to the Application Segment Group |
| name | string | No | The name of the Application Segment Group |
| zpaAppSegmentsCount | integer (int32) | No | The number of ZPA Application Segments in the group |
| zpaId | integer (int64) | No | ID of the ZPA tenant where the Application Segment is configured |

### ZpaGateway
ZPA gateway information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| description | string | No | Additional details about the ZPA gateway |
| id | integer (int32) | No | A unique identifier assigned to the ZPA gateway |
| lastModifiedBy | EntityReference | No | Information about the admin user that last modified the ZPA gateway |
| lastModifiedTime | integer (int32) | No | Timestamp when the ZPA gateway was last modified |
| name | string | No | The name of the ZPA gateway |
| type | string | No | Indicates whether the ZPA gateway is configured for Zscaler Internet Access (using option `ZPA`) or Zscaler Cloud Connector (using option `ECZPA`) |
| zpaAppSegments | array[EntityReference] | No | All the Application Segments that are associated with the selected ZPA Server Group for which Source IP Anchoring is enabled |
| zpaServerGroup | EntityReference | No | The ZPA Server Group that is configured for Source IP Anchoring |
| zpaTenantId | integer (int64) | No | The ID of the ZPA tenant where Source IP Anchoring is configured |
