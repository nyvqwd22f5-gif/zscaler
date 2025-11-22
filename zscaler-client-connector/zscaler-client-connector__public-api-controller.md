# Public API Controller
Source: https://help.zscaler.com/zscaler-client-connector/public-api-controller

Api Documentation

## `GET /papi/public/v1/downloadDevices`

Downloads or exports device information as a CSV file.

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| osTypes | query | string | No | Filter the list of devices by operating systems. The default value is null, which represents ALL OS types. The following values represent different OS types:
- 1 - iOS
- 2 - Android
- 3 - Windows
- 4 - macOS
- 5 - Linux
A sample API call: https://api-mobile.zscalerbeta.net/papi/public/v1/downloadDevices?osTypes=1,2 |
| registrationTypes | query | string | No | Filter the list of devices by registration types or states. The following values represent different device states:
- 0 - All states except Removed
- 1 - Registered
- 3 - Removal pending
- 4 - Unregistered
- 5 - Removed
- 6 - Quarantined
A sample API call:
https://api-mobile.zscalerbeta.net/papi/public/v1/downloadDevices?registrationTypes=1,3 |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `GET /papi/public/v1/downloadDisableReasons`

Downloads or exports a report as a CSV file showing the disable reasons of a device.

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| Time-Zone | header | string | No | Time-Zone |
| osTypes | query | string | No | Filter the list of entries by operating systems. The default value is null, which represents ALL OS types. The following values represent different OS types:
- 1 - iOS
- 2 - Android
- 3 - Windows
- 4 - macOS
- 5 - Linux |
| startDate | query | string | Yes | startDate |
| endDate | query | string | No | endDate |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `GET /papi/public/v1/downloadServiceStatus`

Downloads service status of all devices as a CSV file.

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| osTypes | query | string | No | Filter the list by operating systems. The default value is null, which represents ALL OS types. The following values represent different OS types:
- 1 - iOS
- 2 - Android
- 3 - Windows
- 4 - macOS
- 5 - Linux
A sample API call: https://api-mobile.zscalerbeta.net/papi/public/v1/downloadServiceStatus?osTypes=1,2 |
| registrationTypes | query | string | No | Filter the list by registration types or states. The following values represent different device states:
- 0 - All states except Removed
- 1 - Registered
- 3 - Removal pending
- 4 - Unregistered
- 5 - Removed
- 6 - Quarantined
A sample API call:
https://api-mobile.zscalerbeta.net/papi/public/v1/downloadServiceStatus?registrationTypes=1,3 |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `PUT /papi/public/v1/editAdminUser`
editAdminUser

Updates a specific admin user.
** ⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `POST /papi/public/v1/forceRemoveDevices`

Force removes the enrolled device from the portal. You can only remove devices that are in registered or device removal pending state. At least one criterion (username, Zscaler Client Connector version, OS type, or UDID) must be specified to remove devices.
The following are the valid values for the `osType` attribute. The default value is null, which represents ALL OS types.
- 1 - iOS
- 2 - Android
- 3 - Windows
- 4 - macOS
- 5 - Linux

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| pageSize | query | integer (int32) | No | Specifies the page size. If not provided, the default page size is 30. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `GET /papi/public/v1/getAdminRoles`
getAdminRoles

List of admin roles in your organization.
** ⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | page |
| pageSize | query | integer (int32) | No | pageSize |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `GET /papi/public/v1/getAdminUsers`
getAdminUsers

Gets the list of admin users in your organization.
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | page |
| pageSize | query | integer (int32) | No | pageSize |
| userType | query | string (byte) | No | userType |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `GET /papi/public/v1/getAdminUsersSyncInfo`
adminUsersSyncInfo

Synchronizes the local copy of admin users.
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `GET /papi/public/v1/getCompanyInfo`
getCompanyInfo

Gets information about your organization such as the name of the business, domains, etc.
**⚠ This API endpoint is allowed if called via OneAPI or if the token has admin or read-only admin privileges.**

**Tags:** public-api-controller
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `GET /papi/public/v1/getDeviceCleanupInfo`
getDeviceCleanupInfo

Gets the configuration for device cleanup.
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `GET /papi/public/v1/getDeviceDetails`

Lists device details of enrolled devices of your organization.

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| username | query | string | No | Filter by enrolled user name for the device. |
| udid | query | string | No | Filter by unique device identifier. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `GET /papi/public/v1/getDevices`

Lists all enrolled devices of your organization and their basic details.

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| username | query | string | No | Filter by enrolled user name for the device. |
| osType | query | string (byte) | No | Filter by device operating system type. |
| page | query | integer (int32) | No | Specifies the page number. |
| pageSize | query | integer (int32) | No | Specifies the page size. If not provided, the default page size is 50. The max page size is 5000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `GET /papi/public/v1/getOtp`

Gets the one-time password (OTP) for a specific device. These single-use passwords are unique and tied to the device Unique Device Identifier (UDID). It is made of 10 random alphanumeric characters and can only be used once.

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| udid | query | string | No | Unique device identifier. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `GET /papi/public/v1/getPasswords`

Gets the app profile password for a specific device. You can determine the assigned global passwords by using the username and OS type of a device.

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| username | query | string | No | Enrolled user for the device. |
| osType | query | integer (int32) | No | Device operating system. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `GET /papi/public/v1/getWebPrivacyInfo`
getPrivacyInfo

Gets the configuration information for end user and device-related PII.
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `GET /papi/public/v1/getZdxGroupEntitlements`
getUpmGroupEntitlementEnabled

Gets the list of ZDX entitlements for user groups.

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | page |
| pageSize | query | integer (int32) | No | pageSize |
| search | query | string | No | search |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `GET /papi/public/v1/getZpaGroupEntitlements`
getGroupEntitlementEnabled

Gets the list of ZPA entitlements for user groups.
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | page |
| pageSize | query | integer (int32) | No | pageSize |
| search | query | string | No | search |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `POST /papi/public/v1/removeDevices`

Soft removes the enrolled device from the portal. The soft removal marks the device state as device removal pending. At least one criterion (username, Zscaler Client Connector version, OS type, or UDID) must be specified to remove devices.
The following are the valid values for  the `osType` attribute. The default value is null, which represents ALL OS types.
- 1 - iOS
- 2 - Android
- 3 - Windows
- 4 - macOS
- 5 - Linux

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| pageSize | query | integer (int32) | No | Specifies the page size. If not provided, the default page size is 30. The max page size is 5000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `POST /papi/public/v1/removeMachineTunnel`
removeMachineTunnelDevices

Remove machine tunnel devices.
**Note:** For the parameters described below, you can specify either hostName or machineToken but not both.

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| hostName | query | string | No | Comma-separated list of hostnames for the device. |
| machineToken | query | string | No | Machine token. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `PUT /papi/public/v1/setDeviceCleanupInfo`
setDeviceCleanupInfo

Adds or updates the configuration for device cleanup.
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `PUT /papi/public/v1/setWebPrivacyInfo`
updatePrivacyInfo

Adds or updates the configuration information for end user and device-related PII.
**⚠ This API endpoint is accessible only via test 123 [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `POST /papi/public/v1/syncZiaZdxAdminUsers`
adminUsersZiaZdxSyncInfo

Synchronizes the local copy of all the ZIA and ZDX admin users.
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `POST /papi/public/v1/syncZpaAdminUsers`
adminUsersZpaSyncInfo

Synchronizes the local copy of the ZPA admin users.
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `PUT /papi/public/v1/updateZdxGroupEntitlement`
updateGroupEntitlementUpm

Updates ZDX entitlement for user groups.
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `PUT /papi/public/v1/updateZpaGroupEntitlement`
updateGroupEntitlementZpa

Updates ZPA entitlement for user groups.
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `PUT /papi/public/v1/web/policy/activate`
activateWebPolicy

Enables or disables a policy or app profile for the company by platform (iOS, Android, Windows, macOS, and Linux).
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `PUT /papi/public/v1/web/policy/edit`
editPolicy

Adds or updates a policy or app profile for the company by platform (iOS, Android, Windows, macOS, and Linux).
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `GET /papi/public/v1/web/policy/listByCompany`
getPolicyListByCompanyId

**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**
The following are the valid values for the deviceType attribute:
- 1 - iOS
- 2 - Android
- 3 - Windows
- 4 - macOS
- 5 - Linux

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | page |
| pageSize | query | integer (int32) | No | pageSize |
| search | query | string | No | search |
| searchType | query | string | No | searchType |
| deviceType | query | integer (int32) | No | deviceType |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `DELETE /papi/public/v1/web/policy/{policyId}/delete`
deletePolicy

Deletes a policy or app profile for the company by platform (iOS, Android, Windows, macOS, and Linux).
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| policyId | path | integer (int32) | Yes | policyId |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `GET /papi/public/v1/webAppService/listByCompany`
getAppServiceInfoByCompanyId

Gets the list of applications to bypass Zscaler such as Zoom, Microsoft Teams, etc.
**⚠ This API is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | page |
| pageSize | query | integer (int32) | No | pageSize |
| search | query | string | No | search |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `PUT /papi/public/v1/webFailOpenPolicy/edit`
updateFailOpenPolicy

Updates a specific FailOpen policy for the company.
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `GET /papi/public/v1/webFailOpenPolicy/listByCompany`
getFailOpenPolicy

Gets the list of FailOpen policies for the company.
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | page |
| pageSize | query | integer (int32) | No | pageSize |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `POST /papi/public/v1/webForwardingProfile/edit`
editForwardingProfile

Updates a forwarding profile.
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `GET /papi/public/v1/webForwardingProfile/listByCompany`
forwardingProfilesByCompanyId

Gets the list of forwarding profiles by company.
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | page |
| pageSize | query | integer (int32) | No | pageSize |
| search | query | string | No | search |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `DELETE /papi/public/v1/webForwardingProfile/{profileId}/delete`
deleteForwardingProfile

Deletes a forwarding profile.
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| profileId | path | integer (int32) | Yes | profileId |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `POST /papi/public/v1/webTrustedNetwork/create`
createTrustedNetwork

Adds a new trusted network.
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `PUT /papi/public/v1/webTrustedNetwork/edit`
updateTrustedNetwork

Updates a trusted network.
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `GET /papi/public/v1/webTrustedNetwork/listByCompany`
getMultipleTrustedNetworks

Gets the list of trusted networks by company.

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | page |
| pageSize | query | integer (int32) | No | pageSize |
| search | query | string | No | search |
| searchType | query | string | No | searchType |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |

## `DELETE /papi/public/v1/webTrustedNetwork/{networkId}/delete`
deleteTrustedNetwork

Deletes a trusted network.
**⚠ This API endpoint is accessible only via [OneAPI](https://help.zscaler.com/oneapi).**

**Tags:** public-api-controller

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| networkId | path | integer (int64) | Yes | networkId |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 429 | Too Many Requests |  |
