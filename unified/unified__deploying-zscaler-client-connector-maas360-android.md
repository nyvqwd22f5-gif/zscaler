# Deploying Zscaler Client Connector with MaaS360 for Android
Source: https://help.zscaler.com/unified/deploying-zscaler-client-connector-maas360-android
PDF: https://help.zscaler.com/pdf/com/en/1491981.pdf

This guide is for admins only. If you are an end user, contact your organization’s administrator for deployment-related details.
With IBM MaaS360 with Watson, you can deploy Zscaler Client Connector for Android by pushing Zscaler Client Connector:
- From Google Play *with* Android Enterprise enabled
- From Google Play *without* Android Enterprise enabled
- As an APK file
Optionally, if you deploy Zscaler Client Connector via Google Play *with* Android Enterprise, you can preconfigure Zscaler Client Connector with parameters. This allows you to simplify the Zscaler Client Connector enrollment process for your users.
If you are not enrolled in the Android Enterprise program, or are pushing Zscaler Client Connector as an APK file, you cannot make any configurations. For more information, refer to the [IBM MaaS360 documentation](https://www.ibm.com/docs/en/maas360?topic=android).
- [Deploying Zscaler Client Connector from Google Play](#deploy-google-play)
- [Deploying Zscaler Client Connector as an APK File](#deploy-apk-file)
[]To deploy Zscaler Client Connector to IBM MaaS360 with Watson for Android devices from Google Play Store:
The following deployment procedure is based on MaaS360 10.72.
- In the MaaS360 portal, click **Apps** from the top menu.
![Navigating to the Apps page](/downloads/z-app/maas360-android-1.png)
- Click **Add**, and then click the **Add **icon for Android.
![Selecting to add an Android application](/downloads/z-app/maas360-android-2.png)
- Click **Google Play App**.
![The Google Play App option](/downloads/z-app/maas360-android-3.png)
- Select **Add via Public Google Play Store**.
![The Add via Public Google Play Store option](/downloads/z-app/maas360-android-4.png)
- In the **App Name** field, search for and select `Zscaler Client Connector` and then click **Add**.
![Searching for and selecting the Zscaler Client Connector](/downloads/z-app/maas360-android-5.png)
- If you're using Android Enterprise, you're prompted to accept permissions.
![No permissions required for Zscaler Client Connector if Android Enterprise disabled](/downloads/z-app/maas360-android-6a.png)
![Accepting permissions for Zscaler Client Connector if Android Enterprise enabled](/downloads/z-app/maas360-android-6b.png)
- Click the **Policies and Distribution** tab.
- In the **Distribute to** field, select which user devices to which you're going to deploy Zscaler Client Connector and then click **Add**.
![Selecting to which user devices to distribute Zscaler Client Connector](/downloads/z-app/maas360-android-70.png)
- (Optional) If you have Android Enterprise enabled, you can use parameters to preconfigure Zscaler Client Connector. Preconfiguring Zscaler Client Connector allows you to remove steps from the user enrollment process (e.g., allowing users to skip the enrollment page or the cloud selection prompt on Zscaler Client Connector).
You can only preconfigure Zscaler Client Connector if you deploy the app from Google Play with Android Enterprise enabled.
- Click the **App Configurations** tab.
- Select **Configure App Settings **and then click** Add**.
![The Configure App Settings option for Zscaler Client Connector](/downloads/z-app/maas360-android-8a.png)
- The following parameters are available to configure:
- **userDomain**: Your organization’s domain name, e.g., `safemarch.com`. If your instance has multiple domains associated with it, enter the primary domain for your instance.
- **cloudname**: The name of the cloud on which your organization is provisioned. For example, if your cloud name is zscalertwo.net, you would enter `zscalertwo`.
- **deviceToken**: The appropriate device token from the Admin Portal, if you want to use the [Zscaler Client Connector as an IdP](/unified/using-zscaler-client-connector-identity-provider).
- **userName**: The username for the user. For example, if the username is j.doe@safemarch.com, you would enter` j.doe`.
-
**enableFips**: Enabling this option indicates that Zscaler Client Connector uses FIPS-compliant libraries for communication with Zscaler infrastructure. Enter `1` to enable or `0` to disable this option.
Enable this option only if you require FIPS-level security within your organization.
- **Ownership**:** **If you use the Ownership Variable device posture type, add the key `Ownership`. You can enter up to 32 alphanumeric characters in the **Configuration value** field. To learn more, see [Configuring Device Posture Profiles](/unified/configuring-device-posture-profiles).
-
**autoEnrollWithMDM**: Use this parameter to determine auto-enrollment without user interaction when using the Zscaler Client Connector as an IdP. Select from the following options:
- Enter `0`** **to disable auto-enrollment.
- Enter `1`** **to have users always auto-enroll, even if they log out.
- Enter `2`** **for one-time auto-enrollment.
This option applies to only the Internet & SaaS-enabled accounts that are using Zscaler Client Connector as an IdP. You must specify the parameters deviceToken, cloudName, and userDomain before enabling the autoEnrollWithMDM option.
- **customDNS**: By default, Zscaler Client Connector uses the device's DNS server. You can change the value to another DNS server using this setting. Enter the DNS IP address.
- **allowZCCOnRootedDevice**: This is set to 0 by default to restrict users from running Zscaler Client Connector on a rooted device. Enter `1` to allow users to run Zscaler Client Connector on a rooted device.
- **externalDeviceId**: You can use this ID to associate devices in an MDM solution with devices in the Admin Portal. By default, the value is 0. Enter a custom value to identify the device.
You can also use MaaS360 variables to automatically populate these fields.
![The parameters for Zscaler Client Connector](/downloads/z-app/maas360-android-8b.png)
- Click **Add**.
- Enter your admin password and then click **Confirm**.
![Confirming the changes for deploying Zscaler Client Connector](/downloads/z-app/maas360-android-9.png)
After Zscaler Client Connector is on users’ devices, they must launch the app and log in to enroll to the Zscaler service.
[]You can distribute Zscaler Client Connector outside of Google Play by pushing the APK file to devices.
With this method, you cannot preconfigure Zscaler Client Connector.
To deploy Zscaler Client Connector to IBM MaaS360 with Watson as an APK file:
- In the Admin Portal, [download Zscaler Client Connector APK file](/unified/understanding-zscaler-client-connector-app-downloads).
![The Zscaler Client Connector APK file download link](/downloads/z-app/downloading-deployment/deploying-zscaler-app-maas360-android/MaaS360-Zscaler-App-Android-APK.png)
- In the MaaS360 portal, click **Apps** from the top menu.
![Navigating to the Apps page](/downloads/z-app/maas360-android-apk-2.png)
- Click **Add**, and then click the icon next to **Android**.
![Selecting to add an Android application](/downloads/z-app/maas360-android-apk-3.png)
- Click **Enterprise App for Android**.
![The Enterprise App for Android option](/downloads/z-app/maas360-android-apk-4.png)
- Upload the APK file.
![Uploading the Zscaler Client Connector APK file](/downloads/z-app/maas360-android-apk-5.png)
- (Optional) Add a description, assign a category, or upload screenshots.
![Add a description, a category, or screenshots for the Zscaler Client Connector](/downloads/z-app/maas360-android-apk-6.png)
- Click the **Policies and Distribution** tab.
- In the **Distribute to** field, select the user devices to which you want to deploy Zscaler Client Connector and then click **Add**.
![Selecting to which user devices to distribute Zscaler Client Connector](/downloads/z-app/maas360-android-apk-7.png)
- Enter your admin password and then click **Confirm**.
![Confirming the changes for deploying Zscaler Client Connector](/downloads/z-app/maas360-android-apk-8.png)
After Zscaler Client Connector is on users’ devices, they must launch the app and log in to enroll to the Zscaler service.