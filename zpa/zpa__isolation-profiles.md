# Isolation Profiles
Source: https://help.zscaler.com/zpa/isolation-profiles

To access detailed ZPA API documentation, including references and use cases, refer to the [Zscaler Help Portal](/zpa/about-zpa-api).

## `GET /cbiconfig/cbi/api/customers/{customerId}/profiles`
Gets all isolation profiles for the specified customer.

**Tags:** Isolation Profile Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
| scopeId | query | integer (int64) | No | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the microtenantId field when making an API call to retrieve data from that Microtenant. The microtenantId can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass microtenantId as 0 when making requests to retrieve data from the Default Microtenant. If the microtenantId is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Invalid Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 500 | Server error |  |

## `POST /cbiconfig/cbi/api/customers/{customerId}/profiles`
Adds an isolation profile for the specified customer.

**Tags:** Isolation Profile Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
| scopeId | query | integer (int64) | No | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the microtenantId field when making an API call to retrieve data from that Microtenant. The microtenantId can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass microtenantId as 0 when making requests to retrieve data from the Default Microtenant. If the microtenantId is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Invalid Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 500 | Server error |  |

## `DELETE /cbiconfig/cbi/api/customers/{customerId}/profiles/{profileId}`
Deletes the isolation profile for the specified ID.

**Tags:** Isolation Profile Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
| profileId | path | string (uuid) | Yes | The unique identifier of the isolation profile ID. |
| scopeId | query | integer (int64) | No | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the microtenantId field when making an API call to retrieve data from that Microtenant. The microtenantId can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass microtenantId as 0 when making requests to retrieve data from the Default Microtenant. If the microtenantId is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Invalid Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 500 | Server error |  |

## `GET /cbiconfig/cbi/api/customers/{customerId}/profiles/{profileId}`
Gets the isolation profile details for specified ID.

**Tags:** Isolation Profile Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
| profileId | path | string (uuid) | Yes | The unique identifier of the isolation profile |
| scopeId | query | integer (int64) | No | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the microtenantId field when making an API call to retrieve data from that Microtenant. The microtenantId can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass microtenantId as 0 when making requests to retrieve data from the Default Microtenant. If the microtenantId is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Invalid Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 500 | Server error |  |

## `PUT /cbiconfig/cbi/api/customers/{customerId}/profiles/{profileId}`
Updates the isolation profile for specified ID.

**Tags:** Isolation Profile Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
| profileId | path | string (uuid) | Yes | The unique identifier of the isolation profile. |
| scopeId | query | integer (int64) | No | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the microtenantId field when making an API call to retrieve data from that Microtenant. The microtenantId can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass microtenantId as 0 when making requests to retrieve data from the Default Microtenant. If the microtenantId is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Invalid Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 500 | Server error |  |

## `GET /cbiconfig/cbi/api/customers/{customerId}/regions`
Gets all regions for the specified customer.

**Tags:** Isolation Profile Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Invalid Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 500 | Server error |  |

## `GET /cbiconfig/cbi/api/customers/{customerId}/zpaprofiles`
Gets all isolation profiles in ZPA for the specified customer.

**Tags:** Isolation Profile Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
| showDisabled | query | boolean | No | If set to true, shows all disabled isolation profiles. |
| scopeId | query | integer (int64) | No | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the microtenantId field when making an API call to retrieve data from that Microtenant. The microtenantId can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass microtenantId as 0 when making requests to retrieve data from the Default Microtenant. If the microtenantId is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Invalid Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 500 | Server error |  |

## `GET /mgmtconfig/v1/admin/customers/{customerId}/isolation/profiles`
Gets all isolation profiles for the specified customer.

**Tags:** Isolation Profile Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
| showDisabled | query | boolean | No | If set to true, shows all disabled isolation profiles. |
| search | query | string | No | The search string used to support search by features and fields for the API. |
| page | query | integer (int32) | No | Specifies the page number. |
| pagesize | query | integer (int32) | No | Specifies the page size. If not provided, the default page size is 20. The max page size is 500. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 405 | Method Not Allowed |  |
| 409 | Conflict |  |
| 415 | Unsupported Media Type |  |
| 500 | Internal Server Error |  |
| 503 | Service Unavailable |  |
