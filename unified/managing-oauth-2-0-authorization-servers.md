# Managing OAuth 2.0 Authorization Servers
Source: https://help.zscaler.com/unified/managing-oauth-2-0-authorization-servers
PDF: https://help.zscaler.com/pdf/com/en/1495096.pdf

When using OAuth 2.0 for API authentication, the Zscaler service requires you to add your authorization servers to the Admin Portal in order to authorize client applications. You can add and manage your authorization servers from the OAuth 2.0 Authorization Servers page. You need an admin role with the API Key Management permission enabled to manage your authorization servers. To learn more, see [Adding Admin Roles](/unified/adding-admin-roles).
From the OAuth 2.0 Authorization Servers page, you can perform the following tasks:
- [Add an authorization server](#add-auth-server)
- [Edit an authorization server](#edit-auth-server)
- [Delete an authorization server](#delete-auth-server)
- A valid API subscription is required to add or manage authorization servers in the Admin Portal.
- If your API subscription expires, you still have access to the OAuth 2.0 Authorization Servers page, but you cannot make any modifications. The authorization server configuration is re-enabled after your subscription is renewed.
- Zscaler can disable your authorization server configuration if your organization exceeds the threshold for the number of API calls allowed or if the code developed for your organization violates Zscaler's terms and conditions. When this occurs, the added authorization servers appear disabled, and you cannot add, edit, or delete the servers. Also, all API requests with the JWT issued by the disabled authorization server are rejected. Contact Zscaler Support to re-enable the authorization server configuration.
[]An organization can have up to two OAuth 2.0 authorization servers with only one being enabled at a time. To add your authorization server:
- Go to **Administration** > **API Configuration** > **Legacy API** > **Internet & SaaS API**.
- Click the **OAuth 2.0 Authorization Servers** tab.
-
Click **Add Authorization Server**.
The **Add Authorization Server** window opens.
- In the **Add Authorization Server** window:
- **Enable:** Enable the authorization server configuration. The authorization server configuration must be enabled for the JWT verification to take place. Only one authorization server can be enabled at a time.
- **Name:** Enter a name for your authorization server configuration. The name can only contain alphanumeric characters without spaces and cannot exceed 64 characters.
- **Description:** Enter a description for the authorization server configuration. The description cannot exceed 256 characters.
-
**OAuth 2.0 JWKS Location:** Enter the JSON Web Key Set (JWKS) endpoint that returns the public key set of the authorization server in the JWKS format. This public key set is fetched by the Zscaler service on a regular basis to cryptographically verify the authenticity of the JWT in API requests.
Click **Validate** to verify that the JWKS endpoint is configured correctly. The **Save** button appears only after the JWKS endpoint is validated.
- **JWKS Server Certificate Validation:** If the authorization server uses an SSL certificate signed by an unrecognized Certificate Authority (CA) or has a root certificate issued by an unrecognized CA, an SSL handshake error occurs when the Zscaler service tries to establish an SSL connection with the JWKS endpoint. To avoid this error, you can disable the certificate validation using the **JWKS Server Certificate Validation** option or change the server certificate.
- **Audience URI:** (Optional) Enter the `aud` claim value that identifies the recipient of the JWT. If a value is specified for this field, requests are accepted only if the JWT contains a matching `aud` claim.
- **Issuer URI:** (Optional) Enter the `iss` claim value that identifies the issuer of the JWT. If a value is specified for this field, requests are accepted only if the JWT contains a matching `iss` claim.
-
**Client ID:** (Optional) Enter the client ID of the client application that is requesting access to the Internet & SaaS API service. The client ID is issued by the authorization server at the time of client application registration and can be obtained from the OAuth 2.0 service console. If a value is specified for this field, requests are accepted only if the JWT contains a matching `client_id` claim. If multiple client applications need access to the Internet & SaaS API, leave this field blank.
Some identity providers may use `cid` or `appid `claim in place of `client_id`. The Zscaler service matches the configured client ID value against the available claim from the group.
[See image.](#auth-server-configuration-window)
- Click **Save**.
[]You can edit the OAuth 2.0 authorization servers added to the Admin Portal. If the authorization server configuration is already in use, any changes to the configuration may lead to disruption in the API service. To avoid this, ensure that the changes are properly configured in both the Admin Portal and the client applications.
To edit an authorization server configuration:
- Go to **Administration** > **API Configuration** > **Legacy API** > **Internet & SaaS API**.
- Click the **OAuth 2.0 Authorization Servers** tab.
-
Click the **Edit** icon next to the authorization server that you want to edit.
The **Edit Authorization Server** window opens.
- In the **Edit Authorization Server** window, you can modify the necessary configurations. For the list of fields available in this window, see [Add an Authorization Server](#add-auth-server).
- Click **Save**.
[]You can delete the OAuth 2.0 authorization servers added to the Admin Portal. If you delete an authorization server that is currently in use, client applications can no longer access the Internet & SaaS API using OAuth 2.0.
To delete an authorization server configuration:
- Go to **Administration** > **API Configuration** > **Legacy API** > **Internet & SaaS API**.
- Click the **OAuth 2.0 Authorization Server**s tab.
-
Click the **Delete** icon next to the authorization server that you want to delete.
A confirmation dialog box appears.
[See image.](#auth-server-deletion-confirmation)
- Click **OK**.
[]![A screenshot of the Add Authorization server window](/downloads/zia/authentication-administration/api-security/managing-oauth-20-authorization-servers/add-auth-server.png)
[]![A screenshot of the confirmation dialog for OAuth 2.0 Authorization server ](/downloads/zia/authentication-administration/api-key-management/managing-oauth-20-authorization-servers/delete-auth-server.png)