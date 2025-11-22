# Managing App Connectors Using API
Source: https://help.zscaler.com/zpa/managing-app-connectors-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484941.pdf

This article provides information about managing Zscaler Private Access (ZPA) [App Connector](/zpa/about-connectors)s using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Getting Details for a Particular App Connector
To get details for a particular App Connector:
- Send a `GET` request to the following endpoint in the connector-controller: `/mgmtconfig/v1/admin/customers/{customerId}/connector/{connectorId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `connectorId`: The App Connector ID of the customer.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/connector/217246660303024871`.
- [View an example response](#ViewExample)
[]{
"id": "217246660303024871",
"modifiedTime": "1617841545",
"creationTime": "1617841545",
"modifiedBy": "-2",
"name": "example_provising_key-2",
"fingerprint": "TQ0iesqrg2CwSD/CyyP/Tdb4XpEid0o/c8v9yTiJZVE=",
"issuedCertId": "10723",
"enabled": true,
"upgradeAttempt": "0",
"location": "British Columbia, Canada",
"provisioningKeyId": "6211",
"provisioningKeyName": "example_provising_key",
"enrollmentCert": {
"id": "2858",
"name": "Mock Company Root Certificate"
},
"appConnectorGroupId": "217246660303024864",
"appConnectorGroupName": "example_connector_group"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details for All App Connectors
To get details for all App Connectors:
- Send a `GET` request to the following endpoint in the connector-controller: `/mgmtconfig/v1/admin/customers/{customerId}/connector`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/connector`.
- [View an example response](#ViewExample2)
[] {
"totalPages": "168",
"list": [
{
"id": "217246660303024865",
"modifiedTime": "1617747782",
"creationTime": "1617747781",
"modifiedBy": "-2",
"name": "example_provising_key-1",
"fingerprint": "ypAytG0R89+86b/HJEP3C86SJNiEjKLMXZGi7UzC070=",
"issuedCertId": "10718",
"enabled": true,
"currentVersion": "21.67.2-5-gc17a10071-dirty",
"upgradeStatus": "UNKNOWN",
"controlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"upgradeAttempt": "0",
"lastBrokerConnectTime": "1617750694",
"lastBrokerConnectTimeDuration": "132d 19h 50m 43s",
"lastBrokerDisconnectTime": "1617751234",
"lastBrokerDisconnectTimeDuration": "132d 19h 41m 43s",
"platform": "osx20",
"latitude": "53.7266683",
"longitude": "-127.647621",
"location": "British Columbia, Canada",
"provisioningKeyId": "6211",
"provisioningKeyName": "example_provising_key",
"enrollmentCert": {
"id": "2858",
"name": "Mock Company Root Certificate"
},
"appConnectorGroupId": "217246660303024864",
"appConnectorGroupName": "example_connector_group"
},
{
"id": "217246660303024871",
"modifiedTime": "1617841545",
"creationTime": "1617841545",
"modifiedBy": "-2",
"name": "example_provising_key-2",
"fingerprint": "TQ0iesqrg2CwSD/CyyP/Tdb4XpEid0o/c8v9yTiJZVE=",
"issuedCertId": "10723",
"enabled": true,
"upgradeAttempt": "0",
"location": "British Columbia, Canada",
"platformDetail": "ESXi",
"provisioningKeyId": "6211",
"provisioningKeyName": "example_provising_key",
"enrollmentCert": {
"id": "2858",
"name": "Mock Company Root Certificate"
},
"appConnectorGroupId": "217246660303024864",
"appConnectorGroupName": "example_connector_group"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
To search for App Connectors that last connected with the ZPA Public Service Edge, use `search=lastBrokerConnectTimeDuration LT (N)`, where (`N`) equals the days (d), hours (h), minutes (m), and seconds (s) in integers.
To search for all App Connectors that last disconnected with the ZPA Public Service Edge, use `search=lastBrokerDisconnectTimeDuration LT (N)`, where `(N)` equals the days (d), hours (h), minutes (m), and seconds (s) in integers.
For example, to search for App Connectors that last connected with the ZPA Public Service Edge within 150 days, use `search=lastBrokerConnectTimeDuration LT 150d`.
The following filters are supported for use with the search parameter:
- `lastBrokerConnectTimeDuration`: Filters for App Connectors that last connected with the ZPA Public Service Edge.
- `lastBrokerDisconnectTimeDuration`: Filters for App Connectors that last disconnected with the ZPA Public Service Edge.
- `controlChannelStatus`: Filters for inactive App Connectors.
- `currentVersion`: Filters for the current version of the App Connector.
- `expectedVersion`: Filters for the expected version of the App Connector based on the associated version profile.
For example, to search for an App Connector that has `controlChannelStatus` as disconnected with the last disconnected time greater than (N) days, use `controlChannelStatus EQ ZPN_STATUS_DISCONNECTED AND lastBrokerDisconnectTimeDuration GT 15d`.
- [View an example response](#ViewExample3)
[]{
"totalPages": "128",
"list": [
{
"id": "217246660303024865",
"modifiedTime": "1617747782",
"creationTime": "1617747781",
"modifiedBy": "-2",
"name": "example_provising_key-1",
"fingerprint": "ypAytG0R89+86b/HJEP3C86SJNiEjKLMXZGi7UzC070=",
"issuedCertId": "10718",
"enabled": true,
"currentVersion": "21.67.2-5-gc17a10071-dirty",
"upgradeStatus": "UNKNOWN",
"controlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"upgradeAttempt": "0",
"lastBrokerConnectTime": "1617750694",
"lastBrokerConnectTimeDuration": "181d 13h 38m 46s",
"lastBrokerDisconnectTime": "1617751234",
"lastBrokerDisconnectTimeDuration": "181d 13h 29m 46s",
"platform": "osx20",
"latitude": "53.7266683",
"longitude": "-127.647621",
"location": "British Columbia, Canada",
"provisioningKeyId": "6211",
"provisioningKeyName": "example_provising_key",
"enrollmentCert": {
"id": "2858",
"name": "Mock Company Root Certificate"
},
"appConnectorGroupId": "217246660303024864",
"appConnectorGroupName": "example_connector_group"
},
{
"id": "217246660303025075",
"modifiedTime": "1622502016",
"creationTime": "1622502016",
"modifiedBy": "-2",
"name": "example_provising_key-4",
"fingerprint": "TkL50KRJxbkaCEOLtkS/Exv9qeUoHcuMtTHfr/gS8FQ=",
"issuedCertId": "10766",
"enabled": true,
"currentVersion": "21.172.1-703-g4f9451e18",
"previousVersion": "21.172.1-703-g9cedf7b87-dirty",
"lastUpgradeTime": "1628190895",
"upgradeStatus": "UNKNOWN",
"controlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"upgradeAttempt": "0",
"lastBrokerConnectTime": "1628206943",
"lastBrokerConnectTimeDuration": "60d 13h 07m 56s",
"lastBrokerDisconnectTime": "1628209139",
"lastBrokerDisconnectTimeDuration": "60d 12h 31m 21s",
"platform": "osx20",
"latitude": "53.7266683",
"longitude": "-127.647621",
"location": "British Columbia, Canada",
"platformDetail": "ESXi",
"provisioningKeyId": "6211",
"provisioningKeyName": "example_provising_key",
"enrollmentCert": {
"id": "2858",
"name": "Mock Company Root Certificate"
},
"appConnectorGroupId": "217246660303024864",
"appConnectorGroupName": "example_connector_group"
}
]
}
{
"totalPages": "128",
"list": [
{
"id": "217246660303024865",
"modifiedTime": "1617747782",
"creationTime": "1617747781",
"modifiedBy": "-2",
"name": "example_provising_key-1",
"fingerprint": "ypAytG0R89+86b/HJEP3C86SJNiEjKLMXZGi7UzC070=",
"issuedCertId": "10718",
"enabled": true,
"currentVersion": "21.67.2-5-gc17a10071-dirty",
"upgradeStatus": "UNKNOWN",
"controlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"upgradeAttempt": "0",
"lastBrokerConnectTime": "1617750694",
"lastBrokerConnectTimeDuration": "181d 13h 38m 46s",
"lastBrokerDisconnectTime": "1617751234",
"lastBrokerDisconnectTimeDuration": "181d 13h 29m 46s",
"platform": "osx20",
"latitude": "53.7266683",
"longitude": "-127.647621",
"location": "British Columbia, Canada",
"provisioningKeyId": "6211",
"provisioningKeyName": "example_provising_key",
"enrollmentCert": {
"id": "2858",
"name": "Mock Company Root Certificate"
},
"appConnectorGroupId": "217246660303024864",
"appConnectorGroupName": "example_connector_group"
},
{
"id": "217246660303025075",
"modifiedTime": "1622502016",
"creationTime": "1622502016",
"modifiedBy": "-2",
"name": "example_provising_key-4",
"fingerprint": "TkL50KRJxbkaCEOLtkS/Exv9qeUoHcuMtTHfr/gS8FQ=",
"issuedCertId": "10766",
"enabled": true,
"currentVersion": "21.172.1-703-g4f9451e18",
"previousVersion": "21.172.1-703-g9cedf7b87-dirty",
"lastUpgradeTime": "1628190895",
"upgradeStatus": "UNKNOWN",
"controlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"upgradeAttempt": "0",
"lastBrokerConnectTime": "1628206943",
"lastBrokerConnectTimeDuration": "60d 13h 07m 56s",
"lastBrokerDisconnectTime": "1628209139",
"lastBrokerDisconnectTimeDuration": "60d 12h 31m 21s",
"platform": "osx20",
"latitude": "53.7266683",
"longitude": "-127.647621",
"location": "British Columbia, Canada",
"provisioningKeyId": "6211",
"provisioningKeyName": "example_provising_key",
"enrollmentCert": {
"id": "2858",
"name": "Mock Company Root Certificate"
},
"appConnectorGroupId": "217246660303024864",
"appConnectorGroupName": "example_connector_group"
}
]
}
The following rule tag operations are allowed:
- `GT`: Greater than
- `LT`: Less than
- `GTEQ`: Greater than or equal to
- `LTEQ`: Less than or equal to
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint in the connector-controller: `/mgmtconfig/v1/admin/customers/{customerId}/connector?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/connector?page=1&pagesize=20.`
- [View an example response](#paginationResponse)
[]{
"totalPages": "1",
"list": [
{
"id": "144118148382064836",
"modifiedTime": "1621702841",
"creationTime": "1499716060",
"modifiedBy": "-2",
"name": "Azure Connector-1",
"fingerprint": "Ic7rJNG6HQvjQ7EJj0uR76WBpm6mtCe3JCrLw91WmXE=",
"issuedCertId": "258586",
"enabled": true,
"expectedVersion": "22.73.4",
"currentVersion": "22.73.4",
"previousVersion": "22.48.2",
"lastUpgradeTime": "1647708745",
"upgradeStatus": "COMPLETE",
"controlChannelStatus": "ZPN_STATUS_AUTHENTICATED",
"upgradeAttempt": "0",
"ctrlBrokerName": "US-CA-9396",
"lastBrokerConnectTime": "1649128946",
"lastBrokerConnectTimeDuration": "17h 32m 50s",
"sargeVersion": "17.20.2",
"lastBrokerDisconnectTime": "1649128888",
"lastBrokerDisconnectTimeDuration": "17h 33m 48s",
"privateIp": "10.0.0.4",
"publicIp": "10.0.0.1",
"platform": "el7",
"applicationStartTime": "1647708745",
"latitude": "36.778261",
"longitude": "-119.417932",
"location": "California, USA",
"platformDetail": "Azure",
"provisioningKeyId": "554",
"provisioningKeyName": "Azure Connector",
"enrollmentCert": {
"id": "117",
"name": "Connector"
},
"appConnectorGroupId": "144118148382064835",
"appConnectorGroupName": "Azure Connectors"
},
{
"id": "144118148382065437",
"modifiedTime": "1621702855",
"creationTime": "1591139746",
"modifiedBy": "-2",
"name": "*Do not Delete* Lanukcorp AWS Connectors-4",
"fingerprint": "Gvyg1hnlredGtyt7EWyLVRlyinXmXZnknbAfM9lClf4=",
"issuedCertId": "258589",
"enabled": true,
"expectedVersion": "22.73.4",
"currentVersion": "22.73.4",
"previousVersion": "22.48.2",
"lastUpgradeTime": "1647708563",
"upgradeStatus": "COMPLETE",
"controlChannelStatus": "ZPN_STATUS_AUTHENTICATED",
"upgradeAttempt": "0",
"ctrlBrokerName": "US-WA-0317",
"lastBrokerConnectTime": "1649062642",
"lastBrokerConnectTimeDuration": "01d 11h 57m 54s",
"sargeVersion": "18.66.2",
"lastBrokerDisconnectTime": "1647708499",
"lastBrokerDisconnectTimeDuration": "17d 04h 06m 57s",
"privateIp": "10.0.1.108",
"publicIp": "52.222.36.1",
"platform": "el7",
"applicationStartTime": "1647711424",
"latitude": "45.3573429",
"longitude": "-122.606758",
"location": "Oregon City, OR 97045, USA",
"provisioningKeyId": "154",
"provisioningKeyName": "*Do not Delete* Lanukcorp AWS Connectors",
"enrollmentCert": {
"id": "117",
"name": "Connector"
},
"appConnectorGroupId": "144118148382064655",
"appConnectorGroupName": "AWS Assistants"
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports a search option to search by features and fields. To search by features and fields:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/73186051597795328/connector&search={searchString}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid search string values. The search string values are in the format `fieldName operator fieldValue`. Only search string values that correspond to the values for valid fields and filters are supported. For example, the string `enabled%EQ%true` is supported for the **Status** filter, using the **Equals **(`EQ`) operator, for the **True **(`Enabled`) filter value.
For example: `/mgmtconfig/v1/admin/customers/73186051597795328/connector&search=enabled%20EQ%20true`.
- [View an example response](#getAppConnectorGroupsSearch)
[]{
"totalPages": "16",
"totalCount": "16",
"list": [
{
"id": "72057594038053055",
"modifiedTime": "1662757554",
"creationTime": "1633089623",
"modifiedBy": "72057594038058534",
"name": "Example App Connector",
"description": "Example description",
"fingerprint": "ZWM5OWM1ODcwMzcxMDJmOGY2Mzc3YjE5NjUyODJhOGUyZTAwNWMwZjhkN2",
"enabled": true,
"upgradeAttempt": "0",
"location": "1234 Example Location",
"microtenantName": "Default",
"provisioningKeyId": "8588",
"provisioningKeyName": "Abct",
"appConnectorGroupId": "72057594038009372",
"appConnectorGroupName": "Example App Connector Group"
}
]
}
If you use the ZPA API Portal or the [Reference Guide](/zpa/zpa-api/api-developer-reference-guide/reference-guide) to make your API calls, the search field string does not require any characters. For example, `enabled%20EQ%20true` is `enabled EQ true`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating an App Connector
To update an App Connector:
- Send a `PUT` request to the following endpoint in the connector-controller: `/mgmtconfig/v1/admin/customers/{customerId}/connector/{connectorId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `connectorId`: The App Connector ID of the customer.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/connector/217246660303024871`.
- Use the following JSON payload to update an App Connector and provide the following information about the App Connector:
- `name`: Name of the App Connector.
- `description`: Description of the App Connector.
- `enabled`: Whether the App Connector is enabled or not.
- [View the JSON payload](#ViewJSON)
[]{
"description": "Test Connector",
"enabled": true,
"name": "Test_Connector",
}
Refer to the [Adding Field Descriptions](#AddingFieldDescriptions) section for supported values.
A successful response yields code 204, meaning the App Connector is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
If an App Connector is configured using Zscaler Deception, then the update and delete options are unavailable.
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the App Connector use cases:
[](/zpa/about-api-keys)[](/zpa/configuring-microtenants-using-api)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| name | Name of the App Connector | No | String |
| description | Description of the App Connector | No | String |
| enabled | Whether the App Connector is enabled or not | No | Default: `true`Supported values: `true`, `false` |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. Pass `microtenantId` as null to retrieve data from all Microtenants associated with the tenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
Deleting an App Connector
To delete an App Connector:
- Send a `DELETE` request to the following endpoint in the connector-controller: `/mgmtconfig/v1/admin/customers/{customerId}/connector/{connectorId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `connectorId`: The App Connector ID of the customer.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/connector/217246660303024871`.
A successful response yields code 204, meaning the App Connector is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
If an App Connector is configured using Zscaler Deception, then the update and delete options are unavailable.
Bulk Deleting App Connectors
To bulk delete App Connectors:
- Provide the following JSON payload with the App Connector IDs you wish to bulk delete, then send a `POST` request to the following endpoint in the connector-controller: `/mgmtconfig/v1/admin/customers/{customerId}/connector/bulkDelete`.
- [View the JSON payload](#ViewJSON2)
[]{
"ids": [
"<AppConnectorId>",
"<AppConnectorId2>"
]
}
- [View the example JSON payload](#ViewExampleJSON)
[]{
"ids": [
"217246660303024723",
"217246660303024725"
]
}
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/connector/bulkDelete`.
A successful response yields code 200, meaning the App Connectors are deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).

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