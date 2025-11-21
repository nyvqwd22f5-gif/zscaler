# Revoking Access Tokens
Source: https://help.zscaler.com/zidentity/revoking-access-tokens
PDF: https://help.zscaler.com/pdf/com/en/1506051.pdf

You can revoke the [access tokens](/zidentity/about-access-tokens) assigned to the API clients, when required. The revoked access token can no longer be used to access the Zscaler API resources.
You can only revoke active tokens.
To revoke an access token:
-
Go to **Integrations** > **Tokens**.
On the** ZIdentity Issued Tokens** page, you can see the list of tokens.
- Search or use the **Status** filter to view the list of active tokens.
-
Click **Revoke** for the specific active token.
[See image.](#zid-activetokens)
-
In the **Revoke Token** window, enter `YES` to confirm the action, then click **Revoke**.
[See image.](#zid-revokemsg)
The token is revoked, and it can no longer be used to access the Zscaler API resources. You need to generate a new token when required.
[]![List of active tokens](/downloads/zidentity/integration/oneapi-authentication/revoking-access-tokens/zid-activetokens.png)
[]![Confirm the revoke action](/downloads/zidentity/integration/oneapi-authentication/revoking-access-tokens/zid-revoketokenmsg.png)