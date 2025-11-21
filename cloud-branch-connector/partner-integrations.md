# Partner Integrations
Source: https://help.zscaler.com/cloud-branch-connector/partner-integrations

## `GET /accountGroups`

Retrieves the details of AWS account groups with metadata. To learn more, see [About Amazon Web Services Account Groups](/cloud-branch-connector/about-amazon-web-services-account-groups).

**Tags:** Partner Integrations

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `POST /accountGroups`

Creates an AWS account group. You can create a maximum of 128 groups in each organization. To learn more, see [Adding an Amazon Web Services Account Group](/cloud-branch-connector/adding-amazon-web-services-account-group).

**Tags:** Partner Integrations
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `GET /accountGroups/count`

Retrieves the total number of AWS account groups.

**Tags:** Partner Integrations
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `GET /accountGroups/lite`

Retrieves the ID and name of all the AWS account groups. For additional details, use the `GET /accountGroups` method.

**Tags:** Partner Integrations
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `DELETE /accountGroups/{id}`

Removes a specific AWS account group based on the provided ID.

**Tags:** Partner Integrations

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer (int32) | Yes | The unique ID of the AWS account group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `GET /accountGroups/{id}`

Retrieves the specific AWS account group details based on the provided group ID.

**Tags:** Partner Integrations

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer (int32) | Yes | The ID of the AWS account group. |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `PUT /accountGroups/{id}`

Updates the existing AWS account group details based on the provided ID.

**Tags:** Partner Integrations

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer (int32) | Yes | The unique ID of the AWS account group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `GET /discoveryService/workloadDiscoverySettings`

Retrieves the workload discovery service settings.

**Tags:** Partner Integrations
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `PUT /discoveryService/{id}/permissions`

Verifies the specified AWS account permissions using the discovery role and external ID.

**Tags:** Partner Integrations

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer (int32) | Yes | The unique identifier for the AWS account. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `GET /publicCloudInfo`

Retrieves the list of AWS accounts with metadata. To learn more, see [About Amazon Web Services Accounts](/cloud-branch-connector/about-amazon-web-services-accounts).

**Tags:** Partner Integrations

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `POST /publicCloudInfo`

Creates a new AWS account with the provided account and region details. You can create a maximum of 512 accounts in each organization. To learn more, see [Adding an Amazon Web Services Account](/cloud-branch-connector/adding-amazon-web-services-account).

**Tags:** Partner Integrations
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `GET /publicCloudInfo/cloudFormationTemplate`

Retrieves the CloudFormation template URL. To learn more, see [Adding an Amazon Web Services Account](/cloud-branch-connector/adding-amazon-web-services-account).

**Tags:** Partner Integrations

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| awsAccountId | query | string | No | (Optional) The AWS account ID to customize the CloudFormation template URL. If an `awsAccountId` is provided, the URL is customized with account-specific values, or a generic template URL is returned. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `GET /publicCloudInfo/count`

Retrieves the total number of AWS accounts.

**Tags:** Partner Integrations
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `POST /publicCloudInfo/generateExternalId`

Creates an external ID for an AWS account.

**Tags:** Partner Integrations
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `GET /publicCloudInfo/lite`

Retrieves basic information about the AWS cloud accounts. For additional details, use the `GET /publicCloudInfo` method.

**Tags:** Partner Integrations

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| cloudType | query | string | No | The cloud type. The default and mandatory value is AWS. |
| search | query | string | No | The search string. |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Defaultresponse. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `GET /publicCloudInfo/supportedRegions`

Retrieves a list of AWS regions supported for  workload discovery settings (WDS).

**Tags:** Partner Integrations

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `DELETE /publicCloudInfo/{id}`

Removes a specific AWS account based on the provided ID.

**Tags:** Partner Integrations

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer (int32) | Yes | The unique ID of the AWS account. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `GET /publicCloudInfo/{id}`

Retrieves the existing AWS account details based on the provided ID.

**Tags:** Partner Integrations

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer (int32) | Yes | The unique ID of the AWS account. |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `PUT /publicCloudInfo/{id}`

Updates the existing AWS account details based on the provided ID.

**Tags:** Partner Integrations

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer (int32) | Yes | The unique ID of the AWS account. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `PUT /publicCloudInfo/{id}/changeState`

Enables or disables a specific AWS account in all regions based on the provided ID.

**Tags:** Partner Integrations

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer (int32) | Yes | The unique ID of the AWS account. |
| enable | query | boolean | No | Set `true` to enable the AWS account, and `false` to disable it. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |
