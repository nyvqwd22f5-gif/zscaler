# Obtaining Isolation Profile Details Using API
Source: https://help.zscaler.com/zpa/obtaining-isolation-profile-details-using-api
PDF: https://help.zscaler.com/pdf/com/en/1485731.pdf

This article provides information for managing Zscaler Private Access (ZPA) isolation profiles using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Getting Details of All Isolation Profiles
To get details of all isolation profiles for a specific customer:
- Send a `GET` request to the following endpoint in the isolation-profile-controller: `/mgmtconfig/v1/admin/customers/{customerId}/isolation/profiles`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/73189906330943488/isolation/profiles`.
- [View an example response](#getExample)
[]{
"totalPages": "1",
"totalCount": "3",
"list": [
{
"id": "73186051597800349",
"creationTime": "1665399497",
"modifiedBy": "72057594037986137",
"name": "Test Isolation Profile",
"enabled": true,
"isolationTenantId": "5469af78-c8d5-48ab-8018-d499c9fb875b",
"isolationProfileId": "02b320ad-aef7-4cfa-a763-5cf8524544f7",
"isolationUrl": "https://fb.4af6eb6dad89.appsulate.com/profile/02b320ad-aef7-4cfa-a763-5cf8524544f7/zpa/render"
},
{
"id": "73186051597800311",
"modifiedTime": "1663869847",
"creationTime": "1663836249",
"modifiedBy": "72057594037986137",
"name": "Test Isolation Profile 1",
"enabled": true,
"isolationTenantId": "5469af78-c8d5-48ab-8018-d499c9fb875b",
"isolationProfileId": "92924d37-cb71-4a14-9bc4-cb5682062729",
"isolationUrl": "https://sf.4af6eb6dad89.appsulate.com/profile/92924d37-cb71-4a14-9bc4-cb5682062729/zpa/render"
},
{
"id": "73186051597800310",
"modifiedTime": "1663836536",
"creationTime": "1663836115",
"modifiedBy": "72057594037986137",
"name": "Test Isolation Profile 2",
"enabled": true,
"isolationTenantId": "5469af78-c8d5-48ab-8018-d499c9fb875b",
"isolationProfileId": "91a5ba7a-1e84-49a3-ba92-ccba306c6a29",
"isolationUrl": "https://sb.4af6eb6dad89.appsulate.com/profile/91a5ba7a-1e84-49a3-ba92-ccba306c6a29/zpa/render"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint in the isolation-profile-controller: `/mgmtconfig/v1/admin/customers/{customerId}/isolation/profiles?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: the ZPA tenant ID of the customer, in the request endpoint.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/73189906330943488/isolation/profiles?page=1&pagesize=2`.
- [View an example response](#getPaginationExample)
[]{
"totalPages": "2",
"totalCount": "3",
"list": [
{
"id": "73186051597800349",
"creationTime": "1665399497",
"modifiedBy": "72057594037986137",
"name": "Test Isolation Profile",
"enabled": true,
"isolationTenantId": "5469af78-c8d5-48ab-8018-d499c9fb875b",
"isolationProfileId": "02b320ad-aef7-4cfa-a763-5cf8524544f7",
"isolationUrl": "https://fb.4af6eb6dad89.appsulate.com/profile/02b320ad-aef7-4cfa-a763-5cf8524544f7/zpa/render"
},
{
"id": "73186051597800311",
"modifiedTime": "1663869847",
"creationTime": "1663836249",
"modifiedBy": "72057594037986137",
"name": "Test Isolation Profile 1",
"enabled": true,
"isolationTenantId": "5469af78-c8d5-48ab-8018-d499c9fb875b",
"isolationProfileId": "92924d37-cb71-4a14-9bc4-cb5682062729",
"isolationUrl": "https://sf.4af6eb6dad89.appsulate.com/profile/92924d37-cb71-4a14-9bc4-cb5682062729/zpa/render"
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).