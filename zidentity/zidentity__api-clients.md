# API Clients
Source: https://help.zscaler.com/zidentity/api-clients

## `GET /api-clients`

Retrieves a paginated list of API clients, providing details such as total records, current page offset, and links for pagination navigation.
To learn more, see [About API Clients](/zidentity/about-api-clients).

**Tags:** API Clients

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| offset | query | integer (int32) | No | The starting point for pagination, with the number of records that can be skipped before fetching results. |
| limit | query | integer (int32) | No | The maximum number of records to return per request. Minimum: `0`, Maximum: `1000` |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request was successful, and a paginated list of API clients is returned. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `POST /api-clients`

Creates a new API client with authentication settings and assigned roles.

**Tags:** API Clients
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 201 | The request has succeeded and a new resource has been created as a result. |  |
| 202 | The request has been accepted for processing, but processing has not yet completed. |  |
| 400 | The server could not understand the request due to invalid syntax. |  |

## `DELETE /api-clients/{id}`

Removes an existing API client from the system. After deletion, the API client cannot be recovered.

**Tags:** API Clients

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | Unique identifier of the API client to be deleted. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | The API client was successfully deleted.
No content is returned in the response, but headers may be useful for validation purposes. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `GET /api-clients/{id}`

Retrieves detailed information about a specific API client using its `ID`.

**Tags:** API Clients

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | Unique identifier of the API client to be retrieved. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request was successful, and the API client details are returned. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `PUT /api-clients/{id}`

Updates the existing API client details based on the provided `ID`. This allows modification of attributes such as name, authentication settings, and assigned roles.

**Tags:** API Clients

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | Unique identifier of the API client to be updated. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request was successful, and the API client details are updated. |  |
| 500 | Unexpected server issue occurred while processing the request. |  |

## `GET /api-clients/{id}/secrets`

Retrieves a list of secrets associated with a specific API client using its `ID`.
**NOTE:**
- Secret values in the response are masked to prevent exposure of sensitive information.
- This API is applicable only when the authentication type is **SECRET**.

**Tags:** API Clients

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | The API client `ID` to retrieve the client secrets. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request was successful, and a list of secrets is returned. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `POST /api-clients/{id}/secrets`

Creates and associates a new secret with a specified API client `ID`. This secret can be used for authentication with ZIdentity.
**NOTE:** This API is applicable only when the authentication type is **SECRET**.

**Tags:** API Clients

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | Unique identifier of the API client to which the secret is added. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 201 | The request was successful, and a new secret has been created and associated with the API client. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `DELETE /api-clients/{id}/secrets/{secretsId}`

Removes a specific secret associated with an API client using the Client ID and secret ID. After deletion, the secret cannot be recovered.

**Tags:** API Clients

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | Unique identifier of the API client. |
| secretsId | path | string | Yes | Unique identifier of the secret to be deleted. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | The secret was successfully deleted.
No content is returned in the response, but may be useful for validation purposes. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |
