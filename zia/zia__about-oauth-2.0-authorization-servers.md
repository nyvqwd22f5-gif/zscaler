# About OAuth 2.0 Authorization Servers
Source: https://help.zscaler.com/zia/about-oauth-2.0-authorization-servers
PDF: https://help.zscaler.com/pdf/com/en/1415061.pdf

When using the [OAuth 2.0 authentication](/zia/securing-zia-apis-oauth-2.0) model, the Zscaler service needs to validate the access token (JSON Web Token) in API requests to accept the requests. To allow Zscaler to perform this validation, you need to add your OAuth 2.0 authorization servers to the ZIA Admin Portal. After the authorization server is added, the Zscaler service can obtain the public key set from the authorization server’s JWKS endpoint and cryptographically verify the JWT signature.
OAuth 2.0 Authorization Server configuration provides the following benefits and enables you to:
- Configure third-party authorization servers to provide secured access to ZIA API resources.
- Automate authorization and authentication of API clients using trusted third-party OAuth 2.0 services.
In addition to cryptographically verifying the JWT, the Zscaler service allows you to mandate verification against some of the supported JWT claims, including audience, issuer, and client ID. You can specify these values when adding the authorization server to the ZIA Admin Portal.
After verifying the authenticity of the JWT, the Zscaler service evaluates the scope claim and other additional claims, if any, to determine whether to accept or reject the API request.
- The Zscaler service supports OAuth 2.0 implementations with PingFederate, Okta, and Microsoft Entra ID (formerly Azure Active Directory).
- OAuth 2.0 authentication is supported only for [cloud service API](/zia/about-api#CloudServiceAPI).
About the OAuth 2.0 Authorization Servers Page
On the OAuth 2.0 Authorization Servers page (Administration > Cloud Service API Security > OAuth 2.0 Authorization Servers), you can do the following:
- View the base URL for the cloud service API.
- [Add a third-party OAuth 2.0 authorization server.](/zia/managing-oauth-2.0-authorization-servers#add-auth-server)
- View information regarding your authorization server. For each authorization server, you can view:
- **Authorization Server Name:** The name provided for the authorization server configuration.
- **Status:** The status of the authorization server configuration (enabled or disabled).
- **Description:** The description of the authorization server configuration.
- **Last Successful Fetch Time:** The date and time when the authorization server’s public key was last fetched from its JWKS endpoint.
- [Edit the authorization server.](/zia/managing-oauth-2.0-authorization-servers#edit-auth-server)
- [Delete the authorization server.](/zia/managing-oauth-2.0-authorization-servers#delete-auth-server)
- [Modify the table and its columns.](/zia/how-do-i-use-tables-admin-portal)
- Go to the [Sandbox API Token](/zia/about-sandbox-api-token) tab.
- Go to the [Cloud Service API Key](/zia/about-cloud-service-api-key) tab.
![A screenshot of OAuth 2.0 Authorization Servers page](/downloads/zia/authentication-administration/api-key-management/about-oauth-20-authorization-servers/oauth2-authorization-servers.png)