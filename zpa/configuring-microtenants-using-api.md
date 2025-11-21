# Configuring Microtenants Using API
Source: https://help.zscaler.com/zpa/configuring-microtenants-using-api
PDF: https://help.zscaler.com/pdf/com/en/1485721.pdf

This article provides information for managing Zscaler Private Access (ZPA) [Microtenants](/zpa/about-microtenants) using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
The following conditions apply when passing `microtenantId`, the unique identifier of the Microtenant, in a request:
- If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the [API Keys](/zpa/about-api-keys) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant.
- If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant.
- When making requests using inheritable resources, you can pass `microtenantId` as null to retrieve data from all Microtenants associated with the tenant. [Click here to see a list of inheritable resources.](#inheritableResources)
- []Application Segments
- Segment Groups
- App Connectors
- App Connector Groups
- Certificates
- Emergency Access users
- Machine Groups
- Microtenants
- Privileged Approvals
- Privileged Consoles
- Privileged Credentials
- Privileged Portals
- Provisioning Keys
- Servers
- Server Groups
- ZPA Private Service Edges
- ZPA Private Service Edge Groups
[]Getting Details for All Microtenants
To get details for all Microtenants:
- Send a `GET` request to the following endpoint in the Microtenant controller: `/mgmtconfig/v1/admin/customers/{customerId}/microtenants`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the endpoint. For example: `/mgmtconfig/v1/admin/customers/72057594037927936/microtenants`.
- [View an example response](#ViewExample)
[]{
"totalPages": "3",
"list": [
{
"id": "72057594038621068",
"creationTime": "1663791107",
"modifiedBy": "72057594038052745",
"name": "Example Microtenant",
"enabled": false,
"operator": "OR",
"criteriaAttribute": "AuthDomain",
"criteriaAttributeValues": [
"1467901757270.com"
]
},
{
"name": "Default",
"description": "This is the default Microtenant for users not associated to any Microtenant",
"enabled": true,
"operator": "OR"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting All Microtenants by Given Filters
To get all Microtenants by the given filters:
- Send a `POST` request to the following endpoint in the Microtenant controller: `/mgmtconfig/v1/admin/customers/{customerId}/microtenants/search`.
- Provide the `customerId`, the tenant ID of the ZPA customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057594037987390/microtenants/search`.
- Use the following JSON payload to get all Microtenants by given filters.
You choose the filter criteria to include in the JSON payload. Refer to the [Adding Field Descriptions](#fieldDescriptions) section for supported values.
- [View the JSON payload](#ViewJson)
[]{
"filterBy": [
{
"filterName": "string",
"operator": "string",
"values": [
"string"
]
}
],
"pageBy": {
"page": "string",
"pageSize": "string",
"validPage": 0,
"validPageSize": 0
},
"sortBy": {
"sortName": "string",
"sortOrder": "string"
}
}
- [View a sample JSON payload](#ViewSampleJson)
[]{
"pageBy":{
"page":1,
"pageSize":20
},
"filterBy":[
{
"filterName":"criteriaAttributeValues",
"operator":"LIKE",
"values":[
"Test"
]
}
]
}
- [View an example response](#ViewExample1)
[]{
"totalPages": "1",
"list": [
{
"id": "73186051597800497",
"creationTime": "1669058887",
"modifiedBy": "73186051597795329",
"name": "Example Microtenant 1",
"enabled": true,
"operator": "OR",
"criteriaAttribute": "AuthDomain",
"criteriaAttributeValues": [
"dummytest-365.in",
"dummytest.c3.com"
]
},
{
"id": "73186051597800358",
"modifiedTime": "1667566039",
"creationTime": "1666168946",
"modifiedBy": "73186051597795329",
"name": "Example Microtenant 2",
"enabled": true,
"operator": "OR",
"criteriaAttribute": "AuthDomain",
"criteriaAttributeValues": [
"dummytestad.com"
]
},
{
"id": "73186051597800399",
"modifiedTime": "1667566034",
"creationTime": "1666207734",
"modifiedBy": "73186051597795329",
"name": "Example Microtenant 3",
"enabled": true,
"operator": "OR",
"criteriaAttribute": "AuthDomain",
"criteriaAttributeValues": [
"dummytest.org"
]
},
{
"id": "73186051597800513",
"modifiedTime": "1669223724",
"modifiedBy": "72057594038052595",
"name": "Example Test Microtenant",
"description": "Example Microtenant",
"enabled": false,
"operator": "OR",
"criteriaAttribute": "AuthDomain",
"criteriaAttributeValues": [
"dummytest.com",
"dummytest.co.in"
]
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details for a Particular Microtenant
To get details for a particular Microtenant:
- Send a `GET` request to the following endpoint in the Microtenant controller: `/mgmtconfig/v1/admin/customers/{customerId}/microtenants/{microtenantId}`.
- Provide the following in the request endpoint:
- `name`: The name of the Microtenant.
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The Microtenant ID for the particular Microtenant that was captured in the [Getting Details for All Microtenants](#GettingAllMicrotenants) section.
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/microtenants/72057594038621068`.
- [View an example response](#ViewExample2)
[]{
"id": "72057594038621068",
"creationTime": "1663791107",
"modifiedBy": "72057594038052745",
"name": "Example Microtenant1",
"enabled": false,
"operator": "OR",
"criteriaAttribute": "AuthDomain",
"criteriaAttributeValues": [
"1467901757270.com"
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Name and ID for All Microtenants
To get the name and ID for all Microtenants:
- Send a `GET` request to the following endpoint in the Microtenant controller: `/mgmtconfig/v1/admin/customers/{customerId}/microtenants/summary`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057594037927936/microtenants/summary`.
- [View an example response](#ViewExample3)
[][
{
"id": "72057594038621068",
"name": "Microtenant1"
},
{
"id": "72057594038622872",
"name": "security-new"
},
{
"name": "default"
}
]
A successful response returns code 200. To learn more, see [About Error Codes](/zpa/about-error-codes).
Getting Details of User Session and User Microtenant ID
To get details of a user session and a user Microtenant ID, send a `GET` request to the following endpoint in the Microtenant controller: `/mgmtconfig/v1/admin/me`.
- [View an example response](#ViewExample4)
[]{
"customerId": "72057594037927936",
"customerName": "zscaler",
"microtenantName": "default"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Creating a Microtenant
The ability to create a Microtenant is only supported for Default Microtenant admins.
To create a Microtenant:
- Send a `POST` request to the following endpoint in the Microtenant controller: `/mgmtconfig/v1/admin/customers/{customerId}/microtenants`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057594037927936/microtenants`.
- Use the following JSON payload to update a Microtenant and provide the following information about the Microtenant:
- `name`: The name of the Microtenant.
- `criteriaAttribute`: The criteria attribute for the Microtenant(i.e., `AuthDomain`).
- `criteriaAttributeValues`: The value for the criteria attribute (i.e., valid authentication domains configured for a customer).
You choose the Microtenant criteria in the JSON payload. Refer to the [Adding Field Descriptions](#fieldDescriptions) section for supported values.
- [View the JSON payload](#ViewJson2)
[]{
"creationTime": 0,
"criteriaAttribute": "string",
"criteriaAttributeValues": [
"string"
],
"description": "string",
"enabled": true,
"id": "string",
"modifiedBy": "string",
"modifiedTime": 0,
"name": "string",
"priority": 0
}
- [View the sample JSON payload](#ViewSampleJson2)
[]{
"name":"Example Microtenant",
"enabled":false,
"description":"Example Microtenant",
"criteriaAttribute":"AuthDomain",
"criteriaAttributeValues":[
"dummytest.com",
"dummytest.co.in"
]
}
- [View an example response](#ViewExample5)
[]{
"id": "73186051597800513",
"creationTime": "1669222935",
"modifiedBy": "72057594038052595",
"name": "Example Microtenant",
"description": "Example Microtenant",
"enabled": false,
"operator": "OR",
"criteriaAttribute": "AuthDomain",
"criteriaAttributeValues": [
"dummytest.com",
"dummytest.co.in"
],
"user": {
"id": "73186051597800514",
"username": "mtAdmin_73186051597800513@dummytest.com",
"displayName": "Zscaler Private Access Scope Administrator",
"email": "mtAdmin_73186051597800513@dummytest.com",
"password": "#<6I!7WE",
"roleId": "12",
"forcePwdChange": true,
"localLoginDisabled": false,
"pinSession": true,
"isLocked": false,
"microtenantId": "73186051597800513"
}
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the Microtenant use cases:
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| name | The name of the Microtenant | Yes | String |
| enabled | Whether the Microtenant is enabled or not | No | Boolean: `true`, `false` |
| description | The description of the Microtenant | No | String |
| criteriaAttribute | The criteria attribute for the Microtenant | Yes | Supported value: `AuthDomain` |
| criteriaAttributeValues | The value for the criteria attribute. This is the valid authentication domains configured for a customer (e.g., `ExampleAuthDomain.com`). | Yes | String |
| filterBy | This indicates the filter, the operator, and the value for the filter | Yes | Array of attributes (i.e., `filterName`, `operator`, `values`) |
| filterName | The name of the filter | Yes | String |
| operator | The operator of the Microtenant | Yes | StringSupported values: `EQ` (Equals), `LIKE` (Contains), and `NQ` (Not Equals) |
| values | The values for the filter | No | String |
| pageBy | This indicates the page and page size | No | Array of attributes (i.e., `page` and `pageSize`) |
| page | This indicates the page | No | Integer |
| pageSize | This indicates the page size. If not provided, the default page size is 20. The max page size is 500. | No | Integer |
| sortBy | This indicates the sort name and sort order | No | Array of attributes (i.e., `sortName` and `SortOrder`) |
Updating a Microtenant
The ability to update a Microtenant is only supported for Default Microtenant admins.
To update a Microtenant:
- Send a `PUT` request to the following endpoint in the Microtenant controller: `/mgmtconfig/v1/admin/customers/{customerId}/microtenants/{microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The Microtenant ID for the particular Microtenant you want to update.
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/microtenants/72057594038621068`.
- Use the following JSON payload to update a Microtenant and provide the following information about the Microtenant:
- `Name`: The name of the Microtenant.
- `criteriaAttribute`: The criteria attribute for the Microtenant(i.e., `AuthDomain`).
- `criteriaAttributeValues`: The value for the criteria attribute (i.e., valid authentication domains configured for a customer).
- [View the JSON payload](#ViewJson3)
[]{
"creationTime": 0,
"criteriaAttribute": "string",
"criteriaAttributeValues": [
"string"
],
"description": "string",
"enabled": true,
"id": "string",
"modifiedBy": "string",
"modifiedTime": 0,
"name": "string",
"priority": 0
}
- [View a sample JSON payload](#ViewSampleJson3)
[]{
"name":"Test Microtenant",
"enabled":false,
"description":"Example Microtenant",
"criteriaAttribute":"AuthDomain",
"criteriaAttributeValues":[
"dummytest.com",
"dummytest.co.in"
]
}
A successful response yields code 204, meaning the Microtenant is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting a Microtenant
To delete a Microtenant:
- Send a `DELETE` request to the following endpoint in the Microtenant controller: `/mgmtconfig/v1/admin/customers/{customerId}/microtenants/{microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The Microtenant ID for the particular Microtenant you want to delete.
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/microtenants/72057594038621068`.
A successful response yields code 204, meaning the Microtenant is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting the Details of Your Current Session
To get the details of your current session, send a `GET` request to the following endpoint in the Microtenant controller: `/mgmtconfig/v1/admin/me`.
- [View an example response](#GetSessionExample)
[]
`{
"customerId": "72057594037927936",
"customerName": "Zscaler - Example User - safemarch.com",
"microtenantId": "72057594038621068”
"microtenantName": "Example Microtenant"
}    `
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).