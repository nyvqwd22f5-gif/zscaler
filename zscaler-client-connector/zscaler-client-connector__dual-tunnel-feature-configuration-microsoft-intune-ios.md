# Dual Tunnel Feature Configuration with Microsoft Intune for iOS
Source: https://help.zscaler.com/zscaler-client-connector/dual-tunnel-feature-configuration-microsoft-intune-ios
PDF: https://help.zscaler.com/pdf/com/en/1508081.pdf

With the dual tunnel feature, organizations can capture Per App traffic via a secondary tunnel and send it to the Zscaler Private Access (ZPA) applications, while all other apps continue tunneling to Zscaler Internet Access (ZIA) through the primary tunnel.
Before using this guide, ensure that Zscaler Client Connector is installed on your device. To learn more, see [Deploying Zscaler Client Connector with Microsoft Intune for iOS](/zscaler-client-connector/deploying-zscaler-client-connector-microsoft-intune-ios).
With Microsoft Intune, you can configure the dual tunnel feature for iOS devices:
- [Step 1: Create and Push Primary Tunnel Configuration Profile from Microsoft Intune](#primary-tunnel)
- [Step 2: Create and Push Secondary Tunnel Configuration Profile from Microsoft Intune](#secondary-tunnel)
- [Step 3: Assign Secondary Tunnel Configuration Profile to a Third-Party App](#secondary-tunnel-third-party)
- [Step 4: Verify Profiles Created on iOS VPN Settings](#verify-profiles)
- []In the **Devices** section, go to **Configuration > Create > New Policy**.
[See image.](#primary-config-new)
[]![Add a new policy](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/dual-tunnel-ios-intune-primary-tunnel-new.jpg)
- In the **Create a Profile** section:
- **Profile type**: Select **Templates**.
- **Template name**: Select **Custom**.
- Click **Create**.
[See image.](#primary-template)
[]![Create a profile](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/dual-tunnel-ios-intune-primary-template_1.jpg)
- In the **Basics **section, enter a **Name** and provide an optional **Description**.
[See image.](#primary-basics)
[]![Add a name and description](/downloads/zscaler-client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/dual-tunnel-ios-intune-primary-basics.jpg)
- Click **Next**.
- In the **Configuration settings** section:
- **Custom configuration profile name**: Enter the name of the configuration profile.
- **Configuration profile file**: Download the [Dual Tunnel Primary VPN mobileconfig file](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/Dual%20Tunnel%20Primary%20VPN%20Intune.mobileconfig) and upload it. The mobileconfig file is populated in the box.
[See image.](#primary-config-settings)
[]![input primary config settings](/downloads/zscaler-client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/dual-tunnel-ios-intune-primary-config-settings.jpg)
- Click **Next**.
- In the **Assignment** section, assign groups/users to the profiles.
[See image.](#primary-assignments)
[]![Assignments section](/downloads/client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/dual-tunnel-ios-intune-primary-assignments.jpg)
- Click **Create** to publish the profile.
[See image.](#primary-review-profile)
[]![Review and create your profile](/downloads/zscaler-client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/dual-tunnel-ios-intune-primary-review-profile.jpg)
- []In the **Devices** section, go to **Configuration > Create > New Policy**.
[See image.](#secondary-new)
[]![Create a new policy](/downloads/zscaler-client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/dual-tunnel-ios-intune-secondary-tunnel-new.jpg)
- In the **Create a Profile** section:
- **Profile type**: Select **Templates**.
- **Template name**: Select **VPN**.
- Click **Create**.
[See image.](#secondary-template)
[]![Create a profile](/downloads/zscaler-client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/dual-tunnel-ios-intune-secondary-template.jpg)
- In the **Basics **section, enter a **Name** and provide an optional **Description**.
[See image.](#secondary-basics)
[]![Enter a Name and a Description](/downloads/zscaler-client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/dual-tunnel-ios-intune-secondary-basics_0.jpg)
- Click **Next**.
- In the **Configuration settings** section:
- **Connection type**: Choose **Custom VPN**.
[See image.](#secondary-config-settings)
[]![VPN configuration settings](/downloads/zscaler-client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/dual-tunnel-ios-intune-secondary-config-settings-connection-type.jpg)
- **Connection name**: Enter a name for the VPN connection.
- **VPN server address**: Enter `perappvpn`.
- **Authentication method**: Enter your authentication method.
- **Split tunneling**: Select **Disable**.
- **VPN identifier**: Enter `com.zscaler.zscaler`.
- **Enter key and value pairs for the custom VPN attributes**: Enter the key `tunnelType` and the value `APP`. To add other key value pairs, see [Deploying Zscaler Client Connector with Microsoft Intune for iOS](/zscaler-client-connector/deploying-zscaler-client-connector-microsoft-intune-ios).
[See image.](#secondary-config-settings-2)
[]![Fill the configuration settings for VPN](/downloads/zscaler-client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/dual-tunnel-ios-intune-secondary-config-settings_0.jpg)
- Click **Next**.
- In **Automatic VPN**:
- **Type of automatic VPN**: Select **Per-app VPN**.
- **Provider Type**: Select **packet-tunnel**.
- Click **Next**.
[See image.](#secondary-vpn-settings)
[]![VPN settings](/downloads/zscaler-client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/dual-tunnel-ios-intune-secondary-vpn-settings.jpg)
- In the **Assignment** section, assign groups/users to the profiles.
[See image.](#secondary-assignments)
[]![Assignments section](/downloads/zscaler-client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/dual-tunnel-ios-intune-secondary-assignments_0.jpg)
- Click **Create** to publish the profile.
[See image.](#secondary-review-profile)
[]![Create the profile](/downloads/zscaler-client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/dual-tunnel-ios-intune-secondary-vpn-review_0.jpg)
- []Go to **Apps** > **iOS/iPadOS apps**.
- Search for the app you want to assign the secondary tunnel configuration profile to.
- Click the app to select it.
[See image.](#mobile-device-apps)
[]![Apps section](/downloads/zscaler-client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/dual-tunnel-ios-intune-secondary-third-party-search-app.jpg)
- From the left-side navigation, go to **Properties**.
- Click **Edit** next to **Assignments**.
[See image.](#secondary-third-party-assignments)
[]![Edit assignment](/downloads/zscaler-client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/dual-tunnel-ios-intune-secondary-third-party-properties_1.jpg)
- Scroll down to the **Per-App Networking** section. For **Per-App VPN,** select the Per-App VPN profile that you created in [Step 2: Create and Push Secondary Tunnel Configuration Profile from Microsoft Intune](/zscaler-client-connector/dual-tunnel-feature-configuration-microsoft-intune-ios#secondary-tunnel).
- In **App settings**, for **VPN**, select **None** from the drop-down menu. A list of VPNs you created appear.
[See image.](#secondary-third-party-assignments-edit)
[]![Edit assignment](/downloads/zscaler-client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/dual-tunnel-ios-intune-secondary-third-party-assignments-edit_0.jpg)
- Click OK.
- Click **Review+save**.
- Click **Save** to publish the change.
[See image.](#secondary-third-party-edit-application)
[]![Review and save](/downloads/zscaler-client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/dual-tunnel-ios-intune-secondary-third-party-edit-application_0.jpg)
- []In the **Settings **section of your iPhone, go to **VPN**.
- Verify that the two VPN profiles you created are shown in the **Device VPN** and **Per-App VPN** sections.
[See image.](#iphone-vpn)
[]![Device VPN and Per-App VPN](/downloads/zscaler-client-connector/downloading-deployment/dual-tunnel-feature-configuration-microsoft-intune-ios/dual-tunnel-ios-intune-secondary-iphone-vpn-settings_0.jpg)