# Deploying the AWS Tree Discovery Template
Source: https://help.zscaler.com/dspm/deploying-aws-tree-discovery-template
PDF: https://help.zscaler.com/pdf/com/en/1525746.pdf

After adding the [organization details](/dspm/adding-organization-details), deploy the tree discovery template. This template includes the policies and permissions required to create IAM roles in the AWS root account, along with the Cloudtrail details required to perform incremental [data scans](/dspm/about-scan-settings). The IAM roles provide DSPM with read-only access to discover the resources in the AWS organization.
Deploying the Templates
When the CloudTrail S3 bucket is present in one of the following accounts:
- **Management account**: DSPM generates only the tree discovery template. Download and deploy this template in the AWS root account.
- **An account other than the management account**: DSPM generates both the CloudTrail and tree discovery templates. Deploy the CloudTrail template in the AWS account where the CloudTrail S3 bucket is present, and then deploy the tree discovery template. The CloudTrail template provides DSPM with the access required to analyze the trails and perform incremental data scans.
To deploy the templates:
- Under **Connect to the Organization**, for **Template Type**, select **CloudFormation** or **Terraform**.
-
Click **CloudTrail** to download the template to your local system.
- [Deploy the CloudFormation template in AWS.](#cloudtrail-treediscovery)
- [Deploy the Terraform template in AWS.](#cloudtrail-td-terraform)
[See image.](#cloudtrailtemplatedeployment)
-
Click **Tree Discovery** to download the template to your local system.
- [Deploy the CloudFormation template in AWS.](#tree-discovery)
- [Deploy the Terraform template in AWS.](#td-localsystem)
[See image.](#connectorgstep2)
DSPM validates the template deployment every hour by checking the IAM roles and permissions.
You can also validate the template immediately by clicking **Validate**.
[See image.](#validate-tree-discovery)
If the validation is successful, you are directed to the [Orchestrator & Monitoring Scope](/dspm/selecting-aws-orchestrator-and-monitoring-scope) section.
- []Sign in to the [AWS Management Console](https://aws.amazon.com/console/) and go to **CloudFormation**.
- In the left-side navigation, select **Stacks**.
-
Click **Create stack**.
[See image.](#createstackbutton)
-
On the **Create stack** page:
- **Prepare template**: Select **Choose an existing template**.
- **Specify template**: Select **Upload a template file **to upload the template you downloaded from the DSPM Admin Portal.
- **Upload a template file**: Click **Choose file**, browse and select template, then click **Open**.
[See image.](#createstackaws)
- Click **Next**.
-
On the **Specify stack details **page, under **Stack name**, enter a unique stack name.
[See image.](#aws-specifystackdet)
- Click **Next**.
- On the **Configure stack options** page, click **Next**.
-
On the **Review and create** page, under **Capabilities**, select the **I acknowledge** checkbox to acknowledge AWS CloudFormation's creation of IAM resources with custom names.
[See image.](#aws-acknoweledgestack)
- Click **Submit**.
- []Update the `backend.tf` file with the name of the storage services where you want to store the Terraform state files. For example:
- **bucket**: Enter the name of the S3 bucket.
- **region**: Enter the primary region.
- **dynamodb_table**: Enter the name of the dynamoDB table.
- Open the Command Prompt or any other CLI app in your local system.
- Switch to the directory that contains the Terraform template.
- Copy and paste the access keys of the root account and press `Enter`.
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
- []Sign in to the [AWS Management Console](https://aws.amazon.com/console/) and go to **CloudFormation**.
- In the left-side navigation, select **Stacks**.
-
Click **Create stack**.
[See image.](#aws-stack)
-
On the **Create stack** page:
- **Prepare template**: Select **Template is ready**.
- **Specify template**: Select **Upload a template file **to upload the template you downloaded from the DSPM Admin Portal.
- **Upload a template file**: Click **Choose file**, browse and select template, then click **Open**.
[See image.](#create-stack)
- Click **Next**.
-
On the **Specify stack details **page, under **Stack name**, enter a unique stack name.
[See image.](#specify-stack)
- Click **Next**.
- On the **Configure stack options** page, click **Next**.
-
On the **Review and create** page, under **Capabilities**, select the **I acknowledge** checkbox to acknowledge AWS CloudFormation's creation of IAM resources with custom names.
[See image.](#acknowledgement)
- Click **Submit**.
- []Update the `backend.tf` file with the name of the storage services where you want to store the Terraform state files. For example:
- **bucket**: Enter the name of the S3 bucket.
- **region**: Enter the region.
- **dynamodb_table**: Enter the name of the dynamoDB table.
- Open the Command Prompt or any other CLI app in your local system.
- Switch to the directory that contains the Terraform template.
- Copy and paste the access keys of the target account and press `Enter`.
- Run the following commands:
-
To initialize the Terraform working directory:
`terraform init`
[See image.](#td-init)
-
To verify the changes in the Terraform configuration:
`terraform plan`
-
To run the Terraform script:
`terraform apply`
[See image.](#td-apply)
For **Do you want to perform these actions?**, enter `yes`** **and press `Enter`.
[See image.](#td-perform)
[]![Run the CloudTrail template](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/deploying-aws-tree-discovery-template/dspm-cloudtrail-template.png)
[]![Connect to the Organization section](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/deploying-aws-tree-discovery-template/dspm-tree-discovery-template.png)
[]![Validate the template execution](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-validate-tree-discovery.png)
[]![Create stack button](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-awscreatestack-button.png)
[]![Create Stack page](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-create-stack_0.png)
[]![Specify stack details page](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-specifystacksetdetails.png)
[]![Acknowledge the stack creation](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-acknowledge-stackcreation.png)
[]![Run the init command](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-cloutrail-init_0.png)
[]![Run the apply command](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-cloudtrail-tfapply.png)
[]![dspm-aws-tfconfirm.png](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-tfconfirm.png)
[]![Create a stack in the AWS Console](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-cloudformation-stack.png)
[]![Create a stack in the AWS Management Console](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-create-stack.png)
[]![Specify Stack details in the AWS console](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/aws-specify-stackset-details-page.png)
[]![Select the acknowledgement checkbox](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-acknowledgemtn.png)
[]![Initialize the directory](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/td-terraform-init.png)
[]![Run the terraform apply command](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/td-terraform-apply.png)
[]![Apply the changes](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/aws-terraform-perform-actions.png)