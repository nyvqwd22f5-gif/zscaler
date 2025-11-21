# Responding to an End User Notification
Source: https://help.zscaler.com/workflow-automation/responding-end-user-notification
PDF: https://help.zscaler.com/pdf/com/en/1421056.pdf

The format of the notification and survey might not be the same as illustrated in this article. It depends upon the notification and the survey template that your organization configured in the Workflow Automation Admin Portal.
As an end user, when you make a transaction that violates the Data Loss Prevention (DLP) policies of your organization, a DLP admin can notify you about the incident through an alert notification (e.g., email, Slack message, or Microsoft Teams message). This notification comes from the Workflow Automation Admin Portal, where the organization's admins record and evaluate all incidents. The notification contains an Incident Detail Link associated with the survey that you must complete to justify that incident.
Depending on the severity of that incident, the admin can directly escalate it to your manager or another approver.
Viewing the Notification
When an incident occurs, you receive a notification (e.g., email, Slack message, or Microsoft Teams message) requesting justification. The notification contains the following information:
- The date and time when the incident occurred.
- The Incident Detail Link, where you can view the incident details and also take a survey to justify the incident. This link is only valid for 24 hours.
- The incident ID.
- The hostname or the application of the incident.
- The priority of the incident.
- The note to the user from the admin who initiated the notification. This note appears only if the admin enters a note.
The following images are examples of a user notification sent by email, Slack message, and Microsoft Teams message. The notifications contain the same information, but the format of the message is different.
[See image.](#Email-Notification-Image)
Depending on your email settings, notification emails might be tagged as spam and sent to your spam folder. Change your settings to receive the notification emails directly in your inbox.
Viewing the Incident Details
To view the details of the incident, click the **Incident Detail Link** provided in the user notification. You are redirected to the **Incident** page, where you can view the following details:
- [Overview](#overview-details)
- [Violation Details](#violation-details)
- [Policy](#policy-section-email-incidents)
Completing the Survey
After reviewing the incident details, you might be required to complete a survey at the end of the Incident page to justify your action.
To provide justification, complete the following survey and then click **Submit**:
- **Justification Type**: Select a justification type for the incident. Justification types are **False Positive**, **Manager Approved**, and **Others**.
- **Justification Reason**: Enter a justification reason in detail for the incident.
[See image.](#justification-image)
Your justification response is sent to the organization's admin who is investigating the incident for further review.
[]In the Overview** **section, you can see:
- **Incident ID**: The ID of the incident.
- **Incident Date**: The date on which the incident occurred.
- **Severity**: The severity of the incident. This field is not available for incidents with a Source DLP type of **Email**.
- **Resolution Date**: The date and time when the incident was resolved (i.e., closed). This field only appears for resolved incidents.
[See image.](#overview-image)
[]In the Violation Details section, you can see:
The attributes that appear under the Originating User subsection can vary, depending on how and what information was imported to Workflow Automation through the primary user data source of System for Cross-domain Identity Management (SCIM) or a CSV file. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings), [Managing User Attributes](/workflow-automation/managing-user-attributes), and [SAML & SCIM Configuration Guide for Microsoft Entra ID](/zia/saml-scim-configuration-guide-microsoft-entra-id).
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
- **Department**: The department of the end user.
- **Work Location**: The work location of the end user.
- **Additional Information**: Displays the user attributes associated with the end user responsible for the incident. To view the additional user attributes:
- Click the link provided in this field. The **Additional Information** window appears.
-
In the **Additional Information** window, you can view data associated with the incident such as end user attributes, manager attributes, and addresses. If you choose user attributes for obfuscation, these obfuscated attributes appear with multiple asterisks in this window. To learn more about obfuscation settings, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
The additional information is fetched from the primary user data source (i.e, CSV or SCIM) you selected during the incident generation.
For example, if you select CSV as the primary user data source during the incident generation, the **Additional Information** window displays the user attributes fetched from the imported CSV file. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
The additional information displayed for an incident does not change if you alter the primary user data source. The change of the primary user data source settings impacts only new incidents.
[See image.](#additional-information-inline)
To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- Policy:
- **Rules**: The DLP rules that the end user violated (e.g., Block-HIPAA).
- **Engines**: The DLP engines associated with the incident.
- **Dictionaries with Match Count**:** **The DLP dictionaries associated with the incident. The number of times the end user's traffic violated a specific dictionary is displayed in brackets (e.g., Medical Information[2]).
- **Other Matched Rules**: Click this field to display the rules that the incident violated, in addition to the primary rules that caused the incident. This field is only available for incidents of Source DLP type **Inline** and **Endpoint**.
The policy fields are only available if the **Hide Policy Details - End User **field is not selected on the **Zscaler DLP Integration** page, the **Zscaler DLP Azure Integration** page, or the **Zscaler DLP GCP Integration** page in the Workflow Automation Admin Portal. To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services](/workflow-automation/configuring-dlp-application-integration-using-amazon-web-services), [Configuring the DLP Application Integration Using Azure](/workflow-automation/configuring-dlp-application-integration-using-azure), and [Configuring the DLP Application Integration Using Google Cloud Platform](/workflow-automation/configuring-dlp-application-integration-using-google-cloud-platform).
- Content:
- **File Name**: The name of the file.
- **File Type**: The type or extension of the file.
- **File MD5**: The 32-character MD5 hash of the file.
- Application:
- **URL**: The URL of the application.
- **Name**: The name of the application.
- **Category**: The category of the application
The following image is an example of the Violation Details section for an Inline incident. The information that is displayed in the Violation Details section varies depending on the type of incident.
[See image.](#violation-details-image-inline-incident)
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
In the **Additional Information** window, you can view data associated with the incident such as end user attributes, manager attributes, and addresses. If you choose user attributes for obfuscation, these obfuscated attributes appear with multiple asterisks in this window. To learn more about obfuscation settings, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
The additional information is fetched from the primary user data source (i.e, CSV or SCIM) you selected during the incident generation.
For example, if you select CSV as the primary user data source during the incident generation, the **Additional Information** window displays the user attributes fetched from the imported CSV file. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
The additional information displayed for an incident does not change if you alter the primary user data source. The change of the primary user data source settings impacts only new incidents.
[See image.](#additional-information-saas-security)
To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- Policy:
- **Rules**: The DLP rules that the end user violated (e.g., Block-HIPAA).
- **Engines**: The DLP engines associated with the incident.
- **Dictionaries with Match Count**:** **The DLP dictionaries associated with the incident. The number of times the end user's traffic violated a specific dictionary is displayed in brackets (e.g., Medical Information[2]).
The policy fields are only available if the **Hide Policy Details - End User **field is not selected on the **Zscaler DLP Integration** page, the **Zscaler DLP Azure Integration** page, or the **Zscaler DLP GCP Integration** page in the Workflow Automation Admin Portal. To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services](/workflow-automation/configuring-dlp-application-integration-using-amazon-web-services), [Configuring the DLP Application Integration Using Azure](/workflow-automation/configuring-dlp-application-integration-using-azure), and [Configuring the DLP Application Integration Using Google Cloud Platform](/workflow-automation/configuring-dlp-application-integration-using-google-cloud-platform).
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
[See image.](#violation-details-image-saasapi-incident)
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
In the **Additional Information** window, you can view data associated with the incident such as end user attributes, manager attributes, and addresses. If you choose user attributes for obfuscation, these obfuscated attributes appear with multiple asterisks in this window. To learn more about obfuscation settings, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
The additional information is fetched from the primary user data source (i.e, CSV or SCIM) you selected during the incident generation.
For example, if you select CSV as the primary user data source during the incident generation, the **Additional Information** window displays the user attributes fetched from the imported CSV file. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
The additional information displayed for an incident does not change if you alter the primary user data source. The change of the primary user data source settings impacts only new incidents.
[See image.](#additional-information-endpoint)
To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- Policy:
- **Rules**: The DLP rules that the end user violated (e.g., Block-HIPAA).
- **Engines**: The DLP engines associated with the incident.
- **Dictionaries with Match Count**:** **The DLP dictionaries associated with the incident. The number of times the end user's traffic violated a specific dictionary is displayed in brackets (e.g., Medical Information[2]).
- **Other Matched Rules**: Click this field to display the rules that the incident violated, in addition to the primary rules that caused the incident. This field is only available for incidents of Source DLP type **Inline** and **Endpoint**.
The policy fields are only available if the **Hide Policy Details - End User **field is not selected on the **Zscaler DLP Integration** page, the **Zscaler DLP Azure Integration** page, or the **Zscaler DLP GCP Integration** page in the Workflow Automation Admin Portal. To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services](/workflow-automation/configuring-dlp-application-integration-using-amazon-web-services), [Configuring the DLP Application Integration Using Azure](/workflow-automation/configuring-dlp-application-integration-using-azure), and [Configuring the DLP Application Integration Using Google Cloud Platform](/workflow-automation/configuring-dlp-application-integration-using-google-cloud-platform).
- Content:
- **File Name**: The name of the file.
- **File Type**: The type or extension of the file.
- **File MD5**: The 32-character MD5 hash of the file.
- **File Size**: The size of the file in bytes.
- User Activity:
- **Activity Type**: The type of activity the user performed that caused the incident.
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
[See image.](#violation-details-image-endpoint-incident)
[]Originating User:
- **Name**: The name of the end user responsible for the incident. If you choose the User Name attribute for obfuscation, multiple asterisks appear in this field. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- **Email Subject**: The subject of the email.
- **Application Name**: The name of the application used to create the email.
- **Additional Information**: Displays the user attributes associated with the end user responsible for the incident. To view the additional user attributes:
- Click the link provided in this field. The **Additional Information** window appears.
-
In the **Additional Information** window, you can view data associated with the incident such as end user attributes, manager attributes, and addresses. If you choose user attributes for obfuscation, these obfuscated attributes appear with multiple asterisks in this window. To learn more about obfuscation settings, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
The additional information is fetched from the primary user data source (i.e, CSV or SCIM) you selected during the incident generation.
For example, if you select CSV as the primary user data source during the incident generation, the **Additional Information** window displays the user attributes fetched from the imported CSV file. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
The additional information displayed for an incident does not change if you alter the primary user data source. The change of the primary user data source settings impacts only new incidents.
[See image.](#additional-information-email)
The following image is an example of the Violation Details section for an Email incident. The information that is displayed in the Violation Details section varies depending on the type of incident.
[See image.](#violation-details-image-email-incident)
[]This section is only available for incidents of Source DLP type **Email**. For the other types of incidents, the policy information for the incident appears in the Violation Details section.
In the Policy section, you can see:
- **Recipients Email**: The email address of the recipient who received the incident. If you choose the Recipient Email attribute for obfuscation, multiple asterisks appear in this field. To learn more about user data obfuscation, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- **Rule**: The DLP rule that the end user violated.
- **Other Matched Rules**: The other rules that the incident violated in addition to the primary DLP rule that caused the incident.
[See image](#policy-section-image-email-incident)
[]![Viewing the End User's Notification Email from the Workflow Automation Admin Portal](/downloads/workflow-automation/incidents/responding-end-user-notification/WA-Responding-End-User-Notification-Email-Image.png)
![Viewing a User Notification Slack Message in Slack](/downloads/workflow-automation/incidents/responding-end-user-notification/WA-End-User-Notification-Message-Slack.png)
![Viewing a User Notification Microsoft Teams Message in Microsoft Teams](/downloads/zia/policies/data-loss-prevention/workflow-automation/responding-end-user-notification-email/ZIA-WA-End-User-Notification-Message-Teams.png)
[]![Responding to an End User Notification Using the Survey](/downloads/workflow-automation/incidents/responding-end-user-notification/WA-Responding-End-User-Notification-Survey.png)
[]![Incident Page - Additional Information - Inline](/downloads/workflow-automation/incidents/responding-end-user-notification/WA-Responding-End-User-Notification-Additional-Information-Window-Inline.png)
[]![Incident Page - Inline Violation Details](/downloads/workflow-automation/incidents/responding-end-user-notification/WA-Responding-End-User-Notification-Violation-Details-Section-Inline.png)
[]![Incident Page - Additional Information - SaaS Security](/downloads/workflow-automation/incidents/responding-end-user-notification/WA-Responding-End-User-Notification-Additional-Information-Window-saasapi.png)
[]![Incident Page - SaaS Security Violation Details](/downloads/workflow-automation/incidents/responding-end-user-notification/WA-Responding-End-User-Notification-Violation-Details-Section-SaaS-Security.png)
[]![ Incident Page - Additional Information - Endpoint](/downloads/workflow-automation/incidents/responding-end-user-notification/WA-Responding-End-User-Notification-Additional-Information-Window-endpoint.png)
[]![Incident page - Violation Details Endpoint](/downloads/workflow-automation/incidents/responding-end-user-notification/WA-Responding-End-User-Notification-Violation-Details-Section-Endpoint.png)
[]![Incident Page - Additional Information - Email](/downloads/workflow-automation/incidents/responding-end-user-notification/WA-Responding-End-User-Notification-Additional-Information-Window-email.png)
[]![Incident Page - Email Violation Details](/downloads/workflow-automation/incidents/responding-end-user-notification/WA-Responding-End-User-Notification-Violation-Details-Section-Email.png)
[]![Incident Page - Email Policy Section](/downloads/workflow-automation/incidents/responding-end-user-notification/WA-Responding-End-User-Notification-Policy-Section-Email.png)
[]![End User Notification - Overview Section](/downloads/workflow-automation/incidents/responding-end-user-notification/WA-Responding-End-User-Notification-Overview-Section.png)