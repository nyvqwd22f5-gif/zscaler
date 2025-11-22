# Groups
Source: https://help.zscaler.com/zidentity/groups

## `GET /groups`

Retrieves a paginated list of groups with optional query parameters for pagination and filtering by group name or dynamic group status.
To learn more, see [About User Groups](/zidentity/about-user-groups).

**Tags:** Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| offset | query | integer (int32) | No | The starting point for pagination, with the number of records that can be skipped before fetching results. |
| limit | query | integer (int32) | No | The maximum number of records to return per request. Minimum: `0`, Maximum: `1000` |
|  |  |  | No |  |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request was successful, and a paginated list of groups are returned. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `POST /groups`

Creates a new group with the specified name and description.

**Tags:** Groups
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 201 | The request was successful, and a new group has been created. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `DELETE /groups/{id}`

Deletes an existing group based on the provided group `ID`.

**Tags:** Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | The unique identifier of the group to be deleted. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | The group was successfully deleted.
No content is returned in the response, but headers may be useful for validation purposes. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `GET /groups/{id}`

Retrieves detailed information about a specific group using its unique identifier `ID`.

**Tags:** Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | Unique identifier of the group to retrieve. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request was successful, and the group details are returned. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `PUT /groups/{id}`

Update an existing group based on the provided group `ID`.

**Tags:** Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | Unique identifier of the group to be updated. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request has succeeded, and the group details have been updated. |  |
| 500 | Unexpected server issue occurred while processing the request. |  |

## `GET /groups/{id}/users`

Retrieves the list of users details for a specific group using the group `ID`.

**Tags:** Groups

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
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request was successful, and a paginated list of users details are returned. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `POST /groups/{id}/users`

Adds users to an existing group using the unique identifier `ID` of the group.

**Tags:** Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | Unique identifier of the group to which users will be added. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request was successful, and users have been added to the group. |  |
| 400 | The request contains invalid syntax or missing required fields. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `PUT /groups/{id}/users`

Replaces the list of users in a specific group using the group `ID`.
**NOTE:** This operation completely replaces all existing users in the group.

**Tags:** Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | Unique identifier of the group which users needs to be updated. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request has succeeded. All existing users in the group have been replaced. |  |
| 400 | The request could not be processed due to invalid syntax or missing required fields. |  |

## `DELETE /groups/{id}/users/{userId}`

Removes a specific user from an existing group using the group `ID` and the user `ID`.

**Tags:** Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | Unique identifier of the group from which the user needs to be removed. |
| userId | path | string | Yes | Unique identifier of the user to be removed from the group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | The user has been removed from the group.
No content is returned in the response, but headers may be useful for validation purposes. |  |
| 400 | The request could not be processed due to invalid syntax or missing required fields. |  |
| 401 | Authentication failed or missing authorization credentials.
The request requires a valid Bearer token. However, either no token was provided, or the provided token is invalid or expired. |  |

## `POST /groups/{id}/users/{userId}`

Adds a specific user to an existing group using the group `ID` and the user `ID`.

**Tags:** Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | Unique identifier of the group to which the user needs to be added. |
| userId | path | string | Yes | Unique identifier of the user being added to the group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The request was successful, and the user has been added to the group |  |
| 400 | The request could not be processed due to invalid syntax or missing required fields. |  |
