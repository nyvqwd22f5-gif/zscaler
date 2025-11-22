# Deploying Zscaler Client Connector with MobileIron for iOS
Source: https://help.zscaler.com/unified/deploying-zscaler-client-connector-mobileiron-ios
PDF: https://help.zscaler.com/pdf/com/en/1492296.pdf

This guide is for admins only. If you are an end-user, contact your organization’s administrator for deployment-related details.
With MobileIron, you can configure and deploy Zscaler Client Connector for iOS devices.
- [Deploying Zscaler Client Connector from the App Store](#Deploying-ZscalerClientConnector-Appstore)
- [Configure a Custom Settings Profile](#Configure-Custom-profile-deployment)
[]To configure and deploy Zscaler Client Connector to MobileIron for iOS devices:
- In the MobileIron Admin Portal, click **Apps** from the left menu.
![MobileIron Admin Portal App Catalog](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-mobileiron-ios/mobileiron-clickapps.png)
- Click **Add** and search for `Zscaler Client Connector`.
- Select Zscaler Client Connector from the list, and then click **Next**.
![Adding Zscaler Client Connector app](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-mobileiron-ios/mobileiron-search-zscalerclientconnector_1.png)
- (Optional) Modify the **Description** and select a **Category**. Click **Next**.
![App information such as description and category ](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-mobileiron-ios/mobileIron-modify-description-and-category.png)
- In the **Delegate** section, choose the **App Delegation** options.
![App delegation options](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-mobileiron-ios/mobileIron-choose-%20delegate-options.png)
- In the **Distribute** section, choose the distribution options.
![Distribution filter options](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-mobileiron-ios/mobileIron-choose-distribute-options.png)
- In the **Configure** section, click on **Apple Managed App Configuration**.
![App Configurations](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-mobileiron-ios/mobileIron-apple-managed-app-configuration-.png)
- Under **Apple Managed App Settings**, click **Add** and enter the following configuration keys and their corresponding configuration values. Set the value type as a string for all the configuration keys.
- **userDomain**: Your organization’s domain name (e.g., `safemarch.com`.) If your instance has multiple domains associated with it, enter the primary domain for your instance.
- **cloudname**: The name of the cloud on which your organization is provisioned. For example, if your cloud name is zscalertwo.net, you would enter `zscalertwo`.
- **strictEnforcement**: This allows you to block internet traffic before the user enrolls in Zscaler Client Connector. Enter `1` to enable.
- **excludeList**: This allows you to exclude domains and IP addresses that should not be tunneled. If you are using strictEnforcement, this is critical because identity provider (IdP) domains and MDM connectivity must be bypassed to maintain connectivity. Enter a value, for example, `apple.com`, `airwatch.com`.
- **newBindFlow**: Enables multithreaded implementation of Zscaler Client Connector microservices binding with Zscaler Client Connector virtual interface. Enter `1` to enable.
- **deviceToken**: This option allows you to use Zscaler Client Connector as an IdP. The Zscaler service silently provisions and authenticates users even if you don't have an authentication mechanism in place. Before adding this option, you must generate a device token in the Zscaler Client Connector and complete the full configuration detailed in [Using Zscaler Client Connector as an IdP](/unified/using-zscaler-client-connector-identity-provider).
- **policyToken**: This option specifies which app profile policy you want to enforce for the app before the user enrolls. This install option is only applicable and required if you enable the strictEnforcement option and want users to enroll with the app before accessing the internet. Retrieve the policy token from the iOS application profile located in the Admin Portal.
- **username**: The username for the user. For example, if the username is j.doe@zscaler.com, you would enter` j.doe`.
- **authByTunnel**: The auto-enrollment settings for users when Zscaler Client Connector is used as an identity provider (IdP) for authentication. Set it to `1` to always auto-enroll the users even if they are logged out manually or forcefully removed from the portal. Set it to `2` for one-time auto-enrollment. Set it to `0` to disable auto-enrollment.
- **ownership**: If you use the device posture type **ownership Variable**, add the key `ownership`. You can enter up to 32 alphanumeric characters in the **Configuration value** field. To learn more, see [Configuring Device Posture Profiles](/unified/configuring-device-posture-profiles).
- **SkipInterfaceInstallation**: When enabled, Zscaler Client Connector doesn’t install a virtual interface if a user isn’t logged in. This prevents the VPN icon from displaying on the device when the user is not logged in. Enter `1` to enable or `0` to disable this option. By default, the value is `0`.
- **PAVConnectionSynced**: Applicable to per-app VPN deployments only. It allows the initial launch of the per-app VPN application in the loading state instead of showing an error while Zscaler Client Connector configuration is being downloaded. By default, it's disabled (i.e., `0`. Pass `1` to enable this feature).
-
**enableFips**: Enabling this option indicates that Zscaler Client Connector uses FIPS-compliant libraries for communication with Zscaler infrastructure. Enter `1` to enable or `0` to disable this option.
Enable this option only if you require FIPS-level security within your organization.
![Configuration setup and adding configuration keys](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-mobileiron-ios/mobileIron-configuration-keys.png)
[]To configure custom settings payload with XML code for an iOS device profile:
- In the MobileIron Admin Portal, go to **Configurations**.
- In the OS Version section, select **iOS**.
- From the options on the right, click **Custom**.
![Adding configurations and OS versions](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-mobileiron-ios/mobileIron-select-custom-and-iOS_1.png)
- Provide a name for the profile and upload your .mobileconfig file.
![Create custom configuration screen](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-mobileiron-ios/mobileIron-add-name-upload-file.png)
- You can use the [ZscalerSample.mobileconfig](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-mobileiron-ios/zscalersample.mobileconfig) file as a starting template, and edit the following values in the <VendorConfig> section of the file based on your needs.
- **userDomain**: Your organization’s domain name (e.g., `safemarch.com`). If your instance has multiple domains associated with it, enter the primary domain for your instance.
- **cloudname**: The name of the cloud where your organization is provisioned. For example, if your cloud name is zscalertwo.net, enter `zscalertwo`.
- **strictEnforcement**: This allows you to block internet traffic before the user enrolls in Zscaler Client Connector. Enter `1` to enable.
- **excludeList**: This allows you to exclude domains and IP addresses that should not be tunneled. If you are using strictEnforcement, this is critical because identity provider (IdP) domains and MDM connectivity must be bypassed to maintain connectivity. Enter a value, for example, `apple.com`, `airwatch.com`.
- **newBindFlow**: Enables multithreaded implementation of Zscaler Client Connector microservices binding with Zscaler Client Connector virtual interface. Enter `1` to enable.
- **deviceToken**: This option allows you to use Zscaler Client Connector as an IdP. The Zscaler service silently provisions and authenticates users even if you don't have an authentication mechanism in place. Before adding this option, you must generate a device token in the Zscaler Client Connector and complete the full configuration detailed in [Using Zscaler Client Connector as an IdP](/unified/using-zscaler-client-connector-identity-provider).
- **policyToken**: This option specifies which app profile policy you want to enforce for the app before the user enrolls. This install option is only applicable and required if you enable the strictEnforcement option and want users to enroll with the app before accessing the internet. Retrieve the policy token from the iOS application profile located in the Admin Portal.
- **username**: The username for the user. For example, if the username is j.doe@zscaler.com, you would enter` j.doe`.
- **authByTunnel**: The auto-enrollment settings for users when Zscaler Client Connector is used as an identity provider (IdP) for authentication. Set it to `1` to always auto-enroll the users even if they are logged out manually or forcefully removed from the portal. Set it to `2` for one-time auto-enrollment. Set it to `0` to disable auto-enrollment.
- **ownership**: If you use the device posture type **ownership Variable**, add the key `ownership`. You can enter up to 32 alphanumeric characters in the **Configuration value** field. To learn more, see [Configuring Device Posture Profiles](/unified/configuring-device-posture-profiles).
- **SkipInterfaceInstallation**: When enabled, Zscaler Client Connector doesn’t install a virtual interface if a user isn’t logged in. This prevents the VPN icon from displaying on the device when the user is not logged in. Enter `1` to enable or `0` to disable this option. By default, the value is `0`.
-
**enableFips**: Enabling this option indicates that Zscaler Client Connector uses FIPS-compliant libraries for communication with **Zscaler** infrastructure. Enter `1` to enable or `0` to disable this option.
Enable this option only if you require FIPS-level security within your organization.
- In the **Distribute** section, configure the distribution settings.
![Configure distribute settings screen](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-mobileiron-ios/mobileIron-configure-distribute-settings.png)
- Click **Done**.
Users must open Zscaler Client Connector once for the configurations to be applied for the first time.