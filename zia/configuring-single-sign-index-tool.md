# Configuring Single Sign-On for the Index Tool
Source: https://help.zscaler.com/zia/configuring-single-sign-index-tool
PDF: https://help.zscaler.com/pdf/com/en/1530810.pdf

Instead of logging in to the [Index Tool](/zia/about-index-tool) with a username and password, you can configure single sign-on (SSO) to the Index Tool through your identity provider (IdP).
To configure SSO for the Index Tool:
-
Configure the Index Tool SSO integration in your IdP's admin console:
- [Okta](#idp-sso-okta)
- [Microsoft Entra ID](#idp-sso-entra)
To learn more, refer to the documentation for your IdP.
- After you finish integrating the Index Tool in your IdP's admin console, log in to the ZIA Admin Portal.
- Go to **Administration **> **Index Tool**.
- Click the **Edit **icon for the Index Tool configuration that you are enabling SSO for or click **Add Index Tool Configuration **if you are creating a new one.
-
Click **Enabled **for **Enable Single Sign-On**.
[See image.](#see-image-1)
-
In the **SSO Configurations **section:
- **IDP URL**: Enter the IdP SSO URL that you copied during the Index Tool integration.
-
**Issuer**: Enter `<Index tool URL>``/ssoLogin`.
This value is case-sensitive. Ensure that you enter it correctly.
- **SSO Certificate**: Upload the certificate that you downloaded during the Index Tool integration.
- **SAML Issuer ID**: Enter the URL that is used to verify your IdP.
[See image.](#see-image-2)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-zia-admin-portal).
- []Log in to the [Okta admin console](https://login.okta.com/) as an administrator.
-
In the Okta admin console, go to **Applications** > **Applications**.
[See image.](#okta-see-image-1)
-
Click **Create App Integration**.
[See image.](#okta-see-image-2)
-
In the **Create a new app integration** window, select **SAML 2.0**, and click **Next**.
[See image.](#okta-see-image-3)
-
On the **General Settings** tab, enter an **App name** for the Index Tool and click **Next**.
[See image.](#okta-see-image-4)
-
[]In the **SAML Settings **section:
- **Single sign-on URL**: Enter `<Index tool URL>``/ssoLogin`.
- **Use this for Recipient URL and Destination URL**: Select this option.
- **Audience URI (SP Entity ID)**: Enter `<Index tool URL>``/ssoLogin`.
- **Default RelayState**: Leave this field blank.
- **Name ID format**: Select **Unspecified**.
- **Application username**: Select **Okta username**.
- **Update application username on**: Select **Create and update**.
[See image.](#okta-see-image-5)
- Click **Next**.
- Click **Finish**.
-
On the **Sign On** tab, in the **SAML 2.0** section, click **More details**. Copy the **Sign on URL** and **Download **the **Signing Certificate**. You need them to configure SSO for the Index Tool in the ZIA Admin Portal.
[See image.](#okta-see-image-6)
- Copy the **Issuer **URL to have the Zscaler service verify the IdP.
-
Go to the **Assignments **tab for the Index Tool application and click **Assign**.
[See image.](#okta-see-image-7)
- Select **Assign to People **or **Assign to Groups**.
-
Click **Assign **for the users or groups you want to assign to the application.
[See image.](#okta-see-image-8)
-
If you are assigning people, confirm the username and click **Save and Go Back**.
[See image.](#okta-see-image-9)
-
Click **Done**.
The Okta service displays a notification that the application assignment was successful.
- []Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
-
In the left-side navigation, go to **Identity **> **Applications **> **Enterprise applications**.
[See image.](#entra-1)
-
Click **New application**.
[See image.](#entra-2)
The **Browse Microsoft Entra Gallery** page appears.
-
On the **Browse Microsoft Entra Gallery** page, click **Create your own application**.
[See image.](#entra-3)
The **Create your own application** window appears.
-
Enter a name for the application and select **Integrate any other application you don't find in the gallery (Non-gallery)**.
[See image.](#entra-4)
-
Click **Create**.
The Microsoft Entra service displays a notification that the application was added.
The **Overview** page for the newly created application appears.
-
On the **Overview** page, click **Get started **in the **2. Set up single sign on **section.
[See image.](#entra-5)
-
On the **Single sign-on **page, select **SAML**.
[See image.](#entra-6)
-
In the **Basic SAML Configuration **section, click **Edit**.
[See image.](#entra-7)
The **Basic SAML Configuration** window appears.
-
In the **Basic SAML Configuration** window:
- **Identifier (Entity ID)**: Click **Add identifier **and enter `<Index tool URL>``/ssoLogin`.
- **Reply URL (Assertion Consumer Service URL)**: Click **Add reply URL **and enter `<Index tool URL>``/ssoLogin`.
- **Sign on URL**: Leave this field blank.
- **Relay State**: Leave this field blank.
- **Logout URL**: Leave this field blank.
[See image.](#entra-8)
- Click **Save** and exit the window.
-
In the **SAML Certificates **section, download **Certificate (Base64)**. You need this certificate file when you configure SSO for the Index Tool in the ZIA Admin Portal.
[See image.](#entra-9)
-
In section four, copy the **Login URL**. You need it when you configure SSO for the Index Tool in the ZIA Admin Portal.
[See image.](#entra-10)
-
Copy the **Microsoft Entra Identifier** to have the Zscaler service verify the IdP.
[See image.](#entra-11)
-
In the left-side navigation for the Index Tool enterprise application, go to **Users and groups**.
[See image.](#entra-12)
-
On the **Users and groups **page, click **Add user/group**.
[See image.](#entra-13)
-
On the **Add Assignment **page, click **None Selected**.
[See image.](#entra-14)
-
In the **Users and groups **window, choose the users and groups you would like to assign to the Index Tool enterprise application and click **Select**.
[See image.](#entra-15)
-
Click **Assign**.
The Microsoft Entra service displays a notification that the application assignment was successful.
[]![Navigation to the Enterprise Applications page](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-index-entra-apps-nav.png)
[]![Click New application on the Enterprise applications page](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-index-entra-new-app.png)
[]![Click Create your own application on the Browse Microsoft Entra Gallery page](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-index-entra-create-app.png)
[]![Configure details in the Create your own application window](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-index-entra-create-window.png)
[]![Select Get started for Set up single sign on](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-index-entra-sso-get-started.png)
[]![Select SAML on the Single sign-on page](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-index-entra-select-saml-sso.png)
[]![Edit the Basic SAML Configuration](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-index-entra-edit-saml.png)
[]![Enter the Identifier and Reply URL on the Basic SAML Configuration page](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-entra-index-basic-saml-config.png)
[]![Download the Certificate (Base64)](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-index-entra-download-certificate.png)
[]![Copy the Login URL](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-index-entra-copy-login-url.png)
[]![Copy the Microsoft Entra Identifier](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-index-entra-copy-identifier.png)
[]![Navigate to the Users and Groups page in the Microsoft Entra admin center](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-index-entra-users-groups-nav.png)
[]![Add users and groups in the Microsoft Entra admin center](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-index-entra-click-add-user-group.png)
[]![Add an assignment to the enterprise application](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-index-entra-add-assignment.png)
[]![Select users and groups to assign to the enterprise application](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/zia-index-entra-search-add-users.png)
[]![View of the applications breadcrumb in the Okta Admin Console](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-okta-navigation-apps.png)
[]![View of the Create App Integration button in the Okta Admin Console](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-index-sso-okta-create-integration.png)
[]![View of the option to select SAML 2.0 in the Okta Admin Console](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-okta-select-saml-2.0.png)
[]![View of the general settings for the SSO integration in the Okta Admin Console](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-index-sso-okta-general-settings.png)
[]![View of the SAML Settings for the Index Tool SSO configuration in the Okta Admin Console](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-index-tool-saml-okta-saml-settings.png)
[]![View of the Sign On URL and Signing Certificate in the Okta Admin Console](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-okta-sign-on-settings.png)
[]![Assignments tab in the Okta admin console](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-index-okta-assign-people-groups.png)
[]![Assigning a user in the Okta admin console](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-index-okta-click-assign.png)
[]![Confirm the username for the assigned user](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-index-okta-save-go-back.png)
[]![View of the option to enable SSO for the Index Tool](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-enable-index-sso.png)
[]![View of the configuration fields for the Index Tool SSO configuration](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-single-sign-index-tool/ZIA-edit-index-tool-config-window.png)