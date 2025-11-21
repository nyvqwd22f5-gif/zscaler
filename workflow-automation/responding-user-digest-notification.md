# Responding to a User Digest Notification
Source: https://help.zscaler.com/workflow-automation/responding-user-digest-notification
PDF: https://help.zscaler.com/pdf/com/en/1447086.pdf

The format of the notification might not be the same as illustrated in this article. It depends upon the digest notification template that your organization configured in the Workflow Automation Admin Portal.
If a channel (e.g., Email, Slack, or Teams) is enabled for the User Digest notification flags on the Account Settings page, Workflow Automation uses a digest notification template to generate and send a user digest notification daily via that channel to all users who have incidents assigned to them. The Workflow Automation Admin Portal provides default user digest notification templates (Digest - Email Template, Digest - Slack Template, and Digest - Teams Template) that you can clone and use for these notifications. These default digest notifications list the number of all open incidents and the number of open incidents that have a high priority. They also provide a link to the Incidents page, where the user can manage these incidents. The digest notifications contain the same information, but the format of the message and where it is delivered varies depending on the channel. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings), [Managing Notification Templates](/workflow-automation/managing-notification-templates), and [Managing Incident and Digest Template Mappings](/workflow-automation/managing-incident-and-digest-template-mappings).
Viewing the User Digest Notification
If you have incidents that are open or in progress, a digest notification (e.g., email, Slack message, or Microsoft Teams message) is sent to you. The digest notification contains the following information:
- The number of open and in-progress incidents that require your attention.
- The number of high-priority incidents that require your attention.
- A link to the Incidents page, where you can view a list of your assigned incidents and also take a survey to justify or approve the incidents. This link is only valid for 24 hours.
The incident count provided in the message is accurate as of the date and time the notification is generated. However, the count is subject to change as new incidents are created, reassigned, or resolved.
The following images are examples of a digest notification email, Slack message, and Microsoft Teams message. The digest notifications contain the same information, but the format of the message is different.
[See image.](#user-digest-notification-images)
Your email settings might tag the digest notification emails as spam and send them to your spam folder. Change your settings to receive the digest notification emails directly in your inbox.
Viewing the Incidents
To view your assigned incidents, click the **View all incidents assigned to me **link provided in the use digest notification. The **Incidents** page appears, listing all the open or in-progress incidents that require your attention. For each incident, you can view the following information:
- **Last Change Date**: The date and time the incident was last changed.
- **Transaction ID**: The transaction ID for the incident.
- **Status**: The status of the incident. Statuses are:
- **New**
- **Investigating**
- **Validating with User**
- **Justification Response Received**
- **Escalated**
- **Action**: The action required for the incident. Actions are:
- **Justify**: When you click this action, you are redirected to the **Justify** page, where you can view the incident details and complete the justification survey for the incident.
- **Approve**: When you click this action, you are redirected to the **Approve** page, where you can view the incident details and complete the approval survey for the incident.
[See image.](#digest-notification-incidents-page)
To view only the incidents where you are the owner, select the **My Incidents** checkbox at the top-left of the page.
Viewing the Incident Details
To view the details of an incident, on the **Incidents** page, click the **Justify **or **Approve** action next to the incident. You are redirected to either the **Justify **or** Approve** page, where you can view the following details:
- [Overview](#overview-details)
- [Violation Details](#violation-details)
- [Policy](#policy-section-email-incidents)
- [Violation Content](#violation-content-section)
Completing the Survey
After reviewing the incident details, you might be required to complete the survey at the end of the Justify** **or** **Approve page to justify, approve, or suggest the next steps for the incident.
To respond, complete the following survey and then click **Submit**:
- **Justification Type**: Select a justification type for the incident. Justification types are **False Positive**, **Manager Approved**, and **Others**.
- **Justification Reason**: Enter a response to proceed with the incident.
[See image.](#justification-survey-image)
Your response is sent to the organization's admin investigating the incident for further review.
[]In the Overview** **section, you can see:
- **Incident ID**: The ID of the incident.
- **Incident Date**: The date on which the incident occurred.
- **Severity**: The severity of the incident. This field is not available for incidents with a Source DLP type of **Email**.
- **Resolution Date**: The date and time when the incident was resolved (i.e., closed). This field only appears for resolved incidents.
[See image.](#overview-image)
[]In the Violation Details section, you can see:
The attributes that appear under the Originating User subsection can vary, depending on what information was imported to Workflow Automation and whether it was imported via the primary user data source of System for Cross-domain Identity Management (SCIM) or a CSV file. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings), [Managing User Attributes](/workflow-automation/managing-user-attributes), and [SAML & SCIM Configuration Guide for Microsoft Entra ID](/zia/saml-scim-configuration-guide-microsoft-entra-id).
- [Incidents of Source DLP Type Inline](#violation-details-inline-incident)
- [Incidents of Source DLP Type SaaS Security](#violation-details-saasapi-incident)
- [Incidents of Source DLP Type Endpoint](#violation-details-endpoint-incident)
- [Incidents of Source DLP Type Email](#violation-details-email-incident)
-
[]Originating User:
- **Name**: The name of the end user responsible for the incident. If you choose the User Name attribute for obfuscation, multiple asterisks appear in this field.
- **Client IP**: The client IP address of the end user. If you choose the Client IP attribute for obfuscation, multiple asterisks appear in this field.
- **Manager Name**: The name of the user's manager. If you choose the Manager Name attribute for obfuscation, multiple asterisks appear in this field.
- **Manager Email**: The email address of the manager. If you choose the Manager Email attribute for obfuscation, multiple asterisks appear in this field.
- **Employee Number**: The employee number of the end user.
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
[See image.](#additional-information-inline)
To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- Policy:
- **Rules**: The DLP rules that the end user violated (e.g., Block-HIPAA).
- **Engines**: The DLP engines associated with the incident.
- **Dictionaries with Match Count**:** **The DLP dictionaries associated with the incident. The number of times the end user's traffic violated a specific dictionary is displayed in brackets (e.g., Medical Information[2]).
- **Other Matched Rules**: Click this field to display the rules that the incident violated, in addition to the primary rules that caused the incident. This field is only available for incidents of Source DLP type **Inline** and **Endpoint**.
The policy fields are only available if the **Hide Policy Details - End User **field is not selected on the **Zscaler DLP Integration** page, the **Zscaler DLP Azure Integration **page, or the **Zscaler DLP GCP Integration **page in the Workflow Automation Admin Portal. To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services](/workflow-automation/configuring-dlp-application-integration-using-amazon-web-services), [Configuring the DLP Application Integration Using Azure](/workflow-automation/configuring-dlp-application-integration-using-azure), and [Configuring the DLP Application Integration Using Google Cloud Platform](/workflow-automation/configuring-dlp-application-integration-using-google-cloud-platform).
- Content:
- **File Name**: The name of the file.
- **File Type**: The type or extension of the file.
- **File MD5**: The 32-character MD5 hash of the file.
- Application:
- **URL**: The URL of the application.
- **Name**: The name of the application.
- **Category**: The category of the application.
The following image is an example of the Violation Details section for an Inline incident. The information that is displayed in the Violation Details section varies depending on the type of incident.
[See image.](#digest-notification-violation-details-section-inline)
-
[]Originating User:
- **Name**: The name of the end user responsible for the incident. If you choose the User Name attribute for obfuscation, multiple asterisks appear in this field.
- **Email**: The email address of the end user responsible for the incident.
- **Manager Name**: The name of the user's manager. If you choose the Manager Name attribute for obfuscation, multiple asterisks appear in this field.
- **Manager Email**: The email address of the manager. If you choose the Manager Email attribute for obfuscation, multiple asterisks appear in this field.
- **Employee Number**: The employee number of the end user.
- **Department**: The department of the end user.
- **Work Location**: The work location of the end user.
- **Additional Information**: Displays the user attributes associated with the end user responsible for the incident. To view the additional user attributes:
- Click the link provided in this field. The **Additional Information** window appears.
-
In the **Additional Information** window, you can view data associated with the incident, such as end user attributes, manager attributes, and addresses. If you choose user attributes for obfuscation, these obfuscated attributes appear with multiple asterisks in this window.
The additional information is fetched from the primary user data source (i.e., CSV or SCIM) you selected during the incident generation.
For example, if you select **CSV** as the primary user data source during the incident generation, the **Additional Information** window displays the user attributes fetched from the imported CSV file. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
The additional information displayed for an incident does not change if you alter the primary user data source. Changing the primary user data source settings impacts only new incidents.
[See image.](#additional-information-saassecurity)
To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- Policy:
- **Rules**: The DLP rules that the end user violated (e.g., Block-HIPAA).
- **Engines**: The DLP engines associated with the incident.
- **Dictionaries with Match Count**:** **The DLP dictionaries associated with the incident. The number of times the end user's traffic violated a specific dictionary is displayed in brackets (e.g., Medical Information[2]).
The policy fields are only available if the **Hide Policy Details** **- End User **field is not selected on the **Zscaler DLP Integration** page, the **Zscaler DLP Azure Integration **page, or the **Zscaler DLP GCP Integration **page in the Workflow Automation Admin Portal. To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services](/workflow-automation/configuring-dlp-application-integration-using-amazon-web-services), [Configuring the DLP Application Integration Using Azure](/workflow-automation/configuring-dlp-application-integration-using-azure), and [Configuring the DLP Application Integration Using Google Cloud Platform](/workflow-automation/configuring-dlp-application-integration-using-google-cloud-platform).
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
[See image.](#digest-notification-violation-details-section-saasapi)
-
[]Originating User:
- **Name**: The name of the end user responsible for the incident. If you choose the User Name attribute for obfuscation, multiple asterisks appear in this field.
- **Manager Name**: The name of the user's manager. If you choose the Manager Name attribute for obfuscation, multiple asterisks appear in this field.
- **Manager Email**: The email address of the manager. If you choose the Manager Email attribute for obfuscation, multiple asterisks appear in this field.
- **Department**: The department of the end user.
- **Device Name**: The name of the end user's device.
- **Device OS**: The operating system of the end user's device.
- **Device Trust Level**: The trust level of the end user's device.
- **Additional Information**: Displays the user attributes associated with the end user responsible for the incident. To view the additional user attributes:
- Click the link provided in this field. The **Additional Information** window appears.
-
In the **Additional Information** window, you can view data associated with the incident, such as end user attributes, manager attributes, and addresses. If you choose user attributes for obfuscation, these obfuscated attributes appear with multiple asterisks in this window.
The additional information is fetched from the primary user data source (i.e., CSV or SCIM) you selected during the incident generation.
For example, if you select **CSV** as the primary user data source during the incident generation, the **Additional Information** window displays the user attributes fetched from the imported CSV file. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
The additional information displayed for an incident does not change if you alter the primary user data source. Changing the primary user data source settings impacts only new incidents.
[See image.](#additional-information-endpoint)
To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- Policy:
- **Rules**: The DLP rules that the end user violated (e.g., Block-HIPAA).
- **Engines**: The DLP engines associated with the incident.
- **Dictionaries with Match Count**:** **The DLP dictionaries associated with the incident. The number of times the end user's traffic violated a specific dictionary is displayed in brackets (e.g., Medical Information[2]).
- **Other Matched Rules**: Click this field to display the rules that the incident violated, in addition to the primary rules that caused the incident. This field is only available for incidents of Source DLP type **Inline** and **Endpoint**.
The policy fields are only available if the **Hide Policy Details - End User **field is not selected on the **Zscaler DLP Integration** page, the **Zscaler DLP Azure Integration **page, or the **Zscaler DLP GCP Integration **page in the Workflow Automation Admin Portal. To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services](/workflow-automation/configuring-dlp-application-integration-using-amazon-web-services), [Configuring the DLP Application Integration Using Azure](/workflow-automation/configuring-dlp-application-integration-using-azure), and [Configuring the DLP Application Integration Using Google Cloud Platform](/workflow-automation/configuring-dlp-application-integration-using-google-cloud-platform).
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
- **ZDP Mode**: The Zscaler Data Protection (ZDP) mode for the incident. ZDP modes can be **Block** or **Exemption**.
- **Expected Action**: The expected action by the ZDP mode for the incident.
- **Confirm Action**: The action that the user took when prompted with a confirmation dialog box for the incident creation.
- **Confirm Justification**: The justification that the user provided during incident creation.
- **Additional Information**: Additional information or notes about the incident.
The following image is an example of the Violation Details section for an Endpoint incident. The information that is displayed in the Violation Details section varies depending on the type of incident.
[See image.](#digest-notification-violation-details-section-endpoint)
[]Originating User:
- **Name**: The name of the end user responsible for the incident. If you choose the User Name attribute for obfuscation, multiple asterisks appear in this field. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- **Email Subject**: The subject of the email.
- **Application Name**: The name of the application used to create the email.
- **Additional Information**: Displays the user attributes associated with the end user responsible for the incident. To view the additional user attributes:
- Click the link provided in this field. The **Additional Information** window appears.
-
In the **Additional Information** window, you can view data associated with the incident, such as end user attributes, manager attributes, and addresses. If you choose user attributes for obfuscation, these obfuscated attributes appear with multiple asterisks in this window.
The additional information is fetched from the primary user data source (i.e., CSV or SCIM) you selected during the incident generation.
For example, if you select **CSV** as the primary user data source during the incident generation, the **Additional Information** window displays the user attributes fetched from the imported CSV file. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
The additional information displayed for an incident does not change if you alter the primary user data source. Changing the primary user data source settings impacts only new incidents.
[See image.](#additional-information-email)
The following image is an example of the Violation Details section for an Email incident. The information that is displayed in the Violation Details section varies depending on the type of incident.
[See image.](#digest-notification-violation-details-section-email)
[]This section is only available for incidents of Source DLP type **Email**. For other types of incidents, the policy information for the incident appears in the Violation Details section.
In the Policy section, you can see:
- **Recipients Email**: The email address of the user who received the incident. If you choose the Recipient Email attribute for obfuscation, multiple asterisks appear in this field. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- **Rule**: The DLP rule that the end user violated.
- **Other Matched Rules**: The other rules that the incident violated in addition to the primary DLP rule that caused the incident.
[See image.](#digest-notification-policy-section-email)
[]The **Generate Presigned Link** field is not available for incidents of Source DLP type **Email**.
In the Violation Content section, you can see:
- [Generate Presigned Link](#generate-presigned-link)
- [View Trigger Data](#view-trigger-data)
[]This field displays the presigned link of the incident and also the link's expiration date and time. It allows you to:
- Before the expiration time, click the presigned link to download the actual data that triggered the incident.
-
Click the **Copy** icon to copy the link for reference.
[See image.](#generate-presigned-link-image)
When justifying an incident, this field enables users to automatically download the actual data that triggered an incident only if the **Hide Evidence Data - End User** field is not selected for the DLP integration. When approving an incident, this field enables approvers to automatically download the actual data that triggered an incident only if the **Hide Evidence Data - Manager/Approver** field is not selected for the DLP integration.
[]When justifying an incident, this field is available only if the **Hide Trigger Data - End User** field is not selected for the DLP integration. When approving an incident, this field is available only if the **Hide Evidence Data - Manager/Approver** field is not selected for the DLP integration.
This field displays the data that triggered the incident. The prefix and suffix for the trigger data are displayed along with the trigger data itself. The actual trigger data portion is highlighted. You can view the DLP dictionaries, DLP rules, and DLP engines associated with the incident and the exact data that violated the DLP policies.
[See image.](#trigger-data-image)
![Viewing an example of an email user digest notification. The user digest notification contains the number of open and in-progress incidents that require your attention and the number of high-priority incidents that require your attention. It also contains a link to the Incidents page, where you can view a list of your assigned incidents and also take a survey to justify or approve the incidents.](/downloads/workflow-automation/incidents/responding-user-digest-notification/WA-DLP-User-Digest-Notification-Email-Example.png)
[]
![Viewing an example of a Slack user digest notification. The user digest notification contains the number of open and in-progress incidents that require your attention and the number of high-priority incidents that require your attention. It also contains a link to the Incidents page, where you can view a list of your assigned incidents and also take a survey to justify or approve the incidents.](/downloads/workflow-automation/incidents/responding-user-digest-notification/WA-Slack-Message-User-Digest-Notification-Image-White.png)
![Viewing an example of a Teams user digest notification. The user digest notification contains the number of open and in-progress incidents that require your attention and the number of high-priority incidents that require your attention. It also contains a link to the Incidents page, where you can view a list of your assigned incidents and also take a survey to justify or approve the incidents.](/downloads/workflow-automation/incidents/responding-user-digest-notification/WA-Digest-Notification-User-Message-Teams.png)
[]![Viewing the list of incidents for the User Digest Notification generated from Workflow Automation](/downloads/workflow-automation/incidents/responding-user-digest-notification/WA-Incidents-PG-From-User-Digest-Not.png)
[]![Viewing the Overview section on the Justify page or Approve page for the user digest notification](/downloads/workflow-automation/incidents/responding-user-digest-notification/WA-Responding-User-Digest-Notification-Overview-Section.png)
[]![Viewing the Violation Details section for an Inline incident when responding to a user digest notification](/downloads/workflow-automation/incidents/responding-user-digest-notification/WA-User-Digest-Not-Violation-Details-Inline.png)
[]![Viewing the Additional Information window displaying multiple attributes (i.e., Organization, Division, Phone Number, Project IDs, Termination Date, Worker Type, Organization Hierarchy, Location, User Role, and Manager Information) for the incident that were imported to Workflow Automation via SCIM or CSV](/downloads/workflow-automation/incidents/responding-user-digest-notification/WA-Responding-User-Digest-Not-Additional-Information-Window-Inline.png)
[]![Viewing the Violation Details section for a SaaS Security incident when responding to a user digest notification](/downloads/workflow-automation/incidents/responding-user-digest-notification/WA-User-Digest-Notification-Violation-Details-Section-SaaS-Security.png)
[]![Viewing the Additional Information window displaying multiple attributes (i.e., Organization, Division, Phone Number, Project IDs, Termination Date, Worker Type, Organization Hierarchy, Location, User Role, and Manager Information) for the incident that were imported to Workflow Automation via SCIM or CSV](/downloads/workflow-automation/incidents/responding-user-digest-notification/WA-Responding-User-Digest-Not-Additional-Information-Window-SaaSSecurity.png)
[]![Viewing the Violation Details section for an Endpoint incident when responding to a user digest notification](/downloads/workflow-automation/incidents/responding-user-digest-notification/WA-User-Digest-Not-Violation-Details-Endpoint.png)
[]![Viewing the Additional Information window displaying multiple attributes (i.e., Organization, Division, Phone Number, Project IDs, Termination Date, Worker Type, Organization Hierarchy, Location, User Role, and Manager Information) for the incident that were imported to Workflow Automation via SCIM or CSV](/downloads/workflow-automation/incidents/responding-user-digest-notification/WA-Responding-User-Digest-Not-Additional-Information-Window-Endpoint.png)
[]![Viewing the Violation Details section for an Email incident when responding to a user digest notification](/downloads/workflow-automation/incidents/responding-user-digest-notification/WA-User-Digest-Not-Violation-Details-Email.png)
[]![Viewing the Additional Information window displaying multiple attributes (i.e., Organization, Division, Phone Number, Project IDs, Termination Date, Worker Type, Organization Hierarchy, Location, User Role, and Manager Information) for the incident that were imported to Workflow Automation via SCIM or CSV](/downloads/workflow-automation/incidents/responding-user-digest-notification/WA-Responding-User-Digest-Not-Additional-Information-Window-Email.png)
[]![Viewing the Policy Section for an Email incident when responding to a user digest notification](/downloads/workflow-automation/incidents/responding-user-digest-notification/WA-User-Digest-Not-Policy-Section-Email.png)
[]![Viewing the Generate Presigned Link when responding to a user digest notification](/downloads/workflow-automation/incidents/responding-user-digest-notification/WA-User-Digest-Not-Generate-Presigned-Link.png)
[]![Viewing the View Trigger Data section when responding to a user digest notification](/downloads/workflow-automation/incidents/responding-user-digest-notification/WA-User-Digest-Not-Trigger-Data.png)
![Viewing the Survey section on the Justify page or Approve page for the user digest notification](/downloads/workflow-automation/incidents/responding-user-digest-notification/WA-User-Digest-Not-Survey-Section.png)
[]