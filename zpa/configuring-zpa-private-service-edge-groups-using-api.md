# Configuring ZPA Private Service Edge Groups Using API
Source: https://help.zscaler.com/zpa/configuring-zpa-private-service-edge-groups-using-api
PDF: https://help.zscaler.com/pdf/com/en/1485016.pdf

This article provides information for managing Zscaler Private Access (ZPA) [Private Service Edge groups](/zpa/about-zpa-service-edge-groups) using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Prerequisite API Calls
Before creating a Private Service Edge Group, you must get the following required details:
- All version profiles. To learn more, see [Obtaining Version Profile Details Using API](/zpa/obtaining-version-profile-details-using-api).
- All trusted networks. To learn more, see [Obtaining Trusted Network Details Using API](/zpa/obtaining-trusted-network-details-using-api).
[]Creating a Private Service Edge Group
To create a Private Service Edge Group:
- Send a `POST` request to the following endpoint in the Private Service Edge Group Controller: `/mgmtconfig/v1/admin/customers/{customerId}/serviceEdgeGroup`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/serviceEdgeGroup`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload to create a Private Service Edge Group and provide the following information about the Private Service Edge Group:
- `name`: The name of the Private Service Edge Group.
- `latitude`: The latitude of the Private Service Edge Group.
- `longitude`: The longitude of the Private Service Edge Group.
- `location`: The location of the Private Service Edge Group.
- `upgradeDay`: The valid day (i.e., Sunday, Monday) for when the Private Service Edges in this group attempt to upgrade.
- `upgradeTimeInSecs`: The integer in seconds (i..e, 66600) for how long the Private Service Edge Groups attempt to upgrade.
- [View the JSON payload](#ViewJSONPayload)
[]{
"name": "<Service Edge Group name>",
"description": "<Service Edge Group description>",
"upgradeDay": "<upgradeDay>",
"upgradeTimeInSecs": "<upgradeTimeInSecs>",
"latitude": "<latitude>",
"longitude": "<longitude>",
"location": "<location>",
"graceDistanceEnabled": "false",
"graceDistanceValue": 0,
"graceDistanceValueUnit": "MILES",
"altCloud": "<Sample Alt Cloud name>"
}
- [View the sample JSON payload](#ViewSampleJSONPayload)
[]{
"name": "Service Edge Group",
"description": "Service Edge Group in San Jose",
"upgradeDay": "SUNDAY",
"upgradeTimeInSecs": "66600",
"latitude": "37.3382082",
"longitude": "-121.8863286",
"location": "San Jose, CA, USA",
"graceDistanceEnabled": "false",
"graceDistanceValue": 0,
"graceDistanceValueUnit": "MILES",
"altCloud": "Sample Alt Cloud name"
}
- [View an example response](#ViewExample)
[]{
"enabled": true,
"isPublic": false,
"location": "48960 Usansolo, Biscay, Spain",
"dnsQueryType": "IPV4_IPV6",
"overrideVersionProfile": true,
"name": "test sg7",
"description": "test sg description",
"trustedNetworks": [
{
"id": "217306507451043634"
}
],
"upgradeDay": "SUNDAY",
"upgradeTimeInSecs": "70200",
"latitude": "43.2187353",
"longitude": "-2.8190749",
"versionProfileId": "0",
"graceDistanceEnabled": "false",
"altCloud": "Sample Alt Cloud name"
}
A successful response returns code 201, meaning the Private Service Edge Group is created. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the Private Service Edge Group criteria you want to include in the JSON payload. Refer to the [Adding Field Descriptions](#AddingFieldDescriptions) section for supported values.
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the Private Service Edge Group use cases:
-
-
-
[](/zpa/obtaining-version-profile-details-using-api)[](/zpa/about-api-keys)[](/zpa/configuring-microtenants-using-api)[](/zpa/understanding-disaster-recovery)
[](/zpa/configuring-service-edges#addgroup)
-
-
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| name | Name of the Private Service Edge Group | Yes | String |
| description | Description of the Private Service Edge Group | No | String |
| enabled | Whether this Private Service Edge Group is enabled or not | No | Default value: `true`Supported values: `true`, `false` |
| latitude | Latitude for the Private Service Edge Group | Yes | Integer or decimal with values in the range of -90 to 90 |
| longitude | Longitude for the Private Service Edge Group | Yes | Integer or decimal with values in the range of -180 to 180 |
| location | Location for the Private Service Edge Group | Yes | String |
| upgradeDay | Private Service Edges in this group attempt to update to a newer version of the software during this specified day | No | Default value: `SUNDAY`List of valid days (i.e., Sunday, Monday) |
| upgradeTimeInSecs | Private Service Edges in this group attempt to update to a newer version of the software during this specified time | No | Default value: 66600Integer in seconds (i..e, 66600). The integer must be greater than or equal to 0 and less than 86400, in 15 minute intervals |
| isPublic | Enable or disable public access for the Private Service Edge Group. | No | Default value: `FALSE`Supported values:`DEFAULT``TRUE``FALSE` |
| trustedNetworks | Trusted networks for this Private Service Edge Group. | No | List of trusted network objects |
| overrideVersionProfile | Whether the default version profile of the App Connector Group is applied or overridden | No | Default: `true`Supported values: `true`, `false` |
| versionProfileId | ID of the version profile. To learn more, see Obtaining Version Profile Details Using API. | Yes, if the value for `overrideVersionProfile` is set to true | Any long value in the version profile IDs |
| MicrotenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. Pass `microtenantId` as null to retrieve data from all Microtenants associated with the tenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
| useInDrMode | Whether or not the ZPA Private Service Edge group is designated for disaster recovery | No | Default: `false`Supported values: `true`, `false` |
| graceDistanceEnabled | If enabled, allows the ZPA Private Service Edge of the ZPA Private Service Edge Group within the specified distance to be prioritized over a closer ZPA Public Service Edge. To learn more, see Configuring ZPA Private Service Edges. | No | Default: `false`Supported values: `true`, `false` |
| graceDistanceValue | Indicates the maximum distance in miles or kilometers to ZPA Private Service Edge groups that would override a ZPA Public Service Edge. The maximum limit for the distance is 25,000 miles, or 40,233.6 kilometers. | No | Float |
| graceDistanceValueUnit | Indicates the grace distance unit of measure in miles or kilometers. This value is only required if `graceDistanceEnabled` is set to `true`. | No | Supported values:`MILES``KMS` |
| altCloud | The alternative cloud domain that can override the default cloud name for the ZPA Private Service Edge Group it is assigned to | No | String |
Getting Details for All Private Service Edge Groups
To get details for all Private Service Edge Groups:
- Send a `GET` request to the following endpoint in the Private Service Edge Group Controller: `/mgmtconfig/v1/admin/customers/{customerId}/serviceEdgeGroup`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/serviceEdge`.
- [View an example response](#ViewExample3)
[]{
"totalPages": "17",
"list": [
{
"id": "217246660303024722",
"modifiedTime": "1618444226",
"creationTime": "1607887129",
"modifiedBy": "72057594038006519",
"name": "1 mp pb group",
"enabled": true,
"isPublic": "FALSE",
"location": "120 Holger Way, San Jose, CA 95134, USA",
"upgradeTimeInSecs": "28800",
"upgradeDay": "MONDAY",
"latitude": "37.4181643",
"longitude": "-121.9531325",
"cityCountry": "San Jose, US",
"countryCode": "US",
"altCloud": "Sample Alt Cloud",
"graceDistanceEnabled": false,
"serviceEdges": [
{
"id": "217246660303024723",
"modifiedTime": "1607915744",
"creationTime": "1607887364",
"modifiedBy": "72057594037950342",
"name": "1 mp pb-1",
"fingerprint": "asbErAYZ7/mNUcQhRPd8XFMIRutWjMsWrfot1dDrOOY=",
"issuedCertId": "10591",
"enabled": true,
"listenIps": [
"192.168.255.2"
],
"publishIps": [
"192.168.255.2"
],
"privateBrokerVersion": {
"id": "217246660303024723",
"modifiedTime": "1618419215",
"modifiedBy": "72057594037928167",
"currentVersion": "21.67.2-2-g1a8538e55-dirty",
"systemStartTime": "0",
"applicationStartTime": "1618248071",
"lastConnectTime": "1618417904046524",
"lastDisconnectTime": "1618419214878810",
"platform": "osx20",
"brokerId": "72057594037950451",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "192.168.255.1",
"publicIp": "192.168.255.1",
"loneWarrior": true,
"tunnelId": "m3JSAvHG72PIEWN18iXR",
"previousVersion": "21.26.0-91-g018c50e7f-dirty",
"lastUpgradedTime": "1617857786",
"upgradeAttempt": "0",
"serviceEdgeGroupId": "217246660303024722"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6115"
},
{
"id": "217246660303024725",
"modifiedTime": "1607918700",
"creationTime": "1607918700",
"modifiedBy": "3",
"name": "1 mp pb-2",
"fingerprint": "37As8jQglTtuEr5XXkb1MuMHXeYSLTG0+OLeJneupJE=",
"issuedCertId": "10593",
"enabled": true,
"privateBrokerVersion": {
"id": "217246660303024725",
"modifiedTime": "1607918775",
"creationTime": "1607918704",
"modifiedBy": "72057594037928167",
"expectedVersion": "20.40.2",
"currentVersion": "20.148.2-59-gb3abc04-asan",
"systemStartTime": "10790289",
"applicationStartTime": "1607918770",
"lastConnectTime": "1607918775548271",
"lastDisconnectTime": "1607918775572483",
"platform": "el7",
"platformDetail": "ESXi",
"brokerId": "72057594037937044",
"restartTimeInSec": "1607932800",
"upgradeStatus": "IN_PROGRESS",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "10.80.1.213",
"publicIp": "199.168.150.161",
"loneWarrior": true,
"tunnelId": "6ZFoRXycAivHanaOk3Ld",
"upgradeAttempt": "1",
"serviceEdgeGroupId": "217246660303024722"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6115"
},
{
"id": "217246660303024726",
"modifiedTime": "1607919146",
"creationTime": "1607919103",
"modifiedBy": "72057594037950342",
"name": "1 mp pb-3",
"fingerprint": "DvW3Bty5CmlRqI5n1pLGWCBRxZPIRMLu5GcRJn2sQpg=",
"issuedCertId": "10594",
"enabled": true,
"listenIps": [
"0.0.0.0"
],
"publishIps": [
"broker1a.sjc5.prod.zpath.net"
],
"privateBrokerVersion": {
"id": "217246660303024726",
"modifiedTime": "1607920424",
"creationTime": "1607919107",
"modifiedBy": "72057594037928167",
"currentVersion": "20.148.2-60-gb16909d-asan",
"systemStartTime": "4551151",
"applicationStartTime": "1607920165",
"lastConnectTime": "1607920170963047",
"lastDisconnectTime": "1607920424100860",
"platform": "el7",
"platformDetail": "ESXi",
"brokerId": "72057594037937044",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "10.17.248.46",
"publicIp": "54.67.88.171",
"loneWarrior": true,
"tunnelId": "rrqb/ms0Obfoiknhk77j",
"previousVersion": "20.148.2-59-gb3abc04-asan",
"lastUpgradedTime": "1607920169",
"upgradeAttempt": "0",
"serviceEdgeGroupId": "217246660303024722"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6115"
},
{
"id": "217246660303024755",
"modifiedTime": "1611279015",
"creationTime": "1611279014",
"modifiedBy": "3",
"name": "1 mp pb-4",
"fingerprint": "jFgW0FtrX3BT5bQWRavNViwLLn1GzDxqKT9G3AAFfC0=",
"issuedCertId": "10630",
"enabled": true,
"privateBrokerVersion": {
"id": "217246660303024755",
"modifiedTime": "1611279174",
"creationTime": "1611279019",
"modifiedBy": "72057594037928167",
"currentVersion": "21.20.1-1-gb1bbb0d",
"systemStartTime": "40211",
"applicationStartTime": "1611279165",
"lastConnectTime": "1611279172008161",
"lastDisconnectTime": "1611279173985030",
"platform": "el7",
"brokerId": "72057594037937044",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "172.17.0.2",
"publicIp": "207.47.45.254",
"loneWarrior": true,
"tunnelId": "mPT1qthUYrTHFtxy2SYV",
"upgradeAttempt": "0",
"serviceEdgeGroupId": "217246660303024722"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6115"
},
{
"id": "217246660303024756",
"modifiedTime": "1611279972",
"creationTime": "1611279972",
"modifiedBy": "3",
"name": "1 mp pb-5",
"fingerprint": "C3jWKc1P340Gl9OPFCUiRUHMg5+0i6iQf0LYoT0fQ1w=",
"issuedCertId": "10631",
"enabled": true,
"privateBrokerVersion": {
"id": "217246660303024756",
"modifiedTime": "1611280009",
"creationTime": "1611279977",
"modifiedBy": "72057594037928167",
"currentVersion": "21.20.1-1-gb1bbb0d",
"systemStartTime": "41040",
"applicationStartTime": "1611279993",
"lastConnectTime": "1611280000504792",
"lastDisconnectTime": "1611280009428607",
"platform": "el7",
"brokerId": "72057594037937044",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "172.17.0.2",
"publicIp": "207.47.45.254",
"loneWarrior": true,
"tunnelId": "rjpt0rGVrXlVn/QYZVIn",
"upgradeAttempt": "0",
"serviceEdgeGroupId": "217246660303024722"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6115"
},
{
"id": "217246660303025050",
"modifiedTime": "1621885476",
"creationTime": "1621885476",
"modifiedBy": "3",
"name": "1 mp pb-6",
"fingerprint": "mTjGKNLwROP/GAEiNSnNeZYU0bDdjxT5CFSShPVld+c=",
"issuedCertId": "10758",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "6115"
}
]
},
{
"id": "217246660303025237",
"creationTime": "1627602372",
"modifiedBy": "72057594038008981",
"name": "example-pb-service-edge-gp",
"enabled": true,
"description": "pbroker service-edge group",
"isPublic": "FALSE",
"location": "British Columbia, Canada",
"upgradeTimeInSecs": "25200",
"upgradeDay": "MONDAY",
"latitude": "53.7266683",
"longitude": "-127.6476206",
"cityCountry": "Terrace, CA",
"altCloud": "Sample Alt Cloud",
"countryCode": "CA",
"graceDistanceEnabled": false,
"serviceEdges": [
{
"id": "217246660303025238",
"modifiedTime": "1627609436",
"creationTime": "1627602563",
"modifiedBy": "72057594038008981",
"name": "example-pb-provisioning-key-1",
"fingerprint": "y7wB7e9s0K0/s7Z0fisrThqXmM4iP0MaS6qRDZ/m8t8=",
"issuedCertId": "10817",
"enabled": true,
"listenIps": [
"192.168.97.1"
],
"publishIps": [
"192.168.97.1"
],
"privateBrokerVersion": {
"id": "217246660303025238",
"modifiedTime": "1627669261",
"creationTime": "1627602572",
"modifiedBy": "72057594037928167",
"currentVersion": "21.172.1-1-g16b0894c0",
"systemStartTime": "0",
"applicationStartTime": "1627668835",
"lastConnectTime": "1627668837629824",
"lastDisconnectTime": "1627669260880099",
"platform": "osx20",
"brokerId": "72057594038008982",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "192.168.96.1",
"publicIp": "192.168.96.1",
"loneWarrior": true,
"tunnelId": "SCq71dN8T17K8sj4HitJ",
"upgradeAttempt": "0",
"serviceEdgeGroupId": "217246660303025237"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6270"
},
{
"id": "217246660303025239",
"modifiedTime": "1627663848",
"creationTime": "1627663847",
"modifiedBy": "3",
"name": "example-pb-provisioning-key-2",
"fingerprint": "an0gBzUTPJJ69FEKDIvRSuP2//IlsCk4Skjd3Z5/xg8=",
"issuedCertId": "10818",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "6270"
},
{
"id": "217246660303025271",
"modifiedTime": "1628031064",
"creationTime": "1628030993",
"modifiedBy": "72057594038008981",
"name": "example-pb-provisioning-key-3",
"fingerprint": "p15uKYw17cA4dOfxYaKf1Lm7LtfUS7M2y604/Ew8v4E=",
"issuedCertId": "10825",
"enabled": true,
"listenIps": [
"192.168.97.1"
],
"publishIps": [
"192.168.97.1"
],
"privateBrokerVersion": {
"id": "217246660303025271",
"modifiedTime": "1628206738",
"creationTime": "1628031005",
"modifiedBy": "72057594037928167",
"currentVersion": "21.172.1-703-g4f9451e18",
"systemStartTime": "0",
"applicationStartTime": "1628205678",
"lastConnectTime": "1628205680713282",
"lastDisconnectTime": "1628206737965749",
"platform": "osx20",
"brokerId": "72057594038008982",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "192.168.96.1",
"publicIp": "192.168.96.1",
"loneWarrior": true,
"tunnelId": "l+UcOdrW/g106BD6v/qe",
"previousVersion": "21.172.1-704-g145e4251c-dirty",
"lastUpgradedTime": "1628190738",
"upgradeAttempt": "0",
"serviceEdgeGroupId": "217246660303025237"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6270"
}
]
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/serviceEdgeGroup?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/serviceEdge?page=1&pagesize=2.`
- [View an example response](#paginatedResponse)
[]{
"totalPages": "19",
"list": [
{
"id": "217246660303024722",
"modifiedTime": "1618444226",
"creationTime": "1607887129",
"modifiedBy": "72057594038006519",
"name": "Test Service Edge Group",
"enabled": true,
"versionProfileId": "0",
"overrideVersionProfile": false,
"versionProfileName": "default",
"versionProfileVisibilityScope": "ALL",
"upgradeTimeInSecs": "28800",
"upgradeDay": "MONDAY",
"isPublic": "FALSE",
"location": "120 Holger Way, San Jose, CA 95134, USA",
"latitude": "37.4181643",
"longitude": "-121.9531325",
"cityCountry": "San Jose, US",
"altCloud": "Sample Alt Cloud",
"countryCode": "US",
"graceDistanceEnabled": false,
"serviceEdges": [
{
"id": "217246660303024723",
"modifiedTime": "1607915744",
"creationTime": "1607887364",
"modifiedBy": "72057594037950342",
"name": "Test Service Edge Group",
"fingerprint": "asbErAYZ7/mNUcQhRPd8XFMIRutWjMsWrfot1dDrOOY=",
"issuedCertId": "10591",
"enabled": true,
"listenIps": [
"192.168.255.2"
],
"publishIps": [
"191.144.215.2"
],
"privateBrokerVersion": {
"id": "217246660303024723",
"modifiedTime": "1618419215",
"modifiedBy": "72057594037928167",
"currentVersion": "21.67.2-2-g1a8538e55-dirty",
"systemStartTime": "0",
"applicationStartTime": "1618248071",
"lastConnectTime": "1618417904046524",
"lastDisconnectTime": "1618419214878810",
"platform": "osx20",
"platformDetail": "ESXi",
"brokerId": "72057594037950451",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "192.168.255.1",
"publicIp": "192.168.255.1",
"loneWarrior": true,
"tunnelId": "m3JSAvHG72PIEWN18iXR",
"previousVersion": "21.26.0-91-g018c50e7f-dirty",
"lastUpgradedTime": "1617857786",
"upgradeAttempt": "0",
"serviceEdgeGroupId": "217246660303024722"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6115"
},
{
"id": "217246660303024725",
"modifiedTime": "1607918700",
"creationTime": "1607918700",
"modifiedBy": "3",
"name": "Test Service Edge Group-2",
"fingerprint": "37As8jQglTtuEr5XXkb1MuMHXeYSLTG0+OLeJneupJE=",
"issuedCertId": "10593",
"enabled": true,
"privateBrokerVersion": {
"id": "217246660303024725",
"modifiedTime": "1607918775",
"creationTime": "1607918704",
"modifiedBy": "72057594037928167",
"expectedVersion": "20.40.2",
"currentVersion": "20.148.2-59-gb3abc04-asan",
"systemStartTime": "10790289",
"applicationStartTime": "1607918770",
"lastConnectTime": "1607918775548271",
"lastDisconnectTime": "1607918775572483",
"platform": "el7",
"brokerId": "72057594037937044",
"restartTimeInSec": "1607932800",
"upgradeStatus": "IN_PROGRESS",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "10.80.1.213",
"publicIp": "199.168.150.161",
"loneWarrior": true,
"tunnelId": "6ZFoRXycAivHanaOk3Ld",
"upgradeAttempt": "1",
"serviceEdgeGroupId": "217246660303024722"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6115"
},
{
"id": "217246660303024726",
"modifiedTime": "1607919146",
"creationTime": "1607919103",
"modifiedBy": "72057594037950342",
"name": "Test Service Edge Group-3",
"fingerprint": "DvW3Bty5CmlRqI5n1pLGWCBRxZPIRMLu5GcRJn2sQpg=",
"issuedCertId": "10594",
"enabled": true,
"listenIps": [
"0.0.0.0"
],
"publishIps": [
"broker1a.sjc5.test.net"
],
"privateBrokerVersion": {
"id": "217246660303024726",
"modifiedTime": "1607920424",
"creationTime": "1607919107",
"modifiedBy": "72057594037928167",
"currentVersion": "20.148.2-60-gb16909d-asan",
"systemStartTime": "4551151",
"applicationStartTime": "1607920165",
"lastConnectTime": "1607920170963047",
"lastDisconnectTime": "1607920424100860",
"platform": "el7",
"platformDetail": "ESXi",
"brokerId": "72057594037937044",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "10.17.248.46",
"publicIp": "54.67.88.171",
"loneWarrior": true,
"tunnelId": "rrqb/ms0Obfoiknhk77j",
"previousVersion": "20.148.2-59-gb3abc04-asan",
"lastUpgradedTime": "1607920169",
"upgradeAttempt": "0",
"serviceEdgeGroupId": "217246660303024722"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6115"
},
{
"id": "217246660303024755",
"modifiedTime": "1611279015",
"creationTime": "1611279014",
"modifiedBy": "3",
"name": "Test Service Edge Group-4",
"fingerprint": "jFgW0FtrX3BT5bQWRavNViwLLn1GzDxqKT9G3AAFfC0=",
"issuedCertId": "10630",
"enabled": true,
"privateBrokerVersion": {
"id": "217246660303024755",
"modifiedTime": "1611279174",
"creationTime": "1611279019",
"modifiedBy": "72057594037928167",
"currentVersion": "21.20.1-1-gb1bbb0d",
"systemStartTime": "40211",
"applicationStartTime": "1611279165",
"lastConnectTime": "1611279172008161",
"lastDisconnectTime": "1611279173985030",
"platform": "el7",
"brokerId": "72057594037937044",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "172.17.0.2",
"publicIp": "207.47.45.254",
"loneWarrior": true,
"tunnelId": "mPT1qthUYrTHFtxy2SYV",
"upgradeAttempt": "0",
"serviceEdgeGroupId": "217246660303024722"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6115"
},
{
"id": "217246660303024756",
"modifiedTime": "1611279972",
"creationTime": "1611279972",
"modifiedBy": "3",
"name": "Test Service Edge Group-5",
"fingerprint": "C3jWKc1P340Gl9OPFCUiRUHMg5+0i6iQf0LYoT0fQ1w=",
"issuedCertId": "10631",
"enabled": true,
"privateBrokerVersion": {
"id": "217246660303024756",
"modifiedTime": "1611280009",
"creationTime": "1611279977",
"modifiedBy": "72057594037928167",
"currentVersion": "21.20.1-1-gb1bbb0d",
"systemStartTime": "41040",
"applicationStartTime": "1611279993",
"lastConnectTime": "1611280000504792",
"lastDisconnectTime": "1611280009428607",
"platform": "el7",
"brokerId": "72057594037937044",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "172.17.0.2",
"publicIp": "222.41.62.224",
"loneWarrior": true,
"tunnelId": "rjpt0rGVrXlVn/QYZVIn",
"upgradeAttempt": "0",
"serviceEdgeGroupId": "217246660303024722"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6115"
},
{
"id": "217246660303025050",
"modifiedTime": "1621885476",
"creationTime": "1621885476",
"modifiedBy": "3",
"name": "Test Service Edge Group-6",
"fingerprint": "mTjGKNLwROP/GAEiNSnNeZYU0bDdjxT5CFSShPVld+c=",
"issuedCertId": "10758",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "6115"
},
{
"id": "217246660303025436",
"modifiedTime": "1630980984",
"creationTime": "1630980984",
"modifiedBy": "3",
"name": "Test Service Edge Group-7",
"fingerprint": "6vr06ZYlGlmJQUv2YojI8bqlBoRvdckip06bJoaMyqA=",
"issuedCertId": "10891",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "6115"
}
]
},
{
"id": "217246660303025237",
"creationTime": "1627602372",
"modifiedBy": "72057594038008981",
"name": "Test Service Edge Group-8",
"enabled": true,
"description": "pbroker service-edge group",
"versionProfileId": "0",
"overrideVersionProfile": false,
"versionProfileName": "default",
"versionProfileVisibilityScope": "ALL",
"upgradeTimeInSecs": "25200",
"upgradeDay": "MONDAY",
"isPublic": "FALSE",
"location": "British Columbia, Canada",
"latitude": "53.7266683",
"longitude": "-127.6476206",
"cityCountry": "Terrace, CA",
"countryCode": "CA",
"altCloud": "Sample Alt Cloud",
"graceDistanceEnabled": false,
"serviceEdges": [
{
"id": "217246660303025271",
"modifiedTime": "1628031064",
"creationTime": "1628030993",
"modifiedBy": "72057594038008981",
"name": "Test-provisioning-key-3",
"fingerprint": "p15uKYw17cA4dOfxYaKf1Lm7LtfUS7M2y604/Ew8v4E=",
"issuedCertId": "10825",
"enabled": true,
"listenIps": [
"192.168.97.1"
],
"publishIps": [
"112.124.97.5"
],
"privateBrokerVersion": {
"id": "217246660303025271",
"modifiedTime": "1628206738",
"creationTime": "1628031005",
"modifiedBy": "72057594037928167",
"currentVersion": "21.172.1-703-g4f9451e18",
"systemStartTime": "0",
"applicationStartTime": "1628205678",
"lastConnectTime": "1628205680713282",
"lastDisconnectTime": "1628206737965749",
"platform": "osx20",
"brokerId": "72057594038008982",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "192.168.96.1",
"publicIp": "196.158.92.1",
"loneWarrior": true,
"tunnelId": "l+UcOdrW/g106BD6v/qe",
"previousVersion": "21.172.1-704-g145e4251c-dirty",
"lastUpgradedTime": "1628190738",
"upgradeAttempt": "0",
"serviceEdgeGroupId": "217246660303025237"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6270"
},
{
"id": "217246660303025434",
"modifiedTime": "1630626344",
"creationTime": "1630626286",
"modifiedBy": "72057594038041059",
"name": "Test-provisioning-key-4",
"fingerprint": "0gPXH0n/6PZv0D8aIg4qFo6sGf1T5hCx8ZyYazcflm0=",
"issuedCertId": "10890",
"enabled": true,
"listenIps": [
"10.80.1.75"
],
"publishIps": [
"10.80.1.75"
],
"upgradeAttempt": "0",
"provisioningKeyId": "6270"
},
{
"id": "217246660303025508",
"modifiedTime": "1633734936",
"creationTime": "1633734936",
"modifiedBy": "3",
"name": "Testp-provisioning-key-5",
"fingerprint": "8JUNBgu7051dUWuU8veNclocUBOdIo1d1n+kx79ws/Y=",
"issuedCertId": "10925",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "6270"
},
{
"id": "217246660303025238",
"modifiedTime": "1627609436",
"creationTime": "1627602563",
"modifiedBy": "72057594038008981",
"name": "Test-provisioning-key-1",
"fingerprint": "y7wB7e9s0K0/s7Z0fisrThqXmM4iP0MaS6qRDZ/m8t8=",
"issuedCertId": "10817",
"enabled": true,
"listenIps": [
"192.168.97.1"
],
"publishIps": [
"192.168.97.1"
],
"privateBrokerVersion": {
"id": "217246660303025238",
"modifiedTime": "1627669261",
"creationTime": "1627602572",
"modifiedBy": "72057594037928167",
"currentVersion": "21.172.1-1-g16b0894c0",
"systemStartTime": "0",
"applicationStartTime": "1627668835",
"lastConnectTime": "1627668837629824",
"lastDisconnectTime": "1627669260880099",
"platform": "osx20",
"brokerId": "72057594038008982",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "192.168.96.1",
"publicIp": "192.168.96.1",
"loneWarrior": true,
"tunnelId": "SCq71dN8T17K8sj4HitJ",
"upgradeAttempt": "0",
"serviceEdgeGroupId": "217246660303025237"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6270"
},
{
"id": "217246660303025239",
"modifiedTime": "1627663848",
"creationTime": "1627663847",
"modifiedBy": "3",
"name": "Test-provisioning-key-2",
"fingerprint": "an0gBzUTPJJ69FEKDIvRSuP2//IlsCk4Skjd3Z5/xg8=",
"issuedCertId": "10818",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "6270"
}
]
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports a search option to search by features and fields. To search by features and fields:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/73186051597795328/serviceEdgeGroup&search={searchString}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid search string values. The search string values are in the format `fieldName operator fieldValue`. Only search string values that correspond to the values for valid fields and filters are supported. For example, the string `enabled%20EQ%20true` is supported for the **Enabled **filter, using the **Equals **(`EQ`) operator, for the filter value `true`.
For example: `/mgmtconfig/v1/admin/customers/73186051597795328/serviceEdgeGroup&search=enabled%20EQ%20true`.
- [View an example response](#getAllPseGroupsSearch)
[]{
"totalPages": "9",
"totalCount": "9",
"list": [
{
"id": "72057594038043580",
"modifiedTime": "1663345500",
"creationTime": "1626565185",
"modifiedBy": "72057594038078999",
"name": "example-serviceedge-group",
"enabled": true,
"versionProfileId": "0",
"overrideVersionProfile": false,
"versionProfileName": "default",
"versionProfileVisibilityScope": "ALL",
"upgradeTimeInSecs": "25200",
"upgradeDay": "MONDAY",
"isPublic": "FALSE",
"location": "San Jose, CA, USA",
"latitude": "37.3382082",
"longitude": "-121.8863286",
"cityCountry": "San Jose, US",
"countryCode": "US",
"altCloud": "Sample Alt Cloud",
"graceDistanceEnabled": false,
"useInDrMode": false,
"microtenantName": "Default",
"serviceEdges": [
{
"id": "72057594038079110",
"modifiedTime": "1668204817",
"creationTime": "1652812168",
"modifiedBy": "72057594038619644",
"name": "dsfsd-1652812168584",
"description": "test",
"fingerprint": "Test_128",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "22603"
},
{
"id": "72057594038079111",
"creationTime": "1652813096",
"modifiedBy": "3",
"name": "dsfsd-1652813096106",
"fingerprint": "Test_129",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "22603"
},
{
"id": "72057594038079622",
"creationTime": "1653054146",
"modifiedBy": "3",
"name": "dsfsd-1653054146462",
"fingerprint": "Test_130",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "22603"
},
{
"id": "72057594038079623",
"creationTime": "1653054380",
"modifiedBy": "3",
"name": "dsfsd-1653054380848",
"fingerprint": "Test_131",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "22603"
},
{
"id": "72057594038603657",
"creationTime": "1655123985",
"modifiedBy": "3",
"name": "dsfsd-1655123985977",
"fingerprint": "Test_199",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "22603"
},
{
"id": "72057594038603664",
"creationTime": "1655128698",
"modifiedBy": "3",
"name": "dsfsd-1655128694574",
"fingerprint": "Test_202",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "22603"
},
{
"id": "72057594038603668",
"creationTime": "1655129491",
"modifiedBy": "3",
"name": "dsfsd-1655129488391",
"fingerprint": "Test_203",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "22603"
},
{
"id": "72057594038603944",
"creationTime": "1655275522",
"modifiedBy": "3",
"name": "dsfsd-1655275522756",
"fingerprint": "Test_204",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "22603"
},
{
"id": "72057594038603945",
"creationTime": "1655275551",
"modifiedBy": "3",
"name": "dsfsd-1655275551449",
"fingerprint": "Test_205",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "22603"
},
{
"id": "72057594038603946",
"modifiedTime": "1655282990",
"creationTime": "1655276221",
"modifiedBy": "3",
"name": "dsfsd-1655276221504",
"fingerprint": "Test_206",
"issuedCertId": "28362",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "22603"
}
]
}
]
}
If you use the ZPA API PortaI or the [Reference Guide](/zpa/zpa-api/api-developer-reference-guide/reference-guide) to make your API calls, the search field string does not require any characters. For example, `enabled%20EQ%20true` is `enabled EQ true`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of a Particular Private Service Edge Group
To get details for a particular Private Service Edge Group:
- Send a `GET` request to the following endpoint in the Private Service Edge Group Controller: `/mgmtconfig/v1/admin/customers/{customerId}/serviceEdgeGroup/{serviceEdgeGroupId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `serviceEdgeGroupId`: The unique identifier of the Private Service Edge Group.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/serviceEdge/217246660303024722`.
- [View an example response](#ViewExample2)
[]{
"totalPages": "33",
"list": [
{
"id": "217246660303024722",
"modifiedTime": "1618444226",
"creationTime": "1607887129",
"modifiedBy": "72057594038006519",
"name": "1 mp pb group",
"enabled": true,
"isPublic": "FALSE",
"location": "111 Example Way, San Jose, CA 95134, USA",
"upgradeTimeInSecs": "28800",
"upgradeDay": "MONDAY",
"latitude": "37.4181643",
"longitude": "-121.9531325",
"cityCountry": "San Jose, US",
"altCloud": "Sample Alt Cloud",
"countryCode": "US",
"graceDistanceEnabled": false,
"serviceEdges": [
{
"id": "217246660303024723",
"modifiedTime": "1607915744",
"creationTime": "1607887364",
"modifiedBy": "72057594037950342",
"name": "1 mp pb-1",
"fingerprint": "asbErAYZ7/mNUcQhRPd8XFMIRutWjMsWrfot1dDrOOY=",
"issuedCertId": "10591",
"enabled": true,
"listenIps": [
"192.111.111.2"
],
"publishIps": [
"192.111.111.2"
],
"privateBrokerVersion": {
"id": "217246660303024723",
"modifiedTime": "1618419215",
"modifiedBy": "72057594037928167",
"currentVersion": "21.67.2-2-g1a8538e55-dirty",
"systemStartTime": "0",
"applicationStartTime": "1618248071",
"lastConnectTime": "1618417904046524",
"lastDisconnectTime": "1618419214878810",
"platform": "osx20",
"brokerId": "72057594037950451",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "192.111.255.1",
"publicIp": "192.111.255.1",
"loneWarrior": true,
"tunnelId": "m3JSAvHG72PIEWN18iXR",
"previousVersion": "21.26.0-91-g018c50e7f-dirty",
"lastUpgradedTime": "1617857786",
"upgradeAttempt": "0",
"serviceEdgeGroupId": "217246660303024722"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6115"
},
{
"id": "217246660303024725",
"modifiedTime": "1607918700",
"creationTime": "1607918700",
"modifiedBy": "3",
"name": "1 mp pb-2",
"fingerprint": "37As8jQglTtuEr5XXkb1MuMHXeYSLTG0+OLeJneupJE=",
"issuedCertId": "10593",
"enabled": true,
"privateBrokerVersion": {
"id": "217246660303024725",
"modifiedTime": "1607918775",
"creationTime": "1607918704",
"modifiedBy": "72057594037928167",
"expectedVersion": "20.40.2",
"currentVersion": "20.148.2-59-gb3abc04-asan",
"systemStartTime": "10790289",
"applicationStartTime": "1607918770",
"lastConnectTime": "1607918775548271",
"lastDisconnectTime": "1607918775572483",
"platform": "el7",
"brokerId": "72057594037937044",
"restartTimeInSec": "1607932800",
"upgradeStatus": "IN_PROGRESS",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "10.80.1.213",
"publicIp": "199.168.150.161",
"loneWarrior": true,
"tunnelId": "6ZFoRXycAivHanaOk3Ld",
"upgradeAttempt": "1",
"serviceEdgeGroupId": "217246660303024722"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6115"
},
{
"id": "217246660303024726",
"modifiedTime": "1607919146",
"creationTime": "1607919103",
"modifiedBy": "72057594037950342",
"name": "1 mp pb-3",
"fingerprint": "DvW3Bty5CmlRqI5n1pLGWCBRxZPIRMLu5GcRJn2sQpg=",
"issuedCertId": "10594",
"enabled": true,
"listenIps": [
"0.0.0.0"
],
"publishIps": [
"broker1example.sjc5.example.net"
],
"privateBrokerVersion": {
"id": "217246660303024726",
"modifiedTime": "1607920424",
"creationTime": "1607919107",
"modifiedBy": "72057594037928167",
"currentVersion": "20.148.2-60-gb16909d-asan",
"systemStartTime": "4551151",
"applicationStartTime": "1607920165",
"lastConnectTime": "1607920170963047",
"lastDisconnectTime": "1607920424100860",
"platform": "el7",
"brokerId": "72057594037937044",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "10.17.248.46",
"publicIp": "54.67.88.171",
"loneWarrior": true,
"tunnelId": "rrqb/ms0Obfoiknhk77j",
"previousVersion": "20.148.2-59-gb3abc04-asan",
"lastUpgradedTime": "1607920169",
"upgradeAttempt": "0",
"serviceEdgeGroupId": "217246660303024722"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6115"
},
{
"id": "217246660303024755",
"modifiedTime": "1611279015",
"creationTime": "1611279014",
"modifiedBy": "3",
"name": "1 mp pb-4",
"fingerprint": "jFgW0FtrX3BT5bQWRavNViwLLn1GzDxqKT9G3AAFfC0=",
"issuedCertId": "10630",
"enabled": true,
"privateBrokerVersion": {
"id": "217246660303024755",
"modifiedTime": "1611279174",
"creationTime": "1611279019",
"modifiedBy": "72057594037928167",
"currentVersion": "21.20.1-1-gb1bbb0d",
"systemStartTime": "40211",
"applicationStartTime": "1611279165",
"lastConnectTime": "1611279172008161",
"lastDisconnectTime": "1611279173985030",
"platform": "el7",
"brokerId": "72057594037937044",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "172.17.0.2",
"publicIp": "207.47.45.254",
"loneWarrior": true,
"tunnelId": "mPT1qthUYrTHFtxy2SYV",
"upgradeAttempt": "0",
"serviceEdgeGroupId": "217246660303024722"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6115"
},
{
"id": "217246660303024756",
"modifiedTime": "1611279972",
"creationTime": "1611279972",
"modifiedBy": "3",
"name": "1 mp pb-5",
"fingerprint": "C3jWKc1P340Gl9OPFCUiRUHMg5+0i6iQf0LYoT0fQ1w=",
"issuedCertId": "10631",
"enabled": true,
"privateBrokerVersion": {
"id": "217246660303024756",
"modifiedTime": "1611280009",
"creationTime": "1611279977",
"modifiedBy": "72057594037928167",
"currentVersion": "21.20.1-1-gb1bbb0d",
"systemStartTime": "41040",
"applicationStartTime": "1611279993",
"lastConnectTime": "1611280000504792",
"lastDisconnectTime": "1611280009428607",
"platform": "el7",
"brokerId": "72057594037937044",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"privateIp": "172.17.0.2",
"publicIp": "207.47.45.254",
"loneWarrior": true,
"tunnelId": "rjpt0rGVrXlVn/QYZVIn",
"upgradeAttempt": "0",
"serviceEdgeGroupId": "217246660303024722"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6115"
},
{
"id": "217246660303025050",
"modifiedTime": "1621885476",
"creationTime": "1621885476",
"modifiedBy": "3",
"name": "1 mp pb-6",
"fingerprint": "mTjGKNLwROP/GAEiNSnNeZYU0bDdjxT5CFSShPVld+c=",
"issuedCertId": "10758",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "6115"
}
]
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Private Service Edge Group
To update a Private Service Edge Group:
- Provide the updated JSON payload from the [Creating a Private Service Edge Group](#CreateServiceEdgeGroup) section and send a `PUT` request to the following endpoint in the Private Service Edge Group Controller: `/mgmtconfig/v1/admin/customers/{customerId}/serviceEdgeGroup/{serviceEdgeGroupId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `serviceEdgeGroupId`: The unique identifier of the Private Service Edge Group.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/serviceEdge/217246660303025050`.
- [View the JSON payload](#viewJSON2)
[]{
"name": "<Service Edge Group name>",
"description": "<Service Edge Group description>",
"upgradeDay": "<upgradeDay>",
"upgradeTimeInSecs": "<upgradeTimeInSecs>",
"latitude": "<latitude>",
"longitude": "<longitude>",
"location": "<location>",
"graceDistanceEnabled": "false",
"graceDistanceValue": 0,
"graceDistanceValueUnit": "MILES",
"altCloud": "<Sample Alt Cloud name>",
}
A successful response returns code 204, meaning the Private Service Edge Group is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting a Private Service Edge Group
To delete a Private Service Edge Group:
- Send a `DELETE` request to the following endpoint in the Private Service Edge Group Controller: `/mgmtconfig/v1/admin/customers/{customerId}/serviceEdgeGroup/{serviceEdgeGroupId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `serviceEdgeGroupId`: The unique identifier of the Private Service Edge Group.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/serviceEdge/217246660303025050`.
A successful response returns code 204, meaning the Private Service Edge Group is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).