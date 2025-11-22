# Deploying Zscaler Client Connector with Jamf Pro for iOS
Source: https://help.zscaler.com/zscaler-client-connector/deploying-zscaler-client-connector-jamf-pro-ios
PDF: https://help.zscaler.com/pdf/com/en/1402801.pdf

This guide is for admins only. If you are an end user, contact your organization’s administrator for deployment-related details.
With Jamf Pro, you can distribute App Store apps and apps purchased in volume to mobile devices. After an app is distributed, you can use Jamf Pro to manage future updates to Zscaler Client Connector.
The following deployment procedure is based on Jamf Pro 10.37.2.
- [Deploying Zscaler Client Connector from the App Store](#deploying-zscaler-client-connector-from-the-app-store)
- [Configuring a Custom Settings Profile](#configuring-custom-settings-profile)
[]To configure and deploy Zscaler Client Connector with Jamf Pro for iOS devices:
- In the Jamf Pro portal, click **Mobile Device Apps** from the left menu, and click **New**.
[See image.](#jamf1)
- In the **Choose Type** section, select **App Store app or apps purchased in volume** as the app type, and click **Next**.
[See image.](#jamf2)
- In the **Search or Upload** section, enter `Zscaler` in the search bar. Select your **App Store Country or Region** from the drop-down menu, and click **Next**.
[See image.](#jamf3)
Jamf Pro connects to the App Store and searches for all Zscaler apps.
- In the **Add App** section, select **iPad Apps**. If you are deploying to iPhones or iPods, select **iPhone & iPod touch Apps**.
[See image.](#jamf4)
- Click **Add** next to the Zscaler Client Connector app.
Jamf Pro automatically populates the **Display Name**,** Short Version**,** **and** Bundle Identifier **fields.
[See image.](#jamf5)
- Click **Scope** to determine iOS endpoints for policy deployment. Select the targets, limitations, and exclusions.
[See image.](#jamf6)
- Click **App Configuration** to configure Zscaler Client Connector before distributing it to mobile devices. Managed App Configuration is a set of key-value pairs in XML format used to configure iOS applications.
- In the **Preferences** box, copy and paste the following `<dict>`XML tag content and edit [Zscaler configuration parameters](/zscaler-client-connector/supported-parameters-zscaler-client-connector-ios) and their corresponding values per your organization's needs.
`<dict>
<key>cloudname</key>
<string>zscalerthree</string>
<key>ownership</key>
<string>Dattalabz</string>
<key>strictEnforcement</key>
<string>0</string>
<key>userDomain</key>
<string>dattalabz.com</string>
<key>excludeList</key>
<string>company.jamfcloud.com, aadcdn.msftauth.net,login.microsoftonline.com,oktacdn.com,samlsp.prod.zpath.net</string>
</dict>`
[See image.](#jamf7)
- Click **Save**, and then click **Publish**.
Zscaler Client Connector is now downloaded and installed on managed iOS devices. After installation, you must manually launch Zscaler Client Connector to complete enrollment.
[]To configure custom settings for an iOS device profile:
- In the Jamf Pro Admin Portal, go to **Devices**.
- Select **Configuration Profiles**.
[See image.](#jamf-config-profile)
- Click **Upload**.
[See image.](#click-upload)
- To add custom settings for your profile:
- Use a mobileconfig file. You can download the ZscalerSample.mobileconfig file below:
[Download ZscalerSample.mobileconfig file](/downloads/zscaler-client-connector/downloading-deployment/deploying-zscaler-client-connector-jamf-pro-ios/zscalersample.mobileconfig)
- Edit [Zscaler configuration parameters](/zscaler-client-connector/supported-parameters-zscaler-client-connector-ios) and their corresponding values per your organization's needs.
- Click **Upload** to upload your .mobileconfig file.
[See image.](#upload-mobile-config-file)
- In the **Scope **tab, assign the profile to the devices and the users.
[See image.](#assign-devices-and-users)
- Click **Save**.
[]![Mobile Device Apps section in the Jamf Pro portal ](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-jamf-pro-ios/Mobile-devices-apps-mainpage.png)
[]![Choose Type option in the Mobile Device Apps section](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-jamf-pro-ios/choose-type.png)
[]![Search or Upload section to search for Zscaler and add a country or region](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-jamf-pro-ios/enter-zscaler.png)
[]![Add App section for selecting the types of Apps](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-jamf-pro-ios/add-app.png)
[]![General information section](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-jamf-pro-ios/general.png)
[]![Scope section for determining iOS endpoints for policy deployment](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-jamf-pro-ios/scope.png)
[]![App configuration section for pasting the <dict> XML tag content](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-jamf-pro-ios/app-configuration.png)
[]![In devices, go to Jamf pro configuration profiles](/downloads/tech-pubs-drafts/client-connector-draft-articles/jamf-configure-custom-settings-profile-draft/Jamf-Devices-Config%20Profiles.png)
[]![Click Upload](/downloads/tech-pubs-drafts/client-connector-draft-articles/jamf-configure-custom-settings-profile-draft/Jamf-Click-Upload.png)
[]![Choose your mobile config file and click Upload](/downloads/tech-pubs-drafts/client-connector-draft-articles/jamf-configure-custom-settings-profile-draft/Jamf-Upload-Sample-Mobile-Config-File.png)
[]![In the Scope tab, assign profile to devices and users](/downloads/tech-pubs-drafts/client-connector-draft-articles/jamf-configure-custom-settings-profile-draft/Jamf-Scope.png)