# Adding API Keys
Source: https://help.zscaler.com/unified/adding-api-keys
PDF: https://help.zscaler.com/pdf/com/en/1491541.pdf

An [API key](/unified/about-api-key-management-0) is required for authenticating with the Private Applications API in order to make API calls.
To add a new API key:
- Go to **Administration** > **API Configuration** > **Legacy API** > **Private Access API**.
- Click **Add API Key**.
The **Add API Key** window appears.
-
In the **Add API Key** window:
- **Name**: Enter a name for the key.
- **Status**: Enable the key. If **Disabled**, the key will be unavailable to use. By default, this is enabled.
- **Session Validity Interval (In Seconds)**: The amount of time the key is available to use. The maximum amount of time is 3600 seconds.
- **Role**: The predefined role or a custom role of the API key (e.g., full access, policy-only access, application-only access). Roles for API keys enforce granular role-based access control (RBAC) on all publicly available API operations for Private Applications. For each API key, you can select the **API Full Access** predefined role. This predefined role provides full access to the API. To learn more, see [Understanding Role-Based Access Control for API](/unified/understanding-role-based-access-control-api), [About API Clients](/unified/about-api-clients), and [Adding an API Client](/unified/adding-api-client).
![Adding an API Key](/downloads/unified/administration/private-applications/api-configuration/adding-api-keys/experience-center-add-api-key.png)
- Click **Save**. The client secret for the key displays.
- Copy the client secret to your clipboard. You will need it for authentication.
The client secret is only available to copy when creating an API key. It is not available to access in the Admin Portal once you close the window, so store it in a secure location.
- Close the window.