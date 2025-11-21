# Configuring the Jira Outegration
Source: https://help.zscaler.com/uvm/configuring-jira-outegration
PDF: https://help.zscaler.com/pdf/com/en/1527961.pdf

The Jira outegration is used to dispatch tickets from the Zscaler Security Operations (SecOps) platform applications (e.g., UVM) to your Jira project, creating a Jira issue that can then be tracked, assigned, and managed by your remediation teams working with Jira.
This article is a step-by-step guide to setting up the Jira work management outegration. The process involves setting up authentication, outegration visibility in the platform, outegration mapping, and when relevant, configuring a Jira webhook to enable bidirectional synchronization.
Each Jira issue type (e.g., Bug, Task, Feature) requires a separate outegration configuration.
Prerequisites
Before getting started, identify the Jira platform your organization uses: Jira Cloud or Jira Data Center. While the setup process for both Jira outegrations is mostly similar, Jira Data Center users must first set up a gateway and then proceed to follow the standard Jira outegration setup process. To learn more, see [Configuring the Zscaler SecOps Platform Gateway](/uvm/configuring-zscaler-secops-platform-gateway).
Retrieve the required authentication parameters based on your Jira deployment type (i.e., Jira Cloud or Jira Data Center), and enter them in the corresponding fields during the Connect step of the outegration setup wizard.
- [Jira Cloud](#jira-cloud-authentication)
- [Jira Data Center](#jira-data-center-authentication)
Creating the Jira Outegration
To configure the Jira outegration, complete the following steps:
- [Step 1: Authenticate the Jira Connection (Connect)](#step1-jira-authentication)
- [Step 2: Configure the Outegration Visibility and Behavior (Settings)](#step2-jira-settings)
- [Step 3: Map the Outegration Fields (Mapping)](#step3-jira-mapping)
- [Step 4: Configure the Jira Webhook](#step4-jira-webhook)
[]Obtain the following required parameters for the Jira Cloud outegration:
- [Jira Organization Domain](#cloud-jira-org-domain)
- [Project Key](#cloud-project-key)
- Choose one of the following authentication methods and retrieve the necessary parameters:
- [Email Password Domain](#cloud-email-pw-domain)
- [API Key Domain](#cloud-api-key-domain)
[]The Jira organization domain is the unique domain that identifies your organization's Jira instance, in the format `<Domain Name>``.atlassian.net`. For example, if your Jira Cloud URL is `https://``acme``.atlassian.net`, then your Jira organization domain is `acme.atlassian.net`.
[See image.](#example-jira-cloud-org-domain)
[]Your Jira project key is the shortened version of the Jira project name that you want the platform to dispatch tickets to.
Your project key can be found in the following locations:
- All Projects list:** **The Key column displays the project key for each of your projects.
- Jira Issue ID Prefix:** **The project key is often used as a prefix for issue IDs (e.g., `PROJ-123`).
- Project URL:** **The project key is included in the URL of your project, after `/projects/`. For example, the project key in the URL `https://acme.atlassian.net/projects/PROJ/summary` is `PROJ`.
[]For the Email Password Domain authentication method, you’ll need to provide the email and password (API Token) associated with a Jira user account. This account is used to authenticate with Jira and will be displayed as the issue reporter in Jira by default, unless an alternative reporter is specified in the Jira mapping.
[]For the API Key Domain authentication method, you’ll need to provide the Jira API key that was generated using a Jira user account. To learn more, refer to the [Jira Atlassian documentation](https://support.atlassian.com/statuspage/docs/create-and-manage-api-keys/).
To generate an API key:
- Log in to your Jira instance using an admin account.
- Click your avatar in the bottom left of the management interface.
- Click** API info**.
- Click **Create key**.
- Enter a key name that clearly indicates its association with the SecOps platform application (e.g., UVM, AEM).
- Click** Confirm**.
- Copy and securely save the key to be used in the Connect step.
[]![751a05b0-7856-45e2-bf03-97349193e7f7.png](/downloads/uvm/configure/outegrations/jira-outegration/751a05b0-7856-45e2-bf03-97349193e7f7.png)
[]Before proceeding, make sure a Zscaler Gateway has been configured. To learn more, see [Configuring the Zscaler SecOps Platform Gateway](/uvm/configuring-zscaler-secops-platform-gateway).
Obtain the following required parameters for the Jira Data Center outegration:
- [Jira Organization Domain](#jira-dc-org-domain)
- [Project Key](#dc-project-key)
- Choose one of the following authentication methods and retrieve the necessary parameters:
- [Email Password Domain](#dc-email-pw-domain)
- [API Key Domain](#dc-api-key-domain)
- [Gateway](#dc-gateway)
[]The Jira organization domain is the unique domain that identifies your organization's Jira instance, typically the domain name or host name of your Jira server. For example, if your Jira Data Center URL is `https://jira.acme.com`, your Jira organization domain is `jira.acme.com`.
[See image.](#example-jira-dc-org-domain)
The domain for Jira Data Center can vary depending on how your Jira instance is configured and hosted.
[]Your Jira project key is the shortened version of the Jira project name that you want the platform to dispatch tickets to.
Your project key can be found in the following locations:
- All Projects list:** **The Key column displays the project key for each of your projects.
- Jira Issue ID Prefix:** **The project key is often used as a prefix for issue IDs (e.g., `PROJ-123`).
- Project URL:** **The project key is included in the URL of your project, after `/projects/`. For example, the project key in the URL `https://acme.atlassian.net/projects/PROJ/summary` is `PROJ`.
[]For the Email Password Domain authentication method, you’ll need to provide the email and password (API Token) associated with the Jira admin account. This account is used to authenticate with Jira and will be displayed as the issue reporter in Jira by default, unless an alternative reporter is specified in the Jira mapping.
[]For the API Key Domain authentication method, you’ll need to provide the Jira API key that was generated using a Jira admin account. To learn more, refer to the [Jira Atlassian documentation](https://support.atlassian.com/statuspage/docs/create-and-manage-api-keys/).
To generate an API key:
- Log in to your Jira account as an admin.
- Click your avatar in the bottom left of the management interface.
- Click** API info**.
- Click **Create key**.
- Enter a key name that clearly indicates its association with the SecOps platform application (e.g., UVM, AEM).
- Click** Confirm**.
- Copy and securely save the key to be used in the Connect step.
[]Jira Data Center users must first set up a gateway and then proceed to follow the standard Jira outegration setup process. To learn more, see [Configuring the Zscaler Gateway](/uvm/configuring-zscaler-gateway).
If you already have a gateway configured, select the gateway from the drop-down menu.
[]![cf066fa4-ceab-465c-b6fb-b6c258fa7524.png](/downloads/uvm/configure/outegrations/jira-outegration/cf066fa4-ceab-465c-b6fb-b6c258fa7524.png)
[]The first step in setting up your Jira outegration is to authenticate using valid credentials to establish a secure connection with your Jira project. With the required parameters retrieved in the prerequisites, you can begin the Jira outegration setup in the SecOps platform.
To create an outegration:
-
In the SecOps platform, go to **Configure** > **Outegrations**.
[See image.](#configure-outegrations)
-
Click **Create**, then select either **Jira Cloud** or **Jira Data Center**, depending on your organization's Jira deployment.
The **Connect** step appears.
[See image.](#jira-outegration-connect)
- In the **Details** section:
- **Display Name**: Enter a name for your outegration.
- **Active**: Enable to activate the Jira outegration.
- **Project Key**: Enter the key of the Jira project where the tickets should be created.
- **Authentication**: Select an existing authentication, or click **Create New** to set up a new authentication and enter the required parameters you retrieved earlier into the corresponding fields. To learn more, see [Configuring Authentications](/uvm/configuring-authentications).
- Click **Test** in the bottom-right corner of the page to verify the connection. Invalid credentials trigger error messages to assist with troubleshooting connectivity issues.
- After the test passes, click **Next **to advance to the **Settings **step.
[]![cbd83f72-e7af-4497-a7f1-c1f8e0c9ac18.png](/downloads/uvm/configure/outegrations/jira-outegration/cbd83f72-e7af-4497-a7f1-c1f8e0c9ac18.png)
[]![create jira cloud outegration page connect step](/downloads/uvm/configure/outegrations/configuring-jira-outegration/jira%20cloud%20outegration%20connect.png)
[]In the Settings step of the outegration setup wizard, configure your Jira outegration's visibility and behavior within the relevant application in the SecOps platform (e.g., UVM, AEM). In this step, you'll set the SecOps entity that triggers the Jira issue dispatch (e.g., ticket, violation ticket), the Jira Issue Type that the SecOps ticket should be dispatched to, and when the Create Jira Ticket button should appear in the application. The Create Jira Ticket button allows end users with access to SecOps tickets to dispatch these tickets to a Jira project directly from the SecOps ticket drawer or from the SecOps tickets page.
To configure the outegration's visibility and behavior:
- In the **Advanced Settings** section:
-
**Create Jira item from**:** **Select the entity that you want to configure the outegration for. This selection affects the view you'll configure in the <Entity> **View **step (e.g., selecting Ticket displays the Tickets View setting).
- **UVM**: Select **Ticket**.
- **AEM**: Select **Violation Ticket**.
Other entity types might be visible depending on the apps enabled in your account.
[See image.](#create-jira-data-center-item-field)
-
**Issue Type**:** **Select the Jira issue type that the ticket should be dispatched to (e.g., **Task**, **Bug**). The schema associated with the selected issue type will be retrieved from your Jira project and made available for mapping in the Mapping step.
[See image.](#issue-type-field)
-
In the <Entity> **View** section, select how the SecOps ticket should display the **Create Jira Ticket** button. This setting can be modified at any time.
- **Always**: Select to display the button in all tickets, allowing users to dispatch tickets to a Jira issue without exception.
- **Never**: Select to hide the button in all tickets. This is useful during the outegration* *setup process to hide the button from users while still keeping the outegration active.
- **For specific tickets**: Define custom conditions to control when the button is displayed, allowing you to target specific tickets. For example, if your organization uses multiple ticketing systems, you can grant access to the button only to users who work with Jira, while excluding those who use other ticketing systems (e.g., ServiceNow).
[See image.](#tickets-view-setting)
- Click **Map **to advance to the **Mapping** step.
The **Create Jira Ticket **button appears in two locations:
-
In the individual entity drawer (e.g., in the [UVM ticket drawer](/uvm/managing-tickets-uvm), in the [AEM violation ticket drawer](/uvm/managing-violation-tickets-aem)).
[See image.](#button-in-ticket)
-
On the entity page in the relevant application (e.g., on the [Tickets page](/uvm/about-tickets-operational-view-uvm) in UVM, on the [Violation Tickets page](/uvm/about-violation-tickets-operational-view-aem) in AEM).
[See image.](#button-in-tickets-view)
[]![7b4e5c72-9ca9-42e7-9577-8ae9907b7a05.png](/downloads/uvm/configure/outegrations/jira-outegration/7b4e5c72-9ca9-42e7-9577-8ae9907b7a05.png)
[]![0dfab25c-a67d-4166-bc52-fdb49204a08c.png](/downloads/uvm/configure/outegrations/jira-outegration/0dfab25c-a67d-4166-bc52-fdb49204a08c.png)
[]![60122c5d-0dfb-423e-92f6-fde718ae5cb4.png](/downloads/uvm/configure/outegrations/jira-outegration/60122c5d-0dfb-423e-92f6-fde718ae5cb4.png)
[]![794c89f3-f9a0-406f-a197-5763abe734ae.png](/downloads/uvm/configure/outegrations/jira-outegration/794c89f3-f9a0-406f-a197-5763abe734ae.png)
[]![af9c2053-b0de-43a8-9805-72ea5ced614c.png](/downloads/uvm/configure/outegrations/jira-outegration/af9c2053-b0de-43a8-9805-72ea5ced614c.png)
[]The third step in setting up your Jira outegration is configuring the field mapping between your SecOps tickets and Jira issues. This defines how data is exchanged and synchronized between the two systems upon initial dispatch and subsequent updates. The SecOps platform's unique mapping capabilities allow for flexible mapping of any custom field or logic to any field in your Jira projects, facilitating highly customized workflows that align with your organization's requirements.
The main objective of the mapping process is to map values to fields. To map values to fields, configure values on the left to populate the fields selected on the right.
[See image.](#jira-outegration-mapping-right-left)
There are three mapping components:
- Tickets initially dispatched to Jira: Map SecOps ticket fields (left) to Jira fields (right) for the initial dispatch of a ticket to a Jira issue. You can also add an attachment to your Jira issue. Commonly mapped fields include Summary, Description, Assignee, Priority, Due Date, and Status.
- (Optional) Sync from ticket to Jira: Map SecOps ticket fields (left) to Jira fields (right) for syncing ticket updates to Jira, including configuring comments and adding an attachment to your Jira issue. Commonly mapped fields include Status and Due Date.
- (Optional) Sync from Jira to ticket: Map Jira fields (left) to SecOps ticket fields (right) for syncing Jira updates to tickets. This step also requires setting up a Jira webhook. Commonly mapped fields include Ticket Status and Ticket SLA.
The initial Jira outegration mapping includes preconfigured default mappings for each part, based on common use cases and industry best practices. These defaults can be modified and customized as needed.
Creating a New Mapping
In each of the three mapping components, you’ll need to select a field on the right, and then configure the corresponding field value on the left.
To create a new mapping:
- Select a field (right):
- Click** Mapping**.
-
Select a field on the right.
The field's schema details open on the right of the page. The schema lists available Jira fields to be used during mapping. This is the list of fields configured in your Jira project for the Issue Type selected in the [Settings](#step2-jira-settings) step (e.g., Bug).
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
Repeat** **the mapping process for all required Jira fields and for any other fields you want to map.
In addition to the mapping of fields on the right to fields on the left, you can perform a set of actions when setting up the Jira outegration mapping, each relevant to a specific part of the mapping.
- [Set a ticket field as mandatory.](#set-as-mandatory)
- [Add attachments to the ticket dispatch.](#attachments)
- [Configure comments synchronization.](#comments)
Mapping Ticket Title to Summary
To illustrate the mapping process, consider the mapping of the required Jira Summary field. The final result of the mapping process should show the Summary field on the right, and the Ticket Title field on the left.
![75f223d1-3181-4d51-b496-339c74a3fa46.png](/downloads/uvm/configure/outegrations/jira-outegration/75f223d1-3181-4d51-b496-339c74a3fa46.png)
To map the Ticket Title field to the Summary field:
-
Select **Summary **as the Jira field on the right.
[See image.](#example-jira-summary-right)
Selecting the Jira Summary field opens the field's details in the schema. The schema specifies that the field is required and thus must be mapped before the outegration can be saved, and that the field expects a TEXT input type. Therefore, the field for which a value is being configured must also be of TEXT type.
[See image.](#example-summary-schema)
-
Select the **Ticket Title **field on the left:
- Click** Add Value**.
- Under the **Field** tab, select the **Ticket Title** field, which is the equivalent to the Jira **Summary **field.
[See image.](#example-ticket-title-field)
Previewing the Ticket to Jira Mapping
After completing the SecOps ticket to Jira dispatch mapping, preview the mapping to review the configuration. This helps ensure that SecOps ticket dispatch is behaving as expected and that the Jira issue fields are populated correctly.
To preview the mapping, click **Preview **on the bottom right of the ticket initially dispatched to Jira section. The Mapping Preview window appears. On the left of the Mapping Preview window, there is a sample of the SecOps tickets in your account, organized by ticket ID. You can select, filter, or search tickets and preview the mapping to their corresponding Jira issue. You can also open the actual SecOps ticket in a new tab for a more in-depth review.
[See image.](#preview)
Common Mapping Examples
These mapping examples highlight commonly used field configurations in your outegration. While some might be preconfigured by default, Zscaler recommends reviewing and customizing them to ensure they align with your workflow.
- [Ticket to Jira Description](#mapping-ticket-jira-description)
- [Ticket SLA to Jira Due Date Sync](#mapping-jira-due-date-ticket-sla)
- [Jira to Ticket Status Sync](#mapping-jira-status-ticket-status)
[]![1b61b2af-6437-4d24-ad59-e8429252c3c1.png](/downloads/uvm/configure/outegrations/jira-outegration/1b61b2af-6437-4d24-ad59-e8429252c3c1.png)
[]The Required attribute is TRUE if a field is required by Jira. If a field is not required, the attribute is not displayed. A required Jira field is also indicated by a red asterisk (*) on the Jira field in the first mapping step.
Required Jira fields must be mapped before saving the outegration.
[]The Input Type specifies the data type of the Jira field, such as TEXT (e.g., Summary), DATE (e.g., Due Date), or NUMBER (e.g., Risk Score). This indicates the format that the selected source field must match in order to successfully map to the Jira field.
[]For Jira fields with fixed values, the Available Options column displays the available values. For example, if the Jira field Priority is configured to include the following fixed values—High, Low, Medium, Lowest, Highest—the corresponding values in the Ticket Severity field can be mapped to these values.
[]![mceclip1.png](/downloads/uvm/configure/outegrations/jira-outegration/mceclip1.png)
[]![bb42ebaf-93e6-4b90-be96-6c5a9064f9bf.png](/downloads/uvm/configure/outegrations/jira-outegration/bb42ebaf-93e6-4b90-be96-6c5a9064f9bf.png)
[]Select a field on the left to populate the field on the right.
Dictionary
The field dictionary allows you to create mappings between specific values from the field on the right and values of the field on the left. To use the dictionary, you must first select a field on the right and a field to populate it with on the left.
For example, if your Jira** **Priority field includes the following fixed values—Highest, High, Medium, Low, Lowest—you can use the dictionary to map the corresponding Ticket Severity values to each of the Priority field values.
[See image.](#example-dictionary)
[]![a01c0fe8-5f42-4b60-8ea9-8c71572c7c8e.png](/downloads/uvm/configure/outegrations/jira-outegration/a01c0fe8-5f42-4b60-8ea9-8c71572c7c8e.png)
[]Configure the field value using free text, or create a template using a combination of free text and selected fields. This allows you to dynamically insert specific field values (e.g., Ticket SLA, Ticket Assignee, or Asset Name) into customized free text sentences or paragraphs.
To add a Smart Text field, enclose it in double curly brackets (e.g., `{{Ticket Assignee}}`). The field's display name automatically translates to its system name.
This option is commonly used to configure the value of fields like Ticket Title and Ticket Description.
[See image.](#example-smart-text)
[]![908f493f-957e-4794-9cd7-62cc4f83b0ff.png](/downloads/uvm/configure/outegrations/jira-outegration/908f493f-957e-4794-9cd7-62cc4f83b0ff.png)
[]For use cases that require more advanced configuration than either of the two methods above, you can use Python scripts to configure the field value to be mapped to the target field.
[]![1d97790b-72cd-4453-86f3-2d4b03770792.png](/downloads/uvm/configure/outegrations/jira-outegration/1d97790b-72cd-4453-86f3-2d4b03770792.png)
[]When dispatching tickets to Jira, map the Jira Description field with a summary of the Ticket content to provide remediation teams with a brief overview of the ticket.
To configure the Ticket to Jira Description mapping:
- Click** Mapping**.
- Select** Description** as the field on the** **right.
-
Click **Add Value** on the left.
The **Field Editor** appears.
- In the **Field Editor**, select **Smart Text**.
- Enter a ticket description, including dynamic fields (e.g., `{{SLA}}`).
Tickets dispatched to Jira will now include the configured description.
[]In the Ticket to Jira sync, map the Jira Due Date field to keep timelines in sync with Ticket SLA changes.
To configure the Ticket SLA to Jira Due Date mapping:
- Click** Mapping**.
- Select** Due Date** as the field on the right.
-
Click** Add Value** on the left.
The **Field Editor** appears.
- In the **Field Editor**, select **Field**, and select **Ticket SLA** as the field on the left.
Ticket SLA changes will now automatically update Jira issue due dates.
[]In the Jira to Ticket sync, map the Ticket Status field to ensure it's updated when remediation teams change the Jira Issue Status.
To configure the Jira to Ticket Status mapping:
- Click** Mapping**.
- Select** Ticket Status** as the field on the right.
-
Click** Add Value** on the left.
The **Field Editor** appears.
- In the **Field Editor**, select **Field**, and select **Status** as the field on the left. Use the **Dictionary** to map your Jira** Status** types to **Ticket Status** types.
Jira issue Status changes will now automatically update the Ticket Status.
[]![mceclip0.png](/downloads/uvm/configure/outegrations/jira-outegration/mceclip0.png)
[]You can set a SecOps ticket field as mandatory, by selecting the Set as Mandatory** **checkbox in the Column Menu to the right of the mapping. Some fields can be set as mandatory by default.
[See image.](#set-as-mandatory-checkbox)
Setting a field as mandatory guarantees that critical fields (e.g., Ticket Assignee) are always populated before a ticket is dispatched to Jira, so Jira issues are always actionable for your remediation teams. Attempts to dispatch a ticket without a value in a mandatory field will trigger an error message.
Required fields are defined by your Jira schema, whereas Mandatory fields are mandatory for SecOps ticket dispatch.
[]![83d803fe-06d1-4895-bb53-bf66703b351f.png](/downloads/uvm/configure/outegrations/jira-outegration/83d803fe-06d1-4895-bb53-bf66703b351f.png)
[]You can create a file attachment that summarizes your ticket content and set the trigger to automatically add it to your Jira issue. Adding an attachment to your Jira issue simplifies the review and management of findings dispatched from a ticket.
You can configure file attachments in two of the mapping steps:
-
Initial ticket dispatch
[See image.](#attachment-intial-dispatch)
-
Sync from Ticket to Jira
[See image.](#attachment-ticket-jira-sync)
When configured in the Ticket to Jira sync section, the attachment is included in the Jira issue alongside existing attachments as a downloadable file in the selected format.
Use the **File Format** drop-down menu on the top left of the attachment page to select from the available formats (**CSV**, **PDF**, **JSONL**, **Excel**).
[See image.](#attachment-format)
To provide your Jira remediation teams with a comprehensive view of the findings in the ticket, consider including the following fields in your attachment:
- [Recommended Attachment Fields](#recommended-attachment-fields)
[]![ef712f7f-ea12-4b05-9a4c-6370ebc22bed.png](/downloads/uvm/configure/outegrations/jira-outegration/ef712f7f-ea12-4b05-9a4c-6370ebc22bed.png)
[]![fdcef0ba-d9b2-44b5-90d6-6415d58f3370.png](/downloads/uvm/configure/outegrations/jira-outegration/fdcef0ba-d9b2-44b5-90d6-6415d58f3370.png)
[]![596433f4-e75d-482c-a9b4-d52bd3937a27.png](/downloads/uvm/configure/outegrations/jira-outegration/596433f4-e75d-482c-a9b4-d52bd3937a27.png)
- []Finding Severity
- Finding Title
- Finding CVE
- Component Name
- Asset Name
- Asset Operating System
- Finding Optimal Fix
- Finding Description
- Finding Sources
[]In the Ticket to Jira sync step, you can configure how ticket comments are synchronized with Jira issue comments. To configure comments, click **Comment Sync**.
[See image.](#comment-sync-button)
Sync Comments
Enable **Sync Comments **to automatically push comments from the ticket's Comments tab to the corresponding Jira issue.
[See image.](#sync-comments-toggle)
Trigger Comments
Enable **Sync Trigger Comments **and set conditions to trigger a comment when specific fields are modified. Syncing trigger comments is useful when you want to be notified of important changes to tickets without updating the corresponding Jira issue. For example, you can configure a trigger to post a comment in Jira when the Ticket Severity changes from Medium to Critical.
[See image.](#sync-trigger-comments-toggle)
To add a trigger condition:
- Select the field you want to monitor (e.g., **Severity**).
- Set the value change that should trigger the comment:
- **From**: Select the original value.
- **To**: Select the updated value.
When the specified change occurs in the ticket, a comment is automatically created and added to the Jira issue. The following is an example of a trigger comment:
`Linked UVM ticket updated:
Ticket severity changed from: MEDIUM to: CRITICAL
<URL to ticket>`
[]![fd038411-d12b-4dc0-95b8-4e800faa3938.png](/downloads/uvm/configure/outegrations/jira-outegration/fd038411-d12b-4dc0-95b8-4e800faa3938.png)
[]![fe3b243c-fae6-41ff-9f0a-cbead663f4dd.png](/downloads/uvm/configure/outegrations/jira-outegration/fe3b243c-fae6-41ff-9f0a-cbead663f4dd.png)
[]![e7859188-4e91-4cbe-b9d3-9446737d49c3.png](/downloads/uvm/configure/outegrations/jira-outegration/e7859188-4e91-4cbe-b9d3-9446737d49c3.png)
[]![jira outegration mapping](/downloads/uvm/configure/outegrations/configuring-jira-outegration/jira%20outegration%20mapping.png)
[]The Jira outegration webhook enables automatic syncing of Jira issue updates (e.g., Status or SLA changes) to their corresponding SecOps tickets, reducing the need for manual changes. This step is required when configuring the Jira to Ticket mapping to keep issues and tickets in sync. To learn more, see [Configuring the Jira Outegration Webhook](/uvm/configuring-jira-outegration-webhook).
[See image.](#jira-ticket-step)
A Jira webhook is only needed to sync updates from Jira to the ticket. It is not required for the initial ticket dispatch or for syncing updates from the ticket to Jira.
[]![f389aee3-d4a0-4fbe-a72c-fbfc5cd55703.png](/downloads/uvm/configure/outegrations/jira-outegration-webhook/f389aee3-d4a0-4fbe-a72c-fbfc5cd55703.png)
When the outegration setup is complete, you can begin dispatching SecOps tickets using the Create Jira Ticket button that appears in the Create Ticket menu within individual tickets, as well as in the Create Issue menu in the Tickets View. To learn more, see [Creating & Managing Third-Party Tickets](/uvm/creating-managing-third-party-tickets).