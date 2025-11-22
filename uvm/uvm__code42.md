# Code42
Source: https://help.zscaler.com/uvm/code42
PDF: https://help.zscaler.com/pdf/com/en/1527681.pdf

![The Code42 tile](/downloads/uvm/configure/sources/code42/d69d18ff-4fa4-415a-904d-3530aaf5132d.png)
Code42 is a cloud-native data security platform that provides real-time visibility, detection, and response capabilities to help organizations protect sensitive data from insider threats and data leaks.
The Code42 connector retrieves alerts from configured alert rules, including details on alert destinations and alert actors.
Required Parameters
The source Authentication configuration requires the Client ID and Client Secret parameters. You must be assigned the Customer Cloud Admin role. To learn more, refer to the [Mimecast documentation](https://mimecastsupport.zendesk.com/hc/en-us/articles/42665971063059-API-clients#h_01HTZPCPPSPC94S81VPJS71YHM).
To create an API client:
- Log in to the Code42 console.
- Go to **Administration** > **Integrations** > **API Clients**.
- Click **Create new API client**. In the **Create new API client** window:
- **Client name**: Enter a name.
- **Description (optional)**: Enter a description.
- **API Permissions**: In the **Alerts** row, check the **Read** checkbox.![The Create new API client window in the Code42 console](/downloads/uvm/configure/sources/code42/b04d4d94-648d-40b6-8ebf-ac191e62aa41.png)
-
Click** Save** and copy the Client ID and Client Secret
The client ID and Client Secret will not be available after closing the window.
- Click** Done**.
In the source setup** **Retrieval section, optionally set the following:
- Days To Fetch: Specify a timeframe in days to retrieve CVEs that were first detected within that period. For example, entering `4` retrieves CVEs that were first seen in the last 4 days.