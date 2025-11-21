# Configuring Privileged Consoles Using API
Source: https://help.zscaler.com/zpa/configuring-privileged-consoles-using-api
PDF: https://help.zscaler.com/pdf/com/en/1485916.pdf

This article provides information on managing Zscaler Private Access (ZPA) privileged consoles using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Prerequisite API Calls
Before creating a new privileged console, you must get details of the application segment that has Privileged Remote Access (PRA) enabled. To learn more, see [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api).
Creating a New Privileged Console
To create a new privileged console:
- Send a `POST` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/praConsole` in the Privileged Console Controller.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/praConsole`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following in the request body:
- The name of the privileged console.
- The details of the application that has PRA enabled. The `praApplication` model is highlighted in red.
- [View the JSON payload](#PostPayload)
[]{
"enabled": true,
"name": "string",
"praApplication": {
"appId": 0,
"applicationPort": 0,
"applicationProtocol": "HTTP",
"connectionSecurity": "ANY",
"domain": "string",
"enabled": true,
"hidden": true,
"id": 0,
"name": "string"
},
"praPortals": [
{
"certificateId": 0,
"certificateName": "string",
"domain": "string",
"enabled": true,
"id": 0,
"name": "string",
"userNotificationEnabled": true
}
]
}
- [View an example JSON payload](#samplePostPayload)
[][
{
"enabled":true,
"name":"Test PRA Console",
"description":"",
"PraPortals":[
{
"id":"72057594038076717",
"modifiedTime":"1651391898",
"creationTime":"1651391879",
"modifiedBy":"72057594038073668",
"name":"Test",
"enabled":true,
"certificateId":"72057594038037594",
"certificateName":"1daycert1",
"cName":"72057594038076717.72057594037927936.pra.d.zpa-app.net",
"domain":"testurl.com",
"userNotification":"Welcome :",
"userNotificationEnabled":true
}
],
"PraApplication":{
"id":"72057594038656944"
}
}
]
- [View an example response](#samplePostResponse)
[][
{
"id":"72057594038660861",
"modifiedTime":"1686678719",
"creationTime":"1686678719",
"modifiedBy":"72057594038040687",
"name":"Test PRA Console",
"enabled":true,
"PraApplication":{
"id":"72057594038656944",
"modifiedTime":"1685472255",
"creationTime":"1685472255",
"modifiedBy":"72057594038609323",
"name":"pra-app-add",
"enabled":true,
"domain":"pra-app-add",
"appId":"72057594038656942",
"hidden":false,
"applicationProtocol":"SSH",
"applicationPort":"22"
},
"PraPortals":[
{
"id":"72057594038076717",
"modifiedTime":"1651391898",
"creationTime":"1651391879",
"modifiedBy":"72057594038073668",
"name":"Test",
"enabled":true,
"certificateId":"72057594038037594",
"certificateName":"1daycert1",
"cName":"72057594038076717.72057594037927936.pra.d.zpa-app.net",
"domain":"testurl.com",
"userNotification":"Welcome :",
"userNotificationEnabled":true
}
]
}
]
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Microtenant Support
To create a new privileged console within a Microtenant:
- Send a `POST` request to the following endpoint in the Privileged Console Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praConsole?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `mgmtconfig/v1/admin/customers/145260601092866048/praConsole?microtenantId=145260601092866314`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following in the request body:
- The name of the privileged console.
- The ID of the application that has PRA enabled.
- [View the JSON payload](#postRequestMicrotenantPayload)
[]
`{
"enabled": true,
"name": "string",
"praApplication": {
"id": 0
},
"praPortals": [
{
"id": 0
}
]
}`
- [View a sample JSON payload](#samplePayloadPostMicrotenant)
[]
`{
"enabled": true,
"name": "10.10.10.10",
"description": "",
"praPortals": [
{
"id": "145260601092866325"
}
],
"praApplication": {
"id": "145260601092866519"
}
}`
- [View an example response](#sampleResponsePostMicrotenant)
[]
`{
"id": "145260601092866537",
"modifiedTime": "1705617359",
"creationTime": "1705617359",
"modifiedBy": "145260601092866482",
"name": "10.10.10.10",
"enabled": true,
"praApplication": {
"id": "145260601092866519",
"modifiedTime": "1705615436",
"creationTime": "1705083996",
"modifiedBy": "145260601092866482",
"name": "10.10.10.10",
"enabled": true,
"domain": "10.10.10.10",
"appId": "145260601092866518",
"hidden": false,
"applicationProtocol": "SSH",
"applicationPort": "22",
"microtenantName": "Default"
},
"praPortals": [
{
"id": "145260601092866325",
"enabled": true
}
],
"microtenantId": "145260601092866314"
}`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Creating a List of PRA Consoles
To create a list of PRA consoles:
- Send a `POST` request to the following endpoint in the Privileged Console Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praConsole/bulk`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/praConsole/bulk`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following in the request body:
- The name of the privileged console.
- The ID of the application that has PRA enabled.
- [View the JSON payload](#bulkPostPayload)
[][
{
"enabled": true,
"name": "string",
"praApplication": {
"appId": 0,
"applicationPort": 0,
"applicationProtocol": "HTTP",
"connectionSecurity": "ANY",
"domain": "string",
"enabled": true,
"hidden": true,
"id": 0,
"name": "string"
},
"praPortals": [
{
"certificateId": 0,
"certificateName": "string",
"domain": "string",
"enabled": true,
"id": 0,
"name": "string",
"userNotificationEnabled": true
}
]
}
]
- [View an example JSON payload](#bulkPostSamplePayload)
[][
{
"enabled": true,
"name": "testvnc.com",
"description": "",
"praPortals": [
{
"id": "289370814522851478",
"creationTime": "1649156687",
"modifiedBy": "72057594038050500",
"name": "test2",
"enabled": true,
"certificateId": "289370814522851367",
"certificateName": "portaltest",
"cName": "289370814522851478.289370814522851328.h.d.zpa-app.net",
"domain": "portalabc.com",
"userNotificationEnabled": false
}
],
"praApplication": {
"id": "289370814522851493"
}
}
]
- [View an example response](#bulkPostResponse)
[][
{
"id": "289370814522851639",
"creationTime": "1668439345",
"modifiedBy": "72057594038624153",
"name": "testvnc.com",
"enabled": true,
"praApplication": {
"id": "289370814522851493",
"creationTime": "1654158837",
"modifiedBy": "72057594038050500",
"name": "testvnc.com",
"enabled": true,
"domain": "testvnc.com",
"appId": "289370814522851492",
"hidden": false,
"applicationProtocol": "SSH",
"applicationPort": "22"
},
"praPortals": [
{
"id": "289370814522851478",
"creationTime": "1649156687",
"modifiedBy": "72057594038050500",
"name": "test2",
"enabled": true,
"certificateId": "289370814522851367",
"certificateName": "portaltest",
"cName": "289370814522851478.289370814522851328.h.d.zpa-app.net",
"domain": "portalabc.com",
"userNotificationEnabled": false
}
]
}
]
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
To create a list of PRA consoles within a Microtenant:
- Send a `POST` request to the following endpoint in the Privileged Console Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praConsole/bulk?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/{customerId}/praConsole/bulk?microtenantId=145260601092866314`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following in the request body:
- The name of the privileged console.
- The ID of the application that has PRA enabled.
- The ID of the privileged portal.
- [View the minimum criteria JSON payload](#bulkPostConsolesMicrotenant)
[]
`[
{
"enabled": true,
"name": "string",
"microtenantName": "string",
"praApplication": {
"id": 0
},
"praPortals": [
{
"id": 0
}
]
}
]`
- [View the sample JSON payload](#samplePayloadBulkPostMicrotenant)
[]
`[
{
"enabled": true,
"name": "10.10.10.10",
"description": "",
"praPortals": [
{
"id": "145260601092866325"
}
],
"praApplication": {
"id": "145260601092866519"
}
}
]`
- [View an example response](#bulkPostResponseMicrotenant)
[]
`[
{
"id": "145260601092866538",
"modifiedTime": "1705618822",
"creationTime": "1705618822",
"modifiedBy": "145260601092866482",
"name": "10.10.10.10",
"enabled": true,
"praApplication": {
"id": "145260601092866519",
"modifiedTime": "1705615436",
"creationTime": "1705083996",
"modifiedBy": "145260601092866482",
"name": "10.10.10.10",
"enabled": true,
"domain": "10.10.10.10",
"appId": "145260601092866518",
"hidden": false,
"applicationProtocol": "SSH",
"applicationPort": "22",
"microtenantName": "Default"
},
"praPortals": [
{
"id": "145260601092866325",
"enabled": true
}
],
"microtenantId": "145260601092866314"
}
]`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of All PRA Consoles
To get details of all PRA consoles for a given customer:
- Send a `GET` request to the following endpoint in the Privileged Console Controller: `/mgmtconfig/v1/customers/{customerId}/praConsole`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
For example: `/mgmtconfig/v1/customers/145256180497776640/praConsole`.
- [View an example response](#GetConsolesResponse)
[]{
"id": "289370814522851651",
"creationTime": "1669638768",
"modifiedBy": "72057594038624153",
"name": "tsett.com",
"enabled": true,
"praApplication": {
"id": "289370814522851417",
"modifiedTime": "1637356774",
"creationTime": "1637356460",
"modifiedBy": "72057594038006701",
"name": "tsett.com",
"enabled": true,
"domain": "tsett.com",
"appId": "289370814522851416",
"hidden": false,
"applicationProtocol": "RDP",
"applicationPort": "3389",
"connectionSecurity": "TLS"
},
"praPortals": [
{
"id": "289370814522851473",
"modifiedTime": "1665565095",
"creationTime": "1642045470",
"modifiedBy": "72057594038620387",
"name": "test100",
"enabled": true,
"certificateId": "289370814522851367",
"certificateName": "portaltest",
"cName": "289370814522851473.289370814522851328.h.d.zpa-app.net",
"domain": "test100.com",
"userNotificationEnabled": true
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint in the Privileged Console Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praConsole?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId:` The ZPA tenant ID of the customer.
- Valid page and page size values.
For example: `/mgmtconfig/v1/customers/145256180497776640/praConsole?page=1&pagesize=20`.
- [View an example response](#GetConsolesPagResponse)
[]{
"totalPages": "1",
"list": [
{
"id": "145256180497776670",
"creationTime": "1639088246",
"modifiedBy": "72057594038048819",
"name": "eng-workstation.sahuhaus.local",
"enabled": true,
"praApplication": {
"id": "145256180497776669",
"creationTime": "1639088219",
"modifiedBy": "72057594038048819",
"name": "eng-workstation.sahuhaus.local",
"enabled": true,
"domain": "eng-workstation.sahuhaus.local",
"appId": "145256180497776668",
"hidden": false,
"applicationProtocol": "RDP",
"applicationPort": "3389",
"connectionSecurity": "ANY"
},
"praPortals": [
{
"id": "145256180497776653",
"modifiedTime": "1665520467",
"creationTime": "1636745350",
"modifiedBy": "72057594038006701",
"name": "ZeroTrust Dev Portal",
"enabled": true,
"description": "&<>",
"certificateId": "145256180497776652",
"domain": "portal-dev.zerotrust.to",
"userNotification": "Welcome to the OT Portal for the Houston Site!",
"userNotificationEnabled": true
}
]
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports Microtenants. To get details of all PRA consoles for a Microtenants:
- Send a `GET` request to the following endpoint in the Privileged Console Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praConsole?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId:` The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
- Valid page and page size values.
- [View an example response](#getConsolesExampleMicrotenant)
[]
`{
"totalPages": "1",
"totalCount": "1",
"list": [
{
"id": "145260601092866331",
"modifiedTime": "1698124810",
"creationTime": "1698124810",
"modifiedBy": "72057594038068982",
"name": "monica-scope-c-ssh.com",
"enabled": true,
"praApplication": {
"id": "145260601092866329",
"modifiedTime": "1698124747",
"creationTime": "1698124747",
"modifiedBy": "72057594038068982",
"name": "monica-scope-c-ssh.com",
"enabled": true,
"domain": "monica-scope-c-ssh.com",
"appId": "145260601092866327",
"hidden": false,
"applicationProtocol": "SSH",
"applicationPort": "22",
"microtenantId": "145260601092866314"
},
"praPortals": [
{
"id": "145260601092866325",
"modifiedTime": "1698124586",
"creationTime": "1698124586",
"modifiedBy": "72057594038068982",
"name": "Scope C Portal",
"enabled": true,
"certificateId": "145260601092866074",
"domain": "pra-portal-otdev-scope-c.com",
"userNotificationEnabled": false,
"microtenantId": "145260601092866314"
}
],
"microtenantId": "145260601092866314"
}
]
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details of a Particular Privileged Console
To get a particular PRA console configured for a given customer:
- Send a `GET` request to the following endpoint in the Privileged Console Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praConsole/{id}`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
For example: `mgmtconfig/v1/admin/customers/289370814522851328/praConsole/289370814522851460`.
- [View an example response](#GetConsoleResponse)
[]{
"id": "289370814522851460",
"creationTime": "1637816978",
"modifiedBy": "72057594038006701",
"name": "10.12.12.23",
"enabled": true,
"praApplication": {
"id": "289370814522851443",
"creationTime": "1637438036",
"modifiedBy": "72057594038006701",
"name": "10.12.12.23",
"enabled": true,
"domain": "10.12.12.23",
"appId": "289370814522851442",
"hidden": false,
"applicationProtocol": "RDP",
"applicationPort": "3389",
"connectionSecurity": "ANY"
},
"praPortals": [
{
"id": "289370814522851476",
"modifiedTime": "1665563899",
"creationTime": "1646066550",
"modifiedBy": "72057594038050500",
"name": "portaltest",
"enabled": true,
"description": "ab&<>c",
"certificateId": "289370814522851367",
"domain": "portaltest.com",
"userNotificationEnabled": false
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports getting details for a PRA console within a Microtenant. To get details for a PRA console within a Microtenant:
- Send a GET request to the following endpoint in the Privileged Console Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praConsole/{id}?microtenantId={microtenantId}`
- Provide the following in the request endpoint:
- `customerId:` The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/{customerId}/praConsole/{id}?microtenantId=145260601092866314`.
- [View an example response](#getRequestConsoleMicrotenant)
[]
`{
"id": "145260601092866536",
"modifiedTime": "1705608783",
"creationTime": "1705608783",
"modifiedBy": "145260601092866482",
"name": "10.10.10.10",
"enabled": true,
"praApplication": {
"id": "145260601092866519",
"modifiedTime": "1705083996",
"creationTime": "1705083996",
"modifiedBy": "72057594038608958",
"name": "10.10.10.10",
"enabled": true,
"domain": "10.10.10.10",
"appId": "145260601092866518",
"hidden": false,
"applicationProtocol": "SSH",
"applicationPort": "22"
},
"praPortals": [
{
"id": "145260601092866325",
"modifiedTime": "1698124586",
"creationTime": "1698124586",
"modifiedBy": "72057594038068982",
"name": "Scope C Portal",
"enabled": true,
"certificateId": "145260601092866074",
"domain": "pra-portal-otdev-scope-c.com",
"userNotificationEnabled": false,
"microtenantId": "145260601092866314"
}
],
"microtenantId": "145260601092866314"
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Privileged Consoles for a Privileged Portal
To get privileged consoles for the given privileged portal:
- Send a `GET` request to the following endpoint in the Privileged Console Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praConsole/praPortal/{portalId}`.
- Provide the following in the request endpoint:
- `customerId:` The ZPA tenant ID of the customer.
- `portalId`: The unique identifier of the privileged portal. To learn more, see [Configuring Privileged Portals Using API](/zpa/configuring-privileged-portals-using-api).
- Valid page and page size values.
For example: `mgmtconfig/v1/admin/customers/145256180497776640/praConsole/praPortal/145256180497776653?page=1&pagesize=20`.
- [View an example response](#GetConsolesPerPortalResponse)
[]{
"totalPages": "1",
"list": [
{
"id": "145256180497776908",
"creationTime": "1675971235",
"modifiedBy": "72057594038006701",
"name": "1.1.1.122",
"enabled": true,
"praApplication": {
"id": "145256180497776887",
"modifiedTime": "1674584300",
"creationTime": "1674584177",
"modifiedBy": "72057594038006701",
"name": "1.1.1.122",
"enabled": true,
"domain": "1.1.1.122",
"appId": "145256180497776882",
"hidden": false,
"applicationProtocol": "SSH",
"applicationPort": "22"
},
"praPortals": [
{
"id": "145256180497776653",
"modifiedTime": "1665520467",
"creationTime": "1636745350",
"modifiedBy": "72057594038006701",
"name": "Example Sample Portal",
"enabled": true,
"description": "&<>",
"certificateId": "145256180497776652",
"domain": "portal-sample.example.to",
"userNotification": "Welcome to the OT Portal for the Houston Site!",
"userNotificationEnabled": true
}
]
},
{
"id": "145256180497776670",
"creationTime": "1639088246",
"modifiedBy": "72057594038048819",
"name": "example-workstation.sample.local",
"enabled": true,
"praApplication": {
"id": "145256180497776669",
"creationTime": "1639088219",
"modifiedBy": "72057594038048819",
"name": "example-workstation.sample.local",
"enabled": true,
"domain": "example-workstation.sample.local",
"appId": "145256180497776668",
"hidden": false,
"applicationProtocol": "RDP",
"applicationPort": "3389",
"connectionSecurity": "ANY"
},
"praPortals": [
{
"id": "145256180497776653",
"modifiedTime": "1665520467",
"creationTime": "1636745350",
"modifiedBy": "72057594038006701",
"name": "Example Sample Portal",
"enabled": true,
"description": "&<>",
"certificateId": "145256180497776652",
"domain": "portal-sample.example.to",
"userNotification": "Welcome to the Sample Portal for the Example Site!",
"userNotificationEnabled": true
}
]
},
{
"id": "145256180497776903",
"creationTime": "1675726124",
"modifiedBy": "72057594038006701",
"name": "testapp4.com",
"enabled": true,
"praApplication": {
"id": "145256180497776776",
"modifiedTime": "1666224661",
"creationTime": "1666224569",
"modifiedBy": "72057594038006701",
"name": "testapp4.com",
"enabled": true,
"domain": "testapp4.com",
"appId": "145256180497776741",
"hidden": false,
"applicationProtocol": "SSH",
"applicationPort": "22"
},
"praPortals": [
{
"id": "145256180497776653",
"modifiedTime": "1665520467",
"creationTime": "1636745350",
"modifiedBy": "72057594038006701",
"name": "Sample Example Portal",
"enabled": true,
"description": "&<>",
"certificateId": "145256180497776652",
"domain": "portal-sample.example.to",
"userNotification": "Welcome to the Sample Portal for the Example Site!",
"userNotificationEnabled": true
}
]
},
{
"id": "145256180497776900",
"creationTime": "1675726036",
"modifiedBy": "72057594038006701",
"name": "testapp5.com",
"enabled": true,
"praApplication": {
"id": "145256180497776778",
"creationTime": "1666289492",
"modifiedBy": "72057594038006701",
"name": "testapp5.com",
"enabled": true,
"domain": "testapp5.com",
"appId": "145256180497776777",
"hidden": false,
"applicationProtocol": "SSH",
"applicationPort": "22"
},
"praPortals": [
{
"id": "145256180497776653",
"modifiedTime": "1665520467",
"creationTime": "1636745350",
"modifiedBy": "72057594038006701",
"name": "Sample Example Portal",
"enabled": true,
"description": "&<>",
"certificateId": "145256180497776652",
"domain": "portal-example.sample.to",
"userNotification": "Welcome to the Example Portal for the Sample Site!",
"userNotificationEnabled": true
}
]
},
{
"id": "145256180497776906",
"creationTime": "1675729013",
"modifiedBy": "72057594038006701",
"name": "testapp.com",
"enabled": true,
"praApplication": {
"id": "145256180497776742",
"modifiedTime": "1667503708",
"creationTime": "1660089136",
"modifiedBy": "72057594038006701",
"name": "testapp.com",
"enabled": true,
"domain": "testapp.com",
"appId": "145256180497776741",
"hidden": false,
"applicationProtocol": "SSH",
"applicationPort": "22"
},
"praPortals": [
{
"id": "145256180497776653",
"modifiedTime": "1665520467",
"creationTime": "1636745350",
"modifiedBy": "72057594038006701",
"name": "Example Sample Portal",
"enabled": true,
"description": "&<>",
"certificateId": "145256180497776652",
"domain": "portal-example.sample.to",
"userNotification": "Welcome to the Sample Portal for the Example Site!",
"userNotificationEnabled": true
}
]
},
{
"id": "145256180497776905",
"creationTime": "1675729013",
"modifiedBy": "72057594038006701",
"name": "test-vnc.com",
"enabled": true,
"praApplication": {
"id": "145256180497776787",
"creationTime": "1667517421",
"modifiedBy": "72057594038006701",
"name": "test-vnc.com",
"enabled": true,
"domain": "test-vnc.com",
"appId": "145256180497776786",
"hidden": false,
"applicationProtocol": "VNC",
"applicationPort": "5900"
},
"praPortals": [
{
"id": "145256180497776653",
"modifiedTime": "1665520467",
"creationTime": "1636745350",
"modifiedBy": "72057594038006701",
"name": "Sample Portal",
"enabled": true,
"description": "&<>",
"certificateId": "145256180497776652",
"domain": "portal-example.sample.to",
"userNotification": "Welcome to the OT Portal for the Houston Site!",
"userNotificationEnabled": true
}
]
},
{
"id": "145256180497776667",
"creationTime": "1639086676",
"modifiedBy": "72057594038048819",
"name": "ubuntu-desktop.example.local",
"enabled": true,
"praApplication": {
"id": "145256180497776660",
"modifiedTime": "1639086121",
"creationTime": "1636745998",
"modifiedBy": "72057594038048819",
"name": "ubuntu-desktop.example.local",
"enabled": true,
"domain": "ubuntu-desktop.example.local",
"appId": "145256180497776659",
"hidden": false,
"applicationProtocol": "SSH",
"applicationPort": "22"
},
"praPortals": [
{
"id": "145256180497776653",
"modifiedTime": "1665520467",
"creationTime": "1636745350",
"modifiedBy": "72057594038006701",
"name": "ZeroTrust Dev Portal",
"enabled": true,
"description": "&<>",
"certificateId": "145256180497776652",
"domain": "portal-example.sample.to",
"userNotification": "Welcome to the Sample Portal for the Example Site!",
"userNotificationEnabled": true
}
]
},
{
"id": "145256180497776972",
"creationTime": "1682681529",
"modifiedBy": "72057594038624153",
"name": "zscaler.com",
"enabled": true,
"praApplication": {
"id": "145256180497776971",
"creationTime": "1682681448",
"modifiedBy": "72057594038624153",
"name": "zscaler.com",
"enabled": true,
"domain": "zscaler.com",
"appId": "145256180497776970",
"hidden": false,
"applicationProtocol": "SSH",
"applicationPort": "22"
},
"praPortals": [
{
"id": "145256180497776653",
"modifiedTime": "1665520467",
"creationTime": "1636745350",
"modifiedBy": "72057594038006701",
"name": "Example Sample Portal",
"enabled": true,
"description": "&<>",
"certificateId": "145256180497776652",
"domain": "portal-sample.example.to",
"userNotification": "Welcome to the sSample Portal for the Example Site!",
"userNotificationEnabled": true
}
]
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Privileged Console
To update a privileged console:
- Send a `PUT` request to the following endpoint in the Privileged Console Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praConsole/{id}`.
- Provide the following in the request endpoint:
- `customerId:` The ZPA tenant ID of the customer.
- `portalId`: The unique identifier of the privileged portal. To learn more, see [Configuring Privileged Portals Using API](/zpa/configuring-privileged-portals-using-api).
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/praConsole/289370814522851640`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following in the request body:
- The name of the privileged console.
- The ID of the application that has PRA enabled.
- The ID of the privileged portal.
- [View the JSON payload](#UpdateConsolePayload)
[]{
"enabled": true,
"name": "string",
"praApplication": {
"appId": 0,
"applicationPort": 0,
"applicationProtocol": "HTTP",
"connectionSecurity": "ANY",
"domain": "string",
"enabled": true,
"hidden": true,
"id": 0,
"name": "string"
},
"praPortals": [
{
"certificateId": 0,
"domain": "string",
"enabled": true,
"id": 0,
"name": "string",
"userNotificationEnabled": true
}
]
}
- [View the sample JSON payload](#samplePutJsonPayload)
[]{
"enabled": true,
"port": "3389",
"protocol": "RDP",
"id": "289370814522851640",
"creationTime": "1668441154",
"modifiedBy": "72057594038624153",
"name": "tsett.com",
"praApplication": {
"id": "289370814522851417",
"modifiedTime": "1637356774",
"creationTime": "1637356460",
"modifiedBy": "72057594038006701",
"name": "tsett.com",
"enabled": true,
"domain": "tsett.com",
"appId": "289370814522851416",
"hidden": false,
"applicationProtocol": "RDP",
"applicationPort": "3389",
"connectionSecurity": "TLS"
},
"praPortals": [
{
"id": "289370814522851473"
}
],
"link": "tsett.com",
"connectionSecurity": "TLS",
"description": "Test Console"
}
A successful response returns code 204, meaning the update was successful. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports updating a privileged console within a Microtenant. To update a privileged console within a Microtenant:
- Send a `PUT` request to the following endpoint in the Privileged Console Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praConsole/{id}?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId:` The ZPA tenant ID of the customer.
- `id`: The unique identifier of the privileged console.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145260601092866048/praConsole/145260601092866536?microtenantId=145260601092866314`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following in the request body:
- The name of the privileged console.
- The details of the application that has PRA enabled.
- The unique identifier of the privileged portal.
- [View the minimum criteria JSON payload](#minimumCriteriaPutRequestMicrotenant)
[]
`{
"enabled": true,
"name": "string",
"microtenantId": "string",
"praApplication": {
"id": 0,
},
"praPortals": [
{
"id": 0
}
]
}`
- [View the sample JSON payload](#samplePayloadPutMicrotenant)
[]
`{
"id": "145260601092866536",
"modifiedTime": "1705613297",
"creationTime": "1705608783",
"modifiedBy": "72057594038608958",
"name": "10.10.10.10",
"enabled": true,
"description": "PRA Console",
"praApplication": {
"id": "145260601092866519",
"modifiedTime": "1705083996",
"creationTime": "1705083996",
"modifiedBy": "72057594038608958",
"name": "10.10.10.10",
"enabled": true,
"domain": "10.10.10.10",
"appId": "145260601092866518",
"hidden": false,
"applicationProtocol": "SSH",
"applicationPort": "22"
},
"praPortals": [
{
"id": "145260601092866325",
"modifiedTime": "1698124586",
"creationTime": "1698124586",
"modifiedBy": "72057594038068982",
"name": "Scope C Portal",
"enabled": true,
"certificateId": "145260601092866074",
"domain": "pra-portal-example-scope-c.com",
"userNotificationEnabled": false,
"microtenantId": "145260601092866314"
}
],
"microtenantId": "145260601092866314"
}`
A successful response returns code 204, meaning the update was successful. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting a Privileged Console
To delete a privileged console:
- Send a `DELETE` request to the following endpoint in the Privileged Console Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praConsole/{id}`.
- Provide the following in the request endpoint:
- `customerId:` The ZPA tenant ID of the customer.
- `consoleId`: The unique identifier of the privileged console. To learn more, see [Getting Details of a Particular Privileged Console](#getConsoles).
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/praConsole/289370814522851640`.
A successful response returns code 204 `No Content`, meaning the delete was successful. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API provides support to delete a privileged console within a Microtenant. To delete a privileged console within a Microtenant:
- Send a `DELETE` request to the following endpoint in the Privileged Console Controller: `/mgmtconfig/v1/admin/customers/{customerId}/praConsole/{id}?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId:` The ZPA tenant ID of the customer.
- `consoleId`: The unique identifier of the privileged console. To learn more, see [Getting Details of a Particular Privileged Console](#getConsoles).
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/praConsole/289370814522851640?microtenantId=145260601092866314`.
A successful response returns code 204, meaning the delete was successful. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the privileged console use cases:
[](/zpa/about-microtenants)[](/zpa/about-api-keys)[](/zpa/configuring-microtenants-using-api)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| customerId | The unique identifier of the ZPA tenant | Yes | Integer |
| page | Specifies the page number | No | Integer |
| pageSize | Specifies the page size | No | Integer |
| search | Indicates the search string used to support search by features or fields | No | String |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. Pass `microtenantId` as null to retrieve data from all customers associated with the tenant. If the `microtenantId` is not passed in the request endpoint when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |