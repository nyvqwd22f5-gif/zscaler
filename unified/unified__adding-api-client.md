# Adding an API Client
Source: https://help.zscaler.com/unified/adding-api-client
PDF: https://help.zscaler.com/pdf/com/en/1505621.pdf

Any application or service that wants to access the [Zscaler API resources](/oneapi/understanding-oneapi-endpoints) must have an [API client](/unified/about-api-clients) created and provisioned in the Admin Portal. When an API client sends an authentication request, ZIdentity verifies the client secret or assertion depending on the authentication mechanism and issues an access token. The API client uses this access token to request access to the required API resources. ZIdentity supports the [OAuth 2.0 Client Credentials Grant type](https://oauth.net/2/grant-types/) to authorize the API clients.
ZIdentity administrators assigned with Full permission to access the API Clients and API Resources modules can configure API clients in the Admin Portal. To learn more, see [Admin Roles and Permissions](/unified/admin-roles-and-permissions).
To add an API client:
- Go to **Administration** > A**PI Configuration** > **OneAPI** >** API Clients**.
- Click **Add API Client**.
- On the **Add API Client** page, the **Client **tab is selected by default. Enter the following details:
- **Client Information**:
- **Name**: Enter a name to identify the API client.
- **Description**: Enter a brief description that indicates the purpose of the API client (e.g., a software application or a script that is using this name to interact with OneAPI).
-
**Status**: Enable the status. This allows the API client to authenticate and use the API resources.
When the status is disabled, the API client cannot get the access tokens issued by ZIdentity.
- **Access Token Lifetime**: The validity of the access token that is used to access the API resource. Enter the time in minutes. The minimum and maximum validity periods are 1 minute and 24 hours, respectively.
-
**Client Authentication**: Configure any of the following supported authentication methods: JSON Web Key (JWK) specification, certificates and public keys, or Secret. You also need to set up the same authentication method in your application. For example, if you configure JWK in the Admin Portal, your application should sign and verify the JSON Web Token (JWT) with the same key when sent for authentication.
-
**Client JWKs URL**: Enter the **Client JWK **URL where the key must be obtained for verification. JWT is a URL-safe token used to securely transmit data between applications A JWK URL hosts a set of public keys in JSON format, which is used by the API server to verify the signatures of JWT issued by the API client.
[See image.](#oapi-jwk)
-
**Certificates/Public Keys**: Upload a .pem file that contains the public key. ZIdentity reads the public key and verifies the authentication.
[See image.](#oapi-uploadkey)
-
**Secret**: Click **Add**. A key is auto-generated and displayed along with the validity period. This key is generated once, and it cannot be updated. The minimum duration is 30 days and the maximum duration is 365 days. Ensure to copy the secret key and save it in your local folder as it is not going to be displayed again. You can add a maximum of two client secrets. If you add a third one, the new value replaces the most recent client secret. So, at any point in time, there are only two client secrets.
[See image.](#oapi-secret)
[See image.](#addclient)
-
Select the **Resources** tab.
You can see the APIs for Zscaler services that are linked to your tenant along with the role (scope). Scope refers to the permission that limits the access to specific API resources. The role is assigned in the Admin Portal and is synced with ZIdentity. To learn more, see [Understanding OneAPI](/oneapi/understanding-oneapi).
[See image.](#oapi-resource)
- Select the required API resources that the API client can access. You can select only one API resource for each Zscaler service and depending on the scope that is assigned.
-
Click **Save**.
When you save the API client details, ZIdentity auto-generates a client ID and it is displayed on the **API Clients** page.
- Copy the Client ID and save it, as you need to provide the Client ID along with the token or secret to make the API call.
- You can also copy the client ID from the **Edit API Client** window.
- On the **API Clients** page, click the **Edit** icon for the newly configured API client.
-
In the **Edit API Client** window, copy the Client ID and save it in your local folder.
[See image.](#oapi-clientid)
[]![Add an API client and set up the authentication method](/downloads/zslogin/authentication/api-client-authentication/configuring-api-client/zid-addapiclient.png)
[]![Upload a certificate or public key](/downloads/zslogin/authentication/api-client-authentication/configuring-api-client/zid-cert.png)
[]![Add the client JWK URL](/downloads/zslogin/authentication/api-client-authentication/configuring-api-client/zid-jwk.png)
[]![Set up the client secret and validity period](/downloads/zslogin/authentication/api-client-authentication/configuring-api-client/zid-secret.png)
[]![Select the API resources that the API client can access.](/downloads/zslogin/authentication/api-client-authentication/configuring-api-client/zid-resources.png)
[]![Copy the client ID](/downloads/zslogin/authentication/api-client-authentication/configuring-api-client/zd-clientid.png)