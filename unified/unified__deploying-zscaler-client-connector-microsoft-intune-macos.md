# Deploying Zscaler Client Connector with Microsoft Intune for macOS
Source: https://help.zscaler.com/unified/deploying-zscaler-client-connector-microsoft-intune-macos
PDF: https://help.zscaler.com/pdf/com/en/1492281.pdf

With Microsoft Intune, you can deploy Zscaler Client Connector for your macOS devices. Before deploying Zscaler Client Connector from the Microsoft Intune admin center, download the .pkg file from the Zscaler Client Connector App Store first. The version used for the following steps is Microsoft Intune Service release version 2507.
- [][Step 1: Download the Zscaler Client Connector .pkg file](#a-pkg-file)
- [Step 2: Deploy Zscaler Client Connector from the Microsoft Intune admin center](#deploy-intune-portal)
- [Step 3: Configure Optional Settings](#optional-settings)
- [][Configure a Custom Settings Profile](#configure-custom-profile)
- [Configure a Certificate Configuration Profile](#certificate-config-profile)
- [Configure a Transparent Proxy-based Traffic Interception](#transparent-proxy)
- [Configure Tunnel Parameters](#config-tunnel-param)
- [Configure a Custom VPN Profile for ZPA VPN (for Legacy Apps)](#custom-VPN-profile-ZPA-VPN-service)
- [Configure Full Disk Access for Endpoint DLP](#configure-full-disk-access-endpoint-DLP)
- [Configure Managed Login Items](#managed-login)
- [Configure a Custom VPN Profile for Application Bypasses](#config-custom-vpn-application-bypass)
[]To deploy Zscaler Client Connector using the Microsoft Intune admin center, you must obtain a .pkg file from the Admin Portal.
To download the Zscaler Client Connector .pkg file:
- In the Admin Portal, go to **Infrastructure** > **Common Resources** > **Client Connector Deployment** > **Platform Releases**.
- On the **New Releases **tab, select **macOS**.
- Download the .pkg file.
![pkg file](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/app-store-admin-new-releases-macos-pkg.png)
[]To deploy Zscaler Client Connector on your macOS devices from the Microsoft Intune admin center:
- In the Microsoft Intune admin center, click **Apps** from the menu.
- In the **By platform** section, select **macOS**.
- Click **Create**.
- In **Select app type**, click **macOS app (PKG)**.
[See image.](#apps-macos)
[]![Microsoft endpoint manager screen with menu](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/apps-mac-pkg_0.png)
- Click **Select**.
- In the **App Information** section, click **Select app package file **and upload the PKG file downloaded in the [Download the Zscaler Client Connector .pkg](#download-pkg-step) file step.
- Click **OK**.
[See image.](#click-select)
[]![Microsoft endpoint manager screen with menu for app type - line of business](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/apps-upload-pkg_0.png)
- In the **App information** section:
- **Select file**: Displays the uploaded PKG file.
- **Name**: Enter `Zscaler Client Connector X.X.X.X - macOS X.X.X.X` (where X.X.X.X is the version number of the app and allows you to distinguish the version distributed by Intune).
- **Description**: Enter `Zscaler Client Connector for macOS`.
- **Publisher**: Enter `Zscaler, Inc`.
- **Category**: (Optional) Select an app category to allocate Zscaler Client Connector to.
[See image.](#app-information)
[]![Microsoft endpoint manager screen with menu for app information](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/apps-upload-pkg-app-info_1.png)
- Click **Next**.
- In the **Program** section, configure the app installation scripts, if required.
[See image.](#program)
[]![Microsoft endpoint manager screen with menu for app information](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/program.png)
- Click **Next**.
- In the requirements section, select the **Minimum operating system**.
- Zscaler Client Connector versions 3.7 and earlier support macOS 10.14.
- Zscaler Client Connector versions 3.7 to 4.5.1 support macOS 10.15.
- Zscaler Client Connector versions 4.5.1 and later support macOS 12.4.
- In the **Detection rules** section:
- **Ignore app version**: Select **Yes**.
- **Included apps**: Provide a list of apps included in the uploaded PKG file.
If Intune populates `zscaler.installer.uninstall`, delete it. If the app version is different from the .pkg file you uploaded, manually fix it.
- Click **Next**.
- On the **Assignments** tab, select the group assignments for which you want to deploy Zscaler Client Connector.
You can allocate users or groups to two different sections depending on how you want the app rolled out to users.
- **Required**: The app is mandatory for these users and groups. The app is automatically pushed to the users of this group.
- **Available for enrolled devices**: The app is optional for these users and groups. The app is not automatically pushed and the users can download the app themselves from the Intune Company Portal.
[See image.](#assignments)
[]![Microsoft endpoint manager screen with menu for assignments](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/apps-assignments.png)
- Click **Next**.
- On the **Review + create** tab, review the values and settings entered, and then click **Create**.
[]You can use a property list (PLIST) file to set values for various configuration keys in the Microsoft Intune admin center. To configure a custom settings profile in the Microsoft Intune admin center:
- In the Microsoft Intune admin center, go to **Devices **>**Configuration**.
-
Click **Create** > **New Policy**.
[See image.](#custom-settings-device-config-create)
-
In the **Create a profile** section:
- **Platform**: Select **macOS**.
- **Profile type**: Select **Templates**.
- **Template name**: Choose **Preference file**.
[See image.](#custom-settings-create-profile-section)
- Click **Create**.
-
In the **Basics** section:
- **Name**: Enter a name for the preference file. For example, `Zscaler Plist`.
- **Description**: (Optional) Enter a description.
[See image.](#custom-settings-basics)
- Click **Next**.
-
In the **Configuration settings** section:
- **Preference domain name**: Enter `com.zscaler.installparams`.
- **Property list file**: Upload the property list file. You can use the [ZscalerSample.plist](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-macos/ZscalerSamplePlist.plist) file as a starting template, and edit the following values in the <VendorConfig> section of the file based on your needs:
- **cloudName**: The name of the cloud on which your organization is provisioned. For example, if your cloud name is zscalertwo.net, you would enter zscalertwo.
- **deviceToken**: The appropriate device token from the Admin Portal, if you want to use the [Zscaler Client Connector as an IdP](/unified/using-zscaler-client-connector-identity-provider).
- **hideAppUIOnLaunch**: Forces the app window to stay hidden before users enroll. Users can always open the window by clicking the app icon in the system tray.
- **launchTray**: By default, Zscaler Client Connector starts its services and user interface after installation. launchTray prevents Zscaler Client Connector from automatically starting after installation. Users must open Zscaler Client Connector manually to start the app, or Zscaler Client Connector automatically runs after the next reboot.
- **policyToken**: Allows you to specify which app profile policy you want to enforce for the app before the user enrolls. All relevant settings associated with the policy apply, including the bypass of the IdP login page. Once the user enrolls, this policy is replaced with the app profile policy that matches the user based on group affiliation.
- **strictEnforcement**: Allows you to block internet traffic before the user enrolls in Zscaler Client Connector. strictEnforcement works when the forwarding profile action for Zscaler Client Connector is **Tunnel** or **Tunnel with Local Proxy**.
- **userDomain**: This allows you to configure the user domain so that the users skip the Zscaler Client Connector enrollment page and directly go to the SSO login page.
- **externalRedirect**: Allows you to redirect authentication to your organization’s SAML IdP through the Safari browser. When redirected to the browser for the first time, the users must select Remember Me on their IdP log-in screen. For any subsequent authentications, the browser remembers the user and automatically logs them in.
[See image.](#custom-settings-plist)
- Click **Next**.
-
In the **Assignments** section, choose the users, groups, and devices for the profile.
[See image.](#custom-settings-assignments)
- Click **Next**.
- In the **Review + create** section, review the summary, and click **Create**.
[]![Creating a new profile in the Microsoft Intune Portal](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-custom-config-macos-config-create.png)
[]![Create a profile in configuration profiles](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-draft/zclientconnector-macos-config%20profiles-create-profile.png)
[]![Basics section in the configuration profiles](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-custom-config-macos-config-basics.png)
[]![Configuration settings](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-custom-config-macos-config-plist.png)
[]![Assignments section in configuration profiles](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-custom-config-macos-config-assignments.png)
[]If you use Internet & SaaS and you want to perform SSL inspection, you must configure a certificate profile to push the Certificate Authority (CA) certificate required for SSL inspection. You can use the default Zscaler CA certificate or a custom Root or Intermediate CA certificate. To learn more, see [Choosing the CA Certificate for SSL Inspection](/unified/choosing-ca-certificate-ssl-inspection) and [Certificate Pinning and SSL Inspection](/unified/certificate-pinning-and-ssl-inspection).
To configure a certificate configuration profile:
- [(Optional) Download the Zscaler CA Certificate.](#download-zscaler-certificate)
- [Configure the Certificate Profile.](#configure-cert-profile)
[]To download the certificate:
- In the Admin Portal, go to **Policies **>** Common Configuration **>** SSL/TLS Inspection **>** SSL/TLS Inspection Intermediate Certificate.**
-
Click the **Edit** icon corresponding to the Zscaler Intermediate CA Certificate.
The **View Zscaler Intermediate CA Certificate** window appears.
-
In the **View Zscaler Intermediate CA Certificate** window, under the **Root Certificate** field, click **Download**.
The root certificate is downloaded as a ZIP file.
- Navigate to the ZscalerRootCerts.zip file, unzip it, and rename the file extension `.cer`.
[]To configure the certificate profile:
- In the Microsoft Intune admin center, go to **Devices** > **Configuration**.
- Go to **Create** > **New Policy**.
- In the **Create a profile** section:
- **Platform**: Select **macOS**.
- **Profile type**: Select **Templates**.
- **Template name**: Choose **Trusted certificate**.
- Click **Create**.
[See image.](#certificate-profile)
[]![Configure certificate](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/cert-trusted-cert.png)
- In the **Basics** section:
- **Name**: Enter a name for the custom file. For example, `Zscaler Root CA`.
- **Description**: (Optional) Enter a description.
[See image.](#upload-certificate)
[]![Upload certificate](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/cert-basics.png)
- In **Configuration Settings**:
- **Deployment channel**: Select **Device Channel**.
- **Certificate file**: Upload the certificate previously downloaded.
- Click **Next**.
[See image.](#certificate-configuration-settings)
[]![Save certificate profile](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/cert-config-settings.png)
- In the **Assignments** section, choose the users, groups, and devices for the profile.
- Click **Next**.
- In the **Review + create** section, review the summary, and click **Create**.
[]Zscaler Client Connector can intercept traffic locally using either Route-based Interception or Transparent Proxy-based Interception. Transparent Proxy-based Interception is a newer method introduced in Zscaler Client Connector version 4.5.1 and later for macOS. This feature uses the macOS Transparent Network Proxy Extension to intercept traffic. The TRPTunnel Network Extension (com.zscaler.zscaler.TRPTunnel) is used for traffic interception and application bypass and has the following benefits:
- No reliance on routing tables
- Better performance
- Zscaler Tunnel (Z-Tunnel) 2.0 compatibility with third-party VPN clients
- Removes the need for inbound firewall rules
To configure Transparent Proxy-based Traffic Interception, you must apply the following high-level steps:
- [Deploy a Configuration Profile to macOS Devices](#trp-deploy-config-profile)
- [Enable HTTP Tunneling Option in Internet & SaaS](#trp-http-tunneling)
- [Create a Forwarding Profile and Enable Z-Tunnel 2.0](#trp-create-forwarding)
- [Create an App Profile and Enable Transparent Proxy-based Traffic Interception](#trp-app-profile)
[]Follow these steps to import a preconfigured mobileconfig file into Microsoft Intune:
- In the Microsoft Intune admin center, go to **Devices** > **Configuration**.
- Go to **Create** > **New Policy**.
- In the **Create a profile** section:
- **Platform**: Select **macOS**.
- **Profile type**: Select **Templates**.
- **Template name**: Choose **Custom**.
[See image.](#trp-custom-profile)
[]![Upload mobile config file](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-macos-config-create-custom-1.png)
- Click **Create**.
- In the **Basics** section:
- **Name**: Enter a name for the custom file. For example, `Zscaler TRP Network Extension`.
- **Description**: (Optional) Enter a description.
[See image.](#trp-basics-section)
[]![Upload mobile config file](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/trp-basics.png)
- In **Configuration Settings**:
- **Deployment channel**: Select **Device channel**.
- **Configuration profile file**: [Download the mobileconfig file](/downloads/zscaler-client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune/deploying-zscaler-client-connector-microsoft-intune-macos/Zscaler-Sample-trp.mobileconfig) and upload it. You can copy and paste the file in a Text Editor and edit the values per your organization's requirements.
[See image.](#trp-upload-mobile-config-file)
[]![Upload mobile config file](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/trp-mobile-config_0.png)
In some scenarios, third-party VPNs can block connections from the Zscaler Client Connector utun interface or stop the Network Extension preventing Z-Tunnel 2.0 from connecting. In those situations, the values for the `proxyTCPOverT2` and `proxyUDPOverT2` keys must be changed to `true`.
- Click **Next**.
- In the **Assignments** tab, select the group assignments for which you want to deploy Zscaler Client Connector.
- Click **Next**.
[]
To enable HTTP tunneling option:
- In the Admin Portal, go to **Policies **>** Common Configuration **>** Advanced **>** Advanced Settings**.
- Disable the options **Block Tunneling to Non-HTTP/HTTPS Ports** and **Block Non-RFC Compliant HTTP Traffic on HTTP/HTTPS Ports**.
- []Create a [forwarding profile](/unified/configuring-forwarding-profiles-zscaler-client-connector).
- Select Z-Tunnel 2.0 when configuring a forwarding profile with Tunnel mode and the packet filter driver is enabled.
- Configure bypasses for Z-Tunnel 2.0 in [Zscaler Client Connector profile](/unified/configuring-zscaler-client-connector-app-profiles#mac-IP). To learn more, see [Best Practices for Adding Bypasses for Z-Tunnel 2.0](/unified/best-practices-adding-bypasses-z-tunnel-2-0).
- []In the Admin Portal, go to **Infrastructure** > **Connectors** > **Client**.
- Under Platform Settings, select **macOS**. Add a new macOS policy or edit an existing one.
- Go to **Traffic Steering** > **Advanced**.
- Enable the **Enable Transparent Proxy-based Traffic Interception**.
[See image.](#enable-trp-app-profile)
[]![Enable Transparent Proxy-based Traffic Interception](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-57940/enable-trp-app-profile.png)
[]You can configure the following tunnel parameters for Zscaler Client Connector with Microsoft Intune.
- [Prevent DNS Caching](#prevent-dns-caching)
- [Bring Zscaler Client Connector Window to the Foreground](#window-foreground)
- [Z-Tunnel 2.0 Quick Reconnect on Device Wakeup](#reconnect-tunnel-2)
[]This configuration setting is only supported with Route-based Traffic Interception and is not compatible with Transparent Proxy-based Traffic Interception.
You can use a property list (PLIST) file to set tunnel parameters, allowing DNS caching to be cleared from users’ devices. To configure tunnel parameters in the Microsoft Intune admin center:
- In the Microsoft Intune admin center, go to **Devices** > **Configuration**.
- Click **Create**.
- In the** Create a Profile** section:
- **Platform**: Select **macOS**.
- **Profile type**: Select **Templates**.
- **Template name**: Select **Custom**.
[See image.](#tunnel-param-create-profile)
[]![Custom profile](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-macos-config-create-custom-2.png)
- Click **Create**.
- In the **Basics** section:
- **Name**: Enter a name for the custom file.
- **Description**: (Optional) Enter a description.
- Click **Next**.
[See image.](#dns-cache-basic)
[]![Basics section](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-tunnel-params-basics-1.png)
- In the **Configuration settings** tab:
- **Custom configuration profile name**: Enter a profile name.
- **Deployment channel:** Select **Device channel**.
- **Configuration profile file**: Upload the following PLIST file. You can copy and paste the file in a Text Editor and upload it.
`<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
<key>tunnel-parameters</key>
<dict>
<key>clearDnsCacheOnT2Start</key>
<string>1</string>
</dict>
</dict>
</plist>`
If the** clearDnsCacheOnT2Start **parameter is enabled, on Tunnel restart, DNS caches are cleared from the device. Enter `1` to enable, or `0` to disable.
- Click **Next**.
[See image.](#dns-cache-config)
[]![Configuration Settings](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-tunnel-params-dns-cache-config.png)
- In the **Assignments** tab, select the group assignments for which you want to deploy Zscaler Client Connector.
- Click **Next**.
[]You can use a property list (PLIST) to set tunnel parameters, allowing you to bring the Zscaler Client Connector window to the foreground.
To bring Zscaler Client Connector window to the foreground:
- In the Microsoft Intune admin center, go to **Devices** > **Configuration**.
- Click **Create**.
If you already have an existing configuration profile to control a particular Zscaler Client Connector behavior (e.g., prevent DNS caching), select the profile and click **Edit**.
- In the** Create a Profile** section:
- **Platform**: Select **macOS**.
- **Profile type**: Select **Templates**.
- **Template name**: Select **Custom**.
- Click **Create**.
- In the **Basics** section:
- **Name**: Enter a name for the custom file.
- **Description**: (Optional) Enter a description.
[See image.](#basics-section-tunnel-2)
[]![Basics section](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-tunnel-params-basics-2.png)
- Click **Next**.
- In the **Configuration settings** tab:
- **Custom configuration profile name**: Enter a profile name.
- **Deployment channel:** Select **Device channel**.
- **Configuration profile file**: Upload the following property list (PLIST) file. You can copy and paste the file in a Text Editor and upload it.
`<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
<key>tunnel-parameters</key>
<dict>
<key>zccToForegroundDuringAuth</key>
<string>1</string>
</dict>
</dict>
</plist>`
If **zccToForegroundDuringAuth **parameter is enabled, it brings the Zscaler Client Connector window to the foreground during WebView-based authentication. Enter `1` to enable, or `0` to disable.
[See image.](#tunnel-window-foreground)
[]![Upload the PLIST file](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-tunnel-params-dns-window-foreground.png)
- Click **Next**.
- In the **Assignments** tab, select the group assignments for which you want to deploy Zscaler Client Connector.
- Click **Next**.
[]You can use a property list (PLIST) file to allow Zscaler Client Connector to immediately restart Zscaler Tunnel (Z-Tunnel) 2.0 on device wakeup.
To configure tunnel parameters in the Microsoft Intune admin center:
- In the Microsoft Intune admin center, go to **Devices** > **Configuration**.
- Click **Create**.
- In the** Create a Profile** section:
- **Platform**: Select **macOS**.
- **Profile type**: Select **Templates**.
- **Template name**: Select **Custom**.
- Click **Create**.
- In the **Basics** section:
- **Name**: Enter a name for the custom file.
- **Description**: (Optional) Enter a description.
[See image.](#basics-section-tunnel-quick)
[]![Custom settings](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-tunnel-params-basics-3.png)
- In the **Upload** section:
- **Preference Domain**: Enter `com.zscaler.tunnelparams`
- **Property List**: Upload the following PLIST file. You can copy and paste the file in a Text Editor and upload it:
`<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
<key>tunnel-parameters</key>
<dict>
<key>reconnectT2OnWake</key>
<string>1</string>
</dict>
</dict>
</plist>`
If the reconnectT2OnWake parameter is enabled, on device wakeup, Zscaler Client Connector immediately restarts Z-Tunnel to reduce the time it takes in tunnel establishment. Enter `1` to enable, or `0` to disable. If you have enabled [Reconnect Tunnel on System Wakeup](/unified/configuring-zscaler-client-connector-app-profiles#mac-general) feature in the App Profiles, you do not need to enable the reconnectT2OnWake parameter via an MDM.
[See image.](#create-profile-tunnel-2-plist)
[]![Upload section](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-tunnel-params-quick-reconnect.png)
- Click **Save**.
- In the **Scope** section, set **Targets**, **Limitations**, and **Exclusions** to bind the configuration profile to particular devices and users.
[]You can use a mobileconfig file to configure a custom VPN profile for ZPA VPN (for Legacy Apps) in the Microsoft Intune admin center:
- In the Microsoft Intune admin center, go to **Devices** > **Configuration**.
- Click **Create**.
- In the** Create a Profile** section:
- **Platform**: Select **macOS**.
- **Profile type**: Select **Templates**.
- **Template name**: Select **Custom**.
[See image.](#ZPA-VPN-Config-Profile-Custom)
[]![Custom profile](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-macos-config-create-custom-zpa-vpn.png)
- Click **Create**.
- In the **Basics** section:
- **Name**: Enter a name for the custom file.
- **Description**: (Optional) Enter a description.
- Click **Next**.
[See image.](#ZPA-VPN-Config-Profile-Custom-Basics)
[]![Basics section](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/zpa-vpn-basic.png)
- In the **Configuration settings** tab:
- **Custom configuration profile name**: Enter a profile name.
- **Deployment channel:** Select **Device channel**.
- **Configuration profile file**: [Download the ZscalerSampleMobileConfig file](/downloads/zscaler-client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune/deploying-zscaler-client-connector-microsoft-intune-macos/zpa-vpn.mobileconfig) and upload it.
- Click **Next**.
[See image.](#ZPA-VPN-Config-Profile-Custom-Config-Settings)
[]![Configuration Settings](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/zpa-vpn-config-profile.png)
- In the **Assignments** tab, select the group assignments for which you want to deploy Zscaler Client Connector.
- Click **Next**.
[See image.](#ZPA-VPN-Config-Profile-Custom-Assignments)
[]![Assignments section](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-55298/Intune-ZPA-VPN-Config-Profile-Create-Custom-Assignments.png)
[]Endpoint Data Loss Prevention (DLP) requires full disk access for proper operation. To create a DLP profile with Microsoft Intune to allow full disk access for Endpoint DLP:
- In the Microsoft Intune admin center, go to **Devices**.
- From the options, select **Configuration** > **Create** > **New Policy.**
[See image.](#endpoint-dlp-configuration-profile)
- In the **Create a profile** section:
- **Platform**: Select **macOS**.
- **Profile type**: Choose **Settings catalog**.
- Click **Create**.
[See image.](#endpoint-dlp-create-profile-macos)
- In the **Basics** section:
- **Name**: Enter a name for the settings catalog. For example, `Endpoint DLP Settings`.
- **Description (Optional)**: Enter a description.
[See image.](#endpoint-dlp-create-profile-basics)
- Click **Next**.
- In the **Configuration settings** section, click **Add settings**.
[See image.](#endpoint-dlp-add-config-settings)
-
Configure the following settings using the **Settings picker**:
- [System Policy All Files](#system-policy-all-files-settings-all-settings)
- [Notifications](#endpoint-dlp-add-notification-settings-all-settings)
- [System Extensions](#endpoint-dlp-add-system-extension-settings-all-settings)
- []In the **Browse by category** section, scroll down to **Privacy**.
- Select **Privacy Preferences Policy Control**.
- Under the **Setting name** section, expand **Services** > **System Policy All Files**.
- Select **System Policy All Files** and **Allowed**.
[See image.](#endpoint-dlp-system-policy-all-files-add)
- []In the **Browse by category** section, scroll down to **User Experience**.
- Select **Notifications**.
- Under the **Setting name** section, expand the **Notification Settings** section and select all of the options.
[See image.](#endpoint-dlp-add-notification-settings)
- []In the **Browse by category** section, scroll down to **System Configuration**.
- Select **System Extensions**.
- Under the **Setting name** section, check **Allowed System Extensions**, **Allowed Team Identifiers**, and **Removable System Extensions**.
[See image.](#endpoint-dlp-add-system-extension)
-
On the left-side navigation, configure the settings for the profiles you added in the previous step:
- [System Policy All Files](#endpoint-dlp-system-policy-left-screen)
- [Notifications](#endpoint-dlp-notification-left-screen)
- [System Extensions](#endpoint-dlp-privacy-preferences-left-screen)
- []Under **System Policy All Files**, click **Edit Instance**.
[See image.](#endpoint-dlp-system-policy-all-enter-details)
- In the **Privacy Preferences Policy Control** section, add the following three identifiers and configure settings for these identifiers.
| **Identifier** | `com.zscaler.zdp.pd` | `com.zscaler.zdp.esd` | `com.zscaler.zdp.at` |
| -------------- | -------------------- | --------------------- | -------------------- |
| **Identifier Type** | **Bundle ID** | **Bundle ID** | **Bundle ID** |
| **Code Requirement** | `identifier "com.zscaler.zdp.pd" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = PCBCQZJ7S7` | `identifier "com.zscaler.zdp.esd" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = PCBCQZJ7S7` | `identifier "com.zscaler.zep.at" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = PCBCQZJ7S7` |
| **App or Service** | **SystemPolicyAllFiles** | **SystemPolicyAllFiles** | **SystemPolicyAllFiles** |
| **Access** | **Allow** | **Allow** | **Allow** |
- []In the **Privacy Preferences Policy Control** section, under **System Extensions** section, configure the following settings:
- Under the **Allowed Team Identifiers** section, enter `PCBCQZJ7S7`.
- In the **Removable System Extensions** and the **Allowed System Extensions** sections, click the **Edit Instance** button.
- In the window that opens on the right:
- In the first text field, enter `com.zscaler.zep.at`.
- In the **Team Identifier** section, enter `PCBCQZJ7S7`.
[See image.](#endpoint-dlp-system-extension-enter)
- Click **Save**.
- []In the **Notifications** section, configure the settings under the **Notification Settings** section.
- Click **Edit instance**. In the window that opens on the right, add the following details:
- **Alert Type**: Select **Persistent Banner** from the drop-down menu.
- **Badges Enabled**: Toggle to **False**.
- **Bundle Identifier**: `com.zscaler.zdp.agent`
Leave all other settings as they are.
- Click **Save**.
[See image.](#endpoint-dlp-notification-settings-enter)
- Click **Next**.
- In the **Scope** tags section, add tags for particular devices and users.
- On the **Assignments** tab, select the group assignments for which you want to assign the app configuration policy, and then click **Next**.
- Click **Review and Create**.
- Click **Create**.
[See image.](#endpoint-dlp-review-create)
[]![Configure profile Endpoint DLP](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-macos-config-create-endpoint-dlp.png)
[]![Add settings for creating a profile](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-draft/ZSclientconnector-endpoint-dlp-full-disk-create-profile_0.png)
[]![Basic settings for creating a profile](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-draft/ZSclientconnector-endpoint-dlp-basics.png)
[]![Add settings for configuration ](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-draft/ZSclientconnector-endpoint-dlp-configuration-add-settings.png)
[]![Privacy settings system policy all files](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-draft/ZSclientconnector-endpoint-dlp-add-settings-system-policy.png)
[]![Add notifications settings](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-draft/ZSclientconnector-endpoint-dlp-add-settings-notifications.png)
[]![Add system extension settings](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-draft/ZSclientconnector-endpoint-dlp-add-system-extensions.png)
[]![Add system policy settings](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-draft/ZSclientconnector-endpoint-dlp-add-settings-system-policy-enter.png)
[]![System extension details](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-draft/ZSclientconnector-endpoint-dlp-system-extension-enter.png)
[]![Notification settings enter](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-draft/ZSclientconnector-endpoint-dlp-system-notifications-enter.png)
[]![Review and create](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-draft/ZSclientconnector-endpoint-dlp-review-and-create.png)
[]You can configure managed login items to prevent users from disabling Zscaler Client Connector on their own devices. To configure managed login items in the Microsoft Intune admin center:
- In the Microsoft Intune admin center, go to **Devices**.
- From the options, select **Configuration **>** Create **>** New Policy**.
[See image.](#managed-login-create)
[]![Configure new policy](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/managed-login-intune-macos-config-create.png)
- In the **Create a profile** section:
- **Platform**: Select **macOS**.
- **Profile type**: Choose **Settings catalog**.
- Click **Create**.
[See image.](#managed-login-settings-catalog)
[]![Create a profile](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/managed-login-create-profile-settings-catalog.png)
- In the **Basics** section:
- **Name**: Enter a name for the settings catalog. For example, `Start Client Connector on Login`.
- **Description (Optional)**: Enter a description.
[See image.](#managed-login-config-basics)
[]![Basics section](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/managed-login-intune-macos-config-basics.png)
- Click **Next**.
- In the **Configuration settings** section, click **Add settings**.
[See image.](#managed-login-config-add-settings)
[]![Configuration settings](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/managed-login-intune-macos-config-add-settings.png)
- In the **Settings picker**, under **Browse by category**, search for **Managed** **Login Item**.
- Select **Login **>** Service Managed - Managed Login Items**.
- Under **Setting name**, select the **Rules** checkbox.
[See image.](#managed-login-config-add-settings-picker)
[]![Settings picker](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/managed-login-intune-macos-config-add-settings-picker.png)
- On the left-side navigation, click **Edit Instance** to configure the settings for the rule you added in the previous step.
[See image.](#managed-login-add-settings-picker-edit-instance)
[]![Edit instance](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/managed-login-intune-macos-config-add-settings-picker-edit-instance.png)
- Under **Configure Instance**:
- **Rule Type**: Select `Bundle Identifier`.
- **Rule Value**: Enter `com.zscaler.tray`.
- **Team Identifier**: Enter `PCBCQZJ7S7`.
- Click **Save**.
[See image.](#managed-login-settings-picker-edit-instance-add-details)
[]![Add details for the instance](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/managed-login-intune-macos-config-add-settings-picker-edit-instance-add-details.png)
- Under **Rules**, click **Add**.
[See image.](#managed-login-add-settings-picker-add)
[]![Add more rules](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/managed-login-intune-macos-config-add-settings-picker-add.png)
- Configure each of the following additional rules under **Configure Instance**. Enter `PCBCQZJ7S7` for **Team Identifier**.
| **Rule Type** | **Rule Value** |
| ------------- | -------------- |
| Bundle Identifier Prefix | `com.zscaler` |
| Label | `com.zscaler.tray` |
| Label Prefix | `com.zscaler` |
- **Bundle Identifier**: The bundle ID.
- **Bundle Identifier Prefix**: A part of the bundle identifier reflecting the developer or organization.
- **Label**: A descriptive name for an app or an element in the app's UI or settings.
- **Label Prefix**: Used to group or categorize labels.
- **Team Identifier**: A unique identifier for the developer team or organization within the Apple ecosystem. Applies to all of the configured rules. Enter `PCBCQZJ7S7`.
- **Rule comment**: (Optional) Enter a comment for the rule.
[See image.](#managed-login-add-settings-picker-add-all-rules)
[]![All rules](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/managed-login-intune-macos-config-add-settings-picker-add-all-rules.png)
- Click **Save**.
- In the **Scope** tags section, add tags for particular devices and users.
- On the **Assignments** tab, select the group assignments for which you want to assign the app configuration policy, and then click **Next**.
- Click **Review and Create**.
- Click **Create**.
[]You must import a preconfigured mobileconfig file because Microsoft Intune doesn't support arrays in custom data types at this time.
To configure a custom settings profile in the Microsoft Intune admin center for the applications you want to bypass:
- [Step 1: Deploy a Configuration Profile to macOS Devices](#app-bypass-deploy-config-profile)
- [Deploy Application Bypass with Route-based Traffic Interception](#app-bypass-route-based)
- [Deploy Application Bypass with Transparent Proxy-based Traffic Interception](#app-bypass-trp-based)
- [Step 2: Enable Application Bypass in App Profiles](#app-bypass-enable)
[]Application Bypass is deployed using the VPN payload in a configuration profile and because the VPN payloads are different for Route-based Traffic Interception and Transparent Proxy-based Traffic Interception, the mobileconfig files differ based on traffic interception type in use.
You can use bundle identifiers for application identification. If your identifier has both a Team ID and a Bundle ID in it, enter them in the format <Team ID>.<Bundle ID>. For example: `<string>UBF8T346G9.com.microsoft.teams</string>`
Where:
- `UBF8T346G9` is the Team ID
- `com.microsoft.teams` is the Bundle ID
To enter multiple processes or applications, you can add all the bundle identifiers using an array. As an example, to bypass all Zoom processes, modify the downloaded mobileconfig file’s `BypassAppProcesses` key with the following:
`<key>BypassAppProcesses</key>
<array>
<string>BJ4HAAB9B3.us.zoom.xos</string>
<string>BJ4HAAB9B3.zoom.us.ZoomAudioDevice</string>
</array>`
[]You can use a mobileconfig file to enter the bundle identifier for the applications you want to bypass. To configure a custom VPN profile in the Microsoft Intune admin center:
- Go to **Devices**.
- From the options, select **Configuration**.
- Go to **Create** > **New Policy**.
- In the **Create a profile** section:
- **Platform**: Select **macOS**.
- **Profile type**: Select **Templates**.
- **Template name**: Choose **Custom**.
[See image.](#appbypass-route-create-profile)
[]![Create a profile and choose custom](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-macos-config-create-app-bypass-custom-0.png)
- Click **Create**.
- In the **Basics** section:
- **Name**: Enter a name for the custom file. For example, `Zscaler Client Connector App Bypasses`.
- **Description**: (Optional) Enter a description.
[See image.](#appbypass-route-basics)
[]![Fill the basics section and add a name and description](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-app-bypass-basics-1.png)
- Click **Next**.
- In the **Configuration settings** section:
- **Custom configuration profile name**: Enter the profile name.
- **Deployment channel**:** **Choose a channel for deployment.
- **Configuration profile file**: [Download the ZscalerSampleMobileConfig](/downloads/zscaler-client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune/deploying-zscaler-client-connector-microsoft-intune-macos/Intune_AppbypassRoutebased.mobileconfig). Upload the mobile config file. You can use this file as a starting template and edit the values in the VendorConfig section of the file based on your needs.
For **BypassAppProcesses**, enter the bundle identifier for the applications you want to bypass.
[See image.](#appbypass-route-configuration-settings)
[]![In configuration settings, upload the mobile config file](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-app-bypass-config-settings.png)
- Click **Next**.
- In the **Assignments** section, choose the users, groups, and devices for the profile.
[See image.](#appbypass-route-assignments)
[]![Set your groups in assignments](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-appbypass-route-assignments.png)
- Click **Next**.
- In the **Review + create** section, review the summary, and click **Create**.
[]In the Microsoft Intune admin center, go to **Computers** > **Configuration**.
- Go to **Devices**.
- From the options, select **Configuration**.
- Go to **Create** > **New Policy**.
- In the **Create a profile** section:
- **Platform**: Select **macOS**.
- **Profile type**: Select **Templates**.
- **Template name**: Choose **Custom**.
[See image.](#appbypass-create-profile)
[]![Create a profile and choose custom](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-macos-config-create-app-bypass-custom.png)
- Click **Create**.
- In the **Basics** section:
- **Name**: Enter a name for the custom file. For example, `Zscaler Client Connector App Bypasses`.
- **Description**: (Optional) Enter a description.
[See image.](#appbypass-basics)
[]![Fill the basics section and add a name and description](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-app-bypass-basics-2.png)
- Click **Next**.
- In the **Configuration settings** section:
- **Custom configuration profile name**: Enter the profile name.
- **Deployment channel**:** **Choose a channel for deployment.
- **Configuration profile file**: [Download the ZscalerSampleMobileConfig](/downloads/zscaler-client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune/deploying-zscaler-client-connector-microsoft-intune-macos/Zscaler-Sample-trp_0.mobileconfig). Upload the mobile config file. You can use this file as a starting template, and edit the values in the VendorConfig section of the file based on your needs.
For **BypassAppProcesses**, enter the bundle identifier for the applications you want to bypass.
[See image.](#appbypass-configuration-settings)
[]![In configuration settings, upload the mobile config file](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-app-bypass-config-settings-trp.png)
- Click **Next**.
- In the **Assignments** section, choose the users, groups, and devices for the profile.
[See image.](#appbypass-assignments)
[]![Set your groups in assignments](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/intune-appbypass-trp-assignments.png)
- Click **Next**.
- In the **Review + create** section, review the summary, and click **Create**.
- []In the Admin Portal, go to **Infrastructure **>** Connectors **>** Client.**
- Under Platform Settings, select **macOS**.
- Edit the respective profile from the list.
- Under **Traffic Steering**, go to **App and IP Bypass** > **Global Bypasses**.
- Enable the **Process-based Application Bypass** option.
[See image.](#process-based-app)
[]![Process-based Application Bypass](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-57940/process-based-app-bypass.png)