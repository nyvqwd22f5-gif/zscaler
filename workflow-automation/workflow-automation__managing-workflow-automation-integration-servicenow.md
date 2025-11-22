# Managing Workflow Automation Integration with ServiceNow
Source: https://help.zscaler.com/workflow-automation/managing-workflow-automation-integration-servicenow
PDF: https://help.zscaler.com/pdf/com/en/1457511.pdf

Workflow Automation can integrate with ServiceNow, a sanctioned Software as a Service (SaaS) application for Zscaler. During the remediation process for a data protection incident in Workflow Automation, admins can create and assign a ServiceNow ticket to an incident on the Incident Details page. When the ticket action is initiated on the Incident Details page for an incident, the admin selects the user to assign to the ticket in ServiceNow. The user they select must exist in the ServiceNow application and must have already been added on the Integration Users page in Workflow Automation. To learn more, see [Managing Integration Users](/zia/managing-integration-users) and [Viewing & Managing Incident Details](/zia/viewing-managing-incident-details).
When configuring the ServiceNow integration in Workflow Automation, you can select whether you want to sync the ticket status between ServiceNow and Workflow Automation. If you choose to sync the ticket status, you can also select whether to close the incident in Workflow Automation when the ticket is closed in ServiceNow. If you enable this option, after Workflow Automation receives the Closed status through the sync process, it automatically closes the incident.
The workflow functionality in Workflow Automation also has an Auto Create Tickets template that you can use to create tickets in ServiceNow. To learn more, see [Managing Workflow Templates](/zia/managing-workflow-templates).
Integrating Workflow Automation with ServiceNow
Before you can integrate Workflow Automation with ServiceNow, you must:
- Configure the Data Loss Prevention (DLP) application integration for your organization using Amazon Web Services. Ensure that you add a DLP application integration in Workflow Automation during this process. To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services](/workflow-automation/configuring-dlp-application-integration-using-amazon-web-services).
- Obtain and configure the ServiceNow application for your organization.
- Ensure that you define the different users for your organization who can use the ServiceNow application.
- Ensure that you have admin credentials for the ServiceNow application. These credentials are required to integrate Workflow Automation with ServiceNow.
To learn more, refer to the [ServiceNow documentation](https://docs.servicenow.com/en-US/).
To integrate Workflow Automation with ServiceNow:
- In the ZIA Admin Portal, go to **Administration** > **SaaS Application Tenants**.
- Click **Add SaaS Application Tenant**. The **Add SaaS Application Tenant** page appears.
- On the **Add SaaS Application Tenant** page, configure and add the ServiceNow application as a SaaS application tenant using the ServiceNow admin credentials. When adding the tenant, ensure that you select the **Workflow Automation** checkbox in the **Onboard SaaS Application for** section. This process authorizes the ServiceNow application with Zscaler Internet Access (ZIA) and integrates the ServiceNow application with Workflow Automation. On the **Integrations** dashboard in Workflow Automation, the ServiceNow application appears as a tile in the **Connected Apps** section. To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
[See image.](#add-saas-application-tenant-image)
Managing ServiceNow Integrations in Workflow Automation
On the Integrations dashboard in the Workflow Automation Admin Portal, admins can:
- [Configure ServiceNow Integrations](#configure-sn-integration)
- [Edit ServiceNow Integrations](#edit-sn-integration)
- [Disable or Enable ServiceNow Integrations](#enable-disable-sn-integration)
- [View ServiceNow Integrations](#view-sn-integrations)
[]To configure a ServiceNow integration in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations** dashboard appears, displaying a **ServiceNow** application tile in the** Connected Apps** section. The **Tile View** icon is selected by default.
[See image.](#Integrations-Dashboard-View-SN-Card)
- Perform one of the following steps:
- In the tile view, in the **Connected Apps **section,** **click anywhere on the **ServiceNow** tile.
- In the list view, in the **Connected Apps** section, click **View Details **next to the ServiceNow integration.
The **ServiceNow Integration** details page appears. In the **Connected Accounts** section, all the ServiceNow integrations appear along with their statuses (Enabled and Disabled). To display the deleted application integrations, click **Show Deleted Accounts** at the top right of the **Connected Accounts** section.
[See image.](#ServiceNow-Integration-Details-Page-Configure)
- On the **ServiceNow Integration** details page, click the **Edit** icon next to the connected account you want to configure. The **ServiceNow Integration** editing page appears.
- On the **ServiceNow Integration** editing page:
- (Optional) **Sync ticket status**: Select this checkbox if you want to sync the ticket status between ServiceNow and Workflow Automation. The sync process runs daily. When the ticket is closed in ServiceNow, only the **Closed** status for a ticket appears on the **Incident Details** page in Workflow Automation. None of the other ServiceNow ticket statuses appear on the **Incident Details** page. After you select this checkbox, the **Close incident when ticket is closed** checkbox appears on the page.
- (Optional) **Close incident when ticket is closed**: Select this checkbox if you want Workflow Automation to automatically close the incident in Workflow Automation when the ticket is closed in ServiceNow.
[See image.](#Edit-ServiceNow-Integration-Page)
- Click **Save Changes**.
[]To edit a ServiceNow integration in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations **dashboard appears, displaying a **ServiceNow** application tile in the** Connected Apps** section. The **Tile View** icon is selected by default.
- Perform one of the following steps:
- In the tile view, in the **Connected Apps **section,** **click anywhere on the **ServiceNow** tile.
- In the list view, in the **Connected Apps** section, click **View Details **next to the ServiceNow integration.
The **ServiceNow Integration** details page appears. In the **Connected Accounts** section, all the ServiceNow integrations appear, along with the status of each integration (Enabled and Disabled), the date each integration was last modified, and the name of the individual who performed the modification. To display the deleted application integrations, click **Show Deleted Accounts** at the top right of the **Connected Accounts** section.
[See image.](#ServiceNow-Integration-Details-Page-Edit)
- On the **ServiceNow Integration** details page, click the **Edit** icon next to the connected account you want to edit. The **ServiceNow Integration** editing page appears.
- On the **ServiceNow Integration** editing page, edit any of the fields that are displayed.
- Click **Save Changes**.
[]To disable or enable a ServiceNow integration in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations **dashboard appears, displaying a **ServiceNow** application tile in the** Connected Apps** section. The **Tile View** icon is selected by default.
- Perform one of the following steps:
- In the tile view, in the **Connected Apps** section, click anywhere on the **ServiceNow** tile.
- In the list view, in the **Connected Apps** section, click **View Details **next to the ServiceNow integration.
The **ServiceNow Integration** details page appears. In the **Connected Accounts** section, all the ServiceNow integrations appear, along with their statuses (Enabled and Disabled), the date each integration was last modified, and the name of the individual who performed the modification.
[See image.](#ServiceNow-Integration-Details-Page-Disable-Enable)
- On the **ServiceNow Integration** details page, click the **Edit** icon next to a connected account with an Enabled status that you want to disable or an account with a Disabled status that you want to enable. The **ServiceNow Integration** editing page appears.
- On the **ServiceNow Integration** editing page, click **Disable Integration **or** Enable Integration. **The status of the integration changes to Disabled or Enabled. You cannot enable or disable ServiceNow integrations that have been deleted.
[]To view ServiceNow integrations in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations **dashboard appears.
- On the **Integrations **dashboard:
- Filter the integrations that are displayed on the dashboard. Select **All** to display all the integrations or select **Connected** to display only those integrations that are connected. By default, all integrations display.
[See image.](#All-Connected-icons)
- Change the layout of the dashboard. Select the **Tile View** icon to view the integrations in a tile format or select the **List View** icon to view the integrations in a list format. By default, the dashboard displays in the tile view.
[See image.](#card-view-and-list-view-icons)
- View the list of all ServiceNow integrations that have been added to your organization.
In the tile view, in the **Connected Apps** section, you can view the following information:
- **App**: The application that is associated with the integration—for example, ServiceNow.
- **Account Details**: The integration name for each account associated with the integration.
- **Status**: The status of the accounts for the integration. An oval at the top of the tile lists the number of accounts that are connected and the status of **Connected**. This number does not include accounts with a Deleted status.
[See image.](#ServiceNow-Card)
In the list view, in the **Connected Apps** section, you can view the following information:
- **App Integration:** The application that is associated with the integration.
- **Account Details**: The integration name for each account associated with the integration.
- **Status**: The status of the accounts for the integration. An oval in this field lists the number of accounts that are connected and the status of **Connected. **This number does not include accounts with a Deleted status.
- **Account Connected**: The number of accounts that are connected.
[See image.](#ServiceNow-List-View)
- View additional details for the ServiceNow integrations by performing one of the following steps:
- In the tile view, in the **Connected Apps** section, click anywhere in the **DLP** tile.
- In the list view, in the **Connected Apps** section, click **View Details** next to the DLP application integration.
The **ServiceNow Integration** details page appears, displaying a **Configuration Steps** tab and a **Configuration** tab. The **Configuration Steps** tab provides a link to the instructions on how to manage the Workflow Automation integration with ServiceNow. On the **Configuration** tab, you can view the list of ServiceNow integration accounts along with the status of each account, the date when each account was last modified, and the individual who performed the modification. To display the deleted application integrations, click **Show Deleted Accounts** at the top right of the **Connected Accounts** section.
- On the **Configuration** tab, click the **Edit** icon next to a ServiceNow integration account to view the specific details for that integration.
[]![Adding ServiceNow as a SaaS Application Tenant on the Add SaaS Application Tenant page in the ZIA Admin Portal](/downloads/zia/policies/data-loss-prevention/zscaler-workflow-automation/setup/configuring-workflow-automation-integration-servicenow/ZIA-WA-Add-SaaS-Application-Tenant-Page-ServiceNow.png)
[]![Viewing the ServiceNow connected application tile on the Integrations Dashboard in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/managing-workflow-automation-integration-servicenow/WA-Integrations-Dashboard-Viewing-ServiceNow-Integration-Tile.png)
[]![Viewing the ServiceNow Integration details page with an enabled ServiceNow integration in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/managing-workflow-automation-integration-servicenow/WA-ServiceNow-Integration-Details-Page-Enabled.png)
[]![Configuring the ServiceNow Integration on the ServiceNow Integration editing page in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/managing-workflow-automation-integration-servicenow/WA-Edit-ServiceNow-Integration-Page.png)
[]![Viewing all the ServiceNow integrations on the ServiceNow Integration details page in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/managing-workflow-automation-integration-servicenow/WA-ServiceNow-Integration-Details-Page-Show-All.png)
[]![Viewing the ServiceNow Integration details page after editing a ServiceNow integration](/downloads/workflow-automation/setup/managing-workflow-automation-integration-servicenow/WA-ServiceNow-Integration-Details-Page-After-Edit.png)
[]![Viewing the All and Connected icons on the Integrations Dashboard in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/managing-workflow-automation-integration-servicenow/WA-ServiceNow-Integrations-Dashboard-All-Connected-Icons.png)
[]![Viewing the Tile and List View icons on the Integrations Dashboard in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/managing-workflow-automation-integration-servicenow/WA-ServiceNow-Integrations-Dashboard-Tile-Listview-Icons.png)
[]![Viewing the ServiceNow Integration tile on the Integrations Dashboard in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/managing-workflow-automation-integration-servicenow/WA-Integrations-Dashboard-ServiceNow-Tile.png)
[]![Viewing the ServiceNow list entry on the Integrations Dashboard in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/managing-workflow-automation-integration-servicenow/WA-Integrations-Dashboard-ServiceNow-List-View.png)