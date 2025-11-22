# Deploying Zscaler Client Connector with Google Workspace for ChromeOS
Source: https://help.zscaler.com/zscaler-client-connector/deploying-zscaler-client-connector-google-workspace-chromeos
PDF: https://help.zscaler.com/pdf/com/en/1509681.pdf

This guide is for admins only. If you are an end user, contact your organization’s administrator for deployment-related details.
With Google Workspace, you can distribute App Store apps, including apps purchased in volume, to mobile devices. After an app is distributed, you can use Google Workspace to manage future updates to Zscaler Client Connector. You must have a required license for managing ChromeOS devices before deployment.
To deploy Zscaler Client Connector with Google Workspace:
- [Step 1: Add and Manage Public Apps with Google Workspace](#apps-with-google-workspace)
- [Step 2: Configure Always-On VPN](#config-always-on-vpn)
- []Log in to the Google Admin Console.
- In the left-side navigation, go to **Devices** > **Chrome **>** Apps & Extensions**.
[See image.](#apps-extensions)
[]![Apps & Extensions](/downloads/zscaler-client-connector/downloading-deployment/deploying-zscaler-client-connector-google-workspace/Deploying-Zscaler-Google-Workspace-Apps-Extensions.png)
- On the right side of the screen, select the **Users & Browsers** tab.
- Click the **+** button located in the bottom-right corner of the screen and select the **Add from Google Play** icon.
[See image.](#users-browsers)
[]![Add from Google Play icon](/downloads/zscaler-client-connector/downloading-deployment/deploying-zscaler-client-connector-google-pixelbook/Deploying-Zscaler-Google-Workspace-Add-App.png)
- From the Google Play Store, select the **Client Connector - Chromebook **app for Chrome devices.
- In the expanded section on the right, under the **Installation policy** drop-down menu, select **Force install** to install the application at the endpoint.
[See image.](#force-install)
[]![Force Install](/downloads/zscaler-client-connector/downloading-deployment/deploying-zscaler-client-connector-google-workspace/Deploying-Zscaler-Google-Workspace-JSON.png)
- Under **Managed configuration, **enter the following JSON format:
``{`
`"userDomain":"<org’s_domain>",`
`"cloudName":"zscalerone",`
`"autoEnrollWithMDM":"1",`
`"deviceToken":"<token_value>",`
`"externalDeviceId":"${DEVICE_SERIAL_NUMBER}"`
`}``
[See image.](#enter-json)
[]![JSON](/downloads/zscaler-client-connector/downloading-deployment/deploying-zscaler-client-connector-google-workspace/Deploying-Zscaler-Google-Workspace-Enter-JSON.png)
- You can add [Zscaler parameters](/zscaler-client-connector/parameters-guide-zscaler-client-connector-android-and-android-chromeos) to the JSON format based on your organization's needs and click **Save**.
- []From the left-side navigation, go to **Devices** > **Settings**.
- In the **Search or add a filter **section, search for **Always on VPN**.
- Click **Edit in legacy view**. A new tab opens for configuring the Always on VPN app.
[See image.](#settings)
[]![Always on VPN](/downloads/zscaler-client-connector/downloading-deployment/deploying-zscaler-client-connector-google-pixelbook/Deploying-Zscaler-Google-Workspace-Settings-Search-for-VPN.png)
- Select the app. Apps with the **Installation Policy** configured as **Force install** appear in the search. Apps with any other configurations do not appear here. Ensure that your app's **Installation Policy** is **Force install**.
[See image.](#always-on-vpn)
[]![Client Connector - Chromebook](/downloads/zscaler-client-connector/downloading-deployment/deploying-zscaler-client-connector-google-workspace/Deploying-Zscaler-Google-Workspace-Config-Always-On-VPN.png)
- Click **OK**.
Users might be required to restart Chromebooks for the changes to be applied.