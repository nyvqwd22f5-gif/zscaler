# Configuring Client Forwarding Policies Using API
Source: https://help.zscaler.com/zpa/configuring-client-forwarding-policies-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484811.pdf

This article provides information on managing Zscaler Private Access (ZPA) client forwarding policy use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
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
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/policySet/policyType/CLIENT_FORWARDING_POLICY`.
- [View an example response](#ViewExample)
[]{
"id":"217246660303023168",
"modifiedTime":"1624647543",
"creationTime":"1562693881",
"modifiedBy":"72057594037984006",
"name":"Bypass_Policy",
"enabled":true,
"description":"Bypass policies.",
"policyType":"4"
}
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/rules/policyType/{policyType}?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policyType`: The value for differentiating the policy types. The supported values are:
- `ACCESS_POLICY or GLOBAL_POLICY`
- `TIMEOUT_POLICY` or `REAUTH_POLICY`
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
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/policySet/rules/policyType/CLIENT_FORWARDING_POLICY?page=1&pagesize=2.`
- [View an example response](#paginatedResponse)
[]{
"totalPages":"3",
"list":[
{
"id":"217246660303023826",
"modifiedTime":"1628101611",
"creationTime":"1590609953",
"modifiedBy":"217246660303023906",
"name":"allowall",
"ruleOrder":"1",
"priority":"5",
"policyType":"4",
"operator":"AND",
"action":"INTERCEPT",
"defaultRuleName":"Default_Rule",
"defaultRule":false
},
{
"id":"217246660303023636",
"modifiedTime":"1628101611",
"creationTime":"1577988747",
"modifiedBy":"217246660303023906",
"name":"user nodownload gets no apps",
"ruleOrder":"2",
"priority":"4",
"policyType":"4",
"operator":"AND",
"conditions":[
{
"id":"288237",
"modifiedTime":"1577988747",
"creationTime":"1577988747",
"modifiedBy":"217246660302995458",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"288238",
"creationTime":"1577988747",
"modifiedBy":"217246660302995458",
"objectType":"SAML",
"lhs":"217246660303022796",
"rhs":"nodownload",
"name":"username_Custom entityId IDP configuration - User sso - do NOT delete"
}
]
}
],
"action":"BYPASS",
"defaultRuleName":"Default_Rule",
"defaultRule":false
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
- Valid search string values. The search string values are in the format `action OPERATOR ruleAction`. The supported `ruleAction` values for client forwarding policies are `INTERCEPT` (forward to ZPA), `INTERCEPT_ACCESIBLE` (only forward allowed applications), and `BYPASS` (bypass ZPA). The supported value for `OPERATOR` is `EQ` (i.e., equals). Only search string values that correspond to the values for valid rule actions and operators are supported. For example, the string `action%20EQ%INTERCEPT` is supported for the **Rule Action** filter, using the **Equals** operator, for the `INTERCEPT` rule action.
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/policySet/rules/policyType/CLIENT_FORWARDING_POLICY?page=1&pagesize=500&search=action%20EQ%20INTERCEPT`.
If not provided, the default page size is 20. The maximum page size is 500.
- [View an example response](#ruleActionResponse)
[]
`{
"totalPages":"4",
"totalCount":"0",
"list":[
{
"id":"72057594037992779",
"creationTime":"1669125035",
"modifiedBy":"72057594037928020",
"name":"Posture11",
"ruleOrder":"1",
"priority":"2",
"policyType":"4",
"operator":"AND",
"action":"INTERCEPT",
"defaultRule":false,
"defaultRuleName":"Default_Rule",
"restrictedEntity":false
},
{
"id":"72057594038018626",
"creationTime":"1681997589",
"modifiedBy":"72057594037941138",
"name":"asd",
"description":"ef",
"ruleOrder":"2",
"priority":"2",
"policyType":"4",
"operator":"AND",
"action":"INTERCEPT",
"defaultRule":false,
"defaultRuleName":"Default_Rule",
"restrictedEntity":false
},
{
"id":"72057594038032911",
"modifiedTime":"1687206863",
"creationTime":"1687206863",
"modifiedBy":"72057594037993401",
"name":"Copy of asd",
"description":"ef",
"ruleOrder":"3",
"priority":"2",
"policyType":"4",
"operator":"AND",
"action":"INTERCEPT",
"defaultRule":false,
"defaultRuleName":"Default_Rule",
"restrictedEntity":false
}
]
}`
If you use the ZPA API Portal or the Reference Guide to make your API calls, the search field string does not require any characters. For example, `action%20EQ%20INTERCEPT` is `action EQ INTERCEPT`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Required Details for the Client Forwarding Policy
The following are the required details needed for the policy criteria:
- Application segment. To learn more, see [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api#getAppSegments).
- Client types. To learn more, see [Getting Details of All Client Types](#getClientTypes).
- Cloud Connector group. To learn more, see [Obtaining Cloud Connector Group Details Using API](/zpa/obtaining-cloud-connector-group-details-using-api).
- IdP. To learn more, see [Obtaining IdP Configuration Details Using API](/zpa/obtaining-idp-configuration-details-using-api).
- Machine group. To learn more, see [Obtaining Machine Group Details Using API](/zpa/obtaining-machine-group-details-using-api).
- Platform types. To learn more, see [Getting Platform Types for a Customer](#getPlatformTypes).
- Posture profile. To learn more, see [Obtaining Posture Profile Details Using API](/zpa/obtaining-posture-profile-details-using-api).
- SAML attribute. To learn more, see [Obtaining SAML Attribute Details Using API](/zpa/obtaining-saml-attribute-details-using-api).
- SCIM attribute. To learn more, see [Obtaining SCIM Attribute Details Using API](/zpa/obtaining-scim-attribute-details-using-api).
- SCIM attribute value. To learn more, see [Obtaining SCIM Attribute Details Using API](/zpa/obtaining-scim-attribute-details-using-api#getSCIMvalue).
- SCIM groups. To learn more, see [Obtaining SCIM Group Details Using API](/zpa/obtaining-scim-group-details-using-api).
- Segment Group. To learn more, see [Configuring Segment Groups Using API](/zpa/configuring-segment-groups-using-api).
- Trusted network. To learn more, see [Obtaining Trusted Network Details Using API](/zpa/obtaining-trusted-network-details-using-api).
[]Creating a New Client Forwarding Rule
This API will be deprecated in a future release, and a new API to create a policy rule is provided. To learn more, see [Creating a New Client Forwarding Policy Rule V2](#postV2).
To add a new client forwarding rule for a given policy set and for a given customer:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in the [prerequisite API call](#Prerequisite).
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/policySet/72057615512764421/rule`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the entire JSON payload and provide the policy criteria you want for creating a client forwarding rule with the specific SAML attributes as one of the criteria.
- [View the entire JSON payload](#Viewthejsonpayload)
[]
{
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
"name":"Test Policy",
"description":"test policy",
"action":"INTERCEPT"
}
- [View the minimum criteria for a JSON payload](#minimumcriteriaJson)
[]{
"name":"PolicyName",
"action":"RE_AUTH",
"reauthTimeout":172800,
"reauthIdleTimeout":600
}
- [View the minimum criteria example response](#Viewanexampleresponse6)
[]{
"id":"72057615512764645",
"creationTime":"1612898408",
"modifiedBy":"72057615512764644",
"name":"Client Forwarding Policy Test",
"description":"Description",
"ruleOrder":"7",
"priority":"1",
"policyType":"1",
"operator":"AND",
"action":"ALLOW",
"customMsg":"MsgString",
"auditMessage":"{\"policyType\":\"Access Policy\",\"name\":\"Client Forwarding Policy Test\",\"description\":\"Description\",\"action\":\"ALLOW\",\"ruleOrder\":\"7\",\"messageToUser\":\"MsgString\"}"
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the policy criteria you want to include in the JSON payload. You can also use the minimum criteria in the JSON payload to create a client forwarding rule. Refer to the [Field Descriptions](#Fielddescriptions) section for supported values.
[]Creating a New Client Forwarding Policy Rule V2
To add a new client forwarding rule for a given policy set and for a given customer:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule`.
-
Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in the [prerequisite API call](#Prerequisite).
For example: `/mgmtconfig/v2/admin/customers/72057615512764416/policySet/72057615512764421/rule`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the JSON payload and provide the policy criteria you want for creating a client forwarding rule with the specific SAML attributes as one of the criteria.
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
"name":"<Example Policy Rule Name>",
"description":"<Example Policy Rule Description>",
"action":"INTERCEPT"
}
`
- [View the minimum criteria JSON payload](#postV2minPayload)
[]
`{
"name":"PolicyName",
"action":"RE_AUTH",
"reauthTimeout":172800,
"reauthIdleTimeout":600
}`
- [View the example response](#postV2response)
[]
`{
"id":"72057615512764645",
"creationTime":"1612898408",
"modifiedBy":"72057615512764644",
"name":"Client Forwarding Policy Test",
"description":"Description",
"ruleOrder":"7",
"priority":"1",
"policyType":"1",
"operator":"AND",
"action":"ALLOW",
"customMsg":"MsgString",
"auditMessage":"{\"policyType\":\"Access Policy\",\"name\":\"Client Forwarding Policy Test\",\"description\":\"Description\",\"action\":\"ALLOW\",\"ruleOrder\":\"7\",\"messageToUser\":\"MsgString\"}"
}`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the client forwarding policy use cases:
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
| name | This is the name of the client forwarding rule | Yes | String |
| description | This is the description of the client forwarding rule | No | String |
| action | This is for providing the rule action | Yes | Supported values: `INTERCEPT` (forward to ZPA) (default value), `INTERCEPT_ACCESIBLE` (only forward allowed applications), `BYPASS` (bypass ZPA) |
| customMsg | This is for providing a custom message for the user | No | String |
| conditions | This is for providing the set of conditions for the policy | No | Array of operands |
| operands | This signifies the various policy criterias | No | Array of attributes (`objectType, lhs, rhs, name`) |
| objectType | This is for specifying the policy criteria | No | Supported values:`APP``APP_GROUP``SAML``IDP``CLIENT_TYPE``TRUSTED_NETWORK``POSTURE``SCIM``SCIM_GROUP``CLOUD_CONNECTOR_GROUP``TRUSTED_NETWORK` is only supported for` CLIENT_TYPE` |
| lhs | This signifies the key for the object type | No | String ID example: `id` |
| rhs | This denotes the value for the given object type. Its value depends upon the key. | No | For `APP`, `APP_GROUP`, and `IDP`, the supported value is `entity id`For `CLIENT_TYPE`, the supported values are: `zpn_client_type_zapp` for the Zscaler Client Connector and `zpn_client_type_exporter` (for Clientless).For `TRUSTED_NETWORK`, the supported value is `true`. |
| operator | This denotes the operation type | No | Supported values: `AND`, `OR` |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
For a comprehensive table of LHS and RHS values, see [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api#lhsandrhsvalues).
Getting Details for a Particular Client Forwarding Rule
To get details for a particular client forwarding rule:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in the [prerequisite API call](#Prerequisite).
- `ruleId`: The ID of the rule you created in [Creating a New Client Forwarding Policy Rule](#Create).
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/policySet/72057615512764421/rule/72057615512764645`.
- [View an example response](#Viewanexampleresponse8)
[]{
"id":"72057615512764645",
"creationTime":"1612898408",
"modifiedBy":"72057615512764644",
"name":"Client Forwarding Policy Test",
"description":"Description",
"ruleOrder":"7",
"priority":"1",
"policyType":"1",
"operator":"AND",
"action":"ALLOW",
"customMsg":"MsgString",
"auditMessage":"{\"policyType\":\"Access Policy\",\"name\":\"Client Forwarding Policy Test\",\"description\":\"Description\",\"action\":\"ALLOW\",\"ruleOrder\":\"7\",\"messageToUser\":\"MsgString\"}",
"policySetId":"72057615512764421"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Client Forwarding Policy Rule
This API will be deprecated in a future release, and a new API to update a policy rule is provided. To learn more, see [Updating a Client Forwarding Policy Rule V2](#putV2).
To update the details of a client forwarding rule in the policy set:
- Get the `policySetId` provided in the [prerequisite API call](#Prerequisite).
- Use the updated JSON payload from [Creating a New Client Forwarding Policy Rule](#Create) and send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the client forwarding policy set captured in the [prerequisite API call](#Prerequisite).
- `ruleId`: The ID of the rule you created in [Creating a New Client Forwarding Policy Rule](#Create).
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/policySet/72057615512764421/rule/72057615512764645`.
- [View the JSON payload](#Viewthejsonpayload2)
[]
{
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
"name":"Test Policy",
"description":"test policy",
"action":"INTERCEPT"
}
- [View the minimum criteria JSON payload](#viewtheminimumcriteriaJsonpayload2)
[]{
"name":"PolicyName",
"action":"RE_AUTH",
"reauthTimeout":172800,
"reauthIdleTimeout":600
}
A successful response returns code 204, meaning the client forwarding rule is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the policy criteria you want to include in the JSON payload. You can also use the minimum criteria in the JSON payload to update a client forwarding policy. Refer to the [Adding Field Descriptions](#Fielddescriptions) section for supported values.
[]Updating a Client Forwarding Policy Rule V2
To update the details of a client forwarding rule in the policy set:
- Get the `policySetId` provided in [prerequisite API call](#Prerequisite).
- Use the updated JSON payload from [Creating a New Client Forwarding Policy Rule](#Create) and send a `PUT` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
-
Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the client forwarding policy set captured in the [prerequisite API call](#Prerequisite).
- `ruleId`: The ID of the rule you created in [Creating a New Client Forwarding Policy Rule](#Create).
For example: `/mgmtconfig/v2/admin/customers/72057615512764416/policySet/72057615512764421/rule/72057615512764645`.
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
"name":"<Example Policy Rule Name>",
"description":"<Example Policy Rule Description>",
"action":"INTERCEPT"
}
`
A successful response returns code 204, meaning the client forwarding rule is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Rule Order
To update a rule order:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}/reorder/{newOrder}`.
- Provide the following parameters in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the policy set.
- `ruleId`: The ID of the rule.
- `newOrder`: The new order of the rule.
For example: `mgmtconfig/v1/admin/customers/72057594037927936/policySet/72057594037938994/rule/72057615512764641/reorder/4`.
A successful response returns code 204, meaning the rule order is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
The ability to update the rule order for all rules in a policy set is also available. To learn more, see [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api#bulkUpdatingRuleOrder).
Deleting a Client Forwarding Rule
To delete a client forwarding rule:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the client forwarding policy set captured in the [prerequisite API call](#Prerequisite).
- `ruleId`: The ID of the rule you created in [Creating a New Client Forwarding Rule](#Create).
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/policySet/72057615512764421/rule/72057615512764645`.
A successful response yields code 204, meaning the client forwarding rule is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
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