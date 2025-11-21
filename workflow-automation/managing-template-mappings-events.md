# Managing Template Mappings for Events
Source: https://help.zscaler.com/workflow-automation/managing-template-mappings-events
PDF: https://help.zscaler.com/pdf/com/en/1500281.pdf

Mapping event templates in Workflow Automation is one of the tasks for configuring Workflow Automation. Admins with access to Workflow Automation must configure the template mappings. Event template mappings determine which notification and survey templates Workflow Automation uses when it generates the notifications for the end user notification type.
Prerequisites
Before configuring event template mappings, you must:
- Add notification templates on the [Notification Templates](/workflow-automation/managing-notification-templates-events) page in the Workflow Automation Admin Portal.
- Add survey templates on the [Survey Templates](/workflow-automation/managing-survey-templates-events) page in the Workflow Automation Admin Portal.
Managing Template Mappings
On the Template Mapping page, admins can:
- [View Event Template Mappings](#view-event-digest-template-mappings)
- [Add Event Template Mappings](#add-event-template-mapping)
- [Edit Event Template Mappings](#edit-event-template-mapping)
[]To add an event template mapping:
- Go to **Setup** > **Template Mappings**. The **Template** **Mappings** page appears, listing all the event template mappings.
- On the **Event **tab, click **Add More**. The **Add Template Mapping** window appears.
- In the **Add Template Mapping** window:
- **Event Type**: Select the event type. The event type is **Deprovision**.
- **Notification Type**: Select the notification type.
-
In the **Template Family** section:
- **Email**: Select the email notification template family for the notification type. All email notification template families that have been added on the **Notification Templates** page are available for selection.
- **Survey**: Select the survey template family for the notification type. All survey template families that have been added on the **Survey Templates** page are available for selection.
[See image.](#template-mapping-add-event)
- Click **Add**.
[]To edit an event template mapping:
- Go to **Setup** > **Template Mappings**. The **Template** **Mappings** page appears, listing all the event template mappings that have been mapped on the **Event** tab.
- (Optional) On the **Event** tab, use the **Search** field to locate the template mapping that you want to edit.
-
In the **Action** column next to the template mapping, click the **Edit** icon. The **Edit Template Mapping** window appears.
[See image.](#edit-template-mappings)
-
In the **Edit Template Mapping** window, modify the settings. You can only edit the template values in the **Template** **Family** section.
[See image.](#edit-window-image)
- Click **Update**.
To delete an event template mapping, on the **Template Mappings** page, click the **Delete** icon next to an event template mapping.
[]To view event template mappings, go to **Setup** > **Template Mappings**. The **Template** **Mappings** page appears, listing all the event template mappings.
For event template mappings, you can view:
- **Event Type**: The type of event.
- **Notification Type**: The type of notification for an event.
- **Email Template**: The email notification template family used for the event end user notification.
- **Survey Template**: The survey template family used for the event survey notification.
[See image.](#Template-Mapping-Page-View-All-event)
![Viewing the edit icon on the event Template Mappings page](/downloads/workflow-automation/business-insights/setup/managing-template-mappings-events/WA-BI-Event-Template-Mappings-Edit-Icon.png)
[]
![The Edit Template Mapping window in the Template Mappings page](/downloads/workflow-automation/business-insights/setup/managing-template-mappings-events/WA-BI-Edit-Event-Template-Mapping-Page.png)
[]
[]![The Add Template Mapping window, with drop-down menus for Event Type, Notification Type, Email template family, and Survey template family.](/downloads/workflow-automation/business-insights/setup/managing-template-mappings-events/WA-BI-Add-Event-Template-Mapping-Page.png)
[]![Viewing the template mappings on the Template Mappings page. The template mappings are listed in a table that has columns for Event Type, Notification Type, Email Template, Survey Template, and Action.](/downloads/workflow-automation/business-insights/setup/managing-template-mappings-events/WA-BI-Event-Template-Mappings-Main-Page.png)