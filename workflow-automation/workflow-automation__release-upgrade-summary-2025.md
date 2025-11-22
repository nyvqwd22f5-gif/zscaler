# Release Upgrade Summary (2025)
Source: https://help.zscaler.com/workflow-automation/release-upgrade-summary-2025

This article provides a summary of all new features and enhancements for Workflow Automation.

**Clouds:** Zscaler Automation
The following service updates were deployed to Zscaler Automation on

## November 21, 2025
### Feature Available
#### Enhancements to Data Protection Features
The following are enhancements to the Data Protection features in Workflow Automation:
Introducing Custom Workflows
You can now create custom workflows in Workflow Automation using the custom workflow builder page accessed by clicking the Add Custom Workflow button on the Workflows page. The custom workflow builder page contains drag-and-drop capabilities that enable you to quickly create and configure a custom workflow.
[See image.](#custom-workflows)
To learn more, see [Understanding Workflows in Workflow Automation](/workflow-automation/understanding-workflows-workflow-automation) and [Managing Workflows](/workflow-automation/managing-workflows).
Enhancements to the Incidents Page
A few enhancements were made to the Incidents page. These enhancements are:
- The Triggered Recipients column is added to the Incident table for incidents of Source DLP type Email. Triggered recipients are those recipients who took actions that triggered rules on which some action was taken, such as allow and block.
- Additional columns are added to the Incident table for incidents of Source DLP type SaaS Security. The following additional columns appear:
- External Recipients: The recipients outside your organization who received the email that caused the incident.
- Internal Recipients: The recipients within your organization who received the email that caused the incident.
- In the Filters window, the External Recipients attribute, Internal Recipients attribute, and Triggered Recipients attribute are also added as filter options.
In addition, on the Account Settings page or the Admin Assignment page, if you choose to obfuscate the Recipient Email attribute, the obfuscation applies to the External Recipients attribute, the Internal Recipients attribute, and the Triggered Recipients attribute.
[See image.](#managing-incidents-recipient-emails)
To learn more, see [Managing Incidents](/workflow-automation/managing-incidents), [Using Incident Filters in Workflow Automation](/workflow-automation/using-incident-filters-workflow-automation), [Managing Account Settings](/workflow-automation/managing-account-settings), and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
Enhancement to the Export Incident File
On the Incidents page, you can export incidents to a downloadable file. You can then download it as a CSV file to your local system. The following additional columns appear in the file:
- External Recipients: The recipients outside your organization who received the email that caused the incident.
- Internal Recipients: The recipients within your organization who received the email that caused the incident.
- Triggered Recipients: The recipients who took actions that triggered rules on which some action was taken, such as allow and block.
[See image.](#export-incident-process)
To learn more, see [Managing Incidents](/workflow-automation/managing-incidents) and [Managing Downloads](/workflow-automation/managing-downloads).
Enhancements to the Incident Details Page
A couple of enhancements were made to the Incident Details page. These enhancements are:
-
The Policy subsection in the Violation Details section is redesigned to contain a Triggered Engines and Dictionaries heading and a Non-Triggered Engines and Dictionaries heading. If you expand the Triggered Engines and Dictionaries heading, the Engines field and Dictionaries with Match Count field appear, displaying the engines and dictionaries that are assigned to the rule that caused the incident. If you expand the Non-Triggered Engines and Dictionaries heading, the Engines field and Dictionaries with Match Count field appear, displaying the engines and dictionaries that are not assigned to the rule that caused the incident.
[See image.](#incident-details-policy-subsection)
-
The Policy window in the Files section is redesigned to contain a Triggered Engines and Dictionaries heading and a Non-Triggered Engines and Dictionaries heading. If you expand the Triggered Engines and Dictionaries heading, the Engines field and Dictionaries with Match Count field appear, displaying the engines and dictionaries that are assigned to the file that caused the incident. If you expand the Non-Triggered Engines and Dictionaries heading, the Engines field and Dictionaries with Match Count field appear, displaying the engines and dictionaries that are not assigned to the file that caused the incident.
[See image.](#incident-details-policy-window)
To learn more, see [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).
[]![Viewing the Workflows page with the Add Custom Workflow button highlighted at the top of the page..](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Workflows-Page-Add-Custom-Workflow-Button.png)
![Viewing a published custom  workflow example on the custom workflow builder page.  The custom workflows has a few Notify tiles and one Close Incident tile. ](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Custom-Workflow-Builder-Page-Published-Custom-Workflow.png)
[]![Viewing the Incidents page with the Triggered Recipients column, the Internal Recipients column, and the External Recipients columns highlighted in the Incidents table.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incidents-Page-Recipient-Emails.png)
![Viewing the Filters window with the External Recipients filter, the Internal Recipients filter, and the Triggered Incidents filter highlighted.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Filters-Window-Email-Recipients.png)
[]![Viewing the Incidents page with the Export icon highlighted](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incidents-Page-Export-Icon-Highligted.png)
![Viewing the CSV file in Microsoft Excel](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Export-Incidents-CSV-File.png)
[]![Viewing the violation details for an incident on the Incident Details page. The Policy subsection is highlighted to show the Triggered Engines and Dictionaries heading and its content, and the Non-Triggered Engines and Dictionaries heading and its content. ](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incident-Details-Page-Policy-Subsection.png)
[]![Viewing the Policy window in the Files section of the Incident Details page. The Triggered Engines and Dictionaries heading is highlighted and the Non-Triggered Engines and Dictionaries heading is highlighted.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incident-Details-Page-Files-Section-Policy-Window.png)

## November 06, 2025
### Feature Available
#### Enhancement to the Add Admin Assignment Window
On the Add Admin Assignment window in the Data Protection integration, you have the option to override your organization's data privacy settings when adding the admin assignments for an individual admin. To override the settings, enable or disable the Hide Evidence Data setting (formerly Evidence Data Privacy) and the Hide Trigger Data setting (formerly Trigger Data Privacy) on the window. These settings are now grouped and repositioned to a new Data Privacy Settings section in this window. The names of these settings are updated for clarity.
[See image.](#add-admin-assignment-window)
To learn more, see [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
[]![Viewing the Data Privacy Settings section in the Add Admin Assignment window before overriding. The Override link is highlighted in this section.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Add-Admin-Assignment-Window-Data-Privacy-Section-Before-Override.png)
![Viewing the Data Privacy Settings section on the Add Admin Assignment window after overriding. The Hide Evidence Data setting and Hide Trigger Data setting are available. Plus, the Reset link is highlighted in this section.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Add-Admin-Assignment-Window-Data-Privacy-Section-After-Override.png)

## October 23, 2025
### Feature Available
#### Enhancement to the Incidents Page
On the Incidents page in the Data Protection integration, additional columns are added to the incident table for incidents of Source DLP type SaaS Security. The following additional columns appear:
- **External Collaborators Groups**: The collaborator groups outside your organization for the incident.
- **File Link Expiry**: The date and time when the file link expires.
- **File Modified By**: The email address of the user who last modified the file.
- **File Shared By**: The email address of the user who shared the file.
- **File Shared At**: The date and time when the file was shared.
In addition, in the Filters window, the External Collaborators Groups attribute, File Modified By attribute, and File Shared By attribute are also added as filter options.
[See image.](#enhancement-incidents-page)
To learn more, see [Managing Incidents](/workflow-automation/managing-incidents) and [Using Incident Filters in Workflow Automation](/workflow-automation/using-incident-filters-workflow-automation).
[]![Viewing the Incidents page with the following columns highlighted in the incidents table: External Collaborators Groups, File Link Expiry, File Modified By, File Shared By, and File Shared At.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Incidents-Page-Saassecurity-attributes.png)
![Viewing the Filters window with the following filter options highlighted: External Collaborators Groups, File Modified By, and File Shared By.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Filters-Window-Saassecurity-attributes.png)

## October 13, 2025
### Feature Available
#### Enhancements to Data Protection Features
The following are enhancements to the Data Protection features in Workflow Automation:
Enhancement to Audit Logs
Workflow Automation creates audit logs when you update an incident group mapping on the Incident Group Mapping page, and when you update a workflow mapping on the Workflow Mappings page. You can view these audit logs on the Audit Logs page.
[See image.](#Enhancement-Audit-Logs)
To learn more, see [Managing Workflow Mappings](/workflow-automation/managing-workflow-mappings), [Managing Incident Group Mappings](/workflow-automation/managing-incident-group-mappings), and [About Audit Logs](/workflow-automation/about-audit-logs).
Enhancement to Incidents of Source DLP Type SaaS Security
On the Incident Details page, in a few different sections, additional attributes appear for an incident of Source DLP type SaaS Security. The following additional attributes appear:
- Current Tag Name: The name of the tag currently assigned to the application.
- Is Copilot Accessible: Indicates whether Copilot can access the application. Values are Yes or No.
- Internal Collaborators Groups: The collaborator groups inside your organization for the incident.
- External Collaborators Groups: The collaborator groups outside your organization for the incident.
- Document Sub Type: The document subtype for the file.
[See image.](#enhancements-saassecurity-sourcedlptype)
To learn more, see [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).
Enhancements to Incident Group Mappings and Workflow Mappings
On the Incident Group Mapping page, you can map an incident group to one or more properties, and on the Workflow Mappings page, you can map a workflow to one or more properties. The following is a list of properties added for incidents of Source DLP type SaaS Security that you can use to map an incident group or workflow:
- Current Tag Name
- Is Copilot Accessible
- External Groups Collaborators
- Internal Groups Collaborators
- Document Sub Type
- File Line Expiry
- File Modified By
- File Shared At
- File Shared By
The same properties are available when mapping an incident group as when mapping a workflow. The following images show the properties when mapping an incident group.
[See image.](#incident-group-workflow-mapping)
To learn more, see [Managing Incident Group Mappings](/workflow-automation/managing-incident-group-mappings) and [Managing Workflow Mappings](/workflow-automation/managing-workflow-mappings).
Enhancement to Time Range
On the Incidents page and the Incident Analytics dashboard, you select a time range for what incident information to display on the page or dashboard. The time range field is enhanced to include the following hour options:
- Current Hour
- Last Hour
- Last 2 Hours
- Last 6 Hours
- Last 12 Hours
[See image.](#date-range)
To learn more, see [Managing Incidents](/workflow-automation/managing-incidents) and [About the Incident Analytics Dashboard](/workflow-automation/about-incident-analytics-dashboard).
Enhancement to the Filters Window
On the Incidents page and the Incident Analytics dashboard, you can use filters to modify the incident data that is displayed. The Filters window is enhanced to enable you to select or enter the filter values to include or exclude.
[See image.](#filters-window-include-exclude)
To learn more, see [Using Incident Filters in Workflow Automation](/workflow-automation/using-incident-filters-workflow-automation), [Managing Incidents](/workflow-automation/managing-incidents), and [About the Incident Analytics Dashboard](/workflow-automation/about-incident-analytics-dashboard).
Enhancement to the Incidents Page and Incident Details Page
On the Incidents page, a new System Creation Date column is added to the incident table. The System Creation Date displays the date and time when the incident was created in the system. The System Creation Date field is also added to the Incident Details page in the Overview section for the incident.
[See image.](#enhancement-incident-page-system-creation-date)
To learn more, see [Managing Incidents](/workflow-automation/managing-incidents) and [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).
Filter Incidents by Clickable Name Link
On the Incidents page, the Username field appears for each incident in the Incidents table, and on the Incident Analytics dashboard, the User Email field appears for each user in the Top 10 Users section. The Username field and User Email field are enhanced to be clickable links. When you click these links, you are redirected to the Incidents page, which displays only the incidents created by the same end user. The user filter is automatically applied in the Filters section.
[See image.](#clickable-name-link)
To learn more, see [Managing Incidents](/workflow-automation/managing-incidents) and [About the Incident Analytics Dashboard](/workflow-automation/about-incident-analytics-dashboard).
[]![Viewing the Audit Logs page. The Workflow Definition Mapping audit log and Incident Group Mapping audit logs are highlighted. ](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Audit-Logs-Page-Update-Incident-Workflow-Mappings.png)
[]![Viewing the Violation Details section on the Incident Details page for an Incident of Source DLP Type SaaS Security. In the Application sub-section, the Current Tag Name and Is Copilot Accessible fields are highlighted. ](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Incident-Details-PG-Violation-Details-SaaSSecurity-Application.png)
![Viewing the Collaborators section on the Incident Details page for an Incident of Source DLP Type SaaS Security. In the Collaborators section, the Internal Collaborators Groups and External Collaborators Groups fields are highlighted. ](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Incident-Details-PG-Collaborators-SaaSSecurity1.png)
![Viewing the Attachments section on the Incident Details page for an Incident of Source DLP Type SaaS Security. In the Attachments section, the Document Sub Type field is highlighted. ](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Incident-Details-PG-Attachments-SaaSSecurity.png)
[]![Viewing the Property field on the Incident Group Mapping page. The Application Info properties for Current Tag Name and Is Copilot Accessible are highlighted.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Incident-Group-Mapping-Application-Attributes1.png)
![Viewing the Property field on the Incident Group Mapping page. The Content Info > Additional Info properties for External Groups Collaborators and Internal Groups Collaborators are highlighted.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Incident-Group-Mapping-Collaborator-Attributes.png)
![Viewing the Property field on the Incident Group Mapping page. The Content Info > Attachments property for Document Sub Type is highlighted.  ](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Incident-Group-Mapping-Attachment-Attributes.png)
![Viewing the Property field on the Incident Group Mapping page. The Content Info properties for File Link Expiry, File Modified By, File Shared At, and File Shared By are highlighted. ](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Incident-Group-Mapping-Content-Info-Attributes1.png)
[]![Viewing the available time range options on the Incidents page. The hour options are highlighted. Hour options are Current Hour, Last Hour, Last 2 Hours, Last 6 Hours, and Last 12 Hours.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Incidents-Page-Date-Range.png)
![Viewing the available time range options on the Incident Analytics dashboard. The hour options are highlighted. Hour options are Current Hour, Last Hour, Last 2 Hours, Last 6 Hours, and Last 12 Hours. ](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Incident-Analytics-Dashboard-Date-Range.png)
[]![Viewing the Filters window with the Include and Exclude headings highlighted for the Department filter.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Filters-Window-Include-Exclude.png)
[]![Viewing the Incidents page with the System Creation Date column highlighted on the Incidents table.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Incidents-Page-System-Creation-Date-Column.png)
![Viewing the Overview section on the Incident Details page. The System Creation Date field is highlighted on this section.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Incident-Details-PG-System-Creation-Date.png)
[]![Viewing the Incidents page with the Username column highlighted. The Username field is a clickable link.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Incidents-Page-Username-Column.png)
![Viewing the Top 10 Users section on the Incident Analytics dashboard with the User Email column highlighted. The User Email field is a clickable link. ](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Incident-Analytics-DB-Top-10-Users-User-Email-Link.png)

## September 25, 2025
### Feature Available
#### Enhancements to Data Protection Features
The following are enhancements to the Data Protection features in Workflow Automation:
Filter Incidents of Source DLP Type Endpoint by Channel
On the Incidents page, a new Channel column is added to the Incidents table, and the Channel attribute is added as a filter in the Filters window. Using the Filters window, you can filter the incidents of Source DLP type Endpoint by channel.
[See image.](#filter-incidents-channel)
To learn more, see [Using Incident Filters in Workflow Automation](/workflow-automation/using-incident-filters-workflow-automation) and [Managing Incidents](/workflow-automation/managing-incidents).
Enhancement to Incidents of Source DLP Type SaaS Security
On the Incident Details page, in the Violation Details section, additional attributes appear for an incident of Source DLP type SaaS Security. The following is a list of the additional attributes that appear:
- File Shared By: The email address of the user who shared the file.
- File Shared At: The date and time the file was shared
- File Modified By: The email address of the user who modified the file.
- File Link Expiry: The date and time the file link expires.
[See image.](#enhancement-incident-saassecurity)
To learn more, see [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).
Support for Sort Order when Exporting Incidents to a CSV File
On the Incidents page, you can sort the column data for the incidents that appear on the page by clicking the Sort icon next to the column headings that have these Sort icons. If you export incidents to a CSV file after you have sorted the columns, the CSV file is generated with the incidents listed in that sort order.
[See image.](#support-order-export-incidents)
To learn more, see [Managing Incidents](/workflow-automation/managing-incidents) and [Using Tables in Workflow Automation](/workflow-automation/using-tables-workflow-automation).
Support for DLP Application Integration with GCP
Workflow Automation now supports Data Loss Prevention (DLP) application integration with Google Cloud Platform (GCP). This integration enables your organization to forward DLP policy violations to your Google Cloud storage buckets via the Cloud-to-Cloud Incident Forwarding method. You can manage the DLP GCP application integrations on the Setup > Integrations page in the Workflow Automation Admin Portal.
[See image.](#RN-DLP-GCP-app)
To learn more, see [Configuring the DLP Application Integration Using Google Cloud Platform](/workflow-automation/configuring-dlp-application-integration-using-google-cloud-platform) and [Managing DLP GCP Application Integrations in Workflow Automation](/workflow-automation/managing-dlp-gcp-application-integrations-workflow-automation).
[]![Viewing the Incidents Page with the Channel Column Highlighted in the Incidents Table. The Channel Column Only Appears for Incidents of Source DLP Type Endpoint.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Incidents-PG-Channel-Column.png)
![Viewing the Filters Window on the Incidents Page with the Channel filter highlighted. The Channel filter displays all the channels for Incidents with a Source DLP Type of Endpoint.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Filters-Window-Channel.png)
[]![Viewing the Violation Details Section of the Incident Details Page for an Incident of Source DLP Type SaaS Security. In the Content subsection, the File Shared By, File Shared At, File Modified By, and File Link Expiry Attributes are highlighted. ](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Incident-Details-PG-Additional-Attributes-SaaS-Security.png)
![Image]()
[]![Viewing the Incidents Page with Multiple Incidents Displayed.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Incidents-PG-Incidents-Not-Sorted.png)
![Viewing the Incidents Page with the Incidents Sorted by Severity. The Transactions ID and Severity Fields, and the Export Icon are highlighted.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Incidents-PG-Incidents-Sorted.png)
![Viewing the CSV File Generated by Exporting the Incidents on the Incidents Page. The CSV File Displays All the Incident columns for the Incidents from the Incidents Page.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-Release-Note-Incidents-CSV-Export-File.png)
![The Zscaler DLP GCP Integration application on the Setup > Integrations page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-DLP-GCP-application-integration-tile-view.png)
[]

## August 28, 2025
### Feature Available
#### Enhancement to the Incidents Analytics Dashboard
A new widget, All, is added to the Incident Analytics dashboard. This widget displays the total number of incidents that have occurred in your organization.
[See image.](#RN-all-widget)
To learn more, see [About the Incident Analytics Dashboard](/workflow-automation/about-incident-analytics-dashboard).
![All widget in the Incident Analytics dashboard in the Workflow Automation Admin Portal](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-incident-analytics-dashboard-all-widget.png)
[]

## August 14, 2025
### Feature Available
#### Enhancements for Data Protection Features
The following are enhancements to the Data Protection features in Workflow Automation:
Support for Cloud-to-Cloud Forwarding in DLP Application Integration
Workflow Automation Data Loss Prevention (DLP) Application integration with Amazon Web Services (AWS) and Microsoft Azure now supports Cloud-to-Cloud Incident Forwarding for DLP policy violations. Configuring Cloud-to-Cloud Forwarding with your AWS and Azure accounts allows your organization to send DLP incident metadata and evidence files to your organization's AWS S3 storage buckets and Azure storage containers without deploying appliances.
You can enable Cloud-to-Cloud Forwarding for your organization on the DLP Policy page in the ZIA Admin Portal.
To learn more, see [Configuring the DLP Application Integration Using Azure](/workflow-automation/configuring-dlp-application-integration-using-azure) and [Configuring the DLP Application Integration Using Amazon Web Services](/workflow-automation/configuring-dlp-application-integration-using-amazon-web-services).
Enhancement to the Incidents Dashboard Page
The following new widgets are added to the Incident Dashboard Page:
- **Top 10 Incidents by Rule**: Displays the top 10 DLP rule violations with the number of incidents generated against that specific rule.
- **Top 10 Incidents by Dictionary**: Displays the top 10 DLP dictionary violations with the number of incidents generated against that specific dictionary.
- **Top 10 Users**: Displays the top 10 end users with the most incidents associated with them. This table provides details such as the email ID, the total number of incidents, number of critical priority incidents, etc., associated with the end user.
[See image.](#RN-incidents-dashboard)
To learn more, see [About the Incident Analytics Dashboard](/workflow-automation/about-incident-analytics-dashboard).
[]
![The Top 10 Incidents by Rule widget on the Incidents Dashboard page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-about-incidents-dashboard-top-10-incidents-rules.png)
![The Top 10 Incidents by Dictionary widget on the Incidents Dashboard page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-about-incidents-dashboard-top-10-incidents-dictionaries.png)
![The Top 10 Users table in the Incident Dashboard page ](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-about-incidents-dashboard-top-10-users.png)

## July 31, 2025
### Feature Available
#### Enhancement to the Workflow Automation Admin Portal
A window, What's New?, now appears whenever an admin logs in to the Workflow Automation Admin Portal. This window highlights the latest feature releases, including new functionalities, fixes, and improvements. Admins have the option to permanently disable this window if it is not required.
[See image.](#RN-whats-new)
![What's New window in the Workflow Automation Admin Portal](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-What's-New-feature.png)
[]

### Feature Available
#### Enhancements for Data Protection Features
The following are enhancements to the Data Protection features in Workflow Automation:
Enhancement to Notification Templates
On the Notification Templates page, a new Subject Line field is available when you add, edit, or clone an email template. This field allows you to enter a subject or a short description for the notification template.
This field is only available for email notification templates and supports content in English.
[See image.](#RN-subject-line-notification-templates)
To learn more, see [Managing Notification Templates](/workflow-automation/managing-notification-templates) and [Adding Email Notification Templates](/workflow-automation/adding-email-notification-templates).
Enhancement to the Incidents Page
On the Incidents page, two new options, Add and Remove, are available when performing label actions or bulk action against the incidents available on the Incident table. You can use these options to add a new label to the incident or remove an existing label from an incident.
[See image.](#RN-add-remove-label-button)
To learn more, see [Managing Incidents](/workflow-automation/managing-incidents).
Enhancement to Incident Group Mappings and Workflow Mappings
A new Other Email Recipients property is added to the Email Source DLP Type property list. This field allows you to enter the recipient’s email address as a property value when configuring incident group mappings and workflow mappings.
[See image.](#RN-other-email-recipients-property)
To learn more, see [Managing Workflow Mappings](/workflow-automation/managing-workflow-mappings) and [Managing Incident Group Mappings](/workflow-automation/managing-incident-group-mappings).
![Subject Line field in the Notifications Templates page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-notification-templates-subject-line.png)
[]
![Add or Remove buttons for adding and removing labels for incidents](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-managing-incidents-labels-add-remove-options.png)
[]
![Email Source DLP type > Other Email Recipients property for Incident Group and Workflow Mappings](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-incident-workflow-mappings-other-email-recipients-property.png)
[]

## July 17, 2025
### Feature Available
#### Enhancements to Account Settings
On the Account Settings page in the Data Protection integration, a new Restrict Approver Email Domains option is added under the Approvers Domain Management section. This option allows you to add a maximum of 10 trusted email domains to restrict who can be set as approvers. On the [Approvers](/workflow-automation/managing-approvers) page, admins can only add approver email addresses that belong to one of the specified domains.
[See image.](#RN-approver-domain-managament)
To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
![Restrict Approver Email Domains on the Account Settings page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-managing-account-settings-approver-domain-management.png)
[]

## June 20, 2025
### Feature Available
#### Configurable User Digest Notification Frequency
On the Account Settings page in the Data Protection integration, you can select the frequency at which user digest notifications are generated for your organization. Frequencies are Hourly, Daily, or Weekly. The default is daily.
[See image.](#user-digest-frequency)
To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
[]![Viewing Digest Notification settings on the Account Settings page. The Digest Frequency drop-down menu is highlighted for End User digest notifications. ](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Account-Settings-Page-User-Digest-Notification-Frequency.png)

## June 05, 2025
### Feature Available
#### Enhancements to Data Protection Features
The following are enhancements to the Data Protection features in Workflow Automation:
Enhancement to Viewing Incidents on the Incidents Page
On the Incidents page, the incidents that have occurred for your organization appear in a table. This table displays multiple columns with headings for each incident. The table column headings are always visible (i.e., frozen) when scrolling through multiple pages of incidents.
[See image.](#Incidents-Page-Frozen-Header)
To learn more, see [Managing Incidents](/workflow-automation/managing-incidents).
Modifications to Incident Sorting on the Incidents Page
On the Incidents page, you can sort the incidents that appear in the table across all the pages by clicking the Sort icon in one of the attribute column headings. The following modifications are made to incident sorting:
- The Sort icon is removed from several of the attribute column headings. You can sort the incidents by any attribute column in the table except for the following attribute columns:
- Transaction ID
- Last Change Date
- Source DLP Type
- Labels
- Status
- Engine
- Dictionary
- Rule
- Dictionary Match Count
- Action
- Last Change
- Incident Groups
- Justification Reason
- Justification Note
- Username
- Client IP
- File MD5
- Home Location
- Work Location
- File Source Location
- File Modification Time
- Resolution Date
- Integration
- If you click the Sort icon in an attribute column heading in the table, the column's data is sorted for all the incidents across all the pages. You can only sort by one attribute column at a time. For example, if you sort by the DLP Admin column, all the pages are sorted by that column. If you next sort by the Source DLP Type column, the sorting for DLP Admin goes away and all the pages are sorted by Source DLP Type.
[See image.](#incidents-page-table-sorting)
To learn more, see [Using Tables in Workflow Automation](/workflow-automation/using-tables-workflow-automation) and [Managing Incidents](/workflow-automation/managing-incidents).
[]![Viewing the Incidents page when the table column headings are frozen for the Incidents table. The Incidents page with a table containing columns for Transaction ID, Last Change Date, Priority, Severity, DLP Admin, Source DLP Type, and DLP Type. The table heading is highlighted.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incidents-Page-Frozen-Header.png)
[]![Viewing the Incidents page with the incident table column heading highlighted. The Sort icon is also highlighted next to the Priority, Severity, DLP Admin, and Source DLP Type column headings.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incidents-Page-Table-Sorting_0.png)

## May 08, 2025
### Feature Available
#### Enhancements to DLP Incident Filters
On the Incidents page in the Data Protection Integration, you can use filters to determine which incidents appear on the Incidents page. Using the Filters window, you can choose the Data Loss Prevention (DLP) incident filters and enter the values for these filters. Some of the filters contain predefined values, and some of the filters require you to enter a text string value. The following is a list of enhancements made to the filters that require you to enter a text string value:
- None of the text string values that you enter for a filter are case sensitive.
- For the Referrer URL filter and the URL filter, you can enter a complete URL (e.g., https://www.jumpshare.com/https-post), or you can enter a complete host name (e.g., www.jumpshare.com) for the URL.
- You can enter multiple strings within a single text string value. If you enter multiple strings within a text string value, each string value is treated with an AND operation. For example, if you select the Application Name filter and enter Microsoft Office as the text string value, all incidents with the application name containing Microsoft and Office are returned with this filter, such as Microsoft Office, Microsoft Office 365, and Office 365 Microsoft. This filter does not return incidents with an application name containing only Microsoft or Office.
[See image.](#incident-filters)
To learn more, see [Using Incident Filters in Workflow Automation](/workflow-automation/using-incident-filters-workflow-automation) and [Managing Incidents](/workflow-automation/managing-incidents).
[]![Viewing the Incidents page with the Application Name column highlighted. This column is displaying application names for Microsoft Outlook, Thunderbird, Microsoft 365, Gmail, and Thunderbird. ](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incidents-Page-Before-Filter.png)
![Viewing the Filters window with the Application Name filter entered. The Application Name filter value contains microsoft outlook,Gmail. Microsoft Outlook is not capitalized.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Filters-Window-Application-Name.png)
![Viewing the Incidents page with the Application Name column highlighted after the filter is applied. This column is displaying only Gmail and Microsoft Outlook application names.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incidents-Page-After-Filter.png)
![Viewing the Incidents page with the Destination column highlighted. This column is displaying destination URLs for www.box.com/upload, www.dropsend.com/upload, www.dropbox.com/upload, www.hightail.com/upload, www.googledrive.com/upload, www.zippyshare.com/upload, and www.microsoftonedrive.com/upload.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incidents-Page-Before-Filter-URL.png)
![Viewing the Filters window with the URL filter entered. The URL filter value contains only the domain name of www.box.com.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Filters-Window-URL-Filter.png)
![Viewing the Incidents page with the Destination column highlighted after the URL filter is applied. This column is displaying only www.box.com/upload destinations.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incidents-Page-After-Filter-URL.png)

## April 24, 2025
### Feature Available
#### Enhancements to Data Protection Features
The following are enhancements to the Data Protection features in Workflow Automation:
Enhancement to Incident Filters
On the Incidents page, you can filter the incidents that appear on the page. In the Filters window, for filters with predefined values (e.g., Dictionary and Department), a Select All checkbox is added. When you select this checkbox, all the filter values are selected at once for the filter.
[See image.](#select-all-incident-filter)
To learn more, see [Using Incident Filters in Workflow Automation](/workflow-automation/using-incident-filters-workflow-automation).
Enhancements to the Incidents Page
On the Incidents page, a new Unassigned widget is added. When you click this widget, all the incidents that have not been assigned to a DLP admin are displayed. You can also filter for unassigned incidents on the Incidents page by using the Filters window and selecting Unassigned as the filter value for the DLP Admin filter.
[See image.](#unassigned-incidents)
To learn more, see [Managing Incidents](/workflow-automation/managing-incidents).
Configurable Expiration Periods for Justification Links on Notifications
On the Account Settings page, you can configure the expiration periods for the justification links that appear for the recipients in the user, escalation, user digest, and DLP admin digest notifications that Workflow Automation generates. A new Notifications section is added to the page, and that section has an End User Notifications tab and a Digest Notification tab. In these tabs, you can use the Expiration period fields that are added to configure the expiration periods for the different notifications.
[See image.](#notifications-section)
To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings), [Responding to an End User Notification](/workflow-automation/responding-end-user-notification), [Responding to an Escalation Notification](/workflow-automation/responding-escalation-notification), [Responding to a User Digest Notification](/workflow-automation/responding-user-digest-notification), and [Responding to a DLP Admin Digest Notification](/workflow-automation/responding-dlp-admin-digest-notification).
Enhancement to Custom Email Domains
When configuring a custom email domain in the Custom Email Domain Setup wizard, the following enhancements are made:
- On the Add Custom Domain page (first step), a new Envelope Sender Domain Name field is added, which enables you to configure the envelope sender domain. Configuring this domain improves email deliverability, helps with Sender Policy Framework (SPF) alignment, and ensures a consistent sending identity for your notifications.
- On the Add DNS Record page (second step), to support you with configuring the envelope sender domain, additional DNS records are displayed in the table that Workflow Automation generates. You must publish these additional DNS records in your DNS provider to complete the configuration.
[See image.](#custom-email-domains)
To learn more, see [Managing Custom Email Domains](/workflow-automation/managing-custom-email-domains).
[]![Viewing the Filters window with the Select All checkbox selected for the filter values for the Dictionary filter.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Filters-Window-Select-All.png)
[]![Viewing the Incidents page with the Unassigned widget highlighted](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incidents-PG-Unassigned.png)
![Viewing the Filters window with the DLP Admin filter selected and the Unassigned filter value highlighted](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Filters-Window-Unassigned.png)
[]![Viewing the fields in the End User Notifications tab on the Account Settings page. This tab contains Expiration period fields for the justification links on the user and escalation (manager and approver) notifications.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Accounting-Settings-PG-Notifications-End-User.png)
![Viewing the fields in the Digest Notifications tab on the Account Settings page. This tab contains the channels (email, Slack, and Teams) that you can enable for a user digest notification and a DLP admin digest notification. Plus, it contains Expiration period fields for the justification links on the user digest and DLP admin digest notifications.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Accounting-Settings-PG-Notifications-Digest.png)
[]![Viewing the Add Custom Domain page with the new Envelope Sender Domain Name field highlighted. This page has the Domain Name field, the Envelope Sender Domain Name field, and the Originating Email Address field.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Add-Custom-Domain-Page-Envelope-Sender-Domain-Name.png)
![Viewing the Add DNS Record page with the additional DNS records to support the configuration of the envelope sender domain highlighted. The page contains a table that lists all the DNS records you need to publish in your DNS provider to add a custom email domain.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Add-DNS-Record-Page-Additional-DNS-Records.png)

## April 10, 2025
### Feature Available
#### Enhancements to Data Protection Features
The following are enhancements to the Data Protection features in Workflow Automation:
Support for Managing Incidents Across Multiple ZIA Tenants in a Single Workflow Automation Account
In the Workflow Automation Admin Portal, you can manage the incidents that occur across multiple Zscaler Internet Access (ZIA) tenants in a single Workflow Automation account. On the Incidents page, you can view and remediate all the incidents that have occurred across all of your ZIA tenants (i.e., Data Loss Prevention (DLP) application integrations) in one location. To support this feature, the following changes are made:
- On the Incidents page:
- The Integration column is added to the table that lists all the incidents. This column displays the names of the DLP application integrations where the incidents occurred.
- The Integration field is added as a filter in the Filters window. Using the Filters window, you can filter the incidents that appear on the page by DLP application integration.
- When you export incidents, the Integration field displays in the download file.
- On the Incident Details page, in the Overview section, the Integration field is added for an incident. This field displays the name of the DLP application integration where the incident occurred.
- On the Incident Analytics page, the Integration field is added as a filter in the Filters window. Using the Filters window, you can filter the information that appears on the page by DLP application integration.
[See image.](#multiple-tenants)
To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services](/workflow-automation/configuring-dlp-application-integration-using-amazon-web-services), [Configuring the DLP Application Integration Using Azure](/workflow-automation/configuring-dlp-application-integration-using-azure), [Managing Incidents](/workflow-automation/managing-incidents), [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details), [Using Incident Filters in Workflow Automation](/workflow-automation/using-incident-filters-workflow-automation), and [About the Incident Analytics Dashboard](/workflow-automation/about-incident-analytics-dashboard).
Enhancement to Transaction ID Search
On the Incidents page, you can search for one or more incidents using their Transaction IDs. To search for multiple incidents, enter the transaction IDs separated by a comma. You can search for up to 10 incidents.
[See image.](#transaction-id-search)
To learn more, see [Managing Incidents](/workflow-automation/managing-incidents).
Enhancement to Incident Detail Information
On the Incidents and Incident Details pages, a Resolution Date field is added. This field displays the date and time when the incident was resolved using the Close Incident action. It only appears for resolved (i.e., closed) incidents.
The Resolution Date field is also added to the Overview section for a resolved incident on user, escalation, and user digest notifications.
[See image.](#resolution-date)
To learn more, see [Managing Incidents](/workflow-automation/managing-incidents), [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details), [Responding to an End User Notification](/workflow-automation/responding-end-user-notification), [Responding to an Escalation Notification](/workflow-automation/responding-escalation-notification), and [Responding to a User Digest Notification](/workflow-automation/responding-user-digest-notification).
[]![Incidents page showing the Transaction ID search field populated with transaction IDs](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incidents-PG-Transaction-ID-Search.png)
[]![Viewing the Incidents page with the incidents table displaying the last columns (Transaction ID, File Size, File Modification Time, Document Type, Integration, and Resolution Date) in the incidents table. The Resolution Date column is highlighted.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incidents-PG-Resolution-Date-Col.png)
![Viewing the Resolution Date field for an incident on the Incident Details page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incident-Details-PG-Resolution-Date.png)
![Viewing the Resolution Date field for an incident on the Incident page from a user notification](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-User-Notification-Resolution-Date.png)
[]![Viewing the Incidents page with the incidents table displaying the last columns (Transaction ID, File Size, File Modification Time, Document Type, Integration, and Resolution Date) in the incidents table. The Integration column is highlighted.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incidents-PG-Integration-Column.png)
![Viewing the Filters window on the Incidents page with the Integration field highlighted](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incidents-PG-Filters-Window-Integration.png)
![Viewing the Integration field in the Overview section on the Incident Details page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incident-Details-PG-Integration-Field.png)
![Viewing the Filters window on the Incident Analytics page with the Integration field highlighted](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incident-Analytics-PG-Filters-Window-Integration-Field.png)

## March 31, 2025
### Feature Available
#### Enhancements to Data Protection Features
The following are enhancements to the Data Protection features in Workflow Automation:
Modification to the System Default Escalation Survey Template
Workflow Automation provides a system default survey template (Escalation - Questionnaire Template) that you can use for your escalation notifications. A new justification type of Manager Rejected is added to this template. You can view the design and details of this template on the Survey Template page.
[See image.](#system-default-survey-templates)
To learn more, see [Managing Survey Templates](/workflow-automation/managing-survey-templates) and [Responding to an Escalation Notification](/workflow-automation/responding-escalation-notification).
Enhancement to the Incidents and Incident Details Pages
The Update Incident Group action is added to the Incidents and Incident Details pages. When you select this action on the Incident Details page, the Update Incident Group window appears. In the Update Incident Group window, you can add and delete incident groups assigned to the incident. You also have the option to select a different incident group to use for the admin assignment of the incident. When you select this action on the Incidents page, the Update Incident Group window appears. In the Update Incident Group window, you can add and delete incident groups assigned to multiple incidents that you selected on the Incidents page. You can also select a different incident group to use for the admin assignment of the incidents, and you can select a default incident group for those incidents that might become unassigned after you delete an assigned incident group.
The following images show the Update Incident Group window accessed from the Incidents and Incident Details pages.
[See image.](#update-incident-group-windows)
To learn more, see [Managing Incidents](/workflow-automation/managing-incidents), [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details), and [Managing Bulk Actions](/workflow-automation/managing-bulk-actions).
Viewing the Incident Details Page for Multiple Incidents
You can view the Incident Details page for one or more incidents in separate tabs in the same browser window. To view the Incident Details page for an incident in a separate tab, right-click the Transaction ID of an incident on the Incidents page, and select Open in New Tab. In the new tab, the Incident Details page appears, displaying detailed information for the incident.
[See image.](#incident-details-page-separate-tabs)
To learn more, see [Managing Incidents](/workflow-automation/managing-incidents).
[]![Viewing the system default Escalation - Questionnaire Template on the Survey Template page. The template contains the Justification Type field along with its values (False Positive, Manager Approved, Manager Rejected, and Others), and the Justification Reason field.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Survey-Templates-PG-Manager-Rejected-Justification-Type.png)
[]![Viewing the Update Incident Group window accessed by selecting the Update Incident Group action on the Incidents page ](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Update-Incident-Group-Window-Incidents-PG.png)
![Viewing the Update Incident Group window accessed by selecting the Update Incident Group action on the Incident Details page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Update-Incident-Group-Window-Incident-Details-PG.png)
[]![Viewing the Incidents page with the Open in New Tab option displayed for an incident ](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incidents-Page-Open-In-New-Tab.png)
![Viewing the Incident Details page after Open in New Tab is selected for an incident on the Incidents page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incident-Details-Page-Open-In-New-Tab.png)

## March 11, 2025
### Feature Available
#### Enhancements to Data Protection Features
The following are enhancements to the Data Protection features in Workflow Automation:
Modification to the Close Incident Action
In the Close Incident window, which you access by selecting the Close Incident action on the Incidents page or the Incident Details page, you must enter a resolution label to close the incident.
[See image.](#close-incident-window)
To learn more, see [About Incidents](/workflow-automation/about-incidents) and [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).
Enhancement to Table Column Sort Settings
On the Incidents page, the incidents that have occurred in your organization display in a table. Using the column sort settings for the table, you can modify how the incidents are sorted and displayed in this table. These column sort settings are saved in local storage, allowing them to persist within the same browser, but they won't carry over to different devices and browsers. They are saved for each user. If you have multiple users sharing the same browser, then each user's settings are stored separately. In addition, these column sort settings stay with the users even if they refresh the page or if they log out of the Workflow Automation Admin Portal and log back in again.
[See image.](#incidents-page-column-sort-settings)
To learn more, see [Using Tables in Workflow Automation](/workflow-automation/using-tables-workflow-automation).
Enhancement to Custom Email Domains
A DNS record verification process is added to the Custom Email Domain functionality. When adding a custom email domain using the Custom Email Domain Setup wizard, Workflow Automation generates the DNS records required for domain verification. These records are displayed in a table on the Add DNS Record page. You must then publish those DNS records to your DNS provider. After you publish the DNS records to the DNS provider, the DNS server calls Amazon Web Services (AWS) to check whether the records are valid. If the records are valid, the custom email domain is added. If the records are not valid, or if there is a technical issue with verifying the records, the custom email domain is not added. As a result of this new verification process, new messages are displayed on the Add DNS Record page informing you of the status of the verification process. In addition, the custom email domain statuses have changed. The custom email domain statuses are:
- DNS verification pending: Domain is pending DNS record verification.
- Expired: Domain is expired. You did not publish the DNS records to your DNS provider within the 72-hour deadline.
- Failed: Domain failed DNS record verification and was not added.
- In Use: Domain is currently being used as the originating sender domain for user notifications.
- Success: Domain passed DNS record verification and was added.
[See image.](#verification-process)
To learn more, see [Managing Custom Email Domains](/workflow-automation/managing-custom-email-domains).
[]![Viewing the Resolution Label field highlighted on the Close Incident window](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Close-Incident-Window.png)
[]![Viewing the Incidents page with the Sort icons highlighted for each column in the table](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incidents-PG-Column-Sort-Settings.png)
[]![Viewing the Add DNS Record page after the domain was successfully verified. A message appears on the page stating that the domain was successfully verified and to proceed to the next step.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Add-DNS-Record-Page-Domain-Successfully-Verified.png)
![Viewing the Add DNS Record page after the domain verification failed. A message appears on the page stating that the domain failed verification and to ensure the DNS records were accurately entered in your DNS provider..](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Add-DNS-Record-Page-Domain-Verification-Failed.png)
![Viewing the Custom Email Domain page with the Status column highlighted for each custom domain ](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Custom-Email-Domain-Page-Statuses.png)

## February 21, 2025
### Feature Available
#### Enhancement to Notification Templates
On the Notification Template page in the Data Protection integration, the Client IP tag is added to the Merge Tags drop-down menu when adding buttons, text, and headings to an email notification template. The Client IP tag is also added to the Select Merge Tags drop-down menu when adding a Slack notification template and when adding a Microsoft Teams notification template.
[See image.](#merge-tag-images)
To learn more, see [Managing Notification Templates](/workflow-automation/managing-notification-templates), [Adding Email Notification Templates](/workflow-automation/adding-email-notification-templates), [Adding Slack Notification Templates](/workflow-automation/adding-slack-notification-templates), and [Adding Microsoft Teams Notification Templates](/workflow-automation/adding-microsoft-teams-notification-templates).
[]![Viewing the available merge tags in the Merge Tags drop-down when adding text to an email notification template on the Notification Template page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Notification-Template-PG-Email-Template-Merge-Tags.png)
![Viewing the available merge tags in the Select Merge Tags drop-down when adding text to a Slack notification template on the Notification Template page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Notification-Template-PG-Slack-Template-Select-Merge-Tags.png)
![Viewing the available merge tags in the Select Merge Tags drop-down when adding text to a Teams notification template on the Notification Template page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Notification-Template-PG-Teams-Template-Select-Merge-Tags.png)

## February 03, 2025
### Feature Available
#### Enhancements to Custom Email Domains
The following are enhancements to the Custom Email Domains feature in the Data Protection integration:
-
On the Custom Email Domain page, you can revert back to the Zscaler domain (zsworkflow.net) by clicking Revert to Zscaler Domain. The status of the custom email domain that you previously selected as the default is changed from In Use to Verified. When you want to use your custom email domain again for the notifications, on the Custom Email Domain page, you can click the Make Default icon again next to your custom email domain.
[See image.](#revert-zscaler-domain)
-
On the Verify Custom Domain Setup page, when you select that you did not receive the test email, the Didn't receive an email? section appears at the bottom of the page. When you expand that section, a list of troubleshooting tips appears to assist you with correcting the issues you might have with your custom email domain setup.
[See image.](#did-not-receive-email)
To learn more, see [Managing Custom Email Domains](/workflow-automation/managing-custom-email-domains).
[]![Custom Email Domain page with Revert to Zscaler Domain highlighted](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Custom-Email-Domain-PG-Revert-Zscaler-Domain.png)
[]![Viewing the Verify Custom Domain Setup page when you did not receive the test email and the Didn't receive an email section? is expanded to display the troubleshooting tips.](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Verify-Custom-Domain-Setup-PG-Didnt-Receive-Email-Sec.png)

## January 21, 2025
### Feature Available
#### Custom Email Domains
On the Custom Email Domain page in the Data Protection integration, admins can configure custom email domains for their organization. Workflow Automation generates and sends email notifications for the various actions that you can perform, such as notifying the user of an incident, escalating an incident to an approver or manager, and performing bulk actions. After you add a custom email domain, Workflow Automation uses that custom email domain as the sender for these email notifications.
[See image.](#custom-email-domain)
To learn more, see [Managing Custom Email Domains](/workflow-automation/managing-custom-email-domains).
[]![Viewing all the custom email domains on the Custom Email Domain page](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Custom-Email-Domain-Page.png)
![Viewing the sender email address on a escalation email notification generated by Workflow Automation](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Escalation-Notification-Sender-Email-Address.png)

## January 06, 2025
### Feature Available
#### Enhancements to Data Protection Features
The following are enhancements to the Data Protection features in Workflow Automation:
Enhancement to the Account Settings Page
The Incident Management section is added to the Account Settings page. In this section, you can enable the Retrieve User Email from Primary Data Source option. When you enable this option, the user email address that appears for an incident on the Incident Details page is retrieved from the primary user data source—i.e., System for Cross-domain Identity Management (SCIM) or CSV attributes. Otherwise, the user email address associated with the incident appears for the incident.
[See image.](#incident-management-section-image)
To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).
Enhancement to Obfuscation Settings
On the Account Settings page, you can choose to obfuscate the phone number user attribute for incidents that have occurred in your organization. When you select the phone number for obfuscation, that affects the admin's visibility of this attribute associated with incidents on the Incidents, Incident Details, and workflow pages. In addition, you can override this phone number obfuscation setting by admin on the Admin Assignment page.
[See image.](#phone-number-obfuscation)
To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings), [Managing Admin Assignments](/workflow-automation/managing-admin-assignments), and [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).
[]![Account Settings Page - Incident Management Section](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Account-Settings-Page-Incident-Management-Section.png)
![Incident Details Page - Email Address Field](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incident-Details-Page-Email-Address-Field.png)
[]![Account Settings Page - Privacy and Security Section](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Account-Settings-Page-Phone-Number-Obfuscation.png)
![Add Admin Assignment Page - Obfuscation Settings Section](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Add-Admin-Assignment-Page-Phone-Number-Obfuscation.png)
![Incident Details Page - Additional Information Window](/sites/default/files/downloads/workflow-automation/release-notes/release-upgrade-summary-2025/WA-RN-Incident-Details-Page-Additional-Information-Phone%20Number.png)
