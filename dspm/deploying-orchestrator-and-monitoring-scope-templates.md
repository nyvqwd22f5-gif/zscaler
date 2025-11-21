# Deploying the Orchestrator and Monitoring Scope Templates
Source: https://help.zscaler.com/dspm/deploying-orchestrator-and-monitoring-scope-templates
PDF: https://help.zscaler.com/pdf/com/en/1525806.pdf

[]After configuring the [orchestrator and monitoring scope](/dspm/selecting-aws-orchestrator-and-monitoring-scope), deploy the orchestrator and monitoring scope templates. The templates include policies and permissions to create IAM roles that provide DSPM with read-only access to the resources in the organization.
To download and deploy the templates:
-
1. For **Template Type**, select **CloudFormation** or **Terraform**.
[See image.](#gp-templatetype)
- [][2. Deploy the orchestrator template.](#orchestrator-template-step4)
- [3. Deploy the evidence template.](#deploy-evidence-template)
- [][4. Deploy the monitoring scope template.](#monitoringscope-template-step4)
- [5. Validate the template.](#validate-templatedeployment)
After the orchestrator and monitoring scope templates are successfully deployed, the following resources are created in the AWS orchestrator account:
[][List of Resources](#listofresources)
After completing the onboarding process, you can configure the scan settings. To learn more, see [About Scan Settings](/dspm/about-scan-settings).
[]
- To deploy the CloudFormation template:
- [a. Download the orchestrator template.](#orch-zipfile)
- [b. Create StackSets in the AWS Management Console.](#aws-orch-template)
- To deploy the Terraform template:
- [a. Download the orchestrator template.](#orch-dwonload-terr)
- [b. Update and deploy the Terraform files.](#orch-executetemplate)
[]
- To deploy the CloudFormation template:
- [a. Download the monitoring scope template.](#monitoringscope)
- [b. Create StackSets in the AWS Management Console.](#monitoring-scope-template-aws)
- To deploy the Terraform template:
- [a. Download the monitoring scope template.](#monitor-dspmportal)
- [b. Update and deploy the Terraform files.](#targetterraform-local)
[]This template is available only if you have configured an S3 bucket to store evidence data. The template includes policies and permissions to upload evidence data snippets to the selected S3 bucket.
- To deploy the CloudFormation template:
- [a. Download the evidence template.](#evidence-cft)
- [b. Create stacks.](#evidence-create-stacksets)
- To deploy the Terraform template:
- [a. Download the evidence template.](#evidence-terraform)
- [b. Update and deploy the Terraform files.](#deploy-evidence)
[]Click **Orchestrator** to download the template as a ZIP file and extract it to your local system.
[See image.](#zip-files-orchestrator)
[]Click **Orchestrator** to download the template as a ZIP file and extract it to your local system. The ZIP file includes:
- Multiple Terraform files.
- A README file with instructions for running the template.
[See image.](#orch-terraformtemplatefiles)
[]Click **Monitoring Scope** to download the template as a ZIP file and extract it to your local system. The ZIP file includes:
- []A CSV file with the target account details.
- A YAML file.
[See image.](#ms-template-files)
[]Click **Monitoring Scope** to download the template as a ZIP file and extract it to your local system. The ZIP file includes:
- A CSV file with the target account details.
- Multiple Terraform files.
- A README file with instructions for running the template.
[]Before creating a new StackSet for the new orchestrator account, delete the existing infrastructure of the old orchestrator account to avoid conflicts.
- Sign in to the root account [AWS Management Console](https://aws.amazon.com/console/) and go to **CloudFormation**.
- In the left-side navigation, select **StackSets**.
-
Click **Create StackSet**.
[See image.](#create-stackset-orch)
-
On the **Choose a template** page:
- **Permissions**: Select **Self-service permissions**.
- **IAM admin role ARN - optional**: Select the **IAM role name** from the drop-down menu, and then select **AWSCloudformationStackSetExecutionRole.**
- **IAM execution role name**: **AWSCloudformationStackSetExecutionRole** is populated by default.
- **Prerequisite - Prepare template**: Select **Template is ready**.
- **Specify template**: Select **Upload a template file** and click **Choose file**. Select the downloaded template (YAML file), then click **Open**.
[See image.](#choose-template)
- Click **Next**.
-
On the **Specify StackSet Details** page:
- **StackSet name**: Enter a unique name for the StackSet.
- **Description **(Optional): Enter a description for the StackSet.
- Verify the other fields that are auto-populated.
[See image.](#specify-stackset-details)
- Click **Next**.
- On the **Configure StackSet options** page, click **Next**.
-
[]On the **Set deployment options** page:
- **Add stacks to stack set**: Select **Deploy new stacks**.
- **Accounts**:
- **Deployment locations**: Select **Deploy stacks in accounts**.
- **Account numbers**: Enter the AWS account ID of the [orchestrator account](#orch&Moni) that you selected in the DSPM Admin Portal.
-
[]**Specify regions**: Select the [regions](#configureregions-page) that you selected in the DSPM Admin Portal to deploy the resources required for scanning.
Select the [primary region of the orchestrator](#orch&Moni) as the first region, followed by other regions. DSPM supports all the 29 global regions that are supported by AWS.
- **Deployment options**:
- **Region concurrency**: Select **Sequential** to deploy StackSets in one region at a time, specified by the region deployment order.
[See image.](#configure-stackset-orch)
- Click **Next**.
-
On the **Review** page, review the StackSet details and then select the **I acknowledge** checkbox to acknowledge AWS CloudFormation's creation of IAM resources with custom names.
[See image.](#orch-review)
-
Click **Submit**.
On the **Operations** tab, you can view the status of the StackSet deployment.
[See image.](#operationsorchestrator-status)
If you encounter a conflicting S3 bucket error during StackSet creation, try deleting the existing bucket and retry the StackSet creation. To learn more, refer to the [AWS documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/delete-bucket.html).
-
[]Update the `backend.tf` file with the name of the storage services where you want to store the Terraform state files. For example:
- **bucket**: Enter the name of the [S3 bucket](#awss3bucket) in the primary region of the orchestrator account.
- **region**: Enter the primary region.
- **dynamoDB_table**: Enter the name of the [DynamoDB table](#dynamodbtable) in the primary region of the orchestrator account.
[See image.](#orch-backendfile)
- Open the Command Prompt or any other CLI app in your local system.
- Switch to the directory that contains the terraform template.
- Copy and paste the access keys of the orchestrator account and press `Enter`.
- Run the following commands:
-
To initialize the Terraform working directory:
`terraform init`
[See image.](#orch-init)
-
To verify the changes in the Terraform configuration:
`terraform plan`
-
To run the Terraform script:
`terraform apply`
[See image](#orch-apply)
Under **Do you want to perform these actions?**, enter `yes`** **and then press `Enter`.
[See image.](#orch-perform)
- []Sign in to the [AWS Management Console](https://aws.amazon.com/console/) and go to **CloudFormation**.
- In the left-side navigation, select **StackSets**.
-
Click **Create StackSet**.
[See image.](#ms-createstackset)
-
On the **Choose a template** page:
- **Permissions**: Select **Service managed permissions**.
- **Prerequisite - Prepare template**: Select **Template is ready**.
- **Specify template**: Select **Upload a template file** and click **Choose file**. Select the downloaded template (YAML file), then click **Open**.
[See image.](#ms-choosetemplate)
- Click **Next**.
-
On the **Specify StackSet Details** page:
- **StackSet name**: Enter a unique and friendly name for the StackSet. This is required when you want to [add new target accounts](/dspm/managing-monitoring-scope-aws) after onboarding.
- Verify the parameters that are auto-populated.
[See image.](#ms-sepcifystackset)
- Click **Next**.
- On the **Configure StackSet options** page, click **Next**.
-
[]On the **Set deployment options** page:
- **Add stacks to stack set**: Select **Deploy new stacks**.
- **Deployment targets**: Select **Deploy to organization**.
- []**Auto-deployment options:**
- **Automatic deployment**:** **Select **Activated** to automatically deploy additional stack instances for any new account added to the OU in the future.
- **Account removal behavior**:** **Select **Delete stacks** to remove stack instances if an account is removed from the OU.
- **Specify regions: **Select the regions that contain the data stores that you want to scan.
- **Region concurrency**: Select **Sequential** to deploy the StackSets in a sequential order as specified in the **Specify regions**.
[See image.](#ms-deploymentoption)
- Click **Next**.
-
On the **Review** page, review the StackSet details and then select the **I acknowledge** checkbox to acknowledge the AWS CloudFormation's creation of IAM resources with custom names.
[See image.](#ms-acknowledge)
-
Click **Submit**.
On the **Operations** tab, you can view the status of the StackSet deployment.
[See image.](#ms-operationstab)
On the **Stack instances** tab, you can view the stack instances created for [each region you selected](#region-ms).
The StackSet deployment is completed only when all the individual stack instances are deployed successfully. [See image.](#ms-stacksetinstance)
-
[]Update the `backend.tf` file with the name of the storage services where you want to store the Terraform state files. For example:
- **bucket**: Enter the name of the [S3 bucket](#awss3bucket).
- **region**: Enter the primary region of the target account.
- **dynamoDB_table**: Enter the name of the dynamoDB table in the primary region of the target account.
[See image.](#target-backen)
- Open the Command prompt or any other CLI app in your local system.
- Switch to the directory containing the downloaded Terraform files.
- Copy and paste the access keys of the target account and press `Enter`.
- Run the following commands:
-
To initialize the Terraform working directory:
`terraform init`
[See image.](#target-init)
-
To verify the changes in the Terraform configuration:
`terraform plan`
-
To run the Terraform script:
`terraform apply`
[See image.](#target-apply)
Under **Do you want to perform these actions?**, enter `yes`** **and press `Enter`.
[See image.](#terraform-perform)
- []**Auto scaling groups**: Scaling group used for orchestrator instance.
- **VPC**: Virtual private cloud (VPC) used to launch AWS resources.
- **Subnet**: Range of IP addresses used to connect to internet, other VPCs, or datacenters.
- **NAT gateway**: Network address translation gateway used to prevent inbound connectivity from the public internet to orchestrator or scanner instances.
- **VPC S3 Gateway endpoint**: Used for safe, secure communication between VPC and S3.
- **VPC peering connection**: Peering between orchestrator and scanner VPCs.
- **Route table**: Used to identify network traffic from subnet or gateway.
- **SQS Queue**: Simple queue service (SQS) used for sending scan requests from DSPM.
- **SNS Topic**: Simple notification service (SNS) used for forwarding the event bridge notifications to SQS.
- **Event bridge rule**: Used for forwarding the CloudTrail data events to orchestrator account.
- **IAM Roles**: Roles required to discover resources, orchestrate, and perform data scanning.
- **Security group**: Used to manage traffic within the AWS resources.
- **KMS Key**: Customer managed key for encryption.
- **DBSubnet group**: Group of subnets associated with EC2 VPC.
- **Secret**: Used to store the secret.
[]Click **Evidence **to download the template as a ZIP file and extract it to your local system.
[]
-
Sign in to the AWS Management Console and go to **CloudFormation**.
If you selected **Zscaler Managed S3 Bucket**, sign in to the orchestrator account and if you selected **Custom S3 Bucket**, sign in to the account where the custom S3 bucket is available.
- In the left-side navigation, select **Stacks**.
-
Click **Create stack**.
[See image.](#create-stackbutton)
-
On the **Create stack** page:
- **Prepare template**: Select **Choose an existing template**.
- **Specify template**: Select **Upload a template file **to upload the template you downloaded from the DSPM Admin Portal.
- **Upload a template file**: Click **Choose file**, browse and select template, then click **Open**.
[See image.](#createstack-page)
- Click **Next**.
-
On the **Specify stack details **page, under **Stack name**, enter a unique stack name.
[See image.](#specifystackdetails-page)
- Click **Next**.
- On the **Configure stack options** page, under **Capabilities**, select the **I acknowledge** checkbox to acknowledge AWS CloudFormation's creation of IAM resources with custom names and click **Next**.
- On the **Review and create** page, review the stack details and click **Submit**.
[]Click **Evidence **to download the template as a ZIP file and extract it to your local system. The file includes:
- Multiple Terraform files.
- A README file with instructions for running the template.
-
[]Update the `backend.tf` file with the name of the storage services where you want to store the Terraform state files. For example:
- **bucket**: Enter the S3 bucket name.
- **region**: Enter the primary region.
- **dynamoDB_table**: Enter the DynamoDB table name.
[See image](#targetbackend)
- Open the Command Prompt or any other CLI app in your local system.
- Switch to the directory that contains the terraform template.
- Run the following commands:
-
To initialize the Terraform working directory:
`terraform init`
[See image.](#targetinitialize)
-
To verify the changes in the Terraform configuration:
`terraform plan`
-
To run the Terraform script:
`terraform apply`
Under **Do you want to perform these actions?**, enter `yes`** **and then press `Enter`.
[]DSPM validates the template deployment every hour by checking the roles and permissions.
Click **Validate** to verify if the template is deployed.
[See image.](#gp-validatedeployment)
An error message appears if there is any issue deploying the template. Rerun the template in the root account.
[See image.](#validation-failed)
If the templates are successfully deployed, you are directed to the [Overview](/dspm/viewing-onboarding-status) page.
[]![Select the template type](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-grant-permissions-section_1.png)
[]![Orchestrator template files](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-orchestrator-template-files.png)
[]![Create a StackSet in the AWS console](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-create-stackset-button.png)
[]![Choose a template](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-orch-choose-template.png)
[]![Enter the StackSet name and API key](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-specify-aws-stackset-details_0.png)
[]![Configure StackSet options](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/aws-orch-setdeployment-options.png)
[]![Acknowledge the CloudFormation StackSet creation](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-orchestrator-acknowledge.png)
[]![View the status of StackSet execution](/downloads/tech-pubs-drafts/zpc-draft-articles/onboarding-aws-organization/aws-operations-tab-status.png)
[]![Extract the .zip files](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-orchestrator-terraform%20files.png)
[]![Edit the backend file](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/backendterrformfile.png)
[]![Run terraform init command](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/orchestrator-terraform-init.png)
[]![Run terraform apply command](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/aws-orchestrator-terraform-apply.png)
[]![Confirm the actions to perform](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/aws-terraform-orchestrator-apply.png)
[]![The CloudFormation page with Stacks option selected and annotation around Create stack button.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-cft-create-stack.png)
[]![The Create stack page displaying the fields that must be entered.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-create-stack-page.png)
[]![The Specify stack details page with all the required fields.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-evidence-specify-stack.png)
[]![Update the backend file](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/update-backend-file.png)
[]![Initialize the working directory](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/target-terraform-init.png)
[]![Extract the Template files](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-ms-template-files.png)
[]![Create StackSet for monitoring scope](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-monitoring-scope-stackset.png)
[]![Choose a template](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/aws-ms-choose-template.png)
[]![Specify StackSet details](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-ms-specify-stackset-details_0.png)
[]![Specify the regions to deploy the orchestrator](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-monitor-scope-set-deployement-option.png)
[]![dspm-aws-ms-acknowledge.png](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-ms-acknowledge.png)
[]![View the status of StackSet execution](/downloads/tech-pubs-drafts/zpc-draft-articles/onboarding-aws-organization/aws-operations-tab-status.png)
[]![View the status of the StackSet execution](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-ms-operations-tab.png)
[]![View the status of each StackSet instances](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-monitoring-scope-stackinstances.png)
[]![Update the backend file](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/update-backend-file.png)
[]![Initialize the working directory](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/target-terraform-init.png)
[]![Apply the terraform configuration](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/target-terraform-apply.png)
[]![Approve the actions](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/target-perform-actions.png)
[]![Click Validate to validate the template deployment](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-grant-permissions-validate_0.png)
[]![View the status of the template execution](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-template-execution-failed.png)