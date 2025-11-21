# API Authentication
Source: https://help.zscaler.com/zdx/api-authentication

APIs for Zscaler Digital Experience (ZDX).

## `GET /oauth/jwks`

Returns a JSON Web Key Set (JWKS) that contains the public keys that can be used to verify the JWT tokens.

**Tags:** API Authentication
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 401 |  |  |
| 403 |  |  |

## `POST /oauth/token`

Authenticate using the API key_id and key_secret from the ZDX Admin Portal to access ZDX Public APIs. The response returns a token that must be used in subsequent requests.

**Tags:** API Authentication
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation. The response contains the token and the token type. The token is valid for 3600 seconds. |  |
| 401 |  |  |
| 403 |  |  |

## `GET /oauth/validate`

Checks if the JWT token is valid.

**Tags:** API Authentication
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation. The JWKS keys are valid. |  |
| 401 |  |  |
| 403 |  |  |
