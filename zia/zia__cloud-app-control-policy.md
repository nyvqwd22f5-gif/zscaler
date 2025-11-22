# Cloud App Control Policy
Source: https://help.zscaler.com/zia/cloud-app-control-policy

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /cloudApplicationInstances`

Retrieves the list of cloud application instances configured in the ZIA Admin Portal. To learn more, see [About Cloud Application Instances](/zia/about-cloud-application-instances).

**Tags:** Cloud App Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| instanceName | query | string | No | The cloud application instance name |
| instanceType | query | string | No | The cloud application instance type |
| page | query | integer | No | Specifies the page offset |
| pageSize | query | integer | No | Specifies the page size |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[CloudApplicationInstance] |

## `POST /cloudApplicationInstances`

Add a new cloud application instance. To learn more, see [Adding a Cloud Application Instance](/zia/adding-cloud-application-instance).

**Tags:** Cloud App Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | CloudApplicationInstance | No | Cloud application instance details |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | CloudApplicationInstance |

## `DELETE /cloudApplicationInstances/{instanceId}`

Deletes a cloud application instance based on the specified ID

**Tags:** Cloud App Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| instanceId | path | integer | Yes | The cloud application instance ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /cloudApplicationInstances/{instanceId}`

Retrieves information about a cloud application instance based on the specified ID

**Tags:** Cloud App Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| instanceId | path | integer | Yes | The cloud application instance ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | CloudApplicationInstance |

## `PUT /cloudApplicationInstances/{instanceId}`

Updates information about a cloud application instance based on the specified ID

**Tags:** Cloud App Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | CloudApplicationInstance | No | Cloud application instance details |
| instanceId | path | integer | Yes | The cloud application instance ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | CloudApplicationInstance |

## `GET /tenancyRestrictionProfile`

Retrieves all the restricted tenant profiles. To learn more, see [About Tenant Profiles](/zia/about-tenant-profiles).

**Tags:** Cloud App Control Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[TenancyRestrictionProfile] |

## `POST /tenancyRestrictionProfile`

Creates restricted tenant profiles. To learn more, see [Adding Tenant Profiles](/zia/adding-tenant-profiles).

**Tags:** Cloud App Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | TenancyRestrictionProfile | No | Tenant profile information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | TenancyRestrictionProfile |

## `GET /tenancyRestrictionProfile/app-item-count/{appType}/{itemType}`

Retrieves the item count of the specified item type for a given application, excluding any specified profile

**Tags:** Cloud App Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| appType | path | string | Yes | Application type |
| itemType | path | string | Yes | Item type |
| excludeProfile | query | integer | No | Specifies the profile ID that is excluded from the item count calculation |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | integer (int32) |

## `DELETE /tenancyRestrictionProfile/{profileId}`

Deletes the restricted tenant profile based on the specified ID

**Tags:** Cloud App Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| profileId | path | integer | Yes | Profile ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /tenancyRestrictionProfile/{profileId}`

Retrieves the restricted tenant profile based on the specified ID

**Tags:** Cloud App Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| profileId | path | integer | Yes | Profile ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | TenancyRestrictionProfile |

## `PUT /tenancyRestrictionProfile/{profileId}`

Updates the restricted tenant profile based on the specified ID

**Tags:** Cloud App Control Policies
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| profileId | path | integer | Yes | Profile ID |
| body | body | TenancyRestrictionProfile | No | Tenant profile information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | TenancyRestrictionProfile |

## `GET /webApplicationRules/ruleTypeMapping`

Gets the backend keys that match the application type string.

**Tags:** Cloud App Control Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | object |

## `GET /webApplicationRules/{rule_type}`

Gets the list of cloud application rules by the type of rule.

**Tags:** Cloud App Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| rule_type | path | string | Yes | The rule type selected from the available options |
| search | query | string | No | The search string used to match against a rule type option. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[WebApplicationRule] |

## `POST /webApplicationRules/{rule_type}`

Adds a new cloud application rule.

**Tags:** Cloud App Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| rule_type | path | string | Yes | The rule type selected from the available options |
| body | body | WebApplicationRule | No | The Cloud App Control policy rule information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | WebApplicationRule |

## `POST /webApplicationRules/{rule_type}/availableActions`

Fetches the granular actions supported for the applications.

**Tags:** Cloud App Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| rule_type | path | string | Yes | The rule type selected from the available options |
| body | body | WebApplicationTypeList | No | The Cloud App Control policy rule information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[string] |

## `POST /webApplicationRules/{rule_type}/duplicate/{ruleId}`

Duplicates a Cloud App Control policy rule.

**Tags:** Cloud App Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| rule_type | path | string | Yes | The rule type selected from the available options |
| ruleId | path | integer | Yes | The ID of the Cloud App Control policy rule. |
| name | query | string | No | The duplicated Cloud App Control policy rule's name. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | WebApplicationRule |

## `DELETE /webApplicationRules/{rule_type}/{ruleId}`

Deletes a Cloud App Control policy rule.

**Tags:** Cloud App Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| rule_type | path | string | Yes | The rule type selected from the available options |
| ruleId | path | integer | Yes | The ID of the Cloud App Control policy rule. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /webApplicationRules/{rule_type}/{ruleId}`

Gets a Cloud App Control policy rule by the rule type and ID.

**Tags:** Cloud App Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| rule_type | path | string | Yes | The rule type selected from the available options |
| ruleId | path | integer | Yes | The ID of the Cloud App Control policy rule. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | WebApplicationRule |

## `PUT /webApplicationRules/{rule_type}/{ruleId}`

Updates the Cloud App Control policy rule.

**Tags:** Cloud App Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| rule_type | path | string | Yes | The rule type selected from the available options |
| ruleId | path | integer | Yes | The ID of the Cloud App Control policy rule. |
| body | body | WebApplicationRule | No | The Cloud App Control policy rule information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | WebApplicationRule |

## Models
### BrowserIsolationProfile
Information about browser isolation profile. To learn more, see [What Is Isolation?](/isolation/what-isolation) and [Creating Isolation Profiles for ZIA](/isolation/creating-zia-isolation-profile-isolation).
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| defaultProfile | boolean | No | (Optional) Indicates whether this is a default browser isolation profile. Zscaler sets this field. |
| id | string | No | The universally unique identifier (UUID) for the browser isolation profile |
| name | string | No | Name of the browser isolation profile |
| url | string | No | The browser isolation profile URL |

### CloudApplicationInstance
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| instanceId | integer (int32) | No | Cloud application instance ID |
| instanceIdentifiers | array[CloudApplicationInstanceIdentifier] | No | List of cloud application instance identifiers |
| instanceName | string | No | Cloud application instance name |
| instanceType | string | No | Cloud application instance type |
| modifiedAt | integer (int32) | No | Timestamp of when the instance was last modified |
| modifiedBy | EntityReference | No | The user who last modified the instance |

### CloudApplicationInstanceIdentifier
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| identifierType | string | No | Type of the cloud application instance identifier |
| instanceId | integer (int32) | No | ID of the cloud application instance identifier |
| instanceIdentifier | string | No | Cloud application instance identifier, such as URL, IP address, or keyword. |
| instanceIdentifierName | string | No | Name of  the cloud application instance identifier |
| modifiedAt | integer (int32) | No | Timestamp when the cloud application instance identifier was last modified |
| modifiedBy | EntityReference | No | The user who last modified the cloud application instance identifier |

### CloudApplicationInstanceLite
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| id | integer (int32) | No | The cloud application instance ID. |
| name | string | No | The cloud application instance name. |
| type | string | No | The instance of the cloud application selected from the available options |

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

### TenancyRestrictionProfile
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| allowGcpCloudStorageRead | boolean | No | Flag to allow or disallow cloud storage resources for GCP |
| allowGoogleConsumers | boolean | No | Flag to allow Google consumers |
| allowGoogleVisitors | boolean | No | Flag to allow Google visitors |
| appType | string | No | Restricted tenant profile application type |
| description | string | No | Additional information about the profile |
| id | integer (int32) | No | System-generated tenant profile ID |
| itemDataPrimary | array[string] | No | Tenant profile primary item data |
| itemDataSecondary | array[string] | No | Tenant profile secondary item data |
| itemTypePrimary | string | No | Tenant profile primary item type |
| itemTypeSecondary | string | No | Tenant profile secondary item type |
| itemValue | array[string] | No | Tenant profile item value for YouTube category |
| msLoginServicesTrV2 | boolean | No | Flag to decide between v1 and v2 for tenant restriction on MSLOGINSERVICES |
| name | string | No | Tenant profile name |
| restrictPersonalO365Domains | boolean | No | Flag to restrict personal domains for Office 365 |

### WebApplicationRule
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| accessControl | string | No | Access privilege of this rule based on the admin's RBA state. |
| actions | array[string] | No | Action taken when traffic matches rule. |
| applications | array[PolicyWebApplication] | No | List of cloud applications for which rule will be applied |
| browserEunTemplateId | integer (int32) | No |  |
| cascadingEnabled | boolean | No |  |
| cbiProfile | BrowserIsolationProfile | No | Cloud browser isolation profile info |
| cloudAppInstances | array[CloudApplicationInstanceLite] | No |  |
| cloudAppRiskProfile | EntityReference | No | Name-ID pair of cloud Application Risk Profile for which rule will be applied |
| departments | array[EntityReference] | No | Name-ID pairs of departments for which rule will be applied |
| description | string | No | Additional information about this rule |
| deviceGroups | array[EntityReference] | No | Name-ID pairs of device groups for which rule will be applied |
| deviceTrustLevels | array[string] | No | List of device trust levels for which the rule must be applied. While the High Trust, Medium Trust, or Low Trust evaluation is applicable only to Zscaler Client Connector traffic, Unknown evaluation applies to all traffic. The trust levels are assigned to the devices based on your [posture configurations](/client-connector/adding-zia-posture-profiles) in the Zscaler Client Connector Portal. If no value is set, this field  is ignored during the policy evaluation. |
| devices | array[EntityReference] | No | Name-ID pairs of device for which rule will be applied |
| enforceTimeValidity | boolean | No | Enforce a set a validity time period for the Web Application rule |
| eunEnabled | boolean | No |  |
| eunTemplateId | integer (int32) | No |  |
| formSharingDomainProfiles | array[EntityReference] | No |  |
| groups | array[EntityReference] | No | Name-ID pairs of groups for which rule must be applied |
| id | integer (int32) | No | Web Application Rule Id |
| labels | array[EntityReference] | No | Rule label for the policy |
| lastModifiedBy | EntityReference | No | Who modified the rule last |
| lastModifiedTime | integer (int32) | No |  |
| locationGroups | array[EntityReference] | No | Name-ID pairs of locations groups for which rule must be applied. |
| locations | array[EntityReference] | No | Name-ID pairs of locations for which rule must be applied |
| name | string | No | Rule Name |
| numberOfApplications | integer (int32) | No |  |
| order | integer (int32) | No | Order of execution of rule with respect to other Web Application rules |
| predefined | boolean | No |  |
| rank | integer (int32) | No | Admin rank of the admin who creates this rule |
| sharingDomainProfiles | array[EntityReference] | No |  |
| sizeQuota | integer (int32) | No | Daily limit value for size up to which uploading and/or downloading of data is allowed from the Web Application Rule |
| state | string | No | Rule State |
| tenancyProfileIds | array[EntityReference] | No |  |
| timeQuota | integer (int32) | No | Daily limit value for time up to which uploading and/or downloading of data is allowed from the Web Application Rule |
| timeWindows | array[EntityReference] | No | Name-ID pairs of time interval during which rule must be enforced. |
| type | string | No |  |
| userAgentTypes | array[string] | No | User Agent types on which this rule will be applied |
| userRiskScoreLevels | array[string] | No | List of user risk score levels for which policy must be applied. If not set, policy will be applied for all user risk score levels. |
| users | array[EntityReference] | No | Name-ID pairs of users for which rule must be applied |
| validityEndTime | integer (int32) | No | If enforceTimeValidity is set to true, the Web Application rule ceases to be valid on this end date and time. |
| validityStartTime | integer (int32) | No | If enforceTimeValidity is set to true, the Web Application rule ceases to be valid on this start date and time. |
| validityTimeZoneId | string | No | Validity time zone id for start and end time if rule has time based expiry |

### WebApplicationTypeList
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| cloudApps | array[PolicyWebApplication] | No | Web Applications |
| type | string | No |  |
