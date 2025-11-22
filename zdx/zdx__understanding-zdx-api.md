# Understanding the ZDX API
Source: https://help.zscaler.com/zdx/understanding-zdx-api
PDF: https://help.zscaler.com/pdf/com/en/1397191.pdf

The ZDX API gives you programmatic access to ZDX features:
- [Authentication](#authentication)
- [Administration](#administration)
- [Alerts](#alerts)
- [Inventory](#inventory)
- [Reports](#reports)
- [Troubleshooting](#troubleshooting)
If you are using ZDX API, be aware of the caveats:
- [Inconsistency in data](#inconsistency)
- [Delay in data](#delay)
- [ZDX Score value of -1](#ZDXScore)
Prior to the use of API, Zscaler recommends reviewing [Getting Started](/zdx/getting-started-zdx-api) for information regarding prerequisites, authentication, and making API calls.
For information on rate limits, see [Understanding Rate Limiting](/zdx/understanding-rate-limiting). To learn more about HTTP status codes, see [Understanding Error Codes](/zdx/understanding-error-codes). If you encounter any issues with the ZDX API, contact Zscaler Support.
[]Returns the authentication token for access to ZDX API.
[]Retrieves ZDX Scores for applications and specific device health metrics and events.
Most Report API endpoints require a 2-hour time range to provide 2 hours of data. If more data is required for a longer duration, another request with a different 2-hour time frame must be sent. For example, you cannot send an API request from 12:00 PM to 4:00 PM as this exceeds 2 hours. You must send an API request with a time range from 12:00 PM to 2:00 PM and another one from 2:00 PM to 4:00 PM.
The endpoint, `/devices/{deviceid}/events`, does not require a time range.
[]Lists the active locations and departments for a tenant.
[]Retrieves alert details such as device, application, network performance, and ZDX Score.
Some Alert API endpoints require a 2-hour time range to provide 2 hours of data. If more data is required for a longer duration, another request with a different 2-hour time frame must be sent. For example, you cannot send an API request from 12:00 PM to 4:00 PM as this exceeds 2 hours. You must send an API request with a time range from 12:00 PM to 2:00 PM and another one from 2:00 PM to 4:00 PM.
The following endpoints do not require a time range:
- `/alerts/{alert_id}`
- `/alerts/{alert_id}/affected_devices`
[]Start deep tracing on a specific user and their respective device.
[]Retrieve the distribution of software information across your organization.
[]The data returned by the ZDX API might not exactly match the data on the ZDX UI. The difference between the data is a marginal 2% because the aggregated metrics compute using approximate functions. The ZDX API does this in order to maximize performance.
For example, the Page Fetch Time (PFT) for a Web probe on the ZDX UI is 89ms while the API shows PFT as 90ms.
[]Zscaler Client Connector does the hard work of collecting all the telemetry and reporting. This can cause a delay from collection to reporting, which is estimated to be 20 minutes. To get the full data for an hour, ensure that you use the correct timestamp and adjust for this delay.
[]If you receive a ZDX Score of -1 on the ZDX API, then there is no data available.

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