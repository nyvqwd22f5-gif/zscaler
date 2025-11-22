# Using Zscaler Client Connector as an Identity Provider
Source: https://help.zscaler.com/unified/using-zscaler-client-connector-identity-provider
PDF: https://help.zscaler.com/pdf/com/en/1491341.pdf

Zscaler Client Connector can function as an identity provider (IdP) for the Zscaler service. With this feature, users do not need to be tied to your organization’s standard IdP in order to authenticate to the Zscaler service. Instead, if your organization uses SAML-based single sign-on (SSO), Zscaler Client Connector can use a device token to auto-provision and silently authenticate users and devices for the Zscaler service.
You can generate the device token in the Admin Portal and pass the token to Zscaler Client Connector in an installer option. In addition, you must select Zscaler Client Connector as your authentication method. The app is then able to gather user ID and other relevant parameters from devices and send the information to the Zscaler cloud in SAML requests. The Admin Portal parses and verifies the SAML requests, enabling the Zscaler cloud to provision and silently authenticate users.
Configuring Zscaler Client Connector to function as an IdP
To configure Zscaler Client Connector to function as an IdP:
- [Create a Device Token in the Admin Portal](/z-app/creating-device-token)
- [Add Zscaler Client Connector as an IdP in the Admin Portal](/unified/adding-zscaler-client-connector-idp)
- [Pass the Device Token, User Domain, and Cloud Name](#PassToken)
[]To use Zscaler Client Connector as an IdP for your users, you must pass the device token, user domain, and cloud name to users' devices during installation.
- For Windows with MSI Installer, refer to [Customizing Zscaler Client Connector with Install Options for MSI](/unified/customizing-zscaler-client-connector-install-options-msi).
- For Windows with EXE Installer, refer to [Customizing Zscaler Client Connector with Install Options for EXE](/unified/customizing-zscaler-client-connector-install-options-exe).
- For macOS with Installer App, refer to [Customizing Zscaler Client Connector with Install Options for macOS](/unified/customizing-zscaler-client-connector-install-options-macos).
- For Android with MDM Deployment procedures, refer to [Customizing Zscaler Client Connector with Install Options for Android](/unified/customizing-zscaler-client-connector-install-options-android).
- For iOS with MDM Deployment procedures, refer to [Customizing Zscaler Client Connector with Install Options for iOS](/unified/customizing-zscaler-client-connector-install-options-ios).