# Deploying Zscaler Client Connector with Google Workspace for ChromeOS
Source: https://help.zscaler.com/unified/deploying-zscaler-client-connector-google-workspace
PDF: https://help.zscaler.com/pdf/com/en/1529011.pdf

This guide is for admins only. If you are an end user, contact your organization’s administrator for deployment-related details.
With Google Workspace, you can distribute App Store apps, including apps purchased in volume, to mobile devices. After an app is distributed, you can use Google Workspace to manage future updates to Zscaler Client Connector. You must have a required license for managing ChromeOS devices before deployment.
To deploy Zscaler Client Connector with Google Workspace:
- [Step 1: Add and Manage Public Apps with Google Workspace](#apps-with-google-workspace)
- [Step 2: Configure Always-On VPN](#config-always-on-vpn)
- []Log in to Google Admin Console.
- From the left-side navigation, go to **Devices** > **Chrome **>** Apps & Extensions**.
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
- You can add the following values to the JSON format based on your organization's needs:
- **Ownership**:** **If you use the device posture type **Ownership Variable**, enter the key `Ownership`. You can enter up to 32 alphanumeric characters in the **Configuration value** field. To learn more, see [Configuring Device Posture Profiles](/unified/configuring-device-posture-profiles).
- **userDomain**: Your organization's domain name (e.g., `safemarch.com)`. If your instance has multiple domains associated with it, enter the primary domain for your instance.
- **cloudName**: The name of the cloud on which your organization is provisioned. For example, if your cloud name is zscalertwo.net, you would enter `zscalertwo`.
- **deviceToken**: The appropriate device token from the Admin Portal, if you want to use [Zscaler Client Connector as an IdP](/unified/using-zscaler-client-connector-identity-provider).
- **customDNS**: By default, Zscaler Client Connector uses the device's DNS server. You can change the value to another DNS server using this setting. Enter the DNS IP address.
- **allowRunningOnRootedDevice**: This is set to 0 by default to restrict users from running Zscaler Client Connector on a rooted device. Enter `1` to allow users to run Zscaler Client Connector on a rooted device.
- **allowZCCOnEmulator**: This is set to 0 to restrict users from running Zscaler Client Connector on an emulator. Enter `1` to allow users to run Zscaler Client Connector on an emulator.
- **externalDeviceId**: Used to supply the Device ID externally which is used for the registration. The value for this parameter can be a unique string, such as `SERIAL_NUMBER`, or another device identifier. The MDM provides device identifiers in the form of a macro (e.g., `-: "${DEVICE_SERIAL_NUMBER}",`). The macro is replaced by the device's serial number. The default value is `"" (EMPTY_STRING)`. To use different macros, see [Deploy Android apps to managed users on ChromeOS devices](https://support.google.com/chrome/a/answer/7131624#zippy=%2Csupported-variables-for-managed-configuration-files.%2Csupported-variables-for-managed-configuration-files).
- **userName**: The username of the user. For example, if the username is j.doe@zscaler.com, you would enter `j.doe.`
- **enableFips**: Enabling this option indicates that Zscaler Client Connector uses FIPS-compliant libraries for communication with Zscaler infrastructure. Enter `1` to enable or `0` to disable this option.
Enable this option only if you require FIPS-level security within your organization.
- **autoEnrollWithMDM**: Use this parameter to determine auto-enrollment without user interaction when using Zscaler Client Connector as an IdP or to skip the app enrollment page. Select from the following options:
- Enter `0`** **to disable auto-enrollment.
- Enter `1`** **to have users always auto-enroll, even if they log out.
- Enter `2`** **for one-time auto-enrollment.
This option applies to only the Internet & SaaS-enabled accounts that are using Zscaler Client Connector as an IdP. You must specify the parameters deviceToken, cloudName, and userDomain before enabling the autoEnrollWithMDM option.
- Click **Save**.
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