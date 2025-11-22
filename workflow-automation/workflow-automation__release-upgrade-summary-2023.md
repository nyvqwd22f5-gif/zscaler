# Release Upgrade Summary (2023)
Source: https://help.zscaler.com/workflow-automation/release-upgrade-summary-2023

This article provides a summary of all new features and enhancements for Workflow Automation. To view all the older release notes of Workflow Automation, go to [ZIA Release Upgrade Summary (2023)](/zia/release-upgrade-summary-2023).

**Clouds:** Zscaler Automation
The following service updates were deployed to Zscaler Automation on

## December 11, 2023
### Feature Available
#### Auto-Populate Manager's Name in the Incident Details Page
In the Incident Details page, when you escalate an incident to the user's manager for approval, the manager's email assigned to the incident is auto-populated in the Escalate window. You cannot edit the manager's email.
[See image.](#greyed-out-manager-field)
To learn more, see [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).
![Screenshot of the greyed out Manager Field in the Escalate window](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/WA-release-notes-escalate-greyed-out-manager-field-image.png)
[]

### Feature Available
#### Enhancements to Digest Notifications
The incident count provided in your user or DLP admin digest notification message for Email, Slack, and Microsoft Teams is only accurate to the date and time when the notification is generated. The count changes as new incidents are created, reassigned, or resolved.
To learn more, see [Responding to a User Digest Notification](/workflow-automation/responding-user-digest-notification) and [Responding to a DLP Admin Digest Notification](/workflow-automation/responding-dlp-admin-digest-notification).

### Feature Available
#### Enhancements to the Incidents Page
In the Incidents page, you can search for an incident using duplicate transaction IDs. The search displays the actual transaction ID of the incident created because of the policy violation.
[See image.](#duplicate-incidents-search)
To learn more, see [About Incidents](/workflow-automation/about-incidents).
![Screenshot of the Transaction ID search for duplicate incidents in the Incidents page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/WA-release-notes-incidents%20page-search-duplicate-incidents.png)
[]

## November 29, 2023
### Feature Available
#### Delete Incidents
An incident can be deleted by selecting the Delete action for the incident on the Incident Details page.
[See image.](#Incident-Details-Page)
To learn more, see [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).
[][![Screenshot of the Incident Details Page Displaying the Action Menu in the Workflow Automation Admin Portal](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-1130-Incident-Details-Page.png)
](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-1130-Incident-Details-Page.png)

### Feature Available
#### Enhancements to Incident Group Mapping and Workflow Mapping
The incident group mapping and workflow mapping are enhanced. The EQUALS, NOT_EQUALS, CONTAINS_EXACT, and NOT_CONTAINS_EXACT operations make case-insensitive comparisons with the value entered for the property.
To learn more, see [Managing Incident Group Mappings](/workflow-automation/managing-incident-group-mappings) and [Managing Workflow Mappings](/workflow-automation/managing-workflow-mappings).

### Feature Available
#### Enhancements to the Incidents Page
The Incidents page is enhanced.
- The Priority filter enables you to filter incidents by all priorities or by only high and critical priorities.
- The Open, Resolved, Waiting Feedback, and Escalated widgets display a blue bottom border after the widget is selected.
[See image.](#Incidents-Page-Enhancements)
[][![Screenshot of the Incidents Page in the Workflow Automation Admin Portal](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-1130-Incidents-PG-Enhancements.png)
](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-1130-Incidents-PG-Enhancements.png)

### Feature Available
#### Enhancements to Workflow Automation API: New Audit Logs Endpoint
A new `POST /dlp/v1/customer/audit` endpoint is added to the Workflow Automation API. You can use this endpoint to filter audit logs for every action made by the admins or APIs based on the specified time period and field values.
To learn more about the endpoint, see [Understanding Workflow Automation API](/workflow-automation/understanding-workflow-automation-api) and [API Rate Limit Summary](/workflow-automation/api-rate-limit-summary-workflow-automation-api).
The Postman collection is also updated to include the new resource. To learn more, see [Configuring the Postman REST API Client](/workflow-automation/configuring-postman-rest-api-client-workflow-automation-api).

### Feature Available
#### Export Incidents to a CSV File
The incidents that are displayed on the Incidents page can be exported to a CSV file by clicking the Export icon.
[See image.](#Incidents-Page)
To learn more, see [About Incidents](/zia/about-incidents).
[][![Screenshot of the Incidents Page in the Workflow Automation Admin Portal](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-1130-Incidents-PG.png)
](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-1130-Incidents-PG.png)

### Feature Available
#### Notify User and Close Incident Workflow Template
The Notify Owner and Close Incident workflow template notifies the user that generated the incident and closes the incident if a response is not received from the user after a configurable time period in seconds.
[See image.](#Workflow-Template)
To learn more, see [Managing Workflow Templates](/workflow-automation/managing-workflow-templates) and [Managing Workflows](/workflow-automation/managing-workflows).
[][![Screenshot of the Auto Notify User and Close Incident Template on the Workflow Settings Page in the Workflow Automation Admin Portal](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-1130-Workflow-Settings-PG-AutoNotifyCloseIncident.png)
](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/ZIA-WA-RN-1130-Workflow-Settings-PG-AutoNotifyCloseIncident.png)

### Feature Available
#### Support for Roles and Permissions
A new Roles page is added to the Setup > Roles and Permissions menu in the Workflow Automation Admin Portal. This page enables you to create roles and assign permissions to control a DLP admin's access to the major features of Workflow Automation.
[See image.](#roles-permissions-image)
As part of this feature, a new Roles field is added to the Setup > Admins > Add Admins window. You can add multiple roles to an admin while configuring admin assignments.
[See image.](#admin-assignments-image)
Ensure that you configure roles and permissions before configuring admin assignments.
To learn more, see [Managing Admins](/workflow-automation/managing-admins) and [Managing Roles and Permissions](/workflow-automation/managing-roles-and-permissions).
[]![Screenshot of Roles and Permissions option in the Setup menu in Workflow Automation Admin Portal](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/WA-release-notes-managing-roles-permissions.png)
[]![Screenshot of Roles field in the Add Admin Assignments window](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/WA-release-notes-managing-roles-permissions-admin-assignments.png)
