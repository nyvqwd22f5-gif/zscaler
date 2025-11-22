# Managing Internet & SaaS API Key
Source: https://help.zscaler.com/unified/managing-internet-saas-api-key
PDF: https://help.zscaler.com/pdf/com/en/1494846.pdf

After your API subscription is enabled, your organization's Internet & SaaS API key is initially provisioned by Zscaler, enabled, and displayed within the Cloud Service API Key page along with the base URL. An organization can only have one API key for the Internet & SaaS API.
From this page, you can:
- [Add a new API key](#AddKey)
- [Edit the API key](#EditKey)
- [Regenerate the API key](#RegenerateKey)
- [Delete the API key](#DeleteKey)
Your Internet & SaaS API key can be disabled by Zscaler or your service provider. The key might be disabled if your organization exceeds the threshold number of API calls allowed or the code developed for your organization violates Zscaler's terms and conditions. If this occurs, the ability to add, regenerate, or delete the key is removed and a **Disabled** status appears. You must contact Zscaler Support or your service provider to re-enable the key.
[See image.](#APIKeyDisabled)
If your [API subscription](/unified/viewing-subscriptions) expires you still have access to the Cloud Service API Key page, but you cannot make any modifications (i.e., you lose access to the POST and PUT actions within the API). Also, your existing API key is still valid but disabled. If this occurs, contact Zscaler Support. The API key is re-enabled after your subscription is renewed.
[]Your organization can only have one API key. You must delete the existing key before adding a new one.
To add a new Internet & SaaS API key:
- Go to **Administration** > **API Configuration** > **Legacy API** > **Internet & SaaS API** > **Cloud Service API Key**.
- On the **Cloud Service API** **Key** tab, make sure that you have deleted the existing key. After the key is removed, the **Add API Key** option becomes available.
- Click **Add API Key**.
- You can immediately start using the new **API key** displayed on the tab.
[]This action cannot be undone.
To edit the Internet & SaaS API key:
- Go to **Administration** > **API Configuration** > **Legacy API** > **Internet & SaaS API** > **Cloud Service API Key**.
-
On the **Cloud Service API Key** tab, click the **Edit** icon.
The **Edit API Key** window appears.
- In the **Edit API Key** window, enter the **New API** Key. The new key must meet the following requirements:
- The new key must be alphanumeric (A-Z, a-z, 0-9) and exactly 12 characters in length.
- The new key cannot be the same as the current API Key.
-
Click **Confirm**.
After confirmation, the old API key is immediately invalidated.
[]This action cannot be undone.
To regenerate the Internet & SaaS API key:
- Go to **Administration** > **API Configuration** > **Legacy API** > **Internet & SaaS API** > **Cloud Service API Key**.
- On the **Cloud Service API Key** tab, click the **Regenerate** icon.
-
In the confirmation window that appears, click **Ok**.
After confirmation, a randomized key string is immediately generated and the old string is invalidated.
[]This action cannot be undone.
To delete the Internet & SaaS API key:
- Go to **Administration** > **API Configuration** > **Legacy API** > **Internet & SaaS API** > **Cloud Service API Key**.
- On the **Cloud Service API Key Key** tab, click the **Delete** icon.
-
In the confirmation window that appears, click **Ok**.
After confirmation, the key is immediately removed and invalidated.
[]![A screenshot of the API key in the disabled status](/downloads/zia/authentication-administration/api-key-management/managing-organization-api-key/APIKeyMgmt_Disabled_0.png)