# Configuring Segment Groups Using API
Source: https://help.zscaler.com/zpa/configuring-segment-groups-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484786.pdf

This article provides information on managing Zscaler Private Access (ZPA) [segment groups](/zpa/about-segment-groups) using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Prerequisite API Call
Before you create a new segment group, you must get the required application segment details. To learn more, see [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api).
[]Creating a New Segment Group
To add a new segment group:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/segmentGroup`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057615512764416/segmentGroup`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the entire JSON payload to create a segment group and add the applications to link:
- [View the entire JSON payload](#Viewthejsonpayload)
[]{
"name": "string",
"description": "string",
"enabled": true,
"applications": [{
"id": "<appId>"
}]
}
- [View the minimum criteria for a JSON payload](#Viewthebareminimumjsonpayload)
[]{
"name": "string",
"description": "string",
"enabled": true
}
- [View an example response](#Viewanexampleresponse2)
[]{
"id": "217246660303024818",
"creationTime": "1614290499",
"modifiedBy": "217246660303024817",
"name": "Example Test Segment Group",
"description": "App Segment Group for testing",
"enabled": true,
"applications": [
{
"id": "217246660303024812",
"bypassType": "NEVER",
"configSpace": "DEFAULT",
"isCnameEnabled": "true",
"ipAnchored": false,
"bypassOnReauth":false,
"inspectTrafficWithZia": false
}
],
"configSpace": "DEFAULT"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the segment group criteria you want to include in the JSON payload. You can also use the minimum criteria for a JSON payload to create a segment group. Refer to the [Adding Field Descriptions](#FieldDescriptions) section for supported values.
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the application segment group use cases:
[](/zpa/about-api-keys)[](/zpa/configuring-microtenants-using-api)[](/zpa/configuring-application-segments#define-generalinfo)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| name | Name of the segment group | Yes | String |
| description | Description of the segment group | No | String |
| enabled | Whether this segment group is enabled or not | Yes | Default: `False`Boolean: `True`, `False` |
| applications:id | The ID of the applications | No | Long |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. Pass `microtenantId` as null to retrieve data from all Microtenants associated with the tenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
| InspectTrafficWithZia | Indicates if **Inspect Traffic with ZIA** is enabled for the application. When enabled, this leverages a single posture for securing internet/SaaS and private applications, and applies Data Loss Prevention policies to the application segment you are creating. To learn more, see Configuring Defined Application Segments. | No | Default: `false`Boolean: `true`, `false` |
Getting Details for a Particular Segment Group
To get a segment group:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/segmentGroup/{segmentGroupId}`.
-
Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `segmentGroupId`: The particular segment group ID you want details for.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/segmentGroup/217246660303026632`.
- [View an example response](#Viewanexampleresponse3)
[]{
"id": "217246660303026632",
"creationTime": "1660797940",
"modifiedBy": "72057594038608960",
"name": "01-gdusgotra-app-seg-1",
"microtenantName": "Default",
"enabled": true,
"applications": [
{
"id": "217246660303026633",
"modifiedTime": "1661413693",
"creationTime": "1660797940",
"modifiedBy": "72057594038608960",
"name": "01-gdusgotra-app-seg-1",
"domainName": "mywebsite.com",
"domainNames": [
"mywebsite.com"
],
"enabled": true,
"passiveHealthEnabled": true,
"tcpPortRanges": [
"80",
"80",
"8080",
"8080"
],
"doubleEncrypt": false,
"healthCheckType": "DEFAULT",
"icmpAccessType": "NONE",
"bypassType": "NEVER",
"configSpace": "DEFAULT",
"cnameConfig": "NOFLATTEN",
"ipAnchored": false,
"autoAppProtectEnabled": true,
"bypassOnReauth":false,
"inspectTrafficWithZia": false,
"tcpKeepAlive": "0",
"useInDrMode": false,
"selectConnectorCloseToApp": false,
"matchStyle": "INCLUSIVE"
"tcpPortRange": [
{
"from": "80",
"to": "80"
},
{
"from": "8080",
"to": "8080"
}
]
},
{
"id": "217246660303027213",
"modifiedTime": "1682025474",
"creationTime": "1682021568",
"modifiedBy": "217246660303024753",
"name": "example22",
"domainName": "exampledomain.com",
"domainNames": [
"exampledomain.com"
],
"enabled": true,
"passiveHealthEnabled": true,
"tcpPortRanges": [
"53",
"53"
],
"udpPortRanges": [
"54",
"54"
],
"doubleEncrypt": false,
"healthCheckType": "DEFAULT",
"icmpAccessType": "NONE",
"bypassType": "NEVER",
"configSpace": "DEFAULT",
"cnameConfig": "NOFLATTEN",
"ipAnchored": false,
"inspectTrafficWithZia": false,
"tcpKeepAlive": "0",
"useInDrMode": false,
"selectConnectorCloseToApp": false,
"matchStyle" : "INCLUSIVE",
"tcpPortRange": [
{
"from": "53",
"to": "53"
}
],
"udpPortRange": [
{
"from": "54",
"to": "54"
}
]
}
],
"configSpace": "DEFAULT",
"tcpKeepAliveEnabled": "0",
"restrictedEntity": false
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details for All Segment Groups
To get details for all segment groups:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/segmentGroup`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057615512764416/segmentGroup`.
- [View an example response](#Viewanexample4)
[]{
"totalPages": "106",
"totalCount": "106",
"list": [
{
"id": "217246660303026632",
"creationTime": "1660797940",
"modifiedBy": "72057594038608960",
"name": "01-gdusgotra-app-seg-1",
"microtenantName": "Default",
"enabled": true,
"applications": [
{
"id": "217246660303026633",
"modifiedTime": "1661413693",
"creationTime": "1660797940",
"modifiedBy": "72057594038608960",
"name": "01-gdusgotra-app-seg-1",
"domainName": "mywebsite.com",
"domainNames": [
"mywebsite.com"
],
"enabled": true,
"passiveHealthEnabled": true,
"tcpPortRanges": [
"80",
"80",
"8080",
"8080"
],
"doubleEncrypt": false,
"healthCheckType": "DEFAULT",
"icmpAccessType": "NONE",
"bypassType": "NEVER",
"configSpace": "DEFAULT",
"cnameConfig": "NOFLATTEN",
"ipAnchored": false,
"autoAppProtectEnabled": true,
"bypassOnReauth":false,
"inspectTrafficWithZia": false,
"tcpKeepAlive": "0",
"useInDrMode": false,
"selectConnectorCloseToApp": false,
"matchStyle" : "INCLUSIVE",
"tcpPortRange": [
{
"from": "80",
"to": "80"
},
{
"from": "8080",
"to": "8080"
}
]
},
{
"id": "217246660303027213",
"modifiedTime": "1682025474",
"creationTime": "1682021568",
"modifiedBy": "217246660303024753",
"name": "example22",
"domainName": "exampledomain.com",
"domainNames": [
"exampledomain.com"
],
"enabled": true,
"passiveHealthEnabled": true,
"tcpPortRanges": [
"53",
"53"
],
"udpPortRanges": [
"54",
"54"
],
"doubleEncrypt": false,
"healthCheckType": "DEFAULT",
"icmpAccessType": "NONE",
"bypassType": "NEVER",
"configSpace": "DEFAULT",
"cnameConfig": "NOFLATTEN",
"ipAnchored": false,
"inspectTrafficWithZia": false,
"tcpKeepAlive": "0",
"useInDrMode": false,
"selectConnectorCloseToApp": false,
"matchStyle" : "INCLUSIVE",
"tcpPortRange": [
{
"from": "53",
"to": "53"
}
],
"udpPortRange": [
{
"from": "54",
"to": "54"
}
]
}
],
"policyMigrated": true,
"configSpace": "DEFAULT",
"tcpKeepAliveEnabled": "0",
"restrictedEntity": false
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/segmentGroup?page=1&pagesize=20` .
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/segmentGroup?page=1&pagesize=2`.
- [View an example response](#Viewanexampleresponse5)
[]{
"totalPages": "1",
"list": [
{
"id": "144118148382064801",
"modifiedTime": "1603149530",
"creationTime": "1489571820",
"modifiedBy": "144118148382064642",
"name": "Do not delete",
"description": "desc",
"enabled": true,
"applications": [
{
"id": "144118148382064803",
"modifiedTime": "1648481104",
"creationTime": "1489571905",
"modifiedBy": "144118148382065486",
"name": "CRM AWS",
"domainName": "crm.lanukcorp.com",
"domainNames": [
"crm.lanukcorp.com"
],
"description": "Test text",
"enabled": true,
"passiveHealthEnabled": true,
"tcpPortRanges": [
"80",
"80"
],
"doubleEncrypt": false,
"healthCheckType": "DEFAULT",
"icmpAccessType": "NONE",
"bypassType": "NEVER",
"configSpace": "DEFAULT",
"ipAnchored": false,
"autoAppProtectEnabled": true,
"bypassOnReauth":false,
"inspectTrafficWithZia": false,
"tcpPortRange": [
{
"from": "80",
"to": "80"
}
]
},
{
"id": "144118148382065459",
"creationTime": "1616227608",
"modifiedBy": "144118148382064667",
"name": "test",
"domainName": "api.github.com",
"domainNames": [
"api.github.com"
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
"doubleEncrypt": false,
"healthCheckType": "DEFAULT",
"icmpAccessType": "NONE",
"bypassType": "NEVER",
"configSpace": "DEFAULT",
"ipAnchored": false,
"inspectTrafficWithZia": false,
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
]
}
],
"policyMigrated": false,
"configSpace": "DEFAULT",
"tcpKeepAliveEnabled": "0"
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports a search option to search by features and fields. To search by features and fields:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/segmentGroup&search={searchString}` .
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid search string values. The search string values are in the format `fieldName operator fieldValue`. Only search string values that correspond to the values for valid fields and filters are supported. For example, the string `enabled%20EQ%20true` is supported for the **Status **filter, using the **Equals **(`EQ`) operator, for the **True **(`Enabled`) filter value.
For example: `/mgmtconfig/v1/admin/customers/73186051597795328/segmentGroup&search=enabled%20EQ%20true`.
- [View an example response](#getAllSegmentGroupsSearch)
[]{
"totalPages": "8",
"totalCount": "8",
"list": [
{
"id": "73186051597800104",
"creationTime": "1656365638",
"modifiedBy": "73186051597795329",
"name": "AD",
"enabled": true,
"applications": [
{
"id": "73186051597800105",
"modifiedTime": "1667504714",
"creationTime": "1656365638",
"modifiedBy": "73186051597795329",
"name": "Example Server App",
"domainName": "10.66.62.15",
"domainNames": [
"10.66.62.15",
"testdc.dummytest.com"
],
"enabled": true,
"passiveHealthEnabled": true,
"doubleEncrypt": false,
"healthCheckType": "NONE",
"icmpAccessType": "PING",
"bypassType": "ALWAYS",
"configSpace": "DEFAULT",
"ipAnchored": false,
"autoAppProtectEnabled": true,
"tcpKeepAlive": "1",
"useInDrMode": false,
"selectConnectorCloseToApp": false
}
],
"policyMigrated": true,
"configSpace": "DEFAULT",
"tcpKeepAliveEnabled": "0",
"microtenantName": "Default"
}
]
}
If you use the [Reference Guide](/zpa/zpa-api/api-developer-reference-guide/reference-guide) to make your API calls, the search field string does not require any characters. For example, `enabled%20EQ%20true` is `enabled EQ true`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Updating Segment Group Details
To update a segment group:
- Use the updated JSON payload from [Creating a New Segment Group](#Create) and send a `PUT` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/segmentGroup/{segmentGroupId}`.
-
Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `segmentGroupId`: The ID of the segment group captured in [Creating a New Segment Group](#Create).
For example: `/mgmtconfig/v2/admin/customers/72057615512764416/segmentGroup/72057615512764613`.
- [View the JSON payload](#Viewthejsonpayload3)
[]{
"enabled": true,
"skipDetailedAppInfo": true,
"id":"<segmentGroupId>",
"name":"string",
"scopeName": "Default",
"configSpace":"DEFAULT",
"restrictedEntity":false,
"hideInfoTooltip":true,
"description":"string",
"addedApps":["<appId>"],
"deletedApps":["<appId>"]
}
The `addedApps` and `deletedApps` models contain a list of application IDs that can be used to add or remove the applications associated with segment groups.
An unsuccessful response returns code 400.
- [View Error Code 400](#errorcode400v2)
[]{
"id": "invalid.resource.argument",
"reason": "One or more input fields applications are not valid."
}
A successful response returns code 204, meaning the segment group is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
If a segment group is configured using Zscaler Deception, then the update and delete options are unavailable.
[]Deleting a Segment Group
To delete a segment group:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/segmentGroup/{segmentGroupId}`.
-
Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `segmentGroupId`: The ID of the segment group.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/segmentGroup/72057615512764613`.
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
A successful response returns code 204, meaning the segment group is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
If a segment group is configured using Zscaler Deception, then the update and delete options are unavailable.