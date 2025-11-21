# About Token Validators
Source: https://help.zscaler.com/zsdk/about-token-validators
PDF: https://help.zscaler.com/pdf/com/en/1507651.pdf

ZSDK uses token validators to inspect and validate JSON Web Tokens (JWTs) issued by your identity provider. During validation, ZSDK verifies token validity, signing certificate authenticity, and required token claims (e.g., subject, issuer, and audience).
Token validators provide the following benefits and enable you to:
- Enforce Zero Trust Network Access (ZTNA) by validating user identity prior to granting access.
- Establish secure communication channels only after successful token validation.
About the Token Validators Page
On the Token Validators page (ZIdentity Administration > Integration > Token Validators), you can do the following:
- [Add a token validator.](/zsdk/managing-token-validators)
- Search for a token validator.
- View a list of token validators. For each token validator, you can see:
- **Name**: The name of the token validator.
- **Type**: The type of the token validator.
- **Actions**: The actions you want to take upon for the token validator.
- [Edit or delete a token validator.](/zsdk/managing-token-validators)
![Token Validators Page](/downloads/zsdk/getting-started/provisioning/about-token-validators/ZscalerSDK-TokenValidatorsPage-2-Outline.png)