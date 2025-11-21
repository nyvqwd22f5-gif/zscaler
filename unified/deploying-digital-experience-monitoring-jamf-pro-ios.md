# Deploying Digital Experience Monitoring with Jamf Pro for iOS
Source: https://help.zscaler.com/unified/deploying-digital-experience-monitoring-jamf-pro-ios
PDF: https://help.zscaler.com/pdf/com/en/1530894.pdf

This guide is for admins only. If you are an end user, contact your organization’s administrator for deployment-related details.
With Jamf Pro, you can configure and deploy Digital Experience Monitoring for iOS devices. Before following this guide, ensure that Zscaler Client Connector is installed on your device. To learn more, see [Deploying Zscaler Client Connector with Jamf Pro for iOS](/unified/deploying-zscaler-client-connector-jamf-pro-ios).
This deployment guide applies to devices running iOS version 16 and later.
- [Create and Push Per App Content Filter Configuration Profile from Jamf Pro](#content-filter-section)
- [Create and Push Associated App from Jamf Pro](#associated-per-app)
[]To create and push Per App content filter configuration profile from Jamf Pro, follow these steps:
- In the Jamf Pro portal, click **Configuration Profiles** under the **Devices** section.
- Click **New**.
[See image.](#config-profile)
[]![Configuration profiles](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zdx-jamf-pro-ios/ZSclientconnector-zdx-jamf-config-profiles.png)
- In the **General** section, enter a **Name** for the configuration profile and add a **Description**.
[See image.](#general)
[]![Fill in the details in the general section](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zdx-jamf-pro-ios/ZSclientconnector-zdx-jamf-general_2.png)
- From the menu on the left, scroll down to the **Content Filter **section.
- **Filter Name**: Enter a name for the filter.
- **Filter type**: Select **Plug-in**.
- **Identifier**: Enter `**com.zscaler.zscaler**`
- **Organization**: Enter `**Zscaler**`
- **Per-app networking**: Select **Enable**
- **Socket-filter**: Select **Enable**
[See image.](#content-filter)
[]![Fill in the details in the content filter section](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zdx-jamf-pro-ios/ZSclientconnector-zdx-jamf-content-filter_1.png)
- Click **Save.**
Your profile is created. To push the Per App Content filter configuration profile, follow these steps:
- Open the configured content filter profile that you just created.
- Go to the **Scope** section.
- Click **Edit**.
[See image.](#edit-app)
[]![Click Edit to add the device](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zdx-jamf-pro-ios/ZSclientconnector-zdx-jamf-edit-config-profile_1.png)
- Click **+Add** to see a list of enrolled devices.
[See image.](#click-add)
[]![Click add to see list of enrolled devices](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zdx-jamf-pro-ios/ZSclientconnector-zdx-jamf-click-add_1.png)
- Click **Add** to add a newly enrolled device. Select the device and **Save** the configuration.
[See image.](#add-app)
[]![Add a device and click save](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zdx-jamf-pro-ios/ZSclientconnector-zdx-jamf-add-device_1.png)
- Choose the redistribution option that applies to your organization and click **Save**.
[See image.](#redistribute)
[]![Choose a redistribution option](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zdx-jamf-pro-ios/ZSclientconnector-zdx-jamf-redistribution-options_0.png)
[]To create and push an Associated App from Jamf Pro, follow these steps:
- From the menu on the left, under** Devices**, click **Mobile Device Apps** and click**+New**.
[See image.](#mobile-device)
[]![Mobile device apps](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zdx-jamf-pro-ios/ZSclientconnector-zdx-mobile-device-apps-new.png)
- For **Choose an App Type**, select **App Store app or apps purchased in volume**.
- Click **Next**.
[See image.](#choose-type)
[]![App type](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zdx-jamf-pro-ios/ZSclientconnector-zdx-mobile-device-app-type.png)
- Search for the associated app. You can choose any app in the App Store.
- Choose a country or region.
- Click **Next**.
[See image.](#search-app)
[]![Search an app](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zdx-jamf-pro-ios/ZSclientconnector-zdx-mobile-device-app-search.png)
- In the **Add App** section, select the app from the list and click **Add**.
- Click **Enter Manually** and fill in the details related to the associated app.
[See image.](#mobile-device-general)
[]![General section](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zdx-jamf-pro-ios/ZSclientconnector-zdx-mobile-device-app-general_0.png)
- Within the **General** tab, for the **Per-App Content Filter** section, select the content filter you created earlier.
[See image.](#mobile-device-per-app)
[]![Fill the details in the general section of the Mobile Device App](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zdx-jamf-pro-ios/ZSclientconnector-zdx-mobile-device-app-general-per-app-content.png)
- In the **Self Service **tab, provide the **Button Name** and add an optional **Description**.
- Click **Save**.
[See image.](#self-service-section)
[]![Self service section](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zdx-jamf-pro-ios/ZSclientconnector-zdx-mobile-device-app-self-service_0.png)
- Go to the **Scope** section to assign devices and click **Save**.
To verify that the profile is pushed to the device correctly, go to device **Settings** >**General** > **VPN & Device Management** > **Content Filter**. The Zscaler Content Filter shows as **running**. Clicking the filter shows the apps associated with the filter.
[See image.](#content-filter-running)
[]![Content filter is running](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zdx-jamf-pro-ios/ZSclientconnector-zdx-content-filter-status_0.png)
Open the Zscaler Client Connector app on your iOS device to see the Digital Experience Monitoring service running.
[See image.](#zdx-on-app)
[]![ZDX on Client Connector](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zdx-jamf-pro-ios/ZscalerClientConnector-ZDX-app.jpg)