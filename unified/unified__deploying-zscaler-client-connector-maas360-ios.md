# Deploying Zscaler Client Connector with MaaS360 for iOS
Source: https://help.zscaler.com/unified/deploying-zscaler-client-connector-maas360-ios
PDF: https://help.zscaler.com/pdf/com/en/1491986.pdf

This guide is for admins only. If you are an end-user, contact your organization’s administrator for deployment-related details.
With IBM MaaS360 with Watson, you can deploy Zscaler Client Connector for iOS devices. Optionally, you can also configure Zscaler Client Connector with parameters to simplify the enrollment process for your users. For more information, refer to the IBM MaaS360 documentation.
To deploy Zscaler Client Connector to IBM MaaS360 with Watson for iOS devices:
The deployment procedure below is based on MaaS360 10.72.
- In the MaaS360 portal, click **Apps** from the top menu.
![Navigating to the Apps page](/downloads/z-app/maas360-ios-1.png)
- Click **Add**, and then click the icon next to **iOS**.
![Selecting to add an iOS application](/downloads/z-app/maas360-ios-2.png)
- Click **iTunes App Store App** from the list.
![The iTunes App Store App option](/downloads/z-app/maas360-ios-3.png)
- In the **App** field, search for and select `Zscaler Client Connector`.
![Searching for and selecting the Zscaler Client Connector](/downloads/z-app/maas360-ios-4.png?1603972089)
- (Optional) Assign categories to the apps.
![Assigning categories for the Zscaler Client Connector](/downloads/z-app/maas360-ios-5.png?1603971854)
- Click the **Policies and Distribution** tab.
- In the **Distribute to** field, select to which user devices to deploy Zscaler Client Connector.
![Selecting to which user devices to distribute Zscaler Client Connector](/downloads/z-app/maas360-ios-6.png)
- (Optional) You can use parameters to preconfigure Zscaler Client Connector. Preconfiguring Zscaler Client Connector allows you to remove steps from the user enrollment process (e.g., allowing users to skip the enrollment page or the cloud selection prompt on Zscaler Client Connector.)
- Click the **Configuration** tab.
- In **App Config Source**, select **Key/Value**.
![Selecting Key/Value as the Zscaler Client Connector configuration source](/downloads/z-app/maas360-ios-7a.png)
- Enter any of the following key/value pairs in the Enter Attribute Name and Enter Attribute Value fields. You can also use MaaS360 variables to automatically populate these fields.
- **userDomain**: Your organization’s domain name, e.g., `safemarch.com`. If your instance has multiple domains associated with it, enter the primary domain for your instance.
- **cloudname**: The name of the cloud on which your organization is provisioned. For example, if your cloud name is zscalertwo.net, you would enter` zscalertw`o.
- **strictEnforcement**: This allows you to block internet traffic before the user enrolls in Zscaler Client Connector. Enter `1` to enable.
- **excludeList**: This allows you to exclude domains and IP addresses that should not be tunneled. If you are using strictEnforcement, this is critical because identity provider (IdP) domains and MDM connectivity must be bypassed to maintain connectivity. Enter a value, for example, `apple.com`, `airwatch.com`.
- **newBindFlow**: Enables multithreaded implementation of Zscaler Client Connector microservices binding with Zscaler Client Connector virtual interface. Enter `1` to enable.
- **deviceToken**: This option allows you to use the Zscaler Client Connector as an IdP. The Zscaler service silently provisions and authenticates users even if you don't have an authentication mechanism in place. Before adding this option, you must generate a device token in the Zscaler Client Connector and complete the full configuration detailed in [Using Zscaler Client Connector as an IdP](/unified/using-zscaler-client-connector-identity-provider).
- **policyToken**: This option specifies which app profile policy you want to enforce for the app before the user enrolls. This install option is only applicable and required if you enable the strictEnforcement option and want users to enroll with the app before accessing the internet. Retrieve the policy token from the iOS application profile located in the Admin Portal.
- **username**: The username for the user. For example, if the username is j.doe@zscaler.com, you would enter` j.doe`.
- **authByTunnel**: The auto-enrollment settings for users when Zscaler Client Connector is used as an identity provider (IdP) for authentication. Set it to `1` to always auto-enroll the users even if they are logged out manually or forcefully removed from the portal. Set it to `2` for one-time auto-enrollment. Set it to `0` to disable auto-enrollment.
- **ownership**: If you use the device posture type **ownership Variable**, add the key `ownership`. You can enter up to 32 alphanumeric characters in the **Configuration value** field. To learn more, see [Configuring Device Posture Profiles](/unified/configuring-device-posture-profiles).
- **SkipInterfaceInstallation**: When enabled, Zscaler Client Connector doesn’t install a virtual interface if a user isn’t logged in. This prevents the VPN icon from displaying on the device when the user is not logged in. Enter `1` to enable or `0` to disable this option. By default, the value is `0`.
- **PAVConnectionSynced**: Applicable to per-app VPN deployments only. It allows the initial launch of the per-app VPN application in the loading state instead of showing an error while Zscaler Client Connector configuration is being downloaded. By default, it's disabled (i.e., `0`. Pass `1` to enable this feature).
-
**enableFips**: Enabling this option indicates that Zscaler Client Connector uses FIPS-compliant libraries for communication with Zscaler infrastructure. Enter `1` to enable or `0` to disable this option.
Enable this option only if you require FIPS-level security within your organization.
![Configured key/value pairs for the Zscaler Client Connector](/downloads/z-app/downloading-deployment/deploying-zscaler-app-maas360-ios/GOV-maas360-iOS-7b.png?1597394254)
- Once you are finished making changes, click **Add**.
- Enter your admin password to confirm the changes.
![Confirming the changes for deploying Zscaler Client Connector](/downloads/z-app/maas360-ios-8.png)
Once Zscaler Client Connector is on users’ devices, they must launch the app and log in to enroll to the Zscaler service.