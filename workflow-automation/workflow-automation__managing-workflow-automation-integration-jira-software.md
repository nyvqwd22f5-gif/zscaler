# Managing Workflow Automation Integration with Jira Software
Source: https://help.zscaler.com/workflow-automation/managing-workflow-automation-integration-jira-software
PDF: https://help.zscaler.com/pdf/com/en/1461951.pdf

Workflow Automation can integrate with Jira Software, a sanctioned Software as a Service (SaaS) application for Zscaler. During the remediation process for a data protection incident in Workflow Automation, admins can create and assign a Jira ticket to an incident on the Incident Details page. When the ticket action is initiated on the Incident Details page for an incident, the admin selects the user to assign to the ticket in Jira Software and specifies the Jira project where the ticket is created in Jira Software. The user they select must exist in Jira Software and must have already been added to the Integration Users page in Workflow Automation. To learn more, see [Managing Integration Users](/zia/managing-integration-users) and [Viewing & Managing Incident Details](/zia/viewing-managing-incident-details).
When configuring the Jira Software integration in Workflow Automation, you can select whether you want to sync the project list and the ticket status between Jira Software and Workflow Automation. If you choose to sync the ticket status, you can also select whether to close the incident in Workflow Automation when the ticket is completed in Jira Software. When configuring the Jira Software integration in Workflow Automation, you can specify the Jira complete status to use for the ticket closure. After Workflow Automation receives the specified complete status through the sync process, it automatically closes the incident.
The workflow functionality in Workflow Automation also has an Auto Create Tickets template that you can use to create tickets in Jira Software. To learn more, see [Managing Workflow Templates](/zia/managing-workflow-templates).
Integrating Workflow Automation with Jira Software
Before you can integrate Workflow Automation with Jira Software, you must:
- Configure the Data Loss Prevention (DLP) application integration for your organization using Amazon Web Services. Ensure that you add a DLP application integration in Workflow Automation during this process. To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services](/workflow-automation/configuring-dlp-application-integration-using-amazon-web-services).
- Obtain and configure Jira Software for your organization.
- Ensure that you define the different users for your organization who can use Jira Software.
- Ensure that you have admin credentials for Jira Software. These credentials are required to integrate Workflow Automation with Jira Software.
To learn more, refer to the [Jira Software documentation](https://confluence.atlassian.com/jirasoftware/jira-software-documentation-774242447.html).
To integrate Workflow Automation with Jira Software:
- In the ZIA Admin Portal, go to **Administration** > **SaaS Application Tenants**.
- Click **Add SaaS Application Tenant**. The **Add SaaS Application Tenant** page appears.
- On the **Add SaaS Application Tenant** page, configure and add Jira Software as a SaaS application tenant using the Jira Software admin credentials. When adding the tenant, ensure that you select the **Workflow Automation** checkbox under the **Onboard SaaS Application for** section. This process authorizes Jira Software with Zscaler Internet Access (ZIA) and integrates Jira Software with Workflow Automation. On the **Integrations** dashboard in Workflow Automation, the Jira Cloud tile appears in the **Connected Apps** section. To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
[See image.](#add-saas-application-tenant-image)
Managing Jira Software Integrations in Workflow Automation
On the Integrations dashboard in the Workflow Automation Admin Portal, admins can:
- [Configure Jira Software Integrations](#configure-jira-software-integrations)
- [Edit Jira Software Integrations](#edit-jira-software-integration)
- [Disable or Enable Jira Software Integrations](#enable-disable-jira-software-integration)
- [View Jira Software Integrations](#view-jira-software-integrations)
[]To configure a Jira Software integration in Workflow Automation:
- [1. Configure project settings for a Jira Software integration.](#configure-project-setting)
- [2. Configure integration settings for a Jira Software integration.](#configure-integration)
[]Before you can create a Jira Software ticket on the Incident Details page in Workflow Automation, you must configure the project settings for the Jira projects in Workflow Automation. This process includes defining the field mappings for the project and specifying a complete status for the project. To learn more, see [Viewing & Managing Incident Details](/zia/viewing-managing-incident-details).
To configure project settings for a Jira Software integration in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations** dashboard appears, displaying a **Jira Cloud** application tile in the** Connected Apps** section. The **Tile View** icon is selected by default.
[See image.](#Integration-Dashboard-Configure-Projects)
- Perform one of the following steps:
- In the tile view, in the **Connected Apps **section, click anywhere on the **Jira Cloud** tile.
- In the list view, in the **Connected Apps** section, click **View Details **next to the Jira Cloud integration.
The **Jira Integration** details page appears. In the **Connected Accounts** section, all the Jira Cloud integrations appear along with their statuses (Enabled and Disabled). To display the deleted application integrations, click **Show Deleted Accounts** at the top right of the **Connected Accounts** section.
[See image.](#Jira-Integration-Details-Page-Configure-Projects)
- On the **Jira Integration** details page, click the **Expand** icon for a connected account. The Jira projects display along with their metadata associated with the Jira Cloud integration. When you enable the Jira Cloud integration for the first time, all the projects and their metadata for the Jira Cloud integration are synced with Workflow Automation and are displayed on the page.
[See image.](#Jira-Integration-Details-Page-Expand-Account)
- (Optional) At the top right of the project details section, click **Sync Project List **to manually sync the Jira Cloud integration project list with Workflow Automation.
- In the project details section, configure the complete status settings for each project associated with the Jira Cloud account. From the **Complete Status** drop-down menu, select a status for when the Jira tickets are considered complete in the project in the Jira Software application. If a status has not been selected, **Click to change status** appears for the **Complete Status** field. All the completed statuses for the project in Jira Software are available for selection—for example, **In Progress**, **To Do**, **In Review**, **Done**, and **Closed**.
[See image.](#Jira-integration-Details-page-select-complete-account)
- Enter the field mapping for the Jira tickets in the project between the Jira Cloud integration and Workflow Automation.
- Click the **Add Field Mapping** icon next to a project. The **Required Fields Mappings** page appears.
[See image.](#Required-Field-Mappings-Initial-Page)
- On the **Required Fields Mappings** page, select an issue type from the **Issue Type** drop-down menu. The menu displays the issue types available for that project in the Jira Cloud account (e.g., **Task**, **Bug**, and **Epic**). After you select an issue type, all the required Jira fields for that project and issue type are listed on the page and cannot be deleted. The system automatically maps the Issue Type Jira field for you. For the **Issue Type** field, the **Zscaler Fields **value is set to **None** and the **Default Value** is set to the same value as the issue type that you selected. You cannot edit or delete the Issue Type Jira field mapping.
- Enter the field mapping for all the other required Jira fields:
- Next to the required field:
- If applicable, from the **Zscaler Fields** drop-down menu, select the Zscaler field that you want to map to that Jira field. The drop-down menu displays all Zscaler fields that are available on the Incident Details page.
- If applicable, set a default value that you want to map to that Jira field. Enter the **Default Value** field or select the default value from the **Default Value** drop-down menu. Some fields that have predefined values have a drop-down menu that you can select from, and other fields allow you to enter a value.
- Click **Save**. The field mapping is configured. After you map the last required field and save it, the **Add More** button becomes available. You can only edit a required field mapping. You cannot delete required field mappings.
[See image.](#Required-Field-Mappings-Page-All-Required)
- (Optional) Add optional Jira field mappings for the ticket:
- Click the **Add More** button. An additional row appears at the bottom of the table.
- In the new row:
- From the **Jira Fields** drop-down menu, select the optional Jira field.
- If applicable, from the **Zscaler Fields** drop-down menu, select the Zscaler field to map to this Jira field. All potential Zscaler fields that match this Jira field are available in the drop-down menu.
- If applicable, enter the default value that you want to map to that Jira field in the **Default Value** field or select the default value from the **Default Value** drop-down menu. Some fields that have predefined values have a drop-down menu that you can select from, and other fields allow you to enter a value.
- Click **Save **at the end of the row. The field mapping is configured.
[See image.](#Required-Field-Mappings-Page-Optional-Fields)
You can edit or delete optional field mappings.
[]To configure integration settings for a Jira Software integration in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations** dashboard appears, displaying a **Jira Cloud** application tile in the** Connected Apps** section. The **Tile View** icon is selected by default.
[See image.](#Integrations-Dashboard-View-Jira-Cloud-Card)
- Perform one of the following steps:
- In the tile view, in the **Connected Apps **section, click anywhere on the **Jira Cloud** tile.
- In the list view, in the **Connected Apps** section, click **View Details **next to the Jira Cloud integration.
The **Jira Integration** details page appears. In the **Connected Accounts** section, all the Jira Cloud integrations appear along with their statuses (Enabled and Disabled). To display the deleted application integrations, click **Show Deleted Accounts** at the top right of the **Connected Accounts** section.
[See image.](#Jira-Integration-Details-Page-Configure)
- On the **Jira Integration** details page, click the **Edit** icon next to the connected account you want to configure. The **Jira Integration** editing page appears.
- On the **Jira Integration** editing page:
- (Optional) **Integration Name**: Edit the integration name.
- (Optional) **Sync project list**: Select this checkbox if you want to automatically sync the project list between the Jira Cloud integration and Workflow Automation. The sync process runs daily. To manually sync the project list, on the **Jira Integration** details page, click the **Sync Project List** button at the top right of the project details section.
- (Optional) **Sync ticket status**: Select this checkbox if you want to sync the ticket status between the Jira Cloud integration and Workflow Automation. The sync process runs daily. On the **Incident Details** page in Workflow Automation, only the complete status that you specified for a project appears in the Ticket section for an incident. This status appears when a ticket matches that complete status for the project in the Jira Cloud integration. None of the other Jira Cloud integration ticket statuses appear on the **Incident Details** page. After you select this checkbox, the **Close incident when ticket is closed** checkbox appears on the page.
-
(Optional) **Close incident when ticket is closed**: Select this checkbox if you want Workflow Automation to automatically close the incident in Workflow Automation when the Jira ticket matches the complete status you defined for the project on the **Jira Integration** details page. If you do not select this checkbox, Workflow Automation does not automatically close the ticket.
[See image.](#Edit-Jira-Integration-Page-Configure-Settings)
- Click **Save Changes**.
[]You can edit both project settings and integration settings for a Jira Software integration in Workflow Automation.
- [Editing Project Settings for a Jira Software Integration.](#edit-project-settings-for-integration)
- [Editing Integration Settings for a Jira Software Integration.](#edit-jira-software-configuration-fields)
[]To edit project settings for a Jira Software integration in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations** dashboard appears, displaying a **Jira Cloud** application tile in the** Connected Apps** section. The **Tile View** icon is selected by default.
[See image.](#Integrations-Dashboard-Edit-Project-Settings)
- Perform one of the following steps:
- In the tile view, in the **Connected Apps **section,** **click anywhere on the **Jira Cloud** tile.
- In the list view, in the **Connected Apps** section, click **View Details **next to the Jira Cloud integration.
The **Jira Integration** details page appears. In the **Connected Accounts** section, all the Jira Cloud integration accounts appear along with the status of each account (Enabled and Disabled), the date each account was last modified, the name of the individual who performed the modification, the total number of projects for the account, and the total number of mapped projects for the account. To display the deleted application integrations, click **Show Deleted Accounts** at the top right of the **Connected Accounts** section.
[See image.](#Jira-Integration-Details-Page-Edit-Project-Settings)
- On the **Jira Integration** details page, click the **Expand** icon for a connected account. The Jira projects display along with their metadata associated with the Jira Cloud integration. When you enable the Jira Cloud integration for the first time, all the projects and their metadata for the Jira Cloud integration sync with Workflow Automation and display on the page.
[See image.](#Jira-Integration-Details-Page-Edit-Project-Settings-Expand-Row)
- (Optional) In the top right of the project details section, click **Sync Project List **to manually sync the Jira Cloud integration project list with Workflow Automation.
- (Optional) In the project details section, modify the complete status settings for each project associated with the Jira Cloud account. Select a different status from the **Complete Status** drop-down menu for each project.
- Edit the field mapping for the Jira tickets in the project between the Jira Cloud integration and Workflow Automation.
- Click the **View Field Mapping** icon next to a project. The **Required Fields Mappings** page appears, listing all the current field mappings.
- On the **Required Fields Mappings** page:
- Edit the existing values or enter new field mapping values for each required field for the Jira issue type. In the **Action** column, click **Save**. You cannot delete a required field value mapping.
- Edit the field mapping values for each existing optional field for the Jira issue type and click **Save **in the** Action **column. Alternatively, click **Add More** and configure a new optional field mapping and click **Save **in the **Action **column.
You can delete optional field mappings. To delete an optional field mapping, click **Delete** in the **Action** column.
[]To edit integration settings for a Jira Software integration in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations **dashboard appears, displaying a **Jira Cloud** application tile in the** Connected Apps** section. The **Tile View** icon is selected by default.
[See image.](#Integrations-Dashboard-Edit-Configuration-Settings)
- Perform one of the following steps:
- In the tile view, in the **Connected Apps** section,** **click anywhere on the **Jira Cloud** tile.
- In the list view, in the **Connected Apps** section, click **View Details **next to the Jira Cloud integration.
The **Jira Integration** details page appears. In the **Connected Accounts** section, all the Jira Cloud integration accounts appear, along with the status of each account (Enabled and Disabled), the date each account was last modified, the name of the individual who performed the modification, the total number of projects for the account, and the total number of mapped projects for the account. To display the deleted application integrations, click **Show Deleted Accounts** at the top right of the **Connected Accounts** section.
[See image.](#Jira-Integration-Details-Page-Edit-Config-Settings)
- On the **Jira Integration **details page, click the **Edit** icon next to the connected account you want to edit. The **Jira Cloud Integration** editing page appears.
[See image.](#Edit-Jira-Cloud-Integration-Page-Edit-Config-Settings)
- On the **Jira Integration** editing page, edit any of the fields that are displayed.
- Click **Save Changes**.
[]To disable or enable a Jira Software integration in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations **dashboard appears, displaying a **Jira Cloud** application tile in the** Connected Apps** section. The **Tile View** icon is selected by default.
[See image.](#Integrations-Dashboard-Enable-Disable)
- Perform one of the following steps:
- In the tile view, in the **Connected Apps **section,** **click anywhere on the **Jira Cloud** tile.
- In the list view, in the **Connected Apps** section, click **View Details **next to the Jira Cloud integration.
The **Jira Integration** details page appears. In the **Connected Accounts** section, all the Jira Cloud integration accounts appear, along with the status of each account (Enabled and Disabled), the date each account was last modified, the name of the individual who performed the modification, the total number of projects for the account, and the total number of mapped projects for the account.
[See image.](#Jira-Integration-Details-Page-Enable-Disable)
- On the **Jira Integration** details page, click the **Edit** icon next to a connected account with an Enabled status that you want to disable or an account with a Disabled status that you want to enable. The **Jira Integration** editing page appears.
- On the **Jira Integration** editing page, click **Disable Integration **or** Enable Integration. **The status of the integration changes to Disabled or Enabled. You cannot enable or disable Jira Cloud integrations that have been deleted.
[]To view Jira Software integrations in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations **dashboard appears.
- On the **Integrations **dashboard:
- Filter the integrations that are displayed on the dashboard. Select **All** to display all the integrations or select **Connected** to display only those integrations that are connected. By default, all integrations are displayed.
[See image.](#All-Connected-icons)
- Change the layout of the dashboard. Select the **Tile View** icon to view the integrations in a tile format or select the **List View** icon to view the integrations in a list format. By default, the dashboard displays in the tile view.
[See image.](#card-view-and-list-view-icons)
- View the list of all Jira Cloud integrations that have been added to your organization:
In the tile view, in the **Connected Apps** section, you can view the following information:
- **App**: The application that is associated with the integration (e.g., **Jira Cloud**).
- **Account Details**: The integration name for each account associated with the integration.
- **Status**: The status of the accounts for the integration. An oval at the top of the tile lists the number of accounts that are connected and the status of **Connected**. This number does not include accounts with a Deleted status.
[See image.](#Jira-Cloud-Card)
In the list view, in the **Connected Apps** section, you can view the following information:
- **App Integration:** The application that is associated with the integration.
- **Account Details**: The integration name for each account associated with the integration.
- **Status**: The status of the accounts for the integration. An oval in this field lists the number of accounts that are connected and the status of **Connected. **This number does not include accounts with a Deleted status.
- **Account Connected**: The number of accounts that are connected.
[See image.](#Jira-Cloud-List-View)
- View additional configuration details for the Jira Cloud integrations:
- On the **Integrations** dashboard, perform one of the following steps:
- In the tile view, in the **Connected Apps **section,** **click anywhere in the **Jira Cloud** tile.
- In the list view, in the **Connected Apps** section, click **View Details** next to the Jira Cloud application integration.
The **Jira Integration** details page appears, displaying a **Configuration Steps** tab and a **Configuration** tab. The **Configuration Steps** tab provides a link to the instructions on how to manage the Workflow Automation integration with Jira Software. On the **Configuration** tab, you can view the list of Jira Cloud integration accounts along with the status of each account (Enabled and Disabled), the date when each account was last modified, the name of the individual who performed the modification, the total number of projects for the account, and the total number of mapped projects for the account. To display the deleted application integrations, click **Show Deleted Accounts** at the top right of the **Connected Accounts** section.
- On the **Configuration** tab, click the **Edit** icon next to a Jira Cloud integration account to view the configuration details for that integration.
- View project settings for the Jira Cloud integrations:
- On the **Integrations** dashboard, perform one of the following steps:
- In the tile view, in the **Connected Apps** section,** **click anywhere in the **Jira Cloud** tile.
- In the list view, in the **Connected Apps** section, click **View Details** next to the Jira Cloud application integration.
The **Jira Integration** details page appears, displaying a **Configuration Steps** tab and a **Configuration** tab.
- On the **Jira Integration** details page, click the **Expand** icon for a connected account. The project details section appears, listing all the project configurations for that account. To view all projects (mapped and unmapped) for the integration, select **All **at the top of the section. To view projects that have been mapped, select **Only Mapped** at the top of the section. In the project details section, you can see:
- **Project**: The name of the project.
- **Modified By**: The name of the user who modified the project settings.
- **Complete Status**: The complete status specified for the project. If a status has not been selected, **Click to change status** appears for the field.
- **Auto Sync**: Indicates whether auto sync is **Enabled** or **Disabled** for the project. To view the reason the auto sync is disabled, click the **Information** icon next to the **Disabled** status. You can disable auto sync for the following reasons:
- **Mapping is Empty**: The field mapping has not been added for the project using this section of the page. Click the **Add Field Mapping** icon next to a project to add the field mapping for the project.
- **Labels Not Supported**: The Labels field is not supported for the project in the Jira Software application. Workflow Automation uses labels to search for and sync the tickets in Jira Software with the tickets on the Incident Details page in Workflow Automation. To correct this issue, you must add the **Labels** field to the project in Jira Software.
- **Field Mappings**: Displays either the **Add Field Mapping** icon or the **View Field Mapping** icon. The **Add Field Mapping** icon appears if no field mapping has been added for the project. The **View Field Mapping** icon appears if field mapping has been added for the project.
[See image.](#Jira-Cloud-Integration-Details-Page-View-All-Projects)
- To view the existing field mapping for the project, click the **View Field Mapping** icon next to a project. The **Required Fields Mappings** page appears, displaying the existing field mappings.
[See image.](#Required-Field-Mappings-Page-View-Mappings)
[]![Adding Jira Software as a SaaS Application Tenant in the ZIA Admin Portal](/downloads/zia/policies/data-loss-prevention/zscaler-workflow-automation/setup/managing-workflow-automation-integration-jira-software/ZIA-WA-Add-SaaS-Application-Tenant-Page-Jira.png)
[]![Viewing the Jira Cloud tile on the Integrations dashboard in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Integrations-Dashboard-Viewing-Jira-Integration-Tile.png)
[]![Viewing the Jira Integration details page for an integration in the Integrations dashboard](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Jira-Integration-Details-Page-Enabled-Status.png)
[]![Viewing the Jira Integration details page with an account row expanded in the Integrations dashboard](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Jira-Integration-Details-Page-Expand-Integration-Account.png)
[]![Selecting the complete status for a project on the Jira Cloud Integration Details page in the Integrations Dashboard](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Jira-Integration-Details-Page-Complete-St.png)
[]![Viewing the Required Fields Mapping page in the Integrations dashboard](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Required-Fields-Mapping-Page-Initial.png)
[]![Viewing the Required Fields Mapping page with all the required fields entered in the Integrations dashboard](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Required-Fields-Mapping-Page-All-Required.png)
[]![Required Fields Mapping page with optional fields entered in the Integrations dashboard](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Required-Fields-Mapping-Optional-Entered.png)
[]![Viewing the Jira Cloud tile on the Integrations dashboard in the Workflow Automation Admin Portall](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Integrations-Dashboard-Viewing-Jira-Integration-Tile2.png)
[]![Viewing the Jira Integration details page with an account enabled in the Integrations dashboard](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Jira-Integration-Details-Page-Enabled-Status2.png)
[]![Configuring Jira Cloud configuration settings on the Jira Integration editing page in the Integrations dashboard](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Jira-Integration-Editing-Page.png)
![Viewing the Jira Cloud tile on the Integrations dashboard in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Integrations-Dashboard-Viewing-Jira-Integration-Tile3.png)
[]
[]![Viewing the Jira Integration details page with an account that has been edited in the Integrations dashboard](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Jira-Integration-Details-Page-After-Edit.png)
![Viewing the Jira Integration details page with an account row expanded in the Integrations dashboard](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Jira-Integration-Details-Page-Expand-Integration-Account2.png)
[]
[]![Viewing the Jira Cloud tile on the Integrations dashboard in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Integrations-Dashboard-Viewing-Jira-Integration-Tile4.png)
[]![Viewing the Jira Integration details page with an account that has been edited in the Integrations dashboard](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Jira-Integration-Details-Page-After-Edit2.png)
[]![Viewing the Jira Integration details page with an account that has been edited in the Integrations dashboard](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Jira-Integration-Editing-Page2.png)
[]![Viewing the Jira Cloud tile on the Integrations dashboard in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Integrations-Dashboard-Viewing-Jira-Integration-Tile5.png)
[]![Viewing the Jira Integration details page with an account that has been edited in the Integrations dashboard](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Jira-Integration-Details-Page-After-Edit3.png)
[]![Viewing the All and Connected icons on the Integrations dashboard in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-JiraIntegration-Integrations-Dashboard-All-Connected-Icons.png)
[]![Viewing the Tile and List View icons on the Integrations dashboard in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-JiraIntegration-Integrations-Dashboard-Tile-Listview-Icons.png)
[]![Viewing the Jira Cloud Integration tile in the Integrations dashboard in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-JiraIntegration-Integrations-Dashboard-JiraCloud-Tile.png)
[]![Viewing the Jira Cloud list entry in the list view on the Integrations dashboard in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-JiraIntegration-Integrations-Dashboard-List-View.png)
[]![Viewing the Jira Integration details page with an account row expanded in the Integrations dashboard](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Jira-Integration-Details-Page-Expand-Integration-Account3.png)
[]![Viewing all the existing field mappings on the Required Fields Mapping page in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/managing-workflow-automation-integration-jira-software/WA-Required-Fields-Mapping-Optional-Entered2.png)