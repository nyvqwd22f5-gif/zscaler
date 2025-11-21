# Obtaining Customer Details Using API
Source: https://help.zscaler.com/zpa/obtaining-customer-details-using-api
PDF: https://help.zscaler.com/pdf/com/en/1485186.pdf

This article provides information for managing Zscaler Private Access (ZPA) customers using APIs. All APIs are rate limited. To learn more, see [About Rate Limiting](/zpa/about-rate-limiting).
Getting Authentication Domains for a Customer
To get authentication domains for the customer:
- Send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/authdomains` in the customer-controller.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/authdomains`.
- [View an example response](#exampleResponse)
[]{
"authDomains": [
"mockcompany.com",
"test1000.com",
"test2000.com",
"test3000.com"
]
}
A successful response returns code 200. To learn more, see [About Error Codes](/zpa/about-error-codes).