# Deploying Zscaler Client Connector with Workspace ONE UEM for Android
Source: https://help.zscaler.com/zscaler-client-connector/deploying-zscaler-client-connector-workspace-one-uem-android
PDF: https://help.zscaler.com/pdf/com/en/1358846.pdf

This guide is for admins only. If you are an end user, contact your organization’s administrator for deployment-related details.
With Omnissa Workspace ONE Unified Endpoint Management (UEM), you can configure and deploy Zscaler Client Connector for Android devices by pushing the app:
- From Google Play with* *Android Enterprise enabled
- From Google Play without Android Enterprise enabled
- As an APK file
If you deploy Zscaler Client Connector from Google Play *with* Android Enterprise enabled, you can preconfigure Zscaler Client Connector with [parameters](/zscaler-client-connector/parameters-guide-zscaler-client-connector-android-and-android-chromeos). This allows you to simplify the Zscaler Client Connector enrollment process for your users. If you deploy Zscaler Client Connector from Google Play *without* Android Enterprise enabled or as an APK file, you cannot preconfigure Zscaler Client Connector.
The version used for the following steps is Workspace ONE UEM 25.6.111.0 (2506).
- [Deploying Zscaler Client Connector from Google Play](#googleplay-without-android-enterprise-enabled)
- [Deploying Zscaler Client Connector as an APK file](#as-an-apk-file)
[]To deploy Zscaler Client Connector to Workspace ONE UEM for Android devices from the Google Play Store:
- In the Workspace ONE UEM portal, go to **Resources **> **Apps** > **Native Apps** > **Public **and then click **Add Application**.
[See image.](#native)
- On the **Add Application** page, configure the following options, and then click **Search**.
- **Managed By**: Enter `Zscaler`.
- **Platform**: Select **Android**.
- **Source**: The option **Search the App Store** is enabled by default.
- **Name**: Enter `Zscaler Client Connector`.
[See image.](#add_app)
- Select **Zscaler Client Connector** from the Google Play Store.
[See image.](#google_play_store)
- Click **Approve** to review and accept Zscaler Client Connector permissions.
- Select **Keep approved when app requests new permissions** to automatically approve all future updates to the app.
- Click **Select **to select Zscaler Client Connector from the Google Play Store.
[See image.](#add_application_approved)
- On the **Details** tab, enter `Zscaler Client Connector`** **in the** Name** field, and then click **Save & Assign**. Zscaler Client Connector is added to your Workspace ONE UEM portal.
[See image.](#details_tab)
- Select **Zscaler Client Connector **for the Android platform, and then click **Assign**.
[See image.](#assign)
- On the **Zscaler Client Connector - Assignment **page, click **Add Assignment **and then click** Save**.
[See image.](#add_assignment)
- On the **Distribution** tab, configure the following options and then click **Create**.
- **Name**: Enter `Zscaler Client Connector`.
- **Description**: Enter a relevant description for the app.
- **Assignment Groups**: Select a group or groups for which you want to assign the app.
- **App Delivery Method**: Select the app delivery method, **Auto **or** On Demand**, based on your requirements.
- **Pre-release Version**: Select **None** from the drop-down menu.
[See image.](#distrib1)
- (Optional) On the **Application Configuration** tab:
If you have Android Enterprise enabled, you can use [Zscaler parameters](/zscaler-client-connector/parameters-guide-zscaler-client-connector-android-and-android-chromeos) to preconfigure Zscaler Client Connector. Preconfiguring Zscaler Client Connector allows you to remove steps from the user enrollment process (e.g., allowing users to skip the enrollment page or the cloud selection prompt on Zscaler Client Connector). You can use Omnissa variables for some of the Zscaler parameters, for example, userName. To learn more, refer to your MDM's documentation.
To preconfigure Zscaler Client Connector:
- Enable **Send Configuration**.
- Add [Zscaler configuration parameters](/zscaler-client-connector/parameters-guide-zscaler-client-connector-android-and-android-chromeos) and their corresponding values per your organization's needs.
- Click **Create**.
[See image.](#parameters)
- On the **Zscaler Client Connector - Assignment** page, review the values and settings entered, and then click **Save**.** **Zscaler Client Connector is pushed to the devices in the group or groups that you selected.
[See image.](#assignment)
After Zscaler Client Connector is installed on users’ devices, they must launch the app and log in to [enroll](/zscaler-client-connector/enrolling-zscaler-service-zscaler-client-connector) in the Zscaler service.
[]To deploy Zscaler Client Connector to Workspace ONE UEM for Android devices as an APK file:
- From the Zscaler Client Connector Portal, go to **Administration **> **Client Connector App Store** and download the Zscaler Client Connector APK file from the **Registered Devices** > **Android **tab.
Contact Zscaler Support to enable the APK file link.
[See image.](#store)
- On the Workspace ONE UEM portal, go to **Resources** > **Apps** > **Native Apps** > **Internal** and select **Application File **from the **Add** drop-down menu.
[See image.](#application_file)
- On the **Add Application** page:
- **Organization Group ID**: Enter `Zscaler`.
- **Application File**: Click** Upload**.
[See image.](#add_application)
- On the **Add** page, select **Choose File** to upload the Zscaler Client Connector APK file from your local file, and then click **Save**.
[See image.](#upload_APK)
- Click **Continue** on the **Add Application** page.
[See image.](#APK_file_continue)
- On the **Details** tab, configure the following options and then click **Save & Assign**.
- **Name**: Enter `Zscaler Client Connector`.
- **Minimum OS**: Select **Android 8.0**.
The minimum operating system for Android on ChromeOS is **Android 6.0**.
[See image.](#minOS)
- On the **Zscaler Client Connector - Assignment **page, click **Add Assignment**.
[See image.](#add_ass)
- On the **Distribution** tab, configure the following options and then click **Create**.
- **Name**: Enter `Zscaler Client Connector`.
- **Description**: Enter a relevant description for the app.
- **Assignment Groups**: Select a group or groups for which you want to assign the app.
- **Deployment Begins**: Set a date and a time for the deployment to start based on your requirements.
- **App Delivery Method**: Select the app delivery method as **Auto **or** On Demand** based on your requirements.
[See image.](#distrib_tab)
- On the **Zscaler Client Connector - Assignment** page, review the values and settings entered, and then click **Save**.** **Zscaler Client Connector is pushed to the devices in the group or groups that you selected.
[See image.](#assngmt)
After Zscaler Client Connector is installed on users’ devices, they must launch the app and log in to [enroll](/zscaler-client-connector/enrolling-zscaler-service-zscaler-client-connector) in the Zscaler service.
[]![List View in Omnissa Workspace One UEM for Android](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-android/Omnissa_add_application.png)
[]![Omnissa Workspace ONE UEM portal Add Application Window](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-android/Omnissa_add_application_search_0.png)
[]![Select Zscaler Client Connector from the Google Play Store](/downloads/z-app/downloading-deployment/deploying-zscaler-app-airwatch-android/airwatch_workspaceone_uem_add_application_googleplaystore.png?1599044108)
[![Omnissa Workspace ONE UEM portal select Zscaler Client Connector to add the app to the portal](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-android/Omnissa_ZCC_Select.png)
]
[]
[![Workspace ONE UEM portal App Configuration Details tab](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-android/Omnissa_uem_details_tab.png)
]
[]
[][![Screenshot of Omnissa Workspace ONE UEM portal selecting Assign](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-android/workspaceone_uem_Select_Assign.png)
]
[![Workspace ONE UEM portal select Add Assignment for app assignments](/downloads/tech-pubs-drafts/client-connector-draft-articles/zscaler-client-connector-connection-status-errors-doc-55700/Omnissa_add_assignment_from_assignment_page_Save.png)
]
[]
[![Omnissa Workspace ONE UEM portal Distribution tab for app assignments](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-android/Omnissa_Distribution_Create.png)
]
[]
[![Omnissa Workspace ONE UEM portal Application Configuration tab](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-android/Omnissa_Workspace_One_parameters.png)
]
[]
[![Omnissa Workspace ONE UEM portal Assignment page to review app Assignments](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-android/Omnissa_review_assingments.png)
]
[]
![Zscaler Client Connector Download Link in App Store](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-android/Client_Connector_App_Store.png)
[]
[]
[![Select Application File from Omnissa Workspace ONE UEM portal](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-android/Omnissa_application_file.png)
][][]
![Omnissa Workspace ONE UEM portal Add Application page](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-android/Omnissa_apk_add_application_page.png)
[]
![Omnissa Workspace ONE UEM portal Add page to upload app APK file](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-android/airwatch_workspaceone_uem_apkfile_upload_apkfile_add_page.png)
[]
[]
![Workspace ONE UEM portal app APK file uploaded to Add Application page](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-android/Omnissa_APK_File_Continue.png)
[]
![Omnissa Workspace ONE UEM portal Details tab](/downloads/zscaler-client-connector/monitoring-usage/device-states-enrolled-devices/Omnissa_min_os.png)
[]
![Omnissa Workspace ONE UEM portal Add Assignment page](/downloads/z-app/downloading-deployment/deploying-zscaler-app-airwatch-android/airwatch_workspaceone_uem_apkfile_add_assignment_page.png?1597074295%0D%20<a%20class=)
[]
![Omnissa Workspace ONE UEM portal Distribution tab](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-android/Omnissa_distrib_tab.png)
[]
![Workspace ONE UEM portal Assignment page to review app Assignments](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-android/Omnissa_apk_assignment.png)
[]