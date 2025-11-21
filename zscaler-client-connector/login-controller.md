# Login Controller
Source: https://help.zscaler.com/zscaler-client-connector/login-controller

Api Documentation

## `POST /papi/auth/v1/login`

Authenticate using the `apikey` and the `secretKey`. The response returns a JSON Web Token (JWT), which must be used for authentication against other API calls in subsequent requests. To learn more, see [ Locate your base URI.](https://help.zscaler.com/zscaler-client-connector/getting-started-client-connector-api#locate-your-base-url)

**Tags:** login-controller
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 404 | Not Found |  |
