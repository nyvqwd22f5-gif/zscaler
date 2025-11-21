# Understanding API Rate Limiting
Source: https://help.zscaler.com/workflow-automation/understanding-api-rate-limiting-workflow-automation-api
PDF: https://help.zscaler.com/pdf/com/en/1452116.pdf

Rate limits throttle the number of API calls you can make. Every endpoint has a weight, and every weight has a default rate limit, but some endpoints have rate limits that differ from the default. To learn more, see the [API Rate Limit Summary](/zia/api-rate-limit-summary-workflow-automation-api).
The following table provides the typical assignment and values for each weight. However, specific operations can have a different weight from these typical values.
| Weight | Typical Assignment | Req/min | Req/hr |
| ------ | ------------------ | ------- | ------ |
| Medium | POST | 20 | 400 |
| Light | GET, POST, DELETE | 30 | 1000 |