# Obtaining IdP Configuration Details Using API
Source: https://help.zscaler.com/zpa/obtaining-idp-configuration-details-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484821.pdf

This article provides information on managing Zscaler Private Access (ZPA) [IdP configurations](/zpa/about-idp-configuration) using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Getting Details for All IdPs V2
To get the configured IdP details:
- Send a `GET` request to the following endpoint in the idp-controller: `/mgmtconfig/v2/admin/customers/{customerId}/idp`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v2/admin/customers/217246660302995456/idp`.
- [View an example response](#ViewExample)
[]{
"totalPages": "3",
"list": [
{
"id": "217246660303022670",
"modifiedTime": "1619718855",
"creationTime": "1547402803",
"modifiedBy": "217246660303024869",
"name": "Custom entityId IDP configuration - User sso - do NOT delete Changed",
"loginUrl": "https://mockcompany2.okta.com/app/mockcompany2_mymockcomanydomusersso_1/exkli5sevfsnKhh6n0x7/sso/saml",
"idpEntityId": "http://www.okta.com/exkli5sevfsnKhh6n0x7",
"autoProvision": "0",
"signSamlRequest": "1",
"ssoType": [
"USER"
],
"domainList": [
"mockcompany.com"
],
"useCustomSPMetadata": false,
"scimEnabled": false,
"enableScimBasedPolicy": false,
"disableSamlBasedPolicy": false,
"reauthOnUserUpdate": false,
"userSpSigningCertId": "0",
"adminSpSigningCertId": "0",
"scimSharedSecretExists": false,
"forceAuth": false,
"enabled": true,
"redirectBinding": false
},
{
"id": "217246660303022599",
"modifiedTime": "1624663236",
"creationTime": "1542394689",
"modifiedBy": "72057594037928105",
"name": "IDP Config - Admin SSO",
"loginUrl": "https://mockcompany2.okta.com/app/mockcompany2_zpaadminsso_1/exkgdl7ctkw3I3cWW0x7/sso/saml",
"idpEntityId": "http://www.okta.com/exkgdl7ctkw3I3cWW0x7",
"autoProvision": "0",
"signSamlRequest": "0",
"ssoType": [
"ADMIN"
],
"domainList": [
"mockcompany.com"
],
"useCustomSPMetadata": false,
"scimEnabled": false,
"enableScimBasedPolicy": false,
"disableSamlBasedPolicy": false,
"reauthOnUserUpdate": false,
"adminSpSigningCertId": "0",
"scimSharedSecretExists": false,
"forceAuth": false,
"enabled": true,
"redirectBinding": true
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/idp?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v2/admin/customers/217246660302995456/idp?page=1&pagesize=2.`
- [View an example response](#paginatedResponse)
[]{
"totalPages": "3",
"list": [
{
"id": "217246660303022670",
"modifiedTime": "1648147227",
"creationTime": "1547402803",
"modifiedBy": "72057594038052745",
"name": "Test entityId IDP configuration - User sso",
"loginUrl": "https://testcompany.okta.com/app/testcompany_mytestcomanydomusersso_1/exkli5sevfsnKhh6n0x/sso/saml",
"idpEntityId": "http://www.okta.com/exkli5sevfsnKhh6n0x7",
"autoProvision": "0",
"signSamlRequest": "1",
"ssoType": [
"USER"
],
"domainList": [
"mockcompany.com"
],
"useCustomSPMetadata": false,
"scimEnabled": false,
"enableScimBasedPolicy": false,
"disableSamlBasedPolicy": false,
"reauthOnUserUpdate": false,
"userSpSigningCertId": "0",
"adminSpSigningCertId": "0",
"scimSharedSecretExists": false,
"forceAuth": false,
"enabled": true,
"redirectBinding": false
},
{
"id": "217246660303022599",
"modifiedTime": "1624663236",
"creationTime": "1542394689",
"modifiedBy": "72057594037928105",
"name": "IDP Config - Admin SSO",
"loginUrl": "https://testcompany.com/app/testcompany_zpaadminsso_1/exkgdl7ctkw3I3cWW0x7/sso/saml",
"idpEntityId": "http://www.okta.com/exkgdl7ctkw3I3cWW0x7",
"autoProvision": "0",
"signSamlRequest": "0",
"ssoType": [
"ADMIN"
],
"domainList": [
"mockcompany.com"
],
"useCustomSPMetadata": false,
"scimEnabled": false,
"enableScimBasedPolicy": false,
"disableSamlBasedPolicy": false,
"reauthOnUserUpdate": false,
"adminSpSigningCertId": "0",
"scimSharedSecretExists": false,
"forceAuth": false,
"enabled": true,
"redirectBinding": true
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports a search option to search by features and fields. To search by features and fields:
- Send a GET request to the following endpoint: `/mgmtconfig/v1/admin/customers/73186051597795328/idp&search={searchString}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid search string values. The search string values are in the format `fieldName operator fieldValue`. Only search string values that correspond to the values for valid fields and filters are supported. For example, the string `name%20LIKE%20test` is supported for the **Name **filter, using the **Contains **(`LIKE`) operator, for the `test` filter value.
For example: `/mgmtconfig/v1/admin/customers/73186051597795328/idp&search=name%20LIKE%20test`.
- [View an example response](#gettingIdpConfigurationsSearch)
[]{
"totalPages": "2",
"totalCount": "2",
"list": [
{
"id": "72057594037961373",
"modifiedTime": "1668808938",
"creationTime": "1572496367",
"modifiedBy": "72057594038006517",
"name": "test2",
"loginUrl": "http://test.com/sso",
"idpEntityId": "https://test1.com",
"autoProvision": "0",
"signSamlRequest": "1",
"ssoType": [
"USER"
],
"domainList": [
"1467901757270.com"
],
"useCustomSPMetadata": true,
"scimEnabled": true,
"enableScimBasedPolicy": true,
"disableSamlBasedPolicy": false,
"reauthOnUserUpdate": false,
"userSpSigningCertId": "0",
"enableArbitraryAuthDomains": "0",
"scimSharedSecretExists": false,
"forceAuth": false,
"loginHint": true,
"enabled": true,
"redirectBinding": true
}
]
}
If you use the ZPA API PortaI or the [Reference Guide](/zpa/zpa-api/api-developer-reference-guide/reference-guide) to make your API calls, the search field string does not require any characters. For example, `name%20LIKE%20test` is `name LIKE test`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details for a Particular IdP
To get details for a particular IdP:
- Send a `GET` request to following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/idp/{idpId}` in the idp-controller.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `idpId`: The ID of the desired IdP.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/idp/72057615512764510`.
- [View an example response](#Viewanexampleresponse2)
[]{
"id": "72057615512764510",
"modifiedTime": "1571334125",
"creationTime": "1571334045",
"modifiedBy": "72057615512764417",
"name": "AAD",
"certificates": [
{
"cName": "Microsoft Azure Federated SSO Certificate",
"serialNo": "52394493998477153587022235475127474407",
"certificate": "-----BEGIN CERTIFICATE-----\nMIIC8DCCAdigAwIBAgIQJ2rP/22CQ6BDYyU1iU6Y5zANBgkqhkiG9w0BAQsFADA0\nMTIwMAYDVQQDEylNaWNyb3NvZnQgQXp1cmUgRmVkZXJhdGVkIFNTTyBDZXJ0aWZp\nY2F0ZTAeFw0xOTEwMTcxNzM5NTZaFw0yMjEwMTcxNzM5NTZaMDQxMjAwBgNVBAMT\nKU1pY3Jvc29mdCBBenVyZSBGZWRlcmF0ZWQgU1NPIENlcnRpZmljYXRlMIIBIjAN\nBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAmom8BuAvTHJ6Oj69fH4t2iFHNDrh\nE4MUs2TkeH474ogEPG1ilGS2qJW1XBc0XDny5Kior1GC6+q92OL6/VeNHQD1vDPd\nC2u5P+qui6SacjHV/3sM7pDfI01hCF3BxRLo3zEk9ir44lKmRo3B81L+ioGRVgJg\nJj3mbGez8v6YUnHkoSnBrU74Px4wB8DmyeZkZvwyey8+yKse03zC5nzwTDKalOvz\nu1NT09tWQXjvqfn3xyT8RCzo4ukZCF/Fn4CzhldvhO2ERcRlxPY8SxvJTkm26BCr\nrPTlOwY5D3XXEtJdamfziUO2hOdi/GmfC7PIbg7HOF+hTl9uDf+o6C+PSwIDAQAB\nMA0GCSqGSIb3DQEBCwUAA4IBAQBLqHfmFXnDCbVd6ZFkc6NmHE5IK2rCC5tpt3+i\nwjcHYCAScnI+lxmf3snb2E8kBvD7YVA45DUHEI1N1IiF76z1CkxAOIDjgeCFslQ5\nawnVJzHu17J/cTYCD579J9YWdDyz0AaD+lmwRrUP0QoxNZRtjq8dFLh8NGXW87wo\nlAhNXZEIo71Z0dbuAJLKHMSYLGwRG6jBmBzKp0rO4Z8nF3MLJ+bVhX5aYvVKSR8k\nmt/ZAkwqc1ePiiWeru/7VyDypz26fBFJk4UaLz0F9NMDkICR//zWQdfXXDTiKm53\nY/9cwLyFLj3fjRI3f/Qa2gkKU8f1WAqHXhBIPS/4XPaDU4IJ\n-----END CERTIFICATE-----\n",
"validFromInSec": "1571333996",
"validToInSec": "1666028396"
}
],
"loginUrl": "https://login.microsoftonline.com/fe4036f5-76ad-4232-9bda-313544c3ad54/saml2",
"idpEntityId": "https://sts.windows.net/fe4036f5-76ad-4232-9bda-313544c3ad54/",
"autoProvision": "0",
"signSamlRequest": "1",
"ssoType": [
"USER"
],
"domainList": [
"lanuk.net"
],
"useCustomSPMetadata": true,
"scimEnabled": true,
"enableScimBasedPolicy": false,
"disableSamlBasedPolicy": false,
"reauthOnUserUpdate": false,
"userMetadata": {
"spEntityId": "https://samlsp.zpabeta.net/auth/metadata/72057615512764510",
"spPostUrl": "https://samlsp.zpabeta.net/auth/72057615512764510/sso",
"certificateUrl": "https://samlsp.zpabeta.net/auth/certificate",
"spMetadataUrl": "https://samlsp.zpabeta.net/auth/72057615512764510/metadata"
},
"scimServiceProviderEndpoint": "https://scim1.zpabeta.net/scim/1/72057615512764510/v2",
"scimSharedSecretExists": true,
"forceAuth": false,
"enabled": true,
"redirectBinding": true
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