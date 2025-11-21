# Managing Notification Templates
Source: https://help.zscaler.com/workflow-automation/managing-notification-templates
PDF: https://help.zscaler.com/pdf/com/en/1419961.pdf

Adding notification templates in Workflow Automation is one of the tasks in configuring Workflow Automation. Admins with access to Workflow Automation must add and map the notification templates. Notification templates provide:
- The format for the notifications that Workflow Automation generates and sends when admins are investigating an incident. Notifications are sent when the admin asks the end user to justify actions that led to an incident and when the admin escalates the incident to an approver from the Incidents page or the Incident Details page.
- The format for the digest notifications that Workflow Automation sends to the users and the Data Loss Prevention (DLP) admins.
- The format for the notifications that are generated and sent from the various workflows defined in Workflow Automation.
To learn more, see [Managing Incident and Digest Template Mappings](/zia/managing-incident-and-digest-template-mappings), [About Incidents](/zia/about-incidents), [Viewing & Managing Incident Details](/zia/viewing-managing-incident-details), [Managing Workflow Templates](/zia/managing-workflow-templates), [Managing Workflows](/zia/managing-workflows), and [Managing Workflow Mappings](/zia/managing-workflow-mappings).
Workflow Automation provides the following system default notification template families and templates:
-
Email Families and Templates
| Notification Template Family | Notification Template |
| ---------------------------- | --------------------- |
| End-user Justification - Email Template | End-user Justification - Email Template |
| Escalation - Email Template | Escalation - Email Template |
| Digest - Email Template | Digest - Email Template |
| DLP Admin Digest - Email Template | DLP Admin Digest - Email Template |
-
Slack Families and Templates
These families and templates are only available if you have integrated Workflow Automation with Slack.
| Notification Template Family | Notification Template |
| ---------------------------- | --------------------- |
| End-user Justification - Slack Template | End-user Justification - Slack Template |
| Escalation - Slack Template | Escalation - Slack Template |
| Digest - Slack Template | Digest - Slack Template |
| DLP Admin Digest - Slack Template | DLP Admin Digest - Slack Template |
-
Microsoft Teams Families and Templates
These families and templates are only available if you have integrated Workflow Automation with Microsoft Teams.
| Notification Template Family | Notification Template |
| ---------------------------- | --------------------- |
| End-user Justification - Teams Template | End-user Justification - Teams Template |
| Escalation - Teams Template | Escalation - Teams Template |
| Digest - Teams Template | Digest - Teams Template |
| DLP Admin Digest - Teams Template | DLP Admin Digest - Teams Template |
For each template family, you can create only one template in each language. You cannot create two templates of the same language for a single template family.
Admins cannot edit the system default notification templates. They can only view and clone the default notification templates.
On the Notification Templates page in the Workflow Automation Admin Portal, admins can:
- [View Notification Templates](#view-email-templates)
- [Add Notification Templates](#add-email-templates)
- [Preview Notification Templates](#Preview-email-templates)
- [Edit Notification Templates](#edit-email-templates)
- [Translate Notification Templates](#translate-template)
- [Clone Notification Templates](#clone-notification-template)
[]To view notification templates:
- Go to **Setup** > **Notification Templates**. The **Notification Templates **page appears.
- (Optional) Filter the templates by status, type, template family, or language. You can also search for specific templates that you want to view.
- (Optional) Reset all the applied filters.
-
View a list of notification templates configured for your organization. For each notification template, you can see:
- **Template Name**: The name of the template.
- **Template Family**: The family of the template.
- **Type**: The type of template. Template types are **Email**, **Slack**,** **and** Teams**. The Slack and Microsoft Teams templates are only available if you have integrated Workflow Automation with Slack and Microsoft Teams, respectively.
- **Language**: The language of the template.
- **Last Modified**: The date and time the template was last modified.
- **Status**: The status of the template. Statuses are **Draft**, **Published**,** **and **System Default**.
[See image.](#notification-templates-page-view-all)
[]![Notification Templates Page - View All Notification Templates](/downloads/workflow-automation/setup/managing-notification-templates/WA-Notification-Templates-PG-View-All_0.png)
[]To add a notification template:
- Go to **Setup** > **Notification Templates**. The **Notification Templates** page appears.
-
Click **Add More**. The **Notification Template** page appears.
[See image.](#add-edit-template-page-adding-template-1)
- On the **Notification Template **page, you can create a custom notification template for the following types of notifications:
- [Adding an Email Notification Template](/workflow-automation/adding-email-notification-templates)
- [Adding a Slack Notification Template](/workflow-automation/adding-slack-notification-templates)
- [Adding a Microsoft Teams Notification Template](/workflow-automation/adding-microsoft-teams-notification-templates)
[]![Notification Templates Page - Add More Button](/downloads/workflow-automation/setup/managing-notification-templates/WA-Notification-Templates-PG-Add-New-Template.png)
[]To preview a notification template:
- Go to **Setup** > **Notification Templates**. The **Notification Templates **page appears.
-
In the **Action** column next to a template, click the **View Template** icon. The **Notification Template** page appears, displaying the notification template. The following images show examples of an email notification template, a Slack notification template, and a Microsoft Teams notification template.
[See image.](#Preview-Template-Page)
-
(Optional) Click **Edit Template**. You are redirected to a page where you can modify and publish the notification template. To learn more, see [Add Notification Templates](#add-email-templates).
[See image.](#edit-template-option-preview-page)
- Click **Close**.
[]![Notification Template Page - Previewing Email Notification Template ](/downloads/workflow-automation/setup/managing-notification-templates/WA-Notification-Template-PG-Preview-Notification-Template.png)
![Notification Template Page - Preview Slack Notification Template](/downloads/workflow-automation/setup/managing-notification-templates/WA-Preview-Notification-Template-Slack_0.png)
![Notification Template Page - Preview Teams Notification Template](/downloads/workflow-automation/setup/managing-notification-templates/WA-Preview-Notification-Template-Teams_0.png)
![Preview Notification Template Page - Edit Template](/downloads/workflow-automation/setup/managing-notification-templates/WA-Notification-Templates-Preview-Page-Edit.png)
[]
[]You can only edit draft and published notification templates. You cannot edit or delete system default notification templates.
- [Editing a Draft Notification Template](#edit-draft-notification)
- [Editing a Published Notification Template](#edit-published-notification)
[]To edit a draft notification template:
- Go to **Setup** > **Notification Templates**. The **Notification Templates** page appears.
-
In the **Action** column next to a draft template, click the** Edit Template** icon. The **Notification Template** page appears, displaying the notification template.
[See image.](#edit-notification-template)
- Edit the template details or the notification template design using the tools or format options provided for the template. To learn more, see [Add Notification Templates](#add-email-templates).
- (Optional) Click **Save as Draft**. The edited template appears on the **Notification Templates** page with a draft status. You can come back later and continue to work on the template design.
- Click **Publish Template**. The template is published. Workflow Automation only uses published templates for its notifications.
To delete a draft notification template, click the **Delete Template** icon in the **Action** column next to the template.
[]![Notification Template Page - Editing a Draft Notification Template](/downloads/workflow-automation/setup/managing-notification-templates/WA-Notification-Template-PG-Edit-Draft-Notification-Template.png)
[]To edit a published notification template:
- Go to **Setup** > **Notification Templates**. The **Notification Templates** page appears.
-
In the **Action** column next to a published template, click the** Edit Template** icon. The **Notification Template** page appears, displaying the notification template.
[See image.](#edit-published-notification-page)
- Edit the template details or the notification template design using the tools or format options provided for the template. To learn more, see [Add Notification Templates](#add-email-templates).
- Click **Update Template**. The published template is updated. The template still appears on the **Notification Templates** page with a published status.
To delete a published notification template, click the **Delete Template** icon in the **Action** column next to the template.
[]![Notification Template Page - Editing a Published Notification Template](/downloads/workflow-automation/setup/managing-notification-templates/WA-Notification-Template-PG-Edit-Published-Not-Template.png)
[]To translate a notification template into a different language:
- Go to **Setup** > **Notification Templates**. The **Notification Templates** page appears.
-
In the **Action** column next to a template, click the **Translate Template** icon. The **Notification Template** page appears, with the **Translate **dialog** **window.
[See image.](#translate-template-icon-image)
- In the **Translate** dialog window, from the **Translate To** drop-down menu, select a language to which you want to translate the template.
-
To view the translated template, click **Preview**. The template displays in the selected language.
[See image.](#translate-window-image)
-
(Optional) To revert the template to the original language and also to revert any changes made after translation, click **Reset**.
[See image.](#reset-option-translate-image)
- (Optional) Click **Save as Draft**. You can come back later and continue to work on the template.
- Click **Publish Template**. The template is published. Workflow Automation only uses published templates for its notifications.
[]![Notification Templates Page - Translate Icons](/downloads/workflow-automation/setup/managing-notification-templates/WA-Notification-Templates-Page-Translate-Icons_0.png)
![Translate Dialog Window](/downloads/workflow-automation/setup/managing-notification-templates/WA-Notification-Templates-Page-Translate-1.png)
[]
![Notification Template Page - Revert Translations](/downloads/workflow-automation/setup/managing-notification-templates/WA-Notification-Templates-Page-Translate-2.png)
[]
[]To clone a notification template:
- Go to **Setup** > **Notification Templates**. The **Notification Templates** page appears.
-
In the **Action** column next to a template, click the **Clone Template** icon. The **Notification Template **page appears. In the **Template Name** field, "Clone of" appears in front of the name of the notification template that you cloned.
[See image.](#clone-template-window)
- (Optional) In the **Template Name** field, change the template name.
- Edit the template details or the notification template design using the tools or format options provided for the template. To learn more, see [Add Notification Templates](#add-email-templates).
-
(Optional) Click **Save as Draft**. The cloned template appears on the **Notification Templates** page with a draft status. You can come back later and continue to work on the template design.
[See image.](#Notification-Templates-Page-Cloned-Template)
- (Optional) Click **Translate** to translate the newly created template to a different language. The **Translate **dialog** **window appears.
- In the **Translate** dialog window, from the **Translate To** drop-down menu, select a language to which you want to translate the template.
- Click **Preview** to view the translated template. The template displays in the selected language.
- (Optional) To revert the template to the original language and also to revert any changes made after translation, click **Reset**.
- Click **Publish Template**. The template is published. Workflow Automation only uses published templates for its notifications.
You can only update the [template mappings](workflow-automation/managing-incident-and-digest-template-mappings) with templates that are in a published status. You also receive notifications from Workflow Automation to update the template mappings to use this template.
[]![Notification Template Page - Cloning a Template](/downloads/workflow-automation/setup/managing-notification-templates/WA-Notification-Template-Page-Clone-Template.png)
[]![Notification Templates Page - Cloned Notification Template](/downloads/workflow-automation/setup/managing-notification-templates/WA-Notification-Template-Page-Clone-Template-2.png)