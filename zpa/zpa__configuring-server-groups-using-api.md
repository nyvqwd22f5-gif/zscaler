# Configuring Server Groups Using API
Source: https://help.zscaler.com/zpa/configuring-server-groups-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484796.pdf

This article provides information on managing Zscaler Private Access (ZPA) [server group](/zpa/about-server-groups) use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Prerequisite API Call
Before you create a new server group, you must get the required list of App Connector groups. To learn more, see [Configuring App Connector Groups Using API](/zpa/configuring-app-connector-groups-using-api#getAppConnectorGroups).
[]Creating a New Server Group
To add a new server group:
- Send a `POST` request to the following endpoint in the** **server-group-controller: `/mgmtconfig/v1/admin/customers/{customerId}/serverGroup`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057615512764416/serverGroup`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the entire JSON payload to create a server group and provide the required details:
- `name`: The name of the server group.
- `enabled`: Indicates if the server group is enabled (`true`) or disabled (`false`).
- `dynamicDiscovery`: This field controls dynamic discovery of the servers.
- Associated App Connector groups
- Provide the associated server list only when the auto-server-discovery is disabled (i.e., dynamicDiscovery= false)
- [View the JSON payload](#Viewthejsonpayload)
[]{
"enabled":true,
"dynamicDiscovery":false,
"name":"<serverGroupName>",
"description":"desc",
"servers":[
{
"id":"<serverId1>",
},
{
"id":"<serverId2>",
}
],
"appConnectorGroups":[
{
"id":"<appConnectorGroupId1>",
},
{
"id":"<appConnectorGroupId2>",
}
]
}
- [View the example response](#Viewanexampleresponse2)
[]{
"id": "217246660303024819",
"enabled": true,
"name": "Example Test Server Group",
"description": "Example Server Group for testing",
"servers": [
{
"id": "217246660302995951",
"configSpace": "DEFAULT"
},
{
"id": "217246660303024816",
"configSpace": "DEFAULT"
}
],
"ipAnchored": false,
"configSpace": "DEFAULT",
"dynamicDiscovery": false,
"appConnectorGroups": [
{
"id": "217246660303020475",
"name": "11113",
"enabled": true,
"siemAppConnectorGroup": false
},
{
"id": "217246660303023146",
"name": "1 mp connector grp",
"enabled": true,
"siemAppConnectorGroup": false
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the server group criteria you want to include in the JSON payload. Refer to the [Adding Field Descriptions](#FieldDescriptions) section below for supported values.
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the server group use cases:
[](/zpa/about-api-keys)[](/zpa/configuring-microtenants-using-api)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| name | This field defines the name of the server group | Yes | String |
| description | This field is the description of the server group | No | String |
| enabled | This field defines if the server group is enabled or disabled | No | `true`, `false` |
| dynamicDiscovery | This field controls dynamic discovery of the servers | Yes | `true`, `false` |
| appConnectorGroups | This field is a json array of App Connector Group IDs | Yes | Accepts values in the format:`{``"id":"<appConnectorGrpId>",``}` |
| servers | This field is a list of servers that are applicable only when dynamic discovery is disabled. Server name is required only in cases where the new servers need to be created in this API. For existing servers, pass only the `serverId`. | No | Accepts values in the format:`{``"id":"<serverId>",``}` |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. Pass `microtenantId` as null to retrieve data from all Microtenants associated with the tenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
Getting Details for a Particular Server Group
To get details for a particular server group:
- Send a `GET` request to the following endpoint in the server-group-controller: `/mgmtconfig/v1/admin/customers/{customerId}/serverGroup/{groupId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `groupId`: The ID of the particular server group you want to get details for.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/serverGroup/72057615512764618`.
- [View an example response](#Viewanexampleresponse3)
[]{
"creationTime": "1612476914",
"modifiedBy": "72057615512764617",
"id": "72057615512764618",
"enabled": false,
"name": "TestAppServerGrp",
"learningEnabled": false,
"description": "string",
"ipAnchored": false,
"configSpace": "DEFAULT"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details for All Server Groups
To get details for all the server groups:
- Send a `GET` request to the following endpoint in the server-group-controller: `/mgmtconfig/v1/admin/customers/{customerId}/serverGroup`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057615512764416/serverGroup`.
- [View an example response](#Viewanexampleresponse4)
[]{
"totalPages": "1",
"list": [
{
"modifiedTime": "1612391262",
"creationTime": "1574113633",
"modifiedBy": "72057615512764552",
"id": "72057615512764532",
"enabled": true,
"name": "AWS Connector",
"learningEnabled": true,
"ipAnchored": false,
"configSpace": "DEFAULT",
"connectorGroups": [
{
"id": "72057615512764441",
"modifiedTime": "1610747816",
"creationTime": "1553590280",
"modifiedBy": "72057594037928174",
"name": "AWS",
"enabled": true,
"location": "Oregon City, OR 97045, USA",
"cityCountry": "Oregon City, US",
"countryCode": "US",
"siemConnectorGroup": false
}
]
},
{
"creationTime": "1579729263",
"modifiedBy": "72057615512764417",
"id": "72057615512764545",
"enabled": true,
"name": "PB App",
"learningEnabled": false,
"servers": [
{
"id": "72057615512764544",
"creationTime": "1579729244",
"modifiedBy": "72057615512764417",
"name": "PB App",
"address": "10.0.0.190",
"enabled": true,
"configSpace": "DEFAULT"
},
{
"id": "72057615512764604",
"creationTime": "1612389365",
"modifiedBy": "72057615512764603",
"name": "TestApplicationServer",
"address": "10.0.0.190",
"enabled": true,
"description": "string",
"configSpace": "DEFAULT"
}
],
"applications": [
{
"id": "72057615512764533",
"name": "PB App"
}
],
"ipAnchored": false,
"configSpace": "DEFAULT",
"connectorGroups": [
{
"id": "72057615512764441",
"modifiedTime": "1610747816",
"creationTime": "1553590280",
"modifiedBy": "72057594037928174",
"name": "AWS",
"enabled": true,
"location": "Oregon City, OR 97045, USA",
"cityCountry": "Oregon City, US",
"countryCode": "US",
"siemConnectorGroup": false
}
]
},
{
"modifiedTime": "1560279822",
"creationTime": "1551291935",
"modifiedBy": "72057615512764417",
"id": "72057615512764418",
"enabled": true,
"name": "Server Group",
"learningEnabled": true,
"servers": [
{
"id": "72057615512764604",
"creationTime": "1612389365",
"modifiedBy": "72057615512764603",
"name": "TestApplicationServer",
"address": "10.0.0.190",
"enabled": true,
"description": "string",
"configSpace": "DEFAULT"
}
],
"applications": [
{
"id": "72057615512764419",
"name": "Internal Application"
}
],
"ipAnchored": false,
"configSpace": "DEFAULT",
"connectorGroups": [
{
"id": "72057615512764449",
"modifiedTime": "1610747816",
"creationTime": "1560278889",
"modifiedBy": "72057594037928174",
"name": "Azure",
"enabled": true,
"location": "Oregon, USA",
"cityCountry": "Brothers, US",
"countryCode": "US",
"siemConnectorGroup": false
}
]
},
{
"creationTime": "1560983270",
"modifiedBy": "72057615512764447",
"id": "72057615512764473",
"enabled": true,
"name": "srvgrp1",
"learningEnabled": false,
"servers": [
{
"id": "72057615512764472",
"creationTime": "1560983093",
"modifiedBy": "72057615512764447",
"name": "srv1",
"address": "10.0.3.7",
"enabled": true,
"configSpace": "DEFAULT"
},
{
"id": "72057615512764604",
"creationTime": "1612389365",
"modifiedBy": "72057615512764603",
"name": "TestApplicationServer",
"address": "10.0.0.190",
"enabled": true,
"description": "string",
"configSpace": "DEFAULT"
}
],
"applications": [
{
"id": "72057615512764474",
"name": "app1"
},
{
"id": "72057615512764478",
"name": "app2"
}
],
"ipAnchored": false,
"configSpace": "DEFAULT",
"connectorGroups": [
{
"id": "72057615512764449",
"modifiedTime": "1610747816",
"creationTime": "1560278889",
"modifiedBy": "72057594037928174",
"name": "Azure",
"enabled": true,
"location": "Oregon, USA",
"cityCountry": "Brothers, US",
"countryCode": "US",
"siemConnectorGroup": false
}
]
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/serverGroup?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/serverGroup?page=1&pagesize=2`.
- [View an example response](#Viewanexampleresponse5)
[]{
"totalPages": "11",
"list": [
{
"modifiedTime": "1584421166",
"creationTime": "1492592504",
"modifiedBy": "144118148382064930",
"id": "144118148382064812",
"enabled": true,
"name": "161_sg",
"description": "DESC - u",
"servers": [
{
"id": "144118148382064811",
"modifiedTime": "1498248533",
"creationTime": "1492592483",
"modifiedBy": "144118148382064667",
"name": "Server_161",
"address": "10.66.62.243",
"enabled": true,
"description": "DESC",
"configSpace": "DEFAULT"
}
],
"ipAnchored": false,
"configSpace": "DEFAULT",
"dynamicDiscovery": false,
"appConnectorGroups": [
{
"id": "144118148382064739",
"creationTime": "1471333758",
"modifiedBy": "144118148382064667",
"name": "New_Connector",
"enabled": true,
"description": "desc",
"overrideVersionProfile": false,
"dnsQueryType": "IPV4_IPV6",
"lssAppConnectorGroup": false
}
]
},
{
"creationTime": "1549613557",
"modifiedBy": "144118148382064667",
"id": "144118148382065088",
"enabled": true,
"name": "akk",
"servers": [
{
"id": "144118148382065089",
"creationTime": "1549613557",
"modifiedBy": "144118148382064667",
"name": "akk",
"address": "10.65.1.220",
"enabled": true,
"configSpace": "DEFAULT"
}
],
"ipAnchored": false,
"configSpace": "DEFAULT",
"dynamicDiscovery": false,
"appConnectorGroups": [
{
"id": "144118148382064835",
"modifiedTime": "1611094156",
"creationTime": "1499715985",
"modifiedBy": "72057594037928187",
"name": "Azure Connectors",
"enabled": true,
"versionProfileId": "72057594037928267",
"overrideVersionProfile": true,
"location": "California, USA",
"dnsQueryType": "IPV4_IPV6",
"cityCountry": "Sanger, US",
"countryCode": "US",
"lssAppConnectorGroup": false
}
]
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports a search option to search by features and fields. To search by features and fields:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/73186051597795328/serverGroup&search={searchString}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid search string values. The search string values are in the format `fieldName operator fieldValue`. Only search string values that correspond to the values for valid fields and filters are supported. For example, the string `name%20LIKE%20test` is supported for the **Name **filter, using the **Contains** (`LIKE`) operator, for the filter value `test`.
For example: `/mgmtconfig/v1/admin/customers/73186051597795328/serverGroup&search=name%20LIKE%20test`.
- [View an example response](#gettingAllServersSearch)
[]{
"totalPages": "16",
"totalCount": "16",
"list": [
{
"creationTime": "1657606560",
"modifiedBy": "72057594038606761",
"id": "72057594038606770",
"enabled": true,
"name": "test-group1",
"description": "Testing",
"applications": [
{
"id": "72057594038606771",
"name": "test-segment"
}
],
"ipAnchored": false,
"configSpace": "DEFAULT",
"microtenantName": "Default",
"dynamicDiscovery": true,
"appConnectorGroups": [
{
"id": "72057594038011105",
"modifiedTime": "1664486317",
"creationTime": "1620326590",
"modifiedBy": "72057594037982266",
"name": "App_Connector_Test_1",
"enabled": true,
"versionProfileId": "0",
"overrideVersionProfile": false,
"location": "1234 Test Rd, Bronx, NY 10466, USA",
"dnsQueryType": "IPV4_IPV6",
"cityCountry": "New York, US",
"countryCode": "US",
"tcpQuickAckApp": false,
"tcpQuickAckAssistant": false,
"tcpQuickAckReadAssistant": false,
"ipAcl": [
"::/0"
],
"lssAppConnectorGroup": false
}
]
}
]
}
If you use the ZPA API Portal or the [Reference Guide](/zpa/zpa-api/api-developer-reference-guide/reference-guide) to make your API calls, the search field string does not require any characters. For example, `name%20LIKE%20test` is `name LIKE test`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating Server Group Details
To update the server group details:
- Use the updated JSON payload from the [Creating a New Server Group](#Create) section and send a `PUT` request to the following endpoint in the server-group-controller: `/mgmtconfig/v1/admin/customers/{customerId}/serverGroup/{groupId}`.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/serverGroup/72057615512764618`.
- Provide the required details:
- `name`: The name of the Server Group.
- `enabled`: Indicates the status of the Server Group is enabled (`true`) or disabled (`false`).
- `dynamicDiscovery`: This field controls dynamic discovery of the servers.
- Information about the associated App Connector Groups.
- Provide the associated server list only when the auto-server-discovery is disabled (i.e., `learningEnabled` is `false`)
Refer to the [Adding Field Descriptions](#FieldDescriptions) section for supported values.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `groupId`: The ID of the server group captured in the [Creating a New Server Group](#Create) section.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/serverGroup/72057615512764618`.
- [View the JSON payload](#Viewthejsonpayload2)
[]{
"enabled":true,
"dynamicDiscovery":false,
"name":"<serverGroupName>",
"description":"desc",
"servers":[
{
"id":"<serverId1>"
},
{
"id":"<serverId2>"
}
],
"appConnectorGroups":[
{
"id":"<appConnectorGroupId1>"
},
{
"id":"<appConnectorGroupId2>"
}
]
}
A successful response returns code 204, meaning the server group is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
If a server group is configured using Zscaler Deception, then the update and delete options are unavailable.
[]Deleting a Server Group
To delete a server group:
- Send a `DELETE` request to the following endpoint in the server-group-controller: `/mgmtconfig/v1/admin/customers/{customerId}/serverGroup/{groupId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `groupId`: The ID of the server group captured in the [Creating a New Server Group](#Create) section.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/serverGroup/72057615512764618`.
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
A successful response returns code 204, meaning the application server group is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
If a server group is configured using Zscaler Deception, then the update and delete options are unavailable.

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