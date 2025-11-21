# Configuration Guide for Microsoft Azure AD
Source: https://help.zscaler.com/zpa/configuration-guide-microsoft-azure-ad
PDF: https://help.zscaler.com/pdf/com/en/1483896.pdf

This guide provides information on how to set up Microsoft Azure Active Directory (AD) as a IdP for ZPA.
Zscaler and Microsoft are technology partners. To learn more about integrating Zscaler and Microsoft Azure AD, see the [Zscaler and Microsoft Entra ID Passwordless Deployment Guide](/zscaler-technology-partners/zscaler-and-microsoft-entra-ID-passwordless-deployment-guide).
Prerequisites
Ensure that you have the following:
- A premium Azure AD subscription, or an Azure AD subscription that has used less than 10 gallery Single Sign-On (SSO) applications with the license.
- An existing directory in Azure AD.
- A ZPA account with an administrator role that allows you to add an IdP Configuration.
Configuring Azure AD for SSO
The reference to private.zscaler.com in this article might differ depending on your organization’s assigned cloud. To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
[]To configure Azure AD as the IdP for ZPA user and admin SSO:
- Log in to the [Azure portal](http://portal.azure.com/) and go to **Azure Active Directory** > **Enterprise applications** from the left navigation pane.
[See image.](#Step1_UserImg)
- Click **New application**.
[See image.](#Step2_UserImg)
- Under **Add from the gallery**, search for "Zscaler Private Access". Choose one of the following:
- For ZPA user SSO in the IdP configuration, click the **Zscaler Private Access (ZPA)** application.
- For ZPA admin SSO in the IdP configuration, click the **Zscaler Private Access Administrator** application.
The following images in this procedure use the **Zscaler Private Access (ZPA) **application as an example.
[See image.](#Step3_UserImg)
- Click **Add**.
[See image.](#Step4_UserImg)
You are redirected to the Zscaler application's **Overview** page.
- Click **Single sign-on**, then **SAML**.
[See image.](#Step5_UserImg)
The **Set up Single Sign-on with SAML - Preview** page appears.
- For **Basic SAML Configuration**, click **Edit** and complete the following fields:
- For **Identifier (Entity ID)** enter the **Service Provider Entity ID** that is provided for you when you [configured a new IdP configuration](/zpa/about-idp/new#IdP_BothSSO) in ZPA Admin Portal. This ID is specific to your IdP.
- For **Reply URL (Assertion Customer Service URL)** enter the **Service Provider URL** that is provided for you when you configured a new IdP configuration in ZPA Admin Portal. This URL is specific to your IdP.
-
For **Sign on URL**, perform the following:
- [For ZPA user SSO configuration](#step6_1_user)
- [For ZPA admin SSO configuration](#step6_2_admin)
- Click **Save**.
After saving, you will be prompted to test the configuration. Do not test the configuration at this time.
- Leave **User Attributes & Claims** as default and skip to the next step.
- Under **SAML Signing Certificate**, for **Federation Metadata XML**, click the **Download** link to obtain the metadata file. You will need to upload this IdP metadata information to the ZPA Admin Portal later in order to complete the configuration.
[See image.](#Step9_UserImg)
- Leave **Set up Zscaler Private Access** (for ZPA user SSO) or **Set up Zscaler Private Access Administrator** (for ZPA admin SSO) as default, and skip to the next step.
Do not test the configuration at this time.
- In order for Azure AD users to authenticate through ZPA, you must assign these users to the ZPA application. In the application, click **Users and Groups** then **Add user**.
[See image.](#Step11_UserImg)
- Search for the user you want to assign to the ZPA application.
- Select the checkbox next to the user name, then click **Select**.
[See image.](#Step13_UserImg)
- In the **Add Assignment** panel, click **Assign**.
[See image.](#Step14_UserImg)
- If you are configuring the Azure AD for user SSO and want to use [SCIM](/zpa/about-scim), proceed to the [SCIM Configuration Guide for Microsoft Azure AD](/zpa/scim-configuration-guide-microsoft-azure-ad).
- If you are configuring the Azure AD for user SSO, proceed to the [Using Roles for Group Mapping](#Roles4GroupMap_userSSO) procedure below, then [complete the IdP configuration](/zpa/about-idp/new#IdP_BothSSO). If you are configuring the Azure AD for admin SSO, you can go directly to the ZPA Admin Portal to complete the IdP configuration.
Using Roles for Group Mapping
[]The following procedure applies to IdP configurations for ZPA user SSO only.
If all of the following criteria are met, then group mapping is not required:
- User-friendly group names are only sent to Azure AD using Azure AD Connect. For example, groups from an on-premise active directory show up in Azure AD when Azure AD Connect syncs the group information.
- AD Connect is on version 1.2.7.0 or greater.
To configure group mapping in Azure AD, you must customize the role claim type in the SAML response token in order to push groups to ZPA. To learn more about configuring role claims, see the [Microsoft product documentation](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-enterprise-app-role-management).
- [1. Adding Roles in the ZPA Application](#AddingRoles4ZPAApp_userSSO)
- [2. Assigning Roles to Groups](#AssigningRoles2Groups_userSSO)
- [3. Importing the memberOf Attribute](#ImportingMemberOfAttr_userSSO)
After configuring your IdP, be sure to [verify the configuration](/zpa/about-idp/new#Verify_SSO).
If you are verifying your ZPA admin SSO configuration, you can also go to [myapps.microsoft.com](http://myapps.microsoft.com/). From your Dashboard, click on the Zscaler Private Access** **app to initiate admin SSO.
[]You must add a role for each group you've created. If possible, ensure that the role name and group name are the same.
To add a role in the ZPA application:
- Go to the [Microsoft Graph Explorer](https://developer.microsoft.com/en-us/graph/graph-explorer).
- Sign in using your Azure credentials to run the Graph Explorer against your tenant.
[See image.](#GraphExplorer_Login)
- Under **Authentication**, click **modify permissions**.
[See image.](#GraphExplorer_ModifyPerms)
The **Modify Permissions** window appears.
- Select the following permissions from the list, then click **Modify Permissions**:
- **Directory.AccessAsUser.All**
- **Directory.Read.All**
- **Directory.ReadWrite.All**
[See image.](#GraphExplorer_ModifyPermsSelections)
- Choose **beta** for the version.
[See image.](#GraphExplorer_Beta)
- Enter the following query to retrieve the list of servicePrincipals from your tenant:
https://graph.microsoft.com/beta/servicePrincipals
- Click **Run Query**.
[See image.](#GraphExplorer_RunQuery1)
- Under **Response Preview**, search for the following service principal.
"appDisplayName": "Zscaler Private Access (ZPA)"
Following is a part of the response preview for the ZPA application. Its id is highlighted in green.
{
"id": "c7195233-3226-4121-b436-b8e755bab66c",
"deletedDateTime": null,
"accountEnabled": true,
"addIns": [],
"appDisplayName": "Zscaler Private Access (ZPA)",
- Use the id to enter the following query:
https://graph.microsoft.com/beta/servicePrincipals/<"id" of ZPA application>
In this example, it's https://graph.microsoft.com/beta/servicePrincipals/c7195233-3226-4121-b436-b8e755bab66c.
- Click **Run Query**.
[See image.](#GraphExplorer_RunQuery2)
You will get a response preview similar to the following. The appRoles property is highlighted in green.
{
"@odata.context": "https://graph.microsoft.com/beta/$metadata#servicePrincipals/$entity",
"id": "c7195233-3226-4121-b436-b8e755bab66c",
"deletedDateTime": null,
"accountEnabled": true,
"addIns": [],
"appDisplayName": "Zscaler Private Access (ZPA)",
"appId": "6a59ce75-7dd0-4033-a651-8053a9884f88",
"appOwnerOrganizationId": "6f7ada54-20ef-4a88-810b-a1c4179e8da9",
"appRoleAssignmentRequired": false,
"appRoles": [
{
"allowedMemberTypes": [
"User"
],
"description": "msiam_access",
"displayName": "msiam_access",
"id": "8866de6e-6d1e-4990-b534-2927284b7c14",
"isEnabled": true,
"origin": "Application",
"value": null
}
],
- Copy the entire appRoles property and paste it in the **Request Body**.
[See image.](#GraphExplorer_PasteAppRole)
- Add roles in the same JSON format. Each role must:
- Be in the same format as the msiam_access role
- Have a unique id (e.g., "id": "82811e87-6f98-4510-95e5-9cbe849acfad"). You can use a Globally Unique Identifier (GUID) generator.
- Have ServicePrincipal as the origin (e.g., "origin": "ServicePrincipal")
- Have a unique value (e.g., "value": "Engineer")
In the following request body example, the Engineer and Quality_Assurance roles are being added:
{    "appRoles": [
{
"allowedMemberTypes": [
"User"
],
"description": "msiam_access",
"displayName": "msiam_access",
"id": "8866de6e-6d1e-4990-b534-2927284b7c14",
"isEnabled": true,
"origin": "Application",
"value": null
},
{
"allowedMemberTypes": [
"User"
],
"description": "Engineer",
"displayName": "Engineer",
"id": "8866de6e-6d1e-4990-b534-2927284b7c15",
"isEnabled": true,
"origin": "ServicePrincipal",
"value": "Engineer"
},
{
"allowedMemberTypes": [
"User"
],
"description": "Quality_Assurance",
"displayName": "Quality_Assurance",
"id": "8866de6e-6d1e-4990-b534-2927284b7c16",
"isEnabled": true,
"origin": "ServicePrincipal",
"value": "Quality_Assurance"
}
],
}
- Choose **PATCH**.
[See image.](#GraphExplorer_Patch)
- Click **Run Query**. If your request body patched successfully, you'll see a success status code.
[See image.](#GraphExplorer_RunQuery3)
- To see if the roles were added, under **History** on the left navigation pane, choose the query with the "id" of the ZPA application. In this example, it's https://graph.microsoft.com/beta/servicePrincipals/c7195233-3226-4121-b436-b8e755bab66c.
[See image.](#GraphExplorer_History)
- Under **Response Preview**, scroll down to the appRoles property, and you'll see the added roles. In this example, within the section highlighted in green, the added roles are Quality_ Assurance and Engineer:
{
"@odata.context": "https://graph.microsoft.com/beta/$metadata#servicePrincipals/$entity",
"id": "c7195233-3226-4121-b436-b8e755bab66c",
"deletedDateTime": null,
"accountEnabled": true,
"addIns": [],
"appDisplayName": "Zscaler Private Access (ZPA)",
"appId": "6a59ce75-7dd0-4033-a651-8053a9884f88",
"appOwnerOrganizationId": "6f7ada54-20ef-4a88-810b-a1c4179e8da9",
"appRoleAssignmentRequired": false,
"appRoles": [
{
"allowedMemberTypes": [
"User"
],
"description": "msiam_access",
"displayName": "msiam_access",
"id": "8866de6e-6d1e-4990-b534-2927284b7c14",
"isEnabled": true,
"origin": "Application",
"value": null
},
{
"allowedMemberTypes": [
"User"
],
"description": "Quality_Assurance",
"displayName": "Quality_Assurance",
"id": "8866de6e-6d1e-4990-b534-2927284b7c16",
"isEnabled": true,
"origin": "ServicePrincipal",
"value": "Quality_Assurance"
},
{
"allowedMemberTypes": [
"User"
],
"description": "Engineer",
"displayName": "Engineer",
"id": "8866de6e-6d1e-4990-b534-2927284b7c15",
"isEnabled": true,
"origin": "ServicePrincipal",
"value": "Engineer"
}
],
"displayName": "Zscaler Private Access (ZPA)",
"errorUrl": null,
"homepage": "https://samlsp.private.zscaler.com/auth/sso?metadata=zscalerprivateaccess|ISV9.2|primary|z",
"keyCredentials": [
You need the roles you added in order to complete step f of the [Assigning Roles to Groups](/zpa/configuration-example-microsoft-azure-ad#AssigningRoles2Groups_userSSO) procedure below.
[]Assign roles to the groups in the ZPA application. Each group must be paired with its own role (i.e., 1:1 mapping ratio between groups and roles).
To assign a role to a group:
- Log in to the [Azure portal](http://portal.azure.com/) and go to **Azure Active Directory** > **Enterprise applications** from the left navigation pane.
[See image.](#Roles2Group_Step1)
- Click **All applications**, then click the **Zscaler Private Access (ZPA) **application you added for the [Adding Roles in the ZPA Application](/zpa/configuration-example-microsoft-azure-ad#AddingRoles4ZPAApp_userSSO) procedure above.
[See image.](#AzureRole4GroupMap_ZPAApp)
- Click **Users and groups**, then click **Add user**.
[See image.](#AzureRole4GroupMap_AddUser)
- In the **Add Assignment** panel that appears, select **Users and groups**.
[See image.](#AzureRole4GroupMap_AddAssignmentUsersAndGroups)
- Select the group you want to assign a role to (e.g., the **Engineer** group), then click **Select**.
[See image.](#AzureRole4GroupMap_AddAssignmentSelectGroup)
- []Click **Select Role**, then choose the role you added for the [Adding Roles in the ZPA Application](/zpa/configuration-example-microsoft-azure-ad#AddingRoles4ZPAApp_userSSO) above (e.g., the **Engineer** role).
[See image.](#AzureRole4GroupMap_AddAssignmentSelectRole)
- Click **Select**.
- In the **Add Assignment** panel, click **Assign**.
[See image.](#AzureRole4GroupMap_AddAssignmentAssignRole)
Repeat this procedure for each role you added for the [Adding Roles in the ZPA Application](/zpa/configuration-example-microsoft-azure-ad#AddingRoles4ZPAApp_userSSO) procedure above.
[]You must import the memberOf attribute to ZPA. Ensure that you have already added the attribute in Azure.
To import the memberOf attribute to ZPA:
- In the ZPA Admin Portal, go to **Authentication **> **User Authentication** > **IdP Configuration**.
- In the **IdP Configuration** page, expand the user SSO configuration for Azure AD.
- Click **Import SAML Attributes**.
![IdP Configuration page with Import SAML Attributes link](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-importsamlbutton.png)
If ZPA was correctly configured, the link redirects you to the SSO login page.
- Sign in using your Azure AD credentials. The ZPA authentication service automatically imports the memberOf attribute.
![Import SAML Attributes page in ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-role4groupmapping-zpaimportsaml.png)
- Click** Save**.
[]![Azure Active Directory > Enterprise applications menu option within Microsoft Azure Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-azure-entappnavigation.png)
[]
[]![Azure Active Directory > Enterprise applications menu option within Microsoft Azure Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-azure-entappnavigation.png)
[]![Enterprise applications page with New application option within Microsoft Azure Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-azure-newapp.png)
[]![Zscaler Private Access application in gallery search results within the Microsoft Azure Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-azure-zpauserssoapp.png)
[]![Add app panel within the Microsoft Azure Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-azure-adduserssoapp.png)
[]![Single sign-on panel within the Microsoft Azure Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-example-microsoft-azure-ad/zpa-azure-usersso-manage1.png)
[Enter the same URL you used for the **Reply URL (Assertion Customer Service URL)** field in the previous step.]
[![User SSO SAML Configuration in Microsoft Azure AD with matching Sign on URL and Reply URL](/downloads/zscaler-tech-pubs-style-guide/draft-articles/configuration-guide-microsoft-azure-ad-draft/zpa-azure-preview-step1_1_cropped.png?1626840792)
]
[Leave the **Sign on URL** field blank.]
[]
[]![Admin SSO SAML Configuration in Microsoft Azure AD with blank Sign on URL](/downloads/zscaler-tech-pubs-style-guide/draft-articles/configuration-guide-microsoft-azure-ad-draft/zpa-azure-preview-step1_0_cropped.png)
[]![SAML Signing Certificate information within the Microsoft Azure Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-example-microsoft-azure-ad/zpa-azure-preview-step3.png)
[]![Users and groups > Add User panel within the Microsoft Azure Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-azure-usersandgroups2.png)
[]![Add Assignment > Users and groups panel within the Microsoft Azure Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-azure-usersandgroups4.png)
[]![Add Assignment panel within the Microsoft Azure Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-azure-usersandgroups5.png)
[]![Sign in with Microsoft button within Microsoft Graph Explorer](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-role4groupmapping-azurelogin.png)
[]![API version menu within Microsoft Graph Explorer](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-role4groupmapping-azurebeta.png)
[]![API version menu within Microsoft Graph Explorer](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-role4groupmapping-azurerunquery.png)
[]![Run Query button within Microsoft Graph Explorer](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-role4groupmapping-azurerunquery2.png)
[]![Request Body section within Microsoft Graph Explorer](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-role4groupmapping-azureapproles.png)
[]![API method menu within Microsoft Graph Explorer](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-role4groupmapping-azurepatch.png)
[]![Success Status Code example within Microsoft Graph Explorer](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-role4groupmapping-azurerunquery3.png)
[]![History section within Microsoft Graph Explorer](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-role4groupmapping-azurehistory.png)
[]![Enterprise applications > All applications within the Microsoft Azure Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-role4groupmapping-azureselectzpaapp.png)
[]![Users and groups > Add user within the Microsoft Azure Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-azure-usersandgroups2.png)
[]![Add Assignment panel within the Microsoft Azure Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-role4groupmapping-azureaddassignmentselectuser.png)
[]![Add Assignment > Users and groups panel within the Microsoft Azure Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-role4groupmapping-azureengineergroup.png)
[]![Add Assignment > Users and groups panel within the Microsoft Azure Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-role4groupmapping-azureengineerrole.png)
[]![Add Assignment panel within the Microsoft Azure Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-role4groupmapping-azureassign.png)
[]![Authentication with modify permissions within the Microsoft Graph Explorer](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-role4groupmapping-modifyperms.png)
[]![Modify Permissions window within the Microsoft Graph Explorer](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-microsoft-azure-ad/zpa-role4groupmapping-modifyperms2.png)