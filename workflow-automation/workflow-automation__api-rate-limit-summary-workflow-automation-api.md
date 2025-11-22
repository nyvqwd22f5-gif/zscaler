# API Rate Limit Summary
Source: https://help.zscaler.com/workflow-automation/api-rate-limit-summary-workflow-automation-api
PDF: https://help.zscaler.com/pdf/com/en/1452126.pdf

The following table summarizes the Workflow Automation API resources and their rate limits for each API call.
Rate limits are subject to change. To learn more, see [Understanding API Rate Limiting](/zia/understanding-api-rate-limiting-workflow-automation-api).
| Resource URI | GET (read) | POST (create) | DELETE |
| ------------ | ---------- | ------------- | ------ |
| /v1/auth/api-key/token | - | 20/min and 400/hr |  |
| /dlp/v1/customer/audit | - | 20/min and 400/hr |  |
| /dlp/v1/incidents/transactions/{transactionId} | 30/min and 1,000/hr | - |  |
| /dlp/v1/incidents/{dlpIncidentId} | 30/min and 1,000/hr | - | 30/min and 1,000/hr |
| /dlp/v1/incidents/{dlpIncidentId}/change-history | 30/min and 1,000/hr | - |  |
| /dlp/v1/incidents/{dlpIncidentId}/tickets | 30/min and 1,000/hr | - |  |
| /dlp/v1/incidents/{dlpIncidentId}/incident-groups/search | - | 20/min and 400/hr |  |
| /dlp/v1/incidents/{dlpIncidentId}/close | - | 30/min and 1,000/hr |  |
| /dlp/v1/incidents/{dlpIncidentId}/notes | - | 20/min and 400/hr |  |
| /dlp/v1/incidents/{dlpIncidentId}/labels |  | 20/min and 400/hr |  |
| /dlp/v1/incidents/search | - | 20/min and 400/hr |  |
| /dlp/v1/incidents/{dlpIncidentId}/triggers | 30/min and 1,000/hr | - |  |
| /dlp/v1/incidents/{dlpIncidentId}/evidence | 30/min and 1,000/hr | - |  |

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