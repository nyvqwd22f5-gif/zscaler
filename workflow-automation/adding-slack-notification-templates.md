# Adding Slack Notification Templates
Source: https://help.zscaler.com/workflow-automation/adding-slack-notification-templates
PDF: https://help.zscaler.com/pdf/com/en/1495206.pdf

[]Workflow Automation allows you to create various Slack notification templates using the notification template builder to send notifications to the Data Loss Prevention (DLP) admins, managers, approvers, and end users. The notification template builder ensures that the notification template displays properly to all Slack clients.
You can only add Slack notification templates if you have integrated Workflow Automation with Slack.
To add a Slack notification template:
-
On the **Notification Template **page:
- **Template Name**: Enter a name for the template.
- **Template Family**: From the drop-down menu, select an existing template family or add a new template family.
- **Type**: From the drop-down menu, select **Slack**.
- **Digest**: Enable this option if you want to make this template a digest notification template. This option identifies whether the template is for a digest type of notification (user digest and DLP admin digest) or a non-digest type of notification (user notification and escalation).
- **Source Language**: From the drop-down menu, select a language in which you want to create the notification template.
After you select the template type, a section to create the Slack notification template appears under the row on the page. Using the options at the top of this new section, you can create and design a Slack notification template, change the content of the template, and insert links.
[See image.](#add-slack-template)
- In the content section, design the Slack notification template by entering text and using one or more of the following options:
- **Font options**: Change the font for the text to bold or italics.
- **Strikethrough**: Apply the strikethrough format to the text.
- **HTML**: Add custom HTML.
- **Lists**: Add a numbered list or a bulleted list.
- **Link**: Apply a link to the text that you have entered.
- **Select Merge Tag**: From the drop-down menu, select a merge tag. Merge tags are:
- **All Incidents Waiting for Feedback Count**
- **Client IP**
- **Current Time**
- **Customer ID**
- **Date**
- **Destination URL**
- **Document Name**
- **High Priority Incidents Waiting for Feedback Count**
- **Hostname or Application**
- **Incident ID**
- **New Incidents Count**
- **Note to the User**
- **Open Incidents Count**
- **Operation**
- **Priority**
- **Severity**
- **State Changes Count**
- **Time**
- **User Name**
- **Violated Policy**
- **Select Special Link**: From the drop-down menu, select a special link. The following are special links:
- **Incident Justification Magic Link**: Redirects the user to the Incident page, where they can view and enter justification details for an incident.
- **Incident Escalation Magic Link**: Redirects the manager or approver to the Incident page, where they can view and enter justification details for an incident.
- **Incident List Page Magic Link**: Redirects the user or the DLP admin to the Incident page, where they can view the incidents that require their attention.
- (Optional) Click **Save as Draft**. You can come back later and continue to work on the template design. The status of the template is **Draft**.
- (Optional) Click **Translate** to translate the newly created template into a different language. The **Translate **dialog window appears.
- In the **Translate** dialog window, from the **Translate To** drop-down menu, select a language to which you want to translate the template.
- Click **Preview** to view the translated template. The template displays in the selected language.
- (Optional) To revert the template to the original language, click **Reset**. Doing so also reverts any changes made after translation.
- Click **Publish Template**. The template is published, and the status of the template is **Published**. Workflow Automation only uses published templates for its notifications.
[]![Notification Template Page - Adding Slack Notification Template](/downloads/workflow-automation/setup/adding-slack-notification-templates/WA-Notification-Template-PG-Add-Slack-Notification.png)