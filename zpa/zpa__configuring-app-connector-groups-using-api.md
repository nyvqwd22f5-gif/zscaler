# Configuring App Connector Groups Using API
Source: https://help.zscaler.com/zpa/configuring-app-connector-groups-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484816.pdf

This article provides information on managing Zscaler Private Access (ZPA) [App Connector groups](/zpa/about-connector-groups) using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Prerequisite API Call
Before creating an App Connector group, you must get the required details of all version profiles. To learn more, see [Obtaining Version Profiles Using API](/zpa/obtaining-version-profile-details-using-api).
[]Creating an App Connector Group
To create an App Connector group:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/appConnectorGroup`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/appConnectorGroup`.
- Use the following JSON payload to create an App Connector group and provide the following information about the App Connector Group:
- `name`: The name of the App Connector group.
- `latitude`: The latitude of the App Connector group.
- `longitude`: The longitude of the App Connector group.
- `location`: The location of the App Connector group.
- `upgradeDay`: App Connectors in this group attempt to update to a newer version of the software during this specified day.
- `upgradeTimeInSecs`: App Connectors in this group attempt to update to a newer version of the software during this specified time.
- [View the JSON payload](#ViewJSON)
[]{
"name": "<App Connector group name>",
"description": "<App Connector group description>",
"upgradeDay": "<upgradeDay>",
"upgradeTimeInSecs": "<upgradeTimeInSecs>",
"latitude": "<latitude>",
"longitude": "<longitude>",
"location": "<location>",
}
- [View the sample JSON payload](#ViewSampleJSON)
[]{
"name": "App Connector group",
"description": "App Connector group in San Jose",
"upgradeDay": "SUNDAY",
"upgradeTimeInSecs": "66600",
"latitude": "37.3382082",
"longitude": "-121.8863286",
"location": "San Jose, CA, USA",
}
- [View an example response](#ViewExample)
[]{
"enabled": true,
"location": "San Jose, CA, USA",
"dnsQueryType": "IPV4_IPV6",
"overrideVersionProfile": false,
"name": "test cg2",
"description": "test cg description",
"upgradeDay": "SUNDAY",
"upgradeTimeInSecs": "81000",
"latitude": "37.3382082",
"longitude": "-121.8863286",
"versionProfileId": "0"
}
A successful response returns code 201, meaning the App Connector group is created. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the App Connector group criteria you want to include in the JSON payload. Refer to the [Adding Field Descriptions](#AddingFieldDescriptions) section for supported values.
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the App Connector group use cases:
-
-
-
[](/zpa/obtaining-version-profile-details-using-api)
[](/zpa/understanding-disaster-recovery)
[](/zpa/about-api-keys)[](/zpa/configuring-microtenants-using-api)[](/zpa/configuring-connectors#createconnectorgroup)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| name | The name of the App Connector group | Yes | String |
| description | The description of the App Connector group | No | String |
| enabled | Whether this App Connector group is enabled or not | No | Default value: `true`Supported values: `true`, `false` |
| dnsQueryType | Whether to enable IPv4 or IPv6, or both, for DNS resolution of all applications in the App Connector group | No | Default: `IPV4_IPV6`Supported values:`IPV4_IPV6``IPV4``IPV6` |
| latitude | The latitude of the App Connector group | Yes | Integer or decimal, with values in the range of -90 to 90 |
| longitude | The longitude of the App Connector group | Yes | Integer or decimal, with values in the range of -180 to 180 |
| location | The location of the App Connector group | Yes | String |
| upgradeDay | App Connectors in this group attempt to update to a newer version of the software during this specified day | No | Default value: `SUNDAY`List of valid days (i.e., Sunday, Monday) |
| upgradeTimeInSecs | App Connectors in this group attempt to update to a newer version of the software during this specified time | No | Default value: 66600Integer in seconds (i.e., -66600). The integer should be greater than or equal to 0 and less than 86400, in 15-minute intervals. |
| overrideVersionProfile | Whether the default version profile of the App Connector group is applied or overridden | No | Default: `false`Supported values: `true`, `false` |
| versionProfileId | ID of the version profile. To learn more, see Obtaining Version Profiles Using API. | Yes, if the value for `overrideVersionProfile` is set to `true` | Any long value in the version profile IDs |
| tcpQuickAckApp | Whether TCP Quick Acknowledgement is enabled or disabled for the application. The `tcpQuickAckApp`, `tcpQuickAckAssistant`, and `tcpQuickAckReadAssistant` fields must all share the same value. | No | Default: `false`Supported values: `true`, `false` |
| tcpQuickAckAssistant | Whether TCP Quick Acknowledgement is enabled or disabled for the application. The `tcpQuickAckApp`, `tcpQuickAckAssistant`, and `tcpQuickAckReadAssistant` fields must all share the same value. | No | Default: `false`Supported values: `true`, `false` |
| tcpQuickAckReadAssistant | Whether TCP Quick Acknowledgement is enabled or disabled for the application. The `tcpQuickAckApp`, `tcpQuickAckAssistant`, and `tcpQuickAckReadAssistant` fields must all share the same value. | No | Default: `false`Supported values: `true`, `false` |
| useInDrMode | Whether or not the App Connector group is designated for disaster recovery | No | Default: `false`Supported values: `true`, `false` |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. Pass `microtenantId` as null to retrieve data from all Microtenants associated with the tenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
| wafDisabled | Whether or not AppProtection is disabled for the App Connector group. To learn more, see Configuring App Connectors. | No | Default: `false`Supported values: `true`, `false` |
[]Getting Details for All App Connector Groups
To get details for all the App Connector groups:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/appConnectorGroup`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057615512764416/appConnectorGroup`.
- [View an example response](#Viewanexampleresponse)
[]{
"totalPages": "1",
"list": [
{
"id": "72057615512764441",
"modifiedTime": "1610747816",
"creationTime": "1553590280",
"modifiedBy": "72057594037928174",
"name": "AWS",
"enabled": true,
"upgradeTimeInSecs": "82800",
"upgradeDay": "SUNDAY",
"location": "Oregon City, OR 97045, USA",
"latitude": "45.3363593",
"longitude": "-122.60484730000002",
"cityCountry": "Oregon City, US",
"countryCode": "US",
"tcpQuickAckApp": false,
"tcpQuickAckAssistant": false,
"tcpQuickAckReadAssistant": false,
"connectors": [
{
"id": "72057615512764537",
"modifiedTime": "1602726801",
"creationTime": "1574304547",
"modifiedBy": "72057615512764423",
"name": "AWS-6",
"fingerprint": "VWMwrlVCgjgltBh+CZJrIjnq22a5n6HOW8uCnSUK1hI=",
"issuedCertId": "952",
"enabled": true,
"upgradeAttempt": "0"
},
{
"id": "72057615512764540",
"modifiedTime": "1608370882",
"creationTime": "1576893934",
"modifiedBy": "-2",
"name": "AWS-7",
"fingerprint": "xMe+zaxrE+tFPCtCbdFyo0d2bkmtDVPUVEOumyUXP10=",
"issuedCertId": "1376",
"enabled": true,
"upgradeAttempt": "0"
}
],
"siemConnectorGroup": false
},
{
"id": "72057615512764449",
"modifiedTime": "1610747816",
"creationTime": "1560278889",
"modifiedBy": "72057594037928174",
"name": "Azure",
"enabled": true,
"upgradeTimeInSecs": "25200",
"upgradeDay": "MONDAY",
"location": "Oregon, USA",
"latitude": "43.8041334",
"longitude": "-120.55420119999997",
"cityCountry": "Brothers, US",
"countryCode": "US",
"siemConnectorGroup": false
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/appConnectorGroup?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/144118148382064655/appConnectorGroup?page=1&pagesize=2`.
- [View an example response](#Viewanexamplepagination)
[]{
"totalPages": "6",
"list": [
{
"id": "144118148382064655",
"modifiedTime": "1611094156",
"creationTime": "1452153594",
"modifiedBy": "72057594037928187",
"name": "AWS Assistants",
"enabled": true,
"versionProfileId": "72057594037928267",
"overrideVersionProfile": true,
"versionProfileName": "Internal - ET Ops QA ",
"versionProfileVisibilityScope": "NONE",
"upgradeTimeInSecs": "28800",
"upgradeDay": "SATURDAY",
"location": "Oregon City, OR 97045, USA",
"latitude": "45.35734290000001",
"longitude": "-122.60675839999999",
"dnsQueryType": "IPV4_IPV6",
"cityCountry": "Oregon City, US",
"countryCode": "US",
"connectors": [
{
"id": "144118148382065437",
"modifiedTime": "1621702855",
"creationTime": "1591139746",
"modifiedBy": "-2",
"name": "*Do not Delete* Lanukcorp AWS Connectors-4",
"fingerprint": "Gvyg1hnlredGtyt7EWyLVRlyinXmXZnknbAfM9lClf4=",
"issuedCertId": "258589",
"enabled": true,
"assistantVersion": {
"id": "144118148382065437",
"modifiedTime": "1649062642",
"creationTime": "1591139749",
"modifiedBy": "72057594037928156",
"expectedVersion": "22.73.4",
"currentVersion": "22.73.4",
"systemStartTime": "1591138972",
"applicationStartTime": "1647711424",
"lastBrokerConnectTime": "1649062642296878",
"lastBrokerDisconnectTime": "1647708499102454",
"brokerId": "72057594037930317",
"restartTimeInSec": "1647708497",
"platform": "el7",
"upgradeStatus": "COMPLETE",
"ctrlChannelStatus": "ZPN_STATUS_AUTHENTICATED",
"latitude": "45.3573429",
"longitude": "-122.606758",
"privateIp": "10.0.1.108",
"publicIp": "51.224.54.1",
"loneWarrior": true,
"mtunnelId": "DuYfuxOT5rxaXyVKEXTH",
"previousVersion": "22.48.2",
"lastUpgradedTime": "1647708563",
"upgradeAttempt": "0",
"sargeVersion": "18.66.2",
"platformDetail": "AWS",
"appConnectorGroupId": "144118148382064655"
},
"upgradeAttempt": "0",
"provisioningKeyId": "154"
}
],
"lssAppConnectorGroup": false
},
{
"id": "144118148382064835",
"modifiedTime": "1611094156",
"creationTime": "1499715985",
"modifiedBy": "72057594037928187",
"name": "Azure Connectors",
"enabled": true,
"versionProfileId": "72057594037928267",
"overrideVersionProfile": true,
"versionProfileName": "Internal - ET Ops QA ",
"versionProfileVisibilityScope": "NONE",
"upgradeTimeInSecs": "28800",
"upgradeDay": "MONDAY",
"location": "California, USA",
"latitude": "36.778261",
"longitude": "-119.41793239999998",
"dnsQueryType": "IPV4_IPV6",
"cityCountry": "Sanger, US",
"countryCode": "US",
"tcpQuickAckApp": false,
"tcpQuickAckAssistant": false,
"tcpQuickAckReadAssistant": false,
"connectors": [
{
"id": "144118148382064836",
"modifiedTime": "1621702841",
"creationTime": "1499716060",
"modifiedBy": "-2",
"name": "Azure Connector-1",
"fingerprint": "Ic7rJNG6HQvjQ7EJj0uR76WBpm6mtCe3JCrLw91WmXE=",
"issuedCertId": "258586",
"enabled": true,
"assistantVersion": {
"id": "144118148382064836",
"modifiedTime": "1649128946",
"creationTime": "1499716065",
"modifiedBy": "72057594037928156",
"expectedVersion": "22.73.4",
"currentVersion": "22.73.4",
"systemStartTime": "1519507264",
"applicationStartTime": "1647708745",
"lastBrokerConnectTime": "1649128946004754",
"lastBrokerDisconnectTime": "1649128888426147",
"brokerId": "72057594037929396",
"restartTimeInSec": "1647708679",
"platform": "el7",
"upgradeStatus": "COMPLETE",
"ctrlChannelStatus": "ZPN_STATUS_AUTHENTICATED",
"latitude": "36.778261",
"longitude": "-119.417932",
"privateIp": "10.0.0.4",
"publicIp": "11.82.14.22",
"loneWarrior": true,
"mtunnelId": "hSpeuLqqbEzPgbTMdzf7",
"previousVersion": "22.48.2",
"lastUpgradedTime": "1647708745",
"upgradeAttempt": "0",
"sargeVersion": "17.20.2",
"platformDetail": "AWS",
"appConnectorGroupId": "144118148382064835"
},
"upgradeAttempt": "0",
"provisioningKeyId": "554"
}
],
"lssAppConnectorGroup": false
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports a search option to search by features and fields. To search by features and fields:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/73186051597795328/appConnectorGroup&search={searchString}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid search string values. The search string values are in the format `fieldName operator fieldValue`. Only search string values that correspond to the values for valid fields and filters are supported. For example, the string `name%20LIKE%20test` is supported for the **Name **filter, using the **Contains **(`LIKE`) operator, for the `test `filter value.
For example: `/mgmtconfig/v1/admin/customers/73186051597795328/appConnectorGroup&search=name%20LIKE%20test`.
- [View an example response](#getAppConnectorGroupsSearch)
[]{
"totalPages": "28",
"totalCount": "28",
"list": [
{
"id": "72057594038011104",
"modifiedTime": "1664486317",
"creationTime": "1620326350",
"modifiedBy": "72057594037982266",
"name": "App_Connector_Test",
"enabled": true,
"versionProfileId": "0",
"overrideVersionProfile": false,
"versionProfileName": "default",
"versionProfileVisibilityScope": "ALL",
"upgradeTimeInSecs": "77400",
"upgradeDay": "SUNDAY",
"location": "3843 Boston Rd, Bronx, NY 10466, USA",
"latitude": "40.88222220000001",
"longitude": "-73.8369444",
"dnsQueryType": "IPV4_IPV6",
"cityCountry": "New York, US",
"countryCode": "US",
"tcpQuickAckApp": false,
"tcpQuickAckAssistant": false,
"tcpQuickAckReadAssistant": false,
"ipAcl": [
"2001:db8:85a3::8a2e:370:7334",
"2001:db8:85a3:1:1:8a2e:370:7334",
"684d:1111:222:3333:4444:5555:6:77",
"2001:db8:3::/64",
"2001:db8:85a3::8a2e:370:7334"
],
"microtenantName": "Default",
"lssAppConnectorGroup": true
}
]
}
If you use the ZPA API PortaI or the [Reference Guide](/zpa/zpa-api/api-developer-reference-guide/reference-guide) to make your API calls, the search field string does not require any characters. For example, `name%20LIKE%20test` is `name LIKE test`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Particular App Connector Group Details
To get details for a particular App Connector group:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/appConnectorGroup/{appConnectorGroupId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `appConnectorGroupId`: The ID of the App Connector group.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/connectorGroup/72057615512764441`.
- [View an example response](#Viewanexampleresponse2)
[]{
"id": "72057615512764441",
"modifiedTime": "1610747816",
"creationTime": "1553590280",
"modifiedBy": "72057594037928174",
"name": "AWS",
"enabled": true,
"upgradeTimeInSecs": "82800",
"upgradeDay": "SUNDAY",
"location": "Oregon City, OR 97045, USA",
"latitude": "45.3363593",
"longitude": "-122.60484730000002",
"cityCountry": "Oregon City, US",
"countryCode": "US",
"tcpQuickAckApp": false,
"tcpQuickAckAssistant": false,
"tcpQuickAckReadAssistant": false,
"connectors": [
{
"id": "72057615512764537",
"modifiedTime": "1602726801",
"creationTime": "1574304547",
"modifiedBy": "72057615512764423",
"name": "AWS-6",
"fingerprint": "VWMwrlVCgjgltBh+CZJrIjnq22a5n6HOW8uCnSUK1hI=",
"issuedCertId": "952",
"enabled": true,
"upgradeAttempt": "0"
},
{
"id": "72057615512764540",
"modifiedTime": "1608370882",
"creationTime": "1576893934",
"modifiedBy": "-2",
"name": "AWS-7",
"fingerprint": "xMe+zaxrE+tFPCtCbdFyo0d2bkmtDVPUVEOumyUXP10=",
"issuedCertId": "1376",
"enabled": true,
"upgradeAttempt": "0",
"platformDetail": "AWS",
}
],
"siemConnectorGroup": false
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating an App Connector Group
To update an App Connector group:
- Provide the updated JSON payload from [Creating an App Connector group](#CreateAppConnectorGroup) and send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/appConnectorGroup/{appConnectorGroupId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `appConnectorGroupId`: The ID of the App Connector group.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/connectorGroup/72057615512764441`.
- [View the JSON payload](#ViewJSON2)
[]{
"name": "<App Connector group name>",
"description": "<App Connector group description>",
"upgradeDay": "<upgradeDay>",
"upgradeTimeInSecs": "<upgradeTimeInSecs>",
"latitude": "<latitude>",
"longitude": "<longitude>",
"location": "<location>",
}
A successful response yields code 204, meaning the App Connector group is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
If an App Connector group is configured using Zscaler Deception, then the update and delete options are unavailable.
Deleting an App Connector Group
To delete an App Connector group:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/appConnectorGroup/{appConnectorGroupId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `appConnectorGroupId`: The ID of the App Connector group.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/connectorGroup/72057615512764441`.
A successful response yields code 204, meaning the App Connector group is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
If an App Connector group is configured using Zscaler Deception, then the update and delete options are unavailable.

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