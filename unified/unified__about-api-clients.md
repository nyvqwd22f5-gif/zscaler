# About API Clients
Source: https://help.zscaler.com/unified/about-api-clients
PDF: https://help.zscaler.com/pdf/com/en/1505611.pdf

An API client refers to any application or service that wants to access the [Zscaler API resources](/unified/viewing-api-resources) and retrieve data. You can [configure and manage the API clients](/unified/adding-api-client) in the Admin Portal, along with their authentication information and necessary scope to access the API resources. ZIdentity is the authorization server that validates the API client's request and issues an [access token](/unified/about-access-tokens) that must be used to access the API resources via the [OneAPI server](/oneapi/understanding-oneapi).
API clients include the following key features and benefits:
- Consistent API experience across all Zscaler services.
- Consistent authorization through ZIdentity.
- Access resources across all Zscaler services with entitlements via role-based access control.
About the API Clients Page
On the API Clients page (Administration > API Configuration > OneAPI > API Clients), you can do the following:
- [Add an API client](/unified/adding-api-client).
- View the list of API clients you've configured. For each API client, you can see:
- **Name**: The name of the API client.
- **Client ID**: The unique identifier for the API client.
- **Status**: The status (Active or Inactive) of the API client.
- Reset the page to the default view.
- Search for an API client.
- [Edit an API client](/unified/editing-or-deleting-api-client).
- [Delete an API client](/unified/editing-or-deleting-api-client).
![The API client page](/downloads/zslogin/authentication/api-client-authentication/about-api-clients/zid-apiclientpage.png)