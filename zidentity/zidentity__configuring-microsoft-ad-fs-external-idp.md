# Configuring Microsoft AD FS as an External IdP
Source: https://help.zscaler.com/zidentity/configuring-microsoft-ad-fs-external-idp
PDF: https://help.zscaler.com/pdf/com/en/1499366.pdf

This guide provides information on how to configure Microsoft Active Directory Federated Services (AD FS) as the Identity Provider (IdP) for ZIdentity to facilitate single sign-on (SSO) to various Zscaler services for admin access management.
If you want to leverage [step-up authentication](/zidentity/understanding-step-up-authentication), it is recommended to use OIDC-based integrations as most IdPs only support step-up authentication with the OIDC protocol.
- [OIDC-Based Authentication](#oidc-based-authentication-ad-fs)
- [SAML-Based Authentication](#saml-based-authentication-ad-fs)
- [IdP-Initiated SSO for ZIdentity Tenants Enabled with Experience Center](#idp-initiated-sso-experience-center-case)
[]Prerequisites
Before you configure AD FS as an external IdP, ensure that you have:
- A Microsoft Windows Server with the following components installed and connected:
- Active Directory
- AD FS
- An administrator account for the Windows Server.
- A ZIdentity account with an admin role that allows you to add an IdP configuration.
Configuring Microsoft AD FS as OP for ZIdentity
To set up AD FS as an OP for ZIdentity:
- [1. Set up AD FS as an OP in the ZIdentity Admin Portal.](#set-up-ad-fs-as-op-zidentity)
- [2. Configure OIDC-based integration in the AD FS Management Console.](#adfs-oidc-set-up-in-adfs)
- [3. Provision users for ZIdentity.](#adfs-oidc-provision-users)
- [4. (Optional) Enable step-up authentication.](#adfs-oidc-step-up-authentication)
- []Log in to the ZIdentity Admin Portal.
- Go to **Integration **> **External Identities**.
-
Click **Add Primary IdP **(or **Add Secondary IdP**).
The **Add Primary Identity Provider **or **Add Secondary Identity Provider **window appears.
- On the **Basic **tab:
-
Under the **General **section:
- **Name**: Enter a name for the IdP.
- **Identity Vendor**: Select **Active Directory Federation Service **from the drop-down menu.
- **Domain**: Select the domain for which the IdP is responsible for authenticating the users. This allows the Zscaler service to display the correct IdP to authenticate an incoming user.
- **Protocol**: Select **OIDC**.
- **Status**: Select **Enabled**.
-
**Login ID Attribute**: Enter an attribute whose value must be used as the login ID. This attribute must exist in the tokens received from the IdP. By default, the `preferred_username` attribute is populated in this field when the OIDC option is selected in the **Protocol** field. You can use any attribute that is present in the [ID token](https://openid.net/specs/openid-connect-core-1_0.html#IDToken) or the response of the [UserInfo endpoint](https://openid.net/specs/openid-connect-core-1_0.html#UserInfo), provided its value is in the email address format (e.g., <user_name>@domain.com>).
- Ensure that the domain part of the email addresses received in the ID tokens match with one of the domains configured in ZIdentity.
- Ensure that the attribute you enter matches exactly with the attribute received in the ID token or the UserInfo endpoint.
-
**Enforce Zscaler Admin MFA**: Enable this option to ensure that admins using an external IdP authenticate with the multi-factor authentication (MFA) process in ZIdentity, irrespective of whether MFA is configured on the external IdP.
An email is sent to all super admins in ZIdentity when the Enforce Zscaler Admin MFA option is disabled.
[See image.](#basic-oidc-adfs-tab)
-
Under the **OIDC Configuration **section:
- **Input Method**: Select **Metadata URL**.
-
**Metadata URL**: Enter the AD FS server's OIDC well-known URL and click **Fetch**.
- The format for the OIDC well-known URL is `https://<host>/adfs/.well-known/openid-configuration`. An example URL is `https://myadfs.example.com/adfs/.well-known/openid-configuration`.
-
Obtain the metadata path from the AD FS Management Console: In the **Server Manager**, go to **AD FS **> **Tools **> **AD FS Management**, then **Service **> **Endpoints**, and locate the OpenID Connect metadata URL path.
[See image.](#adfs-path-oidc)
-
**Redirect URI**: Copy this value because it is used in a subsequent step.
If you are configuring AD FS as your secondary IDP, the final segment in the **Redirect URI** is required for configuring **Initiate Login URI** in the AD FS Management Console.
- **Client ID**: Enter a random value. The actual client ID is generated while configuring an application for ZIdentity in the AD FS Management Console in a subsequent step. This random value entered in the field is replaced later with the actual client ID.
- **Client Secret**: Enter a random value. This value is manually overridden in a subsequent step. The actual client secret is generated while configuring a client for ZIdentity in the AD FS Management Console in a subsequent step. This random value entered in the field is replaced later with the actual client secret.
- **Requested Scopes**: Add the required scopes. By default, when the OIDC protocol is selected, the `openid`, `email`, and `profile `scopes are added.
[See image.](#oidc-configuration-adfs)
- Click **Save**.
- []Log in to the Windows Server as an administrator.
- Open **Server Manager **and go to **AD** **FS **> **Tools **> **AD FS Management**.
-
In the AD FS window, go to **AD FS **> **Application Groups**, and click** Add Application Group...**
[See image.](#add-app-group-oidc)
The **Add Application Group Wizard** window appears.
- In the **Add Application Group Wizard **window:
- **Name**: Enter a name for the application.
- **Description**: Enter a description for the application.
-
**Template**: Select **Server application**.
[See image.](#add-app-group-step-1)
-
In the **Server application **step:
- **Client Identifier**: Copy this value because it is used in a subsequent step.
- **Redirect URI**: Enter the **Redirect URI** copied from the ZIdentity Admin Portal in a previous step, and click **Add**.
- Click **Next**.
[See image.](#add-app-group-step-2)
-
In the **Configure Application Credentials **step:
- **Generate a** **shared secret**: Select this option to generate a secret and copy the value as it is used in a subsequent step.
- Click **Next**.
[See image.](#add-app-group-step-3)
-
In the **Summary **step, verify the configuration details, and click **Next**.
[See image.](#add-app-group-step-4)
-
In the **Complete **step, click **Close **to complete the application registration.
[See image.](#add-app-group-step-5)
- Open the created application group.
-
In the **<application group_name> Properties** window, click **Add application...**
[See image.](#web-api-add-oidc)
- In the **Add a new application to <application_group_name>** window:
-
Go to the **Template **section, select **Web API **and click **Next**.
[See image.](#web-api-step1)
-
In the **Configure Web API **step, edit name and add identifier, and click **Next**.
[See image.](#web-api-oidc-step2)
-
In the **Apply Access Control Policy **step, select **Permit everyone**, and click **Next**.
[See image.](#web-api-oidc-step3)
-
In the **Configure** **Application Permissions **step:
- **Client application (caller)**: Ensure that the server application created for ZIdentity is selected.
- **Permitted scopes**: Select `allatclaims`, `email`, `openid`, and `profile`.
- Click **Next**.
[See image.](#web-api-oidc-step4)
-
In the **Summary **step, verify the details, and click **Next**.
[See image.](#web-api-oidc-step5)
-
In the **Complete **step, click **Close **to complete Web API configuration.
[See image.](#web-api-oidc-step6)
-
In the **<application group_name> Properties** window, select the Web API created for ZIdentity, and click **Edit**.
[See image.](#edit-webi-api-button-oidc)
-
In the **<web_API_name> Properties** window, go to **Issuance Transform Rules **and click **Add Rule**.
[See image.](#add-rule-button-web-api)
- In the **Add Transform Claim Rule Wizard** window:
-
**Claim rule template:** Select **LDAP Attributes as Claims**.
[See image.](#rule-wizard-oidc-step1)
- Click **Next**.
-
In the **Configure Claim Rule **step:
- **Claim rule** **name**: Enter a name for the rule.
- **Attribute store**: Select **Active Directory **from the drop-down menu.
- **Mapping of LDAP attributes to outgoing claim types**: Map the required attributes.
[See image.](#rule-wizard-oidc-step2)
- Click **Finish**.
-
In the **<application group_name> Properties** window, click **OK**.
[See image.](#okay-rule-oidc)
-
Go to **AD FS **> **Service **> **Relying Party Trusts**, click** Add Replying Party Trust...**
[See image.](#add-rpt-button)
- In the **Add Relying Party Trust Wizard **window:
-
Select **Claims aware **and click **Start**.
[See image.](#rpt-step1)
-
In the **Select Data Source **step, select **Enter the data about the relying party manually**.
[See image.](#rpt-step2)
-
In the **Specify Display Name** step:
- **Display Name**: Enter a name for the relying party trust.
- Click **Next**.
[See image.](#rpt-step3-oidc)
-
In the **Configure Identifiers **step:
-
**Relying party trust identifier**: Enter `https://<adfs_endpoint>/adfs/services/trust`
Replace `<adfs_endpoint>` with your AD FS endpoint which is publicly resolvable and has a valid certificate signed by a trusted CA.
- Click **Next**.
[See image.](#rpt-oidc-step4)
-
In the **Choose Access Control Policy **step:
- **Choose** **an access control policy**: Select **Permit everyone**.
- Click **Next**.
[See image.](#rpt-oidc-step5)
- Complete the subsequent steps.
- In the ZIdentity Admin Portal, go to **Integrations **> **External Identities**.
- Locate the IdP created for ZIdentity on the **Primary Identity Provider** (or **Secondary Identity Provider**) table, and click the **Edit **icon.
- In the **Edit Primary IdP **(or **Edit Secondary IdP**) window:
- On the **Basic **tab, in the** OIDC Configuration** section:
- **Client ID**: Override the previously configured random value with the actual client ID of the application created in the AD FS Management Console.
-
**Client Secret**: Override the previously configured random value with the actual client secret of the application created in the AD FS Management Console.
[See image.](#client-credentails-ad-fs)
- Click **Update**.
- []In the ZIdentity Admin Portal, go to **Integration **> **External Identities**.
- Locate the IdP entry created for AD FS under the **Primary Identity Provider **(or **Secondary Identity Providers**) tab and click the **Edit **icon.
-
In the **Edit Primary IdP **(or **Edit Secondary IdP**) window:
- Go to the **Provisioning **tab and select **Enable Just-in-time (JIT) Provisioning**.
- **Just-in-time User Group Attribute**: Enter the claim name created for group information retrieval (i.e., Groups). This retrieves the group membership information of the users from AD FS.
-
Map the `Primary Email `User Attribute with the `email` Just-in-time User Attribute.
The mapping of the `Primary Email` attribute is mandatory as it is required for functionalities, such as password resetting and multi-factor authentication.
- Map other ZIdentity user attributes with the appropriate AD FS attributes as necessary. By default, the following attributes in ID tokens are mapped with the corresponding user attributes in ZIdentity:
| Attribute in ID Tokens | Default ZIdentity User Attributes |
| ---------------------- | --------------------------------- |
| given_name | First Name |
| family_name | Last Name |
| name | Display Name |
- If the external IdP is configured to send different attributes for `First Name`, `Last Name`, or `Display Nam`e, then you must map those attributes. For example, if the ID token from the external IdP includes `Surname` instead of `family_name`, then you must map it with the `Last Name` user attribute in ZIdentity. [See image.](#sample-token)
- While mapping attributes, ensure that the attributes that you enter in the **Just-in-time Attribute** field match exactly with the attributes that would be received in the ID tokens.
[See image.](#oidc-users-provision)
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
[]![Configuring the basic details for AD FS integration in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-adfs-basic.jpg)
[]![Endpoints section in AD FS Management Console showing the OIDC discovery path](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-ad-fs-path.jpg)
[]![Configuring OIDC details in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-pingfed-oidc-configuration_0.png)
[]![Application Groups in AD FS Management Console showing the option to add group](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-adfs-add-application-group.jpg)
[]![Configuring an application group in AD FS](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-add-application-group-step1.jpg)
[]![Configuring server application details for an application group in AD FS](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-add-application-group-step-2.jpg)
[]![Generate a shared secret for an application group in AD FS](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-add-application-group-step2.jpg)
[]![Reviewing the summary of a server application configuration in AD FS](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-add-application-group-step3.jpg)
[]![Completing the application group configuration in AD FS](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-add-application-group-step5.jpg)
[]![Option to add an application within a application group in AD FS](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-add-application-in-properties.jpg)
[]![Configuring a Web API for ZIdentity in AD FS](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-add-web-api-step1.jpg)
[]![Configuring the basic details of the Web API in AD FS](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-add-web-api-step2.jpg)
[]![Configuring an access policy for the Web API](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-add-web-api-step3.jpg)
[]![Configuring permissions for the Web APi](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-add-web-api-step4.jpg)
[]![Reviewing the summary of the Web API in AD FS](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-add-web-step5.jpg)
[]![Completing the Web API configuration in AD FS](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-add-web-api-step6.jpg)
[]![Option to edit an application in application group](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-web-api-edit.jpg)
[]![Issuance transform rules for Web API showing the option add a rule](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-issuance-transform-rules.jpg)
[]![Configuring a template for the claim rule in AD FS](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-rule-step1.jpg)
[]![Configuring the claim rule in AD FS](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-rule-step2_0.jpg)
[]![Web API properties showing option confirm the changes](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-rule-okay.jpg)
[]![Relying Party Trusts in AD FS showing the option to add a relying party trust](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-add-relying-parry-trust-button.jpg)
[]![Configuring a relying party trust in ADFS ](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-rpt-step1.jpg)
[]![Selecting a source data for the relying party trust](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-step2-rpt.jpg)
[]![Configuring a display name for relying](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-rpt-step3.jpg)
[]![Configuring identifiers for a relying party trust](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-rpt-step6.jpg)
[]![Configuring relying party trust access control policy](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-rpt-step7.jpg)
[]![Overriding the client ID and secret in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-identity-ad-fs.png)
[]![Provisioning users via JIT in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-jit-oin-okta.png)
[]![A sample OIDC ID token](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-id-token-sample%20(3).png)
[]Prerequisites
- A Microsoft Windows Server with the following components installed and connected:
- Active Directory
- AD FS
- An administrator account for the Windows Server
- A ZIdentity account with an admin role that allows you to add an IdP configuration
Configuring Microsoft AD FS as IdP for ZIdentity
- [1. Set up AD FS as an IdP for ZIdentity.](#ad-fs-as-idp)
- [2. Configure Relying Party Trust in AD FS.](#relying-party-trust-ad-fs)
- [3. Provision users for ZIdentity.](#ad-fs-user-provisioning)
- [][a. Obtain Federation Metadata from AD FS.](#metadata-from-ad-fs)
- [b. Configure AD FS as an IdP in the ZIdentity Admin Portal.](#ad-fs-idp-zslogin)
- []Log in to the Windows Server as an administrator.
- Open the **Server Manager **and go to **AD FS **> **Tools **> **AD FS Management**.
-
Go to **Services **> **Endpoints **and locate the **Metadata URL Path**. The typical URL path is `/FederationMetadata/2007-06/FederationMetadata.xml`.
[See image.](#url-path-adfs)
-
To download the metadata, enter the following URL in the browser:
`https://<computer-name.domain><metadata_URL_path>`
For example, if the computer name is `zsad` and the domain name is `zsidentity`, the URL to download the metadata is `https://zsad.zsidentity.com/FederationMetadata/2007-06/FederationMetadata.xml`.
The federation metadata is downloaded as an XML file.
- []Log in to the ZIdentity Admin Portal.
- Go to **Integration **> **External Identities**.
-
Click **Add Primary IdP **(or **Add Secondary IdP**).
The **Add Primary Identity Provider **(or **Add Secondary Identity Provider**)** **window appears.
-
On the **Basic **tab:
-
Under the **General **section:
- **Name**: Enter a name for the IdP.
- **Identity Vendor**: Select **Active Directory Federated Service **from the drop-down menu.
- **Domain**: Select the domain for which the IdP is responsible for authenticating the users. This allows the Zscaler service to display the correct IdP to authenticate an incoming user.
- **Protocol**: Select **SAML**.
- **Status**: Select **Enabled**.
-
**Login ID Attribute**: Enter an attribute whose value must be used as the login ID. This attribute must exist in the token received from the IdP. By default, the `NameID` attribute is populated in this field when the **SAML** option is selected in the **Protocol** field. You can use any attribute that is present in the SAML assertion, provided its value is in the email address format (e.g., <user_name>@domain.com>).
- Ensure that the domain part of the email addresses received in the SAML assertion matches with one of the domains configured in ZIdentity.
- Ensure that the attribute you enter matches exactly with the attribute received in the SAML assertion.
-
**Enforce Zscaler Admin MFA**: Enable this option to ensure that admins using an external IdP authenticate with the multi-factor authentication (MFA) process in ZIdentity, irrespective of whether MFA is configured on the external IdP.
An email is sent to all super admins in ZIdentity when the **Enforce Zscaler Admin MFA **option is disabled.
[See image.](#general-zslogin)
-
Under the **SAML Configuration **section:
- Select **Upload Metadata **as the **Input Method**.
- Click **Upload IdP Metadata**.
- Select the AD FS federation metadata file downloaded in the [previous step](#metadata-from-ad-fs).
- Click **Save**.
[See image.](#upload-metadate-saml)
The AD FS IdP configuration is saved.
- Locate the IdP configuration created for AD FS and click the **Edit **icon.
-
Under the **SAML Configuration **section, locate **SP Metadata**, and click **Download SP Metadata**.
[See image.](#download-sp-metadata)
The SP Metadata file is downloaded as an XML file.
-
Go to the **Advanced **tab and enable **SAML Request Signing**.
[See image.](#advanced-tab-zslogin)
- Click **Update**.
- []On the Windows Server, open the **Server Manager**.
- Go to **AD FS **> **Tools **> **AD FS Management**.
-
Under **AD FS > Relying Party Trusts**, click **Add Relying Party Trust...**.
[See image.](#add-ad-fs-rpt)
The **Add Relying Party Trust Wizard** window appears.
-
In the **Add Relying Party Trust Wizard **window**:**
-
Select **Claims aware **and click **Start**.
[See image.](#add-rpt-start)
-
In the **Select Data Source **step, select the **Import data about the relying party from a file** option, and enter the location of the SP Metadata XML file downloaded from the ZIdentity Admin Portal in the [previous step](#ad-fs-idp-zslogin).
[See image.](#add-rpt-datasource)
- Click **Next**.
-
In the **Specify Display Name **step, enter a name for the relying party (i.e., ZIdentity).
[See image.](#add-rpt-specify-name)
- Click **Next**.
-
Navigate to the **Finish **step and click **Close**.
[See image.](#finish-wizard-rpt)
The ZIdentity is added as a Relying Party Trust in AD FS.
- []In the ZIdentity Admin Portal, go to **Integration **> **External Identities**.
- Locate the IdP entry created for AD FS under the **Primary Identity Provider **(or **Secondary Identity Providers**) tab and click the **Edit **icon.
-
In the **Edit Primary IdP **(or **Edit Secondary IdP**) window:
- Go to the **Provisioning **tab.
- Select **Enable Just-in-time (JIT) Provisioning**.
- **Just-in-time User Group Attribute**: Enter the claim name created for group information retrieval (i.e., Groups). This retrieves the group membership information of the users from AD FS.
-
Map the ZIdentity user attributes including the custom attributes with the appropriate AD FS attributes as necessary. The mapping of the `Primary Email` attribute is mandatory as it is required for functionalities, such as password resetting and multi-factor authentication. By default, the following attributes in SAML assertions are mapped with the corresponding user attributes in ZIdentity.
| Attribute in SAML Assertions | Default ZIdentity User Attributes |
| ---------------------------- | --------------------------------- |
| firstName | First Name |
| lastName | Last Name |
| displayName | Display Name |
- If the external IdP is configured to send different attributes for `First Name`, `Last Name`, or `Display Name`, then you must map those attributes. For example, if the SAML assertion from the external IdP includes `Surname` instead of `lastName`, then you must map it with the `Last Name` user attribute in ZIdentity.
- If you want to map custom user attributes (e.g., Department), make sure they are already configured in the ZIdentity Admin Portal. To learn more about configuring custom user attributes, see [Adding User Attributes](/zidentity/adding-user-attributes).
-
While mapping attributes, ensure that the attributes that you enter in the **Just-in-time Attribute** field match exactly with the attributes that would be received in the SAML assertions.
[See image.](#sample-saml-assertion)
[See image.](#jit-ad-fs-enable)
- On the Windows Server, open **Server Manager**.
- Go to **AD FS **> **Tools **> **AD FS Management**.
- Under **AD FS**, click** Relying Party Trusts **and locate the relying party trust created for ZIdentity.
-
Right-click the ZIdentity relying party trust and select **Edit Claim Issuance Policy**.
The **Edit Claim Issuance Policy **window appears.
-
In the **Edit Claim Issuance Policy **window:
-
Click **Add Rule...**.
[See image.](#edit-claim-adfs)
The **Add Transform Claim Rule Wizard **window appears.
- In the **Add Transform Claim Rule Wizard **window:
-
In the **Choose Rule Type **step, select the **Send LDAP Attributes as Claims **option from the **Claim rule template **drop-down menu.
[See image.](#claim-rule-adfs)
-
Click **Next**.
The **Edit Rule **window appears.
-
In the **Edit Rule **window:
- **Claim rule name**: Enter a name for the claim rule.
- Map the ZIdentity user attributes including the custom attributes with the appropriate AD FS attributes as configured in the ZIdentity Admin Portal in the [previous step](#ad-fs-user-provisioning).
- Click **OK**.
[See image.](#rule-map-adfs)
The claim rule is added.
- Click **OK**.
The AD FS users are provisioned for ZIdentity.
[]During the IdP-initiated SSO for ZIdentity, tenants using OIDC or SAML protocols are redirected as follows:
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
[]
![Server Manager with the Metadata URL information selected](/downloads/zslogin/administration/authentication/third-party%20saml/zslogin-adfs-metadata-path.png)
[]
![Option to add Relying Party Trust in the Server Manager](/downloads/zslogin/administration/authentication/third-party%20saml/add-rpt-adfs.png)
[]
![Configuring the Welcome step in Relying Party Trust wizard](/downloads/zslogin/administration/authentication/third-party%20saml/wizard-adfs-welcome.png)
[]
![Configuring the Data Source in the Relying Party Trust wizard](/downloads/zslogin/administration/authentication/third-party%20saml/zslogin-ad-fs-select-data-source.png)
[]
![Configuring Display Name in the Relying Party Trust wizard](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zslogin-sepecify-name-wizard.png)
[]
![Configuring the final step in the Relying Party Trust wizard](/downloads/zslogin/administration/authentication/third-party%20saml/zslogin-finish-adfs-wizard.png)
[]
![Option to add a rule to specify claims for the relying party](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zslogin-claim-edit-adfs.png)
[]
![Choosing a rule type in Claim Rule wizard](/downloads/zslogin/administration/authentication/third-party%20saml/zslogin-adfs-add-rule.png)
[]
![Editing a claim rule](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zslogin-rule-map.png)
[]![Configuring basic information of primary IdP in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/Basic-tab.png)
[]![Configuring SAML in IdP Configuration window with the option to upload IdP metadata highlighted](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-upload-metadata-adfs_0.png)
[]![Configuring SAML in IdP Configuration window with the option to download SP metadata highlighted](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-adfs-upload-sp-metadata.png)
[]![Enabling SAML signing request in ZIdentity](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-saml-signing-adfs.png)
[]![A SAML assertion sample with blurred sensitive information.](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-saml-assertion-sample.png)
[]![Mapping JIT attributes in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-adfs-jit.png)
[]![ZIdentity Landing Page with highlighted banner at the top.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-configuring-okta-external-idp-doc-57200/zid-landing-page-1.png)