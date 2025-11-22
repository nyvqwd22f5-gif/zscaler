# Managing ZDX API Keys
Source: https://help.zscaler.com/zdx/managing-zdx-api-keys
PDF: https://help.zscaler.com/pdf/com/en/1403316.pdf

After your API subscription is enabled, the ZDX API Key Management page is accessible to an admin role. From there, the admin can provision and display available API keys.
If you need to obtain API keys or secrets to access [Zscaler OneAPI](/oneapi) endpoints, see [About API Clients](/zidentity/about-api-clients) in ZIdentity.
The API Key Management page allows you to perform the following actions:
- [Create a new API key.](#CreateAPIKey)
- [View an API key.](#ViewAPIKey)
- [Edit the API key.](#EditAPIKey)
- [Delete the API key.](#DeleteAPIKey)
To learn more, see [About API Key Management](/zdx/about-api-key-management).
[]
- Go to **Administration > Authentication > API Key Management**.
- Click the **View** icon for a specific API key to open the **API Key** window.
- You can:
- Click **Copy** to copy the API Key ID.
- Click **Copy** to copy the API Key Secret.
- Click **Download** to download a JSON file of the API key.
![View the API Key window to copy API Key information or download a JSON file.](/downloads/zdx/administration/api-key-management/managing-zdx-api-keys/zdx-view-api-key.png)
[]
- Go to **Administration > Authentication > API Key Management**.
- Click **Create New API Key**.
-
Enter the required information:
- **Name**: Enter the API key name.
- **Select Role**: Select an admin role to be assigned the API key.
![Create a new API Key](/downloads/zdx/administration/api-key-management/managing-zdx-api-keys/zdx-create-new-api-key.png)
- Click **Create Key** to confirm, and the **API Key** window appears.
-
Click **Copy** to copy the API Key ID or Key Secret, or click **Download** to download the JSON file. You need both the API Key ID and Key Secret for [authentication](/zdx/getting-started-zdx-api/#authenticate-api).
![Copy API Key ID or Secret or Download API Key](/downloads/zdx/administration/api-key-management/managing-zdx-api-keys/zdx-view-api-key.png)
- Close the window.
[]
- Go to **Administration > Authentication > API Key Management**.
- Click the **Edit** icon for a specific API key to open the **Edit API Key** window.
- Edit the **Name** or choose a new role from the **Select Role** drop-down menu.
- Click **Save** to confirm the changes.
![Edit the API key name or role.](/downloads/zdx/administration/api-key-management/managing-zdx-api-keys/zdx-edit-api-key.png)
[]The **Delete** action allows you to delete the specified API key.
To delete a specific API key:
- Go to **Administration > Authentication > API Key Management**.
- Click the **Delete** icon for a specific API key to open the **Delete API Key** window.
- Click **Delete** to confirm the deletion.
![Delete API Key](/downloads/zdx/administration/api-key-management/managing-zdx-api-keys/zdx-delete-api-key.png)