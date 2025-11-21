# Configuring Azure DevOps Outegration
Source: https://help.zscaler.com/uvm/configuring-azure-devops-outegration
PDF: https://help.zscaler.com/pdf/com/en/1532592.pdf

The Azure DevOps outegration is used to dispatch tickets from the Zscaler Security Operations (SecOps) platform applications (e.g., UVM) to your Azure DevOps project, enabling you to track and assign tickets to a specific team for analysis and remediation.
This article is a step-by-step guide to configuring the Azure DevOps work management outegration.
Each Azure DevOps ticket type (e.g., Bug, Task, Feature) requires a separate outegration configuration.
Prerequisites
Before configuring the outegration, ensure that you complete the authentication and retrieve the Client ID, Client Secret, Tenant ID, organization name, and project name.
- [Authentication Workflow](#uvm-authentication)
[]
- Log in to the [Azure portal.](https://portal.azure.com/#home)
- Go to **App registrations**.
[See image.](#ds-app-reg-image-1)
-
Create a new application.
- On the **Register an application** page, enter a name for the application.
- Select **Accounts in any organizational directory (Any Microsoft Entra ID tenant - Multitenant)**.
- Click **Register**.
[See image.](#ds-reg-image)
The **Overview **page appears when the application is created.
If you have already registered an application, then proceed to create the client secret.
- []Copy and save the **Application (client) ID** and **Directory (tenant) ID**.
[See image.](#uvm-overview)
- In the left-side navigation, go to **Manage **> **Authentication**.
- Click **Add a Platform **and select **Web**.
- Under **Configure Web**, enter `https://app.avalor.io/oauth` as the application's redirect URI.
[See image.](#uvm-configure-web)
- Click **Configure**.
- In the left-side navigation, go to **Manage **> **API Permissions**.
- Click **Add a permission **and add the following permissions:
- Azure DevOps: vso.project_manage
- Azure DevOps: vso.work_write
- Microsoft Graph: offline_access
- Microsoft Graph: User.Read
- In the left-side navigation, go to **Manage **> **Certificates & Secrets**.
- Create a new client secret, select an expiration time, and save the value.
[See image.](#uvm-client-secret-image)
- Enter all the retrieved credentials (client ID, tenant ID, and client secret) in the **Authentication **section on the Create Azure DevOps Outegration page.
A unique** Authentication ID **is generated when the authentication is successful.
[See image.](#ds-authentication)
- On the Azure DevOps dashboard, copy your organization's name displayed at the top of the left-side navigation.
-
On the **Projects** tab, copy the project name.
[See image.](#uvm-details)
[]
![Details to add a client secret](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/ds-client-secret.png)
[]
![Organization and project names in the Azure DevOps portal](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-org-project.png)
[]
![The unique authentication ID generated](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-auth-id.png)
[]
![App Registration option in Azure portal](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/UVM-app-reg-new.png)
[]
![Application ID and Directory ID details](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/UVM-ID.png)
[]
![Redirect URI on Configure Web page](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-configure-web.png)
[]
![The page to register a new application](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/ds-app-reg-1.png)
Configuring the Azure DevOps Outegration
To configure the Azure DevOps outegration, complete the following steps:
- [Step 1: Authenticate the Azure DevOps Connection (Connect)](#step1-azure-authentication)
- [Step 2: Configure the Outegration Visibility and Behavior (Settings)](#step2-azure-settings)
- [Step 3: Map the Outegration Fields (Mapping)](#step3-azure-mapping)
- [Step 4: Configure the Azure DevOps Webhook](#step4-azure-webhook)
[]
To establish a secure connection with the Azure DevOps project, you need to authenticate with the client ID, tenant ID, and client secret you [previously saved](#copytheid).
-
In the SecOps platform, go to **Configure** > **Outegrations**.
[See image.](#configure-outegrations)
- Click **Create** and select **Azure DevOps**.
-
In the **Details** section:
- **Display Name**: Enter a name for your outegration from the Azure DevOps dashboard.
- **Organization**: Enter the name of your organization from the Azure DevOps dashboard.
- **Project**: Enter the name of the project.
- **Authentication**: Select an existing authentication ID, or click **Create New** to set up a new authentication and enter the required parameters you retrieved earlier into the corresponding fields.
[See image.](#uvm-authentication-section)
- (Optional) **Refresh Token** and **Access Token**: Enter the values if required.
[See image.](#jira-outegration-connect)
- Click **Test** in the bottom-right corner of the page to verify the connection. If the credentials are invalid, an error message is displayed along with the remediation steps to resolve the issue.
- After the connection is verified, click **Next **to proceed to the **Settings **step.
[]
![List of outegrations](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-azure-authentication.png)
[]
![Azure DevOps outegration setup details](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-azure-connect.png)
[]
![Azure DevOps outegration authentication setup](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-authentication-section.png)
[]
In this step, you need to set the SecOps entity that triggers the Azure DevOps ticket dispatch, the Azure DevOps ticket type that the SecOps ticket should be dispatched to, and when the Create Azure DevOps Ticket button should appear in the application. The Create Azure DevOps Ticket button allows users with access to SecOps tickets to dispatch these tickets to an Azure DevOps project directly from the SecOps ticket drawer or from the SecOps tickets page.
- In the **Advanced Settings** section:
-
**Create Azure DevOps item from**:** **Select the entity that you want to configure the outegration for. This selection affects the view you configure in the <Entity> **View **step (e.g., selecting Ticket displays the Tickets View setting).
- **UVM**: Select **Ticket**.
- **AEM**: Select **Policy Violation** or **Violation Ticket**.
Other entity types might be visible depending on the apps enabled in your account.
[See image.](#create-azure-data-center-item-field)
-
**Work Item Type**:** **Select the work item. The schema associated with the selected work item is retrieved from your Azure DevOps project and made available for mapping in the [Mapping step](#mappingstep).
[See image.](#issue-type-field)
-
In the <Entity> **View** section, select how the SecOps ticket should display the **Create Azure DevOps **button. This setting can be modified at any time.
- **Always**: Select to display the button on all tickets, allowing users to dispatch all tickets to an Azure DevOps issue.
- **Never**: Select to hide the button in all tickets. This is useful during the outegration* *setup process to hide the button from users while still keeping the outegration active.
- **For specific tickets**: Display the button for specific tickets. For example, if your organization uses multiple ticketing systems, you can display the button only to users who work with Azure DevOps, while excluding those using other ticketing systems (e.g., ServiceNow).
[See image.](#tickets-view-setting)
The **Create ****Azure DevOps ****Ticket **button appears at two locations:
-
In the individual entity drawer (e.g., in the [UVM ticket drawer](/uvm/managing-tickets-uvm), in the [AEM violation ticket drawer](/uvm/managing-violation-tickets-aem)).
[See image.](#button-in-ticket)
-
On the entity page in the relevant application (e.g., on the [Tickets page](/uvm/about-tickets-operational-view-uvm) in UVM, on the [Violation Tickets page](/uvm/about-violation-tickets-operational-view-aem) in AEM).
[See image.](#button-in-tickets-view)
- Click **Map **to proceed to the **Mapping** step.
[]![Advanced Settings options](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-advanced-settings.png)
[]![List of work item types](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-work-item.png)
[]![Tickets View details](/downloads/uvm/configure/outegrations/jira-outegration/60122c5d-0dfb-423e-92f6-fde718ae5cb4.png)
[]![Create Azure DevOps Ticket button in a ticket](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/image%20(2).png)
[]![Create Azure DevOps button on the Tickets page](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/image%20(1).png)
[]Map the SecOps and Azure DevOps tickets to enable exchange of data.
The objective of the mapping process is to map SecOps ticket fields (left) to Azure DevOps fields (right). To map values to fields, configure values on the left to populate the fields selected on the right.
[See image.](#jira-outegration-mapping-right-left)
There are three mapping components:
- Tickets initially dispatched to Azure DevOps: Map SecOps ticket fields (left) to Azure DevOps fields (right) for the initial dispatch of a ticket to an Azure DevOps issue. You can also add an attachment to your Azure DevOps issue. Commonly mapped fields include Summary, Description, Assignee, Priority, Due Date, and Status.
- (Optional) Sync from ticket to Azure DevOps: Map SecOps ticket fields (left) to Azure DevOps fields (right) for syncing ticket updates to Azure DevOps, including configuring comments and adding an attachment to your Azure DevOps ticket. Commonly mapped fields include Status and Due Date.
- (Optional) Sync from Azure DevOps to ticket: Map Azure DevOps fields (left) to SecOps ticket fields (right) for syncing Azure DevOps updates to tickets. This step also requires setting up an Azure DevOps webhook. Commonly mapped fields include Ticket Status and Ticket SLA.
The initial Azure DevOps outegration mapping includes preconfigured default mappings for each part, based on common use cases and industry best practices. These defaults can be modified and customized as needed.
Creating a New Mapping
[]To create a new mapping from a SecOps ticket to an Azure Devops ticket:
- Select a field (right):
[See image.](#uvm-right-filed)
- Click** Mapping**.
-
Select a field on the right.
The field's schema details open on the right of the page. The schema lists the Azure DevOps fields that can be used for mapping. This is the list of fields configured in your Azure DevOps project for the Work Item Type selected in the [Settings](#step2-azure-settings) step (e.g., Bug).
[See image.](#priority-schema-fields)
The following details are specified for fields, when available:
- [Required](#schema-required)
- [Input Type](#schema-input-type)
- [Available Options](#schema-available-options)
- Configure the field value (left):
-
Click **Add value** on the left.
The **Field Editor** appears.
- In the **Field Editor**, select one of the following methods to configure the value of the field:
- [Field (Dictionary)](#field-dictionary)
- [Smart Text](#smart-text)
- [Script](#script-python)
Repeat** **the mapping process for all required Azure DevOps fields and for any other fields you want to map.
In addition to the mapping of fields on the right to fields on the left, you can perform a set of actions when setting up the Azure DevOps outegration mapping, each relevant to a specific part of the mapping.
- [Set a ticket field as mandatory.](#set-as-mandatory)
- [Add attachments to the ticket dispatch.](#attachments)
- [Configure comments synchronization.](#comments)
Mapping Ticket Title to Summary
To illustrate the mapping process, consider the mapping of the required Azure DevOps Summary field. The final result of the mapping process should show the Summary field on the right, and the Ticket Title field on the left.
![Mapping ticket title to summary](/downloads/uvm/configure/outegrations/jira-outegration/75f223d1-3181-4d51-b496-339c74a3fa46.png)
To map the Ticket Title field to the Summary field:
-
Select **Summary **as the Azure DevOps field on the right.
[See image.](#example-jira-summary-right)
Selecting the Azure DevOps Summary field opens the field's details in the schema. The schema specifies that the field is required and thus must be mapped before the outegration can be saved, and that the field expects a TEXT input type. Therefore, the field for which a value is being configured must also be of TEXT type.
[See image.](#example-summary-schema)
-
Select the **Ticket Title **field on the left:
- Click** Add Value**.
- Under the **Field** tab, select the **Ticket Title** field, which is the equivalent to the Azure DevOps **Summary **field.
[See image.](#example-ticket-title-field)
Previewing the Ticket to Azure DevOps Mapping
After completing the SecOps ticket to Azure DevOps dispatch mapping, preview the mapping to review the configuration. This helps ensure that ticket dispatch is behaving as expected and that the Azure DevOps issue fields are populated correctly.
To preview the mapping, click **Preview **on the bottom right of the ticket initially dispatched to Azure DevOps section. The Mapping Preview window appears. On the left of the Mapping Preview window, there is a sample of the tickets in your account, organized by ticket ID. You can select, filter, or search tickets and preview the mapping to their corresponding Azure DevOps issue. You can also open the actual ticket in a new tab for a more in-depth review.
[See image.](#preview)
Common Mapping Examples
These mapping examples highlight commonly used field configurations in your outegration. While some might be preconfigured by default, Zscaler recommends reviewing and customizing them to ensure they align with your workflow.
- [Ticket to Azure DevOps Description](#mapping-ticket-jira-description)
- [Ticket SLA to Azure DevOps Due Date Sync](#mapping-Azure_Devops-due-date-ticket-sla)
- [Azure DevOps to Ticket Status Sync](#mapping-jira-status-ticket-status)
[]
![Mapping fields to populate on the right](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-field-right.png)
[]![Outegration schema field options](/downloads/uvm/configure/outegrations/jira-outegration/1b61b2af-6437-4d24-ad59-e8429252c3c1.png)
[]The Required attribute is TRUE if a field is required by Azure DevOps. If a field is not required, the attribute is not displayed. A required Azure DevOps field is also indicated by a red asterisk (*) on the Azure DevOps field in the first mapping step.
Required Azure DevOps fields must be mapped before saving the outegration.
[]The Input Type specifies the data type of the Azure DevOps field, such as TEXT (e.g., Summary), DATE (e.g., Due Date), or NUMBER (e.g., Risk Score). This indicates the format that the selected source field must match to successfully map to the Azure DevOps field.
[]For Azure DevOps fields with fixed values, the Available Options column displays the available values. For example, if the Azure DevOps field Priority is configured to include the following fixed values—High, Low, Medium, Lowest, Highest—the corresponding values in the Ticket Severity field can be mapped to these values.
[]![Data Mapping details](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-filed%20to%20populate.png)
[]![Field details in the schema](/downloads/uvm/configure/outegrations/jira-outegration/bb42ebaf-93e6-4b90-be96-6c5a9064f9bf.png)
[]Select a field on the left to populate the field on the right.
The field dictionary allows you to create mappings between specific values from the field on the right and values of the field on the left. To use the dictionary, you must first select a field on the right and a field to populate it with on the left.
For example, if your Azure DevOps Priority field includes the following fixed values—Highest, High, Medium, Low, Lowest—you can use the dictionary to map the corresponding Ticket Severity values to each of the Priority field values.
[See image.](#example-dictionary)
[]![Create mappings between specific values from the field on the right and values from the field on the left](/downloads/uvm/configure/outegrations/jira-outegration/a01c0fe8-5f42-4b60-8ea9-8c71572c7c8e.png)
[]Configure the field value using free text, or create a template using a combination of free text and selected fields. This allows you to dynamically insert specific field values (e.g., Ticket SLA, Ticket Assignee, or Asset Name) into customized free text sentences or paragraphs.
To add a Smart Text field, enclose it in double curly brackets (e.g., `{{Ticket Assignee}}`). The field's display name automatically translates to its system name.
This option is commonly used to configure the value of fields like Ticket Title and Ticket Description.
[See image.](#example-smart-text)
[]![Adding a Smart Text field](/downloads/uvm/configure/outegrations/jira-outegration/908f493f-957e-4794-9cd7-62cc4f83b0ff.png)
[]For use cases that require more advanced configuration than either of the previous two methods, you can use Python scripts to configure the field value to be mapped to the target field.
[]![Define the Ticket Title field using the Field Editor](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-filed.png)
[]When dispatching tickets to Azure DevOps, map the Azure DevOps Description field with a summary of the Ticket content to provide remediation teams with a brief overview of the ticket.
To configure the Ticket to Azure DevOps Description mapping:
- Click** Mapping**.
- Select** Description** as the field on the** **right.
-
Click **Add Value** on the left.
The **Field Editor** appears.
- In the **Field Editor**, select **Smart Text**.
- Enter a ticket description, including dynamic fields (e.g., `{{SLA}}`).
Tickets dispatched to Azure DevOps will now include the configured description.
[]In the Ticket to Azure DevOps sync, map the Azure DevOps Due Date field to keep timelines in sync with Ticket SLA changes.
To configure the Ticket SLA to Azure Devops Due Date mapping:
- Click** Mapping**.
- Select** Due Date** as the field on the right.
-
Click** Add Value** on the left.
The **Field Editor** appears.
- In the **Field Editor**, select **Field**, and select **Ticket SLA** as the field on the left.
Ticket SLA changes will now automatically update Azure DevOps issue due dates.
[]In the Azure DevOps to Ticket sync, map the Ticket Status field to ensure it's updated when remediation teams change the Azure DevOps Issue Status.
To configure the Azure DevOps to Ticket Status mapping:
- Click** Mapping**.
- Select** Ticket Status** as the field on the right.
-
Click** Add Value** on the left.
The **Field Editor** appears.
- In the **Field Editor**, select **Field**, and select **Status** as the field on the left. Use the dictionary to map your Azure DevOps **Status** types to **Ticket Status** types.
Azure DevOps issue Status changes will now automatically update the Ticket Status.
[]![Mapping Preview details](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-mapping-preview.png)
[]You can set a SecOps ticket field as mandatory by selecting the **Set as Mandatory **checkbox in the Column Menu to the right of the mapping. Some fields can be set as mandatory by default.
[See image.](#set-as-mandatory-checkbox)
Setting a field as mandatory guarantees that critical fields (e.g., Ticket Assignee) are always populated before a ticket is dispatched, so Azure DevOps tickets are always actionable for your remediation teams. Attempts to dispatch a ticket without a value in a mandatory field will trigger an error message.
Required fields are defined by your Azure DevOps schema, whereas mandatory fields are for SecOps ticket dispatch.
[]![Select the Set as Mandatory checkbox to set a SecOps ticket field as mandatory](/downloads/uvm/configure/outegrations/jira-outegration/83d803fe-06d1-4895-bb53-bf66703b351f.png)
[]You can create a file attachment that summarizes your ticket content and set the trigger to automatically add it to your Azure DevOps issue. Adding an attachment to your Azure DevOps issue simplifies the review and management of findings dispatched from a ticket.
You can configure file attachments in two of the mapping steps:
-
Initial ticket dispatch
[See image.](#attachment-intial-dispatch)
-
Sync from ticket to Azure DevOps
[See image.](#attachment-ticket-jira-sync)
When configured in the ticket to the Azure DevOps sync section, the attachment is included in the Azure DevOps issue alongside existing attachments as a downloadable file in the selected format.
Use the **File Format** drop-down menu on the top left of the attachment page to select from the available formats (**CSV**, **PDF**, **JSONL**, **Excel**).
[See image.](#attachment-format)
To provide your Azure DevOps remediation teams with a comprehensive view of the findings in the ticket, consider including the following fields in your attachment:
- Finding Severity
- Finding Title
- Finding CVE
- Component Name
- Asset Name
- Asset Operating System
- Finding Optimal Fix
- Finding Description
- Finding Sources
[]![Field details of the ticket dispatched to Azure DevOps](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-attachment.png)
[]![Sync update details](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-sync.png)
[]![List of file formats to add an attachment](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-attachment-format.png)
[]In the Ticket to Azure DevOps sync step, you can configure how ticket comments are synchronized with Azure DevOps issue comments. To configure comments, click **Comment Sync**.
[See image.](#comment-sync-button)
Sync Comments
Enable **Sync Comments **to automatically push comments from the ticket's Comments tab to the corresponding Azure DevOps issue.
[See image.](#sync-comments-toggle)
Trigger Comments
Enable **Sync Trigger Comments **and set conditions to trigger a comment when specific fields are modified. Syncing trigger comments is useful when you want to be notified of important changes to tickets without updating the corresponding Azure DevOps issue. For example, you can configure a trigger to post a comment in Azure DevOps when the Ticket Severity changes from Medium to Critical.
[See image.](#sync-trigger-comments-toggle)
To add a trigger condition:
- Select the field you want to monitor (e.g., **Severity**).
- Set the value change that should trigger the comment:
- **From**: Select the original value.
- **To**: Select the updated value.
When the specified change occurs in the ticket, a comment is automatically created and added to the Azure DevOps issue. The following is an example of a trigger comment:
`Linked UVM ticket updated:
Ticket severity changed from: MEDIUM to: CRITICAL
<URL to ticket>`
[]![Sync ticket comments to Azure DevOps issue comments](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-sync-comment.png)
[]![Enable ticket comments to push to Azure DevOps issue](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-sync-comment-2.png)
[]![Enable to trigger comments when fields are modified](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-sync-comment-3.png)
[]![Azure DevOps Mapping](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-right-to-left_0.png)
[]The Azure DevOps outegration webhook enables automatic syncing of Azure DevOps issue updates (e.g., Status or SLA changes) to their corresponding tickets, reducing the need for manual changes. This step is required when configuring the Azure DevOps to Ticket mapping to keep issues and tickets in sync. To learn more, see [Configuring the Azure Outegration Webhook.](/uvm/configuring-azure-devops-outegration-webhook)
[See image.](#jira-ticket-step)
An Azure DevOps webhook is only needed to sync updates from Azure DevOps to the ticket. It is not required for the initial ticket dispatch or for syncing updates from the ticket to Azure DevOps.
[]![Sync update details](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops/uvm-webhoook.png)
When the outegration setup is complete, you can begin dispatching SecOps tickets using the Create Azure DevOps Ticket button that appears in the Create Ticket menu within individual tickets, as well as in the Create Issue menu in the Tickets View. To learn more, see [Creating & Managing Third-Party Tickets](/uvm/creating-managing-third-party-tickets).