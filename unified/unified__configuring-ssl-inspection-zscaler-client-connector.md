# Configuring SSL Inspection for Zscaler Client Connector
Source: https://help.zscaler.com/unified/configuring-ssl-inspection-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1496331.pdf

When you enable [SSL inspection](/unified/about-ssl-inspection) for your Zscaler Client Connector devices, this allows the Zscaler service to decrypt and inspect HTTPS traffic to and from the browser to a device, and to and from the destination server. You can also exempt URLs from SSL inspection.
Depending on the platform, Zscaler Client Connector or your Mobile Device Management (MDM) solution installs the Zscaler SSL certificate required for SSL inspection.
Select from the following options for a description of each task:
- [Configuring SSL Inspection for Zscaler Client Connector](#configure-SSL-Zscaler-App)
- [Exempting URLs from SSL Inspection](#exempting-URLs-SSL)
- [Configuring Zscaler Client Connector to Install the Zscaler SSL Certificate](#configure-Zscaler-App-SSL-cert)
[]In the Admin Portal, you must enable the service to perform SSL inspection for Zscaler Client Connector users on each relevant platform. To learn more, see [Configuring SSL Inspection Policy](/unified/configuring-ssl-inspection-policy).
Location-specific SSL inspection settings are separate from Zscaler Client Connector SSL inspection settings. To learn more, see [Configuring Locations](/unified/configuring-locations).
[]
To exempt URLs from SSL inspection, you must first create a custom category for the URLs and then add the custom category to **URL Categories **in the Admin Portal. If you already have a custom category for bypassed URLs, edit the category and add the URLs.
- Apple recommends bypassing specific iOS URLs from SSL inspection. Refer to the[ Apple Support page](https://support.apple.com/en-au/101555).
- Google recommends bypassing specific URLs from SSL inspection. Refer to [Chrome Enterprise and Education Help](https://support.google.com/chrome/a/answer/6334001?hl=en&ref_topic=3504941#allowlist&zippy=%2Chostname-allowlist-for-chromeos-devices-using-android-apps-google-play-store).
Creating a Custom URL Category
To create a custom URL category in the Admin Portal:
- Go to **Policies > Access Control > Internet & SaaS** > **URL Categories**.
- Click **Add URL Category**.
- Enter a name for the category.
- Add the URLs to the **Custom URLs** field.
-
Click **Save** and activate the change.
[See image.](#url-category)
To learn more about creating a custom URL category, see [Configuring Custom URL Categories](/unified/configuring-custom-url-categories).
Adding the Custom Category to URL Categories
To add the custom category in the Admin Portal:
- Go to **Policies > Common Configuration > SSL/TLS Inspection > SSL/TLS Inspection Policy**.
- Select the SSL inspection policy you created.
- Under **Criteria**, select the URL categories you want to exempt from decryption from the **URL Categories** drop-down menu.
- Under **Action**, click **Do Not Inspect**.
-
Click** Save** and activate the change.
[See image.](#custom)
[]The SSL certificate allows the Zscaler service to perform SSL inspection on user traffic forwarded by the app. Any SSL exemptions you configure in the Admin Portal also apply.
(Optional) If you [upload your organization’s custom SSL certificate](/unified/uploading-custom-ssl-certificate-zscaler-client-connector), you can install the custom certificate instead.
Installing the Zscaler SSL Certificate on Device Platforms
**Install Zscaler SSL Certificate** is not supported on devices running macOS Big Sur (11) and later.
To install the Zscaler SSL certificate by device:
- [Windows, Linux, and macOS](#WindowsLinuxmacOS)
- [Android](#android)
- [iOS](#iOS)
[]In the Admin Portal, enable Zscaler Client Connector to automatically install the Zscaler SSL certificate on your users’ devices for Windows, Linux, and macOS.
- Go to **Infrastructure > Connectors > Client**.
- Under Platform Settings, select the operating system, and click to [add a policy](/unified/configuring-zscaler-client-connector-app-profiles) or select an existing policy to edit.
- Enable **Install Zscaler SSL Certificate**.
- Click **Save**.
[]For Android, Zscaler Client Connector does not automatically install the certificate. Zscaler recommends installing the root certificate using your MDM.
Zscaler Client Connector only installs certificates for Samsung devices that have administrator privileges. To install the certificate, go to the **More** window in Zscaler Client Connector and click **Install Certificates**.
For Android version 7.0 and later, Google prevents non-default certificate authorities from being trusted. Unless the third-party application developer explicitly allows it, the Zscaler certificate or any third-party certificate is not trusted.
[]For iOS, Zscaler Client Connector does not automatically install the certificate because Apple requires application-installed certificates to be untrusted by default. Zscaler recommends installing the root certificate using your MDM.
Events That Prompt Zscaler Client Connector to Install the Certificate
If a certificate is already deployed and you upload a new certificate, Zscaler Client Connector uses a native Windows method to install the certificate. The app automatically replaces the certificate if it’s new or different, but won’t change it if the same certificate already exists.
The Internet & SaaS service imports the certificate in the following situations:
- Upon enrollment
- If the admin modifies the app profile and the device checks in to download the new profile
- When Zscaler Client Connector updates
- When the user clicks **Update Policy** for Zscaler Client Connector
When these events occur, Zscaler Client Connector receives the certificate link from the Admin Portal and attempts to install the certificate.
To learn more about deploying SSL Inspection, see [Deploying SSL Inspection](/unified/deploying-ssl-inspection).
[]![URL Categories ZIA  Admin](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-ssl-inspection-zscaler-client-connector-doc-48136/add-URL-category-custom_URLs.png)
[]![Add an SSL Inspection Rule](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-ssl-inspection-zscaler-client-connector-doc-48136/ZIA-Add-SSL-Inspection-Rule.png)