# Managing Private Cloud Controller Groups Using API
Source: https://help.zscaler.com/zpa/managing-private-cloud-controller-groups-using-api
PDF: https://help.zscaler.com/pdf/com/en/1531213.pdf

This article provides information on Private Cloud Controller group use cases using APIs. All APIs are rate limited. To learn more, see [About Private Cloud Controller Groups](/zpa/about-private-cloud-controller-groups) and [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Creating a Private Cloud Controller Group
To create a Private Cloud Controller group:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/privateCloudControllerGroup?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289397352052031488/privateCloudControllerGroup?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following:
- `countryCode`: The country code of the Private Cloud Controller group.
- `latitude`: The latitude of the Private Cloud Controller group.
- `location`: The location of the Private Cloud Controller group.
- `longitude`: The longitude of the Private Cloud Controller group.
- `name`: The name of the Private Cloud Controller group.
- `upgradeDay`: Private Cloud Controllers in this group attempt to update to a newer version of the software during this specified day.
- `upgradeTimeInSecs`: Private Cloud Controllers in this group attempt to update to a newer version of the software during this specified time.
- [View the JSON payload](#createPccGroupPayload)
[]
`{
"name": "<name>",
"enabled": true,
"description": "<description>",
"site": [
{
"id": "",
"name": ""
}
],
"overrideVersionProfile": false,
"upgradeDay": "<DAY>",
"upgradeTimeInSecs": "<Upgrade time in seconds>",
"location": "<location>",
"latitude": <latitude>,
"longitude": <longitude>,
"countryCode": "<country code>",
"siteId": "",
"siteName": ""
}
`
- [View a sample JSON payload](#createPccSamplePayload)
[]
`{
"name": "Test_AK",
"enabled": true,
"description": "Test_AK",
"site": [
{
"id": "",
"name": ""
}
],
"overrideVersionProfile": false,
"upgradeDay": "MONDAY",
"upgradeTimeInSecs": "25200",
"location": "Hyderabad, Telangana, India",
"latitude": 17.406498,
"longitude": 78.47724389999999,
"countryCode": "IN",
"siteId": "",
"siteName": ""
}
`
- [View an example response](#createPccExampleResponse)
[]
`{
"modifiedTime": "1753252360",
"creationTime": "1753252360",
"modifiedBy": "72057594038609323",
"id": "289397352052032393",
"enabled": true,
"description": "Test_AK",
"overrideVersionProfile": false,
"upgradeTimeInSecs": "25200",
"upgradeDay": "MONDAY",
"isPublic": "FALSE",
"location": "Hyderabad, Telangana, India",
"latitude": "17.406498",
"longitude": "78.47724389999999",
"cityCountry": "Hyderabad, IN",
"countryCode": "IN",
"name": "Test_AK"
}
`
You can choose the Private Cloud Controller group criteria you want to include in the JSON payload. Refer to [Adding Field Descriptions](#fieldDescriptions) for supported fields and values.
A successful response returns code 201, meaning the Private Cloud Controller group is created. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details of All Private Cloud Controller Groups
To get details of all Private Cloud Controller groups:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/privateCloudControllerGroup?page={page}&pagesize={pagesize}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `page`: Specifies the page number.
- `pagesize`: Specifies the page size. If not provided, the default page size is 20. The maximum page size is 500.
For example: `/mgmtconfig/v1/admin/customers/289397352052031488/privateCloudController?page=1&pagesize=2`.
- [View an example response](#getAllPccGroupsResponse)
[]
`{
"totalPages": "4",
"totalCount": "8",
"list": [
{
"modifiedTime": "1740024243",
"creationTime": "1740023898",
"modifiedBy": "72057594038834533",
"id": "289397352052032169",
"scopeName": "Default",
"enabled": true,
"versionProfileId": "72057594038893230",
"overrideVersionProfile": false,
"siteId": "289397352052032172",
"versionProfileName": "ramesh-version-profile",
"upgradePriority": "FORCE_NOW",
"versionProfileVisibilityScope": "CUSTOM",
"upgradeTimeInSecs": "0",
"upgradeDay": "MONDAY",
"siteName": "ankur-pc",
"isPublic": "FALSE",
"location": "Bengaluru, Karnataka, India",
"siteControllers": [
{
"id": "289397352052032238",
"modifiedTime": "1742974453",
"creationTime": "1742974452",
"modifiedBy": "3",
"name": "ankur-pcc-key-1742974452949",
"fingerprint": "Qk7xCDo8HK9QuoA9lRAzEppa9NxSfnq6gIkwFm00c2w=",
"issuedCertId": "2104",
"enabled": true,
"siteControllerVersion": {
"id": "289397352052032238",
"modifiedTime": "1743744152",
"creationTime": "1742974467",
"modifiedBy": "72057594037928167",
"currentVersion": "25.44.0-datapath44-g16a09e8efd-dirty",
"systemStartTime": "1742875832",
"applicationStartTime": "1743061798",
"lastConnectTime": "1743061803494634",
"lastDisconnectTime": "1743744152075266",
"platform": "el9",
"runtimeOS": "Red Hat Enterprise Linux 9.5",
"brokerId": "72057594038878207",
"siteControllerGroupId": "289397352052032169",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "10.10.10.114",
"publicIp": "34.53.54.187",
"loneWarrior": true,
"tunnelId": "v3jCUR3VUvgNucLvbjYF",
"upgradeAttempt": "0",
"platformDetail": "GCP",
"osUpgradeEnabled": false
},
"nonceId": "933",
"upgradeAttempt": "0"
},
{
"id": "289397352052032268",
"modifiedTime": "1750655686",
"creationTime": "1745475250",
"modifiedBy": "72057594038834533",
"name": "ankur-bansal-dfa3a.gcplab.dev.zpath.net",
"fingerprint": "CqQetS4iWtuGZIRo/4guF1HvRrXazhtnZo48TmdzT4w=",
"issuedCertId": "2128",
"enabled": true,
"siteControllerVersion": {
"id": "289397352052032268",
"modifiedTime": "1753251896",
"creationTime": "1745475309",
"modifiedBy": "72057594038609323",
"expectedVersion": "25.44.6",
"currentVersion": "25.47.0-ET-90082-notific-gd6aecbef90",
"systemStartTime": "1752053559",
"applicationStartTime": "1752834806",
"lastConnectTime": "1752834991190453",
"lastDisconnectTime": "1752852335349736",
"masterLastSyncTime": "1752850800",
"userdbLastSyncTime": "1752834508",
"shardLastSyncTime": "1752835046",
"platform": "el9",
"runtimeOS": "Red Hat Enterprise Linux 9.5",
"brokerId": "72057594038877360",
"siteControllerGroupId": "289397352052032169",
"restartTimeInSec": "1753252196",
"upgradeStatus": "FAILED",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "10.10.10.147",
"publicIp": "34.168.195.122",
"loneWarrior": true,
"tunnelId": "c/70HBKKA0sAZHqJdnXe",
"previousVersion": "25.46.0-ET-87495-extendi-g3b29a7200b",
"lastUpgradedTime": "1752834531",
"upgradeAttempt": "3",
"platformDetail": "GCP",
"upgradeNowOnce": true,
"platformVersion": "NA"
},
"nonceId": "933",
"upgradeAttempt": "0"
},
{
"id": "289397352052032375",
"modifiedTime": "1753251191",
"creationTime": "1752761344",
"modifiedBy": "72057594038609323",
"name": "ankur-pcc-key-1752761344576",
"fingerprint": "Test__1223",
"enabled": true,
"nonceId": "933",
"upgradeAttempt": "0"
}
],
"latitude": "12.9715987",
"longitude": "77.5945627",
"cityCountry": "Bengaluru, IN",
"countryCode": "IN",
"name": "ankur-pcc-group",
"readOnly": false,
"restrictedEntity": false,
"zscalerManaged": false
},
{
"modifiedTime": "1750917498",
"creationTime": "1749017571",
"modifiedBy": "72057594038071237",
"id": "289397352052032350",
"scopeId": "289397352052032197",
"scopeName": "firedrill_scope-1",
"enabled": true,
"versionProfileId": "72057594038893230",
"overrideVersionProfile": false,
"siteId": "289397352052032349",
"versionProfileName": "ramesh-version-profile",
"upgradePriority": "FORCE_NOW",
"versionProfileVisibilityScope": "CUSTOM",
"upgradeTimeInSecs": "66600",
"upgradeDay": "SUNDAY",
"siteName": "hgurram.ddil.pcc",
"isPublic": "FALSE",
"location": "San Jose, CA, USA",
"siteControllers": [
{
"id": "289397352052032351",
"modifiedTime": "1749018052",
"creationTime": "1749018052",
"modifiedBy": "3",
"name": "hgurram.ddil.pcc.prov.key-1749018052365",
"scopeId": "289397352052032197",
"fingerprint": "T/zkKeSsROOdAFPJmPBezOnKHIDzThSBBCHsWRDvkaU=",
"issuedCertId": "2166",
"enabled": true,
"nonceId": "1022",
"upgradeAttempt": "0"
},
{
"id": "289397352052032352",
"modifiedTime": "1749018479",
"creationTime": "1749018478",
"modifiedBy": "3",
"name": "hgurram.ddil.pcc.prov.key-1749018478778",
"scopeId": "289397352052032197",
"fingerprint": "cJ+DHvewTEyqfgnI+/ez9KPKydTUdLIKLuDZiSaXbf8=",
"issuedCertId": "2167",
"enabled": true,
"nonceId": "1022",
"upgradeAttempt": "0"
},
{
"id": "289397352052032353",
"modifiedTime": "1749026115",
"creationTime": "1749026115",
"modifiedBy": "3",
"name": "hgurram.ddil.pcc.prov.key-1749026115652",
"scopeId": "289397352052032197",
"fingerprint": "+deYCUNbDuojOBBs3eZ9mfQfecW/MygXivRLynTKmBI=",
"issuedCertId": "2168",
"enabled": true,
"siteControllerVersion": {
"id": "289397352052032353",
"modifiedTime": "1749100352",
"creationTime": "1749026209",
"modifiedBy": "72057594037928167",
"expectedVersion": "25.42.4",
"currentVersion": "25.46.0-ET-86305-firedri-g3ac9811820",
"systemStartTime": "1745556022",
"applicationStartTime": "1749100318",
"lastConnectTime": "1749100332793988",
"lastDisconnectTime": "1749100352317487",
"platform": "el9",
"runtimeOS": "Red Hat Enterprise Linux 9.5",
"brokerId": "72057594038825700",
"siteControllerGroupId": "289397352052032350",
"restartTimeInSec": "1749100932",
"upgradeStatus": "IN_PROGRESS",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "10.12.12.10",
"publicIp": "34.47.166.180",
"loneWarrior": true,
"tunnelId": "UA2+OYcaTCfLkepvc/uh",
"previousVersion": "25.46.0-PR-11294-46-g5bebf6b965",
"lastUpgradedTime": "1749100332",
"upgradeAttempt": "1",
"platformDetail": "GCP",
"upgradeNowOnce": false,
"platformVersion": "NA"
},
"nonceId": "1022",
"upgradeAttempt": "0"
},
{
"id": "289397352052032356",
"modifiedTime": "1749100667",
"creationTime": "1749100666",
"modifiedBy": "3",
"name": "hgurram.ddil.pcc.prov.key-1749100666769",
"scopeId": "289397352052032197",
"fingerprint": "DnZhFch0JRbB6t+6yhLnK7Q58TAtjdXRT5q7HF45BOo=",
"issuedCertId": "2169",
"enabled": true,
"nonceId": "1022",
"upgradeAttempt": "0"
},
{
"id": "289397352052032357",
"modifiedTime": "1749198878",
"creationTime": "1749198878",
"modifiedBy": "3",
"name": "hgurram.ddil.pcc.prov.key-1749198878202",
"scopeId": "289397352052032197",
"fingerprint": "A/sG3bulN7CUcDK+vhDmngO73imiGXtCQ8iXKnxg9cY=",
"issuedCertId": "2170",
"enabled": true,
"siteControllerVersion": {
"id": "289397352052032357",
"modifiedTime": "1750224610",
"creationTime": "1749443434",
"modifiedBy": "72057594037928167",
"expectedVersion": "25.42.4",
"currentVersion": "25.46.0-ET-93456-bcp-fir-gb900556476",
"systemStartTime": "1745556022",
"applicationStartTime": "1750224225",
"lastConnectTime": "1750224591799181",
"lastDisconnectTime": "1750224610352596",
"masterLastSyncTime": "1750222800",
"userdbLastSyncTime": "1750221180",
"shardLastSyncTime": "1750224591",
"platform": "el9",
"runtimeOS": "Red Hat Enterprise Linux 9.5",
"brokerId": "72057594038881706",
"siteControllerGroupId": "289397352052032350",
"restartTimeInSec": "1749458208",
"upgradeStatus": "FAILED",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "10.12.12.10",
"publicIp": "34.47.166.180",
"loneWarrior": true,
"tunnelId": "3gA9bPi0ynZprq5U5quE",
"previousVersion": "25.46.0-ET-93456-bcp-fir-g2a2ac140af-dirty",
"lastUpgradedTime": "1750221207",
"upgradeAttempt": "3",
"platformDetail": "GCP",
"upgradeNowOnce": false,
"platformVersion": "NA"
},
"nonceId": "1022",
"upgradeAttempt": "0"
},
{
"id": "289397352052032360",
"modifiedTime": "1750225021",
"creationTime": "1750225021",
"modifiedBy": "3",
"name": "hgurram.ddil.pcc.prov.key-1750225021041",
"scopeId": "289397352052032197",
"fingerprint": "oBBezrYFIhvvowRCZc8o9Ss/56bmk964Fmyd+RghQ24=",
"issuedCertId": "2171",
"enabled": true,
"siteControllerVersion": {
"id": "289397352052032360",
"modifiedTime": "1750226150",
"creationTime": "1750225136",
"modifiedBy": "72057594037928167",
"expectedVersion": "25.42.4",
"currentVersion": "25.46.0-ET-93456-bcp-fir-gb900556476",
"systemStartTime": "1745556022",
"applicationStartTime": "1750225967",
"lastConnectTime": "1750226033175736",
"lastDisconnectTime": "1750226149968928",
"masterLastSyncTime": "1750225114",
"userdbLastSyncTime": "1750225090",
"shardLastSyncTime": "1750226053",
"platform": "el9",
"runtimeOS": "Red Hat Enterprise Linux 9.5",
"brokerId": "72057594038881706",
"siteControllerGroupId": "289397352052032350",
"restartTimeInSec": "1750226633",
"upgradeStatus": "IN_PROGRESS",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "10.12.12.10",
"publicIp": "34.47.166.180",
"loneWarrior": true,
"tunnelId": "sxsGXSjxmGv7DMii9BNq",
"upgradeAttempt": "1",
"platformDetail": "GCP",
"upgradeNowOnce": false,
"platformVersion": "NA"
},
"nonceId": "1022",
"upgradeAttempt": "0"
},
{
"id": "289397352052032363",
"modifiedTime": "1752819435",
"creationTime": "1750226714",
"modifiedBy": "3",
"name": "hgurram.ddil.pcc.prov.key-1750226714381",
"scopeId": "289397352052032197",
"fingerprint": "sc/0kNvrpioIbVI4hoHwhWVVF+2bTbXvzLRjzsTfV64=",
"issuedCertId": "2213",
"enabled": true,
"siteControllerVersion": {
"id": "289397352052032363",
"modifiedTime": "1753254148",
"creationTime": "1750226810",
"modifiedBy": "72057594037928167",
"expectedVersion": "25.44.6",
"currentVersion": "25.46.0-ET-94753-observi-g2fc0a9a4d7-dirty",
"systemStartTime": "1745556022",
"applicationStartTime": "1752244927",
"lastConnectTime": "1752244993458924",
"lastDisconnectTime": "1752732208784000",
"masterLastSyncTime": "1753254000",
"userdbLastSyncTime": "1750226782",
"shardLastSyncTime": "1753252361",
"platform": "el9",
"runtimeOS": "Red Hat Enterprise Linux 9.5",
"brokerId": "72057594038881706",
"siteControllerGroupId": "289397352052032350",
"restartTimeInSec": "1752244925",
"upgradeStatus": "FAILED",
"ctrlChannelStatus": "ZPN_STATUS_AUTHENTICATED",
"privateIp": "10.12.12.10",
"publicIp": "34.47.166.180",
"loneWarrior": true,
"tunnelId": "6TdmnJu0Y0STd0RzLM3R",
"previousVersion": "25.46.0-ET-93456-bcp-fir-g388fe22bba-dirty",
"lastUpgradedTime": "1750935451",
"upgradeAttempt": "3",
"platformDetail": "GCP",
"upgradeNowOnce": false,
"platformVersion": "NA"
},
"nonceId": "1022",
"upgradeAttempt": "0"
}
],
"latitude": "37.33874",
"longitude": "-121.8852525",
"cityCountry": "San Jose, US",
"countryCode": "US",
"name": "hgurram.ddil.pcc.grp",
"readOnly": false,
"restrictedEntity": false,
"zscalerManaged": false
}
]
}
`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details for a Particular Private Cloud Controller Group
To get details for a particular Private Cloud Controller group:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/privateCloudControllerGroup/{privateCloudControllerGroupId}µtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `privateCloudControllerGroupId`: The unique identifier of the Private Cloud Controller group. To learn more, see [Getting Details of All Private Cloud Controller Groups](#getAllPccGroups).
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289397352052031488/privateCloudControllerGroup/289397352052032393µtenantId=0`.
- [View an example response](#GetPccGroupExampleResponse)
[]
`{
"modifiedTime": "1753252360",
"creationTime": "1753252360",
"modifiedBy": "72057594038609323",
"id": "289397352052032393",
"MicrotenantName": "Default",
"enabled": true,
"description": "Test_AK",
"versionProfileId": "72057594038893230",
"overrideVersionProfile": false,
"versionProfileName": "ramesh-version-profile",
"upgradePriority": "FORCE_NOW",
"versionProfileVisibilityScope": "CUSTOM",
"upgradeTimeInSecs": "25200",
"upgradeDay": "MONDAY",
"isPublic": "FALSE",
"location": "Hyderabad, Telangana, India",
"latitude": "17.406498",
"longitude": "78.47724389999999",
"cityCountry": "Hyderabad, IN",
"countryCode": "IN",
"name": "Test_AK",
"readOnly": false,
"restrictedEntity": false,
"zscalerManaged": false
}
`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting All Configured Private Cloud Controller Groups by ID and Name
To get all configured Private Cloud Controller groups by ID and name:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/privateCloudControllerGroup/summary?page={page}&pagesize={pagesize}µtenantId={microtenantId}`.
-
Provide the following in the request endpoint.
- `customerId`: The ZPA tenant ID of the customer.
- `page`: Specifies the page number.
- `pagesize`: Specifies the page size. If not provided, the default page size is 20. The maximum page size is 500.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/{customerId}/privateCloudControllerGroup/summary?page={page}&pagesize={pagesize}µtenantId={microtenantId}`.
- [View an example response](#getPccGroupSummary)
[]
`{
"totalPages": "8",
"totalCount": "8",
"list": [
{
"id": "289397352052032169",
"name": "ankur-pcc-group",
"enabled": true
}
]
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Private Cloud Controller Group
To update a Private Cloud Controller group:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/privateCloudControllerGroup/{privateCloudControllerGroupId}?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `privateCloudControllerGroupId`: The unique identifier of the Private Cloud Controller group. To learn more, see [Getting Details of All Private Cloud Controller Groups](#getAllPccGroups).
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289397352052031488/privateCloudControllerGroup/289397352052032393?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following:
- `countryCode`: The country code of the Private Cloud Controller group.
- `latitude`: The latitude of the Private Cloud Controller group.
- `location`: The location of the Private Cloud Controller group.
- `longitude`: The longitude of the Private Cloud Controller group.
- `name`: The name of the Private Cloud Controller group.
- `upgradeDay`: Private Cloud Controllers in this group attempt to update to a newer version of the software during this specified day.
- `upgradeTimeInSecs`: Private Cloud Controllers in this group attempt to update to a newer version of the software during this specified time.
- [View the JSON payload](#updatePccGroupPayload)
[]
`{
"name": "<name>",
"enabled": true,
"description": "<description>",
"site": [
{
"id": "",
"name": ""
}
],
"overrideVersionProfile": false,
"upgradeDay": "<DAT>",
"upgradeTimeInSecs": "<upgrade time in seconds>",
"id": "289397352052032393",
"location": "<location>",
"latitude": "<latitude>",
"longitude": "<longitude>",
"countryCode": "<country code>",
"siteId": ""
}
`
- [View an example JSON payload](#updatePccGroupExamplePayload)
[]
`{
"name": "Test_AK",
"enabled": true,
"description": "Test_AK",
"site": [
{
"id": "",
"name": ""
}
],
"overrideVersionProfile": false,
"upgradeDay": "MONDAY",
"upgradeTimeInSecs": "25200",
"id": "289397352052032393",
"location": "Hyderabad, Telangana, India",
"latitude": "17.406498",
"longitude": "78.47724389999999",
"countryCode": "IN",
"siteId": ""
}
`
You can choose the Private Cloud Controller group criteria you want to include in the JSON payload. Refer to [Adding Field Descriptions](#fieldDescriptions) for supported fields and values.
A successful response returns code 204, meaning the Private Cloud Controller group is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting a Private Cloud Controller Group
To delete a Private Cloud Controller group:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/privateCloudControllerGroup/{privateCloudControllerGroupId}µtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `privateCloudControllerGroupId`: The unique identifier of the Private Cloud Controller group. To learn more, see [Getting Details of All Private Cloud Controller groups](#getAllPccGroups).
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289397352052031488/privateCloudControllerGroup/289397352052032393µtenantId=0`.
A successful response returns code 204, meaning the Private Cloud Controller group is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the Private Cloud Controller group use cases:
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| countryCode | The country code of the Private Cloud Controller group | Yes | String |
| description | The description of the Private Cloud Controller group | No | String |
| enabled | Whether or not the Private Cloud Controller group is enabled | No | Default: `true`Supported values: `true`, `false` |
| latitude | The latitude of the Private Cloud Controller group | Yes | Integer or decimal, with values in the range of –90 to 90 |
| location | The location of the Private Cloud Controller group | Yes | String |
| longitude | The longitude of the Private Cloud Controller group | Yes | Integer or decimal, with values in the range of –180 to 180 |
| overrideVersionProfile | Whether or not the default version profile of the Private Cloud Controller group is applied or overridden | No | Default: `false`Supported values: `true`, `false` |
| siteId | The ID of the Private Cloud | No | Integer |
| siteName | The name of the Private Cloud | No | String |
| upgradeDay | Private Cloud Controllers in this group attempt to update to a newer version of the software during this specified day | No | Default value: `MONDAY`List of valid days (e.g., Sunday, Monday) |
| upgradeTimeInSecs | Private Cloud Controllers in this group attempt to update to a newer version of the software during this specifeid time | No | Default value: `66600`Integer in seconds (i.e., –66600). The integer should be greater than or equal to 0, and less than 86400, in 15-minute intervals. |

## Contents
- **API Developer & Reference Guide**
  - [Getting Started](/zpa/getting-started-zpa-api)
  - [Configuring the Postman REST API Client](/zpa/configuring-postman-rest-api-client)
  - [Understanding Rate Limiting](/zpa/understanding-rate-limiting)
  - [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages)
  - **Reference Guide**
    - [Admin Single Sign-On Management](/zpa/admin-single-sign-management)
    - [API Key Management](/zpa/api-key-management-zpa-api-reference)
    - [Application Segment Management](/zpa/application-segment-management)
    - [Segment Group Management](/zpa/segment-group-management)
    - [AppProtection Control Management](/zpa/appprotection-control-management)
    - [AppProtection Profile Management](/zpa/appprotection-profile-management)
    - [App Connector Management API](/zpa/app-connector-management-api)
    - [App Connector Group Management](/zpa/app-connector-group-management)
    - [Certificate Management](/zpa/certificate-management-api)
    - [Customers](/zpa/customers)
    - [Customer Domain Management](/zpa/customer-domain-management)
    - [Cloud Connector Groups](/zpa/cloud-connector-groups)
    - [Emergency Access User Management](/zpa/emergency-access-user-management)
    - [Enrollment Certificates](/zpa/enrollment-certificates)
    - [Feature Configuration Management](/zpa/feature-configuration-management)
    - [IdP Configurations](/zpa/idp-configurations)
    - [Isolation Profiles](/zpa/isolation-profiles)
    - [Log Streaming Service (LSS) Configuration](/zpa/log-streaming-service-lss-configuration)
    - [Machine Groups](/zpa/machine-groups)
    - [Delegated Tenant Administration](/zpa/delegated-tenant-administration)
    - [Policy Management](/zpa/policy-management)
    - [Posture Profiles](/zpa/posture-profiles)
    - [Private Service Edge Management](/zpa/private-service-edge-management-api)
    - [Private Service Edge Group Management](/zpa/private-service-edge-group-management)
    - [Private Cloud Controller Management](/zpa/private-cloud-controller-management-zpa-api-reference)
    - [Private Cloud Controller Group Management](/zpa/private-cloud-controller-group-management)
    - [Privileged Approval Management](/zpa/privileged-approval-management)
    - [Privileged Console Management](/zpa/privileged-console-management)
    - [Privileged Credential Management](/zpa/privileged-credential-management)
    - [Privileged Portal Management](/zpa/privileged-portal-management)
    - [Provisioning Key Management](/zpa/provisioning-key-management)
    - [SAML Attributes](/zpa/saml-attributes)
    - [SCIM Attributes](/zpa/scim-attributes)
    - [SCIM Groups](/zpa/scim-groups)
    - [Server Management](/zpa/server-management)
    - [Server Group Management](/zpa/server-group-management)
    - [Trusted Networks](/zpa/trusted-networks)
    - [User Portal Management](/zpa/user-portal-management)
    - [User Portal Link Management](/zpa/user-portal-link-management)
    - [Version Profiles](/zpa/version-profiles)
    - [VPN (for Legacy Apps) API](/zpa/vpn-legacy-apps-api)
    - [Zscaler Clouds ](/zpa/zscaler-clouds)
    - [Zscaler Virtual IP Address Range Management](/zpa/zscaler-virtual-ip-address-range-management)
  - **Working with APIs**
    - [Managing Administrators Using API](/zpa/managing-administrators-using-api)
    - [Managing Administrator Roles Using API](/zpa/managing-administrator-roles-using-api)
    - [Managing Admin Single Sign-On Login Configurations Using API](/zpa/managing-admin-single-sign-login-configurations-using-api)
    - [Managing Client Settings Using API](/zpa/managing-client-settings-using-api)
    - [Obtaining Alternative Cloud Domain Details Using API](/zpa/obtaining-alternative-cloud-domain-details-using-api)
    - [Configuring API Keys Using API](/zpa/configuring-api-keys-using-api)
    - [Managing Application Load Balancing and High Availability Using API](/zpa/managing-application-load-balancing-and-high-availability-using-api)
    - [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api)
    - [Configuring Application Segment Multimatch Using API](/zpa/configuring-application-segment-multimatch-using-api)
    - [Configuring Segment Groups Using API](/zpa/configuring-segment-groups-using-api)
    - [Managing App Connectors Using API](/zpa/managing-app-connectors-using-api)
    - [Configuring Auto Delete for Disconnected App Connectors Using API](/zpa/configuring-auto-delete-disconnected-app-connectors-using-api)
    - [Configuring App Connector Groups Using API](/zpa/configuring-app-connector-groups-using-api)
    - [Configuring Browser Access Application Segments Using API](/zpa/configuring-browser-access-application-segments-using-api)
    - [Configuring Certificates Using API](/zpa/configuring-certificates-using-api)
    - [Obtaining Cloud Connector Group Details Using API](/zpa/obtaining-cloud-connector-group-details-using-api)
    - [Obtaining Customer Details Using API](/zpa/obtaining-customer-details-using-api)
    - [Managing Customer Domains Using API](/zpa/managing-customer-domains-using-api)
    - [Configuring Emergency Access Users Using API](/zpa/configuring-emergency-access-users-using-api)
    - [Obtaining Enrollment Certificate Details Using API](/zpa/obtaining-enrollment-certificate-details-using-api)
    - [Managing Feature Configurations Using API](/zpa/managing-feature-configurations-using-api)
    - [Obtaining IdP Configuration Details Using API](/zpa/obtaining-idp-configuration-details-using-api)
    - [Configuring AppProtection Controls Using API](/zpa/configuring-appprotection-controls-using-api)
    - [Configuring AppProtection Profiles Using API](/zpa/configuring-appprotection-profiles-using-api)
    - [Obtaining Isolation Profile Details Using API](/zpa/obtaining-isolation-profile-details-using-api)
    - [Managing Log Streaming Service Configurations Using API](/zpa/managing-log-streaming-service-configurations-using-api)
    - [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api)
    - [Configuring AppProtection Policies Using API](/zpa/configuring-appprotection-policies-using-api)
    - [Configuring Client Forwarding Policies Using API](/zpa/configuring-client-forwarding-policies-using-api)
    - [Configuring Isolation Policies Using API](/zpa/configuring-isolation-policies-using-api)
    - [Configuring Privileged Policies Using API](/zpa/configuring-privileged-policies-using-api)
    - [Configuring Redirection Policies Using API](/zpa/configuring-redirection-policies-using-api)
    - [Configuring Timeout Policies Using API](/zpa/configuring-timeout-policies-using-api)
    - [Obtaining Machine Group Details Using API](/zpa/obtaining-machine-group-details-using-api)
    - [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api)
    - [Obtaining Posture Profile Details Using API](/zpa/obtaining-posture-profile-details-using-api)
    - [Configuring Privileged Approvals Using API](/zpa/configuring-privileged-approvals-using-api)
    - [Configuring Privileged Credentials Using API](/zpa/configuring-privileged-credentials-using-api)
    - [Configuring Privileged Consoles Using API](/zpa/configuring-privileged-consoles-using-api)
    - [Configuring Privileged Portals Using API](/zpa/configuring-privileged-portals-using-api)
    - [Configuring Provisioning Keys Using API](/zpa/configuring-provisioning-keys-using-api)
    - [Obtaining SAML Attribute Details Using API](/zpa/obtaining-saml-attribute-details-using-api)
    - [Obtaining SCIM Attribute Details Using API](/zpa/obtaining-scim-attribute-details-using-api)
    - [Obtaining SCIM Group Details Using API](/zpa/obtaining-scim-group-details-using-api)
    - [Configuring Servers Using API](/zpa/configuring-servers-using-api)
    - [Configuring Server Groups Using API](/zpa/configuring-server-groups-using-api)
    - [Managing ZPA Private Service Edges Using API](/zpa/managing-zpa-private-service-edges-using-api)
    - [Configuring ZPA Private Service Edge Groups Using API](/zpa/configuring-zpa-private-service-edge-groups-using-api)
    - [Managing Private Cloud Controllers Using API](/zpa/managing-private-cloud-controllers-using-api)
    - [Managing Private Cloud Controller Groups Using API](/zpa/managing-private-cloud-controller-groups-using-api)
    - [Obtaining VPN (for Legacy Apps) Resources Using API](/zpa/obtaining-vpn-legacy-apps-resources-using-api)
    - [Obtaining Trusted Network Details Using API](/zpa/obtaining-trusted-network-details-using-api)
    - [Obtaining Version Profile Details Using API](/zpa/obtaining-version-profile-details-using-api)
    - [Configuring User Portals Using API](/zpa/configuring-user-portals-using-api)
    - [Configuring User Portal Links Using API](/zpa/configuring-user-portal-links-using-api)
    - [Configuring Zscaler Virtual IP Address Ranges Using API](/zpa/configuring-zscaler-virtual-ip-address-ranges-using-api)