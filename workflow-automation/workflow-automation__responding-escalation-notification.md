# Responding to an Escalation Notification
Source: https://help.zscaler.com/workflow-automation/responding-escalation-notification
PDF: https://help.zscaler.com/pdf/com/en/1433821.pdf

The format of the notification and survey might not be the same as illustrated in this article. It depends upon the notification and the survey template that your organization configured in the Workflow Automation Admin Portal.
If you are a manager or an approver, the Workflow Automation Admin Portal sends you an alert notification (e.g., email, Slack message, or Microsoft Teams message) about transactions (incidents) that violate Data Loss Prevention (DLP) policies. The notification contains an Incident Detail Link associated with the survey that you must complete to approve or suggest the next steps for the incidents.
An incident can be escalated when the justification submitted by the end user is not acceptable or when the incident is of high severity and priority. If the organization accepts the justification that the end user submits, then you are not notified about that incident.
Viewing the Escalation Notification
When an incident is escalated, you receive a notification (e.g., email, Slack message, or Microsoft Teams message) requesting a response. The notification contains the following information:
- The email address of the end user responsible for the incident. If you choose the User Email attribute for obfuscation, multiple asterisks appear in the user email address field for the notification. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- The date and time when the incident occurred.
- The Incident Detail Link, where you can view the details of the incident and also complete a survey to respond to the incident. This link is only valid for 24 hours.
- The incident ID.
- The hostname or the application of the incident.
- The priority of the incident.
- The note to the approver from the admin who initiated the escalation. This note appears only if the admin enters a note.
The following images are examples of an escalation notification sent by email, Slack message, and Microsoft Teams message. The escalation notifications contain the same information, but the format of the message is different.
[See image.](#notification-images)
Depending on your email settings, the escalation notification emails might be tagged as spam and sent to your spam folder. Change your settings to receive the escalation notification emails directly in your inbox.
Viewing the Incident Details
To view the details of the incident, click the **Incident Detail Link** provided in the escalation notification. You are redirected to the **Incident** page, where you can view the following details:
- [Overview](#overview-details)
- [Violation Details](#violation-details)
- [Generate Presigned Link](#generate-evidence)
- [View Trigger Data](#view-trigger-data)
- [Policy](#policy-section-email-incidents)
- [Notification Response History](#notification-response-history)
Completing the Survey
After reviewing the incident details, you might be required to complete the survey at the end of the Incident page to approve or suggest the next steps for the incident.
To respond, complete the following survey and then click **Submit**:
- **Justification Type**: Select a justification type for the incident. Justification types are **False Positive**, **Manager Approved**, **Manager Rejected**, and **Others**.
- **Justification Reason**: Enter a justification reason in detail for the incident—approve it or suggest next steps.
[See image.](#justification-section)
Your response is sent to the organization's admin who is investigating the incident for further review.
[]In the Overview** **section, you can see:
- **Incident ID**: The ID of the incident.
- **Incident Date**: The date on which the incident occurred.
- **Severity**: The severity of the incident. This field is not available for incidents with a Source DLP type of **Email**.
- **Resolution Date**: The date and time when the incident was resolved (i.e., closed). This field only appears for resolved incidents.
[See image.](#overview-image)
[]In the Violation Details section, you can see the following attributes:
The attributes that appear under the Originating User subsection can vary, depending on what information was imported to Workflow Automation and whether it was imported via the primary user data source of System for Cross-domain Identity Management (SCIM) or a CSV file. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings), [Managing User Attributes](/workflow-automation/managing-user-attributes), and [SAML & SCIM Configuration Guide for Microsoft Entra ID](/zia/saml-scim-configuration-guide-microsoft-entra-id).
- [Incidents of Source DLP Type Inline](#violation-details-inline-incident)
- [Incidents of Source DLP Type SaaS Security](#violation-details-saasapi-incident)
- [Incidents of Source DLP Type Endpoint](#violation-details-endpoint-incident)
- [Incidents of Source DLP Type Email](#violation-details-email-incident)
-
[]Originating User:
- **Name**: The name of the end user responsible for the incident. If you choose the User Name attribute for obfuscation, multiple asterisks appear in this field.
- **Email**: The email address of the end user responsible for the incident. If you choose the User Email attribute for obfuscation, multiple asterisks appear for this field.
- **Client IP**: The client IP address of the end user. If you choose the Client IP attribute for obfuscation, multiple asterisks appear in this field.
- **Manager Name**: The name of the user's manager. If you choose the Manager Name attribute for obfuscation, multiple asterisks appear in this field.
- **Manager Email**: The email address of the manager. If you choose the Manager Email attribute for obfuscation, multiple asterisks appear in this field.
- **Employee Number**: The employee number of the end user.
- **Job Title**: The job title of the end user.
- **Department**: The department of the end user.
- **Home Location**: The home location of the end user.
- **Work Location**: The work location of the end user.
- **Additional Information**: Displays the user attributes associated with the end user responsible for the incident. To view the additional user attributes:
- Click the link provided in this field. The **Additional Information** window appears.
-
In the **Additional Information** window, you can view data associated with the incident, such as end user attributes, manager attributes, and addresses. If you choose user attributes for obfuscation, these obfuscated attributes appear with multiple asterisks in this window.
The additional information is fetched from the primary user data source (i.e., CSV or SCIM) you selected during the incident generation.
For example, if you select **CSV** as the primary user data source during the incident generation, the **Additional Information** window displays the user attributes fetched from the imported CSV file. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
The additional information displayed for an incident does not change if you alter the primary user data source. Changing the primary user data source settings impacts only new incidents.
[See image.](#additional-information-window-inline)
To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- Policy:
- **Rules**: The DLP rules that the end user violated (e.g., Block-HIPAA).
- **Engines**: The DLP engines associated with the incident.
- **Dictionaries with Match Count**:** **The DLP dictionaries associated with the incident. The number of times the end user's traffic violated a specific dictionary is displayed in brackets (e.g., Medical Information[2]).
- **Other Matched Rules**: Click this field to display the rules that the incident violated, in addition to the primary DLP rules that caused the incident. This field is only available for incidents of Source DLP type **Inline** and **Endpoint**.
The policy fields are only available if the **Hide Policy Details - Manager/Approver** field is not selected on the **Zscaler DLP Integration** page, the **Zscaler DLP Azure Integration **page, or the **Zscaler DLP GCP Integration **page in the Workflow Automation Admin Portal. To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services](/workflow-automation/configuring-dlp-application-integration-using-amazon-web-services), [Configuring the DLP Application Integration Using Azure](/workflow-automation/configuring-dlp-application-integration-using-azure), and [Configuring the DLP Application Integration Using Google Cloud Platform](/workflow-automation/configuring-dlp-application-integration-using-google-cloud-platform).
- Content:
- **File Name**: The name of the file.
- **File Type**: The type or extension of the file.
- **File MD5**: The 32-character MD5 hash of the file.
- Application:
- **URL**: The URL of the application.
- **Name**: The name of the application.
- **Category**: The category of the application.
The following image is an example of the Violation Details section for an Inline incident. The information that is displayed in the Violation Details section varies depending on the type of incident.
[See image.](#violation-details-section-inline-incident)
-
[]Originating User:
- **Name**: The name of the end user responsible for the incident. If you choose the User Name attribute for obfuscation, multiple asterisks appear in this field.
- **Email**: The email address of the end user responsible for the incident.
- **Manager Name**: The name of the user's manager. If you choose the Manager Name attribute for obfuscation, multiple asterisks appear in this field.
- **Manager Email**: The email address of the manager. If you choose the Manager Email attribute for obfuscation, multiple asterisks appear in this field.
- **Employee Number**: The employee number of the end user.
- **Job Title**: The job title of the end user.
- **Department**: The department of the end user.
- **Home Location**: The home location of the end user.
- **Work Location**: The work location of the end user.
- **Additional Information**: Displays the user attributes associated with the end user responsible for the incident. To view the additional user attributes:
- Click the link provided in this field. The **Additional Information** window appears.
-
In the **Additional Information** window, you can view data associated with the incident, such as end user attributes, manager attributes, and addresses. If you choose user attributes for obfuscation, these obfuscated attributes appear with multiple asterisks in this window.
The additional information is fetched from the primary user data source (i.e., CSV or SCIM) you selected during the incident generation.
For example, if you select **CSV** as the primary user data source during the incident generation, the **Additional Information** window displays the user attributes fetched from the imported CSV file. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
The additional information displayed for an incident does not change if you alter the primary user data source. Changing the primary user data source settings impacts only new incidents.
[See image.](#additional-information-window-saassecurity)
To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- Policy:
- **Rules**: The DLP rules that the end user violated (e.g., Block-HIPAA).
- **Engines**: The DLP engines associated with the incident.
- **Dictionaries with Match Count**:** **The DLP dictionaries associated with the incident. The number of times the end user's traffic violated a specific dictionary is displayed in brackets (e.g., Medical Information[2]).
The policy fields are only available if the **Hide Policy Details - Manager/Approver** field is not selected on the **Zscaler DLP Integration** page, the **Zscaler DLP Azure Integration **page, or the **Zscaler DLP GCP Integration **page in the Workflow Automation Admin Portal. To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services](/workflow-automation/configuring-dlp-application-integration-using-amazon-web-services), [Configuring the DLP Application Integration Using Azure](/workflow-automation/configuring-dlp-application-integration-using-azure), and [Configuring the DLP Application Integration Using Google Cloud Platform](/workflow-automation/configuring-dlp-application-integration-using-google-cloud-platform).
- Content:
- **File Name**: The name of the file.
- **File Type**: The type or extension of the file.
- **File MD5**: The 32-character MD5 hash of the file.
- **File Source Location**: The source location of the file.
- **File Size**: The size of the file.
- **Document Type**: The type of document.
- **File Shared By**: The email address of the user who shared the file.
- **File Shared At**: The date and time the file was shared.
- **File Modified By**: The email address of the user who modified the file.
- **File Link Expiry**: The date and time the file link expires.
- Application:
- **Name**: The name of the application.
- **Category**: The category of the application. Categories are **File** and **Email**.
- **Current Tag Name**: The name of the tag currently assigned to the application.
- **Is Copilot Accessible**: Indicates whether Copilot can access the application. Values are **yes** or **no**.
The following image is an example of the Violation Details section for a SaaS Security incident. The information that is displayed in the Violation Details section varies depending on the type of incident.
[See image.](#violation-details-section-saasapi-incident)
-
[]Originating User:
- **Name**: The name of the end user responsible for the incident. If you choose the User Name attribute for obfuscation, multiple asterisks appear in this field.
- **Manager Name**: The name of the user's manager. If you choose the Manager Name attribute for obfuscation, multiple asterisks appear in this field.
- **Manager Email**: The email address of the manager. If you choose the Manager Email attribute for obfuscation, multiple asterisks appear in this field.
- **Employee Number**: The employee number of the end user.
- **Job Title**: The job title of the end user.
- **Department**: The department of the end user.
- **Device Name**: The name of the user's device. If you choose the Device Name attribute for obfuscation, multiple asterisks appear for this field.
- **Device OS**: The operating system of the user's device.
- **Device Trust Level**: The trust level of the user's device.
- **Home Location**: The home location of the end user.
- **Work Location**: The work location of the end user.
- **Additional Information**: Displays the user attributes associated with the end user responsible for the incident. To view the additional user attributes:
- Click the link provided in this field. The **Additional Information** window appears.
-
In the **Additional Information** window, you can view data associated with the incident, such as end user attributes, manager attributes, and addresses. If you choose user attributes for obfuscation, these obfuscated attributes appear with multiple asterisks in this window.
The additional information is fetched from the primary user data source (i.e., CSV or SCIM) you selected during the incident generation.
For example, if you select **CSV** as the primary user data source during the incident generation, the **Additional Information** window displays the user attributes fetched from the imported CSV file. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
The additional information displayed for an incident does not change if you alter the primary user data source. Changing the primary user data source settings impacts only new incidents.
[See image.](#additional-information-window-endpoint)
To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- Policy:
- **Rules**: The DLP rules that the end user violated (e.g., Block-HIPAA).
- **Engines**: The DLP engines associated with the incident.
- **Dictionaries with Match Count**:** **The DLP dictionaries associated with the incident. The number of times the end user's traffic violated a specific dictionary is displayed in brackets (e.g., Medical Information[2]).
The policy fields are only available if the **Hide Policy Details - Manager/Approver** field is not selected on the **Zscaler DLP Integration** page, the **Zscaler DLP Azure Integration **page, or the **Zscaler DLP GCP Integration **page in the Workflow Automation Admin Portal. To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services](/workflow-automation/configuring-dlp-application-integration-using-amazon-web-services), [Configuring the DLP Application Integration Using Azure](/workflow-automation/configuring-dlp-application-integration-using-azure), and [Configuring the DLP Application Integration Using Google Cloud Platform](/workflow-automation/configuring-dlp-application-integration-using-google-cloud-platform).
- Content:
- **File Name**: The name of the file.
- **File Type**: The type or extension of the file.
- **File MD5**: The 32-character MD5 hash of the file.
- **File Size**: The size of the file in bytes.
- User Activity:
- **Activity Type**: The type of activity that the user performed that caused the incident.
- **Channel**: The type of channel (e.g., Network Drive Transfer or Remote Drive Transfer) that the user used to cause the incident.
- **Source**: The source of the incident.
- **Destination**: The destination of the incident.
- **Source Type**: The source type of the incident.
- **Destination Type**: The destination type (e.g., Removable Storage Device) for the incident.
- **Source Location**: The source location of the incident.
- **Destination Location**: The destination location for the incident.
- **ZDP Mode**: The Zscaler Data Protection (ZDP) mode for the incident.
- **Expected Action**: The expected action by the ZDP mode for the incident.
- **Confirm Action**: The action that the user took when prompted with a confirmation dialog box for the incident creation.
- **Confirm Justification**: The justification that the user provided during incident creation.
- **Additional Information**: Additional information or notes about the incident.
The following image is an example of the Violation Details section for an Endpoint incident. The information that is displayed in the Violation Details section varies depending on the type of incident.
[See image.](#violation-details-section-endpoint-incident)
[]Originating User:
- **Name**: The name of the end user responsible for the incident. If you choose the User Name attribute for obfuscation, multiple asterisks appear in this field. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- **Email Subject**: The subject of the email.
- **Application Name**: The name of the application used to create the email.
- **Work Location**: The work location of the end user.
- **Additional Information**: Displays the user attributes associated with the end user responsible for the incident. To view the additional user attributes:
- Click the link provided in this field. The **Additional Information** window appears.
-
In the **Additional Information** window, you can view data associated with the incident, such as end user attributes, manager attributes, and addresses. If you choose user attributes for obfuscation, these obfuscated attributes appear with multiple asterisks in this window.
The additional information is fetched from the primary user data source (i.e., CSV or SCIM) you selected during the incident generation.
For example, if you select **CSV** as the primary user data source during the incident generation, the **Additional Information** window displays the user attributes fetched from the imported CSV file. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
The additional information displayed for an incident does not change if you alter the primary user data source. Changing the primary user data source settings impacts only new incidents.
[See image.](#additional-information-window-email)
The following image is an example of the Violation Details section for an Email incident. The information that is displayed in the Violation Details section varies depending on the type of incident.
[See image.](#violation-details-section-email-incident)
[]This section is only available for incidents of Source DLP type **Email**. For the other types of incidents, the policy information for the incident appears in the Violation Details section.
In the Policy section, you can see:
- **Recipients Email**: The email address of the recipient who received the incident. If you choose the Recipient Email attribute for obfuscation, multiple asterisks appear in this field. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- **Rule**: The DLP rule that the end user violated.
- **Other Matched Rules**: The other rules that the incident violated in addition to the primary DLP rule that caused the incident.
[See image.](#policy-section-image-email-incident)
[]This field displays the presigned link of the incident and also the expiration date and time of the presigned link. It allows you to:
- Click the presigned link to download the actual data that triggered the incident before the expiration time.
- Click the **Copy** icon to copy the link for reference.
[See image.](#generate-presigned-link-image)
This field enables you to automatically download the actual data for the incident only if the **Hide** **Evidence Data - Manager/Approver **field is not selected on the **Zscaler DLP Integration** page, the **Zscaler DLP Azure Integration **page, or the **Zscaler DLP GCP Integration **page in the Workflow Automation Admin Portal. Otherwise, to view the actual data, you can copy the evidence link and then access and log in to either Amazon Web Services (AWS), Azure, or Google Cloud Platform and paste the link in that environment.
[]This field displays the data that triggered the incident. The prefix and suffix for the trigger data are displayed, along with the trigger data itself. The actual trigger data portion is highlighted. You can view the DLP dictionaries, DLP rules, and DLP engines associated with the incident and the exact data that violated the DLP policies.
[See image.](#view-trigger-data-image)
This field is available only if the **Hide** **Trigger Data - Manager/Approver** field is not selected on the **Zscaler DLP Integration** page, the **Zscaler DLP Azure Integration **page, or **Zscaler DLP GCP Integration **page in the Workflow Automation Admin Portal.
[]The Notification Response History table displays a detailed log of the incident's end user notifications and escalations sent to the originating user and the user's manager or approver, respectively.
The table displays the following information:
- **User**: The person to whom the admin sends the details of the incident. If you choose the User Email attribute or the Manager Email attribute for obfuscation, multiple asterisks appear in this field for the manager or user. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- **Role**: The role of the user. The roles are **Originating User**, **Manager**, or **Approver**.
- **Initial Notification Date**: The date and time when the first notification was sent to a user.
- **Response Date**: The date and time when the user responded to the notification.
- **User Response**: The actual response received from the user.
[See image.](#notification-response-history-image)
![Incident Page - Notification Response History](/downloads/workflow-automation/incidents/responding-escalation-notification/WA-Responding-Escalation-Notification-Notification-Response-History.png)
[]
[]![Viewing an example of an email escalation notification. The escalation notification contains the email address of the end user responsible for the incident, the date and time the incident occurred, the incident ID, the hostname or the application of the incident, the priority of the incident, and a note to the approver from the admin who initiated the escalation. In addition, it contains an Incident Detail Link, where you can view the details of the incident and complete a survey to respond to the incident.](/downloads/workflow-automation/incidents/responding-escalation-notification/WA-Responding-Escalation-Notification-Email-Image.png)
[]![Viewing an example of a Slack escalation notification. The escalation notification contains the email address of the end user responsible for the incident, the date and time the incident occurred, the incident ID, the hostname or the application of the incident, the priority of the incident, and a note to the approver from the admin who initiated the escalation. In addition, it contains an Incident Detail Link, where you can view the details of the incident and complete a survey to respond to the incident.](/downloads/zia/policies/data-loss-prevention/workflow-automation/responding-escalation-email/ZIA-WA-Escalation-Notification-Message-Slack.png)
![Viewing an example of a Teams escalation notification. The escalation notification contains the email address of the end user responsible for the incident, the date and time the incident occurred, the incident ID, the hostname or the application of the incident, the priority of the incident, and a note to the approver from the admin who initiated the escalation. In addition, it contains an Incident Detail Link, where you can view the details of the incident and complete a survey to respond to the incident.](/downloads/zia/policies/data-loss-prevention/workflow-automation/responding-escalation-email/ZIA-WA-Escalation-Notification-Message-Teams.png)
[]![Viewing the Survey section on the Incidents page for the escalation email](/downloads/workflow-automation/incidents/responding-escalation-notification/WA-Responding-Escalation-Notification-Survey-Image.png)
[]![Viewing the Violation Details section on the Incidents page for the escalation email](/downloads/workflow-automation/incidents/responding-escalation-notification/WA-Responding-Escalation-Notification-Violation-Details-Inline.png)
[]![Viewing the Additional Information window displaying multiple attributes (i.e., Organization, Division, Phone Number, Project IDs, Termination Date, Worker Type, Organization Hierarchy, Location, User Role, and Manager Information) for the incident that were imported to Workflow Automation via SCIM or CSV](/downloads/workflow-automation/incidents/responding-escalation-notification/WA-Responding-Escalation-Notification-Additional-Information-Window-Inline.png)
[]![Viewing the Violation Details section on the Incidents page for the escalation email](/downloads/workflow-automation/incidents/responding-escalation-notification/WA-Responding-Escalation-Notification-Violation-Details-Section-SaaS-Security.png)
[]![Viewing the Additional Information window displaying multiple attributes (i.e., Organization, Division, Phone Number, Project IDs, Termination Date, Worker Type, Organization Hierarchy, Location, User Role, and Manager Information) for the incident that were imported to Workflow Automation via SCIM or CSV](/downloads/workflow-automation/incidents/responding-escalation-notification/WA-Responding-Escalation-Notification-Additional-Information-Window-saasapi.png)
[]![Viewing the Violation Details section on the Incidents page for the escalation email](/downloads/workflow-automation/incidents/responding-escalation-notification/WA-Responding-Escalation-Notification-Violation-Details-Endpoint.png)
[]![Viewing the Additional Information window displaying multiple attributes (i.e., Organization, Division, Phone Number, Project IDs, Termination Date, Worker Type, Organization Hierarchy, Location, User Role, and Manager Information) for the incident that were imported to Workflow Automation via SCIM or CSV](/downloads/workflow-automation/incidents/responding-escalation-notification/WA-Responding-Escalation-Notification-Additional-Information-Window-endpoint.png)
[]![Viewing the Violation Details section on the Incidents page for the escalation email](/downloads/workflow-automation/incidents/responding-escalation-notification/WA-Responding-Escalation-Notification-Violation-Details-Email.png)
[]![Viewing the Additional Information window displaying multiple attributes (i.e., Organization, Division, Phone Number, Project IDs, Termination Date, Worker Type, Organization Hierarchy, Location, User Role, and Manager Information) for the incident that were imported to Workflow Automation via SCIM or CSV](/downloads/workflow-automation/incidents/responding-escalation-notification/WA-Responding-Escalation-Notification-Additional-Information-Window-email.png)
[]![Viewing the Presigned Evidence Link section on the Incidents page for the escalation email](/downloads/workflow-automation/incidents/responding-escalation-notification/WA-Responding-Escalation-Notification-Generate-Presigned-Link.png)
[]![Viewing the Trigger Data section on the Incidents page for the escalation email](/downloads/workflow-automation/incidents/responding-escalation-notification/WA-Responding-Escalation-Notification-View-Trigger-Data.png)
[]![Viewing the Policy section on the Incidents page for the escalation email](/downloads/workflow-automation/incidents/responding-escalation-notification/WA-Responding-Escalation-Notification-Policy-Section-Email.png)
[]![Viewing the Overview section on the Incidents page for the escalation notification](/downloads/workflow-automation/incidents/responding-escalation-notification/WA-Responding-Escalation-Notification-Overview-Section_0.png)