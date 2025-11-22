# Understanding Rate Limits
Source: https://help.zscaler.com/cloud-branch-connector/understanding-rate-limits
PDF: https://help.zscaler.com/pdf/com/en/1447231.pdf

Rate limits throttle the number of API calls you can make for POST, GET, PUT, and DELETE operations. Every endpoint and operation has two rate limit types:
- A lower bound limit that protects against a high volume of requests over a short period of time
- An upper bound limit that protects against a high volume of requests over a long period of time
These limits throttle the number of API calls you can make. Every endpoint has a weight, and every weight has a default rate limit.
The following table provides the typical assignment for each weight. However, specific operations can have a different weight from these typical values.
| Weight | Typical Assignment | Requests/sec | Requests/min | Requests/hr |
| ------ | ------------------ | ------------ | ------------ | ----------- |
| Heavy | DELETE | - | 1 | 4 |
| Medium | POST, PUT | 1 | - | 400 |
| Light | GET | 2 | - | 1000 |
As a best practice, after each call to an endpoint, your script should include a wait (or sleep) period. For example in Python, you would use the `time.sleep()` function. When the rate limit is exceeded, a [429 HTTP error message](/cloud-branch-connector/api-response-codes-and-error-messages) is returned with a `Retry-After` response in the Body. For example:
{
"message": "Rate Limit (1/SECOND) exceeded",
"Retry-After": "0 seconds"
}

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