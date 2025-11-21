# Configuring Browser Access Application Segments Using API
Source: https://help.zscaler.com/zpa/configuring-browser-access-application-segments-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484776.pdf

This article provides information on managing Zscaler Private Access (ZPA) browser access application segments using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Prerequisite API Calls
Before you create a new browser access application segment, you must get the following required details:
- Segment group ID. To learn more, see [Configuring Segment Groups Using API](/zpa/configuring-segment-groups-using-api#getSegmentGroups).
- Server group ID. To learn more, see [Configuring Server Groups Using API](/zpa/configuring-server-groups-using-api).
- Certificate ID. To learn more, see [Configuring Certificates Using API](/zpa/configuring-certificates-using-api).
[]Creating a New Browser Access Application Segment
To add a new browser access application segment:
- Send a `POST` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/application` in the application-controller.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057615512764416/application`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload to create browser access application segments and provide the following:
- The name of the application segment
- The domains of the application
- The TCP and UDP ports. You can provide multiple port ranges using the format in the JSON payload. To learn more, see the [Adding Field Descriptions](/zpa/browser-access-application-segment-use-cases#FieldDescriptions) section.
- Protocol
- Certificate
- Other details like segment group and server group IDs
- [View the JSON payload](#Viewthejsonpayload)
[]{
"name":"string",
"description":"string",
"enabled":false,
"healthReporting":"ON_ACCESS",
"ipAnchored":false,
"doubleEncrypt":false,
"bypassType":"NEVER",
"isCnameEnabled":"true",
"tcpPortRange":[
{
"from":"fromPort1",
"to":"toPort1"
},
{
"from":"fromPort2",
"to":"toPort2"
],
"udpPortRange":[
{
"from":"fromPort1",
"to":"toPort1"
},
{
"from":"fromPort2",
"to":"toPort2"
],
"domainNames":[
"domainName or IpAddress"
],
"segmentGroupId":"<segmentGroupId>",
"serverGroups":[
{
"id":"<serverGroupId>"
}
],
"clientlessApps":[
{
"domain":"domainName or IP address",
"name":"string",
"applicationProtocol":"HTTPS",
"applicationPort":"443",
"trustUntrustedCert":true,
"certificateId":"<signingCertId>"
}
]
}
- [View an example response](#Viewanexampleresponse4)
[]{
"modifiedTime": "0",
"creationTime": "0",
"modifiedBy": "string",
"id": "217246660303024813",
"domainNames": [
"testapp.com"
],
"name": "string",
"description": "string",
"defaultIdleTimeout": "0",
"defaultMaxAge": "0",
"serverGroups": [
{
"id": "217246660303020476",
"modifiedTime": "0",
"creationTime": "0",
"modifiedBy": "0",
"name": "Test Server Group",
"enabled": true,
"description": "string",
"configSpace": "DEFAULT",
"dynamicDiscovery": true
}
],
"enabled": true,
"passiveHealthEnabled": true,
"tcpPortRange": [{
"from": "90",
"to": "90"
}],
"doubleEncrypt": false,
"configSpace": "DEFAULT",
"bypassType": "NEVER",
"healthCheckType": "NONE",
"isCnameEnabled": "true",
"clientlessApps": [
{
"id": "0",
"modifiedTime": "0",
"creationTime": "0",
"modifiedBy": "0",
"name": "batestapp.com",
"enabled": true,
"description": "string",
"certificateId": "217246660303022046",
"certificateName": "string",
"applicationPort": "90",
"applicationProtocol": "HTTPS",
"domain": "Example ba test app",
"path": "string",
"hidden": true,
"appId": "217246660303024813",
"trustUntrustedCert": true,
"allowOptions": true,
"cname": "string",
"localDomain": "string"
}
],
"ipAnchored": true,
"healthReporting": "NONE",
"segmentGroupId": "217246660303022382",
"segmentGroupName": "Example BA Test Application"
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the application segment criteria you want to include in the JSON payload. Refer to the [Adding Field Descriptions](/zpa/browser-access-application-segment-use-cases#FieldDescriptions) section for supported values.
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the browser access application segment use cases:
[](/zpa/understanding-health-reporting)
-
-
-
-
-
-
-
-
-
-
-
-
-
[](/zpa/configuring-application-segments#define-cmnconfig)
[](/zpa/configuring-application-segments)
-
-
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| name | Name of the application | Yes | String |
| description | Description of the application | No | String |
| enabled | Whether this application is enabled or not | No | Default: `false`Boolean values: `true`, `false` |
| domainNames | List of domains and IP addresses | Yes | List of string values |
| configSpace | Whether the configuration is created as part of the SIEM or application resource | No | Default: `DEFAULT`Supported values: `DEFAULT`, `SIEM` |
| healthReporting | Whether health reporting for the application is **Continuous** or **On Access**. If `matchStyle` is set to `INCLUSIVE`, then `healthReporting` must be set to either `NONE` or `ON ACCESS`. To learn more, see Understanding Health Reporting. | No | Supported values:`NONE``ON_ACCESS``CONTINUOUS` |
| ipAnchored | If Source IP Anchoring for use with ZIA, is enabled or disabled for the application. If `ipAnchored` is set to true, then `matchStyle` must be set to `EXCLUSIVE`. | No | Default: `false`Boolean values: `true`, `false` |
| doubleEncrypt | Whether Double Encryption is enabled or disabled for the application. If `doubleEncrypt` is true, then the field `matchStyle` must be set to `EXCLUSIVE`. | No | Default: `false`Boolean values: `true`, `false` |
| isCnameEnabled | Indicates if Zscaler Client Connector receives CNAME DNS records from the App Connectors | No | Default: `true`Boolean values: `true`, `false` |
| icmpAccessType | Indicates the ICMP access type | No | Default: `NONE`Supported values:`NONE``PING_TRACEROUTING``PING` |
| bypassType | Indicates whether users can bypass ZPA to access applications | No | Default: `NEVER`Supported values:`ALWAYS``NEVER``ON_NET`The value `NEVER` indicates the use of the client forwarding policy. |
| tcpPortRange | TCP port ranges used to access the application | No | List of valid TCP ports. The port ranges are in the format:`"tcpPortRange":[``{``"from":"fromPort1",``"to":"toPort1"``}``]`For providing multiple ports, use the following format:`"tcpPortRange":[``{``"from":"fromPort1",``"to":"toPort1"``},``{``"from":"fromPort2",``"to":"toPort2"``}``]` |
| udpPortRange | UDP port ranges used to access the application | No | List of valid UDP ports. The port ranges are in the format:`"udpPortRange":[``{``"from":"fromPort1",``"to":"toPort1"``}``]`For providing multiple ports, use the following format:`"udpPortRange":[``{``"from":"fromPort1",``"to":"toPort1"``},``{``"from":"fromPort2",``"to":"toPort2"``}``]` |
| segmentGroupId | ID of the segment group | Yes | Valid segment group ID |
| serverGroups:id | ID of the server group | Yes | Valid server group ID |
| selectConnectorCloseToApp | Whether the App Connector is closest to the application (`true`) or closest to the user (`false`). To learn more, see Configuring Defined Application Segments. | No | Default: `false`Boolean: `true`, `false` |
| clientlessApps | List of clientless or browser access applications. If a list of Browser Access applications are provided, then the field `matchStyle` must be set to `EXCLUSIVE`. |  |  |
| clientlessApps:name | Name of the browser access application | Yes | String |
| clientlessApps:domain | Domain name or IP address of the browser access applications | Yes | String |
| clientlessApps:applicationProtocol | Protocol for the browser access application | Yes | Supported values: `HTTP`, `HTTPS` |
| clientlessApps:applicationPort | Port for the browser access application | Yes | String |
| clientlessApps:trustUntrustedCert | Indicates whether Use Untrusted Certificates is enabled or disabled for a browser access application | No | Default: f`alse`Supported values: t`rue`, `false` |
| clientlessApps:certficateId | ID of the Browser Access certificate | Yes | BA certificate ID |
| clientlessApps:allowOptions | If you want ZPA to forward unauthenticated HTTP preflight OPTIONS requests from the browser to the app | No | Default: `false`Supported values: `true`, `false` |
| matchStyle | Indicates if Multimatch is enabled for the application segment. If enabled (`INCLUSIVE`), the request allows traffic to match multiple applications. If disabled (`EXCLUSIVE`), the request allows traffic to match a single application. A domain can only be `INCLUSIVE` or `EXCLUSIVE`, and any application segment can only contain inclusive or exclusive domains. To learn more, see Configuring Defined Application Segments. | No | Default: `EXCLUSIVE`Supported values:`INCLUSIVE`: All matched applications marked as `INCLUSIVE`, including their domains, protocols, and ports, are selected for application access. This includes the application segments and segment groups marked as `INCLUSIVE` that are selected for the policy evaluation.`EXCLUSIVE`: The first matched application marked as `EXCLUSIVE` is selected for application access. |
Getting Details for a Particular Application Segment
To get application segment details:
- Send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/application/{applicationId}` in the application-controller.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `applicationId`: The particular application segment ID you want to get details for.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/application/217246660302996821`.
- [View an example response](#Viewanexampleresponse5)
[]{
"modifiedTime": "1560983316",
"creationTime": "1560983270",
"modifiedBy": "72057615512764447",
"id": "72057615512764474",
"domainNames": [
"www.oneone.com"
],
"name": "app1",
"serverGroups": [
{
"id": "72057615512764473",
"creationTime": "1560983270",
"modifiedBy": "72057615512764447",
"name": "srvgrp1",
"enabled": true,
"dynamicDiscovery": false,
"configSpace": "DEFAULT"
}
],
"enabled": true,
"passiveHealthEnabled": true,
"tcpPortRange": [{
"from": "80",
"to": "80"
}],
"doubleEncrypt": false,
"segmentGroupId": "72057615512764420",
"segmentGroupName": "Internal Application Group",
"configSpace": "DEFAULT",
"bypassType": "NEVER",
"healthCheckType": "DEFAULT",
"isCnameEnabled": "true",
"clientlessApps": [
{
"id": "72057615512764475",
"modifiedTime": "1560983316",
"creationTime": "1560983270",
"modifiedBy": "72057615512764447",
"name": "www.oneone.com",
"enabled": true,
"certificateId": "72057615512764448",
"certificateName": "Wild Card Cert",
"applicationPort": "80",
"applicationProtocol": "HTTP",
"domain": "www.oneone.com",
"path": "/",
"hidden": false,
"appId": "72057615512764474",
"trustUntrustedCert": false,
"allowOptions": false,
"cname": "67.72057615512764416.h.b.zpa-app.net"
}
],
"ipAnchored": false,
"healthReporting": "ON_ACCESS",
"matchStyle":"EXCLUSIVE"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of All Application Segments
To get details of all application segments:
- Send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/application` in the application-controller.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057615512764416/application`.
- [View an example response](#Viewanexampleresponse6)
[]{
"totalPages": "1",
"list": [
{
"modifiedTime": "1560983316",
"creationTime": "1560983270",
"modifiedBy": "72057615512764447",
"id": "72057615512764474",
"domainNames": [
"www.oneone.com"
],
"name": "app1",
"serverGroups": [
{
"id": "72057615512764473",
"creationTime": "1560983270",
"modifiedBy": "72057615512764447",
"name": "srvgrp1",
"enabled": true,
"dynamicDiscovery": false,
"configSpace": "DEFAULT"
}
],
"enabled": true,
"passiveHealthEnabled": true,
"tcpPortRange": [{
"from": "80",
"to": "80"
}],
"doubleEncrypt": false,
"segmentGroupId": "72057615512764420",
"segmentGroupName": "Internal Application Group",
"configSpace": "DEFAULT",
"bypassType": "NEVER",
"healthCheckType": "DEFAULT",
"isCnameEnabled": "true",
"clientlessApps": [
{
"id": "72057615512764475",
"modifiedTime": "1560983316",
"creationTime": "1560983270",
"modifiedBy": "72057615512764447",
"name": "www.oneone.com",
"enabled": true,
"certificateId": "72057615512764448",
"certificateName": "Wild Card Cert",
"applicationPort": "80",
"applicationProtocol": "HTTP",
"domain": "www.oneone.com",
"path": "/",
"hidden": false,
"appId": "72057615512764474",
"trustUntrustedCert": false,
"allowOptions": false,
"cname": "67.72057615512764416.h.b.zpa-app.net"
}
],
"ipAnchored": false,
"healthReporting": "ON_ACCESS"
},
{
"modifiedTime": "1560990371",
"creationTime": "1560983656",
"modifiedBy": "72057615512764447",
"id": "72057615512764478",
"domainNames": [
"www.onetwo.com"
],
"name": "app2",
"serverGroups": [
{
"id": "72057615512764473",
"creationTime": "1560983270",
"modifiedBy": "72057615512764447",
"name": "srvgrp1",
"enabled": true,
"dynamicDiscovery": false,
"configSpace": "DEFAULT"
}
],
"enabled": true,
"passiveHealthEnabled": true,
"tcpPortRange": [{
"from": "80",
"to": "90"
}],
"doubleEncrypt": false,
"segmentGroupId": "72057615512764420",
"segmentGroupName": "Internal Application Group",
"configSpace": "DEFAULT",
"bypassType": "NEVER",
"healthCheckType": "DEFAULT",
"isCnameEnabled": "true",
"clientlessApps": [
{
"id": "72057615512764479",
"creationTime": "1560983656",
"modifiedBy": "72057615512764447",
"name": "www.onetwo.com",
"enabled": true,
"certificateId": "72057615512764448",
"certificateName": "Wild Card Cert",
"applicationPort": "80",
"applicationProtocol": "HTTP",
"domain": "www.onetwo.com",
"path": "/",
"hidden": false,
"appId": "72057615512764478",
"trustUntrustedCert": false,
"allowOptions": false,
"cname": "68.72057615512764416.h.b.zpa-app.net"
}
],
"ipAnchored": false,
"healthReporting": "ON_ACCESS"
},
{
"modifiedTime": "1564600894",
"creationTime": "1551291935",
"modifiedBy": "72057615512764423",
"id": "72057615512764419",
"domainNames": [
"crm.lanuk.ca",
"test.lanuk.ca"
],
"name": "Internal Application",
"serverGroups": [
{
"id": "72057615512764418",
"modifiedTime": "1560279822",
"creationTime": "1551291935",
"modifiedBy": "72057615512764417",
"name": "Server Group",
"enabled": true,
"dynamicDiscovery": true,
"configSpace": "DEFAULT"
}
],
"enabled": true,
"passiveHealthEnabled": true,
"tcpPortRange": [{
"from": "1",
"to": "65535"
}],
"udpPortRange": [{
"from": "1",
"to": "65535"
}],
"doubleEncrypt": false,
"segmentGroupId": "72057615512764420",
"segmentGroupName": "Internal Application Group",
"configSpace": "DEFAULT",
"bypassType": "NEVER",
"healthCheckType": "DEFAULT",
"isCnameEnabled": "true",
"clientlessApps": [
{
"id": "72057615512764451",
"modifiedTime": "1560286271",
"creationTime": "1560279796",
"modifiedBy": "72057615512764417",
"name": "crm.lanuk.ca",
"enabled": true,
"certificateId": "72057615512764448",
"certificateName": "Wild Card Cert",
"applicationPort": "80",
"applicationProtocol": "HTTP",
"domain": "crm.lanuk.ca",
"path": "/",
"hidden": false,
"appId": "72057615512764419",
"trustUntrustedCert": false,
"allowOptions": false,
"cname": "61.72057615512764416.h.b.zpa-app.net"
}
],
"ipAnchored": false,
"healthReporting": "ON_ACCESS"
},
{
"modifiedTime": "1581028834",
"creationTime": "1574113633",
"modifiedBy": "72057615512764423",
"id": "72057615512764533",
"domainNames": [
"10.0.0.190",
"*.pb.ca"
],
"name": "PB App",
"serverGroups": [
{
"id": "72057615512764545",
"creationTime": "1579729263",
"modifiedBy": "72057615512764417",
"name": "PB App",
"enabled": true,
"dynamicDiscovery": false,
"configSpace": "DEFAULT"
}
],
"enabled": true,
"passiveHealthEnabled": true,
"tcpPortRange": [{
"from": "1",
"to": "65535"
}],
"doubleEncrypt": false,
"segmentGroupId": "72057615512764420",
"segmentGroupName": "Internal Application Group",
"configSpace": "DEFAULT",
"bypassType": "NEVER",
"healthCheckType": "DEFAULT",
"isCnameEnabled": "true",
"ipAnchored": false,
"healthReporting": "ON_ACCESS"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/application` in the application-controller.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer, in the request endpoint.
- Provide valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/application?page=1&pageSize=2`
- [View an example response](#Viewanexampleresponse7)
[]{
"totalPages": "1",
"list": [
{
"modifiedTime": "1648481104",
"creationTime": "1489571905",
"modifiedBy": "144118148382065486",
"id": "144118148382064803",
"domainNames": [
"crm.lanukcorp.com"
],
"name": "CRM AWS",
"description": "Test text",
"serverGroups": [
{
"id": "144118148382064657",
"modifiedTime": "1591165070",
"creationTime": "1452154381",
"modifiedBy": "144118148382064642",
"name": "Do not delete Apps AWS",
"enabled": true,
"configSpace": "DEFAULT",
"dynamicDiscovery": true
}
],
"enabled": true,
"passiveHealthEnabled": true,
"tcpPortRanges": [
"80",
"80"
],
"tcpPortRange": [
{
"from": "80",
"to": "80"
}
],
"doubleEncrypt": false,
"configSpace": "DEFAULT",
"bypassType": "NEVER",
"healthCheckType": "DEFAULT",
"icmpAccessType": "NONE",
"isCnameEnabled": true,
"ipAnchored": false,
"healthReporting": "ON_ACCESS",
"segmentGroupId": "144118148382064801",
"segmentGroupName": "Do not delete"
},
{
"creationTime": "1616227608",
"modifiedBy": "144118148382064667",
"id": "144118148382065459",
"domainNames": [
"api.github.com"
],
"name": "test",
"serverGroups": [
{
"id": "144118148382064657",
"modifiedTime": "1591165070",
"creationTime": "1452154381",
"modifiedBy": "144118148382064642",
"name": "Do not delete Apps AWS",
"enabled": true,
"configSpace": "DEFAULT",
"dynamicDiscovery": true
}
],
"enabled": true,
"passiveHealthEnabled": true,
"tcpPortRanges": [
"1",
"52",
"54",
"65535"
],
"udpPortRanges": [
"1",
"52",
"54",
"65535"
],
"tcpPortRange": [
{
"from": "1",
"to": "52"
},
{
"from": "54",
"to": "65535"
}
],
"udpPortRange": [
{
"from": "1",
"to": "52"
},
{
"from": "54",
"to": "65535"
}
],
"doubleEncrypt": false,
"configSpace": "DEFAULT",
"bypassType": "NEVER",
"healthCheckType": "DEFAULT",
"icmpAccessType": "NONE",
"isCnameEnabled": true,
"ipAnchored": false,
"healthReporting": "ON_ACCESS",
"segmentGroupId": "144118148382064801",
"segmentGroupName": "Do not delete",
"matchStyle":"EXCLUSIVE"
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating an Application Segment
To update an application segment:
- Use the updated JSON payload and send a `PUT` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/application/{applicationId}` in the application-controller.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `applicationId`: The application segment ID for the application segment you want to update.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/application/217246660302996821`.
- [View the entire JSON payload](#Viewthejsonpayload2)
[]{{
"segmentGroupId":"string",
"bypassType":"ALWAYS",
"clientlessApps":[
{
"allowOptions":true,
"appId":0,
"applicationPort":0,
"applicationProtocol":"HTTP",
"certificateId":0,
"certificateName":"string",
"cname":"string",
"creationTime":0,
"description":"string",
"domain":"string",
"enabled":true,
"hidden":true,
"id":0,
"modifiedBy":0,
"modifiedTime":0,
"name":"string",
"path":"string",
"trustUntrustedCert":true
}
],
"isCnameEnabled":"true",
"configSpace":"DEFAULT",
"creationTime":0,
"defaultIdleTimeout":0,
"defaultMaxAge":0,
"description":"string",
"domainNames":[
"string"
],
"doubleEncrypt":true,
"matchStyle":"EXCLUSIVE",
"enabled":true,
"healthCheckType":"DEFAULT",
"healthReporting":"NONE",
"id":"string",
"ipAnchored":true,
"modifiedBy":"string",
"modifiedTime":0,
"name":"string",
"passiveHealthEnabled":true,
"serverGroups":[
{
"id":"<serverGroupId>"
}
]"tcpPortRange":[
{
"from":"fromPort1",
"to":"toPort1"
},
{
"from":"fromPort2",
"to":"toPort2"
}
],
"udpPortRange":[
{
"from":"fromPort1",
"to":"toPort1"
},
{
"from":"fromPort2",
"to":"toPort2"
}
]
}
Refer to the [Adding Field Descriptions](#FieldDescriptions) section for supported values.
A successful response yields `Code 204 - No Response`, meaning the application segment is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting an Application Segment
To delete an application segment:
- Send a `DELETE` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/application/{applicationId}` in the application-controller.
- Use the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `applicationId`: The particular application segment ID you want to get details for.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/application/217246660302996821`.
An object that is referenced in another object cannot be deleted. Error code 400 is returned in this situation.
- [View error code 400](#errorcode)
[]{
"params": [
"Application",
"app 3 created on postman feb 5_edited"
],
"id": "resource.referenced",
"reason": "Resource is being referenced in Application : app 3 created on postman feb 5_edited."
}
A successful response yields `Code 204 - No Response`, meaning the application segment is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).