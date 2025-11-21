# Configuration Guide for Onelogin
Source: https://help.zscaler.com/zpa/configuration-guide-onelogin
PDF: https://help.zscaler.com/pdf/com/en/1483756.pdf

This guide provides information on how to set up Onelogin as a IdP for ZPA.
Prerequisites
Ensure that you have the following:
- A Onelogin account with admin privileges.
- A ZPA account with an administrator role that allows you to add an IdP Configuration.
Configuring Onelogin for SSO
[]To configure Onelogin as the IdP for ZPA user and admin SSO:
- Log in to the Onelogin portal as an administrator and select **Apps** > **Add Apps**.
[See image.](#Step1_UserImg)
- In the search toolbar, search for `Zscaler Private Access`. If you are:
- Configuring the IdP for ZPA user SSO, click the **Zscaler Private Access 2.0** application.
- Configuring the IdP for ZPA admin SSO, click the **Zscaler Private Access Administrator 2.0** application.
[See image.](#Step2_UserImg)
The following steps are identical for both applications.
- On the **Configuration** page that appears, for **Display Name** make sure that **Zscaler Private Access 2.0** is entered for user SSO or **Zscaler Private Access Administrator 2.0** is entered for admin SSO, then click **Save**.
[See image.](#Step3_UserImg)
- From the **More Actions** drop-down menu, select **SAML Metadata** to download the IdP's metadata file. You will need this file later in order to [complete the configuration](/zpa/about-idp/new#IdP_BothSSO) within the ZPA Admin Portal.
[See image.](#Step4_UserImg)
- Go to **Configuration**.
- For **Application Details**:
- Log in to the ZPA Admin Portal, and [complete step 2 of the new IdP configuration procedure](/zpa/about-idp/new#AddIdPConfig_UserSSO). During this procedure, you must copy the identifier within the **Service Provider URL** string provided. The following is an example SP URL with the identifier highlighted in green:
[`https://adminsamlsp.private.zscaler.com/auth/``144118148382065352``/sso`](https://adminsamlsp.private.zscaler.com/auth/144118148382065352/sso)
The reference to private.zscaler.com in the following example might differ depending on your organization’s assigned cloud. To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
After you copy the identifier, you can **Pause** the configuration.
- Go back to the Onelogin portal, and paste the identifier into the **Unique identifier **field.
- Click **Save**.
[See image.](#Identifier_UserImg)
- Go to **Users** > **All Users**.
[See image.](#Step5_UserImg)
- On the **All Users** page, click on the user you want to assign the ZPA application to.
- Click **Applications**, then click the **New app** icon.
[See image.](#Step8_UserImg)
- In the window that appears, from the **Select Application** drop-down menu, select **Zscaler Private Access 2.0** for user SSO or **Zscaler Private Access Administrator 2.0** for admin SSO.
[See image.](#Step9_UserImg)
- Click **Continue**.
- In the window that appears, edit the user's attributes for login, then click **Save**.
[See image.](#Step11_UserImg)
After you have assigned the application, it appears in the user's **Applications **list.
- Click **Save User**.
- Go to the ZPA Admin Portal and [complete the IdP configuration set up](/zpa/about-idp/new#IdP_BothSSO).
For Onelogin, the IdP metadata file you upload to the ZPA Admin Portal will populate the **Name**, **Single Sign-On URL**, and **IdP Entity ID** fields. **ZPA (SP) SAML Request **is set to **Signed** and the **IdP Certificate** is uploaded automatically.
After configuring your IdP, be sure to [verify the configuration](/zpa/about-idp/new#Verify_SSO).
[]![Apps > Add Apps Menu Option within Onelogin](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-onelogin/zpa-onelogin-addapps.png)
[]![Find Applications search field within Onelogin](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-onelogin/zpa-onelogin-findapps-usersso.png)
[]![Display Name Field in the Configuration page within Onelogin](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-onelogin/zpa-onelogin-displayname.png)
[]![More Actions > SAML Metadata Menu Option within Onelogin](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-onelogin/zpa-onelogin-samluserssometadata.png)
[]![Configuration page on the Onelogin portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-onelogin/zpa-onelogin-appdetails-identifier.png)
[]![Users > All Users Menu Option within Onelogin](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-onelogin/zpa-onelogin-allusers.png)
[]![Applications > New app icon within Onelogin](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-onelogin/zpa-onelogin-assignuser2app.png)
[]![Select Application field in Assign New Login to user window within Okta](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-onelogin/zpa-onelogin-user2userssoapp.png)
[]![User Attributes fields within Onelogin](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-onelogin/zpa-onelogin-assignuserattrs.png)