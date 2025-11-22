# Configuring SAML for Microsoft Entra ID
Source: https://help.zscaler.com/itdr/configuring-saml-microsoft-entra-id
PDF: https://help.zscaler.com/pdf/com/en/1531729.pdf

Zscaler recommends that you use the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal) to configure primary and secondary [external identity providers (IdPs)](/zidentity/about-external-identity-providers). ZIdentity supports both SAML and OpenID configurations. Contact Zscaler Support to subscribe to ZIdentity.
This article provides information on how to configure SAML identity provider (IdP) single sign-on (SSO) for Azure Microsoft Entra ID.
Prerequisites
Make sure that the following prerequisites are met:
- You have access to the Microsoft Entra ID service with a privileged user role, preferably the Global Administrator role.
-
Browsers can access the following URLs:
- `*.azure.com`
- `*.illusionblack.com`
Remove any proxy restrictions on these URLs.
Configuring SAML
Follow these steps to configure SAML IdP for Entra ID:
- [Step 1: Configure an Enterprise Application in Microsoft Entra ID for SSO](#itdr-azure-ad-saml-sso-create-ea)
- [Step 2: Obtain the Microsoft Entra ID SAML Metadata](#itdr-azure-ad-saml-sso-download-idp-metadata)
- [Step 3: Create a SAML Provider for Microsoft Entra ID in the Zscaler ITDR Admin Portal](#itdr-azure-ad-saml-sso-config-saml-portal)
- [Step 4: Configure SSO for the Enterprise Application](#itdr-azure-ad-saml-sso-config-sso-enterprise-app)
- [Step 5: Add a User or Group Account to the Enterprise Application](#itdr-azure-ad-saml-sso-add-user-group)
- [(Optional) Step 6: Configure SAML Group Provisioning for Microsoft Entra ID](#itdr-azure-sso-group-saml-div)
- []Log in to the [Azure portal](http://portal.azure.com/) with the Global Administrator role.
-
Go to **Microsoft Entra ID** > **Enterprise applications**.
The **All applications** page opens.
-
Click **New application**.
[See image.](#itdr-image-create-new-enterprise-app)
The **Browse Azure AD Gallery** page opens.
-
Click **Create your own application**.
[See image.](#itdr-azure-sso-image-create-own-app)
-
In the **Create your own application** window:
- Enter a name for your application.
- Select **Integrate any other application you don't find in the gallery (Non-gallery)**.
[See image.](#itdr-azure-sso-image-config-own-app)
Don't click any of the recommended applications that might match your application name.
-
Click **Create**.
The enterprise application is created.
[See image.](#itdr-azure-sso-image-enterprise-app-created)
- []Open the [enterprise application](#itdr-azure-ad-saml-sso-create-ea) that you created.
-
In the left-side navigation, select **Single sign-on**.
[See image.](#itdr-azure-image-select-sso)
-
On the **Single sign-on** page, click **SAML**.
[See image.](#itdr-azure-image-select-saml-enterprise-app)
-
On the **SAML-based Sign-on **page, under **SAML Certificates**, copy the URL in **App Federation Metadata Url** and paste it into your browser to download the metadata XML file.
[See image.](#itdr-azure-image-copy-url-metadata)
- [][Configure SAML for SSO in the Zscaler ITDR Admin Portal](/itdr/configuring-saml-single-sign-on). In the **SAML Provider Details** window, make sure you unselect **Encryption** and **Sign Get Request**, and** **select **Use Dedicated Certificate**.
- Upload the [metadata XML](#itdr-azure-ad-saml-sso-download-idp-metadata) file that you downloaded.
- Obtain the SAML XML file from the ITDR Admin Portal. To learn more, see [Obtaining SAML Setup Information](/itdr/configuring-saml-single-sign-on#itdr-obtain-saml-setup-instn).
- []Log in to the [Azure portal](http://portal.azure.com/) with the Global Administrator role.
- Open the [enterprise application](#itdr-azure-ad-saml-sso-create-ea) that you created.
- In the left-side navigation, select **Single sign-on**.
-
On the **Set up Single Sign-On with SAML** page, click **Upload metadata file**.
[See image.](#itdr-azure-image-upload-metadata-file)
-
In the **Upload metadata file** window, browse and select the [metadata XML](#itdr-azure-ad-saml-sso-download-idp-metadata) file that you downloaded, and then click **Add**.
[See image.](#itdr-azure-image-browse-metadata-file)
-
In the **Basic SAML Configuration** window, click **Save**.
[See image.](#itdr-azure-image-save-saml-config)
-
[]On the **SAML-based Sign-on** page, under **SAML Certificates**, click **Download** for **Federation Metadata XML**.
[See image.](#itdr-azure-download-fed-metadata-xml-file)
The federation metadata XML file is downloaded.
- Log in to the ITDR Admin Portal.
- Go to **Settings** >** Users & Roles** > **IdP Providers**.
- Click the **Edit** icon for the [SAML SSO entry](#itdr-azure-ad-saml-sso-config-saml-portal) that you created for Microsoft Entra ID.
-
In the **SAML Provider Details** window, click **Upload** to upload the [federation metadata XML](#itdr-federation-metadata-xml) that was downloaded.
[See image.](#itdr-azure-upload-fed-metadata-xml-admin-portal)
- Click **Save**.
- []Log in to the [Azure portal](http://portal.azure.com/) with the Global Administrator role.
- Open the [enterprise application](#itdr-azure-ad-saml-sso-create-ea) that you created.
-
In the left-side navigation, select **Users and groups**, and then select **Add user/group**.
[See image.](#itdr-azure-image-add-user-groups)
- In the **Add Assignment** window:
-
Under **Users**, click **None Selected**.
The **Users** window opens.
-
Search for the user you want to assign to the enterprise application, and then click **Select**.
[See image.](#itdr-azure-image-select-user-group)
-
Verify if the user is selected, and click **Assign**.
[See image.](#itdr-azure-image-assign-user)
The **User Principal Name** of the [user](/itdr/about-users-roles#itdr-add-new-user-admin-portal) in the Azure portal must match the **Email** field of the user created in the ITDR Admin Portal.
After configuring the SSO, log out of the ITDR Admin Portal, and sign in with Azure Microsoft Entra ID SSO.
[See image.](#itdr-azure-image-login-page-azure-ad)
- []Log in to the [Azure portal](http://portal.azure.com/) with the Global Administrator role.
- Open the [enterprise application](#itdr-azure-ad-saml-sso-create-ea) that you created.
- In the left-side navigation, select **Single sign-on**.
-
On the **Set up Single Sign-On with SAML** page, under **Attributes & Claims**, click **Edit**.
[See image.](#itdr-azure-group-saml-attribute-claim-edit-image)
-
On the **Attributes & Claims** page, click **Add a group claim**.
[See image.](#itdr-azure-group-saml-add-group-claim-image)
-
In the **Group Claims** window:
- For **Which groups associated with the user should be returned in the claim?**, select **Groups assigned to the application**.
- For **Source attribute**, select **Group ID** from the drop-down menu.
[See image.](#itdr-azure-group-saml-config-group-claim-image)
- Click **Save**.
-
[]On the **Attributes & Claims** page, copy the **Claim name** for the `user.groups [All]` and `user.givenname `attributes.
[See image.](#itdr-azure-group-saml-copy-attributes-image)
-
In the Azure portal, click **Groups**.
[See image.](#itdr-azure-saml-group-groups-service-image)
-
[]Copy the **Object Id** for the groups you want to map users to the ITDR Admin Portal.
[See image.](#itdr-azure-group-saml-copy-objectid-image)
- Log in to the ITDR Admin Portal.
- Go to **Settings** >** Users & Roles** > **IdP Providers**.
-
Click the **Edit** icon for the [SAML SSO entry](#itdr-azure-ad-saml-sso-config-saml-portal) you created for Azure Microsoft Entra ID.
[See image.](#itdr-azure-group-saml-edit-sso-image)
-
In the **SAML Provider Details** window, under **Group-Based SAML Login**:
- Enable **Auto Create User**.
- For **SAML Response Group Attribute**, enter the [Claim name](#itdr-claim-name) you copied for the `user.groups [All]` attribute.
- For **SAML Response Name Attribute**, enter the [Claim name](#itdr-claim-name) you copied for the `user.givenname` attribute.
- Click **Add** to add a group and map the roles for each group.
- For **Group Name**, enter the [Object Id](#itdr-object-id) for a group you copied.
- Select a role for the group from the drop-down menu.
[See image.](#itdr-azure-group-saml-config-portal-image)
- Click **Save**.
[]![Create a new enterprise application](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-azure-active-directory-single-sign-on/zscaler-itdr-azure-saml-sso-create-new-app.png)
[]![Create your own application](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-azure-active-directory-single-sign-on/zscaler-itdr-azure-saml-sso-create-own-app.png)
[]![Configure own application](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-azure-active-directory-single-sign-on/zscaler-itdr-azure-saml-create-app-details.png)
[]![New app created](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-azure-active-directory-single-sign-on/zscaler-itdr-azure-saml-sso-create-new-app-created.png)
[]![Manage SSO option](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-azure-active-directory-single-sign-on/zscaler-itdr-azure-saml-sso-option.png)
[]![Select SAML for SSO](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-azure-active-directory-single-sign-on/zscaler-itdr-azure-saml-sso-saml-option.png)
[]![Copy app federation metadata URL](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-azure-active-directory-single-sign-on/zscaler-itdr-azure-saml-app-metadata-url.png)
[]![Add user or group accounts](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-azure-microsoft-entra-id-single-sign-on/zscaler-itdr-azure-saml-sso-add-user-groups-option.png)
[]![Select a user ](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-entra-id-single-sign-on/zscaler-itdr-azure-saml-sso-select-user.png)
[]![Assign a user](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-entra-id-single-sign-on/zscaler-itdr-azure-saml-assign-user.png)
[]![Upload metadata file](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-azure-active-directory-single-sign-on/zscaler-itdr-azure-saml-upload-metadat-file.png)
[]![Browse and add the metadata.xml file](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-azure-active-directory-single-sign-on/zscaler-itdr-azure-saml-browse_metadata-file.png)
[]![Save basic SAML configuration](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-azure-active-directory-single-sign-on/zscaler-itdr-azure-saml-sso-save-basic-saml-config.png)
[]![Download federation metadata XML](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-azure-active-directory-single-sign-on/zscaler-itdr-azure-saml-download-federation-metadata-xml.png)
[]![Upload IdP metadata.xml](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-azure-active-directory-single-sign-on/zscaler-itdr-azure-saml-upload-federation-xml.png)
[]![ITDR Admin Portal login page](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-entra-id-single-sign-on/zscaler-itdr-azure-saml-login-page.png)
[]![Edit SAML attributes and claims](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-entra-id-single-sign-on/zscaler-itdr-azure-saml-edit-attribute-claims.png)
[]![Add a group claim](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-entra-id-single-sign-on/zscaler-itdr-azure-saml-add-group-claim.png)
[]![Configure group claims](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-entra-id-single-sign-on/zscaler-itdr-azure-saml-save-group-claims-1.png)
[]![Copy claim names](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-entra-id-single-sign-on/zscaler-itdr-azure-saml-copy-user-given-name.png)
[]![SAML Groups option](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-entra-id-single-sign-on/zscaler-itdr-azure-saml-groups-option.png)
[]![Copy Object IDs of the groups](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-entra-id-single-sign-on/zscaler-itdr-azure-saml-copy-object-id.png)
[]![Edit SAML SSO](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-entra-id-single-sign-on/zscaler-itdr-azure-saml-edit-saml-sso.png)
[]![Configure group-based SAML login](/downloads/itdr/authentication/saml-configuration/configuring-saml-microsoft-entra-id-single-sign-on/zscaler-itdr-azure-saml-config-group-based-saml-login.png)