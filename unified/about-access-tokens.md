# About Access Tokens
Source: https://help.zscaler.com/zidentity/about-access-tokens
PDF: https://help.zscaler.com/pdf/com/en/1503966.pdf

Access tokens are [JSON web tokens (JWT)](https://auth0.com/docs/secure/tokens/json-web-tokens) required by API clients for authorization. After the [API client](/zidentity/about-api-clients) completes the authentication with ZIdentity, an access token is generated in the ZIdentity Admin Portal and the API client must use this token for authorization. OneAPI verifies the access token and allows the API client to access the required Zscaler service's API resource. The access tokens have limited validity. This ensures the API client can access the API resources only for a specific duration and they are protected from any security breaches.
The access token can be revoked only by admins.
Access tokens include the following benefits:
- API clients can use the access token for authorization.
- Access tokens have limited validity to prevent prolonged exposure of API resources and protect them from any security breaches.
- Admins can revoke the access tokens and control the API client's access to the API resources.
About the ZIdentity Issued Tokens Page
On the ZIdentity Issued Tokens page (Integration > Tokens), you can do the following:
- View the list of client IDs and the assigned tokens. For each API client, you can see:
- **Client ID**: The unique identifier for the API client.
- **JTI**: The JSON identifier.
- **Issued At**: The date and time when the token was issued.
- **Expires At**: The date and time when the token expires.
- **JWT**: Click to view the JSON web token details. You can view the details only for active tokens.
- **Status**: View the status (Active, Revoked, Expired) of the token.
- Apply the filters to view specific data.
- **Issued At**: View the tokens that were issued in the selected time frame.
- **Expired At**: View the tokens that have expired in the selected time frame.
- **Status**: View the tokens with the following status:
- **Active**: The token is active and can be used by the API client for authorization.
- **Expired**: The token is invalid, and a new token must be generated for the API client to access the API resources.
-
**Revoked**: The token is marked as invalid by ZIdentity. The revoked state is applicable in the following scenarios:
- Token is revoked because the API client to which the token was assigned is deleted. You need to create a new API client and authenticate to get a new token.
- Token is revoked because the status of the API client to which the token was assigned is disabled. You can change the status to Enabled and generate a new token for this API client.
- An administrator manually revoked a token on the **Tokens** page.
If the token is revoked but the API client's status is enabled in the ZIdentity Admin Portal, you can generate a new token and access the API resources.
- Reset the filters.
- Search for a specific API client.
- [Revoke the access token](/zidentity/revoking-access-tokens).
- View the JSON web token details.
![List of issued tokens](/downloads/zidentity/integration/oneapi-authentication/revoking-api-access-token/zid-tokenspage.png)