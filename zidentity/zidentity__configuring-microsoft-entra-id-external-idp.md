# Configuring Microsoft Entra ID as an External IdP
Source: https://help.zscaler.com/zidentity/configuring-microsoft-entra-id-external-idp
PDF: https://help.zscaler.com/pdf/com/en/1499421.pdf

This guide provides information on how to configure Microsoft Entra ID as an external identity provider (IdP) for ZIdentity to facilitate single sign-on (SSO) to various Zscaler services for admin access management. You can configure Entra ID as an external IdP to enable SSO to ZIdentity using OpenID Connect (OIDC) or Security Assertion Markup Language (SAML) authentication protocols.
Zscaler and Microsoft are technology partners. To learn more about integrating Zscaler and Microsoft Entra ID, see the [Zscaler and Microsoft Entra ID Passwordless Deployment Guide](/zscaler-technology-partners/zscaler-and-microsoft-entra-ID-passwordless-deployment-guide).
Depending on the authentication protocol, you can provision users to ZIdentity from Entra ID using Just-in-Time (JIT) provisoning or System for Cross-domain Identity Management (SCIM) provisioning.
If you want to leverage [step-up authentication](/zidentity/understanding-step-up-authentication), it is recommended to use OIDC-based integrations as most IdPs only support step-up authentication with the OIDC protocol.
- [OIDC-Based Authentication via Microsoft Entra Gallery App Integration](#oidc-entra-id)
- [SAML-Based Authentication](#saml-entra-id)
- [IdP-Initiated SSO for ZIdentity Tenants Enabled with Experience Center](#idp-initiated-sso-flow)
[]
During the IdP-initiated SSO for ZIdentity, tenants using OIDC or SAML protocols are redirected as follows:
- [OIDC Protocol](#OIDC-protocol-redirection)
- [SAML Protocol](#SAML-protocol-redirection)
To change the default redirection, contact [Zscaler Support](/contact-support).
[]
All admins authenticating using the SAML protocol for ZIdentity and IdP integrations are redirected to Experience Center. However, if the `zidServiceId` attribute is configured in the IdP within the ZIdentity tenant, then the admins are redirected to the ZIdentity Admin Portal instead of Experience Center.
To configure IdP-initiated SSO, the **Require verification certificates** option must be disabled while configuring the Verification Certifications for the ZIdentity application in Entra ID. If the **Require verification certificates** option is enabled, the SAML Request Signature Verification works only for SP-initiated authentication requests. The IdP-initiated authentication requests are not validated as the IdP would not possess the same private keys as the registered application. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/howto-enforce-signed-saml-authentication).
Configuring Attribute in Entra ID
To configure the `zidServiceId` attribute in Entra ID for SAML protocol:
- Log in to the [Entra Admin Center](https://entra.microsoft.com/).
- Go to **Identity **> **Applications **> **Enterprise applications**.
- Locate the application created for ZIdentity and open it.
- Go to **Manage **> **Single sign-on**.
-
Locate the **Attributes & Claims** section, and click **Edit**.
[See image.](#redirection-edit-claim)
-
On the **Attributes & Claims** page, click **Add new claim**.
[See image.](#redirection-add-claim)
- On the **Manage Claim** page:
- Enter `zidServiceId` as the attribute name.
- Under **Claim conditions**, configure administrator groups for which you want to send the claim:
- Select **Members **from the User type drop-down menu.
- Click **Select groups** under the **Scoped Groups **column, and select the administrator groups for which you want to send the claim.
- Select **Attribute **from the **Source **drop-down menu.
-
Enter `800000000103` as the **Value**. This value is the same for all tenants.
[See image.](#redirection-manage-claim)
- Click **Save**.
[]
ZIdentity tenants that are enabled with Experience Center at the time of tenant creation and admins using OIDC protocol for ZIdentity and IdP integrations are redirected to the Experience Center.
ZIdentity tenants that are not enabled with Experience Center at the time of tenant creation and admins using OIDC protocol for ZIdentity and IdP integrations are redirected to the ZIdentity Admin Portal. They can click the Experience Center link and go to the Experience Center from the [ZIdentity Landing page](/zidentity/accessing-and-navigating-zidentity-landing-page).
[See image.](#Zidentity_Landing_Page)
If you want to change this default behavior and have users redirected to the Experience Center, raise a Support ticket with the ticket type set to **Provisioning**.
[]This section explains how to configure Microsoft Entra ID as the OpenID Provider (OP) for the ZIdentity via prebuilt app integration to facilitate SSO to various Zscaler services for admin access management.
Prerequisites
Ensure that you have:
- A subscription to Entra ID.
- An existing user directory in Entra ID.
- A ZIdentity account with an admin role that allows you to add an IdP configuration.
-
A preferred choice of provisioning mode (JIT or SCIM) as this determines the number of apps you need to configure in Entra ID — one app for JIT and two apps for SCIM.
[Implementation Differences Between JIT and SCIM Provisioning Modes](#differences-jit-scim)
Configuring Microsoft Entra ID as OP for ZIdentity
To set up Microsoft Entra ID as an OP for ZIdentity:
- [1. Configure app integration using the Zscaler app in the Entra ID gallery.](#set-up-integration-pre-built-app)
- [2. Set up Entra ID as an OP for ZIdentity.](#setup-entra-id-as-op)
- [3. Provision users for ZIdentity.](#provisioning-users)
- [4. (Optional) Enabling step-up authentication.](#enabling-step-up-authentication)
[]Setting Up IdP-Initiated SSO
You can log in to the ZIdentity Admin Portal via the IdP-initiated flow.
To log in to ZIdentity Admin Portal from the Entra ID's My Apps portal:
- Log in to the Entra ID's [My Apps portal](https://myapps.microsoft.com/).
-
Locate and click the Zscaler app.
[See image.](#my-apps-page)
The ZIdentity Admin Portal URL is opened in a new tab or window and you are logged in.
[See image.](#landing-page)
[]Entra ID only supports JIT provisioning for OIDC apps via the Microsoft Entra App Gallery. If you prefer SCIM provisioning with OIDC, you need to create a custom Entra ID app for SCIM, in addition to using the Gallery App for authentication. The following table summarizes the implementation differences for JIT and SCIM:
| Provisioning Mode | Authentication via Gallery App | Provisioning Support | Additional Requirements |
| ----------------- | ------------------------------ | -------------------- | ----------------------- |
| JIT Provisioning | Yes | Supported by default | None |
| SCIM Provisioning | Yes | Not supported in the Gallery Application | Create a custom Entra ID app for SCIM provisioning in addition to using the Gallery App for authentication. |
- []Log in to the [Entra Admin Center](https://entra.microsoft.com/).
- In the left-side navigation, go to **Identity **> **Applications **> **Enterprise applications**.
-
Click **New application**.
[See image.](#new-app-button-entra-app)
The **Microsoft Entra Gallery **window appears.
- In the **Microsoft Entra Gallery** window, search for `zscaler`.
-
Click the Zscaler tile on the search results.
[See image.](#entra-app-zscaler-tile)
The Zscaler app window appears.
-
In the Zscaler app window, customize the app name, if needed, and click **Create**.
[See image.](#entra-app-zscaler-window)
The Application Details page appears.
-
On the application details page, click **Single sign-on** and click **Go to application**.
[See image.](#entra-app-go-to-app)
The **App Registration** page for Zscaler app appears.
- On the **App Registration** page:
-
Copy the **Application (Client) ID **and save it for future use.
[See image.](#entra-app-copy-client-id)
-
Click **Endpoints**.
[See image.](#entra-app-endpoints)
The **Endpoints **window appears.
-
In the **Endpoints **window, locate the **OpenID Connect metadata document **field, and copy and save the URL for future use.
[See image.](#entra-app-oidc-url)
- In the left-side navigation, go to **Manage > Branding & properties**.
-
In the **Home page URL **field, enter the ZIdentity Admin Portal URL along with the `idp_id` URL parameter. This step is required for enabling the IdP-initiated SSO option for ZIdentity Admin Portal.
[]The value for the `idp_id` URL parameter is `default` if you are configuring Entra ID as your primary IdP in the ZIdentity Admin Portal. If you are configuring Entra ID as a secondary IdP, the value for `idp_id` must be sourced from the final segment of the **Redirect URI**.
-
Home page URL if Entra ID is configured as your primary IdP in the ZIdentity Admin Portal: `https://``<your_domain>``.zslogin.net/?idp_id=default`
[See image.](#idp-id-primary-example)
-
Home page URL if Entra ID is configured as your secondary IdP in the ZIdentity Admin Portal: `https://``<your_domain>``.zslogin.net/?idp_id=``<final_segment_from_redirect_URI>`
[See image.](#idp-id-secondary-example)
If you are configuring Entra ID as your secondary IdP, update this field with the appropriate `idp_id` value after setting up Entra ID as the IdP in the ZIdentity Admin Portal in the subsequent steps.
[See image.](#homepage-url-page)
-
Click **Save**.
The configuration is saved, and it takes a few hours for the changes to take effect.
-
In the left-side navigation, click **Certificates & secrets**.
The **Certificates & secrets **window appears.
- In the **Certificates & secrets** window:
-
Click **New client secret**.
[See image.](#entra-app-new-client-secret-button)
The **Add a client secret** window appears.
-
In the **Add a client secret** window, enter a description, and click **Add**.
[See image.](#entra-app-client-secret-window)
The client secret is added and is shown in the **Client secrets** table.
-
Copy the client secret value from the **Value **column and save it for future use.
[See image.](#entra-app-copy-value)
The client secret value cannot be accessed or viewed after you leave the page.
-
In the left-side navigation, click **API permissions**.
The **API permissions** window appears.
- In the **API permissions** window:
-
Click **Grant admin consent for <entra_ID_tenant_name>**.
[See image.](#entra-app-consent-grant-button)
To ensure only administrators can accept grants, this configuration is required as it prevents the end users from getting the prompt to accept the grant while logging in to the application.
-
Click **Yes **on the **Grant admin consent confirmation** window.
[See image.](#entra-app-grant-admin-confirm)
Make sure the **Status **column shows the green checkmark.
[See image.](#entra-app-grant-admin-success)
-
In the left-side navigation, click **Token configuration**.
The **Token configuration **window appears.
- In the **Token configuration **window:
-
Click **Add optional claim**.
[See image.](#add-optional-claim-button)
The **Add optional claim** window appears.
-
In the **Add optional claim** window:
-
Select **ID** as the token type, and from the list of claims, select `email` and `preferred_username`.
[See image.](#add-optional-claim-window)
- Click **Add**.
The selected claims are added.
[See image.](#optional-claims-added)
-
Click **Add groups claim**.
[See image.](#entra-app-add-group-claim)
The **Edit groups claim **window appears.
-
In the **Edit groups claim **window:
- Under the **Select group types** **to include** **in Access, ID, and SAML tokens **section, select the **Groups assigned to the application** option.
-
Under the **Customize token properties by type** section, click **ID **to expand the **ID **subsection, and select the **Group ID **option.
The Group ID must be selected as Entra ID does not support sending group names with OIDC protocol when groups are created in the Entra Cloud.
[See image.](#entra-app-edit-group-claims-window)
If the group names are received via the Entra ID sync, click the **sAMAccountName** option instead of the **Group ID** option to pass on the group names.
[See image.](#entra-app-editgrop-claim-another)
- Click **Add**.
The group claims are added.
[See image.](#added-groups-claim-entra)
-
In the left-side navigation, click **Manifest**.
The **Manifest **window appears.
-
In the **Manifest **window, update the required attributes in the graph manifest:
- [Updating Microsoft Graph App Manifest](#microsoft-graph-manifest)
These changes are required if you are adding any optional claims in a future step.
-
Click the **OIDC-based Sign-on** option on the top to go to the application page.
[See image.](#entra-app-oidc-breadcrumb)
-
In the left-side navigation, click **Users and groups**.
The **Users and groups **window appears.
-
In the **Users and groups **window, select the users and groups that you want to have access to the application.
[See image.](#entra-app-users-and-groups)
If you want to pass group memberships as claims, make sure that the groups are assigned instead of individual users in the **Users and groups** window.
-
In the left-side navigation, click **Single sign-on**.
The **Single sign-on** window appears.
-
In the **Single sign-on** window, locate **Attributes & Claims**, and click the **Edit **icon.
[See image.](#entra-app-edit-attributes-and-claim)
The **Attributes & Claims **window appears.
- In the **Attributes & Claims **window:
-
In the **Attributes & Claims **window, click** Add new claim**.
[See image.](#entra-app-add-new-claim)
The **Manage claim** window appears.
-
In the **Manage claim **window:
- **Name**: Enter `Department`.
- **Source**: Select **Attribute**.
- Source attribute: Select `user.department`.
-
Click **Save.**
[See image.](#entra-app-save-manage-claim)
The Department claim is added. Repeat the preceding steps to add other claims if needed.
- []Change the value of the `acceptMappedClaims` attribute to `true`.
-
Change the value of the `requestedAccessTokenVersion` attribute to `2`.
[See image.](#microsoft-graph-manifest-image)
-
To display "group names" instead of "group IDs" in ZIdentity, update the `cloud_displayname`. This configuration is required to send "group names" instead of "group IDs". To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-fed-group-claims#configure-the-azure-ad-application-registration-for-group-attributes).
[See image.](#manifest-graph-new-additioanl-properties)
[]
- [Adding an IdP in the ZIdentity Admin Portal](#zslogin-idep-configuration)
- [Configuring the Platform Settings in the Entra Admin Center](#entra-idplatform-settings)
- []Log in to the ZIdentity Admin Portal.
- Go to **Integration **> **External Identities**.
- Click **Add Primary IdP** (or **Add Secondary IdP**).
The **Add Primary Identity Provider** or **Add Secondary Identity Provider** window appears.
- On the **Basic **tab:
-
In the **General **section:
- **Name**: Enter a name for the IdP.
- **Identity Vendor**: Select **Microsoft Entra ID** from the drop-down menu.
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
[See image.](#basic-app-oidc-tab)
-
In the **OIDC Configuration **section:
- Paste the **OpenID Connect metadata document **value copied from the Entra Admin Center to the **Metadata URL **field and click **Fetch**.
-
[]Copy the **Redirect URI** value. This value is used in the client application in the Entra Admin Center in the subsequent steps.
[]If you are configuring Entra ID as the secondary IdP in the ZIdentity Admin Portal, the final segment of the **Redirect URI** is required for configuring IdP-initiated SSO. Use this value as `idp_id` as part of the **Home page URL** in the Entra Admin Center.
-
Paste the **Client ID **and **Client Secret **values copied from the Entra Admin Center to the respective fields.
In the Entra Admin Center, the value copied from the** Application (Client) ID** field must be used for the **Client ID** field, and the value copied from the **Value **column in the **Client secrets** tab must be used for the **Client Secret** field.
[See image.](#client-id-secret-illustration)
- Under **Requested Scopes**, add required scopes. By default, when the OIDC protocol is selected, the `openid`, `email`, and `profile` scopes are added.
[See image.](#metadata-url-zslogin-oidc)
- Click **Save**.
- []Go to the [Entra Admin Center](https://entra.microsoft.com/) and go to the client application created for ZIdentity.
- Go to **Manage **> **Authentication**.
-
In the **Platform configurations** section, click **Add a platform**.
[See image.](#add-platform-entra-id)
The **Configure platforms **window appears.
-
In the **Configure platforms **window:
-
Click **Web**.
[See image.](#configure-platform-entra-id)
- Paste the **Redirect URI **you** **copied earlier.
- Click **Configure**.
[See image.](#configure-web-redirect-uri)
[]This section explains how to provision Entra ID users in the ZIdentity Admin Portal. Currently, Entra ID does not support SCIM provisioning for OIDC apps added via Microsoft Entra App Gallery. Currently, provisioning is supported via Just-in-Time (JIT) provisioning with the gallery application. However if you prefer using SCIM provisioning with OIDC, you need to create a custom app in the Entra ID specifically to support SCIM-based provisioning, in addition to configuring the Microsoft Entra Gallery App for authentication.
- [Provisioning via JIT](#jit-provisioning-oidc-app)
- [Provisioning via SCIM using a Custom App](#scim-oidc-custom-app)
[]Users created in ZIdentity via SCIM cannot be updated via JIT provisioning. These records must be updated via SCIM provisioning only.
- In the ZIdentity Admin Portal, go to **Integration **> **External Identities**.
- Locate the IdP entry created for Entra ID under the **Primary Identity Provider **(or **Secondary Identity Providers**) tab and click the **Edit **icon.
-
In the** Edit Primary IdP** (or **Edit Secondary IdP**) window:
- On the **Provisioning **tab, select **Enable Just-in-time (JIT) Provisioning**.
-
Enter `groups` as the **Just-in-time User Group Attribute** and map the `Primary Email` User Attribute with the `email` JIT User Attribute.
The mapping of the `Primary Email` attribute is mandatory as it is required for functionalities, such as password resetting and multi-factor authentication.
-
Map other ZIdentity user attributes with the appropriate Entra ID attributes as necessary. By default, the following attributes in ID tokens are mapped with the corresponding user attributes in ZIdentity:
| Attribute in ID Tokens | Default ZIdentity User Attributes |
| ---------------------- | --------------------------------- |
| given_name | First Name |
| family_name | Last Name |
| name | Display Name |
- If the external IdP is configured to send different attributes for `First Name`, `Last Name`, or `Display Name`, then you must map those attributes. For example, if the ID token from the external IdP includes `Surname` instead of `family_name`, then you must map it with the `Last Name` user attribute in ZIdentity.
-
While mapping attributes, ensure that the attributes that you enter in the **Just-in-time Attribute** field match exactly with the attributes that would be received in the ID Tokens.
[See image.](#id-token-sample)
[See image.](#attribute-mapping-oidc)
- Click **Update**.
- []Log in to the [Entra Admin Center](https://entra.microsoft.com/) and go to **Identity **> **Applications** > **Enterprise applications**.
-
Click **New application**.
[See image.](#new-app-oidc-entra-id-button)
-
In the **Browse Microsoft Entra Gallery** window that appears, click **Create your own application**.
[See image.](#create-app-button-oidc-entra-id)
The **Create your own application window** appears.
- In the **Create your own application** window:
- Enter an application name for the ZIdentity service in the **What's the name of your app?** field. For example, enter `ZIdentity-OIDC-SCIM`.
- Select the **Integrate any other application you don't find in the gallery (Non-gallery)** option.
- Click **Create**.
[See image.](#create-own-app-oidc-antra-id)
- In the ZIdentity Admin Portal, go to **Integration **> **External Identities**.
-
Locate the IdP entry created for Entra ID under the **Primary Identity Provider **(or **Secondary Identity Providers**) tab and click the **Edit **icon.
The **Edit Primary IdP** (or **Edit Secondary IdP**)** **window appears.
- In the** Edit Primary IdP** (or **Edit Secondary IdP**) window:
- On the **Provisioning **tab and in the **SCIM Configuration** section:
- Select **Enable SCIM Provisioning**.
-
Copy the **SCIM Endpoint URL**. This value is used in a subsequent step.
The **SCIM Endpoint URL** field appears only if the configurations for the IdP in the **Basic** tab are completed and saved.
[See image.](#caution-scim-url-oidc-entraid)
- Click **Generate Token **and **Bearer Token **value. This value is used in a subsequent step.
- (Optional) Map the SCIM attributes (e.g., `addresses`) with the corresponding ZIdentity user attribute. This mapping is required only for attributes that need to be mapped to a custom [user attribute](/zidentity/adding-user-attributes) in ZIdentity.
- [See image.](#scim-oidc-entra-id-zslogin-tab)
- Click **Update**.
-
In the Entra Admin Center, go to **Identity > Applications > Enterprise applications**.
[See image.](#enterprise-app-option)
-
Locate and click the custom application that you created for SCIM provisioning.
The application overview page appears.
-
In the left-side navigation, click **Users and groups**.
The **Users and groups **window appears.
-
In the **Users and groups **window, select the users and groups that you want to have access to the application.
[See image.](#add-users-groups-scim)
If you want to pass group memberships as claims, make sure that the groups are assigned instead of individual users in the **Users and groups** window.
-
In the left-side navigation, click **Provisioning**.
The **Provisioning **window appears.
- In the **Provisioning **window:
- **Provisioning Mode**: Select **Automatic** from the **Provisioning Mode** drop-down menu.
- Under the **Admin Credentials **section:
-
**Tenant URL**: Enter the endpoint displayed in the **SCIM Endpoint URL** field while adding the primary or secondary IdP in the ZIdentity Admin Portal.
The **SCIM Endpoint URL** field appears only if the configurations for the IdP in the **Basic** tab are completed and saved.
[See image.](#endpoint-zs-option)
- **Secret Token**: Enter the bearer token that you generated and copied from the **Bearer Token** field while configuring the primary or secondary IdP in the ZIdentity Admin Portal.
- Click **Test Connection**. The Microsoft Entra ID attempts to connect to the SCIM endpoint. When the connection is successful, a verification message appears. If the attempt fails, error information is displayed, and you must resolve those errors before moving forward.
-
Click **Save** after a successful connection.
[See image.](#save-proviosning-scim-oidc)
The provisioning configuration is saved and the **Mappings** section appears within the **Provisioning **window.
- In the **Mappings **section:
-
Click the groups attributes mapping.
The **Attribute Mapping** window appears.
- In the **Attributes Mapping **window:
- Review the attributes that are synchronized from Microsoft Entra ID to your application.
-
Verify the group attribute mappings as listed in the following table and change as needed by clicking Edit on an existing attribute or by clicking **Add New Mapping**.
| Zscaler Attribute (Target Attribute) | Microsoft Entra Attribute (Source Attribute) | Match Objects Using this Attribute |
| ------------------------------------ | -------------------------------------------- | ---------------------------------- |
| displayName | displayName | Yes |
| externalId | objectId |  |
| members | members |  |
[See image.](#scim-group-attribute-mapping-oidc-scim)
- Click **Save** to save the attribute mapping changes.
- Return to the **Provisioning** screen.
-
Click the users attribute mapping.
The **Attribute Mapping** window appears.
- In the **Attributes Mapping **window:
- Review the attributes that are synchronized from Microsoft Entra ID to your application.
-
Verify the users attribute mappings as listed in the following table and change as needed by clicking Edit on an existing attribute or by clicking **Add New Mapping**.
| Zscaler Attribute (Target Attribute) | Microsoft Entra Attribute (Source Attribute) | Match Objects Using this Attribute |
| ------------------------------------ | -------------------------------------------- | ---------------------------------- |
| userName | userPrincipalName | Yes |
| active | Switch([IsSoftDeleted], , "False", "True", "True", "False") |  |
| displayName | displayName |  |
| emails[type eq "work"].value | mail |  |
| name.givenName | givenName |  |
| name.familyName | surname |  |
| externalid | objectId |  |
| urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | department |  |
[See image.](#scim-user-attribute-mapping-oidc-scim)
- Click **Save** to save the attribute mapping changes.
- Return to the **Provisioning** screen.
-
In the **Settings** section:
- **Send an email notification when a failure occurs**: (Optional) Select this and provide an email to receive a notification when there is a provisioning failure.
- **Prevent accidental deletion**: (Optional) Selecting this option allows you to set an Accidental deletion threshold. When the option is enabled, deleting a number of groups and users over the threshold requires approval from an admin.
- **Scope**: (Optional) Choose **Sync only assigned users and groups**. Zscaler recommends using this setting.
[See image.](#provisioning-settings-oidc-scim)
- Set the **Provisioning Status** to **On**.
[See image.](#provisionin-status-entra-id)
- Click **Save** to start the Microsoft Entra ID provisioning service.
[]You can configure step-up authentication to extend the existing authentication process by requiring multi-factor authentication (MFA) when needed, ensuring that access to high-risk or sensitive data is protected.
Prerequisites
Before configuring [step-up authentication](/zidentity/understanding-step-authentication), ensure that:
- Zscaler Client Connector version 4.7 or later is deployed for the users in your organization.
- ZIdentity is enabled for both admins and users.
- Step-up authentication is enabled for ZIdentity, Zscaler Internet Access (ZIA), and Zscaler Private Access (ZPA).
To enable step-up authentication:
- [a. Configure the necessary authentication levels in the ZIdentity Admin Portal](/zidentity/configuring-authentication-levels)
- [b. Configure ACR values and authentication policies in the Entra Admin Center](#configure-conditional-access-policies-entra)
- [c. Map authentication contexts and ACR values in the ZIdentity Admin Portal](#map-als-and-acr-in-zidentity)
- [d. Configure policies in supported Zscaler services](#policies-in-zscaler-services)
-
[]In the Entra Admin Center, go to **Entra ID **> **Conditional Access**.
[See image.](#entra-conditional-access)
- In the **Conditional Access **window, click **Authentication contexts**.
-
Click **New authentication context**.
[See image.](#entra-new-authentication-context)
-
In the **Add authentication context **drawer:
- **Name**: Enter a name for the authentication context.
- **Description**: Enter a description for the authentication context.
- **Publish **to apps: Ensure that this option is enabled.
-
**ID**: Select an ID for the authentication context from the drop-down menu. You can select a value from C1 to C99.
Each authentication context corresponds to an ACR value in ZIA Admin Portal.
Repeat the steps to create multiple authentication contexts as required for your organization.
[See image.](#authentication-context-configuration)
-
Click **Save**.
The authentication context is created.
-
In the left-side navigation, go to **Policies**, and click **New policy**.
[See image.](#entra-new-conditional-access-policy)
-
In the **New policy **window:
- Under **Assignments**:
- **Name**: Enter a name for the policy.
-
**Users**: Click the link to configure users and groups, and select the users and groups to which the policy must apply.
[See image.](#entra-conditional-access-users)
-
**Target resources**: Click the link to configure target resources, select the Authentication context from the **Select what this policy applies to** drop-down menu, and select the authentication context created previously to which the policy must apply.
[See image.](#entra-conditional-access-target-resources)
- Under **Access controls**:
- **Grant**: Click the link to configure grant controls, select **Grant access**, and select **Require multifactor authentication**.
-
Click **Select**.
[See image.](#entra-conditional-access-access-controls)
Microsoft Entra ID provides you with various controls for MFA using a combination of [authentication strength](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-strengths) and [authentication methods](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-methods-manage).
[See image.](#entra-conditional-access-policy-create)
-
Click **Create**.
The authentication policy mapped with the necessary authentication context is created.
[]In the ZIdentity Admin Portal, go to **Integration **> **External Identities**.
- Locate the IdP entry created for Entra ID under the **Primary Identity Provider** (or **Secondary Identity Providers**) tab and click the **Edit **icon.
-
In the **Edit Primary IdP** (or **Edit Secondary IdP**) window:
-
On the **Advanced** tab, in the **Levels to Authentication context mapping** section, enter the **Authentication Context ID **for each authentication level. To learn more about the supported authentication contexts in Entra ID, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-cloud-apps#authentication-context).
Ensure that you map the proper **Authentication context ID **for each level depending on the hierarchy. The highest level of authentication must be mapped to the **Authentication Context ID** for the strongest context.
[See image.](#zidentity-al-acr-mapping)
- Click **Update**.
[]After configuring step-up authentication in ZIdentity and Entra ID, you can configure the necessary policies in the following Zscaler services as required:
- ZPA: [Configure Access Policies](/zpa/configuring-access-policies) for the target application or app segment with the **Conditional Access **as the **Rule Action**. Ensure that the necessary authentication level is selected using the **Step-up Authentication **
**Level** field.
- ZIA: [Configure the URL Filtering Policy](/zia/configuring-url-filtering-policy) and [Cloud App Control Policies](/zia/adding-rules-cloud-app-control-policy) with the **Conditional Access **as the **Action**. Ensure that the necessary authentication level is selected using the **Authentication **
**Level** field.
[]
![Configuring an enterprise application in Entra Admin Center with the option to create new application highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-new-application-enterprise-button_0_0%20(1).png)
[]
![Configuring Zscaler app from Entra Gallery](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-zscaler-tile-selection.png)
[]
![Configuring Zscaler app in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-create-zscaler-app_1.png)
[]
![OIDC SSO page with the option to go to the application highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-got-to-application.png)
[]
![OIDC SSO page with Application ID highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogn-copy-client-id.png)
[]
![OIDC SSO page with the endpoint option highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-endpoints-button.png)
[]
![List of OpenID endpoints with the OIDC metadate URL highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-opein-connect-url.png)
[]
![List of client secrets with the option to create a new client secret highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zscaler-client-secret-button.png)
[]
![Adding a client secret in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-add-cleint-secret_1.png)
[]
![List of client secrets with the value of a secret highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-copy-value-secret.png)
[]
![List of configured API permissions with the option to grant admin consent highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-grant-button-highlighted.png)
[]
![Granting admin consent in API permission](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-yes-grant-popup.png)
[]
![List of configured permissions with their status highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-grant-for%20all-attributes-check.png)
[]![Configuring optional claims with the option to add an optional claim highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-optional-claim.png)
[]![Adding required claims in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-add-optional-claim-window.png)
[]![List of optional claims in token configuration page](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-token-claims.png)
[]
![Configuring optional claims with the option to add groups claim highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-add-group-claims-button.png)
[]
![Selecting custom token properties in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-edit-groupclaims-window-one_0.png)
[]
![Selecting custom token properties in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-samaaacount-valyue_0.png)
[]![Configuring optional claims with the groups claim highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-added-groups-claim.png)
[]![Configuring manifest using Microsoft Graph App with an API properties highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-microsoft-graphy-manifest.png)
[]![Configuring manifest using Microsoft Graph App with an ID token property highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-manifest-graph-cloudname_0.png)
[]
![Option to go to the OIDC SSO configuration highlighted in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-oidc-breadcrumbs_0.png)
[]
![List of users and groups assigned to the enterprise application in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-user-group-assignement_0%20(1).png)
[]
![Configuring SSO for an enterprise application in Entra Admin Center with the option to edit attributes and claims highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-edit-oidc-ssoclaims.png)
[]
![Configuring attributes and claims in Entra Admin Center with the option to add new claim option highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-add-clain.png)
[]
![Configuring claims in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-manage-claim.png)
[]
![Configuring basic information for a primary IdpP in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/Basic-tab.png)
[]
![Configuring OIDC options in ZIdentity Admin Portal](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-oidc-configuration.png)
[]
![Configuring platforms in Entra Admin Center with the option to add a platform highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-add-platform.png)
[]
![Configuring platforms in Entra Admin Center with the web platform option highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-web-platform.png)
[]
![Configuring web platform settings in Entra Admin Center with the Redirect URI highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-redirect-uri-page_0.png)
[]![A sample ID token with blurred sensitive information.](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-id-token-sample.png)
[]
![Mapping JIT attributes in ZIdentity Admin Portal](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-jit-mapping.png)
[]
![Configuring home page URL in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-idp-id-branding.png)
[]![Locating IdP ID paramter in ZIdentity and Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-primary-idp-example.png)
[]![Locating IdP ID parameter in ZIdentity and Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-secodnary-idp-example.png)
[]
![Entra ID's My Apps portal with the ZIdentity app highlighted](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-app-lauch-my-apps.png)
[]
![Landing page of ZIdentity Admin Portal](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-landing-page.png)
[]
![List of enterprise applications in Entra Admin Center with the option to create a new application highlighted](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-add-newapplication.jpg)
[]
![Entra Gallery with the option to create custom application highlighted](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-create-won-appbutton.jpg)
[]
![Creating a custom application in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-create-new-scim-app.png)
[]
![Configuring SCIM provisioning with the SCIM endpoint URL highlighted](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-scim-url-entra-oidc.png)
[]
![Configuring SCIM provisioning in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-scim-mapping.png)
[]
![Left-side navigation in Entra Admin Center with the option to configure enterprise applications highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/ZSLogin-Enterprise%20applications%20(1)%20(1).png)
[]![List of users and groups assigned to ZIdentity app in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-add-users-groups-scim.png)
[]
![Configuring SCIM provisioning in Entra Admin Center with the SCIM endpoint URL highlighted](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-scim-url-entra-oidc.png)
[]
![Configuring provisioning in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-tenant-url-new%20(1).jpg)
[]
![Mapping group attributes in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/ZIA-entra-groups-mapping-example%20(2).png)
[]
![Mapping SCIM attributes for users in Entra ID](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-attribute-mapping-for-users.png)
[]
![Configuring provisioning settings in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-settings-provision%20(1).jpg)
[]
![Enabling provisioning in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-save-option%20(1).jpg)
[]![Locating Client ID and Client secret in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-emtra-client-id-secret.jpg)
[]![Conditional access configuration option in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-conditional-access-entra-id.png)
[]![Option to create a new authentication context in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-new-authentication-context-button.png)
[]![Adding a new authentication context in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-add-authentication-context-drawer.png)
[]![The option to create a new conditional access policy in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-new-policy-button-entra-id.png)
[]![Configuring users and groups in a conditional access policy](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-entra-policy-users.png)
[]![Configuring targered resources in conditional access policy](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-new-policy-target-resources.png)
[]![Configuring access controls in conditional access policy](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-entra-id-grant-drawer.png)
[]![Configuring conditional access policy](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-new-policy-full.png)
[]![Mapping authentication contexts with authentication levels](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-mappingal-acr-entra-id.png)
[]This section explains how to configure Microsoft Entra ID as an identity provider (IdP) for the ZIdentity service. Zscaler recommends configuring the IdP and service provider (SP) simultaneously as configurations are interdependent on each other. To learn more, see [Adding SAML Identity Providers](/zidentity/adding-saml-identity-providers).
Prerequisites
Ensure that you have:
- A premium Microsoft Entra ID subscription.
- An existing directory in Microsoft Entra ID.
- A ZIdentity account with an admin role that allows you to add an IdP configuration.
Configuring Microsoft Entra ID as IdP for ZIdentity
[]To set up Microsoft Entra ID as an IdP for ZIdentity:
- [1. Set up Microsoft Entra ID as an IdP for ZIdentity.](#entra-id-idp-step-1)
- [2. Provision users for ZIdentity.](#provision-users-entra-id-methods-saml)
- []Log in to the [Entra Admin Center](https://entra.microsoft.com/) and go to **Identity **> **Applications** > **Enterprise applications** from the left-side navigation.
[See image.](#enterprise-app)
- Click **New application**, then **Create your own application**.
- In the **Create your own application** window, enter an application name for the ZIdentity service in the **What's the name of your app?** field. For example, enter `ZIdentity`.
- Select the **Integrate any other application you don't find in the gallery (Non-gallery)** option.
-
Click **Create**.
[See image.](#create-your-app)
The Microsoft Entra ID service displays a notification that the application is added and you are redirected to the application's **Overview** page.
-
From the left-side navigation, click **Single sign-on**, then **SAML**.
[See image.](#single-sign-on)
The **Set up Single Sign-on with SAML** page appears.
-
In the **Basic SAML Configuration **section, click **Edit** and do the following:
- **Identifier (Entity ID)**: Enter the entity ID displayed in the **SP Entity ID** field when you [configure Microsoft Entra ID as an IdP](/zidentity/adding-saml-identity-providers) in the ZIdentity Admin Portal. This ID is specific to your IdP.
-
**Reply URL (Assertion Customer Service URL)**: Enter the URL that is displayed **SP URL **field when you [configure Microsoft Entra ID as an IdP](/zidentity/adding-saml-identity-providers) in the ZIdentity Admin Portal.
[See image.](#sp-entity-id-zs)
- Leave the other fields blank.
- Click **Save** and exit the window.
[See image.](#basic-saml-cong)
After saving, you are prompted to test the configuration. Do not test the configuration at this time.
-
In the **User Attributes & Claims **section, verify that you have the necessary claims mapped to the attributes.
[See image.](#user-attributes-claims)
-
Map the required attributes in the ZIdentity Admin Portal. The mapping of the `Primary Email` attribute is mandatory as it is required for functionalities, such as password resetting or multi-factor authentication.
[See image.](#group-attribute-zs)
-
Click **Add a group claim **and do the following:
- **Which groups associated with the user should be returned in the claim?**: Select **Groups assigned to the application**.
- **Source attribute**: Select **Cloud-only group display names**.
- Enable the **Customize the name of the group claim** option.
- **Name (required)**: Enter a name for the group attribute.
- Click **Save **and exit the window.
[See image.](#group-attribute)
Map this attribute to the **User Group SAML Attribute** field in the ZIdentity Admin Portal when [configuring Microsoft Entra ID as an IdP](/zidentity/adding-saml-identity-providers).
-
Depending on how you want to provide the IdP inputs when [configuring Microsoft Entra ID as an IdP](/zidentity/adding-saml-identity-providers#input-method) in the ZIdentity Admin Portal, complete one of the following actions:
- [Metadata URL](#meta-url)
- [Upload Metadata](#upload-meta)
- [Enter Manually](#manually)
[See image.](#idp-input-method-zs)
- (Optional) If you want to enable the SAML request and response signing options in the ZIdentity Admin Portal, go to the **Advanced **tab, and do the following:
- Enable **SAML Request Signing**.
-
**Signing Algorithm**: Select **SHA-256 **from the drop-down menu.
[See image.](#saml-request-signing-image)
-
Under **SP SAML Certificate**, click **Download Certificate**.
[See image.](#download-saml-certificate-image)
The Service Provider (SP) SAML Certificate is downloaded to your system as a PEM file. Rename this file and change the file extension from `.pem` to `.cer`.
- Select **Encrypted SAML Assertion**.
-
Under **SAML Encryption Certificate**, click **Download Certificate**.
[See image.](#download-saml-encryption-certificate-image)
The SAML Encryption Certificate is downloaded to your system as a PEM file. Rename this file and change the file extension from `.pem` to `.cer`.
- Click **Update**.
- Go to the Entra Admin Center and go to the application created for ZIdentity.
-
To complete the SAML Request Signing configuration, go to **Manage **> **Single sign-on**, and click the **Edit **icon for the **Verification certificates (optional)** section.
[See image.](#edit-verification-certificate-image)
-
In the **Verification certificates **window:
-
Select **Require verification certificates**.
If the **Require verification certificates** option is enabled, the SAML Request Signature Verification works only for SP-initiated authentication requests. The IdP-initiated authentication requests are not validated as the IdP would not possess the same private keys as the registered application. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/howto-enforce-signed-saml-authentication).
-
Click **Upload certificate **and upload the SP SAML Certificate file downloaded from the ZIdentity Admin Portal.
Ensure that the SP SAML Encryption Certificate was renamed by changing the file extension from `.pem` to `.cer` before uploading.
- Click **Save**.
[See image.](#verification-certificate-window-image)
The **Verification Certificate** is uploaded to the Entra Admin Center.
- To complete the Encrypted SAML Assertion configuration, go to **Security **> **Token encryption**.
-
Click **Import Certificate **and upload the SAML Encryption Certificate file downloaded from the ZIdentity Admin Portal.
[See image.](#token-encryption-window-image)
Ensure that the SAML Encryption Certificate file was renamed by changing the file extension from `.pem` to `.cer` before uploading.
-
In the left-side navigation, go to **Manage **> **Single Sign-on**, and click the **Edit **icon for the **SAML Certificates **section.
[See image.](#sign-on-window-image)
-
In the **SAML Signing Certificate **window:
- **Signing Option**: Select **Sign SAML response and assertion **from the drop-down menu.
- **Signing Algorithm**: Select **SHA-256** from the drop-down menu,
- Click **Save**.
[See image.](#saml-sigining-window-image)
The configuration in the Azure Portal is completed. Finish the [IdP configuration in the ZIdentity Admin Portal](/zidentity/adding-saml-identity-providers) to set up Microsoft Entra ID as an IdP for ZIdentity.
Assigning Users and Groups to ZIdentity
To assign users to the ZIdentity service:
- Go to **Identity **> **Applications** > **Enterprise applications** from the left-side navigation.
- Search and open the ZIdentity application.
-
From the left-side navigation, click **Users and groups**, then **Add user/group**.
[See image.](#add-user-group)
The **Users and groups** window appears.
- Search for the user or group you want to assign to ZIdentity service.
-
Select the checkbox next to the user or group names you want to assign to the ZIdentity service, then click **Select**.
[See image.](#adding-user)
If you want to pass group memberships as claims, make sure that the groups are assigned instead of individual users in the **Users and groups** window.
-
In the **Add Assignment** panel, click **Assign**.
[See image.](#assign-user)
You are redirected to the **Users and groups** page where you can see the users are successfully assigned to ZIdentity.
[See image.](#assigned-users)
[]This section provides information on how to set up Microsoft Entra ID to use System for Cross-Domain Identity Management (SCIM) in ZIdentity. SCIM allows you to quickly remove, manage, or add users to ZIdentity. Before you proceed, ensure that you have the **Enable SCIM Provisioning** option selected when [configuring Microsoft Entra ID as an IdP](/zidentity/adding-saml-identity-providers) in the ZIdentity Admin Portal.
Optionally, map the SCIM attributes (e.g., `addresses`) with the corresponding ZIdentity user attribute. This mapping is required only for attributes that need to be mapped to a custom [user attribute](/zidentity/adding-user-attributes) in ZIdentity.
[See image.](#screenshot-enable-scim)
To configure SCIM in Microsoft Entra ID:
- Log in to the [Entra Admin Center](https://entra.microsoft.com/) and go to **Identity > Applications > Enterprise applications**.
[See image.](#AzurePortal)
-
Locate and click the ZIdentity application that you created.
The application overview page appears.
-
In the left-side navigation, click **Provisioning**.
The **Provisioning** window appears.
- In the **Provisioning** window:
- **Provisioning Mode**: Select **Automatic** from the **Provisioning Mode** drop-down menu.
- Under the **Admin Credentials** section:
-
**Tenant URL**: Enter the endpoint displayed in the **SCIM Endpoint URL** field while configuring the primary or secondary IdP in the ZIdentity Admin Portal.
The **SCIM Endpoint URL** field appears only if the configurations for the IdP in the **Basic** tab are completed and saved.
[See image.](#endpoint-zs)
- **Secret Token**: Enter the bearer token that you generated and copied from the **Bearer Token** field while configuring the primary or secondary IdP in the ZIdentity Admin Portal.
- Click **Test Connection**. The Microsoft Entra ID attempts to connect to the SCIM endpoint. When the connection is successful, a verification message appears. If the attempt fails, error information is displayed, and you must resolve those errors before moving forward.
-
Click **Save** after a successful connection.
[See image.](#AzureSaveProvisioning)
The provisioning configuration is saved and the **Mappings** section appears within the **Provisioning **window.
- Under the **Mappings **section:
-
Click the groups attributes mapping.
The **Attribute Mapping** window appears.
- In the **Attributes Mapping **window:
- Review the attributes that are synchronized from Microsoft Entra ID to your application.
-
Verify the group attribute mappings as listed in the following table and change as needed by clicking Edit on an existing attribute or by clicking **Add New Mapping**.
| Zscaler Attribute (Target Attribute) | Microsoft Entra Attribute (Source Attribute) | Match Objects Using this Attribute |
| ------------------------------------ | -------------------------------------------- | ---------------------------------- |
| displayName | displayName | Yes |
| externalId | objectId |  |
| members | members |  |
[See image.](#scim-group-attribute-mapping)
- Click **Save** to save the attribute mapping changes.
- Return to the **Provisioning** screen.
-
Click the users attribute mapping.
The **Attribute Mapping** window appears.
- In the **Attributes Mapping **window:
- Review the attributes that are synchronized from Microsoft Entra ID to your application.
-
Verify the users attribute mappings as listed in the following table and change as needed by clicking Edit on an existing attribute or by clicking **Add New Mapping**.
| Zscaler Attribute (Target Attribute) | Microsoft Entra Attribute (Source Attribute) | Match Objects Using this Attribute |
| ------------------------------------ | -------------------------------------------- | ---------------------------------- |
| userName | userPrincipalName | Yes |
| active | Switch([IsSoftDeleted], , "False", "True", "True", "False") |  |
| displayName | displayName |  |
| emails[type eq "work"].value | mail |  |
| name.givenName | givenName |  |
| name.familyName | surname |  |
| externalid | objectId |  |
| urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | department |  |
[See image.](#scim-user-attribute-mapping)
- Click **Save** to save the attribute mapping changes.
- Return to the **Provisioning** screen.
-
Under the **Settings** section:
- **Send an email notification when a failure occurs**: (Optional) Select this and provide an email to receive a notification when there is a provisioning failure.
- **Prevent accidental deletion**: (Optional) Selecting this option allows you to set an Accidental deletion threshold. When the option is enabled, deleting a number of groups and users over the threshold requires approval from an admin.
- **Scope**: (Optional) Choose **Sync only assigned users and groups**. Zscaler recommends using this setting.
[See image.](#provisioning-settings)
- Set the **Provisioning Status** to **On**.
[See image.](#AzureProvisioningStatus)
- Click **Save** to start the Microsoft Entra ID provisioning service.
[]![Enabling SCIM provisioning in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-scim-mapping_0.png)
[]![Configuring SCIM provisioning in ZIdentity with the SCIM endpoint URL highlighted](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-scim-url-entraid-saml.png)
[]![Left-side navigation in Entra Admin Center with the option to configure enterprise applications highlighted](/downloads/zslogin/administration/authentication/scim-configuration-guide-microsoft-entra-id/ZSLogin-Enterprise%20applications%20(1).png)
[]![Verifying provisionin status and saving the configuration](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-tenant-url-new%20(2).jpg)
[]
![Mapping group attributes in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/ZIA-entra-groups-mapping-example%20(1).png)
[]
![Mapping attributes in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp-1/zidentiy-attribute-mapping_0.png)
[]
![Configuring settings for user provisioning in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-settings-provision.jpg)
[]![Verifying the provisioning status and saving the configuration](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-save-option.jpg)
[]![Single Sign-on page with the edit button highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-edit-button_0.png)
[]![Attributes & Claims page with the Add new claim button highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-add-new-claim-button.png)
[]![Configuring custom claim in Entra ID](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-manage-claim-page.png)
[]From the **SAML Signing Certificate **section, copy the URL displayed in the **App Federation Metadata Url **field. Paste this metadata URL in the **IdP Metadata URL **field in the ZIdentity Admin Portal when [configuring Microsoft Entra ID as an IdP](/zpa/about-idp/new#IdP_BothSSO).
[See image.](#fed-metadata-url)
[]From the **SAML Signing Certificate **section, for the **Federation Metadata XML **field, click the **Download** link to obtain the metadata file. Upload this IdP metadata to the **IdP Metadata **field in the ZIdentity Admin Portal when [configuring Microsoft Entra ID as an IdP](/zpa/about-idp/new#IdP_BothSSO).
[See image.](#fed-metadata-xml)
-
[]From the **Set up **section, copy the **Microsoft Entra Identifier **and **Login URL **values. Paste these values in **IdP Issuer URI **and **IdP Single Sign-On URL **fields respectively in the ZIdentity Admin Portal when [configuring Microsoft Entra ID as an IdP](/zpa/about-idp/new#IdP_BothSSO).
[See image.](#login-url-identifier)
-
From the **SAML Signing Certificate **section, download **Certificate (base64)**. Upload this certificate to the **IdP Certificate **field in the ZIdentity Admin Portal when [configuring Microsoft Entra ID as an IdP](/zpa/about-idp/new#IdP_BothSSO).
[See image.](#cert-base64)
-
Ensure the certificate file name:
- Has a **.**`pem` extension (e.g., rename it to `entra`.pem). The ZIdentity service only accepts certificates with the .`pem` extension.
- Contains only one period (".").
[See image.](#perm-file)
By default, Windows hides extensions for known file types.
- [Change the Windows Folder Properties to View and Edit Extensions](#pem-instructions)
- []Start Windows 10 Control Panel.
- Go to **Appearance & Personalization** > **File Explorer Options**.
- When the **File Explorer Options** window appears, click the **View **tab.
-
In **Advanced settings:** deselect **Hide extensions for known file types** to view extensions.
[See image.](#explorer)
- Rename the certificate to change the extension.
[]![Left-side navigation in Entra Admin Center with the option to configure enterprise applications highlighted](/downloads/zslogin/administration/authentication/idp-configuration-guide-microsoft-entra-id/ZSLogin-Enterprise%20applications%20(1).png)
[]![Creating your own application in Entra Admin Center](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-create-your-own-app_0.jpg)
[]![Configuring group claims in Entra Admin Center](/downloads/zslogin/administration/idp-configuration-guide-microsoft-azure-ad/ZSLogin-group-attribute.png)
[]![Adding JIT attributes](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-jit-entra-saml.png)
[]![Left-side navigation in Entra Admin Center with the option to configure SSO highlighted](/downloads/zslogin/administration/configuration-guide-microsoft-azure-ad/ZSLogin-Single%20sign-on.png)
[]![Locating SP Entity ID and SP URL in the ZIdentity Admin Portal](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-saml-configuration-entraid.png)
[]![Configuring basic SAML properties for an Entra ID app](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/ZSLogin-Basic-SAML-Configuration-section_0.png)
![Verifying the mapping of necessary attributes and claims in an Entra ID app](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-attribbutes-and-claims_0.png)
[]
[]![Configuring input method for metadata in ZIdentity Admin Portal](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-entra-saml_0.png)
[]![Locating the option to add a new user or group in Entra ID Admin Center](/downloads/zslogin/administration/configuration-guide-microsoft-azure-ad/ZSLogin-Add-user-group.png)
[]![Selecting a user for adding them to Entra ID Admin Center](/downloads/zslogin/administration/configuration-guide-microsoft-azure-ad/ZSLogin-adding-users.png)
[]![Assigning users to Entra ID app](/downloads/zslogin/administration/configuration-guide-microsoft-azure-ad/ZSLogin-Assign-user-group.png)
![Locating options to download and upload IdP certificate from Entra Admin Center and ZIdentity Admin Portal respectively](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp-1/ZSLogin-Certificate-base64.png)
[]
[]![Locating fields to obtain and configure Login URLs in Entra ID and ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp-1/ZSLogin-login-url-%26-Identifier%20_0.png)
[]![Locating options to download and upload metadat XML in Entra ID and ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp-1/ZSLogin-Federation%20Metadata%20XML.png)
[]![Locating fields to obtain and configure metadat URLs in Entra ID and ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp-1/zidentity-idp-url-entra-saml-meta.png)
[]![Locating the downloaded PEM file in Windows](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/Windows-Azure-signing-certificate-pem.png)
[]![Configuring the option to view file extensions for known file types in Windows](/downloads/zslogin/administration/configuration-guide-microsoft-azure-ad/Windows-File-Explorer-Options-View-Hide-extensions-for-known-file-types.png)
[]![List of users assigned to ZIdentity app in Entra ID](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/ZSLogin-users-assigned-in-azure-portal.png)
[]
![Enabling SAML request signing in the ZIdentiy Admin Portal](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-signing-request-entra-scaml.png)
[]
![Option to download SP SAML certificate from the ZIdentity Admin Portal](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-signing-request-entra-saml-download.png)
[]
![Option to download SAML encryption certificate from the ZIdentity Admin Portal](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zidentity-certificate-download.png)
[]
![Configuring SSO in Entra Admin Center with the option to edit verification certificates highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-edit-verification-certification-entra-id-new.png)
[]
![Enabling certificate verification for SSO in Entra Admin Center](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-upload-verification-certificate.png)
[]
![Configuring SAML token encryption in Entra Admin Center with the option to import a certificate highlighted](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-import-certificate-token.png)
[]
![Configuring SSO in Entra Admin Center with the option to edit SAML certificates highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-edit-token.png)
[]
![Configuring signing option and algorithm for a SAML Signing Certificate in Entra Admin Center](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zslogin-saml-signing-certificate-window.png)
[]
![ZIdentity Landing page with highlighted banner at the top.](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-entra-id-external-idp/zid-landing-page-1%20(1).png)