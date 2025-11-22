# About Token Validators
Source: https://help.zscaler.com/unified/about-token-validators
PDF: https://help.zscaler.com/pdf/com/en/1532773.pdf

Token validators are used to validate JSON Web Tokens (JWT). The tokens must contain values that match the configuration of the token validator to gain access to the Zscaler service, like Internet & Saas. You can create token validators in the ZIdentity and use them for authorization.
Token Validators provide the following benefits and enable you to:
- Simplify authorization for Zscaler service, like Internet & SaaS.
- Granular identity-based access for required Zscaler service using a secure JWT.
- Monitor token validator logs.
Prerequisite
To use token validators, ensure that the following prerequisite is met:
You must have Internet & Saas and Private Applications services provisioned in the ZIdentity.
About the Token Validators Page
On the Token Validators page (Administration > API Configuration > OneAPI > Token Validators), you can do the following:
- View the configured Token Validators. For the token validator, you can see:
- **Name**: The name of the token validator.
-
**Type**: The type of token accepted by the token validator for the authorization request.
Currently, ZIdentity only supports JWT token.
- [Add a new token validator](/unified/adding-token-validator).
- [Test a JWT token manually](/unified/testing-access-token).
- Search for a token validator by name.
- Edit or delete a token validator.
![Annotated Token Validators page.](/downloads/Token-Validator-List-page.png)