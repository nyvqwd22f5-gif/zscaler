# Register Your App
Source: https://help.zscaler.com/zsdk/register-your-app
PDF: https://help.zscaler.com/pdf/com/en/1506966.pdf

Register your mobile app to create a unique app key where it contains security configurations.
To register your app:
-
Go to **Configuration & Control** > **Apps** > **Registered Apps** > **Add**.
The **Add New App** window appears.
-
In the **Add New App** window:
- **Name**: Enter the name of the mobile app.
- **Description**: Enter a description of the mobile app.
- **Authentication Type**: **One Identity** is selected as the default.
- **Trust Binding**: Select a trust binding level (Strong or Loose) that determines device re-enrollment frequency. Admins can choose the appropriate binding mode based on their organization's security requirements and user needs.
- **Strong**: Requires more frequent device re-enrollment for heightened security.
- **Loose**: Allows longer intervals between device re-enrollments.
[See image.](#AddNewApp)
- Click **Save**.
- To activate your new key on the **Registered Apps** page, click the **Publish** (![ZscaslerSDK-PublishIcon-1.png](/downloads/zsdk/getting-started/provisioning/register-app/ZscaslerSDK-PublishIcon-1.png)
) icon.
After publishing your app key, you can configure Token Validation settings for your app. To learn more, see [Managing Token Validators](/zsdk/managing-token-validators).
To use Firebase in your Apple app, you need to register your app with your Firebase project. Registering your app is often referred to as adding your app to your project.
[]
![Add New App Window](/downloads/zsdk/getting-started/provisioning/register-app-key/ZscaslerSDK-RegisterAppWindow.png)