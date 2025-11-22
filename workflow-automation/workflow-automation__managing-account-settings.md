# Managing Account Settings
Source: https://help.zscaler.com/workflow-automation/managing-account-settings
PDF: https://help.zscaler.com/pdf/com/en/1418021.pdf

Managing account settings is one of the tasks for configuring Workflow Automation. Admins with access to Workflow Automation can manage the account settings for Workflow Automation. In account settings, admins can:
- Enter the expiration period for the justification links on user and escalation notifications.
- Enable or disable the generation of user digest notifications by channel for their organization, and enter the expiration period for the justification links on the user digest notifications.
- Enable or disable the generation of Data Loss Prevention (DLP) admin digest notifications by channel for their organization, and enter the expiration period for the justification links on the DLP admin digest notifications.
- Specify trusted email domains for approver email addresses.
- Copy the customer Globally Unique Identifier (GUID) for their organization.
- Choose the primary data source for user information.
- Choose the user's unique identifier.
- Choose the privacy and security user data-obfuscation settings for their organization.
- Choose the primary data source for retrieving the user's email address.
On the Account Settings page, you can do the following:
- [Entering Expiration Periods for Justification Links on User and Escalation Notifications](#expiration-periods-justification-links)
- [Enabling Digest Notifications and Entering Expiration Periods for Justification Links on Digest Notifications](#digest-notifications)
- [Adding Trusted Email Domains for Approvers](#approver-domain-mamagement)
- [Copying Customer Information](#copy-customerguid)
- [Selecting a Primary User Data Source](#primary-data-source)
- [Selecting a Unique Identifier](#unique-identifier)
- [Selecting Privacy and Security User Data-Obfuscation Settings](#privacy-and-security)
- [Selecting the Primary Data Source for Retrieving the User Email Address](#select-incident-management-user-email-address)
[]The Approvers Domain Management feature allows you to specify trusted email domains for approver email addresses. This ensures that only authorized email addresses that belong to one of the trusted domains can be added as approver emails on the [Approvers](/workflow-automation/managing-approvers) page. It helps prevent unauthorized or personal email addresses from being added to the approvers.
To enable Approvers Domain Management:
- Go to **Setup** > **Account Settings**. The **Account Settings** page appears.
- On the **Account Settings **page, expand the **Approvers Domain Management **section.
-
Enable **Restrict Approver Email Domains**.
A new section for entering the email domains appears.
- In the new section, enter a trusted email domain.
- Click the **Add** icon to add additional email domains. You can add up to 10 trusted email domains for the approvers.
- Click the **Delete** icon to delete a saved email domain.
- Click **Save**.
To delete all unsaved changes, click **Reset**.
[See image.](#approver-domain-image)
[]Workflow Automation generates user and escalation notifications that contain links for users, managers, and approvers to provide justification for an incident. You can set the number of days after which the justification links expire.
To enter expiration periods for justification links on user and escalation notifications:
- Go to **Setup** > **Account Settings**. The **Account Settings** page appears.
- On the **Account Settings **page, expand the **Notifications **section.
- Click the **End User Notifications** tab.
- In the **Expiration Period** field for the** End User**, **Manager**, and **Approver**, enter the number of days before the justification link expires for recipients in the user and escalation (manager and approver) notifications. If you do not enter an expiration period, one day appears by default. The maximum number of days for an expiration period is 30 days. If you enter a value greater than 30 days, the system automatically changes it to 30 days.
- Click **Save**.
[See image.](#notifications-end-user-notifications-image)
[]Workflow Automation allows you to enable or disable digest notifications by channel (i.e., email, Slack, or Microsoft Teams) for the end users and the DLP admins:
- [User](#digest-notifications-users)
- [Admins](#digest-notifications-admins)
To enable or disable digest notifications:
- Go to **Setup** > **Account Settings**. The **Account Settings** page appears.
- On the **Account Settings **page, expand the **Notifications **section.
-
Click the **Digest Notifications** tab and do the following:
- **End User****s**:
- Enable or disable the channels for the user digest notifications. Channels are **Email**, **Slack**, and **Teams**.
- In the **Expiration Period** field, enter the number of days before the justification link expires in the user digest notifications. If you do not enter an expiration period, the default is one day. The maximum number of days for an expiration period is 30 days. If you enter a value greater than 30 days, the system automatically changes it to 30 days.
- From the **Digest Frequency** drop-down menu, select the frequency for the user digest notification. Frequencies are **Hourly**, **Daily**, and **Weekly**. If you do not enter a digest frequency, the default is daily.
- **Admin**:
- Enable or disable the channels for the DLP admin digest notifications. Channels are **Email**, **Slack**, and **Teams**.
- In the **Expiration Period** field, enter the number of days before the justification link expires for recipients in the DLP admin digest notifications. If you do not enter an expiration period, one day appears by default. The maximum number of days for an expiration period is 30 days. If you enter a value greater than 30 days, the system automatically changes it to 30 days.
The Slack channel and the Teams channel are only available if you have integrated Workflow Automation with Slack and Microsoft Teams, respectively.
- Click **Save**.
[See image.](#notifications-digest-notifications-image)
[]If you enable the user digest notification by channel (i.e., email, Slack, or Microsoft Teams), Workflow Automation uses a digest notification template to generate and send a user digest notification to all the users who have assigned incidents. On the Account Settings page, you can configure how often users receive digest notifications. Workflow Automation provides the following system default digest notification templates that admins can clone for these notifications, or they can create custom digest notification templates:
- Digest - Email Template
- Digest - Slack Template: This template is only available if you integrate Workflow Automation with Slack.
- Digest - Teams Template: This template is only available if you integrate Workflow Automation with Microsoft Teams.
To learn more, see [Managing Notification Templates](/workflow-automation/managing-notification-templates) and [Managing Incident and Digest Template Mappings](/workflow-automation/managing-incident-and-digest-template-mappings).
All system default user digest notifications provide the number of all open incidents and the number of open incidents that have a high priority. They also provide a justification link to an Incidents page where the user can manage these incidents. To learn more, see [Responding to a User Digest Notification](/workflow-automation/responding-user-digest-notification).
[]If you enable the DLP admin digest notification by channel, Workflow Automation uses a DLP admin digest notification template to generate and send a DLP admin digest notification (i.e., email, Slack message, or Microsoft Teams message) to all the admins who have assigned incidents. On the Admins page, admins with full access can configure the DLP admin digest notification frequency and the incident priorities to be included in the digest notification for each admin. Workflow Automation provides the following system default DLP admin digest notification templates that admins can clone for these notifications, or they can create custom DLP admin digest notification templates:
- DLP Admin Digest - Email Template
- DLP Admin Digest - Slack Template: This template is only available if you integrate Workflow Automation with Slack.
- DLP Admin Digest - Teams Template: This template is only available if you integrate Workflow Automation with Microsoft Teams.
To learn more, see [Managing Notification Templates](/workflow-automation/managing-notification-templates), [Managing Incident and Digest Template Mappings](/workflow-automation/managing-incident-and-digest-template-mappings), and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
All system default DLP admin digest notifications provide the number of all new incidents, the number of all open incidents, and the number of state changes. They also provide a justification link to the Incident page where the admins can view and manage these incidents. To learn more, see [Responding to a DLP Admin Digest Notification](/workflow-automation/responding-dlp-admin-digest-notification).
[]When you configure the DLP application integration in Amazon Web Services (AWS), you create a CloudFormation stack in AWS. On the Account Settings page, the required parameters include the Customer GUID and the AWS environment information fields under the Customer Information section. To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services.](/workflow-automation/configuring-dlp-application-integration-using-amazon-web-services)
To copy the customer information:
- Go to **Setup** > **Account Settings**. The **Account Settings** page appears.
- On the **Account Settings** page, expand the **Customer Information **section and do the following:
- Click the **Copy** icon next to the **Customer GUID**, the **AWS Account**, and the **Role Name** to copy customer information.
[See image.](#customer-information-image)
[]Workflow Automation fetches user attributes from two user data sources, System for Cross-domain Identity Management (SCIM) and CSV. You must select a primary user data source, from which Workflow Automation fetches the user attributes that display in the Workflow Automation Admin Portal. After you select your primary user data source, Workflow Automation displays only the user attributes available in that source. If a user attribute is missing, Workflow Automation does not populate that data.
To select the primary user data source:
- Go to **Setup** > **Account Settings**. The **Account Settings** page appears.
- On the **Account Settings** page, expand the **Primary User Data Source** section and select one of the following sources:
- **SCIM**: When you select this option, Workflow Automation displays the user information from the SCIM protocol. This option is only available if you have enabled SCIM provisioning in the ZIA Admin Portal. To learn more, see [Configuring SCIM](/zia/configuring-scim).
- **CSV**: When you select this option, Workflow Automation displays the user information imported from a CSV file.
[See image.](#primary-user-data-source-image)
[]The unique identifier refers to the attribute that is used to index a specific user. Workflow Automation allows you to select either the user's email address or the employee ID as the unique identifier. Selecting a unique identifier helps Workflow Automation to accurately locate and identify a specific user in the primary user data source. You must ensure that the selected unique identifier data is available in the primary user data source.
To select the unique identifier:
- Go to **Setup** > **Account Settings**. The **Account Settings** page appears.
- On the **Account Settings** page, expand the **Unique Attributes** section and select one of the following attributes:
- **Email Address**: The email address of the user in your organization.
- **Employee ID**: The employee ID of the user in your organization.
[See image.](#unique-identifier-image)
If the selected unique identifier is not available in the primary user data source, Workflow Automation uses the other (unselected) unique identifier to identify the user. When neither of the unique identifiers, email address or employee ID, are available in the primary user data source, Workflow Automation fetches that user information from the unselected primary user data source.
[]To protect the privacy of the user information associated with incidents in your organization, you can select the user attributes you want Workflow Automation to obfuscate for those incidents. When you select user attributes for obfuscation, the admin cannot see the values of those user attributes associated with incidents on the Incidents, Incident Details, and workflow pages. The obfuscated user attributes appear as several asterisks instead of the actual value for the attribute. For example, if you obfuscate the User Name attribute, the User Name appears as "******" instead of the user's actual name.
In addition, for individual admins, you can override the user attribute obfuscation settings that you specified for your organization. To learn more, see [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
You cannot search or filter for obfuscated user attributes.
To select privacy and security user attributes for obfuscation:
- Go to **Setup** > **Account Settings**. The **Account Settings** page appears.
- On the **Account Settings **page, expand the **Privacy and Security** section.
-
In the **Privacy and Security** section, select the checkbox next to each user attribute you want the Workflow Automation system to obfuscate. The user attributes you can choose for obfuscation are **User Name**, **User Email**, **Recipient Email**, **Manager Name**, **Client IP**, **Manager Email**, **Device Name**, **Phone Number**, and **Trigger Data**. If you select the **Recipient Email** attribute, the obfuscation applies to the **External Recipients** attribute, the **Internal Recipients **attribute, and the **Triggered Recipients** attribute. If you want to obfuscate all the user attributes, select the **Obfuscate All** checkbox. By default, no attributes are selected for obfuscation.
[See image.](#privacy-and-security-image)
-
Click **Save**.
To change the attribute selections back to their previous settings, click **Reset**.
[]Workflow Automation displays the email address of the user associated with an incident on the Incident Details page. You can choose to have Workflow Automation retrieve and display the user email address from the primary user data source—i.e., SCIM or CSV attributes.
To select the primary data source for retrieving the user email address:
- Go to **Setup** > **Account Settings**. The **Account Settings** page appears.
- On the **Account Settings **page, expand the **Incident Management** section.
-
In the **Incident Management **section, enable **Retrieve User Email from Primary Data Source**.
[See image.](#incident-management-image)
To learn more, see [Viewing & Managing Incident Details.](/workflow-automation/viewing-managing-incident-details)
[]![Viewing the Account Settings page with the Notifications section expanded and displaying the information on the End User Notifications tab. This tab contains Expiration period fields for the justification links on the user and escalation (manager and approver) notifications.](/downloads/workflow-automation/setup/managing-account-settings/WA-Account-Settings-Page-Notifications-End-User-Notifications_0.png)
[]![Viewing the Account Settings page with the Notifications section expanded and displaying the information on the Digest Notifications tab. This tab contains channel options (email, Slack, and Teams) that can be enabled for user and DLP admin digest notifications. It also contains Expiration period fields for the justification links on the user and DLP admin digest notifications and a Digest Frequency field for user digest notifications.](/downloads/workflow-automation/setup/managing-account-settings/WA-Account-Settings-Page-Notifications-Digest-Notifications_3.png)
[]![Account Settings Page - Customer Information Section](/downloads/workflow-automation/setup/managing-account-settings/WA-Account-Settings-Page-Customer-Information.png)
[]![Account Settings Page - Primary User Data Source Section](/downloads/workflow-automation/setup/managing-account-settings/WA-Account-Settings-Page-Primary-User-Data-Source.png)
[]![Account Settings Page - Unique Identifier Section](/downloads/workflow-automation/setup/managing-account-settings/WA-Account-Settings-Page-Unique-Identifier.png)
[]![Account Settings Page - Privacy and Security Section](/downloads/workflow-automation/setup/managing-account-settings/WA-Account-Settings-Page-Privacy-Security-Section_0.png)
[]![Account Settings Page - Incident Management Section](/downloads/workflow-automation/setup/managing-account-settings/WA-Acct-Settings-Page-Incident-Management-Section.png)
![Approvers Domain Management section on the Account Settings page](/downloads/workflow-automation/data-protection/setup/managing-account-settings/WA-managing-account-settings-approver-domain-management.png)
[]