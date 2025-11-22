# Updating the GCP Service Account
Source: https://help.zscaler.com/dspm/updating-gcp-service-account
PDF: https://help.zscaler.com/pdf/com/en/1498116.pdf

While onboarding a GCP organization, a service account is created within the GCP organization. The service account defines the policies and permissions required for DSPM to access specific resources within the onboarded GCP organization.
If the service account is accidentally deleted, DSPM's access to the onboarded organization is impacted, and all the onboarded projects within the organization move to the [Needs Attention](/dspm/viewing-project-onboarding-status) state. To restore access, you must update the service account details.
Prerequisites
You must be assigned either an [Administrator role](/dspm/predefined-roles-and-permissions) or any role with permission to add accounts in the DSPM Admin Portal.
Updating Service Account:
To update the service account:
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
- Select the GCP cloud account for which you want to update the service account.
-
Click **Manage**, and then select **Update Service Account** from the drop-down menu.
[See image.](#serviceaccount_dropdown)
- Download and run the **Tree Discovery** template:
- [a. In the DSPM Admin Portal](#dl_td_tmpt)
- [b. On the Local System](#update_run_template)
- [c. In the DSPM Admin Portal](#validate_tf_td)
- On the **Roles and Templates** tab, download and run the **GCP Onboarding** template:
- [a. In the DSPM Admin Portal](#download_gcp_onboarding)
- [b. On the Local System](#deploy_gcp_onboarding)
After the template is successfully deployed, DSPM's access to the GCP organization is restored, and the onboarded projects move to the Successfully Configured state.
[]In the **Roles and Templates** tab, click **GCP Onboarding** to download the template as a .zip file.
[See image.](#download_orch_tf)
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
[]![Confirm Terraform Apply](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/orch_tf_yes.png)
[]![Terraform apply ](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/orch_tf_apply.png)
[]![Orchestrator Terraform Template Plan](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/orch_tf_region.png)
[]![Initialise the Terraform](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/orch_tf_init.png)
[]![Modify the Onboarding Template](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/edit_oboarding_template.png)
[]![Locate the onboarding backend.tf file](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/locate_onboarding_template.png)
[]![Download GCP Onboarding Template](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/updating-gcp-service-account/downloadgcptf.png)
[]In the **Update Service Account** section, click **Tree Discovery** to download the template as a .zip file.
[See image.](#serviceaccountpage)
[]Enter the JSON output generated while running the [Terraform apply](#json_out) command, and validate the template deployment.
- In the **Update Service Account **window, paste the JSON output into the **Generated JSON** text field.
-
Click **Validate**.
[See image.](#validate_td)
DSPM verifies the JSON input and validates the template deployment. If the validation is successful, a message appears indicating that the service account was updated.
- Click **Done**.
[]![Update Service Account - Validate page](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/updating-gcp-service-account/updateserviceaccount_validate.png)
[]Update and run the template in the gcloud using the CLI app:
- Extract the downloaded .zip file to a local directory on your system.
- Locate the `backend.tf` file within the extracted folder and open it in a text editor.
[See image.](#locatefile)
- Update the file by adding the name of the storage bucket and a preferred prefix where you would like to store the Terraform state files, then save and close the file.
[See image.](#update_td)
- Launch the installed Google Cloud SDK on your local system.
-
Run the following command to connect to the GCP console:
`gcloud auth application-default login`
[See image.](#run_login_cmd)
You are redirected to a browser to authorize access to the Google Auth Library. Log in to your GCP account to confirm authorization and close it after you have authorized access.
[See image.](#gcloud_login)
After successful authentication, the Google Cloud SDK displays a confirmation message, indicating that your credentials have been saved to a file. These credentials are used by any library that requests Application Default Credentials (ADC).
- Open the Command Prompt or any other CLI app in your local system.
- Switch to the directory containing the downloaded Terraform file.
- Run the following commands:
-
To initialize the working directory and apply Terraform configuration:
`terraform init`
[See image.](#td_terraform_init)
-
To verify the changes in the Terraform configuration:
`terraform plan`
-
To run the Terraform script:
`terraform apply`
[]The command returns a JSON output that includes the project ID, private key ID, private key, client email address, and other credentials to connect the DSPM with the GCP organization.
[See image.](#json_op)
- To access the JSON data later, copy it to a text file and note the `client email` which is part of the JSON output.
[]![Tree Discovery Template JSON Output](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/json_op.png)
[]![Terraform Tree Discovery Initialization](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/td_tf_init.png)
[]![Run GCP login command](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/run_login_cmd.png)
[]![Google Auth Library Login Page](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/gclould_login.png)
[]![Locate the backend.tf Tree Discovery](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/locatefile.png)
[]![Update Tree Discovery backend.tf](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/update_td.png)
[]![Update service account page](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/updating-gcp-service-account/serviceaccountpage.png)
[]![Select Update Service Account](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/updating-gcp-service-account/serviceaccount.png)