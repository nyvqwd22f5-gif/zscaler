# SAML & SCIM Configuration Guide for Google Workspace
Source: https://help.zscaler.com/zia/saml-scim-configuration-guide-google-workspace
PDF: https://help.zscaler.com/pdf/com/en/1399656.pdf

This guide illustrates how to configure Google Workspace as the identity provider (IdP) for the Zscaler service.
Supported Features
The SAML features supported by the Zscaler and Google Workspace integration are:
[SP-initiated SSO](#sp-initiated-sso)
- Just-in-Time (JIT) Provisioning (SAML auto-provisioning)
The SCIM features supported by the Zscaler and Google Workspace integration are:
- Create Users
- Update User Attributes
Google Workspace does not support the following features:
- Sign SAML request
- On-demand provisioning for users
Prerequisites
Ensure that you have the following to configure Google Workspace as the IdP:
- Google Workspace account with admin privileges.
- The Zscaler SAML certificate (See [Adding Identity Providers](/zia/adding-identity-providers#SP-SAML-Certificate)).
Configuring Google Workspace as the IdP for the Zscaler Service
To configure Google Workspace as the IdP for the Zscaler service:
- [1. Configure the Zscaler app in the Google Admin console.](#Google-apps)
- [2. Add Google Workspace as the IdP in the ZIA Admin Portal.](#zia-add-idp)
- [3. Enable SAML in the ZIA Admin Portal.](#zia-enable-saml)
- [4. Enable SCIM in the ZIA Admin Portal.](#zia-scim)
- [5. Configure SCIM in the Google Admin console.](#google-scim)
- [6. Configure the Zscaler Authentication Exemptions List.](#authentication-exemptions-list)
Testing the SAML and SCIM Configuration
[]When your configuration is complete, you can test your work on another device.
Test the configuration with one or both of the following methods:
- [Test the SAML Configuration by Logging Out of the Zscaler Service](#test-saml-1)
- [Test the SAML Configuration with the Test URL](#test-saml-2)
To test the SCIM configuration, in the ZIA Admin Portal, go to **Administration** >** User Management**. You should see a complete list of the users and groups added to your user database.
Troubleshooting
If any errors occur, see [Troubleshooting SAML](/zia/saml-troubleshooting-guidelines) to troubleshoot browser settings and SAML error codes.
[]This testing method only applies if you're forwarding traffic using Proxy Auto-Configuration (PAC) files, Generic Routing Encapsulation (GRE) tunnels, or IPSec tunnels, and you've enabled Enforce Authentication for the location or sublocation.
- On the device, browse to [ip.zscaler.com](http://ip.zscaler.com).
- If you are already logged in to the Zscaler service, click **Logout**. Otherwise, ensure that your traffic is being forwarded to the Zscaler service.
- Browse to a website. You are redirected to Google and prompted to log in.
- Log in using your Google credentials, and you are automatically redirected to the original URL request.
- Go to [ip.zscaler.com](http://ip.zscaler.com). The status window shows the username indicating that authentication was successful.
-
[]On the device, enter `https://login.``<Zscaler Cloud Name>``/clstart?version=1&_domain=``<Tenant Domain>``&redrurl=https://mobile.``<Zscaler Cloud Name>`. To learn how you can find your cloud name, see [What Is My Cloud Name for ZIA?](/zia/what-my-cloud-name-zia) The <Tenant Domain> is your organization's domain that is used to log in to the Zscaler service. For example, if you logged in to the Zscaler service with the username `admin@``zscaler.com`, then zscaler.com is your <Tenant Domain>.
Given an organization on the `zscalerbeta.net` cloud with `zscaler.com` as the <Tenant Domain>, the completed URL would be:
``https://login.``zscalerbeta.net``/clstart?version=1&_domain=``zscaler.com``&redrurl=https://mobile.``zscalerbeta.net``
- If you are redirected to the ZIA Admin Portal, the SAML configuration is successful. You might be prompted to authenticate with your IdP.
[]To perform SP-initiated SSO:
- Open your site.
- You are redirected to `https://gateway.``<Zscaler Cloud Name>``.net` and prompted for a **User Name**.
- Enter your **User Name** and click **Sign in**.
[]
- Sign in to the [Google Admin console](http://admin.google.com/).
-
In the** **Google Admin console, go to** Apps > Web and mobile apps.**
[See image.](#see-image-1b)
-
In the **Add app **drop-down, click **Search for apps**.
[See image.](#see-image-1c)
-
Enter `Zscaler` in the search bar and click **Select **for the **Zscaler **web app.
[See image.](#see-image-1d)
-
On the **Google Identity Provider details **page, do the following, then click **CONTINUE**:
- Copy the **SSO URL**. You need it when configuring Google Workspace as the IdP for the Zscaler service.
-
Download or copy the **Certificate**. You need it when configuring Google Workspace as the IdP for the Zscaler service.
Ensure the certificate file name:
-
Has a .pem extension (e.g., rename it to google.pem). The Zscaler service only accepts certificates with the .pem extension.
By default, Windows hides extensions for known file types.
- [Change the Windows Folder Properties to View and Edit Extensions](#pem-instructions)
-
Contains only one dot (".").
[See image.](#see-image-1e-google-pem)
[See image.](#see-image-1e)
-
On the **Service provider details** page enter the following, then click **CONTINUE**:
- **ACS URL**: Enter `https://login.``<Zscaler cloud name>``.net:443/sfc_sso`.
-
**Entity ID**: Enter your `<Zscaler cloud name>`. To learn how you can find your cloud name, see [What is my cloud name for ZIA?](/zia/what-my-cloud-name-zia) In this example, the cloud is Zscaler Two, so the **Entity ID **is `zscalertwo.net`.
If you have more than one organization instance on the same Zscaler cloud, you must use an org-specific entity ID. You can see the org-specific entity ID for your instance in the ZIA Admin Portal while [adding or editing an identity provider](/zia/adding-identity-providers).
The org-specific entity ID is formatted like the following example:
`https://login.zscalertwo.net/sfc_sso/3829920`
- **Name ID format**: In the drop-down menu, select **EMAIL**.
- **Name ID**: In the drop-down menu, select **Basic Information** > **Primary email.**
[See image.](#see-image-1f)
-
On the **Attribute mapping **page, in the** Attributes **section:
- Select** Department** in the **Google Directory attributes **drop-down and enter `Department` in **App attributes**.
- Select** First name** in the **Google Directory attributes **drop-down and enter `DisplayName` in **App attributes**.
[See image.](#see-image-1g)
- Click **FINISH**.
[]
- Go to **Administration** > **Authentication Settings** > **Identity Providers**.
-
Click **Add IdP**.
If you have an existing IdP configuration, the **What do you want to do?** window appears. Click **Add another SAML IdP for a subset of users or locations** and then **Next**.
[See image.](#see-image-2b)
-
In the **Add IdP **window:
- **SAML Portal URL**: Enter the **SSO URL **that you copied from the Google Admin console.
- **Login Name Attribute**: Enter `NameID` (case-sensitive).
- **IdP SAML Certificate**: Upload the .pem certificate that you downloaded from the Google Admin console.
- **Org-Specific Entity ID**: Enable if you have more than one organization instance on the same Zscaler cloud. For example, if you have two organization instances on the same Zscaler cloud and must authenticate both instances against the same Google account, you can't use the same entity ID for multiple apps in the Google admin console. For this situation, you must enable this setting for both instances to generate a unique org-specific entity ID.
- **Locations**: Select the [locations](/zia/about-locations) to map to this IdP. You can also search for a location. Any unselected locations are mapped to the default IdP. This field is set to **Any** for the default IdP, and you can't modify it.
- **Authentication Domains**: Select the domains to map to this IdP. This allows the Zscaler service to display the correct IdP to authenticate an incoming user. Any unselected domains are mapped to the default IdP. This field is set to **Any** for the default IdP, and you can't modify it. Apart from the default IdP, any additional IdPs must be mapped to at least one domain.
- **Vendor**: Select **Google**.
- **Locations**: Select the Locations you want to map to the IdP. If it is your default IdP, all unselected locations are mapped to it.
- **Authentication Domains**: Select the domains you want to map to the IdP. If it is your default IdP, all unselected domains are mapped to it.
[See image.](#see-image-2c)
-
(Optional) If you want to Configure SAML Auto-Provisioning, in the **Provisioning Options **section:
- **Enable SAML Auto-Provisioning**: Enable this option.
- **User Display Name Attribute**: Enter `DisplayName` (case-sensitive).
- **Group Name Attribute**: (Optional) Specify a group name attribute or leave this field blank.
- **Department Name Attribute**: Enter `Department` (case-sensitive).
[See image.](#see-image-2d)
-
Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
To learn more about configuring an IdP in the ZIA Admin Portal, see [Adding Identity Providers](/zia/adding-identity-providers).
[]
- Go to **Administration** > **Authentication Settings** > **Identity Providers**.
- Click the **Edit **icon for your previously configured Google IdP.
- In the **Edit IdP **window, select **Enable SCIM Provisioning**.
-
Copy the **Base URL **and **Bearer Token**. You need them to configure SCIM in the Google Admin console.
[See image.](#see-image-4d)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-zia-admin-portal).
[]
- In the** **Google Admin console, go to** Apps > Web and mobile apps **and select the previously configured **Zscaler** app.
-
On the home page for the **Zscaler** app, click **Configure auto-provisioning**.
[See image.](#see-image-5b)
-
On the **App authorisation **page, enter the **Bearer Token **you copied from the ZIA Admin Portal, then click **CONTINUE**.
[See image.](#see-image-5c)
-
On the **Endpoint URL **page, enter the **Base URL **you copied from the ZIA Admin Portal, then click **CONTINUE**.
[See image.](#see-image-5d)
-
On the **Attribute mapping **page, configure the attributes so they match the following table, then click **CONTINUE**:
| Google Directory Attributes | App attributes |
| --------------------------- | -------------- |
| Formatted name | displayName |
| Last name | name.familyName |
| First name | name.givenName |
| Department | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User.department |
| Username | userName |
[See image.](#see-image-5e)
- (Optional) On the **Provisioning scope (optional) **page, search for and select a group if you want to limit provisioning to a specific group instead of all users, then click **CONTINUE**.
-
On the **Deprovisioning **page, specify an action and time for:
- **When an app is turned off for a user**
- **When a user is suspended from Google**
- **When a user is deleted from Google**
[See image.](#see-image-5g)
- Click **FINISH**.
-
On the home page for the Zscaler app, click **TEST SAML LOGIN**.
[See image.](#see-image-5i)
-
In the **Can't test SAML login** window, click** ALLOW ACCESS.**
[See image.](#see-image-5j)
-
In the **Service status **option, select **ON for everyone**.
[See image.](#see-image-5k)
- Click **SAVE.**
-
On the home page for the Zscaler app, enable **Auto-provisioning**.
[See image.](#see-image-5m)
The **Turn on** window appears.
-
Click **TURN ON**.
[See image.](#see-image-5n)
[]
- Go to **Administration **>** Authentication Settings**.
- For **Authentication Frequency**, select how often users are required to authenticate to the Zscaler service. If you select **Custom**, the field **Custom Authentication Frequency (days) **appears. Specify 1 to 180 days. To learn more, see [About Default Settings](/zia/about-authentication-default-settings).
-
For** Authentication Type**, choose **SAML**.
[See image.](#see-image-3c)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
- []Start the Windows 10 Control Panel.
- Go to **Appearance & Personalization** > **File Explorer Options**.
- When the **File Explorer Options** window appears, click the **View **tab.
-
In **Advanced settings**, deselect **Hide extensions for known file types** to view extensions.
[See image.](#change-file-type)
- Rename the certificate to change the extension.
[]To configure the list and enable users access to Google Workspace:
- Go to **Administration **>** Advanced Settings**.
- In the **Authentication Exemptions** section, enter `accounts.google.com `in **Exempted URLs**.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
If you are using PAC files, enter the following exception to the [PAC file](/zia/using-default-pac-files-forward-traffic-zia) exemption list. Otherwise, the authentication fails.
If (shExpMatch(host, "accounts.google.com"))
return "DIRECT";
This option only applies to user traffic from known locations. To learn more, see [Exempting URLs and Cloud Apps from Authentication](/zia/exempting-urls-cloud-apps-authentication).
[]![The Web and mobile apps section in the Google Admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/ZIA-google-click-search-for-apps.png)
[]![The Search for apps option in the Google Admin console](/downloads/tech-pubs-drafts/zia-draft-articles/saml-configuration-guide-google-apps-draft-doc-54658/ZIA-google-click-search-for-apps.png)
[]![The Zscaler app in the Google Admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/ZIA-google-search-zscaler-app.png)
[]![The Google .pem SAML certificate](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/ZIA-google-pem.png)
[]![The configured Google Identity Provider details section in the Google Admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/ZIA-google-add-zscaler-1_0.png)
[]![The configured Service provider details in the Google Admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/ZIA-google-add-zscaler-app-2_0.png)
[]![The configured SAML Attribute mapping in the Google Admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/ZIA-google-add-zscaler-3_0.png)
[]![The What do you want to do? window](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/ZIA-What-do-you-want-to-do-window.png)
[]![The configured Add IdP window](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/ZIA-google-add-idp.png)
[]![The SAML Auto-Provisioning section](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/ZIA-google-click-enable-saml-auto-provisioning.png)
[]![The option to enable SAML](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/Zia-Saml-SSO.png)
[]![The SCIM Base URL and Bearer Token](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/ZIA-google-edit-idp-scim.png)
[]![The option to Configure Auto Provisioning in the Google Admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/ZIA-google-click-on-configure-auto-provisioning.png)
[]![The App authorisation page in the Google Admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/ZIA-google-scim-1.png)
[]![The Endpoint URL page in the Google Admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/ZIA-google-scim-2.png)
[]![The configured Attribute mapping page in the Google Admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/ZIA-google-scim-3_0.png)
[]![The Deprovisioning page in the Google Admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/ZIA-google-scim-5_0.png)
[]![The Test SAML Login option in the Google Admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/ZIA-google-click-test-saml-login.png)
[]![The Can't test SAML login window in the Google Admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/zia-google-can't-test-saml-login.png)
[]![The Service status in the Google Admin console](/downloads/tech-pubs-drafts/zia-draft-articles/saml-configuration-guide-google-apps-draft-doc-54658/ZIA-google-click-on-for-everyone.png)
[]![The toggle to enable Auto-provisioning in the Google Admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/ZIA-google-click-auto-provisioning-toggle.png)
[]![The Turn on window in the Google Admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/ZIA-google-turn-on-provisioning.png)
[]![The Hide extensions for known file types option in the File Explorer Options window](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-google-apps/ZIA-Windows-File-Explorer-Options-View-Hide-extensions-for-known-file-types.png)