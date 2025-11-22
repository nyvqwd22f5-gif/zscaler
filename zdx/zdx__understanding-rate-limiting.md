# Understanding Rate Limiting
Source: https://help.zscaler.com/zdx/understanding-rate-limiting
PDF: https://help.zscaler.com/pdf/com/en/1397331.pdf

Rate limits throttle the number of API calls you can make for any basic CRUD operation for scalability purposes.
Based on your tier level, your system rate limits if an endpoint is called from a given IP when one of the following occurs:
| **Tier Level** | **Number of Licenses** | **API Calls/Second** | **API Calls/Minute** | **API Calls/Hour** | **API Calls/Day** |
| -------------- | ---------------------- | -------------------- | -------------------- | ------------------ | ----------------- |
| 1 | 5,000 | 5 | 30 | 1,000 | 10,000 |
| 2 | 20,000 | 5 | 60 | 3,000 | 15,000 |
| 3 | 100,000 | 5 | 120 | 6,000 | 30,000 |
| 4 | More than 100,000 | 5 | 180 | 9,000 | 60,000 |
All rate limits start as soon as the first call is executed. Calls may occur more than once per second, but no more than the limits for each operation type.
Clients who are subject to rate limiting need to back off exponentially in order to proceed further.
Rate Limit Headers
The Rate Limit headers provide information about the current status of rate limits. This allows users to plan ahead for their API integration to prevent hitting the rate limit and receiving the 429 error code.
The Rate Limit headers are:
- RateLimit-Limit: The rate limit ceiling that is applicable for the current API request.
- RateLimit-Remaining: The number of API requests remaining for the current rate-limit window.
- RateLimit-Reset: The time at which the rate limit resets, specified in UTC epoch time (in seconds).

## Contents
- **API Developer & Reference Guide**
  - [Getting Started](/zdx/getting-started-zdx-api)
  - [Understanding Rate Limiting](/zdx/understanding-rate-limiting)
  - [Understanding Error Codes](/zdx/understanding-error-codes)
  - [Configuring the Postman REST API Client](/zdx/configuring-postman-rest-api-client)
  - **Reference Guide**
    - [API Authentication](/zdx/api-authentication)
    - [Administration](/zdx/administration-0)
    - [Alerts](/zdx/alerts-zdx-api)
    - [Inventory](/zdx/inventory)
    - [Reports](/zdx/reports)
    - [Troubleshooting](/zdx/troubleshooting)
    - [ZDX Snapshots](/zdx/zdx-snapshots)
  - **Working with APIs**
    - [Managing Administration Using API](/zdx/managing-administration-using-api)
    - [Configuring Deep Tracing Using API](/zdx/configuring-deep-tracing-using-api)