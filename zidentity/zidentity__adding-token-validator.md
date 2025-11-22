# Adding a Token Validator
Source: https://help.zscaler.com/zidentity/adding-token-validator
PDF: https://help.zscaler.com/pdf/com/en/1532125.pdf

You can configure a token validator in the ZIdentity Admin Portal based on your requirements and use it in Zscaler Internet Access (ZIA). During authorization requests, ZIA can verify the identity of the user using the configured claims in the ZIdentity Admin Portal.
ZIdentity Administrators assigned with Full permission to access the Token Validators module can configure the token validator in the ZIdentity Admin Portal. To learn more, see [Admin Roles and Permissions](/zidentity/admin-roles-and-permissions).
To add a token validator:
- Go to **Integration **> **Token Validators**.
-
Click **Add Token Validator**.
[See image.](#clicking_add_token_validator)
-
On the **Token Validator** page:
- **Name**: Enter a name for the token validator.
- **Claim Requirements**: Configure the claim requirements for the JSON Web Token (JWT). These claims are validated at the time of authorization request.
- **Audience**: Displays the audience for whom this token is intended for. You cannot edit this field. Click the **Copy **icon to copy the audience, if required.
- **Subject Claim**: Enter the subject claim that represents the identity of the user.
-
**Claim iss**: Enter the issuer URI of the IdP.
You can configure multiple token validators for a ZIdentity tenant. However, the tenant cannot have a duplicate issuer.
-
**Add Claim**: Click **Add Claim** to add more claims for the JWT token.
The audience claim added manually has precedence over the audience displayed in the **Audience **field.
- Under **Signature Validation,** select and configure any of the following validation types:
- **Client JWKs URL**: Enter the Client JSON Web Key (JWK) URL where the key must be obtained for verification. JWT is a URL-safe token used to securely transmit data between applications. A JWK URL hosts a set of public keys in JSON format, which is used by the API server to verify the JWT signatures issued by the API client.
-
**Certificates and Public Keys**: Upload a certificate that contains the public key. The certificate must be in Base64-encoded PEM format. The file extension must be `.pem` and have no other periods (.) in the file name.
You can upload multiple certificates and public keys files.
[See image.](#add_token_validator)
-
Click **Save**.
[]
![Token Validators page with highlighted Add Token Validator button.](/downloads/zidentity/getting-started/admin-portal/accessing-and-navigating-zidentity-landing-page/Click-Add-Token-Validator.png)
[]
![Add Token Validator page with blurred Audience, Claim Value, and Client JWKs URL fields. ](/downloads/zidentity/getting-started/admin-portal/accessing-and-navigating-zidentity-landing-page/AddingTokenValidator.png)