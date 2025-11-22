# Configuring the Postman REST API Client
Source: https://help.zscaler.com/zpa/configuring-postman-rest-api-client
PDF: https://help.zscaler.com/pdf/com/en/1484901.pdf

Zscaler supports the Google Chrome app version and the standalone Windows, macOS, and Linux versions of the Postman REST API client.
The base URLs and references to `config.private.zscaler.com` within this article differ depending on your organization’s assigned cloud. To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
Installing the Standalone Postman App for Windows, macOS, or Linux
To install the Postman app:
- []Go to the [Postman website](https://www.postman.com/downloads/) and download the app for your OS (i.e., Windows, macOS, or Linux).
For example purposes, the following instructions reference the Windows 64-bit version of the app.
- Install the app. After installation, the login window appears.
- In the login window, create an account and log in.
[See image.](#PostmanSignup)
[]![Signing up to Postman after Installation](/downloads/Sign%20Up%20to%20Postman.png?1618255091)
Configuring the Environment
With Postman installed and opened, you must first create the appropriate environment and add the collection before you can start testing.
To add the environment:
- In the **My Workspace** left-side navigation, click **Environments**.
- Before selecting a new environment, click on the **Menu** icon and then complete the following steps:
- Click **View more actions**.
- Click **Rename** and enter a descriptive environment name (e.g., `Zscaler Private Access`).
[See image.](#SeeImage)
- Click the environment you renamed. This opens a new tab.
- On the opened tab, click **Add a new variable** under the **Variable **column.
- Enter the text `baseUrl`.
- Under the **Initial Value** column, enter the base URL (`https://config.private.zscaler.com`) into the blank field of the environment you want to test in. All API endpoints are relative to the base URL.
- Under the **Current Value** column, click the blank field. The field auto-populates.
[See image.](#SeeImage2)
- Click **Save**.
- In the banner at the top, select the environment you renamed (i.e., Zscaler Private Access) using the drop-down menu.
[See image.](#SeeImage3)
[]![Rename the environment](/downloads/Rename%20the%20Environment.png)
[]![Environment variables](/downloads/Environment%20variables.png)
[]![Environment selection](/downloads/Selecting%20the%20environment.png)
[]Adding the Collection
With the environment configured, now you can add the collection. To add the ZPA API collection:
- Go to the [Reference Guide](/zpa/zpa-api/api-developer-reference-guide/reference-guide) and click **Try In Postman** to download the latest version of the cloud service API collection file.
- From the main window of the Postman application, click **Import**.
[See image.](#importCollection)
Alternatively, go to the application menu and click **File **>** Import...**
[See image.](#postman-import-menu)
- In the import window that appears, select your `.postman_collection` file or drag the file to the selection area.
After the file is imported, a new folder with the name used within the Postman collection file (e.g., Zscaler Private Access API Portal) is displayed within **Collections**.
[]![Clicking Import in the Postman Client](/downloads/zpa/configuring-postman-rest-api-client/postman-import.png)
[]![Importing a File in Postman](/downloads/zpa/configuring-postman-rest-api-client/postman-import-menu.png)
To access specific coding language scripts, click the **Code** icon in the toolbar. Select the desired language from the drop-down menu.
[See images.](#SeeImagesCode)
[]![Postman code snippets](/downloads/Code%20snippets.png)
When using the code scripts for the API, ZPA does not require the `'cookie'` part of the code.
[]Authenticating a Session in Postman
Before you make an API call in Postman, you have to authenticate a session. Currently, the API to sign in must be created manually.
To create a sign-in request:
- In the **My Workspace** left-side navigation, click **Collections**.
- Right-click the **Zscaler Private Access API Portal** collection, and then click **Add Folder**.
- Right-click the folder, and then click **Rename**. Name the folder (e.g., `Login Tokens`).
- Right-click the **Zscaler Private Access API Portal **collection, and then click **Add Request**.
- Right-click the request, and then click **Rename**. Name the request (e.g., `Login`).
- Click the new request. A window appears with the request name.
- Click the request type drop-down menu and select **POST**.
[See image.](#Seeimagerequesttype)
- In the **Enter a request URL **field, enter `{{baseUrl}}/signin`.
[See image.](#Seeimagebaseurl)
- Click **Body,** and then select **x-www-form-urlencoded**.
- Under the **KEY** field, enter `client_id`.
- Under the **VALUE **field, enter your client ID. To learn more, see [About API Key Management](/zpa/about-api-keys).
- In the second row for the **KEY** field, enter `client_secret`.
- In the second row for the **VALUE** field, enter your client secret. To learn more, see [About API Key Management](/zpa/about-api-keys).
[See image.](#Seeimagebodyvalues)
- Click **Send **after the sign-in request is complete.
If your API key was set up properly, a successful response returns status code 200, along with your authorization token.
[See image.](#Seeimagesigninresponse)
[]![Request Drop Down for Request Type Signin](/downloads/Creating%20a%20sign%20in_0.png)
[]![Add the Sign in Request](/downloads/Creating%20a%20sign%20in.png)
[]![Sign in body key](/downloads/Sign%20in%20body%20key.png)
[]![Successful sign in ](/downloads/Successful%20sign%20in.png)
[]Making an API Call in Postman
Try making an API call using Postman. In the following example, get the global policy set ID for a specific ZPA tenant by sending a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/:customerId/policySet/global`:
- Ensure that you can [authenticate](#Authenticating) and log in successfully using the `POST` request to `{{baseUrl}}signin`.
- Click the **Zscaler Private Access API Portal **collection > **policy Set** > **Get the global policy**.
- On the **Params **tab, verify you are using the correct `customerId`. To learn more, see [About API Key Management](/zpa/about-api-keys).
- Under **Path Variables**, enter your customer ID into the **Value** field for the `customerId` Key.
- On the **Authorization **tab, verify the **Type **is **Bearer Token**, and that the correct authorization token has been passed.
- Copy the bearer token you received from the successful `POST` request to `{{baseUrl}}signin`.
- Paste the bearer token into the Token field.
- Click **Send**.
A successful response returns status code 200.
[See image.](#SeeimageGlobalpolicy)
[]![Successful API call](/downloads/Successful%20GET%20request.png)
By default, the session expiration time is 3,600 seconds (one hour).
Logging Out
To invalidate your authorization token and log out of your API session:
- In the **My Workspace** left-side navigation, click **Collections**.
- Right-click the **Zscaler Private Access API Portal** collection, and then click **Add Folder**.
- Right-click the folder, and then click **Rename**. Name the folder (e.g., `Logout`).
- Right-click the **Zscaler Private Access API Portal **collection, and then click **Add Request**.
- Right-click the request, and then click **Rename**. Name the request (e.g., `Logout`).
- Click the new request. A tab opens up in the center window with the request name.
- Click the request type drop-down menu and select **POST**.
[See image.](#Seeimagesignoutrequest)
- In the **Enter a request URL **field, enter `{{baseUrl}}/signout`.
[See image.](#Seeimagesignouturl)
- On the **Authorization** tab, verify the **Type **is **Bearer Token**, and that the correct authorization token has been passed.
- Click **Send** after the sign-out request is complete.
A successful response returns status code 200.
[]![Request Drop Down for Request Type Signout](/downloads/Request%20type%20drop%20down%20menu%20for%20signout.png?1618935849)
[]![Request Drop Down for Request Type Signout](/downloads/Creating%20a%20sign%20out.png)
After your token is invalidated using the `POST` request to `{{baseUrl}}/signout`, you must [authenticate](#Authenticating) and receive a new authorization token to make any further requests.
To learn more about rate limiting and HTTP status codes, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting) and [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages). If you encounter any issues with the API, contact Zscaler Support.

## Contents
- **API Developer & Reference Guide**
  - [Getting Started](/zpa/getting-started-zpa-api)
  - [Configuring the Postman REST API Client](/zpa/configuring-postman-rest-api-client)
  - [Understanding Rate Limiting](/zpa/understanding-rate-limiting)
  - [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages)
  - **Reference Guide**
    - [Admin Single Sign-On Management](/zpa/admin-single-sign-management)
    - [API Key Management](/zpa/api-key-management-zpa-api-reference)
    - [Application Segment Management](/zpa/application-segment-management)
    - [Segment Group Management](/zpa/segment-group-management)
    - [AppProtection Control Management](/zpa/appprotection-control-management)
    - [AppProtection Profile Management](/zpa/appprotection-profile-management)
    - [App Connector Management API](/zpa/app-connector-management-api)
    - [App Connector Group Management](/zpa/app-connector-group-management)
    - [Certificate Management](/zpa/certificate-management-api)
    - [Customers](/zpa/customers)
    - [Customer Domain Management](/zpa/customer-domain-management)
    - [Cloud Connector Groups](/zpa/cloud-connector-groups)
    - [Emergency Access User Management](/zpa/emergency-access-user-management)
    - [Enrollment Certificates](/zpa/enrollment-certificates)
    - [Feature Configuration Management](/zpa/feature-configuration-management)
    - [IdP Configurations](/zpa/idp-configurations)
    - [Isolation Profiles](/zpa/isolation-profiles)
    - [Log Streaming Service (LSS) Configuration](/zpa/log-streaming-service-lss-configuration)
    - [Machine Groups](/zpa/machine-groups)
    - [Delegated Tenant Administration](/zpa/delegated-tenant-administration)
    - [Policy Management](/zpa/policy-management)
    - [Posture Profiles](/zpa/posture-profiles)
    - [Private Service Edge Management](/zpa/private-service-edge-management-api)
    - [Private Service Edge Group Management](/zpa/private-service-edge-group-management)
    - [Private Cloud Controller Management](/zpa/private-cloud-controller-management-zpa-api-reference)
    - [Private Cloud Controller Group Management](/zpa/private-cloud-controller-group-management)
    - [Privileged Approval Management](/zpa/privileged-approval-management)
    - [Privileged Console Management](/zpa/privileged-console-management)
    - [Privileged Credential Management](/zpa/privileged-credential-management)
    - [Privileged Portal Management](/zpa/privileged-portal-management)
    - [Provisioning Key Management](/zpa/provisioning-key-management)
    - [SAML Attributes](/zpa/saml-attributes)
    - [SCIM Attributes](/zpa/scim-attributes)
    - [SCIM Groups](/zpa/scim-groups)
    - [Server Management](/zpa/server-management)
    - [Server Group Management](/zpa/server-group-management)
    - [Trusted Networks](/zpa/trusted-networks)
    - [User Portal Management](/zpa/user-portal-management)
    - [User Portal Link Management](/zpa/user-portal-link-management)
    - [Version Profiles](/zpa/version-profiles)
    - [VPN (for Legacy Apps) API](/zpa/vpn-legacy-apps-api)
    - [Zscaler Clouds ](/zpa/zscaler-clouds)
    - [Zscaler Virtual IP Address Range Management](/zpa/zscaler-virtual-ip-address-range-management)
  - **Working with APIs**
    - [Managing Administrators Using API](/zpa/managing-administrators-using-api)
    - [Managing Administrator Roles Using API](/zpa/managing-administrator-roles-using-api)
    - [Managing Admin Single Sign-On Login Configurations Using API](/zpa/managing-admin-single-sign-login-configurations-using-api)
    - [Managing Client Settings Using API](/zpa/managing-client-settings-using-api)
    - [Obtaining Alternative Cloud Domain Details Using API](/zpa/obtaining-alternative-cloud-domain-details-using-api)
    - [Configuring API Keys Using API](/zpa/configuring-api-keys-using-api)
    - [Managing Application Load Balancing and High Availability Using API](/zpa/managing-application-load-balancing-and-high-availability-using-api)
    - [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api)
    - [Configuring Application Segment Multimatch Using API](/zpa/configuring-application-segment-multimatch-using-api)
    - [Configuring Segment Groups Using API](/zpa/configuring-segment-groups-using-api)
    - [Managing App Connectors Using API](/zpa/managing-app-connectors-using-api)
    - [Configuring Auto Delete for Disconnected App Connectors Using API](/zpa/configuring-auto-delete-disconnected-app-connectors-using-api)
    - [Configuring App Connector Groups Using API](/zpa/configuring-app-connector-groups-using-api)
    - [Configuring Browser Access Application Segments Using API](/zpa/configuring-browser-access-application-segments-using-api)
    - [Configuring Certificates Using API](/zpa/configuring-certificates-using-api)
    - [Obtaining Cloud Connector Group Details Using API](/zpa/obtaining-cloud-connector-group-details-using-api)
    - [Obtaining Customer Details Using API](/zpa/obtaining-customer-details-using-api)
    - [Managing Customer Domains Using API](/zpa/managing-customer-domains-using-api)
    - [Configuring Emergency Access Users Using API](/zpa/configuring-emergency-access-users-using-api)
    - [Obtaining Enrollment Certificate Details Using API](/zpa/obtaining-enrollment-certificate-details-using-api)
    - [Managing Feature Configurations Using API](/zpa/managing-feature-configurations-using-api)
    - [Obtaining IdP Configuration Details Using API](/zpa/obtaining-idp-configuration-details-using-api)
    - [Configuring AppProtection Controls Using API](/zpa/configuring-appprotection-controls-using-api)
    - [Configuring AppProtection Profiles Using API](/zpa/configuring-appprotection-profiles-using-api)
    - [Obtaining Isolation Profile Details Using API](/zpa/obtaining-isolation-profile-details-using-api)
    - [Managing Log Streaming Service Configurations Using API](/zpa/managing-log-streaming-service-configurations-using-api)
    - [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api)
    - [Configuring AppProtection Policies Using API](/zpa/configuring-appprotection-policies-using-api)
    - [Configuring Client Forwarding Policies Using API](/zpa/configuring-client-forwarding-policies-using-api)
    - [Configuring Isolation Policies Using API](/zpa/configuring-isolation-policies-using-api)
    - [Configuring Privileged Policies Using API](/zpa/configuring-privileged-policies-using-api)
    - [Configuring Redirection Policies Using API](/zpa/configuring-redirection-policies-using-api)
    - [Configuring Timeout Policies Using API](/zpa/configuring-timeout-policies-using-api)
    - [Obtaining Machine Group Details Using API](/zpa/obtaining-machine-group-details-using-api)
    - [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api)
    - [Obtaining Posture Profile Details Using API](/zpa/obtaining-posture-profile-details-using-api)
    - [Configuring Privileged Approvals Using API](/zpa/configuring-privileged-approvals-using-api)
    - [Configuring Privileged Credentials Using API](/zpa/configuring-privileged-credentials-using-api)
    - [Configuring Privileged Consoles Using API](/zpa/configuring-privileged-consoles-using-api)
    - [Configuring Privileged Portals Using API](/zpa/configuring-privileged-portals-using-api)
    - [Configuring Provisioning Keys Using API](/zpa/configuring-provisioning-keys-using-api)
    - [Obtaining SAML Attribute Details Using API](/zpa/obtaining-saml-attribute-details-using-api)
    - [Obtaining SCIM Attribute Details Using API](/zpa/obtaining-scim-attribute-details-using-api)
    - [Obtaining SCIM Group Details Using API](/zpa/obtaining-scim-group-details-using-api)
    - [Configuring Servers Using API](/zpa/configuring-servers-using-api)
    - [Configuring Server Groups Using API](/zpa/configuring-server-groups-using-api)
    - [Managing ZPA Private Service Edges Using API](/zpa/managing-zpa-private-service-edges-using-api)
    - [Configuring ZPA Private Service Edge Groups Using API](/zpa/configuring-zpa-private-service-edge-groups-using-api)
    - [Managing Private Cloud Controllers Using API](/zpa/managing-private-cloud-controllers-using-api)
    - [Managing Private Cloud Controller Groups Using API](/zpa/managing-private-cloud-controller-groups-using-api)
    - [Obtaining VPN (for Legacy Apps) Resources Using API](/zpa/obtaining-vpn-legacy-apps-resources-using-api)
    - [Obtaining Trusted Network Details Using API](/zpa/obtaining-trusted-network-details-using-api)
    - [Obtaining Version Profile Details Using API](/zpa/obtaining-version-profile-details-using-api)
    - [Configuring User Portals Using API](/zpa/configuring-user-portals-using-api)
    - [Configuring User Portal Links Using API](/zpa/configuring-user-portal-links-using-api)
    - [Configuring Zscaler Virtual IP Address Ranges Using API](/zpa/configuring-zscaler-virtual-ip-address-ranges-using-api)