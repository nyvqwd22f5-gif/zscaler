# Using Zscaler Client Connector Portal as an Identity Provider
Source: https://help.zscaler.com/zscaler-client-connector/using-zscaler-client-connector-portal-identity-provider
PDF: https://help.zscaler.com/pdf/com/en/1285431.pdf

If you are a ZIdentity user, see [Using ZIdentity as an Identity Provider](/zidentity/using-zslogin-identity-provider).
This information applies to Zscaler Internet Access (ZIA) only. The Zscaler Client Connector Portal can function as an identity provider (IdP) for the Zscaler service. With this feature, users do not need to be tied to your organization’s standard IdP in order to authenticate to the Zscaler service. Instead, if your organization uses SAML-based single sign-on (SSO), Zscaler Client Connector can use a device token to auto-provision and silently authenticate users and devices for the Zscaler service.
You can generate the device token in the Zscaler Client Connector Portal and pass the token to Zscaler Client Connector in an installer option. In addition, in the ZIA Admin Portal, you must select the Zscaler Client Connector Portal as your authentication method. The app is then able to gather user ID and other relevant parameters from devices and send the information to the Zscaler cloud in SAML requests. The Zscaler Client Connector Portal parses and verifies the SAML requests, enabling the Zscaler cloud to provision and silently authenticate users.
Configuring the Zscaler Client Connector Portal to function as an IdP
To configure the Zscaler Client Connector Portal to function as an IdP:
- [Create a device token in the Zscaler Client Connector Portal](/zscaler-client-connector/creating-device-token).
- [Add the Zscaler Client Connector Portal as an IdP in the ZIA Admin Portal](/zia/adding-zscaler-client-connector-portal-idp).
- [Pass the device token, user domain, and cloud name](#PassToken).
[]To use Zscaler Client Connector as an IdP for your users, you must pass the device token, user domain, and cloud name to users' devices during installation.
- For Windows with MSI Installer, see [Customizing Zscaler Client Connector with Install Options for MSI](/zscaler-client-connector/customizing-zscaler-client-connector-install-options-msi).
- For Windows with EXE Installer, see [Customizing Zscaler Client Connector with Install Options for EXE](/zscaler-client-connector/customizing-zscaler-client-connector-install-options-exe).
- For macOS with Installer App, see [Customizing Zscaler Client Connector with Install Options for macOS](/zscaler-client-connector/customizing-zscaler-client-connector-install-options-macos).
- For Android with MDM Deployment procedures, see [Customizing Zscaler Client Connector with Install Options for Android](/zscaler-client-connector/customizing-zscaler-client-connector-install-options-android).
- For iOS with MDM Deployment procedures, see [Customizing Zscaler Client Connector with Install Options for iOS](/zscaler-client-connector/customizing-zscaler-client-connector-install-options-ios).