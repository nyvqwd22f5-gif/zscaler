# Configuring Auth0 as an External IdP
Source: https://help.zscaler.com/zidentity/configuring-auth0-external-idp
PDF: https://help.zscaler.com/pdf/com/en/1499341.pdf

This guide provides information on how to configure Auth0 as the OpenID Provider (OP) for the ZIdentity to facilitate single sign-on (SSO) to various Zscaler services for admin access management.
Prerequisites
Ensure that you have:
- A subscription to Auth0
- An existing user directory in Auth0
- A ZIdentity account with an admin role that allows you to add an IdP configuration
IdP-Initiated SSO for ZIdentity Tenants Enabled with Experience Center
During the IdP-initiated SSO for ZIdentity, tenants using OIDC or SAML protocols are redirected as follows:
- [OIDC Protocol](#OIDC-protocol-redirection)
- [SAML Protocol](#SAML-protocol-redirection)
To change the default redirection, contact [Zscaler Support](/contact-support).
[]
All admins authenticating using the SAML protocol for ZIdentity and IdP integrations are redirected to Experience Center. However, if the `zidServiceId` attribute is configured in the IdP within the ZIdentity tenant, then the admins are redirected to the ZIdentity Admin Portal instead of Experience Center.
[]
ZIdentity tenants that are enabled with Experience Center at the time of tenant creation and admins using OIDC protocol for ZIdentity and IdP integrations are redirected to the Experience Center.
ZIdentity tenants that are not enabled with Experience Center at the time of tenant creation and admins using OIDC protocol for ZIdentity and IdP integrations are redirected to the ZIdentity Admin Portal. They can click the Experience Center link and go to the Experience Center from the [ZIdentity Landing page](/zidentity/accessing-and-navigating-zidentity-landing-page).
[See image.](#Zidentity_Landing_Page)
If you want to change this default behavior and have users redirected to the Experience Center, raise a Support ticket with the ticket type set to **Provisioning**.
Configuring Auth0 as OP for ZIdentity
Complete the following steps to set up Auth0 as an OP for ZIdentity:
- [1. Configure a custom OIDC application in Auth0.](#add-app-auth0)
- [2. Set up Auth0 as an OP for ZIdentity.](#setup-auth0-as-op)
- [3. Provision users for ZIdentity.](#provision-users-auth0)
- [4.(Optional) Enable step-up authentication.](#enabling-step-up-authentication)
- []Log in to the [Auth0 Dashboard](https://manage.auth0.com/).
- Go to **Applications **> **Applications**.
-
Click **Create Application**.
[See image.](#create-app-button-auth0)
-
In the **Create Application **window:
- **Name**: Enter a name for the application.
- **Application Type**: Select the **Regular Web Application **option.
- Click **Create**.
[See image.](#create-app-auth0)
The application is created.
- On the application page, select the **Settings **tab, and do the following:
- Under the **Basic Information **section, copy the **Client ID** and **Client Secret **values.
[See image.](#client-id-secret-auth0)
- Expand the **Advanced Settings **section, select the **Endpoints **tab, and copy the **OpenID Configuration **value.
[See image.](#metadata-url-auth0)
- []Log in to the ZIdentity Admin Portal.
- Go to **Integration **> **External Identities**.
- Click **Add Primary IdP** (or **Add Secondary IdP**).
The **Add Primary Identity Provider** or **Add Secondary Identity Provider** window appears.
- On the **Basic **tab:
- In the **General **section:
- **Name**: Enter a name for the IdP.
- **Identity Vendor**: Select **Others** from the drop-down menu.
- **Domain**: Select the domain for which the IdP is responsible for authenticating the users. This allows the Zscaler service to display the correct IdP to authenticate an incoming user.
- **Protocol**: Select **OIDC**.
- **Status**: Select **Enabled**.
-
**Login ID Attribute**: Enter an attribute whose value must be used as the login ID. This attribute must exist in the tokens received from the IdP. By default, the `preferred_username` attribute is populated in this field when the **OIDC** option is selected in the **Protocol** field. You can use any attribute that is present in the [ID token](https://openid.net/specs/openid-connect-core-1_0.html#IDToken) or the response of the [UserInfo endpoint](https://openid.net/specs/openid-connect-core-1_0.html#UserInfo), provided its value is in the email address format (e.g., <user_name>@domain.com>).
- Ensure that the domain part of the email addresses received in the ID tokens match with one of the domains configured in ZIdentity.
- Ensure that the attribute you enter matches exactly with the attribute received in the ID token or the UserInfo endpoint.
-
**Enforce Zscaler Admin MFA**: Enable this option to ensure that admins using an external IdP authenticate with the multi-factor authentication (MFA) process in ZIdentity, irrespective of whether MFA is configured on the external IdP.
An email is sent to all super admins in ZIdentity when the **Enforce Zscaler Admin MFA **option is disabled.
- [See image.](#basic-setup-auth0)
-
In the **OIDC Configuration **section:
- Paste the **Client ID **and **Client Secret **values copied from the Auth0 Dashboard in [step 1e](#add-app-auth0) to the respective fields.
- Paste the **OpenID Configuration **value copied from the Auth0 Dashboard in [step 1e](#add-app-auth0) to the **Metadata URL **field and click **Fetch**.
- Copy the **Redirect URI **value.
- Add required scopes to the **Requested Scopes** field. By default, when the OIDC protocol is selected, the `openid`, `email`, and `profile` scopes are added.
[See image.](#oidc-setup-auth0)
- Click **Save**.
- On the Auth0 dashboard, go to **Applications** > **Applications**, and click the application created for Auth0 in [step 1](#add-app-auth0).
-
On the application page, go to **Settings > Application URIs**, and do the following:
- Paste the **Redirect URI** value copied from the ZIdentity Admin Portal to the **Application Login URI **and **Allowed Callback URLs **fields.
- Click **Save Changes**.
[See image.](#redirect-uri-auth0)
- []In the ZIdentity Admin Portal, go to **Integration **> **External Identities**.
- Locate the IdP entry created for Auth0 on the **Primary Identity Provider **(or **Secondary Identity Providers**) tab and click the **Edit **icon.
-
In the **Edit Primary IdP **(or **Edit Secondary IdP**) window:
- Select the **Provisioning **tab.
- Select **Enable Just-in-time (JIT) Provisioning**.
-
Map the ZIdentity user attributes with the appropriate Auth0 attributes as necessary. The mapping of the `Primary Email` attribute is mandatory as it is required for functionalities, such as password resetting and multi-factor authentication. By default, the following attributes in ID tokens are mapped with the corresponding user attributes in ZIdentity.
[See image.](#jit-zslogin-auth0)
| Attribute in ID Tokens | Default ZIdentity User Attributes |
| ---------------------- | --------------------------------- |
| given_name | First Name |
| family_name | Last Name |
| name | Display Name |
- If the extenral IdP is configured to send different attributes for `First Name`, `Last Name`, or `Display Name`, then you must map those attributes. For example, if the ID token from the external IdP includes `Surname` instead of `family_name`, then you must map it with the `Last Name` user attribute in ZIdentity. [See image.](#oidc-id-token-sample)
- While mapping attributes, ensure that the attributes you enter in the **Just-in-time Attribute** field match exactly with the attributes that would be received in the ID tokens.
- Click **Update**.
[]
You can configure step-up authentication to extend the existing authentication process by requiring multi-factor authentication (MFA) when needed, ensuring that access to high-risk or sensitive data is protected.
Prerequisites
Before configuring [step-up authentication](/zidentity/understanding-step-authentication), ensure that:
- Zscaler Client Connector version 4.7 or later is deployed for the users in your organization.
- ZIdentity is enabled for both admins and users.
- Step-up authentication is enabled for ZIdentity, Zscaler Internet Access (ZIA), and Zscaler Private Access (ZPA) tenants.
To enable step-up authentication:
- [a. Configure authentication levels in the ZIdentity Admin Portal.](/zidentity/configuring-authentication-levels)
- [b. Enable ACR values and configure the necessary policies in the external IdPs.](#external-idp-configuration)
- [c. Map authentication levels and ACR values in the ZIdentity Admin Portal.](#al-acr-mapping)
- [d. Configure access policies in supported Zscaler services.](#access-policies-mapping)
[]In the [external IdP integrated with ZIdentity](/zidentity/about-external-identity-providers), configure the necessary ACR values and authentication policies. To learn more about the configuration, refer to the respective product documentation.
[]
- Go to **Integration **> **External Identities**.
- Locate the IdP under the **Primary Identity Provider** (or **Secondary Identity Providers**) tab and click the **Edit **icon.
-
In the **Edit Primary IdP** (or **Edit Secondary IdP**) window:
- Select the **Advanced** tab.
-
Under the **Levels to Authentication context mapping** section, enter the **ACR Claim** value for each authentication level. To learn more about the supported ACR claims in external IdP, refer to the respective product documentation.
Ensure that you map proper ACR claims for each level depending on the hierarchy. The highest level of authentication must be mapped to the ACR value for the strongest context.
[See image.](#al-acr-mapping-zidentity)
- Click **Update**.
[]You can configure the necessary policies in the following Zscaler services as required:
- ZPA: [Configure Access Policies](/zpa/configuring-access-policies) for the target application or app segment with the **Conditional Access **as the **Rule Action**. Ensure that the necessary authentication level is selected using the **Step-up Authentication Level** field.
- ZIA: [Configure the URL Filtering Policy](/zia/configuring-url-filtering-policy) and [Cloud App Control Policies](/zia/adding-rules-cloud-app-control-policy) with the **Conditional Access **as the **Action**. Ensure that the necessary authentication level is selected using the **Authentication Level **field.
[]![Mapping authentication levels with ACR values in ZIdentity](/downloads/zidentity/authentication/configuring-step-authentication/zidentity-al-acr-mapping.png)
[]![Applications page in Auth0 with the option to create an application highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-auth0-external-idp/zslogin-auth0-add-app-button.jpg)
[]
![Creating an application in Auth0 with the option to create a regular application highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-auth0-external-idp/zidentity-app-selection_0.jpg)
[]
![Configuring a client application in Auth0 showing the basic information](/downloads/zidentity/integration/external-idp-configuration/configuring-auth0-external-idp/zidentity-app-creation_0.jpg)
[]
![List of OIDC endpoints in Auth0 with the Well-Known Configuration URL highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-auth0-external-idp/zslogin-discovery-endpoint-auth0.jpg)
[]
![Configuring SSO in Auth0 for an application with the Application URIs highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-auth0-external-idp/zslogin-redirect-uri-auth0.jpg)
[]
![Configuring basic information for an IdP in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-auth0-external-idp/Basic-tab.png)
[]
![Configuring scopes for an OIDC-based IdP in ZIdentity Admin Portal](/downloads/zidentity/integration/external-idp-configuration/configuring-auth0-external-idp/zidentity-oidc-configuration-auth0.png)
[]![A sample ID token with blurred sensitive information.](/downloads/zidentity/integration/external-idp-configuration/configuring-auth0-external-idp/zidentity-id-token-sample%20(2).png)
[]
![Configuring JIT provisioning for an IdP in ZIdentity Admin Portal](/downloads/zidentity/integration/external-idp-configuration/configuring-auth0-external-idp/zidentity-jit-mapping-no-groups%20(1).png)
[]
![ZIdentity Landing page with highlighted banner at the top.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-configuring-okta-external-idp-doc-57200/zid-landing-page-1.png)