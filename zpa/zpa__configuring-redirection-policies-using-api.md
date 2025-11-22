# Configuring Redirection Policies Using API
Source: https://help.zscaler.com/zpa/configuring-redirection-policies-using-api
PDF: https://help.zscaler.com/pdf/com/en/1485771.pdf

This article provides information on managing Zscaler Private Access (ZPA) [redirection policy](/zpa/about-redirection-policy) use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
[]Prerequisite API Call
To get the `policySetId` by policy type:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/policyType/{policyType}`.
- Provide the `policyType`, the value for differentiating the policy types, in the request endpoint. The supported values are:
- `ACCESS_POLICY` or `GLOBAL_POLICY` (i.e., access policy)
- `TIMEOUT_POLICY` or `REAUTH_POLICY` (i.e., timeout policy)
- `BYPASS_POLICY` or `CLIENT_FORWARDING_POLICY` (i.e., client forwarding policy)
- `INSPECTION_POLICY` (i.e., AppProtection policy)
- `ISOLATION_POLICY` (i.e., Isolation policy)
- `REDIRECTION_POLICY` (i.e., redirection policy)
- `CAPABILITIES_POLICY` (i.e., privileged capabilities policy)
- `CREDENTIAL_POLICY` (i.e., privileged credentials policy)
- `CLIENTLESS_SESSION_PROTECTION_POLICY` (i.e., browser protection policy)
- `PRIVILEGED_PORTAL_POLICY` (i.e., privileged portals policy)
To get a redirection policy set ID, provide the `REDIRECTION_POLICY` policy type in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/policySet/policyType/REDIRECTION_POLICY`.
- [View an example response](#GetPolicySet)
[]{
"id": "217246660303027250",
"creationTime": "1683058318",
"modifiedBy": "72057594038040687",
"name": "ReDirection_Policy",
"enabled": true,
"description": "Re-Direction policies.",
"policyType": "10",
"sorted": true
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
To get the paginated policy rules for the specified policy type:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/rules/policyType/{policyType}?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policyType`: The value for differentiating the policy types. The supported values are:
- `ACCESS_POLICY` or `GLOBAL_POLICY` (i.e., access policy)
- `TIMEOUT_POLICY` or `REAUTH_POLICY` (i.e., timeout policy)
- `BYPASS_POLICY` or `CLIENT_FORWARDING_POLICY` (i.e., client forwarding policy)
- `INSPECTION_POLICY` (i.e., AppProtection policy)
- `ISOLATION_POLICY` (i.e., Isolation policy)
- `REDIRECTION_POLICY` (i.e., redirection policy)
- `CAPABILITIES_POLICY` (i.e., privileged capabilities policy)
- `CREDENTIAL_POLICY` (i.e., privileged credentials policy)
- `CLIENTLESS_SESSION_PROTECTION_POLICY` (i.e., browser protection policy)
- `PRIVILEGED_PORTAL_POLICY` (i.e., privileged portals policy)
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/policySet/rules/policyType/REDIRECTION_POLICY?page=1&pagesize=1`.
- [View an example response](#GetPolicySetPaginated)
[]{
"totalPages": "10",
"list": [
{
"id": "72057594038644505",
"modifiedTime": "1683038805",
"modifiedBy": "72057594038606777",
"name": "New UX test",
"description": "in safari",
"ruleOrder": "1",
"priority": "1",
"policyType": "10",
"operator": "AND",
"conditions": [
{
"id": "31470314",
"modifiedTime": "1683038805",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"operator": "OR",
"negated": false,
"operands": [
{
"id": "31470315",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"objectType": "COUNTRY_CODE",
"lhs": "AE",
"rhs": "true",
"name": "AE"
},
{
"id": "31470316",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"objectType": "COUNTRY_CODE",
"lhs": "AG",
"rhs": "true",
"name": "AG"
}
]
},
{
"id": "31470317",
"modifiedTime": "1683038805",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"operator": "OR",
"negated": false,
"operands": [
{
"id": "31470318",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"objectType": "CLIENT_TYPE",
"lhs": "id",
"rhs": "zpn_client_type_machine_tunnel",
"name": "zpn_client_type_machine_tunnel"
},
{
"id": "31470319",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"objectType": "CLIENT_TYPE",
"lhs": "id",
"rhs": "zpn_client_type_branch_connector",
"name": "zpn_client_type_branch_connector"
}
]
},
{
"id": "31470320",
"modifiedTime": "1683038805",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"operator": "OR",
"negated": false,
"operands": [
{
"id": "31470321",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"objectType": "SAML",
"lhs": "72057594038603627",
"rhs": "test 1",
"name": "http___schemas_xmlsoap_org_ws_2005_05_identity_claims_givenname_Azure_User"
},
{
"id": "31470322",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"objectType": "SAML",
"lhs": "72057594038603627",
"rhs": "test 2",
"name": "http___schemas_xmlsoap_org_ws_2005_05_identity_claims_givenname_Azure_User"
},
{
"id": "31470323",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"objectType": "SAML",
"lhs": "72057594038603627",
"rhs": "test 3",
"name": "http___schemas_xmlsoap_org_ws_2005_05_identity_claims_givenname_Azure_User"
},
{
"id": "31470324",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"objectType": "SAML",
"lhs": "72057594038042068",
"rhs": "test 1",
"name": "dssdd"
},
{
"id": "31470325",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"objectType": "SAML",
"lhs": "72057594038042068",
"rhs": "test 2",
"name": "dssdd"
},
{
"id": "31470326",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"objectType": "SAML",
"lhs": "72057594038042068",
"rhs": "test 3",
"name": "dssdd"
},
{
"id": "31470327",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"objectType": "SAML",
"lhs": "72057594038620864",
"rhs": "test 1",
"name": "department1"
},
{
"id": "31470328",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"objectType": "SAML",
"lhs": "72057594038620864",
"rhs": "test 2",
"name": "department1"
},
{
"id": "31470329",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"objectType": "SAML",
"lhs": "72057594038620864",
"rhs": "test 3",
"name": "department1"
},
{
"id": "31470330",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"objectType": "SCIM",
"lhs": "72057594037988775",
"rhs": "bjensen3",
"name": "userName",
"idpId": "72057594037961373"
},
{
"id": "31470331",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"objectType": "SCIM_GROUP",
"lhs": "72057594037961373",
"rhs": "20470"
},
{
"id": "31470332",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"objectType": "SCIM_GROUP",
"lhs": "72057594037961373",
"rhs": "20524"
},
{
"id": "31470333",
"creationTime": "1683038805",
"modifiedBy": "72057594038606777",
"objectType": "IDP",
"lhs": "id",
"rhs": "72057594038072942",
"name": "Testtest"
}
]
}
],
"action": "REDIRECT_PREFERRED",
"serviceEdgeGroups": [
{
"id": "72057594038038943",
"modifiedTime": "1680861999",
"creationTime": "1622618432",
"modifiedBy": "72057594037987389",
"name": "testvr",
"enabled": false,
"description": "testvr",
"versionProfileId": "0",
"overrideVersionProfile": false,
"isPublic": "TRUE",
"location": "India",
"cityCountry": "Wadgaon, IN",
"countryCode": "IN",
"useInDrMode": false,
"graceDistanceEnabled": false
},
{
"id": "72057594038054625",
"modifiedTime": "1639642844",
"creationTime": "1633932755",
"modifiedBy": "72057594038046699",
"name": "testserviceedgegrp-1_2",
"enabled": true,
"description": "sdsd",
"versionProfileId": "0",
"overrideVersionProfile": false,
"isPublic": "FALSE",
"location": "Hyderabad, Telangana, India",
"cityCountry": "Hyderabad, IN",
"countryCode": "IN",
"graceDistanceEnabled": false
}
],
"defaultRule": false,
"restrictedEntity": false
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Required Details for the Redirection Policy
Before creating a redirection policy rule, you must get the following required client types needed for the policy criteria. To learn more, see [Getting Details of All Client Types](#GetClientTypes).
[]Creating a New Redirection Policy Rule
To create a new redirection policy rule for a given policy set and for a given customer:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule`.
-
Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in the [prerequisite API call](#prereq).
For example: `/mgmtconfig/v2/admin/customers/72057594037927936/policySet/72057594038644503/rule`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the policy criteria you want for creating a redirection policy rule.
- [View the JSON payload](#postV2payload)
[]
`{
"conditions":[
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
"objectType":"COUNTRY_CODE",
"entryValues":[
{
"lhs":"<CountryCode>",
"rhs":true
}
]
}
]
}
],
"name":"PolicyName",
"description":"Description",
"action":"REDIRECT_ALWAYS",
"customMsg":"MsgString"
}`
- [View an example response](#postV2response)
[]
`{
"policySetId":"72057594038644503",
"conditions":[
{
"operands":[
{
"objectType":"COUNTRY_CODE",
"entryValues":[
{
"lhs":"US",
"rhs":true
}
]
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"CLIENT_TYPE",
"values":[
"zpn_client_type_machine_tunnel",
"zpn_client_type_edge_connector",
"zpn_client_type_zapp_partner",
"zpn_client_type_zapp",
"zpn_client_type_branch_connector"
]
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"SCIM",
"entryValues":[
{
"lhs":"72057594037988776",
"rhs":"Jensen"
}
]
},
{
"objectType":"SCIM_GROUP",
"entryValues":[
{
"lhs":"72057594037961373",
"rhs":20470
}
]
}
],
"operator":"OR"
}
],
"name":"Example Redirection Policy",
"description":"Example description",
"action":"REDIRECT_ALWAYS",
"serviceEdgeGroups":[
{
"id":"72057594038056014",
"modifiedTime":"1678798195",
"creationTime":"1634589741",
"modifiedBy":"72057594038606777",
"name":"test_abc",
"MicrotenantName":"Default",
"enabled":true,
"description":"Private broker group",
"versionProfileId":"72057594038644936",
"overrideVersionProfile":false,
"versionProfileName":"hshinde-vp",
"versionProfileVisibilityScope":"ALL",
"upgradeTimeInSecs":"25200",
"upgradeDay":"MONDAY",
"isPublic":"FALSE",
"location":"California, USA",
"latitude":"36.778261",
"longitude":"-119.4179324",
"cityCountry":"Sanger, US",
"countryCode":"US",
"useInDrMode":false,
"graceDistanceEnabled":true,
"graceDistanceValue":"2500.0",
"graceDistanceValueUnit":"MILES",
"restrictedEntity":false,
"level":2,
"parent":"California, USA",
"isLeaf":true
}
]
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the redirection policy use cases:
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
[](/zpa/configuring-service-edges)
-
-
[](/zpa/about-api-keys)[](/zpa/configuring-microtenants-using-api)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| name | The name of the redirection rule | Yes | String |
| description | The description of the redirection rule | No | String |
| action | This is for providing the rule action | Yes | Supported values:`REDIRECT_DEFAULT``REDIRECT_PREFERRED``REDIRECT_ALWAYS` |
| conditions | This is for providing the set of conditions for the policy | No | Array of operands |
| operands | The various policy criteria | No | Array of attributes (`objectType`, `lhs`, `rhs`, `name`) |
| objectType | The policy criteria | No | Supported values:`IDP``SCIM``SCIM_GROUP``CLIENT_TYPE``COUNTRY_CODE` |
| lhs | The key for the object type | No | String ID example: `"id"` |
| rhs | The value for the given object type. Its value depends upon the key. | No | For `IDP`, the supported value is `entity id`.For `CLIENT_TYPE`, the supported values are:`zpn_client_type_machine_tunnel` (for Machine Tunnels)`zpn_client_type_edge_connector` (For Cloud Connectors)`zpn_client_type_zapp` (for Zscaler Client Connector)`zpn_client_type_zapp_partner` (for Zscaler Client Connector Support for Multiple Tenants)`zpn_client_type_branch_connector` (for Branch Connectors)The `CLIENT_TYPE` values `zpn_client_type_edge_connector` and `zpn_client_type_branch_connector` are not supported if the `action` field is set to `REDIRECT_ALWAYS`.For `POSTURE`, the supported values are:`true` (verified)`false` (verification failed) |
| operator | The operation type | No | Supported values:`AND``OR` |
| graceDistanceEnabled | If enabled, allows ZPA Private Service Edge groups within the specified distance to be prioritized over a closer ZPA Public Service Edge. To learn more, see Configuring ZPA Private Service Edges. | No | Default: `false`Boolean: `true`, `false` |
| graceDistanceValue | Indicates the maximum distance in miles or kilometers to ZPA Private Service Edge groups that would override a ZPA Public Service Edge | No | Integer |
| graceDistanceValueUnit | Indicates the grace distance unit of measure in miles or kilometers. This value is only required if `graceDistanceEnabled` is set to `true`. | No | Supported values:`MILES``KMS` |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
For a comprehensive table of LHS and RHS values, see [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api#lhsandrhsvalues).
Getting Details for a Particular Redirection Rule
To get details for a particular redirection rule:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the redirection policy set captured in the [prerequisite API call](#prereq).
- `ruleId`: The ID of the redirection rule.
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/policySet/72057594038644503/rule/72057594038649412`.
- [View an example response](#GetRedirectionRuleExample)
[]{
"id": "72057594038649412",
"modifiedTime": "1683038920",
"creationTime": "1683038920",
"modifiedBy": "72057594038040687",
"name": "Example Redirection Policy",
"description": "Example description",
"ruleOrder": "9",
"priority": "1",
"policyType": "10",
"operator": "AND",
"conditions": [
{
"id": "31470342",
"modifiedTime": "1683038920",
"creationTime": "1683038920",
"modifiedBy": "72057594038040687",
"operator": "OR",
"negated": false,
"operands": [
{
"id": "31470343",
"creationTime": "1683038920",
"modifiedBy": "72057594038040687",
"objectType": "COUNTRY_CODE",
"lhs": "US",
"rhs": "true",
"name": "US"
}
]
},
{
"id": "31470344",
"modifiedTime": "1683038920",
"creationTime": "1683038920",
"modifiedBy": "72057594038040687",
"operator": "OR",
"negated": false,
"operands": [
{
"id": "31470345",
"creationTime": "1683038920",
"modifiedBy": "72057594038040687",
"objectType": "CLIENT_TYPE",
"lhs": "id",
"rhs": "zpn_client_type_branch_connector"
},
{
"id": "31470346",
"creationTime": "1683038920",
"modifiedBy": "72057594038040687",
"objectType": "CLIENT_TYPE",
"lhs": "id",
"rhs": "zpn_client_type_zapp"
}
]
},
{
"id": "31470347",
"modifiedTime": "1683038920",
"creationTime": "1683038920",
"modifiedBy": "72057594038040687",
"operator": "OR",
"negated": false,
"operands": [
{
"id": "31470348",
"creationTime": "1683038920",
"modifiedBy": "72057594038040687",
"objectType": "SCIM",
"lhs": "72057594037988776",
"rhs": "Jensen",
"name": "name.familyName",
"idpId": "72057594037961373"
},
{
"id": "31470349",
"creationTime": "1683038920",
"modifiedBy": "72057594038040687",
"objectType": "SCIM_GROUP",
"lhs": "72057594037961373",
"rhs": "20470",
"idpId": "72057594037961373"
}
]
}
],
"action": "REDIRECT_ALWAYS",
"serviceEdgeGroups": [
{
"id": "72057594038056014",
"modifiedTime": "1678798195",
"creationTime": "1634589741",
"modifiedBy": "72057594038606777",
"name": "dhareeshkumar_pb_grp",
"enabled": true,
"description": "Private broker group",
"versionProfileId": "0",
"overrideVersionProfile": false,
"isPublic": "FALSE",
"location": "California, USA",
"cityCountry": "Sanger, US",
"countryCode": "US",
"useInDrMode": false,
"graceDistanceEnabled": true,
"graceDistanceValue": "2500.0",
"graceDistanceValueUnit": "MILES"
}
],
"policySetId": "72057594038644503",
"defaultRule": false,
"restrictedEntity": false
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Updating a Redirection Policy Rule
To update the details of a redirection policy rule in the policy set:
- Get the `policySetId` captured in the [prerequisite API call](#prereq).
- Use the JSON payload from [Creating a New Redirection Rule](#create) and send a `PUT` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
-
Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the redirection policy set.
- `ruleId`: The ID of the redirection policy rule.
For example: `/mgmtconfig/v2/admin/customers/72057615512764416/policySet/72057615512764421/rule/72057615512764641`.
- [View the JSON payload](#putV2payload)
[]
`{
"conditions":[
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
"objectType":"COUNTRY_CODE",
"entryValues":[
{
"lhs":"<CountryCode>",
"rhs":true
}
]
}
]
}
],
"name":"PolicyName",
"description":"Description",
"action":"REDIRECT_ALWAYS",
"customMsg":"MsgString"
}`
- [View an example JSON payload](#putExamplePayloadv2)
[]
`{
"policySetId":"72057594038644503",
"conditions":[
{
"operands":[
{
"objectType":"COUNTRY_CODE",
"entryValues":[
{
"lhs":"US",
"rhs":true
}
]
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"CLIENT_TYPE",
"values":[
"zpn_client_type_machine_tunnel",
"zpn_client_type_edge_connector",
"zpn_client_type_zapp_partner",
"zpn_client_type_zapp",
"zpn_client_type_branch_connector"
]
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"SCIM",
"entryValues":[
{
"lhs":"72057594037988776",
"rhs":"Jensen"
}
]
},
{
"objectType":"SCIM_GROUP",
"entryValues":[
{
"lhs":"72057594037961373",
"rhs":20470
}
]
}
]
}
],
"name":"Example Redirection Policy",
"description":"Example description",
"action":"REDIRECT_ALWAYS",
"serviceEdgeGroups":[
{
"id":"72057594038665671",
"modifiedTime":"1689071571",
"creationTime":"1689071571",
"modifiedBy":"72057594038642792",
"name":"test_abc",
"MicrotenantName":"Default",
"enabled":true,
"versionProfileId":"72057594038660432",
"overrideVersionProfile":false,
"versionProfileName":"test_aglawe07",
"versionProfileVisibilityScope":"ALL",
"upgradeTimeInSecs":"66600",
"upgradeDay":"SUNDAY",
"isPublic":"FALSE",
"location":"Nagpur, Maharashtra, India",
"latitude":"21.1458004",
"longitude":"79.0881546",
"cityCountry":"Nagpur, IN",
"countryCode":"IN",
"useInDrMode":false,
"graceDistanceEnabled":true,
"graceDistanceValue":"2500.0",
"graceDistanceValueUnit":"MILES",
"restrictedEntity":false,
"level":2,
"parent":"Nagpur, Maharashtra, India",
"isLeaf":true
}
]
}`
A successful response returns code 204, meaning the redirection rule is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Rule Order
To update a rule order:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}/reorder/{newOrder}`.
- Provide the following parameters in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the policy set.
- `ruleId`: The ID of the redirection rule.
- `newOrder`: The new order of the rule.
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/policySet/72057594037938994/rule/72057615512764641/reorder/4`.
A successful response returns code 204, meaning the rule order is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting a Redirection Rule
To delete a redirection rule:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the redirection policy set captured in the [prerequisite API call](#prereq).
- `ruleId`: The ID of the rule you want to delete.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/policySet/72057615512764421/rule/72057615512764641`.
A successful response returns code 204, meaning the redirection rule is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details of All Client Types
To get details of all client types:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/clientTypes`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/clientTypes`.
- [View an example response](#GetClientTypesResponse)
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