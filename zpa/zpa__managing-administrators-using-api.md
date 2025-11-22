# Managing Administrators Using API
Source: https://help.zscaler.com/zpa/managing-administrators-using-api
PDF: https://help.zscaler.com/pdf/com/en/1529291.pdf

This article provides information for managing Zscaler Private Access (ZPA) administrators using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Getting Administrator Details
To get the details of an administrator:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/administrators/{adminId}?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `adminId`: The unique identifier of the administrator.
- `microtenantId`: The unique identifier of the Microtenant. If the administrator is within a Microtenant, then this field is required. If the administrator is within the Default Microtenant, then this field must be passed as `0`. To learn more, see [Configuring Microtenant Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145256180497776640/administrators/145256180497776640`.
- [View an example response](#getAdminResponse)
[]
`{
"modifiedTime": "1695815396",
"creationTime": "1695815322",
"modifiedBy": "145256180497778056",
"id": "145256180497778056",
"username": "exampletest@145256180497776640.zpa-customer.com",
"email": "exampletest@145256180497776640.zpa-customer.com",
"customerId": "145256180497776640",
"isDeleted": "0",
"role": {
"id": "12",
"name": "ZPA Administrator"
},
"eula": "0",
"isEnabled": true,
"twoFactorAuthEnabled": false,
"phoneNumber": "+911111111111",
"forcePwdChange": false,
"pinSession": true,
"localLoginDisabled": false,
"isLocked": false,
"microtenantId": "145256180497776789"
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting All Administrators for a Customer or Company
To get details of all administrators for a customer or company:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/administrators`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/145256180497776640/administrators`.
- [View an example response](#getAllAdminsResponse)
[]
`[
{
"modifiedTime": "1695815396",
"creationTime": "1695815322",
"modifiedBy": "145256180497778056",
"id": "145256180497778056",
"username": "exampletest@145256180497776640.zpa-customer.com",
"email": "exampletest@145256180497776640.zpa-customer.com",
"customerId": "145256180497776640",
"isDeleted": "0",
"role": {
"id": "12",
"name": "ZPA Administrator"
},
"eula": "0",
"isEnabled": true,
"twoFactorAuthEnabled": false,
"phoneNumber": "+911111111111",
"forcePwdChange": false,
"pinSession": true,
"localLoginDisabled": false,
"isLocked": false,
"microtenantId": "145256180497776789"
},
{
"modifiedTime": "1685997687",
"creationTime": "1667540273",
"modifiedBy": "72057594038006701",
"id": "145256180497776790",
"username": "mtAdmin_145256180497776789@145256180497776640.zpa-customer.com",
"displayName": "Zscaler Private Access Scope Administrator",
"email": "mtAdmin_145256180497776789@145256180497776640.zpa-customer.com",
"customerId": "145256180497776640",
"isDeleted": "0",
"role": {
"id": "12",
"name": "ZPA Administrator"
},
"eula": "0",
"isEnabled": false,
"twoFactorAuthEnabled": false,
"phoneNumber": "2342321312312",
"forcePwdChange": false,
"pinSession": true,
"localLoginDisabled": false,
"isLocked": false,
"microtenantId": "145256180497776789"
}
]`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Prerequisite API Calls
Before you create or update an administrator, you must get the unique identifier of the role for the administrator. To learn more, see [Managing Administrator Roles Using API](/zpa/managing-administrator-roles-using-api).
Creating an Administrator
To create an administrator:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/administrators`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant. If the administrator is within a Microtenant, then this field is required. If the administrator is within the Default Microtenant, then this field must be passed as `0`. To learn more, see [Configuring Microtenant Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145256180497776640/administrators?microtenantId=145256180497776789`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- `tmpPassword`: The temporary password of the administrator. The password must be at least 8 characters in length, and include at least one uppercase letter, one special character, and one number.
- `password`: The password for the admin. The password must be at least 8 characters in length, and include at least one uppercase letter, one special character, and one number.
- `username`: This is the login ID for the administrator. It must be an email address, where the domain name matches your company's authentication domain name.
- `email`: (Optional) Enter the email address for the administrator. Updates regarding ZPA are sent to this email address.
- `phoneNumber`: The 10-digit phone number without any hyphens (-). This field is mandatory and is used for password recovery purposes.
- `roleId`: The unique identifier of the role for the administrator. To learn more, see [Managing Administrator Roles Using API](/zpa/managing-administrator-roles-using-api).
- [View the JSON payload](#viewJsonPayloadPost)
[]
`{
"microtenantId": 0,
"microtenantName": "string",
"username": "string",
"displayName": "string",
"email": "string",
"timezone": "string",
"password": "string",
"tmpPassword": "string",
"roleId": "string",
"comments": "string",
"languageCode": "string",
"eula": "string",
"groupIds": [
"string"
],
"isEnabled": true,
"forcePwdChange": true,
"twoFactorAuthEnabled": true,
"twoFactorAuthType": "string",
"tokenId": "string",
"phoneNumber": "string",
"localLoginDisabled": true,
"pinSession": true,
"isLocked": true,
"syncVersion": 0,
"deliveryTag": 0,
"operationType": "UPSERT"
}`
- [View an example JSON payload](#viewExamplePostJson)
[]
`{
"isEnabled":true,
"forcePwdChange":true,
"pinSession":true,
"username":"exampleuser@lanukcorp.com",
"email":"",
"phoneNumber":"1234567890",
"twoFactorAuthEnabled":false,
"allowLocalLogin":true,
"password":"Admin@123!",
"confirmPassword":"Admin@123!",
"twoFactorAuthType":"",
"roleId":"144118148382065792",
"localLoginDisabled":false
}`
- [View an example response](#postExampleResponse)
[]
`{
"id": "144118148382065795",
"username": "exampleuser@lanukcorp.com",
"roleId": "144118148382065792",
"isEnabled": true,
"forcePwdChange": true,
"twoFactorAuthEnabled": false,
"phoneNumber": "1234567890",
"localLoginDisabled": false,
"pinSession": true,
"isLocked": false,
"syncVersion": "0",
"deliveryTag": "0",
"oneIdentityUser": false
} `
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating Details of an Administrator
To update an administrator:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/administrators/{adminId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `adminId`: The unique identifier of the administrator.
- `microtenantId`: The unique identifier of the Microtenant. If the administrator is within a Microtenant, then this field is required. If the administrator is within the Default Microtenant, then this field must be passed as `0`. To learn more, see [Configuring Microtenant Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145256180497776640/administrators/145256180497778056?microtenantId=145256180497776789`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- `tmpPassword`: The temporary password of the administrator. The password must be at least 8 characters in length, and include at least one uppercase letter, one special character, and one number.
- `username`: This is the login ID for the administrator. It must be an email address, where the domain name matches your company's authentication domain name.
- `email`: (Optional) The email address for the administrator. Updates regarding ZPA are sent to this email address.
- `phoneNumber`: The 10-digit phone number without any hyphens (-). This field is mandatory and is used for password recovery purposes.
- `roleId`: The unique identifier of the role for the administrator. To learn more, see [Managing Administrator Roles Using API](/zpa/managing-administrator-roles-using-api).
- [View the JSON payload](#putJsonPayload)
[]
`{
"microtenantId": 0,
"microtenantName": "string",
"username": "string",
"displayName": "string",
"email": "string",
"timezone": "string",
"password": "string",
"tmpPassword": "string",
"roleId": "string",
"comments": "string",
"languageCode": "string",
"eula": "string",
"groupIds": [
"string"
],
"isEnabled": true,
"forcePwdChange": true,
"twoFactorAuthEnabled": true,
"twoFactorAuthType": "string",
"tokenId": "string",
"phoneNumber": "string",
"localLoginDisabled": true,
"pinSession": true,
"isLocked": true,
"syncVersion": 0,
"deliveryTag": 0,
"operationType": "UPSERT"
}`
A successful response returns code 204, meaning the administrator is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting an Administrator
To delete an administrator:
- Send a DELETE request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/administrators/{adminId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `adminId`: The unique identifier of the administrator.
- `microtenantId`: The unique identifier of the Microtenant. If the administrator is within a Microtenant, then this field is required. If the administrator is within the Default Microtenant, then this field must be passed as `0`. To learn more, see [Configuring Microtenant Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145256180497776640/administrators/145256180497778056?microtenantId=145256180497776789`.
A successful response returns code 204, meaning the administrator is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Adding Field Descriptions
The following table includes available fields you can use for the administrator API use cases:
[](/zpa/configuring-microtenants-using-api)[](/zpa/configuring-zpa-administrators)
[](/zpa/configuring-zpa-administrators)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as 0 when making requests to retrieve data from the Default Microtenant. Pass `microtenantId` as null to retrieve data from all Microtenants associated with the tenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
| tmpPassword | The temporary password of the administrator. The password must be at least 8 characters in length, and include at least one uppercase letter, one special character, and one number. | Yes | String |
| password | The password for the admin. The password must be at least 8 characters in length, and include at least one uppercase letter, one special character, and one number. To learn more, see Configuring ZPA Administrators. | Yes | String |
| username | This is the login ID for the administrator. It must be an email address, where the domain name matches your company's authentication domain name. | Yes | String |
| phoneNumber | The 10-digit phone number without any hyphens (-). This field is mandatory and is used for password recovery purposes. | Yes | Integer |
| forcePwdChange | Forces the admin to reset their password at login if set to `true`. | No | Default: `true`Supported values: `true`, `false` |
| twoFactorAuthEnabled | Allows the admin to use two-factor authentication (2FA) if set to `true`. | No | Default: `true`Supported values: `true`, `false` |
| twoFactorAuthType | The 2FA type. This field is required if `twoFactorAuthEnabled` is set to `true`. To learn more, see Configuring ZPA Administrators. | No | StringThe supported value is `YUBIKEY` |

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