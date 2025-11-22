# Admin SAML Configuration Guide for Azure Active Directory
Source: https://help.zscaler.com/cloud-branch-connector/admin-saml-configuration-guide-azure-active-directory
PDF: https://help.zscaler.com/pdf/com/en/1420901.pdf

This guide demonstrates how to configure Microsoft Azure Active Directory (Azure AD) as the identity provider (IdP) for Zscaler Cloud & Branch Connector and use [SAML single-sign-on (SSO) for your organization's admins](/cloud-branch-connector/accessing-administrator-management). To learn more about how to configure SAML within the Azure portal, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/add-application-portal).
Prerequisites
Ensure that you have the following before you start configuring Azure AD as the IdP:
- Existing Azure AD account
- [Zscaler cloud name](/cloud-branch-connector/what-my-cloud-name-zscaler-cloud-branch-connector)
- [Admin accounts created for your organization's admins](/cloud-branch-connector/adding-admins)
If you are subscribed to ZIdentity, some of the following options are only configurable within the ZIdentity Admin Portal. To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
Configuring SAML Admin SSO with Azure AD
To configure Azure AD as the IdP for Cloud & Branch Connector and use SAML SSO for admins:
- [Step 1: Add the Zscaler Cloud and Branch Connector Administrator Application](#CloudConnectorAdministratorApplication)
- [Step 2: Configure the SAML Admin SSO in Azure](#configure-saml-admin-sso)
- [Step 3: Assign Admins to Zscaler Cloud and Branch Connector Administrator Application](#assign-admins)
- [Step 4: (Optional) Enable IdP-Initiated SSO](#EnableIdP-InitiatedSSO)
- [Step 5: Configure SAML Admin SSO in the Cloud & Branch Connector Admin Portal](/cloud-branch-connector/configuring-saml-admins)
[]
- Sign in to the [Azure portal](http://portal.azure.com/).
-
Go to **Azure Active Directory**.
[See image.](#AzureAD1B)
-
On the left-side navigation, click **Enterprise applications**.
[See image.](#AzureAD1C)
-
Click **New application**.
[See image.](#AzureAD1D)
The **Browse Azure AD Gallery** page appears.
-
On the **Browse Azure AD Gallery** page, click **Create your own application**.
[See image.](#AzureAD1E)
-
In the **Create your own application** window, for **What's the name of your app?**, enter `Zscaler Cloud and Branch Connector Administrator Application`.
[See image.](#AzureAD1F)
- Click **Create**.
[]
To configure SAML admin SSO in Azure:
-
On the left-side navigation of the Zscaler Cloud and Branch Connector Administrator Application, click **Single sign-on**.
[See image.](#AzureAD2A)
-
Click **SAML**.
[See image.](#AzureAD2B)
-
In the **Basic SAML Configuration** section, click the **Edit** icon.
[See image.](#AzureAD2C)
- In the **Basic SAML Configuration** window:
- **Identifier (Entity ID)**: Enter `connector.<``Zscaler Cloud``>.net` as the identifier.
- **Reply URL (Assertion Consumer Service URL)**: The Zscaler cloud name depends on the URL you use to log in to the Zscaler service. For example, if you log in to https://connector.Zscalerbeta.net, then enter `https://connector.Zscalerbeta.net/bac-adminsso.do`. In the **Index** field, enter **1**.
- **Sign on URL (Optional)**: Leave this field blank.
- **Relay State (Optional)**: Leave this field blank.
-
**Logout URL (Optional)**: Leave this field blank.
[See image.](#AzureAD2D)
- Click **Save** and exit the window.
-
When prompted to **Test single sign-on with Zscaler Cloud and Branch Connector Administrator Application**, click **No, I'll test later**.
[See image.](#AzureAD2F)
-
(Optional) In **Attributes & Claims**, edit the **Unique User Identifier** if required by your organization.
[See image.](#AzureAD2G)
-
In **SAML Certificates**, download the **Certificate (Base64)**. You need this certificate in order to [configure SAML admin SSO in the Cloud & Branch Connector Admin Portal](/cloud-branch-connector/configuring-saml-admins).
[See image.](#AzureAD2H)
-
In **Set up Zscaler Cloud and Branch Connector Administrator Application**, copy the **Azure AD Identifier**. You need this certificate in order to [configure SAML admin SSO in the Cloud & Branch Connector Admin Portal](/cloud-branch-connector/configuring-saml-admins).
[See image.](#AzureAD2I)
[]
For Azure AD admins to authenticate through the Zscaler service, you must assign Azure AD admins to the Zscaler Cloud and Branch Connector Administrator Application. To assign admins to the Zscaler Cloud and Branch Connector Administrator Application in Azure:
-
On the left-side navigation of the Zscaler Cloud and Branch Connector Administrator Application, click **Users and groups**.
[See image.](#AzureAD3A)
-
Click **Add user/group**.
[See image.](#AzureAD3B)
-
In the **Add Assignment** window, click **Users and groups**.
[See image.](#AzureAD3C)
-
In the **Users and groups** window, select the admins you want to assign to the Zscaler Cloud and Branch Connector Administrator Application, then click **Select**.
[See image.](#AzureAD3D)
-
In the **Add Assignment** window, click **Assign**.
[See image.](#AzureAD3E)
[]
By default, the Zscaler Cloud and Branch Connector Administrator Application is visible to admins in their My Apps portal.
To enable or disable application visibility:
-
On the left-side navigation for the Zscaler Cloud and Branch Connector Administrator Application, click **Properties**.
[See image.](#AzureAD4A)
-
For **Visible to users?**, select **Yes** or **No**.
[See image.](#AzureAD4B)
Testing the SAML Configuration
To test the SAML admin SSO, you can initiate the SAML connection from the Zscaler Cloud and Branch Connector Administrator Application. There are two ways to do this:
- [Go to Microsoft My Apps Portal](#MyAppsPortal)
- [Browse to the User Access URL](#UserAccessURL)
[]
You can use this method if you have enabled application visibility, as demonstrated in the [Enable IdP-Initiated SSO step](https://admin-saml-configuration-guide-azure-active-directory#EnableIdP-InitiatedSSO).
- Sign in to the [Microsoft My Apps](http://myapps.microsoft.com) portal.
-
Click **Zscaler Cloud and Branch Connector Administrator Application**.
[See image.](#AzureADMicrosoftMyApps2)
[]
If you have disabled application visibility, demonstrated in [Enable IdP-Initiated SSO](#EnableIdP-InitiatedSSO), you can access the Zscaler Cloud and Branch Connector Administrator Application directly from your browser.
-
On the left-side navigation for the Zscaler Cloud and Branch Connector Administrator Application, click **Properties**.
[See image.](#AzureADBrowse1)
-
Copy the **User access URL**.
[See image.](#AzureADBrowse2)
- Browse to the User Access URL. You are signed in to the Zscaler Cloud & Branch Connector Admin Portal.
[]![Azure Active Directory](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD1B.png)
[]![Enterprise applications](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD1C.png)
[]![New application](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD1D.png)
[]![Create your own application](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD1E.png)
[]![Input name](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD1F.png)
[]![Single sign-on](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD2A.png)
[]![SAML](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD2B.png)
[]![Edit Basic SAML Configuration](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD2C.png)
[]![Basic SAML Configuration](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD2D.png)
[]![Select No, I'll test later](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD2F.png)
[]![Unique User Identifier](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD2G.png)
[]![Download Certificate (Base64)](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD2H.png)
[]![Copy Azure AD Identifier](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD2I.png)
[]![Users and groups](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD3A.png)
[]![Add user/group](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD3B.png)
[]![Users and groups](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD3C.png)
[]![Selecting Users and groups admins](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD3D.png)
[]![Assign admins](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD3E.png)
[]![Properties](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD4A.png)
[]![Visible to users?](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureAD4B.png)
[]![Zscaler Cloud and Branch Connector Administrator Application](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureADMicrosoftMyApps2.png)
[]![Properties](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureADBrowse1.png)
[]![User access URL](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-azure-active-directory-draft-doc-51903/AzureADBrowse2.png)