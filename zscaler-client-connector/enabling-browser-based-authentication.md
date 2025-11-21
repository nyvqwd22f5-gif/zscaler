# Enabling Browser-Based Authentication
Source: https://help.zscaler.com/zscaler-client-connector/enabling-browser-based-authentication
PDF: https://help.zscaler.com/pdf/com/en/1382586.pdf

If your organization uses advanced multi-factor authentication (MFA) for SAML, your users can authenticate using their browser instead of authenticating in Zscaler Client Connector. Zscaler Client Connector still manages traffic for Zscaler Internet Access (ZIA) and provides access to applications through Zscaler Private Access (ZPA).
Zscaler must enable this feature.
- In the Zscaler Client Connector Portal, go to **Administration**.
- In the left-side navigation, select **Platform Settings**.
- Select the platform tab where you want to enable browser authentication.
- [Windows](#windows)
- [macOS](#macOS)
- [Linux](#linux)
- [iOS](#iOS)
- [Android](#android)
[]Applies to Windows version 3.6 and later.
- Select **Browser-Based Authentication**.
![Enable Browser Based Authentication](/downloads/client-connector/platform-and-authentication-management/about-authentication-settings/Windows-Browser-Based-Authentication.png)
[]Applies to macOS version 3.6 and later.
- Select **Browser-Based Authentication**.
- Select **Use Default Browser **to use your default browser for authentication.
If you enable **Browser-Based Authentication** only, Zscaler Client Connector uses the Safari browser for authentication.
![Enable Browser Based Authentication macOS](/downloads/tech-pubs-drafts/client-connector-draft-articles/about-authentication-settings-draft/macOS_bb.png?1675464919)
[]Applies to Linux version 1.3 and later. Select **Browser-Based** **Authentication**.
![Enable Browser Based Authentication Linux BB](/downloads/tech-pubs-drafts/client-connector-draft-articles/about-authentication-settings-draft/linux_BB.png?1675465735)
[]Applies to iOS version 1.8.8 and later. Select **Browser-Based** **Authentication**.
![Enable Browser Based Authentication iOS](/downloads/tech-pubs-drafts/client-connector-draft-articles/about-authentication-settings-draft/iOS_BB_log.png)
[]Applies to Android version 1.9.1 and later. Select **Browser-Based** **Authentication**.
![Enable Browser Based Authentication Android](/downloads/tech-pubs-drafts/client-connector-draft-articles/enabling-zia-device-groups/Android%20BB.png?1675889675)
- Click **Save**.