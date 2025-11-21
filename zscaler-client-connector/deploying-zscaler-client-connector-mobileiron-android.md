# Deploying Zscaler Client Connector with MobileIron for Android
Source: https://help.zscaler.com/zscaler-client-connector/deploying-zscaler-client-connector-mobileiron-android
PDF: https://help.zscaler.com/pdf/com/en/1341011.pdf

This guide is for admins only. If you are an end user, contact your organization’s administrator for deployment-related details.
With MobileIron Unified Endpoint Management (UEM), you can configure and deploy Zscaler Client Connector for Android devices. Before deploying Zscaler Client Connector, you must first enable the Android Enterprise feature for MobileIron UEM. For more information, refer to the [MobileIron documentation](https://help.ivanti.com/mi/help/en_us/CORE/11.1.0.0/dmga/Content/DMGfiles/Android_enterprise_Overv.htm).
The following deployment procedure is based on MobileIron Core 10.1.
To configure and deploy Zscaler Client Connector to MobileIron for Android devices:
- In the MobileIron Admin Portal, click **Apps** from the top menu.
![Navigating to the apps page to import the Zscaler Client Connector](/downloads/z-app/mobileiron-1.png)
- Click **Add** to import Zscaler Client Connector to the **App Catalog**.
![mobileiron-20.png](/downloads/z-app/mobileiron-20.png)
- Click **Google Play**, and then search for `Zscaler Client Connector`.
![Searching for the Zscaler Client Connector](/downloads/z-app/mobileiron-3.png)
- Select **Zscaler Client Connector** from the list, and then click **Next**.
![Selecting the Zscaler Client Connector](/downloads/z-app/mobileiron-4.png)
- (Optional) Modify the **Description** and select a **Category**. Click **Next**.
![Details for the Zscaler Client Connector](/downloads/z-app/mobileiron-5.png)
- In the **Android Enterprise (All Modes)** section, enable the **Install this app for Android enterprise** option.
![Enabling Zscaler Client Connector for Android Enterprise](/downloads/z-app/mobileiron-6.png)
The **Configuration Choices** section appears.
This section appears only if you have already enabled Android Enterprise for MobileIron Core.
![Configuration choices for the Zscaler Client Connector](/downloads/z-app/mobileiron-7.png)
-
Under **Default Configuration for Zscaler Client Connector**, the following parameters are available to configure:
- **userDomain**: Your organization’s domain name, e.g., `safemarch.com`. If your instance has multiple domains associated with it, enter the primary domain for your instance.
- **cloudName**: The name of the cloud on which your organization is provisioned. For example, if your cloud name is zscalertwo.net, you would enter `zscalertwo`. To learn more, see [What is my cloud name for ZIA?](/zia/what-my-cloud-name-zia)
- **deviceToken**: The appropriate device token from the Zscaler Client Connector Portal, if you want to use the [Zscaler Client Connector Portal as an IdP](/zscaler-client-connector/using-zscaler-app-portal-identity-provider-idp).
- **userName**: The username for the user. For example, if the username is j.doe@safemarch.com, enter `j.doe`.
- **enableFips**: Enabling this option indicates that Zscaler Client Connector uses FIPS-compliant libraries for communication with Zscaler infrastructure. Enter `1` to enable or `0` to disable this option.
Enable this option only if you require FIPS-level security within your organization.
- **Ownership**:** **If you use the Ownership Variable device posture type, add the key `Ownership`. You can enter up to 32 alphanumeric characters in the **Configuration value** field. To learn more, see [Configuring Device Posture Profiles for ZPA](/zscaler-client-connector/configuring-device-posture-profiles-zpa).
- **autoEnrollWithMDM**: Use this parameter to determine auto-enrollment without user interaction, when using the Zscaler Client Connector Portal as an IdP. Select from the following options:
- Enter `0`** **to disable auto-enrollment.
- Enter `1`** **to have users always auto-enroll, even if they log out.
- Enter `2`** **for one-time auto-enrollment.
This option applies to only the ZIA-enabled accounts that are using Zscaler Client Connector Portal as an IdP. You must specify the parameters deviceToken, cloudName, and userDomain before enabling the autoEnrollWithMDM option.
- **customDNS**: By default, Zscaler Client Connector uses the device's DNS server. You can change the value to another DNS server using this setting. Enter the DNS IP address.
- **allowRunningOnRootedDevice**: This is set to 0 by default to restrict users from running Zscaler Client Connector on a rooted device. Enter `1` to allow users to run Zscaler Client Connector on a rooted device.
-
Click **Finish**.
![The Default Configuration for Zscaler Client Connector options](/downloads/z-app/downloading-deployment/deploying-zscaler-app-mobileiron-android/CustomDNS%20MobileIron.png)
You can now register the device (that has a work profile or is in Device Owner mode) and apply the Android Enterprise configuration. Zscaler Client Connector is automatically installed and configured.
Users must open Zscaler Client Connector once for the configurations to be applied for the first time.