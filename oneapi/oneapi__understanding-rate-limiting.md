# Understanding Rate Limiting
Source: https://help.zscaler.com/oneapi/understanding-rate-limiting
PDF: https://help.zscaler.com/pdf/com/en/1497111.pdf

Rate limits throttle the number of API calls that are made within a specific time frame. The following sections provide a summary of the rate limits used by Zscaler OneAPI.
ZIA API
In Zscaler Internet Access (ZIA) API, every endpoint and action has two different types of rate limit:
- A lower bound limit that protects against high bursts of requests over a short period of time.
- An upper bound limit that protects against a high volume of requests over a long period of time.
Every endpoint is assigned a weight and every weight has a default rate limit. The following table provides the typical assignment for each weight. However some endpoints have exceptions, and additionally, specific operations can have a different weight from these typical values. To learn more about the rate limits of individual ZIA API endpoints, see the [API Rate Limit Summary](/zia/api-rate-limit-summary).
| Weight | Typical Assignment | Requests/second | Requests/minute | Requests/hour |
| ------ | ------------------ | --------------- | --------------- | ------------- |
| Heavy | DELETE | - | 1 | 4 |
| Medium | POST, PUT | 1 | - | 400 |
| Light | GET | 2 | - | 1000 |
As a best practice, after each call to an endpoint, make sure your script includes a wait (or sleep) period. For example, if you are programming in Python, you can use the `time.sleep()` function. When the defined rate limit is exceeded, an [HTTP 429 response code](/oneapi/understanding-response-codes-error-messages) is returned.
ZIA sends Rate Limit headers in API responses to provide information about the current status of rate limits, allowing users to plan ahead for their API integration and prevent reaching the rate limit. The Rate Limit headers are:
- `x-ratelimit-limit`: The rate limit ceiling that is applicable for the current API request.
- `x-ratelimit-remaining`: The number of API requests remaining for the current rate limit window.
- `x-ratelimit-reset`: The time (in seconds) remaining in the current window after which the rate limit resets.
ZPA API
For each organization, all Zscaler Private Access (ZPA) API endpoints called from a specific IP address are subjected to the following rate limits:
- 20 times in a 10-second interval for a GET call
- 10 times in a 10-second interval for any POST/PUT/DELETE call
All rate limits start as soon as the first call is executed. Calls can occur more than once per second, but no more than the limits for each operation type.
When an API request exceeds the defined rate limit, an [HTTP 429 response code](/oneapi/understanding-response-codes-error-messages) is returned along with a response header that includes the `retry-after` field. This field indicates the time required to wait before the next API call is made to facilitate the retry mechanism. The following example is a response header that includes the `retry-after` field and the value `13s` indicates 13 seconds of wait period:
`{
"content-type": "application/json",
"date": "Wed, 6 Mar 2024 11:38 GMT",
"retry-after": "13s"
} `
Zscaler Client Connector API
For each organization, all Zscaler Client Connector API endpoints called from a specific IP address are subjected to a rate limit of 100 calls per hour,* *except for the `/downloadDevices` endpoint which has a rate limit of 3 calls per day*.*
All rate limits start as soon as the first call is executed. Calls can occur more than once per second, but no more than the limits for each operation type.
Zscaler Client Connector sends Rate Limit headers in API responses to provide information about the current status of rate limits, allowing users to plan ahead for their API integration and prevent reaching the rate limit. The Rate Limit headers are:
- `x-ratelimit-limit`: The rate limit ceiling that is applicable for the current API request.
- `x-ratelimit-remaining`: The number of API requests remaining for the current rate limit window.
- `x-ratelimit-reset`: The time (in seconds) remaining in the current window after which the rate limit resets.
Clients subject to rate limits need to back off exponentially to proceed further.
Zscaler Cloud & Branch Connector API
In Cloud & Branch Connector API, every endpoint and operation has two rate limit types:
- A lower bound limit that protects against a high volume of requests over a short period of time.
- An upper bound limit that protects against a high volume of requests over a long period of time.
Every endpoint has a weight, and every weight has a default rate limit. The following table provides the typical assignment for each weight. However, specific operations can have a different weight from these typical values.
| Weight | Typical Assignment | Requests/second | Requests/minute | Requests/hour |
| ------ | ------------------ | --------------- | --------------- | ------------- |
| Heavy | DELETE | - | 1 | 4 |
| Medium | POST, PUT | 1 | - | 400 |
| Light | GET | 2 | - | 1,000 |
As a best practice, after each call to an endpoint, make sure your script includes a wait (or sleep) period. For example, in Python, use the `time.sleep()` function. When the rate limit is exceeded, a [429 HTTP error message](/oneapi/understanding-response-codes-error-messages) is returned with a `Retry-After` response in the Body. For example:
{
"message": "Rate Limit (1/SECOND) exceeded",
"Retry-After": "0 seconds"
}
ZDX API
In Zscaler Digital Experience (ZDX) API, every endpoint is called from a specific IP address and the rate limit is dependent on the Tier Level.
| **Tier Level** | **Number of Licenses** | **API Calls/second** | **API Calls/minute** | **API Calls/hour** | **API Calls/day** |
| -------------- | ---------------------- | -------------------- | -------------------- | ------------------ | ----------------- |
| 1 | 5,000 | 5 | 30 | 1,000 | 10,000 |
| 2 | 20,000 | 5 | 60 | 3,000 | 15,000 |
| 3 | 100,000 | 5 | 120 | 6,000 | 30,000 |
| 4 | More than 100,000 | 5 | 180 | 9,000 | 60,000 |
All rate limits start as soon as the first call is executed. Calls can occur more than once per second, but no more than the limits for each operation type.
Clients who are subject to rate limiting need to back off exponentially in order to proceed further.
ZDX sends Rate Limit headers to provide information about the current status of rate limits. Users can use the Rate Limit headers to plan ahead for their API integration to prevent reaching the rate limit and receiving the [HTTP 429 response code](/oneapi/understanding-response-codes-error-messages).
The Rate Limit headers are:
- `RateLimit-Limit`: The rate limit ceiling that is applicable for the current API request.
- `RateLimit-Remaining`: The number of API requests remaining for the current rate-limit window.
- `RateLimit-Reset`: The time at which the rate limit resets, specified in UTC epoch time (in seconds).