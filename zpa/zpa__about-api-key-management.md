# About API Key Management
Source: https://help.zscaler.com/zpa/about-api-key-management
PDF: https://help.zscaler.com/pdf/com/en/1484746.pdf

An API key is required in order to access the publicly available set of [ZPA APIs](/zpa/about-zpa-api). An API key consists of a client ID and a client secret. Both are required for authentication prior to accessing the publicly available set of ZPA APIs.
Generating an API key only occurs in the ZPA Admin Portal from the API Keys page. Client IDs are always accessible from the page. Client secrets are only displayed when the key is first created, and they are not available in the saved configuration.
If you need to obtain API keys or secrets to access [Zscaler OneAPI ](/oneapi)endpoints, see [API Client Authentication](/zslogin/integration/oneapi-authentication) in ZIdentity.
API keys provide the following benefits and enable you to:
- Authenticate and access the ZPA APIs.
- Generate the Client ID and Client Secret used to access the ZPA APIs.
About the API Keys Page
On the API Keys page (Configuration & Control > Public API > API Keys), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the API Keys page to reflect the most current information.
- Click the **Menu **icon (![Menu icon](/downloads/zpa/api-key-management/about-api-key-management/zpa-menu-icon.png)
). Within the menu, you can:
- Copy your customer ID. The customer ID is needed for making API calls.
-
Copy your Microtenant ID. The Microtenant ID is the unique identifier of the Microtenant, and is needed for making API calls if you're within a Microtenant.
The **Copy Microtenant ID** action is only visible if you are within a Microtenant. If you are within a Microtenant, then you must pass the `microtenantId` when making an API call. To learn more, see [Getting Started](/zpa/getting-started-zpa-api) and [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add an API key](/zpa/adding-api-keys).
-
View a list of API keys. For each key, you can see:
- **Name**: The name of the API key.
- **Client ID**: The ID for the key. It is needed to access the ZPA API Portal.
- **Status**: Indicates whether the key is enabled or disabled.
- **Session Validity Interval (In Seconds)**: The amount of time in seconds that the key remains active before expiring.
- **Creation Date**: The date and time the API key was created.
- **Role**: The predefined role or a custom role of the API key (e.g., full access, policy-only access, application-only access). Roles for API keys enforce granular role-based access control (RBAC) on all publicly available ZPA API operations. For each API key, you can select the **API Full Access** predefined role. This predefined role provides full access to the ZPA API. To learn more, see [Understanding Role-Based Access Control for ZPA API](/zpa/understanding-role-based-access-control-zpa-api), [About API Clients](/zidentity/about-api-clients), and [Adding an API Client](/zidentity/adding-api-client).
If you are subscribed to ZIdentity and have it enabled for your tenant, API keys created in the ZIdentity Admin Portal appear on the API Keys page in the ZPA Admin Portal and are read-only. To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
- Copy a client ID.
- [Edit an API key](/zpa/editing-api-key).
-
Delete an API key.
If an API key is configured using Zscaler Deception, then the edit and delete options are unavailable.
-
Unlock a locked API client.
Locking occurs automatically after three unsuccessful attempts at API access and persists for 30 minutes.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
![Viewing the API Keys page](/downloads/zpa/api-key-management/about-api-key-management/zpa-api-keys-page-no-swagger.png)