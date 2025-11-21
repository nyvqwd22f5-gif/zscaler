# Configuring Privileged Approvals Using API
Source: https://help.zscaler.com/zpa/configuring-privileged-approvals-using-api
PDF: https://help.zscaler.com/pdf/com/en/1485926.pdf

This article provides information on managing Zscaler Private Access (ZPA) privileged approvals using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Prerequisite API Call
Before creating a new privileged approval, you must get the ID of the application segments you want to include in the privileged approval. To learn more, see [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api).
Creating a New Privileged Approval
To create a new privileged approval:
- Send a `POST` request to the following endpoint in the Privileged Approval Controller: `/mgmtconfig/v1/admin/customers/{customerId}/approval`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/approval`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- `emailIds`: The user's email address that you are assigning the privileged approval to. You can assign only one email address to the privileged approval.
- The ID of the application segment you want to include in the privileged approval.
- The start and end times and dates for time bound access.
- [View the JSON payload](#postPayload)
[]{
{
"applications": [
{
"id": 0
}
],
"emailIds": [
"string"
],
"endTime": 0,
"startTime": 0,
"workingHours": {
"days": [
"string"
],
"endTime": "string",
"endTimeCron": "string",
"startTime": "string",
"startTimeCron": "string",
"timeZone": "string"
}
}
- [View an example JSON payload](#postExamplePayload)
[]{
"email": "email@safemarch.com",
"startDate": "May 18, 2023",
"startTimeHours": "17",
"startTimeMins": "05",
"startTimeSeconds": "27",
"endDate": "Jun 01, 2023",
"endTimeHours": "17",
"endTimeMins": "05",
"endTimeSeconds": "27",
"enableWorkingHours": true,
"startTime": 1684409727,
"endTime": 1685619327,
"applications": [
{
"id": "145256180497776992"
}
],
"currentTime": 1684409826,
"minAllowedStartTime": 1684406226,
"workingHours": {
"days": [
"MON",
"TUE",
"WED",
"THU",
"FRI"
],
"startTime": "09:00",
"endTime": "17:00",
"timeZone": "Asia/Calcutta",
"startTimeCron": "0 30 3 ? * MON,TUE,WED,THU,FRI",
"endTimeCron": "0 30 11 ? * MON,TUE,WED,THU,FRI"
},
"emailIds": [
"email@safemarch.com"
]
}
- [View an example response](#postResponse)
[]{
"id": "137629",
"creationTime": "1684409827",
"modifiedBy": "72057594038624153",
"startTime": "1684409727",
"endTime": "1685619327",
"workingHours": {
"startTimeCron": "0 30 3 ? * MON,TUE,WED,THU,FRI",
"endTimeCron": "0 30 11 ? * MON,TUE,WED,THU,FRI",
"startTime": "09:00",
"endTime": "17:00",
"days": [
"MON",
"TUE",
"WED",
"THU",
"FRI"
],
"timeZone": "Asia/Calcutta"
},
"emailIds": [
"email@safemarch.com"
],
"applications": [
{
"id": "145256180497776992",
"icmpAccessType": "NONE",
"bypassType": "NEVER",
"configSpace": "DEFAULT",
"cnameConfig": "NOFLATTEN",
"ipAnchored": false,
"tcpKeepAlive": "0",
"useInDrMode": false,
"selectConnectorCloseToApp": false,
"adpEnabled": false
}
]
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Microtenant Support
To create a new privileged approval within a Microtenant:
- Send a `POST` request to the following endpoint in the Privileged Approval Controller: `/mgmtconfig/v1/admin/customers/{customerId}/approval?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/approval?microtenantId=145260601092866314`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- `emailIds`: The user's email address that you are assigning the privileged approval to. You can assign only one email address to the privileged approval.
- The ID of the application segment you want to include in the privileged approval.
- The start and end times and dates for time bound access.
- [View the minimum criteria JSON payload](#postMinimumPayloadMicrotenant)
[]
`{
{
"applications": [
{
"id": 0
}
],
"emailIds": [
"string"
],
"endTime": 0,
"startTime": 0,
"workingHours": {
"days": [
"string"
],
"endTime": "string",
"endTimeCron": "string",
"startTime": "string",
"startTimeCron": "string",
"timeZone": "string"
}
}
`
- [View the example JSON payload](#sampleJsonPayloadPostMicrotenant)
[]
`{
"email": "example@safemarch.com",
"startDate": "May 18, 2023",
"startTimeHours": "17",
"startTimeMins": "05",
"startTimeSeconds": "27",
"endDate": "Jun 01, 2023",
"endTimeHours": "17",
"endTimeMins": "05",
"endTimeSeconds": "27",
"enableWorkingHours": true,
"startTime": 1684409727,
"endTime": 1685619327,
"applications": [
{
"id": "145256180497776992"
}
],
"currentTime": 1684409826,
"minAllowedStartTime": 1684406226,
"workingHours": {
"days": [
"MON",
"TUE",
"WED",
"THU",
"FRI"
],
"startTime": "09:00",
"endTime": "17:00",
"timeZone": "Asia/Calcutta",
"startTimeCron": "0 30 3 ? * MON,TUE,WED,THU,FRI",
"endTimeCron": "0 30 11 ? * MON,TUE,WED,THU,FRI"
},
"emailIds": [
"example@safemarch.com"
]
}
`
- [View an example response](#responsePostMicrotenant)
[]
`{
"id": "137629",
"creationTime": "1684409827",
"modifiedBy": "72057594038624153",
"startTime": "1684409727",
"endTime": "1685619327",
"microtenantId": "145260601092866314",
"workingHours": {
"startTimeCron": "0 30 3 ? * MON,TUE,WED,THU,FRI",
"endTimeCron": "0 30 11 ? * MON,TUE,WED,THU,FRI",
"startTime": "09:00",
"endTime": "17:00",
"days": [
"MON",
"TUE",
"WED",
What is      "THU",
"FRI"
],
"timeZone": "Asia/Calcutta"
},
"emailIds": [
"example@safemarch.com"
],
"applications": [
{
"id": "145256180497776992",
"icmpAccessType": "NONE",
"bypassType": "NEVER",
"configSpace": "DEFAULT",
"cnameConfig": "NOFLATTEN",
"ipAnchored": false,
"tcpKeepAlive": "0",
"useInDrMode": false,
"selectConnectorCloseToApp": false,
"adpEnabled": false
}
]
}`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of All Privileged Approvals
To get details of all privileged approvals:
- Send a `GET` request to the following endpoint in the Privileged Approval Controller: `/mgmtconfig/v1/admin/customers/{customerId}/approval`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/approval`.
- [View an example response](#getApprovals)
[]{
"totalPages": "1",
"totalCount": "2",
"list": [
{
"id": "5638",
"creationTime": "1661437691",
"modifiedBy": "72057594038052745",
"startTime": "1667572066",
"endTime": "1691159266",
"status": "ACTIVE",
"emailIds": [
"test@test.com"
],
"applications": [
{
"id": "72057594038061005",
"modifiedTime": "1674451351",
"creationTime": "1637668324",
"modifiedBy": "72057594038620086",
"name": "ammo4",
"domainName": "deomain4.com",
"domainNames": [
"deomain4.com"
],
"description": "description text",
"enabled": true,
"passiveHealthEnabled": true,
"tcpPortRanges": [
"443",
"443"
],
"doubleEncrypt": false,
"healthCheckType": "DEFAULT",
"icmpAccessType": "NONE",
"bypassType": "NEVER",
"configSpace": "DEFAULT",
"cnameConfig": "NOFLATTEN",
"ipAnchored": false,
"bypassOnReauth": false,
"inspectTrafficWithZia": false,
"tcpKeepAlive": "0",
"useInDrMode": true,
"selectConnectorCloseToApp": false,
"tcpPortRange": [
{
"from": "443",
"to": "443"
}
]
}
]
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint in the Privileged Approval Controller: `/mgmtconfig/v1/admin/customers/{customerId}/approval?page=1&pagesize=20&sortBy=status&sortdir=ASC`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid page and page size values.
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/approval?page=1&pagesize=20&sortBy=status&sortdir=ASC`.
- [View an example response](#getPagApprovals)
[]{
"totalPages": "1",
"totalCount": "2",
"list": [
{
"id": "26",
"modifiedTime": "1664801234",
"creationTime": "1661859900",
"modifiedBy": "72057594038073668",
"startTime": "1661859881",
"endTime": "1686915881",
"workingHours": {
"startTimeCron": "0 0 7 ? * MON,TUE",
"endTimeCron": "0 0 15 ? * MON,TUE",
"startTime": "09:00",
"endTime": "17:00",
"days": [
"MON",
"TUE"
],
"timeZone": "Europe/Berlin"
},
"status": "ACTIVE",
"emailIds": [
"df@dsf1.com"
],
"applications": [
{
"id": "289370814522851438",
"modifiedTime": "1661233018",
"creationTime": "1637367216",
"modifiedBy": "72057594038050500",
"name": "exampleUser-pra-22",
"domainName": "192.168.65.2",
"domainNames": [
"192.168.65.2"
],
"enabled": true,
"passiveHealthEnabled": false,
"tcpPortRanges": [
"22",
"22",
"443",
"443"
],
"doubleEncrypt": false,
"healthCheckType": "DEFAULT",
"icmpAccessType": "NONE",
"bypassType": "NEVER",
"configSpace": "DEFAULT",
"cnameConfig": "NOFLATTEN",
"ipAnchored": false,
"tcpKeepAlive": "0",
"selectConnectorCloseToApp": false,
"tcpPortRange": [
{
"from": "22",
"to": "22"
},
{
"from": "443",
"to": "443"
}
]
}
]
},
{
"id": "50",
"creationTime": "1673536589",
"modifiedBy": "72057594038624153",
"startTime": "1673622881",
"endTime": "1673709281",
"status": "FUTURE",
"emailIds": [
"test@zscaler.com"
],
"applications": [
{
"id": "289370814522851383",
"modifiedTime": "1666272390",
"creationTime": "1636122923",
"modifiedBy": "72057594038050500",
"name": "apipratest.com",
"domainName": "apitest7.com",
"domainNames": [
"apitest7.com"
],
"description": "new app segment",
"defaultIdleTimeout": "0",
"defaultMaxAge": "0",
"enabled": true,
"passiveHealthEnabled": true,
"tcpPortRanges": [
"440",
"443"
],
"doubleEncrypt": false,
"healthCheckType": "NONE",
"icmpAccessType": "NONE",
"bypassType": "NEVER",
"configSpace": "DEFAULT",
"cnameConfig": "NOFLATTEN",
"ipAnchored": false,
"tcpKeepAlive": "0",
"selectConnectorCloseToApp": false,
"tcpPortRange": [
{
"from": "440",
"to": "443"
}
]
}
]
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports Microtenants. To get details of all privileged approvals within a Microtenant:
- Send a `GET` request to the following endpoint in the Privileged Approval Controller: `/mgmtconfig/v1/admin/customers/{customerId}/approval?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/approval?microtenantId=145260601092866314`.
- [View an example response](#getApprovalsResponseMicrotenant)
[]
`{
"totalPages": "1",
"totalCount": "2",
"list": [
{
"id": "26",
"modifiedTime": "1664801234",
"creationTime": "1661859900",
"modifiedBy": "72057594038073668",
"startTime": "1661859881",
"endTime": "1686915881",
"microtenantId": "145260601092866314",
"workingHours": {
"startTimeCron": "0 0 7 ? * MON,TUE",
"endTimeCron": "0 0 15 ? * MON,TUE",
"startTime": "09:00",
"endTime": "17:00",
"days": [
"MON",
"TUE"
],
"timeZone": "Europe/Berlin"
},
"status": "ACTIVE",
"emailIds": [
"df@dsf1.com"
],
"applications": [
{
"id": "289370814522851438",
"modifiedTime": "1661233018",
"creationTime": "1637367216",
"modifiedBy": "72057594038050500",
"name": "exampleUser-pra-22",
"domainName": "192.168.65.2",
"microtenantId": "145260601092866314",
"domainNames": [
"192.168.65.2"
],
"enabled": true,
"passiveHealthEnabled": false,
"tcpPortRanges": [
"22",
"22",
"443",
"443"
],
"doubleEncrypt": false,
"healthCheckType": "DEFAULT",
"icmpAccessType": "NONE",
"bypassType": "NEVER",
"configSpace": "DEFAULT",
"cnameConfig": "NOFLATTEN",
"ipAnchored": false,
"tcpKeepAlive": "0",
"selectConnectorCloseToApp": false,
"tcpPortRange": [
{
"from": "22",
"to": "22"
},
{
"from": "443",
"to": "443"
}
]
}
]
},
{
"id": "50",
"creationTime": "1673536589",
"modifiedBy": "72057594038624153",
"startTime": "1673622881",
"endTime": "1673709281",
"status": "FUTURE",
"microtenantId": "145260601092866314",
"emailIds": [
"test@zscaler.com"
],
"applications": [
{
"id": "289370814522851383",
"modifiedTime": "1666272390",
"creationTime": "1636122923",
"modifiedBy": "72057594038050500",
"name": "apipratest.com",
"domainName": "apitest7.com",
"microtenantId": "145260601092866314",
"domainNames": [
"apitest7.com"
],
"description": "new app segment",
"defaultIdleTimeout": "0",
"defaultMaxAge": "0",
"enabled": true,
"passiveHealthEnabled": true,
"tcpPortRanges": [
"440",
"443"
],
"doubleEncrypt": false,
"healthCheckType": "NONE",
"icmpAccessType": "NONE",
"bypassType": "NEVER",
"configSpace": "DEFAULT",
"cnameConfig": "NOFLATTEN",
"ipAnchored": false,
"tcpKeepAlive": "0",
"selectConnectorCloseToApp": false,
"tcpPortRange": [
{
"from": "440",
"to": "443"
}
]
}
]
}
]
}
`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of a Particular Privileged Approval
To get details of a particular privileged approval:
- Send a `GET` request to the following endpoint in the Privileged Approval Controller: `/mgmtconfig/v1/admin/customers/{customerId}/approval/{id}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The ID of the privileged approval.
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/approval/50`.
- [View an example response](#getApproval)
[]{
"id": "50",
"creationTime": "1673536589",
"modifiedBy": "72057594038624153",
"startTime": "1673622881",
"endTime": "1673709281",
"status": "FUTURE",
"emailIds": [
"test@zscaler.com"
],
"applications": [
{
"id": "289370814522851383",
"modifiedTime": "1666272390",
"creationTime": "1636122923",
"modifiedBy": "72057594038050500",
"name": "apipratest.com",
"domainName": "apitest7.com",
"domainNames": [
"apitest7.com"
],
"description": "new app segment",
"defaultIdleTimeout": "0",
"defaultMaxAge": "0",
"enabled": true,
"passiveHealthEnabled": true,
"tcpPortRanges": [
"440",
"443"
],
"doubleEncrypt": false,
"healthCheckType": "NONE",
"icmpAccessType": "NONE",
"bypassType": "NEVER",
"configSpace": "DEFAULT",
"cnameConfig": "NOFLATTEN",
"ipAnchored": false,
"tcpKeepAlive": "0",
"selectConnectorCloseToApp": false,
"tcpPortRange": [
{
"from": "440",
"to": "443"
}
]
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports Microtenants. To get details for a particular privileged approval within a Microtenant:
- Send a `GET` request to the following endpoint in the Privileged Approval Controller: `/mgmtconfig/v1/admin/customers/{customerId}/approval/{id}?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/approval/50?microtenantId=145260601092866314`.
- [View an example response](#getApprovalResponseMicrotenant)
[]
`{
"id": "50",
"creationTime": "1673536589",
"modifiedBy": "72057594038624153",
"startTime": "1673622881",
"endTime": "1673709281",
"status": "FUTURE",
"microtenantId": "145260601092866314",
"emailIds": [
"test@zscaler.com"
],
"applications": [
{
"id": "289370814522851383",
"modifiedTime": "1666272390",
"creationTime": "1636122923",
"modifiedBy": "72057594038050500",
"microtenantId": "145260601092866314",
"name": "apipratest.com",
"domainName": "apitest7.com",
"domainNames": [
"apitest7.com"
],
"description": "new app segment",
"defaultIdleTimeout": "0",
"defaultMaxAge": "0",
"enabled": true,
"passiveHealthEnabled": true,
"tcpPortRanges": [
"440",
"443"
],
"doubleEncrypt": false,
"healthCheckType": "NONE",
"icmpAccessType": "NONE",
"bypassType": "NEVER",
"configSpace": "DEFAULT",
"cnameConfig": "NOFLATTEN",
"ipAnchored": false,
"tcpKeepAlive": "0",
"selectConnectorCloseToApp": false,
"tcpPortRange": [
{
"from": "440",
"to": "443"
}
]
}
]
}
`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Privileged Approval
To update a privileged approval:
- Send a `PUT` request to the following endpoint in the Privileged Approval Controller: `/mgmtconfig/v1/admin/customers/{customerId}/approval/{id}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The ID of the privileged approval.
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/approval/50.`
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- `emailIds`: The user's email address that you are assigning the privileged approval to. You can assign only one email address to the privileged approval.
- The ID of the application segment you want to include in the privileged approval.
- The start and end times and dates for time bound access.
- [View the JSON payload](#putPayload)
[]{
{
"applications": [
{
"id": 0
}
],
"emailIds": [
"string"
],
"endTime": 0,
"startTime": 0,
"workingHours": {
"days": [
"string"
],
"endTime": "string",
"endTimeCron": "string",
"startTime": "string",
"startTimeCron": "string",
"timeZone": "string"
}
}
- [View an example JSON payload](#putExamplePayload)
[]{
"id": "50",
"objectType": "JITApprovals",
"creationTime": "1673536589",
"modifiedBy": "72057594038624153",
"startTime": 1673622881,
"endTime": 1673709281,
"status": "FUTURE",
"emailIds": [
"test@zscaler.com"
],
"applications": [
{
"id": "289370814522851383"
}
],
"hideInfoTooltip": true,
"restrictedEntity": false,
"email": "test@zscaler.com",
"startDate": "Jan 13, 2023",
"startTimeHours": "20",
"startTimeMins": "44",
"startTimeSeconds": "41",
"endDate": "Jan 14, 2023",
"endTimeHours": "20",
"endTimeMins": "44",
"endTimeSeconds": "41",
"enableWorkingHours": false,
"currentTime": 1673539671,
"minAllowedStartTime": 1673536071
}
A successful response returns code 204, meaning the privileged approval was updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports updating a privileged approval within a Microtenant. To update a privileged approval within a Microtenant:
- Send a `PUT` request to the following endpoint in the Privileged Approval Controller: `/mgmtconfig/v1/admin/customers/{customerId}/approval/{id}?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/approval/50?microtenantId=145260601092866314`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- `emailIds`: The user's email address that you are assigning the privileged approval to. You can assign only one email address to the privileged approval.
- The ID of the application segment you want to include in the privileged approval.
- The start and end times and dates for time bound access.
- [View the minimum criteria JSON payload](#putMinimumPayloadMicrotenant)
[]
`{
{
"applications": [
{
"id": 0
}
],
"emailIds": [
"string"
],
"endTime": 0,
"startTime": 0,
"workingHours": {
"days": [
"string"
],
"endTime": "string",
"endTimeCron": "string",
"startTime": "string",
"startTimeCron": "string",
"timeZone": "string"
}
}
`
- [View an example JSON payload](#putExamplePayloadMicrotenant)
[]
`{
"id": "50",
"objectType": "JITApprovals",
"creationTime": "1673536589",
"modifiedBy": "72057594038624153",
"startTime": 1673622881,
"endTime": 1673709281,
"status": "FUTURE",
"microtenantId": "145260601092866314",
"emailIds": [
"test@zscaler.com"
],
"applications": [
{
"id": "289370814522851383"
}
],
"hideInfoTooltip": true,
"restrictedEntity": false,
"email": "test@zscaler.com",
"startDate": "Jan 13, 2023",
"startTimeHours": "20",
"startTimeMins": "44",
"startTimeSeconds": "41",
"endDate": "Jan 14, 2023",
"endTimeHours": "20",
"endTimeMins": "44",
"endTimeSeconds": "41",
"enableWorkingHours": false,
"currentTime": 1673539671,
"minAllowedStartTime": 1673536071
}
`
A successful response returns code 204, meaning the privileged approval was updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting a Privileged Approval
To delete a privileged approval:
- Send a `DELETE` request to the following endpoint in the Privileged Approval Controller: `/mgmtconfig/v1/admin/customers/{customerId}/approval/{id}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The ID of the privileged approval.
For example: `mgmtconfig/v1/admin/customers/289370814522851328/approval/50`.
A successful response returns code 204 `No Content`, meaning the privileged approval was deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API also supports Microtenants. To delete a privileged approval within a Microtenant:
- Send a `DELETE` request to the following endpoint in the Privileged Approval Controller: `/mgmtconfig/v1/admin/customers/{customerId}/approval/{id}?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/approval/50?microtenantId=145260601092866314`.
A successful response returns code 204, meaning the privileged approval was deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting All Expired Privileged Approvals
To delete all expired privileged approvals:
- Send a `DELETE` request to the following endpoint in the Privileged Approval Controller: `/mgmtconfig/v1/admin/customers/{customerId}/approval/expired`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/approval/expired`.
A successful response returns code 204. meaning the privileged approvals are deleted. If no records are found, code 200 `OK` is returned. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
- [View an example response](#deleteExpiredApprovals)
[]
`HTTP 200 OK
"No records found"`
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the privileged approval use cases:
-
-
[](/zpa/about-api-keys)[](/zpa/configuring-microtenants-using-api)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| customerId | The ZPA tenant ID of the customer | Yes | Integer |
| page | Specifies the page number | No | Integer |
| pageSize | Specifies the page size | No | Integer |
| search | Indicates the search string used to support search by features or fields | No | String |
| sortBy | Indicates the parameter to sort by | No | String |
| sortdir | Specifies the sort direction (i.e., ascending or descending order) | No | EnumSupported values:`ASC`: Ascending`DSC`: Descending |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. Pass `microtenantId` as null to retrieve data from all customers associated with the tenant. If the `microtenantId` is not passed in the request endpoint when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |