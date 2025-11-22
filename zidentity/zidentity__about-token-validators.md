# About Token Validators
Source: https://help.zscaler.com/zidentity/about-token-validators
PDF: https://help.zscaler.com/pdf/com/en/1532124.pdf

Token validators are used to validate JSON Web Tokens (JWT). The tokens must contain values that match the configuration of the token validator to gain access to the Zscaler service, like Zscaler Internet Access (ZIA). You can create token validators in the ZIdentity Admin Portal and use them for authorization.
Token Validators provide the following benefits and enable you to:
- Simplify authorization for Zscaler service, like ZIA.
- Granular identity-based access for required Zscaler service using a secure JWT.
- Monitor token validator logs.
Prerequisite
To use token validators, ensure that the following prerequisite is met:
You must have ZIA and Zscaler Private Access (ZPA) tenants provisioned in the ZIdentity Admin Portal.
About the Token Validators Page
On the Token Validators page (Integration > Token Validators), you can do the following:
- View the configured Token Validators. For the token validator, you can see:
- **Name**: The name of the token validator.
-
**Type**: The type of token accepted by the token validator for the authorization request.
Currently, ZIdentity only supports JWT token.
- [Add a new token validator](/zidentity/adding-token-validator).
- [Test a JWT token manually](/zidentity/testing-access-token).
- Search for a token validator by name.
- [Edit or delete a token validator](/zidentity/editing-or-deleting-items).
![Annotated Token Validators page.](/downloads/Token-Validator-List-page.png)