# Managing Monitoring Scope for GCP
Source: https://help.zscaler.com/dspm/managing-monitoring-scope-gcp
PDF: https://help.zscaler.com/pdf/com/en/1498106.pdf

The monitoring scope refers to the GCP projects that are onboarded. When new projects are created in your GCP organization, you can onboard and add new projects to the monitoring scope.
You can also enable autodetection, which allows DSPM to automatically detect and onboard any new projects added in the future. This eliminates the need to manually onboard new projects to DSPM.
Prerequisites
Be assigned either an [Administrator role](/dspm/predefined-roles-and-permissions) or any role with the Configure Monitoring Scope permission in the DSPM Admin Portal.
Managing Monitoring Scope
To add new projects to the monitoring scope:
- Go to **Administration** > **Configuration** >** Cloud Accounts**.
- Select the Cloud Account to which you want to add new target projects.
- Click **Manage**, and then select **Monitoring & Autodetection** from the drop-down menu.
[See image.](#monitor-scope-dropdown)
-
On the **Add to Monitoring Scope** page, select the projects that you want to be monitored.
Enable **Autodetection** so DSPM can automatically detect and onboard any new subscriptions that are added in the future.
[See image.](#add_monitoring_scope)
Click **Next**.
After a project has been added to the monitoring scope, you cannot remove it from the monitoring scope. If you want to stop monitoring a project, you need to delete the project from the DSPM organization. To learn more, see[ Deleting an Onboarded Account](/dspm/deleting-onboarded-account).
- On the **Assign Business Units** page, change the [business unit](/dspm/about-business-units) for the management group if required, then click **Next**.
[See image.](#assign_bu)
- On the **Apply Changes** page:
- [Monitoring Scope](#monitoring_scope)
- [Autodetection](#autodetection)
- Click **Done**.
The new projects are added to the monitoring scope. You can view all the organization's onboarded projects on the [Projects tab](/dspm/viewing-onboarded-account-details).
[]
The onboarding template includes policies and permissions to create custom roles in the GCP organization. This template provides DSPM with the permissions to access the organization.
- [i. In the DSPM Admin Portal](#dspm_admin_portal)
- [ii. On the Local System](#deploy_gcp_onboarding)
[]Click **GCP Onboarding** to download the template as a .zip file.
[See image.](#dwnld_gcp_onboarding)
[]![Download GCP Onboarding Template](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/managing-monitoring-scope-gcp/gcp_ms_dwld_orch_temp.png)
[]Update and run the template in the gcloud using the CLI app:
- Extract the downloaded .zip file to a local directory on your system.
-
Locate the `backend.tf` file within the extracted folder and open it in a text editor.
[See image.](#locate_onboarding_template)
-
Update the file by adding the name of the storage bucket and a preferred prefix where you would like to store the Terraform state files, and then, save and close the file.
[See image.](#edit_oboarding_template)
- Open the Command Prompt or any other CLI app on your local system.
- Switch to the directory containing the downloaded Terraform file.
- Run the following commands:
-
To initialize the working directory and apply the Terraform configuration:
`terraform init`
[See image.](#orch_tf_init)
-
To verify the changes in the Terraform configuration:
`terraform plan`
For **Enter a value**, enter the regions where you want DSPM to monitor and scan data in the following format:
`["region name1", "region name2", "region name3", and so on.]`
DSPM creates resources required for data scanning only in these specified regions.
[See image.](#orch_tf_plan)
-
To run the Terraform script:
`terraform apply`
For **Enter a value**, enter the regions where you want to deploy the template in the following format:
`["region name1", "region name2", "region name3", and so on.]`
[See image.](#orch_tf_apply)
For **Do you want to perform these actions?**, enter `yes` and then press `Enter`.
[See image.](#orch_tf_yes)
[]![Locate the onboarding backend.tf file](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/locate_onboarding_template.png)
[]![Modify the Onboarding Template](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/edit_oboarding_template.png)
[]![Initialise the Terraform](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/orch_tf_init.png)
[]![Orchestrator Terraform Template Plan](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/orch_tf_region.png)
[]![Terraform apply ](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/orch_tf_apply.png)
[]![Confirm Terraform Apply](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/orch_tf_yes.png)
[]Review the list of folders that you selected for autodetection.
[See image.](#enable_autodetection)
[]![Autodetection enabled projects](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/managing-monitoring-scope-gcp/gcp_ms_auto_detect.png)
[]![Monitoring and Autodetection](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/managing-monitoring-scope-gcp/monitoring_autodetection_dropdown.png)
[]![Add Projects to Monitoring Scope](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/managing-monitoring-scope-gcp/add_monitoring_scope.png)
[]![Assign Business Units](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/managing-monitoring-scope-gcp/assign-bu.png)