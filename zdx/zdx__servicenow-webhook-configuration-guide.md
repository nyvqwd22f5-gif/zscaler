# ServiceNow Webhook Configuration Guide
Source: https://help.zscaler.com/zdx/servicenow-webhook-configuration-guide
PDF: https://help.zscaler.com/pdf/com/en/1414521.pdf

ZDX supports the integration of IT Service Management (ITSM) via Incident Management (IM) and IT Operations Management (ITOM) via Event Management (EM). You can configure webhooks to deliver alerts about an application, device, or network performance. You can also use webhooks in an alert rule and configure multiple alert rules for the webhook. To learn more, see [Configuring an Alert Rule](/zdx/configuring-alert-rule).
Prerequisites
Ensure the following steps are completed prior to integrating with ServiceNow Event Management:
- Enable ITOM. To learn more, refer to [ServiceNow IT Operations Management](https://www.servicenow.com/products/it-operations-management.html).
- Request the EM plugin and install it from the store when it is available. To learn more, refer to ServiceNow's [Zscaler Digital Experience: Event Management](https://store.servicenow.com/sn_appstore_store.do#!/store/application/161c06b787ad8110419aff77cebb35f8/1.0.0?referer=%2Fstore%2Fsearch%3Flistingtype%3Dallintegrations%25253Bancillary_app%25253Bcertified_apps%25253Bcontent%25253Bindustry_solution%25253Boem%25253Butility%25253Btemplate%26q%3Dzscaler&sl=sh).
To configure a webhook for ServiceNow, you must:
- [1. Create Service users and an OAuth 2.0 API endpoint in ServiceNow.](#CreateServiceUser_SNOW)
- [2. Create a ZDX Role in the ZDX Admin Portal.](#CreateZDXRole)
- [3. Configure a webhook in the ZDX Admin Portal.](#ConfigureWebhookZDX)
- [4. Confirm the webhook test result and Deep Tracing connection on ServiceNow.](#TestResultServiceNow)
Deep Tracing is a type of [Diagnostics session](/zdx/starting-new-diagnostics-session). In ServiceNow, you can only configure for Deep Tracing.
[]Prior to creating a webhook, you must create users in ServiceNow and admins in the ZDX Admin Portal. Creating an OAuth 2.0 API endpoint is optional based on your authentication requirements.
In your ServiceNow Console:
- [Create the required service user.](#ServiceNowServiceUsers)
- [(Optional) Create an OAuth 2.0 API endpoint.](#ServiceNowOAuthAPIEndpoint)
[]
- Go to **All** > **User Administration** > **Users**.
- Click **New**.
-
Enter your **User ID**. You can enter an email address as your User ID.
Zscaler recommends using an email address in lieu of a user ID.
- Select the **Web Services Access only** checkbox.
- Click **Submit**.
- Reopen the user's record and click **Set Password**.
- In the **Set Password** window:
- Click **Generate**.
-
**Copy** the generated password. Save the user ID and password information.
[See image.](#zdx-servicenow-setpassword)
- Click **Save Password**.
- Click **Set Password **on the User Record to save the password.
-
In the Roles related list, click **Edit**.
[See image.](#zdx-servicenow-edituser)
- Based on your service user's access needs, assign the respective role to the service user:
- [Incident Management](#IncidentManagementRequiredUser)
- [Event Management](#EventManagementRequiredUser)
- Click **Save**.
- Click **Update** on the user's record.
[]
-
Search for `oauth` and go to **Application Registry** > **New** > **Create an OAuthAPI endpoint for external clients**.
[See image.](#ServiceNow-CreateOAuth)
-
In the **Application Registries** page:
- **Name**: Enter a name for the OAuth support.
- **Client ID**: This is not configurable. Save the Client ID for later use.
- **Client Secret**: If this field is left empty, it auto-generates a Client Secret code. Save this Client Secret for later use.
-
**Redirect UR**L: Enter your URL based on the cloud name of the ZDX tenant.
The format must be:
``https://admin.``<cloud name>``/zdx/admin/webhooks``
Replace `<cloud name`> with your designated cloud name. To learn more, see [What Is my Cloud Name for ZDX?](/zdx/what-my-cloud-name-zdx)
- **Refresh Token Lifespan**: Enter your refresh token lifespan. Zscaler recommends a lifespan of 5 years from the current date.
- **Access Token Lifespan**: Enter your access token lifespan. Zscaler recommends a lifespan of 1 hour to maximize reuse.
[See image.](#ServiceNow-SubmitOAuthDetails)
- Click **Submit** to save your settings.
[]
- [Add a ZDX Role](/zdx/adding-zdx-roles) to have the following permissions:
- **Diagnostics**: Full
- **Webhooks**: Full
- **User & Device Names**: Visible
- **Configuration Access**: Full
- **Alerts**: Full
- **UCaaS Monitoring**: View Only
- Assign the ServiceNow Role from the previous step to an existing ZDX Admin or by [adding a ZDX Admin](/zdx/adding-zdx-admins).
- Click **Save**.
- [Activate the changes.](/zdx/saving-and-activating-changes-admin-portal)
- []Go to **Administration** > **Integrations** > **Webhooks **> **Add New Webhook**.
- In the **Add New Webhook** window:
- **Name**: Enter a name for the webhook.
- **Status**: Select **Enabled** to enable the webhook.
- **URL**: Enter one of the following URLs based on the integration:
- [Incident Management](#IncidentManagementURL)
- [Event Management](#EventManagementURL)
- []**Authentication Type**: Select your authentication type.
- [Basic](#BasicAuthentication)
- [OAuth](#OAuth)
-
Click **Test Webhook** to see if it functions correctly.
Test Webhook for OAuth does not post a test message on ServiceNow. Instead, it acquires the OAuth token.
- If the test is successful, a message indicating success appears.
- Click **Save**.
- [Activate the changes](/zdx/saving-and-activating-changes-admin-portal).
- If the test is unsuccessful, an error message appears.
- To troubleshoot the error, check for issues in the **URL** or the **Authentication Type** fields.
- If the error persists, record to provide details of your error (e.g., screenshots or small video). Click **Cancel** so that the webhook configuration containing errors is not saved, and contact Zscaler Support with the error information.
[]To confirm if the webhook test result is on ServiceNow:
- Go to the ServiceNow service portal.
- In the **Filter Navigator** search bar, enter `Zscaler Digital Experience`.
-
From the menu, select **ServiceNow Incidents** or **ServiceNow Events** module to see if the test webhook is recorded.
[See image.](#zdx-servicenow-incidentsandeventstestresult)
To confirm the Deep Tracing connection is on ServiceNow for IM:
- Go to the **ServiceNow **portal.
- In the **Filter Navigator** search bar, enter `Zscaler Digital Experience`.
- From the menu, select the **ServiceNow Incidents** module.
- Open your targeted incident record.
- Go to the Deep Tracing section and see if one of the following occurs to confirm the Deep Tracing connection:
- The information message, "There are no related Deep Tracing Sessions." indicates there are no existing Deep Tracing sessions in ZDX related to the current incident.
- A table of Deep Tracing sessions.
After the webhook configuration is complete and the ServiceNow users are assigned the Incident Management role, x_zsca2_zdx_manage.zdx_management, you can configure the **Settings** and **Mapping** modules in the ZDX application on ServiceNow to meet your alerting requirements. To learn more, see [Understanding the ZDX Application Fields on ServiceNow](/zdx/mapping-zdx-application-fields-servicenow).
[]If your service user requires access to IM:
- For web service users that require access to IM, add the **x_zsca2_zdx_manage.zdx_management** role.
- For users working with the Deep Tracing feature, add the **x_zsca2_zdx_manage.zdx_dt_management** role.
[]If your service user requires access to EM:
- For web service users that require access to EM, add the **evt_mgmt_integration** role.
- For active users that require managing the application, add the **x_zsca2_zdx_manage.zdx_em_admin** and **evt_mgmt_user** roles.
[]https://<your-instance-ID>.service-now.com/api/x_zsca2_zdx_manage/incident_management_api
To learn more about installation and configuration details for ServiceNow Incident Management for ZDX, refer to the [ServiceNow Store](https://store.servicenow.com/sn_appstore_store.do#!/store/application/faa68b0987510510d52bca2e0ebb358d/2.0.1?referer=%2Fstore%2Fsearch%3Flistingtype%3Dallintegrations%25253Bancillary_app%25253Bcertified_apps%25253Bcontent%25253Bindustry_solution%25253Boem%25253Butility%25253Btemplate%26q%3Dzscaler&sl=sh).
[]https://<your-instance-ID>.service-now.com/api/global/em/jsonv2
To learn more about installation and configuration details for ServiceNow Event Management for ZDX, refer to the [ServiceNow Store](https://store.servicenow.com/sn_appstore_store.do#!/store/application/161c06b787ad8110419aff77cebb35f8/1.0.0?referer=%2Fstore%2Fsearch%3Flistingtype%3Dallintegrations%25253Bancillary_app%25253Bcertified_apps%25253Bcontent%25253Bindustry_solution%25253Boem%25253Butility%25253Btemplate%26q%3Dzscaler&sl=sh).
[]
![Copy your generated password on the service user](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/servicenow-webhook-configuration-guide/ZDX-SNOW-SetPassword.png)
[]
![Edit the user](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/configuring-webhooks-servicenow/ZDX-SNOW-IM-Edit-0.png)
[]ServiceNow Incidents
![Incidents Test Results](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/configuring-webhooks-servicenow/ZDX-SNOW-TestIncidents-0.png)
ServiceNow Events
![Events Test Result](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/servicenow-webhook-configuration-guide/ZDX-SNOW-TestEvents.png)
[]
For Basic Authentication:
- **Username**: Enter the username of the previously created service user.
- **Password**: Enter the password of the previously created service user.
Click **Save **to save your webhook configuration.
[]
For OAuth Authentication:
- **Application**: Select **ServiceNow**.
- **Client ID**: Enter the Client ID of the previously created OAuth 2.0 API endpoint.
- **Client Secret**: Enter the Client Secret of the previously created OAuth 2.0 API endpoint.
- **Refresh Token Expiration**: Select the date of when the refresh token expires from the previously created OAuth API 2.0 endpoint.
- Click **Authenticate Tenant**.
Click **Save **to save your webhook configuration.
[]
![Create an OAuth API endpoint for external clients](/downloads/zdx/alerts/webhook-configuration-guide-servicenow/ServiceNow-WhichOAuth.png)
[]
![Enter OAuth Details](/downloads/zdx/alerts/webhook-configuration-guide-servicenow/ServiceNow-ApplicationRegistries-OAuth.png)