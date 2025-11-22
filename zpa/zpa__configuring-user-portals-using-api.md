# Configuring User Portals Using API
Source: https://help.zscaler.com/zpa/configuring-user-portals-using-api
PDF: https://help.zscaler.com/pdf/com/en/1530947.pdf

This article provides information on managing Zscaler Private Access (ZPA) user portal use cases using APIs. All APIs are rate limited. To learn more, see [About User Portals](/zpa/about-user-portals) and [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Prerequisite API Call
Before you create or update a user portal, you must get the certificate ID. To learn more, see [Configuring Certificates Using API](/zpa/configuring-certificates-using-api).
Creating a User Portal
To create a user portal:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/userPortal?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/userPortal?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following:
- `managedByZs`: Indicates if the certificate type is Managed (`true`) or Custom (`false`).
-
`domain`: Enter the full URL for the portal. This is the URL that users access to view the portal. The URL must use the HTTPS protocol and be a fully qualified domain name (FQDN). A user portal's FQDN cannot be configured as an application within an application segment.
The `domain` field is only required if `managedByZs` is set to `false`.
-
`certificateId`: The unique identifier of the certificate. To learn more, see [Configuring Certificates Using API](/zpa/configuring-certificates-using-api).
The `certificateId` field is only required if `managedByZs` is set to `false`.
- `enabled`: Indicates if the user portal is enabled (`true`) or disabled (`false`). If disabled, the portal is inaccessible to users.
- `name`: The name of the user portal.
- `extLabel`: The authentication domain name prefix used for the portal URL. The supported string can include integers, lowercase characters, and hyphens (-). This field supports integers between 3 and 31. For example, `server-2`.
- `extDomain`: The authentication domain name prefix used for a Zscaler-managed certificates when [creating a privileged portal](/zpa/configuring-privileged-portals). If you are using Zscaler-managed certificates and pass the external domain name prefix, the `certificateId` field becomes null. Periods (.) are not supported since the FQDN includes a period as part of the suffix or top-level domain.
- [View the JSON payload](#createUserPortalPayload)
[]
`{
"enabled":true,
"name":"<example name>",
"certManagedByZsRadio":"<string>",
"domain":"<string>",
"description":"<example description>",
"userNotificationEnabled":true,
"userNotification":"<example user notification>",
"certificateId":"<certificate ID>",
"managedByZs":true,
"extLabel":"<string>",
"extDomain":"<string>"
}`
- [View an example JSON payload](#createUserPortalSamplePayload)
[]
`{
"enabled":true,
"name":"userportal name",
"certManagedByZsRadio":"managed",
"domain":"",
"description":"test description",
"userNotificationEnabled":true,
"userNotification":"test message text",
"certificateId":"",
"managedByZs":true,
"extLabel":"portalurl",
"extDomain":"aneela.com"
}`
- [View an example response](#createUserPortalExampleResponse)
[]
`{
"id":"145283994705985862",
"modifiedTime":"1753247369",
"creationTime":"1753247369",
"modifiedBy":"72057594038779845",
"name":"userportal name",
"enabled":true,
"description":"test description",
"domain":"portalurl-aneela-com.d.zscalerportal.net",
"userNotification":"test message text",
"userNotificationEnabled":true,
"extDomainTranslation":"aneela.com",
"extLabel":"portalurl",
"extDomain":"aneela.com"
}`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of All User Portals
To get details of all user portals for a given customer:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/userPortal/?microtenantId={microtenantId}&page={page}&pagesize={pageSize}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
- `page`: Specifies the page number.
- `pagesize`: Specifies the page size. If not provided, the default page size is 20. The maximum page size is 500.
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/userPortal/?microtenantId=0&page=1&pagesize=20`.
- [View an example response](#getAllUserPortalsResponse)
[]
`{
"totalPages": "1",
"totalCount": "1",
"list": [
{
"id": "145283994705985838",
"modifiedTime": "1747939958",
"creationTime": "1747939958",
"modifiedBy": "72057594038779845",
"name": "test user portal",
"scopeName": "Default",
"enabled": true,
"domain": "aneela-aneela-com.d.zscalerportal.net",
"userNotificationEnabled": true,
"extDomainTranslation": "aneela.com",
"extLabel": "aneela",
"extDomain": "aneela.com",
"extDomainName": "aneela-com.d.zscalerportal.net"
}
]
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of a Particular User Portal
To get details of a particular user portal:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/userPortal/{id}?microtenantId={microtenantId}&page={page}&pagesize={pageSize}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the user portal.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
- `page`: Specifies the page number.
- `pagesize`: Specifies the page size. If not provided, the default page size is 20. The maximum page size is 500.
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/userPortal/145283994705985862?microtenantId=0&page=1&pagesize=20`.
- [View an example response](#getUserPortalDetailsResponse)
[]
`{
"id": "145283994705985862",
"modifiedTime": "1753247369",
"creationTime": "1753247369",
"modifiedBy": "72057594038779845",
"name": "userportal name",
"scopeName": "Default",
"enabled": true,
"description": "test description",
"domain": "portalurl-aneela-com.d.zscalerportal.net",
"userNotification": "test message text",
"userNotificationEnabled": true,
"extDomainTranslation": "aneela.com",
"extLabel": "portalurl",
"extDomain": "aneela.com",
"extDomainName": "aneela-com.d.zscalerportal.net"
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a User Portal
To update a user portal:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/userPortal/{Id}?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the user portal.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/userPortal/145283994705985862?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following:
- `managedByZs`: Indicates if the certificate type is Managed (`true`) or Custom (`false`).
-
`domain`: Enter the full URL for the portal. This is the URL that users access to view the portal. The URL must use the HTTPS protocol and be a fully qualified domain name (FQDN). A user portal's FQDN cannot be configured as an application within an application segment.
The `domain` field is only required if `managedByZs` is set to `false`.
-
`certificateId`: The unique identifier of the certificate. To learn more, see [Configuring Certificates Using API](/zpa/configuring-certificates-using-api).
The `certificateId` field is only required if `managedByZs` is set to `false`.
- `enabled`: Indicates if the user portal is enabled (`true`) or disabled (`false`). If disabled, the portal is inaccessible to users.
- `name`: The name of the user portal.
- `extLabel`: The authentication domain name prefix used for the portal URL. The supported string can include integers, lowercase characters, and hyphens (-). This field supports integers between 3 and 31. For example, `server-2`.
- `extDomain`: The authentication domain name prefix used for a Zscaler-managed certificates when [creating a privileged portal](/zpa/configuring-privileged-portals). If you are using Zscaler-managed certificates and pass the external domain name prefix, the `certificateId` field becomes null. Periods (.) are not supported since the FQDN includes a period as part of the suffix or top-level domain.
- [View the JSON payload](#updateUserPortalPayload)
[]
`{
"enabled":true,
"id":"<id>",
"objectType":"UserPortals",
"action":"EDIT",
"modifiedTime":"1753247369",
"creationTime":"1753247369",
"modifiedBy":"72057594038779845",
"name":"<example user portal name>",
"scopeName":"Default",
"description":"<example description>",
"domain":"",
"userNotification":"<example user notification>",
"userNotificationEnabled":true,
"extDomainTranslation":"aneela.com",
"extLabel":"portalurl",
"extDomain":"aneela.com",
"extDomainName":"aneela-com.d.zscalerportal.net",
"hideInfoTooltip":true,
"restrictedEntity":false,
"certManagedByZsRadio":"managed",
"certificateId":"",
"managedByZs":true
}`
- [View an example JSON payload](#updateUserPortalExamplePayload)
[]
`{
"enabled":true,
"id":"145283994705985862",
"objectType":"UserPortals",
"action":"EDIT",
"modifiedTime":"1753247369",
"creationTime":"1753247369",
"modifiedBy":"72057594038779845",
"name":"userportal name updated",
"scopeName":"Default",
"description":"test description updated",
"domain":"",
"userNotification":"test message text updated",
"userNotificationEnabled":true,
"extDomainTranslation":"aneela.com",
"extLabel":"portalurl",
"extDomain":"aneela.com",
"extDomainName":"aneela-com.d.zscalerportal.net",
"hideInfoTooltip":true,
"restrictedEntity":false,
"certManagedByZsRadio":"managed",
"certificateId":"",
"managedByZs":true
}`
A successful response returns code 204, meaning the user portal is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting a User Portal
To delete a user portal:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/userPortal/{Id}?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the user portal.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/userPortal/145283994705985862?microtenantId=0`.
A successful response returns code 204, meaning the user portal is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).

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