# Release Upgrade Summary (2024)
Source: https://help.zscaler.com/workflow-automation/release-upgrade-summary-2024

This article provides a summary of all new features and enhancements for Workflow Automation.

**Clouds:** Zscaler Automation
The following service updates were deployed to Zscaler Automation on

## December 16, 2024
### Feature Available
#### Enhancements to Data Protection Features
The following are enhancements to the Data Protection features in Workflow Automation:
Enhancements to Incident Group and Workflow Mappings
The following are enhancements to incident group and workflow mappings:
- Support for the date matching property (Termination Date) when adding an incident group mapping or a workflow mapping. This Termination Date property is only available if you select CSV as the primary user data source on the Account Settings page.
- When mapping a property, the values you can select are based on your organization's values, and they are filtered by source DLP type.
[See image.](#enhancements)
To learn more, see [Managing Incident Group Mappings](/workflow-automation/managing-incident-group-mappings), [Managing Workflow Mappings](/workflow-automation/managing-workflow-mappings), [Managing Account Settings](/workflow-automation/managing-account-settings), and [Managing User Attributes](/workflow-automation/managing-user-attributes).
Enhancements to Bulk Actions
On the Incidents page, two new actions, Assign to Me and Assign DLP Admin, are available when performing bulk actions.
- Assign to Me action allows you to assign yourself as the DLP admin to all incidents in the incident list table.
- Assign DLP Admin action allows you to assign a new DLP admin to all incidents in the incident list table.
[See image.](#RN-bulk-actions)
To learn more, see [About Incidents](/workflow-automation/about-incidents).
Renamed Source DLP Type
Several pages (e.g., Incidents page, Incident Details page, and Incident Group Mapping page) in Workflow Automation either display or use the Source DLP Type incident attribute, which has a few different values. The Source DLP Type attribute value of SaaS Security API is renamed to SaaS Security on all those pages.
[See image.](#source-dlp-type)
To learn more, see [About Incidents](/workflow-automation/about-incidents), [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details), and [Managing Incident Group Mappings](/workflow-automation/managing-incident-group-mappings).
![Screenshot of the Assign to Me and Assign DLP Admin actions for performing bulk actions](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-about-incidents-bulk-actions.png)
[]
[]![Incident Group Mapping Page - Termination Date Property](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incident-Group-Mapping-Termination-Date.png)
![Workflow Mappings Page - Termination Data Property](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Workflow-Mapping-Termination-Date.png)
![Workflow Mappings Page - Source Actions Inline Property Values](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Workflow-Mapping-Source-Actions-Inline.png)
![Workflow Mappings Page - Source Actions SaaS Security Property Values](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Workflow-Mapping-Source-Actions-SaaSSecurity.png)
[]![Incidents Page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incidents-Page-Renamed-SaaSSecurity.png)
![Incident Details Page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incident-Details-Page-Renamed-SaaSSecurity.png)
![Incident Group Mapping Page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incident-Group-Mapping-Page-Renamed-SaaSSecurity.png)

## December 02, 2024
### Feature Available
#### Enhancements to Data Protection Features
The following are enhancements to the Data Protection features in Workflow Automation:
Enhancement to the Incidents Page
On the Incidents page, the Severity column is added to the incidents table. The severity of each incident appears in this column.
[See image.](#severity-column)
To learn more, see [About Incidents](/workflow-automation/about-incidents).
[]![Incidents Page - Severity Column](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incidents-Page-Severity-Column.png)
Enhancement to the DLP Azure Application Integration Configuration
When you configure the DLP application integration using Azure, one of the steps is to add a DLP Azure application integration in Workflow Automation using the output from the bash script and the Azure resource manager stack. On the add Zscaler DLP Azure Integration page, a Validate button is added. When you click this button after populating the fields on this page, the Workflow Automation system validates the configuration.
[See image.](#dlp-application-integration)
To learn more, see [Configuring the DLP Application Integration Using Azure](/workflow-automation/configuring-dlp-application-integration-using-azure) and [Managing DLP Azure Application Integrations in Workflow Automation](/workflow-automation/managing-dlp-azure-application-integrations-workflow-automation).
[]![Add Zscaler DLP Azure Integration Page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Add-Zscaler-DLP-Azure-Integration-PG-Validate-Button.png)
Enhancement to the Incident Details Page
On the Incidents Details page, for incidents of Source DLP type Email, the Files section appears. The Files section displays the files sent to the recipients of the incident. In the Files section, the Policy column is added to the Files table. When you click the View icon in the Policy field for a file, the Policy window appears, displaying the engines and the dictionaries with their match count that were violated by the file.
[See image.](#files-policy-window)
To learn more, see [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).
[]![Incident Details Page - Files Section](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/RN-WA-Incident-Details-Page-Email-Files-Section.png)
![Incident Details Page - Files Section - Policy Window](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/RN-WA-Incident-Details-PG-Files-Section-Policy.png)
User Attribute Obfuscation
To protect the privacy and security of the user information associated with incidents in your organization, you can select the user attributes you want the Workflow Automation system to obfuscate for those incidents. You select the user attributes you want obfuscated for your organization in the Privacy and Security section of the Account Settings page. In addition, you can override the organization's obfuscation settings for an admin on the Admin Assignment page.
When you select user attributes for obfuscation, that selection affects the admin's visibility of those user attributes on incidents on the Incidents, Incident Details, and workflow pages. The obfuscated user attributes appear as several asterisks instead of the actual values for the attributes. For example, if you select to obfuscate the User Name attribute, the User Name appears as ****** instead of the user's actual name.
[See image.](#obfuscation-images)
To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings), [Managing Admin Assignments](/workflow-automation/managing-admin-assignments), [About Incidents](/workflow-automation/about-incidents), and [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).
[]![Account Settings Page - Privacy and Security Drop-Down Section](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Account-Settings-Page-Privacy-Security-Section.png)
![Add Admin Assignment Window](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Add-Admin-Assignment-Win-Obfuscation.png)
![Viewing the Incident Details Page in the Workflow Automation Admin Portal](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incident-Details-Page-Obfuscated-Fields.png)
Enhancements to the Audit Logs page
The Audit Logs page is enhanced with new Module and Resource filters. You can filter the audit logs based on the Csv Upload module entry and the Csv User Data resource entry.
[See image.](#RN-audit-logs-filters)
To learn more, see[ About Audit Logs](/workflow-automation/about-audit-logs).
![Screenshot of the Filters window > Module and Resources filters in the Audit Logs page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-about-audit-logs-csv-upload.png)
[]

### Feature Available
#### Redesigned Workflow Automation Admin Portal
The Workflow Automation Admin Portal is redesigned to have a more modern look and feel. All the pages within the portal are redesigned. The following is a list of changes made to the portal:
- A new color scheme is used for all pages (e.g., background color, text color, button color, and search bar color). In addition, the menu and submenu for the portal appear in the new color scheme.
- The same common icons are used for all pages (e.g., Delete icon and Edit icon).
- The Workflow Automation logo appears in the Zscaler brand colors.
- The same font and font size are used for page and section headers, table headers, body text, and label and field values.
- The table rows for a table appear in one color. There are no longer alternating row colors.
[See image.](#incidents-page-redesigned)
[]![Incidents Page - Redesigned](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incidents-Page-Redesigned-Portal.png)
![Incident Details Page - Redesigned](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incidents-Details%20Page-Redesigned.png)

## November 18, 2024
### Feature Available
#### Enhancement to Workflow, Incident Group, and Event Group Mappings
On the Workflow Mappings page, Incident Group Mapping page, and Event Group Mappings page, the Property drop-down menu for a statement (i.e., rule) is redesigned to make the display and selection of properties more user friendly. The Property drop-down menu has the following improvements:
- Lines to illustrate the different levels of the property hierarchy.
- Shortened property names that appear in alphabetical order.
- Frozen header on top, which provides context on the complete property path when scrolling through the properties.
This enhancement applies to the Workflow Mappings page for Data Protection, Business Insights, and Digital Experience Monitoring (ZDX) integrations, the Incident Group Mapping page for Data Protection integration, and the Event Group Mappings page for Business Insights integration.
[See image.](#property-drop-down)
To learn more, see [Managing Workflow Mappings](/workflow-automation/managing-workflow-mappings), [Managing Incident Group Mappings](/workflow-automation/managing-incident-group-mappings), [Managing Workflow Mappings for Events](/workflow-automation/managing-workflow-mappings-events), [Managing Event Group Mappings](/workflow-automation/managing-event-group-mappings), and [Managing Workflow Mappings for ZDX Alerts](/workflow-automation/managing-workflow-mappings-zdx-alerts).
[]![Workflow Mappings Page - Property Field](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Workflow-Mappings-Page-Property-Field.png)
![Incident Group Mapping Page - Property Field](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incident-Group-Mapping-Page-Property-Field.png)
![Event Group Mappings Page - Property Field](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Event-Group-Mappings-Page-Property-Field.png)

### Feature Available
#### Restart Import Action for CSV Files
The following enhancements are available on the User Attributes page in the Workflow Automation Admin Portal:
-
When the status of a CSV file is Partial Complete, you can use the Resume icon under the Status column to resume importing the pending user attributes.
[See image.](#RN-resume-icon)
-
When the status of a CSV file is Failed, you can use the Retry icon under the Status column to restart the import action for the CSV file.
[See image.](#RN-retry-icon)
You can only restart an import action a maximum of three times.
As part of this enhancement, you receive email notifications when your CSV file import is completed, partially completed, or has failed.
To learn more, see [Managing User Attributes](/workflow-automation/managing-user-attributes).
![Screenshot of the Resume icon for the Partial Complete status for the CSV file import](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/RN-WA-managing-user-attributes-partial-complete-status-resume-icon.png)
[]
![Screenshot of the Retry icon for the Failed status for the CSV file import](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/RN-WA-managing-user-attributes-failed-status-retry-icon.png)
[]

## November 04, 2024
### Feature Available
#### Enhancements to Data Protection Features
The following are enhancements to the Data Protection features in Workflow Automation:
Support for Importing User Attributes as CSV File
Workflow Automation is enhanced to support importing user attributes as a CSV file. As part of this feature, the following updates are available:
-
A new User Attributes (Setup > User Attributes) page is added to the left-side navigation of the Workflow Automation Admin Portal. This page allows you to import end user attributes as a CSV file. The attributes then display in the Workflow Automation Admin Portal.
[See image.](#RN-csv-user-attributes-menu)
-
Two new options, Primary User Data Source (SCIM or CSV) and Unique Identifier (email address or employee ID), are added to the Account Settings page. You must select a primary user data source and a unique identifier from which Workflow Automation fetches the user attributes that display on the Workflow Automation Admin Portal.
[See image.](#RN-csv-account-settings)
-
A new option, Additional Information, is added to the Violation Details section of the Incident Details page. This section displays additional data associated with the incident, such as end user details, manager details, and address. Workflow Automation fetches the additional information from the primary user date source (i.e, CSV or SCIM) selected during the incident generation.
[See image.](#RN-csv-additional-information)
- The Property list on the Incident Group Mapping page and the Workflow Mapping page is enhanced. You can add additional `userInfo`, `managerInfo`,** **and `userInfo.Skip Level Managers` properties when configuring incident mappings and workflow mappings.
To learn more, see [Managing User Attributes](/workflow-automation/managing-user-attributes), [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details), [Managing Account Settings](/workflow-automation/managing-account-settings), [Managing Workflow Mappings](/workflow-automation/managing-workflow-mappings), and [Managing Incident Group Mappings](/workflow-automation/managing-incident-group-mappings).
![Screenshot of the User Attributes menu on the left side navigation](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-managing-user-attributes-left-menu.png)
[]
![Screenshot of the Primary user Data Source and the Unique identifier sections on the  Account Settings page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-user-attributes-account-settings.png)
[]
![Screenshot of the Additional Information section on the Incident Details page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-incident-details-addtional-information.png)
[]
Enhancement to the DLP Application Integration Configuration Using Amazon Web Services
When configuring the DLP application integration in Amazon Web Services (AWS), you have the option to create the AWS resources for this integration by creating a CloudFormation stack. Workflow Automation provides a template file that you can use to create the CloudFormation stack. Additional parameters are added to this template file for enhanced security and auditability and to define S3 retention (Lifecycle) policies. In addition, the Create Stack page is enhanced to support these new parameters. The following parameters are added:
- zirRoleARN
- lockRetentionMode
- lockRetentionDays
- enableCloudtrail
- cloudTrailLogsBucket
- enableExpiration
- expirationDaysCurrent
- expirationDaysNonCurrent
- incompleteMultipartDays
[See image.](#specify-stack-details)
To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services.](/workflow-automation/configuring-dlp-application-integration-using-amazon-web-services)
[]![Specify Stack Details Page in AWS](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-AWS-Specify-Stack-Details-Page-Complete-Page.png)

## October 18, 2024
### Feature Available
#### Enhancements to Data Protection Features
The following are enhancements to the Data Protection features in Workflow Automation:
Enhancement to Closed Incidents
On the Incidents page, after an incident is closed (Status is Resolved), you can perform the following actions from the Actions drop-down menu for one or more incidents, but the status for those incidents remains Resolved:
- Assign DLP Admin
- Assign to Me
- Assign Priority
- Notify User
- Label
[See image.](#Incidents-Page)
To learn more, see [About Incidents](/workflow-automation/about-incidents).
Enhancement to Workflow Templates
When adding a workflow on the Workflow Settings page using the templates for Auto Escalate, Auto Notify User and Escalate, or Auto Notify User and Concurrently Escalate, you can select the approver for the workflow from the Approver Name drop-down menu. You must add approvers on the Approvers page in Workflow Automation before they are available to select in the Approver Name drop-down field for the workflow.
[See image.](#approver-name-drop-down)
To learn more, see [Managing Workflows](/workflow-automation/managing-workflows) and [Managing Approvers](/workflow-automation/managing-approvers).
[]![Incidents page - Actions Drop-Down for Closed Incidents](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incidents-Page-Actions-After-Resolved.png)
[]![Workflow Settings Page - Approver Name field](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Workflow-Settings-Page-Approver-Name-Field.png)

## October 03, 2024
### Feature Available
#### Enhancement to Event Details Page for Business Insights Events
On the Event tab of the Event Details page, the Users Count By Plan Type field is added to the Event Details section, replacing the Plan Type field. The User Count By Plan Type field lists the plan types for the application associated with the event along with the number of impacted users under those plan types for the event. If there are more than 5 plan types, a Show More link becomes available for the field. You can click this link to see the rest of the plan types with their user counts.
[See image.](#event-details-page)
To learn more, see [Managing Event Details](/workflow-automation/managing-event-details).
[]![Viewing  an Event on the Event Details Page in the Workflow Automation Admin Portal](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Event-Details-Page-Plan-Types-Field.png)

### Feature Available
#### Enhancements to Data Protection Features
The following are enhancements to the Data Protection features in Workflow Automation:
Enhancement to Closed Incidents
On the Incident Details page, after an incident is closed (Status=Resolved), you can perform the following actions from the Actions drop-down menu for the incident, but the incident status remains as Resolved:
- Notify User
- Assign to Me
- Assign DLP Admin
- Assign Priority
- Ticket
- Label
[See image.](#incident-details-page-resolved-actions)
To learn more, see [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).
Enhancement to Auto Create Tickets Workflow
On the Workflow Settings page, when adding a workflow using the Auto Create Tickets template, the Ticketing Configuration section on the page is enhanced to contain the following fields:
- Ticketing Service
- Default Ticketing System
- Jira Project (Appears only when JiraCloud is selected in the Ticketing Service field)
- Default Ticket Assignee Email
From the Default Ticket Assignee Email drop-down menu, you can select the assignee for the ticket that gets created in JiraCloud or ServiceNow.
[See image.](#workflow-settings-page)
To learn more, see [Managing Workflows](/workflow-automation/managing-workflows) and [Managing Workflow Templates](/workflow-automation/managing-workflow-templates).
[]![Viewing the Actions Drop-Down Menu on the Incident Details Page in the Workflow Automation Admin Portal](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incident-Details-Page-Resolved-Incident-Actions.png)
[]![Adding an Auto Create Tickets Workflow on the Workflow Settings Page in the Workflow Automation Admin Portal](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Workflow-Settings-Page-Auto-Create-Tickets-Enh.png)
![Adding a Auto Create Tickets Workflow on the Workflow Settings Page in the Workflow Automation Admin Portal](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Workflow-Settings-PG-Auto-Create-Tickets-ServiceNow.png)

### Feature Available
#### Support for User Login to Workflow Automation Service from ZIdentity
Workflow Automation integrates with ZIdentity Admin Portal. Admins who have a subscription to ZIdentity can log in to Workflow Automation Admin Portal from the ZIdentity Admin Portal. Admins can also use the ZIdentity service to enroll Workflow Automation users as well as manage the roles of each user.
To learn more, see [What Is ZIdentity?](/zslogin/what-zslogin), [Accessing and Navigating the Workflow Automation Admin Portal](/workflow-automation/accessing-and-navigating-workflow-automation-admin-portal), [Accessing and Navigating the Workflow Automation Admin Portal for ZDX Alerts](/workflow-automation/accessing-and-navigating-workflow-automation-admin-portal-zdx), and [Accessing and Navigating the Workflow Automation Admin Portal for Events](/workflow-automation/accessing-and-navigating-workflow-automation-admin-portal-events).

## September 19, 2024
### Feature Available
#### Change to Event Status
On the Events page, the Closed event status is added for an event.
[See image.](#event-statuses)
To learn more, see [Managing Events](/workflow-automation/managing-events).
[]![Viewing the Status Column on the Event Details Page in Workflow Automation](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-BI-Events-Page-Status-Field.png)
![Viewing the Filters Section for the Events Page in Workflow Automation](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-BI-Events-Page-Filters-Section-Status.png)

### Feature Available
#### Change to the Event ID Field Format for Business Insights Events
The Event ID field format is changed everywhere it appears in the Workflow Automation Admin Portal for Business Insights events. The Customer ID prefix is removed from the Event ID field. The following image shows one example of where Event ID appears.
[See image.](#event-id-example)
To learn more, see [Managing Events](/workflow-automation/managing-events), [Managing Event Details](/workflow-automation/managing-event-details), and [Responding to an End User Notification for Events](/workflow-automation/responding-end-user-notification-events).
[]![Viewing the Events Page for Business Insights Events in Workflow Automation](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-BI-Events-Page-Event-ID.png)

### Feature Available
#### Enhancement to the Event Details Page
An Actions drop-down menu containing the Close Event action is added to the Event Details page for Business Insights events. You can select this action for a Business Insights event when you want to close it.
[See image.](#close-event)
To learn more, see [Managing Event Details](/tech-pubs-drafts/managing-event-details-doc-53893-and-doc-53896).
[]![Event Details Page - Actions Menu](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-BI-Event-Details-Page-Actions_0.png)

### Feature Available
#### Support for the Filewatcher
The following enhancements were made in support of the Filewatcher:
-
In Azure, when you are configuring the DLP application integration, you can run the Zscaler run-filewatcher.sh bash script to install or upgrade the container for the Filewatcher virtual machine using either the Docker or Podman platforms.
[See image.](#download-script)
-
On the Notifications Center page, an alert notification appears on this page for the Filewatcher when its health status is unhealthy. This alert notification is removed from this page when the Filewatcher health status changes back to healthy.
[See image.](#alert-notification)
To learn more, see [Viewing Alert Notifications](/workflow-automation/viewing-alert-notifications) and [Configuring the DLP Application Integration Using Azure](/workflow-automation/configuring-dlp-application-integration-using-azure).
[]![Viewing the Zscaler DLP Azure Integration Details Page Where the Run Filewatcher Script Can be Downloaded in the Workflow Automation Admin Portal](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Zscaler-DLP-Azure-Integration-runfilewatcher-script.png)
[]![Viewing the Notifications on the Notification Center Page in the Workflow Automation Admin Portal  ](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Notification-Center-PG.png)

## September 05, 2024
### Feature Available
#### Enhancement to Incident Trigger Data
On the Incident Details page and the incident escalation notification, the format for the trigger data that is displayed has changed. The prefix and suffix for the trigger data are displayed along with the trigger data itself. The actual trigger data portion is highlighted.
[See image.](#trigger-data)
To learn more, see [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details) and [Responding to an Escalation Notification](/workflow-automation/responding-escalation-notification).
[]![Viewing the Trigger Data Section on the Incident Details Page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Trigger-Data-Section.png)

### Feature Available
#### Enhancements to Incident Data Privacy Settings
The following enhancements were made to the incident data privacy settings in the Workflow Automation Admin Portal:
- On the DLP integration pages, all the field labels for the incident data privacy setting fields are changed to be more user-friendly.
- On the DLP integration pages, you can select the incident data privacy setting fields (Hide Evidence Data, Hide Trigger Data, and Hide Policy Details) for an admin, end user, and manager/approver. These privacy settings determine whether an admin, end user, or manager/approver can view the evidence data, trigger data, and policy details for the incidents that appear in the Workflow Automation Admin Portal.
[See image.](#DLP-Integration-Pages)
To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services](/workflow-automation/configuring-dlp-application-integration-using-amazon-web-services) and [Configuring the DLP Application Integration Using Azure](/workflow-automation/configuring-dlp-application-integration-using-azure).
[]![Viewing the Edit Zscaler DLP Integration Page for an AWS Integration](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Edit-Zscaler-DLP-AWS-Integration-Page.png)
![Viewing the Edit Zscaler DLP Integration Page for an Azure Integration](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Edit-Zscaler-DLP-Azure-Integration-Page.png)

### Feature Available
#### Enhancements to the Incident Details Page
The following enhancements were made to the Incident Details page:
-
The following fields are added to the Violation Details section:
- Incidents of Source DLP type Inline
- Application subsection
- Referrer URL
- Name
- Category
- Incidents of Source DLP type SaaS Security API
- Content subsection
- File Modification Time
- File Size
- Document Type
[See image.](#violation-details)
-
A Collaborators section is added for incidents of Source DLP type SaaS Security API. This section displays the internal and external collaborators for the incident and the collaborator scope.
[See image.](#collaborators)
To learn more, see [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).
[]![Viewing the Incident Details Page for Incidents of Source DLP type Inline](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incident-Details-Page-Application-Subsection.png)
![Viewing the Incident Details Page for Incidents of Source DLP type SaaS Security API](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incident-Details-PG-Content-Subsection.png)
[]![Viewing the Collaborators Section on the Incident Details Page for Incidents of Source DLP type Inline](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incident-Details-Page-Collaborators-Section.png)

### Feature Available
#### Enhancements to the Incidents Page
The following filters are added to the Filters section of the Incidents page:
- Department
- Document Type
- File Source Location
- Referrer URL
You can filter incidents by adding multiple values (comma-separated) to the File Source Location and Referrer URL filters and selecting multiple options that appear for Department and Document Type filters.
[See image.](#filters-dialog)
To learn more, see [About Incidents.](/workflow-automation/about-incidents)
[]![Incidents page - Filter section](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incidents-PG-Filters-Dialog.png)

## August 30, 2024
### Feature Available
#### Workflow Automation Integration with Business Insights
Workflow Automation supports integration with Business Insights. This integration provides you with the capability to view and manage Business Insights events that occur due to underutilized SaaS application licenses. It also enables you to configure workflows that automatically trigger tickets through a ticketing system for resolving Business Insights events. If a user has not logged into an application for a number of days specified by your organization, then an event is recorded in the Workflow Automation Admin Portal.
As a result of this integration, admins can streamline application license management allocated to the employees, leading to more granular and cost-effective management by creating tickets to manage Business Insights events.
To learn more, see [What Is Workflow Automation?](/workflow-automation/what-workflow-automation), [Step-by-Step Configuration Guide for Workflow Automation for Events](/workflow-automation/step-step-configuration-guide-workflow-automation-events), and [Accessing and Navigating the Workflow Automation Admin Portal for Events](/workflow-automation/accessing-and-navigating-workflow-automation-admin-portal-events).

## August 21, 2024
### Feature Available
#### Enhancement to the Notification Template Page
On the Notification Template page, an Update Template button is added when editing a published notification template. After editing the content or design for the published notification template, you click this button to update the notification template with the edits. This Update Template button replaces the Save as Draft and Publish Template buttons that were available before.
[See image.](#update-template-button)
To learn more, see [Managing Notification Templates](/workflow-automation/managing-notification-templates).
[]![Notification Template Page - Editing Published Notification](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Notification-Template-Page-Edit-Published.png)

### Feature Available
#### Resolved Incident Deletion
You can delete a resolved incident by selecting the Delete action from the Actions drop-down menu on the Incident Details page. For resolved incidents, only the Reopen and Delete actions appear in the Actions drop-down menu.
[See image.](#delete-resolved-incident)
To learn more, see [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).
[]![Screenshot of the Incident Details Page Where You Can Delete a Resolved Incident](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/RN-WA-Incident-Details-Page-Delete-Resolved.png)

## August 06, 2024
### Feature Available
#### Enhancements to API: Search Incidents Endpoint
The` POST /dlp/v1/incidents/search` endpoint supports the Incident Group and Engine field values. This enhancement allows you to provide the relevant incident group name and the DLP engine in the request body to search for an incident. The Postman collection is also updated to include new resources.
To learn more, see [Understanding Workflow Automation API](/workflow-automation/understanding-workflow-automation-api) and [Configuring the Postman REST API Client](/workflow-automation/configuring-postman-rest-api-client-workflow-automation-api).

## August 02, 2024
### Feature Available
#### Workflow Automation Integration with Zscaler Digital Experience (ZDX)
Workflow Automation supports integration with Zscaler Digital Experience (ZDX). This integration enables you to configure workflows that automatically trigger tickets for ZDX alerts through a SaaS application ticketing system. An alert is triggered when certain events in your organization meet the alert rule criteria defined in the ZDX Admin Portal.
As a result of this integration, admins can proactively monitor end user experience and productivity metrics that might fluctuate due to device and network issues and take the necessary steps to resolve those issues.
To learn more, see [What Is Workflow Automation?](/workflow-automation/what-workflow-automation), [Step-by-Step Configuration Guide for Workflow Automation for ZDX Alerts](/workflow-automation/step-step-configuration-guide-workflow-automation-zdx), and [Accessing and Navigating the Workflow Automation Admin Portal for ZDX Alerts](/workflow-automation/accessing-and-navigating-workflow-automation-admin-portal-zdx).

## July 23, 2024
### Feature Available
#### Enhancements to Duplicate Incidents
If the filename attribute is different for the file associated with an incident, Workflow Automation creates a new incident rather than duplicating it for the same Data Loss Prevention (DLP) violation. This enhances the chance of detecting malicious files forwarded through Zscaler.
To learn more, see [Understanding Duplicate Incidents in Workflow Automation](/workflow-automation/understanding-duplicate-incidents-workflow-automation).

### Feature Available
#### Support for Home and Work Location of End Users
Workflow Automation is enhanced to display the home location and work location of the end user associated with an incident. As part of this feature, the following updates are available:
- On the Incidents page:
-
Two columns, Home Location and Work Location, are added to the incidents list table.
[See image.](#home-work-country-columns)
-
Two filters, Home Location and Work Location, are added to the Filters Section.
[See image.](#home-work-country-filters)
-
On the Incident Details page, Home Location and Work Location attributes are added to the Violation Details section.
[See image](#home-work-country-fields)
To learn more, see [About Incidents](/workflow-automation/about-incidents) and [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).
![Home and Work Country columns](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-incidents-page-home-work-location-columns.png)
[]
![Home Country and Work Country filters](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-incidents-page-home-work-location-filters.png)
[]
![ Home and Work Country fields](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-incidents-details-home-work-location-fields.png)
[]

### Feature Available
#### Support for Labels Bulk Action
On the Incidents page, Label action is available when performing bulk actions, which allows you to add labels to all incidents in the incident list table.
[See image.](#RN-label-bulk-action)
To learn more, see [About Incidents](/workflow-automation/about-incidents).
![Screenshot of the Label bulk action for all incidents in the Incidents page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-label-bulk-actions.png)
[]

## July 09, 2024
### Feature Available
#### Async Activity Email Notifications
Workflow Automation is enhanced to send you email notifications about the completion status of your async activities (download incidents and bulk actions). The statuses are Complete, Partial Success and Failed.
To learn more, see [Managing Downloads](/workflow-automation/managing-downloads) and [Managing Bulk Actions](/workflow-automation/managing-bulk-actions).

### Feature Available
#### Enhancements to Alerts Notifications
When Workflow Automation does not receive DLP incidents for a time period, the application triggers a health check for the user's system. If an unhealthy status is returned by the Incident Receiver, an alert is automatically logged on the Notification Center page.
[See image.](#RN-incident-receiver-alert-notification)
To learn more, see [Viewing Alert Notifications](/workflow-automation/viewing-alert-notifications).
![Screenshot of the Incident Receiver module alert notification in the Notification Center page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-alert-notification-incident-receiver-module.png)
[]

### Feature Available
#### Enhancements to Export Incidents
When you download incidents from the Workflow Automation Admin Portal, the date and time of the incidents in the downloaded CSV file displays in your local time zone (i.e., your browser time settings).
To learn more, see [About Incidents](/workflow-automation/about-incidents).

### Feature Available
#### Enhancements to the Bulk Actions Page
A new Notes column is added to the Bulk Actions page, which displays any notes or information that the admin added when performing the bulk action.
[See image.](#notes-bulk-actions)
To learn more, see [Managing Bulk Actions](/workflow-automation/managing-bulk-actions).
![Screenshot of the Bulk Actions pages displaying the Notes column](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-bulk-actions-notes-column.png)
[]

### Feature Available
#### Enhancements to the Incidents Page
On the Incidents page, a new Assign to Me action is added to the Actions menu. This action allows admins to assign the selected incidents to themselves to investigate them.
[See image.](#RN-assign-to-me-action)
To learn more, see [About Incidents](/workflow-automation/about-incidents).
![Screenshot of the Assign To Me action in the Actions Menu - Incidents page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-about-incidents-actions-assigntome-button.png)
[]

### Feature Available
#### Limit for Concurrent Async Activities
For async activities (download incidents and bulk actions), there can be a maximum of three activities in progress concurrently.
For example, you have one incident file download with the Progress status on the [Downloads](/workflow-automation/managing-downloads) page and two bulk actions with the Progress status on the [Bulk Actions](/workflow-automation/managing-bulk-actions) page. In this case, you can only perform another async activity after one of these in progress activities is moved to a Complete or Failed status.
To learn more, see [About Incidents](/workflow-automation/about-incidents).

### Feature Available
#### Restart Activity for Downloads and Bulk Actions
The following enhancements are available on the Downloads and Bulk Actions pages in the Workflow Automation Admin Portal:
-
When the status of an incident file download or bulk action is Partial Success, you can use the Resume option available in the Status column to restart the activity for the pending incidents.
[See image.](#RN-resume-async-activity)
-
When the status of an incident file download or bulk action is Failed, you can use the Try Again option available in the Status column to restart the activity.
[See image.](#RN-tryagain-async-activity)
You can only restart an incident file download or bulk action for a maximum of three times.
To learn more, see [Managing Bulk Actions](/workflow-automation/managing-bulk-actions) and [Managing Downloads](/workflow-automation/managing-downloads).
![Screenshot of the Resume button the Partial Success incident downloads and bulk actions](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-resume-async-activity.png)
[]
![Screenshot of the Try Again button the Failed incident downloads and bulk actions](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-tryagain-async-activity.png)
[]

## July 01, 2024
### Feature Available
#### Enhancements to the DLP Azure Integration Page
In the Workflow Automation Admin Portal, the Integrations > DLP Azure > Zscaler DLP Azure Integration page is enhanced with the following updates:
- A new optional Custom Storage Endpoint URL field is added. This field allows you to use custom storage endpoints (i.e., private endpoints) to access the Azure storage accounts to minimize security risks.
- The Event Grid Topic Resource Id is renamed to Event Grid System Topic Resource Id.
[See image.](#RN-dlp-azure-integration-page)
To learn more, see [Configuring the DLP Application Integration Using Azure.](/workflow-automation/configuring-dlp-application-integration-using-azure)
![Screenshot of the DLP Azure Integration page displaying the Custom Storage Endpoint URL field](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Add-Zscaler-DLP-Azure-Integration-custom-storage-endpoint.png)
[]

### Feature Available
#### Enhancements to the Incidents Analytics Dashboard
An Export icon is added to the Incident Analytics dashboard that allows you to export the incident analytics displayed on the page to a PDF file.
[See image.](#RN-export-icon-dashboard)
To learn more, see [About Incident Analytics Dashboard](/workflow-automation/about-incident-analytics-dashboard).
![Screenshot of the Export icon on the Incident Analytics Dashboard](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-about-incident-analytics-export%20icon.png)
[]

### Feature Available
#### Enhancements to the Time Range Filter
The time range filter on the Incidents and the Incident Analytics pages is enhanced. You can select the current date (i.e., today's date) while configuring the Custom Date Range option to view specific incidents and incident analytics.
To learn more, see [About Incidents](/workflow-automation/about-incidents) and [About the Incident Analytics Dashboard](/workflow-automation/about-incident-analytics-dashboard).

### Feature Available
#### Support for Downloads Email Notifications
Workflow Automation is enhanced to send you email notifications when the incident file export is completed and the file is ready for download from the Downloads page.
[See image.](#RN-email-notification-downloads)
To learn more, see [Managing Downloads](/workflow-automation/managing-downloads).
![Screenshot of the Exporting Incidents is Complete email notification](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-downloads-complete-success-email-notification.png)
[]

### Feature Available
#### Support for Incidents Export Notifications
On the Incidents page, when you export incidents to a CSV file, you receive a notification in the Workflow Automation Admin Portal when your incident file export is successfully completed.
You must be logged in to the Workflow Automation Admin Portal to receive notifications.
To learn more, see [About Incidents](/workflow-automation/about-incidents).

### Feature Available
#### Support for the Bulk Actions Page
A new Bulk Actions page (My Activity > Bulk Actions) is added to the Workflow Automation Admin Portal. This page allows you to monitor the status of the bulk actions performed on the [Incidents](/workflow-automation/about-incidents) page. It provides you with details such as the type of bulk action, the incident count, the generation date and time, and the status of the bulk action.
[See image.](#RN-bulk-actions)
To learn more, see [Managing Bulk Actions](/workflow-automation/managing-bulk-actions).
![Screenshot of the My Activity > Bulk Actions page in Workflow Automation Admin Portal ](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-bulk-actions-page.png)
[]

## June 12, 2024
### Feature Available
#### Support for the Downloads page
A new My Activity > Downloads page is added to the Workflow Automation Admin Portal. This page allows you to download the incidents that you export from the [Incidents](/workflow-automation/about-incidents) page to a CSV file. It provides you with details such as the incident file name, number of incidents exported, the generation time and date, the status of the incident file download, etc.
[See image.](#RN-Downloads-page)
To learn more, see [Managing Downloads](/workflow-automation/managing-downloads).
![Screenshot of the My Activity > Downloads page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-managing-downloads.png)
[]

## May 24, 2024
### Feature Available
#### Enhancements to the Incidents Page
A new widget, All, is added to the Incidents page in the Workflow Automation Admin Portal. This widget displays the total number of incidents that have accrued in your organization regardless of the status (i.e., Open, Resolved, Waiting Feedback, and Escalated).
[See image.](#all-widget-incidents-RN)
To learn more, see [About Incidents](/workflow-automation/about-incidents).
![Screenshot of the All widget tile displayed in the Incidents page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-All-Widget-Incidents-Page.png)
[]

## April 29, 2024
### Feature Available
#### Auto Assign Incidents to Admins
A new Auto Assign Incidents field is added to the Admin Assignment > Add Admin Assignment window. Enable this field if you want Workflow Automation to automatically assign incidents to the admin as the incidents occur.
[See image.](#WA-RN-auto-assign-incidents)
To learn more, see [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
![Screenshot displaying the Auto Assign Incidents field in the Add Admin Assignment window when adding or editing configured admins](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Add-Admin-Assignment-PG-Auto-Assign-Incidents.png)
[]

### Feature Available
#### Enhancement to Admin Role Permissions
On the Add Role page, you can configure the permission for an admin role to delete an incident. For the Incidents category, you can select the Delete permission. For admins assigned to a role with incident delete permission, the Delete action is available to them on the Incident Details page. Otherwise, the Delete action is not available.
[See image.](#Delete-Permission)
To learn more, see [Managing Roles and Permissions](/workflow-automation/managing-roles-and-permissions) and [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).
[]![Viewing the Delete Incidents Permission on the Add Role Page in Workflow Automation](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Add-Role-Page-DeleteIncidentPermission.png)
![Viewing the Delete Action on the Incidents Details Page in Workflow Automation](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incident-Details-Page-Action-Delete.png)

### Feature Available
#### Enhancements to API: Labels Endpoint
A new `POST /dlp/v1/incidents/{dlpIncidentId}/labels` endpoint is added to the Workflow Automation API. You can use this endpoint to assign labels (label names and label values) to Data Loss Prevention (DLP) incidents. The Postman collection is also updated to include the new resource.
To learn more, see [Understanding Workflow Automation API](/workflow-automation/understanding-workflow-automation-api), [API Rate Limit Summary](/workflow-automation/api-rate-limit-summary-workflow-automation-api), and [Configuring the Postman REST API Client](/workflow-automation/configuring-postman-rest-api-client-workflow-automation-api).

### Feature Available
#### Self Assign Action for Incidents
A new action, Assign to Me, is added to the Actions menu on the Incident Details page. Admins can assign incidents to themselves using the Assign to Me action that appears on the page.
[See image.](#assign-to-me-button)
To learn more, see [Viewing & Managing Incident Details.](/workflow-automation/viewing-managing-incident-details)
[]
![Viewing the Assign to Me Button on the Incident Details Page in Workflow Automation](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incident-Details-PG-Assign-To-Me-Action.png)

### Feature Available
#### Support for Email DLP Incidents
Email Data Loss Prevention (DLP) incidents are displayed in Workflow Automation. You can remediate these incidents using the various actions on the Incidents and Incident Details pages in Workflow Automation and through the predefined workflows that Workflow Automation provides.
[See image.](#incidents-page)
To learn more, see [About Incidents](/workflow-automation/about-incidents), [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details), and [Understanding Workflows in Workflow Automation](/workflow-automation/understanding-workflows-workflow-automation).
[]![Viewing Email Type Incidents on the Incidents Page in the Workflow Automation Admin Portal](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incidents-Page-Email-Incidents.png)

## April 01, 2024
### Feature Available
#### Enhancements to the Incidents Page
On the Incidents page, if applicable, additional details for an incident appear. The following fields might appear for an incident:
- Dictionary Match Count
- Username
- Client IP
- File Name
- File Type
- File MD5
[See image.](#new-table-columns)
To learn more, see [About Incidents](/workflow-automation/about-incidents).
[][![Viewing Incident Details on the Incidents Page in Workflow Automation](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incidents-Page-New-Fields1.png)
](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incidents-Page-New-Fields1.png)
[![Viewing Incident Details on the Incidents Page in Workflow Automation](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incidents-Page-New-Fields2.png)
](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Incidents-Page-New-Fields2.png)

### Feature Available
#### Enhancements to the Incidents Page
On the Incidents page, two new filters are added to the Filters section: URL and Client IP. You can add multiple values (comma-separated) to the URL and Client IP filters to view the incidents corresponding to those values. These filters can do full-text matching for the values enter.
[See image.](#RN-URL-ClientIP-Filters)
To learn more, see [About Incidents](/workflow-automation/about-incidents).
![Screenshot of the URL and Client IP filters in the Incidents page - Filters section](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-URL-ClientIP-Filters.png)
[]

### Feature Available
#### Prefiltered Incidents for End Users
On the Incident Details page, under the Originating User section, you can click the username link to view all the incidents created by the same end user in the Incidents page. The end user's name is automatically applied in the Filters section, and the incidents table displays only the incidents that the end user is responsible for.
[See image.](#RN-prefiltered-username-hyperlink)
To learn more, see [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).
![Screenshot of the originating username prefiltered hyperlink in the Incident Details page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-viewing-managing-incident-details-username.png)
[]

## March 19, 2024
### Feature Available
#### Enhancements to the Incidents Page
On the Incidents page:
-
In the Filters section, a new Duplicated Incidents filter is added to filter only the incidents that have duplicate incidents.
[See image.](#RN-duplicated-incidents-filters)
-
If duplicate incidents exist for an incident, you can view the the total count of the duplicate incidents next to the Transaction ID in the incidents table.
[See image.](#RN-duplicate-incident-count)
To learn more, see [About Incidents](/workflow-automation/about-incidents).
![Screenshot of the Duplicated Incidents filter in the Incidents page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-about-incidents-duplicated-incidents-filters.png)
[]
[]![Screenshot of the duplicate incident count near Transaction ID in the Incidents page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-about-incidents-duplicate-incidents-count.png)

### Feature Available
#### Support for Reset Filters
A new Reset icon is added to the Workflow Automation Admin Portal, that can be used to reset all the applied filters. The new icon is added to the following pages:
- Notification Templates
- Survey Templates
- Audit Logs
- Incidents
- Incident Analytics Dashboard
[See image.](#RN-reset-filters-icon)
To learn more, see [Managing Notification Templates](/workflow-automation/managing-notification-templates), [Managing Survey Templates](/workflow-automation/managing-survey-templates), [About Audit Logs](/workflow-automation/about-audit-logs), [About Incidents](/workflow-automation/about-incidents), and [About Incident Analytics Dashboard](/workflow-automation/about-incident-analytics-dashboard).
![Screenshot of the Reset icon added to reset applied filters in the Workflow Automation Admin Portal](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-support-reset-filters-image.png)
[]

## February 28, 2024
### Feature Available
#### Enhancements to API: Close Incidents Endpoint
A new property, `resolutionLabel`, is added to the `POST /dlp/v1/incidents/{dlpIncidentId}/close` endpoint. This property allows you to provide the label and label value assigned to the incident to resolve and close it. The Postman collection is also updated to include new resources.
The label and the label value must be available in the Workflow Automation Admin Portal.
To learn more, see [Understanding Workflow Automation API](/workflow-automation/understanding-workflow-automation-api).

### Feature Available
#### Enhancements to the Incidents Page
On the Incidents page, in the Filters section, you can filter the incidents list by adding multiple values (comma-separated) to the Hostname or Application, User, and File Name filters.
[See image.](#RN-multiple-values-filters-image)
To learn more, see [About Incidents](/workflow-automation/about-incidents).
![Screenshot of the Hostname or Application, File Name, and User filters with a option to add multiple values in the Incidents page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-multiple-values-filters-incidents-page.png)
[]

## February 07, 2024
### Feature Available
#### Enhancements to Inline and Endpoint Source DLP Types
The following enhancements are available for incidents of Source DLP types Inline and Endpoint in the Workflow Automation Admin Portal:
-
On the Incidents page, a new Other Rule filter is added to the Filters section. You can use this filter to display the incidents that match the selected DLP rules.
[See image.](#other-rule-filter)
To learn more, see [About Incidents](/workflow-automation/about-incidents).
-
On the Incidents Details page:
-
A new Other Matched Rules field is added to display the rules that match the violated DLP rule that created the incident.
[See image.](#other-matched-rule-inline-endpoint)
-
Under Violation Details, the following fields are added to Endpoint Source DLP type:
- Device Name
- Device OS
- Device Trust Level
- File Size
- ZDP Mode
- Expected Action
- Confirm Action
- Confirm Justification
- Justification Text
- Additional Information
[See image.](#violation-details-endpoint)
To learn more, see [Viewing & Managing Incident Details](/zia/viewing-managing-incident-details).
-
On the Incidents Group Mappings and Workflow Mappings page, the Other Rules option is added to the Matching Policies property for Inline Source DLP type. When configuring an incident group or workflow mapping, you can select other DLP rules by rule name or the total number of rules.
[See image.](#other-rules-mappings)
To learn more, see [Managing Incident Group Mappings](/workflow-automation/managing-incident-group-mappings) and [Managing Workflow Mappings](/workflow-automation/managing-workflow-mappings).
![Screenshot of the Other Rule filter in the Filter section of the Incidents page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-incidents-page-other-rules-filters.png)
[]
![Screenshot of the Other Matched Rules field for Inline and Endpoint DLP types under the Violation Details section in the incidents Details page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-incidents-details-page-violation-details-inline-dlp.png)
[]
![Screenshot of the Violation Details section for Endpoint DLP type in the Incident Details page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-incidents-details-page-violation-details-endpoint-dlp.png)
[]
![Screenshot of the Other Rules option under the Matching Polices property in Incident Group and Workflow Mappings page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-other-rules-property-incident-workflow-mappings.png)
[]

### Feature Available
#### Enhancements to Multiple Language Templates Support
A new Transalate Template icon is added to the Notification Templates and Survey Templates pages. This icon allows you to translate a published, system default, or draft template into a different language based on your requirements. You can also revert the tanslated template to its original language.
[See image.](#release-notes-multi-language-enhancements)
To learn more, see [Managing Notification Templates](/workflow-automation/managing-notification-templates) and [Managing Survey Templates](/workflow-automation/managing-survey-templates%20).
[]
![Screenshot of the Translate Template icon in the Notification and Survey Templates page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Multipe-Language-Enhancementes-Translate-Template-Icon.png)

### Feature Available
#### Enhancements to Roles and Permissions Page
A new field, Product, is available when configuring new roles in the Workflow Automation Admin Portal. By default, the Product is DLP and you cannot change it. This field is also available as a column displaying the product of a role on the Roles page.
[See image.](#RN-product-roles)
To learn more, see [Managing Roles and Permissions](/workflow-automation/managing-roles-and-permissions).
![Screenshot of Product field in Add Role window in the Roles and Permissions page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-Add-Product-Roles-Permissions-Page.png)
[]

### Feature Available
#### Enhancements to the Incidents Details Page
A new section, User Notification, is added to the Incidents > Incidents Details page. This section allows the Data Loss Prevention (DLP) admin to effortlessly track the incident's notification status to manage the incident. It provides a detailed log of the incident's notifications and escalations sent to the originating user, the user's manager or approver.
[See image.](#user-notification-table-image-RN)
To learn more, see [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).
![Screenshot of the User Notification section with the table in the Incident Details Page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2024/WA-RN-incident-details-user-notification-table.png)
[]

### Feature Available
#### Enhancements to the Incidents Page
On the Incidents page, selecting widgets is independent of filters. When you click a widget (i.e, Open, Resolved, Waiting Feedback, and Escalated) to view the applicable incidents in the incidents table, Workflow Automation no longer applies the Status filter in the Filters section of the page.
To learn more, see [About Incidents](/workflow-automation/about-incidents).

## January 18, 2024
### Feature Available
#### Enhancements to API: Delete Incidents Endpoint
A new `DELETE /dlp/v1/incidents/{dlpIncidentId}` endpoint is added to the Workflow Automation API. You can use this endpoint to delete a DLP incident based on the specified incident ID.
To learn more about the endpoint, see [Understanding Workflow Automation API](/workflow-automation/understanding-workflow-automation-api) and [API Rate Limit Summary](/workflow-automation/api-rate-limit-summary-workflow-automation-api).
The Postman collection is also updated to include the new resource. To learn more, see [Configuring the Postman REST API Client](/workflow-automation/configuring-postman-rest-api-client-workflow-automation-api).

### Feature Available
#### Enhancements to the Incidents Page
Two new filters, File Name and File Type, are added to the Filters section of the Incidents page.
[See image.](#filetype-filename-filter)
To learn more, see [About Incidents](/workflow-automation/about-incidents)[.]
[]![Screenshot of the File Name and File Type filters in the Incidents and Incident Analytics page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/WA-RN-filename-filetype-filter-incident-analytics-page.png)

### Feature Available
#### Support for Incident Analytics Dashboard
A new Incident Analytics page is added to the Workflow Automation Admin Portal. The Incident Analytics dashboard provides high-level visibility and insight into your organization's Data Loss Prevention (DLP) incidents. It allows you to monitor and analyze various information about incidents over a specified time frame from a single location.
Only admins with full workflow access can monitor all the incidents through the dashboard. Admins with restricted workflow access can monitor only the incidents assigned to them.
[See image.](#RN-incident-analytics-dashboard)
To learn more, see [About Incident Analytics Dashboard](/workflow-automation/about-incident-analytics-dashboard).
[]
![Screenshot of the Incident Analytics dashboard in the Workflow Automation Admin Portal](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/WA-RN-incident-analytics-dashboard.png)

### Feature Available
#### Support for Multiple Language Template
The following updates are available in Workflow Automation as part of the Multiple Language support:
- On the Notification Template page and the Survey Template page:
-
A new option, Add Template, is added which allows you to create custom templates in addition to cloning system default templates.
[See image.](#add-template)
-
Two new filters, Template Family and Language, are added to the Filter section. The Category filter is renamed as Product in the Filter section.
[See image.](#new-filter-options)
-
A new column, Template Family, is added. All system default templates are displayed under the Template Family column.
[See image.](#template-family-column)
-
A new option, Translate, is available when creating, editing, or cloning a template to translate the template into a different language.
[See image.](#translate-option)
-
On the Incident Details page, a Language drop-down is added to the Notify User and Escalate window. You can select a language in which the notification and escalation messages are displayed.
[See image.](#language-incident-details)
-
On the Workflows page, a Language drop-down is added to the Notification Channel field when you add a new workflow. You can select a language in which the notification and escalation messages are displayed.
[See image.](#workflows-language-field)
To learn more, see [Managing Notification Templates](/workflow-automation/managing-notification-templates), [Managing Survey Templates](/workflow-automation/managing-survey-templates), [Managing Workflows](/workflow-automation/managing-workflows), and [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).
[]![Screenshot of the Add Template option in the Notification Template and Survey Template page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/WA-RN-multi-language-support-add-template.png)
![Screenshot of the new filters Template Family and Language in the Notification Template and Survey Template page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/WA-RN-multi-language-support-new-filter-options.png)
[]
[]![Screenshot of the Template Family column in the Notification Template and Survey Template page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/WA-RN-multi-language-support-template-family-column.png)
[]![Screenshot of the Translate option when creating, editing, and cloning in the Notification Template and Survey Template](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/WA-RN-multi-language-support-translate-option.png)
![Screenshot of the Language option in Notify User and Escalate window in the Incident Details page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/WA-RN-multi-language-support-incident-details-language-option.png)
[]
![Screenshot of the Add Workflows page with Language field for the Notification Channel](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2023/WA-RN-multi-language-support-workflows.png)
[]
