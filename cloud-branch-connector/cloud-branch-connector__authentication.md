# Authentication
Source: https://help.zscaler.com/cloud-branch-connector/authentication

## `DELETE /auth`

Log out of authenticated session.

**Tags:** Authentication
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | default response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `GET /auth`

Checks if there is an authenticated session.

**Tags:** Authentication
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation. When an authenticated session exists, the response contains authType information.  If authType is not present, the authenticated session has expired or does not exist. |  |

## `POST /auth`

Creates an authenticated session. The response returns a cookie in the header called `JSESSIONID` that must be used in subsequent requests.

**Tags:** Authentication

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| includeDisplayPreferences | query | boolean | No | Indicates whether to include localization info from organization settings. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
