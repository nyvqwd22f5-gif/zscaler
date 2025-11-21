# Configuring Okta as an External IdP
Source: https://help.zscaler.com/zidentity/configuring-okta-external-idp
PDF: https://help.zscaler.com/pdf/com/en/1499411.pdf

This guide provides information on how to configure Okta as an external Identity Provider (IdP) for ZIdentity to facilitate single sign-on (SSO) to various Zscaler services for admin access management. You can configure Okta as an external IdP to enable SSO to ZIdentity using OpenID Connect (OIDC) or Security Assertion Markup Language (SAML) authentication protocols.
Zscaler and Okta are technology partners. To learn more about integrating Zscaler and Okta, see the [Zscaler and Okta Deployment Guide](/zscaler-technology-partners/zscaler-and-okta-deployment-guide).
Depending on the authentication protocol, you can provision users to ZIdentity from Okta using Just-in-Time (JIT) provisioning or System for Cross-domain Identity Management (SCIM) provisioning.
If you want to leverage [step-up authentication](/zidentity/understanding-step-up-authentication), it is recommended to use OIDC-based integrations as most IdPs only support step-up authentication with the OIDC protocol.
- [OIDC-Based Authentication via OIN App Integration](#oidc-okta-oin)
- [OIDC-Based Authentication via Custom App Integration](#oidc-okta-custom-app)
- [SAML-Based Authentication](#saml-okta-custom-app)
- [IdP-Initiated SSO for ZIdentity Tenants Enabled with Experience Center](#idp-initiated-sso-flow)
[]
This section provides information on how to use the Okta Integration Network (OIN) app integration to configure Okta as your OpenID Provider (OP) for ZIdentity for facilitating single sign-on (SSO) to various Zscaler services for admin access management.
An OIN-based integration uses SCIM-based provisioning and Zscaler recommends the OIN-based integration. If your Okta subscription does not include SCIM provisioning, Zscaler recommends using the custom OIDC application as Okta does not support sending custom claims such as `Groups` or `Departments` with the OIN application. To learn more, see [OIDC-Based Authentication via Custom App Integration](/zidentity/configuring-okta-external-idp#oidc-okta-custom-app).
Prerequisites
Ensure that you have:
- An Okta account with admin privileges
- A SCIM provisioning subscription for Okta
- An existing user directory in Okta
- A ZIdentity account with an admin role that allows you to add an IdP configuration
Supported Features
The following features are supported for OIDC and SCIM:
Supported Features for OIDC
- JIT Provisioning
- IdP-Initiated SSO
- [SP-Initiated SSO](#sp-initiated-sso)
Supported Features for SCIM
- Create Users
- Update User Attributes
- Deactivate Users
- Group Push
Configuring Okta as OP for ZIdentity
To set up Okta as an OP for ZIdentity:
- [1. Configure OIN app integration for ZIdentity in Okta.](#oin-app-integration)
- [2. Set up Okta as an OP for ZIdentity.](#okta-as-op-zslogin)
- [3. Provision users for ZIdentity using JIT or SCIM provisioning.](#provision-user-oin-jit-scim)
- [4. (Optional) Enable step-up authentication.](#enabling-step-up-authentication-oin)
- []Log in to the [Okta Admin Console](https://support.okta.com/help/s/article/How-to-access-Okta-admin-console-when-Default-App-for-Sign-In-Widget-is-enabled?language=en_US).
- Go to **Applications** > **Applications**.
-
Click **Browse App Catalog**.
[See image.](#okta-app-catalog-button)
- Search for `zscaler`.
-
From the search results, locate and click the **Zscaler **app.
[See image.](#search-app-oin)
-
In the app details page, click **Add Integration**.
[See image.](#add-oin-app)
-
In the **Add Zscaler** window, enter a name for the **Application label **field.
[See image.](#oin-general-settings)
-
Click **Done**.
An OIN app for ZIdentity is added.
-
In the application page, on the **Sign On** tab, copy the **Client ID** and **Client secret **values. These values are used in a subsequent step when configuring Okta as an OP for ZIdentity.
[See image.](#sign-on-tab-oin-app)
-
To obtain the metadata URL, right-click the** OpenID Provider Metadata** text, and copy the URL. This value is used in a subsequent step when configuring Okta as an OP for ZIdentity. The metadata URL has the following format:
https://`<your_subdomain>`.okta.com/oauth2/default/.well-known/openid-configuration
[See image.](#metadata-url-copy)
- []Log in to the ZIdentity Admin Portal.
- Go to **Integration** > **External Identities**.
- Click **Add Primary IdP** (or **Add Secondary IdP**).
The **Add Primary Identity Provider** or **Add Secondary Identity Provider** window appears.
- On the **Basic **tab:
-
Under the **General **section:
- **Name**: Enter a name for the IdP.
- **Identity Vendor**: Select **Okta** from the drop-down menu.
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
[See image.](#basic-tab-oidc-oin)
-
Under the **OIDC Configuration **section:
- Enter the following value for the **Metadata URL **field copied from the Okta Admin Console.
- Click **Fetch**.
-
Copy the **Redirect URI** value. This value is used in a subsequent step.
If you are configuring Okta as your secondary IDP, the final segment in the **Redirect URI** is required for configuring **Initiate Login URI **in the Okta Admin Console.
- Paste the **Client ID **and **Client Secret **values copied from the Okta Admin Console.
- In the **Requested Scopes** section, add the required scopes. By default, when the OIDC protocol is selected, the `openid`, `email`, and `profile` scopes are added.
[See image.](#oin-oidc-configuration-basic)
- Click **Save**.
- Go to the Okta Admin Console, and go to the OIN app added for ZIdentity.
- On the **Sign On **tab:
- Click **Edit**.
- Paste the **Redirect URI** copied from ZIdentity Admin Portal.
- Enter the following value for the **Initiate Login URI** field:
-
If you are configuring Okta as your primary IdP in the ZIdentity Admin Portal:
`https://<your_domain>.zslogin.net/?idp_id=default `
[See image.](#zslogon-redirect-uri)
-
If you are configuring Okta as your secondary IdP in the ZIdentity Admin Portal:
`https://<your_domain>.zslogin.net/?idp_id=<final_segment_from_redirect_URI>`
[See image.](#idp-id-secondary-example)
- Click **Save**.
- [][JIT provisioning](#provision-user-oin-jit)
- [SCIM provisioning](#oin-scim-provisioning)
[]Users created in ZIdentity via SCIM cannot be updated using JIT provisioning. These user records must be updated via SCIM provisioning only.
- In the ZIdentity Admin Portal, go to **Integration **> **External Identities**.
- Locate the IdP entry created for Okta under the **Primary Identity Provider** (or **Secondary Identity Providers**) tab and click the **Edit **icon.
- In the **Edit Primary IdP** (or **Edit Secondary IdP**) window:
- Select the **Provisioning **tab, and select **Enable Just-in-time (JIT) Provisioning**.
-
Map the required attributes. The mapping of the `Primary Email` attribute is mandatory as it is required for functionalities, such as password resetting and multi-factor authentication. By default, the following attributes in ID tokens are mapped with the corresponding user attributes in ZIdentity.
| Attribute in ID Tokens | Default ZIdentity User Attributes |
| ---------------------- | --------------------------------- |
| given_name | First Name |
| family_name | Last Name |
| name | Display Name |
- If the external IdP is configured to send different attributes for `First Name`, `Last Name`, or `Display Name`, then you must map those attributes. For example, if the ID token from the external IdP includes `Surname` instead of `family_name`, then you must map it with the `Last Name` user attribute in ZIdentity. [See image](#id-token-sample-1)
- While mapping attributes, ensure that the attributes you enter in the **Just-in-time Attribute** field match exactly with the attributes that would be received in the ID tokens.
[See image.](#oin-jit-image)
- Click **Update**.
- In the Okta Admin Console, go to **Applications **> **Applications**.
- Open the OIN app created for ZIdentity and go to the **Assignments **tab.
-
Add users and groups to the application using the **Assign **drop-down menu.
[See image.](#oin-jit-users-groups)
The JIT provisioning with Okta users is configured for ZIdentity.
- []In the ZIdentity Admin Portal, go to **Integration **> **External Identities**.
- Locate the IdP entry created for Okta under the **Primary Identity Provider **(or **Secondary Identity Providers**) tab and click the **Edit **icon.
- In the **Edit Primary IdP **(or **Edit Secondary IdP**) window:
- On the **Provisioning **tab, select **Enable SCIM Provisioning**.
-
Copy the **SCIM Endpoint URL**. This value is used in a subsequent step.
The **SCIM Endpoint URL** field appears only if the configurations for the IdP in the **Basic** tab are completed and saved.
[See image.](#scim-endpoint-url)
- Click **Generate Token **and copy the **Bearer Token** value. This value is used in a subsequent step.
-
(Optional) Map the SCIM attribute (e.g., `addresses`) with the corresponding ZIdentity user attribute. This mapping is required only for attributes that need to be mapped to a custom [user attribute](/zidentity/adding-user-attributes) in ZIdentity.
[See image.](#scim-provisioning-oin)
- Click **Update**.
- Go the Okta Admin Console, and go to the OIN app added for ZIdentity.
- On the **Provisioning **tab:
-
Click **Configure API Integration**.
[See image.](#configure-api-integration-oin)
- Select **Enable API integration**.
- Paste the **SCIM Endpoint URL **value copied from the ZIdentity Admin Portal to the **Base URL **field.
- Paste the **Bearer Token **value copied from the ZIdentity Admin Portal to the **API Token **field.
- Click **Test API Credentials**.
-
Click **Save**.
[See image.](#zslogin-oin-save-token)
-
Click **Edit**.
[See image.](#oin-edit-provision-tab)
-
Under the **Provisioning to App** section, enable the **Create Users**, **Update Users to Attributes**, and **Deactivate** **Users **options**.**
[See image.](#oin-enable-options)
- Click **Save.**
- On the **Assignments **tab, click the **Assign **drop-down menu, and select an option to assign users or groups:
- [Assign users](#assign-users-oin)
- [Assign groups](#assign-groups-oin)
-
To sync groups and the assigned users or members from Okta to ZIdentity, go to the **Push Groups **tab, and select an option to push groups by name or rule:
- [Push Groups by name](#push-groups-oin-name)
- [Push Groups by rule](#push-groups-oin-rule)
To learn more about group push, refer to the [Okta technical documentation](https://help.okta.com/en-us/content/topics/users-groups-profiles/usgp-about-group-push.htm).
The SCIM provisioning with Okta users is configured for ZIdentity.
[]
-
Select **Assign to People**.
[See image.](#assign-to-people-oin)
-
Search and locate users you want to assign, and click **Assign**.
[See image.](#assign-button-zslogin)
- Click **Done**.
[]
-
Select **Assign to Groups**.
[See image.](#groups-oin-button)
-
Search and locate the groups you want to assign, and click **Assign**.
[See image.](#groups-assign-button)
[]
-
Select the **Find groups by name **option from the **Push Groups **drop-down menu.
[See image.](#by-name-menu-oin)
By default, the **Push group memberships immediately **option is selected to push groups immediately to ZIdentity. However, you can disable it if you do not want to do this.
-
Enter the name of the group that you want to push and select the group from the drop-down menu.
[See image.](#group-oin-new-name)
- Click **Save **or click **Save & Add Another** if you want to push multiple groups.
- Click **Close**.
-
On the **Push Groups **tab, click **By name** on the left-side navigation and verify that all your groups have been added. Ensure that the **Push Status** for each group is **Active**.
[See image.](#active-group-by-name-oin)
[]
-
Select the **Find groups by rule** option from the **Push Groups **drop-down menu.
[See image.](#by-rule-menu-oin)
- In the **Push groups by rule **window:
- **Rule name**: Enter a name for the rule.
- **Group name**: Select a match condition from the drop-down menu and enter a string that should be used to find a group with the name matching the condition. For example, you can select **Contains** as the match condition and enter `Admins` as the string to match all groups that has the string "Admin" and push them to ZIdentity.
-
**Group description**: Select a match condition from the drop-down menu and enter a string that should be used to find a group with the description matching the condition. For example, you can select **Contains** as the match condition and enter `For Admins` as the string to match all groups that has the string "For Admins" in the description and push them to ZIdentity.
By default, the **Immediately push groups found by this rule **option is selected to push groups immediately to ZIdentity. However, you can disable it if you do not want to do this.
[See image.](#rule-define-push-oin)
- Click **Create Rule**.
-
On the **Push Groups **tab, select the rule name created in the previous step under the **By rule **option** **on the left-side navigation, and verify that all of your groups have been added. Ensure that the **Push Status** for each group is **Active**.
[See image.](#active-rule-groups-oin)
[]After setting up the OIN-based integration, ZIdentity administrators can log in to the ZIdentity Admin Portal using Okta.
To log in to ZIdentity Admin Portal via Okta:
-
Go to the ZIdentity Admin Portal using your vanity URL specific to your ZIdentity tenant. For example, the vanity URL has the following format:
`https://customername.zslogin.net/`
-
Enter your username registered with Okta.
If the username is valid, you are redirected to the Okta page for authentication. After successful authentication, you are logged in to the ZIdentity Admin Portal.
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
[]
![Obtaining metadata URL in Okta with appropriate option highlighted](/downloads/zslogin/administration/authentication/oidc-configuration-guides/oidc-configuration-guide-okta-oin-app/zslogin-metadate-url.png)
[]
![List of applications in Okta with the option to browse app catalog highlighted](/downloads/zslogin/administration/authentication/oidc-configuration-guides/oidc-configuration-guide-okta-oin-app/zslogin-app-catalog-button.png)
[]
![Finding ZIdentity app in Okta from the App Integration Catalog](/downloads/zslogin/administration/authentication/oidc-configuration-guides/oidc-configuration-guide-okta-oin-app/zslogin-add-app-search.png)
[]
![Adding ZIdentity app integration to Okta with the Add Integration button highlighted](/downloads/zslogin/administration/authentication/oidc-configuration-guides/oidc-configuration-guide-okta-oin-app/zslogin-add-oin-integration-button.png)
[]
![Adding ZIdentity app to Okta](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zidentity-oin-add-zscaler.jpg)
[]
![Configuring Sign On settings in Okta for ZIdentity with client ID and client secret highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zslogin-okta-oin-id-secret.png)
[]
![Configuring basic information for IdP in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/basic-tab.png)
[]
![Configuring OIDC options in ZIdentity with some fields highlighted](/downloads/zslogin/authentication/external-idp-configuration/configuring-okta-external-idp/zidentity-okta-oic-basic-oidc-configuration.png)
[]
![Locating IdP ID parameter for primary IdP](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zidentity-okta-primary-idp-id_0.png)
[]![Locating IdP ID parameter for secondary IdP](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zidentity-okta-secondary-idp.png)
[]
![Enabling SCIM provisioning in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zidentity-scim-saml-oin.png)
[]![A sample ID token with blurred sensitive information.](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zidentity-id-token-sample.png)
[]![Enabling JIT provisioning in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zidentity-jit-oin-okta.png)
[]![Assigning the ZIdentity app in Okta to people with the appropriate option highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zslogin-assign-to-people-oin.jpg)
[]
![Configuring SCIM provisioning in ZIdentity with the ScIM endpoint URL highlighted](/downloads/zslogin/authentication/external-idp-configuration/configuring-okta-external-idp/zidentity-scim-endpoint-url-oin-okta.png)
[]
![Configuring provisioning in Okta with the option to configure API integration highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zslogin-api-integration-oin.png)
[]
![Enabling API integration for the ZIdentity app in Okta](/downloads/zslogin/administration/authentication/oidc-configuration-guides/oidc-configuration-guide-okta-oin-app/zslogin-api-integration-save-new.png)
[]
![Configuring provisioning in Okta with the option to edit provisioning to app highlighted](/downloads/zslogin/administration/authentication/oidc-configuration-guides/oidc-configuration-guide-okta-oin-app/zslogin-save-as-click-edit.png)
[]
![Configuring provisioning in Okta for ZIdentity](/downloads/zslogin/administration/authentication/oidc-configuration-guides/oidc-configuration-guide-okta-oin-app/zslogin-save-enable-provision.png)
[]
![Configuring assignments in Okta with the option to assign to people highlighted](/downloads/zslogin/administration/authentication/oidc-configuration-guides/oidc-configuration-guide-okta-oin-app/zslogin-assign-to-people-oin.png)
[]
![List of people with the option to assign them to ZIdentity highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zslogin-assign-users-new.png)
[]
![Configuring assigments in Okta with the option to assign the app to groups highlighted](/downloads/zslogin/administration/authentication/oidc-configuration-guides/oidc-configuration-guide-okta-oin-app/zslogin-assign-to-groups-oin.png)
[]
![Assigning ZIdentity app to groups with the option to assign highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zslogin-group-assign.png)
[]
![Pushing groups with the option to push groups by name highlighted](/downloads/zslogin/administration/authentication/oidc-configuration-guides/oidc-configuration-guide-okta-oin-app/zslogin-by-name-oin.jpg)
[]
![Pushing groups options with the option to find groups by rule highlighted](/downloads/zslogin/administration/authentication/oidc-configuration-guides/oidc-configuration-guide-okta-oin-app/zslogin-by-rule-menu.jpg)
[]
![Pushing groups by name rule](/downloads/zslogin/administration/authentication/oidc-configuration-guides/oidc-configuration-guide-okta-oin-app/okta-zslogin-group-byname-select.jpg)
[]
![List of groups pushed from Okta with the Push status highlighted](/downloads/zslogin/administration/authentication/oidc-configuration-guides/oidc-configuration-guide-okta-oin-app/zslogin-group-active.jpg)
[]
![List of groups pushed from Okta with the Push status highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zslogin-active-groups-okta-rule-oin_0.jpg)
[]
![Creating a rule for group push](/downloads/zslogin/administration/authentication/oidc-configuration-guides/oidc-configuration-guide-okta-oin-app/zslogin-rule-new-oin.jpg)
[]
This section provides information on how to configure Okta as your OpenID Provider (OP) for ZIdentity to facilitate single sign-on (SSO) to various Zscaler services for admin access management.
Prerequisites
Ensure that you have:
- An Okta account with admin privileges
- An existing user directory in Okta
- A ZIdentity account with an admin role that allows you to add an IdP configuration
Configuring Okta as OP for ZIdentity
To set up Okta as an OP for ZIdentity:
- [1. Configure app integration for ZIdentity in Okta.](#app-integrate-okta)
- [2. Set up Okta as an OP for ZIdentity.](#setup-okta-as-op)
- [3. Provision users for ZIdentity.](#provision-users-okta)
- [4. (Optional) Enable step-up authentication.](#enabling-step-up-authentication-custom-app)
- []Log in to the [Okta Admin Console](https://support.okta.com/help/s/article/How-to-access-Okta-admin-console-when-Default-App-for-Sign-In-Widget-is-enabled?language=en_US).
- Go to **Applications **> **Applications**.
-
Click **Create App Integration**.
[See image.](#okta-app-integrate)
-
In the **Create a new app integration** window:
- **Sign-in method**: Select the **OIDC - OpenID Connect **option.
- **Application type**: Select the **Web Application **option.
- Click **Next**.
[See image.](#app-wizard-okta)
The **New Web App Integration** window appears.
- In the **New Web App Integration** window:
-
In the **General Settings **section:
- **App integration name**: Enter a name for the ZIdentity integration.
- Ensure that **Grant type** is set to **Authorization Code**.
[See image.](#new-app-window-okta)
-
In the **Assignments **section:
- **Controlled Access**: Select an appropriate option.
- Disable the **Enable immediate access with Federation Broker Mode **option.
[See image.](#assigments-app-okta)
-
[]Click **Save.**
-
[]In the application page, under the **General **tab, copy the **Client ID** and **Client Secret **values.
[See image.](#secrets-okta)
- []Log in to the ZIdentity Admin Portal.
- Go to **Integration **> **External Identities**.
- Click **Add Primary IdP** (or **Add Secondary IdP**).
The **Add Primary Identity Provider** or **Add Secondary Identity Provider** window appears.
- On the **Basic **tab:
-
In the **General **section:
- **Name**: Enter a name for the IdP.
- **Identity Vendor**: Select **Okta** from the drop-down menu.
- **Domain**: Select the domain for which the IdP is responsible for authenticating the users. This allows the Zscaler service to display the correct IdP to authenticate an incoming user.
- **Protocol**: Select **OIDC**.
- **Status**: Select **Enabled**.
- **Login ID Attribute**: Enter an attribute whose value must be used as the login ID. This attribute must exist in the tokens received from the IdP. By default, the `preferred_username` attribute is populated in this field when the **OIDC** option is selected in the **Protocol** field. You can use any attribute that is present in the [ID token](https://openid.net/specs/openid-connect-core-1_0.html#IDToken) or the response of the [UserInfo endpoint](https://openid.net/specs/openid-connect-core-1_0.html#UserInfo), provided its value is in the email address format (e.g., <user_name>@domain.com>).
- Ensure that the domain part of the email addresses received in the ID tokens match with one of the domains configured in ZIdentity.
- Ensure that the attribute you enter matches exactly with the attribute received in the ID token or the UserInfo endpoint.
[See image.](#basic-setup-okta)
-
In the **OIDC Configuration **section:
-
Enter the following value for the **Metadata URL **field:
`https://`<your_subdomain>`.okta.com/oauth2/default/.well-known/openid-configuration`
- Click **Fetch**.
- []Copy the **Redirect URI** value.
- Paste the **Client ID **and **Client Secret **values copied from the Okta Admin Console to the respective fields.
- Add required scopes. By default, when the OIDC protocol is selected, the `openid`, `email`, and `profile` scopes are added.
[See image.](#oidc-setup-okta)
- Click **Save**.
- Go to the Okta Admin Console, and go to the application integration created for ZIdentity.
- On the **General **tab:
-
In **General Settings **section, click **Edit**.
[See image.](#edit-settings-okta)
-
In the **Login **section, paste the **Redirect URI **value copied from the ZIdentity Admin Portal in a previous step to the** Sign-in redirect URIs** field.
[See image.](#redirect-uri-okta)
- Click **Save**.
[]
This section explains how to provision Okta users in ZIdentity Admin Portal using Just-in-Time (JIT) provisioning. Okta does not support SCIM provisioning for custom OIDC applications. For configuring SCIM-based provisioning using Okta, Zscaler recommends using a SAML app integration.
- [a. (Optional) Configure Okta to retrieve group membership information](#configure-group-scope-claim-okta)
- [b. Configure JIT provisioning in ZIdentity Admin Portal](#provision-users-zslogin-portal)
- []In the Okta Admin Console, go to **Security **> **API**.
-
Click the **Edit **icon for the authorization server.
[See image.](#api-edit-okta)
- Under the **Scopes **tab:
-
Click **Add Scope**.
[See image.](#add-scope-button-okta)
-
Enter a name for the scope. For example, enter `Groups-Scope`.
[See image.](#add-scope-okta)
-
Click **Create**.
The custom scope is added to the authorization server.
- Under the **Claims **tab:
-
Click **Add Claim**.
[See image.](#add-claim-button-okta)
- Enter a name for the claim. For example, enter `Groups`.
- **Include in the Token Type**: Select **ID Token** and select **Always **from the respective drop-down menus.
- **Value type**: Select **Groups **from the drop-down menu.
- **Filter**: Select **Match regex **from the drop-down menu and enter `.*` to return all of the user's groups.
-
**Include in**: Select **The following scopes** and add the scope created in step iii (i.e., `Groups-Scope`).
[See image.](#add-claim-okta)
-
Click **Create**.
The custom claim is added to the authorization server.
- []In the ZIdentity Admin Portal, go to **Integration **> **External Identities**.
- Locate the IdP entry created for Okta under the **Primary Identity Provider** (or **Secondary Identity Providers**) tab and click the **Edit **icon.
-
In the **Edit Primary IdP** (or **Edit Secondary IdP**) window:
- On the **Provisioning **tab, select **Enable Just-in-time (JIT) Provisioning**.
- **Just-in-time User Group Attribute**: Enter the claim name created for group information retrieval (i.e., `Groups`). This retrieves the group membership information of the users from Okta.
-
Map ZIdentity user attributes with the appropriate Okta attributes as necessary. The mapping of the `Primary Email` attribute is mandatory as it is required for functionalities, such as password resetting and multi-factor authentication. By default, the following attributes in ID tokens are mapped with the corresponding user attributes in ZIdentity.
| Attribute in ID Tokens | Default ZIdentity User Attributes |
| ---------------------- | --------------------------------- |
| given_name | First Name |
| family_name | Last Name |
| name | Display Name |
- If the external IdP is configured to send different attributes for First Name, Last Name, or Display Name, then you must map those attributes. For example, if the ID token from the external IdP includes `Surname` instead of `family_name`, then you must map it with the `Last Name` user attribute in ZIdentity. [See image](#oidc-id-token-sample-2)
- While mapping attributes, ensure that the attributes you enter in the **Just-in-time Attribute** field match exactly with the attributes that would be received in the ID tokens.
[See image.](#jit-zslogin-okta-oidc)
-
Click **Update**.
The JIT provisioning with Okta users is configured for ZIdentity.
[]You can configure step-up authentication to extend the existing authentication process by requiring multi-factor authentication (MFA) when needed, ensuring that access to high-risk or sensitive data is protected.
Prerequisites
Before configuring [step-up authentication](/zidentity/understanding-step-authentication), ensure that:
- Zscaler Client Connector version 4.7 or later is deployed for the users in your organization.
- ZIdentity is enabled for both admins and users.
- Step-up authentication is enabled for ZIdentity, Zscaler Internet Access (ZIA), and Zscaler Private Access (ZPA) tenants.
To enable step-up authentication:
- [1. Configure authentication levels in the ZIdentity Admin Portal.](/zidentity/configuring-authentication-levels)
- [2. Enable ACR values and configure the necessary policies in the external IdPs.](#external-idp-configuration-custom-app)
- [3. Map authentication levels and ACR values in the ZIdentity Admin Portal.](#al-acr-mapping-custom-app)
- [4. Configure access policies in supported Zscaler services.](#access-policies-mapping-custom-app)
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
[See image.](#al-acr-mapping-zidentity-custom-app)
- Click **Update**.
[]You can configure the necessary policies in the following Zscaler services as required:
- ZPA: [Configuring Access Policies](/zpa/configuring-access-policies) for the target application or app segment with the **Conditional Access **as the **Rule Action**. Ensure that the necessary authentication level is selected using the **Step-up Authentication Level** field.
- ZIA: [Configuring the URL Filtering Policy](/zia/configuring-url-filtering-policy) and [Cloud App Control Policies](/zia/adding-rules-cloud-app-control-policy) with the **Conditional Access **as the **Action**. Ensure that the necessary authentication level is selected using the **Authentication Level **field.
[]![Mapping authentication levels with ACR values in ZIdentity](/downloads/zidentity/authentication/configuring-step-authentication/zidentity-al-acr-mapping.png)
[]
![Application page in Okta with the option to create an app integration highlighted](/downloads/zslogin/administration/authentication/Third-Party%20OIDC/okta-create-app-integration.png)
[]
![Configuring new app integration in Okta](/downloads/zslogin/administration/authentication/Third-Party%20OIDC/app-window-okta.png)
[]
![Creating a new web app integration in Okta with the app name highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zidentity-web-app-okta.png)
[]
![Configuring assignment options for an app in Okta](/downloads/zslogin/administration/authentication/Third-Party%20OIDC/okta-assignment.png)
[]
![Configuring general settings in Okta with the Client ID field highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/okta-secrets.png)
[]
![Adding basic information for an IdP in ZIdentity](/downloads/zslogin/authentication/external-idp-configuration/configuring-okta-external-idp/zidentity-okta-oidc-oin-basic-idp_0%20(1).png)
[]
![OIDC Configuration options with some fields highlighted](/downloads/zslogin/authentication/external-idp-configuration/configuring-okta-external-idp/zidentity-okta-oic-basic-oidc-configuration-another.png)
[]
![configuring general settings for ZIdentity app in Okta with the option to edit the setttings highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zidentity-app-registration.jpg)
[]
![List of login settings with the redirect URI highlighted](/downloads/zslogin/administration/authentication/Third-Party%20OIDC/okta-metadata-url.png)
[]
![List of authorization servers with the option to edit a server highlighted](/downloads/zslogin/administration/authentication/Third-Party%20OIDC/zslogin-okta-api.jpg)
[]
![List of scopes with the option to add a scope highlighted](/downloads/zslogin/administration/authentication/Third-Party%20OIDC/zslogin-add-scope-okta-oidc.jpg)
[]
![Adding scope in Okta](/downloads/zslogin/administration/authentication/Third-Party%20OIDC/zslogin-group-scope-okta-oidc.jpg)
[]
![List of claims with the option to add a claim highlighted](/downloads/zslogin/administration/authentication/Third-Party%20OIDC/zslogin-claim-add-okta-oidc.jpg)
[]
![Adding a claim in Okta](/downloads/zslogin/administration/authentication/Third-Party%20OIDC/zslogin-add-claim-okta-oidc-new.jpg)
[]![A sample ID token with blurred sensitive information.](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zidentity-id-token-sample.png)
[]
![Mapping JIT attributes in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zidentity-jit-customapp.png)
[]
This section provides information on how to configure Okta as the SAML Identity Provider (IdP) for ZIdentity to facilitate single sign-on (SSO) to various Zscaler services for admin access management.
Prerequisites
- A subscription to Okta
- An existing user directory in Okta
- A ZIdentity account with an admin role that allows you to add an IdP configuration
Configuring Okta as IdP for ZIdentity
To set up Okta as an idP for ZIdentity:
- [1. Set up Okta as an IdP for ZIdentity.](#set-up-idp-okta)
- [2. Configure app integration for ZIdentity in Okta.](#okta-app-integration)
- [3. Provision users for ZIdentity using JIT or SCIM provisioning.](#provision-users-okta-sam-jit)
[]
During the IdP-initiated SSO for ZIdentity, tenants using OIDC or SAML protocols are redirected as follows:
- [OIDC Protocol](#OIDC-protocol-redirection)
- [SAML Protocol](#SAML-protocol-redirection)
To change the default redirection, contact [Zscaler Support](/contact-support).
[]
All admins authenticating using the SAML protocol for ZIdentity and IdP integrations are redirected to Experience Center. However, if the `zidServiceId` attribute is configured in the IdP within the ZIdentity tenant, then the admins are redirected to the ZIdentity Admin Portal instead of Experience Center.
Configuring Attribute in Okta
To configure the `zidServiceId` attribute in Okta for SAML protocol:
- Log in to the [Okta Admin Console](https://support.okta.com/help/s/article/How-to-access-Okta-admin-console-when-Default-App-for-Sign-In-Widget-is-enabled?language=en_US).
- Go to **Applications **> **Applications**.
- Locate the application created for ZIdentity and open it.
-
Go to the **General **tab, locate **SAML Settings**, and click **Edit**.
[See image.](#redirection-saml-settings)
- In the **Edit SAML Integration** wizard, click **Next **in the **General Settings **tab.
- In the **Configure SAML **tab, locate the **Attribute Statements (optional)** section.
- In the **Name **field, enter `zidServiceId`.
-
In the **Value **field, enter `800000000103`. This value is the same for all tenants.
[See image.](#redirection-attribute-steps-saml)
- Click **Next**.
- On the **Feedback **tab, click **Finish**.
[]
ZIdentity tenants that are enabled with Experience Center at the time of tenant creation and admins using OIDC protocol for ZIdentity and IdP integrations are redirected to the Experience Center.
ZIdentity tenants that are not enabled with Experience Center at the time of tenant creation and admins using OIDC protocol for ZIdentity and IdP integrations are redirected to the ZIdentity Admin Portal. They can click the Experience Center link and go to the Experience Center from the [ZIdentity Landing page](/zidentity/accessing-and-navigating-zidentity-landing-page).
If you want to change this default behavior and have users redirected to the Experience Center, raise a Support ticket with the ticket type set to **Provisioning**.
[See image.](#Zidentity_Landing_Page)
- []Log in to the ZIdentity Admin Portal.
- Go to **Integration **> **External Identities**.
-
Click **Add Primary IdP **(or **Add Secondary IdP**).
The **Add Primary Identity Provider **(or **Add Secondary Identity Provider) **window appears.
-
On the **Basic **tab:
- Under the **General **section:
- **Name**: Enter a name for the IdP.
- **Identity Vendor**: Select **Okta **from the drop-down menu.
- **Domain**: Select the domain for which the IdP is responsible for authenticating the users. This allows the Zscaler service to display the correct IdP to authenticate an incoming user.
- **Protocol**: Select **SAML**.
- **Status**: Select **Enabled**.
-
**Login ID Attribute**: Enter an attribute whose value must be used as the login ID. This attribute must exist in the token received from the IdP. By default, the `NameID` attribute is populated in this field when the **SAML** option is selected in the **Protocol** field. You can use any attribute that is present in the SAML assertion, provided its value is in the email address format (e.g., <user_name>@domain.com>).
- Ensure that the domain part of the email addresses received in the SAML assertion matches with one of the domains configured in ZIdentity.
- Ensure that the attribute you enter matches exactly with the attribute received in the SAML assertion.
- Under the **SAML Configuration **section, copy the **SP Entity ID**.
[See image.](#sp-entity-id)
Do not close the window as the **SP Entity ID** is going to be refreshed.
- []Log in to the [Okta Admin Console](https://support.okta.com/help/s/article/How-to-access-Okta-admin-console-when-Default-App-for-Sign-In-Widget-is-enabled?language=en_US).
- Go to **Applications **> **Applications**.
-
Click **Create App Integration**.
[See image.](#create-app-okta)
-
In the **Create a new app integration** window:
- **Sign-in method**: Select the **SAML 2.0 **option.
- Click **Next**.
[See image.](#create-app-saml-okta)
The **Create SAML Integration** window appears.
- In the **Create SAML Integration** window:
-
Under the **General Settings **section:
- **App name**: Enter a name for the ZIdentity integration.
- Click **Next**.
[See image.](#general-settings-okta)
-
Under the **Configure SAML **section:
- Enter the **SP Entity ID** value copied from ZIdentity Admin Portal in the previous step for both **Single sign-on URL **and **Audience URI (SP Entity ID) **fields.
- **Attribute Statements**: Enter a SAML attribute and an appropriate filter. This is used to pass any user attributes. For example, enter `Email` for the **Name **field and enter the appropriate variable name (e.g., `user.email`) from the Okta profile.
- **Group Attribute Statements**: Enter a group name and an appropriate filter. This is used to pass group information. For example, enter `Groups` for the **Name **field and set **Filter **to **Matches regex** for `.*` to retrieve group membership information of users.
- Click **Next**.
[See image.](#configure-saml-okta)
-
Under the **Feedback **section:
- Select the **This is an internal app that we have created **option.
- Click **Finish**.
[See image.](#feedback-saml-okta)
The SAML application page appears.
-
On the SAML application page, copy the **Metadata URL **from the **Metadata details **section.
[See image.](#sign-on-okta-tab)
- Go to the ZIdentity Admin Portal where the **Add Primary Identity Provider **(or **Add Secondary Identity Provider) **window that is already open.
-
Under the **SAML Configuration **section:
- Enter the **Metadata URL** copied from the Okta Admin Console in the previous step for the **IdP Metadata URL** field.
- Click **Fetch**.
- Click **Save**.
[See image.](#saml-fetch-okta)
The SAML integration between Okta and ZIdentity is completed.
[]You can provision Okta users for ZIdentity using Just-in-time (JIT) provisioning or System for Cross-domain Identity Management (SCIM) provisioning.
- [JIT provisioning](#jit-provisioning-okta-saml)
- [SCIM provisioning](#scim-provisioning-okta-saml)
[]Users created in ZIdentity via SCIM cannot be updated via JIT provisioning. These records must be updated via SCIM provisioning only.
- In the ZIdentity Admin Portal, go to **Integration **> **External Identities**.
- Locate the IdP entry created for Okta under the **Primary Identity Provider** (or **Secondary Identity Providers**) tab and click the **Edit **icon.
-
In the **Edit Primary IdP **(or **Edit Secondary IdP**) window:
- Go to the **Provisioning **tab.
- Select** Enable Just-in-time (JIT) Provisioning**.
-
Map the ZIdentity user and group attributes with the appropriate Okta attributes as necessary. The mapping of the `Primary Email` attribute is mandatory as it is required for functionalities, such as password resetting and multi-factor authentication. By default, the following attributes in SAML assertions are mapped with the corresponding user attributes in ZIdentity.
| Attribute in SAML Assertions | Default ZIdentity User Attributes |
| ---------------------------- | --------------------------------- |
| firstName | First Name |
| lastName | Last Name |
| displayName | Display Name |
- If the external IdP is configured to send different attributes for First Name, Last Name, or Display Name, then you must map those attributes. For example, if the SAML assertion from the external IdP includes `Surname` instead of `lastName`, then you must map it with the `Last Name` user attribute in ZIdentity.
-
While mapping attributes, ensure that the attributes you enter in the **Just-in-time Attribute** field match exactly with the attributes that would be received in the SAML assertions.
[See image.](#saml-assertion-sample)
- Click **Update**.
[See image.](#jit-saml-okta)
- In the Okta Admin Console, go to **Applications **> **Applications**.
- Open the SAML application created for ZIdentity and go to the **Assignments **tab.
-
Add users and groups to the application using the **Assign **drop-down menu.
[See image.](#assignments-tab-one)
The JIT provisioning with Okta users is configured for ZIdentity.
- []In the ZIdentity Admin Portal, go to **Integration **> **External Identities**.
- Locate the IdP entry created for Okta under the **Primary Identity Provider** (or **Secondary Identity Providers**) tab and click the **Edit **icon.
-
In the **Edit Primary IdP **(or **Edit Secondary IdP**) window:
- Go to the **Provisioning **tab.
- Select **Enable SCIM Provisioning**.
-
Copy the **SCIM Endpoint URL**. This value is used in a subsequent step.
The **SCIM Endpoint URL** field appears only if the configurations for the IdP in the **Basic** tab are completed and saved.
[See image.](#scim-url-another)
- Click **Generate Token **and copy the **Bearer Token**.
- (Optional) Map the SCIM attributes (e.g., `addresses`) with the corresponding ZIdentity user attribute. This mapping is required only for attributes that need to be mapped to a custom [user attribute](/zidentity/adding-user-attributes) in ZIdentity.
[See image.](#bearer-scim)
- In the Okta Admin Console, go to **Applications **> **Applications**.
- Open the SAML application created for ZIdentity and do the following:
-
On the **General **tab:
- Click **Edit **next to **App Settings**.
- Select **Enable SCIM provisioning**.
- Click **Save**.
[See image.](#enable-scim-in-okta)
- On the **Provisioning **tab:
- Click **Edit **for **SCIM Connection**.
- **SCIM Connector Base URL**: Enter the **SCIM Endpoint URL **copied from the ZIdentity Admin Portal.
- **Unique identifier field for users**: Enter `userName` as the value.
- **Supported provisioning actions**: Select the **Push New Users **and **Push Groups **options.
- **Authentication mode**: Select **HTTP Header **from the drop-down menu.
-
**Authorization**: Enter the bearer token copied from the ZIdentity Admin Portal.
[See image.](#okta-saml-provisioning)
-
Click **Test Connector Configuration** and make sure that **Create users** and **Push Groups **options are shown with green checkmarks.
[See image.](#test-connection-okta)
- Close the **Test Connector Configuration** window.
-
Click **Save **and ensure that the **Create users **option is enabled under the **Provisioning **tab.
[See image.](#create-user-okta)
- On the **Assignments **tab, click the **Assign **drop-down menu, and select an option to assign users or groups:
- [Assign users](#assign-groups-to-users)
- [Assign groups](#assigme-groups-to-app)
-
To sync users between an Okta group and a ZIdentity group, go to the **Push Groups **tab, and select an option to push groups by name or rule:
- [Push groups by name](#group-by-name-steps)
- [Push groups by rule](#group-by-rule-steps)
To learn more about group push, refer to the [Okta technical documentation](https://help.okta.com/en-us/content/topics/users-groups-profiles/usgp-about-group-push.htm).
The SCIM provisioning with Okta users is configured for ZIdentity.
[]
-
Select **Assign to People**.
[See image.](#assign-to-people-two)
-
Search and locate users you want to assign, and click **Assign**.
[See image.](#asssign-user-button)
- Click **Done**.
[]
-
Select **Assign to Groups**.
[See image.](#assign-to-groups-option)
-
Search and locate the groups you want to assign, and click **Assign**.
[See image.](#assign-group-button)
- Click **Done**.
[]
-
Select the **Find groups by name **option from the **Push Groups **drop-down menu.
[See image.](#push-by-name-option)
By default, the **Push group memberships immediately **option is selected to push groups immediately to ZIdentity. However, you can disable it if you do not want to push groups immediately.
-
Enter the name of the group that you want to push and select the group from the drop-down menu.
[See image.](#push-by-name-window)
- Click **Save **or click **Save & Add Another** if you want to push multiple groups.
- Click **Close**.
-
On the **Push Groups **tab, click **By name** on the left-side navigation and verify that all of your groups have been added.
[See image.](#active-name-group-okta)
[]
-
Select the **Find groups by rule** option from the **Push Groups **drop-down menu.
[See image.](#push-by-rule-option)
- In the **Push groups by rule **window:
- **Rule name**: Enter a name for the rule.
- **Group name**: Select a match condition from the drop-down menu and enter a string that should be used to find a group with the name matching the condition. For example, you can select **Contains** as the match condition and enter `Admins` as the string to match all groups that has the string "Admin" and push them to ZIdentity.
-
**Group description**: Select a match condition from the drop-down menu and enter a string that should be used to find a group with the description matching the condition. For example, you can select **Contains** as the match condition and enter `For Admins` as the string to match all groups that has the string "For Admins" in the description and push them to ZIdentity.
By default, the **Immediately push groups found by this rule **option is selected to push groups immediately to ZIdentity. However, you can disable it if you do not want to push groups immediately.
[See image.](#push-by-rule-window)
- Click **Create Rule**.
-
On the **Push Groups **tab, select the rule name created in the previous step under the **By rule **option** **on the left-side navigation, and verify that all of your groups have been added.
[See image.](#active-rule-group-okta)
[]
![Configuring basic information for an IdP](/downloads/zslogin/authentication/external-idp-configuration/configuring-okta-external-idp/zidentity-saml-okta-basic.png)
[]
![List of applications with the option to create an app integration highlighted](/downloads/zslogin/administration/authentication/third-party%20saml/zslogin-create-app-integration-okta.png)
[]
![Creating a new app integration in Okta](/downloads/zslogin/administration/authentication/third-party%20saml/zslogin-saml-app-option.png)
[]
![Configuring general settings for a SAML integration in Okta](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zslogin-general-settings.png)
[]
![Configuring SAML integration for Okta](/downloads/zslogin/administration/authentication/third-party%20saml/zslogin-config-saml-new-one.jpg)
[]
![Creating a SAML integration for ZIdentity in Okta](/downloads/zslogin/administration/authentication/third-party%20saml/zslogin-saml-feedback.png)
[]
![Configuring SSO in Okta for ZIdentity with the metadata URL highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zslogin-copy-metadata.png)
[]
![Assigning Zscaler app to people in Okta with appropriate option highlighted](/downloads/zslogin/administration/authentication/third-party%20saml/zslogin-assign-to-people.jpg)
[]
![Assigning Zscaler app to people in Okta with the appropriate option highlighted](/downloads/zslogin/administration/authentication/third-party%20saml/zslogin-assign-to-people.jpg)
[]![A SAML assertion sample with blurred sensitive information](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zidentity-saml-assertion-sample.png)
[]
![Mapping JIT attributes in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zidentity-jit-customapp_0.png)
[]
![Configuring SAML settings in ZIdentity](/downloads/zslogin/authentication/external-idp-configuration/configuring-okta-external-idp/zidenity-saml-configuration.png)
[]
![Configuring SCIM provisioning in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zidentity-saml-scim-okta.png)
[]
![Enabling SCIM provisioning in ZIdentity with the SCIM endpoint URL highlighted](/downloads/zslogin/authentication/external-idp-configuration/configuring-okta-external-idp/zidentity-saml-okta-scim-url.png)
[]
![Enabling SCIM provisioning for ZIdentity app in Okta](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zidentity-enable-scim-in-okta.jpg)
[]
![Configuring SCIM connection to provision users](/downloads/zslogin/administration/authentication/third-party%20saml/zslogin-provisioning-tab-new.png)
[]
![Testing connector configuration in Okta with some options highlighted](/downloads/zslogin/administration/authentication/third-party%20saml/zslogin-test-connection.png)
[]
![Enabling provisioning for ZIdentity from Okta](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zidentity-provisoning-highlight.jpg)
[]
![Assigning ZIdentity app to groups in Okta](/downloads/zslogin/administration/authentication/third-party%20saml/zslogin-assign-to-groups.jpg)
[]
![Assigning people to ZIdentity app in Okta](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zslogin-assign-user%20(1).jpg)
[]
![Assigning the ZIdentity app integration to groups](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zslogin-assign-groups%20(1).jpg)
[]
![Configuring group push with the option to find groups by name highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zslogin-group-push-by-name-menu_0%20(1).jpg)
[]
![Configuring group push with the option to find groups by rule highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zslogin-group-push-by-rule-menu_0%20(2).jpg)
[]
![Finding a group in Okta](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zslogin-push-groups_0%20(1)_0.jpg)
[]
![Creating a rule to push groups in Okta](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zslogin-push-groups-rule%20(1).jpg)
[]
![Configuring group push in Okta with the push status highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zslogin-active-grousp-okta-name%20(1).jpg)
[]
![Configuring group push in Okta with the push status highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-okta-external-idp/zslogin-active-groups-okta-rule%20(1).jpg)
[]![SAML Settings with the Edit option highlighted](/downloads/tech-pubs-drafts/zslogin-draft-articles/configuring-microsoft-entra-id-external-idp-draft-doc-56276/zidentity-okta-edit-saml-seetings.png)
[]![Configuring an atttribute in Okta](/downloads/tech-pubs-drafts/zslogin-draft-articles/configuring-microsoft-entra-id-external-idp-draft-doc-56276/zidentity-okta-attribute-statements.png)
[]
![ZIdentity Landing page with highlighted banner at the top.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-configuring-okta-external-idp-doc-57200/zid-landing-page-1.png)