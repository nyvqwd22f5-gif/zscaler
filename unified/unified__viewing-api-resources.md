# Viewing API Resources
Source: https://help.zscaler.com/unified/viewing-api-resources
PDF: https://help.zscaler.com/pdf/com/en/1505616.pdf

API resources refer to the Zscaler APIs available via the OneAPI gateway. The API resources are a collection of [Zscaler API endpoints](/oneapi/understanding-oneapi-endpoints) that represent various data entities, services, or functionalities that can be accessed by the [API clients](/unified/about-api-clients). To learn more, see [Understanding OneAPI](/oneapi/understanding-oneapi).
The API resources are available for the Zscaler services (Internet & SaaS, Private Applications, Client Connector, etc.) that are linked to ZIdentity and the API client can access the API resources of the linked Zscaler services.
The API resources are automatically created in the Admin Portal based on the role-based access control (RBAC) roles applicable to the APIs within the various Zscaler services. Each API client is assigned one or more roles (API resources), which define the specific endpoints and operations that the API client is permitted to access. This ensures that the API client can only interact with specific parts of the API, thereby enhancing security and reducing the risk of unauthorized or unintentional actions.
While [configuring the API client](/unified/adding-api-client), you can select the API resources that determine the permissions (scope) the API client has to access the API resources of each Zscaler service. You can select only one API resource for each Zscaler service.
To view the API resources:
-
Go to **Administration** > **API Configuration > OneAPI > API Resources**.
The **API Resources** page appears.
[See image.](#zid-apiresourcepage)
-
Click the **View** icon (![zid-viewicon.png](/downloads/zidentity/integration/oneapi-authentication/viewing-api-resources/zid-viewicon.png)
) to see the API resources available for each Zscaler service.
[See image.](#zd-apiresourcelist)
[]![API Resources page with list of API Resources. ](/downloads/zidentity/integration/oneapi-authentication/viewing-api-resources/zid-apiresources.png)
[]![API Resource page displaying details of API.](/downloads/zidentity/integration/oneapi-authentication/viewing-api-resources/zid-apiresourcelist.png)