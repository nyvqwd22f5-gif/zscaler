# Admin SAML Configuration Guide for AD FS 3.0
Source: https://help.zscaler.com/unified/admin-saml-configuration-guide-ad-fs-3-0
PDF: https://help.zscaler.com/pdf/com/en/1491036.pdf

This example illustrates how to configure a Windows Server 2012 R2 running Active Directory Federation Services 3.0 (AD FS) as the identity provider (IdP) for the Zscaler service and use [SAML single sign-on (SSO) for your organization's admins](/unified/configuring-saml-admins). To learn more about the steps in the Windows Server 2012 R2, refer to the [Microsoft AD FS documentation](https://docs.microsoft.com/en-us/windows-server/identity/active-directory-federation-services).
Prerequisites
Ensure you have the following before configuring AD FS:
- AD FS account with admin privileges
- [Admin accounts](/zidentity/adding-zidentity-admin-roles) created for your organization's admins
- Zscaler Admin XML Metadata
Configuring Admin SAML SSO in AD FS
To configure AD FS as the IdP for the Zscaler service and use SAML SSO for admins:
- [Add a Relying Party Trust and Claim Rule.](#add-trust-claim-rule)
- [Export the IdP SAML SSL certificate.](#export-cert)
- Make sure that the [External Identities (IdP)](/zslogin/adding-saml-identity-providers) and [SAML Attributes](/zslogin/about-attributes) are configured in the Admin Portal.
Verifying Admin Portal Access via SSO
To verify the Admin Portal access via SSO:
- On the Windows device, browse to the following URL:
https://<AD FS Server>/adfs/ls/idpinitiatedSignOn.aspx
The <AD FS Server> depends on your AD FS server name. For example, if your AD FS server name is adfs.safemarch.com, you enter https://adfs.safemarch.com/adfs/ls/idpinitiatedSignOn.aspx.
- Verify that you are directed to the AD FS login screen.
- Log in using your SAML admin login credentials to authenticate.
[See image.](#seeimage0)
[]![C. Testing the Configuration](/downloads/zia/d047d427-8228-49f8-9791-9a586f10cfb5_display.png)
[]In AD FS, a relying party is a Federation Service or application that requests and processes claims from a claims provider in a particular transaction. Configure the Zscaler service as a relying party trust. After, add a claim rule, which is a statement that provides information about a user. It is used by the Zscaler service to determine if the user is allowed access.
To add Zscaler as a relying party trust and to add a claim rule:
- On the **Server Manager**, go to **Tools** >** AD FS Management**.
- In the left navigation panel of the **AD FS** window, expand the **AD FS** folder, then expand the **Trust Relationships** folder, and click the **Relying Party Trusts** folder.
[See image.](#seeimage2)
- In the **Actions** panel on the right, under **Relying Party Trusts**, click **Add Relying Party Trust…**.
[See image.](#seeimage3)
- When the **Add Relying Party Trust** **Wizard** appears, click **Start**. The wizard sections are listed on the left pane.
[See image.](#seeimage4)
- In **Select Data Source**, do the following:
- Select **Import data about the relying party from a file**.
- Under **Federation metadata file location**, click **Browse**, navigate to the Admin SP XML metadata file, and then click **Open**.
- When the location of the Admin SP XML metadata file displays, click **Next**.
[See image.](#seeimage5)
- In **Specify Display Name**, enter a display name for the Zscaler service, such as Zscaler Admin SAML, and then click **Next**.
[See image.](#seeimage6)
- In **Configure Multi-factor Authentication Now?**,** **select **I do not want to configure multi-factor authentication settings for this relying party trust at this time**,** **and then click **Next**.
[See image.](#seeimage7)
- In **Choose Issuance Authorization Rules**, select **Permit all users to access this relying party**, and then click **Next**.
[See image.](#seeimage8)
- In **Ready to Add Trust**, review your settings, and click **Next**.
[See image.](#seeimage9)
- In **Finish**, select **Open the** **Edit Claim Rules dialog for this relying party trust when the wizard closes**, and then click **Finish** to add the relying party trust to the database.
[See image.](#seeimage10)
- When the **Edit Claim Rules** window appears, click **Add Rule**.
[See image.](#seeimage11)
- In **Choose Rule Type** of the **Add Transform Claim Rule** **Wizard**, choose **Send LDAP Attributes as Claims** from the dropdown menu, and then click **Next**.
[See image.](#seeimage12)
- In **Configure Claim Rule**, do the following:
- Enter a name for the claim rule, such as zsbeta claims.
- Choose **Active Directory** from the **Attribute Store** dropdown menu.
- Map the LDAP attributes that represent the admin's login name, full name, department, group to fields in the outgoing claim type.
- Map the LDAP attribute for login name to an outgoing claim type. In the **LDAP Attribute** column, choose **User-Principal-Name**. In the **Outgoing Claim Type** column, choose **Name ID**. The email address is sent as the Name ID.
- Map the LDAP attribute for full name to an outgoing claim type. In the **LDAP Attribute **column, choose **Display-Name**. In the **Outgoing Claim Type **column, enter **displayName**.
- Click **Finish** to add the claim rule.
[See image.](#seeimage13)
- When the **Edit Claim Rules** window displays the newly added claim rule in the list, click **Apply**, and then click **OK**.
[See image.](#seeimage14)
[]![A. Adding a Relying Party Trust and Claim Rule](/downloads/zia/2857b372-89de-4381-be1f-07f29cf188af_display.png)
[]![ab90d992-98f1-49c7-af0b-b1634c388092_display.png](/downloads/zia/ab90d992-98f1-49c7-af0b-b1634c388092_display.png)
[]![576219e2-60cf-4a5e-a486-99e9ee90ade6_display.png](/downloads/zia/576219e2-60cf-4a5e-a486-99e9ee90ade6_display.png)
[]![e2240763-c4af-4150-ad29-0975e1211f45_display.png](/downloads/zia/e2240763-c4af-4150-ad29-0975e1211f45_display.png)
[]![21cd8440-b2ee-41ea-8462-ad9cbbaad136_display.png](/downloads/zia/21cd8440-b2ee-41ea-8462-ad9cbbaad136_display.png)
[]![13b1621e-28b2-4dfa-9d18-27a476b8fbfe_display.png](/downloads/zia/13b1621e-28b2-4dfa-9d18-27a476b8fbfe_display.png)
[]![73695051-7830-4ce8-a0fb-b63fccb28b48_display.png](/downloads/zia/73695051-7830-4ce8-a0fb-b63fccb28b48_display.png)
[]![5a21287a-4696-4ca6-87a0-1c6805db2f7e_display.png](/downloads/zia/5a21287a-4696-4ca6-87a0-1c6805db2f7e_display.png)
[]![2268c66e-7780-4996-85d3-8d9bc5a94034_display.png](/downloads/zia/2268c66e-7780-4996-85d3-8d9bc5a94034_display.png)
[]![f2e378f4-5caa-46fc-b764-f2a71ff41f24_display.png](/downloads/zia/f2e378f4-5caa-46fc-b764-f2a71ff41f24_display.png)
[]![5197b2ee-0541-4add-b474-db98709af63a_display.png](/downloads/zia/5197b2ee-0541-4add-b474-db98709af63a_display.png)
[]![7f65f8c0-eab4-4162-8d78-00192bf4faf1_display.png](/downloads/zia/7f65f8c0-eab4-4162-8d78-00192bf4faf1_display.png)
[]![6d07cd3b-eccf-49bb-8856-457f16910c75_display.png](/downloads/zia/6d07cd3b-eccf-49bb-8856-457f16910c75_display.png)
[]To export the AD FS token-signing certificate that you will upload to the Zscaler service:
- In the left navigation panel of the **AD FS** window, expand the **Service** folder, and then click the **Certificates** folder.
[See image.](#seeimage2a)
- In the **Certificates** panel, right-click the certificate under **Token-signing**, and click **View Certificate...**.
[See image.](#seeimage2b)
- In the **Certificate** window, select the **Details** tab, and click **Copy to File…**.
[See image.](#seeimage2c)
- When the** Certificate Export** **Wizard** appears, click **Next**.
[See image.](#seeimage2d)
- In **Export File Format**, select **Base-64 encoded X.509 (.CER)**, and click **Next**.
[See image.](#seeimage2e)
- In **File to Export**, click **Browse** to navigate to the location where you want to export the certificate, enter a certificate name, and then click **Next**. In this example, the certificate is called adfsadmin.
[See image.](#seeimage2f)
- When the export is complete, click **Finish**, and then click **OK** to close the **Certificate Export Wizard**.
[See image.](#seeimage2g)
- Click **OK** to close the **Certificate** window.
- Go to the exported certificate, and ensure the following:
- The certificate file name has a .pem extension. (For example, rename adfsadmin.cer to adfsadmin.pem.) TheZscaler service accepts certificates with the .pem extension only.
- The file name contains one dot (".") only.
By default, Windows hides extensions for known file types.
- [Change the Windows Folder Properties to View and Edit Extensions](#view-extensions-windows)
You will upload this IdP SAML SSL certificate to the Admin Portal.
- []Start Windows **Control Panel**.
- Go to **Appearance** > **Folder Options** > **View**.
- When the **Folder Option** window appears, deselect **Hide extensions for known file types** to view extensions.
- Rename the extension of the exported certificate.
[]![B. Exporting the Certificate](/downloads/zia/22ebf15b-187e-48dc-bc20-a8387f6baffe_display.png)
[]![98c5ac68-0e5f-4fdf-b02c-4a54d1dc89da_display.png](/downloads/zia/98c5ac68-0e5f-4fdf-b02c-4a54d1dc89da_display.png)
[]![b5b734e7-3175-4630-b1a0-edb02be100fb_display.png](/downloads/zia/b5b734e7-3175-4630-b1a0-edb02be100fb_display.png)
[]![6b515af3-9cce-48a6-9c6a-f622183e2639_display.png](/downloads/zia/6b515af3-9cce-48a6-9c6a-f622183e2639_display.png)
[]![2e8dfef8-ff56-477e-9c59-bc537b100d9f_display.png](/downloads/zia/2e8dfef8-ff56-477e-9c59-bc537b100d9f_display.png)
[]![255fd459-b0aa-42e5-af36-9142b96e7774_display.png](/downloads/zia/255fd459-b0aa-42e5-af36-9142b96e7774_display.png)
[]![2113a399-df6a-4a20-8b0e-3bb810c7e7b3_display.png](/downloads/zia/2113a399-df6a-4a20-8b0e-3bb810c7e7b3_display.png)