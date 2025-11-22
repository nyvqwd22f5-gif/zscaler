# Onboarding an AWS Organization
Source: https://help.zscaler.com/dspm/onboarding-aws-organization
PDF: https://help.zscaler.com/pdf/com/en/1474896.pdf

You can onboard an AWS organization and its associated accounts. DSPM monitors and [scans](/dspm/about-scan-settings) the [data stores](/dspm/supported-data-stores) (e.g., S3, EC2 instances, RDS instances and clusters) in the onboarded accounts to identify sensitive data and vulnerabilities.
Onboarding Workflow
The onboarding process is illustrated in the following image:
[See image.](#aws-orgillustration)
Prerequisites
Before onboarding an AWS organization, ensure you have completed the following:
- Identify an AWS account as the orchestrator account. The DSPM template is deployed in this account to scan the data in the target accounts.
- Identify the target AWS accounts that need to be monitored and protected. DSPM defines these target accounts as monitoring scope.
- You must be assigned either an [Administrator role](/dspm/predefined-roles-and-permissions) or any role with Add Accounts permissions in the DSPM Admin Portal.
- Configure[ ][CloudTrail](/dspm/about-cloudtrail) for management and data events. This allows DSPM to perform incremental [data scans](/dspm/about-scan-settings) on S3 buckets. To enable data event for S3 buckets:
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/) and go to **CloudTrail**.
- Under **Trails**, click the name of the CloudTrail that must be used to store data events.
-
Under **Data events**, click **Edit**.
[See image.](#editdataeventsfors3)
-
For **All current and future S3 buckets**, select the **Write** checkbox.
[See image.](#allcurrentfutues3)
- Click **Save changes**.
- Identify the template type you want to use:
- [][CloudFormation Template](#cloudform-template-prereq)
- [][Terraform Template](#terraform-template-prereq)
Onboarding an AWS Organization
To onboard an AWS organization:
- [Provide AWS organization details.](/dspm/adding-organization-details)
- [Deploy the tree discovery template.](/dspm/deploying-aws-tree-discovery-template)
- [Select the network configuration, orchestrator account, monitoring scope, and business unit.](/dspm/selecting-aws-orchestrator-and-monitoring-scope)
- [Deploy the orchestrator and monitoring scope templates.](/dspm/deploying-orchestrator-and-monitoring-scope-templates)
[]To use the CloudFormation template:
- Understand the following AWS concepts:
- **Stacks**: A collection of AWS resources that can be managed as a single unit. They are required to run the DSPM templates. To learn more, refer to the [AWS documentation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacks.html).
- **StackSets**: An entity that allows you to create, update, or delete stacks across multiple AWS accounts and regions using a CloudFormation template. StackSets are required to run the DSPM templates. It also allows you to add a new region to an existing StackSet (e.g., add secondary regions for orchestrator setup). To learn more, refer to the [AWS documentation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stackinstances-create.html).
- **Identity and Access Management (IAM) Roles**: IAM roles are entities that assign specific permissions to allow trusted identities to perform actions in AWS. To learn more, refer to the [AWS documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html).
- **Subnet**: A subnet is a range of IP addresses in your VPC that can be connected to the internet, other VPCs, or data centers. To learn more, refer to the [AWS documentation](https://docs.aws.amazon.com/vpc/latest/userguide/how-it-works.html).
- Create the following IAM roles in the orchestrator account to establish a trust relationship between the orchestrator account and target accounts. The IAM roles are required to create stacks and StackSets that are used to deploy the DSPM template in the AWS organization.
- [AWSCloudFormationStackSetAdministrationRole](#stacksetadminrole)
- [AWSCloudFormationStackSetExecutionRole](#executionrole)
- Create the [AWSCloudFormationStackSetExecutionRole](#execiamrole) IAM role on all the target accounts with a trust relationship with the root account and the AWSCloudFormationStackSetAdministrationRole role. This is required to deploy the DSPM templates on the target accounts via the root account.
- Ensure that each AWS region has at least two default subnets in the default virtual private clouds (VPC). DSPM creates subnets to launch AWS cloud resources (e.g., EC2 instances, S3 buckets) in specific subnets.
[]To use the Terraform template:
- Install the following on your local system:
- Terraform CLI to run the Terraform templates.
-
AWS CLI 2.22 version or later to connect to the AWS organization.
For instructions on installing or updating AWS CLI, refer to the [AWS documentation](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).
- Identify the storage services in the primary region of the orchestrator account to store the Terraform state files. You can use an existing storage service or create a new one. For example:
- [][AWS S3 Bucket](#aws-s3-bucket)
- [][DynamoDB Table](#DynamoDB-table)
[]To create an AWS S3 bucket:
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/) and go to **S3**.
- Click **Create bucket**.
- Under **Bucket name**, enter a unique name to the S3 bucket.
- Click **Create bucket**.
[]To create a DynamoDB table:
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/) and go to **DynamoDB**.
- Click **Create table**.
- On the **Table details** page:
- **Table name**: Enter a unique name to the table.
- **Partition key**: Enter **LockID**.
- Click **Create table**.
[]This IAM role with admin permissions creates a trust relationship with the CloudFormation service.
To create the AWSCloudFormationStackSetAdministrationRole role:
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/) and go to **IAM**.
- In the left-side navigation, select **Roles**.
- Click **Create Role**.
- In the **Select trusted entity** page:
- **Trusted entity type**: Select the **AWS account** tile.
- **An AWS account**: Select **This account (<root account ID>).**
- Click **Next**.
- In the **Add permissions **page, select the **AdministratorAccess** policy from the table and click **Next**.
- In the **Name, review, and create **page, under **Role name**, enter the role name as **AWSCloudFormationStackSetAdministrationRole**.
- Click **Create role**.
- On the **Permissions** tab, click **Add permissions** and then select **Create inline policy** from the drop-down menu.
- On the **Specify permissions** page, under **Policy editor**, select **JSON**.
-
Copy the following JSON text and paste it in the **Policy editor** text box.
`{
"Version": "2012-10-17",
"Statement": [
{
"Action": [
"sts:AssumeRole"
],
"Resource": [
"arn:aws:iam::*:role/AWSCloudFormationStackSetExecutionRole"
],
"Effect": "Allow"
}
]
}`
- Click **Next**.
- On the **Review and create** page, under **Policy name**, enter `AWSCloudFormationStackSetAdministrationPolicy`.
- Click **Create policy**.
[]This IAM role creates a trust relationship with the administrator account and the AWSCloudFormationStackSetAdministrationRole IAM role.
[]To create the AWSCloudFormationStackSetExecutionRole role:
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/) and go to **IAM**.
- In the left-side navigation, select **Roles**.
- Click **Create Role**.
- In the **Select trusted entity** page:
- **Trusted entity type**: Select the **AWS account** tile.
- **An AWS account**: Select **This account (<root account ID>)**.
- Click **Next**.
- In the **Add permissions **page, select **AdministratorAccess **and **SystemAdministrator** policy from the table and click **Next**.
- In the **Name, review, and create **page, under **Role name**, enter the role name as **AWSCloudFormationStackSetExecutionRole**.
- Click **Create role**.
- On the **Permissions** tab, click **Add permissions** and then select **Create inline policy **to provide additional permissions from the drop-down menu.
- On the **Specify permissions** page, under **Policy editor**, select **JSON**.
-
Copy the following JSON text and paste it in the **Policy editor** text box.
`{
"Version": "2012-10-17",
"Statement": [
{
"Effect": "Allow",
"Action": [
"cloudformation:*"
],
"Resource": "*"
}
]
}`
- Click **Next**.
- On the **Review and create** page, under **Policy name**, enter `ScannerCFT`.
- Click **Create policy**.
[]![The AWS organization onboarding workflow represented in a flow chart.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/Workflow_DSPM_Onboarding-AWS_v3.png)
[]![Enable S3 data events for CloudTrail](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspmcloudtrail-dataevents-s3.png)
[]![Edit Data Events for S3 bucket](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-dataevents-edit.png)