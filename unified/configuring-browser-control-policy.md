# Configuring the Browser Control Policy
Source: https://help.zscaler.com/zia/configuring-browser-control-policy
PDF: https://help.zscaler.com/pdf/com/en/1398716.pdf

[Watch a video about Browser Control](https://fast.wistia.net/embed/iframe/hwz5y9619y)
You can define a Browser Control policy to warn users from going to the internet when they are using outdated or vulnerable browsers, plugins, and applications. The Zscaler service examines browser versions and patches (including beta browsers), internet applications (e.g., Adobe Flash, Sun Java, Apple QuickTime), and media download applications (e.g., Windows Media Player).
You can also reduce the security risk of your organization by blocking the use of browsers or specific browser versions that are older or that have known vulnerabilities. The ZIA Admin Portal displays the latest 12 versions for most browsers.
The Zscaler service has Secure Browsing reports that you can run to track the use of vulnerable browsers, plugins, and applications, and then modify your Browser Control policy if needed. To learn more, see [Viewing Secure Browsing Reports](/zia/viewing-secure-browsing-reports).
To see how this policy fits into the overall order of policy enforcement, see [Understanding Policy Enforcement](/zia/understanding-policy-enforcement).
You can also see the [Recommended Browser Control Policy](/zia/recommended-browser-control-policy).
To configure the Browser Control policy:
- Go to** Policy **>** Secure Browsing**.
-
On the **Browser Control** tab:
-
**Enable Checks & User Notification**: Enable to warns users when they are using outdated or vulnerable browsers, plugins, and applications. The following options appear:
- **How Often to Check**: Choose how frequently the service checks browsers and relevant applications. It can check **Daily**, **Monthly**, or **Weekly**.
- **Disable Notification for Browsers**:** **Enable to disable warnings for all browsers.
- **Disable Notification for Plugins**: Choose the plugins to exempt from warnings. You can search for plugins and choose any number of them.
- **Disable Notification for Applications**: Choose the applications to exempt from warnings. You can search for applications and choose any number of them.
This feature is only applicable when you are using browser-based authentication (non-Zscaler Client Connector).
- **Allow All Browsers**: Enable to allow all browsers and their respective versions access to the internet. If disabled, the following browser options appear, and you can block specific browsers and their versions:
- **Microsoft Browsers**
- **Chrome**
- **Firefox**
- **Safari**
- **Opera**
[See image.](#image-browser-control)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![Screenshot of ZIA Secure Browsing Browser Control Policy](/downloads/zia/policies/browser-control/configuring-browser-control-policy/ZIA-Secure-Browsing-Browser-Control.png)