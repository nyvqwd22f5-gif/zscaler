# Configuring Application Segments Using API
Source: https://help.zscaler.com/zpa/configuring-application-segments-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484781.pdf

This article provides information for managing Zscaler Private Access (ZPA) application segments using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Prerequisite API Calls
Before you create an application segment, enable or disable AppProtection on an existing application segment, or enable AppProtection on a new application segment, you must get the following required details:
- Details of all application segments. To learn more, see [Getting Details of All Application Segments](#getAppSegments).
- Segment group IDs. To learn more, see [Configuring Segment Groups Using API](/zpa/configuring-segment-groups-using-api#getSegmentGroups).
- Server Group IDs. To learn more, see [Configuring Server Groups Using API](/zpa/configuring-server-groups-using-api).
- Certificate ID. To learn more, see [Configuring Certificates Using API](/zpa/configuring-certificates-using-api).
[]Creating an Application Segment
To create an application segment:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/application`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057615512764416/application`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the entire JSON payload to create an application segment and provide the following:
- The name of the application segment.
- The domains of the application. To learn more, see [Adding Field Descriptions](#FieldDescriptions).
- The TCP and UDP ports. You can provide multiple port ranges using the format in the entire JSON payload. To learn more, see [Adding Field Descriptions](#FieldDescriptions).
- Other details like the segment group and server group IDs.
- [View the entire JSON payload](#Viewthejsonpayload)
[]{
"segmentGroupId":"string",
"segmentGroupName":"string",
"autoAppProtectEnabled":true,
"bypassOnReauth":"false",
"inspectTrafficWithZia":false,
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
"enabled":true,
"healthCheckType":"DEFAULT",
"healthReporting":"NONE",
"id":"string",
"ipAnchored":true,
"matchStyle":"EXCLUSIVE",
"modifiedBy":"string",
"modifiedTime":0,
"name":"string",
"passiveHealthEnabled":true,
"selectConnectorCloseToApp":true,
"serverGroups":[
{
"configSpace":"DEFAULT",
"creationTime":0,
"description":"string",
"enabled":true,
"id":0,
"learningEnabled":true,
"modifiedBy":0,
"modifiedTime":0,
"name":"string"
}
],
"tcpPortRange":[
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
- [View the minimum criteria JSON payload](#Viewthebareminimumjsonpayload)
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
}
],
"domainNames":[
"domainName or IpAddress"
],
"segmentGroupId":"<segmentGroupId>",
"selectConnectorCloseToApp":true,
"serverGroups":[
{
"id":"<serverGroupId>"
}
]
}
- [View the example response](#Viewanexampleresponse3)
[]{
"id":"72057594038648257",
"name":"Test Example",
"domainNames":[
"exampletest.com"
],
"enabled":true,
"passiveHealthEnabled":true,
"tcpPortRanges":[
"335",
"335"
],
"udpPortRanges":[
"445",
"445"
],
"doubleEncrypt":false,
"segmentGroup":{
"id":"72057594038071913",
"name":"123",
"enabled":true,
"configSpace":"DEFAULT",
"tcpKeepAliveEnabled":"0"
},
"serverGroupDTOs":[
{
"modifiedTime":"1646056922",
"creationTime":"1612438082",
"modifiedBy":"72057594038052745",
"id":"72057594037988579",
"microtenantName":"Default",
"enabled":true,
"name":"1234",
"learningEnabled":true,
"description":"/><img src=x onerror=alert(document.cookie)>",
"ConnectorGroups":[
{
"id":"72057594037962495",
"name":"yo111",
"useInDrMode":false,
"siemConnectorGroup":false
},
{
"id":"72057594038010497",
"name":"Abcdefg12",
"useInDrMode":false,
"siemConnectorGroup":false
},
{
"id":"72057594038011104",
"name":"App_Connector_Test",
"useInDrMode":false,
"siemConnectorGroup":false
},
{
"id":"72057594038011105",
"name":"App_Connector_Test_1",
"useInDrMode":false,
"siemConnectorGroup":false
},
{
"id":"72057594038011107",
"name":"App_Connector_Test_10_ITER1_PRA_ENABLED",
"useInDrMode":false,
"siemConnectorGroup":false
}
],
"ipAnchored":false,
"configSpace":"DEFAULT",
"restrictedEntity":false
}
],
"configSpace":"DEFAULT",
"bypassType":"NEVER",
"healthCheckType":"DEFAULT",
"icmpAccessType":"NONE",
"ipAnchored":false,
"autoAppProtectEnabled":true,
"bypassOnReauth":"false",
"inspectTrafficWithZia":false,
"cnameConfig":"NOFLATTEN",
"isCnameEnabled":true,
"commonAppsDto":{
},
"healthReporting":"ON_ACCESS",
"tcpKeepAlive":"0",
"selectConnectorCloseToApp":false,
"useInDrMode":false,
"matchStyle":"EXCLUSIVE"
}
An error is returned if **Inspect Traffic with ZIA** is not enabled on your tenant and `InspectTrafficWithZia` is passed as enabled when making a `POST` or `PUT` request. The following is an example error:
`{
"params":[
"inspectTrafficWithZia",
"testApplication,
"feature.application.inspect_traffic_with_zia",
"72057594037927936"
],
"id":"config.change.not.allowed.sku.not.enabled",
"reason":"Cannot update config inspectTrafficWithZia of testApplication as this is managed by SKU feature.application.inspect_traffic_with_zia which is not enabled for customer 72057594037927936"
}   `
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the application segment criteria you want to include in the JSON payload. You can also use the minimum criteria JSON payload to create an application segment. Refer to the [Adding Field Descriptions](#FieldDescriptions) section for supported values.
AD Protection Support
To create an application segment and enable [Active Directory Inspection](/zpa/configuring-application-segments#ADProtection):
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/application`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057615512764416/application`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the entire JSON payload to create an application segment and provide the following:
- The name of the application segment.
- The domains of the application.
- The TCP and UDP ports. You can provide multiple port ranges using the format in the entire JSON payload. To learn more, see the [Adding Field Descriptions](#FieldDescriptions) section.
- Other details like the segment group and server group IDs.
-
Set `adpEnabled` as `true`. This field is highlighted in the JSON payload.
If `adpEnabled` is set to `true`, then `autoAppProtectEnabled` cannot be set to `true` for inspection by AppProtection. To learn more, see the [Adding Field Descriptions](#fieldDescriptions) section.
- TCP and UDP protocols. These fields are highlighted in the JSON payload. To learn more, see the [Adding Field Descriptions](#FieldDescriptions) section.
- [View the JSON payload](#AdProtectionPostPayload)
[]{
"matchStyle":"EXCLUSIVE",
"enabled":true,
"healthReporting":"ON_ACCESS",
"ipAnchored":false,
"selectConnectorCloseToApp":false,
"icmpAccessType":"NONE",
"isCnameEnabled":true,
"tcpKeepAlive":"0",
"name":"Example Application Segment",
"useInDrMode":false,
"description":"",
"adpEnabled":true,
"domain":"exampleApp.com",
"trustUntrustedCert":true,
"allowOptions":false,
"doubleEncrypt":false,
"commonAppsDto":{
"appsConfig":[
{
"domainJson":{
"domain":""
},
"showADInspectionToggle":true,
"viewId":"3814358737_2917168947",
"isEmptyModel":false,
"domain":"exampleapp.com",
"name":"exampleapp.com",
"protocols":[
"LDAP",
"SMB",
"KERBEROS"
],
"applicationProtocol":"NONE",
"certificateId":null,
"applicationPort":0,
"trustUntrustedCert":false,
"allowOptions":false,
"localDomain":"",
"adpEnabled":true,
"appTypes":[
"INSPECT"
],
"enabled":true
}
]
},
"bypassType":"NEVER",
"tcpPortRanges":[
"443",
"443"
],
"tcpProtocols":[
"LDAP"
],
"udpPortRanges":[
"334",
"334"
],
"udpProtocols":[
"KERBEROS"
],
"domainNames":[
"exampleApp.com"
],
"hideDependencies":true,
"segmentGroup":{
"enabled":true,
"tcpKeepAliveEnabled":0,
"skipDetailedAppInfo":false,
"objectType":"segmentGroup",
"name":"Example Segment Group",
"description":"",
"applications":[
]
},
"serverGroupDTOs":[
{
"enabled":true,
"learningEnabled":true,
"objectType":"ServerGroup",
"name":"Example Server Group",
"description":"",
"servers":[
],
"ConnectorGroups":[
{
"id":"72057594038010497",
"name":"Abcdefg12"
}
]
}
],
"serverGroups":[
{
"id":{
"enabled":true,
"learningEnabled":true,
"objectType":"ServerGroup",
"name":"Example Server Group",
"description":"",
"servers":[
],
"ConnectorGroups":[
{
"id":"72057594038010497",
"name":"Abcdefg12"
}
]
}
}
]
}
- [View an example response](#AdProtectionPostExample)
[]{
"id":"72057594038668832",
"name":"Example Application Segment",
"domainNames":[
"exampleapp.com"
],
"enabled":true,
"passiveHealthEnabled":true,
"tcpPortRanges":[
"443",
"443"
],
"udpPortRanges":[
"334",
"334"
],
"doubleEncrypt":false,
"segmentGroup":{
"id":"72057594038668830",
"modifiedTime":"1691079323",
"creationTime":"1691079323",
"modifiedBy":"72057594038040687",
"name":"Example Segment Group",
"enabled":true,
"configSpace":"DEFAULT",
"tcpKeepAliveEnabled":"0"
},
"serverGroupDTOs":[
{
"id":"72057594038668831",
"enabled":true,
"name":"Example Server Group",
"learningEnabled":true,
"ConnectorGroups":[
{
"id":"72057594038010497",
"name":"Abcdefg12",
"useInDrMode":false,
"wafDisabled":false,
"siemConnectorGroup":false
}
],
"ipAnchored":false,
"configSpace":"DEFAULT"
}
],
"configSpace":"DEFAULT",
"bypassType":"NEVER",
"healthCheckType":"DEFAULT",
"icmpAccessType":"NONE",
"ipAnchored":false,
"bypassOnReauth":false,
"inspectTrafficWithZia":false,
"cnameConfig":"NOFLATTEN",
"isCnameEnabled":true,
"commonAppsDto":{
"appsConfig":[
{
"name":"exampleapp.com",
"enabled":true,
"applicationPort":"0",
"applicationProtocol":"NONE",
"domain":"exampleapp.com",
"hidden":false,
"portal":false,
"appId":"72057594038668832",
"trustUntrustedCert":false,
"allowOptions":false,
"appTypes":[
"INSPECT"
],
"protocols":[
"LDAP",
"SMB",
"KERBEROS"
],
"adpEnabled":true
}
]
},
"healthReporting":"ON_ACCESS",
"tcpKeepAlive":"0",
"selectConnectorCloseToApp":false,
"useInDrMode":false,
"matchStyle":"EXCLUSIVE",
"tcpProtocols":[
"LDAP"
],
"udpProtocols":[
"KERBEROS"
],
"adpEnabled":true
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the application segment criteria you want to include in the JSON payload. Refer to the [Adding Field Descriptions](#FieldDescriptions) section for supported values.
[]AppProtection Support
To create a new application segment and enable AppProtection on an application:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/application`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/application`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- The name of the application segment.
- The domains of the application.
- The TCP and UDP ports.
- Other details like segment group and server group IDs.
- `Ensure "appTypes": ["INSPECT"]` and the other fields in `"commonAppsDto"` are included in the JSON payload. These fields are highlighted in red.
- [View the JSON payload](#jsonPayload7)
[]{
"name":"string",
"description":"string",
"matchStyle": "EXCLUSIVE",
"enabled":true,
"healthReporting":"ON_ACCESS",
"ipAnchored":false,
"doubleEncrypt":false,
"bypassType":"NEVER",
"isCnameEnabled":true,
"tcpPortRanges":[
"from",
"to"
],
"udpPortRanges":[
"from",
"to"
],
"domainNames":[
"domainName"
],
"serverGroups":[
{
"id":"<serverGroupId>"
}
],
"segmentGroupId":"<segmentGroupId>",
"commonAppsDto":{
"appsConfig":[
{
"name":"string",
"domain":"<domainName>",
"applicationProtocol":"HTTP",
"applicationPort":"80",
"appTypes":[
"INSPECT"
],
"enabled":true
}
]
}
}
- [View the example response](#exampleResponse7)
[]{
"id":"72057594038079016",
"domainNames":[
"inspect.com"
],
"name":"WAAP_Public_API_1",
"description":"WAAP Public API One",
"serverGroups":[
{
"id":"72057594038048851",
"enabled":false,
"configSpace":"DEFAULT",
"dynamicDiscovery":false
}
],
"enabled":true,
"passiveHealthEnabled":true,
"tcpPortRanges":[
"80",
"88"
],
"udpPortRanges":[
"90",
"98"
],
"doubleEncrypt":false,
"configSpace":"DEFAULT",
"bypassType":"NEVER",
"healthCheckType":"DEFAULT",
"icmpAccessType":"NONE",
"isCnameEnabled":true,
"commonAppsDto":{
"appsConfig":[
{
"name":"common_app",
"enabled":true,
"applicationPort":"80",
"applicationProtocol":"HTTP",
"domain":"inspect.com",
"hidden":false,
"portal":false,
"appId":"72057594038079016",
"trustUntrustedCert":false,
"allowOptions":false,
"appTypes":[
"INSPECT"
]
}
]
},
"ipAnchored":false,
"healthReporting":"ON_ACCESS",
"segmentGroupId":"72057594037988995",
"matchStyle":"EXCLUSIVE"
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
When creating an application segment with AppProtection enabled, the field `matchStyle` must be set to `EXCLUSIVE`. To learn more, see [Adding Field Descriptions](#FieldDescriptions).
[]Microtenant Support
To move an application segment from one Microtenant to the Default Microtenant and vice-versa:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/application/{applicationId}/move`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `applicationId`: The ID of the application.
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/application/72057594038642786/move`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- `targetSegmentGroupId`: The unique identifier of the target segment group that the application segment is being moved to.
- `targetMicroTenantId`: The unique identifier of the Microtenant that the application segment is being moved to. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
- `targetServerGroupId`: The unique identifier of the target server group that the application segment is being moved to. To learn more, see [Configuring Server Groups using API](/zpa/configuring-server-groups-using-api).
Browser Access on an application segment does not persist if the application segment is moved from the default Microtenant to another Microtenant. You must select the web server certificate after the application segment is moved.
- [View the JSON payload](#MicrotenantPostPayload)
[]
{
"targetSegmentGroupId": <targetSegmentGroupId>,
"targetMicrotenantId": <targetMicroTenantId>,
"targetServerGroupId": <targetServerGroupId>
}
- [View the sample JSON payload](#MicrotenantPostSamplePayload)
[]{
"targetMicrotenantId":"73201978410270733",
"targetServerGroupId":"73201978410273451",
"targetSegmentGroupId":"73201978410273450"
}
The pre- and post-configuration changes for any successful move operation can be viewed and downloaded in the [Audit Logs](/zpa/about-audit-logs#config).
A successful response returns code 204. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Privileged Remote Access Support
To create a new application segment with Privileged Remote Access (PRA) enabled on an application:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/application`.
- Provide the `customerId`, the ZPA tenant ID of the customer, following in the request endpoint.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- Name of the application segment
- Domains of the application
- TCP and UDP ports
- Segment Group ID
- Server Group ID
- Ensure `"appTypes": ["SECURE_REMOTE_ACCESS"]` and the other fields in `"commonAppsDto"` are included in the JSON payload.
- [View the JSON payload](#postPraPayload)
[]
`{
"name":"<NAME>",
"commonAppsDto":{
"appsConfig":[
{
"name":"<NAME>",
"domain":"<DOMAIN_NAME>",
"appTypes":[
"SECURE_REMOTE_ACCESS"
],
"applicationPort":"3389",
"applicationProtocol":"RDP",
"connectionSecurity":"ANY",
"enabled":true
}
]
},
"segmentGroup":{
"enabled":true,
"tcpKeepAliveEnabled":0,
"skipDetailedAppInfo":false,
"name":"<Server Group Name>",
"applications":[
]
},
"tcpPortRanges":[
"<port_from>",
"<port_to>"
],
"udpPortRanges":[
"<port_from>",
"<port_to>"
],
"domainNames":[
"<DOMAIN_NAME>"
]
}    `
- [View an example JSON payload](#praPostSamplePayload)
[]
`{
"name":"test-pra-app3",
"commonAppsDto":{
"appsConfig":[
{
"name":"testdomain3",
"domain":"testdomain3",
"appTypes":[
"SECURE_REMOTE_ACCESS"
],
"applicationPort":"3389",
"applicationProtocol":"RDP",
"connectionSecurity":"ANY",
"enabled":true
}
]
},
"applicationGroup":{
"enabled":true,
"tcpKeepAliveEnabled":0,
"skipDetailedAppInfo":false,
"name":"Internal Application Group2",
"applications":[
]
},
"tcpPortRanges":[
"3389",
"3389"
],
"udpPortRanges":[
"3389",
"3389"
],
"domainNames":[
"testdomain3"
]
} `
- [View the example response](#PostPraResponse)
[]
`{
"name":"Sample app segment",
"description":"sample app segment",
"enabled":true,
"healthReporting":"ON_ACCESS",
"ipAnchored":false,
"doubleEncrypt":false,
"bypassType":"NEVER",
"isCnameEnabled":true,
"tcpPortRanges":[
"443",
"443"
],
"domainNames":[
"domain.com"
],
"udpPortRanges":[
],
"segmentGroupId":"72057594038043583",
"serverGroups":[
{
"id":"72057594037988996"
}
],
"commonAppsDto":{
"appsConfig":[
{
"name":"domain.com",
"domain":"domain.com",
"applicationProtocol":"HTTPS",
"certificateId":"72057594038037594",
"applicationPort":"443",
"appTypes":[
"SECURE_REMOTE_ACCESS"
],
"enabled":true
}
]
}
}`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the application segment use cases:
[](/zpa/using-pattern-matching-application-segments)[](/zpa/configuring-defined-application-segments#define-cmnconfig)
-
-
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
-
-
[](/zpa/about-api-keys)[](/zpa/configuring-microtenants-using-api)[](/zpa/configuring-application-segments#tab1)
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
[](/zpa/configuring-application-segments#define-clientconnector)
[](/zpa/configuring-application-segments#define-generalinfo)
[](/zpa/configuring-application-segments)
-
-
[](/zpa/configuring-application-segments)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| name | Name of the application | Yes | String |
| description | Description of the application | No | String |
| enabled | Whether this application is enabled or not | No | Default: `false`Supported values: `true`, `false` |
| domainNames | List of domains and IP addresses. When creating or updating an application segment using the ZPA cloud service API, ZPA supports domains that contain asterisks (*) and question marks (?) within the prefix of top-level domains (i.e., TLD+1). To support the application pattern match, `matchStyle` must be set to `INCLUSIVE` (i.e., Multimatch must be enabled). To learn more, see Using Pattern Matching for Application Segments and Configuring Defined Application Segments. | Yes | List of string values |
| configSpace | Whether the configuration is created as part of the SIEM or the application segment | No | Default: `DEFAULT`Supported values:`DEFAULT``SIEM` |
| healthReporting | Whether health reporting for the app is Continuous or On Access. If `matchStyle` is set to `INCLUSIVE`, then `healthReporting` must be set to either `NONE` or `ON ACCESS`. To learn more, see Understanding Health Reporting. | No | Supported values:`NONE``ON_ACCESS``CONTINUOUS` |
| ipAnchored | Whether Source IP Anchoring for use with ZIA is enabled or disabled for the app. If `ipAnchored` is set to `true`, then `matchStyle` must be set to `EXCLUSIVE`. | No | Default: `false`Supported: `true`, `false` |
| doubleEncrypt | Whether Double Encryption is enabled or disabled for the app. If `doubleEncrypt` is set to `true`, then `matchStyle` must be set to `EXCLUSIVE`. | No | Default: `false`Boolean: `true`, `false` |
| isCnameEnabled | Indicates if Zscaler Client Connector receives CNAME DNS records from the connectors | No | Default: `true`Boolean: `true`, `false` |
| icmpAccessType | Indicates the ICMP access type | No | Default: `NONE`Supported values:`NONE``PING_TRACEROUTING``PING` |
| bypassType | Indicates whether users can bypass ZPA to access applications | No | Default: `NEVER`Supported values:`ALWAYS``NEVER``ON_NET`The value `NEVER` indicates the use of the client forwarding policy. |
| tcpPortRange | TCP port ranges used to access the app | No | List of valid TCP ports. The application segment API supports multiple TCP and UDP port ranges. The port ranges are in the format:`"tcpPortRange":[``{``"from":"fromPort1",``"to":"toPort1"``}``]`For providing multiple ports, use the following format:`"tcpPortRange":[``{``"from":"fromPort1",``"to":"toPort1"``},``{``"from":"fromPort2",``"to":"toPort2"``}``]]` |
| updPortRange | UDP port ranges used to access the app | No | List of valid UDP ports. The port ranges are in the format:`"udpPortRange":[``{``"from":"fromPort1",``"to":"toPort1"``}``]`For providing multiple ports, use the following format:`"udpPortRange":[``{``"from":"fromPort1",``"to":"toPort1"``},``{``"from":"fromPort2",``"to":"toPort2"``}``]` |
| tcpPortRanges | TCP port ranges used to access the app. Note that this field will be deprecated in a future release. |  | List of valid TCP ports. The port ranges are in the format:`"tcpPortRanges":[``"from",``"to"``]`For providing multiple ports, use the following format:`"tcpPortRanges":[``"fromPort1",``"toPort1",``"fromPort2",``"toPort2"``]` |
| udpPortRanges | UDP port ranges used to access the app. Note that this field will be deprecated in a future release. |  | List of valid UDP ports. The port ranges are in the format:`"udpPortRanges":[``"from",``"to"``]`For providing multiple ports, use the following format:`"udpPortRanges":[``"fromPort1",``"toPort1",``"fromPort2",``"toPort2"``]` |
| segmentGroupId | ID of the segment group | Yes | A valid segment group ID |
| segmentGroupName | Name of the segment group. Not required for `PUT` and `POST` requests. | No | String |
| serverGroups:id | ID of the server group | Yes | A valid server group ID |
| serverGroups:name | Name of the server group. Not required for `PUT` and `POST` requests. | No | String |
| selectConnectorCloseToApp | Whether the App Connector is closest to the application (`True`) or closest to the user (`False`). | No | Default: `false`Boolean: `true`, `false` |
| clientlessApps | List of clientless or Browser Access applications. If a list of Browser Access applications are provided, then the field `matchStyle` must be set to `EXCLUSIVE`. | No |  |
| commonAppsDto | List of applications (e.g., AppProtection, Privileged Remote Access, or Browser Access). If AppProtection or Browser Access applications are provided, then the field `matchStyle` must be set to `EXCLUSIVE`. | Yes |  |
| commonAppsDto.appsconfig | List of applications to be configured | Yes |  |
| commonAppsDto.appsConfig.name | Name of the AppProtection or Privileged Remote Access application | Yes | String |
| commonAppsDto.appsConfig.domain | Domain name of the AppProtection or Privileged Remote Access application | Yes | String |
| commonAppsDto.appsConfig.applicationProtocol | Protocol for the Privileged Console or AppProtection application | Yes | Supported values:`HTTP``HTTPS``RDP``SSH``VNC` |
| commonAppsDto.appsConfig.certificateId | ID of the signing certificate. This field is required if the `applicationProtocol` is set to `HTTPS`. The `certificateId` is not supported if the `applicationProtocol` is set to `HTTP`. | Yes | A valid certificate ID |
| commonAppsDto.appsConfig.applicationPort | Port for the AppProtection or Privileged Remote Access application | Yes | String |
| commonAppsDto.appsConfig.connectionSecurity | The connection security mode for the application | Yes | StringFor `RDP`, the supported values are:`ANY``NLA``TLS``RDP` |
| commonAppsDto.appsConfig.appTypes | Indicates the type of application | Yes | StringSupported values:`INSPECT`: AppProtection`SECURE_REMOTE_ACCESS`: Privileged Remote Access |
| commonAppsDto.appsConfig.enabled | Whether this application is enabled or not | Yes | String |
| commonAppsDto.deletedInspectApps | Indicates the AppProtection application to be disabled | Yes | A valid application ID |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. Pass `microtenantId` as null to retrieve data from all Microtenants associated with the tenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
| targetSegmentGroupId | The unique identifier of the target segment group that the application segment is being moved to. This field is required if you want to move an application segment. | No | Integer |
| targetMicrotenantId | The unique identifier of the Microtenant that the application segment is being moved to. This field is required if you want to move an application segment. | No | Integer |
| targetServerGroupId | The unique identifier of the target server group that the application segment is being moved to. This field is required if you want to move an application segment. | No | Integer |
| shareToMicrotenants | The unique identifier of the Microtenant that the application segment is being shared to. This field is required if you want to share an application segment. | No | Integer |
| adpEnabled | Indicates if Active Directory Inspection is enabled or not for the application. This allows the application segment's traffic to be inspected by Active Directory (AD) Protection. By default, this field is set to false. If `adpEnabled` is set to true, then the field `matchStyle` must be set to `EXCLUSIVE`. If `adpEnabled` is set to `true`, then `autoAppProtectEnabled` cannot be set to `true`. To learn more, see Configuring Defined Application Segments. | No | BooleanSupported values: `true`, `false` |
| protocols | Indicates the AD Protection protocols to be inspected on the application. This field is only required if `adpEnabled` is set to `true`. | No | StringSupported values:`LDAP``SMB``KERBEROS` |
| tcpProtocols | Indicates the AD Protection protocols to be inspected on the specified TCP port ranges. This field is only required if `adpEnabled` is set to `true`. | No | StringSupported values:`NONE``LDAP``SMB``KERBEROS` |
| udpProtocols | Indicates the AD Protection protocols to be inspected on the specified UDP port ranges. This field is only required if `adpEnabled` is set to `true`. | No | StringSupported values:`NONE``LDAP``SMB``KERBEROS` |
| bypassOnReauth | Indicates if **Bypass During Reauthentication** is enabled for the application. To learn more, see Configuring Defined Application Segments. | No | Default: `false`Boolean: `true`, `false` |
| inspectTrafficWithZia | Indicates if **Inspect Traffic with ZIA** is enabled for the application. When enabled, this leverages a single posture for securing internet/SaaS and private applications, and applies Data Loss Prevention policies to the application segment you are creating. To learn more, see Configuring Defined Application Segments. | No | Default: `false`Boolean: `true`, `false` |
| matchStyle | Indicates if Multimatch is enabled for the application segment. If enabled (`INCLUSIVE`), the request allows traffic to match multiple applications. If disabled (`EXCLUSIVE`), the request allows traffic to match a single application. A domain can only be `INCLUSIVE` or `EXCLUSIVE`, and any application segment can only contain inclusive or exclusive domains. To learn more, see Configuring Defined Application Segments. | No | Default: `EXCLUSIVE`Supported values:`INCLUSIVE`: All matched applications marked as `INCLUSIVE`, including their domains, protocols, and ports, are selected for application access. This includes the application segments and segment groups marked as `INCLUSIVE` that are selected for the policy evaluation.`EXCLUSIVE`: The first matched application marked as `EXCLUSIVE` is selected for application access. |
| autoAppProtectEnabled | If `autoAppProtectEnabled` is set to `true`, this field indicates if the application segment’s traffic is inspected by AppProtection. If set to `true`, a valid AppProtection enrollment certificate must be generated to inspect application segment traffic by AppProtection. If `adpEnabled` is set to `true` for Active Directory Inspection, then `autoAppProtectEnabled` cannot be true. To learn more, see Configuring Defined Application Segments. | No | Boolean: `true`, `false` |
| weightedLoadBalancing | Indicates if the application load balancing configuration for application segments is enabled (`true`) or disabled (`false`). This field is not supported when sending a `POST` request to the `/mgmtconfig/v1/admin/customers/{customerId}/application` endpoint to create an application segment, or when sending a `PUT` request to the `/mgmtconfig/v1/admin/customers/{customerId}/application/{applicationId}` endpoint to update an application segment. | No | Boolean: `true`, `false` |
Getting Details for a Particular Application Segment
To get application segment details:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/application/{applicationId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `applicationId`: The particular application segment ID you want to get details for.
For example: `/mgmtconfig/v1/admin/customers/144118148382064640/application/144118148382065748`.
- [View an example response](#Viewanexampleresponse4)
[]{
"modifiedTime": "1716571633",
"creationTime": "1716571633",
"modifiedBy": "144118148382064930",
"id": "144118148382065748",
"domainNames": [
"example.com"
],
"name": "Copy of Test App Segment",
"serverGroups": [
{
"id": "144118148382064812",
"modifiedTime": "1584421166",
"creationTime": "1492592504",
"modifiedBy": "144118148382064930",
"name": "161_sg",
"enabled": true,
"description": "DESC - u",
"configSpace": "DEFAULT",
"weight": "0",
"passive": false,
"extranetEnabled": false,
"dynamicDiscovery": false
}
],
"enabled": true,
"passiveHealthEnabled": true,
"tcpPortRanges": [
"89",
"90"
],
"tcpPortRange": [
{
"from": "89",
"to": "90"
}
],
"doubleEncrypt": false,
"configSpace": "DEFAULT",
"bypassType": "NEVER",
"healthCheckType": "DEFAULT",
"icmpAccessType": "NONE",
"isCnameEnabled": true,
"ipAnchored": false,
"bypassOnReauth": false,
"inspectTrafficWithZia": false,
"healthReporting": "ON_ACCESS",
"useInDrMode": false,
"tcpKeepAlive": "0",
"selectConnectorCloseToApp": false,
"matchStyle": "EXCLUSIVE",
"isIncompleteDRConfig": false,
"adpEnabled": false,
"autoAppProtectEnabled": false,
"apiProtectionEnabled": false,
"fqdnDnsCheck": false,
"weightedLoadBalancing": false,
"extranetEnabled": false,
"microtenantName": "Default",
"segmentGroupId": "144118148382065533",
"segmentGroupName": "exampleSegmentGroup"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details for All Application Segments
To get details of all application segments:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/application`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the endpoint. For example: `/mgmtconfig/v1/admin/customers/72057615512764416/application`.
- [View an example response](#Viewanexampleresponse5)
[]{
"totalPages":"1",
"list":[
{
"modifiedTime":"1560983316",
"creationTime":"1560983270",
"modifiedBy":"72057615512764447",
"id":"72057615512764474",
"domainNames":[
"www.oneone.com"
],
"name":"app1",
"serverGroups":[
{
"id":"72057615512764473",
"creationTime":"1560983270",
"modifiedBy":"72057615512764447",
"name":"srvgrp1",
"enabled":true,
"learningEnabled":false,
"configSpace":"DEFAULT"
}
],
"enabled":true,
"passiveHealthEnabled":true,
"tcpPortRange":[
{
"from":"80",
"to":"80"
}
],
"doubleEncrypt":false,
"segmentGroupId":"72057615512764420",
"segmentGroupName":"Internal Application Group",
"configSpace":"DEFAULT",
"bypassType":"NEVER",
"healthCheckType":"DEFAULT",
"isCnameEnabled":"true",
"clientlessApps":[
{
"id":"72057615512764475",
"modifiedTime":"1560983316",
"creationTime":"1560983270",
"modifiedBy":"72057615512764447",
"name":"www.oneone.com",
"enabled":true,
"certificateId":"72057615512764448",
"certificateName":"Wild Card Cert",
"applicationPort":"80",
"applicationProtocol":"HTTP",
"domain":"www.oneone.com",
"path":"/",
"hidden":false,
"appId":"72057615512764474",
"trustUntrustedCert":false,
"allowOptions":false,
"cname":"67.72057615512764416.h.b.zpa-app.net"
}
],
"icmpAccessType":"NONE",
"ipAnchored":false,
"bypassOnReauth":false,
"inspectTrafficWithZia":false,
"healthReporting":"ON_ACCESS",
"useInDrMode":"false",
"tcpKeepAlive":"0",
"selectConnectorCloseToApp":false,
"adpEnabled":false,
"autoAppProtectEnabled":false,
"isIncompleteDRConfig":false,
"microtenantName":"Default",
"segmentGroupId":"217246660303026632",
"segmentGroupName":"test-app-seg-group",
"matchStyle":"EXCLUSIVE"
},
{
"modifiedTime":"1560990371",
"creationTime":"1560983656",
"modifiedBy":"72057615512764447",
"id":"72057615512764478",
"domainNames":[
"www.onetwo.com"
],
"name":"app2",
"serverGroups":[
{
"id":"72057615512764473",
"creationTime":"1560983270",
"modifiedBy":"72057615512764447",
"name":"srvgrp1",
"enabled":true,
"learningEnabled":false,
"configSpace":"DEFAULT"
}
],
"enabled":true,
"passiveHealthEnabled":true,
"tcpPortRange":[
{
"from":"80",
"to":"90"
}
],
"doubleEncrypt":false,
"segmentGroupId":"72057615512764420",
"segmentGroupName":"Internal Application Group",
"configSpace":"DEFAULT",
"bypassType":"NEVER",
"healthCheckType":"DEFAULT",
"isCnameEnabled":"true",
"clientlessApps":[
{
"id":"72057615512764479",
"creationTime":"1560983656",
"modifiedBy":"72057615512764447",
"name":"www.onetwo.com",
"enabled":true,
"certificateId":"72057615512764448",
"certificateName":"Wild Card Cert",
"applicationPort":"80",
"applicationProtocol":"HTTP",
"domain":"www.onetwo.com",
"path":"/",
"hidden":false,
"appId":"72057615512764478",
"trustUntrustedCert":false,
"allowOptions":false,
"cname":"68.72057615512764416.h.b.zpa-app.net"
}
],
"ipAnchored":false,
"bypassOnReauth":false,
"inspectTrafficWithZia":false,
"healthReporting":"ON_ACCESS",
"matchStyle":"EXCLUSIVE"
},
{
"modifiedTime":"1564600894",
"creationTime":"1551291935",
"modifiedBy":"72057615512764423",
"id":"72057615512764419",
"domainNames":[
"crm.lanuk.ca",
"test.lanuk.ca"
],
"name":"Internal Application",
"serverGroups":[
{
"id":"72057615512764418",
"modifiedTime":"1560279822",
"creationTime":"1551291935",
"modifiedBy":"72057615512764417",
"name":"Server Group",
"enabled":true,
"learningEnabled":true,
"configSpace":"DEFAULT"
}
],
"enabled":true,
"passiveHealthEnabled":true,
"tcpPortRange":[
{
"from":"1",
"to":"65535"
}
],
"udpPortRange":[
{
"from":"1",
"to":"65535"
}
],
"doubleEncrypt":false,
"segmentGroupId":"72057615512764420",
"segmentGroupName":"Internal Application Group",
"configSpace":"DEFAULT",
"bypassType":"NEVER",
"healthCheckType":"DEFAULT",
"isCnameEnabled":"true",
"clientlessApps":[
{
"id":"72057615512764451",
"modifiedTime":"1560286271",
"creationTime":"1560279796",
"modifiedBy":"72057615512764417",
"name":"crm.lanuk.ca",
"enabled":true,
"certificateId":"72057615512764448",
"certificateName":"Wild Card Cert",
"applicationPort":"80",
"applicationProtocol":"HTTP",
"domain":"crm.lanuk.ca",
"path":"/",
"hidden":false,
"appId":"72057615512764419",
"trustUntrustedCert":false,
"allowOptions":false,
"cname":"61.72057615512764416.h.b.zpa-app.net"
}
],
"ipAnchored":false,
"bypassOnReauth":false,
"inspectTrafficWithZia":false,
"healthReporting":"ON_ACCESS",
"matchStyle":"EXCLUSIVE"
},
{
"modifiedTime":"1581028834",
"creationTime":"1574113633",
"modifiedBy":"72057615512764423",
"id":"72057615512764533",
"domainNames":[
"10.0.0.190",
"*.pb.ca"
],
"name":"PB App",
"serverGroups":[
{
"id":"72057615512764545",
"creationTime":"1579729263",
"modifiedBy":"72057615512764417",
"name":"PB App",
"enabled":true,
"learningEnabled":false,
"configSpace":"DEFAULT"
}
],
"enabled":true,
"passiveHealthEnabled":true,
"tcpPortRange":[
{
"from":"1",
"to":"65535"
}
],
"doubleEncrypt":false,
"segmentGroupId":"72057615512764420",
"segmentGroupName":"Internal Application Group",
"configSpace":"DEFAULT",
"bypassType":"NEVER",
"healthCheckType":"DEFAULT",
"isCnameEnabled":"true",
"ipAnchored":false,
"bypassOnReauth":false,
"inspectTrafficWithZia":false,
"healthReporting":"ON_ACCESS",
"matchStyle":"EXCLUSIVE"
},
{
"creationTime":"1612473591",
"modifiedBy":"72057615512764611",
"id":"72057615512764612",
"domainNames":[
"1.1.1.1"
],
"name":"Test",
"description":"string",
"enabled":false,
"passiveHealthEnabled":true,
"tcpPortRange":[
{
"from":"80",
"to":"80"
],
"doubleEncrypt":false,
"configSpace":"DEFAULT",
"bypassType":"NEVER",
"healthCheckType":"DEFAULT",
"isCnameEnabled":"true",
"ipAnchored":false,
"bypassOnReauth":false,
"inspectTrafficWithZia":false,
"healthReporting":"ON_ACCESS",
"matchStyle":"EXCLUSIVE"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/application?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/application?page=1&pagesize=2`.
- [View an example response](#Viewanexampleresponse6)
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
"selectConnectorCloseToApp": true,
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
"bypassOnReauth":false,
"inspectTrafficWithZia": false,
"healthReporting": "ON_ACCESS",
"useInDrMode": "false",
"tcpKeepAlive": "0",
"selectConnectorCloseToApp": false,
"adpEnabled": false,
"autoAppProtectEnabled": false,
"isIncompleteDRConfig": false,
"microtenantName": "Default",
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
"selectConnectorCloseToApp": true,
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
"bypassOnReauth":false,
"inspectTrafficWithZia": false,
"healthReporting": "ON_ACCESS",
"segmentGroupId": "144118148382064801",
"segmentGroupName": "Do not delete"
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Application Type Details for the Application Segment
To get application type details for the application segment:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/application/getAppsByType?applicationType=<applicationType>`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `applicationType`: The type of application. The supported values are AppProtection (`INSPECT`) or Privileged Remote Access (`SECURE_REMOTE_ACCESS`).
For example: `/mgmtconfig/v2/admin/customers/145256180497776640/application/getAppsByType?applicationType=SECURE_REMOTE_ACCESS`.
- [View an example response](#getAppTypeDetailsResponse)
[]
`{
"totalPages":"1",
"list":[
{
"id":"145256180497776887",
"name":"1.1.1.122",
"enabled":true,
"applicationPort":"22",
"applicationProtocol":"SSH",
"domain":"1.1.1.122",
"appId":"145256180497776882",
"hidden":false,
"portal":false
},
{
"id":"145256180497776669",
"name":"eng-workstation.sahuhaus.local",
"enabled":true,
"applicationPort":"3389",
"applicationProtocol":"RDP",
"domain":"eng-workstation.sahuhaus.local",
"appId":"145256180497776668",
"hidden":false,
"portal":false,
"connectionSecurity":"ANY"
},
{
"id":"145256180497776776",
"name":"testapp4.com",
"enabled":true,
"applicationPort":"22",
"applicationProtocol":"SSH",
"domain":"testapp4.com",
"appId":"145256180497776741",
"hidden":false,
"portal":false
},
{
"id":"145256180497776778",
"name":"testapp5.com",
"enabled":true,
"applicationPort":"22",
"applicationProtocol":"SSH",
"domain":"testapp5.com",
"appId":"145256180497776777",
"hidden":false,
"portal":false
},
{
"id":"145256180497776742",
"name":"testapp.com",
"enabled":true,
"applicationPort":"22",
"applicationProtocol":"SSH",
"domain":"testapp.com",
"appId":"145256180497776741",
"hidden":false,
"portal":false
},
{
"id":"145256180497776787",
"name":"test-vnc.com",
"enabled":true,
"applicationPort":"5900",
"applicationProtocol":"VNC",
"domain":"test-vnc.com",
"appId":"145256180497776786",
"hidden":false,
"portal":false
},
{
"id":"145256180497776660",
"name":"ubuntu-desktop.sahuhaus.local",
"enabled":true,
"applicationPort":"22",
"applicationProtocol":"SSH",
"domain":"ubuntu-desktop.sahuhaus.local",
"appId":"145256180497776659",
"hidden":false,
"portal":false
},
{
"id":"145256180497776971",
"name":"zscaler.com",
"enabled":true,
"applicationPort":"22",
"applicationProtocol":"SSH",
"domain":"zscaler.com",
"appId":"145256180497776970",
"hidden":false,
"portal":false
}
]
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports a search option to get application type details by MicrotenantID. To get application type details by Microtenant ID (`microtenantId`):
- Send a `GET` request to the following endpoint: `mgmtconfig/v1/admin/customers/{customerId}/application/getAppsByType?applicationType=<applicationType>?microtenantId=<microtenantId>&search=<searchString>`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `applicationType`: The type of application. The supported values are AppProtection (`INSPECT`) or Privileged Remote Access (`SECURE_REMOTE_ACCESS`).
- Valid search string values. The search string values are in the following format: `<filter>%20<operator>%20<filterValue>`. The supported `filter` value is `ownershipType`. The supported `operator` value is `EQ` (equals). The supported values for the `ownershipType` filter value are:
- `INHERITED`: The application is inherited by the Microtenant.
- `MICROTENANT_SPECIFIC`: The application is Microtenant-specific.
- `SHARED_FROM_THIS_MICROTENANT`: The application is shared from this Microtenant.
- `SHARED_TO_THIS_MICROTENANT`: The application is shared to this Microtenant.
For example: `mgmtconfig/v1/admin/customers/145256180497776640/application/getAppsByType?applicationType=SECURE_REMOTE_ACCESS?microtenantId=145260601092866314&search=ownershipType%20EQ%20MICROTENANT_SPECIFIC`.
- [View an example response](#getAppTypeMicrotenantResponse)
[]
`{
"totalPages":"1",
"totalCount":"0",
"list":[
{
"id":"145260601092866291",
"name":"example-Microtenanta-test.com",
"enabled":true,
"applicationPort":"22",
"applicationProtocol":"SSH",
"domain":"example-Microtenanta-test.com",
"microtenantId":"145260601092866116",
"microtenantName":"Microtenant A",
"appId":"145260601092866290",
"hidden":false
},
{
"id":"145260601092866295",
"name":"mithun-app-seg-test.com",
"enabled":true,
"applicationPort":"22",
"applicationProtocol":"SSH",
"domain":"example-app-seg-test.com",
"microtenantId":"145260601092866116",
"microtenantName":"Microtenant A",
"appId":"145260601092866294",
"hidden":false
}
]
}`
If you use the ZPA API Portal or the Reference Guide to make your API calls, the search field string does not require any characters. For example, the search string `ownershipType%20EQ%20MICROTENANT_SPECIFIC` is `ownershipType EQ MICROTENANT_SPECIFIC`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Updating Application Segment Details
To update an application segment:
- Use the updated JSON payload from [Creating an Application Segment](#Create) and send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/application/{applicationId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `applicationId`: The particular application segment ID you want to update.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/application/217246660302996821`.
You can provide multiple port ranges using the format in the entire JSON payload. To learn more, refer to the entire JSON payload, or see the [Adding Field Descriptions](#FieldDescriptions) section.
- [View the entire JSON payload](#Viewthejsonpayload2)
[]{
"segmentGroupId":"string",
"segmentGroupName":"string",
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
"enabled":true,
"healthCheckType":"DEFAULT",
"healthReporting":"NONE",
"id":"string",
"ipAnchored":true,
"matchStyle":"EXCLUSIVE",
"modifiedBy":"string",
"modifiedTime":0,
"name":"string",
"passiveHealthEnabled":true,
"selectConnectorCloseToApp":true,
"serverGroups":[
{
"configSpace":"DEFAULT",
"creationTime":0,
"description":"string",
"enabled":true,
"id":0,
"learningEnabled":true,
"modifiedBy":0,
"modifiedTime":0,
"name":"string"
}
],
"tcpPortRange":[
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
- [View the minimum criteria JSON payload](#Viewthebareminimumjsonpayload2)
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
}
],
"domainNames":[
"domainName or IpAddress"
],
"segmentGroupId":"<segmentGroupId>",
"selectConnectorCloseToApp":true,
"serverGroups":[
{
"id":"<serverGroupId>"
}
]
}
An error is returned if **Inspect Traffic with ZIA** is not enabled on your tenant and `InspectTrafficWithZia` is passed as `enabled` when making a `POST` or `PUT` request. The following is an example error:
`{
"params":[
"inspectTrafficWithZia",
"testApplication",
"feature.application.inspect_traffic_with_zia",
"72057594037927936"
],
"id":"config.change.not.allowed.sku.not.enabled",
"reason":"Cannot update config inspectTrafficWithZia of testApplication as this is managed by SKU feature.application.inspect_traffic_with_zia which is not enabled for customer 72057594037927936"
}`
A successful response yields code 204, meaning the application segment is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
The following limits are applicable when updating an application segment using the ZPA cloud service API:
- If an application segment is configured using Zscaler Deception, then the update and delete options are unavailable.
- The `weightedLoadBalancing` field is not supported when sending a `PUT` request to the `/mgmtconfig/v1/admin/customers/{customerId}/application/{applicationId}` endpoint to update an application segment.
- Removing all active server groups that have values for the `weight` field greater than `0` disables application load balancing and high availability. To learn more, see [Managing Application Load Balancing and High Availability Using API](/zpa/managing-application-load-balancing-and-high-availability-using-api).
AD Protection Support
To update an application segment and enable [Active Directory Inspection](/zpa/configuring-application-segments#ADProtection):
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/application/{applicationId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `applicationId`: The particular application segment ID you want to update.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/application/217246660302996821`.
You can provide multiple port ranges using the format in the entire JSON payload. To learn more, refer to the entire JSON payload, or see the [Adding Field Descriptions](#FieldDescriptions) section.
- Provide the following in the JSON payload:
- Set `adpEnabled` as true. This field is highlighted in the JSON payload.
- TCP and UDP protocols. These fields are highlighted in the JSON payload.
- [View the JSON payload](#AdProtectionPutPayload)
[]{
"enabled":true,
"healthReporting":"ON_ACCESS",
"ipAnchored":false,
"selectConnectorCloseToApp":false,
"icmpAccessType":"PING",
"isCnameEnabled":true,
"tcpKeepAlive":"0",
"id":"72057594038668832",
"domainNames":[
"exampleapp.com"
],
"tcpPortRanges":[
"443",
"443"
],
"tcpProtocols":[
"SMB"
],
"udpPortRanges":[
"334",
"334"
],
"udpProtocols":[
"LDAP"
],
"clientlessApps":null,
"inspectionApps":null,
"praApps":null,
"adpEnabled":true,
"description":"",
"name":"Example Application Segment",
"serverGroups":[
{
"id":"72057594038668831"
}
],
"selectedServerGroups":[
"72057594038668831"
],
"doubleEncrypt":false,
"segmentGroupName":"Example Segment Group",
"bypassType":"NEVER",
"configSpace":"DEFAULT",
"useInDrMode":false,
"segmentGroupId":"72057594038668830",
"commonAppsDto":{
"appsConfig":[
{
"domainJson":{
"domain":""
},
"showADInspectionToggle":true,
"viewId":"3814358737_2917168947",
"isEmptyModel":false,
"domain":"exampleapp.com",
"name":"exampleapp.com",
"protocols":[
"LDAP",
"SMB",
"KERBEROS"
],
"applicationProtocol":"NONE",
"certificateId":null,
"applicationPort":0,
"trustUntrustedCert":false,
"allowOptions":false,
"localDomain":"",
"adpEnabled":true,
"appTypes":[
"INSPECT"
],
"enabled":true
}
]
}
}
A successful response yields code 204, meaning the application segment is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
AppProtection Support
The following operations to enable or disable AppProtection on an application are supported for the same endpoint to update an application segment:
- [Enable AppProtection on an Existing Application Segment](#EnableInspection)
- [Disable AppProtection on an Existing Application Segment](#DisableInspection)
[]To enable AppProtection on an existing application segment:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/application/{applicationId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer, in the request endpoint.
- `applicationId`: The ID of the application.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/application/217246660302996821`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- The name of the application segment.
- The domains of the application.
- The TCP and UDP ports.
- Other details like the segment group and server group IDs.
- Ensure` "appTypes": ["INSPECT"]` and the other fields in `"commonAppsDto"` are included in the JSON payload. These fields are highlighted in red.
- [View the JSON payload](#jsonPayload4)
[]{
"name":"string",
"domainNames":[
"existing domain name",
"new domain name"
],
"serverGroups":[
{
"id":"<serverGroupId>"
}
],
"enabled":true,
"passiveHealthEnabled":true,
"tcpPortRange":[
"from",
"to"
],
"udpPortRanges":[
"from",
"to"
],
"doubleEncrypt":false,
"configSpace":"DEFAULT",
"bypassType":"NEVER",
"healthCheckType":"DEFAULT",
"icmpAccessType":"NONE",
"isCnameEnabled":true,
"ipAnchored":false,
"healthReporting":"ON_ACCESS",
"segmentGroupId":"<segmentGroupId>",
"commonAppsDto":{
"appsConfig":[
{
"name":"string",
"enabled":true,
"applicationProtocol":"HTTPS",
"applicationPort":"443",
"path":"/",
"domain":"string",
"trustUntrustedCert":false,
"allowOptions":false,
"certificateId":"<signingCertId>",
"appTypes":[
"INSPECT"
]
}
]
}
}
- [Sample JSON payload](#sampleJsonPayload4)
[]{
"domainNames":[
"domain.com"
],
"name":"app segment name",
"serverGroups":[
{
"id":"72057594037988996"
}
],
"enabled":true,
"passiveHealthEnabled":true,
"tcpPortRanges":[
"from":"10",
"to":"10"
],
"doubleEncrypt":false,
"configSpace":"DEFAULT",
"bypassType":"NEVER",
"healthCheckType":"DEFAULT",
"icmpAccessType":"NONE",
"isCnameEnabled":true,
"ipAnchored":false,
"healthReporting":"ON_ACCESS",
"segmentGroupId":"72057594037988995",
"commonAppsDto":{
"appsConfig":[
{
"name":"domain.com",
"enabled":true,
"applicationProtocol":"HTTPS",
"applicationPort":"10",
"path":"/",
"domain":"domain.com",
"trustUntrustedCert":false,
"allowOptions":false,
"certificateId":"72057594038037594",
"appTypes":[
"INSPECT"
]
}
]
}
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the application criteria you want to include in the JSON payload. Refer to the [Adding Field Descriptions](#FieldDescriptions) section for supported values.
[]To disable AppProtection on an existing application segment:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/application/{applicationId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer, in the request endpoint.
- `applicationId`: The ID of the application.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/application/217246660302996821`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use one of the following JSON payloads and provide the following information:
- The name of the application segment.
- The domains of the existing or new application segment.
- The TCP and UDP ports.
- Other details like the segment group and server group IDs.
- Include the `"deletedInspectApps"` field. This field is highlighted in red.
- [View the entire JSON payload](#viewJsonPayload5)
[]{
"name":"string",
"domainNames":[
"existing domain name",
"new domain name"
],
"serverGroups":[
{
"id":"<serverGroupId>"
}
],
"enabled":true,
"passiveHealthEnabled":true,
"tcpPortRanges":[
"from",
"to"
],
"udpPortRanges":[
"from",
"to"
],
"doubleEncrypt":false,
"configSpace":"DEFAULT",
"bypassType":"NEVER",
"healthCheckType":"DEFAULT",
"icmpAccessType":"NONE",
"isCnameEnabled":true,
"ipAnchored":false,
"healthReporting":"ON_ACCESS",
"segmentGroupId":"<segmentGroupId>",
"commonAppsDto":{
"deletedInspectApps":[
"<applicationId>"
]
}
}
- [Sample JSON payload](#sampleJson5)
[]{
"name":"WAAP_Public_API_Test",
"description":"WAAP Public API Test",
"enabled":true,
"healthReporting":"ON_ACCESS",
"ipAnchored":false,
"doubleEncrypt":false,
"bypassType":"NEVER",
"isCnameEnabled":true,
"tcpPortRanges":[
"20",
"28"
],
"udpPortRanges":[
"30",
"38"
],
"domainNames":[
"inspect.com"
],
"serverGroups":[
{
"id":"72057594038048851"
}
],
"segmentGroupId":"72057594037988995",
"commonAppsDto":{
"deletedInspectApps":[
72057594038079024
]
}
}
- [View the minimum criteria JSON payload](#viewJsonPayload6)
[]{
"domainNames": ["existing domain name"],
"commonAppsDto": {
"deletedInspectApps": [
<applicationId>
]
}
}
- [Sample JSON payload](#sampleJsonPayload6)
[]{
"domainNames": ["inspect3.com"],
"commonAppsDto": {
"deletedInspectApps": [
72057594038079526
]
}
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the application criteria you want to include in the JSON payload. Refer to the [Adding Field Descriptions](#FieldDescriptions) section for supported values.
[]Microtenant Support
To share an application segment to Microtenants:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/customers/{customerId}/application/{applicationId}/share`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `applicationId`: The ID of the application.
For example: `/mgmtconfig/v1/customers/72057594037927936/application/72057594038642786/share`.
- Use the following JSON payload and provide the `microtenantId`, the unique identifier of the Microtenants you want to share to, in the `shareToMicrotenants` model.
- [View the JSON payload](#MicrotenantPutPayload)
[]{
"shareToMicrotenants": [
<MicrotenantId>
<MicrotenantId>
…
]
}
- [View the sample JSON payload](#MicrotenantPutSamplePayload)
[]{
"shareToMicrotenants":[
"73201978410270795",
"73201978410270803",
"73201978410270741"
]
}
A successful response returns code 204. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Deleting an Application Segment
To delete an application segment:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/application/{applicationId}`.
- Provide the following key-value pairs in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `applicationId`: The particular application segment ID you want to delete.
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
A successful response yields code 204, meaning the application segment is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
If an application segment is configured using Zscaler Deception, then the update and delete options are unavailable.