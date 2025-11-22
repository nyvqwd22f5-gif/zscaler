# Deploying Zscaler Client Connector with Google Workspace for Android
Source: https://help.zscaler.com/zscaler-client-connector/deploying-zscaler-client-connector-google-workspace-android
PDF: https://help.zscaler.com/pdf/com/en/1532018.pdf

This guide is for admins only. If you're an end user, contact your organization’s administrator for deployment-related details.
With Google Workspace, you can distribute App Store apps, including apps purchased in volume, to mobile devices. After an app is distributed, you can use Google Workspace to manage future updates to Zscaler Client Connector. You must have the required license for managing Android devices before deployment.
This article contains terms specific to the Google Workspace. To learn more, refer to [Google Workspace Admin documentation](https://support.google.com/a/answer/6328701?sjid=6371310950853617416-NC).
To deploy Zscaler Client Connector with Google Workspace, you must add and manage public apps with Google Workspace:
- Log in to the Google Admin console.
-
In the left-side navigation, go to **Apps** > **Web and mobile apps** > **Add App**. Select **Add private Android app**.
[See image.](#add-private-android)
-
In the left-side navigation, click **Search Play Store **and enter `Zscaler Client Connector` in the **Search** field.
[See image.](#search_play_store)
-
Click **Select**.
[See image.](#selectZCC)
You're automatically redirected to Apps > Web and mobile apps > Zscaler Client Connector, where you can configure app settings. Click **View details **in the **User access **section.
[See image.](#redirect)
-
Select **Make this app available to users in this organizational unit**.** **Click **Save** and collapse the **User access** section.
[See image.](#useraccess)
- In the **Settings **section, click **Learn more** and select the following values for each setting. When finished, collapse the **Settings** section.
- **Access method: Force install **or **Available**
- **Prevent users from uninstalling the app**: **OFF**
- **Allow users to add widgets to homescreen**: **ON **or **OFF**
- **Use as the** **always-on VPN** **app**: **ON**
- **Managed configuration:** **IdP**
[See image.](#settings)
- In the **Runtime permissions **section, select **Allow** for the **Contacts **feature if [**Zscaler Client Connector Portal as IdP**](/zia/adding-zscaler-client-connector-portal-idp)** **is the preferred authentication type**. **Click **Save** and collapse the **Runtime permission**s section.
[See image.](#runtime)
- In the **Managed configurations **section, enter the following JSON format:
``{`
`"userDomain":"<org’s_domain>",`
`"cloudName":"zscalerone",`
`"autoEnrollWithMDM":"1",`
`"deviceToken":"<token_value>",`
`"externalDeviceId":"${DEVICE_SERIAL_NUMBER}"`
`}``
[See image.](#json)
- You can add [Zscaler parameters](/zscaler-client-connector/parameters-guide-zscaler-client-connector-android-and-android-chromeos) to the JSON format based on your organization's needs and click **Save**.
[]![Google Admin Console Add Private app in Apps > Web and Mobile Apps](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-google-workspace-android-doc-59336/Google_Admin_Console_Apps_Add%20Private%20Android%20App.png)
[]![Google Admin Console Search Play Store](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-google-workspace-android-doc-59336/Google_Admin_Console_Search_Play_Store.png)
[]![Select Zscaler Client Connector in the Google Play Store](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-google-workspace-android-doc-59336/Google_Admin_Console_Select_Client_Connector.png)
[]![Image]()
![Google Admin Console User Access View Details link](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-google-workspace-android-doc-59336/Google_Admin_Console_User_Access_View_Details.png)
[]![Google Admin Console User Access](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-google-workspace-android-doc-59336/Google_Admin_Console_User%20Access.png)
[]![Google Admin Console Settings page](/downloads/zscaler-client-connector/downloading-deployment/deploying-zscaler-client-connector-google-workspace/deploying-zscaler-client-connector-google-workspace-android/Google_Admin_Console_Settings_1.png)
[]![Google Admin Console Runtime permissions  allow app to access contacts and profiles](/downloads/zscaler-client-connector/downloading-deployment/deploying-zscaler-client-connector-google-workspace/deploying-zscaler-client-connector-google-workspace-android/Contact_Pemission.png)
[]![Google Admin Console enter a JSON value](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-google-workspace-android-doc-59336/Google_Admin_Console_Enter_JSON_cropped.png)