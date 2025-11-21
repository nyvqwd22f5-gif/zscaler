# Deploying the Orchestrator Template
Source: https://help.zscaler.com/dspm/deploying-orchestrator-template
PDF: https://help.zscaler.com/pdf/com/en/1520281.pdf

After [adding the orchestrator details](/dspm/adding-orchestrator-details-and-configuring-regions), deploy the orchestrator template that includes policies and permissions to create IAM roles that provide DSPM with read-only access to the account.
To download and deploy the template:
- For **Template Type**, select **CloudFormation **or **Terraform**.
- Deploy the Orchestrator template:
- [To deploy the CloudFormation template](#cloudformation-template)
- [To deploy the Terraform template](#terraform-deployment)
-
Deploy the Evidence template:
This template is available only if you have configured an S3 bucket to store evidence data. The template includes policies and permissions to upload evidence data snippets to the selected S3 bucket.
- [To deploy the CloudFormation template](#evidence-cloudformation-template)
- [To deploy the Terraform template](#evidence-terraform-deployment)
-
Click **Validate**.
[See image.](#dspmvalidate-orch)
If the template is successfully deployed, you are directed to the [Overview](/dspm/viewing-onboarding-status) page to add the [target accounts](/dspm/adding-account-details-and-deploying-templates) that must be monitored.
- [][a. Download the orchestrator template.](#download-orch-template)
- [b. Create StackSets in the orchestrator account.](#create-stacksets)
- [][a. Download the orchestrator template.](#terraform-download)
- [b. Update and deploy the Terraform files.](#update-deploy-terraform)
[]Click **Orchestrator **to download the template as a ZIP file and extract it to your local system.
[See image.](#download-cft-orch-template)
- []Sign in to the orchestrator account on the AWS console and go to **CloudFormation**.
- In the left-side navigation, select **StackSets**.
-
Click **Create StackSet**.
[See image.](#create-stackset-button)
-
On the **Choose a template** page:
- **IAM admin role ARN - optional**: Select the **IAM role name** from the drop-down menu, and then select **AWSCloudformationStackSetAdministratorRole.**
- **IAM execution role name**: **AWSCloudformationStackSetExecutionRole** is populated by default.
- **Prerequisite - Prepare template**: Select **Template is ready**.
- **Specify template**: Select **Upload a template file** and click **Choose file**. Select the downloaded template (YAML file), then click **Open**.
[See image.](#choosetemplatepage)
- Click **Next**.
-
On the **Specify StackSet Details** page:
- **StackSet name**: Enter a unique name for the StackSet.
- **Description **(Optional): Enter a description for the StackSet.
- Verify the other fields that are auto-populated.
[See image.](#specify-stacksetdetails-orch)
- Click **Next**.
-
On the **Configure StackSet options** page, under **Capabilities**, select the **I acknowledge** checkbox for AWS CloudFormation to create IAM resources with custom names and click **Next**.
[See image.](#configure-orch-stackset-options)
-
[]On the **Set deployment options** page:
- **Add stacks to stack set**: Select **Deploy new stacks**.
- **Accounts**:
- **Deployment locations**: Select **Deploy stacks in accounts**.
- **Account numbers**: Enter the orchestrator account ID that you selected in the DSPM Admin Portal.
-
[]**Specify regions**: Select the regions in which DSPM templates must be deployed.
Select the primary region of the orchestrator as the first region, followed by other regions. DSPM supports all the 29 global regions that are supported by AWS.
- **Deployment options**:
- **Region concurrency**: Select **Sequential** to deploy StackSets in one region at a time.
[See image.](#orch-set-deploymentoptions)
- Click **Next**.
-
On the **Review **page, review the StackSet details and then click **Submit**.
[See image.](#review-orch-details)
On the **Operations** tab, you can see that the StackSet is successfully deployed.
[See image.](#orch-operations-tab)
[]Click **Orchestrator** to download the template as a ZIP file and extract it to your local system. The file includes:
- Multiple Terraform files.
- A README file with instructions for running the template.
[See image.](#download-terraform-orch-template)
-
[]Update the `backend.tf` file with the name of the storage services where you want to store the Terraform state files in the orchestrator account. For example:
- **bucket**: Enter the S3 bucket name.
- **region**: Enter the primary region.
- **dynamoDB_table**: Enter the DynamoDB table name.
[See image.](#backend-tf-file)
- Open the Command Prompt or any other CLI app in your local system.
- Switch to the directory that contains the terraform template.
- Copy and paste the access keys of the orchestrator account and press `Enter`.
- Run the following commands:
-
To initialize the Terraform working directory:
`terraform init`
[See image.](#terraforminit-command)
-
To verify the changes in the Terraform configuration:
`terraform plan`
-
To run the Terraform script:
`terraform apply`
Under **Do you want to perform these actions?**, enter `yes`** **and then press `Enter`.
[See image.](#terraformapply-cmd)
- [][a. Download the evidence template.](#evidence-cft)
- [b. Create a stack.](#evidence-create-stacksets)
- [][a. Download the evidence template.](#evidence-terraform)
- [b. Update and deploy the Terraform files.](#deploy-evidence)
[]Click **Evidence **to download the template as a ZIP file and extract it to your local system.
[See image.](#evidence-button)
[]Create a stack in the account where the S3 bucket is available.
-
Sign in to the AWS Management console and go to **CloudFormation**.
If you selected **Zscaler Managed S3 Bucket**, sign in to the orchestrator account and if you selected **Custom S3 Bucket**, sign in to the account where the custom S3 bucket is available.
- In the left-side navigation, select **Stacks**.
-
Click **Create stack**.
[See image.](#create-stack-button)
-
On the **Create stack** page:
- **Prepare template**: Select **Choose an existing template**.
- **Specify template**: Select **Upload a template file **to upload the template you downloaded from the DSPM Admin Portal.
- **Upload a template file**: Click **Choose file**, browse and select template, then click **Open**.
[See image.](#create-stack-page)
- Click **Next**.
-
On the **Specify stack details **page, under **Stack name**, enter a unique stack name.
[See image.](#specifystack-details)
- Click **Next**.
- On the **Configure stack options** page, under **Capabilities**, select the **I acknowledge** checkbox to acknowledge AWS CloudFormation's creation of IAM resources with custom names and click **Next**.
- On the **Review and create** page, review the stack details and click **Submit**.
[]Click **Evidence **to download the template as a ZIP file and extract it to your local system. The file includes:
- Multiple Terraform files.
- A README file with instructions for running the template.
[See image.](#evidencebutton)
-
[]Update the `backend.tf` file with the name of the storage services where you want to store the Terraform state files. For example:
- **bucket**: Enter the S3 bucket name.
- **region**: Enter the primary region.
- **dynamoDB_table**: Enter the DynamoDB table name.
[See image.](#backend-file)
- Open the Command Prompt or any other CLI app in your local system.
- Switch to the directory that contains the terraform template.
- Run the following commands:
-
To initialize the Terraform working directory:
`terraform init`
[See image.](#td-initcmd)
-
To verify the changes in the Terraform configuration:
`terraform plan`
-
To run the Terraform script:
`terraform apply`
Under **Do you want to perform these actions?**, enter `yes`** **and then press `Enter`.
[]![The CloudFormation Stackset page with annotation around create stackset button.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/dspm-aws-create-stackset.png)
[]![The step 1 of CloudFormation stackset creation page.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/aws-choose-template-page.png)
[]![The step 2 of CloudFormation stackset creation page to specify stackset details.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/aws-orch-specify-stackset-details.png)
[]![The step 3 of CloudFormation stackset creation page to configure stackset options.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/aws-orch-configure-stackset-options.png)
[]![The step 4 of CloudFormation stackset creation page to set deployment options.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/aws-set-deployment-options.png)
[]![The review section of stackset creation workflow to review the provided details.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/aws-orch-review-page.png)
[]![The operations tab displaying the status of stackset creation with created and completed time.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/aws-orch-operations-tab.png)
[]![The deploy orchestrator section with the template type, orchestrator section with annotation around orchestrator template.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/dspm-deploy-orchestrator-section.png)
[]![The deploy orchestrator section with the template type, orchestrator section with annotation around orchestrator template.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/dspm-single-account-onboarding.png)
![The backend.tf file with s3 bucket details, primary region, and dynamoDB table details.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/backendterrformfile.png)
[]
[]
![The command prompt section showing the output of terraform init command.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/dspm-cmd-terraform-init.png)
[]![The output of terraform apply command to confirm the deployment of the template.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/aws-terraform-orchestrator-apply.png)
![The deploy orchestrator section with annotation around validate button.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/dspm-deploy-orch-template.png)
[]
[]![The Evidence section with annotation around Evidence button.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/dspm-evidence-button.png)
[]![The CloudFormation page with annotation around Create stack.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/dspm-cft-create-stack.png)
[]![The create stack page to enter the required fields and upload the evidence template file.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/dspm-create-stack-page.png)
[]![The Specify stack details page to provide a unique stack name.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/dspm-evidence-specify-stack.png)
[]![The backend.tf file updated with backend configuration.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/backendterrformfile_0.png)
[]![The command prompt section running the terraform init command](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/evidence-terraform-init.png)
[]![The evidence section with annotation around the Evidence button.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/deploying-orchestrator-template/dspm-evidence-terraform-button.png)