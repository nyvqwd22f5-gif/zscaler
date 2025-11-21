# Managing Admin Single Sign-On Login Configurations Using API
Source: https://help.zscaler.com/zpa/managing-admin-single-sign-login-configurations-using-api
PDF: https://help.zscaler.com/pdf/com/en/1530912.pdf

This article provides information on managing Zscaler Private Access (ZPA) administrator single sign-on (SSO) login configuration use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Getting SSO Login Configuration Details
To get SSO login details:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/v2/ssoLoginOptions`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/144118148382064640/v2/ssoLoginOptions`.
- [View an example response](#getSsoLoginExample)
[]
`{
"ssologinonly": false
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating SSO Login Configuration Details
To update SSO login configuration details:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/v2/ssoLoginOptions`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/144118148382064640/v2/ssoLoginOptions`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and pass the `ssologinonly` field as `true` (to enable SSO), or `false` (to disable SSO).
- [View the JSON payload](#putSsoLoginPayload)
[]
`{
"ssologinonly": true
}`
A successful response returns code 204, meaning the SSO login configuration is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).