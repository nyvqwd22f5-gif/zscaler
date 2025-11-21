# API Authentication
Source: https://help.zscaler.com/zia/api-authentication

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `DELETE /authenticatedSession`

Ends an authenticated session.

**Tags:** API Authentication
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | ActivationStatus |

## `GET /authenticatedSession`

Checks if there is an authentication session.

**Tags:** API Authentication
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation. When an authenticated session exists, the response contains authType information. If authType is not present, the authenticated session has expired or it does not exist. | SessionInfo |
| 503 | Service is temporarily unavailable due to maintenance |  |

## `POST /authenticatedSession`

Creates an authenticated session. The response returns a cookie in the header called `JSESSIONID` that must be used in subsequent requests.

**Tags:** API Authentication
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| credentials | body | AuthCredentials | Yes | User credential. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation. The response contains authType information only when authentication has completed successfully, regardless of the response code given. | SessionInfo |

## Models
### ActivationStatus
Organization Policy Edit/Update Activation status
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| status | string | No |  |

### AuthCredentials
Credential info that is required for authenticating a session
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| apiKey | string | No | The obfuscated form of the API key |
| password | string | No | Password of the admin user |
| timestamp | string | No | Long value that represent the the current time in milliseconds since  midnight, January 1, 1970 UTC. This timestamp value must be reflecting the real current time. |
| username | string | No | Username of admin user that is provisioned |

### SessionInfo
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| authType | string | No | Login type |
| obfuscateApiKey | boolean | No | Whether API key was obfuscated or not |
| passwordExpiryDays | integer (int32) | No | Password Expiry Days |
| passwordExpiryTime | integer (int64) | No | Password Expiry Time |
