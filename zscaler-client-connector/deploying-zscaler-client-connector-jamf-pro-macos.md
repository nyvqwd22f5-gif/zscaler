# Deploying Zscaler Client Connector with Jamf Pro for macOS
Source: https://help.zscaler.com/zscaler-client-connector/deploying-zscaler-client-connector-jamf-pro-macos
PDF: https://help.zscaler.com/pdf/com/en/1450836.pdf

This guide is for admins only. If you are an end user, contact your organization’s administrator for deployment-related details.
With Jamf Pro, you can deploy Zscaler Client Connector for your macOS devices. Before deploying Zscaler Client Connector from the Jamf Pro Portal, download the .pkg file from the Zscaler Client Connector App Store first.
- [Step 1: Download the Zscaler Client Connector .pkg file](#download-pkg-file)
- [Step 2: Deploy Zscaler Client Connector from Jamf Pro](#deploy-client-connector-Jamf)
- [Step 3: (Optional) Configure a Custom Settings Profile](#configure-custom-settings)
- [Step 4: (Optional) Configure a Certificate Configuration Profile](#certificate-config-profile)
- [Step 5: (Optional) Configure a Transparent Proxy-based Traffic Interception](#transparent-proxy)
- [Step 6: (Optional) Configure Tunnel Parameters](#config-tunnel-param)
- [Step 7: (Optional) Configure a Custom VPN Profile for ZPA VPN (for Legacy Apps)](#custom-VPN-profile-ZPA-VPN-service)
- [Step 8: (Optional) Configure Full Disk Access for Endpoint DLP](#configure-full-disk-access)
- [Step 9: (Optional) Configure Managed Login Items](#managed-login-items)
- [Step 10: (Optional) Configure a Custom VPN Profile for Application Bypasses](#config-custom-vpn-application-bypass)
[]To deploy Zscaler Client Connector using the Jamf Pro Portal, you must obtain a .pkg file from the Zscaler Client Connector Portal.
To download the Zscaler Client Connector .pkg file:
- In the **Zscaler Client Connector Portal**, go to **Administration**.
- In the left-side navigation, go to **Client Connector App Store**.
- On the **New Releases **tab, select **macOS**.
- Download the .pkg file.
![pkg file](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-macos-doc-57940/app-store-admin-new-releases-macos-pkg.png)
[]To deploy Zscaler Client Connector on your macOS devices from the Jamf Pro Portal:
- In the Jamf Pro Portal, go to **Settings **>** Computer Management **>** Packages**​​​​​​.
- Under the **General** section, click **Choose File** to upload the .pkg file.
[See image.](#settings-packages)
[]![Package settings in Jamf Pro portal](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-jamf-pro-macos/zclientconnector-jamf-settings-packages.png)
- Click **Save**.
- In the left-side navigation, go to **Computers** > **Policies**.
- In the **Policies** window, click **New**.
[See image.](#policies-new)
[]![Add a new policy in policies section](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-jamf-pro-macos/zclientconnector-jamf-policies-new.png)
- In the **General** section, choose the **Trigger** events and **Execution frequency** as needed in your environment.
[See image.](#general)
[]![General section in policies](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-jamf-pro-macos/zclientconnector-jamf-policies-general.png)
- Click **Save**.
- In the left-side navigation, select **Packages**, and click **Configure**.
[See image.](#configure-packages)
[]![Packages section under new policy](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-jamf-pro-macos/zclientconnector-jamf-packages-config.png)
- Click **Add**, and choose the .pkg file uploaded previously.
- Click **Save**.
- On the **Scope** tab, assign the .pkg to the applicable devices.
[See image.](#scope)
[]![Scope section under policies](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-jamf-pro-macos/zclientconnector-jamf-scope.png)
- Click **Save**.
To reinstall the same version of Zscaler Client Connector for a specific device or user, go to the computer's history and select **Flush All** for all the **Policy Logs**. Alternatively, you can delete the device or user from Jamf Pro and reinstall via the client.
[]You can use a PLIST file to set values for various configuration keys in the Jamf Pro Portal. To configure a custom settings profile in the Jamf Pro Portal:
- In the Jamf Pro Portal, go to **Computers** > **Configuration Profiles**.
- Click **Application & Custom Settings** to expand the section.
- Select **Upload**,** **then click** Add (+)**.
[See image.](#configuration-profiles-upload)
[]![Application and Custom Settings in Configuration Profiles](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-jamf-pro-macos/zclientconnector-jamf-custom-settings-config-profiles.png?1680810643)
- In the **Upload** section:
- **Preference Domain**: Enter `com.zscaler.installparams`
- **Property List**: Enter the following PLIST file and edit [Zscaler configuration parameters](/zscaler-client-connector/supported-parameters-zscaler-client-connector-macos) and their corresponding values per your organization's needs.
`<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
<key>installation-parameters</key>
<dict>
<key>cloudName</key>
<string>zscalertwo</string>
<key>deviceToken</key>
<string></string>
<key>hideAppUIOnLaunch</key>
<string>0</string>
<key>launchTray</key>
<string>1</string>
<key>policyToken</key>
<string> <policy token from app></string>
<key>strictEnforcement</key>
<string>0</string>
<key>userDomain</key>
<string>zexample.com</string>
<key>externalRedirect</key>
<string>false</string>
<key>externalDeviceId</key>
<string>device123</string>
<key>userName</key>
<string>test11</string>
<key>enableFips</key>
<string>0</string>
</dict>
</dict>
</plist>`
[See image.](#plist-file)
[]![Property list file](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-jamf-pro-macos/zclientconnector-jamf-custom-settings-upload-plist.png)
- In the **Scope** section, set **Targets**, **Limitations**, and **Exclusions** to bind the configuration profile to particular devices and users.
[]If you use Zscaler Internet Access (ZIA) and you want to perform SSL inspection, you must configure a certificate profile to push the Certificate Authority (CA) certificate required for SSL inspection. You can use the default Zscaler CA certificate or a custom Root or Intermediate CA certificate. To learn more, see [Choosing the CA Certificate for SSL Inspection](/zia/choosing-ca-certificate-ssl-inspection) and [Certificate Pinning and SSL Inspection](/zia/certificate-pinning-and-ssl-inspection).
To configure a certificate configuration profile:
- [(Optional) Download the Zscaler CA Certificate.](#download-zscaler-certificate)
- [Configure the Certificate Profile.](#configure-cert-profile)
[]To download the certificate:
- In the ZIA Admin Portal, go to **Policy > SSL Inspection **>** Intermediate CA Certificates**.
-
Click the **Edit** icon corresponding to the Zscaler Intermediate CA Certificate.
The **View Zscaler Intermediate CA Certificate** window appears.
-
In the **View Zscaler Intermediate CA Certificate** window, under the **Root Certificate** field, click **Download**.
The root certificate is downloaded as a ZIP file.
- Navigate to the ZscalerRootCerts.zip file and unzip it and rename the file extension to .cer.
[]To configure the profile:
- In the Jamf Pro Portal, go to **Computers** > **Configuration Profiles**.
- Select **New** and under **General**, enter a** **name for the configuration profile.
- Select **Certificate** and click **Configure**.
[See image.](#certificate-profile)
[]![Configure certificate](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-57940/cert-profile-create-profile.png)
- Enter a name for the certificate.
- In the **Select Certificate** option, click **Upload**.
- Click **Upload** to upload the certificate previously downloaded.
[See image.](#upload-certificate)
[]![Upload certificate](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-57940/cert-profile-create-profile-upload.png)
- Enable the **Allow all apps** **access** option and **Save** the profile.
[See image.](#save-certificate-profile)
[]![Save certificate profile](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-57940/cert-profile-create-profile-save.png)
- In the **Scope** section, set **Targets**, **Limitations**, and **Exclusions** to bind the configuration profile to particular devices and users.
[]Zscaler Client Connector can intercept traffic locally using either Route-based Interception or Transparent Proxy-based Interception. Transparent Proxy-based Interception is a newer method introduced in Zscaler Client Connector version 4.5.1 and later for macOS. This feature uses the macOS Transparent Network Proxy Extension to intercept traffic. The TRPTunnel Network Extension (com.zscaler.zscaler.TRPTunnel) is used for traffic interception and application bypass and has the following benefits:
- No reliance on routing tables
- Better performance
- Zscaler Tunnel (Z-Tunnel) 2.0 compatibility with third-party VPN clients
- Removes the need for inbound firewall rules
To configure Transparent Proxy-based Traffic Interception, you must apply the following high-level steps:
- [Deploy a Configuration Profile to macOS Devices](#trp-deploy-config-profile)
- [Enable HTTP Tunneling Option in ZIA](#trp-http-tunneling)
- [Create a Forwarding Profile and Enable Z-Tunnel 2.0](#trp-create-forwarding)
- [Create an App Profile and Enable Transparent Proxy-based Traffic Interception](#trp-app-profile)
[]Choose either of the following two options to create a configuration profile to deploy Transparent Proxy-based Traffic Interception. If you also need to deploy Application Bypass, use the **Import a Preconfigured mobileconfig File Into Jamf** option because since Jamf Pro doesn't support arrays in custom data types at this time.
- [Manually Create a Configuration Profile in Jamf Pro](#trp-deploy-manually-create-config-profile)
- [Import a Preconfigured mobileconfig File Into Jamf Pro](#trp-deploy-import-mobileconfig)
- []In the Jamf Pro Portal, go to **Computers** > **Configuration Profiles**.
- From the left-side navigation, go to **General**, click **New** and enter a name for the configuration profile.
- Go to **System Extensions** and click **Configure**.
[See image.](#trp-config-system-ext)
[]![Configure system extensions](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-57940/deploy-config-profile-system-extension-config_0.png)
- In the **System Extensions** section:
- **Display Name**: Enter `Zscaler TRP Network Extension`.
- **System Extension type**: Select **Non-removable system extensions from UI **to prevent users from disabling Zscaler Client Connector forwarding.
- **Team Identifier**: Enter `PCBCQZJ7S7`.
- **Non-removable system extensions from UI**: Click **Add (+)** and enter `com.zscaler.zscaler.TRPTunnel`.
- Click **Save**.
[See image.](#trp-config-system-ext-settings)
[]![Settings for system extension](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-57940/deploy-config-profile-system-extension-settings.png)
- From the left-side navigation, go to **VPN** and click **Configure**.
[See image.](#trp-config-vpn)
[]![Configure VPN](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-57940/deploy-config-profile-system-config-vpn.png)
- In the **VPN** section:
- **Connection Name**: Enter `Zscaler TRP Tunnel`.
- **VPN Type**: Select **VPN**.
- **Connection Type**: Select **Custom SSL**.
- **Identifier**: Enter `com.zscaler.zscaler`
- **Server**: Enter `Zscaler server`.
- **Provider Bundle Identifier**: Enter `com.zscaler.zscaler.TRPTunnel`
[See image.](#trp-config-vpn-settings)
[]![VPN settings](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-57940/deploy-config-profile-system-config-vpn-settings-trptunnel.png)
- Under **Custom Data**, enter the following **Key** and **Value** fields:
- Enter Key `proxyTCPOverT2` and set Value as `false`.
- Enter Key `proxyUDPOverT2` and set Value as `false`.
In some scenarios, third-party VPNs can block connections from the Zscaler Client Connector utun interface or stop the Network Extension preventing Z-Tunnel 2.0 from connecting. In those situations, the values for the `proxyTCPOverT2` and `proxyUDPOverT2` keys must be changed to `true`.
- **Provider Type**: Select **App-proxy**.
- **Provider Designated Requirement**: Enter `identifier "com.zscaler.zscaler.TRPTunnel" and anchor apple generic`.
[See image.](#trp-config-vpn-settings-1)
[]![VPN Settings](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-57940/deploy-config-profile-system-config-vpn-settings.png)
- Select the checkbox for **Prohibit users from disabling on-demand VPN settings**
- Click** Save.**
- In the **Scope** section, set **Targets**, **Limitations**, and **Exclusions** to bind the configuration profile to particular devices and users.
- []In the Jamf Pro Portal, go to **Computers** > **Configuration Profiles**.
- [Download the mobileconfig file](/downloads/zscaler-client-connector/downloading-deployment/deploying-zscaler-client-connector-jamf-pro/deploying-zscaler-client-connector-jamf-pro-macos/Zscaler-Sample-trp.mobileconfig).
- Click **Upload** > **Choose File** and upload the mobileconfig file.
[See image.](#upload-mobile-config-file)
[]![Upload mobile config file](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-57940/deploy-download-mobile-config.png)
- The **General**, **VPN**, and **System Extensions** sections are auto-populated.
- In the **Scope** section, set **Targets**, **Limitations**, and **Exclusions** to bind the configuration profile to particular devices and users.
[]
To enable HTTP tunneling option:
- Go to **ZIA Admin Portal** > **Administration**.
- Click **Advanced Settings**.
- Disable the options **Block Tunneling to Non-HTTP/HTTPS Ports** and **Block Non-RFC Compliant HTTP Traffic on HTTP/HTTPS Ports**.
- []Create a [forwarding profile](/zscaler-client-connector/configuring-forwarding-profiles-zscaler-client-connector).
- Select Z-Tunnel 2.0 when configuring a forwarding profile with Tunnel mode and the packet filter driver is enabled.
- Configure bypasses for Z-Tunnel 2.0 in [Zscaler Client Connector profile](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles#mac-IP). To learn more, see [Best Practices for Adding Bypasses for Z-Tunnel 2.0](/zscaler-client-connector/best-practices-adding-bypasses-z-tunnel-2.0).
- []In the Zscaler Client Connector Portal, from the left-side navigation, click **App Profiles** and select **macOS**. Add a new macOS policy or edit an existing one.
- Go to **Traffic Steering** > **Advanced**.
- Enable the **Enable Transparent Proxy-based Traffic Interception**.
[See image.](#enable-trp-app-profile)
[]![Enable Transparent Proxy-based Traffic Interception](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-57940/enable-trp-app-profile.png)
[]You can configure the following tunnel parameters for Zscaler Client Connector with Jamf Pro.
- [Prevent DNS Caching](#prevent-dns-caching)
- [Bring Zscaler Client Connector Window to the Foreground](#window-foreground)
- [Z-Tunnel 2.0 Quick Reconnect on Device Wakeup](#reconnect-tunnel-2)
[]This configuration setting is only supported with Route-based Traffic Interception and is not compatible with Transparent Proxy-based Traffic Interception.
You can use a property list (PLIST) file to set tunnel parameters, allowing DNS caching to be cleared from users’ devices. To configure tunnel parameters in the Jamf Pro Portal:
- In the Jamf Pro Portal, go to **Computers** > **Configuration Profiles**.
- In **General**, select **New** to create a new profile and enter a name for the profile.
- Click **Application & Custom Settings** to expand the section and click **Upload **>** Add**.
[See image.](#prevent-dns-caching-config-profiles)
[]![Configuration profiles for dns caching](/downloads/tech-pubs-drafts/client-connector-draft-articles/saira-testing/Jamf-pro-macOS-tunnel-parameters-config-profiles.png)
- In the **Upload** section:
- **Preference Domain**: Enter `com.zscaler.tunnelparams`
- **Property List**: Add the following PLIST:
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
[See image.](#prevent-dns-caching-config-profiles-upload)
[]![Upload the Plist file](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-57940/dns-cache.png)
- Click **Save**.
- In the **Scope** section, set **Targets**, **Limitations**, and **Exclusions** to bind the configuration profile to particular devices and users.
If you are already logged in to Zscaler Client Connector, exit and relaunch the app or click **Restart Service** in the More window of the app.
[]You can use a property list (PLIST) to set tunnel parameters, allowing you to bring the Zscaler Client Connector window to the foreground.
To bring Zscaler Client Connector window to the foreground:
- In the Jamf Pro Portal, go to **Computers** > **Configuration Profiles**.
If you already have an existing configuration profile to control a particular Zscaler Client Connector behavior (e.g., prevent DNS caching), select the profile and click **Edit**.
- Expand the **Application & Custom Settings** section and click **Upload **>** Add**.
- In the **Upload** section:
- **Preference Domain**: Enter `com.zscaler.tunnelparams`
- **Property List**: Add the following PLIST:
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
The following image combines the PLIST for both **clearDnsCacheOnT2Start** and** zccToForegroundDuringAuth **parameters. You can configure settings for both parameters together if you haven't already configured settings for **clearDnsCacheOnT2Start**.
[See image.](#bring-zcc-to-foreground)
[]![Bring Zscaler Client Connector to Foreground](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-57940/zcc-to-foreground.png)
- Click **Save**.
- In the **Scope** section, set **Targets**, **Limitations**, and **Exclusions** to bind the configuration profile to particular devices and users.
If you are already logged in to Zscaler Client Connector, exit and relaunch the app or click Restart Service in the More window of the app.
[]You can use a property list (PLIST) file to allow Zscaler Client Connector to immediately restart Zscaler Tunnel (Z-Tunnel) 2.0 on device wakeup. To configure tunnel parameters in the Jamf Pro Portal:
- In the Jamf Pro Portal, go to **Computers** > **Configuration Profiles**.
- In **General**, select **New** to create a new profile and enter a name for the profile.
- Expand the **Application & Custom Settings** section and click **Upload **>** Add**.
[See image.](#create-profile-tunnel-2)
[]![config profile for reconnect tunnel 2](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-58770/tunnel-2-wake-up-config-profile_0.png)
- In the **Upload** section:
- **Preference Domain**: Enter `com.zscaler.tunnelparams`
- **Property List**: Add the following PLIST:
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
[See image.](#create-profile-tunnel-2-plist)
[]![Upload section](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-58770/tunnel-2-wake-up-config-profile-plist.png)
If the **reconnectT2OnWake** parameter is enabled, on device wakeup, Zscaler Client Connector immediately restarts Z-Tunnel to reduce the time it takes in tunnel establishment. Enter `1` to enable, or `0` to disable.
- Click **Save**.
- In the **Scope** section, set **Targets**, **Limitations**, and **Exclusions** to bind the configuration profile to particular devices and users.
[]This configuration setting is only supported with Route-based Traffic Interception and is not compatible with Transparent Proxy-based Traffic Interception.
You can use a property list (PLIST) file to configure a custom VPN profile for [ZPA VPN (for Legacy Apps)](/zpa/about-network-connectors) in the Jamf Pro Portal:
- In the Jamf Pro Portal, go to **Computers** > **Configuration Profiles**.
- In **General**, select **New** to create a new profile and enter a name for the profile.
- From the left-side navigation, go to **VPN** and click **Configure**.
[See image.](#pkt-config-vpn-settings-1)
[]![VPN Configure](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-57940/ZPA-VPN-config-profile-system-config-vpn-pkt.png)
- In the **VPN** section:
- **Connection Name**: Enter `Zscaler ZPA VPN`.
- **VPN Type**: Select **VPN**.
- **Connection Type**: Select **Custom SSL**.
- **Identifier**: Enter `com.zscaler.zscaler`
- **Server**: Enter `Zscaler server`.
- **Provider Bundle Identifier**: Enter `com.zscaler.zscaler.pktfilter`
[See image.](#pkt-config-vpn-settings)
[]![VPN settings](/downloads/zscaler-client-connector/downloading-deployment/deploying-zscaler-client-connector-jamf-pro/deploying-zscaler-client-connector-jamf-pro-macos/deploy-config-profile-system-extension-vpn-config-pkt.png)
- **Provider Type**: Select **Packet-tunnel**.
- **Provider Designated Requirement**: Enter `identifier "com.zscaler.zscaler.pktfilter" and anchor apple generic`.
- **Prohibit users from disabling on-demand VPN settings**: Select this checkbox.
[See image.](#pkt-config-vpn-settings-2)
[]![VPN Settings](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-57940/ZPA-VPN-config-profile-system-config-vpn-pkt-2.png)
- To ensure a seamless user experience, configure the system extension in Jamf Pro and activate it. To learn more, see [Configuration Profile for Auto Approval of Zscaler System Extension](/zscaler-client-connector/blocking-lan-access-and-configuring-zscaler-client-connector-firewall-macos#configuration-profile-auto-approval-Zscaler-system-extension).
- Click **Save**.
- In the **Scope** section, set **Targets**, **Limitations**, and **Exclusions** to bind the configuration profile to particular devices and users.
[]Zscaler Endpoint Data Loss Prevention (DLP) requires full disk access for proper operation. Choose either of the following two options to create a DLP profile with Jamf Pro Portal to allow full disk access.
- [Manually Create a Configuration Profile in Jamf Pro](#manually-create-config-profile-full-disk)
- [Import a Preconfigured mobileconfig File Into Jamf](#import-preconfigured-mobileconfig-file)
[]To configure a full disk access for Endpoint DLP in the Jamf Pro Portal:
- [a. Create a general profile.](#create-general-profiles)
- [b. Configure privacy preferences for policy control.](#configure-privacy-preferences-policy)
- [c. Configure notification settings.](#configure-notification-settings)
- [d. Configure permissions for system extensions.](#configure-permissions-system-extension)
- []Go to **Computers** > **Configuration Profiles**.
- Click **New**.
- For the **General** section:
- **Name**: Enter `ZDP`.
- **Description**: (Optional) Enter a brief explanation of the profile.
- Click **Save**.
[See image.](#new-macOS-config-profile)
[]![New macOS configuration profiles](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-49960/full-disk-access-config-profiles.png)
- []On the Options tab, click the **Privacy Preferences Policy Control** > **Configure**.
- Click **Add (+)** (located in the upper right-hand corner of the pane) to add a new app to the **Privacy Preferences** section. Repeat this step for the three identifiers listed in the following table in the **App Access** section:
| **Identifier** | `com.zscaler.zdp.pd` | `com.zscaler.zdp.esd` | `com.zscaler.zep.at` |
| -------------- | -------------------- | --------------------- | -------------------- |
| **Identifier Type** | **Bundle ID** | **Bundle ID** | **Bundle ID** |
| **Code Requirement** | `identifier "com.zscaler.zdp.pd" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = PCBCQZJ7S7` | `identifier "com.zscaler.zdp.esd" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = PCBCQZJ7S7` | `identifier "com.zscaler.zep.at" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = PCBCQZJ7S7` |
| **App or Service** | **SystemPolicyAllFiles** | **SystemPolicyAllFiles** | **SystemPolicyAllFiles** |
| **Access** | **Allow** | **Allow** | **Allow** |
- Click **Save**.
[See image.](#full-disk-app-access-privacy-control)
[]![Privacy preferences policy control](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-49960/full-disk-access-privacy-preferences.png)
- []On the Options tab, click the **Privacy Preferences Policy Control** > **Configure**.
- From the left-side navigation, click the **Notifications** section.
- Click **Add** to add a new notification.
- **App Name**: Enter `zdpagent`.
- **Bundle ID**: Enter `com.zscaler.zdp.agent`.
-
For **Notifications**, select **Enable**.
- **Banner alert type**: Select **Persistent** from the drop-down menu.
- **Notifications in Notification Center**: Select **Display** from the drop-down menu.
- **Play sound for notifications**: Select **Enable**.
[See image.](#full-disk-access-notifications)
[]![Notification settings](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-49960/full-disk-access-notifications.png)
[]For Endpoint DLP to function correctly, you must configure permissions for System Extensions.
- From the left-side navigation, click **System Extensions** > **Configure**.
- In the **Allowed Team IDs and System Extensions** section:
- **Display Name**: Enter `PCBCQZJ7S7`.
- **System Extension Types**: Select **Allowed System Extensions**.
- **Team Identifier**: Enter `PCBCQZJ7S7`.
- In the **Allowed System Extensions** section, click **Add (+)** and enter `com.zscaler.zep.at`.
- Click **Save**.
- To add a removable System Extensions configuration, click **Add (+)** next to the **Allowed Team IDs and System Extensions**.
- In the **Allowed Team IDs and System Extensions** section:
- **Display Name**: Enter `PCBCQZJ7S7`.
- **System Extension Types**: Select **Removable System Extensions**.
- **Team Identifier**: Enter `PCBCQZJ7S7`.
- In the **Removable System Extensions** section, Click **Add (+)** and enter `com.zscaler.zep.at`.
[See image.](#full-disk-access-system-extensions)
[]![System extensions](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-49960/full-disk-access-system-extension.png)
- Click **Save**.
- []In the Jamf Pro Portal, go to **Computers** > **Configuration Profiles**.
- [Download the ZDP.mobileconfig file.](/downloads/zscaler-client-connector/downloading-deployment/deploying-zscaler-client-connector-jamf-pro-macos/ZDP-mobileconfig.mobileconfig)
You must remove any existing ZDP MDM profiles before uploading a new profile.
- Click the **Upload button** > **Choose File** and upload the **ZDP.mobileconfig** file.
[See image.](#full-disk-access-upload-mobileconfig)
[]![Upload mobileconfig file](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-49960/full-disk-access-upload-mobileconfig.png)
- Click **Save.**
[See image.](#full-disk-access-mobileconfig-file)
[]![Configuration profile screen](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-49960/full-disk-access-new-config-profile.png)
[]You can configure managed login items to prevent users from disabling Zscaler Client Connector on their own devices. To configure managed login items in the Jamf Pro Portal:
- In the Jamf Pro Portal, go to **Computers** > **Configuration Profiles**.
- Select **Managed Login Items**.
[See image.](#managed-login-items-config)
[]![Managed Login Items Configuration](/downloads/tech-pubs-drafts/client-connector-draft-articles/saira-testing/Jamf-Pro-macOS-Managed-Login-Items.png)
- Click **Add** for each of the following **Rule Types** and **Rule Values**:
| **Rule Type** | **Rule Value** |
| ------------- | -------------- |
| Bundle Identifier | `com.zscaler.tray` |
| Bundle Identifier Prefix | `com.zscaler` |
| Label | `com.zscaler.tray` |
| Label Prefix | `com.zscaler` |
- **Bundle Identifier**: The bundle ID.
- **Bundle Identifier Prefix**: A part of the bundle identifier reflecting the developer or organization.
- **Label**: A descriptive name for an app or an element in the app's UI or settings.
- **Label Prefix**: Used to group or categorize labels.
- **Team Identifier**: A unique identifier for the developer team or organization within the Apple ecosystem. Applies to all of the configured rules. Enter `PCBCQZJ7S7`.
- **Rule comment**: (Optional) Enter a comment for the rule.
[See image.](#managed-login-items-rule)
[]![Example of Rule Type and Rule Value](/downloads/tech-pubs-drafts/client-connector-draft-articles/saira-testing/Jamf-Pro-macOS-Managed-Login-Items-Rule-Example.png)
- Click **Save**.
[See image.](#managed-login-items-rules-edit)
[]![Click Edit](/downloads/zscaler-client-connector/downloading-deployment/deploying-zscaler-client-connector-jamf-pro-macos/Jamf-Pro-macOS-Managed-Login-Items-Rules-Save.png)
- In the **Scope** section, set **Targets**, **Limitations**, and **Exclusions** to bind the configuration profile to particular devices and users.
[]You must import a preconfigured mobileconfig file because Jamf Pro doesn't support arrays in custom data types at this time.
To configure a custom settings profile in the Jamf Pro Portal for the applications you want to bypass:
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
[]In the Jamf Pro Portal, go to **Computers** > **Configuration Profiles**.
- Select **Upload**.
- Upload the mobile config file.
- Use the [ZscalerSampleMobileConfig](/downloads/zscaler-client-connector/downloading-deployment/deploying-zscaler-client-connector-jamf-pro-macos/ZscalerSampleMobileConfigApp_0.mobileconfig) file as a starting template, and edit the values in the `<VendorConfig>` section of the file based on your needs.
- To ensure a seamless user experience, configure the system extension in Jamf Pro and activate it. To learn more, see [Configuration Profile for Auto Approval of Zscaler System Extension](/zscaler-client-connector/blocking-lan-access-and-configuring-zscaler-client-connector-firewall-macos#configuration-profile-auto-approval-Zscaler-system-extension).
- In the **Scope** section, set **Targets**, **Limitations**, and **Exclusions** to bind the configuration profile to particular devices and users.
[]In the Jamf Pro Portal, go to **Computers** > **Configuration Profiles**.
- Select **Upload**.
- Upload the mobile config file.
- Use the [ZscalerSampleMobileConfig](/downloads/zscaler-client-connector/downloading-deployment/deploying-zscaler-client-connector-jamf-pro/deploying-zscaler-client-connector-jamf-pro-macos/Zscaler-Sample-trp_0.mobileconfig) file as a starting template, and edit the values in the `<VendorConfig>` section of the file based on your needs.
- To ensure a seamless user experience, configure the system extension in Jamf Pro and activate it. To learn more, see [Configuration Profile for Auto Approval of Zscaler System Extension](/zscaler-client-connector/blocking-lan-access-and-configuring-zscaler-client-connector-firewall-macos#configuration-profile-auto-approval-Zscaler-system-extension).
- In the **Scope** section, set **Targets**, **Limitations**, and **Exclusions** to bind the configuration profile to particular devices and users.
- []In the Zscaler Client Connector Portal, go to **App Profiles** > **macOS**.
- Edit the respective profile from the list.
- Under **Traffic Steering**, go to **App and IP Bypass** > **Global Bypasses**.
- Enable the **Process-based Application Bypass** option.
[See image.](#process-based-app)
[]![Process-based Application Bypass](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-jamf-pro-macos-doc-57940/process-based-app-bypass.png)