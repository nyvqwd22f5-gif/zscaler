# Configuring SAML for SSO
Source: https://help.zscaler.com/zpc/configuring-saml-sso
PDF: https://help.zscaler.com/pdf/com/en/1392516.pdf

You can configure ZPC as the service provider (SP) and use the Security Assertion Markup Language (SAML) single sign-on (SSO) for provisioning and authenticating administrators. To learn more about SAML, see [About SAML](/zpc/about-saml).
Prerequisites
Before configuring the Zscaler service for SAML, ensure you obtain the SAML IdP certificate from your identity provider (IdP). You need to upload this IdP certificate to the ZPC Admin Portal when you're [adding the IdP configuration](/zpc/adding-idp-configuration).
Configuring SAML
To configure SAML-based SSO with ZPC:
- [1. Download the XML Metadata from the ZPC Admin Portal](#downloadxml)
- [2. Configure the IdP for SAML](#idps)
- [3. Add the IdP in the ZPC Admin Portal](#addidp)
- [4. Add Administrators to ZPC](#addadmins)
Configuring SAML JIT Provisioning
You can enable SAML just-in-time (JIT) provisioning to allow ZPC to automatically retrieve information related to users such as first name, or role name from the SAML response. If the user doesn't exist in the database, then the user is added to the database along with the role information. This new user is activated, and can access the ZPC Admin Portal.
JIT works only when you log in via an IDP-initiated SSO.
Before configuring SAML JIT provisioning, make sure to first [create a group](/zpc/adding-group) in the ZPC Admin Portal, add the same group name to the IdP, and assign users to this group. Or if you have an existing group on the IdP portal, then add the same group name in the ZPC Admin Portal. All users in the existing IdP group are provisioned on ZPC. This step is mandatory to avoid any errors during configuration.
IdP groups are prioritized over ZPC groups. If a user is part of both groups, they are logged into the IdP group.
To configure SAML Just-in-Time (JIT) provisioning with ZPC, you must enable JIT on the ZPC Admin Portal:
- Go to **Administration > Single Sign On**.
- On the **Single Sign On** page, click the **Edit** icon for the IdP.
- Select the checkbox under **Enable JIT**.
- Click **Save**.
Follow the relevant configuration guides of [Okta](http://developer.okta.com/docs/guides/build-sso-integration/saml2/main/#create-your-integration), [PingOne](https://docs.pingidentity.com/r/en-us/pingone/p1_c_introduction), [OneLogin](http://onelogin.service-now.com/support?id=kb_article&sys_id=b2c91143db109700d5505eea4b9619d5), and [Azure AD](https://learn.microsoft.com/en-us/power-apps/maker/portals/configure/configure-saml2-settings-azure-ad) to configure ZPC as an SP for your IdP.
[]
Follow the relevant configuration guides to configure ZPC as an SP for your IdP:
- [Okta](#okta)
- [PingOne](#pingone)
- [OneLogin](#onelogin)
- [Azure AD](#azuread)
- [CyberArk Iadaptive](#cyberark)
[]
- Log in to Okta with admin privileges.
- In the left-navigation menu, click **Applications**.
- Click **Create App Integration**.
- Select **SAML 2.0**, then click **Next**.
- On the **General Settings** tab, enter your **App Name** and click **Next**.
[See image.](#oktaidp)
- Under **SAML Settings**:
- For **Single Sign on URL**, enter the ACS URL provided in the [XML Metadata](#downloadxml) that you downloaded from the ZPC Admin Portal.
- Select the **Use this for Recipient URL and Destination URL** checkbox.
- For **Audience URI (SP Entity ID)**, enter the Entity ID provided in the [XML Metadata](#downloadxml) that you downloaded from the ZPC Admin Portal.
- From the **Name ID format** drop-down menu, select **Email Address**.
[See image.](#okta-samlsettings)
- Click **Next**.
- Select **I'm an Okta customer adding an internal app**, then click **Finish**.
- On the **Sign On** tab, click **View Setup Instructions **to view the following details. Copy and save this information because you need it when [adding an IdP configuration](/zpc/adding-idp-configuration):
- Identity Provider SSO URL
- Identity Provider Issuer
- X.509 Certificate
To learn more, see the [Okta documentation](https://developer.okta.com/docs/guides/build-sso-integration/saml2/main/#create-your-integration).
[]
- Log in to PingOne with admin privileges.
- Go to **Connections** > **Applications**.
- Click **Add Application**, then select **WEB APP**.
- Choose **SAML** as your connection type.
[See image.](#pingoneidp)
- Click **Configure**.
- Enter the **Application Name**, then click **Next**.
- Click **Import Metadata**, then upload the [XML Metadata](#downloadxml) that you downloaded from the ZPC Admin Portal.
[See image.](#samlping)
- Enter the **Assertion Validation Duration**, then click **Save and Continue**.
- From the **PingOne User Attribute** drop-down menu, select **Family Name**.
- Click **Save and Close**.
- Select your application, then click the **Configuration** tab.
- Download the Metadata that contains the following details. Copy and save this information, as you need it for [adding an IdP configuration](/zpc/adding-idp-configuration):
- Identity Provider SSO URL
- Identity Provider Issuer
- X.509 Certificate
To learn more, see the [PingOne documentation](https://docs.pingidentity.com/bundle/solution-guides/page/Chunk2116878145.html).
[]
- Log in to OneLogin with admin privileges.
- Click **Applications**, then click **Add App**.
[See image.](#onelogin-addapp)
- Search for SAML, then select the **SAML Test Connector (Advanced)** connector.
- Enter the **Display Name**, then click **Save**.
- On the **Configuration** tab:
- **ACS (Consumer) URL**: Enter the ACS URL provided in the [XML Metadata](#downloadxml) that you downloaded from the ZPC Admin Portal.
- **ACS(Consumer) URL Validator**: Enter the following URL:
https:\/\/app.us.zpccloud.net\/auth\/saml\/acs
- **Audience (EntityID)**: Enter the Entity ID provided in the [XML Metadata](#downloadxml) that you downloaded from the ZPC Admin Portal.
- Go to the **SSO** tab to view the following details. Copy and save this information, as you need it for [adding an IdP configuration](/zpc/adding-idp-configuration):
- Identity Provider SSO URL
- Identity Provider Issuer
- X.509 Certificate
[See image.](#onelogin-sso)
To learn more about configuring SSO, see the [OneLogin documentation](https://onelogin.service-now.com/support?id=kb_article&sys_id=b2c91143db109700d5505eea4b9619d5).
[]
- Go to **Administration** > **Single Sign On**.
- Click **Add IdP Configuration**.
- Click **Download XML Metadata**.
[See image.](#xml)
The XML Metadata contains the following information which you need to submit while [adding an IdP configuration](/zpc/adding-idp-configuration):
- **Name Identifier Format**: ZPC only supports email address as the Name ID format.
- **Entity ID**: A unique identifier for a SAML entity.
- **Assertion Consumer Service (ACS) URL**: ZPC destination URL where the SAML response must be sent to by the IdP.
[]
You can add a single IdP configuration for one tenant. To learn more, see [Adding an IdP Configuration](/zpc/adding-idp-configuration).
[]
You need to add the administrators to ZPC after configuring SAML-based authentication. To learn more, see [About Administrators](/zpc/about-administrators).
- []Log in to the Azure AD Portal with admin privileges.
- In the left-navigation menu, select **Azure Active Directory**, then select **Enterprise applications**.
[See image.](#enterpriseapp)
- Click **New application** > **Create your own** **application**.
[See image.](#azure-createnewapp)
- In the **Create your own application** section:
- Enter a name for the application that you want to configure with Azure AD.
- Select **Integrate any other application you don't find in the gallery**.
- Click **Create**.
[See image.](#app-name)
The newly created application page appears.
- In the left-navigation menu, select **Single sign-on** > **Setup single sign on**.
[See image.](#ssoinmenu)
- Click **Edit** in the **Basic SAML Configuration** section.
[See image.](#setupsso)
- In the **Basic SAML Configuration** window:
- Under **Identifier (Entity ID)**, click **Add Identifier** and enter the Entity ID provided in the [XML Metadata](#downloadxml) that you downloaded from the ZPC Admin Portal.
- Under **Reply URL (Assertion Consumer Service URL)**, click **Add reply URL **and enter the ACS URL provided in the [XML Metadata](#downloadxml) that you downloaded from the ZPC Admin Portal.
[See image.](#addidurl)
- Click **Save**.
A message appears indicating that the SAML configuration was saved successfully.
Next, you must add the user to the application.
- Go back to the application page.
- In the left-navigation menu, select **Users and groups** > **Add user/groups**.
[See image.](#azure-selectusermenu)
- On the **Add Assignment** page, click **Users and groups** to view the list of users.
- Enter the name of the user or search for the specific user.
[See image.](#azure-searchuser)
- Click **Select**. The user is selected.
[See image.](#azure-assignusers)
- Click **Assign**.The user is assigned to the application.
- Next, click **Users and groups** again.
- On the **Manage claims** page:
- For **Name identifier format**, select **email address** from the drop-down menu.
- For **Source attribute**, select **user.mail** from the drop-down menu.
[See image.](#azure-manageclaim)
- Click **Save**.
To learn more, see the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-fed-group-claims).
- []Log in to the CyberArk Identity Admin Portal.
- In the left-side navigation, go to **Apps & Widgets** > **Web Apps**.
- Click **Add Web Apps**.
[See image.](#cyberark-app)
- On the **Add Web Apps** screen, select the **Custom** tab.
- Search for SAML app and click **Add**.
[See image.](#cyberark-samlapp)
- In the confirmation window that appears, click **Yes**.
The SAML web app is added.
- Close the** Application Catalog**.
The **Settings** page opens for the SAML web app that you added.
- Enter the name and description for the SAML web app.
- Click **Save**.
Configuring the IdP
- In the left-side navigation of the SAML web app page, select **Trust** to set up the IdP configuration.
- Select **Manual Configuration**.
- Click the arrows to view the **IdP Entity ID/Issuer** and **Signing Certificate** fields.
- Copy the **Entity ID** and save it. This value is used in the SAML assertion to identify the IdP attempting to authenticate.
- Download the **Signing Certificate** to your local system. The certificate is used for secure SSO authentication between CyberArk Identity and ZPC.
- Copy the **Single Sign-On URL** and save it. ZPC uses this URL to notify CyberArk Identity of SAML SSO.
[See image.](#cyberark-idp)
- Click **Save**.
- Log in to the ZPC Admin Portal and [add the IdP configuration](/zpc/adding-idp-configuration). Use the values you copied in step 3 to configure the IdP.
Configuring the Service Provider
Next, you need to configure ZPC as the Service Provider in the CyberArk Identity Admin Portal.
- In the left-side navigation of the SAML web app page, select **Trust**.
- Scroll down to view the **Service Provider Configuration**.
- Select **Manual Configuration **and enter the following:
- **SP Entity/ ID / Audience**: Enter the Entity ID provided in the [XML metadata](/zpc/configuring-saml-sso#downloadxml) file that you downloaded while adding the IdP configuration in the ZPC Admin Portal.
- **Assertion Consumer Service (ACS) URL**: Enter the URL provided in the [XML metadata](/zpc/configuring-saml-sso#downloadxml) file that you downloaded from the ZPC Admin Portal.
- **NameID Format**: By default, the format is **Unspecified**. Retain this value.
[See image.](#cyberark-spconfig)
- Click **Save**.
The status of the SAML web app changes to **Ready to Deploy**.
Setting up the SAML Response
- In the left-side navigation of the SAML web app page, select **SAML Response **to map the attributes from ZPC to SAML attributes.
- Click **Add**.
- Enter the following attributes:
| **Attribute Name** | **Attribute Value** |
| ------------------ | ------------------- |
| `http://schemas.xmlsoap.org/claims/Group` | Click the **Edit** icon and select **LoginUser** from the drop-down list. Then select **RoleNames** from the list. |
| `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress` | Click the **Edit** icon and select **LoginUser** from the drop-down list. Then select **RoleNames** from the list. |
| `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name` | Click the **Edit **icon, select **LoginUser** from the drop-down list. Select **DisplayName** from the list. |
[See image.](#cyberark-samlattrib)
- Click **Save**.
- Scroll down and click **Preview SAML Response** to check if the attributes are mapped correctly.
Adding Roles
You need to add a role and assign users to this role.
Roles function as groups in the CyberArk Iadaptive.
To add a role:
- In the left-side navigation of the CyberArk Identity Admin Portal, select **Roles**.
- Click** Add Role**.
[See image.](#cyberark-addroles)
- Enter a name for the role, then click **Save**.
[See image.](#cyberark-rolename)
The newly added role is displayed on the **Roles** page.
- Click the role name again to view the **Roles** page and assign users to this role.
- Select **Members**, then click **Add**.
[See image.](#cyberark-addmembers)
- Search for the users that you want to add. Select the checkbox for the required users, then click **Add**.
[See image.](#cyberark-selectmembers)
When you create users, ensure that the Login name is the same as the email address for users. [See image.](#cyberark-suffix) If not, the SAML authentication fails.
- Click **Save**.
The users are now part of this role.
Assigning Permission to Role
You must assign permission for the role to access the SAML application.
- In the left-side navigation of the SAML web app page, select **Permissions**.
- Click **Add**.
[See image.](#cyberark-permissions)
- In the pop-up window that appears, search for the role.
The role is displayed.
- Select the checkbox for the role, then click **Add**.
[See image.](#cyberark-rolepermission)
After completing these steps, users can log in to the ZPC Admin Portal using SAML SSO. To learn more, see the [CyberArk documentation](https://docs.cyberark.com/Product-Doc/OnlineHelp/idaptive/Latest/en/Content/Applications/AppsCustom/AddConfigSAML.htm?tocpath=Administrator%7CIntegrate%20apps%7CAdd%20custom%20applications%7CCustom%20SAML%20applications%7C_____1).
[![Download the XML metadata](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-add-idp.png)
]
[![Configure the Okta IdP](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-okta2.png)
]
[![Configure the Okta SAML settings](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-okta-nameid.png?1670825878)
]
[![Configure PingOne IdP](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-ping2.png?1656411957)
]
[![Configure SAML for PingOne](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-ping3.png?1656412032)
]
[![Add the app to Onelogin](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-onelogin-addapp.png)
]
[![Copy the SSO data](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-onelogin-ssodata.png)
]
[![Select create a new application](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-azure-createapp1.png)
]
[![Add SAML configuration](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-azure-basicsamlconfig.png)
]
[![Enter the app name](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-azure-addappname.png)
]
[![Select SSO](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-azure-selectsso.png)
]
[![Set up the SSO details](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-azure-sso.png?1670494760)
]
[![Select enterprise application](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-azure-selectenterprise.png)
]
[![Select users and group](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-azure-adduser.png)
]
[![Add user from the list](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-azure-addassignment.png)
]
[![Assign users to the app](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-azure-usersselected.png)
]
[![Add the name ID and source attribute](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-azure-nameidsourceattrib.png)
]
[![Add the SAML app](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-addsaml.jpg)
]
[![Set up the IdP configuration for CyberArk](/downloads/zpc/authentication/saml/configuring-saml-sso/cyberark-idpconfiguration.jpg)
]
[![Add the service provider configuration](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-serviceproviderconfiguration.jpg?1680248802)
]
[![Add SAML web app](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-addwebapp.jpg)
]
[![Add user members to the role](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-cyberark-addusers.jpg)
]
[![Provide the role name](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-addrolename.jpg)
]
[![Add a role to the SAML web app](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-addrole.jpg)
]
[![Add the SAML attributes](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-attributes.jpg)
]
[![Same login name and email address for users](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-usersuffix.jpg)
]
[![Add permissions to the role](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-permissions.jpg)
]
[![Select the role and assign permission](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-addpermission.jpg)
]
[![Select the users from the list](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-cyberarkselectusers.jpg)
]