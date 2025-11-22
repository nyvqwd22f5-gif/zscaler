# URL Filtering Policy
Source: https://help.zscaler.com/zia/url-filtering-policy

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /timeWindows`

Gets a list of [time intervals](/zia/defining-time-intervals) used for by the Firewall policy or the URL Filtering policy.

**Tags:** Firewall Policies, URL Filtering Policies
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[TimeWindow] |

## `GET /timeWindows/lite`

Gets a name and ID dictionary of [time intervals](/zia/defining-time-intervals) used by the Firewall policy or the URL Filtering policy.

**Tags:** Firewall Policies, URL Filtering Policies
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[TimeWindow] |

## `GET /urlFilteringRules`

Gets a list of all of URL Filtering Policy rules.

**Tags:** URL Filtering Policies
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[UrlFilteringRule] |

## `POST /urlFilteringRules`

Adds a URL Filtering Policy rule.
If you are using the Admin Rank feature, refer to [About Admin Rank](/zia/about-admin-rank) to determine which value to provide for `rank` when adding a policy rule. If you are not using Admin Rank, the `rank` value must be 7.

**Tags:** URL Filtering Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | UrlFilteringRule | No | The URL filtering rule information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | UrlFilteringRule |

## `DELETE /urlFilteringRules/{ruleId}`

Deletes the URL Filtering Policy rule for the specified ID.

**Tags:** URL Filtering Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | The unique identifier for the URL Filtering Policy rule. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /urlFilteringRules/{ruleId}`

Gets the URL Filtering Policy rule for the specified ID.

**Tags:** URL Filtering Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | The unique identifier for the URL Filtering Policy rule. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | UrlFilteringRule |

## `PUT /urlFilteringRules/{ruleId}`

Updates the URL Filtering Policy rule for the specified ID.
If you are using the Admin Rank feature, refer to [About Admin Rank](/zia/about-admin-rank) to determine which value to provide for `rank` when adding a policy rule. If you are not using Admin Rank, the `rank` value must be 7.

**Tags:** URL Filtering Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | The unique identifier for the URL Filtering Policy rule. |
| body | body | UrlFilteringRule | No | The URL filering rule information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | UrlFilteringRule |

## Models
### BrowserIsolationProfile
Information about browser isolation profile. To learn more, see [What Is Isolation?](/isolation/what-isolation) and [Creating Isolation Profiles for ZIA](/isolation/creating-zia-isolation-profile-isolation).
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| defaultProfile | boolean | No | (Optional) Indicates whether this is a default browser isolation profile. Zscaler sets this field. |
| id | string | No | The universally unique identifier (UUID) for the browser isolation profile |
| name | string | No | Name of the browser isolation profile |
| url | string | No | The browser isolation profile URL |

### EntityReference
This is an immutable reference to an entity. which mainly consists of id and name
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

### TimeWindow
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| dayOfWeek | array[string] | No |  |
| endTime | integer (int32) | No |  |
| id | integer (int32) | No |  |
| name | string | No |  |
| startTime | integer (int32) | No |  |

### UrlFilteringRule
URL Filtering Rule
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| action | string | No | Action taken when traffic matches rule criteria.
**Note**: The ISOLATE action is available only if Cloud Browser Isolation is enabled for your organization. To learn more, see [Configuring the URL Filtering Policy](/zia/configuring-url-filtering-policy#Action). |
| blockOverride | boolean | No | When set to true, a 'BLOCK' action triggered by the rule could be overridden. If true and both overrideGroup and overrideUsers are not set, the BLOCK triggered by this rule could be overridden for any users. If blockOverride is not set, 'BLOCK' action cannot be overridden. |
| cbiProfile | object | No | The cloud browser isolation profile to which the ISOLATE action is applied in the [URL Filtering Policy](/zia/configuring-url-filtering-policy#Action) rules.
**Note**: This parameter is required for the ISOLATE action and is not applicable to other actions. |
| ciparule | boolean | No | If set to true, the CIPA Compliance rule is enabled |
| departments | array[EntityReference] | No | Name-ID pairs of departments for which rule must be applied |
| description | string | No | Additional information about the URL Filtering rule |
| deviceGroups | array[EntityReference] | No | This field is applicable for devices that are managed using Zscaler Client Connector. If no value is set, this field is ignored during the policy evaluation. |
| deviceTrustLevels | array[string] | No | List of device trust levels for which the rule must be applied. While the High Trust, Medium Trust, or Low Trust evaluation is applicable only to Zscaler Client Connector traffic, Unknown evaluation applies to all traffic.
The trust levels are assigned to the devices based
on your [posture configurations](/client-connector/adding-zia-posture-profiles) in the Zscaler Client Connector Portal. If no value is set, this field is ignored during the policy evaluation. |
| devices | array[EntityReference] | No | Name-ID pairs of devices for which rule must be applied. Specifies devices that are managed using Zscaler Client Connector. If no value is set, this field is ignored during the policy evaluation. |
| endUserNotificationUrl | string | No | URL of end user notification page to be displayed when the rule is matched. Not applicable if either 'overrideUsers' or 'overrideGroups' is specified. |
| enforceTimeValidity | boolean | No | Enforce a set a validity time period for the URL Filtering rule. To learn more, see [Configuring the URL Filtering Policy](/zia/configuring-url-filtering-policy). |
| groups | array[EntityReference] | No | Name-ID pairs of groups for which rule must be applied |
| id | integer (int32) | No | URL Filtering Rule ID |
| labels | array[EntityReference] | No | The URL Filtering rule's label. Rule labels allow you to logically group your organization's policy rules. Policy rules that are not associated with a rule label are grouped under the Untagged label. |
| lastModifiedBy | object | No | Who modified the rule last |
| lastModifiedTime | integer (int32) | No | When the rule was last modified |
| locationGroups | array[EntityReference] | No | Name-ID pairs of the location groups to which the rule must be applied. |
| locations | array[EntityReference] | No | Name-ID pairs of locations for which rule must be applied |
| name | string | Yes | Rule Name |
| order | integer (int32) | No | Order of execution of rule with respect to other URL Filtering rules |
| overrideGroups | array[EntityReference] | No | Name-ID pairs of groups for which this rule can be overridden. Applicable only if blockOverride is set to 'true' and action is 'BLOCK'. If this overrideGroups is not set, 'BLOCK' action can be overridden for any group. |
| overrideUsers | array[EntityReference] | No | Name-ID pairs of users for which this rule can be overridden. Applicable only if blockOverride is set to 'true', action is 'BLOCK' and overrideGroups is not set.If this overrideUsers is not set, 'BLOCK' action can be overridden for any user. |
| protocols | array[string] | No | Protocol criteria |
| rank | integer (int32) | No | Admin rank of the admin who creates this rule |
| requestMethods | array[string] | No | Request method for which the rule must be applied. If not set, rule is applied to all methods |
| sizeQuota | integer (int32) | No | Size quota in KB beyond which the URL Filtering rule is applied. If not set, no quota is enforced. If a policy rule action is set to 'BLOCK', this field is not applicable. |
| state | string | No | Rule State |
| timeQuota | integer (int32) | No | Time quota in minutes, after which the URL Filtering rule is applied. If not set, no quota is enforced. If a policy rule action is set to 'BLOCK', this field is not applicable. |
| timeWindows | array[EntityReference] | No | Name-ID pairs of time interval during which rule must be enforced. |
| urlCategories | array[string] | No | List of URL categories for which rule is be applied. |
| urlCategories2 | array[string] | No | List of URL categories for which rule is applied.
**Note**: The urlCategories and urlCategories2 parameters are connected with a logical `AND` operator so that the URL Filtering policy rules are triggered when it matches the selected categories in both the URL Categories fields. To learn more, see [Configuring the URL Filtering Policy](/zia/configuring-url-filtering-policy). |
| users | array[EntityReference] | No | Name-ID pairs of users for which rule must be applied |
| validityEndTime | integer (int32) | No | If enforceTimeValidity is set to true, the URL Filtering rule ceases to be valid on this end date and time. |
| validityStartTime | integer (int32) | No | If enforceTimeValidity is set to true, the URL Filtering rule is valid starting on this date and time. |
| validityTimeZoneId | string | No | If enforceTimeValidity is set to true, the URL Filtering rule date and time is valid based on this time zone ID. |
| workloadGroups | array[WorkloadGroup] | No | The list of preconfigured workload groups to which the policy must be applied. To learn more, see [About Workload Groups](/zia/about-workload-groups) and [Configuring Workload Groups]( /zia/configuring-workload-groups). |

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
