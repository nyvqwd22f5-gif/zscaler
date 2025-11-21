# Configuring SAML for Okta
Source: https://help.zscaler.com/itdr/configuring-saml-okta
PDF: https://help.zscaler.com/pdf/com/en/1531727.pdf

Zscaler recommends that you use the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal) to configure primary and secondary [external identity providers (IdPs)](/zidentity/about-external-identity-providers). ZIdentity supports both SAML and OpenID configurations. Contact Zscaler Support to subscribe to ZIdentity.
This article provides information on how to configure SAML identity provider (IdP) single sign-on (SSO) for Okta.
To configure SAML IdP SSO for Okta:
- [Step 1: Configure Okta for SSO](#itdr-config-okta-sso)
- [Step 2: Obtain the Identity Provider Metadata](#itdr-obtain-idp-metadata)
- [Step 3: Create a SAML Provider in the Zscaler ITDR Admin Portal](#itdr-config-saml-admin-portal)
- [Step 4: Configure SAML Settings](#itdr-config-saml-settings)
- [Step 5: Assign Users or Groups Access via Okta](#itdr-assign-user-groups)
- [(Optional) Step 6: Configure SAML Group Provisioning for Okta](#itdr-config-saml-group-okta)
- []Log in to the Okta portal as an administrator.
- Go to **Applications** > **Applications**.
-
Click **Create App Integration**.
[See image.](#itdr-okta-create-app)
-
In the **Create a new app integration** window, select **SAML 2.0**, and click **Next**.
[See image.](#itdr-select-saml-2-sso)
-
On the **General Settings** tab, enter the **App name**, and click **Next**.
[See image.](#itdr-okta-app-name-general-settings)
- On the **Configure SAML **page, under **General**:
- **Single sign-on URL**: Enter `https://``<ITDR Admin Portal instance name>``/saml/id/1/assert`.
- **Audience URI (SP Entity ID)**: Enter `https://``<ITDR Admin Portal instance name>``/saml/id/1/metadata.xml`.
- **Name ID format**: Select **EmailAddress** from the drop-down menu.
-
**Application username**: Select **Email** from the drop-down menu.
The **Single sign-on URL** and **Audience URI (SP Entity ID)** are placeholder values, which must be changed later.
[See image.](#itdr-okta-config-saml-settings)
- Click **Next**.
-
Select **This is an internal app that we have created**, and then click **Finish**.
[See image.](#itdr-okta-complete-app)
The application is created.
- []Go to **Applications** > **Applications**.
- Select the ITDR application that you created in Step 1.
- Click **Sign On**.
-
Scroll down to the **SAML Setup** section, and click **View SAML setup instructions**.
[See image.](#itdr-okta-view-saml-setup-instructions)
-
In the window that appears:
- Copy the IdP SSO URL and IdP Issuer details.
- Copy the content from **Optional** and save it as Metadata.xml.
[See image.](#itdr-okta-download-idp-metadata)
- [][Configure SAML for Single Sign-On in the ITDR Admin Portal](/itdr/configuring-saml-single-sign-on).
Use the Metadata.xml file that you saved in Step 2.
- Obtain the service provider entity ID and service provider assertion URL, and download the encryption certificate. To learn more, see [Obtaining SAML Setup Information](/itdr/configuring-saml-single-sign-on#itdr-obtain-saml-setup-instn).
- []Log in to the Okta portal as an administrator.
- Go to **Applications** > **Applications**.
- Select the ITDR application created in Step 1.
- Click **General**.
- Scroll down to the **SAML Settings** section, and click **Edit**.
- In the **Edit SAML Integration wizard**, click **Next**.
- In the** SAML Settings** section, under **General**:
- **Single sign-on URL**: Enter the service provider assertion URL that you obtained from Step 3.
-
**Audience URI (SP Entity ID)**: Enter the service provider entity ID that you obtained from the ITDR Admin Portal in Step 3.
[See image.](#itdr-okta-sso-uri-audience-uri)
- Click **Show Advanced Settings** and scroll down:
- **Assertion Encryption**: Select **Encrypted** from the drop-down menu.
-
**Encryption Certificate**: Upload the encryption certificate that you downloaded from the ITDR Admin Portal in Step 3.
[See image.](#itdr-okta-config-sso-advance-settings)
- []Go to **Applications** > **Applications**.
- Select the ITDR application created in Step 1.
- Click **Assignments**.
-
Select **Assign** > **Assign to People **or **Assign to Groups** depending on whether you want to assign access to a single user or a group of users.
[See image.](#itdr-okta-assign-option)
-
In the window that appears, click **Assign** for the user or group you want to select, and click **Done**.
[See image.](#itdr-okta-assign-app-group-done)
- Repeat the previous step for all users and groups you want to assign to ITDR.
[]Before you configure SAML group provisioning using Okta as an IdP, make sure you create groups in Okta so that users within each group can be mapped to a role in the ITDR Admin Portal.
- Log in to the Okta portal as an administrator.
- Go to **Applications** > **Applications**.
-
Select the application that you created while configuring SAML for ITDR in Okta.
[See image.](#itdr-saml-group-okta-select-app)
-
Select **General** and scroll down to the **SAML Settings** section, and click **Edit**.
[See image.](#itdr-saml-group-okta-edit-saml-settings)
- On the **Edit SAML Integration** page, click **Next**.
- Under **SAML Settings**:
- In** Attribute Statements**:
- **Name**: Enter `FullName`.
- **Name Format**: Select **Basic** from the drop-down menu.
-
**Value**: Enter `String.join(" ", user.firstName, user.lastName)`.
[See image.](#itdr-saml-group-okta-attribute-statements)
- In **Group Attribute Statements**:
- **Name**: Enter `Group`.
- **Name Format**: Select **Basic** from the drop-down menu.
-
**Filter**: Select **Matches regex** from the drop-down menu, and then enter `.*` as the filter value.
[See image.](#itdr-saml-group-okta-group-attribute-statement)
- Click **Next**, and then click **Finish**.
- Log in to the ITDR Admin Portal.
- Go to **Settings** > **User & Roles** > **IdP Providers**.
- Select the SAML configuration that you configured for your IdP.
- In the **SAML Provider Details **window, under the **Group-Based SAML Login** section:
- **Auto Create User**: Enable to make sure the users in the specified groups are automatically created in the ITDR Admin Portal.
- **SAML Response Group Attribute**: Enter `Group`.
- **SAML Response Name Attribute**: Enter `FullName`.
-
Click **Add** to add a group and select the roles for each group.
- Enter the group name.
- Select a role for the group from the drop-down menu.
[See image.](#itdr-saml-group-okta-login)
- Click **Save**.
If the group attribute specified is not part of the SAML assertion when logging in or doesn't match one of the groups specified in the ITDR Admin Portal, then all roles mapped to the users who attempt to log in are removed. This can lock out the user during authentication. Therefore, test the SAML user provisioning and role mapping with a separate user so that you don't lock out your main account. Contact Zscaler Support if you are locked out of your account.
[]![Create an app in Okta](/downloads/itdr/authentication/saml-configuration/configuring-saml-okta-single-sign-on/zscaler-itdr-okta-create-application.png)
[]![Select SAML 2.0](/downloads/itdr/authentication/saml-configuration/configuring-saml-okta-single-sign-on/zscaler-itdr-okta-select-saml-2.png)
[]![Configure the app name](/downloads/itdr/authentication/saml-configuration/configuring-saml-okta-single-sign-on/zscaler-itdr-okta-config-app-name.png)
[]![Configure SAML settings](/downloads/itdr/authentication/saml-configuration/configuring-saml-okta-single-sign-on/zscaler-itdr-okta-config-saml-settings-2.png)
[]![Configure app type](/downloads/itdr/authentication/saml-configuration/configuring-saml-okta-single-sign-on/zscaler-itdr-okta-config-app-type-feedback.png)
[]![View SAML setup instructions](/downloads/itdr/authentication/saml-configuration/configuring-saml-okta-single-sign-on/zscaler-itdr-okta-view-saml-instructions.png)
[]![Download IdP metadata](/downloads/itdr/authentication/saml-configuration/configuring-saml-okta-single-sign-on/zscaler-itdr-okta-download-idp-metadata.png)
[]![Edit SSO URL and Audience URI](/downloads/itdr/authentication/saml-configuration/configuring-saml-okta-single-sign-on/zscaler-itdr-okta-edit-saml-settings.png)
[]![Configure SAML advance settings](/downloads/itdr/authentication/saml-configuration/configuring-saml-okta-single-sign-on/zscaler-itdr-okta-edit-saml-settings-advance.png)
[]![Assign the app to people or group](/downloads/itdr/authentication/saml-configuration/configuring-saml-okta-single-sign-on/zscaler-itdr-okta-assign-app-groups-1.png)
[]![Assign the app to a group](/downloads/itdr/authentication/saml-configuration/configuring-saml-okta-single-sign-on/zscaler-itdr-okta-assign-app-groups.png)
[]![Select the app in Okta](/downloads/itdr/authentication/saml-configuration/configuring-saml-okta-single-sign-on/zscaler-itdr-okta-select-app-saml-config.png)
[]![Edit SAML settings](/downloads/itdr/authentication/saml-configuration/configuring-saml-okta-single-sign-on/zscaler-itdr-okta-group-edit-saml-settings.png)
[]![Configure attribute statement](/downloads/itdr/authentication/saml-configuration/configuring-saml-okta-single-sign-on/zscaler-itdr-okta-group-attribute-statements.png)
[]![Configure group attribute statement](/downloads/itdr/authentication/saml-configuration/configuring-saml-okta-single-sign-on/zscaler-itdr-okta-attribute-statements-for-group-1.png)
[]![Configure group-based SAML login ](/downloads/itdr/authentication/saml-configuration/configuring-saml-okta-single-sign-on/zscaler-itdr-okta-group-based-saml-login.png)