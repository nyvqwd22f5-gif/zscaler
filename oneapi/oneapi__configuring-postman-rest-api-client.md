# Configuring the Postman REST API Client
Source: https://help.zscaler.com/oneapi/configuring-postman-rest-api-client
PDF: https://help.zscaler.com/pdf/com/en/1497126.pdf

Zscaler offers a Postman collection that simplifies interaction with its API endpoints, allowing you to easily test and manage API requests within the Postman application. This collection is designed to work seamlessly with all APIs included in Zscaler OneAPI, requiring minimal configurations from the user. It includes preconfigured request scripts for authentication, along with prebuilt payloads and parameters where necessary. Additionally, the collection includes all the essential preset variables, ensuring a smooth experience. This article provides information on how to set up your Postman application and make API requests, along with a link to download the Postman collection for OneAPI.
- You can use the Postman collection provided by Zscaler on Windows, Linux, and macOS versions of the Postman REST API client.
- Before getting started, ensure that you have [obtained the API client information](/zidentity/adding-api-client), such as client ID and client secret, from the ZIdentity Admin Portal. This article follows the client secret flow of authentication which is supported by the Postman application.
To learn more about rate limiting and HTTP status codes, see [Understanding Rate Limiting](/oneapi/understanding-rate-limiting) and [Understanding Response Codes & Error Messages](/oneapi/understanding-response-codes-error-messages). If you encounter any issues with the API, contact Zscaler Support.
Installing and Configuring Postman for Windows, macOS, or Linux
To install the Postman application:
-
[]Go to the [Download Postman page](https://www.postman.com/downloads/) and download the application for your OS (i.e., Windows, macOS, or Linux).
For this example, the Postman application for 64-bit version Windows is used to illustrate the instructions.
- Open the downloaded Postman setup file to install the application. After installation, the login window for signing in to Postman appears.
-
In the login window, create an account, and sign in using your account. If you already have a Postman account, log in to Postman with your existing credentials.
[See image.](#postman-signup)
[]Adding OneAPI Postman Collection
After logging in to Postman, you can import the Postman collection for OneAPI. To add the collection to the Postman application:
- Download the latest Postman collection for OneAPI from the following link: [Download JSON](/downloads/oneapi/getting-started-oneapi/configuring-postman-rest-api-client/OneAPI_postman_collection_09_18_2025.json)
- In the Postman application, go to your preferred workspace. The default workspace is **My Workspace**.
-
Click **Import**. Alternatively, you can go to the application menu on the top-left corner and click **File** > **Import**.
[See image.](#postman-import-collection)
-
In the import window that appears, select your Postman collection file or drag the file to the import window. The Postman collection for OneAPI is imported into the application. A new folder with the name used within the Postman collection file (e.g., OneAPI) is displayed within **Collections** in the left-side navigation.
[See image.](#postman-oneapi-collection)
[]Setting Up Variables and Environments
Before you make API calls using the collection in Postman, you must configure a set of variables that helps reuse specific values across your API requests. You can configure variables at different scopes in Postman. For OneAPI, it is recommended to configure variables either at the collection level or at the environment level. To learn more, refer to the [Postman documentation](https://learning.postman.com/docs/sending-requests/variables/variables-intro/).
The Postman collection provided by Zscaler is preconfigured with variables at the collection level to help you get started quickly by specifying values for these variables. Alternatively, you can create an environment with the same set of variables and reference the variables in your API requests by selecting the environment. Using environments is especially recommended if you are working across multiple OneAPI collections (e.g., you can use different environments for testing and production purposes). The following sections explain how to set up the predefined collection variables or create an environment with the same set of variables.
Configuring Collection Variables
To configure collection variables:
- In the workspace where you added your collection, go to **Collections**.
- Click the OneAPI collection folder name.
-
Go to the **Variables** tab displayed for the collection.
The variables present in the collection are displayed in a table, with values prepopulated for variables that are universal to all organizations (e.g., base URL for APIs).
[See image.](#postman-oneapi-default-variables)
-
For variables that contain values specific to the organization, such as client ID, client secret, ZIdentity's token endpoint, etc., you must configure the values manually. For each variable, enter its value into the **Initial value** column, then re-enter the same value in the **Current value** column.
[See a table showing variables and a description of their values.](#collection-variables)
[See image.](#postman-oneapi-collection-variables-configured)
Ensure that the variables are selected and configured properly.
-
Click the **Save **icon displayed in the top right of the collection window.
[See image.](#postman-oneapi-save-collection-variables)
Creating an Environment
To add an environment:
- In the workspace where you added your collection, go to **Environments **in the workspace.
-
Click **Create Environment **or click the **Add** icon.
[See image.](#postman-create-environment-option1)
Alternatively, you can click the **Environment quick look** icon on the right panel from any location of the Postman application.
[See image.](#postman-create-environment-option2)
A new environment is added and opens in a tab.
-
On the environment tab, enter a descriptive name for the environment (e.g., OneAPI) where the current generic name is highlighted.
[See image.](#postman-new-environment)
-
In the variables table, add the variables listed in the following table and configure their values. For each variable, enter its value into the **Initial value** column, and the same value is automatically populated in the **Current value** column.
[See a table showing variables and a description of their values.](#environment-variables)
[See image.](#postman-oneapi-environment)
Ensure that the variables are selected, the **Type** is set to **default**, and that the variables are configured properly.
-
Click **Save** in the top right of the environment tab.
[See image.](#postman-save-environment)
[]Authenticating a Session in Postman
Before you make an API call from Postman, you must authenticate a session by sending a POST request to ZIdentity's token endpoint and obtaining an authorization token (i.e., bearer access token) in exchange for the API client credentials. The Postman collection provided by Zscaler is prebuilt with the authorization request and associated configurations, simplifying the process of getting access tokens. In addition, authorization is configured at the collection level, which allows you to get the access token once and automatically use it for all requests in the collection.
- The authorization request and token configuration use variables such as `zIdentityBaseUrl`, `clientID`, and `clientSecret`, so ensure that you have configured these variables with appropriate values before sending the request. To learn more, see [Setting Up Variables and Environments](#setting-up-variables-environments).
- The instructions in this section follow the client secret flow of authentication which is supported by the Postman application. The other method of authentication that you can use for OneAPI, Private Key JWT authentication, is not supported by Postman.
To send an authorization request to retrieve the access token:
- In the workspace where you added your collection, go to **Collections**.
- Click the OneAPI collection folder name.
-
Go to the **Authorization** tab displayed for the collection.
[See image.](#postman-collection-authorization)
-
Review the authorization details that are prepopulated for the OAuth 2.0 authentication type and verify the token configuration details.
Under **Advanced**, ensure that the `audience` parameter configured with the value `https://api.zscaler.com/` is selected for both **Token Request** and **Refresh Request**.
[See image.](#postman-authorization-audience-parameter)
-
If you are using an environment for your variables, ensure that the correct environment is selected in the top-right corner.
[See image.](#postman-collection-authorization-use-environment)
-
After verifying the authorization details, click **Get New Access Token**.
[See image.](#postman-get-access-token-oauth2)
If authentication is successful, an access token is returned and appears in a window. This window displays the complete token details, such as the access token, token type (i.e., bearer token), token expiration, etc.
[See image.](#postman-access-token)
- (Optional) Rename the token for easy identification using the **Token Name** field in the window.
- To use the access token in your API requests, click **Use Token **in the window.
-
On the **Authorization **tab, the access token name is selected in the drop-down menu and the token is populated in the **Token** field under **Current Token**.
[See image.](#postman-access-token-selected)
When the access token is selected for use, the **Auto-refresh Token** option is automatically enabled.
This authorization token is automatically passed onto each request made from the collection to the OneAPI resources.
[]Making an API Call in Postman
Before making API calls, ensure that the API is authenticated.
If you are using an environment to reference your variables, select the appropriate environment configured for OneAPI from the environment drop-down menu in the top-right corner.
[See image.](#postman-api-request-select-environment)
The steps to making calls to OneAPI are explained using the following examples:
- [Example request to ZIA API](#zia-api-request)
- [Example request to ZPA API](#zpa-api-request)
- [Example request to Zscaler Client Connector API](#client-connector-api-request)
- [Example request to Zscaler Cloud & Branch Connector API](#cloud-branch-connector-api-request)
- [Example request to Zscaler Digital Experience (ZDX) API](#zdx-api-request)
- [Example request to ZIdentity API](#zidentity-api-request)
To access specific coding language scripts, go to the request for which you need the script and click the **Code** icon in the toolbar. Select the desired language from the drop-down menu.
[See image.](#postman-code-snippet)
[]Using the following example, you can get the details of a user by sending a GET request to the `/users/:id` endpoint.
- In the workspace where you added your collection, go to **Collections**.
- Click the **OneAPI** folder and then click the **ZIdentity** folder.
- Go to the **users** folder and select **Users Ops get**. The `/Users Ops get` request appears on the right-side pane.
-
On the **Params** tab, verify that you are using the correct `id`. Under **Path Variables**, enter the user ID into the Value field for the `id` key.
[See image.](#img-zidentity-config-postman)
- Click **Send**.
A successful response returns a `Status: 200 OK` message along with the ZIdentity user details in the response body.
[]The following example shows how to look up categories in ZIA for a specified list of URLs using `/urlLookup`.
- In the workspace where you added your collection, go to **Collections**.
- Click the **OneAPI** folder and then click the **Zscaler Internet Access (ZIA)** folder.
-
Go to **URL categories** > **POST URL Lookup**. The `/urlLookup` request appears on the right-side pane.
Click the request's **Body** tab to view the list of reconfigured URLs for which the lookup operation must be performed. You can look up a maximum of 100 URLs per request, with each URL not exceeding 1,024 characters.
-
Click **Send**.
When the request is successful, you receive a `Status 200 OK` message and a response body that looks as follows:
[See image.](#postman-zia-request-response)
[]Using the following example, you can get the global policy set ID for a specific ZPA tenant by sending a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/:customerId/policySet/global`.
- In the workspace where you added your collection, go to **Collections**.
- Click the **OneAPI** folder and then click the **Zscaler Private Access (ZPA)** folder.
- Go to **Policy Set** > **Get the global policy**. The `/mgmtconfig/v1/admin/customers/:customerId/policySet/global` request appears on the right-side pane.
-
On the **Params **tab, verify that you are using the correct `customerId`. To learn more, see [About API Key Management](/zpa/about-api-keys).
Under **Path Variables**, enter your customer ID into the **Value** field for the `customerId` Key.
-
Click **Send**.
A successful response returns a `Status: 200 OK` message and a response body that looks as follows:
[See image.](#postman-zpa-request-response)
[]Using the following example, you can get a one-time password (OTP) for a specific device​​ from Zscaler Client Connector by sending a GET request to the `/getOtp` endpoint.
- In the workspace where you added your collection, go to **Collections**.
- Click the **OneAPI** folder and then click the **Zscaler Client Connector** folder.
- Go to **Get OTP** > **Get OTP for device**. The `/getOtp` request appears on the right pane.
- On the **Params **tab, select the `udid` query parameter and enter the Unique Device Identifier value. Optionally, you can configure `udid` as a variable and reference it in the requests.
-
Click **Send**.
A successful response returns a `Status: 200 OK` message along with an OTP in the response body.
[]Using the following example, you can get the list of available Cloud & Branch Connector groups by sending a GET request to the `/ecgroup` endpoint.
- In the workspace where you added your collection, go to **Collections**.
- Click the **OneAPI** folder and then click the **Zscaler Cloud & Branch Connector** folder.
- Go to the **Cloud & Branch Connector Groups** folder and select **Cloud & Branch Connector Groups - Get All Groups and VMs**. The `/ecgroup` request appears on the right-side pane.
-
Click **Send**.
A successful response returns a `Status: 200 OK` message along with the Cloud & Branch Connector groups in the response body.
[See image.](#cloud-branch-connector-postman-request)
[]Using the following example, you can get the list of available ZDX groups by sending a GET request to the `/apps` endpoint.
- In the workspace where you added your collection, go to **Collections**.
- Click the **OneAPI** folder and then click the **Zscaler Digital Experience (ZDX)** folder.
- Go to the **Reports** > **Apps** folder and select **/apps**. The `/apps` request appears on the right-side pane.
-
Click **Send**.
A successful response returns a `Status: 200 OK` message along with the ZDX groups in the response body.
[][](/oneapi/getting-started)
| Variable Name | Description |
| ------------- | ----------- |
| clientID | API client ID obtained from the ZIdentity Admin Portal. |
| clientSecret | API client secret obtained from the ZIdentity Admin Portal. |
| customerId | Zscaler Private Access (ZPA) tenant ID of the customer obtained from the ZIdentity Admin Portal or the ZPA Admin Portal. To learn how to obtain the ZPA customer ID, see Getting Started. This configuration is applicable only to ZPA API clients. |
| oneAPIBaseUrl | This variable is prepopulated with the base URL for OneAPI: `https://api.zsapi.net`. |
| ZIABase | This variable is prepopulated with the base URL for Zscaler Internet Access (ZIA) API: `{{oneAPIBaseUrl}}/zia/api/v1`, which would become `https://api.zsapi.net/zia/api/v1` when the `{{oneAPIBaseUrl}}` variable is replaced with its value. |
| ZPABase | This variable is prepopulated with the base URL for Zscaler Private Access (ZPA) API: `{{oneAPIBaseUrl}}/zpa`, which would become `https://api.zsapi.net/zpa` when the `{{oneAPIBaseUrl}}` variable is replaced with its value. |
| ZCCBase | This variable is prepopulated with the base URL for Zscaler Client Connector API: `{{oneAPIBaseUrl}}/zcc/papi/public`, which would become `https://api.zsapi.net/zcc/papi/public` when the `{{oneAPIBaseUrl}}` variable is replaced with its value. |
| ZTWBase | This variable is prepopulated with the base URL for Cloud & Branch Connector API: `{{oneAPIBaseUrl}}/ztw/api/v1`, which would become `https://api.zsapi.net/ztw/api/v1` when the `{{oneAPIBaseUrl}}` variable is replaced with its value. |
| ZDXBase | This variable is prepopulated with the base URL for Zscaler Digital Experience (ZDX) API: `{{oneAPIBaseUrl}}/zdx/v1`, which would become `https://api.zsapi.net/zdx/v1` when the `{{oneAPIBaseUrl}}` variable is replaced with its value. |
| zIdentityBaseUrl | Represents ZIdentity's token endpoint: `https://<Vanity Domain>.zslogin.net`, where `<Vanity Domain>` refers to the domain name used by your organization. |
[][](/oneapi/getting-started)
| Variable Name | Description |
| ------------- | ----------- |
| clientID | API client ID obtained from the ZIdentity Admin Portal. |
| clientSecret | API client secret obtained from the ZIdentity Admin Portal. |
| customerId | Zscaler Private Access (ZPA) tenant ID of the customer obtained from the ZIdentity Admin Portal or the ZPA Admin Portal. To learn how to obtain the ZPA customer ID, see Getting Started. This configuration is applicable only to ZPA API clients. |
| oneAPIBaseUrl | Base URL for OneAPI: `https://api.zsapi.net`. |
| ZIABase | Base URL for Zscaler Internet Access (ZIA) API: `{{oneAPIBaseUrl}}/zia/api/v1`. |
| ZPABase | Base URL for Zscaler Private Access (ZPA) API: `{{oneAPIBaseUrl}}/zpa`. |
| ZCCBase | Base URL for Zscaler Client Connector API: `{{oneAPIBaseUrl}}/zcc/papi/public`. |
| ZTWBase | Base URL for Cloud & Branch Connector API: `{{oneAPIBaseUrl}}/ztw/api/v1`. |
| ZDXBase | Base URL for Zscaler Digital Experience (ZDX) API: `{{oneAPIBaseUrl}}/zdx/v1`. |
| zIdentityBaseUrl | Represents ZIdentity's token endpoint: `https://<Vanity Domain>.zslogin.net`, where `<Vanity Domain>` refers to the domain name used by your organization. |
| ZIAMBase | Base URL for Zscaler ZIdentity API: `{{oneAPIBaseUrl}}/ziam/admin/api/v1`. |
[]![A screenshot showing the Postman app sign-up page](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-signup.png)
[]![A screenshot showing options to import a collection in Postman](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-import-collection.png)
[]![A screenshot showing the OneAPI collection imported into Postman](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-oneapi-collection.png)
[]![A screenshot showing OneAPI collection variables in Postman](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-oneapi-default-variables.png)
[]![A screenshot from Postman app showing how to configure collection variables](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-oneapi-collection-variables-configured.png)
[]![A screenshot from Postman app showing how to configure collection variables](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-oneapi-save-collection-variables.png)
[]![A screenshot showing how to add a new environment in Postman](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-create-environment-option1.png)
[]![A screenshot showing how to add a new environment in Postman](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-create-environment-option2.png)
[]![A screenshot from Postman app showing how to add a new environment](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-new-environment_0.png)
[]![A screenshot from Postman app showing the variables configured in an environment](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-oneapi-environment-configured.png)
[]![A screenshot from Postman app showing how to save an environment](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-save-environment_0.png)
[]![A screenshot showing the Authorization tab for the collection in Postman](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-collection-authorization_0.png)
[]![A screenshot showing the Authorization tab for the collection in Postman](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-collection-authorization-use-environment_0.png)
[]![A screenshot from Postman app showing option to get access token](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-get-access-token-oauth2_0.png)
[]![A screenshot from Postman app showing access token returned by ZIdentity token endpoint](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-access-token.png)
[]![A screenshot from Postman app showing access token selected for OAuth 2.0](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-access-token-selected_1.png)
[]![Zscaler Internet Access (ZIA) API sample response](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-zia-request-response.png)
[]![Zscaler Private Access (ZPA) API sample response](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-zpa-request-response.png)
[]![A screenshot from Postman app showing option to select configured environment](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-api-request-select-environment_0.png)
[]![A screenshot of the audience parameter configured for the authorization request in Postman](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/Postman-authorization-audience.png)
[]![A screenshot of the code snippets available for API requests in different languages in Postman app](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/postman-code-snippet.png)
[]![Cloud & Branch Connector Request in Postman](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/cloud-branch-connector-postman-request.png)
[]![Postman interface showing ZIdentity GET user API request with path variables, headers, and response preview.](/downloads/oneapi/getting-started-zscaler-apis/configuring-postman-rest-api-client/config-postman-zidentity.png)