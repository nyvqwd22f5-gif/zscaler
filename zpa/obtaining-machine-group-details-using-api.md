# Obtaining Machine Group Details Using API
Source: https://help.zscaler.com/zpa/obtaining-machine-group-details-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484856.pdf

This article provides information on managing Zscaler Private Access (ZPA) [machine group](/zpa/about-machine-groups) use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
[]Getting Details for All Machine Groups
To get details for all the machine groups:
- Send a `GET` request to the following endpoint in the machine-group-controller: `/mgmtconfig/v1/admin/customers/{customerId}/machineGroup`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057615512764416/machineGroup`.
- [View an example response](#Viewanexampleresponse)
[]{
"totalPages": "1",
"list": [
{
"id": "73196561382769734",
"creationTime": "1612770231",
"modifiedBy": "73196561382768641",
"name": "Example machine group 1 DND",
"enabled": true
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/machineGroup?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/machineGroup?page=1&pagesize=2.`
- [View an example response](#paginatedResponse)
[]{
"totalPages": "2",
"list": [
{
"id": "217246660303025140",
"creationTime": "1624496602",
"modifiedBy": "217246660303023906",
"name": "test_machine_group",
"enabled": true,
"description": "test_machine_group"
},
{
"id": "217246660303023893",
"creationTime": "1594844294",
"modifiedBy": "72057594037935690",
"name": "Test",
"enabled": true,
"description": "test"
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports a search option to search by features and fields. To search by features and fields:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/73186051597795328/machineGroup&search={searchString}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid search string values. The search string values are in the format `fieldName operator fieldValue`. Only search string values that correspond to the values for valid fields and filters are supported. For example, the string `name%20LIKE%20123` is supported for the **Name **filter, using the **Contains **(`LIKE`) operator, for the filter value `123`.
For example: `/mgmtconfig/v1/admin/customers/73186051597795328/machineGroup&search=name%20LIKE%20123`.
- [View an example response](#gettingAllMachineGroupsSearch)
[]{
"totalPages": "2",
"totalCount": "2",
"list": [
{
"id": "72057594037987359",
"modifiedTime": "1646157983",
"creationTime": "1610701957",
"modifiedBy": "72057594038052745",
"name": "123",
"enabled": true,
"description": "/><img src=x onerror=alert(document.cookie)>"
}
]
}
If you use the ZPA API Portal or the [Reference Guide](/zpa/zpa-api/api-developer-reference-guide/reference-guide) to make your API calls, the search field string does not require any characters. For example, `name%20LIKE%20123` is `name LIKE 123`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details for a Particular Machine Group
To get details of a particular machine group:
- Send a `GET` request to the following endpoint in the machine-group-controller: `/mgmtconfig/v1/admin/customers/{customerId}/machineGroup/{Id}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The ID of the desired machine group.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/machineGroup/73196561382769734`.
- [View an example response](#Viewanexampleresponse2)
[]{
"id": "73196561382769734",
"creationTime": "1612770231",
"modifiedBy": "73196561382768641",
"name": "Example machine group 1 DND",
"enabled": true
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).