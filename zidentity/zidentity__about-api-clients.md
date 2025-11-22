# About API Clients
Source: https://help.zscaler.com/zidentity/about-api-clients
PDF: https://help.zscaler.com/pdf/com/en/1499371.pdf

An API client refers to any application or service that wants to access the [Zscaler API resources](/zidentity/viewing-api-resources) and retrieve data. You can [configure and manage the API clients](/zidentity/adding-api-client) in the ZIdentity Admin Portal, along with their authentication information and necessary scope to access the API resources. ZIdentity is the authorization server that validates the API client's request and issues an [access token](/zidentity/about-access-tokens) that must be used to access the API resources via the [OneAPI server](/oneapi/understanding-oneapi).
API clients include the following key features and benefits:
- Consistent API experience across all Zscaler services.
- Consistent authorization through ZIdentity.
- Access resources across all Zscaler services with entitlements via role-based access control.
About the API Clients Page
On the API Clients page (Integration > API Clients), you can do the following:
- [Add an API client](/zidentity/adding-api-client).
- View the list of API clients you've configured. For each API client, you can see:
- **Name**: The name of the API client.
- **Client ID**: The unique identifier for the API client.
- **Status**: The status (Active or Inactive) of the API client.
- Reset the page to the default view.
- Search for an API client.
- [Edit an API client](/zidentity/editing-or-deleting-api-client).
- [Delete an API client](/zidentity/editing-or-deleting-api-client).
![The API client page](/downloads/zslogin/authentication/api-client-authentication/about-api-clients/zid-apiclientpage.png)