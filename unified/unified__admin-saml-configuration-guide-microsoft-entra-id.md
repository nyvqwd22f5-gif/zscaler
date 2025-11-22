# Admin SAML Configuration Guide for Microsoft Entra ID
Source: https://help.zscaler.com/unified/admin-saml-configuration-guide-microsoft-entra-id
PDF: https://help.zscaler.com/pdf/com/en/1491141.pdf

This guide illustrates how to configure Microsoft Entra ID (formerly Azure Active Directory) as the identity provider (IdP) for the Zscaler service and use [SAML single sign-on (SSO) for your organization's admins](/unified/configuring-saml-admins). To learn more about the steps in the Microsoft Entra admin center, refer to the [Microsoft Entra ID documentation](https://learn.microsoft.com/en-us/entra/identity/saas-apps/zscaler-internet-access-administrator-tutorial).
Prerequisites
Ensure that you have the following before you start configuring Microsoft Entra ID as the IdP:
- Existing Microsoft Entra account
- Zscaler cloud name
- [Admin accounts](/zidentity/adding-zidentity-admin-roles) created for your organization's admins
Configuring SAML Admin SSO with Microsoft Entra ID
To configure Microsoft Entra ID as the IdP for the Zscaler service and use SAML SSO for admins:
[1. Add the Zscaler application in the Microsoft Entra admin center.](#adding-zia-admin-application)
[2. Configure SAML Admin SSO in the Microsoft Entra admin center.](#configure-saml-admin-azure)
[3. Assign admins to the application in the Microsoft Entra admin center.](#assigning-admins-zia-admin-app)
[4. (Optional) Enable IdP-Initiated SSO in the Microsoft Entra admin center.](#application-visibility)
5. Make sure that the [External Identities (IdP)](/zslogin/adding-saml-identity-providers) and [SAML Attributes](/zslogin/about-attributes) are configured in the Admin Portal.
Testing the SAML Configuration
[]To test the SAML admin SSO, users can initiate the SAML connection from the application. There are two ways to do this:
- [Go to Microsoft My Apps Portal](#access-panel)
- [Browse to the User Access URL](#user-access-url)
[]To add the Zscaler application in Microsoft Entra ID:
- Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
-
Go to **Identity **> **Applications **> **Enterprise applications**.
[See image.](#seeimage1b)
-
Click **New application**.
[See image.](#seeimage1d)
The **Browse Microsoft Entra ID Gallery** page appears.
-
On the **Browse Microsoft Entra ID Gallery** page, enter `zscaler admin` in the search bar, and click the **Zscaler Internet Access Administrator** application.
[See image.](#seeimage1e)
-
Click **Create**.
[See image.](#seeimage1f)
The Microsoft Entra ID service displays a notification that the application was added.
[]****![Enterprise applications in the Microsoft Entra navigation](/downloads/zia/documentation-knowledgebase/managing-admins/about-saml-single-sign-sso-admins/admin-saml-configuration-guide-microsoft-entra-id/ZIA-entra-navigation.png)
****
[]****![Screenshot highlighting the New application button on the Enterprise applications | All applications (Preview) page.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-add-entra-ID-enterprise-app.png)
****
[]****![Screenshot highlighting the search bar and the Zscaler Internet Access Administrator application on the Browse Microsoft Entra ID Gallery page](/downloads/zia/documentation-knowledgebase/managing-admins/about-saml-single-sign-sso-admins/admin-saml-configuration-guide-microsoft-entra-id/ZIA-entra-browse-app-gallery.png)
****
[]****![Screenshot highlighting the Create button for the Zscaler Internet Access Administrator application](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-id-create-zia-admin-app.png)
****
[]To configure SAML admin SSO in the Microsoft Entra admin center:
-
In the left-side navigation for the application, click **Single sign-on**.
[See image.](#seeimage2a)
-
Choose **SAML**.
[See image.](#seeimage2b)
-
In **Basic SAML Configuration**, click the **Edit** icon.
[See image.](#seeimage2c)
The **Basic SAML Configuration** window appears.
-
In the **Basic SAML Configuration** window:
-
**Identifier (Entity ID)**: Enter the following identifier.
`admin.<Zscaler cloud>.net`
The <Zscaler cloud> depends on the URL you use to log in to the Zscaler service. For example, if you log in to https://admin.zscalerbeta.net, then the identifier is admin.zscalerbeta.net.
- **Reply URL (Assertion Consumer Service URL)**: Select one of the following Zscaler admin SSO URLs with your Zscaler cloud name.
- **https://admin.zscaler.net/adminsso.do**
- **https://admin.zscalerone.net/adminsso.do**
- **https://admin.zscalertwo.net/adminsso.do**
- **https://admin.zscalerthree.net/adminsso.do**
- **https://admin.zscloud.net/adminsso.do**
- **https://admin.zscalerbeta.net/adminsso.do**
- The Zscaler cloud name depends on the URL you use to log in to the Zscaler service. For example, if you log in to https://admin.zscalerbeta.net, then select **https://admin.zscalerbeta.net/adminsso.do**.
- **Sign on URL**: Leave this field blank.
- **Relay State**: Leave this field blank.
- **Logout URL**: Leave this field blank.
[See image.](#seeimage2d)
- Click **Save** and exit the window.
-
In **SAML Signing Certificate**, download **Certificate (base64)**. You need it for Step 3 in [5. Configure SAML Admin SSO in the Admin Portal](/unified/configuring-saml-admins#configuring-saml-admins).
[See image.](#seeimage2f)
[]****![Screenshot highlighting the Single sign-on menu for the added Zscaler cloud application](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/Azure-Zscaler-cloud-application-Single-sign-on-menu.png)
****
[]****![Screenshot highlighting SAML for the single sign-on method](/downloads/zia/authentication-administration/administrator-role-management/saml-admins/admin-saml-configuration-guide-azure-active-directory/Azure-Zscaler-cloud-application-Single-sign-on-method-admin.png)
****
[]![Screenshot of the Edit icon for the the Basic SAML Configuration section.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/Azure-Basic-SAML-Configuration-Edit-Icon.png)
[]![Screenshot of the admin SAML configuration in the Basic SAML Configuration window.](/downloads/zia/documentation-knowledgebase/managing-admins/about-saml-single-sign-sso-admins/admin-saml-configuration-guide-microsoft-entra-id/ZIA-entra-admin-basic-saml-config.png)
[]****![Screenshot highlighting the Download button for the base64 Azure signing certificate in the SAML Signing Certificate section.](/downloads/zia/documentation-knowledgebase/managing-admins/about-saml-single-sign-sso-admins/admin-saml-configuration-guide-microsoft-entra-id/ZIA-entra-download-saml-cert.png)
****
[]In order for Microsoft Entra ID admins to authenticate through the Zscaler service, you must assign Microsoft Entra ID admins to the application.
To assign admins to the Zscaler cloud application in the Microsoft Entra admin center:
-
In the left-side navigation of the application, click **Users and groups**.
[See image.](#seeimage3a)
-
Click **Add user**.
[See image.](#seeimage3b)
The **Add Assignment** window appears.
-
In the **Add Assignment** window, click **Users and groups**.
[See image.](#seeimage3c)
The **Users and groups** window appears.
-
In the **Users and groups** window, select the admins you want to assign to the application, and click **Select**.
[See image.](#seeimage3d)
-
In the **Add Assignment** window, click **Assign**.
[See image.](#seeimage3e)
[]![Screenshot highlighting the Users and groups menu for the added Zscaler cloud application.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/Azure-Zscaler-cloud-application-User-and-groups-menu.png)
[]![Screenshot highlighting the Add user button on the Users and groups page.](/downloads/zia/documentation-knowledgebase/managing-admins/about-saml-single-sign-sso-admins/admin-saml-configuration-guide-microsoft-entra-id/ZIA-entra-admin-add-user.png)
[]![Screenshot highlighting the Users and groups button in the Add Assignment window.](/downloads/zia/documentation-knowledgebase/managing-admins/about-saml-single-sign-sso-admins/admin-saml-configuration-guide-microsoft-entra-id/ZIA-entra-admin-none-selected.png)
[]![Screenshot of the selected admins in the Users and groups window.](/downloads/zia/documentation-knowledgebase/managing-admins/about-saml-single-sign-sso-admins/admin-saml-configuration-guide-microsoft-entra-id/ZIA-entra-admin-select-users.png)
[]![Screenshot highlighting the Assign button in the Add Assignment window.](/downloads/zia/documentation-knowledgebase/managing-admins/about-saml-single-sign-sso-admins/admin-saml-configuration-guide-microsoft-entra-id/ZIA-entra-admin-users-assign.png)
[]By default, the application is visible to admins in their My Apps portal.
To enable or disable application visibility:
-
In the left-side navigation for the application, click **Properties**.​​​​​
[See image.](#seeimagee5)
-
For **Visible to users?**, choose **Yes** or **No**.​​​
[See image.](#seeimagee6)
[]![Screenshot highlighting the Properties menu for the ZIA Admin application.](/downloads/zia/authentication-administration/administrator-role-management/saml-admins/admin-saml-configuration-guide-azure-active-directory/Azure-ZIA-Admin-Properties-menu.png)
[]![Screenshot highlighting the Visible to users? field on the Properties page.](/downloads/zia/documentation-knowledgebase/managing-admins/about-saml-single-sign-sso-admins/admin-saml-configuration-guide-microsoft-entra-id/ZIA-entra-admin-properties.png)
[]You can use this method if you've enabled application visibility in Step 2 of [4. (Optional) Enable IdP-Initiated SSO](#application-visibility).
To go to the Microsoft My Apps portal:
- Sign in to the [Microsoft My Apps portal](https://myapps.microsoft.com) to get access to all your assigned visible applications.
-
Click **Zscaler Internet Access Administrator**.
[See image.](#seeimagee4)
You are automatically signed in to the Admin Portal.
[]![Screenshot highlighting the Zscaler Internet Access Administrator application in the Microsoft My Apps portal.](/downloads/zia/documentation-knowledgebase/managing-admins/about-saml-single-sign-sso-admins/admin-saml-configuration-guide-microsoft-entra-id/ZIA-entra-admin-my-apps.png)
[]If you've disabled application visibility in Step 2 of [4. (Optional) Enable IdP-Initiated SSO](#application-visibility), you can use this method to directly access the application from the browser.
To browse to the user access URL:
-
In the left-side navigation for the application, click **Properties**.
[See image.](#seeimagee1)
-
Copy the **User access URL**.
[See image.](#seeimagee2)
-
Browse to the user access URL.
[See image.](#seeimagee3)
You are automatically signed in to the Admin Portal.
[]![Screenshot highlighting the Properties menu for the ZIA Admin application.](/downloads/zia/authentication-administration/administrator-role-management/saml-admins/admin-saml-configuration-guide-azure-active-directory/Azure-ZIA-Admin-Properties-menu.png)
[]![Screenshot highlighting the Copy icon for the User access URL.](/downloads/zia/authentication-administration/administrator-role-management/saml-admins/admin-saml-configuration-guide-azure-active-directory/Azure-Properties-User-access-URL-copy-icon.png)
[]![Screenshot of the Sign In page for the ZIA Admin application.](/downloads/zia/authentication-administration/administrator-role-management/saml-admins/admin-saml-configuration-guide-azure-active-directory/Azure-Admin-Sign-In-page.png)