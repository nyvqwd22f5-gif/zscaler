# API Response Codes and Error Messages
Source: https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages
PDF: https://help.zscaler.com/pdf/com/en/1447246.pdf

The following HTTP status codes are returned by the API:
-
-
-
| Code | Description |
| ---- | ----------- |
| 200 OK | Successful |
| 204 No Content | Successful. No content returned. |
| 400 Bad Request | Request not completed due to incorrect syntax. |
| 401 Unauthorized | Session is not authenticated or timed out. |
| 403 Forbidden | This code is returned for one of the following reasons:The API key was disabled by your service provider.User's role has no access permissions or functional scope.API operations that use POST, PUT, or DELETE methods were performed when the Zscaler Cloud & Branch Connector Admin Portal is in maintenance mode during a scheduled upgrade.Contact Zscaler Support or your Zscaler Account team for assistance. |
| 404 Not Found | Resource does not exist. |
| 409 Conflict | Request could not be processed because a possible edit conflict occurred. Another admin might be saving configuration changes at the same time. In this scenario, the client is expected to retry after a short time period. |
| 415 Unsupported Media Type | Unsupported media type. This error is returned if you don't include `application/json` as the `Content-Type` in the request header (for example, `Content-Type: application/json`). |
| 429 Too Many Requests | Exceeded the rate limit or quota. The response includes a `Retry-After` value. |
| 500 Internal Server Error | Unexpected error. |
| 503 Service Unavailable | Service is temporarily unavailable. |

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