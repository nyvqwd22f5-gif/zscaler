# Policy Resources
Source: https://help.zscaler.com/cloud-branch-connector/policy-resources

## `GET /ipDestinationGroups`

Retrieves the list of destination IP groups. To learn more, see [About Destination IP Groups](/cloud-branch-connector/about-destination-ip-groups).

**Tags:** Policy Resources

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| excludeType | query | string | No | Specifies the destination IP group type that must be excluded from the list. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `POST /ipDestinationGroups`

Adds a new custom destination IP group. To learn more, see [Configuring Destination IP Groups](/cloud-branch-connector/configuring-destination-ip-groups).

**Tags:** Policy Resources
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `GET /ipDestinationGroups/lite`

Retrieves the list of destination IP groups. This request retrieves basic information about the destination IP groups, ID, name, and type. For extensive details, use the `GET /ipDestinationGroups` request.

**Tags:** Policy Resources

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| type | query | array[string] | No | List of destination IP group types that must be included in the response. |
| excludeType | query | string | No | Specifies the destination IP group type that must be excluded from the response. |
| includeURLCategory | query | boolean | No | Not applicable to Cloud & Branch Connector. |
| search | query | string | No | The search string used to match against the destination IP group name. |
| includeZscalerDomains | query | boolean | No | A Boolean field indicating whether or not to include the automatically generated **Zscaler Domains** group in the response. |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. The default size is 100. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `DELETE /ipDestinationGroups/{ipGroupId}`

Deletes the destination IP group based on the specified ID. Default destination groups that are automatically created cannot be deleted.

**Tags:** Policy Resources

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ipGroupId | path | integer (int32) | Yes | ID of the group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `GET /ipGroups`

Retrieves the list of IP pools. To learn more, see [About IP Pool](/cloud-branch-connector/about-ip-pool).

**Tags:** Policy Resources

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | The search string used to match against the IP pool parameters. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `POST /ipGroups`

Adds a new custom IP pool. To learn more, see [Configuring  IP Pool](/cloud-branch-connector/about-ip-pool).

**Tags:** Policy Resources
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `GET /ipGroups/lite`

Retrieves the list of IP pools. This request retrieves basic information about the IP pools, such as name and ID. For extensive details, use the `GET /ipGroups` request.

**Tags:** Policy Resources
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `DELETE /ipGroups/{ipGroupId}`

Deletes an IP pool based on the specified ID.

**Tags:** Policy Resources

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ipGroupId | path | integer (int32) | Yes | ID of the IP pool. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `GET /ipSourceGroups`

Retrieves the list of source IP groups. To learn more, see [About Source IP Groups](/cloud-branch-connector/about-source-ip-groups).

**Tags:** Policy Resources

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | The search string used to match against the source IP group parameters, such as name and IP addresses. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `POST /ipSourceGroups`

Adds a new custom source IP group. To learn more, see [Configuring Source IP Groups](/cloud-branch-connector/configuring-source-ip-groups).

**Tags:** Policy Resources
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `GET /ipSourceGroups/lite`

Retrieves the list of source IP groups. This request retrieves basic information about the source IP groups, such as name and ID. For extensive details, use the `GET /ipSourceGroups` request.

**Tags:** Policy Resources
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `DELETE /ipSourceGroups/{ipGroupId}`

Deletes a source IP group based on the specified ID.

**Tags:** Policy Resources

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ipGroupId | path | integer (int32) | Yes | ID of the source IP group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `GET /networkServiceGroups`

Retrieves the list of network service groups. To learn more, see [About Network Service Groups](/cloud-branch-connector/about-network-service-groups).

**Tags:** Policy Resources

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | The search string used to match against the group name and the network services included in the group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `GET /networkServices`

Retrieves the list of all network services. The search parameters find matching values within the `name` or `description` attributes.

**Tags:** Policy Resources

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| locale | query | string | No | When set to one of the supported locales (i.e., en-US, de-DE, es-ES, fr-FR, ja-JP, zh-CN), the network service's description is localized into the requested language. |
| search | query | string | No | The search string used to match against a service's name or description attributes. |
| protocol | query | string | No | Filter based on the network service protocol. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `POST /networkServices`

Creates a new network service.

**Tags:** Policy Resources
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `DELETE /networkServices/{serviceid}`

Deletes the network service for the specified ID.

**Tags:** Policy Resources

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| serviceid | path | integer (int32) | Yes | ID of the network service. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `PUT /networkServices/{serviceid}`

Updates the network service information for the specified service ID.

**Tags:** Policy Resources

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| serviceid | path | integer (int32) | Yes | ID of the network service. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `GET /zpaResources/applicationSegments`

Retrieves the list of ZPA application segments that can be configured in traffic forwarding rule criteria. To learn more, see [Configuring Traffic Forwarding Rules](/cloud-branch-connector/configuring-traffic-forwarding-rule).

**Tags:** Policy Resources

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | The search string used to match against the ZPA application segment name. |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. The default size is 50. |
| sortBy | query | string | No | Specifies the application segment parameter by which the list must be sorted. By default, it is sorted by name. |
| sortOrder | query | string | No | The order in which the list must be sorted, such as ascending or descending order of the specified parameter or rule execution order. Supported values are `asc` and `desc`. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |
