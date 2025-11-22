# About Cloud Service API Key
Source: https://help.zscaler.com/unified/about-cloud-service-api-key
PDF: https://help.zscaler.com/pdf/com/en/1494841.pdf

You can authenticate with the cloud service API using a combination of API key (an alphanumeric key of 12 characters in length) and admin credentials (i.e., username and password).
Cloud Service API Key enhances your API experience by enabling you to:
- Prevent the misuse of API services by providing API key access only to authorized Internet & SaaS admins configured with appropriate functional scope access to the API services.
- Prevent API service abuse via stolen API key by regenerating the API key whenever required or in events you suspect vulnerabilities for an attack.
- Ensure no further API requests are possible after you finish consuming the API services by deleting the API key.
You need a valid [API subscription](/unified/viewing-subscriptions) to access and manage your organization’s API key. When an API subscription is applied to your organization, your organization's API key is initially provisioned by Zscaler, enabled, and displayed within the Cloud Service API Key page along with the base URL. The base URL and key are required in order to authenticate via the API and create a session.
On the Cloud Services API Key page, you can:
- Remove the API key and add a new one.
- Edit the API key.
- Regenerate the API key, which randomly generates a new key string that replaces the old string.
An organization can only have one API key. However, if you are managing multiple organizations within Zscaler and want to maintain the same key string across them, Zscaler recommends editing the key instead of adding a new one or regenerating it. This allows you to use the same key string across organizations, if necessary.
Adding, editing, or regenerating an API key, immediately invalidates the old key. If you replace or edit a key, you also need to replace any references to the old key within any code developed for your organization.
About the Cloud Service API Key Page
On the Cloud Service API Key page (Administration > API Configuration > Legacy API > Internet & SaaS API), you can do the following:
- View the base URL for the cloud service API.
- [Add a new API Key](/unified/managing-internet-saas-api-key). You must delete the existing key before you can add a new one.
- View information regarding your organization's cloud service API key. For the key, you can see:
- **Key:** The API key string.
- **Last Modified By:** The last admin to modify the key.
- **Last Modified On:** The date and time the key was last modified.
- [Edit the API key.](/unified/managing-internet-saas-api-key)
- [Regenerate the API key.](/unified/managing-internet-saas-api-key)
- [Delete the API key.](/unified/managing-internet-saas-api-key)
- [Modify the table and its columns.](/unified/using-tables)
- Go to the [OAuth 2.0 Authorization Servers](/unified/about-oauth-2-0-authorization-servers) or [Sandbox API Token](/unified/about-sandbox-api-token) tab.
![A screenshot of the Cloud Service API Key page](/downloads/zia/authentication-administration/api-key-management/about-cloud-service-api-key-management/cloud-service-api-key.png)