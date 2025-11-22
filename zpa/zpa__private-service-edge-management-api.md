# Private Service Edge Management
Source: https://help.zscaler.com/zpa/private-service-edge-management-api

To access detailed ZPA API documentation, including references and use cases, refer to the [Zscaler Help Portal](/zpa/about-zpa-api).

## `GET /mgmtconfig/v1/admin/customers/{customerId}/serviceEdge`
Gets all the configured ZPA Private Service Edge details for the specified customer.

**Tags:** Private Service Edge Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
| search | query | string | No | The search string used to support search by features and fields for the API. |
| page | query | integer (int32) | No | Specifies the page number. |
| pagesize | query | integer (int32) | No | Specifies the page size. If not provided, the default page size is 20. The max page size is 500. |
| sortBy | query | string | No | Indicates the parameter to sort by. |
| sortDir | query | string | No | Specifies the sort direction (i.e., ascending or descending order). |
| microtenantId | query | integer (int64) | No | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the microtenantId field when making an API call to retrieve data from that Microtenant. The microtenantId can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass microtenantId as 0 when making requests to retrieve data from the Default Microtenant. If the microtenantId is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. |

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

## `POST /mgmtconfig/v1/admin/customers/{customerId}/serviceEdge/bulkDelete`
Bulk deletes the ZPA Private Service Edges for the specified customer.

**Tags:** Private Service Edge Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
| microtenantId | query | integer (int64) | No | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the microtenantId field when making an API call to retrieve data from that Microtenant. The microtenantId can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass microtenantId as 0 when making requests to retrieve data from the Default Microtenant. If the microtenantId is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. |

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

## `DELETE /mgmtconfig/v1/admin/customers/{customerId}/serviceEdge/{serviceEdgeId}`
Deletes the ZPA Private Service Edge for the specified ID.

**Tags:** Private Service Edge Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
| serviceEdgeId | path | integer (int64) | Yes | The unique identifier of the ZPA Private Service Edge. |
| microtenantId | query | integer (int64) | No | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the microtenantId field when making an API call to retrieve data from that Microtenant. The microtenantId can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass microtenantId as 0 when making requests to retrieve data from the Default Microtenant. If the microtenantId is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | No Content |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 405 | Method Not Allowed |  |
| 409 | Conflict |  |
| 415 | Unsupported Media Type |  |
| 500 | Internal Server Error |  |
| 503 | Service Unavailable |  |

## `GET /mgmtconfig/v1/admin/customers/{customerId}/serviceEdge/{serviceEdgeId}`
Gets the ZPA Private Service Edge details for the specified ID.

**Tags:** Private Service Edge Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
| serviceEdgeId | path | integer (int64) | Yes | The unique identifier of the ZPA Private Service Edge. |
| microtenantId | query | integer (int64) | No | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the microtenantId field when making an API call to retrieve data from that Microtenant. The microtenantId can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass microtenantId as 0 when making requests to retrieve data from the Default Microtenant. If the microtenantId is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. |

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

## `PUT /mgmtconfig/v1/admin/customers/{customerId}/serviceEdge/{serviceEdgeId}`
Updates the ZPA Private Service Edge details for the specified ID.

**Tags:** Private Service Edge Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
| serviceEdgeId | path | integer (int64) | Yes | The unique identifier of the ZPA Private Service Edge. |
| microtenantId | query | integer (int64) | No | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the microtenantId field when making an API call to retrieve data from that Microtenant. The microtenantId can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass microtenantId as 0 when making requests to retrieve data from the Default Microtenant. If the microtenantId is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | No Content |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 405 | Method Not Allowed |  |
| 409 | Conflict |  |
| 415 | Unsupported Media Type |  |
| 500 | Internal Server Error |  |
| 503 | Service Unavailable |  |

## `GET /mgmtconfig/v1/admin/customers/{customerId}/serviceEdgeSchedule`
Gets the Auto Delete frequency of the ZPA Private Service Edge for the specified customer.

**Tags:** Private Service Edge Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
| microtenantId | query | integer (int64) | No | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the microtenantId field when making an API call to retrieve data from that Microtenant. The microtenantId can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass microtenantId as 0 when making requests to retrieve data from the Default Microtenant. If the microtenantId is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. |

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

## `POST /mgmtconfig/v1/admin/customers/{customerId}/serviceEdgeSchedule`
Configures Auto Delete for the specified disconnected ZPA Private Service Edge.

**Tags:** Private Service Edge Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
| microtenantId | query | integer (int64) | No | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the microtenantId field when making an API call to retrieve data from that Microtenant. The microtenantId can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass microtenantId as 0 when making requests to retrieve data from the Default Microtenant. If the microtenantId is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | No Content |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 405 | Method Not Allowed |  |
| 409 | Conflict |  |
| 415 | Unsupported Media Type |  |
| 500 | Internal Server Error |  |
| 503 | Service Unavailable |  |

## `PUT /mgmtconfig/v1/admin/customers/{customerId}/serviceEdgeSchedule/{id}`
Updates the Auto Delete frequency for the disconnected ZPA Private Service Edge by the specified Auto Delete configuration ID.

**Tags:** Private Service Edge Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
| id | path | integer (int64) | Yes | The unique identifier for the ZPA Private Service Edge auto-deletion configuration for a customer. This field is only required for the PUT request to update the frequency of the ZPA Private Service Edge settings. |
| microtenantId | query | integer (int64) | No | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the microtenantId field when making an API call to retrieve data from that Microtenant. The microtenantId can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass microtenantId as 0 when making requests to retrieve data from the Default Microtenant. If the microtenantId is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | No Content |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 405 | Method Not Allowed |  |
| 409 | Conflict |  |
| 415 | Unsupported Media Type |  |
| 500 | Internal Server Error |  |
| 503 | Service Unavailable |  |
