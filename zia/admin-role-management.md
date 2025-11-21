# Admin & Role Management
Source: https://help.zscaler.com/zia/admin-role-management

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /adminRoles`

Retrieves a list of all admin roles. To learn more, see [About Role Management](/zia/about-role-management).

**Tags:** Admin & Role Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| includeAuditorRole | query | boolean | No | Includes or excludes the auditor role information in the list |
| includePartnerRole | query | boolean | No | Includes or excludes the partner admin role information in the list |
| includeApiRole | query | boolean | No | Includes or excludes the API role information in the list |
| id | query | array | No | Specifies the admin role login ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AdminRole |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 500 | Internal Server Error |  |

## `POST /adminRoles`

Adds an admin role. To learn more, see [Adding Admin Roles](/zia/adding-admin-roles).
**Note**: This endpoint is accessible via [Zscaler OneAPI](/oneapi/understanding-oneapi) only.

**Tags:** Admin & Role Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | AdminRole | No | Admin role information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AdminRole |
| 201 | Created | AdminRole |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 500 | Internal Server Error |  |

## `GET /adminRoles/lite`

Retrieves a name and ID dictionary of all admin roles. The list only includes the name and ID for all admin roles. To learn more, see [About Role Management](/zia/about-role-management).

**Tags:** Admin & Role Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| includeAuditorRole | query | boolean | No | Includes or excludes the auditor role information in the list |
| includePartnerRole | query | boolean | No | Includes or excludes the partner admin role information in the list |
| includeApiRole | query | boolean | No | Includes or excludes the API role information in the list |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AdminRole |

## `DELETE /adminRoles/{roleId}`

Deletes the admin role based on the specified ID.
**Note**: This endpoint is accessible via [Zscaler OneAPI](/oneapi/understanding-oneapi) only.

**Tags:** Admin & Role Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| roleId | path | integer | Yes | Specifies the role ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | No Content |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 500 | Internal Server Error |  |

## `GET /adminRoles/{roleId}`

Retrieves the admin role based on the specified ID

**Tags:** Admin & Role Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| roleId | path | integer | Yes | Specifies the role ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AdminRole |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 500 | Internal Server Error |  |

## `PUT /adminRoles/{roleId}`

Updates the admin role based on the specified ID.
**Note**: This endpoint is accessible via [Zscaler OneAPI](/oneapi/understanding-oneapi) only.

**Tags:** Admin & Role Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| roleId | path | integer | Yes | Specifies the role ID |
| body | body | AdminRole | No | Admin role information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AdminRole |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 500 | Internal Server Error |  |

## `GET /adminUsers`

Gets a list of admin users. By default, auditor user information is not included. To learn more, see [About Administrators](/zia/about-administrators) and [About Auditors](/zia/about-auditors).

**Tags:** Admin & Role Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| includeAuditorUsers | query | boolean | No | Include or exclude auditor user information in the list. |
| includeAdminUsers | query | boolean | No | Include or exclude admin user information in the list. |
| search | query | string | No | The search string used to partially match against an admin/auditor user's Login ID or Name. |
| page | query | integer | No | Specifies the page offset. |
| pageSize | query | integer | No | Specifies the page size. The default size is 100, but the maximum size is 1000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AdminUser |

## `POST /adminUsers`

Creates an admin or auditor user. To learn more, see [Adding Admins](/zia/adding-admins) and [Adding Auditors](/zia/adding-auditors).

**Tags:** Admin & Role Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | AdminUser | No |  |
| associateWithExistingAdmin | query | boolean | No | This field is set to true to update an admin user that already exists in other Zscaler services but does not exist in ZIA. For example, this field must be set to true when creating an admin user in ZIA who's already a user in Zscaler Digital Experience (ZDX). To learn more, see [Adding ZIA Admins](/zia/adding-zia-admins). |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AdminUser |

## `GET /adminUsers/me`

Retrieves information about the current administrator or auditor user, or both.

**Tags:** Admin & Role Management
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AdminUser |

## `DELETE /adminUsers/{userId}`

Deletes an admin or auditor user using the specified ID
**Note**: This request deletes an admin and removes them as a user from the ZIA Admin Portal. To delete the admin privileges for a user while retaining them as a regular user of your organization in the ZIA Admin Portal, use the `POST /adminUsers/{userId}/convertToUser` request.
**Sample Request (Python)**import http.client
import json
conn = http.client.HTTPSConnection("HOSTNAME")
headers = {
'content-type': "application/json",
'cache-control': "no-cache",
'cookie': "JSESSIONID=xxxxxxx"
}
conn.request("DELETE", "/api/v1/adminUsers/6794036", headers=headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
**Sample Response**204 No Content

**Tags:** Admin & Role Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| userId | path | integer | Yes | The unique identifier for the admin/auditor user. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | Successful Operation |  |

## `PUT /adminUsers/{userId}`

Updates admin or auditor user for the specified ID. You can only disable/enable the [default admin account](/zia/about-administrators) using this endpoint, all other updates within the request are ignored for this admin account.

**Tags:** Admin & Role Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| userId | path | integer | Yes | The unique identifier for the admin/auditor user. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AdminUser |

## `POST /adminUsers/{userId}/convertToUser`

Removes admin privileges for a user while retaining them as a regular user of your organization in the ZIA Admin Portal. This can be used as an alternative to the `DELETE /adminUsers/{userId}` request, which deletes an admin and removes them as a user from the ZIA Admin Portal. To learn more, see [Deleting ZIA Admins](/zia/deleting-zia-admins).
Before you can delete the admin privileges for a user, you need to obtain the admin user's ID and other information by using the `GET /users` request and then send the admin user details in the `POST /adminUsers/{userId}/convertToUser` request.

**Tags:** Admin & Role Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| userId | path | integer | Yes | The unique identifier of the admin user |
| body | body | User | No | Information about the user for whom the admin privileges must be removed. Group information is mandatory in the request Body. Optionally, you can include other field information to modify the values. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | User |

## `GET /passwordExpiry/settings`

Retrieves the password expiration information for all the admins

**Tags:** Admin & Role Management
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | PasswordExpirySettings |

## `PUT /passwordExpiry/settings`

Updates the password expiration information for all the admins. To learn more, see [Configuring Password Expiration](/zia/configuring-password-expiration).

**Tags:** Admin & Role Management
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | PasswordExpirySettings |

## Models
### AdminRole
Specifies an admin's level of access to the ZIA Admin Portal
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| adminAcctAccess | string | No | Admin and role management access permission |
| alertingAccess | string | No | Alerting access permission |
| analysisAccess | string | No | Insights Logs access permission |
| dashboardAccess | string | No | Dashboard access permission |
| deviceInfoAccess | string | No | Device information access permission. When set to NONE, device information is obfuscated. |
| extFeaturePermissions | object | No | External feature access permission. Indicates whether an admin role has full or restricted access to external features. When set to NONE, the admin role does not have permission to access any external features. |
| featurePermissions | object | No | Feature access permission. Indicates which features an admin role can access and if the admin has both read and write access, or read-only access. |
| id | integer (int32) | No | Admin role ID |
| isAuditor | boolean | No | Indicates whether this is an auditor role |
| isNonEditable | boolean | No | Indicates whether or not this admin user is editable |
| logsLimit | string | No | Enter the number of days an admin with this role can view logs. Admins can view real-time logs of every transaction performed by your users regardless of where they are in the world. |
| name | string | Yes | Name of the admin role |
| permissions | array[string] | No | List of functional areas to which this role has access. This attribute is subject to change. |
| policyAccess | string | No | Policy access permission |
| rank | integer (int32) | No | Admin rank of this admin role. This is applicable only when the admin rank is enabled in the advanced settings. Default value is 7 (the lowest rank). The assigned admin rank determines the roles or admin users this user can manage and the rule orders the admin can access. |
| reportAccess | string | No | Report access permission |
| reportTimeDuration | integer (int32) | No | Time duration allocated to the report dashboard. The default value of -1 indicates that no time restriction is applied to the
report dashboard. Time Unit is in hours. |
| roleType | string | No | The admin role type. This attribute is subject to change. |
| usernameAccess | string | No | Username access permission. When set to NONE, the username is obfuscated. |

### AdminScope
An admin's scope can be limited to certain resources, policies, or reports. An admin's scope can be limited by LOCATION, LOCATION GROUP, or DEPARTMENT. If this is not specified, then the admin has an ORGANIZATION scope by default.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| ScopeEntities | array[EntityReference] | No | Based on the admin scope type, the entities can be the ID/name pair of departments, locations, or location groups. The attribute name is subject to change. |
| Type | string | No | The admin scope type. The attribute name is subject to change. |
| scopeGroupMemberEntities | array[EntityReference] | No | Only applicable for the LOCATION_GROUP admin scope type, in which case this attribute gives the list of ID/name pairs of locations within the location group. The attribute name is subject to change. |

### AdminUser
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| adminScope | object | No | The admin's scope. A scope is required for the admins, but not applicable to auditors. This attribute is subject to change. |
| comments | string | No | Additional information about the admin or auditor |
| disabled | boolean | No | Indicates whether or not the admin account is disabled |
| email | string | Yes | Admin or auditor's email address |
| execMobileAppTokens | array[MobileAppTokenInfo] | No | Read-only information about the Executive Insights App token, if it exists. |
| id | integer (int32) | No | Admin or auditor's user ID |
| isAuditor | boolean | No | Indicates whether the user is an auditor. This attribute is subject to change. |
| isExecMobileAppEnabled | boolean | No | Indicates whether or not the Executive Insights App access is enabled for the admin |
| isNonEditable | boolean | No | Indicates whether or not the admin can be edited or deleted |
| isPasswordExpired | boolean | No | Indicates whether or not an admin's password has expired |
| isPasswordLoginAllowed | boolean | No | The default value is true when SAML Authentication is disabled. When SAML Authentication is enabled, this can be set to false to force the admin to log in via SSO only. |
| isProductUpdateCommEnabled | boolean | No | Enables or disables communication regarding product updates. Enable if you want the admin to receive communication regarding important changes and updates for the Zscaler service. |
| isSecurityReportCommEnabled | boolean | No | Enables or disables communication regarding security updates. Enable this to receive the latest information on vulnerabilities and threats that might affect your organization. |
| isServiceUpdateCommEnabled | boolean | No | Enables or disables communication regarding service updates. Enable this to receive new Zscaler service and product enhancements, including new data center notification and cloud release information. |
| loginName | string | Yes | Admin or auditor's login name. The login name is in email format and uses the domain name associated with the Zscaler account. |
| newLocationCreateAllowed | boolean | No | Determines if the user is allowed to create a new location |
| password | string | No | The admin's password. If the single sign-on (SSO) for the admin is disabled, then this field is mandatory for POST requests. This information is not provided in a GET response. |
| role | object | No | Role of the admin. This is not required for an auditor. |
| userName | string | Yes | Admin or auditor's username |

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

### MobileAppTokenInfo
Executive Insights App device token information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| cloud | string | No |  |
| createTime | integer (int64) | No |  |
| deviceId | string | No |  |
| deviceName | string | No |  |
| name | string | No |  |
| orgId | integer (int32) | No |  |
| token | string | No |  |
| tokenExpiry | integer (int64) | No |  |
| tokenId | string | No |  |

### PasswordExpirySettings
Password expiration information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| passwordExpirationEnabled | boolean | No | Specifies whether password expiration is enabled for the admin |
| passwordExpiryDays | integer (int32) | No | Password expiration duration, calculated in days |

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
