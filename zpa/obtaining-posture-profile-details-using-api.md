# Obtaining Posture Profile Details Using API
Source: https://help.zscaler.com/zpa/obtaining-posture-profile-details-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484836.pdf

This article provides information on managing Zscaler Private Access (ZPA) [posture profile](/client-connector/about-device-posture-profiles) use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
[]Getting Details for All Posture Profiles V2
To get the details for all posture profiles:
- Send a `GET` request to the following endpoint in the posture-profile-controller: `/mgmtconfig/v2/admin/customers/{customerId}/posture`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v2/admin/customers/217246660302995456/posture`.
- [View an example response](#ViewExample)
[]{
"totalPages": "13",
"list": [
{
"id": "217246660303020736",
"creationTime": "1502955460",
"modifiedBy": "72057594037928107",
"name": "39845-registryTest",
"postureUdid": "014b03ff-bcfd-4219-b574-5b7f74aa4a68",
"zscalerCloud": "zscalerbeta"
},
{
"id": "217246660303021896",
"modifiedTime": "1544470438",
"creationTime": "1511380873",
"modifiedBy": "72057594037928107",
"name": "Android Test",
"postureUdid": "4eb1ecd4-8e05-425f-b677-4340381ea849",
"zscalerCloud": "zscalerbeta"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/posture?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v2/admin/customers/217246660302995456/posture?page=1&pagesize=2.`
- [View an example response](#paginatedResponse)
[]{
"totalPages": "15",
"list": [
{
"id": "217246660303020736",
"creationTime": "1502955460",
"modifiedBy": "72057594037928107",
"name": "39845-registryTest (zscalerbeta.net)",
"postureUdid": "014b03ff-bcfd-4219-b574-5b7f74aa4a68",
"zscalerCloud": "zscalerbeta"
},
{
"id": "217246660303021896",
"modifiedTime": "1544470438",
"creationTime": "1511380873",
"modifiedBy": "72057594037928107",
"name": "Android Test (zscalerbeta.net)",
"postureUdid": "4eb1ecd4-8e05-425f-b677-4340381ea849",
"zscalerCloud": "zscalerbeta"
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports a search option to search by features and fields. To search by features and fields:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/73186051597795328/posture&search={searchString}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid search string values. The search string values are in the format `fieldName operator fieldValue`. Only search string values that correspond to the values for valid fields and filters are supported. For example, the string `name%20LIKE%20test` is supported for the **Name **filter, using the **Equals **(`EQ`) operator, for the filter value **test**.
For example: `/mgmtconfig/v1/admin/customers/73186051597795328/posture&search=name%20EQ%20test`.
- [View an example response](#gettingAllPostureProfileDetailsSearch)
[]{
"totalPages": "1",
"totalCount": "1",
"list": [
{
"id": "72057594038041099",
"modifiedTime": "0",
"creationTime": "1624340878",
"modifiedBy": "72057594037987389",
"name": "test (cloud.net)",
"postureUdid": "test",
"zscalerCloud": "cloud"
}
]
}
If you use the ZPA API Portal or the [Reference Guide](/zpa/zpa-api/api-developer-reference-guide/reference-guide) to make your API calls, the search field string does not require any characters. For example, `name%20LIKE%20test` is `name LIKE test`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details for a Particular Posture Profile
To get details for a particular posture profile:
- Send a `GET` request to the following endpoint in the posture-profile-controller: `/mgmtconfig/v1/admin/customers/{customerId}/posture/{id}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The ID of the desired posture profile.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/posture/217246660303022290`.
- [View an example response](#Viewanexampleresponse2)
[]{
"id": "217246660303022290",
"creationTime": "1531369746",
"modifiedBy": "72057594037928107",
"name": "test123",
"postureUdid": "519fe22c-bfd8-418a-ab9d-5c7f77f3ac54",
"zscalerCloud": "zscalerbeta"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).