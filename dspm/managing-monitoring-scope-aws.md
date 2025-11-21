# Managing Monitoring Scope for AWS
Source: https://help.zscaler.com/dspm/managing-monitoring-scope-aws
PDF: https://help.zscaler.com/pdf/com/en/1478016.pdf

The monitoring scope refers to the AWS target accounts that are onboarded. When new accounts are added to your organization, you can onboard them to DSPM for monitoring data stores. You can add new accounts to the monitoring scope, but you cannot remove the existing target accounts.
Additionally, you can enable autodetection at the organization or organizational unit (OU) level. The autodetection feature enables DSPM to automatically detect and onboard any new accounts added to the organization or OU in the future. This eliminates the need to manually onboard new accounts to DSPM.
Prerequisites
You must be assigned either an [Administrator role](/dspm/predefined-roles-and-permissions) or any role with the Configure Monitoring Scope permission in the DSPM Admin Portal.
Managing Monitoring Scope
To add new accounts to the monitoring scope:
- Go to **Administration** > **Configuration** >** Cloud Accounts**.
-
Select the organization for which you want to add new target accounts.
[See image.](#select-org)
-
Click **Manage**, and then select **Monitoring and Autodetect** from the drop-down menu.
[See image.](#actions-monitorin)
-
On the **Add Accounts to Monitoring Scope** page, select the accounts that you want to be monitored.
[See image.](#add-accounts)
Enable **Autodetection** at the organization or OU level so DSPM can automatically detect and onboard any new accounts that are added in the future. Click **Next**.
You must activate [automatic deployment](#auto-deployment-options) in AWS to automatically deploy stack instances for newly added account in the future.
-
On the **Assign Business Units** page, change the [business unit](/dspm/about-business-units) for the OU if required, then click **Next**.
[See image.](#assign-bu)
-
On the **Apply Changes** page, download the monitoring scope template and run it in the [AWS console](https://aws.amazon.com/console/).
- [Template Type](#templatetype)
- [Monitoring Scope](#monitoring-scope)
- [Autodetection](#autodetection)
[See image.](#applychanges)
-
Click **Done**.
The new target accounts are added to the monitoring scope. You can view all the organization's onboarded accounts in the [Accounts tab](/dspm/viewing-cloud-accounts-and-organizations).
[]Select the **CloudFormation **or **Terraform **template.
[]
- [Run the CloudFormation template](#cloudformation)
- [Run the Terraform template](#terraform)
[]
- [i. Download the monitoring scope template.](#dspm-portal)
- [ii. Update the StackSet.](#aws-console)
[]Click **Monitoring Scope** to download the template as a .zip file and extract it to your local system. The .zip file contains two files:
- []A CSV file that contains a list of target accounts that needs to be scanned.
- []A YAML file that contains the policies and permissions required for DSPM to connect to AWS organization.
- []Sign in to the [AWS Management Console](https://aws.amazon.com/console/) root account and go to **CloudFormation**.
-
In the left-side navigation, select **StackSets**.
[See image.](#stacksets)
-
Identify the StackSet created for monitoring scope while [onboarding the organization](/dspm/onboarding-aws-organization) and click **StackSet name**.
[See image.](#stacksetname)
-
Under **Actions**, click **Edit StackSet details**.
[See image.](#editstackset)
-
On the **Choose a template** page:
- **Prerequisite - Prepare template**: Select **Replace current template**.
- **Specify template**: Select **Upload a template file**.
- **Upload a template file**: Click **Choose file**, browse your folder and select the YAML file [downloaded from the DSPM Admin Portal](#yamlfile), then click **Open**.
[See image.](#choosetemplate)
- Click **Next**.
- On the **Specify StackSet Details** page, click **Next**.
- On the **Configure StackSet options** page, click **Next**.
-
On the **Set deployment options** page:
- Select **Deploy to accounts **and then select **Deploy stacks in accounts**.
- **Account numbers**: Add the new account numbers or upload the .csv file [downloaded from the DSPM Admin Portal](#yamlfile).
- **Specify regions: **Select the regions that contain the data stores that you want to scan.
- **Region concurrency**: Select **Sequential** to deploy the StackSets in a sequential order as specified in the **Specify regions**.
[See image.](#setdeploymntoptions)
- Click **Next**.
-
On the **Review** page, review the StackSet details and then select the **I acknowledge** checkbox to acknowledge AWS CloudFormation's creation of IAM resources with custom names.
[See image.](#reviewdetails)
-
Click **Submit**.
On the **Operations** tab, you can see the status of the StackSet execution.
[See image.](#operations)
On the **Stack Instances** tab, you can view the stack instances created for each account and region. To complete the StackSet execution, all the individual stack instances must be deployed successfully.
[See image.](#stackinstances)
[]
- [i. Download the monitoring scope template.](#dspmterraform)
- [ii. Copy the access keys of the target account.](#awsaccessportal)
- [iii. Update and run the Terraform files.](#localsystem)
[]Click **Monitoring Scope** to download the Terraform template as a .zip file and extract it to your local system. The .zip file contains the following files:
- []A .CSV file containing the list of target accounts that you want to be monitored.
- Multiple Terraform files that contains policies and permissions required for the DSPM to connect to the AWS organization.
- A Readme file that contains the instructions to run the template.
[]The access keys provide DSPM with administrator access to the target account from the AWS CLI.
- []Sign in to the AWS access portal and select the target account.
-
Click **Access keys**.
[See image.](#accessportal)
- Select the required tab (macOS/Linux, Windows, PowerShell) based on your operating system.
-
Under **Option 1: Set AWS environment variables**, click **Copy **and save the access keys.
[See image.](#accesskeys)
[]
- Update the [downloaded Terraform files](#terraform-files):
-
In the **parameters.auto.tfvars** file, under **regions**, enter the primary region of the target account.
[See image.](#parametersfile)
-
In the **backend.tf** file, add the name of the storage services where you want to store the Terraform state files. For example:
- **bucket**: Enter the name of the S3 bucket of the target account.
- **region**: Enter the primary region of the target account.
- **dynamoDB_table**: Enter the name of the dynamoDB table in the primary region of the target account.
[See image.](#backednfile)
- Open the Command prompt or any other CLI app in your local system.
- Switch to the directory containing the downloaded Terraform files.
- Paste the [access keys](#acceskeys-target) you copied earlier and press `Enter`.
- Run the following commands:
-
To initialize the Terraform working directory:
`terraform init`
[See image.](#terraforminit)
-
To verify the changes in the Terraform configuration:
`terraform plan`
-
To run the Terraform script:
`terraform apply`
[See image.](#terraformapply)
Under **Do you want to perform these actions?**, enter `yes`** **and press `Enter`.
[See image.](#terraformconfig)
[]Review the list of OUs that you selected for autodetection.
[]![Select the Organization to add the monitoring scope](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/monitoring-scope-1.png)
[]![Select Monitoring and Auto-Detect](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/dspm-manage-monitoring-scope.png)
[]![Add accounts to monitoring scope](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/dspm-add-to-monitoring-scope_0.png)
[]![Assign Business Units to Organizational Unit](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/dspm-assign-bu-ms.png)
[]![Review the Changes](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/dspm-apply-changes.png)
[]![Select StackSets in the Left-side navigation](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/dspm-aws-select-stacksets-leftnavigation.png)
[]![Click the StackSet name](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/dspm-aws-identify-ms-stackset.png)
[]![Edit StackSet details](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/dspm-aws-actions-edit-stackset-details.png)
[]![Upload the YAML template](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/dspm-aws-choose-template-page.png)
[]![Review the StackSet details](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/dspm-specify-stackset-details.png)
[]![View the Stack instances](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/dspm-aws-stack-instances-tab.png)
[]![View the Operations tab](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/dspm-aws-operations-tab.png)
[]![AWS access portal](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/dspm-aws-access-portal.png)
[]![Access keys on the AWS access portal](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/dspm-aws-access-keys.png)
[]![Update the parameters file](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/target-parameter-file.png)
[]![update the backend terraform file](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/update-backend-file.png)
[]![Run the terraform init command](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/target-terraform-init.png)
[]![Run the terraform apply command](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/target-terraform-apply.png)
[]![Apply the terraform configuration](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/target-perform-actions.png)
[]![Set deployment options](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-monitoring-scope-aws/dspm-set-deployment-options_0.png)