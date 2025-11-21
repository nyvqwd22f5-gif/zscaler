# Using ZIdentity as an Identity Provider
Source: https://help.zscaler.com/zidentity/using-zidentity-identity-provider
PDF: https://help.zscaler.com/pdf/com/en/1499311.pdf

ZIdentity can function as an identity provider (IdP) for the Zscaler service. With this feature, users need not be tied to your organization’s standard IdP to authenticate to the Zscaler service. Instead, if your organization uses SAML-based single sign-on (SSO), ZIdentity can use a device token to auto-provision and silently authenticate users and devices to the Zscaler service.
Configuring the ZIdentity to Function as an IdP
To configure ZIdentity as an IdP:
- [1. Generate Device Token in the Zscaler Client Connector Portal.](#zcc-device-token)
- [2. Enable the device token in the ZIdentity Admin Portal](/zidentity/managing-device-token-authentication).
- [3. Pass the device token, user domain, and cloud name to users' devices.](#step3-passtoken)
-
[][Log in to ZIdentity](/zidentity/accessing-and-navigating-zidentity-landing-page) and click the** Zscaler Client Connector **tile.
[See image.](#landing-page)
- [Create a Device Token.](/zscaler-client-connector/creating-device-token)
-
Copy the generated device token shown in the Zscaler Client Connector Portal.
[See image.](#device-token-screen)
[]To use ZIdentity as an IdP for your users, you must pass the device token generated and copied from the Zscaler Client Connector Portal, user domain, and cloud name to users' devices during installation.
- For Windows with MSI Installer, see [Customizing Zscaler Client Connector with Install Options for MSI](/zscaler-client-connector/customizing-zscaler-client-connector-install-options-msi).
- For Windows with EXE Installer, see [Customizing Zscaler Client Connector with Install Options for EXE](/zscaler-client-connector/customizing-zscaler-client-connector-install-options-exe).
- For macOS with Installer App, see [Customizing Zscaler Client Connector with Install Options for macOS](/zscaler-client-connector/customizing-zscaler-client-connector-install-options-macos).
- For Android with MDM Deployment procedures, see [Customizing Zscaler Client Connector with Install Options for Android](/zscaler-client-connector/customizing-zscaler-client-connector-install-options-android).
- For iOS with MDM Deployment procedures, see [Customizing Zscaler Client Connector with Install Options for iOS](/zscaler-client-connector/customizing-zscaler-client-connector-install-options-ios).
[]![A screenshot highlighting the Zscaler Client Connetor tile in ZIdentity Landing Page](/downloads/zidentity/authentication/using-zslogin-identity-provider/zidentity-zcc-tile.png)
[]![A screenshot highlighting the Device Toekn in Zscaler Client Connector Portal](/downloads/zidentity/authentication/using-zslogin-identity-provider/zidenetity-copy-device-token.png)