# Managing Sandbox API Token
Source: https://help.zscaler.com/unified/managing-sandbox-api-token
PDF: https://help.zscaler.com/pdf/com/en/1494856.pdf

After your Sandbox subscription is enabled, your organization's sandbox API token is initially provisioned by Zscaler, enabled, and displayed within the Sandbox API Token page along with the base URL. An organization can only have one API token for the Sandbox Submission API.
From this page, you can:
- [Add a new API token](#AddToken)
- [Regenerate the API token](#RegenerateToken)
- [Delete the API token](#DeleteToken)
Your sandbox API token can be disabled by Zscaler or your service provider. The token might be disabled if your organization exceeds the threshold number of API calls allowed or the code developed for your organization violates Zscaler's terms and conditions. If this occurs, the ability to add, regenerate, or delete the token is removed and a Disabled status appears. You must contact Zscaler Support or your service provider to re-enable the token.
If your Sandbox subscription expires, you still have access to the Sandbox API Token page, but you cannot make any modifications (i.e., you lose access to the POST and PUT actions within the API). Also, your existing API token is still valid but disabled. If this occurs, contact Zscaler Support. The API token is re-enabled after your subscription is renewed.
Your organization can only have one API token. You must delete the existing token before you can add a new one.
[]To add a new Sandbox API token:
- Go to **Administration** > **API Configuration** > **Legacy API** > **Internet & SaaS API** > **Sandbox API Token**.
- On the **Sandbox API Token** tab, make sure that you have deleted the existing token. After the token is removed, the **Add Sandbox API Token** option becomes available.
-
Click **Add Sandbox API Token**.
You can immediately start using the new API token displayed on the tab. The token information is hidden by default, but you can view it by clicking the **Eye** icon.
![A screenshot of the masked Sandbox API token](/downloads/zia/authentication-administration/api-key-management/managing-sandbox-api-token/view-api-token.png)
[]This action cannot be undone.
To regenerate the Sandbox API token:
- Go to **Administration** > **API Configuration** > **Legacy API** > **Internet & SaaS API** > **Sandbox API Token**.
- On the **Sandbox API Token** tab, click the **Regenerate** icon.
-
In the confirmation window that appears, click **Ok**.
After confirmation, a randomized token string is immediately generated and the old string is invalidated.
[]This action cannot be undone.
To delete the Sandbox API token:
- Go to **Administration** > **API Configuration** > **Legacy API** > **Internet & SaaS API** > **Sandbox API Token**.
- On the **Sandbox API Token** tab, click the **Delete** icon.
-
In the confirmation window that appears, click **Ok**.
After confirmation, the token is immediately removed and invalidated.