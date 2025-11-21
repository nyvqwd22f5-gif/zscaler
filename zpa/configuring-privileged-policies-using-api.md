# Configuring Privileged Policies Using API
Source: https://help.zscaler.com/zpa/configuring-privileged-policies-using-api
PDF: https://help.zscaler.com/pdf/com/en/1485911.pdf

This article provides information on managing Zscaler Private Access (ZPA) Privileged Remote Access (PRA) policies using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
[]Prerequisite API Call
To get the `policySetId` by policy type:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/policyType/{policyType}`.
- Provide the `policyType`, the value for differentiating the policy types, in the request endpoint. The supported values are:
- `ACCESS_POLICY` or `GLOBAL_POLICY` (i.e., access policy)
- `TIMEOUT_POLICY` or `REAUTH_POLICY` (i.e., timeout policy)
- `BYPASS_POLICY` or `CLIENT_FORWARDING_POLICY` (i.e., client forwarding policy)
- `INSPECTION_POLICY` (i.e., AppProtection policy)
- `ISOLATION_POLICY` (i.e., Isolation policy)
- `CREDENTIAL_POLICY` (i.e., privileged credential policy)
- `CAPABILITIES_POLICY` (i.e., privileged capabilities policy)
- `REDIRECTION_POLICY` (i.e., redirection policy)
- `CLIENTLESS_SESSION_PROTECTION_POLICY` (i.e., Browser Protection policy)
- `PRIVILEGED_PORTAL_POLICY` (i.e., privileged portal policy)
To get a privileged credential policy set ID, provide the `CREDENTIAL_POLICY` policy type in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/policySet/policyType/CREDENTIAL_POLICY`.
- [View an example response](#ViewExample)
[]{
"id":"73186051597800563",
"creationTime":"1672160223",
"modifiedBy":"73186051597795329",
"name":"Credential_Policy",
"enabled":true,
"description":"Credential policies.",
"policyType":"8",
"sorted":true
}
To get a privileged capabilities policy set ID, provide the `CAPABILITIES_POLICY` policy type in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/policySet/policyType/CAPABILITIES_POLICY`.
- [View an example response](#ViewExample2)
[]{
"id":"217246660303026842",
"creationTime":"1670367805",
"modifiedBy":"217246660303026835",
"name":"Capabilities_Policy",
"enabled":true,
"description":"Capabilities Policies",
"policyType":"7",
"sorted":true
}
To get a privileged portals policy set ID, provide the `PRIVILEGED_PORTAL_POLICY` policy type in the request endpoint. For example:
`/mgmtconfig/v1/admin/customers/144118148382064640/policySet/policyType/PRIVILEGED_PORTAL_POLICY`.
- [View an example response](#getSetPortalPolicyResponse)
[]
`{
"id": "144118148382065763",
"modifiedTime": "1737667616",
"creationTime": "1737667616",
"modifiedBy": "144118148382065745",
"name": "Privilege_Portal_Policy",
"enabled": true,
"description": "Privilege Portal Policies",
"policyType": "11",
"sorted": true
}`
To get the privileged portals policy set ID for a privileged portal within a Microtenant, pass `?microtenantId=<microtenantId>` in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/144118148382064640/policySet/policyType/PRIVILEGED_PORTAL_POLICY?microtenantId=0144118148382065713`.
- [View an example response](#getPolicySetMicrotenant)
[]
`{
"id": "144118148382065766",
"modifiedTime": "1738793896",
"creationTime": "1738793896",
"modifiedBy": "144118148382065745",
"name": "Privilege_Portal_Policy-144118148382065713",
"enabled": true,
"description": "Privilege Portal Policies",
"policyType": "11",
"sorted": true,
"microtenantId": "144118148382065713"
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint `/mgmtconfig/v1/admin/customers/{customerId}/policySet/rules/policyType/{policyType}?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policyType`: The value for differentiating the policy types. The supported values are:
- `ACCESS_POLICY` or `GLOBAL_POLICY` (i.e., access policy)
- `TIMEOUT_POLICY` or `REAUTH_POLICY` (i.e., timeout policy)
- `BYPASS_POLICY` or `CLIENT_FORWARDING_POLICY` (i.e., client forwarding policy)
- `INSPECTION_POLICY` (i.e., AppProtection policy)
- `ISOLATION_POLICY` (i.e., Isolation policy)
- `CREDENTIAL_POLICY` (i.e., privileged credential policy)
- `CAPABILITIES_POLICY` (i.e., privileged capabilities policy)
- `REDIRECTION_POLICY` (i.e., redirection policy)
- `CLIENTLESS_SESSION_PROTECTION_POLICY` (i.e., Browser Protection policy)
- `PRIVILEGED_PORTAL_POLICY` (i.e., privileged portal policy)
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/policySet/rules/policyType/CREDENTIAL_POLICY?page=1&pagesize=2.`
- [View an example response](#paginatedResponse)
[]{
"totalPages":"2",
"list":[
{
"id":"145248664305009730",
"modifiedTime":"1671047708",
"creationTime":"1669145498",
"modifiedBy":"72057594038060431",
"name":"ssh-sample",
"ruleOrder":"1",
"priority":"4",
"policyType":"8",
"operator":"AND",
"conditions":[
{
"id":"21812856",
"modifiedTime":"1669145498",
"creationTime":"1669145498",
"modifiedBy":"72057594038060431",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"21812857",
"creationTime":"1669145498",
"modifiedBy":"72057594038060431",
"objectType":"CONSOLE",
"lhs":"id",
"rhs":"145248664305009340",
"name":"sample-site1-ssh"
}
]
}
],
"action":"INJECT_CREDENTIALS",
"credential":{
"id":"228",
"name":"ssh-sample-passwd"
},
"defaultRule":false
},
{
"id":"145248664305009659",
"modifiedTime":"1666652678",
"creationTime":"1666652678",
"modifiedBy":"72057594038060431",
"name":"rdp-test",
"ruleOrder":"2",
"priority":"1",
"policyType":"8",
"operator":"AND",
"conditions":[
{
"id":"21778372",
"modifiedTime":"1666652678",
"creationTime":"1666652678",
"modifiedBy":"72057594038060431",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"21778373",
"creationTime":"1666652678",
"modifiedBy":"72057594038060431",
"objectType":"CONSOLE",
"lhs":"id",
"rhs":"145248664305009526",
"name":"sample-site1-rdp.com"
}
]
}
],
"action":"INJECT_CREDENTIALS",
"credential":{
"id":"390",
"name":"rdp-sample-1"
},
"defaultRule":false
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting the Required Policy Criteria Details
Before creating a new privileged rule, you must get the following required details for the policy criteria:
- Application segment. To learn more, see [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api).
- Credential ID. To learn more, see [Configuring Privileged Credentials Using API](/zpa/configuring-privileged-credentials-using-api).
- IdP. To learn more, see [Obtaining IdP Configuration Details Using API](/zpa/obtaining-idp-configuration-details-using-api).
- SAML attribute. To learn more, see [Obtaining SAML Attribute Details Using API](/zpa/obtaining-saml-attribute-details-using-api).
- Segment group. To learn more, see [Configuring Segment Groups Using API](/zpa/configuring-segment-groups-using-api).
- SCIM attribute. To learn more, see [Obtaining SCIM Attribute Details Using API](/zpa/obtaining-scim-attribute-details-using-api).
- SCIM attribute value. To learn more, see [Obtaining SCIM Attribute Details Using API](/zpa/obtaining-scim-attribute-details-using-api).
- SCIM group. To learn more, see [Obtaining SCIM Group Details Using API](/zpa/obtaining-scim-group-details-using-api).
[]Creating a New Privileged Capabilities Rule
To create a new privileged capabilities rule:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in [Prerequisite API Calls](#Prereq).
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v2/admin/customers/289370814522851328/policySet/289370814522851333/rule?microtenantId=145260601092866116`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the entire JSON payload and provide the following parameters in the request body:
- `name`: The name of the rule.
- `action`: The rule action for the capabilities rule (`CHECK_CAPABILITIES`).
- `capabilities`: The type of capabilities for the privileged policy. This field must be passed in the request body when creating a privileged capabilities policy. The supported values are:
- `CLIPBOARD_COPY`: Indicates the PRA Clipboard Copy function.
- `CLIPBOARD_PASTE`: Indicates the PRA Clipboard Paste function.
- `FILE_UPLOAD`: Indicates the PRA File Transfer capabilities that enable the File Upload function.
- `FILE_DOWNLOAD`: Indicates the PRA File Transfer capabilities that enable the File Download function.
- `INSPECT_FILE_UPLOAD`: Inspects the file via ZIA sandbox (if you have set up the ZIA cloud and the [Integrations](/zpa/about-integrations) settings) and uploads the file following the inspection.
- `INSPECT_FILE_DOWNLOAD`: Inspects the file via ZIA sandbox (if you have set up the ZIA cloud and the [Integrations](/zpa/about-integrations) settings) and downloads the file following the inspection.
- `MONITOR_SESSION`: Indicates the PRA Monitoring Capabilities to enable the PRA Session Monitoring function.
- `RECORD_SESSION`: Indicates the PRA Session Recording capabilities to enable PRA Session Recording.
- `SHARE_SESSION`: Indicates the PRA Session Control and Monitoring capabilities to enable PRA Session Monitoring.
- [View the JSON payload](#postV2payloadCap)
[]
`{
"policySetId": "<policy set ID>",
"conditions": [
{
"operands": [
{
"objectType": "APP",
"values": [
"<application ID>"
]
}
]
}
],
"name": "<example policy rule name>",
"description": "<example description>",
"action": "CHECK_CAPABILITIES",
"privilegedCapabilities": {
"capabilities": [
"FILE_UPLOAD"
]
}
}`
- [View an example response](#postV2exampleCap)
[]
`{
"id":"145260601092866511",
"modifiedTime":"1704898052",
"creationTime":"1704898052",
"modifiedBy":"72057594038606761",
"name":"Scope A Policy-3",
"microtenantId":"145260601092866116",
"description":"Micro tenant A",
"ruleOrder":"5",
"priority":"1",
"policyType":"7",
"operator":"AND",
"conditions":[
{
"id":"25240454",
"modifiedTime":"1704898052",
"creationTime":"1704898052",
"modifiedBy":"72057594038606761",
"microtenantId":"145260601092866116",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"25240455",
"modifiedTime":"1704898052",
"creationTime":"1704898052",
"modifiedBy":"72057594038606761",
"microtenantId":"145260601092866116",
"objectType":"APP",
"lhs":"id",
"rhs":"145260601092866051",
"name":"Internal Application"
},
{
"id":"25240456",
"modifiedTime":"1704898052",
"creationTime":"1704898052",
"modifiedBy":"72057594038606761",
"microtenantId":"145260601092866116",
"objectType":"APP_GROUP",
"lhs":"id",
"rhs":"145260601092866489",
"name":"test-simha-sg"
}
]
},
{
"id":"25240457",
"modifiedTime":"1704898052",
"creationTime":"1704898052",
"modifiedBy":"72057594038606761",
"microtenantId":"145260601092866116",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"25240458",
"modifiedTime":"1704898052",
"creationTime":"1704898052",
"modifiedBy":"72057594038606761",
"microtenantId":"145260601092866116",
"objectType":"IDP",
"lhs":"id",
"rhs":"145260601092866079",
"name":"Contractors SSO"
}
]
}
],
"action":"CHECK_CAPABILITIES",
"policySetId":"145260601092866124",
"privilegedCapabilities":{
"capabilities":[
"FILE_UPLOAD",
"FILE_DOWNLOAD",
"INSPECT_FILE_UPLOAD",
"INSPECT_FILE_DOWNLOAD",
"CLIPBOARD_COPY",
"CLIPBOARD_PASTE",
"RECORD_SESSION",
"SHARE_SESSION",
"MONITOR_SESSION"
]
},
"defaultRule":false,
"defaultRuleName":"null-145260601092866116"
}`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Creating a New Privileged Credentials Rule
To create a new privileged credentials rule for a given policy set and for a given `customerId`:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in [Prerequisite API Calls](#Prereq).
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v2/admin/customers/289370814522851328/policySet/289370814522851333/rule?microtenantId=145260601092866116`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the entire JSON payload and provide the following parameters in the request body:
- `name`: The name of the rule.
- `action`: The rule action (`INJECT_CREDENTIALS`).
- `id`: The ID of the privileged credential. To learn more, see [Configuring Privileged Credentials Using API](/zpa/configuring-privileged-credentials-using-api).
- [View the JSON payload](#postV2payloadCred)
[]
`{
"policySetId": "72057594038624156",
"conditions": [
{
"operands": [
{
"objectType": "CONSOLE",
"values": [
"72057594038071247"
]
}
]
}
],
"name": "credential-policy",
"description": "Credential Policy",
"action": "INJECT_CREDENTIALS",
"disabled": "0",
"credential": {
"id": "47",
"name": "test"
}
}`
- [View an example response](#postv2exampleCred)
[]
`{
"id":"145260601092866557",
"modifiedTime":"1705987890",
"creationTime":"1705987890",
"modifiedBy":"72057594038606761",
"name":"Testing-user",
"scopeId":"145260601092866116",
"description":"testing",
"ruleOrder":"4",
"priority":"1",
"policyType":"8",
"operator":"AND",
"conditions":[
{
"id":"25243672",
"modifiedTime":"1705987890",
"creationTime":"1705987890",
"modifiedBy":"72057594038606761",
"scopeId":"145260601092866116",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"25243673",
"modifiedTime":"1705987890",
"creationTime":"1705987890",
"modifiedBy":"72057594038606761",
"scopeId":"145260601092866116",
"objectType":"CONSOLE",
"lhs":"id",
"rhs":"145260601092866269",
"name":"ExampleUser-approval-rdp.com"
}
]
}
],
"action":"INJECT_CREDENTIALS",
"credential":{
"id":"11534",
"name":".116 RDP Credentials"
},
"policySetId":"145260601092866125",
"privilegedCapabilities":{
},
"defaultRule":false,
"defaultRuleName":"null-145260601092866116"
}`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Creating a New Privileged Portals Rule
To create a new privileged portals policy rule for a given policy set and for a given `customerId`:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in [Prerequisite API Calls](#Prereq).
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v2/admin/customers/145255689797763072/policySet/145255689797875541/rule?microtenantId=0`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the entire JSON payload and provide the following parameters in the request body:
- `name`: The name of the rule.
- `action`: The rule action (`CHECK_PRIVILEGED_PORTAL_POLICIES`).
- The ID of the privileged portal. To learn more, see [Configuring Privileged Portals Using API](/zpa/configuring-privileged-portals-using-api).
- [View the JSON payload](#postPortalPayload)
[]
`{
"policySetId":"<policy Set ID>",
"conditions":[
{
"operands":[
{
"objectType":"IDP",
"values":[
"<IdP ID>"
]
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"PRIVILEGE_PORTAL",
"values":[
"<privileged portal ID>"
]
}
]
},
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
}
],
"name":"<name>",
"description":"<description>",
"disabled":0,
"action":"CHECK_PRIVILEGED_PORTAL_CAPABILITIES",
"privilegedPortalCapabilities":{
"capabilities":[
"DELETE_FILE",
"ACCESS_UNINSPECTED_FILE",
"UPLOAD_INSPECTED_SCAN",
"REQUEST_APPROVALS",
"REVIEW_APPROVALS"
]
}
}`
- [View the sample JSON payload](#postPortalSamplePayload)
[]
`{
"policySetId":"145255689797875541",
"conditions":[
{
"operands":[
{
"objectType":"IDP",
"values":[
"145255689797763136"
]
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"PRIVILEGE_PORTAL",
"values":[
"145255689797787884"
]
}
]
},
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
}
],
"name":"Example Privileged Portals Policy",
"description":"Example description",
"disabled":0,
"action":"CHECK_PRIVILEGED_PORTAL_CAPABILITIES",
"privilegedPortalCapabilities":{
"capabilities":[
"DELETE_FILE",
"ACCESS_UNINSPECTED_FILE",
"UPLOAD_INSPECTED_SCAN",
"REQUEST_APPROVALS",
"REVIEW_APPROVALS"
]
}
}`
- [View an example response](#examplePostPortalsResponse)
[]
`{
"id": "145255689797892137",
"modifiedTime": "1738787787",
"creationTime": "1738787787",
"modifiedBy": "72057594038006701",
"name": "Example Privileged Portals Policy",
"description": "Example description",
"ruleOrder": "1509",
"priority": "1",
"policyType": "11",
"operator": "AND",
"action": "CHECK_PRIVILEGED_PORTAL_CAPABILITIES",
"disabled": "0",
"extranetEnabled": false,
"policySetId": "145255689797875541",
"privilegedCapabilities": {},
"privilegedPortalCapabilities": {
"capabilities": [
"DELETE_FILE",
"UPLOAD_INSPECTED_SCAN",
"ACCESS_UNINSPECTED_FILE",
"REQUEST_APPROVALS",
"REVIEW_APPROVALS"
]
},
"conditions": [
{
"id": "40703255",
"modifiedTime": "1738787787",
"creationTime": "1738787787",
"modifiedBy": "72057594038006701",
"operator": "OR",
"negated": false,
"operands": [
{
"id": "40703256",
"modifiedTime": "1738787787",
"creationTime": "1738787787",
"modifiedBy": "72057594038006701",
"objectType": "IDP",
"lhs": "id",
"rhs": "145255689797763136",
"name": "Idp_saml"
}
]
},
{
"id": "40703257",
"modifiedTime": "1738787787",
"creationTime": "1738787787",
"modifiedBy": "72057594038006701",
"operator": "OR",
"negated": false,
"operands": [
{
"id": "40703258",
"modifiedTime": "1738787787",
"creationTime": "1738787787",
"modifiedBy": "72057594038006701",
"objectType": "PRIVILEGE_PORTAL",
"lhs": "id",
"rhs": "145255689797787884",
"name": "test_portal"
}
]
},
{
"id": "40703259",
"modifiedTime": "1738787787",
"creationTime": "1738787787",
"modifiedBy": "72057594038006701",
"operator": "OR",
"negated": false,
"operands": [
{
"id": "40703260",
"modifiedTime": "1738787787",
"creationTime": "1738787787",
"modifiedBy": "72057594038006701",
"objectType": "COUNTRY_CODE",
"lhs": "US",
"rhs": "true",
"name": "US"
}
]
}
],
"defaultRule": false
}`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting a Particular Privileged Rule Details
Before you get details for a particular privileged rule, you must get the `policySetId` captured in [Prerequisite API Calls](#Prereq).
To get details for a particular privileged rule:
- Send a `GET` request to to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/rules/policyType/{policyType}?microtenantId={microtenantId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in the [prerequisite API call](#Prereq).
- `ruleId`: The ID of the rule you created in either [Creating a New Privileged Capabilities Rule](#CreateCapabilities) or [Creating a New Privileged Credential Rule](#CreateCredentials).
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/policySet/rules/policyType/CREDENTIAL_POLICY?microtenantId=145260601092866116`.
- [View an example response](#Viewanexampleresponse3)
[]{
"totalPages":"1",
"totalCount":"0",
"list":[
{
"id":"145260601092866378",
"modifiedTime":"1699520116",
"creationTime":"1699520116",
"modifiedBy":"72057594038068982",
"name":"Scope A Ssh policy",
"microtenantId":"145260601092866116",
"ruleOrder":"1",
"priority":"2",
"policyType":"8",
"operator":"AND",
"conditions":[
{
"id":"25157962",
"modifiedTime":"1699520116",
"creationTime":"1699520116",
"modifiedBy":"72057594038068982",
"microtenantId":"145260601092866116",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"25157963",
"modifiedTime":"1699520116",
"creationTime":"1699520116",
"modifiedBy":"72057594038068982",
"microtenantId":"145260601092866116",
"objectType":"CONSOLE",
"lhs":"id",
"rhs":"145260601092866270",
"name":"ExampleUser-ssh.com"
},
{
"id":"25157964",
"modifiedTime":"1699520116",
"creationTime":"1699520116",
"modifiedBy":"72057594038068982",
"microtenantId":"145260601092866116",
"objectType":"CONSOLE",
"lhs":"id",
"rhs":"145260601092866374",
"name":"ExampleUser-ssh.com"
}
]
}
],
"action":"INJECT_CREDENTIALS",
"credential":{
"id":"11608",
"name":"Example User SSH"
},
"defaultRule":false,
"defaultRuleName":"null-145260601092866116",
"restrictedEntity":false
},
{
"id":"145260601092866507",
"modifiedTime":"1704878956",
"creationTime":"1704878956",
"modifiedBy":"72057594038073668",
"name":"Scope A RDP",
"microtenantId":"145260601092866116",
"ruleOrder":"2",
"priority":"1",
"policyType":"8",
"operator":"AND",
"conditions":[
{
"id":"25240409",
"modifiedTime":"1704878956",
"creationTime":"1704878956",
"modifiedBy":"72057594038073668",
"microtenantId":"145260601092866116",
"operator":"OR",
"negated":false,
"operands":[
{
"id":"25240410",
"modifiedTime":"1704878956",
"creationTime":"1704878956",
"modifiedBy":"72057594038073668",
"microtenantId":"145260601092866116",
"objectType":"CONSOLE",
"lhs":"id",
"rhs":"145260601092866269",
"name":"ExampleUser-approval-rdp.com"
}
]
}
],
"action":"INJECT_CREDENTIALS",
"credential":{
"id":"11534",
"name":".116 RDP Credentials"
},
"defaultRule":false,
"defaultRuleName":"null-145260601092866116",
"restrictedEntity":false
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Updating a Privileged Capabilities Policy Rule
To update the details of a privileged capabilities policy rule in the policy set:
- Get the `policySetId` captured in the [prerequisite API call](#Prereq).
- Use the entire JSON payload from [Creating a New Privileged Capabilities Rule](#CreateCapabilities) and send a `PUT` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}?microtenantId={microtenantId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in the [prerequisite API call](#Prereq).
- `ruleId`: The ID of the rule you created in [Creating a New Privileged Capabilities Rule](#CreateCapabilities).
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/policySet/289370814522851333/rule/289370814522851657?microtenantId=145260601092866116`.
- [View the JSON payload](#putV2payloadCap)
[]
`{
"policySetId": "<policy set ID>",
"id": "<rule ID>",
"conditions": [
{
"operands": [
{
"objectType": "APP",
"values": [
"<application ID>"
]
}
]
}
],
"name": "capabilities-policy",
"description": "Capabilities Policy",
"action": "CHECK_CAPABILITIES",
"privilegedCapabilities": {
"capabilities": [
"FILE_UPLOAD",
"FILE_DOWNLOAD"
]
}
}`
A successful response returns code 204, meaning the privileged credential rule is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Updating a Privileged Credentials Rule
To update the details of a privileged credentials policy rule in the policy set:
- Get the `policySetId` captured in the [prerequisite API call](#Prereq).
- Use the entire JSON payload from [Creating a New Privileged Credentials Rule](#CreateCredentials) and send a `PUT` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}?microtenantId={microtenantId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in the [prerequisite API call](#Prereq).
- `ruleId`: The ID of the rule you created in [Creating a New Privileged Credentials Rule](#CreateCredentials).
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v2/admin/customers/289370814522851328/policySet/289370814522851333/rule/289370814522851657?microtenantId=145260601092866116`.
- [View the JSON payload](#putV2payloadCred)
[]
`{
"policySetId": "<policy set ID>",
"id": "<rule ID>",
"conditions": [
{
"operands": [
{
"objectType": "CONSOLE",
"values": [
"<privileged console ID>"
]
}
]
}
],
"name": "<privileged console name>",
"description": "<example description>",
"action": "INJECT_CREDENTIALS",
"disabled": "0",
"credential": {
"id": "<privileged credential ID>",
"name": "<privileged credential name>"
}
}`
A successful response returns code 204, meaning the access rule is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Privileged Portals Rule
To update the details of a privileged portals policy rule in the policy set:
- Get the `policySetId` captured in the [prerequisite API call](#Prereq).
- Using the entire JSON payload from [Creating a New Privileged Portals Rule](#CreatePortalsPolicy), make the necessary updates, and then send a `PUT` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}?microtenantId={microtenantId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in the [prerequisite API call](#Prereq).
- `ruleId`: The ID of the rule you created in [Creating a New Privileged Portals Rule](#CreatePortalsPolicy).
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v2/admin/customers/145255689797763072/policySet/145255689797875541/rule/145255689797892137?microtenantId=0`.
- Ensure the following is passed in the request body:
- `name`: The name of the rule.
- `action`: The rule action (`CHECK_PRIVILEGED_PORTAL_POLICIES`).
- The ID of the privileged portal. To learn more, see [Configuring Privileged Portals Using API](/zpa/configuring-privileged-portals-using-api).
- [View the JSON payload](#postPortalsPayload)
[]
`{
"policySetId":"<policy Set ID>",
"conditions":[
{
"operands":[
{
"objectType":"IDP",
"values":[
"<IdP ID>"
]
}
],
"operator":"OR"
},
{
"operands":[
{
"objectType":"PRIVILEGE_PORTAL",
"values":[
"<privileged portal ID>"
]
}
]
},
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
}
],
"name":"<name>",
"description":"<description>",
"disabled":0,
"action":"CHECK_PRIVILEGED_PORTAL_CAPABILITIES",
"privilegedPortalCapabilities":{
"capabilities":[
"DELETE_FILE",
"ACCESS_UNINSPECTED_FILE",
"UPLOAD_INSPECTED_SANDBOX",
"UPLOAD_INSPECTED_SCAN",
"REQUEST_APPROVALS",
"REVIEW_APPROVALS"
]
}
}`
A successful response returns code 204, meaning the access rule is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Rule Order
To update a rule order:
- Send a PUT request to the following endpoint: `mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}/reorder/{newOrder}`.
- Provide the following parameters in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `policySetId`: The ID of the policy set.
- `ruleId`: The ID of the rule.
- `newOrder`: The new order of the rule.
For example: `mgmtconfig/v1/admin/customers/72057594037927936/policySet/72057594037938994/rule/72057615512764641/reorder/4`.
A successful response returns code 204, meaning the rule order is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
The ability to update the rule order for all rules in a policy set is also available. To learn more, see [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api#bulkUpdatingRuleOrder).
Deleting a Privileged Rule
To delete a privileged rule:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/policySet/{policySetId}/rule/{ruleId}`.
- Provide the following key-value pairs in the request body:
- `customerId:` The ZPA tenant ID of the customer.
- `policySetId`: The ID of the global policy set captured in the [prerequisite API call](#Prereq).
- `ruleId`: The ID of the rule you created in [Creating a New Privileged Rule](#Create).
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/policySet/72057615512764421/rule/72057615512764594`.
A successful response returns code 204, meaning the privileged policy rule is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
If a privileged policy is configured using Zscaler Deception, then the update and delete options are unavailable.
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
- Send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/platform`.
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
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the privileged policy use cases:
-
-
-
-
-
-
-
- [](/zpa/about-integrations)
- [](/zpa/about-integrations)
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
[](/zpa/about-microtenants)[](/zpa/about-api-keys)[](/zpa/configuring-microtenants-using-api)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| name | This is the name of the rule | Yes | String |
| description | This is the description of the rule | No | String |
| action | This is for providing the rule action | Yes | StringSupported values:`CHECK_CAPABILITIES`: The rule action to create a privileged capabilities policy.`INJECT_CREDENTIALS`: The rule action to create a privileged credentials policy.`CHECK_PRIVILEGED_PORTAL_POLICIES`: The rule action to create a privileged portals policy. |
| capabilties | Indicates the type of capabilities for the privileged policy | Yes | StringSupported values:`CLIPBOARD_COPY`: Indicates the PRA Clipboard Copy function.`CLIPBOARD_PASTE`: Indicates the PRA Clipboard Paste function.`FILE_UPLOAD`: Indicates the PRA File Transfer capabilities that enable the File Upload function.`FILE_DOWNLOAD`: Indicates the PRA File Transfer capabilities that enable the File Download function.`INSPECT_FILE_UPLOAD`: Inspects the file via ZIA sandbox (if you have set up the ZIA cloud and the Integrations settings) and uploads the file following the inspection.`INSPECT_FILE_DOWNLOAD`: Inspects the file via ZIA sandbox (if you have set up the ZIA cloud and the Integrations settings) and downloads the file following the inspection.`MONITOR_SESSION`: Indicates the PRA Monitoring Capabilities to enable the PRA Session Monitoring function.`RECORD_SESSION`: Indicates the PRA Session Recording capabilities to enable PRA Session Recording.`SHARE_SESSION`: Indicates the PRA Session Control and Monitoring capabilities to enable PRA Session Monitoring. |
| privilegedPortalCapabilities | Indicates the type of capabilities for the privileged portals policy | Yes | StringThe supported values are:`ACCESS_UNINSPECTED_FILE`: Allows uninspected files to be displayed in the PRA Portal.`DELETE_FILE`: Allows the deletion of files.`REQUEST_APPROVALS`: Allows privileged approval requests to be created in the PRA Portal.`REVIEW_APPROVALS`: Allow privileged approval requests to be reviewed, approved, and rejected.`UPLOAD_INSPECTED_SANDBOX`: Allows ZIA Sandbox integration inspection of the file.`UPLOAD_INSPECTED_SCAN`: Allows inspection via another format other than ZIA Sandbox. |
| customerMsg | This is for providing a customer message for the user | No | String |
| conditions | This is for providing the set of conditions for the policy | No | Array of operands |
| operands | This signifies the various policy criteria | No | Array of attributes (`objectType, lhs, rhs, name`) |
| objectType | This is for specifying the policy criteria | No | Supported values:`APP``APP_GROUP``CONSOLE``IDP``SAML``SCIM``SCIM_GROUP` |
| lhs | This signifies the key for the object type | No | String ID example: `"id"` |
| rhs | This denotes the value for the given object type. Its value depends upon the key. | No | For `APP`, `APP_GROUP`, `IDP`, `SAML`, `SCIM`, and `SCIM_GROUP`, the supported value is <`entity id>`. |
| operator | This denotes the operation type | No | Supported values: `AND`, `OR` |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the microtenantId is not passed in the request endpoint when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
For a comprehensive table of LHS and RHS values, see [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api#lhsandrhsvalues).