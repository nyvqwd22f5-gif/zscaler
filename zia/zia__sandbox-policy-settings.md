# Sandbox Policy & Settings
Source: https://help.zscaler.com/zia/sandbox-policy-settings

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /behavioralAnalysisAdvancedSettings`

Gets the custom list of MD5 file hashes that are blocked by Sandbox

**Tags:** Sandbox Policy & Settings
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | BaAdvancedSettings |

## `PUT /behavioralAnalysisAdvancedSettings`

Updates the custom list of MD5 file hashes that are blocked by Sandbox. This overwrites a previously generated blocklist. If you need to completely erase the blocklist, submit an empty list.
**Note:** Only the file types that are supported by Sandbox analysis can be blocked using MD5 hashes.

**Tags:** Sandbox Policy & Settings
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | BaAdvancedSettings | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | BaAdvancedSettings |

## `GET /behavioralAnalysisAdvancedSettings/fileHashCount`

Gets the used and unused quota for blocking MD5 file hashes with Sandbox

**Tags:** Sandbox Policy & Settings
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | CustomFileHashQuota |

## `GET /sandboxRules`

Retrieves the list of all Sandbox policy rules configured in the ZIA Admin Portal. To learn more, see [About Sandbox](/zia/about-sandbox).

**Tags:** Sandbox Policy & Settings
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[BARule] |

## `POST /sandboxRules`

Adds a Sandbox policy rule. To learn more, see [Configuring the Sandbox Policy](/zia/configuring-sandbox-policy).

**Tags:** Sandbox Policy & Settings
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | BARule | Yes | Sandbox policy configuration |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | BARule |

## `DELETE /sandboxRules/{ruleId}`

Deletes the Sandbox policy rule based on the specified ID

**Tags:** Sandbox Policy & Settings
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Unique identifier of the Sandbox policy rule |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /sandboxRules/{ruleId}`

Retrieves the Sandbox policy rule information based on the specified ID

**Tags:** Sandbox Policy & Settings
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Unique identifier of the Sandbox policy rule |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | BARule |

## `PUT /sandboxRules/{ruleId}`

Updates the Sandbox policy rule configuration for the specified ID

**Tags:** Sandbox Policy & Settings
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Unique identifier of the Sandbox policy rule |
| body | body | BARule | Yes | Sandbox policy configuration |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | BARule |

## Models
### AppSegment
Application Segment information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| externalId | integer (int64) | No | Indicates the external ID. Applicable only when this reference is of an external entity. |
| id | integer (int32) | No | A unique identifier assigned to the Application Segment |
| name | string | No | The name of the Application Segment |
| zpaTenantId | integer (int64) | No | ID of the ZPA tenant where the Application Segment is configured |

### BARule
Sandbox policy rule configuration details. To learn more, see [Configuring the Sandbox Policy](/zia/configuring-sandbox-policy).
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| accessControl | string | No | The admin’s access privilege to this rule based on the assigned role |
| baPolicyCategories | array[string] | No | The threat categories to which the rule applies |
| baRuleAction | string | No | The action configured for the rule that must take place if the traffic matches the rule criteria |
| byThreatScore | integer (int32) | No |  |
| cbiProfile | BrowserIsolationProfile | No | The cloud browser isolation profiles to which the rule applies. This field is applicable only when the rule action is set to isolate. |
| cbiProfileId | integer (int32) | No | Unique identifier of the cloud browser isolation profiles to which the rule applies |
| defaultRule | boolean | No | A Boolean value that indicates whether the rule is marked as the default rule. |
| departments | array[EntityReference] | No | The departments to which the rule applies |
| description | string | No | The description of the rule |
| deviceGroups | array[EntityReference] | No | The list of device groups to which the rule applies. This field is applicable for devices that are managed using Zscaler Client Connector. If no value is set, this field is ignored during the policy evaluation. |
| devices | array[EntityReference] | No | The list of devices to which the rule applies. This field specifies devices that are managed using Zscaler Client Connector. If no value is set, this field is ignored during the policy evaluation. |
| fileTypes | array[string] | Yes | The file types to which the rule applies |
| firstTimeEnable | boolean | No | A Boolean value indicating whether a First-Time Action is specifically configured for the rule. The First-Time Action takes place when users download unknown files. The action to be applied is specified using the firstTimeOperation field. |
| firstTimeOperation | string | No | The action that must take place when users download unknown files for the first time |
| groups | array[EntityReference] | No | The user groups to which the rule applies |
| id | integer (int32) | No | Unique identifier generated for the rule |
| labels | array[EntityReference] | No | The label associated with the rule |
| lastModifiedBy | EntityReference | No | The admin who last modified the rule |
| lastModifiedTime | integer (int32) | No | The timestamp when the rule was last modified |
| locationGroups | array[EntityReference] | No | The location groups to which the rule applies |
| locations | array[EntityReference] | No | The locations to which the rule applies |
| mlActionEnabled | boolean | No | A Boolean value indicating whether to enable or disable the AI Instant Verdict option to have the Zscaler service use AI analysis to instantly assign threat scores to unknown files. This option is available to use only with specific rule actions such as Quarantine and Allow and Scan for First-Time Action. |
| name | string | Yes | The name of the Sandbox rule |
| order | integer (int32) | Yes | Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and this field specifies the order of execution for the rule. |
| protocols | array[string] | No | The protocols to which the rule applies |
| rank | integer (int32) | No | The admin rank specified for the rule based on your assigned admin rank. Admin rank determines the rule order that can be specified for the rule. Admin rank can be configured if it is enabled in the Advanced Settings. To learn more, see [About Admin Rank](/zia/about-admin-rank). |
| state | string | No | The state of the rule indicating whether it is enabled or disabled |
| timeWindows | array[EntityReference] | No | The time intervals during which the rule applies |
| urlCategories | array[UrlCategoryForPolicy] | No | The URL categories to which the rule applies |
| users | array[EntityReference] | No | The users to which the rule applies |
| zpaAppSegments | array[AppSegment] | No | The list of ZPA application segments to which the rule applies. This field is applicable only for the ZPA Gateway forwarding method. |

### BaAdvancedSettings
Advanced Sandbox Settings
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| md5HashValueList | array[UrlDetails] | No | A custom list of unique MD5 file hashes that must be blocked by Sandbox. A maximum of 10,000 MD5 file hashes can be blocked. |

### BrowserIsolationProfile
Information about browser isolation profile. To learn more, see [What Is Isolation?](/isolation/what-isolation) and [Creating Isolation Profiles for ZIA](/isolation/creating-zia-isolation-profile-isolation).
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| defaultProfile | boolean | No | (Optional) Indicates whether this is a default browser isolation profile. Zscaler sets this field. |
| id | string | No | The universally unique identifier (UUID) for the browser isolation profile |
| name | string | No | Name of the browser isolation profile |
| url | string | No | The browser isolation profile URL |

### CustomFileHashQuota
Used and unused quota for blocking MD5 file hashes.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| blockedFileHashesCount | integer (int32) | No | The number of unique MD5 file hashes that are blocked by Sandbox. |
| remainingFileHashes | integer (int32) | No | Unused quota for blocking MD5 file hashes. |

### EntityReference
This is an immutable reference to an entity that mainly consists of an ID and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### UrlCategoryForPolicy
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

### UrlDetails
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| type | string | No | This field is for Zscaler internal use only |
| url | string | No | The URL that has a match in one or more existing custom URL categories |
| urlComment | string | No | Additional information about the URL. This is an optional field. |
