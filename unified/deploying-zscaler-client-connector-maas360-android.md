# Deploying Zscaler Client Connector with MaaS360 for Android
Source: https://help.zscaler.com/zscaler-client-connector/deploying-zscaler-client-connector-maas360-android
PDF: https://help.zscaler.com/pdf/com/en/1341041.pdf

This guide is for admins only. If you are an end user, contact your organization’s administrator for deployment-related details.
With IBM MaaS360 with Watson, you can deploy Zscaler Client Connector for Android by pushing Zscaler Client Connector:
- From Google Play *with* Android Enterprise enabled
- From Google Play *without* Android Enterprise enabled
- As an APK file
Optionally, if you deploy Zscaler Client Connector via Google Play *with* Android Enterprise, you can preconfigure Zscaler Client Connector with [parameters](/zscaler-client-connector/parameters-guide-zscaler-client-connector-android-and-android-chromeos). This allows you to simplify the Zscaler Client Connector [enrollment process](/zscaler-client-connector/enrolling-zscaler-service-zscaler-client-connector) for your users.
If you are not enrolled in the Android Enterprise program, or are pushing Zscaler Client Connector as an APK file, you cannot make any configurations. For more information, refer to [IBM MaaS360 documentation](https://www.ibm.com/docs/en/maas360?topic=android).
- [Deploying Zscaler Client Connector from Google Play](#deploy-google-play)
- [Deploying Zscaler Client Connector as an APK File](#deploy-apk-file)
[]To deploy Zscaler Client Connector to IBM MaaS360 with Watson for Android devices from Google Play Store:
The following deployment procedure is based on MaaS360 10.72.
- In the MaaS360 portal, click **Apps** from the top menu.
![Navigating to the Apps page](/downloads/z-app/maas360-android-1.png)
- Click **Add **and then click the **Add **icon for Android.
![Selecting to add an Android application](/downloads/z-app/maas360-android-2.png)
- Click **Google Play App**.
![The Google Play App option](/downloads/z-app/maas360-android-3.png)
- Select **Add via Public Google Play Store**.
![The Add via Public Google Play Store option](/downloads/z-app/maas360-android-4.png)
- In the **App Name** field, search for and select `Zscaler Client Connector` and then click **Add**.
![Searching for and selecting the Zscaler Client Connector](/downloads/z-app/maas360-android-5.png)
- If you're using Android Enterprise, you're prompted to accept permissions. Click **I Agree**.
- Click the **Policies and Distribution** tab.
- In the **Distribute to** field, select the user devices to which you're going to deploy Zscaler Client Connector and then click **Add**.
![Selecting to which user devices to distribute Zscaler Client Connector](/downloads/z-app/maas360-android-70.png)
- (Optional) If you have Android Enterprise enabled, you can use [parameters](/zscaler-client-connector/parameters-guide-zscaler-client-connector-android-and-android-chromeos) to preconfigure Zscaler Client Connector. Preconfiguring Zscaler Client Connector allows you to remove steps from the user enrollment process (e.g., allowing users to skip the enrollment page or the cloud selection prompt on Zscaler Client Connector).
You can only preconfigure Zscaler Client Connector if you deploy the app from Google Play with Android Enterprise enabled.
- Click the **App Configurations** tab.
- Select **Configure App Settings** and then click** Add**.
![The Configure App Settings option for Zscaler Client Connector](/downloads/z-app/maas360-android-8a.png)
- Add [Zscaler configuration parameters](/zscaler-client-connector/parameters-guide-zscaler-client-connector-android-and-android-chromeos) and their corresponding values per your organization's needs.
You can also use MaaS360 variables to automatically populate these fields.
- Click **Add**.
![The parameters for Zscaler Client Connector](/downloads/z-app/maas360-android-8b.png)
- Enter your admin password and then click **Confirm**.
![Confirming the changes for deploying Zscaler Client Connector](/downloads/z-app/maas360-android-9.png)
After Zscaler Client Connector is on users’ devices, they must launch the app and log in to enroll in the Zscaler service.
[]You can distribute Zscaler Client Connector outside of Google Play by pushing the APK file to devices.
With this method, you cannot preconfigure Zscaler Client Connector with parameters.
To deploy Zscaler Client Connector to IBM MaaS360 with Watson as an APK file:
- In the Zscaler Client Connector Portal, go to **Administration **> **Client Connector App Store** and download the Zscaler Client Connector APK file from the **Registered Devices** tab.
Contact Zscaler Support to enable the APK file link.
![Client Connector Portal App Store Download Link](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-maas360-android/Client_Connector_App_Store.png)
- In the MaaS360 portal, click **Apps** from the top menu.
![Navigating to the Apps page](/downloads/z-app/maas360-android-apk-2.png)
- Click **Add**, and then click the **Add **icon for Android.
![Selecting to add an Android application](/downloads/z-app/maas360-android-apk-3.png)
- Click **Enterprise App for Android**.
![The Enterprise App for Android option](/downloads/z-app/maas360-android-apk-4.png)
- Upload the APK file.
![Uploading the Zscaler Client Connector APK file](/downloads/z-app/maas360-android-apk-5.png)
- (Optional) Enter a description, assign a category, or upload screenshots.
- Click **Add**.
![Add a description, a category, or screenshots for the Zscaler Client Connector](/downloads/z-app/maas360-android-apk-6.png)
- Click the **Policies and Distribution** tab.
- In the **Distribute to** field, select the user devices to which you want to deploy Zscaler Client Connector and then click **Add**.
![Selecting to which user devices to distribute Zscaler Client Connector](/downloads/z-app/maas360-android-apk-7.png)
- Enter your admin password and then click **Confirm**.
![Confirming the changes for deploying Zscaler Client Connector](/downloads/z-app/maas360-android-apk-8.png)
After Zscaler Client Connector is on users’ devices, they must launch the app and log in to enroll to the Zscaler service.