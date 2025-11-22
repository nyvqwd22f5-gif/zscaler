# Obtaining SCIM Group Details Using API
Source: https://help.zscaler.com/zpa/obtaining-scim-group-details-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484846.pdf

This article provides information on managing Zscaler Private Access (ZPA) SCIM group use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Getting Details of All SCIM Groups
To get details of all SCIM groups for the specified IdP ID:
- Send a `GET` request to the following endpoint: `/userconfig/v1/customers/{customerId}/scimgroup/idpId/{idpId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `idpId`: The ID of a particular IdP. To learn more, see [Obtaining IdP Configuration Details Using API](/zpa/obtaining-idp-configuration-details-using-api).
For example: `/userconfig/v1/customers/72057615512764416/scimgroup/idpId/73196561382768893`.
- [View an example response](#Viewanexampleresponse)
[]{
"totalPages": "1",
"totalCount": "2",
"list": [
{
"id": "20464",
"modifiedTime": "1610781818",
"creationTime": "1610626185",
"name": "group 2 public api",
"idpId": "73196561382768893",
"idpGroupId": null
},
{
"id": "20463",
"modifiedTime": "1610781110",
"creationTime": "1610626168",
"name": "group 1 public api",
"idpId": "73196561382768893",
"idpGroupId": null
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination and sort capabilities. To get a paginated response and sort:
- Send a `GET` request to the following endpoint: `/userconfig/v1/customers/{customerId}/scimgroup/idpId/{idpId}?page=1&pagesize=5&sortBy=name&sortOrder=DSC`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer, in the request endpoint.
- `idpId`: The ID of a particular IdP.
- Valid values for page and page size parameters.
- Valid `sortBy` string values (e.g., `name`).
For example: `/userconfig/v1/customers/145254298228359168/scimgroup/idpId/145254298228359525?page=1&pagesize=5&sortBy=name&sortOrder=DSC`.
- [View an example response](#GetAllScimPagResponse)
[]{
"totalPages": 70000,
"totalCount": 350000,
"list": [
{
"id": 1981044,
"modifiedTime": 1666936258,
"creationTime": 1666073884,
"name": "grp99999",
"idpId": 145254298228359520,
"idpGroupId": "grp99999",
"internalId": "1981044"
},
{
"id": 1981043,
"modifiedTime": 1666936258,
"creationTime": 1666073884,
"name": "grp99998",
"idpId": 145254298228359520,
"idpGroupId": "grp99998",
"internalId": "1981043"
},
{
"id": 1981042,
"modifiedTime": 1666936258,
"creationTime": 1666073884,
"name": "grp99997",
"idpId": 145254298228359520,
"idpGroupId": "grp99997",
"internalId": "1981042"
},
{
"id": 1981041,
"modifiedTime": 1666936258,
"creationTime": 1666073884,
"name": "grp99996",
"idpId": 145254298228359520,
"idpGroupId": "grp99996",
"internalId": "1981041"
},
{
"id": 1981040,
"modifiedTime": 1666936258,
"creationTime": 1666073884,
"name": "grp99995",
"idpId": 145254298228359520,
"idpGroupId": "grp99995",
"internalId": "1981040"
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details for a Particular SCIM Group
To get details of a particular SCIM group:
- Send a `GET` request to the following endpoint: `/userconfig/v1/customers/{customerId}/scimgroup/{scimGroupId}`.
- Use the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `scimGroupId`: The ID of a particular SCIM group.
For example: `/userconfig/v1/customers/72057615512764416/scimgroup/20464`.
- [View an example response](#Viewanexampleresponse2)
[]{
"id": "20464",
"modifiedTime": "1610781818",
"creationTime": "1610626185",
"name": "group 2 public api",
"idpId": "73196561382768893",
"idpGroupId": null
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Field Descriptions
The following table includes descriptions of available fields for the SCIM group use cases:
-
-
-
-
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| page | Indicates the page. If not provided, the default value is `1`. | No | Integer |
| pageSize | Indicates the page size. If not provided, the default page size is `20`. The max page size is `500`. | No | Integer |
| sortBy | Indicates the `sortBy` field name that is used to sort the results. If not provided, the results are sorted by `modifiedTime`. | No | Supported values:`id``name``creationTime``modifiedTime` |

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