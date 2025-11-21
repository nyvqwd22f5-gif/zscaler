# Integrating with Atlassian
Source: https://help.zscaler.com/unified/integrating-atlassian
PDF: https://help.zscaler.com/pdf/com/en/1515256.pdf

You can connect your Atlassian organization to Zscaler 3rd-Party App Governance to gain continuous visibility and governance for third-party apps installed in the Atlassian environment.
Atlassian integration consists of the following steps:
- Generate an Atlassian API token.
- Connect Atlassian to the 3rd-Party App Governance Platform.
Prerequisite
- A user with Atlassian Admin privileges.
- An Atlassian API token is required to retrieve all the relevant information from Atlassian.
[]Generate an Atlassian API Token
Due to the various authentication methods used by Atlassian to retrieve your platform’s information, some functions might not be available without your Atlassian API token.
To generate an Atlassian API token:
- Log in to the Atlassian Admin Portal.
- Create an API token in Atlassian. To learn more, refer to the [Atlassian Documentation](https://support.atlassian.com/atlassian-account/docs/manage-api-tokens-for-your-atlassian-account/).
- Note the API token you created. You will need it in the following steps.
For security reasons, you cannot view the API key in plain text. You must store the API key securely.
Connect Atlassian to the 3rd-Party App Governance Platform
To connect Atlassian to 3rd-Party App Governance:
- Click the **Connect** icon in the left-side navigation.
[See image.](#Connect-Button)
The **Integrations** window appears.
- In the **Integrations** window, click **Add** next to **Atlassian. **You are prompted to sign in if you haven't already done so.
[See image.](#Atlassian-Integration)
A consent window appears (all privileges are read-only), and you can see a detailed list of permissions and data [here](#Permissions-Table).
This consent step only allows reading of the apps in your workspace. Additional consent steps are required for the revocation and banning of apps. By default, 3rd-Party App Governance users who are not explicitly granted revocation rights are unable to perform revoke operations.
- Copy and paste the token you created in the** API Key** text box and click **Connect**.
[See image.](#Add-API-Key)
If you have yet to generate the API key, click **Generate an API Key. **You are redirected to Atlassian. Complete the steps provided in [Generate an Atlassian API Token](#Generate-API-Token).
After connection is achieved, it might take a while to pull and ingest all relevant application data depending on the size of your tenant. During this time, a message is displayed that the domain is still being processed. After integration is completed, a success message appears, and the number of domains is updated. You then receive an email from Zscaler when the domain is ready for further review. To learn more about the integration statuses of a domain, see [Status](#Integration-Status).
Viewing and Managing Atlassian Integration
You can click **Atlassian **in the** Integrations **window** **to expand and view the list of added domains along with information such as API Key, First connected, Last Synced, and Status.
- **Domain**: The name of the domain integrated with 3rd-Party App Governance.
- **API Key**: The API Key generated for the domain.
- **First connected**: The date and time the domain was added, and the person who added the domain.
- **Last Synced**: The date and time the domain was last synced. If the domain has yet to sync, N/A is displayed. If the duration of the sync is excessive, the last sync time is highlighted in red.
When there are multiple domains, 3rd-Party App Governance displays the last sync with the most excessive time duration to indicate an issue so you can expand, view the domain, and take the relevant actions.
- []**Status**: The integration status of the domain. One of the following statuses is displayed:
- **Error**: Failure to achieve a connection. The error message displays the reason for the failure. Contact Zscaler Support if you require further assistance.
- **In progress**: Connection is achieved and 3rd-Party App Governance is ingesting the relevant data. It might take a while to pull and ingest all relevant application data depending on the size of your tenant. During this time, a message is displayed that the domain is still being processed. You then receive an email from Zscaler when the domain is ready for further review.
- **Success**: The integration is completed successfully and the last sync time is updated.
Reconnecting Atlassian to 3rd-Party App Governance
You might need to reconnect Atlassian to 3rd-Party App Governance if an error is displayed (e.g., `Grant Expired)`. To reconnect Atlassian to 3rd-Party App Governance:
- Click** Atlassian **in the** Integrations **window** **to expand and view the list of added domains.
- Click the **Reconnect **icon next to the relevant domain.
A confirmation window appears.
- Click **Confirm** to continue.
A consent window appears. After consent is granted, the connection is updated.
Updating the Atlassian API token
If you revoke an API token that is currently in use, you can replace it with a new token. To update the API token:
- Click **Atlassian **in the** Integrations **window** **to expand and view the list of added domains.
- Click the **Edit** icon next to the API key for the relevant domain.
- Update the API key and click the check mark to save the changes.
A confirmation window appears.
- Click **Confirm** if you want to override the connection.
The connection is updated.
Deleting an Atlassian Connection
You can delete an Atlassian connection to 3rd-Party App Governance. To delete an Atlassian connection:
- Click **Atlassian **in the** Integrations **window** **to expand and view the list of added domains.
- Click the **Delete **icon next to the relevant domain.
A confirmation window appears.
- Click **Confirm** to continue.
The connection is successfully deleted.
[]Permissions and Data Collected
The following table lists the permissions and data collected after integration.
| **Which permissions do we use?** | **What data do we collect?** |
| -------------------------------- | ---------------------------- |
| offline_access | A global OAuth scope, enabling 3rd-Party App Governance to refresh the token upon its expiration to keep the integration live without the need to repetitively ask for consent |
| read:me | View the profile details for the currently logged-in user |
| read:application-role:jira | View application roles |
| read:audit-log:jira | View audit logs |
| read:avatar:jira | View system and custom avatars |
| read:group:jira | View user groups |
| read:user:jira | View users |
| read:permission:jira | View permissions |
| read:permission-scheme:jira | View permission schemes |
| read:project-role:jira | View project roles |
| read:instance-configuration:jira | View instance configurations |
| read:license:jira | View licenses |
| read:field:jira | View fields |
| read:project:jira | View projects |
| read:user-configuration:jira | View user configurations |
| read:configuration:confluence | View Confluence settings, themes, and system information |
| read:group:confluence | View details about groups |
![Screenshot of Connect Button](/downloads/zia/apptotal/getting-started/connecting-your-platforms/atlassian-integration/Connect_Button_0.png)
[]
![API Key Text Box](/downloads/tech-pubs-drafts/zia-draft-articles/integrating-atlassian-doc-48720/APIKey_TextBox2.png)
[]
![Screenshot of Atlassian Integration](/downloads/tech-pubs-drafts/zia-draft-articles/integrating-atlassian-doc-48720/Atlassian%20Integration.png)
[]