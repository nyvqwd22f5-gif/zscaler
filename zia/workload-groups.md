# Workload Groups
Source: https://help.zscaler.com/zia/workload-groups

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /workloadGroups`

Retrieves the list of workload groups configured in the ZIA Admin Portal. To learn more, see [About Workload Groups](/zia/about-workload-groups).

**Tags:** Workload Groups
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer | No | Specifies the page offset |
| pageSize | query | integer | No | Specifies the page size. The default size is 250 and the maximum size is 1,000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[WorkloadGroup] |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 500 | Internal server error |  |

## `POST /workloadGroups`

Adds a workload group for an organization. To learn more, see [Configuring Workload Groups](/zia/configuring-workload-groups).

**Tags:** Workload Groups
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | WorkloadGroup | No | Workload group information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | WorkloadGroup |
| 400 | Invalid |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 500 | Internal Server Error |  |

## `DELETE /workloadGroups/{workloadGroupId}`

Updates the workload group based on the specified ID

**Tags:** Workload Groups
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| workloadGroupId | path | integer | Yes | The workload group ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | Workload Group deleted successfully |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 500 | Internal Server Error |  |

## `GET /workloadGroups/{workloadGroupId}`

Retrieves the workload group based on the specified ID

**Tags:** Workload Groups
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| workloadGroupId | path | integer | Yes | The workload group ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | WorkloadGroup |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 500 | Internal Server Error |  |

## `PUT /workloadGroups/{workloadGroupId}`

Updates the workload group for an organization based on the specified ID

**Tags:** Workload Groups
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| workloadGroupId | path | integer | Yes | The workload group ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Workload Group updated successfully! | WorkloadGroup |
| 400 | Invalid Workload Group supplied or ID incorrect |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Workload Group not found |  |
| 500 | Internal server error |  |

## Models
### EntityReference
This is an immutable reference to an entity that mainly consists of an ID and name
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

### WorkloadGroup
Workload group information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| description | string | No | Additional information of the workload group |
| expression | string | No | The workload group expression containing tag types, tags, and their relationships. |
| expressionJson | WorkloadTagExpression | No | The workload group expression containing tag types, tags, and their relationships represented in a JSON format. |
| id | integer (int32) | No | A unique identifier assigned to the workload group |
| lastModifiedBy | EntityReference | No | Information about the user that last modified the workload group |
| lastModifiedTime | integer (int32) | No | Timestamp of when the workload group was last modified |
| name | string | No | The name of the workload group |

### WorkloadTagExpression
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| expressionContainers | array[ExpressionContainer] | No | Contains one or more tag types (and associated tags) combined using logical operators within a workload group |
