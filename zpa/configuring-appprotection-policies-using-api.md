# Configuring AppProtection Policies Using API
Source: https://help.zscaler.com/zpa/configuring-appprotection-policies-using-api
PDF: https://help.zscaler.com/pdf/com/en/1485461.pdf

This article provides information on managing Zscaler Private Access (ZPA) AppProtection policy use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
[]Prerequisite API Call
To get the `policySetId` by policy type:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/policyType/{policyType}`.
- Provide the `policyType`, the value for differentiating the policy types, in the request endpoint. The supported values are:
- `ACCESS_POLICY or GLOBAL_POLICY`
- `TIMEOUT_POLICY or REAUTH_POLICY`
- `BYPASS_POLICY or CLIENT_FORWARDING_POLICY`
- `INSPECTION_POLICY` (i.e., AppProtection policy)
- `ISOLATION_POLICY`
- `REDIRECTION_POLICY`
- `CAPABILITIES_POLICY`
- `CREDENTIAL_POLICY`
- `CLIENTLESS_SESSION_PROTECTION_POLICY`
- `PROTECTION_POLICY`
- `PRIVILEGED_PORTAL_POLICY`
To get an AppProtection policy set ID, provide the `INSPECTION_POLICY` policy type in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/144118148382064640/policySet/policyType/INSPECTION_POLICY`.
- [View an example response](#ViewExample)
[]{
"id":"144118148382065495",
"creationTime":"1649873731",
"modifiedBy":"144118148382065487",
"name":"Inspection_Policy",
"enabled":true,
"description":"Inspection Policies",
"policyType":"6",
"sorted":true
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
To get the paginated policy rules for the specified policy type:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/rules/policyType/{policyType}?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policyType`: The value for differentiating the policy types. The supported values are:
- `ACCESS_POLICY or GLOBAL_POLICY`
- `TIMEOUT_POLICY or REAUTH_POLICY`
- `BYPASS_POLICY or CLIENT_FORWARDING_POLICY`
- `INSPECTION_POLICY` (i.e., AppProtection policy)
- `ISOLATION_POLICY`
- `REDIRECTION_POLICY`
- `CAPABILITIES_POLICY`
- `CREDENTIAL_POLICY`
- `CLIENTLESS_SESSION_PROTECTION_POLICY`
- `PROTECTION_POLICY`
- `PRIVILEGED_PORTAL_POLICY`
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/policySet/rules/policyType/INSPECTION_POLICY?page=1&pagesize=1`.
- [View an example response](#ViewExample2)
[]{
"totalPages":"33",
"list":[
{
"id":"72057594038008613",
"modifiedTime":"1665047399",
"modifiedBy":"72057594038606777",
"name":"test policy",
"description":"test policy description",
"ruleOrder":"1",
"priority":"28",
"policyType":"6",
"operator":"AND",
"conditions":[
{
"id":"28546925",
"modifiedTime":"1665047399",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"28546926",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"objectType":"APP",
"lhs":"id",
"rhs":"72057594038050042",
"name":"aaaa1112"
},
{
"id":"28546927",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"objectType":"APP_GROUP",
"lhs":"id",
"rhs":"72057594038071913",
"name":"123"
}
]
},
{
"id":"28546928",
"modifiedTime":"1665047399",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"28546929",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"objectType":"IDP",
"lhs":"id",
"rhs":"72057594037961373",
"name":"test2"
}
]
},
{
"id":"28546930",
"modifiedTime":"1665047399",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"28546931",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"objectType":"EDGE_CONNECTOR_GROUP",
"lhs":"id",
"rhs":"72057594038073156",
"name":"Sample"
}
]
},
{
"id":"28546932",
"modifiedTime":"1665047399",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"28546933",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"objectType":"CLIENT_TYPE",
"lhs":"id",
"rhs":"zpn_client_type_machine_tunnel",
"name":"zpn_client_type_machine_tunnel"
},
{
"id":"28546934",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"objectType":"CLIENT_TYPE",
"lhs":"id",
"rhs":"zpn_client_type_exporter",
"name":"zpn_client_type_exporter"
},
{
"id":"28546935",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"objectType":"CLIENT_TYPE",
"lhs":"id",
"rhs":"zpn_client_type_ip_anchoring",
"name":"zpn_client_type_ip_anchoring"
},
{
"id":"28546936",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"objectType":"CLIENT_TYPE",
"lhs":"id",
"rhs":"zpn_client_type_edge_connector",
"name":"zpn_client_type_edge_connector"
},
{
"id":"28546937",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"objectType":"CLIENT_TYPE",
"lhs":"id",
"rhs":"zpn_client_type_zapp",
"name":"zpn_client_type_zapp"
}
]
},
{
"id":"28546938",
"modifiedTime":"1665047399",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"28546939",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"objectType":"MACHINE_GRP",
"lhs":"id",
"rhs":"72057594037987359",
"name":"123"
}
]
},
{
"id":"28546940",
"modifiedTime":"1665047399",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"28546941",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"objectType":"POSTURE",
"lhs":"test",
"rhs":"true",
"name":"test (cloud.net)"
}
]
},
{
"id":"28546942",
"modifiedTime":"1665047399",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"28546943",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"objectType":"TRUSTED_NETWORK",
"lhs":"2",
"rhs":"true",
"name":"Test 20 (cloud.net)"
}
]
},
{
"id":"28546944",
"modifiedTime":"1665047399",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"28546945",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"objectType":"PLATFORM",
"lhs":"linux",
"rhs":"true"
},
{
"id":"28546946",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"objectType":"PLATFORM",
"lhs":"android",
"rhs":"true"
},
{
"id":"28546947",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"objectType":"PLATFORM",
"lhs":"windows",
"rhs":"true"
},
{
"id":"28546948",
"creationTime":"1665047399",
"modifiedBy":"72057594038606777",
"objectType":"PLATFORM",
"lhs":"mac",
"rhs":"true"
}
]
}
],
"action":"BYPASS_INSPECT",
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
- Valid search string values. The search string values are in the format `action OPERATOR ruleAction`. The supported `ruleAction` values for AppProtection policies are `INSPECT` (Inspect) and `BYPASS_INSPECT` (Bypass Inspect). The supported value for `OPERATOR` is `EQ` (i.e., equals). Only search string values that correspond to the values for valid rule actions and operators are supported. For example, the string `action%20EQ%BYPASS_INSPECT` is supported for the **Rule Action** filter, using the **Equals** operator, for the `BYPASS_INSPECT` rule action.
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/policySet/rules/policyType/ACCESS_POLICY?page=1&pagesize=500&search=action%20EQ%20BYPSAS_INSPECT`.
If not provided, the default page size is 20. The maximum page size is 500.
- [View an example response](#ruleActionExample)
[]
`{
"totalPages":"1",
"totalCount":"0",
"list":[
{
"id":"72057594038004599",
"modifiedTime":"1675765302",
"modifiedBy":"72057594037959293",
"name":"test123",
"ruleOrder":"1",
"priority":"1",
"policyType":"6",
"operator":"AND",
"action":"BYPASS_INSPECT",
"defaultRule":false,
"restrictedEntity":false
},
{
"id":"72057594038004600",
"creationTime":"1675765292",
"modifiedBy":"72057594037959293",
"name":"test1",
"ruleOrder":"2",
"priority":"1",
"policyType":"6",
"operator":"AND",
"action":"BYPASS_INSPECT",
"defaultRule":false,
"restrictedEntity":false
}
]
}`
If you use the ZPA API Portal or the Reference Guide to make your API calls, the search field string does not require any characters. For example, `action%20EQ%20BYPASS_INSPECT` is `action EQ BYPASS_INSPECT`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Get Required Details for the AppProtection Policy
Before creating an AppProtection rule, you must get the following required details needed for the policy criteria:
- Application segment. To learn more, see [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api).
- Client types. To learn more, see [Getting Details of All Client Types](#getClientTypes).
- IdP. To learn more, see [Obtaining IdP Configuration Details Using API](/zpa/obtaining-idp-configuration-details-using-api).
- AppProtection profile. To learn more, see [Configuring AppProtection Profiles Using API](/zpa/configuring-inspection-profiles-using-api#getAll).
- Platform types. To learn more, see [Getting platform Types for a Customer](#getPlatformTypes).
- Posture profile. To learn more, see [Obtaining Posture Profile Details Using API](/zpa/posture-profile-use-cases).
- SAML attribute. To learn more, see [Obtaining SAML Attribute Details Using API](/zpa/saml-attributes-use-cases).
- Segment Group. To learn more, see [Configuring Segment Groups Using API](/zpa/configuring-segment-groups-using-api).
- Trusted Network. To learn more, see [Obtaining Trusted Network Details Using API](/zpa/trusted-network-use-cases).
[]Creating a New AppProtection Policy Rule
This API will be deprecated in a future release, and a new API to create a policy rule is provided. To learn more, see [Creating a New AppProtection Policy Rule V2](#postV2).
To create a new AppProtection policy rule for a given policy set and for a given customer:
- Send a `POST` request to the following endpoint in the policy-set controller: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in the [Prerequisite API Call](#prerequisite) section.
For example: `/mgmtconfig/v1/admin/customers/144118148382064640/policySet/144118148382065495/rule`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the JSON payload and provide the policy criteria you want for creating an AppProtection rule.
- [View the JSON payload](#viewJSON)
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
"objectType":"EDGE_CONNECTOR_GROUP",
"lhs":"id",
"rhs":"<edgeConnectorGroupId>"
}
]
},
{
"operands":[
{
"objectType":"IDP",
"lhs":"id",
"rhs":"<IDP Id>"
}
]
},
{
"operands":[
{
"objectType":"MACHINE_GRP",
"lhs":"id",
"rhs":"<machineGroupId>"
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
]
}
],
"policySetId":"<policySetId>",
"name":"<Rule name>",
"description":"<Rule description>",
"action":"INSPECT",
"zpnInspectionProfileId":"<inspectionProfileId>"
}
- [View the sample JSON payload](#sampleJSON)
- [View the minimum criteria JSON payload](#minimumCriteriaJson)
[]{
"policySetId":"<policySetId>",
"name":"<Rule name>",
"action":"INSPECT",
"zpnInspectionProfileId":"<inspectionProfileId>"
}
[]
{
"conditions":[
{
"operands":[
{
"objectType":"APP",
"lhs":"id",
"rhs":"123456xxxxxx",
"name":"Test App"
},
{
"objectType":"APP_GROUP",
"lhs":"id",
"rhs":"12465xxxxxx",
"name":"Test App Group"
}
]
},
{
"operands":[
{
"objectType":"SAML",
"lhs":"12879xxxxxx",
"rhs":"test",
"name":"Test attribute"
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"POSTURE",
"lhs":"2e789b4t-7r3d-7143-2e9y-3u6x97p0wrt",
"rhs":true,
"name":"Test Posture"
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"TRUSTED_NETWORK",
"lhs":"8dc9t02ut-4e9y-7268-9r3f-2i4y59q7uwp",
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
]
}
],
"policySetId":"72057594038007144",
"name":"Test_Inspection_Policy",
"description":"Test Inspection Policy",
"action":"INSPECT",
"zpnInspectionProfileId":"72057594038049496"
}
- [View the example response](#exampleResponse2)
[]{
"id":"217310974217027776",
"creationTime":"1662732360",
"modifiedBy":"72057594038056530",
"name":"Test_Inspection_Policy",
"description":"Test Inspection Policy",
"ruleOrder":"1",
"priority":"1",
"policyType":"6",
"operator":"AND",
"action":"INSPECT",
"zpnInspectionProfileId":"217310974217027613",
"policySetId":"217310974217027625",
"defaultRule":false
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the policy criteria you want to include in the JSON payload. You can also use the minimum criteria JSON payload to create an AppProtection policy. Refer to [Adding Field Descriptions](#fieldDescriptions) for the supported values.
[]Creating a New AppProtection Policy Rule V2
To create a new AppProtection rule for a given policy set and for a given customer:
- Send a `POST` request to the following endpoint in the policy-set controller: `/mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule`.
-
Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in the [Prerequisite API Call](#prerequisite) section.
For example: `/mgmtconfig/v2/admin/customers/144118148382064640/policySet/144118148382065495/rule`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the JSON payload and provide the policy criteria you want for creating an AppProtection policy rule.
- [View the JSON payload](#postV2payload)
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
"name": "<Example Policy Rule Name>",
"description": "<Example Policy Rule Description>",
"action": "INSPECT",
"zpnInspectionProfileId": "<AppProtectionProfileId>"
}
`
- [View the sample payload](#postV2samplePayload)
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
"123456xxxxxx",
"784945xxxxxx",
"154675xxxxxx"
]
},
{
"objectType": "APP_GROUP",
"values": [
"12465xxxxxx"
]
}
]
}
],
"name": "Example AppProtection Rule",
"description": "Example description",
"action": "INSPECT",
"zpnInspectionProfileId": "72057594038049496"
}
`
- [View the minimum criteria JSON payload](#postV2minPayload)
[]
`{
"policySetId":"<policySetId>",
"name":"<Rule name>",
"action":"INSPECT",
"zpnInspectionProfileId":"<inspectionProfileId>"
}`
- [View the example response](#postV2response)
[]
`{
"id":"217310974217027776",
"creationTime":"1662732360",
"modifiedBy":"72057594038056530",
"name":"Test_Inspection_Policy",
"description":"Test Inspection Policy",
"ruleOrder":"1",
"priority":"1",
"policyType":"6",
"operator":"AND",
"action":"INSPECT",
"zpnInspectionProfileId":"217310974217027613",
"policySetId":"217310974217027625",
"defaultRule":false
}`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the AppProtection policy use cases:
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
[](/zpa/configuring-application-segments-using-api)[](/zpa/about-api-keys)[](/zpa/configuring-microtenants-using-api)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| name | The name of the AppProtection rule | Yes | String |
| description | The description of the AppProtection rule | No | String |
| action | This is for providing the rule action | Yes | Supported values: `INSPECT` |
| conditions | This is for providing the set of conditions for the policy | No | Array of operands |
| operands | The various policy criteria | No | Array of attributes (`objectType, lhs, rhs, name`) |
| objectType | The policy criteria | No | Supported values:`APP``APP_GROUP``SAML``IDP``CLIENT_TYPE``POSTURE``TRUSTED_NETWORK``MACHINE_GRP``SCIM``SCIM_GROUP``POSTURE` and `TRUSTED_NETWORK` values are only supported for the `CLIENT_TYPE.` |
| lhs | The key for the object type | No | String ID example: `"id"` |
| rhs | The value for the given object type. Its value depends upon the key. | No | For `APP`, `APP_GROUP`, and `IDP`, the supported value is `entity id`For `CLIENT_TYPE`, the supported values are: `zpn_client_type_zapp` (for Zscaler Client Connector), `zpn_client_type_exporter` (for Clientless)For `POSTURE`, the supported values are: `true` (verified), `false` (verification failed)For `TRUSTED_NETWORK`, the supported value is `true` |
| operator | The operation type | No | Supported values: `AND`, `OR` |
| zpnInspectionProfileId | The AppProtection profile ID associated with the rule. If `adpEnabled` is set to `true` and **Active Directory Inspection** is enabled for all applications, the selected AppProtection profile ID does not apply the Active Directory protocols. To learn more, see Configuring Application Segments Using API. | Yes | String |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
For a comprehensive table of LHS and RHS values, see [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api#lhsandrhsvalues).
Getting Details for a Particular AppProtection Rule
To get details for a particular AppProtection rule:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the AppProtection policy set captured in [Prerequisite API Call](#prerequisite).
- `ruleId`: The ID of the AppProtection policy rule.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/policySet/72057615512764594/rule/217310974217027776`.
- [View an example response](#ViewanexampleresponseGet)
[]{
"id":"217310974217027776",
"creationTime":"1662732360",
"modifiedBy":"72057594038056530",
"name":"Test_Inspection_Policy",
"description":"Test policy",
"ruleOrder":"1",
"priority":"1",
"policyType":"6",
"operator":"AND",
"action":"INSPECT",
"zpnInspectionProfileId":"217310974217027613",
"zpnInspectionProfileName":"Test_Inspection_Profile",
"policySetId":"217310974217027625",
"defaultRule":false,
"restrictedEntity":false
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating an AppProtection Rule
This API will be deprecated in a future release, and a new API to update a policy rule is provided. To learn more, see [Updating an AppProtection Policy Rule V2](#putV2).
To update the details of an AppProtection rule in the policy set:
- Get the `policySetId` captured in the [Prerequisite API Call](#Prerequisite) section.
- Use the JSON payload from [Creating a New Inspection Rule](#create) and send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the inspection policy set captured in the [Prerequisite API Call](#prerequisite) section.
- `ruleId`: The ID of the inspection rule.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/policySet/72057615512764421/rule/72057615512764641`.
- [View the JSON payload](#Viewthejsonpayload2)
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
"objectType":"EDGE_CONNECTOR_GROUP",
"lhs":"id",
"rhs":"<edgeConnectorGroupId>"
}
]
},
{
"operands":[
{
"objectType":"IdP",
"lhs":"id",
"rhs":"<IDP Id>"
}
]
},
{
"operands":[
{
"objectType":"MACHINE_GRP",
"lhs":"id",
"rhs":"<machineGroupId>"
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
]
}
],
"policySetId":"<policySetId>",
"id":"<ruleId>",
"name":"<Rule name>",
"description":"<Rule description>",
"action":"INSPECT",
"zpnInspectionProfileId":"<inspectionProfileId>"
}
A successful response yields code 204, meaning the AppProtection rule is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the policy criteria you want to include in the JSON payload. You may also use the minimum criteria in the JSON payload to update an AppProtection rule. Refer to the [Adding Field Descriptions](#fieldDescriptions) section for supported values.
[]Updating an AppProtection Policy Rule V2
To update the details of an AppProtection policy rule in the policy set:
- Get the `policySetId` captured in [Prerequisite API Call](#prerequisite).
- Use the JSON payload from [Creating a New AppProtection Rule](#create) and send a `PUT` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
-
Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the inspection policy set captured in the Prerequisite API Call section.
- `ruleId`: The ID of the inspection rule.
For example: `/mgmtconfig/v2/admin/customers/72057615512764416/policySet/72057615512764421/rule/72057615512764641`.
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
"name": "<example Policy Rule Name>",
"description": "<Example Policy Rule Description>",
"action": "INSPECT",
"zpnInspectionProfileId": "<AppProtectionProfileId>"
}
`
A successful response yields code 204, meaning the AppProtection rule is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Rule Order
To update a rule order:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}/reorder/{newOrder}`.
- Provide the following parameters in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the policy set.
- `ruleId`: The ID of the AppProtection rule.
- `newOrder`: The new order of the rule.
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/policySet/72057594037938994/rule/72057615512764641/reorder/4`.
A successful response returns code 204, meaning the rule order is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
The ability to update the rule order for all rules in a policy set is also available. To learn more, see [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api#bulkUpdatingRuleOrder).
Deleting an AppProtection Rule
To delete an AppProtection rule:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the AppProtection policy set captured in the [Prerequisite API Call](#prerequisite) section.
- `ruleId`: The ID of the rule you created in [Create a New Inspection Rule](#create).
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/policySet/72057615512764421/rule/72057615512764641`.
A successful response yields code 204, meaning the AppProtection rule is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
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
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/platform` .
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