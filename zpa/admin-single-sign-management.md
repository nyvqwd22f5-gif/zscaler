# Admin Single Sign-On Management
Source: https://help.zscaler.com/zpa/admin-single-sign-management

To access detailed ZPA API documentation, including references and use cases, refer to the [Zscaler Help Portal](/zpa/about-zpa-api).

## `GET /mgmtconfig/v1/admin/customers/{customerId}/v2/ssoLoginOptions`
Gets the single sign-on (SSO) login configuration details for the specified customer.

**Tags:** Admin Single Sign-On Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The ZPA tenant ID of the customer. |

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

## `POST /mgmtconfig/v1/admin/customers/{customerId}/v2/ssoLoginOptions`
Updates the SSO login configuration details for the specified customer.

**Tags:** Admin Single Sign-On Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customerId | path | integer (int64) | Yes | The ZPA tenant ID of the customer. |

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
