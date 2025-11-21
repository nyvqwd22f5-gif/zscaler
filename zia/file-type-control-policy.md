# File Type Control Policy
Source: https://help.zscaler.com/zia/file-type-control-policy

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /customFileTypes`

Retrieves the list of [custom file types](/zia/configuring-custom-file-types). Custom file types can be configured as rule conditions in different ZIA policies.

**Tags:** File Type Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer | No | Specifies the page offset |
| pageSize | query | integer | No | Specifies the page size |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[CustomFileType] |

## `POST /customFileTypes`

Adds a new custom file type. To learn more, see [Configuring Custom File Types](/zia/configuring-custom-file-types).

**Tags:** File Type Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | CustomFileType | No | Custom file type information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | CustomFileType |

## `PUT /customFileTypes`

Updates information for a custom file type based on the specified ID

**Tags:** File Type Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | CustomFileType | No | The request Body contains the custom file type information to be updated and also specifies the ID of the custom file to be modified. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | CustomFileType |

## `GET /customFileTypes/count`

Retrieves the count of custom file types available

**Tags:** File Type Control Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | integer (int32) |

## `DELETE /customFileTypes/{id}`

Deletes a custom file type based on the specified ID

**Tags:** File Type Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer | Yes | Custom file type ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /customFileTypes/{id}`

Retrieves information about a custom file type based on the specified ID

**Tags:** File Type Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer | Yes | Custom file type ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | CustomFileType |

## `GET /fileTypeCategories`

Retrieves the list of all file types, including predefined and custom file types, available for configuring rule conditions in different ZIA policies. You can retrieve predefined file types for specific file categories of policies by using the **enum** request parameter and by specifying one of the following values:
- `ZSCALERDLP`: Web DLP rules with content inspection
- `EXTERNALDLP`: Web DLP rules without content inspection
- `FILETYPECATEGORYFORFILETYPECONTROL`: File Type Control policy

**Tags:** File Type Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| enums | query | array | No | Specifies the file type category for specific policies to retrieve the corresponding list of predefined file types supported for the policy category. The following values are supported:
- `ZSCALERDLP`: DLP rules with content inspection
- `EXTERNALDLP`: DLP rules without content inspection
- `FILETYPECATEGORYFORFILETYPECONTROL`: File Type Control policy |
| excludeCustomFileTypes | query | boolean | No | A Boolean value specifying whether custom file types must be excluded from the list or not |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[FileTypeCategoryDTO] |

## `GET /fileTypeRules`

Retrieves all the rules in the File Type Control policy

**Tags:** File Type Control Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[FileTypeRule] |

## `POST /fileTypeRules`

Adds a new File Type Control policy rule

**Tags:** File Type Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | FileTypeRule | No | The File Type Control policy rule information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | FileTypeRule |

## `GET /fileTypeRules/lite`

Retrieves all the rules in the File Type Control policy

**Tags:** File Type Control Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[FileTypeRule] |

## `DELETE /fileTypeRules/{ruleId}`

Deletes a File Type Control policy rule information for the specified ID

**Tags:** File Type Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Unique identifier for the policy rule |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /fileTypeRules/{ruleId}`

Retrieves the File Type Control policy rule information for the specified ID

**Tags:** File Type Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Unique identifier for the policy rule |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | FileTypeRule |

## `PUT /fileTypeRules/{ruleId}`

Updates the File Type Control policy rule information for the specified ID

**Tags:** File Type Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Unique identifier for the policy rule |
| body | body | FileTypeRule | No | The File Type Control policy rule information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | FileTypeRule |

## Models
### AppSegment
Application Segment information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| externalId | integer (int64) | No | Indicates the external ID. Applicable only when this reference is of an external entity. |
| id | integer (int32) | No | A unique identifier assigned to the Application Segment |
| name | string | No | The name of the Application Segment |
| zpaTenantId | integer (int64) | No | ID of the ZPA tenant where the Application Segment is configured |

### CustomFileType
Custom file type information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| description | string | No | Additional information about the custom file type, if any. |
| extension | string | No | Specifies the file type extension. The maximum extension length is 10 characters. Existing Zscaler extensions cannot be added to custom file types. |
| fileTypeId | integer (int32) | No | File type ID. This ID is assigned and maintained for all file types including predefined and custom file types, and this value is different from the custom file type ID. |
| id | integer (int32) | No | Custom file type ID. This ID is assigned and maintained exclusively for custom file types, and this value is different from the file type ID (i.e., fileTypeId field). |
| name | string | No | Custom file type name |

### EntityReference
This is an immutable reference to an entity that mainly consists of id and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### FileTypeCategoryDTO
File type information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| id | integer (int64) | No | File type ID |
| name | string | No | File type description |
| parent | string | No | Parent category of the file type |

### FileTypeRule
File Type rule
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| accessControl | string | No | Access privilege of this rule based on the admin's RBA state. Ignored if the request is POST or PUT. |
| activeContent | boolean | No | Flag to check whether a file has active content or not |
| capturePCAP | boolean | No | Enable or disable Capture PCAP Settings |
| cloudApplications | array[PolicyWebApplication] | No | The list of cloud applications to which the File Type Control policy rule must be applied |
| departments | array[EntityReference] | No | Name-ID pairs of departments for which the rule is applied. If not set, the rule is applied for all departments. |
| description | string | No | Comments provided by the administrator |
| deviceGroups | array[EntityReference] | No | Name-ID pairs of device groups for which the rule is applied |
| deviceTrustLevels | array[string] | No | List of device trust levels for which the rule must be applied. While the High Trust, Medium Trust, or Low Trust evaluation is applicable only to Zscaler Client Connector traffic, Unknown evaluation applies to all traffic. The trust levels are assigned to the devices based on your [posture configurations](/client-connector/adding-zia-posture-profiles) in the Zscaler Client Connector Portal. If no value is set, this field  is ignored during the policy evaluation. |
| devices | array[EntityReference] | No | Name-ID pairs of device for which the rule is applied |
| fileTypeCategories | array[FileTypeCategoryDTO] | No | The list of file types to which the rule applies |
| fileTypes | array[string] | No | This field is replaced with **fileTypeCategories**. Zscaler recommends updating your API configurations to use the **fileTypeCategories** attribute in place of fileTypes. |
| filteringAction | string | No | Action taken when traffic matches policy. This field is not applicable to the Lite API. |
| groups | array[EntityReference] | No | Name-ID pairs of groups for which the policy must be applied. If not set, the policy is applied for all groups. |
| id | integer (int32) | No | System-generated identifier for a file type policy |
| labels | array[EntityReference] | No |  |
| lastModifiedBy | object | No | Admin user that last modified the rule. Ignored if the request is POST or PUT. |
| lastModifiedTime | integer (int32) | No | Timestamp when the rule was last modified. Ignored if the request is POST or PUT. |
| locationGroups | array[EntityReference] | No | Name-ID pairs of locations groups for which rule must be applied. |
| locations | array[EntityReference] | No | Name-ID pairs of locations for which the policy must be applied. If not set, the policy is applied for all locations. |
| maxSize | integer (int32) | No | Maximum file size (in KB) used for evaluation of the FTP rule |
| minSize | integer (int32) | No | Minimum file size (in KB) used for evaluation of the FTP rule |
| name | string | No | Rule Name |
| operation | string | No | File operation performed. This field is not applicable to the Lite API. |
| order | integer (int32) | No | Order of policy execution with respect to other file type policies. Order N indicates N-th file type policy is evaluated. This field is not applicable to the Lite API. |
| passwordProtected | boolean | No | A Boolean field indicating whether the rule applies to password-protected files. This criterion is used in combination with the fileTypes criterion and is applicable only to specific file types such as 7-Zip, RAR, ZIP, ZIPx, PDF, password-protected Microsoft Office files, and other password-protected and encrypted files. So, when the passwordProtected field is set to true, only the applicable file types can be specified using the **fileTypes** field.
**Note**: Traffic is evaluated against this criterion only when uploading and downloading of password-protected files is allowed at the organization level via the Security Exceptions in the Malware Protection policy. |
| protocols | array[string] | No | Protocol for the given rule. This field is not applicable to the Lite API. |
| rank | integer (int32) | No | Admin rank. This field is not applicable to the Lite API. |
| sizeQuota | integer (int32) | No | Size quota in KB, beyond which the policy must be applied. If not set, size quota is not enforced. Ignored if action is BLOCK. |
| state | string | No | Administrative state of the policy. This field is not applicable to the Lite API. |
| timeQuota | integer (int32) | No | Time quota in minutes, after which the policy must be applied. If not set, no time quota is enforced. Ignored if action is BLOCK. |
| timeWindows | array[EntityReference] | No |  |
| unscannable | boolean | No | Flag to check whether a file is unscannable or not |
| urlCategories | array[UrlCategoryForPolicy] | No | List of URL categories for which the policy must be applied. If not set, the policy is applied for all URL categories. |
| users | array[EntityReference] | No | Name-ID pairs of users for which the policy must be applied. If not set, user criteria is not considered for policy enforcement. |
| zpaAppSegments | array[AppSegment] | No | List of Source IP Anchoring-enabled ZPA Application Segments for which this rule is applicable |

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
| mask | integer (int32) | No |  |
| name | string | No |  |
| urlSupercategory | string | No |  |
| userConfiguredName | string | No |  |
| val | integer (int32) | No |  |
