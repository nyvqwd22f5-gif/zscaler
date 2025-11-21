# Obtaining Trusted Network Details Using API
Source: https://help.zscaler.com/zpa/obtaining-trusted-network-details-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484841.pdf

This article provides information on managing Zscaler Private Access (ZPA) trusted network use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
[]Getting Details for All Trusted Networks V2
To get details for all the trusted networks:
- Send a `GET` request to the following endpoint in the trusted-network-controller: `/mgmtconfig/v2/admin/customers/{customerId}/network`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v2/admin/customers/217246660302995456/network`.
- [View an example response](#ViewExample)
[]{
"totalPages": "3",
"list": [
{
"id": "217246660303023500",
"creationTime": "1568929136",
"modifiedBy": "72057594037928107",
"name": "example mac",
"networkId": "1cd35d99-e509-49c6-a0fe-a1e1f754ac3e",
"zscalerCloud": "zpadev"
},
{
"id": "217246660303023640",
"creationTime": "1578427726",
"modifiedBy": "72057594037959595",
"name": "test1",
"networkId": "f373dbe7-1a21-488e-bd2b-6557e702357c",
"zscalerCloud": "zscalerone"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/network?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer, in the request endpoint.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/network?page=1&pagesize=2.`
- [View an example response](#paginatedResponse)
[]{
"totalPages": "3",
"list": [
{
"id": "217246660303023500",
"creationTime": "1568929136",
"modifiedBy": "72057594037928107",
"name": "Test network",
"networkId": "1cd35d99-e509-49c6-a0fe-a1e1f754ac3e",
"zscalerCloud": "zpaTest"
},
{
"id": "217246660303023640",
"creationTime": "1578427726",
"modifiedBy": "72057594037959595",
"name": "test1 (zscalerone.net)",
"networkId": "f373dbe7-1a21-488e-bd2b-6557e702357c",
"zscalerCloud": "zscalerone"
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports a search option to search by features and fields. To search by features and fields:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/73186051597795328/network&search={searchString}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid search string values. The search string values are in the format `fieldName operator fieldValue`. Only search string values that correspond to the values for valid fields and filters are supported. For example, the string `enabled%20EQ%20true` is supported for the **Name **filter, using the **Contains **(`LIKE`) operator, for the filter value `test`.
For example: `/mgmtconfig/v1/admin/customers/73186051597795328/network&search=name%20LIKE%20test`.
- [View an example response](#getAllTrustedNetworksSearch)
[]{
"totalPages": "1",
"totalCount": "2",
"list": [
{
"id": "72057594038041097",
"creationTime": "1624340572",
"modifiedBy": "72057594037987389",
"name": "Test (cloud.net)",
"networkId": "1",
"zscalerCloud": "cloud"
},
{
"id": "72057594038041098",
"creationTime": "1624340631",
"modifiedBy": "72057594037987389",
"name": "Test 20 (cloud.net)",
"networkId": "2",
"zscalerCloud": "cloud"
}
]
}
If you use the ZPA API PortaI or the [Reference Guide](/zpa/zpa-api/api-developer-reference-guide/reference-guide) to make your API calls, the search field string does not require any characters. For example, `name%20LIKE%20test` is `name LIKE test`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details for a Particular Trusted Network
To get details of a particular trusted network:
- Send a `GET` request to the following endpoint in the trusted-network-controller: `/mgmtconfig/v1/admin/customers/{customerId}/network/{id}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The ID of the desired trusted network.
For example:`/mgmtconfig/v1/admin/customers/72057615512764416/network/72057615512764509`.
- [View an example response](#Viewanexampleresponse2)
[]{
"id": "72057615512764509",
"creationTime": "1571232759",
"modifiedBy": "72057594037927995",
"name": "Home",
"networkId": "2b8a83bd-3fab-4961-b12c-e64553f15327",
"zscalerCloud": "zscalerbeta"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).