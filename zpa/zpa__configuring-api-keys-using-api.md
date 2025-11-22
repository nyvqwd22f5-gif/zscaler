# Configuring API Keys Using API
Source: https://help.zscaler.com/zpa/configuring-api-keys-using-api
PDF: https://help.zscaler.com/pdf/com/en/1530945.pdf

This article provides information on managing Zscaler Private Access (ZPA) API key use cases using APIs. All APIs are rate limited. To learn more, see [About API Key Management](/zpa/about-api-key-management) and [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Prerequisite API Call
Before you create or update an API key, you must get the `roleId`, the unique identifier of the administrator role. To learn more, see [Managing Administrator Roles Using API](/zpa/managing-administrator-roles-using-api).
Creating an API Key
To create an API key:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/apiKeys?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/apiKeys?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following:
- `roleId`: The unique identifier of the administrator role. To learn more, see [Managing Administrator Roles Using API](/zpa/managing-administrator-roles-using-api).
- `name`: The name of the API key.
- `tokenExpiryTimeInSec`: The amount of time the key is available to use. The maximum amount of time is 3,600 seconds.
- [View the JSON payload](#createApiKeyJson)
[]
`{
"enabled":true,
"tokenExpiryTimeInSec":"<integer>",
"name":"<example name>",
"roleId":"<role ID>"
}`
- [View the sample JSON payload](#createApiKeySampleJson)
[]
`{
"enabled":true,
"tokenExpiryTimeInSec":"3600",
"name":"test API key",
"roleId":"28"
}`
- [View an example response](#createApiKeyExampleResponse)
[]
`{
"id":"145283994705985861",
"name":"test aneela jul22",
"scopeId":"0",
"clientId":"MTQ1MjgzOTk0NzA1OTg1ODYxLWIwYjEyYWFhLTkxNzQtNGNlMi05ZWQxLTBmYzVmYjdmYzYyNg==",
"clientSecret":"'[dbx(&.Y(mDtrx*jj2ysoV7lM)9G-t9",
"enabled":true,
"tokenExpiryTimeInSec":"3600",
"roleId":"28",
"pinSessionEnabled":false,
"isLocked":false
}`
A successful response returns code 201, meaning the API key is created. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details for All API Keys
To get details for all API keys:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/apiKeys?microtenantId={microtenantId}&page={pageNumber}&pageSize={pageSize}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
- `page`: Specifies the page number.
- `pageSize`: Specifies the page size. If not provided, the default page size is 20. The maximum page size is 500.
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/apiKeys?microtenantId=0&page=1&pageSize=20`.
- [View an example response](#getAllKeysResponse)
[]
`{
"totalPages": "2",
"totalCount": "37",
"list": [
{
"modifiedTime": "1753213126",
"creationTime": "1744752949",
"modifiedBy": "72057594038779845",
"id": "145283994705985775",
"clientId": "MTQ1MjgzOTk0NzA1OTg1Nzc1LTAyNWFiMTYyLTllODgtNDg1MC1hYWQ0LWUyNDM3YjVjZjQyMA==",
"name": "test user apr15_2",
"tokenExpiryTimeInSec": "360",
"enabled": true,
"pinSessionEnabled": false,
"isLocked": false,
"syncVersion": "0",
"deliveryTag": "0",
"customerId": "145283994705985536",
"roleId": "28",
"readOnly": false,
"restrictedEntity": false,
"zscalerManaged": false
}
]
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details for a Particular API Key
To get details for a particular API key:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/apiKeys/{id}?microtenantId={microtenantId}&page={pageNumber}&pageSize={pageSize}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the API key. To learn more, see [Getting Details for All API Keys](#get-all-keys).
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
- `page`: Specifies the page number.
- `pageSize`: Specifies the page size. If not provided, the default page size is 20. The maximum page size is 500.
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/apiKeys/145283994705985775?microtenantId=0&page=1&pageSize=20`.
- [View an example response](#getApiKeyResponse)
[]
`{
"modifiedTime": "1753213126",
"creationTime": "1744752949",
"modifiedBy": "72057594038779845",
"id": "145283994705985775",
"clientId": "MTQ1MjgzOTk0NzA1OTg1Nzc1LTAyNWFiMTYyLTllODgtNDg1MC1hYWQ0LWUyNDM3YjVjZjQyMA==",
"name": "aneela17 user apr15_2",
"tokenExpiryTimeInSec": "360",
"enabled": true,
"pinSessionEnabled": false,
"isLocked": false,
"syncVersion": "0",
"deliveryTag": "0",
"customerId": "145283994705985536",
"roleId": "28",
"readOnly": false,
"restrictedEntity": false,
"zscalerManaged": false
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating an API Key
To update an API key:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/apiKeys/{id}?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the API key. To learn more, see [Getting Details for All API Keys](#get-all-keys).
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/apiKeys?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following:
- `roleId`: The unique identifier of the administrator role. To learn more, see [Managing Administrator Roles Using API](/zpa/managing-administrator-roles-using-api).
- `name`: The name of the API key.
- [View an example JSON payload](#updateApiKeyPayload)
[]
`{
"enabled":true,
"tokenExpiryTimeInSec":"360",
"id":"145283994705985775",
"objectType":"ClientCredential",
"action":"EDIT",
"modifiedTime":"1748384838",
"creationTime":"1744752949",
"modifiedBy":"72057594038779845",
"clientId":"MTQ1MjgzOTk0NzA1OTg1Nzc1LTAyNWFiMTYyLTllODgtNDg1MC1hYWQ0LWUyNDM3YjVjZjQyMA==",
"name":"test user apr15_2",
"pinSessionEnabled":false,
"isLocked":false,
"syncVersion":"0",
"deliveryTag":"0",
"customerId":"145283994705985536",
"roleId":"28",
"readOnly":false,
"restrictedEntity":false,
"zscalerManaged":false
}`
A successful response returns code 204, meaning the API key is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting an API Key
To delete an API key:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/apiKeys/{id}?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the API key. To learn more, see [Getting Details for All API Keys](#get-all-keys).
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/apiKeys/145283994705985775/?microtenantId=0`.
A successful response returns code 204, meaning the API key is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).

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