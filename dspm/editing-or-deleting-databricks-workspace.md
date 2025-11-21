# Editing or Deleting a Databricks Workspace or Account
Source: https://help.zscaler.com/dspm/editing-or-deleting-databricks-workspace
PDF: https://help.zscaler.com/pdf/com/en/1532036.pdf

You can modify or delete a configured [Databricks workspace or account](/dspm/about-service-registration) as required.
The Account registration type is available only for the AWS cloud configuration.
Editing a Databricks Workspace or Account
To edit a Databricks workspace or account:
- Go to **Administration **>** Configuration **>** Service Registration**.
-
On the **Service Registration** page, select the **Databricks **tab.
The Databricks tab provides two views: **Workspace **and **Account**.
- Select the **Workspace** or **Account** button to choose which entry you want to edit.
-
Do one of the following:
-
Click **Actions **(![fa-action.png](/downloads/dspm/administration/unmanaged-database/editing-or-deleting-unmanaged-database/fa-action.png)
), and select **Edit** for the required workspace or account.
[See image.](#databricks-action-edit.png)
-
Click the name of the Databricks workspace or account to view the specific [Databricks workspace or account](/dspm/about-service-registration#databricks-details) details page, then click **Actions**, and select **Edit**.
[See image.](#databricks-details-edit.png)
The **Edit Databricks Workspace** or **Edit Databricks Account** confirmation window appears based on your selection.
- In the confirmation window, read the message and click **Proceed** to continue.
- [Edit Databricks Workspace](#edit-workspace)
- [Edit Databricks Account](#edit-account)
- Click **Save**.
Any changes to the Databricks configuration take effect at the next scheduled scan. To learn more, see [Configuring Scan Rules for Databricks Workspace](/dspm/configuring-scan-rule-databricks-workspace).
[]In the **Edit Databricks Workspace** window, update the editable fields:
- **Client ID** (for AWS only): Update the client identifier issued by the cloud provider.
- **Client Secret ARN** (for AWS only): Update the AWS Secrets Manager ARN that stores the client secret.
- **Connection String** (for AWS and Azure): Update the JDBC connection string to connect DSPM to the Databricks workspace.
- Execute the script in the Databricks workspace by clicking one of the following buttons:
- **Copy Script**: Copy the script to the clipboard for manual execution in the Databricks workspace.
- **Download Script**: Download the script file for offline use or automation.
[]![Edit Databricks Workspace with the necessary information filled for AWS.](/downloads/dspm/administration/unmanaged-database/about-unmanaged-database/db-edit-workspace.png)
[]In the **Edit Databricks Account** window, update the editable fields:
- **Account Information**:
- **Business Unit**: Update the business unit that owns the account or choose **Default** if none applies.
- **DSPM Integration Alias**: Update the DSPM alias for this integration.
- **Authentication Details**:
- **Client ID**: Update the client identifier issued by the cloud provider.
- **Client Secret ARN**: Update the AWS Secrets Manager ARN that stores the client secret.
[]![Edit Databricks Account with the necessary information filled for AWS.](/downloads/dspm/administration/unmanaged-database/about-unmanaged-database/db-edit-account.png)
[]![ Databricks page displaying the action menu options, with an annotation highlighting the Edit option.](/downloads/dspm/administration/unmanaged-database/about-unmanaged-database/ds-sr-databricks-workspace-action-edit.png)
[]![ Databricks details page showing the Actions options, with an annotation for Edit option.](/downloads/dspm/administration/service-registration/databricks/editing-or-deleting-databricks-workspace/ds-sr-databricks-details-edit.png)
Deleting a Databricks Workspace or Account
To delete a Databricks workspace or account:
- Go to **Administration **>** Configuration **>** Service Registration**.
-
On the **Service Registration** page, select the **Databricks **tab.
The Databricks tab provides two views: **Workspace **and **Account**.
- Select the **Workspace** or **Account** button to choose which entry you want to delete.
-
Do one of the following:
-
Click **Actions** (![fa-action.png](/downloads/dspm/administration/unmanaged-database/editing-or-deleting-unmanaged-database/fa-action.png)
), and select **Delete **for the required workspace or account.
[See image.](#img-ds-db-action-delete)
-
Click the name of the Databricks workspace or account to go to a specific [Databricks workspace or account](/dspm/about-service-registration#databricks-details) details page, then click **Actions**, and select **Delete**.
[See image.](#img-ds-db-details-delete)
The **Delete Databricks Workspace** or **Delete Databricks Account **confirmation window appears.
-
In the confirmation window, read the message, and then enter `CONFIRM` in the text box.
[See image.](#img-ds-db-confirm-delete)
- Click **Delete**.
The Databricks workspace or account is deleted from the DSPM Admin Portal.
[]![Databricks page displaying the action menu options, with an annotation highlighting the Delete option.](/downloads/dspm/administration/unmanaged-database/about-unmanaged-database/ds-sr-databricks-workspace-action-delete.png)
[]![Databricks details page showing the Actions options, with an annotation for Delete option.](/downloads/dspm/administration/service-registration/databricks/editing-or-deleting-databricks-workspace/ds-sr-databricks-details-delete.png)
[]![Confirmation window for deleting a Databricks workspace, with an input field to confirm to proceed.](/downloads/dspm/administration/service-registration/databricks/editing-or-deleting-databricks-workspace/ds-db-delete-message.png)