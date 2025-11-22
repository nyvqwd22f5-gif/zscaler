# Managing Incident and Digest Template Mappings
Source: https://help.zscaler.com/workflow-automation/managing-incident-and-digest-template-mappings
PDF: https://help.zscaler.com/pdf/com/en/1418216.pdf

Mapping incident and digest templates in Workflow Automation is one of the tasks for configuring Workflow Automation. Admins with access to Workflow Automation must configure the template mappings. Incident template mappings determine which notification and survey templates Workflow Automation uses when it generates the notifications for the different notification types (end user notification and escalation). The digest template mapping determines which templates Workflow Automation uses when it generates the digest notifications for your organization.
Workflow Automation provides a default source action for each source Data Loss Prevention (DLP) type (Inline, Email, Endpoint, and SaaS Security). These default actions are mapped to the default notification and survey templates that Workflow Automation provides. You can change the notification and survey templates associated with these default mappings, and you can delete them. If you want to add additional incident template mappings associated with the different source DLP type incidents and notification types, additional source actions are available.
On the Template Mappings page in the Workflow Automation Admin Portal, admins can:
- [Add Incident Template Mappings](#add-incident-template-mapping)
- [Edit Incident Template Mappings](#edit-incident-template-mapping)
- [Add Digest Template Mappings](#add-digest-template-mapping)
- [Edit Digest Template Mappings](#edit-digest-template-mapping)
- [View Incident and Digest Template Mappings](#view-incident-digest-template-mappings)
[]Before adding incident template mappings, you must:
- Add notification templates on the Notification Templates page of the Workflow Automation Admin Portal. To learn more, see [Managing Notification Templates](/zia/managing-notification-templates).
- Add survey templates on the Survey Templates page of the Workflow Automation Admin Portal. To learn more, see [Managing Survey Templates](/zia/managing-survey-templates).
To add an incident template mapping:
- Go to **Setup** > **Template Mappings**. The **Template** **Mappings** page appears, listing all the incident template mappings that have been mapped on the **Incident** tab.
- On the **Incident **tab, click **Add More**. The **Add Template Mapping** window appears.
- In the **Add Template Mapping** window:
- **Source DLP Type**: From the drop-down menu, select the source DLP type. Source DLP types are **Email**, **Endpoint**, **Inline**, and **SaaS Security**.
- **Source Action**: From the drop-down menu, select the source action for the incident. The available source actions depend on the source DLP type you select.
- [Inline](#Inline-Source-Actions)
- [Endpoint](#endpoint-actions)
- [SaaS Security](#saas-security-api-actions)
- [Email](#email-actions)
- **Notification Type**: From the drop-down menu, select the notification type. Notification types are **End User Notification** and **Escalation**.
- In the Template Family section:
- **Email**: From the drop-down menu, select the email notification template family for the incident and notification type. All email notification template families that have been added on the **Notification Templates** page are available for selection.
- **Slack**: From the drop-down menu, select the Slack notification template family for the incident and notification type. All Slack notification template families that have been added on the **Notification Templates** page are available for selection. This field is only available if you have integrated Workflow Automation with Slack.
- **Team**: From the drop-down menu, select the Microsoft Teams notification template family for the incident and notification type. All Microsoft Teams notification template families that have been added on the **Notification Templates** page are available for selection. This field is only available if you have integrated Workflow Automation with Microsoft Teams.
- **Survey**: From the drop-down menu, select the survey template family for the incident and notification type. All survey template families that have been added on the **Survey Templates** page are available for selection.
[See image.](#template-mapping-add-incident)
- Click **Add**.
- []**Default**
- **Violates Compliance Category**
- **Violates Compliance Category Archived To Mailbox**
- **Violates Compliance Category Archive To Mailbox Failed**
- **Allowed**
- **Allowed And Archived To Mailbox**
- **Allowed And Archived to Mailbox Failed**
- []**Default**
- **Allow**
- **Block**
- **Confirm**
- []**Default**
- **Quarantine**
- **Remove**
- **Report Malware**
- **Apply Email Tag**
- **Report Incident**
- **Make Sharing Read Only**
- **Make External Sharing Read Only**
- **Make Internal Sharing Read Only**
- **Remove Public Link Sharing**
- **Revoke Sharing Make Private**
- **Remove External Sharing**
- **Remove Internal Sharing**
- **Remove All Collaborators**
- **Remove Internal Link Sharing**
- **Remove Discoverable**
- **Notify End User**
- **Apply Azure Information Protection Label**
- **Apply BOX Tag**
- **Move To Restricted Folder**
- **Apply Email Label**
- **Apply Google Drive Label**
- **Remove External Collaborators**
- **Quarantine To User Root Folder**
- []**Default**
[]To edit an incident template mapping:
- Go to **Setup** > **Template Mappings**. The **Template** **Mappings** page appears, listing all the incident template mappings that have been mapped on the **Incident** tab.
- (Optional) On the **Incident** tab, use the **Search** field to locate the template mapping that you want to edit.
- In the **Action** column next to the template mapping, click the **Edit** icon. The **Edit Template Mapping** window appears. You can only edit the template values in the **Template** **Family** section of the edit window.
- In the **Edit Template Mapping** window, change one or more of the following template family fields for an incident template mapping: **Email**, **Slack**, **Team**, and **Survey**. The **Slack **template family field is only available if you have integrated Workflow Automation with Slack, and the **Teams **template family field is only available if you have integrated Workflow Automation with Microsoft Teams.
To delete an incident template mapping, on the **Template Mapping** page, click the **Delete** icon next to an incident template mapping.
[]Before you can add a digest template mapping, add user and DLP admin digest notification templates on the Notification Templates page of the Workflow Automation Admin Portal. To learn more, see [Managing Notification Templates](/zia/managing-notification-templates).
To add a digest template mapping:
- Go to **Setup** > **Template Mappings**. The **Template** **Mappings** page appears, listing all the incident template mappings that have been mapped on the **Incident** tab.
- Click the **Digest **tab.
- On the **Digest **tab:
- Under User:
- From the **Email Template** drop-down menu, select a user digest email notification template family.
- From the **Slack Template **drop-down menu, select a user digest Slack notification template family. The **Slack Template** field is only available if you have integrated Workflow Automation with Slack.
- From the **Teams Template **drop-down menu, select a user digest Microsoft Teams notification template family. The **Teams Template** field is only available if you have integrated Workflow Automation with Microsoft Teams.
- Under DLP Admin:
- From the **Email Template** drop-down menu, select a DLP admin digest email notification template family.
- From the **Slack Template** drop-down menu, select a DLP admin digest Slack notification template family. The **Slack Template** field is only available if you have integrated Workflow Automation with Slack.
- From the **Teams Template **drop-down menu, select a DLP admin digest Microsoft Teams notification template family. The **Teams Template** field is only available if you have integrated Workflow Automation with Microsoft Teams.
[See image.](#template-mapping-add-digest)
[]To edit the digest template mapping:
- Go to **Setup** > **Template Mappings**. The **Template** **Mappings** page appears, listing all the incident template mappings that have been mapped on the **Incident** tab.
- Click the **Digest **tab.
- On the **Digest **tab, change any of the user or DLP admin template families that are displayed. Select another email notification template family from the **Email Template** drop-down menu, select another Slack notification template family from the **Slack Template** drop-down menu, or select another Microsoft Teams notification template family from the **Teams Template** drop-down menu. The **Slack Template** fields are only available if you have integrated Workflow Automation with Slack, and the **Teams Template** fields are only available if you have integrated Workflow Automation with Microsoft Teams.
[]To view incident and digest template mappings:
- Go to **Setup** > **Template Mappings**. The **Template** **Mappings **page appears, listing all the incident template mappings that have been mapped on the **Incident** tab. For incident template mappings, you can view:
- **Source DLP Type**: The type of DLP incident. Source DLP types are **Email**, **Endpoint**, **Inline**,** **and **SaaS Security**.
- **Notification Type**: The type of notification for an incident. Notifications are **End User Notification** and **Escalation**.
- **Source Action**: The source action for the incident notification. Source actions vary depending on the source DLP type.
- **Email Template**: The email notification template family used for this type of incident notification.
- **Slack Template**: The Slack notification template family used for this type of incident notification. The **Slack Template** field is only available if you have integrated Workflow Automation with Slack.
- **Teams Template**: The Microsoft Teams notification template family used for this type of incident notification. The **Teams Template** field is only available if you have integrated Workflow Automation with Microsoft Teams.
- **Survey Template**: The survey template family used for this type of incident notification.
[See image.](#Template-Mapping-Page-View-All-Incident)
- Click the **Digest** tab. The **Digest** tab appears, listing the **Email Template **families, **Slack Template **families,** **and** Teams Template **families for the user and DLP admin digest notifications. The **Slack Template** family fields are only available if you have integrated Workflow Automation with Slack and the **Teams Template** family fields are only available if you have integrated Workflow Automation with Microsoft Teams.
[See image.](#Template-Mapping-Page-View-Digest)
[]![Add Template Mapping Window](/downloads/workflow-automation/setup/managing-incident-and-digest-template-mappings/WA-Add-Template-Mapping-Window.png)
[]![Template Mappings Page - Digest Tab](/downloads/workflow-automation/setup/managing-incident-and-digest-template-mappings/WA-Template-Mapping-PG-Add-Digest-Mapping.png)
[]![Template Mappings Page - Incidents tab](/downloads/workflow-automation/setup/managing-incident-and-digest-template-mappings/WA-Template-Mapping-PG-Incident-Tab.png)
[]![Template Mappings Page - Digest Tab](/downloads/workflow-automation/setup/managing-incident-and-digest-template-mappings/WA-Template-Mappings-Page-Digest-Tab.png)