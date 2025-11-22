# Configuring Application Segment Multimatch Using API
Source: https://help.zscaler.com/zpa/configuring-application-segment-multimatch-using-api
PDF: https://help.zscaler.com/pdf/com/en/1531143.pdf

This article provides information for managing application segment multimatch using APIs. All APIs are rate limited. To learn more, see [Using Application Segment Multimatch](/zpa/using-app-segment-multimatch) and [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Getting Application Segments by Domain That Are Incompatible with Application Segment Multimatch
To get application segments by domain that are incompatible with application segment Multimatch:
- Send a `POST` request to the following endpoint: `/customers/{customerId}/application/multimatchUnsupportedReferences`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/customers/144118148382064640/application/multimatchUnsupportedReferences`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the domains for the application segments.
- [View the JSON payload](#getIncompatibleAppSegmentsJson)
[]
`[
"<domain>",
"<domain>"
]`
- [View an example JSON file](#getIncompatibleAppSegmentsExampleJson)
[]
`[
"app.example.com",
"legacy-app.internal.corp"
]`
- [View an example response](#getIncompatibleAppSegmentsExampleResponse)
[]
`[
{
"id":"216903833601306634",
"appSegmentName":"Corp App",
"domains":[
"app.example.com"
],
"matchStyle":"EXCLUSIVE",
"tcpPorts":[
8080,
8080
],
"udpPorts":[
],
"scopeId":null,
"scopeName":null,
"unsupportedFeatures":[
]
},
{
"id":"216903833601306645",
"appSegmentName":"Legacy App",
"domains":[
"legacy-app.internal.corp"
],
"matchStyle":"EXCLUSIVE",
"tcpPorts":[
443,
443
],
"udpPorts":[
],
"scopeId":null,
"scopeName":null,
"unsupportedFeatures":[
"BROWSER_ACCESS",
"Double Encryption"
]
}
]`
An unsuccessful response returns error code 400 if all or none of the domains of the application segment are not provided. For example, the following error code is returned if all or none of the domains of the application segment are not provided:
`{
"message":"Domain(s) are not provided for checking multimatch unsupported features"
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Bulk Updating Application Segment Multimatch for Applications
To bulk update (i.e., enable or disable) application segment Multimatch for a list of application segments:
- Send a `PUT` request to the following endpoint: `/customers/{customerId}/application/bulkUpdateMultiMatch`.
- Provide the `customerId`, the ZPA tenant ID, in the request endpoint. For example: `/customers/144118148382064640/application/bulkUpdateMultiMatch`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information for the application segments:
- `matchStyle`: Indicates if Multimatch is enabled for the application segment. If enabled (`INCLUSIVE`), the request allows traffic to match multiple applications. If disabled (`EXCLUSIVE`), the request allows traffic to match a single application. A domain can only be `INCLUSIVE` or `EXCLUSIVE`, and any application segment can only contain inclusive or exclusive domains. To learn more, see [Using Application Segment Multimatch](/zpa/using-app-segment-multimatch) and [Configuring Defined Application Segments](/zpa/configuring-application-segments).
- `applicationIds`: The IDs of the application segments. To learn more, see [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api).
- [View the JSON file](#BulkUpdateJson)
[]
`{
"applicationIds":[
<application segment ID>,
<application segment ID>
],
"matchStyle":"INCLUSIVE"
}`
- [View the example JSON file](#bulkUpdateExampleJson)
[]
`{
"applicationIds":[
216903833601306634,
216903833601306635
],
"matchStyle":"INCLUSIVE"
}`
If `matchStyle` is set to `INCLUSIVE` and the application segment has features that are unsupported for Multimatch, then the following error code 400 (i.e., bad request) is returned:
`{
"code": "features.not.supported.for.multimatch",
"message": "The following features [BROWSER_ACCESS] are not supported for multimatch in application segment Legacy App"
}`
Multimatch must be disabled if the configuration contains applications using the Access Type of Browser Access, AppProtection, or Privileged Remote Access. Additionally, Multimatch must be disabled if the configuration contains applications using Double Encryption, Inspect Traffic with ZIA, and Source IP Anchor. To learn more, see [Using Application Segment Multimatch](/zpa/using-app-segment-multimatch).
If all of the application segment IDs that share the same domain are not provided, the following error code 400 is returned:
`{
"code":"multimatch.inconsistent.missing.apps",
"message":"The following application(s) are missing from the request but are required for the update: [216903833601306650]"
}`
A successful response returns code 204, meaning the bulk update operation is successful. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).

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