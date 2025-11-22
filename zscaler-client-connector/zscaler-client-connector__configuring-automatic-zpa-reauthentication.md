# Configuring Automatic ZPA Reauthentication
Source: https://help.zscaler.com/zscaler-client-connector/configuring-automatic-zpa-reauthentication
PDF: https://help.zscaler.com/pdf/com/en/1364591.pdf

You can enable Zscaler Client Connector to automatically attempt reauthentication for users with Zscaler Private Access (ZPA). This article describes how to configure automatic ZPA reauthentication.
This feature is only available for Zscaler Client Connector version 3.0 and later for Windows and macOS.
Prior to configuring automatic ZPA reauthentication, you must:
- [Configure your IdP for single sign-on (SSO)](/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides).
- Enable Integrated Windows Authentication (IWA).
Enabling IWA
After you [configure your organization's IdP](/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides), you can enable IWA on the following browsers. Select a browser to learn more.
While IWA works with most browsers, it does not work over some HTTP proxy servers.
- [Mozilla Firefox](#Mozilla)
- [Google Chrome version 8.0 and later](#Google)
- [Safari, after you obtain a Kerberos ticket](#Safari)
- [Microsoft Edge version 77 and later](#Microsoft)
[]Enabling IWA on Mozilla Firefox depends on your OS.
To enable IWA on Mozilla Firefox for Windows:
- Start `about:config`:
- In the URL field, enter `about:config` and press `Enter`.
- Click **Accept the Risk and Continue**.
- Configure `network.negotiate-auth.trusted-uris`:
- In the **Search preference name **field, enter `negotiate`.
- Click the **Edit **icon for `network.negotiate-auth.trusted-uris`.
- Add the SSO domain.
- Press `Enter` or click the checkmark.
[See image.](#Firefox)
- Configure `network.automatic-ntlm-auth.trusted-uris`:
- In the **Search preference name** field, enter `automatic`.
- Click the **Edit **icon for `network.automatic-ntlm-auth.trusted-uris`.
- Add the SSO domain.
- Press `Enter` or click the checkmark.
[See image.](#Firefox2)
To enable IWA on Mozilla Firefox for macOS:
- Start `about:config`:
- In the URL field, enter `about:config` and press `Enter`.
- Click **Accept the Risk and Continue**.
- Configure `network.negotiate-auth.delegation-uris`:
- In the **Search preference name** field, enter `negotiate`.
- Click the **Edit **icon for `network.negotiate-auth.delegation-uris`.
- Add the SSO domain.
- Press `Enter` or click the checkmark.
[See image.](#Firefox3)
- Configure `network.automatic-ntlm-auth.trusted-uris`:
- In the **Search preference name** field, enter `automatic`.
- Click the **Edit **icon for `network.automatic-ntlm-auth.trusted-uris`.
- Add the SSO domain.
- Press `Enter` or click the checkmark.
[See image.](#Firefox4)
- Configure `network.automatic-ntlm-auth.allow-proxies`:
- In the **Search preference name **field, enter `automatic`.
- Click the gray toggle for `network.automatic-ntlm-auth.allow-proxies` to set this value to **true**.
[See image.](#Firefox5)
- Configure `network.negotiate-auth.allow-proxies`
- In the **Search preference name** field, enter `negotiate`.
- Click the gray toggle for `network.negotiate-auth.allow-proxies` to set this value to **true**.
[See image.](#Firefox6)
[]For Windows and macOS, IWA is automatically enabled on Google Chrome and this function is allowlist-driven. The only way to change the policy is through the command prompt (Windows) or terminal window (macOS).
To change the policy in Windows:
- Enter `cmd` into the search field on your taskbar to start the command prompt.
- Configure the allowlist using the following command-line parameter:
`--auth-server-whitelist="https://www.example.com"`.
Use a comma to separate multiple domains.
To change the policy in macOS:
- Start the terminal application.
- Create a Kerberos ticket for the account using the following command: `kinit username@example.com`.
- Replace `username@example.com` with your username and domain. When prompted, enter your password.
- Configure the allowlist using the following command-line parameter:
`$ defaults write com.google.Chrome AuthServerWhitelist "httpsL//www.example.com, https://www.example2.net, https://www.example3.org"`.
Use a comma to separate multiple domains.
[]For macOS devices running OS X, IWA is enabled automatically for Safari.
[]To enable IWA on Microsoft Edge:
-
In the Windows Control Panel, select **Network and Internet **> **Internet Options**.
[See image.](#Edge1)
-
Click the **Security **tab and click **Local Intranet > Sites**.
[See image.](#Edge1a)
-
Click **Advanced**.
[See image.](#Edge1b)
- In the **Add this website to the zone **field, enter the SSO domain.
- Click **Add**.
-
Click **Close**.
[See image.](#Edge2)
Admins use their organization's preferred method to enable IWA for all users. For example, an admin might use Microsoft Group Policy Object (GPO) to enable IWA for all their users. To learn more, see [Kerberos Trust Relationship Configuration Guide for Windows Server 2012 & GPO Push](/zia/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push).
Configuring Automatic ZPA Reauthentication
Zscaler Client Connector enforces system proxy settings, and all applications on the device must comply with these settings. Administrators will review any custom proxy settings within applications, then restrict these settings.
After you've configured your IdP for SSO and enabled IWA, you can configure automatic ZPA reauthentication:
- In the Zscaler Client Connector Portal, go to **Administration **and select **Client Connector Support**.
- On the **App Supportability** tab:
-
Select **Automatically Attempt ZPA Reauthentication **to allow users to continue to access ZPA. When enabled, Zscaler Client Connector attempts to log in silently when users must reauthenticate to ZPA. Successful attempts allow users to continue accessing ZPA. If unsuccessful, users must reauthenticate manually.
If you use Zscaler Client Connector version 4.8 and later for Windows, you can enable this feature per app profile and by network type. To learn more, see [Configuring Zscaler Client Connector App Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles#zpa-reauth).
- From the **Timeout for Automatic ZPA Reauthentication (in seconds) **drop-down menu, select the time it takes for the browser to automatically reauthenticate. The default is 30 seconds. You can also select 60, 90, or 120 seconds.
- Click **Save**.
If automatic reauthentication is unsuccessful, users are prompted to reauthenticate with their credentials using Zscaler Client Connector.
![Client-Connector-Automatic-ZPA-Reauthentication](/downloads/zscaler-client-connector/zscaler-client-connector-support-settings/app-supportability/configuring-automatic-zpa-reauthentication/zclient-connector-app-support-auto-zpa-reauth.png)
[]![Firefox-about-config-negotiate](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-automatic-zpa-reauthentication/mozilla-negotiate-config.png)
[][]![Client-Connector-Firefox-aboutconfig](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-automatic-zpa-reauthentication/mozilla-automatic-config-750.png)
[]![Firefox Configuration](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-automatic-zpa-reauthentication/Firefox-about-config-negotiate-delegation.png)
[]![Firefox Configuration](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-automatic-zpa-reauthentication/Firefox-about-config-automatic.png)
[]![Firefox Configuration](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-automatic-zpa-reauthentication/Firefox-about-config-automatic-allow-proxies.png)
[]![Firefox Configuration](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-automatic-zpa-reauthentication/Firefox-about-config-negotiate-proxies.png)
[]![IWA Configuration for Edge 1](/downloads/z-app/configuring-policy-and-administration-settings/zscaler-app-support-settings/app-supportability/configuring-automatic-zpa-reauthentication/Edge%20Config%201.png)
![IWA Configuration for Edge 2](/downloads/z-app/configuring-policy-and-administration-settings/zscaler-app-support-settings/app-supportability/configuring-automatic-zpa-reauthentication/Edge%20Config%202.png)
[]![IWA Configuration for Edge 3](/downloads/z-app/configuring-policy-and-administration-settings/zscaler-app-support-settings/app-supportability/configuring-automatic-zpa-reauthentication/Edge%20Config%203.png)
[]![IWA Configuration for Edge 4](/downloads/z-app/configuring-policy-and-administration-settings/zscaler-app-support-settings/app-supportability/configuring-automatic-zpa-reauthentication/Edge%20Config%204.png)
[]![IWA Configuration for Edge 5](/downloads/z-app/configuring-policy-and-administration-settings/zscaler-app-support-settings/app-supportability/configuring-automatic-zpa-reauthentication/Edge%20Config%205.png)