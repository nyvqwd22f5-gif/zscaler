# Log Streaming Service (LSS) Configuration
Source: https://help.zscaler.com/zpa/log-streaming-service-lss-configuration

To access detailed ZPA API documentation, including references and use cases, refer to the [Zscaler Help Portal](/zpa/about-zpa-api).

## `GET /mgmtconfig/v2/admin/customers/{customerId}/lssConfig`
Gets all LSS configurations for the specified customer.

**Tags:** Log Streaming Service (LSS) Configuration

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
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

## `POST /mgmtconfig/v2/admin/customers/{customerId}/lssConfig`
Adds a new LSS configuration for the specified customer.

**Tags:** Log Streaming Service (LSS) Configuration

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 201 | Created |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
| 405 | Method Not Allowed |  |
| 409 | Conflict |  |
| 415 | Unsupported Media Type |  |
| 500 | Internal Server Error |  |
| 503 | Service Unavailable |  |

## `GET /mgmtconfig/v2/admin/customers/{customerId}/lssConfig/logType/formats`
Gets all LSS log formats for the specified customer.

**Tags:** Log Streaming Service (LSS) Configuration

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
| logType | query | string | No | The log type of the LSS resource. The supported log type values are:
- `zpn_trans_log`: Denotes the User Activity log type.
- `zpn_auth_log`: Denotes the User Status log type.
- `zpn_ast_auth_log`: Denotes the App Connector Status log type.
- `zpn_http_trans_log`: Denotes the Browser Access log type.
- `zpn_audit_log`: Denotes the Audit Log log type.
- `zpn_sys_auth_log`: Denotes the Private Service Edge Status log type.
- `zpn_ast_comprehensive_stats`: Denotes the App Connector Metrics log type.
- `zpn_waf_http_exchanges_log`: Denotes the AppProtection log type.
- `zpn_smb_inspection_log`: Denotes the SMB Inspection log type.
- `zpn_ldap_inspection_log`: Denotes the LDAP Inspection log type.
- `zpn_krb_inspection_log`: Denotes the KRB Inspection log type.
- `zpn_pbroker_comprehensive_stats`: Denotes the Private Service Edge Metrics log type.
- `zpn_sitec_auth_log`: Denotes the Private Cloud Controller Status log type.
- `zpn_sitec_comprehensive_stats`: Denotes the Private Cloud Controller Metrics log type.
- `zms_flow_log`: Denotes the Microsegmentation Flow Logs log type. |

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

## `DELETE /mgmtconfig/v2/admin/customers/{customerId}/lssConfig/{lssId}`
Deletes the LSS configuration for the specified ID.

**Tags:** Log Streaming Service (LSS) Configuration

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
| lssId | path | integer (int64) | Yes | The unique identifier of the LSS resource. |

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

## `GET /mgmtconfig/v2/admin/customers/{customerId}/lssConfig/{lssId}`
Gets the LSS configuration details for the specified ID.

**Tags:** Log Streaming Service (LSS) Configuration

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
| lssId | path | integer (int64) | Yes | The unique identifier of the LSS resource. |

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

## `PUT /mgmtconfig/v2/admin/customers/{customerId}/lssConfig/{lssId}`
Updates the LSS configuration for the specified ID.

**Tags:** Log Streaming Service (LSS) Configuration

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |
| lssId | path | integer (int64) | Yes | The unique identifier of the LSS resource. |

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

## `GET /mgmtconfig/v2/admin/lssConfig/clientTypes`
Gets all LSS client types. This API will be deprecated in a future release.

**Tags:** Log Streaming Service (LSS) Configuration
No parameters.

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

## `GET /mgmtconfig/v2/admin/lssConfig/customers/{customerId}/clientTypes`
Gets all LSS client types for the specified customer.

**Tags:** Log Streaming Service (LSS) Configuration

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The unique identifier of the ZPA tenant. |

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

## `GET /mgmtconfig/v2/admin/lssConfig/logType/formats`
Gets all LSS log formats.

**Tags:** Log Streaming Service (LSS) Configuration

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| logType | query | string | No | The log type of the LSS resource. The supported log type values are:
- `zpn_trans_log`: Denotes the User Activity log type.
- `zpn_auth_log`: Denotes the User Status log type.
- `zpn_ast_auth_log`: Denotes the App Connector Status log type.
- `zpn_http_trans_log`: Denotes the Browser Access log type.
- `zpn_audit_log`: Denotes the Audit Log log type.
- `zpn_sys_auth_log`: Denotes the Private Service Edge Status log type.
- `zpn_ast_comprehensive_stats`: Denotes the App Connector Metrics log type.
- `zpn_waf_http_exchanges_log`: Denotes the AppProtection log type.
- `zpn_smb_inspection_log`: Denotes the SMB Inspection log type.
- `zpn_ldap_inspection_log`: Denotes the LDAP Inspection log type.
- `zpn_krb_inspection_log`: Denotes the KRB Inspection log type.
- `zpn_pbroker_comprehensive_stats`: Denotes the Private Service Edge Metrics log type.
- `zpn_sitec_auth_log`: Denotes the Private Cloud Controller Status log type.
- `zpn_sitec_comprehensive_stats`: Denotes the Private Cloud Controller Metrics log type.
- `zms_flow_log`: Denotes the Microsegmentation Flow Logs log type. |

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

## `GET /mgmtconfig/v2/admin/lssConfig/statusCodes`
Gets a list of LSS status codes.

**Tags:** Log Streaming Service (LSS) Configuration
No parameters.

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
