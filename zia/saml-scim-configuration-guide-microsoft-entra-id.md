# SAML & SCIM Configuration Guide for Microsoft Entra ID
Source: https://help.zscaler.com/zia/saml-scim-configuration-guide-microsoft-entra-id
PDF: https://help.zscaler.com/pdf/com/en/1400361.pdf

This guide illustrates how to configure Microsoft Entra ID (formerly Azure Active Directory) as the identity provider (IdP) for the Zscaler service. To learn more about the steps in the Microsoft Entra admin center, refer to the [Microsoft Entra ID documentation](https://learn.microsoft.com/en-us/entra/identity/saas-apps/zscaler-tutorial).
Zscaler and Microsoft are technology partners. To learn more about the Zscaler and Microsoft Entra ID integration, see the [Zscaler and Microsoft Entra ID Passwordless Deployment Guide](/zscaler-technology-partners/zscaler-and-microsoft-entra-ID-passwordless-deployment-guide).
Prerequisites
Although you can set some configurations with a free Microsoft Entra subscription, a premium subscription is highly recommended to avoid restricted functionality.
Ensure that you have the following before you start configuring Microsoft Entra ID as your IdP:
- Premium Microsoft Entra subscription
- Existing Microsoft Entra Account
- [Zscaler cloud name](/zia/what-my-cloud-name-zia)
Configuring Microsoft Entra ID as the IdP for the Zscaler Service
Zscaler recommends using Security Assertion Markup Language (SAML) single sign-on (SSO) for user authentication and System for Cross-domain Identity Management (SCIM) for user provisioning.
To configure SAML SSO and SCIM provisioning with Microsoft Entra ID:
- [1. Add the Zscaler cloud application in the Microsoft Entra admin center.](#adding-zscaler-cloud-application)
- [2. Configure SAML SSO in the Microsoft Entra admin center.](#configure-saml-entra)
- [3. Add Microsoft Entra ID as the IdP for the Zscaler service in the ZIA Admin Portal.](#add-idp)
- [4. Enable SAML SSO in the ZIA Admin Portal.](#configuring-saml-sso-zscaler-admin-portal)
- [5. Configure SCIM provisioning in the ZIA Admin Portal.](#conf-scim)
- [6. Configure SCIM provisioning in the Microsoft Entra admin center.](#configuring-scim-entra)
- [7. Configure the Zscaler Authentication Exemptions list in the ZIA Admin Portal.](#zscaler-authentication-exemptions-list)
- [8. Assign users to the Zscaler cloud application in the Microsoft Entra admin center.](#assigning-users-zscaler-cloud-application)
Testing the SAML and SCIM Configuration
[]When your configuration is complete, you can test your work on another device.
Test the configuration with one or both of the following methods:
- [Test the SAML Configuration by Logging Out of the Zscaler Service](#test-saml-1)
- [Test the SAML Configuration with the Test URL](#test-saml-2)
Test the SCIM configuration by doing the following:
- [1. Initiate a provision on demand for your application in Microsoft Entra ID.](#provision-on-demand)
- 2. After provisioning successfully, in the ZIA Admin Portal, go to **Administration** > **User Management**. You should see a complete list of the users and groups added to your user database.
Troubleshooting
If any errors occur, see [Troubleshooting SAML](/zia/saml-troubleshooting-guidelines) to troubleshoot browser settings and SAML error codes.
[]This testing method only applies if you're forwarding traffic using Proxy Auto-Configuration (PAC) files, Generic Routing Encapsulation (GRE) tunnels, or IPSec tunnels, and you've enabled Enforce Authentication for the location or sublocation.
- On the device, browse to [ip.zscaler.com](http://ip.zscaler.com).
- If you are already logged in to the Zscaler service, click **Logout**. Otherwise, ensure that your traffic is being forwarded to the Zscaler service.
- Browse to a website. You are redirected to Microsoft Entra ID and prompted to log in.
- Log in using your Microsoft Entra credentials, and you are automatically redirected to the original URL request.
- Go to [ip.zscaler.com](http://ip.zscaler.com). The status window shows the username indicating that authentication was successful.
-
[]On the device, enter `https://login.``<Zscaler Cloud Name>``/clstart?version=1&_domain=``<Tenant Domain>``&redrurl=https://mobile.``<Zscaler Cloud Name>`. To learn how you can find your cloud name, see [What Is My Cloud Name for ZIA?](/zia/what-my-cloud-name-zia) The <Tenant Domain> is your organization's domain that is used to log in to the Zscaler service. For example, if you logged in to the Zscaler service with the username `admin@``zscaler.com`, then zscaler.com is your <Tenant Domain>.
Given an organization on the `zscalerbeta.net` cloud with `zscaler.com` as the <Tenant Domain>, the completed URL would be:
``https://login.``zscalerbeta.net``/clstart?version=1&_domain=``zscaler.com``&redrurl=https://mobile.``zscalerbeta.net``
- If you are redirected to the ZIA Admin Portal, the SAML configuration is successful. You might be prompted to authenticate with your IdP.
- []Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
-
In the left-side navigation, go to **Identity **> **Applications **> **Enterprise applications**.
[See image.](#seeimage1c)
-
Click **New application**.
[See image.](#seeimage1d)
The **Browse Microsoft Entra Gallery** page appears.
-
On the **Browse Microsoft Entra Gallery** page, enter `zscaler internet access` in the search bar, then click the Zscaler application with your cloud name. Your cloud name depends on the URL you use to log in to the Zscaler service. For example, if you log in to https://admin.zscalerbeta.net, then your cloud name is Zscaler Beta and your application name is Zscaler Internet Access ZSBeta. This guide uses the Zscaler Internet Access ZSBeta application as an example.
[See image.](#seeimage1e)
-
Click **Create**.
[See image.](#seeimage1f)
The Microsoft Entra service displays a notification that the Zscaler cloud application was added.
[]****![Screenshot highlighting the Enterprise applications menu for Microsoft Entra ID](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-navigation-enterprise-apps.png)
****
[]****![Screenshot highlighting the New application button on the Enterprise applications | All applications page.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-new-enterprise-app.png)
****
[]****![Screenshot highlighting the search bar and the Zscaler Beta application on the Browse Microsoft Entra Gallery page](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-search-zsbeta.png)
****
[]****![Screenshot highlighting the Create button for the application](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-create-ziazsbeta.png)
****
-
[]In the left-side navigation for the Zscaler cloud application, click **Single sign-on**.
[See image.](#seeimage2a)
-
Select **SAML**.
[See image.](#seeimage2b)
-
In the **Basic SAML Configuration **section, click **Edit**.
[See image.](#seeimage2c)
The **Basic SAML Configuration** window appears.
-
In the **Basic SAML Configuration** window:
-
**Identifier (Entity ID)**: Enter the default identifier based on your added Zscaler cloud application. It's typically <Zscaler Cloud Name>. The <Zscaler Cloud Name> depends on the URL you use to log in to the Zscaler service. For example, if you log in to https://admin.zscalerbeta.net, then the identifier is zscalerbeta.net.
If you have more than one organization instance on the same Zscaler cloud, you must use an org-specific entity ID. You can see the org-specific entity ID for your instance in the ZIA Admin Portal while [adding or editing an identity provider](/zia/adding-identity-providers).
The org-specific entity ID is formatted like the following example:
`https://login.zscalerbeta.net/sfc_sso/3829920`
-
**Reply URL (Assertion Consumer Service URL)**: Enter the following Zscaler SSO URL:
`https://login.<Zscaler Cloud Name>:443/sfc_sso`
The <Zscaler Cloud Name> depends on the URL you use to log in to the Zscaler service. For example, if you log in to https://admin.zscalerbeta.net, then the Zscaler SSO URL is https://login.zscalerbeta.net/sfc_sso.
- **Sign on URL**: Enter the **Reply URL (Assertion Consumer Service URL)**. In this example, it's https://login.zscalerbeta.net:443/sfc_sso.
- **Relay State**: Leave this field blank.
- **Logout URL**: Leave this field blank.
[See image.](#seeimage2d)
- Click **Save** and exit the window.
-
In the **Attributes & Claims **section, click **Edit**.
[See image.](#attributes-claims)
- Click **Add a group claim**.
- In the **Group Claims **window:
-
If the groups you are assigning exist in Microsoft Entra ID locally:
- Select **Groups assigned to the application**.
- For **Source attribute**, select **Cloud-only group display names**.
[See image.](#group-claim-local)
-
If the groups you are assigning are from an on-premises active directory (AD):
- Select **Groups assigned to the application**.
- For **Source attribute**, select **sAMAccountName**.
[See image.](#group-claim-ad)
- Click **Save**.
- Click **Add new claim**.
-
On the **Manage claim **page:
- **Name**: Enter `Department` (case sensitive).
- **Source**: Select **Attribute**.
- **Source attribute**: Enter `user.department` (case sensitive).
[See image.](#add-new-claim)
-
Click **Save**.
When you are finished, check the **Attribute & Claims **section to ensure that you have configured the **Department **and **groups** attributes properly.
[See image](#attributes-claims-example)
-
In the **SAML Certificates **section, download **Certificate (base64)**. You need this certificate file when you [add Microsoft Entra ID as the IdP for the Zscaler service](/zia/saml-scim-configuration-guide-microsoft-entra-id#add-idp).
[See image.](#seeimage2f)
Ensure that the certificate file name:
- Has a **.**`pem` extension (e.g., rename it to Entra.pem). The Zscaler service only accepts certificates with the .`pem` extension.
- Contains only one dot (".").
[See image.](#seeimage2f0)
By default, Windows hides extensions for known file types.
- [Change the Windows Folder Properties to View and Edit Extensions](#pem-instructions)
-
In the **Set up Zscaler Beta **section, copy the **Login URL**. You need this URL when you [add Microsoft Entra ID as the IdP for the Zscaler service](/zia/saml-scim-configuration-guide-microsoft-entra-id#add-idp).
[See image.](#seeimage2g)
(Optional) for [Seamless SSO](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-sso-how-it-works), you must append the [domain hint](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/configure-authentication-for-federated-users-portal) `?whr=contoso.com` to the end of the **Login URL**. The URL must be similar to the following example:
`https://login.microsoftonline.com/1ab234c5-def6-789a-bcde-0f1abc23456d/saml2?whr=contoso.com`
[]![Image of the Attributes & Claims Edit button](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-attributes-claims-edit.png)
[]![Image of the configuration settings for a group claim with local groups](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-group-claim-local.png)
[]![Image of the configuration settings for a group claim with an on-premises AD](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-group-claim-ad.png)
[]![Image of the Manage Claim page](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-add-new-claim.png)
[]![Image of the Department and groups attributes](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-attributes-claims-example.png)
[]****![Screenshot highlighting the Single sign-on menu for the added Zscaler cloud application](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-click-SSO.png)
****
[]****![Screenshot highlighting SAML for the single sign-on method](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-click-saml.png)
****
[]![Edit icon for the the Basic SAML Configuration section](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/Azure-Basic-SAML-Configuration-Section-Edit-Icon.png)
[]![Screenshot of the SAML configuration in the Basic SAML Configuration window.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-basic-saml-configuration.png)
[]****![Screenshot highlighting the Download button for the base64 Azure signing certificate in the SAML Signing Certificate section.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-click-download-saml-certificate.png)
****
[]****![Screenshot of the Microsoft Entra signing certificate renamed with the .pem extension.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-cert-pem.png)
****
[]![Screenshot highlighting the Copy icon for the Login URL under Configuration URLs.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-copy-login-URL.png)
- []Start Windows 10 Control Panel.
- Go to **Appearance & Personalization** > **File Explorer Options**.
- When the **File Explorer Options** window appears, click the **View **tab.
-
In the **Advanced settings: **section, deselect **Hide extensions for known file types** to view extensions.
[See image.](#seeimage3iv)
- Rename the certificate to change the extension.
[]![The Hide extensions for known file types deselected in the View tab of the Windows File Explorer Options.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/Windows-File-Explorer-Options-View-Hide-extensions-for-known-file-types.png)
- []Go to **Administration **>** Authentication Settings**.
- Under **Authentication Frequency**,** **select how often users are required to authenticate to the Zscaler service. To learn more, see [About Authentication Profile](/zia/about-authentication-profile#authentication-frequency). If you select **Custom**, the **Custom Authentication Frequency (days)** field appears. In this field, specify 1 to 180 days.
-
Under** Authentication Type**, select **SAML**.
[See image.](#seeimage-2c)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![Screenshot highlighting the SAML option under Authentication Type on the Authentication Profile page.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-SAML-auth-type.png)
[]To configure the Zscaler Authentication Exemptions list and enable users access to Microsoft Entra ID in the ZIA Admin Portal:
- Go to **Administration **>** Advanced Settings**.
-
In the **Authentication Exemptions** section, enter the following exceptions in **Exempted URLs**, and click **Add Items**:
- `login.windows.net`
- `login.microsoftonline.com`
- `.windowsazure.com`
- `aadcdn.msauth.net`
- `aadcdn.msftauth.net`
[See image.](#seeimage5b)
This option only applies to user traffic from known locations. For more information, see [Exempting URLs and Cloud Apps from Authentication](/zia/exempting-urls-cloud-apps-authentication).
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
If you are using PAC files, enter the following exceptions in the [PAC file](/zia/using-default-pac-files-forward-traffic-zia) exemption list. Otherwise, the authentication fails.
if (shExpMatch(host, "login.windows.net") || shExpMatch(host, "login.microsoftonline.com") || shExpMatch(host, "*.windowsazure.com"))
return "DIRECT";
[]![Screenshot highlighting the configured Exempted URLs field in the Authentication Exemptions section.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-Advanced-Settings-Authentication-Exemptions-Exempted-URLs.png)
[]To learn more about SCIM provisioning in Microsoft Entra ID, refer to the [Microsoft Entra ID documentation](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/use-scim-to-provision-users-and-groups).
-
In the Microsoft Entra admin center, in the left-side navigation of the Zscaler cloud application, click **Provisioning**.
[See image.](#seeimage6a)
-
On the provisioning **Overview** page, click **Get started**.
[See image.](#seeimage6a0)
The **Provisioning **page appears.
-
For **Provisioning Mode**, select **Automatic**.
[See image.](#seeimage6b)
-
Under **Admin Credentials**:
- **Tenant URL**: Enter the **Base URL** you copied previously in [Configure SCIM provisioning in the ZIA Admin Portal](#conf-scim).
- **Secret Token**: Enter the **Bearer Token** you copied previously in [Configure SCIM provisioning in the ZIA Admin Portal](#conf-scim).
-
Click **Test Connection**. Microsoft Entra ID connects to the SCIM endpoint. If the connection is successful, the Microsoft Entra service displays a notification that the credentials are authorized.
[See image.](#seeimage6c)
If the connection fails, error information is displayed. Resolve any errors before moving forward.
[See image.](#seeimage6d)
- Click **Save** to save your credentials.
- Under **Mappings**:
-
Click the groups attribute mapping link (e.g., Provision Azure Active Directory Groups). The **Attribute Mapping** page appears.
[See image.](#provisioning-page-mappings-group)
- On the **Attribute Mapping** page, review the attributes that are synchronized from Microsoft Entra ID to your application.
-
Verify the group attribute mappings as listed in the following table. If needed, change them by clicking **Edit **on an existing attribute or by clicking **Add New Mapping**.
| Zscaler Attribute (Target Attribute) | Microsoft Entra Attribute (Source Attribute) | Match Objects Using This Attribute |
| ------------------------------------ | -------------------------------------------- | ---------------------------------- |
| displayName | displayName | Yes |
| members | members |  |
| externalId | objectId |  |
[See image.](#seeimage6e)
- Click **Ok **to save the attribute parameters.
- Click **Save** to save the attribute mapping changes.
- Return to the **Provisioning **page.
- Under **Mappings**:
-
Click the users attribute mapping link (e.g., Provision Azure Active Directory Users). The **Attribute Mapping** page appears.
[See image.](#provisioning-page-mappings-users)
- On the **Attribute Mapping** page, review the attributes that are synchronized from Microsoft Entra ID to your application.
-
Verify the users attribute mappings as listed in the following table. If needed, change them by clicking **Edit **on an existing attribute or by clicking **Add New Mapping**.
| Zscaler Attribute (Target Attribute) | Microsoft Entra Attribute (Source Attribute) | Match Objects Using This Attribute |
| ------------------------------------ | -------------------------------------------- | ---------------------------------- |
| userName | userPrincipalName | Yes |
| externalId | objectId |  |
| active | Switch([IsSoftDeleted], , "False", "True", "True", "False") |  |
| name.familyName | surname |  |
| name.givenName | givenName |  |
| displayName | displayName |  |
| urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | department |  |
[See image.](#seeimage6e0)
- (Optional) If you use the Workflow Automation Admin Portal, add and map additional user attributes that Workflow Automation uses.
- [1. Add Additional User Attributes](#add-additional-user-attributes-WA)
- [2. Map Additional User Attributes](#map-additional-user-attributes-WA)
-
Under **Settings**:
- **Send an email notification when a failure occurs**: (Optional) Select this and provide an email to receive a notification when there is a provisioning failure.
- **Prevent accidental deletion**: (Optional) Selecting this option allows you to set an **Accidental deletion threshold**. When the option is enabled, deleting a number of groups and users over the threshold requires approval from an admin.
- **Scope**: (Optional) Select **Sync only assigned users and groups**. Zscaler recommends enabling this setting. To learn more about assigning users, see [Assign Users to the Zscaler Cloud Application](#assigning-users-zscaler-cloud-application).
[See image.](#seeimage6g)
- For **Provisioning Status**, select **On.**
- Click **Save** to start the Microsoft Entra provisioning service.
- Return to the provisioning **Overview** page.
-
On the provisioning **Overview** page, review the current cycle status, provisioning details, and technical information for the Microsoft Entra provisioning service.
[See image.](#seeimage6h)
[]The following table lists the additional user attributes to add for Workflow Automation:
| Name | Type | Referenced Object Attribute |
| ---- | ---- | --------------------------- |
| urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager.value | Reference | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User |
| urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:employeeNumber | String |  |
| title | String |  |
| emails[type eq "work"].value | String |  |
| preferredLanguage | String |  |
| addresses[type eq "work"].formatted | String |  |
| addresses[type eq "work"].streetAddress | String |  |
| addresses[type eq "work"].locality | String |  |
| addresses[type eq "work"].region | String |  |
| addresses[type eq "work"].postalCode | String |  |
| addresses[type eq "work"].country | String |  |
| addresses[type eq "home"].country | String |  |
| phoneNumbers[type eq "work"].value | String |  |
| phoneNumbers[type eq "mobile"].value | String |  |
| phoneNumbers[type eq "fax"].value | String |  |
To add additional user attributes:
-
Under the existing attribute mappings that are displayed, select the **Show advanced** **options** checkbox. The page expands to display additional information.
[See image.](#attribute-mapping-page-show-advanced-options)
-
Click the **Edit attribute list** link (e.g., Edit attribute list for Zscaler). The **Edit Attribute List** page appears, displaying the existing user attributes. An empty row appears at the bottom of the list.
[See image.](#edit-attribute-list-page-users-attributes)
-
In the empty row, add the information for an additional user attribute:
Add the user attributes one at a time. When you begin to enter a name in the empty row, an additional empty row appears below that row. Add all the user attributes using the information that is provided in the table above.
- **Name**: Enter the name of the user attribute. When you begin to enter a name, an additional blank row appears below that row.
- **Type**: From the drop-down menu, select the user attribute type. Types are **Binary**, **Boolean**, **DateTime**, **Integer**, **Reference**, and **String**. The user attributes for Workflow Automation use either **String** or **Reference** as the type.
- **Referenced Object Attribute**: From the drop-down menu, select the referenced object attribute for the user attribute.
- Click **Save**. A dialog window appears, asking if you are sure you want to make these changes.
- Click **Yes**. The attributes are added. You can now map these user attributes.
[]The following table lists the mapping information to use when mapping the additional user attributes you previously added:
| Mapping Type | Microsoft Entra Attribute (Source Attribute) | Zscaler Attribute (Target Attribute) | Match Objects Using This Attribute | Apply This Mapping |
| ------------ | -------------------------------------------- | ------------------------------------ | ---------------------------------- | ------------------ |
| Direct | jobTitle | title | No | Always |
| Direct | mail | emails[type eq "work"].value | No | Always |
| Direct | preferredLanguage | preferredLanguage | No | Always |
| Direct | physicalDeliveryOfficeName | addresses[type eq "work"].formatted | No | Always |
| Direct | streetAddress | addresses[type eq "work"].streetAddress | No | Always |
| Direct | city | addresses[type eq "work"].locality | No | Always |
| Direct | state | addresses[type eq "work"].region | No | Always |
| Direct | postalCode | addresses[type eq "work"].postalCode | No | Always |
| Direct | country | addresses[type eq "work"].country | No | Always |
| Direct | extension_d46aad061f2b47f497418d1ff465699b_HomeCountry | addresses[type eq "home"].country | No | Always |
| Direct | mobile | phoneNumbers[type eq "work"].value | No | Always |
| Direct | mobile | phoneNumbers[type eq "mobile"].value | No | Always |
| Direct | facsimileTelephoneNumber | phoneNumbers[type eq "fax"].value | No | Always |
| Direct | employeeId | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:employeeNumber | No | Always |
| Direct | manager | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager.value | No | Always |
To map additional user attributes:
-
Under the existing attribute mappings that are displayed, click **Add New Mapping**. The **Edit Attribute** page appears.
[See image.](#attribute-mapping-page-add-new-mapping-link)
-
On the **Edit Attribute** page:
Add the user attribute mappings one at a time. With attribute mappings, you control how attributes are populated in a non-Microsoft SaaS application. Map all the user attributes using the information that is provided in the table above.
- **Mapping type**: From the drop-down menu, select the mapping type. Mapping types are:
- **Direct**: The target attribute is populated with the value of an attribute of the linked object in Microsoft Entra ID. All the user attribute mappings for Workflow Automation use **Direct **for this field.
- **Constant**: The target attribute is populated with a specific string you specified.
- **Expression**: The target attribute is populated based on the result of a script-like expression.
- **None**: The target attribute is left unmodified.
- **Source attribute**: From the drop-down menu, select the Microsoft Entra Attribute (source attribute) for the mapping.
- **Target attribute**: From the drop-down menu, select the Zscaler attribute (target attribute) for the mapping.
- **Match objects using this attribute**: From the drop-down menu, select **Yes** or **No**. If you select **Yes**, this mapping is used to uniquely identify users between the source and target systems. All the user attribute mappings for Workflow Automation use **No** for this field.
- **Apply this mapping**: From the drop-down menu, select when to apply this mapping. Options are **Always**, **Only if the attribute contains multiple values**, and **Only during object creation**. All the user attribute mappings for Workflow Automation use **Always** for this field.
[See image.](#edit-attribute-page-data-populated)
- Click **Ok**.
- Click **Save**. A dialog window appears, asking if you are sure you want to make these changes.
- Click **Yes**. The attribute mapping is added and is listed in the **Attribute Mappings** section of the **Attribute Mapping** page.
- Return to the **Provisioning** page.
[]![Provisioning menu for added Zscaler cloud application](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-Azure-Zscaler-Cloud-Application-Provisioning-Menu.png)
[]![Image of the Provisioning page in Microsoft Entra ID ](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-scim-get-started.png)
[]![Screenshot of the configured Provisioning Mode in the Provisioning window.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-provisioning-mode.png)
[]![Screenshot of the Azure AD successful notification for testing the credentials](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/azure-scim-text-connection-notification.png)
[]![Screenshot of the Admin Credentials section in the Provisioning window.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-admin-credentials.png)
[]![Microsoft Entra ID - Provisioning Page](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-Entra-ID-Provisioning-Page-Group-Mappings.png)
[]![Attribute Mapping window in Microsoft Entra ID](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-groups-mapping-example.png)
[]![Microsoft Entra ID - Provisioning Page](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-Entra-ID-Provisioning-Page-Users-Mappings.png)
[]![Attribute Mapping Window Showing the User Attribute Mappings in Microsoft Entra ID ](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-users-mapping-example.png)
[]![Microsoft Entra ID - Attribute Mapping - Show Advanced Options checkbox selected ](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-Entra-ID-Attribute-Mapping-show-advanced-options.png)
[]![Edit Attribute List Page - Blank Row for Adding New Attribute](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-Entra-ID-Edit-Attribute-List-Page.png)
[]![Microsoft Entra ID - Attribute Mapping - Add New Mapping Link ](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-Entra-ID-Attribute-Mapping-Add-New-Mapping-Link.png)
[]![Microsoft Entra ID - Edit Attribute Page ](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-Entra-ID-Edit-Attribute-Page.png)
[]![Image of the provisioning Settings section](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-provisioning-settings-section.png)
[]![Viewing Provisioning Service Status and Details in Microsoft Entra ID](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-provisioning-overview-page-zsbeta.png)
[]For Microsoft Entra users to authenticate through the Zscaler service, you must assign Microsoft Entra users or groups to the Zscaler cloud application.
-
In the left-side navigation of the Zscaler cloud application, click **Users and groups**.
[See image.](#seeimage7a)
-
Click **Add user/group**.
[See image.](#seeimage7b)
The **Add Assignment** window appears.
-
In the **Add Assignment** window, under **Users and groups**, click **None Selected**.
[See image.](#seeimage7c)
The **Users and groups** window appears.
-
In the **Users and groups** window, select the users or groups you want to assign to the Zscaler cloud application, and click **Select**.
To ensure that Microsoft Entra ID sends group memberships to Zscaler, you must assign groups to the enterprise application.
[See image.](#seeimage7d)
-
In the **Add Assignment** window, click **Assign**.
[See image.](#seeimage7e)
[]![Screenshot highlighting the Users and groups menu for the added Zscaler cloud application.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/Azure-Zscaler-cloud-application-User-and-groups-menu.png)
[]![Screenshot highlighting the Add user button on the Users and groups page.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-add-user-group-zsbeta.png)
[]![Screenshot highlighting the Users and groups button in the Add Assignment window.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-add-assignment.png)
[]![Screenshot of the selected users in the Users and groups window.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-select-users-groups-example.png)
[]![Screenshot highlighting the Assign button in the Add Assignment window.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-assign-users-groups.png)
- []Sign in to the [Microsoft Entra admin center](http://entra.microsoft.com/).
- In the left-side navigation, go to **Applications > Enterprise applications**.
- On the **Enterprise applications **page, locate the application for which you want to initiate the provision on demand.
-
Click the application.
The **Overview** page for the application appears.
-
In the left-side navigation, click **Provisioning**.
The provisioning **Overview** page for the application appears.
-
Click **Provision on demand**.
To learn more about provision on demand, refer to the [Microsoft Entra ID documentation](https://docs.microsoft.com/en-us/azure/active-directory/app-provisioning/provision-on-demand).
[See image.](#seeimage8a0)
-
In the **Provision on demand** page, search for a user.
This user must have already been assigned to the cloud application. This user can be a part of the initial payload. If you select a user that is part of the initial payload, then this user is skipped over when the initial payload is provisioned because they were already provisioned on demand. To learn more, see [Assigning Users to the Zscaler Cloud Application](#assigning-users-zscaler-cloud-application).
[See image.](#seeimage8b)
- Select the user for which you want to provision.
-
Click **Provision**.
The provision on demand process is initiated. After the process is completed, the **Provision on demand** page appears, displaying the results from the 5 steps that the provisioning service takes when provisioning a user. If a step is successful, a green check mark appears next to the step. If a step is not successful, then a red circle with an X appears next to the step.
[See image.](#seeimage8c)
-
On the **Provision on demand** page, review the results.
If there are no failures in the steps, then the provisioning configuration for your application has been properly configured. If there are failures, fix the issues that are listed and retry the provision on demand process again. Focus on the **Perform action** step. To understand why the failure occurred, click the **View Details** link located under each step.
For failures that you cannot fix, contact either Microsoft Entra Support or Zscaler Support for assistance.
[See image.](#seeimage8d)
- Verify that the user has been added to your database in the ZIA Admin Portal. In the ZIA Admin Portal, go to **Administration** >** User Management**.
- []Go to **Administration** > **Authentication Settings**.
- Click the **Identity Providers **tab.
- Click **Add IdP**.
If you have an existing IdP configuration, the **What do you want to do?** window appears. Select **Add another SAML IdP for a subset of users or locations** and then **Next**.
[See image.](#what-to-do)
-
In the **Add IdP **window:
- **SAML Portal URL**: Enter the **Login URL **that you copied from the Microsoft Entra admin center in [Configure SAML SSO in the Microsoft Entra admin center](#configure-saml-entra).
- **Login Name Attribute**: Enter `NameID` (case sensitive).
- **IdP SAML Certificate**: Upload the `.pem` certificate that you downloaded from the Microsoft Entra admin center in [Configure SAML SSO in the Microsoft Entra admin center](#configure-saml-entra).
- **Org-Specific Entity ID**: If you have more than one organization instance on the same Zscaler cloud, enable this option. For example, if you have two organization instances on the same Zscaler cloud and must authenticate both instances against the same Microsoft Entra account, you can't use the same entity ID for multiple apps in the Microsoft Entra admin center. For this situation, you must enable this setting for both instances to generate a unique organization-specific entity ID.
- **Vendor**: Select the vendor of your IdP. In this case, it is **Microsoft Entra ID**.
- **Locations**: Select the [locations](/zia/about-locations) to map to this IdP. You can also search for a location. Any unselected locations are mapped to the default IdP. This field is set to **Any** for the default IdP, and you can't modify it.
- **Authentication Domains**: Select the domains to map to this IdP. This allows the Zscaler service to display the correct IdP to authenticate an incoming user. Any unselected domains are mapped to the default IdP. For the default IdP, this field is set to **Any**, and you can't modify it. You must map any additional IdPs to at least one domain.
[See image.](#idp-config)
- (Optional) If you want to enable **Sign SAML Request **for additional security:
-
After enabling **Sign SAML Request**:
- **Signature Algorithm**: Zscaler recommends selecting **SHA-2 (256-bit)**.
- **Request Signing SAML Certificate**: Select the most recent certificate.
- **SP SAML Certificate**: Click **Download Certificate**.
[See image.](#sign-saml-1)
- In the Microsoft Entra admin center, go to the **Single sign-on **page in your previously configured Zscaler cloud application.
-
In the **Verification certificates (optional) **section, click **Edit**.
[See image.](#sign-saml-2)
-
In the **Verification certificates **window:
- **Require verification certificates**: Enable this option.
- **Allow requests signed with RSA-SHA1**: If you selected **SHA-1 (160-bit) **in the ZIA Admin Portal, enable this option.
- Upload the **SP SAML Certificate** you downloaded in the ZIA Admin Portal.
[See image.](#sign-saml-3)
- Click **Save**.
-
In the **Token signing certificate **section, click **Edit**.
[See image.](#sign-saml-4)
-
In the **SAML Signing Certificate **window:
- **Signing Option**: Select **Sign SAML response and assertion**.
- **Signing Algorithm**: Select either **SHA-256 **or **SHA-1 **depending on your selection in the ZIA Admin Portal.
[See image.](#sign-saml-5)
- Click **Save**.
-
(Optional) If you want to configure SAML Auto-Provisioning, in the **Provisioning Options **section:
- **Enable SAML Auto-Provisioning**: Enable this option.
- **User Display Name Attribute**: Enter `displayName` (case sensitive).
- **Group Name Attribute**: Enter `groups` (case sensitive).
- **Department Name Attribute**: Enter `Department` (case sensitive).
[See image.](#saml-auto-provisioning)
Zscaler recommends using SCIM to provision users. Skip this step if you are using SCIM provisioning.
- Click **Save** and [activate the changes](/zia/saving-and-activating-changes-zia-admin-portal).
To learn more about configuring an IdP in the ZIA Admin Portal, see [Adding Identity Providers](/zia/adding-identity-providers).
- []Go to **Administration **>** Authentication Settings**.
- Click the **Identity Providers** tab.
-
Click the **Edit** icon for the identity provider (IdP) you configured for Microsoft Entra ID. To learn more, see [Add Microsoft Entra ID as the IdP for the Zscaler service in the ZIA Admin Portal](#add-idp).
The **Edit IdP** window appears.
-
In the **Edit IdP** window:
- **Enable SAML Auto-Provisioning**: Disable this option when enabling SCIM-based provisioning.
- **Enable SCIM Provisioning**: Enable to activate SCIM-based provisioning for users on the Zscaler service. To learn more, see [About SCIM](/zia/about-scim). SCIM provisioning isn't supported with Active Directory or OpenLDAP user repositories. If you want to migrate from directory synchronization to SCIM provisioning, enable **Disable Directory Sync & Enable SCIM Provisioning** on the [Authentication Profile page](/zia/about-authentication-profile). After enabling SCIM provisioning, the following fields appear:
-
**Base URL**: Copy the Base URL for the SCIM server. You need this URL when configuring your IdP for SCIM provisioning. Okta only accepts strings with the following format. In this example it is `37146169/1605333`.
``https://scim.``<Zscaler Cloud>``/``<Organization ID>``/``<IdP ID>``/scim``
The old SCIM Base URL marked as **(Deprecated)** will be removed in the future.
- **Bearer Token**: Copy the bearer token. It's a unique alphanumeric string that is used by the SCIM client to make authenticated API calls to the Zscaler SCIM server. You need this token when configuring your IdP for SCIM provisioning.
- **Generate Token**: Click to generate a new bearer token for security reasons. If you're generating a new bearer token for an existing SCIM configuration, ensure you update the token for your IdP.
[See image.](#enable-scim)
- Click **Save** to exit the window.
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
To learn more about configuring SCIM in the ZIA Admin Portal, see [Configuring SCIM](/zia/configuring-scim).
[]![Image of the SAML Auto-Provisioning options](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-saml-auto-provisioning-example.png)
[]![Image of the Enable SCIM Provisioning option](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-enable-scim.png)
[]![Image of the What do you want to do? window](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-What-do-you-want-to-do-window.png)
[]![General Info and Criteria sections in the Add IdP window](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-microsoft-entra-id/ZIA-add-idp-entra-id.png)
[]![Image of the Service Provider (SP) Options section](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-microsoft-entra-id/ZIA-enable-sign-saml-request.png)
[]![Image of the Edit button in the Verification certificates section](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-microsoft-entra-id/ZIA-entra-edit-verification-certificates.png)
[]![Image of the Verification certificates window](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-microsoft-entra-id/ZIA-entra-upload-verification-certificate.png)
[]![Image of the Edit button in the Token signing certificate section](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-microsoft-entra-id/ZIA-entra-edit-token-certificate.png)
[]![Image of the SAML Signing Certificate window](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-microsoft-entra-id/ZIA-entra-edit-signing-option-algorithim.png)
[]![Clicking Provision on demand on the Microsoft Entra Provisioning page](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-click-pod-example.png)
[]![Searching for a User on the Provision on demand page in Microsoft Entra ID](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-provision-on-demand-example.png)
[]![Clicking Provision Button on the Provision on demand page in Microsoft Entra ID](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/ZIA-entra-pod-click-provision.png)
[]![Viewing Results from Provisioning on demand in Microsoft Entra ID](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-azure-active-directory/Azure_Provision_On_Demand_Screen_Results.png)