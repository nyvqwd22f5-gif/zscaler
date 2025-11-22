# Onboarding a GCP Organization
Source: https://help.zscaler.com/dspm/onboarding-gcp-organization
PDF: https://help.zscaler.com/pdf/com/en/1498091.pdf

You can onboard a Google Cloud Platform (GCP) account and its associated projects to DSPM. DSPM monitors and scans the Cloud Storage buckets in the onboarded projects to identify sensitive data, misconfigurations, vulnerabilities, and more.
Onboarding Workflow
The onboarding process is illustrated in the following image:
[See image.](#gcp-onboarding-process)
[]![The GCP onboarding workflow represented in a flow chart.](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/GCP-Onboarding.png)
[]Prerequisites
Before onboarding the GCP organization, ensure you have completed the following:
- Required Access and Roles
- You must have Super Admin access to the Google Admin console.
- You must have a GCP [Organization Administrator role](/dspm/predefined-roles-and-permissions) and an owner role.
- Install Required Tools
- gcloud CLI to connect to the Google Cloud project if you are deploying the template using gcloud CLI. To learn more, refer to the [Google Cloud documentation](https://cloud.google.com/sdk/docs/install).
- Terraform CLI v1.7.5 or later to run the Terraform on a Windows system. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/developer/terraform/quickstart-configure).
- Enable Debug Logging (optional but recommended for troubleshooting). [Click to view the instructions.](#debug-logging)
- Create a Custom Role in Google Admin Console. [Click to view the instructions.](#create_role)
- Override Service Account Key Creation Policy. [Click to view the instructions.](#overridepolicy)
- Identify a GCP project that has the required roles and which is linked to a billing account to deploy the orchestrator template.
- Enable the required GCP APIs in the selected GCP project. [Click to view the list of required APIs.](#gcpapis)
Zscaler DSPM leverages the below OAuth scopes for API authentication:
- https://www.googleapis.com/auth/cloud-platform
- https://www.googleapis.com/auth/userinfo.email
- https://www.googleapis.com/auth/admin.directory.user.readonly
- https://www.googleapis.com/auth/admin.directory.group.readonly
- https://www.googleapis.com/auth/admin.directory.group.member.readonly
- https://www.googleapis.com/auth/admin.directory.domain.readonly
[]Run the following commands to enable the debug logs:
-
PowerShell
`$env:TF_LOG="TRACE"
$env:TF_LOG_PATH="<filepath>filename.log"`
-
Bash
`export TF_LOG="TRACE"
$ export TF_LOG_PATH="<filepath>filename.log"`
[]By default, the disable service account key creation policy prevents you from creating a service account key. Override the `Disable service account key creation` policy for the project where you want to create the service account.
- Go to the Google Cloud console and go to [Organization policies](https://console.cloud.google.com/iam-admin/orgpolicies).
-
Select the organization from the project picker.
[See image.](#projectpicker)
-
Search for `Disable service account key creation` and click **Disable service account key creation**.
[See image.](#search_serviceaccountkey)
-
On the **Policy for Disable service account key creation** page, click **MANAGE POLICY**.
[See image.](#managepolicy)
- Under the **Policy source** section, select **Override parent's policy**.
-
Under the **Rules** section, click **ADD A RULE**.
[See image.](#addrule)
- In the **New rule** window, under the **Enforcement** section, select **Off**.
-
Click **Done**.
[See image.](#newrule)
-
Click **SET POLICY** to apply the changes.
[See image.](#setpolicy)
Ensure the status of `Disable service account key creation` policy is set to **Not enforced**.
[See image.](#validatepolicy)
-
[]Run the following command on Google Cloud Shell or gcloud CLI:
`gcloud organizations describe <ORG_ID>`
Replace `<ORG_ID>` with your organization ID, which is required to get the `directoryCustomerId`.
-
Copy the `directoryCustomerId` value from the output.
[See image.](#gshell)
- Go to the [Google Admin SDK Directory](https://developers.google.com/admin-sdk/directory/reference/rest/v1/roles/insert).
- Click the **API** tag in the right panel and paste the copied `directoryCustomerId` into the **customer** string.
-
Copy the following request provided and paste it into the **Request body** field.
`{
"roleName": "role_name",
"rolePrivileges": [
{
"privilegeName": "DOMAIN_MANAGEMENT",
"serviceId": "00haapch16h1ysv"
},
{
"privilegeName": "GROUPS_RETRIEVE",
"serviceId": "00haapch16h1ysv"
},
{
"privilegeName": "USERS_RETRIEVE",
"serviceId": "00haapch16h1ysv"
}
]
}`
Replace `role_name` with a desired name for the new role.
-
Click **Execute**.
You are prompted to log in again. You can see the JSON output that includes the newly created role.
`
{
"kind": "admin#directory#role",
"etag": "\"0A0Bc2deFgHi\"",
"roleId": "4123456782",
"roleName": "role_name",
"roleDescription": "",
"rolePrivileges": [
{       "privilegeName": "DOMAIN_MANAGEMENT",       "serviceId": "00abcdef16g1hij"     }
,
{       "privilegeName": "GROUPS_RETRIEVE",       "serviceId": "00abcdef16g1hij"     }
,
{       "privilegeName": "USERS_RETRIEVE",       "serviceId": "00abcdef16g1hij"     }
],
"isSystemRole": false,
"isSuperAdminRole": false
}`
[See image.](#api-body)
-
Go to the [Google Admin console](https://admin.google.com/ac/roles), search for the newly created role, then click **View privileges** to see the assigned permissions.
[See image.](#view_privileges)
The following roles are created and permissions are assigned:
| Role | Permission | Description |
| ---- | ---------- | ----------- |
| User | Read | To collect the user data |
| Group | Read | To collect the group and member data |
| Domain Management | Read | To collect domain resources |
[]![Google Admin Console Roles](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/view_privileges.png)
[]![Google Admin SDK Directory API](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/api-body.png)
[]![Google Cloud Shell Window](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/gshell.png)
[]![Validate Policy Rule](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/validatepolicy.png)
[]![Set Policy Rule Option](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/setpolicy.png)
[]![Add Policy Rule](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/newrule.png)
[]![Add Rule Option](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/addrule.png)
[]![Manage Policy Option](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/managepolicy.png)
[]![Search Service Account Policy Window](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/search_serviceaccountkey.png)
[]![GCP Project Picker Window](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/projectpicker.png)
[]
| API | Description | Required for |
| --- | ----------- | ------------ |
| admin.googleapis.com | Discover Google Workspace account resources | Tree Discovery |
| cloudresourcemanager.googleapis.com | Discover Google Cloud Platform resource containers | Tree Discovery |
| cloudasset.googleapis.com | Discover the history and inventory of Google Cloud resources | Tree Discovery |
| monitoring.googleapis.com | Discover cloud monitoring data and configurations | Tree Discovery |
| orgpolicy.googleapis.com | Discover governance rules on GCP resources | Tree Discovery |
| apikeys.googleapis.com | Manage and use API keys for Google Cloud services and APIs | Tree Discovery |
| serviceusage.googleapis.com | Consume quota for a project | Tree Discovery, Orchestrator, Target |
| iam.googleapis.com | Discover identity and access control for Google Cloud resources | Tree Discovery, Orchestrator, Target |
| compute.googleapis.com | Discover compute resources and perform compute-related operations | Orchestrator |
| networkmanagement.googleapis.com | Check connections between virtual private cloud (VPC) network and DSPM. It is required for BYON | Orchestrator |
| logging.googleapis.com | Discover logs resources and perform logging operations | Orchestrator |
| secretmanager.googleapis.com | Discover secret manager resources and perform operations | Orchestrator |
| cloudkms.googleapis.com | Discover KMS resources and perform KMS-related operations | Orchestrator, Target |
| storage.googleapis.com | Discover storage resources and read data from storage | Orchestrator, Target |
| sqladmin.googleapis.com | Manage Cloud SQL instances | Orchestrator, Target |
| servicenetworking.googleapis.com | Enable private connections between the virtual private cloud (VPC) network and DSPM | Orchestrator |
Run the following commands in the gcloud CLI:
-
To set your project ID:
`gcloud config set project <PROJECT_ID>`
Replace <PROJECT_ID> with your project ID, which is required to authenticate your API requests and associate them with the correct project.
-
To enable the required API:
`gcloud services enable <API_SERVICE_NAME>`
Replace <API_SERVICE_NAME> with the API you want to enable.
For example, if your project ID is `812345678902`, you can enable the `admin.googleapis.com` API by running:
`gcloud config set project 812345678902``gcloud services enable admin.googleapis.com`
Onboarding a GCP Organization
To onboard a GCP account:
- [1. Provide the GCP account details.](#org-details)
- [][2. Deploy the tree discovery template.](#connect-org)
- [][3. Select the orchestrator project, monitoring scope, and business units.](#orch-moni-scope)
- [][(Optional) 4. Configure custom tags.](#add_custom_tags)
- [][5. Grant permissions and deploy the onboarding template.](#grantpermission)
After completing the onboarding process, you can [configure the scan settings](/dspm/configuring-scan-settings-gcp-cloud-storage).
[]The account details are required for DSPM to generate a tree discovery template that is used to connect to the GCP project.
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
- Click **Add New**.
-
Under **Select Cloud Type**, click **Google Cloud**.
[See image.](#gcptile)
- Click **Next**.
- In the **Organization Details** section:
-
**Organization Name**: Enter the organization name that contains the GCP project.
This organization name will be validated with the Organization ID on the GCP console. After validation, the verified name is synced with DSPM.
- **Organization ID**: Enter the organization ID.
-
**Project ID**: Enter the project ID where you want to create the service account and roles.
You can get the organization ID, organization name, and project ID from the [GCP console](https://console.cloud.google.com/).
- **Role Name**: Enter a unique name for the role that is created in the project.
-
**Service Account**: Enter a unique name for the service account.
The role and service account names must contain only alphabets, numbers, hyphens ("-"), and underscores ("_").
- **Notification Emails** (Optional): Enter the email addresses of the recipients who must be notified of any configuration or permissions issues encountered with the onboarded tenant. You can add up to 30 email addresses to receive notifications about the issues. You can also add email addresses after completing the onboarding process.
-
Click **Apply **to continue, or click **Reset** if you want to change the details.
[See image.](#gcporgdetails)
If all the details are accurate, you are directed to the [Connect to the Organization](#step2) section.
[]![Select Google Cloud Organization](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/gcptile.png)
[]![Provide Organization Details](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/dspm-gcp-org.png)
[]Download and deploy the tree discovery template on the project to create a role that provides read-only access to DSPM, for collecting the metadata for various services and network discoveries. This template contains policies and permissions to create a service principal, a [resource discovery role](/dspm/iam-roles-and-permissions-gcp) with the required permissions, and managed identities.
- [a. Download and modify the tree discovery template](#Download_and_update_the_tree_discovery)
- [b. Deploy the tree discovery template](#deploy_tree_discovery)
- [c. Initialize the tree discovery template](#tree_discovery_template_commands)
- [d. Add a service account](#add_service_account)
- [e. Validate the deployment in DSPM](#validate_tree_discovery)
-
[]In the DSPM Admin Portal, under the **Connect to the Organization** section, click **Tree Discovery** to download the template as a zip file and extract it to a folder on your system.
[See image.](#dl_td_template)
-
Locate the `backend.tf` file in the folder and open it in a text editor.
[See image.](#locatefile)
-
Add the name of the storage bucket and a preferred prefix where you want to store the Terraform state files, then save and close the .tf file.
[See image.](#update_td)
[]Use any of the following methods:
- [Google Cloud Shell (Recommended)](#Google_Cloud_Shell)
- [gcloud CLI](#Google_Cloud_CLI)
Run the following commands to initialize the template. This is required to manage your infrastructure resources.
-
[]
To initialize the Terraform configuration:
`terraform init`
[See image.](#td_terraform_init)
-
To verify the changes in the Terraform configuration:
`terraform plan`
-
To apply the Terraform script:
`terraform apply`
When you run the `terraform plan` or `terraform apply` command, Terraform verifies that all the required APIs are enabled. If any API is missing, an error message is displayed prompting you to enable the APIs and then continue with the verification. To avoid this situation, enable the required APIs in your project. To learn more, see [Enable APIs](#enableapis).
-
[]The command returns a JSON output that includes the project ID, private key ID, private key, client email address, and other credentials for DSPM to connect with the GCP organization.
[See image.](#json_op)
- Copy the JSON data, including the `client email` to a text file. While adding a service account, you need to provide the email ID to validate the template deployment.
- []Sign in to the [Google Admin console](https://admin.google.com/).
- Go to **Menu** > **Account** > **Admin roles**.
-
Locate the role you created as part of the [prerequisites](#pre_roles), click the **Actions **drop-down menu, and select **Assign admin**.
[See image.](#ac_roles)
-
Click **Assign service accounts**.
[See image.](#assign_ser_acc)
- In the **Add service accounts** window, enter the `client_email` that you copied from the JSON file.
-
Click **ADD** to add the service account to the service accounts list, then click **ASSIGN ROLE** to proceed.
[See image.](#assign_role)
- []In the **Connect to the Organization** section, under **Generated JSON**, paste the JSON output generated with the [Terraform apply](#json_out) command.
-
Click **Validate**.
[See image.](#validate_td)
DSPM verifies the JSON data and validates the template deployment. If the validation is successful, you are directed to the [Orchestrator & Monitoring Scope](#step3) section.
[]![Validate the Tree Discovery Template Page](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/validate_td.png)
[]![Add Service Account Page](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/assign_role.png)
[]![Custom Roles Page](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/assign_ser_acc.png)
[]![GCP Admin Console Admin Roles Page](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/dspm-gcp-assign-admin-permission-updated.png)
- []Open the Command Prompt or any other CLI app on your local system.
-
Run the following command to connect to the Google Cloud console:
`gcloud auth application-default login`
[See image.](#run_login_cmd)
You are directed to a browser to authorize access to the Google Auth Library. Log in to your GCP account to confirm authorization and close it after granting access.
[See image.](#gcloud_login)
After successful authorization, the Google Cloud SDK displays a confirmation message, indicating that your credentials are saved to a file.
- Change the current working directory to the folder containing the modified Terraform file from your system.
- Run the commands to initialize the template.
- []Sign in to the [Google Cloud console](http://console.cloud.google.com/).
-
On the **Project Selector**, select the Google Cloud project where you want to apply the Terraform configuration.
[See image.](#td_proj_select)
-
Click **Activate Cloud Shell** at the top.
This launches a session in the bottom pane. It can take a few seconds for the session to initialize.
[See image.](#td_cloud_shell_activate)
-
From the **More** menu, click **Upload**, then select the **Folder** option. Click **Choose Folder** to select the folder containing the modified Terraform file from your system, and click the **Upload** button.
[See image.](#td_upload_folder)
- Run the commands to initialize the template.
[]![Select the GCP project](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/project_selector.png)
[]![Activate the cloud shell in GCP console](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/activate_cloud_shell.png)
[]![Upload the terraform template folder to the GCP Cloud Shell](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/upload_folder.png)
[]![Tree Discovery Template JSON Output](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/json_op.png)
[]![Terraform Tree Discovery Initialization](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/td_tf_init.png)
[]![Run GCP login command](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/run_login_cmd.png)
[]![Google Auth Library Login Page](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/gclould_login.png)
[]![Locate the backend.tf Tree Discovery](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/locatefile.png)
[]![Update Tree Discovery backend.tf](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/update_td.png)
[]![Download Tree Discovery Template](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/dl_td_template.png)
[]After validating the [tree discovery template](/dspm/onboarding-gcp-organization#connect-org), select the network configuration, orchestrator, and monitoring scope.
Under **Orchestrator & Monitoring Scope**:
- [Select the network configuration.](#SelectNetworkConfiguration)
- [Configure the Orchestrator.](#config_gcp_orch)
- [Set the Monitoring Scope.](#config_gcp_ms)
To modify the configuration for Orchestrator or Monitoring Scope, click **Reset**.
After successfully configuring the projects, you are directed to the [Additional Configuration](#step4-additionalconfig) section.
[]You can choose any of the following network configurations:
- **Zscaler**: Use Zscaler resources to deploy the orchestrator and monitoring scope.
- **Custom**: Use your organization's resources to deploy the orchestrator and monitoring scope.
[See image.](#byon_config)
Changing the network configuration resets the existing configurations.
[]To configure the orchestrator, click **Configure Orchestrator**.
The orchestrator configuration depends on the network configuration you chose earlier.
- [If you have selected the Zscaler network configuration](#zscaler_configuration)
- [If you have selected the custom network configuration](#custom_configuration)
[]
-
On the **Configure Orchestrator Project** page:
- Select an orchestrator project on which you want to deploy the DSPM orchestrator template.
- **Select Orchestrator Region**: Select the region where you want to deploy the orchestrator project.
- **VPC Selflink**: Enter the selflink of the VPC network where you want to deploy the orchestrator. The VPC selflink is the unique identifier for your VPC network in the selected region.
- **Subnet Selflink**: Enter the selflink of the subnet within the selected VPC where you want to deploy the orchestrator. The subnet selflink identifies the specific subnet network that is used for deployment.
-
**Log Bucket Name**: Enter a unique name for the log bucket. This log bucket stores the target projects' activity logs. The log bucket is created while deploying the onboarding template. The name must be unique, otherwise, DSPM shows an error message.
DSPM automatically excludes Google Cloud Storage buckets used for storing logs.
[See image.](#byon-config-orch-proj)
- Click **Next**.
-
On the **Configure Regions for monitoring and scanner's configuration** page:
- **VPC Selflink**: Enter the selflink of the VPC network where you want to deploy the scanner instances.
- Choose the regions that DSPM must monitor and enter the **Subnet Selflink** for each selected region. DSPM creates and deploys resources required for scanning only in the selected regions.
[See image.](#byon-config-regions)
- Click **Done**.
[]
-
On the **Configure Orchestrator Project** page:
- Select an orchestrator project on which you want to deploy the DSPM orchestrator template.
- **Select Orchestrator Region**: Select the region where you want to deploy the orchestrator project.
-
**Log Bucket Name**: Enter a unique name for the log bucket. This log bucket stores the target projects' activity logs. The log bucket is created while deploying the onboarding template. The name must be unique, otherwise, DSPM shows an error message.
DSPM automatically excludes Google Cloud Storage buckets used for storing logs.
[See image.](#config_orch_proj)
- Click **Next**.
-
On the **Configure Regions for monitoring and scanner's configuration** page, select the regions where you want to deploy scanning resources, limiting the DSPM to monitor only the chosen regions, deploying networking infrastructure components to those areas.
[See image.](#zscaler-config-regions)
- Click **Done**.
[]![The orchestrator & monitoring scope section with annotations around Network Configurations.](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/dspm-select-network-configuration.png)
[]![Configure Orchestrator Project page](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/ds-byon-config-orch-proj.png)
[]![Configure Orchestrator Project page](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/config_orch_proj01.png)
-
[]Click **Set Monitoring Scope**.
[See image.](#set_ms)
-
On the **Configure Monitoring Scope** page, select the projects that DSPM should monitor.
- Select the main project group if all projects under that group must be scanned.
- Select **Autodetection** if you want DSPM to automatically include and scan new projects that are added to the management group in the future. This eliminates the need to manually onboard new projects.
[See image.](#config_ms)
- Click **Next**.
-
On the **Assign Business Units** page, assign a [business unit](/dspm/about-business-units) to the management group. All projects in that management group are assigned to the same business unit.
A default business unit is assigned to the management groups. You can [change the business unit](/dspm/changing-business-unit) if required, after completing the onboarding process.
[See image.](#config_bu)
- Click **Done**.
[]![Configure Regions Window](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/ds-zscaler-config-regions.png)
[]![Configure Regions Window](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/ds-byon-config-regions.png)
[]![Assign Business Units Page](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/config_bu01.png)
[]![Configure Monitoring Scope Page](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/config_ms01.png)
[]![Set Monitoring Scope button](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/dspm-fcp-set-monitoring-scope.png)
[]You can configure custom tags while onboarding or skip this step and configure it after completing the onboarding process.
Custom tags are assigned to the resources created by DSPM that enable you to distinguish resources in the organization.
To add custom tags:
-
Click **Add Custom Tags**.
[See image.](#cust_tag)
-
On the **Add Custom Tags** page, enter a key and value pair for the tag.
Ensure to [follow the guidelines](/dspm/managing-custom-tags) while entering key-value pairs for custom tags.
-
Click **Add More**, to add additional tags.
[See image.](#add_cust_tag)
- Click **Done**.
After successfully configuring the custom tags, you are directed to the [Grant Permissions](#step4) section.
[]![Add Custom Tag button](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/dspm-gcp-additional-configuration.png)
[]![Add Custom Tag page](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/dspm-gcp-add-custom-tags.png)
[]Download and deploy the GCP onboarding template, which includes policies and permissions to create custom roles and allow DSPM to access the GCP organization.
- [a. Download and modify the GCP onboarding template](#download_gcp_onboarding)
- [b. Deploy the GCP onboarding template](#deploy_gcp_onboarding)
- [c. Initialize the GCP onboarding template](#Initialize_GCP_onboarding)
- [d. Validate the deployment in DSPM](#validateonboarding)
An error message appears if there is any issue while deploying the template. Rerun the template in the root account. If the template is successfully deployed, you are directed to the [Cloud Accounts page](/dspm/viewing-onboarding-status) to view the status of the onboarded project.
After deploying the onboarding template, you can reset the [Orchestrator project](/dspm/configuring-gcp-orchestrator-account) or the [Monitoring scope](/dspm/managing-monitoring-scope-gcp) if required.
-
[]In the DSPM Admin Portal, under the **Grant Permissions** section, click **GCP Onboarding** to download the template as a .zip file and extract it to a folder on your system.
[See image.](#download_orch_tf)
-
Locate the `backend.tf` file within the extracted folder and open it in a text editor.
[See image.](#locate_onboarding_template)
-
Add the name of the storage bucket and a preferred prefix where you want to store the Terraform state files, then save and close the .tf file.
[See image.](#edit_oboarding_template)
[]Use any of the following methods:
- [Google Cloud Shell (Recommended)](#onboarding_gcloudCLI)
- [gcloud CLI](#onboarding_cloudCLI)
- []Sign in to the [Google Cloud console](http://console.cloud.google.com/).
-
On the **Project Selector**, select the Google Cloud project where you want to apply the Terraform configuration.
[See image.](#ob_proj_select)
-
Click **Activate Cloud Shell** at the top.
This launches a session in the bottom pane. It can take a few seconds for the session to initialize.
[See image.](#ob_cloud_shell_activate)
-
From the **More** menu, click **Upload**, then select the **Folder** option. Click **Choose Folder** to select the folder containing the modified Terraform file from your system, and click the **Upload** button.
[See image.](#ob_upload_folder)
- Run the commands to initialize the template.
[]![Select the GCP project](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/project_selector.png)
[]![Activate the cloud shell in GCP console](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/activate_cloud_shell.png)
[]![Upload the terraform template folder to the GCP Cloud Shell](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/upload_folder.png)
- []Open the Command Prompt or any other CLI app on your local system.
- Change the current working directory to the folder containing the modified Terraform file from your system.
- Run the commands to initialize the template.
Run the following commands to initialize the template. This is required to manage your infrastructure resources.
-
[]
To initialize the Terraform configuration:
`terraform init`
[See image.](#orch_tf_init)
-
To verify the changes in the Terraform configuration:
`terraform plan`
When you run the `terraform plan` or `terraform apply` command, Terraform verifies that all the required APIs are enabled. If any necessary API is missing, an error message is displayed to enable it to continue. To avoid this, ensure that the required APIs are enabled in your project. To enable the necessary APIs, see [Enable APIs](#enableapis).
-
For **Enter a value**, enter the regions where you want DSPM to monitor and scan data in the following format:
`["region name1", "region name2", "region name3", and so on.]`
DSPM creates resources required for data scanning only in these specified regions.
[See image.](#orch_tf_plan)
-
To run the Terraform script:
`terraform apply`
-
For **Enter a value**, enter the regions where you want to deploy the template in the following format:
`["region name1", "region name2", "region name3", and so on.]`
[See image.](#orch_tf_apply)
-
For **Do you want to perform these actions?**, enter `yes` and then press `Enter`.
[See image.](#orch_tf_yes)
After the Orchestrator and Monitoring Scope templates are successfully deployed, the required resources are created in the GCP orchestrator project.
-
[]In the Connect to the **Grand Permissions** section, click **Validate** to verify if the template is deployed. This process takes a couple of minutes to complete.
[See image.](#orch_validate)
DSPM validates the template deployment every hour by checking the roles that are created and permissions granted.
[]![Validate the Orchestrator Terraform](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/validate_orch_tf.png)
[]![Download the Orchestrator Terraform](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/dwnld_orch_tf.png)
[]![Confirm Terraform Apply](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/orch_tf_yes.png)
[]![Terraform apply ](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/orch_tf_apply.png)
[]![Orchestrator Terraform Template Plan](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/orch_tf_region.png)
[]![Initialise the Terraform](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/orch_tf_init.png)
[]![Modify the Onboarding Template](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/edit_oboarding_template.png)
[]![Locate the onboarding backend.tf file](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/onboarding-gcp-organization/locate_onboarding_template.png)