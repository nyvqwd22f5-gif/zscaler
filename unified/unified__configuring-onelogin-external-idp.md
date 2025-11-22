# Configuring OneLogin as an External IdP
Source: https://help.zscaler.com/unified/configuring-onelogin-external-idp
PDF: https://help.zscaler.com/pdf/com/en/1505486.pdf

This guide provides information on how to configure OneLogin as the OpenID Provider (OP) for the ZIdentity to facilitate single sign-on (SSO) to various Zscaler services for admin access management.
Prerequisites
Ensure that you have:
- A subscription to OneLogin
- An existing user directory in OneLogin
- A ZIdentity account with an admin role that allows you to add an IdP configuration
IdP-Initiated SSO for ZIdentity Tenants Enabled with Experience Center
During the IdP-initiated SSO for ZIdentity, tenants using OIDC or SAML protocols are redirected as follows:
- [OIDC Protocol](#OIDC-protocol-redirection)
- [SAML Protocol](#SAML-protocol-redirection)
To change the default redirection, contact [Zscaler Support](/contact-support).
Configuring OneLogin as OP for ZIdentity
Complete the following steps to set up OneLogin as an OP for ZIdentity:
- [1. Configure a custom OIDC application in OneLogin.](#add-oidc-app-onelogin)
- [2. Set up OneLogin as an OP for ZIdentity.](#setup-onelogin-as-op)
- [3. Provision users for ZIdentity.](#onelogin-user-provisioning)
- [4. (Optional) Enable step-up authentication.](#enabling-step-up-authentication)
[]
All admins authenticating using the SAML protocol for ZIdentity and IdP integrations are redirected to Experience Center. However, if the `zidServiceId` attribute is configured in the IdP within the ZIdentity tenant, then the admins are redirected to the ZIdentity Admin Portal instead of Experience Center.
[]
ZIdentity tenants that are enabled with Experience Center at the time of tenant creation and admins using OIDC protocol for ZIdentity and IdP integrations are redirected to the Experience Center.
ZIdentity tenants that are not enabled with Experience Center at the time of tenant creation and admins using OIDC protocol for ZIdentity and IdP integrations are redirected to the ZIdentity Admin Portal. They can click the Experience Center link and go to the Experience Center from the [ZIdentity Landing page](/zidentity/accessing-and-navigating-zidentity-landing-page).
[See image.](#ec-zidlpage)
If you want to change this default behavior and have users redirected to the Experience Center, raise a Support ticket with the ticket type set to **Provisioning**.
- []Log in to the OneLogin Portal.
- Go to **Applications**.
-
Click **Add App**.
[See image.](#add-app-onelogin)
The **Find Applications** window appears.
-
In the **Find Applications** window, search for `oidc`, and click the **OpenID Connect (OIDC)** option from the search results.
[See image.](#find-app-onelogin)
The **Add OpenId Connect (OIDC)** page appears.
-
On the **Add OpenId Connect (OIDC)** page:
- **Display Name**: Enter a name for the application.
- **Description**: (Optional) Enter a description for the application.
- (Optional) Upload an icon for the application.
- Click **Save**.
[See image.](#setup-app-onelogin)
The OIDC application is created.
-
Seelct the **SSO** tab and copy the** Client ID**,** Client Secret**, and **Issuer URL **values.
To copy the **Issuer URL** value, right-click the **Well-known configuration** link, and select **Copy Link Address **(or an equivalent option in your browser).
[See image.](#onelogin-well-known-url)
[See image.](#secrets-app-onelogin)
- Assign users to the application either manually or roles and mapping in OneLogin. To learn more, refer to the [OneLogin documentation](https://onelogin.service-now.com/support?id=kb_article&sys_id=e5e35e0047ccbd509d8dfd1f536d43c2&kb_category=e9866930db185340d5505eea4b9619b7).
- []Log in to the Admin Portal.
- Go to **Administration > Identity > ZIdentity > External Identities**.
- Click **Add Primary IdP** (or **Add Secondary IdP**).
The **Add Primary Identity Provider** or **Add Secondary Identity Provider** window appears.
- On the **Basic **tab:
-
In the **General **section:
- **Name**: Enter a name for the IdP.
- **Identity Vendor**: Select **OneLogin** from the drop-down menu.
- **Domain**: Select the domain for which the IdP is responsible for authenticating the users. This allows the Zscaler service to display the correct IdP to authenticate an incoming user.
- **Protocol**: Select **OIDC**.
- **Status**: Select **Enabled**.
-
**Login ID Attribute**: Enter an attribute whose value must be used as the login ID. This attribute must exist in the tokens received from the IdP. By default, the `preferred_username` attribute is populated in this field when the **OIDC** option is selected in the **Protocol** field. You can use any attribute that is present in the ID token or UserInfo response, provided its value is in the email address format (e.g., <user_name>@domain.com>).
- Ensure that the domain part of the email addresses received in the ID tokens match with one of the domains configured in ZIdentity.
- Ensure that the attribute you enter matches exactly with the attribute in the ID token or UserInfo endpoint.
-
**Enforce Zscaler Admin MFA**: Enable this option to ensure that admins using an external IdP authenticate with the multi-factor authentication (MFA) process in ZIdentity, irrespective of whether MFA is configured on the external IdP.
An email is sent to all super admins in ZIdentity when the **Enforce Zscaler Admin MFA **option is disabled.
[See image.](#basic-setup-onelogin)
-
In the **OIDC Configuration **section:
- Paste the **Issuer URL **value copied from the OneLogin Portal in [step 1f](#add-oidc-app-onelogin) to the **Metadata URL **field and click **Fetch**.
-
[]Copy the **Redirect URI** value. This value will be used in the OIDC application in the OneLogin Portal in the subsequent steps.
If you are configuring OneLogin as a secondary IdP in the Admin Portal, the final segment in the **Redirect URI** is required for configuring **Login URL** in the OneLogin Portal.
- Paste the **Client ID **and **Client Secret **values copied from the OneLogin Portal [step 1f](#add-oidc-app-onelogin) to the respective fields.
- In the **Requested Scopes** section, add the required scopes. By default, when the OIDC protocol is selected, the `openid`, `email`, and `profile` scopes are added.
[See image.](#oidc-setup-onelogin)
- In the OneLogin Portal, go to **Applications**, click the newly created OIDC application in [step 1](#add-oidc-app-onelogin), and do the following:
-
On the **Configuration **tab:
- Enter the following value for the **Login URL** field:
-
If you are configuring OneLogin as your primary IdP in the Admin Portal:
`https://<your_domain>.zslogin.net/?idp_id=default `
[See image.](#primpary-idp-example)
-
If you are configuring OneLogin as your secondary IdP in the Admin Portal:
`https://<your_domain>.zslogin.net/?idp_id=<final_segment_from_redirect_URI>`
[See image.](#secondary-idp-example)
- Paste the **Redirect URI** value copied from the Admin Portal to the **Redirect URI's** field.
[See image.](#redirect-uri-onelogin)
- Click **Save**.
- []In the Admin Portal, go to **Administration > Identity > ZIdentity > External Identities**.
- Locate the IdP entry created for OneLogin on the **Primary Identity Provider **(or **Secondary Identity Providers**) tab and click the **Edit **icon.
-
In the **Edit Primary IdP **(or **Edit Secondary IdP**) window:
- Select the **Provisioning **tab, and select **Enable Just-in-time (JIT) Provisioning**.
- Map the ZIdentity user attributes with the appropriate OneLogin attributes as necessary. The mapping of the `Primary Email` attribute is mandatory as it is required for functionalities, such as password resetting and multi-factor authentication. By default, the following attributes in ID tokens are mapped with the corresponding user attributes in ZIdentity.
| Attribute in ID Tokens | Default ZIdentity User Attributes |
| ---------------------- | --------------------------------- |
| given_name | First Name |
| family_name | Last Name |
| name | Display Name |
- If the external IdP is configured to send different attributes for `First Name`, `Last Name`, or `Display Name`, then you must map those attributes. For example, if the ID token from the external IdP includes `Surname` token instead of `family_name`, then you must map it with the `Last Name` user attribute in ZIdentity. [See image.](#oidc-sample-id-token)
- While mapping attributes, ensure that the attributes you enter in the **Just-in-time Attribute** field match exactly with the attributes that would be received in the ID tokens.
[See image.](#jit-zslogin-onelogin)
- Click **Update**.
[]You can configure step-up authentication to extend the existing authentication process by requiring multi-factor authentication (MFA) when needed, ensuring that access to high-risk or sensitive data is protected.
Before configuring step-up authentication, make sure you have configured authentication levels and access policies. To learn more, see [Understanding Step-Up Authentication](/unified/understanding-step-authentication).
To enable step-up authentication:
- In the Admin Portal, go to **Administration > Identity > ZIdentity > External Identities**.
- Locate the IdP entry created for OneLogin on the **Primary Identity Provider** (or **Secondary Identity Providers**) tab and click the **Edit **icon.
- In the **Edit Primary IdP** (or **Edit Secondary IdP**) window:
- Select the **Advanced** tab.
-
In the **Levels to Authentication context mapping** section, enter the **ACR Claim** value for each authentication level. To learn more about the supported ACR Claims in OneLogin, refer to the [OneLogin Technical documentation](https://developers.onelogin.com/openid-connect/api/authorization-code).
Ensure that you map proper ACR claims for each level depending on the hierarchy. The highest level of authentication must be mapped to the ACR value for the strongest context.
- Click **Update**.
[]
![Applications page win OneLogin Portal with the option to add an app highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-onelogin-external-idp/zslogin-add-app-onelogin.png)
[]
![Finding an application in OneLogin Portal with OIDC Connector option highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-onelogin-external-idp/zslogin-add-oidc-onelogin.png)
[]
![Adding an OIDC application in OneLogin Portal](/downloads/zidentity/integration/external-idp-configuration/configuring-onelogin-external-idp/zidentity-resking-update_0.png)
[]![Copying the Well-Known Configuration URL from OneLogin Portal](/downloads/zidentity/integration/external-idp-configuration/configuring-onelogin-external-idp/zidentity-onelogin-url_1_0.png)
[]
![Enabling OIDC for an application in OneLogin with client credentials highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-onelogin-external-idp/zslogin-onelogin-id-secret-issuer-url.png)
[]![Configuring SSO for an application in OneLogin with the default IDP ID highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-onelogin-external-idp/zidentity-onelogin-primary-idp-id_0.png)
[]![Configuring SSO for an application in OneLogin with IDP ID highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-onelogin-external-idp/zidentity-onelogin-idp-id-secondary_0_0.png)
[]
![Configirung Redirrect URIs in OneLogin Portal](/downloads/zidentity/integration/external-idp-configuration/configuring-onelogin-external-idp/zidentity-onelogin-login-url_0.png)
[]
![Configuring basic information for an IdP in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-onelogin-external-idp/Basic-tab.png)
[]
![Configuring OIDC for an IdP with some options highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-onelogin-external-idp/zidentity-onelogin-oidc-configuration_0.png)
[]![A sample ID token with blurred sensitive information.](/downloads/zidentity/integration/external-idp-configuration/configuring-onelogin-external-idp/zidentity-id-token-sample%20(1).png)
[]
![Configuring JIT Provisioning for an IdP in ZIdentity Admin Portal](/downloads/zidentity/integration/external-idp-configuration/configuring-onelogin-external-idp/zidentity-jit-mapping-no-groups_0.png)
[]
![Click the link in the banner to go to the Experience Center](/downloads/unified/administration/zidentity/idp-configuration/external-idp-configuration/configuring-onelogin-external-idp/zid-landing-page-withbanner.png)