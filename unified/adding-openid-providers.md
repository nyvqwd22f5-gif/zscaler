# Adding OpenID Providers
Source: https://help.zscaler.com/zidentity/adding-openid-providers
PDF: https://help.zscaler.com/pdf/com/en/1499216.pdf

OpenID Connect (OIDC) is a single sign-on protocol much like SAML, which is used to authenticate users at an OpenID Provider (OP) and to assert their authenticated identities to Relying Parties (RP).
This article describes how to add an OpenID Provider. You can add a primary OP or multiple secondary OPs and assign a subset of user domains to a specific OP.
To add an OP (primary or secondary):
- Go to **Integration **> **External Identities**.
-
Click **Add Primary IdP** if you want to configure an external IdP as your primary IdP or **Add Secondary IdP** if you want to configure an external IdP as a secondary IdP.
The **Add Primary Identity Provider** or **Add Secondary Identity Provider** window appears.
You can add a secondary IdP only if a primary IdP is already configured.
-
[]On the **Basic **tab, add the following details:
- **Name**: Enter a name for the OP.
- **Identity Vendor**: Select the OP.
- **Domain**: Select the domain for which the OP is responsible for authenticating the users. This allows the Zscaler service to display the correct OP to authenticate an incoming user.
- **Protocol**: Select **OIDC**.
- **Status**: Enable or disable the OP.
-
**Login ID Attribute**: Enter an attribute whose value must be used as the login ID. This attribute must exist in the tokens received from the IdP. By default, the `preferred_username` attribute is populated in this field when the **OIDC** option is selected in the **Protocol** field. You can use any attribute that is present in the [ID token](https://openid.net/specs/openid-connect-core-1_0.html#IDToken) or the response of the [UserInfo endpoint](https://openid.net/specs/openid-connect-core-1_0.html#UserInfo), provided its value is in the email address format (e.g., <user_name>@domain.com>).
- Ensure that the domain part of the email addresses received in the ID tokens match with one of the domains configured in ZIdentity.
- Ensure that the attribute you enter matches exactly with the attribute received in the ID token or the UserInfo endpoint.
- To learn more about supported attributes and their expected value formats (such as email address), refer to the product documentation of the respective IdPs.
-
**Enforce Zscaler Admin MFA**: Enable this option to ensure that admins using an external IdP authenticate with the multi-factor authentication (MFA) process in ZIdentity, irrespective of whether MFA is configured on the external IdP.
An email is sent to all super admins in ZIdentity when the **Enforce Zscaler Admin MFA **option is disabled.
-
[]**Input Method**: Select one of the following input methods to procure the information required for the OIDC configuration. You can get the required information from the OP:
- [Metadata URL](#meta-url)
- [Enter Manually](#metadata-manually)
- **Redirect URI**: Copy the URI. You need this URI when configuring ZIdentity as the RP on the OP's portal.
- **Token Endpoint Authentication Method**: Select the token authentication method to be used when ZIdentity authenticates itself to the OP to exchange the authorization code for tokens (i.e., **Client Secret Basic** or **Client Secret Post**).
- **Client ID**: Enter the client ID. The unique identifier used by the OP for ZIdentity. You can get this information from the OP.
- **Client Secret**: Enter the client secret. This is a confidential code used to authenticate ZIdentity to the OP. You can get this information from the OP.
- **Requested Scopes**: Enter the scopes you want ZIdentity to include in the authentication request to the OP. Depending on configuration at the OP, it's possible to use scopes to retrieve additional user attributes.
- **Default Requested Authentication Context (Optional)**: Enter the authentication context class reference values to be passed in the authentication request to the OP. The value defines the authentication method or levels required from the user (e.g., password only, multi-factor authentication, etc.). You can get these values from your OP.
[See image.](#basic)
-
On the **Advanced** tab:
- **IdP Attribute**: Enter the IdP attribute that must be mapped to the session attribute. You can get all the attributes from the OIDC JSON for your IdP.
- **Session Attribute**: Select the required attribute from the drop-down menu.
[See image.](#zsl-oidc-sessionattrib)
If you are configuring Zscaler Identity Proxy for Cloud Apps, you must map the `Is Device Managed` session attribute with the appropriate IdP attribute, and then configure the managed devices settings in the ZIA Admin Portal. To learn more, see [Configuring the Zscaler Identity Proxy for Cloud Apps](/zia/configuring-zscaler-identity-proxy-cloud-apps).
-
On the **Provisioning **tab:
- **Enable Just-in-time (JIT) Provisioning**: Enabling this option allows automated user provisioning to the ZIdentity service when the user tries to access ZIdentity for the first time and is not provisoned to the ZIdentity service yet. The ZIdentity service uses the response sent by the OP containing user information to create a [user database](/zidentity/about-users) with ZIdentity in real time.
If you disable this option, unprovisioned users are denied access to the ZIdentity service until the [users are configured](/zidentity/adding-users) in the ZIdentity Admin Portal. For JIT provisioning, add the following details:
- **Just-in-time User Group Attributes**: Enter the JIT user group attribute.
- **Just-in-time Attribute**: Enter the JIT attribute that you want to map from the OP.
- **User Attribute**:** **Select the user attribute** **that you want to map to the JIT attribute. Click** Add More** to map additional attributes. To remove an attribute mapping, click the **Delete** icon next to the user attribute.
- **Enable SCIM Provisioning**: Enable to activate SCIM-based provisioning for users. The following fields appear:
-
**SCIM Endpoint URL**: Copy the SCIM Endpoint URL. This is the base URL for the SCIM server and it's needed when configuring SCIM-based provisioning with your external IdP.
The **SCIM Endpoint URL** field appears only if the configurations for the IdP in the **Basic **tab are completed and saved.
[See image.](#scim-url)
- **Authentication Method**: Select the authentication method.
- **Bearer Token**: Copy the bearer token. It's a unique alphanumeric string that is used by the SCIM client to make authenticated API calls to the Zscaler SCIM server. You need this token when configuring your IdP for SCIM provisioning.
- **Generate Token**: Click to generate a new bearer token for security reasons. If you're generating a new bearer token for an existing SCIM configuration, ensure to update the token on your OP portal.
- **SCIM Attributes**: Enter the SCIM attribute that you want to map.
- **User Attribute**:** **Select the user attribute** **that you want to map to the SCIM attribute. Click** Add More** to map additional attributes. To remove an attribute mapping, click the **Delete** icon next to the user attribute.
[See image.](#provisioning)
- Click **Save**.
[]**Metadata URL**: Paste the link to the OP's metadata file and click **Fetch**.
- []**Issuer**: Enter the issuer URL of the OP.
- **Authorization Endpoint**: Enter the OP's URL where the user is redirected for authentication. Upon successful authentication at this endpoint, an authorization code is sent to the ZIdentity service.
- **Token Endpoint**: Enter the OP's URL where the ZIdentity service presents the authorization code in exchange for an ID token and access token.
- **JWKS Endpoint**: Enter the JSON Web Key Set (JWKS) URL where the JWKS is obtained containing public keys that are used to validate digital signatures on ID tokens and access tokens issued by the OP
- **UserInfo Endpoint**: Enter the OP's URL from where the user information is received when an access token is provided.
[]![Basic tab in the Add Identity Provider page.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-adding-openid-providers-doc-57297/Add-Primary-Identity-Provider.png)
[]![Adding the provisioning details](/downloads/zslogin/authentication/external-idp-configuration/adding-openid-providers/zidentity-provisioning-add-primary-idp.png)
[]
![SCIM Endpoint URL](/downloads/zslogin/authentication/external-idp-configuration/adding-openid-providers/zidentity-scim-endpoint-url.png)
[]![Adding the session attributes](/downloads/zslogin/authentication/external-idp-configuration/adding-openid-providers/zidentity-session-attributes.png)