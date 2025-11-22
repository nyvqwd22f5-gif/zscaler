# Viewing & Managing Incident Details
Source: https://help.zscaler.com/workflow-automation/viewing-managing-incident-details
PDF: https://help.zscaler.com/pdf/com/en/1420336.pdf

Workflow Automation provides access to the Incident Details page, which displays detailed information about an incident, such as an overview of the incident, violation details, and the current status of the incident. This page also allows you to manage and take action on an incident.
You can access the** **Incident Details page from the [Incidents](/zia/about-incidents) page by clicking the **Transaction ID** of an incident. On the Incident Details page, you can use the **Next Incident** and **Previous Incident **icons at the top of the page to navigate through the list of incidents.
Viewing Incident Details
You can view the following details about the incident:
- [Duplicate Incidents](#Duplicate-Incidents)
- [Overview](#overview)
- [Violation Details](#violation-details)
- [Current State Details](#current-state-details)
- [Ticket](#ticket-details)
- [Notes](#new-comments)
- [Violation Content](#violation-content-section)
- [Files](#files-section)
- [Recipients](#recipients-section)
- [Collaborators](#collaborator-section)
- [Attachments](#attachments-section)
- [User Notifications](#user-notification-section)
- [State Changes](#change-state)
[]Sometimes a rule can retrigger duplicate incidents for a user. In this case, the first incident appears on the Incidents page, and you can view all the duplicate messages on that incident's detail page.
If duplicate incidents exist for an incident, at the top of its detail page, a message appears stating that fact and providing a link to view the duplicate incidents. If there are no duplicate incidents, this message does not appear on the page.
[See image.](#Duplicate-Incident-Message)
To view the duplicate incidents, click the link at the top of the page. The **Duplicate Incidents** dialog window appears, displaying all the duplicate incidents for the incident. In the **Duplicate Incidents** dialog window, you can see:
- **Transaction ID**: The transaction ID of the duplicate incident.
- **Transaction Time**: The date and time of the transaction. The date and time display in the local time zone of the user.
[See image.](#Duplicate-Incident-Dialog-Box)
To learn more, see [Understanding Duplicate Incidents in Workflow Automation](/workflow-automation/understanding-duplicate-incidents-workflow-automation).
[]In the Overview section, you can see:
- **Incident ID**: The ID of the incident.
- **System Creation Date**: The date and time when the incident was created in the system.
- **Incident Date**: The date and time when the incident was generated due to a policy violation. The date and time display in the local time zone of the user.
- **Severity**: The severity of the incident. Severities can be **Critical**, **High**, **Low**, **Medium**, and **Info**.
- **Priority**: The priority of the incident. Priorities are **Critical**, **High**, **Medium**, and **Low**.
- **Action**: The action associated with the incident. This field is not available for incidents with a Source DLP type of **Email**.
- **DLP Admin**: The Data Loss Prevention (DLP) admin who is responsible for validating the incident.
- **Source DLP Type**: The source DLP type of the incident. Source DLP types are **Inline**, **Email**,** SaaS Security**, and **Endpoint**.
- **Incident Groups**: The incident groups mapped to the incident.
- **Labels**: The labels assigned to the incident.
- **Action Recipient Count**: The actions taken against the recipients of the incident. The number of times the action was taken against the recipients displays next to the action (e.g., Block: 3 and Allow: 1). This field is only available for incidents with a Source DLP type of **Email**.
- **Resolution Date**: The date and time when the incident was resolved (i.e., closed). This field only appears for resolved incidents.
- **Integration**: The name of the DLP application integration in Workflow Automation where the incident occurred. To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services](/workflow-automation/configuring-dlp-application-integration-using-amazon-web-services), [Configuring the DLP Application Integration Using Azure](/workflow-automation/configuring-dlp-application-integration-using-azure), and [Configuring the DLP Application Integration Using Google Cloud Platform](/workflow-automation/configuring-dlp-application-integration-using-google-cloud-platform).
[See image.](#overview-image)
[]In the Violation Details section, you can see:
The attributes that appear under the Originating User subsection can vary, depending on how and what information was imported to Workflow Automation through the primary user data source of System for Cross-domain Identity Management (SCIM) or a CSV file. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings), [Managing User Attributes](/workflow-automation/managing-user-attributes), and [SAML & SCIM Configuration Guide for Microsoft Entra ID](/zia/saml-scim-configuration-guide-microsoft-entra-id).
- Originating User:
-
**Name**: The name of the end user responsible for the incident. When you click the name link, you are redirected to the Incidents page, which displays only the incidents created by the same end user. The user filter is automatically applied in the Filters section. If you applied other filters before clicking the name link, those filters remain applied, as well.
If you choose the User Name attribute for obfuscation, multiple asterisks appear for this field, and the name link is not available. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
[See image.](#username-prefiltered-hyperlink)
-
**Email**: The email address of the end user responsible for the incident. If you choose the User Email attribute for obfuscation, multiple asterisks appear for this field. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
You can override the email address that appears for the end user with the email address for that user from your primary user data source—i.e., SCIM or CSV attributes. To override the email address, on the **Account Settings** page, in the **Incident** **Management** section, enable the **Retrieve User Email from Primary Data Source** option. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
- **Client IP**: The client IP address of the end user. This field is only available for incidents with a Source DLP type of **Inline**. If you choose the Client IP attribute for obfuscation, multiple asterisks appear for this field. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- **Device Name**: The name of the user's device. This field is only available for incidents with a Source DLP type of **Endpoint**. If you choose the Device Name attribute for obfuscation, multiple asterisks appear for this field. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- **Device OS**: The operating system of the user's device. This field is only available for incidents with a Source DLP type of **Endpoint**.
- **Device Trust Level**: The trust level of the user's device. This field is only available for incidents with a Source DLP type of **Endpoint**.
- **Manager Name**: The name of the user's manager. If you choose the Manager Name attribute for obfuscation, multiple asterisks appear for this field. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- **Manager Email**: The email address of the user's manager. If you choose the Manager Email attribute for obfuscation, multiple asterisks appear for this field. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- **Employee Number**: The employee number of the end user.
- **Job Title**: The job title of the end user.
- **Department**: The department of the end user.
- **Home Location**: The home location of the end user.
- **Work Location**: The work location of the end user.
- **Additional Information**: Displays the user attributes associated with the end user responsible for the incident. To view the additional user attributes:
- Click the link provided in this field. The **Additional Information** window appears.
-
In the **Additional Information** window, you can view data associated with the incident such as end user attributes, manager attributes, and addresses. If you choose user attributes for obfuscation, these obfuscated attributes appear with multiple asterisks in this window. To learn more about obfuscation settings, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
The additional information is fetched from the primary user data source (i.e, CSV or SCIM) you selected during the incident generation.
For example, if you select CSV as the primary user data source during the incident generation, the **Additional Information** window displays the user attributes fetched from the imported CSV file. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
The additional information displayed for an incident does not change if you alter the primary user data source. The change of the primary user data source settings impacts only new incidents.
[See image.](#additional-information-windoe-image)
- Policy:
- **Rules**: The DLP rules that the end user violated (e.g., Block-HIPAA). This field is not available for incidents with a Source DLP type of **Email**.
- **Triggered Engines and Dictionaries**. Expand this heading to view the following fields:
- **Engines**: The DLP engines that are assigned to the DLP rules that caused the incident.
- **Dictionaries with Match Count: **The DLP dictionaries that are assigned to the DLP rules that caused the incident. The number of times the end user's traffic violated a specific dictionary is displayed in brackets (e.g., Medical Information[2]).
- **Non-Triggered Engines and Dictionaries**: Expand this heading to view the following fields:
- **Engines**: The DLP engines that are not assigned to the DLP rules that caused the incident.
- **Dictionaries with Match Count: **The DLP dictionaries that are not assigned to the DLP rules that caused the incident. The number of times the end user's traffic violated a specific dictionary is displayed in brackets (e.g., Medical Information[2]).
- **Other Matched Rules**: Click this field to display the rules that the incident violated, in addition to the primary DLP rules that caused the incident. This field is only available for incidents of Source DLP type **Inline** and **Endpoint**.
- Content:
- For incidents of Source DLP type **Inline **and **Endpoint**:
- **File Name**: The name of the file.
- **File Type**: The type or extension of the file.
- **File MD5**: The 32-character MD5 hash of the file.
- **File Size**: The size of the file in bytes.
- For incidents of Source DLP type **SaaS Security**:
- **File Name**: The name of the file.
- **File Type**: The type or extension of the file.
- **File MD5**: The 32-character MD5 hash of the file.
- **File Source Location**: The source location of the file.
- **File Size**: The size of the file in bytes.
- **Document Type**: The type of document.
- **File Shared By**: The email address of the user who shared the file.
- **File Shared At**: The date and time the file was shared.
- **File Modified By**: The email address of the user who modified the file.
- **File Link Expiry**: The date and time the file link expires.
- For incidents of Source DLP type **Email**:
- **File Name**:** **The name of the file.
- **Message ID**: The message ID of the incident.
- **Email Subject**: The subject of the email.
-
Application:
This section is only available for incidents of Source DLP type **Inline**, **SaaS Security**, and **Email**.
- For incidents of Source DLP type **Inline**:
- **URL**: The URL of the application.
- **Referrer URL**: The referrer URL of the application.
- **Name**: The name of the application.
- **Category**: The category of the application.
- For incidents of Source DLP type **SaaS Security**:
- **Name**: The name of the application.
- **Category**: The category of the application. Categories are **File** and **Email**.
- **Current Tag Name**: The name of the tag currently assigned to the application.
- **Is Copilot Accessible**: Indicates whether Copilot can access the application. Values are **yes** or **no**.
- For incidents of Source DLP type **Email**:
- **Name**: The name of the application used to create the email.
- **Tenant**: The tenant ID of the end user.
-
User Activity:
This section is only available for incidents of Source DLP type **Endpoint**.
- **Activity Type**: The type of activity that the user performed that caused the incident.
- **Channel**: The type of channel (e.g., Network Drive Transfer or Remote Drive Transfer) that the user used to cause the incident.
- **Source**: The source of the incident.
- **Destination**: The destination of the incident.
- **Source Type**: The source type of the incident.
- **Destination Type**: The destination type (e.g., Removable Storage Device) for the incident.
- **Source Location**:** **The source location of the incident.
- **Destination Location**: The destination location of the incident.
- **ZDP Mode**: The Zscaler Data Protection (ZDP) mode for the incident. ZDP modes can be **Block** or **Exemption**.
- **Expected Action**: The expected action by the ZDP mode for the incident.
- **Confirm Action**: The action that the user took when prompted with a confirmation dialog box for the incident creation.
- **Confirm Justification**: The justification that the user provided during incident creation.
- **Justification Text**: The optional text that the user provided for the incident. This field is only available if the user adds a justification text.
- **Additional Information**: Additional information or notes about the incident.
The following images are examples of the Violation Details section for a SaaS Security incident, an Inline incident, an Endpoint incident, and an Email incident. The information that displays in the Violation Details section depends on the type of incident.
[See image.](#violation-image)
[]In the Current State Details section, you can see:
- **Status**: The current status of the incident.
- **User**: The person from whom you need a response to move forward with the incident. The person can be the end user, another user, the end user's manager, or another approver. If you choose the User Name attribute or Manager Name attribute for obfuscation, multiple asterisks appear for this field depending on the state. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
[See image.](#current-state-details-image)
[]The Ticket section appears on the page only after you have integrated Workflow Automation with a ticketing integration application (e.g., ServiceNow or Jira Software) and you have executed the Ticket action for the data protection incident on the Incident Details page.
In the Ticket section, you can see:
- **Ticketing Integration**: The tenant ID associated with the ticketing integration application (e.g., ServiceNow or Jira Software).
- **Ticket ID**: The ticket ID associated with the incident in the ticketing integration application. Click the ticket ID link to go to the ticketing integration application (e.g., ServiceNow or Jira Software). After you log in to the ticketing integration application, this particular ticket displays in the application. You can manage the ticket using the ticketing integration application.
- **Project**: The project associated with the ticket in Jira Software. This field only displays for tickets created by the Jira Software application.
- **Ticket Status**: The status of **Closed** displays in this field. This field does not appear on this page until after the ticket is closed in the ticketing integration application (e.g., ServiceNow or Jira Software) and synced with Workflow Automation. Only the **Closed** status displays for these types of tickets. None of the other ticketing integration application statuses are displayed.
The following images are examples of the Ticket section after a ticket is created in ServiceNow and after a ticket is created in Jira Software.
[See image.](#ticket-section-image)
[]In the Notes** **section, you can enter additional notes or information about the progress of the incident, which is logged in the State Changes table.
[See image.](#new-comments-image)
[]The Generate Presigned Link field is not available for incidents of Source DLP type **Email**.
In the Violation Content section, you can see:
- [Generate Presigned Link](#generate-presigned-link-over)
- [View Trigger Data](#view-trigger-data-over)
[]This field displays the presigned link of the incident and also the link's expiration date and time. It allows you to:
- Before the expiration time, click the presigned link to download the actual data that triggered the incident.
- Click the **Copy** icon to copy the link for reference.
[See image.](#generate-presigned-link)
This field enables admins to automatically download the actual data that triggered an incident only if the **Hide Evidence Data - Admin** field is not selected for the DLP integration, and the **Evidence Data Privacy** field is not enabled for the admin on the **Admin Assignment** page in the Workflow Automation Admin Portal. Otherwise, to view the actual data, the admin can copy the evidence link and then access and log in to either Amazon Web Services (AWS) or Azure and paste the link.
[]This field is available only if the **Hide Trigger Data - Admin** field is not selected for the DLP integration, and the **Trigger Data Privacy** field is not enabled on the Admin Assignment** **page for the admin in the Workflow Automation Admin Portal.
This field displays the data that triggered the incident. The prefix and suffix for the trigger data are displayed along with the trigger data itself. The actual trigger data portion is highlighted. You can view the DLP dictionaries, DLP rules, and DLP engines associated with the incident and the exact data that violated the DLP policies.
[See image.](#view-trigger-data)
[]This section is only available for incidents of Source DLP type **Email**.
The Files section displays the files sent to the recipients of the incident and the policies violated by those files. At the top of the section, the total number of files sent appears in parentheses.
In the Files section, you can see:
- **File Name**: The name of the file.
- **File Type**: The type of file (e.g., PDF, XLSX, TXT, or DOCX).
- **File Size**: The size of the file.
- **Document Type**: The type of document (e.g., Invoice).
- **MD5**: The 32-character MD5 hash of the file.
-
**Policy**: Displays the DLP policies that the file violated. To view the policies:
- Click the **View** icon in this field. The **Policy** window appears, displaying a **Triggered Engines and Dictionaries** heading and a **Non-Triggered Engines and Dictionaries** heading.
- In the **Policy** window, expand the **Triggered Engines and Dictionaries** heading to view the following fields:
- **Engines**: The DLP engines that are assigned to the files that caused the incident.
- **Dictionaries with Match Count**: The DLP dictionaries assigned to the files that caused the incident. The number of times the end user's traffic violated a specific dictionary is displayed in brackets (e.g., Medical Information[2]).
- Expand the **Non-Triggered Engines and Dictionaries** heading to view the following fields:
- **Engines**: The DLP engines that are not assigned to the files that caused the incident.
- **Dictionaries with Match Count**: The DLP dictionaries that are not assigned to the files that caused the incident. The number of times the end user's traffic violated a specific dictionary is displayed in brackets (e.g., Medical Information[2]).
[See image.](#file-policies)
[See image.](#Files-Section-Image)
[]This section is only available for incidents of Source DLP type **Email **and **SaaS Security**.
- [Email Source DLP Type](#recipients-section-email)
- [SaaS Security Source DLP Type](#recipients-section-saas-security)
[]The Recipients** **section displays the recipients of the incident and the action taken against each recipient. At the top of the section, the total number of recipients appears in parentheses.
In the Recipients section, you can see:
- **Recipients Email**: The email address of the recipient. If you choose the Recipient Email attribute for obfuscation, multiple asterisks appear for this field. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- **Rule**: The DLP rule that was violated for each recipient (e.g., Block-HIPAA).
- **Severity**: The severity by recipient and rule that was violated. Severity can be **Critical**, **High**, **Low**, **Medium**, or **Info**.
- **Content Location**: The location of the content on the email. Content locations are **Email Attachments** and **Email Body**.
- **Other Matched Rules**: Any other rules that the incident violated in addition to the primary email DLP rule that caused the incident.
- **Action Taken**: The action taken against each recipient. Actions are **Allow, Block**, or **Custom Header Insertion**.
[See image.](#Recipients-Section-Image)
[]The Recipients section displays the internal and external recipients for the incident. This section only appears when the application category for the incident is **Email**.
In the Recipients section, you can see:
- **Internal Recipients**: The recipients within your organization that received the incident. At the top of the section, the total number of recipients appears in parentheses.
- **External Recipients**: The recipients outside your organization that received the incident. At the top of the section, the total number of recipients appears in parentheses.
[See image.](#recipients-section-image-saas-security)
[]This section is only available for incidents of Source DLP type **SaaS Security**.
The Collaborators section displays the internal and external collaborators for the incident and the collaborator scope.
In the Collaborators section, you can see:
- **Internal Collaborators**: The collaborators inside your organization for the incident.
- **External Collaborators**: The collaborators outside your organization for the incident.
- **Collaborator Scope**: The scope for the collaborators.
- **Internal Collaborators Groups**: The collaborator groups inside your organization for the incident.
- **External Collaborators Groups**: The collaborator groups outside your organization for the incident.
[See image.](#Collaborator-section-image)
[]This section is only available for incidents of Source DLP type **SaaS Security **with an application category of **Email**.
The Attachments section displays the files sent to the recipients of the incident. At the top of the section, the total number of attachments sent appears in parentheses.
In the Attachments section, you can see:
- **File Name**: The name of the file.
- **File Type**: The type of file (e.g., PDF, XLSX, TXT, or DOCX).
- **File Size**: The size of the file.
- **Document Type**: The type of document (e.g., Invoice).
- **MD5**: The 32-character MD5 hash of the file.
- **Document Sub Type**: The document subtype for the file.
[See image.](#attachments-section-image)
[]The User Notifications section provides a table that records and displays a detailed log of the incident's notifications sent to the originating user. This section includes the incident's escalations that have been sent to the user's manager or approver. It provides details such as the timeline of the initial notification, the number of times that the user was notified, the communication channels of the notifications, etc. It also displays whether the user responded, the timing of the response, and the actual response itself.
The table provides the following information:
- **User**: The person to whom the admin sends the details of the incident. If you choose the User Name attribute or Manager Name attribute for obfuscation, multiple asterisks appear for this field depending on the type of notification. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- **Role**: The role of the user. The roles are **Originating User**, **Manager**, or **Approver**.
- **Channel**: The communication medium used for notification.
- **Status**: The status of the notification.
- **No. of Attempts**: The number of times the notification was sent to the user.
- **Initial Notification Date**: The date and time when the first notification was sent to a user. The User Notification table is sorted by the initial notification date.
- **Response Date**: The date and time when the user responded to the notification.
- **User Response**: The actual response received from the user.
[See image.](#user-notification-table-image)
[]The State Changes section acts as an audit log for the incident. The State Changes table records and displays all the changes to the incident.
The table displays the following information:
- **State**: The state of the incident. The latest state is displayed at the top.
- **Date**: The date and time when the incident's state changed. The date and time display in the local time zone of the user who caused the incident.
- **Changed By**: The name of the user or service that updated the incident.
- **Comment**: The system-generated comments or comments that the user added about the incident. If you choose the User Name attribute or Manager Name attribute for obfuscation, multiple asterisks appear for those fields in the comments related to a user or manager. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
[See image.](#state-change-image)
Managing the Incident
The Incident Details page allows you to perform certain actions to manage the incidents assigned to you. All the actions you perform, except for the Delete action, are logged in the [State Changes](#change-state) table.
[See image.](#manage-incidents-image)
When managing an incident, you are not required to follow the order of the actions as they appear in the **Actions** drop-down menu. You can perform actions based on the requirements of the incident. For example, you can directly escalate the incident to an approver without notifying the user, depending upon the severity of that incident.
At the top-right of the page, the **Actions** drop-down menu contains the following actions:
- [Close Incident](#close-incident)
- [Notify User](#notify-user)
- [Escalate](#escalate)
- [Investigating](#investigating)
- [Assign to Me](#assign-to-me-action)
- [Assign DLP Admin](#assign-dlp)
- [Assign Priority](#change-priority)
- [Ticket](#ticket-action)
- [Label](#label-assign)
- [Delete](#delete-incidents)
- [Reopen](#reopen-incidents)
- [Update Incident Group](#update-incident-group)
[]Depending on your investigation, you can assign or change the assigned priority of the incident. You can also assign or change the priority of multiple incidents through the [Incidents](/zia/about-incidents) page.
To assign or change the priority of the incident:
- From the **Actions** drop-down menu, select **Assign Priority**. The **Assign Priority** window appears.
-
In the **Assign Priority** window:
- **Priority**: From the drop-down menu, select a priority for the incident. Priorities are **Critical**, **High**, **Medium**, or **Low**.
- **Notes**: Enter additional notes or information about the incident.
[See image.](#change-priority-window)
- Click **Assign**.
[]You can assign an incident to yourself to investigate and resolve it.
To assign an incident to yourself, from the **Actions** drop-down menu, select **Assign to Me**. The incident is assigned to you.
[]You can assign a new DLP admin to the incident. The newly assigned DLP admin is responsible for managing the incident. You can also assign new DLP admins to multiple incidents through the [Incidents](/zia/about-incidents) page.
To assign a new DLP admin to the incident:
- From the **Actions** drop-down menu, select **Assign DLP Admin**. The **Assign DLP Admin** window appears.
-
In the **Assign DLP Admin** window:
- **DLP Admin**: From the drop-down menu, select a new DLP admin for the incident. The drop-down menu displays only the DLP admins who have edit access to the incident group.
- **Notes**: Enter additional notes or information about the incident.
[See image.](#assign-dlp-admin-window)
- Click **Assign**​​​​​.
Only DLP admins with full access to Workflow Automation can assign incidents to DLP admins with restricted access to Workflow Automation.
[]You can assign or change the labels for the incident. Labels can assist you with managing incidents. You can also assign labels to multiple incidents through the [Incidents](/zia/about-incidents) page.
To assign a label to the incident:
- From the **Actions** drop-down menu, select **Label**. The **Label** window appears.
-
In the **Label** window:
- **Label**: From the drop-down menu, select a label that you want to assign to the incident.
- **Value**: From the drop-down menu, select a value for the label. You only need to select a value if the label has associated values.
To add another label to the incident, click the **Add** icon at the end of the row and select another label and label value.
[See image.](#assign-label)
- Click **Submit**​​​​​.
To change the label for the incident:
- From the **Actions** drop-down menu, select **Label**. The **Label** window appears, displaying the assigned labels for the incident.
-
In the **Label** window, change the label or the value associated with an existing label.
To delete a label, click the **Delete** icon at the end of a row.
- Click **Submit**.
[]You can start investigating the incident assigned to you and view the DLP rules violated, the severity, the priority, etc. You can investigate multiple incidents through the [Incidents](/zia/about-incidents) page.
To investigate an incident:
- From the **Actions** drop-down menu, select **Investigating**. The **Investigating** window appears.
-
In the **Investigating **window, under **Notes**,** **enter additional notes or information about the incident.
[See image.](#investigating-window)
- Click **Submit**.
The status of the incident changes to Investigating.
[]You can notify the end user or another user about the DLP violation that created the incident through email, a Slack message if you have integrated Workflow Automation with Slack, or a Microsoft Teams message if you have integrated Workflow Automation with Microsoft Teams. You can also notify the users of multiple incidents through the [Incidents](/zia/about-incidents) page.
To notify the user:
- From the **Actions** drop-down menu, select **Notify User**. The **Notify User** window appears.
-
In the **Notify User** window:
- **Channel Type**:** **Select the type of channel to use for the user notification. Channel types are **Email**, **Slack**, and** Teams**. This field is only available in the window if you have integrated Workflow Automation with Slack or Microsoft Teams. If the **Channel Type** field is not available in the window, the user notification is by email.
- **Language**: From the drop-down menu, select the language for the notification message that the user receives.
- **User**: Enter the email address of the user. By default, this field displays the user who is associated with the incident, but you can enter a different user. If you have integrated Workflow Automation with Slack and you select the **Slack** channel type, the email address that you enter must be associated with a user for your organization in Slack. If you have integrated Workflow Automation with Microsoft Teams and you select the **Teams** channel type, the email address that you enter must be associated with a user for your organization in Microsoft Teams.
In addition, if you choose the User Email attribute for obfuscation, multiple asterisks appear for this field. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- **Note to user**: Enter additional notes or information about the incident.
[See image.](#notify-user-window)
-
Click **Submit**.
A user notification (i.e., email, Slack message, or Microsoft Teams message) is sent to the user requesting justification for the incident.
The status of the incident changes to Validating with User. After the user reviews and responds to the user notification, the status of the incident changes to Received Justification Response.
[]After the status of the incident changes to Received Justification Response, you can evaluate the justification that the user submitted. If you are not satisfied with the response, you can escalate the incident to the user's manager or another approver. You can escalate multiple incidents to a manager or approver through the [Incidents](/zia/about-incidents) page.
To escalate the incident:
- From the **Actions** drop-down menu, select **Escalate**. The **Escalate **window appears.
-
In the **Escalate** window:
-
**User Type: **Select the type of user to whom you want to escalate the incident.
- To escalate the incident to the user's manager, select **Manager**. The **Manager** option is visible only when a manager is available to the end user. In this case, the incident is escalated to the manager associated with the incident.
- To escalate the incident to an approver, select **Approver**. After you select the **Approver** user type, the **Approver** field appears, where you can select the approver of your choice for the incident.
The **User Type** field, where you can select the type of user (i.e., Approver or Manager), is only available if you map the additional Workflow Automation user attributes when configuring [SCIM](/zia/saml-scim-configuration-guide-microsoft-entra-id) provisioning in Azure. Otherwise, the **User Type** field is not available, and you can only escalate the incident to an **Approver**.
[See image.](#escalate-window-no-user-type)
- **Channel Type**: Select the type of channel to use for the escalation notification. Channel types are **Email**, **Slack**, and** Teams**. This field is only available in the window if you have integrated Workflow Automation with Slack or Microsoft Teams. If the **Channel Type** field is not available in the window, the escalation notification is by email.
- **Language**: From the drop-down menu, select the language for the escalation message to the manager or approver.
- **Approver**: Select or manually enter an approver to whom you want to escalate the issue. This field is not available if you select **Manager** as the user type. If you have integrated Workflow Automation with Slack and select the **Slack** channel type, the email address that you enter for the approver must be associated with a user for your organization in Slack. If you have integrated Workflow Automation with Microsoft Teams and you select the **Teams** channel type, the email address that you enter must be associated with a user for your organization in Microsoft Teams.
- **Note to user**: Enter additional notes or information about the incident.
[See image.](#escalate-incident)
-
Click **Submit**.
An escalation notification (i.e., email, Slack message, or Microsoft Teams message) is sent to the approver or manager requesting the next steps.
The status of the incident changes to Escalated*.* After the manager or approver reviews and responds to the escalation notification, the status of the incident changes to Received Justification Response.
You can also directly close the incident if you are satisfied with the justification response that the user submitted.
[]You can close the incident when the justification response from the user is acceptable or the approver or manager, after reviewing the escalation email, decides that the incident can be closed. You can close multiple incidents at the same time through the [Incidents](/zia/about-incidents) page.
To close the incident:
- From the **Actions** drop-down menu, select **Close Incident**. The **Close Incident** window appears.
-
In the **Close Incident** window:
- **Notes**: (Optional) Enter additional notes or information about the incident.
- **Resolution Label**: From the drop-down menu, select the reason for the resolution. If values are associated with the label, select the label value. You can only associate one label value with a resolution label.
- If the incident is a false positive, select the **False Positive **checkbox.** **When you mark an incident as a false positive, after the incident is closed, Workflow Automation categorizes the incident to be shown in the False Positive Incidents By Rule widget and the False Positive Incidents By Dictionary widget on the Incident Analytics dashboard. Workflow Automation reports the number of false positives for each incident on the Incident Analytics dashboard by rule and by dictionary. To learn more, see [About the Incident Analytics Dashboard](/workflow-automation/about-incident-analytics-dashboard).
[See image.](#close-incident-action)
- Click **Yes**.
The status changes to Resolved.
After an incident is closed (status is Resolved), you can still perform all the other actions against the incident except for the Investigating and Escalate actions, but the incident status remains at Resolved.
[]You can create a ticket for a ticketing integration application (e.g., ServiceNow or Jira Software) and associate it with the incident. You cannot associate multiple incidents with a ticketing integration application ticket through the [Incidents](/zia/about-incidents) page. The Ticket action is only available if you have integrated Workflow Automation with a ticketing integration application (e.g., ServiceNow or Jira Software).
To create and associate a ticket with the incident:
- From the **Actions** drop-down menu, select **Ticket**. The **Ticket **window appears.
-
In the **Ticket** window:
- **Ticketing Integration**: From the drop-down menu, select the tenant ID associated with the ticketing integration application (e.g., ServiceNow or Jira Software).
- **Project**: (Jira tickets only) Select the project in the ticketing integration application where you want the ticket to be created. This field is only available after you select a Jira Software tenant ID in the **Ticketing Integration** field.
- **User**: From the drop-down menu, select the user to assign to the ticket. Only users who appear on the **Integration Users** page for that ticketing integration application are available for selection. To learn more, see [Managing Integration Users](/zia/managing-integration-users).
- **Notes**: Enter additional information about the incident. These notes appear as a comment in the ticket in the ticketing integration application.
[See image.](#Ticket-window-image)
-
Click **Submit**.
A ticket is created in the ticketing integration application (e.g., ServiceNow or Jira Software), and that ticket information appears in the Ticket section of the **Incident Details** page. Adding a ticket to the incident does not change the status of the incident.
[]After an incident is closed (Status is Resolved), the **Reopen **action appears in the **Actions** drop-down menu on the page for that incident. You can reopen an incident only from the Incident Details page.
[See image.](#Reopen-Incident)
To reopen an incident, from the **Actions** drop-down menu, select **Reopen**. The incident is reopened, and the status of the incident changes from Resolved to Investigating.
[]You can delete an incident only from the Incident Details page, and you can delete an incident in any status. The delete action is only available for admins who are assigned to a role that has delete access permission for the Incidents category. To learn more, see [Managing Roles and Permissions.](/workflow-automation/managing-roles-and-permissions)
To delete an incident:
-
From the **Actions** drop-down menu, select **Delete**. The **Delete Incidents **dialog window appears, displaying a message asking whether you are sure that you want to delete the incident.
[See image.](#delete-incident)
-
Click **Yes**. The incident is deleted.
This action permanently deletes the incident, and you can't recover a deleted incident later.
[]On the Incident Details page, you can use the Update Incident Group action to do the following:
- Add additional incident groups to the incident.
- Delete one or more of the incident groups that are currently assigned to the incident.
- Update the incident group that is used for assigning the admin to the incident. When making this update, you can select one of the newly added incident groups, or you can select another one of the incident groups that was previously assigned to the incident.
You can also update the incident groups for multiple incidents through the [Incidents](/workflow-automation/about-incidents) page.
To update incident groups:
-
From the **Actions** drop-down menu, select **Update Incident Group**. The **Update Incident Group** window appears, displaying the following information:
- In the **Available **section, all the incident groups that have been assigned to at least one admin appear in alphabetical order. The number of available incident groups appears in parentheses next to the heading. To learn more, see [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- In the **Assigned** section, the incident groups that are currently assigned to the incident appear, and an information icon appears next to the incident group that is currently being used to assign the admin. The number of assigned incident groups appears in parentheses next to the heading.
[See image.](#update-incident-group-window-image-initial)
- (Optional) Add incident groups:
-
(Optional) At the top of the window, use the search field to locate an incident group in the **Available** section.
The search for incident groups spans across the **Available**, **Assigned**, and **Newly added** sections.
-
In the **Available** section, click the **Add** icon next to each incident group that you want to add to the incident. The incident group is moved from the **Available** section to the **Newly added** section. The number of newly added incident groups appears in parentheses next to the heading. After you add an incident group, the **Update Admin Assignment** checkbox becomes available.
In the **Newly added** section, you can also delete a newly added incident group by clicking the **Delete** icon next to an incident group. After you delete an incident group, that incident group is displayed in the **Available** section. You can also click **Reset** to reset the window to the original incident group settings.
[See image.](#update-incident-group-window-adding-incident-groups)
-
(Optional) Delete assigned incident groups. You can delete assigned incident groups even if you have not added new incident groups. In the **Assigned** section, click the **Delete** icon next to each incident group you want to delete. After you delete an incident group, that incident group is displayed in the **Available** section.
If you delete an incident group that is being used for admin assignment, a warning message appears stating that the current assigned admin will be removed and instructing you to update the admin assignment to select a new incident group for admin mapping. If you have already added new incidents groups, the **Update Admin Assignment** checkbox is already available. If you have not added new incidents groups, the **Update Admin Assignment** checkbox becomes available at this time.
You must have at least one incident group assigned to the incident. If you delete all the assigned and newly added incident groups, a message appears stating that at least one group must be assigned. You can also click **Reset** to reset the window to the original incident group settings.
[See image.](#update-incident-group-window-deleting-assigned-incident-groups)
-
(Optional) Update the admin assignment:
You can update the admin assignment for the incident to use one of the newly added incident groups or to use another one of the previously existing assigned incident groups that is not used for admin assignment. If you delete the existing assigned incident group that is used for admin assignment, to ensure an admin gets assigned to the incident, you must select another incident group to be used for admin assignment.
- Select the** Update Admin Assignment** checkbox. The **Incident Group** field appears.
-
From the **Incident Group** drop-down menu, select the incident group to be used for assigning the admin to the incident. This menu lists all the incident groups that are displayed in the **Assigned** and **Newly added** sections of the window.
[See image.](#update-incident-group-window-update-admin-assignment)
- (Optional) In the **Notes** field, enter additional notes for updating the incident groups.
-
Click **Update**. The **Incident Details** page appears. To see the updates, refresh the page. After refreshing the page, you can see the following updates:
- The **Incident Groups **field displays the updated incident groups.
- The **Priority** field might change based on the final list of incident groups that you assigned to the incident. The priority of an incident is derived from the incident groups assigned to the incident. If the incident groups have different priorities, the highest priority is used.
- If you updated the admin assignment to use a different incident group, the **DLP Admin** field displays the name of the admin derived from that incident group.
- The **State Changes** section displays all the state changes that were made to the incident when you updated the incident groups for the incident.
[See image.](#incident-details-page-image-after-update-incident-group)
[]![Incidents Details Page - Duplicate Incident Message](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Duplicate-Incidents-Link-Message.png)
[]![Incident Details Page - Duplicate Incidents Dialog Window](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Duplicate-Incidents-Window.png)
[]![Overview section](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Overview-Sect_0.png)
[]![Screenshot of the originating username prefiltered hyperlink on the Incident Details page](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Username-Link.png)
[]![Incident Details Page - Violation Details - SaaS Security Incident](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Violation-Details-SaaSSecurity_2.png)
![Incident Details Page - Violation Details - Inline](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Violation-Details-Inline_0.png)
![Incident Details Page - Violation Details - Endpoint Incident](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Violation-Details-Endpoint_0.png)
![Incident Details - Violation Details - Email Incident](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Violation-Details-Email_0.png)
[]![Incident Details page - Generate Presigned Link section](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Generate-Presigned-Link.png)
[]![Incident Details Page - View Trigger Data Section](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-View-Trigger-Data.png)
[]![Current State Details section](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Current-State-Details-Section.png)
[]![Incident Details page - Ticket section](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Ticket-Section-ServiceNow.png)
![Incident Details Page - Ticket Section](/downloads/zia/policies/data-loss-prevention/workflow-automation/incidents/viewing-managing-incident-details/ZIA-WA-Incident-Details-PG-Ticket-Section-JIRA.png)
[]![Incident Details Page - Notes Section](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Notes-Section.png)
[]![Incident Details Page - Policy Window](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Files-Sect-Policy.png)
[]![Incident Details Page - Files Section](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-Page-Email-Files-Section.png)
[]![Viewing the Recipients Section on the Incident Details Page for an Incident of Source DLP type Email](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Recipients.png)
[]![Viewing the Recipients Section on the Incident Details Page for an Incident of Source DLP Type SaaS Security](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Recipients-Section-Saas-Security.png)
[]![Incident Details Page - Collaborators Section](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Collaborators-Section_1.png)
[]![Viewing the Attachments Table on the Incident Details Page](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Attachments-Section.png)
![User Notifications Table on the Incident Details Page](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-User-Notifications.png)
[]
[]![Incidents Details Page - State Changes Section](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-State-Changes-Section.png)
[]![Viewing the Incident Details page showing the Actions menu. The menu shows the following options: Close Incident, Notify User, Escalate, Investigating, Assign to Me, Assign DLP Admin, Assign Priority, Ticket, Label, Delete, and Update Incident Group.](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Action-Menu_1.png)
[]![Incident Details Page - Investigating Action](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Investigating-Win.png)
[]![Incident Details Page - Assign Priority Action](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Assign-Priority-Window_0.png)
[]![Incident Details Page - Assign DLP Admin Action](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Assign-DLP-Admin-Win.png)
[]![Incident Details Page - Label Window](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Label-Win.png)
[]![Incident Details Page - Notify User Action](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Notify-User-Win_0.png)
[]![Incident Details Page - Escalate Action](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Escalate-Window-Manager-UT.png)
![Incident Details Page - Escalate Action](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Escalate-Window-Approver-UserT.png)
[]![Incident Details Page - Close Incident Action](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Close-Incident-Window_0.png)
[]![Incident Details page - Ticket Action](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Ticket-Window_0.png)
[]![Incidents Details page - Reopen Action](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Reopen-Incident_0.png)
[]![Incidents Details Page - Delete Incident Action](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Delete-Incidents-Window.png)
[]
![Incident Details Page - Escalate Window](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Escalate-Window.png)
![Additional Information Window](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-Additional-Information-Window.png)
[]
[]![Viewing the Update Incident Group window before incident groups are updated. The window contains an Available incident group section, an Assigned incident group section, an update admin assignment section, and a Notes field. ](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Update-Incident-Group-Window-Initial-Window.png)
[]![Video showing how to add and delete new incident groups on the Update Incident Group window](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Update-Incident-Group-Window-Step2-Adding-Incident-Groups.gif)
[]![Video showing how to delete assigned incident groups on the Update Incident Group window](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Update-Incident-Group-Window-Step3-Deleting-Assigned.gif)
[]![Video showing how to update the incident group for admin assignment on the Update Incident Group window](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Update-Incident-Group-Window-Step4-Update-Admin-Assignment.gif)
[]![Viewing the Incident Details page after doing incident group updates. The fields that are affected by an incident group update are highlighted on the window. Those fields are Incident Groups, DLP Admin, and Priority. In addition, the State Changes section is highlighted showing the entries for the incident group updates.](/downloads/workflow-automation/incidents/viewing-managing-incident-details/WA-Incident-Details-PG-After-Incident-Group-Updates.png)