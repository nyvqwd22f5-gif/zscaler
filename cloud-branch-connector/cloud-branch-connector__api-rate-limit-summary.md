# API Rate Limit Summary
Source: https://help.zscaler.com/cloud-branch-connector/api-rate-limit-summary
PDF: https://help.zscaler.com/pdf/com/en/1531136.pdf

The following table summarizes the Zscaler Cloud & Branch Connector API resources and their rate limits for each method.
Rate limits are subject to change. To learn more, see [Understanding Rate Limits](/cloud-branch-connector/understanding-rate-limits).
| **Resource URI** | **GET (read)** | **POST (create)** | **PUT (replace)** | **DELETE** |
| ---------------- | -------------- | ----------------- | ----------------- | ---------- |
| /accountGroups | 5/sec and up to 3,000/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr |
| /adminRoles | 2/sec and up to 1,000/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr |
| /adminUsers | 2/sec and up to 1,000/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr | 1/sec and up to 400 /hr |
| /auth | Unlimited Access | Unlimited Access | - | Unlimited Access |
| /apiKeys | 2/sec and up to 1,000/hr | - | - | - |
| /apiKeys/{keyId}/regenerate | - | 1/sec and up to 400/hr | - | - |
| /ccaTemplate | 20/sec and up to 10,000/hr | - | - | - |
| /ccaCsr/signCert/{deviceId} | - | 20/sec and up to 10,000/hr | - | - |
| /ccaTemplate/bootupConfig | 20/sec and up to 10,000/hr | - | - | - |
| /ecAdminActivateStatus | 10/sec and up to 5,000/hr | - | - | - |
| /ecAdminActivateStatus/activate | - | - | 1/sec and up to 400/hr | - |
| /ecCsr | - | 10/min and up to 40/hr | - | - |
| /ecgroup | 5/sec and up to 3,000/hr | 5/sec and up to 3,000/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr |
| /ecgroup/lite | 5/sec and up to 3,000/hr | 5/sec and up to 3,000/hr | 1/sec and up to 400/hr | - |
| /ecInstance/lite | 2/sec and up to 1,000/hr | - | - | - |
| /ecRules/ecRdr | 5/sec and up to 3,000/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr |
| /ecVm | 5/sec and up to 3,000/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr |
| /ecVm/uuid/{vmInstanceId} | 5/sec and up to 3,000/hr | - | - | 1/sec and up to 400/hr |
| /gateways | 5/sec and up to 3,000/hr | 1/sec and up to 400/hr | - | 1/sec and up to 400/hr |
| /gateways/lite | 5/sec and up to 3,000/hr | - | - | - |
| /intf | 5/sec and up to 3,000/hr | 5/sec and up to 3,000/hr | 5/sec and up to 3,000/hr | 5/sec and up to 3,000/hr |
| /ipDestinationGroups | 5/sec and up to 3,000/hr | 1/sec and up to 400/hr | - | 1/sec and up to 400/hr |
| /ipDestinationGroups/lite | 5/sec and up to 3,000/hr | - | - | - |
| /ipGroups | 5/sec and up to 3,000/hr | 1/sec and up to 400/hr | - | 1/sec and up to 400/hr |
| /ipGroups/lite | 5/sec and up to 3,000/hr | - | - | - |
| /ipSourceGroups | 5/sec and up to 3,000/hr | 1/sec and up to 400/hr | - | 1/sec and up to 400/hr |
| /ipSourceGroups/lite | 5/sec and up to 3,000/hr | - | - | - |
| /location | 5/sec and up to 3,000/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr |
| /location/lite | 5/sec and up to 3,000/hr | - | - | - |
| /locationTemplate | 2/sec and up to 1,000/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr |
| /networkServices | 5/sec and up to 3,000/hr | - | - | - |
| /networkServiceGroups | 5/sec and up to 3,000/hr | - | - | - |
| /passwordChange | - | 1/sec and up to 400/hr | - | - |
| /provUrl | 5/sec and up to 3,000/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr |
| /publicCloudAccountDetails | 20/sec and up to 10,000/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr |
| /publicCloudAccountIdStatus | 20/sec and up to 10,000/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr |
| /publicCloudInfo | 5/sec and up to 3,000/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr | 1/sec and up to 400/hr |
| /publicCloudInfo/{generateExternalId} | - | 5/sec and up to 3,000/hr | - | - |
| /route | 5/sec and up to 3,000/hr | 5/sec and up to 3,000/hr | 5/sec and up to 3,000/hr | 5/sec and up to 3,000/hr |
| /workloadGroups | 2/sec and up to 1,000/hr | - | - | - |
| /workloadGroups/lite | 5/sec and up to 3,000/hr | - | - | - |
| /zpaResources/applicationSegments | 5/sec and up to 3,000/hr | - | - | - |

## Contents
- **API Developer & Reference Guide**
  - [Getting Started](/cloud-branch-connector/getting-started-cloud-branch-connector-api)
  - [Configuring the Postman REST API Client](/cloud-branch-connector/configuring-postman-rest-api-client)
  - [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages)
  - [Understanding Rate Limits](/cloud-branch-connector/understanding-rate-limits)
  - **Reference Guide**
    - [Activation](/cloud-branch-connector/activation)
    - [Admin and Role Management](/cloud-branch-connector/admin-and-role-management)
    - [Authentication](/cloud-branch-connector/authentication)
    - [Cloud & Branch Connector Groups](/cloud-branch-connector/cloud-branch-connector-groups)
    - [Forwarding Gateways](/cloud-branch-connector/forwarding-gateways)
    - [Location Management](/cloud-branch-connector/location-management)
    - [Partner Integrations](/cloud-branch-connector/partner-integrations)
    - [Policy Management](/cloud-branch-connector/policy-management)
    - [Policy Resources](/cloud-branch-connector/policy-resources)
    - [Provisioning](/cloud-branch-connector/provisioning)
    - [API Rate Limit Summary](/cloud-branch-connector/api-rate-limit-summary)
  - **Working with APIs**
    - [Deleting Cloud & Branch Connectors Using API](/cloud-branch-connector/deleting-cloud-branch-connectors-using-api)
    - [Managing Admin Users and Roles Using API](/cloud-branch-connector/managing-admin-users-and-roles-using-api)
    - [Managing Credentials Using API](/cloud-branch-connector/managing-credentials-using-api)