# Configuring SAML for Microsoft Azure Active Directory Single Sign-On
Source: https://help.zscaler.com/deception/configuring-saml-azure-active-directory-single-sign
PDF: https://help.zscaler.com/pdf/com/en/1531472.pdf

Zscaler recommends that you use the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal) to configure primary and secondary [external identity providers (IdPs)](/zidentity/about-external-identity-providers). ZIdentity supports both SAML and OpenID configurations. Contact Zscaler Support to subscribe to ZIdentity.
This article provides information on how to configure Microsoft Azure Active Directory (AD) as a SAML identity provider (IdP) for single sign-on (SSO).
Prerequisites
Make sure that the following prerequisites are met:
- You have access to the Azure AD service with a privileged user role, preferably the Global Administrator role.
-
Browsers can access the following URLs:
- `*.azure.com`
- `*.illusionblack.com`
Remove any proxy restrictions on these URLs.
Configuring SAML for Azure AD Single Sign-On
To configure Azure AD as a SAML IdP for SSO:
- [Step 1: Configure an Enterprise Application in Azure AD for SSO](#deception-azure-ad-saml-sso-create-ea)
- [Step 2: Obtain the Azure AD SAML Metadata](#deception-azure-ad-saml-sso-download-idp-metadata)
- [Step 3: Create a SAML Provider for Azure AD in the Zscaler Deception Admin Portal](#deception-azure-ad-saml-sso-config-saml-portal)
- [Step 4: Configure SSO for the Enterprise Application](#deception-azure-ad-saml-sso-config-sso-enterprise-app)
- [Step 5: Add a User or Group Account to the Enterprise Application](#deception-azure-ad-saml-sso-add-user-group)
- [(Optional) Step 6: Configure SAML Group Provisioning for Azure](#deception-azure-sso-group-saml-div)
- []Log in to the [Azure portal](http://portal.azure.com/) with the Global Administrator role.
-
Go to **Azure Active Directory** > **Enterprise applications**.
The **All applications** page opens.
-
Click **New application**.
[See image.](#deception-image-create-new-enterprise-app)
The **Browse Azure AD Gallery** page opens.
-
Click **Create your own application**
[See image.](#deception-azure-sso-image-create-own-app)
-
In the **Create your own application** window:
- Enter a name for your application.
- Select **Integrate any other application you don't find in the gallery (Non-gallery)**.
[See image.](#deception-azure-sso-image-config-own-app)
Don't click any of the recommended applications that might match your application name.
-
Click **Create**.
The enterprise application is created.
[See image.](#deception-azure-sso-image-enterprise-app-created)
- []Open the [enterprise application](#deception-azure-ad-saml-sso-create-ea) that you created.
-
In the left-side navigation, select **Single sign-on**.
[See image.](#deception-azure-image-select-sso)
-
On the **Single sign-on** page, click **SAML**.
[See image.](#deception-azure-image-select-saml-enterprise-app)
-
On the **SAML-based Sign-on **page, under **SAML Certificates**, copy the URL in **App Federation Metadata Url** and paste it into your browser to download the metadata XML file.
[See image.](#deception-azure-image-copy-url-metadata)
- [][Configure SAML for SSO in the Zscaler Deception Admin Portal](/deception/configuring-saml-single-sign). In the **SAML Provider Details** window, make sure you unselect **Encryption** and **Sign Get Request**, and** **select **Use Dedicated Certificate**.
- Upload the [metadata XML](#deception-azure-ad-saml-sso-download-idp-metadata) file that you downloaded.
- Obtain the SAML XML file from the Deception Admin Portal. To learn more, see [Obtaining SAML Setup Information](/deception/configuring-saml-single-sign#obtain-saml-setup-instn).
- []Log in to the [Azure portal](http://portal.azure.com/) with the Global Administrator role.
- Open the [enterprise application](#deception-azure-ad-saml-sso-create-ea) that you created.
- In the left-side navigation, select **Single sign-on**.
-
On the **Set up Single Sign-On with SAML** page, click **Upload metadata file**.
[See image.](#deception-azure-image-upload-metadata-file)
-
In the **Upload metadata file** window, browse and select the [metadata XML](#deception-azure-ad-saml-sso-download-idp-metadata) file that you downloaded, and then click **Add**.
[See image.](#deception-azure-image-add-metadata-file)
-
In the **Basic SAML Configuration** window, click **Save**.
[See image.](#deception-azure-image-save-saml-config)
-
[]On the **SAML-based Sign-on** page, under **SAML Certificates**, click **Download** for **Federation Metadata XML**.
[See image.](#deception-azure-download-fed-metadata-xml-file)
The federation metadata XML file is downloaded.
- Log in to the Deception Admin Portal.
- Go to **Settings** >** Users & Roles** > **IdP Providers**.
- Click the **Edit** icon for the [SAML SSO entry](#deception-azure-ad-saml-sso-config-saml-portal) that you created for Azure AD.
- In the **SAML Provider Details** window, click **Upload** to upload the [federation metadata XML](#deception-federation-metadata-xml) that was downloaded.
-
Click **Save**.
[See image.](#deception-azure-upload-fed-metadata-xml-admin-portal)
- []Log in to the [Azure portal](http://portal.azure.com/) with the Global Administrator role.
- Open the [enterprise application](#deception-azure-ad-saml-sso-create-ea) that you created.
-
In the left-side navigation, select **Users and groups**, and then select **Add user/group**.
[See image.](#deception-azure-image-add-user-groups)
- In the **Add Assignment** window:
-
Under **Users**, click **None Selected**.
The **Users** window opens.
- Search for the user you want to assign to the enterprise application.
-
Click **Select**.
[See image.](#deception-azure-image-select-user-group)
-
Click **Assign**.
[See image.](#deception-azure-image-assign-user)
The **User Principal Name** of the user in the Azure portal must match the **Email** field of the [user](/deception/about-users-roles#deception-add-new-user-admin-portal) created in the Deception Admin Portal.
After configuring the SSO, log out of the Deception Admin Portal, and sign in with Azure AD SSO.
[See image.](#deception-azure-image-login-page-azure-ad)
- []Log in to the [Azure portal](http://portal.azure.com/) with the Global Administrator role.
- Open the [enterprise application](#deception-azure-ad-saml-sso-create-ea) that you created.
- In the left-side navigation, select **Single sign-on**.
-
On the **Set up Single Sign-On with SAML** page, under **Attributes & Claims**, click **Edit**.
[See image.](#deception-azure-group-saml-attribute-claim-edit-image)
-
On the **Attributes & Claims** page, click **Add a group claim**.
[See image.](#deception-azure-group-saml-add-group-claim-image)
-
In the **Group Claims** window:
- For **Which groups associated with the user should be returned in the claim?**, select **Groups assigned to the application**.
- For **Source attribute**, select **Group ID** from the drop-down menu.
[See image.](#deception-azure-group-saml-config-group-claim-image)
- Click **Save**.
-
[]On the **Attributes & Claims** page, copy the **Claim name** for the **user.groups [All]** and **user.givenname** attributes.
[See image.](#deception-azure-group-saml-copy-attributes-image)
-
In the Azure portal, click **Groups**.
[See image.](#deception-azure-saml-group-groups-service-image)
-
[]Copy the **Object Id** for the groups you want to map users to in the Deception Admin Portal.
[See image.](#deception-azure-group-saml-copy-objectid-image)
- Log in to the Deception Admin Portal.
- Go to **Settings** >** Users & Roles** > **IdP Providers**.
-
Click the **Edit** icon for the [SAML SSO entry](#deception-azure-ad-saml-sso-config-saml-portal) you created for Azure AD.
[See image.](#deception-azure-group-saml-edit-sso-image)
- In the **SAML Provider Details** window, under **Group-Based SAML Login**:
- Enable **Auto Create User**.
- For **SAML Response Group Attribute**, enter the [Claim name](#deception-claim-name) you copied for the **user.groups [All]** attribute.
- For **SAML Response Name Attribute**, enter the [Claim name](#deception-claim-name) you copied for the **user.givenname** attribute.
-
Click **Add** to add a group and map the roles for each group.
- For **Group Name**, enter the [Object Id](#deception-object-id) for a group you copied.
- Select a role for the group from the drop-down menu.
[See image.](#deception-azure-group-saml-config-portal-image)
- Click **Save**.
[]![Create a new enterprise application in Azure](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-saml-sso-create-new-app.png)
[]![Create your own enterprise application](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-saml-sso-create-your-own-app.png)
[]![Create your own enterprise application](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-saml-sso-config-create-your-own-app.png?1679557133)
[]![Enterprise app created](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-saml-sso-new-enterprise-app-created.png)
[]![Select SSO for the enterprise app](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-saml-sso-select-sso.png)
[]![Select SAML for the enterprise app](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-saml-sso-select-saml.png)
[]![Copy URL to download the metadata XML file](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-saml-sso-download-metadata-file.png)
[]![Add user or groups to enterprise app](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-saml-sso-add-user-group.png)
[]![Search and select users and groups](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-saml-sso-select-user.png)
[]![Assign a user or group](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-saml-sso-assign-user.png?1679402839)
[]![Upload metadata file option in Azure AD](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-saml-sso-upload-metadata.png?1679544330)
[]![Add a metadata file](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-saml-sso-add-metadata.png)
[]![Save SAML configuration](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-saml-sso-save-SAML-config.png)
[]![Download federation metadata XML file from Azure](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-saml-sso-download-federation-metadata.png)
[]![Upload Azure Federation metadata xml file in Zscaler Deception Admin Portal](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-saml-sso-upload-federationmetadata-xml.png)
[]![Zscaler Deception login page with Azure AD SSO](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-saml-sso-log-in-page-portal.png)
[]![Edit attributes and claims](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-group-saml-attributes-claims-edit.png)
[]![Add a group claim](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-group-saml-add-group-claim.png)
[]![Configure group claims](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-group-saml-config-group-claim-2.png)
[]![Copy Claim name attributes](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-group-saml-copy-claim-name-attributes.png)
[]![Access Groups service in Azure](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-group-saml-access-groups-service.png)
[]![Copy Object ID for the groups](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-group-saml-copy-group-object-id.png)
[]![Edit Azure SAML SSO](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-group-saml-user-roles-edit-icon-2.png)
[]![Configure group SAML for Azure](/downloads/deception/authentication/saml-configuration/configuring-saml-azure-active-directory-single-sign/zscaler-deception-azure-group-saml-login-config.png)