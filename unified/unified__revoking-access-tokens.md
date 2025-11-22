# Revoking Access Tokens
Source: https://help.zscaler.com/unified/revoking-access-tokens
PDF: https://help.zscaler.com/pdf/com/en/1508271.pdf

You can revoke the [access tokens](/unified/about-access-tokens) assigned to the API clients, when required. The [API client](/unified/about-api-clients) can no longer use the revoked token for authentication.
You can only revoke active tokens.
To revoke an access token:
- Go to **Administration **> **API Configuration** > **OneAP**I > **Tokens**.
- On the** ZIdentity Issued Tokens** page, you can see the list of tokens.
- Search or use the **Status** filter to view the list of active tokens.
-
For the specific active token, click **Revoke**.
[See image.](#zid-activetokens)
-
In the **Revoke Token** window, enter `YES` to confirm the action, then click **Revoke**.
[See image.](#zid-revokemsg)
The token is revoked, and the API client can no longer use this token for authentication. You need to generate another token when required.
[]![List of active tokens](/downloads/zidentity/integration/oneapi-authentication/revoking-access-tokens/zid-activetokens.png)
[]![Confirm the revoke action](/downloads/zidentity/integration/oneapi-authentication/revoking-access-tokens/zid-revoketokenmsg.png)