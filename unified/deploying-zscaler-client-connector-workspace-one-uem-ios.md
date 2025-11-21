# Deploying Zscaler Client Connector with Workspace ONE UEM for iOS
Source: https://help.zscaler.com/zscaler-client-connector/deploying-zscaler-client-connector-workspace-one-uem-ios
PDF: https://help.zscaler.com/pdf/com/en/1358951.pdf

This guide is for admins only. If you are an end user, contact your organization’s administrator for deployment-related details.
With Workspace ONE Unified Endpoint Management (UEM), you can configure and deploy Zscaler Client Connector for iOS devices. The version used for the following steps is Workspace ONE UEM 20.7.0.0 (2007).
The first section explains how to push the Zscaler Client Connector application to your devices. The second section is optional, but allows you to pre-configure Zscaler Client Connector, which can simplify enrollment for end users.
- [Deploying Zscaler Client Connector from the App Store](#Deploying-ZscalerClientConnector-Appstore)
- [Configuring a Custom Settings Profile](#Configure-Custom-profile-deployment)
[]To deploy Zscaler Client Connector to Workspace ONE UEM for iOS devices:
- In the Workspace ONE UEM portal, go to **Apps & Books **>** Applications **>** Native **>** Public **and then click** Add Application**.
![Screenshot of Worksapce ONE UEM portal navigating to Add Application from the menu](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-ios-doc-50278/airwatch_workspaceonr_uen_ios_add_application_page.png)
- On the **Add Application** page, configure the following options and then click **Next**.
- **Platform**: Select **Apple iOS** from the **Platform** drop-down menu.
- **Source**: Click **Search App Store**.
- **Name**: Enter Zscaler Client Connector.
![Screenshot of Worksapce ONE UEM portal Add Application page to search for Zscaler Client Connector in app store](/downloads/z-app/downloading-deployment/deploying-zscaler-app-workspace-one-uem-ios/airwatch_workspaceonr_uen_ios_search_appstore_page.png?1601035588)
- Click **Select** to select Zscaler Client Connector from the App Store.
![Screenshot of Worksapce ONE UEM portal App Store page to select Zscaler Client Connector](/downloads/z-app/downloading-deployment/deploying-zscaler-app-workspace-one-uem-ios/airwatch_workspaceonr_uen_ios_selecting_zscalerapp_app_store.png)
- On the **Details** tab, enter Zscaler Client Connector in the** Name **field and then click **Save & Assign**.** **The **Zscaler Client Connector **is added to your Workspace ONE UEM portal.
![Screenshot of Worksapce ONE UEM portal App Configuration Details page](/downloads/z-app/downloading-deployment/deploying-zscaler-app-workspace-one-uem-ios/airwatch_workspaceonr_uen_ios_add_application_details_page.png?1599046644)
- Select **Zscaler Client Connector** for the Apple iOS platform from the Workspace ONE UEM portal, and then click **Assign**.
![Screenshot of Worksapce ONE UEM portal App Assignment page](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-ios-doc-50278/airwatch-workspaceone-ios-zscaler-app-assign.png)
- On the** Zscaler Client Connector - Assignments **page, click **Add Assignment**.
![Screenshot of Worksapce ONE UEM portal App Assignment page to add assignments](/downloads/z-app/downloading-deployment/deploying-zscaler-app-workspace-one-uem-ios/airwatch_workspaceonr_uen_ios_add_assignment_page.png?1597079569)
- On the **Distribution** tab:
- **Name**: Enter Zscaler Client Connector.
- **Description**: Enter a relevant description for the app.
- **Assignment Groups**: Select a group for which you want to assign the app.
- **App Delivery Method**: Select the app delivery method as **Auto **or** On-Demand** based on your requirements.
![Screenshot of Worksapce ONE UEM portal Distribution tab of Assignment page ](/downloads/z-app/downloading-deployment/deploying-zscaler-app-workspace-one-uem-ios/airwatch_workspaceonr_uen_ios_add_assignments_distributiontab.png)
- (Optional) On the **Application Configuration** tab:
You can use parameters to preconfigure Zscaler Client Connector. Preconfiguring Zscaler Client Connector allows you to remove steps from the user enrollment process (e.g., allowing users to skip the enrollment page or the cloud selection prompt on Zscaler Client Connector).
- Enable **Send Configuration**.
- Click **Add** and enter [Zscaler configuration parameters](/zscaler-client-connector/supported-parameters-zscaler-client-connector-ios) and their corresponding values per your organization's needs.
![Screenshot of Worksapce ONE UEM portal Application Configuration tab for app configurations](/downloads/z-app/downloading-deployment/deploying-zscaler-app-workspace-one-uem-ios/WorkspaceONE-app-config.png)
- Click **Create**.
- On the **Zscaler Client Connector - Assignment** page, review the values and settings entered, and then click **Save**.** **Zscaler Client Connector** **gets pushed to the devices in the group that you selected.
![Screenshot of Worksapce ONE UEM portal Assignment page to review app Assignments](/downloads/z-app/downloading-deployment/deploying-zscaler-app-workspace-one-uem-ios/airwatch_workspaceonr_uen_ios_add_assignments_review.png?1597079903)
After Zscaler Client Connector is installed on users’ devices, they must launch the app and log in to enroll in the Zscaler service.
[]Zscaler Client Connector automatically creates a VPN profile on the device if one is not already present. However, this means that the user is prompted to install the VPN profile and they can reject this installation. By pushing the VPN profile as Custom VPN, you can pre-deploy this VPN profile, which means not only is the user not prompted to install the profile, they also cannot remove the profile as it is pushed and managed by the MDM.
To configure custom settings payload with XML code for an iOS device profile:
- In the Workspace ONE UEM portal, go to **Devices** > **Profiles & Resources** > **Profiles** > **Add** > **Add Profile**.
[See image.](#VPN-add-profile)
[]![Screenshot of Worksapce ONE UEM portal Device Profiles page](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-ios-doc-50278/WorkspaceONE_custom_settings_profiles_page.png)
- On the **Add Profile** page, click **iOS** and then **Device Profile**.
[See image.](#vpn-add-profile-ios)
[]![Screenshot of Workspace ONE UEM portal Add Profile page to selection iOS platform](/downloads/z-app/downloading-deployment/deploying-zscaler-app-workspace-one-uem-ios/WorkspaceONE_custom_settings_add_profile_page.png)
- Name your profile and add an optional description.
[See image.](#vpn-name-profile)
[]![Name your profile](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-ios-doc-50278/ZSclientconnector-WorkspaceONE-VPN-name-profile.jpg)
- Scroll down to the **VPN** section. Click **Add** to add a new VPN profile.
- Under **Connection Info**:
- **Connection Name**: Enter a connection name. For example, `VPN Configuration`.
- **Connection Type**: From the drop-down menu, select **Custom**.
- **Identifier**: Enter `com.zscaler.zscaler`.
- **Server**: Enter a server name. For example, `VPN`.
For **Account**, **Disconnect on idle (sec)**, and **Per-App VPN Rules**, leave these settings they are.
[See image.](#vpn-connection-info)
[]![VPN profile](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-ios-doc-50278/ZSclientconnector-WorkspaceONE-VPN-settings.jpg)
- For **Custom Data**, enter [Zscaler configuration parameters](/zscaler-client-connector/supported-parameters-zscaler-client-connector-ios) and their corresponding values per your organization's needs.
- Under the **Authentication** section:
- **User Authentication**: From the drop-down menu, select **Certificate**.
- **Identity Certificate**: Select **None**.
- **Include User PIN**: Leave as disabled.
- **Enable VPN On Demand**: Enable this setting.
- **User new on-demand keys**: Enable this setting.
- **Prevent on demand override**: Enable this setting.
[See image.](#vpn-authentication)
[]![VPN authentication settings](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-ios-doc-50278/ZSclientconnector-WorkspaceONE-VPN-authentication.jpg)
Enabling the **User new on-demand keys** setting allows you to create an **On-Demand Rule**. When the end users access the internet, the traffic must go through Zscaler Client Connector. Therefore, as an admin, you should configure the **On-Demand Rule** settings. When the **On-Demand Rule** matches with the configured rules, the OS launches the Zscaler Client Connector VPN.
[See image.](#vpn-on-demand-rule)
[]![On-demand rule](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-ios-doc-50278/ZSclientconnector-WorkspaceONE-VPN-on-demand-rule.jpg)
- In the **On Demand Rule** section, configure the following settings:
- **Select interface type**: Choose **Any**.
- **Action if network matches**: Select **Connect**.
- Click **Next**.
- For the **VPN on Demand** section:
- **Match Domain or Host**: Leave this setting as it is.
- **On Demand Action**: From the drop-down menu, select **Always Establish**.
Under **Proxy**, for **Gateway Platform**, select **None**.
- Click **Next**.
- In the **Assignment** section:
- **Smart Group**: From the drop-down menu, select **All Devices (Zscaler)**.
- **Allow Exclusion**: Exclude any groups, if required.
- For **Deployment**, from the drop-down menu, select **Managed**.
For all of the other items in this section, choose settings as per your organization’s policies.
[See image.](#vpn-deployment)
[]![Deployment configuration](/downloads/tech-pubs-drafts/client-connector-draft-articles/deploying-zscaler-client-connector-workspace-one-uem-ios-doc-50278/ZSclientconnector-WorkspaceONE-VPN-application-deployment_0.png)
- Click **Save and** **Publish**.