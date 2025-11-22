# Managing Bulk Actions
Source: https://help.zscaler.com/workflow-automation/managing-bulk-actions
PDF: https://help.zscaler.com/pdf/com/en/1487351.pdf

The Bulk Actions page allows you to monitor the progress of the bulk actions that Data Loss Prevention (DLP) admins perform on the incidents assigned to them. DLP admins with full access to Workflow Automation can perform bulk actions for all incidents that are available on the [Incidents](m/workflow-automation/about-incidents) page. This activity is recorded on the Bulk Actions page, where you can view the status of your bulk action in real time.
Admins can perform the** **following bulk actions for the incidents:
- Assign DLP Admin
- Assign to Me
- Close incidents
- Add Labels
- Update Incident Group
Performing bulk action on numerous incidents takes time to complete. Workflow Automation sends you an email notification when your bulk action is complete, suspended, partially complete, or has failed.
- [View Bulk Actions](#view-bulk-actions)
- [Restart Bulk Actions](#restart-bulk-actions)
[]To view the bulk actions:
- Go to **My Activity**. The **My Activity** page appears, displaying the **Downloads** and **Bulk Actions** tabs.
-
Click the **Bulk Actions** tab. The **Bulk Actions** tab lists all the bulk actions performed on the **Incidents** page. For each bulk action, you can view:
- **Name**: The bulk action that the admin performed on the Incidents page.
- **Incident Count**: The number of incidents associated with the bulk action.
- **Generation Time**: The date and time when the bulk action was performed.
-
**Status**: The status of the bulk action. The statuses are:
- **Complete**: The bulk action is successfully completed for the selected incidents.
- **Partially Complete**: The bulk action is incomplete for a few of the selected incidents.
- **Suspended**: The bulk action is suspended due to technical issues. After the issue is resolved, Workflow Automation automatically resumes the bulk action.
- **Failed**: The bulk action failed for the selected incidents.
To view the details of each bulk action, hover over the** Information** icon next to its status.
[See image.](#info-icon-partially-success)
- **Notes**: The notes that the admin added for the bulk action.
You can also search for a bulk action using the **Search** field on the page.
[See image.](#View-bulk-action-image)
[]For a bulk action that is partially complete or failed, you can restart the action on the **Bulk Actions** page.
To restart a bulk action:
-
Go to **My Activity**. The **My Activity** page appears, displaying the **Downloads** and **Bulk Actions** tabs.
[See image.](#my-activity-icon)
- Click the **Bulk Actions** tab. The **Bulk Actions** tab lists all the bulk actions performed on the **Incidents** page.
-
Restart a bulk action in one of the following ways:
-
For a partially complete bulk action, in the **Actions** column, click the** Resume** icon to restart the bulk action. The bulk action restarts, and the progress displays in the **Status** column.
[See image.](#reume-icon)
-
For a failed bulk action, in the **Actions** column, click the** Retry** icon to restart the bulk action. The bulk action restarts, and the progress displays in the **Status** column.
[See image.](#try-again-icon)
You can only restart a bulk action a maximum of three times. If you reach the maximum number of attempts, go to the **Incidents** page and perform the bulk action again.
[See image.](#error-message-maximum-attempts)
![Viewing the My Activity icon in the left-side navigation on the Workflow Automation Admin Portal](/downloads/workflow-automation/getting-started/admin-portal/managing-bulk-actions/WA-Managing-Bulk-Actions-My-Activity-Icon-Nav.png)
[]
![Viewing the Information icon for a failed bulk action on the My Activity page](/downloads/workflow-automation/getting-started/admin-portal/managing-bulk-actions/WA-Managing-Bulk-Actions-Failed-Info-Icon_0.png)
[]
![Viewing the Resume icon for a partially complete bulk action on the Bulk Actions page. This page lists the bulk actions in a table. The table has columns for Status, Notes, and Actions.](/downloads/workflow-automation/getting-started/admin-portal/managing-bulk-actions/WA-Managing-Bulk-Actions-Partially-Complete-Resume-Icon.png)
[]
![Viewing the Retry icon for a failed bulk action on the Bulk Actions page. This page lists the bulk actions in a table. The table has columns for Status, Notes, and Actions.](/downloads/workflow-automation/getting-started/admin-portal/managing-bulk-actions/WA-Managing-Bulk-Actions-Failed-Retry-Icon_0.png)
[]
![Bulk Actions page displaying the following message for a partially complete bulk action that has reached its maximum attempts: You have reached the maximum number of attempts to resume bulk action. Go to the Incidents page and perform the bulk action again.](/downloads/workflow-automation/getting-started/admin-portal/managing-bulk-actions/WA-Managing-Bulk-Actions-Resume-Message_0.png)
[]
[]![Viewing the bulk actions on the My Activity page](/downloads/workflow-automation/getting-started/admin-portal/managing-bulk-actions/WA-Managing-Bulk-Actions-Main-Page.png)