# Viewing API Resources
Source: https://help.zscaler.com/zidentity/viewing-api-resources
PDF: https://help.zscaler.com/pdf/com/en/1503371.pdf

API resources refer to the Zscaler APIs available via the OneAPI gateway. The API resources are a collection of [Zscaler API endpoints](/oneapi/understanding-oneapi-endpoints) that represent various data entities, services, or functionalities that can be accessed by the [API clients](/zidentity/about-api-clients). To learn more, see [Understanding OneAPI](/oneapi/understanding-oneapi) and [Adding API Roles](/zia/adding-api-roles).
The API resources are available for the Zscaler services (Zscaler Internet Access (ZIA), Zscaler Private Access (ZPA), Zscaler Client Connector, etc.) that are linked to ZIdentity and the API client can access the API resources of the linked Zscaler services.
The API resources are automatically created in the ZIdentity Admin Portal based on the role-based access control (RBAC) roles applicable to the APIs within the various Zscaler services. Each API client is assigned one or more roles (API resources), which define the specific endpoints and operations that the API client is permitted to access. This ensures that the API client can only interact with specific parts of the API, thereby enhancing security and reducing the risk of unauthorized or unintentional actions.
While [configuring the API client](/zidentity/adding-api-client), you can select the API resources that determine the permissions (scope) the API client has to access the API resources of each Zscaler service. You can select only one API resource for each Zscaler service.
To view the API resources:
-
Go to **Integration** > **API Resources**.
The **API Resources** page appears.
[See image.](#zid-apiresourcepage)
-
Click the **View** icon (![zid-viewicon.png](/downloads/zidentity/integration/oneapi-authentication/viewing-api-resources/zid-viewicon.png)
) to see the API resources available for each Zscaler service.
[See image.](#zd-apiresourcelist)
[]![Click the View icon to see the API resources available ](/downloads/zidentity/integration/oneapi-authentication/viewing-api-resources/zid-apiresources.png)
[]![zid-apiresourcelist.png](/downloads/zidentity/integration/oneapi-authentication/viewing-api-resources/zid-apiresourcelist.png)