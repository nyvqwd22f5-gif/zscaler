# Bandwidth Control & Classes
Source: https://help.zscaler.com/zia/bandwidth-control-classes

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /bandwidthClasses`

Retrieves a list of bandwidth classes for an organization. To learn more, see [About Bandwidth Classes](/zia/about-bandwidth-classes).

**Tags:** Bandwidth Control & Classes
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[BandwidthClass] |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |

## `POST /bandwidthClasses`

Adds a new bandwidth class. To learn more, see [Adding Bandwidth Classes](/zia/adding-bandwidth-classes).

**Tags:** Bandwidth Control & Classes
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | BandwidthClass | No | Information about the bandwidth class |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | BandwidthClass |
| 201 | Created |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |

## `GET /bandwidthClasses/lite`

Retrieves a list of bandwidth classes for an organization

**Tags:** Bandwidth Control & Classes
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[BandwidthClass] |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |

## `DELETE /bandwidthClasses/{bandwidthClassId}`

Deletes a bandwidth class based on the specified ID

**Tags:** Bandwidth Control & Classes
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| bandwidthClassId | path | integer | Yes | Bandwidth class ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | Bandwidth class deleted successfully |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |

## `GET /bandwidthClasses/{bandwidthClassId}`

Retrieves the bandwidth class based on the specified ID

**Tags:** Bandwidth Control & Classes
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| bandwidthClassId | path | integer | Yes | Bandwidth class ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | BandwidthClass |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |

## `PUT /bandwidthClasses/{bandwidthClassId}`

Updates a bandwidth class based on the specified ID

**Tags:** Bandwidth Control & Classes
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| bandwidthClassId | path | integer | Yes | Bandwidth class ID |
| body | body | BandwidthClass | No | Information about the bandwidth class |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | BandwidthClass |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |

## `GET /bandwidthControlRules`

Retrieves all the rules in the Bandwidth Control policy. To learn more, see [About Bandwidth Control](/zia/about-bandwidth-control).

**Tags:** Bandwidth Control & Classes
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[BandwidthControlRule] |

## `POST /bandwidthControlRules`

Adds a new Bandwidth Control policy rule. To learn more, see [Adding Rules to the Bandwidth Control Policy](/zia/adding-rules-bandwidth-control-policy).

**Tags:** Bandwidth Control & Classes
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | BandwidthControlRule | No | The Bandwidth Control policy rule information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | successful operation | BandwidthControlRule |

## `GET /bandwidthControlRules/lite`

Retrieves all the rules in the Bandwidth Control policy

**Tags:** Bandwidth Control & Classes
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[BandwidthControlRule] |

## `DELETE /bandwidthControlRules/{ruleId}`

Deletes a Bandwidth Control policy rule based on the specified ID

**Tags:** Bandwidth Control & Classes
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Bandwidth Control rule ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /bandwidthControlRules/{ruleId}`

Retrieves the Bandwidth Control policy rule based on the specified ID

**Tags:** Bandwidth Control & Classes
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Bandwidth Control rule ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | BandwidthControlRule |

## `PUT /bandwidthControlRules/{ruleId}`

Updates the Bandwidth Control policy rule based on the specified ID

**Tags:** Bandwidth Control & Classes
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Bandwidth Control rule ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | BandwidthControlRule |

## Models
### BandwidthClass
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| applicationServiceGroups | array[string] | No | The application service groups included in the bandwidth class |
| applications | array[string] | No | The applications included in the bandwidth class |
| getfileSize | string | No | The file size for a bandwidth class |
| id | integer (int32) | No | System-generated identifier for the bandwidth class |
| isNameL10nTag | boolean | No | Indicates whether the bandwidth class name is localized |
| name | string | No | Name of the bandwidth class |
| networkApplications | array[string] | No | The network applications included in the bandwidth class |
| networkServices | array[string] | No | The network services included in the bandwidth class |
| type | string | No | The application type for which the bandwidth class is configured |
| urlCategories | array[UrlCategoryForPolicy] | No | The URL categories to add to the bandwidth class |
| urls | array[string] | No | The URLs included in the bandwidth class. You can include multiple entries. |
| webApplications | array[PolicyWebApplication] | No | The web conferencing applications included in the bandwidth class. To learn more, see [Configuring the Web Conferencing Applications Bandwidth Class](/zia/configuring-web-conferencing-applications-bandwidth-class). |

### BandwidthControlRule
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| accessControl | string | No | Access privilege of this rule based on the admin's Role Based Authorization (RBA) state |
| bandwidthClasses | array[EntityReference] | No | The bandwidth classes to which you want to apply this rule. You first must add URLs or cloud applications to predefined or custom bandwidth classes. |
| defaultRule | boolean | No | Indicates whether the default rule is enabled. If set to true, the default rule is applied. |
| description | string | No | Additional information about the rule |
| deviceGroups | array[EntityReference] | No | Name-ID pairs of device groups for which the rule must be applied. This field is applicable for devices that are managed using Zscaler Client Connector. If no value is set, this field is ignored during the policy evaluation. |
| deviceTrustLevels | array[string] | No | List of device trust levels for which the rule must be applied. While the High Trust, Medium Trust, or Low Trust evaluation is applicable only to Zscaler Client Connector traffic, Unknown evaluation applies to all traffic. The trust levels are assigned to the devices based on your posture configurations in the Zscaler Client Connector Portal. If no value is set, this field is ignored during the policy evaluation. |
| devices | array[EntityReference] | No | Name-ID pairs of devices for which rule must be applied. Specifies devices that are managed using Zscaler Client Connector. If no value is set, this field is ignored during the policy evaluation. |
| id | integer (int32) | No | System-generated identifier for bandwidth control rule |
| labels | array[EntityReference] | No | Labels that are applicable to the rule. This field is not applicable to the Lite API. |
| lastModifiedBy | EntityReference | No | Last user that modified the rule. This field is not applicable to the Lite API. |
| lastModifiedTime | integer (int32) | No | Timestamp of when the rule was last modified. This field is not applicable to the Lite API. |
| locationGroups | array[EntityReference] | No | The location groups to which the rule applies |
| locations | array[EntityReference] | No | The locations to which the Bandwidth Control policy rule applies |
| maxBandwidth | integer (int32) | No | The maximum percentage of a location's bandwidth to be guaranteed for each selected bandwidth class. This percentage includes bandwidth for uploads and downloads. |
| minBandwidth | integer (int32) | No | The minimum percentage of a location's bandwidth you want to be guaranteed for each selected bandwidth class. This percentage includes bandwidth for uploads and downloads. |
| name | string | Yes | Rule name |
| order | integer (int32) | No | Rule order. Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule's place in the order. You can change the value, but if you've enabled the Admin Rank, your assigned admin rank determines the rule order values you can select. |
| protocols | array[string] | No |  |
| rank | integer (int32) | No | Admin rank of the Bandwidth Control policy rule |
| state | string | No | Indicates whether the rule is enabled or disabled. An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order. The service skips it and moves to the next rule. |
| timeWindows | array[EntityReference] | No | The time interval in which the Bandwidth Control policy rule applies |

### EntityReference
This is an immutable reference to an entity that mainly consists of id and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### PolicyWebApplication
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| appCatModified | boolean | No |  |
| appNotReady | boolean | No |  |
| backendName | string | No |  |
| deprecated | boolean | No |  |
| misc | boolean | No |  |
| name | string | No |  |
| originalName | string | No |  |
| underMigration | boolean | No |  |
| val | integer (int32) | No |  |
| webApplicationClass | string | No | The cloud application class selected from the available options |

### UrlCategoryForPolicy
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| backendName | string | No |  |
| comments | string | No |  |
| deprecated | boolean | No |  |
| name | string | No |  |
| urlSupercategory | string | No |  |
| userConfiguredName | string | No |  |
