# Deploying Zscaler Client Connector with MobileIron for iOS
Source: https://help.zscaler.com/zscaler-client-connector/deploying-zscaler-client-connector-mobileiron-ios
PDF: https://help.zscaler.com/pdf/com/en/1395496.pdf

This guide is for admins only. If you are an end user, contact your organization’s administrator for deployment-related details.
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
- Under **Apple Managed App Settings**, click **Add** and enter [Zscaler configuration parameters](/zscaler-client-connector/supported-parameters-zscaler-client-connector-ios) and their corresponding values per your organization's needs.
![Configuration setup and adding configuration keys](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-mobileiron-ios/mobileIron-configuration-keys.png)
[]To configure custom settings payload with XML code for an iOS device profile:
- In the MobileIron Admin Portal, go to **Configurations**.
- In the OS Version section, select **iOS**.
- From the options on the right, click **Custom**.
![Adding configurations and OS versions](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-mobileiron-ios/mobileIron-select-custom-and-iOS_1.png)
- Provide a name for the profile and upload your .mobileconfig file.
![Create custom configuration screen](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-mobileiron-ios/mobileIron-add-name-upload-file.png)
- You can use the [ZscalerSample.mobileconfig](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-mobileiron-ios/zscalersample.mobileconfig) file as a starting template and edit [Zscaler configuration parameters](/zscaler-client-connector/supported-parameters-zscaler-client-connector-ios) and their corresponding values per your organization's needs.
- In the **Distribute** section, configure the distribution settings.
![Configure distribute settings screen](/downloads/z-app/downloading-deployment/deploying-zscaler-client-connector-mobileiron-ios/mobileIron-configure-distribute-settings.png)
- Click **Done**.
Users must open Zscaler Client Connector once for the configurations to be applied for the first time.