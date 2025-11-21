# Deploying Zscaler Client Connector with Microsoft Intune for iOS
Source: https://help.zscaler.com/zscaler-client-connector/deploying-zscaler-client-connector-microsoft-intune-ios
PDF: https://help.zscaler.com/pdf/com/en/1357451.pdf

This guide is for admins only. If you are an end user, contact your organization’s administrator for deployment-related details.
With Microsoft Intune, you can deploy Zscaler Client Connector for your iOS devices and configure a custom settings profile. The version used for the following steps is Microsoft Intune Service release version 2048.
- [Step 1: Deploy Zscaler Client Connector from the Microsoft Intune Portal](#deploying-zscaler-client-connector-from-intune)
- [Step 2: Configure Required Policy Settings](#configuring-required-policy-settings)
- [Step 3: (Optional) Configure a Certificate Configuration Profile](#configure-cert-config-profile)
- [Step 4: (Optional) Configure Per-App VPN Access to a Specific Application](#configure-access-specific-application)
- [Step 5: (Optional) Configure the Microsoft Enterprise SSO Plug-In](#configure-MS-enterprise-SSO-plugin)
- [Step 6: (Optional) Configure Additional Strict Enforcement Settings](#configure-strict-enforcement-settings)
[]To deploy Zscaler Client Connector using the Microsoft Intune portal:
- In the Microsoft Intune portal, from the left-side navigation, select **Apps**.
-
Click **iOS/iPadOS apps**, and then click **Add**.
[See image.](#add-app)
-
From the **App type** drop-down menu, select **iOS store app**, and then click **Select**.
[See image.](#ios-store-app)
- To add the app from the iOS store app:
- On the **App information **tab, click **Search the App Store**.
-
Search for and select **Zscaler Client Connector**, and then click **Select**.
[See image.](#select-zcc-app)
Zscaler Client Connector details are automatically populated.
- In the **Minimum operating system** field, select **iOS 9.0**.
-
In the **Show this as a featured app in the Company Portal** field, select **Yes**, and then click **Next**.
[See image.](#add-app-info)
- On the **Assignments **tab, select the group assignments for which you want to deploy Zscaler Client Connector, and then click **Next**.
-
(Optional) Click **Included** and edit the **Assignment Settings**:
- To automatically uninstall Zscaler Client Connector if the device is removed from Intune, select **Yes** for **Uninstall on device removal**.
- To ensure that the user can’t remove Zscaler Client Connector from the device, select **No** for **Install as removable**.
[See image.](#edit-assignment)
- On the **Review + create** tab, review the values and settings, and then click **Create**.
[]You must configure custom policy settings in the Microsoft Intune portal using either a device configuration profile or an app configuration policy.
Zscaler recommends that you use a device configuration profile to configure custom policy settings, but you can use an app configuration policy instead. If you use a device posture check of the **Ownership Variable**, you can use a device configuration profile for all settings except the ownership setting (which you must set using an app configuration policy). To learn more about setting up a device posture, see [Configuring Device Posture Profiles](/zscaler-client-connector/configuring-device-posture-profiles).
- [Configure a device configuration policy for On-demand VPN (recommended).](#configure-device-configuration-profile)
- [Configure an app configuration policy.](#add-app-configuration-policy)
[]
To configure a device configuration policy for On-demand VPN:
- In the Microsoft Intune portal, from the left-side navigation, click **Devices**.
-
Select **Devices > Configuration**.
[See image.](#devices-config-profiles)
-
Click **Create **and select** New Policy**.
[See image.](#create-policy)
-
In the **Create a profile** section:
- **Platform**: Select **iOS/iPadOS**.
- **Profile type**: Select **Templates**.
- **Template name**: Select **VPN**.
[See image.](#create-a-profile-details)
- Click **Create**.
-
In the **Basics** section:
- **Name**: Enter a name.
- **Description**: (Optional) Enter a description.
[See image.](#vpn-basics-section)
- Click **Next**.
-
On the **Configuration settings** tab, for **Connection type**, select **Zscaler**.
[See image.](#configuration-settings)
-
Enter the following parameters:
- **Connection name**: The label for the profile.
- **Custom domain name**: Enter your Zscaler tenant domain. This allows you to configure the user domain so that users can skip the Zscaler Client Connector enrollment page and go directly to the single sign-on (SSO) login page.
-
**Enable strict enforcement**: Enabling this option blocks internet traffic before a user enrolls in Zscaler Client Connector when:
- The user has not logged in after a new install.
- The user logs in and then logs out.
- An administrator removes the device from the Zscaler Client Connector Portal.
If you enable Strict Enforcement, you must use the policyToken configuration key. Excluded URLs must also be defined in a device configuration policy or excludeList in an app configuration policy. There are also additional configuration settings required. To learn more, see [Configure Additional Strict Enforcement Settings](#configure-strict-enforcement-settings).
- **Organization’s cloud name**: The name of the cloud where your organization is provisioned. For example, if your cloud name is zscalertwo.net, enter `zscalertwo`. To learn more, see [What Is My Cloud Name for ZIA?](/zia/what-my-cloud-name-zia)
- **Excluded URLs**: Enter any URLs you want to bypass. For example, enter your identity provider (IdP), MDM (Mobile Device Management) server, or anything else the user should have access to before enrollment. If you use the Zscaler Private Access (ZPA) service, you must enter `authsp.prod.zpath.net`. For a list of additional Intune requirements, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/mem/intune/fundamentals/intune-endpoints?tabs=north-america).
[See image.](#config-settings-vpn)
-
(Optional) Enter [Zscaler configuration parameters](/zscaler-client-connector/supported-parameters-zscaler-client-connector-ios) and their corresponding values per your organization's needs.
[See image.](#enter-keys)
-
For **Type of automatic VPN**, select **On-demand VPN**.
[See image.](#type-of-vpn)
-
In the **On-demand rules** section, click **Add**, select **Connect VPN**, restrict to **All domains** as the primary rule, and click **Save**.
[See image.](#on-demand-rule)
-
If you are using supervised devices, you can block users from disabling automatic VPN. To enable this option, select **Yes** from the drop-down menu.
[See image.](#block-users-vpn)
- Click **Next**.
- In the **Assignments** section, choose the users, groups, and devices for the profile, and click **Next**.
- In the **Review + create** section, review the summary, and click **Create**.
[]To add the policy:
- Go to **Apps** > **App configuration policies** > **Add** > **Managed devices**.
-
On the **Basics** tab, configure the following parameters, and then click **Next**.
- **Name**:** **Enter** **`Zscaler Client Connector`.
- **Description**: (Optional) Enter a relevant description for Zscaler Client Connector.
- **Platform**: Select **iOS/iPadOS**.
- **Targeted app**: Click **Select app.** From the **Associated app** window, select **Zscaler Client Connector**, and then click **OK**.
The **Device enrollment type **field** **is automatically set to **Managed devices**. You cannot edit it.
- On the **Settings **tab, for **Configurations settings format**, select **Use configuration designer**.
- Enter [Zscaler configuration parameters](/zscaler-client-connector/supported-parameters-zscaler-client-connector-ios) and their corresponding values per your organization's needs.
[See image.](#app-config-policy)
- On the **Assignments** tab, select the group assignments for which you want to assign the app configuration policy, and click **Next**.
- On the **Review + create **tab, review the values and settings, and then click **Create**. Intune pushes Zscaler Client Connector to the devices in the group that you selected.
After Zscaler Client Connector is installed on users’ devices, they must launch the app and log in to enroll in the Zscaler service.
[]If you use Zscaler Internet Access (ZIA) and you want to perform SSL inspection, you must configure a certificate profile to push the Certificate Authority certificate required for SSL inspection. You can use the default Zscaler Central Authority (CA) certificate or a custom Root CA certificate.
To learn more, see [Choosing the CA Certificate for SSL Inspection](/zia/choosing-ca-certificate-ssl-inspection) and [Certificate Pinning and SSL Inspection](/zia/certificate-pinning-and-ssl-inspection).
- [(Optional) Download the Zscaler CA certificate.](#download-zscaler-certificate)
- [Configure the certificate profile.](#configure-cert-profile)
[]To download the certificate:
- In the Zscaler Internet Access (ZIA) Admin Portal, go to **Policy > SSL Inspection > Intermediate CA Certificates**.
-
Click the **Edit** icon corresponding to the Zscaler Intermediate CA Certificate.
The **View Zscaler Intermediate CA Certificate** window appears.
-
In the **View Zscaler Intermediate CA Certificate** window, under the **Root Certificate** field, click **Download**.
The root certificate is downloaded as a ZIP file.
- Navigate to the ZscalerRootCerts.zip file and unzip it.
[]To configure the profile:
- In the Microsoft Intune portal, from the left-side navigation, select **Devices**.
- Click **Manage Devices > Configuration**.
- Click **Create **and select** New Policy**.
-
In the **Create a profile** section:
- **Platform**: Select **iOS/iPadOS**.
- **Profile type**: Select **Templates**.
- **Template name**: Select **Trusted Certificate**.
[See image.](#ios-deploy-certificate-profile)
- Click **Create**.
- In the **Basics** section:
- **Name**: Enter a name.
- **Description**: (Optional) Enter a description.
- On the **Configuration Settings** tab, upload the .crt file to Intune and click **Next**.
[See image.](#ios-deploy-trusted-certificate)
- In the **Assignments** section, choose the users, groups, and devices for the profile, and click **Next**.
- In the **Review + create** section, review the summary, and click** Create**.
[]You can add a specific application to Microsoft Intune and associate the application with a per-app VPN configuration profile to ensure that selected applications are protected by ZIA and can access other applications. For example, you can allow access to private applications only from a specific browser.
![How the per-app VPN works](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-per-app-vpn-image.png)
- [a. Add the application to Microsoft Intune.](#add-specific-application-to-intune)
- [b. Configure a device configuration profile for per-app VPN.](#configure-per-app-vpn-device-configuration-profile)
- [c. Associate the application with the per-app VPN device configuration profile.](#associate-app-to-device-configuration-profile)
[]To add the application:
- In the Microsoft Intune portal, from the left-side navigation, select **Apps**.
- Click **iOS/iPadOS apps**, and then click **Add**.
-
From the **App type** drop-down menu, select **iOS store app** and then click **Select**.
[See image.](#add-ios-store-app)
-
To add the app from the iOS store app:
- On the **App information **tab, click **Search the App Store**.
- Search for the application and click **Select**.
[See image.](#select-ios-store-app)
- On the **Assignments **tab, select the group assignments for which you want to deploy the application, and then click **Next**.
- On the **Review + create** tab, review the values and settings, and then click **Create**.
[]
To configure a device configuration profile for per-app VPN:
- In the Microsoft Intune portal, from the left-side navigation, select **Devices**.
-
Click **Manage devices > Configuration**.
[See image.](#devices-config-profiles2)
-
Click **Create **and select** New Policy**.
[See image.](#create-policy2)
-
In the **Create a profile** section:
- **Platform**: Select **iOS/iPadOS**.
- **Profile type**: Select **Templates**.
- **Template name**: Select **VPN**.
[See image.](#create-a-profile-details2)
- Click **Create**.
-
On the **Basics** tab:
- **Name**: Enter a name.
- **Description**: (Optional) Enter a description.
[See image.](#vpn-basics-section2)
- Click **Next**.
-
On the **Configuration settings** tab, for **Connection type**, select **Zscaler**.
[See image.](#configuration-settings2)
-
Enter the following parameters:
- **Connection name**: The label for the profile.
- **Custom domain name**: Enter your Zscaler tenant domain. This allows you to configure the user domain so that users can skip the Zscaler Client Connector enrollment page and go directly to the SSO login page.
-
**Enable strict enforcement**: Enable this option if you want to block internet traffic before the user enrolls in Zscaler Client Connector when:
- The user has not logged in after a new install.
- The user logs in and then logs out.
- An administrator removes the device from the Zscaler Client Connector Portal.
If you enable Strict Enforcement, you must must include policyToken in a device configuration policy and use **Excluded URLs** in a device configuration policy or an excludeList in an app configuration policy. Additional configuration settings are also required. To learn more, see [Configure Additional Strict Enforcement Settings](#configure-strict-enforcement-settings).
- **Organization’s cloud name**: The name of the cloud where your organization is provisioned. For example, if your cloud name is zscalertwo.net, enter `zscalertwo`. To learn more, see [What Is My Cloud Name for ZIA?](/zia/what-my-cloud-name-zia)
- **Excluded URLs**: Enter any URLs you want to bypass. Enter your IdP, MDM server, or anything else the user should have access to before enrollment. If you use the Zscaler Private Access (ZPA) service, you must enter `authsp.prod.zpath.net`. For a list of additional Intune requirements, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/mem/intune/fundamentals/intune-endpoints?tabs=north-america).
[See image.](#config-settings-vpn2)
-
(Optional) Enter [Zscaler configuration parameters](/zscaler-client-connector/supported-parameters-zscaler-client-connector-ios) and their corresponding values per your organization's needs.
[See image.](#enter-keys2)
-
In the **Automatic VPN** section:
- For **Type of automatic VPN**, select **Per-app VPN**.
- If you want Safari to selectively send traffic to specific destinations via Zscaler Client Connector, enter domains in **Safari URLs that will trigger this VPN**.
- If you want to exclude traffic to specific domains, enter domains in **Excluded Domains**.
- If you are using supervised devices, you can block users from disabling automatic VPN. To enable this option, select **Yes** from the drop-down menu.
[See image.](#type-of-vpn-perapp)
- Click **Next**.
- On the **Assignments** tab, choose the users, groups, and devices for the profile, and click **Next**.
- In the **Review + create** section, review the summary, and click **Create**.
[]To associate the application:
- In the Microsoft Intune portal, from the left-side navigation, select **Apps**.
-
Click **All apps**, select the application to forward using Zscaler Client Connector, and select **Properties**.
[See image.](#ios-deploy-edge-properties)
- Next to Assignments, click** Edit** and then click **Included** to access the Assignment Settings.
-
Select the Per-app VPN profile you created in the [previous step](#configure-per-app-vpn-device-configuration-profile) to associate the application with the profile.
[See image.](#ios-deploy-associate-vpn)
[]If you use Entra ID (Azure AD) as your IdP, you can integrate Zscaler Client Connector with the Microsoft Enterprise SSO plug-in so that users do not need to log in to Zscaler Client Connector during enrollment or reauthentication.
![How the Microsoft SSO plug-in works](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-Microsoft-SSO-image.png)
To integrate with the plug-in, the device configuration profile you create must exclude specific URLs for the plug-in and ensure that the VPN profile includes the `username` Key with the Value set to `{{partialupn}}`. To learn more, see [Configure Required Policy Settings](#configuring-required-policy-settings). For a list of URLs, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity-platform/apple-sso-plugin).
To configure the plug-in:
- In the Microsoft Intune portal, from the left-side navigation, select **Devices**.
- Click **Manage Devices > Configuration**.
- Click **Create **and select** New Policy**.
- In the **Create a profile** section:
- **Profile type**: Select **Templates**.
- **Template name**: Select **Device features**.
- Click **Create**.
- On the **Basics** tab:
- **Name**: Enter a name.
- **Description**: (Optional) Enter a description.
- Click **Next**.
- On the **Device features** tab:
- Click **Single sign-on app extension**.
- For **SSO app extension type**, select **Microsoft Entra ID**.
- Enter the **App bundle IDs** allowed to use SSO:
- `**com.apple.**`: Allows all Apple apps to use SSO (required).
- `**com.microsoft.**`: Allows all Microsoft apps to use SSO (required).
- `**com.zscaler.**`: Allows all Zscaler apps to use SSO (required).
- Enter the additional configuration parameters:
- `browser_sso_interaction_enabled`: Enter a value of `1` with a type of `integer` so that Zscaler Client Connector can use Safari to authenticate.
- `disable_explicit_app_prompt`: Enter a value of `1` with a type of `integer` to reduce end-user prompts. Some apps might incorrectly enforce end-user prompts at the protocol layer, resulting in users being prompted to sign in, even though the Microsoft Enterprise SSO plug-in works for other apps.
- `AppPrefixAllowList`: Enter a list of prefixes for apps that are allowed to use SSO. The following prefixes are required:
- `com.zscaler.`
- `com.microsoft.`
- `com.apple.`
[See image.](#device-features)
- On the **Assignments** tab, select the group assignments for which you want to assign the policy, and click **Next**.
- On the** Review + create** tab, review the values and settings, and then click **Create**.
[]If you are installing Zscaler Client Connector with Strict Enforcement, you must complete additional configuration steps:
- In the **Zscaler Client Connector Portal**, go to **App Profiles** > **iOS **to configure the app profile policy you want to enforce during strict enforcement. To bypass destination IPs, add the IP addresses to the IP Exclusion List. To bypass web destinations, add the domain names to the custom PAC file associated with the policy (e.g., your IdP login page). Save the App Profile and reopen it to copy the Policy Token.
[See image.](#test)
[]![Policy Token value](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-ios-doc-58629/strictenforcement-policytoken.png)
- In Microsoft Intune, create a device configuration profile or edit your [previously](#configure-device-configuration-profile) created profile and include the following:
-
**Enable** **strict enforcement** is selected on the **Configuration Settings** tab.
[See image.](#strict-enforcement-enabled)
-
The list of **Excluded URLs** includes the following hostnames:
- Hosts required for ZPA:
- authsp.prod.zpath.net
- samlsp.private.zscaler.com
- samlsp-pdx2.private.zscaler.com
- Hosts required for Intune. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/mem/intune/fundamentals/intune-endpoints?tabs=north-america#apple-dependencies).
- Hosts required for Apple. To learn more, refer to the [Apple documentation](https://support.apple.com/en-us/101555).
- Hosts required for your organization's IdP. To learn more, refer to your IdP documentation.
When deploying Strict Enforcement, a policyToken must be defined and the **Excluded URLs** list must contain at least one entry.
[See image.](#se-pt)
[]![Enter the excluded URLs](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-ios-doc-58629/intune-strict-enforce.png)
- Add a new key-value pair for policyToken.
[See image.](#key-value-pt)
[]![policy token](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-ios-doc-58629/intune-policy-token-strict.png)
Troubleshooting Strict Enforcement
If Zscaler Client Connector blocks sites after being installed with Strict Enforcement, you can inspect the ZSATunnel_[DATETIME].log file for the string `Proxy=PROXY`. If the file includes a `Local captive mode! Dropping Https request` message for a hostname, you can resolve the issue by adding the hostname to the **Excluded URLs** field in the device configuration profile.
[See image.](#strict-enforcement-zsatunnellog)
[]![Add an application](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-add-app.png)
[]![Select the app type](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-ios-store-app.png)
[]![Select the Zscaler Client Connector app](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-select-zclient-connector-app.png)
[]![Enter the app information](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-add-app-info.png)
[]![Edit the app settings](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-edit-assignment.png)
[]![Click Configuration](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-ios-doc-58629/zclientconnector-ios-configuration%20Profiles.png)
[]![Click New Policy](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-create-policy.png)
[]![Select platform, profile type and template of VPN](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-create-profile.png)
[]![Enter a name and an optional description in the Basics section.](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-profile-basics.png)
[]![Select the Zscaler connection type](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-configuration-settings.png)
[]![Enter the configuration settings for the VPN](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-configuration-parameters.png)
[]![Enter the key and value pairs](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-enter-keys.png)
[]![Add an on-demand rule](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-on-demand-rule.png)
[]![Select the VPN type](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-on-demand-vpn.png)
[]![Block users from disabling automatic VPN](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-block-users-vpn.png)
[]![Use the configuration designer](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-app-config-policy.png)
[]![Fill in the details for the Assignments section](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-associate-perapp-vpn.png)
[]![Select the app properties](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-edge-properties.png)
[]![Upload the certificate](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-trusted-certificate.png)
[]![Select the Trusted certificate template](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-certificate-profile.png)
[]![Select the app type](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-select-ios-app.png)
[]![Search for the app](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-search-edge-app.png)
[]![Click Configuration](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-devices.png)
[]![Click New Policy](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-create-policy.png)
[]![Select platform, profile type and template of VPN](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-create-profile.png)
[]![Enter a name and an optional description in the Basics section.](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-profile-basics-perapp.png)
[]![Select a connection type of Zscaler](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-configuration-settings.png)
[]![Enter the configuration settings for the VPN](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-configuration-parameters.png)
[]![Enter the key and value pairs](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-enter-keys.png)
[]![Select the type of VPN](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-type-of-vpn-perapp.png)
[]![Enter the SSO configuration settings](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-device-features.png)
[]![Enable strict enforcement](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-strict-enforcement-enabled.png)
[]![View log file for strict enforcement errors](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-ios/ios-deployment-intune-strict-enforcement-zsatunnellog.png)