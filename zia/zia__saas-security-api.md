# SaaS Security API
Source: https://help.zscaler.com/zia/saas-security-api

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /casbDlpRules`

Retrieves the SaaS Security Data at Rest Scanning Data Loss Prevention (DLP) rules based on the specified rule type. To learn more, see [About Data at Rest Scanning DLP](/zia/about-data-rest-scanning-dlp).

**Tags:** SaaS Security API
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleType | query | string | No | Specifies the DLP rule type |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[CASBDlpRule] |

## `POST /casbDlpRules`

Adds a new SaaS Security Data at Rest Scanning DLP rule. To learn more, see [Configuring the Data at Rest Scanning DLP Policy](/zia/configuring-data-rest-scanning-dlp-policy).

**Tags:** SaaS Security API
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | CASBDlpRule | No | Information about the SaaS Security Data at Rest Scanning DLP rule |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | CASBDlpRule |

## `GET /casbDlpRules/all`

Retrieves all the SaaS Security Data at Rest Scanning DLP rules

**Tags:** SaaS Security API
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[CASBDlpRule] |

## `DELETE /casbDlpRules/{ruleId}`

Deletes the SaaS Security Data at Rest Scanning DLP rule based on the specified ID

**Tags:** SaaS Security API
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Rule ID |
| ruleType | query | string | No | Rule type |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /casbDlpRules/{ruleId}`

Retrieves the SaaS Security Data at Rest Scanning DLP rule based on the specified ID

**Tags:** SaaS Security API
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Rule ID |
| ruleType | query | string | No | Rule type |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | CASBDlpRule |

## `PUT /casbDlpRules/{ruleId}`

Updates the SaaS Security Data at Rest Scanning DLP rule based on the specified ID

**Tags:** SaaS Security API
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Rule ID |
| body | body | CASBDlpRule | No | Information about the SaaS Security Data at Rest Scanning DLP rule |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | CASBDlpRule |

## `GET /casbEmailLabel/lite`

Retrieves the email labels generated for the SaaS Security policies in a user's email account. To learn more, see [About Email Labels](/zia/about-email-labels).

**Tags:** SaaS Security API
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[CasbEmailLabel] |

## `GET /casbMalwareRules`

Retrieves the SaaS Security Data at Rest Scanning Malware Detection rules based on the specified rule type. To learn more, see [About Data at Rest Scanning Malware Detection](/zia/about-data-rest-scanning-malware-detection).

**Tags:** SaaS Security API
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleType | query | string | No | Rule type |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[CASBMalwareRule] |

## `POST /casbMalwareRules`

Adds a new SaaS Security Data at Rest Scanning Malware Detection rule. To learn more, see [Configuring the Data at Rest Scanning Malware Detection Policy](/zia/configuring-data-rest-scanning-malware-detection-policy).

**Tags:** SaaS Security API
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | CASBMalwareRule | No | Information about the SaaS Security Data at Rest Scanning Malware Detection rule |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | CASBMalwareRule |

## `GET /casbMalwareRules/all`

Retrieves all the SaaS Security Data at Rest Scanning Malware Detection rules

**Tags:** SaaS Security API
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[CASBMalwareRule] |

## `DELETE /casbMalwareRules/{ruleId}`

Deletes the SaaS Security Data at Rest Scanning Malware Detection rule based on the specified ID

**Tags:** SaaS Security API
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Rule ID |
| ruleType | query | string | No | Rule type |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /casbMalwareRules/{ruleId}`

Retrieves the SaaS Security Data at Rest Scanning Malware Detection rule based on the specified ID

**Tags:** SaaS Security API
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Rule ID |
| ruleType | query | string | No | Rule type |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | CASBMalwareRule |

## `PUT /casbMalwareRules/{ruleId}`

Updates the SaaS Security Data at Rest Scanning Malware Detection rule based on the specified ID

**Tags:** SaaS Security API
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Rule ID |
| body | body | CASBMalwareRule | No | Information about the SaaS Security Data at Rest Scanning Malware Detection rule |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | CASBMalwareRule |

## `GET /casbTenant/lite`

Retrieves information about the SaaS application tenant. To learn more, see [About SaaS Application Tenants](/zia/about-saas-application-tenants).

**Tags:** SaaS Security API
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| activeOnly | query | boolean | No | Indicates that the tenant is in use. Policies are enforced for this SaaS application. |
| includeDeleted | query | boolean | No |  |
| appType | query | string | No | Specifies the SaaS application type |
| app | query | string | No | Specifies the sanctioned SaaS application |
| scanConfigTenantsOnly | query | boolean | No | Specifies the tenant for which the scan is already configured |
| includeBucketReadyS3Tenants | query | boolean | No | For the AWS S3 SaaS application, this parameter indicates that the buckets have been read and are ready for use in policies and scan configurations. |
| filterByFeature | query | array | No | Filters the SaaS application tenant by feature |
| page | query | integer | No | Specifies the page offset |
| pageSize | query | integer | No | Specifies the page size |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |

## `GET /casbTenant/scanInfo`

Retrieves the SaaS Security Scan Configuration information. To learn more, see [About SaaS Security Scan Configuration](/zia/about-saas-security-scan-configuration).

**Tags:** SaaS Security API
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer | No | Specifies the page offset |
| pageSize | query | integer | No | Specifies the page size |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[CasbTenantScanInfo] |

## `GET /casbTenant/validate/status/{tenantId}`

Retrieves the validation status of the SaaS application tenant based on the tenant ID

**Tags:** SaaS Security API
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| tenantId | path | integer | Yes | SaaS application tenant ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | CasbTenantValidationResponse |

## `GET /casbTenant/{tenantId}/tags/policy`

Retrieves the tags used in the policy rules associated with a tenant, based on the tenant ID.

**Tags:** SaaS Security API
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| tenantId | path | integer | Yes | SaaS application tenant ID |
| page | query | integer | No | Specifies the page offset |
| pageSize | query | integer | No | Specifies the page size |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[CASBTenantTags] |

## `GET /domainProfiles/lite`

Retrieves the domain profile summary. To learn more about domain profiles, navigate to the 'Domain Profiles' section from [About Email Profiles](/zia/about-email-profiles).

**Tags:** SaaS Security API
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[DomainProfile] |

## `GET /quarantineTombstoneTemplate/lite`

Retrieves the templates for the tombstone file created when a file is quarantined. To learn more, see [About Quarantine Tombstone File Templates](/zia/about-quarantine-tombstone-file-templates).

**Tags:** SaaS Security API
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[QuarantineTombstoneTemplate] |

## Models
### CASBDlpRule
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| accessControl | string | No | Access privilege of this rule based on the admin's Role Based Authorization (RBA) state |
| action | string | No | The configured action for the policy rule |
| auditor | EntityReference | No | Selects an auditor for the rule. If you do not select an auditor, notifications are not sent for this rule. |
| auditorNotification | EntityReference | No | Notification template used for DLP email alerts sent to the auditor |
| bucketOwner | string | No | A user who inspect their buckets for sensitive data. When you choose a user, their buckets are available in the Buckets field. |
| buckets | array[EntityReference] | No | The buckets for the Zscaler service to inspect for sensitive data |
| casbEmailLabel | EntityReference | No | Name-ID of the email label associated with the rule |
| casbTombstoneTemplate | EntityReference | No | Name-ID of the quarantine tombstone template associated with the rule |
| cloudAppTenants | array[EntityReference] | No | Name-ID pairs of the cloud application tenants for which the rule is applied. If the name-ID pairs of the cloud application tenants are not specified, the rule is applied to all tenants. |
| collaborationScope | array[string] | No | Collaboration scope for the rule |
| components | array[string] | No | List of components for which the rule is applied. Zscaler service inspects these components for sensitive data. |
| contentLocation | string | No | The location for the content that the Zscaler service inspects for sensitive data |
| criteriaDomainProfiles | array[EntityReference] | No | Name-ID pairs of domain profiles that are mandatory in the criteria for the rule |
| departments | array[EntityReference] | No | Name-ID pairs of departments for which the rule is applied. If not set, the rule is applied to all departments. |
| description | string | No | An admin editable text-based description of the rule |
| deviceGroups | array[EntityReference] | No | Name-ID pairs of device groups for which the rule must be applied. This field is applicable for devices that are managed using Zscaler Client Connector. If no value is set, this field is ignored during the policy evaluation. |
| deviceTrustLevels | array[string] | No | List of device trust levels for which the rule must be applied. While the High Trust, Medium Trust, or Low Trust evaluation is applicable only to Zscaler Client Connector traffic, Unknown evaluation applies to all traffic. The trust levels are assigned to the devices based on your posture configurations in the Zscaler Client Connector Portal. If no value is set, this field is ignored during the policy evaluation. |
| devices | array[EntityReference] | No | Name-ID pairs of devices for which rule must be applied. Specifies devices that are managed using Zscaler Client Connector. If no value is set, this field is ignored during the policy evaluation. |
| dlpEngines | array[EntityReference] | No | DLP engines whose violation is checked by this rule |
| domains | array[string] | No | The domain for the external organization sharing the channel. This field is applicable only when you select CONTENT_LOCATION_SHARED_CHANNEL in the 'contentLocation' field. |
| emailRecipientProfiles | array[EntityReference] | No | Name-ID pairs of recipient profiles for which the rule is applied. The rule is applied only when there is at least one email recipient from outside an organization, and that recipient is not an external trusted user or is not using an external trusted domain. |
| entityGroups | array[EntityReference] | No | Name-ID pairs of entity groups that are part of the rule criteria |
| excludedDomainProfiles | array[EntityReference] | No | Name-ID pairs of domain profiles excluded in the criteria for the rule |
| externalAuditorEmail | string | No | Email address of the external auditor to whom the DLP email alerts are sent |
| fileTypes | array[string] | No | File types for which the rule is applied. If not set, the rule is applied across all file types. |
| groups | array[EntityReference] | No | Name-ID pairs of groups for which the rule is applied. If not set, the rule is applied for all groups. |
| id | integer (int32) | No | System-generated identifier for the SaaS Security Data at Rest Scanning DLP rule |
| includeCriteriaDomainProfile | boolean | No | If true, criteriaDomainProfiles is included as part of the criteria, else they are excluded from the criteria. |
| includeEmailRecipientProfile | boolean | No | If true, emailRecipientProfiles is included as part of the criteria, else they are excluded from the criteria. |
| includeEntityGroups | boolean | No | If true, entityGroups is included as part of the criteria, else are excluded from the criteria. |
| includedDomainProfiles | array[EntityReference] | No | Name-ID pairs of domain profiles included in the criteria for the rule |
| labels | array[EntityReference] | No | Name-ID pairs of rule labels associated with the rule |
| lastModifiedBy | EntityReference | No | Admin user that last modified the rule |
| lastModifiedTime | integer (int32) | No | Timestamp of when the rule was last modified |
| name | string | Yes | Rule name |
| numberOfExternalCollaborators | string | No | Selects the number of external collaborators for files that are shared with specific collaborators outside of an organization |
| numberOfInternalCollaborators | string | No | Selects the number of internal collaborators for files that are shared with specific collaborators or are discoverable within an organization |
| objectTypes | array[CasbDlpObjectType] | No | List of object types for which the rule is applied |
| order | integer (int32) | Yes | Order of rule execution with respect to other SaaS Security Data at Rest Scanning DLP rules |
| quarantineLocation | string | No | Location where all the quarantined files are moved and necessary actions are taken by either deleting or restoring the data |
| rank | integer (int32) | No | Admin rank that is assigned to this rule. Mandatory when admin rank-based access restriction is enabled. |
| receiver | IncidentReceiver | No | Details of the DLP Incident Receiver, which could be one of the following types: [Zscaler Incident Receiver](/zia/about-zscaler-incident-receiver) or [a Cloud-to-Cloud Incident Forwarding tenant](/zia/dlp-cloud-cloud-incident-forwarding). |
| recipient | string | No | Specifies if the email recipient is internal or external |
| redactionProfile | EntityReference | No | Name-ID of the redaction profile in the criteria |
| severity | string | No | The severity level of the incidents that match the policy rule |
| state | string | No | Administrative state of the rule |
| tag | EntityReference | No | Tag applied to the rule |
| type | string | No | The type of SaaS Security Data at Rest Scanning DLP rule |
| users | array[EntityReference] | No | Name-ID pairs of users for which rule is applied. If not set, the rule is applied to all users. |
| watermarkDeleteOldVersion | boolean | No | A Boolean value that specifies whether to delete an old version of the watermarked file |
| watermarkProfile | EntityReference | No | Watermark profile applied to the rule. To learn more, see [Adding & Editing Watermark Profiles](/zia/adding-editing-watermark-profiles). |
| withoutContentInspection | boolean | No | If true, Content Matching is set to None |
| zscalerIncidentReceiver | EntityReference | No | This attribute is deprecated and is no longer supported. It is replaced by the **receiver** attribute. Previously, **zscalerIncidentReceiver** was used to specify the Zscaler Incident Receiver to associate with the DLP policy rule, whereas **receiver** is currently used to specify the DLP Incident Receiver details for any given type of the Incident Receiver.
**Note**: API calls using this attribute would not be successful. To ensure continued API operation, you must immediately update your configurations to use the **receiver** attribute in the corresponding endpoints. |

### CASBMalwareRule
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| accessControl | string | No | Access privilege of this rule based on the admin's Role Based Authorization (RBA) state |
| action | string | No | The configured action for the policy rule |
| buckets | array[EntityReference] | No | The buckets for the Zscaler service to inspect for sensitive data |
| casbEmailLabel | EntityReference | No | Name-ID of the email label associated with the rule |
| casbTombstoneTemplate | EntityReference | No | Name-ID of the quarantine tombstone template associated with the rule |
| cloudAppTenants | array[EntityReference] | No | Name-ID pairs of the cloud application tenants for which the rule is applied. If the name-ID pairs of the cloud application tenants are not specified, the rule is applied to all tenants. |
| id | integer (int32) | No | System-generated identifier for a SaaS Security Data at Rest Scanning Malware rule |
| labels | array[EntityReference] | No | Name-ID pairs of rule labels associated with the rule |
| lastModifiedBy | EntityReference | No | Admin user that last modified the rule |
| lastModifiedTime | integer (int32) | No | Timestamp of when the rule was last modified |
| name | string | Yes | Rule name |
| order | integer (int32) | Yes | Order of rule execution with respect to other SaaS Security Data at Rest Scanning Malware rules |
| quarantineLocation | string | No | Location where all the quarantined files are moved and necessary actions are taken by either deleting or restoring the data |
| scanInboundEmailLink | string | No | Enables or disables the scan inbound email link |
| state | string | No | Administrative state of the rule |
| type | string | No | The type of SaaS Security Data at Rest Scanning Malware rule |

### CASBTenantTags
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| deleted | boolean | No | A Boolean value that indicates whether or not a tag is deleted |
| tagId | integer (int32) | No | System-generated tag ID |
| tagName | string | No | Tag name |
| tagUUID | string | No | Universally Unique Identifier (UUID) of the tag |
| tenantId | integer (int32) | No | Tenant ID to which the tag belongs |

### CasbDlpObjectType
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| id | integer (int32) | No | The DLP object type ID |
| name | string | No | Name of the DLP rule object type defined in the criteria |

### CasbEmailLabel
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| id | integer (int32) | No | SaaS Security email label ID |
| labelColor | string | No | Color to apply to the email label |
| labelDeleted | boolean | No | A Boolean value that indicates whether or not the email label is deleted |
| labelDesc | string | No | Description of the email label |
| name | string | No | SaaS Security email label name |

### CasbScanInfo
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| cur_scan_start_time | integer (int64) | No | The SaaS Security scan start time. A scan starts running when the initialization is completed successfully. |
| prev_scan_end_time | integer (int64) | No | Timestamp of when the SaaS Security Data at Rest Scanning policies for a tenant were last scanned |
| scan_reset_num | integer (int64) | No |  |

### CasbTenantScanInfo
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| saasApplication | string | No | The sanctioned SaaS application type |
| scanAction | integer (int32) | No |  |
| scanInfo | CasbScanInfo | No | The scan configuration information |
| tenantId | integer (int32) | No | The SaaS application tenant ID |
| tenantName | string | No | The SaaS application tenant name |

### CasbTenantValidationJsonMsg
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| errorCode | integer (int32) | No | The validation error code |
| errorMsg | string | No | The validation error message |

### CasbTenantValidationResponse
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| lastTenantValidationTime | integer (int32) | No | Timestamp of when the scan was last validated |
| lastValidationMsg | CasbTenantValidationJsonMsg | No | The validation error message information |
| status | array[string] | No | Status of the scan |
| tenantAuthorizationInfo | TenantAuthorizationInfo | No |  |
| tenantDeleted | boolean | No |  |
| tenantId | integer (int32) | No | The SaaS application tenant ID |
| tenantName | string | No | The SaaS application tenant name |

### DlpQuarantineInfo
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| adminId | string | No |  |
| modTime | integer (int64) | No |  |
| qtnFolderPath | string | No |  |

### DomainProfile
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| customDomains | array[string] | No | List of custom domains for the domain profile. There can be one or more custom domains. |
| description | string | No | Additional notes or information about the domain profile |
| includeCompanyDomains | boolean | No | A Boolean flag to determine if the organizational domains have to be included in the domain profile |
| includeSubdomains | boolean | No | A Boolean flag to determine whether or not to include subdomains |
| predefinedEmailDomains | array[string] | No | List of predefined email service provider domains for the domain profile |
| profileId | integer (int32) | No | Domain profile ID |
| profileName | string | No | Domain profile name |

### EntityReference
This is an immutable reference to an entity that mainly consists of an ID and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### ICAPServer
DLP server (i.e., servers using ICAP) information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| id | integer (int32) | No | The unique identifier for a DLP server. |
| name | string | Yes | The DLP server name. |
| status | string | Yes | The DLP server status |
| url | string | Yes | The DLP server URL. |

### IncidentReceiver
Information about the DLP Incident Receiver
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| id | integer (int64) | No | ID of the Incident Receiver |
| name | string | No | The configured name of the Incident Receiver |
| tenant | EntityReference | No | Name-ID pair of the SaaS application tenant, applicable when the Cloud-to-Cloud Incident Forwarding type is used. |
| type | string | Yes | Incident Receiver type |

### QuarantineTombstoneTemplate
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| description | string | Yes | The text that is included in the tombstone file |
| id | integer (int32) | No | Tombstone file template ID |
| name | string | Yes | Tombstone file template name |

### TenantAuthorizationInfo
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| accessToken | string | No | The access token issued to the SaaS tenant application by the authorization serverfor tenant authorization |
| apicp | string | No |  |
| botId | string | No |  |
| botToken | string | No |  |
| clientId | string | No |  |
| clientSecret | string | No |  |
| cloudTrailBucketName | string | No |  |
| credJson | string | No |  |
| credentials | string | No |  |
| dlpQtnLibName | string | No |  |
| enterpriseId | string | No |  |
| env | string | No | Specifies the SaaS tenant environment |
| externalId | string | No |  |
| featuresSupported | array[string] | No |  |
| instanceUrl | string | No |  |
| malQtnLibName | string | No |  |
| orgApiKey | string | No |  |
| organizationId | string | No |  |
| qtnInfo | array[DlpQuarantineInfo] | No |  |
| qtnInfoCleared | boolean | No |  |
| quarantineBucketName | string | No |  |
| redirectUrl | string | No |  |
| restApiEndpoint | string | No |  |
| role | string | No |  |
| roleArn | string | No |  |
| secretToken | string | No |  |
| smirBucketConfig | array[ICAPServer] | No |  |
| subdomain | string | No |  |
| tempAuthCode | string | No |  |
| tokenEndpoint | string | No |  |
| type | string | No |  |
| userName | string | No |  |
| userPwd | string | No |  |
| workspaceId | string | No |  |
| workspaceName | string | No |  |
