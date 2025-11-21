# Adding Account Details and Deploying Templates
Source: https://help.zscaler.com/dspm/adding-account-details-and-deploying-templates
PDF: https://help.zscaler.com/pdf/com/en/1520286.pdf

After deploying the [orchestrator template](/dspm/deploying-orchestrator-template), add the target accounts that must be monitored and deploy the monitoring and CloudTrail templates that include policies and permissions providing DSPM with read-only access to the target accounts.
To add account details and deploy templates:
- On the **Overview **page, go to **Manage **> **Add Account**.
-
In the **Account Details** window:
- Under **Account Details:**
- **Account Name**: Enter the AWS account name that must be monitored.
- **Account ID**: Enter the 12-digit AWS account ID.
- **Select Business Unit**: A default [business unit](/dspm/about-business-units) is assigned. Select another business unit, if required.
- Under **CloudTrail Details, **enter the S3 bucket details where the [CloudTrail ](/dspm/understanding-aws-cloudtrail)events are logged.
- **CloudTrail Type: **Select the **OrgCloudTrail** checkbox, if it is an organization CloudTrail.
- **CloudTrail Bucket Name: **Enter the S3 bucket name.
- **Prefix **(Optional): Enter the prefix, if any.
- **Bucket Account ID: **Enter the 12-digit AWS account ID.
- **Organization ID: **Enter the AWS organization ID.
- Under **Configure Data Events (Optional)**, enter the S3 bucket details where the data events are stored:
- **CloudTrail Type: **Select the **OrgCloudTrail** checkbox, if it is an organization CloudTrail.
- **CloudTrail Bucket Name: **Enter the S3 bucket name.
- **Prefix **(Optional): Enter the prefix, if any.
- **Bucket Account ID: **Enter the 12-digit AWS account ID.
- Click **Apply**.
[See image.](#accountdetailswindow)
-
Under **Download and Deploy** Template, select the template type (**CloudFormation **or **Terraform**) and deploy the following templates:
- [Monitoring Scope](#monitoring-scope-deployment)
- [CloudTrail](#cloudtrail-deployment)
- [Data Events](#dataevents-deployment)
[See image.](#downloaddeploytemplate)
- Click **Done**.
DSPM validates the template deployment every hour by checking the [roles created and permissions assigned](/dspm/viewing-roles-and-templates). You can also run an [on-demand validation](/dspm/validating-cloud-accounts) to check if the target accounts are onboarded successfully.
You can view the status of the target accounts on the [Overview](/dspm/viewing-onboarding-status) page.
- [][To deploy CloudFormation template](#deploy-ms-cloudformation)
- [To deploy Terraform template](#deploy-ms-terraform)
- [][To deploy CloudFormation template](#cft-download-template)
- [To deploy Terraform template](#deploy-terraform-cloudtrail)
- [][][a. Download the monitoring scope template.](#download-ms-CFT)
- [b. Create StackSets in the AWS Management Console.](#ms-cloudformation-deployment)
- [][a. Download the monitoring scope template.](#download-ms-terraform)
- [b. Update and deploy the Terraform files.](#ms-terraform-deployment)
- [][To deploy the CloudFormation template](#deploycftdataevents)
- [To deploy the Terraform template](#terrafromdeployment-dataevents)
- [][a. Download the Data Events template.](#clickdataevents)
- [b. Create stacks in the AWS Management Console.](#dataevents-cft)
[]Click **Data Events** to download the template as a YAML file to your local system.
- []Sign in to the [AWS Management Console](https://aws.amazon.com/console/) and go to **CloudFormation**.
- In the left-side navigation, select **Stacks**.
- Click **Create stack**.
-
On the **Create stack** page:
- **Prepare template**: Select **Template is ready**.
- **Specify template**: Select **Upload a template file **to upload the template you downloaded from the DSPM Admin Portal.
- **Upload a template file**: Click **Choose file**, browse and select the template.
[See image.](#createstakpage)
- Click **Next**.
- On the **Specify stack details **page, under **Stack name**, enter a unique stack name and click **Next**.
-
On the **Configure stack options** page, select the **I acknowledge** checkbox for AWS CloudFormation to create IAM resources with custom names and click **Next**.
[See image.](#configurestackoption)
- On the **Review and create** page, click **Submit**.
- []Update the `backend.tf` file with the name of the storage services where you want to store the Terraform state files. For example:
- **bucket**: Enter the name of the S3 bucket.
- **region**: Enter the region where the S3 bucket is present.
- **dynamodb_table**: Enter the name of the DynamoDB table.
- Copy the access keys** **of the root account to run the Terraform template. The access keys provide DSPM with administrator access to the root account.
- Sign in to the AWS access portal and select the root account.
-
Click **Access keys**.
[See image.](#aws-accessportal-accesskeys)
- Select the required tab (macOS/Linux, Windows, PowerShell) based on your operating system.
-
Under **Option 1: Set AWS environment variables**, click **Copy **and save the access keys.
[See image.](#aws-envivariables)
- Open the Command Prompt or any other CLI app in your local system.
- Switch to the directory that contains the Terraform template.
- Paste the access keys you copied earlier and press `Enter`.
- Run the following commands:
-
To initialize the Terraform working directory:
`terraform init`
[See image.](#cloudtrailinitcmd)
-
To verify the changes in the Terraform configuration:
`terraform plan`
-
To run the Terraform script:
`terraform apply`
[See image.](#cloudtrail-applycmd)
For **Do you want to perform these actions?**, enter `yes`** **and press `Enter`.
[See image.](#dspm-aws-tfconfirm)
[]Click **Monitoring Scope** to download the template as a ZIP file and extract it to your local system. The ZIP file includes:
- []A CSV file that contains the target account details.
- A YAML file.
[]Click **Monitoring Scope** to download the template as a ZIP file and extract it to your local system. The ZIP file includes:
- A CSV file with the target account details.
- Multiple Terraform files with policies and permissions.
- A README file with instructions for running the template.
- []Sign in to the target account and go to **CloudFormation**.
- In the left-side navigation, select **StackSets**.
- Click **Create StackSet**.
-
On the **Choose a template** page:
- **Permissions**: Select **Service managed permissions**.
- **Prerequisite - Prepare template**: Select **Template is ready**.
- **Specify template**: Select **Upload a template file** and click **Choose file**. Browse to the location where the downloaded ZIP file is extracted, select the YAML file, and then click **Open**.
[See image.](#choose-mstemplate-page)
- Click **Next**.
-
On the **Specify StackSet Details** page:
- **StackSet name**: Enter a unique and friendly name for the StackSet.
- Verify the parameters that are auto-populated.
[See image.](#specify-msstacksetdetails)
- Click **Next**.
-
On the **Configure StackSet options** page, select the **I acknowledge** checkbox for AWS CloudFormation to create IAM resources with custom names and click **Next**.
[See image.](#configure-msstacksetoptions)
-
[]On the **Set deployment options** page:
- **Add stacks to stack set**: Select **Deploy new stacks**.
- **Deployment targets**: Select **Deploy to organization**.
- []**Auto-deployment options:**
- **Automatic deployment**:** **Select **Activated** to automatically deploy additional stack instances for any new account added to the OU in the future.
- **Account removal behavior**:** **Select **Delete stacks** to remove stack instances if an account is removed from the OU.
- **Specify regions: **Select the regions in which the data stores must be scanned.
- **Region concurrency**: Select **Sequential** to deploy the StackSets in a sequential order.
[See image.](#ms-setdeploymentoptions)
- Click **Next**.
-
On the **Review **page, review the StackSet details and click **Submit**.
On the **Operations** tab, you can view the status of the StackSet deployment.
[See image.](#ms-operationstab)
-
[]Update the `backend.tf` file with the name of the storage services where you want to store the Terraform state files. For example:
- **bucket**: Enter the name of the S3 bucket.
- **region**: Enter the primary region of the target account.
- **dynamoDB_table**: Enter the name of the dynamoDB table in the primary region of the target account.
[See image.](#backend-targetfile)
- Open the Command Prompt or any other CLI app in your local system.
- Switch to the directory containing the downloaded Terraform files.
- Copy and paste the access keys of the target account and press `Enter`.
- Run the following commands:
-
To initialize the Terraform working directory:
`terraform init`
[See image.](#msterraform-init)
-
To verify the changes in the Terraform configuration:
`terraform plan`
-
To run the Terraform script:
`terraform apply`
Under **Do you want to perform these actions?**, enter `yes`** **and press `Enter`.
[See image.](#ms-terraformapply)
- [][a. Download the CloudTrail template.](#click-cft-cloudtrail)
- [b. Create stacks in the AWS Management Console.](#create-stacks)
- [][a. Download the CloudTrail template.](#cloudtrail-terraform)
- [b. Update and deploy the Terraform files.](#cloudtrail-td-terraform)
[]Click **CloudTrail **to download the template as a YAML file to your local system.
- []Sign in to the AWS account where CloudTrail S3 bucket is available and go to **CloudFormation**.
- In the left-side navigation, select **Stacks**.
- Click **Create stack**.
-
On the **Create stack** page:
- **Prepare template**: Select **Choose an existing template**.
- **Specify template**: Select **Upload a template file **to upload the template you downloaded from the DSPM Admin Portal.
- **Upload a template file**: Click **Choose file**, browse and select the template.
[See image.](#createstackpage)
- Click **Next**.
- On the **Specify stack details **page, under **Stack name**, enter a unique stack name and click **Next**.
-
On the **Configure stack options** page, select the **I acknowledge** checkbox for AWS CloudFormation to create IAM resources with custom names and click **Next**.
[See image.](#configurestackoptions)
- On the **Review and create** page, click **Submit**.
-
[]Update the `backend.tf file` with the name of the storage services where you want to store the Terraform state files. For example:
- **bucket**: Enter the name of the S3 bucket.
- **region**: Enter the region.
- **dynamodb_table**: Enter the name of the dynamoDB table.
[See image.](#cloudtrail-backendfile)
- Open the Command Prompt or any other CLI app in your local system.
- Switch to the directory that contains the Terraform template.
-
Copy and paste the access keys of the account and press `Enter`.
[See image.](#cloudtrail-accesskeys)
- Run the following commands:
-
To initialize the Terraform working directory:
`terraform init`
[See image.](#cloudtrailinit-cmd)
-
To verify the changes in the Terraform configuration:
`terraform plan`
-
To run the Terraform script:
`terraform apply`
[See image.](#terraform-cloudtrailapply)
For **Do you want to perform these actions?**, enter `yes`** **and press `Enter`.
[See image.](#confirm-templatedeployment)
[]Click **CloudTrail **to download the template as a ZIP file and extract it to your local system. The ZIP file includes:
- Multiple Terraform files.
- A README file with instructions for running the template.
[]![The account details window with target and CloudTrail details.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-account-details-and-deploying-templates/dspm-account-details-window_0.png)
![The download and deploy template section with the template type, monitoring scope, and CloudTrail templates.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-account-details-and-deploying-templates/dspm-account-details-template-deployment.png)
[]
![The step 1 of CloudFormation stackset creation page to choose the monitoring scope template..](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-account-details-and-deploying-templates/aws-monitoring-scope-choose-template-page.png)
[]
[]![The step 2 of CloudFormation stackset creation page to specify stackset details.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-account-details-and-deploying-templates/aws-ms-specify-stackset-details-page_0.png)
![The step 3 of CloudFormation stackset creation page to configure stackset options.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-account-details-and-deploying-templates/aws-ms-configure-stackset-options-page.png)
[]
![The step 4 of CloudFormation stackset creation page to set deployment options.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-account-details-and-deploying-templates/aws-ms-set-deployment-options_0.png)
[]
![The operations tab displaying the status of stackset creation with created and completed time.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-account-details-and-deploying-templates/aws-ms-operations-succeeded.png)
[]
![The backend.tf file with s3 bucket details, primary region, and dynamoDB table details.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-account-details-and-deploying-templates/backendterrformfile_0.png)
[]
![The command prompt section showing the output of terraform init command.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-account-details-and-deploying-templates/cmd-ms-terraforminit.png)
[]
![The output of terraform apply command to confirm the deployment of the template.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-account-details-and-deploying-templates/ms-terraform-apply.png)
[]
![The create stack page with stack details and template upload section.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-account-details-and-deploying-templates/aws-create-stack-page.png)
[]
![The configure stack options page with available stack options and a checkbox to confirm the creation of IAM resources.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-account-details-and-deploying-templates/aws-configure-stack-options.png)
[]
![The command prompt section showing the output of terraform init command.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-account-details-and-deploying-templates/dspm-cloutrail-init.png)
[]
![The output of terraform apply command to confirm the deployment of the template.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-account-details-and-deploying-templates/dspm-cloudtrail-tfapply.png)
[]
![The output of terraform apply command to confirm the deployment of the template.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-account-details-and-deploying-templates/dspm-aws-tfconfirm.png)
[]
![The backend.tf file with s3 bucket details, primary region, and dynamoDB table details.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-account-details-and-deploying-templates/backendterrformfile_1.png)
[]
![The command prompt section displaying the command to connect to the AWS account.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-account-details-and-deploying-templates/accesskeys-cloudtrail.png)
[]
[]![Copy the Access keys](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-awsaccesskeys_0.png)
[]![Copy the AWS environment variables](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-awsaccesskeys-envi-variables_0.png)
[]![Run the init command](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-cloutrail-init_0.png)
[]![Run the apply command](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-cloudtrail-tfapply.png)
[]![Confirm the actions to perform](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-tfconfirm.png)
[]![The Create stack page with the list of details that must be provided.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/aws-create-stack-page.png)
![The configure stack options page with available stack options and a checkbox to confirm the creation of IAM resources.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-account-details-and-deploying-templates/aws-configure-stack-options.png)
[]