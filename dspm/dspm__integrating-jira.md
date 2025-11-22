# Integrating with Jira
Source: https://help.zscaler.com/dspm/integrating-jira
PDF: https://help.zscaler.com/pdf/com/en/1487566.pdf

DSPM leverages Jira APIs to automatically create tickets when sensitive data or any misconfigurations are detected in your cloud resources. You can integrate DSPM with Jira to leverage the alert data logs from the cloud storage services and create incidents for further evaluation.
DSPM can be integrated with Jira Cloud versions, provided there is support for the required authentication mechanism and APIs to create a Jira task.
Prerequisites
You must first complete the OAuth configuration before integrating DSPM with Jira.
To configure the OAuth app:
- Sign in to the [Atlassian Developer console](https://id.atlassian.com/login?continue=https%3A%2F%2Fdeveloper.atlassian.com%2Fconsole%2Fmyapps%2F).
-
Click **Create** and select **OAuth 2.0 integration**.
[See image.](#ds-oauth)
-
Under **Create a New OAuth 2.0 (3LO) integration**, enter a name for the application.
[See image.](#ds-oauthname)
-
Accept the terms and conditions, then click **Create**.
The application is created and displayed under **Console** > **My apps**.
Set up the API permissions:
- On the Atlassian Developer console, click **Permissions**.
-
Click **Add** for the Jira API.
[See image.](#ds-addapi)
The button name changes to **Configuration**.
- Click **Configuration** to view the list of Jira APIs.
-
Select the scope for the required Jira features that you want to use for this integration. For example, select `read:jira-work` to read the Jira project, issue data, etc.
[See image.](#ds-scope)
- Click **Save**.
Authorize DSPM to access the Jira APIs:
-
Go to the DSPM Admin Portal and copy the application URL.
[See image.](#ds-copyurl)
- On the Atlassian Developer console, click **Authorization** in the left-side navigation.
- Click **Add**.
-
For **Callback URL**, paste the application URL you copied from the DSPM Admin Portal
[See image.](#ds-callbackurl)
- Click **Save Changes**.
- Next, click **Settings** in the left-side navigation.
-
Copy the **Client ID** and **Client Secret**. You need to use these values while adding the Jira integration in the DSPM Admin Portal.
[See image.](#ds-clientidsecret)
Integrating with Jira
To integrate DSPM with Jira:
- Go to** Administration** > **Integrations**.
-
Under the **ITSM integrations**, click **Add**.
[See image.](#ds-jira-addbutton)
-
Under **Integration Information**:
- For **Integration Name**, enter a unique name for the integration.
- For **IT Service**, select **Jira**.
[See image.](#ds-selectjira)
- Click **Next**.
-
Under **ITSM Details**:
- **Jira Client ID**: Paste the Client ID that you copied while configuring the OAuth app.
- **Jira Client Secret**: Paste the Client Secret that you copied while configuring the OAuth app.
- Click **Authorize **to validate the Jira connection.
[See image.](#ds-jiradetails)
You are redirected back to the Atlassian login page. If you're not able to log in, then you see the *Authorization in Process* message in the DSPM Admin Portal, and the following message on the Atlassian Developer console: [See image.](#ds-jiraerror) Check and use the correct **Jira Client ID** and **Client Secret** values for the authorization to be successful.
-
On the Atlassian Developer console, click **Accept** to grant the required permissions to the OAuth client app to perform API operations in Jira.
[See image.](#ds-acceptauth)
You are again redirected back to the DSPM Admin Portal and a message is displayed indicating the authorization is successful.
- Select the required Jira project from the drop-down menu.
- Click **Next**.
-
Review the integration details. Click the **Edit** icon if you want to make any changes.
[See image.](#ds-jira-summary)
- Click **Finish**.
The integration is added, and the details are displayed on the **Integrations** page.
[]![Add a Jira integration](/downloads/dspm/third-party-integrations/itsm-tools/integrating-jira/ds-itsm-addbutton.png)
[]![Select Jira ](/downloads/dspm/third-party-integrations/itsm-tools/integrating-jira/ds-jira-select.png)
[]![Add the Jira details](/downloads/dspm/third-party-integrations/itsm-tools/integrating-jira/ds-jira-details.png)
[]![Review the integration settings](/downloads/dspm/third-party-integrations/integrating-jira/ds-jirasummary.png)
[]![Select OAuth integration](/downloads/dspm/third-party-integrations/itsm-tools/integrating-jira/ds-jira-selectoauth.png)
[]![Provide a name for the integration](/downloads/dspm/third-party-integrations/itsm-tools/integrating-jira/ds-jira-addname.png)
[]![Add Jira API](/downloads/dspm/third-party-integrations/itsm-tools/integrating-jira/ds-addjira-apiscope.png)
[]![Set up the permissions](/downloads/dspm/third-party-integrations/itsm-tools/integrating-jira/ds-jira%20scopepermissions.png)
[]![Enter the DSPM app URL](/downloads/dspm/third-party-integrations/itsm-tools/integrating-jira/ds-jira-appurl.png)
[]![Copy the client ID and secret](/downloads/dspm/third-party-integrations/itsm-tools/integrating-jira/ds-jira-clientid-secret.png)
[]![Error message](/downloads/dspm/third-party-integrations/itsm-tools/integrating-jira/ds-jira-errormessage.png)
[]![Grant access to the app](/downloads/dspm/third-party-integrations/itsm-tools/integrating-jira/ds-jira-accept-auth.png)
[]
![Copy the app URL](/downloads/dspm/third-party-integrations/itsm-tools/integrating-jira/ds-dspm-url.png)