# Managing Workflow Automation API Keys
Source: https://help.zscaler.com/workflow-automation/managing-workflow-automation-api-keys
PDF: https://help.zscaler.com/pdf/com/en/1452006.pdf

If you have a subscription to Workflow Automation, API Management is automatically accessible to an admin role. An admin can create and display the API key required for authenticating with the Workflow Automation API to make API calls.
The API Keys page allows you to perform the following actions:
- [Create a New API Key](#create-api-key)
- [Disable an API Key](#disable-api-key)
- [Regenerate an API Key](#regenerate-api-key)
- [Delete an API Key](#delete-api-key)
To learn more, see [About API Keys](/zia/about-api-keys).
[]The **Create API Key** action allows you to create API keys for an admin. An API key must be created for authentication to make API calls.
To create a new API key:
- Go to **Setup** > **API Management**. The **API Keys** page appears, listing the API keys.
- Click **Add More**. The **Create API Key** window appears.
- In the **Create API Key** window:
- **Name**: Enter the name for the API key.
- **Expiration Time**: (Optional) Enable to set an expiration time for the API key.
- **Lifetime (days)**: Enter the number of days that you want the key to be valid.
If the **Expiration Time** option is disabled, the API key has no expiration time.
[See image.](#create-api-key-image)
- Click **Submit**. The **API Key** window appears.
- In the **API Key** window, click the **Copy** icon to copy the **Key Secret **and the **Key ID**. You need both for authentication.
The key secret is only available to copy when creating an API key. Copy and save the key secret for authentication.
[See image.](#key-secret-window)
- Click **Done** to close the window.
[]When created, the API key is enabled by default. You can use the toggle button corresponding to a specific API key to disable that key.
To disable an API key:
- Go to **Setup** > **API Management**. The **API Keys** page appears, listing the API keys.
- On the **API Keys** page, click the blue toggle under the **Action** column to disable a specific API key.
[See image.](#toggle-button)
The API key is disabled and cannot be used for authentication. You can use the same action to enable the API key when needed.
[]You can generate a new key secret for the same admin and the key ID.
To regenerate an API key:
- Go to **Setup** > **API Management**. The **API Keys** page appears, listing the API keys.
- On the **API Keys** page, click the **Regenerate** icon corresponding to a specific API key.
- Click **Yes** in the pop-up window that appears.
[See image.](#regenerate-icon)
A new key secret for the API key is generated.
[]The **Delete** action allows you to delete the specified API key.
To delete an API key:
- Go to **Setup** > **API Management**. The **API Keys** page appears, listing the API keys.
- On the **API Keys** page, click the **Delete** icon for a specific API key.
- Click **Yes **in the pop-up window that appears.
[See image.](#delete-icon)
The API key is deleted permanently.
![Create API Key Window](/downloads/workflow-automation/api-management/managing-workflow-automation-api-keys/WA-Create-API-Key-Window.png)
[]
[]![API Key Window ](/downloads/workflow-automation/api-management/managing-workflow-automation-api-keys/WA-API-Key-Window.png)
[]![API Keys Page - Toggle Button](/downloads/workflow-automation/api-management/managing-workflow-automation-api-keys/WA-API-Keys-Page-Disable-Enable.png)
[]![API Keys Page - Regenerate Icon](/downloads/workflow-automation/api-management/managing-workflow-automation-api-keys/WA-API-Keys-Page-Regenerate.png)
[]![API Keys Page - Delete Icon](/downloads/workflow-automation/api-management/managing-workflow-automation-api-keys/WA-API-Keys-Page-Delete-Key.png)