# Configuring the Postman REST API Client
Source: https://help.zscaler.com/workflow-automation/configuring-postman-rest-api-client-workflow-automation-api
PDF: https://help.zscaler.com/pdf/com/en/1452371.pdf

Zscaler supports the macOS, Windows, and Linux versions of the Postman REST API app. To learn more about the app and its features, refer to the [Postman documentation](https://learning.postman.com/docs/getting-started/introduction/).
If you already have Postman installed and configured, you can download the latest version of the Workflow Automation API Postman collection files from any article within the [Reference Guide](/zia/api-authentication-workflow-automation-api).
Installing and Configuring Postman for macOS, Windows, or Linux
To install and configure Postman:
- Go to the [Postman website](https://www.getpostman.com/), download, and install the app for your OS (i.e., macOS, Windows, or Linux).
- After installation, open the app and log in to your account. If you do not have an account, you can create one.
- Download the latest version of the Workflow Automation API Postman collection file from the [Reference Guide](/zia/api-authentication-workflow-automation-api).
- From the main window, click **Import**. Alternatively, from the top menu, you can go to **File > Import**.
[See image.](#import-button)
- In the **Import** window that appears, drag and drop the `.postman_collection` file into the window or click** Files** and upload it from your local.
[See image.](#drop-upload-files)
After the file is imported, a new folder, Workflow Automation API (e.g., workflow-automation-api-postman-collection), is displayed within **Collections**.
- Next to the environment drop-down menu in the upper right, ensure that **No Environment** is selected, then click the **Environment quick look** icon.
- Click **Add**.
[See image.](#add-icon)
- On the **New Environment** tab that appears, complete the following steps:
- Enter a descriptive name for the environment (e.g., Zscaler Test Environment).
- For **Variable**, enter `url`.
- For **Type**, leave as default.
- For the **Initial Value**, enter `https://api.``<us1.zsworkflow.net>``/dlp/v1`, where `<us1.zsworkflow.net>` is the cloud provisioned for your organization.
- Click **Save**.
[See image.](#new-environment)
You can then select this environment (e.g., Zscalerr Test Environment) from the drop-down menu in the upper right. To learn more, refer to the [Postman documentation](https://learning.postman.com/docs/sending-requests/managing-environments/).
Authenticating a Session in Postman
After installing and configuring the Postman app, try to authenticate a session.
- Log in to the Workflow Automation Admin Portal using your API admin credentials. To learn more, see [Getting Started](/zia/getting-started-workflow-automation-api).
- Copy the** **Key ID and the Key Secret from the **API Keys** page.
- In the Postman app:
- Go to **File** > **Settings**.
[See image.](#settings-navigation)
- Under **General**, turn off **SSL certificate verification**.
[See image.](#disable-ssl-inspection)
- Go to POST **get-token-by-api-key** in the Postman collection, you imported previously.
- Click **Body **and replace your `key_id` and `key_secret` you copied in Step 3.
- Click **Send**.
[See image.](#api-authentication-post-request)
If your API key was set up correctly, a **Status 200 OK** message with the authorization token is returned.
[See image.](#successful-authentication)
Making an API Call in Postman
Try making an API call using Postman. In the following example, we download information about a specific DLP incident using `/incidents/transactions/{transcationId}`:
- Make sure that you can authenticate successfully.
- Go to GET** get-dlp-incidents-by-transaction-id**. Ensure that you replace the `{transcationId}` in the GET request with the actual transaction ID.
[See image.](#actual-transaction-id)
- In the **Authorization **tab, verify the **Type** is **Bearer Token**, and that the correct authorization token has been passed.
- Copy the bearer token you received from successful API authentication.
- Paste the bearer token into the **Token **field.
[See image.](#get-request-list-dlp-incidents)
- Click **Send**.
You should receive a **Status 200 OK** message and a response.
[See image.](#successful-response-dlp-incidents)
By default, the session is terminated after 300 seconds or 5 minutes.
[]![Screenshot of the Import button in the Postman application](/downloads/zia/workflow-automation-api/api-developer-reference-guide/configuring-postman-rest-api-client-0/workflow-automation-api-postman-import.png)
[]![Screenshot of the Drop or Upload postman collection window in the Postman application](/downloads/zia/workflow-automation-api/api-developer-reference-guide/configuring-postman-rest-api-client-0/workflow-automation-api-postman-drag-files.png)
[]![Screenshot of Add icon to add a new environment to the Postman app](/downloads/zia/workflow-automation-api/api-developer-reference-guide/configuring-postman-rest-api-client-0/workflow-automation-api-postman-add-environment.png?1683313955)
[]![Screenshot of setting variables, initial and current values to the new environment in the Postman app](/downloads/zia/workflow-automation-api/api-developer-reference-guide/configuring-postman-rest-api-client-0/workflow-automation-api-postman-variable-initial-values.png)
[]![Screenshot of the File > Settings navigation in the Postman app](/downloads/zia/workflow-automation-api/api-developer-reference-guide/configuring-postman-rest-api-client-0/workflow-automation-api-postman-settings.png)
[]![Screenshot of disabling SSL inspection in the Settings window in the Postman app](/downloads/zia/workflow-automation-api/api-developer-reference-guide/configuring-postman-rest-api-client-0/workflow-automation-api-postman-disable-ssl-inspection.png)
[]![Screenshot of the POST request to authenticate API with the API key in the Postman app](/downloads/zia/workflow-automation-api/api-developer-reference-guide/configuring-postman-rest-api-client-0/workflow-automation-api-postman-authentication-request-body.png?1683568874)
[]![Screenshot of successful response with the authorization token to the API authentication request](/downloads/zia/workflow-automation-api/api-developer-reference-guide/configuring-postman-rest-api-client-0/workflow-automation-api-postman-authentication-200status.png)
[]![Screenshot of replacing the actual transaction ID in the GET request body](/downloads/zia/workflow-automation-api/api-developer-reference-guide/configuring-postman-rest-api-client-0/workflow-automation-api-postman-replace-transaction-id.png)
[]![Screenshot of an example GET request to download the list of a DLP incidents using the transaction ID](/downloads/zia/workflow-automation-api/api-developer-reference-guide/configuring-postman-rest-api-client-0/workflow-automation-api-postman-transactionid-get-request.png?1683568494)
[]![Screenshot of a successful response with the list of DLP Incidents for a transaction ID](/downloads/zia/workflow-automation-api/api-developer-reference-guide/configuring-postman-rest-api-client-0/workflow-automation-api-postman-transactionid-response-200status.png)