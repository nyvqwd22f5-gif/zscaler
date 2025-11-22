# About Platform Settings
Source: https://help.zscaler.com/zscaler-client-connector/about-platform-settings
PDF: https://help.zscaler.com/pdf/com/en/1443706.pdf

The Platform Settings page allows you to configure settings by platform.
The Platform Settings page provides the following benefits:
- The flexibility to allow users to authenticate using either their device’s default browser or by using WebView2 (for Zscaler Client Connector version 4.2 and later for Windows).
- The simplicity of setting the global default log mode for all new policies at once instead of having to configure the setting for each new customer.
- An extra layer of security if you use your own mechanism for deploying Zscaler Client Connector on your users' devices. For example, you might use a Group Policy Object (GPO), System Center Configuration Manager (SCCM), or other device management method (for Zscaler Client Connector version 4.2.1 and later for Windows).
About the Platform Settings Page
On the Platform Settings page (Administration > Platform Settings), you can configure settings for each of the following device platforms:
[Windows](#Windows)
[macOS](#macOS)
[Linux](#Linux)
[iOS](#iOS)
[Android](#Android)
[]
To configure platform settings for Windows, click the **Windows **tab and select from the following settings:
For Windows only, users can authenticate in the following two ways:
- Using Browser-Based Authentication so that Zscaler Client Connector opens in their device’s default browser.
- Using WebView2 for the embedded browser.
If both options are selected, Browser-Based Authentication overrides WebView2.
- [Enable Browser-Based Authentication](/zscaler-client-connector/about-authentication-settings).
- [Enable WebView2 authentication.](/zscaler-client-connector/enabling-webview-2.0-authentication)
- [Enable resizing of the Zscaler Client Connector authentication window.](/zscaler-client-connector/enabling-resizing-zscaler-client-connector-authentication-window)
- [Set the global default log mode](/zscaler-client-connector/configuring-global-default-log-level).
- [Enable Zscaler Digital Experience (ZDX) Module upgrades via the CLI.](/zscaler-client-connector/enabling-zdx-module-upgrades-cli)
- [Configure passwords for access in unattended mode](/zscaler-client-connector/configuring-passwords-access-unattended-mode).
![About Platform setting](/downloads/zscaler-client-connector/platform-and-authentication-management/about-platform-settings/zclient-connector-platform-settings-windows_0.png)
[]
To configure platform settings for macOS, click the **macOS** tab and select from the following settings:
- [Enable Browser-Based Authentication](/zscaler-client-connector/about-authentication-settings).
- [Use the Default Browser](/zscaler-client-connector/enabling-browser-based-authentication).
- [Set the global default log mode](/zscaler-client-connector/configuring-global-default-log-level).
![Platform Settings macOS tab](/downloads/tech-pubs-drafts/client-connector-draft-articles/about-platform-settings/Platform_Settings_mac_OS.png)
[]
To configure platform settings for Linux, click the **Linux** tab and select from the following settings:
- [Enable Browser-Based Authentication](/zscaler-client-connector/about-authentication-settings).
- [Set the global default log mode](/zscaler-client-connector/configuring-global-default-log-level).
![Platform Settings Linux tab](/downloads/tech-pubs-drafts/client-connector-draft-articles/about-platform-settings/Platform_Settings_Linux_2.png)
[]
To configure platform settings for iOS, click the **iOS **tab and select from the following settings:
- [Enable Browser-Based Authentication](/zscaler-client-connector/about-authentication-settings).
- [Set the global default log mode](/zscaler-client-connector/configuring-global-default-log-level).
- [Use Device Groups in Service Entitlement](/zscaler-client-connector/enabling-device-groups-android).
![Platform Settings iOS tab](/downloads/tech-pubs-drafts/client-connector-draft-articles/about-platform-settings-doc-60531-doc-60440/about-platform-settings-ios.png)
[]
To configure platform settings for Android, click the **Android **tab and select from the following settings:
- [Enable Browser-Based Authentication](/zscaler-client-connector/about-authentication-settings).
- [Set the global default log mode](/zscaler-client-connector/configuring-global-default-log-level).
- [Use Device Groups in Service Entitlement](/zscaler-client-connector/enabling-device-groups-android).
![Platform Settings Android tab](/downloads/tech-pubs-drafts/client-connector-draft-articles/about-platform-settings/Platform_Settings_Android_4.png)