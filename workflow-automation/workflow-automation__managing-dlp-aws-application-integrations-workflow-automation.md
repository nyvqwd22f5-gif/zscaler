# Managing DLP Amazon Web Services Application Integrations in Workflow Automation
Source: https://help.zscaler.com/workflow-automation/managing-dlp-aws-application-integrations-workflow-automation
PDF: https://help.zscaler.com/pdf/com/en/1417866.pdf

Application integration is the step required to connect the source of the DLP incidents (i.e., ZIA) to Workflow Automation. Super admins or admins with Full or Restricted access to Workflow Automation can configure the DLP application integration. Before your organization's DLP incidents are available for review and remediation on the Incidents page in the Workflow Automation Admin Portal, the DLP Amazon Web Services (AWS) application integration must be configured. To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services](/zia/configuring-dlp-application-integration-using-amazon-web-services).
On the Integrations dashboard in the Workflow Automation Admin Portal, admins can:
- [Add DLP AWS Application Integrations](#add-integration)
- [Edit or Delete DLP AWS Application Integrations](#edit-delete-integration)
- [Disable or Enable DLP AWS Application Integrations](#disable-enable-integrations)
- [View DLP AWS Application Integrations](#view-details)
Prerequisites
Ensure that you have successfully created the AWS resources through the creation of a CloudFormation stack in AWS or you have manually created the resources in AWS. Various outputs (IAM Cross-account Role ARN, IAM Cross-account Role External ID, Support Role ARN (if created), SNS Topic ARN, and S3 Bucket Name Prefix) from the stack creation or manually created are required to add a DLP AWS application integration on the Integrations dashboard in Workflow Automation. To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services](/zia/configuring-dlp-application-integration-using-amazon-web-services).
Adding DLP AWS Application Integrations
[]To add a DLP AWS application integration in Workflow Automation:
-
Go to **Setup** > **Integrations**. The **Integrations** dashboard appears, displaying a **DLP** AWS application tile. The **Tile View** icon is selected by default.
[See image.](#integrations-dashboard-card-view-initial-display)
-
(Optional) On the **Integrations **dashboard, change the view format for the dashboard. Click the **List View** icon to view the integrations in a list.
[See image.](#Integrations-Page-List-View-Initial-Display)
- After you select a view option, perform one of the following procedures:
-
In the tile view:
In the DLP AWS application tile, click the **Add** icon. The add **Zscaler DLP Integration** page appears.
- In the list view:
-
Click **Connect** next to the DLP AWS application integration. The **Zscaler DLP Integration** details page appears, displaying a **Configuration Steps** tab and a **Configuration** tab.
[See image.](#Integrations-Dashboard-ListView-Add-Integration)
The **Configuration Steps** tab provides a link to the instructions for configuring the DLP AWS application integration and a link to download the Zscaler template file that you can use to create the CloudFormation stack in AWS.
- On the **Configuration** tab, click **Add New**. The add **Zscaler DLP integration** page appears.
- On the add **Zscaler DLP integration** page, in the **Zscaler DLP Integration** section, enter an **Integration Name**.
- In the **Account Credentials** section:
- **IAM Cross-Account Role ARN**: Copy the IAM Cross-account Role ARN output of the CloudFormation stack and enter it here.
-
**IAM Cross-Account Role External ID**: The IAM Cross-account Role External ID is automatically populated for you and cannot be changed.
This same ID also appears as the **Customer GUID **on the **Account Settings** page in the Workflow Automation Admin Portal. To learn more, see [Managing Account Settings.](/zia/managing-account-settings)
- **Support User Role ARN**: (Optional) If you have created a support role using the CloudFormation stack or you have manually created the support role, copy the Support Role ARN output from the CloudFormation stack and enter it here or enter the Support Role ARN that was manually created. Zscaler Support can assume this role and assist you with troubleshooting any integration configuration issues that you might have in your AWS account. This role is restricted, and cannot access any of the incidents or the data associated with those incidents in your account. Entering a Support User Role ARN is optional.
- In the **Zscaler DLP Integration** section:
- **S3 Bucket Name Prefix**: Copy the S3 Bucket Name Prefix output of the CloudFormation stack and enter it here.
- **SNS Topic ARN**: Copy the SNS Topic ARN output of the CloudFormation stack and enter it here.
- In the Privacy Settings section:
- **Hide Evidence Data - Admin**: Select if you do not want admins to be able to generate presigned evidence links for an incident on the** Incident Details** page. Otherwise, they can generate evidence links.
- **Hide Trigger Data - Admin**: Select if you do not want admins to be able to see the trigger data for an incident on the **Incident Details** page. Otherwise, they can see the trigger data.
- **Hide Policy Details - Admin**: Select if you do not want the admins to be able to view the policy details for the incident on the **Incident Details** page. Otherwise, they are able to view the policy details for the incident.
- **Hide Evidence Data - End User**: Select if you do not want end users to be able to generate presigned evidence links for an incident. Otherwise, they can generate evidence links.
- **Hide Trigger Data - End User**: Select if you do not want end users to be able to see the trigger data for an incident. Otherwise, they can see the trigger data.
- **Hide Policy Details - End User**: Select if you do not want the end users responding to an incident notification to be able to view the policy details for the incident. Otherwise, they are able to view the policy details for the incident.
- **Hide Evidence Data - Manager/Approver**: Select if you do not want the approvers or managers responding to an incident escalation notification to be able to generate presigned evidence links for the incident. Otherwise, they are able to generate evidence links.
- **Hide Trigger Data - Manager/Approver**: Select if you do not want the approvers or managers responding to an incident escalation notification to be able to see the trigger data for the incident. Otherwise, they are able to see the trigger data.
- **Hide Policy Details - Manager/Approver**: Select if you do not want the approvers or managers responding to an incident escalation notification to be able to view the policy details for the incident. Otherwise, they are able to view the policy details for the incident.
[See image.](#Integrations-Dashboard-Card-Add-Integration-2)
If you disable **Hide Evidence Data** or **Hide Trigger Data** in the integration, but you did not enable read access to the S3 bucket when creating the CloudFormation stack, no one can generate evidence links and view trigger data in the Workflow Automation Admin Portal.
-
Click **Validate**. The system validates the account credentials that are entered with the AWS integration. It verifies that the IAM Cross-Account Role ARN entry is valid and it also checks if the format is correct for the SNS Topic ARN. The integration can only be added if it passes validation.
If the validation fails for any reason or if the configuration has been created or updated with the wrong values, the admin must disable and enable the integration after they have corrected the values for the integration.
-
Click **Add**. The **Zscaler DLP Integration** details page appears, displaying the DLP AWS integration under **Connected Accounts** with an **Enabled** status.
[See image.](#Zscaler-DLP-Integration-Details-Page-After-Add)
[]Editing DLP AWS Application Integrations
To edit a DLP AWS application integration in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations **dashboard appears.
- On the **Integrations **dashboard, select the view format for the dashboard. Click the **Tile View** icon to view the integrations displayed in tiles or click the **List View** icon to view the integrations in a list. The **Tile View** icon is selected by default.
- (Optional) On the** Integrations **dashboard, use the **Search** field to locate the DLP AWS Application Integration that you want to edit.
-
Perform one of the following steps:
- In the tile view, under **Connected Apps, **click anywhere on the **DLP** AWS tile.
- In the list view, in the **Connected Apps** section, click **View Details **next to the DLP AWS app integration.
The **Zscaler DLP Integration** details page appears, displaying all the existing DLP AWS app integrations along with their specific statuses (Enabled, Disabled, and Failed) under the **Connected Accounts** section. To display the deleted application integrations, select **Show Deleted Accounts** at the top right of the **Connected Accounts** section.
[See image.](#Integrations-Dashboard-Edit-Integration-1)
-
On the **Zscaler DLP Integration** details page, click the **Edit** icon next to the connected account you want to edit. The edit **Zscaler DLP Integration** page appears.
[See image.](#Integrations-Dashboard-Edit-Integration-2)
- On the edit **Zscaler DLP Integration** page, edit any of the fields that are displayed except for the **IAM-Cross-Account Role External ID** field. For integrations with a Deleted status, you can only edit the data privacy field settings.
-
Click **Validate**.** **The system validates the account credentials that are entered with the AWS integration. It verifies that the IAM Cross-Account Role ARN entry is valid, and it also checks if the format is correct for the SNS Topic ARN. The integration can only be changed if it passes validation.
If the validation fails for any reason or if the configuration has been created or updated with the wrong values, the admin must disable and re-enable the integration after they have corrected the values for the integration.
- Click **Save Changes**.
Deleting DLP AWS Application Integrations
To delete a DLP AWS application integration in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations **dashboard appears.
- On the **Integrations **dashboard, select the view format for the dashboard. Click the **Tile View** icon to view the integrations displayed in tiles or click the **List View** icon to view the integrations in a list. The **Tile View** icon is selected by default.
- (Optional) On the** Integrations **dashboard, use the **Search** field to locate the DLP AWS Application Integration that you want to delete.
-
Perform one of the following steps:
- In the tile view, under **Connected Apps, **click anywhere on the **DLP** AWS tile.
- In the list view, in the **Connected Apps** section, click **View Details **next to the DLP AWS app integration.
The **Zscaler DLP Integration** details page appears, displaying all the DLP AWS app integrations along with their specific statuses (Enabled, Disabled, and Failed) under the **Connected Accounts** section. To display the deleted application integrations, select **Show Deleted Accounts** at the top right of the **Connected Accounts** section.
[See image.](#Integrations-Dashboard-Delete-Integration)
- On the **Zscaler DLP Integration** details page, click the **Edit** icon next to the connected account you want to delete. Only connected accounts with a status of Enabled, Disabled, or Failed can be deleted. The edit **Zscaler DLP Integration** page appears.
- On the edit **Zscaler DLP Integration** page, click **Delete Integration. **The status of the integration changes to Deleted.
[]To disable or enable a DLP AWS application integration in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations **dashboard appears.
- On the **Integrations **dashboard, select the view format for the dashboard. Click the **Tile View** icon to view the integrations displayed in tiles or click the **List View** icon to view the integrations in a list. The **Tile View** icon is selected by default.
- (Optional) On the** Integrations **dashboard, use the **Search** field to locate the DLP AWS Application Integration that you want to disable or enable.
-
Perform one of the following steps:
- In the tile view, under **Connected Apps, **click anywhere on the **DLP** AWS tile.
- In the list view, in the **Connected Apps** section, click **View Details **next to the DLP AWS app integration.
The **Zscaler DLP Integration** details page appears, displaying all the DLP AWS app integrations along with their specific statuses (Enabled, Disabled, and Failed) under the **Connected Accounts** section. To display the deleted application integrations, select **Show Deleted Accounts** at the top right of the **Connected Accounts** section.
[See image.](#Integrations-Dashboard-Disable-Integration)
- On the **Zscaler DLP Integration** details page, click the **Edit** icon next to a connected account with an Enabled status that you want to disable or an account with a Disabled status that you want to enable. The edit **Zscaler DLP Integration** page appears.
- On the edit **Zscaler DLP Integration** page, click **Disable Integration **or** Enable Integration. **The status of the integration changes to Disabled or Enabled.
[]To view DLP AWS application integrations in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations **dashboard appears.
- On the **Integrations **dashboard:
-
Filter the integrations that are displayed on the dashboard. Select **All** to display all the integrations or select **Connected** to display only those integrations that are connected. By default, all integrations are displayed.
[See image.](#Integrations-Dashboard-All-Connected)
-
Change the view format for the dashboard. Select the **Tile View** icon to view the integrations in a tile format or select the **List View** icon to view the integrations in a list format. By default, the dashboard is displayed in the tile view.
[See image.](#Integrations-Dashboard-Card-List-View-Icons)
- View the list of all connected DLP AWS application integrations that have been added to your organization:
In the tile view, under the **Connected Apps** section, you can view the following information:
- App: The application that is associated with the integration. For example, Data Loss Prevention (DLP).
- Account Details: The integration name for each account associated with the integration.
- Status: The status of the accounts for the integration. A green oval is displayed at the top of the tile listing the number of accounts that are connected and the status of **Connected**. This number does not include accounts with a Failed or Deleted status.
[See image.](#Integrations-Dashboard-Viewing-All-Integrations-Card)
In the list view, under the **Connected Apps** section, you can view the following information:
- **App Integration:** The application that is associated with the integration.
- **Account Details**: The integration name for each account associated with the integration.
- **Status**: The status of the accounts for the integration. A green oval is displayed in the field listing the number of accounts that are connected and the status of **Connected. **This number does not include accounts with a Failed or Deleted status.
- **Account Connected**: The number of accounts that are connected.
[See image.](#Integrations-Dashboard-Viewing-All-Connected-List-View)
-
View additional details for the DLP AWS application integrations by performing one of the following steps:
- In the tile view, under **Connected Apps, **click anywhere on the **DLP** AWS tile.
- In the list view, in the **Connected Apps** section, click **View Details **next to the DLP AWS app integration.
The **Zscaler DLP Integration** details page appears, displaying a **Configuration Steps** tab and a **Configuration** tab. On the **Configuration** tab, you can view the list of DLP AWS application integration accounts along with the status of each account and the date when each account was last modified. To display the deleted application integrations, select **Show Deleted Accounts** at the top right of the **Connected Accounts** section.
[See image.](#Integrations-Dashboard-Viewing-Additional-Details)
- On the **Configuration** tab, click the **Edit** icon next to a DLP AWS application integration account to view the specific details for that integration.
[]![Viewing the Integrations Dashboard in Card View with No Integrations Configured](/downloads/workflow-automation/setup/managing-dlp-aws-application-integrations-workflow-automation/WA-Integrations-Dashboard-CardView-Initial-Display.png)
[]![Viewing the Integrations Dashboard in List View with No Integrations Configured](/downloads/workflow-automation/setup/managing-dlp-aws-application-integrations-workflow-automation/WA-Integrations-Dashboard-ListView-Initial-Display.png)
[]![Add Zscaler DLP Integration Page](/downloads/workflow-automation/setup/managing-dlp-aws-application-integrations-workflow-automation/WA-Add-Zscaler-DLP-AWS-Integration-Page.png)
![Adding a Zscaler DLP AWS Integration Using the List View on the Integrations Dashboard](/downloads/workflow-automation/setup/managing-dlp-aws-application-integrations-workflow-automation/WA-Zscaler-DLP-AWS-Integration-Details-Page-LV-After-Connect.png)
[]
[]![Viewing a Zscaler DLP Integration After it was Added on the Zscaler DLP Integration details page](/downloads/workflow-automation/setup/managing-dlp-aws-application-integrations-workflow-automation/WA-AWS-Zscaler-DLP-Integration-Details-Page-Integration-Enabled.png)
[]![Viewing All the Existing Zscaler DLP Integrations on the Zscaler DLP Integration details page](/downloads/workflow-automation/setup/managing-dlp-aws-application-integrations-workflow-automation/WA-AWS-Zscaler-DLP-Integration-Details-Page-Integration-Viewing-All-Integrations.png)
[]![Editing a Zscaler DLP Integration on the Zscaler DLP Integration Page](/downloads/workflow-automation/setup/managing-dlp-aws-application-integrations-workflow-automation/WA-AWS-Edit-Zscaler-DLP-Integration-Page-managing.png)
[]![Viewing All the Existing Zscaler DLP Integrations on the Zscaler DLP Integration details page](/downloads/workflow-automation/setup/managing-dlp-aws-application-integrations-workflow-automation/WA-AWS-Zscaler-DLP-Integration-Details-Page-Integration-Viewing-All-Integrations-Delete.png)
[]![Viewing All the Existing Zscaler DLP Integrations on the Zscaler DLP Integration details page](/downloads/workflow-automation/setup/managing-dlp-aws-application-integrations-workflow-automation/WA-AWS-Zscaler-DLP-Integration-Details-Page-Integration-Viewing-All-Integrations-Disable.png)
[]![Integrations Dashboard - All and Connected Icons](/downloads/workflow-automation/setup/managing-dlp-aws-application-integrations-workflow-automation/WA-Integrations-Dashboard-All-Connected-Icons.png)
[]![Viewing the Card View and List View Icons on the Integrations Dashboard](/downloads/workflow-automation/setup/managing-dlp-aws-application-integrations-workflow-automation/WA-Integrations-Dashboard-ListView-CardView-Icons.png)
[]![Viewing Information that displays in the AWS DLP Card on the Integrations Dashboard](/downloads/workflow-automation/setup/managing-dlp-aws-application-integrations-workflow-automation/WA-AWS-Integrations-Dashboard-Card-Information.png)
[]![Viewing Information that displays in the AWS DLP List View on the Integrations Dashboard](/downloads/workflow-automation/setup/managing-dlp-aws-application-integrations-workflow-automation/WA-AWS-Integrations-Dashboard-ListView-Information.png)
[]![Viewing Details for All the Existing Zscaler DLP Integrations on the Zscaler DLP Integration details page](/downloads/workflow-automation/setup/managing-dlp-aws-application-integrations-workflow-automation/WA-AWS-Zscaler-DLP-Integration-Details-Page-Last-Modified-Date.png)