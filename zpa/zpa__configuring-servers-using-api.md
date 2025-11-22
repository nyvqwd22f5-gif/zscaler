# Configuring Servers Using API
Source: https://help.zscaler.com/zpa/configuring-servers-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484791.pdf

This article provides information on managing Zscaler Private Access (ZPA) [server](/zpa/about-servers) use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Prerequisite API Call
Before you create a new server, you must get the required details for server groups. To learn more, see [Configuring Server Groups Using API](/zpa/configuring-server-groups-using-api).
[]Creating a New Server
To add a new server:
- Send a `POST` request to the following endpoint in the server-controller: `/mgmtconfig/v1/admin/customers/{customerId}/server`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057615512764416/server`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload to create the server and provide the following information:
- `name`: The name of the server.
- `enabled`: Indicates the status of the server (`true`, `false`).
- `address`: Indicates the server IP or the domain.
- Information about the associated server groups.
- [View the JSON payload](#Viewthejsonpayload)
[]{
"name":"server_name",
"description":"description",
"enabled":true,
"address":"serverIP or domain",
"appServerGroupIds":[
"serverGroupId1",
"serverGroupId2"
]
}
- [View an example response](#Viewanexampleresponse)
[]{
"id": "217246660303024816",
"creationTime": "1614272495",
"modifiedBy": "217246660303024815",
"name": "server_example",
"address": "192.168.1.1",
"enabled": true,
"description": "Test App Server",
"appServerGroupIds": [
"217246660303020476",
"217246660302996731"
],
"configSpace": "DEFAULT"
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the server criteria you want to include in the JSON payload. Refer to the [Adding Field Descriptions](#FieldDescriptions) section for supported values.
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the server use cases:
[](/zpa/about-api-keys)[](/zpa/configuring-microtenants-using-api)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| name | This field defines the name of the server | Yes | String |
| description | This field defines the description of the server | No | String |
| enabled | This field defines the status of the server | Yes | true, false |
| address | This field defines the domain or IP address of the server | Yes | String |
| appServerGroupIds | This field defines the list of server groups IDs | No | List of strings |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. Pass `microtenantId` as null to retrieve data from all Microtenants associated with the tenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
[]Getting Details for a Particular Server
To get details for a particular server:
- Send a `GET` request to the following endpoint in the server-controller: `/mgmtconfig/v1/admin/customers/{customerId}/server/{serverId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `serverId`: The ID of the server.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/server/72057615512764544`.
- [View an example response](#Viewanexampleresponse3)
[]{
"id": "72057615512764544",
"creationTime": "1579729244",
"modifiedBy": "72057615512764417",
"name": "PB App",
"address": "10.0.0.190",
"enabled": true,
"appServerGroupAssociations": {
"72057615512764545": "PB App"
},
"configSpace": "DEFAULT"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details for All Servers
To get details for all servers:
- Send a `GET` request to the following endpoint in the server-controller: `/mgmtconfig/v1/admin/customers/{customerId}/server`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057615512764416/server`.
- [View an example response](#Viewanexampleresponse4)
[]{
"totalPages": "1",
"list": [
{
"id": "72057615512764544",
"creationTime": "1579729244",
"modifiedBy": "72057615512764417",
"name": "PB App",
"address": "10.0.0.190",
"enabled": true,
"appServerGroupAssociations": {
"72057615512764545": "PB App"
},
"configSpace": "DEFAULT"
},
{
"id": "72057615512764472",
"creationTime": "1560983093",
"modifiedBy": "72057615512764447",
"name": "srv1",
"address": "10.0.3.7",
"enabled": true,
"appServerGroupAssociations": {
"72057615512764473": "srvgrp1"
},
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
"appServerGroupAssociations": {
"72057615512764545": "PB App",
"72057615512764418": "Server Group",
"72057615512764473": "srvgrp1"
},
"configSpace": "DEFAULT"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/server?page=1&pagesize=20` .
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/144118148382065089/server?page=1&pagesize=2`.
- [View an example response](#Viewanexampleresponse5)
[]{
"totalPages": "7",
"list": [
{
"id": "144118148382065089",
"creationTime": "1549613557",
"modifiedBy": "144118148382064667",
"name": "akk",
"address": "10.65.1.220",
"enabled": true,
"appServerGroupIds": [
"144118148382065088"
],
"configSpace": "DEFAULT"
},
{
"id": "144118148382065094",
"modifiedTime": "1591164519",
"creationTime": "1549616584",
"modifiedBy": "144118148382064642",
"name": "app2.lanukcorp.com",
"address": "10.0.1.145",
"enabled": true,
"appServerGroupIds": [
"144118148382065093"
],
"configSpace": "DEFAULT"
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports a search option to search by features and fields. To search by features and fields:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/73186051597795328/server&search={searchString}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid search string values. The search string values are in the format `fieldName operator fieldValue`. Only search string values that correspond to the values for valid fields and filters are supported. For example, the string `address%20LIKE%20test` is supported for the **Domain or IP Address** filter, using the **Contains **(`LIKE`) operator, for the filter value `test`.
For example: `/mgmtconfig/v1/admin/customers/73186051597795328/server&search=address%20LIKE%20test`.
- [View an example response](#gettingAllServersSearch)
[]{
"totalPages": "1",
"totalCount": "1",
"list": [
{
"id": "72057594037996318",
"creationTime": "1615454081",
"modifiedBy": "72057594037957297",
"name": "Test Error1",
"address": "newtest.com",
"enabled": true,
"description": "&",
"appServerGroupIds": [
"72057594037988996"
],
"configSpace": "DEFAULT"
}
]
}
If you use the ZPA API PortaI or the [Reference Guide](/zpa/zpa-api/api-developer-reference-guide/reference-guide) to make your API calls, the search field string does not require any characters. For example, `address%20LIKE%20test` is `address LIKE test`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Updating Server Details
To update the server:
- Use the updated JSON payload from the [Creating a New Server](#Create) section and send a `PUT` request to the following endpoint in the server-controller: `/mgmtconfig/v1/admin/customers/{customerId}/server/{serverId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `serverId`: The server ID captured in the [Creating a New Server](#Create) section.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/server/72057615512764544`.
Refer to the [Adding Field Descriptions](#FieldDescriptions) section for supported values.
- [View the JSON payload](#Viewthejsonpayload2)
[]{
"address": "string",
"appServerGroupIds": [
"string"
],
"configSpace": "DEFAULT",
"creationTime": 0,
"description": "string",
"enabled": true,
"id": 0,
"modifiedBy": 0,
"modifiedTime": 0,
"name": "string"
}
A successful response yields code 204, meaning the server is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Deleting a Server
To delete a server:
- Send a `DELETE` request to the following endpoint in the server-controller: `/mgmtconfig/v1/admin/customers/{customerId}/server/{serverId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `serverId`: The server ID captured in the [Creating a New Server](#Create) section.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/server/72057615512764544`.
An object that is referenced in another object cannot be deleted. Error code 400 is returned in this situation. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
- [View error code 400](#errorcode)
[]{
"params": [
"Application",
"app 3 created on postman feb 5_edited"
],
"id": "resource.referenced",
"reason": "Resource is being referenced in Application : app 3 created on postman feb 5_edited."
}
A successful response yields code 204, meaning the server is deleted.

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