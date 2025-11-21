# Configuring Chrome Enterprise Browser Connector Settings
Source: https://help.zscaler.com/zpa/configuring-chrome-enterprise-browser-connector-settings
PDF: https://help.zscaler.com/pdf/com/en/1526401.pdf

Within the ZPA Admin Portal, you can configure Chrome Enterprise Browser Connector settings to allow ZPA to create access policies to verify if a user is accessing private applications via the Chrome Enterprise browser.
If you send a cross-origin or same-origin AJAX request from the Chrome Enterprise browser, the Javascript code should include `withCredentials = true;`. Zscaler recommends refreshing the browser every 30 minutes to refresh the posture. Contact Zscaler Support to enable the CORS feature.
- [Example](#example)
[]
`const xhr = new XMLHttpRequest();
xhr.open("GET", "http://example.com/", true);
xhr.withCredentials = true;
xhr.send(null); `
To configure the settings:
- In the ZPA Admin Portal, go to **Configuration & Control** > **Chrome Enterprise Browser **> **Settings**.
- Under **Chrome Enterprise Browser - Connector Configuration**, copy the following information to set up your Chrome Enterprise device trust connector for Zscaler in the Google Admin Console:
- **URL Patterns to Allow**: Copy your organization's URL pattern.
-
**Service Accounts**: Copy your Chrome Enterprise service account.
- [Adding a Connector in the Google Admin Console](#Connector)
-
Under **Organization Information**, enter the Google Workspace domains to configure policies for. If you have more than one Google Workspace Domain, add a comma (`,`) in between them. For example, `example.com, acme.com`.
[See image.](#Settings)
- Click **Save**.
After saving your settings, configure an access policy with **Chrome Enterprise Browser** as a criteria. To learn more, see [Configuring Access Policies](/zpa/configuring-access-policies).
[See image.](#accesspolicy)
[]
- In the Google Admin console, go to **Devices** > **Chrome** > **Connectors**.
- In the **Connectors** window:
- Click **New Provider Configuration**.
-
Locate** Zscaler**, and click **Set Up**.
[See image.](#EnterpriseSetUpProvider)
-
In the **Zscaler configuration** drawer:
- **Configuration name**: Enter a name for the Zscaler connector.
- **URL patterns to allow, one per line**: Enter the URL pattern that was copied from the ZPA Admin Portal.
- **Service accounts, one per line**: Enter the service account that was copied from the ZPA Admin Portal.
[See image.](#EnterpriseZscalerConfiguration)
- Click **Add Configuration** to save the configuration settings.
- Go to **Devices** > **Chrome** > **Connectors**.
- In the **Connectors** window:
- Select your child organizational unit.
-
Select the Zscaler configuration that you created as the **Device trust connectors**.
[See image.](#Connectors)
- Click **Save**.
To learn more, refer to the [Chrome Enterprise documentation](https://support.google.com/chrome/a/answer/13570263?hl=en).
[]
![Chrome Enterprise Browser as Criteria](/downloads/zpa/browser-access/configuring-chrome-enterprise-browser-connector-settings/ZPA-AccessPolicy-ChromeEnterpriseBrowser-1_0.png)
[]
![Chrome Enterprise Browser Settings](/downloads/zpa/browser-access/configuring-chrome-enterprise-browser-connector-settings/ZPA-ChromeEnterpriseBrowserSettings-2_0.png)
[]
![Set up a provider](/downloads/zpa/browser-access/configuring-chrome-enterprise-browser-connector-settings/ChromeEnterprise-Zscaler.png)
[]
![Add Zscaler Configuration](/downloads/zpa/browser-access/configuring-chrome-enterprise-browser-connector-settings/ChromeEnterprise-Zscaler-SETUP_0.png)
[]
![Adding a Connector](/downloads/zpa/browser-access/configuring-chrome-enterprise-browser-connector-settings/ChromeEnterprise-Zscaler-Connectors.png)