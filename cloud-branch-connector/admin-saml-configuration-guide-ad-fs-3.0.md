# Admin SAML Configuration Guide for AD FS 3.0
Source: https://help.zscaler.com/zdx/admin-saml-configuration-guide-ad-fs-3.0
PDF: https://help.zscaler.com/pdf/com/en/1420001.pdf

This guide illustrates how to configure a Windows Server 2012 R2 running Active Directory Federation Services (AD FS) 3.0 as the identity provider (IdP) for the Zscaler service and use [SAML single sign-on (SSO) for your organization's admins](/zdx/configuring-saml-zdx-admins/). Refer to the [Microsoft AD FS documentation](https://docs.microsoft.com/en-us/windows-server/identity/active-directory-federation-services) for the Windows Server 2012 R2 steps.
Prerequisites
Ensure you have the following before configuring AD FS:
- [AD FS account with admin privileges](https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/overview/ad-fs-requirements#permissions-requirements)
- [ZDX Admin accounts](/zdx/adding-zdx-admins) created for your organization's admins
- [Zscaler Admin XML Metadata](#ZDX-XML-Metadata)
Configuring Admin SAML SSO in AD FS
To configure AD FS as the IdP for the Zscaler service and use SAML SSO for admins:
- [Add a Relying Party Trust and Claim Rule.](#add-trust-claim-rule)
- [Export the IdP SAML SSL Certificate.](#export-cert)
- [Configure SAML Admin SSO in the ZDX Admin Portal.](/zdx/configuring-saml-zdx-admins#configuring-saml-admins)
- [Add the Relay State URL as required.](#RelayState)
**Verifying ZDX Admin Portal Access via SSO**
To verify the ZDX Admin Portal access via SSO:
- On a Windows device, browse to the following URL:
https://<AD FS Server>/adfs/ls/idpinitiatedSignOn.aspx
The <AD FS Server> depends on your AD FS server name. For example, if your AD FS server name is adfs.safemarch.com, browse and select https://adfs.safemarch.com/adfs/ls/idpinitiatedSignOn.aspx.
- Verify that you are directed to the AD FS login screen.
- Log in using your SAML admin login credentials to authenticate.
[]In AD FS, a relying party is a Federation Service or application that requests and processes claims from a claims provider in a particular transaction. Configure the Zscaler service as a relying party trust. After, add a claim rule, which is a statement that provides information about a user. It is used by the Zscaler service to determine if the user is allowed access.
To add Zscaler as a relying party trust and to add a claim rule:
- On the **Server Manager**, go to **Tools** >** AD FS Management**.
- In the left navigation panel of the **AD FS** window, go to **AD FS** >**Trust Relationships** > **Relying Party Trusts**.
[See image.](#findRelyingPartyTrusts)
- In the **Actions** panel on the right, under **Relying Party Trusts**, click **Add Relying Party Trust…**.
[See image.](#addRelyingPartyTrusts)
- When the **Add Relying Party Trust** **Wizard** appears, click **Start**. The wizard sections are listed on the left pane.
[See image.](#startWizard)
- In **Select Data Source**:
- Select **Import data about the relying party from a file**.
- Under **Federation metadata file location**, click **Browse**.
- **Open** your downloaded Admin SP XML metadata file from the prerequisites.
When the location of the Admin SP XML metadata file displays, click **Next**.
[See image.](#selectImportDataFile)
- In **Specify Display Name** , enter a display name for the Zscaler service, such as Zscaler Admin SAML.
Click **Next**.
[See image.](#relyingPartyEnterDisplayName)
- In **Configure Multi-factor Authentication Now?** ,** **select **I do not want to configure multi-factor authentication settings for this relying party trust at this time**.
Click **Next**.
[See image.](#selectMFASetting)
- In **Choose Issuance Authorization Rules** , select **Permit all users to access this relying party**.
Click **Next**.
[See image.](#selectIssuanceAuthorizationRules)
- In **Ready to Add Trust** , review your settings.
Click **Next**.
[See image.](#readyToAddTrust)
- In **Finish** , select **Open the** **Edit Claim Rules dialog for this relying party trust when the wizard closes**.
Click **Finish** to add the relying party trust to the database.
[See image.](#selectEditClaimRulesClose)
- When the **Edit Claim Rules** window appears, click **Add Rule**.
[See image.](#issuanceTransformRules)
- In **Choose Rule Type** of the **Add Transform Claim Rule** **Wizard**, choose **Send LDAP Attributes as Claims** from the drop-down menu.
Click **Next**.
[See image.](#configureClaimRules)
- In **Configure Claim Rule**:
- Enter a name for the claim rule, such as `ZDX claims`.
- Choose **Active Directory** from the **Attribute Store** drop-down menu.
- Map the LDAP attributes that represent the admin's login name, full name, department, group to fields in the outgoing claim type.
- Map the LDAP attribute for login name to an outgoing claim type.
- In the **LDAP Attribute** column, choose **User-Principal-Name**.
- In the **Outgoing Claim Type** column, choose **Name ID**. The email address is sent as the Name ID.
- Map the LDAP attribute for full name to an outgoing claim type.
- In the **LDAP Attribute **column, choose **Display-Name**.
- In the **Outgoing Claim ****Type **column, enter **displayName**.
Click **Finish** to add the claim rule.
[See image.](#claimRuleName)
- When the **Edit Claim Rules** window displays the newly added claim rule in the list, click **Apply**.
Click **OK**.
[See image.](#applyZDXClaims)
[]![Find Relying Trust Folder](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-add-relying-party-trusts-folder.png)
[]![Select Add Relying Party Trust](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-add-relying-party-trusts-folder-select-add-relying-party-trust.png)
[]![Start Add Relying Party Trust Wizard](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-add-relying-party-trust-wizard-start.png)
[]![Import Admin SAML Metadata](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-add-relying-party-trust-wizard-import-data.png?1666846718)
[]![Enter your display name](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-add-relying-party-trust-wizard-name.png)
[]![Select I do not want to configure Multi-factor Authentication settings.](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-add-relying-party-trust-wizard-configure-mfa.png)
[]![​​​​Select Issuance Authorization Rules](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-add-relying-party-trust-wizard-issuance-authorization-rules.png)
[]![Ready to Add Trust](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-add-relying-party-trust-wizard-ready-to-add-trust.png)
[]![Select Edit Claim Rules](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-add-relying-party-trust-wizard-finish.png)
[]![Issuance Transform Rules - Add Rule](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-Edit-Claim-Rules.png)
[]![Configure Claim Rules - LDAP](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-Add-Claim-Rule-LDAP.png)
[]![Fill out the Claim Rule Name](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-Add-Claim-Rule-Configure-Claim-Rule.png)
[]![Apply ZDX Claims](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-Add-Claim-Rule-Configure-Claim-Rule-Apply.png)
[]To export the AD FS token-signing certificate that you will upload to the Zscaler service:
- In the left navigation panel of the **AD FS** window, go to **Service** > **Certificates**.
[See image.](#selectCertificates)
- In the **Certificates** panel, right-click the certificate under **Token-signing**, and click **View Certificate...**.
[See image.](#viewCertificate)
- In the **Certificate** window, select the **Details** tab, and click **Copy to File…**.
[See image.](#copyToFile)
- When the** Certificate Export** **Wizard** appears, click **Next**.
[See image.](#certificateExportWizard)
- In **Export File Format**, select **Base-64 encoded X.509 (.CER)**.
Click **Next**.
[See image.](#selectCertificateFormat)
- In **File to Export**, click **Browse** to navigate to the location where you want to export the certificate, enter a certificate name. In this example, the certificate is called `adfsadmin`.
Click **Next**.
[See image.](#folderToExport)
- When the export is complete, click **Finish**.
[See image.](#completeCertificateExportWizard)
- Click **OK** to close the **Certificate** window.
- Go to the exported certificate, and ensure the following:
- The certificate file name has a .pem extension. (For example, rename `adfsadmin.cer` to `adfsadmin.pem`.) The Zscaler service accepts certificates with the .pem extension only.
- The file name contains one dot (".") only.
By default, Windows hides extensions for known file types.
- [Change the Windows Folder Properties to View and Edit Extensions](#view-extensions-windows)
Upload this IdP SAML SSL certificate to the ZDX Admin Portal in step 3.
- []Start Windows **Control Panel**.
- Go to **Appearance** > **Folder Options** > **View**.
- When the **Folder Option** window appears, deselect **Hide extensions for known file types** to view extensions.
- Rename the extension of the exported certificate.
[]![Select Certificates](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-Certificates.png)
[]![View Certificate](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-Certificates-View.png)
[]![Certificate - Details - Copy to File](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-Certificates-Copy-To-File.png)
[]![Certificate Export Wizard](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-Certificates-Next.png)
[]![Select Certificate Format](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-Certificates-Base-64.png)
[]![Browse Folder to export](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-Certificates-Browse.png)
[]![Complete Certificate Export Wizard](/downloads/zdx/administration/admin-saml-configuration-guide-ad-fs-30/ZDX-AD-FS-Certificates-Finish.png)
[]The relay state is required if you have a domain defined on multiple ZIA clouds, enter the ZIA cloud name that is associated with ZDX in the Relay State field (for example, `zscalertwo.net`) for each application. To learn more, see [Microsoft's AD FS 2.0 RelayState](https://techcommunity.microsoft.com/t5/ask-the-directory-services-team/ad-fs-2-0-relaystate/ba-p/400145).
[]
[]To download the XML Metadata from ZDX:
- Sign in to ZDX as an administrator.
- Go to **Administration** > **Administrator Management** > **Administrator Management**.
- Click **Download**.
[See image.](#Download-XML-Metadata)
[]![Download XML Metadata.](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-ZDX-SAML%20Authentication.png)
To learn more, see [Configuring SAML for ZDX Admins](/zdx/configuring-saml-zdx-admins).