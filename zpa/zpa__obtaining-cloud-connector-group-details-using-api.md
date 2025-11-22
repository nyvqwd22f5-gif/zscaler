# Obtaining Cloud Connector Group Details Using API
Source: https://help.zscaler.com/zpa/obtaining-cloud-connector-group-details-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484861.pdf

This article provides information on managing Zscaler Private Access (ZPA) Cloud Connector Group use cases using APIs. All APIs are rate limited. To learn more, see [About Rate Limiting](/zpa/about-rate-limiting).
Getting Details for All Cloud Connector Groups
To get details for all the Cloud Connector groups:
- Send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/cloudConnectorGroup` in the cloud-connector-group-controller.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057615512764416/cloudConnectorGroup`.
- [View an example response](#Viewanexampleresponse)
[]{
"totalPages": "1",
"list": [
{
"creationTime": "1569858419",
"modifiedBy": "72057594037927958",
"id": "217246660303023507",
"name": "TestZNF",
"enabled": true,
"cloudConnectors": [
{
"id": "217246660303023508",
"modifiedTime": "1601588754",
"creationTime": "1569876403",
"modifiedBy": "3",
"name": "TestZNF-1",
"fingerprint": "my_fingerprint",
"issuedCertId": "10230",
"enabled": true
},
{
"id": "217246660303023540",
"modifiedTime": "1571609955",
"creationTime": "1571609954",
"modifiedBy": "3",
"name": "TestZNF-2",
"fingerprint": "my-fingerprint",
"issuedCertId": "1480",
"enabled": true
},
{
"id": "217246660303023559",
"modifiedTime": "1572472297",
"creationTime": "1572472296",
"modifiedBy": "3",
"name": "TestZNF-3",
"fingerprint": "test1",
"issuedCertId": "1491",
"enabled": true
},
{
"id": "217246660303023565",
"modifiedTime": "1572896745",
"creationTime": "1572896744",
"modifiedBy": "3",
"name": "TestZNF-4",
"fingerprint": "my-fingerprint-haha",
"issuedCertId": "1497",
"enabled": true
},
{
"id": "217246660303023627",
"modifiedTime": "1576242337",
"creationTime": "1576242334",
"modifiedBy": "3",
"name": "TestZNF-5",
"fingerprint": "my-fingerprint-so-unique",
"issuedCertId": "1857",
"enabled": true
},
{
"id": "217246660303024153",
"modifiedTime": "1604707454",
"creationTime": "1604707454",
"modifiedBy": "3",
"name": "TestZNF-6",
"fingerprint": "my-fingerprint-hahahahah23",
"issuedCertId": "10548",
"enabled": true
}
]
},
{
"creationTime": "1579645656",
"modifiedBy": "72057594037928105",
"id": "217246660303023669",
"name": "Test ZNF group",
"enabled": true,
"cloudConnectors": [
{
"id": "217246660303023670",
"modifiedTime": "1579646496",
"creationTime": "1579646495",
"modifiedBy": "3",
"name": "Test ZNF group provisioning key-1",
"fingerprint": "Testy-fingerprint",
"issuedCertId": "1889",
"enabled": true
}
]
},
{
"creationTime": "1596498299",
"modifiedBy": "72057594037953048",
"id": "217246660303023942",
"name": "Test_znf_group",
"enabled": true,
"ziaCloud": "zscaler.net",
"ziaOrgId": "12345",
"cloudConnectors": [
{
"id": "217246660303023943",
"modifiedTime": "1596499647",
"creationTime": "1596499647",
"modifiedBy": "3",
"name": "TestZNF-1",
"fingerprint": "Testfingerprint_0001",
"issuedCertId": "2383",
"enabled": true
}
]
},
{
"creationTime": "1598635915",
"modifiedBy": "72057594037950342",
"id": "217246660303024004",
"name": "Tesst_ZNF",
"enabled": true,
"ziaCloud": "zscaler.net",
"ziaOrgId": "12345",
"cloudConnectors": [
{
"id": "217246660303024005",
"modifiedTime": "1598638787",
"creationTime": "1598638787",
"modifiedBy": "3",
"name": "Tesstt_ZNF-1",
"fingerprint": "test-fingerprint-1",
"issuedCertId": "10104",
"enabled": true
},
{
"id": "217246660303024724",
"modifiedTime": "1607900877",
"creationTime": "1607900877",
"modifiedBy": "3",
"name": "MP_ZNF-2",
"fingerprint": "test-fingerprint-2",
"issuedCertId": "10592",
"enabled": true
}
]
},
{
"creationTime": "1599259086",
"modifiedBy": "72057594037941168",
"id": "217246660303024029",
"name": "test-econnector-grp",
"enabled": true,
"ziaCloud": "zscaler.net",
"ziaOrgId": "12345"
},
{
"creationTime": "1599763819",
"modifiedBy": "72057594037941168",
"id": "217246660303024036",
"name": "test_example",
"enabled": true,
"ziaCloud": "zscaler.net",
"ziaOrgId": "12345",
"cloudConnectors": [
{
"id": "217246660303024037",
"modifiedTime": "1599764564",
"creationTime": "1599764563",
"modifiedBy": "3",
"name": "test_example_1-1",
"fingerprint": "test111121212121",
"issuedCertId": "10142",
"enabled": true
}
]
},
{
"creationTime": "1603994989",
"modifiedBy": "72057594037959758",
"id": "217246660303024130",
"name": "test2 edge connector group",
"enabled": true,
"ziaCloud": "zscaler.net",
"ziaOrgId": "111111",
"cloudConnectors": [
{
"id": "217246660303024131",
"modifiedTime": "1603996783",
"creationTime": "1603996782",
"modifiedBy": "3",
"name": "test nonce-1",
"fingerprint": "Test0001",
"issuedCertId": "10531",
"enabled": true
}
]
}
]
}
A successful response returns code 200. To learn more, see [About Error Codes](/zpa/about-error-codes).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/cloudConnectorGroup?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/cloudConnectorGroup?page=1&pagesize=2.`
- [View an example response](#paginatedResponse)
[]{
"totalPages": "8",
"list": [
{
"creationTime": "1628119973",
"modifiedBy": "72057594038044466",
"id": "217246660303025287",
"name": "Test_cloud_connector_group",
"enabled": true,
"ziaCloud": "zscaler.net",
"ziaOrgId": "12345",
"cloudConnectors": [
{
"id": "217246660303025288",
"modifiedTime": "1628122567",
"creationTime": "1628122567",
"modifiedBy": "3",
"name": "Test nonce-1",
"fingerprint": "Test-fingerprint",
"issuedCertId": "10829",
"enabled": true
},
{
"id": "217246660303025478",
"modifiedTime": "1632766307",
"creationTime": "1632766306",
"modifiedBy": "3",
"name": "Test nonce-2",
"fingerprint": "Test-fingerprint002",
"issuedCertId": "10912",
"enabled": true
},
{
"id": "217246660303025510",
"modifiedTime": "1634187902",
"creationTime": "1634187902",
"modifiedBy": "3",
"name": "Test nonce-3",
"fingerprint": "Test-fingerprint003",
"issuedCertId": "10926",
"enabled": true
}
]
},
{
"creationTime": "1644974062",
"modifiedBy": "72057594037988394",
"id": "217246660303026090",
"name": "branch_connector",
"enabled": true,
"description": "branch connector poc",
"ziaCloud": "zscaler.net",
"ziaOrgId": "21400",
"cloudConnectors": [
{
"id": "217246660303026091",
"modifiedTime": "1644975292",
"creationTime": "1644975292",
"modifiedBy": "3",
"name": "branch_conn_poc-1644975292103",
"fingerprint": "branch_connector_poc-vp1",
"issuedCertId": "11409",
"enabled": true
}
]
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [About Error Codes](/zpa/about-error-codes).
Getting Details for a Particular Cloud Connector Group
To get details of a particular Cloud Connector group:
- Send a `GET` request to the endpoint `mgmtconfig/v1/admin/customers/{customerId}/cloudConnectorGroup/{id}` in the cloud-connector-group-controller.
- Provide the following values pairs in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The ID of the desired cloud connector group.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/cloudConnectorGroup/217246660303023507`.
- [View an example response](#Viewanexampleresponse2)
[]{
"creationTime": "1569858419",
"modifiedBy": "72057594037927958",
"id": "217246660303023507",
"name": "TestZNF",
"enabled": true,
"cloudConnectors": [
{
"id": "217246660303023508",
"modifiedTime": "1601588754",
"creationTime": "1569876403",
"modifiedBy": "3",
"name": "TestTestZNF-1",
"fingerprint": "my_fingerprint",
"issuedCertId": "10230",
"enabled": true
},
{
"id": "217246660303023540",
"modifiedTime": "1571609955",
"creationTime": "1571609954",
"modifiedBy": "3",
"name": "TestTestZNF-2",
"fingerprint": "my-fingerprint",
"issuedCertId": "1480",
"enabled": true
},
{
"id": "217246660303023559",
"modifiedTime": "1572472297",
"creationTime": "1572472296",
"modifiedBy": "3",
"name": "TestTestZNF-3",
"fingerprint": "Testprivatebroker1",
"issuedCertId": "1491",
"enabled": true
},
{
"id": "217246660303023565",
"modifiedTime": "1572896745",
"creationTime": "1572896744",
"modifiedBy": "3",
"name": "TestTestZNF-4",
"fingerprint": "my-fingerprint-haha",
"issuedCertId": "1497",
"enabled": true
},
{
"id": "217246660303023627",
"modifiedTime": "1576242337",
"creationTime": "1576242334",
"modifiedBy": "3",
"name": "TestTestZNF-5",
"fingerprint": "my-fingerprint-so-unique",
"issuedCertId": "1857",
"enabled": true
},
{
"id": "217246660303024153",
"modifiedTime": "1604707454",
"creationTime": "1604707454",
"modifiedBy": "3",
"name": "TestTestZNF-6",
"fingerprint": "my-fingerprint-hahahahah23",
"issuedCertId": "10548",
"enabled": true
}
]
}
A successful response returns code 200. To learn more, see [About Error Codes](/zpa/about-error-codes).

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