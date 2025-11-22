# Adding SAML Identity Providers
Source: https://help.zscaler.com/zidentity/adding-saml-identity-providers
PDF: https://help.zscaler.com/pdf/com/en/1499086.pdf

This article describes how to add an identity provider (IdP). You can add a primary IdP or multiple secondary IdPs and assign a subset of user domains to a specific IdP. You can add up to 64 secondary IdPs.
To add an IdP (primary or secondary):
- Go to **Integration **> **External Identities**.
-
Click **Add Primary IdP **if you want to configure an external IdP as your primary IdP** **or **Add Secondary IdP **if you want to configure an external IdP as a secondary IdP.
The **Add Primary Identity Provider** or **Add Secondary Identity Provider** window appears.
You can add a secondary IdP only if a primary IdP is already configured.
-
[]On the **Basic **tab:
- **Name**: Enter a name for the IdP.
- **Identity Vendor**: Select the IdP.
- **Domain**: Select the domain for which the IdP is responsible for authenticating the users. This allows the Zscaler service to display the correct IdP to authenticate an incoming user.
- **Protocol**: Select **SAML** or** OIDC**.
- **Status**: Enable or disable the IdP.
-
**Login ID Attribute**: Enter an attribute whose value must be used as the login ID. This attribute must exist in the token received from the IdP. By default, the `NameID` attribute is populated in this field when the **SAML **option is selected in the **Protocol** field. You can use any attribute that is present in the SAML assertion, provided its value is in the email address format (e.g., <user_name>@domain.com>).
- Ensure that the domain part of the email addresses received in the SAML assertion matches with one of the domains configured in ZIdentity.
- Ensure that the attribute you enter matches exactly with the attribute received in the SAML assertion.
- To learn more about supported attributes and their expected value formats (such as email address), refer to the product documentation of the respective IdPs.
-
**Enforce Zscaler Admin MFA**: Enable this option to ensure that admins using an external IdP authenticate with the multi-factor authentication (MFA) process in ZIdentity, irrespective of whether MFA is configured on the external IdP.
An email is sent to all super admins in ZIdentity when the **Enforce Zscaler Admin MFA **option is disabled.
-
[]**Input Method**: Select one of the following input methods to procure the information required for SAML configuration:
- [Metadata URL](#meta-url)
- [Upload Metadata](#zsl-idpmetadata)
- [Enter Manually](#metadata-manually)
[See image.](#basic)
-
On the **Advanced **tab:
- **SAML Request Signing**:** **Enable the option to configure SAML request signing for authentication. Select the signing algorithm from the drop-down menu that appears.
- **Encrypted SAML Assertion**:** **Enable the option to configure encrypted SAML response for authentication.
- **Session Attribute Mapping:**
- **IdP Attribute**: Enter the IdP attribute that must be mapped to the session attribute. To find all the available attribute names, refer to the SAML JSON file for your IdP.
- **Session Attribute**: Select the session attribute from the drop-down menu.
[See image.](#advanced)
- Ensure to select Sign SAML response and assertion as the signing option on the IdP because ZIdentity does not process any SAML response that is not signed.
-
If you are configuring Zscaler Identity Proxy for Cloud Apps, you must map the `Is Device Managed` session attribute with the appropriate IdP attribute, and then configure the managed devices settings in the ZIA Admin Portal. To learn more, see [Configuring the Zscaler Identity Proxy for Cloud Apps](/zia/configuring-zscaler-identity-proxy-cloud-apps).
[See image.](#manged-device-mapping)
After configuring information on the **Advanced **tab, you can add a Request Signing and Decryption Certificate from the **Edit Primary or Secondary IdP** page. To learn more, see [Editing or Deleting a SAML Identity Provider](/zidentity/editing-or-deleting-saml-identity-provider).
-
On the **Provisioning **tab:
- **Enable Just-in-Time (JIT) Provisioning**: Enable this option to allow automated user provisioning to the ZIdentity service when the user tries to access ZIdentity for the first time. The IdP sends a SAML Assertion (XML file) containing user information, which the ZIdentity service uses to create a [user database](/zidentity/about-users) with ZIdentity in real time. If you disable this option, unprovisioned users are denied access to the ZIdentity service until the [users are configured](/zidentity/adding-users) in the ZIdentity Admin Portal.
- Under **Just-in-Time Attribute Mapping**, add the following details:
- **Just-in-Time User Group Attribute**: Enter a name for the user group attribute.
- **Just-in-Time Attribute**: Enter a name for the JIT attribute.
- **User Attribute**: Select the user attribute that you want to map. Click** Add More** to map additional attributes. To remove an attribute mapping, click the **Delete** icon. ZIdentity supports the following default attributes:
- First Name
- Last Name
- Name
- Primary Email
- Login Name
- Display Name
- **Enable SCIM Provisioning**: Enable to activate SCIM-based provisioning for users. The following fields appear:
-
**SCIM Endpoint URL**: Copy the SCIM Endpoint URL. This is the base URL for the SCIM server and it's needed when configuring SCIM-based provisioning with your external IdP.
The **SCIM Endpoint URL **field appears only if the configurations for the IdP in the **Basic **tab are completed and saved.
[See image.](#scim-url)
- **Authentication Method**: Select the authentication method.
- **Bearer Token**: Copy the bearer token. It's a unique alphanumeric string that is used by the SCIM client to make authenticated API calls to the Zscaler SCIM server. You need this token when configuring your IdP for SCIM provisioning.
- **Generate Token**: Click to generate a new bearer token for security reasons. If you're generating a new bearer token for an existing SCIM configuration, ensure you update the token for your IdP.
- **SCIM Attribute**: Enter the SCIM attribute that you want to map.
- **User Attribute**:** **Select the user attribute that you want to map to the SCIM attribute. Click** Add More** to map additional attributes. To remove an attribute mapping, click the **Delete** icon.
[See image.](#provisioning)
- Click **Save**.
[]**IdP Metadata URL**: Paste the link to the IdP's metadata file and click **Fetch**. You can get the URL from the IdP.
[]**IdP Metadata**: Upload the metadata file of the IdP. Click **Upload IdP Metadata** and select the file.
- []**IdP Issuer URI**: Enter the issuer URI of the IdP. This value is the entity ID in the IdP's metadata.
- **IdP Single Sign-On URL**: Enter the IdP's URL where the user is redirected for authentication.
-
**IdP Certificate**: Upload the SAML certificate that is used to verify the digital signature of the IdP. This is the certificate you downloaded from your IdP. The certificate must be in base-64 encoded PEM format. The file extension must be .pem and have no other periods (.) in the file name.
You can upload more than one IdP certificate, if required.
- **SP Entity ID**: Copy the service provider (SP) entity ID. You need this ID when configuring ZIdentity as your SP.
- **SP URL**: Copy the SP entity ID. You need this URL when configuring ZIdentity as your SP on the IdP portal.
[]![Basic Tab in the Add Identity Provider window for SAML protocol.](/downloads/Basic-tab.png)
[]![Advanced Tab in Add Identity Provider page.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-adding-saml-identity-providers-doc-55564/add-advanced-tab.png)
[]![Configuring JIT provisioning](/downloads/zslogin/authentication/external-idp-configuration/adding-openid-providers/zidentity-saml-provisioning_0.png)
[]
![SCIM Endpoint URL Option](/downloads/zslogin/authentication/external-idp-configuration/adding-openid-providers/zidentity-scim-ednpoint-url_0.png)
[]
![IdP Attribute Mapping](/downloads/zslogin/authentication/external-idp-configuration/adding-openid-providers/zidentity-advanced-saml-session-attribute_0.png)