# Firewall Policies
Source: https://help.zscaler.com/zia/firewall-policies

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /dnsGateways`

Retrieves a list of DNS Gateways. To learn more, see [About DNS Gateways](/zia/about-dns-gateways).

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer | No | Set the page number of the response |
| pageSize | query | integer | No | Set the size of the response |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[RedirectDnsGateway] |

## `POST /dnsGateways`

Adds a new DNS Gateway. To learn more, see [Adding DNS Gateways](/zia/adding-dns-gateways).

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | RedirectDnsGateway | No | Information about the DNS Gateway |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | RedirectDnsGateway |
| 201 | Created |  |
| 401 | Unauthorized Access |  |
| 403 | Forbidden Access |  |

## `GET /dnsGateways/lite`

Retrieves a list of DNS Gateways

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer | No | Set the size of the response |
| pageSize | query | integer | No | Set the size of the response |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[RedirectDnsGateway] |

## `DELETE /dnsGateways/{id}`

Deletes a DNS Gateway based on the specified ID

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer | Yes |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | DNS gateway deleted successfully |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |

## `GET /dnsGateways/{id}`

Retrieves the DNS Gateway based on the specified ID

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer | Yes | Unique identifier for the DNS Gateway |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | RedirectDnsGateway |

## `PUT /dnsGateways/{id}`

Updates the DNS Gateway based on the specified ID

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer | Yes | Unique identifier for the DNS Gateway |
| body | body | RedirectDnsGateway | No | Information about the DNS Gateway |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | RedirectDnsGateway |
| 400 | Invalid Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 500 | Internal Server Error |  |

## `GET /firewallFilteringRules`

Retrieves all rules in the Firewall Filtering policy

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleName | query | string | No | Filters rules based on rule names using the specified keywords |
| ruleLabel | query | string | No | Filters rules based on rule labels using the specified keywords |
| ruleOrder | query | string | No | Filters rules based on rule order using the specified keywords |
| ruleDescription | query | string | No | Filters rules based on rule description using the specified keywords |
| ruleAction | query | string | No | Filters rules based on rule actions using the specified keywords |
| location | query | string | No | Filters rules based on locations using the specified keywords |
| department | query | string | No | Filters rules based on user departments using the specified keywords |
| group | query | string | No | Filters rules based on user groups using the specified keywords |
| user | query | string | No | Filters rules based on users using the specified keywords |
| device | query | string | No | Filters rules based on devices using the specified keywords |
| deviceGroup | query | string | No | Filters rules based on device groups using the specified keywords |
| deviceTrustLevel | query | string | No | Filters rules based on device trust levels using the specified keywords |
| srcIps | query | string | No | Filters rules based on source IP addresses using the specified keywords |
| destAddresses | query | string | No | Filters rules based on destination IP addresses using the specified keywords |
| srcIpGroups | query | string | No | Filters rules based on source IP groups using the specified keywords |
| destIpGroups | query | string | No | Filters rules based on destination IP groups using the specified keywords |
| nwApplication | query | string | No | Filters rules based on network applications using the specified keywords |
| nwServices | query | string | No | Filters rules based on network services using the specified keywords |
| destIpCategories | query | string | No | Filters rules based on destination URL categories using the specified keywords |
| page | query | integer | No | Specifies the page offset |
| pageSize | query | integer | No | Specifies the page size. The default size is set to 5,000, if not specified. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[FirewallFilteringRule] |

## `POST /firewallFilteringRules`

Adds a new Firewall Filtering policy rule

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | FirewallFilteringRule | No | The Firewall Filtering policy rule information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | FirewallFilteringRule |

## `GET /firewallFilteringRules/count`

Retrieves the rule count for Firewall Filtering policy based on search criteria. If no search criteria is specified for filtering rules, the total number of Firewall Filtering rules is retrieved by default.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleName | query | string | No | Filters rules based on rule names using the specified keywords |
| ruleLabel | query | string | No | Filters rules based on rule labels using the specified keywords |
| ruleOrder | query | string | No | Filters rules based on rule order using the specified keywords |
| ruleDescription | query | string | No | Filters rules based on rule description using the specified keywords |
| ruleAction | query | string | No | Filters rules based on rule actions using the specified keywords |
| location | query | string | No | Filters rules based on locations using the specified keywords |
| department | query | string | No | Filters rules based on user departments using the specified keywords |
| group | query | string | No | Filters rules based on user groups using the specified keywords |
| user | query | string | No | Filters rules based on users using the specified keywords |
| device | query | string | No | Filters rules based on devices using the specified keywords |
| deviceGroup | query | string | No | Filters rules based on device groups using the specified keywords |
| deviceTrustLevel | query | string | No | Filters rules based on device trust levels using the specified keywords |
| srcIps | query | string | No | Filters rules based on source IP addresses using the specified keywords |
| destAddresses | query | string | No | Filters rules based on destination IP addresses using the specified keywords |
| srcIpGroups | query | string | No | Filters rules based on source IP groups using the specified keywords |
| destIpGroups | query | string | No | Filters rules based on destination IP groups using the specified keywords |
| nwApplication | query | string | No | Filters rules based on network applications using the specified keywords |
| nwServices | query | string | No | Filters rules based on network services using the specified keywords |
| destIpCategories | query | string | No | Filters rules based on destination URL categories using the specified keywords |
| page | query | integer | No | Specifies the page offset |
| pageSize | query | integer | No | Specifies the page size. The default size is set to 5,000, if not specified. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | FirewallFilteringRule |

## `DELETE /firewallFilteringRules/{ruleId}`

Deletes a Firewall Filtering policy rule for the specified ID

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | The unique identifier for the policy rule |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /firewallFilteringRules/{ruleId}`

Gets the Firewall Filtering policy rule information for the specified ID

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | The unique identifier for the policy rule |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | FirewallFilteringRule |

## `PUT /firewallFilteringRules/{ruleId}`

Updates Firewall Filtering policy rule information for the specified ID

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | The unique identifier for the policy rule |
| body | body | FirewallFilteringRule | No | The Firewall Filtering policy rule information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | FirewallFilteringRule |

## `GET /ipDestinationGroups`

Gets a list of all IP destination groups.
**Note**: This endpoint retrieves only IPv4 destination address groups. Organizations that have enabled IPv6 can use GET `/ipSourceGroups/ipv6SourceGroups` to retrieve IPv6 destination address groups.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| excludeType | query | string | No | Filter based on the IP destination group's type. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[DestinationIpGroup] |

## `POST /ipDestinationGroups`

Adds a new IP Destination group.
**Note**: This endpoint can only add an IPv4 destination address group. User-defined groups for IPv6 addresses are currently not supported.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | DestinationIpGroup |

## `GET /ipDestinationGroups/ipv6DestinationGroups`

Gets the list of destination IPv6 address groups.
**Note**: User-defined groups for IPv6 addresses are currently not supported, so this endpoint retrieves only the predefined group that includes all IPv6 addresses.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| excludeType | query | string | No | Specifies a destination group type to exclude the corresponding  groups from the list. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[DestinationIpGroup] |

## `GET /ipDestinationGroups/ipv6DestinationGroups/lite`

Gets a name and ID dictionary for destination IPv6 address groups.
**Note**: User-defined groups for IPv6 addresses are currently not supported, so this endpoint retrieves only the predefined group that includes all IPv6 addresses.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| type | query | array | No | Filters the list based on the destination group type. |
| excludeType | query | string | No | Specifies a destination group type to exclude the corresponding  groups from the list type. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[EntityReference] |

## `GET /ipDestinationGroups/lite`

Gets a name and ID dictionary of all IP destination groups.
**Note**: This endpoint retrieves only IPv4 destination address groups. Organizations that have enabled IPv6 can use GET `/ipDestinationGroups/ipv6DestinationGroups/lite` to retrieve IPv6 destination address groups.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| type | query | array | No | Filter based on the IP destination group's type. |
| excludeType | query | string | No | Exclude from list based on the IP destination group's type. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[DestinationIpGroup] |

## `DELETE /ipDestinationGroups/{ipGroupId}`

Deletes the IP destination group for the specified ID.
**Note**: Only user-defined IP groups can be deleted.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ipGroupId | path | integer | Yes |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /ipDestinationGroups/{ipGroupId}`

Gets the IP destination group information for the specified ID.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ipGroupId | path | integer | Yes | The unique identifier for the IP destination group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | DestinationIpGroup2 |

## `PUT /ipDestinationGroups/{ipGroupId}`

Updates the IP destination group information for the specified ID.
**Note**: Only user-defined IP groups can be updated.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ipGroupId | path | integer | Yes | Unique identifier for the IP destination group |
| override | query | boolean | No | Indicates whether the IPs must be overridden. When set to false, the IPs are appended; else the existing IPs are overridden. The default value is true. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | DestinationIpGroup |

## `GET /ipSourceGroups`

Gets a list of all IP source groups. The search parameters find matching values within the `name` or `description` attributes.
**Note**: This endpoint retrieves only IPv4 source address groups. Organizations that have enabled IPv6 can use GET `/ipSourceGroups/ipv6SourceGroups` to retrieve IPv6 source address groups.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | The search string used to match against a group's name or description attributes. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[IpGroup] |

## `POST /ipSourceGroups`

Adds a new IP source group.
**Note**: This endpoint can only add an IPv4 source address group. User-defined groups for IPv6 addresses are currently not supported.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | IpGroup |

## `GET /ipSourceGroups/ipv6SourceGroups`

Gets the list of source IPv6 address groups.
**Note**: User-defined groups for IPv6 addresses are currently not supported, so this endpoint retrieves only the predefined group that includes all IPv6 addresses.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[IpGroup] |

## `GET /ipSourceGroups/ipv6SourceGroups/lite`

Gets a name and ID dictionary for source IPv6 address groups.
**Note**: User-defined  groups for IPv6 addresses are currently not  supported, so this endpoint retrieves only the predefined  group that includes all IPv6 addresses.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[IpGroup] |

## `GET /ipSourceGroups/lite`

Gets a name and ID dictionary of all IP source groups.
**Note**: This endpoint retrieves only IPv4 source address groups. Organizations that have enabled IPv6 can use GET `/ipSourceGroups/ipv6SourceGroups/lite` to retrieve IPv6 source address groups.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[IpGroup] |

## `DELETE /ipSourceGroups/{ipGroupId}`

Deletes the IP source group for the specified ID.
**Note**: Only user-defined IP groups can be deleted.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ipGroupId | path | integer | Yes | The unique identifier for the IP source group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /ipSourceGroups/{ipGroupId}`

Gets the IP source group information for the specified ID.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ipGroupId | path | integer | Yes | The unique identifier for the IP source group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | IpGroup |

## `PUT /ipSourceGroups/{ipGroupId}`

Updates the IP source group information for the specified ID.
**Note**: Only user-defined IP groups can be updated.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ipGroupId | path | integer | Yes | The unique identifier for the IP source group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | IpGroup |

## `GET /networkApplicationGroups`

Gets a list of all network application groups. The search parameters find matching values within the `name` or `description` attributes.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | The search string used to match against a group's name or description attributes. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[NetworkApplicationGroup] |

## `POST /networkApplicationGroups`

Creates a new custom network application group.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | NetworkApplicationGroup |

## `GET /networkApplicationGroups/lite`

Gets a name and ID dictionary of all network application groups.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[NetworkApplicationGroup] |

## `DELETE /networkApplicationGroups/{groupId}`

Deletes the custom network application group for the specified ID.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| groupId | path | integer | Yes | The unique identifier for the network application group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /networkApplicationGroups/{groupId}`

Gets the network application group information for the specified ID.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| groupId | path | integer | Yes | The unique identifier for the network application group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | NetworkApplicationGroup |

## `PUT /networkApplicationGroups/{groupId}`

Updates the customer network application group for the specified ID.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| groupId | path | integer | Yes | The unique identifier for the network application group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | NetworkApplicationGroup |

## `GET /networkApplications`

Gets a list of all predefined network applications. The search parameters find matching values within the `description` attribute.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | The search string used to match against a network application's description attribute. |
| locale | query | string | No | When set to one of the supported locales (i.e., en-US, de-DE, es-ES, fr-FR, ja-JP, zh-CN), the network application's description is localized into the requested language. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[NetworkApplicationDom] |

## `GET /networkApplications/{appId}`

Gets the network application information for the specified ID.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| appId | path | string | Yes | The unique identifier for the network application. |
| locale | query | string | No | When set to one of the supported locales (i.e., en-US, de-DE, es-ES, fr-FR, ja-JP, zh-CN), the network application's description is localized into the requested language. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | NetworkApplicationDom |

## `GET /networkServiceGroups`

Gets a list of all network service groups. The search parameters find matching values within the `name` or `description` attributes.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | The search string used to match against a group's name or description attributes. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[NetworkServiceGroup] |

## `POST /networkServiceGroups`

Adds a new network service group.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | NetworkServiceGroup |

## `GET /networkServiceGroups/lite`

Gets a name and ID dictionary of all network service groups.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[NetworkServiceGroup] |

## `DELETE /networkServiceGroups/{serviceGroupId}`

Deletes the network service group for the specified ID.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| serviceGroupId | path | integer | Yes | The unique identifier for the network service group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /networkServiceGroups/{serviceGroupId}`

Gets the network service group information for the specified ID.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| serviceGroupId | path | integer | Yes | The unique identifier for the network service group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | NetworkServiceGroup |

## `PUT /networkServiceGroups/{serviceGroupId}`

Updates the network service group information for the specified ID.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| serviceGroupId | path | integer | Yes | The unique identifier for the network service group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | NetworkServiceGroup |

## `GET /networkServices`

Gets a list of all network services. The search parameters find matching values within the `name` or `description` attributes.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | The search string used to match against a service's name or description attributes. |
| protocol | query | string | No | Filter based on the network service protocol. |
| locale | query | string | No | When set to one of the supported locales (i.e., en-US, de-DE, es-ES, fr-FR, ja-JP, zh-CN), the network service's description is localized into the requested language. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[NetworkService] |

## `POST /networkServices`

Adds a new network service.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | NetworkService | No | The network service information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | NetworkService |

## `GET /networkServices/lite`

Gets a name and ID dictionary of all network services.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| locale | query | string | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[NetworkService] |

## `DELETE /networkServices/{serviceId}`

Deletes the network service for the specified ID.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| serviceId | path | integer | Yes | The unique identifier for the network service. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /networkServices/{serviceId}`

Gets the network service for the specified ID.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| serviceId | path | integer | Yes | The unique identifier for the network service. |
| locale | query | string | No | When set to one of the supported locales (i.e., en-US, de-DE, es-ES, fr-FR, ja-JP, zh-CN), the network service's description is localized into the requested language. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | NetworkService |

## `PUT /networkServices/{serviceId}`

Updates the network service information for the specified ID.

**Tags:** Firewall Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| serviceId | path | integer | Yes | The unique identifier for the network service. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | NetworkService |

## `GET /timeWindows`

Gets a list of [time intervals](/zia/defining-time-intervals) used for by the Firewall policy or the URL Filtering policy.

**Tags:** Firewall Policies, URL Filtering Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[TimeWindow] |

## `GET /timeWindows/lite`

Gets a name and ID dictionary of [time intervals](/zia/defining-time-intervals) used by the Firewall policy or the URL Filtering policy.

**Tags:** Firewall Policies, URL Filtering Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[TimeWindow] |

## Models
### DestinationIpGroup
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| addresses | array[string] | No | Destination IP addresses, FQDNs, or wildcard FQDNs added to the group. |
| countries | array[string] | No | Destination IP address counties. You can identify destinations based on the location of a server. |
| description | string | No | Additional information about the destination IP group |
| id | integer (int32) | No | Unique identifier for the destination IP group |
| ipCategories | array[string] | No | Destination IP address URL categories. You can identify destinations based on the URL category of the domain. |
| isNonEditable | boolean | No | If set to true, the destination IP address group is non-editable. This field is applicable only to predefined IP address groups, which cannot  be modified. |
| name | string | No | Destination IP group name |
| type | string | No | Destination IP group type (i.e., the group can contain destination IP addresses or FQDNs) |

### DestinationIpGroup2
TBD
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| addresses | array[string] | No | Destination FQDNs, domains, or IP addresses within the group. This list must reflect the type of addresses that are specified in the `type` attribute. DSTN_FQDN type must contain only FQDNs. DSTN_DOMAIN type can be a mix of FQDNs, domains, or wildcard domains. DSTN_IP type can have any of the following:
Single IP address
- Range of IP Addresses (e.g., 1.1.1.1 - 1.1.1.255)
- IP addresses specified by subnet mask. (e.g., 1.1.1.0/24) |
| countries | array[string] | No | Destination IP address counties. You can identify destinations based on the location of a server. |
| description | string | No | Additional information about the destination IP group |
| id | integer (int32) | No | Unique identifer for the destination IP group |
| ipAddresses | array[string] | No | Destination FQDNs or IP addresses within the group. This list cannot contain both. The IP address can be any of the following:
- Single IP address
- Range of IP Addresses (e.g., 1.1.1.1 - 1.1.1.255)
- IP addresses specified by subnet mask. (e.g., 1.1.1.0/24) |
| ipCategories | array[string] | No | Destination IP address URL categories. You can identify destinations based on the URL category of the domain. |
| name | string | No | Destination IP group name |
| type | string | No | Destination IP group type (i.e., the group can contain destination IP addresses or FQDNs) |
| urlCategories | array[string] | No | This attribute is present for backward compatibility only. Zscaler recommends using the `ipCategories` attribute. Destination IP address URL categories. You can identify destinations based on the URL category of the domain. |

### EntityReference
This is an immutable reference to an entity that mainly consists of id and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### ExpressionContainer
One or more tag types (and associated tags) combined using logical operators within a workload group
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| operator | string | No | The operator (either AND or OR) used to create logical relationships among tag types |
| tagContainer | TagContainer | No | Contains one or more tags and the logical operator used to combine the tags within a tag type |
| tagType | string | No | The tag type selected from a predefined list |

### FirewallFilteringRule
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| action | string | No | The action the Firewall Filtering policy rule takes when packets match the rule |
| appServiceGroups | array[EntityReference] | No | Application service groups on which this rule is applied |
| appServices | array[EntityReference] | No | Application services on which this rule is applied |
| defaultRule | boolean | No | If set to true, the default rule is applied |
| departments | array[EntityReference] | No | The departments to which the Firewall Filtering policy rule applies |
| description | string | No | Additional information about the rule |
| destAddresses | array[string] | No | List of destination IP addresses for which the rule is applicable. CIDR notation can be used for destination IP addresses. If not set, the rule is not restricted to a specific destination addresses unless specified by destCountries, destIpGroups or destIpCategories. |
| destCountries | array[string] | No | Destination countries for which the rule is applicable. If not set, the rule is not restricted to specific destination countries. |
| destIpCategories | array[string] | No | IP address categories of destination for which the DNAT rule is applicable. If not set, the rule is not restricted to specific destination IP categories. |
| destIpGroups | array[EntityReference] | No | User-defined destination IP address groups to which the rule is applied. If not set, the rule is not restricted to a specific destination IP address group.
**Note**: For organizations that have enabled  IPv6, the `destIpv6Groups` field lists the IPv6 source address groups for which the rule is applicable. |
| destIpv6Groups | array[EntityReference] | No | Destination IPv6 address groups for which the rule is applicable.  If not set, the rule is not restricted to a specific source IPv6 address group.
**Note**: User-defined groups for IPv6 addresses are currently not supported. |
| deviceGroups | array[EntityReference] | No | Name-ID pairs of device groups for which the rule must be applied. This field is applicable for devices that are managed using Zscaler Client Connector. If no value is set, this field is ignored during the policy evaluation. |
| deviceTrustLevels | array[string] | No | List of device trust levels for which the rule must be applied. While the High Trust, Medium Trust, or Low Trust evaluation is applicable only to Zscaler Client Connector traffic, Unknown evaluation applies to all traffic. The trust levels are assigned to the devices based on your [posture configurations](/client-connector/adding-zia-posture-profiles) in the Zscaler Client Connector Portal. If no value is set, this field  is ignored during the policy evaluation. |
| devices | array[EntityReference] | No | Name-ID pairs of devices for which rule must be applied. Specifies  devices that are managed using Zscaler Client Connector. If no value is set, this field is ignored during the policy evaluation. |
| excludeSrcCountries | boolean | No | Indicates whether the countries specified in the sourceCountries field are included or excluded from the rule. A true value denotes that the specified source countries are excluded from the rule. A false value denotes that the rule is applied to the source countries if there is a match. |
| groups | array[EntityReference] | No | The groups to which the Firewall Filtering policy rule applies |
| id | integer (int32) | No | Unique identifier for the Firewall Filtering policy rule |
| labels | array[EntityReference] | No | Labels that are applicable to the rule. |
| lastModifiedBy | EntityReference | No |  |
| lastModifiedTime | integer (int32) | No | Timestamp when the rule was last modified. Ignored if the request is POST or PUT. For GET, ignored if or the rule is current version. |
| locationGroups | array[EntityReference] | No | The location groups to which the Firewall Filtering policy rule applies |
| locations | array[EntityReference] | No | The locations to which the Firewall Filtering policy rule applies |
| name | string | Yes | Name of the Firewall Filtering policy rule |
| nwApplicationGroups | array[EntityReference] | No | User-defined network service application group to which the rule is applied. If not set, the rule is not restricted to a specific network service application group. |
| nwApplications | array[string] | No | User-defined network service applications to which the rule is applied. If not set, the rule is not restricted to a specific network service application. |
| nwServiceGroups | array[EntityReference] | No | User-defined network service group to which the rule is applied. If not set, the rule is not restricted to a specific network service group. |
| nwServices | array[EntityReference] | No | User-defined network services to which the rule is applied. If not set, the rule is not restricted to a specific network service. |
| order | integer (int32) | No | Rule order number of the Firewall Filtering policy rule |
| predefined | boolean | No | If set to true, a predefined rule is applied |
| rank | integer (int32) | No | Admin rank of the Firewall Filtering policy rule |
| sourceCountries | array[string] | No | The list of source countries that must be included or excluded from the rule based on the excludeSrcCountries field value. If no value is set, this field is ignored during policy evaluation and the rule is applied to all source countries. |
| srcIpGroups | array[EntityReference] | No | Source IP address groups for which the rule is applicable. If not set, the rule is not restricted to a specific source IP address group.
**Note**: For organizations that have enabled IPv6, the `srcIpv6Groups` field lists the IPv6 source address groups for which the rule is applicable. |
| srcIps | array[string] | No | User-defined source IP addresses for which the rule is applicable. If not set, the rule is not restricted to a specific source IP address. |
| srcIpv6Groups | array[EntityReference] | No | Source IPv6 address groups for which the rule is applicable. If not set, the rule is not restricted to a specific source IPv6 address group.
**Note**: User-defined groups for IPv6 addresses are currently not supported. |
| state | string | No | Determines whether the Firewall Filtering policy rule is enabled or disabled |
| timeWindows | array[EntityReference] | No | The time interval in which the Firewall Filtering policy rule applies |
| users | array[EntityReference] | No | The users to which the Firewall Filtering policy rule applies |
| workloadGroups | array[WorkloadGroup] | No | The list of preconfigured workload groups to which the policy must be applied. To learn more, see [About Workload Groups](/zia/about-workload-groups) and [Configuring Workload Groups]( /zia/configuring-workload-groups). |

### IpGroup
IP group information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| description | string | No | The description of the source IP address group. |
| id | integer (int32) | No | A unique identifier of the source IP address group. |
| ipAddresses | array[string] | No | Source IP addresses added to the group. |
| isNonEditable | boolean | No | If set to true, the source IP address group is non-editable. This field is applicable only to predefined IP address groups, which cannot  be modified. |
| name | string | No | The name of the source IP address group. |

### NetworkApplicationDom
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| deprecated | boolean | No |  |
| description | string | No |  |
| id | string | No |  |
| parentCategory | string | No |  |

### NetworkApplicationGroup
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| description | string | No |  |
| id | integer (int32) | No |  |
| name | string | No |  |
| networkApplications | array[string] | No |  |

### NetworkService
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| description | string | No |  |
| destTcpPorts | array[PortRange] | No |  |
| destUdpPorts | array[PortRange] | No |  |
| id | integer (int32) | No |  |
| isNameL10nTag | boolean | No |  |
| name | string | No |  |
| srcTcpPorts | array[PortRange] | No |  |
| srcUdpPorts | array[PortRange] | No |  |
| tag | string | No |  |
| type | string | No |  |

### NetworkServiceGroup
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| description | string | No |  |
| id | integer (int32) | No |  |
| name | string | No |  |
| services | array[NetworkService] | No |  |

### PortRange
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| end | integer (int32) | No |  |
| start | integer (int32) | No |  |

### RedirectDnsGateway
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| autoCreated | boolean | No | Indicates that the gateway is system-generated |
| dnsGatewayProtocols | array[string] | No | Protocols that must be used to connect to the DNS service. This field is a duplicate of the protocols field. |
| dnsGatewayType | string | No | Specifies the DNS Gateway type |
| failureBehavior | string | No | Selects an action that must be performed if the configured DNS service is unavailable or unhealthy. This field is not applicable to the Lite API. |
| id | integer (int32) | No | System-generated identifier for the DNS Gateway |
| lastModifiedBy | EntityReference | No | Last user that modified the rule. This field is not applicable to the Lite API. |
| lastModifiedTime | integer (int32) | No | Timestamp of when the rule was last modified. This field is not applicable to the Lite API. |
| name | string | No | Name of the DNS Gateway |
| natZtrGateway | boolean | No | Indicates the association of the gateway to a specific DNS Control policy |
| primaryIpOrFqdn | string | No | The IP address or the FQDN of the primary DNS service provided by the third-party DNS service provider. This field is not applicable to the Lite API. |
| primaryPorts | array[integer (int32)] | No | Lists the ports for the primary DNS server depending on the protocols selected for the gateway. This field is not applicable to the Lite API. |
| protocols | array[string] | No | Protocols that must be used to connect to the DNS service |
| secondaryIpOrFqdn | string | No | The IP address or the FQDN of the secondary DNS service provided by your third-party DNS service provider. This field is not applicable to the Lite API. |
| secondaryPorts | array[integer (int32)] | No |  |

### Tag
The list of tags (key-value pairs) selected within a tag type
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| key | string | No | The *key* component present in the key-value pair contained in a tag |
| value | string | No | The *value* component present in the key-value pair contained in a tag |

### TagContainer
One or more tags combined using logical operators within a tag type
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| operator | string | No | The logical operator (either AND or OR) used to combine the tags within a tag type |
| tags | array[Tag] | No | One or more tags, each consisting of a key-value pair, selected within a tag type. If multiple tags are present within a tag type, they are combined using a logical operator.
**Note**: A maximum of 8 tags can be added to a workload group, irrespective of the number of tag types present. |

### TimeWindow
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| dayOfWeek | array[string] | No |  |
| endTime | integer (int32) | No |  |
| id | integer (int32) | No |  |
| name | string | No |  |
| startTime | integer (int32) | No |  |

### WorkloadGroup
Workload group information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| description | string | No | The description of the workload group |
| expression | string | No | The workload group expression containing tag types, tags, and their relationships. |
| expressionJson | WorkloadTagExpression | No | The workload group expression containing tag types, tags, and their relationships represented in a JSON format. |
| id | integer (int32) | No | A unique identifier assigned to the workload group |
| lastModifiedBy | EntityReference | No | Information about the admin that last modified the workload group |
| lastModifiedTime | integer (int32) | No | Timestamp when the workload group was last modified |
| name | string | No | The name of the workload group |

### WorkloadTagExpression
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| expressionContainers | array[ExpressionContainer] | No | Contains one or more tag types (and associated tags) combined using logical operators within a workload group |
