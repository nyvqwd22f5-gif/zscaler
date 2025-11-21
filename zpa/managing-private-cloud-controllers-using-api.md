# Managing Private Cloud Controllers Using API
Source: https://help.zscaler.com/zpa/managing-private-cloud-controllers-using-api
PDF: https://help.zscaler.com/pdf/com/en/1531060.pdf

This article provides information on Private Cloud Controller use cases using APIs. All APIs are rate limited. To learn more, see [About Private Cloud Controllers](/zpa/about-private-cloud-controllers) and [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Updating a Private Cloud Controller
To update a Private Cloud Controller:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/privateCloudController/{privateCloudControllerId}?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `privateCloudControllerId`: The unique identifier of the Private Cloud Controller. To learn more, see [Getting Details of All Private Cloud Controllers](#getAllPccs).
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289397352052031488/privateCloudController/289397352052032375?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following:
- `name`: The name of the Private Cloud Controller.
- `id`: The unique identifier of the Private Cloud Controller.
- [View the JSON payload](#updatePccPayload)
[]
`{
"name":"<Private Cloud Controller name>",
"description":"",
"enabled":true,
"id":"289397352052032375"
}`
Refer to [Adding Field Descriptions](#fieldDescriptions) for supported fields and values.
A successful response returns code 204, meaning the Private Cloud Controller is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details of All Private Cloud Controllers
To get details of all Private Cloud Controllers:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/privateCloudController?page={page}&pagesize={pagesize}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `page`: Specifies the page number.
- `pagesize`: Specifies the page size. If not provided, the default page size is 20. The maximum page size is 500.
For example: `/mgmtconfig/v1/admin/customers/289397352052031488/privateCloudController?page=1&pagesize=20`.
- [View an example response](#getAllPccResponse)
[]
` {
"totalPages": "86",
"totalCount": "86",
"list": [
{
"modifiedTime": "1750655686",
"creationTime": "1745475250",
"modifiedBy": "72057594038834533",
"id": "289397352052032268",
"scopeName": "Default",
"fingerprint": "CqQetS4iWtuGZIRo/4guF1HvRrXazhtnZo48TmdzT4w=",
"issuedCertId": "2128",
"enabled": true,
"name": "ankur-bansal-dfa3a.gcplab.dev.zpath.net",
"nonceId": "933",
"nonceName": "ankur-pcc-key",
"PrivateCloudControllerGroupId": "289397352052032169",
"PrivateCloudControllerGroupName": "ankur-pcc-group",
"signingCert": {
"id": "2526",
"name": "Root"
},
"latitude": "12.9715987",
"longitude": "77.5945627",
"location": "Bengaluru, Karnataka, India",
"siteSpDnsName": "bcpsp-289397352052032268.ddiltest-od.com",
"expectedVersion": "25.44.6",
"currentVersion": "25.47.0-ET-90082-notific-gd6aecbef90",
"previousVersion": "25.46.0-ET-87495-extendi-g3b29a7200b",
"lastUpgradeTime": "1752834531",
"expectedUpgradeTime": "1752244842",
"upgradeStatus": "FAILED",
"controlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"upgradeAttempt": "3",
"lastBrokerConnectTime": "1752834991",
"lastBrokerConnectTimeDuration": "04d 19h 46m 45s",
"lastBrokerDisconnectTime": "1752852335",
"lastBrokerDisconnectTimeDuration": "04d 14h 57m 41s",
"masterLastSyncTime": "1752850800",
"userdbLastSyncTime": "1752834508",
"shardLastSyncTime": "1752835046",
"privateIp": "10.10.10.147",
"publicIp": "34.168.195.122",
"platform": "el9",
"runtimeOS": "Red Hat Enterprise Linux 9.5",
"applicationStartTime": "1752834806",
"platformDetail": "GCP",
"zpnSubModuleUpgradeList": [
{
"id": "289397352052032269",
"modifiedTime": "1745480246",
"creationTime": "1745475309",
"modifiedBy": "72057594037928167",
"entityGid": "289397352052032268",
"entityType": "SITE_CONTROLLER",
"role": "MMDB_GEOIP",
"currentVersion": "20221018"
},
{
"id": "289397352052032270",
"modifiedTime": "1745480246",
"creationTime": "1745475309",
"modifiedBy": "72057594037928167",
"entityGid": "289397352052032268",
"entityType": "SITE_CONTROLLER",
"role": "MMDB_ISP",
"currentVersion": "20221018"
}
],
"sargeUpgradeStatus": "UNKNOWN",
"osUpgradeStatus": "UNKNOWN",
"platformVersion": "NA",
"readOnly": false,
"restrictedEntity": false,
"zscalerManaged": false
}
]
}
`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details for a Particular Private Cloud Controller
To get details for a particular Private Cloud Controller:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/privateCloudController/{privateCloudControllerId}µtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `privateCloudControllerId`: The unique identifier of the Private Cloud Controller. To learn more, see [Getting Details of All Private Cloud Controllers](#getAllPccs).
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289397352052031488/privateCloudController/289397352052032375µtenantId=0`.
- [View an example response](#GetPccExampleResponse)
[]
`{
"creationTime": "1752761344",
"modifiedBy": "3",
"id": "289397352052032375",
"scopeName": "Default",
"fingerprint": "Test__1223",
"enabled": true,
"name": "ankur-pcc-key-1752761344576",
"nonceId": "933",
"nonceName": "ankur-pcc-key",
"privateCloudControllerGroupId": "289397352052032169",
"privateCloudControllerGroupName": "ankur-pcc-group",
"latitude": "12.9715987",
"longitude": "77.5945627",
"location": "Bengaluru, Karnataka, India",
"siteSpDnsName": "bcpsp-289397352052032375.ddiltest-od.com",
"upgradeAttempt": "0",
"readOnly": false,
"restrictedEntity": false,
"zscalerManaged": false
}
`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Restarting a Private Cloud Controller
To restart a Private Cloud Controller:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/privateCloudController/{privateCloudControllerId}/restart?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `privateCloudControllerId`: The unique identifier of the Private Cloud Controller. To learn more, see [Getting Details of All Private Cloud Controllers](#getAllPccs).
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289397352052031488/privateCloudController/289397352052032268/restart?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
A successful response returns code 204, meaning the Private Cloud Controller is restarted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting a Private Cloud Controller
To delete a Private Cloud Controller:
- Send a DELETE request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/privateCloudController/{privateCloudControllerId}µtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `privateCloudControllerId`: The unique identifier of the Private Cloud Controller. To learn more, see [Getting Details of All Private Cloud Controllers](#getAllPccs).
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289397352052031488/privateCloudController/289397352052032377µtenantId=0`.
A successful response returns code 204, meaning the Private Cloud Controller is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the Private Cloud Controller use cases:
[](/zpa/configuring-microtenants-using-api)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| description | The description of the Private Cloud Controller | No | String |
| enabled | Whether or not the Private Cloud Controller is enabled | No | Default: `true`Supported values: `true`, `false` |
| microtenantId | The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
| name | The name of the Private Cloud Controller | Yes | String |
| page | Specifies the page number | No | Integer |
| pagesize | Specifies the page size. If not provided, the default page size is 20. The maximum page size is 500. | No | Integer |