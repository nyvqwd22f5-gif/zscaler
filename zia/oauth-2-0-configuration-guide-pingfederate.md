# OAuth 2.0 Configuration Guide for PingFederate
Source: https://help.zscaler.com/zia/oauth-2-0-configuration-guide-pingfederate
PDF: https://help.zscaler.com/pdf/com/en/1529512.pdf

The following guide explains how you can configure [OAuth 2.0 authorization](/zia/securing-zia-apis-oauth-2.0) for the [cloud service API](/zia/understanding-zia-apis) using PingFederate.
Zscaler and Ping Identity are technology partners. To learn more about the Zscaler and Ping Identity integration, see the [Zscaler and Ping Identity Deployment Guide](/zscaler-technology-partners/zscaler-and-pingone-deployment-guide).
Prerequisites
Ensure that the following prerequisites are met before you start configuring PingFederate as your OAuth 2.0 authentication service:
- You have a PingFederate subscription for your organization.
- You have an application (i.e., API Client) that needs to send API requests to the Zscaler service.
- You have a certificate for access token management configured in the PingFederate admin console.
Configuring OAuth 2.0 for PingFederate
Complete the following steps to set up OAuth 2.0 authorization using PingFederate:
- [1. Add the Zscaler client configuration in the PingFederate admin console.](#ping-client-config)
- [2. Configure an Access Token Management Instance in the PingFederate admin console.](#ping-access-token-config)
- [3. Obtain the JKWS URL from the PingFederate admin console.](#ping-jwks)
- [4. Create an API Role and Authorization Server in the ZIA Admin Portal.](#zia-config)
- [5. Configure a scope in the PingFederate admin console.](#ping-scope)
- [6. Request an access token.](#request-access-token)
-
[]In the PingFederate admin console, go to **Applications** > **OAuth** > **Clients **and click **Add Client**.
[See image.](#ping-image-1)
-
On the **Client **page:
- **Client ID**: Enter an ID for the client configuration.
- **Name**: Enter a name for the client configuration.
- **Client Authentication**: Select **Client Secret**.
- **Client Secret**: Select **Change Secret **and** **enter a secret, or choose **Generate Secret **for a random secret.
- **Allowed Grant Types**: Select **Client Credentials**.
[See image.](#ping-image-10)
Configure the other fields as desired or use the defaults.
- Click **Save**.
-
[]Go to **Applications** > **OAuth** > **Access Token Management **and click **Create New Instance**.
[See image.](#ping-image-2)
-
In the **Type **section:
- **Instance Name**: Enter a name for the instance.
- **Instance ID**: Enter an ID for the instance.
- **Type**: Select **JSON Web Tokens**.
- **Parent Instance**: Select **None**.
[See image.](#ping-image-3)
- Click **Next**.
-
Click **Add a new row to "Certificates"**.
[See image.](#ping-image-4)
-
Configure the following fields:
- **Key ID**: Enter a key ID for the certificate.
- **Certificate**: Select a certificate from the drop-down menu.
- **JWS Algorithm**: Select **RSA using SHA-256.**
- **Active Signing certificate Key ID**: Select the **Key ID **you entered in the **Certificates **section.
[See image.](#ping-image-11)
Configure the other fields as desired or use the defaults.
-
Click **Show Advanced Fields**.
[See image.](#ping-image-5)
-
For **Scope Claim Name**, enter `scp` and click **Next**.
[See image.](#ping-image-12)
- In the **Session Validation **section, click **Next**.
-
In the **Access Token Attribute Contract** section, **Add** any single attribute and click **Next**.
In this example, the attribute used is `userPrincipalName`.
[See image.](#ping-image-6)
- In the **Resource URIs **and **Access Control **sections, click **Next**.
- In the **Summary** section, click **Save**.
- On the **Clients **page, select the configured client and click **Edit**.
-
For **Default Access Token Manager**, select the token you configured previously and click **Save**.
[See image.](#ping-image-7)
- []Click the **? **icon in the top-right corner and select **OAuth Endpoints**.
-
Copy the **OAuth Authorization Server Endpoint **and the **OAuth Token Endpoint **(you need them later to retrieve an access token).
[See image.](#ping-image-8)
- Append the **OAuth Authorization Server Endpoint** to the URL you use to log in to the PingFederate admin console and press `Enter`. For example, if your Pingfederate URL is `https://zpf.zpingfed.com`, the URL with the endpoint appended would be `https://zpf.zpingfed.com/.well-known/oauth-authorization-server`.
-
On the resulting web page, copy the `jwks_uri`. You need it for configuration in the ZIA Admin Portal.
[See image.](#ping-image-13)
- []Go to **System** > **OAuth Settings** > **Scope Management**.
-
Enter a **Scope Value** in the format supported by the Zscaler service, `<Zscaler Cloud Name>::<Org ID>::<API Role>`, where:
- `<Zscaler Cloud Name>` represents the name of the cloud on which your organization is provisioned.
- `<Org ID>` represents your organization ID obtained from the Company Profile page within the ZIA Admin Portal.
- `<API Role>` represents the name of API roles configured on the Role Management page in the ZIA Admin Portal. This name must match the name of the API role you create in the ZIA Admin Portal.
Also, enter a **Scope Description**.
[See image.](#ping-image-9)
- Click **Add**.
- Click **Save**.
-
[]In the ZIA Admin Portal go to **Administration** > **Role Management** and click **Add API Role**.
[See image.](#zia-image-1)
The **Add API Role **window appears.
-
In the **Add API Role **window:
- **Name**: Enter a name for the API role. It must match the name you entered in the PingFederate admin console.
- **Policy Access**: Select **Full**.
- **Administrators Access**: Select **Full**.
- Enable all options in the **Functional Scope **section.
[See image.](#zia-image-2)
- Click **Save**.
-
Go to **Administration **> **Cloud Service API Security **> **OAuth 2.0 Authorization Servers** and click **Add Authorization Server**.
[See image.](#zia-image-3)
The **Add Authorization Server **window appears.
-
In the Add Authorization Server window:
- **Enable**: Enable the server.
- **Name**: Enter a name for the server.
- **OAuth 2.0 JWKS Location**: Enter the `jwks_uri` you copied from the PingFederate admin console.
- **JWKS Certificate Authentication**: Enable this option.
- **Audience URI (Optional)**: You can enter an audience URI.
- **Issuer ID (Optional)**: You can enter an issuer ID.
- **Client ID (Optional)**: You can enter a client ID.
[See image.](#zia-image-4)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-zia-admin-portal).
[]You can implement the authorization flow between your client and authorization server by requesting an access token. To do this, you need the following information from the PingFederate admin console:
- **Client ID:** A unique identifier issued to the client application during registration with the authorization server. This value can be obtained from **Applications **> **OAuth Clients **> **Clients **in the PingFederate admin console.
- **Client Secret:** A secret string used by the client application for authenticating with the authorization server. This value is established when you [configure the OAuth client in the PingFederate admin console](#ping-client-config) and can be changed later.
- **Scope:** [Custom scopes](#ping-scope) configured for your custom authorization server to define the permissions required by the client application to access the cloud service API. Custom scopes can be obtained from **System** > **OAuth Settings** > **Scope Management **in the PingFederate admin console.
- **Token Endpoint:** The endpoint exposed by the authorization server to allow the client application to request an access token. This is the **OAuth Token Endpoint **that you copied from the **OAuth Endpoints **page in the PingFederate admin console.
With this information, you can set up the client to send an authorization request to the token endpoint via an HTTP POST request. This request must contain the client ID and the client secret presented in the authorization header of the request using HTTP basic authentication. The request body must contain the following parameters:
- `grant_type` as `client_credentials`, indicating that the Client Credentials grant type is used.
- `scope` must be at least one custom scope created for your authorization server.
Example POST request to the token endpoint:
POST /oauth2/default/v1/token HTTP/1.1
Host: https://${yourPingFederateDomain}
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
To learn more about the configuration steps, refer to the [PingFederate documentation](https://docs.pingidentity.com/pingfederate/12.2/pf_pf_landing_page.html).
[]![Add client button in the PingFederate admin console](/downloads/zia/authentication-administration/api-security/oauth-2-0-configuration-guide-pingfederate/ZIA-PingFed-Clients.png)
[]![The button to create a new Access Token Management instance in the PingFederate admin console](/downloads/zia/authentication-administration/api-security/oauth-2-0-configuration-guide-pingfederate/ZIA-pingfed-access-token-management.png)
[]![The Type section for creating a new Access Token Management Instance in the PingFederate admin console](/downloads/zia/authentication-administration/api-security/oauth-2-0-configuration-guide-pingfederate/ZIA-pingfed-create-new-token-instance.png)
[]![Adding a new certificate in the PingFederate admin console](/downloads/zia/authentication-administration/api-security/oauth-2-0-configuration-guide-pingfederate/ZIA-pingfed-add-new-row-to-certificate.png)
[]![The option to show advanced fields in the PingFederate admin console](/downloads/zia/authentication-administration/api-security/oauth-2-0-configuration-guide-pingfederate/ZIA-pingfed-show-advanced-fields.png)
[]![The Access Token Attribute Contract page in the PingFederate admin console](/downloads/zia/authentication-administration/api-security/oauth-2-0-configuration-guide-pingfederate/ZIA-pingfed-access-token-attribute-contact.png)
[]![Selecting a Default Access Token Manager in the PingFederate admin console](/downloads/zia/authentication-administration/api-security/oauth-2-0-configuration-guide-pingfederate/ZIA-pingfed-select-default-token-management.png)
[]![OAuth endpoints with the OAuth Authorization Server Endpoint highlighted in the PingFederate admin console](/downloads/zia/authentication-administration/api-security/oauth-2-0-configuration-guide-pingfederate/ZIA-pingfed-oauth-endpoints-page.png)
[]![Where to enter and an example of the Scope Value on the Scope Management page in the PingFederate admin console](/downloads/zia/authentication-administration/api-security/oauth-2-0-configuration-guide-pingfederate/ZIA-pingfed-scope-management-details.png)
[]![The Client settings that must be configured in the PingFederate admin console](/downloads/zia/authentication-administration/api-security/oauth-2-0-configuration-guide-pingfederate/ZIA-pingfed-client-settings.png)
[]![The access token management instance settings that must be configured in the PingFederate admin console](/downloads/zia/authentication-administration/api-security/oauth-2-0-configuration-guide-pingfederate/ZIA-pingfed-add-new-certificate-row-details.png)
[]![Scope Claim Name value in the PingFederate admin console](/downloads/zia/authentication-administration/api-security/oauth-2-0-configuration-guide-pingfederate/ZIA-pingfed-scope-claim-name.png)
[]![jwks_uri on the OAuth authorization server endpoint in the PingFederate admin console](/downloads/zia/authentication-administration/api-security/oauth-2-0-configuration-guide-pingfederate/ZIA-pingfed-oauth-jwks-uri.png)
[]![The Add API Role option on the Role Management page in the ZIA Admin Portal](/downloads/zia/authentication-administration/api-security/oauth-2-0-configuration-guide-pingfederate/ZIA-oauth-add-api-role.png)
[]![Configuring the PingFederate API role in the Add API Role window in the ZIA Admin Portal](/downloads/zia/authentication-administration/api-security/oauth-2-0-configuration-guide-pingfederate/ZIA-oauth-add-api-role-window.png)
[]![The option to add an Authorization Server on the Cloud Service API Security page in the ZIA Admin Portal](/downloads/zia/authentication-administration/api-security/oauth-2-0-configuration-guide-pingfederate/ZIA-oauth-add-authorization-server.png)
[]![Adding the PingFederate Authorization Server in the ZIA Admin Portal](/downloads/zia/authentication-administration/api-security/oauth-2-0-configuration-guide-pingfederate/ZIA-oauth-add-authorization-server-window.png)