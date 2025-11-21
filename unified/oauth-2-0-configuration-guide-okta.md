# OAuth 2.0 Configuration Guide for Okta
Source: https://help.zscaler.com/unified/oauth-2-0-configuration-guide-okta
PDF: https://help.zscaler.com/pdf/com/en/1495106.pdf

The following guide explains how you can configure [OAuth 2.0 authorization](/unified/securing-internet-saas-apis-oauth-2-0) for the Internet & SaaS API using Okta.
Prerequisites
Ensure that the following prerequisites are met before you start configuring Okta as your OAuth 2.0 authentication service:
- You have an Okta subscription for your organization.
- You have an application (i.e., API Client) that needs to send API requests to the Zscaler service.
- You have configured the necessary [API Roles](/unified/adding-api-roles) in the Admin Portal.
Configuring Okta
Complete the following steps to set up OAuth 2.0 authorization using Okta:
- [Step 1: Register your Application](#RegisterApplication)
- [Step 2: Create an Authorization Server](#CreateAuthorizationServer)
- [Step 3: Request an Access Token](#RequestAccessToken)
[]You need to register your application (i.e., API client) with Okta by creating an app integration from the Okta Admin Console.
To register your application:
- In the Okta Admin Console, go to **Applications** > **Applications**.
-
Click **Create App Integration**.
[See image.](#CreateAppIntegrationButton)
The **Create a new app integration** window appears.
-
In the **Create a new app integration** window, select **API Services** as the Sign-in method, and click **Next**.
[See image.](#SignInMethod)
-
Provide a name for the app integration.
[See image.](#AppIntegrationWindow)
- Click **Save**.
After your application is registered, the app integration page appears with the General and Okta API Scopes tabs.
The General tab of your app integration displays the generated Client ID and Client Secret values that are necessary to implement your authorization flow. The client application must have its client ID and client secret values stored securely.
[]You need to create a custom authorization server and define your OAuth 2.0 scope, claims, and access policies within the authorization server, as applicable.
To create a custom authorization server:
-
In the Okta Admin Console, go to **Security** > **API**.
[See image.](#SecurityAPIMenu)
-
Click **Add Authorization Server**.
[See image.](#AddAuthorizationServerButton)
The **Add Authorization Server** window appears.
-
In the **Add Authorization Server** window:
- **Name:** Enter a name for your authorization server.
- **Audience:** (Optional) Enter the audience value for the authorization server.
- **Description:** (Optional) Enter a description for your authorization server.
[See image.](#AuthorizationServerWindow)
- Click **Save**.
After the configuration is saved, the authorization server's Settings tab displays the information that you provided and additional details, such as Metadata URI, Signing Key Rotation, Last Key Rotation, etc.
If you need to modify any of the information, such as Issuer or Signing Key Rotation, click **Edit**.
[See image.](#SettingsTab)
You need the Metadata URI to retrieve the token endpoint and the JWKS endpoint that are necessary for implementing the authorization flow.
[]Configure Scopes
For the [Client Credentials](/unified/securing-internet-saas-apis-oauth-2-0) flow of OAuth 2.0 authorization, Okta requires that you create custom scopes to define the access privileges required for authorization.
To create a custom scope:
- In the Okta Admin Console, go to **Security** > **API**.
-
On the **Authorization Servers** tab, select the name of the required authorization server.
[See image.](#AuthorizationServers)
The authorization server’s **Settings** tab appears.
-
Select the **Scopes** tab.
[See image.](#ScopesTab)
-
Click **Add Scope**.
[See image.](#AddScopeButton)
The **Add Scope** window appears.
-
In the **Add Scope** window, configure *only* the following fields that are applicable to the Client Credentials flow:
-
**Name:** Enter the name of the scope in the format supported by the Zscaler service, `<Zscaler Cloud Name>``::``<Org ID>``::``<API Role>`, where:
- `<Zscaler Cloud Name>` represents the name of the cloud on which your organization is provisioned
- `<Org ID>` represents your organization ID obtained from the Company Profile page within the Admin Portal
- `<API Role>` represents the name of API Roles configured on the Role Management page within the Admin Portal
For example, `zscalerbeta.net::272378::sampleRole`.
- **Description:** (Optional) Enter a description for the scope.
-
**Default scope:** (Optional) Select **Set as a default scope** to allow Okta to authorize clients that omit the scope parameter in the authorization request. Okta returns all of the default scopes permitted in the access token by the access policy rule.
Zscaler recommends that you do *not* select this option if you have multiple clients accessing the Internet & SaaS API using different scopes.
- **Metadata:** (Optional) Select **Include in public metadata** to allow the scope to be [publicly discoverable](https://developer.okta.com/docs/reference/api/oidc/#well-known-oauth-authorization-server).
[See image.](#AddScopeWindow)
- Click **Create**.
[]Create Access Policies and Policy Rules
Access policies allow you to define rules for client applications that are requesting access tokens from your authorization server. The rules within an access policy assign expiry time to an access token based on the grant type, scope, and various other parameters in the access token request.
Access policies and rules within each policy are evaluated in priority order (i.e., order of listing), which is automatically assigned on rule/policy creation. You can change the priority of individual policies and rules by reordering them using drag and drop.
To create an access policy for an authorization server:
- In the Okta Admin Console, go to **Security** > **API**.
-
On the **Authorization Servers** tab, select the name of the authorization server for which you want to add an access policy.
[See image.](#AuthServerList)
-
Select **Access Policies**.
[See image.](#AccessPoliciesTab)
- The authorization server’s **Access Policies** tab appears.
-
On the **Access Policies** tab, click **Add Policy**.
[See image.](#AddPolicyButton)
The **Add Policy** window appears.
-
In the **Add Policy** window:
- **Name:** Enter a name for the access policy.
- **Description:** Enter a description for the access policy.
- **Assign to:** Choose from the following options:
- **All Clients:** The policy is assigned to all configured client applications.
-
**The following clients:** The policy is assigned to the client applications that you specify within this field. To specify client applications, enter the name of a client application and select the application when it appears.
This field auto-completes the name of your client applications as you type.
[See image.](#AddPolicyWindow)
- Click **Create Policy**.
To create a rule within an access policy:
- In the Okta Admin Console, go to **Security** > **API**.
-
On the **Authorization Servers** tab, select the name of the authorization server for which you want to add access policy rules.
[See image.](#AuthServers)
-
Select **Access Policies**.
[See image.](#access-policies-tab)
The authorization server’s **Access Policies** tab appears.
-
On the **Access Policies** tab, select the name of an access policy, and then select **Add Rule**.
[See image.](#AddRuleButton)
The **Add Rule** window appears.
-
In the **Add Rule** window, configure *only* the following settings that are applicable to the Client Credentials flow:
- **Name:** Enter a name for the rule.
- **IF Grant type is:** Select the Client Credentials grant type.
- **AND Scopes requested:** Select one or more scopes that need to be covered by this rule.
- **THEN Use this inline hook:** Select an [inline hook](https://developer.okta.com/docs/concepts/inline-hooks/), as required.
- **AND Access token lifetime is:** Select the length of time in Minutes, Hours, or Days before an access token expires.
[See image.](#AddRuleWindow)
- Click **Create Rule**.
The first policy and rule that matches the client's request is applied, and no further rule or policy evaluation takes place. If a client matches no policies, then the authentication attempt fails.
[]Test your Authorization Server Configuration
You can verify that the authorization server is configured correctly by previewing the access token and validating the configured details.
To test your authorization server configuration:
- In the Okta Admin Console, go to **Security** > **API**.
-
On the **Authorization Servers** tab, select the name of the authorization server that you need to verify.
[See image.](#auth-server-list)
-
On the authorization server page, select **Token Preview**.
[See image.](#TokenPreviewTab)
- Select the following properties for your access request:
- **OAuth/OIDC client:** Select your client application from the drop-down. To specify a client application, enter the name of the client application and select the application when it appears. This field auto-completes the name of your client applications as you type.
- **Grant type:** Select Client Credentials from the drop-down.
- **Scopes:** Select one or more custom scopes created for your authorization server. To specify custom scopes, enter the name of a scope and select the scope when it appears. This field auto-completes the name of your custom scopes as you type.
-
Click **Preview Token**.
[See image.](#TokenPreview)
If the authorization server is configured properly, a token preview is generated with the configured information. Otherwise, an error is displayed, and you need to review your authorization server configurations.
[]After [registering the client application](#RegisterApplication) and [configuring your authorization server](#CreateAuthorizationServer), you can implement the authorization flow between your client and authorization server. To do this, you need the following information from the Okta Admin Console:
- **Client ID:** A unique identifier issued to the client application during registration with the authorization server. This value can be obtained from the General tab of your app integration page in the Okta Admin Console.
- **Client Secret:** A secret string used by the client application for authenticating with the authorization server. This value can be obtained from the General tab of your app integration page in the Okta Admin Console.
- **Scope:** [Custom scopes](#ConfigureScope) configured for your custom authorization server to define the permissions required by the client application to access the Internet & SaaS API. Custom scopes can be obtained from within the Scopes tab of the authorization server you created.
- **Token Endpoint:** The endpoint exposed by the authorization server to allow the client application to request an access token. The token endpoint can be retrieved from the Metadata URI displayed on the Settings tab of the authorization server you created.
With this information, you can set up the client to send an authorization request to the token endpoint via an HTTP POST request. This request must contain the client ID and the client secret presented in the authorization header of the request using HTTP basic authentication. The request Body must contain the following parameters:
- `grant_type` as `client_credentials`, indicating that the Client Credentials grant type is used.
- `scope` must be at least one custom scope created for your authorization server.
Example POST request to the token endpoint:
POST /oauth2/default/v1/token HTTP/1.1
Host: https://${yourOktaDomain}
Authorization: Basic xxxxxxx
Content-Type: application/x-www-form-urlencoded
{
"grant_type": "client_credentials",
"scope": "zscalerbeta.net::272378::sampleRole"
}
If the credentials passed in the request are valid, the application receives an access token in a JSON structure, as follows:
{
"access_token": "xxxxxxx",
"token_type": "Bearer",
"expires_in": 1663909495,
"scope": "zscalerbeta.net::272378::sampleRole"
}
The client ID and the secret must be placed in the HTTP Authorization header and cannot be included in the request body.
To learn more about the configuration steps, refer to the [Okta documentation](https://developer.okta.com/docs/guides/authorization/).
[]![A screenshot of the Create App Integration button in the Applications menu](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/create-app-integration-button.png)
[]![A screenshot of the various sign-in methods for the app integration.](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/app-integration-sign-in-method.png)
[]![A screenshot of the app integration window](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/app-integration-details.png)
[]![A screenshot of the navigation to the API menu ](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/security-api-navigation.png)
[]![A screenshot of the Add Authorization Server button](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/add-authorization-server-button.png)
[]![A screenshot of the authorization server window](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/authorization-server-details.png)
[]![A screenshot of the authorization server's Settings tab ](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/authorization-server-settings-tab.png)
[]![A screenshot of the list of authorization servers ](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/select-authorization-server.png)
[]![A screenshot of the Scopes tab of the authorization server](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/scopes-tab.png)
[]![A screenshot of the Add Scope button](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/add-scope-button.png)
[]![A screenshot of the Add Scope window](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/scope-details.png)
[]![A screenshot of the list of authorization servers ](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/select-authorization-server.png)
[]![A screenshot of the Access Policies tab of the authorization server](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/access-policies-tab.png)
[]![A screenshot of the Add Policy button](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/add-policy-button.png)
[]![A screenshot of the Add Policy window](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/access-policy-details.png)
[]![A screenshot of the list of authorization servers ](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/select-authorization-server.png)
[]![A screenshot of the Access Policies tab of the authorization server](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/access-policies-tab.png)
[]![A screenshot of the Add Rule button](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/add-rule-button.png)
[]![A screenshot of the Add Rule window](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/rule-details.png)
[]![A screenshot of the list of authorization servers ](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/select-authorization-server.png)
[]![A screenshot of the Token Preview tab](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/token-preview-tab.png)
[]![A screenshot of the access token preview](/downloads/zia/authentication-administration/api-security/oauth-20-configuration-guide-okta/token-preview.png)