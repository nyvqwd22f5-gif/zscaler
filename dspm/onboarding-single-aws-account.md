# Onboarding a Single AWS Account
Source: https://help.zscaler.com/dspm/onboarding-single-aws-account
PDF: https://help.zscaler.com/pdf/com/en/1474901.pdf

You can onboard a single AWS account for DSPM to monitor and [scan](/dspm/about-scan-settings) the [data stores](/dspm/supported-data-stores) (e.g., S3, EC2 instances, etc.) to identify sensitive data, misconfigurations, and vulnerabilities.
Onboarding Workflow
The onboarding workflow is as follows:
- Provide the orchestrator account details, select the network configuration, and configure the regions where you want to deploy the local scanner. DSPM uses these details to generate a template in both CloudFormation and Terraform format.
- Deploy the template on the orchestrator account. The template creates roles that provide DSPM with read-only permissions to access the account.
- Add the target accounts that must be monitored and deploy the templates.
Prerequisites
Before onboarding an AWS account, ensure you have completed the following:
- You must be assigned an Administrator role to onboard the AWS account.
- Identify an AWS account as the orchestrator account. The DSPM template is deployed in this account to scan the data in the target accounts.
- Configure[ ][CloudTrail](/dspm/about-cloudtrail) for management and data events. This allows DSPM to perform incremental [data scans](/dspm/about-scan-settings) on S3 buckets. To enable data events for S3 buckets:
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/) and go to **CloudTrail**.
- Under **Trails**, click the name of the CloudTrail that must be used to store data events.
-
Under **Data events**, click **Edit**.
[See image.](#dataevents-edit)
-
For **All current and future S3 buckets**, select the **Write** checkbox.
[See image.](#cloudtrail-event)
- Click **Save changes**.
- You must be assigned either an [Administrator role](/dspm/predefined-roles-and-permissions) or any role with Add Accounts permissions in the DSPM Admin Portal.
- Select the [CloudFormation](/dspm/onboarding-aws-organization#cfttemplate) or [Terraform Template](/dspm/onboarding-aws-organization#tftemplate).
Onboarding an AWS Account
To onboard an AWS account:
- [Add orchestrator details and configure regions.](/dspm/adding-orchestrator-details-and-configuring-regions)
- [Deploy the orchestrator template.](/dspm/deploying-orchestrator-template)
- [Add the target account and deploy the templates.](/dspm/adding-account-details-and-deploying-templates)
[]![The data events section with annotation around edit button](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/onboarding-aws-account/dspm-edit-dataevents-d3.png)
![The events and data events section with annotation around S3 bucket actions.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/onboarding-aws-account/dspmcloudtrail-dataevents-s3.png)
[]