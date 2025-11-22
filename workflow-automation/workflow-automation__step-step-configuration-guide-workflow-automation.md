# Step-by-Step Configuration Guide for Workflow Automation
Source: https://help.zscaler.com/workflow-automation/step-step-configuration-guide-workflow-automation
PDF: https://help.zscaler.com/pdf/com/en/1417806.pdf

Data Protection integration with Workflow Automation is enabled when you subscribe to Data Loss Prevention (DLP). If you have subscriptions to multiple integrated applications of Workflow Automation such as Business Insights and Zscaler Digital Experience (ZDX), you are prompted to select an application when you log in to the Workflow Automation Admin Portal. Select **Data Protection** to manage and configure automated workflows for DLP incidents.
This guide takes you through the configuration steps you need to complete to begin using Workflow Automation for your organization. Because Workflow Automation integrates with Zscaler Internet Access (ZIA), you must set up and configure ZIA and configure the Data Loss Prevention (DLP) policies before you configure Workflow Automation. To learn more, see the [Step-By-Step Configuration Guide for ZIA](/zia/step-step-configuration-guide-zia).
Before you begin configuring Workflow Automation, Zscaler recommends reading the following articles:
- [What Is Workflow Automation?](/zia/what-zscaler-workflow-automation)
- [Accessing and Navigating the Workflow Automation Admin Portal](/zia/accessing-and-navigating-workflow-automation-admin-portal)
- [About Incidents](/zia/about-incidents)
- [Viewing & Managing Incident Details](/zia/viewing-managing-incident-details)
Prerequisites
Ensure that you have permission to access Workflow Automation from the ZIA Admin Portal. If you don't have permission, contact a Super Admin to provide you with the necessary permission.
Configuring Workflow Automation
To configure Workflow Automation, complete the following steps:
- [Step 1: Provision Your Admins in ZIA to Access Workflow Automation](#Step1-Provision-Admins)
- [Step 2: Configure the DLP Application Integration for Your Organization](#Step2-Configure-DLP-Application-Integration)
- [Step 3: Integrate Workflow Automation with Slack](#slack-integration)
- [Step 4: Integrate Workflow Automation with Microsoft Teams](#Microsoft-Teams-Integration)
- [Step 5: Integrate Workflow Automation with a Ticketing Integration Application](#ticketing-application-integration-step)
- [Step 6: Configure Incident Groups in Workflow Automation](#Step3-Configure-Map-Incident-Groups)
- [Step 7: Configure Roles and Permissions for the Admins in Workflow Automation](#Step7-Configure-Roles-Permissions)
- [Step 8: Configure Incident Group Permissions for Restricted Workflow Admins in Workflow Automation](#Step4-Configure-RestrictedAdmin-Permissions)
- [Step 9: Configure Incident Group Priorities in Workflow Automation](#Step5-Incident-Group-Priorities)
- [Step 10: Configure Incident Approvers in Workflow Automation](#Step6-Configure-Approvers)
- [Step 11: Configure Account Settings in Workflow Automation](#Step7-Configure-Account-Settings)
- [Step 12: Configure User Attributes in Workflow Automation](#configure-user-attributes)
- [Step 13: Configure and Map Notification and Survey Templates in Workflow Automation](#Step8-Configure-Templates)
- [Step 14: Configure Labels in Workflow Automation](#step9-configure-labels)
- [Step 15: Configure Workflows in Workflow Automation](#step10-configure-workflows)
- [Step 16. Configure Custom Email Domains in Workflow Automation](#step16-configure-custom-email-domains)
[]To manage incidents in Workflow Automation, admins need to be provisioned in the ZIA Admin Portal with a role that has the **Workflow Access** permission configured. Admins can be configured with full or restricted workflow access to the Workflow Automation Admin Portal.
To provision administrators as applicable, see:
- [About Administrators](/zia/about-administrators)
- [Adding ZIA Admins](/zia/adding-zia-admins)
- [About Role Management](/zia/about-role-management)
- [Adding Admin Roles](/zia/adding-admin-roles)
After the admins have been provisioned with the Workflow Access permission, ensure that they can access the Workflow Automation Admin Portal. To access the Workflow Automation Admin Portal from the ZIA Admin Portal, go to **Administration**. Under Data Loss Prevention (DLP), click **Workflow Automation**. If the admins can access the Workflow Automation Admin Portal, proceed with the next step to configure the DLP application integration in Amazon Web Services (AWS), Google Cloud Platform (GCP), or Microsoft Azure.
[See image.](#Navigation-to-Workflow-Automation)
[]To enable your organization's DLP incident transactions to appear as incidents in the Workflow Automation Admin Portal, you must configure a DLP application integration for your organization. You can configure a DLP application integration using Amazon Web Services, Google Cloud Platform (GCP), or Microsoft Azure.
To configure a DLP application integration, see[ Configuring the DLP Application Integration Using Amazon Web Services](/zia/configuring-dlp-application-integration-using-amazon-web-services), [Configuring the DLP Application Integration Using Azure,](/zia/configuring-dlp-application-integration-using-azure) and [Configuring the DLP Application Integration Using Google Cloud Platform](/workflow-automation/configuring-dlp-application-integration-using-google-cloud-platform).
[](Optional) To use Slack messages for the notifications (user, escalation, and digest) that admins or the application initiate during the incident remediation process, you must integrate Workflow Automation with Slack.
To integrate Workflow Automation with Slack, see [Managing Workflow Automation Integration with Slack](/zia/managing-workflow-automation-integration-slack).
[](Optional) To use Microsoft Teams messages for the notifications (user, escalation, and digest) that admins or the application initiate during the incident remediation process, you must integrate Workflow Automation with Microsoft Teams.
To integrate Workflow Automation with Microsoft Teams, see [Managing Workflow Automation Integration with Microsoft Teams](/zia/managing-workflow-automation-integration-microsoft-teams).
[](Optional) During the remediation process for a data protection incident in Workflow Automation, admins can create and associate a ticket from ServiceNow or Jira Software with the incident. To be able to create and associate a ticket with an incident, you must integrate Workflow Automation with ServiceNow or Jira Software and add the users for those integrations on the Integration Users page in Workflow Automation.
To integrate Workflow Automation with a ticketing integration application (ServiceNow or Jira Software), see:
- [Managing Workflow Automation Integration with ServiceNow](/zia/managing-workflow-automation-integration-servicenow)
- [Managing Workflow Automation Integration with Jira Software](/zia/managing-workflow-automation-integration-jira-software)
- [Managing Integration Users](/zia/managing-integration-users)
[]To assist with the management of incidents that appear on the Incidents page, admins can add and map incident groups. Admins with full workflow access to Workflow Automation can map incident groups to the different properties associated with an incident transaction.
To configure incident groups, see:
- [Managing Incident Groups](/zia/managing-incident-groups)
- [Managing Incident Group Mappings](/zia/managing-incident-group-mappings)
[]Only admins with full access to Workflow Automation can configure roles and assign them to restricted workflow access admins during an admin assignment. Configure roles to complete the admin assignments for DLP admins. For each role, you can assign Edit, View, or None permissions to access and manage different Workflow Automation features.
To configure roles and permissions for DLP admins, see [Managing Roles and Permissions](/workflow-automation/managing-roles-and-permissions).
[]Admins who have been provisioned with the restricted workflow access permission in ZIA need to have their incident group permissions configured in the Workflow Automation Admin Portal. An admin with full access to Workflow Automation configures their incident group permissions.
To configure incident group permissions for restricted workflow access admins in the Workflow Automation Admin Portal, see [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
[]Admins can prioritize the DLP incidents that appear on the Incidents page in the Workflow Automation Admin Portal by assigning a priority to the different incident groups.
To configure incident group priorities, see [Managing Priorities](/zia/managing-priorities).
[]On the Incidents page or the Incident Details page, admins can escalate an incident to an approver who is defined in the Workflow Automation Admin Portal. An approver can be the manager of the end user responsible for the incident or any other individual.
To configure approvers, see [Managing Approvers](/zia/managing-approvers).
[]On the Account Settings page, admins can:
- Enable user and admin digest notifications to be sent on a daily basis to those end users or approvers who have incidents waiting for their response.
- Select the primary data source from which Workflow Automation fetches the user information and the user's unique identifier, an attribute that is used to index a specific user.
- Select the privacy and security user data-obfuscation settings for their organization.
To configure account settings, see [Managing Account Settings](/workflow-automation/managing-account-settings).
[]On the User Attributes page, admins can import the end user attributes as CSV files, from which Workflow Automation fetches the user attributes that display on the Workflow Automation Admin Portal. To view the user attributes imported through a CSV file in the Workflow Automation Admin Portal, you must select CSV as the primary data source and select a unique identifier on the [Account Settings](/zia/managing-account-settings) page.
To configure user attributes, see [Managing User Attributes](/workflow-automation/managing-user-attributes).
[]While investigating an incident, admins can notify the end user who caused the incident and ask for justification for the incident. They can also escalate the incident to an approver, if required. When an admin performs either of these actions for an incident, an email is sent to the end user or approver using a notification template and a survey template that was created in the Workflow Automation Admin Portal. Workflow Automation provides default notification templates and survey templates, but admins can configure custom notification or survey templates, if they choose. After admins define these new custom templates, they must also map them to a DLP Type, Notification Type, and Source Action.
In addition, a notification template is also used for the email digest that can be sent from Workflow Automation on a daily basis.
To configure and map notification and survey templates, see:
- [Managing Notification Templates](/zia/managing-notification-templates)
- [Managing Survey Templates](/zia/managing-survey-templates)
- [Managing Incident and Digest Template Mappings](/zia/managing-incident-and-digest-template-mappings)
[][](Optional) Admins can label the DLP incidents that appear on the Incidents page or the Incident Details page in Workflow Automation by assigning a label to the incident.
To configure labels, see [Managing Labels.](/zia/managing-labels)
[](Optional) Admins can configure workflows to assist them with remediating incidents that occur in their organization. Workflows are automatically triggered for those incidents that match the mapped criteria for the workflows. Workflows can contain one or more actions to be performed against an incident and do not require user intervention.
To configure and map workflows, see:
- [Understanding Workflows in Workflow Automation](/zia/understanding-workflows-workflow-automation)
- [Managing Workflow Templates](/zia/managing-workflow-templates)
- [Managing Workflows](/zia/managing-workflows)
- [Managing Workflow Mappings](/zia/managing-workflow-mappings)
[](Optional) Admins can configure custom email domains for their organization. Workflow Automation generates and sends email notifications for the various actions that you can perform, such as notifying the user of an incident, escalating an incident to an approver or manager, and performing bulk actions. After you configure a custom email domain, Workflow Automation uses that custom email domain as the sender for these email notifications.
To configure custom email domains, see [Managing Custom Email Domains](/workflow-automation/managing-custom-email-domains).
[]![Navigating to the Workflow Automation Admin Portal from the ZIA Admin Portal](/downloads/zia/policies/data-loss-prevention/zscaler-workflow-automation/getting-started/step-step-configuration-guide-workflow-automation/ZIA-WA-Navigation-to-WA-From-ZIAAdminPortal.png)