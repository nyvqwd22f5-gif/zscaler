# Resource Servers
Source: https://help.zscaler.com/zidentity/resource-servers

## `GET /resource-servers`

Retrieves a paginated list of resource servers with an optional query parameters for pagination.
To learn more, see [Viewing API Resources](/zidentity/viewing-api-resources).

**Tags:** Resource Servers

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| offset | query | integer (int32) | No | The starting point for pagination, with the number of records that can be skipped before fetching results. |
| limit | query | integer (int32) | No | The maximum number of records to return per request. Minimum: `0`, Maximum: `1000` |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request was successful, and a paginated list of resource servers are returned. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `GET /resource-servers/{id}`

Retrieves details about a specific resource server using the server `ID`.

**Tags:** Resource Servers

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | Unique identifier of the resource server to retrieve. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request was successful, and the resource server details are returned. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |
