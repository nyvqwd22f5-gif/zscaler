# Creating API Keys
Source: https://help.zscaler.com/zpc/creating-api-keys
PDF: https://help.zscaler.com/pdf/com/en/1453161.pdf

An [API key](/zpc/about-api-key-management) is required for authenticating with the Zscaler Posture Control (ZPC) API in order to make API calls. You can create a maximum of 100 API keys.
To add a new API key:
- Go to **Administration **> **Authentication & Authorization** > **API Keys**.
- Click **Create API Key**.
The **Create API Key** window appears.
- In the **Create API Key** window:
- **Name**: Enter a name for the key. The name is displayed in the audit logs as the entity performing the API actions. Symbols like ampersands (&) and asterisks (*) are not supported.
- **Role Groups**: Select the group and role from the drop-down menu for role-based access.
Zscaler recommends creating an API key with the least permissive role.
- **Revocation Date**: Select a date from the drop-down menu that the API key is revoked. You can set the Revocation date to Never, **7 Days**, **15 Days**, **1 Month**, or **3 Months**. Revoked API keys no longer allow access to authenticate to the ZPC API, but remain in the table. By default, this is set to **7 Days**.
[See image.](#createAPIKey)
[]![Create API Key window in the ZPC Admin Portal](/downloads/zpc/authentication-authorization/api-key-management/creating-api-keys/zpc-creating-api-keys-window.png)
- Click **Save**. The API key is displayed.
- Click the **View** icon to view the API key, click the **Copy **icon to copy the API key to your Clipboard, or click the **Download **icon to download the API key as a CSV file. You need it for authentication.
The API key is only available when creating an API key. It is not available to access in the ZPC Admin Portal after you close the window, so store it in a secure location.
- Close the window.