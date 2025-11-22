# Configuring AppProtection Profiles Using API
Source: https://help.zscaler.com/zpa/configuring-appprotection-profiles-using-api
PDF: https://help.zscaler.com/pdf/com/en/1485386.pdf

This article provides information on managing Zscaler Private Access (ZPA) [AppProtection profile](/zpa/about-appprotection-profiles) use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
[]Prerequisite API Calls
Before creating a new AppProtection profile, you must get the following required details:
- All predefined AppProtection controls. To learn more, see [Configuring AppProtection Controls Using API](/zpa/configuring-inspection-controls-using-api#getAllPredefinedInspectionControls).
- All predefined AppProtection control versions. To learn more, see [Configuring AppProtection Controls Using API](/zpa/configuring-inspection-controls-using-api#getPredefinedControlVersions).
Creating a New AppProtection Profile
To create a new AppProtection profile:
- Send a `POST` request to the following endpoint in the inspection-profile-controller: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionProfile`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057594038056531/inspectionProfile`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- Name of the application
- Paranoia level: An integer which refers to the associated paranoia level. The supported values are 1, 2, 3, or 4.
- Ensure the required `predefinedControls` and `predefinedControlsVersion` fields are included in the JSON payload. These fields are highlighted in red. All the mandatory [predefined controls](/zpa/inspection-control-use-cases#getAllPredefinedInspectionControls) must be passed. To learn more, see [Prerequisite API Calls](#prereq).
- [View the entire JSON payload](#jsonPayload)
[]{
"controlsInfo": [{
"controlType": "CUSTOM",
"count": 0
}],
"creationTime": 0,
"customControls": [{
"action": "PASS",
"actionValue": "string",
"associatedInspectionProfileNames": [{
"id": 0,
"name": "string"
}],
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
"rules": [{
"conditions": [{
"lhs": "SIZE",
"op": "RX",
"rhs": "string"
}],
"names": [
"string"
],
"type": "REQUEST_HEADERS"
}],
"severity": "CRITICAL",
"type": "REQUEST",
"version": "string"
}],
"description": "string",
"globalControlActions": [
"string"
],
"id": 0,
"incarnationNumber": 0,
"modifiedBy": 0,
"modifiedTime": 0,
"name": "string",
"paranoiaLevel": 0,
"predefinedControls": [{
"action": "PASS",
"actionValue": "string",
"associatedInspectionProfileNames": [{
"id": 0,
"name": "string"
}],
"attachment": "string",
"controlGroup": "string",
"controlNumber": 0,
"creationTime": 0,
"defaultAction": "PASS",
"defaultActionValue": "string",
"description": "string",
"id": 0,
"modifiedBy": 0,
"modifiedTime": 0,
"name": "string",
"paranoiaLevel": 0,
"severity": "CRITICAL",
"version": "string"
}],
"predefinedControlsVersion": "string"
}
- [View the minimum criteria JSON payload](#minimumCriteriaJSONpayload)
[]{
"name": "string",
"paranoiaLevel": "string",
"predefinedControlsVersion": "string",
"predefinedControls": [
{
"id": "string",
"action": "string",
"actionValue": "string"
}
]
}
- [View an example response](#exampleResponse3)
[]{
"id": "73170362082263059",
"modifiedTime": "1652719814",
"creationTime": "1652719814",
"modifiedBy": "72057594038056531",
"name": "Example AppProtection Profile",
"description": "desc",
"paranoiaLevel": "1",
"globalControlActions": [
"PREDEFINED:NONE",
"CUSTOM:NONE",
"OVERRIDE_ACTION:NONE"
],
"predefinedControlsVersion": "OWASP_CRS/3.3.0",
"predefinedControls": [
{
"id": "72057594038049511",
"action": "BLOCK"
},
{
"id": "72057594038049512",
"action": "BLOCK"
},
{
"id": "72057594038049513",
"action": "BLOCK"
},
{
"id": "72057594038049514",
"action": "BLOCK"
},
{
"id": "72057594038050059",
"action": "BLOCK"
},
{
"id": "72057594038010025",
"action": "BLOCK"
},
{
"id": "72057594038010028",
"action": "BLOCK"
},
{
"id": "72057594038010032",
"action": "BLOCK"
},
{
"id": "72057594038010066",
"action": "BLOCK"
}
],
"customControls": [
{
"id": "73170362082263045",
"action": "PASS"
}
],
"incarnationNumber": "1",
"commonGlobalOverrideActionsConfig": {
"IS_OVERRIDE_ACTION_NONE": "TRUE"
}
}
You choose the AppProtection profile criteria you want to include in the JSON payload. Refer to the [Adding Field Descriptions](#fieldDescriptions) section for supported values.
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Adding Field Descriptions
The following table includes descriptions of available fields you may use for the AppProtection profile use cases:
[](/zpa/configuring-appprotection-profiles)
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
| name | Name of the application | Yes | Any string |
| description | Description of the application | No | Any string |
| paranoiaLevel | The OWASP Predefined Paranoia Level. To learn more, see Configuring AppProtection Profiles. | Yes | IntegerRange: [1-4], inclusive |
| associatedInspectionProfileName | Name of the AppProtection profile | No | String |
| controlNumber | Domain name of the AppProtection application | No | Integer |
| predefinedControlsVersion | Protocol for the AppProtection application | Yes | String |
| predefinedControls | The predefined controls | Yes | JSON |
| predefinedControls.id | ID of the predefined control | Yes | String |
| predefinedControls.action | The action of the predefined control | Yes | Supported values:`PASS``BLOCK``REDIRECT` |
| predefinedControls.actionValue | Value for the predefined controls action. This field is only required if the `action` is set to `REDIRECT`. | Yes | String |
| InspectionPredefinedControl.attachment | Control attachment | No | String |
| InspectionPredefinedControl.controlGroup | Control group | No | String |
| customControls.type | Types for custom controls | No | String |
| customControls.controlRuleJson | Custom controls string in JSON format | No | String |
| customControls.rules.type | Request headers for the custom controls | No | Supported values:`REQUEST_HEADERS``REQUEST_URI``QUERY_STRING``REQUEST_COOKIES``REQUEST_METHOD``REQUEST_BODY``RESPONSE_HEADER``RESPONSE_BODY` |
| customControls.rules.names | Name types for the custom controls | No | String |
| customControls.rules.conditions.lhs | Signifies the key for the object type | No | String |
| customControls.rules.conditions.rhs | Denotes the value for the given object type. Its value depends upon the key. | No | String |
| customControls.rules.conditions.op | Denotes the operation type | No | String |
| controlsInfo.controlType | Control types | No | String. Supported values:`CUSTOM``PREDEFINED``ZSCALER` |
| controlsInfo.count | Control information counts | No | Long |
[]Getting Details for All AppProtection Profiles
To get all AppProtection profiles:
- Send a `GET` request to the following endpoint in the inspection-profile-controller: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionProfile`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/inspectionProfile`.
- [View an example response](#exampleResponse)
[]{
"totalPages": "9",
"list": [
{
"id": "217246660303025210",
"modifiedTime": "1627001532",
"creationTime": "1627001532",
"modifiedBy": "72057594037994933",
"name": "test_local",
"description": "inspect simple http app ",
"paranoiaLevel": "4",
"globalControlActions": [
"PREDEFINED:PASS",
"CUSTOM:NONE",
"OVERRIDE_ACTION:COMMON"
],
"controlsInfo": [
{
"controlType": "PREDEFINED",
"count": "50"
}
],
"incarnationNumber": "0",
"commonGlobalOverrideActionsConfig": {
"PREDEF_CNTRL_GLOBAL_ACTION": "PASS",
"IS_OVERRIDE_ACTION_COMMON": "TRUE"
}
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionProfile?page=1&pagesize=20` .
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/inspectionProfile?page=1&pagesize=2`.
- [View an example response](#paginatedResponse)
[]{
"totalPages": "50",
"list": [
{
"id": "72057594038049518",
"modifiedTime": "1648567589",
"creationTime": "1629746592",
"modifiedBy": "72057594037973665",
"name": "test",
"description": "example description",
"paranoiaLevel": "2",
"globalControlActions": [
"PREDEFINED:NONE",
"CUSTOM:NONE",
"OVERRIDE_ACTION:SPECIFIC"
],
"controlsInfo": [
{
"controlType": "CUSTOM",
"count": "1"
},
{
"controlType": "PREDEFINED",
"count": "207"
}
],
"incarnationNumber": "48",
"commonGlobalOverrideActionsConfig": {
"IS_OVERRIDE_ACTION_SPECIFIC": "TRUE"
}
},
{
"id": "72057594038071229",
"modifiedTime": "1645227522",
"creationTime": "1645227522",
"modifiedBy": "72057594038006701",
"name": "test2",
"paranoiaLevel": "1",
"globalControlActions": [
"PREDEFINED:PASS",
"CUSTOM:PASS",
"OVERRIDE_ACTION:COMMON"
],
"controlsInfo": [
{
"controlType": "CUSTOM",
"count": "2"
},
{
"controlType": "PREDEFINED",
"count": "11"
}
],
"incarnationNumber": "1",
"commonGlobalOverrideActionsConfig": {
"PREDEF_CNTRL_GLOBAL_ACTION": "PASS",
"CUSTOM_CNTRL_GLOBAL_ACTION": "PASS",
"IS_OVERRIDE_ACTION_COMMON": "TRUE"
}
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports a search option to search by features and fields. To search by features and fields:
- Send a GET request to the following endpoint: `/mgmtconfig/v1/admin/customers/73186051597795328/inspectionProfile&search={searchString}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid search string values. The search string values are in the format `fieldName operator fieldValue`. Only search string values that correspond to the values for valid fields and filters are supported. For example, the string `paranoiaLevel%20EQ%201` is supported for the **Paranoia Level** filter, using the **Equals **(`EQ`) operator, for the filter value `1`.
For example: `/mgmtconfig/v1/admin/customers/73186051597795328/inspectionProfile&search=paranoiaLevel%20EQ%201`.
- [View an example response](#gettingDetailsAllAppProtectionSearch)
[]{
"totalPages": "71",
"totalCount": "71",
"list": [
{
"id": "72057594038071229",
"modifiedTime": "1669379350",
"creationTime": "1645227522",
"modifiedBy": "72057594037940740",
"name": "aaThreatlabzProfile",
"description": "to test in-progress controls",
"paranoiaLevel": "1",
"globalControlActions": [
"PREDEFINED:PASS",
"CUSTOM:PASS",
"WEBSOCKET:BLOCK",
"THREATLABZ:NONE",
"OVERRIDE_ACTION:COMMON"
],
"controlsInfo": [
{
"controlType": "CUSTOM",
"count": "2"
},
{
"controlType": "PREDEFINED",
"count": "60"
},
{
"controlType": "WEBSOCKET_CUSTOM",
"count": "1"
},
{
"controlType": "WEBSOCKET_PREDEFINED",
"count": "4"
}
],
"incarnationNumber": "53"
}
]
}
If you use the ZPA API PortaI or the [Reference Guide](/zpa/zpa-api/api-developer-reference-guide/reference-guide) to make your API calls, the search field string does not require any characters. For example, `paranoiaLevel%20EQ%201` is `paranoiaLevel EQ 1`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of the AppProtection Profile
To get details of the AppProtection profile:
- Send a `GET` request to the following endpoint in the inspection-profile-controller: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionProfile/{inspectionProfileId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `inspectionProfileId`: The unique identifier of the inspection profile.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/inspectionProfile/217246660303025210`.
- [View an example response](#exampleResponse2)
[]{
"id": "72057594038049518",
"modifiedTime": "1648567589",
"creationTime": "1629746592",
"modifiedBy": "72057594037973665",
"name": "sample name",
"description": "sample description",
"paranoiaLevel": "2",
"globalControlActions": [
"PREDEFINED:NONE",
"CUSTOM:NONE",
"OVERRIDE_ACTION:SPECIFIC"
],
"predefinedControls": [
{
"id": "72057594038010284",
"modifiedTime": "1619611688",
"creationTime": "1619611688",
"name": "SQL Injection Attack Data fetch attempt",
"description": "This rule detects SQL Injection Attack by Data fetch attempt.",
"severity": "CRITICAL",
"controlNumber": "942480",
"version": "OWASP_CRS/3.3.0",
"paranoiaLevel": "2",
"defaultAction": "BLOCK",
"action": "BLOCK",
"controlGroup": "SQL Injection"
},
{
"id": "72057594038010287",
"modifiedTime": "1619611688",
"creationTime": "1619611688",
"name": "SQLi bypass attempt by ticks or backticks detected",
"description": "This rule detects SQL Injection bypass attempt by ticks or backticks.",
"severity": "CRITICAL",
"controlNumber": "942510",
"version": "OWASP_CRS/3.3.0",
"paranoiaLevel": "2",
"defaultAction": "BLOCK",
"action": "BLOCK",
"controlGroup": "SQL Injection"
},
{
"id": "72057594038010288",
"modifiedTime": "1619611688",
"creationTime": "1619611688",
"name": "SQLi bypass attempt by ticks detected",
"description": "This rule detects SQL Injection bypass attempt by ticks.",
"severity": "CRITICAL",
"controlNumber": "942511",
"version": "OWASP_CRS/3.3.0",
"paranoiaLevel": "3",
"defaultAction": "BLOCK",
"action": "BLOCK",
"controlGroup": "SQL Injection"
},
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating an AppProtection Profile
To update an AppProtection profile:
- Send a `PUT` request to the following endpoint in the inspection-profile-controller: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionProfile/{inspectionProfileId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `inspectionProfileId`: The unique identifier of the AppProtection profile.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/inspectionProfile/217246660303025210` in the inspection-profile-controller.
- Use the following JSON payload and provide the following information:
- Name of the application
- Paranoia level: An integer which refers to the associated paranoia level. The supported values are 1, 2, 3, or 4.
- [View the JSON payload](#jsonPayload2)
[]{
"controlsInfo": [{
"controlType": "CUSTOM",
"count": 0
}],
"creationTime": 0,
"customControls": [{
"action": "PASS",
"actionValue": "string",
"associatedInspectionProfileNames": [{
"id": 0,
"name": "string"
}],
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
"rules": [{
"conditions": [{
"lhs": "SIZE",
"op": "RX",
"rhs": "string"
}],
"names": [
"string"
],
"type": "REQUEST_HEADERS"
}],
"severity": "CRITICAL",
"type": "REQUEST",
"version": "string"
}],
"description": "string",
"globalControlActions": [
"string"
],
"id": 0,
"incarnationNumber": 0,
"modifiedBy": 0,
"modifiedTime": 0,
"name": "string",
"paranoiaLevel": 0,
"predefinedControls": [{
"action": "PASS",
"actionValue": "string",
"associatedInspectionProfileNames": [{
"id": 0,
"name": "string"
}],
"attachment": "string",
"controlGroup": "string",
"controlNumber": 0,
"creationTime": 0,
"defaultAction": "PASS",
"defaultActionValue": "string",
"description": "string",
"id": 0,
"modifiedBy": 0,
"modifiedTime": 0,
"name": "string",
"paranoiaLevel": 0,
"severity": "CRITICAL",
"version": "string"
}],
"predefinedControlsVersion": "string"
}
Passing an empty list of custom or predefined controls in the JSON payload dissociates the controls from the AppProtection profile. The JSON payload passed for the `PUT` request to update the AppProtection profile is considered the source of truth and replaces the old custom or predefined controls with the new values. You choose the AppProtection profile criteria you want to include in the JSON payload. Refer to the [Adding Field Descriptions](#fieldDescriptions) section for supported values.
A successful response yields `Code 204 - No Content`, meaning the AppProtection profile is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Associating All Predefined Controls to an AppProtection Profile
To associate all predefined controls with an AppProtection profile:
- Send a `PUT` request to the following endpoint in the inspection-profile-controller: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionProfile/{inspectionProfileId}/associateAllPredefinedControls`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `inspectionProfileId`: The unique identifier of the AppProtection profile.
- version: The predefined control version. The supported value is `OWASP_CRS/3.30`.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/inspectionProfile/217246660303025210/associateAllPredefinedControls`.
To associate all predefined controls to an AppProtection profile using a version:
- Send a `PUT` request to the following endpoint in the inspection-profile-controller: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionProfile/{inspectionProfileId}/associateAllPredefinedControls?version=<version_id>`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/inspectionProfile/217246660303025210/associateAllPredefinedControls?version=``1.0`.
A successful response yields `Code 204 - No Content`, meaning the AppProtection profile is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Dissociate All Predefined Controls from an AppProtection Profile
This API is deprecated and will not be supported after January 27, 2023. To learn more, see [Dissociate All Predefined Controls from an AppProtection Profile](#dissociate).
To dissociate all predefined controls from an AppProtection profile:
- Send a `PUT` request to the following endpoint in the inspection-profile-controller: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionProfile/{inspectionProfileId}/deAssociateAllPredefinedControls`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `inspectionProfileId`: The unique identifier of the inspection profile.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/inspectionProfile/217246660303025210/deAssociateAllPredefinedControls`
A successful response yields `Code 204 - No Content`, meaning the AppProtection profile is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Dissociate All Predefined Controls from an AppProtection Profile
To dissociate all predefined controls from an AppProtection profile:
- Send a `PUT` request to the following endpoint in the inspection-profile-controller: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionProfile/{inspectionProfileId}/dissociateAllPredefinedControls`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `inspectionProfileId`: The unique identifier of the AppProtection profile.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/inspectionProfile/217246660303025210/deAssociateAllPredefinedControls`
A successful response yields `Code 204 - No Content`, meaning the inspection profile is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Partially Updating the AppProtection Profile and Controls
To partially update the AppProtection profile and controls:
- Send a `PATCH` request to the following endpoint in the inspection-profile-controller: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionProfile/{inspectionProfileId}/patch`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `inspectionProfileId`: The unique identifier of the AppProtection profile.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/inspectionProfile/217246660303025210/patch`.
- Use the following JSON payload and provide the following information:
- Name of the application
- Paranoia level: An integer which refers to the associated paranoia level. The supported values are 1, 2, 3, or 4.
- [View the JSON payload](#jsonPayload3)
[]{
"controlsInfo": [{
"controlType": "CUSTOM",
"count": 0
}],
"creationTime": 0,
"customControls": [{
"action": "PASS",
"actionValue": "string",
"associatedInspectionProfileNames": [{
"id": 0,
"name": "string"
}],
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
"rules": [{
"conditions": [{
"lhs": "SIZE",
"op": "RX",
"rhs": "string"
}],
"names": [
"string"
],
"type": "REQUEST_HEADERS"
}],
"severity": "CRITICAL",
"type": "REQUEST",
"version": "string"
}],
"description": "string",
"globalControlActions": [
"string"
],
"id": 0,
"incarnationNumber": 0,
"modifiedBy": 0,
"modifiedTime": 0,
"name": "string",
"paranoiaLevel": 0,
"predefinedControls": [{
"action": "PASS",
"actionValue": "string",
"associatedInspectionProfileNames": [{
"id": 0,
"name": "string"
}],
"attachment": "string",
"controlGroup": "string",
"controlNumber": 0,
"creationTime": 0,
"defaultAction": "PASS",
"defaultActionValue": "string",
"description": "string",
"id": 0,
"modifiedBy": 0,
"modifiedTime": 0,
"name": "string",
"paranoiaLevel": 0,
"severity": "CRITICAL",
"version": "string"
}],
"predefinedControlsVersion": "string"
}
The `PATCH` request to partially update the AppProtection profile and controls adds new controls or updates existing controls with the inputs in the payload. You choose the AppProtection profile criteria you want to include in the JSON payload. Refer to the [Adding Field Descriptions](#fieldDescriptions) section for supported values.
A successful response yields `Code 204 - No Content`, meaning the AppProtection profile is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting an AppProtection Profile
To delete an AppProtection profile:
- Send a `DELETE` request to the following endpoint in the inspection-profile-controller: `/mgmtconfig/v1/admin/customers/{customerId}/inspectionProfile/{inspectionProfileId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `inspectionProfileId`: The unique identifier of the inspection profile.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/inspectionProfile/217246660303025210`.
A successful response yields `Code 204 - No Content`, meaning the AppProtection profile is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).

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