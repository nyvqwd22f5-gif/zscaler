# Using WebView2 Authentication
Source: https://help.zscaler.com/zscaler-client-connector/using-webview2-authentication
PDF: https://help.zscaler.com/pdf/com/en/1477906.pdf

If your organization uses advanced multi-factor authentication (MFA) for SAML or FIDO2 (Fast Identity Online 2), your users can authenticate using WebView2 in their embedded browser. Zscaler Client Connector still manages traffic for Zscaler Internet Access (ZIA) and provides access to applications through Zscaler Private Access (ZPA).
This article describes how to configure and enable WebView2.
Users can also authenticate using their browser. To learn more, see [Enabling Browser-Based Authentication](/zscaler-client-connector/about-authentication-settings).
Prerequisites
To use WebView2 authentication, your system must meet the following minimum versions:
- Zscaler Client Connector version 4.2 or later for Windows
- .Net Framework 4.5+
- WebView2 103.0.1264.42+
If an existing version of WebView2 is earlier than the minimum version, Zscaler Client Connector pulls the latest version from Microsoft's content delivery network (CDN), using the bootstrap installer included in the Zscaler Client Connector install package.
Configuring WebView2
To avoid encountering issues with the automated download and install of WebView2 by the Evergreen WebView2 bootstrap installer included in the Zscaler Client Connector package, do the following:
- Bypass the following Microsoft CDN domains in strict enforcement mode or for any other security policies, so that the bootstrapper can download and install WebView2.
- .delivery.mp.microsoft.com
- .cdp.microsoft.com
The WebView2 installation is shared by other apps which use the WebView2 runtime.
- Allowlist the file `MicrosoftEdgeWebview2Setup.exe` in antivirus and other security policies on client machines. To learn more, see [Zscaler Client Connector Processes to Allowlist](/zscaler-client-connector/zscaler-client-connector-processes-allowlist).
WebView2 launches its own set of processes, so Zscaler Client Connector must bypass them in the strict enforcement mode. The full path of the exe is: `%ProgramFiles%\Zscaler\ThirdParty\WebView2\MicrosoftEdgeWebview2Setup.exe`.
Enabling WebView2 Authentication
To enable WebView2 authentication in the Zscaler Client Connector Portal:
- In the left-side navigation, select **Administration** > **Platform Settings**.
- Select the respective platform tab.
- Under **Authentication Settings**:
- **WebView2**: Select this option to enable WebView2 authentication.
- **SSO using Windows Primary account**: (Optional) Select this option to automatically log in users in an Azure AD environment using Windows as an IdP. If this option is disabled, users must enter their credentials separately to log in to Zscaler Client Connector. This option is available only for Zscaler Client Connector version 4.4 and later for Windows.
- **Ignore Client Cert errors for Webview2**: (Optional) Select this option to have Zscaler Client Connector continue authenticating if the IdP requires a client certificate for mutual authentication but the client device does not have a client certificate or if the client certificate is invalid. This option is available only for Zscaler Client Connector version 4.4 and later for Windows.
- **Allow WebView2 to follow System Proxy**: (Optional) Deselect this option to connect directly to the internet. This option is available only for Zscaler Client Connector version 4.5 and later for Windows.
- **Additional IdP Domains**: (Optional) Enter additional domains if the user login domain is different from the IdP domain. These domains are added to the Auth Server allowlist in the embedded WebView2 browser along with the user login domain added by default. This option is available only for Zscaler Client Connector version 4.6 and later for Windows and you must [integrate with Imprivata](/zscaler-client-connector/zscaler-client-connector-and-imprivata-integration) to use it with a version earlier than 4.8.
-
**Display certificate selection popup on desktop**: (Optional) Select this option to display a list of certificates for the user to select from in a pop-up window if multiple authentication certificates for the IdP are available. If disabled, the selection window displays only when users are viewing the app. Available only with Zscaler Client Connector version 4.7 and later for Windows.
If you select this option, you can enable [app profile options](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles#auth) to control what displays when users reauthenticate to Zscaler Private Access (ZPA)
- Click **Save**.
![Enabling WebView2 authentication](/downloads/zscaler-client-connector/platform-and-authentication-management/using-webview2-authentication/zclient-connector-platform-settings-webview2_2.png)