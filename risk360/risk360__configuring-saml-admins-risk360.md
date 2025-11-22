# Configuring SAML for Admins in Risk360
Source: https://help.zscaler.com/risk360/configuring-saml-admins-risk360
PDF: https://help.zscaler.com/pdf/com/en/1461806.pdf

The Zscaler service supports identity provider (IdP)-initiated SAML to authenticate admins. The admin can log in to the Risk360 Admin Portal directly from a Single Sign-On (SSO) provider's portal by clicking the Zscaler application icon. This feature also enables you to integrate admin authentication with your existing two-factor authentication solution.
Admins are not added through auto-provisioning. Rather, an admin must be added in the Risk360 Admin Portal and can then use SAML authentication to log into it. The Zscaler service does provide a password authentication option for admins, but the Zscaler service recommends that admins use SAML authentication to log in to the Risk360 Admin Portal. However, the service also recommends that you have at least one super admin with password authentication enabled to ensure an admin can still access the Risk360 Admin Portal if SAML servers external to the Zscaler service become unreachable. The Zscaler service supports SAML 2.0 and later.
Prerequisites
Ensure you do the following before configuring SAML SSO for admins:
- Create admin accounts for your organization's admins. To learn more, see [Adding Admins](/risk360/adding-admins-risk360).
- Configure an IdP, such as [Okta](/risk360/saml-configuration-guide-okta), [Microsoft Entra ID](/risk360/saml-configuration-guide-entra-id), etc.
- Obtain the SAML certificate of the IdP. You upload this certificate to the Risk360 Admin Portal when you configure the service to use SAML.
If you are subscribed to the ZIdentity service, the Administrator Management page shows a link to the ZIdentity Admin Portal. You can manage your admins from the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal). To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
[See image.](#zidentity-administration)
[]Configuring SAML SSO for Admins
To configure SAML SSO for admins in the Risk360 Admin Portal:
- Go to** Administration **>** Administrator Management**.
- Click the **Administrator Management** tab.
- In the **SAML Authentication for Administrators** section:
- **Enable** **SAML Authentication**: Enable to allow admins to log in to the Risk360 Admin Portal directly from your SSO provider portal. You must have already configured an IdP (e.g., ADFS, Okta, etc.) for your organization and added the admin account in the Risk360 Admin Portal (instead of using auto-provisioning).
- **IdP SAML Certificate**:** **Upload the SAML public certificate that is used to verify the digital signature of the IdP. This is the base-64 encoded PEM format that you downloaded from the IdP. The file extension must be .pem or .cer and have no other periods (.) in the file name.
[See image.](#seeimage1)
- [Change the Windows Folder Properties to View and Edit Extensions](#pem-instructions)
- []Start Windows 10 Control Panel.
- Go to **Appearance & Personalization** > **File Explorer Options**.
- When the **File Explorer Options** window appears, click the **View **tab.
- In **Advanced settings:**, deselect **Hide extensions for known file types** to view extensions and click **OK**.
- Rename the certificate to change the extension.
- **Download XML Metadata**:** **Download the XML metadata of the Zscaler service. The metadata details Zscaler SAML capabilities and is used for auto-configuration. Some IdPs require the metadata to configure service providers.
- **Issuer**: (Optional) Enter the IdP issuer associated with the Zscaler service, and click **Add Items**. You can enter multiple entries. Press `Enter` after each entry. You can add up to custom 25,000 URLs (across all categories). For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
[See image.](#seeimage2)
- Click **Save** and [activate the change](/risk360/saving-and-activating-changes-risk360-admin-portal).
[]![Screenshot highlighting the Upload button in the IdP Public SSL Certificate window.](/downloads/zia/authentication-administration/administrator-role-management/saml-admins/configuring-saml-admins/ZIA-IdP-SAML-Certificate-Window.png)
[]![Screenshot of the SAML Authentication for Administrators section on the Administrator Management page.](/downloads/zia/authentication-administration/administrator-role-management/saml-admins/configuring-saml-admins/ZIA-SAML-Authentication-For-Administrators-Section.png)
[]![Link to the ZSLogin Admin Portal on the Administrator Management Page](/downloads/risk360/administration-authentication/administrator-role-management/configuring-password-expiration-risk360/Risk360-ZIdentity-Administration.png)