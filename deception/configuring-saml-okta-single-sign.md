# Configuring SAML for Okta Single Sign-On
Source: https://help.zscaler.com/deception/configuring-saml-okta-single-sign
PDF: https://help.zscaler.com/pdf/com/en/1531359.pdf

Zscaler recommends that you use the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal) to configure primary and secondary [external identity providers (IdPs)](/zidentity/about-external-identity-providers). ZIdentity supports both SAML and OpenID configurations. Contact Zscaler Support to subscribe to ZIdentity.
This article provides information on how to configure Okta as a SAML identity provider (IdP) for single sign-on (SSO).
To configure Okta as a SAML IdP for SSO:
- [Step 1: Configure Okta for SSO](#config-okta-sso)
- [Step 2: Obtain the Identity Provider Metadata](#obtain-idp-metadata)
- [Step 3: Create a SAML Provider in the Zscaler Deception Admin Portal](#config-saml-admin-portal)
- [Step 4: Configure SAML Settings](#config-saml-settings)
- [Step 5: Assign Users or Groups Access via Okta](#assign-user-groups)
- [(Optional) Step 6: Configure SAML Group Provisioning for Okta](#deception-config-saml-group-okta)
- []Log in to the Okta portal as an administrator.
- Go to **Applications** > **Applications**.
- Click **Create App Integration**.
[See image.](#okta-create-app)
- In the **Create a new app integration** window, select **SAML 2.0**, and click **Next**.
[See image.](#select-saml-2-sso)
- On the **General Settings** tab, enter the **App name**, and click **Next**.
[See image.](#okta-app-name-general-settings)
- On the **Configure SAML **page, under **General**:
- **Single sign on URL**: Enter `https://``<Zscaler Deception Admin Portal instance name>``/saml/id/1/assert`.
- **Audience URI**: Enter `https://``<Zscaler Deception Admin Portal instance name>``/saml/id/1/metadata.xml`.
- **Name ID format**: Select **EmailAddress** from the drop-down menu.
- **Application username**: Select **Email** from the drop-down menu.
The **Single sign on URL** and **Audience URI** are placeholder values, which must be changed later.
[See image.](#okta-config-saml-settings)
- Click **Next**.
- Select **I'm an Okta customer adding an internal app**, and then click **Finish**.
[See image.](#okta-complete-app)
The application is created.
- []Go to **Applications** > **Applications**.
- Select the [Zscaler Deception](#config-okta-sso) application that you created.
- Click **Sign On**.
- Scroll down to the **SAML Setup** section, and click **View SAML setup instructions**.
[See image.](#okta-view-saml-setup-instructions)
- In the window that appears:
- Copy the IdP SSO URL and IdP Issuer details.
- Copy the content from **Optional** and save it as Metadata.xml.
[See image.](#okta-download-idp-metadata)
- [][Configure SAML for Single Sign-On in the Zscaler Deception Admin Portal](/deception/configuring-saml-single-sign).
Use the [Metadata.xml file](#obtain-idp-metadata) that you saved.
- Obtain the service provider entity ID and service provider assertion URL, and download the encryption certificate. To learn more, see [Obtaining SAML Setup Information](/deception/configuring-saml-single-sign#obtain-saml-setup-instn).
- []Log in to the Okta portal as an administrator.
- Go to **Applications** > **Applications**.
- Select the [Zscaler Deception](#config-okta-sso) application created.
- Click **General**.
- Scroll down to the **SAML Settings** section, and click **Edit**.
- In the **Edit SAML Integration wizard**, click **Next**.
- In the** SAML Settings** section, under **General**:
- **Single sign on URL**: Enter the [service provider assertion URL](#config-saml-admin-portal) that you obtained.
- **Audience URI (SP Entity ID)**: Enter the [service provider entity ID](#config-saml-admin-portal) that you obtained from the Deception Admin Portal.
[See image.](#okta-sso-uri-audience-uri)
- Scroll down to the **Show Advanced Settings** section:
- **Assertion Encryption**: Select **Encrypted** from the drop-down menu.
- **Encryption Certificate**: Upload the [encryption certificate](#config-saml-admin-portal) that you downloaded from the Deception Admin Portal.
[See image.](#okta-config-sso-advance-settings)
- []Go to **Applications** > **Applications**.
- Select the [Zscaler Deception](#config-okta-sso) application created.
- Click **Assignments**.
- Select **Assign** > **Assign to People **or **Assign to Groups** depending on whether you want to assign access to a single user or a group of users.
[See image.](#okta-assign-option)
- In the window that appears, click **Assign** for the user or group you want to select, and click **Save and Go Back**.
- Repeat the previous step for all users and groups you want to assign to Zscaler Deception, then click **Done**.
[]Before you configure SAML group provisioning using Okta as an IdP, make sure you create groups in Okta so that users within each group can be mapped to a role in the Deception Admin Portal.
- Log in to the Okta portal as an administrator.
- Go to **Applications** > **Applications**.
- Select the application that you created while configuring SAML for Zscaler Deception in Okta.
[See image.](#deception-saml-group-okta-select-app)
- Select the **General** tab.
[See image.](#deception-saml-group-okta-general)
- Scroll down to the **SAML Settings** section, and click **Edit**.
[See image.](#deception-saml-group-okta-edit-saml-settings)
- On the **Edit SAML Integration** page, click **Next**.
- Under **SAML Settings**:
- In** Attribute Statements**:
- **Name**: Enter `FullName`.
- **Name Format**: Select **Basic** from the drop-down menu.
- **Value**: Enter `String.join(" ", user.firstName, user.lastName)`.
[See image.](#deception-saml-group-okta-attribute-statements)
- In **Group Attribute Statements**:
- **Name**: Enter `Group`.
- **Name Format**: Select **Basic** from the drop-down menu.
- **Filter**: Select **Matches regex** from the drop-down menu, and then enter `.*` as the filter value.
[See image.](#deception-saml-group-okta-group-attribute-statement)
- Click **Next**, and then click **Finish**.
- Log in to the Deception Admin Portal.
- Go to **Settings** > **User & Roles** > **SSO**.
- Select the SAML configuration that you configured for your IdP.
- In the **SAML Provider Details **window, under the **Group-Based SAML Login** section:
- **Auto Create User**: Enable to make sure the users in the specified groups are automatically created in the Deception Admin Portal.
- **SAML Response Group Attribute**: Enter `Group`.
- **SAML Response Name Attribute**: Enter `FullName`.
- Click **Add** to add a group and select the roles for each group.
- Enter the group name.
- Select a role for the group from the drop-down menu.
[See image.](#deception-saml-group-okta-login)
- Click **Save**.
If the group attribute specified is not part of the SAML assertion when logging in or doesn't match one of the groups specified in the Deception Admin Portal, then all roles mapped to the users who attempt to log in are removed. This can lock out the user during authentication. Therefore, test the SAML user provisioning and role mapping with a separate user so that you don't lock out your main account. Contact the Zscaler Support if you are locked out of your account.
[]![Create an application to configure Okta for SSO](/downloads/deception/authentication/saml-configuration/configuring-saml-okta-single-sign/zscaler-deception-okta-create-application.png)
[]![Select SAML 2.0 for SSO](/downloads/deception/authentication/saml-configuration/configuring-saml-okta-single-sign/zscaler-deception-okta-select-saml-2.png)
[]![Configure application name in the General Settings page](/downloads/deception/authentication/saml-configuration/configuring-saml-okta-single-sign/zscaler-deception-okta-application-general-settings.png)
[]![Configure SAML Settings ](/downloads/deception/authentication/saml-configuration/configuring-saml-okta-single-sign/zscaler-deception-okta-application-config%20-saml.png)
[]![Complete application creation in Okta](/downloads/deception/authentication/saml-configuration/configuring-saml-okta-single-sign/zscaler-deception-okta-application-feedback.png)
[]![View SAML setup instructions](/downloads/deception/authentication/saml-configuration/configuring-saml-okta-single-sign/zscaler-deception-okta-application-view-saml-setup-info.png)
[]![Download IdP metadata information](/downloads/deception/authentication/saml-configuration/configuring-saml-okta-single-sign/zscaler-deception-okta-application-idp-metadata-info.png?1657635496)
[]![Configure SSO URL and Audience URI](/downloads/deception/authentication/saml-configuration/configuring-saml-okta-single-sign/zscaler-deception-okta-application-config%20-sso-audience-uri.png)
[]![Configure SAML advance settings](/downloads/deception/authentication/saml-configuration/configuring-saml-okta-single-sign/zscaler-deception-okta-application-config%20-advanced-settings.png)
[]![Assign option in the Okta Assignment page](/downloads/deception/authentication/saml-configuration/configuring-saml-okta-single-sign/zscaler-deception-okta-application-assign-option.png)
[]![Select the Okta application](/downloads/deception/authentication/saml-configuration/configuring-saml-group-provisioning-okta/zscaler-deception-saml-group-okta-select-app.png)
[]![General settings for SAML Okta application](/downloads/deception/authentication/saml-configuration/configuring-saml-group-provisioning-okta/zscaler-deception-saml-group-okta-select-app-general.png)
[]![Edit SAML settings in Okta](/downloads/deception/authentication/saml-configuration/configuring-saml-group-provisioning-okta/zscaler-deception-saml-group-okta-saml-settings-edit.png)
[]![Configure attribute statement settings in Okta](/downloads/deception/authentication/saml-configuration/configuring-saml-group-provisioning-okta/zscaler-deception-saml-group-okta-attribute-statement.png)
[]![Configure group attribute statements in Okta](/downloads/deception/authentication/saml-configuration/configuring-saml-okta-single-sign/zscaler-deception-saml-group-okta-group-attribute-statement.png)
[]![Configure group-based SAML login](/downloads/deception/authentication/saml-configuration/configuring-saml-group-provisioning-okta/zscaler-deception-saml-group-okta-saml-login.png)