# Managing Token Validators
Source: https://help.zscaler.com/zsdk/managing-token-validators
PDF: https://help.zscaler.com/pdf/com/en/1507266.pdf

Token validators use JSON Web Tokens (JWTs) signed by your identity provider (IdP) to enforce authentication requirements.
Your IdP's JWT must contain the following claims when configuring a token validator:
- Subject (sub): Identifies the principal that is the subject of the JWT. This claim represents the user or entity making the request.
- Audience (aud): Specifies the intended recipients of the JWT.
- Issuer (iss): Identifies the issuer of the JWT.
You can use [jwt.io](https://jwt.io/) to inspect and extract the required preceding information from a JWT issued by your app’s IdP.
To access the Token Validator page:
- On the [ZIdentity Landing Page](/zidentity/accessing-and-navigating-zidentity-landing-page), click **ZIdentity Administration**.
- Go to **Integration **> **Token Validators**.
On the **Token Validators** page, you can:
- [Add a token validator.](#Add)
- [Edit a token validator.](#Edit)
- [Delete a token validator.](#Delete)
[]
-
On the **Token Validators** page, click **Add Token Validator**.
The **Add Token Validator** drawer appears.
-
In the **Add Token Validator** drawer:
- **Name**: Enter the name of the token validator.
- **Application**: Select the name of the app key [you previously registered](/zsdk/register-your-app).
-
Click **Add Claim **to enter the following information from the JWT issued by your app's IdP:
- **aud**: Add the value listed from the JWT's aud.
- **iss**: Add the value listed from the JWT's iss.
- **sub**: Add the value listed from the JWT's sub.
Depending on your app's IdP, the values might differ from aud, iss, or sub.
- Select a **Validation Type** and depending on what you selected:
- **Client JWKs URL**: Enter your JSON Web Key's (JWK's) URL from your app's IdP.
- **Certificates and Public Keys**: Upload the certificate used by your app's IdP to sign JWTs.
[See image.](#ADD)
- Click **Save**.
[]
-
On the **Token Validators** page, click the **Edit** icon on the token validator.
The **Edit Token Validator** drawer appears.
-
In the **Edit Token Validator** drawer:
- **Name**: Edit the name of the token validator.
- **Application**: Select the name of your registered app.
- Under **Claim Requirements**, you can edit any of the claim requirements and their values or click **Add Claim** to create more claim requirements.
- Depending on what you selected as a **Validation Type**:
- **Client JWKs URL**: Edit the JWK's URL.
- **Certificates and Public Keys**: Upload a new certificate or public key used by your app's IdP to sign JWTs.
[See image.](#EDIT)
- Click **Update**.
[]
- On the **Token Validators** page, click the **Delete **icon on the token validator.
- The **Delete Token Validator** window appears.
-
In the **Delete Token Validator** window, enter **YES** and then click **Delete** to confirm the deletion of the token validator.
[See image.](#DELETE)
-
On the **Token Validators** page, a confirmation window briefly appears.
[See image.](#DELETE-CONFIRMATION)
[]
![Add a token validator to use JWTs from your IdP.](/downloads/zsdk/managing-token-validators/ZscalerSDK-TokenValidatorsPage-AddTokenValidator-1.png)
[]
![Edit an existing token validator to configure the JWT's Claim Requirements](/downloads/zsdk/managing-token-validators/ZscalerSDK-TokenValidatorsPage-EditTokenValidator-1.png)
[]
![Delete the selected Token Validator](/downloads/zsdk/managing-token-validators/ZscalerSDK-TokenValidatorsPage-DeleteTokenValidator.png)
[]
![The confirmation window for the deletion of the token validator appears briefly](/downloads/zsdk/managing-token-validators/ZscalerSDK-TokenValidatorsPage-DeleteTokenValidator-ConfirmationWindow-2.png)