# Admin and Role Management
Source: https://help.zscaler.com/cloud-branch-connector/admin-and-role-management

## `GET /adminRoles`

Lists existing admin roles.

**Tags:** Admin and Role Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| includeAuditorRole | query | boolean | No | Include or exclude auditor role information in the list. |
| includePartnerRole | query | boolean | No | Include or exclude partner admin role information in the list. |
| includeApiRole | query | boolean | No | Include or exclude API role information in the list. |
| id | query | array[integer (int32)] | No | Include or exclude role ID information in the list. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |

## `POST /adminRoles`

Creates an admin role.

**Tags:** Admin and Role Management
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | default response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `DELETE /adminRoles/{roleId}`

Deletes the admin role specified by the role ID.

**Tags:** Admin and Role Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| roleId | path | integer (int32) | Yes | The unique identifier for the admin role. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | No Content |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |

## `PUT /adminRoles/{roleId}`

Updates the admin role specified by the role ID.

**Tags:** Admin and Role Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| roleId | path | integer (int32) | Yes | The unique identifier for the admin role. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |

## `GET /adminUsers`

Lists admin users.

**Tags:** Admin and Role Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| includeAuditorUsers | query | boolean | No | Include or exclude auditor user information in the list. |
| includeAdminUsers | query | boolean | No | Include or exclude admin user information in the list. |
| partnerType | query | string | No | Include or exclude partner type information in the list. |
| search | query | string | No | The search string used to partially match against an admin user's Login ID or Name. |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. The default size is 100; the maximum size is 1000. |
| version | query | integer (int32) | No | Specifies backed up admins from backup version. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |

## `POST /adminUsers`

Creates an admin user.

**Tags:** Admin and Role Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| associateWithExistingAdmin | query | boolean | No | Indicates whether to associate this admin with an existing admin. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |

## `DELETE /adminUsers/{userId}`

Deletes an admin user for the specified user ID.

**Tags:** Admin and Role Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| userId | path | integer (int32) | Yes | The unique identifier for the admin user. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | No Content |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |

## `GET /adminUsers/{userId}`

Gets the admin user specified by the user ID.

**Tags:** Admin and Role Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| userId | path | integer (int32) | Yes | The unique identifier for the admin user. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |

## `PUT /adminUsers/{userId}`

Updates admin user for the specified user ID.

**Tags:** Admin and Role Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| userId | path | integer (int32) | Yes | The unique identifier for the admin user. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |

## `POST /passwordChange`

Changes current password.

**Tags:** Admin and Role Management
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
