# Managing Incidents
Source: https://help.zscaler.com/workflow-automation/managing-incidents
PDF: https://help.zscaler.com/pdf/com/en/1420341.pdf

The Incidents page in Workflow Automation captures and displays a list of the transactions that have violated the Data Protection policies (Inline DLP, Endpoint DLP, Email DLP, and SaaS Security DLP) that your organization has configured in the ZIA Admin Portal. Each such recorded transaction is known as an incident. This page enables you to review and remediate Data Loss Prevention (DLP) incidents.
The following is a primary process flow for incident resolution using the Workflow Automation Admin Portal:
-
Workflow Automation assigns the transaction that violated the DLP policies of an organization (the incident) to an admin who has edit access to that incident group.
If the violated rules belong to an incident group that is not mapped to an admin, incidents are not auto-assigned to an admin. For those incidents, super admins can log in to the Incidents page and assign admins manually.
- The admin accesses the Incidents page in the Workflow Automation Admin Portal to review new incidents.
- The admin then starts investigating the new incident and determines whether to notify the end user (the next step) or escalate to an approver or the end user's manager (the step after that), depending upon the severity of the incident.
- An email notification requests justification from the end user. After receiving a justification, the admin either closes the incident or escalates it to an approver or the end user's manager (the next step).
- The approver or the end user's manager receives an email notification requesting advice on how to proceed. After the approver responds, the admin proceeds with the incident or closes it, depending upon the response.
While investigating an incident, the admin can also change the priority of the incident and assign a new DLP admin.
A restricted admin can only assign an incident to a super admin.
Viewing Incidents
On the Incidents page, you can do the following:
- [Select a date range for the incidents displayed on the Incidents page.](/workflow-automation/managing-incidents#date-range-filter)
- Filter the incident information that is displayed on the page by priority. To display only information about critical and high-priority incidents, select **High Only**.
- Filter the incident information that is displayed on the page by severity. To display only information about high-severity incidents, select **High Only**.
- [Use and manage the incident filters](/workflow-automation/using-incident-filters-workflow-automation).
- Reset all the applied filters.
- Export incidents to a CSV file.
-
View the following widgets:
- **All**: Displays the total number of incidents that have occurred in your organization (i.e., **Open**, **Unassigned**, **Resolved**, **Waiting Feedback**, and **Escalated **incidents).
- **Open**: Displays the number of open incidents (i.e., incidents with the status **New**, **Investigating**, or **Received** **Justification Response**).
- **Unassigned**: Displays the number of incidents that are not assigned to a DLP admin.
- **Resolved**: Displays the number of closed incidents (i.e., incidents with the status **Resolved**).
- **Waiting Feedback**: Displays the number of incidents awaiting justification from the end user or awaiting feedback from the approver after escalation (i.e., incidents with the status **Validating with User** or **Escalated**).
- **Escalated**: Displays the number of incidents escalated to the managers or approvers for further review (i.e., incidents with the status **Escalated**).
You can click a widget to view only the applicable incidents for the selected widget. For example, if you click the **Open** widget, only the incidents with the status **New**, **Investigating**, or **Received** **Justification Response **are displayed in the incidents table, and the widget is highlighted with a blue border. To reset the selection, click the widget again.
- Perform actions against one or more incidents available on a single page or bulk actions against all incidents available across different pages.
- Search for an incident by **All** or **Transaction ID**. The search only shows results that match the search string.
-
**All**: This option allows you to enter free-form text that can match multiple incidents. This search is not case-sensitive.
You can search for incidents associated with a URL by entering a complete URL (e.g., https://www.jumpshare.com/https-post) or the complete host name (e.g., www.jumpshare.com) for a URL.
You can also enter multiple strings within a single text string. If you enter multiple strings within a text string, each string is treated with an AND operation. For example, if you enter `Microsoft Office` as the text string, all incidents containing Microsoft and Office are returned with this search, such as Microsoft Office, Microsoft Office 365, and Office 365 Microsoft. This search does not return incidents containing only Microsoft or Office.
If you choose user attributes for obfuscation, you cannot search for incidents using these obfuscated user attributes.
In addition, there might be times when you perform a free-form text search for incidents and some of the incidents might not display in the search results due to the obfuscation settings. A notification message appears at the top of the incidents table to inform you of this situation.
[See image.](#obfuscation-search-message)
To learn more about obfuscation settings, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
-
**Transaction ID**: This option allows you to search for one or more incidents by their transaction IDs. To search for multiple incidents, enter the transaction IDs separated by a comma. You can search for up to 10 incidents.
You can also search for an incident using its duplicate transaction ID. The search result provides the actual transaction ID of the incident. To learn more about duplicated incidents, see [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details#Duplicate-Incidents).
- View a list of incidents that have occurred in your organization. For each incident, you can view:
- **Transaction ID**: The transaction ID for the incident. If duplicate incidents exist for an incident, this column also displays the total count of the duplicate incidents next to the transaction ID. To learn more, see [Understanding Duplicate Incidents in Workflow Automation](/workflow-automation/understanding-duplicate-incidents-workflow-automation).
- **System Creation Date**: The date and time when the incident was created in the system. Workflow Automation searches the incidents based on the System Creation Date, and by default it sorts the incidents based on the Incident Date.
- **Last Change Date**: The date and time when the incident was last modified. The date and time are displayed in the local time zone of the admin.
- **Priority**: The priority of the incident. Priorities are **Critical**, **High**, **Medium**, and **Low**.
- **Severity**: The severity of the incident. Severities are **High**, **Medium**, and **Low**.
- **DLP Admin**: The DLP admin who is responsible for the incident.
- **Source DLP Type:** The type of DLP policy that the incident violated. Source DLP types are **Inline**, **Email**, **Endpoint**, and **SaaS Security**.
- **DLP Type**: The type of DLP incident. This value is retrieved from the incident itself.
- **Labels**: The labels assigned to the incident.
- **Status**: The status of the incident. Statuses are:
- **New**
- **Investigating**
- **Validating with User**
- **Justification Response Received**
- **Escalated**
- **Resolved**
- **Engine**: The DLP engine associated with the incident.
- **Dictionary**: The DLP dictionary associated with the incident.
- **Rule**: The DLP rule associated with the incident.
- **Dictionary Match Count**: The number of times the incident matched the dictionary.
- **Action**: The action associated with the incident.
- **Destination**: The destination of the incident.
- **Last Change**: The latest state of the incident. It indicates the most recent change to the incident.
- **Incident Date**: The date and time when the incident was generated due to a policy violation. The date and time are displayed in the local time zone of the end user.
- **Incident Groups: **The incident groups associated with the incident.
- **Justification Reason**: The reason for the incident submitted by the end user, the end user's manager, or another approver.
- **Justification Note**: The justification type of the incident.
- **Username**: The name of the end user responsible for the incident. When you click the name link, you are redirected to the Incidents page, which displays only the incidents created by that end user. The user filter is automatically applied in the Filters section. If you applied other filters before clicking the name link, those filters remain applied, as well. If you choose the User Name attribute for obfuscation, multiple asterisks appear for this field. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- **Client IP**: The client IP address of the end user. If you choose the Client IP attribute for obfuscation, multiple asterisks appear for this field. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- **File Name**: The name of the file associated with the incident.
- **File Type**: The type or extension of the file.
- **File MD5**: The 32-character MD5 hash of the file.
- **Application Name**: The name of the application.
- **Application Category**: The category of the application.
- **Home Location**: The home location of the end user.
- **Work Location**: The work location of the end user.
- **Department**: The department of the end user.
- **Referrer URL**: The referrer URL of the application.
- **File Source Location**: The source location of the file.
- **File Size**: The size of the file in bytes.
- **File Modification Time**: The date and time that the file was last modified.
- **Document Type**: The type of document.
- **Resolution Date**: The date and time when the incident was resolved (i.e., closed).
- **Integration**: The name of the DLP application integration in Workflow Automation where the incident occurred. To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services](/workflow-automation/configuring-dlp-application-integration-using-amazon-web-services), [Configuring the DLP Application Integration Using Azure](/workflow-automation/configuring-dlp-application-integration-using-azure), and [Configuring the DLP Application Integration Using Google Cloud Platform](/workflow-automation/configuring-dlp-application-integration-using-google-cloud-platform).
- **Channel**: The type of channel (e.g., Network Drive Transfer or Remote Drive Transfer) that the user used to cause the incident. This field appears only for incidents of Source DLP type Endpoint.
- **External Collaborators Groups**: The collaborator groups outside your organization for the incident. This field appears only for incidents of Source DLP type SaaS Security.
- **File Link Expiry**: The date and time when the file link expires. This field appears only for incidents of Source DLP type SaaS Security.
- **File Modified By**: The email address of the user who last modified the file. This field appears only for incidents of Source DLP type SaaS Security.
- **File Shared By**: The email address of the user who shared the file. This field appears only for incidents of Source DLP type SaaS Security.
- **File Shared At**: The date and time when the file was shared. This field appears only for incidents of Source DLP type SaaS Security.
- **Triggered Recipients**: The recipients who took actions that triggered rules on which some action was taken, such as allow and block. This field appears only for incidents of Source DLP type Email. If you choose the Recipient Email attribute for obfuscation, multiple asterisks appear for each recipient email in this field. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- **Internal Recipients**: The recipients within your organization who received the email that caused the incident. This field appears only for incidents of Source DLP type SaaS Security. If you choose the Recipient Email attribute for obfuscation, multiple asterisks appear for each recipient email in this field. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- **External Recipients**: The recipients outside your organization who received the email that caused the incident. This field appears only for incidents of Source DLP type SaaS Security. If you choose the Recipient Email attribute for obfuscation, multiple asterisks appear for each recipient email in this field. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- [Modify the table and its columns.](/zia/using-tables-workflow-automation)
- [View detailed information about each incident on the Incident Details page.](/workflow-automation/managing-incidents#viewing-incident-details)
- [View the number of rows of incidents displayed on the page](/workflow-automation/managing-incidents#rows-per-page). You can modify the number of rows using the **Rows per page** drop-down menu.
[See image.](#viewing-incidents)
Managing Incidents
The Incidents page allows you to perform certain actions to manage the incidents assigned to you.
- [Apply Time Range Filter](#date-range-filter)
- [Export Incidents](#exporting-incidents)
- [Perform Actions](#permorming-actions)
- [Perform Bulk Actions](#bulk-actions)
- [View Incident Details](#viewing-incident-details)
- [Modify Rows Per Page](#rows-per-page)
[]You can filter the incidents displayed on the Incidents page by the date and time of occurrence. By default, this page displays information about the incidents that occurred in the current calendar week (Sunday through Saturday). The time range filter applies to all widgets. Time ranges are:
- Hours
- Current Hour
- Last Hour
- Last 2 Hours
- Last 6 Hours
- Last 12 Hours
- Days
- Current Day
- Last Day
- Weeks
- Current Week
- Last Week
- Months
- Current Month
- Last Month
-
Custom Date Range
To view the incidents that occurred in a specific date range, you can use the **Custom Date Range** option and specify the start and end dates and times. The **Custom Date Range** option only supports incidents that are up to 6 months old, and you can only search for a maximum of a three-month rolling window.
[See image.](#date-range-filter-image)
[]You can export all incidents, or you can use the filter criteria or sort the incidents to modify the incidents that are displayed, and then export those incidents. After you perform the export action, and when your incident file export is successfully completed, Workflow Automation emails you a notification stating that your incident file export is successfully completed. The incident file is available on the [Downloads](/workflow-automation/managing-downloads) page, where you can download the incidents to a CSV file. The CSV file lists the incidents in the order in which they appeared in the Incidents table when you exported them.
Exporting numerous incidents takes time to download. Only a maximum of three bulk activities (download incidents and bulk actions) can be in progress concurrently.
[]To manage incidents, you can perform various actions against them. You can also perform these same actions against a single incident on the [Incident Details](/zia/viewing-managing-incident-details) page.
To perform actions:
- On the** Incidents** page, select the checkbox next to one or more **Transaction ID**s on a single page to select the incidents.
- From the **Actions** drop-down menu, select one of the following actions that you want to perform:
- [Assign DLP Admin](#assign-dlp-admin)
- [Assign to Me](#assign-to-me)
- [Assign Priority](#assign-priority)
- [Close Incident](#close-incident)
- [Notify User](#notify-user)
- [Investigating](#investigating)
- [Escalate](#escalate)
- [Label](#label)
- [Update Incident Group](#update-incident-group)
[See image.](#actions-button-image)
[]To assign a DLP admin for incidents:
-
Select **Assign DLP Admin**.
The **Assign DLP Admin** window appears.
- In the **Assign DLP Admin** window, you can:
-
**DLP Admin**: Select a DLP admin to assign to the incident. The drop-down menu displays only the DLP admins who have edit access to the incident groups. If you have selected two or more incidents, the menu displays only DLP admins who have edit access to at least one incident group of the selected incidents. An empty menu indicates that no DLP admin has edit access to the incident groups.
Only DLP admins with full access to Workflow Automation can assign incidents to DLP admins with restricted access.
- **Notes**: (Optional) Enter additional notes for the action.
- Click **Assign**.
[See image.](#assign-dlp-admin-image)
[]To assign incidents to yourself, select **Assign to Me**. The selected incidents are assigned to you.
[]To close incidents:
-
Select **Close Incident**.
The **Close Incident** window appears.
- In the **Close Incident **window, you can:
- **Notes**: (Optional) Enter additional notes for the action.
- **Resolution Label**: Select a resolution label and values associated with the label.
- **False Positive**: If the incident is a false positive, select the **False Positive** checkbox
- Click **Close Incidents**.
[See image.](#close-incidents-image)
After an incident is closed (status is **Resolved**), you can still perform all the other actions against the incident except for the **Investigating** and **Escalate** actions, but the incident status remains at **Resolved**.
[]
To investigate incidents:
-
Select **Investigating**.
The **Investigating **window appears.
- (Optional) In the **Investigating **window, enter additional notes for the action.
- Click **Submit**.
[See image.](#investigating-image)
[]
To assign or modify priority for incidents:
-
Select **Assign Priority**.
The **Assign Priority** window appears.
- In the **Assign Priority** window, you can:
- **Priority**: From the drop-down menu, select the priority for the incidents.
- **Notes**: (Optional) Enter additional notes for the action.
- Click **Assign**.
[See image.](#assign-priority-image)
[]
To notify the current user about the incident:
-
Select **Notify User**.
The **Notify User** window appears.
- In the **Notify User** window, you can:
- **Channel Type**: Select the channel type through which you want to send the incident notification to the end-user. The current user for the incident is displayed in the **Current State Details** section of the [Incident Details](/zia/viewing-managing-incident-details) page.
- **Note to user**: (Optional) Enter additional notes for the action.
- Click **Submit**.
[See image.](#notify-user-image)
[]
To notify the user's manager or another approver about the incident:
- Select **Escalate**. The **Escalate** window appears.
- In the **Escalate** window, you can:
- **User Type**: Select the type of user (Manager and Approver) to whom you want to escalate the incident. If you select the Approver user type, the Approver field appears, where you can select the approver of your choice for the incident.
- **Channel Type**: Select the channel type through which you want to send the escalations to the user's manager or approver for further review.
- **Note to user**: (Optional) Enter additional notes for the action.
- Click **Submit**.
[See image.](#escalete-action-image)
[]
To add or remove labels for an incident:
-
Select **Label**.
The **Add or Remove Label** window appears.
- In the **Add or Remove Label** window, you can add or remove labels for an incident:
- To add a label:
- Click **Add**.
- In the **Label** field, from the drop-down menu, select a label for the incident.
- In the **Value **field, from the drop-down menu, select the label value if values are associated with that label.
- Click the **Add** icon to input more labels and values to add to the incident.
- Click **Submit**.
- To remove a label:
- Click **Remove**.
- In the **Label** field, from the drop-down menu, select a label for the incident.
- In the **Value **field, from the drop-down menu, select the label value if values are associated with that label.
- Click the **Add** icon to input more labels and values to be removed from the incident.
- Click **Submit**.
[See image.](#label-action-image)
Click the **Delete** icon to remove a label-value pair for the incident.
[]You can use the Update Incident Group action to do the following:
- Add additional incident groups to multiple incidents.
- Delete one or more of the incident groups that are currently assigned to multiple incidents. Deleting incident groups might result in unassigned incidents and the removal of the admin assigned to the incident.
- Update the incident group that is used for assigning the admin to multiple incidents. When making this update, you can select one of the newly added incident groups, or you can select another one of the incident groups that was previously assigned to the incidents.
- Assign a default incident group to those unassigned incidents that might occur as a result of deleting an existing assigned incident group.
To update incident groups assigned to multiple incidents:
-
Select **Update Incident Group**. The **Update Incident Group** window appears, displaying the following information:
- In the **Available **section, all the incident groups that have been assigned to at least one admin appear in alphabetical order. The number of available incident groups appears in parentheses next to the heading. To learn more, see [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- In the **Assigned** section, the incident groups that are currently assigned to the incidents appear. The number of assigned incident groups appears in parentheses next to the heading.
[See image.](#update-incident-group-window-initial)
- (Optional) Add incident groups:
-
(Optional) At the top of the window, use the search field to locate an incident group in the **Available** section.
The search for incident groups spans across the **Available**, **Assigned**, and **Newly added** sections.
-
In the **Available** section, click the **Add** icon next to each incident group that you want to add to the incidents. The incident group is moved from the **Available** section to the **Newly added** section. The number of newly added incident groups appears in parentheses next to the heading.
In the **Newly added** section, you can also delete a newly added incident group by clicking the **Delete** icon next to an incident group. After you delete an incident group, that incident group is displayed in the **Available** section. You can also click **Reset** to reset the window to the original incident group settings.
[See image.](#update-incident-group-window-add-delete-incident-groups)
-
(Optional) Delete assigned incident groups. You can delete assigned incident groups even if you have not added new incident groups. In the **Assigned** section, click the **Delete** icon next to each incident group you want to delete. After you delete an incident group, that incident group is displayed in the **Available** section.
[See image.](#update-incident-group-window-delete-assigned-incident-groups)
If you delete an assigned incident group in the **Assigned** section, and you have not added any new incident groups in the **Newly added **section, the **Assign Default Group** checkbox becomes available and is selected. Deleting an assigned incident group might result in unassigned incidents and the removal of the admin assignments for those incidents. Assigning a default group is only required if you delete an assigned incident group, and you have not added any new incident groups.
You must have at least one incident group assigned to the incidents. If you delete all the assigned and newly added incident groups, a message appears, stating that at least one group must be assigned. You can also click **Reset** to reset the window to the original incident group settings.
-
If you deleted an assigned incident group in the **Assigned** section, and you did not add any new incident groups in the **Newly added **section, assign the default incident group to be used for those incidents that might become unassigned as a result of the assigned incident group deletion. The system automatically selects the **Assign Default Group** checkbox. From the **Incident Group** drop-down menu, select the default incident group to be used for assigning admins to those unassigned incidents. The menu lists all the incident groups that have been assigned to at least one admin, and they are displayed in alphabetical order.
[See image.](#update-incident-group-window-assign-default)
-
(Optional) Update the admin assignment for the incidents:
You can update the admin assignment for the incidents to use one of the newly added incident groups or to use another one of the previously existing assigned incident groups.
- Select the** Update Admin Assignment** checkbox. The **Incident Group** field appears.
-
From the **Incident Group** drop-down menu, select the incident group to be used for assigning the admin to the incidents. This menu lists all the incident groups that are displayed in the **Assigned** and **Newly added** sections of the window.
[See image.](#update-incident-group-window-update-admin-assignment)
- (Optional) In the **Notes** field, enter additional notes for updating the incident groups.
- Click **Update**. The **Incident **page appears. To see the updates, refresh the page. After refreshing the page, you can see the following updates:
- The **Incident Groups **field for each incident displays the updated incident groups. Some of the incidents might display the default incident group if you assigned a default incident group.
- The** Priority** field might change on the incidents based on the final list of incident groups that you assigned to the incidents. The priority for the incidents is derived from the incident groups assigned to the incidents. If the incident groups have different priorities, the highest priority is used.
- If you updated the admin assignment to use a different incident group, the **DLP Admin** field for the incidents displays the name of the admin derived from that incident group.
- If you assigned a default incident group to support unassigned incidents, the **DLP Admin** field for those incidents displays the name of the admin derived from the default incident group.
- The **Last Change** field for each incident displays the latest state change that occurred for the incident group updates.
[]To perform bulk actions:
- On the** Incidents** page, select the checkbox of the **Transaction ID** header on the incident table.
- Click **Select All Incidents**. This action selects all incidents with or without filter criteria available across different pages on the incidents table.
-
From the **Actions** drop-down menu, select one of the following actions that you want to perform:
- [Assign DLP Admin](#assign-dlp-admin-bulk-actions)
- [Assign to Me](#assign-to-me-bulk-action)
- [Close Incident](#close-incident-bulk-actions)
- [Label](#label-bulk-actions)
- [Update Incident Group](#update-incident-group-bulk-action)
[See image.](#bulk-actions-menu)
Performing bulk action on numerous incidents takes time to complete. You can check the status of your bulk action on the [Bulk Actions](/workflow-automation/managing-bulk-actions) page. After you confirm the bulk action, and it is complete, Workflow Automation emails you a notification stating that your bulk action is successfully completed.
Only a maximum of three bulk activities (download incidents and bulk actions) can be in progress concurrently.
[]To assign a DLP admin for incidents:
-
Select **Assign DLP Admin**.
The **Assign DLP Admin** window appears.
- In the **Assign DLP Admin** window, you can:
-
**DLP Admin**: Select a DLP admin to assign to the incidents. The drop-down menu displays only the DLP admins who have edit access to the incident groups. An empty menu indicates that no DLP admin has edit access to the incident groups.
Only DLP admins with full access to Workflow Automation can assign incidents to DLP admins with restricted access.
- **Notes**: (Optional) Enter additional notes for the action.
- Click **Assign**.
[See image.](#assign-dlp-admin-bulk-actions-image)
[]To close incidents:
-
Select **Close Incident**.
The **Confirm Bulk Action **window appears.
- In the **Confirm Bulk Action **window, you can:
- **Notes**: (Optional) Enter additional notes for the action.
- **Resolution Label**: Select a resolution label and values associated with the label.
- **False Positive**: If the incident is a false positive, select the **False Positive** checkbox
- Click **Close Incidents**.
[See image.](#close-incidents-bulk-actions-image)
[]
To add or remove labels for incidents:
-
Select **Label**.
The **Add or Remove Label** window appears.
- In the **Add or Remove Label** window, you can perform an add or remove labels bulk action for incidents:
- To add a label:
- Click **Add**.
- In the **Label** field, from the drop-down menu, select a label for the incident.
- In the **Value **field, from the drop-down menu, select the label value if values are associated with that label.
- Click the **Add** icon to input more labels and values to add to the incident.
- Click **Submit**.
- To remove a label:
- Click **Remove**.
- In the **Label** field, from the drop-down menu, select a label for the incident.
- In the **Value **field, from the drop-down menu, select the label value if values are associated with that label.
- Click the **Add** icon to input more labels and values to be removed from the incident.
- Click **Submit**.
[See image.](#label-bulk-actions-image)
Click the **Delete** icon to remove a label-value pair for the incident.
[]To assign incidents to yourself:
-
Select **Assign to Me**.
The **Assign to Me **window appears.
- (Optional) In the **Assign to Me **window, enter additional notes for the action.
- Click **Assign to Me**.
[See image.](#assign-to-me-bulk-actions-image)
[]You can use the Update Incident Group action to do the following:
- Add additional incident groups to multiple incidents.
- Delete one or more of the incident groups that are currently assigned to multiple incidents. Deleting incident groups might result in unassigned incidents and the removal of the admin assigned to the incident.
- Update the incident group that is used for assigning the admin to multiple incidents. When making this update, you can select one of the newly added incident groups, or you can select another one of the incident groups that was previously assigned to the incidents.
- Assign a default incident group to those unassigned incidents that might occur as a result of deleting an existing assigned incident group.
To update incident groups assigned to multiple incidents:
-
Select **Update Incident Group**. The **Update Incident Group** window appears, displaying the following information:
- In the **Available **section, all the incident groups that have been assigned to at least one admin appear in alphabetical order. The number of available incident groups appears in parentheses next to the heading. To learn more, see [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- In the **Assigned** section, the incident groups that are currently assigned to the incidents appear. The number of assigned incident groups appears in parentheses next to the heading.
[See image.](#update-incident-group-window-initial-Bulk-Actions)
- (Optional) Add incident groups:
-
(Optional) At the top of the window, use the search field to locate an incident group in the **Available** section.
The search for incident groups spans across the **Available**, **Assigned**, and **Newly added** sections.
-
In the **Available** section, click the **Add** icon next to each incident group that you want to add to the incidents. The incident group is moved from the **Available** section to the **Newly added** section. The number of newly added incident groups appears in parentheses next to the heading.
In the **Newly added** section, you can also delete a newly added incident group by clicking the **Delete** icon next to an incident group. After you delete an incident group, that incident group is displayed in the **Available** section. You can also click **Reset** to reset the window back to the original incident group settings.
[See image.](#update-incident-group-window-add-delete-incident-groups-bulk-action)
-
(Optional) Delete assigned incident groups. You can delete assigned incident groups even if you have not added new incident groups. In the **Assigned** section, click the **Delete** icon next to each incident group you want to delete. After you delete an incident group, that incident group is displayed in the **Available** section.
[See image.](#update-incident-group-window-delete-assigned-incident-groups-bulk-action)
If you delete an assigned incident group in the **Assigned** section, and you have not added any new incident groups in the **Newly added **section, the **Assign Default Group** checkbox becomes available and is selected. Deleting an assigned incident group might result in unassigned incidents and the removal of the admin assignments for those incidents. Assigning a default group is only required if you delete an assigned incident group, and you have not added any new incident groups.
You must have at least one incident group assigned to the incidents. If you delete all the assigned and newly added incident groups, a message appears, stating that at least one group must be assigned. You can also click **Reset** to reset the window back to the original incident group settings.
-
If you deleted an assigned incident group in the **Assigned** section, and you did not add any new incident groups in the **Newly added **section, assign the default incident group to be used for those incidents that might become unassigned as a result of the assigned incident group deletion. The system automatically selects the **Assign Default Group** checkbox. From the **Incident Group** drop-down menu, select the default incident group to be used for assigning admins to those unassigned incidents. The menu lists all the incident groups that have been assigned to at least one admin, and they are displayed in alphabetical order.
[See image.](#update-incident-group-window-assign-default-bulk-action)
-
(Optional) Update the admin assignment for the incidents:
You can update the admin assignment for the incidents to use one of the new incident groups that you added or to use another one of the existing assigned incident groups.
- Select the** Update Admin Assignment** checkbox. The **Incident Group** field appears.
-
From the **Incident Group** drop-down menu, select the incident group to be used for assigning the admin to the incidents. This menu lists all the incident groups that are displayed in the **Assigned** and **Newly added** sections of the window.
[See image.](#update-incident-group-window-update-admin-assignment-bulk-action)
- (Optional) In the **Notes** field, enter additional notes for updating the incident groups.
- Click **Update**. The **Incident **page appears, displaying the incident group updates for the incidents. To see the updates, refresh the page. After refreshing the page, you can see the following updates:
- The **Incident Groups **field for each incident displays the updated incident groups. Some of the incidents might display the default incident group if you assigned a default incident group.
- The** Priority** field might change on the incidents based on the final list of incident groups that you assigned to the incidents. The priority for the incidents is derived from the incident groups assigned to the incidents. If the incident groups have different priorities, the highest priority is used.
- If you updated the admin assignment to use a different incident group, the **DLP Admin** field for the incidents displays the name of the admin derived from that incident group.
- If you assigned a default incident group to support unassigned incidents, the **DLP Admin** field for those incidents displays the name of the admin derived from the default incident group.
- The **Last Change** field for each incident displays the latest state change that occurred for the incident group updates.
[]To go to the [Incident Details](/zia/viewing-managing-incident-details) page, click the **Transaction ID** of an incident on the **Incidents** page. You can view detailed information about each incident, such as incident ID, violation details, state changes, priority, and severity, and manage the incident.
[See image.](#view-incident-details-image)
To view the **Incident Details** page for an incident in a new tab of the same browser window, right-click the **Transaction ID** of an incident on the **Incidents** page, and select **Open in New Tab**. In the new tab, the **Incident Details** page appears, displaying the detailed information for the incident. You can only view the incident details on this page. You cannot do any actions against the incident using this page.
[See image.](#view-incident-details-open-in-new-tab-image)
[]To modify the number of incidents displayed per page, click the **Rows per page** drop-down menu and select the number of rows. Options are **10 rows**, **20 rows**, **25 rows**, **50 rows**, and **100 rows**. The default display is **10 rows**.
You can also configure the rows that are displayed on the page using the **Table Options** dialog window.
[See image.](#rows-per-page-image)
![The Rows per page menu displaying the options available to set the number of incidents that the Incidents page displays](/downloads/workflow-automation/data-protection/incidents/managing-incidents/WA-managing-incidents-rows-per-page-menu.png)
[]
![Selecting the time range to apply for the incidents displayed on the Incidents page.](/downloads/workflow-automation/incidents/managing-incidents/WA-managing-incidents-date-range-filter.png)
[]
![Selecting new DLP Admin for the selected incidents in the Assign DLP Admin window](/downloads/workflow-automation/data-protection/incidents/managing-incidents/WA-managing-incidents-assign-dlp-admin-window.png)
[]
![Assigning new priority for the selected incidents in the Assign Priority window](/downloads/workflow-automation/data-protection/incidents/managing-incidents/WA-managing-incidents-assign-priority-window.png)
[]
![Assigning Resolution Label and notes for resolving the incidents in the Close Incident window](/downloads/workflow-automation/data-protection/incidents/managing-incidents/WA-managing-incidents-close-incident-window.png)
[]
![Selecting the User Type and Channel Type for escalating the incident to the manager or approver](/downloads/workflow-automation/data-protection/incidents/managing-incidents/WA-managing-incidents-escalate-action-window.png)
[]
![Selecting the Channel Type to send notifications about the incident to the end user](/downloads/workflow-automation/data-protection/incidents/managing-incidents/WA-managing-incidents-notify-user-window.png)
[]
![Adding optional notes or information to start investigating the incident in the Investigating window](/downloads/workflow-automation/data-protection/incidents/managing-incidents/WA-managing-incidents-investigating-window.png)
[]
![Adding Label and Value to the incidents in the Label window](/downloads/workflow-automation/data-protection/incidents/managing-incidents/WA-managing-incidents-perform-actions-label.png)
[]
![Bulk Actions - Selecting new DLP Admin for the all incidents in the Assign DLP Admin window](/downloads/workflow-automation/data-protection/incidents/managing-incidents/WA-managing-incidents-assign-dlp-admin-window-bulk-actions.png)
[]
![Bulk Actions - Assigning incidents to yourself in the Assign To Me window](/downloads/workflow-automation/data-protection/incidents/managing-incidents/WA-managing-incidents-assign-to-me-window-bulk-actions.png)
[]
![Bulk Actions - Adding Resolution Labels and Values for closing incidents in the Confirm Bulk Action window](/downloads/workflow-automation/data-protection/incidents/managing-incidents/WA-managing-incidents-confirm-bulk-action-window-bulk-actions.png)
[]
![Bulk Actions - Selecting Label and Value for incidents in the Add Label window](/downloads/workflow-automation/data-protection/incidents/managing-incidents/WA-managing-incidents-perform-bulk-actions-label.png)
[]
[]![Viewing the Update Incident Group window before incident groups are updated. The window contains an Available incident group section, an Assigned incident group section, an assign default group section, an update admin assignment section, and a Notes field.](/downloads/workflow-automation/incidents/managing-incidents/WA-Update-Incident-Group-Window-Incidents-Page-Access.png)
[]![Video showing how to add and delete new incident groups on the Update Incident Group window](/downloads/workflow-automation/incidents/managing-incidents/WA-Video-Update-Incident-Group-Window-Adding-Deleting-New-Incident-Groups.gif)
[]![Video showing how to delete assigned incident groups when new incident groups have been added on the Update Incident Group window](/downloads/workflow-automation/incidents/managing-incidents/WA-Video-Update-Incident-Group-Window-Deleting-Assigned-Incident-Groups-With-Newly-Added-Incidents.gif)
[]![Video showing how to assign the default incident group for incidents after deleting an assigned incident group when no new incident groups have been added on the Update Incident Group window](/downloads/workflow-automation/incidents/managing-incidents//WA-Video-Update-Incident-Group-Window-Deleting-Assigned-Incident-Groups-No-Newly-Added-Incidents.gif)
[]![Video showing how to update the admin assignment incident group for the incidents on the Update Incident Group window](/downloads/workflow-automation/incidents/managing-incidents/WA-Video-Update-Incident-Group-Window-Updating-Admin-Assignment.gif)
[]![Viewing the Update Incident Group window before incident groups are updated. The window contains an Available incident group section, an Assigned incident group section, an assign default group section, an update admin assignment section, and a Notes field. ](/downloads/workflow-automation/incidents/managing-incidents/WA-Update-Incident-Group-Window-Incidents-Page-Bulk-Action-Access.png)
[]![Video showing how to add and delete new incident groups on the Update Incident Group window](/downloads/workflow-automation/incidents/managing-incidents/WA-Video-Update-Incident-Group-Window-Adding-Deleting-New-Incident-Groups-Bulk.gif)
[]![Video showing how to delete assigned incident groups when new incident groups have been added on the Update Incident Group window](/downloads/workflow-automation/incidents/managing-incidents/WA-Video-Update-Incident-Group-Window-Deleting-Assigned-Incident-Groups-With-Newly-Added-Incidents-Bulk.gif)
[]![Video showing how to assign the default incident group for incidents after deleting an assigned incident group when no new incident groups have been added on the Update Incident Group window](/downloads/workflow-automation/incidents/managing-incidents/WA-Video-Update-Incident-Group-Window-Deleting-Assigned-Incident-Groups-No-Newly-Added-Incidents-Bulk.gif)
[]![Video showing how to update the admin assignment incident group for the incidents on the Update Incident Group window](/downloads/workflow-automation/incidents/managing-incidents/WA-Video-Update-Incident-Group-Window-Updating-Admin-Assignment-Bulk.gif)
![Selecting Transaction ID to navigate from the Incidents page to the Incident Details page](/downloads/workflow-automation/incidents/managing-incidents/WA-Managing-Incidents-Transaction-ID.png)
[]
[]![Viewing the Incidents page with the Open in New Tab option selected for an incident](/downloads/workflow-automation/incidents/managing-incidents/WA-Managing-Incidents-Page-Open-In-New-Tab.png)
![Viewing the Actions menu on the Incidents page when performing actions in bulk. The Actions menu has the following options: Assign DLP Admin, Assign To Me, Close Incident, Label, and Update Incident Group.](/downloads/workflow-automation/incidents/managing-incidents/WA-Incidents-PG-Bulk-Actions-Menu.png)
[]
![Viewing the Actions menu on the Incidents page. The Actions menu has the following options: Assign DLP Admin, Assign To Me, Assign Priority, Close Incident, Notify User, Investigating, Escalate, Label, and Update Incident Group.](/downloads/workflow-automation/incidents/managing-incidents/WA-Incidents-PG-Actions-Menu.png)
[]
[]
![Viewing the Incidents Page in the Workflow Automation Admin Portal](/downloads/workflow-automation/incidents/managing-incidents/WA-Managing-Incidents-Main-Page_0.png)
[]![Viewing the obfuscation message displayed on the Incidents page. Below the Actions drop-down menu and above the Incidents table a message reads "Some incidents may not display in search results due to the obfuscation settings".](/downloads/workflow-automation/incidents/managing-incidents/WA-Managing-Incidents-Page-Obfuscation-Message.png)