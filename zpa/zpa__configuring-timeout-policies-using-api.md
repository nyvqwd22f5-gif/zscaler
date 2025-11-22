# Configuring Timeout Policies Using API
Source: https://help.zscaler.com/zpa/configuring-timeout-policies-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484806.pdf

This article provides information on managing Zscaler Private Access (ZPA) timeout policy use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
[]Prerequisite API Call
To get the policySetId by policy type:
- Send a `GET` request to the following endpoint in the policy set controller: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/policyType/{policyType}`.
- Provide the `policyType`, the value for differentiating the policy types, in the request endpoint. The supported values are:
- `ACCESS_POLICY or GLOBAL_POLICY`
- `TIMEOUT_POLICY or REAUTH_POLICY`
- `BYPASS_POLICY or CLIENT_FORWARDING_POLICY`
- `INSPECTION_POLICY` (i.e., AppProtection policy)
- `ISOLATION_POLICY`
- `REDIRECTION_POLICY`
- `CAPABILITIES_POLICY`
- `CREDENTIAL_POLICY`
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/policySet/policyType/TIMEOUT_POLICY`.
- [View an example response](#ViewExample)
[]{
"id": "217246660303019912",
"modifiedTime": "1619407211",
"creationTime": "1474933642",
"modifiedBy": "217246660303024869",
"name": "ReAuth_Policy",
"enabled": true,
"description": "Re-Authentication policies.",
"policyType": "2"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint in the policy set controller: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/rules/policyType/{policyType}?page=1&pagesize=20`.
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
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/policySet/rules/policyType/TIMEOUT_POLICY?page=1&pagesize=2.`
- [View an example response](#paginatedResponse)
[]{
"totalPages": "2",
"list": [
{
"id": "217246660303023272",
"modifiedTime": "1629497358",
"modifiedBy": "72057594037978891",
"name": "Test",
"ruleOrder": "1",
"priority": "4",
"policyType": "2",
"operator": "AND",
"conditions": [
{
"id": "506762",
"modifiedTime": "1629497328",
"creationTime": "1629497328",
"modifiedBy": "72057594037978891",
"operator": "OR",
"negated": false,
"operands": [
{
"id": "506763",
"creationTime": "1629497328",
"modifiedBy": "72057594037978891",
"objectType": "APP",
"lhs": "id",
"rhs": "217246660303022176",
"name": "testl.com"
},
{
"id": "506764",
"creationTime": "1629497328",
"modifiedBy": "72057594037978891",
"objectType": "APP_GROUP",
"lhs": "id",
"rhs": "217246660302996388",
"name": "Apps for All"
}
]
},
{
"id": "506765",
"modifiedTime": "1629497328",
"creationTime": "1629497328",
"modifiedBy": "72057594037978891",
"operator": "OR",
"negated": false,
"operands": [
{
"id": "506766",
"creationTime": "1629497328",
"modifiedBy": "72057594037978891",
"objectType": "SAML",
"lhs": "217246660303022775",
"rhs": "testing",
"name": "test234324"
}
]
},
{
"id": "506767",
"modifiedTime": "1629497328",
"creationTime": "1629497328",
"modifiedBy": "72057594037978891",
"operator": "OR",
"negated": false,
"operands": [
{
"id": "506768",
"creationTime": "1629497328",
"modifiedBy": "72057594037978891",
"objectType": "CLIENT_TYPE",
"lhs": "id",
"rhs": "zpn_client_type_zapp",
"name": "zpn_client_type_zapp"
}
]
}
],
"action": "RE_AUTH",
"reauthTimeout": "172800",
"reauthIdleTimeout": "600",
"customMsg": "timeout message",
"defaultRuleName": "Default_Rule",
"defaultRule": false
},
{
"id": "217246660303024789",
"modifiedTime": "1629497358",
"modifiedBy": "72057594037978891",
"name": "test_zapp_reauth",
"ruleOrder": "2",
"priority": "3",
"policyType": "2",
"operator": "AND",
"conditions": [
{
"id": "489501",
"modifiedTime": "1612834764",
"creationTime": "1612834764",
"modifiedBy": "217246660303023754",
"operator": "OR",
"negated": false,
"operands": [
{
"id": "489502",
"creationTime": "1612834764",
"modifiedBy": "217246660303023754",
"objectType": "SAML",
"lhs": "217246660303022795",
"rhs": "test@mockcompany.com",
"name": "login_Custom entityId IDP configuration - User sso - do NOT delete"
}
]
}
],
"action": "RE_AUTH",
"reauthTimeout": "2592000",
"reauthIdleTimeout": "3456000",
"defaultRuleName": "Default_Rule",
"defaultRule": false
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Get Required Details for the Timeout Policy
Before creating a timeout rule, you must get the following required details needed for the policy criteria:
- Application segment. To learn more, see [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api#getAppSegments).
- Client types. To learn more, see [Getting Details of All Client Types](#getClientTypes).
- Cloud Connector Group. To learn more, see [Obtaining Cloud Connector Group Details Using API](/zpa/obtaining-cloud-connector-group-details-using-api).
- IdP. To learn more, see [Obtaining IdP Configuration Details Using API](/zpa/obtaining-idp-configuration-details-using-api).
- Machine Group. To learn more, see [Obtaining Machine Group Details Using API](/zpa/obtaining-machine-group-details-using-api).
- Platform types. To learn more, see [Getting Platform Types for a Customer](#getPlatformTypes).
- Posture profile. To learn more, see [Obtaining Posture Profile Details Using API](/zpa/obtaining-posture-profile-details-using-api).
- SAML attribute. To learn more, see [Obtaining SAML Attribute Details Using API](/zpa/obtaining-saml-attribute-details-using-api).
- SCIM attribute. To learn more, see [Obtaining SCIM Attribute Details Using API](/zpa/obtaining-scim-attribute-details-using-api).
- SCIM attribute value. To learn more, see [Obtaining SCIM Attribute Details Using API](/zpa/obtaining-scim-attribute-details-using-api).
- SCIM Group. To learn more, see [Obtaining SCIM Group Details Using API](/zpa/obtaining-scim-group-details-using-api).
- Segment Group. To learn more, see [Configuring Segment Group Details Using API](/zpa/configuring-segment-groups-using-api#getSegmentGroups).
[]Creating a New Timeout Policy Rule
This API will be deprecated in a future release, and a new API to create a new policy rule is provided. To learn more, see [Creating a New Timeout Policy Rule V2](#postV2).
To add a new timeout policy rule for a given policy set and for a given customer:
- Send a `POST` request to the following endpoint in the policy set controller `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the timeout policy set captured in the [Prerequisite API Call](#Prerequisite) section.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/policySet/72057615512764594/rule`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the entire JSON payload and provide the policy criteria you want for creating a timeout rule with the specific SAML attributes as one of the criteria.
- [View the entire JSON payload](#Viewthejsonpayload)
[]{
"conditions": [{
"operands": [{
"objectType": "APP",
"lhs": "id",
"rhs": "<applicationId>"
}, {
"objectType": "APP_GROUP",
"lhs": "id",
"rhs": "<segmentGroupId>"
}],
}, {
"operands": [{
"objectType": "SAML",
"lhs": "<samlAttrId>",
"rhs": "<samlAttrValue>"
}],
"operator": "OR"
}, {
"operands": [{
"objectType": "SCIM",
"lhs": "<scimAttrId>",
"rhs": "<scimAttrValue>"
}],
"operator": "OR"
}, {
"operands": [{
"objectType": "SCIM_GROUP",
"lhs": "<scimGroupAttrId>",
"rhs": "<scimGroupAttrValue>"
}],
"operator": "OR"
}, {
"operands": [{
"objectType": "POSTURE",
"lhs": "<postureUdid>",
"rhs": true
}],
"operator": "OR"
}, {
"operands": [{
"objectType": "TRUSTED_NETWORK",
"lhs": "<networkId>",
"rhs": true
}],
"operator": "OR"
}, {
"operands": [{
"objectType": "CLIENT_TYPE",
"lhs": "id",
"rhs": "zpn_client_type_zapp"
}],
"operator": "OR"
}, {
"operands": [{
"objectType": "MACHINE_GRP",
"lhs": "id",
"rhs": "<machineGroupId>"
}],
"operator": "OR"
}, {
"operands": [{
"objectType": "CLOUD_CONNECTOR_GROUP",
"lhs": "id",
"rhs": "<CloudConnectorGroupId>"
}],
}],
"name": "Test Timeout Policy",
"description": "Description",
"action": "RE_AUTH",
"customMsg": "msg",
"reauthTimeout": 172800,
"reauthIdleTimeout": 600
}
- [View the minimum criteria for a JSON payload](#Viewtheminimumcriteriapayload)
[]{
"name": "PolicyName",
"action": "RE_AUTH",
"reauthTimeout": 172800,
"reauthIdleTimeout": 600
}
- [View an example response](#Viewanexampleresponse6)
[]{
"id": "72057615512764641",
"creationTime": "1612891454",
"modifiedBy": "72057615512764638",
"name": "Test Timeout Policy",
"description": "Test Timeout Policy",
"ruleOrder": "7",
"priority": "1",
"policyType": "1",
"operator": "AND",
"action": "RE_AUTH",
"reauthTimeout": "172800",
"reauthIdleTimeout": "600",
"customMsg": "msg",
"auditMessage": "{\"idleConnectionTimeoutInSeconds\":\"600\",\"policyType\":\"Access Policy\",\"name\":\"Test Timeout Policy\",\"description\":\"Test Timeout Policy\",\"action\":\"RE_AUTH\",\"ruleOrder\":\"7\",\"messageToUser\":\"msg\",\"authenticationTimeoutInSeconds\":\"172800\"}"
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the policy criteria you want to include in the JSON payload. You can also create a timeout rule by just using the minimum criteria in the JSON payload. Refer to the [Adding Field Descriptions](#Fielddescriptions) section for supported values.
[]Creating a New Timeout Policy Rule V2
To add a new timeout rule for a given policy set and for a given customer:
- Send a `POST` request to the following endpoint in the policy set controller `/mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule`.
-
Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the timeout policy set captured in the [prerequisite API call](#prerequisite).
For example: `/mgmtconfig/v2/admin/customers/72057615512764416/policySet/72057615512764594/rule`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the entire JSON payload and provide the policy criteria you want for creating a timeout policy rule with the specific SAML attributes as one of the criteria.
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
"action": "RE_AUTH",
"customMsg": "<Example Custom Message>",
"reauthTimeout": 172800,
"reauthIdleTimeout": 600
}
`
- [View an example response](#postV2response)
[]
`{
"id": "72057615512764641",
"creationTime": "1612891454",
"modifiedBy": "72057615512764638",
"name": "Test Timeout Policy",
"description": "Test Timeout Policy",
"ruleOrder": "7",
"priority": "1",
"policyType": "1",
"operator": "AND",
"action": "RE_AUTH",
"reauthTimeout": "172800",
"reauthIdleTimeout": "600",
"customMsg": "msg",
"auditMessage": "{\"idleConnectionTimeoutInSeconds\":\"600\",\"policyType\":\"Access Policy\",\"name\":\"Test Timeout Policy\",\"description\":\"Test Timeout Policy\",\"action\":\"RE_AUTH\",\"ruleOrder\":\"7\",\"messageToUser\":\"msg\",\"authenticationTimeoutInSeconds\":\"172800\"}"
} `
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the timeout policy use cases:
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
| name | This is the name of the timeout rule | Yes | String |
| description | This is the description of the timeout rule | No | String |
| action | This is for providing the rule action | Yes | Supported value: `RE_AUTH` |
| customMsg | This is for providing a custom message for the user | No | String |
| reauthTimeout | This denotes the authentication timeout | Yes | Provides the timeout value in seconds. The value `-1` denotes `Never`. |
| reauthIdleTimeout | This denotes the idle connection timeout | Yes | Provides the timeout value in seconds. The value `-1` denotes `Default`. |
| conditions | This is for providing the set of conditions for the policy | No | Array of operands. |
| operands | This signifies the various policy criteria | No | Array of attributes (`objectType, lhs, rhs, name`). |
| objectType | This is for specifying the policy criteria | No | Supported values:`APP``APP_GROUP``SAML``IDP``CLIENT_TYPE``POSTURE``SCIM``SCIM_GROUP` |
| lhs | This signifies the key for the object type | No | String ID example: `id` |
| rhs | This denotes the value for the given object type. Its value depends upon the key. | No | For `APP`, `APP_GROUP`, and `IDP`, the supported value is `entity id`.For `CLIENT_TYPE`, the supported values are: `zpn_client_type_zapp` for the Zscaler Client Connector, and `zpn_client_type_exporter` (for Clientless). |
| operator | This denotes the operation type | No | Supported values:` AND, OR` |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
For a comprehensive table of LHS and RHS values, see [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api#lhsandrhsvalues).
Getting Details for a Particular Timeout Rule
To get details for a particular timeout rule:
- Send a `GET` request to the following endpoint in the policy set controller: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the Timeout policy set captured in the [prerequisite API call](#Prerequisite).
- `ruleId`: The ID of the rule you created in the [Creating a New Timeout Policy Rule](#Create) section.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/policySet/72057615512764594/rule/72057615512764641`.
- [View an example response](#ViewanexampleresponseGet)
[]{
"id": "72057615512764641",
"creationTime": "1612891454",
"modifiedBy": "72057615512764638",
"name": "Test Timeout Policy",
"description": "Test Timeout Policy",
"ruleOrder": "7",
"priority": "1",
"policyType": "1",
"operator": "AND",
"action": "RE_AUTH",
"reauthTimeout": "172800",
"reauthIdleTimeout": "600",
"customMsg": "msg",
"auditMessage": "{\"idleConnectionTimeoutInSeconds\":\"600\",\"policyType\":\"Access Policy\",\"name\":\"Test Timeout Policy\",\"description\":\"Test Timeout Policy\",\"action\":\"RE_AUTH\",\"ruleOrder\":\"7\",\"messageToUser\":\"msg\",\"authenticationTimeoutInSeconds\":\"172800\"}",
"policySetId": "72057615512764421"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Timeout Policy Rule
This API will be deprecated in a future release, and a new API to update a policy rule is provided. To learn more, see [Updating a New Timeout Policy Rule V2](#putV2).
To update the details of a timeout policy rule in the policy set:
- Get the `policySetId` captured in the p[rerequisite API call](#Prerequisite).
- Use the entire JSON payload from the [Creating a New Timeout Rule](#Create) section and send a `PUT` request to the following endpoint in the policy set controller: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the Timeout policy set captured in the [prerequisite API call](#Prerequisite).
- `ruleId`: The ID of the rule you created in [Creating a New Timeout Policy Rule](#Create).
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/policySet/72057615512764421/rule/72057615512764641`.
- [View the entire JSON payload](#Viewthejsonpayload2)
[]{
"conditions": [{
"operands": [{
"objectType": "APP",
"lhs": "id",
"rhs": "<applicationId>"
}, {
"objectType": "APP_GROUP",
"lhs": "id",
"rhs": "<segmentGroupId>"
}],
}, {
"operands": [{
"objectType": "SAML",
"lhs": "<samlAttrId>",
"rhs": "<samlAttrValue>"
}],
"operator": "OR"
}, {
"operands": [{
"objectType": "SCIM",
"lhs": "<scimAttrId>",
"rhs": "<scimAttrValue>"
}],
"operator": "OR"
}, {
"operands": [{
"objectType": "SCIM_GROUP",
"lhs": "<scimGroupAttrId>",
"rhs": "<scimGroupAttrValue>"
}],
"operator": "OR"
}, {
"operands": [{
"objectType": "POSTURE",
"lhs": "<postureUdid>",
"rhs": true
}],
"operator": "OR"
}, {
"operands": [{
"objectType": "TRUSTED_NETWORK",
"lhs": "<networkId>",
"rhs": true
}],
"operator": "OR"
}, {
"operands": [{
"objectType": "CLIENT_TYPE",
"lhs": "id",
"rhs": "zpn_client_type_zapp"
}],
"operator": "OR"
}, {
"operands": [{
"objectType": "MACHINE_GRP",
"lhs": "id",
"rhs": "<machineGroupId>"
}],
"operator": "OR"
}, {
"operands": [{
"objectType": "CLOUD_CONNECTOR_GROUP",
"lhs": "id",
"rhs": "<CloudConnectorGroupId>"
}],
}],
"name": "Test Timeout Policy",
"description": "Description",
"action": "RE_AUTH",
"customMsg": "msg",
"reauthTimeout": 172800,
"reauthIdleTimeout": 600
}
- [View the minimum criteria JSON payload](#Viewtheminimumcriteriapayload2)
[]{
"name": "PolicyName",
"action": "RE_AUTH",
"reauthTimeout": 172800,
"reauthIdleTimeout": 600
}
A successful response returns code 204, meaning the timeout policy rule is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the policy criteria you want to include in the JSON payload. You may also use the minimum criteria in the JSON payload to update a timeout policy. Refer to the [Adding Field Descriptions](#Fielddescriptions) section for supported values.
[]Updating a Timeout Policy Rule V2
To update the details of a timeout policy rule in the policy set:
- Get the `policySetId` captured in the [prerequisite API call](#prerequisite).
- Use the entire JSON payload from the [Creating a New Timeout Policy Rule](#Create) section and send a `PUT` request to the following endpoint in the policy set controller: `/mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
-
Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the timeout policy set captured in the [prerequisite API call](#Prerequisite).
- `ruleId`: The ID of the rule you created in [Creating a New Timeout Policy Rule](#postV2).
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
"name": "<Example Policy Rule Name>",
"description": "<Example Policy Rule Description>",
"action": "RE_AUTH",
"customMsg": "<Example Custom Message>",
"reauthTimeout": 172800,
"reauthIdleTimeout": 600
}
`
A successful response returns code 204, meaning the timeout policy rule is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Rule Order
To update a rule order:
- Send a `PUT` request to the following endpoint in the policy set controller: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}/reorder/{newOrder}`.
- Provide the following parameters in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the policy set.
- `ruleId`: The ID of the rule.
- `newOrder`: The new order of the rule.
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/policySet/72057594037938994/rule/72057615512764641/reorder/4`.
A successful response returns code 204, meaning the rule order is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
The ability to update the rule order for all rules in a policy set is also available. To learn more, see [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api#bulkUpdatingRuleOrder).
Deleting a Timeout Policy Rule
To delete a timeout rule:
- Send a `DELETE` request to the following endpoint in the policy set controller: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the timeout policy set captured in the [prerequisite API call](#Prerequisite).
- `ruleId`: The ID of the rule you created in the [Create a New Timeout Rule](#Create) section.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/policySet/72057615512764421/rule/`72057615512764641.
A successful response returns code 204, meaning the timeout rule is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details of All Client Types
To get details of all client types:
- Send a `GET` request to the following endpoint in the policy set controller: `/mgmtconfig/v1/admin/customers/{customerId}/clientTypes`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/clientTypes`.
- [View an example response](#exampleResponseClientTypes)
[]{
"zpn_client_type_exporter": "Web Browser",
"zpn_client_type_machine_tunnel": "Machine Tunnel",
"zpn_client_type_ip_anchoring": "ZIA Service Edge",
"zpn_client_type_edge_connector": "Cloud Connector",
"zpn_client_type_zapp": "Client Connector",
"zpn_client_type_slogger": "ZPA LSS"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Platform Types for a Customer
To get the platform types for a customer:
- Send a `GET` request to the following endpoint in the policy set controller: `/mgmtconfig/v1/admin/customers/{customerId}/platform`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/platform`.
- [View an example response](#examplePlatformType)
[]{
"linux": "Linux",
"android": "Android",
"windows": "Windows",
"ios": "iOS",
"mac": "Mac"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).

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