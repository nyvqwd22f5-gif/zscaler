# Configuring Privileged Portals Using API
Source: https://help.zscaler.com/zpa/configuring-privileged-portals-using-api
PDF: https://help.zscaler.com/pdf/com/en/1485921.pdf

This article provides information on managing Zscaler Private Access (ZPA) privileged portals using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Creating a New Privileged Portal
To create a new privileged portal for a given customer:
- Send a POST request to the following endpoint in the Privileged Portal Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praPortal`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
For example: `mgmtconfig/v1/admin/customers/289370814522851328/praPortal`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following in the request body:
- The name of the privileged portal.
- The unique identifier of the certificate.
- The domain of the privileged portal.
- [View the JSON payload](#PostPayload)
[]{
"certificateId":0,
"domain":"string",
"enabled":true,
"name":"string",
"userNotificationEnabled":false
}
- [View an example JSON payload](#examplePostPayload)
[]{
"enabled":true,
"name":"testPortal12",
"domain":"testPortal12",
"userNotificationEnabled":false,
"certificateId":"289370814522851367"
}
- [View an example response](#postResponse)
[]{
"id":"289370814523661112",
"modifiedTime":"1684403355",
"creationTime":"1684403355",
"modifiedBy":"145256180497777000",
"name":"testPortal12",
"enabled":true,
"certificateId":"289370814522851367",
"domain":"testportal12",
"userNotificationEnabled":false
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Microtenant Support
To create a privileged portal in a Microtenant:
- Send a `POST` request to the following endpoint in the Privileged Portal Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praPortal?microtenantId=<microtenantId>`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/praPortal?microtenantId=145260601092866314`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following in the request body:
- The name of the privileged portal.
- The unique identifier of the certificate.
- The domain of the privileged portal.
- [View the JSON payload](#MicrotenantPostPayload)
[]{
"certificateId":0,
"domain":"string",
"enabled":true,
"name":"string",
"userNotificationEnabled":false
}
- [View an example JSON payload](#exampleMicrotenantPostPayload)
[]{
"enabled":true,
"name":"testPortal12",
"domain":"testPortal12",
"userNotificationEnabled":false,
"certificateId":"289370814522851367"
}
- [View an example response](#postMicrotenantResponse)
[]{
"id":"145260601092866514",
"modifiedTime":"1704924637",
"creationTime":"1704924637",
"modifiedBy":"145260601092866482",
"name":"public-api",
"enabled":true,
"certificateId":"145260601092866074",
"domain":"public-api.com",
"userNotificationEnabled":false,
"microtenantId":"145260601092866314"
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details of All Privileged Portals
To get all privileged portals that are configured for a customer:
- Send a GET request to the following endpoint in the Privileged Portal Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praPortal`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
For example: `mgmtconfig/v1/admin/customers/217246660302995456/praPortal`.
- [View an example response](#GetPortalsResponse)
[]{
"totalPages":"1",
"list":[
{
"id":"217246660303026030",
"creationTime":"1642122047",
"modifiedBy":"72057594038008981",
"name":"TestPriviledgePortal",
"enabled":true,
"description":"Priviledge Portal",
"certificateId":"217246660303022046",
"certificateName":"CN=*.mockcompany.com,O=Zscaler,ST=California,C=US",
"cName":"217246660303026030.217246660302995456.pra.d.zpa-app.net",
"domain":"Testpriviledgeportal.com",
"userNotificationEnabled":false
},
{
"id":"217246660303026391",
"modifiedTime":"1652836201",
"creationTime":"1652836184",
"modifiedBy":"72057594038071293",
"name":"TestPRAExporter1",
"enabled":true,
"certificateId":"217246660303022046",
"certificateName":"CN=*.mockcompany.com,O=Zscaler,ST=California,C=US",
"cName":"217246660303026391.217246660302995456.pra.d.zpa-app.net",
"domain":"Testpraexp1.com",
"userNotificationEnabled":false
},
{
"id":"217246660303026335",
"modifiedTime":"1652836155",
"creationTime":"1650420269",
"modifiedBy":"72057594038071293",
"name":"TestPRAExporter2",
"enabled":true,
"certificateId":"217246660303022046",
"certificateName":"CN=*.mockcompany.com,O=Zscaler,ST=California,C=US",
"cName":"217246660303026335.217246660302995456.pra.d.zpa-app.net",
"domain":"Testpraexp2.com",
"userNotificationEnabled":false
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a GET request to the following endpoint in the Privileged Portal Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praPortal?page=1&pagesize=20`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/praPortal?page=1&pagesize=2`.
- [View an example response](#getPagPortals)
[]{
"totalPages":"2",
"list":[
{
"id":"217246660303026030",
"creationTime":"1642122047",
"modifiedBy":"72057594038008981",
"name":"TestPriviledgePortal",
"enabled":true,
"description":"Priviledge Portal",
"certificateId":"217246660303022046",
"certificateName":"CN=*.mockcompany.com,O=Zscaler,ST=California,C=US",
"cName":"217246660303026030.217246660302995456.pra.d.zpa-app.net",
"domain":"Testpriviledgeportal.com",
"userNotificationEnabled":false
},
{
"id":"217246660303026391",
"modifiedTime":"1652836201",
"creationTime":"1652836184",
"modifiedBy":"72057594038071293",
"name":"TestPRAExporter1",
"enabled":true,
"certificateId":"217246660303022046",
"certificateName":"CN=*.mockcompany.com,O=Zscaler,ST=California,C=US",
"cName":"217246660303026391.217246660302995456.pra.d.zpa-app.net",
"domain":"Testpraexp1.com",
"userNotificationEnabled":false
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports Microtenants. To get details of all privileged portals within a Microtenant:
- Send a GET request to the following endpoint in the Privileged Portal Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praPortal?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `mgmtconfig/v1/admin/customers/145260601092866048/praPortal?microtenantId=145260601092866314`.
- [View an example response](#getPortalsMicrotenant)
[]
`{
"totalPages":"1",
"totalCount":"2",
"list":[
{
"id":"145260601092866113",
"modifiedTime":"1702537630",
"creationTime":"1693202870",
"modifiedBy":"72057594038073668",
"name":"OT Example Default Portal",
"enabled":true,
"description":"Hello!",
"certificateId":"145260601092866074",
"certificateName":"pra-portal-example.com",
"cName":"145260601092866113.145260601092866048.pra.d.zpa-app.net",
"domain":"pra-portal-otdev.com",
"userNotification":"TEST",
"userNotificationEnabled":true,
"microtenantName":"Default"
},
{
"id":"145260601092866325",
"modifiedTime":"1698124586",
"creationTime":"1698124586",
"modifiedBy":"72057594038068982",
"name":"Scope C Portal",
"enabled":true,
"certificateId":"145260601092866074",
"certificateName":"pra-portal-example.com",
"cName":"145260601092866325.145260601092866048.pra.d.zpa-app.net",
"domain":"pra-portal-sample-scope-c.com",
"userNotificationEnabled":false,
"microtenantId":"145260601092866314",
"microtenantName":"Scope C"
}
]
}    `
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of a Particular Privileged Portal
To get the details of a particular privileged portal for a given customer:
- Send a `GET` request to the following endpoint in the Privileged Portal Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praPortal/{id}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the privileged portal. To learn more, see [Getting Details of All Privileged Portals](#gettingPortals).
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/praPortal/289370814522851328`.
- [View an example response](#getPortalResponse)
[]{
"id":"289370814522851641",
"creationTime":"1668688130",
"modifiedBy":"72057594038624153",
"name":"kritest",
"enabled":true,
"description":"Sample portal",
"certificateId":"289370814522851367",
"certificateName":"portaltest",
"cName":"289370814522851641.289370814522851328.h.d.zpa-app.net",
"domain":"kritest.com",
"userNotificationEnabled":false
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports Microtenants. To get details of a particular privileged portal within a Microtenant:
- Send a `GET` request to the following endpoint in the Privileged Portal Controller: /mgmtconfig/v1/admin/customers/{customerId}/praPortal/{id}?microtenantId={microtenantId}.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant for the tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `mgmtconfig/v1/admin/customers/145260601092866048/praPortal/145260601092866514?microtenantId=145260601092866314`.
- [View an example response](#getPortalMicrotenant)
[]
`{
"id":"145260601092866514",
"modifiedTime":"1704924637",
"creationTime":"1704924637",
"modifiedBy":"145260601092866482",
"name":"public-api",
"enabled":true,
"certificateId":"145260601092866074",
"certificateName":"pra-portal-sample.com",
"cName":"145260601092866514.145260601092866048.pra.d.zpa-app.net",
"domain":"public-api.com",
"userNotificationEnabled":false,
"microtenantId":"145260601092866314",
"microtenantName":"Scope C"
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Privileged Portal
To update a privileged portal:
- Send a PUT request to the following endpoint in the Privileged Portal Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praPortal/{id}` .
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the privileged portal.
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/praPortal/289370814523661112`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following in the request body:
- The name of the privileged portal.
- The unique identifier of the certificate.
- The domain of the privileged portal.
- [View the JSON payload](#putPortalPayload)
[]{
"certificateId":0,
"domain":"string",
"enabled":true,
"name":"string",
"userNotificationEnabled":true
}
- [View an example JSON payload](#putSamplePayload)
[]{
"name":"testPortal123",
"enabled":true,
"certificateId":"289370814522851367",
"domain":"testportal12",
"userNotificationEnabled":false
}
A successful response returns code 204, meaning the update was successful. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports Microtenants. To update a privileged portal within a Microtenant:
- Send a `PUT` request to the following endpoint within the Privileged Portal Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praPortal/{id}?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/praPortal/289370814523661112?microtenantId=145260601092866314`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following in the request body:
- The name of the privileged portal.
- The unique identifier of the certificate.
- The domain of the privileged portal.
- [View the minimum criteria JSON payload](#putRequestPayloadMicrotenant)
[]
`{
"certificateId":0,
"domain":"string",
"enabled":true,
"name":"string",
"userNotificationEnabled":true
}`
- [View the sample payload](#samplePayloadPutMicrotenant)
[]
`{
"enabled":true,
"name":"public-api-edit",
"domain":"public-api.com",
"userNotificationEnabled":false,
"certificateId":"145260601092866074"
}`
A successful response returns code 204, meaning the update was successful. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting a Privileged Portal
To delete a privileged portal:
- Send a `DELETE` request to the following endpoint in the Privileged Portal Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praPortal/{id}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the privileged portal.
For example: `mgmtconfig/v1/admin/customers/289370814522851328/praPortal/289370814523661112`.
A successful response returns code 204, meaning the delete was successful. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports Microtenants. To delete a privileged portal within a Microtenant:
- Send a DELETE request to the following endpoint in the Privileged Portal Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praPortal/{id}?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `mgmtconfig/v1/admin/customers/289370814522851328/praPortal/289370814522851641?microtenantId=145260601092866314`.
A successful response returns code 204, meaning the delete was successful. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Field Descriptions
The following table includes descriptions of available fields you can use for the privileged portal use cases:
[](/zpa/about-microtenants)[](/zpa/about-api-keys)[](/zpa/configuring-microtenants-using-api)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| customerId | The unique identifier of the ZPA tenant | Yes | Integer |
| page | Specifies the page number | No | Integer |
| pageSize | Specifies the page size | No | Integer |
| search | Indicates the search string used to support search by features or fields | No | String |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. Pass `microtenantId` as null to retrieve data from all customers associated with the tenant. If the `microtenantId` is not passed in the request endpoint when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |