# Obtaining Enrollment Certificate Details Using API
Source: https://help.zscaler.com/zpa/obtaining-enrollment-certificate-details-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484951.pdf

This article provides information for managing Zscaler Private Access (ZPA) [enrollment certificates](/zpa/about-enrollment-ca-certificates) using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Getting Details for All Enrollment Certificates
To get all enrollment certificates:
- Send a `GET` request to the following endpoint in the enrollment-cert-controller: `/mgmtconfig/v2/admin/customers/{customerId}/enrollmentCert`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v2/admin/customers/217246660302995456/enrollmentCert`.
- [View an example response](#ViewExample)
[]{
"totalPages": "15",
"list": [
{
"id": "22143",
"creationTime": "1563925306",
"modifiedBy": "217246660302995849",
"description": "2",
"name": "1",
"allowSigning": false,
"privateKeyPresent": true,
"clientCertType": "NONE",
"csr": "-----BEGIN CERTIFICATE REQUEST-----\nMIICwTCCAakCAQAwSjEQMA4GA1UEChMHWnNjYWxlcjEXMBUGA1UECxMOUHJpdmF0\nZSBBY2Nlc3MxHTAbBgNVBAMTFG15LW1vY2tjb21wYW55LmN\n-----END CERTIFICATE REQUEST-----\n"
},
{
"id": "22144",
"modifiedTime": "1580448229",
"creationTime": "1563925326",
"modifiedBy": "217246660303023681",
"cName": "my-mockcompany.com/12345",
"validFromInEpochSec": "1563838926",
"validToInEpochSec": "2510005326",
"certificate": "-----BEGIN CERTIFICATE-----\nMIIDSjCCAjKgAwIBAgIRAPq0bFzg30vMM3efHU83n9EwDQYJKoZIhvcNAQELBQAw\nTjEQMA4GA1UEChMHWnNjYWxlcjEXMBUGA1UECxMOUHJpdm\n-----END CERTIFICATE-----",
"issuedTo": "O=Zscaler,OU=Private Access,CN=my-mockcompany.com/12345",
"issuedBy": "O=Zscaler,OU=Private Access,CN=my-mockcompany.com/12345",
"serialNo": "333243810239587973493898071045372878801",
"description": "2",
"name": "12345\"<>",
"allowSigning": true,
"privateKeyPresent": true,
"clientCertType": "NONE",
"csr": "-----BEGIN CERTIFICATE REQUEST-----\nMIICxTCCAa0CAQAwTjEQMA4GA1UEChMHWnNjYWxlcjEXMBUGA1UECxMOUHJpdmF0\nZSBBY2Nlc3MxITAfBgNVBAMTGG15LW1vY2tjb21wYW55Lm\n-----END CERTIFICATE REQUEST-----\n"
},
{
"id": "23164",
"creationTime": "1612417564",
"modifiedBy": "72057594037973665",
"cName": "root.zscaler.com/clien2",
"validFromInEpochSec": "1612331164",
"validToInEpochSec": "2558497564",
"certificate": "----BEGIN CERTIFICATE----\nMIIDSjCCAjKgAwIBAgIRAJePjUG/811dcldsFg74MxUwDQYJKoZIhvcNAQELBQAw\nTTEQMA4GA1UEChM\n----END CERTIFICATE----\n",
"issuedTo": "O=Zscaler,OU=Private Access,CN=root.zscaler.com/clien2",
"issuedBy": "O=Zscaler,OU=Private Access,CN=root.zscaler.com/clien2",
"serialNo": "201458790843283302225978988853372400405",
"name": "clien2",
"allowSigning": true,
"privateKeyPresent": true,
"clientCertType": "ZAPP_CLIENT",
"csr": "----BEGIN CERTIFICATE REQUEST----\nMIICxDCCAawCAQAwTTEQMA4GA1UEChMHWnNjYWxlcjEXMBUGA1UECxMOUHJpdmF0\nZSBBY2Nlc3MxIDAenk\n-----END CERTIFICATE REQUEST-----\n"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
To get enrollment certificates for use with creating provisioning keys, provide the `privateKeyPresent EQ` as set to `true` in the search parameters. For example: `privateKeyPresent EQ true`.
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/enrollmentCert?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v2/admin/customers/217246660302995456/enrollmentCert?page=1&pagesize=2.`
- [View an example response](#paginatedResponse)
[]{
"totalPages": "15",
"list": [
{
"id": "22143",
"modifiedTime": "1646153872",
"creationTime": "1563925306",
"modifiedBy": "72057594038009308",
"description": "2",
"name": "1",
"allowSigning": false,
"privateKeyPresent": true,
"clientCertType": "NONE",
"csr": "-----BEGIN CERTIFICATE REQUEST-----\nMIICwTCCAakCAQAwSjEQMA4GA1UEChMHWnNjYWxlcjEXMBUGA1UECxM\n-----END CERTIFICATE REQUEST-----\n"
},
{
"id": "22144",
"modifiedTime": "1646153872",
"creationTime": "1563925326",
"modifiedBy": "72057594038009308",
"cName": "my-testcompany.com/12345",
"validFromInEpochSec": "1563838926",
"validToInEpochSec": "2510005326",
"certificate": "-----BEGIN CERTIFICATE-----\nMIIDSjCCAjKgAwIBAgIRAPq0bFzg30vMM3efHU83n9EwDQYJKoZIhvcNAQELBQAw\nTjEQMA4GA1UEChMHWnNjYWxlcj\n-----END CERTIFICATE-----",
"issuedTo": "O=Zscaler,OU=Private Access,CN=my-mockcompany.com/12345",
"issuedBy": "O=Zscaler,OU=Private Access,CN=my-mockcompany.com/12345",
"serialNo": "333243810239587973493898071045372878801",
"description": "2",
"name": "12345\"<>",
"allowSigning": true,
"privateKeyPresent": true,
"clientCertType": "NONE",
"csr": "-----BEGIN CERTIFICATE REQUEST-----\nMIICxTCCAa0CAQAwTjEQMA4GA1UEChMHWnNjYWxlcjEXMBUGA1UECxMOUHJpdmF0\nZSBBY2Nlc3MxITAfBgNVBAMTGG=\n-----END CERTIFICATE REQUEST-----\n"
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports a search option to search by features and fields. To search by features and fields:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/73186051597795328/enrollmentCert&search={searchString}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid search string values. The search string values are in the format `fieldName operator fieldValue`. Only search string values that correspond to the values for valid fields and filters are supported. For example, the string `name%20LIKE%20test` is supported for the **Name **filter, using the **Contains **(`LIKE`) operator, for the `test` filter value.
For example: `/mgmtconfig/v1/admin/customers/73186051597795328/enrollmentCert&search=name%20LIKE%20test`.
- [View an example response](#gettingAllEnrollmentCertsSearch)
[]{
"totalPages": "15",
"totalCount": "15",
"list": [
{
"id": "23841",
"modifiedTime": "1646194497",
"creationTime": "1614304266",
"modifiedBy": "72057594038009308",
"cName": "root.zscaler.com/Isolation Cert Test",
"validFromInEpochSec": "1614217866",
"validToInEpochSec": "2560384266",
"certificate": "-----BEGIN CERTIFICATE-----\nMIIDZDCCAkygAwIBAgIRAJWAvoGLsEiEGgOHCRoGwT4wDQYJKoZIhvcNAQELBQAw\nWjEQMA4GA1UEChMHWnNjYWxlcjEXMBUGA1UECxMOUHJpdmF0ZSBBY2Nlc3MxLTAr\nBgNVBAMTJHJvb3QuenNjYWxlci5jb20vSXNvbGF0aW9uIENlcnQgVGVzdDAgFw0y\nMTAyMjUwMTUxMDZaGA8yMDUxMDIxOTAxNTEwNlowWjEQMA4GA1UEChMHWnNjYWxl\ncjEXMBUGA1UECxMOUHJpdmF0ZSBBY2Nlc3MxLTArBgNVBAMTJHJvb3QuenNjYWxl\nci5jb20vSXNvbGF0aW9uIENlcnQgVGVzdDCCASIwDQYJKoZIhvcNAQEBBQADggEP\nADCCAQoCggEBANlcrFANmS4c8VDsQTD8j+N083qOryHzf02tUJnQG3SxqL9U7LSz\nJXkBzZqaTdPbitBYUQipwQdANJ76/ckNHPkJD0U0BMhcCxABRlOv/3gkKbDsP0GP\nSeIi/ZthsNkXfDwBydB4uKypmsPan5sNPtQfDKQb8vbzEZ6+YRdI24untMNHGYDV\n7xo5Pg50AVQIC4pZuvr0x3+67C5Hbx7NNrdWkagbYgtML3FkLxQ+EaPzVbvKohde\njtd6uqjb/ou9lJtVPImd5JmZCmeV+gFceHbccVi4MdsNqILeILD59WHKeo5BJkb1\nXz5TBErBk9LM63Nt9oTr7RpUuhxsSKQOOQMCAwEAAaMjMCEwDwYDVR0TAQH/BAUw\nAwEB/zAOBgNVHQ8BAf8EBAMCAQYwDQYJKoZIhvcNAQELBQADggEBAH0MrPIFr3KD\n7RH5D0IjgQNloBn+2cQlf0wLh3kcgldqBHZWUlXJRiVsIWZiVTW7hwUZ9WXHj8aYF2fLPxD7EBUBXlBJIEI3oyzwk\n6iAJ/0tu2vs=\n-----END CERTIFICATE-----\n",
"issuedTo": "O=Zscaler,OU=Private Access,CN=root.zscaler.com/Isolation Cert Test",
"issuedBy": "O=Zscaler,OU=Private Access,CN=root.zscaler.com/Isolation Cert Test",
"serialNo": "198723449291334110913249869031511867710",
"name": "Isolation Cert Test",
"allowSigning": true,
"privateKeyPresent": true,
"clientCertType": "NONE",
"csr": "-----BEGIN CERTIFICATE REQUEST-----\nMIIC0TCCAbkCAQAwWjEQMA4GA1UEChMHWnNjYWxlcjEXMBUGA1UECxMOUHJpdmF0\nZSBBY2Nlc3MxLTArBgNVBAMTJHJvb3QuenNjYWxlci5jb20vSXNvbGF0aW9uIENl\ncnQgVGVzdDCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBANlcrFANmS4c\n8VDsQTD8j+N083qOryHzf02tUJnQG3SxqL9U7LSzJXkBzZqaTdPbitBYUQipwQdA\nNJ76/ckNHPkJD0U0BMhcCxABRlOv/3gkKbDsP0GPSeIi/ZthsNkXfDwBydB4uKyp\nmsPan5sNPtQfDKQb8vbzEZ6+YRdI24untMNHGYDV7xo5Pg50AVQIC4pZuvr0x3+6\n7C5Hbx7NNrdWkagbYgtML3FkLxQ+EaPzVbvKohdejtd6uqjb/ou9lJtVPImd5JmZ\nCmeV+gFceHbccVi4MdsNqILeILD59WHKeo5BJkb1Xz5TBErBk9LM63Nt9oTr7RpU\nuhxsSKQOOQMCAwEAAaAyMDAGCSqGSIb3DQEJDjEjMCEwDwYDVR0TAQH/BAUwAwEB\n-----END CERTIFICATE REQUEST-----\n"
}
]
}
If you use the ZPA API PortaI or the [Reference Guide](/zpa/zpa-api/api-developer-reference-guide/reference-guide) to make your API calls, the search field string does not require any characters. For example, `name%20LIKE%20test` is `name LIKE test`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of a Particular Enrollment Certificate
To get details of a particular enrollment certificate:
- Send a `GET` request to the following endpoint in the enrollment-cert-controller: `/mgmtconfig/v1/admin/customers/{customerId}/enrollmentCert/{enrollmentCertId}`.
- Provide the following parameters in the request:
- `customerId`: The ZPA tenant ID of the customer.
- `enrollmentCertId`: The ID of the enrollment certificate.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/enrollmentCert/22144`.
- [View an example response](#ViewExample2)
[]{
"id": "22144",
"modifiedTime": "1580448229",
"creationTime": "1563925326",
"modifiedBy": "217246660303023681",
"cName": "my-mockcompany.com/12345",
"validFromInEpochSec": "1563838926",
"validToInEpochSec": "2510005326",
"certificate": "-----BEGIN CERTIFICATE-----\nMIIDSjCCAjKgAwIBAgIRAPq0bFzg30vMM3efHU83n9EwDQYJKoZIhvcNAQELBQAw\nTjEQMA4GA1UEChMHWnNjYWxlcjEXMBUGA1UECxMOUHJpdmF0ZSBB\n-----END CERTIFICATE-----",
"issuedTo": "O=Zscaler,OU=Private Access,CN=my-mockcompany.com/12345",
"issuedBy": "O=Zscaler,OU=Private Access,CN=my-mockcompany.com/12345",
"serialNo": "333243810239587973493898071045372878801",
"description": "2",
"name": "12345\"<>",
"allowSigning": true,
"privateKeyPresent": true,
"clientCertType": "NONE",
"csr": "-----BEGIN CERTIFICATE REQUEST-----\nMIICxTCCAa0CAQAwTjEQMA4GA1UEChMHWnNjYWxlcjEXMBUGA1UECxMOUHJpdmF0\nZSBBY2Nlc3MxITAfBgNVBAMTGG15LW1vY2tjb21wYW55LmNvbS8x\n-----END CERTIFICATE REQUEST-----\n"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).

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