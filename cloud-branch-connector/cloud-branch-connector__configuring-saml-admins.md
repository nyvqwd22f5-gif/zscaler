# Configuring SAML for Admins
Source: https://help.zscaler.com/cloud-branch-connector/configuring-saml-admins
PDF: https://help.zscaler.com/pdf/com/en/1420806.pdf

The Zscaler service supports authenticating administrators using SAML initiated by an identity provider (IdP). An admin can log in to the Zscaler Cloud & Branch Connector Admin Portal directly via single sign-on (SSO) by clicking the Zscaler application icon within the provider's portal. This feature also enables you to integrate admin authentication with your existing two-factor authentication solution.
Admins are not added through auto-provisioning. Rather, you must add an admin in the Cloud & Branch Connector Admin Portal, and then they can use SAML authentication to log in to it.
Although the Zscaler service provides a password authentication option for admins, Zscaler recommends that admins use SAML authentication to log in to the Cloud & Branch Connector Admin Portal. However, Zscaler also recommends that you have at least one [super admin](/cloud-branch-connector/adding-super-admins) with password authentication enabled to ensure that an admin can still access the Cloud & Branch Connector Admin Portal even if SAML servers external to the Zscaler service become unreachable. The Zscaler service supports SAML 2.0 and later.
Prerequisites
Ensure that you do the following before configuring SAML SSO for admins:
- [Create admin accounts for your organization's admins](/cloud-branch-connector/adding-admins).
- Configure an IdP, such as Active Directory Federation Services (AD FS), Okta, Azure Active Directory, etc.
- Obtain the SAML certificate of the IdP. You upload this certificate to the Cloud & Branch Connector Admin Portal when you configure the service to use SAML.
[]Configuring SAML SSO for Admins
If you are subscribed to ZIdentity, some of the following options are only configurable within the ZIdentity Admin Portal. To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
To configure SAML SSO for admins in the Cloud & Branch Connector Admin Portal:
- Go to** Administration **>** Administrator Management**.
- Click the **Administrators Management** tab.
- In the **SAML Authentication for Administrators** section:
- **Enable** **SAML Authentication**: Enable to allow admins to log in to Cloud & Branch Connector via SSO from their identity provider's portal. Before you enable SAML authentication, you must configure an IdP (e.g., AD FS, Okta, etc.) for your organization. Also, you must add the admin account to the Cloud & Branch Connector Admin Portal, because admins cannot be added using auto-provisioning.
- **IdP SAML Certificate**:** **Upload the SAML public certificate that is used to verify the digital signature of the IdP. This is the Base64-encoded PEM format that you downloaded from the IdP. The file extension must be `.pem` or `.cer` and have no other periods (.) in the file name.
[See image.](#seeimage1)
- **Download XML Metadata**:** **Download the XML metadata of the Zscaler service. The metadata details Zscaler SAML capabilities and is used for auto-configuration. Some IdPs require the metadata to configure service providers.
- **Issuer**: (Optional) Enter the IdP issuer associated with the Zscaler service, and click **Add Items**. You can enter multiple issuers. Press** **`Enter` after each entry. You can add up to 25,000 custom URLs (across all categories). For item lists, you can view up to 500 items on a page. Filter the list by searching for a word, phrase, or number contained in an item. To remove all items from the list, click **Remove All**. To remove all items from only a specific page, click **Remove Page**. When you select** Remove All** or **Remove Page**, a confirmation window is displayed.
[See image.](#seeimage2)
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
[]![Upload button in the IdP SAML Certificate window in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/administration/administrator-role-management/configuring-saml-cloud-connector-admins/IDP_SAMLCERT_UPLOAD.png)
[]![SAML Authentication for Administrators section on the Administrator Management page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/administration/administrator-role-management/configuring-saml-cloud-connector-admins/SAMLAUTH_FORADMINS.png)