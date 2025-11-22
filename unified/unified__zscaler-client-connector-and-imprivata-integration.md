# Zscaler Client Connector and Imprivata Integration
Source: https://help.zscaler.com/unified/zscaler-client-connector-and-imprivata-integration
PDF: https://help.zscaler.com/pdf/com/en/1491371.pdf

This feature is available only for Zscaler Client Connector version 4.4 and later for Windows.
Zscaler Client Connector supports seamless integration with Imprivata OneSign. This integration is useful if your users authenticate on shared devices and allows you to:
- Silently log Imprivata users in to and out of Zscaler Client Connector.
- Apply different security policies on the same device based on the user.
- Log activity for each user.
In the following example, a nurse taps an Imprivata badge to access the shared workstation in Room 1. Zscaler Client Connector silently logs them in, applies the appropriate security policy, and begins tracking end user activity. When the doctor accesses the shared workstation, Zscaler Client Connector logs out the nurse and logs in the doctor. The nurse and doctor can later access the workstation in Room 2, and Zscaler Client Connector applies the same security profiles and logging as in Room 1.
![An example of Imprivata integration](/downloads/client-connector/platform-and-authentication-management/zscaler-client-connector-and-imprivata-integration/Imprivata-Integration-Example.png)
The Zscaler Client Connector system tray icon does not display when Imprivata users are logged in. Imprivata users can access Zscaler Client Connector from the Start menu. Updates to Zscaler Client Connector or changes in the Admin Portal that result in temporary downtime of the app do not affect the Imprivata login.
The following recommendations are best practices for integrating Zscaler Client Connector with Imprivata:
- Disable the [Zscaler Notification Framework](/unified/using-zscaler-notification-framework) to prevent pop-up messages for users.
- Set your Private Applications policies to expire at the same time.
To use Zscaler Client Connector integration with Imprivata:
- Deploy Zscaler Client Connector with a customized install option. To learn more, see [Customizing Zscaler Client Connector with Install Options for MSI](/unified/customizing-zscaler-client-connector-install-options-msi) and [Customizing Zscaler Client Connector with Install Options for EXE](/unified/customizing-zscaler-client-connector-install-options-exe).
- Enable Integrated Windows Authentication (IWA). To learn more about enabling IWA, see [Configuring Automatic Private Applications Reauthentication](/unified/configuring-automatic-private-applications-reauthentication).
- (Optional) If you [use WebView2 authentication](/unified/enabling-webview-2-0-authentication), enter additional domains if the user login domain is different from the IdP domain.
- View the type of user accessing a device (Windows or Imprivata) on the [Zscaler Client Connector Registered Device Details page](/unified/viewing-device-fingerprint-enrolled-device).
- View user activity on the Admin Portal.