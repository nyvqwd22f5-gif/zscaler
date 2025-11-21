# Users
Source: https://help.zscaler.com/zidentity/users

## `GET /users`

Retrieves a list of users with optional query parameters for pagination and filtering.
To learn more, see [About Users](/zidentity/about-users).

**Tags:** Users

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| offset | query | integer (int32) | No | The starting point for pagination, with the number of records that can be skipped before fetching results. |
| limit | query | integer (int32) | No | The maximum number of records to return per request. Minimum: `0`, Maximum: `1000` |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request was successful, and a paginated list of users are returned. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `POST /users`

Creates a new user using the provided details.

**Tags:** Users
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 202 | The request has been accepted for processing, but processing has not yet completed. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `DELETE /users/{id}`

Deletes an existing user from the system by the provided user `ID`.

**Tags:** Users

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | Unique identifier of the user to be deleted. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | The user was successfully deleted.
No content is returned in the response, but headers may be useful for validation purposes. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `GET /users/{id}`

Retrieves detailed information about a specific user using the provided user `ID`.

**Tags:** Users

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | Unique identifier of the user to retrieve. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request was successful, and the user details are returned. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `PUT /users/{id}`

Updates the details of an existing user based on the provided user `ID`.

**Tags:** Users

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | Unique identifier of the user that needs to be updated. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request was successful, and the user details are updated. |  |
| 500 | Unexpected server issue occurred while processing the request. |  |

## `GET /users/{id}/admin-entitlements`

Retrieves the administrative entitlements for a specific user by their user `ID`.

**Tags:** Users

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | The user `ID` of the individual whose admin entitlements are being retrieved. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request was successful, and returns a list of administrative entitlement objects. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `GET /users/{id}/groups`

Retrieves a paginated list of groups associated with a specific user `ID`.

**Tags:** Users

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| offset | query | integer (int32) | No | The starting point for pagination, with the number of records that can be skipped before fetching results. |
| limit | query | integer (int32) | No | The maximum number of records to return per request. Minimum: `0`, Maximum: `1000` |
| id | path | string | Yes | The user `ID` of the individual whose groups details are to be retrieved. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request was successful, and returns a paginated list of groups for the specified user. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `GET /users/{id}/service-entitlements`

Retrieves service entitlements for a specified user `ID`.

**Tags:** Users

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | The user `ID` of the individual for whom the service entitlements are to be retrieved. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request was successful, and returns the service entitlements for the user. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `POST /users/{id}:resetpassword`

Initiates a password reset for a specific user `ID`

**Tags:** Users

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | The user `ID` of the user for whom the password is to be reset. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The password reset request has been initiated successfully. |  |
| 400 | The request could not be processed due to invalid syntax or missing required fields. |  |

## `POST /users/{id}:setskipmfa`

Sets a flag to skip Multi-Factor Authentication (MFA) for a specified user `ID`.

**Tags:** Users

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | The user `ID` of the individual for whom the MFA needs to be skipped. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request was successful, and MFA skip has been set. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `PUT /users/{id}:updatepassword`

Updates the password for a specific user `ID`. Optionally, a boolean flag can be set to require the user to reset their password during next login.

**Tags:** Users

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | The user `ID` of the individual for whom the password needs to be updated. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request was successful, and the password has been reset. |  |
| 400 | The request could not be processed due to invalid syntax or missing required fields. |  |
