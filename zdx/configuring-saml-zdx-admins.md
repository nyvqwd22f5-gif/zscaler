# Configuring SAML for ZDX Admins
Source: https://help.zscaler.com/zdx/configuring-saml-zdx-admins
PDF: https://help.zscaler.com/pdf/com/en/1382401.pdf

The Zscaler service supports identity provider (IdP)-initiated SAML to authenticate administrators. The admin can log in to the ZDX Admin Portal directly from a Single Sign-On (SSO) provider's portal. This feature also enables you to integrate admin authentication with your existing two-factor authentication solution.
Admins are not added through auto-provisioning. Rather, an admin must be [added](/zdx/adding-zdx-admins) in the ZDX Admin Portal, and then the admin can use SAML authentication to log in. The Zscaler service provides a password authentication option for admins, but the Zscaler service recommends that admins use SAML authentication to log in to the ZDX Admin Portal. However, the service also recommends that you have at least one super admin with password authentication enabled to ensure an admin can still access the ZDX Admin Portal if SAML servers external to the Zscaler service become unreachable. The Zscaler service supports SAML 2.0 and later.
Prerequisites
Before you configure SAML SSO for ZDX admins, you must configure an IdP, such as AD FS, Okta, or Azure Active Directory.
The following are guides for configuring admin SAML SSO with specific IdPs:
- [Admin SAML Configuration Guide for AD FS 3.0](/zdx/admin-saml-configuration-guide-ad-fs-3.0)
- [Admin SAML Configuration Guide for Azure Active Directory](/zdx/admin-saml-configuration-guide-azure-active-directory)
- [Admin SAML Configuration Guide for Okta](/zdx/admin-saml-configuration-guide-okta)
- [Admin SAML Configuration Guide for PingFederate](/zdx/admin-saml-sso-configuration-guide-pingfederate)
[]
[]When configuring IdPs, the following information might be required for ZDX.
- ACS URL:
For ZDX Cloud:
https://admin.zdxcloud.net/zdx/idp-auth
For ZDX Beta Cloud:
https://admin.zdxbeta.net/zdx/idp-auth
- Download the SAML SSL certificate from the IdP. It must be in Base64-encoded PEM format.
- Entity ID:
For ZDX Cloud:
https://admin.zdxcloud.net
For ZDX Beta Cloud:
https://admin.zdxbeta.net
If you have a domain defined on multiple ZIA clouds, enter the ZIA cloud name that is associated with ZDX in the **Relay State** field (for example, `zscalertwo.net`) for each application.
You must also create admin accounts for your organization's admins. To learn more, see [Adding ZDX Admins](/zdx/adding-zdx-admins).
[]Configuring SAML SSO for ZDX Admins
To configure SAML SSO for admins in the ZDX Admin Portal:
- Go to** Administration **>** Administrator Management**.
- Click the **Administrator Management** tab.
- In the **SAML Authentication for Administrators** section, do the following:
- **Enable** **SAML Authentication**: Enable this setting to allow admins to log in to the ZDX Admin Portal directly from your SSO provider portal. An IdP (such as AD FS or Okta) must already be configured for your organization, and you must add the admin account in the ZDX Admin Portal, rather than through auto-provisioning.
-
**IdP SAML Certificate**:** **Upload the SAML public certificate that is used to verify the digital signature of the IdP. This is the Base64-encoded PEM format that you downloaded from the IdP. The file extension must be .pem or .cer and have only alphanumeric characters in the file name. If the file name contains non-alphanumeric characters (e.g., period, hyphen), rename the file name to consist of only alphanumeric characters.
[See image.](#UploadIdPSAML)
- **Download XML Metadata**:** **Download the XML metadata of the Zscaler service. The metadata details Zscaler SAML capabilities and is used for auto-configuration. Some IdPs require the metadata to configure service providers.
-
**Issuer**: (Optional) Enter the IdP issuer associated with the Zscaler service, and click **Add Items**. You can enter multiple entries. Press `Enter` after each entry. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
[See image.](#SAMLAuthentication)
- Click **Save** and [activate the change](/zdx/saving-and-activating-changes-admin-portal).
[]
![Screenshot of Upload button for the IdP SAML certificate](/downloads/zdx/administration/configuring-saml-zdx-admins/ZDX-IdP-SAML-Certificate-Window.png)
[]
![Screenshot of the SAML Authentication for Administrators section on the Administrator Management page](/downloads/zdx/administration/configuring-saml-zdx-admins/ZDX-SAML-Authentication-For-Administrators-Section2.png)