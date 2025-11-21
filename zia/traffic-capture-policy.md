# Traffic Capture Policy
Source: https://help.zscaler.com/zia/traffic-capture-policy

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /trafficCaptureRules`

Retrieves the list of Traffic Capture policy rules configured in the ZIA Admin Portal. To learn more, see [About Traffic Capture Policy](/zia/about-traffic-capture-policy).

**Tags:** Traffic Capture Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleName | query | string | No | Filter based on the rule name |
| ruleLabel | query | string | No | Filter based on the rule label |
| ruleLabelId | query | integer | No | Filter based on the rule label ID |
| ruleOrder | query | string | No | Filter based on the rule order |
| ruleDescription | query | string | No | Filter based on the rule description |
| ruleAction | query | string | No | Filter based on the rule action |
| location | query | string | No | Filter based on the location criteria used in the rules |
| department | query | string | No | Filter based on the department criteria used in the rules |
| group | query | string | No | Filter based on the group criteria used in the rules |
| user | query | string | No | Filter based on the user criteria used in the rules |
| device | query | string | No | Filter based on the device criteria used in the rules |
| deviceGroup | query | string | No | Filter based on the device group criteria used in the rules |
| deviceTrustLevel | query | string | No | Filter based on the device trust level criteria used in the rules |
| page | query | integer | No | Specifies the page offset |
| pageSize | query | integer | No | Specifies the page size. Default size is 5000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[TrafficCaptureRule] |

## `POST /trafficCaptureRules`

Creates a new Traffic Capture policy rule. To learn more about rule configuration, see [Configuring the Traffic Capture Policy](/zia/configuring-traffic-capture-policy).

**Tags:** Traffic Capture Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | TrafficCaptureRule | No | Specifies the rule details |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | TrafficCaptureRule |

## `GET /trafficCaptureRules/count`
Retrieves the rule count for the Traffic Capture policy based on the specified search criteria. If no search criteria are specified, the total number of Traffic Capture policy rules is retrieved by default.

**Tags:** Traffic Capture Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleName | query | string | No | Filter based on the rule name |
| ruleLabel | query | string | No | Filter based on the rule label |
| ruleLabelId | query | integer | No | Filter based on the rule label ID |
| ruleOrder | query | string | No | Filter based on the rule order |
| ruleDescription | query | string | No | Filter based on the rule description |
| ruleAction | query | string | No | Filter based on the rule action |
| location | query | string | No | Filter based on the location criteria used in the rules |
| department | query | string | No | Filter based on the department criteria used in the rules |
| group | query | string | No | Filter based on the group criteria used in the rules |
| user | query | string | No | Filter based on the user criteria used in the rules |
| device | query | string | No | Filter based on the device criteria used in the rules |
| deviceGroup | query | string | No | Filter based on the device group criteria used in the rules |
| deviceTrustLevel | query | string | No | Filter based on the device trust level criteria used in the rules |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | TrafficCaptureRule |

## `GET /trafficCaptureRules/order`

Retrieves the rule order information for the Traffic Capture policy, including the admin rank and rule order mappings and the maximum configured rule order.

**Tags:** Traffic Capture Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | TrafficCaptureRuleOrderInfo |

## `GET /trafficCaptureRules/ruleLabels`

Retrieves the list of rule labels associated with the Traffic Capture policy rules

**Tags:** Traffic Capture Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| searchByField | query | string | No | Search option based on specific rule fields |
| searchByValue | query | string | No | Search option based on specified values for rule fields |
| page | query | integer | No | Specifies the page offset |
| pageSize | query | integer | No | Specifies the page size. Default size is 1024. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[RuleLabelInfo] |

## `DELETE /trafficCaptureRules/{ruleId}`

Deletes the Traffic Capture policy rule based on the specified rule ID

**Tags:** Traffic Capture Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Specifies the rule ID. This value can be obtained using the `GET /trafficCaptureRules` request. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /trafficCaptureRules/{ruleId}`

Retrieves the Traffic Capture policy rule based on the specified rule ID

**Tags:** Traffic Capture Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Specifies the rule ID. This value can be obtained using the `GET /trafficCaptureRules` request. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | TrafficCaptureRule |

## `PUT /trafficCaptureRules/{ruleId}`

Updates information for the Traffic Capture policy rule based on the specified rule ID. To learn more about rule configuration, see [Configuring the Traffic Capture Policy](/zia/configuring-traffic-capture-policy).

**Tags:** Traffic Capture Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Specifies the rule ID. This value can be obtained using the `GET /trafficCaptureRules` request. |
| body | body | TrafficCaptureRule | No | Specifies the rule details |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | TrafficCaptureRule |

## Models
### EntityReference
This is an immutable reference to an entity that mainly consists of id and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### RuleLabelInfo
Rule label information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| id | integer (int32) | No | Rule label ID |
| name | string | No | Rule label name |
| orgId | integer (int32) | No | Organization ID |

### TrafficCaptureRule
Traffic Capture policy rule details. To learn more about the individual rule fields, see [Configuring the Traffic Capture Policy](/zia/configuring-traffic-capture-policy).
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| action | string | Yes | The action to be enforced when the traffic matches the rule criteria |
| appServiceGroups | array[EntityReference] | No | Application service groups to which the rule applies |
| defaultRule | boolean | No | A Boolean field that indicates whether this is a default rule by using the true value |
| departments | array[EntityReference] | No | Name-ID pairs of departments to which the rule applies. If no specific value is set, the rule applies to all departments. |
| description | string | No | Rule description |
| destAddresses | array[string] | No | Destination IP addresses (IPv4) or FQDNs to which the rule applies. Each IP entry can be an individual IP address (e.g., 192.0.2.1), a subnet or CIDR (e.g., 192.0.2.0/24), or an address range (e.g., 192.0.2.1 - 192.0.2.5). If no specific value is set, the rule is not restricted to a specific source IP address or FQDN. |
| destCountries | array[string] | No | Destination countries to which the rule applies. If no specific value is set, the rule applies to all destination countries. |
| destIpGroups | array[EntityReference] | No | Name-ID pairs of destination IP groups to which the rule applies. If no specific value is set, the rule is not restricted to specific destination IP groups.
**Note**: For organizations that have enabled IPv6, **destIpv6Groups** can be used to specify the destination IPv6 address groups to which the rule applies. |
| destIpv6Groups | array[EntityReference] | No | Name-ID pairs of destination IPv6 groups to which the rule applies. If no specific value is set, the rule is not restricted to specific destination IPv6 groups.
**Note**: User-defined groups for IPv6 addresses are currently not supported. |
| deviceGroups | array[EntityReference] | No | Name-ID pairs of device groups to which the rule applies |
| deviceTrustLevels | array[string] | No | Device trust levels to which the rule applies. If no specific value is set, the rule applies to all device trust levels. |
| devices | array[EntityReference] | No | Name-ID pairs of devices to which the rule applies |
| excludeSrcCountries | boolean | No | Indicates whether the countries specified in the **sourceCountries** field are included or excluded from the rule. A true value denotes that the specified source countries are excluded from the rule. A false value denotes that the rule is applied to the source countries if there is a match. |
| groups | array[EntityReference] | No | Name-ID pairs of groups to which the rule applies. If no specific value is set, the rule applies to all groups. |
| id | integer (int32) | No | A unique identifier of the rule |
| labels | array[EntityReference] | No | Labels associated with the rule |
| lastModifiedBy | EntityReference | No | The admin user who last modified the rule (using POST or PUT request) |
| lastModifiedTime | integer (int32) | No | Timestamp of when the rule was last modified (using POST or PUT request) |
| locationGroups | array[EntityReference] | No | Name-ID pairs of location groups to which the rule applies. If no specific value is set, the rule applies to all location groups. |
| locations | array[EntityReference] | No | Name-ID pairs of locations to which the rule applies. If no specific value is set, the rule applies to all locations. |
| name | string | Yes | Rule name |
| nwApplicationGroups | array[EntityReference] | No | Network application groups to which the rule applies |
| nwApplications | array[string] | No | Network applications to which the rule applies |
| nwServiceGroups | array[EntityReference] | No | Name-ID pairs of network service groups to which the rule applies |
| nwServices | array[EntityReference] | No | Name-ID pairs of network services to which the rule applies |
| order | integer (int32) | Yes | The rule's order of execution with respect to other Traffic Capture policy rules |
| predefined | boolean | No | A Boolean field that indicates whether this is a predefined rule by using the true value |
| rank | integer (int32) | Yes | Admin rank assigned to the rule |
| sourceCountries | array[string] | No | The countries of traffic origin that are included or excluded from the rule based on the **excludeSrcCountries** field value. If no specific value is set, this field is ignored during policy evaluation and the rule is applied to all source countries. |
| srcIpGroups | array[EntityReference] | No | Name-ID pairs of source IP groups to which the rule applies. If no specific value is set, the rule is not restricted to specific source IP groups.
**Note**: For organizations that have enabled IPv6, **srcIpv6Groups** can be used to specify the source IPv6 address groups to which the rule applies. |
| srcIps | array[string] | No | Source IP addresses (IPv4) to which the rule applies. Each entry can be an individual IP address (e.g., 192.0.2.1), a subnet or CIDR (e.g., 192.0.2.0/24), or an address range (e.g., 192.0.2.1 - 192.0.2.5). If no specific value is set, the rule is not restricted to a specific source IP address. |
| srcIpv6Groups | array[EntityReference] | No | Name-ID pairs of source IPv6 groups to which the rule applies. If no specific value is set, the rule is not restricted to specific source IPv6 groups.
**Note**: User-defined groups for IPv6 addresses are currently not supported. |
| state | string | No | Indicates the rule status as enabled or disabled |
| timeWindows | array[EntityReference] | No | Time intervals during which the rule applies. By default, this field is set to Always, making the rule applicable at all times. |
| txnSampling | string | No | The percentage of connections sampled for capturing each time the rule is triggered |
| txnSizeLimit | string | No | The maximum size of traffic to capture per connection |
| users | array[EntityReference] | No | Name-ID pairs of users to which the rule applies. If no specific value is set, the rule applies to all users. |

### TrafficCaptureRuleOrderInfo
Rule order information for the Traffic Capture policy rules
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| maxOrderConfigured | integer (int32) | No | The maximum rule order assigned to the Traffic Capture policy rules |
| ruleOrderRange | object | No | Admin rank mapping with the rule order (represented in a range) |
