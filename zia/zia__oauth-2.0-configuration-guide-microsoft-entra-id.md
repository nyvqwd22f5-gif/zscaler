# OAuth 2.0 Configuration Guide for Microsoft Entra ID
Source: https://help.zscaler.com/zia/oauth-2.0-configuration-guide-microsoft-entra-id
PDF: https://help.zscaler.com/pdf/com/en/1453081.pdf

The following guide explains how to configure OAuth 2.0 authorization for ZIA API using Microsoft Entra ID (formerly Azure Active Directory).
Microsoft Entra ID is an identity provider (IdP) that you can use for authentication and authorization. Using OAuth 2.0 with Client Credentials flow in Microsoft Entra ID permits a web client to use its own credentials, instead of impersonating a user. To manage authorization and consent in Microsoft Entra ID, you need to configure both the client and the resource server as applications. Based on this implementation, there is a separate application registration for each of the clients and the resource server (ZIA API).
OAuth 2.0 authorization is currently supported only for [cloud service API](/zia/about-api#CloudServiceAPI).
Zscaler and Microsoft are technology partners. To learn more about the Zscaler and Microsoft Entra ID integration, see the [Zscaler and Microsoft Entra ID Passwordless Deployment Guide](/zscaler-technology-partners/zscaler-and-microsoft-entra-ID-passwordless-deployment-guide).
Prerequisites
Ensure that the following prerequisites are met before you start configuring Microsoft Entra ID as your OAuth 2.0 service for ZIA API:
- You have a subscription to Microsoft Entra ID.
- You have an application (i.e., API Client) that needs to send API requests to the cloud service API.
- You have configured the necessary [API Roles](/zia/adding-api-roles) in the ZIA Admin Portal and assigned appropriate API permissions.
Configuring Microsoft Entra ID
For each API Role configured in the ZIA Admin Portal, you need to complete the following steps to set up OAuth 2.0 authorization using Microsoft Entra ID.
- [1. Register the ZIA API client application.](#register-client-app)
- [2. Configure the ZIA API service to expose a web API.](#register-app-and-expose-web-api)
- [3. Configure the client to access the web API.](#add-permission)
- [4. Collect information for Zscaler OAuth 2.0 server configuration.](#collect-info)
Validating Configurations and Retrieving an Access Token
After completing the necessary configurations in Microsoft Entra ID, you can validate the authorization server configuration and retrieve an access token.
- [1. Validate authorization server configuration.](#validate-configuration)
- [2. Retrieve an access token.](#retrieve-access-token)
[]This section covers how to register your ZIA API client application in Microsoft Entra ID and configure the client credentials.
- [a. Register the app.](#register-client)
- [b. Configure client credentials.](#configure-client-credentials)
[]To complete the client application registration process:
- Sign in to [Microsoft Entra admin center](https://entra.microsoft.com).
- Go to **Identity **> **Applications **> **App registrations**.
-
Click **New Registration**.
[See image.](#client-app-new-registration-button)
The **Register an application** window opens.
- In the **Register an application** window:
- **Name**: Enter a name for the application that is representative of the ZIA API Role used (e.g., ZIA API Client Super Admin).
- **Supported account types**: Ensure that this option is set to the **Accounts in this organizational directory only (****<tenant>**** only - Single tenant)** value.
-
Click **Register**.
[See image.](#client-app-registration-window)
The application is registered and the application's **Overview** page is displayed. Copy the **Application (client) ID** value from the **Overview** page and save it for later use.
[See image.](#client-app-id)
[]To configure the credentials for your API client application:
-
Click **Certificates & secrets** in the left-side navigation of the app and then click **New client secret** on the **Client secrets** tab.
[See image.](#new-client-secret-button)
The **Add a client secret** pane opens.
-
In the **Add a client secret** pane:
- **Description**: Provide information about the client's secret.
- **Expires**: Select the appropriate expiration time from the drop-down menu.
[See image.](#client-secret-window)
-
Click **Add**.
The client secret value is generated and displayed.
-
Copy the secret value immediately and save it for later use.
The client secret value is displayed only once and cannot be retrieved after you navigate away from the page.
[See image.](#client-secret)
[]This section covers how to register the ZIA API service in Microsoft Entra ID and configure the app to expose a web API that is accessible by the client app.
- [a. Register the app.](#register-zia-api)
- [b. Add a scope.](#add-scope)
- [c. Define an app role.](#define-app-role)
[]To complete the application registration process:
- In the Microsoft Entra admin center, go to **Identity **> **Applications **> **App registrations**.
-
Click **New Registration**.
[See image.](#register-zia-api-button)
The **Register an application** window opens.
-
In the **Register an application** window:
- **Name**: Enter a name for the ZIA API service, e.g., ZIA API Web Service.
- **Supported account types**: Ensure that this option is set to the **Accounts in this organizational directory only (****<tenant>**** only - Single tenant)** value.
[See image.](#register-zia-api-service-window)
-
Click **Register**.
The application is registered and displayed.
[]To configure the ZIA API app to expose a web API:
- Click **Expose an API** on the left-side navigation of the app.
- Click **Add **next to the **Application ID URI **and then click **Save** with the default value that is provided. Copy the Application ID URI and save it for later use.
-
Click **Add a scope** under **Scopes defined by this API**.
[See image.](#add-scope-button)
The **Add a Scope** pane opens.
-
In the **Add a Scope **pane:
- **Scope name**: Enter a relevant scope name (e.g., ZIA API Client <ZIA API Role>).
-
**Who can consent?**: Choose which users can consent to this scope based on your business requirements and organization policies.
If you are configuring this for testing purposes, make sure this option is restricted to **Admins only**.
- **Admin consent display name**: Enter a consent name that must be displayed on the consent screen when admins consent to this scope.
- **Admin consent description**: Enter a detailed description that must be displayed when tenant admins expand a scope on the consent screen.
- **User consent display name**: Enter a consent name that must be displayed on the consent screen when users consent to this scope.
- **User consent description**: Enter a detailed description that must be displayed when users expand a scope on the consent screen.
- **State**: Ensure that the scope is enabled.
[See image.](#add-scope-window)
- Click **Add scope**.
-
To authorize the client application, click **Add a client application **under **Authorized client applications**.
[See image.](#add-client-application-button)
-
In the **Client ID** field, enter the Application (client) ID from [Step 1 > a](#register-client), and select the required scope under **Authorized scopes**.
[See image.](#add-client-application-window)
- Click **Add Application**.
[]To declare a role for the ZIA API app (can be assigned to the client app for accessing the API):
-
Click **App roles** on the left-side navigation and then click **Create app role**.
[See image.](#create-app-role-button)
The **Create app role **pane opens.
-
In the **Create app role** pane:
- **Display name**: Enter a display name for the app role.
- **Allowed member types**: Select **Applications** for this option.
-
**Value**: Enter a value in the format supported by the Zscaler service, `<Zscaler Cloud Name>``::``<Org ID>``::``<API Role>`, where:
- `<Zscaler Cloud Name>` represents the name of the cloud on which your organization is provisioned.
- `<Org ID>` is an identifier assigned to your organization by Zscaler. You can obtain this value from the Company Profile page within the ZIA Admin Portal.
- `<API Role>` represents the API Role configured on the Role Management page within the ZIA Admin Portal.
For example, `zscalerbeta.net::272378::sampleRole`.
- **Description**: Enter a description of the app role.
- **Do you want to enable this app role?**: Enable this checkbox.
[See image.](#app-role-window)
- Click **Apply**.
- After the app role is created, go to the **Manifest** page from the left-side navigation and ensure that the app role you configured appears in the `appRoles` field within the JSON fields.
[]To configure the client app's permissions to the ZIA API app:
- In the Microsoft Entra admin center, go to **Identity **> **Applications **> **App registrations**.
-
Select the ZIA API client app configured in [Step 1](#register-client-app).
The **Overview** page of the app is displayed.
-
Click **API permissions** on the left-side navigation and then click **Add a permission** under **Configured permissions**.
The **Request API permissions** pane opens.
- In the **Request API permissions** pane:
-
Navigate to the **My APIs** tab and then click the ZIA API app that you configured in [Step 2](#register-app-and-expose-web-api).
[See image.](#request-api-permissions-step1)
- Choose the **Application permissions** as the type of permission required by the client application.
-
Under **Select permissions**, select the API Role that was created in [Step.2c](#add-permission).
[See image.](#request-api-permissions-step2)
- Click **Add permissions**.
If you are testing the configurations, enable the **Grant admin consent for ****<tenant>** option under the **Configured permissions** section and click **Yes** when prompted.
[]To collect information from Microsoft Entra ID used to configure the OAuth 2.0 authorization server in the ZIA Admin Portal:
- In the Microsoft Entra admin center, go to **Identity **> **Applications **> **App registrations**.
- Select the ZIA API app configured in [Step 2](#register-app-and-expose-web-api).
-
Click the **Endpoints** tab on the **Overview** page.
[See image.](#endpoints-button)
The **Endpoints** pane opens.
-
In the **Endpoints** pane:
- Copy the **OAuth 2.0 token endpoint (v2)** URL. The typical format is `https://login.microsoftonline.com/``<Application ID>``/oauth2/v2.0/token`.
- Copy the URL displayed in the **OpenID Connect metadata document** field and open the link in a new browser window. Locate the `jwks_uri` parameter in the metadata displayed and copy its value. The typical format is `https://login.microsoftonline.com/``<Application ID>``/discovery/v2.0/keys`.
[See image.](#endpoints)
These values are required for configuring the OAuth 2.0 authorization server in the ZIA Admin Portal, as explained in the subsequent section.
[]To validate your authorization server configuration:
- Log in to the ZIA Admin Portal.
- Go to **Administration** > **Cloud Service API Security**.
-
Click the **OAuth 2.0 Authorization Servers** tab and then click **Add Authorization Server**.
The **Add Authorization Server** window opens.
-
In the **Add Authorization Server** window, fill out the following information that is necessary for validating your authorization server configuration:
- **Name:** Enter a name for your authorization server configuration (e.g., Microsoft Entra ID). The name can only contain alphanumeric characters without spaces and cannot exceed 64 characters.
- **OAuth 2.0 JWKS Location:** Enter the JSON Web Key Set (JWKS) endpoint value obtained through the `jwks_uri` parameter in [Configuring Microsoft Entra ID > Step 4](#collect-info). The JWKS endpoint returns the public key set of the authorization server that is used by Zscaler to cryptographically verify the authenticity of the JWT in API requests.
[See image.](#oauth-server-zscaler)
Click **Validate** to verify that the JWKS endpoint is configured correctly. If validation is successful, a **Save** button appears.
- After successful validation, click **Save**.
[]To retrieve an access token from the authorization server by using the credentials saved in the previous steps:
-
Create a JSON file with the following fields:
`grant_type = client_credentials
client_id = `<Application (client) ID from `[Step 1.a](#register-client)`>`
client_secret = `<Client secret value from `[Step 1.b](#configure-client-credentials)`>`
scope = <`Application ID URI from `[Step 2.b](#add-scope), appended with "/.default". For example, api://fe2f6a75-199e-48a5-b9ef-a7357ab78c53/.default>
`
-
Send a POST request to the **OAuth 2.0 token endpoint (v2) **URL from [Step 4](#collect-info), with the JSON payload in the request body.
The API response should contain the access token (JWT). This access token must be sent in the API calls made to the ZIA API service. The access token can be presented in the request Authorization header using the bearer authentication scheme along with the token expiration time.
[]![A screenshot of the new app registration option in Microsoft Entra ID](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-microsoft-entra-id/ZIA-entra-new-registration.png)
[]![A screenshot of the app registration window in Microsoft Entra ID](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-azure-active-directory/ZIA-register-client-app-window.png)
[]![A screenshot of the client application ID in Microsoft Entra ID](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-azure-active-directory/client-application-id_0.png)
[]![A screenshot of the option to create a client secret in Microsoft Entra ID](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-azure-active-directory/new-client-secret.png)
[]![A screenshot of the Add a Client Secret window in Microsoft Entra ID](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-azure-active-directory/add-client-secret.png)
[]![A screenshot of the client secret displayed in Microsoft Entra ID](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-azure-active-directory/client-secret.png?1684781430)
[]![A screenshot of the ZIA API service registration in Microsoft Entra ID](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-microsoft-entra-id/ZIA-entra-new-registration.png)
[]![A screenshot of the ZIA API service registration window in Microsoft Entra ID](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-azure-active-directory/ZIA-register-zia-api-service-window.png)
[]![A screenshot of the Add new scope button in Microsoft Entra ID](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-azure-active-directory/add-scope-button.png)
[]![A screenshot of the new scope window in Microsoft Entra ID](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-azure-active-directory/add-scope-window_0.png)
[]![A screenshot of the option to add client application in Microsoft Entra ID](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-azure-active-directory/add-client-application-button.png)
[]![A screenshot of the window where client application is added in Microsoft Entra ID](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-azure-active-directory/add-client-application-window_0.png)
[]![A screenshot of the Endpoints button in the app registration page of Microsoft Entra ID](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-azure-active-directory/endpoints-button_0.png)
[]![A screenshot of the endpoints in the app registration page of Microsoft Entra ID](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-azure-active-directory/endpoints_0.png)
[]![A screenshot of the option to create an app role in Microsoft Entra ID](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-azure-active-directory/create-app-role-button.png)
[]![A screenshot of the app role window in Microsoft Entra ID](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-azure-active-directory/new-app-role-window.png)
[]![A Screenshot of the My APIs tab under an app's API Permissions tab in Microsoft Entra ID](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-azure-active-directory/my-apis-tab.png)
[]![A screenshot of the request permission configuration for an app in Microsoft Entra ID](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-azure-active-directory/request-api-permissions.png)
[]![A screenshot of the OAuth 2.0 server configuration in the ZIA Admin Portal](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-azure-active-directory/ZIA-add-entraID-server-zscaler.png)