# Integrating with Jira
Source: https://help.zscaler.com/zpc/integrating-jira
PDF: https://help.zscaler.com/pdf/com/en/1409771.pdf

Zscaler Posture Control (ZPC) leverages Jira APIs to automatically create tickets when a misconfiguration is detected. You can integrate ZPC with Jira to create incidents and send alert notifications whenever a security policy violation occurs on specific cloud accounts.
ZPC can be integrated with Jira cloud versions, provided there is support for the required authentication mechanism and APIs to create a Jira task.
Prerequisites
You must first complete the OAuth configuration before integrating ZPC with Jira.
To configure the OAuth app:
- Log in to the Atlassian Developer console.
-
Click **Create** and select **OAuth 2.0 integration**.
[See image.](#zpc-selectoauth)
- Under **Create a New OAuth 2.0 (3LO) integration**, enter a name for the application.
-
Accept the terms and conditions, then click **Create**.
[See image.](#zpc-jiraname)
The application is created and displayed under **Console** > **My apps**. Next, you must set up the API permissions.
- Click **Permissions**.
-
Click **Add** for the Jira API.
[See image.](#zpc-jiraapi)
The button name changes to **Configuration**.
- Click **Configuration** to view the list of Jira APIs.
-
Select the scope for the required Jira features that you want to use for this integration. For example, select `read:jira-work` to read the Jira project, issue data, etc. Select `write:jira-work` to create and edit issues in Jira.
[See image.](#zpc-permissions)
-
Click **Save**.
Next, you need to authorize ZPC to access the Jira APIs.
- Go to the ZPC Admin Portal and copy the application URL.
- On the Atlassian Developer Console, click **Authorization** in the left-side navigation.
- Click **Add**.
-
For **Callback URL**, paste the application URL you copied from the ZPC Admin Portal.
[See image.](#zpc-callback)
- Click **Save Changes**.
- Next, click **Settings** in the left-side navigation.
-
Copy the **Client ID** and **Client Secret**. You need to use these values while adding the Jira integration in the ZPC Admin Portal.
[See image.](#zpc-clientid)
Integrating with Jira
To integrate ZPC with Jira:
- Go to** Administration** > **Integrations**.
-
Under the **ITSM integrations**, click **Add**.
[See image.](#zpc-addjira)
-
Under **Integration Information**:
- For **Integration Name**, enter a unique name for the integration.
- For **IT Service**, select **Jira**.
[See image.](#zpc-selectjira)
- Click **Next**.
- Under **ITSM Details**:
- **Jira Client ID**: Paste the Client ID that you copied while configuring the OAuth app.
- **Jira Client Secret**: Paste the Client Secret that you copied while configuring the OAuth app.
-
Click **Authorize **to validate the Jira connection.
You are redirected back to the Atlassian login page.
If you're not able to log in, then you see the *Authorization in Process* message in the ZPC Admin Portal, and the following message on the Atlassian Developer console: [See image.](#zpc-errormsg) Check and use the correct **Jira Client ID** and **Client Secret** values for the authorization to be successful.
-
On the Atlassian Developer console, click **Accept** to grant the required permissions to the Oauth client app to perform API operations in Jira.
[See image.](#zpc-authorize)
You are again redirected back to the ZPC Admin Portal and a message is displayed indicating the authorization is successful.
[See image.](#zpc-message)
- Select the required Jira project from the drop-down menu.
- Click **Next**.
- Review the integration details. Click the **Edit** icon if you want to make any changes.
- Click **Finish**.
The integration is added and the details are displayed on the **Integrations** page.
[]![Add a Jira integration](/downloads/zpc/third-party-integrations/itsm-integrations/integrating-jira/zpc-add-jira.png)
[]![Provide a name for the Jira integration](/downloads/zpc/third-party-integrations/itsm-integrations/integrating-jira/zpc-select-jira.png)
[]![Provide a name for the new Jira integration](/downloads/zpc/third-party-integrations/itsm-integrations/integrating-jira/zpc-jira-addname.png)
[]![Add the Jira API](/downloads/zpc/third-party-integrations/itsm-integrations/integrating-jira/zpc-addjira-api.png)
[]![Set up the Jira permissions](/downloads/zpc/third-party-integrations/itsm-integrations/integrating-jira/zpc-jira%20permissions.png)
[]![Enter the callback URL](/downloads/zpc/third-party-integrations/itsm-integrations/integrating-jira/zpc-callbackurl.png)
[]![Copy the client ID and secret](/downloads/zpc/third-party-integrations/itsm-integrations/integrating-jira/zpc-jira-clientid-secret.png)
[]![Accept the authorization](/downloads/zpc/third-party-integrations/itsm-integrations/integrating-jira/zpc-jira-accept-auth.png)
[]![Message that indicates authorization is successful](/downloads/zpc/third-party-integrations/itsm-integrations/integrating-jira/zpc-jira-auth-successmsg.png)
[]![Select OAuth 2.0 integration](/downloads/zpc/third-party-integrations/itsm-integrations/integrating-jira/zpc-jira-selectoauth.png?1671099141)
[]![Error message on Atlassian portal](/downloads/zpc/third-party-integrations/itsm-integrations/integrating-jira/zpc-jira-message.png?1671097346)