# NAT Control Policy
Source: https://help.zscaler.com/zia/nat-control-policy

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /dnatRules`

Retrieves a list of all configured and predefined DNAT Control policies. To learn more, see [About NAT Control](/zia/about-nat-control).

**Tags:** NAT Control Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[DnatRule] |

## `POST /dnatRules`

Adds a new DNAT Control policy rule. To learn more, see [Configuring the NAT Control Policy](/zia/configuring-nat-control-policy).

**Tags:** NAT Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | DnatRule | No | The DNAT Control policy rule information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | DnatRule |

## `DELETE /dnatRules/{ruleId}`

Deletes the DNAT Control policy rule information based on the specified ID

**Tags:** NAT Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Unique identifier for the policy rule |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /dnatRules/{ruleId}`

Retrieves the DNAT Control policy rule information based on the specified ID

**Tags:** NAT Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Unique identifier for the policy rule |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | DnatRule |

## `PUT /dnatRules/{ruleId}`

Updates the DNAT Control policy rule information based on the specified ID

**Tags:** NAT Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Unique identifier for the policy rule |
| body | body | DnatRule | No | The DNAT Control policy rule information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | DnatRule |

## Models
### DnatRule
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| accessControl | string | No | Access privilege of this rule based on the admin's Role Based Authorization (RBA) state. Ignored if the request is POST or PUT. |
| defaultRule | boolean | No | If set to true, the default rule is applied |
| departments | array[EntityReference] | No | Name-ID pairs of departments for which the rule is applied. If not set, rule is applied for all departments. |
| description | string | No | Comments provided by administrator |
| destAddresses | array[string] | No | List of destination IP addresses or FQDNs to which this rule is applied. CIDR notations can be used for destination IP addresses. If not set, the rules are not restricted to specific destination addresses unless specified by destCountries, destIpGroups or destIpCategories. |
| destCountries | array[string] | No | Destination countries for which the rule is applicable. If not set, the rule is not restricted to specific destination countries. |
| destIpCategories | array[string] | No | IP address categories of destination for which the DNAT rule is applicable. If not set, the rule is not restricted to specific destination IP categories. |
| destIpGroups | array[EntityReference] | No | User-defined destination IP address groups on which the rule is applied. If not set, the rule is not restricted to specific destination IP address groups. |
| destIpv6Groups | array[EntityReference] | No | User-defined destination IPv6 address groups on which the rule is applied. If not set, the rule is not restricted to specific destination IPv6 address groups. |
| deviceGroups | array[EntityReference] | No | Name-ID pairs of device groups for which rule is applied |
| devices | array[EntityReference] | No | Name-ID pairs of devices for which rule is applied |
| enableFullLogging | boolean | No |  |
| groups | array[EntityReference] | No | Name-ID pairs of groups for which the policy must be applied. If not set, policy is applied for all groups. |
| id | integer (int32) | No | System-generated identifier for the DNAT control rule. Ignored if the request is POST. |
| labels | array[EntityReference] | No | Labels that are applicable to the rule |
| lastModifiedBy | EntityReference | No | User that last modified the rule. Ignored if the request is POST or PUT. For GET, ignored if the rule is current version. |
| lastModifiedTime | integer (int32) | No | Timestamp of when the rule was last modified. Ignored if the request is POST or PUT. For GET, ignored if the rule is current version. |
| locationGroups | array[EntityReference] | No | Name-ID pairs of locations groups to which the rule applies |
| locations | array[EntityReference] | No | Name-ID pairs of locations for which the policy must be applied. If not set, policy is applied for all the locations. |
| name | string | Yes | Rule name |
| nwServiceGroups | array[EntityReference] | No | User-defined network service groups on which the rule is applied. If not set, the rule is not restricted to specific network service groups created by the user. |
| nwServices | array[EntityReference] | No | Network services for which the rule is applicable. Services could be predefined or custom. |
| order | integer (int32) | No | Order of policy execution with respect to other cloud application policies of the same kind. Order N indicates N-th cloud application policy of the same kind evaluated. |
| predefined | boolean | No | If set to true, a predefined rule is applied |
| rank | integer (int32) | Yes | Admin rank that is assigned to this rule |
| redirectFqdn | string | No | FQDN to which the traffic is redirected to when the DNAT rule is triggered. This is mutually exclusive to redirect IP. |
| redirectIp | string | No | IP address to which the traffic is redirected to when the DNAT rule is triggered. If not set, no redirection is done to the specific IP address. |
| redirectPort | integer (int32) | No | Port to which the traffic is redirected to when the DNAT rule is triggered. If not set, no redirection is done to the specific port. |
| resCategories | array[string] | No | Resolved categories of destination for which the DNAT rule is applicable. If not set, the rule is not restricted to specific destination IP categories. |
| srcIpGroups | array[EntityReference] | No | User-defined source IP groups for which the rule is applicable. If not set, the rule is not restricted to any user-defined groups of source IP addresses. |
| srcIps | array[string] | No |  |
| srcIpv6Groups | array[EntityReference] | No | User-defined source IPv6 groups for which the rule is applicable. If not set, the rule is not restricted to any user-defined groups of source IPv6 addresses. |
| state | string | No | State whether it is enabled, disabled, or just set to monitoring |
| timeWindows | array[EntityReference] | No | Time interval during which policy must be enforced. If not set, policy is applied at all times. |
| trustedResolverRule | boolean | No | Set to true in the predefined rule for Zscaler Trusted DNS Resolver |
| users | array[EntityReference] | No | Name-ID pairs of users for which the policy must be applied. If not set, user criteria is not considered for policy enforcement. |

### EntityReference
This is an immutable reference to an entity that mainly consists of id and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |
