# Changing AWS CloudTrail Details
Source: https://help.zscaler.com/dspm/changing-aws-cloudtrail-details
PDF: https://help.zscaler.com/pdf/com/en/1478051.pdf

You can change the [CloudTrail](/dspm/understanding-aws-cloudtrail) for an organization or a single account within the organization as required.
Prerequisites
- You must be assigned either an [Administrator role](/dspm/predefined-roles-and-permissions) or any role with Edit Cloud Accounts permission.
- To configure a cross-account CloudTrail that stores logs in an S3 bucket located in a different account than the onboarded account (member account), enable the following settings:
- [CloudTrail Permissions for Member Accounts](#memberaccount-permissions)
- [Cross-Account Log Decryption](#kmsdecrypt)
- [KMS Key ID](#kmskeyupdate)
Changing AWS CloudTrail for an Organization
The organization CloudTrail shares the CloudTrail events of the management and member accounts of the organization to the same CloudTrail S3 bucket. When you reset the organization AWS CloudTrail details, the existing CloudTrail is disabled and all the onboarded accounts move to the [Needs Attention](/dspm/viewing-organization-onboarding-status)[** **]state until the new CloudTrail is validated successfully.
To change AWS CloudTrail for an organization:
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
-
Select the organization account for which you want to change the CloudTrail details.
[See image.](#select-org)
-
Click **Manage**, and then select **Manage CloudTrail** from the drop-down menu.
[See image.](#managecloudtrail)
- In the **Organization CloudTrail** window:
-
Click **Reset** to edit the existing CloudTrail details and add new details.
[See image.](#resetoption)
- **CloudTrail Type**: If it is an [organization CloudTrail](/dspm/understanding-aws-cloudtrail)[, s]elect the **OrgCloudTrail** checkbox.
- **CloudTrail Bucket Name**: Enter the S3 bucket name that is associated with the CloudTrail.
-
**Prefix (Optional)**: Enter the prefix specified in the CloudTrail S3 bucket path, if any.
[See image.](#prefix)
- **Bucket Account ID**: Enter the AWS account ID where the CloudTrail S3 bucket is present.
-
Click **Apply**.
[See image.](#click-apply)
A message appears indicating that the CloudTrail details is saved successfully.
- Under **Download and Deploy Template, **select one of the following template types:
- [CloudFormation](#dspmoraws)
- [Terraform](#cloudtrail-terraform)
- Click **Done**.
-
In the **Overview** tab, under **CloudTrail**, click **Validate**.
[See image.](#validate-details)
After the CloudTrail is validated successfully, the status of the CloudTrail shows **Enabled**.
[See image.](#cloudtrailenabled)
If there is any issue found while validating the template, the status of the CloudTrail shows **Failed**. Download the template and run it again, and then validate the CloudTrail.
[See image.](#failed-status)
Changing AWS CloudTrail for Single or Multiple Accounts
When you update the account CloudTrail, the existing CloudTrail is disabled only for that account, without affecting the other accounts in the organization. The account moves to the [Needs Attention](/dspm/viewing-organization-onboarding-status) state until the new CloudTrail is validated successfully.
To change AWS CloudTrail for single or multiple accounts:
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
-
Select the AWS account and then select the **Accounts** tab.
[See image.](#select-the-accounts-tab)
- Choose one of the following options:
-
To change CloudTrail for a single account:
Click the **Actions** icon for the account you want to change the CloudTrail details, then select **Update CloudTrail**.
[See image.](#update-account-cloudtrail)
- To change CloudTrail for multiple accounts:
- Select the checkboxes for the required accounts.
-
From the **Actions **drop-down menu, select **Update CloudTrail**.
[See image.](#actionsdropdownmenu)
-
In the **Update Account CloudTrail** window:
-
Click **Reset** to edit the existing CloudTrail details and add new details.
[See image.](#reset-existing-cloudtrail)
- **CloudTrail Bucket Name**: Enter the S3 bucket name that is associated with CloudTrail.
- **Prefix (Optional)**: Enter the prefix specified in the CloudTrail S3 bucket path, if any.
-
**Bucket Account ID**: Enter the AWS account ID where the CloudTrail S3 bucket is present.
[See image.](#add-new-cloudtrail-details)
-
Click **Apply**.
A message appears indicating that the CloudTrail details is saved successfully.
- Under **Download and Deploy Template, **select one of the following template types:
- [CloudFormation](#accountcft)
- [Terraform](#accountctterraform)
- Click **Done**.
DSPM validates the template deployment by checking the new CloudTrail details provided.
If there is any error while validating the template, download and rerun the template.
You can see the CloudTrail details of the account in the corresponding account drawer.
[See image.](#account-drawer)
[]To update the CloudTrail details using the CloudFormation template:
- [i. Download the CloudFormation template.](#dspm)
- [ii. Update the stack.](#aws)
[]In the **Organization CloudTrail** window, click **Organization CloudTrail** to download the template as a YAML file to your local system.
- []Sign in to the [AWS Management Console](https://aws.amazon.com/console/) using the root account credentials and go to **CloudFormation**.
- In the left-side navigation, select **Stacks**.
-
Identify the stack created while [onboarding an organization](/dspm/onboarding-aws-organization) and click the stack name.
[See image.](#click-stackname)
-
Click **Update**.
[See image.](#update-option)
-
On the **Update stack** page:
- **Prepare template**: Select **Replace current template**.
- **Specify template**: Select **Upload a template file** and click **Choose file**. Browse your folder and select the [downloaded YAML file](#dspm), then click **Open**.
[See image.](#update-stack-page)
- Click **Next**.
- On the **Specify stack details** page, click **Next**.
- On the **Configure stack options** page, click **Next**.
-
On the **Review stack** page, review the stack details and then select the **I acknowledge** checkbox to acknowledge AWS CloudFormation's creation of IAM resources with custom names.
[See image.](#acknowledge)
-
Click **Submit**.
On the **Events** tab, you can view the status of the stack execution.
[See image.](#stack-update-status)
[]To update the CloudTrail details using the Terraform template:
- [i. Download the Terraform template.](#dspm-terraform)
- [ii. Copy the access keys of the root account.](#accesskeys)
- [iii. Run the Terraform template.](#cmdprompt)
[]In the **Organization CloudTrail** window, click **Organization CloudTrail** to download the template as a Terraform file to your local system.
[]Copy the **Access keys** of the root account. The access keys provide DSPM with administrator access to the root account from the AWS CLI.
To copy the access keys:
- Sign in to the AWS access portal and select the root account.
-
Click **Access keys**.
[See image.](#awsaccessportal)
- Select the required tab (macOS/Linux, Windows, PowerShell) based on your operating system.
-
[]Under **Option 1: Set AWS environment variables**, click **Copy**.
[See image.](#acceskeysacesportal)
- []Open the Command Prompt or any other CLI app in your local system.
- Switch to the directory that contains the [downloaded template .tf folder](#dspm-terraform).
- Paste the [access keys](#copy-accesskeys) you copied earlier and press `Enter`.
- Run the following commands:
-
To initialize the Terraform working directory:
``terraform init``
[See image.](#tdinit)
-
To verify the changes in the Terraform configuration:
``terraform plan``
-
To run the Terraform script:
``terraform apply``
[See image.](#td-apply)
Under **Do you want to perform these actions?**, enter `yes`** **and press `Enter`.
[See image.](#confirm)
[]To update the CloudTrail details using the CloudFormation template:
- [i. Download the CloudFormation template.](#download-cft)
- [ii. Create a stack.](#createastack)
[]In the **Update Account CloudTrail** window, click** CloudTrail** to download the template as a YAML file to your local system.
[See image.](#download-template-cloudtrail)
- []Sign in to the [AWS Management Console](https://aws.amazon.com/console/) for the account you want to change the CloudTrail, and go to **CloudFormation**.
- In the left-side navigation, select **Stacks**.
-
Click **Create stack**.
[See image.](#create-stack-new)
- On the **Create stack** page:
- **Prepare template**: Select **Choose an existing template**.
- **Specify template**: Select **Upload a template file **to upload the template you downloaded from the DSPM Admin Portal.
- **Upload a template file**: Click **Choose file**, browse and select template, then click **Open**.
- Click **Next**.
-
On the **Specify stack details **page, under **Stack name**, enter a unique stack name.
[See image.](#specify-stack-dets)
- Click **Next**.
- On the **Configure stack options** page, click **Next**.
-
On the **Review and create** page, under **Capabilities**, select the **I acknowledge** checkbox to acknowledge AWS CloudFormation's creation of IAM resources with custom names.
[See image.](#ack-stack-creation)
- Click **Submit**.
[]To update the CloudTrail details using the Terraform template:
- [i. Download the Terraform template.](#download-terraform)
- [ii. Copy the access keys of the account for which you want to change the CloudTrail details.](#accesskeystarget)
- [iii. Run the Terraform template.](#runterraform)
[]In the **Update Account CloudTrail** window, select **Terraform** and click** CloudTrail** to download the template as a Terraform file to your local system.
[See image.](#download-ct-template)
[]The access keys provide DSPM with administrator access to the account from the AWS CLI.
To copy the access keys:
- Sign in to the AWS access portal and select the account for which you want to change the CloudTrail details.
-
Click **Access keys**.
[See image.](#select-accesskeys)
- Select the required tab (macOS/Linux, Windows, PowerShell) based on your operating system.
-
[]Under **Option 1: Set AWS environment variables**, click **Copy**.
[See image.](#copy-accesskeys-new)
- []Open the Command Prompt or any other CLI app in your local system.
- Switch to the directory that contains the downloaded template .tf folder.
- Paste the [access keys](#copaccesskeys) you copied earlier and press `Enter`.
- Run the following commands:
-
To initialize the Terraform working directory:
``terraform init``
[See image.](#terraform-init-cmd)
-
To verify the changes in the Terraform configuration:
``terraform plan``
-
To run the Terraform script:
``terraform apply``
[See image.](#terraform-apply-cmd)
Under **Do you want to perform these actions?**, enter `yes`** **and press `Enter`.
[See image.](#perform-actions-tf)
- []Sign in to the [AWS account](https://aws.amazon.com/console/) where the S3 bucket that stores CloudTrail logs is available, and go to **CloudTrail**.
- Under **Trails**, select the required CloudTrail.
-
Under **General details**, click the **Trail log location**.
[See image.](#aws-cloudtrail-loglocation)
-
Select the S3 bucket, and then select the **Permissions **tab.
[See image.](#s3bucket-permissionstab)
-
Under **Bucket policy**, click **Edit **and add the following permissions to write CloudTrail logs of the member accounts in the S3 bucket:
`	{
"Sid": "AllowCloudTrailWriteLogsFor*<*CloudTrail account ID*>*",
"Effect": "Allow",
"Principal": {
"Service": "cloudtrail.amazonaws.com"
},
"Action": "s3:PutObject",
"Resource": "arn:aws:s3:::cross-bucketpolicy/AWSLogs/*<*CloudTrail account ID*>*/*",
"Condition": {
"StringEquals": {
"AWS:SourceArn": "arn:aws:cloudtrail:us-west-2:*<*CloudTrail account ID*>*:trail/cross-trail",
"s3:x-amz-acl": "bucket-owner-full-control"
}
}``{
"Sid": "AllowBucketAccessForMembers",
"Effect": "Allow",
"Principal": {
"AWS": [
"arn iam::*<*CloudTrail account ID*>*: root"
]
}
}	`
-
Click **Save changes**.
[See image.](#addpermissions)
- []Sign in to the [AWS Management Console](https://aws.amazon.com/console/) where the CloudTrail account is available, and go to **CloudTrail**.
- []Copy the S3 bucket name of the CloudTrail.
- Sign in to the member account, and go to **CloudTrail**.
- Click **Create trail**.
-
On the **Choose trail attributes** page:
- **Trail name**: Enter a unique name.
- **Storage location**: Select **Use existing S3 bucket**.
- **Trail log bucket name**: Paste the [CloudTrail](#copycloudtrail) bucket name.
- **AWS KMS alias**: Enter the KMS alias.
- Click **Next**.
[See image.](#createtrail-memberaccount)
-
On the **Choose log events** page:
- Under **Events**, select **Management events** or **Data events**.
- Click **Next**.
[See image.](#chooselogeventspage)
- On the **Review and create** page, click **Create trail**.
- On the **Trails **page, click the newly created trail.
- Under **General **details, click **AWS KMS key** to update the policy and provide access to the S3 bucket where the CloudTrail is present.
-
On the **Key policy** tab, click **Edit **to add the following policies:
[See image.](#edit-keypolicy)
`"Sid": "Enable IAM User Permissions",
"Effect": "Allow",
"Principal": {
"AWS": [
"arn:aws:iam::*<*CloudTrail Account ID*>*:root",
"arn:aws:iam::*<*S3 bucket account ID*>*:role/DSPM-Role-org-1stjuly",
"arn:aws:sts::*<*CloudTrail Account ID*>*:assumed-role/AWSReservedSSO_AdministratorAccess_2d4e2733faaf72bb/*<userID>*"
]
},`
` {
"Sid": "Enable cross account log decryption",
"Effect": "Allow",
"Principal": {
"AWS": [
"arn:aws:iam::*<*S3 bucket account ID*>*:role/DSPM-Role-org-1stjuly-get-data-events",
"arn:aws:iam::*<*S3 bucket account ID*>*:role/DSPM-Role-org-1stjuly"
]
},
"Action": [
"kms:Decrypt",
"kms:ReEncryptFrom"
],
"Resource": "*",
"Condition": {
"StringEquals": {
"kms:CallerAccount": "*<*S3 bucket account ID*>*"
},
"StringLike": {
"kms:EncryptionContext:aws:cloudtrail:arn": "arn:aws:cloudtrail:*:*<*CloudTrail Account ID*>*:trail/*"
}`
[See image.](#keypolicysection)
[]
- Sign in to the [AWS account](https://aws.amazon.com/console/) where the S3 bucket that stores CloudTrail logs is available, and go to **Roles**.
- Select the [resource discovery](/dspm/iam-roles-and-permissions-aws) role that is created by DSPM.
- Under **Permissions**, expand **DSPM-CLOUDTRAIL-KMS-POLICY **and click **Edit**.
-
[]In the **Policy editor**, add the S3 bucket account ID where the KMS key is present.
[See image.](#kmscloudtrailupdate)
`{
"Version": "2012-10-17",
"Statement": [
{
"Action": [
"kms:Decrypt",
],
"Resource": [
"arn:aws:kms:*:<CloudTrail account ID>:key*",
"arn:aws:kms:*:<S3 bucket account ID>:key*",
"Effect": "Allow",
"Sid": "DSPMCLOUDTRAILKMSPOLICY"
}
]
}`
You can also add a specific KMS key:
- Go to **KMS **> **Customer-managed keys** >** Key ID**.
-
Copy the **Key ID** and paste it in the [Policy editor](#policyeditoe).
` "arn:aws:kms:*:<S3 bucket account ID>:key <kms key ID>", `
- Click **Save**.
[]![The Manage action drop-down with annotation around Manage CloudTrail.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-manage-cloudtrail-option.png)
[]![Click Reset to edit the CloudTrail details](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-cloudtrail-window.png)
[]![The Organization CloudTrail window with annotation around CloudTrail details.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-cloudtrail-apply.png)
[]![The Overview tab displaying the details of the onboarded account, Orchestrator, and Cloudtrail.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/cloudtrail/managing-cloudtrail/dspm-aws-overview-tab.png)
[]![The CloudFormation page with the details of the stack created.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/cloudtrail/managing-cloudtrail/dspm-aws-click-stack-name.png)
[]![The CloudFormation stack page with annotation around the Update button.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/cloudtrail/managing-cloudtrail/dspm-aws-stack-update.png)
[]![The Update stack page with annotation around fields that need to be updated.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/cloudtrail/managing-cloudtrail/dspm-aws-update-stack-page.png)
[]![The Review page displaying all the provided details to review and acknowledge.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/cloudtrail/managing-cloudtrail/dspm-aws-stack-update-acknowledge.png)
[]![The Events tab to view the status of stack update.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/cloudtrail/managing-aws-cloudtrail-details/dspm-aws-event-status.png)
[]![The Overview page with orchestrator and CloudTrail details and annotation around the status.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-cloudtrail-failed-status.png)
[]![The Overview page listing the accounts onboarded to DSPM.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-org-account.png)
[]![The CloudTrail log location with annotation around prefix.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/cloudtrail/managing-aws-cloudtrail-details/dspm-aws-cloutrail-logs.png)
[]![The AWS access portal listing the AWS accounts and annotation around access keys.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/cloudtrail/managing-aws-cloudtrail-details/dspm-aws-access-portal.png)
[]![The IAM credentials page for the selected account and annotation around Copy button.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/cloudtrail/managing-aws-cloudtrail-details/dspm-aws-copy-accesskeys.png)
[]![The command prompt section with the output of terraform init command.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/cloudtrail/managing-aws-cloudtrail-details/td-terraform-init.png)
[]![The command prompt section with the initial configuration of terraform apply command](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/cloudtrail/managing-aws-cloudtrail-details/td-terraform-apply.png)
[]![The command prompt section with the output of the terraform apply command.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/cloudtrail/managing-aws-cloudtrail-details/aws-terraform-perform-actions.png)
[]![The Overview page with the status of the updated CloudTrail.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/aws-overview-tab-status.png)
[]![The Accounts tab displaying the list of accounts onboarded.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-org-accounts-tab.png)
[]![The Action dropdown with annotation around Update CloudTrail option.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-update-cloudtrail-option.png)
[]![The Update Account CloudTrail window with annotation around Reset button.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-update-account-cloudtrail-window.png)
[]![The Update Account CloudTrail window with the details of the new CloudTrail.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-updateaccount-cloudtrail.png)
[]![View the CloudTrail information in the Account Drawer](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-account-drawer.png)
[]![The Update Account CloudTrail window with annotation around CloudTrail template.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-updateaccount-cloudtrail-template.png)
[]![The CloudFormation page with annotation around Create stack button.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-create-stack.png)
[]![The Specify Stack details page with the details of the new stack.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-specify-stackset-details.png)
[]![The Review and create page with the details of all the entered fields to review and acknowledge.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-acknowledge-stack.png)
[]![The AWS access portal with list of available account and annotation around Access keys.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-click-access-keys.png)
[]![Copy the access keys](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/cloudtrail/managing-aws-cloudtrail-details/dspm-aws-copy-accesskeys.png)
[]![The command prompt section with the output of terraform init command.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/td-terraform-init.png)
[]![The command prompt section with the configuration of terraform apply command.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/td-terraform-apply.png)
[]![The command prompt section with the output of Terraform apply command.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/aws-terraform-perform-actions.png)
[]![The Update Account CloudTrail window with CloudTrail details in the DPSM Admin Portal.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-updateaccount-cloudtrail-template.png)
[]![The general details of the CloudTrail with Trail log location blurred.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-cloudtrail-log-location.png)
[]![The S3 bucket page with list of available tabs and annotation around Permissions tab](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/cloudtrail/managing-aws-cloudtrail-details/dspm-aws-permissions-tab.png)
[]![The Edit bucket policy section with the permissions added.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/cloudtrail/managing-aws-cloudtrail-details/dspm-policy-edit.png)
[]![The Choose trail attributes page with details of all required fields.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/cloudtrail/managing-aws-cloudtrail-details/dspm-create-trail-memberaccount.png)
[]![The KMS key policy page with the permissions added.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/cloudtrail/managing-aws-cloudtrail-details/dspm-cloudtrail-keypolicy.png)
[]![The Choose log events page displaying all the required fields.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/cloudtrail/managing-aws-cloudtrail-details/dspm-choose-log-events.png)
[]![The Key policy section with the permissions added.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-aws-key-policy.png)
[]![The Actions drop-down menu listing the actions available for the selected accounts.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-bulk-update-cloudtrail.png)
[]![The policy editor to edit the permissions for CloudTrail KMS policy.](/downloads/dspm/administration/cloud-accounts-onboarding/cloudtrail/managing-cloudtrail/dspm-cloudtrail-policy.png)