# API Authentication
Source: https://help.zscaler.com/workflow-automation/api-authentication-workflow-automation-api

Zscaler Workflow Automation - DLP Incident Management API.

## `POST /v1/auth/api-key/token`

Authenticate using the `key_id` and the `key_secret`. The response returns a session token in the header called `Bearer Token` that must be used in subsequent requests.

**Tags:** API Authentication
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 201 | Successful operation. A new authorization token is created. |  |
| 401 | Authorization failure |  |
