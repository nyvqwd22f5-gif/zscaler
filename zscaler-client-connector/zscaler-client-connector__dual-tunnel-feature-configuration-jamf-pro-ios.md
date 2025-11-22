# Dual Tunnel Feature Configuration with Jamf Pro for iOS
Source: https://help.zscaler.com/zscaler-client-connector/dual-tunnel-feature-configuration-jamf-pro-ios
PDF: https://help.zscaler.com/pdf/com/en/1506691.pdf

With the dual tunnel feature, organizations can capture Per App traffic via a secondary tunnel and send it to the Zscaler Private Access (ZPA) applications, while all other apps still tunnel to Zscaler Internet Access (ZIA) through the primary tunnel.
Before following this guide, ensure that Zscaler Client Connector is installed on your device. To learn more, see [Deploying Zscaler Client Connector with Jamf Pro for iOS](/zscaler-client-connector/deploying-zscaler-client-connector-jamf-pro-ios).
With Jamf Pro, you can configure the dual tunnel feature for iOS devices:
- [Step 1: Create and Push Primary Tunnel Configuration Profile from Jamf Pro](#primary-tunnel)
- [Step 2: Create and Push Secondary Tunnel Configuration Profile from Jamf Pro](#secondary-tunnel)
- [Step 3: Push Per App VPN App on Mobile Device from Jamf Pro](#push-per-app-vpn)
- [Step 4: Install Per App VPN App from Self Service Application](#install-per-app-vpn)
- [Step 5: Verify Profiles Created on iOS VPN Settings](#verify-profiles)
- []In the **Devices** section, go to **Configuration Profile**.
[See image.](#primary-config)
[]![Primary config profiles](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-primary-tunnel-config-profiles_0.png)
- Click **New**.
[See image.](#primary-config-new)
[]![New profile](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-primary-tunnel-new-profile.png)
- In the **General** section, enter a **Name** for the profile.
[See image.](#primary-profile-name)
[]![Enter details in the general section](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-primary-tunnel-general-info_0.png)
- From the menu on the left, scroll down to the **VPN** section.
In the **VPN** section:
- **Connection Name**: Enter a name for the connection.
- **VPN Type**: Choose **VPN**.
- **Connection Type**: Choose **Custom SSL**.
- **Identifier**: Enter `com.zscaler.zscaler`
- **Server**: Enter `VPN`
- **Provider Bundle Identifier**: Enter `com.zscaler.zscaler.tunnel`
[See image.](#primary-vpn)
[]![Details for the VPN section](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-primary-tunnel-vpn_1.png)
- **Custom Data**: Click **Add** to add the key `tunnelType` and value `ZIA`.
- **User Authentication**: Choose **Certificate.**
- **Provider Type**: Choose **Packet-Tunnel.**
[See image.](#primary-vpn-settings)
[]![Custom data and user auth](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-primary-tunnel-vpn-custom-data.png)
- Select **Enable VPN On Demand** and **Prohibit users from disabling on-demand VPN settings **option.
[See image.](#primary-vpn-enable)
[]![Enable VPN fields](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-primary-tunnel-vpn-enable_0.png)
- Click **Save**.
- In the **Scope** section, click **Add **to add a device.
[See image.](#primary-scope)
[]![Scope section](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-primary-tunnel-scope_0.png)
- []In the **Devices** section, go to **Configuration Profile** and click **New**.
- In the **General** section, provide a **Name** for the profile.
[See image.](#secondary-general)
[]![General section of secondary tunnel](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-secondary-tunnel-general-info_0.png)
- From the menu on the left, scroll down to the **VPN** section.
In the **VPN** section:
- **Connection Name**: Enter a name for the connection.
- **VPN Type**: Choose **Per-App VPN**
- Select **Automatically start Per App VPN connection**
[See image.](#secondary-vpn)
[]![Add details for the secondary tunnel VPN](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-secondary-tunnel-vpn_1.png)
- **Per-App VPN Connection Type**: Choose **Custom SSL**
- **Identifier**: Enter `com.zscaler.zscaler`
- **Server**: Enter `VPN`
- **Provider Bundle Identifier**: Enter `com.zscaler.zscaler.tunnelsecondary`
- **Custom Data**: Click **Add** to add the key `tunnelType` and value `APP`.
[See image.](#secondary-vpn-settings)
[]![VPN section](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-secondary-tunnel-vpn-per-app.png)
- **User Authentication**: Choose **Certificate**
- **Provider Type**: Choose **Packet-Tunnel**
[See image.](#secondary-vpn-settings-2)
[]![VPN section user auth and provider type](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-secondary-tunnel-vpn-user-auth.png)
- Select the **Enable VPN On Demand **and **Prohibit users from disabling on-demand VPN settings**
[See image.](#secondary-vpn-settings-enable)
[]![Enable options in the VPN section](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-secondary-tunnel-vpn-enable.png)
- Click **Save**.
- In the **Scope** section, click **Add **to add a device.
[See image.](#secondary-scope)
[]![Scope section](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-secondary-tunnel-scope.png)
- []In the **Devices** section, go to **Mobile Device Apps** and click **New**.
[See image.](#mobile-device-apps)
[]![Mobile device apps](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-per-app-vpn-mobile-device.png)
- Select the previously added application. For example, **Microsoft Edge: Web Browser**.
- In the **General** section, choose the **Make Available in Self Service **option for the **Distribution method**.
[See image.](#mobile-device-apps-general)
[]![General section of mobile device apps](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-per-app-vpn-mobile-device-dist-method.png)
- Scroll down to the **Per-App Networking** section. For **Per-App VPN,** select the Per-App VPN profile that you created in [Step 2: Create and Push Secondary Tunnel Configuration Profile from Jamf Pro](/zscaler-client-connector/dual-tunnel-feature-configuration-jamf-pro-ios#secondary-tunnel)
[See image.](#mobile-device-apps-per-app)
[]![Add previously created per-app profile in Per-app networking](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-per-app-vpn-mobile-device-networking_1.png)
- In the **Scope** section, click **Add **to add a device.
- []On a mobile phone, open the **Self Service** application.
[See image.](#self-service)
[]![Self-service application](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-per-app-self-service.png)
- Browse all the listed applications and install the Per-App VPN Application. For example, Microsoft Edge.
[See image.](#install-per-app)
[]![Per-app install](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-per-app-self-service-application_0.png)
- []Go to your mobile phone **Settings**> **General** > **VPN & Device Management**.
[See image.](#vpn-device-management)
[]![VPN & Device Management](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-per-app-general-settings-iphone.png)
- The two VPN profiles that you created are shown in the **Device VPN** and **Per-App VPN** sections.
[See image.](#vpn-profiles)
[]![Per-app profiles](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-jamf-pro-ios/ZSclientconnector-jamf-per-app-self-service-application-vpn-on-iphone_1.png)