# Configuring the Postman REST API Client
Source: https://help.zscaler.com/zia/configuring-postman-rest-api-client
PDF: https://help.zscaler.com/pdf/com/en/1400491.pdf

Zscaler supports the Windows, macOS, and Linux versions of the Postman REST API app. To learn more about the app and its features, refer to the [Postman documentation](https://learning.postman.com/docs/getting-started/introduction/).
If you already have Postman installed and configured, you can download the latest version of the cloud service API and Sandbox Submission API Postman collection files from any article within the [Reference Guide](/zia/activation).
[See image.](#try-in-postman-button)
The Sandbox Submission API uses a base URL that is different from that of the cloud service API. It also requires an API token. Make sure that both are set properly within Postman for your Zscaler cloud. To learn more, see [Getting Started](/zia/api-getting-started).
Installing and Configuring Postman for Windows, macOS, or Linux
To install and configure Postman:
- []Go to the [Postman website](https://www.postman.com/) and download the app for your OS (i.e., Windows, macOS, or Linux).
For this example, the 64-bit version of the Postman application running on Windows is used to illustrate the instructions.
- Install the app.
- After installation, open the app and log in using your account.
- Download the latest version of the cloud service API collection file from the [Reference Guide](/zia/activation).
- From the main window, click **Import**.
[See image.](#ImportButton_Img)
Alternatively, go to the application menu on the top-left corner and click **File** > **Import...**.
[See image.](#file-import-option)
- In the Import window that appears, select your .postman_collection file or drag the file to the selection area.
[See image.](#UploadFile_Img)
After the file is imported, a new folder with the name used within the Postman collection file (e.g.,** cloud service API**) is displayed within **Collections**.
- []Ensure that **No Environment** is selected in the environment drop-down menu on the top right, and then click the **Environment quick look** icon.
- Click **Add**.
[See image.](#EnvQuicklook_Img)
- On the **New Environment** tab that appears, complete the following steps:
- Enter a descriptive name for the environment (e.g., `Zscaler Test Environment`).
- Under **Variable**, enter `url`.
- For **Type**, leave as **default**.
- For **Initial Value**, enter `https://zsapi.``<Zscaler Cloud Name>``/api/v1`, where `<Zscaler Cloud Name>` is the cloud name provisioned for your organization by Zscaler (e.g., `zsapi.zscalerbeta.net`). To learn more, see [What Is My Cloud Name for ZIA?](/zia/what-my-cloud-name)
- Click **Save **and close the tab.
[See image.](#ManageEnv_Img)
Select the environment you configured (e.g., `Zscaler Test Environment`) from the environment drop-down menu on the top right. To learn more, refer to the [Postman documentation](https://learning.postman.com/docs/sending-requests/managing-environments/).
[See image.](#SelectEnv_Img)
[]Authenticating a Session in Postman
After installing and configuring the Postman app, authenticate a session.
- Log in to the ZIA Admin Portal using your API admin credentials. To learn more, see [Getting Started](/zia/api-getting-started#RetrieveAPIKey).
- Go to **Administration** > **Cloud Service API Security** > **Cloud Service API Key**.
- On the **Cloud Service API Key** tab, copy the **Key**.
- In the Postman app:
- []Click the **Settings** icon on the top right, and then choose **Settings**.
[See image.](#settings-option)
Alternatively, go to the application menu on the top-left corner and click **File** > **Settings**.
[See image.](#file-settings-option)
- Under the **General **tab, turn off **SSL certificate verification**.
[See image.](#DisableSSLCertVerify_Img)
- In the Postman collection you imported previously, select the **POST Authenticate** request.
[See image.](#authenticate-api-request)
- Go to the **Pre-request Script **tab and replace YourApiKey in the script with the **Key** you copied in step 3.
[See image.](#AuthenticateSess_Img)
- Go to the request's **Body** tab and replace the username and password with your API admin credentials.
[See image.](#AuthUserInfo_Img)
- Click **Send**.
If authentication is successful, a **Status 200 OK** message is returned, for example:
[See image.](#200OKMsg_Img)
Making an API Call in Postman
Make an API call using Postman. The following example shows how to look up categories for a specified list of URLs using /urlLookup:
- Make sure that you can [authenticate successfully](/zia/configuring-postman-rest-api-client#AuthenticationSteps).
- Go to **URL categories** > **POST URL lookup**.
Click the request's **Body** tab to view the list of reconfigured URLs for which the lookup operation must be performed. You can look up a maximum of 100 URLs per request, with each URL not exceeding 1024 characters.
- Click **Send**.
If the request is successful, you should receive a **Status 200 OK** message and a response **Body** that looks as follows:
[See image.](#URLLookup_Img)
You can see the `JSESSIONID` under the **Cookies **tab.
[See image.](#JSESSIONID_Img)
By default, the session is terminated after 5 minutes and reauthentication is required.
[]![Try In Postman button location in Zscaler API Reference Guide](/downloads/zia/zia-api/api-developer-reference-guide/configuring-postman-rest-api-client/download-postman-collection.png)
[]![Import button on Postman app](/downloads/zia/zia-api/api-developer-reference-guide/configuring-postman-rest-api-client/postman-collection-import-button_0.png)
[]![Upload File to Import in Postman](/downloads/zia/zia-api/api-developer-reference-guide/configuring-postman-rest-api-client/import-window_0.png)
[]![Environment Quick Look Menu in Postman ](/downloads/zia/zia-api/api-developer-reference-guide/configuring-postman-rest-api-client/add-new-environment_0.png)
[]![Add Environment and Set Variable and Value for cloud services API in Postman](/downloads/zia/zia-api/api-developer-reference-guide/configuring-postman-rest-api-client/configure-environment-variables_0.png)
[]![Select an Environment in Postman](/downloads/zia/zia-api/api-developer-reference-guide/configuring-postman-rest-api-client/select-environment_0.png)
[]![Disable SSL Certificate Verification in Postman](/downloads/zia/zia-api/api-developer-reference-guide/configuring-postman-rest-api-client/ssl-certificate-verification-setting_0.png)
[]![Adding API Key to POST /authenticateSession request](/downloads/zia/zia-api/api-developer-reference-guide/configuring-postman-rest-api-client/replace-api-key_0.png)
[]![Adding API user information to /authenticateSession request in Postman](/downloads/zia/zia-api/api-developer-reference-guide/configuring-postman-rest-api-client/replace-admin-credentials_0.png)
[]![/authenticateSession Response - Status 200 OK](/downloads/zia/zia-api/api-developer-reference-guide/configuring-postman-rest-api-client/authenticated-session-reponse_0.png)
[]![/urlLookup Response - 200 OK](/downloads/zia/zia-api/api-developer-reference-guide/configuring-postman-rest-api-client/url-lookup-request.png)
[]![Postman Interceptor Enabled - JSESSIONID in Cookie](/downloads/zia/zia-api/api-developer-reference-guide/configuring-postman-rest-api-client/jsessionid-cookie_0.png)
[]![Option to choose Postman app Settings from the File menu](/downloads/zia/zia-api/api-developer-reference-guide/configuring-postman-rest-api-client/file-settings-option_0.png)
[]![Import option in the File menu of the Postman app](/downloads/zia/zia-api/api-developer-reference-guide/configuring-postman-rest-api-client/file-import-option_0.png)
[]![Cloud service API authentication request in Postman app](/downloads/zia/zia-api/api-developer-reference-guide/configuring-postman-rest-api-client/authenticate-request_0.png)
[]![Postman app settings button in the Postman app](/downloads/zia/zia-api/api-developer-reference-guide/configuring-postman-rest-api-client/postman-app-settings-icon_0.png)

## Contents
- **API Developer & Reference Guide**
  - [Getting Started](/zia/getting-started-zia-api)
  - [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client)
  - [Understanding Rate Limiting](/zia/understanding-rate-limiting)
  - [API Response Codes and Error Messages](/zia/api-response-codes-and-error-messages)
  - **Reference Guide**
    - [3rd-Party App Governance API](/zia/3rd-party-app-governance-api)
    - [Sandbox Submission API](/zia/sandbox-submission-api)
    - [Activation](/zia/activation)
    - [Admin Audit Logs](/zia/admin-audit-logs)
    - [Admin & Role Management](/zia/admin-role-management)
    - [Advanced Settings](/zia/advanced-settings)
    - [Advanced Threat Protection Policy](/zia/advanced-threat-protection-policy)
    - [Alerts](/zia/alerts)
    - [API Authentication](/zia/api-authentication)
    - [Authentication Settings](/zia/authentication-settings)
    - [Bandwidth Control & Classes](/zia/bandwidth-control-classes)
    - [Browser Control Policy](/zia/browser-control-policy)
    - [Browser Isolation](/zia/browser-isolation)
    - [Cloud Applications](/zia/cloud-applications)
    - [Cloud App Control Policy](/zia/cloud-app-control-policy)
    - [Cloud Nanolog Streaming Service (NSS)](/zia/cloud-nanolog-streaming-service-nss)
    - [Data Loss Prevention](/zia/data-loss-prevention)
    - [Device Groups](/zia/device-groups)
    - [DNS Control Policy](/zia/dns-control-policy)
    - [End User Notifications](/zia/end-user-notifications)
    - [Event Logs](/zia/event-logs)
    - [File Type Control Policy](/zia/file-type-control-policy)
    - [Firewall Policies](/zia/firewall-policies)
    - [Forwarding Control Policy](/zia/forwarding-control-policy)
    - [FTP Control Policy](/zia/ftp-control-policy)
    - [Intermediate CA Certificates](/zia/intermediate-ca-certificates)
    - [IoT Report](/zia/iot-report)
    - [IPS Control Policy](/zia/ips-control-policy)
    - [Location Management](/zia/location-management)
    - [Malware Protection Policy](/zia/malware-protection-policy)
    - [Mobile Malware Protection Policy](/zia/mobile-malware-protection-policy)
    - [NAT Control Policy](/zia/nat-control-policy)
    - [Organization Details](/zia/organization-details)
    - [PAC Files](/zia/pac-files)
    - [Policy Export](/zia/policy-export)
    - [Remote Assistance Support](/zia/remote-assistance-support)
    - [Rule Labels](/zia/rule-labels)
    - [SaaS Security API](/zia/saas-security-api)
    - [Sandbox Policy & Settings](/zia/sandbox-policy-settings)
    - [Sandbox Report](/zia/sandbox-report)
    - [Security Policy Settings](/zia/security-policy-settings)
    - [Service Edges](/zia/service-edges)
    - [Shadow IT Report](/zia/shadow-it-report-api)
    - [SSL Inspection Policy](/zia/ssl-inspection-policy)
    - [System Audit Report](/zia/system-audit-report)
    - [Time Intervals](/zia/time-intervals)
    - [Traffic Capture Policy](/zia/traffic-capture-policy)
    - [Traffic Forwarding](/zia/traffic-forwarding-0)
    - [URL Categories](/zia/url-categories)
    - [URL Filtering Policy](/zia/url-filtering-policy)
    - [URL & Cloud App Control Policy Settings](/zia/url-cloud-app-control-policy-settings)
    - [User Authentication Settings](/zia/user-authentication-settings)
    - [User Management](/zia/user-management)
    - [Workload Groups](/zia/workload-groups)
    - [API Rate Limit Summary](/zia/api-rate-limit-summary)
  - **Working with APIs**
    - [Generating Admin Audit Logs Using API ](/zia/generating-admin-audit-logs-using-api)
    - [Managing Admins and Roles Using API ](/zia/managing-admins-and-roles-using-api)
    - [Managing Intermediate CA Certificates Using API](/zia/managing-intermediate-ca-certificates-using-api)
    - [Managing Locations Using API](/zia/managing-locations-using-api)
    - [Obtaining Sandbox Reports Using API](/zia/obtaining-sandbox-reports-using-api)
    - [SD-WAN Integrations Using API](/zia/sd-wan-integrations-using-api)
    - [Configuring VPN Credentials for IPSec Tunnels Using API](/zia/configuring-vpn-credentials-ipsec-tunnels-using-api)
    - [Managing URL Allowlist and Denylist Using API](/zia/managing-url-allowlist-and-denylist-using-api)
    - [Configuring URL Categories Using API](/zia/configuring-url-categories-using-api)
    - [Managing Users Using API](/zia/managing-users-using-api)