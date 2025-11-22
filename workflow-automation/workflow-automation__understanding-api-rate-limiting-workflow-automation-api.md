# Understanding API Rate Limiting
Source: https://help.zscaler.com/workflow-automation/understanding-api-rate-limiting-workflow-automation-api
PDF: https://help.zscaler.com/pdf/com/en/1452116.pdf

Rate limits throttle the number of API calls you can make. Every endpoint has a weight, and every weight has a default rate limit, but some endpoints have rate limits that differ from the default. To learn more, see the [API Rate Limit Summary](/zia/api-rate-limit-summary-workflow-automation-api).
The following table provides the typical assignment and values for each weight. However, specific operations can have a different weight from these typical values.
| Weight | Typical Assignment | Req/min | Req/hr |
| ------ | ------------------ | ------- | ------ |
| Medium | POST | 20 | 400 |
| Light | GET, POST, DELETE | 30 | 1000 |

## Contents
- **API Developer & Reference Guide**
  - [Getting Started](/workflow-automation/getting-started-workflow-automation-api)
  - [Configuring the Postman REST API Client](/workflow-automation/configuring-postman-rest-api-client-workflow-automation-api)
  - [Understanding API Rate Limiting](/workflow-automation/understanding-api-rate-limiting-workflow-automation-api)
  - [API Response Codes and Error Messages](/workflow-automation/api-response-codes-error-messages-workflow-automation-api)
  - **Reference Guide**
    - [Audit Logs](/workflow-automation/audit-logs)
    - [API Authentication](/workflow-automation/api-authentication-workflow-automation-api)
    - [DLP Incidents](/workflow-automation/dlp-incidents-workflow-automation-api)
    - [API Rate Limit Summary](/workflow-automation/api-rate-limit-summary-workflow-automation-api)