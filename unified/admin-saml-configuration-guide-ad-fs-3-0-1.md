# Admin SAML Configuration Guide for AD FS 3.0
Source: https://help.zscaler.com/unified/admin-saml-configuration-guide-ad-fs-3-0-1
PDF: https://help.zscaler.com/pdf/com/en/1516696.pdf

This guide demonstrates how to configure a Windows Server 2012 R2 running Active Directory Federation Services (AD FS) 3.0 as the identity provider (IdP) for the Zscaler service and use [SAML single sign-on (SSO) for your organization's admins](/unified/configuring-saml-admins-0). To learn more about the steps in the Windows Server 2012 R2, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/windows-server/identity/active-directory-federation-services).
Prerequisites
Ensure that you have the following before configuring AD FS:
- AD FS account with admin privileges
- [Admin accounts created for your organization's admins](/zidentity/adding-zidentity-admin-roles)
- Zscaler Admin XML Metadata
Configuring Admin SAML SSO in AD FS
To configure AD FS as the IdP for Zscaler Cloud & Branch Connector and use SAML SSO for admins:
- [Step 1: Add a Relying Party Trust and Claim Rule](#1RelyingPartyTrust)
- [Step 2: Export the IdP SAML SSL Certificate](#2IdPSAMLSSLCertificate)
- [Step 3: Configure SAML Admin SSO in the Admin Portal](/unified/configuring-saml-admins-0)
[]
In AD FS, a relying party is a Federation Service or application that requests and processes claims from a provider in a particular transaction. To add Cloud & Branch Connector as a relying party trust and to add a claim rule:
- In the left-side navigation of the **AD FS** window, expand the **AD FS** folder, then expand the **Trust Relationships** folder.
-
Right-click **Relying Party Trusts** and click **Add Relying Party Trust...** Alternatively, in the right-side navigation of the **AD FS** window, in **Relying Party Trusts**, click **Add Relying Party Trust...**
[See image.](#ADFS1B)
- In the **Add Relying Party Trust Wizard** window:
-
On the **Welcome** step, click **Start**.
[See image.](#ADFS1Ci)
-
On the **Select Data Source** step, select **Import data about the relying party from a file**, then click **Browse**.
[See image.](#ADFS1Cii)
- [Import your XML Metadata file](/unified/configuring-saml-admins-0), then click **Next**.
-
On the **Specify Display Name** step, under **Display name**, enter `Zscaler Cloud and Branch Connector Administrator Application`, then click **Next**.
[See image.](#ADFS1Civ)
-
On the **Configure Multi-factor Authentication Now?** step, select **I do not want to configure multi-factor authentication settings for this relying party trust at this time**, then click **Next**.
[See image.](#ADFS1Cv)
-
On the **Choose Issuance Authorization Rules** step, select **Permit all users to access this relying party**, then click **Next**.
[See image.](#ADFS1Cvi)
-
On the **Ready to Add Trust** step, review your settings, then click **Next**.
[See image.](#ADFS1Cvii)
-
On the **Finish** step, select the checkbox **Open the Edit Claim Rules dialog for this relying party trust when the wizard closes**, then click **Close**.
[See image.](#ADFS1Cviii)
-
In the **Edit Claim Rules for Zscaler Cloud and Branch Connector Administrator Application** window, click **Add Rule**. The **Add Transform Claim Rule Wizard** window appears.
[See image.](#ADFS1D)
- In the **Add Transform Claim Rule Wizard** window:
-
On the **Choose Rule Type** step, under **Claim rule template**, select **Send LDAP Attributes as Claims**, then click **Next**.
[See image.](#ADFS1Ei)
-
On the **Configure Claim Rule** step, under **Claim rule name**, enter `Zscaler Cloud and Branch Connector Administrator Application`.
[See image.](#ADFS1Eii)
-
Under **Attribute store**, select **Active Directory**.
[See image.](#ADFS1Eiii)
-
Under **Mapping of LDAP attributes to outgoing claim types**, in **LDAP Attribute**, select **User-Principal-Name**.
[See image.](#ADFS1Eiv)
-
Under **Outgoing Claim Type**, select **Name ID**, then click **Finish**.
[See image.](#ADFS1Ev)
-
When the **Edit Claim Rules for Zscaler Cloud and Branch Connector Administrator Application** window displays the newly added claim rule in the list, click **Apply**, then click **OK**.
[See image.](#ADFS1F)
[]
To export the AD FS token-signing certificate that uploads to Cloud & Branch Connector:
-
In the left-side navigation of the **AD FS** window, expand the **Service** folder, then click the **Certificates** folder.
[See image.](#ADFS2A)
-
In the **Certificates** panel, under **Token-signing**, right-click the primary certificate, then click **View Certificate...**
[See image.](#ADFS2B)
-
In the **Certificate** window, click the **Details** tab, and click **Copy to File…**
[See image.](#ADFS2C)
-
When the **Certificate Export Wizard** window appears, click **Next**.
[See image.](#ADFS2D)
-
In **Export File Format**, select **Base-64 encoded X.509 (.CER)**, then click **Next**.
[See image.](#ADFS2E)
-
In **File to Export**, under **File name**, click **Browse**, enter `adfs-token-signing` as the certificate name, then click **Next**.
[See image.](#ADFS2F)
-
In **Completing the Certificate Export Wizard**, click **Finish**.
[See image.](#ADFS2G)
- In the **Certificate Export Wizard** window, click **OK**.
Verifying Admin Portal Access via SSO
To verify the Admin Portal access via SSO:
- Browse to the following URL:
https://<AD FS Server>/adfs/ls/idpinitiatedSignOn.aspx
where `<AD FS Server>` is the exact AD FS server name. For example, if your server name is adfs.safemarch.com, enter `https://adfs.safemarch.com/adfs/ls/idpinitiatedSignOn.aspx`.
- Verify that you are directed to the AD FS login screen.
- Log in using your SAML admin login credentials to authenticate.
[]![Add Relying Party Trust in AD FS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS1B.png)
[]![Start in Welcome step](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS1Ci.png)
[]![Import data about the relying party from a file](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS1Cii.png)
[]![Display name](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS1Civ.png)
[]![Configure Multi-factor Authentication Now? in AD FS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS1Cv.png)
[]![Choose Issuance Authorization Rules in AD FS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS1Cvi.png)
[]![Ready to Add Trust in AD FS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS1Cvii.png)
[]![Configure claims insurance policy in AD FS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS1Cviii.png)
[]![Edit Claim Insurance Policy in AD FS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS1D.png)
[]![Select Rule Template in AD FS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS1Ei.png)
[]![Claim rule name in AD FS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS1Eii.png)
[]![Attribute store in AD FS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS1Eiii.png)
[]![LDAP Attribute in AD FS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS1Eiv.png)
[]![Outgoing Claim Type in AD FS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS1Ev.png)
[]![Edit Claim Insurance Policy in AD FS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS1F.png)
[]![Certificates in AD FS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS2A.png)
[]![View Certificate... in AD FS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS2B.png)
[]![Copy to File... in AD FS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS2C.png)
[]![Next in Certificate Export Wizard window of AD FS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS2D.png)
[]![Base-64 encoded X.509 (.CER) in AD FS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS2E.png)
[]![Token signing certificate export in AD FS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS2F.png)
[]![Finish button of Certificate Export Wizard window of AD FS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-ad-fs-3-0-draft-doc-51903/ADFS2G.png)