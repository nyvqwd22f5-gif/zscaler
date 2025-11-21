#  Securing ZIA APIs with OAuth 2.0
Source: https://help.zscaler.com/zia/securing-zia-apis-oauth-2.0
PDF: https://help.zscaler.com/pdf/com/en/1415051.pdf

The Zscaler service supports OAuth 2.0 authentication to securely access the [cloud service API](/zia/about-api#CloudServiceAPI). OAuth 2.0 authentication allows third-party applications to obtain controlled access to protected resources using access tokens. The Zscaler service uses the Client Credentials OAuth flow, in which the clients exchange their credentials for an access token and gain access to the cloud service API, outside the context of users. The Zscaler service supports OAuth 2.0 implementations with PingFederate, Okta, and Microsoft Entra ID (formerly Azure Active Directory).
OAuth 2.0 authentication offers the following advantages over other authentication methods:
- **Better Security:** OAuth 2.0 secures your APIs with dynamic credentials, which are time-bound and generated on demand for a client.
- **Limits Exposure of Credentials:** Unlike the authentication model that uses API keys and ZIA admin credentials and may involve user management outside the organization's identity provider, OAuth 2.0 does not require ZIA admin credentials for authentication.
- **Granular Access Control:** The Client Credentials OAuth flow employs [API Roles](/zia/adding-api-roles) to define permissions required to access specific categories of cloud service API. Unlike admin roles, API roles are not assigned to ZIA admin users. Instead, API roles are associated with the client applications that are accessing the API. OAuth 2.0 provides added security to API access by isolating API permissions from admin users with access to the ZIA Admin Portal.
- **Reduced Maintenance:** OAuth 2.0 does not require obfuscation of credentials, unlike API keys which need to be [obfuscated](/zia/getting-started-zia-api#CreateSession) on the client with additional programming for enhanced security.
OAuth 2.0 authentication is supported only for [cloud service API](/zia/about-api#CloudServiceAPI).
Terminologies and Concepts
OAuth 2.0 authentication includes the following components:
**Resource Server:** The host in which the protected resources reside. After successful authorization of client applications, the resource server grants clients access to protected resources. In Zscaler’s OAuth 2.0 authentication model, the cloud service API acts as the resource server and authorizes client applications to make API calls.
**Authorization Server:** The identity provider that accepts authorization requests from clients and issues signed access tokens upon successful authorization.
**Client:** The client application that requests access to protected resources residing in the resource server (i.e., cloud service API). The client authenticates with the authorization server to obtain an access token and then uses the access token to access the cloud service API.
**Access Tokens:** An access token is a string issued to a client application by the authorization server. The client application uses the access token to identify itself and gain authorized access to protected resources residing in the resource server (i.e., cloud service API).
**Grant Type:** Also referred to as OAuth flows, grant types define the various methods in which a client application can obtain an authorization grant from the authorization server and also the sequence in which the OAuth 2.0 authorization process takes place. The Zscaler service uses Client Credentials grant type, which allows clients to access protected resources outside the context of users.
**Scope:** Scope defines the specific permissions required by a client application to access the data in the resource server (i.e., cloud service API). In Zscaler’s OAuth 2.0 authentication model, scope is defined using [API Roles](/zia/adding-api-roles) and must be associated with the client application in the OAuth 2.0 service console.
[]OAuth 2.0 Flow
The Zscaler service uses the Client Credentials OAuth flow. In this model, client applications make API calls to the cloud service API using an access token obtained from the authorization server in exchange for their credentials. Therefore, the clients access the cloud service API resources on their behalf without requiring any user interaction.
![An illustration of OAuth flow of Client Credentials type](/downloads/zia/documentation-knowledgebase/oauth-client-credentials-flow.png)
-
**A client requests an access token from the authorization server**
A client application registered with the authorization server sends an authorization request with its credentials (i.e., client ID and client secret) to the authorization server. In addition to the client credentials, the authorization request must specify the required scope and the grant type.
-
**The authorization server authenticates the client and provides an access token**
The authorization server validates the client's credentials and provides the client with a signed JWT access token upon successful authorization. The response from the authorization server contains the access token, token type (bearer token), and the token expiration time.
-
**The client sends the access token to the resource server**
The client sends an API request to the resource server (i.e., cloud service API) with the signed access token (JSON Web Token) in the request authorization header.
-
**The resource server grants access to protected resources**
The following series of events take place before the resource server (i.e., cloud service API) can accept the API request:
- The Zscaler service extracts the JWT access token from the API request header and decodes the token to fetch information such as the key ID, algorithm, scope, client ID, audience, expiration, and other configured values.
- The Zscaler service cryptographically verifies the signature of the JWT token using the authorization server's public key.
-
If the JWT signature verification is successful, the Zscaler service validates the JWT’s scope claim, which is in `<Zscaler Cloud Name>``::``<Org ID>``::``<API Role>` format. The `<API Role>` value in the scope is used to authorize the API request. This value must match with one of the API Roles configured in the ZIA Admin Portal. If no match is found, the API request is rejected.
The Zscaler service might verify any additional claims in the JWT, such as audience, issuer, client ID, etc.
- Finally, the Zscaler service grants the client application access to the requested API resources.
Setting up OAuth 2.0
You need to set up the following configurations sequentially before initiating cloud service API authentication using OAuth 2.0:
- [Configure API Roles in the ZIA Admin Portal](#configure-api-roles)
- [Register applications on the external OAuth provider](#register-applications-on-auth-server)
- [Add OAuth 2.0 Authorization Servers to the ZIA Admin Portal](#add-auth-server)
API operations that are authenticated using OAuth 2.0 are associated with an auto-generated Admin ID and recorded in [Audit Logs](/zia/about-audit-logs). An Admin ID is generated for each API role in the following format: `oauth-``<rolename>``$@``<orgid>``.``<cloud_domain>`. To learn more, see [Adding API Roles](/zia/adding-api-roles).
[]With the OAuth 2.0 authentication model, the Zscaler service provides role-based, controlled access to its cloud service API resources. API roles define the scope of access for client applications to specific categories of cloud service API endpoints.
API roles are associated with the client applications registered with the authorization server using the scope claim. The scope claim is included in the JWT access token issued to the client by the authorization server, and it is used by the Zscaler service to validate and authorize the client.
You can add and manage API roles on the Role Management page. To learn more, see [Adding API Roles](/zia/adding-api-roles).
- When authorizing API requests, the Zscaler service uses the scope claim to obtain your organization's Zscaler cloud name, organization ID, and API role. Therefore, a [specific format](#scope-claim) must be followed when configuring the scope claim.
- Unlike admin roles, API roles are associated with client applications instead of administrators.
[]Register the client applications on your external OAuth 2.0 service provider (i.e., PingFederate, Okta, or Microsoft Entra ID) with the required scope and configure them appropriately. The scope claim must contain your organization’s Zscaler cloud name, organization ID, and API role information obtained from the ZIA Admin Portal. For added security, you can configure optional claims, such as audience, issuer, client ID, etc., for the client.
The claim names might vary with the OAuth 2.0 vendors. Refer to the vendor documentation and use the names recommended by the vendors.
[]
-
-
-
| Claim | Description |
| ----- | ----------- |
| scope, scp, or roles | (Required) Permissions required by the client application to access the protected resources. You must configure the scope in the `<Zscaler Cloud Name>``::``<Org ID>``::``<API Role>` format, where:`<Zscaler Cloud Name>` represents the cloud on which your organization is provisioned.`<Org ID>` represents your organization ID obtained from the ZIA Admin Portal under Administration > Company Profile.`<API Role>` represents an API role configured in the ZIA Admin Portal under Administration > Role Management.For example, `zscalerbeta.net::272378::sampleRole`If you are using PingFederate as your OAuth 2.0 authorization server, ensure that the **Scope Claim Name** is set to `scp` within the Access Token Management instance. |
| iss | (Optional) The issuer of the JWT. |
| aud | (Optional) The intended recipient of the JWT. |
| client_id, cid, or appid | (Optional) A custom claim that uniquely identifies the client application registered on the authorization server and requests access to cloud service API endpoints. |
You can configure and manage the lifetime of the access token on the OAuth service console.
To learn how to set up client applications on your OAuth provider, refer to the respective help documentation.
[]The Zscaler service requires you to add your authorization servers to the ZIA Admin Portal to verify the authenticity of the access token in API requests and optionally validate against various supported claims.
You can add and manage your authorization servers from the OAuth 2.0 Authorization Servers page. To learn more, see [About OAuth 2.0 Authorization Servers](/zia/about-oauth-2.0-authorization-servers).