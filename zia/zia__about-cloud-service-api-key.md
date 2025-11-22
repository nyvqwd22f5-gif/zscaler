# About Cloud Service API Key
Source: https://help.zscaler.com/zia/about-cloud-service-api-key
PDF: https://help.zscaler.com/pdf/com/en/1400501.pdf

You can authenticate with the cloud service API using a combination of API key (an alphanumeric key of 12 characters in length) and ZIA admin credentials (i.e., username and password).
If you need to obtain API keys or secrets to access [Zscaler OneAPI](/oneapi) endpoints, see [API Client Authentication](/zidentity/integration/oneapi-authentication) in ZIdentity.
Cloud Service API Key enhances your API experience by enabling you to:
- Prevent the misuse of API services by providing API key access only to authorized ZIA admins configured with appropriate functional scope access to the API services.
- Prevent API service abuse via stolen API key by regenerating the API key whenever required or in events you suspect vulnerabilities for an attack.
- Ensure no further API requests are possible after you finish consuming the API services by deleting the API key.
You need a valid [API subscription](/zia/viewing-subscriptions) to access and manage your organization’s API key. When an API subscription is applied to your organization, your organization's API key is initially provisioned by Zscaler, enabled, and displayed within the Cloud Service API Key page along with the base URL. The base URL and key are required in order to [authenticate via the API and create a session](/zia/api-getting-started#CreateSession).
In the Cloud Service API Key page, you can:
- Remove the API key and add a new one.
- Edit the API key.
- Regenerate the API key, which randomly generates a new key string that replaces the old string.
An organization can only have one API key. However, if you are managing multiple organizations within Zscaler and want to maintain the same key string across them, Zscaler recommends editing the key instead of adding a new one or regenerating it. This allows you to use the same key string across organizations, if necessary.
Adding, editing, or regenerating an API key, immediately invalidates the old key. If you replaced or edited a key, you also need to replace any references to the old key within any code developed for your organization. To learn more about the cloud service API, including developer getting started information and API endpoints, see [Getting Started](/zia/api-getting-started) and the [API Reference](/zia/about-api).
Admins have view access to the Cloud Service API Key page information within the [Zscaler Cloud Connector Portal](/cloud-branch-connector/about-cloud-connector-portal).
About the Cloud Service API Key Page
On the Cloud Service API Key page (Administration > Cloud Service API Security > Cloud Service API Key), you can do the following:
- View the base URL for the cloud service API.
- [Add a new Cloud Service API Key](/zia/managing-cloud-service-api-key#AddKey). You must delete the existing key before you can add a new one.
- View information regarding your organization's cloud service API key. For the key, you can see:
- **Key:** The API key string.
- **Last Modified By:** The last admin to modify the key.
- **Last Modified On:** The date and time the key was last modified.
- [Edit the API key.](/zia/managing-cloud-service-api-key#EditKey)
- [Regenerate the API key.](/zia/managing-cloud-service-api-key#RegenerateKey)
- [Delete the API key.](/zia/managing-cloud-service-api-key#DeleteKey)
- [Modify the table and its columns.](/zia/how-do-i-use-tables-admin-portal)
- Go to the [OAuth 2.0 Authorization Servers](/zia/about-oauth-2.0-authorization-servers) or [Sandbox API Token](/zia/about-sandbox-api-token) tab.
![Cloud Service API Key page](/downloads/zia/authentication-administration/api-security/about-cloud-service-api-key/ZIA-cloud-service-api-key.png)