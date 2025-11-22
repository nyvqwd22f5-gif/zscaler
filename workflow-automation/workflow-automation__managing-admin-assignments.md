# Managing Admin Assignments
Source: https://help.zscaler.com/workflow-automation/managing-admin-assignments
PDF: https://help.zscaler.com/pdf/com/en/1418066.pdf

You provision admins in the ZIA Admin Portal with either full or restricted workflow access permission to the Workflow Automation Admin Portal. An admin with full workflow access can access certain incident groups or all incident groups based on their assignment. An admin with restricted workflow access is restricted to certain incident groups in the Workflow Automation Admin Portal. To learn more, see [Adding Admin Roles](/zia/adding-admin-roles) and [Adding ZIA Admins.](/zia/adding-zia-admins)
Admin assignments define which incident group permissions an admin with restricted workflow access has. Only admins with full access to Workflow Automation can add assignments for the restricted workflow access admins. Assignments must be added to a restricted workflow access admin before they can manage any incidents on the Incidents page in the Workflow Automation Admin Portal. To learn more, see [Managing Incidents](/workflow-automation/managing-incidents).
Dividing the incident group assignments among the various restricted workflow access admins enables you to control the number of incidents that one admin is managing. It also enables an admin to focus on a specific type of incident. An admin's access to the features of Workflow Automation is defined by the roles assigned to that admin.
Admin assignments also define the following settings:
- Data Loss Prevention (DLP) admin digest notification settings and privacy and security (user data obfuscation) settings for both full and restricted workflow access admins. To learn more, see [Managing Notification Templates](/workflow-automation/managing-notification-templates), [Managing Incident and Digest Template Mappings](/workflow-automation/managing-incident-and-digest-template-mappings), [Responding to a DLP Admin Digest Notification](/workflow-automation/responding-dlp-admin-digest-notification-email), and [Managing Account Settings](/workflow-automation/managing-account-settings).
- Data privacy (generate presigned links and see trigger data) settings for restricted workflow access admins. To learn more, see [Managing DLP Amazon Web Services Application Integrations in Workflow Automation](/workflow-automation/managing-dlp-aws-application-integrations-workflow-automation), [Managing DLP Azure Application Integrations in Workflow Automation](/workflow-automation/managing-dlp-azure-application-integrations-workflow-automation), and [Managing DLP GCP Application Integration in Workflow Automation](/workflow-automation/managing-dlp-gcp-application-integrations-workflow-automation).
Adding Admin Assignments
Before adding admin assignments, you must:
- Provision restricted workflow access admins in the ZIA Admin Portal. To learn more, see [Adding Admin Roles](/zia/adding-admin-roles) and [Adding ZIA Admins.](/zia/adding-zia-admins)
- Configure and map incident groups. To learn more, see [Managing Incident Groups](/workflow-automation/managing-incident-groups) and [Managing Incident Group Mappings](/workflow-automation/managing-incident-group-mappings).
- Configure and map DLP admin digest notification templates. To learn more, see [Managing Notification Templates](/workflow-automation/managing-notification-templates) and [Managing Incident and Digest Template Mappings](/workflow-automation/managing-incident-and-digest-template-mappings).
- Configure the DLP admin digest notification flags and privacy and security (user data obfuscation) settings for your organization. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
- Configure roles and permissions for your organization. To learn more, see [Managing Roles and Permissions](/workflow-automation/managing-roles-and-permissions).
To add an admin assignment:
-
Go to **Setup** > **Admin Assignment**. The **Admin Assignment** page appears, listing all the admin assignments for your organization.
[See image.](#Admins-Page-Add)
- On the **Admin Assignment** page, click **Add More. **The **Add Admin Assignment** window appears.
-
In the **Add Admin Assignment** window:
- **Admin Name**: From the drop-down menu, select an admin's name.
-
**Roles**: From the drop-down menu, select a role for the admin. You can select multiple roles for an admin.
If you are subscribed to ZIdentity, you can assign roles to admins only from the ZIdentity Admin Portal. To learn more, see [About Administrative Entitlements](/zidentity/about-administrative-entitlements).
- **Digest Notification Channel**: Select how this admin receives their DLP admin digest notification. Digest notification channels are **Email**, **Slack**, and **Teams**. Only the channels enabled for your organization on the **Account Settings** page are displayed. The Slack digest notification channel is only available on this window if you have integrated Workflow Automation with Slack, and it is selected on the **Account Settings** page. The Teams Digest notification channel is only available on this window if you have integrated Workflow Automation with Microsoft Teams, and it is selected on the **Account Settings** page. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
- **Incident Priority for Digest**: Select one or more incident priorities to include in the DLP admin digest notification. Priorities are **Critical**, **High**, **Medium**, and **Low**.
- **Digest Frequency**: Select the frequency for the DLP admin digest notifications. Frequencies are **Hourly**, **Daily**, and **Weekly**.
- **Digest Notification**: Enable DLP digest notifications for the admin. If you do not enable this setting, the admin does not receive DLP admin digest notifications. If you enable digest notification, you must select values for the **Digest Notification Channel**, **Incident Priority for Digest**, and **Digest Frequency** fields.
- **Auto Assign Incidents**: Enable this setting to have Workflow Automation automatically assign incidents to this admin as they occur. Otherwise, the admin is not automatically assigned to incidents. By default, it is enabled.
-
**Incident Groups (Edit)**: From the drop-down menu, select one or more incident groups to which you want the restricted workflow access admin to have edit access. With edit access, the admin can perform various actions on the incidents. For full workflow access admins, you can give them edit access to either specific incident groups or **All** (all incident groups).
Workflow Automation automatically assigns incidents belonging to a specific incident group to the restricted workflow access admins who have edit access to that incident group.
- **Incident Groups (View)**: From the drop-down menu, select one or more incident groups to which you want the restricted workflow access admin to have view access. In view-only mode, the admin can only view the incidents. This field is not available for full workflow access admins.
- **Data Privacy Settings**: (Optional) Override the organization's data privacy (generate presigned links and see trigger data) settings for restricted workflow access admins. These settings are not available for full workflow access admins. By default, the organization's data privacy settings appear. To override the data privacy settings for an admin:
-
Under **Data Privacy Settings**, click **Override**. A message appears that asks whether you are sure you want to override the data privacy settings.
[See image.](#override-data-privacy-settings-message)
-
Click **Yes**. The data privacy settings for your organization appear.
[See image.](#data-privacy-settings-section)
-
Enable or disable the **Hide** **Evidence Data** setting. Enable this setting if you do not want the restricted workflow access admin to be able to generate presigned links related to the violation content for incidents on the **Incident Details** page. If you do not enable this setting, the admin can generate presigned links.
This setting takes precedence over the DLP application integration **Hide** **Evidence** **Data - Admin** setting. To learn more, see [Managing DLP Amazon Web Services Application Integrations in Workflow Automation](/workflow-automation/managing-dlp-aws-application-integrations-workflow-automation), [Managing DLP Azure Application Integrations in Workflow Automation](/workflow-automation/managing-dlp-azure-application-integrations-workflow-automation), and [Managing DLP GCP Application Integration in Workflow Automation](/workflow-automation/managing-dlp-gcp-application-integrations-workflow-automation).
-
Enable or disable the **Hide** **Trigger Data** setting. Enable this setting if you do not want the restricted workflow access admin to be able to see trigger data related to the violation content for incidents on the **Incident Details** page. If you do not enable this setting, the admin can see the trigger data.
This setting takes precedence over the DLP application integration **Hide** **Trigger** **Data - Admin** setting. To learn more, see [Managing DLP Amazon Web Services Application Integrations in Workflow Automation](/workflow-automation/managing-dlp-aws-application-integrations-workflow-automation), [Managing DLP Azure Application Integrations in Workflow Automation](/workflow-automation/managing-dlp-azure-application-integrations-workflow-automation), and [Managing DLP GCP Application Integration in Workflow Automation](/workflow-automation/managing-dlp-gcp-application-integrations-workflow-automation).
To reset the data privacy settings back to the organization's settings, click **Reset**.
[See image.](#reset-data-privacy-settings)
-
**Obfuscation Settings**: (Optional) Override the organization's obfuscation settings for the admin. When you select user attributes for obfuscation, the admin cannot see the values of those user attributes associated with incidents on the Incidents, Incident Details, and workflow pages. The obfuscated user attributes appear as several asterisks instead of the actual value for the attribute. For example, if you obfuscate the User Name attribute, the User Name appears as "******" instead of the user's actual name. By default, the organization's obfuscation settings appear. To override the obfuscation settings for an admin:
-
Under **Obfuscation Settings**, click **Override**. A message appears that asks whether you are sure you want to override the obfuscation settings.
[See image.](#override-obfuscation-setting-message)
- Click **Yes**.
-
Select the checkbox next to each user attribute you want to override for this admin. The user attributes you can choose for obfuscation are **User Name**, **User Email**, **Recipient Email**, **Manager Name**, **Client IP**,** Manager Email**, **Device Name**, **Phone Number**, and** Trigger Data**. If you select the **Recipient Email** attribute, the obfuscation applies to the **External Recipients** attribute, the **Internal Recipients **attribute, and the **Triggered Recipients** attribute. If you want to obfuscate all the user attributes, select the **Obfuscate All** checkbox.
To reset the user attributes back to the organization's obfuscation settings, click **Reset**.
[See image.](#reset-obfuscation-settings)
To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
[See image.](#add-admin-assignment-window)
- Click **Add**.
To see the assignments that were added to a restricted workflow access admin, the restricted admin must log out and log in again to the Workflow Automation Admin Portal.
Editing Admin Assignments
To edit an admin assignment:
- Go to **Setup** > **Admin Assignment**.** **The **Admin Assignment** page appears, listing all the admin assignments for your organization.
- (Optional) On the **Admin Assignment** page, use the **Search** field to locate the admin assignment that you want to edit.
- In the **Action** column next to the admin assignment, click the **Edit** icon. The **Edit Admin Assignment** window appears.
- In the **Edit Admin Assignment** window, change any of the fields for the admin assignment.
- Click **Update**.
To delete an admin assignment, on the **Admin Assignment** page, click the **Delete** icon in the **Action** column next to an admin assignment.
Viewing Admin Assignments
To view admin assignments, go to **Setup** > **Admin Assignment**.** **The **Admin Assignment** page appears, listing all the admin assignments for your organization. For admin assignments, you can view the following information:
- **Admin Name**: The name of the admin.
- **Roles**: The roles of the admin. Multiple roles can be assigned to an admin.
- **Incident Groups (Edit)**: The type and name of the incident groups that the restricted workflow access admin has access to edit. For full workflow access admins, the type and name of the incident groups are displayed if they have edit access to specific incident groups. If they have edit access to all incident groups, no values are displayed.
- **Incident Groups (View)**: The type and name of the incident groups that the restricted workflow access admin has access to view only. This field is not available for full workflow access admins.
- **Digest Frequency**: How often the DLP admin digest notification is sent to the admin.
- **Channel**: The channel on which the DLP admin digest notification is sent to the admin.
- **Priority**: The incident priorities included in the DLP admin digest notification sent to the admin.
- **Evidence Data Privacy**: The evidence data privacy setting for the restricted workflow access admin, whether it is enabled or disabled. For full workflow access admins, a hyphen appears.
- **Trigger Data Privacy**: The trigger data privacy setting for the restricted workflow access admin, whether it is enabled or disabled. For full workflow access admins, a hyphen appears.
- **Digest Notification**: The DLP admin digest notification setting for the admin, whether it is enabled or disabled.
[See image.](#Admins-Page-View)
![Viewing existing admin assignments on the Admin Assignment page](/downloads/workflow-automation/setup/managing-admins/WA-Admin-Assignment-Page-Adding_1.png)
[]
[]![Viewing the Add Admin Assignment window](/downloads/workflow-automation/setup/managing-admins/WA-Add-Admin-Assignment-Window_2.png)
[]![Viewing the override data privacy settings message in the Add Admin Assignment window](/downloads/workflow-automation/setup/managing-admins/WA-Add-Admin-Assignment-Window-Override-Data%20Privacy.png)
[]![Viewing the Data Privacy Settings section on the Add Admin Assignment window. This section contains the Hide Evidence Data setting and the Hide Trigger Data setting.](/downloads/workflow-automation/setup/managing-admins/WA-Add-Admin-Assignment-Window-Data-Privacy-Settings.png)
[]![Viewing the Data Privacy Settings section in the Add Admin Assignment window. The Reset link is highlighted in this section.](/downloads/workflow-automation/setup/managing-admins/WA-Add-Admin-Assignment-Window-Reset-Data%20Privacy.png)
[]![Viewing the Override Obfuscation Settings message on the Add Admin Assignment window](/downloads/workflow-automation/setup/managing-admins/WA-Add-Admin-Assignment-Window-Override-Obfuscation-Message.png)
[]![Reset Link in the Obfuscation Settings section in the Add Admin Assignment window](/downloads/workflow-automation/setup/managing-admins/WA-Add-Admin-Assignment-Window-Reset-Obfuscation_1.png)
[]![Viewing existing admin assignments on the Admin Assignment page](/downloads/workflow-automation/setup/managing-admins/WA-Admin-Assignment-Page-Viewing_1.png)