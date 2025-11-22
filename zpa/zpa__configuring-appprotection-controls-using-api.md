# Configuring AppProtection Controls Using API
Source: https://help.zscaler.com/zpa/configuring-appprotection-controls-using-api
PDF: https://help.zscaler.com/pdf/com/en/1485381.pdf

This article provides information on managing Zscaler Private Access (ZPA) AppProtection control use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Prerequisite API Calls
Before you can add a new custom control for a customer, you must get the following:
- [AppProtection control action types](#getControlActionTypes)
- [AppProtection control types](#getControlTypes)
- [AppProtection control severity types](#getControlSeverityTypes)
- [Supported HTTP Methods](#getSupportedHTTPMethods)
[]Getting AppProtection Control Action Types
To get AppProtection control action types:
- Send a `GET` request to the following endpoint: `mgmtconfig/v1/admin/customers/{customerId}/inspectionControls/actionTypes`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `mgmtconfig/v1/admin/customers/72057615512764416/inspectionControls/actionTypes`.
- [View an example response](#exampleResponse)
[][
"PASS",
"BLOCK",
"REDIRECT"
]
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting AppProtection Control Types
To get AppProtection control types:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionControls/controlTypes`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057615512764416/inspectionControls/controlTypes`.
- [View an example response](#exampleResponse2)
[][
"CUSTOM",
"PREDEFINED",
"ZSCALER"
]
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting AppProtection Control Severity Types
To get the AppProtection control severity types:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionControls/severityTypes`.
- Provide the customerId, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/inspectionControls/severityTypes`.
- [View an example response](#exampleResponse11)
[][
"CRITICAL",
"ERROR",
"WARNING",
"INFO"
]
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting the AppProtection Custom Control Types
To get the AppProtection custom control types, send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/inspectionControls/customControlTypes`.
- [View an example response](#viewExampleResponse9)
[]{
"REQUEST": [
"REQUEST_HEADERS",
"REQUEST_COOKIES",
"REQUEST_URI",
"REQUEST_METHOD",
"REQUEST_BODY",
"QUERY_STRING"
],
"RESPONSE": [
"RESPONSE_HEADERS",
"RESPONSE_BODY"
]
}
[]Getting the Supported HTTP Methods
To get the supported HTTP methods:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionControls/custom/httpMethods`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/inspectionControls/custom/httpMethods`.
- [View an example response](#exampleResponse7)
[][
"GET",
"HEAD",
"POST",
"OPTIONS",
"PUT",
"PATCH",
"DELETE",
"CHECKOUT",
"COPY",
"LOCK",
"MERGE",
"MKACTIVITY",
"MKCOL",
"MOVE",
"PROPFIND",
"PROPPATCH",
"UNLOCK",
"TRACE",
"CONNECT"
]
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Creating a New Custom Control
To create a new custom control for a customer:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionControls/custom`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057594038056530/inspectionControls/custom`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- Name of the custom control
- Control type of the custom control
- Control action of the custom control
- Rules of the custom control
- [View the JSON payload](#jsonPayload)
[]{
"action": "PASS",
"actionValue": "string",
"associatedInspectionProfileNames": [
{
"id": 0,
"name": "string"
}
],
"controlNumber": 0,
"controlRuleJson": "string",
"creationTime": 0,
"defaultAction": "PASS",
"defaultActionValue": "string",
"description": "string",
"id": 0,
"modifiedBy": 0,
"modifiedTime": 0,
"name": "string",
"paranoiaLevel": 0,
"rules": [
{
"conditions": [
{
"lhs": "SIZE",
"op": "RX",
"rhs": "string"
}
],
"names": [
"string"
],
"type": "REQUEST_HEADERS"
}
],
"severity": "CRITICAL",
"type": "REQUEST",
"version": "string"
}
- [Sample JSON payload](#sampleJsonPayload)
[]{
"type": "REQUEST",
"defaultAction": "BLOCK",
"paranoiaLevel": 1,
"severity": "CRITICAL",
"name": "custom control",
"description": "",
"rules": [
{
"conditions": [
{
"lhs": "SIZE",
"op": "GE",
"rhs": "1000"
}
],
"names": [example],
"type": "REQUEST_BODY"
},
{
"conditions": [
{
"lhs": "VALUE",
"op": "RX",
"rhs": "POST"
}
],
"names": [test, demo, inspection],
"type": "REQUEST_METHOD"
}
]
}
- [View the minimum criteria JSON payload](#viewMinimumCriteriaJSON)
[]{
"type": "string",
"defaultAction": "string",
"severity": "string",
"name": "string",
"rules": [{
"conditions": [{
"lhs": "string",
"op": "string",
"rhs": "string"
}],
"names": ["string"],
"type": "string"
}]
}
- [View an example response](#exampleResponse4)
[]{
"id": "72057594038078996",
"creationTime": "1652715710",
"modifiedBy": "72057594038056530",
"name": "Demo_custom control",
"severity": "CRITICAL",
"controlNumber": "5500004",
"version": "1.0",
"paranoiaLevel": "1",
"defaultAction": "BLOCK",
"type": "REQUEST",
"controlRuleJson": "[{\"type\":\"REQUEST_BODY\",\"conditions\":[{\"lhs\":\"SIZE\",\"op\":\"GE\",\"rhs\":\"1000\"}]},{\"type\":\"REQUEST_METHOD\",\"conditions\":[{\"lhs\":\"VALUE\",\"op\":\"RX\",\"rhs\":\"POST\"}]}]",
"rules": [
{
"type": "REQUEST_BODY",
"conditions": [
{
"lhs": "SIZE",
"op": "GE",
"rhs": "1000"
}
]
},
{
"type": "REQUEST_METHOD",
"conditions": [
{
"lhs": "VALUE",
"op": "RX",
"rhs": "POST"
}
]
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the AppProtection control criteria you want to include in the JSON payload. Refer to the [Adding Field Descriptions](#fieldDescriptions) section for supported values.
To create a custom control and specify the negation of a specific request method:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionControls/custom`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057594038056530/inspectionControls/custom`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- Name of the custom control
- Control type of the custom control
- Control action of the custom control
- Rules of the custom control
- [View the JSON payload](#postCustomControlNegationPayload)
[]
`{
"action": "PASS",
"actionValue": "string",
"associatedInspectionProfileNames": [
{
"id": 0,
"name": "string"
}
],
"controlNumber": 0,
"controlRuleJson": "string",
"creationTime": 0,
"defaultAction": "PASS",
"defaultActionValue": "string",
"description": "string",
"id": 0,
"modifiedBy": 0,
"modifiedTime": 0,
"name": "string",
"paranoiaLevel": 0,
"rules": [
{
"conditions": [
{
"lhs": "VALUE",
"op": "NOT_RX",
"rhs": "string"
}
],
"names": [
"string"
],
"type": "REQUEST_METHOD"
}
],
"severity": "CRITICAL",
"type": "REQUEST",
"version": "string"
}`
- [Sample JSON payload](#samplePostPayloadCustomControlNegation)
[]
`{
"type":"REQUEST",
"defaultAction":"PASS",
"paranoiaLevel":1,
"severity":"CRITICAL",
"name":"Test Negation",
"description":"",
"rules":[
{
"conditions":[
{
"lhs":"VALUE",
"op":"NOT_RX",
"rhs":"GET"
}
],
"names":[
],
"type":"REQUEST_METHOD"
}
]
}`
- [View an example response](#examplePostCustomControlNegationResponse)
[]
`{
"id":"145256180497790235",
"modifiedTime":"1751395925",
"creationTime":"1751395925",
"modifiedBy":"72057594038040687",
"name":"Test Negation",
"severity":"CRITICAL",
"controlNumber":"4500005",
"version":"1.0",
"paranoiaLevel":"1",
"defaultAction":"PASS",
"protocolType":"HTTP",
"type":"REQUEST",
"controlRuleJson":"[{\"type\":\"REQUEST_METHOD\",\"conditions\":[{\"lhs\":\"VALUE\",\"op\":\"NOT_RX\",\"rhs\":\"GET\"}]}]",
"rules":[
{
"type":"REQUEST_METHOD",
"conditions":[
{
"lhs":"VALUE",
"op":"NOT_RX",
"rhs":"GET"
}
]
}
]
}`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the AppProtection control use cases:
-
-
-
-
-
-
[](/zpa/configuring-appprotection-profiles#paranoia-execution)
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
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| action | The performed action | Yes | Supported values:`PASS``BLOCK``REDIRECT` |
| actionValue | Denotes the action | Yes | Any string |
| associatedInspectionProfileName | Name of the AppProtection profile | No | String |
| controlRuleJson | The control rule in JSON format that has the conditions and type of control for the AppProtection control | No | Any string |
| defaultAction | The performed action | Yes | Supported values:`PASS``BLOCK``REDIRECT` |
| defaultActionValue | This is used to provide the redirect URL if the default action is set to `REDIRECT` | No | String |
| description | Description of the custom control | No | String |
| name | Name of the custom control | Yes | String |
| panaoiaLevel | The OWASP Predefined Paranoia Level. To learn more, see Configuring AppProtection Profiles. | Yes | IntegerRange: [1-4], inclusive |
| rules | Rules of the custom controls applied as conditions | Yes | JSON |
| rules.type | Type value for the rules | Yes | StringIf `type` is set to `REQUEST`, users can only select one of the following values for `rules.type`:`REQUEST_HEADERS``REQUEST_COOKIES``REQUEST_URI``REQUEST_METHOD``QUERY_STRING`If `type` is set to `RESPONSE`, users can only select one of the following values for `rule.type`:`RESPONSE_HEADERS``RESPONSE_BODY` |
| rules.names | Name of the rules. If `rules.type` is set to `REQUEST_HEADERS`, `REQUEST_COOKIES`, or `RESPONSE_HEADERS`, the `rules.names` field is required. | Yes | List of string values or a single string |
| severity | Severity of the control number | Yes | Supported values:`CRITICAL``ERROR``WARNING``INFO` |
| type | Rules to be applied to the request or response type | Yes | Supported values:`REQUEST``RESPONSE` |
| conditions.lhs | Signifies the key for the object type | Yes | StringSupported values:`SIZE``VALUE` |
| conditions.rhs | Denotes the value for the given object type. Its value depends on the key. | Yes | StringIf `rules.type` is set to `REQUEST_METHOD`, the `conditions.rhs` field must have one of the following values:`GET``HEAD``POST``OPTIONS``PUT``DELETE``TRACE` |
| conditions.op | Denotes the operation type. | Yes | StringIf `lhs` is set to `SIZE`, then the user can pass one of the following:`EQ`: Equals`LE`: Less than or equal to`GE`: Greater than or equal toIf the `lhs` is set to `VALUE`, then the user can pass one of the following:`CONTAINS`: Denotes the control type that contains the specified `rhs` value.`STARTS_WITH`: Denotes the control type that starts with the specified `rhs` value.`ENDS_WITH`: Denotes the control type that ends with the specified `rhs` value.`RX`: Denotes the control type with the regex with the specified `rhs` value.`EXISTS`: Denotes the presence of the control type in the custom control. The `EXISTS` value for the `OP` field is only supported for the following control types (i.e., `rules.type` must be one of the following):`REQUEST_HEADERS``REQUEST_COOKIES``QUERY_STRING``RESPONSE_HEADERS``NOT_RX`: Denotes the control type that does not match the regex.`NOT_CONTAINS`: Denotes the control type that does not contain the specified `rhs` value.`NOT_STARTS_WITH`: Denotes the control type that does not start with the specified `rhs` value.`NOT_ENDS_WITH`: Denotes the control type that does not end with the specified `rhs` value.`NOT_EXISTS`: Denotes the absence of the control type. The `NOT_EXISTS` value for the `OP` field is only supported for the following control types (i.e., `rules.type` must be one of the following):`REQUEST_HEADERS``REQUEST_COOKIES``QUERY_STRING``RESPONSE_HEADERS` |
[]Getting All Custom Controls
To get all custom controls:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionControls/custom`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057615512764416/inspectionControls/custom`.
- [View an example response](#exampleResponse3)
[]{
"totalPages": "1",
"list": [
{
"id": "73170362082263045",
"modifiedTime": "1638465732",
"creationTime": "1638465437",
"modifiedBy": "72057594038056531",
"name": "Test name One",
"description": "Default description",
"severity": "CRITICAL",
"controlNumber": "4500000",
"version": "1.0",
"paranoiaLevel": "1",
"defaultAction": "PASS",
"defaultActionValue": "REDIRECT",
"type": "REQUEST",
"controlRuleJson": "[{\"type\":\"REQUEST_HEADERS\",\"names\":[\"Sample text\"],\"conditions\":[{\"lhs\":\"SIZE\",\"op\":\"EQ\",\"rhs\":\"300\"}]}]"
},
{
"id": "73170362082263047",
"modifiedTime": "1638465699",
"creationTime": "1638465611",
"modifiedBy": "72057594038056531",
"name": "Test name Three",
"description": "Default description",
"severity": "CRITICAL",
"controlNumber": "4500002",
"version": "1.0",
"paranoiaLevel": "1",
"defaultAction": "PASS",
"defaultActionValue": "REDIRECT",
"type": "REQUEST",
"controlRuleJson": "[{\"type\":\"REQUEST_HEADERS\",\"names\":[\"Sample text\"],\"conditions\":[{\"lhs\":\"SIZE\",\"op\":\"EQ\",\"rhs\":\"300\"}]}]"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionControls/custom?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/inspectionControls/custom?page=1&pagesize=2`.
- [View an example response](#paginatedResponse)
[]{
"totalPages": "100",
"list": [
{
"id": "72057594038037607",
"modifiedTime": "1628532877",
"creationTime": "1622144195",
"modifiedBy": "72057594037973665",
"name": "custom control 1",
"description": "desc",
"severity": "INFO",
"controlNumber": "80000",
"version": "1.0",
"paranoiaLevel": "1",
"defaultAction": "PASS",
"associatedInspectionProfileNames": [
{
"id": "72057594038073206",
"name": "aProfileWithWebsocketControls"
},
{
"id": "72057594038049518",
"name": "TestProfileWithWebsocketControls"
},
],
"type": "REQUEST",
"controlRuleJson": "[{\"type\":\"REQUEST_HEADERS\",\"names\":[\"Sample Text, \",\"Sample Text\"],\"conditions\":[{\"lhs\":\"SIZE\",\"op\":\"EQ\",\"rhs\":\"4\"},{\"lhs\":\"VALUE\",\"op\":\"RX\",\"rhs\":\"dfgdfg\"}]},{\"type\":\"REQUEST_URI\",\"conditions\":[{\"lhs\":\"VALUE\",\"op\":\"RX\",\"rhs\":\"fdg\"}]},{\"type\":\"QUERY_STRING\",\"conditions\":[{\"lhs\":\"VALUE\",\"op\":\"RX\",\"rhs\":\"sdgfs\"}]},{\"type\":\"REQUEST_COOKIES\",\"names\":[\"gsds\"],\"conditions\":[{\"lhs\":\"SIZE\",\"op\":\"EQ\",\"rhs\":\"4\"},{\"lhs\":\"VALUE\",\"op\":\"RX\",\"rhs\":\"dfg\"}]},{\"type\":\"REQUEST_BODY\",\"conditions\":[{\"lhs\":\"VALUE\",\"op\":\"RX\",\"rhs\":\"sdfsd\"}]},{\"type\":\"REQUEST_METHOD\",\"conditions\":[{\"lhs\":\"VALUE\",\"op\":\"RX\",\"rhs\":\"DELETE\"}]}]"
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting a Custom Control by ID
To get a custom control by ID:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionControls/custom/{id}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the AppProtection control.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/inspectionControls/custom/72057594038037608`.
- [View an example response](#exampleResponse5)
[]{
"id": "72057594038037608",
"modifiedTime": "1628508820",
"creationTime": "1622144273",
"modifiedBy": "72057594037973665",
"name": "Test cc2",
"severity": "ERROR",
"controlNumber": "80001",
"version": "1.0",
"paranoiaLevel": "1",
"defaultAction": "REDIRECT",
"defaultActionValue": "http://www.toggle1.com",
"associatedInspectionProfileNames": [
{
"id": "72057594038043697",
"name": "testInspectionProfile"
},
{
"id": "72057594038047624",
"name": "testInspectionProfile2"
}
],
"type": "RESPONSE",
"controlRuleJson": "[{\"type\":\"RESPONSE_HEADERS\",\"names\":[\"ds\"],\"conditions\":[{\"lhs\":\"SIZE\",\"op\":\"EQ\",\"rhs\":\"300\"}]},{\"type\":\"RESPONSE_BODY\",\"conditions\":[{\"lhs\":\"VALUE\",\"op\":\"RX\",\"rhs\":\"test\"}]}]"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Custom Control
To update a custom control:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionControls/custom/{id}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the AppProtection control.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/inspectionControls/custom/72057594038037608`.
A successful response returns code 204, meaning the custom control is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting a Custom Control
To delete a custom control:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionControls/custom/{id}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the AppProtection control.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/inspectionControls/custom/72057594038037608`.
A successful response returns code 204, meaning the custom control is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Associated Profile Details by Control ID
To get the name and ID of the associated profile by control ID:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionControls/custom/{id}/profiles`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the AppProtection control.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/inspectionControls/custom/217246660303025057/profiles`.
- [View an example response](#exampleResponse6)
[][
{
"id": "72057594038073206",
"name": "aProfileWithWebsocketControls"
},
{
"id": "72057594038049518",
"name": "testProfileWithWebSocketControls"
},
]
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting All Predefined AppProtection Controls
To get all predefined AppProtection controls:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionControls/predefined`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer
- `version`: The predefined-control version. To learn more, see [Getting All Predefined AppProtection Control Versions](#getPredefinedControlVersions).
- Include the mandatory default predefined controls in the request endpoint with the search string.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/inspectionControls/predefined?search=controlGroup%20eq%20Preprocessors&version=OWASP_CRS%2f3.3.0`.
The preprocessor is the group for the default controls.
- [View an example response](#exampleResponse8)
[][
{
"controlGroup": "Preprocessors",
"predefinedInspectionControls": [
{
"id": "72057594037930391",
"modifiedTime": "1631459708",
"creationTime": "1631459708",
"name": "Internal error flagged",
"description": "Internal error flagged",
"severity": "CRITICAL",
"controlNumber": "200005",
"version": "OWASP_CRS/3.3.0",
"paranoiaLevel": "1",
"defaultAction": "BLOCK",
"controlGroup": "Preprocessors"
},
{
"id": "72057594037930409",
"modifiedTime": "1632525142",
"creationTime": "1632525142",
"name": "Method is not allowed by policy",
"description": "This rule check if the Method is allowed by policy",
"severity": "CRITICAL",
"controlNumber": "911100",
"version": "OWASP_CRS/3.3.0",
"paranoiaLevel": "1",
"defaultAction": "BLOCK",
"controlGroup": "Preprocessors"
},
{
"id": "72057594037929947",
"modifiedTime": "1621936649",
"creationTime": "1621936649",
"name": "Invalid HTTP Request Line",
"description": "Validate request line against the format specified in the HTTP RFC.",
"severity": "WARNING",
"controlNumber": "920100",
"version": "OWASP_CRS/3.3.0",
"paranoiaLevel": "1",
"defaultAction": "BLOCK",
"controlGroup": "Preprocessors"
},
{
"id": "72057594037929950",
"modifiedTime": "1621936649",
"creationTime": "1621936649",
"name": "Content-Length HTTP header is not numeric",
"description": "Accept only digits in content length.",
"severity": "CRITICAL",
"controlNumber": "920160",
"version": "OWASP_CRS/3.3.0",
"paranoiaLevel": "1",
"defaultAction": "BLOCK",
"controlGroup": "Preprocessors"
},
{
"id": "72057594037929954",
"modifiedTime": "1621936649",
"creationTime": "1621936649",
"name": "Content-Length and Transfer-Encoding headers present",
"description": "This rule blocks if both Content-Length and Transfer-Encoding headers present.",
"severity": "WARNING",
"controlNumber": "920181",
"version": "OWASP_CRS/3.3.0",
"paranoiaLevel": "1",
"defaultAction": "BLOCK",
"controlGroup": "Preprocessors"
},
{
"id": "72057594037929988",
"modifiedTime": "1621936649",
"creationTime": "1621936649",
"name": "HTTP protocol version is not allowed by policy",
"description": "This rule checks for HTTP Protocol version is from allowed versions or not.",
"severity": "CRITICAL",
"controlNumber": "920430",
"version": "OWASP_CRS/3.3.0",
"paranoiaLevel": "1",
"defaultAction": "BLOCK",
"controlGroup": "Preprocessors"
}
],
"defaultGroup": true
}
]
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting a Predefined Control by ID
To get a predefined AppProtection control by ID:
- Send a `GET` request to the following endpoint : `/mgmtconfig/v1/admin/customers/{customerId}/inspectionControls/predefined/{id}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the AppProtection control.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/inspectionControls/predefined/72057594038049511`.
- [View an example response](#exampleResponse9)
[]{
"id": "72057594038049511",
"modifiedTime": "1629743139",
"creationTime": "1629743139",
"name": "Failed to parse request body",
"description": "Failed to parse request body",
"severity": "CRITICAL",
"controlNumber": "200002",
"version": "OWASP_CRS/3.3.0",
"paranoiaLevel": "1",
"defaultAction": "BLOCK",
"controlGroup": "Protocol Issues"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting All Predefined AppProtection Control Versions
To get all predefined AppProtection control versions:
- Send a `GET` request to the following endpoint : `/mgmtconfig/v1/admin/customers/{customerId}/inspectionControls/predefined/versions`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/inspectionControls/predefined/versions`.
- [View an example response](#exampleResponse10)
[][
"OWASP_CRS/4.8.0",
"OWASP_CRS/3.3.5",
"OWASP_CRS/3.3.0"
]
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