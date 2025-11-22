# Managing Notification Templates for Events
Source: https://help.zscaler.com/workflow-automation/managing-notification-templates-events
PDF: https://help.zscaler.com/pdf/com/en/1500261.pdf

Adding notification templates in Workflow Automation is one of the tasks in configuring Workflow Automation. Admins with access to Workflow Automation must add and map the notification templates. Notification templates provide:
- The format for the notifications that Workflow Automation generates and sends when the investigating admins ask the end user to justify actions that led to an event.
- The format for the notifications that are generated and sent from the various workflows defined in Workflow Automation.
To learn more, see [Managing Events](/workflow-automation/managing-events), [Managing Workflows for Events](/workflow-automation/managing-workflows-events), and [Understanding Workflows for Events](/workflow-automation/understanding-workflows-events).
Workflow Automation provides the system default **End-user Justification **email template. You can create only one template in each language. You cannot create two templates of the same language for a single template family.
Admins cannot edit the system default notification templates. They can only view and clone the default notification templates.
On the Notification Templates page, admins can:
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
- **Type**: The type of template. The template type is **Email**.
- **Language**: The language of the template.
- **Last Modified**: The date and time that the template was last modified.
- **Status**: The status of the template. Statuses are **Draft**, **Published**,** **and **System Default**.
[See image.](#notification-templates-page-view-all)
[]![Viewing all templates on the Notification Templates page. The notification templates are listed in a table that has columns for Template Name, Template Family, Type, Language, Last Modified, Status, and Action.](/downloads/workflow-automation/business-insights/setup/managing-notification-templates-events/WA-BI-Notification-Templates-Page-View-Main.png)
[]To add a notification template:
- Go to **Setup** > **Notification Templates**. The **Notification Templates** page appears.
-
Click **Add More**. The **Notification Template** page appears.
[See image.](#add-edit-template-page-adding-template-1)
- On the **Notification Template **page, you can create a custom notification template for the email notification. To learn more, see [Adding Email Notification Templates for Events](/workflow-automation/adding-email-notification-templates-events).
[]![Viewing the Add More button on the Notification Templates page](/downloads/workflow-automation/business-insights/setup/managing-notification-templates-events/WA-BI-Notification-Templates-Page-Add-More-Button.png)
[]To preview a notification template:
- Go to **Setup** > **Notification Templates**. The **Notification Templates **page appears.
-
In the **Action** column next to a template, click the **View** icon. The **Notification Template** page appears, displaying the notification template.
[See image.](#Preview-Template-Page)
-
(Optional) Click **Edit Template**. You are redirected to a page where you can modify and publish the notification template. To learn more, see [Add Notification Templates](#add-email-templates).
[See image.](#edit-template-option-preview-page)
- Click **Close**.
[]![Viewing the View icon in the Action column next to a template on the Notification Templates page](/downloads/workflow-automation/business-insights/setup/managing-notification-templates-events/WA-BI-Notification-Templates-Page-View-Icon.png)
![Edit Template button when viewing a notification template on the Notification Template page](/downloads/workflow-automation/business-insights/setup/managing-notification-templates-events/WA-BI-Notification-Template-PG-Edit-Template-Button.png)
[]
[]To edit a notification template:
- Go to **Setup** > **Notification Templates**. The **Notification Templates** page appears.
-
In the **Action** column next to a published or draft template, click the** Edit** icon. The **Notification Template** page appears, displaying the notification template.
[See image.](#edit-notification-template)
You cannot edit a system default template.
- Edit the template details or the notification template design using the tools or format options provided for the template. To learn more, see [Add Notification Templates](#add-email-templates).
- (Optional) Click **Save as Draft**. The edited template appears on the **Notification Template** page with a draft status. You can come back later and continue to work on the template design.
-
Click **Update Template**. The published template is updated. The template still appears on the Notification Template page with a published status.
[See image.](#update-template-button)
To delete a notification template, click the **Delete** icon in the **Action** column next to the template. You cannot delete a system default template.
[]![Viewing the Edit icon in the Action column next to a template on the Notification Templates page](/downloads/workflow-automation/business-insights/setup/managing-notification-templates-events/WA-BI-Notification-Templates-Page-Edit-Icon.png)
![Update Template button when editing a notification template on the Notification Template page](/downloads/workflow-automation/business-insights/setup/managing-notification-templates-events/WA-BI-Notification-Template-PG-Update-Template-Button.png)
[]
[]To translate a notification template into a different language:
- Go to **Setup** > **Notification Templates**. The **Notification Templates** page appears.
-
In the **Action** column next to a published, system default, or draft template, click the **Translate** icon. The **Notification Template** page appears, with the **Translate **dialog** **window.
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
[]![Viewing Translate icon in the Action column next to a template on the Notification Templates page](/downloads/workflow-automation/business-insights/setup/managing-notification-templates-events/WA-BI-Notification-Templates-Page-Translate-Icon.png)
![Language drop-down menu in the Translate window](/downloads/workflow-automation/business-insights/setup/managing-notification-templates-events/WA-BI-Notification-Templates-Page-Translate-Preview-Button.png)
[]
![Reset button to revert the translation changes on the Notification Template page](/downloads/workflow-automation/business-insights/setup/managing-notification-templates-events/WA-BI-Notification-Template-PG-Reset-Button.png)
[]
[]To clone a notification template:
- Go to **Setup** > **Notification Templates**. The **Notification Templates** page appears.
-
In the **Action** column next to a draft, published, or system default template, click the **Clone** icon. The **Notification Template **page appears. In the **Template Name** field, "Clone of" appears in front of the name of the notification template that you cloned.
[See image.](#clone-template-window)
- (Optional) In the **Template Name** field, change the template name.
- Edit the template details or the notification template design using the tools or format options provided for the template. To learn more, see [Add Notification Templates](#add-email-templates).
-
(Optional) Click **Save as Draft**. The cloned template appears in the **Notification Template** page with a draft status. You can come back later and continue to work on the template design.
[See image.](#Notification-Templates-Page-Cloned-Template)
- (Optional) To translate the newly created template to a different language, click **Translate**. The **Translate **dialog** **window appears.
- In the **Translate** dialog window, from the **Translate To** drop-down menu, select a language to which you want to translate the template.
- Click **Preview** to view the translated template. The template displays in the selected language.
- (Optional) To revert the template to the original language and also to revert any changes made after translation, click **Reset**.
- Click **Publish Template**. The template is published. Workflow Automation only uses published templates for its notifications.
You can only update the [template mappings](/workflow-automation/managing-template-mappings-events) with templates that are in a published status. You also receive notifications from Workflow Automation to update the template mappings to use this template.
[]![Viewing a cloned template on the Notification Template page](/downloads/workflow-automation/business-insights/setup/managing-notification-templates-events/WA-BI-Notification-Template-PG-Clone-Template.png)
[]![Viewing a cloned template with a draft status on the Notification Templates page](/downloads/workflow-automation/business-insights/setup/managing-notification-templates-events/WA-BI-Notification-Templates-Page-Draft-Status.png)