# About Sandbox API Token
Source: https://help.zscaler.com/unified/about-sandbox-api-token
PDF: https://help.zscaler.com/pdf/com/en/1494851.pdf

You can authenticate the Sandbox Submission API using a combination of API token and admin credentials (i.e., username and password).
Sandbox API Token enhances your API experience by enabling you to:
- Prevent the misuse of API services by providing API token access only to authorized Internet & SaaS admins configured with appropriate functional scope access to the API services.
- Prevent API service abuse via stolen API token by regenerating the API token whenever required or in events you suspect vulnerabilities for an attack.
- Ensure no further API requests are possible after you finish consuming the API services by deleting the API token.
You need a valid [Sandbox subscription](/unified/viewing-subscriptions) to access and manage your organization’s API token. When the Sandbox subscription is applied to your organization, your organization's API token is initially provisioned by Zscaler, enabled, and displayed within the Sandbox API Token page along with the base URL. The base URL and token are required in order to authenticate via the API and create a session.
On the Sandbox API Token page, you can:
- Remove the API token and add a new one.
- Regenerate the API token, which randomly generates a new token string that replaces the old string.
An organization can only have one API token. However, if you are managing multiple organizations within Zscaler and want to maintain the same token string across them, Zscaler recommends editing the token instead of adding a new one or regenerating it. This allows you to use the same token string across organizations, if necessary.
Adding, or regenerating an API token, immediately invalidates the old token. If you replace or edit a token, you also need to replace any references to the old token within any code developed for your organization.
About the Sandbox API Token Page
On the Sandbox API Token page (Administration > API Configuration > Legacy API > Internet & SaaS API > Sandbox API Token), you can do the following:
- View the base URL for the Sandbox Submission API.
- [Add a new Sandbox API Token.](/unified/managing-sandbox-api-token) You must delete the existing token before adding a new one.
- View information regarding your organization's sandbox API token. For the token, you can see:
- **Sandbox API Token:** The API token string, displayed upon clicking the eye icon.
- **Last Modified By:** The last admin to modify the token.
- **Last Modified On:** The date and time the token was last modified.
- [Regenerate the API token.](/unified/managing-sandbox-api-token)
- [Delete the API token.](/unified/managing-sandbox-api-token)
- [Modify the table and its columns.](/unified/using-tables)
- Go to the [cloud service API Key](/unified/about-internet-saas-api-key) or [OAuth 2.0 Authorization Servers](/unified/about-oauth-2-0-authorization-servers) tab.
![A screenshot of the Sandbox API Token page](/downloads/zia/authentication-administration/api-key-management/about-sandbox-api-token/sandbox-api-token.png)