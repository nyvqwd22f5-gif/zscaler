# Rule Labels
Source: https://help.zscaler.com/zia/rule-labels

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /ruleLabels`

Gets a list of rule labels. To learn more, see [About Rule Labels](/zia/about-rule-labels).

**Tags:** Rule Labels
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer | No | Specifies the page offset. |
| pageSize | query | integer | No | Specifies the page size. The default size is 100, but the maximum size is 1000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[RuleLabel] |

## `POST /ruleLabels`

Adds a rule label.

**Tags:** Rule Labels
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | RuleLabel |

## `DELETE /ruleLabels/{ruleLabelId}`

Deletes the rule label for the specified ID.

**Tags:** Rule Labels
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleLabelId | path | integer | Yes | The unique identifier for the rule label. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /ruleLabels/{ruleLabelId}`

Gets rule label information for the specified ID.

**Tags:** Rule Labels
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleLabelId | path | integer | Yes | The unique identifier for the rule label. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | RuleLabel |

## `PUT /ruleLabels/{ruleLabelId}`

Updates rule label information for the specified ID.

**Tags:** Rule Labels
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleLabelId | path | integer | Yes | The unique identifier for the rule label. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | RuleLabel |

## Models
### EntityReference
This is an immutable reference to an entity. which mainly consists of id and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### RuleLabel
Rule label information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| createdBy | object | No | The admin that created the rule label. This is a read-only field. Ignored by PUT requests. |
| description | string | No | The rule label description. |
| id | integer (int32) | No | The unique identifier for the rule label. |
| lastModifiedBy | object | No | The admin that modified the rule label last. This is a read-only field. Ignored by PUT requests. |
| lastModifiedTime | integer (int32) | No | Timestamp when the rule lable was last modified. This is a read-only field. Ignored by PUT and DELETE requests. |
| name | string | No | The rule label name. |
| referencedRuleCount | integer (int32) | No | The number of rules that reference the label. |
