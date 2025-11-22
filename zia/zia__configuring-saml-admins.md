# Configuring SAML for Admins
Source: https://help.zscaler.com/zia/configuring-saml-admins
PDF: https://help.zscaler.com/pdf/com/en/1401156.pdf

[Watch a video about Administrator Management](https://fast.wistia.net/embed/iframe/8jluj4bctu)
If you are subscribed to ZIdentity, you can configure and manage SAML for your admins from the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal). To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
The Zscaler service supports identity provider (IdP)-initiated SAML to authenticate admins. The admin can log in to the ZIA Admin Portal directly from a Single Sign-On (SSO) provider's portal by clicking the Zscaler application icon. This feature also enables you to integrate admin authentication with your existing two-factor authentication solution.
Admins are not added through auto-provisioning. Rather, an admin must be [added](/zia/adding-admins) in the ZIA Admin Portal and can then use SAML authentication to log into it. The Zscaler service does provide a password authentication option for admins, but the Zscaler service recommends that admins use SAML authentication to log in to the ZIA Admin Portal. However, the service also recommends that you have at least one [super admin](/zia/adding-super-admin-role) with password authentication enabled to ensure an admin can still access the ZIA Admin Portal if SAML servers external to the Zscaler service become unreachable. The Zscaler service supports SAML 2.0 and above.
Prerequisites
Ensure you do the following before configuring SAML SSO for admins:
- Create admin accounts for your organization's admins. To learn more, see [Adding ZIA Admins](/zia/adding-admins).
- Configure an IdP, such as AD FS, Okta, Microsoft Entra ID (formerly Azure Active Directory), etc.
- Obtain the SAML certificate of the IdP. You upload this certificate to the ZIA Admin Portal when you configure the service to use SAML.
[]Configuring SAML SSO for Admins
To configure SAML SSO for admins in the ZIA Admin Portal:
- Go to** Administration **>** Administrator Management**.
- Click the **Administrator Management** tab.
-
In the **SAML Authentication for Administrators** section:
- **Enable** **SAML Authentication**: Enable to allow admins to log in to the ZIA Admin Portal directly from your SSO provider portal. You must have already configured an IdP (e.g., AD FS, Okta, etc.) for your organization and added the admin account in the ZIA Admin Portal (instead of using auto-provisioning).
-
**IdP SAML Certificate**:** **Upload the SAML public certificate that is used to verify the digital signature of the IdP. This is the base-64 encoded PEM format that you downloaded from the IdP. The file extension must be `.pem` or `.cer` and have no other periods (.) or spaces in the file name.
[See image.](#seeimage1)
- **Download XML Metadata**:** **Download the XML metadata of the Zscaler service. The metadata details Zscaler SAML capabilities and is used for auto-configuration. Some IdPs require the metadata to configure service providers.
- **Issuer**: (Optional) Enter the IdP issuer associated with the Zscaler service, and click **Add Items**. You can enter multiple entries. Press `Enter` after each entry. You can add up to 25K custom URLs (across all categories). To learn more, see [Ranges & Limitations](/zia/ranges-limitations). For guidance on entering URLs, see the [URL format guidelines](/zia/url-format-guidelines). For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appear.
[See image.](#seeimage2)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
IdP Configuration Guides
Following are guides for configuring admin SAML SSO with specific IdPs.
- [Admin SAML Configuration Guide for AD FS 3.0](/zia/admin-saml-configuration-guide-adfs-3.0)
- [Admin SAML Configuration Guide for Okta](/zia/configuring-okta-admin-saml-single-sign)
- [Admin SAML Configuration Guide for Microsoft Entra ID](/zia/saml-authentication-administrators-microsoft-azure-active-directory)
When configuring other IdPs, the following information might be required:
-
The ACS URL:
`https://admin.<Zscaler Cloud>.net/adminsso.do`
Replace <Zscaler Cloud> with the name of the cloud on which your organization is provisioned. To learn more, see [What is my cloud name for ZIA?](/zia/what-my-cloud-name-zia)
- The SAML SSL certificate downloaded from the IdP must be in Base-64 encoded PEM format.
-
The Entity ID:
`admin.<Zscaler Cloud>.net`
Replace <Zscaler Cloud> with the name of the cloud on which your organization is provisioned. To learn more, see [What is my cloud name for ZIA?](/zia/what-my-cloud-name-zia)
[]![The Upload button in the IdP Public SSL Certificate window.](/downloads/zia/authentication-administration/administrator-role-management/saml-admins/configuring-saml-admins/ZIA-admin-saml-upload-idp-certificate.png)
[]![The SAML Authentication for Administrators section on the Administrator Management page.](/downloads/zia/authentication-administration/administrator-role-management/saml-admins/configuring-saml-admins/ZIA-saml-auth-for-admins.png)