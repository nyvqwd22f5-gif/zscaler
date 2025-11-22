# Adding Organization Details
Source: https://help.zscaler.com/dspm/adding-organization-details
PDF: https://help.zscaler.com/pdf/com/en/1525716.pdf

The first step in the [onboarding process](/dspm/onboarding-aws-organization) is to provide the AWS organization details. DSPM uses these details to generate a template to connect to the AWS organization.
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
- Click **Add New**.
-
In the **Select Cloud Provider** window:
- For **Select Cloud Type**, select **AWS**.
- For **Select Onboarding Type**, select **Organization**.
[See image.](#selecr-csp)
- Click **Next**.
-
In the **Add New Organization Configuration** section:
- **Organization Details**:
- **DSPM Alias**: Enter a user-friendly name for the organization that you want to onboard.
- []**Role Name**: Enter a unique role name. This role name is added as a prefix to all the [roles](/dspm/iam-roles-and-permissions-aws) that are created during the onboarding process.
- **Management Account Name**: Enter the name of the management account. You can find this in the [AWS Management Console](https://aws.amazon.com/console/) under **Organization**.
- **Management Account ID**: Enter the 12-digit AWS account ID of the management account.
- **Organization ID**: Enter the organization ID that you want to onboard. You can find this in the [AWS Management Console](https://aws.amazon.com/console/) in multiple ways. For example:
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/).
- On the top right, select your account and then click **Organization**.
-
In the left-side navigation, copy the **Organization ID**.
[See image.](#organizationID)
- **Notification Emails** (Optional): Enter the email addresses of the recipients who must be notified of any configuration or permissions issues encountered with the onboarded organization. You can add up to 30 email addresses of recipients. You can also add email addresses after completing the onboarding process.
- **External ID**: View the optional identifier that is autopopulated. This ID is used in an IAM role trust policy to designate a specific user to assume the IAM role to provide access to the AWS resources. To learn more, refer to the [AWS documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-user_externalid.html).
- **CloudTrail Details**:
-
**CloudTrail Type**: Select the **OrgCloudTrail** checkbox, if it is an organization CloudTrail. [Organization CloudTrail](/dspm/understanding-aws-cloudtrail) shares the CloudTrail events of the management and member accounts of the organization to the same CloudTrail S3 bucket.
During initial onboarding, DSPM checks for log files to perform data scan in the following paths:
| CloudTrail Type | Path |
| --------------- | ---- |
| Organization CloudTrail | `prefix/<organization ID>/<management account ID>` |
| Account CloudTrail | `prefix/<management account ID>` |
After the onboarding is completed successfully, DSPM checks for log files in each target account.
- **CloudTrail Bucket Name**: Enter the S3 bucket name that is associated with CloudTrail. This S3 bucket stores the CloudTrail events.
-
**Prefix **(Optional): Enter the prefix specified in the CloudTrail S3 bucket path, if any.
[See image.](#cloudtrailprefix)
- **Bucket Account ID**: Enter the 12-digit AWS account ID where CloudTrail S3 bucket is present.
[See image.](#add-org-details)
- Click **Apply **to continue. Click **Reset** if you want to change the details.
If all the details are accurate, you are directed to the [Connect to the Organization](/dspm/deploy-aws-tree-discovery-template) section to deploy the tree discovery template.
[]![Select the cloud provider and onboarding type](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/adding-organization-details/dspm-select-cloud-provider.png)
[]![The AWS Organizations page with the list of AWS accounts and Organization ID blurred out.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-portal-org-ID.png)
[]![Enter the CloudTrail prefix](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/cloudtrail/managing-aws-cloudtrail-details/dspm-aws-cloutrail-logs.png)
[]![Enter the organization and CloudTrail details](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/adding-organization-details/dspm-aws-org-details.png)