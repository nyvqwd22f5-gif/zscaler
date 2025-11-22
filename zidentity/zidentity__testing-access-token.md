# Testing an Access Token
Source: https://help.zscaler.com/zidentity/testing-access-token
PDF: https://help.zscaler.com/pdf/com/en/1532126.pdf

You can test the [JSON Web Token (JWT)](https://auth0.com/docs/secure/tokens/json-web-tokens) before the actual authorization request is sent using that token. To learn more, see [About Access Tokens](/zidentity/about-access-tokens).
ZIdentity Administrators assigned with Full and View Only permissions to access the Token Validators module can test a token in the ZIdentity Admin Portal. To learn more, see [Admin Roles and Permissions](/zidentity/admin-roles-and-permissions).
To test a token:
-
Go to **Integrations** > **Token Validators**.
On the **Token Validators** page, you can see the list of token validators.
[See image.](#clicking_test_token)
-
Click **Test Token**.
The **Test Token** page appears.
- In the **Encoded **field, paste a valid JWT token.
-
In the **Decoded** field, the results are automatically populated. The token is divided into the following parts:
- **Matching Token Validator**: Displays the token validator from the configured list.
- **Header**: Displays the algorithm (RS256 or ES256) and token type (JWT).
- **Payload**: Displays the claims in the token (e.g., subject, issuer, audience, name, etc.).
- **Signature**: Displays the signature used to validate the token.
[See image.](#test-token)
[]
![Token Validators page with highlighted Test Token option and displaying the list of available token validators in Zidentity Admin Portal.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-configuring-pingone-external-idp-doc-57200/Click-Test-Token.png)
[]
![Test Token page displaying the Encoded and Decoded fields. ](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-configuring-pingone-external-idp-doc-57200/Test-Token.png)