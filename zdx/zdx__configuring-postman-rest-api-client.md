# Configuring the Postman REST API Client
Source: https://help.zscaler.com/zdx/configuring-postman-rest-api-client
PDF: https://help.zscaler.com/pdf/com/en/1402766.pdf

When Postman is configured with ZDX API, it allows for more readily available ZDX API use cases. Zscaler supports the macOS, Windows, and Linux versions of the Postman REST API app. To learn more about the app and its features, see the [Postman documentation](https://learning.postman.com/docs/getting-started/introduction/).
If you already have Postman installed and configured, you can download the latest version of the ZDX API by using the API Postman collection files from any article within the [Reference Guide](/zdx/api-authentication).
[See image.](#DownloadPostman)
Ensure that you have the prerequisites set properly within Postman for your ZDX API. To learn more, see [Getting Started](/zdx/getting-started-zdx-api).
[]![Select Try in Postman to download the ZDX Postman Collection file.](/downloads/zdx/zdx-api/api-developer-reference-guide/configuring-postman-rest-api-client/ZDX-TryInPostman.png)
Installing and Configuring Postman for macOS, Windows, or Linux
To install and configure Postman:
For example purposes, the following instructions reference the Windows 64-bit version of the app using the ZDX API collection.
- []Go to the [Postman website](https://www.getpostman.com/) and download the app for your OS (i.e., macOS, Windows, or Linux).
- Install the app.
- After installation, open the app. Log in to your account, or create a new one.
- Download the latest version of the ZDX API Postman collection file from the [Reference Guide](/zdx/api-authentication).
- From the main window, click **Import**. You can also go to **File** > **Import** from the top menu.
[See image.](#ImportButton_Img)
[]![Import button on Postman app](/downloads/zia/cloud-service-api/api-developer-reference-guide/configuring-postman-rest-api-client/zapi-importbutton-winapp.png)
- In the **Import **window that appears, make sure the **File** is selected, then drag and drop the .postman_collection file into the window. You can also click **Upload Files**.
[See image.](#UploadFile_Img)
[]![Upload File to Import in Postman](/downloads/zia/cloud-service-api/api-developer-reference-guide/configuring-postman-rest-api-client/Postman_ImportFile2.png)
After the file is imported, the **ZDX API** folder is created and displayed within the **Collections** tab.
[See image.](#CollectionZDXAPI)
[![Upon successful upload, the ZDX API Folder is created in the Collections tab.](/downloads/zdx/administration/api-key-management/configuring-postman-rest-api-client/zdx-api-collection.png)
]
[]Authenticating a Session in Postman
After installing and configuring the Postman app, try to authenticate a session.
For example purposes, the following instructions reference the Windows 64-bit version of the app using the ZDX API collection.
- []Log in to the ZDX Admin Portal using your API admin credentials. To learn more, see [Getting Started](/zdx/getting-started-zdx-api).
- Go to **Administration** > **Authentication** > **API Key Management**.
- Copy your API Key ID and Key Secret, or download a JSON file of the API Key for reference. To learn more, see [Managing API Keys](/zdx/managing-zdx-api-keys/#ViewAPIKey).
- In the Postman app:
- Set up your Global Variables:
- Go to **Environment Quick Looks** > **Globals **>** Edit**.
- Create your global variables, `api_key` and `api_secret`. If you already have the global variables, `api_key` and `api_secret`, proceed to the next step.
- Set your global variables, `api_key` and `api_secret`, with your `key_id` and `key_secret` values from Step 1.
- Optionally, you can use the following pre-request script.
var currTimestamp = Math.round(Date.now()/1000)
pm.globals.set("key_secret")
pm.globals.set("timestamp", currTimestamp)
You can download the latest ZDX API Postman collection file from any article within the [Reference Guide](/zdx/api-authentication).
- Click** Save**.
- Authenticate your API Key for a bearer token:
- Go to **Collections** > **ZDX API** > **oauth** > **POST/oauth/token**.
- Under **Headers**, deselect all the headers except **Postman-Token**.
- Click **Send**.
Upon successful authentication, you receive a **Status 200 OK** message and a bearer token is created.
Making an API Call in Postman
Try making an API call using Postman. In the following example, a list of ZDX Scores for all active apps and the most impacted region using /apps is retrieved:
For example purposes, the following instructions reference the Windows 64-bit version of the app using the ZDX API collection.
- Make sure that you can authenticate successfully.
- In the ZDX API collection, go to **Apps** > **GET /apps**.
- Click **Send**.
Upon successful authentication, you receive a **Status 200 OK** message and a list of active apps and the most impacted region.
By default, the session terminates after 3,600 seconds or 60 minutes, and then reauthentication is required.

## Contents
- **API Developer & Reference Guide**
  - [Getting Started](/zdx/getting-started-zdx-api)
  - [Understanding Rate Limiting](/zdx/understanding-rate-limiting)
  - [Understanding Error Codes](/zdx/understanding-error-codes)
  - [Configuring the Postman REST API Client](/zdx/configuring-postman-rest-api-client)
  - **Reference Guide**
    - [API Authentication](/zdx/api-authentication)
    - [Administration](/zdx/administration-0)
    - [Alerts](/zdx/alerts-zdx-api)
    - [Inventory](/zdx/inventory)
    - [Reports](/zdx/reports)
    - [Troubleshooting](/zdx/troubleshooting)
    - [ZDX Snapshots](/zdx/zdx-snapshots)
  - **Working with APIs**
    - [Managing Administration Using API](/zdx/managing-administration-using-api)
    - [Configuring Deep Tracing Using API](/zdx/configuring-deep-tracing-using-api)