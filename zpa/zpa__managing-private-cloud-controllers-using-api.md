# Managing Private Cloud Controllers Using API
Source: https://help.zscaler.com/zpa/managing-private-cloud-controllers-using-api
PDF: https://help.zscaler.com/pdf/com/en/1531060.pdf

This article provides information on Private Cloud Controller use cases using APIs. All APIs are rate limited. To learn more, see [About Private Cloud Controllers](/zpa/about-private-cloud-controllers) and [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Updating a Private Cloud Controller
To update a Private Cloud Controller:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/privateCloudController/{privateCloudControllerId}?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `privateCloudControllerId`: The unique identifier of the Private Cloud Controller. To learn more, see [Getting Details of All Private Cloud Controllers](#getAllPccs).
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289397352052031488/privateCloudController/289397352052032375?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following:
- `name`: The name of the Private Cloud Controller.
- `id`: The unique identifier of the Private Cloud Controller.
- [View the JSON payload](#updatePccPayload)
[]
`{
"name":"<Private Cloud Controller name>",
"description":"",
"enabled":true,
"id":"289397352052032375"
}`
Refer to [Adding Field Descriptions](#fieldDescriptions) for supported fields and values.
A successful response returns code 204, meaning the Private Cloud Controller is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details of All Private Cloud Controllers
To get details of all Private Cloud Controllers:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/privateCloudController?page={page}&pagesize={pagesize}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `page`: Specifies the page number.
- `pagesize`: Specifies the page size. If not provided, the default page size is 20. The maximum page size is 500.
For example: `/mgmtconfig/v1/admin/customers/289397352052031488/privateCloudController?page=1&pagesize=20`.
- [View an example response](#getAllPccResponse)
[]
` {
"totalPages": "86",
"totalCount": "86",
"list": [
{
"modifiedTime": "1750655686",
"creationTime": "1745475250",
"modifiedBy": "72057594038834533",
"id": "289397352052032268",
"scopeName": "Default",
"fingerprint": "CqQetS4iWtuGZIRo/4guF1HvRrXazhtnZo48TmdzT4w=",
"issuedCertId": "2128",
"enabled": true,
"name": "ankur-bansal-dfa3a.gcplab.dev.zpath.net",
"nonceId": "933",
"nonceName": "ankur-pcc-key",
"PrivateCloudControllerGroupId": "289397352052032169",
"PrivateCloudControllerGroupName": "ankur-pcc-group",
"signingCert": {
"id": "2526",
"name": "Root"
},
"latitude": "12.9715987",
"longitude": "77.5945627",
"location": "Bengaluru, Karnataka, India",
"siteSpDnsName": "bcpsp-289397352052032268.ddiltest-od.com",
"expectedVersion": "25.44.6",
"currentVersion": "25.47.0-ET-90082-notific-gd6aecbef90",
"previousVersion": "25.46.0-ET-87495-extendi-g3b29a7200b",
"lastUpgradeTime": "1752834531",
"expectedUpgradeTime": "1752244842",
"upgradeStatus": "FAILED",
"controlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"upgradeAttempt": "3",
"lastBrokerConnectTime": "1752834991",
"lastBrokerConnectTimeDuration": "04d 19h 46m 45s",
"lastBrokerDisconnectTime": "1752852335",
"lastBrokerDisconnectTimeDuration": "04d 14h 57m 41s",
"masterLastSyncTime": "1752850800",
"userdbLastSyncTime": "1752834508",
"shardLastSyncTime": "1752835046",
"privateIp": "10.10.10.147",
"publicIp": "34.168.195.122",
"platform": "el9",
"runtimeOS": "Red Hat Enterprise Linux 9.5",
"applicationStartTime": "1752834806",
"platformDetail": "GCP",
"zpnSubModuleUpgradeList": [
{
"id": "289397352052032269",
"modifiedTime": "1745480246",
"creationTime": "1745475309",
"modifiedBy": "72057594037928167",
"entityGid": "289397352052032268",
"entityType": "SITE_CONTROLLER",
"role": "MMDB_GEOIP",
"currentVersion": "20221018"
},
{
"id": "289397352052032270",
"modifiedTime": "1745480246",
"creationTime": "1745475309",
"modifiedBy": "72057594037928167",
"entityGid": "289397352052032268",
"entityType": "SITE_CONTROLLER",
"role": "MMDB_ISP",
"currentVersion": "20221018"
}
],
"sargeUpgradeStatus": "UNKNOWN",
"osUpgradeStatus": "UNKNOWN",
"platformVersion": "NA",
"readOnly": false,
"restrictedEntity": false,
"zscalerManaged": false
}
]
}
`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details for a Particular Private Cloud Controller
To get details for a particular Private Cloud Controller:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/privateCloudController/{privateCloudControllerId}µtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `privateCloudControllerId`: The unique identifier of the Private Cloud Controller. To learn more, see [Getting Details of All Private Cloud Controllers](#getAllPccs).
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289397352052031488/privateCloudController/289397352052032375µtenantId=0`.
- [View an example response](#GetPccExampleResponse)
[]
`{
"creationTime": "1752761344",
"modifiedBy": "3",
"id": "289397352052032375",
"scopeName": "Default",
"fingerprint": "Test__1223",
"enabled": true,
"name": "ankur-pcc-key-1752761344576",
"nonceId": "933",
"nonceName": "ankur-pcc-key",
"privateCloudControllerGroupId": "289397352052032169",
"privateCloudControllerGroupName": "ankur-pcc-group",
"latitude": "12.9715987",
"longitude": "77.5945627",
"location": "Bengaluru, Karnataka, India",
"siteSpDnsName": "bcpsp-289397352052032375.ddiltest-od.com",
"upgradeAttempt": "0",
"readOnly": false,
"restrictedEntity": false,
"zscalerManaged": false
}
`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Restarting a Private Cloud Controller
To restart a Private Cloud Controller:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/privateCloudController/{privateCloudControllerId}/restart?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `privateCloudControllerId`: The unique identifier of the Private Cloud Controller. To learn more, see [Getting Details of All Private Cloud Controllers](#getAllPccs).
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289397352052031488/privateCloudController/289397352052032268/restart?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
A successful response returns code 204, meaning the Private Cloud Controller is restarted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting a Private Cloud Controller
To delete a Private Cloud Controller:
- Send a DELETE request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/privateCloudController/{privateCloudControllerId}µtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `privateCloudControllerId`: The unique identifier of the Private Cloud Controller. To learn more, see [Getting Details of All Private Cloud Controllers](#getAllPccs).
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289397352052031488/privateCloudController/289397352052032377µtenantId=0`.
A successful response returns code 204, meaning the Private Cloud Controller is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the Private Cloud Controller use cases:
[](/zpa/configuring-microtenants-using-api)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| description | The description of the Private Cloud Controller | No | String |
| enabled | Whether or not the Private Cloud Controller is enabled | No | Default: `true`Supported values: `true`, `false` |
| microtenantId | The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
| name | The name of the Private Cloud Controller | Yes | String |
| page | Specifies the page number | No | Integer |
| pagesize | Specifies the page size. If not provided, the default page size is 20. The maximum page size is 500. | No | Integer |

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