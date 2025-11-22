# Understanding Rate Limiting
Source: https://help.zscaler.com/zpc/understanding-rate-limiting
PDF: https://help.zscaler.com/pdf/com/en/1455886.pdf

Rate limits throttle the number of API calls you can make for any basic CRUD operation.
The system rate limits if an endpoint is called from a given IP more than:
- 5 times in a second interval for a `GET` call.
- 5,000 times in an hour interval for a `GET` call.
All rate limits start as soon as the first call is executed. Calls may occur more than once per second, but no more than the limits for each operation type. Zscaler recommends you wait to proceed with making calls if you are subject to rate limiting.

## Contents
- **API Developer & Reference Guide**
  - [Getting Started](/zpc/getting-started-zpc-api)
  - [Understanding Rate Limiting](/zpc/understanding-rate-limiting)
  - [API Response Codes and Error Messages](/zpc/api-response-codes-and-error-messages)
  - **Reference Guide**
    - [Alerts](/zpc/alerts-api)
  - **Working with APIs**
    - [Obtaining Alerts Using API](/zpc/obtaining-alerts-using-api)