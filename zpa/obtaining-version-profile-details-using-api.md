# Obtaining Version Profile Details Using API
Source: https://help.zscaler.com/zpa/obtaining-version-profile-details-using-api
PDF: https://help.zscaler.com/pdf/com/en/1485041.pdf

This article provides information for managing Zscaler Private Access (ZPA) version profiles using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
[]Getting Details of All Version Profiles
To get details of all version profiles:
- Send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/visible/versionProfiles` in the customer-version-profile-controller.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057594037927936/visible/versionProfiles`.
- [View an example response](#ViewExample)
[]{
"totalPages": "1",
"list": [
{
"id": "0",
"modifiedTime": "1626626015",
"modifiedBy": "72057594037939756",
"name": "Default",
"upgradePriority": "WEEK",
"visibilityScope": "ALL",
"customerId": "72057594037927936"
},
{
"id": "1",
"modifiedTime": "1629892276",
"creationTime": "1624262913",
"modifiedBy": "72057594037988570",
"name": "Previous Default",
"description": "Cloud wide previous stable/default build. Provides roll-back ability",
"upgradePriority": "FORCE_NOW",
"visibilityScope": "ALL",
"customerId": "72057594037927936"
},
{
"id": "2",
"modifiedTime": "1631705841",
"creationTime": "1624262914",
"modifiedBy": "72057594037939756",
"name": "New Release",
"upgradePriority": "WEEK",
"visibilityScope": "ALL",
"customerId": "72057594037927936"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/visible/versionProfiles?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/144118148382065089/server?page=1&pagesize=2.`
- [View an example response](#paginatedResponse)
[]{
"totalPages": "2",
"list": [
{
"id": "0",
"modifiedTime": "1644938687",
"creationTime": "1475127781",
"modifiedBy": "72057594037928187",
"name": "Default",
"upgradePriority": "WEEK",
"visibilityScope": "ALL",
"customerId": "72057594037927936"
},
{
"id": "1",
"modifiedTime": "1634285256",
"creationTime": "1631577657",
"modifiedBy": "72057594037928193",
"name": "Previous Default",
"upgradePriority": "DAY",
"visibilityScope": "ALL",
"customerId": "72057594037927936"
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).