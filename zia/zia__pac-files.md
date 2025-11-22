# PAC Files
Source: https://help.zscaler.com/zia/pac-files

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /pacFiles`

Retrieves the list of all PAC files which are in deployed state. This list includes default and [custom PAC files](/zia/using-custom-pac-file-forward-traffic-zia). To learn more, see [About Hosted PAC Files](/zia/about-hosted-pac-files).

**Tags:** PAC Files
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | Returns PAC files with the names that match the search criteria |
| filter | query | string | No | Retrieves the list of PAC files without the PAC file content in the response |
| page | query | integer | No | Specifies the page offset |
| pageSize | query | integer | No | Specifies the page size. The default size is 100. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[Pac] |

## `POST /pacFiles`

Adds a new custom PAC file. To learn more about PAC file configuration, see [Using Custom PAC Files to Forward Traffic to ZIA](/zia/using-custom-pac-file-forward-traffic-zia) and [Writing a PAC File](/zia/writing-pac-file).
**Note**: Before adding a new PAC file, you can validate the content of the PAC file by sending a POST request to `/pacFiles/validate`. This request only adds a PAC file. The PAC file needs to be transitioned to the **Deploy** state in order for the file to be deployed.

**Tags:** PAC Files
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | Pac | Yes | PAC object that defines PAC file to be created |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Pac |

## `POST /pacFiles/validate`

Sends the PAC file content for validation and returns the validation result. To learn more, see [Using Custom PAC Files to Forward Traffic to ZIA](/zia/using-custom-pac-file-forward-traffic-zia).

**Tags:** PAC Files
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | string | Yes | PAC file content |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | PacResult |

## `DELETE /pacFiles/{pacId}`

Deletes an existing PAC file including all of its versions based on the specified ID

**Tags:** PAC Files
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| pacId | path | integer | Yes | Specifies the ID of the PAC file |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /pacFiles/{pacId}/version`

Retrieves all versions of a PAC file based on the specified ID

**Tags:** PAC Files
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| pacId | path | integer | Yes | Specifies the ID of the PAC file |
| filter | query | string | No | Excludes specific information about the PAC file from the response such as the PAC file content |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[Pac] |

## `POST /pacFiles/{pacId}/version/{clonedPacVersion}`

Adds a new PAC file version by branching an existing version based on the specified ID. To learn more, see [Using Custom PAC Files to Forward Traffic to ZIA](/zia/using-custom-pac-file-forward-traffic-zia).

**Tags:** PAC Files
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| pacId | path | integer | Yes | Specifies the ID of the PAC file for which a new version needs to be created |
| clonedPacVersion | path | integer | Yes | Specifies the PAC file version that needs to be branched |
| deleteVersion | query | integer | No | Currently, only 10 versions of a PAC file are supported. If this limit is reached and if you are adding a new version using the `POST /pacFiles/{pacId}/version/{clonedPacVersion}` endpoint, the **deleteVersion** parameter can be used to specify the PAC file version that must be replaced with the new version created using this request. However, if the limit is reached and if a version is not specified using this parameter, the version with the least number is automatically replaced. If the limit is not reached, this parameter is ignored. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Pac |

## `GET /pacFiles/{pacId}/version/{pacVersion}`

Retrieves a specific version of a PAC file based on the specified ID

**Tags:** PAC Files
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| pacId | path | integer | Yes | Specifies the ID of the PAC file |
| pacVersion | path | integer | Yes | Specifies the version of the PAC file |
| filter | query | string | No | Excludes specific information about the PAC file from the response such as the PAC file content |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Pac |

## `PUT /pacFiles/{pacId}/version/{pacVersion}/action/{pacVersionAction}`

Performs the specified action on the PAC file version and updates the file status. Supported actions include deploying, staging, unstaging, and marking or unmarking the file as last known good version can be performed on PAC file versions.

**Tags:** PAC Files
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| pacId | path | integer | Yes | Specifies the ID of the PAC file |
| pacVersion | path | integer | Yes | Specifies the version of the PAC file |
| pacVersionAction | path | string | Yes | Specifies the action that must be performed on the PAC file version |
| newLKGVer | query | integer | No | If you are removing a PAC file version as the last known good version using this request, you need to specify a different version that can be marked as the last known good version. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Pac |

## Models
### EntityReference
This is an immutable reference to an entity that mainly consists of id and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### Pac
Information about the PAC file along with the PAC file content. To learn more, see [Writing a PAC File](/zia/writing-pac-file).
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| createTime | integer (int32) | No | The timestamp when the PAC file was created. This value is represented in Unix time. |
| description | string | No | The description of the PAC file |
| domain | string | No | The domain of your organization to which the PAC file applies |
| editable | boolean | No | Indicates whether the PAC file is editable
**Note**: The Zscaler service provides default PAC files, and admins with sufficient permissions and scope can additionally create and manage their own custom PAC files. To learn more, see  [Using Default PAC Files to Forward Traffic to ZIA](/zia/using-default-pac-files-forward-traffic-zia) and [Using Custom PAC Files to Forward Traffic to ZIA](/zia/using-custom-pac-file-forward-traffic-zia). This field is read-only. |
| id | integer (int32) | No | The unique identifier for the PAC file |
| lastModificationTime | integer (int32) | No | The timestamp when the PAC file was last modified. This value is represented in Unix time. |
| lastModifiedBy | EntityReference | No | The username of the admin who last modified the PAC file |
| name | string | No | The name of the PAC file |
| pacCommitMessage | string | No | The commit message entered while saving the PAC file version as indicated by the pacVersion field |
| pacContent | string | No | The content of the PAC file. To learn more, see [Writing a PAC File](/zia/writing-pac-file). |
| pacSubURL | string | No | Obfuscated domain name of the organization to which this PAC file applies |
| pacUrl | string | No | The URL location of the PAC file that is auto-generated when the PAC file is added for the first time.
**Note**: This value is not required in POST and PUT requests and the value is ignored if present. |
| pacUrlObfuscated | boolean | No | A Boolean value that indicates whether the PAC file URL is obfuscated. If this value is true, the obfuscated URL is returned in the **pacSubURL** field. |
| pacVerificationStatus | string | No | Indicates the verification status of the PAC file and if any errors are identified in the syntax |
| pacVersion | integer (int32) | No | The version number of the PAC file |
| pacVersionStatus | string | No | Indicates the status of a specific version of a PAC file as whether it is deployed, staged for deployment, or is marked as the last known good version. |
| totalHits | integer (int64) | No | The number of times the PAC file was used during the last 30 days |

### PacResult
Results of PAC file validation
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| errorCount | integer (int32) | No | The number of errors present in the list of **messages** |
| messages | array[PacValidationMessage] | No | The list of errors and warnings generated as a result of the PAC file validation |
| success | boolean | No | A Boolean value indicating whether the PAC file validation was successful or not |
| warningCount | integer (int32) | No | The number of warnings present in the list of **messages** |

### PacValidationMessage
Information about the PAC file validation results
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| column | integer (int32) | No | Designates the number of the first column to which the messages applies |
| endColumn | integer (int32) | No | Designates the number of the last column to which the messages applies |
| endLine | integer (int32) | No | Designates the number of the last line to which the messages applies |
| fatal | boolean | No | A Boolean value indicating the PAC file validation completion status. A true value is returned when validation is not completed. |
| line | integer (int32) | No | Designates the number of the first line to which the messages applies |
| message | string | No | The message string |
| severity | integer (int32) | No | Indicates the severity of the message. A value of 1 indicates a warning, whereas a value of 2 indicates an error. |
