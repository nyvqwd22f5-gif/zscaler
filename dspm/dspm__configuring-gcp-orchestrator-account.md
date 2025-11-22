# Configuring a GCP Orchestrator Account
Source: https://help.zscaler.com/dspm/configuring-gcp-orchestrator-account
PDF: https://help.zscaler.com/pdf/com/en/1498126.pdf

DSPM regularly scans the data stores of the target projects by leveraging the [orchestrator template](/dspm/understanding-orchestrator) deployed in the GCP orchestrator project while onboarding.
You can change the orchestrator project if the existing orchestrator project is being decommissioned, deleted, or if an incorrect project was selected while [onboarding](/dspm/onboarding-gcp-organization). When you change the orchestrator project, you must run the orchestrator template in the new project. DSPM validates the template deployment and updates the [orchestrator status](/dspm/viewing-orchestrator-status) accordingly.
Until the new orchestrator project is successfully validated, the following changes occur:
- The existing orchestrator is disabled.
- The DSPM connection status moves to the Waiting for Connection state and Configuration status moves to the Pending state.
- The data scans are stopped.
- The target projects move to the Needs Attention state.
Prerequisites
Be assigned either an [administrator ](/dspm/predefined-roles-and-permissions)role or a custom role with the Configure New Orchestrator permission in the DSPM Admin Portal.
Changing Orchestrator Subscription
To change the orchestrator project:
- Go to **Administration** > **Configuration** >** Cloud Accounts**.
- Select the organization to which you want to change the orchestrator subscription.
- Click **Manage**, and then select **Configure New Orchestrator** from the drop-down menu.
[See image.](#config_new_orch_dropdown)
-
In the **New Orchestrator** window, read the caution and then select the **I understand** checkbox.
[See image.](#config_new_orch_cnfm)
- Click **Continue**.
- In the **Configure an Orchestrator project **page:
- Select an orchestrator project on which you want to deploy the DSPM's orchestrator template.
- **Select Orchestrator Region**: Select a region where you want to deploy the orchestrator project.
- **Log Bucket Name**: Enter a unique name for the log bucket. This log bucket will store the activity logs of the target projects. The log bucket is created while deploying the onboarding template. The name must be unique, otherwise DSPM shows an error message.
- Click **Next**.
-
In the Grant Permissions section, download the GCP onboarding template, which includes policies and permissions to create custom roles in the GCP organization, and deploy it on your cloud account. This template provides DSPM with the permissions to access the organization.
Before running the template on the new orchestrator subscription, purge the template that was previously deployed on the existing orchestrator by running the `terraform destroy` command.
- [a. In the DSPM Admin Portal](#dspm_admin_portal)
- [b. On the Local System](#deploy_gcp_onboarding)
-
Click **Done**.
DSPM validates the template deployment every hour by checking the roles that are created and permissions granted.
An error message appears if there is any issue while deploying the template. Rerun the template in the root account. After the template is successfully deployed, the DSPM begins the [data scan](/dspm/about-scan-settings) for the onboarded projects, and you are directed to the [Overview page](/dspm/viewing-project-onboarding-status) to view the status of the onboarded project and orchestrator details.
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
[]![Configure new orchestrator](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/configuring-gcp-orchestrator-account/config_new_orch.png)
[]![Confirm New Orchestrator Configuration](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/configuring-gcp-orchestrator-account/config_new_orch_cnfm.png)