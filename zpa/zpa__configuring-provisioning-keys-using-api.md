# Configuring Provisioning Keys Using API
Source: https://help.zscaler.com/zpa/configuring-provisioning-keys-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484956.pdf

This article provides information for managing Zscaler Private Access (ZPA) provisioning keys using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Prerequisite API Calls
Before you can create a provisioning key, you must get the required details for the following:
- Provisioning keys. To learn more, see [Getting Details of All Provisioning Keys](#getProvisioningKeys) and [Getting Details of a Particular Provisiong Key by ID and Type](#getParticularPkey).
- App Connector Groups. To learn more, see [Configuring App Connector Groups Using API](/zpa/configuring-app-connector-groups-using-api#getAppConnectorGroups).
- Private Service Edge Groups. To learn more, see [Configuring ZPA Private Service Edge Groups Using API](/zpa/configuring-zpa-private-service-edge-groups-using-api).
- Enrollment certificates. To learn more, see [Obtaining Enrollment Certificate Details Using API](/zpa/obtaining-enrollment-certificate-details-using-api).
[]Getting Details for All Provisioning Keys
To get details of all provisioning keys:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/associationType/{associationType}/provisioningKey`.
- Provide the following in the request:
- `customerId`: The ZPA tenant ID of the customer.
- `associationType`: The provisioning key for the App Connector group, Private Service Edge group, or Network Connector group. The supported values are `CONNECTOR_GRP`, `SERVICE_EDGE_GRP`, or `NP_ASSISTANT_GRP`.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/associationType/CONNECTOR_GRP/provisioningKey`.
- [View an example response](#ViewExample3)
[]{
"totalPages": "38",
"list": [
{
"id": "6221",
"creationTime": "1618365768",
"modifiedBy": "217246660303024936",
"name": "example_test",
"usageCount": "0",
"maxUsage": "2000",
"autoSign": "1",
"zcomponentId": "217246660303024937",
"enabled": true,
"enrollmentCertName": "Mock Company Root Certificate",
"zcomponentName": "example_test",
"provisioningKey": "3|sample.test.net|yy6CCpQ8M8QUlGKyFUjUZBspPIxR3n3X2loHsRWt9nt0+b9TMdCqKvrkO8sfdnhMb7l",
"enrollmentCertId": "2858",
"appConnectorGroupName": "example_test"
},
{
"id": "6211",
"modifiedTime": "1626298081",
"creationTime": "1617747326",
"modifiedBy": "72057594038008981",
"name": "example_provising_key",
"usageCount": "5",
"maxUsage": "1000",
"autoSign": "1",
"zcomponentId": "217246660303024864",
"enabled": true,
"enrollmentCertName": "Mock Company Root Certificate",
"zcomponentName": "test_connector_group",
"provisioningKey": "3|sample.test.net|7b2hqKIV36K7AUPNBQzrPNh9MK8IZaXItNFWwmXQPGeEDfdMk90buQ/qmrefavlkr6Pv",
"enrollmentCertId": "2858",
"appConnectorGroupName": "test_connector_group"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/associationType/{associationType}/provisioningKey?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer, in the request endpoint.
- `associationType`: The provisioning key for the App Connector group, Private Service Edge group, or Network Connector group. The supported values are `CONNECTOR_GRP`, `SERVICE_EDGE_GRP`, or `NP_ASSISTANT_GRP`.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/associationType/CONNECTOR_GRP/provisioningKey?page=1&pagesize=20.`
- [View an example response](#paginatedResponse)
[]{
"totalPages": "50",
"list": [
{
"id": "6221",
"creationTime": "1618365768",
"modifiedBy": "217246660303024936",
"name": "testPkey",
"usageCount": "0",
"maxUsage": "2000",
"zcomponentId": "217246660303024937",
"enabled": true,
"zcomponentName": "testPkey",
"provisioningKey": "3|test.net|yy6CCpQ8M8QUlGKyFUjUZBspPIxR3n3X2loHsRWt9nt",
"enrollmentCertId": "2858",
"enrollmentCertName": "Test Company Root Certificate"
},
{
"id": "6211",
"modifiedTime": "1647894135",
"creationTime": "1617747326",
"modifiedBy": "3",
"name": "test_provising_key",
"usageCount": "11",
"maxUsage": "1000",
"zcomponentId": "217246660303024864",
"enabled": true,
"zcomponentName": "Test_connector_group",
"provisioningKey": "3|test.net|7b2hqKIV36K7AUPNBQzrPN",
"enrollmentCertId": "2858",
"enrollmentCertName": "Test Company Root Certificate"
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports a search option to search by features and fields. To search by features and fields:
- Send a **GET** request to the following endpoint: `/mgmtconfig/v1/admin/customers/73186051597795328/associationType/{associationType}/provisioningKey&search={searchString}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid search string values. The search string values are in the format `fieldName operator fieldValue`. Only search string values that correspond to the values for valid fields and filters are supported. For example, the string `maxUsage%20EQ%202` is supported for the **Maximum # of App Connectors** filter, using the **Equals **(`EQ`) operator, for the filter value `2`.
For example: `/mgmtconfig/v1/admin/customers/73186051597795328/associationType/CONNECTOR_GRP/provisioningKey&search=maxUsage%20EQ%202`.
- [View an example response](#gettingAllPkeysSearch)
[]{
"totalPages": "1",
"totalCount": "2",
"list": [
{
"id": "8639",
"creationTime": "1620326351",
"modifiedBy": "72057594037987389",
"name": "App_Connector_Test",
"usageCount": "0",
"maxUsage": "2",
"zcomponentId": "72057594038011104",
"enabled": true,
"zcomponentName": "App_Connector_Test",
"provisioningKey": "1|api-f1.dev.zpath.net|nDDqXjr077Iv/ThxVzpnZa2OlPQBJinz5EOeZ1weBeTb42n5/GyDiocPAz/byiZnA3haAe43R8YUMO8lsjwWaxM74SiPmz8EkMyaei2yWYigACY5289WAeR+zSVHk0c4l9tFv4Mxe0YIJB88EcSUENpwA4h0INP00H3s5q/n9s5qWzIgC1Iix4OXgxip/fgAUMIb3w1WfHv5woPJ0kBxSKxKJ5zElTHAbqtsE8Cl8Dobb/tC9yoxpqBys8PgLIRJnmiqyBAykMsBCOqUllz76Ng4Nnr/6TbGTRm1Wzjqc48v+7R9V6VIVk7v6a2/SBevNPxvkTD5BnB+llhkTChTCCal3bCKBBx2Q/NrFjPF",
"enrollmentCertId": "14009",
"enrollmentCertName": "test1"
},
{
"id": "16173",
"modifiedTime": "1636950866",
"creationTime": "1636884834",
"modifiedBy": "72057594038058788",
"name": "kalai2-pk",
"usageCount": "0",
"maxUsage": "2",
"zcomponentId": "72057594038059864",
"enabled": true,
"zcomponentName": "kalai2",
"provisioningKey": "1|api-f8.dev.zpath.net|j1ZdiPJxwjukKf8hzvQ+2uxNZTec/6ct6WxcHLeWHkXTm597Xy2WDvBrTOJaAqpoApXu7qxgPx8IJL7uAwMGJpncHh+v8MB5vdW1ZYAF84gv4j5WyIulAiC1F95j/XIULlTpzD/RYQAVmRfDljeRE7vVUyYHOeL87R5lHtGUtwFyEzciDZR/0AGR3G2Uw+6leeI7l/vrt4MlgE+QaQPInTsOM8PfpDgSUw2NYevXMkwaDb+9wFGEmUzp7rrtYJ9DYihyeJqIrA0gO+XrUPbaAH",
"enrollmentCertId": "14009",
"enrollmentCertName": "test1"
}
]
}
If you use the [Reference Guide](/zpa/zpa-api/api-developer-reference-guide/reference-guide) to make your API calls, the search field string does not require any characters. For example, `maxUsage%20EQ%202` is `maxUsage EQ 2`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details of a Particular Provisioning Key by ID and Type
To get details of a particular provisioning key by ID and type:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/associationType/{associationType}/provisioningKey/{provisioningKeyId}`.
- Provide the following in the request:
- `customerId`: The ZPA tenant ID of the customer.
- `associationType`: The provisioning key for the App Connector group, Private Service Edge group, or Network Connector group. The supported values are `CONNECTOR_GRP`, `SERVICE_EDGE_GRP`, or `NP_ASSISTANT_GRP`.
- `provisioningKeyId`: The ID of the provisioning key.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/associationType/CONNECTOR_GRP/provisioningKey/6211`.
- [View an Example Response](#ViewExample2)
[]{
"id": "6211",
"modifiedTime": "1626298081",
"creationTime": "1617747326",
"modifiedBy": "72057594038008981",
"name": "test_provisioning_key",
"usageCount": "5",
"maxUsage": "1000",
"autoSign": "1",
"zcomponentId": "217246660303024864",
"enabled": true,
"enrollmentCertName": "Mock Company Root Certificate",
"zcomponentName": "test_connector_group",
"provisioningKey": "3|sample.test.net|7b2hqKIV36K7AUPNBQzrPNh9MK8IZaXItNFWwmXQPGeEDfdMk90buQ",
"enrollmentCertId": "2858",
"appConnectorGroupName": "test_connector_group"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Creating a Provisioning Key
To create a provisioning key:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/associationType/{associationType}/provisioningKey`.
- Provide the following in the request:
- `customerId`: The ZPA tenant ID of the customer.
- `associationType`: The provisioning key for the App Connector group, Private Service Edge group, or Network Connector group. The supported values are `CONNECTOR_GRP`, `SERVICE_EDGE_GRP`, or `NP_ASSISTANT_GRP`.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/associationType/CONNECTOR_GRP/provisioningKey`.
- Use the following JSON payload to create a provisioning key and provide the following information about the provisioning key:
- `name`: The name of the provisioning key.
- `maxUsage`: The maximum number of instances where this provisioning key can be used for enrolling an App Connector, Private Service Edge, or Network Connector. To reduce the possibility of compromise, Zscaler recommends setting the maxUsage field to the number of App Connectors, ZPA Private Service Edges, or Network Connectors you plan to deploy immediately.
- `enrollmentCertId`: The ID of the enrollment certificate that can be used for this provisioning key. To learn more, see [Obtaining Enrollment Certificate Details Using API](/zpa/obtaining-enrollment-certificate-details-using-api).
- `exportable`: Indicates if View or Export Provisioning Key After Creation is enabled or disabled. If set to `true`, this option allows you to view, copy, or download the provisioning key after creation. If set to `false`, you cannot enable this option at a later time, and provisioning keys are hidden when sending `GET` requests to retrieve provisioning key details.
- `zcomponentId`: The ID of the existing App Connector, Private Service Edge, or Network Connector.
- [View the JSON payload](#ViewJSON)
[]{
"name": "<Provisioning key name>",
"maxUsage": "<max usage for this key>",
"enrollmentCertId": "<enrollment certificate ID>",
"exportable": "true",
"zcomponentId": "<App Connector, ZPA Private Service Edge ID, or Network Connector ID>"
}
- [View the sample JSON payload](#ViewSampleJSON)
[]{
"name": "App Connector Provisioning Key",
"maxUsage": "300",
"enrollmentCertId": "22115",
"exportable": "true",
"zcomponentId": "217306507451045314"
}
- [View an example response](#ViewExample)
[]{
"id": "13191",
"creationTime": "1632411234",
"modifiedBy": "72057594038052595",
"name": "Test App Connector Provisioning Key",
"usageCount": "0",
"maxUsage": "300",
"zcomponentId": "72057594038009372",
"enabled": true,
"provisioningKey": "1|api-develop.sample.zpath.net|b+4GLZRQ6VvCJjgQ9GTwZXbjm55FgTCCXkfgEdy4m8+wEY1b2UMrhHLERsEVJJ5YJ/T9du2H+8Z+txHC5rpUykuA72nyLTDK+",
"exportable": "true",
"enrollmentCertId": "14009"
}
A successful response returns code 201, meaning the provisioning key is created. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the provisioning key criteria you want to include in the JSON payload. Refer to the [Adding Field Descriptions](#AddingFieldDescriptions) section for supported values.
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the provisioning key use cases:
[](/zpa/obtaining-enrollment-certificate-details-using-api)[](/zpa/about-api-keys)[](/zpa/configuring-microtenants-using-api)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| name | Name of the provisioning key | Yes | String |
| enabled | Whether the provisioning key is enabled or not | No | Default: `true`Supported values: `true`, `false` |
| exportable | Indicates if View or Export Provisioning Key After Creation is enabled or disabled. If set to `true`, this option allows you to view, copy, or download the provisioning key after creation. If set to `false`, you cannot enable this option at a later time, and provisioning keys are hidden when sending `GET` requests to retrieve provisioning key details. If exportable is not passed in the payload, then the View or Export Provisioning Key After Creation option is considered enabled, and exportable is set to true by default. | No | Default: `true`Supported values: `true`, `false` |
| maxUsage | The maximum number of instances where this provisioning key can be used for enrolling an App Connector, ZPA Private Service Edge, or Network Connector. To reduce the possibility of compromise, Zscaler recommends setting the `maxUsage` field to the number of App Connectors, ZPA Private Service Edges, or Network Connectors you plan to deploy immediately. You can enter a value greater than `1` when sending a `PUT` request to update a provisioning key. This results in an audit log with the Nonce MaxUsage Increment value for the Action. | Yes | Integer |
| usageCount | The provisioning key utilization count | No | Integer |
| enrollmentCertId | ID of the enrollment certificate that can be used for this provisioning key. To learn more, see Obtaining Enrollment Certificate Details Using API. | Yes | Integer. ID of the existing enrollment certificate that has the private key |
| zcomponentId | ID of the existing App Connector or ZPA Private Service Edge Group | Yes | Integer |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. Pass `microtenantId` as null to retrieve data from all Microtenants associated with the tenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
Updating a Provisioning Key
To update a provisioning key:
- Use the JSON payload from [Creating a Provisioning Key](#CreatePkey).
- Send a `PUT` request to the following endpoint: /`mgmtconfig/v1/admin/customers/{customerId}/associationType/{associationType}/provisioningKey/{provisioningKeyId}`.
-
Provide the following in the request:
- `customerId`: The ZPA tenant ID of the customer.
- `associationType`: The provisioning key for the App Connector group, Private Service Edge group, or Network Connector group. The supported values are `CONNECTOR_GRP`, `SERVICE_EDGE_GRP`, or `NP_ASSISTANT_GRP`.
- `provisioningKeyId`: The ID of the provisioning key.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/associationType/CONNECTOR_GRP/provisioningKey/6211`.
- Use the following JSON payload to create a provisioning key and provide the following information about the provisioning key:
- `name`: The name of the provisioning key.
- `maxUsage`: The maximum number of instances where this provisioning key can be used for enrolling an App Connector, ZPA Private Service Edge, or Network Connector. To reduce the possibility of compromise, Zscaler recommends setting the `maxUsage` field to the number of App Connectors, ZPA Private Service Edges, or Network Connectors you plan to deploy immediately. You can enter a value greater than `1` when sending a `PUT` request to update a provisioning key. This results in an audit log with the Nonce MaxUsage Increment value for the Action.
- `enrollmentCertId`: The ID of the enrollment certificate that can be used for this provisioning key. To learn more, see [Obtaining Enrollment Certificate Details Using API](/zpa/obtaining-enrollment-certificate-details-using-api).
-
`exportable`: Indicates if View or Export Provisioning Key After Creation is enabled or disabled. If set to `true`, this option allows you to view, copy, or download the provisioning key after creation. If set to `false`, you cannot enable this option at a later time, and provisioning keys are hidden when sending `GET` requests to retrieve provisioning key details.
If `exportable` is not passed in the payload, then the View or Export Provisioning Key After Creation option is considered enabled, and exportable is set to `true` by default.
- `zcomponentId`: The ID of the existing App Connector, ZPA Private Service Edge, or Network Connector.
- [View the JSON payload](#ViewJSON2)
[]{
"name": "<Provisioning key name>",
"maxUsage": "<max usage for this key>",
"enrollmentCertId": "<enrollment cert id>",
"exportable": "true",
"zcomponentId": "<connector/service edge group id>"
}
A successful response returns code 204, meaning the provisioning key is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
If a provisioning key is configured using Zscaler Deception, then the update and delete options are unavailable.
Deleting a Provisioning Key
To delete a provisioning key:
- Send a `DELETE` request to the following endpoint: /`mgmtconfig/v1/admin/customers/{customerId}/associationType/{associationType}/provisioningKey/{provisioningKeyId}`.
- Provide the following in the request:
- `customerId`: The ZPA tenant ID of the customer.
- `associationType`: The provisioning key for the App Connector group, Private Service Edge group, or Network Connector group. The supported values are `CONNECTOR_GRP`, `SERVICE_EDGE_GRP`, or `NP_ASSISTANT_GRP`.
- `provisioningKeyId`: The ID of the provisioning key.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/associationType/CONNECTOR_GRP/provisioningKey/6211`.
A successful response returns code 204, meaning the provisioning key is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
If a provisioning key is configured using Zscaler Deception, then the update and delete options are unavailable.

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