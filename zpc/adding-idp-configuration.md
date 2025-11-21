# Adding an IdP Configuration
Source: https://help.zscaler.com/zpc/adding-idp-configuration
PDF: https://help.zscaler.com/pdf/com/en/1402946.pdf

Adding an identity provider (IdP) in Zscaler Posture Control (ZPC) is one of the tasks you must complete when configuring SAML single sign-on (SSO). When you set up the IdP configuration, all the users in a particular tenant of your organization can log in using SSO.
You can add only one IdP configuration for one tenant. After you've configured one IdP, the option to add an IdP configuration is not visible on the Identity Provider page.
Prerequisites
A user with admin privileges can add or manage IdP configurations. You must first [configure SAML for SSO](/zpc/configuring-saml-sso) for your organization before proceeding with the IdP configuration.
Adding an IdP Configuration
To add an IdP configuration:
- Go to **Administration** > **Single Sign On**.
- On the **Single Sign On** page, click **Add IdP Configuration**.
[See image.](#zpc-addidp)
- In the **Add IdP Configuration** window:
- **Name**: Enter a unique name for the IdP.
- **Identity Provider Issuer**: Enter the unique value of the IdP that you obtained while [configuring SAML](/zpc/configuring-saml-sso).
- **Single Sign-on URL**: Enter the SSO URL of the SAML portal to which users are sent for authentication. This information is in the XML metadata of the IdP or obtained while [configuring SAML](/zpc/configuring-saml-sso).
-
**Single Sign-On**: By default, SSO is enabled for all users in the specified tenant.
When SSO is enabled, all users belonging to the specified tenant can log in only through SSO and they cannot log in using the local authentication method, as this option is disabled. When SSO is disabled, then all users receive an email to reset their password and log in through the local authentication method. However, the Default Super Administrator can log in to the ZPC Admin Portal through SSO or local authentication.
- **IdP Certificate**: Upload the IdP certificate that is used to verify the digital signature of the IdP. This is the certificate you downloaded from your IdP. To learn more, see [configuring SAML](/zpc/configuring-saml-sso).
- **XML Metadata**: Click to download the XML Metadata that you need for [configuring SAML](/zpc/configuring-saml-sso).
-
**Enable JIT**: Select to enable just-in-time (JIT) provisioning and allow ZPC to automatically retrieve user information from the IdP and provision users in ZPC.
- JIT works only when you log in via an IDP-initiated SSO.
- If you enable JIT provisioning, then make sure to first [create a group](/zpc/adding-group) in the ZPC Admin Portal and enable the SSO option. Then, configure the same group attribute in your IdP and assign users to this group. This attribute is mandatory for ZPC to invoke the same group that is mapped in your IdP. If the user belongs to multiple groups, then you must create at least one group with the same name in ZPC, so the user can log in to ZPC using SSO. To learn more, see [Adding a Group](/zpc/adding-group).
Follow these steps to configure the group attributes in:
- [Okta](#jit-okta)
- [OneLogin](#jit-onelogin)
- [PingOne](#jit-pingone)
- [Microsoft Entra ID](#azuread)
-
**Auto Update Group Based on IdP**: Select to allow automatic update of user and user's group information from your IdP.
When auto update is selected, the default groups (Default admin and Default Read only) associated with the user are not impacted.
[See image.](#zpc-idpconfig-window)
-
Click **Save**.
The IdP is configured and the details are displayed on the **Single Sign On** page.
[See image.](#zpc-idp-page)
When users try to log in to the ZPC Admin Portal, they are directed to the IdP portal for single sign-on.
- []Log in to the Okta portal.
- In the left-navigation menu, select **Applications** > **Applications**, then select ZPC application from the list.
- Click the** General** tab.
- Scroll down to **SAML Settings**, then click **Edit**.
- Under **Group Attribute Statements (optional)**, you can add the group attributes to the SAML assertion:
- **Name**: Enter the name of the group that you created on the ZPC Admin Portal.
- **(Optional) Name format**: Select URI Reference.
- **Filter**: If you choose the Name format, then select the required value (Starts with, Equals, Contains, Matches regex) from the drop-down list. This value is used to match against the Okta GroupName values and added to the SAML assertion.
- Click **Next**.
- Click **Finish**.
To learn more, refer to the [Okta documentation](https://help.okta.com/en-us/Content/Topics/users-groups-profiles/usgp-about-groups.htm).
- []Log in to the OneLogin portal.
- Click the **Parameters** tab.
- Add the group names that you created on the ZPC Admin Portal.
To learn more, refer to the [OneLogin documentation](https://onelogin.service-now.com/support?id=kb_article&sys_id=db0ad543db109700d5505eea4b96190c&kb_category=7506a530db185340d5505eea4b9619ba).
- []Log in to the PingOne portal.
- Go to **Connections** > **Applications**.
- Search for the application that you want to edit.
- Under **Attribute Mappings**, assign the following attribute to the group:
`http://schemas.xmlsoap.org/claims/Group`.
The following image is a sample.
[See image.](#pingone-attrib)
To learn more, refer to the [PingOne documentation](https://docs.pingidentity.com/bundle/pingone/page/jez1625773795534.html#jez1625773795534).
- []Log in to the Azure portal.
- Select **Enterprise applications**.
- In the left-navigation menu, select **Single sign-on** > **Set up single sign-on**.
-
Click **Edit** in the **Attributes & Claims** section and update these values:
- **Name**: Enter `name`.
- **Namespace**: The field is automatically populated based on the identifier that is selected. If the field is empty, then enter the following value: `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/`
- **Source attribute**: Enter `user.displayname`.
[See image.](#azure-sourceattrib)
- Click **Save**.
- Next, click **Add a group claim**.
- On the **Group claims** page, select the **Groups assigned to the application** option.
-
From the **Source attribute** drop-down menu, select **Cloud-only group display names**.
If you want to sync groups and users from an on-premises Active Directory via the Microsoft Entra ID Connect sync service, then select **SAMAccountName** from the drop-down menu.
-
Under **Advanced options**, select the **Customize the name of the group domain** checkbox.
- For **Name**, enter `Group`.
- For **Namespace**, enter [`http://schemas.xmlsoap.org/claims`.](http://schemas.xmlsoap.org/claims.)
[See image.](#add-groupclaim)
- Click **Save**.
To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/add-application-portal-setup-sso).
[][![Add an IdP configuration](/downloads/zpc/authentication/idp-configuration/adding-idp-configuration/zpc-sso-page.png)
]
[][![Add an IdP configuration ](/downloads/zpc/authentication/idp-configuration/adding-idp-configuration/zpc-add-idp.png?1657858876)
]
[][![Add the group attribute in your IdP](/downloads/zpc/authentication/idp-configuration/adding-idp-configuration/JITgroupattributes-IdP.png)
]
[][![Add a group claim](/downloads/zpc/authentication/saml/configuring-saml-sso/zpc-azure-goup.png)
]
[][![Edit the source attribute for Name field](/downloads/zpc/authentication/single-sign/adding-idp-configuration/zpc-idp-manageclaim.png)
]
[][![View the IdP details](/downloads/zpc/authentication/idp-configuration/adding-idp-configuration/zpc-sso-details.png)
]