# Adding API Keys
Source: https://help.zscaler.com/zpa/adding-api-keys
PDF: https://help.zscaler.com/pdf/com/en/1484751.pdf

An [API key](/zpa/about-api-keys) is required for authenticating with the [ZPA API ](/zpa/about-zpa-api)in order to make API calls.
If you need to obtain API keys or secrets to access [Zscaler OneAPI ](/oneapi)endpoints, see [API Client Authentication](/zslogin/integration/oneapi-authentication) in ZIdentity.
To add a new API key:
-
Go to **Configuration & Control **>** Public API** > **API Keys**.
If you are subscribed to ZIdentity and have it enabled for your tenant, API keys created in the ZIdentity Admin Portal appear on the API Keys page in the ZPA Admin Portal and are read-only. To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
-
Click **Add**.
The **Add API Key** window appears.
- In the **Add API Key** window:
- **Name**: Enter a name for the key.
- **Status**: Enable the key. If **Disabled**, the key will be unavailable to use. By default, this is enabled.
- **Session Validity Interval (In Seconds)**: The amount of time the key is available to use. The maximum amount of time is 3,600 seconds.
- **Role**: The predefined role or a custom role of the API key (e.g., full access, policy-only access, application-only access). Roles for API keys enforce granular role-based access control (RBAC) on all publicly available ZPA API operations. For each API key, you can select the **API Full Access** predefined role. This predefined role provides full access to the ZPA API. To learn more, see [Understanding Role-Based Access Control for ZPA API](/zpa/understanding-role-based-access-control-zpa-api), [About API Clients](/zidentity/about-api-clients), and [Adding an API Client](/zidentity/adding-api-client).
![Viewing the Add API Key window](/downloads/zpa/api-key-management/adding-api-keys/zpa-add-api-key-window.png)
- Click **Save**. The client secret for the key is displayed.
-
Copy the client secret to your clipboard. You will need it for authentication.
The client secret is only available to copy when creating an API key. It is not available to access in the ZPA Admin Portal after you close the window, so store it in a secure location.
- Close the window.