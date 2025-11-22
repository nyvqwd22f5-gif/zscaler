# About API Key Management
Source: https://help.zscaler.com/unified/about-api-key-management-private-applications
PDF: https://help.zscaler.com/pdf/com/en/1491536.pdf

An API key is required in order to access the publicly available set of Private Applications APIs. An API key consists of a client ID and a client secret. Both are required for authentication prior to accessing the publicly available set of Private Applications APIs.
Generating an API key only occurs in the Admin Portal from the API Keys page. Client IDs are always accessible from the page. Client secrets are only displayed when the key is first created, and they are not available in the saved configuration.
API keys provide the following benefits and enable you to:
- Authenticate and access the Private Applications APIs.
- Generate the Client ID and Client Secret used to access the Private Applications APIs.
About the API Keys Page
On the API Keys page (Administration > API Configuration > Legacy API > Private Access API), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/unified/using-tables).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the API Keys page to reflect the most current information.
- Click the **Menu **icon (![Menu icon](/downloads/zpa/api-key-management/about-api-key-management/zpa-menu-icon.png)
). Within the menu, you can:
- Copy your customer ID. The customer ID is needed for making API calls.
-
Copy your Microtenant ID. The Microtenant ID is the unique identifier of the Microtenant, and is needed for making API calls if you're within a Microtenant.
The **Copy Microtenant ID** action is only visible if you are within a Microtenant. If you are within a Microtenant, then you must pass the `microtenantId` when making an API call.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/unified/using-tables).
- [Add an API key](/unified/adding-api-keys).
- View a list of API keys. For each key, you can see the following:
- **Name**: The name of the API key.
- **Client ID**: The ID for the key. It is needed to access the Private Applications API Portal.
- **Status**: Indicates whether the key is enabled or disabled.
- **Session Validity Interval (In Seconds)**: The amount of time in seconds that the key remains active before expiring.
- **Creation Date**: The date and time the API key was created.
- **Role**: The predefined role or a custom role of the API key (e.g., full access, policy-only access, application-only access). Roles for API keys enforce granular role-based access control (RBAC) on all publicly available API operations for Private Applications. For each API key, you can select the **API Full Access** predefined role. This predefined role provides full access to the API. To learn more, see [Understanding Role-Based Access Control for API](/unified/understanding-role-based-access-control-api), [About API Clients](/unified/about-api-clients), and [Adding an API Client](/unified/adding-api-client).
- Copy a client ID.
- [Edit an API key.](/unified/editing-api-keys)
-
Unlock a locked API client.
Locking occurs automatically after three unsuccessful attempts at API access and persists for 30 minutes.
- Delete a key.
- [Modify the columns displayed in the table.](/unified/using-tables)
- Display more rows or a different page of the table.
![Viewing and Managing API Keys ](/downloads/zpa/api-key-management/about-api-key-management/experience-center-private-applications-api-keys.png)