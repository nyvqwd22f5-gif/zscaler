# Understanding Response Codes & Error Messages
Source: https://help.zscaler.com/oneapi/understanding-response-codes-error-messages
PDF: https://help.zscaler.com/pdf/com/en/1497106.pdf

The following HTTP status codes are returned by Zscaler OneAPI.
[See OneAPI response codes and error messages.](#oneapi-response-codes)
In addition, the APIs for specific Zscaler services might use a set of status codes that is exclusive to that service. The following sections provide information on the status codes that are exclusive to specific services.
ZIA API
Zscaler Internet Access (ZIA) API uses the following additional response codes and error messages that are specific to use cases and scenarios in ZIA.
[See ZIA-specific API response codes and error messages.](#ZIA-response-codes)
ZPA API
Zscaler Private Access (ZPA) API uses the following additional response codes and error messages that are specific to use cases and scenarios in ZPA.
[See ZPA-specific API response codes and error messages.](#ZPA-response-codes)
Zscaler Client Connector API
Zscaler Client Connector API uses the following additional response codes and error messages that are specific to use cases and scenarios in Zscaler Client Connector.
[See Zscaler Client Connector-specific API response codes and error messages.](#client-connector-response-codes)
Zscaler Cloud & Branch Connector API
Cloud & Branch Connector API uses the following additional response codes and error messages that are specific to use cases and scenarios in Cloud & Branch Connector.
[See Cloud & Branch Connector-specific API response codes and error messages.](#cloud-branch-connector-response-codes)
ZIdentity API
ZIdentity API uses the following additional response codes and error messages that are specific to use cases and scenarios in ZIdentity.
[See ZIdentity-specific API response codes and error messages.](#zid-error-codes)
[]
-
-
-
| Code | Description |
| ---- | ----------- |
| 200 | Successful request. |
| 204 | Successful. No content returned. |
| 400 | Invalid or bad request. |
| 403 | This code is returned due to one of the following reasons:User's role has no access permissions or functional scope.A required SKU subscription is missing.API operations that use POST, PUT, or DELETE methods are performed when the ZIA Admin Portal was in maintenance mode during a scheduled upgrade.Contact Zscaler Support or your Zscaler Account team for assistance. |
| 404 | Resource does not exist. |
| 405 | Method not allowed. This error is returned when the request method is not supported by the target resource. |
| 409 | Request could not be processed because possible edit conflict occurred. Another admin might be saving a configuration change at the same time. In this scenario, the API client automatically retries after a short time period. |
| 415 | Unsupported media type. This error is returned if you don't include `application/json` as the `Content-Type` in the request header (for example, `Content-Type: application/json`). |
| 500 | Unexpected error. |
| 503 | Service is temporarily unavailable. |
[]
[](/oneapi/understanding-rate-limiting)
| Code | Description |
| ---- | ----------- |
| 200 | Successful |
| 201 | Created |
| 204 | No Content |
| 400 | Bad RequestFor example:{
"id": "resource.not.found",
"reason": "No resource exists with the given id/name :0",
"params": [
"0"
]
} |
| 401 | UnauthorizedFor example:{
id: "access.denied",
reason: "Access denied"
} |
| 403 | Forbidden |
| 404 | Not Found |
| 409 | ConflictFor example:`{
"params":[
"com.zscaler.zpn.model.PolicySet"
],
"id":"api.concurrent.access.error",
"reason":"Unable to modify the resource due to concurrent change requests. Try again"
}`Concurrent API calls using POST, PUT, and DELETE methods to the policy set controller might return error 409 - Conflict. Ensure that only one PUT request per policy rule is sent at a given time. |
| 429 | The API client exceeded the rate limit or quota.The following example is the response body when an API call is rate limited:`{
"exception": "invalid.toomanyrequests",
"id": "invalid.toomanyrequests",
"reason": "Exceeded the number of requests allowed"
}`The following example is the response header when an API call is rate limited:`{
"content-type": "application/json",
"date": "Wed, 6 Mar 2024 11:38 GMT",
"retry-after": "13s"
} `To learn more, see Understanding Rate Limiting. |
| 503 | Service UnavailableThe following example is a response body for error code 503:`{
"id": "retryable.server.error",
"reason": "An error occurred. Refer to the Retry-After header, and then try again."
}`The following is an example response header: `{Retry-After: 10s}`Zscaler recommends an exponential backoff strategy before retrying. If a `Retry-After` header is available as part of the response headers, wait until the stipulated time mentioned in the `Retry-After` header before retrying. |
[]
| Code | Description |
| ---- | ----------- |
| 200 | Successful |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
[]
| Code | Description |
| ---- | ----------- |
| 401 | The authorization token is invalid, expired, or missing. |
| 403 | The API client does not have access to the requested resource. |
| 404 | The requested API resource could not be found. |
| 408 | The client took too long to send a complete request. |
| 413 | The HTTP request exceeds the maximum allowable size. |
| 429 | The API client exceeded the rate limit or quota. Too many requests have been made in a short period. |
| 500 | An internal server error occurred while processing the request. |
| 503 | The requested resource is temporarily unavailable. |
| 504 | The server took too long to respond to the request. |
[]
-
-
-
| Code | Description |
| ---- | ----------- |
| 200 OK | Successful |
| 204 No Content | Successful. No content returned. |
| 400 Bad Request | Request not completed due to incorrect syntax. |
| 401 Unauthorized | Session is not authenticated or timed out. |
| 403 Forbidden | This code is returned for one of the following reasons:The API key was disabled by your service provider.User's role has no access permissions or functional scope.API operations that use POST, PUT, or DELETE methods were performed when the Zscaler Cloud & Branch Connector Admin Portal was in maintenance mode during a scheduled upgrade.Contact Zscaler Support or your Zscaler Account team for assistance. |
| 404 Not Found | Resource does not exist. |
| 409 Conflict | Request could not be processed because a possible edit conflict occurred. Another admin might be saving configuration changes at the same time. In this scenario, the API client automatically retries after a short time period. |
| 415 Unsupported Media Type | Unsupported media type. This error is returned if you don't include `application/json` as the `Content-Type` in the request header (for example, `Content-Type: application/json`). |
| 429 Too Many Requests | The API client exceeded the rate limit or quota. The response includes a `Retry-After` value. |
| 500 Internal Server Error | Unexpected error. |
| 503 Service Unavailable | Service is temporarily unavailable. |
[]
| Code | Description |
| ---- | ----------- |
| 200 | OK. The request was successful, and the server returned the expected response. |
| 201 | Created. A new resource was successfully created. |
| 202 | Accepted. The request has been accepted for processing, but processing has not yet been completed. |
| 204 | No Content. The request was processed successfully, but no content is returned in the response. |
| 400 | Bad Request. The request contains invalid syntax or parameters. |
| 401 | Unauthorized. Authentication is required or provided credentials are incorrect. |
| 403 | Forbidden. Indicates that the server understood the request but did not process it. |
| 404 | Not Found. The requested resource was not found on the server. |
| 409 | Conflict. The server encountered a request that conflicts with the current state of the resource. |
| 413 | Payload Too Large. The server cannot process the request because the request's payload exceeds the server's configured limit. |
| 500 | Internal Server Error. An unexpected server issue occurred, preventing the request from being processed. |