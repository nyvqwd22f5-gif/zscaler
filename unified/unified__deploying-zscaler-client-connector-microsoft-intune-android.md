# Deploying Zscaler Client Connector with Microsoft Intune for Android
Source: https://help.zscaler.com/unified/deploying-zscaler-client-connector-microsoft-intune-android
PDF: https://help.zscaler.com/pdf/com/en/1492021.pdf

This guide is for admins only. If you are an end user, contact your organization’s administrator for deployment-related details.
With Microsoft Intune, you can deploy Zscaler Client Connector for your Android and Android on ChromeOS devices. The Microsoft Intune Service release version 2006 is shown in the following steps.
If you deploy Zscaler Client Connector from Google Play *with* Android Enterprise enabled, you can preconfigure Zscaler Client Connector with [parameters](/unified/parameters-guide-zscaler-client-connector-android-and-android-chromeos). This allows you to simplify the Zscaler Client Connector enrollment process for your users. But, if you deploy Zscaler Client Connector from Google Play *without* Android Enterprise enabled or as an APK file, you cannot preconfigure Zscaler Client Connector.
- [From Google Play *with* Android Enterprise enabled](#google-play-with-android-enterprise-enabled)
- [From Google Play *without* Android Enterprise enabled](#google-play-without-android-enterprise-enabled)
- [As an APK file](#apk-file)
[]To deploy Zscaler Client Connector to Microsoft Intune for enterprise-enabled Android devices:
- [Configure Managed Google Play app](#managed-google-play-app)
- [Configure Managed Google Play private app](#managed-google-play-private-app)
- []In the Microsoft Intune admin center, click **Apps** in the left-side navigation.
[See image.](#apps1)
[]![The Microsoft Intune admin center ](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-doc-53347-doc-55060/android_with_enterprise_enabled_select_apps_page_1.png)
- Click **All apps**, and then click **Add**.
[See image.](#all_apps1)
[]![The Apps page in the Microsoft Intune admin center ](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-doc-53347-doc-55060/android_with_enterprise_enabled_apps_add_page_1.png)
- Select **Managed Google Play app** from the **Select app type** drop-down menu, and then click **Select**.
[See image.](#managed)
[]![The All apps page in the Microsoft Intune admin center ](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-doc-53347-doc-55060/android_with_enterprise_enabled_app_type_page_2.png)
- In the **Managed Google Play **app store, search for and select **Zscaler Client Connector**.
[See image.](#search)
[]![The Managed Google Play app store in the Microsoft Intune admin center ](/downloads/z-app/downloading-deployment/deploying-zscaler-app-microsoft-intune-android/android_with_enterprise_enabled_google_play_search.png?1598420224)
- Click **Approve** to accept Zscaler Client Connector permissions in the **Managed Google Play** page.
- Select **Keep approved when app requests new permissions** in the **Approval Settings** tab, and then click **Done**.
- Click **Select**, and then click **Sync **to add Zscaler Client Connector.
[See image.](#sync)
[]![Sync Zscaler Client Connector to Microsoft Intune](/downloads/z-app/downloading-deployment/deploying-zscaler-app-microsoft-intune-android/android_with_enterprise_enabled_google_paly_sync.png?1598421812)
- To configure the app for Android devices:
- Navigate to **Apps** > **App configuration policies**.
- On the **Basics** tab, configure the following parameters, and then click **Next**.
- **Name**:** **Enter** **`Zscaler Client Connector`.
- **Description**: (Optional) Enter a relevant description for Zscaler Client Connector.
- **Platform**: Select **Android Enterprise**.
- **Profile Type**: Select a relevant profile type based on your requirements. In this example, it's **Work Profile Only**.
- **Targeted app**: Click **Select app**, select** Zscaler Client Connector** from the **Associated app** window, and then click **OK**.
[See image.](#basic)
The **Device enrollment type **field** **is automatically set to **Managed devices **and is** **not editable.
[]![Basics tab on the Apps page of the Microsoft Intune admin center](/downloads/z-app/downloading-deployment/deploying-zscaler-app-microsoft-intune-android/android_with_enterprise_enabled_basics_page.png?1598422734)
- On the **Settings **tab, select **Use configuration designer **as the **Configurations settings **format.
- Click **Add**.
- Add [Zscaler configuration parameters](/unified/parameters-guide-zscaler-client-connector-android-and-android-chromeos) and their corresponding values per your organization's needs.
[See image.](#parameters)
- After you enter the appropriate values for the configuration keys that you selected, click **Next**.
[]![Create app configuration policy page to add values to Zscaler parameters](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-doc-53347-version-updates/img7a_parameters_client_connector_deploy_MSIntune_android.png)
- On the **Assignments** tab, select the group assignments for which you want to assign the app configuration policy, and then click **Next**.
[See image.](#assignments)
[]![Assignments tab in the Microsoft Intune admin center](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-doc-53347-doc-55060/android_with_enterprise_enabled_assignments_page1.png)
- On the **Review + create **tab, review the values and settings entered, and then click **Create**. Zscaler Client Connector is pushed to the devices in the group that you selected.
[See image.](#review-create)
[]![Review + Create tab on App configuration policies page in the Microsoft Intune admin center](/downloads/client-connector/downloading-deployment/deploying-zscaler-client-connector-microsoft-intune-android/Microsoft_Intune_Review_Create_tab_Create_Button_2.png)
After Zscaler Client Connector is installed on users' devices, they must launch the app and log in to enroll in the Zscaler service.
- []In the Microsoft Intune admin center, click **Apps** in the left-side navigation.
- Click **Add**.
- Select **Managed Google Play app** from the **Select app type** drop-down menu, and then click **Select**.
[See image.](#private-app-add)
[]![Android apps page in the Microsoft Intune admin center](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-draft-android-112/ZClientConnector-private-app-Apps-Managed-Google-Play-app_1.png)
- In the **Managed Google Play app** section, click the **Lock** icon in the left-side navigation.
- Click the + icon located at the bottom-right of the screen.
[See image.](#plus-icon)
[]![Managed Google Play page in the Microsoft Intune admin center](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-draft-android-112/ZClientConnector-private-app-Managed-Google-Play-app-Lock_0.png)
- In the **Private app** section:
- **Title**: Enter a title for your file.
- **APK file**: Upload the APK file. Contact Zscaler Support for a private APK file.
- Click **Create**.
[See image.](#private-app)
[]![Private app details in the Microsoft Intune admin center](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-draft-android-112/ZClientConnector-private-app-upload-APK.png)
The app can take up to 10 minutes to publish and appear in private apps.
[See image.](#click-create)
[][]![Android apps list in Microsoft Intune admin center](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-draft-android-112/ZClientConnector-private-app-new-app.png)
- Select the app you have created from the Android apps list.
- (Optional) Click **Edit** next to **App information** and **Assignments** to make any changes to these sections.
[See image.](#app-info)
[![Edit properties for App Information and Assignments](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-draft-android-112/ZClientConnector-Private-App-Edit_0.png)
]
[]
- []On the **Review + create **tab, review the values and settings entered and save your settings.
[]To configure Always on VPN device restrictions for private apps, see [Configure Always On VPN](/unified/deploying-zscaler-client-connector-microsoft-intune-android#always-on-vpn).
[]To deploy Zscaler Client Connector to Microsoft Intune from the Google Play Store for Android devices that are not Enterprise enabled:
- In the Microsoft Intune admin center, click **Apps** in the left-side navigation.
[See image.](#wo-enterprise)
[]![Microsoft Intune admin center Apps page](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-doc-53347-doc-55060/android_w_o_enterprise_enabled_select_apps_page_2.png)
- Click **All apps**, and then click **Add**.
[See image.](#apps2)
[]![The All apps page in the Microsoft Intune admin center](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-doc-53347-doc-55060/android_wo_enterprise_enabled_apps_add_page_1.png)
- Select **Android store app** from the **Select app type** drop-down menu, and then click **Select**.
[See image.](#store-app)
[]![Select Android store app on the All apps page in the Microsoft Intune admin center](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-doc-53347-doc-55060/android_store_select_app_type_2.png)
- To add the app from the Android store app:[]
-
On the **App information** tab, provide the following Zscaler Client Connector details, and then click **Next**.
- **Name**: Enter `Zscaler Client Connector`.
- **Description**: Enter a relevant description for Zscaler Client Connector.
- **Publisher**: Enter `Zscaler Inc`.
- **Appstore URL**: Enter the following Google Play Store URL:
[https://play.google.com/store/apps/details?id=zscaler.com.zscaler](https://play.google.com/store/apps/details?id=zscaler.com.zscaler&hl=en_IN).
- **Minimum operating system**: Select **Android 8.0**.
The minimum operating system for Android on ChromeOS is **Android 6.0**.
- **Show this as a featured app in the Company Portal**: Select **Yes**.
[See image.](#add-app-not-enabled)
[]![The App information tab on the All apps page of the Microsoft Intune admin center](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-doc-53347-doc-55060/Microsoft_Intune_w-o_Android_Enterprise_Apps_Add-App_minimum_OS_Android_8.0_1.png)
- On the **Assignments **tab, select the group assignments for which you want to deploy Zscaler Client Connector, and then click **Next**. For more information on adding groups, refer to [Microsoft technical documentation](https://docs.microsoft.com/en-us/mem/intune/fundamentals/groups-add).
[See image.](#select-group-assignments)
[]![The Assignments tab on the All apps page of the Microsoft Intune admin center](/downloads/z-app/downloading-deployment/deploying-zscaler-app-microsoft-intune-android/android_store_assignments_page.png)
-
On the **Review + create** tab, review the values and settings entered, and then click **Create**. Zscaler Client Connector is pushed to the devices in the group that you selected.
[See image.](#review-create-tab2)
[]![Review + Create tab on All apps page of the Microsoft Intune admin center](/downloads/z-app/downloading-deployment/deploying-zscaler-app-microsoft-intune-android/android_store_review_create_page.png)
After Zscaler Client Connector is installed on users' devices, they must launch the app and log in to enroll in the Zscaler service.
[]To deploy Zscaler Client Connector to Microsoft Intune for Android devices as an APK file:
- [Configure using an App Package File](#app-package-file)
- [Configure Always On VPN (Optional)](#always-on-vpn)
- []In the Admin Portal, go to **Infrastructure **>** Common Resources **>** Client Connector Deployment **>** Platform Releases** and download the Zscaler Client Connector APK file from the **Registered Devices** tab.
[See image.](#registered-devices)
Contact Zscaler Support to enable the APK file link.
[]![Zscaler Client Connector Portal App Store page](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-doc-53347/Client_Connector_App_Store.png)
-
In the Microsoft Intune admin center, click **Apps** in the left-side navigation.
[See image.](#apps4)
[]![Microsoft Intune admin center page Apps option](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-doc-53347-doc-55060/android_apk_enterprise_enabled_select_apps_page_1.png)
- Click **All apps**, and then click **Add**.
[See image.](#apk-all-apps)
[]![Microsoft Intune admin center to select All apps](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-doc-53347-doc-55060/android_apk_enterprise_enabled_apps_add_page_1.png)
- Select **Line-of-business app** from the **Select app type** drop-down menu, and then click **Select**.
[See image.](#apk-line-bus-app)
[]![Microsoft Intune admin center to select App type](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-doc-53347-doc-55060/apkflie_select_app_type_page1.png)
- To add the app as an APK file:
- On the **App information** tab, click **Select app package file**.
[See image.](#apk-app-info)
[]![App information tab on All apps page to Search for App Package file](/downloads/z-app/downloading-deployment/deploying-zscaler-app-microsoft-intune-android/apkflie_select_app_package_file.png?1597236128)
- Upload the Zscaler Client Connector APK** **file, and then click **OK**.
[See image.](#apk-upload-file)
[]![ App information tab on All apps page to Upload App package file](/downloads/z-app/downloading-deployment/deploying-zscaler-app-microsoft-intune-android/apkflie_file_upload_page.png?1597236161)
-
Provide the following Zscaler Client Connector details, and then click **Next**.
- **Name**: Enter `Zscaler Client Connector`.
- **Description**: Enter a relevant description for Zscaler Client Connector.
- **Publisher**: Enter `Zscaler Inc`.
- **Minimum operating system**: Select **Android 8.0**.
- **Show this as a featured app in the Company Portal**: Select **Yes**.
[See image.](#enter-details)
[]![The App information tab on the All apps page of the Microsoft Intune admin center](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-doc-53347-doc-55060/Microsoft_Intune_apk_Android_Enterprise_Apps_Add-App_minimum_OS_Android_8.0_1.png)
- On the **Assignments **tab, select the group assignments for which you want to deploy Zscaler Client Connector, and then click **Next**. For more information on adding groups, see [Microsoft technical documentation](https://docs.microsoft.com/en-us/mem/intune/fundamentals/groups-add).
[See image.](#apk-assign-tab)
[]![Assignment page to Add group](/downloads/z-app/downloading-deployment/deploying-zscaler-app-microsoft-intune-android/apkflie_assignment_page.png)
- On the **Review + create** tab, review the values and settings entered, and then click **Create**. Zscaler Client Connector is pushed to the devices in the group that you selected.
[]
After Zscaler Client Connector is installed on users' devices, they must launch the app and log in to enroll in the Zscaler service.
[]Zscaler Client Connector can restrict the traffic and secure the device before enrollment if **Always ON VPN** is enabled on your organization's MDM for Zscaler app. After the app is enrolled, it intercepts the traffic and forwards it according to the policies in the Zscaler Client Connector Portal. To learn more, refer to [Android documentation](https://developer.android.com/work/dpc/network-telephony#about_always-on_vpn_connections).
- In the Microsoft Intune admin center, go to **Devices** > **Android**.
- Under **Android policies**, click **Configuration profiles**.
[See image.](#vpn1)
[]![Configuration profiles in Microsoft Intune](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-draft-android-112/ZClientConnector-VPN-Config-profiles.png)
- On the **Android Configuration profiles** page:
- Click **Create profile**.
- In the **Create a profile** section:
- **Platform**: Enter `Android Enterprise`.
- **Profile type**: Select **Device Restriction** from either the **Fully Managed, Dedicated, and Corporate-Owned Work Profile** or the **Personally-Owned Work Profiles **sections.
- Click **Create**.
[See image.](#vpn2)
[]![Create a profile screen](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-draft-android-112/ZClientConnector-VPN-Create-Profile.png)
- In the **Basics** section:
- **Name**: Enter a name.
- **Description**: (Optional) Enter a description.
- Click **Next**.
- In the **Configuration settings** section, expand the **Connectivity** section to complete the following steps and then click **Next**:
- **Always-on VPN**: Enable to allow Zscaler Client Connector to restrict the traffic and secure the device without enrollment.
- **VPN client**: Select **Custom**.
- **Package ID**: Enter your package ID (e.g., `zscaler.com.zscaler`).
[See image.](#vpn3)
[]![Configuration settings section](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-microsoft-intune-android-draft-android-112/ZClientConnector-VPN-Config-Settings.png)
- In the **Assignments** section, choose the users, groups, and devices for the profile.
- Click **Next**.
- In the **Review + create** section, review the summary, and click **Create**.