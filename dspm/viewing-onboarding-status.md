# Viewing the Onboarding Status
Source: https://help.zscaler.com/dspm/viewing-onboarding-status
PDF: https://help.zscaler.com/pdf/com/en/1520571.pdf

DSPM runs a health validation service to check if the onboarding templates are deployed successfully and roles and permissions are configured for each account. After the validation is completed, the onboarding status of the target accounts and [orchestrator accounts](/dspm/understanding-orchestrator) are displayed on the Overview tab.
In this article, an AWS account's status is shown as an example.
The field names vary depending on the cloud account: **Account **for AWS, **Subscription **for Microsoft tenant, and **Project **for GCP.
On the **Overview **tab, you can view the following details:
-
**New template available for deployment** (Optional): A notification banner is displayed if a new template (e.g., Tree Discovery, Onboarding) is available for deployment. DSPM releases new templates that include additional functionalities for scanning and collecting metadata. Click **See Details** to view the available templates on the [Roles and Templates](/dspm/viewing-roles-and-templates) tab.
[See image.](#notification-banner)
If you close the notification banner, it is removed only for the current session. The message is displayed when you log in again.
- **Account Status**: The number of accounts configured for [data scan](/dspm/about-scan-settings) versus the total number of accounts in the organization displayed in the donut chart. You can see the following statuses:
- **Successfully Configured**: The number of accounts that are configured and validated successfully.
- **Needs Attention**: The number of accounts that have [misconfigurations or permission issues](/dspm/resolving-onboarding-issues).
- **Pending Configuration**: The number of accounts for which the roles and permissions are yet to be configured and validated.
- **Monitored Regions**: The list of [regions](/dspm/managing-regions) where the target accounts are located.
- The list of AWS [services ](/dspm/managing-regions)selected for monitoring and scanning.
- **Orchestrator Details**: The details about the [orchestrator account](/dspm/understanding-orchestrator) in which the DSPM's orchestrator template is deployed. You can see:
- **Account Name**: The account name.
- **Account ID**: The account ID.
- **Custom Tags**: The number of [custom tags](/dspm/managing-custom-tags) added.
- **Region**: The primary region selected while onboarding.
- **Network Type**: The network configuration ([Zscaler](/dspm/onboarding-aws-organization) or [Custom](/dspm/configuring-aws-network)) used for onboarding the account or organization.
- **DSPM Connection Status**: The [connection status](/dspm/viewing-orchestrator-status) (**Successful** or **Failed**) of the orchestrator instance with DSPM.
- **Configuration Status**: The [configuration status](/dspm/viewing-orchestrator-status) (**Successful**, **Warning**, **Failed**, or **Pending Validation**) indicating whether all accounts are available and permissions are configured correctly in the orchestrator subscription.
- **Last Connected**: The last time the orchestrator instance was successfully connected with DSPM.
-
**CloudTrail**: The details of the [organization CloudTrail](/dspm/understanding-aws-cloudtrail) provided while [onboarding](/dspm/onboarding-aws-organization). You can see:
This field is available only for AWS organizations.
- **CloudTrail Bucket Name**: The name of the S3 bucket where the CloudTrail events are logged.
- **Prefix**: The prefix specified in the CloudTrail bucket path.
- **Bucket Account ID**: The AWS account ID where the CloudTrail S3 bucket is present.
- **Status**: The status (**Enabled** or **Failed**) of the CloudTrail configuration.
- **Evidence**: The details of the S3 bucket where the evidence data is stored.
- **S3 Bucket Name**: The S3 bucket name.
- **Storage Type**: The storage type (**Zscaler** or **Custom**).
- **S3 Bucket Account ID**: The S3 bucket account ID.
-
**Data Events**: The details of the CloudTrail where the data events are stored. You can see:
This field is available only for AWS organizations.
- **CloudTrail Bucket Name**: The name of the S3 bucket where the data events are stored.
- **Prefix**: The prefix specified in the CloudTrail bucket path.
- **Bucket Account ID**: The AWS account ID where the S3 bucket is present.
- **Status**: The status (**Enabled** or **Failed**) of the CloudTrail configuration.
![The Overview tab for an AWS account that shows the account status, orchestrator account, and CloudTrail details.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/viewing-onboarding-status/dspm-organization-status.jpg)
[]![View the notification banner at the top of the Overview tab.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/viewing-onboarding-status/dspm-see-details-option.jpg)