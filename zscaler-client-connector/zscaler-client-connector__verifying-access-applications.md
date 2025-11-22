# Verifying Access to Applications
Source: https://help.zscaler.com/zscaler-client-connector/verifying-access-applications
PDF: https://help.zscaler.com/pdf/com/en/1514426.pdf

Your organization can require additional levels of authentication to access specific applications (e.g., your default access requires only a username and password, but an application with sensitive financial information requires multi-factor authentication). If you try to access an application that requires additional authentication, Zscaler Client Connector displays a pop-up notification prompting you to verify your access.
This feature is available for Zscaler Private Access (ZPA) only with Zscaler Client Connector version 4.6 and later for Windows and for Zscaler Internet Access (ZIA) only with Zscaler Client Connector version 4.7 and later for Windows. Additional authentication requirements are set up by administrators in the ZPA Admin Portal and the ZIA Admin Portal and are available only if you are subscribed to ZIdentity. To use this feature with ZIA, you must enable Use Zscaler Notification Framework in the [app profile](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles#notification) and Enable ZIA Notifications in the [end user notifications](/zscaler-client-connector/configuring-end-user-notifications-zscaler-client-connector).
To learn more, see [Understanding Step-Up Authentication](/zidentity/understanding-step-up-authentication), [Configuring Access Policies](/zpa/configuring-access-policies), and [Configuring the URL Filtering Policy](/zia/configuring-url-filtering-policy).
To verify access to applications:
-
Open Zscaler Client Connector and click **Private Access** or **Internet Security**.
The pending verification status message appears.
![Verification status message](/downloads/zscaler-client-connector/end-user-guide/verifying-access-applications/zscaler-client-connector-step-up-verify-now.png)
- Click **Verify Now**.
- Based on your organization’s authentication requirements, you might be prompted to complete one of the following steps:
- You might be redirected to your organization’s single sign-on (SSO) form. Enter your credentials and log in.
-
You might be directed to a window where you can select the application you want to access (if your organization requires verification for multiple applications). Select the application you want to access and click **Verify**. You are redirected to your organization’s authentication form. Enter your credentials and log in.
![Verification page](/downloads/zscaler-client-connector/end-user-guide/verifying-access-applications/zscaler-client-connector-step-up-select-app.png)