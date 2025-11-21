# Deploying Zscaler Client Connector with MaaS360 for iOS
Source: https://help.zscaler.com/zscaler-client-connector/deploying-zscaler-client-connector-maas360-ios
PDF: https://help.zscaler.com/pdf/com/en/1341036.pdf

This guide is for admins only. If you are an end user, contact your organization’s administrator for deployment-related details.
With IBM MaaS360 with Watson, you can deploy Zscaler Client Connector for iOS devices. Optionally, you can also configure Zscaler Client Connector with parameters to simplify the enrollment process for your users.For more information, refer to the IBM MaaS360 documentation.
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
- Enter [Zscaler configuration parameters](/zscaler-client-connector/supported-parameters-zscaler-client-connector-ios) and their corresponding values per your organization's needs. You can also use MaaS360 variables to automatically populate these fields.
![Configured key/value pairs for the Zscaler Client Connector](/downloads/z-app/downloading-deployment/deploying-zscaler-app-maas360-ios/GOV-maas360-iOS-7b.png?1597394254)
- Once you are finished making changes, click **Add**.
- Enter your admin password to confirm the changes.
![Confirming the changes for deploying Zscaler Client Connector](/downloads/z-app/maas360-ios-8.png)
Once Zscaler Client Connector is on users’ devices, they must launch the app and log in to enroll to the Zscaler service.