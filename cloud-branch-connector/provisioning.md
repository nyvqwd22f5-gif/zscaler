# Provisioning
Source: https://help.zscaler.com/cloud-branch-connector/provisioning

## `GET /apiKeys`

Lists available API keys.

**Tags:** Provisioning

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| includePartnerKey | query | boolean | No | Include or exclude partner keys from the list. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |

## `POST /apiKeys/{keyId}/regenerate`

Regenerates an API key.

**Tags:** Provisioning

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| keyId | path | integer (int32) | Yes | The API key ID of the API key you want to regenerate. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |

## `GET /provUrl`

Lists provisioning templates.

**Tags:** Provisioning

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. The default size is 250. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | default response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `GET /provUrl/{id}`

Gets a provisioning template by ID.

**Tags:** Provisioning

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer (int32) | Yes | ID of provisioning template. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | default response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `GET /publicCloudAccountDetails`

Lists public cloud account information.

**Tags:** Provisioning

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. The default size is 250. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | default response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `GET /publicCloudAccountDetails/lite`

Lists a subset of public (Cloud Connector) cloud account information.

**Tags:** Provisioning

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. The default size is 250. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | default response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `GET /publicCloudAccountDetails/{id}`

Gets the public (Cloud Connector) cloud account information for the specified ID.

**Tags:** Provisioning

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. The default size is 250. |
| id | path | integer (int32) | Yes | ID of the public cloud account. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | default response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `GET /publicCloudAccountIdStatus`

Lists public (Cloud Connector) cloud account status information (enabled/disabled).

**Tags:** Provisioning
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | default response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `PUT /publicCloudAccountIdStatus`

Enables/disables public (Cloud Connector) cloud account status.

**Tags:** Provisioning
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | default response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |
