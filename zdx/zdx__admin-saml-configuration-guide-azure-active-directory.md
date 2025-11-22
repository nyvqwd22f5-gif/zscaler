# Admin SAML Configuration Guide for Azure Active Directory
Source: https://help.zscaler.com/zdx/admin-saml-configuration-guide-azure-active-directory
PDF: https://help.zscaler.com/pdf/com/en/1415166.pdf

ZDX provides information on the configuration of Microsoft Azure Active Directory (Azure AD) as an identity provider (IdP) service for the use of [SAML single sign-on (SSO) for your organization's admins](/zdx/configuring-saml-zdx-admins). To learn more about the steps in the Azure portal, see the [Microsoft Azure AD documentation](https://docs.microsoft.com/en-us/azure/active-directory/saas-apps/zscaler-internet-access-administrator-tutorial).
Prerequisites
Ensure that you have the following before you start configuring Azure AD as the IdP:
- [Existing Azure AD account](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/zscaler-internet-access-administrator-tutorial#prerequisites)
- [ZDX Admin accounts](/zdx/adding-zdx-admins) created for your organization's admins
- [ZDX cloud URL](#zdx-cloudurls)
Configuring SAML Admin SSO with Azure
To configure Azure AD as the IdP for ZDX and use SAML SSO for admins:
- [Add the Zscaler Digital Experience Administrator Application](#adding-zdx-admin-application)
- [Configure SAML Admin SSO in Azure](#configure-saml-admin-azure)
- [Assign Admins to ZDX Admin Application](#assigning-admins-zdx-admin-app)
- [(Optional) Enable IdP-Initiated SSO](#application-visibility)
- [Configure SAML Admin SSO in the ZDX Admin Portal](/zdx/configuring-saml-zdx-admins)
Testing the SAML Configuration
[]To test the SAML admin SSO, users can initiate the SAML connection from the ZDX SAML SSO application. There are two ways to do this:
- [Go to Microsoft My Apps Portal](#access-panel)
- [Browse to the User Access URL](#user-access-url)
[]Ensure you enable the new experience preview for Enterprise applications and the Azure AD gallery.
To add the ZDX Administrator application in Azure:
- Sign in to the [Azure portal](http://portal.azure.com/).
- Go to **Azure Active Directory**.
[See image.](#AzureActiveDirectory)
- On the left navigation pane, click **Enterprise applications**.
[See image.](#EnterpriseApplications)
- Click **New application**.
[See image.](#NewApplication)
The **Browse Azure AD Gallery (Preview)** page appears.
- On the **Browse Azure AD Gallery (Preview)** page, enter `zscaler` in the search bar, and click the **Zscaler Internet Access Administrator** application.
[See image.](#BrowserAzureADGallery)
- Rename the application to a preferred name. Then click **Create**.
For example purposes, the application is named ZDX SAML SSO.
[See image.](#ZIAAdministrator)
The Azure AD service displays a notification that the ZDX SAML SSO application was added.
[]**![Screenshot highlighting the Azure Active Directory menu in the Azure portal](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/ZDX-AzureServices-AzureActiveDirectory.png)
**
[]**![Screenshot highlighting the Enterprise applications menu for Azure AD](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/zdx-azure-enterprise-applications.png)
**
[]![New application link on the Enterprise applications | All applications (Preview) page](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/zdx-azure-new-application.png)
[]![Screenshot highlighting the search bar and the Zscaler Internet Access Administrator application on the Browse Azure AD Gallery (Preview) page](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/zdx-azure-search-zscaler.png)
[]**![Screenshot highlighting the Create button for the Zscaler Internet Access Administrator application](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/ZDX-Azure-Zscaler-Internet-Access-Administrator-App-Rename.png)
**
[]To configure SAML admin SSO in Azure:
- On the left navigation pane of the Azure Active Directory, go to **Enterprise Applications** > **ZDX SAML SSO**.
[See image.](#EnterpriseApplications2)
- On the left navigation pane for the ZDX SAML SSO application, click **Single sign-on**.
[See image.](#SSO)
- Choose **SAML**.
[See image.](#SSO-SAML)
- In **Basic SAML Configuration**, click the **Edit** icon.
[See image.](#BasicSAMLConfiguration)
- In the **Basic SAML Configuration** window:
- **Identifier (Entity ID)**: Enter the following identifier.
admin.<ZDX Cloud>.net
The identifier depends on the URL you use to log in to the Zscaler service. For example, if you log in to https://admin.zdxbeta.net, then the identifier is admin.zdxbeta.net. To learn more, see [Configuring SAML for ZDX Admins](/zdx/configuring-saml-zdx-admins#CloudURLs).
- **Reply URL (Assertion Consumer Service URL)**: Click **Add reply URL **to select one of the following Zscaler admin SSO URLs with your Zscaler cloud name.
- **https://admin.zdxcloud.net/zdx/idp-auth**
- **https://admin.zdxpreview.net/zdx/idp-auth**
- **https://admin.zdxbeta.net/zdx/idp-auth**
The Zscaler cloud name depends on the URL you use to log in to the Zscaler service. For example, if you log in to https://admin.zdxbeta.net, then select **https://admin.zdxbeta.net/zdx/idp-auth**. To learn more, see [Configuring SAML for ZDX Admins](/zdx/configuring-saml-zdx-admins#CloudURLs).
[See image.](#ReplyURL)
- **Sign on URL**: Leave this field blank.
- **Relay State (As Required)**: If tenants are defined on multiple Zscaler Internet Access (ZIA) clouds and have a common domain, you need to configure authentication with a specific ZIA cloud by entering and selecting the ZIA cloud domain name (e.g., zscalertwo.net).
- **Logout URL**: Leave this field blank.
[See image.](#BasicSAMLConfigurationEdit)
- Click **Save** and exit the window.
- In **SAML Signing Certificate**, download **Certificate (Base64)**. You need it for Step 5. [Configure SAML Admin SSO in the ZDX Admin Portal](/zdx/configuring-saml-zdx-admins).
[See image.](#SAMLCertificate)
[]**![Screenshot highlighting the Single sign-on menu for the added Zscaler cloud application](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/ZDX-Azure-Zscaler-cloud-application-Single-sign-on-menu.png)
**
[]**![Screenshot highlighting SAML for the single sign-on method](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/zdx-Azure-Zscaler-cloud-application-Single-sign-on-method-admin.png)
**
[]![Screenshot of the Edit icon for the the Basic SAML Configuration section.](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/ZDX-Azure-Basic-SAML-Configuration-Edit-Icon.png)
[]![Screenshot of the admin SAML configuration in the Basic SAML Configuration window.](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/ZDX-Azure-Admin-Basic-SAML-Configuration-window.png)
[]**![Screenshot highlighting the Download button for the Base64 Azure signing certificate in the SAML Signing Certificate section.](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/ZDX-Azure-SAML-Signing-Certificate-Download.png)
**
[]In order for Azure AD admins to authenticate through the Zscaler service, you must assign Azure AD admins to the ZDX SAML SSO application.
To assign admins to the Zscaler cloud application in Azure:
- On the left navigation pane of the ZDX SAML SSO application, click **Users and groups**.
[See image.](#UsersAndGroups)
- Click **Add user/group**.
[See image.](#AddUserGroup)
- In the **Add Assignment** window, click **Users and groups**.
[See image.](#AddAssignmentSelection)
- In the **Users and groups** window, select the admins you want to assign to the ZDX SAML SSO application, and click **Select**.
[See image.](#ConfirmAssignmentSelection)
- In the **Add Assignment** window, click **Assign**.
[See image.](#AssignmentAssign)
[]![Screenshot highlighting the Users and groups menu for the added Zscaler cloud application.](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/ZDX-Azure-User-and-groups-menu.png)
[]![Screenshot highlighting the Add user button on the Users and groups page.](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/ZDX-Azure-user-groups-add-user-button.png)
[]![Screenshot highlighting the Users and groups button in the Add Assignment window.](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/ZDX-Azure-Add-Assignment-Users-and-groups.png)
[]![Screenshot of the selected admins in the Users and groups window.](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/ZDX-azure-users-and-groups-window-admin.png)
[]![Screenshot highlighting the Assign button in the Add Assignment window.](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/ZDX-Azure-Add-Assignment-Assign-button.png)
[]By default, the ZDX SAML SSO application is visible to admins in their My Apps portal.
To enable or disable application visibility:
- On the left navigation pane for the ZDX SAML SSO application, click **Properties**.​​​​​
[See image.](#Properties)
- For **Visible to users?**, choose **Yes** or **No**.​​​
[See image.](#VisibleToUsers)
[]![Screenshot highlighting the Properties menu for the ZDX Admin application.](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/Azure-ZDX-Admin-Properties-menu.png)
[]![Screenshot highlighting the Visible to users? field on the Properties page.](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/ZDX-SAML-SSO-Properties.png)
[]You use this method if you've enabled application visibility in Step b of [4. (Optional) Enable IdP-Initiated SSO](#application-visibility).
To go to the Microsoft My Apps portal:
- Sign in to the [Microsoft My Apps portal](https://myapps.microsoft.com) to get access to all your assigned visible applications.
- Click the **Zscaler Digital Experience**.
You are automatically signed in to the ZDX Admin Portal.
[]If you've disabled application visibility in Step b of [4. (Optional) Enable IdP-Initiated SSO](#application-visibility), you use this method to directly access the ZDX SAML SSO application from the browser.
To browse to the user access URL:
- On the left navigation pane for the ZDX SAML SSO application, click **Properties**.
[See image.](#Properties2)
- Copy the **User access URL**.
[See image.](#ZDXSAMLSSOProperties)
- Browse to the user access URL.
[See image.](#MicrosoftSignIn)
You are automatically signed in to the ZDX SAML SSO Portal.
[]![Screenshot highlighting the Copy icon for the User access URL.](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/ZDX-SAML-SSO-Properties-User-Access-URL.png)
[]![Screenshot of the Sign In page for the ZDX Admin application.](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/ZDX-Microsoft-Azure-Admin-Sign-In-page.png)
[]![Select Enterprise Applications to access ZDX SAML SSO Configuration.](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/zdx-azure-enterprise-applications.png)
![Select ZDX SAML SSO Configuration from Enterprise Applications.](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/zdx-azure-enterprise-applications-zdx-saml-sso.png)
[]![SAML Single-Sign on configuration for Reply URL.](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/zdx-azure-ReplyURL.gif)
[]![Screenshot highlighting the Properties menu for the ZDX Admin application.](/downloads/zdx/administration/admin-saml-configuration-guide-azure-active-directory/Azure-ZDX-Admin-Properties-menu.png)
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
To learn more, see [Configuring SAML for ZDX Admins](/zdx/configuring-saml-zdx-admins).