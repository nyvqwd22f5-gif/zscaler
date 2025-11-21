# Managing Cloud Service API Key
Source: https://help.zscaler.com/zia/managing-cloud-service-api-key
PDF: https://help.zscaler.com/pdf/com/en/1400506.pdf

After your API subscription is enabled, your organization's cloud service API key is initially provisioned by Zscaler, enabled, and displayed within the Cloud Service API Key page along with the base URL. An organization can only have one API key for the cloud service API. To learn more, see [Getting Started](/zia/api-getting-started).
- If you need to obtain API keys or secrets to access [Zscaler OneAPI](/oneapi) endpoints, see [API Client Authentication](/zidentity/integration/oneapi-authentication) in ZIdentity.
- Admins have view access to the Cloud Service API Key page information within the [Zscaler Cloud Connector Portal](/cloud-branch-connector/about-cloud-connector-portal).
From this page, you can:
- [Add a new API key](#AddKey)
- [Edit the API key](#EditKey)
- [Regenerate the API key](#RegenerateKey)
- [Delete the API key](#DeleteKey)
Your cloud service API key can be disabled by Zscaler or your service provider. The key might be disabled if your organization exceeds the threshold number of API calls allowed or the code developed for your organization violates Zscaler's terms and conditions. If this occurs, the ability to add, regenerate, or delete the key is removed and a **Disabled** status appears. You must contact Zscaler Support or your service provider to re-enable the key.
[See image.](#APIKeyDisabled)
If your [API subscription](/zia/how-do-i-view-subscriptions) expires you still have access to the Cloud Service API Key page, but you cannot make any modifications (i.e., you lose access to the POST and PUT actions [within the API](/zia/about-api)). Also, your existing API key is still valid but disabled. If this occurs, contact Zscaler Support. The API key is re-enabled after your subscription is renewed.
[]Your organization can only have one API key. You must delete the existing key before adding a new one.
To add a new cloud service API key:
- Go to **Administration** > **Cloud Service API Security** > **Cloud Service API Key**.
- On the Cloud Service API Key tab, make sure that you have deleted the existing key. After the key is removed, the **Add Cloud Service API Key** option becomes available.
- Click **Add Cloud Service API Key**.
- You can immediately start using the new **API key** displayed on the tab.
[]This action cannot be undone.
To edit the cloud service API key:
- Go to **Administration** > **Cloud Service API Security** > **Cloud Service API Key**.
-
On the **Cloud Service API Key** tab, click the **Edit** icon.
The **Edit Cloud Service API Key** window appears.
-
In the **Edit Cloud Service API Key** window, enter the **New API** Key. The new key must meet the following requirements:
- The new key must be alphanumeric (i.e., A-Z, a-z, 0-9) and exactly 12 characters in length.
- The new key cannot be the same as the current API Key.
[See image.](#edit-cloud-service-api-key)
-
Click **Confirm**.
After confirmation, the old API key is immediately invalidated.
[]This action cannot be undone.
To regenerate the cloud service API key:
- Go to **Administration** > **Cloud Service API Security** > **Cloud Service API Key**.
- On the **Cloud Service API Key** tab, click the **Regenerate** icon.
-
In the confirmation window that appears, click **Ok**.
After confirmation, a randomized key string is immediately generated and the old string is invalidated.
[]This action cannot be undone.
To delete the cloud service API key:
- Go to **Administration** > **Cloud Service API Security** > **Cloud Service API Key**.
- On the **Cloud Service API Key** tab, click the **Delete** icon.
-
In the confirmation window that appears, click **Ok**.
After confirmation, the key is immediately removed and invalidated.
[]![A screenshot of the API key in the disabled status](/downloads/zia/authentication-administration/api-key-management/managing-organization-api-key/APIKeyMgmt_Disabled_0.png)
[]![A screenshot of the Edit API Key window](/downloads/zia/authentication-administration/api-key-management/managing-organization-api-key/APIKeyMgmt_Edit.png)