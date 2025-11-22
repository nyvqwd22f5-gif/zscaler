# Managing Organization API Keys
Source: https://help.zscaler.com/unified/managing-organization-api-keys
PDF: https://help.zscaler.com/pdf/com/en/1516331.pdf

After your API subscription is enabled, your organization's cloud service API key is initially provisioned by Zscaler, enabled, and displayed on the API Key Management page along with the base URL.
From this page, you can perform the following tasks:
- [Add a New API Key](#AddNewKey)
- [Edit the API Key](#EditNewKey)
- [Regenerate the API Key](#RegenerateKey)
- [Delete the API Key](#DeleteKey)
Your API key can be disabled by Zscaler or your service provider. The key can be disabled if your organization exceeds the threshold number of API calls allowed, or the code developed for your organization violatesZscaler's terms and conditions. If this occurs, the ability to add, regenerate, or delete the key is removed and a **Disabled** status appears.
You must contact Zscaler Support or your service provider to re-enable the key.
If your API subscription expires, you will still have access to the API Key Management page, but you will not be able to make any modifications. Also, your existing API key will still be valid but disabled. It will be re-enabled after your subscription is renewed. If this occurs, contact Zscaler Support.
[]Your organization can only have one API key. You must delete the existing key before you can add a new one.
To add a new API key:
- Go to **Administration** >** API Configuration > Legacy API** > **Cloud & Branch Connector API**.
- Delete the existing key. After the key is removed, the **Add Cloud Service API Key** option becomes available.
- Click **Add Cloud Service API Key**.
The new API key is immediately valid and displayed in the tab.
[]After an API key is edited, the action cannot be undone. You cannot edit the Cloud Sandbox Submission API key, but you can delete and re-add a key or regenerate it.
To edit the Cloud Service API key:
- Go to **Administration** >** API Configuration** > **Legacy API** > **Cloud & Branch Connector API.**
- Click the **Edit** icon.
The **Edit Cloud Service API Key** window appears.
- In the **Edit Cloud Service API Key** window, enter the **New API Key**. The new key must meet the following requirements:
- The new key must be alphanumeric (A-Z, a-z, 0-9) and exactly 12 characters in length.
- The new key cannot be the same as the **Current API Key**.
![Edit Cloud Service API Key in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/administration/api-key-management/managing-organization-api-keys/Edit%20Cloud%20Service%20API%20Key.jpg)
- Click **Confirm**.
After confirmation, the old API key is immediately invalidated.
[]After an API key is regenerated, the action cannot be undone.
To regenerate the Cloud Service API key:
- Go to **Administration** > **API Configuration > Legacy API > Cloud & Branch Connector API.**
- Click the **Regenerate **icon.
- In the confirmation window that appears, click **OK**.
After confirmation, a random key string is immediately generated and the old string is invalidated.
[]After an API key is deleted, the action cannot be undone.
To delete the API key:
- Go to **Administration** > **API Configuration** > **Legacy API** > **Cloud & Branch Connector API**.
- Click the **Delete** icon.
- In the confirmation window that appears, click **OK**.
After confirmation, the key is immediately removed and invalidated.