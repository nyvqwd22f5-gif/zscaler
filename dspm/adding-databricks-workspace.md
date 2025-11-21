# Adding a Databricks Workspace or Account
Source: https://help.zscaler.com/dspm/adding-databricks-workspace
PDF: https://help.zscaler.com/pdf/com/en/1532035.pdf

You can add a [Databricks workspace or account](/dspm/about-service-registration) to DSPM. DSPM scans the data assets for sensitive data and identifies any potential security posture risks.
[]Prerequisites
Before adding a Databricks workspace or account to DSPM, ensure the following prerequisites are met:
Onboard an Azure or AWS Workspace
- [1. Obtain Workspace access and permissions.](#pre-access-and-permissions)
- [2. Configure a managed identity for Azure.](#pre-managed-identity)
- [3. Create a service principal for AWS workspaces.](#aspw)
- [4. Set up a connection string.](#pre-connection-string)
- 5. For AWS customer-managed VPCs, ensure the DSPM orchestrator and scanner subnets are allowed by network policies or AWS private link.
Onboard an AWS Account
- [1. Create a service principal.](#createawsaccountsp)
- [2. Generate the OAuth secret in Databricks.](#generatesecret)
- [3. Save the secret in AWS Secrets Manager within the DSPM orchestrator account.](#storenewsecret)
- [4. Copy the secret ARN.](#copysecretarn)
- [5. Copy the Databricks workspace account ID.](#copydbid)
- 6. Grant Metastore Admin permissions to the service principal for the associated workspaces.
[]
Add the service principal to all accounts.
- Go to the [Databricks portal](https://accounts.cloud.databricks.com/).
- In the left-side navigation, click **User management**.
- On the **Service principals** tab, click **Add service principal**.
- Enter a name for the service principal.
- Click **Add**.
- Click the added service principal.
- Go to **Roles**.
- Enable the **Account Admin** permission.
[]
- []Log in to the AWS Databricks portal.
-
Go to **User Management** and select the **Service principals** tab.
[See image.](#img-um-sp)
- Select the required service principal.
- Click **Credentials & secrets**.
-
Under **OAuth secrets**, click **Generate secret**.
[See image.](#img-gen-sec)
-
In the **Generate OAuth secret** window, provide the validity in days for the OAuth token and click **Generate**.
[See image.](#img-gen-sec-button)
The **client ID** and **secret** are generated.
[See image.](#img-copy-save-sec-cli-id)
- Copy the secret and client ID, save them on your system, then click **Done**.
[]
- []Open the **AWS Secrets Manager** in the [AWS Management Console](https://aws.amazon.com/console/).
- Select **Store a new secret**.
- On the **Choose secret type** page, select **Other type of secret**.
-
Select the **Plaintext** tab and enter the generated secret.
[See image.](#img-store-secret)
- Click **Next**.
-
On the **Configure secret** page:
- **Secret name**: Enter a name for the secret.
- **Description** (optional): Enter a description if required.
[See image](#img-name-secret)
- Click **Next**.
- On the **Configure rotation** page, click **Next**.
-
On the **Review** page, review your secret details, and then click **Store**.
[See image.](#img-review-secret)
[]
- Open the **AWS Secrets Manager** in the [AWS Management Console](https://aws.amazon.com/console/).
-
Click the stored secret.
The secret details are displayed.
[See image.](#img-copy-secret-arn)
- Copy and save the Secret ARN on your system, and provide this value during the onboarding process.
[]
- Log in to the AWS Databricks portal.
- In the top-right corner of the portal, click the user profile icon.
-
Locate the **Account ID** from the drop-down menu.
[See image.](#img-ws-acc-id)
- Copy and save the Account ID to provide during the onboarding.
[]![Review secret details window to verify the secret details](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-aws-review-secret.png)
[]![Configure secret window to configure the name of the secret. ](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-aws-config-secret.png)
[]![AWS Secret Manager window showing options to store new secrets.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-aws-cs.png)
[]![AWS Secret Manager window showing the secret details with an annotation around the secret ARN.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-copy-secret-arn.png)
[]![AWS Databricks portal showing the user menu with an annotation around Account ID.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-ws-acc-id.png)
[]![AWS Databricks portal showing the User Management window with Service Principals tab highlighted.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-um-sp.png)
[]![AWS Databricks portal showing Credentials & secrets for the selected Service principal](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-gen-sec.png)
[]![Generate OAuth secret window to select the lifetime of the secret.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-gen-sec-button.png)
[]![Generate secret window showing the generated secret and client ID](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-copy-save-sec-cli-id.png)
[]Use either of these options:
-
[]If a Serverless SQL Warehouse exists in the workspace, retrieve its **JDBC URL** from the **SQL Warehouses** section.
[See image.](#db-copy-warehouses-jdbc)
-
If a Serverless SQL warehouse is not available, create a new compute instance using the following configuration.
- **Databricks Runtime**: Select **17.1**.
- **Node Type**:
- **Azure**: Select **Standard_D2ds_v6**.
- **AWS**: Select **md5.large**.
- **Single Node**: Select the checkbox.
- **Terminate after **`**X**`** minutes of inactivity: **Enter `20`.
[See image.](#db-create-compute)
This is the JSON reference for creating the single node compute instance in Azure:
`{
"data_security_mode": "DATA_SECURITY_MODE_AUTO",
"cluster_name": "DSPM Data Scanning Compute",
"kind": "CLASSIC_PREVIEW",
"runtime_engine": "STANDARD",
"spark_version": "17.1.x-scala2.13",
"node_type_id": "Standard_D2ds_v6",
"autotermination_minutes": 20,
"is_single_node": true
}`
This is the JSON reference for creating the single node compute instance in AWS:
`{
"data_security_mode": "DATA_SECURITY_MODE_AUTO",
"cluster_name": "DSPM Data Scanning Compute",
"kind": "CLASSIC_PREVIEW",
"aws_attributes": {
"zone_id": "auto"
},
"runtime_engine": "STANDARD",
"spark_version": "17.1.x-scala2.13",
"node_type_id": "m5d.large",
"autotermination_minutes": 20,
"is_single_node": true
}`
After creating the compute instance, click the **Advanced **section, and click **JDBC/ODBC** to retrieve the **JDBC URL**. Copy the URL without the last three properties. To learn more, refer to the [Databricks documentation](https://docs.databricks.com/aws/en/compute/configure).
[See image.](#db-copy-compute-jdbc)
[]![Databricks SQL Warehouse connection details with JDBC URL.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/db-sql-warehouses.png)
[]![Databricks page to create new compute with configuration details.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/db-create-compute.png)
[]![Databricks Compute Configuration details with JDBC URL.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/db-copy-compute-jdbc.png)
[]Copy application IDs of orchestrator- and scanner-managed identities from Azure portal during registration:
- Go to the Databricks workspace.
- Add a new service principal to the Databricks account. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/databricks/admin/users-groups/manage-service-principals).
- In the **Add service principal** window, select the **Microsoft Entra ID managed** option, enter a name for the service principal, and paste the **Application ID** from the DSPM Databricks registration (see [Integration Details](#integration-details)).
-
Click **Add**.
[See image.](#db-add-service-principal)
- In the Databricks workspace, select the created service principal.
-
Enable the following entitlements:
- Databricks SQL access
- Workspace access
[See image.](#db-enable-entitlements)
- Click **Update**.
Repeat these steps for both the orchestrator- and scanner-managed identities.
[]![Databricks interface to configure service principal entitlements.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/db-enable-entitlements.png)
[]![Add a new service principal in Databricks with Microsoft Entra ID.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/db-add-service-principal.png)
- []You must be a workspace admin in the Databricks workspace.
- Ensure that the workspace admin is granted **USE CATALOG** access to all catalogs in the workspace.
[]Adding a Databricks Workspace
To add a Databricks workspace:
- Go to **Administration **>** Configuration **>** Service Registration**.
-
On the **Service Registration** page, select the **Databricks **tab, and click **Add Databricks**.
[See image.](#img_add)
The **Add Databricks **window appears.
- In the **Add Databricks **window:
- **Cloud**: Select the cloud service provider that hosts the Databricks.
- **Registration Type**: Select **Workspace**.
- [Azure](#azure-ws)
- [AWS](#aws-ws)
After saving the workspace configuration, run the obtained permission script on the Databricks DSPM compute or any environment that supports Python execution. Proceed to [configure the workspace](#wsp-config).
[]
-
**Workspace Information**:
- **Workspace Name**: Enter the name of the Databricks workspace.
- **Workspace ID**: Enter the unique identifier for the Databricks workspace.
- **Account Name**: Enter the Databricks account name that hosts the workspace.
- **Account ID**: Enter the Databricks account ID.
- **Cloud Account**: Select the connected cloud accounts.
- **Cloud Region**: Select the region where the workspace is deployed.
- **DSPM Integration Alias**: Enter the DSPM alias used to identify the integration for this workspace.
[See image.](#ds-add-aws-databricks-info)
-
[]**Authentication Details**:
- **Authentication Type**: Select the authentication type.
- **Client ID**: Enter the service principal client identifier which was created as a [prerequisite](#pre).
- **Client Secret ARN**: Enter the AWS Secrets Manager ARN from orchestrator account that stores the client secret.
- **Connection String**: Paste the JDBC URL copied during the [prerequisite step](#setup-connection) to establish a connection between DSPM and the Databricks workspace.
- []A permission script is generated.
- **Copy Script**: Copy the script to the clipboard, [create a Databricks job](#createjob) (recommended) or run it manually in the Databricks workspace to grant DSPM the required access.
- **Download Script**: Download the script for offline use or automation.
[See image.](#ds-add-aws-databricks-script)
- Click **Save**.
The AWS Databricks workspace is added and displayed on the **Workspace** tab on the [Databricks page](/dspm/about-service-registration).
[]
-
**Workspace Information**:
- **Workspace Name**: Select a name of the Databricks workspace.
- **Workspace ID**: This field is autopopulated with the unique identifier for the Databricks workspace.
- **Account**: This field is autopopulated with the cloud account that hosts the workspace.
- **Region**: Enter the region where the workspace is deployed.
[See image.](#ds-add-databricks-info)
-
[]**Integration Details**:
- **DSPM Integration Alias**: Enter the DSPM alias used to identify the integration for this workspace.
- **Orchestrator Service Principal Application ID**: This field is autopopulated with the application ID of the orchestrator service principal used for authentication.
- **Scanner Service Principal Application ID**: This field is autopopulated with the application ID of the scanner service principal used for data scans.
- **Connection String**: Paste the JDBC URL copied during the [prerequisite step](#setup-connection) to establish a connection between DSPM and the Databricks workspace.
-
[]A permission script is generated.
Run the script in the Databricks workspace to grant DSPM the required access:
- **Copy Script**: Copy the script to the clipboard, and run it manually in the Databricks workspace.
- **Download Script**: Download the script for offline use or automation.
[See image.](#ds-add-databricks-script)
- Click **Save**.
The Azure Databricks workspace is added and displayed on the **Workspace** tab on the [Databricks page](/dspm/about-service-registration).
Adding a Databricks Account
To add a Databricks account:
- Go to **Administration **>** Configuration **>** Service Registration**.
-
On the **Service Registration** page, select the **Databricks **tab, and click **Add Databricks**.
[See image.](#img_add-acc)
The **Add Databricks **window appears.
- In the **Add Databricks **window:
- **Cloud**: Select the cloud service provider that hosts the Databricks.
-
**Registration Type**: Select **Account**.
The **Account** registration type is available only for **AWS**.
-
**Account Information**:
- **Account Name**: Enter a name for the Databricks account.
- **Account ID**: Enter the Databricks Account ID.
- **DSPM Integration Alias**: Select the DSPM alias for this integration.
[See image.](#ds-add-aws-acc-databricks-info)
-
[]**Authentication Details**:
- **Authentication Type**: Select the authentication type.
- **Client ID**: Enter the service principal client identifier which was created as a [prerequisite](#pre).
- **Client Secret ARN**: Enter the AWS Secrets Manager ARN from orchestrator account that stores the client secret.
[See image.](#ds-add-aws-acc-databricks-script)
- Click **Save**.
The AWS Databricks account is added and displayed on the **Accounts** tab on the [Databricks page](/dspm/about-service-registration).
For Databricks accounts, the associated workspaces are discovered within approximately 15 minutes and then the scan rules can be configured for the workspaces.
[]Configuring the Workspace
After [adding the Databricks workspace](#adding-db-ws-account) in the DSPM Admin Portal, and obtaining the permission script, run the script to complete the integration:
- 1. Run the permission script.
- [For Azure](#post-run-script-azure)
- [For AWS](#post-run-script-aws)
- [2. (Optional) Allowlist IP access to workspaces.](#allowlist-workspcae)
The Databricks workspace is added and displayed on the [Databricks page](/dspm/about-service-registration). You can proceed to [configure the scan rules for the Databricks workspace](/dspm/configuring-scan-rule-azure-databricks-workspace).
[]If the IP Access List is enabled in the workspace and includes rules that might block access to the scanner or orchestrator, allowlist the egress IP addresses where the scanner and orchestrator are hosted. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/databricks/security/network/front-end/ip-access-list-workspace).
-
Run the following command to check if the IP Access List feature is enabled:
`databricks workspace-conf get-status enableIpAccessLists`
-
If the IP Access List feature is not enabled, run the following command:
`databricks workspace-conf set-status --json '{
"enableIpAccessLists": "true"
}'`
This configuration is also required at the Account Level.
To configure the IP access for Account Level:
- Go to the Databricks account portal.
- Go to **Security** > **Networking** > **Account Console IP Access List**.
- Add the required egress IP addresses for the DSPM scanner and orchestrator.
[]To onboard an AWS workspace, create a job in Databricks and grant the required permissions.
- [a. Create a service principal](#csp)
- [b. Grant Metastore admin permissions](#gmap)
- [][c. Create the permission script job.](#cpsj)
- [d. Create a job and associate task with notebook or script](#atwn)
- [e. Configure job execution](#cje)
- [f. Adjust job permissions](#ajp)
[]If you have a service principal to manage jobs, skip this step. Else, create one service principal to manage jobs.
- Go to the [Databricks account portal](https://accounts.cloud.databricks.com/).
- In the sidebar, click **User management**.
- On the **Service principals** tab, click **Add service principal**.
-
Enter a name for the service principal.
[See image.](#ds-img-csp-create)
- Click **Add service principal**.
[]![Service principals screen with Add service principal window for with name field.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-csp-create.png)
[]Create a Metastore Admins group if not created, and add the service principal to this group:
- Go to the [Databricks account portal](https://accounts.cloud.databricks.com/).
- In the left-side navigation, click **User management**.
- On the **Groups** tab, click **Add group**.
-
Enter a name for the group.
[See image.](#ds-img-gmap-add-group)
-
Click **Add group**.
When prompted, add service principals to the group.
- In the left-side navigation, click **Catalog**.
- Click the metastore name associated with your workspace to open its properties.
- Under **Metastore Admin**, click **Edit**.
-
Select a group from the drop-down menu.
[See image.](#ds-img-gmap-edit-admin)
- Click **Save**.
[]![User management Groups tab showing groups and create new group window.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-gmap-add-group.png)
[]![Edit metastore admin window showing the option to search for the groups.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-gmap-edit-admin.png)
[]Add the service principal to all relevant workspaces.
- Go to the Databricks workspace.
- Click your username in the top bar of the Databricks workspace and select **Settings**.
- Select the **Identity and access** tab.
- Next to **Service principals**, click **Manage**.
- Click **Add service principal**.
- Enter a name for the service principal.
- Click **Add**.
Assign the following entitlements to the service principal:
- In the Databricks workspace, select the created service principal.
- Enable the following entitlements:
- Databricks SQL Access
- Workspace Access
- Click **Update**.
- [Generate the OAuth secret.](#ds-gen-secret)
- [Store the secret in the orchestrator account](#sp-secret).
[]Create a new notebook in any folder:
- In the left-side navigation, click **Workspace**.
-
Click **Create**, and select **Notebook**.
[See image.](#ds-img-cpsj-create)
A blank notebook appears.
- Copy the script from the DSPM Admin Portal, and paste it in the notebook.
- [See image.](#ds-img-cpsj-paste)
- Provide a name for the notebook and save it.
[]![Databricks Workspace window with an annotation around Create button and Notebook option.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-cpsj-create.png)
[]![Databricks Notebook- The DSPM script pasted into the Databricks notebook.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-cpsj-paste.png)
- []In your workspace, click **Jobs & Pipelines** in the sidebar.
-
Click **Create**, then **Job**.
[See image.](#ds-img-atwn-create-job)
-
Create the job using the name prefix `zdspm-job`.
[See image.](#ds-img-atwn-create-job-name)
- Select the **Tasks** tab in the Jobs UI.
- Click **Add task**.
- **Task name**: Enter a name for the task.
- **Type**: Select **Notebook**.
- In the **Source** drop-down menu, select **Workspace**.
- Click the **Path**. The **Select Notebook** dialog appears.
-
Browse to the created notebook, and click **Confirm**.
[See image.](#ds-img-atwn-browse-nb)
- Click the **Cluster**, create a Job Cluster with the following configuration:
- **Cluster Type**: Single Node.
- **Node Type**: md5.large.
-
Click **Confirm**.
[See image.](#ds-img-atwn-create-cluster)
-
Click **Create task**.
[See image.](#ds-img-atwn-create-task)
A new job appears in the workspace jobs list.
[]![Databricks - Jobs and Pipelines window with an annotation for Create and Job options.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-atwn-create-job.png)
[]![Databricks - creating a job cluster with the required node type.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-atwn-create-job-name.png)
[]![Databricks - creating a job cluster with the required node type.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-atwn-create-cluster.png)
[]![Databricks browse notebook window, to select the notebook path.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-atwn-browse-nb.png)
[]![Databricks - creating a task with the required fields. ](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-atwn-create-task.png)
-
[]On the right side of the selected job, in the **Job Details** section, edit **Run as**.
[See image.](#ds-img-cje-runas)
-
Select the created Metastore Admin Service Principal.
[See image.](#ds-img-cje-change-runas)
-
Save and confirm that the **Run as** set to the created Service Principal and assigned Metastore Admin permission.
[See image.](#ds-img-cje-verify-runas)
[]![Databricks Jobs UI showing the job details with an annotation for edit Run as option.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-cje-runas.png)
[]![Databricks dialog box to change run as, selected Metastore Admin Service Principal.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-cje-change-runas.png)
[]![Databricks Jobs UI showing the job details with an annotation for edit Run as option.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-cje-verify-runas.png)
-
[]On the right side of the selected job, in the** Permissions** section, click **Edit Permissions**.
[See image.](#ds-img-ajp-edit)
- Select the service principal provided to DSPM at registration.
-
Grant it permission to **Can Manage Run**.
[See image.](#ds-img-ajp-grant)
- Click **Save**.
-
Verify that the Service Principal has the required permission.
[See image.](#ds-img-ajp-verify)
[]![Databricks Jobs UI showing the Edit permissions button.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-ajp-edit.png)
[]![Databricks permission settings with the Can Manage Run permission selected.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-ajp-grant.png)
[]![Databricks Jobs UI showing the permissions.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-img-ajp-verify.png)
- []Log in to the Databricks workspace.
- Create a notebook in the Databricks workspace.
-
Paste the [script](#ser-reg) that you obtained while [Adding a Databricks Workspace](#adding-db-ws-account) into the notebook.
[See image.](#create-notebook)
-
Select the appropriate compute resource, attach it to the notebook, and click **Attach and run**. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/databricks/notebooks/notebooks-manage#create-a-notebook-in-any-folder).
[See image.](#attach-run-notebook)
[]![Databricks attach a compute resource window to attach and run a compute resource to Databricks workspace.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/db-attach-run-notebook.png)
[]![A Notebook in Databricks workspace showing script for permission.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/db-create-notebook.png)
[]![Databricks Workspace with the necessary information filled for Azure.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/db-add-azure-workspace-info.png)
[]![Databricks Workspace with the necessary information filled for AWS.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/db-add-aws-workspace-info.png)
[]![Databricks Account with the necessary information filled for AWS.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/db-add-aws-account-info.png)
[]![The Databricks page with a list of workspaces and annotation around the Add Databricks Workspace button.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-add-databricks-button.png)
[]![The Databricks page with a list of workspaces and annotation around the Add Databricks Workspace button.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-add-databricks-button.png)
[]![Add Databricks Workspace page with the necessary integration details filled.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/db-add-execute.png)
[]![Add Databricks Workspace page with the necessary authentication details filled.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/db-add-aws-authentication-details.png)
[]![Add Databricks Account page with the necessary authentication details filled.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/db-add-aws-account-authentication-details.png)