# Understanding OneAPI Authentication
Source: https://help.zscaler.com/unified/understanding-oneapi-authentication
PDF: https://help.zscaler.com/pdf/com/en/1525096.pdf

OneAPI authentication is the process of verifying the identity of an API client attempting to access the Zscaler service [API resources](/unified/viewing-api-resources). ZIdentity is the centralized platform that acts as an authorization server to validate the [API clients](/unified/about-api-clients) and provide access to the API resources. This process ensures that only authorized API clients can interact with the API resources, protecting the applications and sensitive data from unauthorized access and potential security breaches.
Zscaler OneAPI is a unified and secure gateway that provides programmatic access to API resources of various Zscaler services. OneAPI is based on the [OAuth 2.0](https://auth0.com/docs/authenticate/protocols/oauth) authorization framework. To learn more, see [Understanding OneAPI](/oneapi/understanding-oneapi).
To use OneAPI, the Zscaler services must be linked to ZIdentity.
The OneAPI authentication framework includes the following benefits:
- Secure authentication methods that are compliant with industry standards.
- Secure interactions between the API clients and API resources.
- Role-based access control (RBAC) is implemented to restrict the API client's access to specific API resources.
How OneAPI Authentication Works
ZIdentity provides support for JSON Web Key Set (JWKS) URL, Certificate or Public Key, and Client Secret authentication methods for authenticating to OneAPI. You can choose any of these authentication methods.
**JWKS and Certificate**
The authentication workflow for JWKS and Certificate includes the following stages:
- The [API client](/unified/adding-api-client) that is configured in the Admin Portal generates a JSON Web Token (JWT) on its local system, signing it with a private key.
- The public key, corresponding to the private key used to sign the JWT is hosted at the JWKS URL on a web server that is accessible and trusted by ZIdentity.
- The API client uses the JWT and makes a request to ZIdentity. ZIdentity retrieves the public key from the JWKS URL to verify the JWT’s signature. If the signature is valid, the API client is then authenticated and granted access to the API resource.
**Client Secret**
The authentication workflow for Client Secret includes the following stages:
-
The [API client](/unified/adding-api-client) and ZIdentity (API server) must agree on a shared secret key prior to accessing the API resources. This secret is stored securely on both the API client and ZIdentity.
For OneAPI, the secret key is created when defining an API client.
- When the API client makes a request, the secret is included in the request header, usually in an encrypted or hashed form for security purposes.
- ZIdentity validates the secret against its saved copy. If the secret matches, the API client is authenticated and granted access to the API resource.