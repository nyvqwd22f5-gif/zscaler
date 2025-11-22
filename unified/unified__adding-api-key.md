# Adding an API Key
Source: https://help.zscaler.com/unified/adding-api-key
PDF: https://help.zscaler.com/pdf/com/en/1491561.pdf

An [API key](/unified/about-api-key-management) is required for authenticating with Zscaler back-end servers to make API calls.
Using an API key is available for Zscaler Client Connector version 3.6 and later for Windows.
If you need to obtain API keys or secrets to access [Zscaler OneAPI ](/oneapi)endpoints, see [About API Clients](/unified/about-api-clients).
To add a new API key:
- In the Admin Portal, go to **Administration** > **API Configuration > Legacy API > Client Connector API**.
- Click **Add API Key**. The **Add API Key** window appears.
-
In the **Add API Key** window:
- **Name**: Enter a name for the API key. The name must be alphanumeric, cannot contain spaces, and has a maximum of 50 characters.
- **Status**: Make sure **Enabled** is selected. If **Disabled**, the key will be unavailable to use. By default, this is enabled.
- **Role**: Select **Read** or **Write** access for the key.
- **Session Validity Interval (In Seconds)**: Enter the amount of time the key is available to use. Enter a range between 30 and 999,999,999 seconds.
![Add an API key for Zscaler Client Connector](/downloads/client-connector/administration/api-key-management/adding-api-key/ZscalerClientConnector-AddAPIKey.png)
- Click **Save**. The client secret for the key is displayed.
-
Copy the client secret to your clipboard. You need it for authentication.
![Copy the client secret for the API key](/downloads/client-connector/administration/api-key-management/adding-api-key/ZscalerClientConnector-AddAPIKey-Generated.png)
The client secret is only available to copy when creating an API key. It is not available to access in the Admin Portal after you close the window, so store it in a secure location.
- When finished, click **Cancel **to close the window.