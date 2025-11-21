# Configuring Access Policies Using API
Source: https://help.zscaler.com/zpa/configuring-access-policies-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484771.pdf

This article provides information on managing Zscaler Private Access (ZPA) access policy use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
[]Prerequisite API Call
To get the `policySetId` by policy type:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/policyType/{policyType}`.
- Provide the `policyType`, the value for differentiating the policy types, in the request endpoint. The supported values are:
- `ACCESS_POLICY or GLOBAL_POLICY`
- `TIMEOUT_POLICY or REAUTH_POLICY`
- `SIEM_POLICY`
- `BYPASS_POLICY or CLIENT_FORWARDING_POLICY`
- `INSPECTION_POLICY`
- `ISOLATION_POLICY`
- `CAPABILITIES_POLICY`
- `CREDENTIAL_POLICY`
- `CLIENTLESS_SESSION_PROTECTION_POLICY`
- `PROTECTION_POLICY`
- `PRIVILEGED_PORTAL_POLICY`
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/policySet/policyType/ACCESS_POLICY`.
- [View an example response](#ViewExample)
[]{
"id":"217246660303020009",
"modifiedTime":"1627689868",
"creationTime":"1480979629",
"modifiedBy":"217246660303025242",
"name":"Global_Policy",
"enabled":true,
"description":"The rules in this policy set are executed first.",
"policyType":"1"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/rules/policyType/{policyType}?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policyType`: The value for differentiating the policy types. The supported values are:
- `ACCESS_POLICY or GLOBAL_POLICY`
- `TIMEOUT_POLICY or REAUTH_POLICY`
- `SIEM_POLICY`
- `BYPASS_POLICY or CLIENT_FORWARDING_POLICY`
- `INSPECTION_POLICY`
- `ISOLATION_POLICY`
- `CAPABILITIES_POLICY`
- `CREDENTIAL_POLICY`
- `CLIENTLESS_SESSION_PROTECTION_POLICY`
- `PROTECTION_POLICY`
- `PRIVILEGED_PORTAL_POLICY`
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/policySet/rules/policyType/ACCESS_POLICY?page=1&pagesize=2.`
- [View an example response](#paginatedResponse)
[]{
"totalPages":"16",
"list":[
{
"id":"217246660303025578",
"modifiedTime":"1643242692",
"modifiedBy":"217246660303024774",
"name":"Test all access",
"ruleOrder":"1",
"priority":"31",
"policyType":"1",
"operator":"AND",
"conditions":[
{
"id":"635818",
"modifiedTime":"1643242692",
"creationTime":"1643242692",
"modifiedBy":"217246660303024774",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"635819",
"creationTime":"1643242692",
"modifiedBy":"217246660303024774",
"objectType":"APP",
"lhs":"id",
"rhs":"217246660303025577",
"name":"TEST-MOCK"
},
{
"id":"635820",
"creationTime":"1643242692",
"modifiedBy":"217246660303024774",
"objectType":"APP",
"lhs":"id",
"rhs":"217246660303025612",
"name":"TEST-COPY"
},
{
"id":"635821",
"creationTime":"1643242692",
"modifiedBy":"217246660303024774",
"objectType":"APP",
"lhs":"id",
"rhs":"217246660303025613",
"name":"TEST-MOCK2"
},
{
"id":"635822",
"creationTime":"1643242692",
"modifiedBy":"217246660303024774",
"objectType":"APP_GROUP",
"lhs":"id",
"rhs":"217246660303025575",
"name":"TEST-MOCK"
},
{
"id":"635823",
"creationTime":"1643242692",
"modifiedBy":"217246660303024774",
"objectType":"APP_GROUP",
"lhs":"id",
"rhs":"217246660303025610",
"name":"TEST-COPY"
},
{
"id":"635824",
"creationTime":"1643242692",
"modifiedBy":"217246660303024774",
"objectType":"TEST APP_GROUP",
"lhs":"id",
"rhs":"217246660303025615",
"name":"TEST_COPY2"
}
]
}
],
"action":"ALLOW",
"customMsg":"TEST access rule",
"defaultRule":false
},
{
"id":"217246660303023504",
"modifiedTime":"1642482351",
"modifiedBy":"72057594037995189",
"name":"All_Test",
"ruleOrder":"2",
"priority":"31",
"policyType":"1",
"operator":"AND",
"action":"ALLOW",
"customMsg":"Have fun",
"defaultRule":false
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports a search option to get rules by action. To search by features and fields:
- Send a GET request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/rules/policyType/{policyType}?page=1&pagesize=20&search={searchString}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policyType`: The value for differentiating the policy types. The supported values are:
- `ACCESS_POLICY` or `GLOBAL_POLICY`
- `TIMEOUT_POLICY` or `REAUTH_POLICY`
- `BYPASS_POLICY` or `CLIENT_FORWARDING_POLICY`
- `INSPECTION_POLICY` (i.e., AppProtection policy)
- `ISOLATION_POLICY`
- `REDIRECTION_POLICY`
- `CAPABILITIES_POLICY`
- `CREDENTIAL_POLICY`
- `CLIENTLESS_SESSION_PROTECTION_POLICY`
- `PROTECTION_POLICY`
- `PRIVILEGED_PORTAL_POLICY`
- Valid page and page size values.
- Valid search string values. The search string values are in the format `action OPERATOR ruleAction`. The supported `ruleAction` values for access policies are `ALLOW` and `DENY`. The supported value for `OPERATOR` is `EQ` (i.e., equals). Only search string values that correspond to the values for valid rule actions and operators are supported. For example, the string `action%20EQ%ALLOW` is supported for the **Rule Action** filter, using the **Equals** operator, for the `ALLOW` rule action.
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/policySet/rules/policyType/ACCESS_POLICY?page=1&pagesize=500&search=action%20EQ%20ALLOW`.
If not provided, the default page size is 20. The maximum page size is 500.
- [View an example response](#ruleActionResponse)
`[ ]{
"totalPages":"1",
"totalCount":"0",
"list":[
{
"id":"72057594037928147",
"modifiedTime":"1690194270",
"modifiedBy":"72057594037941138",
"name":"yob",
"ruleOrder":"1",
"priority":"1",
"policyType":"1",
"operator":"AND",
"action":"ALLOW",
"defaultRule":false,
"restrictedEntity":false
},
{
"id":"72057594038004605",
"modifiedTime":"1675769235",
"modifiedBy":"72057594037959293",
"name":"test232",
"ruleOrder":"3",
"priority":"1",
"policyType":"1",
"operator":"AND",
"action":"ALLOW",
"defaultRule":false,
"restrictedEntity":false
},
{
"id":"72057594038007682",
"creationTime":"1676967351",
"modifiedBy":"72057594037993505",
"name":"adfasf",
"description":"asfas",
"ruleOrder":"4",
"priority":"1",
"policyType":"1",
"operator":"AND",
"action":"ALLOW",
"defaultRule":false,
"restrictedEntity":false
}
]
}`
If you use the ZPA API Portal or the Reference Guide to make your API calls, the search field string does not require any characters. For example, `action%20EQ%20ALLOW` is `action EQ ALLOW`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting the Required Policy Criteria Details
Before creating a new access policy rule, you must get the following required details for the policy criteria:
- Application Segment. To learn more, see [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api#getAppSegments).
- Client types. To learn more, see [Getting Details of All Client Types](#getClientTypes).
- Cloud Connector Group. To learn more, see [Obtaining Cloud Connector Group Details Using API](/zpa/obtaining-cloud-connector-group-details-using-api).
- IdP. To learn more, see [Obtaining IdP Configuration Details Using API](/zpa/obtaining-idp-configuration-details-using-api).
- Machine Group. To learn more, see [Obtaining Machine Group Details Using API](/zpa/obtaining-machine-group-details-using-api).
- Platform types. To learn more, see [Getting Platform Types for a Customer](#getPlatformTypes).
- Posture profile. To learn more, see [Obtaining Posture Profile Details Using API](/zpa/obtaining-posture-profile-details-using-api).
- SAML attribute. To learn more, see [Obtaining SAML Attribute Details Using API](/zpa/obtaining-saml-attribute-details-using-api).
- Segment Group. To learn more, see [Configuring Segment Groups Using API](/zpa/configuring-segment-groups-using-api#getSegmentGroups).
- SCIM attribute. To learn more, see [Obtaining SCIM Attribute Details Using API](/zpa/obtaining-scim-attribute-details-using-api).
- SCIM attribute value. To learn more, see [Obtaining SCIM Attribute Details Using API](/zpa/obtaining-scim-attribute-details-using-api#getSCIMvalue).
- SCIM Group. To learn more, see [Obtaining SCIM Group Details Using API](/zpa/obtaining-scim-group-details-using-api).
- Trusted network. To learn more, see [Obtaining Trusted Network Details Using API](/zpa/obtaining-trusted-network-details-using-api).
[]Creating a New Access Policy Rule
This API will be deprecated in a future release, and a new API to create a policy rule is provided. To learn more, see [Creating a New Access Policy Rule V2](#postV2).
To add a new access policy rule for a given policy set and for a given `customerId`:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in the [Prerequisite API Call](#Prereq) section.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/policySet/72057615512764594/rule`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the entire JSON payload and provide the policy criteria you want with the specific SAML attributes as one of the criteria.
- [View the entire JSON payload](#Viewthejsonpayload)
[]{
"conditions":[
{
"operands":[
{
"objectType":"APP",
"lhs":"id",
"rhs":"<applicationId>"
},
{
"objectType":"APP_GROUP",
"lhs":"id",
"rhs":"<segmentGroupId>"
}
]
},
{
"operands":[
{
"objectType":"SAML",
"lhs":"<samlAttrId>",
"rhs":"<samlAttrValue>"
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"SCIM",
"lhs":"<scimAttrId>",
"rhs":"<scimAttrValue>"
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"SCIM_GROUP",
"lhs":"<scimGroupAttrId>",
"rhs":"<scimGroupAttrValue>"
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"POSTURE",
"lhs":"<postureUdid>",
"rhs":true
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"TRUSTED_NETWORK",
"lhs":"<networkId>",
"rhs":true
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"CLIENT_TYPE",
"lhs":"id",
"rhs":"zpn_client_type_zapp"
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"MACHINE_GRP",
"lhs":"id",
"rhs":"<machineGroupId>"
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"CLOUD_CONNECTOR_GROUP",
"lhs":"id",
"rhs":"<CloudConnectorGroupId>"
}
]
}
],
"name":"PolicyName",
"description":"Description",
"action":"ALLOW",
"customMsg":"MsgString"
}
- [View an example response](#Viewanexampleresponse2)
[]{
"id":"72057615512764594",
"creationTime":"1612289724",
"modifiedBy":"72057615512764593",
"name":"PolicyName",
"description":"Description",
"ruleOrder":"5",
"priority":"1",
"policyType":"1",
"operator":"AND",
"action":"ALLOW",
"customMsg":"MsgString",
"auditMessage":"string"
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Choose the policy criteria you want to include in the JSON payload. Refer to the [Adding Field Descriptions](#Field) section for supported values.
[]Creating a New Access Policy Rule V2
To add a new access policy rule for a given policy set and for a given `customerId`:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in [Prerequisite API Call](#Prereq).
For example: `/mgmtconfig/v2/admin/customers/217316918451765248/policySet/217316918451765253/rule`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the entire JSON payload and provide the policy criteria you want for the criteria.
- [View the JSON payload](#postV2Payload)
[]
`{
"policySetId": "<policySetId>",
"conditions": [
{
"operands": [
{
"objectType": "APP",
"values": [
"<applicationId>",
"<applicationId>",
"<applicationId>"
]
},
{
"objectType": "APP_GROUP",
"values": [
"<segmentGroupId>"
]
}
]
}
],
"name": "<Example Policy Rule Name>",
"description": "<Example Policy Rule Description>",
"action": "ALLOW",
"appConnectorGroups": [
{
"id": "<appConnectorGroupId>",
"name": "<Example App Connector Group Name>"
},
{
"id": "<appConnectorGroupId>",
"name": "<Example App Connector Group Name 2>"
}
],
"appServerGroups": [],
"customMsg": "MsgString"
}
`
- [View an example response](#postV2response)
[]
`{
"id":"72057615512764594",
"creationTime":"1612289724",
"modifiedBy":"72057615512764593",
"name":"PolicyName",
"description":"Description",
"ruleOrder":"5",
"priority":"1",
"policyType":"1",
"operator":"AND",
"action":"ALLOW",
"customMsg":"MsgString",
"auditMessage":"string"
}`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
PRA Support
To create an access policy rule with a required approval:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in the [Prerequisite API Call](#Prereq) section.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/policySet/289370814522851333/rule?microtenantId=145260601092866314`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following:
- Ensure `action` is set to `REQUIRE_APPROVAL`
- The policy criteria you want to include.
- [View the JSON payload](#postPayloadApproval)
[]
`{
"action":"REQUIRE_APPROVAL",
"actionId":0,
"appServerGroups":[
{
"configSpace":"DEFAULT",
"creationTime":0,
"description":"string",
"enabled":true,
"id":0,
"learningEnabled":true,
"modifiedBy":0,
"modifiedTime":0,
"name":"string",
"restrictedEntity":true
}
],
"connectorGroups":[
{
"connectors":[
{
"applicationStartTime":0,
"connectorGroupId":"string",
"connectorGroupName":"string",
"controlChannelStatus":"UNKNOWN",
"creationTime":0,
"ctrlBrokerName":"string",
"currentVersion":"string",
"description":"string",
"enabled":true,
"expectedUpgradeTime":0,
"expectedVersion":"string",
"fingerprint":"string",
"id":0,
"ipAcl":[
"string"
],
"issuedCertId":0,
"lastBrokerConnectTime":0,
"lastBrokerConnectTimeDuration":"string",
"lastBrokerDisconnectTime":0,
"lastBrokerDisconnectTimeDuration":"string",
"lastUpgradeTime":0,
"latitude":0,
"location":"string",
"longitude":0,
"modifiedBy":0,
"modifiedTime":0,
"name":"string",
"nonceId":0,
"nonceName":"string",
"platform":"string",
"platformDetail":"string",
"previousVersion":"string",
"privateIp":"string",
"publicIp":"string",
"restrictedEntity":true,
"sargeVersion":"string",
"signingCert":{
"additionalProp1":"string",
"additionalProp2":"string",
"additionalProp3":"string"
},
"upgradeAttempt":0,
"upgradeStatus":"COMPLETE"
}
],
"cityCountry":"string",
"countryCode":"string",
"creationTime":0,
"description":"string",
"dnsQueryType":"IPV4_IPV6",
"enabled":true,
"geoLocationId":0,
"id":0,
"ipAcl":[
"string"
],
"latitude":"string",
"location":"string",
"longitude":"string",
"modifiedBy":0,
"modifiedTime":0,
"name":"string",
"overrideVersionProfile":true,
"restrictedEntity":true,
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
"name":"string",
"restrictedEntity":true
}
],
"lssAppConnectorGroup":true,
"tcpQuickAckApp":true,
"tcpQuickAckAssistant":true,
"tcpQuickAckReadAssistant":true,
"upgradeDay":"string",
"upgradeTimeInSecs":"string",
"versionProfileId":0,
"versionProfileName":"string",
"versionProfileVisibilityScope":"ALL"
}
],
"conditions":[
{
"creationTime":0,
"id":0,
"modifiedBy":0,
"modifiedTime":0,
"negated":true,
"operands":[
{
"creationTime":0,
"id":0,
"idpId":0,
"lhs":"string",
"modifiedBy":0,
"modifiedTime":0,
"name":"string",
"objectType":"USER",
"rhs":"string"
}
],
"operator":"AND"
}
],
"creationTime":0,
"customMsg":"string",
"defaultRule":true,
"defaultRuleName":"string",
"description":"string",
"id":0,
"modifiedBy":0,
"modifiedTime":0,
"name":"string",
"operator":"AND",
"policySetId":0,
"policyType":0,
"priority":0,
"reauthIdleTimeout":0,
"reauthTimeout":0,
"restrictedEntity":true,
"ruleOrder":0,
"zpnCbiProfileId":0,
"zpnInspectionProfileId":0,
"zpnInspectionProfileName":"string"
}`
- [View an example JSON payload](#PostExamplePayloadApproval)
[]
`{
"policySetId":"289370814522851333",
"conditions":[
],
"name":"krishna-test1",
"description":"krishna-test1",
"action":"REQUIRE_APPROVAL",
"connectorGroups":[
],
"appServerGroups":[
],
"customMsg":"krishna-test1"
}`
- [View an example response](#PostExampleResponseApproval)
[]
`{
"id":"289370814522851657",
"creationTime":"1669729158",
"modifiedBy":"72057594038624153",
"name":"krishna-test1",
"description":"krishna-test1",
"microtenantId":145260601092866314,
"ruleOrder":"12",
"priority":"1",
"policyType":"1",
"operator":"AND",
"action":"REQUIRE_APPROVAL",
"customMsg":"krishna-test1",
"policySetId":"289370814522851333",
"privilegedCapabilities":{
},
"defaultRule":false
}`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the access policy use cases:
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
[](/zpa/about-api-keys)[](/zpa/configuring-microtenants-using-api)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| name | This is the name of the access policy rule | Yes | String |
| description | This is the description of the access policy rule | No | String |
| action | This is for providing the rule action | Yes | Supported values:`ALLOW` (default value)`DENY``REQUIRE_APPROVAL` |
| customerMsg | This is for providing a customer message for the user | No | String |
| conditions | This is for providing the set of conditions for the policy | No | Array of operands |
| appConnectorGroups | The IDs and names of the App Connector groups for the application that you want the access policy to use. If no App Connector groups are specified in the payload, then all App Connector groups for the application are selected. The maximum limit of selected App Connector groups is 48. If all App Connector groups for the application are selected, then only 48 App Connector groups are used. This limit applies to newly created or edited policy rules after March 4, 2024. | No |  |
| operands | This signifies the various policy criteria | No | Array of attributes (`objectType, lhs, rhs, name`) |
| objectType | This is for specifying the policy criteria | No | Supported values:`APP``APP_GROUP``SAML``IDP``CLIENT_TYPE``POSTURE``TRUSTED_NETWORK``MACHINE_GRP``SCIM``SCIM_GROUP``POSTURE` and `TRUSTED_NETWORK` values are only supported for the `CLIENT_TYPE.` |
| lhs | This signifies the key for the object type | No | String ID example: `"id"` |
| rhs | This denotes the value for the given object type. Its value depends upon the key. | No | For `APP`, `APP_GROUP`, and `IDP`, the supported value is `entity id`.For `CLIENT_TYPE`, the supported values are `zpn_client_type_zapp` (for Zscaler Client Connector) and `zpn_client_type_exporter` (for Clientless).For `POSTURE`, the supported values are: `true` (verified), `false` (verification failed).For `TRUSTED_NETWORK`, the supported value is `true`. |
| operator | This denotes the operation type | No | Supported values: `AND`, `OR`. |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
[]LHS and RHS Values
LHS and RHS values differ based on object types. Refer to the following table:
| Object Type | LHS | RHS |
| ----------- | --- | --- |
| APP | "id" | <app segment ID> |
| APP_GROUP | "id" | <app segment group ID> |
| CLIENT_TYPE | "id" | `zpn_client_type_zappl``zpn_client_type_exporter` |
| CLOUD_CONNECTOR_GROUP | "id" | <Cloud Connector group ID> |
| IDP | "id" | <IdP ID> |
| MACHINE_GRP | "id" | <Machine group ID> |
| POSTURE | <posture network ID> | "true" / "false" |
| SAML | <SAML attribute ID> | <Attribute value to match> |
| SCIM | <SCIM attribute ID> | <Attribute value to match> |
| SCIM_GROUP | <SCIM group attribute ID> | <Attribute value to match> |
| TRUSTED_NETWORK | <trusted network ID> | "true" |
Getting a Particular Access Policy Rule Details
Before you get details for a particular access policy rule, you must get the `policySetId` captured in the [Prerequisite API Calls](#Prereq) section.
To get details for a particular access policy rule:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the Global policy set captured in the [Prerequisite API Call](#Prereq) section.
- `ruleId`: The ID of the rule you created in [Creating a New Access Policy Rule](#Create) section.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/policySet/72057615512764594/rule/72057615512764594`.
- [View an example response](#Viewanexampleresponse3)
[]{
"id":"72057615512764607",
"creationTime":"1612396045",
"modifiedBy":"72057615512764606",
"name":"PolicyName",
"description":"Description",
"ruleOrder":"6",
"priority":"1",
"policyType":"1",
"operator":"AND",
"action":"ALLOW",
"customMsg":"MsgString",
"auditMessage":"{\"policyType\":\"Access Policy\",\"name\":\"PolicyName\",\"description\":\"Description\",\"action\":\"ALLOW\",\"ruleOrder\":\"6\",\"messageToUser\":\"MsgString\"}",
"policySetId":"72057615512764421"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating an Access Policy Rule
This API will be deprecated in a future release, and a new API to update a policy rule is provided. To learn more, see [Updating a New Access Policy Rule V2](#putV2).
To update the details of an access policy rule in the policy set:
- Get the `policySetId` provided in the [Prerequisite API Calls](#Prereq) section.
- Use the entire JSON payload from [Creating a New Access Policy Rule](#Create) and send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in the [Prerequisite API Call](#Prereq) section.
- `ruleId`: The ID of the rule you created in [Creating a New Access Policy Rule](#Create) section.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/policySet/72057615512764421/rule/72057615512764594`.
- [View the entire JSON payload](#Viewthejsonpayload2)
[]{
"conditions":[
{
"operands":[
{
"objectType":"APP",
"lhs":"id",
"rhs":"<applicationId>"
},
{
"objectType":"APP_GROUP",
"lhs":"id",
"rhs":"<segmentGroupId>"
}
]
},
{
"operands":[
{
"objectType":"SAML",
"lhs":"<samlAttrId>",
"rhs":"<samlAttrValue>"
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"SCIM",
"lhs":"<scimAttrId>",
"rhs":"<scimAttrValue>"
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"SCIM_GROUP",
"lhs":"<scimGroupAttrId>",
"rhs":"<scimGroupAttrValue>"
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"POSTURE",
"lhs":"<postureUdid>",
"rhs":true
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"TRUSTED_NETWORK",
"lhs":"<networkId>",
"rhs":true
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"CLIENT_TYPE",
"lhs":"id",
"rhs":"zpn_client_type_zapp"
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"MACHINE_GRP",
"lhs":"id",
"rhs":"<machineGroupId>"
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"CLOUD_CONNECTOR_GROUP",
"lhs":"id",
"rhs":"<CloudConnectorGroupId>"
}
]
}
],
"name":"PolicyName",
"description":"Description",
"action":"ALLOW",
"customMsg":"MsgString"
}
Choose the policy criteria you want to include in the JSON payload. Refer to [Adding Field Descriptions](#Field) section for supported values
A successful response returns code 204, meaning the access policy rule is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
If an access policy is configured using Zscaler Deception, then the update and delete options are unavailable.
[]Updating an Access Policy Rule V2
To update the details of an access policy rule in the policy set:
- Get the `policySetId` provided in [Prerequisite API Call](#Prereq).
- Use the entire JSON payload from [Creating a New Access Rule V2](#postV2payload) and send a `PUT` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
-
Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in [Prerequisite API Call](#Prereq).
- `ruleId`: The ID of the rule you created in [Creating a New Access Rule V2](#postV2).
For example: `/mgmtconfig/v2/admin/customers/217316918451765248/policySet/217316918451765253/rule/217316918451766917`.
- [View the JSON payload](#putV2payload)
[]
`{
"policySetId": "<policySetId>",
"id": "<ruleId>",
"conditions": [
{
"operands": [
{
"objectType": "APP",
"values": [
"<applicationId>",
"<applicationId>",
"<applicationId>"
]
},
{
"objectType": "APP_GROUP",
"values": [
"<segmentGroupId>"
]
}
]
}
],
"name": "<Example Policy Rule Name",
"description": "<Example Policy Rule Description>",
"action": "ALLOW",
"appConnectorGroups": [
{
"id": "<appConnectorGroupId>",
"name": "<Example App Connector Group Name>"
},
{
"id": "<appConnectorGroupId>",
"name": "<exampleName2>"
],
"appServerGroups": [],
"customMsg": "<Example Custom Message>"
}
`
A successful response returns code 204, meaning the access policy rule is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
PRA Support
To update an access policy rule with a required approval:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in the [Prerequisite API Call](#Prereq) section.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/policySet/289370814522851333/rule?microtenantId=145260601092866314`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following:
- Ensure `action` is set to `REQUIRE_APPROVAL`
- The policy criteria you want to include.
- [View the JSON payload](#putPayloadApproval)
[]
`{
"action":"REQUIRE_APPROVAL",
"actionId":0,
"appServerGroups":[
{
"configSpace":"DEFAULT",
"creationTime":0,
"description":"string",
"enabled":true,
"id":0,
"learningEnabled":true,
"modifiedBy":0,
"modifiedTime":0,
"name":"string",
"restrictedEntity":true
}
],
"connectorGroups":[
{
"connectors":[
{
"applicationStartTime":0,
"connectorGroupId":"string",
"connectorGroupName":"string",
"controlChannelStatus":"UNKNOWN",
"creationTime":0,
"ctrlBrokerName":"string",
"currentVersion":"string",
"description":"string",
"enabled":true,
"expectedUpgradeTime":0,
"expectedVersion":"string",
"fingerprint":"string",
"id":0,
"ipAcl":[
"string"
],
"issuedCertId":0,
"lastBrokerConnectTime":0,
"lastBrokerConnectTimeDuration":"string",
"lastBrokerDisconnectTime":0,
"lastBrokerDisconnectTimeDuration":"string",
"lastUpgradeTime":0,
"latitude":0,
"location":"string",
"longitude":0,
"modifiedBy":0,
"modifiedTime":0,
"name":"string",
"nonceId":0,
"nonceName":"string",
"platform":"string",
"platformDetail":"string",
"previousVersion":"string",
"privateIp":"string",
"publicIp":"string",
"restrictedEntity":true,
"sargeVersion":"string",
"signingCert":{
"additionalProp1":"string",
"additionalProp2":"string",
"additionalProp3":"string"
},
"upgradeAttempt":0,
"upgradeStatus":"COMPLETE"
}
],
"cityCountry":"string",
"countryCode":"string",
"creationTime":0,
"description":"string",
"dnsQueryType":"IPV4_IPV6",
"enabled":true,
"geoLocationId":0,
"id":0,
"ipAcl":[
"string"
],
"latitude":"string",
"location":"string",
"longitude":"string",
"modifiedBy":0,
"modifiedTime":0,
"name":"string",
"overrideVersionProfile":true,
"restrictedEntity":true,
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
"name":"string",
"restrictedEntity":true
}
],
"lssAppConnectorGroup":true,
"tcpQuickAckApp":true,
"tcpQuickAckAssistant":true,
"tcpQuickAckReadAssistant":true,
"upgradeDay":"string",
"upgradeTimeInSecs":"string",
"versionProfileId":0,
"versionProfileName":"string",
"versionProfileVisibilityScope":"ALL"
}
],
"conditions":[
{
"creationTime":0,
"id":0,
"modifiedBy":0,
"modifiedTime":0,
"negated":true,
"operands":[
{
"creationTime":0,
"id":0,
"idpId":0,
"lhs":"string",
"modifiedBy":0,
"modifiedTime":0,
"name":"string",
"objectType":"USER",
"rhs":"string"
}
],
"operator":"AND"
}
],
"creationTime":0,
"customMsg":"string",
"defaultRule":true,
"defaultRuleName":"string",
"description":"string",
"id":0,
"modifiedBy":0,
"modifiedTime":0,
"name":"string",
"operator":"AND",
"policySetId":0,
"policyType":0,
"priority":0,
"reauthIdleTimeout":0,
"reauthTimeout":0,
"restrictedEntity":true,
"ruleOrder":0,
"zpnCbiProfileId":0,
"zpnInspectionProfileId":0,
"zpnInspectionProfileName":"string"
}    `
- [View an example JSON payload](#PutExamplePayloadApproval)
[]
`{
"policySetId":"289370814522851333",
"conditions":[
],
"name":"krishna-test1",
"description":"krishna-test1",
"action":"REQUIRE_APPROVAL",
"connectorGroups":[
],
"appServerGroups":[
],
"customMsg":"krishna-test1"
}`
A successful response returns code 204, meaning the access rule is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Rule Order
To update a rule order:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}/reorder/{newOrder}`.
- Provide the following parameters in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the policy set.
- `ruleId`: The ID of the rule.
- `newOrder`: The new order of the rule.
For example: `mgmtconfig/v1/admin/customers/72057594037927936/policySet/72057594037938994/rule/72057615512764641/reorder/4`.
A successful response returns code 204, meaning the rule order is updated. To learn more, see [About Error Codes](/zpa/about-error-codes).
Updating the rule order of an access policy configured using Zscaler Deception is not supported. When changing the rule order of a regular access policy and there is an access policy configured using Deception, the rule order of the regular access policy must be greater than the rule order for an access policy configured using Deception.
[]Bulk Updating the Rule Order of All Rules in a Policy Set
To bulk update the rule order of all rules in a policy set:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/customers/{customerId}/policySet/{policySet}/reorder`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The unique identifier of the policy set.
For example: `/mgmtconfig/v1/customers/217246660302995456/policySet/217246660303020009/reorder`.
- Use the following JSON payload and provide the new order of rule IDs for the rules in the policy set as an array of integers:
- [View the JSON payload](#bulkUpdatePayload)
[]
`[
<ruleId1>,
<ruleId2>,
<ruleId3>
]`
- [View the sample JSON payload](#putBulkSamplePayload)
[]
`[
217316918451765311,
217316918451765312,
217316918451765310,
217316918451765255
]                    `
A successful response returns code 204, meaning the rules within the policy set are reordered.
Zscaler recommends you are aware of the following when bulk updating the rule order of all rules within a policy set:
- A default rule exists for timeout policies, client forwarding policies, and isolation policies. This default rule cannot be reordered. For PUT requests to bulk update the rule order of timeout policies, client forwarding policies, and isolation policies, the rule ID of the last rule must be placed in the last index of input for the array of rule IDs. If the order of the default rule is changed from the last index, then the exception `default.rule.reorder.notallowed - Reordering not allowed for default rule <ruleId>` is returned.
- All rule IDs for the rules within the policy set must be included in the payload when making the request, otherwise error code 400 is returned with `“reason” : “resource input length is not valid”`.
- If a rule ID from the policy set is missing from the array of rule IDs in the payload, the error `missing.rule - Missing ruleIds: <ruleId1, ruleId2> from policySet <policySetId>` is returned.
- If any invalid rule IDs are passed in the payload when making the request, error code 400 is returned with `“reason”: “The ruleId: <ruleId> does not belong to the policySetId: <policySetId>”`.
- If a rule in the policy set is a restricted entity (e.g., a rule configured using Deception) and its order is changed in the index of input for the array of rule IDs, then the error `"reason": "Rule id <ruleId> is a restricted entity and cannot be reordered"` is returned.
Deleting an Access Policy Rule
To delete an access policy rule:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
- Provide the following key-value pairs in the request body:
- `customerId:` The ZPA tenant ID of the customer.
- `policySetId`: The ID of the Global policySet captured in the [Prerequisite API Call](#Prereq) section.
- `ruleId`: The ID of the rule you created in [Creating a New Access Rule](#Create) section.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/policySet/72057615512764421/rule/72057615512764594`.
A successful response returns code 204, meaning the access policy rule is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
If an access policy is configured using Deception, then the update and delete options are unavailable.
[]Getting Details of All Client Types
To get details of all client types:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/clientTypes`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/clientTypes`.
- [View an example response](#exampleResponseClientTypes)
[]{
"zpn_client_type_exporter": "Web Browser",
"zpn_client_type_exporter_noauth": "Web Browser Unauthenticated",
"zpn_client_type_machine_tunnel": "Machine Tunnel",
"zpn_client_type_edge_connector": "Cloud Connector",
"zpn_client_type_zia_inspection": "ZIA Inspection",
"zpn_client_type_zapp": "Client Connector",
"zpn_client_type_slogger": "ZPA LSS",
"zpn_client_type_browser_isolation": "Cloud Browser",
"zpn_client_type_ip_anchoring": "ZIA Service Edge",
"zpn_client_type_zapp_partner": "Client Connector Partner",
"zpn_client_type_branch_connector": "Branch Connector",
"zpn_client_type_vdi":"Client Connector for VDI"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Platform Types for a Customer
To get the platform types for a customer:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/platform`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/platform`.
- [View an example response](#examplePlatformType)
[]{
"linux":"Linux",
"android":"Android",
"windows":"Windows",
"ios":"iOS",
"mac":"Mac"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).