# Managing DLP GCP Application Integrations in Workflow Automation
Source: https://help.zscaler.com/workflow-automation/managing-dlp-gcp-application-integrations-workflow-automation
PDF: https://help.zscaler.com/pdf/com/en/1532120.pdf

Application integration connects the source of Data Loss Prevention (DLP) incidents (i.e., Zscaler Internet Access (ZIA)) to Workflow Automation. Super admins or admins with Full or Restricted access to Workflow Automation can configure the DLP Google Cloud Platform (GCP) application integration. Before your organization's DLP incidents are available for review and remediation on the Incidents page in the Workflow Automation Admin Portal, you must configure DLP GCP application integration. To learn more, see [Configuring the DLP Application Integration Using Google Cloud Platform](/workflow-automation/configuring-dlp-application-integration-using-google-cloud-platform).
On the Integrations dashboard in the Workflow Automation Admin Portal, admins can:
- [Add DLP GCP Application Integrations](#add-integration)
- [Edit or Delete DLP GCP Application Integrations](#edit-delete-integration)
- [Disable or Enable DLP GCP Application Integrations](#disable-enable-integrations)
- [View DLP GCP Application Integrations](#view-details)
Prerequisites
Ensure that you have successfully [created cloud resources in GCP](/workflow-automation/configuring-dlp-application-integration-using-google-cloud-platform). Various outputs (client_email, private_key, project_id) from the service account key creation are required to add a DLP GCP application integration in Workflow Automation.
Adding DLP GCP Application Integrations
[]To add a DLP GCP application integration in Workflow Automation:
-
Go to **Setup** > **Integrations**. The **Integrations** dashboard appears, displaying a **DLP** **GCP** application tile. The **Tile View** icon is selected by default.
[See image.](#integrations-dashboard-card-view-initial)
-
(Optional) On the **Integrations **dashboard, change the view format for the dashboard. Click the **List View** icon to view the integrations in a list.
[See image.](#integrations-dashboard-list-view-initial)
- After you select a view option, perform one of the following procedures:
-
In the tile view:
In the DLP GCP application tile, click the **Add** icon. The add **Zscaler DLP GCP Integration** page appears.
- In the list view:
-
Click **Connect** next to the DLP GCP application integration. The **Zscaler DLP GCP Integration** details page appears, displaying a **Configuration Steps** tab and a **Configuration** tab.
The **Configuration Steps** tab provides instructions for configuring a DLP GCP application integration and a link to download the Zscaler template file.
-
On the **Configuration** tab, click **Add New**. The add **Zscaler DLP GCP Integration** page appears.
[See image.](#zscaler-gcp-application-integration-page-initial)
- On the add **Zscaler DLP GCP Integration** page, in the **Zscaler DLP GCP Integration** section, enter the following:
- **Integration Name**: Enter a name for the integration.
- **Project ID**: From the JSON key downloaded from the GCP console, copy the `project_id` for the DLP integration and enter it here.
- **Private Key**: From the JSON key downloaded from the GCP console, copy the `private_key` for the DLP integration and enter it here.
- **Client Email**: From the JSON key downloaded from the GCP console, copy the `client_email` for the DLP integration and enter it here.
- **Prefix for Bucket and Topic**: Enter a prefix for the storage bucket and topic.
-
In the **Privacy Settings** section:
- **Hide Evidence Data - Admin**: Select if you do not want admins to be able to generate presigned evidence links for an incident on the** Incident Details** page. Otherwise, they can generate evidence links.
- **Hide Trigger Data - Admin**: Select if you do not want admins to be able to see the trigger data for an incident on the **Incident Details** page. Otherwise, they can see the trigger data.
- **Hide Policy Details - Admin**: Select if you do not want admins to be able to view the policy details for the incident on the **Incident Details** page. Otherwise, they can view the policy details for the incident.
- **Hide Evidence Data - End User**: Select if you do not want end users to be able to generate presigned evidence links for an incident. Otherwise, they can generate evidence links.
- **Hide Trigger Data - End User**: Select if you do not want end users to be able to see the trigger data for an incident. Otherwise, they can see the trigger data.
- **Hide Policy Details - End User**: Select if you do not want end users responding to an incident notification to be able to view the policy details for the incident. Otherwise, they can view the policy details for the incident.
- **Hide Evidence Data - Manager/Approver**: Select if you do not want approvers or managers responding to an incident escalation notification to be able to generate presigned evidence links for the incident. Otherwise, they can generate evidence links.
- **Hide Trigger Data - Manager/Approver**: Select if you do not want approvers or managers responding to an incident escalation notification to be able to see the trigger data for the incident. Otherwise, they can see the trigger data.
- **Hide Policy Details - Manager/Approver**: Select if you do not want approvers or managers responding to an incident escalation notification to be able to view the policy details for the incident. Otherwise, they can view the policy details for the incident.
[See image.](#add-zscaler-dlp-gcp-integration-page)
If you disable **Hide Evidence Data** or **Hide Trigger Data** for the integration, but you did not enable read access to the storage accounts when creating the cloud resources, no one can generate evidence links or view trigger data in the Workflow Automation Admin Portal.
-
Click **Validate**. The system validates the account credentials that are entered with the GCP integration. You can only add the integration if it passes validation.
If the validation fails for any reason, or if you created or updated the configuration with the wrong values, you must disable the integration, correct the values for it, and re-enable the integration.
- Click **Add**. The **Zscaler DLP GCP Integration** details page appears, displaying the DLP integration under **Connected Accounts** with an **Enabled** status.
[]Editing DLP GCP Application Integrations
To edit a DLP GCP application integration in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations **dashboard appears.
- On the **Integrations **dashboard, select the view format for the dashboard. Click the **Tile View** icon to view the integrations in tiles or click the **List View** icon to view the integrations in a list. The **Tile View** icon is selected by default.
- (Optional) On the** Integrations **dashboard, use the **Search** field to locate the DLP GCP application integration that you want to edit.
-
Perform one of the following steps:
- In the tile view, click anywhere on the **DLP GCP** tile under **Connected Apps**.
- In the list view, click **View Details **next to the DLP GCP app integration in the **Connected Apps** section.
The **Zscaler DLP GCP Integration** details page appears, displaying all the DLP GCP app integrations along with their statuses (Enabled, Disabled, or Failed) in the **Connected Accounts** section. To display the deleted application integrations, enable **Show Deleted Accounts** in the top right of the **Connected Accounts** section.
[See image.](#add-zscaler-dlp-gcp-configuration-tab)
-
On the **Zscaler DLP GCP Integration** details page, click the **Edit** icon next to the connected account you want to edit. The edit **Zscaler DLP GCP Integration** page appears.
[See image.](#gcp-connected-accounts-edit-icon)
-
On the edit **Zscaler DLP GCP Integration** page, edit any of the fields. For integrations with a Deleted status, you can only edit the data privacy field settings.
[See image.](#Integrations-Dashboard-Edit-Integration-2)
-
Click **Validate**. The system validates the account credentials that are entered with the GCP integration. You can only add the integration if it passes validation.
If the validation fails for any reason, or if the configuration has been created or updated with the wrong values, you must disable and re-enable the integration after you correct the values for the integration.
- Click **Save Changes**.
Deleting DLP GCP Application Integrations
To delete a DLP GCP application integration in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations **dashboard appears.
- On the **Integrations **dashboard, select the view format for the dashboard. Click the **Tile View** icon to view the integrations in tiles or click the **List View** icon to view the integrations in a list. The **Tile View** icon is selected by default.
- (Optional) On the** Integrations **dashboard, use the **Search** field to locate the DLP GCP application integration that you want to delete.
-
Perform one of the following steps:
- In the tile view, click anywhere on the **DLP GCP** tile under **Connected Apps**.
- In the list view, click **View Details **next to the DLP GCP app integration in the **Connected Apps** section.
The **Zscaler DLP GCP Integration** details page appears, displaying all the DLP GCP app integrations along with their statuses (Enabled, Disabled, or Failed) under the **Connected Accounts** section. To display the deleted application integrations, enable **Show Deleted Accounts** in the top right of the **Connected Accounts** section.
-
On the **Zscaler DLP GCP Integration** details page, click the **Edit** icon next to the connected account you want to delete. Only connected accounts with a status of Enabled, Disabled, or Failed can be deleted. The edit **Zscaler DLP GCP Integration** page appears.
[See image.](#Integrations-Dashboard-edit-icon-delete)
-
On the edit **Zscaler DLP GCP Integration** page, click **Delete Integration. **The status of the integration changes to **Deleted**.
[See image.](#delete-integration-option-image)
[]To disable or enable a DLP GCP application integration in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations **dashboard appears.
- On the **Integrations **dashboard, select the view format for the dashboard. Click the **Tile View** icon to view the integrations displayed in tiles or click the **List View** icon to view the integrations in a list. The **Tile View** icon is selected by default.
- (Optional) On the** Integrations **dashboard, use the **Search** field to locate the DLP GCP application integration that you want to disable or enable.
-
Perform one of the following steps:
- In the tile view, click anywhere on the **DLP** **GCP** tile under **Connected Apps**.
- In the list view, click **View Details **next to the DLP GCP app integration in the **Connected Apps** section.
The **Zscaler DLP GCP Integration** details page appears, displaying all the DLP GCP app integrations along with their statuses (Enabled, Disabled, or Failed) under the **Connected Accounts** section. To display the deleted application integrations, enable **Show Deleted Accounts** in the top right of the **Connected Accounts** section.
-
On the **Zscaler DLP GCP Integration** details page, click the **Edit** icon next to a connected account with an **Enabled** status that you want to disable or an account with a **Disabled** status that you want to enable. The edit **Zscaler DLP GCP Integration** page appears.
[See image.](#Integrations-Dashboard-Disable-Integration)
-
On the edit **Zscaler DLP GCP Integration** page, click **Disable Integration **or** Enable Integration. **The status of the integration changes to **Disabled** or **Enabled**.
[See image.](#disable-integration-option-image)
[]To view DLP GCP application integrations in Workflow Automation:
- Go to **Setup** > **Integrations**. The **Integrations **dashboard appears.
- On the **Integrations **dashboard:
-
Filter the integrations that are displayed on the dashboard. Select **All** to display all the integrations or select **Connected** to display only those integrations that are connected. By default, all integrations are displayed.
[See image.](#Integrations-Dashboard-All-Connected)
-
Change the layout of the dashboard. Click the **Tile View** icon to view the integrations in tiles or click the **List View** icon to view the integrations in a list. By default, the dashboard is displayed in the tile view.
[See image.](#Integrations-Dashboard-Card-List-View-Icons)
-
View the list of all DLP GCP connected application integrations that have been added to your organization:
In the tile view, under the **Connected Apps** section, you can view the following information:
- The application that is associated with the integration. For example, Data Loss Prevention (DLP) GCP.
- The integration name for each account associated with the integration.
- The status of the accounts for the integration. A green oval is displayed at the top of the tile listing the number of accounts that are enabled and the status of **Connected**. This number does not include accounts with a Failed or Deleted status.
[See image.](#Integrations-Dashboard-Viewing-All-Integrations-Card)
In the list view, under the **Connected Apps** section, you can view the following information:
- **App Integration:** The application that is associated with the integration. For example, DLP GCP.
- **Account Details**: The integration name for each account associated with the integration.
- **Status**: The status of the accounts for the integration. A green oval is displayed in the field listing the number of accounts that are enabled and the status of **Connected. **This number does not include accounts with a Failed or Deleted status.
- **Account Connected**: The number of accounts that are connected.
[See image.](#Integrations-Dashboard-Viewing-All-Connected-List-View)
-
View additional details for the DLP GCP application integrations by performing one of the following steps:
- In the tile view, click anywhere on the **DLP** **GCP** tile under **Connected Apps**.
- In the list view, click **View Details** next to the DLP GCP application integration in the **Connected Apps** section.
The **Zscaler DLP GCP Integration** details page appears, displaying a **Configuration Steps** tab and a **Configuration** tab. On the **Configuration** tab, you can view the list of DLP GCP application integration accounts along with the status of each account, and the date when each integration account was last modified. To display the deleted application integrations, select **Show Deleted Accounts** at the top-right of the **Connected Accounts** section.
[See image.](#Integrations-Dashboard-Viewing-Additional-Details)
- On the **Configuration** tab, click the **Edit** icon next to a DLP GCP application integration account to view the details for that integration.
[]![Viewing the Integrations Dashboard in Tile View with no integrations configured](/downloads/workflow-automation/data-protection/setup/managing-dlp-gcp-application-integrations-workflow-automation/WA-managing-DLP-GCP-integrations-connected-apps-tile.png)
[]![Viewing the Integrations Dashboard in List View with no integrations configured](/downloads/workflow-automation/data-protection/setup/managing-dlp-gcp-application-integrations-workflow-automation/WA-managing-DLP-GCP-integrations-connected-apps-view-list.png)
[]![Viewing the Zscaler DLP GCP Integration details page with no integrations configured ](/downloads/workflow-automation/data-protection/setup/managing-dlp-gcp-application-integrations-workflow-automation/WA-managing-DLP-GCP-integrations-add-new-configuration.png)
[]![Adding a Zscaler DLP GCP Integration on the add Zscaler GCP DLP Integration Page in the Workflow Automation Admin Portal](/downloads/workflow-automation/data-protection/setup/managing-dlp-gcp-application-integrations-workflow-automation/WA-managing-DLP-GCP-integrations-add-zscaler-dlp-gcp-integration.png)
[]![Zscaler DLP GCP Integration page displaying connected accounts with enabled and deleted status](/downloads/workflow-automation/data-protection/setup/managing-dlp-gcp-application-integrations-workflow-automation/WA-managing-DLP-GCP-integrations-show-deleted-accounts.png)
![Zscaler DLP GCP Integration page displaying the Edit icon](/downloads/workflow-automation/data-protection/setup/managing-dlp-gcp-application-integrations-workflow-automation/WA-managing-DLP-GCP-integrations-edit-enabled-app.png)
[]
[]![Editing a Zscaler DLP GCP integration on the edit Zscaler GCP DLP Integration page in the Workflow Automation Admin Portal](/downloads/workflow-automation/data-protection/setup/managing-dlp-gcp-application-integrations-workflow-automation/WA-managing-DLP-GCP-integrations-editing-contents-enabled-application.png)
[]![Editing an integration to enable or disable on the Zscaler DLP GCP Integration details page](/downloads/workflow-automation/data-protection/setup/managing-dlp-gcp-application-integrations-workflow-automation/WA-managing-DLP-GCP-integrations-deleting-edit-icon.png)
![Deleting a Zscaler DLP GCP Integration on the edit Zscaler GCP DLP Integration page in the Workflow Automation Admin Portal](/downloads/workflow-automation/data-protection/setup/managing-dlp-gcp-application-integrations-workflow-automation/WA-managing-DLP-GCP-integrations-delete-integration-button.png)
[]
[]![Editing an integration to enable or disable on the Zscaler DLP GCP Integration details page](/downloads/workflow-automation/data-protection/setup/managing-dlp-gcp-application-integrations-workflow-automation/WA-managing-DLP-GCP-integrations-disabling-integration-edit-icon.png)
![Disabling a Zscaler DLP GCP Integration on the edit Zscaler GCP DLP Integration page in the Workflow Automation Admin Portal](/downloads/workflow-automation/data-protection/setup/managing-dlp-gcp-application-integrations-workflow-automation/WA-managing-DLP-GCP-integrations-disable-integration-button.png)
[]
[]![Viewing All and Connected icons on the Integrations Dashboard](/downloads/workflow-automation/data-protection/setup/managing-dlp-gcp-application-integrations-workflow-automation/WA-managing-DLP-GCP-integrations-all-connected-icons.png)
[]![Viewing the Tile View and List View icons on the Integrations Dashboard](/downloads/workflow-automation/data-protection/setup/managing-dlp-gcp-application-integrations-workflow-automation/WA-managing-DLP-GCP-integrations-list-tile-view.png)
[]![Viewing all DLP GCP Integrations using the Tile View on the Integrations Dashboard in Workflow Automation Admin Portal](/downloads/workflow-automation/data-protection/setup/managing-dlp-gcp-application-integrations-workflow-automation/WA-managing-DLP-GCP-integrations-gcp-account-details-tile-view.png)
[]![Viewing all DLP GCP Integrations in the List View on the Integrations Dashboard in the Workflow Automation Admin Portal](/downloads/workflow-automation/data-protection/setup/managing-dlp-gcp-application-integrations-workflow-automation/WA-managing-DLP-GCP-integrations-gcp-account-details-list-view.png)
[]![Viewing last modified details for DLP GCP Integrations on the Zscaler DLP GCP Integration details page in the Workflow Automation Admin Portal](/downloads/workflow-automation/data-protection/setup/managing-dlp-gcp-application-integrations-workflow-automation/WA-managing-DLP-GCP-integrations-gcp-account-last-modified-configuration-tab.png)