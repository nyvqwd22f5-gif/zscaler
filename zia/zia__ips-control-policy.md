# IPS Control Policy
Source: https://help.zscaler.com/zia/ips-control-policy

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /firewallIpsRules`

Retrieves the list of IPS Control policy rules configured in the ZIA Admin Portal

**Tags:** IPS Control Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[FirewallIpsRule] |

## `POST /firewallIpsRules`

Adds a new IPS Control policy rule. To learn more, see [Configuring the IPS Control Policy](/zia/configuring-ips-control-policy).

**Tags:** IPS Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | FirewallIpsRule | No | IPS Control policy rule configuration |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | FirewallIpsRule |

## `DELETE /firewallIpsRules/{ruleId}`

Deletes the IPS Control policy rule information based on the specified ID

**Tags:** IPS Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | The unique identifier for the rule |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /firewallIpsRules/{ruleId}`

Retrieves the IPS Control policy rule information based on the specified ID

**Tags:** IPS Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | The unique identifier for the rule |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | FirewallIpsRule |

## `PUT /firewallIpsRules/{ruleId}`

Updates the IPS Control policy rule information based on the specified ID

**Tags:** IPS Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | The unique identifier for the rule |
| body | body | FirewallIpsRule | No | IPS Control policy rule configuration |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | FirewallIpsRule |

## Models
### AppSegment
Application Segment information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| externalId | integer (int64) | No | Indicates the external ID. Applicable only when this reference is of an external entity. |
| id | integer (int32) | No | A unique identifier assigned to the Application Segment |
| name | string | No | The name of the Application Segment |
| zpaTenantId | integer (int64) | No | ID of the ZPA tenant where the Application Segment is configured |

### EntityReference
This is an immutable reference to an entity that mainly consists of id and name.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### FirewallIpsRule
IPS Control policy rule configuration. To learn about rule configuration details, see [Configuring the IPS Control Policy](/zia/configuring-ips-control-policy).
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| accessControl | string | No | The admin’s access privilege to this rule based on the assigned role |
| action | string | Yes | The action configured for the rule that must take place if the traffic matches the rule criteria, such as allowing or blocking the traffic or bypassing the rule. |
| capturePCAP | boolean | No | A Boolean value that indicates whether packet capture (PCAP) is enabled or not |
| defaultRule | boolean | No | A Boolean value that indicates whether the rule is the Default Cloud IPS Rule or not |
| departments | array[EntityReference] | No | The departments to which the rule applies |
| description | string | No | The description of the rule |
| destAddresses | array[string] | No | Destination IP addresses or FQDNs to which the rule applies. If not set, the rule is not restricted to a specific destination IP address. Each IP entry can be a single IP address, CIDR (e.g., 10.10.33.0/24), or an IP range (e.g., 10.10.33.1-10.10.33.10). |
| destCountries | array[string] | No | Destination countries for which the rule is applicable. If not set, the rule is not restricted to specific destination countries. |
| destIpCategories | array[FirewallUrlCategory] | No | Destination IP categories to which the rule applies. If not set, the rule is not restricted to specific categories. |
| destIpGroups | array[EntityReference] | No | Destination IP address groups for which the rule is applicable. If not set, the rule is not restricted to specific destination IPv6 address groups. |
| destIpv6Groups | array[EntityReference] | No | Destination IPv6 address groups for which the rule is applicable. If not set, the rule is not restricted to a specific source IPv6 address group.
**Note** :User-defined groups for IPv6 addresses are currently not supported. |
| deviceGroups | array[EntityReference] | No | Device groups to which the rule applies. This field is applicable for devices that are managed using Zscaler Client Connector. If no value is set, this field is ignored during the policy evaluation. |
| devices | array[EntityReference] | No | Devices to which the rule applies. This field is applicable for devices that are managed using Zscaler Client Connector. If no value is set, this field is ignored during the policy evaluation. |
| enableFullLogging | boolean | No | A Boolean value that indicates whether full logging is enabled. A true value indicates that full logging is enabled, whereas a false value indicates that aggregate logging is enabled. |
| groups | array[EntityReference] | No | The user groups to which the rule applies |
| id | integer (int32) | No | Unique identifier generated for the rule |
| labels | array[EntityReference] | No | The label associated with the rule |
| lastModifiedBy | EntityReference | No | The admin who last modified the rule |
| lastModifiedTime | integer (int32) | No | The timestamp when the rule was last modified |
| locationGroups | array[EntityReference] | No | The location groups to which the rule applies |
| locations | array[EntityReference] | No | The locations to which the rule applies |
| name | string | Yes | The name of the IPS Control rule |
| nwServiceGroups | array[EntityReference] | No | Network service groups to which the rule applies |
| nwServices | array[EntityReference] | No | Network services to which the rule applies |
| order | integer (int32) | Yes | Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and this field specifies the order of execution for the rule. |
| predefined | boolean | No | A Boolean field that indicates that the rule is predefined by using a true value |
| rank | integer (int32) | Yes | The admin rank specified for the rule based on your assigned admin rank. Admin rank determines the rule order that can be specified for the rule. Admin rank can be configured if it is enabled in the Advanced Settings. To learn more, see [About Admin Rank](/zia/about-admin-rank). |
| resCategories | array[FirewallUrlCategory] | No | URL categories associated with resolved IP addresses to which the rule applies. If not set, the rule is not restricted to a specific URL category. |
| sourceCountries | array[string] | No | The countries of origin of traffic for which the rule is applicable. If not set, the rule is not restricted to specific source countries. |
| srcIpGroups | array[EntityReference] | No | Source IP address groups for which the rule is applicable. If not set, the rule is not restricted to a specific source IP address group. |
| srcIps | array[string] | No | Source IP addresses or FQDNs to which the rule applies. If not set, the rule is not restricted to a specific source IP address. Each IP entry can be a single IP address, CIDR (e.g., 10.10.33.0/24), or an IP range (e.g., 10.10.33.1-10.10.33.10). |
| srcIpv6Groups | array[EntityReference] | No | Source IPv6 address groups for which the rule is applicable. If not set, the rule is not restricted to a specific source IPv6 address group.
**Note**: User-defined groups for IPv6 addresses are currently not supported. |
| state | string | No | The state of the rule indicating whether it is enabled or disabled |
| threatCategories | array[EntityReference] | No | Advanced threat categories to which the rule applies |
| timeWindows | array[EntityReference] | No | The time intervals during which the rule applies |
| users | array[EntityReference] | No | The users to which the rule applies |
| zpaAppSegments | array[AppSegment] | No | The [ZPA application segments](/zpa/configuring-application-segments) to which the rule applies |

### FirewallUrlCategory
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| backendName | string | No |  |
| comments | string | No |  |
| deprecated | boolean | No |  |
| mask | integer (int32) | No |  |
| name | string | No |  |
| urlSupercategory | string | No |  |
| userConfiguredName | string | No |  |
| val | integer (int32) | No |  |
