# Managing ServiceNow Integration for Events
Source: https://help.zscaler.com/workflow-automation/managing-servicenow-integration-events
PDF: https://help.zscaler.com/pdf/com/en/1500256.pdf

Workflow Automation can integrate with ServiceNow, a sanctioned Software as a Service (SaaS) application for Zscaler. For managing the Business Insights events in Workflow Automation, admins can create and assign a ServiceNow ticket to the dedicated teams using workflows. The workflow functionality in Workflow Automation has a** Notify User and Create a Ticket** template to create and assign tickets in the ticketing application. To learn more, see [Managing Workflow Templates for Events](/workflow-automation/managing-workflow-templates-events).
Prerequisites
The following prerequisites are required before you can integrate Workflow Automation with ServiceNow:
- Obtain and configure the ServiceNow application for your organization.
- Ensure that you define the different users for your organization that can use the ServiceNow application.
-
Ensure that you have admin credentials for the ServiceNow application. These credentials are required to integrate Workflow Automation with ServiceNow.
To learn more, refer to the [ServiceNow documentation](https://docs.servicenow.com/en-US/).
Integrating Workflow Automation with ServiceNow for Business Insights
To integrate Workflow Automation with ServiceNow:
- In the Business Insights Admin Portal, go to **Administration** > **Workflow Integration**.
- Click **Add SaaS Application Tenant**. The **Add SaaS Application Tenant** page appears.
-
On the **Add SaaS Application Tenant** page, configure and add the ServiceNow application as a SaaS application tenant using the ServiceNow admin credentials. This process authorizes the ServiceNow application with Business Insights and integrates the ServiceNow application with Workflow Automation. On the **Integrations** dashboard in the Workflow Automation Admin Portal, the ServiceNow application appears as a tile in the **Connected Apps** section. To learn more, see [Adding SaaS Application Tenants](/business-insights/adding-saas-application-tenant-workflow-automation).
[See image.](#add-saas-application-tenant-image)
Managing ServiceNow Integration in Workflow Automation
On the Integration dashboard in the Workflow Automation Admin Portal, admins can:
- [View ServiceNow Integrations](#view-sn-integrations)
- [Edit ServiceNow Integrations](#configure-sn-integration)
- [Disable or Enable ServiceNow Integrations](#enable-disable-sn-integration)
[]To edit a ServiceNow integration in Workflow Automation:
-
Go to **Setup** > **Integrations**. The **Integrations** dashboard appears, displaying a **ServiceNow** application tile in the** Connected Apps** section. The **Tile View** icon is selected by default.
[See image.](#Integrations-Dashboard-View-SN-Card)
-
Perform one of the following steps:
- In the tile view, in the **Connected Apps **section,** **click anywhere on the **ServiceNow** tile.
- In the list view, in the **Connected Apps** section, click **View Details **next to the ServiceNow integration.
The **ServiceNow Integration** details page appears. In the **Connected Accounts** section, all the ServiceNow integrations appear along with the status of each integration (Enabled or Disabled), the date each integration was last modified, and the name of the individual who performed the modification.
-
On the **ServiceNow Integration** details page, click the **Edit** icon next to the connected account you want to edit. The **ServiceNow Integration** editing page appears.
[See image.](#ServiceNow-Integration-Details-Page-Configure)
- On the **ServiceNow Integration** editing page, edit the name for the integration in the **Integration Name** field.
- Click **Save Changes**.
[]To disable or enable a ServiceNow integration in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations **dashboard appears, displaying a **ServiceNow** application tile in the** Connected Apps** section. The **Tile View** icon is selected by default.
-
Perform one of the following steps:
- In the tile view, in the **Connected Apps **section,** **click anywhere on the **ServiceNow** tile.
- In the list view, in the **Connected Apps** section, click **View Details **next to the ServiceNow integration.
The **ServiceNow Integration** details page appears.
- On the **ServiceNow Integration** details page, click the **Edit** icon next to a connected account with an Enabled status that you want to disable, or an account with a Disabled status that you want to enable. The **ServiceNow Integration** editing page appears.
-
On the **ServiceNow Integration** editing page, click **Disable Integration **or** Enable Integration. **The status of the integration changes to Disabled or Enabled.
[See image.](#ServiceNow-Integration-Details-Page-Disable-Enable)
You cannot enable or disable ServiceNow integrations that have been deleted.
[]To view ServiceNow integrations in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations **dashboard appears.
- On the **Integrations **dashboard:
-
Filter the integrations that are displayed on the dashboard. Select **All** to display all the integrations, or select **Connected** to display only those integrations that are connected. By default, all integrations are displayed.
[See image.](#All-Connected-icons)
-
Change the layout of the dashboard. Select the **Tile View** icon to view the integrations in a tile format, or select the **List View** icon to view the integrations in a list format. By default, the dashboard is displayed in the tile view.
[See image.](#card-view-and-list-view-icons)
- View the list of all ServiceNow integrations that have been added to your organization.
-
In the tile view, in the **Connected Apps** section, you can view:
- The status of the accounts for the integration. An oval at the top of the tile lists the number of accounts that are connected and the status of **Connected **accounts. This number does not include accounts with **Deleted** status
- The application that is associated with the integration—for example, ServiceNow.
- The integration name for each account associated with the integration.
[See image.](#ServiceNow-Card)
-
In the list view, in the **Connected Apps** section, you can view:
- The application that is associated with the integration.
- The integration name for each account associated with the integration.
- The status of the accounts for the integration. An oval in this field lists the number of accounts that are connected and the status of **Connected. **This number does not include accounts with **Deleted** status.
- The number of accounts that are connected.
[See image.](#ServiceNow-List-View)
- View additional details for the ServiceNow integrations by performing one of the following steps:
- In the tile view, in the **Connected Apps** section,** **click anywhere in the **ServiceNow** application tile.
-
In the list view, in the **Connected Apps** section, click **View Details** next to the ServiceNow application integration.
The **ServiceNow Integration** details page appears, displaying a **Configuration Steps** tab and a **Configuration** tab. The **Configuration Steps** tab provides a link to an article on how to manage the Workflow Automation integration with ServiceNow. The **Configuration** tab provides the list of ServiceNow integration accounts along with the status of each account.
To display the deleted application integrations, click **Show Deleted Accounts** at the top right of the **Connected Accounts** section.
- (Optional) On the **Configuration** tab, click the **Edit** icon next to a ServiceNow integration account to view the specific details for that integration.
[]![Adding the ServiceNow application on the Add SaaS Application Page in the Business Insights Admin Portal. The Workflow Automation checkbox is selected in the Onboard SaaS Application for section on the page.](/downloads/workflow-automation/business-insights/setup/managing-servicenow-integration-events/Business-Insights-enable-workflow-automation.png)
[]![Viewing the ServiceNow Integration tile on the Integrations dashboard](/downloads/workflow-automation/business-insights/setup/managing-servicenow-integration-events/WA-BI-Integrations-Page-ServiceNow.png)
[]![Viewing the edit icon on the ServiceNow Integration details page in the Integrations dashboard](/downloads/workflow-automation/business-insights/setup/managing-servicenow-integration-events/WA-BI-ServiceNow-Integration-Page-Edit-Icon.png)
[]![Viewing the Disable Integration button on the ServiceNow Integration editing page in the Integrations dashboard](/downloads/workflow-automation/business-insights/setup/managing-servicenow-integration-events/WA-BI-Edit-ServiceNow-Integration-Page-Disable-Integration.png)
[]![Viewing All and Connected Icons on the Integrations dashboard](/downloads/workflow-automation/business-insights/setup/managing-servicenow-integration-events/WA-BI-Integrations-Page-All-Connected-Icons.png)
[]![Viewing the Tile and List View Icons on the Integrations dashboard](/downloads/workflow-automation/business-insights/setup/managing-servicenow-integration-events/WA-BI-Integrations-Page-Tile-List-View-Icons.png)
[]![Viewing the information on the ServiceNow tile in the Integrations dashboard](/downloads/workflow-automation/business-insights/setup/managing-servicenow-integration-events/WA-BI-Integrations-Page-Tile-Information.png)
[]![Viewing the information for the ServiceNow integration in the List View on the Integrations dashboard. In the List View, the integration is listed in a table that has columns for App Integration, Account Details, Status, and Account Connected. It also contains a View Details button.](/downloads/workflow-automation/business-insights/setup/managing-servicenow-integration-events/WA-BI-Integrations-Page-ListView-Information.png)