# User Management
Source: https://help.zscaler.com/zia/user-management

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /departments`

Retrieves a list of departments. The search parameters find matching values within the `name` or `comments` fields.

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | The search string used to match against a department's name or comments attributes |
| page | query | integer | No | Specifies the page offset |
| limitSearch | query | boolean | No | Limits the search to match only against the department name |
| pageSize | query | integer | No | Specifies the page size |
| sortBy | query | string | No | Sorts the departments based on available values |
| sortOrder | query | string | No | Sorts the order of departments based on available values |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[Department] |

## `POST /departments`

Adds a department for an organization. To learn more, see [Adding Departments](/zia/adding-departments).
**Note**: This endpoint is accessible via [Zscaler OneAPI](/oneapi/understanding-oneapi) only.

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | Department | No | Department information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Department |

## `GET /departments/lite`

Retrieves a list of departments. The search parameters find matching values within the `name` or `comments` fields.

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | The search string used to match against a department's name or comments attributes |
| id | query | array | No | Department ID |
| includeDefaultDept | query | boolean | No | Specifies whether to include the default department for a user |
| page | query | integer | No | Specifies the page offset |
| pageSize | query | integer | No | Specifies the page size |
| sortBy | query | string | No | Sorts the departments based on available values |
| sortOrder | query | string | No | Sorts the order of departments based on available values |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Department |

## `GET /departments/lite/{id}`

Retrieves the department based on the specified ID

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer | Yes | Unique identifier for the department |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Department |

## `DELETE /departments/{departmentId}`

Deletes a department for an organization based on the specified ID.
**Note**: This endpoint is accessible via [Zscaler OneAPI](/oneapi/understanding-oneapi) only.

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| departmentId | path | integer | Yes | Department ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `PUT /departments/{departmentId}`

Updates the department for an organization based on the specified ID.
**Note**: This endpoint is accessible via [Zscaler OneAPI](/oneapi/understanding-oneapi) only.

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| departmentId | path | integer | Yes | Department ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Department |

## `GET /departments/{id}`

Retrieves the department based on the specified ID

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer | Yes | Unique identifier for the department |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Department |

## `GET /groups`

Retrieves a list of groups. The search parameters find matching values in the `name` or `comments` attributes.

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | The search string used to match against a group's name or comments attributes |
| definedBy | query | string | No | The string value defined by the group name or other applicable attributes |
| page | query | integer | No | Specifies the page offset |
| pageSize | query | integer | No | Specifies the page size |
| sortBy | query | string | No | Sorts the groups based on available values |
| sortOrder | query | string | No | Sorts the order of groups based on available values |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[Group] |

## `POST /groups`

Adds a new group. To learn more, see [Adding Groups](/zia/adding-groups).
**Note**: This endpoint is accessible via [Zscaler OneAPI](/oneapi/understanding-oneapi) only.

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | Group | No | Group information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Group |
| 201 | Group created successfully |  |
| 401 | Unauthorized access |  |
| 403 | Forbidden access |  |

## `GET /groups/lite`

Retrieves a list of group names. The search parameters find matching values in the `name` or `comments` attributes.

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | The search string used to match against a group's name or comments attributes |
| definedBy | query | string | No | The string value defined by the group name |
| page | query | integer | No | Specifies the page offset |
| pageSize | query | integer | No | Specifies the page size |
| sortBy | query | string | No | Sorts the group names based on available values |
| sortOrder | query | string | No | Sorts the order of group names based on available values |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Group |

## `GET /groups/lite/{groupId}`

Retrieves the group based on the specified ID

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| groupId | path | integer | Yes | Group ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Group |

## `DELETE /groups/{groupId}`

Deletes the group based on the specified ID.
**Note**: This endpoint is accessible via [Zscaler OneAPI](/oneapi/understanding-oneapi) only.

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| groupId | path | integer | Yes | Group ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | Group deleted successfully |  |
| 403 | User does not have the required permissions |  |
| 404 | Group not found |  |

## `GET /groups/{groupId}`

Retrieves the group based on the specified ID

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| groupId | path | integer | Yes | Group ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Group |

## `PUT /groups/{groupId}`

Updates an existing group based on the specified ID.
**Note**: This endpoint is accessible via [Zscaler OneAPI](/oneapi/understanding-oneapi) only.

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| groupId | path | integer | Yes | Group ID |
| body | body | Group | No | Group information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Group updated successfully | Group |
| 400 | Invalid request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 500 | Internal server error |  |

## `GET /users`

Gets a list of all users and allows user filtering by name, department, or group. The `name` search parameter performs a partial match. The `dept` and `group` parameters perform a 'starts with' match.

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| name | query | string | No | Filters by user name. |
| dept | query | string | No | Filters by department name. |
| group | query | string | No | Filters by group name. |
| page | query | integer | No | Specifies the page offset. |
| pageSize | query | integer | No | Specifies the page size. The default size is 100 and the maximum size is 10,000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[User] |

## `POST /users`

Adds a new user. A user can belong to multiple groups, but can only belong to one department.

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| user | body | User | No | User information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | User |

## `GET /users/auditors`

Gets a list of auditors. To learn more, see [About Auditors](/zia/about-auditors).

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[User] |

## `POST /users/bulkDelete`

Bulk delete users up to a maximum of 500 users per request. The response returns the user IDs that were successfully deleted.

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| userIds | body | IdListInteger | No | The user IDs to bulk delete. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | IdList |

## `GET /users/references`

Gets the list of Name-ID pairs for all users in the ZIA Admin Portal that can be referenced in user criteria within policies. Users can be filtered by name and the `name` search parameter performs a partial match. Administrators can be optionally included in the list by using the `includeAdminUsers` parameter.

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| name | query | string | No | Filters by user name |
| includeAdminUsers | query | boolean | No | Specifies whether to include the administrator users when retrieving the list |
| page | query | integer | No | Specifies the page offset |
| pageSize | query | integer | No | Specifies the page size. The default size is 1 and the maximum size is 100. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[EntityReference] |

## `DELETE /users/{userId}`

Deletes the user for the specified ID.

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| userId | path | integer | Yes | The unique identifer for the user. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |

## `GET /users/{userId}`

Gets the user information for the specified ID.

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| userId | path | integer | Yes | The unique identifer for the user. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | User |

## `PUT /users/{userId}`

Updates the user information for the specified ID. However, the `email` attribute is read-only.

**Tags:** User Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| userId | path | integer | Yes | The unique identifer for the user. |
| user | body | User | No | User information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | User |

## Models
### Department
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| comments | string | No | Additional information about this department. This field is not applicable to the Lite API. |
| deleted | boolean | No | List of deleted departments |
| id | integer (int32) | No | Department ID |
| idpId | integer (int64) | No | Identity provider (IdP) ID. This field is not applicable to the Lite API. |
| name | string | Yes | Department name |

### EntityReference
This is an immutable reference to an entity that mainly consists of id and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### Group
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| comments | string | No | Additional information about the  group |
| id | integer (int32) | Yes | Unique identifier for the group |
| idpId | integer (int64) | No | Unique identifier for the identity provider (IdP) |
| isSystemDefined | boolean | No | System-defined group |
| name | string | Yes | Group name |

### IdList
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| ids | array[object] | No |  |

### IdListInteger
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| ids | array[integer (int32)] | No |  |

### User
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| adminUser | boolean | No | True if this user is an Admin user |
| comments | string | No | Additional information about this user. |
| department | object | Yes | Department a user belongs to |
| email | string | Yes | User email consists of a user name and domain name. It does not have to be a valid email address, but it must be unique and its domain must belong to the organization.
**Note**: The email field allows values of alphanumeric characters and certain special characters up to a maximum of 127 characters. The use of the `@` symbol is mandatory. This field corresponds to the User ID (also referred to as Login ID) field in the UI. However, the data validation in the UI uses different constraints. |
| groups | array[Group] | Yes | List of Groups a user belongs to. Groups are used in policies. |
| id | integer (int32) | No | User ID |
| name | string | Yes | User name. This appears when choosing users for policies.
**Note**: The name field allows values containing UTF-8 characters up to a maximum of 127 characters. |
| password | string | Yes | User's password. Applicable only when authentication type is Hosted DB. Password strength must follow what is defined in the auth settings. |
| tempAuthEmail | string | No | Temporary Authentication Email. If you enabled one-time tokens or links, enter the email address to which the Zscaler service sends the tokens or links. If this is empty, the service sends the email to the User email. |
| type | string | No | User type. Provided only if this user is not an end user. |
