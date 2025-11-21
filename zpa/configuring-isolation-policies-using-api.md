# Configuring Isolation Policies Using API
Source: https://help.zscaler.com/zpa/configuring-isolation-policies-using-api
PDF: https://help.zscaler.com/pdf/com/en/1485726.pdf

This article provides information on managing Zscaler Private Access (ZPA) isolation policy use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
[]Prerequisite API Call
To get the `policySetId` by policy type:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/policyType/{policyType}`.
- Provide the following in the request endpoint.
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
To get an isolation policy set ID, provide the `ISOLATION_POLICY` policy type in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/73186051597795328/policySet/policyType/ISOLATION_POLICY`.
- [View an example response](#ViewExample)
[]
{
"id":"73186051597800308",
"modifiedTime":"1667500637",
"creationTime":"1663835487",
"modifiedBy":"73186051597795329",
"name":"Test_Isolation_Policy",
"enabled":true,
"description":"Isolation policies.",
"policyType":"5",
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
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/policySet/rules/policyType/ISOLATION_POLICY?page=1&pagesize=2`.
- [View an example response](#ViewExample2)
[]{
"totalPages":"1",
"list":[
{
"id":"73186051597800314",
"modifiedTime":"1664711572",
"modifiedBy":"73186051597795329",
"name":"Allow all Isolation Policy",
"ruleOrder":"1",
"priority":"2",
"policyType":"5",
"operator":"AND",
"conditions":[
{
"id":"28539832",
"modifiedTime":"1664711572",
"creationTime":"1664711572",
"modifiedBy":"73186051597795329",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"28539833",
"creationTime":"1664711572",
"modifiedBy":"73186051597795329",
"objectType":"APP",
"lhs":"id",
"rhs":"73186051597798372",
"name":"a continuous default"
},
{
"id":"28539834",
"creationTime":"1664711572",
"modifiedBy":"73186051597795329",
"objectType":"APP",
"lhs":"id",
"rhs":"73186051597798373",
"name":"a continuous none"
}
]
},
{
"id":"28539835",
"modifiedTime":"1664711572",
"creationTime":"1664711572",
"modifiedBy":"73186051597795329",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"28539836",
"creationTime":"1664711572",
"modifiedBy":"73186051597795329",
"objectType":"CLIENT_TYPE",
"lhs":"id",
"rhs":"zpn_client_type_exporter",
"name":"zpn_client_type_exporter"
}
]
}
],
"action":"BYPASS_ISOLATE",
"defaultRuleName":"Default_Rule",
"defaultRule":false
},
{
"id":"73186051597800309",
"modifiedTime":"1667215866",
"creationTime":"1663835487",
"modifiedBy":"72057594037987389",
"name":"Default_Rule",
"description":"This is the default Isolation Policy rule",
"ruleOrder":"2",
"priority":"1",
"policyType":"5",
"operator":"AND",
"conditions":[
{
"id":"28528430",
"modifiedTime":"1663835487",
"creationTime":"1663835487",
"modifiedBy":"72057594037940740",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"28528431",
"creationTime":"1663835487",
"modifiedBy":"72057594037940740",
"objectType":"CLIENT_TYPE",
"lhs":"id",
"rhs":"zpn_client_type_exporter",
"name":"zpn_client_type_exporter"
}
]
}
],
"action":"BYPASS_ISOLATE",
"defaultRuleName":"Default_Rule",
"defaultRule":true
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports a search option to get rules by action. To search by features and fields:
- Send a GET request to the following endpoint: /mgmtconfig/v1/admin/customers/{customerId}/policySet/rules/policyType/{policyType}?page=1&pagesize=20&search={searchString}.
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
- Valid search string values. The search string values are in the format `action OPERATOR ruleAction`. The supported `ruleAction` values for isolation policies are `ISOLATE` (Allow Isolation) and `BYPASS_ISOLATE` (Bypass Isolation). The supported value for `OPERATOR` is `EQ` (i.e., equals). Only search string values that correspond to the values for valid rule actions and operators are supported. For example, the string `action%20EQ%ISOLATE` is supported for the **Rule Action** filter, using the **Equals** operator, for the `ISOLATE` rule action.
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/policySet/rules/policyType/ISOLATION_POLICY?page=1&pagesize=500&search=action%20EQ%20ISOLATE`.
If not provided, the default page size is 20. The maximum page size is 500.
- [View an example response](#ruleActionResponse)
[]
`{
"totalPages": "1",
"totalCount": "0",
"list": [
{
"id": "72062453793466810",
"modifiedTime": "1696537736",
"creationTime": "1696537736",
"modifiedBy": "72062453793423372",
"name": "efaa1916e5d84f7e",
"description": "86353a14b3b04518",
"ruleOrder": "1",
"priority": "2",
"policyType": "5",
"operator": "AND",
"conditions": [
{
"id": "31012922",
"modifiedTime": "1696537736",
"creationTime": "1696537736",
"modifiedBy": "72062453793423372",
"operator": "OR",
"negated": false,
"operands": [
{
"id": "31012923",
"modifiedTime": "1696537736",
"creationTime": "1696537736",
"modifiedBy": "72062453793423372",
"objectType": "APP",
"lhs": "id",
"rhs": "72062453793466803",
"name": "37f1439584024113"
},
{
"id": "31012924",
"modifiedTime": "1696537736",
"creationTime": "1696537736",
"modifiedBy": "72062453793423372",
"objectType": "APP_GROUP",
"lhs": "id",
"rhs": "72062453793466801",
"name": "7082377277964324"
},
{
"id": "31012925",
"modifiedTime": "1696537736",
"creationTime": "1696537736",
"modifiedBy": "72062453793423372",
"objectType": "CLIENT_TYPE",
"lhs": "id",
"rhs": "zpn_client_type_exporter",
"name": "zpn_client_type_exporter"
}
]
}
],
"action": "ISOLATE",
"zpnCbiProfileId": "72062453793466808",
"defaultRule": false,
"defaultRuleName": "Default_Rule",
"restrictedEntity": false
},
{
"id": "72062453793466811",
"modifiedTime": "1696537736",
"creationTime": "1696537736",
"modifiedBy": "72062453793423372",
"name": "e3822a6900464099",
"description": "e7706afef9464377",
"ruleOrder": "2",
"priority": "2",
"policyType": "5",
"operator": "AND",
"conditions": [
{
"id": "31012926",
"modifiedTime": "1696537736",
"creationTime": "1696537736",
"modifiedBy": "72062453793423372",
"operator": "OR",
"negated": false,
"operands": [
{
"id": "31012927",
"modifiedTime": "1696537736",
"creationTime": "1696537736",
"modifiedBy": "72062453793423372",
"objectType": "APP",
"lhs": "id",
"rhs": "72062453793466804",
"name": "cdbefe37b1dc4587"
},
{
"id": "31012928",
"modifiedTime": "1696537736",
"creationTime": "1696537736",
"modifiedBy": "72062453793423372",
"objectType": "APP_GROUP",
"lhs": "id",
"rhs": "72062453793466802",
"name": "5df6681c7e574186"
},
{
"id": "31012929",
"modifiedTime": "1696537736",
"creationTime": "1696537736",
"modifiedBy": "72062453793423372",
"objectType": "CLIENT_TYPE",
"lhs": "id",
"rhs": "zpn_client_type_exporter",
"name": "zpn_client_type_exporter"
}
]
}
],
"action": "ISOLATE",
"zpnCbiProfileId": "72062453793466808",
"defaultRule": false,
"defaultRuleName": "Default_Rule",
"restrictedEntity": false
}
]
}
`
If you use the ZPA API Portal or the Reference Guide to make your API calls, the search field string does not require any characters. For example, `action%20EQ%20ISOLATE` is `action EQ ISOLATE`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Required Details for the Isolation Policy
Before creating an isolation rule, you must get the following required details needed for the policy criteria:
- Application segment. To learn more, see [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api).
- Client types. To learn more, see [Getting Details of All Client Types](#getClientTypes).
- IdP. To learn more, see [Obtaining IdP Configuration Details Using API](/zpa/obtaining-idp-configuration-details-using-api).
- Platform types. To learn more, see [Getting platform Types for a Customer](#getPlatformTypes).
- Segment Group. To learn more, see [Configuring Segment Groups Using API](/zpa/configuring-segment-groups-using-api).
[]Creating a New Isolation Policy Rule
This API will be deprecated in a future release, and a new API to create a policy rule is provided. To learn more, see [Creating a New Isolation Policy Rule V2](#postV2).
To create a new isolation policy rule for a given policy set and for a given customer:
- Send a `POST` request to the following endpoint in the policy-set controller: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in the [Prerequisite API Call](#prerequisite) section.
For example: `/mgmtconfig/v1/admin/customers/73186051597795328/policySet/73186051597800308/rule`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the policy criteria you want for creating an isolation rule. You must include the following details in the JSON payload:
- `name`: The name of the isolation policy.
- `action`: The rule action (i.e., `ISOLATE` or `BYPASS_ISOLATE`).
- `zpnIsolationProfileId`: The isolation profile ID associated with the rule and captured in the [prerequisite API call](#prerequisite).
- `objectType`: The policy criteria. You must include `CLIENT_TYPE` as the `objectType`. To learn more, see [Adding Field Descriptions](#fieldDescriptions).
- `Lhs` and `rhs` values for the supported `objectType`. To learn more, see [Adding Field Descriptions](#fieldDescriptions).
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
"action":"ISOLATE",
"zpnIsolationProfileId":"<isolationProfileId>"
}
- [View the sample JSON payload](#sampleJSON)
- [View the minimum criteria JSON payload](#minimumCriteriaJson)
[]
{
"conditions":[
{
"operands":[
{
"objectType":"CLIENT_TYPE",
"lhs":"id",
"rhs":"zpn_client_type_exporter"
}
]
}
],
"policySetId":"73186051597800308",
"name":"Test Isolation Policy Rule",
"action":"ISOLATE",
"zpnIsolationProfileId":"73186051597800310"
}
[]{
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
"rhs":"zpn_client_type_exporter"
}
]
}
],
"policySetId":"73186051597800308",
"name":"Test Isolation Policy",
"description":"Test Isolation Policy",
"action":"ISOLATE",
"zpnIsolationProfileId":"72057594038049496"
}
- [View the example response](#exampleResponse2)
[]{
"id":"73186051597800494",
"modifiedTime":"1669052235",
"creationTime":"1669052235",
"modifiedBy":"72057594038052595",
"name":"Test Isolation Policy Rule",
"ruleOrder":"2",
"priority":"2",
"policyType":"5",
"operator":"AND",
"conditions":[
{
"id":"28616318",
"modifiedTime":"1669052235",
"creationTime":"1669052235",
"modifiedBy":"72057594038052595",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"28616319",
"creationTime":"1669052235",
"modifiedBy":"72057594038052595",
"objectType":"CLIENT_TYPE",
"lhs":"id",
"rhs":"zpn_client_type_exporter"
}
]
}
],
"action":"ISOLATE",
"policySetId":"73186051597800308",
"defaultRuleName":"Default_Rule",
"defaultRule":false,
"zpnIsolationProfileId":"73186051597800310"
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the policy criteria you want to include in the JSON payload. You can also use the minimum criteria JSON payload to create an isolation policy. Refer to [Adding Field Descriptions](#fieldDescriptions) for the supported values.
[]Creating a New Isolation Policy Rule V2
To create a new isolation rule for a given policy set and for a given customer:
- Send a `POST` request to the following endpoint in the policy-set controller: `/mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule`.
-
Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in the [prerequisite API call](#prerequisite).
For example: `/mgmtconfig/v2/admin/customers/73186051597795328/policySet/73186051597800308/rule`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the policy criteria you want for creating an isolation policy rule. You must include the following details in the JSON payload:
- `name`: The name of the isolation policy.
- `action`: The rule action (i.e., `ISOLATE` or `BYPASS_ISOLATE`).
- `zpnIsolationProfileId`: The isolation profile ID associated with the rule and captured in the [prerequisite API call](#prerequisite).
- `objectType`: The policy criteria. You must include `CLIENT_TYPE` as the `objectType`. To learn more, see Adding Field Descriptions.
- `Lhs` and `rhs` values for the supported `objectType`. To learn more, see [Adding Field Descriptions](#fieldDescriptions).
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
"policySetId":"<policySetId>",
"name":"<Rule name>",
"description":"<Rule description>",
"action":"ISOLATE",
"zpnIsolationProfileId":"<isolationProfileId>"
}
`
- [View an example response](#postV2response)
[]
`{
"id":"73186051597800494",
"modifiedTime":"1669052235",
"creationTime":"1669052235",
"modifiedBy":"72057594038052595",
"name":"Test Isolation Policy Rule",
"ruleOrder":"2",
"priority":"2",
"policyType":"5",
"operator":"AND",
"conditions":[
{
"id":"28616318",
"modifiedTime":"1669052235",
"creationTime":"1669052235",
"modifiedBy":"72057594038052595",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"28616319",
"creationTime":"1669052235",
"modifiedBy":"72057594038052595",
"objectType":"CLIENT_TYPE",
"lhs":"id",
"rhs":"zpn_client_type_exporter"
}
]
}
],
"action":"ISOLATE",
"policySetId":"73186051597800308",
"defaultRuleName":"Default_Rule",
"defaultRule":false,
"zpnIsolationProfileId":"73186051597800310"
}`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the isolation policy use cases:
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
| name | The name of the isolation rule | Yes | String |
| description | The description of the isolation rule | No | String |
| action | This is for providing the rule action | Yes | Supported values: `ISOLATE`, `BYPASS_ISOLATE` |
| conditions | This is for providing the set of conditions for the policy | No | Array of operands |
| operands | The various policy criteria | No | Array of attributes (e.g., `objectType`, `lhs`, `rhs`, `name`) |
| objectType | The policy criteria | No | Supported values:`APP``APP_GROUP``SAML``IDP``CLIENT_TYPE``POSTURE``TRUSTED_NETWORK``MACHINE_GRP``SCIM``SCIM_GROUP``POSTURE` and `TRUSTED_NETWORK` values are only supported for the `CLIENT_TYPE.` |
| lhs | The key for the object type | No | String ID example: `"id"` |
| rhs | The value for the given object type. Its value depends upon the key. | No | For `APP`, `APP_GROUP`, and `IDP`, the supported value is `entity id`For `CLIENT_TYPE`, the supported values are: `zpn_client_type_zapp` (for Zscaler Client Connector), `zpn_client_type_exporter` (for Clientless)For `POSTURE`, the supported values are: `true` (verified), `false` (verification failed)For `TRUSTED_NETWORK`, the supported value is `true` |
| operator | The operation type | No | Supported values: `AND`, `OR` |
| zpnIsolationProfileId | The isolation profile ID associated with the rule | Yes | String |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
For a comprehensive table of LHS and RHS values, see [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api#lhsandrhsvalues).
Getting Details for a Particular Isolation Rule
To get details for a particular isolation rule:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the isolation policy set captured in the [Prerequisite API Call](#prerequisite) section.
- `ruleId`: The ID of the rule you created in [Creating a New Isolation Rule](#create).
For example: `/mgmtconfig/v1/admin/customers/73186051597795328/policySet/73186051597800308/rule/73186051597800314`.
- [View an example response](#ViewanexampleresponseGet)
[]
{
"id":"73186051597800314",
"modifiedTime":"1664711572",
"modifiedBy":"73186051597795329",
"name":"Allow all Isolation Policy",
"ruleOrder":"1",
"priority":"2",
"policyType":"5",
"operator":"AND",
"conditions":[
{
"id":"28539832",
"modifiedTime":"1664711572",
"creationTime":"1664711572",
"modifiedBy":"73186051597795329",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"28539833",
"creationTime":"1664711572",
"modifiedBy":"73186051597795329",
"objectType":"APP",
"lhs":"id",
"rhs":"73186051597798372",
"name":"a continuous default"
},
{
"id":"28539834",
"creationTime":"1664711572",
"modifiedBy":"73186051597795329",
"objectType":"APP",
"lhs":"id",
"rhs":"73186051597798373",
"name":"a continuous none"
}
]
},
{
"id":"28539835",
"modifiedTime":"1664711572",
"creationTime":"1664711572",
"modifiedBy":"73186051597795329",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"28539836",
"creationTime":"1664711572",
"modifiedBy":"73186051597795329",
"objectType":"CLIENT_TYPE",
"lhs":"id",
"rhs":"zpn_client_type_exporter"
}
]
}
],
"action":"BYPASS_ISOLATE",
"policySetId":"73186051597800308",
"defaultRuleName":"Default_Rule",
"defaultRule":false
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating an Isolation Policy Rule
This API will be deprecated in a future release, and a new API to update an policy rule is provided. To learn more, see [Updating an Isolation Policy Rule V2](#putV2).
To update the details of an isolation policy rule in the policy set:
- Get the `policySetId` provided in the [prerequisite API call](#prerequisite).
- Use the JSON payload from [Creating a New Isolation Policy Rule](#create) and send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the isolation policy set captured in the [prerequisite API call](#prerequisite).
- `ruleId`: The ID of the particular isolation policy rule you want to update.
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
"rhs":"zpn_client_type_exporter"
}
]
}
],
"policySetId":"<policySetId>",
"name":"<Rule name>",
"description":"<Rule description>",
"action":"ISOLATE",
"zpnIsolationProfileId":"<isolationProfileId>"
}
A successful response yields code 204, meaning the isolation rule is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the policy criteria you want to include in the JSON payload. You may also use the minimum criteria in the JSON payload to update an isolation policy. Refer to the [Adding Field Descriptions](#fieldDescriptions) section for supported values.
[]Updating an Isolation Policy Rule V2
To update the details of an isolation policy rule in the policy set:
- Get the `policySetId` provided in the [prerequisite API call](#prerequisite).
- Use the JSON payload from [Creating a New Isolation Policy Rule](#postV2) and send a `PUT` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
-
Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the isolation policy set captured in the [prerequisite API call](#prerequisite).
- `ruleId`: The ID of the particular isolation policy rule you want to update.
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
"policySetId":"<policySetId>",
"name":"<Rule name>",
"description":"<Rule description>",
"action":"ISOLATE",
"zpnIsolationProfileId":"<isolationProfileId>"
}
`
A successful response yields code 204, meaning the isolation rule is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Rule Order
To update a rule order:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}/reorder/{newOrder}`.
- Provide the following parameters in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the policy set.
- `ruleId`: The ID of the particular isolation policy rule.
- `newOrder`: The new order of the rule.
For example: `/mgmtconfig/v1/admin/customers/73186051597795328/policySet/73186051597800308/rule/73186051597800494/reorder/4`.
A successful response returns code 204, meaning the rule order is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
The ability to update the rule order for all rules in a policy set is also available. To learn more, see [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api#bulkUpdatingRuleOrder).
Deleting an Isolation Policy Rule
To delete an isolation policy rule:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the isolation policy set captured in the p[rerequisite API call](#prerequisite).
- `ruleId`: The ID of the particular isolation policy rule you want to delete.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/policySet/72057615512764421/rule/72057615512764641`.
A successful response yields code 204, meaning the isolation rule is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details of All Client Types
To get details of all client types:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/clientTypes`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/73186051597795328/clientTypes`.
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
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/73186051597795328/platform`.
- [View an example response](#examplePlatformType)
[]{
"linux":"Linux",
"android":"Android",
"windows":"Windows",
"ios":"iOS",
"mac":"Mac"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).