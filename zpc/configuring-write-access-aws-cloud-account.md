# Configuring Write Access for an AWS Cloud Account
Source: https://help.zscaler.com/zpc/configuring-write-access-aws-cloud-account
PDF: https://help.zscaler.com/pdf/com/en/1457306.pdf

The write access permission allows the cloud service provider to remediate alerts generated for the cloud account.
Enabling Write Access for an AWS Cloud Account
To enable write access for an AWS cloud account:
- Go to **Administration** > **Cloud Accounts**.
- Click the **Column Menu** icon (![Edit Icon](/downloads/zpc/alerts/editing-or-deleting-ignore-filters/action-icon.png)
), then click **Add Write Access** for the AWS account you want to remediate.
[See image.](#add-access)
- On the **Deploy Template** page, you can:
- View the prerequisites for running the deploy template bash script. The deploy template script connects all selected CloudTrail S3 buckets to ZPC.
- Copy the bash script.
[See image.](#deploy-add)
- On the [AWS Management Console](https://aws.amazon.com/console/), run the copied bash script on the AWS CloudShell.
- After the script is deployed, return to the Deploy Template page in the ZPC Admin Portal, click **Finish**.
The **Write Access** column for the AWS account changes from N/A to Enabled to indicate that remediation is allowed. To learn more, see [Remediating Alerts](/zpc/remediating-alerts).
[See image.](#write-access-enabled)
Disabling Write Access for the Cloud Account
You can disable write access for an AWS account at the policy level on the AWS Cloudshell.
- Log in to the [AWS Management Console](https://aws.amazon.com/console/).
- Go to **Identity and Access Management (IAM)** > **Roles**.
[See image.](#iam-role)
- Search for the IAM Role associated with the AWS account for which you want to disable write access and then click the IAM Role from the displayed result.
[See image.](#search-iam-aws)
You can find the IAM Role in the cloud account drawer on the **Cloud Accounts** page. [See image.](#cloud-accounts-drawer)
- On the **Permissions** tab, select the **zpc-remediation-policy** checkbox.
[See image.](#checkbox)
- Click **Remove**.
[See image.](#remove)
The write access is disabled for the cloud account.
[![View the Cloud Accounts Page](/downloads/zpc/administration/cloud-accounts/enabling-write-access-cloud-account/zpc-add-write-access.png?1688631378)
]
[![View the Deploy Template page](/downloads/zpc/administration/cloud-accounts/enabling-write-access-cloud-account/zpc-add-deploy.png)
]
[![View the Cloud Accounts Page](/downloads/zpc/administration/cloud-accounts/enabling-write-access-cloud-account/zpc-enabled-write-access.png)
]
[![View the Cloud Accounts Drawer](/downloads/zpc/administration/cloud-accounts/onboarding-cloud-accounts/onboarding-amazon-web-services-account/zpc-search-iam-role.png)
]
[![View the AWS Console page](/downloads/zpc/administration/cloud-accounts/enabling-write-access-cloud-account/zpc-remediation-policy-checkbox.png?1688652880)
]
[![View the AWS Console page](/downloads/zpc/administration/cloud-accounts/enabling-write-access-cloud-account/zpc-write-access-remove.png?1688651697)
]
[![View the AWS Console page](/downloads/zpc/administration/cloud-accounts/enabling-write-access-cloud-account/zpc-iam-roles.png?1688652120)
]
[![View the IAM dashboard](/downloads/zpc/administration/cloud-accounts/enabling-write-access-cloud-account/zpc-search-iam-role-aws.png)
]