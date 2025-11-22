# Configuring PingOne as an External IdP
Source: https://help.zscaler.com/unified/configuring-pingone-external-idp
PDF: https://help.zscaler.com/pdf/com/en/1505476.pdf

This guide provides information on how to configure PingOne as the OpenID Provider (OP) for the ZIdentity to facilitate single sign-on (SSO) to various Zscaler services for admin access management.
Zscaler and Ping Identity are technology partners. To learn more about integrating Zscaler and Ping Identity, see the [Zscaler and Ping Identity Deployment Guide](/zscaler-technology-partners/zscaler-and-pingone-deployment-guide).
Prerequisites
Ensure that you have:
- A subscription to PingOne.
- An existing user directory in PingOne.
- A ZIdentity account with an admin role that allows you to add an IdP configuration.
IdP-Initiated SSO for ZIdentity Tenants Enabled with Experience Center
During the IdP-initiated SSO for ZIdentity, tenants using OIDC or SAML protocols are redirected as follows:
- [OIDC Protocol](#OIDC-protocol-redirection)
- [SAML Protocol](#SAML-protocol-redirection)
To change the default redirection, contact [Zscaler Support](/contact-support).
[]
All admins authenticating using the SAML protocol for ZIdentity and IdP integrations are redirected to Experience Center. However, if the `zidServiceId` attribute is configured in the IdP within the ZIdentity tenant, then the admins are redirected to the ZIdentity Admin Portal instead of Experience Center.
[]
ZIdentity tenants that are enabled with Experience Center at the time of tenant creation and admins using OIDC protocol for ZIdentity and IdP integrations are redirected to the Experience Center.
ZIdentity tenants that are not enabled with Experience Center at the time of tenant creation and admins using OIDC protocol for ZIdentity and IdP integrations are redirected to the ZIdentity Admin Portal. They can click the link in the banner shown on the [ZIdentity Landing page](/zidentity/accessing-and-navigating-zidentity-landing-page) and go to the Experience Center.
[See image.](#ec-zidlandingpage)
If you want to change this default behavior and have users redirected to the Experience Center, raise a Support ticket with the ticket type set to **Provisioning**.
Configuring PingOne as OP for ZIdentity
Complete the following steps to set up PingOne as an OP for ZIdentity:
- [1. Configure custom OIDC application in PingOne.](#add-app-pingone)
- [2. Set up PingOne as an OP for ZIdentity.](#setup-pingone-as-op)
- [3. Provision users for ZIdentity.](#provision-users-pingone)
- [4. (Optional) Enable step-up authentication.](#enabling-step-up-authentication)
- [][Log in to the PingOne admin console](https://docs.pingidentity.com/r/en-us/pingone/p1_access_admin_console).
- Go to **Applications **> **Applications**.
-
Click the **Add Application** icon.
[See image.](#add-application-oidc-pingone)
-
In the **Add Application** drawer:
- **Application Name**: Enter a name for the application.
- **Description**: (Optional) Enter a description for the application.
- **Icon**: (Optional) Upload an icon for the application.
- **Application Type**: Select the **OIDC Web App** option.
- Click **Save**.
[See image.](#pingone-add-application-window)
The OIDC web application is created.
- In the application drawer, click the **Configuration **tab, and do the following:
-
In the **General **section, copy the **Client ID** and **Client Secret **values.
[See image.](#pingone-copy-id-secret)
-
In the **URLs** section, copy the **OIDC Discovery Endpoint** value.
[See image.](#pingone-discovery-url)
-
Select the **Resources **tab and click the **Edit **icon.
[See image.](#pingone-edit-resources)
The **Edit Resources **page appears within the application drawer.
-
On the **Edit Resources **page:
- Under the **Scopes **tab, select **email **and **Profile **to include them as allowed scopes.
- Click **Save**.
[See image.](#pingone-add-scope)
-
Click the toggle on the top right to enable the application.
[See image.](#pingone-enable-app)
- []Log in to the Admin Portal.
- Go to **Administration **> **Identity **> **ZIdentity** > **External Identities**.
- Click **Add Primary IdP** (or **Add Secondary IdP**).
The **Add Primary Identity Provider** or **Add Secondary Identity Provider** window appears.
- On the **Basic **tab:
-
In the **General **section:
- **Name**: Enter a name for the IdP.
- **Identity Vendor**: Select **PingOne **from the drop-down menu.
- **Domain**: Select the domain for which the IdP is responsible for authenticating the users. This allows the Zscaler service to display the correct IdP to authenticate an incoming user.
- **Protocol**: Select **OIDC**.
- **Status**: Select **Enabled**.
-
**Login ID Attribute**: Enter an attribute whose value must be used as the login ID. This attribute must exist in the tokens received from the IdP. By default, the `preferred_username` attribute is populated in this field when the **OIDC **option is selected in the **Protocol** field. You can use any attribute that is present in the ID token or UserInfo response, provided its value is in the email address format (e.g., <user_name>@domain.com>).
- Ensure that the domain part of the email addresses received in the ID tokens match with one of the domains configured in ZIdentity.
- Ensure that the attribute you enter matches exactly with the attribute in the ID token or UserInfo endpoint.
-
**Enforce Zscaler Admin MFA**: Enable this option to ensure that admins using an external IdP authenticate with the multi-factor authentication (MFA) process in ZIdentity, irrespective of whether MFA is configured on the external IdP.
An email is sent to all super admins in ZIdentity when the **Enforce Zscaler Admin MFA **option is disabled.
[See image.](#basic-setup-pingone)
-
In the **OIDC Configuration **section:
- Paste the **Client ID **and **Client Secret **values [copied from the PingOne admin console](#add-app-pingone) to the respective fields.
- Paste the **OIDC Discovery Endpoint **value [copied from the PingOne admin console](#add-app-pingone) to the **Metadata URL **field and click **Fetch**.
- Copy the **Redirect URI **value. The value copied in this step is used in the subsequent steps for configurations in the PingOne admin console.
- In the **Requested Scopes** section, add the required scopes. By default, when the OIDC protocol is selected, the `openid`, `email`, and `profile` scopes are added.
[See image.](#oidc-setup-pingone)
- In the PingOne admin console, go to **Applications** > **Applications **and click the OIDC web application created in the [previous step](#add-app-pingone).
-
Select the **Configuration** tab, and** **click the **Edit **icon.
[See image.](#pingone-edit-configuration)
The **Edit Configuration** page appears within the application drawer.
-
On the **Edit Configuration** page:
- Paste the **Redirect URI** value copied from the Admin Portal to the **Redirect** **URIs **field.
- Click **Save**.
[See image.](#pingone-redirect-uri)
- [][In the Admin Portal](#zidentity-side-provisioning)
- [In the PingOne Admin Console](#pingone-side-provisioning)
[]Users created in ZIdentity via SCIM cannot be updated using JIT provisioning. These user records must be updated via SCIM provisioning only.
- In the Admin Portal, go to **Administration **> **Identity **> **ZIdentity** > **External Identities**.
- Locate the IdP entry created for PingOne under the **Primary Identity Provider **(or **Secondary Identity Providers**) tab and click the **Edit **icon.
- In the** Edit Primary IdP** (or **Edit Secondary IdP**) window:
- Select the **Provisioning **tab.
-
Select **Enable Just-in-time (JIT) Provisioning**.
Users created in ZIdentity via SCIM cannot be updated through JIT provisioning. These user records must be updated via SCIM provisioning only.
-
Map ZIdentity user attributes with the appropriate PingOne attributes as necessary. The mapping of the `Primay Email` attribute is mandatory as it is required for password resetting and multi-factor authentication. By default, the following attributes in ID tokens are mapped with the corresponding user attributes in ZIdentity.
| Attribute in ID Tokens | Default ZIdentity User Attributes |
| ---------------------- | --------------------------------- |
| given_name | First Name |
| family_name | Last Name |
| name | Display Name |
If the external IdP is configured to send different attributes for `First Name`, `Last Name`, or `Display Name`, then you must map those attributes. For example, if the ID token from the external IdP includes `Surname` instead of `family_name`, then you must map it with the `Last Name` user attribute in ZIdentity.
- Select **Enable SCIM Provisioning**.
-
Copy the **SCIM Endpoint URL**. This value is used in a subsequent step.
The SCIM Endpoint URL field appears only if the configurations for the IdP on the Basic tab are completed and saved.
[See image.](#scim-url-token)
- Click **Generate Token** and copy the **Bearer Token **value. This value is used in a subsequent step.
-
(Optional) Map the SCIM attribute (e.g., `addresses`) with the corresponding ZIdentity user attribute. This mapping is required only for attributes that need to be mapped to a custom [user attribute](/unified/adding-user-attributes) in ZIdentity. To learn more about the SCIM attributes that require custom attribute mapping, see [Understanding SCIM](/unified/understanding-scim-0).
[See image.](#jit-zslogin-pingone)
- Click **Update**.
- []In the PingOne admin console, go to **Applications **> **Applications**.
- Locate and click the application created for ZIdentity.
-
In the application drawer that appears, select the **Attributes Mapping **tab, and click the **Edit **icon in the **Custom Attributes **section.
[See image.](#attribute-mapping-tab-pingone)
The **Edit Attribute Mappings **page appears within the application drawer.
- On the **Edit Attribute Mappings **page:
-
Click **Add **and map the necessary attributes configured in the Admin Portal.
[See image.](#add-attribute-mapping-pingone)
To map an expression with an attribute, locate the attribute for which you want to add an expression, and click the **Advanced Expressions **icon, and configure the expression. For example, the `name` attribute in ZIdentity is mapped combining `Given Name` and `Family Name` attributes in PingOne.
[See image.](#gif-attribute-mapping)
-
Click **Save**.
[See image.](#all-attributes-pingone)
- In the left-side navigation, go to **Integration **> **Provisioning**.
-
Click the **Add **icon and add a new connection.
[See image.](#add-new-connection)
- In the **Create a new connection **drawer:
-
Select **Identity Store **as the connection type.
[See image.](#identity-store-select)
- Search for `scim` and the **SCIM Outbound** app appears.
-
Select the **SCIM Outbound **app and click **Next**.
[See image.](#scim-search-select)
-
Enter a name for the connection and click **Next**.
[See image.](#name-descrption-scim-outbound)
- Paste the **SCIM Endpoint URL **[copied from the Admin Portal](#provision-users-pingone) to the **SCIM Base URL** field.
- Select** OAuth 2 Bearer Token** from the **Authentication Method** drop-down menu and paste the **Bearer Token **[copied from the Admin Portal](#zidentity-side-provisioning) to the **Oauth Access token **field.
-
Click **Test Connection** to ensure the connection is successful and click **Next**.
[See image.](#scim-configuration-pingone)
-
Click **Save**.
[See image.](#scim-outbound-last-step)
A new **SCIM Outbound** connection is created.
-
Enable the toggle.
[See image.](#enabled-scim-connection)
-
Click the **Add **icon and select **New Rule**.
[See image.](#new-rule-option)
The **Create New Rule **drawer appears.
- In the **Create New Rule** drawer:
- **Name**: Enter a name for the rule.
-
**Description**: Enter a description for the rule.
[See image.](#new-rule-name-description)
-
Click **Create Rule**.
The rule is created, and the rule configuration drawer opens with the **Configuration **tab selected.
- In the rule configuration drawer:
-
Select the SCIM Outbound app connection created for ZIdentity as the target.
[See image.](#select-target-new-rule)
-
Click **Save**.
The connection is saved and the options to apply user filter, attribute mapping, and group provisioning appears.
-
In the** User Filter** section, click the **Edit **icon.
[See image.](#edit-user-filter)
The **Edit User Filter **page appears.
-
In the **Edit User Filter** page, configure the necessary conditions for user filter. For example, you can filter users based on specific Group Names.
[See image.](#user-filter-configuration)
- Click **Save.**
-
Go to **Attribute Mapping **and modify the attributes if necessary.
[See image.](#rule-attribute-mapping)
-
Go to **Group Provisioning**,** **and in the **Group Provisioning **section, click the **Edit **icon or click **Add Groups**.
[See image.](#add-groups-rule)
The **Edit Group Provisioning **page appears within the rule configuration drawer.
- In the **Edit Group Provisioning **page:
-
Select the groups that you want to be provisioned for ZIdentity.
[See image.](#provisioning-groups)
- Click **Save**.
-
Confirm group overwriting for the matching groups.
The selected groups are added for group provisioning.
-
Enable the toggle.
[See image.](#rule-group-enabled)
[]You can configure step-up authentication to extend the existing authentication process by requiring multi-factor authentication (MFA) when needed, ensuring that access to high-risk or sensitive data is protected.
Prerequisites
Before configuring [step-up authentication](/unified/understanding-step-up-authentication), ensure that:
- Zscaler Client Connector version 4.7 or later is deployed for the users in your organization.
- ZIdentity is enabled for both admins and users.
- Step-up authentication is enabled for ZIdentity, Internet & SaaS, and Private Applications.
To enable step-up authentication:
- [a. Configure the necessary authentication levels in the ZIdentity](/unified/configuring-authentication-levels)
- [b. Enable ACR values and configure policies in the PingOne admin console](#enable-acr-and-policiesin-pingone)
- [c. Map authentication levels and ACR values in the Admin Portal](#map-als-and-acr-in-zidentity)
- [d. Configure policies in supported Zscaler services](#policies-in-zscaler-services)
- []Log in to the PingOne admin console.
- In the left-side navigation, go to **Authentication **> **Policies **> **MFA**.
-
In the **MFA Policies **window, click **Add policy**.
[See image.](#add-mfa-policy-pingone)
-
In the **Add Policy **drawer:
If you want to use an existing policy, ensure that the necessary authentication options are enabled and skip the steps to add new policy.
- **Name**: Enter a name for the MFA policy.
- **Method Selection**: Select how PingOne should determine the MFA method during user authentication.
-
**Send notification when a new device is paired**: Select how PingOne must notify users when a new MFA device is paired to the user account.
[See image.](#mfa-policy-pingone-first)
-
**Allowed Authentication Methods**: Enable the necessary authentication options, such as authenticator app, email, SMS, FIDO2, etc.
[See image.](#mfa-policy-pingone-second)
Ensure that you select only the required authentication methods as the user is prompted with all options configured in this step.
-
Click **Save**.
The MFA policy is created.
- Based on your requirements, you can create multiple MFA policies as required.
- Users can register for the MFA options from the self-service portal (aka PingOne Self-Service - MyAccount app). To verify what information is displayed on the self-service portal for the users, go to **Settings **> **Environments**, click the three dots against the environment created for the ZIdentity app, and select **Properties**. Fetch the self-service URL from the drawer and access the self-service page.
- In the left-side navigation, go to **Authentication **> **Policies **> **Authentication**.
-
Click **Add Policy**.
[See image.](#add-authentication-policy-pingone)
-
In the policy configuration window:
- **Policy Name**: Enter the ACR value that must be mapped to the authentication level in Admin Portal. For example, if you are configuring this authentication policy for email authentication, enter `Email` as the policy name.
- **Step type**: Select **Multi-Factor Authentication**.
- **MFA Policy**: Select the required MFA policy configured for step-up authentication.
-
**Required When**: Select the options when the MFA must be triggered (e.g., always, last sign-on is older than 1 hour, etc.).
[See image.](#single-step-mfa-pingone)
Repeat these steps to create additional policies based on your requirements.
- Click **Save**.
- Go to **Applications **> **Applications**
- Locate and click the application created for ZIdentity.
-
In the application drawer that appears, select the **Policies **tab, and click the **Edit **icon.
[See image.](#application-poingone-policies)
-
Associate the authentication policies created for the application.
[See image.](#select-policies-pingone-application)
- Click **Save**.
- []In the Admin Portal, go to **Administration **> **Identity **> **ZIdentity** > **External Identities**.
- Locate the IdP entry created for PingOne under the **Primary Identity Provider** (or **Secondary Identity Providers**) tab and click the **Edit **icon.
-
In the **Edit Primary IdP** (or **Edit Secondary IdP**) window:
- Select the **Advanced** tab.
-
Under the **Levels to Authentication context mapping** section, enter the **ACR Claim** value for each authentication level. To learn more about the supported ACR Claims in PingOne, refer to the [PingOne documentation](https://docs.pingidentity.com/pingone/applications/p1_edit_application_oidc.html).
Ensure that you map proper ACR claims for each level depending on the hierarchy. The highest level of authentication must be mapped to the ACR value for the strongest context.
[See image.](#zidentity-al-acr-mapping)
- Click **Update**.
[]After configuring step-up authentication in ZIdentity and PingOne, you can configure the necessary policies in the following Zscaler services:
- Private Applications: [Configure Access Policies](/unified/configuring-access-policies) for the target application or app segment with the **Conditional Access **as the **Rule Action**. Ensure that the necessary authentication level is selected using the **Step-up Authentication Level **field.
- Internet & SaaS: [Configure the URL Filtering Policy](/unified/configuring-url-filtering-policy) and [Cloud App Control Policies](/unified/adding-rules-cloud-app-control-policy) with the **Conditional Access **as the **Action**. Ensure that the necessary authentication level is selected using the **Authentication Level **field.
[]![A screenshot highlighting the Add Application option in PingOne Admin Console](/downloads/zslogin/administration/authentication/Third-Party%20OIDC/zslogin-add-application-window.jpg)
[]
![A screenshot of Add Application window in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-add-application.png)
[]
![A screenshot highlighting Client ID and Secret in PingOne ZIdentity App](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-client-id-secret-pingone.png)
[]
![A screenshot highlighting OIDC Endpoint in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-oidc-endpoint_1.png)
[]
![A screenshot highlighting the option to edit configurations in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-edit-configuration_0.png)
[]
![A screenshot highlighting Redirect URIs in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-redirect-uro.png)
[]
![A screenshot highlioghting the option to edit resources in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-scope-edit-pingone.png)
[]
![A screenshot of scope selection for ZIdentity app in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-add-scopes.png)
[]
![A screenshot highlighting the Activation toggle in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-added-scopes.png)
[]
![Configuring basic information for an IdP in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/Basic-tab.png)
[]
![A screenshot highlighting metadata URL in ZIdentity Admin Portal ](/downloads/zslogin/authentication/external-idp-configuration/configuring-onelogin-external-idp/zidentity-oidc-configuration-pingone.png)
[]
![A screenshot of Provisioning tab in IdP configuration](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-provisioning-nogroups-full.png)
[]![A screenshot highlighting the SCIM Enpoint URL in ZIdentity Admin Portal](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-scim-endpoint-url-oin-okta.png)
[]![A screenshot of Attribute Mapping tab in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-attribute-mapping-tab-pingone_0.png)
[]![A screenshot capturing the option to add a new attribute mapping](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-attribute-mapping-configuration.png)
[]
[]![A screen recording showing options to configure an expression for an attribute in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-attribute-mapping.gif)
[]![A screenshot showing the SCIM Endpoint URL in ZIdentity Admin Portal](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-scim-endpoint-url-oin-okta_0.png)
[]![A screenshot capturing the attribues mapped in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-all-attributes-mapped-pingone.png)
[]![A screenshot capturing the option to add a new connection in PingOne Provisioning page](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-add-new-connection.png)
[]![A sceenshot highlighting the option select Identity Store for a new connection in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-select-identity.png)
[]![A screenshot of Create a New Connection Drawer](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/scim-search-and-select.png)
[]![A screenshot of Create a New Connection Drawer](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/scim-name-description.png)
[]![A screenshot of Create a New Connection Drawer in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-base-url-scim.png)
[]![A screenshot of Create a New Connection drawer in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-last-step-pingone.png)
[]![A screenshot higlighting the Connection drawer in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-enable-connection.png)
[]![A screenshot captruing the option to a new connection in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-new-rule-option.png)
[]![A screenshot fo create a new rule drawer](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-new-rule-window.png)
[]![A screenshot highlighting the target connecion in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-select-target.png)
[]![A screenshot highlighting the option to configure user filter in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-edit-user-filter.png)
[]![A screenshot capturing the user filters applied for a rule in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-user-filter.png)
[]![A screenshot of attribute mapping for a rule in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-rule-attribute-mapping.png)
[]![A screenshot highlighting the options to add groups fro provisioning in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-group-provisioning.png)
[]![A screenshot highlighting the groups selected for provisioning](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidenity-adding-groups.png)
[]![A screenshot highlighting the option to enable a rule in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-rule-enabled.png)
[]
![Click the link in the banner to go to Experience Center](/downloads/unified/administration/zidentity/idp-configuration/external-idp-configuration/configuring-pingone-external-idp/zid-landing-page-withbanner.png)
[]![MFA Policies page with the option to add a new policy highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-pingone-add-mfa-policy.png)
[]![Configuring an MFA policy in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-mfa-add-policy.jpeg)
[]![Configuring authentication methods in PingOne for MFA policies](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-select-allowed-authentication-methods.jpeg)
[]![Authentication policies page with the option to add a new policy highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-add-authentication-policy.jpeg)
[]![Configuring a single step authentication in PingOne](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-add-policy-authentication-pingone.jpeg)
[]![Option to edit policies associated with a PingOne application](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-edit-policies-in-the-application.png)
[]![List of policies added to the PingOne application](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-app-pingone-list-policies.png)
[]![Mapping authentication levels with ACR values in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-pingone-external-idp/zidentity-al-acr-mapping-pingone.png)