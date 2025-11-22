# Managing ZPA Private Service Edges Using API
Source: https://help.zscaler.com/zpa/managing-zpa-private-service-edges-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484961.pdf

This article provides information for managing Zscaler Private Access (ZPA) [Private Service Edges](/zpa/about-zpa-private-service-edges) using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Getting Details for All Private Service Edges
To get details for all Private Service Edges:
- Send a `GET` request to the following endpoint in the service-edge-controller: `/mgmtconfig/v1/admin/customers/{customerId}/serviceEdge`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217246660302995456/serviceEdge`.
- [View an example response](#ViewExample2)
[]{
"totalPages": "54",
"list": [
{
"id": "217246660303024723",
"modifiedTime": "1607915744",
"creationTime": "1607887364",
"modifiedBy": "72057594037950342",
"name": "1 mp pb-1",
"fingerprint": "asbErAYZ7/mNUcQhRPd8XFMIRutWjMsWrfot1dDrOOY=",
"issuedCertId": "10591",
"enabled": true,
"listenIps": [
"192.168.255.2"
],
"publishIps": [
"192.168.255.2"
],
"latitude": "37.4181643",
"longitude": "-121.9531325",
"location": "Example Way, San Jose, CA 95134, USA",
"currentVersion": "21.67.2-2-g1a8538e55-dirty",
"previousVersion": "21.26.0-91-g018c50e7f-dirty",
"lastUpgradeTime": "1617857786",
"upgradeStatus": "UNKNOWN",
"controlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"upgradeAttempt": "0",
"lastBrokerConnectTime": "1618417904",
"lastBrokerConnectTimeDuration": "128d 06h 52m 31s",
"lastBrokerDisconnectTime": "1618419214",
"lastBrokerDisconnectTimeDuration": "128d 06h 30m 40s",
"platform": "osx20",
"platformDetail": "ESXi",
"provisioningKeyId": "6115",
"provisioningKeyName": "1 mp pb",
"serviceEdgeGroupId": "217246660303024722",
"serviceEdgeGroupName": "1 mp pb group",
"enrollmentCert": {
"id": "2858",
"name": "Mock Company Root Certificate"
}
},
{
"id": "217246660303024725",
"modifiedTime": "1607918700",
"creationTime": "1607918700",
"modifiedBy": "3",
"name": "1 mp pb-2",
"fingerprint": "37As8jQglTtuEr5XXkb1MuMHXeYSLTG0+OLeJneupJE=",
"issuedCertId": "10593",
"enabled": true,
"latitude": "37.4181643",
"longitude": "-121.9531325",
"location": "Example Way, San Jose, CA 95134, USA",
"expectedVersion": "20.40.2",
"currentVersion": "20.148.2-59-gb3abc04-asan",
"upgradeStatus": "FAILED",
"controlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"upgradeAttempt": "1",
"ctrlBrokerName": "broker2a.pdx2",
"lastBrokerConnectTime": "1607918775",
"lastBrokerConnectTimeDuration": "249d 19h 18m ",
"lastBrokerDisconnectTime": "1607918775",
"lastBrokerDisconnectTimeDuration": "249d 19h 18m ",
"platform": "el7",
"platformDetail": "AWS",
"provisioningKeyId": "6115",
"provisioningKeyName": "1 mp pb",
"serviceEdgeGroupId": "217246660303024722",
"serviceEdgeGroupName": "1 mp pb group",
"enrollmentCert": {
"id": "2858",
"name": "Mock Company Root Certificate"
}
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/serviceEdge?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/serviceEdge?page=1&pagesize=2.`
- [View an example response](#paginatedResponse)
[]{
"totalPages": "60",
"list": [
{
"id": "217246660303024723",
"modifiedTime": "1607915744",
"creationTime": "1607887364",
"modifiedBy": "72057594037950342",
"name": "Test Service Edge",
"fingerprint": "asbErAYZ7/mNUcQhRPd8XFMIRutWjMsWrfot1dDrOOY=",
"issuedCertId": "10591",
"enabled": true,
"listenIps": [
"192.168.255.2"
],
"publishIps": [
"192.168.255.2"
],
"latitude": "37.4181643",
"longitude": "-121.9531325",
"location": "120 Holger Way, San Jose, CA 95134, USA",
"currentVersion": "21.67.2-2-g1a8538e55-dirty",
"previousVersion": "21.26.0-91-g018c50e7f-dirty",
"lastUpgradeTime": "1617857786",
"upgradeStatus": "UNKNOWN",
"controlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"upgradeAttempt": "0",
"lastBrokerConnectTime": "1618417904",
"lastBrokerConnectTimeDuration": "356d 22h 58m 54s",
"lastBrokerDisconnectTime": "1618419214",
"lastBrokerDisconnectTimeDuration": "356d 22h 37m 03s",
"platform": "osx20",
"platformDetail": "ESXi",
"provisioningKeyId": "6115",
"provisioningKeyName": "Test Pkey",
"serviceEdgeGroupId": "217246660303024722",
"serviceEdgeGroupName": "Test Service Edge Group",
"enrollmentCert": {
"id": "2858",
"name": "Mock Company Root Certificate"
}
},
{
"id": "217246660303024725",
"modifiedTime": "1607918700",
"creationTime": "1607918700",
"modifiedBy": "3",
"name": "Test Service Edge 2",
"fingerprint": "37As8jQglTtuEr5XXkb1MuMHXeYSLTG0+OLeJneupJE=",
"issuedCertId": "10593",
"enabled": true,
"latitude": "37.4181643",
"longitude": "-121.9531325",
"location": "120 Holger Way, San Jose, CA 95134, USA",
"expectedVersion": "20.40.2",
"currentVersion": "20.148.2-59-gb3abc04-asan",
"upgradeStatus": "FAILED",
"controlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"upgradeAttempt": "1",
"ctrlBrokerName": "broker2a.pdx2",
"lastBrokerConnectTime": "1607918775",
"lastBrokerConnectTimeDuration": "478d 11h 24m 22s",
"lastBrokerDisconnectTime": "1607918775",
"lastBrokerDisconnectTimeDuration": "478d 11h 24m 22s",
"platform": "el7",
"platformDetail": "ESXi",
"provisioningKeyId": "6115",
"provisioningKeyName": "Test Pkey 2",
"serviceEdgeGroupId": "217246660303024722",
"serviceEdgeGroupName": "Test Service Edge Group 2",
"enrollmentCert": {
"id": "2858",
"name": "Mock Company Root Certificate"
}
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports a search option to search by features and fields. To search by features and fields:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/73186051597795328/serviceEdge&search={searchString}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid search string values. The search string values are in the format `fieldName operator fieldValue`. Only search string values that correspond to the values for valid fields and filters are supported. For example, the string `name%20LIKE%20test` is supported for the **Name **filter, using the **Contains** (`LIKE`) operator, for the filter value `test`.
For example: `/mgmtconfig/v1/admin/customers/73186051597795328/serviceEdge&search=name%20LIKE%20test`.
- [View an example response](#gettingAllPsesSearch)
[]{
"totalPages": "1",
"totalCount": "1",
"list": [
{
"id": "72057594038079655",
"modifiedTime": "1663627925",
"creationTime": "1653333859",
"modifiedBy": "72057594038078999",
"name": "test-service-edge-1653333859596",
"fingerprint": "Od92F7BxT619g5uRTNAX/oUfbSX6jAMD8NCtau0iYbk=",
"issuedCertId": "27972",
"enabled": true,
"latitude": "17.39869",
"longitude": "78.3557962",
"location": "My Home Avatar Rd, Narsingi, Telangana 500075, India",
"expectedVersion": "22.137.0",
"currentVersion": "21.172.4-1009-g0c4b138-dirty",
"upgradeStatus": "FAILED",
"controlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"upgradeAttempt": "0",
"ctrlBrokerName": "broker2.ashekar.dev.zpath.net",
"lastBrokerConnectTime": "1653333862",
"lastBrokerConnectTimeDuration": "202d 22h 05m 59s",
"lastBrokerDisconnectTime": "1653350481",
"lastBrokerDisconnectTimeDuration": "202d 17h 29m ",
"platform": "el7",
"platformDetail": "ESXi",
"microtenantName": "Default",
"provisioningKeyId": "57274",
"provisioningKeyName": "test-service-edge",
"serviceEdgeGroupId": "72057594038009373",
"serviceEdgeGroupName": "Test Broker",
"enrollmentCert": {
"id": "14009",
"name": "test1"
}
}
]
}
If you use the ZPA API PortaI or the [Reference Guide](/zpa/zpa-api/api-developer-reference-guide/reference-guide) to make your API calls, the search field string does not require any characters. For example, `name%20LIKE%20test` is `name LIKE test`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details for a Particular Private Service Edge
To get details for a particular Private Service Edge:
- Send a `GET` request to the following endpoint in the service-edge-controller: `/mgmtconfig/v1/admin/customers/{customerId}/serviceEdge/{serviceEdgeId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `serviceEdgeId`: The Private Service Edge ID of the customer.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/serviceEdge/217246660303024723`.
- [View an example response](#ViewExample)
[]{
"id": "217246660303024723",
"modifiedTime": "1607915744",
"creationTime": "1607887364",
"modifiedBy": "72057594037950342",
"name": "1 mp pb-1",
"fingerprint": "asbErAYZ7/mNUcQhRPd8XFMIRutWjMsWrfot1dDrOOY=",
"issuedCertId": "10591",
"enabled": true,
"listenIps": [
"192.168.255.2"
],
"publishIps": [
"192.168.255.2"
],
"latitude": "37.4181643",
"longitude": "-121.9531325",
"location": "Example Way, San Jose, CA 95134, USA",
"currentVersion": "21.67.2-2-g1a8538e55-dirty",
"previousVersion": "21.26.0-91-g018c50e7f-dirty",
"lastUpgradeTime": "1617857786",
"upgradeStatus": "UNKNOWN",
"controlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"upgradeAttempt": "0",
"lastBrokerConnectTime": "1618417904",
"lastBrokerConnectTimeDuration": "131d 01h 55m 13s",
"lastBrokerDisconnectTime": "1618419214",
"lastBrokerDisconnectTimeDuration": "131d 01h 33m 22s",
"platform": "osx20",
"platformDetail": "ESXi",
"provisioningKeyId": "6115",
"provisioningKeyName": "1 mp pb",
"serviceEdgeGroupId": "217246660303024722",
"serviceEdgeGroupName": "1 mp pb group",
"enrollmentCert": {
"id": "2858",
"name": "Mock Company Root Certificate"
}
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
To search for all Private Service Edges that last connected with the ZPA Public Service Edge, use `search=lastBrokerConnectTimeDuration LT (N)`, where `(N)` equals the days (d), hours (h), minutes (m), and seconds (s) in integers.
To search for all Private Service Edges that last disconnected with the ZPA Public Service Edge, use `search=lastBrokerDisconnectTimeDuration LT (N)`, where (N) equals the days (d), hours (h), minutes (m), and seconds (s) in integers.
For example, to search for Private Service Edges that last connected with the ZPA Public Service Edge within 150 days, use `search=lastBrokerConnectTimeDuration LT 150d`.
The following filters are supported for use with the search parameter:
- `lastBrokerConnectTimeDuration`: Filters for Private Service Edges that last connected with the ZPA Public Service Edge.
- `lastBrokerDisconnectTimeDuration`: Filters for Private Service Edges that last disconnected with the ZPA Public Service Edge.
- `controlChannelStatus`: Filters for inactive Private Service Edges.
- `currentVersion`: Filters for the current version of the Private Service Edge.
- `expectedVersion`: Filters for the expected version of the Private Service Edge based on the associated version profile.
For example, to search for an Private Service Edge that has `controlChannelStatus` as disconnected with the last disconnected time greater than (N) days, use `controlChannelStatus EQ ZPN_STATUS_DISCONNECTED AND lastBrokerDisconnectTimeDuration GT 15d`.
- [View an example response](#ViewExample3)
[]{
"totalPages": "36",
"list": [
{
"id": "217246660303024723",
"modifiedTime": "1607915744",
"creationTime": "1607887364",
"modifiedBy": "72057594037950342",
"name": "1 mp pb-1",
"fingerprint": "asbErAYZ7/mNUcQhRPd8XFMIRutWjMsWrfot1dDrOOY=",
"issuedCertId": "10591",
"enabled": true,
"listenIps": [
"192.168.255.2"
],
"publishIps": [
"192.168.255.2"
],
"latitude": "37.4181643",
"longitude": "-121.9531325",
"location": "120 Holger Way, San Jose, CA 95134, USA",
"currentVersion": "21.67.2-2-g1a8538e55-dirty",
"previousVersion": "21.26.0-91-g018c50e7f-dirty",
"lastUpgradeTime": "1617857786",
"upgradeStatus": "UNKNOWN",
"controlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"upgradeAttempt": "0",
"lastBrokerConnectTime": "1618417904",
"lastBrokerConnectTimeDuration": "175d 44m 32s",
"lastBrokerDisconnectTime": "1618419214",
"lastBrokerDisconnectTimeDuration": "175d 22m 41s",
"platform": "osx20",
"platformDetail": "ESXi",
"provisioningKeyId": "6115",
"provisioningKeyName": "1 mp pb",
"serviceEdgeGroupId": "217246660303024722",
"serviceEdgeGroupName": "1 mp pb group",
"enrollmentCert": {
"id": "2858",
"name": "Mock Company Root Certificate"
}
}
]
}
The following rule tag operations are allowed:
- `GT`: Greater than
- `LT`: Less than
- `GTEQ`: Greater than or equal to
- `LTEQ`: Less than or equal to
Updating a Private Service Edge
To update a Private Service Edge:
- Send a `PUT` request to the following endpoint in the service-edge-controller: `/mgmtconfig/v1/admin/customers/{customerId}/serviceEdge/{serviceEdgeId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `serviceEdgeId`: The Private Service Edge ID of the customer.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/serviceEdge/217246660303024723`.
- Use the following JSON payload to update a Private Service Edge and provide the following information about the Private Service Edge:
- `name`: The name of the Private Service Edge.
- `description`: The description of the Private Service Edge.
- `enabled`: Whether the Private Service Edge is enabled or not.
- [View the JSON payload](#ViewJSON)
[]{
"description": "Test Service Edge",
"enabled": true,
"name": "Test_Service Edge",
}
A successful response returns code 204, meaning the Private Service Edge is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Refer to the[ Adding Field Descriptions](#AddingFieldDescriptions) section for the supported values.
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the Private Service Edge use cases:
[](/zpa/about-api-keys)[](/zpa/configuring-microtenants-using-api)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| name | Name of the Private Service Edge | No | String |
| description | Description of the Private Service Edge | No | String |
| enabled | Whether the Private Service Edge is enabled or not | No | Default: `true`Supported values: `true`, `false` |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. Pass `microtenantId` as null to retrieve data from all Microtenants associated with the tenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
Deleting a Private Service Edge
To delete a Private Service Edge:
- Send a `DELETE` request to the following endpoint in the service-edge-controller: `/mgmtconfig/v1/admin/customers/{customerId}/serviceEdge/{serviceEdgeId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `serviceEdgeId`: The Private Service Edge ID of the customer.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/serviceEdge/217246660303024723`.
A successful response yields code 204, meaning the Private Service Edge is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Bulk Deleting Private Service Edges
To bulk delete Private Service Edges:
- Provide the following JSON payload with the Private Service Edge IDs you wish to bulk delete, then send a `POST` request to the following endpoint in the service-edge-controller: `/mgmtconfig/v1/admin/customers/{customerId}/serviceEdge/bulkDelete`.
- [View the JSON payload](#ViewJSON2)
[]{
"ids": [
"<serviceEdgeId",
"<serviceEdgeId2>"
]
}
- [View the example JSON payload](#ViewExampleJSON)
[]{
"ids": [
"217246660303024723",
"217246660303024725"
]
}
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/serviceEdge/bulkDelete`.
A successful response returns code 200, meaning the Private Service Edges are deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).

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