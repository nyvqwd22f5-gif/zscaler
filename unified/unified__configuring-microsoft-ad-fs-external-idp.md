# Configuring Microsoft AD FS as an External IdP
Source: https://help.zscaler.com/unified/configuring-microsoft-ad-fs-external-idp
PDF: https://help.zscaler.com/pdf/com/en/1505471.pdf

This guide provides information on how to configure Microsoft Active Directory Federated Services (AD FS) as the SAML Identity Provider (IdP) for ZIdentity to facilitate single sign-on (SSO) to various Zscaler services for admin access management.
If you want to leverage [step-up authentication](/unified/understanding-step-up-authentication), it is recommended to use OIDC-based integrations as most IdPs only support step-up authentication with the OIDC protocol.
Prerequisites
- A Microsoft Windows Server with the following components installed and connected:
- Active Directory
- AD FS
- An administrator account for the Window Server
- A ZIdentity account with an admin role that allows you to add an IdP configuration
IdP-Initiated SSO for ZIdentity Tenants Enabled with Experience Center
During the IdP-initiated SSO for ZIdentity, tenants using OIDC or SAML protocols are redirected as follows:
- [OIDC Protocol](#OIDC-protocol-redirection)
- [SAML Protocol](#SAML-protocol-redirection)
To change the default redirection, contact [Zscaler Support](/contact-support).
Configuring Microsoft AD FS as IdP for ZIdentity
- [1. Set up AD FS as an IdP for ZIdentity.](#ad-fs-as-idp)
- [2. Configure Relying Party Trust in AD FS.](#relying-party-trust-ad-fs)
- [3. Provision users for ZIdentity.](#ad-fs-user-provisioning)
[]
All admins authenticating using the SAML protocol for ZIdentity and IdP integrations are redirected to Experience Center. However, if the `zidServiceId` attribute is configured in the IdP within the ZIdentity tenant, then the admins are redirected to the ZIdentity Admin Portal instead of Experience Center.
[]
ZIdentity tenants that are enabled with Experience Center at the time of tenant creation and admins using OIDC protocol for ZIdentity and IdP integrations are redirected to the Experience Center.
ZIdentity tenants that are not enabled with Experience Center at the time of tenant creation and admins using OIDC protocol for ZIdentity and IdP integrations are redirected to the ZIdentity Admin Portal. They can click the Experience Center link and go to the Experience Center from the [ZIdentity Landing page](/zidentity/accessing-and-navigating-zidentity-landing-page).
[See image.](#ec-zidlandingpage)
If you want to change this default behavior and have users redirected to the Experience Center, raise a Support ticket with the ticket type set to **Provisioning**.
- [][a. Obtain Federation Metadata from AD FS.](#metadata-from-ad-fs)
- [b. Configure AD FS as an IdP in the Admin Portal](#ad-fs-idp-zslogin).
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
- []Log in to the Admin Portal.
- Go to **Administration > Identity > ZIdentity > External Identities**.
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
**Login ID Attribute**: Enter an attribute whose value must be used as the login ID. This attribute must exist in the token received from the IdP. By default, the `NameID` attribute is populated in this field when the **SAML** option is selected in the **Protocol** field. You can use any attribute that is present in the SAML token, provided its value is in the email address format (e.g., <user_name>@domain.com>).
- Ensure that the domain part of the email addresses received in the SAML token matches with one of the domains configured in ZIdentity.
- Ensure that the attribute you enter matches exactly with the attribute in the SAML token.
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
In the **Select Data Source **step, select the **Import data about the relying party from a file** option, and enter the location of the SP Metadata XML file downloaded from the Admin Portal in the [previous step](#ad-fs-idp-zslogin).
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
- []In the Admin Portal, go to **Administration > Identity > ZIdentity > External Identities**.
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
- If you want to map custom user attributes (e.g., Department), make sure they are already configured in the Admin Portal. To learn more about configuring custom user attributes, see [Adding User Attributes](/unified/adding-user-attributes).
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
- Map the ZIdentity user attributes including the custom attributes with the appropriate AD FS attributes as configured in the Admin Portal in the [previous step](#ad-fs-user-provisioning).
- Click **OK**.
[See image.](#rule-map-adfs)
The claim rule is added.
- Click **OK**.
The AD FS users are provisioned for ZIdentity.
[]![A screenshot capturing the Server Manager with the Metadata URL information selected](/downloads/zslogin/administration/authentication/third-party%20saml/zslogin-adfs-metadata-path.png)
[]![A screenshot highlighting the option to add Relying Party Trust in the Server Manager](/downloads/zslogin/administration/authentication/third-party%20saml/add-rpt-adfs.png)
[]![A screenshot capturing the Welcome Step in Relying Party Trust wizard](/downloads/zslogin/administration/authentication/third-party%20saml/wizard-adfs-welcome.png)
[]![A screenshot capturing the Select Data Source step in the Relying Party Trust wizard](/downloads/zslogin/administration/authentication/third-party%20saml/zslogin-ad-fs-select-data-source.png)
[]![A screenshot capturing the Specify Display Name step in the Relying Party Trust wizard](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zslogin-sepecify-name-wizard.png)
[]![A screenshot capturing the final step in the Relying Party Trust wizard](/downloads/zslogin/administration/authentication/third-party%20saml/zslogin-finish-adfs-wizard.png)
[]![A screenshot capturing the Add Rule option to Claim in Relying Party Trust](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zslogin-claim-edit-adfs.png)
[]![A screenshot capturing the Claim Rule wizard](/downloads/zslogin/administration/authentication/third-party%20saml/zslogin-adfs-add-rule.png)
[]![A screenshot capturing the Edit Claim Rule window](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zslogin-rule-map.png)
[]![Configuring basic information of primary IdP in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/Basic-tab.png)
[]![IdP Metadata in IdP Conifguration Window](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-upload-metadata-adfs_0.png)
[]![SP Metadata in IdP Configuration Window](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-adfs-upload-sp-metadata.png)
[]![Advanced Tab in IdP Configuration Window](/downloads/zslogin/authentication/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-saml-signing-adfs.png)
[]![A SAML assertion sample with blurred sensitive information.](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-saml-assertion-sample.png)
[]![Provisioning Tab in IdP Configuration Window](/downloads/zidentity/integration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zidentity-adfs-jit.png)
[]![zid-landing-page-withbanner.png](/downloads/unified/administration/zidentity/idp-configuration/external-idp-configuration/configuring-microsoft-ad-fs-external-idp/zid-landing-page-withbanner.png)