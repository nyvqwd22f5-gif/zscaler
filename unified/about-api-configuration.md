# About API Configuration
Source: https://help.zscaler.com/unified/about-api-configuration
PDF: https://help.zscaler.com/pdf/com/en/1516271.pdf

Your organization's API key is initially provisioned by Zscaler, enabled, and displayed within the API Key Management page along with the base URL. The base URL and key are required to authenticate via the API and create a session.
API Key Management provides the following benefits and enables you to:
- Provide API key access only to authorized admins configured with appropriate functional scope access to the API services.
- Regenerate the API key whenever required or in events when you suspect vulnerabilities for an attack.
- Ensure no further API requests are possible after you finish consuming the API services by deleting the API key.
An organization can have only one API key. However, if you are managing multiple organizations within Zscaler and want to maintain the same key string across them, Zscaler recommends editing the key instead of adding a new one or regenerating it. This allows you to use the same key string across organizations, if necessary.
About the API Key Management Page
On the API Key Management page (Administration > API Configuration > Legacy API > Cloud & Branch Connector API), you can do the following:
- View the base URL for the API.
- [Add a new Cloud Service API Key](/unified/managing-organization-api-keys). You must delete the existing key before you can add a new one.
- View information regarding your organization's API key. For the key, you can see:
- **Key**: The API key string.
- **Last Modified By**: Currently, only Zscaler modifies the key.
- **Last Modified On**: The date and time the key was last modified.
- Modify the table and its columns.
- [Edit the API key](/unified/managing-organization-api-keys).
- [Regenerate the API key](/unified/managing-organization-api-keys).
- [Delete the API key](/unified/managing-organization-api-keys).
![The API Key Management page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/administration/api-key-management/about-api-key-management/About%20API%20Key%20Management%20scrnsht%20update.jpg)