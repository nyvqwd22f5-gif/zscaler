# Managing ServiceNow Integration for ZDX Alerts
Source: https://help.zscaler.com/workflow-automation/managing-servicenow-integration-zdx-alerts
PDF: https://help.zscaler.com/pdf/com/en/1478836.pdf

Workflow Automation can integrate with ServiceNow, a sanctioned Software as a Service (SaaS) application for Zscaler. For managing the Zscaler Digital Experience (ZDX) alerts in Workflow Automation, admins can create and assign a ServiceNow ticket to the dedicated teams using Workflows. The workflow functionality in Workflow Automation has a ZDX Alerts Auto Create Tickets template to create and assign tickets in the ticketing application. To learn more, see [Managing Workflow Templates for ZDX Alerts](/workflow-automation/managing-workflow-templates-zdx-alerts).
Integrating Workflow Automation with ServiceNow for ZDX
The following prerequisites are required before you can integrate Workflow Automation with ServiceNow:
- Obtain and configure the ServiceNow application for your organization.
- Ensure that you define the different users for your organization that can use the ServiceNow application.
-
Ensure that you have admin credentials for the ServiceNow application. These credentials are required to integrate Workflow Automation with ServiceNow.
To learn more, refer to the [ServiceNow documentation](https://docs.servicenow.com/en-US/).
To integrate Workflow Automation with ServiceNow:
- Go to **Administration** > **Integrations** > **SaaS App Tenants** in the ZDX Admin Portal.
- Click **Add New Integration**. The **Add New Integration** page appears.
- On the **Add New Integration** page, add the ServiceNow application available under the **Workflow Automation Applications **section as a SaaS application tenant using the ServiceNow admin credentials. This process authorizes the ServiceNow application with ZDX and integrates the ServiceNow application with Workflow Automation. The ServiceNow application appears as a tile under the Connected Apps section on the **Integrations** dashboard in Workflow Automation. To learn more, see [Configuring SaaS Application Tenants for ZDX](/zdx/configuring-saas-application-tenants-zdx).
[See image.](#add-saas-application-tenant-image)
Managing ServiceNow Integrations in Workflow Automation
On the Integrations dashboard in the Workflow Automation Admin Portal, admins can:
- [View ServiceNow Integrations](#view-sn-integrations)
- [Edit ServiceNow Integrations](#configure-sn-integration)
- [Disable or Enable ServiceNow Integrations](#enable-disable-sn-integration)
[]To edit a ServiceNow integration in Workflow Automation:
-
Go to **Setup** > **Integrations**. The **Integrations** dashboard appears, displaying a **ServiceNow** tile under the** Connected Apps** section. The **Tile View** icon is selected by default.
[See image.](#Integrations-Dashboard-View-SN-Card)
-
Perform one of the following steps:
- In the tile view, in the **Connected Apps **section,** **click anywhere on the **ServiceNow** tile.
- In the list view, in the **Connected Apps** section, click **View Details **next to the ServiceNow integration.
The **ServiceNow Integration** details page appears, displaying all the ServiceNow integrations along with the status of each integration (Enabled and Disabled), the date each integration was last modified, and the name of the individual who performed the modification, under the **Connected Accounts** section.
To view the deleted application integrations, select **Show Deleted Accounts** at the top right of the **Connected Accounts** section.
[See image.](#ServiceNow-Integration-Details-Page-Configure)
- On the **ServiceNow Integration** details page, click the **Edit** icon next to the connected account you want to edit.
-
On the new page that appears, you can modify the **Integration Name** field.
[See image.](#Edit-ServiceNow-Integration-Page)
- Click **Save Changes**.
[]To disable or enable a ServiceNow integration in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations **dashboard appears, displaying a **ServiceNow** tile under the** Connected Apps** section. The **Tile View** icon is selected by default.
-
Perform one of the following steps:
- In the tile view, in the **Connected Apps **section,** **click anywhere on the **ServiceNow** tile.
- In the list view, in the **Connected Apps** section, click **View Details **next to the ServiceNow integration.
The **ServiceNow Integration** details page appears.
- On the **ServiceNow Integration** details page, click the **Edit** icon next to a connected account with an Enabled status that you want to disable, or an account with a Disabled status that you want to enable.
-
On the new page that appears, click **Disable Integration **or** Enable Integration. **The status of the integration changes to Disabled or Enabled. You cannot enable or disable ServiceNow integrations that have been deleted.
[See image.](#ServiceNow-Integration-Details-Page-Disable-Enable)
[]To view ServiceNow integrations in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations **dashboard appears.
- On the **Integrations **dashboard:
-
Filter the integrations that are displayed on the dashboard. Select **All** to display all the integrations or select **Connected** to display only those integrations that are connected. By default, all integrations are displayed.
[See image.](#All-Connected-icons)
-
Change the layout of the dashboard. Select the **Tile View** icon to view the integrations in a tile format or select the **List View** icon to view the integrations in a list format. By default, the dashboard is displayed in the tile view.
[See image.](#card-view-and-list-view-icons)
-
View the list of all ServiceNow integrations that have been added to your organization:
In the tile view, under the **Connected Apps** section, you can view the following information:
- The status of the accounts for the integration. An oval at the top of the tile lists the number of accounts that are connected and the status of **Connected**. This number excludes accounts with a deleted status.
- The application that is associated with the integration—for example, ServiceNow.
- The integration name for each account associated with the integration.
[See image.](#ServiceNow-Card)
In the list view, under the **Connected Apps** section, you can view the following information:
- The application that is associated with the integration.
- The integration name for each account associated with the integration.
- The status of the accounts for the integration. An oval is displayed in the field listing the number of accounts that are connected and the status of **Connected. **This number excludes accounts with a deleted status.
- The number of accounts that are connected.
[See image.](#ServiceNow-List-View)
- View additional details for the ServiceNow integrations by performing one of the following steps:
- In the tile view, in the **Connected Apps **section,** **click anywhere on the **ServiceNow** tile.
-
In the list view, in the **Connected Apps** section, click **View Details **next to the ServiceNow integration.
The **ServiceNow Integration** details page appears, displaying a **Configuration Steps** tab and a **Configuration** tab. The **Configuration Steps** tab provides a link to the instructions on how to manage the Workflow Automation integration with ServiceNow. On the **Configuration** tab, you can view the list of ServiceNow integration accounts along with the status of each account, the date when each account was last modified, and the individual that performed the modification.
To display the deleted application integrations, select **Show Deleted Accounts** at the top right of the **Connected Accounts** section.
- (Optional) On the **Configuration** tab, click the **Edit** icon next to a ServiceNow integration account to view the specific details for that integration.
[]![Adding ServiceNow as a SaaS Application Tenant in the ZDX Admin Portal](/downloads/workflow-automation/setup/managing-integrations-servicenow-zdx/wa-zdx-ServiceNow-integrations-ZDX-add-integration-page.png)
[]![Viewing the ServiceNow integration tile in the Connected Apps section on the Integrations dashboard](/downloads/workflow-automation/zscaler-digital-experience/setup/managing-servicenow-integration-zdx-alerts/WA-ZDX-Integrations-Page-ServiceNow-Integration.png)
[]![Viewing the ServiceNow Integration details page in the Integrations dashboard. The Show Deleted Accounts toggle and Edit icon are highlighted.](/downloads/workflow-automation/zscaler-digital-experience/setup/managing-servicenow-integration-zdx-alerts/WA-ZDX-ServiceNow-Integration-Page-Int-Details.png)
[]![Editing the integration name for a ServiceNow integration on the ServiceNow Integration details page](/downloads/workflow-automation/zscaler-digital-experience/setup/managing-servicenow-integration-zdx-alerts/WA-ZDX-ServiceNow-Integration-Editing-Page.png)
[]![The ServiceNow Integration details page with the Disable Integration button highlighted](/downloads/workflow-automation/zscaler-digital-experience/setup/managing-servicenow-integration-zdx-alerts/WA-ZDX-ServiceNow-Integration-Editing-Page-Disable-But.png)
[]![The All and Connected Icons on the Integrations Dashboard in the Workflow Automation Admin Portal](/downloads/workflow-automation/zscaler-digital-experience/setup/managing-servicenow-integration-zdx-alerts/WA-ZDX-Integrations-Page-All-Connected-Buttons.png)
[]![The Tile View and List View icons on the Integrations dashboard](/downloads/workflow-automation/zscaler-digital-experience/setup/managing-servicenow-integration-zdx-alerts/WA-ZDX-Integrations-Page-Tile-List-View-Icons.png)
[]![Viewing the information on the ServiceNow integration tile on the Integrations dashboard](/downloads/workflow-automation/zscaler-digital-experience/setup/managing-servicenow-integration-zdx-alerts/WA-ZDX-Integrations-Page-Tile-Information.png)
[]![Viewing the ServiceNow integration list entry in the list view on the Integrations dashboard. The list view has fields for App Integration, Account Details, Status, and Account Connected.](/downloads/workflow-automation/zscaler-digital-experience/setup/managing-servicenow-integration-zdx-alerts/WA-ZDX-Integrations-Page-ListView-Information.png)